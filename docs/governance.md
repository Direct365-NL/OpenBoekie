# Eigenaarschap en besluiten

De projectverantwoordelijke, GitHub-gebruiker `Carlovdv`, is voorlopig de enige contributor, maintainer en
productverantwoordelijke en draagt de eindverantwoordelijkheid voor het project.
De verantwoordelijkheden en de te vermelden GitHub-gebruikersnaam zijn bevestigd
door de repository-eigenaar op 26 oktober 2026.

Zolang er één maintainer is, vindt technische review plaats als een afzonderlijke,
vastgelegde zelfreview volgens [CONTRIBUTING.md](../CONTRIBUTING.md).
Concrete reviewers en operationele rollen worden vóór samenwerking ingevuld.
Een bevoegde boekhoudkundige reviewer valideert fiscale interpretaties vóór vrijgave.

Voorlopig verzorgt `Carlovdv` de inhoudelijke uitwerking op basis van eigen expertise
en de [geselecteerde kennisbronnen](product/references.md): Belastingdienst,
Kamer van Koophandel, overheidsinformatie, Ondernemersplein en Informer Wiki.
Deze werkwijze en bronnenkeuze zijn bevestigd op 26 oktober 2026. Voor fiscale regels blijven officiële
bronnen leidend volgens [Nederlandse fiscale uitwerking](domain/netherlands.md).
Leg bronnen en interpretaties herleidbaar vast. Een boekhoudkundige reviewer moet
nog bij het project worden betrokken. Deze tijdelijke werkwijze vervangt niet de
vereiste inhoudelijke review voor Ready-goedkeuring of fiscale vrijgave.

| Besluit | Moment | Status |
| --- | --- | --- |
| Productnaam, domein en GitHub-locatie | Vastgelegd 27 oktober 2026 | OpenBookie; openbookie.nl; Direct365-NL/OpenBoekie |
| OSI-licentie (bijv. AGPL-3.0-only of Apache-2.0) | Vóór publieke publicatie | Open; gevolgen voor SaaS en bijdragen afwegen |
| Frameworks, Node/runtime, package manager, database | Eerste implementatie | Open; ADR met ondersteunde versies |
| Hosting, regio, verwerkers, secretsbeheer | Vóór Test uitrol | Open |
| Fiscale scope en inhoudelijk reviewer | Vóór fiscale implementatie | Open; voorgestelde scope in product/vision.md; voorlopige uitwerking door Carlovdv, reviewer nog te betrekken |
| Private securitymeldingen en onderhoudsbeleid | Vóór publieke publicatie | Open |
| RPO, RTO, capaciteit en beschikbaarheidsdoelen | Vóór Acceptatie | Open; geen SLA toegezegd |

Gebruik ADRs voor duurzame keuzes. Een voorstel wordt pas Accepted na vastgelegde
review; vermeld datum en beslisser. Bibliotheeklicenties moeten passen bij de gekozen
projectlicentie. Een contributor bevestigt bevoegd te zijn om bijdragen aan te leveren.
Voeg vóór publicatie een daadwerkelijke LICENSE toe; een intentie is geen licentie.


## Aangescherpte eerste oplevering

Op 27 oktober 2026 zijn op verzoek de [eerste drie milestones](backlog/milestones.md)
vastgelegd: technisch fundament, organisaties/toegang en eerste boekhoudkundige
keten. Ze bevatten einddemonstraties en afhankelijkheden; dit is planning, geen
Ready-goedkeuring, implementatieopdracht of releaseakkoord. Het ontbrekende
fundamentwerk is als UC-0013 Draft geregistreerd. Carlovdv blijft verantwoordelijk
voor productbesluiten; uitvoerders en reviewers worden per werkitem vastgelegd.

Op 27 oktober 2026 heeft `Carlovdv` bevestigd dat één gebruikersaccount toegang
moet kunnen hebben tot meerdere organisaties, met wisselen binnen
de applicatie. Lidmaatschap en rechten blijven per organisatie/administratie gelden;
deze keuze voegt geen automatische toegang of gedeelde boekhouding toe.
Op dezelfde datum is de richting van een eigen team per organisatie bevestigd.
Admin, Developer, Finance, Support en Viewer zijn door `Carlovdv` genoemde voorbeelden.
Op verzoek om best practices toe te passen is op 27 oktober 2026 het
[rollenmodel](architecture/identity-access.md) uitgewerkt: Eigenaar, Admin, Finance,
Medewerker en Viewer, met organisatiebeheer gescheiden van financiële bevoegdheden.
De eigenaar beheert verhoogde rollen; Admin kan zichzelf geen financiële rechten
geven. De aangewezen financieel verantwoordelijke krijgt Finance met de bestaande procesafspraken voor
vrijwilligersvergoedingen. Developer, Support en custom rollen blijven voorlopig
buiten de eerste oplevering. Dit vervangt de eerdere voorgestelde matrix en is
geen Ready-goedkeuring of bewijs van geïmplementeerde autorisatie.

De algemene boekhoudscenario's staan in [visie en scope](product/vision.md), inclusief
vrijwilligersvergoedingen. Fiscale kwalificaties, bewijsstukken en de precieze
functionaliteit moeten nog worden uitgewerkt. De volgende functionele besluiten
zijn op 26 oktober 2026 vastgelegd.
Op dezelfde datum is bevestigd dat zowel declaraties van werkelijk gemaakte kosten
tegen bonnetjes als vaste vergoedingen voor inzet moeten worden ondersteund.
`Carlovdv` heeft op dezelfde datum bepaald dat voorlopig uitsluitend de
aangewezen financieel verantwoordelijke deze namens vrijwilligers invoert. Zelf indienen door vrijwilligers
valt buiten de eerste scope. De aangewezen financieel verantwoordelijke mag beide soorten vergoedingen zelf
goedkeuren zonder verplicht akkoord van een andere bevoegde gebruiker, bevestigd op
26 oktober 2026. Op dezelfde datum is bevestigd dat de aangewezen financieel verantwoordelijke beide soorten
vergoedingen ook zelf definitief mag boeken binnen de eigen administratie.
Daarnaast is op dezelfde datum een overzicht per vrijwilliger bevestigd met
maand- en jaartotalen, uitgesplitst naar declaraties en vaste vergoedingen.
Datumgrondslag, statussen en eventuele signaleringen worden nog uitgewerkt.
Op 26 oktober 2026 is bevestigd dat het overzicht geboekte, uitbetaalde en
openstaande bedragen onderscheidt. Openstaande posten volgen uit geboekte facturen
of vrijwilligersvergoedingen; betalingen worden daarna gekoppeld. Eén betaling
moet meerdere facturen kunnen afwikkelen, bijvoorbeeld bij een maandelijkse
verzamelbetaling. Op dezelfde datum is bevestigd dat één betaling facturen van
meerdere leveranciers mag afwikkelen, bijvoorbeeld via een marketplace of
moederbedrijf met meerdere dienstverlenende dochterbedrijven. De leverancier per
factuur blijft behouden; de betaalontvanger wordt afzonderlijk vastgelegd.

Op 27 oktober 2026 heeft `Carlovdv` bevestigd dat een betaalspecificatie optioneel
is. Het factuurnummer is verplicht voor het koppelen van betalingen aan facturen;
een interne boekstukreferentie en bijlage van de factuur of nota (afbeelding of pdf)
zijn optioneel. Op dezelfde datum is verduidelijkt dat boekstuk hier een interne
referentie betekent, geen extra document.
Dit verduidelijkt dat een upload geen voorwaarde voor deze koppeling is; reeds
toegevoegde bronstukken blijven behouden. Op 27 oktober 2026 is bevestigd dat de
interne boekstukreferentie voorlopig handmatig wordt ingevuld. De koppelreferentie
voor posten zonder factuurnummer staat nog open.

Op dezelfde datum is vastgelegd dat financiële mutaties een doorzoekbaar
mutatienummer, datum, referentie en bedrag hebben; facturen hebben daarnaast een
relatie. Het mutatienummer is onderscheiden van de optionele boekstukreferentie.
Op 27 oktober 2026 is bevestigd dat mutatienummers automatisch, uniek en oplopend
per administratie worden toegekend, niet wijzigbaar zijn en nooit worden hergebruikt.
Op dezelfde datum is besloten dat toekenning pas bij definitief boeken plaatsvindt.
Concepten hebben geen mutatienummer; verwijderen daarvan beïnvloedt de nummerreeks
niet. Dit vervangt de eerdere uitwerking met genummerde, verwijderbare concepten.
Definitieve boekingen blijven uitsluitend via tegenboekingen te corrigeren; een
tegenboeking krijgt een eigen nieuw nummer en behoudt de verwijzing naar de originele post.
Nummerformaat en de precieze velddefinities worden nog uitgewerkt.
Op 27 oktober 2026 is bevestigd dat de mutatienummerreeks per administratie over
boekjaren heen doorloopt; een jaarovergang zet de teller niet terug.
Voor de eerste oplevering is op dezelfde datum gekozen voor
een kalenderboekjaar (1 januari t/m 31 december). Ondersteuning voor
gebroken boekjaren is uitgesteld naar een later traject, vastgelegd in
[UC-0012](backlog/use-cases/UC-0012-broken-financial-year.md).
Op 27 oktober 2026 is besloten dat afsluiten en heropenen voorlopig uitsluitend
per volledig boekjaar gebeurt, niet per maand. Dit beperkt de afsluitfunctie,
niet de beschikbare rapportageperioden.

Op 27 oktober 2026 is verduidelijkt dat het product bedoeld is voor uiteenlopende
activiteiten en rechtsvormen. Persoonlijke organisatievoorbeelden zijn verwijderd;
ze bepalen niet de doelgroep of de inrichting van een nieuwe organisatie.

De functionele scopebesluiten van 26 oktober 2026 blijven gelden: KOR met ingangsdatum
en optionele einddatum, en EU-inkoop van diensten, software en abonnementen met
verlegde btw. De eerste oplevering gebruikt EUR en ondersteunt binnenlandse verkoop;
buitenlandse verkoop, buitenlandse goedereninkoop en niet-EU-inkoop blijven voorlopig
buiten scope. Deze transactiescope staat los van de brede doelgroep. Fiscale voorwaarden
moeten worden onderbouwd en gereviewd; de betrokken use-cases blijven Draft.

De gebruikersopdracht bevestigt de boekhoudkern met winst-en-verlies, balans,
bestaande facturen/bonnetjes, standaard/eigen grootboek en eigen ondernemingsomgeving.
Payroll, urenregistratie, offertes en facturatie vallen erbuiten. De productscope in
product/vision.md vervangt het eerdere voorstel voor verkoopfacturatie.

Passwordless productie en de lokale developmentuitzondering zijn vastgesteld.
Beschikbaarheid van tenants, appregistraties en beheerrechten wordt bij de
providerinrichting vastgesteld; persoonlijke infrastructuur is geen projectafhankelijkheid.
Open vóór auth-implementatie: Entra-tenantmodel, provider/library, één/beide routes,
MFA-combinaties, sessies en account recovery. Leg technische keuzes in een ADR vast;
zonder passwordless providerbewijs geen promotie naar Productie. Concrete fiscale
regels, standaardschema en reviewer blijven inhoudelijk te valideren.

## Projectidentiteit en documentatieopdracht — 27 oktober 2026

De opdrachtgever heeft de productnaam **OpenBookie**, het aangeschafte domein
**openbookie.nl** en de aangemaakte repository
[Direct365-NL/OpenBoekie](https://github.com/Direct365-NL/OpenBoekie) bevestigd.
`Direct365-NL` is de GitHub-organisatie waaronder de repository staat;
`Carlovdv` blijft de hierboven vastgelegde maintainer en productverantwoordelijke.
De afwijkende spelling van de repositorynaam wordt letterlijk overgenomen, niet
stilzwijgend aangepast. Hosting, DNS, e-mail en auth-redirects zijn hiermee niet gekozen.

De opdracht autoriseert uitsluitend deze documentatieaanpassing en een GitHub-
inrichtingshandleiding. Afwijking van de gebruikelijke Ready/claim/PR-procedure:
er is nog geen Ready-item en lokaal nog geen eerste commit; deze wijziging wordt
op de bestaande branch `main` voorbereid, zonder een implementatie-item te claimen.
Uitvoerder: Codex, in opdracht van Carlovdv. Status: lokaal uitgewerkt; nog niet
gecommit, gereviewd of geïntegreerd. UC-0013 en de overige backlogstatussen blijven
ongewijzigd. Zie het [documentatiebewijs](engineering/project-identity-verification.md).
