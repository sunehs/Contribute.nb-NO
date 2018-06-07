---
title: Slik bruker du koblinger i dokumentasjonen
description: Denne artikkelen gir råd om hvordan du oppretter koblinger til innhold i docs.microsoft.com.
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 06/29/2017
ms.prod: non-product-specific
ms.topic: contributor-guide
ms.custom: external-contributor-guide
ms.openlocfilehash: 1699e57ac6a4dc4c5a1ef099ea183b3cbc6307cd
ms.sourcegitcommit: 782b689882cce3ce07f5613763322989f2d0d63f
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/05/2018
ms.locfileid: "34469536"
---
# <a name="using-links-in-documentation"></a><span data-ttu-id="a3761-103">Bruke koblinger i dokumentasjon</span><span class="sxs-lookup"><span data-stu-id="a3761-103">Using links in documentation</span></span>
<span data-ttu-id="a3761-104">Denne artikkelen beskriver hvordan du bruker hyperkoblinger fra sider som er plassert på docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="a3761-104">This article describes how to use hyperlinks from pages hosted at docs.microsoft.com.</span></span> <span data-ttu-id="a3761-105">Koblinger er enkle å legge til i markdown med noen få varierende konvensjoner.</span><span class="sxs-lookup"><span data-stu-id="a3761-105">Links are easy to add into markdown with a few varying conventions.</span></span> <span data-ttu-id="a3761-106">Kobler punktbrukere innhold på samme side, lenker til andre nærliggende sider, eller lenker til URL-adresser og eksterne områder.</span><span class="sxs-lookup"><span data-stu-id="a3761-106">Links point users to content in the same page, point off into other neighboring pages, or point to external sites and URLs.</span></span>

<span data-ttu-id="a3761-107">Docs.microsoft.com-bakserveren bruker Åpne publiseringstjenester (OPS) som implementerer DocFX Flavored Markdown (DFM).</span><span class="sxs-lookup"><span data-stu-id="a3761-107">The docs.microsoft.com site backend uses Open Publishing Services (OPS) which implements DocFX Flavored Markdown (DFM).</span></span> <span data-ttu-id="a3761-108">DFM er svært kompatibel med GitHub Flavored Markdown (GFM), og DFM legger til ekstra funksjonalitet ved hjelp av Markdown-utvidelser.</span><span class="sxs-lookup"><span data-stu-id="a3761-108">DFM is highly compatible with GitHub Flavored Markdown (GFM), and DFM adds additional functionality through Markdown extensions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3761-109">Alle koblinger må være sikre (`https` vs `http`) når målet støtter det (som de fleste bør).</span><span class="sxs-lookup"><span data-stu-id="a3761-109">All links must be secure (`https` vs `http`) whenever the target supports it (which the vast majority should).</span></span>

## <a name="link-text"></a><span data-ttu-id="a3761-110">Koble tekst</span><span class="sxs-lookup"><span data-stu-id="a3761-110">Link text</span></span>

<span data-ttu-id="a3761-111">Ordene du inkluderer i koblingsteksten bør være vennlige.</span><span class="sxs-lookup"><span data-stu-id="a3761-111">The words that you include in link text should be friendly.</span></span> <span data-ttu-id="a3761-112">Med andre ord, bør de være normale engelske ord eller tittelen på siden som du kobler til.</span><span class="sxs-lookup"><span data-stu-id="a3761-112">In other words, they should be normal English words or the title of the page that you're linking to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3761-113">Ikke bruk «klikk her.»</span><span class="sxs-lookup"><span data-stu-id="a3761-113">Do not use "click here."</span></span> <span data-ttu-id="a3761-114">Det er dårlig for SEO og beskriver ikke målet tilstrekkelig.</span><span class="sxs-lookup"><span data-stu-id="a3761-114">It's bad for SEO and doesn't adequately describe the target.</span></span>

<span data-ttu-id="a3761-115">**Rett:**</span><span class="sxs-lookup"><span data-stu-id="a3761-115">**Correct:**</span></span>

- `For more information, see the [contributor guide index](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

- `For more details, see the [SET TRANSACTION ISOLATION LEVEL](https://msdn.microsoft.com/library/ms173763.aspx) reference.`

<span data-ttu-id="a3761-116">**Galt:**</span><span class="sxs-lookup"><span data-stu-id="a3761-116">**Incorrect:**</span></span>

- `For more details, see [https://msdn.microsoft.com/library/ms173763.aspx](https://msdn.microsoft.com/library/ms173763.aspx).`

- `For more information, click [here](https://github.com/Azure/azure-content/blob/master/contributor-guide/contributor-guide-index.md).`

## <a name="links-from-one-article-to-another"></a><span data-ttu-id="a3761-117">Koblinger fra en artikkel til en annen</span><span class="sxs-lookup"><span data-stu-id="a3761-117">Links from one article to another</span></span>

<span data-ttu-id="a3761-118">Hvis du vil opprette en innebygd kobling fra en teknisk Docs-artikkel til en annen teknisk Docs-artikkel i samme docset, kan du bruke følgende koblingssyntaks:</span><span class="sxs-lookup"><span data-stu-id="a3761-118">To create an inline link from a Docs technical article to another Docs technical article within the same docset, use the following link syntax:</span></span>

- <span data-ttu-id="a3761-119">En artikkel i en katalog lenker til en artikkel i samme katalog:</span><span class="sxs-lookup"><span data-stu-id="a3761-119">An article in a directory links to another article in the same directory:</span></span>

  `[link text](article-name.md)`

- <span data-ttu-id="a3761-120">En artikkel lenker fra en underkatalog til en artikkel i rotkatalogen:</span><span class="sxs-lookup"><span data-stu-id="a3761-120">An article links from a subdirectory to an article in the root directory:</span></span>

  `[link text](../article-name.md)`

- <span data-ttu-id="a3761-121">En artikkel i rotkatalogen lenker til en artikkel i en underkatalog:</span><span class="sxs-lookup"><span data-stu-id="a3761-121">An article in the root directory links to an article in a subdirectory:</span></span>

  `[link text](./directory/article-name.md)`

- <span data-ttu-id="a3761-122">En artikkel i underkatalogen lenker til en artikkel i en annen underkatalog:</span><span class="sxs-lookup"><span data-stu-id="a3761-122">An article in a subdirectory links to an article in another subdirectory:</span></span>

  `[link text](../directory/article-name.md)`

- <span data-ttu-id="a3761-123">En artikkel lenker på tvers av docsets (selv om det er i det samme repositoriet): `[link text](./directory/article-name)`</span><span class="sxs-lookup"><span data-stu-id="a3761-123">An article linking across docsets (even if in the same repository): `[link text](./directory/article-name)`</span></span>
  
## <a name="links-to-anchors"></a><span data-ttu-id="a3761-124">Koblinger til forankringer</span><span class="sxs-lookup"><span data-stu-id="a3761-124">Links to anchors</span></span>

<span data-ttu-id="a3761-125">Du trenger ikke opprette forankringer.</span><span class="sxs-lookup"><span data-stu-id="a3761-125">You do not have to create anchors.</span></span> <span data-ttu-id="a3761-126">De genereres automatisk på publiseringstidspunktet for alle H2-overskrifter.</span><span class="sxs-lookup"><span data-stu-id="a3761-126">They're automatically generated at publishing time for all H2 headings.</span></span> <span data-ttu-id="a3761-127">Det eneste du trenger å gjøre er å opprette koblinger til delene H2.</span><span class="sxs-lookup"><span data-stu-id="a3761-127">The only thing you have to do is create links to the H2 sections.</span></span>

- <span data-ttu-id="a3761-128">Slik kobler du til en overskrift i den samme artikkelen:</span><span class="sxs-lookup"><span data-stu-id="a3761-128">To link to a heading within the same article:</span></span>

  `[link](#the-text-of-the-H2-section-separated-by-hyphens)`
  `[Create cache](#create-cache)`

- <span data-ttu-id="a3761-129">Slik kobler du til et anker i en annen artikkel i samme undermappe:</span><span class="sxs-lookup"><span data-stu-id="a3761-129">To link to an anchor in another article in the same subdirectory:</span></span>

  `[link text](article-name.md#anchor-name)`
  `[Configure your profile](media-services-create-account.md#configure-your-profile)`

- <span data-ttu-id="a3761-130">Slik kobler du til et anker i en annen serviceunderkatalog:</span><span class="sxs-lookup"><span data-stu-id="a3761-130">To link to an anchor in another service subdirectory:</span></span>

  `[link text](../directory/article-name.md#anchor-name)`
  `[Configure your profile](../directory/media-services-create-account.md#configure-your-profile)`

## <a name="links-from-includes"></a><span data-ttu-id="a3761-131">Koblinger fra inkluderinger</span><span class="sxs-lookup"><span data-stu-id="a3761-131">Links from includes</span></span>

<span data-ttu-id="a3761-132">Fordi inkluderingsfiler er plassert i en annen katalog, må du bruke lengre relative baner.</span><span class="sxs-lookup"><span data-stu-id="a3761-132">Because include files are located in another directory, you must use longer relative paths.</span></span> <span data-ttu-id="a3761-133">Hvis du vil koble til en artikkel fra en inkluderingsfil, kan du bruke dette formatet:</span><span class="sxs-lookup"><span data-stu-id="a3761-133">To link to an article from an include file, use this format:</span></span>

    [link text](../articles/folder/article-name.md)

## <a name="links-in-selectors"></a><span data-ttu-id="a3761-134">Koblinger i velgere</span><span class="sxs-lookup"><span data-stu-id="a3761-134">Links in selectors</span></span>

<span data-ttu-id="a3761-135">Hvis du har velgere som er innebygd i en inkludering – som Azure-dokumentasjonsgruppen – kan du bruke følgende koblingsstruktur:</span><span class="sxs-lookup"><span data-stu-id="a3761-135">If you have selectors that are embedded in an include--as does the Azure documentation team--use the following link structure:</span></span>

    > <span data-ttu-id="a3761-136">[AZURE.SELECTOR-LIST (Nedtrekk1 | Nedtrekk2 )]</span><span class="sxs-lookup"><span data-stu-id="a3761-136">[AZURE.SELECTOR-LIST (Dropdown1 | Dropdown2 )]</span></span>
    - [<span data-ttu-id="a3761-137">(Tekst 1 | Eksempel 1)</span><span class="sxs-lookup"><span data-stu-id="a3761-137">(Text1 | Example1 )</span></span>](../articles/folder/article-name1.md)
    - [<span data-ttu-id="a3761-138">(Tekst 1 | Eksempel 2)</span><span class="sxs-lookup"><span data-stu-id="a3761-138">(Text1 | Example2 )</span></span>](../articles/folder/article-name2.md)
    - [<span data-ttu-id="a3761-139">(Tekst 2 | Eksempel 3 )</span><span class="sxs-lookup"><span data-stu-id="a3761-139">(Text2 | Example3 )</span></span>](../articles/folder/article-name3.md)
    - <span data-ttu-id="a3761-140">[(Tekst 2 | Eksempel 4 )](../articles/folder/article-name4.md) --></span><span class="sxs-lookup"><span data-stu-id="a3761-140">[(Text2 | Example4 )](../articles/folder/article-name4.md) --></span></span>

## <a name="reference-style-links"></a><span data-ttu-id="a3761-141">Referansestilkoblinger</span><span class="sxs-lookup"><span data-stu-id="a3761-141">Reference-style links</span></span>

<span data-ttu-id="a3761-142">Du kan bruke referansestilkoblinger for å gjøre det enklere å lese kildeinnholdet.</span><span class="sxs-lookup"><span data-stu-id="a3761-142">You can use reference-style links to make your source content easier to read.</span></span> <span data-ttu-id="a3761-143">Referansestilkoblinger erstatter innebygd koblingssyntaks med forenklet syntaks som gjør det mulig å flytte lange URL-adresser til slutten av artikkelen.</span><span class="sxs-lookup"><span data-stu-id="a3761-143">Reference-style links replace inline link syntax with simplified syntax that allows you to move the long URLs to the end of the article.</span></span> <span data-ttu-id="a3761-144">Her er [Daring Fireball](https://daringfireball.net/projects/markdown/)s eksempel:</span><span class="sxs-lookup"><span data-stu-id="a3761-144">Here's [Daring Fireball](https://daringfireball.net/projects/markdown/) 's example:</span></span>

<span data-ttu-id="a3761-145">Innebygd tekst:</span><span class="sxs-lookup"><span data-stu-id="a3761-145">Inline text:</span></span>

    I get 10 times more traffic from [Google][1] than from [Yahoo][2] or [MSN][3].

<span data-ttu-id="a3761-146">Koblingsreferanser på slutten av artikkelen:</span><span class="sxs-lookup"><span data-stu-id="a3761-146">Link references at the end of the article:</span></span>

    <!--Reference links in article-->
    [1]: http://google.com/
    [2]: http://search.yahoo.com/
    [3]: http://search.msn.com/

<span data-ttu-id="a3761-147">Kontroller at du inkluderer mellomrommet etter kolonet, før koblingen.</span><span class="sxs-lookup"><span data-stu-id="a3761-147">Make sure that you include the space after the colon, before the link.</span></span> <span data-ttu-id="a3761-148">Når du kobler til andre tekniske artikler og glemmer å inkludere mellomrommet, brytes koblingen i en publisert artikkel.</span><span class="sxs-lookup"><span data-stu-id="a3761-148">When you link to other technical articles, if you forget to include the space, the link will be broken in the published article.</span></span>

## <a name="links-to-pages-that-are-not-part-of-the-technical-documentation-set"></a><span data-ttu-id="a3761-149">Koblinger til sider som ikke er en del av den tekniske dokumentasjonen</span><span class="sxs-lookup"><span data-stu-id="a3761-149">Links to pages that are not part of the technical documentation set</span></span>

<span data-ttu-id="a3761-150">Hvis du vil koble til en side på en annen Microsoft-eiendom (for eksempel en prisside, SLA-side, eller noe annet som ikke er en dokumentasjons-artikkel), bruker en absolutt URL-adresse, men utelater den nasjonale innstillingen.</span><span class="sxs-lookup"><span data-stu-id="a3761-150">To link to a page on another Microsoft property (such as a pricing page, SLA page, or anything else that is not a documentation article), use an absolute URL, but omit the locale.</span></span> <span data-ttu-id="a3761-151">Målet her er at koblinger fungerer i GitHub og i det gjengitte området:</span><span class="sxs-lookup"><span data-stu-id="a3761-151">The goal here is that links work in GitHub and on the rendered site:</span></span>

    [link text](https://azure.microsoft.com/pricing/details/virtual-machines/)

## <a name="links-to-third-party-sites"></a><span data-ttu-id="a3761-152">Koblinger til tredjepartssider</span><span class="sxs-lookup"><span data-stu-id="a3761-152">Links to third-party sites</span></span>

<span data-ttu-id="a3761-153">Man skaper den beste brukeropplevelsen ved å sende brukere til et annet område så sjeldent som mulig.</span><span class="sxs-lookup"><span data-stu-id="a3761-153">The best user experience minimizes sending users to another site.</span></span> <span data-ttu-id="a3761-154">Baser koblinger til tredjepartssider, som vi noen ganger trenger, på denne informasjonen:</span><span class="sxs-lookup"><span data-stu-id="a3761-154">So base any links to third-party sites, which we do sometimes need, on this info:</span></span>

- <span data-ttu-id="a3761-155">**Ansvarlighet**: Koble til tredjepartsinnhold når det er tredjepartens informasjon som skal deles.</span><span class="sxs-lookup"><span data-stu-id="a3761-155">**Accountability**: Link to third-party content when it's the third-party's information to share.</span></span> <span data-ttu-id="a3761-156">Det er for eksempel ikke opp til Microsoft å fortelle andre hvordan de skal bruke utviklerverktøy for Android – det er opp til Google.</span><span class="sxs-lookup"><span data-stu-id="a3761-156">For example, it's not Microsoft's place to tell people how to use Android developer tools--that is Google's story to tell.</span></span> <span data-ttu-id="a3761-157">Hvis vi må, kan vi forklare hvordan du bruker Android-utviklerverktøy *med* Azure, men Google bør fortelle historien om hvordan du bruker verktøyene deres.</span><span class="sxs-lookup"><span data-stu-id="a3761-157">If we need to, we can explain how to use Android developer tools *with* Azure, but Google should tell the story of how to use their tools.</span></span>
- <span data-ttu-id="a3761-158">**PM-godkjenning**: Be om at Microsoft godkjenner tredjepartsinnhold.</span><span class="sxs-lookup"><span data-stu-id="a3761-158">**PM signoff**: Request that Microsoft sign off on third-party content.</span></span> <span data-ttu-id="a3761-159">Ved å koble til noe, sier vi noe om vår tillit til dette, og vår forpliktelse hvis folk følger instruksjonene.</span><span class="sxs-lookup"><span data-stu-id="a3761-159">By linking to it, we are saying something about our trust in it and our obligation if people follow the instructions.</span></span>
- <span data-ttu-id="a3761-160">**Freshness-gjennomganger**: Kontroller at tredjepartsinfo fortsatt er oppdatert, riktig og relevante, og at koblingen ikke er endret.</span><span class="sxs-lookup"><span data-stu-id="a3761-160">**Freshness reviews**: Make sure that the third-party info is still current, correct, and relevant, and that the link hasn’t changed.</span></span>
- <span data-ttu-id="a3761-161">**Frakoblet**: Gjør brukere oppmerksom på at de kommer til et annet område.</span><span class="sxs-lookup"><span data-stu-id="a3761-161">**Offsite**: Make users aware that they are going to another site.</span></span> <span data-ttu-id="a3761-162">Hvis konteksten ikke gjør det klart, kan du legge til et kvalifiserende uttrykk.</span><span class="sxs-lookup"><span data-stu-id="a3761-162">If the context does not make that clear, add a qualifying phrase.</span></span> <span data-ttu-id="a3761-163">For eksempel: «Forutsetninger inkluderer Android-utviklerverktøy, som du kan laste ned i Android Studio-området.»</span><span class="sxs-lookup"><span data-stu-id="a3761-163">For example: “Prerequisites include the Android Developer Tools, which you can download on the Android Studio site.”</span></span>
- <span data-ttu-id="a3761-164">**Neste trinn**: Det er greit å legge til en kobling til, si, en MVP-blogg i en «Neste trinn»-del.</span><span class="sxs-lookup"><span data-stu-id="a3761-164">**Next steps**: It’s fine to add a link to, say, an MVP blog in a "Next steps" section.</span></span> <span data-ttu-id="a3761-165">Bare sørg for at brukere forstår at de forlater området.</span><span class="sxs-lookup"><span data-stu-id="a3761-165">Again, just make sure that users understand they’ll be leaving the site.</span></span>
- <span data-ttu-id="a3761-166">**Juridisk**: Vi er juridisk dekket under **Koblinger til tredjepartsområder** i **Vilkår for bruk**-bunnteksten på hver side ms.com-side.</span><span class="sxs-lookup"><span data-stu-id="a3761-166">**Legal**: We are covered legally under **Links to Third Party Sites** in the **Terms of Use** footer on every ms.com page.</span></span>

## <a name="links-to-msdn-or-technet"></a><span data-ttu-id="a3761-167">Koblinger til MSDN eller TechNet</span><span class="sxs-lookup"><span data-stu-id="a3761-167">Links to MSDN or TechNet</span></span>

<span data-ttu-id="a3761-168">Når du skal koble til MSDN eller TechNet, bruker du full kobling til emnet og fjerner «nb-NO»-språkinnstillingen fra koblingen.</span><span class="sxs-lookup"><span data-stu-id="a3761-168">When you need to link to MSDN or TechNet, use the full link to the topic, and remove the "en-us" language locale from the link.</span></span>

## <a name="links-to-azure-powershell-reference-content"></a><span data-ttu-id="a3761-169">Koblinger til Azure PowerShell-referanseinnhold</span><span class="sxs-lookup"><span data-stu-id="a3761-169">Links to Azure PowerShell reference content</span></span>

<span data-ttu-id="a3761-170">Azure PowerShell-referanseinnholdet har gjennomgått flere endringer siden november 2016.</span><span class="sxs-lookup"><span data-stu-id="a3761-170">The Azure PowerShell reference content has been through several changes since November 2016.</span></span> <span data-ttu-id="a3761-171">Bruk følgende retningslinjer for å koble til dette innholdet fra andre artikler på docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="a3761-171">Use the following guidelines for linking to this content from other articles on docs.microsoft.com.</span></span>

<span data-ttu-id="a3761-172">Strukturen til URL-adressen:</span><span class="sxs-lookup"><span data-stu-id="a3761-172">Structure of the URL:</span></span>

* <span data-ttu-id="a3761-173">For kommandleter:</span><span class="sxs-lookup"><span data-stu-id="a3761-173">For cmdlets:</span></span>
  - `/powershell/module/<module-name>/<cmdlet-name>[?view=<moniker-name>]`
* <span data-ttu-id="a3761-174">For konseptuelle emner:</span><span class="sxs-lookup"><span data-stu-id="a3761-174">For conceptual topics:</span></span>
  - `/powershell/azure/<topic-file-name>[?view=<moniker-name>]`
  - `/powershell/azure/<service-name>/<topic-file-name>[?view=<moniker-name>]`

<span data-ttu-id="a3761-175">&lt;kallenavn&gt;-delen er valgfri.</span><span class="sxs-lookup"><span data-stu-id="a3761-175">The &lt;moniker-name&gt; portion is optional.</span></span> <span data-ttu-id="a3761-176">Hvis det utelates, vil du bli henvist til den nyeste versjonen av innholdet.</span><span class="sxs-lookup"><span data-stu-id="a3761-176">If it's omitted, you will be directed to the latest version of the content.</span></span> <span data-ttu-id="a3761-177">&lt;Tjenestenavn&gt;-delen er et av eksemplene som vises i følgende grunnleggende URL-adresser:</span><span class="sxs-lookup"><span data-stu-id="a3761-177">The &lt;service-name&gt; portion is one of the examples shown in the following base URLs:</span></span>

- <span data-ttu-id="a3761-178">Azure PowerShell (AzureRM)-innhold: https://docs.microsoft.com/powershell/azure/</span><span class="sxs-lookup"><span data-stu-id="a3761-178">Azure PowerShell (AzureRM) content: https://docs.microsoft.com/powershell/azure/</span></span>
- <span data-ttu-id="a3761-179">Azure PowerShell (ASM)-innhold: https://docs.microsoft.com/powershell/azure/ _servicemanagement_</span><span class="sxs-lookup"><span data-stu-id="a3761-179">Azure PowerShell (ASM) content: https://docs.microsoft.com/powershell/azure/_servicemanagement_</span></span>
- <span data-ttu-id="a3761-180">Azure Active Directory (AzureAD) PowerShell-innhold: https://docs.microsoft.com/powershell/azure/_active-directory_</span><span class="sxs-lookup"><span data-stu-id="a3761-180">Azure Active Directory (AzureAD) PowerShell content: https://docs.microsoft.com/powershell/azure/_active-directory_</span></span>
- <span data-ttu-id="a3761-181">Azure Service Fabric PowerShell: https://docs.microsoft.com/powershell/azure/_service-fabric_</span><span class="sxs-lookup"><span data-stu-id="a3761-181">Azure Service Fabric PowerShell: https://docs.microsoft.com/powershell/azure/_service-fabric_</span></span>
- <span data-ttu-id="a3761-182">Azure Information Protection PowerShell: https://docs.microsoft.com/powershell/azure/_aip_</span><span class="sxs-lookup"><span data-stu-id="a3761-182">Azure Information Protection PowerShell: https://docs.microsoft.com/powershell/azure/_aip_</span></span>
- <span data-ttu-id="a3761-183">Azure Elastic DB Jobs PowerShell: https://docs.microsoft.com/powershell/azure/_elasticdbjobs_</span><span class="sxs-lookup"><span data-stu-id="a3761-183">Azure Elastic DB Jobs PowerShell: https://docs.microsoft.com/powershell/azure/_elasticdbjobs_</span></span>

<span data-ttu-id="a3761-184">Når du bruker disse URL-ene, blir du omdirigert til den nyeste versjonen av innholdet.</span><span class="sxs-lookup"><span data-stu-id="a3761-184">When you use these URLs, you will be redirected to the latest version of the content.</span></span> <span data-ttu-id="a3761-185">På denne måten trenger du ikke å angi et versjonskallenavn.</span><span class="sxs-lookup"><span data-stu-id="a3761-185">This way, you don't have to specify a version moniker.</span></span> <span data-ttu-id="a3761-186">Og du har ikke koblinger til konseptuelt innhold som må oppdateres når versjonen endres.</span><span class="sxs-lookup"><span data-stu-id="a3761-186">And you won't have links to conceptual content that must be updated when the version changes.</span></span>

<span data-ttu-id="a3761-187">Hvis du vil opprette den riktige koblingen, finner du siden du vil koble til i nettleseren og kopierer URL-adressen.</span><span class="sxs-lookup"><span data-stu-id="a3761-187">To create the correct link, find the page that you want to link to in your browser, and copy the URL.</span></span>
<span data-ttu-id="a3761-188">Deretter fjerner du «https://docs.microsoft.com» og informasjon for nasjonal innstilling.</span><span class="sxs-lookup"><span data-stu-id="a3761-188">Then, remove "https://docs.microsoft.com" and the locale info.</span></span>

<span data-ttu-id="a3761-189">Når du kobler fra en innholdsfortegnelse, må du bruke den fullstendige URL-adressen uten informasjon om nasjonal innstilling.</span><span class="sxs-lookup"><span data-stu-id="a3761-189">When you're linking from a TOC, you must use the full URL without the locale information.</span></span>

<span data-ttu-id="a3761-190">Markdown-eksempel:</span><span class="sxs-lookup"><span data-stu-id="a3761-190">Example markdown:</span></span>

```markdown
[Get-AzureRmResourceGroup](/powershell/module/azurerm.resources/get-azurermresourcegroup)
[Get-AzureRmResourceGroup](/powershell/module/azurerm.resources/get-azurermresourcegroup?view=azurermps-4.1.0)
[New-AzureVM](/powershell/module/azure/new-azurevm?view=azuresmps-4.0.0)
[New-AzureRmVM](/powershell/module/azurerm.compute/new-azurermvm)
[Install Azure PowerShell for Service Management](/powershell/azure/servicemanagement/install-azurerm-ps)
[Install Azure PowerShell](/powershell/azure/install-azurerm-ps)
```
