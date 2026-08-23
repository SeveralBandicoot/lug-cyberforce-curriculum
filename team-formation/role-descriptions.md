================================================================================
# Team Roles & Responsibilities

**Last updated:** June 2026  
**Owner:** AJ
**For:** Competitors, team captains, admins

---

## Overview

CyberForce teams are 4–6 people. An ideal team has people with different skills + responsibilities. This document explains what each role does.

**Key principle:** You don't need to be an expert in your role. You learn as you go. The goal is **balanced teams**, not individual perfection.

---

## 🔧 Green Team (1 person, flexible)

**What they do:**
- Maintain the web application throughout competition
- Keep it running (don't break it)
- Secure it (find + fix vulnerabilities)
- Implement changes quickly (if red team exploits something)

**Skills needed:**
- Basic web development (HTML, CSS, JavaScript helpful)
- PHP or Python (framework varies year to year)
- Problem-solving under pressure

**During prep:**
- Study web frameworks (Laravel, Flask, etc.)
- Practice deploying + fixing web apps
- Learn what common vulnerabilities look like (SQL injection, XSS, etc.)
- Test your app under "attack" (intentional break + fix)

**During competition:**
- Monitor the web app (is it responding? Any errors?)
- Respond to attacks (red team breaks something, you fix it)
- Implement hardening (add security features)
- Document changes (what you did + why)

**Workload:** Medium-high (you're the single point of failure for the web app)

**Personality fit:** Detail-oriented, quick to respond, comfortable coding live

---

## 🔍 Vulnerability Hunters (3 people)

**What they do:**
- Explore the network during Week 2
- Find security issues (wrong configs, weak passwords, open ports, etc.)
- Document everything found
- Recommend fixes
- Prioritize what to fix first (some vulnerabilities matter more)

**Skills needed:**
- Basic Linux + Windows
- Curiosity + attention to detail
- Patience (finding vulnerabilities takes time)
- Documentation skills (write what you find)

**During prep:**
- Learn Linux + Windows basics
- Study past anomalies (see what kinds of issues exist)
- Practice port scanning + service enumeration
- Learn common vulnerability categories (weak auth, open ports, misconfiguration)

**During competition Week 2:**
- SSH into machines, explore them
- Use tools like nmap, netstat, system logs
- Document: what service running? What port? What's the vulnerability?
- Flag issues (critical vs. nice-to-have)
- Suggest fixes (not implement yet)

**Workload:** High during Week 2, medium during competition day (you help hunters + monitor status)

**Personality fit:** Detail-oriented, good at research, systematic, collaborative

---

## 🛡️ Monitoring & Hardening (2 people)

**What they do:**
- Set up defensive infrastructure (firewalls, monitoring, IDS)
- Implement vulnerability fixes
- Monitor systems during competition (is anything wrong? Any attacks?)
- Respond to incidents (something broke, fix it fast)
- Keep systems running

**Skills needed:**
- Linux + Windows system administration
- Monitoring tools (Wazuh, firewalls, logs)
- Problem-solving under pressure
- Understanding how systems talk to each other

**During prep:**
- Learn Linux + Windows hardening (users, permissions, services, firewalls)
- Study monitoring tools (Wazuh, syslog, Windows Event Log)
- Practice setting up monitoring (test in VMs)
- Learn incident response (something attacks your system, how do you react?)

**During competition Week 2:**
- Implement fixes from vuln hunters
- Set up monitoring tools (Wazuh agents, log aggregation)
- Configure firewalls (block malicious traffic)
- Set up alerting (get notified of problems)
- Test everything (make sure it works before competition)

**During competition day:**
- Monitor dashboards (Wazuh, logs, system status)
- Respond to alerts (something wrong → investigate → fix)
- Keep systems up (reboot if needed, restart services, etc.)
- Document incidents (what happened? How did you fix it?)

**Workload:** Very high during Week 2 + competition day, medium during prep

**Personality fit:** Calm under pressure, systematic, good at multitasking, enjoys troubleshooting

---

## 👥 Team Captain (Overlap Role)

**Who:** Usually one of the experienced people (could be any role)

**What they do:**
- Coordinate team logistics (meetings, deadlines, confusion)
- Be the point person for admins (communicate decisions)
- Check in on morale + team health
- Make sure everyone knows what's happening
- Resolve conflicts
- Lead team strategy discussions

**Responsibilities:**
- Schedule regular team meetings (biweekly minimum)
- Remind people of deadlines (C-Suite, security doc, competition day)
- Respond to admins when they ask questions
- Support people who are struggling
- Keep team organized + on track

**This is in addition to their role.** If you're a vulnerability hunter + team captain, you do both.

**Time:** ~1–2 hours/week extra (on top of other responsibilities)

**Personality fit:** Organized, communicative, empathetic, good at delegating

---

## 🎯 Ideal Team Composition

**6-person team:**
- 1 Green team
- 3 Vulnerability hunters
- 2 Monitoring & hardening

**Why?** 
- Green team needs dedicated attention (single point of failure)
- Vulnerability hunting is intensive (3 people can parallelize + cover lots of systems)
- Monitoring during competition is non-stop (2 people = one person rests while other watches)

**4-person team:**
- 1 Green team
- 2 Vulnerability hunters (overlap with monitoring)
- 1 Monitoring & hardening (overlap with hunting)

You'll all wear multiple hats. That's okay.

**5-person team:**
- 1 Green team
- 2 Vulnerability hunters
- 2 Monitoring & hardening (or 1.5 hunting + 1.5 hardening)

You figure out the balance based on skills.

---

## 🔄 Roles Can Change

**You don't have to commit to one role forever.**

- Vulnerability hunter who gets interested in monitoring? → Switch!
- Green team person wants to try hardening? → Go for it!
- Someone's struggling? → We'll help or rebalance

**This is prep season.** Roles are flexible. By competition, you'll know what fits best.

---

## 📊 Skill Requirements by Role

| Role | Linux | Windows | Web Dev | CTF | Calmness |
|------|-------|---------|---------|-----|----------|
| **Green team** | Good | Basic | Excellent | Good | Very good |
| **Vuln hunters** | Good | Good | Basic | Good | Good |
| **Monitoring** | Excellent | Excellent | Basic | Okay | Excellent |
| **Team captain** | Varies | Varies | Varies | Varies | Very good |

**Key:** You don't need to be excellent at everything. You need to be decent at your main area + willing to learn.

---

## 🎓 How to Prepare for Your Role

**If you're Green team:**
- Learn the framework CyberForce uses (Laravel, Flask, etc.)
- Practice: set up a test app, intentionally break it, fix it
- Study OWASP top 10 web vulnerabilities

**If you're a Vulnerability hunter:**
- Linux + Windows basics (watch YouTube tutorials)
- Network fundamentals (IP addresses, ports, DNS)
- Common vulnerability types (weak auth, misconfiguration, etc.)
- Tools: nmap, netstat, grep, file permissions
- Study 2024 anomalies (what did they look for?)

**If you're Monitoring & hardening:**
- Deep dive into Linux + Windows hardening
- Learn a monitoring tool (Wazuh, Splunk, syslog)
- Windows Event Log (what events matter?)
- Incident response basics (how to react to attacks)
- Firewall rules + network security

**If you're Team captain:**
- Be organized (keep notes, schedules)
- Communicate clearly (emails, Discord messages)
- Support your team (check in on morale)
- Escalate problems (if someone's struggling, tell admins)

---

## ⚠️ Common Mistakes

**Green team mistakes:**
- ❌ Waiting until competition to learn the framework
- ❌ Not hardening the app (just keeping it running)
- ❌ Not testing your app regularly

**Vulnerability hunter mistakes:**
- ❌ Finding issues but not documenting them
- ❌ Not testing if your fixes actually work
- ❌ Assuming all vulnerabilities are equal (some matter more)

**Monitoring mistakes:**
- ❌ Setting up monitoring but not watching it during competition
- ❌ Not practicing incident response beforehand
- ❌ Hardening so much you break the application

**Team captain mistakes:**
- ❌ Not checking in regularly (people get lost)
- ❌ Assuming people know deadlines (you have to remind them)
- ❌ Not supporting people who are struggling

---

## Mentorship by Role

**If you're experienced in a role, mentor someone:**
- Green team mentor: Helps new person learn the framework, practice deployment
- Vuln hunting mentor: Teaches systematic approach to finding issues
- Monitoring mentor: Helps set up tools, troubleshoot alerts
- Captain mentor: Guides communication, team logistics


---

## Questions About Roles?

- **Not sure which role fits you?** Talk to your team captain or AJ
- **Want to switch roles?** Tell your team captain (flexibility is fine during prep)
- **Need help with your role?** That's what resources + mentors are for
- **Is your role too much?** Talk to your team, rebalance if needed

---

**Last updated:** August 2026  
**Questions?** DM @AJ or ask in #cyberforce

================================================================================
