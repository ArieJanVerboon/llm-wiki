---
type: concept
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [naamgeving, taxonomie, baakiedoc, conventie]
aliases: [bestandsnaamconventie, file naming convention]
---

# Naamgevingsconventie voor De Baak-trainingscontent

> **Citatieslug:** `[[wiki/concepts/naamgevingsconventie]]`

## Eénregelige definitie

Bestandsnamen voor De Baak-trainingscontent volgen het patroon `<trainingafkorting>-<id>_<functie-activiteit>-<onderwerp>_<modulepositie>.<bestandstype>` waarbij elk veld op een gecontroleerde lijst is gebaseerd.

## Structuur

```
afkortingtraining + 3-cijferig ID + functie-activiteit + model-onderwerp_ + modulepositie.bestandstype
```

**Voorbeeld:** `PA-161_ho-in-ijsberg_m1p2.docx` — [[wiki/sources/debaak-dm-phase1]]

## Velden

| Veld | Wat | Voorbeeld | Canonieke lijst |
|---|---|---|---|
| **Afkorting training** | Per training, volgens taglijst | `PA` (Persoonlijk Adviseren) | `baakie-orchestrator/controlled-lists/trainingen.md` + `tax_trainingen`-tab |
| **3-cijferig training-ID** | Op basis van letterposities | `161` | idem (kolom in `tax_trainingen`) |
| **Functie & activiteit** | Functie-code (`pr`, `co`, `ho`, …) + LMS-activiteit | `ho-in` | `controlled-lists/functies.md` + `controlled-lists/activiteiten.md` |
| **Model & onderwerp** | 1–4 woorden | `ijsberg` | `controlled-lists/modellen.md` (voor model-namen) |
| **Modulepositie** | `mXpY` notatie (module + positie) | `m1p2` | vrije waarde, geen lijst |
| **Bestandsvorm** | docx, pdf, xlsx, jpg, png | `.docx` | `controlled-lists/bestandvormen.md` |

**Belangrijk:** dit wiki onderhoudt **geen** kopie van de taglijsten. De single source of truth zijn de markdown-snapshots in `baakie-orchestrator/controlled-lists/` (afgeleid van de `tax_*`-tabs in `registers/bibliotheek_register.xlsx`). Wijziging van een lijst: via xlsx → [`scripts/regenerate-controlled-lists.py`](file:///C:/Users/arijj/baakie-orchestrator/scripts/) → commit. Niet in dit wiki bewerken.

## Sleutelclaims

- Naamgevingsconventie is **gestandaardiseerd** — geen vrije tekst per veld. — [[wiki/sources/debaak-dm-phase1]]
- Standaardisatie van naamgeving levert beoogd 80% tijdsbesparing in zoeken op. — [[wiki/sources/debaak-dm-phase1]]
- Alle medewerkers volgen na invoering dezelfde afspraken (target: 100% adoptie na Fase 1). — [[wiki/sources/debaak-dm-phase1]]

## Verwarrend te onderscheiden van

- **Mapnaamgeving in SharePoint** ([[wiki/concepts/sharepoint-contentflow]]) — verschil: die gaat over locaties (archief / werkmap / bibliotheek), niet over bestandsnamen.
- **v0.3-baakieprint-interne naamgeving** voor prompts en drafts — die volgt een ander patroon (`[space]_[categorie]_[doel]_[taal]_[versie]`). v0.2-conventie hier is leidend voor *register-publicaties*; v0.3 voor *intern werk* binnen baakieprint. Spanning gedocumenteerd in `baakie-orchestrator/memory/decision-log.md` (entries 2026-05-09).

## Standpunten en debat

- Hergebruikte assets (één bestand, meerdere training-koppelingen): B1-conventie — één bestand op disk, meerdere rijen in het register met verschillende `filename_taxonomy` per training-koppeling. Niet in deze wiki-bron expliciet beschreven; canon staat in decision-log 2026-05-10.

## Open vragen

- Wat doet baakiedoc bij naamconflict tussen bestaande conventie en een uitzondering die de gebruiker wil?
- Volledigheid van `controlled-lists/trainingen.md` zelf — niet binnen dit wiki te beantwoorden; xlsx-edit voor baakiedoc.

## Cross-references

- Eigenaar: [[wiki/entities/baakiedoc]]
- Bron: [[wiki/sources/debaak-dm-phase1]]
- Vermeld in: [[wiki/topics/baakie-pipeline]]
