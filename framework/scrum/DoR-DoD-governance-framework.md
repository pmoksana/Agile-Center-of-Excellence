# Enterprise Definition of Ready (DoR) & Definition of Done (DoD) Governance Framework

A comprehensive guide for Scrum Masters and Delivery Leads in SAFe/Scaled Agile environments to establish tailored **Definitions of Ready (DoR)** across specialized domain teams, manage story returns, and evaluate **Definitions of Done (DoD)** quality.

---

## 1. Domain-Specific Definitions of Ready (DoR)

In scaled environments, a single generic DoR fails because specialized teams (Data Engineering, DevSecOps/CI-CD, Web/Mobile) interact with fundamentally different risk profiles and artifacts. 

The baseline criteria below apply universally across all teams, followed by domain-specific extensions.

### Universal Baseline DoR (All Teams)
* [ ] **Business Value & Goal:** Clear value statement linked to a Feature or PI Objective.
* [ ] **Acceptance Criteria:** Written in clear BDD (`Given-When-Then`) format.
* [ ] **Sizing:** Estimated using normalized relative story points ($\le 25\%$ of iteration capacity).
* [ ] **Dependencies:** External dependencies logged and mapped on the ART Program Board.
* [ ] **UX/UI Artifacts:** Figma/design assets attached (if user-facing).

---

### A. Data Engineering & Governance DoR (GDoR)
* [ ] **Business Glossary Mapping:** Business terms defined and linked to **Collibra** glossary entries.
* [ ] **Data Lineage:** Source-to-Target mapping documented (Source tables, transformations, target schema).
* [ ] **Data Quality (DQ) Rules:** Explicit validation rules defined (e.g., null thresholds, regex pattern, unique keys).
* [ ] **Privacy & Compliance:** PII/PHI status identified and data masking/retention requirements specified (GDPR/BCBS 239).
* [ ] **Data Access:** Dev/Staging database access and test datasets verified before iteration start.

### B. DevSecOps & CI/CD Infrastructure DoR
* [ ] **Environment Scope:** Target infrastructure environment explicitly defined (Dev, Staging, Prod-Mirror).
* [ ] **Security & Policy Compliance:** IAM roles, least-privilege policies, and compliance guardrails specified.
* [ ] **Architecture Approval:** Infrastructure as Code (IaC) pattern approved by System Architect/SecOps.
* [ ] **Rollback Strategy:** Clear rollback criteria and recovery requirements documented.
* [ ] **Resource/Cost Impact:** Cloud cost impact estimated for new infrastructure components.

### C. Application / API Development DoR (C# / Python / Web)
* [ ] **API Contracts:** Swagger/OpenAPI spec defined and agreed between producer and consumer teams.
* [ ] **Data Models:** Schema contracts and payload structures validated.
* [ ] **Non-Functional Requirements (NFRs):** Response time SLAs and throughput specs defined.
* [ ] **Mock Endpoints:** Mock APIs available if upstream dependencies are in development.

---

## 2. Best Practice: Returning Unrefined Stories ("Story Rejection Workflow")

When a Product Owner presents a story during Iteration Planning that fails the DoR, pulling it into the sprint creates mid-iteration blockers, scope churn, and technical debt.

### How to Gracefully Return a Story Back to the Backlog
1. **Apply the "GDoR Firewall":** The Scrum Master acts as the neutral facilitator. Returning a story is not a punishment—it protects the team from failure.
2. **Document the Deficit:** Tag the story in Jira with `Blocked-DoR` and leave a explicit comment detailing which checklist item failed (e.g., *"Missing Collibra glossary entry for field X"*).
3. **Assign an Actionable Sub-Task:** If research or architectural clarification is needed, create a timeboxed **Technical Spike** or **Data Discovery Task** for the upcoming iteration instead of pulling in the unrefined implementation story.
[ Unrefined Story ] 
           │
  ( Refinement / GDoR )
           │
   Is DoR 100% Met? ────── No ─────► [ Return to Funnel ]
           │                          │ Assign Spike / Action Item
          Yes                         ▼
           │                    [ Refine in N+1 ]
           ▼

   
