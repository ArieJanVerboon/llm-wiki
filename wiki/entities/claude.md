---
type: entity
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [gereedschap, agent, geplande-taken, research-flow, kennisbank]
entity_kind: product
aliases: [Claude Code, Cowork, claude.ai]
---

# Claude

> **Citatieslug:** `[[wiki/entities/claude]]`

## Wat is het

Het gereedschap dat dit wiki schrijft. In de estate komt het in drie gedaanten voor met **drie verschillende linkermenu's**, en dat onderscheid is geen detail — het bepaalt waar iets kan wonen.

| Gedaante | Menu | Geplande taken |
|---|---|---|
| Chat op claude.ai | New, Projects, Artifacts, Scheduled, Design, Customize | **Scheduled** |
| Cowork | New, Artifacts, Routines, Customize | **Routines** (Projects en Design vallen weg) |
| Terminal (Claude Code) | geen zijbalk | **bestaan niet** — wel `claude -p "…"` in de Windows Taakplanner, zoals bij de Visma-flow |

Stand 2026-09-24 — [[wiki/sources/linkermenu-reeks]] (Claude).

## De geplande taken

Dit is de plek waar [[wiki/topics/research-flow]] op stukloopt, dus letterlijk wat de bron zegt:

- Op `claude.ai/scheduled-task` staan **vier** taken. *"Jij hebt er vier; alleen de Substack Digest draait (elke donderdag 8:00) en vraagt aandacht."*
- De zijbalkschets van diezelfde pagina noemt **2 taken**. ⚠ De bron spreekt zichzelf tegen; vermoedelijk telt de zijbalk alleen de actieve en de kaart alle vier, maar dat staat er niet.
- De zijbalk toont per taak het ritme (bijvoorbeeld *Weekly*) en een geel stipje als een run aandacht nodig heeft.
- Onderaan de pagina staan voorbeeldtaken die je kunt overnemen: Daily briefing, Inbox triage, Meeting prep, Weekly review.

**Waarom dit telt.** Zestien van de twintig pagina's in [[wiki/sources/linkermenu-reeks]] beloven dat een weektaak *Weekly: AI-tools Updates* elke maandag de changelogs naleest. Geen ervan zegt waar die taak staat. De ChatGPT-pagina wijst hem hierheen (*Gepland* is daar leeg, met de opmerking dat de Claude-taken dit al doen). Als hij dus bij deze vier hoort en er draait alleen de Substack Digest, dan wordt die belofte niet ingelost. Dat is test **T6** in het testplan van [[wiki/topics/research-flow]].

## Artifacts is een oppervlak, geen opslag

De bron noemt Artifacts als de plek om *"die uitlegpagina van vorige week"* terug te vinden. Dat werkt — maar het is een lijst op claude.ai, geen bewaarplaats: geen git, geen back-up, niets dat meereist naar een andere machine.

Op **2026-09-29** is dat concreet geworden: de twintig pagina's van [[wiki/sources/linkermenu-reeks]] bestonden twee maanden uitsluitend als gepubliceerde artifacts, en zijn toen byte voor byte naar `raw/` gehaald. Zie ook [[wiki/concepts/three-layer-architecture]] — wat buiten de repo staat is geen bron.

## Belangrijke feiten

- **Cowork mag drie Windows-computers gebruiken** (stand 2026-09-24). Daar staat ook of taken alleen lokaal blijven, en welke browser de voorkeur heeft.
- De lijst *Chats and tasks* mengt chats en Cowork-taken door elkaar, nieuwste boven.
- Instellingen zijn bestanden, en in de terminal blijven gesprekken lokaal — de bron maakt dat onderscheid per gedaante expliciet.
- *Settings → Memory* laat zien en aanpassen wat Claude over je onthoudt.
- *Design → Slides* is het startpunt voor een deck in De Baak-huisstijl; de huisstijl zelf blijft leidend, zie `CLAUDE.md` §9.
- Een nieuw gesprek over een bestaand onderwerp begint via Pinned → project → New — bijvoorbeeld voor [[wiki/entities/baakiedoc]].
- In Claude Code geeft `/` de volledige commandolijst van *jouw* versie; die verschuift per update, dus een opgeschreven lijst verjaart.

## Rol in de estate

Schrijft dit wiki (stap 6 van [[wiki/topics/research-flow]]), gelezen via [[wiki/entities/obsidian]]. Draagt daarnaast de geplande taken die de enige periodieke aanzet van de research-flow zouden moeten zijn. Wordt in vrijwel elke pagina van de reeks als referentiepunt gebruikt — andere gereedschappen worden uitgelegd door te zeggen wat hun equivalent van Claude is.

## Relaties

- Schrijft: `wiki/` in deze kluis — zie [[wiki/concepts/ingest-query-lint]]
- Gelezen via: [[wiki/entities/obsidian]]
- Zou moeten aanzetten: [[wiki/topics/research-flow]] via een geplande taak
- Bedient op afstand: [[wiki/entities/n8n]] (n8n API en Instance-level MCP)

## Open vragen

- Wat zijn de vier geplande taken, en welke staan aan? Zonder dat antwoord blijft T6 open.
- Zijn 2 en 4 te rijmen, of is één van beide getallen simpelweg fout in de bron?
- Waar staat de Visma-flow precies in de Windows Taakplanner, en op welke van de drie computers?
- Wat gebeurt er met een Cowork-taak als de computer waarop hij hoort uit staat?

## Cross-references

- Genoemd in: [[wiki/sources/linkermenu-reeks]], [[wiki/topics/research-flow]], [[wiki/topics/gereedschapslandschap]]
