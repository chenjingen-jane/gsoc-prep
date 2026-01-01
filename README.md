# 🚀 GSoC 2026: Multi-Track Preparation Journey

Welcome! This repository documents my technical evolution as I prepare for GSoC 2026. I am currently focused on Cybersecurity, with parallel tracks in Big Data and AI.

## 🛤️ Strategy & Tracks

### 🛡️ Track A: Cyber Security (Active)
- **Target:** [OWASP Python Honeypot](https://github.com/OWASP/Python-Honeypot)
- **Status:** Analyzing core architecture, environment constraints, and log data for anomalies.

### 📊 Track B: Big Data & Infra (Active)
- **Target:** Distributed systems and high-throughput data processing
- **Status:** Explored Kafka message acknowledgments and log integrity concepts.

### 🤖 Track C: AI & LLM Integration (Active)
- **Goal:** AI-driven log anomaly detection and analysis using Isolation Forest.

## 📈 Consolidated Progress Dashboard

| Date | Track | Focus Topic | Key Accomplishments | Detailed Log |
|:--- |:--- |:--- |:--- |:--- |
| **Dec 22** | 🛠️ Foundation | Environment & Git | Mastered Linux CLI, Git Rebase, and PDB theory. | [Day 1](./logs/day1-summary.md) |
| **Dec 23** | 🛡️ Security | Codebase Tracing | Verified ohp.py entry point; Traced startup flow via PDB; Identified dependency constraints. | [Day 2](./logs/day2-exploration.md) |
| **Jan 1** | 🛡️/📊/🤖 Multi-Track | Security, Big Data & AI | ✅ Docker handled Windows environment limitations; ✅ Learned Kafka ACK importance for log reliability; ✅ Fetched honeypot logs and applied Isolation Forest; ✅ Handled KeyError and empty DataFrame issues; ✅ Generated screenshots for logs and anomalies. | [Day 3](./logsthis/day3/day3-multi-track.md) |

## 🛠️ Technical Insights (Key Milestones)

### 🛡️ Security Track

**Jan 1, 2026**  
- **Docker Advantage 🐳:** Solved dependency/version issues that failed on Windows natively.  
- **Observation 👀:** Running the honeypot without Docker triggered `ModuleNotFoundError` and Flask/Werkzeug conflicts.  
- **Resolution ✅:** Recognized that missing external services (Elasticsearch) are environment constraints, not bugs.  

**Dec 23–24, 2025 (OWASP Python Honeypot – Reference Work)**  
- **Dynamic Tracing 🕵️‍♀️:** Moved from static code reading to live execution tracing using `PDB`.  
- **Logic Verification 🔍:** Identified that `elasticsearch` connection failure is an intentional `sys.exit(1)` design, not a random crash.

---

### 📊 Big Data Track

**Jan 1, 2026**  
- **Kafka ACK Mechanism 📬:** Learned that ACK ensures log messages are reliably stored and not lost.  
- **Impact 💡:** Understanding ACK guarantees helps maintain log integrity when feeding data into AI models.

---

### 🤖 AI Track

**Jan 1, 2026**  
- **Data Pipeline 🗂️:** Fetched honeypot logs from Elasticsearch into pandas DataFrame.  
- **Feature Engineering 🔧:**  
  - Converted `event` to numeric labels.  
  - Converted `timestamp` to numeric for modeling.  

- **Anomaly Detection 🕵️‍♂️:** Applied Isolation Forest on numeric features to flag anomalies.  

- **Bugs & Solutions 🐞:**  
  - `KeyError: 'event_type'` → column did not exist, switched to `event`.  
  - Empty DataFrame initially → added a synthetic `attack_log` to test workflow.  

- **Visualization 📸:** Screenshots captured:  
  - `day3_df_preview.png` — preview of loaded logs.  
  - `day3_anomaly.png` — rows flagged as anomalies.

## 📬 Contact & Open Source Profile
- **Current Status:** Multi-track progress on OWASP Honeypot logs, Kafka concepts, and AI anomaly detection.  
- **GitHub:** [chenjingen-jane](https://github.com/chenjingen-jane)

---

*"Reading code is like reading a map; debugging is like walking the path."*


