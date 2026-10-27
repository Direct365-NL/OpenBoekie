# UC-0007 — Winst-en-verliesrekening en balans

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Eigenaar, boekhouder en lezer.
Scope: Periode-/peildatumrapportage, proef-/saldibalans en grootboekkaarten.
Aanvullend: vrijwilligersvergoedingen per vrijwilliger, maand en jaar, met aparte
totalen voor declaraties en vaste vergoedingen (scopebesluit 26 oktober 2026).

- AC-1: Een winst-en-verliesrekening neemt alleen definitieve opbrengsten en kosten in de gekozen periode op en sluit aan op het grootboek.
- AC-2: Een balans op peildatum bevat beginstanden en definitieve mutaties tot die datum; activa sluiten aan op passiva inclusief eigen vermogen en verwerkt resultaat.
- AC-3: Lopend resultaat en jaarafsluiting worden niet dubbel meegeteld; een latere boeking wijzigt geen eerdere peildatum.
- AC-4: Elke rubriek is herleidbaar tot grootboekregels en beschikbare bronstukken; eigen rekeningen worden volgens hun classificatie meegenomen.
- AC-5: Een synthetische referentieadministratie met beginbalans, inkoop, omzet, deelbetaling en correctie geeft onafhankelijk vooraf berekende rapporten.
- AC-6: Een bevoegde gebruiker kan binnen de eigen administratie per vrijwilliger
  maand- en jaartotalen bekijken, afzonderlijk voor declaraties en vaste vergoedingen,
  met afzonderlijke geboekte, daadwerkelijk uitbetaalde en openstaande bedragen
  en herleiding naar de onderliggende registraties en betalingstoewijzingen.

Het boekjaar is in de eerste oplevering gelijk aan het kalenderjaar
(1 januari t/m 31 december); gebroken boekjaren volgen later via UC-0012.
Voor AC-6 nog nodig vóór Ready: datumgrondslag, mee te tellen
statussen, correctieverwerking en inzagerechten (waaronder de aangewezen financieel verantwoordelijke).
Aanvullende afhankelijkheden: vrijwilligersregistraties uit UC-0006 en betalingen
en afletteringen uit UC-0009. Test meerdere vrijwilligers, beide vergoedingstypen,
maand-/jaargrenzen, correcties en geweigerde toegang met synthetische gegevens en
onafhankelijk berekende totalen. Eventuele fiscale signaleringen zijn nog niet besloten.
Test ook boeking en betaling in verschillende maanden, deelbetalingen en
openstaande bedragen op de gekozen peildatum; vermeng periodemutaties en standen niet.

Afhankelijkheden: UC-0001, UC-0002, UC-0005, UC-0008.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Tekenconventie, datumbereik, resultaatbestemming, jaargrenzen en referentiebedragen. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
