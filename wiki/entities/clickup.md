---
type: entity
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [gereedschap, planning, research-flow, projectmanagement]
entity_kind: product
aliases: []
---

# ClickUp

> **Citatieslug:** `[[wiki/entities/clickup]]`

## Wat is het

Werkplek voor taken, documenten en AI-agents: Spaces met lijsten, weergaven (List, Board, Calendar, Gantt, Team), dashboards en doelen. In de [[wiki/topics/research-flow]] is dit de planlaag.

## Belangrijke feiten

Stand 2026-09-28, waargenomen in de werkruimte *Inspreadables* — [[wiki/sources/linkermenu-reeks]] (ClickUp):

- Eén Space: **Product Research & Delivery Hub**, met de lijst **L&D pilots project management**.
- **7 taken op To Do, alle met prioriteit High, geen eigenaar en geen datum.** Genoemd: de productonderzoek-pijplijn en het prototype-testplan.
- Twee AI-chats in de geschiedenis: **Create Marktanalyse Folder** en **API Token Generation**.
- Een Super Agent staat klaar: **Onboarding Assistant**. Super Agents voeren zelfstandig taken uit binnen ClickUp.
- Koppelen aan n8n of GitHub loopt via *Instellingen → Integrations* en een API-token.
- Dashboards en Goals zijn beschikbaar; de bron noemt een pilotdashboard voor het MT als toepassing.

## Wat dit zegt over de planlaag

Zeven taken die allemaal de hoogste prioriteit hebben, hebben in de praktijk geen prioriteit: zonder onderscheid is de rangorde leeg. Zonder eigenaar en zonder datum kan Planner er ook geen week van maken — de bron zegt dat zelf. De planlaag bestaat dus wel, maar hij stuurt niets aan.

De AI-chat **API Token Generation** is het spoor van een poging om ClickUp aan de automatisering te koppelen. Dat die koppeling werkt, blijkt nergens.

## Rol in de research-flow

Stap 1 van [[wiki/topics/research-flow]], en losgekoppeld van stap 3: ClickUp en [[wiki/entities/n8n]] weten niet van elkaar. Het onderzoek dat in de taken gepland staat, wordt uitgevoerd in [[wiki/entities/perplexity]] en vastgelegd door n8n, zonder dat de status ooit terugkomt in de taak.

## Relaties

- Zou moeten aansturen: [[wiki/entities/perplexity]], [[wiki/entities/n8n]] — koppeling niet aangetroffen
- Koppelbaar aan: n8n, GitHub (via API-token)
- Grenst aan: [[wiki/topics/baakie-pipeline]] — of de L&D-pilots daar deel van zijn, zegt de bron niet

## Open vragen

- Wat zijn de vijf niet-genoemde taken van de zeven?
- Is de ClickUp-n8n-koppeling ooit afgemaakt? Zo niet: is dat een gemis of een bewuste keuze?
- Hoort het pilotdashboard voor het MT in ClickUp, of op het portaal dat elders in de estate staat?

## Cross-references

- Genoemd in: [[wiki/sources/linkermenu-reeks]], [[wiki/topics/research-flow]]
