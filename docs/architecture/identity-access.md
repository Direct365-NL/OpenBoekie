# Identiteit, ondernemingsomgeving en toegang

## Vastgestelde richting en nog open keuzes

Productie is passwordless. Entra ID via OpenID Connect (OIDC) op OAuth 2.0 en/of
passwordless e-mailverificatie zijn de beoogde routes. De providerconfiguratie,
keuze voor één/beide routes, MFA-eisen en sessietermijnen zijn nog te besluiten.
OAuth 2.0 regelt autorisatie; OIDC levert de authenticatielaag voor de Entra-route.

Voor de Entra-route moeten bij de providerinrichting een geschikte tenant,
bevoegde beheerder, appregistraties en passwordless beleid worden vastgesteld.
Er wordt geen persoonlijke of bedrijfsspecifieke tenant als beschikbare
projectinfrastructuur aangenomen. Aanmeldroutes en toegestane directories blijven open.

Een e-mailcode of magic link als enige inlogstap is één factor, geen MFA.
Twee stappen via dezelfde mailbox maken dit niet tot twee onafhankelijke factoren.
Als MFA vereist is, kies een door de provider ondersteunde combinatie van onafhankelijke
factoren of een geschikte multifactor-authenticator. Verifieer die combinatie vóór
implementatie; ondersteuning verschilt per Entra-tenanttype en inlogmethode.
Entra SSO alleen garandeert geen passwordless: configureer en test het vereiste
passwordless authenticatiebeleid bij de identity provider. Een eventuele MFA-route
mag het productievereiste passwordless niet ongemerkt vervangen door een wachtwoordflow.

## Omgevingen

| Omgeving | Authenticatie |
| --- | --- |
| Development (O) | Initieel vooraf vastgestelde gebruikersnaam en wachtwoord; alleen lokale ontwikkeltoegang |
| Test (T) | Geïsoleerde testprovider/testdirectory; mocks alleen voor gerichte geautomatiseerde tests |
| Acceptatie (A) | Productieachtige passwordless route(s), eigen registratie en synthetische accounts |
| Productie (P) | Goedgekeurde passwordless route(s), geen lokale wachtwoorden of developmentfallback |

Developmentgegevens worden vooraf via lokale, niet-gecommitte configuratie vastgesteld.
Geen waarden in broncode, voorbeeldbestanden, logs of documentatie. Ze zijn nog niet
gekozen. Een expliciete developmentmodus is vereist; ontbrekende of foutieve authconfig
weigert opstart/toegang en activeert nooit automatisch de developmentlogin.
T/A/P weigeren deze adapter, ook wanneer developmentcredentials aanwezig zijn.
Dezelfde autorisatielaag geldt in alle omgevingen. Tests gebruiken aparte synthetische
identiteiten voor rollen en tenants; de ene developmentgebruiker is geen isolatietest.

## Productieflows en sessies

Gebruik een onderhouden authlibrary/provider. Voor Entra: authorization code flow
met PKCE, exacte redirect-URI's, state/nonce en validatie van handtekening, issuer,
audience en geldigheid. Leg toegestane Entra-tenants/aanmeldgroepen vast; accepteer
niet iedere directory omdat het SaaS-product meerdere ondernemingen ondersteunt.

Voor e-mail: kies een provider met kort geldige, eenmalige codes/links, beperkte
pogingen/verzendsnelheid, bescherming tegen hergebruik en neutrale accountmeldingen.
Verifieer binding aan de aanmeldpoging en voorkom dat linkvoorvertoning ongemerkt
inlogt. Providerkeuze en concrete termijnen volgen in het auth-ADR.

Sessies ondersteunen verlopen, afmelden en intrekking. Gebruik bij cookies Secure,
HttpOnly, passend SameSite en CSRF-bescherming. Bewaar geen tokens in logs. Een
verlopen of ingetrokken sessie kan niet boeken, exporteren of documenten ophalen.
Beheer account recovery en tweede methode via expliciete herverificatie; geen
stilzwijgende samenvoeging van accounts op alleen hetzelfde e-mailadres.

## Organisaties en autorisatie

Een interne gebruiker koppelt aan een geverifieerde provideridentiteit (issuer +
subject; gebruik bij Entra de passend gevalideerde tenant/object-identificatie).
E-mailadres is contactinformatie, geen onveranderlijke autorisatiesleutel. De
Entra-directorytenant en de applicatieonderneming zijn verschillende concepten.
Lidmaatschap met rol per administratie bepaalt toegang, niet alleen succesvolle login
of een overeenkomend e-maildomein. Nieuwe gebruikers krijgen geen bestaande tenant toegewezen.

Eén gebruikersaccount kan lid zijn van meerdere organisaties en binnen de applicatie
wisselen tussen toegankelijke organisaties en administraties (besluit 27 oktober
2026). Toon de actieve organisatie en administratie duidelijk. De wisselaar toont
alleen toegankelijke omgevingen; de server controleert bij elke aanvraag opnieuw
het betreffende lidmaatschap en de rechten. Wisselen neemt geen rol of gegevens
uit de vorige administratie over. Een verouderd scherm mag door een wissel niet
ongemerkt een mutatie in een andere administratie opslaan. Werk de omgang met
onopgeslagen invoer en meerdere tabbladen vóór Ready uit.

Bij onboarding worden onderneming, eerste administratie, eigenaar-lidmaatschap en
standaardrekeningschema consistent aangemaakt; retries maken geen tweede onderneming.
Uitnodigingen zijn eenmalig, verlopen en gebonden aan de bedoelde geverifieerde
identiteit. Een onbevoegde kan zichzelf niet uitnodigen of zijn rol verhogen.

## Rollenmodel voor de eerste oplevering

Uitgewerkt op 27 oktober 2026 op verzoek van `Carlovdv` om best practices toe te
passen. Uitgangspunten: minimale benodigde rechten, standaard weigeren en
server-side controle bij iedere toegang. De concrete rollen hieronder zijn een
projectkeuze, geen door OWASP voorgeschreven rollenlijst. Dit model vervangt de
voorgaande voorgestelde matrix; UC-0001 blijft Draft tot verdere specificatie en review.

Iedere organisatie heeft een eigen team. Eigenaar en Admin zijn organisatierollen;
Finance, Medewerker en Viewer worden voor expliciet toegewezen administraties
verleend. Eén gebruiker kan rollen combineren en in een andere organisatie andere
rechten hebben. Admin geeft op zichzelf geen financiële inzage of boekingsrechten;
voor een beheerder die ook boekhoudt kan de eigenaar aanvullend Finance toekennen.

| Rol | Bevoegdheden en grenzen |
| --- | --- |
| Eigenaar | Eindverantwoordelijke binnen de organisatie; beheert eigenaarschap, alle teamrollen en organisatie-instellingen, met financiële toegang tot de eigen administraties. Geen rechten in andere organisaties. |
| Admin | Dagelijks organisatie- en teambeheer; beheert algemene instellingen en uitnodigingen voor Medewerker en Viewer binnen door de eigenaar vastgestelde administratiegrenzen. Kan geen Eigenaar, Admin of Finance toekennen, zichzelf promoveren of eigenaarschap overdragen. |
| Finance | Financiële instellingen inclusief KOR, relaties, grootboek, stukken beoordelen, definitief boeken, corrigeren, betalingen afletteren, boekjaren afsluiten/heropenen en financiële exports binnen toegewezen administraties. Geen team- of eigenaarsbeheer. |
| Medewerker | Stukken indienen en eigen indieningen/status bekijken. Geen definitieve boekingen, goedkeuringen, volledige rapportages of exports. |
| Viewer | Boekingen, rapportages en bijbehorende bronstukken lezen binnen toegewezen administraties. Geen wijzigingen, teambeheer of volledige administratie-export. |

De eerdere rol Boekhouder heet Finance; Lezer heet Viewer. De rol Medewerker blijft
nodig voor de reeds afgesproken algemene indieningsflow. Developer en Support
worden pas toegevoegd zodra concrete taken en begrensde rechten nodig zijn.
Custom rollen vallen voorlopig buiten de eerste oplevering; beoordeel ze opnieuw
bij een aantoonbaar tekort in de standaardrollen. Platformsupport is geen gewoon
organisatieteamlid: eventuele toegang blijft tijdelijk, expliciet en gelogd volgens
het securitybeleid.

De aangewezen financieel verantwoordelijke krijgt Finance voor de betreffende
administratie. Binnen vrijwilligersscenario's mag voorlopig uitsluitend deze gebruiker
namens vrijwilligers indienen, zelf goedkeuren en definitief boeken, zoals eerder
besloten. Het systeem moet deze aanwijzing naast de algemene rol kunnen controleren;
Finance alleen geeft deze aanwijzing niet automatisch. De eigenaar kan het team
en deze aanwijzing beheren. Dit is een expliciete uitzondering op een
mogelijk vierogenproces; er wordt geen extra goedkeurder verplicht gesteld.

Alle rechten blijven gebonden aan de organisatie/administratie van het object.
Ook een eigenaar kan geen definitieve boekingen wissen of financiële invarianten
omzeilen. Laatste eigenaar kan niet zonder overdracht worden verwijderd. Overdracht
vereist herverificatie en aanvaarding door de nieuwe eigenaar; bescherm het behouden
van een eigenaar ook bij gelijktijdige wijzigingen. MFA voor beheertoegang blijft
verplicht volgens het bestaande securitybeleid.

Intrekking of rolverlaging werkt bij de eerstvolgende autorisatiecontrole, ook in
bestaande sessies. Iedere rolwijziging registreert actor, tijd, doelgebruiker,
organisatie/administratie en oude/nieuwe rechten. Rollen combineren mag nooit de
organisatiegrens of expliciete procesbeperkingen omzeilen. Test weigeringen net zo
expliciet als toegestane handelingen, inclusief zelfpromotie, onbevoegde roltoekenning,
exports, bestanden en verouderde sessies.

## Bronnen

Geraadpleegd 26 oktober 2026:
- [Microsoft OIDC](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols-oidc)
- [Microsoft applicatietypen en authorization code met PKCE](https://learn.microsoft.com/en-us/entra/identity-platform/v2-app-types)
- [E-mailcodes voor B2B-gasten; geen universele SaaS-e-mailprovider](https://learn.microsoft.com/entra/external-id/one-time-passcode)

Deze bronnen beschrijven mogelijkheden. Het hierboven beschreven beveiligings- en
omgevingsbeleid is een projectvereiste, geen claim dat de provider dit al afdwingt.

Autorisatiebron, geraadpleegd 27 oktober 2026:
- [OWASP Authorization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html): minimale rechten, standaard weigeren en controles bij iedere aanvraag.
