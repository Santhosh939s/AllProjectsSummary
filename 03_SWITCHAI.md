# 03. SwitchAI — Technical Architecture & Interview Deep-Dive

> **Core Stack:** Python 3.8+ · FastAPI · Microservices & Adapter Pattern · SQLAlchemy ORM · SQLite · Pydantic v2 · Pytest · Fernet Encryption  
> **Domain:** Distributed AI Orchestration, Multi-Model Routing, Resilient Microservices, Circuit Breakers, Fault-Tolerant Systems  
> **Source Location:** `S:\gravity projects\SwitchAI`

---

## Table of Contents
1. [Executive Summary & Architectural Philosophy](#1-executive-summary--architectural-philosophy)
2. [Why FastAPI & Microservices Architecture Were Chosen](#2-why-fastapi--microservices-architecture-were-chosen)
3. [How Routing Between Services Works (Smart Router & Context Passport)](#3-how-routing-between-services-works-smart-router--context-passport)
4. [Concurrency, Timeouts & Normalized Error Handling](#4-concurrency-timeouts--normalized-error-handling)
5. [The Circuit Breaker Pattern: Mechanics & Implementation](#5-the-circuit-breaker-pattern-mechanics--implementation)
6. [Testing Service Failures, Resilience & Automated Recovery](#6-testing-service-failures-resilience--automated-recovery)
7. [Top Interview Questions & Battle-Tested Answers](#7-top-interview-questions--battle-tested-answers)

---

## 1. Executive Summary & Architectural Philosophy

### The Problem SwitchAI Solves
Modern generative AI workflows suffer from severe architectural fragmentation and vendor lock-in:
1. **Siloed Provider Memory:** Context in ChatGPT, Claude, or Gemini is trapped inside vendor walls. Switching from GPT-4o to Claude 3.5 Sonnet requires re-explaining the entire project background, architecture, and constraints.
2. **Fragility During Outages & Rate Limits (HTTP 429):** When an AI provider suffers rate limits, quota exhaustion, or service degradation (HTTP 503), the entire user session breaks abruptly without automated fallback to an alternative model.
3. **Excessive Token Costs:** Routine definitions and standard programming concepts consume costly cloud API tokens when they could be answered instantly by a local grounded engine at $0 cost.

**SwitchAI** (*"One memory. Many AI models."*) decouples conversation memory, durable project facts, user decisions, and architectural constraints from individual AI vendors. It acts as an intelligent, resilient gateway across 8 major providers (Google Gemini, OpenAI, Anthropic Claude, DeepSeek, Groq LPU, Mistral AI, Cohere, and Local Ollama), alongside an embedded offline 28-domain RAG engine.

### High-Level System Architecture

```
                      +------------------------------------------+
                      |         REACT 18 / TS CLIENT             |
                      |   Cyber-Flame UI + Real-Time Telemetry   |
                      +--------------------+---------------------+
                                           | HTTPS / REST / SSE
                                           v
                      +------------------------------------------+
                      |          FASTAPI GATEWAY ROUTER          |
                      |    Async ASGI Event Loop / Pydantic v2   |
                      +--------------------+---------------------+
                                           |
                +--------------------------+--------------------------+
                |                                                     |
                v                                                     v
+-------------------------------+                     +-------------------------------+
|     UNIVERSAL MEMORY LAYER    |                     |    SMART ROUTER & FALLBACK    |
| - Goals, Facts, Decisions     |                     | - Task Classifier (Coding/RAG)|
| - Constraints, Preferences    |                     | - Routing Policy (Speed/Cost) |
| - Context Passport Generator  |                     | - Circuit Breaker State Cache |
+---------------+---------------+                     +---------------+---------------+
                |                                                     |
                +--------------------------+--------------------------+
                                           |
                                [ ContextPackage Payload ]
                                           |
     +-------------+-------------+---------+---------+-------------+-------------+
     |             |             |                   |             |             |
     v             v             v                   v             v             v
+---------+   +---------+   +---------+         +---------+   +---------+   +---------+
| Gemini  |   | OpenAI  |   | Claude  |   ...   | DeepSeek|   | Groq    |   | 28-Dom  |
| Adapter |   | Adapter |   | Adapter |         | Adapter |   | Adapter |   | RAG Eng |
+---------+   +---------+   +---------+         +---------+   +---------+   +---------+
```

---

## 2. Why FastAPI & Microservices Architecture Were Chosen

### 2.1. Why FastAPI Instead of Flask or Django?
1. **Asynchronous Non-Blocking Concurrency (ASGI):**
   - AI generation involves long-running HTTP streaming requests (often taking 2–15 seconds per response).
   - In synchronous WSGI frameworks like Flask or Django, every slow LLM call blocks an entire OS worker thread. Under modest traffic (e.g. 50 concurrent users), the thread pool exhausts, leading to request queuing and timeouts.
   - FastAPI is built natively on **Starlette** and **uvicorn** (ASGI event loop). It handles thousands of concurrent I/O connections asynchronously on a single core without thread starvation.
2. **Pydantic v2 Type Safety & Schema Validation:**
   - LLM integrations receive complex nested JSON structures. Pydantic v2 (compiled in Rust) validates incoming payloads, serializes responses, and prevents silent runtime data corruptions.
3. **Automated Interactive Documentation (OpenAPI/Swagger):**
   - Automatically generates live Swagger UI at `/docs`, enabling rapid contract testing for frontend developers and external client consumers.

### 2.2. The Pluggable Microservices / Adapter Pattern
Rather than hardcoding vendor SDK calls inside HTTP route handlers, SwitchAI implements the **Provider Adapter Pattern** via an abstract base class (`app/adapters/base.py`):

```python
class ProviderAdapter(ABC):
    @abstractmethod
    def validate_credentials(self, api_key: str) -> bool: ...

    @abstractmethod
    def list_models(self) -> List[str]: ...

    @abstractmethod
    def generate(self, context_package: ContextPackage, api_key: str, model: str) -> ProviderResponse: ...

    @abstractmethod
    def stream(self, context_package: ContextPackage, api_key: str, model: str) -> AsyncGenerator: ...

    @abstractmethod
    def normalize_error(self, error: Exception) -> NormalizedError: ...

    @abstractmethod
    def get_health(self, api_key: str) -> ProviderHealth: ...
```

#### Why This Decoupled Microservice Design Matters:
- **Vendor SDK Isolation:** When OpenAI updates their SDK or Anthropic deprecates a model name, changes are strictly confined to `adapters/openai.py` or `adapters/anthropic.py`. The core routing and memory services remain untouched.
- **Unified Interface:** Route handlers only interact with the unified `ProviderResponse` and `ContextPackage` schemas.
- **Zero Client-Side Credentials:** All vendor API keys are stored server-side encrypted using 32-byte **Fernet symmetric encryption** (`ENCRYPTION_KEY`) in SQLite, never leaking to browser storage.

---

## 3. How Routing Between Services Works (Smart Router & Context Passport)

### 3.1. Smart Task Classification Heuristics
When a user prompt enters `app/services/routing.py`, the system analyzes its semantic characteristics and classifies it into a specialized task domain:

| Task Type | Trigger Keywords / Heuristics | Optimal Provider Strategy |
| :--- | :--- | :--- |
| `coding` | `def`, `class`, `function`, `code`, `bug`, `sql`, `git`, `regex` | Routes to **DeepSeek** (`deepseek-coder`) or **GPT-4o** |
| `reasoning` | `why`, `prove`, `logic`, `math`, `compare`, `trade-off` | Routes to **Claude 3.5 Sonnet** or **o1-mini** |
| `long_context` | Payload length $> 300$ words, `document`, `report`, `analyze` | Routes to **Gemini 1.5 Pro** (2M token window) |
| `summarization`| `summarize`, `tldr`, `overview`, `key takeaways` | Routes to **Claude 3.5 Haiku** or **Gemini Flash** |
| `fast_response`| Short queries $< 8$ words, greetings, status pings | Routes to **Groq LPU** (`llama-3.3-70b`, $< 500\text{ms}$) |
| `rag_offline`  | Computer science theory, algorithms, physics, history | Routes to **Local 28-Domain RAG Engine** ($0 cost) |

### 3.2. Dynamic Routing Strategies
Users can configure routing strategies to govern model selection:
1. **Quality First:** Prioritizes top-tier frontier models (Claude 3.5 Sonnet, GPT-4o, DeepSeek Reasoner).
2. **Speed First:** Prioritizes Groq LPU models (up to 750 tokens/second).
3. **Cost First:** Prioritizes the offline RAG engine or cost-effective models (Gemini 1.5 Flash, GPT-4o-mini).
4. **Balanced:** Dynamically maps task complexity to cost/performance sweet spots.

### 3.3. The Universal Memory Layer & Context Passport
SwitchAI preserves state across models using semantic memory tagging:
- `goal`: High-level user objectives (*"Build an AI-powered triage platform"*)
- `fact`: Permanent project facts (*"PostgreSQL with asyncpg used for database storage"*)
- `decision`: Architectural choices (*"Decided to use Fernet symmetric encryption"*)
- `constraint`: Negative guidelines (*"Strictly avoid Tailwind v4; use Tailwind v3.4"*)
- `preference`: Response styling (*"Enforce concise, token-efficient system responses"*)

#### The Context Passport Payload (`ContextPackage`):
When a provider switch occurs (e.g. switching from DeepSeek to Gemini mid-thread), the backend compiles all accumulated memory items, recent message turns, and system constraints into a normalized `ContextPackage`:
```json
{
  "conversation_id": "conv_89f1a23c",
  "system_instruction": "Be concise, clear, and token-efficient.",
  "memories": [
    {"category": "goal", "key": "target_app", "value": "SwitchAI platform"},
    {"category": "fact", "key": "backend_framework", "value": "FastAPI + SQLAlchemy"}
  ],
  "recent_messages": [
    {"role": "user", "content": "How do we handle rate limits?"},
    {"role": "assistant", "content": "Using exponential backoff and circuit breaker fallback."}
  ]
}
```
The receiving provider’s adapter translates this unified package into its own vendor-specific format (e.g., Gemini `contents` array vs. OpenAI `messages` array), achieving **frictionless switching with zero context loss**.

---

## 4. Concurrency, Timeouts & Normalized Error Handling

### 4.1. Concurrency Management
- **Async Execution Pipeline:** High-throughput async handlers permit concurrent model queries across different threads.
- **Connection Pooling:** Database sessions use SQLAlchemy with connection pooling, avoiding connection leaks during heavy request bursts.

### 4.2. Bounded Exponential Backoff Retries
In `app/services/fallback.py`, when a transient error occurs (such as a brief network hiccup or temporary rate limit), the service executes bounded exponential retries before giving up:
```python
# Bounded exponential backoff before retrying the same provider
if attempt < max_retries - 1:
    time.sleep(0.1 * (2 ** attempt)) # 100ms, then 200ms
```

### 4.3. Error Normalization Taxonomy
Vendor SDKs throw completely different exceptions (e.g. `google.api_core.exceptions.ResourceExhausted` vs. `openai.RateLimitError` vs. `anthropic.RateLimitError`).

SwitchAI’s adapters intercept vendor-specific exceptions and map them into a single standardized taxonomy: `NormalizedError` (`adapters/base.py`):
```python
@dataclass
class NormalizedError:
    code: str              # RATE_LIMIT | TIMEOUT | SERVICE_UNAVAILABLE | AUTHENTICATION_ERROR | CONTEXT_TOO_LARGE
    message: str           # User-friendly explanation
    is_retryable: bool     # True for 429/503/timeouts, False for 401/400
    provider: str          # Name of the provider that originated the fault
    status_code: int       # HTTP status equivalent
```

---

## 5. The Circuit Breaker Pattern: Mechanics & Implementation

### 5.1. Why Circuit Breakers are Essential in AI Microservices
If Anthropic experiences an outage, a user prompt might wait 30 seconds before failing. If 20 users submit prompts, 20 worker threads hang for 30 seconds. Repeatedly hitting a failing endpoint exhausts system resources, burns through retry quotas, and severely degrades user experience.

A **Circuit Breaker** detects consecutive failures and trips to an `OPEN` state, immediately diverting traffic around the broken provider with **0ms latency penalty**.

### 5.2. State Machine Mechanics (`services/fallback.py`)

```
   [ Normal Operation ]
        CLOSED
          |
          | 3 Consecutive Failures (Rate Limit, Timeout, 503)
          v
         OPEN  <------+  Fast-fails in 0ms; routes to next provider in fallback chain
          |           |
          | 30s Cooldown Expires
          v           |
      HALF-OPEN ------+  Probes provider with limited request
          |
          | Success!
          v
        CLOSED
```

### 5.3. Actual Code Implementation in SwitchAI
```python
# Excerpt from app/services/fallback.py
CIRCUIT_BREAKER_FAILURES: Dict[str, int] = {}
CIRCUIT_BREAKER_LAST_FAILURE: Dict[str, float] = {}

FAILURE_THRESHOLD = 3
COOLDOWN_SECONDS = 30.0

def is_circuit_open(provider: str) -> bool:
    p = provider.lower()
    failures = CIRCUIT_BREAKER_FAILURES.get(p, 0)
    if failures >= FAILURE_THRESHOLD:
        last_fail = CIRCUIT_BREAKER_LAST_FAILURE.get(p, 0)
        if time.time() - last_fail < COOLDOWN_SECONDS:
            return True  # Circuit is OPEN! Reject immediately
        else:
            # Cooldown expired, transition to HALF_OPEN probe mode
            CIRCUIT_BREAKER_FAILURES[p] = 0
            return False
    return False

def record_provider_failure(db: Session, provider: str, status_code: Optional[int], error_type: str, latency_ms: float):
    p = provider.lower()
    CIRCUIT_BREAKER_FAILURES[p] = CIRCUIT_BREAKER_FAILURES.get(p, 0) + 1
    CIRCUIT_BREAKER_LAST_FAILURE[p] = time.time()

    # Log telemetry event to SQLite database for audit & analytics
    event = ProviderEvent(
        id=str(uuid.uuid4()),
        provider=p,
        status_code=status_code,
        error_type=error_type,
        latency_ms=latency_ms
    )
    db.add(event)
    db.commit()

def record_provider_success(db: Session, provider: str):
    p = provider.lower()
    CIRCUIT_BREAKER_FAILURES[p] = 0  # Heal circuit back to CLOSED
```

### 5.4. Dynamic Fallback Chain Traversal
When an error trips or a circuit is `OPEN`, `execute_with_fallback()` dynamically traverses the fallback chain:
1. Primary Provider: e.g., Anthropic Claude (throws 429 Rate Limit)
2. Adapter normalizes error $\rightarrow$ marks failure in circuit breaker cache
3. Engine falls back to Secondary Provider: Google Gemini
4. Successfully generates response $\rightarrow$ response returned with `is_fallback = True`
5. Context is fully preserved, and the UI displays a notification badge:
   `"Provider Switched: Anthropic experienced RATE_LIMIT. Successfully responded via Gemini."`

---

## 6. Testing Service Failures, Resilience & Automated Recovery

### 6.1. The Testing Architecture (`backend/tests/test_fallback.py`)
To rigorously test resilience without spending real API tokens or relying on external cloud stability, SwitchAI uses **Pytest** with:
- **In-Memory SQLite Database with `StaticPool`:** Ensures isolation and speed across test cases.
- **FastAPI `dependency_overrides`:** Replaces production database sessions with isolated test sessions.
- **`unittest.mock.patch`:** Injects controlled synthetic exceptions (429 Rate Limits, 504 Timeouts, 401 Auth Errors).

### 6.2. Verified Test Cases & Scenarios

#### Test 1: Simulating Rate Limit (HTTP 429) Automatic Failover
```python
@patch("app.adapters.anthropic.AnthropicAdapter.generate", side_effect=Exception("429 Too Many Requests: Rate limit exceeded"))
def test_rate_limit_fallback_to_secondary_provider(mock_ant, auth_headers):
    resp = client.post("/api/conversations", json={"title": "Fallback Test"}, headers=auth_headers)
    conv_id = resp.json()["id"]

    resp = client.post(
        f"/api/conversations/{conv_id}/messages", 
        json={"content": "Hello", "provider": "anthropic"}, 
        headers=auth_headers
    )
    assert resp.status_code == 200
    msg = resp.json()
    assert msg["sender_role"] == "assistant"
    assert msg["provider"] == "gemini"  # Successfully routed to fallback!
    assert "Provider Switched" in msg["content"]
    assert "RATE_LIMIT" in msg["content"]
```

#### Test 2: Simulating Downstream Gateway Timeout (HTTP 504)
```python
@patch("app.adapters.anthropic.AnthropicAdapter.generate", side_effect=Exception("504 Gateway Timeout"))
def test_timeout_fallback_to_secondary_provider(mock_ant, auth_headers):
    resp = client.post("/api/conversations", json={"title": "Timeout Test"}, headers=auth_headers)
    conv_id = resp.json()["id"]

    resp = client.post(
        f"/api/conversations/{conv_id}/messages", 
        json={"content": "Check timeout", "provider": "anthropic"}, 
        headers=auth_headers
    )
    assert resp.status_code == 200
    msg = resp.json()
    assert msg["provider"] == "gemini"
    assert "Provider Switched" in msg["content"]
```

#### Test 3: Total Cloud Failure & Degraded Offline RAG Recovery
```python
@patch("app.adapters.anthropic.AnthropicAdapter.generate", side_effect=Exception("429 Rate limit"))
@patch("app.adapters.gemini.GeminiAdapter.generate", side_effect=Exception("429 Quota exceeded"))
@patch("app.adapters.openai.OpenAIAdapter.generate", side_effect=Exception("429 Rate limit"))
@patch("app.adapters.deepseek.DeepSeekAdapter.generate", side_effect=Exception("429 Rate limit"))
@patch("app.adapters.groq.GroqAdapter.generate", side_effect=Exception("429 Rate limit"))
@patch("app.adapters.mistral.MistralAdapter.generate", side_effect=Exception("429 Rate limit"))
@patch("app.adapters.cohere.CohereAdapter.generate", side_effect=Exception("429 Rate limit"))
def test_all_providers_failing_graceful_error(m7, m6, m5, m4, m3, m2, m1, auth_headers):
    resp = client.post("/api/conversations", json={"title": "All Fail Test"}, headers=auth_headers)
    conv_id = resp.json()["id"]

    resp = client.post(
        f"/api/conversations/{conv_id}/messages", 
        json={"content": "Check all fail", "provider": "anthropic"}, 
        headers=auth_headers
    )
    assert resp.status_code == 200
    msg = resp.json()
    # Verifies graceful recovery: falls back to embedded Offline RAG engine
    assert "RAG Knowledge Engine" in msg["content"] or "Offline" in msg["content"]
```

---

## 7. Top Interview Questions & Battle-Tested Answers

### Q1: "Why use FastAPI for an AI gateway instead of Node.js or Go?"
**Answer:**
> "FastAPI gives us the best of both worlds:
> 1. **Native Python Ecosystem:** All leading AI frameworks, embeddings libraries, tokenizers, and vector stores are first-class citizens in Python.
> 2. **Async ASGI Concurrency:** Thanks to `uvicorn` and `asyncio`, FastAPI handles thousands of concurrent I/O connections asynchronously. Slow streaming LLM requests do not block the worker thread pool.
> 3. **Pydantic v2 Type Safety:** Pydantic v2 is implemented in Rust, providing high-speed JSON schema serialization and rigorous validation for complex LLM outputs."

### Q2: "How does SwitchAI prevent memory loss when a user switches from GPT-4o to Claude 3.5 Sonnet mid-conversation?"
**Answer:**
> "We decouple memory from model vendors through our **Universal Memory Layer**. In our SQLite database, conversation memories are stored as typed entities (`goal`, `fact`, `decision`, `constraint`, `preference`).
> 
> When a switch occurs, the backend constructs a **Context Passport** (`ContextPackage`) containing these structured memories alongside recent dialogue turns. The target provider's adapter translates this normalized package into its native API schema. The user experiences zero context loss, and no project facts or instructions are dropped."

### Q3: "What is a Circuit Breaker and how does your implementation prevent cascading failures?"
**Answer:**
> "A Circuit Breaker is a stability pattern that stops an application from repeatedly trying to execute an operation that is guaranteed to fail.
> 
> In SwitchAI, our `services/fallback.py` tracks provider failures in an in-memory cache. If a provider encounters 3 consecutive failures (such as HTTP 429 Rate Limits or 504 Timeouts), the circuit trips to `OPEN`. For the next 30 seconds, any request requesting that provider is immediately redirected to the next healthy provider in the fallback chain in 0ms, without waiting for another network timeout. After 30 seconds, it transitions to `HALF_OPEN` to probe health before fully closing."

### Q4: "How did you test that the fallback chain works without incurring massive API billing charges?"
**Answer:**
> "We wrote an automated test suite in **Pytest** using `unittest.mock.patch`. In `backend/tests/test_fallback.py`, we mock the `generate()` methods of our adapters to simulate realistic failure modes (429 Rate Limit, 504 Gateway Timeout, and 401 Unauthorized).
> 
> We verify that the fallback orchestrator catches the normalized error, trips the provider, seamlessly routes the request to secondary providers (e.g. Anthropic $\rightarrow$ Gemini $\rightarrow$ OpenAI), and ultimately falls back to the embedded offline RAG engine if all cloud APIs are exhausted. All of this runs locally against an in-memory SQLite database in under 3 seconds."
