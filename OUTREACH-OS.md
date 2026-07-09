# Outreach OS — Terribly Creative

**The complete operating manual for TC's daily outreach routine.**

---

## Overview

- **Volume:** 10 emails per day, 7 days a week
- **Mode:** Two-phase — Phase 1 researches leads and creates a review draft. Anant adds his take. Phase 2 reads the annotated draft and creates final Gmail drafts.
- **Sender:** winslinger@gmail.com (Gmail MCP)
- **Lead pool:** `Outreach/lead-queue.csv` — 646 leads, status tracked per row
- **Sequence:** 5-touch per lead (initial + 4 follow-ups). Each touch adds new value.
- **Industries:** Fashion & Apparel + Gadgets & Wearables

---

## PHASE 1 — Research Run (Morning)

**This is what the morning agent does:**

### 1. Pick 10 leads

Open `Outreach/lead-queue.csv`. Find leads where:
- `status = pending` → first email (initial touch)
- OR `status = follow_up_due` → follow-up due today (check `date_sent` + cadence below)

Priority order:
1. Overdue follow-ups first
2. New pending leads — pick the next 10 in order (by `id`)

If fewer than 10 follow-ups are due, fill the rest with new pending leads.

### 2. Research each lead

For each lead, fetch their website using the `website` field from the CSV. Extract:

- **Content output** — What are they actually producing? Lifestyle shots, product stills, video? How much?
- **Content gap** — What's missing or thin? Not enough environments, low posting frequency, same scenes recycled?
- **Brand aesthetic** — What visual style are they going for? Premium, playful, minimal, lifestyle-forward?
- **Product scope** — How many SKUs or product lines? Seasonal drops or evergreen?
- **Anything specific** — A recent campaign, a product launch, a content style they're clearly committed to

This is not keyword scanning. Visit the actual URL. Look at the site like a creative director would.

**For follow-up leads (Touch 2-4):** Skip the website fetch. Use what's already in the `notes` column of the CSV and the prior touch angle.

### 3. Write the research block for each lead

For each lead, produce one structured block:

```
---
Lead [N]: [First Name] [Last Name] | [Company] | [Email]
Touch: [1 / 2 / 3 / 4]
Website visited: [URL]

WHAT I FOUND:
[2-4 specific observations from the website. Concrete. Not generic.]

PROPOSED HOOK:
[1-2 sentence opening line built from those observations — about them, not TC]

PROPOSED SUBJECT: [2-4 words, lowercase]

YOUR TAKE:
[ANANT FILLS THIS IN — leave blank]
---
```

### 4. Create the research review draft

Create a single Gmail draft to winslinger@gmail.com:

- **Subject:** `research — [YYYY-MM-DD]`
- **Body:** All 10 lead research blocks in order, separated by `---`
- **Opening line of the draft:** "Add your take under each lead. When done, send this email to yourself to trigger Phase 2."

Do NOT create any email drafts to leads in Phase 1.

### 5. Write the Phase 1 log entry

Append to `Outreach/outreach-log.md`:
```
## [YYYY-MM-DD] — Phase 1 complete (research)
Leads researched: [list of names + companies]
Notes: [anything flagged — URL returned 404, follow-up lead skipped fetch, etc.]
```

Commit and push with message: `outreach research [YYYY-MM-DD]`

---

## ANANT'S STEP (Between Phase 1 and Phase 2)

Open the Gmail draft with subject `research — [date]`.

Under each lead's `YOUR TAKE:` block, write one line — your angle, your instinct, anything specific you'd add or change. It can be:
- A sharper hook: "lead with the VanMoof urban campaign rebrand"
- A redirect: "skip the content gap angle — focus on launch content"
- An addition: "they just raised a round — mention that"
- A sign-off: "looks good, go with it"

When done, **send the email to yourself** (winslinger@gmail.com). This is what triggers Phase 2 to run.

---

## PHASE 2 — Email Drafting Run (Afternoon)

**This is what the afternoon agent does:**

### 1. Find today's research email

Search Gmail inbox for: `subject:"research — [today's date]"`

- If found: read it, extract all 10 lead blocks including Anant's take
- If not found: log "Phase 2 skipped — research email not found in inbox. Anant has not reviewed yet." Stop. Do not create any drafts.

### 2. For each lead — write the email

Use the research block + Anant's take to write the email.

**Email structure:**
```
Subject: [from research block, or sharper version based on Anant's take]

[Opening — the specific observation from research + Anant's angle]

[1-2 sentences — the cost of that gap: budget wasted, content thin, ROAS suffering]

[TC as the fix — outcome first: more content, lower CAC, higher ROAS. AI is secondary.]

[Proof: "8 campaign videos for a premium German furniture brand — delivered in 10 days, Aman-level quality"]

[One low-friction CTA]

Anant
```

**Hard rules — non-negotiable:**
- Subject: 2-4 words, lowercase, no prospect name, no salesy words
- Body: max 100 words. Often less.
- Opening line is specific to THAT brand from the research. Not generic industry pain.
- Lead with outcome (more sales, lower CAC, more content), not method (AI-powered)
- No "I hope this email finds you well"
- No "My name is Anant and I..."
- No em dashes (—) anywhere in the email. Use a comma or period.
- No feature lists
- One CTA only — reply-level, not call-level
- Sign: just "Anant" (or "Anant / TC")
- Read it aloud — if it sounds like marketing copy, rewrite it

**Subject line approach:**
- Reference the brand or their specific situation: `[brand] content`, `your product shoots`, `saw [brand]`
- Curiosity over category: `quick question` or `saw your page` beats `ad creative`
- Or specific to the gap found: `your shoot budget`, `content at scale`, `your spring campaign`
- Never: the prospect's first name, salesy words, urgency, numbers, percentages

**Outcome framing (use this instead of method framing):**

| Instead of... | Say... |
|---|---|
| "We make AI-powered content" | "You're losing ROAS every week you don't have more creative to test" |
| "AI at every stage of production" | "20 environments, one brief — delivered in a week" |
| "Same quality as a studio shoot" | "8 campaign videos for a premium furniture brand in 10 days" |
| "AI photo and video production" | "More content than a shoot budget can afford" |

**ZinCuTec proof point — use this specific version:**
"We just delivered 8 campaign videos for a premium German furniture brand — Mediterranean interiors, warm light, cinematic — in 10 days. Done entirely with AI."

Or shorter: "Just wrapped 8 campaign videos for a premium furniture brand in 10 days. Aman-level quality, entirely with AI."

### 3. Draft to Gmail

Create a Gmail draft for each of the 10 emails:
- `to`: lead's email address
- `subject`: subject line from research block
- `body`: email body

Note each draft ID.

### 4. Create the summary draft

Create a Gmail draft to winslinger@gmail.com:
- **Subject:** `outreach ready — [YYYY-MM-DD]`
- **Body:** List all 10 leads with name, company, subject line, and draft ID. Flag any anomalies.

### 5. Scan inbox for replies

Search inbox for any replies from lead email addresses (last 30 days). List any found in the summary draft with sender, subject, date, and snippet.

### 6. Write the Phase 2 log entry

Append to `Outreach/outreach-log.md`:
```
## [YYYY-MM-DD] — Phase 2 complete (10 drafts created)
Leads drafted: [list with touch number and framework used]
Inbox replies found: [any or none]
Notes: [anything unusual]
Draft IDs: [all 10]
Summary draft ID: [ID]
```

Commit and push with message: `outreach log [YYYY-MM-DD]`

---

## Follow-Up Cadence

| Touch | Status after send | Next touch due |
|---|---|---|
| Initial email sent | `sent_1` | Day 3 |
| Follow-up 1 sent | `sent_2` | Day 7-8 |
| Follow-up 2 sent | `sent_3` | Day 14 |
| Follow-up 3 sent | `sent_4` | Day 21-28 |
| Follow-up 4 (breakup) sent | `sent_5` | done |
| Replied | `replied` | Anant handles manually |
| Bounced | `bounced` | Skip |

When a lead's next touch is due, set `status = follow_up_due` so the morning agent picks them up.

**Follow-up angle rotation (no website fetch needed — use prior touch context):**
- Touch 2 (BAB): Different angle — content volume / competitive pressure
- Touch 3 (Star-Story-Solution): Case study — "a brand like yours" + ZinCuTec specifics
- Touch 4 (Breakup): 1-2-3 format (1=yes, 2=later, 3=stop)

---

## Quality Bar — Non-Negotiable

Before creating any draft:
- Is the opening line specific to THIS brand — something you only know from looking at them?
- Does it lead with their outcome, not our process?
- Would Anant be proud to have his name on this?
- Would YOU reply to this cold?
- Is every sentence earning its place?

If any answer is no — rewrite.

---

## Do NOT Update the CSV

Do NOT update lead statuses in `lead-queue.csv`. Anant does that manually after sending.

---

## When Anant Replies to a Lead

Update the lead's status to `replied` in lead-queue.csv.
Log the reply in outreach-log.md.
Do NOT send any more automated touches to that lead.
Anant handles the conversation from here.

---

## Files in This System

| File | Purpose |
|---|---|
| `OUTREACH-OS.md` | This file — the master protocol |
| `TC-PITCH.md` | TC value prop, pain points by industry, voice rules |
| `lead-queue.csv` | 646 leads with status tracking |
| `outreach-log.md` | Append-only daily log |
| `Email Frameworks/cold-email/` | Cold email skill + references |
| `Email Frameworks/copywriting/` | Copywriting frameworks |
