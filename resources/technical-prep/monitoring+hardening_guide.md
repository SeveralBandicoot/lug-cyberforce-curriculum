================================================================================
# Monitoring & Hardening Technical Prep
Defensive Infrastructure & Security Monitoring

**Last updated:** August 2026  
**For:** Monitoring & Hardening role (2 people per CyberForce team)  
**Time to read:** 45 min

---

## Monitoring & Hardening Overview

**Your job:** Defend the network + detect/respond to attacks

**What this means:**
- Harden systems BEFORE competition starts (strong baseline)
- Monitor systems DURING competition (detect attacks)
- Respond quickly when attacks detected (mitigate damage)
- Maintain uptime while under attack (keep services running)
- Document everything (needed for security documentation)

**Why it matters:**
- Hardening PREVENTS exploits (proactive defense)
- Monitoring DETECTS attacks (reactive defense)
- Response speed MINIMIZES damage (tactical defense)
- Uptime = points 
- System knowledge = foundation (other roles build on this)

---

## Prerequisites

Before starting this section, you should:
- [ ] Comfortable navigating Linux + Windows systems
- [ ] Basic understanding of networking (ports, services, firewalls)
- [ ] Willingness to read logs + debug systems
- [ ] Patience (hardening is tedious + detail-oriented)

**If you don't have these:** Read `/resources/technical-prep/technical-prep.md` fundamentals first.

---

## What You'll Be Defending

### **Traditional Infrastructure (Hardened by You)**

Systems you can configure before competition when phase 2 starts once rulebook+servers are released:

- **Web Server (Linux: OpenSUSE Leap 15)**
  - Services: HTTP (nginx), SSH, NFS
  - Your job: Harden these services, remove unnecessary ones

- **Task Box (Linux: Ubuntu 22.04)**
  - Services: SSH, SMTP, IMAP, SMB (some might be unnecessary)
  - Your job: Disable unused services, harden enabled ones

- **Database Server (Windows Server 2022)**
  - Services: SMB, phpmyadmin (HTTP), MariaDB, RDP
  - Your job: Set strong DB passwords, firewall rules, Windows hardening

- **AD/DNS Server (Windows Server 2019)**
  - Services: LDAP (Active Directory), WinRM
  - Your job: Set strong AD passwords, Group Policy hardening

### **Assume Breach Infrastructure (Intentionally Vulnerable)**

Systems you CANNOT harden (but must monitor + respond):

- **HMI (Windows Server 2019)** - Human Machine Interface for industrial control
- **PLC (Ubuntu 22.04)** - Programmable Logic Controller

**Important:** Red team will attack these systems. Your job is to detect attacks QUICKLY + document what happened.

---

## Learning Path

### **1: Linux Hardening Fundamentals**

**Goal:** Understand Linux security best practices

**Read:**
- CIS Linux Benchmarks: https://www.cisecurity.org/cis-benchmarks/
  - Focus on: User management, permissions, services, authentication
- Linux security basics:
  - User + group management (sudoers, groups)
  - File permissions (chmod, umask, ACLs)
  - Service management (systemctl, disabling services)
  - SSH hardening (key-based auth, disable root login)

**Practice:**
- [ ] Create Linux VM (VirtualBox)
- [ ] Create users + set permissions
- [ ] Configure SSH key-based auth
- [ ] Disable unnecessary services

---

### **2: Windows Hardening Fundamentals**

**Goal:** Understand Windows security configuration

**Read:**
- Windows Security Baseline: https://learn.microsoft.com/en-us/windows/security/operating-system-security/device-management/windows-security-configuration-framework/windows-security-baselines
- Focus on:
  - Password policy (strength, age)
  - User account control (UAC)
  - Firewall configuration
  - Service startup settings
  - Group Policy basics

**Practice:**
- [ ] Create Windows VM (VirtualBox)
- [ ] Set strong password policy
- [ ] Configure Windows Firewall
- [ ] Disable unnecessary services

---

### **3: Logging & Log Analysis**

**Goal:** Understand what logs tell you + how to find attacks

**Linux Logs:**
- `/var/log/auth.log` — Authentication attempts (who logged in when)
- `/var/log/syslog` — System messages
- `/var/log/audit/audit.log` — Detailed system activity (if auditd installed)
- Application logs — Varies by service (nginx, MySQL, etc.)

**Windows Logs:**
- Event Viewer > Security — Security events (logins, privilege changes)
- Event Viewer > System — System errors + warnings
- Event Viewer > Application — Application events

**Practice:**
- [ ] View Linux logs (`tail -f /var/log/auth.log`)
- [ ] Watch logs in real-time 
- [ ] Identify failed login attempts
- [ ] View Windows Event Viewer
- [ ] Identify security events

---

### **4: Firewall Configuration**

**Goal:** Restrict network access to only required services

**Linux Firewalls (UFW):**
- Allow only required ports/services
- Deny everything else
- Practice:
  ```bash
  sudo ufw default deny incoming
  sudo ufw default allow outgoing
  sudo ufw allow 22/tcp              # SSH
  sudo ufw allow 80/tcp              # HTTP
  sudo ufw allow 443/tcp             # HTTPS
  sudo ufw enable
  ```

**Windows Firewall:**
- Configure inbound/outbound rules
- Allow required services
- Deny suspicious traffic
- Practice via GUI + PowerShell

**Key concept:** Principle of least privilege — only allow what's necessary


---

### **5: Monitoring Tools**

**Goal:** Know which tools to use for monitoring

**Wazuh (Intrusion Detection + Log Analysis)**
- https://wazuh.com/
- **What:** Agent-based threat detection system
- **Why:** Detects attacks via log analysis + file integrity monitoring
- **Setup:** Install manager + agents on systems
- **Key ports:** Manager 1514/1515/1516/55000, Indexer 9200/9300

**Prometheus (Metrics Monitoring)**
- https://prometheus.io/
- **What:** Time-series database for system metrics
- **Why:** Monitor CPU, memory, disk, network in real-time
- **Setup:** Install + configure scrape targets

**Zeek (Network Monitoring)**
- https://zeek.org/
- **What:** Advanced network traffic analysis
- **Why:** Log all network connections for forensics
- **Setup:** Install + configure on gateway

**Bloodhound (AD Vulnerabilities)**
- https://github.com/BloodHoundAD/BloodHound
- **What:** Visualize Active Directory attack paths
- **Why:** Identify privilege escalation routes in AD
- **Setup:** Install Community Edition

---

### **6: Audit Logs & System Monitoring**

**Goal:** Use detailed logs to detect + respond to attacks

**auditctl (Linux Audit Framework)**
- Track system calls + events
- **Key use:** Detect file modifications, command execution
- **Practice:**
  ```bash
  sudo auditctl -w /etc/passwd -p wa    # Monitor passwd file changes
  sudo auditctl -a always,exit -F arch=b64 -S execve -k exec  # Monitor commands
  sudo aureport --summary                # View reports
  sudo ausearch -k exec                  # View executions
  ```

**Blue Team Dashboard (Real-time Monitoring)**
- **Command:**
  ```bash
  sudo watch -n 2 '
    echo "==== RUNNING PROCESSES ====";
    ausearch -k command-execution | tail -10;
    echo "";
    echo "==== RECENT FILE CHANGES ====";
    ausearch -ts recent -f | tail -5;
  '
  ```
- **What:** Updates every 2 seconds, shows suspicious activity
- **Why:** Quick way to spot attacks during competition

---

## Hardening Process (During Prep)

### **Stage 1: Reconnaissance**

**Your goal:** Understand the systems completely

1. **Enumerate everything**
   ```bash
   nmap -sV 10.0.190.0/27              # What services are running?
   ```

2. **List all accounts** (who shouldn't be there?)
   ```bash
   cat /etc/passwd
   net user                            # Windows
   ```

3. **Check permissions** (what's accessible to what users?)
   ```bash
   ls -la /etc/
   icacls C:\                          # Windows
   ```

4. **Review startup programs** (unnecessary things running?)
   ```bash
   systemctl list-unit-files | grep enabled
   Get-Service | Where-Object {$_.StartType -eq 'Automatic'}  # Windows
   ```

5. **Create network diagram** (visual of systems)
   - Document every host + service

---

### **Stage 2: Hardening**

**For each system, do:**

**Remove unnecessary services**
```bash
sudo systemctl disable telnet.service  # Disable old/insecure services
sudo systemctl stop telnet.service
```

**Set strong credentials**
```bash
# Change default passwords
sudo passwd username                   # Linux
net user Administrator NewPassword     # Windows
```

**Configure authentication**
- SSH key-based auth only (disable password login)
- Windows: Strong password policy
- AD: Enforce complex passwords

**Set permissions correctly**
```bash
# Remove overly permissive access
chmod 640 /etc/shadow                  # Only root can read
chmod 750 /etc/sudoers.d/              # Only root can modify sudo
```

**Harden services**
- Nginx: Disable server tokens, set security headers
- SSH: Disable root login, set PermitEmptyPasswords no
- Database: Change default passwords, limit network access

**Configure firewalls**
- UFW (Linux): Allow only required ports
- Windows Firewall: Same principle


---

### **Stage 3: Monitoring Setup**

**Install monitoring systems**

1. **Wazuh agent** on each system
   - Collect logs
   - Alert on suspicious activity

2. **Audit daemon** (Linux)
   - Monitor file changes
   - Track command execution

3. **Prometheus** (if using)
   - Monitor metrics
   - Set alerts for anomalies

4. **Configure dashboards**
   - View real-time alerts
   - See what's happening

---

## During Competition: Detection & Response

### **Stage 1: Continuous Monitoring (Competition Day)**

**Your job:** Watch for attacks

**Every hour, check:**
1. **Log files** (any suspicious activity?)
   ```bash
   tail -50 /var/log/auth.log           # Recent logins
   tail -50 /var/log/audit/audit.log    # Recent commands
   ```

2. **Running processes** (anything unexpected?)
   ```bash
   ps aux | grep -v grep               # What's running?
   ```

3. **Network connections** (unauthorized traffic?)
   ```bash
   ss -tulpn | grep LISTEN             # Open ports
   netstat -tulpn                      # All connections
   ```

4. **File changes** (modified systems?)
   ```bash
   find /etc -type f -mtime -1         # Files changed in last day
   ```

5. **System resources** (under attack - high CPU/memory?)
   ```bash
   top
   free -h                             # Memory usage
   ```

---

### **Stage 2: Attack Detection & Response (During Competition)**

**When you detect an attack:**

1. **Log everything** (for documentation)
   - What happened?
   - When?
   - How did you detect it?

2. **Isolate the issue** (if safe)
   - Kill rogue processes
   - Remove suspicious cron jobs
   - Block attacking IP (firewall)

3. **Mitigate** (stop it from spreading)
   - Apply security patch
   - Change compromised passwords
   - Remove backdoors

4. **Restore** (get back to normal)
   - Restart service if needed
   - Verify system integrity
   - Ensure required services still work

5. **Document** (for security documentation)
   - What was the vulnerability?
   - How did attacker exploit it?
   - How did you detect it?
   - What did you do to fix it?

---

## 💡 Common Mistakes to Avoid

❌ **Over-hardening and breaking services**
- Disable SSH, now can't access system remotely
- Tighten firewall, now required service is blocked
- → System down, lost uptime points

✅ **How to avoid:**
- Test hardening in lab first
- Verify required services still work
- Have rollback plan (snapshots, backups)

---

❌ **Ignoring monitoring**
- Only hardening, no monitoring setup
- Attack happens, don't detect it
- Red team freely exploits system
- → Lost points, lost uptime

✅ **How to avoid:**
- Set up monitoring DURING prep
- Configure alerts
- Practice responding to alerts

---

❌ **Making enemies of hunters**
- Hunters try to enumerate, you blocked all ports
- Green team can't access web app, you set firewall too strict
- → Team conflict during competition

✅ **How to avoid:**
- Work with hunters to understand what MUST be accessible
- Only block unnecessary services
- Communicate before major changes

---

❌ **Not documenting**
- Harden system, fix vulnerabilities, forget what you did
- Can't explain to orange team (C-suite)
- → Lost documentation points

✅ **How to avoid:**
- Keep detailed notes (what you hardened + why)
- Screenshots of configuration
- List of vulnerabilities found + mitigations

---

## Prep Timeline Example

| Week | Goals |
|------|-------|
| **Sept 1** | Read this page |
| **Sept 2** | Linux hardening fundamentals |
| **Sept 3** | Windows hardening fundamentals |
| **Sept 4–5** | Logging & log analysis practice |
| **Sept 6–7** | Firewall configuration practice |
| **Sept 8–9** | Monitoring tools setup (local) |
| **Sept 10–11** | Audit logs + blue team dashboard |
| **Oct 1–31** | Practice hardening VMs |
| **Nov 1–7** | Scenario release: harden AWS systems |
| **Nov 8–13** | Finalize monitoring + respond to testing |
| **Nov 14** | Competition day! |

---

## Additional Resources

### **Hardening References**

**Linux:**
- CIS Linux Benchmarks: https://www.cisecurity.org/cis-benchmarks/
- Ubuntu security guide: https://wiki.ubuntu.com/SecurityTeam

**Windows:**
- Microsoft Security Baseline: https://learn.microsoft.com/en-us/windows/security/
- Windows Hardening Guide: CISA guides

### **Monitoring & Detection**

**Wazuh:**
- Official docs: https://documentation.wazuh.com/
- YouTube tutorials

**Zeek:**
- Official docs: https://docs.zeek.org/
- Example scripts

**Prometheus:**
- Official docs: https://prometheus.io/docs/

---

## Pre-Competition Checklist

By October 31, you should be able to:
- [ ] Explain Linux vs Windows hardening differences
- [ ] Configure SSH key-based authentication
- [ ] Set strong password policies (both OS)
- [ ] Configure firewall rules (both OS)
- [ ] Disable unnecessary services
- [ ] Read and interpret Linux logs
- [ ] Use Windows Event Viewer
- [ ] Install + configure Wazuh agent
- [ ] Set up monitoring dashboards
- [ ] Detect simulated attacks in logs
- [ ] Respond to attack (isolate, mitigate, document)
- [ ] Explain all hardening + monitoring decisions clearly

---

## If You Get Stuck

**For hardening help:** CIS Benchmarks + official OS hardening guides  
**For monitoring help:** Tool documentation + YouTube tutorials  
**For ideas:** Ask hunters about services they need accessible  
**For response help:** Ask if hardening broke something (troubleshoot together)

**Remember:** You can't get outside help during competition, but prep help is fine!

---

## Next Steps

1. [ ] Finish reading this page
2. [ ] Set up Linux + Windows VMs (VirtualBox)
3. [ ] Practice hardening 
4. [ ] Install monitoring tools locally
5. [ ] Practice hardening + monitoring together
6. [ ] Any questions regarding this page? Reach out to @AJ

---


================================================================================
