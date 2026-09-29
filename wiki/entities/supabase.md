---
type: entity
created: 2026-09-29
updated: 2026-09-29
sources: 1
tags: [gereedschap, database, beveiliging, openstaand]
entity_kind: product
aliases: []
---

# Supabase

> **Citatieslug:** `[[wiki/entities/supabase]]`

## Wat is het

Postgres-database in de cloud, met inloggen, bestandsopslag en API's erbij. Twee niveaus: de organisatie en daaronder de projecten. Draagt de portfolio-site.

## ⚠ Openstaande bevinding: RLS uit in `public`

Stand 2026-09-28, waargenomen in de organisatie *Theinspreadables* (gratis plan) — [[wiki/sources/linkermenu-reeks]] (Supabase):

De Security Advisor meldt **1 fout, 9 waarschuwingen en 2 suggesties**. De fout is `RLS Disabled in Public`: Row Level Security staat uit op een tabel in het `public`-schema.

Waarom dat telt: de publieke (anon) sleutel van een Supabase-project zit per definitie in de front-end van de site. Iedere bezoeker heeft hem. Zonder RLS is er niets dat per rij bepaalt wie mag lezen of schrijven — dus is die tabel leesbaar, en afhankelijk van de rechten ook schrijfbaar, voor iedereen die de site opent en de sleutel uit de pagina haalt.

De bron vermeldt uitdrukkelijk dat er niets is veranderd. **Status per 2026-09-29: open.** Dit is geen automatiseringskwestie maar een besluit: RLS aanzetten en een policy schrijven voor wie mag lezen en schrijven raakt een live database, en dat hoort AV zelf te doen of expliciet op te dragen.

## Tweede bevinding: geen vangnet

Ook op 2026-09-28: **geen GitHub-koppeling, geen migraties, geen back-ups.** Het gratis plan biedt geen terugzetbare back-up. Dat maakt de eerste bevinding zwaarder dan hij op zichzelf is: staat een tabel open én is er geen back-up, dan is een verkeerde write niet terug te draaien.

De bron noemt twee tegenmaatregelen: het schema onder versiebeheer brengen via *Integrations → GitHub* (migraties), en zelf een export maken.

## Belangrijke feiten

- Organisatie *Theinspreadables*, gratis plan. — [[wiki/sources/linkermenu-reeks]]
- Onderdelen die in gebruik zijn: Project Overview, Table Editor en SQL Editor, Authentication, Advisors, Project Settings, Integrations.
- Onder *Project Settings* staan de API-sleutels, het databasewachtwoord, back-ups en de knoppen om het project te pauzeren of te verwijderen.
- De bron noemt Cloudflare D1 als alternatief voor een kleine database naast een Worker — relevant omdat de rest van de estate op Cloudflare staat.

## Relaties

- Alternatief binnen de estate: Cloudflare D1
- Onder toezicht van: [[wiki/concepts/gegevenshygiene]] — daar staat deze bevinding naast de modelinstellingen, en daar staat ook waarom die twee ongelijk behandeld zijn
- Genoemd in: [[wiki/topics/gereedschapslandschap]]

## Open vragen

- Welke tabel staat open, en hoort daar data in die niet publiek mag zijn? Dat bepaalt of dit een haastklus is of administratie.
- Wat zijn de 9 waarschuwingen? De bron telt ze maar noemt ze niet.
- Draagt dit project alleen de portfolio-site, of hangt er meer aan?
- Waarom Supabase én Cloudflare D1 in één estate — is dat een keuze of een restant?

## Cross-references

- Genoemd in: [[wiki/sources/linkermenu-reeks]], [[wiki/concepts/gegevenshygiene]], [[wiki/topics/gereedschapslandschap]]
