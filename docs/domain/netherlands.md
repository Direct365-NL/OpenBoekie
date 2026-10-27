# Nederlandse fiscale uitwerking

Status: uitgangspunten; nog geen gevalideerde fiscale implementatie.
KOR is sinds het scopebesluit van 26 oktober 2026 onderdeel van de beoogde eerste
oplevering: deelname wordt vastgelegd met ingangsdatum en optionele einddatum.
Voorwaarden voor deelname, datumtoepassing, gevolgen voor btw en aftrek, overgang
en correcties zijn nog te specificeren met officiële bronnen en inhoudelijke review.
De instelling is geen automatische beoordeling of aanmelding voor de regeling.
De [officiële bronnen](../product/references.md) gaan vóór vergelijkingsproducten.

## Eisen en verificatie

Buitenlandse inkoop met verlegde btw valt sinds het scopebesluit van 26 oktober
2026 binnen de beoogde eerste oplevering, beperkt tot diensten, software en
abonnementen bij leveranciers binnen de EU. Buitenlandse goedereninkoop en inkoop
buiten de EU vallen voorlopig buiten scope. Specificeer per ondersteund scenario
de toepassingsvoorwaarden, benodigde bewijsgegevens, berekening, eventuele aftrek,
rapportagerubricering en correcties. Leid behandeling niet uitsluitend
af uit een leveranciersnaam. Onderbouw dit vóór implementatie met officiële bronnen
en inhoudelijke review. Werk ook de eventuele samenloop met KOR expliciet uit;
ontbrekende ondersteuning mag niet stilzwijgend tot reguliere btw-verwerking leiden.

| Onderwerp | Ontwerpvereiste | Benodigd bewijs vóór vrijgave |
| --- | --- | --- |
| Reguliere factuur | Identiteit/adres partijen, identificatienummers waar vereist, datum, unieke reeks, prestatie, bedragen en btw | Veldmatrix tegen actuele factuureisen; positieve en negatieve voorbeelden |
| Btw | Regelversie met ingangsdatum, categorie en toepassingsvoorwaarden | Officiële bron en gereviewde rekenscenario's |
| Afronding | Eén expliciet consistent beleid per document, exacte decimalen | Grensgevallen, meerdere regels, kortingen en creditnota's |
| Btw-overzicht | Herleidbaarheid van rubriek naar boeking, periode en correctie | Afstemming met grootboek en inhoudelijke review |
| Bewaring | Beleid per documentcategorie, startmoment en uitzondering | Bewaarmatrix en geslaagde lees-/export-/herstelproef |
| Uitzonderingen | Ondersteuning expliciet of invoer blokkeren | Tests voor niet-ondersteunde scenario's |

Bewaartermijnen zijn niet één universele verwijderdatum: doorgaans zeven jaar,
met onder meer tienjarige uitzonderingen. Ook het beginmoment en de blijvende
bruikbaarheid van gegevens vereisen aandacht. Leid nooit enkel uit aanmaakdatum
of opzegging van een abonnement af dat gegevens mogen worden verwijderd.
Zie de brochure en overheidsinformatie in de bronnenlijst voor de onderbouwing.

## Fiscaal regelrecord (te specificeren per use-case)

Vermeld regel-ID, scenario en uitsluitingen, bron-URL, raadpleegdatum, geldig-vanaf/tot,
berekeningsbasis, precisie/afronding, voorbeeldinvoer/-uitvoer, reviewer en test-ID's.
Historische boekingen behouden hun oorspronkelijke toegepaste versie. Een wijziging
werkt niet ongemerkt terug in afgesloten tijdvakken. Beoordeel correcties afzonderlijk.

Geen aangifte-indiening of claims over volledige Nederlandse fiscale dekking voordat
de betreffende integratie, scenario's en inhoudelijke validatie zijn afgerond.


## Toepassing in de eerste oplevering

We stellen geen facturen op. Factuureisen dienen nu voor beoordeling en registratie
van ingediende facturen, bonnetjes en externe creditnota's. Bewaar het originele
bronstuk; een ontbrekend gegeven wordt niet door ons verzonnen. Beoordeel afzonderlijk
of een stuk geboekt kan worden en of btw aftrekbaar is; een bon is niet automatisch
ongeldig en een geslaagde upload geeft niet automatisch recht op aftrek. De exacte
controle- en blokkaderegels vragen fiscale review. Nummeruitgifte en factuurverzending
behoren pas bij een latere facturatie-use-case.
