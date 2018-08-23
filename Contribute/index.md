---
title: Oversikt over håndboken Microsoft Docs-bidragsyter
description: Guiden beskriver hvordan du kan bidra til Microsoft-dokumentasjonssiden docs.microsoft.com.
author: billwagner
ms.author: wiwagn
manager: wpickett
ms.date: 04/17/2018
ms.openlocfilehash: 6206f61a69c14575a726da9ce64ad0b765c7aa87
ms.sourcegitcommit: 886ca76086a302d1d6124967df12a5bcfe4fd4b5
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 08/10/2018
ms.locfileid: "40251422"
---
# <a name="microsoft-docs-contributor-guide-overview"></a>Oversikt over håndboken Microsoft Docs-bidragsyter

Velkommen til [docs.microsoft.com](https://docs.microsoft.com) (Docs) bidragsyterguiden!

Flere av dokumentasjonssettene våre er åpen kilde og driftes av GitHub. Stadig flere hos Microsoft har begynt å bruke denne modellen hele tiden. Til og med dokumentasjonssett som ikke er fullstendig åpen kilde, har repositorier som er åpne for publikum, der du kan gjøre pull-forespørsler. Det gjør prosessen enklere og forbedrer kommunikasjon mellom produktutviklerne, innholdsgruppen og kundene. Du oppnår flere fordeler når du ikke skjuler hva du jobber med:

- Repositorier for åpen kilde viser hva de planlegger, for å få tilbakemeldinger om hvilken dokumentasjon som trengs mest.
- Repositorier for åpen kilde viser hva de går gjennom, slik at de kan publisere det nyttigste innholdet i første utgivelse.
- Repositorier for åpen kilde viser hva de oppdaterer, slik at det er enklere å fortsette å forbedre innholdet.

Brukeropplevelsen på [docs.microsoft.com](https://docs.microsoft.com) integrerer arbeidsflyter fra [GitHub](https://github.com) direkte for å gjøre det enda enklere. Start ved å [redigere dokumentet du viser](#quick-edits-to-existing-documents). Du kan også hjelpe ved å [gå gjennom nye emner](#review-open-prs) eller [opprette gode problemer](#create-quality-issues).

> [!IMPORTANT]
> Alle repositorier som publiserer til docs.microsoft.com, har tatt i bruk [Microsofts regler for god opptreden for åpne kilder](https://opensource.microsoft.com/codeofconduct/) eller [.NET Foundations regler for god opptreden](https://dotnetfoundation.org/code-of-conduct). Hvis du vil ha mer informasjon, se [Vanlige spørsmål om regler for god opptreden](https://opensource.microsoft.com/codeofconduct/faq/). Eller kontakt [ opencode@microsoft.com ](mailto:opencode@microsoft.com), eller [ conduct@dotnetfoundation.org ](mailto:conduct@dotnetfoundation.org) med eventuelle spørsmål eller kommentarer.<br>
>
> Mindre rettelser eller klargjøring av dokumentasjon og kodeeksempler i offentlige repositorier dekkes i [Vilkår for bruk av docs.microsoft.com](https://docs.microsoft.com/legal/termsofuse). Nye eller vesentlige endringer genererer en kommentar i pull-forespørselen og ber deg om å sende en elektronisk Bidragslisensavtale (CLA) hvis du ikke er en medarbeider hos Microsoft. Du må fylle ut nettskjemaet før vi kan gå gjennom eller godta pull-forespørselen din.

## <a name="quick-edits-to-existing-documents"></a>Rask redigering av eksisterende dokumenter

Rask redigering gjør det enklere å rapportere og fikse små feil og utelatelser i dokumentene. Små stavefeil og dårlig grammatikk sniker seg inn i publiserte dokumenter uansett hva man gjør. Du kan opprette et problem for å rapporterer en feil, men det er kjappere og enklere å opprette en pull-forespørsel for å fikse det. Nesten alle artikler har en redigeringsknapp, som vist i den neste illustrasjonen. Hvis du klikker på **Redigering**-knappen, blir du ført til kildefilen på GitHub.

![Plassering av Rediger-koblingen](./media/index/edit-article.png)

Hvis du vil redigere artikkelen, klikker du på blyantikonet, som vist i den neste illustrasjonen.

> [!NOTE]
> Hvis blyantikonet er grått, må du logge på en GitHub-konto eller opprette en ny konto. Gjør endringene i redigeringsprogrammet på nettet. Hvis du vil sjekke formateringen av endringen du har gjort, kan du klikke på **Forhåndsvis endringer**.

![Plassering av blyantikonet](./media/index/editicon.png)

Rull til bunnen av siden når du er ferdig med redigeringen. Skriv inn en tittel og beskrivelse av pull-forespørselen, og klikk på **Foreslå filendring**, som vist i den neste illustrasjonen:

![foreslår endringen](./media/index/submit-pull-request.png)

Det var det! Medlemmer av innholdsgruppen vil gå gjennom og implementere pull-forespørselen. Hvis du har gjort store endringer kan du få tilbakemeldinger med forespørsler om endringer.

Brukergrensesnittet for redigering på GitHub reagerer på tillatelsene du har på repositoriet. De viste bildene viser hvordan det ser ut for brukere som ikke har skrivetillatelse for målrepositoriet. GitHub oppretter automatisk en forgrening av målrepositoriet i kontoen din. Hvis du har skrivetillatelse for målrepositoriet, blir det oppretter GitHub en ny gren der. Grenen får et navn som følger mønsteret **\<GitHubID\>-oppdatering-n**, og bruker din GitHub-ID og et nummer som identifiserer oppdateringsgrenen.

Vi bruker pull-forespørsler til alle endringer, til og med for bidragsytere med skrivetillatelse. `master`-grenen er beskyttet i de fleste repositorier, og oppdateringer må utføres som pull-forespørsler.

Redigering i nettleser er best for små endringer og for endringer som ikke skjer ofte. Hvis du leverer store bidrag eller bruker avanserte Git-funksjoner (for eksempel grenadministrering eller løsing av avanserte sammenslåingskonflikter),må du [opprette en forgrening av repositoriet og arbeide lokalt](how-to-write-workflows-major.md).

## <a name="review-open-prs"></a>Gå gjennom åpne pull-forespørsler

Hvis du sjekker åpne pull-forespørsler, kan du lese nye emner før de blir publisert. Gjennomganger følger prosessen for [GitHub-flyt](https://guides.github.com/introduction/flow/). Du kan se forslåtte oppdateringer og nye artikler i offentlige repositorier. Gå gjennom dem, og legg til dine kommentarer. Hvis du vil finne noe du er interessert i, kan du se gjennom dokumentrepositoriene våre og sjekke de åpne pull-forespørslene. Tilbakemeldinger fra fellesskapet om foreslåtte oppdateringer hjelper hele fellesskapet.

## <a name="create-quality-issues"></a>Opprette gode problemer

Vi jobber alltid på dokumentasjonen vår. Gode problemer lar oss fokusere på problemene med høyest prioritet i felleskapet. Jo flere detaljer du har, jo nyttigere er problemet. Fortell oss hva du så etter. Fortell oss hvilke ord du søkte etter. Hvis du ikke kan komme i gang, kan du fortelle oss hvordan du vil begynne å utforske ny teknologi.

Problemer starter samtalen om hva som må gjøres. Innholdsgruppen svarer på disse problemene med ideer om hva vi kan legge til, og spør hva du syns. Når vi har opprettet et utkast, vil vi be deg om å [gå gjennom pull-forespørselen](#review-open-prs).

## <a name="get-more-involved"></a>Gjør mer

Andre emner viser deg hvordan du kommer i gang med å bidra til Microsoft Docs på en produktiv måte. De forklarer hvordan du arbeider med GitHub-repositorier, Markdown-verktøy og tillegg som brukes på Microsoft Docs-plattformen.
