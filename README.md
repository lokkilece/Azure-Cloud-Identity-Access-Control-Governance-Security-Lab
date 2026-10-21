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

## Steps
### 1. Identity & Directory Structure
Created accounts in MS Entra ID - Set up `Job Title`, `Department`, `Manager` and `Usage Location` for restricting access from other locations & set up hierarchy structure

<img width="500" alt="螢幕擷取畫面 2026-10-21 141557" src="https://github.com/user-attachments/assets/ca2f72ee-ea9d-4c1b-a6ff-930c1f9e128a" />

After that, I set up Security Group for easier RBAC by dividing users into groups in Ms Entra ID - `Groups` - `Members`
<img width="500" alt="螢幕擷取畫面 2026-10-21 143014" src="https://github.com/user-attachments/assets/07389eee-1c45-4549-97b6-0275073950b1" />
<img width="500" alt="螢幕擷取畫面 2026-10-21 181615" src="https://github.com/user-attachments/assets/1b654ff7-0108-44ed-8fcc-a8974265743e" />

### 2. Multi-Factor Authentication (MFA) & Conditional Security
Since I do not have MS Entra ID P1/P2, Conditional Access is not available to me.
In order to make sure MFA, I enabled MS security defaults in `Tenant Properties`

<img width="500" alt="螢幕擷取畫面 2026-10-21 151300" src="https://github.com/user-attachments/assets/53ceb30c-1fba-4f82-b985-0884577a9b87" />

*Testing For MFA*

### 3. Azure RBAC & Access Isolation (Positive / Negative Testing)
Created a storage account based in Canada as well as added tags for better organization
<img width="500" alt="螢幕擷取畫面 2026-10-21 153001" src="https://github.com/user-attachments/assets/f8242558-a5e7-4309-9200-a571944edf13" />

Assigned `Reader` to `SG-Finance`

<img width="500" alt="螢幕擷取畫面 2026-10-21 165427" src="https://github.com/user-attachments/assets/651e10cf-eb5c-4a3e-9b31-33e33b719dc6" />

*Positive Testing in Finance Staff*

<img width="500" alt="螢幕擷取畫面 2026-10-21 165323" src="https://github.com/user-attachments/assets/f7c083c6-9578-48e9-936d-aa74eea4f7e0" />

*Negative Testing in HR Staff*

<img width="500" alt="螢幕擷取畫面 2026-10-21 163024" src="https://github.com/user-attachments/assets/fbcdd45d-fd66-4baf-b5ad-9ae2ae21bf0f" />

### 4. Enterprise Governance with Azure Policy
Implemented policy and allowing resources can be accessed in Canada to prevent unknown access from unknown locations

<img width="500" alt="螢幕擷取畫面 2026-10-21 170901" src="https://github.com/user-attachments/assets/ab88652b-bdfd-4b74-adaf-15412ebdae9b" />

*Testing for region restriction policy*

<img width="500" alt="螢幕擷取畫面 2026-10-21 171900" src="https://github.com/user-attachments/assets/821b5650-0bf5-4d8f-8e91-2d226c0b8451" />

### 5. Identity Lifecycle & Offboarding Safeguards
 Simulated emergency offboarding for departed personnel by disabling the user
 
 <img width="500" alt="螢幕擷取畫面 2026-10-21 172825" src="https://github.com/user-attachments/assets/6cfbcf00-288c-489c-9272-b207a4948cc7" />

 *Testing for the disabled user*

 <img width="500" alt="螢幕擷取畫面 2026-10-21 172904" src="https://github.com/user-attachments/assets/3a83f377-8700-4f40-9e2a-15106d808036" />

