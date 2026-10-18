# 🚀 SAFe Data Product Coaching & WSJF Prioritization Guide

<div align="center">

| **Framework** | **Focus Area** | **Target Audience** |
| :--- | :--- | :--- |
| **SAFe 6.0** | Data & Analytics Value Delivery | Product Owners, Scrum Masters, & Engineering Leads |

</div>

---

## 🎯 Executive Overview & Purpose

In complex technical environments like data engineering, analytics, and cloud infrastructure, **Product Owners (POs)** often face friction when technical preference overrides business value. 

This guide and coaching framework equips POs to take absolute ownership of the backlog by utilizing **Weighted Shortest Job First (WSJF)**, translating technical debt into business risk, and collaborating seamlessly with engineering squads.

---

## ⚖️ The Product Owner's Golden Rule

> **The PO decides WHAT and WHY** based on business value, strategic themes, and Cost of Delay.<br>
> **The Team decides HOW and HOW MUCH** based on technical implementation and sprint capacity.

---

## 📊 The WSJF Prioritization Formula

Gut-feel prioritization (*"I think this is important"*) does not scale. In SAFe, we prioritize data initiatives objectively using **WSJF**:

$$\text{WSJF} = \frac{\text{Cost of Delay (CoD)}}{\text{Job Size (Duration)}}$$

### 1. The Numerator: Cost of Delay (CoD) Components
* **User-Business Value (BV):** Does this initiative generate revenue, reduce operational cost, or satisfy regulatory compliance/governance?
* **Time Criticality (TC):** Is there a hard business deadline? Does the value decay rapidly if delayed?
* **Risk Reduction & Opportunity Enablement (RR | OE):** Does this data pipeline unlock future capabilities, or does *not* doing it expose the firm to severe risk (e.g., data breach, broken reporting)?

### 2. The Denominator: Job Size
* **Duration / Effort:** Estimated relative effort required to build, test, and deploy the data feature (using Fibonacci numbers: `1, 2, 3, 5, 8, 13`).

---

## 📝 Hands-On Simulation: Scoring Data Epics

Use this exercise during your PO coaching sessions to practice scoring conflicting backlog items:

| Initiative / Epic | User Value (1-10) | Time Criticality (1-10) | Risk Reduction (1-10) | **Total CoD** | Job Size (1-13) | **WSJF Score** | **Priority Rank** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **A. Core Cloud Migration** *(Tech-heavy)* | 3 | 2 | 4 | **9** | 13 | **0.69** | 🥉 *Rank 3* |
| **B. Executive Financial Dashboard** | 9 | 10 | 8 | **27** | 5 | **5.40** | 🥇 *Rank 1* |
| **C. SQL Query Optimization** *(Performance)* | 6 | 5 | 7 | **18** | 3 | **6.00** | 🥈 *Rank 2* |

> 💡 **Coaching Takeaway:** Notice how Item A (the massive tech migration) scored high on engineering preference but low on business time-criticality, pushing it down the queue unless reframed as a business risk.

---

## 🛡️ The PO Pushback & Negotiation Playbook

When engineering pushes hard for technical rewrites over business deliverables, coach your POs to use these two rules:

### 🔹 Rule 1: Translate Technical Debt into Business Risk
* ❌ **Never accept:** *"We need to refactor the data pipeline."*
* ✅ **Coach the PO to ask:** *"What is the exact Cost of Delay or risk if we defer this refactoring by one Planning Interval (PI)? If it doesn't break reporting or compliance, where does it rank on WSJF against customer-facing features?"*

### 🔹 Rule 2: Negotiate Fixed Capacity for Tech Enablers
* Protect team morale by establishing a **fixed capacity allocation** (e.g., dedicating **20% of every sprint** exclusively to technical debt, architecture enablers, and pipeline health). 
* This satisfies the engineers' need for technical excellence without letting it hijack 100% of the product backlog.

---

## 🛠️ Action Items for Your Next Sprint

1. **Audit the Backlog:** Review current epics and tag them with WSJF scores.
2. **Protect the PO:** Ensure engineering respects the PO's final authority on the *What*.
3. **Establish Capacity Guardrails:** Lock in a fixed percentage for technical enablers to maintain pipeline hygiene.

---

<div align="center">
  <p><em>Designed for SAFe Agile Centers of Excellence & Enterprise Delivery Teams</em></p>
</div>
