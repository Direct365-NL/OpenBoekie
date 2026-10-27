# UC-0010 — Btw-overzicht, archief en export

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Eigenaar/boekhouder.
Scope: Btw-controleoverzicht en export van boekhouding met bronstukken; geen aangifte-indiening.

- AC-1: Het btw-overzicht is herleidbaar tot definitieve boekingen, regelversies en periode; niet-ondersteunde situaties worden zichtbaar geweigerd.
- AC-2: Een bevoegde gebruiker kan rekeningen, journaalregels, relaties, metadata en bronstukken in een gedocumenteerd formaat exporteren.
- AC-3: De export respecteert tenantgrenzen en een consistente peildatum; totalen en bestandsverwijzingen zijn controleerbaar.
- AC-4: Historische stukken blijven leesbaar volgens het vastgestelde bewaarbeleid, ook na deactivering van een rekening.

Afhankelijkheden: UC-0006, UC-0007, UC-0008.
Aanvullend: KOR-instellingen uit UC-0001. Werk vóór Ready uit hoe het overzicht en
de export KOR-perioden en overgangen herleidbaar weergeven, volgens gereviewde
fiscale regels. Test perioden vóór, tijdens en na deelname, inclusief correcties;
een wijziging van de huidige instelling mag historische regelversies niet vervangen.
Aanvullende scope (26 oktober 2026): inkoop van diensten, software en abonnementen
binnen de EU met verlegde btw uit UC-0006. Specificeer vóór Ready de fiscale rubricering en afstemming met het
grootboek, inclusief correcties en eventuele samenloop met KOR. Gebruik gereviewde,
onafhankelijk berekende scenario's als acceptatiebewijs.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Fiscale rubricering, exportformaat, bewaarmatrix, grote exports en inhoudelijke review. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
