---
type: source
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [llm, knowledge-management, obsidian, pkm, wiki, pattern]
source_path: raw/_seed/karpathy-llm-wiki.md
source_url: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
source_kind: article
source_date: 2026-04
authors: [Andrej Karpathy]
---

# Karpathy — LLM Wiki

> **Citatieslug:** `[[wiki/sources/karpathy-llm-wiki]]`

## Kern in één zin

Een patroon waarbij een LLM een persoonlijk wiki van markdown-bestanden incrementeel onderhoudt in plaats van bij elke vraag opnieuw uit ruwe bronnen te synthetiseren — zodat kennis accumuleert in plaats van telkens opnieuw afgeleid te worden.

## Samenvatting

Karpathy beschrijft een alternatief voor klassieke RAG. Het probleem met RAG: bij elke vraag herontdekt de LLM verbanden tussen bronnen vanaf nul, zonder dat er iets opgebouwd wordt. Subtiele vragen die synthese over vijf documenten vereisen, herhalen telkens dezelfde puzzel.

Het alternatief is een **persistent, samengesteld artefact** — een wiki van onderling gelinkte markdown-pagina's die tussen de gebruiker en de ruwe bronnen zit. Wanneer een nieuwe bron wordt toegevoegd, leest de LLM hem, extraheert kerninformatie, en integreert die in het bestaande wiki: entiteitpagina's worden bijgewerkt, topic-samenvattingen herzien, contradicties met oudere claims gemarkeerd. De kennis wordt **één keer gecompileerd en daarna actueel gehouden**.

De rolverdeling is strikt: de mens cureert bronnen, exploreert en stelt de juiste vragen. De LLM doet al het bookkeeping — samenvatten, cross-references onderhouden, archiveren. Karpathy gebruikt Obsidian aan één kant van het scherm en de LLM-agent aan de andere; "Obsidian is de IDE, de LLM is de programmeur, de wiki is de codebase."

Het patroon kent drie lagen: ruwe bronnen (immutabel), het wiki (volledig door de LLM beheerd), en het schema (een configuratiebestand zoals `CLAUDE.md` of `AGENTS.md` dat conventies en workflows vastlegt). Drie operaties: **ingest** (nieuwe bron verwerken en geraakte pagina's bijwerken — typisch 10–15 pagina's per bron), **query** (vragen aan het wiki, met optie om waardevolle antwoorden terug te archiveren als nieuwe pagina's), en **lint** (periodieke health-check op contradicties, verouderde claims, wees-pagina's, ontbrekende cross-references).

Twee navigatiebestanden helpen schaalbaarheid: `index.md` (inhoudsgerichte catalogus, bijgewerkt bij elke ingest) en `log.md` (chronologisch append-only logboek met parseerbare prefixen).

Waarom het werkt: het saaie deel van een kennisbank is niet het lezen of nadenken, maar het bookkeeping. Mensen verlaten wiki's omdat de onderhoudslast sneller groeit dan de waarde. LLM's vervelen niet, vergeten geen cross-reference, en raken in één pass 15 bestanden aan. Onderhoud wordt vrijwel gratis.

Het idee is verwant aan Vannevar Bush's Memex (1945) — een persoonlijke, gecureerde kennisbank met associatieve trails tussen documenten. Bush kon niet oplossen wie het onderhoud zou doen; de LLM beantwoordt die vraag.

Het document is **bewust abstract**. Het beschrijft het patroon, niet een specifieke implementatie. Mapindeling, schemaconventies, paginaformaten en tooling zijn afhankelijk van het domein van de gebruiker, en moeten in samenwerking met de LLM worden uitgewerkt.

## Kernpunten

- RAG = stateless; deze wiki-aanpak = stateful en cumulatief.
- Drie lagen: raw / wiki / schema. Strikte scheiding, raw is immutabel.
- Drie operaties: ingest / query / lint. Ingest raakt typisch 10–15 pagina's per bron.
- Indexing via `index.md` (inhoud) en `log.md` (chronologie) volstaat op moderate schaal (~100 bronnen, honderden pagina's) — geen embeddings nodig.
- Goede query-antwoorden horen terug-gearchiveerd te worden in het wiki. Anders verdampen ze in chathistory.
- Lint is **periodiek en bewust** — niet stilzwijgend. De LLM rapporteert, de mens beslist.
- Mens cureert; LLM doet al het andere.
- Domein-agnostisch: persoonlijk, onderzoek, boek-companion, team-wiki, due-diligence, hobby.

## Entiteiten genoemd

- [[wiki/entities/karpathy]] — auteur; introduceert het patroon en demonstreert de workflow met Obsidian + Claude Code.
- [[wiki/entities/vannevar-bush]] — historische verwijzing; Memex (1945) als geestelijke voorganger.
- Obsidian — IDE-laag; concrete tool maar geen aparte entiteitpagina (gereedschap, geen subject).
- qmd — lokaal zoek-CLI voor markdown; optionele uitbreiding, geen aparte pagina nodig nu.
- Tolkien Gateway — voorbeeld van een grootschalig fan-wiki; illustratief, geen aparte pagina nodig nu.

## Concepten genoemd

- [[wiki/concepts/llm-wiki-pattern]] — hét centrale concept van deze bron.
- [[wiki/concepts/rag]] — wordt expliciet gecontrasteerd met de wiki-aanpak.
- [[wiki/concepts/three-layer-architecture]] — raw / wiki / schema scheiding.
- [[wiki/concepts/ingest-query-lint]] — de drie kern-operaties.
- [[wiki/concepts/memex]] — Bush's voorstel uit 1945; geestelijke voorganger.

## Citaten waard

> "The wiki is a persistent, compounding artifact."
> — Karpathy, sectie *Core idea*

> "Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase."
> — Karpathy, sectie *Core idea*

> "The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping."
> — Karpathy, sectie *Why this works*

> "The human's job is to curate sources, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else."
> — Karpathy, sectie *Why this works*

## Verbindingen met de bestaande wiki

- Funderend: definieert het hele patroon waarop dit wiki gebaseerd is. Verwacht dat veel toekomstige pagina's hierheen verwijzen via [[wiki/concepts/llm-wiki-pattern]].
- Geen tegenstrijdigheden — dit is de eerste bron.
- Open vragen die de bron zelf oproept en die toekomstige bronnen kunnen vullen:
  - Hoe schaalt het patroon voorbij ~100 bronnen waar enkel `index.md` niet meer volstaat?
  - Hoe ga je om met *identity* (duplicate concepten onder net andere namen), *level* (life-themes vermengd met tactische findings) en *getypeerde relaties*? (Issues die in de comments op de gist door communityleden zijn opgebracht — niet in de bron zelf opgelost.)
  - Wat is de juiste granulariteit van een entiteit- vs concept-pagina?

## Mijn aantekeningen

_(Plek voor Arij Jan om opmerkingen toe te voegen. De LLM laat dit blok ongemoeid bij toekomstige updates.)_

## Provenance

- Bestand: `raw/_seed/karpathy-llm-wiki.md`
- Origineel: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- Opgehaald op: 2026-05-20 via `curl` raw-URL
- Hash (sha256): `dc3efe98ae62f23dd08acad13aba2e95287beb20b6bec2f4af0423557fe37401`
