---
type: topic
created: 2026-05-20
updated: 2026-05-20
sources: 3
tags: [baakie, pipeline, architectuur, documentmanagement, debaak]
thesis_status: opening
---

# De Baakie-pipeline

> **Citatieslug:** `[[wiki/topics/baakie-pipeline]]`

Het overkoepelende onderwerp dat de architectuur en werking van het document-managementproces van [[wiki/entities/de-baak]] beschrijft.

## Huidige these

De Baakie-pipeline is een driestaps-keten van LLM-subagenten waarin trainingscontent achtereenvolgens wordt **gestructureerd** (baakiedoc), **getoetst** (baakiekwal) en **gepubliceerd** (baakieprint). Eén immutabel archief, één Excel-register als boekhouding, één contentbibliotheek als single source of truth, en één huisstijl die alle visuele output bindt. De keten reflecteert dezelfde drie-lagen-discipline (raw / wiki / schema) als het [[wiki/concepts/llm-wiki-pattern]], toegepast op een operationele in plaats van kennis-context.

_Stand per 2026-05-20 — gebaseerd op drie bronnen + orchestrator-canon._

## De drie agenten

```
   Ruwe content (archief)
            │
            ▼
   ┌────────────────────┐
   │  baakiedoc         │  Naamgeving + register
   │                    │  → [[wiki/concepts/naamgevingsconventie]]
   │                    │  → [[wiki/concepts/sharepoint-contentflow]]
   └─────────┬──────────┘
             ▼
   ┌────────────────────┐
   │  baakiekwal        │  Assessment
   │                    │  ├─ [[wiki/concepts/auteursrecht-wetenschappelijk-werk]]
   │                    │  ├─ [[wiki/concepts/bronvermelding]]
   │                    │  └─ [[wiki/concepts/wetenschappelijke-kwaliteit]]
   └─────────┬──────────┘
             ▼
   ┌────────────────────┐
   │  baakieprint       │  Publicatie-output
   │                    │  (print, slides, HTML, infographic via skeletons)
   └────────────────────┘
            │
            ▼
   Contentbibliotheek (single source of truth)
```

**Buiten deze pipeline:** [[wiki/entities/baakiedoc]] kan ook autonoom werken (taxonomie-onderhoud zonder downstream-trigger); `baakiened` (tekstproductie/redactie) bestaat als zelfstandige agent maar speelt geen rol in deze keten.

## Wat we weten

- Pipeline draait op drie agenten sinds 2026-05-20; voormalige `baakiehtml` is samengevoegd met [[wiki/entities/baakieprint]] omdat beide hetzelfde skeleton-mechanisme gebruiken. — canon: `baakie-orchestrator/CLAUDE.md` + decision-log 2026-05-20
- Fase 1 van invoering is een 8-weeks 3-stappen-proces: inventarisatie → naamgevingsconventie definiëren → migratie + lancering. — [[wiki/sources/debaak-dm-phase1]]
- De SharePoint-flow heeft zes stappen, geconcentreerd rond de Excel-metadata-register als spil. — [[wiki/sources/documentbeheer-infographic]]
- Assessment door baakiekwal toetst expliciet **drie** criteria: auteursrecht, bronvermelding, wetenschappelijke kwaliteit. — gesprek met AV (canonieke uitspraak) + [[wiki/sources/auteursrecht-wetenschappelijk-werk]] voor één van die drie
- Huisstijl is canoniek in één spec-bestand (`baakie-orchestrator/context/organisatie/debaak-huisstijl.md`) en bindt alle visuele output van baakieprint. — canon

## Wat we vermoeden

> speculatie: de pipeline schaalt verder zonder structuurwijziging zolang nieuwe assessment-criteria binnen baakiekwal kunnen worden ingeplugd en nieuwe formats binnen baakieprint via skeletons. Wanneer een nieuw soort werk (bijvoorbeeld video) een fundamenteel andere governance vraagt, kan een vierde agent verschijnen. Niet bevestigd door bronnen.

> speculatie: de drie-agenten-architectuur is een eindstaat van een eerder vijf-agenten-ontwerp; verdere consolidatie naar twee of één lijkt niet wenselijk (assessment vs. productie is een eerlijke separation of concerns).

## Wat omstreden is

- **Geen interne contradicties** tussen de huidige drie ingest-bronnen.
- ⚠ Een achterhaald 10-fasenplan (`raw/_archief/document-management-10-fasen-plan.html`) suggereerde een veel zwaardere structuur (22 weken, 10 fasen, 6 trainingen). Buiten canon sinds 2026-05-20. Niet ingest in dit wiki; bewaard als historische evidentie conform Karpathy-principe.

## Belangrijkste entiteiten

- [[wiki/entities/de-baak]] — eigenaar
- [[wiki/entities/baakiedoc]] — schakel 1
- [[wiki/entities/baakiekwal]] — schakel 2
- [[wiki/entities/baakieprint]] — schakel 3
- [[wiki/entities/anewspring]] — LMS, output-target voor HTML-content uit baakieprint

## Belangrijkste concepten

- [[wiki/concepts/naamgevingsconventie]] — input-discipline van baakiedoc
- [[wiki/concepts/sharepoint-contentflow]] — operationele drager
- [[wiki/concepts/auteursrecht-wetenschappelijk-werk]] — assessment-criterium 1
- [[wiki/concepts/bronvermelding]] — assessment-criterium 2 *(placeholder)*
- [[wiki/concepts/wetenschappelijke-kwaliteit]] — assessment-criterium 3 *(placeholder)*
- [[wiki/concepts/baakiekwal-werkwijze]] — brug naar operationele canon in `baakie-orchestrator/spaces/baakiekwal/`

## Evolutie van de these

- 2026-05-20 — these geopend op basis van drie ingeste bronnen + orchestrator-canon. Architectuur per vandaag: drie agenten, twee placeholders voor assessment-criteria 2 en 3.

## Open vragen

- Beslisregels per assessment-criterium — staan in `baakie-orchestrator/spaces/baakiekwal/`, niet in dit wiki. Brug nodig?
- Skeleton-set voor baakieprint na de merge met baakiehtml — nog niet als coherent geheel gedocumenteerd.
- Hoe gaat de pipeline om met content die op meerdere trainingen draait (B1-hergebruik)?
- Trainingsabkortingen — canonieke complete lijst niet in dit wiki.

## Cross-references

- Verwante structuur (kennis i.p.v. operationeel): [[wiki/concepts/llm-wiki-pattern]], [[wiki/concepts/three-layer-architecture]]
- Bronnen die dit onderwerp dragen: [[wiki/sources/debaak-dm-phase1]], [[wiki/sources/documentbeheer-infographic]], [[wiki/sources/auteursrecht-wetenschappelijk-werk]]
