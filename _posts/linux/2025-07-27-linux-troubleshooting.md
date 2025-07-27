---
title: "Linux Troubleshooting"
date: 2025-07-27 00:00:00 +0530
categories: [linux]
tags: [linux]
---

---

### How do you check disk space usage on a Linux system?

To check disk space usage, you can use the df command:

- `df -h`: Shows disk usage in a human-readable format (GB, MB).
- `du -sh /path/to/directory`: Displays disk usage for a specific directory.

---

### How can you troubleshoot high CPU usage on a Linux system?

Use the following tools to troubleshoot high CPU usage:

- `top`: Provides a real-time view of running processes and their CPU usage.
- `htop`: Similar to top, but with a more user-friendly interface.
- `ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu`: Lists processes sorted by CPU usage.

---

### What command can you use to check for open ports and services?

Use the netstat or ss commands:

- `netstat -tuln`: Lists all open ports and associated services.
- `ss -tuln`: Shows open ports with more details and is faster than netstat.

---

### How do you check and free up memory on a Linux system?

- Use the `free -h` command to check memory usage in human-readable form.
- Use `top` or `htop` to monitor memory usage by processes.
- To free up memory, you can kill memory-intensive processes or use `sync; echo 3 > /proc/sys/vm/drop_caches` to drop the cache.

---

### How do you find large files on a Linux system that might be filling up disk space?

Use the find command to search for large files:

- `find / -type f -size +1G`: Finds all files larger than 1GB in size. You can adjust the path and size parameter based on your requirement.

---

### How can you troubleshoot a system that won’t boot?

- `Check GRUB`: Ensure the GRUB bootloader is loading correctly.
- `Boot in recovery mode`: Use recovery or rescue mode to access the system.
- `Check logs`: Check /var/log/syslog or /var/log/messages for error messages.
- `Filesystem issues`: Use fsck to check and repair filesystem corruption.

---

### How do you check for hardware issues on a Linux system?

- `dmesg`: Displays kernel ring buffer messages related to hardware and boot issues.
- `lshw`: Lists detailed information about the hardware components of the system.
- `smartctl -a /dev/sda`: Checks the health of hard drives using S.M.A.R.T. data.

---

### What are some ways to troubleshoot network connectivity issues in Linux?

- `Check interface status`: Use ifconfig or ip a to check network interfaces.
- `Ping test`: Use ping <hostname/IP> to check network connectivity.
- `Traceroute`: Use traceroute <hostname/IP> to trace the route packets take.
- `DNS issues`: Use nslookup or dig to troubleshoot DNS resolution problems.

---

### How do you check the system logs for troubleshooting purposes?

- Use the journalctl command to view the system logs:
  - `journalctl -xe`: Shows the most recent critical errors.
  - `journalctl -u <service-name>`: Views logs specific to a service.
- Alternatively, you can check the log files located in /var/log/, such as syslog, dmesg, and auth.log.

---

### How can you troubleshoot a slow system performance issue in Linux?

- `Check CPU usage`: Use top or htop to monitor processes consuming CPU.
- `Check memory usage`: Use free -h and vmstat to monitor memory usage.
- `Check I/O performance`: Use iotop or iostat to monitor disk I/O issues.
- `Review logs`: Check logs in /var/log/ and use dmesg for hardware-related issues.
