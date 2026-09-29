---
type: entity
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [gereedschap, automatisering, research-flow, koppelingen]
entity_kind: product
aliases: []
---

# n8n

> **Citatieslug:** `[[wiki/entities/n8n]]`

## Wat is het

Automatiseringsplatform dat apps aan elkaar koppelt met workflows: als dit gebeurt, doe dan dat. Het koppelwerk van de estate — geen denkwerk, wel het verplaatsen van gegevens op een trigger of een schema.

## Belangrijke feiten

Stand 2026-09-24, waargenomen in de eigen instance — [[wiki/sources/linkermenu-reeks]] (n8n):

- Instance: **inspreadables.app.n8n.cloud**, met **13 workflows**.
- **Vier Antifragile-flows staan op Published.** Alleen *Antifragile Flow B* is in de bron aan een functie gekoppeld: onderzoek uit Perplexity vastleggen.
- Andere workflows bij naam genoemd: **Marktplaats Daily Scraper**, **n8n Workflow Backup to GitHub**, **Morning Invoice Reconciliation**.
- Credentials worden één keer gemaakt en in alle workflows hergebruikt; genoemd zijn Google, GitHub, **Perplexity** en **OpenRouter**.
- *Overview → Executions* houdt elke run bij met status, duur en de data per stap — de plek waar je ziet of een flow nog draait.
- **n8n API** en **Instance-level MCP** (onder Settings) laten Claude de workflows lezen en starten.
- Voor workflows die veel denkwerk vragen wijst de bron weg van n8n: liever LangGraph, of een AI-node met OpenRouter.

## Wat aandacht vraagt

- **De instance liep 2 versies achter** (stand 2026-09-24). Bijwerken gaat via het Admin Panel, en de bron adviseert dat te doen *nadat* de back-up naar GitHub gedraaid heeft. De pagina vermeldt expliciet dat er bij het nalopen niets is bijgewerkt. — [[wiki/sources/linkermenu-reeks]] (n8n)
- Dat advies is de goede volgorde: er bestaat een back-upflow, dus het risico is beheersbaar — maar alleen als die flow daadwerkelijk gedraaid heeft. Te controleren onder *Executions*.

## Rol in de research-flow

Stap 3 van [[wiki/topics/research-flow]], en de enige machinale schakel die de bron bij naam noemt. n8n neemt onderzoek uit [[wiki/entities/perplexity]] aan en zet het in [[wiki/entities/zotero]]; de machinetags `dedup:topic…`, `dedup:url…` en `ingested:review` daar zijn vermoedelijk zijn handschrift. Wat n8n **niet** doet volgens enige pagina in de reeks: iets afleveren in `raw/` van dit wiki.

Apify levert langs een tweede lijn aan n8n (*Marktplaats Daily Scraper*), buiten Perplexity om.

## Relaties

- Ontvangt van: [[wiki/entities/perplexity]], Apify
- Levert aan: [[wiki/entities/zotero]], GitHub (back-up van de workflows zelf)
- Grenst aan: [[wiki/entities/clickup]] — koppeling genoemd als mogelijkheid, niet als feit
- Alternatief voor denkwerk: LangGraph / LangSmith

## Open vragen

- Wat doen Antifragile A, C en D?
- Wat triggert Flow B, en wanneer draaide hij het laatst?
- Schrijft Flow B alleen in Zotero, of ook ergens anders?
- Is de back-upflow naar GitHub actief, en waar staat die repo?

## Cross-references

- Genoemd in: [[wiki/sources/linkermenu-reeks]], [[wiki/topics/research-flow]]
