<div align="center">

# department.skill

> *新しく入った人はチームを早く理解したい。長くいる人は組織で余計に損したくない。*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

<br>

入ったばかりで、近くで本当に評判のいい外食先がどこか知りたい？<br>
どの上司が比較的やり取りしやすく、どの同僚に最初に声をかけるのが安全か知りたい？<br>
この部署が普段どう話し、どう会議し、どう助けを求めるのか知りたい？<br>
何は直接聞いてよくて、何は二日くらい静かに観察してから触れるべきか知りたい？<br>
チームのリズムをつかんで、余計な失敗を減らしたい？<br>
<br>
しばらく働いていて、上司の曖昧な言い回しの裏にある本音を読みたい？<br>
誰が仕事を押し付け、誰が責任を薄め、誰が owner を曖昧にしているのか見たい？<br>
「もう一度見ておいて」が、修正なのか、考え直しなのか、ペース調整なのか知りたい？<br>
グループチャットで本当に前に進めている人、ただ態度だけ示している人、静かに流れを作っている人を見抜きたい？<br>

<br>

**部署の群聊、上司のメッセージ、スクリーンショット、文書、コードレビューコメントを、実際に使える部署情報へ変える。**

[対応データ](#対応データ) · [インストール](#インストール) · [任意ツール](#任意ツール) · [使い方](#使い方) · [例](#例) · [主要シナリオ](#主要シナリオ) · [プロジェクト構成](#プロジェクト構成) · [注意](#注意) · [詳細インストール](INSTALL.md) · [**中文**](README.md) · [**English**](README_EN.md) · [**Español**](README_ES.md) · [**Deutsch**](README_DE.md) · [**Русский**](README_RU.md) · [**Português**](README_PT.md)

</div>

---

## これは何か

`department.skill` は、誰か一人を「蒸留」するための Skill ではありません。部署全体が実際にどう回っているかを理解するための Skill です。

主に見るものは次のようなものです。

- 誰が進め、誰が決め、誰が緩衝し、誰が owner を曖昧にしているか
- 上司の曖昧な一言の裏で、本当に何が重視されているか
- 新しく入った人がまず誰に近づくべきか、どう聞くべきか、何を先に観察すべきか
- ある程度経験のある人が、責任の押し付け、静かな背刺し、空気の誘導、小さな社内政治をどう見抜くか

出力は曖昧な感想文ではありません。目指すのは次のような整理です。

- 構造化された判断
- 重要な結論
- 対応方針
- リスクと確度

---

## 対応データ

入力は混在していて構いません。材料が多いほど分析は安定しやすくなります。

| ソース | チャット | Docs / PDF | 画像 / スクリーンショット | コード / コメント | 備考 |
|------|:--------:|:----------:|:-------------------------:|:-----------------:|------|
| WeChat / Feishu / DingTalk の会話 | Yes | No | Yes | No | テキスト貼り付けでもスクショでもよい |
| 部署グループ / プロジェクトグループ / 定例グループ | Yes | No | Yes | No | 人間関係や雰囲気の把握に向く |
| Word / プレーンテキスト文書 | No | Yes | No | No | メモ、振り返り、説明文に向く |
| PDF | No | Yes | No | No | 週報、計画、会議メモに向く |
| Markdown | Yes | Yes | No | Yes | Wiki、Issue、PR 説明に向く |
| コード / PR / Review コメント | Yes | No | No | Yes | 協業スタイル、責任線、隠れたシグナルの把握に向く |
| ユーザー補足の背景情報 | Yes | No | No | No | 関係性、赤信号、過去経緯の補助になる |

---

## インストール

`INSTALL.md` を参照してください。

基本的な Skill の動作だけなら、現在のリポジトリ内容で十分です。
Feishu、DingTalk、Slack、メール、各種エクスポート解析まで使いたい場合は、任意依存を追加できます。

```bash
pip3 install -r requirements.txt
playwright install chromium
```

---

## 任意ツール

このリポジトリには、元データを Skill に渡しやすい形へ整える `tools/` ディレクトリも含まれています。

- Feishu 自動収集: `tools/feishu_auto_collector.py`
- Feishu エクスポート解析: `tools/feishu_parser.py`
- Feishu ブラウザ取得: `tools/feishu_browser.py`
- Feishu MCP 読み取り: `tools/feishu_mcp_client.py`
- DingTalk 自動収集: `tools/dingtalk_auto_collector.py`
- Slack 自動収集: `tools/slack_auto_collector.py`
- メール解析: `tools/email_parser.py`
- 汎用チャットエクスポート解析: `tools/generic_chat_parser.py`
- WeChat エクスポート解析: `tools/wechat_parser.py`
- QQ エクスポート解析: `tools/qq_parser.py`

詳しくは `tools/README.md`、第三者由来とライセンス表記は `docs/THIRD_PARTY.md` を参照してください。

---

## 使い方

Skill 対応ランタイムで次のように呼び出します。

```text
/department
```

入力のおすすめは次の通りです。

- 一言だけ: ざっくりした初期判断は可能
- 複数ラウンドの会話、スクショ、文書、背景説明つき: より安定した分析に向く

---

## 例

**シナリオ 1: 新しく入った人のオンボーディング**

```text
ユーザー:
この部署に入ったばかりです。誰が話しやすいか、何を直接聞いてよいか知りたいです。

department.skill:
まず短く結論を言うと:
1. A は新しく入った人を助けやすいタイプに見えます。返答は短いですが、具体的な次の手を返すことが多いです。
2. B はよりシニアですが、会話コストが高めです。最初から強く追う相手としては向きません。
3. この部署の基本スタイルは「まず観察し、その後に話す」です。特に上司がいる群聊ではその傾向が強いです。
```

**シナリオ 2: 上司の言葉を読む**

```text
ユーザー:
上司に「もう一度見ておいて」と言われました。ここでは何を意味しますか。

department.skill:
この文脈では「少し修正して」よりも、次の意味に近いです:
1. 今の案ではまだ納得されていない
2. リスクとメリットの整理がまだ弱い
3. 手順の説明ではなく、もっと強い結論が欲しい
```

**シナリオ 3: チームの流れを読む**

```text
ユーザー:
このグループで誰が本当に進めていて、誰が責任を散らしているか見たいです。

department.skill:
A は実質的な推進役に見えます。ループを閉じ、owner を置き、期限を明確にしています。
C は責任を「みんなで一度見ましょう」の形にぼかしており、ownership を薄める癖が見えます。
D は現時点では確定的な背刺しというより、自分のリスクを切り分けている段階に見えますが、責任移動の初期サインはあります。
```

---

## 主要シナリオ

### 新しく入った人向け

- 周辺でよく言及される外食先や、チームの食事リズム
- どの上司が扱いにくく、どの同僚に助けを求めるのが比較的安全か
- どんな暗黙ルールがあり、どの質問は先に観察してから触れるべきか
- 「ほどよく力を抜く」が単なるリズム観察なのか、本当に危ない行動なのか
- 恋愛状況のような敏感情報は、素材に明示されている場合だけ扱う

### ある程度経験のある人向け

- 上司の一言が、注意、否定、ペース調整、責任移動のどれに近いか
- 誰が責任を押しつけ、誰が裏で動き、誰が owner を曖昧にしているか
- 次に何を足し、どう進めるとより安全か

---

## プロジェクト構成

```text
department/
|- SKILL.md
|- README.md
|- README_EN.md
|- README_ES.md
|- README_DE.md
|- README_JA.md
|- README_RU.md
|- README_PT.md
|- INSTALL.md
|- LICENSE
|- .gitignore
|- requirements.txt
|- docs/
|  |- PRD.md
|  |- FAQ.md
|  `- THIRD_PARTY.md
|- prompts/
|  |- intake.md
|  |- structure_analyzer.md
|  |- subtext_analyzer.md
|  `- response_strategy.md
|- tools/
|  |- README.md
|  |- feishu_auto_collector.py
|  |- feishu_parser.py
|  |- feishu_browser.py
|  |- feishu_mcp_client.py
|  |- dingtalk_auto_collector.py
|  |- slack_auto_collector.py
|  |- email_parser.py
|  |- generic_chat_parser.py
|  |- wechat_parser.py
|  `- qq_parser.py
`- examples/
   |- group-chat-example.md
   |- boss-message-example.md
   `- onboarding-example.md
```

---

## 注意

- 一行だけでも使えますが、文脈が多いほど信頼性はかなり上がります。
- 「誰が背刺しているか」「誰が責任を流しているか」のような判断では、空気だけで決めつけず、観察可能な材料に寄せて判断します。
- 「誰が独身か」のような敏感な情報は、私的推測を行わず、素材に明示されている内容だけを扱います。
