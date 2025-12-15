
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

---

## 4. Performance Testing Plan

Performance testing is planned to evaluate how the operating system behaves under different workloads and how security controls influence system efficiency.

### Metrics to Be Collected
- CPU utilisation
- Memory usage
- Disk I/O activity
- Network throughput and latency
- Service response times (where applicable)

### Testing Phases
1. **Baseline Testing** – System idle, minimal services running
2. **Load Testing** – Application-specific workloads applied
3. **Bottleneck Identification** – Analysis of resource constraints
4. **Optimisation Testing** – Performance improvements applied and re-tested

Quantitative measurements will be captured to support comparative analysis.

---

## 5. Remote Monitoring Methodology

All monitoring will be conducted **remotely via SSH** from the Windows workstation, reinforcing command-line proficiency and professional remote administration practices.

### Planned Monitoring Tools
- `top` / `htop` – CPU and memory usage
- `vmstat` – Memory and process statistics
- `iostat` – Disk I/O performance
- `df` – Disk utilisation
- `ping` / `iperf` – Network latency and throughput

Metrics will be collected using a custom monitoring script executed from the workstation, which connects to the server via SSH and logs results for later analysis.

---

## 6. Testing Environment Considerations

All testing will occur within an isolated VirtualBox environment to ensure ethical and safe operation. Network scanning and security testing tools will only be used against systems owned and controlled by the author.

This controlled environment allows realistic experimentation without exposing external systems to risk.

---

## 7. Week 2 Reflection

This phase highlighted the importance of **planning before implementation** in operating system security. Defining threats and mitigations early ensures that security controls are purposeful and measurable, rather than ad hoc.

The performance testing plan reinforces the understanding that security and performance are interconnected; additional controls can introduce overhead, and their impact must be quantified. Planning remote monitoring further emphasises the role of automation and scripting in professional system administration.

By establishing a clear security baseline and testing methodology, this phase provides a structured foundation for secure system deployment and meaningful performance evaluation in later weeks.
