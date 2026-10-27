# UC-0001 — Administratie en toegang

Status: Draft. Eigenaar: niet toegewezen. GitHub-issue: nog niet aangemaakt.

Actor: organisatie-eigenaar. Doel: een afgeschermde administratie aanmaken.
Scope: eigen onderneming (tenant), eerste administratie, eigenaar-lidmaatschap,
standaardrekeningschema en expliciete rechten. Zie
[identiteit en toegang](../../architecture/identity-access.md).
Uitgesloten: betalende abonnementen en accountantportaal.

- AC-1: Gegeven een ingelogde eigenaar, wanneer geldige administratiegegevens
  worden aangeboden, dan wordt precies één administratie binnen diens organisatie gemaakt.
- AC-2: Gegeven een gebruiker zonder lidmaatschap, wanneer die een administratie-ID
  van een andere tenant gebruikt, dan worden toegang en wijziging geweigerd zonder datalek.
- AC-3: Gegeven ingetrokken toegang, wanneer een volgende aanvraag binnenkomt,
  dan wordt die op actuele rechten beoordeeld en zo nodig geweigerd.

Testplan: rolmatrix, cross-tenant integratietest en E2E aanmaak/weigering.
Nog nodig voor Ready: exacte rolmatrix, verplichte velden, authkeuze, tenantmodel,
retrybeleid, eigenaar en productgoedkeuring.


- AC-4: Gegeven een geauthenticeerde nieuwe gebruiker, wanneer onboarding slaagt,
  dan bestaan onderneming, administratie, eigenaar-lidmaatschap en standaardrekeningen
  consistent; een retry maakt geen duplicaat en een fout laat geen halve inrichting achter.
- AC-5: Gegeven een onbevoegde gebruiker, dan kan deze geen leden uitnodigen of rollen
  verhogen. De laatste eigenaar verwijderen zonder overdracht wordt geweigerd.
- AC-6: Gegeven een uitnodiging, dan kan alleen de bedoelde geverifieerde identiteit
  deze binnen de geldigheid eenmaal accepteren; verlopen en hergebruik worden geweigerd.

Aanvullend testplan: onboarding-rollback/retries, uitnodigingen, rolverhoging en
laatste eigenaar. Afhankelijkheden: UC-0004 en UC-0005; accepteer rechtenmatrix en
onboardingvelden vóór Ready. Productieacceptatie van toegang vereist UC-0011.

## Aanvulling: KOR in bedrijfsinstellingen

Scopebesluit van 26 oktober 2026; status blijft Draft.

- AC-7: Een bevoegde eigenaar kan KOR-deelname vastleggen met een verplichte
  ingangsdatum en optionele einddatum en de vastgelegde historie terugzien.
- AC-8: Ongeldige datumvolgorde en overlappende KOR-perioden worden geweigerd;
  onbevoegde gebruikers kunnen de instelling niet wijzigen.
- AC-9: Een wijziging legt actor, tijd en oude/nieuwe waarden vast en wijzigt geen
  definitieve boekingen stilzwijgend.

Nog nodig voor Ready: datumgrenzen (inclusief/exclusief), beleid voor terugwerkende
wijzigingen en gesloten perioden, plaats van de instelling bij meerdere administraties,
fiscale review en aansluiting op UC-0006 en UC-0010. Aanvullend testplan: open einddatum,
datumgrenzen, opeenvolgende/overlappende perioden, rechten, tenantisolatie en historie.

## Aanvulling: één account voor meerdere organisaties

Scopebesluit van 27 oktober 2026; status blijft Draft.

- AC-10: Een gebruiker met geldige lidmaatschappen voor meerdere organisaties
  kan met één account binnen de applicatie tussen deze organisaties wisselen. De actieve
  organisatie en administratie zijn zichtbaar.
- AC-11: De wisselaar toont alleen toegankelijke omgevingen. Iedere aanvraag wordt
  server-side op actuele rechten voor de betreffende administratie gecontroleerd;
  rollen en gegevens uit de vorige omgeving verlenen geen toegang in de andere.
- AC-12: Na intrekking van een lidmaatschap geeft een bestaande sessie of directe
  URL geen toegang meer tot die omgeving. Een wissel mag invoer uit een oud scherm
  niet ongemerkt in een andere administratie opslaan.

Aanvullend testplan: één account met twee organisaties en verschillende rollen,
wisselen, ingetrokken lidmaatschap, directe URL's en gescheiden gegevens/resultaten.
Nog nodig vóór Ready: UX voor onopgeslagen invoer en meerdere tabbladen, plus de
uitwerking van rollen en lidmaatschappen voor beide omgevingen.

## Aanvulling: team per organisatie

Productrichting van 27 oktober 2026; status blijft Draft.

- AC-13: Iedere organisatie heeft een eigen team met meerdere gebruikers. Dezelfde
  gebruiker kan lid zijn van meerdere teams met verschillende rechten; een teamrol
  geeft nooit automatisch toegang tot een andere organisatie.

Het op verzoek om best practices uitgewerkte [rollenmodel](../../architecture/identity-access.md)
van 27 oktober 2026 is leidend: Eigenaar, Admin, Finance, Medewerker en Viewer.
Developer, Support en custom rollen vallen voorlopig buiten de eerste oplevering.
- AC-14: Admin kan uitsluitend de toegestane teamrollen en administratiegrenzen
  beheren en kan zichzelf of anderen geen Eigenaar-, Admin- of Finance-rechten geven.
  Financiële inzage en handelingen vereisen afzonderlijk passende financiële rechten.
- AC-15: Finance kan binnen toegewezen administraties financieel werk verrichten,
  inclusief afsluiten/heropenen, maar geen teamrollen beheren. Viewer kan alleen lezen;
  Medewerker heeft uitsluitend toegang tot de toegestane indieningsflow.
- AC-16: Rolwijzigingen zijn geaudit en intrekking geldt bij de volgende aanvraag.
  Eigendomsoverdracht vereist herverificatie en aanvaarding; de laatste eigenaar
  kan niet zonder geldige overdracht worden verwijderd.

Nog nodig vóór Ready: concrete permissies en beheerflows, aanwijzing van de
financieel verantwoordelijke voor vrijwilligersscenario's, combinaties van rollen en review.
Test ieder recht en iedere weigering, in het bijzonder zelfpromotie, verschillende
administraties, rolintrekking, concurrency en behoud van de laatste eigenaar.
