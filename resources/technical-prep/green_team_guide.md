================================================================================
# Green Team Technical Prep
Web Application Development & Maintenance

**Last updated:** August 2026  
**For:** Green Team role (1 person per CyberForce team)  
**Time to read:** 30 min

---

## Green Team Overview

**Your job:** Maintain the web application throughout the competition

**What this means:**
- The web app is a critical system that green team (simulated users) + scoreboard rely on
- You must keep it running 24/7 (or lose uptime points)
- You must apply security patches quickly when vulnerabilities found
- You must respond to user issues (green team requests)
- You must make quick CSS/content changes on demand

**Why it matters:**
- 2024 teams neglected web app → couldn't change website → lost points
- Uptime % is worth significant points
- Fast response to changes

---

## Prerequisites

Before starting this section, you should:
- [ ] Understand basic web concepts (HTTP, client-server model)
- [ ] Know what a framework is
- [ ] Be comfortable in Linux command line (basic navigation)
- [ ] Have some JavaScript familiarity (not expert, but basics)

**If you don't have these:** Read [/resources/technical-prep/technical-prep.md](technical-prep.md) fundamentals first.

---

## What You'll Be Working With

### **2024/2025 Framework: Laravel + PHP**

**Laravel** is a PHP web framework (backend logic)  
**PHP** is the server-side language (runs on server)  
**JavaScript** is for frontend interactivity (runs in browser)  
**CSS** is for styling (how it looks)  
**NPM** is a package manager (install libraries)

**Important:** Next year (2026) CyberForce (might) use a different framework. You'll need to learn it quickly when rulebook drops.

---

## Learning Path

### **1: Fundamentals**

**Goal:** Understand web app basics

**Read:**
- https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/ 
  - How the web works
  - Basic HTML/CSS/JavaScript intro

**Install & Practice:**
- [ ] Install VSCode (https://code.visualstudio.com/)
- [ ] Create simple HTML page with CSS
- [ ] Understand view-source in browser (inspect website structure)

---

### **2: JavaScript Basics**

**Goal:** Comfortable modifying JavaScript in web app

**Read & Practice:**
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide (start with basics)
  - Variables, functions, DOM manipulation
  - Don't memorize everything, understand concepts

**Practice:**
- [ ] Modify webpage JavaScript in browser console (Ctrl+Shift+K)
- [ ] Understand event listeners (button clicks, form submissions)
- [ ] Know how to find JavaScript in inspect element

**Why:** During comp, you might need to quick-fix broken JavaScript or add functionality

---

### **3: CSS Mastery**

**Goal:** Quick CSS changes under pressure

**Read & Practice:**
- https://developer.mozilla.org/en-US/docs/Learn/CSS (focus on selectors + styling)
- Understand:
  - CSS selectors (class, ID, element)
  - Common properties (color, font, width, display)
  - Box model (margin, padding, border)
  - Flexbox basics (layout)

**Practice:**
- [ ] Modify CSS on website (change colors, fonts, layout)
- [ ] Do it from browser inspector (test before editing file)
- [ ] Deploy changes (restart server)
- [ ] Ensure you can make changes in a timely manner 

---

### **4: Laravel Basics**

**Goal:** Understand Laravel structure so you can make quick changes

**Important:** You don't need to be a Laravel expert. You need to:
- Know where files are
- Understand the structure
- Be able to make quick changes
- Know how to restart the app

**Read:**
- Laravel documentation: https://laravel.com/docs/10.x (start with intro)
- Focus on:
  - Project structure (where files live)
  - Routes (how URLs map to pages)
  - Views (HTML templates)
  - Controllers (business logic)

**Practice:**
- [ ] Clone Laravel repo locally
- [ ] Run `composer install` + `npm install` (package managers)
- [ ] Run development server (`php artisan serve`)
- [ ] Modify a view (HTML template)
- [ ] See changes in browser
- [ ] Understand the file structure

**Key files to know:**
- `routes/web.php` — URL routing
- `resources/views/` — HTML templates
- `public/` — CSS, JavaScript, images
- `.env` — Configuration (database, app settings)
- `app/Http/Controllers/` — Business logic

---

### **5: Deployment & Patching**

**Goal:** Deploy changes + apply security patches quickly

**Read:**
- Laravel deployment guide: https://laravel.com/docs/10.x/deployment
- Understand:
  - How app runs on production server
  - What `php artisan` commands do
  - Database migrations (schema changes)
  - Environment configuration

**Practice:**
- [ ] Deploy to test server (cloud VM)
- [ ] Practice patching (update a package, restart app)
- [ ] Time yourself, ensure you can deploy changes in a timely manner
- [ ] Know the commands:
  ```bash
  git pull origin main           # Get latest code
  composer install              # Install PHP dependencies
  npm install && npm run build   # Install JS dependencies + build
  php artisan migrate            # Database schema updates
  php artisan config:cache       # Apply config changes
  # Restart web server (method depends on your setup)
  ```

**Reality check:** On competition day, you might need to do this in 5 minutes while under pressure. Practice!

---

## Tools You'll Use

### **Must Have:**
- **VSCode** or similar editor (https://code.visualstudio.com/)
- **Git** (version control, `apt-get install git`)
- **PHP** (comes with Laravel)
- **Node.js/NPM** (package manager, https://nodejs.org/)
- **Composer** (PHP package manager, https://getcomposer.org/)

### **Helpful:**
- **Browser DevTools** (Ctrl+Shift+K or F12)
  - Inspect elements
  - Console (run JavaScript)
  - Network tab (see requests)
- **SSH client** (to connect to server)
- **Database viewer** (if needed for debugging)

---

## 2026 Specific Tasks (When You Get Rulebook)

**First day (rulebook release):**
- [ ] Read rulebook carefully
- [ ] Identify website URL (`web:blue0001.cfc.local` or similar)
- [ ] Get production server access
- [ ] Deploy initial website
- [ ] Test that it works

**Week of prep:**
- [ ] Ensure site loads correctly
- [ ] Check all forms work (job submissions, login, etc.)
- [ ] Verify admin interface works
- [ ] Check footer/logos load
- [ ] Test file upload functionality
- [ ] Know how to quickly change:
  - Career positions listed
  - Admin user settings
  - Footer content
  - Logo images
  - Site styling

**Competition week:**
- [ ] Monitor uptime (is site loading?)
- [ ] Fix issues reported by green team (users)
- [ ] Apply security patches quickly
- [ ] Update content when scoreboard requests it
- [ ] Keep detailed logs of changes made

---


## Prep Timeline Example

| Week | Goals |
|------|-------|
| **Sept 1** | Read this page, understand role | 
| **Sept 2–3** | JavaScript basics, install tools | 
| **Sept 4–5** | CSS practice, modify websites | 
| **Sept 6–7** | Laravel setup, understand structure | 
| **Sept 8–9** | Deployment practice, patching | 
| **Oct 1–31** | Ongoing: CSS changes, Laravel updates | 
| **Nov 1–7** | Scenario release: deploy production site | 
| **Nov 8–13** | Finalize, test everything | 
| **Nov 14** | Competition day! | 

---

## Additional Resources

### **Video Tutorials (If You Prefer Video)**

**Laravel:**
- Laracasts (free intro): https://laracasts.com/
- [Brad Traversy YouTube](https://www.youtube.com/@TraversyMedia): Laravel tutorials

**JavaScript:**
- MDN JavaScript Guide: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide
- JavaScript.info: Interactive tutorials

**CSS:**
- CSS Tricks: https://css-tricks.com/ (articles + guides)
- Flexbox guide: https://css-tricks.com/snippets/css/a-guide-to-flexbox/

### **Practice Projects**

**Do these to get comfortable:**
- [ ] Modify an open-source Laravel project locally
- [ ] Create custom CSS theme for a website
- [ ] Write JavaScript to change page content on click
- [ ] Deploy a simple Laravel site to a test server

---

## Pre-Competition Checklist

By October 31, you should be able to:
- [ ] Explain what Laravel is + why it matters
- [ ] Navigate Laravel project structure
- [ ] Modify CSS in a running app + see changes
- [ ] Update website content (text, images)
- [ ] Commit changes to Git + deploy
- [ ] Run `php artisan` commands
- [ ] Restart web server
- [ ] Handle 2–3 requests per hour during crunch (late Nov)
- [ ] Deploy security patches in a timely manner

---

## If You Get Stuck

**Resource:** CyberForce 101 Library (section on Green Team)  
**People:** Ask hunters/monitoring team for help if stuck  
**Docs:** Read provided website README file carefully  
**Forum:** CyberForce has discussion forums + help tickets  

**Remember:** You can't receive help from outside your team during competition, but prep help is fine!

---

## Next Steps

1. [ ] Finish reading this page
2. [ ] Install VSCode + Git + Node.js
3. [ ] Do JavaScript basics tutorial 
4. [ ] Try modifying a CSS file 
5. [ ] Set up local Laravel project 
6. [ ] Practice deploying changes 
7. [ ] Report back questions to other team members of green team for technical help, for any modifications to this page DM @AJ

---

================================================================================
