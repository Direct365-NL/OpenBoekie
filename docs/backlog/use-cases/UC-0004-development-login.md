# UC-0004 — Developmentlogin

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Ontwikkelaar.
Scope: Vooraf vastgestelde lokale gebruikersnaam en wachtwoord; geen productieauth.

- AC-1: Geldige lokaal geconfigureerde credentials geven een sessie voor de synthetische ontwikkelgebruiker; ongeldige gegevens worden geweigerd.
- AC-2: Buiten Development wordt deze adapter geweigerd, ook bij aanwezige credentials; ontbrekende configuratie activeert geen fallback.
- AC-3: Alle normale tenant- en rolcontroles blijven gelden; uitloggen en verlopen sessies blokkeren vervolgtoegang.

Afhankelijkheden: Authcontract en toolchain.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Credentialsinjectie, rate limiting, sessietermijnen en technische adapterkeuze. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
