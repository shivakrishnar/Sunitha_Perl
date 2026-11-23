# Personal Engineering & System Reference Guide
**Role:** Perl Backend Developer | **Start Date:** YYYY-MM-DD

---

## 1. Key Contacts & Go-To People
| Name | Role / Area of Expertise | Best Way to Reach |
| :--- | :--- | :--- |
| | Team Lead / Manager | |
| | Senior Perl Dev (Architecture / Legacy Framework) | |
| | DBA / SQL Contact | |
| | QA / UAT Lead | |
| | DevOps / Release / On-Call Lead | |

---

## 2. Repository & Codebase Map
*Since there is no central Wiki, log every repo and what it controls here.*

| Repo Name | VCS (Git/TFS) | Purpose / Module | Key Entry-Point Scripts (`.pl` / `.pm`) | Config / XSD / SQL Locations |
| :--- | :--- | :--- | :--- | :--- |
| `e.g., comm-engine` | Git | Core XML document builder | `bin/process_batch.pl` | `/config/prod.ini`, `/schemas/` |
| | | | | |
| | | | | |

---

## 3. End-to-End System Flow
*Document how data enters, transforms, and exits the system.*

1. **Trigger / Ingestion:** *(e.g., Cron job / batch scheduler / DB polling table `incoming_requests`)*
2. **Processing Layer:** *(e.g., Perl script reads DB rows -> maps fields -> generates XML via `XML::LibXML`)*
3. **Validation:** *(e.g., Validated against `schema_v2.xsd`)*
4. **Output / Delivery:** *(e.g., Drops XML to SFTP / calls downstream API / updates status in DB)*
5. **Downstream Consumers:** *(Who receives the generated documents?)*

---

## 4. Environments & Database Connections
| Environment | App Server Host / Path | DB Server & Database Name | Log Directory Path | Notes / Access Rules |
| :--- | :--- | :--- | :--- | :--- |
| **Local / VDI** | `C:\Projects\...` | Local / Dev DB | `./logs/` | |
| **DEV** | | | | |
| **QA / UAT** | | | | |
| **PROD** | *(Read-only / On-call)* | *(Read-only)* | | *Never run unapproved scripts* |

---

## 5. Git / TFS & Deployment Workflow
* **Main / Release Branch:** `_______________________`
* **Branch Naming Rule:** *(e.g., `feature/TICKET-123-short-desc`)*
* **Commit Message Format:** *(e.g., `[TICKET-123] Fix XML encoding for special chars`)*
* **Code Review / PR Rules:** *(Who approves? Any required checks?)*
* **Deployment Steps:**
  * **To DEV:** 
  * **To QA/UAT:** 
  * **To PROD:** 

---

## 6. Local Testing & Debugging Commands
*Save exact commands that work on the VDI so you never have to figure them out twice.*

* **Run syntax check:**
  ```bash
  perl -Ilib -c bin/script_name.pl
  ```
* **Run unit tests:**
  ```bash
  prove -lv t/
  ```
* **Run sample batch locally:**
  ```bash
  # Paste exact command + environment variables + sample XML input path here
  ```
* **Validate XML against XSD:**
  ```bash
  xmllint --noout --schema path/to/schema.xsd path/to/output.xml
  ```

---

## 7. Ticket & Troubleshooting Log
*Keep a running log of every ticket worked on and every production issue seen.*

### `[TICKET-XXX]` - Short Description (Date: YYYY-MM-DD)
* **Repo & Files Modified:** 
* **Root Cause / Requirement:** 
* **DB Tables / Queries Used:** 
* **How It Was Tested:** 
* **Gotchas / Lessons Learned:** 

---

## 8. On-Call & Production Support Playbook
* **Alert Channels:** *(Email / Teams / Slack / PagerDuty)*
* **Common Error #1:**
  * **Symptom / Log Message:** 
  * **SQL Query to Check Status:** 
  * **Resolution / Escalation Contact:** 