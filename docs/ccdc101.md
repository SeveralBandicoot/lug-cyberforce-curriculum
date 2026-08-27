# CCDC 101 — What Is It?

**Last updated:** August 2026  
**Owner:** AJ  
**For:** Everyone on the CyberForce roster considering CCDC

---

> **2026 Note:** NCCDC is transitioning from UTSA/CIAS to the
> [National Cyber Readiness Foundation (NCRF)](https://ccdc.io) starting
> with the 2027 season. The competition structure is expected to stay the
> same. Monitor [ccdc.io](https://ccdc.io) and
> [caeepnc.org/mwccdc](https://www.caeepnc.org/mwccdc/) for official 2027
> updates. **Registration opens October 1, 2026.**

---

## Quick Answer

**CCDC is a live collegiate cyber defense competition where your team defends
a business network against a professional red team — in real time, for two
full days.**

Unlike CyberForce, there is no prep period where you quietly harden systems
before competition day. The red team is active from the moment the drop flag
fires. You defend, respond to business tasks, and write incident reports all
at the same time.

---

## Who Is Eligible

**CCDC at UIC is not separately recruited.** The CCDC roster is drawn
exclusively from people competing in CyberForce. If you are on the
CyberForce roster and want to compete in CCDC, you are the target audience
for this document.

Team size is 4–8 members (minimum 4 to compete). UIC targets 6 people for
an effective split of roles.

---

## How It Works

### The Scenario

Each year CCDC creates a fictional company scenario. Your team plays the role
of IT professionals newly hired to manage that company's network. You inherit
systems that are not properly secured, and your job is to lock them down,
keep services running, and respond to business requests — all while a
professional red team actively tries to break in and kick you out.

### The Environment (Based on 2026 MWCCDC)

The 2026 competition used 11 virtual machines across two network segments,
managed via NETLAB+ and Proxmox. The specific stack:

| VM | OS | Role |
|---|---|---|
| Ubuntu Ecom | Ubuntu Server 24.04 | E-commerce server |
| Fedora Webmail | Fedora 42 | Webmail (email) |
| Splunk | Oracle Linux 9.2 / Splunk 10.0.2 | Log monitoring |
| Ubuntu Workstation | Ubuntu Desktop 24.04 | User workstation |
| Windows Server AD/DNS | Server 2019 | Active Directory + DNS |
| Windows Server Web | Server 2019 | Web server |
| Windows Server FTP | Server 2022 | FTP server |
| Windows Workstation | Windows 11 | User workstation |
| Firewall 1 | Palo Alto PA 11.0.2 | Perimeter firewall |
| Firewall 2 | Palo Alto PA 11.0.2 | Internal firewall |
| VyOS Router | VyOS 1.4.3 | Network router |

> The 2027 topology has not been published yet. Treat the above as your
> training baseline — expect a similar mix of Linux servers, Windows servers,
> Palo Alto firewalls, and a router. Details will be updated when MWCCDC
> releases the 2027 team packet.

### Scored Services

The scoring engine checks these services at random intervals throughout
competition. Every minute a service is down costs you points (SLA penalties
apply):

- **HTTP / HTTPS** — web page content must match expected output exactly
- **SMTP** — email send/receive through valid accounts
- **DNS** — lookups must resolve correctly
- **POP3** — mail retrieval via Active Directory accounts
- **FTP** — file access and presence checks
- **TFTP** — file pull with integrity check
- **NTP** — time server accuracy

Keeping these up is 35–50% of your total score. Hardening a system so well
that you accidentally break a scored service is one of the most common and
costly mistakes.

### Injects (Business Tasks)

Throughout competition, the White Team drops "injects" — business tasks your
team must complete and respond to within a time window. Every inject response
is submitted as a **business memo in PDF format** via the NISE platform.

Injects are worth 35–50% of your total score. Teams that treat inject
responses as an afterthought consistently underperform, even with strong
technical defense.

See [inject-response-template.md](../drills/inject-response-template.md) for
the memo format. The short version: write for a non-technical manager, lead
with conclusions, put technical detail in appendices.

### Incident Response

When the red team successfully compromises something, you need to detect it,
document it, and submit an incident report. This is worth 10–30% of your score.

A good incident report includes: source and destination IPs, timeline of
activity, what was affected, and a remediation plan. Vague reports score
poorly. Specific, accurate reports score well even if the red team got in.

---

## The Season Structure

CCDC is not a single event. It is a progressive season with multiple rounds:

```
Invitationals (Oct/Nov) — optional dry run, virtual, low stakes
        ↓
Illinois State Qualifier (~Feb 14) — must pass to advance
        ↓
Midwest Wildcard Round (~Feb 21) — second-chance path to Regionals
        ↓
MWCCDC Regionals (~Mar 20-21) — Purdue University Northwest (2026)
        ↓
National CCDC (~Apr 24-26) — top regional winner advances
```

> All dates except Invitationals are estimated from the 2026 season.
> Official 2027 dates will be posted at caeepnc.org/mwccdc/ and ccdc.io.
> Illinois state contact: Kevin Vaccaro (vaccaro@morainevalley.edu).

### Invitationals — What They Are

The October/November invitationals are an optional dry run. They mirror the
real competition format — same NISE platform, same inject structure, live red
team — but results do not affect qualification. Think of it as a full-speed
practice with consequences low enough to experiment.

**UIC's invitationals fall during CyberForce crunch time (Role Bootcamp is
Oct 19–23; CyberForce contract period starts Oct 26).** You will be doing
both simultaneously. Plan your workload accordingly.

### Registration

National registration opens October 1, 2026 and historically stays open
into mid/late January. This is **not** a hard recruiting cutoff — it just
means we can register the team before the roster is finalized.

The real deadline is: **register before the first Invitational you want to
attend** (estimated mid-October — confirm with Kevin Vaccaro).

**Cost:** $500 per team, billed after registration. Whether this comes from
the SFAB budget is an open question — check with leadership before assuming
it is covered.

---

## How CCDC Differs from CyberForce

If you competed in CyberForce, you have the technical foundation. Here is
what is different about CCDC and where teams who only trained for CyberForce
get caught off guard:

| | CyberForce | CCDC |
|---|---|---|
| Red team timing | Competition day only | Active from drop flag, both days |
| Prep access | ~3 weeks of SSH access | None — you inherit machines live |
| Business tasks | Injects during competition | Injects throughout, memo format required |
| OT/ICS systems | Yes (HMI, PLC) | Generally no |
| AD/DNS | Sometimes | Always — central to the environment |
| Palo Alto firewalls | No | Yes — two of them |
| Scoring weight | Anomalies heaviest | Services + injects roughly equal |
| Team cohesion pressure | Medium | High — communication failures are fatal |

The biggest gap for CyberForce veterans is Active Directory and Palo Alto
firewalls. Both appear in every CCDC environment and neither appears in
CyberForce. Start there.

The second biggest gap is **business communication**. CyberForce injects are
manageable. CCDC injects come faster, pile up, and are worth up to 50% of
your score. If your team cannot write a clean business memo under pressure,
you will lose points you technically earned.

---

## Scoring Breakdown

| Category | Weight |
|---|---|
| Functional service uptime | 35–50% |
| Inject completion | 35–50% |
| Incident response | 10–30% |

Exact percentages are set by the White Team and not published in advance.
The takeaway: **there is no single thing to optimize**. A team that
completely ignores injects to focus on hardening will lose. A team that
writes perfect memos but lets services go down will also lose.

---

## What the Competition Days Look Like

Based on the 2026 MWCCDC schedule at Purdue University Northwest:

**Day 1 (Friday)**
- Check-in, receive packets and credentials
- Log into NISE, respond to Welcome inject to signal readiness
- Drop flag at 2:30 PM — scoring runs until 8:30 PM
- Red team is active the entire time

**Day 2 (Saturday)**
- Drop flag at 9:00 AM — scoring runs until 6:00 PM
- Injects continue throughout the day
- Team presentations: 2:00–4:00 PM
- Awards at 7:00 PM

Six hours on Day 1, nine hours on Day 2. You will be tired. Teams that have
not drilled communication under fatigue make mistakes that cost them the
competition.

---

## Platform: NISE

All team communication during competition goes through the NISE (National
Inject Scoring Engine), accessible via browser. Each team member gets their
own login account. Key things to know:

- Check NISE first when you arrive — there is a Welcome inject to acknowledge
  before the drop flag fires
- Inject responses must be submitted as PDF attachments unless told otherwise
- NISE may need to be manually refreshed — it does not always auto-update
- SLA status (which services are up/down) is visible through NISE
- All times displayed on NISE are Central Standard Time

For tech support, scoring inquiries, and password change requests, use
Support Services at auth.ccdc.events (same credentials as NISE).

**Critical rule:** Any scored service password change must be reported to the
White Team via a Support Ticket. Changing a password without reporting it
will cause that service to stop scoring.

---

## What You Will Learn

**Technical:**
- Active Directory administration and hardening under attack
- Palo Alto firewall configuration (NAT/PAT, security policies, IPS)
- Service hardening across a mixed Linux/Windows environment
- Real-time incident detection and response
- VyOS router configuration
- Splunk for log monitoring

**Non-technical:**
- Writing business memos under time pressure
- Coordinating 6–8 people defending different systems simultaneously
- Triage — deciding what to fix and what to accept as lost
- Communicating compromises clearly and quickly

---

## Common Questions

**Do I need to know Active Directory going in?**  
Not from day one, but you need to learn it before the Qualifier. It is the
most CCDC-specific gap for CyberForce veterans and will be a focus of fall
prep.

**What if the red team gets in?**  
Write an incident report and keep defending. Red team access is expected —
the question is how quickly you detect it, how well you document it, and
whether you stop further damage. A thorough incident report on a successful
compromise can outscore a team that had no compromises but documented nothing.

**Can I be on both the CyberForce and CCDC roster?**  
Yes — the CCDC roster is drawn from CyberForce competitors. October will be
heavy because CyberForce Role Bootcamp and the CCDC Invitationals overlap.
Plan for it now.

**What is the $500 fee?**  
The MWCCDC entry cost per team. Whether this is covered by SFAB or requires
separate funding is currently unresolved. Do not assume it is covered until
confirmed with leadership.

**Who do I contact for Illinois-specific CCDC questions?**  
Kevin Vaccaro, Illinois State CCDC Director  
vaccaro@morainevalley.edu | 708-608-4249

---

## Next Steps

**Want to compete?**
1. Confirm you are on the CyberForce roster
2. Attend Intro to CCDC — Sept 24 (what & why) and Sept 29 (how it works + roster sign-up)

**Want to prepare now?**
- Study Active Directory: users, groups, Group Policy, DNS integration
- Get familiar with Palo Alto PAN-OS — free labs at
  [paloaltonetworks.com/services/education](https://www.paloaltonetworks.com/services/education)
- Read [inject-response-template.md](../drills/inject-response-template.md)
- Review [2026-mwccdc-topology.md](../topology/2026-mwccdc-topology.md)

**Questions?**  
Ask in #ccdc on Discord or DM @AJ.

---

## Useful Links

| Resource | URL |
|---|---|
| MWCCDC main site | https://www.caeepnc.org/mwccdc/ |
| National CCDC (NCRF) | https://ccdc.io |
| NISE platform | ccdcadmin1.morainevalley.edu |
| NETLAB access | ccdc.cit.morainevalley.edu |
| Illinois state director | vaccaro@morainevalley.edu |