# UC-0006 — Facturen en bonnetjes indienen en verwerken

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Medewerker dient in; eigenaar/boekhouder boekt.
Scope: Upload, metadata, beoordeling en boeking van bestaande facturen, bonnetjes en creditnota’s; geen opstellen/versturen.

- AC-1: Een toegestane upload wordt als nog te beoordelen bronstuk opgeslagen in de eigen administratie; dit maakt geen journaalpost.
- AC-2: Een beoordelaar legt relatie, documentdatum, extern nummer waar aanwezig, bedragen, btw en grootboekverdeling vast; validatie voorkomt ongebalanceerd of onbevoegd boeken.
- AC-3: Na boeken zijn een aanwezig origineel en journaalpost herleidbaar gekoppeld; een retry of storing tussen opslag en boeken veroorzaakt geen dubbele of halve boeking.
- AC-4: Mogelijke duplicaten worden gesignaleerd zonder factuurnummers van verschillende leveranciers globaal uniek te maken.
- AC-5: Een medewerker ziet alleen zijn eigen indieningen; andere tenants kunnen ook via directe bestands-URL’s niets ophalen.
- AC-6: Ongeldig bestandstype, te groot bestand en verdachte upload worden geweigerd of geïsoleerd; afwijzing geeft een reden en auditspoor.

Afhankelijkheden: UC-0001, UC-0002, UC-0005.
Afspraak van 27 oktober 2026: een interne boekstukreferentie en factuur-/notabijlage (afbeelding of pdf)
zijn optioneel; een upload is geen voorwaarde voor registratie en betalingstoewijzing.
Een aanwezig origineel blijft bewaard. De boekstukreferentie is een interne
referentie, geen extra document, en wordt voorlopig handmatig ingevuld; formaat en
uniciteit moeten nog worden bepaald.
Facturen hebben een relatie en hun financiële mutaties zijn doorzoekbaar op
mutatienummer, datum, referentie en bedrag volgens het gedeelde contract uit
[UC-0002](UC-0002-journal.md). Werk dit mee uit vóór Ready.
Voor koppeling van een betaling aan een factuur is het factuurnummer verplicht
volgens UC-0009; de referentie voor nummerloze nota's en vrijwilligersvergoedingen
staat nog open. De overige inhoudelijke boekings- en fiscale controles blijven gelden.
Werk ook de bewijsstukken en algemene boekingsscenario's uit
volgens de [productscope](../../product/vision.md), inclusief vrijwilligersvergoedingen.
Deze omvatten zowel declaraties van werkelijk gemaakte kosten tegen bonnetjes als
vaste vergoedingen voor inzet (bevestigd op 26 oktober 2026). Werk beide vormen als
afzonderlijke scenario's uit, inclusief bewijs, beoordeling, boeking en correctie.
Voor beide vrijwilligersscenario's is voorlopig uitsluitend de aangewezen financieel verantwoordelijke de
indiener namens de vrijwilliger; zelf indienen door vrijwilligers valt buiten scope.
De aangewezen financieel verantwoordelijke mag beide soorten vergoedingen zelf goedkeuren; akkoord van een
andere bevoegde gebruiker is niet vereist (bevestigd op 26 oktober 2026). Dit specificeert
de algemene indieners- en beoordelaarsrol voor deze scenario's nader.
De aangewezen financieel verantwoordelijke mag beide soorten vergoedingen ook zelf definitief boeken binnen
de eigen administratie (bevestigd op 26 oktober 2026). Werk vóór Ready de koppeling
van deze bevoegdheden aan applicatierollen uit.
Test indiening, zelfgoedkeuring en definitief boeken door de aangewezen financieel verantwoordelijke, plus
weigering van onbevoegde toegang tot deze handelingen. Leg de handelingen herleidbaar
vast in de audittrail; de normale boekingsvalidaties blijven gelden.
Nog nodig: documenttypen en gegevens voor inkomsten of vergoedingen waarvoor geen
reguliere inkoop- of verkoopfactuur beschikbaar is, plus beoordeling en correctie.
Aanvullende scope (26 oktober 2026): inkoop bij buitenlandse leveranciers binnen
de EU met verlegde btw, uitsluitend diensten, software en abonnementen.
Buitenlandse goedereninkoop en inkoop buiten de EU vallen voorlopig buiten scope.
Nog nodig voor Ready: concrete fiscale scenario's, bewijsvelden, fiscale
regelversies, berekening en aftrek, samenloop met KOR en correcties. Werk positieve
en negatieve scenario's uit met synthetische facturen en onafhankelijk berekende
boekingen; een leveranciersnaam alleen bepaalt niet de fiscale behandeling.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Uploadlimieten, scanbeleid, documentstatussen, btw-aftrekbeleid, correctieflow en fiscale review. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
