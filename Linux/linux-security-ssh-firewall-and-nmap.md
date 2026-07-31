# Linux Security, SSH, Firewall & Nmap

---

# Sudo Configuration

## View the sudo Group

Display users who belong to the `sudo` group:

```bash
grep sudo /etc/group
```

These users are typically allowed to execute commands with administrative privileges.

---

## Edit sudo Permissions

Use the `visudo` command to safely edit the sudoers file.

```bash
sudo visudo
```

> **Note:** Always use `visudo` instead of editing `/etc/sudoers` directly because it checks for syntax errors before saving.

---

# PAM (Pluggable Authentication Modules)

PAM is the Linux framework responsible for:

- Authentication
- Authorization
- Account management
- Session management
- Password management

PAM configuration files are located in:

```bash
ls /etc/pam.d/
```

Example:

```bash
ls /etc/pam.d/passwd
```

The `passwd` configuration controls password-changing policies.

---

# Display IP Address

Show the IP addresses assigned to your machine.

```bash
sudo ip addr show
```

or

```bash
ip a
```

---

# SSH (Secure Shell)

SSH provides secure remote access to another machine.

Unlike Telnet, SSH encrypts all communication between the client and the server.

---

## Requirements

The remote machine must have an SSH server installed and running.

Install OpenSSH Server:

```bash
sudo apt install openssh-server
```

---

## Connect to a Remote Machine

Connect using the current username:

```bash
ssh <IP_ADDRESS>
```

Connect as a specific user:

```bash
ssh username@<IP_ADDRESS>
```

---

## SSH Configuration

The SSH server configuration file is:

```bash
sudo vi /etc/ssh/sshd_config
```

This file controls settings such as:
- Port number
- Root login
- Password authentication
- Public key authentication

---

# SSH vs Telnet

| SSH | Telnet |
|------|--------|
| Encrypted communication | Unencrypted communication |
| Secure | Insecure |
| Default Port: 22 | Default Port: 23 |

---

# iptables Firewall

`iptables` is the traditional Linux firewall used to filter network traffic.

It operates at the Network Layer (Layer 3) and Transport Layer (Layer 4) by filtering packets based on IP addresses, protocols, and ports.

---

## Display Firewall Rules

```bash
sudo iptables -L
```

Displays the default chains:
- INPUT
- OUTPUT
- FORWARD

---

## Change the Default Policy

Example:

```bash
sudo iptables -P INPUT DROP
```

Common policies:
- ACCEPT
- DROP

---

## Add a Firewall Rule

Block TCP traffic coming from a specific source IP to a specific destination port:

```bash
sudo iptables -A INPUT -s <SOURCE_IP> -p tcp --dport <PORT> -j DROP
```

Example:

```bash
sudo iptables -A INPUT -s 192.168.1.50 -p tcp --dport 22 -j DROP
```

---

## Save Firewall Rules

```bash
sudo iptables-save > firewall.rules
```

---

## Restore Firewall Rules

```bash
sudo iptables-restore < firewall.rules
```

---

# Nmap

Nmap is a network scanning tool used to discover hosts and identify open ports and services.

---

## Install Nmap

```bash
sudo apt install nmap
```

---

## Basic Scan

Scan a target host:

```bash
nmap <IP_ADDRESS>
```

Example:

```bash
nmap 192.168.1.10
```

Nmap can identify:
- Open ports
- Running services
- Service versions
- Operating system (with additional options)

---

## 🧠 Summary

Linux security relies on proper privilege management, secure remote access with SSH, firewall configuration using `iptables`, and network reconnaissance tools such as Nmap. Understanding these components is essential for Linux administration and cybersecurity.
