---
type: concept
created: 2026-05-20
updated: 2026-05-20
sources: 0
tags: [baakiekwal, werkwijze, assessment, canon-bridge, CRAFT]
aliases: [baakiekwal werkwijze, CRAFT rubrieken]
---

# Werkwijze van baakiekwal — brug naar orchestrator-canon

> **Citatieslug:** `[[wiki/concepts/baakiekwal-werkwijze]]`
>
> **Brug-pagina, geen duplicaat.** Dit is een dunne verwijzing. De feitelijke werkwijze, criteria en rubrieken van [[wiki/entities/baakiekwal]] zijn canoniek vastgelegd in `baakie-orchestrator/spaces/baakiekwal/` en horen daar te blijven. Deze pagina zorgt dat het wiki-netwerk een knoop heeft die naar die canon wijst.

## Waarom een brug, geen kopie

[[wiki/entities/baakiekwal]] werkt volgens een operationeel uitgewerkt rubrieken-systeem (CRAFT). Die uitwerking leeft in `baakie-orchestrator/spaces/baakiekwal/` met een eigen versie-historie, decision-log en empirische cold-test-resultaten. Kopiëren naar dit wiki creëert drift: twee waarheden die uit elkaar gaan lopen.

Karpathy's principe ([[wiki/concepts/three-layer-architecture]]) geldt hier op meta-niveau: de operationele canon is de "raw" voor dit wiki. Het wiki *synthetiseert*, maar zet niet over.

## Kern in één alinea

baakiekwal beoordeelt documenten aan de hand van **kwaliteitscriteria** en **rubrieken**. De drie functionele toetsings-criteria zijn [[wiki/concepts/auteursrecht-wetenschappelijk-werk]], [[wiki/concepts/bronvermelding]] en [[wiki/concepts/wetenschappelijke-kwaliteit]]. Daarnaast hanteert baakiekwal zes CRAFT-rubrieken (validiteit, betrouwbaarheid, herhaalbaarheid, transparantie, relevantie, ethiek) voor wetenschappelijke onderbouwing. Het assessment leidt tot een `validatie_status` per registerrij (Goedgekeurd / Afwijking / Geblokkeerd) en een kwaliteitsrapport.

## Canonieke bestanden in de orchestrator

Bestanden onder `C:\Users\arijj\baakie-orchestrator\spaces\baakiekwal\` waar het echte werk staat:

| Bestand | Inhoud |
|---|---|
| `baseline.md` | Rol-definitie, werkwijze, scope, grenzen, kennisbronnen |
| `knowledge/index.md` | Kennis-catalogus binnen de space |
| `knowledge/kwaliteitscriteria.md` | De toetsings-criteria zelf — incl. bron-attributie-conventie en pre-register-vorm |
| `knowledge/kwaliteitsbriefing-modellen.md` | Operationele CRAFT-prompt voor modellen-audits |
| `knowledge/kwaliteitsbriefing-modellen-bron.md` | Historische snapshot (Perplexity-pin, 2026-05-09) |
| `knowledge/kwaliteitsbriefing-redactioneel.md` | Briefing voor redactionele audits |
| `knowledge/rubriek-validiteit.md` | Volledig uitgewerkt |
| `knowledge/rubriek-ethiek.md` | Volledig uitgewerkt |
| `knowledge/rubriek-betrouwbaarheid.md` | Skeleton (zichtbare schuld) |
| `knowledge/rubriek-herhaalbaarheid.md` | Skeleton (zichtbare schuld) |
| `knowledge/rubriek-transparantie.md` | Skeleton (zichtbare schuld) |
| `knowledge/rubriek-relevantie.md` | Skeleton (zichtbare schuld) |
| `knowledge/voorbeeld-kwaliteitsrapport-modellen.md` | EN Step-4 + NL Step-5 voorbeeldrapport |
| `knowledge/voorbeeld-kwaliteitsrapport-redactioneel.md` | Placeholder voor redactioneel voorbeeld |

Stand 2026-05-20. Bij wijziging van de canonieke set: dit lijstje hier bijwerken (één regel) — niet de inhoud kopiëren.

## Wat dit wiki **wel** doet rond baakiekwal

- Per assessment-criterium één conceptpagina ([[wiki/concepts/auteursrecht-wetenschappelijk-werk]], [[wiki/concepts/bronvermelding]] *(placeholder)*, [[wiki/concepts/wetenschappelijke-kwaliteit]] *(placeholder)*) — gevuld met de **juridisch-inhoudelijke kennis** waarop baakiekwal leunt.
- Eén entity-pagina ([[wiki/entities/baakiekwal]]) — wat de agent is en doet op pipeline-niveau.
- Deze brug-pagina — als naviga-tor naar de operationele canon.

## Wat dit wiki **niet** doet

- Geen kopie van CRAFT-rubrieken-tekst.
- Geen kopie van prompt-templates.
- Geen kopie van voorbeeldrapporten.

Alleen verwijzen.

## Open vragen

- Als een rubriek-skeleton in de orchestrator-canon volwaardig wordt uitgewerkt, krijgt dit wiki dan een eigen conceptpagina voor die rubriek? Of blijft alles in de canon staan? Voorlopig: alleen pagina als externe bron de rubriek bespreekt, niet als reproductie van interne canon.
- Hoe gaan we ermee om als de orchestrator-canon en dit wiki tegelijk geraakt worden — bv. bij een nieuwe wet die zowel een wiki-bron als een baakiekwal-rubriek raakt? Vermoedelijk: kennis in wiki, operationalisering in canon, wederzijdse verwijzing.

## Cross-references

- Eigenaar: [[wiki/entities/baakiekwal]]
- Drie toetsings-criteria: [[wiki/concepts/auteursrecht-wetenschappelijk-werk]], [[wiki/concepts/bronvermelding]], [[wiki/concepts/wetenschappelijke-kwaliteit]]
- Vermeld in: [[wiki/topics/baakie-pipeline]]
- Patroon-verwant: huisstijl-verwijzing in `llm-wiki/CLAUDE.md §9` (zelfde principe: één canon, wiki verwijst)
