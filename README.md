<div align="center">

# 部门.skill

> *新员工想快点看懂部门，老员工想少吃一点组织亏。*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

<br>

新员工入职了，想知道公司附近哪家外卖好吃？<br>
想知道哪个领导脾气好，哪个同事更好相处？<br>
想知道这个部门默认怎么说话、怎么开会、怎么求助？<br>
想知道哪些事可以直接问，哪些事最好先观察两天？<br>
想知道怎么把握团队节奏，少踩坑？<br>
<br>
老员工待久了，想知道怎么听懂领导的潜台词？<br>
想知道哪个同事在背刺，哪个同事在甩锅，谁在模糊 owner？<br>
想知道一句“你再看看”到底是在提醒你、否掉你，还是在压节奏？<br>
想知道一个群里谁在真正推进事情，谁只是表态，谁在暗中带风向？<br>

<br>

**把部门里的群聊、老板消息、截图、文档和代码评论，翻译成真正有用的部门信息。**

[支持的数据来源](#支持的数据来源) · [安装](#安装) · [可选工具](#可选工具) · [使用](#使用) · [效果示例](#效果示例) · [项目结构](#项目结构) · [详细安装说明](INSTALL.md) · [**English**](README_EN.md) · [**Español**](README_ES.md) · [**Deutsch**](README_DE.md) · [**日本語**](README_JA.md) · [**Русский**](README_RU.md) · [**Português**](README_PT.md)

</div>

---

## 这是什么

`部门.skill` 不是帮你蒸馏某一个人，而是帮你理解“一个部门是怎么运转的”。

它更关注这些东西：

- 谁在推进，谁在拍板，谁在缓冲，谁在模糊 owner
- 领导一句模糊表达背后真正关心什么
- 新员工应该先找谁、怎么问、哪些默认规则要先观察
- 老员工怎么识别甩锅、背刺、带风向和低级政治动作

输出不是一大段空话，而是：

- 结构化判断
- 重点结论
- 相处建议
- 风险和置信度

---

## 支持的数据来源

支持混合输入，材料越多越准：

| 来源 | 聊天记录 | 文档 / PDF | 图片 / 截图 | 代码 / 评论 | 备注 |
|------|:-------:|:----------:|:-----------:|:-----------:|------|
| 微信 / 飞书 / 钉钉对话 | ✅ | — | ✅ | — | 可直接粘贴文字或上传截图 |
| 部门群 / 项目群 / 周会群 | ✅ | — | ✅ | — | 适合分析人物结构和部门氛围 |
| Word / 文本文档 | — | ✅ | — | — | 适合纪要、复盘、说明 |
| PDF | — | ✅ | — | — | 适合周报、方案、会议纪要 |
| Markdown | ✅ | ✅ | — | ✅ | 适合 Wiki、Issue、PR 描述 |
| 代码 / PR / Review 评论 | ✅ | — | — | ✅ | 适合辅助判断协作风格、责任链路与隐藏信号 |
| 用户主观描述 | ✅ | — | — | — | 可补充人物关系、雷区、背景 |

---

## 安装

详见 `INSTALL.md`。

如果你只使用最基础的 Skill 能力，当前仓库内容已经够用。
如果你还想补飞书、钉钉、Slack、邮件等材料采集和导出解析，可额外安装：

```bash
pip3 install -r requirements.txt
playwright install chromium
```

---

## 可选工具

仓库已补充 `tools/` 目录，用于把原始材料整理成更适合 Skill 分析的输入。

- 飞书自动采集：`tools/feishu_auto_collector.py`
- 飞书导出解析：`tools/feishu_parser.py`
- 飞书浏览器抓取：`tools/feishu_browser.py`
- 飞书 MCP 读取：`tools/feishu_mcp_client.py`
- 钉钉自动采集：`tools/dingtalk_auto_collector.py`
- Slack 自动采集：`tools/slack_auto_collector.py`
- 邮件解析：`tools/email_parser.py`
- 通用聊天导出解析：`tools/generic_chat_parser.py`
- 微信导出解析：`tools/wechat_parser.py`
- QQ 导出解析：`tools/qq_parser.py`

详细说明见 `tools/README.md`，第三方来源和许可见 `docs/THIRD_PARTY.md`。

---

## 使用

在支持 Skill 的运行时中调用：

```text
/department
```

更适合的输入方式：

- 只丢一句话：可以先做初步判断
- 提供多轮聊天、截图、文档、主观描述：分析会更稳

---

## 效果示例

**场景一：新员工入职**

```text
用户        ❯ 我刚来这个部门，想知道谁比较好相处，哪些事能直接问

部门.skill  ❯ 先说结论：
            1. A 更像愿意带新人的人，回复短但会给具体动作
            2. B 职级高但沟通成本更高，不适合上来就直接追问
            3. 这个部门默认是“先观察、后发言”，尤其在老板在场的群里
```

**场景二：听懂领导**

```text
用户        ❯ 老板说“你再看看”，到底什么意思

部门.skill  ❯ 结合上下文，这句话更像不是让你随便改改，而是在表达：
            1. 现在的方案还没打动他
            2. 风险和收益没有说透
            3. 他希望你补结论，而不是补过程
```

**场景三：看懂部门风向**

```text
用户        ❯ 帮我看看这个群里谁在推进，谁在甩锅

部门.skill  ❯ A 像实际推进者，会收口问题、补 owner 和 deadline。
            C 有明显的模糊 owner 倾向，常把责任描述成“大家一起看下”。
            D 暂时更像风险切割，不一定是恶意背刺，但有甩锅前兆。
```

---

## 重点场景

### 新员工入职

- 公司附近哪家外卖经常被提到、午饭节奏如何
- 哪个领导沟通成本高，哪个同事更适合请教
- 团队里有哪些默认规则、哪些话该先观察再问
- 哪些“合理摸鱼”其实只是观察节奏，哪些行为风险高
- 对敏感信息保持克制，例如感情状态只在材料明确提及时才引用，不做猜测

### 老员工进阶

- 领导这句话到底是在提醒、否定、压节奏还是推责任
- 哪个同事在甩锅、哪个同事可能在背刺、谁在模糊 owner
- 该先补什么，怎么推进更稳

---

## 项目结构

```text
department/
├── SKILL.md
├── README.md
├── INSTALL.md
├── LICENSE
├── .gitignore
├── docs/
│   ├── PRD.md
│   └── FAQ.md
├── prompts/
│   ├── intake.md
│   ├── structure_analyzer.md
│   ├── subtext_analyzer.md
│   └── response_strategy.md
└── examples/
    ├── group-chat-example.md
    ├── boss-message-example.md
    └── onboarding-example.md
```

---

## 注意事项

- 支持一句话快速使用，但上下文越多越准
- 对“谁在背刺”“谁在甩锅”这类判断，会尽量绑定证据，不空口定性
- 对“谁单身”这类敏感信息，不做隐私推断，只引用材料里已明确出现的信息
