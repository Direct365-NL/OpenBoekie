# OpenBookie — Git en GitHub zonder Actions

Repository: [Direct365-NL/OpenBoekie](https://github.com/Direct365-NL/OpenBoekie).
Productnaam: **OpenBookie**. Geregistreerd domein: **openbookie.nl**.
Gebruik de exacte repositoryspelling `OpenBoekie` in Git-URL's.

Op 27 oktober 2026 lokaal gecontroleerd: branch `main`, remote `origin` is
`https://github.com/Direct365-NL/OpenBoekie.git`. De eerste commit is inmiddels
lokaal bevestigd. Volgens de opdrachtgever zijn de labels aangemaakt;
branchbescherming en merge-instellingen zijn nog in uitvoering.
De repository is volgens de opdrachtgever aangemaakt. Zichtbaarheid, abonnement,
rechten, labels en beveiligingsinstellingen zijn niet gecontroleerd. Onderstaande
checklist is uit te voeren werk, geen verklaring dat instellingen al actief zijn.

## 1. Basis en eerste upload

- Controleer in de organisatie `Direct365-NL` dat `Carlovdv` de repository kan
  beheren; geef latere contributors alleen de benodigde rechten.
- Controleer de zichtbaarheid. Volgens [governance](../governance.md) blijft publieke
  publicatie geblokkeerd tot de licentie is meegepubliceerd en het private meldkanaal is geregeld.
- Vul bij **About** als beschrijving in: “OpenBookie — Nederlandse
  SaaS-boekhoudapplicatie; momenteel documentatie en projectstructuur.” Voeg
  `https://openbookie.nl` als website toe zodra daar een bruikbare site staat.
- Controleer vóór de eerste commit alle bestanden en `.gitignore`. Commit de
  beoordeelde documentatie en push `main` naar de bestaande `origin`. Controleer
  eerst of de remote al commits heeft; haal die dan op en verenig de geschiedenis.
  Gebruik geen force-push. Stel daarna `main` als default branch in.
- De bestaande `.github`-templates worden pas op GitHub bruikbaar na upload.
  Ze maken geen labels, branchregels of Projects aan.

## 2. Issues en planning

- Schakel **Settings → General → Features → Issues** in.
- Maak labels: `type:use-case`, `type:bug`; `status:triage`, `status:ready`,
  `status:in-progress`, `status:review`, `status:blocked`, `status:deferred`,
  `status:rejected`, `status:duplicate`; `priority:p0` t/m `priority:p3`.
  Gebruik desgewenst `area:accounting`, `area:security` en `area:platform`.
- Maak de milestones uit [de planning](../backlog/milestones.md): M1 technisch
  fundament, M2 organisaties en toegang, M3 eerste boekhoudkundige keten.
  Neem alleen bevestigde deadlines over.
- Maak bij het overzetten van de backlog per use-case een issue met een link naar
  de specificatie. Koppel het issue terug in het Markdown-bestand. Draft wordt
  `status:triage`, Deferred wordt `status:deferred`; niets wordt automatisch Ready.
- Vanaf die overdracht beheert het issue status, prioriteit en eigenaar volgens
  [de backlogafspraken](../backlog/README.md). Verwijder dan dubbele lokale statusvelden.
- Optioneel: maak een handmatig Project-bord met Draft/Triage, Ready, In progress,
  Review, Blocked en Done en velden voor prioriteit, milestone en eigenaar.
  Een afgerond issue wordt na merge gesloten; verwijder het actieve statuslabel.
  Afgewezen/duplicate issues worden met reden gesloten en behouden hun label.

## 3. Pull requests en bescherming van main

Configureer na de eerste upload een actieve branchregel voor `main` via
**Settings → Branches**, of een gelijkwaardig ruleset via **Settings → Rules**:

- Vereis een pull request en opgeloste reviewgesprekken.
- Sta force-push en verwijderen van `main` niet toe.
- Zolang `Carlovdv` alleen werkt: vereis geen goedkeuring door een andere reviewer.
  Leg een afzonderlijke zelfreview in de PR vast volgens
  [CONTRIBUTING.md](../../CONTRIBUTING.md). Zodra een tweede reviewer beschikbaar is,
  stel minimaal één goedkeuring in en laat verouderde goedkeuringen vervallen bij
  nieuwe wijzigingen. Een auteur kan zijn eigen PR niet goedkeuren.
- Stel geen verplichte statuschecks in: er is nog geen checkprovider of toolchain.
- Pas de regels waar mogelijk ook op beheerders toe; configureer geen algemene
  bypass als vervanging voor het werkbare proces met één maintainer.
- Schakel onder **General → Pull Requests** squash merging en automatisch verwijderen
  van gemergede featurebranches in; schakel andere merge-methoden uit voor het
  afgesproken squashproces.

Beschermde branches zijn beschikbaar voor publieke repositories op Free en voor
private repositories onder passende betaalde plannen. Voor een private repository
van een organisatie is Team of Enterprise nodig. Controleer het organisatieplan;
als afdwingen niet beschikbaar is, leg die beperking vast en volg het PR-proces
handmatig. Maak de repository niet publiek om de licentiegate te omzeilen.
Zie [GitHub: branchbescherming](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches)
en [PR-reviews](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews).

## 4. Security en publicatie

- De licentie is `AGPL-3.0-only`; publiceer de toegevoegde [LICENSE](../../LICENSE)
  en de licentievermelding in de README samen met het project.
- Controleer 2FA en herstelmogelijkheden voor beheerders; stel organisatiebeleid
  pas in nadat bestaande leden hun toegang kunnen behouden.
- Regel een bereikbaar privaat meldkanaal en vul [SECURITY.md](../../SECURITY.md)
  aan. Voor een publieke repository: schakel **Settings → Advanced Security →
  Private vulnerability reporting** in en controleer de meldroute via het
  Security/Advisories-scherm. Deze functie is beschikbaar voor publieke repositories;
  gebruik zolang de repository privé is een afgesproken privaat contactkanaal.
- De genoemde meldroute wordt pas als actief gedocumenteerd na controle.
  Zie [GitHub: private meldingen instellen](https://docs.github.com/en/code-security/how-tos/report-and-fix-vulnerabilities/configure-vulnerability-reporting/configure-for-a-repository).
- Voeg nu geen Actions-workflows, deployment secrets of omgevingen voor uitrol toe.
  Automatische CI/CD en publicatie vereisen een afzonderlijke opdracht en de
  [OTAP-gates](../operations/otap.md).

## 5. Domein

Het bezit van `openbookie.nl` vereist geen GitHub Pages-inrichting. Hosting, DNS,
TLS, eventuele e-mail en auth-redirects worden bij de hosting- en identiteitskeuzes
vastgelegd. Stel nu geen Pages/CNAME, subdomeinen of vermeende securitymailbox in.

## Werk ophalen na inrichting

Filter Issues op `is:issue is:open label:"status:ready"` en `label:"type:use-case"`
of `label:"type:bug"`. Lees de volledige specificatie, afhankelijkheden en reacties.
Met een geïnstalleerde en ingelogde GitHub CLI kan dat ook expliciet per repository:

```sh
gh issue list --repo Direct365-NL/OpenBoekie --state open --label status:ready --label type:use-case
gh issue view <nummer> --repo Direct365-NL/OpenBoekie --comments
```

De assignee claimt het item en wijzigt handmatig het statuslabel. De PR verwijst naar
het issue; gebruik `Closes #nummer` uitsluitend als alle criteria zijn afgerond.
Na merge wordt het item Done; uitrol wordt afzonderlijk geregistreerd.

## Controle na inrichting

Leg datum, uitvoerder, zichtbaarheid, plan en bewijs van actieve instellingen vast.
Controleer de templates met een conceptissue/PR, de regels op `main`, de meldroute
en de koppelingen tussen issues en specificaties. Deze controles zijn nog niet
uitgevoerd; deze documentatieaanpassing configureert GitHub niet.
