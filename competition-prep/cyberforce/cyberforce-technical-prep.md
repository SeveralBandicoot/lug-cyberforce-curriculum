================================================================================
# General Competition Preparation
---
## CyberForce Official Resources

For Everyone - Start Here

Last updated: August 2026

For: All competitors

### CyberForce Homepage

https://cyberforce.energy.gov/

What: Official Department of Energy competition site

Contains: News, rules, scenario info, registration

Action: Bookmark this


### CyberForce 101 Library -> START HERE

https://cyberforce.energy.gov/cyberforce-101-library/

What: Comprehensive official learning resource

Covers: Competition overview, infrastructure concepts, security practices, tools

How to use: Read through completely before competition prep starts


### Join the CyberForce Listserv

https://cyberforce.energy.gov/stay-connected/

What: Official email updates from CyberForce organizers

Why: Announcements, deadline reminders, scenario releases

Action: Subscribe ASAP (link on website)


### FOR TEAM CAPTAINS: Register Your Team

When: July 20 2026 

Where: [registeration link](https://cyberforce.energy.gov/cyberforce-competition/2026-competition/)

Action items:
- Get team name + roster ready
- Register within deadline (July 20 - September )

---

## Competition Overview

### What is CyberForce?

National competition run by Department of Energy (DOE) Office of Cybersecurity, Energy Security, and Emergency Response (CESER)
Blue team defensive competition where your team defends a real-world energy infrastructure scenario against attacks from a red team.

Three-week competition window:


Week 1 (Oct 26): C-Suite scenario released + teams prepare briefing

Week 2 (Nov 2): AWS access + security documentation prep

Week 3 (Nov 13-14): Competition day (full day event)


Your goal: Defend systems, maintain uptime, find vulnerabilities (anomalies), respond to incidents, brief leadership on findings.

---

### Competition Structure (5 Teams)

#### Blue Team (Your team: 4–6 people)


- Defend network infrastructure
- Maintain system uptime
- Detect and respond to attacks
- Solve anomalies (CTF-style challenges)
- Document security measures


#### Red Team (Department of Energy staff + industry professionals)


- Attack the blue team network
- Exploit vulnerabilities
- Test defenses
- Score the competition


#### Green Team (Volunteers)


- Play role of end users
- Use web applications
- Test system usability
- Report issues to blue team


#### White Team (National lab employees)


- Help desk
- Support infrastructure setup
- Judge the competition
- Score uptime + services
- Manage competition logistics


#### Orange Team (Volunteers)


- Play role of C-Suite executives
- Review blue team briefing video
- Evaluate security documentation
- Score leadership/communication

---

### Scoring Breakdown (2025 Example)

Points are awarded for:

[scoring will be updated once we recieve the rulebook Nov 2]
- Anomalies/CTF Challenges: ~40% (highest point source)
- System Uptime: ~20% (keeping systems running)
- Incident Response: ~10% (detecting/stopping attacks)
- Security Documentation: ~20% (explaining your measures)
- C-Suite Briefing: ~10% (communication to leadership)

---

### Past Competitions (Learn from These)

#### 2024 CyberForce Team Drive


https://drive.google.com/drive/folders/1CMDQ8fPsviGhkE3nmA0YcQ7K8DPiedaM?usp=sharing

What: Notes + resources left from 2024 CyberForce team

Why: Take a look at how competitions in the past have been handled, could be useful for this years.


#### 2025 CyberForce Team Drive

https://drive.google.com/drive/folders/1CMDQ8fPsviGhkE3nmA0YcQ7K8DPiedaM

What: Notes + resources left from 2025 CyberForce team

Why: Take a look at how competitions in the past have been handled, could be useful for this years.

---

#### 2025 Point Breakdown


https://drive.google.com/file/d/1NXFNB1wIp9bFK6V8Iu-IGZXj0_gzMTsR/view?usp=sharing

What: Official points for each scoring category

Why: Understand what matters most

---

#### 2025 Team Scorecard (Real Example)


https://github.com/CyberForceProgram/2025_CyberForce_Competition/blob/main/Scorecards/Team%201.pdf

What: Actual scorecard from competing team

Why: See what scored well + what didn't

Learn from: Strengths to emulate, weaknesses to avoid

---

### CyberForce GitHub


https://github.com/CyberForceProgram/

What: Official GitHub org with past competitions

Contains: Anomalies, rules, documentation examples, setup scripts

Use: Browse for ideas, understand structure

---

## General Cybersecurity Concepts
---
### NIST Cybersecurity Framework


https://www.nist.gov/cyberframework

What: High-level security practices + concepts

Why: Understand security philosophy beyond "follow rules"

Read: Identify, Protect, Detect, Respond, Recover



### CIS Controls (Critical Security Practices)


https://www.cisecurity.org/cis-controls/

What: Top security measures organizations implement

Why: Many practices you'll use are based on these

Focus: Inventory, Access control, Monitoring



## Everyone Should Install
---
Before competition starts, have these ready:

### VirtualBox (Practice Environment)


https://www.virtualbox.org/

What: Run Linux/Windows VMs on your computer

Why: Practice hardening without breaking your system

Install: Download + follow setup wizard


### Git (Version Control)


What: Track code changes

Why: Some anomalies involve git repos

Install: apt-get install git (Linux) or https://git-scm.com/ (Windows/Mac)


### Docker (Containerization)


What: Run containerized applications

Why: Some anomalies use Docker

Install: https://docs.docker.com/get-docker/


### Python (Scripting)


What: Write quick scripts + tools

Why: Many anomalies require custom Python scripts

Check: Usually pre-installed on Linux

Install: https://www.python.org/


### Text Editor with Good Tools


Recommended: VSCode (https://code.visualstudio.com/)

Why: View code, logs, configs; supports syntax highlighting

Extensions: Useful for viewing different file types



## How to Prepare (Generic Timeline)
---
### Month 1 (September: Foundation)


 1. Skim CyberForce 101 Library
 2. Understand competition structure (what we explained above)
 3. Join CyberForce listserv
 4. Install VirtualBox + practice OS
 5. Start learning your role's fundamentals


### Month 2 (October: Deep Dive)


1. Deep dive on your role (Linux/Windows/Web/Anomalies)
2. Set up AWS account (once provided)
3. Practice in lab environment


### Month 3 (November: Crunch + Competition)


 Week 1: Prepare C-Suite briefing + Security Docs

 Week 2: AWS access → finalize hardening + monitoring
 
 Week 3: Competition day! (Friday or Saturday, all-day event)



>⚠️ Important Rules
>
>### During competition:
>
>Only your 4–6 team members can work on the competition
>
>No help from mentors, teachers, other students
>
>No external resources beyond what you brought
>
>Coordinate with UIC teams (no disqualification through info-sharing mistakes)
>
>Follow all CyberForce rules (they're strict)


### Pre-competition:


- Study materials
- Prepare infrastructure
- Document everything

---

### Your First Steps 


 1. Bookmark CyberForce homepage
 2. Subscribe to listserv
 3. Read CyberForce 101 Library (at least overview)
 4. Install VirtualBox + practice setting up a Linux VM
 5. Install Git + Python
 6. Read your role-specific resources
     - [Green Team Guide](role-prep/green_team_guide.md)
     - [Vulnerability Hunter Guide](role-prep/vuln_hunter_guide.md)
     - [Monitoring & Hardening Guide](role-prep/monitoring+hardening_guide.md)



Questions? Ask in #cyberforce or DM @AJ

================================================================================
