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

_Stand per 2026-09-29 — gebaseerd op één bron ([[wiki/sources/linkermenu-reeks]]), met meetdata 2026-09-24 en 2026-09-28. **Ongetest**: zie het Testplan hieronder. Deze these beschrijft wat de bron zegt dat er staat, niet wat er draait._

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

## Testplan — hiervan is nog niets getest

**Status per 2026-09-29: ongetest.** Alles hierboven is gereconstrueerd uit *beschrijvingen* van de keten, niet waargenomen in werking. De bron zegt dat Flow B onderzoek uit Perplexity vastlegt; hij zegt niet dat die flow deze maand gedraaid heeft. Zolang de tests hieronder niet gedraaid zijn, is dit topic een hypothese en geen beschrijving.

Dat onderscheid is het hele punt van deze sectie: het verschil tussen een keten die *bestaat* en een keten die *draait* is niet uit een beschrijving af te lezen — alleen uit wat er aan de achterkant uitkomt.

### De volgorde is het advies

Niet zeven tests naast elkaar, maar drie ronden met een stopregel ertussen. Meten kost tijd; de meeste tijd gaat verloren aan het nauwkeurig in kaart brengen van iets dat helemaal niet meer draait.

**Ronde 1 — kijk naar de uitkomst, niet naar de machine.**

| | Test | Wat je doet | Wat je opschrijft |
|---|---|---|---|
| **T5** | Komt er iets áán? | Zotero openen, kolom *Date Added* toevoegen en daarop sorteren | de datum van de nieuwste bron |

Dat is één blik en het is de enige test die onafhankelijk is van wat de flows *beweren* te doen. Een keten die bestaat en een keten die draait zien er in n8n identiek uit; in Zotero niet.

> **Stopregel.** Is de nieuwste *Date Added* ouder dan pakweg twee maanden, dan is de keten stil. Sla ronde 2 dan grotendeels over: T2, T3, T4 en T7 beschrijven dan de bouw van iets dat niet loopt. Doe alleen **T1** (wanneer draaide B voor het laatst, en met welke fout) en ga daarna direct naar de end-to-end-test. Eerst weten wáár het stopte, dan pas repareren.

**Ronde 2 — lees de machine, in deze volgorde.**

| | Test | Wat je doet | Bevestigt als | Weerlegt als |
|---|---|---|---|---|
| **T1** | Draait Flow B? | n8n → Overview → Executions, filteren op *Antifragile Flow B* | runs in de laatste 30 dagen met status success | geen runs, of alleen fouten |
| **T2** | Waar schrijft B naartoe? | de workflow openen, de laatste nodes bekijken | een Zotero- of HTTP-node naar de Zotero-API | het eindpunt is iets anders |
| **T3** | Is er een route naar dit wiki? | in álle flows zoeken op `github`, `llm-wiki`, `review` | zo'n node bestaat → gat 1 is half gebouwd | niets → gat 1 staat helemaal open |
| **T6** | Draait de weektaak? | `claude.ai/scheduled-task`, sorteren op volgende run | *Weekly: AI-tools Updates* staat er en is actief | hij staat er niet, of staat gepauzeerd |
| **T4** | Wat doen A, C en D? | de drie workflows openen; trigger en eindpunt noteren | ze horen bij dezelfde keten | losse flows die alleen de naam delen |
| **T7** | ClickUp ↔ n8n? | n8n → Credentials op een ClickUp-credential; ClickUp → Integrations | er is een werkende koppeling | alleen het token uit de AI-chat, niets actief |

T1 tot T3 gaan over de schakel waar alles van afhangt. **T6 staat bewust vóór T4**: als de weektaak niet draait, is er geen periodieke aanzet, en dan is de vraag wat A, C en D doen minder dringend dan de vraag wat de keten in beweging zet. T4 en T7 zijn inventarisatie — nuttig, niet urgent.

Voor T1 tot T4 hoeft niet geklikt te worden: volgens [[wiki/entities/n8n]] staan de **n8n API** en **Instance-level MCP** aan, en daarmee kan Claude de workflows en hun executions rechtstreeks uitlezen. Dat is sneller en het levert een uitslag die te kopiëren is in plaats van na te vertellen. Voorwaarde is een credential die deze sessie mag gebruiken; die is er nu niet.

**Ronde 3 — de enige test die het geheel meet.**

Duw één echte onderzoeksvraag door de keten en kijk waar hij blijft steken:

```
taak in ClickUp  →  onderzoek in Perplexity  →  vastleggen  →
bron in Zotero   →  bestand in raw/          →  ingest      →  pagina in wiki/
```

De zes tests hiervoor meten onderdelen; deze meet de keten. **De plek waar het vastloopt is per definitie het echte gat**, en dat hoeft geen van de zes gaten hierboven te zijn — het kan ook iets zijn wat nergens in de bron staat. Kies een vraag die je toch al wilde uitzoeken, zodat de test zelf ook werk oplevert.

### Uitslag invullen

| Test | Uitslag | Datum | Door |
|---|---|---|---|
| T5 | | | |
| T1 | | | |
| T2 | | | |
| T3 | | | |
| T6 | | | |
| T4 | | | |
| T7 | | | |
| end-to-end | | | |

Vul deze tabel in deze pagina in en schrijf een log-entry `lint | research-flow getest`. Zolang de statusregel bovenaan *ongetest* zegt, is dat geen slordigheid maar de waarheid.

### En daarna: van test naar check

Een test vertelt hoe het er vandaag voor staat. Dat is precies zo duurzaam als het geheugen van degene die hem draaide — en deze hele pagina bestaat omdat niemand wist of Flow B nog liep.

Dus sluit elke bevinding af met iets dat het de volgende keer zélf merkt:

- **T5 → een check.** Draait er niets meer in Zotero, dan is dat pas een storing als iets het opmerkt. Een wekelijkse controle op de nieuwste *Date Added* is genoeg; die kan in dezelfde geplande taak die T6 onderzoekt.
- **T1 → een foutmelding die aankomt.** Een flow die faalt in n8n en niemand waarschuwt, is een flow die stil stopt. n8n houdt het foutpercentage bij; wie leest dat?
- **T6 → één plek waar geplande taken staan.** Dat de weektaak zestien keer beloofd is en nergens aanwijsbaar, komt doordat geplande taken over claude.ai, Cowork, Perplexity en de Windows Taakplanner verspreid liggen. Zie [[wiki/entities/claude]].

> speculatie: de goedkoopste versie hiervan is niet een script maar één geplande taak die wekelijks drie dingen naloopt — de nieuwste *Date Added* in Zotero, het foutpercentage in n8n, en of hijzelf nog bestaat — en die een regel wegschrijft. Drie getallen per week is genoeg om stilstand binnen een week te zien in plaats van binnen een kwartaal.

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
- Vijf van de twintig gereedschappen in [[wiki/topics/gereedschapslandschap]] vormen deze keten
- Al het materiaal loopt door de instellingen uit [[wiki/concepts/gegevenshygiene]]
- Bronnen die dit onderwerp raken: [[wiki/sources/linkermenu-reeks]] (1/1)
