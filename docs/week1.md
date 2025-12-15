# Week 1 – System Planning and Distribution Selection

## 1. System Architecture Overview

This coursework adopts a dual-system architecture consisting of a Linux server system and a separate administrative workstation. The server runs a headless Linux distribution without a graphical interface, while all administration is performed remotely via SSH from a Windows workstation.

This approach mirrors professional data-centre and cloud environments, where remote administration is standard practice and direct local access is avoided to minimise attack surface.

---

## 2. System Architecture Diagram (Description)

The system consists of a Windows workstation acting as the administrative client and an Ubuntu Server virtual machine running headless within VirtualBox. Communication occurs exclusively via SSH over a private virtual network.


Network isolation ensures that security testing can be conducted safely without exposing the server externally.
Windows Workstation
    |
    |  SSH (TCP 22)
    |
Ubuntu Server (Headless)

## 3. Linux Distribution Selection and Justification

### Selected Distribution
Ubuntu Server 22.04 LTS

### Comparison with Debian

| Criterion | Ubuntu Server 22.04 LTS | Debian Stable |
|----------|-------------------------|---------------|
| Release model | Long-Term Support | Stable |
| Security tooling | AppArmor enabled by default | Limited by default |
| Documentation | Extensive and accessible | Highly technical |
| Industry adoption | Very high | Moderate |

### Justification

Ubuntu Server 22.04 LTS was selected due to its balance of long-term stability, security features, and comprehensive documentation. While Debian Stable offers exceptional reliability, Ubuntu provides stronger support for mandatory access control and security tooling required later in the coursework.

This decision reflects a conscious trade-off between maximum stability and operational efficiency.

---

## 4. Workstation Selection Justification

The workstation system is a Windows PC equipped with an SSH client.

### Rationale
- Built-in OpenSSH support via PowerShell
- Reflects common enterprise administration environments
- Enables clear separation between administrative client and server

All server configuration will be performed remotely from this workstation.

---

## 5. Network Configuration Plan

The server virtual machine will be configured using VirtualBox networking with NAT for internet access and a host-only adapter for secure workstation communication. This configuration enables package installation while maintaining network isolation for security testing.

---

## 6. Planned System Specification Documentation

The following commands will be used via SSH to document system specifications once the server is installed:

```bash
uname -a
lsb_release -a
free -h
df -h
ip addr

Week 1 Reflection

This phase demonstrated the importance of early operating system planning decisions. Deploying a headless server reduces resource overhead and limits unnecessary services, improving both performance and security.

Separating the workstation from the server enforces disciplined remote administration practices and aligns with real-world system management approaches. Selecting Ubuntu Server over Debian illustrates a practical trade-off between stability and tooling support.
