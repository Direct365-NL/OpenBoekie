# ADR-0001 — Modulaire monoliet

Status: Proposed. Datum: 2026-10-26. Beslisser: nog vast te leggen.

## Context

Een eenvoudige boekhoud-SaaS vraagt sterke transacties en een kleine beheerlast.
TypeScript is gegeven; omvang, team en belasting zijn nog onbekend.

## Voorstel

Eén repository met web, API en expliciete domein-/applicatie-/adaptergrenzen.
Begin met één backend en een transactionele database. Houd integraties achter poorten.

## Alternatieven en gevolgen

Microservices vergroten netwerk-, consistentie- en beheercomplexiteit en zijn nu
niet nodig. Eén ongestructureerde full-stackcodebase start sneller maar maakt het
moeilijker om fiscale regels onafhankelijk te testen. De voorgestelde grenzen vragen
discipline; splits pas services af bij aantoonbare operationele noodzaak.

## Validatie

Toets de keuze met de eerste verticale slice: tenantautorisatie, één atomische
journaalpost en herleidbare rapportage. Accepteer het ADR na review, vóór die bouw.
