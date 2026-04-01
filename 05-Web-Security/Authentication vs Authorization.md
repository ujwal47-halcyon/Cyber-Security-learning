# Day 16 - Authentication vs Authorization

**Date:** 24 January,2026.

---

## The difference nobody explains properly

these two words get used interchangeably and they shouldnt.

**Authentication** — who are you?
**Authorization** — what are you allowed to do?

thats it. two different questions. two different checks.

---

## Authentication

its how a system verifies your identity. proves youre actually who
you claim to be.

three ways systems do this:

- **Password** — something you know
- **OTP/Token** — something you have
- **Biometrics** — something you are

the login screen on any website is authentication. youre proving
your identity before the system lets you in.

---

## Authorization

happens after authentication. once the system knows who you are,
authorization decides what youre allowed to access.

the admin panel is authorization. you might be logged in (authenticated)
but that doesnt mean youre allowed to access /admin. thats a
separate check.

**Real example:**
- Login screen = authentication
- Admin panel access = authorization

two completely separate things even though they happen back to back.

---

## Why the distinction matters for pentesting

a lot of vulnerabilities come from applications getting these mixed up
or implementing one correctly and completely botching the other.

**Broken authentication** — session tokens that dont expire, weak
password policies, no brute force protection on login endpoints.
this is how account takeover happens.

**Broken authorization** — being logged in as a normal user and being
able to access /admin just by typing the URL. the app checked that
you were authenticated but forgot to check if you were actually
authorized to be there.

IDOR (Insecure Direct Object Reference) is a classic authorization
failure. you change the user id in a URL from 123 to 124 and suddenly
youre looking at someone elses data. the app authenticated you fine —
it just never checked if you were allowed to see that specific resource.

---

## Trust issues

this is where things get interesting. security breaks down when a
system trusts things it shouldnt:

- **Trusting user input** — never. user input is always potentially
  malicious. sanitize everything.

- **Trusting cookies blindly** — cookies can be modified. if authorization
  logic relies on a cookie value without verifying it server side,
  thats a problem.

- **Trusting that a logged in user is who they say they are** — sessions
  can be hijacked. a valid session token doesnt always mean the
  legitimate user is on the other end.

- **Trusting requests from internal network** — just because a request
  comes from inside the network doesnt mean its safe. thats the
  assumption SSRF exploits.

---

## What i want to dig into next

- How session tokens actually work and how they get stolen
- IDOR in detail — finding and exploiting it
- How OAuth gets misconfigured
- JWT tokens and their common vulnerabilities
