## Introduction

This week focused on configuring secure remote access to a Linux server environment. The practical tasks involved establishing SSH connectivity from a Windows workstation, applying hardening measures to reduce attack surface, and implementing firewall rules to control inbound traffic. These activities demonstrate how operating system security, networking, and administration intersect in real-world system management.

### SSH Access Verification

Remote administration was verified by successfully connecting to the server via SSH
from the Windows workstation using key-based authentication


![SSH login from Windows PowerShell](images/week4-ssh-login.png)
### SSH Hardening Configuration

The SSH daemon was hardened by disabling root login and password-based authentication,
while enforcing public key authentication. These changes reduce the risk of brute-force
attacks and unauthorised administrative access.

![Hardened sshd_config file](images/week4-sshd-config.png)
### Firewall Configuration

A firewall was configured using UFW to deny all unsolicited inbound traffic while
explicitly allowing SSH access. This limits network exposure while maintaining
remote administrative connectivity. The firewall ruleset was verified using:
bash
sudo ufw status verbose


![UFW firewall status](images/week4-ufw.png)
The server’s IP address was identified using the `ip addr` command to enable SSH access
from the workstation.
## Reflection

This week highlighted the importance of securing remote administrative access before exposing services to a network. Implementing SSH hardening and firewall rules reinforced how small configuration changes can significantly reduce attack surface while maintaining usability. Troubleshooting connectivity issues also emphasised the need for careful validation when applying security controls, as misconfiguration can directly impact system availability.
