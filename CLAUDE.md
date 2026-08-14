# CLAUDE.md — Schema voor deze LLM Wiki

Dit document configureert hoe een LLM-agent (Claude Code of vergelijkbaar) deze persoonlijke kennisbibliotheek leest, uitbreidt en onderhoudt. Het is gebaseerd op het patroon beschreven in Andrej Karpathy's *LLM Wiki* (zie `raw/_seed/karpathy-llm-wiki.md`).

Co-evolueer dit bestand met de eigenaar (Arij Jan). Wijzigingen aan conventies horen hier — niet verspreid over pagina's.

---

## 1. Drie lagen

| Laag | Map | Eigenaar | Mutabel? |
|---|---|---|---|
| **Raw sources** | `raw/` | Mens | Nee — alleen toevoegen, nooit aanpassen |
| **Wiki** | `wiki/` | LLM | Ja — LLM schrijft en onderhoudt alles |
| **Schema** | `CLAUDE.md` (dit bestand) | Mens + LLM samen | Ja — bewust en expliciet |

**Strikt:** de LLM bewerkt nooit iets onder `raw/`. Bronnen zijn immutabel.

---

## 2. Mapindeling

```
llm-wiki/
├── CLAUDE.md                # dit bestand (schema)
├── index.md                 # catalogus van alle wiki-pagina's
├── log.md                   # chronologisch logboek (append-only)
├── raw/
│   ├── assets/              # afbeeldingen, downloads
│   └── _seed/               # initiële seed-bronnen
├── wiki/
│   ├── overview.md          # synthese op hoog niveau
│   ├── entities/            # personen, organisaties, producten, projecten
│   ├── concepts/            # ideeën, theorieën, methodes, definities
│   ├── topics/              # bredere thema's, evolueerbare these
│   └── sources/             # samenvattingspagina per ingestte bron
└── templates/               # paginasjablonen
    ├── _source.md
    ├── _entity.md
    ├── _concept.md
    ├── _topic.md
    ├── _comparison.md
    └── _log-entry.md
```

Naamgeving: kebab-case bestandsnamen, geen spaties, geen hoofdletters. Bijvoorbeeld `wiki/concepts/spaced-repetition.md`, niet `Spaced Repetition.md`.

---

## 3. Operaties

### 3.1 Ingest

Wanneer een nieuwe bron in `raw/` wordt toegevoegd en de gebruiker zegt "ingest [bestandsnaam]" of vergelijkbaar:

1. **Lees** de bron volledig.
2. **Bespreek** met de gebruiker: wat zijn de hoofdpunten, welke claims, welke entiteiten en concepten verdienen een eigen pagina?
3. **Schrijf** een samenvattingspagina onder `wiki/sources/<slug>.md` op basis van `templates/_source.md`.
4. **Update** alle relevante bestaande pagina's onder `wiki/entities/`, `wiki/concepts/` en `wiki/topics/`:
   - voeg nieuwe claims toe met citatie naar de bron
   - markeer waar de nieuwe bron oudere claims tegenspreekt (met `⚠ contradictie`)
   - werk cross-references bij ([[wiki-links]])
5. **Maak** nieuwe entiteit-/concept-/topic-pagina's aan voor onderwerpen die nog geen pagina hebben maar dat verdienen.
6. **Update** `index.md` met nieuwe pagina's en gewijzigde samenvattingen.
7. **Append** een entry aan `log.md` volgens `templates/_log-entry.md`.

Eén bron raakt typisch 5–15 wiki-pagina's. Werk grondig.

**Stijl:** ingest één bron tegelijk en blijf in dialoog tenzij de gebruiker expliciet om batch-mode vraagt.

### 3.2 Query

Wanneer de gebruiker een vraag stelt over de inhoud van de wiki:

1. Lees eerst `index.md` om relevante pagina's te vinden.
2. Drill door naar de specifieke pagina's; lees ze volledig.
3. Synthetiseer een antwoord met expliciete citaties naar wiki-pagina's én onderliggende bronnen.
4. **Stel voor** om waardevolle antwoorden zelf als wiki-pagina te archiveren (`wiki/topics/<slug>.md` of een vergelijkingspagina via `templates/_comparison.md`). Vraag dit altijd — archiveer niet automatisch.
5. Append een `query`-entry aan `log.md`.

Antwoordformaten naar behoefte: markdown-pagina, tabel, lijst, korte memo. Geen output forceren in chat als de gebruiker er een pagina van wil maken.

### 3.3 Lint

Op verzoek ("lint de wiki", "health check") of bij opvallende drift tijdens een ingest:

- **Contradicties** tussen pagina's — markeer met `⚠ contradictie` en koppel beide kanten.
- **Verouderde claims** die door nieuwere bronnen achterhaald zijn.
- **Wees-pagina's** zonder inkomende links.
- **Belangrijke concepten** die wel genoemd worden maar geen eigen pagina hebben.
- **Ontbrekende cross-references** waar `[[term]]` ontbreekt maar zou moeten staan.
- **Hiaten** in de dekking — onderwerpen waar het wiki dun is en een externe bron of webzoekopdracht zou kunnen helpen.

Rapport in chat; voer alleen wijzigingen door na akkoord van de gebruiker. Append een `lint`-entry aan `log.md`.

---

## 4. Index en log

### index.md

Inhoudsgericht. Catalogus van alle wiki-pagina's, gegroepeerd per type (Overview / Topics / Entities / Concepts / Sources / Comparisons). Per pagina: link, één regel samenvatting, optioneel datum en bronaantal.

De LLM werkt `index.md` bij **bij elke ingest** en **bij elke nieuwe pagina**.

### log.md

Chronologisch. Append-only. Elke entry begint met een vast prefix zodat `grep "^## \[" log.md` werkt:

```
## [JJJJ-MM-DD] ingest | <bron-titel>
## [JJJJ-MM-DD] query | <korte vraagomschrijving>
## [JJJJ-MM-DD] lint  | <reikwijdte>
```

Zie `templates/_log-entry.md` voor het body-formaat.

---

## 5. Paginaconventies

- **Frontmatter (YAML)** verplicht op elke wiki-pagina:
  ```yaml
  ---
  type: entity | concept | topic | source | comparison
  created: JJJJ-MM-DD
  updated: JJJJ-MM-DD
  sources: <aantal onderliggende bronnen>
  tags: [kebab-case, ...]
  ---
  ```
- **Wiki-links** via dubbele blokhaken: `[[wiki/concepts/spaced-repetition]]` of korter `[[spaced-repetition]]` als Obsidian het oplost.
- **Citaties** inline na een claim: `... volgens [[wiki/sources/karpathy-llm-wiki]]`. Vermijd losse voetnoten.
- **Contradictie-marker**: regel begint met `⚠ contradictie:` gevolgd door de tegenstrijdige claims en hun bronnen.
- Nooit een pagina aanmaken zonder ten minste één inkomende link uit `index.md` of een andere pagina.

---

## 6. Wat de LLM **niet** doet

- Niet schrijven in `raw/`.
- Geen pagina's verzinnen zonder bronbasis ("speculatie" mag, maar **expliciet gemarkeerd** als `> speculatie:` blockquote).
- Geen taxonomische bestandsnamen verzinnen voor onderwerpen waar de gebruiker een eigen register hanteert — vraag bij twijfel.
- Niet stilzwijgend wijzigen wat de gebruiker zelf in een wiki-pagina heeft geschreven; markeer mensbewerkingen en bespreek.
- Geen `--Force`-style blanket overschrijvingen van bestaande pagina's bij ingest. Voeg toe, herzie waar nodig, behoud geschiedenis.

---

## 7. Versiebeheer

Deze map is bedoeld om een git-repo te zijn. Initialiseer met `git init` op het juiste moment. Commits per ingest of per lint-sessie zijn natuurlijke eenheden. Commit-bericht-conventie:

```
ingest: <bron-titel>
query: <korte vraag>
lint:   <reikwijdte>
schema: <wijziging aan CLAUDE.md>
```

---

## 8. Bron van waarheid voor dit patroon

Het oorspronkelijke patroon staat in `raw/_seed/karpathy-llm-wiki.md`. Bij twijfel over de bedoeling van een conventie: lees daar.

---

## 9. Visuele deliverables — De Baak huisstijl

Wanneer een query of ingest leidt tot een **visuele deliverable** (HTML, slidedeck, infographic, PDF, poster, e-mail-template) die als Baak-output bedoeld is, geldt strict de canonieke huisstijl-spec:

`C:/Users/arijj/baakie-orchestrator/context/organisatie/debaak-huisstijl.md`

Regels:

- Lees die spec **vóór** je begint te schrijven of styleren. Niet improviseren.
- Raakt de deliverable een gebied dat in §9 *Open punten* van de spec staat (logo-bestand, fotografie, tone-of-voice, print-CMYK, …)? **Vraag** voor je doorgaat — niet invullen.
- Wijziging van de huisstijl zelf gebeurt **niet** vanuit dit wiki. Voorstel → decision-log in `baakie-orchestrator/memory/decision-log.md` → CHANGELOG-entry → pas dan spec aanpassen.

Voor niet-Baak-output (persoonlijke notities, generieke samenvattingen, neutrale tabellen) geldt deze regel niet.
