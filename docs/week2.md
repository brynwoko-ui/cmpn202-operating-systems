
# Week 2 – Security Planning and Testing Methodology

## 1. Security and Performance Planning Overview

This phase focuses on defining a **security baseline** and a **performance testing methodology** prior to implementation. Establishing these plans before configuring the system ensures that security controls are deliberate, measurable, and defensible, rather than reactive.

The planning process draws on operating system security principles, including least privilege, defence in depth, and attack surface minimisation, while also considering how security controls may impact system performance.

---

## 2. Threat Model

A threat model was developed to identify realistic risks applicable to a headless Linux server administered remotely.

### Identified Threats and Mitigations

| Threat | Description | Mitigation Strategy |
|------|------------|---------------------|
| Brute-force SSH attacks | Automated attempts to guess SSH credentials | Disable password authentication, enforce key-based SSH, deploy fail2ban |
| Unauthorised network access | Exposure of services to unintended hosts | Firewall rules allowing SSH only from the workstation IP |
| Privilege escalation | Compromie of root privileges through misconfiguration | Use of non-root administrative user and strict sudo controls |
| Misconfigured services | Unnecessary services increasing attack surface | Service audit and justification in later phases |

This threat model informs all subsequent security decisions and provides a reference point for later security auditing.

---

## 3. Security Configuration Checklist

The following checklist defines the **minimum security baseline** that must be achieved during implementation phases.

### SSH Security
- Disable password authentication
- Enforce key-based authentication
- Restrict SSH access to a single administrative user
- Limit SSH access to workstation IP

### Firewall Configuration
- Enable firewall by default
- Allow only required inbound traffic (SSH)
- Deny all other inbound connections

### User and Privilege Management
- Disable direct root login
- Create a non-root administrative user
- Restrict sudo privileges to essential commands

### Mandatory Access Control
- Enable and configure AppArmor
- Verify active profiles
- Monitor denied access attempts

### System Maintenance
- Enable automatic security updates
- Maintain minimal installed packages

### Intrusion Detection
- Deploy fail2ban to monitor SSH logs
- Automatically ban repeated failed login attempts

This checklist will later be validated automatically using a security baseline verification script.
