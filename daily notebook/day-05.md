# Day 05 — Linux Learning Journey
**Date:** June 27, 2026

---

## ✅ What I Accomplished Today

- Learned what a process is and how Linux manages them
- Learned to view processes using ps, ps aux, and top
- Learned to kill processes using kill command
- Learned system information commands df -h, free -h, uname -a, uptime
- Understood what syslog is and its role in cybersecurity
- Understood what SSH is and why it matters in security
- Understood what Swap memory is
- Read and interpreted all command outputs independently without help
- Connected process management concepts to real cybersecurity scenarios

---

## 💻 Commands Learned

| Command | What it does |
|---------|--------------|
| `ps` | Show only YOUR running processes |
| `ps aux` | Show ALL processes on entire system |
| `top` | Live real-time process monitor like Task Manager |
| `kill PID` | Stop a process using its ID number |
| `sleep 100 &` | Start a dummy process in background for testing |
| `ps aux \| grep name` | Search for specific process by name |
| `df -h` | Show disk storage space in human readable format |
| `free -h` | Show RAM and Swap usage in human readable format |
| `uname -a` | Show complete system and kernel information |
| `uptime` | Show how long system has been running and load |

---

## 🧠 Concepts Learned

- **Process** = every program running on Linux is a process with a unique PID
- **PID** = Process ID — unique number assigned to every running process
- **ps aux columns** = USER (owner), PID (ID), %CPU (processor), %MEM (memory), COMMAND (program name)
- **root processes** = system processes owned by admin — Linux itself runs these
- **asadull+ processes** = YOUR processes — things you started
- **&** = run a process in background so terminal stays free
- **Swap** = emergency fake RAM created from hard drive space when real RAM is full
- **syslog** = Linux system logger — records every event, login, error on the system
- **SSH** = Secure Shell — remotely control another computer securely through terminal
- **Load average** = 3 numbers showing system stress over last 1, 5, 15 minutes
- **0.00 load average** = system completely relaxed and healthy

---

## 📊 Reading ps aux Output

| USER | PID | COMMAND | Meaning |
|------|-----|---------|---------|
| root | 1 | systemd | Linux boss process — first to start |
| root | 113 | cron | Automatic task scheduler |
| syslog | 170 | rsyslogd | System logger records all events |
| asadull+ | 914 | bash | MY terminal session |
| asadull+ | 1003 | ps aux | Command I just ran |

**How to identify:**
- USER = root → Linux system process
- USER = asadull+ → MY process
- COMMAND = bash → my terminal
- COMMAND = what I typed → current running command

---

## 📊 MY System Information

| Info | Value |
|------|-------|
| Computer name | DESKTOP-8BL3MIG |
| OS | GNU/Linux |
| Kernel | 6.18.33.1-microsoft-standard-WSL2 |
| Architecture | x86_64 64-bit |
| Total RAM | 3.7GB |
| Used RAM | 457MB |
| Free RAM | 3.1GB |
| Swap | 1.0GB — 0B used healthy |
| C Drive | 141GB total 101GB used 72% |
| D Drive | 69GB total 59GB used 86% warning |
| E Drive | 30GB total 8.5GB used 29% |
| Uptime | 49 minutes |
| Load Average | 0.00 0.00 0.00 completely relaxed |

---

## 🔐 Cybersecurity Connections

### Finding Malware with ps aux
```bash
ps aux | grep -i suspicious
```
- Malware appears as unknown processes
- Suspicious process running as root = serious red flag
- High CPU from unknown process = possible cryptominer

### SSH Security
- SSH allows remote terminal access to servers
- Hackers attempt brute force attacks on SSH
- Failed SSH attempts recorded in /var/log/auth.log
- Strong passwords and SSH keys prevent unauthorized access

### Syslog Forensics
```bash
cat /var/log/auth.log | grep "Failed"
```
Multiple failed logins from same IP = brute force attack detected!

### Memory Exhaustion Attack
- Attackers fill RAM intentionally to crash systems
- free -h helps monitor RAM consumption
- Heavy swap usage = system struggling = possible attack

### Disk Space Attack
- Attackers fill disk space to crash services
- df -h helps monitor disk usage
- D drive at 86% should be cleaned soon

---

## 🔍 Special Processes Explained

| Process | Owner | Purpose |
|---------|-------|---------|
| systemd | root | PID 1 — boss of all processes |
| cron | root | Runs automatic scheduled tasks |
| rsyslogd | syslog | Records all system events to logs |
| chronyd | _chrony | Keeps system clock accurate |
| dbus-daemon | message+ | Internal Linux process communication |
| wsl-pro-service | root | WSL2 Windows and Linux connection |
| bash | asadullah | My terminal session |

---

## 💡 Big Insight

> *"ps aux is the security analyst's first weapon"*
> When a system is compromised the first thing an analyst runs is ps aux
> Every malware, every backdoor, every suspicious script shows up here
> Learning to read process output is learning to investigate attacks
> This is real SOC analyst and Digital Forensics work!

---

## ❓ Interview Questions I Can Now Answer

**Q: What is a process in Linux?**
A: A process is any program currently running on the system. Every process has a unique PID assigned by the kernel. Linux manages all processes through systemd which is always PID 1.

**Q: How would you find a suspicious process on a Linux system?**
A: I would run ps aux to list all running processes and look for unknown process names, processes consuming unusual CPU or memory, or unexpected processes running as root. I would then use grep to filter specific names and kill to terminate suspicious processes.

**Q: What is the difference between ps and ps aux?**
A: ps shows only processes belonging to the current user in the current terminal. ps aux shows ALL processes running on the entire system from all users including system processes owned by root.

**Q: What is Swap memory?**
A: Swap is hard drive space that Linux uses as emergency RAM when physical memory is full. It is slower than real RAM because hard drives are slower than memory chips. Heavy swap usage indicates the system needs more RAM.

**Q: What is SSH and why is it important in security?**
A: SSH (Secure Shell) is a protocol that allows secure encrypted remote access to Linux systems through terminal. It is important because it is a common attack target — hackers attempt brute force attacks against SSH to gain unauthorized access to servers. Failed SSH attempts are logged in /var/log/auth.log.

**Q: What is syslog?**
A: Syslog is the Linux system logging service that records all system events including logins, errors, and sudo commands. It stores logs in /var/log/. Security analysts use syslog for incident investigation and forensic analysis.

---

## 🎯 Tomorrow's Goal

- Learn SSH in detail
- Connect to a remote server via SSH
- Understand SSH keys and why chmod 600 matters for them
- Learn basic firewall concepts with ufw
