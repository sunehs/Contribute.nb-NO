---
title: Docs Authoring Pack for VS Code
description: Denne artikkelen beskriver VS Code-utvidelsespakke for å forenkle Markdown-oppretting for docs.microsoft.com.
author: meganbradley
ms.author: mbradley
manager: jemash
ms.date: 04/06/2018
ms.openlocfilehash: b9fedce0a73c5c4212ffd0893c745fab56677c8c
ms.sourcegitcommit: 5e508a7ad2991632a38f302e4769b36e3bf37eb2
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 08/30/2018
ms.locfileid: "43308920"
---
# <a name="docs-authoring-pack-for-vs-code"></a>Docs Authoring Pack for VS Code

Docs Authoring Pack er en samling av VS Code-utvidelser for hjelp med Markdown-oppretting for docs.microsoft.com. Pakken er [tilgjengelig på VS Code-markedsplassen](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) og inneholder følgende utvidelser:

- [markdownlint:](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) En populær Markdown-linter av David Anson for å sikre at din Markdown følger anbefalt fremgangsmåte.
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker): En fullstendig frakoblet stavekontroll fra Street Side Software.
- [Docs Preview](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-preview): Bruker docs.microsoft.com CSS for mer nøyaktig Markdown-forhåndsvisning, inkludert egendefinert Markdown.
- [Docs Markdown](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-markdown): Gir Markdown redigeringshjelp for docs.microsoft.com-innhold i det åpne publiseringssystemet (OPS), inkludert grunnleggende støtte for Markdown og støtte for egendefinert Markdown-syntaks i OPS. Resten av dette emnet beskriver Docs Markdown-utvidelsen.
- [Docs Article Templates](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-article-templates): Tillater bruk av Markdown-skjelettinnhold på nye filer.

## <a name="prerequisites-and-assumptions"></a>Forutsetninger og antakelser

Hvis du vil sette inn relative koblinger, bilder og annet innebygd innhold med Docs Markdown-utvidelsen på en nøyaktig måte, må du ha VS Code-arbeidsområdet begrenset til roten av det klonede repositoriet for det åpne publiseringssystemet (OPS).

Enkelte typer syntaks som støttes av utvidelsen, for eksempel varsler og snutter, er egendefinert Markdown for OPS, og vil ikke gjengis riktig hvis det ikke publiseres via OPS.

## <a name="how-to-use-the-docs-markdown-extension"></a>Slik bruker du Docs Markdown-utvidelsen

Hvis du vil ha tilgang til Docs Markdown-menyen, skriver du inn `ALT+M`. Du kan klikke eller bruke opp/ned-pilene for å velge den ønskede funksjonen, eller skrive inn for å starte filtreringen og trykke `ENTER` når funksjonen du vil bruke utheves på menyen. Følgende er tilgjengelig:

|Funksjon     |Beskrivelse           |
|-------------|----------------------|
|Forhåndsvisning      |Forhåndsvis det aktive emnet i et side-ved-side-vindu med Docs Preview-utvidelsen. Dette alternativet er bare tilgjengelig hvis Docs Preview er installert.|
|Fet         |Formaterer teksten **fet**.|
|Kursiv       |Formaterer teksten *kursiv*.|
|Kode         |Hvis en linje eller mindre er valgt, formaterer du tekst som `inline code`.<br><br>Hvis det er merket av for flere linjer, formaterer du dem som en inngjerdet kodeblokk, og du kan også velge et programmeringsspråk som støttes av OPS.|
|Varsel        |Setter inn et notat, viktig, advarsel eller tips.<br><br>Velg varselet fra menyen, og velg deretter varseltype. Hvis du tidligere har valgt tekst, blir den omgitt av valgt varselsyntaks. Hvis ingen tekst velges, legges det til et nytt varsel med plassholdertekst.|
|Nummerert liste|Setter inn en ny nummerert liste.<br><br> Hvis det er merket av for flere linjer, blir hver av dem et listeelement. Vær oppmerksom på at nummererte lister vises Markdown som 1-ere, men vil gjengis på docs.microsoft.com som fortløpende tall eller, for nestede lister, bokstaver. For å opprette en nestet nummerert liste tar du fra kategorien i den overordnede listen.|
|Punktmerket liste|Setter inn en ny punktmerket liste.|
|Tabell        |Setter inn en tabellstruktur for Markdown.<br><br>Når du velger tabellkommandoen, kan du angi hvor mange kolonner og rader i formatkolonner:rader, som 3:4. Legg merke til at det maksimale antallet kolonner som du kan angi via denne utvidelsen er 5, som er anbefalt maksimum for lesbarhet.|
|Koble til filen i repositoriet|Setter inn en relativ kobling til en annen fil i gjeldende repositorium. Når du har valgt dette alternativet, skriver du inn kommandovinduet for å filtrere filene etter navn, og velger deretter filen du vil bruke. Hvis du tidligere har valgt tekst, blir dette koblingsteksten. Hvis ikke, brukes H1 i målfilen som koblingstekst.|
|Koble til nettside    |Setter inn en kobling til en nettside. Etter du har valgt dette alternativet, limer eller skriver du inn URI-en i kommandovinduet. `https://` er obligatorisk. Hvis du tidligere har valgt tekst, blir dette koblingsteksten. Hvis ikke, brukes URI-en som koblingstekst.|
|Koble til overskrift     |Kobler til et bokmerke i gjeldende fil eller en annen fil i repositoriet.<br>`Bookmark in this file`: Velge fra en liste over overskrifter i gjeldende fil å sette inn et bokmerke som er riktig formatert.<br>`Bookmark in another file`: Filtrer først etter filnavn og velg filen du vil koble til, og velg deretter en overskrift i den valgte filen.|
|Bilde        |Skriv inn alternativ tekst (kreves for tilgjengelighet) og velg den, og deretter kaller du denne kommandoen til å filtrere listen over støttede bildefiler i repo og velger den du vil bruke. Hvis du ikke har valgt alt-tekst når du kaller denne kommandoen, vil du bli bedt om det før du kan velge en bildefil.|
|Inkludering      |Finn en fil for å bygge inn i gjeldende fil.|
|Kodesnutt      |Finn en kodesnutt i repo for å bygge inn i gjeldende fil.|
|Video        |Legg til en innebygd video.|
|Mal     |Opprett en ny fil, og bruk en Markdown-mal. Se [Maler](#how-to-use-docs-templates) nedenfor hvis du vil ha mer informasjon.|

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

## <a name="how-to-show-the-legacy-toolbar"></a>Slik viser du en eldre verktøylinje

Brukere av forhåndsversjonen av utvidelsen vil legge merke til at redigeringsverktøylinjen ikke lenger vises nederst i VS Code-vinduet når Docs Markdown-utvidelsen er installert. Dette er fordi verktøylinjen tok opp mye plass på VS Code-statuslinjen og ikke fulgte anbefalt fremgangsmåte for UX-utvidelsen, så den er avverget i den nye utvidelsen. Du kan imidlertid vise verktøylinjen ved å oppdatere VS Code settings.json-filen som følger:

1. I VS Code går du til Fil -> Preferanser -> Innstillinger (`CTRL+Comma`).
1. Velg Brukerinnstillinger for å endre innstillingene for alle VS Code-arbeidsområder eller Arbeidsplassinnstillinger for å endre dem bare for gjeldende arbeidsområde.
1. I Standardinnstillinger-ruten finner du Docs Authoring-utvidelseskonfigurasjon og velger blyantikonet ved siden av ønsket innstilling. Deretter blir du bedt om å velge enten `true` eller `false`. Når du har foretatt valget, legger VS Code automatisk til verdien til settings.json-filen, og du blir bedt om å laste inn på nytt i vinduet for at endringene skal tre i kraft.

## <a name="how-to-use-docs-templates"></a>Slik bruker du Docs-maler

Docs Article Templates-utvidelsen gjør at skrivere i VS Code kan hente en Markdown-mal fra et sentralisert lager og bruke den i en fil. Maler kan sikre at nødvendige metadata er inkludert i artiklene, at innholdsstandarder følges og så videre. Maler administreres som Markdown-filer i et offentlig GitHub-repositorium.

### <a name="to-apply-a-template-in-vs-code"></a>Slik bruker du maler i VS Code

1. Hvis du ikke har installert Docs Markdown-utvidelsen, trykker du på F1 for å åpne kommandopaletten. Begynn å skrive inn «mal» for å filtrere, og klikk deretter på `Docs: Template`. Hvis du har installert Docs Markdown, kan du enten bruke kommandopaletten, eller klikke på `Alt+M` for å hente opp Docs Markdown-hurtigmenyen, og deretter velge `Template` fra listen.
1. Velg ønsket mal fra listen som vises.

### <a name="to-add-your-github-id-andor-microsoft-alias-to-your-vs-code-settings"></a>Slik legger du til GitHub-ID-en eller Microsoft-aliaset i VS Code-innstillingene

Templates-utvidelsen støtter tre dynamiske metadatafelter: forfatter, ms.author og ms.date. Dette betyr at hvis maloppretteren bruker disse feltene i metadatahodet til en Markdown-mal, blir de automatisk fylt ut i filen når du bruker malen, som følger:

|Metadata  |Verdi|
|----------|---------------|
|forfatter    |GitHub-ID-en din hvis angitt i VS Code-innstillingsfilen.|
|ms.author |Microsoft-aliaset ditt hvis angitt i VS Code-innstillingsfilen. Hvis ikke du er en Microsoft-ansatt, lar du dette stå uspesifisert.|
|ms.date   |Gjeldende dato i det Docs-støttede formatet DD/MM/YYYY. Vær oppmerksom på at datoen ikke oppdateres automatisk hvis du oppdaterer filen etterpå. Du må oppdatere denne manuelt for å vise hvor ny artikkelen er.|

### <a name="to-set-author-github-id-andor-msauthor-microsoft-alias"></a>Slik angir du forfatter (GitHub-ID) og/eller ms.author (Microsoft-alias)

1. I VS Code går du til Fil -> Preferanser -> Innstillinger (`CTRL+Comma`).
1. Velg Brukerinnstillinger for å endre innstillingene for alle VS Code-arbeidsområder, eller Arbeidsområdeinnstillinger for å endre dem bare for gjeldende arbeidsområde.
1. Finn konfigurasjonen for Docs Article Templates-utvidelsen i Standardinnstillinger-ruten til venstre. Klikk på blyantikonet ved siden av ønsket innstilling, og klikk deretter på Erstatt i Innstillinger.
1. Brukerinnstillingsfanen åpnes side-ved-side, med en ny oppføring nederst.
1. Legg til riktig GitHub-ID eller Microsoft e-postalias, og lagre filen.
1. Det kan hende du må lukke og starte VS Code på nytt for at endringene skal tre i kraft.
1. Når du nå bruker en mal som bruker dynamiske felter, blir GitHub-ID-en og/eller Microsoft-aliaset automatisk fylt ut i metadatahodet.
