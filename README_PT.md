<div align="center">

# department.skill

> *Quem acabou de entrar quer entender o time mais rápido. Quem já está há mais tempo quer perder menos para a dinâmica organizacional.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

<br>

Acabou de entrar e quer saber quais lugares para comer perto do escritorio sao realmente recomendados pelo time?<br>
Quer saber qual chefe e mais facil de lidar e com qual colega e mais seguro falar primeiro?<br>
Quer entender como esse departamento normalmente fala, faz reunioes e pede ajuda?<br>
Quer saber o que pode perguntar diretamente e o que vale observar em silencio por uns dois dias?<br>
Quer pegar o ritmo do time e cometer menos erros evitaveis?<br>
<br>
Ja esta ha mais tempo e quer ler o subtexto por tras das frases vagas da lideranca?<br>
Quer ver quem empurra trabalho para os outros, quem afasta responsabilidade de si e quem embaralha o ownership?<br>
Quer entender se "olha isso de novo" quer dizer corrigir, repensar ou desacelerar o ritmo?<br>
Quer perceber quem no grupo realmente faz as coisas andarem, quem so sinaliza posicao e quem conduz o ambiente em silencio?<br>

<br>

**Transforma chats do departamento, mensagens de lideranca, capturas, documentos e comentarios de review em informacao realmente util.**

[Fontes Compativeis](#fontes-compativeis) · [Instalacao](#instalacao) · [Ferramentas Opcionais](#ferramentas-opcionais) · [Uso](#uso) · [Exemplos](#exemplos) · [Cenarios-Chave](#cenarios-chave) · [Estrutura do Projeto](#estrutura-do-projeto) · [Notas](#notas) · [Instalacao Detalhada](INSTALL.md) · [**中文**](README.md) · [**English**](README_EN.md) · [**Español**](README_ES.md) · [**Deutsch**](README_DE.md) · [**日本語**](README_JA.md) · [**Русский**](README_RU.md)

</div>

---

## O Que E

`department.skill` nao serve para "destilar" uma unica pessoa. Ele ajuda voce a entender como um departamento inteiro realmente funciona.

Ele olha para coisas como:

- quem empurra, quem decide, quem amortece e quem embaralha o ownership
- o que realmente importa para a lideranca por tras de uma frase vaga
- de quem uma pessoa nova deve se aproximar primeiro, como perguntar e quais regras implicitas valem observar antes de falar
- como pessoas mais experientes podem notar empurrao de culpa, sabotagem silenciosa, conducao de pauta e politica de escritorio em nivel baixo

A saida nao e um bloco vago de texto. A ideia e entregar:

- julgamento estruturado
- conclusoes principais
- sugestoes de interacao
- riscos e nivel de confianca

---

## Fontes Compativeis

Entrada mista e suportada. Quanto mais material, mais confiavel tende a ser a leitura.

| Fonte | Chats | Docs / PDF | Imagens / Capturas | Codigo / Comentarios | Notas |
|------|:-----:|:----------:|:------------------:|:--------------------:|------|
| Conversas de WeChat / Feishu / DingTalk | Yes | No | Yes | No | Pode colar texto ou subir capturas |
| Grupos de departamento / projeto / alinhamento semanal | Yes | No | Yes | No | Bom para mapa de pessoas e clima |
| Documentos Word / texto puro | No | Yes | No | No | Bom para notas, retros e explicacoes |
| PDF | No | Yes | No | No | Bom para relatorios, planos e notas de reuniao |
| Markdown | Yes | Yes | No | Yes | Bom para wiki, issues e descricoes de PR |
| Codigo / PR / comentarios de review | Yes | No | No | Yes | Bom para estilo de colaboracao, cadeia de responsabilidade e sinais escondidos |
| Contexto adicional do usuario | Yes | No | No | No | Ajuda em relacoes, alertas e historico |

---

## Instalacao

Veja `INSTALL.md`.

Se voce so precisa do comportamento basico do Skill, o conteudo atual do repositorio ja basta.
Se tambem quiser suporte para Feishu, DingTalk, Slack, email e parsing de exportacoes, voce pode instalar as dependencias opcionais:

```bash
pip3 install -r requirements.txt
playwright install chromium
```

---

## Ferramentas Opcionais

Este repositorio tambem inclui um diretorio `tools/` para transformar material bruto em entradas mais limpas para o Skill.

- Coleta automatica de Feishu: `tools/feishu_auto_collector.py`
- Parsing de exportacoes do Feishu: `tools/feishu_parser.py`
- Captura de Feishu via navegador: `tools/feishu_browser.py`
- Acesso ao Feishu por MCP: `tools/feishu_mcp_client.py`
- Coleta automatica de DingTalk: `tools/dingtalk_auto_collector.py`
- Coleta automatica de Slack: `tools/slack_auto_collector.py`
- Parsing de email: `tools/email_parser.py`
- Parsing generico de exportacoes de chat: `tools/generic_chat_parser.py`
- Parsing de exportacoes do WeChat: `tools/wechat_parser.py`
- Parsing de exportacoes do QQ: `tools/qq_parser.py`

Para mais detalhe, veja `tools/README.md`. Fontes de terceiros e avisos de licenca estao em `docs/THIRD_PARTY.md`.

---

## Uso

Chame dentro de um runtime compativel com Skills:

```text
/department
```

Entradas mais recomendadas:

- uma linha isolada: suficiente para uma leitura inicial grosseira
- conversas longas, capturas, documentos e contexto do usuario: muito melhor para uma analise estavel

---

## Exemplos

**Cenario 1: Onboarding de quem acabou de entrar**

```text
Usuario:
Acabei de entrar neste departamento. Quero entender com quem e mais facil trabalhar e o que posso perguntar diretamente.

department.skill:
Primeiro, uma leitura rapida:
1. A parece alguem mais disposto a ajudar quem acabou de chegar. As respostas sao curtas, mas normalmente trazem um proximo passo concreto.
2. B e mais senior, mas o custo de comunicacao e maior. Nao e a melhor pessoa para pressionar logo de cara.
3. O estilo padrao deste departamento e "primeiro observar, depois falar", especialmente em grupos onde o chefe esta presente.
```

**Cenario 2: Ler a lideranca**

```text
Usuario:
Meu chefe disse "olha isso de novo". O que isso realmente quer dizer aqui?

department.skill:
Neste contexto, isso soa menos como "faz alguns ajustes" e mais como:
1. a proposta atual ainda nao convenceu
2. riscos e beneficios ainda nao estao claros o bastante
3. a lideranca quer uma conclusao mais forte, nao mais detalhe de processo
```

**Cenario 3: Ler a direcao do time**

```text
Usuario:
Me ajuda a ver quem nesse grupo realmente faz o trabalho andar e quem esta jogando culpa para os lados.

department.skill:
A parece ser o verdadeiro motor. Fecha ciclos, define owner e coloca prazo.
C mostra um padrao claro de embaralhar ownership ao formular responsabilidade como "vamos todos olhar de novo".
D por enquanto parece mais separacao de risco do que sabotagem confirmada, mas ja existem sinais iniciais de deslocamento de culpa.
```

---

## Cenarios-Chave

### Para Quem Acabou de Entrar

- quais lugares para comer aparecem repetidamente e como e o ritmo de refeicao do time
- qual lideranca e mais dificil de lidar e com qual colega e mais seguro pedir ajuda
- quais regras implicitas existem e quais perguntas convem observar antes de fazer
- quais formas de "relaxar de forma razoavel" sao apenas leitura de ritmo e quais comportamentos realmente trazem risco
- detalhes sensiveis, como estado civil ou relacao, so devem aparecer se estiverem explicitos no material

### Para Pessoas Mais Experientes

- se uma frase da lideranca funciona como lembrete, negacao, controle de ritmo ou transferencia de responsabilidade
- qual colega empurra culpa, quem pode estar jogando contra voce e quem embaralha o ownership
- o que acrescentar depois e como empurrar a situacao de forma mais segura

---

## Estrutura do Projeto

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

## Notas

- Funciona com uma unica linha, mas com mais contexto a confiabilidade sobe bastante.
- Em julgamentos como "quem esta apunhalando pelas costas" ou "quem esta deslocando culpa", o Skill tenta se apoiar em sinais observaveis e nao em acusacoes vazias.
- Para detalhes sensiveis como "quem esta solteiro", ele nao faz inferencia privada e so cita o que aparece explicitamente no material.
