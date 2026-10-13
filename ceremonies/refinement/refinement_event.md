# Scrum Master Guide: Preparing for & Facilitating Backlog Refinement (Data & Analytics)

Operational guide for Scrum Masters, Delivery Leads, and Agile Coaches to prepare, organize, and facilitate highly effective 
Backlog Refinement sessions for Data Engineering, Data Science, and Business Intelligence squads.

---

## 1. Pre-Meeting Checklist: What the Scrum Master Must Prepare & Bring

Refinement fails when teams spend 45 minutes reading unrefined tickets for the first time.

The Scrum Master acts as the **process facilitator** to ensure high-quality prep *before* the session begins.

┌─────────────────────────────────────────────────────────────────────────────┐
│                       REFINEMENT PREPARATION CANVAS                         │
├────────────────────────────────┬────────────────────────────────────────────┤
│ Candidate Backlog (1.5–2x Cap) │ Verified by PO & SM before the call        │
├────────────────────────────────┼────────────────────────────────────────────┤
│ Data Contract & Schema Attach. │ Field mappings & source availability check │
├────────────────────────────────┼────────────────────────────────────────────┤
│ Baseline Calibration Model     │ Benchmark 3-point story for relative sizing│
├────────────────────────────────┼────────────────────────────────────────────┤
│ Capacity Split Guardrails      │ Enforces 70% Features /                    │
│                                │ 20% Enablers / 10% Debt                    │
└────────────────────────────────┴────────────────────────────────────────────┘


### Checklist for the Scrum Master (To Complete 24h Before Refinement Session)

- [ ] **Align with Product Owner (PO) on Candidates:** Review candidate items together. Ensure candidates represent **1.5x to 2x average sprint velocity** (e.g., if velocity is 30 pts, prepare ~45–60 pts worth of candidates).
- [ ] **Verify Upstream Access Prerequisites:** Confirm source database, API, or cloud infrastructure access (S3/Snowflake/IAM) is identified on the ticket.
- [ ] **Confirm Data Contract Attachment:** Ensure a basic schema mapping or field specification exists for any data ingestion/transformation ticket.
- [ ] **Pre-Screen Against Definition of Ready (DoR):** Verify candidate items have clear business value context and BDD acceptance criteria (*Given-When-Then*).
- [ ] **Prepare Relative Sizing Baseline:** Have your team’s **3-Point Reference Story** ready to display for relative estimation (Planning Poker).
---
## How **verify Upstream Access Prerequisites** (example)
Here are two real-world examples showing the difference between a ticket that fails this check and one that passes, specifically for a Data & Analytics team.

- [ ] **Scenario: Building a Marketing Conversion Pipeline
The Product Owner wants the data team to build a daily data pipeline that pulls Facebook Ads spend data, joins it with Google Analytics website conversions, and stores it in Snowflake so Marketing can see their Cost-Per-Acquisition (CPA) in Tableau.

- [ ] **Example 1: Fails DoR (Missing Access Identification) ❌
Jira Ticket: DATA-104: Ingest Facebook Ads API Data to Snowflake

- [ ] **Description:
We need Facebook Ads spend data in Snowflake so the marketing team can see daily campaign spend.

- [ ] **Acceptance Criteria:

Pull daily spend, impressions, and clicks.

Save to Snowflake table MARKETING.FACEBOOK_SPEND.

- [ ] **What happens during the Sprint?
On Day 2 of the sprint, the Data Engineer opens the ticket and tries to run their script:
They don't have the API Access Token for the client's Facebook Business Account.
They try to save data to S3 staging, but get an AWS 403 Access Denied error because their IAM role lacks write permissions to s3://prod-analytics-staging/.
They open a security ticket with IT to request access. IT takes 4 days to approve it.

- [ ] **Result: The story spends 5 days stuck in In Progress / Blocked, missing the Sprint Goal.

- [ ] **Example 2: Passes DoR (Access Prerequisites Identified & Verified) ✅
Jira Ticket: DATA-104: Ingest Facebook Ads API Data to Snowflake

- [ ] **Description:
We need Facebook Ads spend data in Snowflake so the marketing team can see daily campaign spend.

Infrastructure & Access Prerequisites (Verified in Refinement):

- [ ] **Source API: Facebook Graph API v19.0
- [ ] **Credentials: Stored in AWS Secrets Manager (secret_name: /prod/marketing/fb_api_token) — Access granted to Data Eng group.
- [ ] **Staging Storage: AWS S3 Bucket s3://company-data-lake-staging/marketing/facebook/
- [ ] **IAM Policy Required: arn:aws:iam::123456789012:role/DataPipelineExecutionRole — Read/Write verified on 2026-10-12.
- [ ] **Target Warehouse: Snowflake Database ANALYTICS_STAGING.MARKETING
- [ ] **Snowflake Role: TRANSFORMER_ROLE — USAGE & CREATE TABLE grants verified.

- [ ] **Acceptance Criteria (BDD):

**Given** daily execution at 02:00 UTC, **When** the script fetches Facebook spend, **Then** write to ANALYTICS_STAGING.MARKETING.FB_SPEND.

**Given** missing or null campaign_id records, **When** validation runs, **Then** fail the dbt run and alert #data-squad-alerts.

What happens during the Sprint?
The Data Engineer picks up the ticket on Day 1, immediately connects to the Facebook API using the Secrets Manager token, writes the staging files to S3 without permissions errors, and merges the dbt model into Snowflake.

Result: The story is completed and validated in 2 days with zero access delays.
---
## How **Confirming Data Contract Attachment** (example):

In Data & Analytics engineering, a **Data Contract** is an agreed specification between the data provider (e.g., source CRM, backend microservice, or external API) and the data consumer (e.g., data engineering team, dbt models, Tableau dashboards). 
Ensuring a Data Contract is attached **before** a ticket enters a sprint prevents broken pipelines, silent data corruption, and failed schema migrations.

---
## Scenario: Ingesting Salesforce Account Data into Snowflake

The marketing team needs the Salesforce `Account` table ingested into the cloud warehouse and transformed via dbt for customer lifetime value (LTV) reporting.

---

## Example 1: Fails DoR (Missing Data Contract) ❌

> ### Jira Ticket: `DATA-105: Ingest Salesforce Account Table to Staging`
>
> **Description:** 
> Pull the Salesforce `Account` object into Snowflake staging so we can calculate LTV in dbt.
> 
> **Acceptance Criteria:**
> * Pull `Account` data daily.
> * Store in `RAW_LANDING.SALESFORCE.ACCOUNT`.

### What happens during the Sprint?
1. **Day 2:** The Data Engineer starts writing the ingestion pipeline, but isn't sure which fields Marketing actually needs out of the 150+ columns in Salesforce.
2. **Day 3:** The developer pulls all 150 fields. During the dbt model run, it crashes because `AnnualRevenue` is formatted as a String (`"$150,000"`) instead of a Numeric type (`150000.00`).
3. **Day 4:** The Salesforce administrator changes the API field name `Customer_Tier__c` to `Account_Tier__c` in production without warning. The pipeline fails entirely.
4. **Result:** 4 days lost debugging schema type mismatches and missing column definitions. The ticket misses the sprint commitment.

---

## Example 2: Passes DoR (Data Contract Attached & Verified) ✅

> ### Jira Ticket: `DATA-105: Ingest Salesforce Account Table to Staging`
>
> **Description:** 
> Pull the Salesforce `Account` object into Snowflake staging so we can calculate LTV in dbt.
> 
> **Attached Data Contract Specification:**
>
> | Source Field (`Salesforce`) | Target Field (`Snowflake Staging`) | Target Data Type | Primary Key? | Nullable? | Transformation / Validation Rule |
> | :--- | :--- | :--- | :---: | :---: | :--- |
> | `Id` | `account_id` | `VARCHAR(18)` | **YES** | **NO** | Must be unique; 18-character string. |
> | `Name` | `account_name` | `VARCHAR(255)` | NO | **NO** | Strip leading/trailing whitespaces. |
> | `AnnualRevenue` | `annual_revenue` | `NUMBER(18,2)` | NO | YES | Cast string currency symbols (`$`, `,`) to float. |
> | `Account_Tier__c` | `account_tier` | `VARCHAR(50)` | NO | YES | Default to `'Standard'` if null. |
> | `CreatedDate` | `created_at_utc` | `TIMESTAMP_NTZ` | NO | **NO** | Convert system timestamp to UTC. |
>
> **Data Quality Gate (dbt Assertions):**
> * `dbt test`: `unique` and `not_null` constraints enforced on `account_id`.
> * `dbt test`: Schema contract validation enabled (`contract: {enforced: true}`).
>
> **Acceptance Criteria (BDD):**
> * **Given** the daily Salesforce extract, **When** the dbt model runs, **Then** all 5 target fields match the specified data types with 0 primary key duplicates.

### What happens during the Sprint?
1. The Data Engineer builds the ingestion pipeline strictly following the 5-field schema mapping.
2. The custom transformation rules (casting currency string to numeric) are implemented on day one.
3. Automated `dbt test` assertions validate primary key uniqueness and null checks in the staging environment.
4. **Result:** The story is completed, fully tested, and documented in **2 days** with zero schema surprises.

---
## Pre-Screening Against Definition of Ready (DoR) example:

Pre-screening candidate items **before** Backlog Refinement ensures that developers do not spend valuable meeting time trying to figure out *why* a feature is being built or *how* it will be tested. 

A story passes pre-screening when it explicitly defines the **Business Value Context** (the ROI / business decision it enables) and provides **BDD Acceptance Criteria** (*Given-When-Then*).

---

## Scenario: Calculating Customer Churn Risk for Marketing Campaigns

The Growth Marketing team wants to identify high-risk subscription customers in Snowflake so they can automatically trigger retention email discounts before users cancel.

---

## Example 1: Fails Pre-Screening (Fails DoR) ❌

> ### Jira Ticket: `DATA-108: Build Customer Churn Risk Model Table`
>
> **Description:** 
> Create a table in Snowflake for customer churn so marketing can send emails.
> 
> **Acceptance Criteria:**
> * Predict churn scores for active customers.
> * Put results in Snowflake.

### Why it Fails Pre-Screening:
* ❌ **Missing Business Context:** Why are we building this now? What churn threshold triggers an email? What business KPI measures success?
* ❌ **Vague Acceptance Criteria:** How does a Data Engineer or QA test if the model output is correct? What happens if a score is missing or null?
* ❌ **Impact on Refinement:** The team will spend 30 minutes in the refinement call arguing over what "churn" means instead of sizing and planning the technical work.

---

## Example 2: Passes Pre-Screening (Passes DoR) ✅

> ### Jira Ticket: `DATA-108: Build Customer Churn Risk Model Table`
>
> **Business Value Context:**
> * **Business Goal:** Reduce monthly subscription churn by 5% in Q4.
> * **End Consumer:** Automated Braze Marketing Platform & Retention Analytics Dashboard.
> * **Business Outcome:** Identifies active subscribers with a predicted churn probability $> 0.70$ so Marketing can auto-deliver a $20\%$ renewal discount.
>
> **BDD Acceptance Criteria (Given-When-Then):**
>
> ```gherkin
> Feature: Customer Churn Risk Pipeline Evaluation
> 
>   Scenario: Successfully scoring daily active subscribers
>     Given active subscribers in the `PROD_ANALYTICS.DIM_CUSTOMERS` table
>     When the ML inference model runs daily at 03:00 UTC
>     Then write the output to `PROD_ANALYTICS.FACT_CHURN_RISK`
>     And ensure `churn_probability` is a numeric value between 0.00 and 1.00.
> 
>   Scenario: Handling missing historical activity data
>     Given a customer has less than 7 days of platform activity history
>     When the churn risk model calculates the score
>     Then assign a default `churn_probability` of NULL
>     And flag `is_insufficient_data = TRUE`
>     And do not trigger an automated marketing email.
> 
>   Scenario: Automated Data Quality Gate (DoD Assertion)
>     Given the table output in staging
>     When `dbt test` executes primary key constraints
>     Then zero duplicate `customer_id` records exist
>     And zero `churn_probability` values exceed 1.00.
> ```

### Why it Passes Pre-Screening:
* ✅ **Clear Business Purpose:** The developer understands the target user, the retention strategy, and the expected business outcome.
* ✅ **Testable Criteria:** BDD format gives QA and Data Engineers unambiguous test cases for success, failure, and edge-case handling.
* ✅ **Seamless Refinement:** The team can review the technical implementation and size the ticket in under 5 minutes.

---

## Refinement DoR Pre-Screening Checklist Item

```markdown
- [ ] **Pre-Screen Against Definition of Ready (DoR):** Candidate items have clear business value context (target consumer & ROI) and testable BDD acceptance criteria (*Given-When-Then*) attached prior to the refinement meeting.

---

## Refinement DoR Checklist Item

```markdown
- [ ] **Data Contract Attached:** Upstream field mapping, explicit target data types, primary keys, nullability rules, and schema contract definitions are attached to the Jira issue.


---
## 2. What to Bring to the Refinement Session (The Toolkit)

| Artifact / Tool | Purpose in Data Refinement |
| :--- | :--- |
| **Data Definition of Ready (DoR) Checklist** | Displayed during the meeting as a strict quality gate before sizing. |
| **70/20/10 Capacity Allocation Framework** | Ensures candidates balance business features, technical enablers, and debt. |
| **Planning Poker Tool** | (e.g., PlanITpoker, Jira Estimation) For relative estimation. |
| **Architecture / Pipeline Diagram** | Visually traces data flow (Ingestion $\rightarrow$ dbt Transformation $\rightarrow$ Serving Layer/Tableau). |
| **Impediment / Dependency Board** | For logging external blockers (e.g., waiting on CRM vendor API access). |

---

## 3. Step-by-Step Refinement Session Guide (60 Minutes)

┌─────────────────────────────────────────────────────────────────────────────┐
│                     60-MINUTE REFINEMENT TIMEBOX ALLOCATION                 │
├───────────────────┬───────────────────┬───────────────────┬─────────────────┤
│ 00-05m: Alignment │ 05-45m: Deep Dive │ 45-55m: Sizing    │ 55-60m: Wrap Up │
│ Goal & Capacity   │ DoR & Contracts   │ Planning Poker    │ DoR Sign-off    │
└───────────────────┴───────────────────┴───────────────────┴─────────────────┘


### Stage 1: Welcome & Capacity Alignment (5 Mins)
* **Objective:** Set the session goal and review capacity split rules.
* **SM Script:**  
  > *"Welcome everyone. Today our goal is to refine and size candidates for Sprints 12 and 13. Remember, we adhere to our **70/20/10 Capacity Allocation Policy** (70% Features, 20% Technical Enablers, 10% Debt). Let's start with our top-ranked WSJF feature candidate."*

### Stage 2: Story Walkthrough & Data Contract Verification (20 Mins)
* **Objective:** Ensure the squad understands *what* needs to be built and *how* data validation will occur.
* **Key Facilitation Questions to Ask the Team:**
  1. *PO:* "What is the core business decision or reporting KPI this dataset enables?"
  2. *Data Engineer:* "Do we have an agreed Data Contract or schema definition from the upstream source team?"
  3. *Data Analyst/QA:* "What automated data quality checks (`dbt test`, null checks, uniqueness) are required for this story to meet DoD?"

### Stage 3: Slicing & Vertical Decomposition (20 Mins)
* **Objective:** Break down monolithic "ETL Epics" into vertical, deliverable slices.
* **SM Slicing Pattern for Data Teams:**
❌ MONOLITHIC HORIZONTAL STORY (13 pts):
"Build entire Customer Data Platform pipeline"

YES -> VERTICAL SLICES (Sliced for Flow):
├── Slice A (3 pts): Ingest raw CRM customer table to S3 Staging (with schema check)
├── Slice B (5 pts): Build dbt staging model & run primary key uniqueness test
└── Slice C (3 pts): Create Tableau reporting view with row-level security


### Stage 4: Relative Estimation & DoR Sign-Off (10 Mins)
* **Objective:** Size stories relatively and verify DoR pass.
* **Facilitation Steps:**
1. Open Planning Poker.
2. Compare candidate item against the team's **3-Point Baseline Reference Story**.
3. Vote simultaneously using Fibonacci numbers ($1, 2, 3, 5, 8$).
4. If estimates diverge (e.g., 2 vs. 8): Ask the lowest and highest voters to explain their reasoning (often reveals hidden technical risks or missing access permissions).
5. Apply the DoR quality gate: If it passes all checks, mark as **`Ready for Sprint`**.

### Stage 5: Wrap-up & Action Log (5 Mins)
* **Objective:** Assign action owners for stories that failed DoR.
* **SM Action:** Log missing dependencies (e.g., *"PO to obtain sample JSON payload from Vendor by Thursday"*).

---

## 4. Handling Common Data Refinement Edge Cases

| Scenario / Edge Case | Cause | Scrum Master Facilitation Response |
| :--- | :--- | :--- |
| **"We can't size this because we don't know the schema."** | Upstream source is unknown or unverified. | **Convert to a Spike:** Create a 2-point, timeboxed Research Spike (max 2 days) to inspect the API/database and write the Data Contract. Do not size the main story until the spike finishes. |
| **"This story is just research and model testing."** | Machine Learning or Data Science EDA tasks. | **Apply Bounded Outcomes:** Require the Data Scientist to state explicit completion criteria (e.g., *"Document decision memo evaluating 2 algorithms with $R^2 > 0.85$ score"*). |
| **"The story is 13 or 21 Story Points."** | Story is too large; high risk to flow. | **Enforce Story Slicing:** Rule: *No story larger than 8 points enters a sprint.* Slice vertically by dataset, environment, or field complexity. |

---

## 5. Refinement DoR Quality Gate Matrix

```markdown
### Refinement DoR Quick Check (All must be TRUE to assign "Ready for Sprint")

- [ ] **Value Context:** Clear statement of business outcome and end consumer.
- [ ] **Data Contract:** Schema definitions, field mapping, and data types attached.
- [ ] **Acceptance Criteria:** Written in testable BDD format (*Given-When-Then*).
- [ ] **Data Quality Gate:** Automated test assertions specified (e.g., zero nulls on primary key).
- [ ] **Sized Relatively:** Estimated by the squad using Fibonacci relative sizing ($\le 8$ points).
- [ ] **Categorized:** Tagged as `Business Feature`, `Technical Enabler`, or `Technical Debt`.
