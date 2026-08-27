# Shared Foundations — CyberForce to CCDC

**Last updated:** August 2026  
**Owner:** AJ  
**For:** CyberForce competitors transitioning into CCDC prep

---

## What This Document Is

This is not a full curriculum. It is a map — specifically, a map of which
skills you built in CyberForce carry directly into CCDC, which ones need to
be extended, and which ones you need to build from scratch.

If you competed in CyberForce, you are not starting from zero for CCDC. But
you are not ready either. Use this document to understand the gap and focus
your prep time on what actually matters.

---

## Skills That Transfer Directly

These are things CyberForce teaches well that CCDC tests in the same or very
similar ways. If you did the work in CyberForce prep, you have these.

### Linux System Hardening
CyberForce gives you hands-on time with Linux servers under real scoring
pressure. CCDC's Linux machines (Ubuntu Ecom, Fedora Webmail, Oracle/Splunk)
require the same fundamentals:

- User and group management (`/etc/passwd`, `/etc/shadow`, `usermod`, `groupmod`)
- File permission auditing (`find / -perm -4000`, world-writable files)
- Service enumeration and disabling (`systemctl`, `ss -tulnp`)
- SSH hardening (`PermitRootLogin no`, key-only auth, `AllowUsers`)
- Host-based firewall rules (`ufw`, `iptables`, `firewalld`)
- Log review (`/var/log/auth.log`, `/var/log/syslog`, `journalctl`)

The difference in CCDC: you do all of this in the first 30 minutes while the
red team is already on the network. Speed matters more than thoroughness.

### Windows System Hardening
CyberForce identified Windows as UIC's biggest gap in 2025. If the team did
genuine Windows prep, those skills carry over:

- Local user and group management
- Windows Firewall with Advanced Security
- Service hardening and disabling unnecessary services
- Event Viewer for log review
- Password policy via Local Security Policy

The difference in CCDC: Windows Server 2019 (AD/DNS and Web) and Server 2022
(FTP) are in scope, not just workstations. Server hardening has additional
considerations that desktop hardening does not.

### Network Fundamentals
CyberForce teaches you to think about network segmentation, firewall rules,
and port-level service exposure. That foundation carries directly:

- TCP/IP addressing and subnetting
- Port/service mapping (what runs on 22, 25, 53, 80, 443, 21, 69, 123)
- Reading and writing firewall rules
- Using nmap for service enumeration
- Understanding what "scoring engine traffic" looks like vs. red team traffic

### Incident Response Basics
CyberForce includes anomaly response and some incident documentation. The
mindset transfers:

- Identifying indicators of compromise (unusual processes, new accounts,
  modified files, unexpected outbound connections)
- Documenting what happened before trying to fix it
- Distinguishing between red team activity and scoring engine traffic

### Service Availability Mindset
CyberForce scores uptime (Orange Team checks services throughout competition
day). CCDC scores uptime continuously via an automated scoring engine with
SLA penalties. The core lesson — "don't break services while hardening" —
is the same. The stakes in CCDC are higher because penalties accrue faster.

### Working Under Pressure
This is the most underrated transferable skill. If you competed in CyberForce,
you know what it feels like to defend systems while injects are dropping and
the clock is running. That experience is real preparation. CCDC is harder and
longer (two full days vs. one), but the mental model is the same.

---

## Skills That Transfer But Need Extension

These are things CyberForce touches but CCDC goes significantly deeper on.
You are not starting from zero, but you cannot rely on CyberForce prep alone.

### Firewall Configuration
**CyberForce:** host-based firewalls (ufw, Windows Firewall) on individual
machines.  
**CCDC:** two Palo Alto PA-11.0.2 firewalls at the network perimeter. This
is a completely different tool with a different management interface, rule
structure, and capability set.

What to extend: learn PAN-OS basics (security policies, NAT/PAT rules, zones,
interfaces). The Palo Alto EDU free labs are the fastest path. See
[palo-alto-primer.md](../topology/palo-alto-primer.md) when it is published.

### Log Monitoring
**CyberForce:** basic log review on individual machines.  
**CCDC:** Splunk is a scored VM in the 2026 topology and a major tool
throughout competition. The Splunk instance needs to be kept alive (it is a
scored service indirectly) and used actively to detect red team activity.

What to extend: learn basic Splunk queries (SPL), how to set up log forwarders
from other machines, and how to create alerts for suspicious activity. Splunk
offers free training at [education.splunk.com](https://education.splunk.com).

### Documentation and Communication
**CyberForce:** C-Suite briefing video, some inject responses.  
**CCDC:** business memos for nearly every inject, submitted as PDFs under
time pressure, worth up to 50% of your total score.

What to extend: practice writing business memos specifically. See
[inject-response-template.md](../drills/inject-response-template.md). The
format is genuinely different from what CyberForce asks for and requires
deliberate practice.

### Team Communication Protocols
**CyberForce:** team coordination matters but the environment is less chaotic.  
**CCDC:** six people defending different systems simultaneously for nine hours
on Day 2, with injects dropping throughout. Without explicit communication
protocols, teams talk over each other, duplicate work, or miss compromises
entirely.

What to extend: establish before competition who owns what system, how
compromises get called out, and who handles injects vs. defense at any given
moment. This cannot be figured out on competition day.

---

## Skills You Need to Build from Scratch

These do not appear in CyberForce in any meaningful way. Budget the most prep
time here.

### Active Directory
AD/DNS (Windows Server 2019) is central to every CCDC environment and is one
of the red team's primary targets. CyberForce's network does not include AD
in the same way.

What you need to know:
- Domain structure: forests, domains, OUs
- User and group management via Active Directory Users and Computers (ADUC)
- Group Policy Objects (GPOs): creating, linking, enforcing
- DNS integration: how AD-integrated DNS works, forward/reverse lookup zones
- Common AD attack vectors: password spraying, Kerberoasting, Pass-the-Hash,
  DCSync — know what they look like in logs, not how to execute them
- Defensive GPOs: account lockout policy, restricted groups, LAPS
- PowerShell for AD: `Get-ADUser`, `Get-ADGroupMember`, `Search-ADAccount`

Start here before anything else. Active Directory is the single largest
knowledge gap between CyberForce veterans and CCDC readiness.

### Palo Alto Firewall (PAN-OS)
Two Palo Alto firewalls sit at the perimeter of the 2026 CCDC network. The
default credentials are `admin/Changeme123` — changing these is the first
thing you do after the drop flag. If you do not, the red team will.

What you need to know:
- Logging into PAN-OS via web UI and command line
- Security policy basics: zones, rules, allow/deny
- NAT/PAT configuration (the public IP pool in CCDC requires NAT)
- Viewing and interpreting traffic logs
- Resetting to known-good state if compromised

See [palo-alto-primer.md](../topology/palo-alto-primer.md) when published.

### VyOS Router
The VyOS router sits above both firewalls and handles external routing.
Default credentials are `vyos/changeme`. It is less of a target than the
firewalls but still needs its credentials changed and its configuration
understood.

What you need to know:
- VyOS CLI basics (it uses a commit/save model, not live edits)
- Viewing routing tables and interfaces
- Basic firewall rules at the router level

### Incident Report Writing
CCDC requires formal incident reports for every red team compromise you
detect. These are different from CyberForce anomaly write-ups — they need
specific structure (source/destination IPs, timeline, affected systems,
remediation plan) and are scored on accuracy and thoroughness.

See [incident-report-template.md](../drills/incident-report-template.md)
when published.

### NISE Platform
CyberForce uses its own scoring system. CCDC uses NISE (National Inject
Scoring Engine) for all communication with judges, inject submission, and
service status. It is browser-based and straightforward, but your team needs
to know it cold before competition day — especially the password change
support ticket workflow.

---

## The One-Sentence Summary

CyberForce gives you the mindset and the Linux/Windows fundamentals. CCDC
tests those fundamentals faster and harder, adds Active Directory and Palo
Alto firewalls as major new domains, and makes business communication worth
half your score.

---

## See Also

- [ccdc101.md](../../docs/ccdc101.md) — full CCDC overview
- [inject-response-template.md](../drills/inject-response-template.md)
- [2026-mwccdc-topology.md](../topology/2026-mwccdc-topology.md)
- [ccdc-roles.md](../../docs/ccdc-roles.md) — how to split the team