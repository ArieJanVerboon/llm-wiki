---
type: entity
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [gereedschap, kennisbank, research-flow, markdown, sync]
entity_kind: product
aliases: []
---

# Obsidian

> **Citatieslug:** `[[wiki/entities/obsidian]]`

## Wat is het

Programma dat een map met markdown-bestanden als kennisbank toont: bestandsverkenner, zoeken, grafiekweergave, opdrachtenpalet. In de [[wiki/topics/research-flow]] is dit de leesbril op dit wiki — Claude Code schrijft, Obsidian leest.

## Belangrijke feiten

Stand 2026-09-24, waargenomen op de eigen computer — [[wiki/sources/linkermenu-reeks]] (Obsidian):

- Versie **1.13.7**, met **dit llm-wiki als kluis**.
- **Obsidian Sync staat uit** (het icoon is doorgestreept). Synchronisatie loopt via GitHub, met `git pull` vooraf en `git push` achteraf, op elke computer.
- De instellingen van de kluis staan in `.obsidian`, en die map gaat mee in de repo. Instellingen zijn dus bestanden, en ze reizen mee.
- De grafiekweergave laat zien welke pagina's los hangen — de bron noemt dat expliciet als aanvulling op de **lint**-operatie uit [[wiki/concepts/ingest-query-lint]].
- Nieuwe bronnen toevoegen gaat zo: in `raw/` zetten en Claude Code een ingest laten doen. Dat is de handmatige stap waar [[wiki/topics/research-flow]] op stukloopt.
- Provenance-kanttekening op de pagina zelf: de namen in het lint komen uit de standaardinstellingen, de tooltips waren niet uit te lezen.

## ⚠ contradictie: waar staat de kluis?

De bron plaatst de kluis op **`C:\arijj\llm-wiki`** — zowel in de hero als bij het advies *"git pull en git push in C:\arijj\llm-wiki"*.

Die map bestaat niet. Nagegaan op 2026-09-29: onder `C:\arijj` staat alleen `Visma`. De kluis en de git-clone staan op **`C:\Users\arijj\llm-wiki`**, en daar staat ook `.obsidian`.

Wie het advies uit de bron letterlijk volgt, opent dus een kluis die er niet is en doet `git pull` in een map die niet bestaat. Vermoedelijke verwarring met `C:\arijj\Visma`, dat wél onder die wortel staat. De bron blijft ongewijzigd — `raw/` is immutabel — en deze pagina is de correctie.

## Kluisinhoud: kleine drift

De bron schetst de kluisboom als `public · published · raw · review · templates · wiki`, met `CLAUDE · index · log · HOWTO · ELI10 · README · SYNC`. Op 2026-09-29 staan `public/`, `raw/`, `review/`, `templates/`, `wiki/` en alle zeven bestanden er nog; `published/` niet, en er zijn `MOCs/` en een `Untitled/` bijgekomen. Niet verontrustend, wel het bewijs dat een kaart van een kluis net zo veroudert als een kaart van een menu.

## Twee computers, twee regimes

De bron beschrijft synchronisatie als handwerk. Maar log-entry **2026-09-24 schema** in dit wiki vermeldt dat op `DESKTOP-NJV6J3J` Obsidian Git is ingesteld op pull bij opstarten en elke 10 minuten automatisch pull en commit-and-sync — met als volgende stap: hetzelfde op de andere computer.

Die twee staan dus niet gelijk: op de ene machine synchroniseert het zichzelf elke tien minuten, op de andere alleen als iemand eraan denkt. Dat is precies de opstelling waarin het conflict ontstaat waar de bron voor waarschuwt. Zolang dat verschil bestaat, is `git pull` vóór je begint geen advies maar een voorwaarde.

## Relaties

- Leest: `wiki/` en `raw/` van dit llm-wiki — zie [[wiki/concepts/three-layer-architecture]]
- Complementair aan: [[wiki/concepts/ingest-query-lint]] (grafiekweergave naast lint)
- Synchroniseert via: GitHub
- Eindpunt van: [[wiki/topics/research-flow]]

## Open vragen

- Staat Obsidian Git nu op beide computers, of nog maar op één?
- Wat staat er in `public/` en `review/`, en hoort `review/` bij de tag `ingested:review` uit [[wiki/entities/zotero]]?
- Waar komt `C:\arijj\llm-wiki` uit? Is er ooit een tweede clone geweest?

## Cross-references

- Genoemd in: [[wiki/sources/linkermenu-reeks]], [[wiki/topics/research-flow]]
