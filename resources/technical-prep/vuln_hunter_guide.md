================================================================================
# Hunters Technical Prep
Vulnerability Finding & Anomaly Solving

**Last updated:** July 2026  
**For:** Vulnerability Hunters (3 people per CyberForce team)  
**Time to read:** 45 min

---

## Hunters Overview

**Your job:** Find security vulnerabilities and solve anomalies (CTF-style challenges)

**What this means:**
- Explore the network + systems to find weaknesses
- Solve mysterious challenges hidden in the infrastructure
- Enumerate services and identify attack vectors
- Document findings for security documentation
- Work under time pressure with tight deadlines

**Why it matters:**
- Anomalies worth [insert percentage] of total points
- Requires mix of technical skills + creative problem-solving
- "Know when to quit" on hard challenges (time management is critical)

---

## Prerequisites

Before starting this section, you should:
- [ ] Comfortable navigating Linux command line
- [ ] Basic understanding of networking (IP, ports, services)
- [ ] Problem-solving skills (CTF experience is huge plus)
- [ ] Willingness to google + learn on the fly

**If you don't have these:** Read [/resources/technical-prep/technical-prep.md](technical-prep.md) fundamentals first.

---

## What You'll Be Hunting For

### **Anomalies (CTF-style Challenges)**

- **Steganography:** Image with hidden data → Extract it
- **Cryptography:** Encrypted message → Crack it
- **Reverse engineering:** Binary file → Understand what it does
- **Forensics:** Log file → Find evidence of attacker activity
- **Radio signals:** RF data → Decode it
- **Privilege escalation:** Limited user → Become root
- **Web exploitation:** Web app → Find SQL injection or XSS

---

### **Vulnerabilities (Real Security Issues)**

These are actual exploitable flaws in systems:

- **Open ports:** Unnecessary services running
- **Weak credentials:** Default passwords not changed
- **Misconfigurations:** Services set up insecurely
- **Permissions errors:** Files/folders accessible by wrong users
- **Known CVEs:** Outdated software with published vulnerabilities
- **Reverse shells:** Attacker backdoors hidden in cron jobs or scripts

**Your job:** Find these BEFORE red team does, so you can patch them.

---

## Learning Path

### **1: Linux Fundamentals**

**Goal:** Comfortable navigating Linux systems

**Reading + Exercises:**
- https://pwn.college/linux-luminarium/ (Linux fundamentals)
  - Command line basics (navigation, file operations)
  - Users & permissions (chmod, chown, sudo)
  - Process management (ps, kill, systemctl)
  - Services (systemctl, service commands)

**Practice:**
- [ ] Set up Linux VM (VirtualBox)
- [ ] Practice navigation + file operations  
- [ ] Create users, change permissions 
- [ ] Start/stop services

---

### **2: Windows Fundamentals**

**Goal:** Navigate Windows systems for vulnerabilities

**Read:**
- Windows security basics
  - Command Prompt vs PowerShell
  - User accounts + groups
  - Registry basics (don't edit, just understand)
  - Services + startup programs
  - Event logs (what they are, not analyzing yet)

**Practice:**
- [ ] Set up Windows VM (VirtualBox)
- [ ] Navigate file system via cmd
- [ ] List users & groups (`whoami /all`, `net user`)
- [ ] View services (`Get-Service` in PowerShell)
- [ ] Check startup programs

---

### **3: Enumeration Tools**

**Goal:** Use tools to scan systems + find services

**Learn & Practice:**

**NMap (Network Mapping)**
- https://nmap.org/docs.html
- **What:** Scan networks for open ports + services
- **Why:** Identify what's running on systems
- **Practice:**
  ```bash
  nmap 10.0.190.0/24              # Scan network
  nmap -p 1-65535 10.0.190.145    # Scan all ports
  nmap -sV 10.0.190.145            # Detect service versions
  ```

**Grep + File Analysis**
- **What:** Search files for sensitive info
- **Why:** Find credentials, config errors, suspicious entries
- **Practice:**
  ```bash
  grep -r "password" /etc/         # Find password mentions
  grep -r "root" /var/log/         # Find root access attempts
  grep "sudo" /var/log/auth.log    # Find sudo usage
  ```

**Port Scanning Basics**
- **What:** Connect to ports to identify services
- **Why:** Validate what's running
- **Practice:**
  ```bash
  nc -zv 10.0.190.145 22          # Check SSH
  telnet 10.0.190.145 80          # Check HTTP
  ```

---

### **4: CTF Fundamentals**

**Goal:** Comfortable solving CTF challenges (anomalies are CTFs)

**Attend CTF Group CTFs**
- **Document:** Write down how you solved it
- **Difficulty curve:** Start easy, work up to harder challenges

**Key strategies:**
- Understand the challenge (read carefully)
- Identify what format the answer is (flag, number, text?)
- Use available tools (see anomaly tools section below)
- Google for hints (searching is allowed in CTFs)
- Don't spend >1 hour on one challenge (move on, return later)

---

### **5: Anomaly Tools**

**Goal:** Know which tool to use for which challenge

**Install all of these:**

**Steghide** (Steganography)
- Extract hidden data from images
- Install: `apt-get install steghide`
- Use: `steghide extract -sf image.jpg`

**John the Ripper + Hashcat** (Password Cracking)
- Crack password hashes
- Install: `apt-get install john hashcat`
- Use:
  ```bash
  john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
  hashcat -m 1400 hashes.txt rockyou.txt
  ```

**NMap** (Network Mapping)
- Already covered above
- Install: `apt-get install nmap`

**CyberChef** (Data Transformation)
- Encode/decode, base64, cipher operations
- Access: https://cyberchef.io/ (web-based, no install needed)
- Why: Many anomalies require encoding/decoding

**Python** (Custom Scripts)
- Write tools for unique challenges
- Usually pre-installed
- Basics: read/write files, string manipulation, base64, hashing

**Universal Radio Hacker (URH)** (RF Analysis)
- Analyze radio signals
- Install: `pip install urh`
- Use: GUI application for signal analysis

**Docker** (Containerization)
- Run containerized applications
- Install: https://docs.docker.com/get-docker/
- Use: `docker run`, `docker inspect`

**Git** (Version Control)
- Analyze git repositories
- Install: `apt-get install git`
- Use: `git log`, `git diff`, git forensics

**Autopsy** (Digital Forensics)
- Recover files, analyze disks
- Install: Download from https://www.sleuthkit.org/autopsy/
- Use: GUI for file recovery + disk analysis

**Ghidra** (Reverse Engineering)
- Disassemble binary files
- Download: https://ghidra-sre.org/
- Use: Analyze compiled programs

**Okteta** (Hex Editor)
- View/edit binary files
- Install: `apt-get install okteta`
- Use: Low-level binary analysis

**WinDebug** (Windows Debugging)
- Debug Windows programs
- Install: Part of Windows SDK
- Use: Analyze binary behavior

**The Fluffy Suite** (Specialized)
- [Note: Research this from CF documentation]
- [Purpose: [Find specific anomaly type]
- Install: [Find installation method]


---

### **6: Hands-On Practice**

**Solve a majority of the CTF challenges from CTF events (challenges will still be open after events)**

**Goal:** Build speed + confidence

**Strategy:**
- Solve easy ones first (build momentum)
- Document your process (helps you remember)
- Try multiple solutions (different ways to solve)


---

## Enumeration Process - Starts once we recieve access to the servers+rulebook (Phase 2)

**Step 1: Reconnaissance (First few hours)**

Your job: Understand the network completely

**Steps:**
1. **Map the network** (NMap scan)
   ```bash
   nmap -sV 10.0.190.0/27
   ```
   → Identify all systems + services running

2. **Create network diagram**
   - Host: webserver (nginx, SSH, NFS)
   - Host: database (MySQL, RDP)
   - Host: AD server (LDAP, WinRM)
   - Host: Task box (SMTP, IMAP, SSH)
   - Host: HMI (web interface, MySQL)
   - Host: PLC (modbus port 502)

3. **List required services**
   - Compare what's running vs what should be running
   - Flag anything unexpected

4. **Document everything**
   - IP, hostname, OS, ports, services
   - This is your team's "asset inventory"


---

**Step 2: Vulnerability Finding**

Your job: Find exploitable weaknesses

**Check for:**
- Unnecessary services (disable them)
- Default credentials (change them)
- Known CVEs (update software)
- Open shares (restrict access)
- Weak permissions (fix them)
- Suspicious files (analyze them)

**Tools to use:**
- File analysis: `find`, `ls -la`, `grep`
- Permission checks: `stat`, `getfacl`
- Network services: `ss`, `netstat`
- Process checks: `ps aux`
- Log analysis: `tail -f`, `grep`


---

**Step 3: Anomaly Solving**

Your job: Solve challenges

**Approach:**
1. Read challenge carefully
2. Identify what's being asked
3. Pick right tool(s)
4. Solve it
5. Document solution
6. Submit answer
7. Move to next


---

## Prep Timeline Example

| Week | Goals |
|------|-------|
| **Sept 1** | Read this page |
| **Sept 2** | Linux fundamentals + practice |
| **Sept 3** | Windows fundamentals + practice |
| **Sept 4–5** | Enumeration tools (NMap, grep) |
| **Sept 6–7** | CTF fundamentals + solve 5 anomalies |
| **Sept 8–9** | Install all anomaly tools |
| **Oct 1–31** | Solve 10–20 more anomalies |
| **Nov 1–7** | Rulebook+server release: network enumeration |
| **Nov 8–13** | Anomaly solving + vulnerability finding |
| **Nov 14** | Competition day! |

---

## Additional Resources

### **Hands-on Practice**

**TryHackMe** (CTF-style training)
- https://tryhackme.com/
- Free rooms with guidance
- Good stepping stone before CTF Group CTFs

**HackTheBox** (Real-world challenges)
- https://www.hackthebox.eu/
- Harder than TryHackMe
- More realistic scenarios

**CTFTime** (writeups from past CTFs)
- https://ctftime.org/
- See how others solved challenges
- Learn different approaches

### **Reading Material**

**MITRE ATT&CK Framework**
- https://attack.mitre.org/
- Understand attacker techniques
- Know what you're looking for in logs

**CyberChef Recipes**
- https://cyberchef.io/
- Search for common encoding/decoding
- Copy + modify recipes for your challenges

---

## Pre-Competition Checklist

By October 31, you should be able to:
- [ ] Explain what anomalies are
- [ ] Run NMap + interpret results
- [ ] Use grep to search files
- [ ] Extract data with Steghide
- [ ] Crack password hashes (John/Hashcat)
- [ ] Solve CTF challenges in <1 hour each
- [ ] Use CyberChef for encoding/decoding
- [ ] Write simple Python scripts
- [ ] Use Ghidra for reverse engineering basics
- [ ] Document findings clearly
---

## If You Get Stuck

**For tool help:** YouTube tutorials + official documentation  
**For anomaly help:** Try TryHackMe or HackTheBox similar challenges  
**For ideas:** CyberChef recipes + CTFTime writeups  
**For team questions:** Ask monitoring team if anomaly involves system access  

**Remember:** You can't get outside help during competition, but prep help is fine!

---

## Next Steps

1. [ ] Finish reading this page
2. [ ] Set up Linux + Windows VMs (VirtualBox)
3. [ ] Practice Linux + Windows navigation 
4. [ ] Install NMap + practice scanning
5. [ ] Install all anomaly tools
6. [ ] Any questions regarding this page? Reach out to @AJ

---

================================================================================
