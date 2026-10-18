# 5 Best Practice Techniques for Identifying Primary Root Causes

> **Target Audience:** Scrum Masters, Agile Coaches, Release Train Engineers (RTEs), and Workshop Facilitators.  
> **Workshop Context:** Phase 3 of the SAFe **Inspect & Adapt (I&A)** Problem-Solving Workshop.  
> **Objective:** Transition from broad brainstorming on a Fishbone diagram to pinpointing the single, highest-impact **Primary Root Cause** before developing solutions.

---

##  Technique Selection Overview

When teams finish populating a **Fishbone (Ishikawa) Diagram**, they are often left with 15 to 30 potential factors. 
Jumping straight to solutions at this point leads to fixing surface-level symptoms. 

To isolate the *true* primary root cause, choose the technique that best fits your team's available data and scenario:

| Technique | Primary Use Case | Facilitation Complexity | Data Required |
| :--- | :--- | :--- | :--- |
| **1. The 5 Whys Deep-Dive** | Linear cause-and-effect chains | 🟢 Low | Qualitative / Team knowledge |
| **2. Pareto Analysis (80/20 Rule)** | Frequent defects, error logs, or recurring failures | 🟡 Medium | Quantitative (counts, logs, metric history) |
| **3. Dot Voting with Constraints** | High volume of brainstormed causes on a Fishbone | 🟢 Low | Consensus / Team judgment |
| **4. Impact vs. Control Matrix** | Complex organizational or cross-team dependencies | 🟡 Medium | Qualitative / Systemic context |
| **5. Fault Tree Analysis (FTA)** | High-risk technical failures or pipeline crashes | 🔴 High | System logs & architectural maps |

---

## 1.  The 5 Whys Deep-Dive

### How It Works
Take the top cluster from your Fishbone diagram and recursively ask **"Why?"** 3 to 5 times. Each answer forms the premise of the next question until you hit a systemic policy, contract, or technical gap.

### Best Practice Rules
* **Trace facts, not assumptions:** Base each "Why" on observable team behavior or system logs.
* **Avoid blaming people:** If an answer is *"Because John forgot to test,"* ask *"Why did the system allow untested code into production?"*

### Execution Template
[ SYMPTOM ] -> High database compute costs & pipeline SLA breaches.|+-- 1. WHY? -> Nightly ETL jobs took 6 hours instead of 1 hour.|+-- 2. WHY? -> Queries executed full-table scans instead of incremental loads.|+-- 3. WHY? -> Raw staging tables lacked incremental timestamp flags.|+-- 4. WHY? -> Upstream database updates were pushed without contract validation.|+-- 5. [PRIMARY ROOT CAUSE] -> No enforced Data Contract policy between software & data teams.
---

## 2.  Pareto Analysis (The 80/20 Rule)

### How It Works
Based on the principle that **80% of system failures stem from 20% of causes**. This technique requires sorting recorded incident data by frequency or downtime cost.

### Best Practice Rules
1. Categorize incident occurrences from the past Program Increment (PI).
2. Rank categories in descending order of frequency or financial impact.
3. Target the top 1 or 2 categories that account for the majority of cumulative losses.

### Execution Example

Failure Cause Frequency Distribution (Last PI)[X] Upstream Schema Changes     ████████████████████ (18 incidents)  <-- 80% Impact Zone
[X] Unclaimed Permissions / Access ██████████        (9 incidents)   <-- 80% Impact Zone
[ ] Flaky Unit Tests            ███                  (3 incidents)
[ ] Network Timeout             █                    (1 incident)> **Outcome:** Focus root-cause analysis exclusively on **Upstream Schema Changes** and **Access Permissions**.

---

## 3.  Constrained Dot Voting (3-Spot Rule)

### How It Works
When quantitative data is unavailable, use structured dot-voting on the completed Fishbone diagram to leverage collective team intelligence.

### Best Practice Rules
* **Limit votes strictly:** Give each participant **3 voting dots**.
* **Rule of Focus:** Participants can place a maximum of **2 dots on a single item** if they feel strongly about it.
* **Silent Voting:** Conduct voting simultaneously (e.g., using Miro/Mural voting features) to avoid senior team members influencing others (HiPPO effect - Highest Paid Person's Opinion).

### Facilitation Script
> *"We have 20 potential causes on our Fishbone. Take your 3 voting dots and place them on the root cause that, if solved today, would eliminate the largest number of secondary problems."*

---

## 4.  Impact vs. Control Matrix

### How It Works
Plot candidate causes from the Fishbone board onto a $2 \times 2$ grid comparing **Systemic Impact** against **Team Control / Influence**.

### The Matrix Layout

              HIGH SYSTEMIC IMPACT
                       ^
                       |
 [ FOCUS ZONE ]        |     [ ESCALATION ZONE ]
(Primary Root Causes     |    (Take to RTE / ARTthe team can solve)      |     Leadership at I&A)|-------------------------+-------------------------> HIGH TEAM CONTROL|[ OUT OF SCOPE ]      |     [ MINOR DISTRACTIONS ](Ignore for now)        |      (Do not spend PI|        capacity here)|LOW SYSTEMIC IMPACT
### Best Practice Outcome
Select the primary root cause from the **FOCUS ZONE** (High Impact, High/Medium Team Control). If the primary cause falls in the **ESCALATION ZONE**, frame it as an **ART-level Risk / Enabler** for the RTE during PI Planning.

---

## 5.  Fault Tree Analysis (FTA)

### How It Works
A top-down, deductive failure analysis technique used for complex technical or infrastructure failures. It maps how combinations of sub-system failures lead to an overall system event using logical gates (`AND` / `OR`).

### Execution Structure

                  +-------------------------------+
                  |   PRIMARY EVENT: ETL Crash    |
                  +-------------------------------+
                                  |
                              [ OR Gate ]
                             /           \
             +--------------+           +--------------+
             | Out of Memory|           | Schema Drift |
             +--------------+           +--------------+
                    |                          |
               [ AND Gate ]               [ OR Gate ]
              /          \               /           \
     +-------+     +-------+       +-------+       +-------+
     | Spike |     | Bad   |       | Drop  |       | Type  |
     | Volume|     | Config|       | Column|       | Change|
     +-------+     +-------+       +-------+       +-------+

---

##  Facilitator Checklist for Root-Cause Validation

Before moving from root-cause identification to brainstorming solutions, validate the selected root cause with these 3 questions:

- [ ] **Fact Check:** Is this cause backed by logs, metrics, or unanimous team experience (rather than speculation)?
- [ ] **System Focus:** Does fixing this cause address a *process, tool, or contract issue* rather than placing blame on an individual?
- [ ] **Controllability:** Does the team have the authority—or a clear escalation path to the ART—to implement a solution for this cause during the next PI?
