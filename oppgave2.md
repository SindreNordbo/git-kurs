# Oppgave 2

Denne oppgaven tar utgangspunkt i et eksempel-repo. Fork repoet før du begynner: https://github.com/sindrebn/eksempelrepo-1

### 1. Opprette pull request

Opprett en pull request fra branchen `feature1` til `master`. Du vil se på pull requesten at branchen har konflikter med `master`. Disse må løses før du kan merge.

### 2. Løse konflikter med merge
Løs konfliktene ved å merge `master` inn i `feature1` lokalt på egen maskin. Push endringene når du er ferdig. Til slutt merger du pull requesten på GitHub.

💡 Konflikter oppstår når en fil har endret seg både i din branch og branchen du merger inn. For å gjennomføre mergen, åpne filen(e) som har en konflikt, endre filen til å være slik du ønsker den skal være og marker konflikten som løst med `git add <fil>`. Når du har gjort det for alle filene som har konflikt, gjennomfør selve mergen med `git commit`.

### 3. Løse konflikter med [rebase](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
Opprett en ny pull request, denne gangen fra `feature2` til `master`. Denne branchen har også konflikter som må løses før merging.

Løs konfliktene ved å rebase `feature2` på `master`. Dette gjør du på følgende vis:

```
> git checkout feature2
> git rebase master
Løs konfliktene etterhvert som de oppstår
> git push --force
```

Legg merke til at vi må gjøre en såkalt _«force push»_ for å kunne pushe den rebasede branchen vår for å indikere at du er klar over at du skriver over endringer remote.

⚠️ Når du _force pusher_ kan du skape trøbbel for andre som har klonet repoet. Tenk deg nøye om og spør en venn før du _force pusher_ til et repo flere jobber på.

💡 I motsetning til ved en merge hvor du får alle konfliktene på én gang, vil du nå løse konfliktene commit for commit. Løs konflikter som i sted, men gjør `git rebase --continue` for å spole deg fremover i historikken. Du kan når som helst gjøre `git rebase --abort` hvis du gjør feil og vil begynne på nytt.

Merge pull requesten fra GitHub.

## Bonusoppgave

Installer [`hub`](https://github.com/github/hub), og bruk verktøyet for å opprette en pull request.
