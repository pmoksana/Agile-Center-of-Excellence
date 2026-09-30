# When & How a Scrum Master Establishes Success Criteria with Data Teams

In Data Science, Data Engineering, and Data Analytics, standard software engineering criteria (*"Code builds without errors and tests pass"*) fall short. Data work involves high uncertainty, non-deterministic exploratory research, schema evolution, and pipeline performance dependencies.

The Scrum Master facilitates, discusses, and enforces success criteria across **four key operational stages**.

---

## 1. At the Story/Spike Creation Phase (Definition of Ready - DoR)

Before a data story or research spike is committed to a sprint, the Scrum Master ensures the Product Owner, Data Lead, and Engineers define explicit, measurable success criteria during **Backlog Refinement**.

### When It Happens
During weekly refinement or "Four Amigos" sessions (PO + Dev + Data Analyst + Cloud Engineer).

### How the SM Facilitates
* **For Data Science / ML Spikes:** The SM prevents open-ended research by enforcing quantitative performance thresholds and timeboxes.
  * *Bad Criteria:* "Explore customer churn data."
  * *Good Criteria:* "Execute exploratory data analysis (EDA) within a 3-day timebox to evaluate feature correlations. Success = Model accuracy target $>85\%$ OR a documented conclusion explaining why the hypothesis was rejected."
* **For Data Engineering & Pipelines:** The SM ensures Data Contracts and SLAs are defined before work begins.
  * *Good Criteria:* "Source-to-target mapping complete; ETL pipeline latency strictly $< 500\text{ms}$; zero unhandled null payloads."

---

## 2. During Iteration Planning (Sprint Goals & Acceptance Criteria)

During Sprint Planning, the Scrum Master checks that daily operational success criteria align with the **Sprint Goal**.

### When It Happens
At the start of every sprint during Iteration Planning.

### How the SM Facilitates
* **Validating BDD Acceptance Criteria:** The SM ensures criteria are written in testable **Given-When-Then** formats:
  > **Given** new raw transaction logs enter the AWS S3 staging bucket,  
  > **When** the automated Glue/Spark ETL job runs overnight,  
  > **Then** the analytics table populates in Snowflake without schema drift,  
  > **And** data validation alerts trigger if missing records exceed $0.01\%$.
* **Definition of Done (DoD) Alignment:** The SM ensures the squad agrees on what "Done" means for data artifacts (e.g., automated unit testing for SQL models using dbt, documentation updated in Collibra/Confluence, and code merged via 24-Hour Review SLA).

---

## 3. During PI Planning (Program Increment Objectives & Predictability)

In scaled environments like SAFe, data deliverables often serve as foundational enablers for multiple customer-facing feature squads.

### When It Happens
During the 2-day PI Planning event at the beginning of each 8–12 week increment.

### How the SM Facilitates
* **Formulating PI Objectives with Business Value:** The SM guides the Data Team and PO to translate technical data tasks into business-aligned PI Objectives with measurable business owner scores ($1\text{--}10$).
  * *Technical Task:* "Migrate Postgres tables to Snowflake."
  * *Value-Driven Objective:* "Enable real-time customer behavior analytics by migrating checkout data pipelines to Snowflake, reducing dashboard query load time by $50\%$."
* **Setting Predictability Targets:** The SM tracks delivery against these objectives to achieve a **Program Predictability Measure (PPM)** target of **$85\%\text{--}90\%$**.

---

## 4. During Sprint Execution & Daily Standups (Flow & Quality Validation)

Success criteria are monitored continuously to detect pipeline drift, blocked validation, or broken builds early.

### When It Happens
Daily during board scans, Daily Standups (DSU), and mid-sprint check-ins.

### How the SM Facilitates
* **Daily Pipeline Health Checks:** Monitor CI/CD dashboards for pipeline build failure rates ($< 10\%$) and Mean Time to Recovery ($\text{MTTR} < 1\text{ hour}$).
* **Reviewing Data Quality Incidents:** If a data pipeline breaks due to an unannounced upstream schema change, the SM uses the incident in the Retrospective to establish a new working agreement around **Data Contracts**.

---

## Summary Matrix: Success Criteria Checklist for Data Teams

| Timing / Stage | Focus Area | Success Criteria Example | SM Facilitation Role |
| :--- | :--- | :--- | :--- |
| **Refinement (DoR)** | Research & Spikes | Timeboxed (e.g., 2 days) + Clear metric threshold ($\text{Precision} \ge 85\%$) | Prevents infinite exploratory research cycles. |
| **Refinement (DoR)** | Pipeline / ETL | Schema contract agreed; source-to-target mapping approved | Enforces DoR before sprint commitment. |
| **Sprint Planning** | Sprint Goal | BDD format (*Given-When-Then*); dbt/unit tests pass; DoD met | Ensures testability and cross-role agreement. |
| **PI Planning** | PI Objectives | PPM target $85\%\text{--}90\%$; Business Owner value assigned ($1\text{--}10$) | Connects data enablers to business outcomes. |
| **Daily Operations** | Flow & Quality | PR Review $< 24\text{ hours}$; Active WIP $\le 2$ items/person; $\text{MTTR} < 1\text{ hour}$ | Protects delivery flow and unblocks handoffs. |
