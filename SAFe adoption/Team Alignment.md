# Team Alignment & Agile Coaching Boards

A comprehensive visual framework guide for Agile Coaches, Scrum Masters, and Delivery Leads to structure Miro/Mural workspaces for team alignment, baseline calibration, and competency mapping.

---

## 1. Team Working Agreements & Charter Board

* **Best For:** Onboarding new team members, resetting team norms, or transitioning a team from *Storming* to *Performing*.
* **Facilitation Technique:** Asynchronous or silent sticky-note generation followed by affinity grouping, open debate, and dot-voting to reach consensus.

### Canvas Layout Matrix
┌───────────────────────────────────────┬───────────────────────────────────────┐
│                                       │                                       │
│          1. CORE VALUES               │     2. COMMUNICATION & SLAs           │
│  - Psychological Safety               │  - Slack / Teams protocols            │
│  - Respect & Candor                   │  - 24-Hour PR Review SLA              │
│  - Ownership & Transparency           │  - Core working hours / Timezones     │
│                                       │                                       │
├───────────────────────────────────────┼───────────────────────────────────────┤
│                                       │                                       │
│       3. QUALITY & FLOW (DoR/DoD)     │       4. CEREMONIES & CADENCE         │
│  - Definition of Ready Checklist      │  - Standup guidelines (Async vs Sync) │
│  - Definition of Done Checklist       │  - Timeboxed Refinement rules         │
│  - Data Contract standards            │  - Retro participation expectations   │
│                                       │                                       │
└───────────────────────────────────────┴───────────────────────────────────────┘


### Key Checklist Criteria

* [ ] **24-Hour PR Review SLA:** All open code/schema pull requests must be reviewed, commented on, or approved within 24 business hours.
* [ ] **Definition of Ready (DoR):** User stories must contain acceptance criteria in **BDD format** (*Given-When-Then*), clear data contracts, and identified dependencies before sprint entry.
* [ ] **Definition of Done (DoD):** Code passes local build and linting checks, automated test suites green, peer review complete, documentation updated in Confluence.

---

## 2. Baseline Story Calibration & Sizing Matrix Board

* **Best For:** Coaching engineering and data teams on relative estimation (Story Points) versus time-based estimation (Hours/Days).
* **Facilitation Technique:** Drag-and-drop relative alignment. Team members place unestimated user stories in relation to established **Golden Anchor** reference cards.

### Calibration Grid Framework

| Story Points | Complexity | Risk / Uncertainty | Effort / Volume | Golden Anchor Reference (Real Example) |
| :---: | :--- | :--- | :--- | :--- |
| **1** | Trivial / Copy-paste | Zero risk; clear pattern | Very Low ($< 2\text{ hrs}$) | Update database column alias or fix UI dashboard typo. |
| **2** | Low; familiar domain | Low risk; tested solution | Low | Add a basic filter to an existing SQL query or dbt model. |
| **3** | Moderate; standard pattern | Minor uncertainty | Medium | Create a new standard ETL ingestion pipeline with existing connectors. |
| **5** | High; multiple files/tables | Moderate risk; 3rd-party API | High | Integrate a new REST API endpoint with schema checks and error handling. |
| **8** | Complex architecture | High risk; unknown dependencies | Very High | Build a new end-to-end data pipeline with complex multi-table joins. |
| **13** | **TOO LARGE** | Extreme risk; major unknowns | Massive | **Action Required:** Split into smaller stories during Backlog Refinement. |

### Estimation Flow Diagram

[ New Story Presented ]
│
▼
┌──────────────────────────────────────────────┐
│  Compare against Golden Anchors in Matrix:    │
│  - Is it as simple as Point 2?               │
│  - Or does it carry Point 5 API Risks?       │
└──────────────────────────────────────────────┘
│
┌────┴───────────────────────────┐
▼                                ▼
[ Consensus Reached ]       [ Disagreement (e.g., 2 vs 8) ]
│                                │
▼                                ▼
[ Assign Points     ]       [ SM Facilitates Calibration: ]
│ - Is risk driving the 8?
│ - Can we split the story?


---

## 3. Skill & Competency Matrix (Skill Radar)

* **Best For:** Identifying single-point-of-failure (SPOF) dependencies, planning cross-training initiatives, and mapping cross-functional squad capabilities across Dev, Data, Cloud, and Quality Engineering.
* **Facilitation Technique:** Self-assessment on a scale of $1\text{--}5$, followed by peer review and team capability gap analysis.

### Proficiency Rating Scale

* **1 - Novice:** Theoretical knowledge only; requires full guidance.
* **2 - Practitioner:** Can deliver basic tasks with occasional supervision.
* **3 - Proficient:** Independent contributor; follows best practices.
* **4 - Advanced:** Mentors others; resolves complex domain edge cases.
* **5 - Expert:** Defines architectural standards; industry-level knowledge.

### Team Skill Mapping Matrix

| Team Member | Role | Data Eng / SQL | Cloud Infra (AWS/GCP) | CI/CD & Automation | Business Domain | QA / Validation |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **Alex M.** | Data Engineer | 5 | 4 | 3 | 2 | 3 |
| **Sarah T.** | Analytics Dev | 4 | 2 | 2 | 5 | 4 |
| **David K.** | Cloud/DevOps | 2 | 5 | 5 | 1 | 2 |
| **Elena R.** | QA / Tester | 3 | 2 | 4 | 3 | 5 |
| **Target Squad Average** | *Balanced Squad* | **$> 3.5$** | **$> 3.0$** | **$> 3.5$** | **$> 3.0$** | **$> 3.5$** |

### Red-Flag / Risk Analysis Rules
1. **Single Point of Failure (SPOF):** Any column where only *one* team member scores $\ge 4$.
2. **Delivery Bottleneck:** Any core competency column where the squad average is $< 2.5$.
3. **Action Plan Trigger:** Formulate cross-training pair-programming stories in the upcoming sprint for identified SPOF domains.
