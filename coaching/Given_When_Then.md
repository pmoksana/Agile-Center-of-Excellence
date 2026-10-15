# Where `**Given**-**When**-**Then**` (BDD) Fits in the Scaled Agile Framework (SAFe)

In the **Scaled Agile Framework (SAFe)**, `**Given**-**When**-**Then**` is the cornerstone syntax for **Behavior-Driven Development (BDD)** and **Acceptance Test-Driven Development (ATDD)**. 
It bridges the gap between business intent and technical implementation.

---

## 1. Which Part of SAFe Does It Relate To?

`**Given**-**When**-**Then**` spans several core areas of the SAFe framework:

1. **Built-In Quality (Core Value / Lean-Agile Principle):**  
   SAFe mandates that quality cannot be tested in at the end; it must be built in.
   BDD ensures that data pipelines, transformations, and models are defined with clear quality constraints before a single line of code is written.

3. **Team Level Backlog Refinement & Story Writing:**  
   It is the standard format used by Product Owners and Agile Teams to write unambiguous, testable Acceptance Criteria for User Stories and Enablers.

4. **Agile Release Train (ART) Execution & Built-In Automation:**  
   In advanced SAFe implementations, these BDD criteria directly feed into automated test suites (such as CI/CD pipelines, unit tests, and `dbt test` assertions) to support Continuous Integration and Continuous Delivery (CI/CD).

---
In SAFe and Behavior-Driven Development (BDD), writing **Given**-**When**-**Then** criteria is not a solo task—it is a collaborative "Three Amigos" practice.

Here is a clear breakdown of how BDD accountabilities are divided between the Product Owner and the Agile Data Team, along with the exact step-by-step workflow during Refinement.

1. Division of Responsibility: PO vs. Team

┌─────────────────────────────────────────────────────────────────────────────┐
│                          BDD DIVISION OF RESPONSIBILITY                     │
├──────────────────────────────────────┬──────────────────────────────────────┤
│ Product Owner Level (WHAT & WHY)     │ Agile Team Level (HOW & VALIDATION)  │
├──────────────────────────────────────┼──────────────────────────────────────┤
│ • Defines Business Outcome & Value   │ • Defines Technical Prerequisites    │
│ • Drafts the Initial BDD Framework   │ • Adds Edge Cases, Nulls & Anomalies │
│ • Identifies End Consumers/Dashboards│ • Maps Criteria to dbt/Pipeline Tests│
│ • Validates Business Rules & Logic   │ • Verifies Feasibility & Estimates   │
└──────────────────────────────────────┴──────────────────────────────────────┘
---
### A. The Product Owner Level ("What & Why")
The PO owns the business context, business logic, and desired outcome. They draft the initial **Given**-**When**-**Then** structure focus on functional expectations.

What the PO writes before Refinement:

Business Purpose: Why are we building this dataset?

**Given** (High Level): Where the business data originates (e.g., "**Given** daily active Salesforce accounts").

**When**: The business trigger (e.g., "**When** the nightly ingestion runs").

**Then** (Functional Outcome): The business expectation (e.g., "**Then** updated customer LTV is available for Marketing in Tableau").

### B. The Agile Team Level ("How, Edge Cases & Validation")
The team—Data Engineers, Analysts, QA, and System Architects—owns the technical accuracy, schema validation, boundary conditions, and quality assertions. They complete the fields the PO cannot know.

What the Team adds during Refinement:

Technical Prerequisites: Exact source tables, S3 bucket paths, API endpoints, and IAM/Secrets Manager access.

Edge Case **Scenario**s: What happens **When** data is missing, duplicated, or formatted incorrectly?

Automated Quality Gates: Explicit assertions like dbt test constraints (unique, not_null, accepted_values, data types).

## 2. BDD Collaboration in Refinement (The 3-Step Flow)
Instead of the PO bringing a "perfect" BDD story, treat Refinement as a collaborative refinement workshop:

# BDD Collaboration in Refinement: The 3-Step Flow

A practical facilitation guide for Scrum Masters, Product Owners, Data Engineers, and QA to collaboratively construct testable, behavior-driven specifications during Backlog Refinement.

In Data & Analytics teams, **BDD is a shared practice—not a solo task.** The Product Owner brings the business vision (*What & Why*), while the Engineering and QA team brings technical precision, schema validation, and edge-case safeguards (*How & Quality Controls*).

---

## The 3-Step Collaboration Lifecycle

Rather than expecting a Product Owner to write complete technical specifications in isolation, follow this 3-step progressive refinement flow:

┌─────────────────────────────────────────────────────────────────────────────┐
│                          3-STEP BDD REFINEMENT FLOW                         │
├───────────────────────┬───────────────────────────┬─────────────────────────┤
│ **Step 1**: PO INTRO      │ **Step 2**: TEAM DEEP-DIVE    │ ****Step 3****: DoR SIGN-OFF    │
│ Business Intent &     │ Schemas, Edge Cases &     │ Quality Gate Check &    │
│ Functional Outcome    │ Automated Assertions      │ Relative Sizing         │
└───────────────────────┴───────────────────────────┴─────────────────────────┘
## Step-by-Step Facilitation Guide

### **Step 1**: Product Owner Presents Business Intent (2 Mins)

The PO opens the ticket and walks through the core business goal, target consumers, and the high-level **Happy Path** **Scenario**.

* **PO Focus:** Business value, target KPI, end-user reporting needs.
* **Coaching Script:**  
  > *"I brought ticket `DATA-105`. Our business goal is to ingest Salesforce accounts into Snowflake so Marketing can run daily LTV models. My draft **Scenario** covers our primary happy path."*

```gherkin
# Drafted by PO prior to refinement
**Scenario**: Successfully syncing active accounts for Marketing LTV
  **Given** active customer accounts exist in Salesforce
  **When** the daily sync pipeline executes at 02:00 UTC
  **Then** output updated records to `PROD_ANALYTICS.DIM_CUSTOMERS`
  And Marketing can query accurate LTV metrics in Tableau.


### **Step 2**: Team Conducts Technical & Edge-Case Deep Dive (5–8 Mins)
The Data Engineers, Architects, and QA Analysts challenge the draft **Scenario**, define the exact schema contract, and introduce defensive edge-case **Scenario**s.

Engineers & QA Focus: Target table schemas, explicit data types, primary keys, nullability rules, and anomaly handling.

**Facilitation Dialogue**:

Data Engineer: "We need an explicit schema contract. Let's add a technical **Scenario** enforcing account_id as VARCHAR(18) and annual_revenue cast to NUMBER(18,2)."

QA Analyst: "What happens if Salesforce sends null customer IDs or string currency symbols like '$150,000'?"

PO: "If account_id is null, we cannot calculate LTV. We must quarantine those rows and alert the data team."
****Step 3****: Joint DoR Sign-Off
Scrum Master: "We now have a complete BDD set: 1 Happy Path from the PO, and 2 Technical/Edge Case **Scenario**s from the team. The schema and test assertions are locked. Is everyone ready to size this story?"
# Added by Data Devs during refinement (Technical Schema Contract)
**Scenario**: Technical schema mapping and type enforcement
  **Given** raw JSON payloads in `s3://landing/salesforce/accounts/`
  **When** the dbt transformation model executes
  **Then** enforce target schema types (`account_id` as VARCHAR, `annual_revenue` as NUMBER(18,2))
  And zero primary key duplicates reach the destination table.

# Added by QA & Devs during refinement (Edge Case Safeguard)
**Scenario**: Handling null customer IDs and corrupt records
  **Given** source records contain missing or NULL `account_id` values
  **When** dbt data quality assertions execute
  **Then** route corrupt records to `STAGING.QUARANTINE_SALESFORCE`
  And trigger an automated alert notification to `#data-squad-alerts`
  And build the production table with zero null keys.

### ****Step 3****: Joint DoR Sign-Off & Sizing (2 Mins)The Scrum Master facilitates a final check against the team's Definition of Ready (DoR).
 Once all 3 **Scenario**s (Business Outcome, Technical Contract, Edge Case) are locked, the team sizes the item using Planning Poker.Scrum Master
Check:Is the business intent clear? Yes (**Scenario** 1)Are data contracts & schemas defined? Yes (**Scenario** 2)Are edge cases & assertions specified? Yes (**Scenario** 3)Outcome: Mark ticket as Ready for Sprint and conduct relative estimation ($1, 2, 3, 5, 8$ pts).
---
## Real-World Comparison: PO-Only vs. Co-Created BDD
❌ If PO Writes BDD Alone (Incomplete / Unusable):
Gherkin
Feature: Salesforce Account Ingestion
  **Scenario**: Ingest accounts
    **Given** salesforce data exists
    **When** pipeline runs
    **Then** data is in Snowflake and looks accurate
Why it fails: Developers don't know which fields to ingest, QA doesn't know what automated tests to run, and pipeline schema crashes won't be caught.

✅ Co-Created BDD (PO + Team in Refinement):
Gherkin

Feature: Salesforce Account Ingestion

  # --- Drafted by PO (Business Outcome) ---
  **Scenario**: Successfully loading active accounts for Marketing LTV
    **Given** active accounts exist in Salesforce
    **When** the daily sync executes at 02:00 UTC
    **Then** output available records in `PROD_ANALYTICS.DIM_CUSTOMERS`
    And Marketing can query updated LTV metrics.

  # --- Added by Data Team in Refinement (Technical & Edge Cases) ---
  **Scenario**: Handling schema contracts and null primary keys
    **Given** raw JSON extracts in `s3://landing/salesforce/accounts/`
    **When** `dbt run` executes transformation models
    **Then** enforce `dbt test` assertions that `account_id` is NOT NULL and UNIQUE
    And cast string currency fields (`annual_revenue`) to `NUMBER(18,2)`.

  ****Scenario****: Handling upstream schema drift
    **Given** an unmapped or unexpected new field in the source API
    **When** the ingestion script validates source metadata against the Data Contract
    **Then** log a schema drift warning to `#data-squad-alerts`
    And proceed without breaking existing warehouse pipeline executions.

4. Summary Matrix  
BDD Component	Who Drafts It?	Where Is It Finalized?
Business Purpose & Context	Product Owner	Pre-Refinement
Happy Path Functional Outcome	Product Owner	Pre-Refinement
Technical Prerequisites & Access	Agile Data Team	Backlog Refinement
Edge Cases & Data Anomalies	Agile Data Team (Engineers/QA)	Backlog Refinement
Automated Test Assertions (dbt)	Agile Data Team	Backlog Refinement
Final DoR Approval & Sizing	Entire Squad (Facilitated by SM)	End of Refinement
---

# BDD Responsibility Matrix: Product Owner vs. Data Squad

A clear breakdown of roles and accountabilities for Behavior-Driven Development (BDD) across the delivery lifecycle. 

In Data & Analytics teams, **BDD is a collaborative practice—not a solo effort.** The Product Owner owns the *Business Intent*, while the Data Engineers and QA Analysts own the *Technical Contracts, Edge Cases, and Quality Assertions*.

---

## BDD Responsibility Matrix

| Role | Pre-Refinement | During Refinement (3-Step Flow) | Post-Refinement / Sprint Execution |
| :--- | :--- | :--- | :--- |
| **Product Owner (PO)** | • Identifies business value & ROI.<br>• Drafts **Scenario** 1: Happy Path** (Business Outcome).<br>• Defines end-consumer target (e.g., Tableau, API). | • Explains business context & logic.<br>• Clarifies domain rules **When** edge cases are raised.<br>• Approves final business behavior criteria. | • Validates completed deliverables against BDD criteria.<br>• Accepts user stories during Iteration Review / Demo. |
| **Data Engineers** | • Pre-screens upstream source accessibility.<br>• Verifies cloud infrastructure prerequisites (S3, Snowflake, IAM). | • Adds **Scenario** 2: Technical Schema Contract**.<br>• Specifies target table structures & field types (`VARCHAR`, `NUMBER`).<br>• Identifies technical dependencies. | • Writes pipeline ingestion & transformation code.<br>• Builds dbt models satisfying `**Given**-**When**-**Then**` conditions.<br>• Implements schema contract enforcement. |
| **Data QA / Analysts** | • Evaluates upstream data quality risks.<br>• Prepares baseline data profiles. | • Adds **Scenario** 3: Edge Cases & Safeguards**.<br>• Defines nullability, duplicate, and anomaly behavior.<br>• Specifies quarantine logic & alerting channels. | • Implements automated test suites (`dbt test`, `pytest`, Great Expectations).<br>• Validates zero quality regressions across pipelines. |
| **Scrum Master (SM)** | • Audits candidate items against DoR 24h prior.<br>• Ensures PO brings initial draft BDD **Scenario**. | • Facilitates the 3-Step Refinement conversation.<br>• Enforces Definition of Ready (DoR) gate.<br>• Drives relative estimation (Planning Poker). | • Protects sprint scope based on locked BDD criteria.<br>• Coaches team on continuous BDD improvement during Retrospectives. |


---
┌─────────────────────────────────────────────────────────────────────────────────┐
│                      UNIFIED JIRA BDD BLOCK OWNERSHIP                           │
├─────────────────────────────────────────────────────────────────────────────────┤
│ **Scenario** 1: Happy Path (Business Outcome)  ──► Owned & Drafted by PO        │
│ **Scenario** 2: Technical Schema Contract      ──► Co-authored by Data Devs     │
│ **Scenario** 3: Edge Cases & Anomaly Handling  ──► Co-authored by QA & Data Devs│
└─────────────────────────────────────────────────────────────────────────────────┘
---

## BDD **Scenario** Ownership Summary

---

## 2. **When** to Use `**Given**-**When**-**Then**` in SAFe

You should use `**Given**-**When**-**Then**` at specific checkpoints across the iteration and PI lifecycle to ensure alignment and prevent rework:

┌─────────────────────────────────────────────────────────────────────────────┐
│                       **When** TO APPLY BDD IN SAFe CADENCE                 │
├───────────────────┬─────────────────────────────────────────────────────────┤
│ 1. Backlog        │ During Backlog Refinement: The Product Owner brings     │
│    Refinement     │ draft BDD **Scenario**s. The team reviews them to ensure│
│                   │ technical feasibility and uncover hidden edge cases.    │
├───────────────────┼─────────────────────────────────────────────────────────┤
│ 2. Definition     │ As a DoR Gate: A story cannot pass the Definition       │
│    of Ready (DoR) │ of Ready (DoR) or enter an active sprint unless it has  │
│                   │ validated **Given**-**When**-**Then** criteria attached.│
├───────────────────┼─────────────────────────────────────────────────────────┤
│ 3. Iteration      │ During Coding & Testing (DoD): Developers and data.     │
│    Execution      │ engineers use the "*Then*" statements to write automated│
│                   │ pipeline assertions (e.g., dbt test, null checks).      │
├───────────────────┼─────────────────────────────────────────────────────────┤
│ 4. Iteration      │ During Iteration Review (Demo): The team demonstrates   │
│    Review         │ that the system satisfies the exact BDD Scenarios agreed│
│                   │ upon during refinement, validating business value.      │
└───────────────────┴─────────────────────────────────────────────────────────┘


---
# Scrum Master Facilitation Scripts: Coaching BDD Across SAFe Events

A collection of plug-and-play facilitation scripts for Scrum Masters, Delivery Leads, and Agile Coaches to guide Data & Analytics teams in applying **Behavior-Driven Development (BDD)** and `**Given**-**When**-**Then**` criteria across key SAFe events.

---

## 1. Backlog Refinement (Primary Coaching Arena)

**Focus:** Transforming vague data requirements into testable, behavior-driven specifications and enforcing the **Definition of Ready (DoR)**.

┌─────────────────────────────────────────────────────────────────────────────┐
│                       REFINEMENT BDD COACHING FLOW                          │
├───────────────────┬───────────────────┬───────────────────┬─────────────────┤
│ 1.Read Raw Context│ 2.Draft **Given** │ 3. Probe Edge     │ 4. Map to dbt / │
│ (PO Walkthrough)  │ (Source / Inputs) │ (Nulls / Drift)   │ DoR Verification│
└───────────────────┴───────────────────┴───────────────────┴─────────────────┘


### Facilitation Script & Prompts

* **[00:00 - Story Intro]**  
  **Scrum Master:** *"Thanks everyone. Let's look at item `DATA-204: Ingest Customer Subscriptions to Snowflake`. Before we estimate or discuss technical design, let's establish our behavioral baseline. PO, can you summarize the business outcome in 60 seconds?"*
* **[00:02 - Framing the '**Given**' and '**When**']**  
  **Scrum Master:** *"Great. Let's build our Happy Path **Scenario** together. Data Engineers, what is our starting state—what source files or API states are we assuming in our `**Given**` statement?"*  
  * *Team output:* `**Given** JSON payloads exist in s3://landing/subscriptions/`
* **[00:05 - Defining '**Then**' and Quality Assertions]**  
  **Scrum Master:** *"And **When** the pipeline or dbt transformation executes (`**When**`), what exact state must be true in Snowflake (`**Then**`) to consider this successfully delivered?"*  
  * *Team output:* `**Then** write records to ANALYTICS_STAGING.SUB_FACT with 0 primary key duplicates`
* **[00:08 - Probing Edge Cases & Anomaly Handling]**  
  **Scrum Master:** *"Now let's push for Built-In Quality. What happens **When** the upstream source sends null timestamps, malformed schemas, or duplicate customer IDs? Let's write an edge-case **Scenario** for how the pipeline should handle that."*  
  * *Team output:* `**Scenario**: Quarantine bad records to `quarantine_subscriptions` and trigger Slack alert`
* **[00:12 - DoR Gate Check]**  
  **Scrum Master:** *"We now have 1 Happy Path and 1 Anomaly Handling **Scenario** in `**Given**-**When**-**Then**` format. Does anyone feel this story is still ambiguous, or are we ready to open Planning Poker and size it?"*

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

* **[**Step 1** - Board Walk]**  
  **Scrum Master:** *"We're pulling `DATA-210: Calculate Monthly Recurring Revenue (MRR)` into Sprint 14. Before we confirm our capacity commitment, let's do our 30-second BDD audit."*
* **[**Step 2** - Verifying Testability]**  
  **Scrum Master:** *"Let's read the `**Then**` statements on this card. Developer and QA, do you have enough clarity in these criteria to write your automated tests (`dbt test`, `pytest`, or Great Expectations assertions) right now without asking the PO for clarification mid-sprint?"*
* **[****Step 3**** - Handling Missing BDD]**  
  **Data Engineer:** *"This **Scenario** says 'Calculate MRR accurately,' but it doesn't specify how to treat mid-month cancellations."*  
  **Scrum Master:** *"Good catch. If the behavioral criteria are incomplete, this item fails our Definition of Ready. Let's either pause for 3 minutes to draft the missing `**Given**-**When**-**Then**` clause with the PO right now, or drop it back to refinement and pull the next ready item."*

---

## 3. Iteration Retrospective (Root Cause & Quality Improvement)

**Focus:** Analyzing pipeline failures or quality escapes by inspecting missing or flawed BDD **Scenario**s during refinement.

┌─────────────────────────────────────────────────────────────────────────────┐
│                      RETROSPECTIVE BDD ROOT-CAUSE FLOW                      │
├───────────────────┬───────────────────┬───────────────────┬─────────────────┤
│ 1. Review Incident│ 2.Inspect Original│3.Identify Missing │ 4. Update BDD   │
│ / Quality Escape  │ Story Acceptance  │ Scenario / Edge   │ Refinement Habi │
└───────────────────┴───────────────────┴───────────────────┴─────────────────┘


### Facilitation Script & Prompts

* **[**Step 1** - Framing the Incident]**  
  **Scrum Master:** *"During Sprint 13, our production dbt build crashed because an upstream microservice added a new column type that our pipeline didn't account for. Let's inspect the original story's acceptance criteria."*
* **[**Step 2** - Evaluating the Gap]**  
  **Scrum Master:** *"Looking back at the ticket: We had a Happy Path BDD **Scenario**, but we didn't write an Edge Case **Scenario** for schema drift or null fields during refinement. How could a stronger `**Given**-**When**-**Then**` clause have caught this during development or CI/CD testing?"*
* **[****Step 3**** - Action Item Creation]**  
  **Data Lead:** *"If we had written a `**Given** upstream schema changes, **Then** log warning and preserve existing table structure` clause, we would have added a dbt contract test."*  
  **Scrum Master:** *"Agreed. Let's record an improvement action item for our next Refinement session: Every data transformation story must include at least one schema assertion **Scenario** before passing DoR."*

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

* **[**Step 1** - Aligning on Feature Intent]**  
  **Scrum Master:** *"We are looking at Feature `FEAT-102: Customer Data Platform (CDP) Real-Time Analytics`. Product Management, before squads begin breaking this into stories during Breakout Session 1, let's state the Feature Acceptance Criteria in BDD format."*
* **[**Step 2** - Crafting High-Level BDD]**  
  **Scrum Master:** *"Let's frame it together:  
  * ****Given**** real-time clickstream data from our mobile app and website,  
  * ****When**** processed by our Streaming Pipeline and Snowflake warehouse,  
  * ****Then**** customer profile traits update within $< 5$ seconds with $99.9\%$ availability.*  
  Does this give our data squads a clear behavioral target for breaking down their team-level user stories?"*

---

## Quick Reference Summary Matrix

| SAFe Event | Coaching Focus | Key Facilitation Output |
| :--- | :--- | :--- |
| **Backlog Refinement** | Story-level `**Given**-**When**-**Then**` authoring & DoR validation. | 1 Happy Path + 1 Edge Case BDD **Scenario** per ticket. |
| **Iteration Planning** | Testability check & commitment alignment. | Zero unrefined/ambiguous stories committed into sprint. |
| **Iteration Retrospective** | Inspecting quality escapes & root-cause analysis. | Updated team refinement habits & dbt assertion rules. |
| **PI Planning** | High-level Feature criteria & cross-team alignment. | Behavior-driven Feature Acceptance Criteria for ART Breakouts. |

---

## 3. Summary 

* **What it is:** A SAFe alignment tool for Built-In Quality using Behavior-Driven Development (BDD).
* ****When** to use it:** Always during **Backlog Refinement** before a story is marked **`Ready for Sprint`**, and subsequently as the basis for automated data quality testing.
