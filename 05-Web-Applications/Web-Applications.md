# Day 12 - Web Applications

**Date:** January 23,2026.

---

## What is a web application

A web app is software running on a server that you access through
a browser. Thats it. You type a URL, your browser talks to a server,
the server sends back a response, your browser renders it.

The reason this matters for pentesting is that web apps are the
largest attack surface most organisations expose to the internet.
Not SSH, not databases — the website. Because websites are
intentionally public.

---

## Whats actually happening behind the scenes

When you load a web page theres a whole stack sitting behind it:

- A **server** (Apache, Nginx, IIS) handling your request
- A **process** running the application code
- **Open ports** (80 for HTTP, 443 for HTTPS) accepting connections
- **Files on disk** — the application code, configs, sometimes
  sensitive data
- Often a **database** storing user data, credentials, content

Each of these is a potential attack surface. The web app is the
front door — but the interesting stuff is usually further in.

---

## How browser and server talk

The browser and server communicate using HTTP/HTTPS.
Its a set of rules — request and response.

Browser sends: "GET /login HTTP/1.1"
Server responds: here's the login page

HTTPS is just HTTP with TLS encryption on top. The traffic looks
the same structurally, you just cant read it in transit without
the keys.

---

## Why web apps are such a big attack surface

Four reasons:

1. **Public** — exposed to the entire internet by design
2. **Complex** — lots of code, lots of moving parts, more chances
   for mistakes
3. **User interaction** — anywhere users can input data is a
   potential injection point
4. **Often insecure** — built fast, not always reviewed for security

The combination of being public and complex is what makes web apps
the bread and butter of most real pentesting engagements.
SQLi, XSS, IDOR, authentication bypass — all of these live here.

---

## What i want to dig into next

- HTTP request/response structure in detail
- What Burp Suite actually does to these requests
- Common web vulnerabilities and where they come from
- How cookies and sessions work (and how they get stolen)
