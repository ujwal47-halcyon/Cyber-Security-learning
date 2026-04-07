# Day 10 - Processes

**Date:** January 9,2026.

---

## File vs Process

A file sits on disk. A process is what happens when that file runs —
its loaded into memory and starts executing.

This distinction matters more than it sounds. When youre on a target
machine and looking for whats running, youre looking at processes
not files. The malware might be sitting as an innocent-looking file on
disk but the process is whats actively doing damage.

---

## Foreground vs Background processes

**Foreground** — runs while youre watching it. If you run a command in
the terminal and it blocks until its done, thats a foreground process.

**Background** — runs silently without your input. This is where
the interesting stuff lives from a security perspective.

Examples of background processes:
- Web server (Apache, Nginx) — sitting there waiting for HTTP requests
- SSH service — waiting for someone to connect
- Database (MySQL, PostgreSQL) — waiting for queries
- Cron jobs — scheduled tasks that wake up and run on a timer

---

## Why background processes are the most vulnerable

Because theyre always on, always listening, and often forgotten about.

A web server that hasnt been updated in two years is still running
quietly in the background. Nobody is actively watching it. The sysadmin
probably hasnt thought about it since they set it up.

From an attackers perspective these are the targets. Find a background
service thats old, misconfigured, or exposed — thats your way in.

---

## How to see whats running on a linux machine
```bash
ps aux          # shows all running processes
ps aux | grep apache   # filter for specific service
top             # live view of processes
netstat -tulnp  # shows which processes are listening on which ports
```

The last one is particularly useful. It maps processes directly to
ports — so you can see that its apache2 listening on port 80, not
just that something is on port 80.

---

## What i want to explore next

- How attackers hide malicious processes (process injection)
- What a zombie process is
- How to identify suspicious processes on a compromised machine
