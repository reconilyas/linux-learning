# Linux Network Configuration & Diagnostics

---

# Viewing Network Configuration

## Check if the DHCP Client is Running

Use the following command to verify whether the system is running a DHCP client:

```bash
sudo ps aux | grep dhclient
```

> **Note:** On most Linux distributions, the DHCP client process is **`dhclient`**, not `dhcclient`.

---

## Display IP Addresses

Show all IP addresses assigned to the system.

```bash
sudo ip addr show
```

or

```bash
ip a
```

---

## Display the Routing Table

View the routing table and the default gateway.

```bash
sudo ip route show
```

---

# Configuring a Static IP Address

## Step 1 — Stop the DHCP Client

Find the DHCP client process:

```bash
sudo ps aux | grep dhclient
```

Terminate the process:

```bash
sudo kill -9 <PID>
```

Replace `<PID>` with the Process ID of `dhclient`.

---

## Step 2 — Configure a Static IP Address

Edit the network configuration file:

```bash
sudo vi /etc/network/interfaces
```

Example configuration:

```text
auto eth0

iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.1
```

Replace `eth0` with your network interface name (such as `ens33`, `enp0s3`, or `wlan0`).

---

## Step 3 — Restart Networking

After saving the configuration, restart the networking service.

```bash
sudo /etc/init.d/networking restart
```

Or on systems using systemd:

```bash
sudo systemctl restart networking
```

---

## Step 4 — Verify the Configuration

Check that the new IP address has been applied.

```bash
ip addr show
```

---

# DNS Configuration

View the configured DNS servers.

```bash
cat /etc/resolv.conf
```

---

# Network Diagnostic Tools

## traceroute

Displays the path packets take to reach a destination.

It is useful for:
- Checking connectivity
- Identifying routing paths
- Finding where communication fails

Example:

```bash
traceroute google.com
```

---

## netstat

Displays network connections, listening ports, routing tables, and network statistics.

### Display Active Connections

```bash
sudo netstat
```

---

### Display All Ports and Processes

```bash
sudo netstat -anp
```

Options:

| Option | Description |
|---------|-------------|
| `-a` | Display all connections and listening ports |
| `-n` | Show numerical addresses and port numbers |
| `-p` | Display the process using each connection |

---

## 🧠 Summary

Linux provides powerful tools for viewing and configuring network settings. Commands such as `ip`, `traceroute`, and `netstat` help administrators configure interfaces, troubleshoot connectivity issues, inspect routing information, and monitor network activity.
