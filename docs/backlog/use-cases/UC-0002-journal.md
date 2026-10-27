# UC-0002 — Journaalpost boeken

Status: Draft. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: bevoegde boekhouder. Doel: een geldige journaalpost definitief vastleggen.
Scope: concept valideren, atomair boeken en audittrail. Uitgesloten: facturatie.

- AC-1: Gegeven een open periode en gebalanceerde regels op geldige rekeningen,
  wanneer geboekt wordt, dan zijn alle regels en auditregistratie atomair definitief.
- AC-2: Gegeven ongelijke debet-/credittotalen of een afgesloten periode,
  wanneer geboekt wordt, dan volgt een uitlegbare fout zonder gedeeltelijke mutatie.
- AC-3: Gegeven een identieke herhaalde opdracht met dezelfde idempotentiesleutel,
  dan ontstaat geen tweede journaalpost; afwijkende inhoud wordt geweigerd.
- AC-4: Gegeven een definitieve post, dan wordt direct wijzigen/verwijderen geweigerd.
- AC-5: Definitief geboekte financiële mutaties hebben een mutatienummer, datum, referentie en bedrag.
  Een bevoegde gebruiker kan op elk van deze velden zoeken; resultaten respecteren
  de administratie-, tenant- en rolgrenzen. Factuurmutaties hebben ook een relatie.
- AC-6: Het systeem kent pas bij definitief boeken automatisch een uniek, oplopend
  mutatienummer per administratie toe, atomair met de boeking en auditregistratie.
  Concepten hebben geen mutatienummer. Wijzigen van een toegekend nummer wordt geweigerd.
  De reeks loopt over boekjaren heen door; een jaarovergang zet de teller niet terug.
- AC-7: Verwijderen van een verwijderbaar concept beïnvloedt de nummerreeks niet.
  Definitieve posten kunnen niet worden verwijderd en nummers worden niet hergebruikt.
  Na uitgifte van 1 t/m 10 krijgt een eerstvolgende tegenboeking van post 3 nummer 11;
  post 3 blijft met haar oorspronkelijke nummer behouden.
- AC-8: Gelijktijdig definitief boeken levert geen dubbele mutatienummers op; een retry van
  een reeds verwerkte opdracht behoudt de bestaande mutatie en haar nummer.

Aanvullend scopebesluit van 27 oktober 2026: AC-5 is het gedeelde contract voor
financiële mutaties, inclusief facturen en betalingen. Vóór Ready uitwerken:
nummerformaat, datumsoort, bedragdefinitie en tekenconventie,
betekenis van de mutatiereferentie versus de optionele handmatige boekstukreferentie,
en zoekgedrag. Test zoeken op ieder veld, gelijke waarden bij verschillende posten
en weigering van inzage buiten de eigen rechten. De use-case blijft Draft.
Aanvullend testplan: concept opslaan zonder mutatienummer, concept verwijderen zonder
invloed op de reeks, nummerwijziging weigeren, tegenboeking met nieuw nummer, concurrente
uitgifte, idempotente retries en onafhankelijke nummerreeksen per administratie.
Werk ook het gedrag bij mislukte aanmaak en rollback uit vóór Ready.
Test de jaarovergang: na mutatienummer 100 volgt bij de eerstvolgende definitieve
boeking in het nieuwe boekjaar nummer 101, zonder een nieuwe jaarreeks te starten.

Testplan: exacte bedragen, property-based balans, transactie-rollback, concurrency,
tenantisolatie en regressie voor dubbele verwerking.
Nog nodig voor Ready: rekeningmodel, afrondingsbeleid, idempotentiecontract,
afsluitbeleid, correctie-use-case, eigenaar en inhoudelijke goedkeuring.


Aanvullende afhankelijkheid: UC-0005 (grootboek). Periode- en correctieregels zijn
gezamenlijk af te stemmen met UC-0008; UC-0008 bouwt voort op deze boekingskern.
