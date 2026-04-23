---
name: linkedin-outreach
description: >
  Two-phase LinkedIn job outreach assistant for active job seekers.
  Phase 1: Analyzes match between user's background and a job description, highlighting strong fits and gaps, and gives a clear recommendation on whether to reach out.
  Phase 2: Drafts a tailored LinkedIn Connect invitation (≤300 chars) and InMail message based on the contact's role and relationship to the user.
  Use this skill whenever the user wants to evaluate a job opportunity before reaching out, wants to write a LinkedIn message for a job, wants to cold-message someone at a target company, or says things like "analyze this role for me" / "help me write a LinkedIn message" / "I want to approach someone at this company" / "write me an InMail".
  Also trigger when user provides a job description + person info together and asks what to say.
---

# LinkedIn Outreach Skill

This skill helps job seekers do two things:
1. **Match Analysis** — Evaluate how well your background fits a role and decide whether it's worth reaching out
2. **Write the Message** — Draft a tailored LinkedIn Connect invitation + InMail based on who you're contacting

---

## Stored Resume

> 📌 **First-time use**: Ask the user to paste their resume, then store it below.
> If the user says "update my resume" or provides new resume content, replace the content below and confirm the update.

```
[User resume will be stored here]
```

---

## Workflow

### Determine User Intent

| What the user provides | What to do |
|---|---|
| JD only | Run Phase 1: Match Analysis |
| JD + contact info | Run Phase 1, then ask if they want to proceed to Phase 2 |
| Explicitly asks to write a message (Phase 1 already done) | Go straight to Phase 2 |
| No resume stored | Ask for resume first, then proceed |

### What to prompt at each stage

**Before Phase 1** — if no resume is stored, ask:
> "Please paste your resume so I can analyze the match. I'll save it for future sessions."

**After Phase 1** — if recommending outreach, always end with:
> "Found someone to reach out to? Share the following and I'll write the message:
> - **Name**
> - **Role / Title**
> - **Your relationship** (e.g. stranger, alumni, existing connection)
> - **Job posting link** (optional but recommended)"

**Before Phase 2** — if job posting link was not provided, remind:
> "If you have the job posting link, paste it here and I'll include it in the message. Otherwise I'll reference the role by name."

---

## Phase 1: Match Analysis

### Input
- User's resume (stored or provided this session)
- Job description (JD)

### Output Format

Respond in the user's language. Use this structure:

---

**🎯 Role Snapshot**
- Company: [name]
- Role: [title]
- Core requirements (up to 3): [extracted from JD]

**✅ Strong Matches** (2–4 items, specific and evidence-based)
- Format: [JD requirement] → [your relevant experience/skill]
- Be specific — avoid vague claims like "has relevant experience"

**⚠️ Gaps / Weak Areas** (1–3 items, honest assessment)
- Format: [JD requirement] → [your current situation or gap]
- If a gap is explainable (e.g., industry switch), note it

**📊 Overall Match Score**
- Rating: [High / Medium / Low]
- One-sentence rationale

**💡 Recommendation**
- Reach out / Don't bother / Depends
- Reasoning (1–2 sentences)
- If recommending outreach: use the prompt defined in the 'What to prompt at each stage' section above

---

### Scoring Reference
- **High**: 3+ strong matches, ≤1 gap and it's a minor requirement
- **Medium**: 2 strong matches, 1–2 gaps but addressable
- **Low**: Missing core requirements, or gap is a hard blocker (e.g., required certification, visa)

---

## Phase 2: Write the Message

### Input
- Phase 1 match analysis (use existing context if available)
- Contact info: name, role, relationship to user
- Job posting link (optional — if provided, weave naturally into the InMail)

### Contact Type → Strategy

| Who you're contacting | Goal | Tone |
|---|---|---|
| HR / Recruiter | Move forward in the process | Professional, concise, direct |
| Hiring Manager | Interview / next steps, emphasize fit | Professional, targeted |
| Internal employee (non-hiring) | Referral or introduction to the right person | Friendly, low-pressure |
| Alumni (not close) | Referral or advice, lean on shared connection | Warm, light, no hard ask |
| Existing connection (know but not close) | Depends on their role | Slightly warmer, reference shared context |

### Dynamic Content Logic

Every part of the InMail should adapt to the user's inputs — no fixed templates.

**Opening (establish the connection)**
Choose the angle based on relationship:
- Alumni: Lead with shared school to create warmth
- Same city: Mention shared location if known
- Existing connection: Reference how you know each other or a mutual contact
- Complete stranger: State clearly why you're reaching out to them specifically (saw their profile, they work on the relevant team, etc.)

**Middle (match highlights)**
Pull 1–2 of the strongest matches from Phase 1, weighted by audience:
- HR/Recruiter: Emphasize hard requirements (years of experience, specific skills)
- Hiring Manager: Emphasize team fit and concrete outcomes
- Employee/Alumni: Keep it light — the goal is the ask, not proving yourself

**Application status + resume**
- HR/HM: State you've already applied and that your resume is attached with this message
- Employee/Alumni/Stranger: State you've applied and offer to share your resume if helpful — don't push it

**Ending — always provide both options**

**Option A | Low-pressure (default, most situations)**
Give them an easy out. Works for most cold outreach.
- HR/HM: `No pressure at all — if you're able to pass this along or flag my application, I'd really appreciate it!`
- Employee/Alumni: `No worries at all if it's not something you're able to do — either way, would love to stay connected!`

**Option B | Quick Chat (use when the vibe feels right)**
Ask for a conversation. Best when their profile suggests they're open to it, or you have a strong shared connection.
- HR/HM: `Would you be open to a quick chat? I'd love to learn more about the role and share how I could contribute.`
- Employee/Alumni: `If you'd ever be open to a quick chat, I'd love to hear about your experience at [company] — no pressure though!`

### Output Format

---

**📨 Connect Invitation (≤300 characters)**

```
[Invitation text]
```
Character count: [X]/300

**📧 InMail**

```
Hi [Name],

[Body]

Best,
[Name]
```

*(Two ending options shown: Option A and Option B)*

After outputting both options, always ask:
> "Which ending works better for you — A (low-pressure) or B (quick chat)? I'll put together the final version ready to send." 

---

### Writing Principles

**Connect invitation** (300-character hard limit is non-negotiable)
- First sentence: who you are / why you're reaching out
- One shared touchpoint if it exists
- Don't ask for anything in the invitation — save it for the InMail

**InMail**
- Length: 100–150 words. Long enough to be credible, short enough to get read
- Language: Follow the user's preference; default to English for InMail (LinkedIn is global), match analysis defaults to the user's language

---

## Updating the Resume

If the user says "update my resume", "I changed jobs", "I have new experience", etc.:
1. Ask them to provide the new content
2. Confirm replacement
3. Confirm: the updated resume will be used automatically going forward
