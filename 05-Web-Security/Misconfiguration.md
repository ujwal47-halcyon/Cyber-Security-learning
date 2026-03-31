# Day 15 - Misconfiguration

**Date:** 24th January,2025.

---

## What even is misconfiguration

Its not a vulnerability in the code. its not a zero day. its just a system
thats been set up wrong — unsafe, or in a way nobody intended.

The frustrating thing is the system still works fine. everything runs,
nobody notices, and the misconfiguration just sits there quietly until
someone finds it.

---

## Why its dangerous

Misconfiguration basically converts a secure system into an insecure one
without anyone realising. thats what makes it so common in real engagements.

A few things that make it worse:

- misconfigurations look completely normal from the outside
- theyre easy to ignore because nothings broken
- they give attackers shortcuts that wouldnt exist otherwise

An attacker doesnt need to find a fancy exploit if the admin panel is
publicly accessible with default credentials. the misconfiguration
does half the work for them.

---

## Common examples

Things i need to watch for when enumerating a target:

**Default passwords not changed** — probably the most common one.
Routers, admin panels, databases — a lot of them ship with default
credentials that never get changed. admin/admin still works on
more systems than it should.

**Unnecessary services running** — every service thats running but
not needed is just extra attack surface. if its not required, it
shouldnt be on.

**Files readable by everyone** — configuration files, logs, backups
sitting there with world-readable permissions. sometimes containing
credentials or internal details.

**Services running as root** — if you can exploit a service thats
running as root, you dont need to do any privilege escalation.
you're already there.

**Debug or test pages left exposed** — developers forget to remove
these before pushing to production. they often bypass normal
authentication entirely.

---

## Why this matters more than people think

Most real breaches dont start with sophisticated exploits. they start
with someone finding a misconfigured service, an exposed admin panel,
or a default credential that never got changed.

Misconfiguration is consistently in the OWASP top 10 for a reason.
its not glamorous but its everywhere.

---

## What i want to look into next

- Tools for automatically detecting misconfigurations
- Common misconfigurations specific to web apps
- How misconfigurations chain with other vulnerabilities
