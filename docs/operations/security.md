# Security, privacy en beheer

## Minimale ontwerpvereisten

Server-side autorisatie op tenant én administratie bij elke aanvraag, achtergrondtaak,
zoekopdracht, export en bestandsdownload. Test IDOR, ingetrokken lidmaatschap en rollen.
Gebruik bewezen auth, sessiebeleid, MFA voor beheertoegang, TLS, secretsbeheer en
minimale database-/opslagrechten. Logs bevatten geen tokens of volledige documenten.
Bescherm uploads met type-/groottelimieten, veilige opslag en malwarebeleid.

Leg vóór productie een dreigingsmodel, rechtenmatrix, verwerkersoverzicht,
privacyinformatie en datastromen vast. Maak onderscheid tussen operationele logs,
audittrail en fiscale bronstukken. Toegang door support is tijdelijk, expliciet en
gelogd; publieke repository en issues bevatten uitsluitend synthetische voorbeelden.

## Levenscyclus en beschikbaarheid

Export omvat documenten, journaalregels, relaties en betekenis van velden zodat
gegevens na beëindiging bruikbaar blijven. Stel bewaartermijnen en verwijderbeleid
per categorie vast op basis van actuele wettelijke grondslag; accountverwijdering
mag niet blind fiscale gegevens wissen. Beoordeel privacyrechten en bewaarplichten
bij de concrete situatie vóór automatische verwijderfuncties worden ingevoerd.

Backups zijn versleuteld en gescheiden beveiligd. Leg frequentie, retentie, regio,
RPO en RTO vast vóór Acceptatie. Voer periodieke restoreproeven uit, inclusief
database, documenten en hun onderlinge verwijzingen. Monitor fouten, mislukte taken,
ongeautoriseerde toegang en boekhoudkundige inconsistenties met concrete eigenaren.
Vóór productie zijn alertdrempels, incidentcontact en herstelrunbook verplicht.


## Eerste oplevering: toegang

[Identiteit en toegang](../architecture/identity-access.md) is leidend voor het
omgevingsspecifieke authbeleid en de voorgestelde rollen. Geen productie-wachtwoorden
of developmentfallback. E-mail als enige factor is geen MFA. Het bestaande MFA-vereiste
voor beheertoegang blijft gelden; gewone gebruikers en kritieke handelingen krijgen
een expliciet vastgesteld beleid. Recovery mag de vereiste bescherming niet omzeilen.
