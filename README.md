# Active Directory Simulation – HyperTechAi Solutions

## 📌 Project Overview

This project demonstrates the deployment and configuration of a Windows Server Domain Controller (Active Directory) for a simulated multi-branch enterprise called **HyperTechAi Solutions**.

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

HyperTechAi Solutions is a multi-branch technology-driven enterprise operating across three Canadian locations:

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
- **Server Name:** HyperTechai
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

- Targeted GPO enforcement
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

Key implementation stages captured:

- [VM grouping](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/1_vm_grouping.png)
- [AD DS installation](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/2_ad_installation.png)
- [Domain Controller promotion](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/3_domaincontroller.png)
- [OU structure creation](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/4_OUs_creation.png)
- [Group creation](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/5_groups_creation.png)
- [User creation](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/6_Users_creation.png)
- [User login](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/6_Users_Pass_created.png)
- [DNS configuration](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/7_dns_change.png)
- [Password policy](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/8_password_policy.png)
- [Account lockout policy](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/9_account_lockout_policy.png)
- [GPO linking](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/10_gpo_link.png)
- [Access control panel](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/11_access_cp.png)
- [Cmd block](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/11_cmd_block.png)
- [Blocking powershell](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/12_Blocking_powershll.png)
- [Gpupdate force](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/14_gp_update_force.png)
- [Control panel disabled](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/15_Control_Panel_disabled.png)
- [Prohibit access control panel](https://github.com/Yem-Tech/Active-Directory-Simulation-HyperTech-Solutions/blob/main/Screenshots/15_prohibit_access_cp.png)

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
