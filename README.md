# Master Engineering Portfolio: Comprehensive Project Catalog & Architecture Playbook

> **Repository Location:** `s:\gravity projects\summary of all projects\README.md`  
> **Source Directory:** `S:\gravity projects`  
> **Author:** Maddila Santhosh Kumar  
> **Master Purpose:** Single-source-of-truth reference documentation for all engineering projects. Every project contains its **exact folder name on disk**, **problem statement & purpose**, **complete tech stack**, **operational architecture & request flow**, **key features**, and **pin-to-pin implementation highlights**.

---

## 📑 Master Navigation Index (24 Projects)

| # | Actual Folder Name on Disk | Project Name | Domain / Category | Core Tech Stack |
| :-: | :--- | :--- | :--- | :--- |
| **01** | [`MSK Code Arena - AI-Powered Coding Practice Platform`](#01-msk-code-arena---ai-powered-coding-practice-platform) | **MSK Code Arena** | Full-Stack Online Judge & Sandbox | React 18, Next.js, Node.js, Express, C++17, Gemini AI |
| **02** | [`Hospital Appointment and Resource Management`](#02-hospital-appointment-and-resource-management-caresync-mobile) | **CareSync Mobile & Hospital ERP** | Healthcare & Mobile Systems | Flutter, Dart, Node.js, Express, MongoDB, Python |
| **03** | [`SwitchAI`](#03-switchai---universal-ai-memory--multi-model-router) | **SwitchAI** | Distributed AI Gateway & Memory | Python 3.8+, FastAPI, SQLAlchemy, SQLite, 8 AI Adapters |
| **04** | [`CryptoFlow-IDS-main`](#04-cryptoflow-ids---encrypted-traffic-intrusion-detection-system) | **CryptoFlow-IDS** | Cyber Defense & Security Analytics | C++ (eBPF), Python, Scapy, Random Forest, FastAPI |
| **05** | [`End-to-End Encrypted Chat Platform`](#05-end-to-end-encrypted-chat-platform-cipherlink) | **CipherLink E2EE Platform** | Zero-Knowledge Cryptography | React, Node.js, Web Crypto API (RSA+AES), Face-api.js |
| **06** | [`REST API Security CICD Orchestrator`](#06-rest-api-security-cicd-orchestrator) | **REST API Security CI/CD Gatekeeper** | DevSecOps & Security Gatekeeping | Node.js, Express, Python, Semgrep, OWASP ZAP, Docker |
| **07** | [`Privacy-Preserving Federated Threat Intelligence Protocol`](#07-privacy-preserving-federated-threat-intelligence-protocol-pp-ftip) | **PP-FTIP Protocol** | Decentralized zkML Cybersecurity | Python, PyTorch, zk-SNARKs (ezkl), FedAvg, Cryptography |
| **08** | [`Secure Exam`](#08-secure-exam---enterprise-proctoring-platform) | **Secure Exam Platform** | High-Stakes Online Proctoring | Next.js, Node.js, Electron.js, MongoDB, HMAC-PRNG |
| **09** | [`Food Processing ERP System`](#09-food-processing-erp-system) | **Food Processing ERP System** | Enterprise Supply Chain & Planning | React, Node.js, Express, MongoDB, SAP MM/PP |
| **10** | [`skillSwap`](#10-skillswap-ai---peer-to-peer-skill-exchange) | **SkillSwap AI** | Real-Time Peer Education & WebRTC | React, Vite, Node.js, Express, WebRTC, Socket.IO |
| **11** | [`Srmap-Api-main`](#11-srmap-api-main-srmapi-next) | **Srmapi Next** | Reverse-Engineered University Portal | Next.js 16, TypeScript, MongoDB, FastAPI, ONNX Solver |
| **12** | [`ATS Resume Checker`](#12-ats-resume-checker-resumate-ats) | **ResuMate ATS** | Client-Side NLP & MCP Agent Server | JavaScript, Vite, Tailwind CSS, PDF.js, MCP Protocol |
| **13** | [`Fine Tuned LLM`](#13-fine-tuned-llm-cyberdefend) | **CyberDefend AI Assistant** | Fine-Tuned Security LLM & RAG | Llama 3.1 8B, QLoRA, Qdrant Vector DB, FastAPI |
| **14** | [`AI`](#14-ai-teacher-whiteboard-mvp) | **AI Teacher Whiteboard MVP** | Edge Vision AI & Interactive Canvas | Next.js, Fabric.js, FastAPI, Ollama Local Vision |
| **15** | [`dance baby dance`](#15-dance-baby-dance---ai-choreography--3d-avatar-animation) | **Dance Baby Dance** | Audio-to-3D AI Motion Synthesis | React Three Fiber, Three.js, FastAPI, mint-main Checkpoint |
| **16** | [`ML challenge`](#16-ml-challenge---amazon-ml-challenge-2026) | **Amazon ML Challenge: Entity Resolution**| Competitive Multimodal Machine Learning| Python, PyTorch, Transformers, DeBERTa, LightGBM |
| **17** | [`python-project-chess-with-AI--main`](#17-chessai-web-app) | **ChessAI Web App** | Browser Game Engine & AI Evaluation | Next.js, TypeScript, Chess.js, Stockfish WASM |
| **18** | [`TypeFlow`](#18-typeflow---minimalist-typing-speed-platform) | **TypeFlow** | High-Performance Keystroke Engine | React 18, Vite, Tailwind CSS, SVG Pace Analytics |
| **19** | [`VNC remote connect`](#19-vnc-remote-connect-asynchronous) | **asynchronous (VNC Remote Connect)** | Encrypted Remote Desktop Control | TightVNC 2.8.90, C++, X25519 + AES-256-GCM Relay |
| **20** | [`mouse control`](#20-gesture-control-mouse) | **Gesture Control Mouse** | Computer Vision Human-Computer Interface| Python, MediaPipe, OpenCV, PyAutoGUI, Flask Web HUD |
| **21** | [`LoopingAgent`](#21-loopingagent-lightagent-v1) | **LightAgent V1** | Windows OS Desktop Automation | Python, PyWin32, Tkinter, Win32 Clipboard, Workflow Engine |
| **22** | [`link please`](#22-linkplease-auto-dm---instagram-webhook-automation) | **LinkPlease Auto-DM** | High-Throughput Webhook Processing | Python, FastAPI / Flask, SQLite, Instagram Graph API |
| **23** | [`cyber`](#23-cyber-triage-agent) | **Security Engineering Triage Agent** | Automated Vulnerability Remediation | Python, Anthropic Claude Tool-Use, GitHub REST API |
| **24** | [`web data store`](#24-webdatastore) | **WebDataStore** | Zero-Database Cross-Device Sync | Vanilla HTML5/JS, Node.js, JSON Cloud Storage |

---

## 01. MSK Code Arena - AI-Powered Coding Practice Platform
* **Actual Folder Name on Disk:** `S:\gravity projects\MSK Code Arena - AI-Powered Coding Practice Platform` *(uses Unicode en-dash `–`)*
* **Official Project Name:** MSK Code Arena
* **Domain / Category:** Distributed Online Judge, Compiler Sandbox & AI Synthesis

### Why It Was Made (Problem Statement & Purpose)
Coding platforms like LeetCode and HackerRank force developers into rigid, pre-curated problem formats. When developers want to practice custom problems from college exams, PDFs, or tech blogs, there is no tool to parse the messy text, extract C++ signatures, generate test cases, and provide an instant, sandboxed execution environment with line diagnostics. MSK Code Arena was engineered to solve this through automated AI problem structuring and an in-house C++ online judge sandbox.

### Complete Tech Stack
* **Frontend:** Next.js 14/16 (App Router), React 18, TypeScript, Tailwind CSS, Microsoft Monaco Editor (`@monaco-editor/react`), `react-resizable-panels`.
* **Backend:** Node.js, Express.js (CommonJS & TypeScript modules).
* **Execution Sandbox:** Native `g++` (C++17 / C++20), Linux namespaces / Windows Child Process isolation.
* **AI Integration:** Google Gemini 2.5 Flash API (Structured JSON Schema output).
* **Storage & Caching:** Pluggable Repository (`InMemoryStorageAdapter` with LRU eviction and 180s TTL sweep; plug-and-play MongoDB/Redis adapter).
* **Networking & Observability:** Server-Sent Events (SSE), Token Bucket Rate Limiter, Circuit Breaker, Custom DSA Regression Runner (128 problem test suite).

### How It Operates (Architecture & Request Flow)
1. **Problem Ingestion:** The user pastes raw problem text. The Gemini API or local regex fallback transforms it into structured JSON: title, description, constraints, I/O examples, and starter C++ boilerplate.
2. **Code Authoring:** The developer writes solutions in the Monaco Editor with autocompletion and bracket matching.
3. **Execution Submission (`POST /run` or `POST /submit`):**
   * The backend generates a SHA-256 hash of `code + testcases`. If cached, the result returns in $< 1\text{ms}$.
   * If identical code is already compiling, the **SingleFlight** engine latches the request onto the in-flight Promise.
   * If new, it enqueues the task into a prioritized queue (Tier 1 `SUBMIT` > Tier 2 `RUN` > Tier 3 `BACKGROUND`).
4. **C++ Wrapper Assembly & Sandbox Execution:**
   * `signatureExtractor.js` extracts function arguments and return types.
   * `literalGenerator.js` converts JSON inputs into C++ data structures (`vector`, `ListNode*`, `TreeNode*`).
   * `wrapperGenerator.js` injects `#line 1 "solution.cpp"` directives around user code and builds `main()`.
   * `cppCompiler.js` compiles the binary with `g++ -O2 -std=c++17` (15s timeout) and executes it with a 5s `SIGKILL` timeout and 512 KB stdout buffer limit.
5. **Real-Time SSE Feedback:** The backend streams live milestone updates (`queued` $\rightarrow$ `compiling` $\rightarrow$ `running_tests` $\rightarrow$ `comparing_outputs` $\rightarrow$ `completed`) directly to the browser.

### Key Features & Engineering Highlights
* **SingleFlight Coalescing:** Eliminates cache stampedes during contests; 50 identical submissions trigger only 1 compilation, saving **90%+ CPU cycles**.
* **1:1 Line Number Mapping:** Uses preprocessor `#line` directives so compiler error line numbers map precisely to the user's Monaco Editor lines.
* **Resilient Circuit Breaker:** Trips to `OPEN` after 3 consecutive Gemini API failures, fast-failing to a local regex parser in 0ms without server degradation.

---

## 02. Hospital Appointment and Resource Management (CareSync Mobile)
* **Actual Folder Name on Disk:** `S:\gravity projects\Hospital Appointment and Resource Management` *(Contains `caresync_mobile` Flutter client)*
* **Official Project Name:** CareSync Mobile & Hospital Resource ERP
* **Domain / Category:** Healthcare Systems, Mobile Application Architecture & Hospital ERP

### Why It Was Made (Problem Statement & Purpose)
Outpatient departments face severe operational gridlock: long registration queues, double-booked doctor slots, manual paper prescriptions, and a complete disconnect between clinical consultations and hospital resource stocks (beds, blood bank reserves, imaging equipment). CareSync was engineered as an enterprise-grade mobile and web platform that unifies patient scheduling, doctor workflows, real-time resource allocation, and automated billing ledgers.

### Complete Tech Stack
* **Mobile Client (`caresync_mobile/`):** Flutter 3.x, Dart (Sound Null Safety), Provider State Management (`ChangeNotifier`, `Consumer`), `http` package, `shared_preferences`.
* **Backend:** Node.js, Express.js REST API, Mongoose ODM.
* **Database:** MongoDB Atlas (Cloud Cluster) with embedded resilient local JSON fallback (`database.json`).
* **Web Portal:** Vanilla JavaScript (ES6+), HTML5, CSS3 Tokens.
* **Data Management:** Python analytical scripts for DB migration, capacity forecasting, and seed data.

### How It Operates (Architecture & Request Flow)
1. **Mobile-to-Backend Layer:** The Flutter app connects via a centralized `ApiClient` (`lib/core/network/api_client.dart`) enforcing 15-second timeouts and mapping HTTP codes into custom `AppException` subclasses.
2. **Slot Selection & Booking:**
   * Displays 5 daily slots (`10:00 AM`, `11:00 AM`, `02:00 PM`, `03:00 PM`, `04:00 PM`) excluding the `12:00 PM - 02:00 PM` lunch blackout.
   * Checks slot limits (maximum 3 patients per doctor per slot).
   * Executes a live availability check immediately before `POST /api/appointments` to eliminate booking race conditions.
3. **Clinical Consultation & Resource Automation (`PUT /api/appointments/:id`):**
   * The doctor records diagnosis, prescriptions, and flags inpatient requirements.
   * **Bed Allocation:** If bed admission is checked, decrements available beds by 1, creates an `Allocation` record, and posts a $500 room charge to `FinancialLedger`.
   * **Blood Transfusion:** Deducts units from the specified blood bank type (`A+`, `O-`, etc.), posts a $150/unit charge to `FinancialLedger`, and triggers an automated `PurchaseOrder` if stock drops $\le 10$ units.
   * **Idempotency Protection:** If the doctor amends prescription notes later (`isUpdated: true`), the system updates clinical text while explicitly avoiding duplicate bed/blood inventory deductions.

### Key Features & Engineering Highlights
* **Strict Concurrency Guards:** Multi-layer slot protection combining client pre-flight checks, server atomic validation, and compound uniqueness checks.
* **Tri-State Resilient UI:** Flutter views handle `LoadingView` (custom shimmer), `EmptyView` (clinical illustrations), and `ErrorView` (interactive retry) cleanly.
* **Zero-Downtime Database Resilience:** The Node.js backend automatically falls back to an embedded JSON database if MongoDB Atlas connection drops.

---

## 03. SwitchAI - Universal AI Memory & Multi-Model Router
* **Actual Folder Name on Disk:** `S:\gravity projects\SwitchAI`
* **Official Project Name:** SwitchAI (*"One memory. Many AI models."*)
* **Domain / Category:** Distributed AI Gateway, Context Engineering & Multi-LLM Orchestration

### Why It Was Made (Problem Statement & Purpose)
AI users suffer from severe vendor lock-in. When working in ChatGPT or Claude, context, architectural decisions, and project facts are trapped inside vendor silos. Moving a complex coding conversation from GPT-4o to Claude 3.5 Sonnet requires re-explaining requirements from scratch. Furthermore, when an AI provider experiences rate limits (HTTP 429) or outages, workflows break. SwitchAI eliminates lock-in by decoupling conversation memory from AI providers, enabling mid-thread model switching with zero context loss.

### Complete Tech Stack
* **Backend:** Python 3.8+, FastAPI (ASGI async event loop / Starlette), Uvicorn, Pydantic v2.
* **Database & Security:** SQLAlchemy ORM, SQLite (`switchai.db`), Fernet 32-byte symmetric encryption for API credentials.
* **Frontend:** React 18, TypeScript, Vite, Tailwind CSS, Lucide Icons, Framer Motion.
* **Integrated LLM Adapters (8 Engines):** Google Gemini, OpenAI GPT, Anthropic Claude, DeepSeek, Groq LPU, Mistral AI, Cohere, Local Ollama.
* **Offline Knowledge Engine:** Embedded 28-domain grounded RAG engine with acronym expansion.
* **Testing:** Pytest with in-memory SQLite (`StaticPool`) and `unittest.mock.patch` failure injection suites.

### How It Operates (Architecture & Request Flow)
1. **Universal Memory Layer:** Memory items are categorized into semantic tags: `goal`, `fact`, `decision`, `constraint`, `preference`.
2. **Context Passport Assembly:** When switching models mid-conversation, the backend bundles all structured memories, file summaries, and recent turns into a normalized `ContextPackage`.
3. **Smart Task Classification & Routing:** Analyzes incoming prompts using heuristic keyword classification (`coding`, `reasoning`, `long_context`, `summarization`, `fast_response`, `rag_offline`) and routes to the optimal model based on policy (`Quality First`, `Speed First`, `Cost First`, `Balanced`).
4. **Sliding Circuit Breaker (`services/fallback.py`):**
   * If a provider encounters 3 consecutive failures (HTTP 429 Rate Limits, 504 Timeouts, 503 Outages), the circuit trips to `OPEN`.
   * For the next **30 seconds**, all requests bypass that provider in **0ms**, automatically failing over to the next healthy provider in the fallback chain.
   * If all cloud APIs fail, it falls back gracefully to the embedded **28-Domain Offline RAG Engine**.

### Key Features & Engineering Highlights
* **Zero Client-Side Keys:** All vendor keys are encrypted at rest with Fernet and never transmitted to the browser.
* **Free Live Web Search:** Built-in keyless DuckDuckGo search with Wikipedia REST API fallback, extracting web facts into SQLite memory.
* **Thorough Test Suite:** Pytest suites verify automated failover across Anthropic $\rightarrow$ Gemini $\rightarrow$ OpenAI under simulated 429 and 504 outages.

---

## 04. CryptoFlow-IDS - Encrypted Traffic Intrusion Detection System
* **Actual Folder Name on Disk:** `S:\gravity projects\CryptoFlow-IDS-main`
* **Official Project Name:** CryptoFlow-IDS
* **Domain / Category:** Network Intrusion Detection (NIDS), In-Kernel Packet Filtering & AI Cyber Defense

### Why It Was Made (Problem Statement & Purpose)
Over 95% of enterprise traffic is encrypted with TLS 1.3, HTTPS, and QUIC/UDP. Threat actors exploit this by exfiltrating proprietary databases and running command-and-control (C2) beacons inside encrypted tunnels. Traditional Deep Packet Inspection (DPI) firewalls fail because payloads are unreadable ciphertexts, while SSL-decryption proxies break privacy and degrade throughput. CryptoFlow-IDS was built to detect encrypted malicious exfiltrations packet-by-packet in real-time **without breaking encryption or violating user privacy**.

### Complete Tech Stack
* **Kernel & Sniffing Layer:** C / eBPF socket filter (`ebpf_sniffer.c` compiled via BCC on Linux), Scapy & Npcap on Windows (`windows_detector.py`).
* **Core Runtime:** Python 3.8+ Multiprocessing (`multiprocessing.Process`), threading mutex locks.
* **Machine Learning:** Scikit-Learn (`RandomForestClassifier`, 100 estimators), Joblib, Pandas, NumPy.
* **Automated Mitigation:** Windows Defender Firewall (`netsh advfirewall`), Linux `iptables`.
* **Cyber HUD & APIs:** FastAPI, WebSockets (streaming 60 FPS telemetry), SQLite (`cryptoflow.db`).
* **Forensics:** Automated PCAP dumper (`incidents/*.pcap`), MaxMind / REST GeoIP & ASN threat intelligence.

### How It Operates (Architecture & Request Flow)
1. **Packet Capture & GIL Bypass:** The sniffer runs inside a dedicated OS worker process, bypassing Python's Global Interpreter Lock (GIL) so CPU-intensive 256-bin byte histogram math does not block the WebSocket UI.
2. **Side-Channel Feature Extraction:**
   * Discards packets with payloads $< 200$ bytes (ACKs, SYNs).
   * Calculates Shannon Entropy on raw bytes: $H(X) = -\sum p(x) \log_2 p(x)$.
   * Inspects UDP ports 443/8443 for RFC 9000 QUIC fixed-bit markers: `(payload[0] & 0x40) != 0`.
   * Triage filters: Plaintext traffic ($H < 4.5$) and standard TLS record headers (`0x14 - 0x17, 0x03`) are marked SAFE instantly.
3. **AI Classification & Tri-Condition Threat Gating:** Evaluates the `[Entropy, PacketSize, DstPort]` feature vector. An alert fires only when:
   $$\text{RF Prediction} == 1 \quad\text{AND}\quad \text{Entropy} > 7.2 \quad\text{AND}\quad \text{Confidence} > 0.75$$
4. **Automated Mitigation & Forensics:** Spawns an inbound BLOCK rule on Windows/Linux firewalls, logs the incident in SQLite, enriches the IP with GeoIP/ASN, and writes offending packets into Wireshark `.pcap` files.

### Key Features & Engineering Highlights
* **High-Accuracy Detection:** Achieves **$99.82\%$ test accuracy** and **$0.9994$ ROC-AUC** across 10,000 calibrated flow samples.
* **100x Mitigation Caching:** Under packet floods, an atomic in-memory cache guarantees strictly ONE `netsh` invocation per malicious IP, dropping mitigation latency from **6,983ms to 69.59ms**.

---

## 05. End-to-End Encrypted Chat Platform (CipherLink)
* **Actual Folder Name on Disk:** `S:\gravity projects\End-to-End Encrypted Chat Platform`
* **Official Project Name:** CipherLink
* **Domain / Category:** Zero-Knowledge Cryptography, Real-Time Messaging & Biometric Authentication

### Why It Was Made (Problem Statement & Purpose)
Centralized messaging platforms (Slack, Discord, unencrypted web chats) store user communications in plaintext or encrypt data only in transit (TLS), leaving messages vulnerable to database leaks, insider threats, and subpoena seizures. CipherLink was designed with a **Zero-Knowledge Architecture** where the server functions as a blind relay: all message encryption and decryption happens purely inside the user's browser, ensuring absolute conversational privacy.

### Complete Tech Stack
* **Frontend:** React (Vite), Tailwind CSS (Glassmorphism theme), Lucide Icons.
* **Cryptographic Engine:** Web Crypto API (Client-Side Native Crypto).
  * **Asymmetric:** RSA-OAEP (2048-bit keys) for user identity and key encapsulation.
  * **Symmetric:** AES-256-GCM for ephemeral per-message encryption.
* **Biometric Authentication:** `face-api.js` (TensorFlow) for 68-point facial landmark vector extraction.
* **Backend:** Node.js, Express.js, Zod (Schema Validation), Bcrypt, JSON Web Tokens (JWT).
* **Database & Email:** MongoDB Atlas (Mongoose ODM), Nodemailer with Gmail SMTP (6-digit hashed OTPs with 10-minute self-destruct).

### How It Operates (Architecture & Request Flow)
1. **Key Generation on Registration:** The browser generates an RSA-OAEP key pair via the Web Crypto API. The public key is stored on MongoDB; the private key stays strictly encrypted in client local storage.
2. **Hybrid Message Encryption:**
   * Sender generates a cryptographically random 256-bit AES key.
   * Encrypts the plaintext message payload using AES-256-GCM.
   * Encrypts the AES key using the recipient's RSA public key.
   * Transmits the encrypted ciphertext bundle to the Express server.
3. **Decryption at Recipient:** The recipient receives the bundle, decrypts the AES key using their local RSA private key, and decrypts the ciphertext payload into viewable text. The server database stores only unreadable ciphertext blobs.
4. **Biometric Face Login:** The user looks at their webcam. `face-api.js` computes a 128-dimensional facial landmark embedding, encrypts it, and verifies it against the user's registered vector profile.
5. **Enterprise Admin Sudo Mode:** Administrative operations require re-authentication (Face or Password). User account deletion triggers a **Wipe Protocol**, physically overwriting encrypted chat payloads with system placeholders for privacy compliance.

### Key Features & Engineering Highlights
* **True Zero-Knowledge:** Neither database administrators nor intercepted network logs can decipher messages.
* **AI Biometric Login:** Passwordless access using local client-side facial landmark tensor matching.
* **Ephemeral OTP Security:** Verification OTPs are hashed with bcrypt before saving to MongoDB, preventing database exposure.

---

## 06. REST API Security CICD Orchestrator
* **Actual Folder Name on Disk:** `S:\gravity projects\REST API Security CICD Orchestrator`
* **Official Project Name:** REST API Security CI/CD Gatekeeper & DevSecOps Testbed
* **Domain / Category:** DevSecOps Automation, API Security & Automated Policy Enforcement

### Why It Was Made (Problem Statement & Purpose)
Modern engineering teams deploy software continuously, but application security testing is frequently an afterthought—conducted manually days before release or after breaches occur. The REST API Security CI/CD Orchestrator demonstrates the **"Shift-Left" DevSecOps methodology**: embedding automated security scanners directly into the CI/CD pipeline to detect vulnerabilities, evaluate enterprise risk thresholds, and programmatically break builds (`exit 1`) before code reaches production.

### Complete Tech Stack
* **Target Application:** Node.js, Express.js, MongoDB / In-Memory Mock (Mongoose), JWT, Bcryptjs.
* **CI/CD Platform:** GitHub Actions (`.github/workflows/devsecops-pipeline.yml`).
* **Security Scanners:**
  * **SCA (Software Composition Analysis):** NPM Audit & OWASP Dependency-Check (identifying vulnerable packages).
  * **SAST (Static Application Security Testing):** Semgrep (`.semgrep.yml` custom AST rules detecting BOLA, NoSQL injection, hardcoded secrets).
  * **DAST (Dynamic Application Security Testing):** OWASP ZAP (Containerized dynamic baseline attack proxy).
* **Policy Gatekeeper Engine:** Custom Python 3.8+ engine (`scripts/security_gate.py`, 467 lines).
* **Containerization:** Docker (running OWASP ZAP in CI/CD).

### How It Operates (Architecture & Request Flow)
1. **Pipeline Trigger:** A developer pushes code or opens a Pull Request.
2. **Parallel Security Scanning:**
   * **Stage 1 (SCA):** Scans `package.json` and lockfiles for known CVEs.
   * **Stage 2 (SAST):** Semgrep executes custom rules checking for unauthenticated endpoints, Broken Object Level Authorization (BOLA), and unescaped MongoDB queries.
   * **Stage 3 (DAST):** Boots a live ephemeral staging instance of the Node.js API and launches containerized OWASP ZAP to fuzz endpoints, inspect headers, and probe for CORS/XSS flaws.
3. **Security Gate Policy Evaluation (`security_gate.py`):**
   * Ingests JSON reports from Semgrep, OWASP ZAP, and NPM Audit.
   * Normalizes disparate vulnerability formats into standard severities (`CRITICAL`, `HIGH`, `MEDIUM`, `LOW`).
   * Evaluates Policy-as-Code rules: If any finding is `CRITICAL` or `HIGH`, the gatekeeper logs full remediation steps, publishes a formatted GitHub Job Summary, and exits with code `1`, blocking deployment.

### Key Features & Engineering Highlights
* **Intentionally Vulnerable Lab Endpoints:** Contains controlled OWASP API Top 10 vulnerabilities (BOLA/IDOR on `/api/users/:id`, NoSQL Injection on `/api/login`, Broken Authentication) for empirical verification.
* **Automated Pull Request Blocking:** Eliminates manual security reviews for routine flaws by automating fail/pass gatekeeping directly in GitHub Actions.

---

## 07. Privacy-Preserving Federated Threat Intelligence Protocol (PP-FTIP)
* **Actual Folder Name on Disk:** `S:\gravity projects\Privacy-Preserving Federated Threat Intelligence Protocol`
* **Official Project Name:** PP-FTIP Protocol
* **Domain / Category:** Decentralized Machine Learning, Zero-Knowledge Proofs (zkML) & Threat Intelligence

### Why It Was Made (Problem Statement & Purpose)
Financial institutions, hospitals, and critical infrastructure operators face identical cyber threats, but privacy regulations (GDPR, HIPAA, GLBA) prohibit sharing raw network logs or customer telemetry. Standard Federated Learning solves privacy by sharing only model gradients ($\Delta W$), but introduces an existential flaw: **Model Poisoning Attacks**. Malicious or compromised participants can upload sabotaged weights to blind the collective AI model. PP-FTIP solves this via **Verifiable Federated Learning (VFL)** using Zero-Knowledge Proofs.

### Complete Tech Stack
* **Language & Frameworks:** Python 3.8+, PyTorch, NumPy, Scikit-Learn.
* **Zero-Knowledge Prover / zkML:** `ezkl` (zero-knowledge SNARK engine for deep learning models), ONNX export pipeline.
* **Datasets:** NSL-KDD Network Intrusion Dataset, UNSW-NB15, synthetically partitioned non-IID SOC telemetry.
* **Execution Environment:** Local Linux / Windows CLI & Google Colab Cloud Runner (`colab_runner.ipynb`).

### How It Operates (Architecture & Request Flow)
1. **Global Model Initialization:** A central SOC aggregator broadcasts global neural network parameters $W^{(t)}$ to all enrolled member SOCs (e.g. Bank SOC, Hospital SOC).
2. **Local Enclave Training:** Each SOC trains the model locally on private telemetry. Raw packets never leave the organization’s secure perimeter.
3. **Cryptographic Proof Generation (zk-SNARK / zkML):**
   * The local prover computes gradient deltas $\Delta W_i = W_i^{(t+1)} - W^{(t)}$.
   * Calculates the Euclidean norm: $\|\Delta W_i\|_2 = \sqrt{\sum (\Delta W_{i,j})^2}$.
   * Enforces the mathematical invariant: $\|\Delta W_i\|_2 \le \gamma$ (where threshold $\gamma = 3.50$).
   * Generates a cryptographic ZK proof $\pi_i$ attesting that weights were derived from valid training data without exceeding the boundary norm.
4. **Byzantine-Robust Verification & Aggregation:**
   * The central aggregator cryptographically verifies proof $\pi_i$ in milliseconds.
   * Honest updates ($w_1, w_2$) are merged using Byzantine-resilient Federated Averaging (`FedAvg`).
   * Poisoned updates ($w_3$) with backdoors or invalid proofs are instantly rejected with 100% accuracy, safeguarding the global AI intrusion detection model.

### Key Features & Engineering Highlights
* **Guaranteed Privacy + Verifiable Integrity:** Combines differential privacy guarantees of Federated Learning with mathematical non-interactive zero-knowledge proofs.
* **Byzantine Fault Tolerance:** Completely neutralizes gradient inversion attacks, data poisoning, and Trojan insertion from rogue nodes.

---

## 08. Secure Exam - Enterprise Proctoring Platform
* **Actual Folder Name on Disk:** `S:\gravity projects\Secure Exam`
* **Official Project Name:** Enterprise Online Examination & Proctoring Platform
* **Domain / Category:** EdTech Security, Anti-Cheat Kiosk Systems & Resilient Assessments

### Why It Was Made (Problem Statement & Purpose)
High-stakes online certification and university exams are plagued by student cheating (screen sharing, unauthorized hotkeys, copy-pasting, multiple devices) and network instability in developing regions. Many remote assessment tools crash or lose student answers if Wi-Fi drops. Secure Exam was engineered as an enterprise three-tier online examination platform featuring deterministic question randomization, machine hardware binding, and offline-tolerant monotonic answer synchronization.

### Complete Tech Stack
* **Backend:** Node.js, Express.js REST API, MongoDB (Mongoose) with automatic `MongoMemoryServer` fallback.
* **Frontend:** Next.js 14+ (App Router), React, Tailwind CSS.
* **Desktop Kiosk Client:** Electron.js (Lightweight Windows Fullscreen Kiosk).
* **Security & Randomization:** HMAC-SHA256 Cryptographic PRNG, Hardware UUID fingerprinting, JWT authentication.
* **Timezone Engine:** UTC database timestamps with automatic Indian Standard Time (IST, UTC+05:30) conversion.

### How It Operates (Architecture & Request Flow)
1. **Access Key & Hardware Binding:** When a student enters their unique access key, `POST /api/auth/verify-key` binds the key to the machine's hardware UUID. Subsequent attempts to log in from other laptops are blocked with `403 HARDWARE_MISMATCH_VIOLATION`.
2. **Deterministic Question Randomization:**
   * Seeds an internal PRNG using `HMAC-SHA256(examId + accessKey)`.
   * Guarantees that the candidate receives a repeatable question subset matching difficulty quotas (e.g. 30% Easy, 50% Medium, 20% Hard) while shuffling option display orders (A, B, C, D) to defeat glance copying.
3. **Monotonic Answer Synchronization (`syncSeq`):**
   * As the student answers questions, the Electron/Next.js frontend caches responses locally.
   * Sync payloads carry an incrementing sequence number (`syncSeq`).
   * The backend rejects out-of-order delayed packets, preventing slow network connections from overwriting newer answers.
4. **Proctor Monitoring & Auto-Scoring:** Live dashboard displays candidate status, hardware integrity, and flags tab-switching violations. Submissions trigger automated scoring with negative marking rules.

### Key Features & Engineering Highlights
* **Offline Grace Periods:** Candidates experiencing connectivity drops continue answering questions in the local encrypted cache and sync back within a 15-minute configurable grace window.
* **Zero-Setup Database Fallback:** Automatically switches to an in-memory Mongo engine if cloud DB credentials are not configured.

---

## 09. Food Processing ERP System
* **Actual Folder Name on Disk:** `S:\gravity projects\Food Processing ERP System`
* **Official Project Name:** Food Processing ERP System (SAP MM & SAP PP Architecture)
* **Domain / Category:** Enterprise Resource Planning (ERP), Manufacturing & Supply Chain

### Why It Was Made (Problem Statement & Purpose)
Food manufacturing companies manage complex, highly perishable supply chains. Errors in procurement, raw ingredient shortages, or lack of Bill of Materials (BOM) synchronization cause production stoppages and spoilage. Inspired by enterprise SAP modules (**SAP MM - Materials Management** and **SAP PP - Production Planning**), this system was designed to provide mid-sized food processing enterprises with a streamlined MERN-stack platform to automate procurement, inventory control, and recipe-driven production runs.

### Complete Tech Stack
* **Frontend:** React (Vite / CRA), React Router, Tailwind CSS, Recharts (Analytical Graphs & Throughput Visualizations).
* **Backend:** Node.js, Express.js REST API.
* **Database:** MongoDB Atlas, Mongoose ODM.
* **Security:** JSON Web Tokens (JWT) & Role-Based Access Control (RBAC: Admin, Procurement Manager, Production Supervisor, Warehouse Operator).

### How It Operates (Architecture & Request Flow)
1. **Materials Management (SAP MM Flow):**
   * Manages supplier directories, generates Purchase Orders (POs), and logs incoming deliveries via Goods Receipt Notes (GRN).
   * Automatically updates warehouse stocks: tracks Current Stock, Reserved Stock (allocated for active batches), and Available Stock.
2. **Production Planning (SAP PP Flow):**
   * **Bill of Materials (BOM):** Formulates precise recipes (e.g., 500 kg Flour, 50 kg Sugar, 20 kg Butter to produce 1,000 packs of Biscuits).
   * **Material Requirement Planning (MRP):** When a production manager schedules a batch, the MRP engine scans current inventory. If raw material is deficient, it immediately flags shortages and generates procurement alerts.
3. **Batch Execution & Inventory Deduction:**
   * Releasing a production order locks raw materials in "Reserved Stock".
   * Completing the batch decrements raw materials and atomically increments finished goods in warehouse stock.

### Key Features & Engineering Highlights
* **Automated Low-Stock Thresholds:** Visual indicators and automated alerts notify procurement teams when raw ingredients dip below safe buffer levels.
* **Full Audit Trail:** Every Goods Receipt and Production Run generates an immutable audit record tied to the user ID.

---

## 10. SkillSwap AI - Peer-to-Peer Skill Exchange
* **Actual Folder Name on Disk:** `S:\gravity projects\skillSwap`
* **Official Project Name:** SkillSwap AI
* **Domain / Category:** Real-Time EdTech, WebRTC Video Collaboration & Community Networks

### Why It Was Made (Problem Statement & Purpose)
Traditional online tutoring is expensive and transactional. Many students and self-taught developers possess valuable skills (e.g. Python, Graphic Design, Spanish) but lack funds to pay professional tutors. SkillSwap AI was built as a barter-economy education platform: users teach a skill they know in exchange for learning a skill they want, connecting over peer-to-peer WebRTC video calls, live chats, dynamic leaderboards, and skill assessments.

### Complete Tech Stack
* **Frontend:** React (Vite), Tailwind CSS, Lucide Icons, Socket.IO Client, Simple-Peer / WebRTC.
* **Backend:** Node.js, Express.js, Socket.IO (WebSocket Signaling Server), WebRTC STUN/TURN handling.
* **Database:** MongoDB Atlas, Mongoose ODM (Schemas for Users, Messages, Meetings, Assessments, Reviews).
* **Deployment:** Vercel (Frontend), Render (Backend API & WebSockets).

### How It Operates (Architecture & Request Flow)
1. **Skill Matching & Discovery:** Users create profiles listing "Skills I Can Teach" and "Skills I Want to Learn". The system matches complementary users.
2. **WebRTC Signaling via Socket.IO:**
   * When two users agree to a session, the Node.js server acts as a WebRTC signaling relay, exchanging SDP offers, answers, and ICE candidates.
   * Once signaling completes, a direct peer-to-peer encrypted audio/video stream is established between the two browsers.
3. **In-Session Collaboration:** Users communicate via real-time WebSocket chat and structured whiteboard notes during the call.
4. **Skill Credits & Gamification:** Completing a teaching session awards learning credits, increments leaderboard rankings, and unlocks post-session peer review forms.

### Key Features & Engineering Highlights
* **Low-Latency P2P Video:** Bypasses central media servers by routing raw video/audio frames directly between client peers via WebRTC.
* **Role-Based Governance:** Includes administrative moderation tools (`makeAdmin.js`) to oversee session logs and enforce community guidelines.

---

## 11. Srmap-Api-main (Srmapi Next)
* **Actual Folder Name on Disk:** `S:\gravity projects\Srmap-Api-main`
* **Official Project Name:** Srmapi Next
* **Domain / Category:** Full-Stack University Portal, Web Scraping & Automated CAPTCHA Solving

### Why It Was Made (Problem Statement & Purpose)
The official university student portal (`student.srmap.edu.in`) is slow, non-responsive on smartphones, frequently crashes during attendance checks, and requires manual CAPTCHA solving on every login. Srmapi Next is a high-performance alternative web portal built for students. It securely proxies student credentials, solves visual CAPTCHAs via an embedded machine learning model, scrapes and normalizes student data, and caches results in MongoDB for instant mobile access.

### Complete Tech Stack
* **Frontend & Gateway:** Next.js 16 (App Router), React, TypeScript, Tailwind CSS.
* **Backend API:** Next.js Route Handlers (`app/api/*`).
* **CAPTCHA Solver Microservice:** Python 3.10+, FastAPI, ONNX Runtime (running an optimized visual CNN CAPTCHA recognition model).
* **Database & Cache:** MongoDB Atlas (`college_db` for academic records, attendance logs, and student discussion forums).
* **Scraping Engine:** Cheerio, Node.js HTTP/HTTPS Client managing persistent `JSESSIONID` cookie jars.

### How It Operates (Architecture & Request Flow)
1. **Student Login (`POST /api/auth/login`):**
   * The Next.js Route Handler requests the raw CAPTCHA image from the SRM portal.
   * Forwards the image buffer to the local FastAPI/ONNX microservice, which infers and returns the alphanumeric CAPTCHA text in $< 50\text{ms}$.
   * Submits student credentials and solved CAPTCHA to the university portal, capturing the session `JSESSIONID`.
2. **Scraping & Data Normalization:**
   * Dispatches parallel requests to fetch timetable, attendance percentages, course marks, and fee balances.
   * Uses Cheerio to parse messy legacy HTML tables into clean, typed JSON objects.
3. **Caching & UI Rendering:**
   * Caches normalized student data in MongoDB to allow instant offline viewing without re-scraping.
   * The React client renders modern dark-mode attendance dials, course progress bars, and timetable alerts.

### Key Features & Engineering Highlights
* **Zero-Friction AI CAPTCHA Bypass:** Eliminates manual CAPTCHA entry by executing lightweight ONNX vision models.
* **Session Persistence:** Maintains student session cookies securely in browser storage, only re-authenticating when the remote session expires.

---

## 12. ATS Resume Checker (ResuMate ATS)
* **Actual Folder Name on Disk:** `S:\gravity projects\ATS Resume Checker`
* **Official Project Name:** ResuMate ATS
* **Domain / Category:** Natural Language Processing, Career Tech & Model Context Protocol (MCP)

### Why It Was Made (Problem Statement & Purpose)
Modern corporations filter over 75% of job applicants using automated Applicant Tracking Systems (ATS) like Workday and Taleo. Job seekers often have their resumes rejected due to unparsed formatting, missing keywords, or poor section headings without knowing why. ResuMate ATS was engineered as a high-performance, 100% client-side ATS analysis tool that inspects resumes, compares them against target job descriptions, scores them out of 100, and exposes analytical tools directly to AI coding assistants via native **Model Context Protocol (MCP)** integration.

### Complete Tech Stack
* **Frontend:** Modern JavaScript (ES6+), Vite, Tailwind CSS, Lucide Icons, Glassmorphism design system.
* **Client-Side Document Parsing:** `pdfjs-dist` (parsing PDF streams), `mammoth.js` (extracting `.docx` XML trees) purely inside the browser without cloud uploads.
* **Agent Integration:** Model Context Protocol (MCP) Server (`mcp-server.js`) built using `@modelcontextprotocol/sdk`.

### How It Operates (Architecture & Request Flow)
1. **Document Ingestion:** The user drags-and-drops a PDF, DOCX, or raw text resume along with a target Job Description (JD).
2. **Text Parsing & Normalization:** `pdfjs-dist` or `mammoth.js` extracts raw text strings directly in browser memory, guaranteeing total user privacy.
3. **Weighted ATS Scoring Engine (0 - 100 Scale):**
   * **Keyword & Skill Match (45 pts):** Tokenizes text, matches against technical dictionaries (Languages, Frameworks, Cloud, Databases), and checks frequency.
   * **Section Headers & Structure (25 pts):** Audits required blocks (Contact, Experience, Education, Skills, Projects).
   * **Impact & Action Verbs (15 pts):** Regex scans for quantified impact metrics (%, $, numbers) and active verbs (*Architected, Spearheaded, Engineered*).
   * **Formatting & Word Count (15 pts):** Evaluates optimal length (400 - 1,000 words) and warns against unparsed graphic tables.
4. **Interactive Dashboard:** Displays animated circular SVG score gauges, green matched skill pills, red missing keyword chips, and prioritized recommendations.
5. **Native MCP Server:** Exposes tools (`analyze_resume`, `match_job_description`) allowing AI agents (Antigravity, Claude Desktop) to invoke ATS scoring programmatically.

### Key Features & Engineering Highlights
* **100% Client-Side Privacy:** Sensitive personal contact info and resumes are parsed locally in browser RAM without external cloud uploads.
* **Native Model Context Protocol (MCP):** Connects as a tool server for AI pair programmers to evaluate resumes directly from chat IDEs.

---

## 13. Fine Tuned LLM (CyberDefend)
* **Actual Folder Name on Disk:** `S:\gravity projects\Fine Tuned LLM`
* **Official Project Name:** CyberDefend - Defensive Cybersecurity LLM & RAG Assistant
* **Domain / Category:** Specialized Generative AI, RAG Architectures & Cyber Defense

### Why It Was Made (Problem Statement & Purpose)
General-purpose frontier LLMs (ChatGPT, Claude) often refuse defensive cybersecurity questions due to over-zealous safety alignment filters, or hallucinate syntax for specialized network commands (`nmap`, `Wireshark`, `Suricata`). Security Operations Center (SOC) analysts need an AI assistant specialized strictly in defensive operations: generating NIST SP 800-61 incident response playbooks, mapping CVEs to MITRE ATT&CK techniques, and producing correct syntax for forensic terminal commands. CyberDefend was built to provide this through fine-tuning and local RAG.

### Complete Tech Stack
* **Model Fine-Tuning:** Unsloth, QLoRA (4-bit quantized Low-Rank Adaptation) fine-tuned on Llama 3.1 8B Instruct / Qwen2.5 7B.
* **Vector Database:** Embedded Qdrant (Disk-backed local vector store `./data/qdrant_db`).
* **Embeddings:** `BAAI/bge-small-en-v1.5` running on CPU-optimized normalized tensors.
* **Knowledge Sources:** MITRE ATT&CK STIX 2.1 datasets, NVD CVE databases, NIST SP 800-61 Rev 2 incident playbooks.
* **API Layer:** Python 3.10+, FastAPI REST endpoints, Streamlit / Cyber Web HUD.

### How It Operates (Architecture & Request Flow)
1. **Threat Intel Ingestion:** Ingests structured JSON/STIX data from MITRE ATT&CK, NIST guidelines, and CVE feeds, chunking them into semantic paragraphs.
2. **Embedding & Storage:** `bge-small-en-v1.5` embeds text chunks into dense 384-dimensional vectors stored in the local disk-backed Qdrant DB.
3. **Retrieval & Grounded Synthesis:**
   * When an analyst queries a threat (e.g. *"How do I mitigate CVE-2024-3094 SSH backdoor?"*), the engine executes cosine similarity search in Qdrant.
   * Injects top-k relevant playbooks and MITRE technique IDs into the fine-tuned LLM system prompt.
   * Generates structured incident triage playbooks with exact terminal commands (`nmap`, `tcpdump`, `Sysmon`).

### Key Features & Engineering Highlights
* **Low-Resource Local Execution:** Optimized to run inference and vector retrieval on an 8GB RAM developer laptop using quantized models and CPU embeddings.
* **Zero-Hallucination Playbooks:** Incorporates provenance badging, citing exact NIST playbook sections and MITRE technique IDs.

---

## 14. AI (AI Teacher Whiteboard MVP)
* **Actual Folder Name on Disk:** `S:\gravity projects\AI`
* **Official Project Name:** AI Teacher Whiteboard MVP
* **Domain / Category:** Edge Vision AI, Interactive Canvas & Autonomous Tutoring

### Why It Was Made (Problem Statement & Purpose)
Traditional online learning tools are passive: students watch videos or type math formulas into clumsy text boxes. When working through complex math equations, circuit diagrams, or physics sketches, students naturally think by hand-drawing on paper. AI Teacher Whiteboard was built to turn hand-drawn sketches into an active, 1:1 tutoring experience: a student draws or writes by hand, pauses for 2.5 seconds, and a locally running AI vision model reads the handwriting and animates step-by-step guidance right onto the whiteboard—**with zero cloud APIs and 100% localhost privacy**.

### Complete Tech Stack
* **Frontend:** Next.js (Node.js 18+), React, Fabric.js (HTML5 Canvas vector drawing engine), Tailwind CSS.
* **Backend:** Python 3.11+, FastAPI REST API (`backend/main.py`).
* **Local Vision Inference:** [Ollama](https://ollama.com) running open-weights local vision models (`moondream`, `llava`, `llama3.2-vision`).
* **Animation Engine:** Custom SVG/Canvas stroke animator rendering progressive handwriting strokes.

### How It Operates (Architecture & Request Flow)
1. **Interactive Drawing:** The student draws math equations, physics diagrams, or code sketches on the Fabric.js digital canvas.
2. **Debounced Pause Detection:** The client detects when drawing stops for **2.5 seconds**, automatically calculates the dirty bounding box, and crops a lightweight PNG image buffer.
3. **Local Vision Inference (`POST /api/analyze`):**
   * FastAPI receives the image buffer and dispatches it to the local Ollama instance running `moondream` or `llama3.2-vision`.
   * The vision model interprets the handwriting, solves the problem step-by-step, and outputs structured JSON containing explanation text and coordinate stroke markers.
4. **Canvas Teaching Animation:** The Next.js frontend reads the coordinate vectors and animates animated handwriting strokes directly beside the student’s work, mimicking a live human tutor writing on the board.

### Key Features & Engineering Highlights
* **100% Localhost & Free:** Uses zero paid cloud APIs (OpenAI, Anthropic) by executing open vision models entirely on device.
* **Dirty Bounding Box Cropping:** Instead of processing full 4K canvas resolutions, the canvas exports only the active drawn region, speeding up inference by 4x.

---

## 15. Dance Baby Dance - AI Choreography & 3D Avatar Animation
* **Actual Folder Name on Disk:** `S:\gravity projects\dance baby dance`
* **Official Project Name:** Dance Baby Dance
* **Domain / Category:** Multimodal Generative AI, 3D Web Graphics & Audio-to-Motion Synthesis

### Why It Was Made (Problem Statement & Purpose)
Creating realistic 3D character animations for games, virtual influencers, and metaverse platforms is exceptionally labor-intensive, requiring expensive motion-capture suits or weeks of manual keyframing. Dance Baby Dance was built as an automated audio-to-motion animation suite: an artist uploads any music audio track, a specialized deep learning choreography model (`mint-main`) synthesizes 3D skeletal dance choreography matching rhythm and tempo, and a React Three Fiber scene renders the dancing 3D avatar in real time.

### Complete Tech Stack
* **Frontend:** React, Vite, Three.js, React Three Fiber (R3F), Drei, Tailwind CSS.
* **Backend Orchestrator:** Node.js, Express.js (Audio forwarding & stream orchestration).
* **AI Engine Microservice (`backend-ai`):** Python 3.7 (Miniconda), FastAPI, TensorFlow 1.x / 2.x, Librosa (Audio feature extraction).
* **AI Model Checkpoint:** `mint-main` (`mint_fact_b32_v3_2_2021-05-06` 1.44 GB pre-trained audio-to-motion checkpoint).

### How It Operates (Architecture & Request Flow)
1. **Audio Ingestion:** The user uploads a `.wav` or `.mp3` music track through the React interface.
2. **Acoustic Feature Extraction:** Express forwards the audio to the FastAPI AI service. Librosa processes the track, extracting acoustic beat frames, chromagrams, and onset envelopes.
3. **Choreography Synthesis (`mint-main`):**
   * The deep generative model processes the audio embeddings and outputs continuous 3D skeletal joint rotation matrices (SMPL / BVH bone positions).
   * The AI service executes the model inside an isolated subprocess to prevent TensorFlow graph state memory corruption across consecutive songs.
4. **3D Avatar Retargeting:** The synthesized bone rotation frames are returned to the React Three Fiber frontend, which retargets the skeletal transforms onto custom GLTF/GLB 3D humanoid avatars, rendering smooth 60 FPS choreographies.

### Key Features & Engineering Highlights
* **Beat-Synchronized Motion:** Dance movements mathematically match musical tempo changes, drops, and pauses.
* **Isolated Process Execution:** Prevents legacy TensorFlow memory leaks by executing batch inference in decoupled OS worker processes.

---

## 16. ML Challenge - Amazon ML Challenge 2026
* **Actual Folder Name on Disk:** `S:\gravity projects\ML challenge`
* **Official Project Name:** Amazon ML Challenge: Business Entity Resolution
* **Domain / Category:** Competitive Machine Learning, Natural Language Processing & Tabular Data Science

### Why It Was Made (Problem Statement & Purpose)
In large-scale e-commerce catalogs (such as Amazon), millions of product listings, merchant entities, and brand names are submitted with typos, abbreviations, divergent formats, and missing attributes. Resolving whether two disparate product records represent the exact same real-world business entity (Record Linkage / Entity Resolution) is critical for catalog deduplication, search ranking, and pricing parity. This repository houses the competition model engineered for the Amazon ML Challenge 2026.

### Complete Tech Stack
* **Language & Core Libraries:** Python 3.8+, PyTorch, Hugging Face Transformers, Datasets.
* **Machine Learning Models:** DeBERTa-v3, LightGBM, CatBoost, TF-IDF Vectorizers.
* **Feature Engineering:** Levenshtein Distance, Jaro-Winkler string similarity, token overlap ratios, fuzzy text matching.
* **Evaluation Framework:** Macro F0.5 Score optimization, K-Fold Cross Validation.

### How It Operates (Architecture & Request Flow)
1. **Data Preprocessing & Cleaning:** Normalizes messy e-commerce text strings, lowercases names, expands vendor abbreviations, and removes special syntax characters.
2. **Candidate Blocking & Pairwise Generation:** Because comparing every record against every other record is $O(N^2)$, the pipeline uses TF-IDF and locality-sensitive hashing (LSH) to generate high-probability candidate match pairs.
3. **Hybrid Feature Engineering:**
   * Textual similarity scores (Jaccard, Levenshtein, Cosine on dense DeBERTa embeddings).
   * Attribute matching on brand, category, address, and numerical product specifications.
4. **Ensemble Classification:** A gradient-boosted decision tree ensemble (LightGBM + CatBoost) trained on pairwise similarity vectors outputs the final binary match decision (`1` for same entity, `0` for distinct).

### Key Features & Engineering Highlights
* **High Validation Macro F0.5:** Achieved **0.9711 Validation Macro F0.5**, heavily penalizing false positives to preserve e-commerce catalog integrity.
* **Scalable Blocking Strategy:** Drastically reduced computational search space from billions of pairs down to manageable candidate sets.

---

## 17. ChessAI Web App
* **Actual Folder Name on Disk:** `S:\gravity projects\python-project-chess-with-AI--main`
* **Official Project Name:** ChessAI Web App
* **Domain / Category:** Web Game Development, Board Game AI & WebAssembly (WASM)

### Why It Was Made (Problem Statement & Purpose)
Online chess platforms typically require heavy server-side infrastructure running Stockfish binaries, resulting in server hosting costs and network latency between moves. The ChessAI Web App was designed as a premium, responsive chess platform that runs **100% client-side in the browser with zero backend requirements**, allowing users to play against an intelligent AI engine, evaluate move advantages, and inspect blunder history offline.

### Complete Tech Stack
* **Frontend:** Next.js (React 18), TypeScript, Tailwind CSS, Lucide Icons.
* **Chess Rules Engine:** `chess.js` (validating legal moves, checkmate, stalemate, and en-passant).
* **AI Evaluation Engine:** Stockfish Chess Engine compiled to WebAssembly (WASM) via Web Workers.
* **UI Board Components:** `react-chessboard` with custom SVG piece assets and sound effects.

### How It Operates (Architecture & Request Flow)
1. **Local Board State:** The React client tracks the board using `chess.js` via Forsyth-Edwards Notation (FEN).
2. **Asynchronous Stockfish Evaluation:**
   * When the human moves, the board updates instantly and fires an event to a dedicated Web Worker running Stockfish WASM.
   * Running Stockfish in a Web Worker keeps the main UI thread at 60 FPS with zero sluggishness or frame freezes.
3. **AI Move Generation:** Stockfish analyzes the FEN position to configurable depth limits, evaluates centipawn advantages, and returns the optimal engine move.
4. **Game Analytics:** Displays an interactive live evaluation bar, move notation log, and captured piece counters.

### Key Features & Engineering Highlights
* **100% Serverless & Offline:** Zero cloud dependencies; can be downloaded and played on an airplane without internet access.
* **Non-Blocking WASM Workers:** Heavy minimax / alpha-beta pruning calculations execute in background browser threads.

---

## 18. TypeFlow - Minimalist Typing Speed Platform
* **Actual Folder Name on Disk:** `S:\gravity projects\TypeFlow`
* **Official Project Name:** TypeFlow
* **Domain / Category:** Frontend Performance Engineering, Client-Side Analytics & Gamified Learning

### Why It Was Made (Problem Statement & Purpose)
Typing speed practice platforms like Monkeytype are often cluttered with ads or require cloud account registrations. Many do not provide granular, stroke-by-stroke pace analytics to identify the exact words where a typist hesitates. TypeFlow was engineered as a modern, lightning-fast, minimalist client-side typing practice web application that provides real-time WPM metrics, SVG pace acceleration graphs, 20-week activity heatmaps, and offline persistence.

### Complete Tech Stack
* **Frontend Framework:** React 18, Vite, Tailwind CSS, Lucide Icons, Glassmorphism aesthetic.
* **Analytics & Graphs:** Pure mathematical SVG charting (Zero heavy external charting library dependencies).
* **Storage:** HTML5 LocalStorage for offline test history and daily streak tracking.
* **Passage Generation:** Curated multi-domain text corpora (Quotes, Code Snippets, Standard English, Numbers & Punctuation).

### How It Operates (Architecture & Request Flow)
1. **Keystroke Capture & Precision Timing:**
   * Attaches low-level `onKeyDown` listeners to measure delta milliseconds between consecutive key presses.
   * Compares input character by character, dynamically coloring correct characters green and mistakes red.
2. **Pace & Metric Calculation:**
   * Calculates **Raw WPM** ($\frac{\text{All Characters}}{5 \times \text{Minutes}}$) and **Net WPM** (adjusted for uncorrected errors).
   * Generates real-time SVG pace curves plotting WPM acceleration and deceleration across the entire paragraph.
3. **Activity Heatmap & Streaks:**
   * Records completed tests into a 20-week GitHub-style activity calendar grid in LocalStorage.
   * Tracks consecutive active practice day streaks with interactive hover tooltips.

### Key Features & Engineering Highlights
* **Zero-Dependency SVG Visualizations:** Renders high-performance, dynamic line charts and circular progress gauges using raw SVG paths without adding runtime bundle weight.
* **Smooth Glassmorphism UI:** Neon accent palette designed for distraction-free, long-duration typing sessions.

---

## 19. VNC Remote Connect (asynchronous)
* **Actual Folder Name on Disk:** `S:\gravity projects\VNC remote connect`
* **Official Project Name:** asynchronous (VNCremoteconnect)
* **Domain / Category:** Systems Programming, Remote Desktop Infrastructure & Network Security

### Why It Was Made (Problem Statement & Purpose)
Standard VNC (Virtual Network Computing) software transmits unencrypted framebuffers or requires complex router port forwarding (opening port 5900), which is completely blocked on university Wi-Fi, corporate firewalls, and Carrier-Grade NAT (CGNAT) networks. Commercial alternatives like TeamViewer or AnyDesk are proprietary, enforce connection time limits, and pose privacy risks. `asynchronous` was engineered as a high-speed, military-grade end-to-end encrypted remote desktop platform that effortlessly traverses campus firewalls without port forwarding.

### Complete Tech Stack
* **Core VNC Engine:** TightVNC 2.8.90 (GPL v2) headless server and viewer integration.
* **Cryptography:** X25519 Elliptic-Curve Diffie-Hellman (ECDH) key exchange, SHA-256 HKDF directional key derivation, AES-256-GCM authenticated AEAD encryption.
* **Relay Architecture:** Zero-Knowledge TLS Relay running on outbound HTTPS ports (8443 / 8444).
* **Process Obfuscation:** Cleanly registered as `asynchronous.exe` / `asynchronous` in Windows Task Manager.
* **Packaging:** Lightweight 0.96 MB portable zip & 32 MB standalone distribution with embedded runtime.

### How It Operates (Architecture & Request Flow)
1. **Permanent Unattended Access:** Each laptop maintains a permanent Unique Device ID and password, active by default with zero confirmation popups.
2. **Outbound Reverse Loopback Bridge:**
   * Keeps the TightVNC server strictly isolated from external networks (`127.0.0.1` loopback only).
   * Both host and viewer establish standard outbound TLS connections to the relay on ports 8443/8444, traversing strict university firewalls and NATs.
3. **End-to-End Cryptographic Handshake:**
   * Host and viewer perform an ephemeral X25519 key exchange through the blind relay.
   * Derives directional 256-bit AES-GCM session keys.
   * All mouse events, keystrokes, and RFB desktop framebuffer chunks are encrypted before leaving the machine; the central relay acts as a blind pipe and cannot view the desktop.
4. **Auto-Update & Versioning:** Automatically queries GitHub Releases for updates, notifying the user without ever breaking connections between mismatched client versions.

### Key Features & Engineering Highlights
* **Traverses College Wi-Fi & CGNAT:** Uses outbound reverse tunneling over standard TLS ports, eliminating the need for public IP addresses or router port forwarding.
* **Military-Grade E2EE:** Protects desktop screen streams with authenticated AES-256-GCM encryption.

---

## 20. Gesture Control Mouse
* **Actual Folder Name on Disk:** `S:\gravity projects\mouse control`
* **Official Project Name:** Gesture Control Mouse
* **Domain / Category:** Computer Vision, Human-Computer Interaction (HCI) & Automation

### Why It Was Made (Problem Statement & Purpose)
Individuals with motor impairments or professionals operating in sterile/hands-busy environments (surgeons, industrial technicians, presenters) cannot use physical hardware mice. The Gesture Control Mouse was built as an accessible, contactless computer mouse controller: it tracks hand movements via a standard laptop webcam, converts finger gestures into mouse coordinates and click events, and provides a real-time web dashboard for live parameter calibration.

### Complete Tech Stack
* **Computer Vision:** Python 3.8+, Google MediaPipe (21 3D Hand Landmark Detection), OpenCV (`cv2`).
* **OS Automation:** PyAutoGUI (Dispatching native Windows cursor movements, clicks, and scrolls).
* **Live Web HUD:** Flask / Lightweight HTTP server rendering live camera feeds and gesture diagnostics.
* **Mathematical Filtering:** Exponential Moving Average (EMA) and Kalman filtering to eliminate hand jitter.

### How It Operates (Architecture & Request Flow)
1. **Webcam Video Capture:** OpenCV captures frames at 30 FPS from the webcam (`DirectShow` / DSHOW backend).
2. **Hand Landmark Extraction:** MediaPipe identifies 21 3D skeletal landmarks (fingertips, knuckles, wrist coordinates).
3. **Gesture Classification:**
   * **Cursor Movement:** Tracks index fingertip $(x, y)$, mapping coordinate space to Windows screen resolution ($1920 \times 1080$).
   * **Left Click:** Measures Euclidean distance between index tip (Landmark 8) and thumb tip (Landmark 4). When distance dips below threshold, it dispatches a native left-click.
   * **Right Click:** Pinch between middle fingertip (Landmark 12) and thumb tip.
   * **Scroll Mode:** Raising both index and middle fingers activates vertical scrolling.
4. **Jitter Smoothing:** Passes raw coordinates through an exponential moving average filter to ensure buttery smooth cursor navigation without jittery jumping.

### Key Features & Engineering Highlights
* **Live Interactive Web Dashboard:** Users can open a browser page to visualize bounding boxes and tune sensitivity sliders in real time.
* **Low CPU Overhead:** Highly optimized vector math runs at $< 10\%$ CPU utilization on standard laptops.

---

## 21. LoopingAgent (LightAgent V1)
* **Actual Folder Name on Disk:** `S:\gravity projects\LoopingAgent`
* **Official Project Name:** LightAgent V1 - LoopingAgent
* **Domain / Category:** Robotic Process Automation (RPA), Desktop Automation & Workflow Engines

### Why It Was Made (Problem Statement & Purpose)
Knowledge workers waste countless hours on repetitive desktop tasks: copying rows from Excel sheets, pasting them into legacy enterprise desktop software, clicking buttons, and repeating the cycle hundreds of times. Commercial RPA tools (UiPath, Automation Anywhere) are heavy, expensive, and require dedicated enterprise servers. LightAgent V1 was built as an ultra-lightweight, zero-bloat Windows automation agent that ties together window management, clipboard manipulation, and workflow scripting in under 10 MB.

### Complete Tech Stack
* **Language & Runtime:** Python 3.8+ (Multithreaded architecture).
* **OS Integration:** PyWin32 (`win32gui`, `win32con`, `win32api`), PyAutoGUI.
* **Clipboard Engine:** Native Windows Win32 Clipboard API wrapper (`clipboard_manager.py`).
* **UI & Logging:** Python Tkinter GUI with thread-safe live log streaming (`AgentLogger`).
* **Configuration:** JSON configuration and workflow definition files (`config.json`, `config.py`).

### How It Operates (Architecture & Request Flow)
1. **Window Targeting:** `window_manager.py` inspects active Windows OS window handles (HWND), matches window titles, and brings target applications to the foreground.
2. **Clipboard Management:** `clipboard_manager.py` hooks directly into the Windows clipboard memory buffer, reading and writing tabular data without race conditions or character corruption.
3. **Workflow Runner (`workflow.py`):**
   * Reads configured step sequences: Focus Window $\rightarrow$ Copy Cell $\rightarrow$ Alt-Tab $\rightarrow$ Paste $\rightarrow$ Submit $\rightarrow$ Loop.
   * Executes calibrated delay timers to allow slow enterprise software to render before firing keyboard strokes.
4. **GUI Controller (`agent.py`):** Ties the automation runner to an interactive desktop GUI with pause, emergency stop (`Esc` key hook), and step-by-step progress logging.

### Key Features & Engineering Highlights
* **Thread-Safe Architecture:** Keeps the desktop GUI responsive during long-running batch automation loops using dedicated Python worker threads.
* **Zero External Dependencies:** Built with pure Python and native Windows APIs, requiring zero complex installation steps.

---

## 22. LinkPlease Auto-DM - Instagram Webhook Automation
* **Actual Folder Name on Disk:** `S:\gravity projects\link please`
* **Official Project Name:** LinkPlease Auto-DM Service
* **Domain / Category:** Social Media Automation, High-Throughput Webhook Processing & Fault Tolerance

### Why It Was Made (Problem Statement & Purpose)
Content creators on Instagram frequently prompt followers: *"Comment PRICE and I will DM you the purchase link"*. Manually sending thousands of direct messages is impossible, and naive automation scripts crash or get banned when viral posts generate 10,000 comments in a few minutes. LinkPlease was built as a resilient, production-ready webhook processing service that ingests Instagram comment webhooks, enforces rate limits, deduplicates duplicate events, and automates DMs with automatic retry reconcilers.

### Complete Tech Stack
* **Language & Framework:** Python 3.8+, FastAPI / Flask REST API (`database.py`, `app.py`).
* **Database:** SQLite (`linkplease.db`) with hard unique constraint schemas.
* **Resilience Patterns:** Background worker queues, Idempotency tables, Exponential Backoff, Reconciliation poller.
* **Integration:** Meta Graph API (Instagram Webhook specifications).

### How It Operates (Architecture & Request Flow)
1. **Rule Configuration (`POST /rules`):** Creators define trigger rules (e.g., `keyword: "PRICE"`, `dm_message: "Here is your 20% discount link: https://..."`).
2. **Instant 200 Webhook Ingestion (`POST /webhook`):**
   * When Instagram dispatches comment events, the webhook handler returns HTTP 200 **immediately in $< 10\text{ms}$** to prevent Meta timeout drops.
   * Drops the event into an internal processing queue.
3. **Deduplication & Idempotency Guards:**
   * Checks `ProcessedEvent` table using `event_id` primary key to prevent duplicate processing on webhook re-deliveries.
   * Enforces a database-level `UNIQUE(rule_id, user_id)` constraint on the `SentDM` table, guaranteeing that a user who comments 5 times receives strictly **ONE DM**.
4. **Rate-Limited Dispatcher & Reconciler:**
   * Enforces Instagram's 10 requests / 60 seconds rate limit.
   * Transient 500 errors trigger retries with bounded exponential backoff.
   * A background reconciler thread polls delivery status every 30 seconds to catch and re-dispatch silent delivery drops.

### Key Features & Engineering Highlights
* **Rock-Solid Idempotency:** Completely immune to duplicate deliveries and spam comments via database unique constraints.
* **Instant Acknowledgement:** Decouples HTTP ingestion from message delivery to comply with strict webhook latency SLAs.

---

## 23. Cyber Triage Agent
* **Actual Folder Name on Disk:** `S:\gravity projects\cyber`
* **Official Project Name:** Security Engineering Triage Agent
* **Domain / Category:** Autonomous Security Agents, Vulnerability Management & AI Tool-Use

### Why It Was Made (Problem Statement & Purpose)
Vulnerability scanners (Snyk, Trivy, Dependabot) output massive JSON reports with hundreds of findings. Security engineers waste hours manually reviewing scanner logs, assessing exploitability, and creating GitHub Issues for developers to fix. The Cyber Triage Agent was engineered as an autonomous security engineering agent that ingests raw scanner reports, uses Anthropic Claude with **tool-use capabilities** to reason about vulnerability severities, and automatically opens prioritized GitHub Issues with actionable remediation steps.

### Complete Tech Stack
* **Language:** Python 3.8+.
* **LLM Reasoning & Tool-Use:** Anthropic Claude API (`anthropic` Python SDK).
* **VCS Integration:** PyGithub (`github` SDK) interacting with the GitHub REST API.
* **Configuration:** `python-dotenv` managing `ANTHROPIC_API_KEY` and `GITHUB_TOKEN`.
* **Input Data:** `scanner_output.json` (Structured vulnerability scanner telemetry).

### How It Operates (Architecture & Request Flow)
1. **Telemetry Ingestion:** `triage_agent.py` reads raw vulnerability findings from `scanner_output.json`.
2. **Agentic Reasoning Loop:**
   * Formats each vulnerability into a prompt for Claude, defining available tools: `create_github_issue(title, body, labels)`.
   * Claude analyzes CVSS scores, affected packages, exploit availability, and production exposure.
3. **Autonomous Action Execution:**
   * **High & Critical Severities:** The agent autonomously invokes the `create_github_issue` tool, creating a beautifully formatted issue with CVE description, affected package versions, and exact upgrade commands (`npm update` / `pip install`).
   * **Medium & Low Severities:** Logged to console output for internal review without cluttering the developer issue tracker.

### Key Features & Engineering Highlights
* **Autonomous Tool-Use (Function Calling):** The LLM autonomously constructs and dispatches API calls to GitHub without hardcoded parsing logic.
* **Noise Reduction:** Filters out minor scanner noise to keep engineering teams focused strictly on high-impact vulnerabilities.

---

## 24. WebDataStore
* **Actual Folder Name on Disk:** `S:\gravity projects\web data store`
* **Official Project Name:** WebDataStore
* **Domain / Category:** Real-Time Web Utilities, Lightweight Data Synchronization & P2P Data

### Why It Was Made (Problem Statement & Purpose)
Developers frequently need a dead-simple way to copy IP addresses, temporary passwords, and configuration snippets between laptops, phones, and collaborators without setting up complex databases, running Docker containers, or logging into heavy cloud dashboards. WebDataStore was built as a zero-setup, cross-device auto-saving web utility with live side-by-side synchronized profiles.

### Complete Tech Stack
* **Frontend:** Vanilla HTML5, Modern CSS3 Tokens, Vanilla JavaScript (ES6+).
* **Local Backend (Optional):** Node.js, Express.js (`server.js`), local JSON persistence (`data.json`).
* **Cloud Sync:** Embedded REST cloud synchronization pipeline with QR code sharing.

### How It Operates (Architecture & Request Flow)
1. **Dual Profile Dashboard:** Renders split-screen live profiles for simultaneous multi-user data sharing.
2. **Debounced Instant Auto-Save:** Input listeners trigger asynchronous auto-save events as the user types or pastes, eliminating manual "Submit" buttons.
3. **Background Sync Polling:** Continuously syncs state across connected phones and laptops, updating fields live when modified from another device.
4. **1-Click Mobile QR Handoff:** Generates dynamic QR codes allowing users to scan their phone camera and immediately open the synchronized session on mobile.

### Key Features & Engineering Highlights
* **Zero Database Required:** Operates immediately in any browser with zero installation, configuration strings, or database servers.
* **Instant Device Handoff:** One-click clipboard copy helpers and dynamic QR code generation.

---

## 🛠️ Maintenance, Updates & Future Project Playbook

Whenever you build a new project or update an existing one in `S:\gravity projects`, update this single master file:
1. **Adding a New Project:** Insert a new row in the [Master Navigation Index](#-master-navigation-index-24-projects) and add a dedicated numbered section following the standard format:
   * **Actual Folder Name on Disk**
   * **Official Project Name & Category**
   * **Why It Was Made (Problem Statement & Purpose)**
   * **Complete Tech Stack**
   * **How It Operates (Architecture & Request Flow)**
   * **Key Features & Engineering Highlights**
2. **Updating Existing Projects:** Directly edit the corresponding numbered section in this file.
3. **Version Control:** Commit and push updates to your GitHub documentation repository:
   ```bash
   git add README.md
   git commit -m "Update project architecture and documentation"
   git push origin main
   ```
