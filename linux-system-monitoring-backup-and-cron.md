# Linux System Monitoring, Cron & Backup

---

# System Monitoring

Linux provides several tools to monitor CPU, memory, disk usage, and overall system performance.

---

## `top`

Displays real-time information about running processes and system resource usage.

```bash
top
```

Shows:
- CPU usage
- Memory usage
- Running processes
- System load

---

## `vmstat`

Displays virtual memory and CPU statistics.

Example:

```bash
vmstat 1 3
```

Meaning:

- `1` → Refresh every second
- `3` → Display three reports

The **idle CPU percentage** is shown in the `id` column.

---

## `free`

Displays memory usage.

Example:

```bash
free -m
```

Option:

- `-m` → Display values in MB

---

## `df`

Displays disk usage.

Example:

```bash
df -h
```

Option:

- `-h` → Human-readable format

---

## `awk`

Used to extract specific columns from command output.

Example:

```bash
df -h | awk '{print $5}'
```

---

# Resource Monitoring Script

Example:

```bash
#!/bin/bash

LIMIT=90

CPU=$(vmstat 1 3 | tail -1 | awk '{print $15}')
CPU=$((100 - CPU))

echo "CPU Usage: $CPU%"

TOTAL_RAM=$(free -m | awk '/Mem:/ {print $2}')
USED_RAM=$(free -m | awk '/Mem:/ {print $3}')
RAM=$((USED_RAM * 100 / TOTAL_RAM))

echo "RAM Usage: $RAM%"

ROOT=$(df -h | awk '$NF=="/" {gsub("%","",$5); print $5}')

echo "Root Partition Usage: $ROOT%"

if [ "$CPU" -gt "$LIMIT" ]; then
    echo "$(date): CPU usage above ${LIMIT}% (${CPU}%)" >> /var/log/resources.log
fi

if [ "$RAM" -gt "$LIMIT" ]; then
    echo "$(date): RAM usage above ${LIMIT}% (${RAM}%)" >> /var/log/resources.log
fi

if [ "$ROOT" -gt "$LIMIT" ]; then
    echo "$(date): Root partition usage above ${LIMIT}% (${ROOT}%)" >> /var/log/resources.log
fi
```

This script:
- Monitors CPU usage
- Monitors RAM usage
- Monitors root partition usage
- Logs an event if usage exceeds 90%

---

# Cron

Cron is the Linux task scheduler used to execute commands or scripts automatically at specified times.

Edit the cron table:

```bash
sudo crontab -e
```

Example:

```text
*/5 * * * * /home/user/resources.sh
```

This runs the script every **5 minutes**.

Cron schedule format:

```text
Minute Hour Day Month Weekday Command
```

---

# Backup with tar

The `tar` command is commonly used to archive and compress files.

---

## Common Options

| Option | Description |
|---------|-------------|
| `c` | Create an archive |
| `z` | Compress using gzip |
| `f` | Specify the archive filename |

---

## Backup Script Example

```bash
#!/bin/bash

tar -czf full-backup.tar.gz /etc

if [ "$(date +%A)" == "Sunday" ]; then
    tar -czf home-backup.tar.gz /home
fi
```

This script:

- Creates a compressed backup of `/etc`
- Every Sunday, also creates a compressed backup of `/home`

---

## 🧠 Summary

Linux provides powerful tools for monitoring system resources, automating tasks, and creating backups. Commands such as `top`, `vmstat`, `free`, and `df` help monitor system health, while `cron` automates recurring tasks. The `tar` utility is widely used to create compressed backups for system recovery and maintenance.
