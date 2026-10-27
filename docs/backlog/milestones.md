# Eerste drie milestones

Vastgelegd op 27 oktober 2026 op verzoek van de productverantwoordelijke.
Status: planning vastgelegd; uitvoering niet gestart. Geen deadlines of
implementatiegoedkeuring vastgelegd. Productverantwoordelijke: Carlovdv;
uitvoerders en reviewers worden per werkitem benoemd.

Deze milestones leveren achtereenvolgens een ontwikkelfundament, veilige toegang
en een eerste boekhoudkundige keten op. Ze zijn geen volledige eerste productrelease.
De [productscope](../product/vision.md) blijft leidend voor het totale product.

| Milestone | Eindresultaat | Harde afhankelijkheid |
| --- | --- | --- |
| M1 — Technisch fundament | Vanuit een schone checkout lokaal starten, controleren en bouwen | Architectuur-/toolchainbesluiten en expliciet implementatieakkoord |
| M2 — Organisaties en toegang | Organisaties inrichten en met gescheiden rechten wisselen | M1; gereviewde auth-/tenantcontracten en rekeningschema |
| M3 — Eerste boekhoudkundige keten | Concept boeken, terugvinden, tegenboeken en boekjaar afsluiten | M2; gereviewde geld-, boekings- en periodecontracten |

## Werkwijze en acceptatie

- Het onderstaande werk is niet automatisch Ready of geclaimd. Volg de
  [backlogprocedure](README.md): criteria, eigenaar, afhankelijkheden, bewijsplan
  en vastgelegde goedkeuring vóór uitvoering; claim één item per keer.
- Werkpakketten zoals M2-A zijn planningslabels, geen afzonderlijke statusadministratie.
  Splits een gedeeltelijke use-case vóór uitvoering in zelfstandig goed te keuren
  backlogitems met eigen nummers en criteria. Een moeder-use-case wordt niet Done
  wanneer alleen het milestonegedeelte is afgerond.
- De demonstraties hieronder zijn te behalen resultaten, geen uitgevoerd bewijs.
  Gebruik uitsluitend synthetische organisaties, identiteiten en bedragen.
- Afgerond vereist geïntegreerd werk, de toepasselijke
  [Definition of Done](../engineering/testing.md), review en demonstratiebewijs
  op dezelfde commit via [het verificatietemplate](../templates/verification.md).
  Vermeld per demo-ID resultaat, commando/stappen en artefactreferentie.
- Een demonstratie vervangt geen automatische tests. Financiële verwachtingen
  worden onafhankelijk doorgerekend en inhoudelijk gereviewd vóór acceptatie.
- M1–M3 zijn lokaal te demonstreren in Development. Ze geven geen toestemming voor
  publicatie of productiegebruik. [OTAP](../operations/otap.md) blijft gelden:
  Test vraagt echte providerintegratie voor authbewijs; Acceptatie en Productie
  vereisen de gekozen werkende passwordless route uit UC-0011.

## M1 — Technisch fundament

Doel: een andere ontwikkelaar kan de repository volgens de README lokaal starten
zonder ongedocumenteerde installatiehandelingen.

### Werkpakketten en afhankelijkheden

| Pakket | Scope | Eerst nodig |
| --- | --- | --- |
| M1-A | Review ADR-0001; ADRs voor runtime, package manager, web/API, database/migraties, validatie, exact rekenen, authlibrary en testtools | Vergelijking op onderhoud, eenvoud, beveiliging en licentie |
| M1-B | Minimale lokale toolchain, web/API-opstart, databaseverbinding en migratiepad; echte lokale checkcommando's | M1-A geaccepteerd; UC-0013 Ready; expliciet implementatieakkoord |
| M1-C | README, configuratie-instructies zonder secrets, architectuurgrenzen en controlebewijs | M1-B |

Werkitem: [UC-0013 — Technisch fundament](use-cases/UC-0013-technical-foundation.md).
M1 bouwt alleen wat nodig is voor de volgende werkpakketten; geen ongebruikte modules,
hosting, GitHub Actions, alternatieve CI/CD of volledige auth-/boekhoudimplementatie.

### Einddemonstratie

1. **M1-D1:** installeer vanuit een schone checkout met vastgelegde toolversies en
   lockfile. Start web, API en lokale database met de gedocumenteerde stappen.
2. **M1-D2:** toon een bereikbare webpagina en API en een gecontroleerde database-
   verbinding. Initialiseer een lege database en toon dat opnieuw uitvoeren van
   het migratiecommando geen al uitgevoerde migratie dubbel toepast.
3. **M1-D3:** voer formattercontrole, lint, strict typecheck, toepasselijke tests en
   build uit met echte commando's; leg resultaten vast. Test minimaal de daadwerkelijk
   geïntroduceerde grens-/configuratiefouten; maak geen fictieve kwaliteitsclaims.
4. **M1-D4:** toon dat ontbrekende verplichte configuratie een begrijpelijke fout
   oplevert zonder secrets te loggen of een onbeveiligde fallback te activeren.

### Nog te besluiten vóór Ready

ADR-0001 staat Proposed. Concrete tools/versies, lokale configuratie, database-
levenscyclus en checks moeten worden gekozen. Authcontract en tenantisolatie worden
uitgewerkt voor M2; keuzes met invloed op M1 worden vóór M1-B besloten. Productnaam, domein en remote zijn vastgelegd in [governance](../governance.md).
De licentiekeuze blijft open; publieke publicatie is
geen onderdeel van M1. Er bestaan nog geen uitvoerbare checks of applicatiecode.

## M2 — Organisaties en toegang

Doel: een gebruiker kan een organisatie met eerste administratie aanmaken, een team
beheren en veilig wisselen tussen toegankelijke organisaties.

### Werkpakketten en afhankelijkheden

| Pakket | Scope en bron | Eerst nodig |
| --- | --- | --- |
| M2-A | Auth-/tenantcontract, rolpermissies, sessies, onboardingvelden en uitnodigingscontract; UC-0001/UC-0004/UC-0011 | M1-keuzes; één/beide aanmeldroutes en providerstrategie vóór auth-implementatie |
| M2-B | Developmentadapter en sessiegedrag; UC-0004 AC-1–3 | M1; M2-A |
| M2-C | Versieerbaar gereviewd basisschema en idempotente schema-initialisatie; UC-0005 AC-1 en template-isolatie uit AC-4 | M2-A; schema- en rubriceringsreview |
| M2-D | Atomaire onboarding, teamrollen, uitnodigingen, eigendomsoverdracht en organisatiewissel; UC-0001 AC-1–6 en AC-10–16 | M2-B en M2-C |

Het contract van UC-0001 is vóór de schemafunctie beschikbaar; de schemafunctie
wordt daarna bij onboarding geïntegreerd. Dit is geen cyclische bouwafhankelijkheid.
Volledig beheer van eigen rekeningen volgt in M3. KOR-instellingen (UC-0001 AC-7–9)
en de vrijwilligersworkflow volgen later. Het specifieke aanwijzingsproces voor
vrijwilligers wordt met die workflow uitgewerkt; er ontstaat geen algemene extra rol.

### Einddemonstratie

1. **M2-D1:** meld lokaal aan en maak synthetische Organisatie A met eerste administratie,
   eigenaar-lidmaatschap en standaardrekeningen aan. Herhaal dezelfde opdracht:
   geen tweede organisatie. Een geforceerde fout laat geen halve inrichting achter.
2. **M2-D2:** gebruik één account met lidmaatschappen bij A en B. Wissel in de UI;
   organisatie en administratie blijven zichtbaar en rechten volgen de actieve context.
3. **M2-D3:** nodig een synthetische gebruiker uit, accepteer eenmalig en toon dat
   verlopen of hergebruikte uitnodigingen worden geweigerd. Toon het verschil tussen
   Eigenaar, Admin, Finance, Medewerker en Viewer met gecontroleerde API-aanvragen.
   Admin kan zichzelf geen Finance toekennen; Viewer kan niet wijzigen.
4. **M2-D4:** probeer met een account dat alleen toegang tot A heeft een direct
   object-ID van B te lezen/wijzigen: geweigerd zonder gegevenslek. Trek een
   lidmaatschap in en herhaal met de bestaande sessie: eveneens geweigerd.
5. **M2-D5:** toon afmelden en sessieverloop. Bewijs met configuratietests dat de
   developmentadapter buiten O wordt geweigerd; dit is geen echte T/A/P-uitrol.
6. **M2-D6:** toon dat de laatste eigenaar niet kan worden verwijderd zonder geldige
   overdracht, en dat een organisatiewissel geen oude invoer in de andere administratie
   opslaat. Meerdere synthetische testidentiteiten bewijzen de rol- en tenantgrenzen.

### Nog te besluiten vóór Ready

Definitieve onboardingvelden, concrete permissies, uitnodigingstermijnen, recovery,
sessietermijnen, credentialsinjectie, rate limiting en gedrag bij onopgeslagen invoer/
meerdere tabbladen. Selecteer de echte providerroute en leg inrichting vast in het
Auth-ADR; de provider hoeft voor de lokale demo niet al aangesloten te zijn.
Het standaardschema en initialisatie-/retrycontract vragen inhoudelijke review.
De vaste developmentgebruiker vervangt geen tests met meerdere identiteiten.

## M3 — Eerste boekhoudkundige keten

Doel: een bevoegde gebruiker kan handmatig een journaalpost boeken, het resultaat
in grootboek/proefbalans herleiden en een fout corrigeren zonder historie te wissen.

### Werkpakketten en afhankelijkheden

| Pakket | Scope en bron | Eerst nodig |
| --- | --- | --- |
| M3-A | Exacte bedragen, tekenconventie, datums, mutatiereferentie, idempotentie, nummering en boekjaarcontract | M2; inhoudelijke review en onafhankelijke referentiebedragen |
| M3-B | Eigen rekeningen, deactivering en historie; resterende UC-0005 AC-2–4 | M3-A; basisschema M2-C |
| M3-C | Concepten, atomair boeken, zoeken en nummering; UC-0002 AC-1–8 voor handmatige journaalposten | M3-B; periode-/correctiecontract afgestemd met UC-0008 |
| M3-D | Beginbalans, tegenboeken en volledig boekjaar afsluiten/heropenen; UC-0008 AC-1–4 en AC-6 | M3-C |
| M3-E | Grootboekkaart en proef-/saldibalans met herleiding naar journaalregels; basisgedeelte UC-0007 | M3-C en M3-D |

De gedeelde zoek- en nummercontracten gelden later ook voor facturen en betalingen;
deze adapters zijn nog geen onderdeel van M3. Jaarafsluiting als boekingsblokkade
wordt hier aangetoond; volledige resultaatbestemming en automatische overdracht
van slotstanden (UC-0008 AC-5) volgen later. Ook volledige balans/W&V, bronstukken,
openstaande posten, vrijwilligersoverzichten, btw en export blijven vervolgwerk.
UC-0002, UC-0007 en UC-0008 worden daarom niet uitsluitend op basis van M3 Done.

### Einddemonstratie

De onderstaande bedragen zijn synthetische demonstratieverwachtingen, geen fiscale
scenario's. Laat de definitieve fixtures vóór Ready onafhankelijk beoordelen.

1. **M3-D1:** initialiseer een beginbalans van EUR 1.000 debet op Bank en EUR 1.000
   credit op Eigen vermogen. Een tweede initialisatie wordt geweigerd.
2. **M3-D2:** maak een eigen kostenrekening en een concept met EUR 100 debet Kosten
   en EUR 100 credit Bank, zonder btw-berekening. Het concept heeft geen mutatienummer
   en telt niet mee in de proefbalans. Definitief boeken geeft één onveranderlijk nummer.
3. **M3-D3:** zoek op mutatienummer, datum, referentie en bedrag. Toon vanuit de
   grootboekkaart de journaalregels. De saldi zijn Bank 900 debet, Kosten 100 debet
   en Eigen vermogen 1.000 credit; totale debetsaldi en creditsaldi zijn beide 1.000.
4. **M3-D4:** herhaal de boekingsopdracht: geen tweede post of nieuw nummer. Een
   ongebalanceerde post, onbevoegde aanvraag of fout tijdens de transactie laat geen
   gedeeltelijke definitieve boeking achter. Concurrentietests bewijzen unieke nummers.
5. **M3-D5:** wijzig/verwijder de definitieve kostenpost: geweigerd. Boek haar tegen
   met een nieuw nummer en verwijzing naar het origineel. Bank staat weer op 1.000,
   Kosten op 0 en Eigen vermogen op 1.000 credit; beide posten blijven herleidbaar.
6. **M3-D6:** deactiveer de gebruikte kostenrekening: historie blijft zichtbaar en
   nieuwe boekingen erop worden geweigerd. Sluit het boekjaar: boeken wordt geweigerd,
   ook bij concurrentie. Bevoegd heropenen vereist een reden en auditregistratie.
7. **M3-D7:** boek in het volgende kalenderboekjaar en toon dat de nummerreeks doorloopt.
   Dit bewijst nummering, niet automatische resultaatverwerking of jaaroverdracht.
   Een tweede administratie heeft een eigen reeks en geen toegang tot de eerste.

### Nog te besluiten vóór Ready

Decimalen/precisie/afronding, nummerformaat en rollbackgedrag, datum- en bedragvelden,
zoekgedrag, beginbalansproces, correctiedatum, heropeningsbeleid en schemawijzigingen.
Verduidelijk bij UC-0007 het verschil tussen boekdatum en invoertijdstip: de bestaande
zin dat een latere boeking geen eerdere peildatum wijzigt is onvoldoende precies
voor later ingevoerde boekingen met een eerdere boekdatum. Leg het rapportagecontract
vast vóór M3-E Ready wordt; deze planning neemt geen bevroren rapportages aan.

## Vervolg en eerstvolgende actie

Bereid UC-0011 vanaf het gedeelde authcontract voor naast de bovenstaande planning;
providerbewijs blijft verplicht bij de OTAP-gates. Daarna volgen bronstukken,
openstaande posten/verzamelbetalingen, volledige rapportages, fiscale scenario's en
export. De volgorde daarvan wordt afzonderlijk vastgelegd; niets vervalt uit de
bestaande eerste productscope.

Eerstvolgende actie: werk M1-A uit en maak UC-0013 gereed voor review. Vraag daarna
expliciet implementatieakkoord voordat uitvoerbare toolchainconfiguratie wordt geschreven.
De huidige opdracht legt uitsluitend de planning en specificaties vast.
