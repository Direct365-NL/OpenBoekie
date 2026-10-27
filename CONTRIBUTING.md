# Bijdragen

Lees eerst [AGENTS.md](AGENTS.md). Documentatie is Nederlands; code-identifiers en
publieke technische API-namen worden Engels. Gebruik toegankelijke Nederlandse UI-tekst.

## Van idee naar wijziging

1. Maak een use-case of bug met de templates in docs/templates, of later GitHub Issues.
2. Triageren: bepaal scope, prioriteit, risico, eigenaar en afhankelijkheden.
3. Maak het item Ready volgens docs/backlog/README.md en leg goedkeuring vast.
4. Haal main op, maak een korte branch: feat/UC-0001-korte-naam,
   fix/BUG-0001-korte-naam of docs/korte-naam. Claim het item.
5. Implementeer uitsluitend de afgesproken scope, met tests en documentatie.
6. Open een PR via het template; link issue en use-case, voeg lokaal checkbewijs toe.
7. Laat een andere contributor reviewen. Bij één maintainer: aparte vastgelegde
   zelfreview, expliciet als zodanig gemarkeerd; fiscale vrijgave vereist domeinreview.
8. Squash naar main na acceptatie. Zet het item op Done na integratie; noteer
   productie-uitrol apart. Verwijder de featurebranch na samenvoegen.

Gebruik Conventional Commits (feat, fix, docs, refactor, test, chore), met een
beknopte beschrijving en itemreferentie. Geen langlevende OTAP-branches: dezelfde
release gaat door de omgevingen. Geen force-push op gedeelde main of releasetags.

Zie [GitHub-inrichting](docs/engineering/github.md) voor ophalen en filteren van werk.
Er zijn momenteel geen build- of testcommando's; introduceer deze met de toolchain
en werk de README bij voordat de eerste implementatie-PR gereed wordt gemeld.
