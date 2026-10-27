# UC-0011 — Passwordless productieauthenticatie

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Gebruiker.
Scope: Entra ID via OIDC/OAuth 2.0 en/of e-mailroute volgens identity-access.md.

- AC-1: Via elke geactiveerde route kan een geldige gebruiker passwordless aanmelden; de toepasselijke providerpolicy wordt aantoonbaar afgedwongen.
- AC-2: Ongeldige issuer/audience/handtekening, verlopen tokens en mislukte state/nonce-validatie worden geweigerd op de Entra-route.
- AC-3: Als e-mail geactiveerd is, worden verlopen/hergebruikte codes of links en te veel pogingen geweigerd zonder accountenumeratie.
- AC-4: Aanmelden kent geen tenantrechten toe zonder lidmaatschap; gelijk e-mailadres bij verschillende providers leidt niet automatisch tot accountkoppeling.
- AC-5: Productie accepteert nooit developmentcredentials; afmelden, intrekken en sessieverloop blokkeren verdere toegang.
- AC-6: Als MFA vereist is, bewijst een test de gekozen onafhankelijke factoren; e-mail als enige stap wordt niet als MFA geaccepteerd.

Afhankelijkheden: Auth-ADR, providerinrichting; autorisatie-integratie UC-0001.
Voor de Entra-route moeten tenant, appregistratiebevoegdheid, credentials en
passwordless providerpolicy bij de projectinrichting worden vastgesteld en geverifieerd.
Er wordt geen bestaande persoonlijke tenant als uitgangspunt aangenomen.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Entra-directorymodel, één/beide routes, MFA-beleid, recovery, sessietermijnen en ondersteunde methoden. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
