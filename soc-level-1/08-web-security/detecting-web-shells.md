# Detecting Web Shells

**Platform:** TryHackMe | **Module:** Web Security | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/detectingwebshells

---
## What This Room Covers

What web shells are, how attackers deploy them, and how to detect them
through log analysis, file system monitoring, and network traffic examination.

---
## Key Concepts Learned

**A web shell is persistent, interactive attacker access through a web application.**
After a successful web attack — file upload vulnerability, RCE through injection —
an attacker uploads a small script to the web server. This script accepts commands
via HTTP and executes them on the server. The attacker now has a persistent
shell that survives reboots and looks like normal web traffic.

**Common Web Shell Examples**

PHP one-liner (the simplest possible web shell):
```php
<?php system($_GET['cmd']); ?>
```

Saved as `image.php` on the server. Attacker accesses:
```
GET /uploads/image.php?cmd=whoami  HTTP/1.1
→ Response: www-data
GET /uploads/image.php?cmd=cat+/etc/passwd  HTTP/1.1
→ Response: root:x:0:0:...
```

The web server executes the command and returns the output in the HTTP response.
From the network, this looks like normal HTTP traffic.

**Web Shell Detection Methods**

**Method 1 — Web Server Access Log Analysis**

Web shell usage leaves distinctive log patterns:
```
GET /uploads/image.php?cmd=whoami  200
GET /uploads/image.php?cmd=id  200
GET /uploads/image.php?cmd=ls+-la  200
GET /uploads/image.php?cmd=cat+/etc/passwd  200
```

Indicators:
- Script file in a directory that should only contain static files (uploads, images)
- Sequential system commands passed as URL parameters
- Short, rapid requests to the same unusual file from one IP
- Requests with shell command syntax in parameters (`ls`, `cat`, `whoami`, `id`, `cmd`, `exec`)

**Method 2 — File System Monitoring**

EDR or file integrity monitoring alerts when new PHP/ASP/JSP files appear in
web-accessible directories — especially upload directories that should never
contain executable scripts.

Key directories to monitor:
- `/var/www/html/uploads/`
- `/tmp/` (sometimes web-accessible)
- Any directory configured for user file uploads

**Method 3 — Network Traffic Analysis**

Web shell responses have a distinctive pattern — the response body contains
command output (system file contents, directory listings, process lists) rather
than normal HTML. In Wireshark, following the TCP stream of a web shell session
reveals operating system information directly in the HTTP response body.

**Common Web Shell File Names Used by Attackers**

Attackers try to blend in:
- Legitimate-looking names: `upload.php`, `image.php`, `config.php`
- Hidden among similar files: `index.php`, `home.php`
- Obfuscated: `a3f8b2.php` (random hash)

File integrity monitoring catches new files regardless of name.

**SIEM Detection for Web Shells**
```spl
index=main sourcetype=access_combined
| where match(uri, "(?i)(cmd=|exec=|system=|passthru=|shell_exec=)")
| table _time, clientip, uri, status
```

---
## Hands-On Tasks

Analyzed web server logs and file system evidence to identify deployed web shells,
traced the initial upload request in logs, identified command execution activity,
and documented the full compromise chain from initial upload through shell usage.

---
## How This Applies to Real SOC Work

Web shell detection is a high-value SOC skill — a deployed web shell represents
persistent attacker access that may have been active for weeks before detection.
Identifying it quickly and tracing back to the initial upload time is critical
for scoping how long the attacker had access and what they accessed.

---
## What I Want to Learn Next Based on This

Detecting Web DDoS covers the volume-based attacks that target availability
rather than confidentiality — a different threat model requiring different detection approaches.
