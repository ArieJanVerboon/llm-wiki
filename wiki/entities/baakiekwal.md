---
type: entity
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [agent, baakie-pipeline, assessment, kwaliteit]
entity_kind: agent
aliases: []
---

# baakiekwal

> **Citatieslug:** `[[wiki/entities/baakiekwal]]`

## Wat is het

Tweede schakel in de [[wiki/topics/baakie-pipeline]]. LLM-subagent verantwoordelijk voor het **assessment-proces**: beoordeelt of documenten klaar zijn voor publicatie aan de hand van drie criteria.

## Rol in de pipeline

Documenten die door [[wiki/entities/baakiedoc]] zijn geregistreerd, komen bij baakiekwal voor toetsing op:

1. **Auteursrecht** — [[wiki/concepts/auteursrecht-wetenschappelijk-werk]]
2. **Bronvermelding** — [[wiki/concepts/bronvermelding]] *(nog geen aparte bron in raw)*
3. **Wetenschappelijke kwaliteit** — [[wiki/concepts/wetenschappelijke-kwaliteit]] *(nog geen aparte bron in raw)*

Goedgekeurde documenten gaan door naar [[wiki/entities/baakieprint]] voor publicatie. Afwijkingen leiden tot herstelacties of blokkade van publicatie.

## Belangrijke feiten

- Schrijft naar de registervelden: `prompt_assessment`, `kwaliteitsrapport`, `validatie_status`. — canon: `baakie-orchestrator/CLAUDE.md`
- Auteursrecht-criterium gedekt door de auteursrecht-bron uit `raw/` ([[wiki/sources/auteursrecht-wetenschappelijk-werk]]). — [[wiki/sources/auteursrecht-wetenschappelijk-werk]]

## Relaties

- Ontvangt input van: [[wiki/entities/baakiedoc]]
- Levert input aan: [[wiki/entities/baakieprint]] (alleen bij goedkeuring)
- Werkt onder: [[wiki/entities/de-baak]]

## Open vragen

- **Bronvermelding** en **wetenschappelijke kwaliteit** als criteria genoemd maar nog niet gedekt door bronnen in dit wiki. Placeholderpagina's wachten op bronnen.
- Exacte beslisregels voor "goedgekeurd / afwijking / geblokkeerd" staan in `baakie-orchestrator/spaces/baakiekwal/`, niet in de bronnen die in dit wiki zitten — relatie tussen wiki en operationele space nog te bepalen.

## Cross-references

- Genoemd in: [[wiki/sources/auteursrecht-wetenschappelijk-werk]], [[wiki/topics/baakie-pipeline]]
- Werkt op: [[wiki/concepts/auteursrecht-wetenschappelijk-werk]], [[wiki/concepts/bronvermelding]], [[wiki/concepts/wetenschappelijke-kwaliteit]]
- Operationele werkwijze (brug naar canon): [[wiki/concepts/baakiekwal-werkwijze]]
