 
# Linux IAM & Hardening (User, group, permissions)

A hands-on project demonstrating Identity & Access Management (IAM) and system hardening on Ubuntu Linux. Design secure user/group models, identify misconfigurations, and implement remediation strategies.

## 📋 Project Overview

This project provides a complete lifecycle for Linux IAM security:
- **Secure Baseline**: Design and implement least-privilege access controls
- **Vulnerability Assessment**: Identify deliberate misconfigurations in a lab environment
- **Remediation**: Fix security issues and harden the system
- **Documentation**: Produce security policies and checklists

## 🎯 Learning Objectives

After completing this lab, I will be able to:
- Design secure user and group structures following principle of least privilege
- Configure granular sudo access controls
- Implement proper file permissions and ACLs
- Set up auditing and monitoring for critical system files
- Identify and remediate common IAM misconfigurations
- Produce professional security documentation

## 🏗️ Lab Architecture

### Secure Baseline Environment
- **Ubuntu Server VM** - Primary lab environment
- **User Groups**: `admin`, `dev`, `auditor`
- **Users**: `ritesh-admin`, `ritesh1-dev`, `ritesh2-dev` , `ritesh-auditor`
- **Secure Sudo Rules**: Least-privilege commands per group
- **File Permissions**: Proper ownership and access controls

### Vulnerable Lab Components
- World-readable backup files (`/etc/passwd.backup`, `/etc/shadow.backup`)
- Insecure home directory permissions
- World-writable log directories
- Dangerous sudo rules (for demonstration)

### 🔍 Key Features
**1. User & Group Management**
   
- Role-based group structure (admin, dev, auditors)
- Secure user creation with proper primary groups
- Regular access reviews and audits

**2. Sudo Privilege Management**
   
- Least-privilege sudo rules
- Restricted command-specific access
- No unnecessary NOPASSWD directives

 **3. File System Security**

- Proper POSIX permissions for sensitive files
- Setgid bits for shared directories
- ACLs for granular access control

**4. Auditing & Monitoring**

- auditd configuration for critical files
- Real-time monitoring of /etc/sudoers, /etc/passwd, /etc/shadow
- Comprehensive logging and alerting

## 🛠️ Technical Components
  **Sudoers Configuration**
- **Admin** - Full system access
- %admin ALL=(ALL:ALL) ALL

- **Developers** - Application-specific commands only
                   **%dev ALL=(root) /usr/bin/systemctl restart nginx,   /usr/bin/systemctl status nginx**
- **Auditors** - No sudo access






















