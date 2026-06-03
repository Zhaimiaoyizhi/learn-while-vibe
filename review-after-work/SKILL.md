---
name: review-after-work
description: >
  Generate a neutral, evidence-based work review report (.md) from the current conversation.
  Use when the user says "review-after-work", "工作复盘", "复盘报告", "review this session",
  "写一份复盘", or any request for a post-work retrospective review of the conversation.
---

# review-after-work

When triggered, produce a `.md` work review report based on the full visible content of the current conversation.

The report must be neutral, calm, and specific. Do not write vague summaries or exaggerate achievements. Every conclusion must be traceable to evidence in this conversation. Mark anything unverifiable as `（存疑？）`, `（未确认）`, or `（本轮对话未体现）`.

## Output File

```
任务关键词_review_YYYY-MM-DD.md
```

Clear hierarchy, suitable for direct `.md` save.

---

## Report Structure

### 1. 核心目的

Explain the background, the user's real goal, and what was actually produced.

Must answer:
- Why did the user start this conversation?
- What was the core problem?
- What was actually delivered?
- Did the output meet the original goal?
- If the goal shifted, describe the shift.

Requirements:
- Distill real intent, don't parrot user words.
- Don't write "completed" for things only attempted.
- If user acceptance is unclear, mark `（存疑？）`.

---

### 2. 技术路线

Write a flowing narrative (not bullet points, not tables) that explains the project's technical roadmap and the reasoning behind each methodological choice.

Requirements:
- 用一段流畅、逻辑承接紧密的话，清晰明白地将用户指定的本对话中的项目的路线规划与每一步的方法选择讲清楚，力求鞭辟入里。
- Each step must state: purpose, input, tool/method used, why this tool (not another), and output.
- The narrative must reveal the logical chain: why step N's result creates the need for step N+1.
- No isolated step descriptions — every method choice must be justified by what the previous step exposed or failed to address.
- Cover the full pipeline from raw input to final output, including any preprocessing, normalization, modeling, and validation steps.
- Use concrete numbers and results from the actual conversation (e.g., "63677 genes filtered to 17199") rather than abstract descriptions.
- Mark anything not executed in this conversation as `（未执行）`.

---

### 3. 工作流

Summarize the actual workflow with arrow-connected chains:

```
用户输入 A → 调用 X 工具 → 生成 Z 成果 → 用户反馈状态
```

Must include:
- What the user provided (files, requirements, constraints).
- What tools/skills/scripts were actually used.
- What was actually produced (files, conclusions, code, tables).
- Whether the user explicitly accepted the output.
- If no clear feedback, mark `（存疑？）`.

Requirements:
- Only write what actually happened.
- Don't write "might" / "should" / "planned" flows unless clearly marked as incomplete.
- Short words, high information density.
- Avoid chronological play-by-play; highlight key nodes.

---

### 4. 核心难题

Summarize difficulties that actually blocked progress.

Format:

| 核心难题 | 具体表现 | 解决方案 | 解决程度 | 值得学习的内容 |
| ---- | ---- | ---- | ---- | ------- |

Requirements:
- Difficulties must be specific, not "task was complex" or "lots of information."
- Explain why the difficulty was hard.
- Distinguish: fully resolved / partially resolved / bypassed / unresolved.
- Extract methodology, not just results.
- If the difficulty was caused by unclear user input, shifting goals, poor file quality, or messy naming, say so directly.

---

### 5. 新技能

Summarize new skills, methods, templates, or reusable workflows discovered.

#### 5.1 已形成的新技能

Skills actually established, verified, or crystallized in this conversation.

Each item includes:
- Skill name
- Description
- Applicable scenarios
- How to reuse
- Limitations

#### 5.2 尚未成熟但值得继续发展的技能

Emerging methods not yet stable.

Requirements:
- Don't force one-time operations into "new skills."
- If no real new skills formed, write: `本次没有形成稳定的新技能，但沉淀了以下可复用经验。`
- Distinguish "calling existing skills" from "establishing new skills."

---

### 6. 改进点

Sharp retrospective from angles: task efficiency, prompt quality, user input quality, communication, file organization, goal control, acceptance criteria.

Do not be deferential to the user. Do not write pleasantries. Audit like a project review.

#### 6.1 用户侧问题

Audit:
- Were prompts clear?
- Were goals stable?
- Was input (files, code, screenshots, logs) sufficient?
- Was necessary context provided?
- Were requirements changed frequently?
- Were acceptance criteria missing?
- Were exploratory tasks packaged as deterministic ones?
- Were too many requirements given without prioritization?
- Were output format, depth, boundaries underspecified?

Be direct. Cite specific conversation content. Tone can be sharp but must be objective.

#### 6.2 AI 侧问题

Audit:
- Unnecessary repeated confirmations?
- Over-expansion or information redundancy?
- Executing too early without clarifying goals?
- Inefficient use of tools/files/skills?
- Unclear output acceptance?
- Possibly missing what the user actually cared about?

Don't only criticize the user. If AI performed well somewhere, note it briefly without self-praise.

#### 6.3 后续优化建议

Format:

| 问题 | 后果 | 下次应该怎么做 |
| -- | -- | ------- |

Each suggestion must directly guide the next conversation. No vague advice like "improve communication efficiency." Write executable actions, e.g.: "Before uploading files, state the file purpose, target section, desired output format, and whether external knowledge is allowed."

---

### 7. 总体评价

One paragraph covering:
- Task completion degree
- Biggest gain
- Biggest waste
- Most reusable experience going forward
- If redoing, what to change first

Tone: neutral, calm, specific, no flattery, no avoidance.

---

## Output Style

- Chinese.
- Markdown headings, tables, lists.
- Precise language, no filler.
- Sharp but not emotional.
- Do not output private reasoning traces.
- Do not fabricate tool calls, file processing, or user feedback that didn't happen.
- Explicitly mark uncertain information.
- Focus on "how to do the next task better," not chronological recording.
