# Week 5 – Advanced Security Controls and Monitoring Automation

## 1. Overview

This week focuses on strengthening the security posture of the Ubuntu Server by implementing
advanced operating system security controls and introducing automation for both security
validation and system monitoring. The activities in this phase demonstrate defence-in-depth
principles and standard system administration practices.

All configuration tasks were performed remotely from a Windows workstation using SSH, reflecting
real-world server administration workflows.

---

## 2. Mandatory Access Control (AppArmor)

AppArmor provides Mandatory Access Control (MAC) by enforcing security profiles that restrict how
applications interact with system resources. Although AppArmor is enabled by default on Ubuntu
Server, profiles are not always actively enforced.

The status of AppArmor was verified using:
<img width="940" height="743" alt="image" src="https://github.com/user-attachments/assets/5162243a-eecc-4587-86b2-d867cfbed9d2" />

```bash
sudo aa-status
To demonstrate active enforcement, an existing profile was transitioned into enforce mode:
sudo aa-enforce tcpdump
<img width="940" height="219" alt="image" src="https://github.com/user-attachments/assets/326469b4-5b76-4c52-bac6-e28534931772" />

```
## 3. Automatic Security Updates


Automatic security updates were enabled to ensure that critical patches are applied promptly,
reducing exposure to known vulnerabilities. Ubuntu’s unattended-upgrades mechanism was used
to automate this process.

The feature was installed and configured using:
<img width="940" height="715" alt="image" src="https://github.com/user-attachments/assets/f168e7eb-5cd5-4006-9947-55da7ad2d5e9" />
<img width="940" height="563" alt="image" src="https://github.com/user-attachments/assets/fe019d8e-7a77-4cb3-bea5-b2566fe74c98" />


```sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

The unattended-upgrades service was then verified to be running:

```sudo systemctl status unattended-upgrades```


This confirmed that the system was configured to automatically download and install security
updates.


## 4. Intrusion Prevention (fail2ban)

fail2ban was implemented to protect the SSH service from brute-force authentication attacks.
The tool monitors authentication logs and temporarily blocks IP addresses that demonstrate
malicious behaviour.

fail2ban was installed, enabled, and started using:

```sudo apt install fail2ban
sudo systemctl enable fail2ban
sudo systemctl start fail2ban```
```
<img width="940" height="729" alt="image" src="https://github.com/user-attachments/assets/ada39fd1-1b0c-4e80-a794-ce6ef5de10f2" />
<img width="940" height="732" alt="image" src="https://github.com/user-attachments/assets/e8a3843c-fdea-45a0-b6a9-73f5499b6dd2" />


The service status was checked to confirm that fail2ban was operational:

sudo systemctl status fail2ban


The SSH jail was also verified to ensure that SSH login attempts were actively monitored:

sudo fail2ban-client status sshd



## 5. Security Baseline Automation Script

To automate verification of the server’s security configuration, a security baseline script
(security-baseline.sh) was created. The script performs read-only checks to confirm the status
of key security controls.

The script verifies:

AppArmor enforcement status

SSH root login configuration

SSH password authentication configuration

Firewall status

fail2ban service status

Because several of these checks require elevated privileges, the script was executed using
sudo:

sudo ./security-baseline.sh

<img width="940" height="510" alt="image" src="https://github.com/user-attachments/assets/dcd89310-ee00-41d8-9e02-06b232bd263b" />

The output confirmed that all security controls were configured correctly and enforcing as
intended.

## 6. System Monitoring Automation Script

A lightweight monitoring script (monitor-server.sh) was developed to collect real-time system
metrics. This script provides a repeatable snapshot of system performance and supports later
performance analysis.

The monitoring script reports:

System uptime

CPU load averages

Memory usage

Disk utilisation

Top CPU-consuming processes

The script was executed without elevated privileges:

./monitor-server.sh
<img width="940" height="508" alt="image" src="https://github.com/user-attachments/assets/d22e523e-1367-4299-887c-733edb8e6e46" />


The resulting output provides a clear overview of current system performance.



 ## 7. Reflection

This phase demonstrated the value of layered security controls within an operating system
environment. Mandatory Access Control, automated patching, and intrusion prevention address
different threat vectors and collectively enhance system resilience.

Automation was used to standardise both security verification and performance monitoring,
reducing manual effort and the potential for configuration errors. Troubleshooting connectivity
and firewall issues reinforced the importance of validating network state and access controls
when hardening a system.

The completed configuration provides a secure and stable foundation for performance testing
and analysis in the next phase.
