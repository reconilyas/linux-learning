# Linux Fundamentals, Users & Permissions

---

# What is Linux?

Linux is an **operating system kernel**. The kernel is the core component of the operating system and manages communication between hardware and software.

A **Linux distribution (distro)** is an operating system built around the Linux kernel with additional software, package managers, and desktop environments.

Examples:
- Ubuntu
- Debian
- Kali Linux
- Red Hat Enterprise Linux (RHEL)
- Fedora

Different distributions are designed for different purposes such as desktop use, servers, scientific computing, or penetration testing.

---

# Basic Linux Commands

## `ls`

Lists files and directories.

```bash
ls
```

Example:

```bash
ls /home
```

---

## `/`

Represents the **root directory** of the Linux filesystem.

Example:

```bash
ls /
```

---

## Command Options

Most Linux commands support options beginning with `-`.

Example:

```bash
ls -l
```

---

## `pwd`

Displays the current working directory.

```bash
pwd
```

---

## `whoami`

Displays the currently logged-in user.

```bash
whoami
```

---

## `man`

Displays the manual page for a command.

Example:

```bash
man cp
```

---

## Linux Prompt

Example:

```text
agent@agent-VirtualBox:~$
```

Meaning:

- **agent** → Current user
- **agent-VirtualBox** → Computer hostname
- **~** → Home directory
- **$** → Regular user

Root user prompt:

```text
#
```

---

## `env`

Displays environment variables.

```bash
env
```

---

# How Linux Executes Commands

The command execution flow is:

```text
Terminal
      ↓
Shell
      ↓
Kernel
      ↓
Hardware
      ↓
Result returned to the Terminal
```

- **Terminal** → User interface
- **Shell** → Interprets commands
- **Kernel** → Executes system operations

---

# File Management

## Redirect Error Output

Save error messages to a file.

```bash
ls /root 2>> errors.txt
```

---

## `rm`

Delete a file.

```bash
rm file.txt
```

---

## `cp`

Copy files.

```bash
cp source.txt destination.txt
```

---

## `history`

Displays previously executed commands.

```bash
history
```

---

## `!`

Execute a command from history.

Example:

```bash
!cp
```

Executes the most recent command beginning with `cp`.

---

# Users

## Display User Accounts

```bash
cat /etc/passwd
```

---

## Create a User

```bash
sudo adduser username
```

The new user receives:
- Home directory
- Password
- Default shell

---

## Usermod Help

```bash
sudo usermod --help
```

---

## Password Information

```bash
sudo cat /etc/shadow
```

Displays encrypted password information.

Documentation:

```bash
man shadow
```

---

## Display User Information

```bash
id username
```

Shows:
- UID
- GID
- Groups

---

## Delete a User

```bash
sudo userdel username
```

Delete user and home directory:

```bash
sudo userdel -r username
```

---

## Change User Information

```bash
sudo chage username
```

Used to manage password aging.

---

## Find Files Owned by a User

```bash
find / -user username
```

---

# Groups

## Create a Group

```bash
sudo groupadd groupname
```

---

## Group Management Help

```bash
sudo gpasswd --help
```

---

# Hidden Files

Display hidden files.

```bash
ls -a
```

---

# Linux File Permissions

Example:

```text
drwxr-xr-x 2 agent agent 4096 May 23 18:56 Desktop
```

Explanation:

| Field | Meaning |
|--------|---------|
| d | Directory |
| rwx | Owner permissions |
| r-x | Group permissions |
| r-x | Others permissions |
| agent | Owner |
| agent | Group |
| 4096 | File size (bytes) |
| May 23 18:56 | Last modification date |
| Desktop | File or directory name |

---

# Permission Types

| Symbol | Permission |
|---------|------------|
| r | Read |
| w | Write |
| x | Execute |

---

# Create a Directory

```bash
mkdir directory_name
```

---

# Change Permissions

Add permission:

```bash
chmod +x file.txt
```

Remove permission:

```bash
chmod -x file.txt
```

---

# Numeric Permissions

Permission values:

| Value | Permission |
|-------|------------|
| 4 | Read |
| 2 | Write |
| 1 | Execute |

Examples:

| Number | Permission |
|--------|------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

Example:

```bash
chmod 750 file.txt
```

Meaning:

- Owner → 7 (rwx)
- Group → 5 (r-x)
- Others → 0 (---)

---

# Symbolic Permissions

Examples:

```bash
chmod u-x file.txt
```

Remove execute permission from the owner.

```bash
chmod ug-x file.txt
```

Remove execute permission from owner and group.

```bash
chmod ugo-x file.txt
```

Remove execute permission from everyone.

Symbols:

- `u` → User (owner)
- `g` → Group
- `o` → Others
- `a` → All users

---

# Change Ownership

Change file owner:

```bash
sudo chown owner file.txt
```

Change owner and group:

```bash
sudo chown owner:group file.txt
```

---

## 🧠 Summary

Linux is built around the kernel, while distributions provide complete operating systems for different use cases. Understanding basic commands, users, groups, permissions, and ownership is essential for Linux administration, security, and system management.




