# Windows Threat Detection 3

**Platform:** TryHackMe
**Path:** Windows Security Monitoring
**Module:** 09 — Windows Security Monitoring
**Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/windowsthreatdetection3

---

## What This Room Covers

How attackers maintain persistent access to compromised Windows hosts — C2 implants,
backdoor accounts, Windows services, scheduled tasks, and startup folder abuse.

---

## Key Concepts Learned

**Persistence is what turns a one-time breach into a long-term threat.**
Without persistence, the attacker loses access at the next reboot. With persistence,
they can return days, weeks, or months later — even if the initial infection vector
is closed. This room covered every major Windows persistence technique.

**C2 Malware Placement — Blending In**
The C2 implant was hidden at `C:\Users\Administrator\AppData\Roaming\update.exe` —
a path that looks like a legitimate application update. AppData\Roaming is a
standard location for user-space application data, making it a common hiding spot.
The domain `route.m365officesync.workers.dev` impersonates Microsoft 365 infrastructure.
Both the file location and domain name are chosen specifically to blend with
legitimate traffic.

**Backdoor Account Creation Pattern**
After RDP brute force (6 failed attempts → 1 success), the attacker created
a user named `support` and added it to Administrators. The name `support`
is deliberately chosen to appear like a legitimate IT account.

**Windows Persistence Mechanisms Covered**

| Mechanism | Technique | Detection Event |
|---|---|---|
| Windows Service | Malware registered as a service | Sysmon Event ID 6 (Driver loaded) or System log 7045 (New service) |
| Scheduled Task | Task created to run malware on schedule | Sysmon Event ID 1 with schtasks.exe or Security Event 4698 |
| Startup Folder | Executable placed in startup folder | Sysmon Event ID 11 (File created) in startup path |
| Registry Run Key | HKCU/HKLM Run key modified | Sysmon Event ID 13 (Registry value set) |

**Ransomware — the most impactful persistence outcome**
The room ended with the strategic point: ransomware is the most destructive
outcome of a Windows breach, and the best time to stop it is at Initial Access
— not at encryption. Every persistence mechanism detected is a ransomware attack
that never reached its final stage.

---

## Task Answers

| Question | Answer |
|---|---|
| Suspicious archive downloaded | `URGENT!.zip` |
| C2 malware file location | `C:\Users\Administrator\AppData\Roaming\update.exe` |
| C2 domain | `route.m365officesync.workers.dev` |
| Failed login attempts before success | `6` |
| Backdoor user created | `support` |
| Privileged group backdoor user added to | `Administrators` |
| Windows service created to persist Nessie malware | `Data Protection Service` |
| Scheduled task created to persist Troy malware | `AmazonSync` |
| Flag from running Troy malware | `THM{c2_is_on_schedule!}` |
| Parent process image of "Odin" malware | `c:\windows\explorer.exe` |
| Last line Odin malware outputs | `Done doing bad stuff!` |
| Flag from running Kitten malware | `THM{persisting_in_basket!}` |
| Biggest threat to corporate Windows networks | `Ransomware` |
| Best stage to detect and stop the attack | `Initial Access` |

---

## Key Concepts for SOC Work

**AppData\Roaming is a standard persistence hiding spot — monitor it.**
Sysmon file creation events (Event ID 11) in `C:\Users\*\AppData\Roaming\` for
executable file types (`.exe`, `.dll`, `.bat`, `.ps1`) are worth alerting on,
especially when the creating process is not a known application installer.

**Scheduled task names that impersonate Microsoft services are a red flag.**
`AmazonSync` in a Windows environment that does not use Amazon services has no
legitimate reason to exist. A detection rule filtering for new scheduled tasks
with names matching common vendor names is a practical, low-noise alert.

---

## What I Want to Learn Next Based on This

This completes the Windows Security Monitoring module. The Linux Security Monitoring
module applies the same detection thinking to Linux systems — different log sources,
similar attacker TTPs.
