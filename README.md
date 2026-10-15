

#Strategic Guide for Scaled Agile & Digital Transformation 
 
 *Roadmap for Agile maturity.*
---

##  Framework
* [**SAFe**](./framework/scrum.md/)


## SAFe adoption
* [**SAFe implementation**](./SAFe adoption/SAFe-implementation.md/)
* [**SAFe adoption_plan**](./SAFe adoption/adoption_plan.md/)


  
### 👥 Role-Specific Guides
* [**Product Owner Guide**](./role/product-owner/) - Accountable for maximizing product value and backlog transparency.
* [**Development Team Guide**](./role/development-team/) - Professionals committed to creating any aspect of a usable Increment.
* [**DevOps**](./role/devops/) - CI/CD and Serverless workflows, AWS Lambda.
* [**QA**](./role/qa/) - Agile testing standards, Quality Gates.
* [**Scrum Master Guide**](./role/scrum-master/) - Facilitator and coach for the Scrum Team and organization.

### 👥 Scrum master Guides
* [**Scrum Master^s day**](./role/scrum-master/scrum-master-day/)
* [**Daily metrics**](./role/scrum-master/daily-metrics/)
* [**Scrum Master & Product Owner Collaboration Framework**](./role/scrum-master/Scrum-master-&-product-owner)
* [**AWS Data Migration Strategy: Clearing Infrastructure Blockers**](./framework/scrum/clearing-blockers.md


# SAFe Events & Ceremonies Directory

In the Scaled Agile Framework (SAFe), events (formerly called ceremonies) are organized across four architectural levels to align teams, manage dependencies, evaluate flow, and ensure continuous delivery.

Below is the central index of event facilitation guides, coaching scripts, metrics, and checklists tailored for Data & Analytics teams. Click on any event to access its dedicated operational guide.

---

## 1. Team Level Events (Iteration Cadence)

These events occur during the 2-week Iteration cycle for each Agile Team:

* [**Backlog Refinement**](./ceremonies/backlog-refinement.md)  
  *Ongoing session where the Product Owner and squad review, slice, and size user stories against the Definition of Ready (DoR).*
* [**Iteration Planning**](./ceremonies/sprint-planning.md)  
  *Teams plan and commit to stories in the team backlog using the 70/20/10 capacity model to achieve the Iteration Goal.*
* [**Team Sync (Daily Standup)**](./ceremonies/daily-standup.md)  
  *Daily 15-minute meeting to walk the board right-to-left, check progress toward the Iteration Goal, enforce WIP limits, and clear blockers.*
* [**Iteration Review (Team Demo)**](./ceremonies/sprint-review.md)  
  *At the end of every iteration, the team demonstrates working pipelines, models, and dashboards to stakeholders for feedback.*
* [**Iteration Retrospective**](./ceremonies/sprint-retrospective.md)  
  *The team reflects on process, cycle time, quality metrics, and collaboration to define continuous improvement action items.*

---

## 2. Program / ART Level Events (Planning Interval / PI Cadence)

These events coordinate all teams belonging to an Agile Release Train (ART) across an 8–12 week Planning Interval (PI):

* [**PI Planning**](./ceremonies/pi-planning.md)  
  *The cornerstone 2-day SAFe event where the entire ART aligns on vision, resolves dependencies, assigns business value, and commits to PI Objectives.*
* [**Scrum of Scrums (SoS)**](./ceremonies/art-sync-and-sos/scrum-of-scrums.md)  
  *Facilitated by the RTE with Scrum Masters to coordinate cross-team dependencies, monitor flow, and clear system-level blockers.*
* [**PO Sync**](./ceremonies/art-sync-and-sos/po-sync.md)  
  *Facilitated by Product Management with Product Owners to monitor PI scope progress, feature status, and priority trade-offs.*
* [**System Demo**](./ceremonies/system-demo.md)  
  *Held at the end of every iteration to demo the fully integrated solution delivered by all teams on the ART in a staging environment.*
* [**Inspect & Adapt (I&A) Workshop**](./ceremonies/inspect_&_adapt.md)  
  *Held at the end of every PI, consisting of the PI System Demo, quantitative measurement review (PPM), and a root-cause problem-solving workshop. A structured guide covering the 3 phases of the Inspect & Adapt event, core metrics, execution diagrams, and continuous improvement tools.*
---

## 3. Large Solution Level Events

Used in large enterprises where multiple ARTs and Suppliers collaborate to build massive, complex systems:

* **Pre- and Post-PI Planning for Large Solutions:** High-level leadership alignment across multiple ARTs to prepare capabilities, context, and dependencies prior to individual ART PI Planning sessions.
* **Solution Sync:** Periodic alignment event between Solution Management, Solution Train Engineer (STE), and Solution Architects across multiple trains.
* **Solution Demo:** Demonstration of integrated capabilities across all ARTs and Suppliers to enterprise executives and business owners.

---

## 4. Portfolio Level Events

Executive-level events that align strategy with execution and govern Lean Portfolios:

* **Strategic Portfolio Review:** Aligns portfolio investments, epic execution, and strategic themes with business strategy.
* **Portfolio Sync:** Regularly scheduled cadence for Lean Portfolio Management (LPM), Solution Portfolio Management, and Enterprise Architects to monitor Epic progress, budget allocations, and value stream health.
* **Participatory Budgeting:** Collaborative event where stakeholders and value stream leaders allocate funding across portfolio value streams.


SAFe Events Coaching Focus

**Backlog Refinement** (Primary)	Collaborative authoring, slicing stories, and enforcing the DoR quality gate.
**Iteration Planning**	Final verification that commitments are testable and unambiguous.
**Iteration Retrospective**	Inspecting quality escapes and refining BDD writing habits.
**PI Planning**	Establishing high-level acceptance criteria for large features and enablers.

## 📊 Estimation (Best Practices)

* [**Relative Sizing & Estimation Guide**](./framework/scrum/estimation.md)
  > Learn the 10 best practices for the team estimation, including **Planning Poker**, **WSJF**, and **T-Shirt Sizing**. This guide explains how to balance task complexity, developer experience, and codebase quality to create predictable delivery timelines.

##  Given_When_Then (PO * team)

[**Given-When-Then Guide**](./coaching/Given_When_Then.md)
 > Given-When-Then is the cornerstone syntax for Behavior-Driven Development (BDD) and Acceptance Test-Driven Development (ATDD). 
It bridges the gap between business intent and technical implementation.

##   Health Framework (PO)

[**Governance Health Framework**] (./coaching/PO.md)
 > This framework provides coaching techniques, best practices, and quantitative metrics for the 6 Core Pillars of Product Owner collaboration. It is designed to bridge the gap between technical delivery and business value, ensuring backlog health, clear goal alignment, and strict following to governance standards.

## Event-by-Event Coaching Guide

[**Maturtity adoption**] (./coaching/maturtity_adoption.md)
Coaching approach to maturity,  during standard SAFe events addresses the specific friction points of data engineering and analytics

## 5 Best Practice Techniques for Identifying Primary Root Causes
[**Root Causes Techniques**] (./coaching/root_cause_techniques.md)
>Phase 3 of the SAFe Inspect & Adapt (I&A) Problem-Solving Workshop.
Objective: Transition from broad brainstorming on a Fishbone diagram to pinpointing the single, highest-impact Primary Root Cause before developing solutions.
 

## 🤝  Working Agreement
*  [**Working Agreements Guidec(./Working-Agreements/working-agreement-TA.md/)
*  [**24-Hour Review SLA**](./Working-Agreements/24-h-review-SLA.md/)
*  [**Case study**](./Working-Agreements/case-study.md/)

[**DoR via DOD[**(./framework/scrum/DoR-DoD-governance-framework.md)
[**SAFe Cadence & Events Guide**](./framework/scrum/SAFe-cadence.md)

[**Event-by-Event Coaching Playbook to transform my team toward SAFe**](./framework/scrum/adoption-coaching.md)



## 🎯  Mission and Vision
*  [**Strategic Alignment**](./mission-vision.md/)

###  Team Workflows
* [**Workflows**](./team-workflows/)
*Onboarding and multicultural team norms.*


### Agile Ceremony Templates
* [**Templates**](./ceremony.templates.md)
This repository contains facilitation guides and templates for key Scrum ceremonies:
- 🕰️ Daily Stand-up
- 🎯 Sprint Planning
- 🔍 Sprint Review
- 🔄 Sprint Retrospective


## 📋 Ceremonies Preparation Checklist
  * [**Ceremonies Preparation Checklist**](./ceremony/ceremonies-prep-checklist.md/) - What to Bring & How to Prepare for Success.

## 📋 Coaching and Observation
  * [**Coaching and Observation Best Practices**](.//ceremony/Observation-and-coaching.md/)


 ### 📊 [Metrics & Data Visualization]
* [**Agile Metrics Dashboard**](./metrics.md)
*Power BI and ClickUp integration for real-time tracking.*


## 📂 Folder structure
- `/daily-standup` → Standup formats and facilitation tips
- `/sprint-planning` → Planning templates and estimation guides
- `/sprint-review` → Review tips
- `/sprint-retrospective` → Retro tips
...

## 📂Folder Path, Purpose
- `/strategy` → Transformation roadmap and maturity models.
- `/roles/product-owner` → Guides on WSJF, MoSCoW, and Backlog health."
- `/roles/scrum-master` → Facilitation guides and "Conflict Resolution" playbooks."
- `/roles/devops` → AWS Lambda CI/CD logic and Bitbucket automation.
- `/team-workflows` → Onboarding checklists and multicultural norms.
- `/metrics` → Screenshots/docs of Power BI + ClickUp integration.


## 📋 How to use
1. Browse a folder
2. Download templates or use Markdown guides
3. Customize to fit current needs
   

## 📬 Contact
Questions or suggestions? Reach me via email: [pmoksana.f@gmail.com](mailto:pmoksana.f@gmail.com)
Connect with me on [LinkedIn](https://linkedin.com/in/oksana-fadyeyeva)
