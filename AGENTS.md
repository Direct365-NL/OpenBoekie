# Instructies voor contributors en agents

Dit bestand geldt voor de hele repository. Lees daarnaast README.md, CONTRIBUTING.md
en de documentatie van het te wijzigen onderdeel. Meld botsende afspraken expliciet.

## Huidige fase

Alleen documentatie en projectstructuur. Schrijf geen applicatiecode, configuratie
voor uitvoerbare builds, migraties of tests totdat implementatie expliciet is gevraagd.
Voeg geen GitHub Actions of andere automatische CI/CD toe zonder expliciete opdracht.
Claim nooit dat niet-uitgevoerde tests of nog niet ingestelde GitHub-regels bestaan.

## Werk selecteren en uitvoeren

- Lees docs/backlog/README.md. Haal alleen goedgekeurd Ready-werk op; neem geen
  willekeurig concept in uitvoering. Verifieer afhankelijkheden en acceptatiecriteria.
- Claim één item met eigenaar en branch, zet het op In progress en werk in kleine PRs.
- Houd scope beperkt tot het item. Leg noodzakelijke afwijkingen en besluiten vast.
- Gebruik geen echte klantdata, geheimen of productiegegevens in repo, issues of tests.
- Werk documentatie, acceptatiebewijs en status bij in dezelfde wijziging.
- Bestaande code eerst begrijpen; voorkom duplicatie en onnodige abstracties.

## Ontwerp en standaarden

- TypeScript strict; geen impliciete any, ongecontroleerde casts of genegeerde fouten.
- Volg DRY, KISS, YAGNI, separation of concerns en SOLID waar dat de eenvoud helpt.
  Deel stabiele domeinregels; abstraheer niet alleen wegens oppervlakkige gelijkenis.
- Gebruik onderhouden libraries voor algemene problemen. Bouw authenticatie,
  cryptografie en fiscale rekentechniek niet achteloos zelf. Beoordeel dependencies
  volgens docs/engineering/standards.md; houd eigen domeinbeleid expliciet.
- Alle code krijgt passende documentatie: moduleverantwoordelijkheid, publieke
  contracten via TSDoc, foutgedrag, invarianten en uitleg van niet-triviale keuzes.
  Geen verplichte commentaarregel bij iedere vanzelfsprekende statement.
- Iedere gedragswijziging heeft relevante geautomatiseerde tests; een bugfix krijgt
  een regressietest. Koppel tests aan acceptatiecriteria. Zie testing.md.

## Financiële en SaaS-invarianten

- Geen binaire floating-pointberekeningen voor geld. Definieer exacte decimalen,
  valuta, precisie en afronding vóór implementatie.
- Debet = credit per definitieve journaalpost. Definitieve boekingen worden gecorrigeerd
  met herleidbare tegenboekingen; nooit stil overschreven of verwijderd.
- Autorizatie en tenant-/administratie-isolatie gelden server-side voor elke toegang,
  achtergrondtaak, export en bijlage. Vertrouw geen tenant-ID uit gebruikersinvoer.
- Boekingen, nummeruitgifte en relevante auditregistratie moeten atomair zijn.
  Voorkom dubbele verwerking met idempotentie en databaseconstraints.
- Fiscale regels zijn versieerbaar op ingangsdatum, voorzien van officiële bron en
  testgevallen. Ondersteun geen uitzondering stilzwijgend via een standaardtarief.

## Verificatie en rapportage

Voer toepasselijke lokale checks uit zodra de toolchain bestaat. Noteer exacte
commando's, commit, omgeving en resultaten; meld blokkades. Verlaag geen kwaliteitsgrens
om een check groen te maken. Controleer bij documentatie links en onderlinge consistentie.
Rapporteer wijziging, bewijs en resterende beperkingen. Publicatie, productiepromotie
en fiscale vrijgave volgen de expliciete gates in docs/operations/otap.md.


## Eerste oplevering: bindende scope

- Volg docs/product/vision.md: boekhoudkern, bronstukken, standaard/eigen grootboek,
  balans en winst-en-verlies, ondernemingsomgeving en toegang.
- Bouw geen payroll, urenregistratie, offertes of verkoopfacturatie in deze oplevering.
  Bestaande facturen/bonnetjes indienen en boeken valt wel binnen scope.
- Productie is passwordless; Entra gebruikt OIDC bovenop OAuth 2.0. E-mailverificatie
  alleen is geen MFA. Volg docs/architecture/identity-access.md voor de afbakening.
- Alleen Development mag de vooraf vastgestelde gebruikersnaam/wachtwoordadapter
  gebruiken. Geen hardcoded credentials en geen automatische fallback buiten O.
