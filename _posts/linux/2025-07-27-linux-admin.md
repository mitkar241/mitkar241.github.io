---
title: "Linux Admin"
date: 2025-07-27 00:00:00 +0530
categories: [linux]
tags: [linux]
---

---

# Linux Admin
---

#### Resources:
- [Top 100+ Linux Interview Questions and Answers (2025) - Naukri Code 360](https://www.naukri.com/code360/library/linux-interview-questions)

---

### What is the purpose of the /etc/passwd file?

The /etc/passwd file is a critical system file in Linux that stores essential information about user accounts. Each line in the file represents a user account and contains fields separated by colons, including:

- Username
- Encrypted password (typically stored in /etc/shadow for security)
- User ID (UID)
- Group ID (GID)
- User's full name or description
- Home directory
- Login shell

This file is used by various system utilities to manage user accounts and permissions.

---

### How do you check system resource usage in Linux?

There are several commands to check system resource usage in Linux:

- `top` or `htop`: Provides a real-time, dynamic view of system processes and resource usage.
- `free`: Displays information about system memory usage.
- `df`: Shows disk space usage for mounted filesystems.
- `iostat`: Reports CPU statistics and I/O statistics for devices and partitions.
- `vmstat`: Reports information about processes, memory, paging, block I/O, and CPU activity.

---

### What is a symbolic link and how do you create one?

A symbolic link (also known as a symlink or soft link) is a special type of file that points to another file or directory. It's similar to a shortcut in Windows.

To create a symbolic link, use the ln command with the -s option:

```
ln -s target_path link_name
```

For example:

```
ln -s /path/to/original/file /path/to/symlink
```

---

### How do you find large files on a Linux system?

You can use the find command combined with sort to locate large files:

```
find /path/to/search -type f -size +100M -exec ls -lh {} \; | sort -k5 -rh
```

This command will:

- Search for files larger than 100MB
- List them with human-readable sizes
- Sort them by size in descending order

---

### What is the purpose of the cron daemon?

The cron daemon is a time-based job scheduler in Unix-like operating systems. It enables users to schedule jobs (commands or shell scripts) to run periodically at fixed times, dates, or intervals. Common uses include:

- Automating system maintenance tasks
- Scheduling backups
- Running periodic reports
- Monitoring system health

Jobs are configured in crontab files, which specify the schedule and command to run.

---

### How do you check open ports on a Linux system?

To check open ports on a Linux system, you can use the following commands:

- `netstat -tuln`: Shows all active listening ports
- `ss -tuln`: A more modern alternative to netstat
- `lsof -i`: Lists all network connections and the processes using them

For example:

```
sudo netstat -tuln | grep LISTEN
```

This will show all TCP and UDP ports in the LISTEN state.

---

### What is the purpose of the /etc/fstab file?

The /etc/fstab (file system table) file contains information about how disk partitions and other block devices should be mounted into the file system. It includes:

- Device identifiers (UUID, device path)
- Mount points
- Filesystem types
- Mount options
- Dump and pass values for filesystem checks

This file is read by the system during boot to determine which filesystems to mount and how to mount them.

---

### How do you troubleshoot high CPU usage on a Linux server?

To troubleshoot high CPU usage:

- Use top or htop to identify which processes are consuming the most CPU.
- Check the load average with uptime to see if the system is overloaded.
- Use ps aux to get more detailed information about specific processes.
- Check system logs (/var/log/syslog or journalctl) for any errors or warnings.
- Use strace to trace system calls and signals for a specific process.
- If it's a web server, check the access logs for unusual traffic patterns.
- Consider using more specialized tools like perf for performance analysis if needed.

---

### What is SELinux and what are its modes?

SELinux (Security-Enhanced Linux) is a security architecture integrated into the Linux kernel that provides mandatory access control (MAC) system. It enforces security policies to restrict programs' access to system resources.

SELinux has three modes:

- `Enforcing`: SELinux policy is enforced. Security policy violations are prevented and logged.
- `Permissive`: SELinux policy is not enforced, but violations are logged. This is useful for troubleshooting.
- `Disabled`: SELinux is turned off completely.

You can check the current mode with getenforce and change it with setenforce (temporarily) or by editing /etc/selinux/config (permanently).

---

### How do you set up a basic firewall using iptables?

Here's a basic example of setting up a firewall using iptables:

```
# Flush existing rules
iptables -F

# Set default chain policies
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Allow loopback connections
iptables -A INPUT -i lo -j ACCEPT

# Allow established and related connections
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

# Allow incoming SSH (adjust port if needed)
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Allow incoming HTTP and HTTPS
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# Log dropped packets
iptables -A INPUT -j LOG --log-prefix "IPTables-Dropped: "

# Save rules (Debian/Ubuntu)
sudo iptables-save > /etc/iptables/rules.v4
```

This basic setup allows SSH, HTTP, and HTTPS traffic while blocking other incoming connections. Remember to adjust rules based on your specific needs and to use a persistent solution like iptables-persistent to ensure rules survive reboots.
