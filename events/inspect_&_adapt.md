# SAFe Inspect & Adapt (I&A) Execution Guide

> **Target Audience:** Scrum Masters, Agile Coaches, Release Train Engineers (RTEs), and Data & Engineering Leads.  
> **Purpose:** A structured guide covering the 3 phases of the Inspect & Adapt event, core metrics, execution diagrams, and continuous improvement tools.

---

##  Summary

The **Inspect & Adapt (I&A)** event is a significant SAFe ceremony held at the end of each **Program Increment (PI)** during the **Innovation and Planning (IP) Iteration**. 
When the entire Agile Release Train (ART) converges to analyze delivery performance, evaluate quantitative metrics, and perform root-cause problem solving to create concrete improvement backlog items for the next PI planning session.

   +-----------------------------------------------------------+
   |             INNOVATION & PLANNING (IP) ITERATION          |
   +-----------------------------------------------------------+
   |                                                           |
   |  [ Hackathons & Spikes ]  -->  [ Inspect & Adapt Event ]  |
   |                                       |                   |
   |                                       v                   |
   |                              [ PI Planning Event ]        |
   +-----------------------------------------------------------+

---

##  The 3 Phases of the I&A Event

The I&A event spans **3 to 4 hours** and consists of three distinct phases:

+-----------------------------------------------------------------------------------+
|                            INSPECT & ADAPT FLOW                                  |
+-----------------------------------+-----------------------------------------------+
| PHASE                             | KEY OUTPUT                                    |
+-----------------------------------+-----------------------------------------------+
| 1. PI System Demo                 | Stakeholder feedback on fully integrated ART  |
| 2. Quantitative Measurements      | ART Predictability Score & Quality Metrics    |
| 3. Problem-Solving Workshop       | 1-2 Actionable Improvement Enabler Stories    |
+-----------------------------------+-----------------------------------------------+


---

##  Core Metrics to Track

### 1. ART Predictability Measure
Calculates how reliably the train delivers on its planned **PI Objectives** (excluding uncommitted objectives in the denominator).

$$\text{Predictability Score (\%)} = \left( \frac{\sum \text{Actual Business Value Achieved}}{\sum \text{Planned Business Value}} \right) \times 100$$

* **Target Range:** **80% – 100%**
* **Under 80%:** Indicates systemic bottlenecks, over-commitment, or scope creep.
* **Over 100%:** Indicates sandbagging or under-committing during PI Planning.

### 2. Operational & Quality Metrics Dashboard

| Metric Category | Specific Indicator | Primary Tool | Target / Health Benchmark |
| :--- | :--- | :--- | :--- |
| **Predictability** | Planned vs. Actual Value | Jira Align / Azure DevOps | 80% – 100% target |
| **Flow & Cycle** | Feature Lead Time & Cycle Time | Tableau / Power BI / Kanban | Decreasing trend or stable SLA |
| **Data & Quality** | Escaped Defect Rate | Jira / GitHub Issues | Zero Critical in production |
| **Tech Debt** | Unplanned Refactoring Work | SonarQube / Git Analytics | $< 15\%$ of team capacity |
| **Pipelines** | Deployment / ETL Failure Rate | GitHub Actions / Databricks | $> 95\%$ successful runs |

---

## 🛠️ Step-by-Step Problem-Solving Workshop

The **Problem-Solving Workshop** 
(Phase 3) is a 2-hour exercise designed to find systemic root causes rather than surface-level symptoms.

+-------------------+      +--------------------+      +-------------------+
|  1. Agree on the  | ---> |  2. Root-Cause     | ---> |  3. Identify      |
|     Problem       |      |     Analysis       |      |     Root Cause    |
+-------------------+      +--------------------+      +-------------------+
|
+-------------------+      +--------------------+                v
|  5. Create        | <--- |  4. Brainstorm     | <------------------+
|     Improvement   |      |     Solutions      |
|     Enablers      |      +--------------------+
+-------------------+


+-------------------+     +--------------------+     +--------------------+
|  1. Briefing &    | --> |  2. Root-Cause     | --> |  3. Identify       |
|     Problem       |     |     Analysis       |     |     Root Cause     |
|     Statement     |     |     (Fishbone)     |     |     (5 Whys)       |
+-------------------+     +--------------------+     +--------------------+
       (15 mins)                 (30 mins)                 (15 mins)
|
+-------------------+     +--------------------+                 v
|  5. Create        | <-- |  4. Brainstorm     | <-------------------+
|     Improvement   |     |     Solutions      |
|     Backlog Item  |     |  (Impact/Effort)   |
+-------------------+     +--------------------+
       (30 mins)                 (30 mins)



### Workshop Breakdown & Script

1. **Agree on the Problem Statement (15 min):**  
   *Restate the issue clearly.*  
   *Example:* *"Data transformation pipelines failed SLA 4 times this PI, causing delayed morning reporting for Business Intelligence stakeholders."*
2. **Root-Cause Analysis (Fishbone / 5 Whys) (30 min):**  
   Analyze symptoms across categories: **People, Process, Tools, Governance, Infrastructure**.
3. **Identify Primary Root Cause (15 min):**  
   Use **Pareto Analysis (80/20 rule)** or dot-voting to isolate the single root cause contributing most to the failure.
4. **Brainstorm Solutions (30 min):**  
   Generate actionable fixes. Avoid vague statements like *"Improve communication"*.
5. **Create Improvement Backlog Items (30 min):**  
   Convert top solutions into explicit **Enabler Stories** or **Improvement Stories** with assigned owners.

---

##  Root-Cause Analysis Artifacts

### 1. Fishbone (Ishikawa) Diagram
Organize findings using this layout during your breakout sessions:

 Process                Tools              Governance
    \                     \                     \
     \                     \                     \
----------+---------------------+---------------------+-------> [ SYMPTOM ]
     /                     /                     /
    /                     /                     /
People             Data / Infra           Dependencies


### 2. The 5 Whys Chain Example

[Symptom] Snowflake cost exceeded budget by 40% & queries were slow.
|
+--> WHY? Nightly batch transformation jobs took 7 hours instead of 1.5 hours.
|
+--> WHY? Queries performed full-table scans instead of incremental loads.
|
+--> WHY? Raw staging schemas lacked incremental audit timestamps.
|
+--> WHY? Upstream database API contract did not enforce schema versioning.
|
+--> [ROOT CAUSE]: Lack of Data Contract governance between upstream producers and the data team.


---

##  Recommended Interactive Tools

To run an engaging remote or hybrid I&A workshop, leverage these digital platforms:

* **Board Platforms:** [Miro](https://miro.com/) | [Mural](https://mural.co/) | [Lucidspark](https://lucidspark.com/)
* **Agile Management:** Jira Align | Azure DevOps Boards | Kendis
* **Pre-built Templates:**
  * [Atlassian 5 Whys Playbook](https://www.atlassian.com/team-playbook/plays/5-whys)
  * [Creately Sailboat / Speedboat Retrospective Guide](https://creately.com/guides/how-to-run-a-sailboat-retrospective/)
  * [SAFe Official Inspect and Adapt Overview](https://www.scaledagileframework.com/inspect-and-adapt/)

---

##  Facilitator Checklist

- [ ] **2 Weeks Before:** Verify that all team PI Objectives have assigned Business Values from Business Owners.
- [ ] **1 Week Before:** Confirm that system demo environments are stable and data dashboards are refreshed.
- [ ] **Day Of Event:** Enforce timeboxes strictly—use visual timers (5–10 min for silent brainstorming).
- [ ] **Post-Event:** Ensure the top 1–2 **Improvement Stories** are entered into the ART Backlog and prioritized for the upcoming **PI Planning session**.

- [ ] ---

   ###  I&A Checklist
  
  ## Phase 1
- [ ] **Pre-Event Preparation** (1–2 Weeks Before)
- [ ]
- [ ]  [ ] Verify Objective Values: Ensure Business Owners have assigned Actual Business Value scores ($1–10$) for all completed PI Objectives.
- [ ] [ ] Gather Metrics: Collect team data (Predictability Score, Escaped Defects, Cycle Time, Velocity stability).
- [ ] [ ] Test Demo Environment: Verify that integrated system demos, data pipelines, or reporting dashboards are working without live failure risks.
- [ ] [ ] Set Up Virtual Board: Prepare your digital whiteboard (Miro/Mural) with pre-drawn templates for Fishbone, 5 Whys, and Action Items.
- [ ] [ ] Confirm Key Stakeholders: Ensure Product Managers, System Architects, and Business Owners are explicitly invited to join the team breakouts.
- [ ]
  ## Phase 2
- [ ] **Event Execution (Day of Event)
- [ ]  [ ] Stage 1 — System Demo (45–60 min): Facilitate team participation in demonstrating integrated features to business stakeholders.
- [ ]  [ ] Stage 2 — Performance Metrics (30 min): Present team predictability measures and open-floor metric reflection.
- [ ]  [ ] Stage 3 — Problem Statement Agreement (15 min): Help the team choose one systemic problem to address (avoid fixing micro-bugs here).
- [ ]  [ ] Stage 4 — Root-Cause Analysis (45 min): Guide the team through a Fishbone Diagram and 5 Whys exercise.
- [ ] [ ] Stage 5 — Brainstorming & Action Items (30 min): Limit output to 1 or 2 concrete improvement stories with assigned owners.
- [ ]
  ## Phase 3:
- [ ] **Post-Event Follow-Up (Immediate)
- [ ]
- [ ] [ ] Publish Artifacts: Export board outputs (Fishbone, Action Items) and link them to the team workspace (Confluence/GitHub Pages).
- [ ] [ ] Feed into PI Planning: Ensure the top 1–2 improvement items are logged as Enabler/Improvement Stories in Jira/Azure DevOps and prioritized in the upcoming PI backlog.
