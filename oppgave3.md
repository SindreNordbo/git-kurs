# Oppgave 3 – interaktiv rebase

Denne oppgaven tar utgangspunkt i et eksempel-repo. Fork repoet før du begynner: https://github.com/sindrebn/eksempelrepo-2

Som du ser er historikken i repoet litt rotete. Vi skal forsøke å rydde i historikken ved hjelp av `git rebase --interactive`.

Ta først en titt på historikken (`git log` + `git show <commit-hash>` eller bruk GitHub) for å identifisere ting som bør ryddes opp i. Kjør deretter `git rebase --interactive cd85e123f740d06711c6b515c37e6bb5a9781fad` for å starte en rebase på commitene mellom `HEAD` (tuppen av branchen du har sjekket ut) og `cd85e123f740d06711c6b515c37e6bb5a9781fad` (den første commiten i repoet).

💡 Du kan også bruke `git rebase --interactive HEAD~5`. `HEAD~5` betyr `HEAD` sin 5. forelder, altså _`HEAD` minus 5 commits_.

Når du kjører denne kommandoen får du en liste med commits, i tillegg til én kommando per commit. Ved å bytte ut kommandoen som står foran hver commit kan du endre historikken. Se på denne listen som et lite script som utføres linje for linje fra toppen.

💡 I motsetning til når du kjører `git log` er commitene sortert fra nyest til eldst i denne visningen.

De ulike kommandoene du kan velge mellom er:

- `pick` behold commiten som den er
- `reword` lar deg endre commit-melding
- `edit` behold commiten som den er, men rebasen vil pause etter denne commiten for at du kan legge til eller fjerne endringer (`amend`)
- `squash` slå sammen med forrige commit
- `fixup` slå sammen med forrige commit, men ikke slå sammen commit-meldingene
- `drop` slett commit

💡 Ved å endre rekkefølge på linjene vil også commitene bytte rekkefølge.

I tillegg kan du legge inn linjer med `exec <shell-kommando som skal kjøres>`. Dette kan være nyttig hvis du vil kjøre en kommando som en del av rebasen din, for eksempel kan du kjøre testene etter hver commit hvis du plutselig har fått en feilende test og du vil finne ut hvilken commit som introduserte feilen.

Når du er fornøyd med hvordan «scriptet» ditt ser ut lagrer du (`:wq` i vim), og alle kommandoene blir utført i sekvens.

💡 Det er veldig lett å trå feil når man rebaser. Så lenge du er midt i en rebase kan du kjøre `git rebase --abort` for å avbryte prosessen og ev. starte på nytt.

Når du endrer historikken må du bruke `--force`-flagget til `git push` for å indikere at du er klar over at du skriver over endringer remote.

⚠️ Når du _force pusher_ kan du skape trøbbel for andre som har klonet repoet. Tenk deg nøye om og spør en venn før du _force pusher_ til et repo flere jobber på.
