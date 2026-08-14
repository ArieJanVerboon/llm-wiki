---
type: concept
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [llm, retrieval, ai]
aliases: [Retrieval-Augmented Generation, retrieval-augmented generation]
---

# RAG (Retrieval-Augmented Generation)

> **Citatieslug:** `[[wiki/concepts/rag]]`

## Eénregelige definitie

Een patroon waarbij een LLM bij elke vraag relevante stukken uit een verzameling ruwe documenten ophaalt en op basis daarvan een antwoord genereert.

## Uitgebreidere uitleg

In een RAG-systeem upload je een collectie documenten; bij elke query haalt het systeem (meestal via vector-embeddings) de meest relevante fragmenten op, en de LLM genereert een antwoord op basis daarvan. Bekende voorbeelden: NotebookLM, ChatGPT file uploads, de meeste "chat-with-your-docs"-producten.

Het systeem werkt, maar is fundamenteel **stateless**: de LLM herontdekt verbanden tussen bronnen bij elke vraag opnieuw. Subtiele vragen die synthese over vijf documenten vereisen, herhalen telkens dezelfde puzzel. Er accumuleert niets.

Dit is het primaire contrast dat Karpathy aanbrengt om het [[wiki/concepts/llm-wiki-pattern]] te motiveren.

## Sleutelclaims

- RAG is stateless: niets wordt opgebouwd tussen queries. — [[wiki/sources/karpathy-llm-wiki]].
- Bij subtiele synthese-vragen moet de LLM elke keer fragmenten zoeken en samenrijgen — er is geen cumulatieve baat. — [[wiki/sources/karpathy-llm-wiki]].
- NotebookLM, ChatGPT file uploads en de meeste RAG-systemen werken volgens dit patroon. — [[wiki/sources/karpathy-llm-wiki]].

## Verwarrend te onderscheiden van

- [[wiki/concepts/llm-wiki-pattern]] — verschil: LLM Wiki bouwt en onderhoudt een persistent artefact tussen mens en bronnen; RAG haalt rechtstreeks uit ruwe bronnen bij query-tijd.

## Standpunten en debat

- Karpathy bekritiseert RAG niet op correctheid (het werkt), maar op **non-accumulatie**: er groeit geen kennisbasis.
- Een hybride is mogelijk: het wiki-patroon zelf kan in de toekomst eventueel BM25/vector-zoek over zijn pagina's gebruiken naarmate het schaalt — dat is RAG-over-LLM-Wiki, niet RAG-over-ruwe-bronnen.

## Open vragen

- Op welke schaal of voor welk type vraag is RAG-over-ruwe-bronnen *beter* dan een LLM-onderhouden wiki? Karpathy adresseert de tegenkant niet expliciet.

## Cross-references

- Contrast: [[wiki/concepts/llm-wiki-pattern]]
- Genoemd in: [[wiki/sources/karpathy-llm-wiki]], [[wiki/topics/llm-augmented-knowledge-bases]]
