# Normalized Relative Estimation: The "1-Point Story" Baseline

To enable meaningful predictability and cross-team alignment across an Agile Release Train (ART), teams must share a common baseline for Story Points. A **1-Point Story** serves as the universal reference benchmark ($1\text{ SP}$) representing a low-complexity, low-risk, highly predictable unit of work.

---

## 1. Concrete Examples of a Shared "1-Point" Baseline Story

A standard **1-Point Baseline Story** across technical and data governance teams satisfies three criteria:
1. **Low Effort:** Can be completed by a single team member in a fraction of a day.
2. **Zero Complexity:** The implementation steps and pattern are fully known.
3. **No Unknowns / Risk:** No external dependencies, research spikes, or policy ambiguities.

### Example A: Data Governance / Collibra Context
> **Story Title:** Register a new Business Term and assign ownership in Collibra.
> 
> **Description:** Add the approved definition, data type, and designated Data Steward for a newly identified attribute (e.g., `Flight_Delay_Reason_Code`) to the enterprise Business Glossary.
> 
> **Acceptance Criteria:**
> * Business Term name and definition added to Collibra Glossary.
> * Data Steward assigned and status updated to `Draft / Pending Sign-off`.
> * No schema or code changes required.

### Example B: Technical / Application Context (C# / Python)
> **Story Title:** Add an existing error code to an API logging dictionary.
> 
> **Description:** Update a known lookup dictionary/enum in a C# microservice or Python script to handle a new standard error response code.
> 
> **Acceptance Criteria:**
> * Enum updated with the new error code.
> * Unit test updated using existing test suite patterns.
> * Code passes local build and linting checks.

---

## 2. Baseline Story Calibration Matrix

Use this relative scale to calibrate your team during Backlog Refinement and Estimation:

| Story Points | Complexity | Uncertainty | Dependencies | Relative Effort Example |
| :---: | :--- | :--- | :--- | :--- |
| **1 SP** *(Baseline)* | **Negligible:** Known pattern, routine task | **None:** 100% clear requirements | **None:** Completely internal | Updating a glossary term or config file key |
| **2 SP** | **Low:** Minor logic changes | **Low:** Well-understood domain | **Minimal:** Standard code review | Adding a new field to an existing API response |
| **3 SP** | **Medium:** Routine feature modification | **Low–Moderate:** Minor edge cases | **Internal:** Requires DB migration | Creating a new validation endpoint or ETL rule |
| **5 SP** | **High:** Multi-component logic | **Moderate:** Technical trade-offs | **External:** Inter-team interface | Building a new microservice component or lineage map |
| **8 SP+** | **Very High:** Refactor or complex data flow | **High:** Potential unknowns | **Cross-ART:** Upstream dependencies | *Action:* Split into smaller stories |

---

## 3. How to Coach Teams on Baseline Normalization

1. **Pick a Reference Story Together:** During PI Planning or ART Launch, select 2–3 historical "1-point" stories that every team agrees represent minimal effort and zero risk.
2. **Estimate Relatively, Not in Hours:** Remind engineers that $1\text{ SP}$ does not equal a fixed number of hours. It measures **Effort + Complexity + Uncertainty**.
3. **Guard Against Drift:** Periodically revisit the baseline during Retrospectives to ensure teams aren't inflating points over time (Point Inflation).

---

## 4. GitHub Pages Front Matter Integration

```yaml
---
layout: post
title: "Agile Estimation Framework: Establishing a Normalized 1-Point Baseline"
date: 2026-09-30
categories: [Agile, SAFe, Capacity Planning]
tags: [Story Points, Relative Estimation, Baseline, SAFe, Scrum Master]
author: "Delivery Leadership Team"
summary: "A practical guide to defining a normalized 1-point baseline story across multi-functional data and engineering teams."
---
