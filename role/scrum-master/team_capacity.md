# Net Team Capacity Calculation    

Calculating **Net Team Capacity** accurately is the process of determining the real, available bandwidth an Agile team has to execute work during an iteration or Program Increment (PI), rather than relying on gross velocity or theoretical maximum hours.

In SAFe, failing to account for PTO, routine operational maintenance, and intentional capacity splits leads to over-commitment, burnout, and missed PI Objectives.

---

## 1. The Net Capacity Mathematical Formula

To move from raw baseline velocity to available capacity for **Business Features**, apply this sequential formula:

$$\text{Gross Baseline Capacity} - \text{Non-Working Time (PTO / Holidays)} = \text{Gross Working Capacity}$$

$$\text{Gross Working Capacity} - \text{Maintenance \& Support Buffer (10\%)} = \text{Net Working Capacity}$$

$$\text{Net Working Capacity} \times \text{Capacity Split Ratio (e.g., 70\% Features / 20\% Enablers)} = \text{Allocated Target Capacity}$$

---

## 2. Step-by-Step Breakdown of Input Variables

### Step 1: Base Velocity / Gross Capacity
Start with the team's historical baseline capacity per iteration:
* **Initial SAFe Baseline:** A standard starting baseline for a **10-day iteration (2 weeks)** is **8 story points per full-time developer/analyst** (excluding Scrum Master and Product Owner).
* **Established ART Baseline:** Use the rolling average of completed story points across the last 3 consecutive sprints.

### Step 2: Factoring in Paid Time Off (PTO) & Holidays
Deduct capacity for planned absences before scheduling any backlog items:
* **Calculation:** If a developer takes 2 days off during a 10-day sprint, their personal capacity is reduced by **20%** ($2 \div 10$).
* **Team Impact:** If a 5-person execution team usually delivers 40 story points, and one engineer is away for 5 days (half the sprint), deduct **4 points** directly from the gross baseline.

### Step 3: Factoring in Operational Maintenance & Support Overhead
Data and software engineering teams always face operational overhead (production alerts, routine pipeline maintenance, bug triage, and minor system updates):
* **Calculation:** Reserve a fixed buffer—typically **10% to 15%** of gross capacity—for operational maintenance.
* **Why it matters:** If you do not explicitly budget for maintenance, this work still occurs—it simply steals capacity from committed PI Objectives, dragging down your Program Predictability Measure (PPM).

### Step 4: Applying the 70 / 20 / 10 Capacity Split
Once you have determined the **Net Working Capacity** (after PTO and operational buffers), distribute the remaining capacity across work types:

| Work Category | Target Split | Purpose & Scheduled Deliverables |
| :--- | :---: | :--- |
| **Business Features** | **70%** | Direct business value delivery, user stories, customer-facing analytics enhancements. |
| **Enablers & Tech Debt** | **20%** | Architectural runway, pipeline refactoring, schema optimization, CI/CD automation, and **Spikes**. |
| **Bugs & Maintenance** | **10%** | Unplanned production incidents, pipeline breaks, and operational support buffer. |

---

## 3. Concrete Example Calculation

Consider a **Data & Feature Team** preparing for a **2-week iteration (10 working days)**:

### Team Composition (5 Execution Roles):
* 2 Data Engineers
* 2 Software Engineers
* 1 Data Analyst
*(Note: SM and PO capacity is excluded from story point calculations).*

### The Calculation Steps:

1. **Gross Baseline Velocity:** $5 \text{ members} \times 8 \text{ points baseline} = \mathbf{40 \text{ Story Points}}$.
2. **Deduct PTO & Holidays:**
   * Data Engineer A takes 5 days PTO (50% of sprint = -4 points).
   * Software Engineer B takes 2.5 days PTO (25% of sprint = -2 points).
   * **Adjusted Gross Capacity:** $40 - 6 = \mathbf{34 \text{ Points}}$.
3. **Apply 70/20/10 Allocation Split on 34 Points:**
   * 🟢 **Business Features (70%):** $34 \times 0.70 = 23.8 \rightarrow \mathbf{24 \text{ Points}}$
   * 🔵 **Architecture & Data Enablers / Spikes (20%):** $34 \times 0.20 = 6.8 \rightarrow \mathbf{7 \text{ Points}}$
   * 🔴 **Bugs & Maintenance Buffer (10%):** $34 \times 0.10 = 3.4 \rightarrow \mathbf{3 \text{ Points}}$

### Final Planning Commitments:
During Sprint Planning, the team commits to **24 story points of Business Features** and **7 points of Architecture Enablers/Spikes**, leaving 3 points unallocated for operational support.

---

## 4. Scrum Master Audit Checklist for Sprint Planning

- [ ] **PTO Audit:** Has every team member updated their planned vacation, training, and public holiday hours in the team availability sheet?
- [ ] **No 100% Feature Commitments:** Is the Product Owner attempting to fill 100% of available capacity with business features? (Enforce the 20% Enabler reservation).
- [ ] **Data Support Buffer Protected:** Is the 10% operational support buffer kept clear of scheduled features to handle unexpected pipeline disruptions or ad-hoc query escalations?
- [ ] **Spike Allocation:** Are high-risk or ambiguous data tasks allocated out of the **20% Enabler** bucket as timeboxed Spikes rather than standard feature capacity?
---

# Calculating Net Team Capacity for Data & Analytics Teams

Calculating capacity for Data Engineering and Data Analytics teams requires a specialized approach compared to standard software development teams. Data teams face unique operational realities: **pipeline breaks, fuzzy data exploration, shifting upstream schemas, ad-hoc query escalations, and model tuning**.

---

## 1. The Data Capacity Mathematical Formula

To derive predictable capacity, convert gross baseline points/hours into available bandwidth for scheduled work:

$$\text{Gross Baseline Capacity} - \text{PTO \& Holidays} = \text{Working Capacity}$$

$$\text{Working Capacity} - \text{Data Ops / Firefighting Buffer (15\%–20\%)} = \text{Net Working Capacity}$$

$$\text{Net Working Capacity} \times \text{Allocation Ratios (60\% Features / 25\% Enablers / 15\% Bugs)} = \text{Commitment Cap}$$

---

## 2. Specialized Capacity Allocation for Data Teams

Standard software teams often use a **70/20/10** capacity split. For Data Engineers and Data Analysts, the operational load is higher, requiring a modified **60 / 25 / 15** capacity model:
--
