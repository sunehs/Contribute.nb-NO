---
title: Definer Git-repositoriet lokalt
description: Denne artikkelen gir veiledning for å opprette ditt lokale Git-repositorium og bidra til dokumentasjon, inkludert prosessen med forgrening og kloning.
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.date: 01/18/2018
ms.openlocfilehash: 2ad0de552d481e2460ca0f56570181e33d0a6608
ms.sourcegitcommit: 92aef5ea8bdd692c5c393d5c8f99b9e4f672ef2b
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238993"
---
# <a name="set-up-git-repository-locally-for-documentation"></a>Sett opp Git-repositorium lokalt for dokumentasjon

Denne artikkelen beskriver fremgangsmåten for å sette opp et git-repositorium på den lokale maskinen din, med formål om å bidra til Microsoft-dokumentasjon. Bidragsytere kan bruke et lokalt klonet repositorium for å legge til nye artikler, foreta større redigeringer i eksisterende artikler eller endre grafikken.

Du kan kjøre disse aktivitetene for engangsoppsett for å bidra til å:
> [!div class="checklist"]
> * Fastslå passende repositorium
> * Forgrene repositoriet til GitHub-kontoen din
> * Velge en lokal mappe for klonede filer
> * Klone repositoriet til den lokale maskinen
> * Konfigurere oppstrøms ekstern verdi

> [!IMPORTANT]
> Hvis du foretar små endringer i en artikkel, trenger du *ikke* å fullføre trinnene i denne artikkelen. Du kan fortsette direkte til [arbeidsflyten for raske endringer](index.md#quick-edits-to-existing-documents).
>

## <a name="overview"></a>Oversikt

For å bidra til webområdet for Microsofts dokumentasjonsområde, og redigere Markdown-filer lokalt ved kloning tilsvarende dokumentasjonsrepositoriet. Microsoft krever at du forgrener det passende repositoriet til githu- kontoen din, slik at du har lese-/skrive-tillatelser der for å lagre de foreslåtte endringene dine. Du kan deretter bruke pull-forespørsler for å slå sammen endringene i et skrivebeskyttet sentralt delt repositorium.

![GitHub Triangle](./media/git-and-github-initial-setup.png)

Hvis GitHub er nytt for deg, kan du se følgende video for en konseptuell oversikt over prosessen med forgrening og kloning:

>[!VIDEO https://channel9.msdn.com/Blogs/CoolMoose/Git-Repository-Setup/player]

## <a name="determine-the-repository"></a>Fastslå repositoriet

Dokumentasjonen plassert på [docs.microsoft.com](https://docs.microsoft.com) ligger i flere forskjellige repositorier på [github.com](https://www.github.com).

1. Hvis du er usikker på hvilket repositorium du skal bruke, går du til artikkelen på docs.microsoft.com ved hjelp av nettleseren din. Velg **Rediger**-koblingen (blyantikon) øverst til høyre i artikkelen.

   ![Klikk Rediger for å fastslå repo og filplassering.](media/index/edit-article.png)

2. Denne koblingen tar deg til github.com-plasseringen for tilsvarende Markdown-fil i riktig repositorium. Noter ned URL-adressen for å vise navnet på repositoriet.

   ![Legg merke til URL-adressen for å finne ut hvor repositoriet er plassert.](media/public-repo.png)

   For eksempel er disse populære repositoriene tilgjengelige for offentlig bidrag:
   - Azure-dokumentasjon [https://github.com/MicrosoftDocs/azure-docs](https://github.com/MicrosoftDocs/azure-docs)
   - Dokumentasjon for SQL-server [https://github.com/MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs)
   - Visual Studio-dokumentasjon [https://github.com/MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs)
   - .NET-dokumentasjon [https://github.com/dotnet/docs](https://github.com/dotnet/docs)
   - Azure .net SDK-dokumentasjon [https://github.com/azure/azure-docs-sdk-dotnet](https://github.com/azure/azure-docs-sdk-dotnet)

## <a name="fork-the-repository"></a>Forgren repositoriet
Bruk riktig repositorium til å opprette en forgrening av repositoriet til GitHub-kontoen ved hjelp av webområdet GitHub.

Det kreves en personlig forgrening siden alle repositorier for hoveddokumentasjon gir lesetilgang, noe som betyr at du ikke kan foreta direkte innholdsendringer i repositoriene. Hvis du vil foreta endringer, må du sende en [pull-forespørsel](git-github-fundamentals.md#pull-requests) fra forgreningen din til hovedrepositoriet. For å forenkle denne prosessen trenger du først din egen kopi av repositoriet, hvor du har skrivetilgang. En GitHub *-forgrening* fungerer til dette.

1. Gå hovedrepositoriets GitHub-side og klikk på **Forgrening** -knappen øverst til høyre.

   ![Eksempel på GitHub-profil](./media/contribute-get-started-setup-local/fork.png)

2. Hvis du blir bedt om det, velger du GitHub-kontoflisen som mål der forgrening skal opprettes. Denne ledeteksten oppretter en kopi av repositoriet i GitHub-kontoen din, kjent som en forgrening.

## <a name="choose-a-local-folder"></a>Velg en lokal mappe
Lag en lokal mappe for å lagre en kopi av repositoriet lokalt. Noen av repositoriene kan være store; opptil 5 GB for azure-dokumenter, for eksempel. Velg en plassering med tilgjengelig diskplass.

1. Velg et mappenavn som er enkelt å huske og skriv inn. Vurder for eksempel en rotmappe `C:\docs\` eller lag en mappe i brukerprofilkatalogen `~/Documents/docs/`

   > [!IMPORTANT]
   > Unngå å velge en lokal mappebane som er nestet i en annen mappeplassering for Git-repositoriet. Selv om det er akseptabelt å lagre Git-klonede mapper ved siden av hverandre, forårsaker nesting av Git-mapper inne i hverandre feil for filsporingen.

2. Start Git Bash

   ![Start Git Bash](./media/contribute-get-started-setup-local/gitbash-start.png)

   Standardplasseringen som Git Bash starter i er vanligvis startkatalogen (~) eller `/c/users/<Windows-user-account>/` på Windows OS.

   For å fastslå gjeldende katalog skriver du inn `pwd` ved ledeteksten $. 

3. Endre mappe (cd) til mappen du opprettet for å være vert lokalt i repositoriet. Merk at Git Bash bruker Linux-konvensjonen til vanlige skråstreker i stedet for omvendte skråstreker for mappebaner.

   For eksempel, `cd /c/docs/ ` eller `cd ~/Documents/docs/`

## <a name="create-a-local-clone"></a>Opprett en lokal klone

Ved hjelp av Git Bash kan du forberede kjøring av **klone**-kommando for å trekke en kopi av et repositorium (forgreningen) til enheten i gjeldende katalog. 

### <a name="authenticate-by-using-git-credential-manager"></a>Godkjenne ved å Git Credential Manager
Hvis du har installert den nyeste versjonen av Git for Windows og godtatt standardinstallasjonen, er Git Credential Manager aktivert som standard. Git Credential Manager gjør godkjenning mye enklere, fordi du ikke trenger å huske ditt personlige tilgangstoken når du gjenoppretter godkjente tilkoblinger og eksterne med GitHub.

1. Kjør **klone**-kommandoen ved å oppgi navnet på repositoriet. Klonenedlastinger (klone) av forgrenet på repositorium på den lokale datamaskinen. 

    > [!Tip]
    > Du kan få forgrenet GitHub URL-adresse for klonekommandoen fra **klone eller nedlastings**-knappen i GitHub-brukergrensesnittet:
    >
    > ![Klon eller last ned](./media/contribute-get-started-setup-local/clone-or-download.png)

    Husk å angi banen til *forgreningen* under kloneprosessen, ikke hovedrepositoriet som du opprettet forgreningen fra. Ellers kan du ikke bidra med endringer. Din forgrening er referert gjennom din personlige GitHub-brukerkonto, slik som `github.com/<github-username>/<repo>`.

    ```bash
    git clone https://github.com/<github-username>/<repo>.git
    ```

    Klonekommandoen bør se ut som dette eksempelet:

    ```bash
    git clone https://github.com/smithj/azure-docs.git
    ```

2. Når du blir bedt om det, må du angi din GitHub-legitimasjon.

    ![GitHub-pålogging](./media/contribute-get-started-setup-local/github-login.png)

3. Når du blir bedt om det, kan du angi koden for to-faktor-godkjenning.

    ![GitHub to-faktor-godkjenning](./media/contribute-get-started-setup-local/github-2fa.png)

    > [!Note]
    > Legitimasjonen lagres og brukes til å godkjenne fremtidige GitHub-forespørsler. Du trenger bare å gjøre denne godkjenningen én gang per datamaskin. 

4. Klone-kommandoen kjøres, og laster ned en kopi av repositoriumfilene fra din forgrening til en ny mappe på den lokale disken. En ny mappe lagres i den nåværende mappen. Det kan ta noen minutter, avhengig av størrelsen på repositoriet. Du kan utforske mappen for å se strukturen når den er ferdig.

## <a name="configure-remote-upstream"></a>Konfigurer ekstern oppstrøms
Etter kloning av repositoriet, konfigurerer du en skrivebeskyttet tilkobling til hovedrepositoriet kalt **oppstrøms**. Du bruker oppstrøms URL-adressen til å synkronisere det lokale repositoriet med de siste endringene som er foretatt av andre. Kommando **git ekstern** brukes til å angi konfigurasjonsverdien. Du bruker **hent**-kommandoen for å oppdatere greninfo fra oppstrøms-repositoriet.

1. Hvis du bruker **Git Credential Manager**, bruker du følgende kommandoer. Erstatt \<repo-\> og \<organisasjons\>-plassholdere.
   ```bash
   cd <repo>
   git remote add upstream https://github.com/<organization>/<repo>.git
   git fetch upstream
   ```

2. Vis konfigurerte verdier og bekreft at nettadresser er korrekte. Kontroller at **opprinnelige** URL-adresser peker mot din personlige forgrening. Forsikre deg om at **oppstrøms** URL-adresser peker mot hovedrepositoriet, som MicrosoftDocs eller Azure. 
   ```bash
   git remote -v 
   ```

   Eksempel på eksterne utdata vises. En fiktiv Git-konto med navnet MyGitAccount er konfigurert med et personlig tilgangstoken for å få tilgang til repo azure-dokumenter:
   ```output
   origin  https://github.com/MyGitAccount/azure-docs.git (fetch)
   origin  https://github.com/MyGitAccount/azure-docs.git(push)
   upstream        https://github.com/MicrosoftDocs/azure-docs.git (fetch)
   upstream        https://github.com/MicrosoftDocs/azure-docs.git (push)
   ```

3. Hvis du har gjort en feil, kan du fjerne den eksterne verdien. Hvis du vil fjerne oppstrømsverdien, kan du kjøre kommandoen `git remote remove upstream`.

## <a name="next-steps"></a>Neste trinn
- Hvis du vil vite mer om å legge til og oppdatere innhold, går du videre til [GitHub-bidragsarbeidsflyt](how-to-write-workflows-major.md).