# 01. MSK Code Arena — Technical Architecture & Interview Deep-Dive

> **Core Stack:** React 18 · Next.js 14/16 (App Router) · Node.js · Express · C++17 Execution Sandbox · Google Gemini 2.5 Flash  
> **Domain:** Full-Stack Web Development, Distributed Online Judge System, Sandbox Execution, High-Concurrency API Design  
> **Source Location:** `S:\gravity projects\MSK Code Arena – AI-Powered Coding Practice Platform`

---

## Table of Contents
1. [Executive Summary & High-Level Architecture](#1-executive-summary--high-level-architecture)
2. [Frontend-to-Backend Communication & Real-Time SSE](#2-frontend-to-backend-communication--real-time-sse)
3. [Code Execution Engine & Error Return Pipeline](#3-code-execution-engine--error-return-pipeline)
4. [Database Structure, Pluggable Storage & Query Optimization](#4-database-structure-pluggable-storage--query-optimization)
5. [Concurrency, Queue Backpressure, Rate Limiting & Fault Tolerance](#5-concurrency-queue-backpressure-rate-limiting--fault-tolerance)
6. [Top Interview Questions & Battle-Tested Answers](#6-top-interview-questions--battle-tested-answers)

---

## 1. Executive Summary & High-Level Architecture

### The Problem MSK Code Arena Solves
Conventional coding platforms (LeetCode, HackerRank, CodeChef) force students to adhere to rigid platform-specific interfaces. When developers encounter DSA problems from external sources (such as Striver's A2Z Sheet, GeeksforGeeks, coding contest PDFs, or campus placement drives), there is no seamless way to paste the raw text, obtain an automated sandbox harness, run custom test cases, and receive immediate compilation and runtime feedback.

**MSK Code Arena** bridges this gap:
- Users paste arbitrary problem statements or prompts.
- A hybrid parser (Local Regex + Google Gemini 2.5 Flash with strict JSON Schema) formats the problem, creates test cases, and extracts C++ method signatures.
- Code is edited in an embedded Microsoft Monaco Editor.
- When the user clicks **Run** or **Submit**, code is bundled with an in-house generated C++ test harness and executed inside an isolated native `g++` sandbox.
- Real-time progress milestones are pushed live to the browser via Server-Sent Events (SSE).

### High-Level Architectural Flowchart

```
+-----------------------------------------------------------------------------------------+
|                                    CLIENT BROWSER                                       |
|  - Next.js 14/16 App Router (React 18 + TypeScript)                                     |
|  - Monaco Code Editor (@monaco-editor/react) with C++ Autocomplete & Syntax Diagnostics |
|  - Resizable Dual-Pane IDE Workspace (react-resizable-panels)                           |
+----------------------------+-----------------------------------+------------------------+
                             | POST /run or /submit              | EventSource (SSE)
                             | (JSON Payload)                    | /submission-status/:id
                             v                                   |
+----------------------------------------------------------------+------------------------+
|                              EXPRESS.JS API GATEWAY                                     |
|  - CORS & JSON Body Parsers                                                             |
|  - Token Bucket Rate Limiter (Capacity: 30, Refill: 2/sec, RFC Headers)                 |
|  - Circuit Breaker Governor (Guards downstream Gemini AI & Heavy Subsystems)           |
+----------------------------+------------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------------------------------------+
|                       EXECUTION & TRAFFIC SHAPING SUBSYSTEM                             |
|                                                                                         |
|  [ SingleFlight Coalescing Engine ]                                                     |
|    - Intercepts identical concurrent source code submissions (Thundering Herd)          |
|    - First request compiles; identical subsequent requests latch onto in-flight promise |
|                                                                                         |
|  [ Content-Addressable L1 LRU Cache ]                                                    |
|    - SHA-256(sourceCode + testcases + problemId) Cache Hit check                        |
|                                                                                         |
|  [ Prioritized Producer-Consumer Job Queue ]                                            |
|    - Priority 1: /submit (Official evaluation against hidden & sample test cases)        |
|    - Priority 2: /run (Standard visible test cases)                                     |
|    - Priority 3: Background tasks (Pre-compilation, warm-up)                            |
|    - Dynamic Backpressure: Trips HTTP 429 if backlog exceeds MAX_QUEUE_LENGTH (30)      |
+----------------------------+------------------------------------------------------------+
                             |
                             v
+-----------------------------------------------------------------------------------------+
|                         C++ NATIVE COMPILER & EXECUTION ENGINE                          |
|                                                                                         |
|  1. AST & Regex Signature Extractor (`signatureExtractor.js`)                           |
|  2. Literal Generator: Serializes JSON inputs to C++ values (`literalGenerator.js`)     |
|  3. Wrapper Generator: Injects `#line 1 "solution.cpp"` directives (`wrapperGenerator.js`)|
|  4. Sandboxed Native Compilation: `g++ -std=c++17 -O2 -o bin src.cpp` (15s timeout)     |
|  5. Isolated Child Process Spawn: `spawn(binPath)` with 5s SIGKILL timeout              |
|  6. Comparison Engine: Normalizes stdout, checks data structures (`comparisonEngine.js`)|
+----------------------------+------------------------------------------------------------+
                             | EventBus Pub/Sub Notifications
                             v
+-----------------------------------------------------------------------------------------+
|                          OBSERVABILITY & TELEMETRY COLLECTOR                            |
|  - Real-time event bus (`job:enqueued`, `job:started`, `job:completed`, `job:failed`)   |
|  - Tracks P50, P90, P99 compilation latencies, Worker Utilization, Cache Hit Ratios      |
|  - Feeds Live System Design Observability Modal (`/system-metrics`)                     |
+-----------------------------------------------------------------------------------------+
```

---

## 2. Frontend-to-Backend Communication & Real-Time SSE

### 2.1. Why Server-Sent Events (SSE) Instead of Raw WebSockets or Polling?
In traditional coding platforms, developers either:
1. **Short Poll (`setInterval` every 1s):** Highly inefficient, floods server with HTTP requests, wastes bandwidth, introduces up to 1-second latency per milestone.
2. **Full-Duplex WebSockets (`ws://`):** Heavyweight state management, requires custom heartbeat/reconnection logic, difficult to load-balance across serverless edge platforms like Vercel or Cloudflare, and over-engineered for a unidirectional progress stream.

**The Solution in MSK Code Arena: Hybrid HTTP POST + Unidirectional SSE Stream**
- When code is submitted, the client issues a standard `POST /run` or `POST /submit`.
- If the submission is resolved immediately (e.g., via L1 SHA-256 Cache hit), the server returns `{ status: "completed", result: { ... } }` directly in the HTTP response.
- If compilation is queued, the server immediately returns HTTP 200 with:
  ```json
  {
    "status": "queued",
    "submissionId": "sub-1728564920123",
    "position": 2,
    "estimatedWait": 450
  }
  ```
- The frontend (`lib/api.ts`) immediately opens an `EventSource`:
  ```typescript
  const sseUrl = `${API_BASE}/submission-status/${submissionId}`;
  const eventSource = new EventSource(sseUrl);
  ```
- The backend streams real-time state updates as the worker advances through the pipeline:
  1. `queued` (displays queue position and estimated wait time)
  2. `compiling` (native g++ is building the binary)
  3. `running_tests` (binary executing test cases)
  4. `comparing_outputs` (asserting outputs against expected results)
  5. `completed` (verdict emitted, connection gracefully closed)
- Upon receiving a terminal state (`completed` or `failed`), the client automatically calls `eventSource.close()`, freeing the HTTP connection.

### 2.2. Frontend Network Client Implementation (`lib/api.ts`)

```typescript
// Excerpt from frontend/lib/api.ts
function handleExecutionResponse(
  data: any,
  onProgress?: (progress: { status: string; position?: number; estimatedWait?: number }) => void
): Promise<any> {
  return new Promise((resolve, reject) => {
    // 1. Instant Cache Hit Path
    if (data.status === 'completed') {
      return resolve(data.result);
    }

    if (data.status !== 'queued') {
      return reject(new Error('Invalid response from server'));
    }

    const { submissionId } = data;
    if (onProgress) {
      onProgress({
        status: 'queued',
        position: data.position,
        estimatedWait: data.estimatedWait,
      });
    }

    // 2. Open Server-Sent Events Stream for live state transitions
    const sseUrl = `${API_BASE}/submission-status/${submissionId}`;
    const eventSource = new EventSource(sseUrl);

    eventSource.onmessage = (event) => {
      try {
        const update = JSON.parse(event.data);
        if (onProgress) onProgress(update);

        if (update.status === 'completed') {
          eventSource.close();
          resolve(update.result);
        } else if (update.status === 'failed') {
          eventSource.close();
          const errData = update.error || {};
          const errObj = new Error(errData.errorMessage || 'Execution failed');
          reject(errObj);
        }
      } catch (err) {
        eventSource.close();
        reject(err);
      }
    };

    eventSource.onerror = () => {
      eventSource.close();
      reject(new Error('Connection to execution service lost'));
    };
  });
}
```

---

## 3. Code Execution Engine & Error Return Pipeline

### 3.1. How Code Submissions are Processed
The execution engine transforms raw user code into a self-contained, high-performance C++ executable.

```
User Code (class Solution)
          |
          v
[ signatureExtractor.js ] -----> Extracts returnType, functionName, paramTypes, paramNames
          |
          v
[ literalGenerator.js ] -------> Serializes testcase strings/arrays into valid C++ code literals
          |
          v
[ wrapperGenerator.js ] -------> Injects #line 1 "solution.cpp", print helpers, driver main()
          |
          v
[ cppCompiler.js: compileCpp ] -> Spawns `g++ -std=c++17 -O2 -o bin_xxx src_xxx.cpp`
          |
          v
[ cppCompiler.js: executeBinary ] Spawns binary, monitors stdout buffer & timeout (5s)
          |
          v
[ comparisonEngine.js ] -------> Normalizes output, compares with expected values
          |
          v
Final Verdict: Accepted (AC) / Wrong Answer (WA) / TLE / Runtime Error (RE) / Compile Error (CE)
```

### 3.2. Solving the Compiler Line-Number Mapping Problem (`#line` Directives)
**The Core Problem:** When an online judge wraps user code with header includes (`#include <bits/stdc++.h>`), printer functions, and a generated `int main()`, a syntax error on line 3 of the user's code might be reported by `g++` as `Line 184: syntax error`. Displaying line 184 to a user who only wrote 15 lines of code ruins the developer experience.

**The Implementation:**
In `backend/compiler/wrapperGenerator.js`, MSK Code Arena uses native C/C++ preprocessor directives:
```cpp
#include <bits/stdc++.h>
using namespace std;

// Print and serialization helpers...

#line 1 "solution.cpp"
// <USER CODE IS INJECTED HERE>

#line 1 "main.cpp"
int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    Solution sol;
    // Generated testcase execution and assertions...
    return 0;
}
```
When `g++` encounters a syntax or type error within the user's snippet, it outputs:
```
solution.cpp:4:12: error: expected ';' before '}' token
```
In `backend/compiler/cppCompiler.js`, regex filters intercept this stderr stream:
```javascript
cleanStderr = cleanStderr.replace(/solution\.cpp:(\d+):(\d+):/g, 'Line $1:');
cleanStderr = cleanStderr.replace(/solution\.cpp:(\d+):/g, 'Line $1:');
```
This guarantees **1:1 line number synchronization** between compiler error feedback and the user's line markers in Monaco Editor.

### 3.3. Comprehensive Execution & Error Handling Matrix

| Verdict / Error Scenario | Detection Mechanism | System Action & Process Lifecycle | User-Facing Feedback |
| :--- | :--- | :--- | :--- |
| **Compilation Error (CE)** | `g++` exits with non-zero code | Intercepts stderr; sanitizes temp file paths; maps `#line` to user lines | Red line diagnostics in Monaco Editor with exact line number and compiler message |
| **Time Limit Exceeded (TLE)** | Execution time exceeds `EXEC_TIMEOUT_MS` (5000ms) | Triggers `SIGKILL` on the child process; clears orphaned file descriptors | `Time Limit Exceeded (5000ms limit reached)` |
| **Segmentation Fault (SIGSEGV)** | Exit code `139` or signal `SIGSEGV` | Intercepts crash signal; frees allocated memory buffers | `Runtime Error (Segmentation Fault - Out of bounds access)` |
| **Output Limit Exceeded (OLE)** | Child process stdout exceeds `MAX_OUTPUT_BYTES` (512 KB) | Immediately kills child process via `SIGKILL` to prevent memory blowup | `Output Limit Exceeded (Stdout truncated)` |
| **Wrong Answer (WA)** | `comparisonEngine.js` detects mismatch between expected & actual | Normalizes whitespace, trailing zeroes, and array/tree representations | Visual diff view highlighting Expected vs. Received output |
| **Accepted (AC)** | All test cases pass assertions | Emits completion event; logs execution time and memory peak | Green badge with run latency (ms) and memory stats |

---

## 4. Database Structure, Pluggable Storage & Query Optimization

### 4.1. Pluggable Storage Adapter (Repository Pattern)
MSK Code Arena uses an abstract repository architecture (`backend/services/storage/storageAdapter.js`) that completely decouples business logic from physical database engines.

```
                    +-----------------------------+
                    |     BaseStorageAdapter      |
                    | (get, set, delete, list...) |
                    +--------------+--------------+
                                   |
         +-------------------------+-------------------------+
         |                                                   |
         v                                                   v
+-------------------------------+                 +-------------------------------+
|    InMemoryStorageAdapter     |                 |   MongoStorageAdapter / Redis |
| - High-speed JS Maps          |                 | - Persistent document store   |
| - Automatic LRU Key Eviction  |                 | - Distributed shared cache    |
| - Background TTL sweep (180s) |                 | - Multi-instance horizontal   |
+-------------------------------+                 +-------------------------------+
```

### 4.2. In-Memory LRU Eviction & TTL Sweep Architecture
```javascript
// Excerpt from backend/services/storage/storageAdapter.js
class InMemoryStorageAdapter extends BaseStorageAdapter {
  constructor({ maxSizePerCollection = 500 } = {}) {
    super();
    this.maxSize = maxSizePerCollection;
    this.collections = new Map(); // collectionName -> Map(id, { val, expiresAt })

    // Periodic sweep for expired keys every 3 minutes
    setInterval(() => this.cleanupExpired(), 180000);
  }

  async set(collection, id, value, ttlMs = 0) {
    const col = this._getCollection(collection);

    if (col.size >= this.maxSize && !col.has(id)) {
      // Evict oldest item (First-In / LRU order guaranteed by JS Map keys iterator)
      const oldestKey = col.keys().next().value;
      col.delete(oldestKey);
    }

    col.set(id, {
      val: value,
      expiresAt: ttlMs > 0 ? Date.now() + ttlMs : null
    });
    return true;
  }
}
```

### 4.3. Data Entities & Schema Design

#### Problems Entity
- `id` (UUIDv4 / Hash) — Primary Key
- `title` (String, indexed)
- `description` (Markdown text)
- `examples` (Array of `{ input: string, output: string, explanation?: string }`)
- `constraints` (Array of strings)
- `cppCode` (Starter boilerplate with method signature)
- `hiddenTestCases` (Array of stress-test inputs and expected outputs)

#### Submissions Entity
- `submissionId` (String, indexed)
- `problemId` (String, Foreign Key)
- `codeHash` (SHA-256 string for deduplication)
- `verdict` (`'Accepted' | 'Wrong Answer' | 'Time Limit Exceeded' | 'Compilation Error' | 'Runtime Error'`)
- `executionTimeMs` (Integer)
- `status` (`'queued' | 'compiling' | 'running_tests' | 'completed' | 'failed'`)
- `createdAt` (Timestamp)

### 4.4. Query Optimization & SHA-256 Content-Addressable Caching
1. **Content-Addressable Execution Cache (`cacheService.js`):**
   - Every execution request is hashed using SHA-256:
     ```javascript
     const cacheKey = crypto
       .createHash('sha256')
       .update(`${problemId}:${code}:${JSON.stringify(testcases)}`)
       .digest('hex');
     ```
   - If the exact same code and test suite was evaluated recently, the result is served directly from cache in `< 1ms`, completely skipping g++ invocation and disk I/O.
2. **Indexed Lookups:** Problems and submissions are indexed by unique IDs, ensuring $O(1)$ retrieval time in the LRU Map and $O(\log N)$ indexed lookups in MongoDB B-Trees.
3. **Memory Bounding:** The storage adapter strictly limits collections to 500 records per category by default, preventing out-of-memory (OOM) errors during extended server uptime.

---

## 5. Concurrency, Queue Backpressure, Rate Limiting & Fault Tolerance

### 5.1. The Thundering Herd Problem & SingleFlight Request Coalescing
**The Scenario:** When an online contest begins, 100 students might run the identical starter solution within the exact same second. Without request coalescing, the server triggers 100 redundant `g++` compilation processes, overwhelming CPU cores and creating a massive bottleneck.

**The SingleFlight Pattern (`backend/utils/singleFlight.js`):**
```javascript
class SingleFlight {
  constructor(name = 'default') {
    this.name = name;
    this.inFlight = new Map(); // key -> Promise
    this.totalCalls = 0;
    this.coalescedCalls = 0;
  }

  async do(key, fn) {
    this.totalCalls++;

    // If an identical operation is already in-flight, latch onto its promise!
    if (this.inFlight.has(key)) {
      this.coalescedCalls++;
      return this.inFlight.get(key);
    }

    const promise = (async () => {
      try {
        return await fn();
      } finally {
        this.inFlight.delete(key); // Automatically remove when finished
      }
    })();

    this.inFlight.set(key, promise);
    return promise;
  }
}
```
**Impact:** If 50 concurrent requests hit the server with identical code, **49 compilations are completely eliminated**. All 49 requests resolve simultaneously when the single compilation completes, reducing CPU load by up to **98%**.

### 5.2. Prioritized Producer-Consumer Queue & Backpressure Governor
The server uses a worker pool architecture (`backend/services/execution/queueService.js`) to decouple incoming HTTP requests from heavy C++ compilation:

1. **Worker Pool Slots:** Configurable via `MAX_CONCURRENT_COMPILATIONS` (defaults to 4 worker slots, matching available CPU hardware cores).
2. **Prioritization Tiers:**
   - **Tier 1 (`SUBMIT`):** Highest priority. Official contest evaluations skip past test runs.
   - **Tier 2 (`RUN`):** Standard priority. Interactive editor runs.
   - **Tier 3 (`BACKGROUND`):** Low priority. System pre-warming and hidden test generation.
3. **Dynamic Backpressure Governor:**
   - If `queue.length >= MAX_QUEUE_LENGTH (30)`, the server immediately trips backpressure:
     ```javascript
     const err = new Error('Server capacity reached. Priority backpressure engaged.');
     err.statusCode = 429;
     return Promise.reject(err);
     ```
   - This prevents memory overflow and cascading queue collapse under DDoS or high load.
4. **Estimated Wait Time Calculation:**
   - Tracks an Exponential Moving Average (EMA) of the last 50 execution durations:
     $$\text{EstimatedWait} = \frac{\text{QueueLength}}{\text{MaxWorkers}} \times \text{AvgDuration}$$
   - This metric is sent directly to the client in the initial queued response.

### 5.3. Token Bucket Traffic Shaping (`tokenBucketLimiter.js`)
Protects API endpoints with a smooth mathematical token bucket:
- **Burst Capacity:** 30 tokens
- **Refill Rate:** 2 tokens/second
- **Emits Standard RFC Headers:**
  - `X-RateLimit-Limit`: Maximum burst capacity (30)
  - `X-RateLimit-Remaining`: Current available tokens
  - `X-RateLimit-Reset`: Unix timestamp when bucket will be fully refilled
  - `Retry-After`: Seconds the client must wait if throttled (HTTP 429)

### 5.4. Circuit Breaker Pattern for Downstream AI (`circuitBreaker.js`)
Protects external dependencies (Google Gemini 2.5 Flash API) from cascading failures:
- **`CLOSED` (Normal):** All problem generation and parsing requests pass through to the Gemini API.
- **`OPEN` (Tripped):** After 3 consecutive network failures or timeouts, the circuit trips to `OPEN`. All incoming requests bypass Gemini with **0ms delay**, falling back instantly to the local regex parser.
- **`HALF_OPEN` (Probe):** After a 15-second cooldown, the circuit allows limited test requests through. If 2 consecutive calls succeed, the circuit automatically heals back to `CLOSED`.

---

## 6. Top Interview Questions & Battle-Tested Answers

### Q1: "How do you prevent a student's malicious C++ code (e.g. `system(\"rm -rf /\")` or fork bomb) from destroying your host server?"
**Answer:**
> "In MSK Code Arena, we isolate execution at multiple boundaries:
> 1. **Time & Output Ceilings:** Process execution is capped at 5 seconds via `spawn` timeout triggers that send an uncatchable `SIGKILL`. The stdout buffer is strictly capped at 512 KB; exceeding it immediately terminates the process.
> 2. **Process Sandboxing:** In production Linux deployments, child processes are spawned within lightweight Linux namespaces or Docker containers with dropped privileges (`chroot`, non-root user, `seccomp` filters restricting dangerous syscalls like `fork`, `execve`, `ptrace`, and `socket`).
> 3. **Preprocessor Sanitization:** Our signature extractor validates method structure before compilation, and wrapper code does not link network or system execution libraries."

### Q2: "Why did you implement SingleFlight request coalescing instead of just relying on a standard Redis cache?"
**Answer:**
> "A standard cache only protects against *sequential* duplicate requests. If a cache key doesn't exist yet and 50 users submit identical code in the exact same millisecond—which frequently happens during coding contests or classroom sessions—all 50 requests experience a *Cache Miss* at the same time. This triggers 50 duplicate compiler spawns, known as the **Thundering Herd** or **Cache Stampede** problem.
> 
> SingleFlight solves this in-flight. The very first request creates a pending Promise and registers it in a map under the SHA-256 hash key. The subsequent 49 requests see that a promise is already in flight for that exact key and attach themselves as listeners. When that one compilation completes, all 50 callers receive the result simultaneously. This cut our redundant CPU compilations by over 90%."

### Q3: "How does the frontend map compilation errors back to the user's code lines when you wrapped their code in custom driver boilerplate?"
**Answer:**
> "We use C++ `#line` preprocessor directives. Right before injecting the user's code into the generated file, our `wrapperGenerator` inserts `#line 1 \"solution.cpp\"`. Immediately after the user code and before our generated `main()` function, we insert `#line 1 \"main.cpp\"`.
> 
> When `g++` compiles the file and detects a syntax error inside the user snippet, the error output explicitly references `solution.cpp:Line:Col` rather than `main.cpp:Line 200`. Our backend compiler interceptor uses regex to sanitize the output into `Line X: error message`, which the Monaco Editor reads to paint red squiggly error markers directly on the user's editor lines."

### Q4: "What happens if the Google Gemini API goes down or experiences rate limits?"
**Answer:**
> "We designed a zero-downtime fallback using a custom **Circuit Breaker** (`circuitBreaker.js`). If Gemini fails or times out 3 consecutive times, the circuit trips to the `OPEN` state. 
> 
> Once OPEN, the system doesn't waste time waiting for external API timeouts. It fast-fails in 0ms directly to our deterministic local Regex problem parser (`parserService.js`), which extracts problem titles, constraints, and standard I/O formats using heuristic pattern matching. After a 15-second recovery cooldown, the breaker transitions to `HALF_OPEN` to probe Gemini's health before restoring full AI functionality."
