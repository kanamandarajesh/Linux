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

---

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
---

## 🔧 **DevOps-Specific Linux Interview Q\&A**

### 1. **How would you automate repetitive Linux administration tasks?**

**Answer:**
I use tools like:

* **Shell scripts** for quick automation (`bash`, `cron`, etc.)
* **Ansible** for agentless configuration management and automation
* **Terraform** for infrastructure provisioning
* **CI/CD pipelines** in tools like Jenkins/GitLab CI to automate deployments
  Example: Automating user creation with an Ansible playbook that reads a CSV.

---

### 2. **What tools do you use for configuration management? Why?**

**Answer:**

* **Ansible**: Simple, agentless, uses YAML, and integrates well with CI/CD.
* **Chef/Puppet**: Scalable, but more complex.
* **SaltStack**: Fast and scalable in large environments.
  For most modern teams, Ansible is preferred due to simplicity and fast adoption.

---

### 3. **How do you handle patching and kernel updates on production systems?**

**Answer:**

* Use **unattended-upgrades** or **yum-cron** for auto security patches.
* For controlled environments, schedule updates via **Ansible** or **WSUS-equivalent for Linux**.
* Kernel updates: Use `kexec` for faster reboots or apply **live patching** (e.g., Canonical Livepatch, kpatch).
* Always test updates in staging before applying to production.

---

### 4. **How do you secure a Linux server in a DevOps environment?**

**Answer:**

* **Disable root SSH login**, use **key-based authentication**
* Set up **firewalls** (`ufw`, `iptables`, or `firewalld`)
* Run **regular patching** and updates
* Use **security benchmarks** (e.g., CIS)
* Implement **role-based access control** (RBAC) using sudo policies
* Use **Fail2Ban** or similar tools to block brute-force attacks
* Enable **auditd** and configure **SELinux** or **AppArmor**

---

### 5. **What’s your backup and disaster recovery strategy on Linux?**

**Answer:**

* **Backup tools**: `rsync`, `restic`, `borg`, or commercial tools like Veeam
* Schedule regular backups via `cron` or automation (e.g., Ansible)
* Store backups offsite or on cloud (AWS S3, Azure Blob)
* Test **restore procedures** regularly
* Keep **snapshots** of cloud instances
* Use **HA (High Availability)** architectures (e.g., active/passive, clustering)

---

### 6. **How do you monitor Linux systems in a DevOps workflow?**

**Answer:**

* **Prometheus + Grafana**: Metric collection and visualization
* **ELK Stack (Elasticsearch, Logstash, Kibana)** for log monitoring
* **Nagios**, **Zabbix** for alerting and checks
* Use **Node Exporter**, `ps`, `top`, and `vmstat` for local monitoring
* Integrate alerts into **Slack, PagerDuty, or Opsgenie**

---

### 7. **How would you deploy an application on Linux via a CI/CD pipeline?**

**Answer:**

1. **Push to Git repo** triggers pipeline (GitHub Actions, Jenkins, etc.)
2. Pipeline stages:

   * **Build**: Compile/package the app
   * **Test**: Run unit/integration tests
   * **Artifact**: Push to Docker registry or package repo
   * **Deploy**:

     * SSH into Linux server
     * Use `scp`, `rsync`, or `Ansible` to copy artifacts
     * Restart services (`systemctl`, Docker, Kubernetes)
3. Notifications sent to Slack/email

---

### 8. **What’s your preferred method of containerizing applications on Linux?**

**Answer:**

* **Docker** is my go-to tool for containerization.
* Create a `Dockerfile`, build images, and push to a container registry.
* Use **docker-compose** for local multi-container apps
* For production, orchestrate with **Kubernetes** (via Helm charts or manifests)
* Monitor containers with **Prometheus cAdvisor**, **Grafana**, and **ELK**

---

### 9. **How do you troubleshoot a failed deployment on a Linux server?**

**Answer:**

* Check CI/CD logs (Jenkins, GitLab, etc.)
* SSH into server → check logs:

  * App logs (`/var/log/app.log`)
  * Web server logs (`/var/log/nginx/error.log`)
  * System logs (`journalctl`, `dmesg`)
* Check running processes (`ps aux`, `top`)
* Check open ports (`ss -tuln`)
* Validate permissions and ownership
* Roll back using Git, backups, or Docker tags

---

### 10. **How do you manage secrets in a Linux-based CI/CD environment?**

**Answer:**

* Use **HashiCorp Vault**, **AWS Secrets Manager**, or **Azure Key Vault**
* For CI/CD, inject secrets via environment variables or secret files
* Store encrypted secrets using `ansible-vault`
* Never hard-code passwords in scripts or repos
* Use tools like **SOPS** for encrypted GitOps workflows

---

### Bonus – Real DevOps Scenario

> **Q: You need to roll out a config change across 100 Linux servers. What's your approach?**
> **A:**

* Use **Ansible** to push config files (idempotent and version-controlled)
* Example: `ansible-playbook nginx_config.yml`
* Validate changes with a **dry run**
* Optionally run in **batches** (e.g., 10 servers at a time using `serial`)
* Monitor for errors and log output for auditing

---
---

## 🧠 **DevOps-Specific Linux Q\&A – Part 2**

### 11. **How do you manage environment-specific configurations in a CI/CD pipeline?**

**Answer:**

* Use **environment variables** injected at runtime (via Jenkins, GitLab, etc.)
* Store secrets in a **vault** and configs in separate files (`config.dev.yaml`, `config.prod.yaml`)
* Use **templating tools** like **Jinja2**, `envsubst`, or **Ansible templates**
* In Kubernetes, manage via **ConfigMaps** and **Secrets**

---

### 12. **How do you manage processes and services on Linux?**

**Answer:**

* Use `systemctl` to manage services (`systemctl start nginx`, `status`, `enable`, etc.)
* For non-systemd systems, use `service` or `init.d` scripts
* Monitor with `ps aux`, `top`, `htop`, and `journalctl`
* Automate service management with **Ansible handlers**

---

### 13. **How do you analyze system performance on Linux?**

**Answer:**

* Use `top`, `htop` → CPU/memory usage
* `iotop`, `iostat` → disk I/O
* `vmstat` → memory paging
* `netstat`, `iftop`, `ss` → network
* Use **sar** and `dstat` for historical performance
* Use Prometheus + Grafana for long-term metrics and alerting

---

### 14. **What is the difference between Docker and a VM (in a Linux context)?**

**Answer:**

* **Docker** uses kernel-level **namespaces and cgroups**, shares the host kernel
* **VMs** emulate entire hardware with a separate OS
* Containers are lightweight and faster to start
* VMs are more secure and isolated, but heavier

---

### 15. **What’s your approach to patching Docker containers in production?**

**Answer:**

* Keep **base images** updated (`FROM ubuntu:latest`)
* Automate rebuilds with security patches
* Use **Docker image scanning** (Trivy, Clair, Aqua)
* Avoid `latest` tag in production—use versioned tags
* Use CI/CD to rebuild → test → redeploy automatically

---

### 16. **How do you handle log rotation in Linux?**

**Answer:**

* Use **logrotate**, configured in `/etc/logrotate.d/`
* Set rotation frequency, file size limits, compression, and retention
* Example config:

  ```bash
  /var/log/myapp.log {
      daily
      rotate 7
      compress
      missingok
      notifempty
  }
  ```
* For containerized logs, use **log drivers** (e.g., `json-file`, Fluentd)

---

### 17. **Explain a real-world incident you resolved using Linux troubleshooting.**

**Answer:**

> “We had a CPU spike on a production server running Nginx. Using `top`, I identified a runaway PHP-FPM process. Logs (`/var/log/php7.4-fpm.log`) showed a recursive function crash. We restarted the service with `systemctl restart php7.4-fpm`, deployed a hotfix, and added alerts to Prometheus for future detection.”

---

### 18. **How do you test infrastructure or Linux changes before pushing to production?**

**Answer:**

* Use **staging/test environments** (ideally identical to prod)
* Use **Vagrant** or **Docker Compose** for local testing
* Write **Ansible playbook dry-runs** (`--check`)
* Use **Terraform plan** to preview infra changes
* Use integration testing tools like **Testinfra**, **Molecule**, or **Goss**

---

### 19. **How do you ensure high availability (HA) of Linux-based services?**

**Answer:**

* Load balancers (HAProxy, NGINX, or AWS ELB)
* Redundant services across AZs or nodes
* **Keepalived + VRRP** for failover IPs
* Use **systemd watchdogs** or process monitoring (Monit)
* Database replication and app clustering (e.g., MySQL replication, Redis Sentinel)

---

### 20. **How do you perform zero-downtime deployments on Linux?**

**Answer:**

* **Blue-Green or Canary deployments** via CI/CD
* Use **load balancer** to shift traffic gradually
* **Docker/K8s rolling updates**
* Use `systemd` socket activation or NGINX with graceful reloads (`nginx -s reload`)
* Automate rollback on failure (GitOps or CD tools)

---

## 🧩 Bonus Scenario-Based Question

### 21. **Scenario: Your deployment pipeline fails intermittently during `scp` to Linux servers. How do you handle it?**

**Answer:**

* Verify **network stability and DNS resolution**
* Add `set -e` and error handling to scripts
* Use **Ansible** or **rsync with retries** instead of plain `scp`
* Add timeout and retry logic
* Store artifacts in a shared location (S3, Nexus) and pull from servers instead

---
