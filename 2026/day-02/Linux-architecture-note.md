# Day 02 – Linux Architecture, Processes, and systemd

---

## 🧱 Core Components of Linux

### Kernel
- The **heart of Linux** — talks directly to hardware (CPU, RAM, disk, network)
- Manages memory, device drivers, system calls, and security
- Lives in kernel space — user programs can't touch it directly

### User Space
- Where **all your programs run** (shell, apps, services)
- Communicates with the kernel via **system calls** (e.g., `open()`, `fork()`, `read()`)
- Isolated from kernel for stability and security

### Init System / systemd
- The **first process** that starts after the kernel boots (PID 1)
- Responsible for starting all other services and processes
- Modern Linux uses **systemd** as the init system

---

## ⚙️ How Processes Are Created & Managed

- Every process has a **PID** (Process ID) and a **PPID** (Parent Process ID)
- The kernel creates processes using two key system calls:
  - `fork()` — duplicates the parent process
  - `exec()` — replaces the process image with a new program
- All processes descend from **PID 1 (systemd)**

### Process States

| State    | Meaning |
|----------|---------|
| **Running (R)**  | Actively using the CPU |
| **Sleeping (S)** | Waiting for an event (I/O, timer) — interruptible |
| **Sleeping (D)** | Uninterruptible sleep — usually waiting on disk I/O |
| **Stopped (T)**  | Paused (e.g., by `Ctrl+Z` or a debugger) |
| **Zombie (Z)**   | Process finished but parent hasn't read its exit status yet |

> 💡 Zombie processes are harmless in small numbers but signal a buggy parent process.

---

## 🚀 What systemd Does & Why It Matters

- Starts, stops, and manages **system services** (daemons)
- Uses **unit files** (`.service`, `.socket`, `.timer`) instead of old bash scripts
- Handles **dependencies** between services — starts things in the right order
- Provides **logging** via `journald` (use `journalctl` to read logs)
- Enables **parallel service startup** → faster boot times

### Common systemctl Commands

```bash
systemctl status nginx        # Check service status
systemctl start nginx         # Start a service
systemctl stop nginx          # Stop a service
systemctl enable nginx        # Auto-start on boot
systemctl restart nginx       # Restart a service
journalctl -u nginx -f        # Follow logs for a service
```

---

## 🛠️ 5 Daily Commands for DevOps

| Command | What It Does |
|---------|-------------|
| `ps aux` | List all running processes with CPU/memory usage |
| `top` / `htop` | Live view of processes and resource usage |
| `kill -9 <PID>` | Force-kill a process by its PID |
| `systemctl status <service>` | Check if a service is running and healthy |
| `journalctl -xe` | View recent system logs with errors |

---

## 🔑 Key Takeaways

- **Kernel** handles hardware; **user space** is where your apps live
- Every process starts via `fork()` + `exec()` from a parent
- **Zombie processes** = finished but not cleaned up by parent
- **systemd** (PID 1) manages all services; `systemctl` is your main tool
- When a service crashes, check: `systemctl status` → `journalctl -u`

---

*Day 02 of #90DaysOfDevOps | #DevOpsKaJosh | #TrainWithShubham*
