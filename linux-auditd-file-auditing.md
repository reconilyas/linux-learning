# Linux Auditd (File Auditing)

---

# Auditd

Auditd (Linux Audit Daemon) is a security auditing framework used to monitor and record system events.

It helps administrators:
- Monitor access to files and directories
- Track who accessed a file
- Record when a file was accessed
- Log what actions were performed
- Detect unauthorized activity

---

# Display Current Audit Rules

List all active audit rules.

```bash
sudo auditctl -l
```

---

# Create an Audit Rule

Monitor a specific file or directory.

Syntax:

```bash
sudo auditctl -w <path_to_file> -p <permissions> -k <key_name>
```

Example:

```bash
sudo auditctl -w /etc/passwd -p wa -k passwd_monitor
```

Where:

- `-w` → Watch the specified file or directory
- `-p` → Permissions to monitor
- `-k` → Assign a searchable key name

---

# Permission Options

| Option | Description |
|---------|-------------|
| `r` | Read |
| `w` | Write |
| `x` | Execute |
| `a` | Attribute changes (permissions, ownership, timestamps) |

Example:

```bash
-p rw
```

Monitors both read and write operations.

---

# Audit Log

Audit events are stored in:

```text
/var/log/audit/audit.log
```

Whenever a monitored rule is triggered, an event is recorded in this log.

---

# Search Audit Logs

Use `ausearch` to search audit events by key.

Syntax:

```bash
sudo ausearch -i -k <key_name>
```

Example:

```bash
sudo ausearch -i -k passwd_monitor
```

Options:

- `-i` → Interpret numeric values into human-readable output.
- `-k` → Search using the rule's key.

---

## 🧠 Summary

Auditd is a powerful Linux security tool used to monitor system activity and file access. By creating audit rules with `auditctl` and reviewing logs using `ausearch`, administrators can detect unauthorized access, investigate security incidents, and maintain accountability across the system.
 


