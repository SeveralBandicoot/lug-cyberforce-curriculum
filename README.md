# UIC Competitive Security — Curriculum & Training

**Welcome.** This repo is the single source of truth for UIC LUG's
competitive security program — covering CyberForce (Fall) and CCDC (Spring).
Whether you're competing, running events, or taking over next year — start here.

This curriculum covers CyberForce (primary) and preparation for CCDC (coming soon).

---

## Quick Links (Start Here!)

### For CyberForce Competitors
- [What is CyberForce?](docs/cyberforce101.md) — overview & competition structure
- [Competition Timeline](docs/event-timeline.md) — full Fall/Spring calendar
- [Official CyberForce 101 Library](https://cyberforce.energy.gov/cyberforce-101-library/) — read this
- [CyberForce 2025 Resources](https://drive.google.com/drive/folders/1CMDQ8fPsviGhkE3nmA0YcQ7K8DPiedaM?usp=sharing) — what last year's team faced
- [Team Structure & Roles](team-formation/role-descriptions.md) — Green, Vuln Hunters, Monitors
- [Technical Prep Guide](competition-prep/cyberforce/cyberforce-technical-prep.md) — Linux, Windows, Open PLC, PHP, networking

### For CCDC Competitors
- [What is CCDC?](docs/ccdc101.md) — overview & competition structure
- [CyberForce → CCDC: What Carries Over](docs/shared-foundations.md) — what transfers, what doesn't
- [How Scoring Works](docs/ccdc-scoring-guide.md) — services, injects, incident response
- [Team Roles](docs/ccdc-roles.md) — the five roles and what each owns
- [Common Pitfalls](docs/ccdc-common-pitfalls.md) — what consistently costs teams points

### For Event Leaders
- [CyberForce Team Kickoff](events/fall-2026/cyberforce-team-kickoff/speaker-notes.md) — Sept 22 playbook
- [CCDC 101](events/fall-2026/ccdc101/speaker-notes.md) — Sept 24: what & why
- [CCDC Deep Dive](events/fall-2026/ccdc-deep-dive/speaker-notes.md) — Sept 29: how it works + roster sign-up
- [C-Suite Briefing Prep Guide](events/c-suite-prep/2026/prep-notes.md) — practice sessions, recording tips
- [Welcome Event Playbook](events/welcome-event/) — agenda, talking points, veteran scripts

### For Admins / Next Year's Leads
- [Handoff Guide](HANDOFF.md) — **read this first** if you're taking over
- [Admin Meeting Notes](docs/admin-timeline.md) — decisions made, timeline
- [CyberForce Common Pitfalls](docs/cyberforce-common-pitfalls.md) — what went wrong + how to fix
- [CCDC Common Pitfalls](docs/ccdc-common-pitfalls.md) — what went wrong in CCDC

### For Alumni / Mentors
- [Mentoring Guide](team-formation/team-mentor-matching.md) — how to help a team
- Red Team Guide — help run the competition *(no documentation yet)*
- Archive: Lessons from Veterans *(no documentation yet)*

---

## What's in This Repo?

```
lug-cyberforce-curriculum/
  README.md (this file)
  HANDOFF.md 
  CONTRIBUTING.md 
  
  docs/ 
    cyberforce101.md 
    ccdc101.md 
    event-timeline.md 
    shared-foundations.md 
    ccdc-scoring-guide.md 
    ccdc-roles.md 
    cyberforce-common-pitfalls.md 
    ccdc-common-pitfalls.md 
    official-links.md 
    admin-timeline.md (WIP)
  
  events/
    fall-2026/
      cyberforce-team-kickoff/ 
        speaker-notes.md
      ccdc101/ 
        speaker-notes.md
      ccdc-deep-dive/ 
        speaker-notes.md
      cyberforce-ctf/ (⚠️ EMPTY - stub)
  
  competition-prep/
    cyberforce/
      cyberforce-technical-prep.md 
      linux-quickref.md 
      windows-quickref.md 
      open-plc-primer.md 
      tools.md 
      role-prep/
        green_team_guide.md 
        monitoring+hardening_guide.md 
        vuln_hunter_guide.md 
    
    ccdc/
      README.md 
      timeline.md (⚠️ WIP - waiting on 2027 packet)
      drills/ 
        incident-report-template.md 
        inject-response-template.md 
        service-template.md 
      skill-domains/ 
        active-directory.md 
        linux-sysadmin.md 
        windows-sysadmin.md 
        networking.md 
        cryptography.md 
        legal-frameworks.md 
        buisness-comms.md 
        virtualization.md 
      topology/ 
        2026-mwccdc-topology.md 
        palo-alto-primer.md 
        vm-roles.md 
  
  team-formation/ 
    role-descriptions.md 
    team-balancing-guide.md 
    team-mentor-matching.md 
  
  announcements/ 
    README.md 
    2026announcements/ (content)
    announcement-templates/
      announcements_template_kickoff.md 
      announcements_template-registration.md 
  
  resources/
    .gitignore (⚠️ folder mostly empty)
  
  templates/ (⚠️ EMPTY - for copy-paste templates)
  leads/ (⚠️ EMPTY - for lead-specific docs)
  scorecards-feedback/ (⚠️ EMPTY - fills after competition)
  archival/ (⚠️ EMPTY - historical competition materials)
```

---

## How to Use This Repo

**If you're a CyberForce competitor:**
1. Read [CyberForce 101](docs/cyberforce101.md)
2. Check [Competition Timeline](docs/event-timeline.md)
3. Study [CyberForce 2025 Team's Google Drive](https://drive.google.com/drive/folders/1CMDQ8fPsviGhkE3nmA0YcQ7K8DPiedaM?usp=sharing)
4. Explore [Technical Prep](competition-prep/cyberforce/cyberforce-technical-prep.md) based on your role
5. Attend workshops and events listed in the calendar

**If you're a CCDC competitor:**
1. Read [CCDC 101](docs/ccdc101.md)
2. Read [Shared Foundations](docs/shared-foundations.md) — know your gaps coming from CyberForce
3. Read [Team Roles](docs/ccdc-roles.md) — know your role before the Invitational
4. Read [Scoring Guide](docs/ccdc-scoring-guide.md) — understand what the points actually come from
5. Attend CCDC 101 and CCDC Deep Dive sessions (Sept 24 and Sept 29)

**If you're running an event:**
1. Go to `/events/[event-name]/`
2. Read the speaker notes and agenda
3. Copy any templates you need
4. Run the event
5. Add a debrief note to the event folder for next year

**If you're taking over next year:**
1. **Read [HANDOFF.md](HANDOFF.md) first**
2. Check [Event Timeline](docs/event-timeline.md) for key deadlines
3. Review [CyberForce Common Pitfalls](docs/cyberforce-common-pitfalls.md) and [CCDC Common Pitfalls](docs/ccdc-common-pitfalls.md)
4. Skim [Admin Timeline Notes](docs/admin-timeline.md)
5. Check GitHub Issues for unfinished work
6. Ask the previous leads questions before they graduate

---

## 2026–2027 Event Calendar (Quick Reference)

### Fall 2026 — CyberForce + CCDC Prep

| Date | What | Competition |
|------|------|-------------|
| Sept 9 | GBM — CCDC pitch | Both |
| Sept 22 | CyberForce Team Kickoff | CyberForce |
| Sept 24 | CCDC 101 — what & why | CCDC |
| Sept 29 | CCDC Deep Dive — how it works + roster sign-up | CCDC |
| Oct 1 | CCDC national registration window opens | CCDC |
| Oct 7 | CyberForce CTF | CyberForce |
| Oct 18/25/Nov 1 | MWCCDC Invitationals (est.) | CCDC |
| Oct 19 | Role Bootcamp Day 1 — Green Team | CyberForce |
| Oct 21 | Role Bootcamp Day 2 — Vulnerability Hunting | CyberForce |
| Oct 23 | Role Bootcamp Day 3 — System Hardening | CyberForce |
| Oct 26, 6pm CT | CyberForce phase 1 begins ✅| CyberForce |
| Oct 29 | Hack-o-ween CTF (WiCyS collab, est.) | CTF Group |
| Nov or Spring Sem. | CCDC post-Invitational debrief | CCDC |
| Nov 2, 6pm CT | CyberForce phase 2 begins ✅| CyberForce |
| Nov 13–14 | CyberForce Competition ✅| CyberForce |

### Spring 2027 — CCDC Season + Open Recruiting

| Date | What | Competition |
|------|------|-------------|
| ~Feb 14 | Illinois State CCDC Qualifier (est.) | CCDC |
| Feb 17 | Intro to CyberForce — open recruiting kickoff | CyberForce |
| Feb 12 | Caught the Lovebug CTF (WiCyS collab, est.) | CTF Group |
| Feb 25 | Intro to CCDC #1 — what & why (open recruiting) | CCDC |
| ~Feb 21 | Midwest Wildcard Round (est.) | CCDC |
| Mar 2 | Intro to CCDC #2 — how it works (open recruiting) | CCDC |
| Mar 9 | Spring CTF — open, beginner-friendly | CTF Group |
| ~Mar 20–21 | MWCCDC Regionals — Purdue NW (est.) | CCDC |
| Mar 23 / Mar 30 | Roster-building workshops | Both |
| ~Apr 5–11 | Capture the Flame (WiCyS flagship CTF) | WiCyS |
| ~Apr 12–18 | Byte the Flame CTF (WiCyS collab, est.) | CTF Group |
| ~Apr 24–26 | National CCDC (est.) | CCDC |
| Apr 20 | Roster-building / summer registration push | Both |
| Apr 27 | Dev team applications + leadership positions open for CTF Group | Both |

*✅ = confirmed from official sources. All other dates estimated from prior seasons.*  
*Full detail in [event-timeline.md](docs/event-timeline.md)*

---

## Questions?

**CyberForce questions?**
→ Read [CyberForce 101](docs/cyberforce101.md) or DM @AJ

**CCDC questions?**
→ Read [CCDC 101](docs/ccdc101.md) or DM @AJ

**Technical questions?**
→ Check [Technical Prep](competition-prep/cyberforce/cyberforce-technical-prep.md)

**Role or team questions?**
→ Check [CyberForce Roles](team-formation/role-descriptions.md) or [CCDC Roles](docs/ccdc-roles.md)

**Repo issue?**
→ Open a GitHub Issue or message @AJ

---

## Contributing

Want to add something? See [CONTRIBUTING.md](CONTRIBUTING.md) for:
- How to add new materials
- File naming conventions
- When to create vs. update files
- Who to ask for feedback

**Key rule:** Add "Last updated" dates to everything so the next lead knows
what's current.

---

## Repo Status

**Last updated:** August 2026  
**Maintained by:** AJ & LUG CTF Group Admin team  
**Competitions covered:** CyberForce (Fall) · CCDC via MWCCDC (Spring)  
**For questions:** See above or check [CONTRIBUTING.md](CONTRIBUTING.md)

---

## What This Repo Is For

This repo exists so that:

1. Competitors have clear learning paths for both CyberForce and CCDC  
2. Event leaders have playbooks to run events without reinventing them  
3. Admins have timelines and checklists to stay on track  
4. Institutional knowledge doesn't disappear when people graduate  
5. Next year's leads don't start from zero  

Make it better each year. Leave notes for the next person. Document lessons learned.

---
