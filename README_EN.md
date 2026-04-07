<div align="center">

# department.skill

> *New joiners want to understand the team faster. Experienced people want to lose less to org dynamics.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

<br>

Just joined the team and want to know which lunch spots people actually recommend nearby?<br>
Want to know which manager is easier to work with and which teammate is safer to approach first?<br>
Want to understand how this department normally talks, runs meetings, and asks for help?<br>
Want to know what you can ask directly and what you should quietly observe for two days first?<br>
Want to understand the team rhythm and make fewer avoidable mistakes?<br>
<br>
Been here longer and want to understand the subtext behind your manager's vague phrasing?<br>
Want to see who is throwing work over the fence, who is cutting blame away from themselves, and who is blurring ownership?<br>
Want to know whether "take another look" means revise it, rethink it, or slow down the pace?<br>
Want to know who in a group chat is actually pushing things forward, who is only signaling, and who is quietly steering the room?<br>

<br>

**Turn department chats, manager messages, screenshots, docs, and code review comments into information you can actually use.**

[Supported Sources](#supported-data-sources) · [Install](#install) · [Optional Tools](#optional-tools) · [Usage](#usage) · [Examples](#examples) · [Key Scenarios](#key-scenarios) · [Project Structure](#project-structure) · [Notes](#notes) · [Detailed Install](INSTALL.md) · [**中文**](README.md) · [**Español**](README_ES.md) · [**Deutsch**](README_DE.md) · [**日本語**](README_JA.md) · [**Русский**](README_RU.md) · [**Português**](README_PT.md)

</div>

---

## What It Is

`department.skill` is not about "distilling" a single person. It helps you understand how an entire department actually works.

It focuses on things like:

- who is driving, who is deciding, who is buffering, and who is blurring ownership
- what a manager really cares about behind one vague sentence
- who a new joiner should approach first, how to ask, and which unwritten rules need to be observed before speaking up
- how more experienced people can spot blame-shifting, quiet backstabbing, agenda steering, and low-level office politics

The output is not a vague wall of text. It aims to give you:

- structured judgment
- key conclusions
- interaction advice
- risks and confidence levels

---

## Supported Data Sources

Mixed input is supported. More material usually means more reliable analysis.

| Source | Chat Logs | Docs / PDF | Images / Screenshots | Code / Comments | Notes |
|------|:---------:|:----------:|:--------------------:|:---------------:|------|
| WeChat / Feishu / DingTalk conversations | ✅ | — | ✅ | — | Paste text directly or upload screenshots |
| Department groups / project groups / weekly sync groups | ✅ | — | ✅ | — | Good for people mapping and team atmosphere |
| Word / plain text docs | — | ✅ | — | — | Good for notes, retros, and explanations |
| PDF | — | ✅ | — | — | Good for weekly reports, plans, and meeting notes |
| Markdown | ✅ | ✅ | — | ✅ | Good for wikis, issues, and PR descriptions |
| Code / PR / review comments | ✅ | — | — | ✅ | Good for collaboration style, responsibility chains, and hidden signals |
| User-provided background | ✅ | — | — | — | Useful for relationship context, red flags, and additional history |

---

## Install

See `INSTALL.md`.

If you only need the core Skill behavior, the current repository contents are already enough.
If you also want Feishu, DingTalk, Slack, email, and export parsing support, you can install the optional dependencies:

```bash
pip3 install -r requirements.txt
playwright install chromium
```

---

## Optional Tools

This repository also includes a `tools/` directory for turning raw materials into cleaner inputs for the Skill.

- Feishu auto collection: `tools/feishu_auto_collector.py`
- Feishu export parsing: `tools/feishu_parser.py`
- Feishu browser capture: `tools/feishu_browser.py`
- Feishu MCP access: `tools/feishu_mcp_client.py`
- DingTalk auto collection: `tools/dingtalk_auto_collector.py`
- Slack auto collection: `tools/slack_auto_collector.py`
- Email parsing: `tools/email_parser.py`
- Generic chat export parsing: `tools/generic_chat_parser.py`
- WeChat export parsing: `tools/wechat_parser.py`
- QQ export parsing: `tools/qq_parser.py`

For more detail, see `tools/README.md`. For third-party sources and license notices, see `docs/THIRD_PARTY.md`.

---

## Usage

Call it inside any Skill-compatible runtime:

```text
/department
```

Preferred input styles:

- one isolated line: enough for a rough first-pass read
- multi-turn chats, screenshots, docs, and user background: much better for stable analysis

---

## Examples

**Scenario 1: New Joiner Onboarding**

```text
User              ❯ I just joined this department. I want to know who is easier to work with and what I can ask directly.

department.skill  ❯ Quick conclusion first:
                  1. A looks more like someone willing to help new joiners. Their replies are short, but they usually give concrete next steps.
                  2. B is more senior but comes with a higher communication cost. Not the best person to aggressively follow up with right away.
                  3. The default style in this department is "observe first, speak second", especially in group chats where the manager is present.
```

**Scenario 2: Reading Your Manager**

```text
User              ❯ My manager said "take another look". What does that actually mean?

department.skill  ❯ In this context, it sounds less like "make a few edits" and more like:
                  1. the current proposal still did not persuade them
                  2. the risks and benefits have not been made clear enough
                  3. they want a stronger conclusion, not more process detail
```

**Scenario 3: Reading Team Direction**

```text
User              ❯ Help me see who is actually pushing things forward in this group and who is dumping blame.

department.skill  ❯ A looks like the real driver. They close loops, assign owners, and add deadlines.
                  C shows a clear pattern of blurring ownership by phrasing responsibility as "let's all take a look".
                  D currently looks more like risk separation than confirmed backstabbing, but there are early signs of blame-shifting.
```

---

## Key Scenarios

### New Joiner Support

- which nearby lunch places are repeatedly mentioned and what the team's meal rhythm looks like
- which manager is harder to communicate with and which teammate is safer to ask for help
- which unwritten rules exist in the team and which questions should be observed before being asked
- which forms of "reasonable slacking" are really just rhythm observation, and which behaviors are genuinely risky
- treat sensitive details carefully; for example, only mention relationship status if it is explicitly present in the material

### Experienced Employee Use

- whether a manager's sentence is a reminder, a rejection, a pace-control move, or a responsibility push
- which teammate is shifting blame, which one may be working against you, and who is blurring ownership
- what to add next and how to push the situation more safely

---

## Project Structure

```text
department/
├── SKILL.md
├── README.md
├── README_EN.md
├── README_ES.md
├── README_DE.md
├── README_JA.md
├── README_RU.md
├── README_PT.md
├── INSTALL.md
├── LICENSE
├── .gitignore
├── requirements.txt
├── docs/
│   ├── PRD.md
│   ├── FAQ.md
│   └── THIRD_PARTY.md
├── prompts/
│   ├── intake.md
│   ├── structure_analyzer.md
│   ├── subtext_analyzer.md
│   └── response_strategy.md
├── tools/
│   ├── README.md
│   ├── feishu_auto_collector.py
│   ├── feishu_parser.py
│   ├── feishu_browser.py
│   ├── feishu_mcp_client.py
│   ├── dingtalk_auto_collector.py
│   ├── slack_auto_collector.py
│   ├── email_parser.py
│   ├── generic_chat_parser.py
│   ├── wechat_parser.py
│   └── qq_parser.py
└── examples/
    ├── group-chat-example.md
    ├── boss-message-example.md
    └── onboarding-example.md
```

---

## Notes

- It works with a single line, but more context makes it much more reliable.
- For judgments like "who is backstabbing" or "who is shifting blame", it tries to stay attached to observable evidence instead of making empty accusations.
- For sensitive details such as "who is single", it does not infer private information and only cites what is explicitly present in the source material.
