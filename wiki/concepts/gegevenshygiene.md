---
type: concept
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [privacy, avg, gegevensbeheer, ai-tools, governance]
aliases: [dataretentie, training op je data, zero data retention]
---

# Gegevenshygiëne

> **Citatieslug:** `[[wiki/concepts/gegevenshygiene]]`

## Eénregelige definitie

De praktijk om per gereedschap vast te leggen wat het met je gegevens mag doen — bewaren, op trainen, doorgeven — en dat bij te houden als een instelling met een datum, niet als een aanname.

## Uitgebreidere uitleg

Op **24 september 2026** is in drie gereedschappen tegelijk dezelfde knop omgezet: OpenRouter op Zero Data Retention voor alle modellen en aanbieders, met trainende aanbieders uit; Copilot met training op tekst- én spraakgesprekken uit; DeepSeek met *Verbeter het model voor iedereen* uit. Dat is geen toeval maar een ronde: iemand is die dag langs de modelkant gegaan en heeft hem dichtgezet. — [[wiki/sources/linkermenu-reeks]]

**Vier dagen later bleek de datakant open te staan.** Op 28 september meldt de Security Advisor van Supabase één fout: `RLS Disabled in Public`. Row Level Security staat uit op een tabel in het `public`-schema, dus iedereen met de openbare sleutel van de site — en die sleutel zit in de front-end van elke bezoeker — kan die tabel lezen en mogelijk wijzigen. Zie [[wiki/entities/supabase]].

Dat is het patroon dat deze pagina vasthoudt: **de zorg is toegepast op de gereedschappen die tekst verwerken, en niet op de plek waar de gegevens liggen.** Dichtgezette modelproviders en een open databasetabel zijn niet tegenstrijdig door onzorgvuldigheid maar door ongelijke aandacht. Het model dat je vraag leest voelt riskant; een tabel die stil op een server staat niet.

## Sleutelclaims

Alle standen uit [[wiki/sources/linkermenu-reeks]], met meetdatum:

| Gereedschap | Stand | Datum | Restrisico |
|---|---|---|---|
| OpenRouter | Zero Data Retention aan, trainende aanbieders uit | 2026-09-24 | sommige modellen vallen af; OpenRouter laat zien welke |
| Copilot | training op tekst en spraak uit | 2026-09-24 | blijft de **consumentenversie**; De Baak-werk hoort in Microsoft 365 Copilot met het werkaccount |
| DeepSeek | *Verbeter het model voor iedereen* uit | 2026-09-24 | gegevens worden volgens het privacybeleid (bijgewerkt 2026-02-10) **verwerkt en opgeslagen in China** — training uit verandert dat niet |
| ChatGPT | **niet nagegaan** | — | de bron draagt op te kijken onder *Instellingen → Gegevensbeheer*; dat is niet gedaan |
| Supabase | ⚠ RLS uit op een tabel in `public` | 2026-09-28 | leesbaar, mogelijk schrijfbaar met de publieke sleutel |
| Disco | deelnemerslijst met namen en profielen van trainers | 2026-09-28 | niet delen met AI-tools die op chats trainen; alleen exporteren als het nodig is |
| Apify | scrapers draaien in de cloud | 2026-09-24 | per site de voorwaarden controleren; geen persoonsgegevens zonder grondslag |

Twee claims die daaruit volgen:

- **Training uitzetten is niet hetzelfde als gegevens niet weggeven.** DeepSeek is het heldere geval: de knop staat goed en de gegevens staan in China. Een instelling dekt één risico, niet de verwerking zelf.
- **Een consumentenversie blijft een consumentenversie.** Copilot met training uit is nog steeds niet de plek voor De Baak-materiaal; daar hoort het zakelijke account bij.

## Voorbeelden

- De ronde van 24 september 2026 zelf: drie gereedschappen op één dag, en precies daarom als één feit vastgelegd in plaats van als drie losse.
- ⚠ **Het gat:** ChatGPT staat op *niet nagegaan*. Een Free-account waar De Baak-werk in gaat en waarvan de traininginstelling ongecontroleerd is, is de zwakste plek in dit rijtje — juist omdat de andere drie wél nagelopen zijn en het zo lijkt of de ronde compleet was.

## Verwarrend te onderscheiden van

- **Beveiliging** — gegevenshygiëne gaat over wat een dienst *mag* met gegevens die je bewust geeft; RLS in Supabase gaat over wie gegevens *kan* opvragen die je nooit hebt willen geven. De Supabase-bevinding staat hier omdat hij hetzelfde vak raakt, maar het is een ander soort fout.
- **AVG-compliance** — dit is de operationele laag eronder: welke knop staat waar, sinds wanneer. Geen juridische beoordeling.

## Wat hier ontbreekt: een check

Dit zijn zeven standen in zeven accounts, elk achter een knop die een mens heeft omgezet en die een aanbieder eenzijdig kan terugzetten bij een nieuwe versie of een nieuw plan. Er is niets dat merkt dat een van die knoppen omgaat. De enige reden dat we ze nu kennen is dat iemand ze op één dag heeft nagelopen en opgeschreven.

> speculatie: dit is een kandidaat voor dezelfde behandeling als de andere storingen in deze estate — een periodieke controle die afgaat als een stand verandert. Voor de meeste van deze zeven bestaat geen API om dat mee te lezen, dus het wordt vermoedelijk een gedateerde checklist en geen script. Dat is nog steeds beter dan geheugen.

## Open vragen

- Staat *Het model verbeteren voor iedereen* in ChatGPT aan of uit? Eén blik, en het gat is dicht.
- Wat staat er in de Supabase-tabel die open staat, en hoort daar überhaupt data in die niet publiek mag zijn?
- Traint Perplexity Enterprise Pro op organisatiedata? De bron zegt er niets over, en juist daar gaat het meeste onderzoek door.
- Welke modellen vallen af door Zero Data Retention, en mist er daardoor iets dat je nodig hebt?
- Hoe vaak moet deze tabel opnieuw nagelopen worden voordat hij fictie wordt?

## Cross-references

- Gemeten in: [[wiki/sources/linkermenu-reeks]]
- Raakt: [[wiki/entities/supabase]], [[wiki/entities/perplexity]], [[wiki/topics/gereedschapslandschap]]
- Relevant voor: [[wiki/topics/research-flow]] — al het onderzoeksmateriaal loopt door deze gereedschappen
