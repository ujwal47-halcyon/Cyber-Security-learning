# Day 17 - User Input

**Date:** 

---

## What is user input

Any data the user can control. thats the definition.

Form fields, URLs, search boxes, file uploads, cookies — if the user
can modify it, it counts as user input. and if the application
processes it without checking it properly, thats where things
go wrong.

---

## Why its dangerous

Applications make assumptions. thats the core problem.

They assume users behave correctly. they assume input is honest.
they assume input follows the rules they designed for.

Attackers do the exact opposite. they break assumptions, send
unexpected input, and test boundaries. the whole job is finding
places where the application trusted something it shouldnt have.

More user control = more risk. less validation = more abuse.
thats the relationship.

---

## Where attackers look

Two categories of places worth targeting:

**Places where input affects logic:**
- Login forms (authentication bypass)
- Search boxes (SQLi, XSS)
- Any field that triggers server-side processing

**Places where input affects files, queries or permissions:**
- File uploads (can you upload a shell?)
- URL parameters (can you access someone elses data by changing an ID?)
- Cookies (can you tamper with your own session to escalate privileges?)

---

## The attacker mindset here

Every input field is a question — what happens if i send something
the developer didnt expect?

What happens if i put SQL syntax in the username field?
What happens if i upload a .php file instead of an image?
What happens if i change my user ID in the URL from 42 to 43?

Most developers build for normal users. they dont build for someone
actively trying to break their assumptions. thats the gap attackers
exploit.

---

## What i want to look into next

- SQL injection in detail
- XSS and why its still relevant
- File upload vulnerabilities
- How input validation actually works and how to bypass it
