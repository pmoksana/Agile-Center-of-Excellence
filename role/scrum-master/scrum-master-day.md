# A Day in the Life: SAFe Scrum Master 

**Focus:** Enterprise B2B2C Platform (Data Pipelines, Cloud Infrastructure & Customer Touchpoints)  
**Team Topology:** Stream-Aligned Feature Squad + Sub-Domain Data & Cloud Specialists (PO, Devs, Data Analysts/Engineers, Cloud/DevOps)

---

## 08:30 – 09:15 | Morning Signal Scan & Async Triage

Before jumping into sync meetings, focus on flow hygiene across code repositories, data pipeline runs, and board status.

* **Pipeline & Build Diagnostics:** Review CI/CD dashboards (GitHub Actions / AWS CodePipeline). Check if overnight automated integration builds or scheduled ETL data pipeline runs failed.
* **Flow & Board Health Check:** 
  * Scan Jira/ClickUp for Work-In-Progress (WIP) violations (e.g., developers holding $> 2$ active cards).
  * Identify flagged/blocked items aged over 12 hours (e.g., frontend developers waiting on backend API endpoints or Data Analysts waiting on database IAM permissions).
  * Review Pull Request (PR) queues to ensure code reviews meet the team's **24-hour Review SLA**.
* **Async Blocker Clearing:** Ping dependent teams via Slack/Teams regarding cross-squad handoffs needed today (e.g., verifying if the Platform Team released the AWS S3 staging bucket required for today's analytics feature).

---

## 09:15 – 09:45 | Pre-Sync Alignment with Product Owner & Data Lead

* **Agenda:** Quick 15-minute alignment to validate mid-sprint priorities and check feature vs. data pipeline progress.
* **Action:** Ensure the Product Owner and Data Lead are aligned on source-to-target schema updates needed for an upcoming user-facing mobile event trigger, preventing mid-sprint scope disconnects.

---

## 10:00 – 10:20 | Daily Standup (DSU) — Right-to-Left Board Walk

Instead of taking status reports, facilitate a self-organizing sync using a rotating developer **"Board Pilot"**.

* **Execution:** Walk the board **Right-to-Left** (from *Done / Released* $\rightarrow$ *QA / Data Validation* $\rightarrow$ *In Progress* $\rightarrow$ *To Do*):
  1. **Customer Touchpoints (Web/Mobile UI):** Check UI stories nearing completion. *"Is the new checkout event tracking ready for telemetry validation?"*
  2. **Data Pipeline & Analytics Stories:** Focus on handoffs. *"Did the Data Analyst finish validating the schema query so the frontend team can deploy the live analytics dashboard?"*
  3. **Cloud Enablers:** Confirm that IaC (Infrastructure as Code) scripts for AWS Lambda triggers are deployed to Staging.
* **Outcome:** Identify 2 critical blockers, log them on the Impediment Board, and assign clear owners to resolve them before 12:00 PM.

---

## 10:30 – 11:30 | Blocker Removal & Cross-Team Dependency Clearing

Step into operational Delivery Lead mode to clear systemic friction across domains.

* **Issue 1 (Data Access):** A Data Analyst is blocked waiting for production-like anonymized data access. Coordinate directly with Data Governance and Security leads to expedite IAM role approvals.
* **Issue 2 (Cross-ART Dependency):** The customer-facing web feature relies on an external API maintained by the Core Platform Team. Reach out to their Scrum Master to verify that the mock endpoint contract is live for integration testing.

---

## 11:30 – 12:30 | Backlog Refinement & "Four Amigos" Workshop

Facilitate a structured refinement session bridging product needs with data and cloud architecture.

* **Attendees:** Product Owner, Lead Engineer, Data Analyst, Cloud/DevOps Engineer.
* **Focus:** Refining upcoming features for the next iteration (e.g., Real-time Customer Personalization Engine).
* **Key Facilitation Tasks:**
  * Guide the PO to write testable Acceptance Criteria using **BDD (Given-When-Then)** formats.
  * Ensure a strict **Definition of Ready (DoR)** gatekeeping check: No user-facing feature enters the sprint without an agreed **Data Contract** (schema specification) and provisioned **Cloud Infrastructure Enabler**.
  * Use **Planning Poker** (Fibonacci sequence) to size user stories and research spikes relatively.

---

## 12:30 – 13:30 | Lunch & Casual Team Social

---

## 13:30 – 14:00 | SAFe Scrum of Scrums (SoS) / ART Sync

Represent the squad at the Release Train Engineer (RTE)-led ART Sync across all Scrum Masters in the train.

* **Status Reporting:** Report squad progress toward **PI Objectives** using flow metrics and the **Program Predictability Measure (PPM)**.
* **Dependency Mapping:** Update the SAFe Program Board regarding shared data pipeline deliverables. High-visibility callout: *"Our mobile analytics tracking feature is on schedule for Sprint 3, pending the Cloud Team's Kafka cluster upgrade in Sprint 2."*
* **Risk ROAMing:** Escalate program-level risks that cannot be resolved at the squad level.

---

## 14:00 – 15:00 | Coaching & 1-on-1 Mentorship

* **1-on-1 with Data Analyst:** Coach on breaking down large exploratory research tasks (*EDA Spikes*) into timeboxed 2-day increments to avoid open-ended, non-deliverable research cycles.
* **1-on-1 with Product Owner:** Review the **70/20/10 Capacity Allocation Model** (70% Features, 20% Architectural/Data Enablers, 10% Tech Debt) to ensure architectural enablers for cloud scaling are prioritized alongside business value.

---

## 15:00 – 16:00 | Sprint Retrospective / Continuous Improvement (Kaizen)

* **Focus Area:** *Why did data validation lag behind feature deployment in the last iteration?*
* **Facilitation Technique:** Use a **Fishbone Diagram** and **5 Whys** to discover root causes (e.g., late schema changes led to manual data re-indexing).
* **Actionable Working Agreement Output:** Create an explicit team rule: *"No UI feature story moves to 'In Progress' until backend payload schemas are locked in Confluence."*

---

## 16:00 – 17:00 | Flow Metrics, Administration & CoE Knowledge Sharing

* **Metrics Analysis:** Update Jira/ClickUp dashboards and review flow trends:
  * **Cycle Time & Lead Time:** Verify if feature cycle times are stabilizing (Target: $< 4$ days).
  * **Flow Efficiency:** Analyze Active vs. Wait Time to reduce handoff idle time between engineering and data teams.
  * **DORA Metrics:** Review Change Failure Rate and Mean Time to Restore (MTTR) with engineering leads.
* **Agile CoE Contribution:** Update the organizational Agile Center of Excellence repository (GitHub/Confluence) with the team's newly refined Working Agreements template.

---

## Daily Schedule At-A-Glance

```text
08:30 AM ──► Signal Scan & Pipeline Diagnostics (CI/CD, ETL, WIP limits)
10:00 AM ──► Daily Standup (Right-to-Left Board Walk)
10:30 AM ──► Blocker Resolution (IAM, API Contracts, Cross-Team Sync)
11:30 AM ──► "Four Amigos" Refinement (Product + Data + Cloud + Dev)
01:30 PM ──► SAFe Scrum of Scrums / ART Sync (Dependency & PPM Tracking)
02:00 PM ──► 1-on-1 Coaching & PO Alignment (Capacity Guardrails)
03:00 PM ──► Retrospective / Problem-Solving Workshop
04:00 PM ──► Flow Metrics Review & CoE Documentation
