
# Day 18 - Enumeration Mindset

**Date:** 26 January, 2026.

---

## What enumeration actually is

Enumeration is the process of gathering information about a system to
understand what exists and how its configured.

Not guessing. not assuming. actually finding out.

You cannot exploit what you dont know exists. thats the whole reason
enumeration comes before everything else. skip it and youre flying blind.

---

## What enumeration does for you

Three things:

- Reduces guessing — you work with facts not assumptions
- Cuts out noise — you focus on whats actually there
- Points you toward the right attack path — different findings
  lead to completely different approaches

A good enumeration phase makes everything after it easier.
a bad one wastes hours chasing things that dont exist

---

## The questions i should be asking

i broke this down into three areas in my notes and i think its
a useful way to think about it:

**Network:**
- What IPs are reachable?
- What ports are open?
- What services are running on those ports?

**System** (once you have access or are doing internal assessment):
- Who am i? what user, what permissions?
- What processes are currently running?
- What files can i read or write?

**Web:**
- What inputs do i control?
- What pages exist that arent linked publicly?
- What actions require login and what dont?

Every single one of these is a question that has a tool or technique
behind it. nmap answers the network questions. gobuster answers the
web questions. id, ps aux, find answer the system questions.

---

## Why this order matters

You enumerate the network first to find the attack surface.
then you enumerate specific services to understand whats running.
then if youre testing a web app you enumerate the application itself.

Going deep on one thing before youve mapped the surface is a
common beginner mistake. i want to get the habit of being
systematic about this from the start.

---

## Day 19 note

Day 19 was a lab day — applying enumeration practically rather than
theory. no separate notes for it, the concepts carry over from here.

---

## What i want to practice

- Running a full enumeration workflow on a THM/HTB machine
- Building a checklist i can follow consistently on every target
- Getting faster at reading nmap output and deciding what to
  investigate next
