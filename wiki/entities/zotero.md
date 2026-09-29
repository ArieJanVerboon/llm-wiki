---
type: entity
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [gereedschap, bronnen, research-flow, citaties]
entity_kind: product
aliases: []
---

# Zotero

> **Citatieslug:** `[[wiki/entities/zotero]]`

## Wat is het

Bronnenbeheer: artikelen, boeken en webpagina's met hun metadata, pdf's, annotaties en citaties. Draait als programma op de computer, met een eenvoudiger webbibliotheek op zotero.org. In de [[wiki/topics/research-flow]] is dit het archief waar het onderzoek landt.

## Belangrijke feiten

Webbibliotheek waargenomen 2026-09-24, gebruiker *inspreadables*; de desktop-app is nagelezen in de documentatie, niet waargenomen — [[wiki/sources/linkermenu-reeks]] (Zotero):

- **5 bronnen**, over antifragiliteit, kennismanagement en vector databases.
- **Geen collecties.** De bronnen liggen ongesorteerd in My Library.
- Drie tags die niet met de hand gezet zijn: `dedup:topic…`, `dedup:url…` en `ingested:review`. De bron noemt een automatisering als herkomst en wijst naar de n8n-flow als vermoedelijke schrijver.
- Desktop-app staat op **versie 9**; nieuw daarin: Read Aloud, annotaties direct als citatie invoegen, en beter zicht op wie wat in een groepsbibliotheek wijzigde.
- De **Connector** in de browser legt met één klik een bron vast met metadata en pdf.
- De Word-plugin verzorgt citaties en literatuurlijst in elke stijl.
- De bron noemt twee uitgangen naar kennisbanken: pdf's exporteren naar een Gemini-notebook of Perplexity-project, en **annotaties exporteren naar markdown voor Obsidian of dit LLM Wiki**.

## Waarom de tags belangrijk zijn

`dedup:topic…` en `dedup:url…` verraden dat de automatisering op dubbelen controleert — iets wat een mens niet met de hand zo tagt. `ingested:review` suggereert een stap ná het opnemen: iets is binnengehaald en wacht op beoordeling. In deze kluis bestaat een map `review/`. Of dat hetzelfde review is, staat nergens; het is als speculatie vastgelegd in [[wiki/topics/research-flow]].

## Rol in de research-flow

Stap 4 en de laatste machinale stap. Hierna is het handwerk: niets in de reeks beschrijft een route van Zotero naar `raw/`. Zotero is daarmee het punt waar de flow stopt met stromen — en met vijf bronnen zonder collectie is het ook het punt waar de opbrengst van de hele keten meetbaar wordt.

De bron adviseert zelf collecties te maken per onderwerp of pilot, zodat wat de automatisering binnenhaalt ergens landt in plaats van op één hoop.

## Relaties

- Ontvangt van: [[wiki/entities/n8n]] (vermoedelijk *Antifragile Flow B*)
- Zou moeten leveren aan: `raw/` in dit wiki — zie [[wiki/concepts/ingest-query-lint]]
- Gelezen via: [[wiki/entities/obsidian]], na een ingest
- Onderwerp van de 5 bronnen raakt: antifragiliteit (zie ook de naam *Antifragile Flow*)

## Open vragen

- Schrijft *Antifragile Flow B* rechtstreeks in Zotero, via de API of via een andere route?
- Wat betekent `ingested:review` precies, en wie zou die review doen?
- Waarom vijf bronnen? Draait de flow zelden, of filtert hij streng?
- Zijn de vijf bronnen dezelfde als, of andere dan, wat in `raw/_seed/` staat?

## Cross-references

- Genoemd in: [[wiki/sources/linkermenu-reeks]], [[wiki/topics/research-flow]]
