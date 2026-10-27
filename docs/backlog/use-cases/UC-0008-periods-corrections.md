# UC-0008 — Beginbalans, correcties en periodebeheer

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Eigenaar/boekhouder.
Scope: Boekjaar, beginbalans, afsluiten/heropenen en tegenboeken.
Afsluiten en heropenen gebeurt uitsluitend per volledig boekjaar; afzonderlijke
maandafsluiting valt buiten de eerste oplevering (besluit 27 oktober 2026).
Eerste oplevering: kalenderboekjaar van 1 januari t/m 31 december voor administraties (besluit 27 oktober 2026). Gebroken boekjaren volgen later via
[UC-0012](UC-0012-broken-financial-year.md).

Het concrete startboekjaar wordt later per administratie bij de inrichting bepaald;
er wordt nu geen startjaar aangenomen.

- AC-1: Een beginbalans is gebalanceerd en wordt eenmaal verwerkt; dubbele initialisatie wordt geweigerd.
- AC-2: Een afgesloten boekjaar accepteert geen nieuwe of gewijzigde boeking binnen
  dat jaar, ook niet bij gelijktijdig afsluiten en boeken. Maanden kunnen niet
  afzonderlijk worden afgesloten; maandrapportages blijven beschikbaar.
- AC-3: Een correctie behoudt de oorspronkelijke post en voegt een gekoppelde gebalanceerde tegenboeking toe; in een gesloten periode wordt niet stil teruggeboekt.
- AC-4: Heropenen van het volledige boekjaar vereist bevoegdheid en reden en legt
  actor/tijd vast; een medewerker of lezer kan dit niet.
- AC-5: Een jaarovergang neemt de vastgestelde slotstanden over zonder resultaat of beginstanden dubbel te tellen.
- AC-6: Het boekjaar loopt van 1 januari t/m 31 december. Een afwijkend boekjaar
  kan in de eerste oplevering niet worden ingesteld. De jaarovergang reset de
  mutatienummerreeks niet.

Afhankelijkheden: UC-0001, UC-0002, UC-0005.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Boekjaarmodel, openingsbalansproces, jaarovergang en correctiebeleid. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
