---
title: Definer Git-repositoriet lokalt
description: Denne artikkelen gir veiledning for å opprette ditt lokale Git-repositorium og bidra til dokumentasjon, inkludert prosessen med forgrening og kloning.
author: jasonwhowell
ms.author: jasonh
manager: kfile
ms.date: 01/18/2018
ms.prod: non-product-specific
ms.topic: contributor-guide
ms.custom: external-contributor-guide
ms.openlocfilehash: f702d0d29ee7dc9c69cb26b79bf6283d91b6b6bc
ms.sourcegitcommit: 782b689882cce3ce07f5613763322989f2d0d63f
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 06/05/2018
ms.locfileid: "34469766"
---
# <a name="set-up-git-repository-locally-for-documentation"></a><span data-ttu-id="70003-103">Sett opp Git-repositorium lokalt for dokumentasjon</span><span class="sxs-lookup"><span data-stu-id="70003-103">Set up Git repository locally for documentation</span></span>

<span data-ttu-id="70003-104">Denne artikkelen beskriver fremgangsmåten for å sette opp et git-repositorium på den lokale maskinen din, med formål om å bidra til Microsoft-dokumentasjon.</span><span class="sxs-lookup"><span data-stu-id="70003-104">This article describes the steps to set up a git repository on your local machine, with the intent to contribute to Microsoft documentation.</span></span> <span data-ttu-id="70003-105">Bidragsytere kan bruke et lokalt klonet repositorium for å legge til nye artikler, foreta større redigeringer i eksisterende artikler eller endre grafikken.</span><span class="sxs-lookup"><span data-stu-id="70003-105">Contributors may use a locally cloned repository to add new articles, do major edits on existing articles, or change artwork.</span></span>

<span data-ttu-id="70003-106">Du kan kjøre disse aktivitetene for engangsoppsett for å bidra til å:</span><span class="sxs-lookup"><span data-stu-id="70003-106">You run these one-time setup activities to get started contributing:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="70003-107">Fastslå passende repositorium</span><span class="sxs-lookup"><span data-stu-id="70003-107">Determine the appropriate repository</span></span>
> * <span data-ttu-id="70003-108">Forgrene repositoriet til GitHub-kontoen din</span><span class="sxs-lookup"><span data-stu-id="70003-108">Fork the repository to your GitHub account</span></span>
> * <span data-ttu-id="70003-109">Velge en lokal mappe for klonede filer</span><span class="sxs-lookup"><span data-stu-id="70003-109">Choose a local folder for the cloned files</span></span>
> * <span data-ttu-id="70003-110">Klone repositoriet til den lokale maskinen</span><span class="sxs-lookup"><span data-stu-id="70003-110">Clone the repository to your local machine</span></span>
> * <span data-ttu-id="70003-111">Konfigurere oppstrøms ekstern verdi</span><span class="sxs-lookup"><span data-stu-id="70003-111">Configure the upstream remote value</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70003-112">Hvis du foretar små endringer i en artikkel, trenger du *ikke* å fullføre trinnene i denne artikkelen.</span><span class="sxs-lookup"><span data-stu-id="70003-112">If you're making only minor changes to an article, you *do not* need to complete the steps in this article.</span></span> <span data-ttu-id="70003-113">Du kan fortsette direkte til [arbeidsflyten for raske endringer](index.md#quick-edits-to-existing-documents).</span><span class="sxs-lookup"><span data-stu-id="70003-113">You can continue directly to the [quick changes workflow](index.md#quick-edits-to-existing-documents).</span></span>
>

## <a name="overview"></a><span data-ttu-id="70003-114">Oversikt</span><span class="sxs-lookup"><span data-stu-id="70003-114">Overview</span></span>

<span data-ttu-id="70003-115">For å bidra til webområdet for Microsofts dokumentasjonsområde, og redigere Markdown-filer lokalt ved kloning tilsvarende dokumentasjonsrepositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-115">To contribute to Microsoft's documentation site, you can make and edit Markdown files locally by cloning the corresponding documentation repository.</span></span> <span data-ttu-id="70003-116">Microsoft krever at du forgrener det passende repositoriet til githu- kontoen din, slik at du har lese-/skrive-tillatelser der for å lagre de foreslåtte endringene dine.</span><span class="sxs-lookup"><span data-stu-id="70003-116">Microsoft requires you to fork the appropriate repository into your own github account, so that you have read/write permissions there to store your proposed changes.</span></span> <span data-ttu-id="70003-117">Du kan deretter bruke pull-forespørsler for å slå sammen endringene i et skrivebeskyttet sentralt delt repositorium.</span><span class="sxs-lookup"><span data-stu-id="70003-117">Then you use pull requests to merge changes into the read-only central shared repository.</span></span>

![GitHub Triangle](./media/git-and-github-initial-setup.png)

<span data-ttu-id="70003-119">Hvis GitHub er nytt for deg, kan du se følgende video for en konseptuell oversikt over prosessen med forgrening og kloning:</span><span class="sxs-lookup"><span data-stu-id="70003-119">If you're new to GitHub, watch the following video for a conceptual overview of the forking and cloning process:</span></span>

>[!VIDEO https://channel9.msdn.com/Blogs/CoolMoose/Git-Repository-Setup/player]

## <a name="determine-the-repository"></a><span data-ttu-id="70003-120">Fastslå repositoriet</span><span class="sxs-lookup"><span data-stu-id="70003-120">Determine the repository</span></span>

<span data-ttu-id="70003-121">Dokumentasjonen plassert på [docs.microsoft.com](https://docs.microsoft.com) ligger i flere forskjellige repositorier på [github.com](https://www.github.com).</span><span class="sxs-lookup"><span data-stu-id="70003-121">Documentation hosted at [docs.microsoft.com](https://docs.microsoft.com) resides in several different repositories at [github.com](https://www.github.com).</span></span>

1. <span data-ttu-id="70003-122">Hvis du er usikker på hvilket repositorium du skal bruke, går du til artikkelen på docs.microsoft.com ved hjelp av nettleseren din.</span><span class="sxs-lookup"><span data-stu-id="70003-122">If you are unsure of which repository to use, then visit the article on docs.microsoft.com using your web browser.</span></span> <span data-ttu-id="70003-123">Velg **Rediger**-koblingen (blyantikon) øverst til høyre i artikkelen.</span><span class="sxs-lookup"><span data-stu-id="70003-123">Select the **Edit** link (pencil icon) on the upper right of the article.</span></span>

   ![Klikk Rediger for å fastslå repo og filplassering.](media/index/edit-article.png)

2. <span data-ttu-id="70003-125">Denne koblingen tar deg til github.com-plasseringen for tilsvarende Markdown-fil i riktig repositorium.</span><span class="sxs-lookup"><span data-stu-id="70003-125">That link takes you to github.com location for the corresponding Markdown file in the appropriate repository.</span></span> <span data-ttu-id="70003-126">Noter ned URL-adressen for å vise navnet på repositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-126">Note the URL to view the repository name.</span></span>

   ![Legg merke til URL-adressen for å finne ut hvor repositoriet er plassert.](media/public-repo.png)

   <span data-ttu-id="70003-128">For eksempel er disse populære repositoriene tilgjengelige for offentlig bidrag:</span><span class="sxs-lookup"><span data-stu-id="70003-128">For example, these popular repositories are available for public contributions:</span></span>
   - <span data-ttu-id="70003-129">Azure-dokumentasjon [https://github.com/MicrosoftDocs/azure-docs](https://github.com/MicrosoftDocs/azure-docs)</span><span class="sxs-lookup"><span data-stu-id="70003-129">Azure documentation [https://github.com/MicrosoftDocs/azure-docs](https://github.com/MicrosoftDocs/azure-docs)</span></span>
   - <span data-ttu-id="70003-130">Dokumentasjon for SQL-server [https://github.com/MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs)</span><span class="sxs-lookup"><span data-stu-id="70003-130">SQL Server documentation [https://github.com/MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs)</span></span>
   - <span data-ttu-id="70003-131">Visual Studio-dokumentasjon [https://github.com/MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs)</span><span class="sxs-lookup"><span data-stu-id="70003-131">Visual Studio documentation [https://github.com/MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs)</span></span>
   - <span data-ttu-id="70003-132">.NET-dokumentasjon [https://github.com/dotnet/docs](https://github.com/dotnet/docs)</span><span class="sxs-lookup"><span data-stu-id="70003-132">.NET Documentation [https://github.com/dotnet/docs](https://github.com/dotnet/docs)</span></span>
   - <span data-ttu-id="70003-133">Azure .net SDK-dokumentasjon [https://github.com/azure/azure-docs-sdk-dotnet](https://github.com/azure/azure-docs-sdk-dotnet)</span><span class="sxs-lookup"><span data-stu-id="70003-133">Azure .Net SDK documentation [https://github.com/azure/azure-docs-sdk-dotnet](https://github.com/azure/azure-docs-sdk-dotnet)</span></span>

## <a name="fork-the-repository"></a><span data-ttu-id="70003-134">Forgren repositoriet</span><span class="sxs-lookup"><span data-stu-id="70003-134">Fork the repository</span></span>
<span data-ttu-id="70003-135">Bruk riktig repositorium til å opprette en forgrening av repositoriet til GitHub-kontoen ved hjelp av webområdet GitHub.</span><span class="sxs-lookup"><span data-stu-id="70003-135">Using the appropriate repository, create a fork of the repository into your own GitHub account by using the GitHub website.</span></span>

<span data-ttu-id="70003-136">Det kreves en personlig forgrening siden alle repositorier for hoveddokumentasjon gir lesetilgang, noe som betyr at du ikke kan foreta direkte innholdsendringer i repositoriene.</span><span class="sxs-lookup"><span data-stu-id="70003-136">A personal fork is required since all main documentation repositories provide read-only access, which means you cannot make changes directly on content in the repositories.</span></span> <span data-ttu-id="70003-137">Hvis du vil foreta endringer, må du sende en [pull-forespørsel](git-github-fundamentals.md#pull-requests) fra forgreningen din til hovedrepositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-137">To make changes, you must submit a [pull request](git-github-fundamentals.md#pull-requests) from your fork into the main repository.</span></span> <span data-ttu-id="70003-138">For å forenkle denne prosessen trenger du først din egen kopi av repositoriet, hvor du har skrivetilgang.</span><span class="sxs-lookup"><span data-stu-id="70003-138">To facilitate this process, you first need your own copy of the repository, in which you have write access.</span></span> <span data-ttu-id="70003-139">En GitHub *-forgrening* fungerer til dette.</span><span class="sxs-lookup"><span data-stu-id="70003-139">A GitHub *fork* serves that purpose.</span></span>

1. <span data-ttu-id="70003-140">Gå hovedrepositoriets GitHub-side og klikk på **Forgrening** -knappen øverst til høyre.</span><span class="sxs-lookup"><span data-stu-id="70003-140">Go to the main repository's GitHub page and click the **Fork** button on the upper right.</span></span>

   ![Eksempel på GitHub-profil](./media/contribute-get-started-setup-local/fork.png)

2. <span data-ttu-id="70003-142">Hvis du blir bedt om det, velger du GitHub-kontoflisen som mål der forgrening skal opprettes.</span><span class="sxs-lookup"><span data-stu-id="70003-142">If you are prompted, select your GitHub account tile as the destination where the fork should be created.</span></span> <span data-ttu-id="70003-143">Denne ledeteksten oppretter en kopi av repositoriet i GitHub-kontoen din, kjent som en forgrening.</span><span class="sxs-lookup"><span data-stu-id="70003-143">This prompt creates a copy of the repository within your GitHub account, known as a fork.</span></span>

## <a name="choose-a-local-folder"></a><span data-ttu-id="70003-144">Velg en lokal mappe</span><span class="sxs-lookup"><span data-stu-id="70003-144">Choose a local folder</span></span>
<span data-ttu-id="70003-145">Lag en lokal mappe for å lagre en kopi av repositoriet lokalt.</span><span class="sxs-lookup"><span data-stu-id="70003-145">Make a local folder to hold a copy of the repository locally.</span></span> <span data-ttu-id="70003-146">Noen av repositoriene kan være store; opptil 5 GB for azure-dokumenter, for eksempel.</span><span class="sxs-lookup"><span data-stu-id="70003-146">Some of the repositories can be large; up to 5 GB for azure-docs for example.</span></span> <span data-ttu-id="70003-147">Velg en plassering med tilgjengelig diskplass.</span><span class="sxs-lookup"><span data-stu-id="70003-147">Choose a location with available disk space.</span></span>

1. <span data-ttu-id="70003-148">Velg et mappenavn som er enkelt å huske og skriv inn.</span><span class="sxs-lookup"><span data-stu-id="70003-148">Choose a folder name should be easy for you to remember and type.</span></span> <span data-ttu-id="70003-149">Vurder for eksempel en rotmappe `C:\docs\` eller lag en mappe i brukerprofilkatalogen `~/Documents/docs/`</span><span class="sxs-lookup"><span data-stu-id="70003-149">For example, consider a root folder `C:\docs\` or make a folder in your user profile directory `~/Documents/docs/`</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="70003-150">Unngå å velge en lokal mappebane som er nestet i en annen mappeplassering for Git-repositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-150">Avoid choosing a local folder path that is nested inside of another git repository folder location.</span></span> <span data-ttu-id="70003-151">Selv om det er akseptabelt å lagre Git-klonede mapper ved siden av hverandre, forårsaker nesting av Git-mapper inne i hverandre feil for filsporingen.</span><span class="sxs-lookup"><span data-stu-id="70003-151">While it is acceptable to store the git cloned folders adjacent to each other, nesting git folders inside one another causes errors for the file tracking.</span></span>

2. <span data-ttu-id="70003-152">Start Git Bash</span><span class="sxs-lookup"><span data-stu-id="70003-152">Launch Git Bash</span></span>

   ![Start Git Bash](./media/contribute-get-started-setup-local/gitbash-start.png)

   <span data-ttu-id="70003-154">Standardplasseringen som Git Bash starter i er vanligvis startkatalogen (~) eller `/c/users/<Windows-user-account>/` på Windows OS.</span><span class="sxs-lookup"><span data-stu-id="70003-154">The default location that Git Bash starts in is typically the home directory (~) or `/c/users/<Windows-user-account>/` on Windows OS.</span></span>

   <span data-ttu-id="70003-155">For å fastslå gjeldende katalog skriver du inn `pwd` ved ledeteksten $.</span><span class="sxs-lookup"><span data-stu-id="70003-155">To determine the current directory, type `pwd` at the $ prompt.</span></span> 

3. <span data-ttu-id="70003-156">Endre mappe (cd) til mappen du opprettet for å være vert lokalt i repositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-156">Change directory (cd) into the folder that you created for hosting the repository locally.</span></span> <span data-ttu-id="70003-157">Merk at Git Bash bruker Linux-konvensjonen til vanlige skråstreker i stedet for omvendte skråstreker for mappebaner.</span><span class="sxs-lookup"><span data-stu-id="70003-157">Note that Git Bash uses Linux convention of forward-slashes instead of back-slashes for folder paths.</span></span>

   <span data-ttu-id="70003-158">For eksempel, `cd /c/docs/ ` eller `cd ~/Documents/docs/`</span><span class="sxs-lookup"><span data-stu-id="70003-158">For example, `cd /c/docs/ ` or `cd ~/Documents/docs/`</span></span>

## <a name="create-a-local-clone"></a><span data-ttu-id="70003-159">Opprett en lokal klone</span><span class="sxs-lookup"><span data-stu-id="70003-159">Create a local clone</span></span>

<span data-ttu-id="70003-160">Ved hjelp av Git Bash kan du forberede kjøring av **klone**-kommando for å trekke en kopi av et repositorium (forgreningen) til enheten i gjeldende katalog.</span><span class="sxs-lookup"><span data-stu-id="70003-160">Using Git Bash, prepare to run the **clone** command to pull a copy of a repository (your fork) down to your device on the current directory.</span></span> 

### <a name="authenticate-by-using-git-credential-manager"></a><span data-ttu-id="70003-161">Godkjenne ved å Git Credential Manager</span><span class="sxs-lookup"><span data-stu-id="70003-161">Authenticate by using Git Credential Manager</span></span>
<span data-ttu-id="70003-162">Hvis du har installert den nyeste versjonen av Git for Windows og godtatt standardinstallasjonen, er Git Credential Manager aktivert som standard.</span><span class="sxs-lookup"><span data-stu-id="70003-162">If you installed the latest version of Git for Windows and accepted the default installation, Git Credential Manager is enabled by default.</span></span> <span data-ttu-id="70003-163">Git Credential Manager gjør godkjenning mye enklere, fordi du ikke trenger å huske ditt personlige tilgangstoken når du gjenoppretter godkjente tilkoblinger og eksterne med GitHub.</span><span class="sxs-lookup"><span data-stu-id="70003-163">Git Credential Manager makes authentication much easier, because you don't need to recall your personal access token when re-establishing authenticated connections and remotes with GitHub.</span></span>

1. <span data-ttu-id="70003-164">Kjør **klone**-kommandoen ved å oppgi navnet på repositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-164">Run the **clone** command, by providing the repository name.</span></span> <span data-ttu-id="70003-165">Klonenedlastinger (klone) av forgrenet på repositorium på den lokale datamaskinen.</span><span class="sxs-lookup"><span data-stu-id="70003-165">Cloning downloads (clone) the forked repository on your local computer.</span></span> 

    > [!Tip]
    > <span data-ttu-id="70003-166">Du kan få forgrenet GitHub URL-adresse for klonekommandoen fra **klone eller nedlastings**-knappen i GitHub-brukergrensesnittet:</span><span class="sxs-lookup"><span data-stu-id="70003-166">You can get your fork's GitHub URL for the clone command from the **Clone or download** button in the GitHub UI:</span></span>
    >
    > ![Klon eller last ned](./media/contribute-get-started-setup-local/clone-or-download.png)

    <span data-ttu-id="70003-168">Husk å angi banen til *forgreningen* under kloneprosessen, ikke hovedrepositoriet som du opprettet forgreningen fra.</span><span class="sxs-lookup"><span data-stu-id="70003-168">Be sure to specify the path to *your fork* during the cloning process, not the main repository from which you created the fork.</span></span> <span data-ttu-id="70003-169">Ellers kan du ikke bidra med endringer.</span><span class="sxs-lookup"><span data-stu-id="70003-169">Otherwise, you cannot contribute changes.</span></span> <span data-ttu-id="70003-170">Din forgrening er referert gjennom din personlige GitHub-brukerkonto, slik som `github.com/<github-username>/<repo>`.</span><span class="sxs-lookup"><span data-stu-id="70003-170">Your fork is referenced through your personal GitHub user account, such as `github.com/<github-username>/<repo>`.</span></span>

    ```bash
    git clone https://github.com/<github-username>/<repo>.git
    ```

    <span data-ttu-id="70003-171">Klonekommandoen bør se ut som dette eksempelet:</span><span class="sxs-lookup"><span data-stu-id="70003-171">Your clone command should look similar to this example:</span></span>

    ```bash
    git clone https://github.com/smithj/azure-docs.git
    ```

2. <span data-ttu-id="70003-172">Når du blir bedt om det, må du angi din GitHub-legitimasjon.</span><span class="sxs-lookup"><span data-stu-id="70003-172">When you're prompted, enter your GitHub credentials.</span></span>

    ![GitHub-pålogging](./media/contribute-get-started-setup-local/github-login.png)

3. <span data-ttu-id="70003-174">Når du blir bedt om det, kan du angi koden for to-faktor-godkjenning.</span><span class="sxs-lookup"><span data-stu-id="70003-174">When you're prompted, enter your two-factor authentication code.</span></span>

    ![GitHub to-faktor-godkjenning](./media/contribute-get-started-setup-local/github-2fa.png)

    > [!Note]
    > <span data-ttu-id="70003-176">Legitimasjonen lagres og brukes til å godkjenne fremtidige GitHub-forespørsler.</span><span class="sxs-lookup"><span data-stu-id="70003-176">Your credentials will be saved and used to authenticate future GitHub requests.</span></span> <span data-ttu-id="70003-177">Du trenger bare å gjøre denne godkjenningen én gang per datamaskin.</span><span class="sxs-lookup"><span data-stu-id="70003-177">You only need to do this authentication once per computer.</span></span> 

4. <span data-ttu-id="70003-178">Klone-kommandoen kjøres, og laster ned en kopi av repositoriumfilene fra din forgrening til en ny mappe på den lokale disken.</span><span class="sxs-lookup"><span data-stu-id="70003-178">The clone command runs and downloads a copy of the repository files from your fork into a new folder on the local disk.</span></span> <span data-ttu-id="70003-179">En ny mappe lagres i den nåværende mappen.</span><span class="sxs-lookup"><span data-stu-id="70003-179">A new folder is made within the current folder.</span></span> <span data-ttu-id="70003-180">Det kan ta noen minutter, avhengig av størrelsen på repositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-180">It may take a few minutes, depending on the repository size.</span></span> <span data-ttu-id="70003-181">Du kan utforske mappen for å se strukturen når den er ferdig.</span><span class="sxs-lookup"><span data-stu-id="70003-181">You can explore the folder to see the structure once it is finished.</span></span>

## <a name="configure-remote-upstream"></a><span data-ttu-id="70003-182">Konfigurer ekstern oppstrøms</span><span class="sxs-lookup"><span data-stu-id="70003-182">Configure remote upstream</span></span>
<span data-ttu-id="70003-183">Etter kloning av repositoriet, konfigurerer du en skrivebeskyttet tilkobling til hovedrepositoriet kalt **oppstrøms**.</span><span class="sxs-lookup"><span data-stu-id="70003-183">After cloning the repository, set up a read-only remote connection to the main repository named **upstream**.</span></span> <span data-ttu-id="70003-184">Du bruker oppstrøms URL-adressen til å synkronisere det lokale repositoriet med de siste endringene som er foretatt av andre.</span><span class="sxs-lookup"><span data-stu-id="70003-184">You use the upstream URL to keep your local repository in sync with the latest changes made by others.</span></span> <span data-ttu-id="70003-185">Kommando **git ekstern** brukes til å angi konfigurasjonsverdien.</span><span class="sxs-lookup"><span data-stu-id="70003-185">The **git remote** command is used to set the configuration value.</span></span> <span data-ttu-id="70003-186">Du bruker **hent**-kommandoen for å oppdatere greninfo fra oppstrøms-repositoriet.</span><span class="sxs-lookup"><span data-stu-id="70003-186">You use the **fetch** command to refresh the branch info from the upstream repository.</span></span>

1. <span data-ttu-id="70003-187">Hvis du bruker **Git Credential Manager**, bruker du følgende kommandoer.</span><span class="sxs-lookup"><span data-stu-id="70003-187">If you're using **Git Credential Manager**, use the following commands.</span></span> <span data-ttu-id="70003-188">Erstatt \<repo-\> og \<organisasjons\>-plassholdere.</span><span class="sxs-lookup"><span data-stu-id="70003-188">Replace the \<repo\> and \<organization\> placeholders.</span></span>
   ```bash
   cd <repo>
   git remote add upstream https://github.com/<organization>/<repo>.git
   git fetch upstream
   ```

2. <span data-ttu-id="70003-189">Vis konfigurerte verdier og bekreft at nettadresser er korrekte.</span><span class="sxs-lookup"><span data-stu-id="70003-189">View the configured values and confirm the URLs are correct.</span></span> <span data-ttu-id="70003-190">Kontroller at **opprinnelige** URL-adresser peker mot din personlige forgrening.</span><span class="sxs-lookup"><span data-stu-id="70003-190">Ensure the **origin** URLs point to your personal fork.</span></span> <span data-ttu-id="70003-191">Forsikre deg om at **oppstrøms** URL-adresser peker mot hovedrepositoriet, som MicrosoftDocs eller Azure.</span><span class="sxs-lookup"><span data-stu-id="70003-191">Ensure the **upstream** URLs point to the main repository, such as MicrosoftDocs or Azure.</span></span> 
   ```bash
   git remote -v 
   ```

   <span data-ttu-id="70003-192">Eksempel på eksterne utdata vises.</span><span class="sxs-lookup"><span data-stu-id="70003-192">Example remote output is shown.</span></span> <span data-ttu-id="70003-193">En fiktiv Git-konto med navnet MyGitAccount er konfigurert med et personlig tilgangstoken for å få tilgang til repo azure-dokumenter:</span><span class="sxs-lookup"><span data-stu-id="70003-193">A fictitious git account named MyGitAccount is configured with a personal access token to access the repo azure-docs:</span></span>
   ```output
   origin  https://github.com/MyGitAccount/azure-docs.git (fetch)
   origin  https://github.com/MyGitAccount/azure-docs.git(push)
   upstream        https://github.com/MicrosoftDocs/azure-docs.git (fetch)
   upstream        https://github.com/MicrosoftDocs/azure-docs.git (push)
   ```

3. <span data-ttu-id="70003-194">Hvis du har gjort en feil, kan du fjerne den eksterne verdien.</span><span class="sxs-lookup"><span data-stu-id="70003-194">If you made a mistake, you can remove the remote value.</span></span> <span data-ttu-id="70003-195">Hvis du vil fjerne oppstrømsverdien, kan du kjøre kommandoen `git remote remove upstream`.</span><span class="sxs-lookup"><span data-stu-id="70003-195">To remove the upstream value, run the command `git remote remove upstream`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="70003-196">Neste trinn</span><span class="sxs-lookup"><span data-stu-id="70003-196">Next steps</span></span>
- <span data-ttu-id="70003-197">Hvis du vil vite mer om å legge til og oppdatere innhold, går du videre til [GitHub-bidragsarbeidsflyt](how-to-write-workflows-major.md).</span><span class="sxs-lookup"><span data-stu-id="70003-197">To learn more about adding and updating content, continue to the [GitHub contribution workflow](how-to-write-workflows-major.md).</span></span>