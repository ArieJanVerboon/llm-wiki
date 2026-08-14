---
type: concept
created: 2026-05-20
updated: 2026-05-20
sources: 1
tags: [sharepoint, workflow, documentmanagement, baakiedoc]
aliases: [SharePoint contentflow, document flow]
---

# SharePoint-contentflow

> **Citatieslug:** `[[wiki/concepts/sharepoint-contentflow]]`

## Eénregelige definitie

De zes-stappen-flow waarin De Baak-trainingscontent door SharePoint beweegt: van immutabel archief, via werkmap en Excel-register met metadata, naar een geborgde contentbibliotheek als single source of truth.

## De zes stappen

1. **Archief & bronmappen** — bestaande content in grote archiefmap (rechten: kopiëren, niet bewerken). Submappen per taakafkorting (bv. `Lap`, `PA`).
2. **Werkmap** — kopie uit archief voor bewerking en selectie (rechten: kopiëren, niet bewerken).
3. **Excel content-metadata register** — beheerd door document management. Bevat training-ID, functie, activiteit, onderwerp, modulelocatie, bestandstype + URL van de PDF in de bibliotheek.
4. **Materiaal klaarzetten** — bestanden hernoemd volgens [[wiki/concepts/naamgevingsconventie]] en omgezet naar gestandaardiseerde PDF's.
5. **Contentbibliotheek** — *single source of truth* voor trainingscontent. Versies gelockt door document management. Wie bewerken wil maakt een kopie.
6. **Werkinstructies & naamgeving** — werkafspraken: altijd vanuit Excel-register en bibliotheek werken, **nooit direct uit het archief**.

Visualisatie en bron: [[wiki/sources/documentbeheer-infographic]].

## Sleutelclaims

- Het archief is **immutabel** — kopiëren mag, bewerken niet. — [[wiki/sources/documentbeheer-infographic]]
- De contentbibliotheek is *single source of truth*; versie-lock ligt bij document management. — [[wiki/sources/documentbeheer-infographic]]
- Good practice: **werk altijd vanuit Excel-register en bibliotheek**, niet direct uit het archief. — [[wiki/sources/documentbeheer-infographic]]
- Elk gepubliceerd document krijgt één URL in de bibliotheek; die URL wordt geregistreerd in het Excel-register. — [[wiki/sources/documentbeheer-infographic]]

## Verbinding met dit wiki zelf

Dit patroon is **functioneel verwant** aan de drie-lagen-architectuur uit [[wiki/concepts/three-layer-architecture]]:

| SharePoint-flow | LLM Wiki-equivalent |
|---|---|
| Archief & bronmappen (immutabel) | `raw/` |
| Excel content-metadata register | `index.md` + register-pagina's |
| Contentbibliotheek (single source of truth) | `wiki/` |
| Werkinstructies | `CLAUDE.md` |

Niet identiek (SharePoint is operationeel/medewerker-gericht; LLM Wiki is kennis-gericht), maar de patroonverwantschap is leerzaam voor toekomstige cross-overs.

## Open vragen

- Hoe gaat de flow om met content die in meerdere bibliotheek-instanties moet leven (B1-hergebruik)?
- Verhouding tussen baakieprint's output-locaties en de bibliotheek-stap: produceert baakieprint *naar* de bibliotheek of *via* een werkmap?

## Cross-references

- Eigenaar: [[wiki/entities/baakiedoc]]
- Bron: [[wiki/sources/documentbeheer-infographic]]
- Verwante structuur: [[wiki/concepts/three-layer-architecture]]
- Vermeld in: [[wiki/topics/baakie-pipeline]]
