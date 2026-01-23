# 🛡️ Data Project Risk Register

| Risk ID | Category | Description | Impact | Mitigation Strategy | Owner |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R-001** | **Compliance** | PII leakage during Silver-to-Gold transition. | **Critical** | Implemented Unity Catalog RBAC & dynamic masking. | Data PM |
| **R-002** | **Technical** | API Token Expiry (ClickUp/Azure). | **High** | Automated secret rotation in Azure Key Vault. | Data PM |
| **R-003** | **Governance** | Scope Creep (Stakeholder side-requests). | **Medium** | Backlog grooming to prioritize MVP for Comité. | Data PM |