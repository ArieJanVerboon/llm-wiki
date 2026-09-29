---
type: source
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [orientatie, gereedschap, interface, provenance, linkermenu]
source_path: raw/linkermenu/<slug>/index.html
source_url: 20 gepubliceerde artifacts op claude.ai, op 2026-09-29 naar raw/ gehaald
source_kind: other
source_date: 2026-09-24 (17 pagina's) en 2026-09-28 (3 pagina's)
authors: [Claude (in sessies van AV), waarnemingen uit AV's eigen accounts]
---

# De linkermenu-reeks — 20 oriëntatiepagina's

> **Citatieslug:** `[[wiki/sources/linkermenu-reeks]]` — gebruik deze in andere pagina's wanneer je deze reeks citeert. Verwijs waar mogelijk naar de specifieke pagina, bijvoorbeeld *linkermenu-reeks (n8n)*.

## Kern in één zin

Twintig pagina's die elk het linkermenu van één gereedschap beschrijven zoals het er op één dag in AV's eigen account uitzag — klikkaarten met een houdbaarheidsdatum, waarin en passant zo'n vijftien harde feiten over de eigen omgeving staan.

## Samenvatting

De reeks is één deliverable in twintig delen, met een vast skelet: (1) een hero met wat het gereedschap is plus *"Nagelopen op \<datum\> in jouw account X"*, (2) een schets van de zijbalk in zones A–D, (3) kaarten per menu-item volgens *Wat je vindt* / *Gebruik het voor*, soms met een **Bij jou**-regel, (4) een wanneer→waar-lijst onder *"Waar zet je het voor in?"*, (5) changelog- en release-notes-links onder *"Waar zie je wat er nieuw is?"*, en (6) een voetnoot met de datum en de waarschuwing dat menu's vaak veranderen. Alles in De Baak-huisstijl.

Het onderwerp van elke pagina is dus niet een vakgebied maar **de interface van één gereedschap op één moment**. Dat maakt de reeks als geheel inhoudelijk incoherent: het enige dat twintig zijbalken delen is dat het zijbalken zijn. Eén uitzondering: Claude, Perplexity, Gemini, DeepSeek en ChatGPT vormen een expliciete subreeks ("het derde overzicht in de reeks") met vergelijkingssecties die naar elkaar verwijzen. Verder is de samenhang die van de toolchain, niet van een onderwerp: Apify→n8n, Disco→n8n, Zotero→n8n/Obsidian, OpenRouter→n8n/LangGraph, en Claude plus GitHub in bijna alles.

**De houdbare laag zit in de Bij jou-regels.** De menubeschrijvingen verouderen — dat staat in hun eigen voetnoot — maar de waarnemingen uit de accounts zijn gedateerde feiten over de eigen omgeving, en die zijn precies wat een kennisbank wél moet bewaren. Daarom is deze reeks in dit wiki verwerkt als *één* bron met feiten over entiteiten, en niet als twintig samenvattingen van vervallen interfaces.

**Provenance is niet gelijk over de reeks.** Drie gradaties, elk op de pagina zelf benoemd:

| Gradatie | Pagina's | Wat dat betekent |
|---|---|---|
| Waargenomen in het eigen account | 18 | De Bij jou-regels zijn waarnemingen; datum is de meetdatum |
| Deels uit documentatie | Zotero, Obsidian | Zotero: webbibliotheek waargenomen, desktop-app nagelezen. Obsidian: lint-namen uit de standaardinstellingen, *"de tooltips waren niet uit te lezen"* |
| Volledig uit documentatie | Antigravity | Expliciet: het staat niet op de computer van die sessie, dus niet in de eigen installatie nagelopen |

Er zijn ook twee meetmomenten, geen één: 17 pagina's van 24 september 2026, en ClickUp, Disco en Supabase van 28 september 2026.

## Kernpunten

- Vast skelet van zes delen, twintig keer ingevuld; onderwerp is de interface, niet een vakgebied.
- Elke pagina dateert en relativeert zichzelf in de voetnoot: *menu's veranderen vaak*.
- De Bij jou-regels zijn de enige claims met houdbaarheid: gedateerde waarnemingen uit de eigen omgeving.
- Drie provenance-gradaties, en twee meetmomenten (24-09 en 28-09-2026).
- De research-flow staat er wél in, maar verspreid over vier pagina's en nergens van begin tot eind. Uitgewerkt in [[wiki/topics/research-flow]].

## Entiteiten genoemd

- [[wiki/entities/perplexity]] — waar het onderzoek gebeurt; Enterprise Pro, vastgezette agent-sessies
- [[wiki/entities/n8n]] — het koppelwerk; 13 workflows, vier Antifragile-flows Published
- [[wiki/entities/zotero]] — het bronnenarchief; 5 bronnen, machinetags uit een automatisering
- [[wiki/entities/clickup]] — de planlaag; Space *Product Research & Delivery Hub*
- [[wiki/entities/obsidian]] — de leesbril op dit wiki; kluis = llm-wiki, versie 1.13.7
- [[wiki/entities/claude]] — schrijft dit wiki, en draagt de geplande taken; drie gedaanten met drie menu's
- [[wiki/entities/supabase]] — de database onder de portfolio-site; ⚠ open beveiligingsbevinding
- [[wiki/entities/baakiedoc]] — genoemd op de Perplexity-pagina als wat op de Perplexity-API bouwt
- [[wiki/entities/de-baak]] — huisstijl en afzender van de reeks

De overige dertien gereedschappen staan als rij in [[wiki/topics/gereedschapslandschap]] en hebben (nog) geen eigen pagina.

## Concepten genoemd

- [[wiki/concepts/ingest-query-lint]] — de Obsidian-pagina beschrijft de ingest als de operationele praktijk: bronnen in `raw/`, dan Claude Code
- [[wiki/concepts/three-layer-architecture]] — de kluisboom in Obsidian maakt de drie lagen letterlijk zichtbaar
- [[wiki/concepts/gegevenshygiene]] — de reeks legt per gereedschap vast wat het met je gegevens mag; op 2026-09-24 is dat in drie tegelijk omgezet

## Citaten waard

> "Onderzoek uit Perplexity vastleggen — Antifragile Flow B"
> — linkermenu-reeks (n8n), sectie *Waar zet je het voor in?*

> "waarschijnlijk je n8n-flow"
> — linkermenu-reeks (Zotero), over de herkomst van de tags `dedup:topic…`, `dedup:url…` en `ingested:review`

Dat tweede citaat is het scherpste wat de reeks over de research-flow zegt: de maker van de pagina kon aan de output zien dat er een automatisering in Zotero schrijft, maar niet welke.

## Verbindingen met de bestaande wiki

- **Vult aan:** [[wiki/concepts/ingest-query-lint]] met de operationele praktijk zoals die in de Obsidian-pagina staat beschreven, en met de rol van Obsidian als leeslaag.
- **Vult aan:** [[wiki/entities/baakiedoc]] met de vaststelling dat Baakiedoc op de Perplexity-API bouwt.
- **Concretiseert:** [[wiki/topics/llm-augmented-knowledge-bases]] — de research-flow is de eerste feitelijke instantie van het patroon in de eigen omgeving, en laat zien waar het breekt.
- ⚠ **contradictie:** de Obsidian-pagina plaatst de kluis op `C:\arijj\llm-wiki`; die map bestaat niet. Uitgewerkt in [[wiki/entities/obsidian]].
- **Roept nieuwe vraag op:** wat doen Antifragile Flow A, C en D? De reeks noemt alleen dat er vier Published staan.

## Mijn aantekeningen (optioneel)

_(leeg — voor AV)_

## Provenance

- Bestanden: `raw/linkermenu/<slug>/index.html`, 20 mappen: antigravity, apify, chatgpt, claude, clickup, cloudflare, copilot, deepseek, disco, figma, gemini, github, langsmith, llm-council, n8n, obsidian, openrouter, perplexity, supabase, zotero.
- Origineel: gepubliceerde artifacts op claude.ai. Die staan buiten git; daarom zijn ze op 2026-09-29 byte voor byte naar `raw/` gehaald (commit `f59b66e`).
- Toegevoegd op: 2026-09-29
- Meetdata van de inhoud: 2026-09-24 (17) en 2026-09-28 (3)
