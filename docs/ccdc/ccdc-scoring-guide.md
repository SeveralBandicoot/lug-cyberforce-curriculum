# CCDC Scoring Guide

**Last updated:** August 2026  
**Owner:** AJ  
**For:** Competitors and team captain

---

## Why This Document Exists

CCDC scoring is more complex than CyberForce and is frequently misunderstood
by teams competing for the first time. Teams lose points they technically
earned because they did not understand the rules. This document explains how
scoring actually works, where most points come from, and how to make decisions
during competition based on scoring reality rather than instinct.

---

## The Three Scoring Buckets

| Category | Weight | What It Measures |
|---|---|---|
| Functional service uptime | 35–50% | Automated engine checking services continuously |
| Inject completion | 35–50% | Business memo responses submitted via NISE |
| Incident response | 10–30% | Reports on red team compromises you detect |

The White Team sets exact percentages and does not publish them in advance.
Treat each bucket as roughly equal in importance. No single bucket can be
neglected.

---

## Bucket 1: Service Uptime (35–50%)

### How It Works

An automated scoring engine continuously checks scored services at random
intervals. For each check:
- Service is up and responding correctly → points awarded
- Service is down or responding incorrectly → no points, SLA timer starts
- Service has been down too long → SLA penalty accrues (negative points)

The scoring engine checks both availability and content. For HTTP/HTTPS, the
returned page must match an expected file exactly. Changing web content
without understanding what the scoring engine expects will cost you points
even if the server is technically running.

### Scored Services (2026 MWCCDC)

| Service | Protocol | Key Requirement |
|---|---|---|
| HTTP | TCP 80 | Page content must match expected output |
| HTTPS | TCP 443 | SSL must be valid; content must match |
| SMTP | TCP 25 | Email must be sendable and receivable |
| DNS | UDP/TCP 53 | Lookups must resolve correctly |
| POP3 | TCP 110 | Must authenticate via AD accounts |
| FTP | TCP 21 | Files must be present; auth must work |
| TFTP | UDP 69 | Small file pull with integrity check |
| NTP | UDP 123 | Time must be accurate |

### Critical Rules That Affect Scoring

**Password changes must be reported.** The scoring engine authenticates to
services using known credentials. If you change a scored service password
without submitting a Support Ticket to the White Team, the service stops
scoring. The service can be fully operational and you will receive zero uptime
points for it.

**You cannot block the scoring engine.** The engine comes from IP addresses
within the competition network. Firewall rules that are too aggressive will
block it. You may block specific IPs confirmed as red team, but you may not
block entire subnets or place blanket deny rules at the network ingress.

**Service resets count against you.** If you request a VM reset, it is
tracked and negatively impacts your score at the Chief Judge's discretion.
All hardening on that machine is also lost and the original vulnerabilities
return.

**Workstations cannot be repurposed.** VMs designated as user workstations
may not be retasked for other purposes. Do not try to turn a workstation into
a monitoring server or secondary defense node.

### Strategy

Monitor NISE's service status dashboard continuously. Assign one team member
to watch it throughout competition — this person's job is to notice when a
service drops and alert the team immediately.

After any configuration change to a scored service, verify the service is
still responding before moving on. This sounds obvious. Under pressure, people
skip the verification step.

Prioritize restoring a downed service over hardening other systems. A downed
service bleeds SLA points every minute it is down.

---

## Bucket 2: Inject Completion (35–50%)

### How It Works

The White Team releases inject tasks via NISE throughout competition. Each
inject is a business task with explicit deliverables and a deadline. Teams
submit responses as PDF attachments through the NISE portal.

Injects are scored by judges (not automated) based on:
- Whether all deliverables were addressed
- Accuracy and completeness of technical content
- Quality of business communication (memo format, clarity, tone)
- Timeliness of submission

### The Business Memo Format

MWCCDC's official Business Memo Guidelines are explicit: inject responses
should be business memos, not technical reports. Judges have provided this
feedback repeatedly because teams consistently get it wrong.

A business memo leads with conclusions and writes for a non-technical manager.
Technical data belongs in appendices, not the body.

**Structure:**
```
TO: [Management / as specified in inject]
FROM: [Your team name / number]
DATE: [Competition date]
RE: [Inject subject]

[Body — 1-3 paragraphs]
What was done / what was found / what will be done next.
Written in plain English. No jargon in the body.
Conclusions first, not last.

[Appendix A — Technical Detail]
Tool output, tables, logs, configurations.
Label every appendix: what tool, what system, what it shows.
```

**Formatting rules from MWCCDC guidelines:**
- Non-serif font throughout (Arial, Calibri, Verdana, Helvetica)
- Tool output may remain in its native monospace font
- Every table and figure must be labeled and captioned
- Professional appearance matters and is assessed by judges

See [inject-response-template.md](../drills/inject-response-template.md) for
a copy-paste starting template.

### Partial Credit Is Real

If you cannot complete all deliverables within the inject window, submit what
you have. Acknowledge what is incomplete, explain why, and state when it will
be completed. Judges score partial submissions. A submitted partial response
beats a perfect response that was never submitted because the team ran out of
time.

### Resubmission

After submitting an inject response, judges may mark it invalid and allow
resubmission. The number of resubmissions allowed is set by White Team policy
and varies. If an inject is marked invalid, fix and resubmit immediately —
do not wait.

### Strategy

Assign a dedicated inject handler. This person monitors NISE, reads every
inject the moment it drops, and either writes the response or immediately
delegates it to the most relevant team member. The inject handler tracks
deadlines and follows up on in-progress responses.

Do not let injects pile up. A technical team that ignores injects to focus
on hardening will lose to a balanced team with slightly weaker defense but
strong inject completion.

Treat each inject deliverable list as a checklist. Do not submit until every
item is addressed or explicitly acknowledged as incomplete.

---

## Bucket 3: Incident Response (10–30%)

### How It Works

When the red team compromises something, you are expected to detect it,
document it, and submit an incident report. Reports are scored by the White
Team in consultation with the Red Team, who know exactly what they did.

Incident reports are scored on:
- Accuracy (does your account match what the red team actually did?)
- Thoroughness (source/destination IPs, timestamps, affected systems)
- Quality of remediation plan
- Clarity of communication

### What Goes in an Incident Report

Per MWCCDC rules, incident reports must contain:
- Description of what occurred
- Source and destination IP addresses
- Timeline of activity
- Passwords cracked (if applicable)
- Discussion of what was affected
- Remediation plan

**Important scope note:** MWCCDC guidelines specify that incident reports
should focus on actual exploitation and unauthorized access — not
misconfigurations, bogus accounts (unless caused by exploitation), or malware
presence alone. A report on a misconfiguration you found during hardening is
not an incident report. A report on the red team adding a new local admin
account after gaining access is.

### Strategy

The moment someone detects a red team compromise, two things happen
simultaneously: the affected system gets immediate attention, and someone
starts writing the incident report. Do not wait until after you have
remediated to document — you will forget details.

Accurate reports score better than thorough reports. If you are not certain
of a detail, say so rather than guessing. The Red Team will know if you
guessed wrong.

Submitting a good incident report on a successful red team compromise can
outscore a team that had no compromises but documented nothing. Detection and
documentation matter even when the red team wins the exchange.

---

## How Points Are Lost

Beyond missed opportunities, there are active ways to lose points:

| Action | Consequence |
|---|---|
| Service down → SLA violation | Negative points accumulate per interval |
| VM reset requested | Tracked; Chief Judge discretion on penalty |
| Scoring engine blocked by firewall | Service scores as down |
| Password changed without White Team ticket | Service scores as down |
| Offensive action against other teams | Immediate disqualification |
| External communication (non-team) | Grounds for disqualification |
| Frivolous or excessive White Team communication | White Team may assess negative score |
| Ending NETLAB reservation accidentally | Team restarts from initial state |

---

## Scoring Visibility During Competition

Running totals are not shared with teams during competition. You will not know
your score relative to other teams until the end of Day 2. What you can see:

- Your own service status (up/down) via NISE
- Inject submission status (submitted, pending, invalid)
- General NISE announcements from the White Team

Do not make decisions based on assumed score position. Play every hour of
competition as if it is close.

---

## Decision Framework: When to Prioritize What

Use this during competition when you have more things to do than time to do
them:

**A service is down.**  
Stop what you are doing. Restoring a scored service is the highest priority.
Every minute of downtime is lost uptime points plus SLA accrual.

**An inject just dropped with a 30-minute deadline.**  
Assign it immediately. Do not wait for a natural break in technical work.
Inject deadlines are real and the window is often shorter than it feels.

**The red team is actively attacking a system.**  
Call it out to the team. Document what you observe (start the incident
report). Assess whether the attack is affecting scored services. If yes,
prioritize service restoration. If no, harden the affected system while
continuing other work.

**You have time and no immediate fires.**  
Harden in order of risk: systems the red team has not yet touched, starting
with highest-value targets (AD, firewalls). Verify scored services are still
passing after each change.

---

## See Also

- [ccdc101.md](../../docs/ccdc101.md) — full CCDC overview
- [inject-response-template.md](../drills/inject-response-template.md)
- [incident-report-template.md](../drills/incident-report-template.md)
- [ccdc-common-pitfalls.md](../../docs/ccdc-common-pitfalls.md)
- [service-checklist.md](../drills/service-checklist.md)