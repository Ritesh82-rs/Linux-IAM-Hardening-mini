 
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
- **Users**: `amit-admin`, `amit1-dev`, `amit2-dev` , `amit-auditor`
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

## Audit Rules

**Monitor critical IAM files**  \
**-w /etc/sudoers -p wa -k sudoers_changes** \
**-w /etc/passwd -p wa -k userdb_changes**  \
**-w /etc/shadow -p wa -k userdb_changes**  

## 📊 Sample Findings & Remediation
**1. Finding: World-readable Backup Files**
- Risk: Sensitive user data exposure
- Fix: sudo chmod 600 /etc/*.backup
- Evidence:
   Before: -rw-r--r--  \
                   After: -rw-------

**2. Finding: Insecure Home Directory**
- Risk: Unauthorized access to user data
- Fix: sudo chmod 700 /home/username
- Evidence:
   Before: drwxr-xr-x  \
                 After: drwx------

**3. Finding: World-writable Log Directory**
- Risk: Log tampering or privilege escalation
- Fix: sudo chmod 755 /var/log/directory
- Evidence:
   Before: drwxrwxrwx \
                 After: drwxr-xr-x

## 🎓 Learning Outcomes
  **Technical Skills**

- Linux user and group management
- Sudoers file configuration and security
- POSIX permissions and ACLs
- Auditd configuration and monitoring
- Security vulnerability assessment
- System hardening techniques

## 🙏 Acknowledgments
- Ubuntu Security Team
- Linux Audit Framework

<div align="center">
</div> 



























