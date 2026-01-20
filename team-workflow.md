# Agile Transformation Playbook
### A Strategic Guide for Scaled Agile & Digital Transformation

[⬅️ Back to Main Guide](../../)
---


# ⚙️ OUR Team Workflows: Scaling Excellence

> **Our operational blueprint for managing brand expansion, platform redesigns, and automated cloud delivery.**

This document outlines the standard workflows for the OUR Engineering and Product teams. Our goal is to maintain a high "Definition of Done" while scaling our mobile and web presence.

---

## 🚀 1. Brand Onboarding & Campaigns
As we welcome **New Brands** to the OUR ecosystem, we follow a standardized integration flow to ensure data integrity and consistent UX.

* **Discovery Phase:** Technical audit of the brand's product data and campaign requirements.
* **Asset Pipeline:** Standardized ingestion of brand assets into our S3/CloudFront CDN.
* **Campaign Launch:** A/B testing configurations must be validated in staging before the brand goes live in the app.

## 🎨 2. Redesign Phase Protocols
We are currently in a **Redesign Phase**. To prevent breaking the user experience during this transition:

* **Feature Flagging:** All new UI/UX components must be hidden behind feature flags (e.g., LaunchDarkly or custom AWS AppConfig).
* **The "Double-Run" Strategy:** Support for legacy styles and new redesign components must coexist in the codebase until the final cut-over.
* **Design System Sync:** Every UI change must reference our Figma Design System tokens to prevent "CSS Drift."

---

## 📱 3. Product Testing & Automation
We don't just "test"—we automate to ensure quality at the speed of deployment.

### Mobile & Web Automation
* **Web:** End-to-end (E2E) testing using Playwright/Cypress for core OUR portal flows.
* **Mobile:** Appium or Detox suites for critical path testing (Scanning, Rewards, Wallet) on iOS and Android.
* **Visual Regression:** Automated snapshots during the **Redesign Phase** to catch unintended UI shifts.

### Integration Testing
* **Lambda Testing:** All AWS Lambda functions must have unit tests with >80% coverage and local integration tests using LocalStack or SAM.

---

## ☁️ 4. CI/CD & Infrastructure (AWS Lambda)
Our infrastructure is built for scale using a Serverless-first approach on **AWS Lambda**.

### The Deployment Pipeline
1.  **Commit:** Developer pushes code to a feature branch.
2.  **Lint & Unit Test:** Triggered via GitHub Actions (ESLint, Jest, etc.).
3.  **SAM Build:** The AWS Serverless Application Model (SAM) packages the Lambda functions.
4.  **Staging Deploy:** Automatic deployment to the `Staging` environment via Lambda Aliases.
5.  **E2E Validation:** Automation suites run against the newly deployed Lambda endpoints.
6.  **Production Release:** Manual "Promote to Prod" after smoke tests pass.

### Performance Standards
* **Cold Start Monitoring:** We optimize Lambda layers and memory allocation to keep the mobile app responsive.
* **Log Hygiene:** All Lambdas must stream structured JSON logs to CloudWatch for easy debugging.

---

## 📈 5. Maintenance & On-Call
* **Error Tracking:** Sentry/Datadog alerts for any 5XX errors on Lambda.
* **Post-Mortems:** If a Campaign launch fails or a Redesign breaks a flow, we conduct a "Blameless Post-Mortem" to update these workflows.

---

## 🔗 Related Resources
* [**Working Agreements: Our Commitment](./commitment.md)
* [**Mission & Vision**](../mission-vision.md)
* [**AWS Lambda Architecture Docs**](../tech-stack/aws-lambda.md)

---
[Return to Agile Center of Excellence Home](../README.md)
