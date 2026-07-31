# Linux Filesystem Directory Structure

---

# Linux Filesystem Hierarchy

Linux organizes files and directories using the **Filesystem Hierarchy Standard (FHS)**. Each directory has a specific purpose.

---

## `/bin`

Contains essential user command binaries required for system operation.

Examples:

- `ls`
- `cp`
- `mv`
- `cat`
- `mkdir`

These commands are available to all users.

```bash
ls /bin
```

---

## `/sbin`

Contains essential system administration binaries.

Examples:

- `fdisk`
- `iptables`
- `reboot`
- `shutdown`

These commands are primarily intended for administrators (root).

```bash
ls /sbin
```

---

## `/boot`

Contains files required to boot the operating system.

Includes:
- Linux kernel
- Bootloader files (GRUB)
- Initial RAM filesystem (initramfs)

```bash
ls /boot
```

---

## `/dev`

Contains device files representing hardware devices.

Examples:

- Hard disks
- USB devices
- Terminals
- Network interfaces

```bash
ls /dev
```

---

## `/etc`

Stores system-wide configuration files.

Examples:
- Network configuration
- SSH configuration
- User account configuration

```bash
ls /etc
```

---

## `/media`

Mount point for removable media.

Examples:
- USB flash drives
- CDs/DVDs
- External hard drives

```bash
ls /media
```

---

## `/mnt`

Temporary mount point used by administrators.

Often used for:
- Manual mounting
- Testing storage devices
- Network shares

```bash
ls /mnt
```

---

## `/proc`

A virtual filesystem containing information about the running system and processes.

Examples:
- CPU information
- Memory usage
- Running processes
- Kernel information

The files are generated dynamically and exist only while the system is running.

```bash
ls /proc
```

---

## `/run`

Contains temporary runtime information created after the system boots.

Examples:
- Process IDs (PID files)
- Runtime sockets
- Lock files

```bash
ls /run
```

---

## `/var`

Stores variable data that changes during system operation.

Common contents:
- System logs (`/var/log`)
- Databases
- Web server files (commonly `/var/www`)
- Mail queues
- Cache files

```bash
ls /var
```

---

## `/usr`

One of the largest directories in Linux.

Contains:
- User applications
- Libraries
- Documentation
- Shared resources

Common subdirectories:

- `/usr/bin`
- `/usr/sbin`
- `/usr/lib`
- `/usr/share`

```bash
ls /usr
```

---

# Summary Table

| Directory | Purpose |
|-----------|---------|
| `/bin` | Essential user commands |
| `/sbin` | System administration commands |
| `/boot` | Bootloader and kernel files |
| `/dev` | Device files |
| `/etc` | Configuration files |
| `/media` | Removable media mount points |
| `/mnt` | Temporary mount points |
| `/proc` | Process and kernel information |
| `/run` | Runtime system information |
| `/var` | Variable data (logs, databases, web files) |
| `/usr` | User applications, libraries, and shared resources |

---

## 🧠 Summary

The Linux filesystem follows a standardized directory hierarchy where each directory has a dedicated purpose. Understanding this structure is essential for Linux administration, troubleshooting, and cybersecurity.
          


      

