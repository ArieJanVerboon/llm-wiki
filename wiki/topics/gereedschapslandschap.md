---
type: topic
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [gereedschap, estate, overzicht, inventaris]
thesis_status: opening
---

# Het gereedschapslandschap

> **Citatieslug:** `[[wiki/topics/gereedschapslandschap]]`

Twintig gereedschappen, één persoon, twee meetmomenten. Deze pagina houdt vast wat [[wiki/sources/linkermenu-reeks]] over elk van hen vaststelde — niet hoe hun menu eruitzag, maar wat er in dát account aan stond.

## Huidige these

De estate is **breed en overlappend**, en de bron duwt op vrijwel elke pagina naar versmalling. Vijf chat-assistenten naast elkaar, twee databases (Supabase én Cloudflare D1), twee automatiseringssporen (n8n én LangGraph), twee ontwerpomgevingen, en een betaald LLM Council-plan van $1 dat juist níet doet waarvoor het bedoeld lijkt — waar de bron zelf OpenRouter Chat als gratis alternatief naast legt.

Dat is geen verwijt: een landschap dat breed is, is verkend. Maar het kost wat. Elk gereedschap is een account met een instelling, een verbruik en een houdbaarheidsdatum — en de lijst *wat aandacht vraagt* hieronder is elf punten lang, verdeeld over acht gereedschappen. Breedte is niet gratis; ze wordt betaald in onderhoud dat niemand plant.

_Stand per 2026-09-29, meetdata 2026-09-24 en 2026-09-28._

## Wat aandacht vraagt

Elf punten, met de datum waarop ze zijn vastgesteld. Geen ervan is door mij veranderd.

| Wat | Waar | Sinds | Soort |
|---|---|---|---|
| ⚠ `RLS Disabled in Public` — tabel leesbaar met de publieke sleutel | [[wiki/entities/supabase]] | 2026-09-28 | beveiliging |
| Geen back-ups, geen migraties, geen GitHub-koppeling | [[wiki/entities/supabase]] | 2026-09-28 | vangnet |
| Google Drive-koppeling **opnieuw verbinden vóór 31-10-2026** | [[wiki/entities/perplexity]] | 2026-09-24 | termijn |
| Twee Computer-taken op *Action needed* | [[wiki/entities/perplexity]] | 2026-09-24 | onafgemaakt werk |
| Instance loopt 2 versies achter; bijwerken ná de GitHub-back-up | [[wiki/entities/n8n]] | 2026-09-24 | onderhoud |
| Van vier geplande taken draait alleen de Substack Digest | [[wiki/entities/claude]] | 2026-09-24 | stilgevallen? |
| Traininginstelling **niet nagegaan** (Free-account) | ChatGPT | — | gat |
| Melding dat Geplande acties lang niet gebruikt zijn | Gemini | 2026-09-24 | opruimen |
| 5 bronnen zonder collecties, terwijl een automatisering erin schrijft | [[wiki/entities/zotero]] | 2026-09-24 | ordening |
| 7 taken allemaal High, zonder eigenaar of datum | [[wiki/entities/clickup]] | 2026-09-28 | planning |
| $5.65 van $19 verbruikt deze periode | Apify | 2026-09-24 | kosten |

De eerste drie hebben een klok: een open tabel zonder back-up, en een koppeling die over een maand verloopt. De rest kan wachten, maar niet onbeperkt — en de zevende regel is het gat dat pas opvalt doordat de andere traininginstellingen wél zijn nagelopen. Zie [[wiki/concepts/gegevenshygiene]].

## De twintig, per rol

| Gereedschap | Rol in de estate | Wat er vaststaat | Pagina |
|---|---|---|---|
| Perplexity | onderzoek | Enterprise Pro; sessies *docuresearch*, *AI News Monitoring* | [[wiki/entities/perplexity]] |
| n8n | koppelwerk | 13 workflows, 4 Antifragile op Published | [[wiki/entities/n8n]] |
| Zotero | bronnenarchief | 5 bronnen, machinetags, geen collecties | [[wiki/entities/zotero]] |
| ClickUp | planning | één Space, 7 taken zonder datum | [[wiki/entities/clickup]] |
| Obsidian | lezen van dit wiki | v1.13.7, sync via GitHub | [[wiki/entities/obsidian]] |
| Claude | schrijft dit wiki, plant taken | drie gedaanten, drie menu's, vier geplande taken | [[wiki/entities/claude]] |
| Supabase | database portfolio | ⚠ RLS uit, gratis plan | [[wiki/entities/supabase]] |
| Cloudflare | hosting van de hele estate | Workers & Pages, D1, AI Gateway, Zero Trust → Access, API-tokens | rij |
| GitHub | code en versies | ArieJanVerboon, Free, organisatie Inspreadables; Actions publiceren naar Cloudflare | rij |
| Apify | scrapen | $5.65 van $19; levert aan n8n | rij |
| OpenRouter | modelkeuze en kosten | nog geen API-sleutel; Zero Data Retention aan | rij |
| LangSmith | agents volgen en testen | Personal; LangGraph voor denkwerk, n8n voor koppelingen | rij |
| Disco | trainerscommunity | de-baak-trainers-community.disco.co, beheerdersrechten; koppelbaar aan n8n | rij |
| Figma | ontwerp en mockups | team Free, account vrijwel leeg | rij |
| ChatGPT | tweede mening, Codex | Free; Work op slot; Bibliotheek leeg; Gepland leeg | rij |
| Gemini | beeld en Google-omgeving | geen zelfstandige agent in het menu | rij |
| DeepSeek | tweede mening | geen mappen; ordening via voorvoegsels *F3*, *D*, *PH* in titels | rij |
| Copilot | consumentenversie | gratis; training uit; niet de plek voor Baak-materiaal | rij |
| LLM Council | meerdere modellen laten wegen | plan $1 — de echte raad zit op Pro ($25) | rij |
| Antigravity | agent-IDE van Google | **niet geïnstalleerd**; pagina uit documentatie | rij |

*Rij* betekent: de waarneming staat hier, en er is nog geen eigen pagina. Elke rij kan gepromoveerd worden zodra er een tweede bron over komt of er iets aan gedaan moet worden. Zeven gereedschappen hebben een pagina omdat er feiten over zijn die uitleg of een status nodig hebben; de dertien rijen hebben dat (nog) niet, en dertien dunne pagina's zouden het netwerk verwateren.

## Wat we weten

- Vijf gereedschappen zijn chat-assistenten die deels hetzelfde doen; de bron vergelijkt ze expliciet in een subreeks (Claude, Perplexity, Gemini, DeepSeek, ChatGPT). — [[wiki/sources/linkermenu-reeks]]
- Twee databases in één estate: Supabase draagt de portfolio-site, Cloudflare D1 wordt genoemd als het lichtere alternatief naast een Worker. De bron kiest niet.
- **DeepSeek heeft geen mappen**, en de ordening is een eigen vondst: voorvoegsels *F3*, *D* en *PH* in de gesprekstitels, samen met Ctrl+K. Die code staat nergens anders opgeschreven dan in de titels zelf — raakt hij kwijt, dan is de ordening weg.
- De estate rust op Cloudflare: Workers & Pages voor de sites, D1 voor data, Zero Trust → Access voor toegang, API-tokens zodat Claude Code kan deployen. GitHub Actions publiceren ernaartoe.
- Disco bevat **persoonsgegevens**: namen en profielen van trainers. Daarmee is het het enige gereedschap in de lijst met een AVG-gewicht dat niet van jezelf is. — zie [[wiki/concepts/gegevenshygiene]]
- Figma is er, maar vrijwel leeg; de bron adviseert de huisstijlkleuren en Arial in Resources vast te leggen zodat een mockup niet afwijkt.

## Wat we vermoeden

> speculatie: de breedte van dit landschap is een fase, niet een eindtoestand. Vijf van de elf aandachtspunten hierboven gaan over gereedschappen die nauwelijks gebruikt worden (Figma leeg, ChatGPT leeg, LLM Council op het laagste plan, Antigravity niet geïnstalleerd, Gemini met ongebruikte acties). Dat is het profiel van een verkenning die klaar is en waaruit nog niet is opgeruimd. Te toetsen door per gereedschap te vragen: wanneer heb ik dit voor het laatst voor echt werk gebruikt?

## Belangrijkste entiteiten

- [[wiki/entities/claude]], [[wiki/entities/perplexity]], [[wiki/entities/n8n]], [[wiki/entities/zotero]], [[wiki/entities/clickup]], [[wiki/entities/obsidian]], [[wiki/entities/supabase]]

## Belangrijkste concepten

- [[wiki/concepts/gegevenshygiene]] — wat elk gereedschap met je gegevens mag
- [[wiki/concepts/three-layer-architecture]] — waarom wat buiten de repo staat geen bron is

## Evolutie van de these

- 2026-09-29 — these geopend op basis van [[wiki/sources/linkermenu-reeks]]. Eén bron, twee meetmomenten, geen verificatie van de standen.

## Open vragen

- Welke van deze twintig zijn in de laatste maand voor echt werk gebruikt?
- Supabase of D1 — is dat een keuze of een restant?
- Wat staat er in de Disco-deelnemerslijst en wie mag die exporteren?
- Wat betekenen *F3*, *D* en *PH* in de DeepSeek-titels, en hoort die code niet ergens opgeschreven?
- Hoort dit landschap ergens centraal bijgehouden te worden, of is deze pagina dat?

## Cross-references

- Gemeten in: [[wiki/sources/linkermenu-reeks]]
- Verwante onderwerpen: [[wiki/topics/research-flow]] — vijf van deze twintig vormen die keten
