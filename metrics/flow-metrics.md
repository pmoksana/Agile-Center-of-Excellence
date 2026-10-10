# Flow Metrics on a SAFe Agile Release Train

For the Scrum Master / Agile Facilitator on a SAFe Agile Release Train (ART), to track data-driven flow metrics help keeps teams predictable, remove execution bottlenecks, and deliver high-quality software continuously.

---

##  Core Flow & SAFe Metrics

### 1. Program Predictability Measure (PPM)
* **What it is:** The percentage ratio of planned **PI Objectives** versus actual **Achieved Business Value** measured at the end of a Program Increment (PI).
* **Target:** **80% – 100%** business value predictability.
* **My Action:** Track iteration burn-up charts regularly to ensure teams deliver their committed features on time, preventing scope carry-over into future iterations.

---

### 2. Flow Velocity & Throughput
* **What it is:** The average number of completed story points or backlog items delivered in each iteration.
* **Target:** Stable throughput with low variance across consecutive sprints.
* **My Action:** During Sprint Planning, I calculate capacity using a **rolling 3-sprint velocity average** to prevent team over-commitment.

---

### 3. Flow Distribution
* **What it is:** The percentage of team capacity split between **Features**, **Enablers** (architecture & infrastructure), **Bugs**, and **Technical Debt**.
* **Target:** A balanced capacity mix (e.g., *70% Features, 20% Enablers/Tech Debt, 10% Bugs*).
* **My Action:** I partner with the Product Owner (PO) and System Architect during Backlog Refinement to ensure technical debt and architectural runway are prioritized next to new business features.

---

### 4. Cycle Time & Work Item Aging
* **What it is:** The total time a user story spends from **"In Progress"** to **"Done"**, and the total duration an active item stays blocked in a single column.
* **Target:** Fast, predictable cycle times (e.g., **1–3 days** per user story).
* **My Action:** I monitor work item age on the Kanban board during daily standups. If an item stays stuck in *Code Review* or *QA* for over **48 hours**, I help the team swarm on it or split it using the **SPIDR** technique.

---

### 5. DORA Metrics (Engineering & Pipeline Health)

| Metric | Definition | Target Goal |
| :--- | :--- | :--- |
| **Deployment Frequency (DF)** | How often code is successfully deployed to staging or production. | High frequency (daily/weekly) |
| **Lead Time for Changes (LTC)** | The total duration from code commit to running live in production. | Short lead times (hours/days) |
| **Change Failure Rate (CFR)** | The percentage of deployments causing pipeline or production failures. | Minimal rate (<10%) |
| **Mean Time to Restore (MTTR)** | How fast the team recovers from an environment failure or outage. | Rapid recovery (<1 hour) |

* **My Action:** I check CI/CD dashboards (*Azure Pipelines, GitHub Actions*) and *AWS CloudWatch* alerts regularly. If build failure rates or automated test suite execution times increase, I prioritize pipeline fixes during Retrospectives.

---

##  Day-to-Day Execution Matrix

### 1. Daily Standup (Daily)
* **Walk the Board:** Facilitate board walk-throughs **right-to-left** (focus on finishing open work before pulling new work).
* **Check Pipeline Health:** Review open Pull Request (PR) turnaround times and check active CI/CD build failure alerts.
* **Unblock Flow:** Identify blocked items and host immediate post-standup **swarming sessions** to resolve technical roadblocks.

### 2. Mid-Iteration (Day 3 & Day 5)
* **Burndown Tracking:** Monitor the Iteration Burndown Chart. If the trend line flattens, facilitate mid-sprint story splitting with the Product Owner.
* **Escalate Dependencies:** Represent the team in the **Coach Sync (Scrum of Scrums)** to escalate cross-team dependencies and risks to the Release Train Engineer (RTE).
* **Refine Backlog:** Lead Backlog Refinement sessions to ensure upcoming user stories meet the **Definition of Ready (DoR)** and enforce an **8-point maximum size limit** per story.

### 3. Iteration Review & Retrospective (End of Sprint)
* **Evaluate Predictability:** Compare the **Commitment vs. Completion Ratio** using objective sprint execution data.
* **Analyze Root Causes:** Run **5 Whys** root-cause analysis on runaway stories (items taking longer than estimated).
* **Actionable Growth:** Convert retro insights into **1 or 2 concrete improvement tasks** and add them directly into the next Sprint Backlog.

### 4. Sprint Planning (Start of Sprint)
* **Capacity Allocation:** Calculate realistic net capacity by factoring in historical velocity, planned time off, and maintenance overhead.
* **Relative Estimation:** Re-anchor story point estimates against standard baseline stories using the team's *Confluence Reference Sheet*.
