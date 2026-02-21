# Active Directory Simulation – HyperTech Solutions

## 📌 Project Overview

This project demonstrates the deployment and configuration of a Windows Server Domain Controller (Active Directory) for a simulated multi-branch enterprise called **HyperTech Solutions**.

The lab simulates centralized identity and access management across multiple locations using Windows Server 2022 and Active Directory Domain Services (AD DS).

The implementation includes:

- Domain Controller deployment
- DNS configuration
- Multi-location Organizational Unit (OU) design
- User and security group creation
- Group Policy Object (GPO) enforcement
- Enterprise security hardening
- Policy validation and testing

---

## 🏢 Company Structure

HyperTech Solutions is a multi-branch technology-driven enterprise operating across three Canadian locations:

### 📍 Toronto (Headquarters)
- IT Department
- HR Department

### 📍 Montreal Branch
- Sales
- Audit Department

### 📍 Halifax Branch
- Production Department
- Marketing Department

All branches are centrally managed using Active Directory to enforce security policies, manage users, and control access across the organization.

---

## 🎯 Project Objectives

The objectives of this simulation were to:

- Deploy Windows Server 2022 as a Domain Controller
- Configure Active Directory Domain Services (AD DS)
- Design structured OUs based on location and department
- Implement role-based access control using security groups
- Enforce password and account lockout policies
- Restrict system-level tools (CMD, PowerShell, Control Panel)
- Configure DNS for domain communication
- Validate policy enforcement using `gpupdate /force`

---

## 🌐 Network Design

```
🌐 Internet
│
│
┌────────────────┐
│ Router │
│ Gateway: │
│ 10.0.2.1 │
└────────────────┘
│
│
┌────────────────┐
│ Switch │
└────────────────┘
│
┌───────────────────────┼────────────────────────┐
│ │ │
┌────────────────┐ ┌────────────────┐ ┌────────────────┐
│ HyperTech │ │ Client PC 1 │ │ Client PC 2 │
│ (Domain Ctrl) │ │ Toronto User │ │ Montreal User │
│ 10.0.2.15 │ │ │ │ │
└────────────────┘ └────────────────┘ └────────────────┘
│
┌────────────────┐
│ Client PC 3 │
│ Halifax User │
└────────────────┘
```

### IP Configuration

- **Domain Name:** HyperTechai.com
- **Server Name:** HyperTech
- **Server Static IP:** 10.0.2.15
- **Gateway:** 10.0.2.1

All client machines were configured to use the Domain Controller as their primary DNS server to enable domain authentication.

---

## 🏗️ Domain Configuration

- Installed Active Directory Domain Services (AD DS)
- Promoted server to Domain Controller
- Created domain: **HyperTechai.com**
- Configured DNS services
- Verified domain login using `HyperTechai\Administrator`

---

## 🗂️ Organizational Unit (OU) Design

The OU structure reflects both geographic location and departmental separation:
HyperTechai.com

```
HyperTechai.com
│
├── Toronto
│ ├── IT
│ │ └── john.IT
│ │
│ └── HR
│ └── patricia.HR
│
├── Montreal
│ ├── Audit
│ │ └── christine.Audit
│ │
│ └── Sales
│ └── ashafa.Sales
│
└── Halifax
├── Marketing
│ └── mickie.Marketing
│
└── Production
└── bryan.Prod
```

This structure allows:

- Targeted GPO enforcement1
- Department-level access control
- Administrative delegation
- Scalable enterprise design

---

## 👥 Users & Security Groups

For each department:

- Security groups were created
- Individual user accounts were created
- Users were assigned to department-specific groups
- Access control was applied using group membership

This follows a role-based access control (RBAC) model.

---

## 🔐 Group Policy Objects (GPO)

The following security policies were implemented:

### 🔑 Password Policy
- Enforced password complexity
- Minimum password length requirement

### 🚫 Account Lockout Policy
- Lockout threshold: 3 failed login attempts
- Mitigates brute-force attacks

### 🛑 System Restrictions
- Disabled Command Prompt
- Blocked PowerShell access
- Restricted Control Panel access

### 📌 Deployment
- GPOs linked to appropriate Organizational Units
- Policies applied using `gpupdate /force`
- Enforcement validated on client systems

---

## 📸 Screenshots

Screenshots documenting the full implementation process are available in:

- `screenshots/` folder
- `screenshots.md` file

Key implementation stages captured:

- VM grouping
- AD DS installation
- Domain Controller promotion
- OU structure creation
- User & group creation
- DNS configuration
- GPO linking
- Policy enforcement validation

---

## ✅ Key Takeaways

- Successfully deployed and configured a multi-branch Active Directory environment
- Implemented structured OU design based on geography and department
- Applied enterprise-level security hardening policies
- Demonstrated centralized identity and access management
- Validated policy enforcement in a simulated corporate environment

---

## 🧠 Skills Demonstrated

- Active Directory Administration
- Windows Server 2022
- DNS Configuration
- Organizational Unit Design
- Group Policy Management
- Role-Based Access Control (RBAC)
- Enterprise Security Hardening
- Network Configuration
