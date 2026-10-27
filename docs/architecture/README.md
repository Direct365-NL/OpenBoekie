# Architectuur

Voorgesteld vertrekpunt: een modulaire monoliet in één TypeScript-repository.
Web en API zijn afzonderlijke applicatiegrenzen; de server blijft één logische
applicatie. Geen microservices, generieke eventbus of event sourcing bij de start.
Zie [ADR-0001](adr/0001-modular-monolith.md).

Afhankelijkheidsrichting: web → API-contract; API → application → domain.
Infrastructure implementeert poorten uit application en wordt in de API samengesteld.
Domain importeert geen UI-, framework-, ORM- of infrastructuurcode. UI bevat geen
gezaghebbende fiscale berekeningen; de server valideert elke aanvraag opnieuw.

## Modules en grenzen

Identiteit/toegang, administraties, grootboek, relaties, bewijsstukverwerking, bank/kas,
btw, rapportages en documenten vormen functionele grenzen. Maak pas mappen en
publieke contracten wanneer een use-case ze nodig heeft. Geen gedeeld utils-pakket
als verzamelbak; deel alleen expliciet benoemde stabiele concepten.

Een relationele database met transacties en constraints is het voorstel. De keuze
van engine en tenantisolatie vereist een ADR met concurrentie- en securitytests.
Bestandsopslag is privé; toegang via geautoriseerde, kort geldige downloads.
Migraties zijn versieerbaar en worden getest op bestaande gegevens en herstel.

API-contracten beschrijven validatie, rechten, fouten, idempotentie en versiebeleid.
Gebruik een bewezen sessie-/identiteitsoplossing. Correlatie-ID's verbinden requests,
audit en operationele logs zonder gevoelige inhoud te loggen.

## Beslissingen vóór de eerste verticale slice

Kies ondersteunde runtime en package manager, web-/serverframework, database en
migratietooling, validatie, exact rekenen, auth en tests. Vergelijk enkele opties op
onderhoud, eenvoud, licentie, beveiliging en transactiemodel. Leg versies vast in
de toekomstige toolchain en lockfile; kies geen dependency alleen op populariteit.


## Eerste oplevering en identiteit

De modulegrenzen volgen [de boekhoudscope](../product/vision.md). Verwerken van extern
opgestelde facturen is geen verkoopfacturatiemodule. Rapportages steunen op de
boekhoudkern en het rekeningschema. Zie [identiteit en toegang](identity-access.md)
voor ondernemingsisolatie, developmentlogin, passwordless productie en de rechtenmatrix.
Een auth-adapter mag verschillen per omgeving; applicatieautorisatie blijft dezelfde.
