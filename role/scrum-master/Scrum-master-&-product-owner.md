# Scrum Master & Product Owner Collaboration Framework

## 1. How the Scrum Master Interacts with the Product Owner

The SM and PO must maintain a daily, high-alignment partnership to prevent scope creep, misaligned priorities, and sprint spillover.

### Daily & Operational Touchpoints
* **Pre-Standup Sync (10–15 mins daily):** Brief check-in to realign on sprint priorities, review potential blockers, and check if any user stories need scope adjustment before the daily team sync.
* **Joint Refinement ("Three/Four Amigos"):** SM facilitates refinement sessions where PO brings business intent, and developers, data analysts, and cloud engineers provide technical estimates and schema/infrastructure constraints.
* **Capacity Guardrail Enforcement:** During Iteration Planning, SM ensures the PO respects historical capacity limits (e.g., using "Yesterday's Weather" and the 80% capacity rule) rather than over-committing the team.
* **Backlog Health Auditing:** SM ensures the PO maintains a prioritized, refined backlog containing at least 2 sprints worth of stories meeting the **Definition of Ready (DoR)**.

---

## 2. Key Metrics Used to Support & Guide the PO

The Scrum Master uses flow and delivery metrics to coach the PO on backlog management, scope stability, and predictability.

| Metric | What It Measures | How the SM Uses It to Coach the PO |
| :--- | :--- | :--- |
| **WSJF (Weighted Shortest Job First)** | $\frac{\text{Cost of Delay}}{\text{Job Size}}$ | Helps PO prioritize high-value features and architectural enablers objectively, avoiding "loudest stakeholder wins." |
| **Backlog Readiness Depth** | Sprint capacity covered by DoR stories | Ensures PO has 2+ sprints of refined work ready, preventing last-minute iteration planning chaos. |
| **Mid-Sprint Scope Churn** | Story points added/removed mid-sprint | High churn indicates poor refinement or external stakeholder pressure. SM uses this data to shield the team. |
| **Say-Do Ratio / Predictability (PPM)** | $\frac{\text{Delivered Objectives}}{\text{Committed Objectives}} \times 100\%$ | Demonstrates if PO expectations align with real team capacity (targeting 85–90%+ predictability). |
| **Feature Lead Time** | Time from PO backlog entry to production release | Shows PO how batch sizing affects time-to-market; guides PO to write smaller, vertical slices. |
| **Escaped Defects / Bug Ratio** | Production bugs per feature release | Validates if PO is rushing feature delivery at the expense of acceptance testing and quality. |

---

## 3. How the Scrum Master Coaches the Product Owner

The SM acts as a mentor and coach to elevate the PO from a passive "requirement gatherer" to an active value optimizer.

### Coaching Area 1: Feature Slicing & BDD
* **Coaching Approach:** Coach the PO to break down large, complex epics into thin, end-to-end vertical slices that deliver increment value every sprint.
* **Technique:** Guide PO to write Acceptance Criteria in **Behavior-Driven Development (BDD)** format (*Given-When-Then*), ensuring clear testability for developers and QA/Data Analysts.

### Coaching Area 2: Balancing Features vs. Technical Enablers
* **Coaching Approach:** POs often push for 100% business features, ignoring refactoring and cloud/data infrastructure.
* **Technique:** Introduce the **70/20/10 Capacity Allocation Model** (70% Business Features, 20% Technical Enablers, 10% Technical Debt/Spikes) to protect long-term platform health.

### Coaching Area 3: Stakeholder Expectation Management
* **Coaching Approach:** POs often struggle to say "No" to external executives.
* **Technique:** Teach PO to use data (Velocity charts, CFD, Flow Efficiency) when communicating with stakeholders: *"We can take this new request, but based on our WIP limit, which existing priority should we trade off?"*

---

## 4. How the Scrum Master Evaluates the Product Owner's Effectiveness

*Note: The Scrum Master does not formally perform HR performance reviews for the PO. Instead, the SM evaluates the PO's **agile maturity, product flow efficiency, and backlog health** to identify coaching opportunities.*

### PO Evaluation Checklist

```text
[ ] Backlog Health: Is the backlog prioritized by business value/WSJF and maintained 2 sprints ahead?
[ ] Definition of Ready (DoR): Do stories enter planning with clear acceptance criteria and dependencies identified?
[ ] Availability & Engagement: Is the PO actively available during sprints to answer developer queries promptly?
[ ] Clear Vision & Goals: Does the PO articulate a clear Sprint Goal and PI Objectives beyond a list of tasks?
[ ] Respect for Capacity: Does the PO refrain from injecting unrefined scope into active sprints?
[ ] Stakeholder Shielding: Does the PO act as the single point of entry for business requests?
