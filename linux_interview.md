---

### ✅ **Scenario-Based Linux Interview Questions and Answers**

---

### **Q1: Server Load is High. How Would You Troubleshoot This?**

**Answer:**

1. Check load average:

   ```bash
   uptime
   ```
2. Check which processes are consuming high CPU/memory:

   ```bash
   top
   htop
   ```
3. Check IO wait:

   ```bash
   iostat -xm 1 3
   ```
4. Check for zombie or stuck processes:

   ```bash
   ps aux | grep 'Z'
   ```
5. Check system logs:

   ```bash
   journalctl -xe
   dmesg | tail
   ```

---

### **Q2: A User Can’t SSH Into the Server. What Will You Check?**

**Answer:**

1. Check if SSH service is running:

   ```bash
   systemctl status sshd
   ```
2. Check if the port is open and listening:

   ```bash
   netstat -tuln | grep :22
   ```
3. Check firewall settings:

   ```bash
   iptables -L -n
   firewall-cmd --list-all
   ```
4. Check user's shell and home directory permissions:

   ```bash
   grep username /etc/passwd
   ls -ld /home/username
   ```
5. Review authentication logs:

   ```bash
   tail -f /var/log/auth.log   # Ubuntu/Debian
   tail -f /var/log/secure     # CentOS/RHEL
   ```

---

### **Q3: A Cron Job is Not Running. How Will You Troubleshoot It?**

**Answer:**

1. Check if the cron service is active:

   ```bash
   systemctl status cron    # Debian/Ubuntu
   systemctl status crond   # RHEL/CentOS
   ```
2. Verify the user's crontab:

   ```bash
   crontab -l
   ```
3. Check cron logs:

   ```bash
   grep CRON /var/log/syslog      # Debian/Ubuntu
   grep CRON /var/log/cron        # RHEL/CentOS
   ```
4. Ensure script has execute permission and full paths:

   ```bash
   chmod +x /path/to/script.sh
   ```
5. Add logging in crontab:

   ```bash
   * * * * * /path/to/script.sh >> /tmp/cron.log 2>&1
   ```

---

### **Q4: Disk Usage Alert: Root Partition is Full. What Will You Do?**

**Answer:**

1. Check disk usage:

   ```bash
   df -h
   ```
2. Find largest files/directories:

   ```bash
   du -ahx / | sort -rh | head -20
   ```
3. Clean journal logs:

   ```bash
   journalctl --vacuum-time=2d
   ```
4. Clean package manager cache:

   ```bash
   apt-get clean        # Ubuntu/Debian
   yum clean all        # RHEL/CentOS
   ```
5. Check for deleted files still held open:

   ```bash
   lsof | grep deleted
   ```

---

### **Q5: Accidentally Deleted `/etc/fstab`. How Will You Recover?**

**Answer:**

1. Don’t reboot the system.
2. Identify mounted devices:

   ```bash
   mount
   lsblk
   blkid
   ```
3. Recreate `/etc/fstab` using UUIDs:
   Example entry:

   ```
   UUID=xxxx-xxxx  /  ext4  defaults  0 1
   ```
4. Validate:

   ```bash
   mount -a
   ```

---

### **Q6: A File Was Accidentally Deleted. Can It Be Recovered?**

**Answer:**

1. If the file is still held open by a process:

   ```bash
   lsof | grep deleted
   ```

   Copy it using:

   ```bash
   cp /proc/<pid>/fd/<fd_number> /tmp/recovered_file
   ```
2. If not open, use recovery tool:

   * For ext4:

     ```bash
     extundelete /dev/sdX --restore-file /path/to/file
     ```
   * Must unmount disk first.

---

### **Q7: How Would You Add a New Disk and Mount It?**

**Answer:**

1. Identify the new disk:

   ```bash
   lsblk
   fdisk -l
   ```
2. Create a partition:

   ```bash
   fdisk /dev/sdX
   ```
3. Format the partition:

   ```bash
   mkfs.ext4 /dev/sdX1
   ```
4. Create a mount point and mount:

   ```bash
   mkdir /mnt/data
   mount /dev/sdX1 /mnt/data
   ```
5. Make it permanent in `/etc/fstab`:

   ```
   UUID=xxxxx /mnt/data ext4 defaults 0 0
   ```

---

### **Q8: A Service Is Failing to Start. How Do You Fix It?**

**Answer:**

1. Check status:

   ```bash
   systemctl status servicename
   ```
2. View logs:

   ```bash
   journalctl -xeu servicename
   ```
3. Check for config errors:

   ```bash
   cat /etc/servicename/config.conf
   ```
4. Validate permissions and ports.
5. Restart the service:

   ```bash
   systemctl restart servicename
   ```
---
---

### **Q9: System is Booting into Emergency Mode. What Will You Check?**

**Answer:**

1. Check boot logs:

   ```bash
   journalctl -xb
   ```

2. Common reasons:

   * Incorrect entry in `/etc/fstab`
   * Corrupted disk
   * Missing root partition

3. Fix `/etc/fstab`:

   * Edit it from rescue mode or boot using `init=/bin/bash`

4. Check disk:

   ```bash
   fsck /dev/sdXn
   ```

---

### **Q10: Network Interface is Down After Reboot. What Steps Will You Take?**

**Answer:**

1. Check interface status:

   ```bash
   ip a
   nmcli device status
   ```

2. Bring it up manually:

   ```bash
   ip link set eth0 up
   ```

3. Check if `NetworkManager` or `network` service is active:

   ```bash
   systemctl status NetworkManager
   ```

4. Verify config in `/etc/sysconfig/network-scripts/ifcfg-eth0` (RHEL) or `/etc/netplan/` (Ubuntu 18.04+)

5. Restart the network:

   ```bash
   systemctl restart network     # RHEL
   netplan apply                 # Ubuntu
   ```

---

### **Q11: You Need to Schedule a Job to Run Once at 2 AM Tomorrow. What Do You Do?**

**Answer:**
Use `at` command:

```bash
echo "/path/to/script.sh" | at 2:00 AM tomorrow
```

Check scheduled jobs:

```bash
atq
```

---

### **Q12: You Want to Create a Swap File on a Running Server. How?**

**Answer:**

1. Create a 1GB swap file:

   ```bash
   dd if=/dev/zero of=/swapfile bs=1M count=1024
   chmod 600 /swapfile
   mkswap /swapfile
   swapon /swapfile
   ```

2. Make it persistent:
   Add to `/etc/fstab`:

   ```
   /swapfile none swap sw 0 0
   ```

---

### **Q13: How to Redirect All Traffic from Port 80 to 8080?**

**Answer:**
Use `iptables`:

```bash
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
```

Make it persistent:

```bash
iptables-save > /etc/sysconfig/iptables
```

Or use `firewalld` with `--permanent` and reload.

---

### **Q14: How Do You Check Which Process is Using a Specific Port (e.g., 3306)?**

**Answer:**

```bash
lsof -i :3306
```

or

```bash
netstat -tulnp | grep 3306
```

or

```bash
ss -ltnp | grep 3306
```

---

### **Q15: How Would You Kill a Process That’s Consuming Too Much Memory?**

**Answer:**

1. Identify the process:

   ```bash
   ps aux --sort=-%mem | head
   ```

2. Kill it:

   ```bash
   kill -9 <PID>
   ```

3. Optionally restart the related service.

---

### **Q16: How Do You Set a Static IP Address on a Linux System?**

**Answer (RHEL/CentOS):**

1. Edit `/etc/sysconfig/network-scripts/ifcfg-eth0`:

   ```
   BOOTPROTO=static
   IPADDR=192.168.1.100
   NETMASK=255.255.255.0
   GATEWAY=192.168.1.1
   DNS1=8.8.8.8
   ```

2. Restart network:

   ```bash
   systemctl restart network
   ```

**Answer (Ubuntu 18.04+):**

1. Edit `/etc/netplan/01-netcfg.yaml`:

   ```yaml
   network:
     version: 2
     ethernets:
       eth0:
         addresses: [192.168.1.100/24]
         gateway4: 192.168.1.1
         nameservers:
           addresses: [8.8.8.8, 8.8.4.4]
   ```

2. Apply changes:

   ```bash
   netplan apply
   ```

---

### **Q17: A User Reports "Permission Denied" When Accessing a File. What Do You Check?**

**Answer:**

1. Check file permissions:

   ```bash
   ls -l /path/to/file
   ```

2. Check directory permissions (especially execute `x`):

   ```bash
   ls -ld /path/to/
   ```

3. Check ownership:

   ```bash
   chown user:group /path/to/file
   ```

4. Use `namei` to trace permission on each directory:

   ```bash
   namei -l /path/to/file
   ```

---

### **Q18: You Need to Limit CPU Usage of a Process. How?**

**Answer:**
Use `cpulimit` or `cgroups`.

Example with `cpulimit`:

```bash
cpulimit -p <PID> -l 20
```

This limits the process to 20% of one CPU core.

---

### **Q19: How Do You Archive and Compress a Directory?**

**Answer:**
To archive and compress:

```bash
tar -czvf backup.tar.gz /path/to/dir
```

To extract:

```bash
tar -xzvf backup.tar.gz
```

---

### **Q20: You Need to Check Which User Executed a Specific Command. How Can You Audit That?**

**Answer:**

1. If `auditd` is enabled:

   ```bash
   ausearch -x /usr/bin/command
   ```

2. If shell history is available:

   ```bash
   cat /home/user/.bash_history
   ```

3. For recent sudo activity:

   ```bash
   cat /var/log/auth.log | grep sudo
   ```

---


## 🔹 **Basic Level – Questions and Answers**
1. **What is Linux and how is it different from Unix?**
   **Answer:**
   Linux is an open-source Unix-like operating system kernel. It's free and developed by the community. Unlike proprietary Unix systems (like AIX, Solaris), Linux distributions (like Ubuntu, CentOS, Red Hat) are widely available for various hardware.

2. **What is the difference between a process and a thread?**
   **Answer:**
   A **process** is an independent program with its own memory space. A **thread** is a lightweight unit of a process that shares the same memory but can run concurrently.

3. **Explain the Linux file system hierarchy.**
   **Answer:**
   The Linux file system starts with `/` (root). Common directories include:

   * `/bin` – essential binaries
   * `/etc` – system config files
   * `/home` – user directories
   * `/var` – log files, spools
   * `/usr` – user applications
   * `/tmp` – temporary files

4. **What does the `ls -l` command show you?**
   **Answer:**
   It lists files and directories in long format, showing permissions, number of links, owner, group, size, and timestamp.

5. **How do you check disk usage in Linux?**
   **Answer:**
   Use `df -h` for filesystem space usage and `du -sh /path` for space used by a directory.

6. **What does `chmod 755 filename` do?**
   **Answer:**
   Sets file permissions to:

   * Owner: read/write/execute
   * Group: read/execute
   * Others: read/execute

7. **How do you view the contents of a text file in Linux?**
   **Answer:**
   Use `cat`, `less`, `more`, or `tail`.

8. **What is the difference between soft and hard links?**
   **Answer:**

   * **Hard link**: Points to the inode. Still works if the original file is deleted.
   * **Soft (symbolic) link**: Points to the file path. Breaks if the file is removed.

9. **How do you find out the IP address of a Linux system?**
   **Answer:**
   Use `ip a`, `hostname -I`, or `ifconfig` (older systems).

10. **How do you create a new user in Linux?**
    **Answer:**
    `sudo adduser username` or `sudo useradd -m username`
    
## 🔹 **Intermediate Level – Questions and Answers**

1. **Difference between symbolic and hard link?**
   **Answer:**
   As above — symbolic links are like shortcuts, hard links are file-level clones that point to the same inode.

2. **Use of `grep`, `awk`, `sed` – with examples:**
   **Answer:**

   * `grep "error" logfile.txt` – search lines with "error"
   * `awk '{print $1}' file` – print first column
   * `sed 's/foo/bar/g' file` – replace "foo" with "bar"

3. **How do you schedule a job using `cron`?**
   **Answer:**
   Use `crontab -e` to edit a user’s cron jobs. Format:
   `* * * * * command` (minute, hour, day, month, weekday)

4. **Difference between `su` and `sudo`?**
   **Answer:**

   * `su` switches the user (asks for target user's password)
   * `sudo` runs a command with root privileges (asks your password)

5. **What happens when you execute a binary in Linux?**
   **Answer:**
   The shell loads the program, the kernel assigns it memory, and the process runs. The binary must have execute permissions.

6. **How to find which process is using a specific port?**
   **Answer:**
   `sudo lsof -i :PORT`, or `netstat -tulnp | grep PORT`, or `ss -tulnp`

7. **Explain the Linux boot process.**
   **Answer:**

   * BIOS → Bootloader (GRUB)
   * Bootloader loads kernel
   * Kernel loads init/systemd
   * `systemd` starts services and user-space

8. **What is a runlevel?**
   **Answer:**
   A state of the machine. Examples:

   * 0: halt
   * 1: single user
   * 3: multi-user (no GUI)
   * 5: multi-user + GUI
     Modern systems use **systemd targets**.

9. **How do you mount a file system?**
   **Answer:**
   `mount /dev/sdX1 /mnt`
   Or define in `/etc/fstab` for persistence.

10. **Explain `top`, `htop`, and how to identify high memory usage.**
    **Answer:**

* `top` and `htop` show system resource usage.
* Look under `%MEM` or `RES` columns.
* `htop` is interactive and color-coded.

---

## 🔹 **Advanced Level – Questions and Answers**

1. **How does memory management work in Linux?**
   **Answer:**
   Uses virtual memory. When RAM is full, it uses swap. Memory is divided into pages. `vmstat`, `free -m`, and `/proc/meminfo` help monitor.

2. **What are inodes?**
   **Answer:**
   Inodes store metadata about files (permissions, owner, timestamps), not content or name.

3. **How do you troubleshoot a slow server?**
   **Answer:**

   * Use `top`, `iotop`, `vmstat`, `dstat`
   * Check logs (`/var/log/`)
   * Look for high CPU, I/O wait, memory swap

4. **What is `strace` and when to use it?**
   **Answer:**
   `strace` traces system calls of a process. Useful for debugging crashing or hanging apps:
   `strace ./app` or `strace -p PID`

5. **Difference between `fork()` and `exec()`?**
   **Answer:**

   * `fork()` creates a new process (child)
   * `exec()` replaces the current process image with a new program

6. **How does `iptables` or `firewalld` work?**
   **Answer:**

   * `iptables` is a packet filter and firewall
   * Rules are applied based on chains: INPUT, OUTPUT, FORWARD
   * `firewalld` is a wrapper for managing rules dynamically

7. **What is SELinux or AppArmor?**
   **Answer:**
   Security modules for mandatory access control (MAC).

   * SELinux: More granular, used in RHEL
   * AppArmor: Simpler, used in Ubuntu

8. **Explain cgroups and namespaces.**
   **Answer:**

   * **cgroups** limit resource usage (CPU, memory) per process group
   * **namespaces** isolate system resources (PID, NET, MNT, UTS), used in containers

9. **How to troubleshoot NFS mount permission issues?**
   **Answer:**

   * Check `/etc/exports` on the server
   * Validate user UID/GID mapping
   * Use `showmount -e server_ip` and `mount -v`

10. **How do you monitor logs in real-time?**
    **Answer:**
    `tail -f /var/log/syslog` or use tools like `journalctl -f` (for systemd systems)

---

