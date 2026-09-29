---
type: topic
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [onderzoek, automatisering, n8n, kennisbank, workflow]
thesis_status: opening
---

# De research-flow

> **Citatieslug:** `[[wiki/topics/research-flow]]`
>
> *Slug voorlopig. Wiki-slugs volgen `CLAUDE.md` §2 (kebab-case) en niet het bibliotheekregister; taxonomische namen lopen via [[wiki/entities/baakiedoc]].*

Hoe komt onderzoek van een vraag tot in deze kennisbank? Dit topic reconstrueert die keten uit wat [[wiki/sources/linkermenu-reeks]] erover laat zien — en benoemt vooral waar de keten niet doorloopt.

## Huidige these

De flow is **geautomatiseerd aan de voorkant en handwerk aan de achterkant**. Van vraag tot bronnenarchief loopt het machinaal: Perplexity doet het onderzoek, een n8n-flow legt het vast, Zotero ontvangt de bronnen met machinetags. Van bronnenarchief tot kennisbank loopt niets: bronnen belanden met de hand in `raw/`, waarna een ingest ze verwerkt.

Die breuk zit precies op de plek waar betekenis wordt toegevoegd. Alles vóór de breuk is verzamelen — dat schaalt en dat draait. Alles ná de breuk is interpreteren — dat is waar de kennisbank van bestaat, en daar is geen automatisering, geen trigger en geen teller. Het gevolg is voorspelbaar en meetbaar: vier gepubliceerde flows aan de ene kant, vijf bronnen zonder collectie aan de andere.

Daarnaast hangt de **planlaag los**. ClickUp bevat de onderzoeksplanning, n8n voert uit, en geen van beide weet van de ander.

_Stand per 2026-09-29 — gebaseerd op één bron ([[wiki/sources/linkermenu-reeks]]), met meetdata 2026-09-24 en 2026-09-28._

## De keten zoals de bron hem laat zien

| # | Stap | Waar | Bewijs in de bron |
|---|---|---|---|
| 1 | plannen | [[wiki/entities/clickup]] | Space *Product Research & Delivery Hub*, 7 taken To Do, alle High, zonder eigenaar of datum |
| 2 | onderzoeken | [[wiki/entities/perplexity]] | Diepgaand onderzoek; vastgezette agent-sessies *docuresearch* en *AI News Monitoring for Learning Design*; organisatieproject *Baakdociereserach* |
| 3 | vastleggen | [[wiki/entities/n8n]] | *Onderzoek uit Perplexity vastleggen — Antifragile Flow B*; vier Antifragile-flows op Published |
| 4 | archiveren | [[wiki/entities/zotero]] | 5 bronnen met de tags `dedup:topic…`, `dedup:url…`, `ingested:review`, zonder collecties |
| 5 | aanlanden | `raw/` in dit wiki | **handwerk** — de bron beschrijft de handmatige instructie als de werkwijze |
| 6 | verwerken | ingest door Claude Code | [[wiki/concepts/ingest-query-lint]] |
| 7 | lezen | [[wiki/entities/obsidian]] | kluis = llm-wiki, versie 1.13.7, sync via GitHub |

Naast stap 2 loopt een tweede invoer: **Apify** levert scrapers aan n8n (*Marktplaats Daily Scraper*), buiten Perplexity om. En naast stap 1 loopt de enige terugkerende, wél gedateerde onderzoekstaak: de weektaak *Weekly: AI-tools Updates*, elke maandag, die de changelogs van zo'n elf gereedschappen naloopt.

Twee verbindingen die je zou verwachten en die er niet zijn:

- **1 ↛ 3.** ClickUp en n8n weten niet van elkaar.
- **4 ↛ 5.** Tussen het bronnenarchief en dit wiki zit geen automatische route.

Beide zijn hieronder uitgewerkt.

## Wat we weten

- Onderzoek gebeurt in Perplexity, met vastgezette agent-sessies **docuresearch** en **AI News Monitoring for Learning Design**, en een organisatieproject *Baakdociereserach*. — [[wiki/sources/linkermenu-reeks]] (Perplexity), via [[wiki/entities/perplexity]].
- Er is één benoemde schakel van onderzoek naar archief: *Onderzoek uit Perplexity vastleggen — Antifragile Flow B*. — [[wiki/sources/linkermenu-reeks]] (n8n), via [[wiki/entities/n8n]].
- Vier van de dertien n8n-workflows zijn Antifragile-flows op **Published**; alleen B is aan een functie gekoppeld in de bron. — [[wiki/sources/linkermenu-reeks]] (n8n).
- Er schrijft iets machinaal in Zotero: de tags `dedup:topic…`, `dedup:url…` en `ingested:review` staan op de bronnen, en de bron wijst zelf naar de n8n-flow als vermoedelijke herkomst. — [[wiki/sources/linkermenu-reeks]] (Zotero), via [[wiki/entities/zotero]].
- Zotero bevat 5 bronnen — antifragiliteit, kennismanagement, vector databases — **zonder collecties**. — [[wiki/sources/linkermenu-reeks]] (Zotero).
- De stap van bron naar kennisbank is expliciet handwerk: bronnen in `raw/` zetten en Claude Code een ingest laten doen. — [[wiki/sources/linkermenu-reeks]] (Obsidian), via [[wiki/concepts/ingest-query-lint]].
- De planning staat in ClickUp: Space *Product Research & Delivery Hub*, 7 taken op To Do, alle prioriteit High, **zonder eigenaar en zonder datum**. — [[wiki/sources/linkermenu-reeks]] (ClickUp), via [[wiki/entities/clickup]].
- Er is één terugkerende, wél gedateerde onderzoekstaak: **Weekly: AI-tools Updates**, elke maandag, die de changelogs van de gereedschappen naloopt. Die taak is de aanleiding voor de *Waar zie je wat er nieuw is?*-sectie in vrijwel elke pagina van de reeks — de formulering staat in 16 van de 20 pagina's, telkens identiek. — [[wiki/sources/linkermenu-reeks]] (16 pagina's).
- Die 16 pagina's zeggen nergens **in welk systeem** die weektaak leeft. De ChatGPT-pagina wijst hem toe aan Claude (*Gepland* staat daar leeg, met de opmerking dat de Claude-taken dit al doen). Of hij dáár ook draait is een tweede vraag — zie *Wat omstreden is*. — [[wiki/sources/linkermenu-reeks]] (ChatGPT, Claude).
- Scraping loopt via Apify naar n8n (*Marktplaats Daily Scraper*), niet via Perplexity. — [[wiki/sources/linkermenu-reeks]] (Apify, n8n).
- Voor denkwerk in lussen wijst de bron weg van n8n, naar LangGraph of een AI-node met OpenRouter. — [[wiki/sources/linkermenu-reeks]] (n8n, LangSmith).

## De gaten

**1. Tussen Zotero en `raw/` zit niets.** Geen enkele pagina in de reeks noemt een automatische route van het bronnenarchief naar deze kennisbank. De Obsidian-pagina beschrijft de handmatige instructie als *de* werkwijze. Zolang dat zo is, is de kennisbank geen eindpunt van de flow maar een los project dat af en toe uit hetzelfde archief eet.

**2. ClickUp en n8n weten niet van elkaar.** De ClickUp-pagina noemt de koppeling alleen als mogelijkheid (*Instellingen → Integrations en API-token*), en er staat een AI-chat **API Token Generation** in de geschiedenis — iemand is het ooit begonnen. Nergens blijkt dat het werkt.

**3. Zotero heeft geen collecties, terwijl er machinaal in geschreven wordt.** De automatisering legt neer, niets ruimt op. De bron adviseert zelf collecties te maken zodat de binnengehaalde bronnen ergens landen.

**4. De opbrengst is klein.** Vier gepubliceerde Antifragile-flows tegenover vijf bronnen in Zotero. Of de flow draait zelden, of hij schrijft weinig weg, of hij is stilgevallen zonder dat iemand het merkte. De bron maakt geen onderscheid tussen die drie.

**5. Antifragile A, C en D zijn onbeschreven.** De reeks noemt alleen dat er vier op Published staan. Wat ze doen, wanneer ze vuren, en of ze samenhangen met B: niets.

**6. Er is geen trigger of schema benoemd** voor Flow B. Bij *Marktplaats Daily Scraper* zit het in de naam; bij B nergens.

## Wat we vermoeden

> speculatie: de tag `ingested:review` verwijst naar de map `review/` in deze kluis. Dan zou de flow al ontworpen zijn op een overdracht naar het wiki, en zou gat 1 niet ontbreken maar half gebouwd zijn. Te toetsen door Antifragile Flow B in n8n te openen en te kijken waar hij naartoe schrijft.

> speculatie: *Antifragile* in de flownamen verwijst naar dezelfde antifragiliteit als de vijf Zotero-bronnen, en de flows zijn dan zelf een toepassing van het onderwerp dat ze verzamelen. Niet bevestigd in de bron.

## Wat omstreden is

⚠ **contradictie: draait de weektaak eigenlijk?** Zestien pagina's beloven dat *Weekly: AI-tools Updates* de changelogs elke maandag voor je naleest. De geplande taken leven in claude.ai — de ChatGPT-pagina zegt dat de Claude-taken dit al doen. Maar de Claude-pagina meldt over diezelfde geplande taken: er zijn er **vier**, en *alleen de Substack Digest draait* (elke donderdag 8:00). Als de weektaak één van die vier is, wordt de belofte uit die zestien pagina's dus niet ingelost. Dezelfde pagina spreekt zichzelf daarbij tegen: de zijbalkschets noemt **2 taken**, de kaart eronder **vier**. — [[wiki/sources/linkermenu-reeks]] (Claude, ChatGPT).

Dat is geen detail: de weektaak is de enige terugkerende onderzoeksactiviteit in de hele keten die een ritme en een datum heeft. Valt hij stil, dan is er niets dat de flow periodiek aanzet.

- Verder geen tegenspraak tussen bronnen — er is pas één bron. De andere tegenspraak is bron-versus-werkelijkheid: het kluispad, uitgewerkt in [[wiki/entities/obsidian]].

## Belangrijkste entiteiten

- [[wiki/entities/perplexity]] — waar het onderzoek gebeurt
- [[wiki/entities/n8n]] — het koppelwerk, en de enige benoemde schakel
- [[wiki/entities/zotero]] — het bronnenarchief, en waar de flow zijn spoor achterlaat
- [[wiki/entities/clickup]] — de planlaag die losstaat
- [[wiki/entities/obsidian]] — de leeslaag op de kennisbank

## Belangrijkste concepten

- [[wiki/concepts/ingest-query-lint]] — de laatste stap van de flow is de eerste operatie van dit wiki
- [[wiki/concepts/three-layer-architecture]] — `raw/` is het aanlandpunt dat de flow niet automatisch bereikt
- [[wiki/concepts/llm-wiki-pattern]] — het patroon waar deze flow op uitkomt

## Evolutie van de these

- 2026-09-29 — these geopend op basis van [[wiki/sources/linkermenu-reeks]]. De keten is gereconstrueerd uit zijopmerkingen in vier pagina's; geen enkele bron beschrijft hem als geheel.

## Open vragen

- Draait Antifragile Flow B nog, en wat is zijn trigger? Te zien in n8n onder Overview → Executions.
- Staat *Weekly: AI-tools Updates* bij de vier geplande taken in claude.ai, en staat hij aan? Te zien op `claude.ai/scheduled-task`, gesorteerd op volgende run.
- Waar schrijft Flow B naartoe — alleen Zotero, of ook naar `review/`?
- Wat doen Antifragile A, C en D?
- Is de ClickUp-n8n-koppeling ooit afgemaakt? De AI-chat *API Token Generation* suggereert een poging.
- Hoort de output van deze flow uiteindelijk in [[wiki/topics/baakie-pipeline]] terecht te komen, of zijn dat twee gescheiden circuits? De bron zegt hier niets over.
- Wat is de bedoelde verhouding tussen Zotero en `raw/`: is Zotero het archief en `raw/` de selectie, of is Zotero een wachtkamer?

## Cross-references

- Concrete instantie van: [[wiki/topics/llm-augmented-knowledge-bases]]
- Bronnen die dit onderwerp raken: [[wiki/sources/linkermenu-reeks]] (1/1)
