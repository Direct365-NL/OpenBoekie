# OTAP en handmatige releases

Er zijn nog geen omgevingen ingericht. OTAP staat voor Ontwikkeling, Test,
Acceptatie en Productie. Omgevingen delen geen databases, opslag, secrets of
toegangsidentiteiten. Omgevingen zijn geen permanente Git-branches.

| Omgeving | Doel en data | Gate naar volgende omgeving |
| --- | --- | --- |
| O — Ontwikkeling | Lokaal, synthetische data, snelle feedback | PR-review, lokale checks en reproduceerbare build |
| T — Test | Geïsoleerde integratie/E2E en migratieproeven | Kritieke suites groen, securitybevindingen beoordeeld |
| A — Acceptatie | Productieachtige configuratie, synthetische data | Productacceptatie, fiscale review waar nodig, herstelproef |
| P — Productie | Echte administraties, minimaal toegangsrecht | Expliciet releaseakkoord, rooktest en monitoring |

## Releaseprocedure zonder Actions

1. Selecteer gereviewde main-commit. Voer lokale checks op een schone checkout uit
   en leg bewijs vast. Bouw met gepinde toolchain en lockfile zodra deze bestaan.
2. Maak één versieerbaar artefact met digest en herkomst. Houd configuratie/secrets
   buiten het artefact. Registreer alles in docs/releases met het releasetemplate.
3. Deploy hetzelfde artefact naar T; test migraties op representatieve synthetische
   data, contracten, tenantgrenzen, transacties en concurrentie.
4. Promoveer naar A. Controleer gebruikersscenario's, fiscale resultaten,
   toegankelijkheid en herstel uit backup. Leg acceptatie vast.
5. Controleer backup, migratiecompatibiliteit, herstelplan en operationele eigenaar.
   De releaseverantwoordelijke geeft expliciet productieakkoord.
6. Promoveer hetzelfde artefact naar P; voer rooktest en financiële
   consistentiecontroles uit. Registreer versie, tijd, uitvoerder en resultaat.

Geen automatische deployments of verborgen alternatieve CI. Een nieuwe commit
na goedkeuring vraagt opnieuw de relevante checks en gates. Gebruik SemVer vanaf
de eerste software-release; documenteer compatibiliteit en migraties ook vóór 1.0.

## Herstel en hotfix

Pas expand/contract toe voor schemawijzigingen waar nodig. Oude applicatie terugzetten
is alleen veilig bij compatibel schema. Destructieve migraties vragen een getest herstel-
of forward-fixplan; een backup terugzetten kan nieuwe boekingen verliezen en vereist
expliciete impactbeoordeling en afstemming. Test restore, niet alleen backupcreatie.
Een hotfix krijgt regressietest, review en dezelfde gates; versnel de planning,
sla financiële controles niet over. Registreer afwijkingen en acceptatie expliciet.


## Auth-gates voor de eerste oplevering

Volg de [authenticatiematrix](../architecture/identity-access.md). Alleen O gebruikt
initieel een vooraf vastgestelde gebruikersnaam en wachtwoord. Voor T is een echte
testprovider nodig voor auth-integratiebewijs; lokale mocks bewijzen dit niet.
A en P gebruiken de geselecteerde passwordless methode(n), met gescheiden registraties,
redirect-URI's en secrets. Test dat de developmentadapter buiten O wordt geweigerd.
Een niet beschikbare provider blokkeert de promotie, nooit een wachtwoordfallback.
Leg vóór A het Entra/passwordlessbeleid, eventuele e-mailroute, MFA en herstel vast.
