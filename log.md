Chronologisch, append-only. Elke entry begint met `## [JJJJ-MM-DD] <operatie> | <reikwijdte>` zodat `grep "^## \[" log.md | tail -N` werkt.

Operaties: `ingest`, `query`, `lint`, `schema`.

Zie `templates/_log-entry.md` voor het body-formaat.

---

## [2026-05-20] schema | initiële opzet

**Door:** mens + LLM (Claude Code, opus-4.7).

**Wijziging:** complete mappenstructuur, schema (`CLAUDE.md`), index, log en templates aangemaakt volgens het patroon uit Andrej Karpathy's *LLM Wiki* gist. Karpathy's gist toegevoegd als seed-bron onder `raw/_seed/karpathy-llm-wiki.md`.

**Volgende stap:** gebruiker beslist welke eerste echte bronnen worden toegevoegd en in welk domein de wiki begint te groeien.

## [2026-05-20] ingest | Karpathy — LLM Wiki

**Bron:** `raw/_seed/karpathy-llm-wiki.md` — article (gist) — Andrej Karpathy — sha256 `dc3efe98ae62f23dd08acad13aba2e95287beb20b6bec2f4af0423557fe37401`
**Samenvattingspagina:** [[wiki/sources/karpathy-llm-wiki]]

**Geraakte pagina's:** geen — dit is de eerste ingest, alles is nieuw.

**Nieuwe pagina's:**
- [[wiki/sources/karpathy-llm-wiki]] — bronsamenvatting
- [[wiki/entities/karpathy]] — auteur van het patroon
- [[wiki/entities/vannevar-bush]] — historische voorouder via Memex
- [[wiki/concepts/llm-wiki-pattern]] — centraal concept van de bron
- [[wiki/concepts/rag]] — primair contrast dat Karpathy aanbrengt
- [[wiki/concepts/three-layer-architecture]] — raw/wiki/schema scheiding
- [[wiki/concepts/ingest-query-lint]] — de drie kern-operaties
- [[wiki/concepts/memex]] — Bush's Memex als geestelijke voorouder
- [[wiki/topics/llm-augmented-knowledge-bases]] — meta-topic; opent met deze ene bron als basis voor de huidige these
- `index.md` — secties Topics / Entities / Concepts / Sources gevuld

**Contradicties geïntroduceerd of opgelost:** geen — pas één bron.

**Open vragen toegevoegd:**
- Op welke schaal volstaat enkel `index.md`-navigatie niet meer?
- Hoe gaan we om met *identity drift* (duplicate concepten onder net andere namen)?
- Moeten relaties tussen pagina's getypeerd worden (similar/contains/contradicts)?
- Welke Memex-eigenschappen zijn nog niet door huidige LLM-implementaties opgepikt?
- Hoe vaak is "periodiek" voor lint in de praktijk?

**Scope-aantekening:** 9 nieuwe pagina's, binnen Karpathy's richtlijn van 5–15 per ingest. Tools (Obsidian, Marp, Dataview, qmd) en illustratief voorbeeld (Tolkien Gateway) hebben *geen* eigen pagina gekregen — pas wanneer een latere bron ze als subject behandelt.

## [2026-05-20] schema | architectuur-correctie + huisstijl + archief

**Door:** mens + LLM (Claude Code, opus-4.7).

**Wijzigingen buiten dit wiki, voorafgaand aan de eerstvolgende ingest:**
1. `baakie-orchestrator/CLAUDE.md` — tabel "Beschikbare subagents" van 5 naar 3 rijen; `baakiehtml` samengevoegd met `baakieprint`; `baakiened` als autonome agent buiten workflow gemarkeerd; routing-regels herzien.
2. `baakie-orchestrator/memory/decision-log.md` — twee entries: "5 → 3 spaces" + "Huisstijl-baseline v0.1 toegevoegd".
3. `baakie-orchestrator/CHANGELOG.md` — v0.2.10 entry.
4. `~/.claude/projects/C--Users-arijj/memory/project_spaces_architecture.md` — bijgewerkt naar drie-agent-architectuur; `baakiehtml` als samengevoegd gemarkeerd.
5. `baakie-orchestrator/context/organisatie/debaak-huisstijl.md` — nieuwe canonieke huisstijl-spec v0.1; verwezen vanuit `baakie-orchestrator/CLAUDE.md` en uit `llm-wiki/CLAUDE.md §9 Visuele deliverables`.
6. `raw/document management.html` → `raw/_archief/document-management-10-fasen-plan.html` — achterhaald 10-fasenplan buiten ingest-pad gezet (Karpathy-principe: ruwe bronnen blijven beschikbaar als historische evidentie).

**Aanleiding:** drift tussen drie mentale modellen (5 agenten in repo, 4 in eerder gesprek, 3 in vandaag-bevestigd). Update-volgorde van kern naar afgeleid uitgevoerd voor één bron-van-waarheid.

## [2026-05-20] ingest | Baakie-pipeline-bronnen (3 bestanden, gecombineerd)

**Bronnen:**
- `raw/debaak-document-management-phase1 (2).html` — sha256 `3d2ae6162741118587fd00237d84d2bcc9a0d67f7525cd3cff990d3e5de691d7` — [[wiki/sources/debaak-dm-phase1]]
- `raw/documentbeheer-infographic.html` — sha256 `aec00556281fc77ac6e768a1d69ef1653f0bcddeeebb08adb431bbddb82f965a` — [[wiki/sources/documentbeheer-infographic]]
- `raw/Auteursrecht op Wetenschappelijk Werk - Factoren die Bescherming Bepalen.html` — sha256 `210d73d4818909b2da87762c7798efdfcf873e12c152473052799ba21e608963` — [[wiki/sources/auteursrecht-wetenschappelijk-werk]]

**Nieuwe pagina's (13):**
- Topic: [[wiki/topics/baakie-pipeline]]
- Entities: [[wiki/entities/de-baak]], [[wiki/entities/baakiedoc]], [[wiki/entities/baakiekwal]], [[wiki/entities/baakieprint]]
- Concepts: [[wiki/concepts/naamgevingsconventie]], [[wiki/concepts/sharepoint-contentflow]], [[wiki/concepts/auteursrecht-wetenschappelijk-werk]]
- Concept-placeholders: [[wiki/concepts/bronvermelding]], [[wiki/concepts/wetenschappelijke-kwaliteit]]
- Source-pagina's: [[wiki/sources/debaak-dm-phase1]], [[wiki/sources/documentbeheer-infographic]], [[wiki/sources/auteursrecht-wetenschappelijk-werk]]

**Geraakte pagina's:** `index.md` aangevuld met 13 nieuwe entries (Topics, Entities, Concepts, Sources).

**Bewust niet ingest:** `raw/_archief/document-management-10-fasen-plan.html` — verplaatst uit `raw/` voorafgaand aan deze ingest. Achterhaalde architectuur (10 fasen, 22 weken) per AV-besluit; behoudt provenance-status als historische evidentie. Zie decision-log `baakie-orchestrator/memory/decision-log.md` 2026-05-20.

**Bewust niet als eigen pagina:**
- `baakiened` (autonome agent, geen taak in deze workflow) — alleen als referentie in topic + entity-buurten.
- `baakiehtml` (samengevoegd met baakieprint per 2026-05-20).
- SharePoint, Excel, PA (training Persoonlijk Adviseren), CRAFT-rubrieken — instrumentele/operationele vermeldingen die in `baakie-orchestrator/`-canon thuishoren, niet als eigen wiki-pagina.

**Contradicties geïntroduceerd of opgelost:** geen interne contradicties tussen de drie bronnen. Eén externe contradictie expliciet gemarkeerd in [[wiki/topics/baakie-pipeline]] (en archief-verplaatsing van bestand 3).

**Open vragen toegevoegd (worden uitgewerkt zodra bronnen beschikbaar):**
- Volledige taglijst trainingsabkortingen
- Operationele beslisregels per assessment-criterium (zit in `baakie-orchestrator/spaces/baakiekwal/`, brug naar wiki nog niet gelegd)
- Skeleton-organisatie binnen baakieprint na merge met baakiehtml
- B1-hergebruik in de pipeline
- Volledige bronnen voor bronvermelding en wetenschappelijke kwaliteit (placeholders nu)

**Scope-aantekening:** 13 nieuwe pagina's — boven de typische 10–15 maar consistent met "3 bronnen tegelijk" ingest. Gecombineerde aanpak gekozen omdat de bronnen één coherente architectuur beschrijven en losse ingest tot herhaaldelijk dezelfde topic-update zou leiden.

## [2026-05-20] schema | uitbreiding na AV-bevestiging fases + Anewspring (A + B + D)

**Door:** mens + LLM. AV bevestigde 3-fase-architectuur (naamgeving / kwaliteit / publicatie) en noemde 5 publicatie-formats waaronder **Anewspring** (LMS); gaf groen licht voor combinatie A + B + D uit eerder voorstel.

**Wijzigingen:**

- **A.** Nieuwe entity-pagina [[wiki/entities/anewspring]] (LMS als output-target). Geen bron in `raw/` yet — open vragen genoteerd. [[wiki/entities/baakieprint]] bijgewerkt: format-target-tabel met 5 formats (doc / pdf / powerpoint / responsive HTML / Anewspring), cross-reference toegevoegd.
- **B.** [[wiki/concepts/naamgevingsconventie]] aangepast: veld-tabel bevat nu kolom "Canonieke lijst" met exacte verwijzingen naar `baakie-orchestrator/controlled-lists/*.md` per veld. Expliciete regel toegevoegd: dit wiki onderhoudt geen kopie van taglijsten — single source of truth is de xlsx + de markdown-snapshots. Oude open vraag "volledige taglijst?" verwijderd, vervangen door "volledigheid is xlsx-edit voor baakiedoc".
- **D.** Nieuwe brug-pagina [[wiki/concepts/baakiekwal-werkwijze]]: dunne verwijzing naar `baakie-orchestrator/spaces/baakiekwal/` met inventaris van canonieke bestanden (baseline + 5 knowledge-files + 6 rubrieken + 2 voorbeeldrapporten — stand 2026-05-20). Geen duplicatie van inhoud. Patroon-verwant aan huisstijl-verwijzing in `llm-wiki/CLAUDE.md §9`. [[wiki/entities/baakiekwal]] kreeg cross-reference naar de brug-pagina.

**Geraakte pagina's:**
- Nieuw: [[wiki/entities/anewspring]], [[wiki/concepts/baakiekwal-werkwijze]] (2)
- Bewerkt: [[wiki/entities/baakieprint]], [[wiki/entities/baakiekwal]], [[wiki/concepts/naamgevingsconventie]], [[wiki/topics/baakie-pipeline]] (4)
- `index.md`: 2 nieuwe entries toegevoegd onder Entities en Concepts.

**Bewust niet gedaan in dit run:**
- C (huisstijl-vragenlijst) — apart, op verzoek van AV.
- E (WebSearch naar AI-auteursrecht-bron) — wacht tot vraag urgent wordt.
- Updaten van `baakieprint/knowledge/` skeleton-set in de orchestrator — daar staat al een open punt voor in decision-log 2026-05-20.

**Open vragen toegevoegd:**
- Anewspring-specifieke skeleton-vereisten (SCORM/xAPI?)
- Versiebeheer Anewspring vs. SharePoint-bibliotheek
- URL-registratie van Anewspring-publicaties in Excel-register

## [2026-09-24] schema | sync via Obsidian Git

**Door:** mens + LLM (Claude, Cowork).

**Wijziging:** Obsidian Git ingesteld op DESKTOP-NJV6J3J: pull bij opstarten, elke 10 minuten automatisch pull en commit-and-sync.

**Volgende stap:** dezelfde instellingen op de andere computer.
## [2026-09-29] ingest | De linkermenu-reeks — de research-flow

**Bron:** `raw/linkermenu/<slug>/index.html`, 20 mappen — oriëntatiepagina's in De Baak-huisstijl, gemaakt in sessies van AV op basis van waarnemingen in zijn eigen accounts. Meetdata 2026-09-24 (17) en 2026-09-28 (3). Op 2026-09-29 uit gepubliceerde artifacts naar `raw/` gehaald (commit `f59b66e`).
**Samenvattingspagina:** [[wiki/sources/linkermenu-reeks]]

**Aanleiding en afbakening.** AV vroeg eerst wat voor content die twintig pagina's eigenlijk hebben, met het vermoeden dat ze niets met elkaar te maken hebben. Dat vermoeden is juist: het onderwerp van elke pagina is de interface van één gereedschap op één moment, en die verouderen — dat staat in hun eigen voetnoot. Twintig samenvattingspagina's zouden dus twintig verouderende pagina's opleveren. Wat wél houdbaar is, zijn de **Bij jou**-waarnemingen. Op verzoek van AV is daarom één cluster verwerkt: de research-flow, verspreid over de pagina's van Perplexity, n8n, Zotero, ClickUp en Obsidian.

**Nieuwe pagina's:**

- [[wiki/sources/linkermenu-reeks]] — één bronpagina voor de hele reeks in plaats van twintig; documenteert het vaste skelet, de twee meetmomenten en de drie provenance-gradaties (waargenomen / deels uit documentatie / volledig uit documentatie).
- [[wiki/topics/research-flow]] — de keten gereconstrueerd uit zijopmerkingen in vier pagina's. Geen enkele bron beschrijft hem als geheel. Zes gaten benoemd.
- [[wiki/entities/perplexity]] — waar het onderzoek gebeurt.
- [[wiki/entities/n8n]] — het koppelwerk; de enige benoemde machinale schakel.
- [[wiki/entities/zotero]] — het bronnenarchief; waar de flow zijn spoor achterlaat.
- [[wiki/entities/clickup]] — de planlaag die losstaat.
- [[wiki/entities/obsidian]] — de leeslaag op dit wiki.

**Geraakte pagina's:**

- [[wiki/concepts/three-layer-architecture]] — nieuwe sectie over de grens van `raw/` in de praktijk: de laag is goed beschermd maar wordt niet gevuld. Plus de vaststelling dat de reeks twee maanden buiten git bestond.
- [[wiki/concepts/ingest-query-lint]] — de ingest blijkt buiten dit wiki als proces te zijn vastgelegd (de Obsidian-pagina instrueert hem). Nieuwe sectie over waar de operatie op vastloopt.
- [[wiki/topics/llm-augmented-knowledge-bases]] — these bijgewerkt: de tweede bron voegt geen theorie toe maar een meting. Het patroon breekt niet op de wiki-laag maar op de aanvoer. `sources: 1 → 2`.
- [[wiki/entities/baakiedoc]] — nieuw feit: bouwt op de Perplexity-API, en is daarmee een draaiende koppeling met een externe afhankelijkheid. `sources: 2 → 3`.
- `index.md` — 1 topic, 5 entities en 1 source toegevoegd; twee bestaande entries van datum en bronaantal bijgewerkt.

**Contradicties geïntroduceerd of opgelost:**

- ⚠ **Kluispad.** De Obsidian-pagina plaatst de kluis op `C:\arijj\llm-wiki`. Die map bestaat niet — nagegaan op 2026-09-29; onder `C:\arijj` staat alleen `Visma`. De kluis en de clone staan op `C:\Users\arijj\llm-wiki`. Bron blijft ongewijzigd (immutabel); gecorrigeerd in [[wiki/entities/obsidian]].
- ⚠ **Draait de weektaak?** Zestien van de twintig pagina's beloven dat *Weekly: AI-tools Updates* elke maandag de changelogs naleest. De geplande taken leven in claude.ai; de Claude-pagina meldt vier taken waarvan *alleen de Substack Digest draait*. Dezelfde pagina noemt in de zijbalkschets 2 taken en in de kaart vier. Gemarkeerd in [[wiki/topics/research-flow]].
- **Complement, geen contradictie:** log-entry 2026-09-24 schema vermeldt Obsidian Git met automatische sync elke 10 minuten op DESKTOP-NJV6J3J, terwijl de Obsidian-pagina synchronisatie als handwerk beschrijft. Twee regimes naast elkaar — vastgelegd in [[wiki/entities/obsidian]].

**Open vragen toegevoegd:**

- Draait Antifragile Flow B nog, wat is zijn trigger, en waar schrijft hij naartoe?
- Wat doen Antifragile A, C en D?
- Staat *Weekly: AI-tools Updates* bij de vier geplande taken in claude.ai, en staat hij aan?
- Verwijst de Zotero-tag `ingested:review` naar de map `review/` in deze kluis?
- Is de ClickUp-n8n-koppeling ooit afgemaakt? De AI-chat *API Token Generation* suggereert een poging.
- Hoort de output van de research-flow in [[wiki/topics/baakie-pipeline]] terecht te komen, of zijn dat gescheiden circuits?
- Wat is de bedoelde verhouding tussen Zotero en `raw/` — archief versus selectie, of wachtkamer?

**Bewust niet gedaan in dit run:**

- Geen entity-pagina's voor de gereedschappen buiten de research-flow: Supabase, Apify, Cloudflare, GitHub, Figma, Disco, LangSmith, OpenRouter, LLM Council, Antigravity, Copilot, ChatGPT, Gemini, DeepSeek, Claude. De reeks bevat over elk daarvan waarnemingen; die wachten op een volgende ingest.
- Geen samenvattingspagina's van de menubeschrijvingen zelf. Die blijven in `raw/` opzoekbaar zonder dat de wiki hun veroudering overneemt.
- Twee bevindingen uit de reeks die buiten dit onderwerp vallen en niet in de wiki zijn verwerkt, maar wel gemeld: **Supabase** meldt `RLS Disabled in Public` op de portfolio-database (1 fout, 9 waarschuwingen, stand 2026-09-28) en heeft geen GitHub-koppeling, geen migraties en geen back-ups op het gratis plan. **Apify** stond op $5.65 van $19.
- Geen wijziging in `CLAUDE.md`. De ervaring dat een bron soms een *reeks* is, en dat twintig samenvattingen dan het verkeerde antwoord zijn, is een kandidaat voor §3.1 — maar schema-wijzigingen gaan in overleg.
