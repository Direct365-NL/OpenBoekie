# production

Echte gegevens; alleen na expliciete releasegoedkeuring en geslaagde OTAP-gates.

Nog niet ingericht. Leg bij inrichting eigenaar, regio, endpoints, toegangsrollen,
secretreferenties (geen waarden), datastore, backupbeleid en deploy-/herstelprocedure vast.
Zie docs/operations/otap.md vanuit de repository-root.


Authenticatie: Uitsluitend goedgekeurde passwordless routes; developmentlogin en wachtwoordfallback worden geweigerd.
Zie docs/architecture/identity-access.md vanuit de repository-root.
