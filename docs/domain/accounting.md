# Domein en invarianten

Een tenant is een organisatiegrens; een administratie bevat één samenhangende
boekhouding. Een organisatie kan meerdere administraties hebben. Iedere transactie,
relatie, bijlage en rapportage behoort tot een expliciete administratie en tenant.

| Begrip | Betekenis |
| --- | --- |
| Grootboekrekening | Rubriek waarop debet- en creditregels worden vastgelegd |
| Dagboek | Verzameling boekingen, zoals verkoop, inkoop, bank of memoriaal |
| Journaalpost | Samenhangende regels waarvan debet en credit gelijk zijn |
| Openstaande post | Te ontvangen of te betalen bedrag met afletteringen |
| Interne boekstukreferentie | Optionele, voorlopig handmatig ingevulde interne referentie, onderscheiden van mutatienummer, extern factuurnummer en bestandsbijlage; formaat en uniciteit zijn nog te bepalen |
| Mutatienummer | Pas bij definitief boeken automatisch toegekende, unieke en oplopende identificatie per administratie; onveranderlijk en nooit hergebruikt; formaat is nog te bepalen |
| Creditnota | Correctiedocument met verwijzing naar oorspronkelijke factuur |
| Boekdatum | Datum die de rapportageperiode bepaalt volgens vastgelegd beleid |
| Auditgebeurtenis | Herleidbare registratie van actor, actie, tijd en object |

## Verplichte ontwerpregels

Definitief geboekte financiële mutaties hebben een mutatienummer, datum, referentie en bedrag; op elk
van deze gegevens kan worden gezocht binnen de bestaande autorisatiegrenzen.
Facturen hebben daarnaast een relatie. Dit productbesluit van 27 oktober 2026
vereist vóór Ready uitwerking van datumsoort, bedragdefinitie (inclusief teken),
mutatiereferentie versus boekstukreferentie en nummerformaat. Een zoekresultaat
mag geen gegevens uit een onbevoegde administratie of tenant tonen.

Mutatienummers worden pas bij definitief boeken automatisch, uniek en oplopend per
administratie toegekend. De reeks loopt over boekjaren heen door en wordt niet
gereset bij een jaarovergang. Concepten hebben geen mutatienummer; een interne technische
identificatie van een concept is geen mutatienummer. Verwijderen van een concept
beïnvloedt de nummerreeks niet. Een toegekend nummer kan niet worden gewijzigd of
hergebruikt. Definitieve boekingen worden niet verwijderd; tegenboekingen krijgen
een eigen nieuw nummer met verwijzing naar de originele post. Na nummers 1 t/m 10
krijgt de eerstvolgende definitieve boeking 11, ook als deze post 3 tegenboekt.
Boeking, nummeruitgifte en relevante auditregistratie zijn atomair. Gelijktijdige
boekingen mogen geen dubbele nummers opleveren; retries behouden het nummer van
een bestaande mutatie. Technisch gedrag van reserveringen bij rollback is nog uit
te werken; er is geen eis van een volledig aaneengesloten reeks vastgelegd.

1. Concepten zijn wijzigbaar; definitieve boekingen zijn onveranderlijk. Correcties
   verlopen via gekoppelde tegenboeking en zo nodig een vervangende boeking.
2. Een boeking in een afgesloten periode wordt geweigerd. In de eerste oplevering
   is de afsluitperiode het volledige boekjaar; maanden worden niet afzonderlijk
   afgesloten. Heropening van het boekjaar is een apart bevoegd proces met reden
   en audittrail. Rapportageperioden staan los van deze afsluitperiode.
3. Geld gebruikt exacte decimalen en expliciete valuta; berekeningen bewaren
   voldoende precisie. Leg afronding per regel/document vast en test grensgevallen.
4. Boekdatum en factuurdatum zijn kalenderdatums; auditmomenten zijn UTC-tijdstempels.
   Nederlandse weergave gebruikt Europe/Amsterdam zonder datums te verschuiven.
5. Bij ingediende documenten bewaren we het externe factuurnummer en de afzender.
   Dat nummer is niet wereldwijd uniek: verschillende leveranciers mogen hetzelfde
   nummer gebruiken. Signaleer mogelijke duplicaten op passende combinatie van
   administratie, relatie, documenttype, nummer en inhoud. Geen eigen factuurnummeruitgifte
   in deze oplevering. Definitieve registraties bewaren een snapshot van relatiegegevens,
   bedragen en toegepaste fiscale regels; het originele bestand blijft behouden.
6. Boeken en benodigde status-/auditwijzigingen vormen één transactie. Externe
   verzending volgt na commit via herhaalbaar proces; een retry maakt geen tweede boeking.
7. Rapportages steunen op definitieve boekingen met expliciete periode en peildatum.
   Openstaande posten ondersteunen deelbetaling en herleidbare aflettering.
   Een geboekte factuur of vrijwilligersvergoeding en de betaling zijn afzonderlijke
   registraties. Eén betaling kan over meerdere openstaande posten worden verdeeld;
   één post kan via meerdere deelbetalingen worden afgewikkeld. Iedere toewijzing
   bewaart het exacte bedrag en de koppeling binnen dezelfde administratie.
   Een betaalbedrag mag niet dubbel worden toegewezen; verschillen blijven expliciet.
   Facturen binnen één betaling mogen verschillende leveranciers hebben. Bewaar de
   oorspronkelijke leverancier per factuur en onderscheid deze van de betaalontvanger
   (zoals een marketplace of moederbedrijf). Aflettering voegt leveranciers niet
   samen en verplaatst geen posten tussen administraties of tenants.
8. Bewaar bronstukken en relaties naar boekingen. Auditlogs bevatten minimale
   persoonsgegevens en zijn beschermd tegen wijziging door gewone gebruikers.

Dit zijn productinvarianten, geen uitspraak dat elk detail wettelijk verplicht is.
Fiscale beslissingen volgen [Nederlandse regels](netherlands.md).


## Grootboek en rapportages in de eerste oplevering

In de eerste oplevering is het boekjaar gelijk aan het kalenderjaar:
1 januari t/m 31 december. Gebroken boekjaren vallen buiten de eerste oplevering
en worden later uitgewerkt in [UC-0012](../backlog/use-cases/UC-0012-broken-financial-year.md).
De mutatienummerreeks loopt onafhankelijk van boekjaargrenzen door.

Elke administratie start met een versieerbaar standaardrekeningschema. De concrete
rekeningnummers en Nederlandse rubrieken worden inhoudelijk gereviewd; het schema is
een producttemplate, geen verondersteld wettelijk verplicht universeel schema.
Eigen rekeningen hebben een binnen de administratie unieke code, naam, type (activa,
passiva/eigen vermogen, opbrengsten of kosten) en rapportagerubriek. Ongebruikte
rekeningen kunnen aangepast worden; gebruikte rekeningen niet verwijderen of zonder
migratiebeleid herclassificeren. Deactiveren blokkeert nieuwe boekingen maar behoudt historie.
Een template-update verandert bestaande administraties niet stilzwijgend.

De winst-en-verliesrekening bevat opbrengsten en kosten in de gekozen periode;
de balans toont standen op peildatum inclusief beginbalans en verwerkt resultaat.
Verwerk lopend resultaat en jaarafsluiting zonder dubbeltelling. Leg tekenconventie,
de verwerking van de vastgestelde kalenderboekjaargrenzen en resultaatbestemming
vast vóór rapportages Ready worden.
Beide rapportages sluiten aan op dezelfde definitieve journaalregels en bieden
herleiding via grootboekkaart naar bronstuk. Concepten tellen niet mee.
