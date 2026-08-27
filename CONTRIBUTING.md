================================================================================
# CONTRIBUTING.md
How to Update & Maintain This Repo

**Last updated:** June 2026  
**Maintained by:** AJ & LUG CTF Group Admin Team

---

## Why This Exists

This repo is the single source of truth for CyberForce curriculum. If you're updating materials, running an event, or learning from past years, you might want to add something here.

**Goal:** Keep this repo useful, organized, and easy to navigate.

---

## Before You Write

**Ask yourself:**

1. **Does this belong in the repo?**
   - ✅ General knowledge, templates, processes, lessons learned
   - ✅ Event planning guides, agendas, talking points
   - ✅ Technical prep materials (if original or curated)
   - ❌ Personal notes, in-progress drafts (use GitHub Issues instead)
   - ❌ Sensitive info (budgets, personal emails, private chat logs)

2. **Does this already exist?**
   - Search the repo first (Ctrl+F)
   - Check GitHub Issues (might be in progress)
   - Ask in #cyberforce discord channel if unsure

3. **Is this temporary or permanent?**
   - Temporary → GitHub Issue (with label `in-progress`)
   - Permanent → Add to repo with "Last updated" date

---

## File Organization

### **Naming Conventions**

**Folders:** lowercase, hyphens
```
/events/welcome-event/
/resources/technical-prep/
/team-formation/
```

**Files:** lowercase, hyphens, `.md` extension
```
cyberforce-101.md
competition-timeline.md
red-team-guide.md
```

**Avoid:**
```
❌ CyberForce 101.md (spaces, uppercase)
❌ CF-timeline (no extension)
❌ RED TEAM GUIDE.MD (wrong case)
```

### **Where Does It Go?**

| Content | Folder |
|---------|--------|
| What is CyberForce? How does it work? | `/docs/` |
| Linux, Windows, PHP, Open PLC tutorials | `/resources/technical-prep/` |
| Tools setup (Wazuh, monitoring, etc.) | `/resources/tools/` |
| Welcome event, C-Suite, info session materials | `/events/[event-name]/` |
| Team formation, roles, balancing guide | `/team-formation/` |
| Sept, Oct, Nov weekly prep schedule | `/competition-prep/` |
| Announcements templates, sent announcements | `/announcements/` |
| Scorecards, lessons learned, team reports | `/archival/` or `/scorecards-feedback/` |
| Admin notes, decisions, budget | `/admin/` |
| Templates for future years | `/templates/` |

---

## File Format (Template)

Every file should have this structure:

```markdown
# [Title]

**Last updated:** [Month Year]  
**Owner:** [Your name or "Team"]  
**For:** [Who this is for: competitors, admins, veterans, etc.]

---

## Overview
[What is this? Why does it exist? Who needs it?]

## Key Info
[Main content, organized with headers]

### Subsection 1
[Details]

### Subsection 2
[Details]

## Tips / Lessons Learned
[What worked? What didn't?]

## TODO for Next Year
- [ ] Task 1
- [ ] Task 2

---

**Questions?** Contact [name] or ask in #cyberforce-chat

**Last updated:** [Date]
```

### **Example:**

```markdown
# C-Suite Briefing Prep Guide

**Last updated:** October 2026  
**Owner:** AJ  
**For:** CyberForce competitors

---

## Overview
The C-Suite briefing is a recorded video presentation where your team explains the breach scenario, your response plan, and resource requests. It's due 1 week after the scenario drops.

## Timeline
- Scenario drops (date TBA)
- C-Suite briefing due 7 days later
- Video is 5–10 minutes, max 2 presenters (team can help write)

## How to Prep
1. Read the scenario carefully
2. Draft talking points (1–2 pages)
3. Practice reading them (time yourself)
4. Record in a quiet space
5. Review, reshoot if needed

## Tips from Veterans
- Divide the script so no one person practices too much (less reshoot burnout)
- Record multiple takes (it's okay to mess up)
- Wear business casual (or a suit if you're feeling fancy)
- Background doesn't matter much (use any quiet room)

## TODO for 2027
- [ ] Record video of good C-Suite example
- [ ] Get feedback from teams about prep process

---

**Questions?** DM AJ or ask in #cyberforce-chat
```

---

## Writing Style

- **Clear > fancy** — use simple language
- **Scannable** — use headers, bullets, short paragraphs
- **Specific** — include dates, names, links when relevant
- **Honest** — mention what was hard, what failed, lessons learned
- **Helpful** — assume reader has no context

### **Don't:**
- ❌ Write like an academic paper
- ❌ Use jargon without explaining it
- ❌ Make assumptions about what people know
- ❌ Leave tasks vague ("do the thing")

### **Do:**
- ✅ Write for someone encountering this for the first time
- ✅ Use examples ("For example, the 2025 teams...")
- ✅ Link to related files
- ✅ Add "Last updated" dates

---

## Linking

**Within repo:**
```markdown
[CyberForce 101](docs/cyberforce101.md)
[Team Structure](team-formation/role-descriptions.md)
```

**External links:**
```markdown
[CyberForce 101 Library](https://cyberforce.energy.gov/cyberforce-101-library/)
[CyberForce 2024 Team Google Drive](https://drive.google.com/drive/folders/1CMDQ8fPsviGhkE3nmA0YcQ7K8DPiedaM?usp=sharing)
```

**Always use descriptive link text:**
```markdown
✅ [CyberForce 101 Library](url)
❌ [Click here](url)
```

---

## Updating Existing Files

**Before you edit:**
1. Check "Last updated" date — is this stale?
2. Read the file — understand the current content
3. Make your change
4. Update the "Last updated" date

**What counts as an update:**
- ✅ Adding new information
- ✅ Fixing typos or clarity
- ✅ Updating dates or links
- ✅ Adding a tip from experience
- ✅ Marking something `[OUTDATED]`

**Commit message:**
```
Updated C-Suite guide with 2026 tips
Updated registration deadline info
Fixed broken link in resources
Added Windows hardening checklist
```

---

## Adding New Files

**Do:**
1. Follow the file format template above
2. Use consistent naming (lowercase, hyphens)
3. Add "Last updated" + "Owner"
4. Add to the appropriate folder
5. Link from README or related files
6. Create a GitHub Issue: "Added X guide, ready to review"

**Example GitHub Issue:**
```
Title: [NEW] C-Suite Recording Tips Guide

I added a new guide in `/events/c-suite-prep/recording-tips.md` 
with tips from 2026 teams about how to record videos.

Ready for review. Any feedback?
```

---

## GitHub Issues & Organization

**Create an Issue if:**
- You're working on something (so people know not to duplicate effort)
- Something needs updating but you don't have time now
- You found a mistake/bug in the repo
- You have an idea but want feedback first

**Label it:**
- `documentation-needed` — something should be documented
- `in-progress` — you're working on it
- `2027-planning` — for next year's lead
- `red-team` — red team stuff
- `event-planning` — event-related
- `technical-prep` — technical content
- `bug` — something's broken

**Example Issue:**
```
Title: Document 2025 lessons learned

After the 2025 competition, we identified these gaps:
- Windows hardening (not enough prep time)
- Anomaly practice (need more CTF skills training)
- Red team planning (should start earlier)

We should document these in `/docs/common-pitfalls.md` 
and plan 2026 accordingly.

Assigned to: AJ
Due: June 2026
```

---

## What NOT to Add

**Don't commit:**
- ❌ Personal contact info (emails, phone numbers)
- ❌ Budget details (amounts, who paid what)
- ❌ Private messages or chats
- ❌ Unfinished drafts (use Issues instead)
- ❌ Duplicate files (link, don't copy)
- ❌ Large files (images, videos)

**If you accidentally committed something private:**
1. Tell AJ immediately
2. Remove it with `git rm`
3. Don't panic (happens to everyone)

---

## Archival (After Competition)

**Right after competition (within 1 week):**
- [ ] Collect team scorecards from CyberForce
- [ ] Ask teams to write a quick report (what went well? what was hard?)
- [ ] Add to `/archival/[year]/`
- [ ] Update `/archival/red-team-knowledge/` with red team insights
- [ ] Create summary doc: `/archival/[year]-competition-summary.md`

**Before next June:**
- [ ] Review lessons learned
- [ ] Update `/docs/common-pitfalls.md`
- [ ] Plan changes for next year
- [ ] Update `/HANDOFF.md` with new insights

**Files to create each year:**
```
/archival/
  ├── 2026-competition-summary.md
  ├── 2026-team-reports/
  │   ├── lug-team-1-report.md
  │   └── lug-team-2-report.md
  └── 2026-lessons-learned.md
```

---

## Checklist Before Submitting

- [ ] File follows naming conventions (lowercase, hyphens, `.md`)
- [ ] File has "Last updated", "Owner", "For" section
- [ ] Content is in the right folder
- [ ] Links are working (test them!)
- [ ] Writing is clear & scannable
- [ ] Added to README or related files
- [ ] Commit message is descriptive
- [ ] TODO section added (if applicable)

---

## Example: How to Add Something

**Scenario:** You want to add a guide on "How to Use Wazuh"

**Steps:**

1. Create file: `/resources/tools/wazuh-setup.md`
2. Follow template:
   ```markdown
   # Wazuh Setup Guide
   
   **Last updated:** June 2026
   **Owner:** Michael
   **For:** Teams setting up monitoring
   
   [content...]
   ```
3. Link from `/resources/tools/README.md` or relevant files
4. In `/README.md`, add link to the new file
5. Commit with message: `Added Wazuh setup guide with 2026 configurations`
6. Create Issue: `[NEW] Wazuh setup guide added, ready for review`

---

## Questions?

- **How do I format this?** → See template above
- **Where does this go?** → See file organization table
- **Should I add this?** → Ask in #cyberforce
- **Found a mistake?** → Create an Issue or fix it + commit
- **Need help?** → DM @AJ or post in #cyberforce

---

## Golden Rule

**If the next person can use this without asking a question, you did it right.**

---

**Last updated:** June 2026  
**Maintained by:** AJ & LUG CTF Group Admin Team

================================================================================
