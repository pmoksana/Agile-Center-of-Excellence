# 📊 Metrics & Data Visualization
> Powering the team with Real-Time Engineering Insights


---
[⬅️ Back to Main Guide](../../)
---

## Data-Driven Agility
We don't guess—we measure. By integrating **ClickUp** with **Power BI**, we transform raw task data into actionable insights, allowing us to identify bottlenecks in our Lambda deployments and brand onboarding flows in real-time.



### 🔄 The Integration: ClickUp + Power BI
Our data pipeline is designed to provide a "single source of truth" for stakeholders and engineering leads:

1.  **Data Ingestion:** We use the ClickUp API to export workspace data (Task status, Time estimates, and Custom Fields).
2.  **Transformation:** Data is processed via AWS Lambda to clean and format JSON payloads for Power BI.
3.  **Visualization:** Power BI Dashboards refresh hourly to show live team health.

---

## 📈 Key Performance Indicators (KPIs)

We track three primary categories of data to ensure our **Redesign Phase** and **New Brand Onboarding** are on track:

### 1. Delivery Velocity
* **Cycle Time:** The time it takes for a brand campaign to go from "Discovery" to "Live."
* **Lead Time:** The total time from a feature request to AWS Lambda production deployment.
* **Throughput:** Number of story points or tasks completed per sprint.

### 2. Quality & Automation (CI/CD)
* **Test Pass Rate:** Percentage of automated Web/Mobile tests passing in Lambda environments.
* **Deployment Frequency:** How often we push code to production.
* **Change Failure Rate:** Percentage of deployments that require a rollback or hotfix.

### 3. Resource Allocation
* **Feature vs. Fix Ratio:** Are we spending too much time on bugs vs. new brand features?
* **Sprint Burndown:** Real-time visibility into whether the team will meet the sprint commitment.

---

## 🛠 Accessing the Dashboards
* **Executive Overview:** [Link to Power BI Dashboard - Shping Strategic View]
* **Engineering Health:** [Link to Power BI Dashboard - Squad Level Metrics]
* **ClickUp Workspace:** [Direct link to Shping ClickUp Space]

> **Note:** Access to Power BI reports requires a Shping.com organizational account and specific workspace permissions.

---

## 🧼 Data Hygiene Standards
To ensure our visualizations are accurate, every team member commits to:
* **Real-time Status Updates:** Move tasks in ClickUp as soon as work begins/ends.
* **Accurate Tagging:** Use the `Redesign`, `Brand-Onboard`, or `Tech-Debt` tags correctly.
* **Time Tracking:** Log hours directly in ClickUp for high-accuracy capacity planning.

---

## 🚀 Performance Benchmarks: What "Good" Looks Like
To drive excellence we measure our progress against modern engineering standards. While our own baseline is our primary focus, these benchmarks help us identify where our **AWS Lambda** workflows or **Brand Onboarding** processes can be optimized.

### 📊 Delivery & Flow Standards

| Metric | Great (Target) | Good (Baseline) | Needs Attention |
| :--- | :--- | :--- | :--- |
| **Change Lead Time** | < 1 working day | < 3 working days | > 7 working days |
| **PR Cycle Time** | < 1 working day | < 3 working days | > 5 working days |
| **Time to Deploy** | < 15 minutes | < 30 minutes | > 1 hour |
| **Deployment Frequency** | Continuous | Daily | Weekly / Manual |
| **Batch Size** | < 200 lines | < 500 lines | > 500 lines |
| **Flow Efficiency** | > 95% Active | > 70% Active | < 70% (High Idle) |

---

## 🏗 Investment Balance
We categorize our engineering effort to ensure we are scaling **Shping.com** effectively while maintaining our infrastructure.

| Investment Category | Great | Good | Needs Attention |
| :--- | :--- | :--- | :--- |
| **New Features** (Redesign/Brands) | 60% | 50% | < 40% |
| **Productivity** (CI/CD / Tooling) | 15% | 10% | < 5% |
| **KTLO** (Bugs / Maintenance) | 10% | 30% | > 50% |

---

## 🔍 How to Use These Metrics at Shping

### ⚡ Speed (Lead Time & PR Cycle)
We aim for **PR Cycle Times under 24 hours**. This ensures that brand-specific updates and redesign components move through our pipeline without creating bottlenecks.

### 🧪 Batch Size & Risk
We prioritize **small batches (<200 lines)**. Smaller changes are easier to test on our mobile automation suites and carry significantly less risk when deploying to our AWS Lambda production environment.

### 🔄 Flow Efficiency
High idle time (low efficiency) usually suggests that engineers are waiting for feedback or blocked by dependencies. We use our **ClickUp + Power BI** integration to flag tasks that have been "In Progress" but inactive for more than 48 hours.

---

## 🛠 Action Plan for "Needs Attention"
If a squad falls into the **Needs Attention** category:
1.  **Retrospective Focus:** Discuss the blocker in the next Team Retro.
2.  **Automation Check:** Can we speed up the **Lambda CI/CD** or **Mobile Tests**?
3.  **WIP Review:** Reduce the number of active tasks in ClickUp to focus on finishing current work.


---
**Next Steps:**
* [**Review Team Workflows**](./team-workflow.md)
* [**View Working Agreements**](/Working-Agreements/commitment.md)



