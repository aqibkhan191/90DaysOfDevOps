
# Day 03 – Linux Commands Cheat Sheet

> Quick reference for Process Management, File System, and Networking troubleshooting.

---

## 🔄 Process Management

| Command | Usage |
|---------|-------|
| `ps aux` | List all running processes with PID, CPU, and memory |
| `top` | Live process monitor — press `q` to quit |
| `htop` | Improved `top` with color and mouse support (install if missing) |
| `kill <PID>` | Send SIGTERM (graceful stop) to a process |
| `kill -9 <PID>` | Force-kill a process immediately (SIGKILL) |
| `pkill nginx` | Kill process by name instead of PID |
| `jobs` | List background/stopped jobs in current shell session |
| `bg %1` | Resume a stopped job in the background |
| `fg %1` | Bring a background job back to the foreground |
| `nice -n 10 ./script.sh` | Start a process with lower CPU priority (niceness 10) |
| `renice 5 -p <PID>` | Change priority of an already-running process |

---

## 📁 File System

| Command | Usage |
|---------|-------|
| `ls -lah` | List files with sizes in human-readable format, including hidden |
| `find / -name "*.log" 2>/dev/null` | Search for all `.log` files from root, suppress errors |
| `du -sh /var/log/*` | Show disk usage of each item in `/var/log` |
| `df -h` | Show disk space used/free on all mounted filesystems |
| `tail -f /var/log/syslog` | Follow a log file in real time |
| `grep -r "ERROR" /var/log/` | Recursively search for "ERROR" in all log files |
| `chmod 755 script.sh` | Set file permissions (owner: rwx, group: r-x, others: r-x) |
| `chown user:group file.txt` | Change ownership of a file |
| `ln -s /original /link` | Create a symbolic (soft) link |
| `tar -czf archive.tar.gz /dir` | Compress a directory into a `.tar.gz` archive |
| `tar -xzf archive.tar.gz` | Extract a `.tar.gz` archive in current directory |

---

## 🌐 Networking

| Command | Usage |
|---------|-------|
| `ping -c 4 google.com` | Send 4 ICMP packets to check connectivity to a host |
| `ip addr` | Show all network interfaces and their IP addresses |
| `ip route` | Display the routing table to see how traffic is directed |
| `dig google.com` | DNS lookup — shows A record and query details |
| `curl -I https://example.com` | Fetch only HTTP response headers (check status code) |
| `curl -o /dev/null -sw "%{http_code}" https://example.com` | Get just the HTTP status code of a URL |
| `ss -tuln` | Show all listening TCP/UDP ports (faster than `netstat`) |
| `netstat -tulnp` | List listening ports with process names (needs `net-tools`) |
| `traceroute google.com` | Trace the network path (hops) to a destination host |
| `wget -q -O - https://example.com/file` | Download a file silently and output to stdout |

---

## 📋 Logs & Systemd (Bonus)

| Command | Usage |
|---------|-------|
| `journalctl -xe` | View recent system journal logs with context and errors |
| `journalctl -u nginx -f` | Follow live logs for a specific systemd service |
| `systemctl status sshd` | Check if SSH service is active and see recent log lines |
| `dmesg | tail -20` | View last 20 lines of kernel ring buffer (hardware/boot events) |

---

## ⚡ One-Liners for Incidents

```bash
# Find top 5 CPU-hungry processes
ps aux --sort=-%cpu | head -6

# Find which process is using port 80
ss -tulnp | grep :80

# Check disk usage sorted largest first
du -sh /var/log/* | sort -rh | head -10

# Watch a log for errors in real time
tail -f /var/log/nginx/error.log | grep --color "ERROR\|WARN"

# Test if a remote port is open
curl -v telnet://192.168.1.10:22
```

---

## 🔑 Quick Reference: Signals

| Signal | Number | Meaning |
|--------|--------|---------|
| SIGTERM | 15 | Graceful shutdown (default `kill`) |
| SIGKILL | 9 | Force kill — cannot be caught or ignored |
| SIGHUP | 1 | Reload config (many daemons respond to this) |
| SIGSTOP | 19 | Pause a process (like `Ctrl+Z`) |

---

*Day 03 of #90DaysOfDevOps | #DevOpsKaJosh | #TrainWithShubham*
