---
name: linkedin-outreach
description: "Two-phase LinkedIn job outreach assistant for active job seekers. Phase 1: Analyzes match between user's background and a job description, highlighting strong fits and gaps, and gives a clear recommendation on whether to reach out. Phase 2: Drafts a tailored LinkedIn Connect invitation (≤300 chars) and InMail message based on the contact's role and relationship to the user. Use this skill whenever the user wants to evaluate a job opportunity before reaching out, wants to write a LinkedIn message for a job, wants to cold-message someone at a target company, or says things like \"帮我分析这个岗位\" / \"帮我写LinkedIn消息\" / \"我想approach这个公司的人\" / \"帮我写inmail\". Also trigger when user provides a job description + person info together and asks what to say."
---

# LinkedIn Outreach Skill

这个Skill帮助求职者完成两件事：
1. **匹配分析**：判断你的背景与目标岗位的契合程度，决定是否值得出击
2. **写信**：根据对方身份，定制LinkedIn Connect邀请 + InMail正文

---

## 用户简历（预存区）

> 📌 **如果用户是第一次使用**：请求用户粘贴简历内容，然后将其存储在下方。
> 如果用户说"更新我的简历"或提供新的简历内容，替换下方内容并确认更新成功。

```
[用户简历内容将存储于此]
```

---

## 使用流程

### 判断用户意图

用户输入可能有以下几种情况：

| 用户提供了什么 | 应该做什么 |
|---|---|
| 只有JD（职位描述） | 执行Phase 1：匹配分析 |
| JD + 对方信息 | 执行Phase 1后，询问是否继续Phase 2 |
| 明确说"帮我写信"且已有Phase 1结果 | 直接执行Phase 2 |
| 没有简历预存 | 先请用户提供简历，再执行 |

---

## Phase 1：匹配分析

### 输入
- 用户的简历（预存或本次提供）
- 职位描述（JD）

### 分析框架

按以下结构输出，语言跟随用户（中文或英文）：

---

**🎯 岗位速览**
- 公司：[公司名]
- 职位：[职位名]
- 核心要求（3条以内）：[提炼JD的关键要求]

**✅ 强匹配点**（2-4条，具体、有证据）
- 每条格式：[JD要求] → [你的对应经历/技能]
- 要具体，不要泛泛说"有相关经验"

**⚠️ 差距/弱项**（诚实列出，1-3条）
- 每条格式：[JD要求] → [你的现状或缺失]
- 如果某个gap是可解释的（如行业转换），注明

**📊 综合匹配评分**
- 评分：[高/中/低]
- 一句话理由

**💡 出击建议**
- 建议出击 / 不建议出击 / 视情况而定
- 理由（1-2句）
- 如果建议出击，提示用户：提供对方信息（姓名、职位、与你的关系）即可进入Phase 2

---

### 评分标准参考
- **高**：3条以上强匹配，gap ≤1条且为次要要求
- **中**：2条强匹配，有1-2条gap但可弥补
- **低**：核心要求缺失，或gap为硬性条件（如特定资质/签证）

---

## Phase 2：写信

### 输入
- Phase 1的匹配分析结果（已有上下文则自动使用）
- 对方信息：姓名、职位、与用户的关系
- 岗位链接（可选，用户提供，融入InMail正文）

### 关系类型与策略

| 对方身份 | 诉求 | 语气 |
|---|---|---|
| HR / Recruiter | 希望进入面试流程 | 专业、简洁、直接 |
| Hiring Manager | 希望进入面试流程，强调与职位的匹配 | 专业、有针对性 |
| 公司内部员工（非招聘） | 希望对方转介绍给负责人或refer | 友好、不施压 |
| 校友（不太熟） | 希望对方refer或给建议，拉校友情分 | 亲切、轻量、不强求 |
| 已有connection（认识但不熟） | 根据对方职位判断诉求 | 稍微暖一点，提及共同背景 |

### InMail动态内容逻辑

InMail的每个部分都应根据用户提供的信息动态调整，不能套固定模版。以下是各变量的影响范围：

**开头（建立联系）**
根据与对方的关系选择切入角度：
- 校友：点明共同学校，拉近距离
- 同城：可提及同城背景（如果知道对方所在城市）
- 已有connection：提及认识的背景或共同联系人
- 完全陌生：直接说明为什么找这个人（看到其profile、在这个公司做相关工作等）

**中间段（匹配点）**
从Phase 1的强匹配点中选1-2条最相关的，根据对方身份侧重不同：
- HR/Recruiter：强调符合JD的硬性条件（年限、技能）
- Hiring Manager：强调与团队方向的契合、具体成果
- 普通员工/校友：轻描淡写即可，重点不在于证明自己，而在于请对方帮忙

**已投递说明 + 简历**
- HR/HM：明确说已投递，附简历
- 校友/陌生人/普通员工：说已投递，表示happy to share简历

**结尾（Option A/B/C）**
三个版本都根据对方身份措辞不同（见下方结尾逻辑）

---

**📨 Connect 邀请（≤300字符）**

```
[邀请文本]
```
字符数：[X]/300

**📧 InMail 正文**

Subject候选（选一个使用）：
1. [标题1，≤10词，侧重岗位匹配]
2. [标题2，≤10词,侧重共同点/校友等关系角度]
3. [标题3，≤10词，更直接简短的版本]

```
Hi [Name],

[正文内容]

[署名]
```

---

### 写信原则

**Connect邀请**（最重要的限制：300字符）
- 第一句说明你是谁/为什么联系
- 点一个共同点（如果有）
- 不要在邀请里就开始要东西——留到InMail
- 示例结构：`Hi [Name], I'm [你的名字], currently exploring [角色] roles. I came across your profile while researching [公司]—would love to connect!`

**InMail正文**
- 开头：一句话说明联系原因
- 中间：1-2句点出你与这个岗位最相关的匹配点（从Phase 1借用）
- 简历说明：
  - HR/HM：一定说明随InMail附上简历。示例：`I've attached my resume alongside this message.`；对 Hiring Manager，匹配点选 1-2条最强的，宁可删掉次要数据，不要堆砌。聚焦 > 全面。
  - 校友/陌生人/普通员工：表达愿意分享简历，但不强推。示例：`I'd be happy to share my resume if that'd be helpful.`

- 每次生成InMail时，输出**三个版本**供用户选择，不要只给一个：

  **Option A｜标准版（默认推荐）**
  完整结构：开头 + 匹配点 + 简历说明 + 低压力结尾。100-150词。
  - HR/HM示例结尾：`No pressure at all—if you're able to pass this along or flag my application, I'd really appreciate it!`
  - 校友/普通员工示例结尾：`No worries at all if it's not something you're able to do—either way, would love to stay connected!`

  **Option B｜Quick Chat版**
  在标准版基础上，结尾改为提出chat请求，适合对方profile看起来open to conversation，或你觉得有更强共同点时。
  - HR/HM示例结尾：`Would you be open to a quick chat? I'd love to learn more about the role and share how I could contribute.`
  - 校友/普通员工示例结尾：`If you'd ever be open to a quick chat, I'd love to hear about your experience at [公司]—no pressure though!`

  **Option C｜极简版（约Option A的一半篇幅，50-75词）**
  适合对方时间宝贵、或你想降低对方阅读压力时。三句话搞定：
  1. 表达兴趣 + 已投递（一句话）
  2. 一句话highlight最强匹配点 + 指向CV（不展开）；从Phase 1强匹配点中**自动选最强的1条**
  3. 请求行动（根据对方身份调整）：
     - HR：希望帮忙flag/推进，或如有其他更适合的岗位也欢迎推荐
     - Hiring Manager：希望帮忙flag application
     - 校友/普通员工：希望帮忙refer或转介绍给负责人

  HR示例：
  `Hi [Name], I recently applied for the [职位] role at [公司] and would love to be considered. With [一句话经验/技能highlight]—more details in my attached CV. If you could help flag my application, or point me to other roles that might be a better fit, I'd really appreciate it!`

  校友示例：
  `Hi [Name], saw you're at [公司]—I just applied for the [职位] role and would love your help. I've worked on [一句话经验highlight], more in my CV (happy to share). If you're able to refer me or pass this along to the right person, that'd mean a lot!`

- 如果用户提供了岗位链接，在InMail正文中自然融入（如提及岗位名称后附链接），不要单独列出
- 长度：Option A/B为100-150词；Option C为50-75词（英文）
- 署名跟随用户指定的名字；如果用户没说，默认用简历上的名字（不要自己编）。

**语言**
- 跟随用户要求；如果用户没指定，InMail默认英文（LinkedIn国际场景），匹配分析默认中文

---

## 简历更新说明

如果用户说"更新简历"、"我换工作了"、"我有新的经历"等，帮用户更新预存简历：
1. 请用户提供新内容
2. 确认替换
3. 说明：下次使用时将自动使用更新后的简历
