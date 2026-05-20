![Platform](https://img.shields.io/badge/platform-RHEL%2010-red)
![Docker](https://img.shields.io/badge/containerized-Docker-blue)
![AI](https://img.shields.io/badge/AI-Ollama-green)
![Workflow](https://img.shields.io/badge/automation-n8n-orange)
![Database](https://img.shields.io/badge/database-PostgreSQL-blue)

# 🛡️ Mini-ThreatGuard

AI-powered SOC automation and threat intelligence pipeline built using **n8n, Ollama, PostgreSQL, Docker, and Telegram**.

Mini-ThreatGuard is a lightweight backend-first cybersecurity automation project designed to simulate modern SOC (Security Operations Center) workflows with local AI-powered threat enrichment.

---

# 🚀 Features

* ✅ Automated CVE ingestion from NVD
* ✅ AI-powered vulnerability enrichment
* ✅ Local LLM inference using Ollama
* ✅ Critical severity filtering
* ✅ PostgreSQL alert persistence
* ✅ Telegram SOC notifications
* ✅ Dockerized deployment
* ✅ Event-driven automation pipeline
* ✅ Lightweight self-hosted architecture

---

# 🧠 Workflow Architecture

```text
+-------------------+
| NVD CVE API       |
| Threat Feed       |
+-------------------+
          |
          v
+-------------------+
| n8n Workflow      |
| Orchestration     |
+-------------------+
          |
          v
+-------------------+
| Data Processing   |
| - Normalize CVEs  |
| - Filter Severity |
| - Rate Limiting   |
+-------------------+
          |
          v
+-------------------+
| Ollama            |
| Local AI Engine   |
+-------------------+
          |
          v
+-------------------+
| PostgreSQL        |
| Alert Persistence |
+-------------------+
          |
          v
+-------------------+
| Telegram Alerts   |
| SOC Notifications |
+-------------------+
```

---

# ⚙️ Tech Stack

| Layer            | Technology              |
| ---------------- | ----------------------- |
| OS               | RHEL 10                 |
| Workflow Engine  | n8n                     |
| Database         | PostgreSQL              |
| Queue/Cache      | Redis                   |
| AI Inference     | Ollama                  |
| AI Models        | TinyLlama / Qwen        |
| Notifications    | Telegram Bot API        |
| Containerization | Docker & Docker Compose |

---

# 🔥 Core Workflow

```text
Schedule Trigger
      ↓
Fetch CVEs from NVD
      ↓
Normalize Vulnerability Data
      ↓
Filter Critical Vulnerabilities
      ↓
AI Enrichment using Ollama
      ↓
Format SOC Alert
      ↓
Store in PostgreSQL
      ↓
Send Telegram Notification
```

---

# 📸 Screenshots

## Workflow Pipeline

> Add your exported workflow screenshot here:

<img width="3200" height="1674" alt="Workflow-canvas" src="https://github.com/user-attachments/assets/32bcf51f-126c-487f-bda7-1196264bb67f" />


---

## Architecture Diagram

> Add your Draw.io architecture export here:

<img width="241" height="971" alt="Mini-ThreatGuard-Workflow-Diagram drawio" src="https://github.com/user-attachments/assets/5525b064-1e52-48b4-8f0d-d1101465b01b" />


---

## Telegram SOC Alerts

> Add Telegram alert screenshot here:

<img width="2392" height="1744" alt="Telegram-Alert" src="https://github.com/user-attachments/assets/54792dc3-42fa-4f9e-9a73-29cd7775351b" />


---

# 🧩 Key Components

## 🔹 Threat Intelligence Ingestion

Mini-ThreatGuard pulls live CVE data directly from the National Vulnerability Database (NVD):

```text
https://services.nvd.nist.gov/rest/json/cves/2.0
```

---

## 🔹 AI-Powered Threat Enrichment

The project uses locally hosted AI models through Ollama to:

* Explain vulnerabilities
* Summarize attack impact
* Generate analyst-friendly insights
* Simulate AI-assisted SOC workflows

---

## 🔹 PostgreSQL Persistence

Processed alerts are stored for:

* historical analysis
* future dashboards
* deduplication
* incident tracking

---

## 🔹 Telegram Notifications

Critical vulnerabilities are pushed as SOC-style alerts directly to Telegram for real-time monitoring.

---

# 🛠️ Challenges Solved

This project involved solving several real-world infrastructure and automation challenges:

* Docker container networking
* Host ↔ container communication
* Ollama service exposure
* Local AI inference under low-memory environments
* API rate limiting
* Workflow orchestration
* Event filtering and persistence
* AI pipeline integration

---

# 📂 Project Structure

```text
Mini-ThreatGuard/
│
├── docker/
├── docs/
│   └── architecture.md
├── screenshots/
├── workflows/
│   └── mini-threatguard-workflow.json
├── README.md
├── .env.example
└── docker-compose.yml
```

---

# 🧪 Example SOC Alert

```text
🚨 CRITICAL CVE ALERT 🚨

CVE: CVE-2026-XXXX
Severity: CRITICAL
CVSS Score: 9.8

AI Analysis:
Remote attackers may execute arbitrary code execution through vulnerable services.

Recommended Action:
Patch affected systems immediately and investigate exposure.
```

---

# 📈 Future Improvements

* 🔹 Wazuh integration
* 🔹 AI-assisted incident correlation
* 🔹 Dashboard & analytics
* 🔹 Deduplication engine
* 🔹 Threat scoring system
* 🔹 Asset inventory correlation
* 🔹 Multi-tenant architecture
* 🔹 Webhook ingestion pipelines

---

# 🧠 Concepts Demonstrated

This project demonstrates practical exposure to:

* Threat intelligence pipelines
* AI-assisted SOC workflows
* Local LLM infrastructure
* Workflow orchestration
* PostgreSQL persistence
* Event-driven automation
* Docker networking
* DevOps troubleshooting
* Security automation engineering

---

# 📌 Design Philosophy

Mini-ThreatGuard focuses on:

* backend-first architecture
* lightweight infrastructure
* open-source tooling
* local AI inference
* operational automation workflows

The goal is to simulate real SOC automation patterns rather than frontend-heavy demo applications.

---

# 👨‍💻 Author

## Mazhar Ali

DevOps & Security Automation Enthusiast

* AI-powered SOC automation
* Infrastructure orchestration
* Threat intelligence workflows
* Local AI inference pipelines

---

# ⭐ Repository Goals

This repository serves as:

* a cybersecurity automation learning project
* a lightweight AI-SOC reference implementation
* an infrastructure orchestration showcase
* a foundation for future detection engineering workflows
