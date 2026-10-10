# Master Portfolio & Technical Interview Guide: Top 4 Engineering Projects

> **Workspace:** `s:\gravity projects\summary of all projects`  
> **Target Audience:** Engineering Hiring Managers, Technical Interviewers, System Design Examiners  
> **Author Portfolio:** High-Performance Full-Stack, Mobile Systems, Distributed Microservices & Cyber Defense

---

## Quick Navigation Index

| # | Project Name | Tech Stack | Primary Focus & Domain | In-Depth Document |
| :-: | :--- | :--- | :--- | :--- |
| **01** | **[MSK Code Arena](#1-msk-code-arena--ai-powered-coding-practice-platform)** | Next.js 14/16 · React 18 · Node.js · Express · C++17 · Gemini AI | Full-Stack, Online Judge Engine, Sandbox Isolation, SSE, SingleFlight, Token Bucket | [📖 Read Deep-Dive](file:///s:/gravity%20projects/summary%20of%20all%20projects/01_MSK_CODE_ARENA.md) |
| **02** | **[CareSync Mobile](#2-caresync-mobile--hospital-appointment--resource-management)** | Flutter (Dart) · Node.js · Express · MongoDB · Python Scripts | Mobile Architecture, Provider Pattern, Clinical Workflows, Inventory Automation | [📖 Read Deep-Dive](file:///s:/gravity%20projects/summary%20of%20all%20projects/02_CARESYNC_MOBILE.md) |
| **03** | **[SwitchAI](#3-switchai--universal-ai-memory--multi-model-router)** | Python 3.8+ · FastAPI · Microservices · SQLAlchemy · SQLite · Pytest | Distributed AI Gateway, Universal Memory, Context Passport, Circuit Breaker | [📖 Read Deep-Dive](file:///s:/gravity%20projects/summary%20of%20all%20projects/03_SWITCHAI.md) |
| **04** | **[CryptoFlow-IDS](#4-cryptoflow-ids--encrypted-traffic-intrusion-detection-system)** | C++ (eBPF) · Python 3.8+ · Scapy · Random Forest · FastAPI · WebSockets | Cyber Analytics, Shannon Entropy Math, In-Kernel Filtering, Mitigation Caching | [📖 Read Deep-Dive](file:///s:/gravity%20projects/summary%20of%20all%20projects/04_CRYPTOFLOW_IDS.md) |

---

## Comparative Engineering Matrix

| Feature / Dimension | 01. MSK Code Arena | 02. CareSync Mobile | 03. SwitchAI | 04. CryptoFlow-IDS |
| :--- | :--- | :--- | :--- | :--- |
| **Primary Language(s)** | TypeScript, JavaScript, C++17 | Dart, JavaScript, Python | Python 3.8+ | C, C++, Python 3.8+ |
| **Frontend Framework** | Next.js 14/16 App Router + Monaco Editor | Flutter 3.x (Material 3) | React 18 + Vite + Tailwind CSS | Cyber HUD (FastAPI + WebSockets) |
| **Backend Framework** | Node.js + Express.js | Express.js + Python Admin Scripts | FastAPI (ASGI / Starlette) | FastAPI + Multi-process Python Engine |
| **Database / Storage** | Pluggable Repository (LRU Map / MongoDB) | MongoDB Atlas (Mongoose) + Local JSON | SQLAlchemy ORM + SQLite (Fernet Vault) | SQLite (`cryptoflow.db`) + PCAP Forensics |
| **Concurrency Model** | Producer-Consumer Prioritized Worker Queue | Scoped ChangeNotifier Providers | Async Event Loop + Bounded Retries | Dedicated OS Process (Python GIL Bypass) |
| **Traffic / Fault Safety** | Token Bucket Limiter + SingleFlight Coalescing | Client Pre-Flight + Transactional Slot Rules | In-Memory Sliding Circuit Breaker (30s) | In-Memory Mutex Lock & Mitigation Debounce |
| **Real-Time Mechanism** | Server-Sent Events (SSE) Unidirectional | Reactive Stream Providers + Timers | SSE Streaming + Context Passport | Bi-Directional WebSockets (60 FPS HUD) |
| **Key Performance Stat** | 90%+ CPU saved via SingleFlight Deduplication | 15s Request Timeouts + Zero Slot Overbooking | 0ms Circuit Fast-Fail on 429 Outages | 100x Faster Mitigation (6,983ms $\rightarrow$ 69.59ms) |

---

## 1. MSK Code Arena — AI-Powered Coding Practice Platform
*Full Document:* **[01_MSK_CODE_ARENA.md](file:///s:/gravity%20projects/summary%20of%20all%20projects/01_MSK_CODE_ARENA.md)**

### Elevator Pitch
> *"MSK Code Arena is a high-performance, full-stack online coding practice and evaluation platform that allows developers to paste unstructured DSA problems from any website and instantly code, test, run, and evaluate C++ solutions in a real-time, sandboxed execution environment."*

### Key Technical Talking Points
1. **Complete Architecture & Request Flow:**
   - **Frontend:** Next.js 14 App Router, Microsoft Monaco Editor, `react-resizable-panels` split view.
   - **Gateway:** Token Bucket rate limiter (30 burst, 2/sec refill) and Circuit Breaker guarding external AI calls.
   - **Execution Pipeline:** Deduplication via SingleFlight $\rightarrow$ L1 SHA-256 Cache $\rightarrow$ Prioritized Job Queue $\rightarrow$ Isolated `g++` compilation.
2. **Frontend-Backend Real-Time Communication:**
   - Hybrid HTTP POST + **Server-Sent Events (SSE)**.
   - Initial `POST /run` responds immediately with queue position and estimated wait time.
   - Client opens `EventSource('/submission-status/:id')`, receiving real-time milestones (`queued` $\rightarrow$ `compiling` $\rightarrow$ `running_tests` $\rightarrow$ `completed`) before closing.
3. **Execution Sandbox & Line Number Synchronization:**
   - Injects `#line 1 "solution.cpp"` directives so compiler error line numbers map **1:1** to the user’s Monaco Editor lines.
   - Strict resource ceilings: 5-second `SIGKILL` timeout, 512 KB stdout overflow kill, and sanitized error streams.
4. **Database & Storage Optimization:**
   - Pluggable Repository Pattern (`BaseStorageAdapter`) with zero-latency `InMemoryStorageAdapter` supporting automatic LRU key eviction and 180s background TTL sweeps.
   - Content-addressable SHA-256 caching skips compilation for identical code submissions ($< 1\text{ms}$ return).
5. **Concurrency & Traffic Shaping:**
   - **SingleFlight Coalescing:** Eliminates the *Thundering Herd* problem during contests—50 concurrent identical requests trigger only 1 compilation, saving 90%+ CPU cycles.
   - **Prioritized Queue:** Dynamic backpressure trips HTTP 429 if the backlog exceeds 30 tasks.

---

## 2. CareSync Mobile — Hospital Appointment & Resource Management
*Full Document:* **[02_CARESYNC_MOBILE.md](file:///s:/gravity%20projects/summary%20of%20all%20projects/02_CARESYNC_MOBILE.md)**

### Elevator Pitch
> *"CareSync Mobile is a cross-platform Flutter healthcare management application that unifies patient slot bookings, doctor consultations, real-time hospital bed/blood inventory tracking, and financial ledger billing into an integrated system."*

### Key Technical Talking Points
1. **Mobile-to-Backend Networking:**
   - Centralized `ApiClient` singleton enforcing 15-second timeouts and mapping HTTP status codes to typed `AppException` subclasses (`ValidationException`, `AuthenticationException`, `ServerException`).
   - Seamless environment switching via `--dart-define=API_BASE_URL` without altering codebase.
   - State management hoisted via `MultiProvider` utilizing `context.read` for event triggers and `context.watch` for scoped UI rebuilds.
2. **Clinical Validation & Scheduling Rules:**
   - Five discrete operational slots: `10:00 AM`, `11:00 AM`, `02:00 PM`, `03:00 PM`, `04:00 PM` with a mandatory `12:00 PM - 02:00 PM` lunch blackout.
   - Hard capacity limit: Maximum **3 patients** per doctor per slot. Past dates disabled in date pickers.
3. **Preventing Race Conditions & Overbooking:**
   - Multi-layer defense: Client disables full slots dynamically; `AppointmentService.bookAppointment()` queries server immediately before dispatching POST; server rejects duplicate or conflicting bookings with HTTP 400.
4. **Database Schema & Inventory Automation:**
   - MongoDB Mongoose schemas for `User`, `Appointment`, `Allocation`, `FinancialLedger`, `PurchaseOrder`, and `Resource`.
   - Completing a consultation automatically decrements available beds and blood bank stock, posts \$500/\$200 charges in `FinancialLedger`, and triggers automated purchase orders if blood units drop $\le 10$.
   - Prescription revisions (`isUpdated: true`) update notes while explicitly skipping duplicate inventory deductions.

---

## 3. SwitchAI — Universal AI Memory & Multi-Model Router
*Full Document:* **[03_SWITCHAI.md](file:///s:/gravity%20projects/summary%20of%20all%20projects/03_SWITCHAI.md)**

### Elevator Pitch
> *"SwitchAI is an intelligent, provider-agnostic conversational platform ('One memory. Many AI models.') that decouples context, facts, and architectural decisions from vendor silos, enabling frictionless switching mid-thread across 8 AI providers with zero context loss and automated circuit breaker fallbacks."*

### Key Technical Talking Points
1. **Why FastAPI & Microservices Were Chosen:**
   - Asynchronous ASGI event loop (`uvicorn`) handles long-running LLM streaming connections without thread pool starvation.
   - Pydantic v2 compiles in Rust for ultra-fast validation and automated Swagger/OpenAPI docs (`/docs`).
   - Decoupled `ProviderAdapter` abstract base class isolates vendor SDKs (Google, OpenAI, Anthropic, DeepSeek, Groq, Mistral, Cohere, Ollama).
2. **Smart Auto-Routing & Universal Memory:**
   - Heuristic task classifier categorizes prompts into `coding`, `reasoning`, `long_context`, `summarization`, `fast_response`, and `rag_offline`.
   - Strategies (`Quality First`, `Speed First`, `Cost First`, `Balanced`) route queries to the most cost-effective model.
   - **Context Passport Engine:** Compiles durable facts, goals, constraints, and dialogue turns into a normalized `ContextPackage` transferred across providers with zero context loss.
3. **Concurrency, Timeouts & Error Normalization:**
   - Bounded exponential backoff retries (`0.1 * 2^attempt`) for transient faults.
   - Standardizes disparate vendor exceptions into unified `NormalizedError` taxonomy (`RATE_LIMIT`, `TIMEOUT`, `SERVICE_UNAVAILABLE`, `AUTHENTICATION_ERROR`).
4. **Circuit Breaker Mechanics & Fault Testing:**
   - State machine: `CLOSED` $\rightarrow$ `OPEN` (tripped after 3 consecutive failures) $\rightarrow$ `HALF_OPEN` (probed after 30s cooldown).
   - Bypasses failing providers in **0ms**, falling back down the chain to secondary providers or the embedded 28-domain offline RAG engine.
   - Verified via **Pytest** using `unittest.mock.patch` with an isolated in-memory SQLite database (`StaticPool`).

---

## 4. CryptoFlow-IDS — Encrypted Traffic Intrusion Detection System
*Full Document:* **[04_CRYPTOFLOW_IDS.md](file:///s:/gravity%20projects/summary%20of%20all%20projects/04_CRYPTOFLOW_IDS.md)**

### Elevator Pitch
> *"CryptoFlow-IDS is a next-generation hybrid Network Intrusion Detection System that combines cryptographic side-channel metadata analysis, Shannon Entropy math, and a Random Forest classifier (99.8% accuracy) to detect malicious exfiltrations inside TLS 1.3 and QUIC traffic without decrypting payloads or violating privacy."*

### Key Technical Talking Points
1. **End-to-End Processing Pipeline:**
   - Packet capture via Scapy / Npcap (Windows) and in-kernel eBPF socket filters in C (`ebpf_sniffer.c` on Linux).
   - Dedicated OS worker process (`multiprocessing.Process`) bypasses Python's Global Interpreter Lock (GIL), keeping the Cyber HUD at 60 FPS.
   - Filters payloads $< 200$ bytes; validates RFC 9000 QUIC packets on UDP ports 443/8443 (fixed bit `0x40`).
2. **Telemetry & Cryptographic Anomalies:**
   - Telemetry tracks packet throughput (pps), byte histograms, and entropy timelines.
   - Anomalies: Benign plaintext has entropy $< 4.5$; benign TLS web browsing has entropy $4.5 - 6.8$ with record framing (`0x14 - 0x17, 0x03`); raw encrypted exfiltration has uniformly distributed random bytes with entropy **$> 7.2 - 7.99$**.
3. **Detection Logic & Machine Learning:**
   - **Shannon Entropy Formula:** $H(X) = -\sum_{i=0}^{255} p(x_i) \log_2 p(x_i)$ over a 256-bin byte frequency histogram.
   - Random Forest AI trained on 10,000 flow samples using `[Entropy, PacketSize, DstPort]`.
   - Tri-Condition Threat Verification: `prediction == 1 AND entropy > 7.2 AND confidence > 0.75`.
4. **False Positive Mitigation & Evaluation:**
   - Eliminates false alerts on compressed media and video streams via TLS header filters, strict entropy gating, and local IP whitelisting.
   - Achieves **99.82% test accuracy**, 99.7% precision, and 0.9994 ROC-AUC.
5. **100x Mitigation Caching Optimization:**
   - Under packet floods, naively spawning `netsh advfirewall` took 6,983ms.
   - Thread-safe mutex lock and `pending_blocks` in-memory cache guarantees **strictly ONE `netsh` invocation per malicious IP**, dropping flood latency to **69.59ms (100x speedup)**.

---

## 5. Master Interview Preparation Playbook

### The STAR Framework for Presenting Your Projects

```
+---------------------------------------------------------------------------------+
| S - SITUATION: Explain the problem space, scale, and bottleneck.               |
| T - TASK: Define your specific engineering goal and technical requirements.     |
| A - ACTION: Explain your architecture, distributed patterns, and custom code.   |
| R - RESULT: Share measurable outcomes (latency, throughput, CPU saved, tests).   |
+---------------------------------------------------------------------------------+
```

#### Example 1: MSK Code Arena (Concurrency & Performance)
- **S:** *"During coding practice, hundreds of users run solutions simultaneously. Firing duplicate compiler processes causes CPU spikes and queue lag."*
- **T:** *"I needed to build an isolated execution engine that protects host resources, prevents duplicate compilations, and streams live progress."*
- **A:** *"I implemented SingleFlight request coalescing, an L1 SHA-256 cache, a prioritized worker queue with dynamic backpressure, and Server-Sent Events (SSE) in Express."*
- **R:** *"Duplicate compilations dropped by 90%+, backpressure protected the server from crashing under load, and SSE eliminated polling overhead."*

#### Example 2: CryptoFlow-IDS (Security & Systems Engineering)
- **S:** *"Modern adversaries exfiltrate corporate data through TLS and QUIC, bypassing traditional firewalls because payloads are encrypted."*
- **T:** *"I set out to detect encrypted data exfiltration packet-by-packet in real-time without breaking user privacy or decrypting payloads."*
- **A:** *"I engineered an in-kernel eBPF and Scapy capture engine, isolated Shannon entropy math in a separate OS process to bypass Python's GIL, and trained a Random Forest model."*
- **R:** *"Achieved 99.8% accuracy, detected RFC 9000 QUIC threats, and reduced automated firewall blocking latency from 6,983ms to 69.59ms using thread-safe caching."*

---

### Key Takeaway Summary
All four projects showcase **real-world production design patterns**:
- **Asynchronous I/O & Non-Blocking Architectures** (FastAPI ASGI, Node.js Event Loop, Python Multiprocessing).
- **Distributed Stability Patterns** (Circuit Breakers, SingleFlight Coalescing, Token Bucket Rate Limiting, Backpressure Governors).
- **Sound Typing & Memory Management** (TypeScript, Dart Null Safety, Pydantic v2, C/C++ memory isolation).
- **Comprehensive Automated Testing** (Pytest mock suites, DSA regression suites, and clinical constraint validations).
