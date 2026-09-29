---
type: concept
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [architecture, llm-wiki, pattern]
aliases: [raw/wiki/schema, three layers]
---

# Drie-lagen-architectuur (raw / wiki / schema)

> **Citatieslug:** `[[wiki/concepts/three-layer-architecture]]`

## Eénregelige definitie

Het LLM Wiki-patroon scheidt drie lagen met verschillende eigenaren: ruwe bronnen (mens, immutabel), het wiki (LLM, volledig beheerd), en het schema (mens + LLM samen, configuratie).

## Uitgebreidere uitleg

De drie lagen zijn:

1. **Raw sources** — Artikels, papers, afbeeldingen, datafiles. De mens cureert; de LLM leest maar **schrijft hier nooit in**. Dit is de bron van waarheid waarop alle wiki-claims uiteindelijk teruggrijpen.

2. **Het wiki** — Een directory met door de LLM gegenereerde markdown-bestanden: samenvattingen, entiteitpagina's, conceptpagina's, vergelijkingen, een overview. De LLM bezit deze laag volledig: maakt pagina's, werkt ze bij wanneer nieuwe bronnen aankomen, onderhoudt cross-references, houdt consistentie. De mens leest; de LLM schrijft.

3. **Het schema** — Een configuratiedocument (`CLAUDE.md` voor Claude Code, `AGENTS.md` voor Codex) dat de LLM vertelt hoe het wiki gestructureerd is, welke conventies gelden, en welke workflows te volgen tijdens ingest, query en lint. Dit maakt de LLM een gedisciplineerde wiki-beheerder in plaats van een algemene chatbot. Het schema **co-evolueert** met de gebruiker.

De scheiding is strikt: de LLM bewerkt nooit `raw/`. De mens bewerkt zelden `wiki/`. Schema-wijzigingen zijn bewust en expliciet gelogd.

## Sleutelclaims

- Raw sources zijn **immutabel** — de LLM mag ze nooit muteren. — [[wiki/sources/karpathy-llm-wiki]].
- Het wiki is **volledig eigendom van de LLM** — de mens leest, de LLM schrijft. — [[wiki/sources/karpathy-llm-wiki]].
- Het schema is **het sleutelconfiguratiebestand** — wat een LLM in een gedisciplineerde wiki-beheerder verandert in plaats van een chatbot. — [[wiki/sources/karpathy-llm-wiki]].

## Voorbeelden

- In dit wiki: `raw/` bevat de gist en eventuele toekomstige bronnen; `wiki/` bevat alle door de LLM gegenereerde pagina's (waaronder deze); `CLAUDE.md` is het schemabestand. — [[wiki/sources/karpathy-llm-wiki]].
- De drie lagen zijn ook **letterlijk zichtbaar** in de kluisboom van [[wiki/entities/obsidian]]: `raw/`, `wiki/` en `CLAUDE` staan naast elkaar in de bestandsverkenner. Wie de kluis opent, ziet de architectuur voordat hij een pagina leest. — [[wiki/sources/linkermenu-reeks]] (Obsidian).

## De grens van `raw/` in de praktijk

`raw/` is het **aanlandpunt** van alles wat van buiten komt, en dat maakt de laag kwetsbaar op een manier die de definitie niet laat zien: er is geen mechanisme dat bronnen *naar* `raw/` brengt. In [[wiki/topics/research-flow]] loopt een geautomatiseerde keten tot in het bronnenarchief en stopt daar; de laatste stap naar `raw/` is handwerk. De immutabiliteit van de laag is dus goed geregeld, het vullen ervan niet.

Twee gevolgen die in deze wiki zijn vastgesteld:

- Bronnen die buiten de repo staan zijn geen bronnen. De twintig pagina's van [[wiki/sources/linkermenu-reeks]] bestonden twee maanden alleen als gepubliceerde artifacts op claude.ai — buiten git, buiten back-up — tot ze op 2026-09-29 naar `raw/` zijn gehaald.
- `raw/` is immutabel, dus een fout in een bron wordt niet gerepareerd maar **gecorrigeerd in de wiki-laag**. Voorbeeld: het onjuiste kluispad in [[wiki/entities/obsidian]].

## Verwarrend te onderscheiden van

- "Documentatie-stack" (bron → render → publicatie) — verschil: in de drie-lagen-architectuur is de wiki-laag *geen render* maar een eigenstandig, door LLM bijgewerkt artefact dat synthese toevoegt.

## Open vragen

- Wat gebeurt er als de mens *wel* in een wiki-pagina wil schrijven (eigen aantekeningen)? De templates in dit wiki lossen dit op met een afgebakend "Mijn aantekeningen"-blok dat de LLM niet overschrijft — maar Karpathy specificeert het niet expliciet.

## Cross-references

- Onderdeel van: [[wiki/concepts/llm-wiki-pattern]]
- Operationaliseert: [[wiki/concepts/ingest-query-lint]]
- Genoemd in: [[wiki/sources/karpathy-llm-wiki]], [[wiki/sources/linkermenu-reeks]], [[wiki/topics/llm-augmented-knowledge-bases]], [[wiki/topics/research-flow]]
- Zichtbaar gemaakt door: [[wiki/entities/obsidian]]
