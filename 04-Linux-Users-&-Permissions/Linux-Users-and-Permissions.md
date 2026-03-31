# Day 11 - Linux Users and Permissions

**Date:** january 24,2026

---

## Why this matters before anything else

Every time you land on a linux machine the first thing you check is
who you are. What user. What permissions. Because everything you can
do — every command, every file, every service — depends on that.

---

## Two types of users

**Normal user:**
- Limited permissions
- Cant change system-wide settings
- One mistake doesnt take down the whole system
- This is almost always where attackers start after getting initial access

---

**Root:**
- Unlimited permissions
- Can change anything system-wide
- One mistake can destroy everything
- Can read, write, delete any file on the system

---

The entire goal of privilege escalation is moving from the first
category to the second.

---

## Groups

Linux uses groups to manage permissions across multiple users at once.
Instead of setting permissions individually for every user, you put
users in a group and assign permissions to the group.

Makes administration cleaner and reduces accidental exposure —
if someone doesnt need access to something, they just arent in
that group.

From a pentesting angle, groups are worth checking immediately.
The `id` command shows you which groups your current user belongs to.
Being in certain groups (docker, sudo, disk, lxd) can be an instant
privesc path even without being root.

---

## Privilege — the core concept

Normal user = limited privilege
Root = unlimited privilege

Thats the whole game in linux post-exploitation. You come in as a
low-privilege user and look for a path to root.
```bash
id                  # who am i, what groups
sudo -l             # what can i run as root
find / -perm -4000  # find SUID binaries
cat /etc/passwd     # list all users on the system
```

Every privesc technique is just a different answer to the same
question — how do i get from here to root?

---

## What i want to explore next

- SUID/SGID binaries in detail
- How group membership leads to privesc (docker, lxd)
- Reading /etc/passwd and /etc/shadow
- What writable files owned by root actually mean
