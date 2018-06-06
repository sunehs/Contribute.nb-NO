---
title: Viktig om Git og GitHub for dokumentasjon
description: Denne artikkelen gir en oversikt over Git, GitHub-repositorium og hvordan innholdet er organisert, samt navnekonvensjoner som brukes for docs.microsoft.com.
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 06/30/2017
ms.prod: non-product-specific
ms.topic: contributor-guide
ms.custom: external-contributor-guide
ms.openlocfilehash: 5f7f90b69953e23833906202c739d2168b139d7e
ms.sourcegitcommit: 782b689882cce3ce07f5613763322989f2d0d63f
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/05/2018
ms.locfileid: "34469490"
---
# <a name="git-and-github-essentials-for-docs"></a>Viktig om Git og GitHub for Docs

## <a name="overview"></a>Oversikt

Som bidragsyter til innhold i Docs, vil du arbeide med flere verktøy og prosesser. Du skal arbeide parallelt med andre bidragsytere på det samme prosjektet, potensielt nøyaktig samme innhold, til og med samtidig. Alt dettes gjøres mulig gjennom Git- og GitHub-programvare.

Git er et versjonskontrollsystem med åpen kildekode. Det gjør det denne typen prosjektsamarbeid enklere gjennom *distribuert versjonskontroll* av filer i *repositorier*. Git gjør det rett og slett mulig å integrere arbeidsstrømmer gjort av flere bidragsytere over tid for et gitt repositorium.

GitHub er en web-basert vertstjeneste for Git-repositorier, for eksempel de som brukes til å lagre [docs.microsoft.com](https://docs.microsoft.com)-innhold. GitHub er vert for hovedrepositoriet for ethvert prosjekt, hvorfra bidragsytere kan ta kopier av arbeidet sitt.

## <a name="git"></a>Git

Hvis du er kjent med sentraliserte versjonskontrollsystemer (for eksempel Team Foundation Server, SharePoint eller Visual SourceSafe), vil du oppdage at Git har en unik bidragsarbeidsflyt og terminologi til å støtte den distribuerte modellen. Det er for eksempel ingen fillåsing som vanligvis er forbundet med sjekk ut- / sjekk inn-operasjoner. Git gjelder faktisk endringer på et enda mindre nivå, der man sammenligner filer byte for byte.

Git bruker også en trinnvis struktur for å lagre og behandle innhold for et prosjekt:

- *Repositorium*: også kjent som et *repo*, dette er den høyeste lagringsenheten. Et repositorium inneholder én eller flere grener.
- *Gren*: En lagringsenhet som inneholder filene og mappene som utgjør et prosjekts innholdssett. Grener skiller arbeidsstrømmer (vanligvis kalt versjoner). Bidrag gjøres alltid og er begrenset til en bestemt gren. Alle repositorier inneholder en standardgren (vanligvis kalt «hoved») og én eller flere grener som skal slås sammen tilbake i den overordnede grenen. Den overordnede grenen fungerer som gjeldende versjon og «eneste kilde til sannhet» for prosjektet. Det er overordnet alle andre grener i repositoriet den er opprettet fra.

Bidragsytere samhandler med Git for å oppdatere og manipulere repositorier både på lokale og GitHub-nivåer:

- Lokalt gjennom verktøy som Git Bash-konsollen, som støtter Git-kommandoer for behandling av lokale repositorier og kommunikasjon med GitHub-repositorier
- Via [www.github.com](https://www.github.com), som integrerer Git for å administrere avstemming av bidrag som flyter tilbake til hovedrepositoriet

## <a name="github"></a>GitHub

> [!NOTE]
> Selv om Docs-veiledning er basert på å bruke GitHub, bruke noen grupper Visual Studio-gruppetjenester som vert for Git-repositorier. Visual Studio Team Explorer-klienten gir et grafisk brukergrensesnitt for samhandling med Team Services-repositorier som et alternativ til å bruke Git-kommandoer via en kommandolinje.
> </br>
> Dessuten mange av disse retningslinjene utviklet som anbefalt fremgangsmåte basert på årevis med erfaring i vertskap for Azure-tjenesteinnhold i GitHub. De kan være nødvendig i noen Docs-repositorier.

Alle arbeidsflyter begynner og slutter på GitHub-nivå, der hovedrepositoriet for alle Docs-prosjektet er lagret. Kopier som bidragsytere oppretter til egen bruk, distribueres på tvers av flere datamaskiner. Disse kopiene avstemmes til slutt tilbake til prosjektets primære GitHub-repositorium.

### <a name="directory-organization"></a>Katalogorganisering

Som nevnt tidligere, fungerer et prosjekts standard-/hovedgren som den gjeldende innholdsversjonen for prosjektet. Innholdet i den overordnede grenen – og grener som er opprettet fra den – justeres løst med organiseringen av artikler på de tilsvarende dokumentsidene. Underkataloger brukes for å skille likt innhold (som tjenester), medieinnhold (som bildefiler), og «inkludering»-filer (som muliggjør gjenbruk av innhold).

Du finner vanligvis en `articles` hovedkatalog utenfor roten til repositoriet. Artikler-katalogen inneholder et sett med underkataloger. Artikler i underkatalogene er formatert som Markdown-filer som bruker en *.md*-utvidelse. Noen repositorier som støtter flere tjenester bruker en generisk `/articles` underkatalog, som [ https://github.com/microsoft/Azure-Docs ](https://github.com/microsoft/Azure-Docs)-repositoriet. Andre kan bruke et tjenestespesifikt navn, for eksempel [ https://github.com/microsoft/IntuneDocs ](https://github.com/microsoft/IntuneDocs)-repositoriet, som bruker `/IntuneDocs`.

I roten i denne katalogen kan du finne generelle artikler relatert til samlet service eller produkt. Vanligvis kan du deretter finne en annen serie med underkataloger som samsvarer med funksjoner/tjenester eller vanlige scenarier. Artikler om Azure «virtuell maskin» er for eksempel i `/virtual-machines`-underkatalogen, og Intune «forstå og utforske»-artikler i `/understand-explore`-underkatalogen.

### <a name="media-subdirectory"></a>Media-underkatalog

Hver artikkelkatalog inneholder en `/media`-underkatalog for tilsvarende mediefiler. Mediefiler inneholder bilder som brukes av artikler som har bildereferanser.

### <a name="includes-subdirectory"></a>inkluderinger-underkatalog

Når vi har innhold som er delt i to eller flere artikler, plasseres det i en `/includes` underkatalog av hovedkatalogen`articles`. I en Markdown-fil som bruker inkluderingsfilen, plasseres en tilsvarende Markdown-utvidelse med «inkludering» der inkluderingsfilen må refereres til.

Se [Slik bruker du Markdown: inkluderinger](how-to-write-use-markdown.md#includes) for ytterligere hjelp.

### <a name="markdown-file-template"></a>Markdown-filmal

For enkelhets skyld, inneholder rotkatalogen til hvert repositorium typisk en Markdown-malfil kalt `template.md`. Du kan bruke denne malfilen som en «startfil» hvis du vil opprette en ny artikkel for sending til repositoriet. Filen inneholder:

- En **metadataoverskrift** merket på toppen av filen, merket av to, 3-bindestrekslinjer. Den inneholder forskjellige koder som brukes til å spore informasjon som er relatert til artikkelen. Artikkelens metadata muliggjør visse funksjoner, for eksempel opprettertillegg, bidragsytertillegg, navigasjonssti og beskrivelser for artikkelen. Den omfatter også SEO-optimalisering og rapporteringsprosesser som Microsoft bruker til å evaluere ytelsen til innholdet. Så disse metadataene er viktige!
- En **metadata-del** som beskriver de forskjellige metadata-kodene og verdiene. Hvis du er usikker på verdiene som skal brukes for metadata-inndeling, kan du la dem være tomme eller kommentere dem med en hashtag (#), og de blir gjennomgått/fullført av evaluerer for pull-forespørsel for repositoriet.
- Ulike **eksempler på bruk av Markdown** for å formatere elementer i en artikkel.
- Generelle **instruksjoner om bruk av Markdown-utvidelser**, som du kan bruke for ulike typer varsler.
- Eksempler på **innebygd video** ved å bruke en iframe.
- Generelle **instruksjoner om bruk av docs.microsoft.com-utvidelser**, som du kan bruke for spesielle kontroller som knapper og velgere.

## <a name="pull-requests"></a>Pull-forespørsler

En *pull-forespørsel* er en praktisk måte for bidragsyteren å foreslå et sett med endringer på som vil bli anvendt på standardgrenen. Endringene (også kjent som *utføringer*) er lagret i en bidragsyters gren, slik at GitHub først kan modellere virkningen av å *slå dem sammen* i standardgrenen. En pull-forespørsel fungerer også som en mekanisme for å gi tilbakemelding fra en build-/valideringsprosess, pull-forespørselskontrolløren, for å løse potensielle problemer med eller spørsmål før endringene er slått sammen til standardgrenen.

Det er to måter å bidra med pull-forespørsel på, avhengig av størrelsen på endringer du vil foreslå. Vi dekker dette i detalj senere i [GitHub-arbeidsflyt](how-to-write-workflows-major.md)-delen av denne veiledningen.

<!---- Reference links for Docs landing pages, associated GitHub repositories, and related Forums matrix. ------------------>
<!---- PLEASE INSERT URLS IN ASCENDING SORT ORDER, AND REMOVE LOCALE SEGMENT FROM URLS (that is, en-us) FOR LOCALIZED FORUMS! -->
<!---- NOTE: these links are saved for future use in another/new article; no longer used above in this article --->
[Visual-Studio-Page]:(https://docs.microsoft.com/en-us/visualstudio/index)
[Visual-Studio-Repo-Internal]:(https://github.com/Microsoft/vsdocs)
[Visual-Studio-Repo-External]:(https://github.com/Microsoft/visualstudio-docs)
[Visual-Studio-SO]: (https://stackoverflow.com/search?q=Visual+Studio+2017)
[Dotnet-Page]: https://docs.microsoft.com/dotnet
[Dotnet-Core-Page]: https://docs.microsoft.com/dotnet/articles/welcome
[Dotnet-Core-Repo]: https://github.com/dotnet/docs
[EM-ATA-Land]: https://docs.microsoft.com/advanced-threat-analytics/
[EM-ATA-Repo]: https://github.com/Microsoft/ATADocs
[EM-AzureAD-Land]: https://docs.microsoft.com/active-directory/
[EM-AzureAD-Repo]: https://github.com/Azure/azure-content/tree/master/articles/active-directory/
[EM-AzureRMS-Land]: https://docs.microsoft.com/rights-management/
[EM-AzureRMS-Repo]: https://github.com/Microsoft/Azure-RMSDocs
[EM-Intune-Land]: https://docs.microsoft.com/intune/
[EM-Intune-Repo]: https://github.com/microsoft/intuneDocs
[EM-Land-Page]: https://docs.microsoft.com/enterprise-mobility/
[EM-Land-Repo]: https://github.com/Microsoft/EMDocs/
[EM-MFA-Land]: https://docs.microsoft.com/multi-factor-authentication/
[EM-MFA-Repo]: https://github.com/Azure/azure-content/tree/master/articles/multi-factor-authentication
[EM-MIM-Land]: https://docs.microsoft.com/microsoft-identity-manager/
[EM-MIM-Repo]: https://github.com/Microsoft/MIMDocs
[EM-RemoteApp-Land]: https://docs.microsoft.com/en-us/remoteapp/
[EM-RemoteApp-Repo]: https://github.com/Azure/azure-content/tree/master/articles/remoteapp
[Forum-MSDN-ATA]: https://social.technet.microsoft.com/Forums/en-US/home?forum=mata
[Forum-MSDN-AzureAD]: https://social.msdn.microsoft.com/Forums/en-US/home?forum=WindowsAzureAD
[Forum-MSDN-AzureRMS]: https://social.technet.microsoft.com/Forums/en-US/home?forum=rmsapps%2Crmscloud&filter=alltypes&sort=lastpostdesc
[Forum-MSDN-EM]: https://social.technet.microsoft.com/Forums/en-US/home?sort=relevancedesc&brandIgnore=True&searchTerm=Enterprise+Mobility
[Forum-MSDN-Intune]: https://social.technet.microsoft.com/Forums/en-us/home?category=microsoftintune
[Forum-MSDN-Main]: https://social.msdn.microsoft.com/Forums/home
[Forum-MSDN-MFA]: https://social.msdn.microsoft.com/Forums/en-US/home?forum=windowsazureactiveauthentication
[Forum-MSDN-MIM]: https://social.technet.microsoft.com/Forums/en-US/home?category=identitymanagement
[Forum-MSDN-RemoteApp]: https://social.technet.microsoft.com/Forums/en-US/home?filter=alltypes&brandIgnore=True&sort=relevancedesc&searchTerm=Azure+Remote+or+RemoteApp
[Forum-SO-AzureAD]: https://stackoverflow.com/questions/tagged/azure-active-directory
[Forum-SO-AzureRMS]: https://stackoverflow.com/questions/tagged/rights-management
[Forum-SO-Dotnet]: https://stackoverflow.com/questions/tagged/.net
[Forum-SO-Dotnet-Core]: https://stackoverflow.com/questions/tagged/.net-core
[Forum-SO-Main]: https://stackoverflow.com/tags
[Forum-SO-Intune]: https://stackoverflow.com/questions/tagged/intune
[Forum-SO-MFA]: https://stackoverflow.com/search?q=%5Bazure%5D+multi-factor
[Forum-SO-MIM]: https://stackoverflow.com/search?q=Microsoft+Identity+Manager
[Forum-SO-RemoteApp]: https://stackoverflow.com/questions/tagged/remoteapp
[Forum-TechNet-Main]: https://social.technet.microsoft.com/Forums/home
[Forum-Yammer-AzureRMS]: https://www.yammer.com/AskIPTeam
[Forum-Yammer-Main]: https://www.yammer.com/
