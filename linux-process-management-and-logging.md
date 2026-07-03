# Linux Process Management & Logging

---

# Process Management

A **process** is a running instance of a program. Linux provides several commands to monitor, manage, and control processes.

---

## `ps`

Displays the processes running in the current shell.

Example:

```bash
ps
```

---

## `ps -l`

Displays processes with detailed information.

Example:

```bash
ps -l
```

Common fields:

| Field | Description |
|-------|-------------|
| UID | User ID that owns the process |
| PID | Process ID (unique identifier) |
| PPID | Parent Process ID |
| PRI | Process priority |
| NI | Nice value (priority adjustment) |
| TTY | Terminal associated with the process |
| TIME | CPU time used by the process |
| CMD | Command that started the process |

---

## `ps aux`

Displays all running processes with detailed information.

Example:

```bash
ps aux
```

This command is commonly used by system administrators to inspect system activity.

---

# Process States

| State | Meaning |
|-------|---------|
| R | Running or ready to run |
| S | Sleeping (waiting for an event) |
| T | Stopped |
| Z | Zombie (process has finished but still has an entry in the process table) |

---

## `pstree`

Displays all running processes in a tree structure, showing parent and child relationships.

Example:

```bash
pstree
```

---

# Process Signals

## `kill -l`

Lists all available signals that can be sent to a process.

Example:

```bash
kill -l
```

Common signals:

- SIGTERM (15) → Gracefully terminate a process
- SIGKILL (9) → Forcefully terminate a process
- SIGSTOP (19) → Pause a process
- SIGCONT (18) → Resume a stopped process

---

## `jobs -l`

Displays background jobs in the current shell along with their Process IDs (PID).

Example:

```bash
jobs -l
```

---

# Process Priority

Linux schedules processes based on priority.

---

## `nice`

Starts a new process with a specified priority.

Example:

```bash
nice -n -10 command
```

Lower nice values = Higher priority

Higher nice values = Lower priority

---

## `renice`

Changes the priority of an existing process.

Example:

```bash
sudo renice -20 -p 10041
```

Output:

```text
10041 (process ID) old priority 0, new priority -20
```

---

# Logging System

Linux stores system logs in:

```text
/var/log
```

To list log files:

```bash
ls /var/log
```

Log files contain information about:
- System events
- Errors
- Services
- Authentication
- Kernel messages
- Applications

---

## 🧠 Summary

Linux process management allows administrators to monitor, control, and prioritize running processes using commands such as `ps`, `pstree`, `kill`, `jobs`, `nice`, and `renice`. System logs stored in `/var/log` are essential for troubleshooting, monitoring, and security analysis.

  



