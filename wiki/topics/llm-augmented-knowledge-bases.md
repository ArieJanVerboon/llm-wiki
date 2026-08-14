---
type: topic
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [llm, knowledge-management, pkm, meta]
thesis_status: opening
---

# LLM-augmented kennisbanken

> **Citatieslug:** `[[wiki/topics/llm-augmented-knowledge-bases]]`

Dit topic vat samen wat dit wiki uit zijn bronnen leert over **hoe je een persoonlijke of teamkennisbank effectief door een LLM laat onderhouden**. Dit is de meta-laag: de wiki gaat (voorlopig) deels over zichzelf.

## Huidige these

De combinatie van een immutabele bronnenlaag, een door de LLM volledig beheerde wiki-laag, en een expliciet schema dat conventies vastlegt, levert een persoonlijke kennisbank op die — anders dan zowel klassieke RAG als handmatige notitie-apps — daadwerkelijk *accumuleert*. De LLM neemt het bookkeeping over dat menselijke wiki's typisch laat verzanden; de mens richt zich op curatie van bronnen en het stellen van de juiste vragen.

_Stand per 2026-05-20 — gebaseerd op één bron ([[wiki/sources/karpathy-llm-wiki]])._

## Wat we weten

- Het patroon scheidt drie lagen (raw / wiki / schema) met strikte eigenaarschap. — [[wiki/sources/karpathy-llm-wiki]] via [[wiki/concepts/three-layer-architecture]].
- Drie operaties dragen de workflow: ingest, query, lint. — [[wiki/sources/karpathy-llm-wiki]] via [[wiki/concepts/ingest-query-lint]].
- Op moderate schaal (~100 bronnen, honderden pagina's) volstaat een `index.md` voor navigatie; geen embeddings vereist. — [[wiki/sources/karpathy-llm-wiki]].
- Goede query-antwoorden moeten terug-gearchiveerd worden of ze verdampen. — [[wiki/sources/karpathy-llm-wiki]].
- Het patroon is geestverwant aan Vannevar Bush's Memex en lost diens onderhoudsvraag op. — [[wiki/sources/karpathy-llm-wiki]] via [[wiki/concepts/memex]].

## Wat we vermoeden

> speculatie: getypeerde relaties tussen pagina's (`similar`, `contains`, `contradicts`) en een onderscheid in *level* (life-themes vs tactische findings) worden waarschijnlijk nodig zodra dit wiki voorbij enkele tientallen pagina's groeit. Bronnen die dit bevestigen of weerleggen staan nog op de leeslijst.

> speculatie: *claim-first extraction* (eerst citeerbare claims, dan concepten erbovenop) is mogelijk een effectievere ingest-strategie dan concept-first. Niet in de hoofdbron, wel in communityreacties geopperd. Verdient empirische toetsing.

## Wat omstreden is

- Geen interne contradicties yet — er is pas één bron.
- Mogelijke spanning tussen Karpathy's "houd het simpel, index.md volstaat" en latere noodzaak van zwaardere zoekinfrastructuur (zoals qmd of BM25/vector). Niet opgelost; afhankelijk van schaal.

## Belangrijkste entiteiten

- [[wiki/entities/karpathy]] — auteur van het patroon
- [[wiki/entities/vannevar-bush]] — geestelijke voorouder via Memex

## Belangrijkste concepten

- [[wiki/concepts/llm-wiki-pattern]] — het centrale concept
- [[wiki/concepts/three-layer-architecture]] — structuur
- [[wiki/concepts/ingest-query-lint]] — operaties
- [[wiki/concepts/rag]] — primair contrast
- [[wiki/concepts/memex]] — historische voorouder

## Evolutie van de these

- 2026-05-20 — these geopend op basis van [[wiki/sources/karpathy-llm-wiki]].

## Open vragen

- Op welke schaal vervalt de "index.md volstaat"-heuristiek?
- Hoe ga je om met *identity drift* (zelfde concept onder verschillende namen) zonder zware infrastructuur?
- Welke linktypes verdienen typering en welke kunnen generiek blijven?
- Werkt het patroon ook voor multi-user / teamkennisbanken, of breekt het op coördinatie?

## Cross-references

- Verwante onderwerpen: nog geen — dit is het eerste topic.
- Bronnen die dit onderwerp raken: [[wiki/sources/karpathy-llm-wiki]] (1/1).
