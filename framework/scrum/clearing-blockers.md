# AWS Data Migration Strategy: Clearing Infrastructure Blockers

As a Scrum Master on a high-stakes AWS data migration project, infrastructure blockers—such as pending AWS IAM permissions, database connection strings, network firewall rules, or unprovisioned staging environments—are among the most frequent causes of stalled engineering flow.

Here is a systematic approach to clearing these blockers before they impact the team, along with the metrics and tools required to support the process.

---

## 1. How to Clear Infrastructure Blockers Proactively

* **Pre-Sprint Readiness Audits (Definition of Ready Enforcement):**
  * During Backlog Refinement, do not allow user stories into the sprint unless prerequisite infrastructure, environment access, and AWS IAM policies are confirmed ready.
  * Audit stories against an **Infrastructure Checklist** (e.g., target S3 bucket provisioned, database VPN ports open, AWS Glue job IAM role created).

* **Aggressive Blocker Escalation & Swarming:**
  * Identify environment delays early during the Daily Standup by asking: *"Are you waiting on any AWS access, pipeline triggers, or infrastructure provisioning today?"*
  * If an engineer is blocked for more than **2 hours**, immediately pull in the DevOps/Cloud Infrastructure team lead or escalate to the Release Train Engineer (RTE) or Engineering Manager.

* **Automated & Self-Service Provisioning Collaboration:**
  * Partner with Cloud Platform/DevOps engineers to move away from ticket-based infrastructure requests toward **Terraform/CloudFormation self-service templates** or scripted IAM setups.

* **Isolate & Shift Technical Dependencies Left:**
  * Use **Sprint 0** or dedicated **Enabler Stories** in preceding iterations to establish underlying infrastructure (e.g., AWS DMS endpoints, Terraform modules) before feature/migration stories begin.

---

## 2. Essential Metrics to Establish

To manage infrastructure health objectively and prove where delays occur, track these key metrics:

* **Blocker Resolution Lead Time (BRLT):**
  * **What it measures:** The total duration from when an infrastructure blocker is flagged on the board to when it is fully resolved.
  * **Target:** `< 24 hours` for standard environment or permission blockers.

* **Work Item Aging (Focus on Infrastructure Flags):**
  * **What it measures:** The exact number of hours or days an active story spends sitting in columns like *"Blocked"* or *"In Infrastructure Provisioning."*
  * **Target:** Highlight any story aging beyond `48 hours` in the same state for immediate swarming.

* **Infrastructure-Induced Downtime / Idle Time:**
  * **What it measures:** Percentage of team sprint capacity lost waiting for environment availability, broken deployment pipelines, or target database connectivity.
  * **Target:** `< 5%` of total sprint capacity.

* **Change Failure Rate (CFR) & Deployment Pipeline Failure Rate:**
  * **What it measures:** The percentage of infrastructure changes (e.g., Terraform script runs, IAM updates, network route additions) that fail and halt development.
  * **Target:** `< 10%` pipeline failure rate.

---

## 3. Recommended Tools & Ecosystem

| Category | Primary Tools | How the Scrum Master Uses Them |
| :--- | :--- | :--- |
| **Board Tracking & Visibility** | Jira Software / Azure DevOps | Flag stories with an `Infrastructure-Blocked` tag or dedicated custom field. Set up automated board alerts when an item remains flagged for over 24 hours. |
| **Pipeline & Cloud Visibility** | AWS CloudWatch / AWS EventBridge / GitHub Actions | Monitor automated build, pipeline deployment, and AWS Glue/DMS execution status. Receive automated Slack/Teams notifications when pipeline builds fail. |
| **Incident & Escalation Management** | PagerDuty / Opsgenie / Slack Channels | Establish dedicated `#infra-blockers` or `#aws-access-requests` channels with DevOps on-call engineers for rapid escalation during sprints. |
| **Real-time Metrics & Dashboards** | Jira Control Charts / Power BI / Tableau | Build visual dashboards displaying **Blocker Aging**, **Control Charts** (for cycle time variance), and **Infrastructure Dependency Trees**. |
