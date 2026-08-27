================================================================================
# CyberForce 101 — What Is It?

**Last updated:** June 2026  
**Owner:** AJ  
**For:** Everyone (competitors, admins, curious people)

---

## Quick Answer

**CyberForce is a national cybersecurity competition where your team defends an energy infrastructure network against live attacks.**

You'll manage systems, find and fix vulnerabilities, respond to real-time threats, and compete against 100+ teams from universities across the US. It's intense, challenging, and genuinely educational.

---

## How It Works

### **The Scenario**

Every year, CyberForce creates a fictional energy company (oil rig, wind farm, solar facility, etc.). Your team's job: **secure and defend their network for ~3 weeks.**

**The network looks like:**
- ~6 computers (mix of Linux & Windows)
- A web application (the "Green Team" system you maintain)
- Automation controls (Open PLC, runs the energy equipment)
- Mail server, monitoring tools, etc.

Some machines are critical (can't break them), others are "vulnerable" on purpose (meant to be attacked).

### **The Timeline (~3 Weeks)**

**Week 1: C-Suite Briefing**
- CyberForce releases a scenario: "Your company had a security breach. Here's what happened."
- Your team records a 5–10 minute video explaining the breach and your response plan
- This is your team's "pitch" to company leadership
- **Due:** 7 days after scenario drops

**Week 2: Security Documentation & Prep**
- You get SSH access to all the machines
- Your team hunts for vulnerabilities, documents what you find
- You harden systems, set up monitoring, prepare defenses
- **Due:** 7 days after day of drop

**Competition Day (Full day event)**
- Live environment: your machines are under attack
- Anomaly challenges drop throughout the day (CTF-style puzzles)
- Your job: keep systems running, solve challenges, defend against red team
- You're scored on vulnerabilities fixed, anomalies solved, documentation quality
- **Location:** Usually near Chicago (Tinley Park in 2025)
- **Timing:** Early-Mid November (estimated for 2026)

---

## What You Actually Do

### **Day-to-Day During Prep (Sept–Oct)**
- Study concepts through provided content (Linux hardening, Windows security, Open PLC, etc.)
- Study anomalies from past years
- Meet with your team
- Ask questions, learn together

### **Week 2 (Active Prep)**
- SSH into machines, explore them
- Find security issues (wrong configs, weak passwords, open ports, etc.)
- Document everything (when you found it, what it was, how you fixed it)
- Set up monitoring tools (Wazuh, firewalls, etc.)

### **Competition Day**
- Defend systems under attack
- Solve anomalies (CTF challenges embedded in the network)
- Respond to incidents (red team triggers problems, you react)
- Maintain uptime and documentation

---

## Scoring

**Points come from:**

| Category | What | Points |
|----------|------|--------|
| C-Suite briefing | Documented response plan | - |
| Security documentation | Found vulnerabilities + fixes | - |
| Anomalies solved | CTF-style challenges during competition | - |
| System uptime | Kept systems running during attacks | - |
| Incident response | How you reacted to attacks | - |

---

## What's Hard

**Windows systems** — One of last year's biggest gaps. Windows has 3 different ways to change every setting, they override each other randomly, and monitoring is complex.

**Time commitment** — Normal season is estimated to be ~2 hrs/week. The 3-week prep crunch is 3–5 hrs/week with your team. 

**Open PLC** — Controls the actual energy equipment. If you break it, your score tanks. Takes practice to get right.

---

## What's Awesome

**You learn real cybersecurity** — Not just theory. You're hardening actual systems, responding to actual attacks, fixing real vulnerabilities.

**Team skill mix** — You don't need to be an expert at everything. Teams deliberately balance: someone good at Linux, someone good at Windows, someone good at CTF. You learn from each other.

**Veterans help** — Michael, Sam, Tegan have done this. They mentor, answer questions, share lessons.

**It's fun** — Weird thing to say about a stressful competition, but people genuinely enjoy it. Adrenaline, teamwork, learning fast.

**Looks great on resumes** — Employers care about this. You can say "I defended a network against live attacks" and mean it.

---

## Requirements

**Technical:**
- Basic Linux knowledge (command line, file permissions, running services)
- Basic networking (IP addresses, ports, firewalls)
- Basic security concepts (passwords, encryption, authentication)
- Willingness to learn Windows (not required upfront, but essential)

You don't need to know everything. Teams are balanced. If you're weak in an area, your teammates cover + teach you.

**Time:**
- Sept–Oct: ~2 hours/week for meetings + workshops
- Final 2-3 weeks: 3–5 hours/week with your team
- Competition day: Full day (usually Saturday, all day)

**Commitment:**
- Show up to events consistently
- Tell your team captain if you can't make something
- Contribute to prep (doesn't have to be technical — keeping morale up counts!)

---

## What You'll Learn

**Technical:**
- Linux system hardening (users, permissions, services, monitoring)
- Windows system hardening (registry, group policy, monitoring)
- Network security (firewalls, intrusion detection, monitoring tools)
- Incident response (what to do when you're attacked)
- Forensics (investigating after an attack)
- Open PLC / industrial control systems (real infrastructure security)
- CTF problem-solving (anomalies require creative thinking)

**Non-technical:**
- Communication (explaining technical stuff to non-technical people)
- Teamwork (coordinating 6 people under stress)
- Time management (balancing prep with classes)
- Dealing with failure (your defense will be broken at some point; how you respond matters)

---

## How Teams Are Structured

**Ideal team split (6 people):**
- 1 person: Green Team (maintains web application)
- 3 people: Vulnerability hunting (finding + documenting security issues)
- 2 people: Monitoring & hardening (setting up defenses, keeping systems secure)

**In practice:** It's flexible. Some teams swap people around. The point is you have diverse skills.

---

## Common Questions

**What if I don't know Linux/Windows?**
Perfect. That's what prep resources are for. Many people start knowing almost nothing.

**What if my team isn't balanced?**
That's what veterans + mentors are for. We can help identify gaps and fill them.

**Can I miss preparation events?**
Ideally no. But life happens. Just tell your team captain ASAP. The big issue is if whole teams go dark.

**What happens if we do really badly?**
You learn a ton. Seriously. Some of the best learning comes from failure. Past teams have scored low and still come back stronger next year.

**Is this just for people who want to work in cybersecurity?**
Not necessarily. Many people do it because it's fun, challenging, and looks good. Some go into security, others go into different fields. The skills help regardless.

---

## Before & After Competition

**Before (Sept–Nov):**
- Attend workshops + meetings
- Study 2024 anomalies (to get a sense of what to expect)
- Learn the technical tools (Linux, Windows, Open PLC, monitoring)
- Get comfortable with your team

**After (what you'll have):**
- Real security experience on your resume
- A network of friends who understand the grind
- Lessons learned (what worked, what didn't)
- Stories to tell (plus adrenaline junkie cred)
- Skills that make you more employable

---

## Next Steps

**Want to learn more?**
- Read [Competition Timeline](event-timeline.md) — understand the actual schedule
- Check [Team Structure & Roles](../team-formation/role-descriptions.md) — what team roles do
- Explore [CyberForce 2024 Repository](https://drive.google.com/drive/folders/1CMDQ8fPsviGhkE3nmA0YcQ7K8DPiedaM?usp=sharing) - 2024's CF team resources 
- Read [CyberForce 101 Library](https://cyberforce.energy.gov/cyberforce-101-library/) — official DoE resource

**Want to get involved?**
- Announce your interest on the CyberForce 2026 Interest Confirmation
- Attend the info session (early July)
- Ask questions in the #cyberforce discord channel

---

**Questions?** Ask in the #cyberforce channel on discord or DM @AJ

================================================================================
