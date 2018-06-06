---
title: Docs Authoring Pack for VS Code
description: Denne artikkelen beskriver VS Code-utvidelsespakke for å forenkle Markdown-oppretting for docs.microsoft.com.
author: meganbradley
ms.author: mbradley
manager: jemash
ms.date: 04/06/2018
ms.prod: non-product-specific
ms.topic: contributor-guide
ms.custom: external-contributor-guide
ms.openlocfilehash: d0d61db2faf88598ecd2c800fb5fbe8df8ec44f5
ms.sourcegitcommit: 782b689882cce3ce07f5613763322989f2d0d63f
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/05/2018
ms.locfileid: "34469582"
---
# <a name="docs-authoring-pack-for-vs-code"></a>Docs Authoring Pack for VS Code

Docs Authoring Pack er en samling av VS Code-utvidelser for hjelp med Markdown-oppretting for docs.microsoft.com. Pakken er [tilgjengelig på VS Code-markedsplassen](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) og inneholder følgende utvidelser:

- **DocFx:** gir en forhåndsvisning av docs.microsoft.com-spesifikk Markdown. Hvis du vil ha mer informasjon, se [DocFx](https://marketplace.visualstudio.com/items?itemName=ms-docfx.DocFX).
- **markdownlint:** En populær Markdown-linter av David Anson for å sikre at din Markdown følger anbefalt fremgangsmåte. Hvis du vil ha mer informasjon, se [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint).
- **Docs Markdown:** Gir Markdown-opprettingshjelp for docs.microsoft.com-innhold i det åpne publiseringssystemet (OPS), inkludert grunnleggende støtte for Markdown og støtte for egendefinert Markdown-syntaks i OPS. Resten av dette emnet beskriver Docs Markdown-utvidelsen.

## <a name="prerequisites-and-assumptions"></a>Forutsetninger og antakelser

Hvis du vil sette inn nøyaktig relative koblinger, bilder og annet innebygd innhold med Docs Markdown-utvidelsen, må du ha VS Code-arbeidsområdet begrenset til roten av din klonede OPS-repo.

Enkelte typer syntaks som støttes av utvidelsen, for eksempel varsler og snutter, er egendefinert Markdown for OPS, og vil ikke gjengis riktig hvis det ikke publiseres via OPS.

## <a name="how-to-use-the-docs-markdown-extension"></a>Slik bruker du Docs Markdown-utvidelsen

Hvis du vil ha tilgang til Docs Markdown-menyen, skriver du inn `ALT+M`. Du kan klikke eller bruke opp/ned-pilene for å velge den ønskede funksjonen, eller skrive inn for å starte filtreringen og trykke `ENTER` når funksjonen du vil bruke utheves på menyen. Følgende er tilgjengelig:

|Funksjon     |Kommando             |Beskrivelse           |
|-------------|--------------------|----------------------|
|Fet         |`formatBold`        |Formaterer teksten **fet**.|
|Kursiv       |`formatItalic`      |Formaterer teksten *kursiv*.|
|Kode         |`formatCode`        |Hvis en linje eller mindre er valgt, formaterer du tekst som `inline code`.<br><br>Hvis det er merket av for flere linjer, formaterer du dem som en inngjerdet kodeblokk, og du kan også velge et programmeringsspråk som støttes av OPS.|
|Varsel        |`insertAlert`       |Setter inn et notat, viktig, advarsel eller tips.<br><br>Velg varselet fra menyen, og velg deretter varseltype. Hvis du tidligere har valgt tekst, blir den omgitt av valgt varselsyntaks. Hvis ingen tekst velges, legges det til et nytt varsel med plassholdertekst.|
|Nummerert liste|`insertNumberedList` |Setter inn en ny nummerert liste.<br><br> Hvis det er merket av for flere linjer, blir hver av dem et listeelement. Vær oppmerksom på at nummererte lister vises Markdown som 1-ere, men vil gjengis på docs.microsoft.com som fortløpende tall eller, for nestede lister, bokstaver. For å opprette en nestet nummerert liste tar du fra kategorien i den overordnede listen.|
|Punktmerket liste|`insertBulletedList` |Setter inn en ny punktmerket liste.|
|Tabell        |`insertTable`        |Setter inn en tabellstruktur for Markdown.<br><br>Når du velger tabellkommandoen, kan du angi hvor mange kolonner og rader i formatkolonner:rader, som 3:4. Legg merke til at det maksimale antallet kolonner som du kan angi via denne utvidelsen er 5, som er anbefalt maksimum for lesbarhet.|
|Kobling         |`selectLinkType`      |Setter inn en kobling. Når du velger denne kommandoen, vises følgende undermeny.<br><br>`External`: Koble til en web-side ved hjelp av URI. Må inkludere «http» eller «https».<br>`Internal`: Sett inn en relativ kobling til en annen fil i samme repo. Når du har valgt dette alternativet, skriver du inn kommandovinduet for å filtrere filene etter navn, og velger deretter filen du vil bruke. <br>`Bookmark in this file`: Velge fra en liste over overskrifter i gjeldende fil å sette inn et bokmerke som er riktig formatert.<br>`Bookmark in another file`: Filtrer først etter filnavn og velg filen du vil koble til, og velg deretter en overskrift i den valgte filen.|
|Bilde        |`insertImage`     |Skriv inn alternativ tekst (kreves for tilgjengelighet) og velg den, og deretter kaller du denne kommandoen til å filtrere listen over støttede bildefiler i repo og velger den du vil bruke. Hvis du ikke har valgt alt-tekst når du kaller denne kommandoen, vil du bli bedt om det før du kan velge en bildefil.|
|Inkludering      |`insertInclude`   |Finn en fil for å bygge inn i gjeldende fil.|
|Kodesnutt      |`insertSnippet`   |Finn en kodesnutt i repo for å bygge inn i gjeldende fil.|
|Video        |`insertVideo`     |Legg til en innebygd video.|
|Forhåndsvisning      |`previewTopic`    |Forhåndsvise det aktive emnet i et side-ved-side-vindu med DocFX-utvidelsen.  Hvis DocFX-utvidelsen ikke er installert eller er installert men deaktivert, vil ikke emnet gjengis emnet.


## <a name="how-to-assign-keyboard-shortcuts"></a>Slik tilordner du hurtigtaster

1. Skriv `CTRL+K` og deretter `CTRL+S` for å åpne listen over hurtigtaster.
1. Søk etter kommandoen, som `formatBold`, hvis du vil opprette en egendefinert hurtigtast.
1. Klikk på plusstegnet som vises i nærheten av kommandonavnet når du har musen over linjen.
1. Når en ny inndataboks er synlig, skriver du inn tastatursnarveien du vil binde til den aktuelle kommandoen. Hvis du vil bruke kommandosnarveien for fet skrift, skriv `ctrl+b`.
1. Det er en god idé å sette inn en `when` setning i hurtigtasten din, slik at den ikke vil være tilgjengelig i andre filer enn Markdown. Hvis du vil gjøre dette, åpner du *keybindings.json* og setter inn følgende linje under kommandonavnet (sørg for å legge til et komma mellom linjene):
   
    `"when": "editorTextFocus && editorLangId == 'markdown'"`

    Den fullførte egendefinerte hurtigtasten skal se slik ut i keybindings.json:

    ```json
    // Place your key bindings in this file to overwrite the defaults
    [
        {
            "key": "ctrl+b",
            "command": "formatBold",
            "when": "editorTextFocus && editorLangId == 'markdown'"
        }
    ]
    ```

1. Lagre keybindings.json.

Se [Hurtigtaster](https://code.visualstudio.com/docs/getstarted/keybindings) i VS Code-dokumenter for mer informasjon.

## <a name="how-to-show-the-legacy-gauntlet-toolbar"></a>Slik viser du verktøylinjen for eldre «Gauntlet»

Tidligere brukere av utvidelseskoden med navnet «Gauntlet» vil legge merke til at redigeringsverktøylinjen ikke lenger vises nederst i VS Code-vinduet når dokumenter Docs Markdown-utvidelsen er installert. Dette er fordi verktøylinjen tok opp mye plass på VS Code-statuslinjen og ikke fulgte anbefalt fremgangsmåte for UX-utvidelsen, så den er avverget i den nye utvidelsen. Du kan imidlertid vise verktøylinjen ved å oppdatere VS Code settings.json-filen som følger:

1. I VS Code går du til Fil -> Preferanser -> Innstillinger (`CTRL+Comma`).
1. Velg Brukerinnstillinger for å endre innstillingene for alle VS Code-arbeidsområder eller Arbeidsplassinnstillinger for å endre dem bare for gjeldende arbeidsområde.
1. I Standardinnstillinger-ruten finner du Docs Authoring-utvidelseskonfigurasjon og velger blyantikonet ved siden av ønsket innstilling. Deretter blir du bedt om å velge enten `true` eller `false`. Når du har foretatt valget, legger VS Code automatisk til verdien til settings.json-filen, og du blir bedt om å laste inn på nytt i vinduet for at endringene skal tre i kraft.

## <a name="known-issues"></a>Kjente problemer

- DocFX-forhåndsvisning: På MacOS og Linux starter ikke DocFX-forhåndsvisning på riktig måte (standarden for forhåndsvisning er VS Code Markdown-forhåndsvisning på disse plattformene).
- DocFx-forhåndsvisning: På alle plattformer kan noen syntakser, for eksempel XREF-koblinger (kryssreferanse) til API-er, ikke gjengis riktig i forhåndsvisning. I noen tilfeller fører dette til manglende innhold.
- Eksterne bokmerker: På Linux vises fillisten, men ikke overskrifter som kan velges.
- Inkluderer: På Linux vises fillisten, men det blir ikke lagt til noen kobling etter at valget er gjort.
