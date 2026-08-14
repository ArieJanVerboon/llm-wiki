# Log-entry templates

Elke entry in `log.md` begint met een kopregel volgens een vast formaat zodat de log parseerbaar blijft.

Kopformaat:

```
## [JJJJ-MM-DD] <operatie> | <reikwijdte>
```

`operatie` is één van: `ingest`, `query`, `lint`, `schema`.

---

## Ingest

```markdown
## [JJJJ-MM-DD] ingest | <bron-titel>

**Bron:** `raw/<map>/<bestand>` — <type> — <auteurs indien bekend>
**Samenvattingspagina:** [[wiki/sources/<slug>]]

**Geraakte pagina's:**
- [[wiki/entities/<slug>]] — <wat veranderde>
- [[wiki/concepts/<slug>]] — <wat veranderde>
- [[wiki/topics/<slug>]] — <wat veranderde>

**Nieuwe pagina's:**
- [[wiki/<map>/<slug>]] — <waarom nieuw>

**Contradicties geïntroduceerd of opgelost:**
- ⚠ <bron A> versus <bron B> over <onderwerp> — gemarkeerd in [[wiki/...]]

**Open vragen toegevoegd:**
- <vraag>
```

---

## Query

```markdown
## [JJJJ-MM-DD] query | <korte vraagomschrijving>

**Vraag (letterlijk):** <citaat van de vraag van de gebruiker>

**Pagina's geraadpleegd:**
- [[wiki/...]]
- [[wiki/...]]

**Antwoordvorm:** chat | wiki-pagina | tabel | slidedeck | overig

**Gearchiveerd als:** [[wiki/topics/<slug>]] of [[wiki/comparisons/<slug>]] — of: niet gearchiveerd.

**Nieuwe vragen die hieruit volgden:**
- <vraag>
```

---

## Lint

```markdown
## [JJJJ-MM-DD] lint | <reikwijdte>

**Reikwijdte:** volledige wiki | <map> | <thema>

**Bevindingen:**
- Contradicties: <aantal> — zie [[wiki/...]], [[wiki/...]]
- Wees-pagina's: <aantal> — <namen>
- Concepten zonder pagina: <aantal> — <termen>
- Verouderde claims: <aantal> — <pagina's>
- Ontbrekende cross-references: <aantal>
- Dekkingshiaten: <thema's waar het wiki dun is>

**Akties uitgevoerd (na akkoord):**
- <actie> in [[wiki/...]]

**Akties uitgesteld:**
- <actie> — reden
```

---

## Schema

```markdown
## [JJJJ-MM-DD] schema | <wijziging>

**Wijziging in `CLAUDE.md`:** <korte beschrijving>

**Aanleiding:** <waarom — vaak een patroon dat tijdens gebruik opkwam>

**Effect op bestaande pagina's:** geen | <welke pagina's moeten retroactief worden bijgewerkt>
```
