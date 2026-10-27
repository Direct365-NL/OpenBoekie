# UC-0013 — Technisch fundament

Status: Draft. Prioriteit: nog te bepalen. Eigenaar: niet toegewezen.
GitHub-issue / branch / PR / release: nog niet aangemaakt.
Milestone: [M1](../milestones.md#m1--technisch-fundament).

## Probleem en gebruikerswaarde

Een contributor moet de applicatie reproduceerbaar lokaal kunnen installeren,
starten, controleren en bouwen. Nu bestaan uitsluitend documentatie en mappen.
Actor: ontwikkelaar met lokale ontwikkeltoegang; geen productiebevoegdheid nodig.

## Scope en voorwaarden

Minimale web/API-toolchain, lokale database en migratiepad, configuratievalidatie,
kwaliteitschecks en installatie-/ontwikkeldocumentatie. Geen productfunctionaliteit,
hosting, automatische CI/CD, secrets in Git of productie-uitrol.
Afhankelijkheden: review en acceptatie van ADR-0001 en de concrete toolchain-ADRs
volgens architectuur/README.md; expliciete opdracht tot implementatie.

## Acceptatiecriteria

- AC-1: Gegeven een schone checkout en de gedocumenteerde vereisten kan een contributor
  met vastgelegde toolversies en lockfile installeren en web/API lokaal starten.
- AC-2: Gegeven een lege lokale database kan het vastgelegde migratiepad initialiseren;
  opnieuw uitvoeren past reeds uitgevoerde migraties niet dubbel toe.
- AC-3: Gegeven ontbrekende verplichte configuratie stopt de betreffende component
  met een begrijpelijke fout zonder secrets of onbeveiligde fallback.
- AC-4: Gegeven de beoordeelde commit bestaan werkende commando's voor formattercontrole,
  lint, strict typecheck, toepasselijke tests en build, met vastgelegd resultaat.
- AC-5: De README beschrijft installatie, start/stop, configuratie en controles;
  afhankelijkheidsrichting en gekozen versies zijn gedocumenteerd.

## Impact en bewijsplan

Gebruik uitsluitend synthetische data. Geen authenticatiebypass, tenantdata of
productiecredentials introduceren. Concrete geld- en fiscale logica vallen buiten
dit item; er is geen fiscale vrijgave. Beoordeel dependencylicenties en onderhoud.
Werk database-initialisatie, migratieherhaling en fout-/herstelgedrag uit na toolkeuze.

AC-1/5 → M1-D1: schone-checkout-demonstratie en documentatiereview.
AC-2 → M1-D2: echte lokale database en migratieherhaling.
AC-3 → M1-D4: gerichte configuratietests.
AC-4 → M1-D3: lokale checkresultaten volgens testing.md.
Leg commit, omgeving, toolversies, commando's en resultaten vast met het
[verificatietemplate](../../templates/verification.md). Geen uitgevoerde checks claimen
zolang de implementatie ontbreekt.

## Nog nodig vóór Ready

Concrete tools/versies en ADR-review, configuratiecontract, migratie-/herstelkeuze,
testcommando's en inhoudelijke testgevallen, eigenaar en prioriteit, vastgelegde
productgoedkeuring met datum en specificatieversie. Implementatieakkoord is een
aparte voorwaarde en wordt niet afgeleid uit goedkeuring van deze planning.

Acceptatiebewijs: ontbreekt; niet geïmplementeerd of uitgerold.
