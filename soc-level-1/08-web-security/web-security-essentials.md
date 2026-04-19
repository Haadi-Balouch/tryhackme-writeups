# Web Security Essentials

**Platform:** TryHackMe | **Module:** Web Security | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/websecurityessentials

---
## What This Room Covers
How the web works at a security level — HTTP, web application architecture,
common vulnerability categories, and the protective controls that defend
against them.

---
## Key Concepts Learned

**The web is the largest attack surface most organizations have.**
Every public-facing web application is reachable by anyone on the internet.
Understanding how web applications work — at the HTTP level, not just as
something you browse — is foundational for detecting web-based attacks in
SIEM and network logs.

**HTTP Request/Response Cycle**
Every web interaction is a request and a response:
```
Client sends:                    Server responds:
GET /login.php HTTP/1.1          HTTP/1.1 200 OK
Host: example.com                Content-Type: text/html
Cookie: session=abc123           Set-Cookie: session=xyz789
User-Agent: Mozilla/5.0          <html>...page content...</html>
```

Every field in these exchanges is visible in web server logs and proxy logs —
and every field can be manipulated by an attacker. This is what makes web
log analysis rich with forensic evidence.

**OWASP Top 10 — The Standard Vulnerability Catalog**

| Vulnerability | What It Is | SOC Detection Approach |
|---|---|---|
| Injection (SQLi, CMDi) | Unsanitized input executed as code | SQL keywords in URL params, HTTP 500 errors |
| Broken Authentication | Weak session management, credential flaws | Brute force patterns, session token reuse |
| XSS | JavaScript injected into pages | `<script>` tags in URL params or POST bodies |
| IDOR | Accessing other users' resources by changing IDs | Sequential ID enumeration in access logs |
| Security Misconfiguration | Default credentials, unnecessary features exposed | Access to admin panels, default page requests |
| Vulnerable Components | Outdated libraries with known CVEs | Requests targeting known vulnerable endpoints |
| SSRF | Server making requests to internal resources | Requests with internal IP addresses in parameters |

**Web server logs — what a SOC analyst reads**

A typical Apache/Nginx access log line:
```
192.168.1.5 - - [19/Apr/2026:14:23:01] "GET /admin.php HTTP/1.1" 403 512 "-" "sqlmap/1.7"
```

This single line tells me: source IP, timestamp, what was requested, HTTP status
(403 = forbidden), response size, and the User-Agent (sqlmap — automated SQL injection
tool). That User-Agent alone confirms this is an automated attack.

**HTTP Status Codes for SOC Analysis**

| Code | Meaning | Attack Context |
|---|---|---|
| 200 | Success | Attacker request succeeded — investigate further |
| 301/302 | Redirect | May indicate URL manipulation |
| 400 | Bad Request | Malformed requests — fuzzing or testing |
| 401/403 | Unauthorized/Forbidden | Access attempts to protected resources |
| 404 | Not Found | Enumeration of paths/files |
| 500 | Internal Server Error | Possible injection — server-side code error |

A burst of 404s from one IP followed by a 200 is a classic pattern: directory
enumeration finding a valid path.

---
## Hands-On Tasks

Explored web application architecture, examined HTTP requests and responses,
reviewed common vulnerability categories, and analyzed web server log samples
for attack indicators.

---
## How This Applies to Real SOC Work

Web application attacks are among the most common alerts in any SOC queue.
SQLmap, Nikto, directory brute forcing, and credential stuffing all leave
distinctive signatures in web server logs. Understanding the HTTP layer means
recognizing these signatures immediately rather than needing to look them up.

---
## What I Want to Learn Next Based on This

Detecting Web Attacks builds directly on this foundation — applying the
vulnerability knowledge to real log analysis scenarios.
