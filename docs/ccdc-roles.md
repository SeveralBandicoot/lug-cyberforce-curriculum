# CCDC Team Roles

**Last updated:** August 2026  
**Owner:** AJ  
**For:** Team captain and competitors finalizing the CCDC roster

---

> **Note:** Roles are organized around skill domains, not individual VMs.
> This means they survive topology changes between seasons and give people
> something concrete to train against before the 2027 team packet is
> released. VM assignments below are based on the 2026 MWCCDC topology and
> will be updated when the 2027 packet is published.

---

## Overview

CCDC fields 4–8 competitors. UIC targets 6. There are five skill-domain
roles. With 6 people, Windows Security gets two — it is the heaviest and
most-targeted role on the team. Every other role is one person.

**The rule that matters most:** every VM is owned by someone. Every role
knows their systems before the drop flag fires. No one is floating.

```
┌──────────────────────┬──────────────────────────────────────────┐
│ Role                 │ Primary VMs (2026 topology)              │
├──────────────────────┼──────────────────────────────────────────┤
│ Windows Security     │ AD/DNS (Server 2019), Web (Server 2019), │
│                      │ FTP (Server 2022), Windows 11 Wks        │
├──────────────────────┼──────────────────────────────────────────┤
│ Linux Security       │ Ubuntu Ecom, Fedora Webmail,             │
│                      │ Ubuntu Workstation                       │
├──────────────────────┼──────────────────────────────────────────┤
│ Network Protection   │ Firewall 1 (Palo Alto), Firewall 2       │
│                      │ (Palo Alto), VyOS Router                 │
├──────────────────────┼──────────────────────────────────────────┤
│ Incident Response    │ Splunk (Oracle Linux) + visibility       │
│                      │ across all systems                       │
├──────────────────────┼──────────────────────────────────────────┤
│ Business & Writing   │ NISE platform — injects, support         │
│                      │ tickets, incident reports                │
└──────────────────────┴──────────────────────────────────────────┘
```

---

## Role Descriptions

### Windows Security

**The red team's primary target. This role gets two people when the roster
allows it.**

Active Directory is the highest-value asset in every CCDC environment. If
the red team owns AD, they own everything that authenticates against it —
which is most of the network. Windows Security is responsible for making
sure that does not happen, and for keeping the Windows-hosted scored services
running while hardening.

**Owns (2026):**
- Windows Server 2019 — AD/DNS
- Windows Server 2019 — Web Server
- Windows Server 2022 — FTP Server
- Windows 11 Workstation

**Responsibilities:**
- Change the built-in Administrator password and rename the account
  immediately at drop flag
- Audit all AD accounts and privileged group memberships — document the
  baseline, then monitor for changes throughout competition
- Lock down Domain Admins, Enterprise Admins, and Schema Admins
- Enforce Group Policy: account lockout policy, password complexity,
  restricted groups, audit logging
- Maintain DNS — forward and reverse zones must keep resolving (POP3
  authenticates via AD; DNS failure cascades into mail scoring)
- Keep the web server serving expected content (HTTP and HTTPS are scored)
- Harden FTP — audit anonymous access, verify required files are present
  (FTP is scored on file presence as well as authentication)
- Harden the Windows 11 workstation without making it unusable (Orange Team
  members act as typical users on workstations)
- Enable and review Windows Event Viewer; forward logs to Splunk

**Skills to have before the Invitational:**
- Active Directory Users and Computers (ADUC) — creating, modifying,
  disabling accounts; managing group membership
- Group Policy Objects — creating, linking, enforcing; know the dangerous
  settings that can lock the team out of the domain if misconfigured
- PowerShell for AD: `Get-ADUser`, `Get-ADGroupMember`,
  `Search-ADAccount -LockedOut`, `Get-ADGroupMember "Domain Admins"`
- Windows Server service hardening: what is running, what should not be
- Windows Firewall with Advanced Security
- IIS or equivalent for web and FTP service configuration
- Common AD attack patterns — what Pass-the-Hash, Kerberoasting, and new
  admin account creation look like in Event Viewer

**If you have 2 people in this role:** one person owns AD/DNS and leads
on Group Policy. The second person owns Web, FTP, and the workstation, and
supports AD tasks as capacity allows.

**If you only have 1 person:** triage ruthlessly. AD/DNS first, web second,
FTP third, workstation last. A broken workstation hurts less than a
compromised domain controller.

---

### Linux Security

**Owns the scored mail and e-commerce services. Two of the most complex
service stacks in the competition.**

Webmail involves SMTP and POP3 — both scored services — running on Fedora.
Ecom involves HTTP/HTTPS on Ubuntu. Both systems have multiple scored
services, which means any misconfiguration during hardening has immediate
scoring consequences.

**Owns (2026):**
- Ubuntu Server 24.04 — Ecom (HTTP/HTTPS)
- Fedora 42 — Webmail (SMTP, POP3)
- Ubuntu Desktop 24.04 — Workstation

**Responsibilities:**
- Change all default credentials immediately (`sysadmin:changeme` on both
  servers)
- Harden SSH across all three systems: disable root login, enforce key-based
  or strong password auth, restrict to named users
- Audit all local users, sudo privileges, cron jobs, and SUID binaries
- Enumerate and disable unnecessary services (`ss -tulnp`, `systemctl`)
- Maintain HTTP/HTTPS on Ecom — content must match what the scoring engine
  expects; do not change web content without understanding the scoring check
- Maintain SMTP and POP3 on Webmail — both are scored continuously
- Configure host-based firewall (`ufw` on Ubuntu, `firewalld` on Fedora)
- Harden the Ubuntu workstation without making it unusable for Orange Team
- Forward logs to Splunk via Universal Forwarder

**Skills to have before the Invitational:**
- Linux command line fluency — file permissions, process management,
  user/group administration
- Service configuration: Apache or Nginx for web; Postfix and Dovecot for
  SMTP/POP3 (Fedora Webmail will be running one of these stacks)
- `ufw` and `firewalld` — know both since the two systems use different distros
- Fedora-specific tooling: `dnf`, `firewalld`, `systemctl`
- Log files: `/var/log/auth.log`, `/var/log/mail.log`, `journalctl`
- Finding persistence: cron jobs (`crontab -l`, `/etc/cron*`), SUID files
  (`find / -perm -4000`), world-writable files, new users in `/etc/passwd`

---

### Network Protection

**Controls the perimeter. If this role fails, the red team has an easier
path into everything else.**

Two Palo Alto firewalls and a VyOS router sit between the competition network
and the outside world. The default credentials on all three are published in
the team packet — meaning the red team has them. Changing those credentials
is the first action this role takes at the drop flag, before anything else.

**Owns (2026):**
- Firewall 1 — Palo Alto PA 11.0.2 (perimeter)
- Firewall 2 — Palo Alto PA 11.0.2 (internal segment)
- VyOS Router 1.4.3

**Default credentials to change immediately:**
- Palo Alto: `admin / Changeme123`
- VyOS: `vyos / changeme`

**Responsibilities:**
- Change credentials on all three devices the moment the drop flag fires —
  before hardening any server
- Understand the full network topology: which VMs are on which segment, what
  the public IP pool is, how NAT maps public to internal addresses
- Configure security policies on both firewalls: what traffic is allowed,
  what is denied, where to log
- Maintain NAT/PAT — the public IP pool assigned to the team requires correct
  NAT configuration for scored services to be reachable by the scoring engine
- Monitor traffic logs on both firewalls throughout competition
- When a red team source IP is confirmed (not guessed), implement a targeted
  block — do NOT block entire subnets or place blanket deny rules at ingress,
  as this risks blocking the scoring engine
- Coordinate with Incident Response on anomalous traffic patterns seen in
  firewall logs
- Alert the team if the scoring engine stops hitting services (may indicate
  a firewall misconfiguration)

**Skills to have before the Invitational:**
- Palo Alto PAN-OS: logging in via web UI and CLI, security policy creation,
  zone configuration, NAT/PAT rules, viewing traffic logs
- VyOS CLI: the commit/save model (changes are not live until committed),
  viewing interfaces and routing tables, basic firewall rules
- TCP/IP and subnetting: comfortable reading the MWCCDC IP table and
  understanding what traffic should flow where
- NAT/PAT: how public-to-private address translation works and how to
  configure it on PAN-OS
- Understanding of application-layer vs. layer-3/4 security policies

**Fastest path to readiness:** Palo Alto's free EDU labs at
[paloaltonetworks.com/services/education](https://www.paloaltonetworks.com/services/education).
Do these before the Invitational. PAN-OS is not intuitive without hands-on
time.

---

### Incident Response

**The team's eyes. Owns Splunk and monitors for red team activity across
all systems throughout competition.**

This role is the only one that does not primarily harden — it watches. While
Windows Security and Linux Security are heads-down on their systems, Incident
Response has visibility across the entire network and surfaces compromises
before they become unrecoverable. IR also writes the formal incident reports
that are worth 10–30% of the total score.

**Owns (2026):**
- Oracle Linux 9.2 / Splunk 10.0.2 (primary tool and a scored VM)
- Visibility across all team systems via log aggregation

**Responsibilities:**
- Change all default credentials on the Splunk VM immediately
  (`root:changemenow`, `sysadmin:changemenow`, `admin:changeme`)
- Keep Splunk operational — it is indirectly scored as the team's monitoring
  infrastructure and a VM the competition expects to be running
- Configure Splunk Universal Forwarder on other VMs to send logs into Splunk
  (coordinate with Windows Security and Linux Security on this)
- Build searches and alerts for key indicators: new local or domain accounts,
  privilege escalation events, failed authentication spikes, unexpected
  outbound connections, new scheduled tasks or cron jobs
- Monitor Splunk continuously throughout competition and call out anomalies
  to the team immediately
- When a compromise is detected: document source IP, destination, timeline,
  and affected systems — then hand off the incident report to Business &
  Writing or draft it directly
- Track which red team actions have been detected so incident reports are
  accurate and complete

**Skills to have before the Invitational:**
- Splunk SPL basics: `index=*`, field extraction, `stats`, `table`,
  `timechart`, `where`, `search`
- Splunk alert creation: threshold-based alerts for authentication failures,
  new account creation, privilege changes
- Splunk Universal Forwarder installation and configuration on Linux and
  Windows (so you can get logs from other VMs into Splunk)
- Reading Windows Event IDs: 4624 (logon), 4625 (failed logon), 4720 (new
  account), 4728/4732 (group membership change), 4672 (special privileges)
- Reading Linux auth logs: failed SSH, su/sudo usage, new users in passwd
- Knowing what normal looks like so anomalies stand out

**Free training:** Splunk's free courses at
[education.splunk.com](https://education.splunk.com) — start with Intro to
Splunk and then Search Under the Hood.

---

### Business & Writing

**Owns the inject pipeline. Injects are worth 35–50% of the total score.
This role protects that bucket.**

Every inject that drops on NISE needs to be read immediately, assigned or
written, and submitted as a business memo PDF before the deadline. Under
competition pressure, inject responses pile up fast. This role makes sure
none are missed and all are submitted in the correct format.

This is not a secondary role. A technically excellent team that ignores
injects will lose to a balanced team with weaker defense but strong inject
completion. Business & Writing is why that does not happen to UIC.

**Owns:**
- NISE platform — monitoring, inject intake, submission tracking
- All Support Tickets (password change reports, tech support, scoring
  inquiries)
- Inject response drafting and PDF submission
- Incident report writing (in coordination with Incident Response)
- Team communication with the White Team

**Responsibilities:**
- Log into NISE immediately and respond to the Welcome inject before the
  drop flag
- Monitor NISE continuously — refresh manually since it does not always
  auto-update
- Read every inject the moment it drops; assess deliverables; either draft
  the response or delegate to the most relevant role and set a follow-up
- Track all open inject deadlines — know what is due when at all times
- Write business memos in the correct format (see
  [inject-response-template.md](../drills/inject-response-template.md))
- Submit responses as PDF attachments unless the inject specifies otherwise
- If an inject is marked invalid for resubmission, fix and resubmit
  immediately
- File Support Tickets for every scored service password change — no
  exceptions — and track which ones have been filed
- Draft incident reports when Incident Response surfaces a compromise;
  IR provides the technical details, Business & Writing structures and
  submits the memo
- Maintain a running log of what has been submitted, what is pending, and
  what has been scored invalid

**Skills to have before the Invitational:**
- Business memo format — not a technical report (see
  [inject-response-template.md](../drills/inject-response-template.md))
- Writing clearly under time pressure: lead with conclusions, plain English
  in the body, technical detail in labeled appendices
- Non-serif font throughout (Arial, Calibri, Verdana); consistent formatting
- PDF creation from a text or word processor document
- Enough technical literacy to understand what Windows Security, Linux
  Security, and IR are telling you and translate it into a business memo

**Who should fill this role:**
The person with the strongest written communication skills and the ability
to stay organized while everything around them is on fire. This does not have
to be the most technical person — it has to be the most reliable writer and
the best multitasker. The team captain is a natural fit.

---

## Shared Responsibilities (Everyone)

Regardless of role, every team member does these things:

**Credential changes → tell Business & Writing immediately.**
Any scored service password change needs a Support Ticket filed before you
move on. Tell the B&W person the service name, the VM, and the new credential
so they can file it.

**Call out compromises verbally.**
The moment you see red team activity — a new account, an unexpected process,
an anomalous connection — say it out loud. Do not silently handle it. The
whole team needs situational awareness.

**Log your changes.**
Keep a running note of what you changed and when. If a service breaks after
a config change, you need to roll it back quickly. You will not remember the
details under pressure unless you wrote them down.

**Check NISE on your own account.**
Everyone has a NISE login. Business & Writing leads on injects, but everyone
should be aware of what has dropped and what is open.

---

## Sizing the Roster

**6 people (target):**
Windows Security gets 2. All other roles get 1. This is the ideal
configuration — Windows Security is the most demanding role and benefits
most from a second person.

**5 people:**
Windows Security gets 1. That person owns all four Windows VMs and will be
stretched thin. Incident Response doubles as support for Linux Security when
Splunk is stable. Prioritize AD/DNS and the web server; FTP and the
workstation are lower priority.

**4 people (minimum to compete):**
Windows Security and Linux Security each get 1. Network Protection and
Incident Response merge into one person (this is very hard — prioritize
firewall credentials and Splunk setup, then choose one to actively monitor).
Business & Writing is the captain, also handling their own system area as
capacity allows. At 4 people, triage is everything — protect scored services
first, everything else second.

---

## Pre-Invitational Roster Checklist

Before the first Invitational, confirm:

- [ ] All 5 roles assigned; Windows Security has 2 people if roster allows
- [ ] Every person knows their systems: OS, default credentials, what
      services run on them
- [ ] Network Protection has completed at least basic PAN-OS lab work
- [ ] Incident Response has completed basic Splunk SPL training
- [ ] Windows Security is comfortable with ADUC and Group Policy basics
- [ ] Business & Writing has read inject-response-template.md and drafted
      at least one practice memo
- [ ] Team has agreed on verbal protocols: how to call out compromises, how
      to flag inject deadlines, how to request cross-role help
- [ ] Everyone knows the NISE login workflow and has their account credentials

---

## See Also

- [ccdc101.md](../../docs/ccdc101.md)
- [shared-foundations.md](../../docs/shared-foundations.md)
- [ccdc-scoring-guide.md](../../docs/ccdc-scoring-guide.md)
- [2026-mwccdc-topology.md](../topology/2026-mwccdc-topology.md)
- [inject-response-template.md](../drills/inject-response-template.md)
- [service-checklist.md](../drills/service-checklist.md)