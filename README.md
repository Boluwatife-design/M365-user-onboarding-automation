# M365-user-onboarding-automation
Step by step process in automating onboarding in M365

# 🚀 Automated User Onboarding with Power Automate + Microsoft Entra ID

This project automates the entire user onboarding process using **Power Automate** and **Microsoft Entra ID (Azure AD)** — eliminating manual steps like account creation, group assignment, and license allocation.

---

## 📌 Overview

From a single trigger (e.g., SharePoint list, HR system, or form), this flow:

- Creates a new user in Entra ID  
- Assigns the user to the correct group  
- Automatically applies Microsoft 365 licenses via Group-Based Licensing  

✅ Zero manual intervention  
✅ Faster onboarding  
✅ Reduced errors  
✅ Easy to scale and audit  

---

## ⚙️ How It Works

### 1️⃣ Trigger: New User Data
- Source: SharePoint List / Form / HR System  
- Captures:
  - First Name
  - Last Name
  - Department
  - Job Role
  - Manager
  - Start Date
 

---

### 2️⃣ Create User in Entra ID
- Uses Power Automate action to:
  - Create user account  
  - Set attributes (Department, Job Title, etc.)  

---

### 3️⃣ Assign to Security Group
- Based on department or role  
- Example:
  - IT → IT-Security-Group  
  - HR → HR-Users-Group  

---

### 4️⃣ Automatic License Assignment
- Group-Based Licensing applies:
  - Microsoft 365 licenses  
- No need to assign licenses in the flow  

---

## 🧠 Architecture
