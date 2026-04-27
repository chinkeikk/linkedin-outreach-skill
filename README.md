# LinkedIn Outreach Skill

A Claude skill for job seekers who want to approach people on LinkedIn — without spending 30 minutes staring at a blank message box.

## What This Does

**Two things, in order:**

**Phase 1 — Match Analysis**
Paste a job description. Claude compares it against your background and tells you:
- Where you're a strong fit (with specifics, not vague claims)
- Where the gaps are (honestly)
- Whether it's worth reaching out at all

**Phase 2 — Write the Message**
Found someone to contact? Tell Claude their name, role, and your relationship. Claude writes:
- A **LinkedIn Connect invitation** (≤300 characters, LinkedIn's hard limit)
- An **InMail message** tailored to who you're talking to — including 3 subject line options to pick from

Both messages adapt based on context — an alumni you've never met gets a different tone than a recruiter at your target company.

## How Messages Are Tailored

| Who you're contacting | Ask for | Resume handling |
|---|---|---|
| HR / Recruiter | Move forward in process | Attached with InMail |
| Hiring Manager | Interview / next steps | Attached with InMail |
| Employee / Alumni | Referral or introduction | "Happy to share if helpful" |

Every InMail comes in **three versions** so you can pick what fits the situation:

- **Option A — Standard (default)** — Full message, low-pressure ending. Gives them an easy out. Works for most cold outreach. ~100-150 words.
- **Option B — Quick Chat** — Same as A but ends with a chat request. Use when their profile feels open to conversation, or when you have a stronger common thread.
- **Option C — Minimalist** — About half the length of A (~50-75 words). Three sentences: I applied, here's my one strongest match point, here's what I'm asking for. Use when you want to respect their time, or when you suspect they're slammed.

## Installation

1. Download `SKILL.md` from this repo
2. Go to Claude.ai → Settings → Capabilities → Skills
3. Create a new skill and paste in the content (or upload the file, depending on your interface)

That's it. The skill activates whenever you mention LinkedIn outreach, job analysis, or paste a JD.

## How to Use

**First time:**
```
Paste your resume + a job description you're excited about
```
Claude will store your resume for future sessions.

**Every time after:**
```
[Paste JD]

Found someone: Sarah Chen, Recruiter at Airbnb, no prior connection
Job link: https://careers.airbnb.com/positions/12345
```

Claude runs the match analysis first, then asks if you want to proceed to writing the message.

**To update your resume:**
```
Update my resume: [new content]
```

## Example Output

**Connect Invitation (142/300 chars)**
```
Hi Sarah, I recently applied for the Senior PM, Growth role at Airbnb 
and wanted to connect directly. Would love to stay on your radar!
```

**InMail Subject — pick one:**
1. Senior PM, Growth — Airbnb Application
2. Excited about the Growth PM role at Airbnb
3. Following up on my application

**InMail — Option A (Standard)**
```
Hi Sarah,

I recently applied for the Senior PM, Growth position at Airbnb 
(https://careers.airbnb.com/positions/12345) and wanted to reach out directly.

My background in growth product and A/B testing maps closely to what the 
team is looking for, and I'm genuinely excited about Airbnb's direction.

I've attached my resume alongside this message.

No pressure at all — if you're able to pass this along or flag my 
application, I'd really appreciate it!

Best,
[Your name]
```

**InMail — Option C (Minimalist)**
```
Hi Sarah,

I recently applied for the Senior PM, Growth role at Airbnb and would 
love to be considered. With 5+ years in growth product and a track 
record of running 100+ A/B tests — more details in my attached CV. 
If you could help flag my application, or point me to other roles 
that might be a better fit, I'd really appreciate it!

Best,
[Your name]
```

## Philosophy

Cold outreach on LinkedIn is awkward for everyone. This skill doesn't try to make it feel effortless — it just makes sure that when you do reach out, the message is specific, honest about fit, and respectful of the other person's time.

The Minimalist option exists for the same reason: sometimes the kindest thing you can do is keep it short.

Generic messages get ignored. These won't be.

## Using with other AI tools

The logic in SKILL.md works as a system prompt for any LLM — paste it into ChatGPT Custom Instructions, a GPT system prompt, or Cursor rules.

## License

MIT — use it, modify it, share it.
