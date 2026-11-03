# Curated Resume Engineering Projects: Architecture & Technical Playbook

> **Author:** Maddila Santhosh Kumar  
> **GitHub Profile:** [https://github.com/Santhosh939s](https://github.com/Santhosh939s)  
> **Master Purpose:** Dedicated, production-grade reference playbook containing the **top 15 flagship engineering projects** curated specifically for resume presentation and technical interviews. Every project features its verified **Live Link**, **GitHub Repository**, **exact disk location**, **problem statement & purpose**, **complete tech stack**, **end-to-end operational architecture**, and **pin-to-pin technical highlights**.

---

## 📑 Curated Project Index (15 Flagship Projects)

| # | Project Name | Domain / Category | Live Demo Link | GitHub Repository |
| :-: | :--- | :--- | :--- | :--- |
| **01** | [**MSK Code Arena**](#01-msk-code-arena) | Full-Stack Online Judge & Sandbox | [🌐 Live Application](https://msk-code-arena.vercel.app) | [🔗 GitHub Repo](https://github.com/Santhosh939s/MSK-Code-Arena) |
| **02** | [**CareSync Mobile & Hospital ERP**](#02-caresync-mobile--hospital-erp) | Healthcare ERP & Mobile Systems | [🌐 Live Web Portal](https://care-sync-hospital-appointment-reso.vercel.app/) | [🔗 GitHub Repo](https://github.com/Santhosh939s/CareSync-HospitalAppointmentResourceManagementSystem) |
| **03** | [**SwitchAI**](#03-switchai) | Distributed AI Gateway & Memory | *(Offline Architecture)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/SwitchAI) |
| **04** | [**CryptoFlow-IDS**](#04-cryptoflow-ids) | Encrypted Traffic Intrusion Detection | *(Kernel / Socket Level)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/CryptoFlow-IDS) |
| **05** | [**REST API Security CICD Orchestrator**](#05-rest-api-security-cicd-orchestrator) | DevSecOps & Security Gatekeeping | *(CI/CD Pipeline)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/REST-API-Security-CICD-Orchestrator) |
| **06** | [**PP-FTIP Protocol**](#06-privacy-preserving-federated-threat-intelligence-protocol-pp-ftip) | Decentralized zkML Threat Intel | *(Cryptographic Enclave)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/Privacy-Preserving-Federated-Threat-Intelligence-Protocol) |
| **07** | [**SkillSwap AI**](#07-skillswap-ai) | Real-Time EdTech & WebRTC Video | *(Deployed WebRTC)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/SkillSwap-AI) |
| **08** | [**Amazon ML Challenge: Entity Resolution**](#08-amazon-ml-challenge-entity-resolution) | Multimodal ML & Tabular Science | [🌐 Kaggle Benchmark Notebook](https://www.kaggle.com/code/jayakrishna639/notebook0a2f5b7b64) | [🔗 GitHub Repo](https://github.com/Santhosh939s/AllProjectsSummary) |
| **09** | [**ChessAI Web App**](#09-chessai-web-app) | Web Game Engine & Minimax Search | [🌐 Live Game Engine](https://chesswithai-seven.vercel.app/) | [🔗 GitHub Repo](https://github.com/Santhosh939s/ChessWithAI) |
| **10** | [**TypeFlow (Team Project)**](#10-typeflow-team-project) | Frontend Performance & SVG Analytics | [🌐 Live Platform](https://typeflow-six.vercel.app/) | [🔗 GitHub Repo](https://github.com/Santhosh939s/TypeFlow) |
| **11** | [**Gesture Control Mouse**](#11-gesture-control-mouse) | Computer Vision & Touchless HCI | *(Local Hardware Video Stream)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/GestureControlMouse) |
| **12** | [**LoopingAgent (LightAgent V1)**](#12-loopingagent-lightagent-v1) | Robotic Process Automation (RPA) | *(Native Windows Subsystem)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/LoopingAgent) |
| **13** | [**Offensive AI & Automated API Pentesting**](#13-offensive-ai--automated-api-penetration-testing-ongoing) | Autonomous Offensive AI Research | *(Kaggle GPU Lab Enclave)* | [🔗 GitHub Repo](https://github.com/Santhosh939s/OffensiveAIandAutonomousAPIPenetrationTesting) |
| **14** | [**Rapid Crisis Response System (CrisisLink)**](#14-rapid-crisis-response-system-crisislink) | Enterprise EOC & Geolocation Dispatch | [🌐 Live EOC Dashboard](https://rapid-crisis-response-two.vercel.app) | [🔗 GitHub Repo](https://github.com/Santhosh939s/Rapid-Crisis-Response.git) |
| **15** | [**CipherLink E2EE Platform**](#15-cipherlink-end-to-end-encrypted-messaging-platform) | Zero-Knowledge Cryptography & Chat | [🌐 Live Secure Messaging](https://end-to-end-flame.vercel.app/) | [🔗 GitHub Repo](https://github.com/Santhosh939s/End-to-end) |

---

## 01. MSK Code Arena
* **Live Demo:** [https://msk-code-arena.vercel.app](https://msk-code-arena.vercel.app)
* **GitHub Repository:** [https://github.com/Santhosh939s/MSK-Code-Arena](https://github.com/Santhosh939s/MSK-Code-Arena)
* **Actual Folder Name on Disk:** `S:\gravity projects\MSK Code Arena - AI-Powered Coding Practice Platform`
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

## 02. CareSync Mobile & Hospital ERP
* **Live Web Portal:** [https://care-sync-hospital-appointment-reso.vercel.app/](https://care-sync-hospital-appointment-reso.vercel.app/)
* **GitHub Repository:** [https://github.com/Santhosh939s/CareSync-HospitalAppointmentResourceManagementSystem](https://github.com/Santhosh939s/CareSync-HospitalAppointmentResourceManagementSystem)
* **Actual Folder Name on Disk:** `S:\gravity projects\Hospital Appointment and Resource Management` *(Contains `caresync_mobile` Flutter client)*
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
1. **Mobile-to-Backend Layer:** The Flutter app connects via a centralized `ApiClient` enforcing 15-second timeouts and mapping HTTP codes into custom `AppException` subclasses.
2. **Slot Selection & Booking:**
   * Displays 5 daily slots (`10:00 AM`, `11:00 AM`, `02:00 PM`, `03:00 PM`, `04:00 PM`) excluding the `12:00 PM - 02:00 PM` lunch blackout.
   * Checks slot limits (maximum 3 patients per doctor per slot).
   * Validates duplicate appointments using an index over `(patientId, doctorId, date, slot)`.
3. **Clinical Consultation & ERP Integration:**
   * Doctors review pending queues and prescribe medications, lab tests, and hospital admission.
   * When admitted, the backend executes an atomic `$inc: { occupied: 1, available: -1 }` operation on the department's physical bed count.
4. **Resilient Local Persistence:** If cloud connectivity is lost, the server switches seamlessly to an embedded local file adapter (`database.json`), preventing hospital intake halts.

### Key Features & Engineering Highlights
* **Zero-Downtime Database Resilience:** Embedded fallback database engine maintains uninterrupted hospital admissions during WAN disconnects.
* **Strict Slot Concurrency Guards:** Multi-layer database validation ensures doctors are never overbooked.

---

## 03. SwitchAI
* **GitHub Repository:** [https://github.com/Santhosh939s/SwitchAI](https://github.com/Santhosh939s/SwitchAI)
* **Actual Folder Name on Disk:** `S:\gravity projects\SwitchAI`
* **Domain / Category:** Distributed AI Gateway, Multi-LLM Orchestration & Prompt Routing

### Why It Was Made (Problem Statement & Purpose)
Enterprises and developers face extreme vendor lock-in when building LLM applications. An API outage (e.g., OpenAI rate limit 429) or sudden price hike can halt critical operations. Furthermore, users cannot switch between models mid-conversation without losing their accumulated chat context. SwitchAI was engineered as a high-availability AI routing gateway that unifies 7 cloud LLMs and local inference engines behind a single interface, featuring persistent contextual memory and automated zero-downtime circuit breaking.

### Complete Tech Stack
* **Backend:** Python 3.10+, FastAPI (Asynchronous ASGI framework), Uvicorn, SQLAlchemy ORM.
* **Databases:** SQLite (Local state) / PostgreSQL (Production), Pydantic v2 schemas.
* **LLM Adapters:** Google Gemini, OpenAI GPT-4o, Anthropic Claude 3.5 Sonnet, DeepSeek-V3, Groq (LLaMA-3), Mistral Large, Cohere Command R+, Local Ollama.
* **Security & Cryptography:** `cryptography.fernet.Fernet` (AES-128-CBC with SHA-256 HMAC for client API key encryption).
* **Information Retrieval:** Built-in 28-Domain keyword & heuristic RAG engine (`rag.py`).

### How It Operates (Architecture & Request Flow)
1. **Request Intake:** Client submits a prompt and conversation ID to `POST /chat/completions`.
2. **Context Enrichment & RAG:** `rag.py` checks query tokens against 28 technology domains, extracting relevant knowledge snippets.
3. **Dynamic Router & Circuit Breaker Check (`fallback.py`):**
   * If the chosen model is healthy, the request routes to its adapter.
   * If the model fails 3 times (`FAILURE_THRESHOLD = 3`), the circuit breaker trips to `OPEN` for 30 seconds (`COOLDOWN_SECONDS = 30.0`).
   * The router automatically cascades the prompt to the next available tier without returning errors to the user.
4. **Universal Memory Synchronization:** Once completed, user and assistant messages are stored under an invariant schema, allowing the user to switch to a different LLM on the next turn while preserving full conversational history.

### Key Features & Engineering Highlights
* **Zero-Downtime Fallback:** Sliding-window circuit breaker prevents cascading microservice failures during third-party API downtime.
* **Fernet Encryption at Rest:** API keys are never stored in cleartext.

---

## 04. CryptoFlow-IDS
* **GitHub Repository:** [https://github.com/Santhosh939s/CryptoFlow-IDS](https://github.com/Santhosh939s/CryptoFlow-IDS)
* **Actual Folder Name on Disk:** `S:\gravity projects\CryptoFlow-IDS-main`
* **Domain / Category:** Network Security Analytics, Encrypted Traffic Analysis & Machine Learning IDS

### Why It Was Made (Problem Statement & Purpose)
Over 90% of modern enterprise network traffic is encrypted via TLS 1.3 / HTTPS. Traditional signature-based Deep Packet Inspection (DPI) firewalls (Snort, Suricata) are rendered blind because they cannot inspect encrypted payloads without costly TLS-terminating proxies. Malicious actors exploit this by concealing Command & Control (C2) communication, DDoS floods, and data exfiltration inside encrypted flows. CryptoFlow-IDS solves this by classifying network attacks purely using **side-channel statistical telemetry** (Shannon Entropy, packet sizes, inter-arrival times) with Random Forest machine learning.

### Complete Tech Stack
* **Packet Ingestion:** C (eBPF socket sniffer `ebpf_sniffer.c`), Scapy (`PcapReader`, `AsyncSniffer`), Raw PCAP files.
* **Machine Learning:** Python, Scikit-Learn (`RandomForestClassifier`), NumPy, Pandas, Joblib.
* **Mitigation Engine:** Windows Defender Firewall (`netsh advfirewall`), Linux `iptables`.
* **Telemetry Dashboard:** FastAPI, WebSockets, HTML5/CSS3 live charts.

### How It Operates (Architecture & Request Flow)
1. **Network Sniffing:** Native C/eBPF socket filters or Scapy intercept raw network packets.
2. **Feature Extraction (`pcap_to_csv.py`):** Computes statistical flow metrics without payload decryption:
   * **Shannon Entropy:** $H(X) = -\sum_{i=1}^{n} P(x_i) \log_2 P(x_i)$ (Measures cryptographic randomness).
   * **Flow Geometry:** Packet length distributions, destination ports, inter-arrival jitter.
3. **Random Forest Classification:** `traffic_classifier.pkl` predicts traffic class (`Benign`, `C2 Beacon`, `DDoS`, `Exfiltration`).
4. **Automated Mitigation (`windows_mitigation.py` / `mitigation.py`):** An atomic in-memory cache drops malicious IP connections at the firewall layer and dumps forensic PCAPs for analysis.

### Key Features & Engineering Highlights
* **99.82% Detection Accuracy:** High precision on encrypted traffic with zero TLS decryption required.
* **100x Mitigation Speedup:** In-memory caching reduces firewall rule insertion latency from 6,983ms to 69.59ms.

---

## 05. REST API Security CICD Orchestrator
* **GitHub Repository:** [https://github.com/Santhosh939s/REST-API-Security-CICD-Orchestrator](https://github.com/Santhosh939s/REST-API-Security-CICD-Orchestrator)
* **Actual Folder Name on Disk:** `S:\gravity projects\REST API Security CICD Orchestrator`
* **Domain / Category:** DevSecOps Automation, API Security & Automated Policy Enforcement

### Why It Was Made (Problem Statement & Purpose)
Modern engineering teams deploy software continuously, but application security testing is frequently an afterthought—conducted manually days before release or after breaches occur. The REST API Security CI/CD Orchestrator demonstrates the **"Shift-Left" DevSecOps methodology**: embedding automated security scanners directly into the CI/CD pipeline to detect vulnerabilities, evaluate enterprise risk thresholds, and programmatically break builds (`exit 1`) before code reaches production.

### Complete Tech Stack
* **Target Application:** Node.js, Express.js, MongoDB / In-Memory Mock (Mongoose), JWT, Bcryptjs.
* **CI/CD Platform:** GitHub Actions (`.github/workflows/devsecops-pipeline.yml`).
* **Security Scanners:**
  * **SCA:** NPM Audit & OWASP Dependency-Check.
  * **SAST:** Semgrep (`.semgrep.yml` custom AST rules detecting BOLA, NoSQL injection, hardcoded secrets).
  * **DAST:** OWASP ZAP (Containerized dynamic baseline attack proxy).
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
* **Intentionally Vulnerable Lab Endpoints:** Contains controlled OWASP API Top 10 vulnerabilities (BOLA/IDOR on `/api/users/:id`, NoSQL Injection on `/api/login`) for empirical testing.
* **Automated Pull Request Blocking:** Eliminates manual security reviews for routine flaws by automating fail/pass gatekeeping directly in GitHub Actions.

---

## 06. Privacy-Preserving Federated Threat Intelligence Protocol (PP-FTIP)
* **GitHub Repository:** [https://github.com/Santhosh939s/Privacy-Preserving-Federated-Threat-Intelligence-Protocol](https://github.com/Santhosh939s/Privacy-Preserving-Federated-Threat-Intelligence-Protocol)
* **Actual Folder Name on Disk:** `S:\gravity projects\Privacy-Preserving Federated Threat Intelligence Protocol`
* **Domain / Category:** Decentralized Machine Learning, Zero-Knowledge Proofs (zkML) & Threat Intelligence

### Why It Was Made (Problem Statement & Purpose)
Financial institutions, hospitals, and critical infrastructure operators face identical cyber threats, but privacy regulations (GDPR, HIPAA) prohibit sharing raw network logs or customer telemetry. Standard Federated Learning solves privacy by sharing only model gradients ($\Delta W$), but introduces an existential flaw: **Model Poisoning Attacks**. Malicious or compromised participants can upload sabotaged weights to blind the collective AI model. PP-FTIP solves this via **Verifiable Federated Learning (VFL)** using Zero-Knowledge Proofs.

### Complete Tech Stack
* **Language & Frameworks:** Python 3.8+, PyTorch, NumPy, Scikit-Learn.
* **Zero-Knowledge Prover / zkML:** `ezkl` (zero-knowledge SNARK engine for deep learning models), ONNX export pipeline.
* **Datasets:** NSL-KDD Network Intrusion Dataset, UNSW-NB15, synthetically partitioned non-IID SOC telemetry.
* **Execution Environment:** Local Linux / Windows CLI & Google Colab Cloud Runner (`colab_runner.ipynb`).

### How It Operates (Architecture & Request Flow)
1. **Global Model Initialization:** A central SOC aggregator broadcasts global neural network parameters $W^{(t)}$ to all enrolled member SOCs.
2. **Local Enclave Training:** Each SOC trains the model locally on private telemetry. Raw packets never leave the organization’s secure perimeter.
3. **Cryptographic Proof Generation (zk-SNARK / zkML):**
   * The local prover computes gradient deltas $\Delta W_i = W_i^{(t+1)} - W^{(t)}$.
   * `ezkl` compiles model weights into an arithmetic circuit and generates a zero-knowledge proof asserting that training followed valid loss convergence and norm bounds.
4. **Verifiable Aggregation:** The aggregator verifies proofs in milliseconds without seeing the training telemetry. Verified updates are merged using Federated Averaging (FedAvg).

### Key Features & Engineering Highlights
* **Byzantine Fault Tolerance:** Mathematically neutralizes rogue model poisoning and gradient inversion attacks.
* **Zero-Knowledge Compliance:** Protects sensitive proprietary network logs while contributing to collective defense.

---

## 07. SkillSwap AI
* **GitHub Repository:** [https://github.com/Santhosh939s/SkillSwap-AI](https://github.com/Santhosh939s/SkillSwap-AI)
* **Actual Folder Name on Disk:** `S:\gravity projects\skillSwap`
* **Domain / Category:** Real-Time EdTech, WebRTC Video Collaboration & Community Networks

### Why It Was Made (Problem Statement & Purpose)
Traditional online tutoring is expensive and transactional. Many students and self-taught developers possess valuable skills but lack funds to pay professional tutors. SkillSwap AI was built as a barter-economy education platform: users teach a skill they know in exchange for learning a skill they want, connecting over peer-to-peer WebRTC video calls, live chats, dynamic leaderboards, and AI-driven skill assessments.

### Complete Tech Stack
* **Frontend:** React (Vite), Tailwind CSS, Lucide Icons, Socket.IO Client, Simple-Peer / WebRTC.
* **Backend:** Node.js, Express.js, Socket.IO (WebSocket Signaling Server), WebRTC STUN/TURN handling.
* **Database:** MongoDB Atlas, Mongoose ODM (Schemas for Users, Messages, Meetings, Assessments, Reviews).
* **AI Integration:** Google Gemini AI API (Dynamic anti-cheat assessment generation).

### How It Operates (Architecture & Request Flow)
1. **Skill Matching & Discovery:** Users create profiles listing "Skills I Can Teach" and "Skills I Want to Learn". The system matches complementary users.
2. **WebRTC Signaling via Socket.IO:**
   * When two users agree to a session, the Node.js server acts as a WebRTC signaling relay, exchanging SDP offers, answers, and ICE candidates.
   * Once signaling completes, a direct peer-to-peer encrypted audio/video stream is established between the two browsers.
3. **AI-Driven Assessment Engine:** Before a user is verified to teach, the backend prompts Google Gemini to generate dynamic, topic-specific multi-choice technical assessments with distractors, preventing static question answer leaks.
4. **In-Session Collaboration:** Users communicate via real-time WebSocket chat and structured collaborative notes during the call.

### Key Features & Engineering Highlights
* **Low-Latency P2P Video:** Bypasses central media servers by routing raw video/audio frames directly between client peers via WebRTC.
* **Dynamic AI Assessment Generation:** Eliminates manual test authoring while maintaining rigorous peer tutor qualification standards.

---

## 08. Amazon ML Challenge: Entity Resolution
* **Kaggle Benchmark Notebook:** [https://www.kaggle.com/code/jayakrishna639/notebook0a2f5b7b64](https://www.kaggle.com/code/jayakrishna639/notebook0a2f5b7b64)
* **GitHub Repository:** [https://github.com/Santhosh939s/AllProjectsSummary](https://github.com/Santhosh939s/AllProjectsSummary)
* **Actual Folder Name on Disk:** `S:\gravity projects\ML challenge`
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
3. **Hybrid Feature Engineering:** Computes textual similarity scores (Jaccard, Levenshtein, Cosine on dense DeBERTa embeddings) and attribute matching across categories and brands.
4. **Ensemble Classification:** A gradient-boosted decision tree ensemble (LightGBM + CatBoost) trained on pairwise similarity vectors outputs the final binary match decision.

### Key Features & Engineering Highlights
* **0.9711 Validation Macro F0.5:** Heavily penalized false positives to preserve e-commerce catalog integrity.
* **Scalable Candidate Blocking:** Reduced the computational search space from billions of pairs down to manageable candidate sets.

---

## 09. ChessAI Web App
* **Live Game Engine:** [https://chesswithai-seven.vercel.app/](https://chesswithai-seven.vercel.app/)
* **GitHub Repository:** [https://github.com/Santhosh939s/ChessWithAI](https://github.com/Santhosh939s/ChessWithAI)
* **Actual Folder Name on Disk:** `S:\gravity projects\python-project-chess-with-AI--main`
* **Domain / Category:** Web Game Engine, Algorithmic Search & Web Workers

### Why It Was Made (Problem Statement & Purpose)
Browser chess applications frequently choke the JavaScript UI thread during deep search tree evaluations, or they rely on expensive cloud backend servers to run engine calculations. The ChessAI Web App was designed as a high-performance web platform executing custom algorithmic search client-side via isolated Web Workers, featuring real-time multiplayer via WebRTC.

### Complete Tech Stack
* **Frontend:** Next.js 16 (React 19), TypeScript, Tailwind CSS, Lucide Icons.
* **Rules Engine:** `chess.js` (validating moves, en-passant, and game state).
* **Algorithmic Engine:** Custom Minimax Search with Alpha-Beta Pruning and Piece-Square Tables (PST).
* **Multi-Threading:** Browser Web Workers (`ai.worker.ts`).
* **Multiplayer & Presence:** PeerJS (WebRTC P2P direct gameplay), Firebase (Online presence & match review history).

### How It Operates (Architecture & Request Flow)
1. **Local Board State:** The React client tracks the board using `chess.js` via Forsyth-Edwards Notation (FEN).
2. **Web Worker Thread Offloading:** Moves trigger calculations inside a dedicated Web Worker (`ai.worker.ts`), preventing main thread UI freezes.
3. **Minimax with Alpha-Beta Pruning:** The custom engine recursively evaluates legal moves, pruning subtrees that cannot improve the outcome and applying Piece-Square Tables (PST) for positional awareness.
4. **Peer-to-Peer Multiplayer:** Players can connect directly via PeerJS WebRTC connections for real-time matches without intermediary game server compute.

### Key Features & Engineering Highlights
* **Smooth 60 FPS UI Execution:** Web Worker isolation keeps board animations fluid even during depth 4 search trees.
* **Zero Backend Hosting Compute:** Entire AI calculation runs locally inside the browser.

---

## 10. TypeFlow (Team Project)
* **Live Application:** [https://typeflow-six.vercel.app/](https://typeflow-six.vercel.app/)
* **GitHub Repository:** [https://github.com/Santhosh939s/TypeFlow](https://github.com/Santhosh939s/TypeFlow)
* **Actual Folder Name on Disk:** `S:\gravity projects\TypeFlow`
* **Domain / Category:** Frontend Performance Engineering & Keystroke Telemetry

### Why It Was Made (Problem Statement & Purpose)
Typing speed platforms (like Monkeytype) frequently rely on heavy external charting bundles (Chart.js, Recharts) that bloat bundle sizes and degrade input latency on lower-end hardware. TypeFlow was built as a minimalist, zero-dependency typing platform designed for pure performance, capturing keystroke deltas and rendering mathematical pace acceleration curves using raw SVG path coordinates.

### Complete Tech Stack
* **Frontend:** React 18, Vite, TypeScript, Tailwind CSS.
* **Charting Engine:** Custom Vanilla SVG Path Mathematics (Zero external charting library).
* **State & Persistence:** React Hooks, HTML5 LocalStorage (20-week historical heatmaps).

### How It Operates (Architecture & Request Flow)
1. **Input Interception:** Global `onKeyDown` listeners measure exact millisecond deltas between individual key presses.
2. **Real-Time WPM Calculations:** Dynamically computes raw WPM, net WPM, error rates, and consistency standard deviations.
3. **SVG Bézier Curve Rendering:** Converts typing velocity arrays directly into normalized SVG path strings (`M`, `C`, `L`), rendering real-time performance acceleration graphs at native 60 FPS.
4. **Historical Heatmap Tracking:** Persists daily training activity across a 20-week GitHub-style activity grid in browser local storage.

### Key Features & Engineering Highlights
* **Zero Charting Dependencies:** Eliminates heavyweight charting runtime bundles by generating clean SVG vector paths natively.
* **Sub-Millisecond Keystroke Latency:** Optimized event loops prevent input lag during 150+ WPM typing bursts.

---

## 11. Gesture Control Mouse
* **GitHub Repository:** [https://github.com/Santhosh939s/GestureControlMouse](https://github.com/Santhosh939s/GestureControlMouse)
* **Actual Folder Name on Disk:** `S:\gravity projects\mouse control`
* **Domain / Category:** Computer Vision, Human-Computer Interaction (HCI) & Automation

### Why It Was Made (Problem Statement & Purpose)
Individuals with motor impairments or professionals operating in sterile or hands-busy environments (surgeons, industrial technicians, live presenters) cannot use physical hardware mice. The Gesture Control Mouse was built as an accessible, contactless computer controller: it tracks hand movements via a standard laptop webcam, converts finger gestures into mouse coordinates and click events, and provides a real-time web dashboard for live parameter calibration.

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
4. **Jitter Smoothing:** Passes raw coordinates through an exponential moving average filter to ensure smooth cursor navigation without jumping.

### Key Features & Engineering Highlights
* **Smooth, Jitter-Free Tracking:** Mathematical EMA filtering stabilizes cursor coordinates with under 10% CPU usage.
* **Contactless Accessibility:** Empowers touchless computer interaction using standard off-the-shelf webcams.

---

## 12. LoopingAgent (LightAgent V1)
* **GitHub Repository:** [https://github.com/Santhosh939s/LoopingAgent](https://github.com/Santhosh939s/LoopingAgent)
* **Actual Folder Name on Disk:** `S:\gravity projects\LoopingAgent`
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
* **Zero Database Overhead:** Executes complex repetitive sequences in under 10 MB RAM without cloud licensing fees.

---

## 13. Offensive AI & Automated API Penetration Testing (Ongoing)
* **GitHub Repository:** [https://github.com/Santhosh939s/OffensiveAIandAutonomousAPIPenetrationTesting](https://github.com/Santhosh939s/OffensiveAIandAutonomousAPIPenetrationTesting)
* **Actual Folder Name on Disk:** `S:\UROP\offensive AI and autonomous APi penetration testing`
* **Domain / Category:** Autonomous AI Security Research, LLM Fine-Tuning & Automated Penetration Testing

### Why It Was Made (Problem Statement & Purpose)
Modern enterprise microservices expose hundreds of RESTful API endpoints. Manual penetration testing and traditional signature-based DAST scanners fail to discover complex business logic flaws (such as Broken Object Level Authorization - BOLA, and Broken Function Level Authorization - BFLA). Conducted as an Undergraduate Research Opportunity Program (UROP) project, this framework trains an LLM to autonomously explore API schemas, understand access control semantics, synthesize targeted exploit payloads, and recommend remediation steps.

### Complete Tech Stack
* **Machine Learning & Fine-Tuning:** Python 3.10+, PyTorch, Hugging Face Transformers, PEFT / LoRA (Low-Rank Adaptation), QLoRA.
* **Dataset Infrastructure:** 40,000+ API security classification records (`classification_40000.csv`), 5,000 chain-of-thought reasoning traces (`reasoning_traces_5000.csv`).
* **Vulnerability Framework:** OWASP API Security Top 10, MITRE ATT&CK Enterprise Matrix mapping.
* **Compute & Evaluation:** Kaggle GPU clusters (T4/P100), automated checkpoint evaluations (`checkpoint-1250`, `checkpoint-4500`).
* **Dashboard & Lab:** Streamlit / Python visualization suite, intentionally vulnerable REST target lab.

### How It Operates (Architecture & Request Flow)
1. **Schema & Endpoint Ingestion:** Ingests OpenAPI/Swagger specifications, extracting path parameters, headers, and authentication requirements.
2. **Contextual Vulnerability Analysis:** The fine-tuned LoRA model evaluates authorization boundaries and predicts vulnerability vectors (e.g., IDOR on `/api/v1/user/{id}/billing`).
3. **Dynamic Exploit Generation:** Formulates nuanced HTTP payloads designed to test privilege escalation, SQL/NoSQL injection, and SSRF.
4. **Verification & Audit Reporting:** Executes payloads against target staging environments, parses responses for state anomalies, and outputs executive CVSS forensic reports.

### Key Features & Engineering Highlights
* **Specialized Chain-of-Thought Reasoning:** Trained on 5,000 expert security reasoning traces to eliminate generic hallucinated vulnerabilities.
* **Low-Rank Adaptation (LoRA):** Enables high-efficiency inference and parameter-efficient fine-tuning on modern GPU hardware.

---

## 14. Rapid Crisis Response System (CrisisLink)
* **Live EOC Dashboard:** [https://rapid-crisis-response-two.vercel.app](https://rapid-crisis-response-two.vercel.app)
* **GitHub Repository:** [https://github.com/Santhosh939s/Rapid-Crisis-Response.git](https://github.com/Santhosh939s/Rapid-Crisis-Response.git)
* **Actual Folder Name on Disk:** `S:\google`
* **Domain / Category:** Enterprise Emergency Operations Center (EOC), Multi-Tenant Incident Dispatch & AI Assessment

### Why It Was Made (Problem Statement & Purpose)
In large-scale venues (hotels, resorts, enterprise campuses, hospitals), emergency response is crippled by fragmented communication: guests panic and cannot convey precise locations, dispatchers manually call responders, and on-ground teams lack contextual SOPs (standard operating procedures) for complex incidents (chemical spills, grease fires, active cardiac arrests). CrisisLink was engineered as a high-availability Emergency Operations Center (EOC) platform connecting guests, commanders, and responders with sub-second WebSocket state synchronization, live GPS telemetry on tactical vector maps, multi-tenant campus architecture, and automated Gemini AI disaster guidance.

### Complete Tech Stack
* **Frontend Framework:** Next.js 14+ (App Router), React 19, TypeScript.
* **UI & Visual Design:** Tailwind CSS (Tactical Dark Mode & Glassmorphism), Framer Motion, Lucide Icons, Recharts (Real-time response KPIs).
* **Mapping & Geolocation:** React-Leaflet, Leaflet, HTML5 `navigator.geolocation` API, Vector Polylines for active dispatch trajectory rendering.
* **Backend Architecture:** Node.js, Express.js (TypeScript), Domain-Driven Design (DDD) with `domains/incident`, `domains/building`, and `domains/assessment`.
* **Multi-Tenancy & Middleware:** Custom `tenantMiddleware` enforcing tenant isolation via `x-tenant-id` request headers.
* **Event-Driven Pub/Sub:** In-memory asynchronous `EventBus` (`IncidentCreated` events triggering automated `operationalPipeline.runPipeline`).
* **Database & Authentication:** Firebase Realtime Database (WebSocket-based zero-refresh NoSQL synchronization across all connected roles), Firebase Authentication (RBAC: Commander, Staff, Guest).
* **Artificial Intelligence:** Google Gemini AI API (`@google/generative-ai`) for real-time tactical SOP emergency instructions, automated incident severity triage, and post-incident "Lessons Learned" debrief analysis.
* **Audio & Notification Infrastructure:** Web Audio API (real-time high-pitch frequency synthesizer for audible emergency alarm pings), Browser Notifications API, PWA Service Worker (`sw.js`) with Stale-While-Revalidate offline caching.
* **Interactive Multi-Role Simulation:** Automated 3-way split-screen "God Mode" view utilizing the `BroadcastChannel` browser API and `postMessage` for zero-database live demonstration.

### How It Operates (Architecture & Request Flow)
1. **Frictionless SOS Reporting (Guest Portal):**
   * Panicked individuals access a mobile-optimized SOS portal requiring no prior login.
   * Selecting an emergency type (Medical, Fire/Smoke, Security) captures both the guest's designated room number and their high-precision device GPS coordinates via `navigator.geolocation`.
   * Submitting the SOS writes the incident payload directly to the Firebase Realtime Database and dispatches an event through the backend `EventBus`.
2. **Tactical EOC Command & Triage (Commander Dashboard):**
   * The incident instantly appears on the Commander's tactical dark-mode dashboard without refreshing the page.
   * The Web Audio synthesizer triggers an audible emergency alarm chime, while background browser push notifications alert off-tab dispatchers.
   * Google Gemini AI immediately processes the emergency category and outputs contextual, step-by-step Standard Operating Procedures (SOPs).
3. **Proximity-Based Dispatch & Vector Routing:**
   * On-ground staff members continuously stream their GPS coordinates to Firebase.
   * The Commander views available responders on an interactive Leaflet map and dispatches the closest staff member with one click.
   * Dynamic vector polylines calculate and draw the active response route directly on the tactical map.
4. **Field Execution & Incident Lifecycle (Staff Mobile Portal):**
   * Responders receive an instant mobile dispatch alert with guest coordinates and Gemini SOP guidelines.
   * Responders transition the incident through its lifecycle: `New` $\rightarrow$ `Claimed` $\rightarrow$ `Dispatched` $\rightarrow$ `Resolved`.
   * Updating status to "Resolved" from the field instantly clears the Commander's active alert queue in real time.
5. **AI Debrief & Executive Reporting:**
   * Upon resolution, Gemini AI analyzes incident timestamps, response latency, and actions taken to generate an automated "Lessons Learned" incident summary.
   * Commanders can export the complete forensic audit trail as a styled executive PDF (`window.print` with custom print-media CSS).

### Key Features & Engineering Highlights
* **Domain-Driven Multi-Tenant Backend:** Decoupled Express TypeScript backend supporting campus, building, and floor hierarchies (`/api/v1/campuses`, `/api/v1/buildings`) with header-based tenant isolation.
* **Sub-Second Real-Time Synchronization:** 100% event-driven Firebase Realtime Database architecture eliminates polling; updates propagate across all viewports in $< 100\text{ms}$.
* **Automated 3-Way "God Mode" Demo:** Employs the `BroadcastChannel` browser API to orchestrate a live 3-pane synchronized simulation (Guest, Commander, Staff) across isolated iframes without polluting production database records.
* **Web Audio Frequency Synthesizer:** Native Web Audio API oscillator creates non-blocking audio alerts even when the tab is minimized or running in the background.

---

## 15. CipherLink: End-to-End Encrypted Messaging Platform
* **Live Messaging Platform:** [https://end-to-end-flame.vercel.app/](https://end-to-end-flame.vercel.app/)
* **GitHub Repository:** [https://github.com/Santhosh939s/End-to-end](https://github.com/Santhosh939s/End-to-end)
* **Actual Folder Name on Disk:** `S:\gravity projects\End-to-End Encrypted Chat Platform`
* **Domain / Category:** Zero-Knowledge Cryptography, Asymmetric/Symmetric Key Encapsulation, Client-Side Biometrics & Enterprise Data Sanitization

### Why It Was Made (Problem Statement & Purpose)
Centralized communication platforms (Slack, Discord, unencrypted messaging portals) store user data in plaintext or rely purely on transport-layer encryption (TLS). In these models, data at rest is fully accessible to cloud providers, database administrators, rogue insiders, and lawful interception. CipherLink was engineered with an absolute **Zero-Knowledge Architecture**: the backend functions as a blind cryptographic relay. Every message payload is encrypted and decrypted exclusively in the client's browser memory using native Web Cryptography, ensuring that neither the database admins nor any compromised intermediary can ever decipher user communications.

### Complete Tech Stack
* **Frontend:** React 18, Vite, TypeScript, Tailwind CSS (Glassmorphism & Tactical Dark Theme), Lucide Icons.
* **Client Cryptography Engine:** Web Crypto API (`window.crypto.subtle` native browser engine).
  * **Asymmetric:** RSA-OAEP (2048-bit modulus, SHA-256 hash, public exponent $65537$) for key encapsulation.
  * **Key Derivation:** PBKDF2 (100,000 iterations, SHA-256, 16-byte cryptographically random salt).
  * **Symmetric:** AES-256-GCM (Authenticated Encryption with 12-byte IV and 128-bit authentication tag) for per-message encryption and private key envelope protection.
* **Client-Side Biometrics:** `face-api.js` (TensorFlow.js backend) utilizing SSD MobileNet V1 for 68-point facial landmark detection and 128-dimensional feature vector extraction.
* **Backend:** Node.js, Express.js (TypeScript), Zod (Strict Runtime Request Validation), Bcrypt, JSON Web Tokens (JWT).
* **Database & Verification:** MongoDB Atlas (Mongoose ODM), Nodemailer with Google SMTP (6-digit OTP verification with bcrypt hashing and 10-minute self-destruct).

### System Architecture & Request Flow

```
+--------------------------------------------------------------------------------------------------+
|                                  CLIENT A (BROWSER MEMORY)                                       |
|  1. Writes plaintext: "Secret Mission Details"                                                   |
|  2. Generates ephemeral AES-256-GCM key (`K_msg`) + 12-byte random IV                           |
|  3. Encrypts message: C = AES-GCM(text, K_msg, IV)                                               |
|  4. Encrypts K_msg with Recipient B's Public Key: E_rec = RSA-OAEP(K_msg, PubKey_B)              |
|  5. Encrypts K_msg with Sender A's Public Key:    E_sen = RSA-OAEP(K_msg, PubKey_A)              |
+-------------------------------------------------+------------------------------------------------+
                                                  |
                                                  | POST /api/chat/messages
                                                  | Payload: { ciphertext: C, iv, E_rec, E_sen }
                                                  v
+--------------------------------------------------------------------------------------------------+
|                                EXPRESS.JS BLIND RELAY API GATEWAY                                |
|  - Validates JWT bearer session and Zod payload schema                                           |
|  - Verifies sender & recipient are confirmed contacts                                            |
|  - Cannot decrypt C (Holds zero private keys or master passwords)                                |
+-------------------------------------------------+------------------------------------------------+
                                                  |
                                                  v
+--------------------------------------------------------------------------------------------------+
|                                    MONGODB ATLAS CLOUD STORAGE                                   |
|  Stores only: { senderId, receiverId, ciphertext: C, iv, encryptedKeyReceiver, encryptedKeySender }|
+-------------------------------------------------+------------------------------------------------+
                                                  |
                                                  | GET /api/chat/messages/:contactId
                                                  v
+--------------------------------------------------------------------------------------------------+
|                                  CLIENT B (RECIPIENT BROWSER)                                    |
|  1. Fetches ciphertext bundle from blind relay                                                   |
|  2. Decrypts K_msg using local private key: K_msg = RSA-OAEP_Decrypt(E_rec, PrivKey_B)           |
|  3. Decrypts plaintext message: text = AES-GCM_Decrypt(C, K_msg, IV)                             |
|  4. Renders decrypted text into UI strictly within React volatile state                          |
+--------------------------------------------------------------------------------------------------+
```

### Detailed Cryptographic Implementation Highlights

#### 1. Zero-Knowledge User Key Registration & Recovery
* **RSA Keypair Generation:** Upon user signup, the browser generates an RSA-OAEP 2048-bit keypair (`window.crypto.subtle.generateKey`).
* **Master Password Key Derivation:** The client passes the user's password through **PBKDF2** with 100,000 iterations and a random salt to produce an AES-GCM 256-bit `MasterKey`.
* **Private Key Envelope:** The user's RSA private key is exported (`pkcs8`) and encrypted locally with this `MasterKey`.
* **Server Storage:** The server only receives and stores the RSA **Public Key** and the **Encrypted Private Key Envelope**. The plaintext private key is never transmitted over the network and never resides on disk.

#### 2. Dual-Envelope Message Encryption
In naive E2EE systems, messages are encrypted only for the recipient. Consequently, when the sender opens their chat on a second device or refreshes the page, they cannot decrypt their own sent messages. CipherLink resolves this via a **Dual-Envelope Cryptographic Pipeline**:
* For every message, an ephemeral 256-bit AES-GCM key is minted.
* The message is encrypted with this ephemeral key.
* The ephemeral key is encapsulated **twice**:
  * $E_{\text{receiver}} = \text{RSA-OAEP}(\text{Key}, \text{PubKey}_{\text{receiver}})$
  * $E_{\text{sender}} = \text{RSA-OAEP}(\text{Key}, \text{PubKey}_{\text{sender}})$
* Both envelopes are stored. Either participant can independently unwrap the symmetric key using their own private key, enabling cross-device synchronization while preserving zero-knowledge security.

#### 3. Biometric Face Authentication & Hybrid In-Transit Shield
* **Face Descriptor Extraction:** On the login screen, `face-api.js` captures webcam video, runs SSD MobileNet V1 to detect 68 facial landmarks, and computes a 128-dimensional floating point descriptor vector.
* **Hybrid Application-Layer Encryption:** Facial vectors represent sensitive biometric PII. To protect against TLS termination interception, the client encrypts the 128D vector using an application-layer hybrid envelope (`rsaB64.ivB64.payloadB64`) before sending it to the server.
* **Euclidean Verification:** The server decrypts the vector and computes the Euclidean distance against the registered biometric baseline:
  $$D = \sqrt{\sum_{i=1}^{128} (v_{\text{candidate}, i} - v_{\text{enrolled}, i})^2}$$
  A distance $D < 0.45$ mathematically authenticates the user, issuing an authenticated JWT session.

#### 4. Enterprise Admin Sudo Mode & Cryptographic Wipe Protocol
* **Sudo Protection:** Destructive admin actions (`/api/admin/users/:id`, `/api/admin/wipe`) require re-authentication via password or live biometric scan to generate an ephemeral `sudo-token`.
* **Cryptographic Data Sanitization:** When a user account is deleted, the system executes a physical **Wipe Protocol**: all associated encrypted chat records are overwritten with randomized cryptogram tombstones, guaranteeing forward secrecy and compliance with GDPR "Right to be Forgotten" standards.

---
