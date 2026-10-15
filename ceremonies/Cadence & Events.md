# SAFe Cadence & Events Guide

This Guide explain all standard events and continuous execution activities within the **Scaled Agile Framework (SAFe)** at both the **Train (ART)** and **Team** levels. 
It details timing, duration, value, participants, and how **Inspect & Adapt (Continuous Improvement)** operates inside each event, with specific checklist.

---

## 1. Summary Cadence & Event Matrix

| Event / Activity | Frequency / Timing | Duration | Key Participants | Scrum Master Role |
| :--- | :--- | :--- | :--- | :--- |
| **PI Planning** | Once per PI (Start of PI) | 2 Full Days | Entire ART, RTE, PM, System Architect, Business Owners | Facilitates team breakouts, manages risks, enforces capacity limits |
| **Daily Standup (DS)** | Daily (Every morning) | 15 Minutes | Team (Devs, Data, QA), PO, SM | Facilitates right-to-left board walk, identifies blockers and aging work |
| **Backlog Refinement** | 1–2 times per Sprint | 60 Minutes | PO, SM, Agile Team (Devs, Data, QA) | Enforces Definition of Ready (DoR), max 8-pt sizing, data contracts |
| **Iteration Review / Demo** | End of every Iteration | 60 Minutes | Team, PO, SM, Business Stakeholders | Ensures objective, working software/pipeline demos (no PowerPoint) |
| **Iteration Retrospective** | End of every Iteration | 45–60 Minutes | Scrum Master, PO, Agile Team | Facilitates root-cause analysis, adds 1–2 retro items to next backlog |
| **Coach Sync (Scrum of Scrums)** | Weekly (or 2x/week) | 30–45 Minutes | RTE, Scrum Masters, System Team reps | Escalates cross-team dependencies, risks, and train-level flow bottlenecks |
| **System Demo** | End of every Iteration | 60 Minutes | Entire ART, RTE, PM, Business Owners | Validates integrated train-level increment across all teams |
| **Inspect & Adapt (I&A)** | End of PI (IP Iteration) | 3–4 Hours (Half Day) | Entire ART, Business Owners, RTE, PM | Co-facilitates metrics review and the 5-Whys Problem-Solving Workshop |

---

## 2. Detailed Event Breakdown

### 1. PI Planning

* **When Held:** At the beginning of every Program Increment (PI), during the Innovation and Planning (IP) Iteration.
* **Duration:** 2 Full Days (16 hours).
* **Goal & Value:** Aligns the entire Agile Release Train (ART) around a shared mission, builds the PI roadmap, resolves cross-team dependencies, and secures Business Owner alignment.
* **Participants:** Entire ART (All Agile Teams, Scrum Masters, Product Owners, Product Manager, Release Train Engineer, System/Data Architect, Business Owners).
* **Scrum Master Role:** Facilitator for team breakout sessions, risk monitor, and protector of team capacity.
* **What Scrum Master Checks:**
  - [ ] Net team capacity calculated accurately (factoring in PTO, maintenance, 70/20/10 split), - [ ] [Team Capacity](https://github.com/pmoksana/Agile-Center-of-Excellence/blob/main/role/scrum-master/team_capacity.md) calculated accurately (factoring in PTO, maintenance, 70/20/10 split).
  - [ ] Unclear data work or unknown APIs converted into **1–3 day Spikes**.
  - [ ] Cross-team dependencies logged clearly on the ART Planning Board.
  - [ ] Draft PI Objectives formatted as outcomes (not activity lists) with assigned Business Values.
* **Inspect & Adapt Element:** Teams reflect on previous PI performance/velocity to adjust sprint loading and evaluate dependency patterns from prior quarters.

---

### 2. Daily Standup (DS)

* **When Held:** Daily, at the start of the working day.
* **Duration:** 15 Minutes.
* **Goal & Value:** Syncs team alignment on iteration progress, surface bottlenecks immediately, and coordinates daily swarming to keep work flowing.
* **Participants:** Agile Team (Software Engineers, Data Engineers, Data Analysts, QA), Product Owner, Scrum Master.
* **Scrum Master Role:** Flow facilitator and impediment remover.
* **What Scrum Master Checks:**
  - [ ] Board walked **right-to-left** (closing open work before starting new work).
  - [ ] Pull Requests (PRs) or schema reviews sitting idle for **> 24–48 hours**.
  - [ ] Work items adhering to Work-In-Process (WIP) limits.
  - [ ] Blockers flagged immediately for post-standup swarming sessions.
* **Inspect & Adapt Element:** Daily micro-adjustments to execution plans based on current iteration burndown slopes and unexpected pipeline blocks.

---

### 3. Backlog Refinement

* **When Held:** Mid-iteration (typically 1–2 times per 2-week sprint).
* **Duration:** 60 Minutes per session.
* **Goal & Value:** Prepares upcoming user stories and enablers so they are fully estimated, clear, and ready for future sprint execution.
* **Participants:** Product Owner, Agile Team members (Developers, Analysts, Engineers), Scrum Master.
* **Scrum Master Role:** Process guardian ensuring items meet technical and clarity standards.
* **What Scrum Master Checks:**
  - [ ] Stories meet the **Definition of Ready (DoR)**.
  - [ ] Story size cap enforced (No story larger than **8 story points**; split using SPIDR if larger).
  - [ ] Data Contracts and input/output schemas defined for data pipeline tasks.
  - [ ] Acceptance criteria explicit and testable.
* **Inspect & Adapt Element:** Evaluates past story estimation accuracy to refine how the team splits and sizes upcoming backlog items.

---

### 4. Iteration Review & System Demo

* **When Held:** At the end of every 2-week iteration (Iteration Review at Team level; System Demo at ART level).
* **Duration:** 60 Minutes each.
* **Goal & Value:** Measures progress by evaluating objective, working software and live data pipelines with stakeholders.
* **Participants:** Team, PO, SM, Business Owners, PM, RTE, Key Stakeholders.
* **Scrum Master Role:** Facilitator and objective feedback organizer.
* **What Scrum Master Checks:**
  - [ ] Demonstrations focus on **working code/dashboards**, not PowerPoint slides.
  - [ ] Completed stories meet the full **Definition of Done (DoR)**.
  - [ ] Unfinished stories are moved back to the backlog without artificial point credit.
* **Inspect & Adapt Element:** Gathers immediate stakeholder feedback on delivered features to adjust upcoming sprint priorities and backlog acceptance criteria.

---

### 5. Iteration Retrospective

* **When Held:** At the very end of each iteration, immediately following the Iteration Review.
* **Duration:** 45–60 Minutes.
* **Goal & Value:** Drives continuous improvement at the team level by evaluating team dynamics, processes, and engineering practices.
* **Participants:** Scrum Master, Product Owner, Agile Team.
* **Scrum Master Role:** Retrospective leader and objective facilitator.
* **What Scrum Master Checks:**
  - [ ] Focus stays on process and flow improvement, not personal blame.
  - [ ] Sprint data reviewed (Velocity variance, Cycle time, Unplanned scope creep).
  - [ ] Root causes analyzed using techniques like the **5 Whys**.
  - [ ] Exactly **1 or 2 concrete improvement items** are created and placed directly into the next Sprint Backlog.
* **Inspect & Adapt Element:** This is the core team-level I&A engine, directly converting execution lessons into actionable backlog improvement items.

---

### 6. Coach Sync (Scrum of Scrums)

* **When Held:** Weekly (or twice weekly during intense execution).
* **Duration:** 30–45 Minutes.
* **Goal & Value:** Provides visibility into train-level flow, resolves cross-team dependencies, and escalates risks impacting overall PI Objectives.
* **Participants:** Release Train Engineer (RTE), Scrum Masters / Team Coaches, System Team representatives.
* **Scrum Master Role:** Team representative and risk escalator.
* **What Scrum Master Checks:**
  - [ ] Cross-team data dependencies (e.g., API release vs. pipeline ingestion) on track.
  - [ ] Impediments that the local team cannot resolve escalated to the RTE.
  - [ ] ART-level risks updated in the train ROAM board.
* **Inspect & Adapt Element:** Evaluates train-level flow impediments and shifts resources or swarming capacity across teams mid-PI.

---

### 7. Inspect & Adapt (I&A) Event

* **When Held:** At the end of every Program Increment (PI), during the IP Iteration.
* **Duration:** 3 to 4 Hours (Half-Day Event).
* **Goal & Value:** Systematically evaluates ART performance, measures predictability, and solves systemic organizational issues.
* **Participants:** Entire ART (All Teams, RTE, PM, Business Owners, Executive Leadership).
* **Scrum Master Role:** Workshop co-facilitator and table group leader.
* **What Scrum Master Checks:**
  - [ ] Final team achievement scores collected for the **Program Predictability Measure (PPM)**.
  - [ ] Team actively participates in the 5-Whys / Fishbone root-cause analysis.
  - [ ] Resulting improvement items formatted as actionable **Features or Enablers** for the upcoming PI Planning event.
* **Inspect & Adapt Element:** The macro-level improvement event of SAFe, feeding strategic process improvements directly into the train's next PI Backlog.
