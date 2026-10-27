# OpenBookie — visie en scope — eerste oplevering

OpenBookie is een Nederlandse boekhoudapplicatie voor organisaties met uiteenlopende activiteiten
en rechtsvormen. De eerste oplevering richt zich op registreren, controleren en
rapporteren. Elke organisatie krijgt een logisch afgeschermde omgeving (tenant)
met administraties, leden en rechten; dit betekent geen afzonderlijke deployment.

## Doelgroep en toepasbaarheid

Het product is niet beperkt tot een specifieke sector, organisatie of rechtsvorm.
De term onderneming in bestaande documentatie omvat ook andere organisaties.
Rechtsvorm, activiteiten en fiscale kenmerken worden per organisatie vastgelegd;
ze worden niet afgeleid uit persoonlijke voorbeelden of één standaardprofiel.
De brede doelgroep betekent niet dat alle fiscale situaties al worden ondersteund:
de functionele en fiscale grenzen van de eerste oplevering staan hieronder.

## Boekhoudscenario's

Onderstaande categorieën zijn algemene, niet-uitputtende voorbeelden voor de
uitwerking van rekeningschema's; het zijn geen verplichte standaardrekeningen of
fiscale kwalificaties. Organisaties gebruiken passende standaard- en eigen rekeningen.

- Inkomsten: verkoop van goederen en diensten, sponsoring, donaties en giften,
  subsidies, toegangsopbrengsten, consumpties en prijzengeld.
- Uitgaven: materialen, huur van materieel, energie en water, deelnamekosten,
  promotiemateriaal en merchandise.
- Vrijwilligersvergoedingen moeten kunnen worden vastgelegd en geboekt, zowel
  declaraties van werkelijk gemaakte kosten tegen bonnetjes als vaste vergoedingen
  voor inzet. Beide vormen zijn bevestigd door `Carlovdv` op 26 oktober 2026.
  Voorlopig voert uitsluitend de aangewezen financieel verantwoordelijke beide vormen namens vrijwilligers
  in; zelf indienen door vrijwilligers valt buiten de eerste scope (bevestigd op
  26 oktober 2026). Deze verantwoordelijke mag deze zelf goedkeuren; akkoord van een
  andere bevoegde gebruiker is hiervoor niet vereist (bevestigd op dezelfde datum).
  Deze verantwoordelijke mag beide soorten vergoedingen ook zelf definitief boeken
  (bevestigd op 26 oktober 2026). De benodigde gegevens en controles per vrijwilliger
  staan nog open.
- Per vrijwilliger is een overzicht vereist met maand- en jaartotalen, afzonderlijk
  voor declaraties en vaste vergoedingen (bevestigd op 26 oktober 2026).
  Toon geboekte, daadwerkelijk uitbetaalde en nog openstaande bedragen afzonderlijk.
  De datumgrondslag, mee te tellen statussen en eventuele signaleringen moeten
  nog worden bepaald; het overzicht is op zichzelf geen fiscale toets.

Werk per scenario bronstukken, boekingswijze, rapportagerubriek en eventuele
btw-behandeling uit. Stel niet alleen op basis van de categorienaam een btw-regel
of kostenrekening vast. De behandeling van materialen en merchandise als kosten,
voorraad of bezitting vereist nadere uitwerking. Voorraadbeheer en een
vaste-activamodule blijven buiten scope. Vrijwilligersvergoedingen vallen binnen
de boekhoudscope; payroll en automatische loonberekening blijven uitgesloten.

## Binnen de eerste oplevering

- Onderneming en eerste administratie aanmaken, aanmelden en toegang beheren.
  Eén gebruikersaccount kan lid zijn van meerdere organisaties en binnen de
  applicatie tussen toegankelijke organisaties wisselen. De actieve organisatie
  en administratie zijn zichtbaar; toegang en rollen worden afzonderlijk bepaald.
  Iedere organisatie heeft een eigen team met meerdere gebruikers en rollen.
  De eerste rollen zijn Eigenaar, Admin, Finance, Medewerker en Viewer, volgens
  [het rollenmodel](../architecture/identity-access.md). Admin beheert de organisatie;
  financieel werk vereist Finance of Eigenaar. Developer, Support en custom rollen
  volgen pas bij een concrete behoefte en vallen voorlopig buiten de eerste oplevering.
- KOR-deelname vastleggen in de bedrijfsinstellingen met ingangsdatum en optionele
  einddatum, met behoud van de historie en uit te werken fiscale verwerking.
- Standaard grootboekrekeningschema toepassen en eigen rekeningen aanmaken/aanpassen.
- Facturen en bonnetjes uploaden, beoordelen en boeken met behoud van bronstukken.
  Ook elders gemaakte verkoopfacturen en creditnota's kunnen worden geregistreerd.
- Relaties, dagboeken, boekjaren, beginbalans en handmatige journaalposten.
  In de eerste oplevering loopt het boekjaar van 1 januari tot en met
  31 december (bevestigd op 27 oktober 2026). Gebroken boekjaren volgen in een
  later traject; zie [UC-0012](../backlog/use-cases/UC-0012-broken-financial-year.md).
- Bank-/kasmutaties handmatig registreren en betalingen, inclusief deelbetalingen,
  afletteren op openstaande posten. Eerst facturen of vrijwilligersvergoedingen
  boeken, daarna betalingen koppelen. Eén betaling kan meerdere facturen afwikkelen,
  bijvoorbeeld een maandelijkse verzamelbetaling; de verdeling blijft per post zichtbaar.
  Dit mag facturen van meerdere leveranciers betreffen, bijvoorbeeld een betaling
  aan een marketplace of moederbedrijf voor diensten van meerdere dochterbedrijven.
  De leverancier per factuur en de ontvanger van de betaling blijven afzonderlijk
  herleidbaar, binnen dezelfde administratie.
  Bij het koppelen aan facturen is het factuurnummer verplicht. Een betaalspecificatie,
  interne boekstukreferentie en factuur-/notabijlage (afbeelding of pdf) zijn optioneel,
  bevestigd op 27 oktober 2026. Met boekstuk wordt hier een interne referentie
  bedoeld, geen extra bijlage. Deze referentie wordt voorlopig handmatig ingevuld. De
  koppelreferentie voor posten zonder factuurnummer, zoals vrijwilligersvergoedingen,
  staan nog open.
  Een factuurnummer wordt binnen de administratie en leverancier beoordeeld;
  bij meerdere mogelijke posten moet de gebruiker de juiste post kiezen.
- Correctieboekingen en volledige boekjaren afsluiten/heropenen met rechten en
  audittrail. In de eerste oplevering geen afzonderlijke maandafsluiting (besluit
  27 oktober 2026); rapportages per maand of andere gekozen periode blijven mogelijk.
- Winst-en-verliesrekening per periode en balans op peildatum, met doorklik naar
  grootboek en bronstuk; proef-/saldibalans als controle.
- Herleidbaar btw-overzicht, basisexports, bronstukkenarchief en audittrail.
- Definitief geboekte financiële mutaties hebben een mutatienummer, datum, referentie en bedrag en
  zijn op elk van deze gegevens doorzoekbaar binnen de toegestane administratie.
  Facturen hebben daarnaast een relatie. Dit is bevestigd op 27 oktober 2026;
  mutatienummers worden pas bij definitief boeken automatisch, uniek en oplopend
  per administratie toegekend. Concepten hebben nog geen mutatienummer.
  De reeks loopt over boekjaren heen door; een nieuw boekjaar start geen nieuwe reeks.
  Een toegekend nummer is niet wijzigbaar en wordt nooit hergebruikt.
  Definitieve boekingen blijven onveranderlijk en worden gecorrigeerd via
  tegenboekingen met een eigen nieuw nummer; de oorspronkelijke post blijft behouden.
  Het nummerformaat en de precieze datum-, referentie- en
  bedragdefinities staan nog open.
- Inkoop van diensten, software en abonnementen bij buitenlandse leveranciers
  binnen de EU met verlegde btw; concrete scenario's
  en fiscale verwerking worden vóór implementatie gespecificeerd en gereviewd.

Facturen indienen betekent bestaande documenten verwerken. Facturatie betekent
zelf verkoopfacturen opstellen, nummeren en versturen; dat laatste valt buiten scope.
Upload alleen maakt nog geen definitieve boeking en bewijst geen btw-aftrekrecht.

## Authenticatie en autorisatie

Productie is passwordless: Entra ID via OpenID Connect/OAuth 2.0 en/of een
passwordless e-mailroute. De keuze voor één of beide routes en het MFA-beleid wordt
vóór productie vastgelegd. Alleen Development gebruikt initieel een vooraf vastgestelde
gebruikersnaam en wachtwoord. Deze uitzondering geeft geen vrijstelling van autorisatie.
Zie [identiteit en toegang](../architecture/identity-access.md).

## Buiten de eerste oplevering

Payroll/salarisverwerking, urenregistratie, offertes en facturatie. Ook uitgesloten:
automatische bankkoppelingen/bestandimport, OCR, Peppol, directe belastingaangifte,
voorraad, vaste-activamodule, vreemde valuta en accountantportaal. Geen automatische
loonberekening of loonintegratie als onderdeel van deze oplevering.

Eerste voorgestelde fiscale profiel: EUR, reguliere binnenlandse btw-plichtige
onderneming en factuurstelsel, aangevuld met KOR-deelname gedurende vastgelegde
geldigheidsperioden en inkoop van diensten, software en abonnementen binnen de EU
met verlegde btw. Buitenlandse goedereninkoop, inkoop buiten de EU,
kasstelsel, ICP, OSS,
overige verleggingssituaties, margeregelingen,
fiscale eenheden en inkomsten-/vennootschapsbelasting zijn nog niet ondersteund.
Tarieven, aftrek en bijzondere situaties vereisen officiële verificatie vóór implementatie.
Een btw-overzicht is geen ingediende aangifte. Niet-ondersteunde situaties worden gemeld
of geblokkeerd, nooit stilzwijgend als reguliere btw behandeld.

KOR en EU-inkoop met verlegde btw maken deel uit van de beoogde eerste oplevering;
dit vervangt hun eerdere algemene uitsluiting. Fiscale kenmerken en toepasselijke
regels moeten per organisatie en scenario worden vastgesteld. Werk voorwaarden,
datumgrenzen, boekingen, rapportages en overgangen vóór implementatie uit met
officiële bronnen en inhoudelijke review. Er wordt geen btw-status van een concrete
organisatie als productuitgangspunt vastgelegd.

De eerste oplevering ondersteunt EUR, binnenlandse verkoop en buitenlandse inkoop
van diensten, software en abonnementen binnen de EU. Buitenlandse verkoop,
buitenlandse goedereninkoop, niet-EU-inkoop en vreemde valuta blijven voorlopig
buiten scope. Deze afbakening betreft ondersteunde transacties, niet de doelgroep
of rechtsvorm van de organisatie.

## Acceptatie van de oplevering

Een gebruiker kan in zijn eigen onderneming bewijsstukken indienen, deze bevoegd
boeken op standaard/eigen rekeningen en de gevolgen in balans en winst-en-verlies
terugvinden. Openstaande posten, correcties, periodeafsluiting en export werken
herleidbaar. Een andere onderneming heeft geen toegang tot gegevens of bestanden.
Productieacceptatie omvat passwordless inloggen en het weigeren van de developmentlogin.
Zie de [backlog](../backlog/README.md) voor afzonderlijke, nog uit te werken use-cases.
