# OpenBookie

OpenBookie is een beoogde open source SaaS-boekhoudapplicatie in TypeScript voor Nederland,
voor organisaties met uiteenlopende activiteiten en rechtsvormen.
Deze repository bevat uitsluitend projectdocumentatie, werkafspraken en templates.
Er is nog geen applicatie, package manifest, database, infrastructuur of uitvoerbare test.
Er zijn geen GitHub Actions.

- Productnaam: **OpenBookie**.
- Geregistreerd domein: **openbookie.nl**; hosting en DNS-inrichting zijn nog niet bevestigd.
- GitHub: [Direct365-NL/OpenBoekie](https://github.com/Direct365-NL/OpenBoekie).
  De repositorynaam heeft bewust in deze documentatie de opgegeven spelling
  `OpenBoekie`; de productnaam blijft `OpenBookie`.
- De lokale remote `origin` verwijst naar deze repository. GitHub-instellingen
  zijn nog niet gecontroleerd; volg de [inrichtingschecklist](docs/engineering/github.md).

## Begin hier

1. Lees [AGENTS.md](AGENTS.md) voor bindende ontwikkelafspraken.
2. Lees [visie en scope](docs/product/vision.md) en [architectuur](docs/architecture/README.md).
3. Kies werk via de [backlog](docs/backlog/README.md) en [bijdrageprocedure](CONTRIBUTING.md).
4. Volg [kwaliteit en testen](docs/engineering/testing.md) en [OTAP](docs/operations/otap.md).

De [eerste drie milestones](docs/backlog/milestones.md) beschrijven het technische
fundament, organisaties/toegang en de eerste boekhoudkundige keten, inclusief
einddemonstraties en afhankelijkheden. De uitvoering is nog niet gestart.

## Structuur

| Map | Doel |
| --- | --- |
| apps/web, apps/api | Toekomstige gebruikersinterface en server |
| packages/domain, packages/application | Boekhoudregels en use-cases |
| packages/infrastructure, packages/ui | Externe adapters en gedeelde presentatie |
| tests | Integratie-, systeem-, security- en acceptatietesten |
| infra/environments | Afspraken per OTAP-omgeving |
| docs/product, docs/domain | Scope, begrippen en fiscale uitgangspunten |
| docs/backlog | Versioneerbare use-cases en bugs |
| docs/architecture/adr | Architectuurbesluiten |
| docs/engineering, docs/operations | Ontwikkeling, testen en beheer |
| docs/templates, docs/releases | Herbruikbare bewijsvoering en releases |
| .github | Issue- en pull-requesttemplates; geen workflows |

TypeScript staat vast. Een modulaire monoliet is het startontwerp; frameworks,
runtimeversies, database, hosting en concrete libraries worden vóór implementatie
via ADRs gekozen. Er zijn dus nog geen installatie- of testcommando's.

## Open source en open besluiten

Open source is het doel. De licentie is nog niet gekozen; zonder LICENSE worden
nog geen open-source-gebruiksrechten verleend. Kies en voeg vóór publieke publicatie
een OSI-goedgekeurde licentie toe. Zie [governance](docs/governance.md) voor deze
en overige beslissingen. Er is nog geen garantie op fiscale geschiktheid.

Inspiratie en officiële referenties staan in [bronnen](docs/product/references.md).


## Eerste oplevering

Boekhoudkern: facturen/bonnetjes indienen, standaard en eigen grootboekrekeningen,
journaalposten, beginbalans, periodebeheer, bank/kas, openstaande posten, balans,
winst-en-verlies, btw-overzicht en export. Geen payroll, urenregistratie, offertes
of verkoopfacturatie. Elke onderneming krijgt een afgeschermde omgeving met rechten.

Productie wordt passwordless via Entra ID (OIDC/OAuth 2.0) en/of e-mailverificatie;
alleen Development gebruikt initieel vaste lokaal ingestelde gebruikersnaam/wachtwoord.
Zie [identiteit en toegang](docs/architecture/identity-access.md) voor MFA, rollen en
omgevingsbeleid. Er zijn nog geen credentials of providers ingericht.
