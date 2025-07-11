Here's a list of 100 important Linux commands:

*File and Directory Operations:*
1. `ls` - List files and directories.
2. `pwd` - Print working directory.
3. `cd` - Change directory.
4. `touch` - Create an empty file.
5. `mkdir` - Create a directory.
6. `rm` - Remove files or directories.
7. `cp` - Copy files and directories.
8. `mv` - Move or rename files and directories.
9. `find` - Search for files and directories.
10. `grep` - Search for text within files.
11. `cat` - View file content.
12. `more` and `less` - View file content one screen at a time.
13. `head` - Display the beginning of a file.
14. `tail` - Display the end of a file.

*File Permissions:*
15. `chmod` - Change file permissions.
16. `chown` - Change file ownership.
17. `chgrp` - Change group ownership.

*User and Group Management:*
18. `useradd` - Add a user.
19. `passwd` - Change user password.
20. `usermod` - Modify user properties.
21. `userdel` - Delete a user.
22. `groupadd` - Add a group.
23. `groupmod` - Modify group properties.
24. `groupdel` - Delete a group.
25. `su` - Switch user or become superuser.

*System Information:*
26. `uname` - Display system information.
27. `df` - Show disk space usage.
28. `du` - Show file and directory space usage.
29. `top` - Monitor system processes.
30. `ps` - Display information about processes.
31. `free` - Display memory usage.
32. `uptime` - Show system uptime.

*Package Management:*
33. `apt` - Advanced Package Tool (Debian/Ubuntu).
34. `yum` - Package manager (Red Hat/CentOS).
35. `dnf` - Next-generation package manager (Fedora).
36. `rpm` - Package manager (Red Hat/CentOS).
37. `dpkg` - Debian package manager.

*Networking:*
38. `ifconfig` - Network interface configuration.
39. `ping` - Send ICMP echo requests.
40. `netstat` - Network statistics.
41. `ss` - Socket statistics.
42. `wget` - Download files from the web.
43. `ssh` - Secure Shell for remote access.
44. `scp` - Securely copy files between hosts.
45. `ip` - Manage IP addresses and routes.
46. `nc` - Netcat for network troubleshooting.

*Archiving and Compression:*
47. `tar` - Archive files.
48. `gzip` - Compress files.
49. `gunzip` - Decompress files.
50. `zip` - Create compressed zip archives.
51. `unzip` - Extract files from zip archives.

*Process Control:*
52. `kill` - Terminate processes.
53. `pkill` - Send signals to processes.
54. `killall` - Terminate processes by name.

*Text Processing:*
55. `awk` - Text processing tool.
56. `sed` - Stream editor for text manipulation.

*System Monitoring:*
57. `htop` - Interactive process viewer.
58. `iotop` - View I/O usage by processes.
59. `nmon` - System monitoring tool.

*System Maintenance:*
60. `fsck` - File system check.
61. `reboot` - Reboot the system.
62. `shutdown` - Shutdown the system.

*Package Installation and Removal:*
63. `apt-get` - APT package handling utility.
64. `yum install` - Install packages (Red Hat/CentOS).
65. `dnf install` - Install packages (Fedora).
66. `rpm -i` - Install RPM packages.
67. `dpkg -i` - Install Debian packages.

*File Transfer:*
68. `rsync` - Remote file synchronization.

*Shell Scripting:*
69. `bash` - Execute Bash scripts.
70. `chmod +x` - Make a script executable.

*File Permissions:*
71. `chown` - Change file ownership.
72. `chmod` - Change file permissions.

*Text Editors:*
73. `vi`/`vim` - Command-line text editor.
74. `nano` - Simple text editor.

*System Logs:*
75. `tail -f` - Monitor log files in real-time.

*Kernel Management:*
76. `uname -r` - Display kernel version.
77. `modprobe` - Load/unload kernel modules.

*File Transfer Protocols:*
78. `ftp` - File Transfer Protocol client.
79. `sftp` - Secure FTP.
80. `scp` - Securely copy files.

*Disk Management:*
81. `fdisk` - Disk partitioning utility.
82. `mkfs` - Create a filesystem.
83. `mount` - Mount a filesystem.
84. `umount` - Unmount a filesystem.

*System Information:*
85. `lscpu` - Display CPU information.
86. `lsusb` - List USB devices.
87. `lsblk` - List block devices.
88. `lshw` - List hardware information.

*Package Queries:*
89. `dpkg -l` - List installed packages (Debian/Ubuntu).
90. `rpm -qa` - List installed packages (Red Hat/CentOS).
91. `yum list installed` - List installed packages (Red Hat/CentOS).

*Firewall Configuration:*
92. `ufw` - Uncomplicated Firewall (Ubuntu).
93. `iptables` - Advanced firewall configuration.

*Cron Jobs:*
94. `crontab` - Schedule tasks.
95. `at` - Schedule one-time tasks.

*SSH Key Management:*
96. `ssh-keygen` - Generate SSH keys.
97. `ssh-copy-id` - Copy SSH keys to remote hosts.

*System Updates:*
98. `apt update` - Update package lists (Debian/Ubuntu).
99. `yum update` - Update packages (Red Hat/CentOS).
100. `dnf update` - Update packages (Fedora).

scp /path/to/example_file.txt username@host_server:/path/on/host/server/
scp vm1711:/tmp/ex.file /tmp


These commands cover a wide range of Linux system administration and everyday tasks. Remember to use them with caution, especially commands that can modify or delete files and directories.

========================
To check **system information in Linux**, you can use the following commands depending on what details you want:

### 🖥️ 1. **Basic System Info**

```bash
uname -a
```

* Shows kernel name, version, and architecture.

```bash
hostnamectl
```

* Shows OS, kernel, architecture, hostname, etc.

---

### 💾 2. **CPU Information**

```bash
lscpu
```

* Displays CPU architecture, cores, threads, and more.

---

### 🧠 3. **Memory Info (RAM)**

```bash
free -h
```

* Shows total, used, and free memory in human-readable format.

```bash
cat /proc/meminfo
```

* Detailed memory stats.

---

### 💽 4. **Disk and Partition Info**

```bash
lsblk
```

* Lists block devices (disks, partitions).

```bash
df -h
```

* Shows disk space usage.

---

### 🌐 5. **Network Info**

```bash
ip a
```

* Shows all network interfaces and IPs.

```bash
nmcli device show
```

* Shows detailed network device info.

---

### 🧰 6. **Distro Info**

```bash
cat /etc/os-release
```

* Shows Linux distribution name, version, etc.

```bash
lsb_release -a
```

* (If installed) Detailed release info for Debian-based systems.

---

### ✅ 7. **Full Summary (one-shot)**

```bash
inxi -F
```

> 🔧 If `inxi` not found, install it using:

```bash
sudo apt install inxi      # Debian/Ubuntu
sudo yum install inxi      # RHEL/CentOS
sudo dnf install inxi      # Fedora
```

---

Would you like me to prepare a script to check all these details at once?


========================
VI EDITOR COMMANDS
========================
Certainly! Here are some important Vi (or Vim) editor commands in Linux:

*Navigation:*
1. `h` - Move cursor left.
2. `j` - Move cursor down.
3. `k` - Move cursor up.
4. `l` - Move cursor right.
5. `0` - Move to the beginning of the current line.
6. `$` - Move to the end of the current line.
7. `G` - Move to the end of the file.
8. `:n` - Move to line "n" (replace "n" with line number).

*Text Editing:*
9. `i` - Insert mode before the cursor.
10. `I` - Insert mode at the beginning of the current line.
11. `a` - Append mode after the cursor.
12. `A` - Append mode at the end of the current line.
13. `o` - Open a new line below the current line.
14. `O` - Open a new line above the current line.
15. `x` - Delete the character under the cursor.
16. `dd` - Delete the current line.
17. `yy` - Yank (copy) the current line.
18. `p` - Paste the yanked text after the cursor.
19. `P` - Paste the yanked text before the cursor.
20. `u` - Undo the last change.
21. `Ctrl + r` - Redo the last change.

*Search and Replace:*
22. `/` - Search forward (type your search term).
23. `?` - Search backward (type your search term).
24. `n` - Go to the next search result.
25. `N` - Go to the previous search result.
26. `:s/search_term/replace_term/g` - Replace "search_term" with "replace_term" globally on the current line.
27. `:%s/search_term/replace_term/g` - Replace "search_term" with "replace_term" globally in the entire file.

*Saving and Quitting:*
28. `:w` - Save changes.
29. `:q` - Quit (if no changes).
30. `:q!` - Quit without saving changes.
31. `:wq` - Save and quit.
32. `:x` or `ZZ` - Save and quit (if changes).

*Copy and Paste:*
33. `v` - Enter visual mode (for selecting text).
34. `V` - Enter visual line mode (select entire lines).
35. `y` - Yank (copy) selected text.
36. `d` - Delete selected text.
37. `"+y` - Yank text to system clipboard.
38. `"+p` - Paste text from system clipboard.

*Advanced Editing:*
39. `.` - Repeat the last command.
40. `:set number` - Display line numbers.
41. `:set nonumber` - Hide line numbers.
42. `:set syntax=on` - Enable syntax highlighting.
43. `:set syntax=off` - Disable syntax highlighting.
44. `:set hlsearch` - Highlight search results.
45. `:set nohlsearch` - Disable search result highlighting.

These Vi/Vim commands will help you navigate, edit, search, and save files efficiently in the Vi text editor. Vim is highly customizable and powerful, so you can explore more features and plugins as needed.
To move to the beginning of a file in the Vi editor, you can use the following command:

1. Press the `Esc` key to ensure you are in normal mode (not insert mode).

2. Then, press `gg`.

This will take you to the beginning of the file.

You can find the files occupying the most memory on a Linux system using the `du` (disk usage) and `sort` commands. Here's a command that can help you identify the largest files and directories:

du -h /path/to/search | sort -rh | head -n 10


Here's what this command does:

1. `du -h /path/to/search`: This command calculates the disk usage of all files and directories under the specified path and displays the results in human-readable format (`-h`).
2. `sort -rh`: It sorts the output in reverse order (`-r`) and numerically (`-h`) so that the largest files and directories are listed first.
3. `head -n 10`: This limits the output to the top 10 largest files or directories.

Replace `/path/to/search` with the directory you want to analyze. This command will show you the largest files and directories within that path, helping you identify which ones are consuming the most memory.
