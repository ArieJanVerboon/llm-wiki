---
type: concept
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [llm, knowledge-management, pattern, pkm]
aliases: [LLM wiki, persistent LLM-maintained wiki]
---

# LLM Wiki Pattern

> **Citatieslug:** `[[wiki/concepts/llm-wiki-pattern]]`

## Eénregelige definitie

Een patroon waarbij een LLM een persoonlijk, onderling gelinkt markdown-wiki incrementeel opbouwt en onderhoudt op basis van ruwe bronnen, in plaats van bij elke vraag opnieuw uit die bronnen te synthetiseren.

## Uitgebreidere uitleg

Het LLM Wiki-patroon zit tussen pure RAG en handmatige notebooks in. Het kerninzicht: het saaie werk van een kennisbank (cross-references, consistentie, contradictiedetectie, samenvattingen actueel houden) is precies waar LLM's geschikt voor zijn en mensen niet. Door de LLM verantwoordelijk te maken voor onderhoud — en de mens voor curatie, exploratie en richting — wordt een wiki houdbaar dat anders zou verzanden.

Het wiki zelf is een **persistent, samengesteld artefact**: cross-references staan er al, contradicties zijn al gemarkeerd, samenvattingen reflecteren alle eerder gelezen bronnen. Bij elke nieuwe bron of vraag wordt het rijker — niet steeds vanaf nul opnieuw afgeleid.

Karpathy benadrukt dat het patroon **abstract en modulair** is. Mapindeling, schemaconventies, paginaformaten en tooling moeten met de eigen LLM uitgewerkt worden op basis van het domein. Wat blijft: drie lagen (raw / wiki / schema), drie operaties (ingest / query / lint), en de strikte rolverdeling mens-versus-LLM.

## Sleutelclaims

- Kennis wordt **één keer gecompileerd** en daarna actueel gehouden — niet bij elke query opnieuw afgeleid. — [[wiki/sources/karpathy-llm-wiki]].
- De wiki is een **compounding artifact**: het wordt rijker met elke bron en elke vraag. — [[wiki/sources/karpathy-llm-wiki]].
- Goede antwoorden op vragen horen **terug-gearchiveerd** te worden in het wiki, anders verdampen ze in chathistory. — [[wiki/sources/karpathy-llm-wiki]].
- Werkt verrassend goed op **moderate schaal** (~100 bronnen, honderden pagina's) zonder embedding-gebaseerde RAG-infrastructuur — een `index.md` volstaat. — [[wiki/sources/karpathy-llm-wiki]].

## Voorbeelden van toepassing

- **Persoonlijk**: doelen, gezondheid, psychologie, zelfontwikkeling — journaalentries, artikels, podcastnotities. — [[wiki/sources/karpathy-llm-wiki]].
- **Onderzoek**: weken/maanden lang papers, artikels en rapporten verwerken tot een synthese met evoluerende these. — [[wiki/sources/karpathy-llm-wiki]].
- **Boek-companion**: pagina's per hoofdstuk, karakter, thema, plotlijn — eindigend met een rijk wiki vergelijkbaar met fan-wiki's zoals Tolkien Gateway. — [[wiki/sources/karpathy-llm-wiki]].
- **Team-wiki**: gevoed door Slack, transcripten, customer calls — onderhoud dat niemand op het team wil doen wordt door de LLM gedragen. — [[wiki/sources/karpathy-llm-wiki]].
- **Concurrentie-analyse, due diligence, reisplanning, cursusnotities, hobby-deepdives** — alles met accumulerende kennis. — [[wiki/sources/karpathy-llm-wiki]].

## Verwarrend te onderscheiden van

- [[wiki/concepts/rag]] — verschil: RAG is stateless en query-driven; LLM Wiki is stateful en ingest-driven.
- "Notitie-app" (Notion, Roam, Logseq) — verschil: in een notitie-app schrijft de mens; in een LLM Wiki schrijft de LLM, de mens cureert en leest.
- "Embedding-gebaseerd second brain" — verschil: gebruikt vector-retrieval over ruwe bronnen; LLM Wiki gebruikt LLM-geschreven samenvattingen en `index.md`-driven navigatie.

## Standpunten en debat

- Karpathy stelt dat het patroon **domein-agnostisch** is. Communityreacties (in de gistcomments) wijzen op drie consistente failure modes bij praktische implementatie: *identity* (duplicate concepten), *level* (life-themes vermengd met tactische findings) en *getypeerde relaties* (alle linktypes platgeslagen). De bron zelf adresseert deze niet.

## Open vragen

- Wat is de juiste schaal-grens waarboven enkel `index.md`-navigatie niet meer volstaat en aanvullende infrastructuur (bv. BM25/vector-zoek) nodig wordt?
- Moeten relaties tussen pagina's getypeerd worden (`similar`, `contains`, `contradicts`) in plaats van als generieke `[[link]]`, en met welke kosten?
- Hoe voorkom je *identity drift* (hetzelfde concept onder twee net verschillende namen)?

## Cross-references

- Hoofdbron: [[wiki/sources/karpathy-llm-wiki]]
- Voorouder: [[wiki/concepts/memex]]
- Contrast: [[wiki/concepts/rag]]
- Gerelateerd: [[wiki/concepts/three-layer-architecture]], [[wiki/concepts/ingest-query-lint]]
- Auteur: [[wiki/entities/karpathy]]
- Beheert dit wiki: [[wiki/topics/llm-augmented-knowledge-bases]]
