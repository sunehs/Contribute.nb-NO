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
# <a name="install-content-authoring-tools"></a><span data-ttu-id="9f0ea-103">Installer innholdsredigeringsverktøy</span><span class="sxs-lookup"><span data-stu-id="9f0ea-103">Install content authoring tools</span></span>

<span data-ttu-id="9f0ea-104">Denne artikkelen beskriver fremgangsmåten for interaktiv installering av Git-klientverktøy og kode for Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-104">This article describes the steps to interactively install Git client tools and Visual Studio Code.</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="9f0ea-105">Installer [Git for Windows](https://git-scm.com/download/win)</span><span class="sxs-lookup"><span data-stu-id="9f0ea-105">Install [Git for Windows](https://git-scm.com/download/win)</span></span>
> * <span data-ttu-id="9f0ea-106">Installer [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="9f0ea-106">Install [Visual Studio Code](https://code.visualstudio.com/)</span></span>
> * <span data-ttu-id="9f0ea-107">Installer [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)</span><span class="sxs-lookup"><span data-stu-id="9f0ea-107">Install [Docs Authoring Pack](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="9f0ea-108">Hvis du bare gjør små endringer i en artikkel, er det *ikke nødvendig* å fullføre trinnene i denne artikkelen, og du kan fortsette direkte til [arbeidsflyten for raske endringer](index.md#quick-edits-to-existing-documents).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-108">If you're making only minor changes to an article, you *do not* need to complete the steps in this article and can continue directly to the [quick changes workflow](index.md#quick-edits-to-existing-documents).</span></span>
>
> <span data-ttu-id="9f0ea-109">Viktige bidragsytere oppfordres til å fullføre disse trinnene, som gjør det mulig å bruke [arbeidsflyten for store/tidkrevende endringer](how-to-write-workflows-major.md).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-109">Major contributors are encouraged to complete these steps, which enable you to use the [major/long-running changes workflow](how-to-write-workflows-major.md).</span></span> <span data-ttu-id="9f0ea-110">Selv om du har skrivetillatelser i hovedrepositoriet, *anbefaler vi på det sterkeste (og denne veiledningen forutsetter) at du forgrener og kloner repositoriet*, slik at du har lese/skrivetillatelser til å lagre de foreslåtte endringene i din forgrening.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-110">Even if you have write permissions in the main repository, *we highly recommend (and this guide assumes) that you fork and clone the repository*, so that you have read/write permissions to store your proposed changes in your fork.</span></span>

## <a name="install-git-client-tools-on-windows"></a><span data-ttu-id="9f0ea-111">Installer Git-klientverktøy på Windows</span><span class="sxs-lookup"><span data-stu-id="9f0ea-111">Install Git client tools on Windows</span></span>

 <span data-ttu-id="9f0ea-112">Installer den nyeste versjonen av [Software Freedom Conservancys Git-klientverktøy](https://git-scm.com/download/).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-112">Install the latest version of [Software Freedom Conservancy's Git client tools](https://git-scm.com/download/).</span></span> <span data-ttu-id="9f0ea-113">Installereringen inkluderer Git-versjonens kontrollsystem og Git Bash, kommandolinjeappen som du bruker for interaksjon med ditt lokale Git-repositorium.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-113">The install includes the Git version control system and Git Bash, the command-line app that you use to interact with your local Git repository.</span></span>

<span data-ttu-id="9f0ea-114">Hvis du foretrekker et grafisk brukergrensesnitt (GUI) fremfor et kommandolinjegrensesnitt (CLI), kan du se [Software Freedom Conservancys tilgjengelige GUI-klientside](https://git-scm.com/downloads/guis), [GitHubs GitHub Desktop](https://desktop.github.com/), eller [ Visual Studio Code](https://www.visualstudio.com/products/code-vs.aspx) for noen populære alternativer.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-114">If you prefer a graphical user interface (GUI) over a command-line interface (CLI), see [Software Freedom Conservancy's available GUI Clients page](https://git-scm.com/downloads/guis), [GitHub's GitHub Desktop](https://desktop.github.com/), or [Visual Studio Code](https://www.visualstudio.com/products/code-vs.aspx) for some popular options.</span></span>

<span data-ttu-id="9f0ea-115">Følg instruksjonene for den valgte klienten for installasjon og konfigurasjon.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-115">Follow the instructions for your chosen client for installation and configuration.</span></span>

<span data-ttu-id="9f0ea-116">I neste artikkel vil du [sette opp et lokalt Git-repositorium](get-started-setup-local.md).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-116">In the next article, you will [Set up a local Git repository](get-started-setup-local.md).</span></span>

   <span data-ttu-id="9f0ea-117">Flere Git-ressurser er tilgjengelig her: [Git-terminologi](https://help.github.com/articles/github-glossary) | [Grunnleggende om Git](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics) | [Lære Git og GitHub](https://help.github.com/articles/good-resources-for-learning-git-and-github/)</span><span class="sxs-lookup"><span data-stu-id="9f0ea-117">Additional Git resources are available here: [Git terminology](https://help.github.com/articles/github-glossary) | [Git basics](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics) | [Learning Git and GitHub](https://help.github.com/articles/good-resources-for-learning-git-and-github/)</span></span>

## <a name="understand-markdown-editors"></a><span data-ttu-id="9f0ea-118">Forstå Markdown-redigeringsprogrammer</span><span class="sxs-lookup"><span data-stu-id="9f0ea-118">Understand Markdown editors</span></span>

<span data-ttu-id="9f0ea-119">Markdown er et lett markeringsspråk som er både lett å lese og lett å lære.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-119">Markdown is a lightweight markup language that is both easy to read and easy to learn.</span></span> <span data-ttu-id="9f0ea-120">Derfor har det raskt blitt en bransjestandard.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-120">Therefore, it has rapidly become an industry standard.</span></span> <span data-ttu-id="9f0ea-121">Hvis du vil skrive artikler i Markdown, anbefaler vi at du først laster ned og installerer et Markdown-redigeringsprogram.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-121">To write articles in Markdown, we recommend that you first download and install a Markdown editor.</span></span>  <span data-ttu-id="9f0ea-122">[Visual Studio Code](https://code.visualstudio.com/) er det foretrukne verktøyet for redigering av Markdown hos Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-122">[Visual Studio Code](https://code.visualstudio.com/) is the preferred tool for editing Markdown at Microsoft.</span></span> <span data-ttu-id="9f0ea-123">[Atom](https://atom.io) er et annet populært verktøy for redigering av Markdown.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-123">[Atom](https://atom.io) is another popular tool for editing Markdown.</span></span>

<span data-ttu-id="9f0ea-124">Markdown-tekst lagres i filer med .md-utvidelse.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-124">Markdown text is saved into files with .md extension.</span></span>

<span data-ttu-id="9f0ea-125">Flere detaljer om hvordan de skriver med Markdown, inkludert grunnleggende om Markdown og funksjoner støttet av OPS-egendefinerte Markdown-utvidelser, dekkes i artikkelen [Slik bruker du Markdown](how-to-write-use-markdown.md).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-125">Additional details on how to write with Markdown, including Markdown basics and the features supported by OPS custom Markdown extensions, are covered later in the [How to use Markdown](how-to-write-use-markdown.md) article.</span></span>

## <a name="visual-studio-code"></a><span data-ttu-id="9f0ea-126">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9f0ea-126">Visual Studio Code</span></span>

<span data-ttu-id="9f0ea-127">[Visual Studio Code](https://code.visualstudio.com/), også kjent som VS Code, er et lett redigeringsprogram som fungerer på Windows, Linux på Mac.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-127">[Visual Studio Code](https://code.visualstudio.com/), also known as VS Code, is a lightweight editor that works on Windows, Linux, and Mac.</span></span> <span data-ttu-id="9f0ea-128">Det inkluderer git-integrasjon og støtte for utvidelser.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-128">It includes git integration, and support for extensions.</span></span>

<span data-ttu-id="9f0ea-129">Last ned og installer [VS Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-129">Download and install [VS Code](https://code.visualstudio.com/).</span></span> <span data-ttu-id="9f0ea-130">VS Codes hjemmeside skal finne operativsystemet på riktig måte.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-130">The VS Code home page should detect your operating system correctly.</span></span>

- [<span data-ttu-id="9f0ea-131">Windows</span><span class="sxs-lookup"><span data-stu-id="9f0ea-131">Windows</span></span>](https://code.visualstudio.com/docs/setup/windows)
- [<span data-ttu-id="9f0ea-132">Mac</span><span class="sxs-lookup"><span data-stu-id="9f0ea-132">Mac</span></span>](https://code.visualstudio.com/docs/setup/mac)
- [<span data-ttu-id="9f0ea-133">Linux</span><span class="sxs-lookup"><span data-stu-id="9f0ea-133">Linux</span></span>](https://code.visualstudio.com/docs/setup/linux)

> [!TIP]
> <span data-ttu-id="9f0ea-134">Hvis du vil starte VS Code og åpne den gjeldende mappen, kan du kjøre kommandoen `code .` i kommandolinjen eller bash shell.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-134">To launch VS Code and open the current folder, run the command `code .` in the command line or bash shell.</span></span> <span data-ttu-id="9f0ea-135">Hvis gjeldende mappe er en del av en lokal git-repo, vises github-integrasjon i Visual Studio Code automatisk.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-135">If the current folder is part of a local git repo, the github integration appears in Visual Studio Code automatically.</span></span>

## <a name="docs-authoring-pack"></a><span data-ttu-id="9f0ea-136">Docs Authoring Pack</span><span class="sxs-lookup"><span data-stu-id="9f0ea-136">Docs Authoring Pack</span></span>
<span data-ttu-id="9f0ea-137">Installer Docs Authoring Pack for Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-137">Install the Docs Authoring Pack for Visual Studio Code.</span></span> <span data-ttu-id="9f0ea-138">Dette utvidelsessettet inneholder grunnleggende opprettingsassistanse som kan hjelpe når du skriver Markdown, og en forhåndsvisning, slik at du kan se hvordan Markdown ser ut med stilen som brukes på nettstedet docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-138">This set of extensions includes basic authoring assistance for help when writing Markdown, and a preview feature, so that you can see what the Markdown looks like in the style of the docs.microsoft.com site.</span></span>

   <span data-ttu-id="9f0ea-139">Gå til [Markedsplass-siden](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) og velg **Installer**, eller bruk VS Code-vinduet til å søke i tilleggslisten etter `docsmsft.docs-authoring-pack`.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-139">Visit this [marketplace page](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) and select **Install**, or search for `docsmsft.docs-authoring-pack` in your extensions list in the VS Code window.</span></span> 

   <span data-ttu-id="9f0ea-140">Hvis du trenger Docs Authoring Pack, finner du den ved å trykke på ALT+M i VS Code.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-140">The Docs Authoring Pack is accessible by pressing Alt+M inside of VS Code.</span></span> <span data-ttu-id="9f0ea-141">Verktøylinjen er skjult som standard, men kan vises ved behov.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-141">The toolbar is hidden by default but can be shown.</span></span> <span data-ttu-id="9f0ea-142">Rediger VS Code-innstillingene (CTRL+KOMMA) og legg til `"markdown.showToolbar": true` for å vise verktøylinjen.</span><span class="sxs-lookup"><span data-stu-id="9f0ea-142">Edit the VS Code settings (Control+comma) and adding user setting `"markdown.showToolbar": true` to show the toolbar.</span></span>

   <span data-ttu-id="9f0ea-143">Hvis du vil ha mer informasjon, kan du se siden [Docs Authoring Pack](how-to-write-docs-auth-pack.md).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-143">For more information, see the [Docs Authoring Pack](how-to-write-docs-auth-pack.md) page.</span></span>


## <a name="next-steps"></a><span data-ttu-id="9f0ea-144">Neste trinn</span><span class="sxs-lookup"><span data-stu-id="9f0ea-144">Next steps</span></span>

<span data-ttu-id="9f0ea-145">Nå er du klar til å [Sette opp et lokalt Git-repositorium](get-started-setup-local.md).</span><span class="sxs-lookup"><span data-stu-id="9f0ea-145">Now you are ready to [Set up a local Git repository](get-started-setup-local.md).</span></span>
