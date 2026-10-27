# UC-0009 — Bank, kas en openstaande posten

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Eigenaar/boekhouder.
Scope: Handmatig mutaties boeken en geheel/gedeeltelijk afletteren; geen bankkoppeling of import.
Inclusief openstaande facturen en vrijwilligersvergoedingen, en één betaling
verdelen over meerdere facturen (bevestigd op 26 oktober 2026). Dit betreft het
registreren en koppelen van betalingen, niet het uitvoeren van bankbetalingen.

- AC-1: Een handmatige bank-/kasmutatie resulteert in één gebalanceerde boeking bij retries.
- AC-2: Een deelbetaling vermindert exact de openstaande post; het resterende bedrag blijft zichtbaar.
- AC-3: Een volledige betaling sluit de post; overbetaling/verschil vereist expliciete verwerking en wordt niet weggeschreven.
- AC-4: Een foutieve koppeling kan herleidbaar worden gecorrigeerd zonder de oorspronkelijke financiële mutatie te verwijderen.
- AC-5: Een geboekte factuur of vrijwilligersvergoeding toont het geboekte bedrag,
  de gekoppelde betalingen en het resterende openstaande bedrag afzonderlijk.
- AC-6: Eén betaling kan met expliciete bedragen aan meerdere openstaande facturen
  worden gekoppeld, bijvoorbeeld alle facturen van een maand. Iedere post toont
  haar eigen afletteringen en restbedrag; de betaling wordt niet dubbel geboekt.
  De facturen mogen van verschillende leveranciers zijn binnen dezelfde administratie;
  de ontvanger van de betaling kan een marketplace of moederbedrijf zijn.
- AC-7: Toewijzingen die samen het beschikbare betaalbedrag overschrijden, dezelfde
  betaling dubbel verwerken of administratie-/tenantgrenzen overschrijden worden
  geweigerd. Gelijktijdige opdrachten of retries veroorzaken geen dubbele aflettering.
- AC-8: Bij een verzamelbetaling over meerdere leveranciers blijven per factuur
  de oorspronkelijke leverancier, het toegewezen bedrag en de koppeling naar de
  betaling zichtbaar. De betaalontvanger is afzonderlijk herleidbaar; leveranciers
  worden niet samengevoegd en factuurgegevens worden niet overschreven.
- AC-9: Bij koppeling van een betaling aan een factuur is het factuurnummer
  verplicht. Het nummer wordt binnen de juiste administratie en leverancier gebruikt
  om de geboekte post te vinden; bij ambiguïteit wordt niet automatisch gekoppeld.
  De opgeslagen toewijzing verwijst naar de concrete post, niet alleen het nummer.
- AC-10: Een gebruiker kan een optionele interne boekstukreferentie handmatig invullen en
  een betaalspecificatie of factuur-/notabijlage (afbeelding of pdf) toevoegen.
  De boekstukreferentie is geen extra document. Ontbreken hiervan blokkeert een overigens geldige
  betalingstoewijzing niet. Toegevoegde bestanden vallen onder de bestaande
  uploadbeveiliging, toegangscontrole en bewaarbeleid.

Aanvullend testplan: verzamelbetaling van twee facturen, gedeeltelijke afwikkeling,
resterend niet-toegewezen betaalbedrag, meerdere betalingen op één post, correctie,
rollback en concurrerende toewijzingen. Gebruik onafhankelijk berekende totalen.
Test ook twee facturen van verschillende leveranciers met één betaling aan een
marketplace of moederbedrijf, inclusief behoud van leverancier en betaalontvanger.
Betaalspecificatie, interne boekstukreferentie en factuur-/notabijlage zijn optioneel volgens het
besluit van 27 oktober 2026. Test koppelen zonder bijlage, ontbreken van het verplichte
factuurnummer en hetzelfde factuurnummer bij verschillende leveranciers.
Betalingsmutaties zijn doorzoekbaar op mutatienummer, datum, referentie en bedrag
volgens het gedeelde contract uit [UC-0002](UC-0002-journal.md).
Nog vast te stellen: formaat en uniciteit van de interne boekstukreferentie, referentie voor posten
zonder factuurnummer (waaronder vrijwilligersvergoedingen), datumgrondslag en peildatum
van openstaande posten, en verwerking van verschillen. Een ontbrekend extern nummer
wordt niet verzonnen; de nummerloze scenario's moeten vóór Ready worden uitgewerkt.

Afhankelijkheden: UC-0002, UC-0006, UC-0008.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Verschillen/overbetalingen, ontkoppeling, relaties en toegestane aflettercombinaties. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
