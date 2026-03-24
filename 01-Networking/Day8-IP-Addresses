# Day 8 - IP Addresses

**Date:** January 7,2026.


## What is an IP address

An IP address is just an address given to a device on a network.
Like a house number — without it, nobody knows where to send the data.

---

## Private vs Public IP

This tripped me up at first so its worth writing down properly.

**Private IP:**
Used inside a network. Your laptop, phone, printer — they all get private
IPs. These never leave your local network and are completely invisible
to the internet.

Common private ranges you'll see constantly:
- 192.168.x.x
- 10.x.x.x
- 172.16.x.x - 172.31.x.x

**Public IP:**
This is what your ISP assigns. The key thing i realised — a public IP
identifies your entire network, not a specific device on it. Your router
holds the public IP. Everything behind it shares it.

Why cant every device have its own public IP? Because theyre running out.
IPv4 only has about 4 billion addresses and the internet has way more
devices than that. So ISPs assign public IPs to networks and NAT handles
the translation internally.

---

## Why this matters for pentesting

When youre doing recon on a target, the public IP is what you start with.
Its the entry point to their network. Everything behind that IP is hidden
behind NAT — finding whats actually running internally is a separate
problem.

When you land on a machine during an engagement and run ifconfig or
ip a, a 192.168 or 10.x address tells you youre inside a private network.
Theres likely more hosts around you worth scanning.

---

## What i want to look into next

- IPv6 and why it matters
- How NAT actually works under the hood
- Subnetting and CIDR notation
