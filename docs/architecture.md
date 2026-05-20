# Mini-ThreatGuard Architecture

## Overview

Mini-ThreatGuard is an AI-powered cybersecurity automation pipeline designed to simulate core SOC (Security Operations Center) workflows using lightweight open-source tooling.

The project focuses on:

* Threat intelligence ingestion
* AI-assisted vulnerability analysis
* Event persistence
* Automated alerting
* Local AI inference

The architecture was designed as a backend-first security automation system inspired by modern SOC orchestration workflows.

---

# High-Level Architecture

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

# Core Components

## 1. NVD CVE Feed

### Purpose

Fetch publicly disclosed vulnerabilities from the National Vulnerability Database (NVD).

### Responsibilities

* Retrieve latest CVEs
* Supply raw vulnerability data
* Act as threat intelligence source

### API

```text
https://services.nvd.nist.gov/rest/json/cves/2.0
```

---

# 2. n8n Workflow Engine

### Purpose

Orchestrate the entire automation pipeline.

### Responsibilities

* Trigger scheduled workflows
* Process CVE events
* Execute filtering logic
* Route data between services
* Handle automation flow

### Key Nodes Used

* Schedule Trigger
* HTTP Request
* Code
* IF
* Wait
* PostgreSQL
* Telegram

---

# 3. Data Processing Layer

### Purpose

Convert raw CVE payloads into structured security events.

### Responsibilities

* Extract severity
* Extract CVSS scores
* Normalize event schema
* Filter critical vulnerabilities
* Reduce noisy alerts

### Example Output

```json
{
  "cve": "CVE-2026-XXXX",
  "severity": "CRITICAL",
  "score": 9.8
}
```

---

# 4. Ollama Local AI Engine

### Purpose

Provide local AI-powered security analysis without external cloud dependencies.

### Responsibilities

* Analyze CVEs
* Generate analyst-friendly explanations
* Summarize vulnerability impact
* Provide remediation guidance

### Models Used

* tinyllama
* qwen2:0.5b

### Benefits

* No API rate limits
* Offline/local inference
* Lower operational cost
* Better infrastructure control

---

# 5. PostgreSQL Persistence Layer

### Purpose

Persist processed security alerts.

### Responsibilities

* Store CVE history
* Save AI-generated analysis
* Enable future dashboards
* Support deduplication

### Stored Data

* CVE ID
* Severity
* CVSS score
* Description
* AI analysis
* Timestamps

---

# 6. Telegram Alerting Layer

### Purpose

Deliver real-time SOC-style notifications.

### Responsibilities

* Send mobile alerts
* Notify critical threats
* Simulate incident escalation

### Example Alert

```text
🚨 CRITICAL CVE ALERT 🚨

CVE: CVE-2026-XXXX
Severity: CRITICAL

AI Analysis:
Remote attackers may execute arbitrary code.
```

---

# Workflow Execution Flow

```text
Schedule Trigger
      ↓
Fetch CVEs
      ↓
Normalize Data
      ↓
Filter Critical CVEs
      ↓
Wait / Rate Control
      ↓
AI Enrichment (Ollama)
      ↓
Format Alert
      ↓
Store in PostgreSQL
      ↓
Send Telegram Alert
```

---

# Technical Challenges Solved

## Docker Networking

* Container-to-host communication
* Service exposure
* Internal DNS resolution

## AI Infrastructure

* Local model serving
* Memory optimization
* Lightweight inference deployment

## Workflow Engineering

* Event filtering
* AI orchestration
* Error handling
* Rate limiting

## Persistence

* Database schema creation
* PostgreSQL integration
* Structured event storage

---

# Future Enhancements

## Wazuh Integration

```text
Wazuh Agent
      ↓
Wazuh Manager
      ↓
n8n Webhook
      ↓
AI Analysis
      ↓
SOC Alert
```

## Planned Features

* Deduplication engine
* Threat correlation
* Dashboard UI
* Incident timelines
* Asset tracking
* AI-assisted investigations

---

# Design Philosophy

Mini-ThreatGuard prioritizes:

* Backend automation
* Lightweight infrastructure
* Local AI inference
* Open-source tooling
* Modular architecture

The project focuses on building operational security workflows rather than frontend-heavy demonstrations.

---

# Author

Mazhar Ali

DevOps & Security Automation Project
