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
- An **InMail message** tailored to who you're talking to

Both messages adapt based on context — an alumni you've never met gets a different tone than a recruiter at your target company.

## How Messages Are Tailored

| Who you're contacting | Ask for | Resume handling |
|---|---|---|
| HR / Recruiter | Move forward in process | Attached with InMail |
| Hiring Manager | Interview / next steps | Attached with InMail |
| Employee / Alumni | Referral or introduction | "Happy to share if helpful" |

Every InMail comes with **two ending options**:
- **Option A (default)** — Low pressure, gives them an easy out
- **Option B** — Asks for a quick chat, for when the vibe feels right

## Installation

### Claude.ai (Web/Mobile)

1. Download `linkedin-outreach.skill` from [Releases](https://github.com/chinkeikk/linkedin-outreach-skill/releases/tag/v1.0.0)
2. Go to Claude.ai → Settings → Skills → Install Skill
3. Upload the `.skill` file

### Claude Code

```bash
mkdir -p ~/.claude/skills/linkedin-outreach
cp SKILL.md ~/.claude/skills/linkedin-outreach/
```

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



**InMail — Option A (low pressure)**
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

## Philosophy

Cold outreach on LinkedIn is awkward for everyone. This skill doesn't try to make it feel effortless — it just makes sure that when you do reach out, the message is specific, honest about fit, and respectful of the other person's time.

Generic messages get ignored. This one won't be.

## Using with other AI tools? 

The logic in SKILL.md works as a system prompt for any LLM — paste it into ChatGPT Custom Instructions, a GPT system prompt, or Cursor rules.

## License

MIT — use it, modify it, share it.
