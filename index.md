# Index

Catalogus van alle wiki-pagina's. Bijgewerkt door de LLM bij elke ingest en bij elke nieuwe pagina. Zie `CLAUDE.md` § 4 voor conventies.

---

## Overview

_(nog leeg — `wiki/overview.md` wordt aangemaakt zodra er meerdere topics zijn om te synthetiseren)_

## Topics

- [[wiki/topics/baakie-pipeline]] — 2026-05-20 — Architectuur en werking van De Baak's document-managementpijplijn: drie agenten (baakiedoc → baakiekwal → baakieprint) rond een centraal Excel-register en single-source-of-truth contentbibliotheek. *(3 bronnen — thesis_status: opening)*
- [[wiki/topics/llm-augmented-knowledge-bases]] — 2026-05-20 — Meta-topic over hoe je een persoonlijke kennisbank effectief door een LLM laat onderhouden. *(1 bron — thesis_status: opening)*

## Entities

- [[wiki/entities/anewspring]] — 2026-05-20 — Learning Management System van De Baak; output-target voor HTML-content uit baakieprint. *(0 bronnen — type: product)*
- [[wiki/entities/baakiedoc]] — 2026-05-20 — Eerste schakel Baakie-pipeline: documentmanagement, taxonomie, naamgeving, register. *(2 bronnen — type: agent)*
- [[wiki/entities/baakiekwal]] — 2026-05-20 — Tweede schakel Baakie-pipeline: assessment op auteursrecht, bronvermelding, wetenschappelijke kwaliteit. *(1 bron — type: agent)*
- [[wiki/entities/baakieprint]] — 2026-05-20 — Derde schakel Baakie-pipeline: publicatie-output in 5 formats (doc/pdf/pptx/responsive-HTML/Anewspring) op basis van skeletons. *(1 bron — type: agent)*
- [[wiki/entities/de-baak]] — 2026-05-20 — Nederlandse organisatie voor training, ontwikkeling en leiderschap sinds 1947; opdrachtgever van de Baakie-pipeline. *(2 bronnen — type: organization)*
- [[wiki/entities/karpathy]] — 2026-05-20 — Andrej Karpathy: AI-onderzoeker/educator, auteur van het LLM Wiki-patroon. *(1 bron — type: person)*
- [[wiki/entities/vannevar-bush]] — 2026-05-20 — Vannevar Bush: ingenieur (1890–1974), bedacht de Memex in *As We May Think* (1945). *(1 bron — type: person)*

## Concepts

- [[wiki/concepts/auteursrecht-wetenschappelijk-werk]] — 2026-05-20 — Drie criteria + werkgeversauteursrecht + Taverne-amendement + AI-implicaties; eerste assessment-criterium van baakiekwal. *(1 bron)*
- [[wiki/concepts/baakiekwal-werkwijze]] — 2026-05-20 — Brug-pagina naar operationele canon in `baakie-orchestrator/spaces/baakiekwal/` (CRAFT-rubrieken, kwaliteitscriteria, voorbeeldrapporten). *(canon-bridge — 0 bronnen)*
- [[wiki/concepts/bronvermelding]] — 2026-05-20 — Tweede assessment-criterium van baakiekwal. *(placeholder — 0 bronnen)*
- [[wiki/concepts/ingest-query-lint]] — 2026-05-20 — De drie kern-operaties op een LLM Wiki: nieuwe bronnen verwerken, vragen beantwoorden, periodiek health-checken. *(1 bron)*
- [[wiki/concepts/llm-wiki-pattern]] — 2026-05-20 — Centraal concept: LLM bouwt incrementeel een persistent markdown-wiki uit ruwe bronnen in plaats van bij elke vraag opnieuw te synthetiseren. *(1 bron)*
- [[wiki/concepts/memex]] — 2026-05-20 — Vannevar Bush's hypothetische persoonlijke kennisapparaat (1945) — geestelijke voorouder van het LLM Wiki-patroon. *(1 bron)*
- [[wiki/concepts/naamgevingsconventie]] — 2026-05-20 — Bestandsnaamconventie voor De Baak-trainingscontent met patroon `<afk>-<id>_<functie-activiteit>-<onderwerp>_<modulepositie>.<ext>`. *(1 bron)*
- [[wiki/concepts/rag]] — 2026-05-20 — Retrieval-Augmented Generation: stateless query-driven retrieval over ruwe bronnen; primair contrast met LLM Wiki. *(1 bron)*
- [[wiki/concepts/sharepoint-contentflow]] — 2026-05-20 — Zes-stappen SharePoint-flow: archief → werkmap → Excel-register → klaarzetten → contentbibliotheek → werkinstructies. *(1 bron)*
- [[wiki/concepts/three-layer-architecture]] — 2026-05-20 — Raw / wiki / schema scheiding met strikte eigenaarschap per laag (Karpathy). *(1 bron)*
- [[wiki/concepts/wetenschappelijke-kwaliteit]] — 2026-05-20 — Derde assessment-criterium van baakiekwal. *(placeholder — 0 bronnen)*

## Sources

- [[wiki/sources/karpathy-llm-wiki]] — 2026-05-20 — Karpathy's gist *LLM Wiki* (april 2026): patroon voor LLM-onderhouden persoonlijke kennisbanken. *(gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)*
- [[wiki/sources/debaak-dm-phase1]] — 2026-05-20 — De Baak Document Management Proces Fase 1: 8 weken, 3 stappen, naamgevingsconventie incl. voorbeeld `PA-161_ho-in-ijsberg_m1p2.docx`. *(intern De Baak, in officiële huisstijl)*
- [[wiki/sources/documentbeheer-infographic]] — 2026-05-20 — Infographic SharePoint-contentflow: 6 stappen archief → werkmap → Excel-register → klaarzetten → bibliotheek → werkinstructies. *(intern De Baak)*
- [[wiki/sources/auteursrecht-wetenschappelijk-werk]] — 2026-05-20 — Auteursrecht op wetenschappelijk werk: drie criteria, werkgeversauteursrecht, Taverne-amendement, AI-implicaties. *(ariejanverboon.github.io/baak/auteursrecht/)*

## Comparisons

_(nog leeg)_

---

## Hoe deze index te lezen

- Elke entry: `- [[pagina]] — JJJJ-MM-DD — eenregelige samenvatting. (optioneel: bron of metadata)`
- Sorteer binnen elke sectie alfabetisch op pagina-slug, tenzij een andere ordening expliciet zinvol is (bijv. chronologie voor Sources).
- Pagina's met `type: comparison` in hun frontmatter horen onder **Comparisons**, ongeacht waar ze fysiek staan.
- Placeholderpagina's (0 bronnen) blijven vermeld zodat het cross-referencer-netwerk volledig is.
