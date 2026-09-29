---
type: concept
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [workflow, llm-wiki, operations]
aliases: [ingest/query/lint, wiki operations]
---

# Ingest / Query / Lint

> **Citatieslug:** `[[wiki/concepts/ingest-query-lint]]`

## Eénregelige definitie

De drie kern-operaties die een LLM op een wiki uitvoert: nieuwe bronnen verwerken (**ingest**), vragen beantwoorden (**query**), en periodiek gezondheid bewaken (**lint**).

## Uitgebreidere uitleg

**Ingest.** Een nieuwe bron wordt in `raw/` gezet en de LLM krijgt opdracht hem te verwerken. De LLM leest, bespreekt kern-takeaways met de mens, schrijft een samenvattingspagina, werkt de index bij, werkt relevante entiteit- en conceptpagina's bij, en append een entry aan het log. Eén bron raakt typisch **10–15 pagina's**. Karpathy zelf prefereert één bron tegelijk; batch-ingest is mogelijk met minder supervisie.

**Query.** De gebruiker stelt een vraag tegen het wiki. De LLM zoekt relevante pagina's, leest ze, en synthetiseert een antwoord met citaties. Antwoordvorm kan variëren — pagina, vergelijkingstabel, slidedeck (Marp), chart, canvas. **Belangrijk inzicht**: goede antwoorden moeten **terug-gearchiveerd** worden in het wiki als nieuwe pagina's, anders verdampen ze in chathistory.

**Lint.** Periodiek wordt het wiki op gezondheid gecontroleerd: contradicties tussen pagina's, verouderde claims, wees-pagina's, belangrijke concepten zonder eigen pagina, ontbrekende cross-references, dekkingshiaten die om externe bronnen vragen. De LLM is goed in het voorstellen van nieuwe vragen om te onderzoeken.

## Sleutelclaims

- Eén ingest raakt typisch **10–15 wiki-pagina's**. — [[wiki/sources/karpathy-llm-wiki]].
- Query-antwoorden die niet terug-gearchiveerd worden, verdampen in chathistory en gaan verloren. — [[wiki/sources/karpathy-llm-wiki]].
- Lint is **periodiek en bewust**, niet stilzwijgend bij elke ingest. — [[wiki/sources/karpathy-llm-wiki]].
- LLM's zijn goed in het *voorstellen* van nieuwe vragen en bronnen om naar te zoeken — een waardevol bijproduct van lint. — [[wiki/sources/karpathy-llm-wiki]].

## Voorbeelden

- Deze pagina is zelf het resultaat van de eerste ingest in dit wiki — zie [[wiki/sources/karpathy-llm-wiki]] en log-entry 2026-05-20.
- De ingest is inmiddels **de beschreven werkwijze buiten dit wiki**: de Obsidian-pagina van [[wiki/sources/linkermenu-reeks]] instrueert nieuwe bronnen in `raw/` te zetten en Claude Code een ingest te laten doen. De operatie is dus niet alleen een conventie in `CLAUDE.md` maar ook wat AV elders als proces heeft vastgelegd.
- Diezelfde bron noemt de **grafiekweergave** van [[wiki/entities/obsidian]] expliciet als aanvulling op lint: losse punten in de grafiek zijn de wees-pagina's die lint zoekt. Eén handmatige blik levert dus een deel van wat lint moet vaststellen.

## Waar de ingest in de praktijk op vastloopt

Bij de ingest van 2026-09-29 bleek de operatie op twee punten te wringen met wat er werkelijk aankomt:

- **De bron is soms een reeks, niet een bron.** Twintig pagina's met één skelet en één onderwerp-per-stuk lenen zich niet voor twintig samenvattingspagina's; dat zou twintig verouderende pagina's opleveren. Verwerkt als *één* bron met feiten over entiteiten — zie [[wiki/sources/linkermenu-reeks]].
- **De aanvoer naar `raw/` is niet geautomatiseerd.** Zie [[wiki/topics/research-flow]]: de keten stopt in het bronnenarchief, één stap vóór de ingest. De ingest is klaar om te werken, maar er wordt niets bij hem afgeleverd.

## Verwarrend te onderscheiden van

- "CRUD-operaties op een database" — verschil: ingest is geen toevoeging maar een synthese-pass over de hele wiki; lint is geen validatie maar een actieve revisie.

## Standpunten en debat

- **Triage vóór write** (uit gistcomments, theafh): elk ingest-rapport eerst tonen (nieuwe pagina's / extensies / contradicties met excerpten en reconciliatie-opties) vóór er geschreven wordt. Karpathy specificeert dit niet expliciet maar het is consistent met "stay involved". Mogelijke uitbreiding van `CLAUDE.md` als we deze flow gaan gebruiken.
- **Claim-first extraction** (uit gistcomments, Andrii via nowissan): eerst citeerbare claims extraheren, dan concepten erbovenop bouwen. Hiermee valt level (= belangrijkheid) structureel uit het aantal claims per concept. Niet in de bron, wel een interessante verfijning.

## Open vragen

- Hoe vaak is "periodiek" voor lint in de praktijk? Karpathy laat dat aan de gebruiker.
- Wanneer is een query-antwoord *waardig genoeg* om te archiveren? Heuristiek ontbreekt in de bron.

## Cross-references

- Onderdeel van: [[wiki/concepts/llm-wiki-pattern]]
- Werkt op: [[wiki/concepts/three-layer-architecture]]
- Genoemd in: [[wiki/sources/karpathy-llm-wiki]], [[wiki/sources/linkermenu-reeks]], [[wiki/topics/llm-augmented-knowledge-bases]], [[wiki/topics/research-flow]]
- Laatste stap van: [[wiki/topics/research-flow]]
