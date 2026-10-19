## Team Sync (Facilitating & Evaluating)

In SAFe 6, the **Team Sync** replaces the traditional "Daily Standup" to emphasize:
**flow, objective alignment, and dynamic** replanning over static status reporting. 

It is a short, daily 15-minute event for the Agile Team to **evaluate Progress toward Iteration Goals, identify flow Bottlenecks, and adjust the daily plan.**


 <<Maturity level teams knows that *Daily 15-minute meeting to walk the board right-to-left, check progress toward the Iteration Goal, enforce WIP limits, and clear blockers.<<


 **Objectives** of the SAFe 6 Team Sync
 
┌─────────────────────────────────────────────────────────────────────────── ──┐
│                       SAFE 6 TEAM SYNC OBJECTIVES                            │
├──────────────────────────────────────────────────────────────────────────── ─┤
│ **1. Align on Iteration Goals:** Keep the focus on outcomes, not tasks.      │
│ **2. Optimize Flow:** Walk the board right-to-left to clear bottlenecks.     │
│ **3. Uncover Impediments:** Surface pipeline, data, or environment blocks.   │
│ **4. Dynamic Replanning:** Adapt daily execution based on new learnings.     │
└──────────────────────────────────────────────────────────────────────────────┘


## Non-Negotiable Rules of Team Sync
Timeboxed to 15 Minutes: Keep it crisp, energetic, and focused.

-- For the Team, By the Team: The event is hosted by and for the Agile Data Squad - it is not a status report to the Scrum Master or Product Owner.

-- Walk the Board Right-to-Left: Focus on completing work in progress **(WIP)** near the finish line before pulling new stories from the left.

-- Take **Off-Topic Discussions Offline** ("Meet-After"): Technical design decisions, complex SQL query debugging, or lengthy block reviews happen immediately after the 15-minute sync in a dedicated "Meet-After" session.

---

**Focus on Iteration Goals:** Every squad member aligns their daily contribution with the overall sprint commitments.

 How to Coach the Team: The 3 Flow Questions
Instead of asking the traditional individual-centric questions ("What did I do yesterday? What will I do today?"), coach your team to focus on **story flow and pipeline progress**:

Traditional Standup Question (Avoid)	SAFe 6 Flow-Centric Question (Use)
"What did you work on yesterday?"	>> "What user stories or data contracts can we close or push to 'Done' today?"
"What are you working on today?"	>> "Where is work blocked or stuck in WIP (e.g., long PR reviews, pipeline failures)?"
"Do you have any blockers?"	>> "Are we still on track to achieve our Iteration Goals?"

---

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
## SM Checklist: Refining & Evaluating Team Sync

Checklist during and after Team Sync to evaluate whether the ceremony is producing value or slipping into anti-patterns.

---

# Phase 1: Preparation & Setup Checklist (Before Sync)
[ ] Is the digital Kanban/Scrum board (Jira/Azure DevOps) fully up to date prior to the call?

[ ] Are active WIP limits visually **defined and visible** to all squad members?

[ ] Is the current **Iteration Goal** clearly displayed at the top of the board?

[ ] Is an automated timer ready to enforce the 15-minute timebox?


# Phase 2: Execution Checklist (During Sync)
[ ] Right-to-Left Focus: Does the team start reviewing items in Testing/Review before looking at In Progress or To Do?

[ ] Swarming Behavior: Does the team offer to help unblock peer stories rather than taking on new parallel tasks?

[ ] Impediment Identification: Are blockers clearly flagged with red tags on the board and assigned an owner?

[ ] Meet-After Parking Lot: Are deep-dive technical discussions parked for the post-sync session without interrupting the 15-minute flow?


# Phase 3: Evaluation Checklist — How Valuable & Productive is Your Sync?
Evaluate your team’s Team Sync maturity every 2–4 weeks using this scorecard:

Evaluation Criteria	🔴 Red Flag (Needs Coaching)	🟡 Yellow Flag (Improving)	🟢 Green Light (High Value)

Focus & Orientation	Team members report individual updates to the SM/PO.
Team members talk to each other but focus strictly on tasks.
Team walks the board right-to-left, focusing on closing stories and achieving Iteration Goals.
WIP Management	Work in Progress continuously exceeds limits; many stories open simultaneously.	
WIP limits are respected, but individual silos persist.
Team swarms on stymied stories to pull them to "Done" before starting new work.
Impediment Handling	Blockers are hidden, ignored, or debated for 10+ minutes during the sync.	Blockers are identified, but no clear owner or escalation plan is named.	
Blockers are tagged instantly, logged, parked for the "Meet-After," and assigned an owner or escalated to the RTE.
Timeboxing & Engagement	Sync regularly runs past 15 minutes; team members tune out.	
Sync hits 15 minutes, but parking lot discussions bleed into the main call.	
Sync finishes in ≤15 minutes; team transitions cleanly into a 5–10 minute focused "Meet-After."


### TEAM SYNC (15 Mins) - Walk the Board Right-to-Left
- [ ] **Step 1: Check Done / Validation Column**
      - Are completed items verified against DoD and dbt/Airflow tests passed?
- [ ] **Step 2: Check PR / In Review Column**
      - Any PR open > 24 hours? Prompt team members to pair and unblock.
- [ ] **Step 3: Check In Progress Column**
      - Is anyone exceeding WIP limits (> 2 items)? 
      - Are there hidden technical blockers or schema issues?
- [ ] **Step 4: Review Blockers & Impediment Log**
      - Log owner and escalation SLA for any new blocker (IAM access, missing source data).

---
## Step-by-Step Coaching Script for the team

"Team, in SAFe 6, our Team Sync isn’t a daily status update where we prove we’ve been busy - it’s our **daily strategy session to win the sprint**.

We start from the right: We look at what is closest to production - like Pull Requests, BDD test validations, or schema reviews—and ask: **'How do we get this to Done today?'**
We protect our flow: If something is stuck, we swarm on it together instead of opening another story and overloading our WIP.
We keep it tight: We stick to our 15-minute timebox for alignment, and take deep-dive technical problem-solving into our **'Meet-After'session.**
When we run our Team Sync this way, we keep our pipeline moving, remove blockers fast, and consistently hit our Iteration Goals!
