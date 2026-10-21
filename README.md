# Azure Cloud Identity, Access Control & Governance Security Lab

## 📌 Project Overview
This project demonstrates end-to-end cloud identity management, access control, and security governance in Microsoft Azure. It showcases enterprise security best practices, including role-based access control (RBAC), multi-factor authentication (MFA) enforcement, policy-driven regional compliance, and offboarding workflows under Zero Trust and Least Privilege principles.

## 🛠️ Key Implementation Modules & Verification

### 1. Identity & Directory Structure
* Created test accounts with specific department metadata, usage locations, and manager hierarchies.
* Structured role-based **Security Groups** (`SG-Finance`) for scalable access control.

### 2. Multi-Factor Authentication (MFA) & Conditional Security
* Configured authentication methods and verified MFA onboarding workflows.

### 3. Azure RBAC & Access Isolation (Positive / Negative Testing)
* **Access Assignment**: Granted `Reader` to `SG-Finance` at the resource level (`kellyseclabproject`).
* **Positive Test**: Verified that authorized account (`finance_staff`) can seamlessly read the data plane (Storage browser/Containers).
* **Negative Test**: Verified that non-finance personnel (`hr_staff`) are completely restricted from viewing or accessing the storage account, enforcing the **Principle of Least Privilege (PoLP)**.

### 4. Enterprise Governance with Azure Policy
* Implemented the **Allowed Locations** policy restricted to Canadian data centers (`Canada Central` & `Canada East`) for Data Residency compliance.
* Verified policy enforcement through negative validation (`Request disallowed by policy` upon attempting deployment in non-compliant regions).

### 5. Identity Lifecycle & Offboarding Safeguards
* Simulated emergency offboarding for departed personnel by toggling **Account Enabled = No** (Block Sign-in).
* Verified first-line authentication boundary enforcement (Attempted login resulted in `Your account has been disabled`).

## Tools Used
* MS Entra ID
* MS Azure
