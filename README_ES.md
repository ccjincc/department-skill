<div align="center">

# department.skill

> *Quien acaba de entrar quiere entender el equipo más rápido. Quien ya lleva tiempo quiere perder menos en la dinámica organizacional.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

<br>

Acabas de entrar al equipo y quieres saber qué sitios para comer recomienda la gente de verdad cerca de la oficina?<br>
Quieres saber qué jefe es más fácil de tratar y con qué compañero es más seguro acercarte primero?<br>
Quieres entender cómo habla normalmente este departamento, cómo lleva las reuniones y cómo pide ayuda?<br>
Quieres saber qué cosas puedes preguntar directamente y cuáles conviene observar en silencio durante un par de días?<br>
Quieres captar el ritmo del equipo y cometer menos errores evitables?<br>
<br>
Llevas más tiempo y quieres entender el subtexto detrás de la forma vaga en la que habla tu jefe?<br>
Quieres ver quién está tirando trabajo hacia otros, quién se está quitando responsabilidad de encima y quién está difuminando el ownership?<br>
Quieres saber si revísalo otra vez significa corregirlo, replantearlo o bajar el ritmo?<br>
Quieres ver quién en un chat grupal realmente empuja el trabajo, quién solo hace señalización y quién mueve el ambiente en silencio?<br>

<br>

**Convierte chats del departamento, mensajes del jefe, capturas, documentos y comentarios de revisión de código en información realmente útil.**

[Fuentes Compatibles](#fuentes-compatibles)  [Instalación](#instalación)  [Herramientas Opcionales](#herramientas-opcionales)  [Uso](#uso)  [Ejemplos](#ejemplos)  [Escenarios Clave](#escenarios-clave)  [Estructura del Proyecto](#estructura-del-proyecto)  [Notas](#notas)  [Instalación Detallada](INSTALL.md)  [**中文**](README.md)  [**English**](README_EN.md)  [**Deutsch**](README_DE.md)  [**日本語**](README_JA.md)  [**Русский**](README_RU.md)  [**Português**](README_PT.md)

</div>

---

## Qué Es

`department.skill` no trata de "destilar" a una sola persona. Te ayuda a entender cómo funciona de verdad un departamento entero.

Se centra en cosas como:

- quién impulsa, quién decide, quién amortigua y quién difumina el ownership
- qué le importa realmente a un jefe detrás de una frase ambigua
- a quién debe acercarse primero una persona nueva, cómo preguntar y qué reglas implícitas conviene observar antes de hablar
- cómo puede alguien con más experiencia detectar reparto de culpa, puñaladas silenciosas, manipulación de agenda y política de bajo nivel

La salida no es un bloque vago de texto. Intenta darte:

- juicio estructurado
- conclusiones clave
- sugerencias de trato
- riesgos y nivel de confianza

---

## Fuentes Compatibles

Se admite entrada mixta. Cuanto más material haya, más fiable suele ser el análisis.

| Fuente | Chats | Docs / PDF | Imágenes / Capturas | Código / Comentarios | Notas |
|------|:-----:|:----------:|:-------------------:|:--------------------:|------|
| Conversaciones de WeChat / Feishu / DingTalk | Yes | No | Yes | No | Puedes pegar texto o subir capturas |
| Grupos del departamento / proyecto / reunión semanal | Yes | No | Yes | No | Util para mapear personas y ambiente |
| Documentos Word / texto plano | No | Yes | No | No | Util para notas, retrospectivas y explicaciones |
| PDF | No | Yes | No | No | Util para reportes, planes y actas |
| Markdown | Yes | Yes | No | Yes | Util para wikis, issues y PR |
| Codigo / PR / comentarios de review | Yes | No | No | Yes | Util para estilo de colaboracion, cadena de responsabilidad y senales ocultas |
| Contexto aportado por el usuario | Yes | No | No | No | Util para relaciones, zonas sensibles y antecedentes |

---

## Instalación

Consulta `INSTALL.md`.

Si solo necesitas el comportamiento base del Skill, el contenido actual del repositorio ya es suficiente.
Si además quieres soporte para Feishu, DingTalk, Slack, email y parsing de exportaciones, puedes instalar las dependencias opcionales:

```bash
pip3 install -r requirements.txt
playwright install chromium
```

---

## Herramientas Opcionales

Este repositorio también incluye un directorio `tools/` para convertir material bruto en entradas más limpias para el Skill.

- Recolección automática de Feishu: `tools/feishu_auto_collector.py`
- Parsing de exportaciones de Feishu: `tools/feishu_parser.py`
- Captura de Feishu vía navegador: `tools/feishu_browser.py`
- Acceso a Feishu por MCP: `tools/feishu_mcp_client.py`
- Recolección automática de DingTalk: `tools/dingtalk_auto_collector.py`
- Recolección automática de Slack: `tools/slack_auto_collector.py`
- Parsing de email: `tools/email_parser.py`
- Parsing genérico de exportaciones de chat: `tools/generic_chat_parser.py`
- Parsing de exportaciones de WeChat: `tools/wechat_parser.py`
- Parsing de exportaciones de QQ: `tools/qq_parser.py`

Para más detalle, consulta `tools/README.md`. Para fuentes de terceros y licencias, consulta `docs/THIRD_PARTY.md`.

---

## Uso

Lánzalo dentro de cualquier runtime compatible con Skills:

```text
/department
```

Formas de entrada preferidas:

- una sola línea aislada: suficiente para una lectura preliminar
- chats de varias rondas, capturas, documentos y contexto del usuario: mucho mejor para un análisis estable

---

## Ejemplos

**Escenario 1: Onboarding de una persona nueva**

```text
Usuario:
Acabo de entrar a este departamento. Quiero saber con quien es mas facil trabajar y que puedo preguntar directamente.

department.skill:
Primero, una conclusion rapida:
1. A parece alguien mas dispuesto a ayudar a la gente nueva. Responde corto, pero suele dar pasos concretos.
2. B es mas senior, pero hablar con esa persona cuesta mas. No es la mejor opcion para presionar desde el principio.
3. El estilo por defecto en este departamento es primero observar y luego hablar, especialmente en grupos donde esta el jefe.
```

**Escenario 2: Leer al jefe**

```text
Usuario:
Mi jefe dijo "revisalo otra vez". Que significa realmente?

department.skill:
En este contexto, suena menos a "haz unos cambios" y mas a:
1. la propuesta actual todavia no le convence
2. los riesgos y beneficios no estan lo bastante claros
3. quiere una conclusion mas fuerte, no mas detalle de proceso
```

**Escenario 3: Leer la dirección del equipo**

```text
Usuario:
Ayudame a ver quien esta empujando el trabajo en este grupo y quien esta soltando culpa.

department.skill:
A parece el verdadero impulsor. Cierra bucles, asigna owners y anade fechas.
C muestra un patron claro de difuminar ownership al formular la responsabilidad como "veamoslo entre todos".
D por ahora se parece mas a separacion de riesgo que a una punalada confirmada, pero ya hay senales tempranas de desplazamiento de culpa.
```

---

## Escenarios Clave

### Apoyo a Recién Llegados

- qué lugares para comer se mencionan repetidamente y cómo es el ritmo de comida del equipo
- qué jefe cuesta más de manejar y con qué compañero es más seguro pedir ayuda
- qué reglas implícitas existen y qué preguntas conviene observar antes de hacer
- qué formas de descansar razonablemente son en realidad observación del ritmo, y qué conductas sí son realmente arriesgadas
- tratar los detalles sensibles con cuidado; por ejemplo, solo mencionar estado sentimental si aparece explícitamente en el material

### Uso para Personal con Más Experiencia

- si una frase del jefe es un recordatorio, un rechazo, un control del ritmo o una transferencia de responsabilidad
- qué compañero está desplazando culpa, cuál puede estar jugando en tu contra y quién está difuminando el ownership
- qué añadir después y cómo empujar la situación de forma más segura

---

## Estructura del Proyecto

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

- Funciona con una sola línea, pero con más contexto es mucho más fiable.
- Para juicios como quién apuñala por la espalda o quién desplaza culpa, intenta mantenerse pegado a evidencia observable en lugar de acusaciones vacías.
- Para detalles sensibles como quién está soltero, no infiere información privada y solo cita lo que aparece explícitamente en el material de origen.
