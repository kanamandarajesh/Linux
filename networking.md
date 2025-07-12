Here’s a list of **essential networking commands in Linux** that are commonly used for troubleshooting, configuration, and monitoring:

---

### 🔧 **Basic Network Configuration Commands**

| Command              | Description                                                      |
| -------------------- | ---------------------------------------------------------------- |
| `ifconfig`           | Show or configure network interfaces *(deprecated, use `ip`)*    |
| `ip a` or `ip addr`  | Display IP addresses and interfaces                              |
| `ip r` or `ip route` | Show the routing table                                           |
| `ip link`            | Show or manage network devices                                   |
| `hostname`           | Display or set the system’s hostname                             |
| `nmcli`              | NetworkManager command-line interface (for managing connections) |
| `nmtui`              | Text-based GUI for NetworkManager                                |

---

### 📶 **Testing Connectivity**

| Command                | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| `ping <host>`          | Send ICMP echo requests to test network reachability |
| `traceroute <host>`    | Show the path packets take to a destination          |
| `tracepath <host>`     | Similar to `traceroute`, doesn't require root        |
| `telnet <host> <port>` | Check connectivity to a specific port                |
| `nc <host> <port>`     | Netcat, for testing TCP/UDP connections              |
| `curl <url>`           | Test HTTP/HTTPS requests                             |
| `wget <url>`           | Download files from a network (HTTP, FTP)            |

---

### 📡 **DNS and Hostname Resolution**

| Command                 | Description                        |
| ----------------------- | ---------------------------------- |
| `nslookup <domain>`     | Query DNS for domain info          |
| `dig <domain>`          | More advanced DNS lookup           |
| `host <domain>`         | DNS lookup                         |
| `getent hosts <domain>` | Resolve using `/etc/nsswitch.conf` |

---

### 🔍 **Monitoring and Diagnostics**

| Command                  | Description                                           |
| ------------------------ | ----------------------------------------------------- |
| `netstat -tuln`          | List open ports and services *(deprecated, use `ss`)* |
| `ss -tuln`               | Show active listening ports                           |
| `ss -s`                  | Display summary of socket stats                       |
| `tcpdump -i <interface>` | Capture network traffic                               |
| `iftop`                  | Live bandwidth usage per connection                   |
| `ip -s link`             | Show statistics of interfaces                         |
| `ethtool <interface>`    | Show/change Ethernet device settings                  |
| `mtr <host>`             | Combines ping and traceroute for network diagnostics  |

---

### 📁 **File Sharing and Transfer**

| Command                       | Description                            |
| ----------------------------- | -------------------------------------- |
| `scp <file> user@host:/path/` | Securely copy files over SSH           |
| `rsync -avz <src> <dest>`     | Sync files/folders efficiently         |
| `ftp` / `sftp`                | Transfer files using FTP/SFTP protocol |

---

### 🔐 **Firewall & Security**

| Command              | Description                               |
| -------------------- | ----------------------------------------- |
| `ufw status`         | Show firewall status (Ubuntu/Debian)      |
| `iptables -L`        | List iptables firewall rules              |
| `firewalld` commands | Use `firewall-cmd` on RHEL/CentOS systems |

---
