# Coding- en documentatiestandaarden

KISS: kies de eenvoudigste oplossing die alle afgesproken eisen afdekt. YAGNI:
bouw geen speculatieve mogelijkheden. DRY: leg dezelfde bedrijfsregel één keer vast,
maar forceer geen abstractie tussen concepten die toevallig dezelfde vorm hebben.
Functies en modules hebben één duidelijke verantwoordelijkheid; afhankelijkheden
zijn expliciet en IO blijft buiten de domeinkern.

TypeScript strict, expliciete publieke types, unknown voor onbetrouwbare invoer,
runtimevalidatie aan grenzen en exhaustieve verwerking van domeintoestanden.
Gebruik voorspelbare fouttypen, geen stil ingeslikte exceptions. Maak taal, locale,
datums, geld en null/undefinedbeleid consistent en gedocumenteerd.

## Libraries

Gebruik onderhouden libraries waar die betrouwbaarheid en onderhoud verbeteren.
Beoordeel onderhoudsactiviteit, beveiliging, licentie, TypeScript-ondersteuning,
transitieve dependencies, prestaties en vervangbaarheid. Noteer doel en keuze.
Eigen helpers zijn passend bij klein, helder gedrag; geen eigen crypto/authframework.
Pin via lockfile, review updates en beoordeel advisories lokaal vóór releases.

## Volledige documentatie

Iedere module documenteert doel, grenzen en gebruik. Publieke functies/types krijgen
TSDoc met contract, relevante fouten en randvoorwaarden. Complexe interne logica
documenteert het waarom, invarianten en rekenvoorbeelden. Beschrijf API's, configuratie,
migraties en herstel zodra ze bestaan. Tests vormen voorbeelden maar vervangen geen
contractdocumentatie. Verouderde documentatie is een defect.

Een toekomstige lokale check voert formatter, linter, typecheck, tests en build uit.
Selecteer tools in een ADR en publiceer echte commando's bij introductie. Voeg geen
schijnbaar werkende scripts of kwaliteitsbadges toe zolang ze ontbreken.
