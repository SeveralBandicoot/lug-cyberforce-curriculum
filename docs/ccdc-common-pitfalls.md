# CCDC Common Pitfalls

**Last updated:** August 2026  
**Owner:** AJ  
**For:** Anyone preparing for CCDC, especially CyberForce veterans

---

## How to Use This Document

These are the mistakes that consistently cost teams points at CCDC — drawn
from MWCCDC feedback, the official Business Memo Guidelines, and the CCDC
Team Preparation Guidelines. Some of these will feel obvious after the fact.
They are not obvious in the moment.

Read this before your first Invitational. Read it again before the Qualifier.

---

## Category 1: The First 30 Minutes

### Not changing default credentials immediately
The 2026 MWCCDC topology ships with known default credentials on every
system — including both Palo Alto firewalls (`admin/Changeme123`) and the
VyOS router (`vyos/changeme`). These are published in the team packet, which
means the red team has them too.

The red team's first move is often to log into the firewalls with the default
credentials before your team does. If they get there first, they own your
perimeter.

**Fix:** The very first thing your team does after the drop flag is change
credentials on the firewalls and router. Before hardening any server. Before
checking services. Before anything else.

### Not responding to the Welcome inject
When you first log into NISE, there is a Welcome inject. It is a simple
acknowledgment — respond to it to signal readiness. Judges will not release
the drop flag notification until they have confirmed teams are ready. Teams
that miss the Welcome inject delay their own start.

**Fix:** Designate one person to handle NISE at the start of competition
while everyone else handles credentials and initial setup.

### Assuming systems are properly configured
They are not. Every system in CCDC starts with vulnerabilities, weak
passwords, unnecessary services, and misconfigurations. "It seems to be
working" is not the same as "it is secure."

**Fix:** Treat every machine as compromised until proven otherwise. Enumerate
everything before assuming anything.

---

## Category 2: Breaking Scored Services

### Hardening a service to death
The scoring engine checks services continuously. Firewall rules that are too
aggressive, service restarts that take too long, or configuration changes that
break expected behavior all cost SLA points. This is one of the most common
ways technically strong teams lose.

**Fix:** After any significant change to a scored service, verify it is still
responding correctly before moving on. Have one person monitoring the NISE
service status dashboard throughout competition.

### Changing scored service passwords without notifying the White Team
CCDC rules are explicit: any password change affecting a scored service must
be reported to the White Team via a Support Ticket. The scoring engine
authenticates to services using known credentials. If you change them without
reporting, the service stops scoring — you lose points for uptime even if the
service is technically running.

**Fix:** Create a password change log during competition. Every scored service
password change gets a Support Ticket immediately. See the
[service-checklist.md](../drills/service-checklist.md) for the ticket workflow.

### Blocking the scoring engine
Teams sometimes try to restrict service access by source IP — for example,
only allowing connections from specific addresses. The scoring engine comes
from addresses that are not always predictable. Blocking it kills your uptime
score.

Per competition rules: teams may block individual IPs confirmed as malicious,
but may not block entire subnets or place blanket ACLs at the network ingress.

**Fix:** Be conservative with IP-based blocks. When in doubt, check with the
White Team before implementing broad restrictions.

### Accidentally ending the NETLAB reservation
The NETLAB interface has a reservation drop-down that, if triggered, restarts
your entire environment. Services come back up, but your team loses all
progress and starts from the initial vulnerable state. This has happened to
teams at regional competitions.

**Fix:** Designate one person as the NETLAB operator. Everyone else accesses
VMs through the topology diagram, not the drop-down. Brief the team on this
before the drop flag.

---

## Category 3: Injects and Business Memos

### Writing technical reports instead of business memos
This is the most consistent feedback in MWCCDC's official Business Memo
Guidelines. Teams write inject responses that read like lab reports —
introduction, procedure, data, conclusions — instead of business memos that
lead with the bottom line.

Judges are experienced professionals. They will notice. Format can be the
difference between partial and full credit on a close score.

**Fix:** The structure of a business memo is: what did you do, what did you
find, what will you do next. Put the conclusion first. Technical detail goes
in appendices. See [inject-response-template.md](../drills/inject-response-template.md).

### Missing deliverables within an inject
Each inject specifies explicit deliverables. Teams frequently address the
general topic of an inject but miss specific items that were asked for. Judges
score on deliverables, not intent.

**Fix:** Before writing the memo, list every deliverable from the inject.
Use those deliverables as the outline of your response. Do not submit until
every deliverable is addressed — even partially. Partial credit for an
acknowledged incomplete item beats zero credit for an item that was ignored.

### Not submitting injects at all
Some teams get so focused on technical defense that injects pile up unread or
unsubmitted. Injects are worth 35–50% of your total score. A team that ignores
them cannot win, regardless of how clean their defense is.

**Fix:** Assign a dedicated inject handler — one person who monitors NISE,
reads every inject immediately, and either writes the response or delegates it
and follows up. This person's primary job is injects, not system defense.

### Submitting injects without appendices
Technical data (tool output, IP tables, log excerpts, configuration files)
belongs in appendices, not the body of the memo. Output pasted into the body
of a memo without labels or context confuses judges and reads as unprofessional.

**Fix:** Every appendix needs a title, a description of what tool produced it,
and which system it was run on. Label everything.

---

## Category 4: Active Directory

### Leaving default AD accounts enabled
Windows Server 2019 AD environments ship with the built-in Administrator
account enabled and with a known password. The red team knows this. Leaving
it as-is is an open door.

**Fix:** Rename the built-in Administrator account, change its password, and
create a named admin account for your team's use. Disable or restrict the
Guest account. Audit all accounts within the first hour.

### Not auditing AD group memberships
Red teams frequently escalate privilege by adding accounts to privileged
groups (Domain Admins, Enterprise Admins, Schema Admins). If you are not
monitoring group membership, you will not notice until the damage is done.

**Fix:** Take a baseline snapshot of privileged group memberships at the start
of competition. Check them periodically throughout the day. Splunk can alert
on group membership changes if configured.

### Overly aggressive GPO changes that break authentication
Group Policy is powerful and dangerous. A GPO that misconfigures authentication
settings, Kerberos policy, or network logon settings can lock your entire team
out of the domain. At competition, recovering from a bad GPO under pressure
is extremely difficult.

**Fix:** Make GPO changes incrementally. Test each change. Know how to access
systems locally (not domain-authenticated) as a fallback in case domain
authentication breaks.

---

## Category 5: Team Coordination

### No clear system ownership
In the chaos of competition, two people working on the same system at the
same time cause conflicts, overwritten changes, and confusion about what has
been done. Two people ignoring the same system because each assumes the other
is handling it is worse.

**Fix:** Assign system ownership before the drop flag. Each person knows
which VMs they are primarily responsible for. Changes to another person's
system require a verbal callout.

### Not calling out compromises immediately
When someone detects a red team compromise, the instinct is often to quietly
start fixing it. This is wrong for two reasons: it delays the incident report
(which costs points), and other team members may be working on the same
system without knowing it was compromised.

**Fix:** Establish a verbal protocol for calling out compromises. Something
as simple as "AD is compromised — I see a new local admin account, logging
now" gives the whole team situational awareness and starts the incident
report timer.

### Letting one person carry the team
In six-person teams, it is common for one or two technically strong members
to take over while others disengage. This creates a single point of failure
and burns out the people doing the work. By Day 2 afternoon, fatigue makes
mistakes. A team with six people each carrying their own load consistently
outperforms a team where two people are doing everything.

**Fix:** Assign roles that match skill levels, not just the most confident
people. Less experienced members should own specific, defined tasks (NISE
monitoring, inject drafting, specific VMs) rather than floating.

---

## Category 6: Mindset

### Treating the Invitational like it does not matter
The Invitationals are unscored for qualification purposes, which leads some
teams to approach them casually. The Invitational is your only opportunity to
run the full competition format — same platform, same inject structure, live
red team — before the Qualifier counts.

**Fix:** Treat the Invitational as a full dress rehearsal. Debrief seriously
afterward. The lessons from the Invitational are the
most specific prep you will get.

### Resetting a VM without thinking through the consequences
When a system is hopelessly compromised or broken, teams can request a VM
reset via Support Ticket. The reset restores the system to its initial
vulnerable state — all your hardening is gone, and the original vulnerabilities
are back. Resets are tracked and negatively impact scores at the Chief Judge's
discretion.

**Fix:** Before requesting a reset, ask: can we recover from this without a
reset? Is the service actually down, or does it just feel chaotic? Resets are
a last resort, not a panic button.

### Going silent when things go wrong
Teams that are being actively attacked sometimes go heads-down and stop
communicating. This is exactly when communication matters most — other team
members need to know what is happening to adjust their own actions.

**Fix:** Establish a norm in practice: more communication under pressure, not
less. Even a quick callout ("red team is hitting the webmail server, I'm on
it") keeps the team oriented.

---

## See Also

- [ccdc101.md](../../docs/ccdc101.md) — full CCDC overview
- [inject-response-template.md](../drills/inject-response-template.md)
- [service-checklist.md](../drills/service-checklist.md)
- [shared-foundations.md](../../docs/shared-foundations.md)