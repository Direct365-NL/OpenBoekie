# Backlog: use-cases en bugs

Nu is deze map de bron voor specificatie én status. Maak een bestand met het juiste
template, een uniek UC- of BUG-nummer en voeg het toe aan onderstaande tabel.
Na GitHub-inrichting beheert het issue status, prioriteit en eigenaar; het Markdown-
bestand blijft de gereviewde specificatie. Leg issue-URL in het bestand vast en link
de specificatie vanuit het issue. Houd dan geen tweede lokale statusadministratie bij.
Nieuwe kleine bugs mogen volledig in een issue staan; bewaar regressiebewijs in de PR.

## Workflow

Draft/Triage → Ready → In progress → Review → Done. Blocked heeft een reden en
voorwaarde om verder te gaan. Afgewezen/Duplicate blijft herleidbaar met motivatie.
Selecteer Ready-werk op prioriteit, voldane afhankelijkheden en daarna ouderdom.
Claim vóór bouwen. Er staat nog geen werk Ready; onderstaande items zijn voorstellen.

Ready vereist: probleem, actor, scope/uitsluitingen, toetsbare criteria, negatieve
scenario's, afhankelijkheden, rechten/tenantimpact, testplan, relevante fiscale bron,
eigenaar en vastgelegde productgoedkeuring. Een bug vereist reproduceerstappen,
verwacht/feitelijk resultaat, omgeving en impact; securitydetails blijven privé.
Done volgt testing.md en betekent geïntegreerd; uitrolstatus wordt apart vastgelegd.

Prioriteit: P0 incident/datalek/datacorruptie (direct triageren), P1 blokkerend probleem,
P2 normale levering, P3 verbetering. Ernst beschrijft impact; prioriteit de werkvolgorde.

| ID | Use-case | Status | Oplevering |
| --- | --- | --- | --- |
| UC-0001 | [Onderneming en toegang](use-cases/UC-0001-administration.md) | Draft | Eerste |
| UC-0002 | [Journaalpost boeken](use-cases/UC-0002-journal.md) | Draft | Eerste |
| UC-0003 | [Verkoopfacturatie](use-cases/UC-0003-invoice.md) | Deferred | Later |
| UC-0004 | [Developmentlogin](use-cases/UC-0004-development-login.md) | Draft | Eerste |
| UC-0005 | [Standaard en eigen grootboekrekeningen](use-cases/UC-0005-ledger-accounts.md) | Draft | Eerste |
| UC-0006 | [Facturen en bonnetjes indienen en verwerken](use-cases/UC-0006-documents.md) | Draft | Eerste |
| UC-0007 | [Winst-en-verliesrekening en balans](use-cases/UC-0007-reports.md) | Draft | Eerste |
| UC-0008 | [Beginbalans, correcties en periodebeheer](use-cases/UC-0008-periods-corrections.md) | Draft | Eerste |
| UC-0009 | [Bank, kas en openstaande posten](use-cases/UC-0009-payments.md) | Draft | Eerste |
| UC-0010 | [Btw-overzicht, archief en export](use-cases/UC-0010-vat-export.md) | Draft | Eerste |
| UC-0011 | [Passwordless productieauthenticatie](use-cases/UC-0011-passwordless.md) | Draft | Eerste |
| UC-0012 | [Gebroken boekjaar](use-cases/UC-0012-broken-financial-year.md) | Deferred | Later |
| UC-0013 | [Technisch fundament](use-cases/UC-0013-technical-foundation.md) | Draft | Eerste |

Deferred betekent bewust buiten de oplevering; heractiveer alleen bij een nieuw
scopebesluit. De eerste scope is bevestigd, maar de afzonderlijke items zijn nog
geen Ready-specificaties. Prioriteit/uitvoerder worden bij triage bepaald.

De [eerste drie milestones](milestones.md) leggen concrete einddemonstraties,
werkpakketten en afhankelijkheden vast. M1 betreft het technische fundament via
UC-0013; M2 organisaties/toegang; M3 een eerste boekhoudkundige keten. Gedeeltelijke
use-cases worden vóór uitvoering opgesplitst in zelfstandig goed te keuren items;
milestoneacceptatie maakt niet automatisch een volledige use-case Done.

Bouwvolgorde na het technische fundament: eerst auth-/tenantcontract en standaardrekeningschema, dan developmentlogin
met onboarding, daarna journaalposten en periodebeheer. Vervolgens bronstukken,
handmatige betalingen en volledige rapportages/export. Een minimale grootboekkaart
en proef-/saldibalans worden al in M3 gebruikt om de boekingskern te demonstreren.
Schema-initialisatie en onboarding
worden samen geïntegreerd; hun contractafhankelijkheid is geen cyclische bouwblokkade.
Werk productieauth vanaf het gedeelde authcontract parallel aan deze fasering uit;
Acceptatie en Productie zijn geblokkeerd totdat UC-0011 met de gekozen echte provider werkt.

Er zijn nog geen bekende bugs geregistreerd. Geen payroll, urenregistratie,
offertes of verkoopfacturatie toevoegen aan deze oplevering.
