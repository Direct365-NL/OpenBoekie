# UC-0005 — Standaard en eigen grootboekrekeningen

Status: Draft. Oplevering: eerste. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: Eigenaar/boekhouder.
Scope: Standaardschema, eigen rekeningen, aanpassing en deactivering.

- AC-1: Een nieuw schema levert de gereviewde standaardrekeningen met versie; herhaald initialiseren maakt geen dubbele codes.
- AC-2: Een bevoegde gebruiker kan een rekening met unieke code, naam, type en rapportagerubriek aanmaken; dubbele codes en ontbrekende rubrieken worden geweigerd.
- AC-3: Een gebruikte rekening kan niet verwijderd of ongecontroleerd geherclassificeerd worden; deactivering behoudt historische rapportages en weigert nieuwe boekingen.
- AC-4: Een wijziging van het standaardtemplate wijzigt bestaande administraties niet zonder expliciete migratie.

Afhankelijkheden: Tenant/autorisatiecontract uit UC-0001; schemafunctie vooraf bouwbaar.
Gebruik de algemene inkomsten- en uitgavencategorieën uit de
[productscope](../../product/vision.md) bij het uitwerken van het schema, inclusief
vrijwilligersvergoedingen. Bepaal rekeningtypes en rapportagerubrieken na inhoudelijke
review; de opgegeven categorieën zijn nog geen definitieve rekeningen of btw-codes.
Testplan: ieder AC krijgt positieve/negatieve tests op passend unit-, integratie- of
E2E-niveau, inclusief tenantisolatie en autorisatie. Financiële tests gebruiken
onafhankelijk berekende fixtures; auth-tests verifiëren ook geweigerde toegang.
Nog nodig voor Ready: Concrete standaardrekeningen, systeemrekeningen, wijzigingsbeleid en boekhoudkundige review. Eigenaar, scenario-uitwerking en productgoedkeuring.
Raadpleeg [scope](../../product/vision.md), [domein](../../domain/accounting.md) en
[identiteit](../../architecture/identity-access.md) voor de bijbehorende invarianten.
