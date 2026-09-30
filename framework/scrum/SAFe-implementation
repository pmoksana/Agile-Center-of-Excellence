# SAFe Implementation Framework: Launching an ART for 20 People

This framework guides a **Scrum Master / Agile Team Coach** in building and launching a **Scaled Agile Framework (SAFe)** environment from scratch for a **20-person cross-functional group**. 

Even with a compact setup, applying SAFe principles ensures alignment, manages cross-discipline dependencies (especially across engineering and data), and maintains a steady flow of business value.

---

## 1. Organizational & Team Design

To avoid team silos, structure your 20 people into **2–3 cross-functional Agile Teams** operating on a single **Agile Release Train (ART)**. Avoid organizing teams by function (e.g., a pure "Data Team" vs. a pure "Engineering Team"), as this creates handoff delays and integration bottlenecks.

### Proposed Team Structure (2 Cross-Functional Teams)
                   ┌─────────────────────────────────────┐
                   │           ART LEADERSHIP            │
                   │ • Product Manager                   │
                   │ • Release Train Engineer / SM Lead  │
                   │ • System / Data Architect           │
                   └──────────────────┬──────────────────┘
                                      │
              ┌───────────────────────┴───────────────────────┐
              ▼                                               ▼
┌───────────────────────────────────┐           ┌───────────────────────────────────┐
│     TEAM 1: Feature / App Team    │           │    TEAM 2: Data & Insights Team   │
├───────────────────────────────────┤           ├───────────────────────────────────┤
│ • Product Owner (1)               │           │ • Product Owner (1)               │
│ • Scrum Master (1)                │           │ • Scrum Master (1)                │
│ • Software Engineers (4)          │           │ • Data Engineers (3)              │
│ • Data Analyst (1)                │           │ • Data Analysts (2)               │
│ • Data Engineer (1)               │           │ • Software Engineer (1)           │
└───────────────────────────────────┘           └───────────────────────────────────┘

### Roles & Responsibilities Matrix

| Role | Count | Primary SAFe Responsibility |
| :--- | :---: | :--- |
| **Product Manager (PM)** | **1** | Owns the **ART Backlog** (Features), defines market vision, and manages WSJF prioritization. |
| **Product Owners (PO)** | **2** | Own local **Team Backlogs** (Stories), refine acceptance criteria, and make daily priority calls. |
| **Scrum Masters (SM)** | **2** | Facilitate daily flow, remove impediments, enforce WIP limits, and co-run ART synchronization. |
| **Data Engineers** | **4** | Build data pipelines, ETL/ELT pipelines, data models, and database infrastructure. |
| **Data Analysts** | **3** | Deliver analytics dashboards, feature tracking metrics, data queries, and ML models. |
| **Software Engineers** | **5** | Build application features, API integrations, and front-end/back-end infrastructure. |
| **System / Data Architect** | **1** | Defines architectural runway, data governance standards, and system designs. |

---

## 2. Step-by-Step Implementation Roadmap
┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐
│  Phase 1: Preparation   │ ──► │  Phase 2: Alignment     │ ──► │ Phase 3: First PI Plan  │ ──► │   Phase 4: Execution    │
│    (Weeks 1 - 2)        │     │     (Weeks 3 - 4)       │     │     (2-Day Event)       │     │     (8 - 12 Weeks)      │
└─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘     └─────────────────────────┘

### Phase 1: Preparation & Backlog Setup (Weeks 1–2)
* **Define the Cadence:** Set a standard cadence for the entire train:
  * **PI Length:** 8–10 weeks (4–5 iterations of 2 weeks each).
  * **Innovation & Planning (IP) Iteration:** Reserve the final 2 weeks of the PI for buffer, innovation, retrospectives, and PI preparation.
* **Build the ART Backlog:** Guide the Product Manager and Architect to write initial **Features** (Business & Architecture Enablers).
* **Establish Definition of Done (DoD):** Define cross-discipline quality rules (e.g., *code reviewed, unit tests passed, data pipeline validated, schema documented*).

### Phase 2: Training & Value Stream Alignment (Weeks 3–4)
* **Train the Teams:** Conduct foundational Lean-Agile training for developers, analysts, and data engineers. Focus on:
  * Decoupling releases from deployments.
  * Estimating with relative story points.
  * Managing dependencies between data pipelines and app software.
* **Pre-PI Planning Alignment:** Host a Pre-PI session with the PM, POs, SMs, and Architects to estimate feature sizes using Weighted Shortest Job First (**WSJF**).

### Phase 3: Execute the First PI Planning Event (2-Day Event)
* **Day 1:**
  1. Executive presentation of Vision and Business Context.
  2. Product Manager presents the top 10 ART Features.
  3. Team Breakout #1: Teams draft initial iteration plans, identify cross-team data dependencies, and log risks.
* **Day 2:**
  1. Adjust plans based on management feedback.
  2. Team Breakout #2: Finalize team PI Objectives and draft Uncommitted Objectives.
  3. Assign **Planned Business Value (1–10)** with Business Owners.
  4. Conduct the **ROAM Risk Session** (*Resolved, Owned, Accepted, Mitigated*) and take the Confidence Vote.

### Phase 4: PI Execution & Synchronization
* Execute 2-week iterations using standardized SAFe synchronization events.

---

## 3. Cadence & Sync Event Framework

| Event | Frequency | Participants | Objective |
| :--- | :--- | :--- | :--- |
| **Daily Standup** | Daily (15 mins) | Team Members, PO, SM | Walk board right-to-left; focus on closing active stories and unblocking flow. |
| **ART Sync / Coach Sync** | Weekly (30–45 mins) | PM, POs, SMs, RTE | Review train-level flow, resolve cross-team dependencies (e.g., API vs. Data Pipeline readiness), and manage PI risks. |
| **Backlog Refinement** | Weekly (60 mins) | PO, Team, Analysts/Engineers | Refine upcoming user stories, ensure they meet **Definition of Ready (DoR)**, and enforce an **8-point max size cap**. |
| **System Demo** | End of Iteration (60 mins) | Entire ART + Stakeholders | Demonstrate integrated, working software and live data pipelines built during the sprint. |
| **Inspect & Adapt (I&A)** | End of PI (Half-Day) | Entire ART | Calculate the **Program Predictability Measure (PPM)** and conduct a 5-Whys problem-solving workshop. |

---

## 4. Integrating Data Engineering & Data Analytics into SAFe

Data work often breaks standard Agile execution due to long discovery phases, fluctuating data schemas, and pipeline dependencies. Implement these rules to keep data work flowing:

┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        DATA & APPLICATION INTEGRATION FLOW                             │
├───────────────────────────────────┬────────────────────────────────────────────────────┤
│ Iteration N-1 (Discovery)         │ Iteration N (Build & Integration)                  │
├───────────────────────────────────┼────────────────────────────────────────────────────┤
│ • Data Analyst writes specs &     │ • Data Engineer builds & deploys pipeline.         │
│   queries.                        │ • Software Engineer connects API to live pipeline. │
│ • Schema contracts are agreed.   │ • Analyst validates output on live data dashboard. │
└───────────────────────────────────┴────────────────────────────────────────────────────┘


1. **Enforce Spike Stories for Data Discovery:** Never pull an unquantified data analysis task directly into an execution sprint. Use timeboxed **Spikes** (1–3 days) to explore dataset availability before estimating build stories.
2. **Establish Data Contracts:** Create schema agreements between Software Engineers and Data Engineers *before* development begins on an feature to avoid broken downstream pipelines.
3. **Use Spikes for Pipeline Refactoring:** Frame database migrations and pipeline refactoring as **Architecture Enablers** in the ART Backlog so they receive dedicated capacity allocation (e.g., 20% capacity).

---

## 5. Tooling & Dashboard Configuration (Jira / Azure DevOps)

### Board Setup & Custom Fields
* **Issue Types:** `Feature` (ART level), `User Story` (Team level), `Enabler` (Technical/Data runway), `Spike` (Research).
* **Custom Fields to Add:**
  * `Planned Business Value` (Number: 1–10)
  * `Actual Business Value` (Number: 1–10)
  * `Is Uncommitted?` (Checkbox: Yes/No)
  * `Target PI` (Select List: e.g., `PI-2026.1`)

### Essential SAFe Flow Metrics to Track

| Metric | Target Goal | SM Action Plan |
| :--- | :---: | :--- |
| **Program Predictability Measure (PPM)** | **80% – 100%** | Track actual vs. planned business value scored by Business Owners at every PI System Demo. |
| **Work Item Aging** | **< 48 hours in review** | Monitor Kanban boards daily; initiate swarming if data pipelines or PRs sit idle in code review/testing. |
| **Flow Distribution** | **70/20/10 Split** | Ensure capacity allocation is split effectively: 70% Features, 20% Enablers/Data Debt, 10% Bugs. |
| **Cycle Time** | **1–3 Days per story** | Use the SPIDR technique to split large data or engineering stories into smaller increments. |
