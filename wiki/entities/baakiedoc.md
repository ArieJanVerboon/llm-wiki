---
type: entity
created: 2026-05-20
updated: 2026-09-29
sources: 3
tags: [agent, baakie-pipeline, documentmanagement, taxonomie]
entity_kind: agent
aliases: []
---

# baakiedoc

> **Citatieslug:** `[[wiki/entities/baakiedoc]]`

## Wat is het

Eerste schakel in de [[wiki/topics/baakie-pipeline]]. LLM-subagent verantwoordelijk voor **documentmanagement**: inventarisatie, taxonomie, bestandsnaamgeving en het bibliotheek-register. Bron-canon: `baakie-orchestrator/CLAUDE.md` tabel *Beschikbare subagents*.

## Rol in de pipeline

Inkomende bronnen (ruw materiaal van trainingen, herzieningen, hergebruik) krijgen via baakiedoc een gestandaardiseerde bestandsnaam volgens de [[wiki/concepts/naamgevingsconventie]] en een rij in het register. Daarna gaat het door naar [[wiki/entities/baakiekwal]] voor assessment of direct naar [[wiki/entities/baakieprint]] voor publicatie.

## Belangrijke feiten

- Schrijft naar de registervelden: `filename_taxonomy`, taxonomiekolommen, `mutatierapport`. — canon: `baakie-orchestrator/CLAUDE.md`
- Werkt met SharePoint-flow archief → werkmap → Excel-register → contentbibliotheek (zie [[wiki/concepts/sharepoint-contentflow]]). — [[wiki/sources/documentbeheer-infographic]]
- Fase 1 van het invoeringsproces (de Fase-1-bron) heeft drie stappen: inventarisatie, naamgevingsconventie definiëren, migratie + lancering. — [[wiki/sources/debaak-dm-phase1]]
- **Bouwt op de Perplexity-API.** De API-changelog van [[wiki/entities/perplexity]] wordt genoemd als de plek waar je wijzigingen volgt *"voor wie op de API bouwt, zoals Baakiedoc"*. Daarmee is baakiedoc niet alleen een rol maar een draaiende koppeling, met een externe afhankelijkheid die kan breken. — [[wiki/sources/linkermenu-reeks]] (Perplexity, 2026-09-24)
- In Perplexity staat een organisatieproject **Baakdociereserach** (naam zoals aangetroffen). Of dat bij deze agent hoort of bij een aparte onderzoekslijn, zegt de bron niet. — [[wiki/sources/linkermenu-reeks]] (Perplexity)

## Relaties

- Levert input aan: [[wiki/entities/baakiekwal]], [[wiki/entities/baakieprint]]
- Werkt onder: [[wiki/entities/de-baak]]
- Hanteert: [[wiki/concepts/naamgevingsconventie]], [[wiki/concepts/sharepoint-contentflow]]

## Open vragen

- Welke Perplexity-API gebruikt baakiedoc, met welke sleutel, en wie merkt het als die API verandert? De changelog volgen is een menselijke taak zolang er geen check op staat.
- Is *Baakdociereserach* hetzelfde werk als deze agent, of een losse onderzoeksmap die er alleen op lijkt?
- Verhouding tot orchestrator: orchestrator wijzigt *de conventie zelf*, baakiedoc *executeert* de conventie. Boundary gedocumenteerd in decision-log 2026-05-09 maar nog niet in dit wiki uitgewerkt.
- Hoe gaat baakiedoc om met hergebruikte assets (B1-conventie: één bestand, meerdere registerrijen)? Genoemd in orchestrator-log, niet in de bronnen van dit wiki.

## Cross-references

- Genoemd in: [[wiki/sources/debaak-dm-phase1]], [[wiki/sources/documentbeheer-infographic]], [[wiki/sources/linkermenu-reeks]], [[wiki/topics/baakie-pipeline]]
- Bouwt op: [[wiki/entities/perplexity]]
- Werkt op: [[wiki/concepts/naamgevingsconventie]], [[wiki/concepts/sharepoint-contentflow]]
