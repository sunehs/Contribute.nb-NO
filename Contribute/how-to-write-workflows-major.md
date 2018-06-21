---
title: GitHub-bidragsarbeidsflyt for store eller tidkrevende endringer
description: Denne artikkelen viser hvordan du bruker arbeidsflyt for «store» bidrag for å bidra til docs.microsoft.com-artikler.
ms.date: 08/30/2017
ms.openlocfilehash: 31f9421fc5edbc2f65c5ff20a86da08c70211ec7
ms.sourcegitcommit: 92aef5ea8bdd692c5c393d5c8f99b9e4f672ef2b
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/19/2018
ms.locfileid: "36239829"
---
# <a name="github-contribution-workflow-for-major-or-long-running-changes"></a>GitHub-bidragsarbeidsflyt for store eller tidkrevende endringer

> [!IMPORTANT]
> Alle repositorier som publiserer til docs.microsoft.com har tatt i bruk enten [Microsofts regler for god opptreden for åpne kilder](https://opensource.microsoft.com/codeofconduct/) eller [.NET Foundations regler for god opptreden](https://dotnetfoundation.org/code-of-conduct). Hvis du vil ha mer informasjon, se [Vanlige spørsmål om regler for god opptreden](https://opensource.microsoft.com/codeofconduct/faq/). Eller kontakt [ opencode@microsoft.com ](mailto:opencode@microsoft.com), eller [ conduct@dotnetfoundation.org ](mailto:conduct@dotnetfoundation.org) med eventuelle spørsmål eller kommentarer.<br>
>
> Mindre rettelser eller klargjøring av dokumentasjon og kodeeksempler i offentlige repositorier dekkes i [Vilkår for bruk av docs.microsoft.com](https://docs.microsoft.com/legal/termsofuse). Nye eller vesentlige endringer vil generere en kommentar i pull-forespørselen, og ber deg om å sende en elektronisk Bidragslisensavtale (CLA) hvis du ikke er en medarbeider hos Microsoft. Du må fylle ut det elektroniske skjemaet før pull-forespørselen kan slås sammen.

## <a name="overview"></a>Oversikt

Denne arbeidsflyten er egnet for en bidragsyter som har behov for å gjøre en større endring eller vil bli en hyppig bidragsyter til et repositorium. Hyppige bidragsytere har vanligvis kontinuerlige (langvarige) endringer, som går gjennom flere validerings-/build-/oppsamlingssykluser eller over flere dager før pull-forespørselen godkjennes og slås sammen.

Eksempler på denne typen bidrag inkluderer:

[!INCLUDE[contribute-major-changes-change-definition](includes/contribute-how-to-write-workflows-major-change-definition.md)]

### <a name="terminology"></a>Terminologi

Før du starter, skal vi gå gjennom noen av Git/GitHub-begrepene og -kallenavnene som brukes i denne artikkelflyten. Ikke vær redd om du ikke forstår dem nå. Bare vit at du får lære om dem, og du kan se på denne delen igjen når du trenger å verifisere en definisjon.

| Navn | Beskrivelse |
|-----------|-------------|
|forgrening|Brukes vanligvis som et substantiv i forbindelse med en kopi av et GitHub-hovedrepositorium. I praksis er en forgrening bare et annet repositorium. Men det er spesielt i den forstand at GitHub beholder en kobling tilbake til det overordnede/hovedrepositoriet. Det brukes noen ganger som et verb, som i «Du må forgrene repositoriet først.»|
|ekstern|En navngitt tilkobling til et eksternt repositorium, for eksempel «opprinnelse» eller «oppstrøms» ekstern. Git refererer til disse som eksterne fordi de brukes som referanse på et repositorium som er vert på en annen datamaskin. I denne arbeidsflyten er en ekstern alltid et GitHub-repositorium.|
|opprinnelse|Navnet som er tilordnet til tilkoblingen mellom det lokale repositoriet det ble klonet fra. I denne arbeidsflyten representerer opprinnelse tilkoblingen til forgreningen din. Den brukes noen ganger som et kallenavn for selve det opprinnelige repositoriet, som i «Husk å overføre endringene til opprinnelsen.»|
|oppstrøms|Som den opprinnelige eksterne, er oppstrøms en navngitt tilkobling til et annet repositorium. I denne arbeidsflyten representerer oppstrøms forbindelsen mellom det lokale repositoriet og hovedrepositoriet, hvor forgreningen ble opprettet fra. Den brukes noen ganger som et kallenavn for selve oppstrømsrepositoriet, som i «Husk å overføre endringene fra oppstrøms.»|

## <a name="workflow"></a>Arbeidsflyt

>[!IMPORTANT]
> Hvis du ikke allerede har gjort det, må du fullføre trinnene i [Oppsett](get-started-setup-github.md)-delen. Denne delen hjelper deg med å opprette GitHub-kontoen, installere Git Bash og et redigeringsprogram for Markdown, opprette en forgrening og sette opp ditt lokale repositorium. Hvis du ikke er kjent med Git og GitHub-konsepter som et repositorium eller en gren, må du først gå gjennom [Git og grunnleggende om GitHub](git-github-fundamentals.md).

I denne arbeidsflyten endrer du flyt i en gjentatt syklus. De starter fra enhetens lokale repositorium, flyter tilbake i GitHub-forgreningen, inn i GitHub-hovedrepositoriet og tilbake lokalt igjen etter hvert som du inkorporerer endringer fra andre bidragsytere.

### <a name="use-github-flow"></a>Bruk GitHub-flyt

Husk fra [Git og grunnleggende om GitHub](git-github-fundamentals.md#git) at et Git-repositorium inneholder en hovedgren, pluss eventuelle ekstra pågående grener som ikke har blitt integrert i hovedgrenen. Når du introduserer et sett av logisk relaterte endringer, er det anbefalt fremgangsmåte å opprette en *arbeidsgren* for å administrere dine endringer gjennom arbeidsflyten. Vi refererer til det her som en arbeidsgren fordi det er et arbeidsområde for gjenta/forfine endringer til de kan integreres tilbake i hovedgrenen.

Ved å isolere relaterte endringer til en spesifikk gren kan du kontrollere og introdusere disse endringene uavhengig, rette dem mot en spesifikk frigjøringstid i publiseringssyklusen. I virkeligheten kan du, avhengig av typen arbeid du utfører, enkelt ende opp med flere arbeidsgrener i repositoriet. Det er ikke uvanlig å arbeide på flere grener på samme tid, hvor hver enkelt representerer forskjellige prosjekter.

>[!TIP]
>Å foreta endringene i hovedgrenen er *ikke* anbefalt fremgangsmåte. Tenk deg at du bruker den overordnede grenen til å introdusere en rekke endringer for en fastsatt fremtidig utgivelse. Du avslutter endringene og venter på å slippe dem. I mellomtiden har du en presserende forespørsel om å fikse noe, og dermed foretar du endringen av en fil i hovedgrenen og publiserer endringen. I dette eksempelet publiserer du utilsiktet både løsningen *og* endringene du planla å utgi på en spesifikk dato.

La oss nå opprette en ny arbeidsgren i ditt lokale repositorium, for å fange opp dine foreslåtte endringer. Hver git-klient er forskjellig, så se i hjelpen for din foretrukne klienten. Du kan se en oversikt over prosessen i GitHub-guiden i [GitHub-flyt](https://guides.github.com/introduction/flow/).

[!INCLUDE[contribute-how-to-write-workflows-pull-request-processing](includes/contribute-how-to-write-workflows-pull-request-processing.md)]

## <a name="next-steps"></a>Neste trinn

Det var det! Du har gjort et bidrag til docs.microsoft.com-innhold!

- For å lære mer om emner som for eksempel Markdown og Markdown-utvidelsessyntaks, går du videre til delen «Grunnleggende om skriving».
