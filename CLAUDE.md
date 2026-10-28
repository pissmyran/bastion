# CLAUDE.md – bastion

@AGENTS.md

Vägledning för Claude Code i `pissmyran/bastion`: en SSH-klient byggd främst för iOS och distribuerad via TestFlight, med delad kärna (`SSHCore`) och appar även för macOS, tvOS, Linux (Rust), Windows (.NET) och Android.

De gemensamma reglerna för alla repon finns i [STYRNING.md](https://github.com/pissmyran/.github/blob/main/STYRNING.md) i `pissmyran/.github`. Kärnreglerna nedan är en ordagrann kopia. Jämför versionen i markeringen med källan i början av varje session (`curl -sS https://raw.githubusercontent.com/pissmyran/.github/main/STYRNING.md`); är kopian äldre, uppdatera den först i en egen PR (`docs: sync core rules from .github`).

## Kärnregler

<!-- kärnregler:start version=2026-10-28 källa=https://github.com/pissmyran/.github/blob/main/STYRNING.md -->
1. **Inga personliga värden.** Repot är publikt. Skriv aldrig in riktiga id:n, domäner, e-postadresser, namn, nycklar, betallänkar eller kontouppgifter i kod, konfiguration, tester, dokumentation eller commit-meddelanden. Använd platshållare och `example.com`-värden.
2. **Inga hemligheter.** Tokens, lösenord, sessioner och nycklar hamnar aldrig i Git, loggar, issues eller publik dokumentation. Hemligheter läggs in utanför repot (Cloudflare, GitHub-miljöer, `wrangler secret put`).
3. **Gren och pull request.** Varje session börjar från senaste `main` (`git fetch origin main`) på en egen gren. `main` ändras bara genom en PR som squash-mergas. Ingen pushar direkt till `main`. En sessions arbete hålls i en PR.
4. **Testa lokalt före varje push.** Det finns inga testkontroller i CI. Repots egna tester och kontroller (avsnittet Kommandon i repots `CLAUDE.md`) är den enda testgrinden. Pusha aldrig med fallerande tester, och skriv tester för det du ändrar.
5. **Rör aldrig workflows.** `.github/workflows/`, `.github/actions/` och `CODEOWNERS` ändras inte av Claude, inte ens för att laga ett fel. Ingen kontroll stoppar det längre, men regeln gäller fullt ut. Behövs en ändring: beskriv den i ett issue och låt ägaren göra den. Bara Renovate och Dependabot får uppdatera dem.
6. **Granskning.** CodeRabbit, Sourcery och Codex granskar, och CodeQL (GitHubs standardinställning) skannar. Varje granskningstråd måste lösas innan merge. Svara i tråden med vad du ändrade, eller med skälet om fyndet är brus.
7. **Auto-merge sist.** Slå på auto-merge först när granskningsbotarna har granskat den senaste commiten (CodeRabbit hoppar över `docs/` och `*.md`; för sådana ändringar räcker Sourcery och Codex), alla trådar är lösta och alla kontroller som körs på PR:en är gröna, även de som reglerna inte kräver (till exempel `Dokumentation`).
8. **Laga orsaken, inte symptomet.** När något fallerar eller en granskning kräver ändring: läs allt, hitta orsaken och gör om den delen rätt. Små uppenbara fel får rättas direkt. Försvaga aldrig ett test, hoppa aldrig över en kontroll och tysta aldrig en varning.
9. **Säkerhet först.** Säkerhetslarm (CodeQL, Dependabot, Renovate) går före annat arbete. Länka issuet med `Closes #n`.
10. **Senaste versionerna.** Lägg aldrig till nya låsningar till ett versionsnummer; använd `@latest`, `node`, `latest` och versionsintervall. Befintliga låsningar som Renovate håller aktuella (till exempel `packageManager`, `requirements-docs.txt`, `.node-version`, lockfiler och actions låsta med commit-SHA) behålls och ändras bara av Renovate.
11. **Commits och titlar.** Sessionen signerar commits själv. Ändra aldrig gits användare, e-post eller signering, och använd aldrig `--no-verify`. PR-titeln blir commiten på `main` och skrivs på engelska enligt Conventional Commits: `typ: beskrivning` eller `typ(område): beskrivning`, med typ feat, fix, docs, refactor, perf, test, build, ci, chore, style eller revert.
12. **Dokumentation i samma PR.** Ändras beteende, inställningar eller kommandon uppdateras `README.md`, `docs/` och repots `CLAUDE.md` i samma PR.
13. **Inga lösa grenar.** Radera grenen när PR:en är mergad eller stängd. PR:er från forkar är förslag: gör ändringen själv på en egen gren om den är önskad, och stäng originalet med tack och länk.
14. **Noll kronor.** Slå aldrig på något som kan kosta pengar.
15. **GitHub bara via REST.** `gh pr` och `gh issue` fungerar inte i molnsessioner (GraphQL är avstängt). Använd `gh api` och de särskilda `ccr`-vägarna; se avsnittet GitHub från sessionen.
<!-- kärnregler:slut -->

## Kommandon

iOS, macOS och tvOS kan inte byggas på Linux. Bygg och testa det som går här, för de delar du har ändrat:

```bash
swift build && swift test
```

```bash
cd LinuxApp && cargo test
```

```bash
dotnet test WindowsApp/Bastion.Core.Tests
```

Windows-appen själv (`WindowsApp/WindowsApp.csproj`, WinUI) kan bara byggas på Windows och testas alltså inte av kommandot ovan.

```bash
cd Android && ./gradlew build
```

Saknas en verktygskedja i sessionen, installera den senaste versionen. Det finns inga byggkontroller i CI just nu, så Apple-apparna verifieras inte automatiskt; skriv i PR:en vilka plattformar du har testat och vilka som inte gick att testa, särskilt Apple- och Windows-apparna.

## Regler för det här repot

- **Ingen signering i repot:** lägg aldrig till kodsignering, certifikat, provisioneringsprofiler eller App Store-nycklar.
- **Gränser:** bevara gränsen mellan den delade `SSHCore` och de plattformsspecifika apparna. Detaljerna står i `AGENTS.md` och `docs/`.
- **Commit-titlarna styr releasen:** `feat` ger minor, `fix`, `perf` och `revert` ger patch och `!` eller `BREAKING CHANGE` ger major. Välj typ med omsorg.

## Kända avvikelser

Läget 2026-10-28. Laga inget av detta på egen hand; det gäller workflows eller inställningar som ägaren äger.

- **Release fallerar** på varje push till `main`: `release.yml` väntar på kontrollerna i `.github/release-required-checks` (Rust, .NET, Android, Swift och Apple), som inte längre körs.
- **`repo_url`** i `zensical.toml` pekar på ett gammalt repo i stället för `pissmyran/bastion`. Rätta det i en egen PR om det ingår i uppgiften.
- **`site_url`** i `zensical.toml` är en egen domän, medan repots hemsida på GitHub är `pissmyran.github.io/bastion`. Ändra inte `site_url` utan ägarens beslut.

## Granskning i det här repot

- **Grind:** `main` kräver PR, linjär historik, lösta granskningstrådar och CodeQL utan fel eller allvarliga larm. Inga andra kontroller krävs, men de som körs ska vara gröna. De lokala testerna i Kommandon är testgrinden.
- **CodeRabbit:** ärver den centrala konfigurationen i `pissmyran/coderabbit`. Repots `.coderabbit.yaml` pekar ut riskområden med egna granskningsinstruktioner; läs den del som gäller filerna du ändrar innan du börjar.
- **Sourcery och Codex:** granskar också, som GitHub-appar utan egen konfiguration här, och de granskar även dokumentation. Behandla deras trådar som CodeRabbits.
- **Extra noggrant:** nyckelhantering, kryptering, synk, värdnycklar och plattformsgränser.

## GitHub från sessionen

GraphQL är avstängt, så `gh pr` och `gh issue` fungerar inte. Använd REST:

- Öppna PR: `gh api repos/pissmyran/bastion/pulls -f base=main -f head=<gren> -f title='…' -f body='…'`
- PR från gren: `gh api 'repos/pissmyran/bastion/pulls?head=pissmyran:<gren>&state=open'`
- Issue: `gh api repos/pissmyran/bastion/issues/<n>` och `…/issues/<n>/comments`
- Granskningstrådar: `gh api repos/pissmyran/bastion/pulls/<n>/ccr/review_threads`
- Svara i tråd: `gh api repos/pissmyran/bastion/pulls/<n>/comments/<id>/replies -f body='…'`
- Lös tråd: `gh api -X POST repos/pissmyran/bastion/pulls/<n>/ccr/comments/<id>/resolve`
- Kontroller: `gh api repos/pissmyran/bastion/commits/<sha>/check-runs`
- Auto-merge på: `gh api -X PUT repos/pissmyran/bastion/pulls/<n>/ccr/auto_merge -f merge_method=squash`
- Är PR:en redan klar att mergas (auto-merge vägras då), squash-merga direkt: `gh api -X PUT repos/pissmyran/bastion/pulls/<n>/merge -f merge_method=squash`
- Stäng PR: `gh api -X PATCH repos/pissmyran/bastion/pulls/<n> -f state=closed`
- Radera gren: GitHub raderar grenen vid merge. En stängd PR:s gren raderas med `git push origin --delete <gren>` (API-vägen är spärrad).
