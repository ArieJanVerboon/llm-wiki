---
type: entity
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [agent, baakie-pipeline, publicatie, output]
entity_kind: agent
aliases: []
---

# baakieprint

> **Citatieslug:** `[[wiki/entities/baakieprint]]`

## Wat is het

Derde schakel in de [[wiki/topics/baakie-pipeline]]. LLM-subagent verantwoordelijk voor **publicatie-output** in vijf format-targets: doc, pdf, powerpoint, responsive HTML, en [[wiki/entities/anewspring]] (LMS HTML-content). Alles op basis van skeletons.

Per 2026-05-20 is de voormalige `baakiehtml`-space samengevoegd met baakieprint omdat beide hetzelfde mechanisme gebruiken (skeleton → format → output).

## Format-targets

| Format | Bestemming | Skeleton |
|---|---|---|
| **doc** | Word-deliverable | TBD in `baakie-orchestrator/spaces/baakieprint/knowledge/` |
| **pdf** | PDF-deliverable, vaak vanuit doc/html geconverteerd | TBD |
| **powerpoint** | PowerPoint-deck (.pptx) | TBD — bestaande template moet nog gedocumenteerd |
| **responsive HTML** | Web-publicatie (intranet, marketing) | TBD |
| **HTML voor [[wiki/entities/anewspring]]** | LMS-content voor cursisten | TBD — mogelijk SCORM/xAPI-vereisten |

## Rol in de pipeline

Goedgekeurde documenten uit [[wiki/entities/baakiekwal]] worden door baakieprint omgezet naar één of meer format-targets. Elke format heeft een eigen skeleton-template; de huisstijl (`baakie-orchestrator/context/organisatie/debaak-huisstijl.md`) bepaalt visuele consistentie.

## Belangrijke feiten

- Schrijft naar de registervelden: `prompt_print_document`, `prompt_html_document`, `filename_laatste_bewerking`, `outputlocatie`. — canon: `baakie-orchestrator/CLAUDE.md`
- Skeleton-aanpak: één space, meerdere format-templates (in plaats van één space per format). Operationeel uitwerken nog open. — canon: decision-log 2026-05-20

## Relaties

- Ontvangt input van: [[wiki/entities/baakiekwal]]
- Werkt onder: [[wiki/entities/de-baak]]
- Gebruikt strict de huisstijl: `baakie-orchestrator/context/organisatie/debaak-huisstijl.md`

## Open vragen

- Skeleton-bestanden voor de 5 format-targets nog niet als één coherente set georganiseerd in `baakie-orchestrator/spaces/baakieprint/knowledge/` (was tweedeling tot 2026-05-20).
- Anewspring-specifieke skeleton: SCORM / xAPI / iets simplers? Zie [[wiki/entities/anewspring]] §Open vragen.
- Hoe gaat baakieprint om met formats waar de huisstijl nog open punten heeft (logo-bestand, fotografie, CMYK)? Antwoord vermoedelijk: vragen aan de gebruiker, niet improviseren — consistent met `llm-wiki/CLAUDE.md §9`.

## Cross-references

- Genoemd in: [[wiki/sources/debaak-dm-phase1]] (impliciet via output-fasen), [[wiki/topics/baakie-pipeline]]
- Output-target: [[wiki/entities/anewspring]] (LMS voor HTML-content)
- Werkt onder canon: huisstijl-spec
