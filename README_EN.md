<div align="center">

# department.skill

> *New joiners want to understand the team faster; experienced people want to lose less to org dynamics.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

Want to know who is easy to work with, how the team talks, and what your manager really means?<br>
Want to see who pushes, who stalls, and who blurs ownership?<br>

**Turn chats, screenshots, docs, and review comments into usable department intelligence.**

[Supported Sources](#supported-data-sources)  [Install](#install)  [Optional Tools](#optional-tools)  [Usage](#usage)  [Examples](#examples)  [Detailed Install](INSTALL.md)  [**中文**](README.md)  [**Español**](README_ES.md)  [**Deutsch**](README_DE.md)  [**日本語**](README_JA.md)  [**Русский**](README_RU.md)  [**Português**](README_PT.md)

</div>

---

## What It Is

`department.skill` helps you understand how a team actually works: hidden signals, ownership flow, onboarding rules, and safer response strategy.

## Supported Data Sources

- WeChat / Feishu / DingTalk chats
- Team and project group messages
- Docs, PDF, Markdown, and text notes
- Code reviews, PR comments, and issue threads
- User-provided background context

## Install

See `INSTALL.md`.

Optional tools:

```bash
pip3 install -r requirements.txt
playwright install chromium
```

## Optional Tools

Includes Python tools for Feishu, DingTalk, Slack, email, WeChat, QQ, and generic chat exports. See `tools/README.md` and `docs/THIRD_PARTY.md`.

## Usage

```text
/department
```

## Examples

- Onboarding: who is approachable and what can be asked directly
- Management subtext: what take another look really means
- Team map: who drives, who decides, and who blurs ownership
