<div align="center">

# department.skill

> *Neue Teammitglieder wollen das Team schneller verstehen. Erfahrene wollen weniger an Organisationsdynamik verlieren.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

<br>

Neu im Team und du willst wissen, welche Essenslaeden in der Naehe wirklich immer wieder empfohlen werden?<br>
Willst du wissen, welche Fuehrungskraft leichter ansprechbar ist und mit welchem Kollegen du am sichersten zuerst sprechen solltest?<br>
Willst du verstehen, wie dieses Department normalerweise spricht, Meetings fuehrt und Hilfe anfragt?<br>
Willst du wissen, was du direkt fragen kannst und was du besser erst zwei Tage lang still beobachtest?<br>
Willst du den Teamrhythmus verstehen und weniger vermeidbare Fehler machen?<br>
<br>
Bist du schon laenger dabei und willst die Zwischentoene hinter vagen Chefsaetzen besser lesen?<br>
Willst du sehen, wer Arbeit nach unten weiterreicht, wer Verantwortung von sich wegschiebt und wer Ownership verwischt?<br>
Willst du wissen, ob "schau noch mal drauf" heisst, dass du ueberarbeiten, neu denken oder das Tempo rausnehmen sollst?<br>
Willst du sehen, wer im Gruppenchat wirklich vorantreibt, wer nur Signale sendet und wer die Richtung still beeinflusst?<br>

<br>

**Verwandle Department-Chats, Chef-Nachrichten, Screenshots, Dokumente und Code-Review-Kommentare in wirklich nutzbare Informationen.**

[Unterstuetzte Datenquellen](#unterstuetzte-datenquellen) · [Installation](#installation) · [Optionale Tools](#optionale-tools) · [Verwendung](#verwendung) · [Beispiele](#beispiele) · [Schluesselszenarien](#schluesselszenarien) · [Projektstruktur](#projektstruktur) · [Hinweise](#hinweise) · [Detaillierte Installation](INSTALL.md) · [**中文**](README.md) · [**English**](README_EN.md) · [**Español**](README_ES.md) · [**日本語**](README_JA.md) · [**Русский**](README_RU.md) · [**Português**](README_PT.md)

</div>

---

## Was Es Ist

`department.skill` geht nicht darum, eine einzelne Person zu "destillieren". Es hilft dir zu verstehen, wie ein gesamtes Department in der Praxis wirklich funktioniert.

Es schaut auf Dinge wie:

- wer treibt, wer entscheidet, wer puffert und wer Ownership verwischt
- was einem Vorgesetzten hinter einem vagen Satz wirklich wichtig ist
- an wen sich neue Leute zuerst wenden sollten, wie sie fragen und welche unausgesprochenen Regeln sie besser zuerst beobachten
- wie erfahrenere Leute Schuldverschiebung, stille Gegenspieler, Agenda-Steuerung und kleine Bueropolitik erkennen koennen

Die Ausgabe ist kein vager Textblock. Sie soll dir geben:

- strukturierte Einordnung
- zentrale Schlussfolgerungen
- Hinweise fuer den Umgang
- Risiken und Vertrauensniveau

---

## Unterstuetzte Datenquellen

Gemischte Eingaben werden unterstuetzt. Mehr Material fuehrt in der Regel zu belastbarerer Analyse.

| Quelle | Chats | Docs / PDF | Bilder / Screenshots | Code / Kommentare | Hinweise |
|------|:-----:|:----------:|:--------------------:|:-----------------:|------|
| WeChat / Feishu / DingTalk Unterhaltungen | Yes | No | Yes | No | Text direkt einfuegen oder Screenshots hochladen |
| Department-Gruppen / Projektgruppen / Weekly-Gruppen | Yes | No | Yes | No | Gut fuer Personenkarte und Teamklima |
| Word-Dokumente / Klartext | No | Yes | No | No | Gut fuer Notizen, Retros und Erklaerungen |
| PDF | No | Yes | No | No | Gut fuer Reports, Plaene und Meeting-Notizen |
| Markdown | Yes | Yes | No | Yes | Gut fuer Wikis, Issues und PR-Beschreibungen |
| Code / PR / Review-Kommentare | Yes | No | No | Yes | Gut fuer Kollaborationsstil, Verantwortungsketten und versteckte Signale |
| Zusatzkontext vom Nutzer | Yes | No | No | No | Nuetzlich fuer Beziehungsbild, rote Flaggen und Hintergrund |

---

## Installation

Siehe `INSTALL.md`.

Wenn du nur das Kernverhalten des Skills brauchst, reicht der aktuelle Repository-Inhalt bereits aus.
Wenn du zusaetzlich Feishu-, DingTalk-, Slack-, E-Mail- und Export-Parsing-Unterstuetzung willst, kannst du die optionalen Abhaengigkeiten installieren:

```bash
pip3 install -r requirements.txt
playwright install chromium
```

---

## Optionale Tools

Dieses Repository enthaelt ausserdem ein Verzeichnis `tools/`, das Rohmaterial in sauberere Eingaben fuer das Skill verwandelt.

- Feishu Auto-Sammlung: `tools/feishu_auto_collector.py`
- Feishu Export-Parsing: `tools/feishu_parser.py`
- Feishu Browser-Erfassung: `tools/feishu_browser.py`
- Feishu Zugriff ueber MCP: `tools/feishu_mcp_client.py`
- DingTalk Auto-Sammlung: `tools/dingtalk_auto_collector.py`
- Slack Auto-Sammlung: `tools/slack_auto_collector.py`
- E-Mail-Parsing: `tools/email_parser.py`
- Generisches Chat-Export-Parsing: `tools/generic_chat_parser.py`
- WeChat Export-Parsing: `tools/wechat_parser.py`
- QQ Export-Parsing: `tools/qq_parser.py`

Fuer mehr Details siehe `tools/README.md`. Hinweise zu Quellen und Lizenzen stehen in `docs/THIRD_PARTY.md`.

---

## Verwendung

Rufe es in einer Skill-kompatiblen Laufzeit auf:

```text
/department
```

Bevorzugte Eingabeformen:

- eine einzelne isolierte Zeile: genug fuer eine erste grobe Einordnung
- mehrteilige Chats, Screenshots, Dokumente und Nutzerkontext: deutlich besser fuer stabile Analyse

---

## Beispiele

**Szenario 1: Onboarding fuer neue Teammitglieder**

```text
Nutzer:
Ich bin neu in diesem Department. Ich moechte verstehen, mit wem man leichter arbeiten kann und was ich direkt fragen kann.

department.skill:
Erst einmal eine schnelle Einordnung:
1. A wirkt wie jemand, der neuen Leuten eher hilft. Die Antworten sind kurz, aber meist konkret.
2. B ist seniorer, kostet kommunikativ aber mehr. Nicht die beste Person fuer aggressives Nachfassen direkt am Anfang.
3. Der Default-Stil in diesem Department ist zuerst beobachten, dann sprechen, besonders in Gruppen, in denen der Vorgesetzte mitliest.
```

**Szenario 2: Den Chef lesen**

```text
Nutzer:
Mein Chef hat gesagt: "schau noch mal drauf". Was bedeutet das hier wirklich?

department.skill:
In diesem Kontext klingt es weniger nach "mach ein paar Aenderungen" und mehr nach:
1. die aktuelle Vorlage ueberzeugt noch nicht
2. Risiken und Nutzen sind noch nicht klar genug
3. es wird eine staerkere Schlussfolgerung erwartet, nicht mehr Prozessdetail
```

**Szenario 3: Teamrichtung lesen**

```text
Nutzer:
Hilf mir zu sehen, wer in dieser Gruppe wirklich vorantreibt und wer Schuld ablaedt.

department.skill:
A sieht nach dem eigentlichen Treiber aus. Diese Person schliesst Schleifen, setzt Owner und nennt Fristen.
C zeigt ein klares Muster, Ownership zu verwischen, indem Verantwortung als "lasst uns alle noch mal draufschauen" formuliert wird.
D sieht im Moment eher nach Risikoabgrenzung als nach bestaetigtem Rueckenstich aus, aber erste Anzeichen fuer Schuldverschiebung sind schon da.
```

---

## Schluesselszenarien

### Hilfe fuer neue Leute

- welche Essensorte wiederholt erwaehnt werden und wie der Mahlzeitenrhythmus im Team aussieht
- welche Fuehrungskraft schwerer zu handhaben ist und mit welchem Kollegen Hilfeanfragen am sichersten sind
- welche stillen Regeln gelten und welche Fragen man besser erst beobachtet, bevor man sie stellt
- welche Formen von "vernuenftigem Leerlauf" in Wahrheit nur Rhythmusbeobachtung sind und welches Verhalten wirklich riskant ist
- sensible Details vorsichtig behandeln; Beziehungsstatus zum Beispiel nur nennen, wenn er explizit im Material steht

### Nutzung fuer Erfahrene

- ob ein Chef-Satz eher Erinnerung, Ablehnung, Tempokontrolle oder Verantwortungsverschiebung ist
- welcher Kollege Schuld schiebt, wer eventuell gegen dich arbeitet und wer Ownership verwischt
- was man als Naechstes ergaenzen und wie man die Situation sicherer anschieben kann

---

## Projektstruktur

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

## Hinweise

- Es funktioniert auch mit einer einzelnen Zeile, aber mehr Kontext macht es deutlich verlaesslicher.
- Bei Urteilen wie "wer sticht von hinten" oder "wer schiebt Schuld" versucht es, bei beobachtbarer Evidenz zu bleiben statt mit leeren Anschuldigungen zu arbeiten.
- Bei sensiblen Details wie "wer ist single" werden keine privaten Informationen geraten; genannt wird nur, was explizit im Ausgangsmaterial steht.
