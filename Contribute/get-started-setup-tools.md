---
title: Installer innholdsredigeringsverktøy
description: Denne artikkelen hjelper deg å laste ned og installere klientverktøyene du trenger for Git og redigering av markdown-filer.
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.date: 04/30/2018
ms.prod: non-product-specific
ms.topic: contributor-guide
ms.custom: external-contributor-guide
ms.openlocfilehash: 1011c3fc829202a3df134ddc80eb05b8959b7bf6
ms.sourcegitcommit: 782b689882cce3ce07f5613763322989f2d0d63f
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/05/2018
ms.locfileid: "34469375"
---
# <a name="install-content-authoring-tools"></a>Installer innholdsredigeringsverktøy

Denne artikkelen beskriver fremgangsmåten for interaktiv installering av Git-klientverktøy og kode for Visual Studio.
> [!div class="checklist"]
> * Installer [Git for Windows](https://git-scm.com/download/win)
> * Installer [Visual Studio Code](https://code.visualstudio.com/)
> * Installer [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)

>[!IMPORTANT]
> Hvis du bare gjør små endringer i en artikkel, er det *ikke nødvendig* å fullføre trinnene i denne artikkelen, og du kan fortsette direkte til [arbeidsflyten for raske endringer](index.md#quick-edits-to-existing-documents).
>
> Viktige bidragsytere oppfordres til å fullføre disse trinnene, som gjør det mulig å bruke [arbeidsflyten for store/tidkrevende endringer](how-to-write-workflows-major.md). Selv om du har skrivetillatelser i hovedrepositoriet, *anbefaler vi på det sterkeste (og denne veiledningen forutsetter) at du forgrener og kloner repositoriet*, slik at du har lese/skrivetillatelser til å lagre de foreslåtte endringene i din forgrening.

## <a name="install-git-client-tools-on-windows"></a>Installer Git-klientverktøy på Windows

 Installer den nyeste versjonen av [Software Freedom Conservancys Git-klientverktøy](https://git-scm.com/download/). Installereringen inkluderer Git-versjonens kontrollsystem og Git Bash, kommandolinjeappen som du bruker for interaksjon med ditt lokale Git-repositorium.

Hvis du foretrekker et grafisk brukergrensesnitt (GUI) fremfor et kommandolinjegrensesnitt (CLI), kan du se [Software Freedom Conservancys tilgjengelige GUI-klientside](https://git-scm.com/downloads/guis), [GitHubs GitHub Desktop](https://desktop.github.com/), eller [ Visual Studio Code](https://www.visualstudio.com/products/code-vs.aspx) for noen populære alternativer.

Følg instruksjonene for den valgte klienten for installasjon og konfigurasjon.

I neste artikkel vil du [sette opp et lokalt Git-repositorium](get-started-setup-local.md).

   Flere Git-ressurser er tilgjengelig her: [Git-terminologi](https://help.github.com/articles/github-glossary) | [Grunnleggende om Git](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics) | [Lære Git og GitHub](https://help.github.com/articles/good-resources-for-learning-git-and-github/)

## <a name="understand-markdown-editors"></a>Forstå Markdown-redigeringsprogrammer

Markdown er et lett markeringsspråk som er både lett å lese og lett å lære. Derfor har det raskt blitt en bransjestandard. Hvis du vil skrive artikler i Markdown, anbefaler vi at du først laster ned og installerer et Markdown-redigeringsprogram.  [Visual Studio Code](https://code.visualstudio.com/) er det foretrukne verktøyet for redigering av Markdown hos Microsoft. [Atom](https://atom.io) er et annet populært verktøy for redigering av Markdown.

Markdown-tekst lagres i filer med .md-utvidelse.

Flere detaljer om hvordan de skriver med Markdown, inkludert grunnleggende om Markdown og funksjoner støttet av OPS-egendefinerte Markdown-utvidelser, dekkes i artikkelen [Slik bruker du Markdown](how-to-write-use-markdown.md).

## <a name="visual-studio-code"></a>Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/), også kjent som VS Code, er et lett redigeringsprogram som fungerer på Windows, Linux på Mac. Det inkluderer git-integrasjon og støtte for utvidelser.

Last ned og installer [VS Code](https://code.visualstudio.com/). VS Codes hjemmeside skal finne operativsystemet på riktig måte.

- [Windows](https://code.visualstudio.com/docs/setup/windows)
- [Mac](https://code.visualstudio.com/docs/setup/mac)
- [Linux](https://code.visualstudio.com/docs/setup/linux)

> [!TIP]
> Hvis du vil starte VS Code og åpne den gjeldende mappen, kan du kjøre kommandoen `code .` i kommandolinjen eller bash shell. Hvis gjeldende mappe er en del av en lokal git-repo, vises github-integrasjon i Visual Studio Code automatisk.

## <a name="docs-authoring-pack"></a>Docs Authoring Pack
Installer Docs Authoring Pack for Visual Studio Code. Dette utvidelsessettet inneholder grunnleggende opprettingsassistanse som kan hjelpe når du skriver Markdown, og en forhåndsvisning, slik at du kan se hvordan Markdown ser ut med stilen som brukes på nettstedet docs.microsoft.com.

   Gå til [Markedsplass-siden](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) og velg **Installer**, eller bruk VS Code-vinduet til å søke i tilleggslisten etter `docsmsft.docs-authoring-pack`. 

   Hvis du trenger Docs Authoring Pack, finner du den ved å trykke på ALT+M i VS Code. Verktøylinjen er skjult som standard, men kan vises ved behov. Rediger VS Code-innstillingene (CTRL+KOMMA) og legg til `"markdown.showToolbar": true` for å vise verktøylinjen.

   Hvis du vil ha mer informasjon, kan du se siden [Docs Authoring Pack](how-to-write-docs-auth-pack.md).


## <a name="next-steps"></a>Neste trinn

Nå er du klar til å [Sette opp et lokalt Git-repositorium](get-started-setup-local.md).