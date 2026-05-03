# Outreach OS — Terribly Creative

**The complete operating manual for TC's daily outreach routine.**

---

## Overview

- **Volume:** 10 emails per day, 7 days a week
- **Mode:** Draft-first — all 10 go to Gmail Drafts. Anant reviews, then sends.
- **Sender:** winslinger@gmail.com (Gmail MCP)
- **Lead pool:** `Outreach/lead-queue.csv` — 646 leads, status tracked per row
- **Sequence:** 5-touch per lead (initial + 4 follow-ups). Each touch adds new value.
- **Industries:** Fashion & Apparel + Gadgets & Wearables

---

## Daily Routine — Step by Step

**This is what the scheduled morning agent does every day:**

### 1. Pick 10 leads

Open `Outreach/lead-queue.csv`. Find leads where:
- `status = pending` → this is their first email (initial touch)
- OR `status = follow_up_due` → a follow-up is due today (check `date_sent` + cadence below)

Priority order:
1. Overdue follow-ups first (don't let active threads go cold)
2. New pending leads — pick the next 10 in order (by `id`)

If fewer than 10 follow-ups are due, fill the rest with new pending leads.

### 2. For each lead — research and write

Read these files before writing:
- `Outreach/TC-PITCH.md` — value prop, pain points by industry, voice rules
- `Outreach/Email Frameworks/cold-email/SKILL.md` — email writing principles
- `Outreach/Email Frameworks/cold-email/references/frameworks.md` — framework selection
- `Outreach/Email Frameworks/cold-email/references/subject-lines.md` — subject line rules
- `Outreach/Email Frameworks/cold-email/references/personalization.md` — personalization system

**For each lead, use this data from the CSV:**
- Name, title, company, industry, website, revenue, employees, keywords, city/country

**Personalization approach (always Level 3 minimum, Level 4 when possible):**

Pull from available signals:
- `keywords_short` — what they sell, what their brand is about → hook into TC's relevant angle
- `revenue` + `employees` — company scale → speaks to budget stage and content volume needs
- `industry` → use the correct TC pitch angle from TC-PITCH.md
- `city/country` → localize tone if relevant (UK brand, German brand, etc.)
- `website` — if possible, visit their site mentally using the URL for brand aesthetic signals

**Opening line rule:** The first sentence must be about THEM. Not TC. Not a compliment for its own sake — an observation that connects to the problem.

### 3. Pick the right framework

| Situation | Framework |
|---|---|
| Default (most cases) | QVC — Question, Value, CTA. Tight, peer-tone. |
| Strong pain signal from keywords | PAS — Problem, Agitate, Solution |
| Company has a visible milestone (funding, launch) | PPP — Praise, Picture, Push |
| Very senior / C-suite | Mouse Trap — 2 sentences, binary CTA |
| Follow-up touch 2 | BAB — Before, After, Bridge (new angle) |
| Follow-up touch 3 | Star-Story-Solution (case study) |
| Follow-up touch 4 | Breakup email (1-2-3 format) |

### 4. Write the email

**Structure:**
```
Subject: [2-4 words, lowercase, internal-looking]

[Opening line — observation about them connected to the problem]

[1-2 sentences — the pain / the situation they're likely in]

[1 sentence — TC's solution + one proof point]

[One low-friction CTA]

Anant
```

**Hard rules:**
- Subject: 2-4 words, lowercase, no prospect name, no salesy words
- Body: max 100 words. Often less.
- No "I hope this email finds you well"
- No "My name is Anant and I..."
- No feature lists
- One CTA only
- Sign: just "Anant" (or "Anant / TC")
- Read it aloud — if it sounds like marketing copy, rewrite it

### 5. Draft to Gmail

Use Gmail MCP (`mcp__claude_ai_Gmail__create_draft`) to create a draft for each email.

Draft fields:
- `to`: lead's email address
- `subject`: the subject line
- `body`: the email body

After creating each draft, note the draft ID in the sent log.

### 6. Update lead-queue.csv

After drafting all 10:
- Set `status = drafted`
- Set `date_drafted = today's date (YYYY-MM-DD)`

### 7. Write the daily log entry

Append to `Outreach/outreach-log.md`:
```
## [YYYY-MM-DD] — 10 drafts created
Leads drafted: [list of names + companies]
Follow-ups drafted: [if any]
Notes: [anything unusual — bounced email in queue, lead already replied, etc.]
```

---

## Follow-Up Cadence

When a lead is contacted, track their sequence position:

| Touch | Status after send | Next touch due |
|---|---|---|
| Initial email sent | `sent_1` | Day 3 |
| Follow-up 1 sent | `sent_2` | Day 7-8 |
| Follow-up 2 sent | `sent_3` | Day 14 |
| Follow-up 3 sent | `sent_4` | Day 21-28 |
| Follow-up 4 (breakup) sent | `sent_5` | — done |
| Replied | `replied` | Anant handles manually |
| Bounced | `bounced` | Skip |

When a lead's next touch is due, set `status = follow_up_due` so the morning agent picks them up.

**Follow-up angle rotation:**
- Touch 1: Personalized hook + TC value + soft CTA
- Touch 2: Different angle — content volume / competitive pressure angle
- Touch 3: Case study angle — "a brand like yours" proof
- Touch 4: Breakup — 1-2-3 format (1=yes, 2=later, 3=stop)

---

## Quality Bar — Non-Negotiable

Before drafting any email:
- Would Anant be proud to have his name on this?
- Does it sound like a peer, not a vendor?
- Would YOU reply to this?
- Is every sentence earning its place?

If the answer to any of these is no — rewrite.

---

## Files in This System

| File | Purpose |
|---|---|
| `OUTREACH-OS.md` | This file — the master protocol |
| `TC-PITCH.md` | TC value prop, pain points by industry, voice rules |
| `lead-queue.csv` | 646 leads with status tracking |
| `outreach-log.md` | Daily log of what was drafted |
| `Email Frameworks/cold-email/` | Cold email skill + references |
| `Email Frameworks/copywriting/` | Copywriting frameworks |

---

## When Anant Replies to a Lead

Update the lead's status to `replied` in lead-queue.csv.
Log the reply in outreach-log.md.
Do NOT send any more automated touches to that lead.
Anant handles the conversation from here.