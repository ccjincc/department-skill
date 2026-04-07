<div align="center">

# department.skill

> *新しく入った人はチームを早く理解したい。長くいる人は組織で余計に損したくない。*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

誰が話しやすいか、上司の言葉が本当は何を意味するのか知りたい？<br>
誰が進め、誰が止め、誰が owner を曖昧にしているか見抜きたい？<br>

**チャット、スクリーンショット、文書、レビューコメントを、使える部署情報に変える。**

[対応データ](#対応データ)  [インストール](#インストール)  [任意ツール](#任意ツール)  [使い方](#使い方)  [例](#例)  [詳細インストール](INSTALL.md)  [**中文**](README.md)  [**English**](README_EN.md)  [**Español**](README_ES.md)  [**Deutsch**](README_DE.md)  [**Русский**](README_RU.md)  [**Português**](README_PT.md)

</div>

---

## これは何か

`department.skill` は、チームが実際にどう動いているかを読む Skill です。暗黙のシグナル、owner の流れ、オンボーディングのルール、安全な返し方を整理します。

## 対応データ

- WeChat / Feishu / DingTalk の会話
- チームやプロジェクトのグループチャット
- ドキュメント、PDF、Markdown、テキストメモ
- コードレビュー、PR、Issue コメント
- ユーザーが補足する背景情報

## インストール

`INSTALL.md` を参照してください。

```bash
pip3 install -r requirements.txt
playwright install chromium
```

## 使い方

```text
/department
```
