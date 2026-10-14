# Where `Given-When-Then` (BDD) Fits in the Scaled Agile Framework (SAFe)

In the **Scaled Agile Framework (SAFe)**, `Given-When-Then` is the cornerstone syntax for **Behavior-Driven Development (BDD)** and **Acceptance Test-Driven Development (ATDD)**. 
It bridges the gap between business intent and technical implementation.

---

## 1. Which Part of SAFe Does It Relate To?

`Given-When-Then` spans several core areas of the SAFe framework:

1. **Built-In Quality (Core Value / Lean-Agile Principle):**  
   SAFe mandates that quality cannot be tested in at the end; it must be built in.
   BDD ensures that data pipelines, transformations, and models are defined with clear quality constraints before a single line of code is written.

3. **Team Level Backlog Refinement & Story Writing:**  
   It is the standard format used by Product Owners and Agile Teams to write unambiguous, testable Acceptance Criteria for User Stories and Enablers.

4. **Agile Release Train (ART) Execution & Built-In Automation:**  
   In advanced SAFe implementations, these BDD criteria directly feed into automated test suites (such as CI/CD pipelines, unit tests, and `dbt test` assertions) to support Continuous Integration and Continuous Delivery (CI/CD).

---

## 2. When to Use `Given-When-Then` in SAFe

You should use `Given-When-Then` at specific checkpoints across the iteration and PI lifecycle to ensure alignment and prevent rework:

┌─────────────────────────────────────────────────────────────────────────────┐
│                       WHEN TO APPLY BDD IN SAFe CADENCE                     │
├───────────────────┬─────────────────────────────────────────────────────────┤
│ 1. Backlog        │ During Backlog Refinement: The Product Owner brings     │
│    Refinement     │ draft BDD scenarios. The team reviews them to ensure    │
│                   │ technical feasibility and uncover hidden edge cases.    │
├───────────────────┼─────────────────────────────────────────────────────────┤
│ 2. Definition     │ As a DoR Gate: A story cannot pass the Definition       │
│    of Ready (DoR) │ of Ready (DoR) or enter an active sprint unless it has  │
│                   │ validated Given-When-Then criteria attached.            │
├───────────────────┼─────────────────────────────────────────────────────────┤
│ 3. Iteration      │ During Coding & Testing (DoD): Developers and data.     │
│    Execution      │ engineers use the "Then" statements to write automated  │
│                   │ pipeline assertions (e.g., dbt test, null checks).      │
├───────────────────┼─────────────────────────────────────────────────────────┤
│ 4. Iteration      │ During Iteration Review (Demo): The team demonstrates   │
│    Review         │ that the system satisfies the exact BDD scenarios agreed│
│                   │ upon during refinement, validating business value.      │
└───────────────────┴─────────────────────────────────────────────────────────┘


---
# Scrum Master Facilitation Scripts: Coaching BDD Across SAFe Events

A collection of plug-and-play facilitation scripts for Scrum Masters, Delivery Leads, and Agile Coaches to guide Data & Analytics teams in applying **Behavior-Driven Development (BDD)** and `Given-When-Then` criteria across key SAFe events.

---

## 1. Backlog Refinement (Primary Coaching Arena)

**Focus:** Transforming vague data requirements into testable, behavior-driven specifications and enforcing the **Definition of Ready (DoR)**.

┌─────────────────────────────────────────────────────────────────────────────┐
│                       REFINEMENT BDD COACHING FLOW                          │
├───────────────────┬───────────────────┬───────────────────┬─────────────────┤
│ 1. Read Raw Context│ 2. Draft Given    │ 3. Probe Edge     │ 4. Map to dbt / │
│ (PO Walkthrough)  │ (Source / Inputs) │ (Nulls / Drift)   │ DoR Verification│
└───────────────────┴───────────────────┴───────────────────┴─────────────────┘


### Facilitation Script & Prompts

* **[00:00 - Story Intro]**  
  **Scrum Master:** *"Thanks everyone. Let's look at item `DATA-204: Ingest Customer Subscriptions to Snowflake`. Before we estimate or discuss technical design, let's establish our behavioral baseline. PO, can you summarize the business outcome in 60 seconds?"*
* **[00:02 - Framing the 'Given' and 'When']**  
  **Scrum Master:** *"Great. Let's build our Happy Path scenario together. Data Engineers, what is our starting state—what source files or API states are we assuming in our `Given` statement?"*  
  * *Team output:* `Given JSON payloads exist in s3://landing/subscriptions/`
* **[00:05 - Defining 'Then' and Quality Assertions]**  
  **Scrum Master:** *"And when the pipeline or dbt transformation executes (`When`), what exact state must be true in Snowflake (`Then`) to consider this successfully delivered?"*  
  * *Team output:* `Then write records to ANALYTICS_STAGING.SUB_FACT with 0 primary key duplicates`
* **[00:08 - Probing Edge Cases & Anomaly Handling]**  
  **Scrum Master:** *"Now let's push for Built-In Quality. What happens when the upstream source sends null timestamps, malformed schemas, or duplicate customer IDs? Let's write an edge-case scenario for how the pipeline should handle that."*  
  * *Team output:* `Scenario: Quarantine bad records to `quarantine_subscriptions` and trigger Slack alert`
* **[00:12 - DoR Gate Check]**  
  **Scrum Master:** *"We now have 1 Happy Path and 1 Anomaly Handling scenario in `Given-When-Then` format. Does anyone feel this story is still ambiguous, or are we ready to open Planning Poker and size it?"*

---

## 2. Iteration Planning (Final Sanity & Commitment Check)

**Focus:** Verifying that candidate stories in the iteration backlog carry complete BDD criteria before the team commits to the Iteration Goal.

┌─────────────────────────────────────────────────────────────────────────────┐
│                        PLANNING BDD SANITY CHECK                            │
├───────────────────┬───────────────────┬───────────────────┬─────────────────┤
│ 1. Pull Story from│ 2. Audit BDD      │ 3. Confirm Test   │ 4. Commit to    │
│ Refined Backlog   │ Criteria Presence │ Alignment (dbt)   │ Iteration Goal  │
└───────────────────┴───────────────────┴───────────────────┴─────────────────┘


### Facilitation Script & Prompts

* **[Step 1 - Board Walk]**  
  **Scrum Master:** *"We're pulling `DATA-210: Calculate Monthly Recurring Revenue (MRR)` into Sprint 14. Before we confirm our capacity commitment, let's do our 30-second BDD audit."*
* **[Step 2 - Verifying Testability]**  
  **Scrum Master:** *"Let's read the `Then` statements on this card. Developer and QA, do you have enough clarity in these criteria to write your automated tests (`dbt test`, `pytest`, or Great Expectations assertions) right now without asking the PO for clarification mid-sprint?"*
* **[Step 3 - Handling Missing BDD]**  
  **Data Engineer:** *"This scenario says 'Calculate MRR accurately,' but it doesn't specify how to treat mid-month cancellations."*  
  **Scrum Master:** *"Good catch. If the behavioral criteria are incomplete, this item fails our Definition of Ready. Let's either pause for 3 minutes to draft the missing `Given-When-Then` clause with the PO right now, or drop it back to refinement and pull the next ready item."*

---

## 3. Iteration Retrospective (Root Cause & Quality Improvement)

**Focus:** Analyzing pipeline failures or quality escapes by inspecting missing or flawed BDD scenarios during refinement.

┌─────────────────────────────────────────────────────────────────────────────┐
│                      RETROSPECTIVE BDD ROOT-CAUSE FLOW                      │
├───────────────────┬───────────────────┬───────────────────┬─────────────────┤
│ 1. Review Incident│ 2.Inspect Original│3.Identify Missing │ 4. Update BDD   │
│ / Quality Escape  │ Story Acceptance  │ Scenario / Edge   │ Refinement Habi │
└───────────────────┴───────────────────┴───────────────────┴─────────────────┘


### Facilitation Script & Prompts

* **[Step 1 - Framing the Incident]**  
  **Scrum Master:** *"During Sprint 13, our production dbt build crashed because an upstream microservice added a new column type that our pipeline didn't account for. Let's inspect the original story's acceptance criteria."*
* **[Step 2 - Evaluating the Gap]**  
  **Scrum Master:** *"Looking back at the ticket: We had a Happy Path BDD scenario, but we didn't write an Edge Case scenario for schema drift or null fields during refinement. How could a stronger `Given-When-Then` clause have caught this during development or CI/CD testing?"*
* **[Step 3 - Action Item Creation]**  
  **Data Lead:** *"If we had written a `Given upstream schema changes, Then log warning and preserve existing table structure` clause, we would have added a dbt contract test."*  
  **Scrum Master:** *"Agreed. Let's record an improvement action item for our next Refinement session: Every data transformation story must include at least one schema assertion scenario before passing DoR."*

---

## 4. PI Planning (Program / Feature Level Alignment)

**Focus:** Coaching Product Management, System Architects, and Product Owners to define high-level acceptance criteria for Epics and Features using BDD.

┌─────────────────────────────────────────────────────────────────────────────┐
│                      PI PLANNING FEATURE BDD COACHING                       │
├───────────────────┬───────────────────┬───────────────────┬─────────────────┤
│ 1. Review Feature │ 2. Express Target │ 3. Identify Cross-│ 4. Break Down to│
│ Vision & WSJF     │ Outcome via BDD   │ ART Dependencies  │ Team Slices     │
└───────────────────┴───────────────────┴───────────────────┴─────────────────┘


### Facilitation Script & Prompts

* **[Step 1 - Aligning on Feature Intent]**  
  **Scrum Master:** *"We are looking at Feature `FEAT-102: Customer Data Platform (CDP) Real-Time Analytics`. Product Management, before squads begin breaking this into stories during Breakout Session 1, let's state the Feature Acceptance Criteria in BDD format."*
* **[Step 2 - Crafting High-Level BDD]**  
  **Scrum Master:** *"Let's frame it together:  
  * **Given** real-time clickstream data from our mobile app and website,  
  * **When** processed by our Streaming Pipeline and Snowflake warehouse,  
  * **Then** customer profile traits update within $< 5$ seconds with $99.9\%$ availability.*  
  Does this give our data squads a clear behavioral target for breaking down their team-level user stories?"*

---

## Quick Reference Summary Matrix

| SAFe Event | Coaching Focus | Key Facilitation Output |
| :--- | :--- | :--- |
| **Backlog Refinement** | Story-level `Given-When-Then` authoring & DoR validation. | 1 Happy Path + 1 Edge Case BDD scenario per ticket. |
| **Iteration Planning** | Testability check & commitment alignment. | Zero unrefined/ambiguous stories committed into sprint. |
| **Iteration Retrospective** | Inspecting quality escapes & root-cause analysis. | Updated team refinement habits & dbt assertion rules. |
| **PI Planning** | High-level Feature criteria & cross-team alignment. | Behavior-driven Feature Acceptance Criteria for ART Breakouts. |

---

## 3. Summary for Your CoE Handbook

* **What it is:** A SAFe alignment tool for Built-In Quality using Behavior-Driven Development (BDD).
* **When to use it:** Always during **Backlog Refinement** before a story is marked **`Ready for Sprint`**, and subsequently as the basis for automated data quality testing.
