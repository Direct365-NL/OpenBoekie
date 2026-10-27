# Controle licentie en domein

Datum: 27 oktober 2026. Uitvoerder: Codex. Omgeving: macOS, zsh, Python 3.
Branch: `docs/licentie-en-domein`. Basiscommit: `d034cba` (Initial Commit).
Bewijs betreft de ongecommitte werkbestanden; maintainerreview en integratie volgen.

Scope: officiële LICENSE, AGPL-3.0-only-vermelding, bijdragenbeleid, gratis eigen
SaaS en domeincorrectie. Rechtstreeks gevraagd documentatiewerk, geen uitvoering
van UC-0013. Geen GitHub-instellingen of applicatiecode gewijzigd.

Controles:

- `curl -fsSL https://www.gnu.org/licenses/agpl-3.0.txt -o /tmp/openboekie-agpl-3.0.txt`:
  officiële tekst opgehaald; eerst DNS-blokkade in sandbox, daarna succesvol met toestemming.
- `cmp LICENSE /tmp/openboekie-agpl-3.0.txt`: identieke bestanden, exitcode 0.
- `git diff --check`: geslaagd, geen whitespacefouten in de gevolgde wijzigingen.
- Lokale Markdown-bestandslinks gecontroleerd met Python (`Path.rglob('*.md')`,
  extractie van Markdown-linkdoelen, URL's/ankers overgeslagen, `Path.exists()`):
  geen ontbrekende bestandsdoelen. Nieuwe README-ankerverwijzing handmatig gecontroleerd.
- Handmatig: uitsluitend versie 3 expliciet in README; standaardlicentietekst
  ongewijzigd. Gratis eigen SaaS gescheiden van rechten van derden onder de AGPL.
  Domein openbookie.nl opnieuw bevestigd; governance legt vast dat de
  tussentijdse domeincorrectie is vervallen.

Geen applicatietests/build: geen toolchain. Geen publicatie of fiscale vrijgave.

Aanvullende domeincontrole: alle actuele verwijzingen gebruiken `openbookie.nl`.
`git diff --check` opnieuw uitgevoerd zonder fouten na deze correctie.
