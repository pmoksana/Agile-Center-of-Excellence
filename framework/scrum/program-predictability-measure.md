# Program Predictability Measure (PPM): Calculation & Inputs

The **Program Predictability Measure (PPM)** evaluates how reliably an Agile Release Train (ART) delivers planned business value across a Program Increment (PI). It compares the **actual business value achieved** at the end of the PI against the **planned business value committed** during PI Planning.

---

## 1. Primary Mathematical Formula

The overall PPM percentage for an ART is calculated using the following formula:

$$\text{Program Predictability Measure (\%)} = \left( \frac{\sum \text{Actual Business Value Achieved}}{\sum \text{Planned Business Value Committed}} \right) \times 100$$

* **Target Range:** **80% – 100%**
* **Under 80%:** Indicates over-commitment, unmanaged dependencies, mid-PI churn, or high technical debt.
* **Over 100%:** May indicate under-commitment, artificial buffer padding, or scope creep maskings.

---

## 2. Core Metrics & Input Data Points

To calculate and analyze PPM, the Release Train Engineer (RTE) and Scrum Masters track four primary input variables for every team on the train:

| Metric / Input Variable | Description | Value Scale |
| :--- | :--- | :--- |
| **Planned Business Value (BV)** | Assigned by Business Owners during PI Planning for every committed PI Objective. | **1 to 10** |
| **Actual Business Value (BV)** | Assigned by Business Owners during the System Demo at the end of the PI based on delivered outcomes. | **1 to 10** |
| **Uncommitted Objectives** | High-risk or capacity-uncertain objectives added to the plan. They are **excluded** from the denominator (planned total) but **included** in the numerator if achieved. | **0 to 10** (if achieved) |
| **Achievement Percentage** | The individual team score comparing actual vs. planned business value before calculating the train-level average. | **0% – 100%+** |

---

## 3. Step-by-Step Calculation Example

### Team Objective Score Breakdown

Suppose **Team Alpha** commits to 4 objectives and 1 uncommitted objective during PI Planning:

| Objective Type | Objective Description | Planned BV | Actual BV Achieved | Included in Denominator? |
| :--- | :--- | :---: | :---: | :---: |
| **Committed** | Checkout Page Redesign | 10 | 10 | Yes |
| **Committed** | Payment Gateway API V2 | 8 | 8 | Yes |
| **Committed** | Automated Test Pipeline | 6 | 4 (Partial) | Yes |
| **Committed** | User Profile Export | 5 | 0 (Missed) | Yes |
| **Uncommitted**| One-Click Guest Checkout | *0 (N/A)* | 7 (Delivered) | **No** |
| **Total** | | **29** | **29** | |

$$\text{Team Alpha PPM} = \left( \frac{10 + 8 + 4 + 0 + 7}{10 + 8 + 6 + 5} \right) \times 100 = \left( \frac{29}{29} \right) \times 100 = \mathbf{100\%}$$

---

## 4. Complementary Flow Metrics Used alongside PPM

While PPM measures business satisfaction and predictability, RTEs use three underlying SAFe Flow Metrics to diagnose *why* PPM is high or low:

### A. Commitment vs. Completion Ratio (Story Points)
* **What it measures:** Total story points planned during Sprint/PI Planning vs. actual story points completed.
* **Role in PPM:** Verifies if low PPM is caused by technical execution bottlenecks or over-estimating capacity.

### B. Flow Load (Work in Process - WIP)
* **What it measures:** The total amount of active work items currently in the system across the train.
* **Role in PPM:** Excess Flow Load increases queue wait times, leading to missed PI Objectives and lower PPM.

### C. Feature Cycle Time
* **What it measures:** The elapsed time from when a feature moves to "In Progress" until it reaches "Done".
* **Role in PPM:** High feature cycle times directly cause team objectives to spill over past the PI boundary, dragging down total achieved business value.

---

## 5. Summary Dashboard View
  

### ART Predictability Overview

| Metric Parameter | Target Range | Current ART Score | Overall Status |
| :--- | :---: | :---: | :---: |
| **Program Predictability Measure (PPM)** | 80% – 100% | **88.5%** | 🟢 **ON TARGET** |

---

### Team-Level Performance Breakdown

| Team Name | Planned Business Value | Actual Business Value Achieved | Individual PPM Score | Target Status |
| :--- | :---: | :---: | :---: | :---: |
| **Team Alpha** | 29 | 29 | **100.0%** | 🟢 On Target |
| **Team Beta** | 33 | 27 | **81.8%** | 🟢 On Target |
| **Team Gamma** | 25 | 21 | **84.0%** | 🟢 On Target |
| **ART Total / Average** | **87** | **77** | **88.5%** | 🟢 **ON TARGET** |

### ART Predictability Overview

| Metric Parameter | Target Range | Current ART Score | Overall Status |
| :--- | :---: | :---: | :---: |
| **Program Predictability Measure (PPM)** | 80% – 100% | **88.5%** | 🟢 **ON TARGET** |

---
 
---


## 1. Roles & Responsibilities: Who Does What?

| Role | Key Responsibility for PPM |
| :--- | :--- |
| **Release Train Engineer (RTE)** | **Owner & Primary User.** Collects scores across all teams, presents the ART-level PPM in the *Inspect & Adapt (I&A)* event, and reports progress to executives. |
| **Business Owners** | **Value Assigners.** Assign the *Planned Business Value* (1–10) during PI Planning and evaluate/assign the *Actual Business Value* (1–10) at the PI System Demo. |
| **Scrum Masters / Team Coaches** | **Facilitators.** Ensure PI Objectives are properly logged in Jira, ensure teams record actual completion, and help calculate individual team percentages. |
| **Jira Administrator** | **Technical Implementer.** Creates custom fields, issue types (PI Objectives), and configures custom dashboards/gadgets in Jira. |

---

## 2. How to Add PPM to Jira (Configuration)

To track PPM directly inside Jira, implement one of the following methods depending on your setup:

### Approach A: Custom Jira Setup (Standard Jira Software / Jira Product Discovery)

#### Step 1: Create a Custom Issue Type
* Navigate to **Jira Settings > Issues > Issue Types**.
* Create a custom issue type called **`PI Objective`** (or track them as high-level Epics/Features tagged with a specific PI label).

#### Step 2: Add Custom Fields
Create the following custom fields under **Jira Settings > Issues > Custom Fields** and assign them to the `PI Objective` screen:

1. **`Planned Business Value`** *(Number Field)*: Score from **1 to 10** assigned during PI Planning.
2. **`Actual Business Value`** *(Number Field)*: Score from **1 to 10** assigned at the end of the PI.
3. **`Is Uncommitted?`** *(Checkbox or Select List - Options: `Yes` / `No`)*: Flags uncommitted/stretch objectives so they are excluded from the denominator.
4. **`Target PI`** *(Select List or Fix Version)*: Identifies which Program Increment the objective belongs to (e.g., `PI-2026.1`).

---

### Approach B: Enterprise Tools (Jira Align or Marketplace Apps)

* **Jira Align:** Native support for PI Objectives out of the box. Go to **Program > Program Increment > Program Objectives** or view the built-in **Program Predictability Report**.
* **Atlassian Marketplace Apps:** Use tools like *Predictability Measure for Jira Cloud*, *Agile Hive*, or *Custom Charts for Jira* (by Tempo) to aggregate and visualize PPM metrics without custom scripts.

---

## 3. How to Calculate & Track PPM

### Mathematical Calculation Formula

$$\text{Team/ART PPM (\%)} = \left( \frac{\sum \text{Actual Business Value Achieved}}{\sum \text{Planned Business Value Committed}} \right) \times 100$$

> **Rule for Uncommitted Objectives:** 
> * **Denominator (Planned):** Exclude Uncommitted Objectives.
> * **Numerator (Actual):** Include Uncommitted Objectives **only if delivered**.

---

