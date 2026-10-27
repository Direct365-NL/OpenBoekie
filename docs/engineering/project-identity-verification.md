# Documentatiecontrole — projectidentiteit OpenBookie

- Datum: 27 oktober 2026. Uitvoerder: Codex in opdracht van Carlovdv.
- Omgeving: lokale macOS-werkmap, zsh, Python 3; geen applicatieruntime gebruikt.
- Branch: `main`. Commit: ontbreekt; `git rev-parse --verify HEAD` geeft
  `fatal: Needed a single revision`. Bewijs geldt voor de lokale werkbestanden.
- Scope: README, productvisie, governance, milestoneverwijzing, changelog,
  securitybeleid en GitHub-handleiding. Geen applicatie- of GitHub-wijzigingen.
- `git remote -v`: fetch en push verwijzen naar
  `https://github.com/Direct365-NL/OpenBoekie.git`.
- `git branch --show-current`: `main`.
- `git status --short`: de projectbestanden zijn nog untracked; er bestaat geen
  commitdiff om deze aanpassing te isoleren van de eerdere documentatie.
- Linkcontrole: onderstaande opdracht controleert lokale Markdown-bestandsdoelen
  in de repository; URL's en ankers worden afzonderlijk beoordeeld.

```sh
python3 - <<'PY'
from pathlib import Path
import re
errors = []
count = 0
for p in Path('.').rglob('*.md'):
    if '.git' in p.parts:
        continue
    for target in re.findall(r'\]\(([^)]+)\)', p.read_text()):
        if '://' in target or target.startswith('#'):
            continue
        target = target.split('#')[0]
        if not target:
            continue
        count += 1
        if not (p.parent / target).exists():
            errors.append(f'{p}: {target}')
print(f'{count} lokale bestandslinks; {len(errors)} ontbrekende doelen')
print('\n'.join(errors))
raise SystemExit(bool(errors))
PY
```

- Resultaat linkcontrole: 98 lokale bestandslinks, 0 ontbrekende doelen.
- `rg -n 'werknaam|remote zijn nog niet|nog geen remote|naam/remote|# Boekhouding' README.md docs`:
  geen verouderde vermeldingen gevonden vóór toevoeging van dit commandoverslag.
- `git diff --check`: geen uitvoer; dit controleert de untracked bestanden niet
  en geldt daarom niet als volledige whitespacecontrole van deze wijziging.
- Handmatige consistentiecontrole: OpenBookie is de productnaam, openbookie.nl
  het opgegeven domein, OpenBoekie de exacte repositorynaam. Geen veronderstelde
  hosting, actieve GitHub-beveiliging of Ready-goedkeuring toegevoegd.
- Het nieuwe anker `github.md#4-security-en-publicatie` past bij de sectietitel.
- GitHub-instructies getoetst aan de officiële bronnen gelinkt in de handleiding.
  De repositorypagina kon via de webtool niet worden opgehaald; dit bewijst niets
  over zichtbaarheid of bestaan. Remote-instellingen zijn niet geïnspecteerd.
- Geen applicatietests/build uitgevoerd: toolchain en implementatie ontbreken.
- Resterend: maintainerreview, eerste commit/upload en uitvoering van de GitHub-
  checklist. Dit is geen onafhankelijke review of acceptatie van UC-0013.
