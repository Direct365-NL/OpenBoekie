# Teststrategie en Definition of Done

Status: testbeleid; er bestaan nog geen uitvoerbare tests.
Alle productiecode moet door passend bewijs worden afgedekt. Coverage alleen bewijst
geen correctheid. Voor geld, btw, boekingsbalans en autorisatie streven we naar 100%
statement- en branchcoverage; uitzonderingen vereisen beschreven risico en review.
Voor overige productiecode is het initiële minimum 90% statements en branches.
Gegenereerde code mag gemotiveerd worden uitgesloten; nooit eigen lastige code.

| Niveau | Wat wordt bewezen |
| --- | --- |
| Unit | Domeinregels, bedragen, afronding, toestandsovergangen, foutpaden |
| Property-based | Debet/creditbalans, behoud van bedragen, afrondingsinvarianten |
| Integratie | Echte database, transacties, constraints, rollback, migraties, tenantisolatie |
| Contract | API-validatie, foutvormen, adapters en externe sandboxcontracten |
| End-to-end | Gebruikersrollen en kritieke journeys inclusief geweigerde toegang |
| Acceptatie | Elk Given/When/Then-criterium en inhoudelijk boekhoudkundig resultaat |
| Operationeel | Backupherstel, export, uitrol, rooktest en herstelpad |

Test gelijktijdige nummeruitgifte, dubbele requests, deelbetalingen, creditnota's,
periodeafsluiting, tenantgrenzen en fout halverwege een transactie. Gebruik onafhankelijke
verwachte bedragen, geen kopie van dezelfde berekeningsfunctie als test-orakel.
Fixtures zijn synthetisch, deterministisch en versieerbaar. Mock externe diensten waar
nodig; mock de database niet als bewijs voor databasegedrag. Controleer toegankelijkheid
en bruikbaarheid van kritieke schermen zodra UI bestaat.

## Done

- Alle criteria en relevante fout-/misbruikscenario's bewezen; regressietest bij bugs.
- Formatter, lint, strict typecheck, toepasselijke tests, coverage en build geslaagd.
- API-/module-/gebruikersdocumentatie en ADRs bijgewerkt.
- Dependency-/securitycontrole uitgevoerd; bevindingen beoordeeld.
- Review en eventuele fiscale review vastgelegd; geen open blokkerende bevindingen.
- PR geïntegreerd en gekoppeld item bijgewerkt. Productiepromotie is een aparte gate.

Gebruik docs/templates/verification.md voor bewijs met commit, toolversies, exacte
commando's, resultaten en artefactreferenties. Voor alleen documentatie: links,
structuur en consistentie controleren; rapporteer applicatietests als niet van toepassing.
Zonder CI beoordeelt de reviewer het lokale bewijs. Bewijs van een eerdere commit
is ongeldig na wijzigingen die de betreffende checks beïnvloeden.


## Aanvullende verplichte eerste-opleveringsscenario's

Verifieer standaard/eigen rekeningen en historie bij deactivering; bronstuk → boeking
→ winst-en-verlies/balans; beginbalans, jaarovergang en resultaat zonder dubbeltelling;
deelbetaling en correcties. Gebruik één kleine onafhankelijk doorgerekende administratie.

Test developmentcredentials uitsluitend in O, en expliciete weigering in T/A/P,
ook bij foutieve configuratie. Test OIDC-token/callbackvalidatie, verlopen/eenmalige
e-mailcodes waar actief, afmelden, recovery en intrekking. Test iedere rol met minimaal
twee tenants, inclusief bestanden en exports. Mocks bewijzen geen passwordless
providerpolicy; voer echte providerintegratietests in T en acceptatietests in A uit.
