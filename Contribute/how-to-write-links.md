---
title: Slik bruker du koblinger i dokumentasjonen
description: Denne artikkelen gir råd om hvordan du oppretter koblinger til innhold i docs.microsoft.com.
ms.date: 06/29/2017
ms.openlocfilehash: a66e2fb4febf1947afe01919b96b1c10873cf57d
ms.sourcegitcommit: 92aef5ea8bdd692c5c393d5c8f99b9e4f672ef2b
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/19/2018
ms.locfileid: "36239730"
---
# <a name="using-links-in-documentation"></a>Bruke koblinger i dokumentasjon
Denne artikkelen beskriver hvordan du bruker hyperkoblinger fra sider som er plassert på docs.microsoft.com. Koblinger er enkle å legge til i markdown med noen få varierende konvensjoner. Kobler punktbrukere innhold på samme side, lenker til andre nærliggende sider, eller lenker til URL-adresser og eksterne områder.

Docs.microsoft.com-bakserveren bruker Åpne publiseringstjenester (OPS) som implementerer DocFX Flavored Markdown (DFM). DFM er svært kompatibel med GitHub Flavored Markdown (GFM), og DFM legger til ekstra funksjonalitet ved hjelp av Markdown-utvidelser.

> [!IMPORTANT]
> Alle koblinger må være sikre (`https` vs `http`) når målet støtter det (som de fleste bør).

## <a name="link-text"></a>Koble tekst

Ordene du inkluderer i koblingsteksten bør være vennlige. Med andre ord, bør de være normale engelske ord eller tittelen på siden som du kobler til.

> [!IMPORTANT]
> Ikke bruk «klikk her.» Det er dårlig for SEO og beskriver ikke målet tilstrekkelig.

**Rett:**

- `For more information, see the [contributor guide index](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

- `For more details, see the [SET TRANSACTION ISOLATION LEVEL](https://msdn.microsoft.com/library/ms173763.aspx) reference.`

**Galt:**

- `For more details, see [https://msdn.microsoft.com/library/ms173763.aspx](https://msdn.microsoft.com/library/ms173763.aspx).`

- `For more information, click [here](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

## <a name="links-from-one-article-to-another"></a>Koblinger fra en artikkel til en annen

Hvis du vil opprette en innebygd kobling fra en teknisk Docs-artikkel til en annen teknisk Docs-artikkel i samme docset, kan du bruke følgende koblingssyntaks:

- En artikkel i en katalog lenker til en artikkel i samme katalog:

  `[link text](article-name.md)`

- En artikkel lenker fra en underkatalog til en artikkel i rotkatalogen:

  `[link text](../article-name.md)`

- En artikkel i rotkatalogen lenker til en artikkel i en underkatalog:

  `[link text](./directory/article-name.md)`

- En artikkel i underkatalogen lenker til en artikkel i en annen underkatalog:

  `[link text](../directory/article-name.md)`

- En artikkel lenker på tvers av docsets (selv om det er i det samme repositoriet): `[link text](./directory/article-name)`

> [!IMPORTANT]
> Det er ikke brukt `~/` som en del av koblingen i noen av eksemplene over. Hvis du oppretter en kobling til roten i repositoriet, starter du med `/`. Hvis du inkluderer `~/`, blir koblingene ugyldige når du navigerer i kilderepositorier i GitHub. Hvis du starter banen med `/`, fungerer koblingene som de skal.

## <a name="links-to-anchors"></a>Koblinger til forankringer

Du trenger ikke opprette forankringer. De genereres automatisk på publiseringstidspunktet for alle H2-overskrifter. Det eneste du trenger å gjøre er å opprette koblinger til delene H2.

- Slik kobler du til en overskrift i den samme artikkelen:

  `[link](#the-text-of-the-H2-section-separated-by-hyphens)`
  `[Create cache](#create-cache)`

- Slik kobler du til et anker i en annen artikkel i samme undermappe:

  `[link text](article-name.md#anchor-name)`
  `[Configure your profile](media-services-create-account.md#configure-your-profile)`

- Slik kobler du til et anker i en annen serviceunderkatalog:

  `[link text](../directory/article-name.md#anchor-name)`
  `[Configure your profile](../directory/media-services-create-account.md#configure-your-profile)`

## <a name="links-from-includes"></a>Koblinger fra inkluderinger

Fordi inkluderingsfiler er plassert i en annen katalog, må du bruke lengre relative baner. Hvis du vil koble til en artikkel fra en inkluderingsfil, kan du bruke dette formatet:

    [link text](../articles/folder/article-name.md)

## <a name="links-in-selectors"></a>Koblinger i velgere

Hvis du har velgere som er innebygd i en inkludering – som Azure-dokumentasjonsgruppen – kan du bruke følgende koblingsstruktur:

    > [AZURE.SELECTOR-LIST (Nedtrekk1 | Nedtrekk2 )]
    - [(Tekst 1 | Eksempel 1)](../articles/folder/article-name1.md)
    - [(Tekst 1 | Eksempel 2)](../articles/folder/article-name2.md)
    - [(Tekst 2 | Eksempel 3 )](../articles/folder/article-name3.md)
    - [(Tekst 2 | Eksempel 4 )](../articles/folder/article-name4.md) -->

## <a name="reference-style-links"></a>Referansestilkoblinger

Du kan bruke referansestilkoblinger for å gjøre det enklere å lese kildeinnholdet. Referansestilkoblinger erstatter innebygd koblingssyntaks med forenklet syntaks som gjør det mulig å flytte lange URL-adresser til slutten av artikkelen. Her er [Daring Fireball](https://daringfireball.net/projects/markdown/)s eksempel:

Innebygd tekst:

    I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].

Koblingsreferanser på slutten av artikkelen:

    <!--Reference links in article-->
    [1]: http://google.com/
    [2]: http://search.yahoo.com/
    [3]: http://search.msn.com/

Kontroller at du inkluderer mellomrommet etter kolonet, før koblingen. Når du kobler til andre tekniske artikler og glemmer å inkludere mellomrommet, brytes koblingen i en publisert artikkel.

## <a name="links-to-pages-that-are-not-part-of-the-technical-documentation-set"></a>Koblinger til sider som ikke er en del av den tekniske dokumentasjonen

Hvis du vil koble til en side på en annen Microsoft-eiendom (for eksempel en prisside, SLA-side, eller noe annet som ikke er en dokumentasjons-artikkel), bruker en absolutt URL-adresse, men utelater den nasjonale innstillingen. Målet her er at koblinger fungerer i GitHub og i det gjengitte området:

    [link text](https://azure.microsoft.com/pricing/details/virtual-machines/)

## <a name="links-to-third-party-sites"></a>Koblinger til tredjepartssider

Man skaper den beste brukeropplevelsen ved å sende brukere til et annet område så sjeldent som mulig. Baser koblinger til tredjepartssider, som vi noen ganger trenger, på denne informasjonen:

- **Ansvarlighet**: Koble til tredjepartsinnhold når det er tredjepartens informasjon som skal deles. Det er for eksempel ikke opp til Microsoft å fortelle andre hvordan de skal bruke utviklerverktøy for Android – det er opp til Google. Hvis vi må, kan vi forklare hvordan du bruker Android-utviklerverktøy *med* Azure, men Google bør fortelle historien om hvordan du bruker verktøyene deres.
- **PM-godkjenning**: Be om at Microsoft godkjenner tredjepartsinnhold. Ved å koble til noe, sier vi noe om vår tillit til dette, og vår forpliktelse hvis folk følger instruksjonene.
- **Freshness-gjennomganger**: Kontroller at tredjepartsinfo fortsatt er oppdatert, riktig og relevante, og at koblingen ikke er endret.
- **Frakoblet**: Gjør brukere oppmerksom på at de kommer til et annet område. Hvis konteksten ikke gjør det klart, kan du legge til et kvalifiserende uttrykk. For eksempel: «Forutsetninger inkluderer Android-utviklerverktøy, som du kan laste ned i Android Studio-området.»
- **Neste trinn**: Det er greit å legge til en kobling til, si, en MVP-blogg i en «Neste trinn»-del. Bare sørg for at brukere forstår at de forlater området.
- **Juridisk**: Vi er juridisk dekket under **Koblinger til tredjepartsområder** i **Vilkår for bruk**-bunnteksten på hver side ms.com-side.

## <a name="links-to-msdn-or-technet"></a>Koblinger til MSDN eller TechNet

Når du skal koble til MSDN eller TechNet, bruker du full kobling til emnet og fjerner «nb-NO»-språkinnstillingen fra koblingen.

## <a name="links-to-azure-powershell-reference-content"></a>Koblinger til Azure PowerShell-referanseinnhold

Azure PowerShell-referanseinnholdet har gjennomgått flere endringer siden november 2016. Bruk følgende retningslinjer for å koble til dette innholdet fra andre artikler på docs.microsoft.com.

Strukturen til URL-adressen:

* For kommandleter:
  - `/powershell/module/<module-name>/<cmdlet-name>[?view=<moniker-name>]`
* For konseptuelle emner:
  - `/powershell/azure/<topic-file-name>[?view=<moniker-name>]`
  - `/powershell/azure/<service-name>/<topic-file-name>[?view=<moniker-name>]`

&lt;kallenavn&gt;-delen er valgfri. Hvis det utelates, vil du bli henvist til den nyeste versjonen av innholdet. &lt;Tjenestenavn&gt;-delen er et av eksemplene som vises i følgende grunnleggende URL-adresser:

- Azure PowerShell (AzureRM)-innhold: https://docs.microsoft.com/powershell/azure/
- Azure PowerShell (ASM)-innhold: https://docs.microsoft.com/powershell/azure/ _servicemanagement_
- Azure Active Directory (AzureAD) PowerShell-innhold: https://docs.microsoft.com/powershell/azure/_active-directory_
- Azure Service Fabric PowerShell: https://docs.microsoft.com/powershell/azure/_service-fabric_
- Azure Information Protection PowerShell: https://docs.microsoft.com/powershell/azure/_aip_
- Azure Elastic DB Jobs PowerShell: https://docs.microsoft.com/powershell/azure/_elasticdbjobs_

Når du bruker disse URL-ene, blir du omdirigert til den nyeste versjonen av innholdet. På denne måten trenger du ikke å angi et versjonskallenavn. Og du har ikke koblinger til konseptuelt innhold som må oppdateres når versjonen endres.

Hvis du vil opprette den riktige koblingen, finner du siden du vil koble til i nettleseren og kopierer URL-adressen.
Deretter fjerner du «https://docs.microsoft.com» og informasjon for nasjonal innstilling.

Når du kobler fra en innholdsfortegnelse, må du bruke den fullstendige URL-adressen uten informasjon om nasjonal innstilling.

Markdown-eksempel:

```markdown
[Get-AzureRmResourceGroup](/powershell/module/azurerm.resources/get-azurermresourcegroup)
[Get-AzureRmResourceGroup](/powershell/module/azurerm.resources/get-azurermresourcegroup?view=azurermps-4.1.0)
[New-AzureVM](/powershell/module/azure/new-azurevm?view=azuresmps-4.0.0)
[New-AzureRmVM](/powershell/module/azurerm.compute/new-azurermvm)
[Install Azure PowerShell for Service Management](/powershell/azure/servicemanagement/install-azurerm-ps)
[Install Azure PowerShell](/powershell/azure/install-azurerm-ps)
```
