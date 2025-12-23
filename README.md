\# 🚀 GSoC 2026: Multi-Track Preparation Journey



Welcome! This repository documents my technical evolution as I prepare for GSoC 2026. I am currently focused on Cybersecurity, with parallel tracks in Big Data and AI.



---



\## 🛤️ Strategy \& Tracks



\### 🛡️ Track A: Cyber Security (Active)

\- \*\*Target:\*\* \[OWASP Python Honeypot](https://github.com/OWASP/Python-Honeypot)

\- \*\*Status:\*\* Analyzing core architecture and environment constraints.



\### 📊 Track B: Big Data \& Infra (Pending)

\- \*\*Target:\*\* Distributed systems and high-throughput data processing.



\### 🤖 Track C: AI \& LLM Integration (Pending)

\- \*\*Goal:\*\* Exploring AI-driven security automation.



---



\## 📈 Consolidated Progress Dashboard



| Date | Track | Focus Topic | Key Accomplishments | Detailed Log |

|:--- |:--- |:--- |:--- |:--- |

| \*\*Dec 22\*\* | 🛠️ Foundation | Environment \& Git | Mastered Linux CLI, Git Rebase, and PDB theory. | \[Day 1](./logs/day1-summary.md) |

| \*\*Dec 23\*\* | 🛡️ Security | Codebase Tracing | Verified `ohp.py` entry point; Traced startup flow via PDB; Identified dependency constraints. | \[Day 2](./logs/day2-exploration.md) |

| \*\*Dec 24\*\* | 🛡️ Security | Environment | \*Next Step: Resolving dependencies via Docker.\* | \*Upcoming\* |



---



\## 🛠️ Technical Insights (Key Milestones)



\### \*\*1. Systems \& Debugging\*\*

\- \*\*Dynamic Tracing:\*\* Moved from static code reading to live execution tracing using `PDB`.

\- \*\*Logic Verification:\*\* Identified that `elasticsearch` connection failure is an intentional `sys.exit(1)` design, not a random crash.



\### \*\*2. Version Control \& Engineering\*\*

\- \*\*Repo Management:\*\* Successfully refactored personal workspace to professional `logs/` structure.

\- \*\*Problem Solving:\*\* Learned to interpret `ModuleNotFoundError` as a signal of environment mismatch (Legacy vs. Modern Python).



---



\## 📬 Contact \& Open Source Profile

\- \*\*Current Status:\*\* Deep-diving into OWASP Honeypot's `core/load.py` logic.

\- \*\*GitHub:\*\* \[chenjingen-jane](https://github.com/chenjingen-jane)



---

\*"Reading code is like reading a map; debugging is like walking the path."\*

