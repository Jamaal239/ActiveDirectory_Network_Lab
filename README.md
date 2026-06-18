# Active Directory Network Lab & Help Desk Simulation

## 📌 Project Overview
This lab demonstrates enterprise-level IT support, system administration, and network troubleshooting techniques within a Windows Server and Windows 11 Client virtual environment.

## 🛠️ Technologies Used
* **Hypervisor:** Oracle VirtualBox
* **Server OS:** Windows Server 2025 Standard Evaluation (`DC-01`)
* **Client OS:** Windows 11 Enterprise Evaluation (`W11-CLIENT-01`)
* **Core Services:** Active Directory Domain Services (AD DS), DNS, Print Spooler, Windows Credential Manager

---

## 🚀 Tasks Completed

### Task 1: Enterprise Printer Sharing & Active Directory Publishing
* Configured a shared local network printer (`Dept_Printer_HP`) using generic drivers on the domain controller.
* Enabled Active Directory directory publishing to allow domain users to easily locate network printing resources.

<img width="998" height="1032" alt="01_Server_Share_Permissions" src="https://github.com/user-attachments/assets/f5c9ce7a-6ec7-4c22-8657-c52e009ddebf" />

*Figure 1: Navigating the Windows Server Add Printer Wizard to set up manual hardware settings.*

### Task 2: Troubleshooting Network Share Pathing
* Successfully mapped a network directory (`\\DC-01\Company_Share`) to user profile `mvance`.
* Diagnosed and resolved standard short-name resolution conflicts by implementing fully qualified domain name (FQDN) mapping.

<img width="998" height="1032" alt="02_Server_Printer_Publishing" src="https://github.com/user-attachments/assets/b776871f-ef5e-49d8-bd23-9a45e5b1874a" />

*Figure 2: Configuring Active Directory Printer Sharing settings for the department's printer queue (`Dept_Printer_HP`).*
---

### Task 3: Resolving Stale User Credentials
* Managed cached network credentials via Windows Credential Manager to address authentication issues resulting from user password updates.

<img width="1091" height="914" alt="03_Client_Credential_Manager" src="https://github.com/user-attachments/assets/13b26845-cd84-4d07-aeb8-91f24b1e2e15" />

*Figure 3: Inspecting and clearing cached domain credentials for user `mvance` inside Windows Credential Manager.*

---

### Task 4: Clearing Frozen Print Queues
* Administered the local print subsystem using the command line interface to stop and start the Print Spooler service (`net stop spooler` / `net start spooler`).
* Inspected and cleared the system print directory (`C:\Windows\System32\spool\PRINTERS`) to clear stuck jobs.

<img width="998" height="1032" alt="04_Client_Print_Spooler_Reset" src="https://github.com/user-attachments/assets/b0d1ffea-24eb-4108-916a-9b60cc571394" />

*Figure 4: Utilizing administrative CLI commands to systematically cycle the local Print Spooler subsystem service.*

---

### Task 5: Network Stack Flush
* Maintained local client network health by clearing local DNS caches (`ipconfig /flushdns`) and resetting active interface adapter bounds.

<img width="998" height="1032" alt="05_Client_Network_Flush" src="https://github.com/user-attachments/assets/69b1875d-1be1-469b-911c-9ae3d7d7c575" />

*Figure 5: Successfully flushing the local client DNS resolver cache via the administrative command line interface.*

---

## 🎓 Summary of Real-World Technical Outcomes

### 🧠 What I Learned
* **Active Directory Resource Publishing:** Learned how enterprise resources like printers are registered and discovered globally within an AD DS environment rather than mapped manually per seat.
* **Windows Subsystem Architecture:** Gained deep insights into how Windows handles printer jobs dynamically via `.SPL` and `.SHD` format tracking files in system folders.
* **Credential Token Caching:** Developed an understanding of how local client operating systems temporarily retain Windows Generic and Internet credentials to support single sign-on (SSO) experiences.

### 🛠️ What I Fixed
* **DNS/Short-Name Share Resolution:** Resolved a "Windows cannot access" error during drive mapping by leveraging FQDN paths and validating structural share configuration properties on the server side.
* **Stale Domain Tokens:** Fixed broken, permission-denied drive mapping events by clearing expired password caches within the client's local security database.
* **Frozen Print Services:** Repaired a locked local hardware queue by utilizing elevated system commands to cycle service dependencies and wipe out corrupt layout documents.

### 💼 Corporate & Day-to-Day Application
* **Tier 1 / Tier 2 Help Desk Alignment:** The specific tasks completed in this simulation represent the highest volume tickets handled by enterprise service desks daily (e.g., locked print arrays, missing target folders, and broken connections post-password changes).
* **Minimizing Enterprise Downtime:** Standardizing workflow scripts to flush DNS configurations or clear local system folders allows technicians to resolve client disruptions in minutes without needing to re-image operating systems or execute unnecessary hardware reboots.
* **Least Privilege Best Practices:** Managing shares, print queues, and directory structures directly mimics the strict data-governance standards required in highly compliant corporate settings.
