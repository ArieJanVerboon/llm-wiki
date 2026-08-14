---
type: entity
created: 2026-05-20
updated: 2026-05-20
sources: 0
tags: [lms, anewspring, publicatie, baakieprint]
entity_kind: product
aliases: [aNewSpring, anewspring]
---

# Anewspring

> **Citatieslug:** `[[wiki/entities/anewspring]]`

## Wat is het

Het Learning Management System (LMS) van De Baak. Eén van de publicatie-targets in de [[wiki/topics/baakie-pipeline]] voor HTML-content: door [[wiki/entities/baakieprint]] geproduceerde HTML-deliverables komen hier terecht voor cursisten.

## Rol in de pipeline

Anewspring is een **output-bestemming**, geen processtap. Wanneer [[wiki/entities/baakieprint]] HTML-content publiceert die voor cursistgebruik bedoeld is, gaat die naar Anewspring in plaats van een statische bibliotheek. Andere HTML (intranet, marketing-pagina's) gaat naar andere bestemmingen.

## Belangrijke feiten

- Anewspring is een externe SaaS-LMS, geen interne tooling — De Baak gebruikt het maar bouwt het niet. *(Geen bron in dit wiki — feit op basis van gesprek met AV, 2026-05-20.)*
- Eén van vijf publicatie-formats die baakieprint kan opleveren — naast doc, pdf, powerpoint en responsive HTML. *(Bron: gesprek AV.)*

## Relaties

- Ontvangt content van: [[wiki/entities/baakieprint]]
- Gebruikt door: [[wiki/entities/de-baak]] cursisten

## Open vragen

- Heeft Anewspring eigen formaat-vereisten of moet baakieprint aan SCORM / xAPI / specifieke template-vorm voldoen?
- Welke skeleton in baakieprint correspondeert met Anewspring-output?
- Versiebeheer: wat gebeurt er met een Anewspring-publicatie wanneer de bronfile in de contentbibliotheek wijzigt — automatische sync of handmatige re-publish?
- URL-registratie: krijgen Anewspring-publicaties ook een URL in het Excel-register zoals beschreven in [[wiki/concepts/sharepoint-contentflow]]?

## Cross-references

- Genoemd in: [[wiki/topics/baakie-pipeline]], [[wiki/entities/baakieprint]]
- Geen bronpagina in `wiki/sources/` yet — toevoegen zodra een externe bron (Anewspring-documentatie, integratiebeschrijving) wordt ingest.
