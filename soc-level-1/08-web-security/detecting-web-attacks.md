# Detecting Web Attacks

**Platform:** TryHackMe | **Module:** Web Security | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/detectingwebattacks

---
## What This Room Covers

Identifying web attack signatures in HTTP access logs and network traffic —
recognizing SQL injection, XSS, directory traversal, and brute force attempts
through log and packet analysis.

---
## Key Concepts Learned

**Web attacks leave signatures at multiple levels — HTTP logs, network traffic, and application logs.**
The same attack looks different depending on which data source you examine.
Understanding all three gives a complete picture.

**SQL Injection Signatures in Web Logs**

SQLmap and manual SQLi attempts generate distinctive URL patterns:
```
GET /page.php?id=1'--  HTTP/1.1
GET /page.php?id=1 AND 1=1--  HTTP/1.1
GET /page.php?id=1 UNION SELECT NULL--  HTTP/1.1
GET /page.php?id=1 ORDER BY 5--  HTTP/1.1
```

Key indicators:
- SQL keywords (`SELECT`, `UNION`, `AND`, `OR`, `DROP`, `INSERT`) in URL parameters
- Single quotes (`'`) in URL parameters
- Double dashes (`--`) or hash (`#`) in URL parameters — SQL comment syntax
- Rapid sequential requests with slight parameter variations from one IP
- Mix of HTTP 200 and HTTP 500 responses to the same endpoint

**XSS Signatures**
```
GET /search?q=<script>alert(1)</script>  HTTP/1.1
GET /page?name=<img src=x onerror=alert(1)>  HTTP/1.1
```

Look for: HTML tags (`<script>`, `<img>`, `<iframe>`) in URL parameters or
POST bodies, JavaScript event handlers (`onerror=`, `onload=`, `onclick=`).

**Directory Traversal Signatures**
```
GET /page.php?file=../../../../etc/passwd  HTTP/1.1
GET /page.php?file=..%2F..%2F..%2Fetc%2Fshadow  HTTP/1.1
```

Look for: `../` sequences, URL-encoded traversal sequences (`%2F` = `/`),
requests for system files (`/etc/passwd`, `/windows/win.ini`).

**Directory Enumeration (Brute Force)**
Tools like DirBuster and Gobuster rapidly request many paths:
```
GET /admin  404
GET /admin.php  404
GET /administrator  404
GET /wp-admin  200  ← found
GET /backup  404
GET /config  404
```

Signature: Hundreds of 404 responses from one IP in a short window,
followed by occasional 200 or 403 responses. The 403s are as interesting
as the 200s — forbidden means the path exists.

**Correlating web logs with SIEM**

The web log analysis workflow in Splunk:
```spl
index=main sourcetype=access_combined
| stats count by clientip, status
| where status=500
| sort -count
```

High 500 count from one IP = likely injection testing.

```spl
index=main sourcetype=access_combined uri="*UNION*" OR uri="*SELECT*" OR uri="*DROP*"
| table _time, clientip, uri, status
```

Direct SQLi keyword detection in URI fields.

---
## Hands-On Tasks

Analyzed real web server access logs — identified SQL injection campaigns,
XSS attempts, directory traversal, and brute force attacks using log patterns
and SIEM-style queries. Classified each attack type and documented the evidence.

---
## How This Applies to Real SOC Work

Web attack alerts are one of the highest-volume alert categories in most SOCs.
The ability to quickly classify a web attack type from log evidence — is this
SQLi, XSS, enumeration, or credential brute force? — determines the correct
investigation path and escalation decision.

---
## What I Want to Learn Next Based on This

Detecting Web Shells covers post-exploitation web activity — what happens
after a successful web attack when the attacker deploys a persistent access mechanism.
