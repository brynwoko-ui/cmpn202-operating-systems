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
