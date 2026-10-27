# UC-0003 — Reguliere Nederlandse verkoopfactuur

Status: Deferred — buiten de eerste oplevering. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: bevoegde gebruiker. Doel: een controleerbare verkoopfactuur definitief maken.
Scope: EUR, reguliere binnenlandse btw en gekoppelde journaalpost.
Uitgesloten: verzending, buitenlandse transacties, bijzondere btw-regelingen.

- AC-1: Gegeven een volledig geldig concept, wanneer definitief gemaakt,
  dan krijgt de factuur een uniek nummer en een onveranderlijk gegevenssnapshot.
- AC-2: Gegeven ontbrekende verplichte velden of een niet-ondersteunde fiscale situatie,
  dan wordt definitief maken geweigerd met een gerichte melding.
- AC-3: Gegeven gelijktijdige verzoeken, dan worden geen nummers dubbel uitgegeven;
  factuur en financiële boeking blijven consistent bij een fout.
- AC-4: Alle bedragen en btw zijn te herleiden tot regels en de vastgelegde rekenversie.

Testplan: fiscale veldmatrix, onafhankelijke rekenvoorbeelden, concurrency en
rollback, rolrechten en historische snapshots na wijziging van relatiegegevens.
Bronnen: docs/product/references.md, onderdeel factuureisen en facturen maken.
Nog nodig voor Ready: tarieven/uitzonderingen, nummerbeleid, afronding,
creditnotaproces, exacte veldmatrix, eigenaar en fiscale review.


Scopebesluit: behouden als toekomstig voorstel, niet selecteren voor de eerste
oplevering. Bestaande facturen en bonnetjes indienen valt onder UC-0006; deze
use-case betreft zelf facturen opstellen. Het UC-nummer wordt niet hergebruikt.
