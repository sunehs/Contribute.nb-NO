---
title: 'Hurtigstart: Angi og hent en hemmelighet fra Azure Key Vault | Microsoft Docs'
description: 'Hurtigstart: Angi og hent en hemmelighet fra Azure Key Vault'
services: key-vault
author: syntaxc4
manager: erifkin
ms.date: 07/24/2018
ms.author: cfowler
zone_pivot_groups: keyvault-languages
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 27ebd3e348fc231d8b82e6c17f282bd9ca4afb9f
ms.sourcegitcommit: 5e508a7ad2991632a38f302e4769b36e3bf37eb2
ms.translationtype: HT
ms.contentlocale: nb-NO
ms.lasthandoff: 08/30/2018
ms.locfileid: "43308828"
---
# <a name="quickstart-set-and-retrieve-a-secret-from-azure-key-vault"></a><span data-ttu-id="16d18-103">Hurtigstart: Angi og hent en hemmelighet fra Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="16d18-103">Quickstart: Set and retrieve a secret from Azure Key Vault</span></span>

<span data-ttu-id="16d18-104">Denne hurtigstarten viser deg hvordan du lagrer en hemmelighet i Key Vault og henter den med en nettapp.</span><span class="sxs-lookup"><span data-stu-id="16d18-104">This quickstart shows you how to store a secret in Key Vault and how to retrieve it using a Web app.</span></span> <span data-ttu-id="16d18-105">Du må kjøre denne på Azure for å se den hemmelige verdien.</span><span class="sxs-lookup"><span data-stu-id="16d18-105">To see the secret value you would have to run this on Azure.</span></span> <span data-ttu-id="16d18-106">Hurtigstarten bruker Node.js og administrerte tjenesteidentiteter (MSI-er)</span><span class="sxs-lookup"><span data-stu-id="16d18-106">The quickstart uses Node.js and Managed service identities (MSIs)</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="16d18-107">Opprett en Key Vault.</span><span class="sxs-lookup"><span data-stu-id="16d18-107">Create a Key Vault.</span></span>
> * <span data-ttu-id="16d18-108">Lagre en hemmelighet i Key Vault.</span><span class="sxs-lookup"><span data-stu-id="16d18-108">Store a secret in Key Vault.</span></span>
> * <span data-ttu-id="16d18-109">Hent en hemmelighet fra Key Vault.</span><span class="sxs-lookup"><span data-stu-id="16d18-109">Retrieve a secret from Key Vault.</span></span>
> * <span data-ttu-id="16d18-110">Opprett et Azure-nettprogram.</span><span class="sxs-lookup"><span data-stu-id="16d18-110">Create an Azure Web Application.</span></span>
> * <span data-ttu-id="16d18-111">[Aktiver administrerte tjenesteidentiteter](https://docs.microsoft.com/azure/active-directory/managed-service-identity/overview).</span><span class="sxs-lookup"><span data-stu-id="16d18-111">[Enable managed service identities](https://docs.microsoft.com/azure/active-directory/managed-service-identity/overview).</span></span>
> * <span data-ttu-id="16d18-112">Gi nødvendige tillatelser til nettprogrammet for å lese data fra Key Vault.</span><span class="sxs-lookup"><span data-stu-id="16d18-112">Grant the required permissions for the web application to read data from Key vault.</span></span>

<span data-ttu-id="16d18-113">Før du går videre, må du sørge for at du kjenner til de [grunnleggende konseptene](https://docs.microsoft.com/azure/key-vault/key-vault-whatis#basic-concepts).</span><span class="sxs-lookup"><span data-stu-id="16d18-113">Before you proceed make sure that you are familiar with the [basic concepts](https://docs.microsoft.com/azure/key-vault/key-vault-whatis#basic-concepts).</span></span>

> [!NOTE]
> <span data-ttu-id="16d18-114">For å kunne forstå hvorfor opplæringen nedenfor er beste fremgangsmåte må vi forstå visse konsepter.</span><span class="sxs-lookup"><span data-stu-id="16d18-114">To understand why the below tutorial is the best practice we need to understand a few concepts.</span></span> <span data-ttu-id="16d18-115">Key Vault er et sentralt repositorium for programmatisk lagring av hemmeligheter.</span><span class="sxs-lookup"><span data-stu-id="16d18-115">Key Vault is a central repository to store secrets programmatically.</span></span> <span data-ttu-id="16d18-116">Men for å kunne gjøre dette må programmer og brukere først godkjenne Key Vault, det vil si presentere en hemmelighet.</span><span class="sxs-lookup"><span data-stu-id="16d18-116">But to do so applications / users need to first authenticate to Key Vault i.e. present a secret.</span></span> <span data-ttu-id="16d18-117">For å kunne følge beste fremgangsmåte for sikkerhet må denne første hemmeligheten også roteres regelmessig.</span><span class="sxs-lookup"><span data-stu-id="16d18-117">To follow security best practices this first secret needs to be rotated periodically as well.</span></span> <span data-ttu-id="16d18-118">Men med [Administrert tjenesteidentitet](https://docs.microsoft.com/azure/active-directory/managed-service-identity/overview) får programmer som kjører i Azure en identitet som automatisk administreres av Azure.</span><span class="sxs-lookup"><span data-stu-id="16d18-118">But with [Managed Service Identity](https://docs.microsoft.com/azure/active-directory/managed-service-identity/overview) applications that run in Azure are given an identity which is automatically managed by Azure.</span></span> <span data-ttu-id="16d18-119">Dette hjelper for å løse **Hemmelig introduksjon-problemet** der brukere eller programmer kan følge beste fremgangsmåte, uten å måtte rotere den første hemmeligheten.</span><span class="sxs-lookup"><span data-stu-id="16d18-119">This helps solve the **Secret Introduction Problem** where users / applications can follow best practices and not have to worry about rotating the first secret</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16d18-120">Forutsetninger</span><span class="sxs-lookup"><span data-stu-id="16d18-120">Prerequisites</span></span>

<span data-ttu-id="16d18-121">::: zone pivot="nodejs"</span><span class="sxs-lookup"><span data-stu-id="16d18-121">::: zone pivot="nodejs"</span></span>
* <span data-ttu-id="16d18-122">[Node JS](https://nodejs.org/en/) ::: zone-end ::: zone pivot="dotnet"</span><span class="sxs-lookup"><span data-stu-id="16d18-122">[Node JS](https://nodejs.org/en/) ::: zone-end ::: zone pivot="dotnet"</span></span>
* <span data-ttu-id="16d18-123">[Visual Studio 2017 versjon 15.7.3 eller nyere](https://www.microsoft.com/net/download/windows) med følgende arbeidsbelastninger:</span><span class="sxs-lookup"><span data-stu-id="16d18-123">[Visual Studio 2017 version 15.7.3 or later](https://www.microsoft.com/net/download/windows) with the following workloads:</span></span>
  * <span data-ttu-id="16d18-124">ASP.NET og nettutvikling</span><span class="sxs-lookup"><span data-stu-id="16d18-124">ASP.NET and web development</span></span>
  * <span data-ttu-id="16d18-125">.NET Core-utvikling på tvers av plattformer</span><span class="sxs-lookup"><span data-stu-id="16d18-125">.NET Core cross-platform development</span></span>
* <span data-ttu-id="16d18-126">[.NET Core 2.1 SDK eller nyere](https://www.microsoft.com/net/download/windows) :::zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-126">[.NET Core 2.1 SDK or later](https://www.microsoft.com/net/download/windows) ::: zone-end</span></span>
* <span data-ttu-id="16d18-127">Git ([nedlasting](https://git-scm.com/downloads)).</span><span class="sxs-lookup"><span data-stu-id="16d18-127">Git ([download](https://git-scm.com/downloads)).</span></span>
* <span data-ttu-id="16d18-128">Et Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="16d18-128">An Azure subscription.</span></span> <span data-ttu-id="16d18-129">Hvis du ikke har et Azure-abonnement, oppretter du en [gratis konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) før du begynner.</span><span class="sxs-lookup"><span data-stu-id="16d18-129">If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.</span></span>
* <span data-ttu-id="16d18-130">[Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) versjon 2.0.4 eller nyere.</span><span class="sxs-lookup"><span data-stu-id="16d18-130">[Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) version 2.0.4 or later.</span></span> <span data-ttu-id="16d18-131">Dette er tilgjengelig for Windows, Mac og Linux.</span><span class="sxs-lookup"><span data-stu-id="16d18-131">This is available for Windows, Mac, and Linux.</span></span>

## <a name="login-to-azure"></a><span data-ttu-id="16d18-132">Azure-pålogging</span><span class="sxs-lookup"><span data-stu-id="16d18-132">Login to Azure</span></span>

<span data-ttu-id="16d18-133">Du kan logge deg på Azure med CLI ved å skrive inn:</span><span class="sxs-lookup"><span data-stu-id="16d18-133">To log in to Azure using the CLI, you can type:</span></span>

```azurecli
az login
```

## <a name="create-resource-group"></a><span data-ttu-id="16d18-134">Opprett ressursgruppe</span><span class="sxs-lookup"><span data-stu-id="16d18-134">Create resource group</span></span>

<span data-ttu-id="16d18-135">Opprett en ressursgruppe med kommandoen [az group create](/cli/azure/group#az-group-create).</span><span class="sxs-lookup"><span data-stu-id="16d18-135">Create a resource group with the [az group create](/cli/azure/group#az-group-create) command.</span></span> <span data-ttu-id="16d18-136">En Azure-ressursgruppe er en logisk beholder der Azure-ressurser distribueres og administreres.</span><span class="sxs-lookup"><span data-stu-id="16d18-136">An Azure resource group is a logical container into which Azure resources are deployed and managed.</span></span>

<span data-ttu-id="16d18-137">Velg navn på ressursgruppen, og fyll inn plassholderen.</span><span class="sxs-lookup"><span data-stu-id="16d18-137">Please select a Resource Group name and fill in the placeholder.</span></span>
<span data-ttu-id="16d18-138">Følgende eksempel oppretter en ressursgruppe som heter *<YourResourceGroupName>* i *eastus*-plasseringen.</span><span class="sxs-lookup"><span data-stu-id="16d18-138">The following example creates a resource group named *<YourResourceGroupName>* in the *eastus* location.</span></span>

```azurecli
# To list locations: az account list-locations --output table
az group create --name "<YourResourceGroupName>" --location "East US"
```

<span data-ttu-id="16d18-139">Ressursgruppen du nettopp har opprettet, brukes gjennom hele denne opplæringen.</span><span class="sxs-lookup"><span data-stu-id="16d18-139">The resource group you just created is used throughout this tutorial.</span></span>

## <a name="create-an-azure-key-vault"></a><span data-ttu-id="16d18-140">Opprett en Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="16d18-140">Create an Azure Key Vault</span></span>

<span data-ttu-id="16d18-141">Deretter oppretter du en Key Vault ved hjelp av ressursgruppen du opprettet i forrige trinn.</span><span class="sxs-lookup"><span data-stu-id="16d18-141">Next you create a Key Vault using the resource group created in the previous step.</span></span> <span data-ttu-id="16d18-142">Selv om ContosoKeyVault brukes som navnet på Key Vault gjennom hele denne artikkelen, må du bruke et unikt navn.</span><span class="sxs-lookup"><span data-stu-id="16d18-142">Although “ContosoKeyVault” is used as the name for the Key Vault throughout this article, you have to use a unique name.</span></span> <span data-ttu-id="16d18-143">Angi følgende informasjon:</span><span class="sxs-lookup"><span data-stu-id="16d18-143">Provide the following information:</span></span>

* <span data-ttu-id="16d18-144">Hvelvnavn – **Velg Key Vault-navn her**.</span><span class="sxs-lookup"><span data-stu-id="16d18-144">Vault name - **Select a Key Vault Name here**.</span></span>
* <span data-ttu-id="16d18-145">Ressursgruppenavn – **Velg et ressursgruppenavn her**.</span><span class="sxs-lookup"><span data-stu-id="16d18-145">Resource group name - **Select a Resource Group Name here**.</span></span>
* <span data-ttu-id="16d18-146">Plassering – **USA, øst**.</span><span class="sxs-lookup"><span data-stu-id="16d18-146">The location - **East US**.</span></span>

```azurecli
az keyvault create --name "<YourKeyVaultName>" --resource-group "<YourResourceGroupName>" --location "East US"
```

<span data-ttu-id="16d18-147">Nå er det bare Azure-kontoen din som er autorisert til å utføre operasjoner på dette nye hvelvet.</span><span class="sxs-lookup"><span data-stu-id="16d18-147">At this point, your Azure account is the only one authorized to perform any operations on this new vault.</span></span>

## <a name="add-a-secret-to-key-vault"></a><span data-ttu-id="16d18-148">Legg til en hemmelighet i nøkkelhvelvet</span><span class="sxs-lookup"><span data-stu-id="16d18-148">Add a secret to key vault</span></span>

<span data-ttu-id="16d18-149">Vi legger til en hemmelighet for å illustrere hvordan dette fungerer.</span><span class="sxs-lookup"><span data-stu-id="16d18-149">We're adding a secret to help illustrate how this works.</span></span> <span data-ttu-id="16d18-150">Du kan lagre en SQL-tilkoblingsstreng eller annen informasjon som må være sikker, men også tilgjengelig for programmet.</span><span class="sxs-lookup"><span data-stu-id="16d18-150">You could be storing a SQL connection string or any other information that you need to keep securely but make available to your application.</span></span> <span data-ttu-id="16d18-151">I denne opplæringen kalles passordet **AppSecret** og har verdien til **MySecret** lagret i passordet.</span><span class="sxs-lookup"><span data-stu-id="16d18-151">In this tutorial, the password will be called **AppSecret** and will store the value of **MySecret** in it.</span></span>

<span data-ttu-id="16d18-152">Skriv inn kommandoene nedenfor for å opprette en hemmelighet i Key Vault som kalles **AppSecret**, og som lagrer verdien **MySecret**:</span><span class="sxs-lookup"><span data-stu-id="16d18-152">Type the commands below to create a secret in Key Vault called **AppSecret** that will store the value **MySecret**:</span></span>

```azurecli
az keyvault secret set --vault-name "<YourKeyVaultName>" --name "AppSecret" --value "MySecret"
```

<span data-ttu-id="16d18-153">Du viser verdien i hemmeligheten som ren tekst, slik:</span><span class="sxs-lookup"><span data-stu-id="16d18-153">To view the value contained in the secret as plain text:</span></span>

```azurecli
az keyvault secret show --name "AppSecret" --vault-name "<YourKeyVaultName>"
```

<span data-ttu-id="16d18-154">Denne kommandoen viser den hemmelige informasjonen, inkludert URI-en.</span><span class="sxs-lookup"><span data-stu-id="16d18-154">This command shows the secret information including the URI.</span></span> <span data-ttu-id="16d18-155">Når du har fullført disse trinnene, skal du ha en URI til en hemmelighet i en Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="16d18-155">After completing these steps, you should have a URI to a secret in an Azure Key Vault.</span></span> <span data-ttu-id="16d18-156">Skriv ned denne informasjonen.</span><span class="sxs-lookup"><span data-stu-id="16d18-156">Write this information down.</span></span> <span data-ttu-id="16d18-157">Du trenger den i et senere trinn.</span><span class="sxs-lookup"><span data-stu-id="16d18-157">You need it in a later step.</span></span>

## <a name="clone-the-repo"></a><span data-ttu-id="16d18-158">Klon repositoriet</span><span class="sxs-lookup"><span data-stu-id="16d18-158">Clone the Repo</span></span>

<span data-ttu-id="16d18-159">Klon repositoriet, slik at du kan lage en lokal kopi der du kan redigere kilden ved å kjøre følgende kommando:</span><span class="sxs-lookup"><span data-stu-id="16d18-159">Clone the repo in order to make a local copy for you to edit the source by running the following command:</span></span>

```bash
git clone https://github.com/Azure-Samples/key-vault-node-quickstart.git
```

<span data-ttu-id="16d18-160">::: zone pivot="nodejs"</span><span class="sxs-lookup"><span data-stu-id="16d18-160">::: zone pivot="nodejs"</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="16d18-161">Installer avhengigheter</span><span class="sxs-lookup"><span data-stu-id="16d18-161">Install dependencies</span></span>

<span data-ttu-id="16d18-162">Her installerer vi avhengighetene.</span><span class="sxs-lookup"><span data-stu-id="16d18-162">Here we install the dependencies.</span></span> <span data-ttu-id="16d18-163">Kjør følgende kommandoer cd-key-vault-node-quickstart npm install</span><span class="sxs-lookup"><span data-stu-id="16d18-163">Run the following commands cd key-vault-node-quickstart npm install</span></span>

<span data-ttu-id="16d18-164">Dette prosjektet brukte 2 node-moduler:</span><span class="sxs-lookup"><span data-stu-id="16d18-164">This project used 2 node modules:</span></span>

* [<span data-ttu-id="16d18-165">ms-rest-azure</span><span class="sxs-lookup"><span data-stu-id="16d18-165">ms-rest-azure</span></span>](https://www.npmjs.com/package/ms-rest-azure) 
* [<span data-ttu-id="16d18-166">azure-keyvault</span><span class="sxs-lookup"><span data-stu-id="16d18-166">azure-keyvault</span></span>](https://www.npmjs.com/package/azure-keyvault)

## <a name="publish-the-web-application-to-azure"></a><span data-ttu-id="16d18-167">Publiser nettprogrammet i Azure</span><span class="sxs-lookup"><span data-stu-id="16d18-167">Publish the web application to Azure</span></span>

<span data-ttu-id="16d18-168">Nedenfor er de få trinnene vi må følge</span><span class="sxs-lookup"><span data-stu-id="16d18-168">Below are the few steps we need to do</span></span>

* <span data-ttu-id="16d18-169">Det første trinnet er å opprette en plan for [Azure App Service](https://azure.microsoft.com/services/app-service/).</span><span class="sxs-lookup"><span data-stu-id="16d18-169">The 1st step is to create a [Azure App Service](https://azure.microsoft.com/services/app-service/) Plan.</span></span> <span data-ttu-id="16d18-170">Du kan lagre flere nettapper i denne planen.</span><span class="sxs-lookup"><span data-stu-id="16d18-170">You can store multiple web apps in this plan.</span></span>

    ```azurecli
    az appservice plan create --name myAppServicePlan --resource-group myResourceGroup
    ```
* <span data-ttu-id="16d18-171">Deretter oppretter vi en nettapp.</span><span class="sxs-lookup"><span data-stu-id="16d18-171">Next we create a web app.</span></span> <span data-ttu-id="16d18-172">I følgende eksempel erstatter du <app_name> med et globalt unikt appnavn (gyldige tegn er a-z, 0–9, og -).</span><span class="sxs-lookup"><span data-stu-id="16d18-172">In the following example, replace <app_name> with a globally unique app name (valid characters are a-z, 0-9, and -).</span></span> <span data-ttu-id="16d18-173">Kjøretiden er angitt til NODE|6.9.</span><span class="sxs-lookup"><span data-stu-id="16d18-173">The runtime is set to NODE|6.9.</span></span> <span data-ttu-id="16d18-174">Du ser alle støttede kjøretider ved å kjøre az webapp list-kjøretider</span><span class="sxs-lookup"><span data-stu-id="16d18-174">To see all supported runtimes, run az webapp list-runtimes</span></span>

    ```azurecli
    az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name <app_name> --runtime "NODE|6.9" --deployment-local-git
    ```

    <span data-ttu-id="16d18-175">Når nettappen har blitt opprettet, viser Azure CLI utdata som ser ut som følgende eksempel:</span><span class="sxs-lookup"><span data-stu-id="16d18-175">When the web app has been created, the Azure CLI shows output similar to the following example:</span></span>

    ```json
    {
      "availabilityState": "Normal",
      "clientAffinityEnabled": true,
      "clientCertEnabled": false,
      "cloningInfo": null,
      "containerSize": 0,
      "dailyMemoryTimeQuota": 0,
      "defaultHostName": "<app_name>.azurewebsites.net",
      "enabled": true,
      "deploymentLocalGitUrl": "https://<username>@<app_name>.scm.azurewebsites.net/<app_name>.git"
      < JSON data removed for brevity. >
    }
    ```
    <span data-ttu-id="16d18-176">Bla gjennom nettappen som nylig er opprettet, og du skal kunne se en fungerende nettapp.</span><span class="sxs-lookup"><span data-stu-id="16d18-176">Browse to your newly created web app and you should see a functioning web app.</span></span> <span data-ttu-id="16d18-177">Erstatt <app_name> med et unikt appnavn.</span><span class="sxs-lookup"><span data-stu-id="16d18-177">Replace <app_name> with a unique app name.</span></span>

    ```text
    http://<app name>.azurewebsites.net
    ```
    <span data-ttu-id="16d18-178">Kommandoen over oppretter også en Git-aktivert app, som gjør at du kan distribuere i Azure fra den lokale git-en.</span><span class="sxs-lookup"><span data-stu-id="16d18-178">The above command also creates a Git-enabled app which allows you to deploy to azure from your local git.</span></span> 
    <span data-ttu-id="16d18-179">Den lokale git-en er konfigurert med nettadressen https://<username>@<app_name>.scm.azurewebsites.net/<app_name>.git</span><span class="sxs-lookup"><span data-stu-id="16d18-179">Local git is configured with url of 'https://<username>@<app_name>.scm.azurewebsites.net/<app_name>.git'</span></span>

* <span data-ttu-id="16d18-180">Opprett en distribusjonsbruker. Når forrige kommando er fullført, kan du legge til en ekstern Azure i det lokale Git-repositoriet.</span><span class="sxs-lookup"><span data-stu-id="16d18-180">Create a deployment user After the previous command is completed you can add add an Azure remote to your local Git repository.</span></span> <span data-ttu-id="16d18-181">Erstatt <url> med nettadressen til den eksterne Git-en som du fikk fra den aktiverte Git-en for appen.</span><span class="sxs-lookup"><span data-stu-id="16d18-181">Replace <url> with the URL of the Git remote that you got from Enable Git for your app.</span></span>

    ```bash
    git remote add azure <url>
    ```
    
<span data-ttu-id="16d18-182">::: zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-182">::: zone-end</span></span>

<span data-ttu-id="16d18-183">::: zone pivot="dotnet"</span><span class="sxs-lookup"><span data-stu-id="16d18-183">::: zone pivot="dotnet"</span></span>
## <a name="open-and-edit-the-solution"></a><span data-ttu-id="16d18-184">Åpne og rediger løsningen</span><span class="sxs-lookup"><span data-stu-id="16d18-184">Open and edit the solution</span></span>

<span data-ttu-id="16d18-185">Rediger program.cs-filen til å kjøre eksemplet med det bestemte nøkkelhvelvnavnet:</span><span class="sxs-lookup"><span data-stu-id="16d18-185">Edit the program.cs file to run the sample with your specific key vault name:</span></span>

1. <span data-ttu-id="16d18-186">Bla gjennom til mappen key-vault-dotnet-core-quickstart.</span><span class="sxs-lookup"><span data-stu-id="16d18-186">Browse to the folder key-vault-dotnet-core-quickstart.</span></span>
2. <span data-ttu-id="16d18-187">Åpne filen key-vault-dotnet-core-quickstart.sln i Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="16d18-187">Open the key-vault-dotnet-core-quickstart.sln file in Visual Studio 2017.</span></span>
3. <span data-ttu-id="16d18-188">Åpne Program.cs-filen, og oppdater plassholderen *YourKeyVaultName* med navnet på nøkkelhvelvet du opprettet tidligere.</span><span class="sxs-lookup"><span data-stu-id="16d18-188">Open the Program.cs file and update the placeholder *YourKeyVaultName* with the name of your key vault that you created earlier.</span></span>

<span data-ttu-id="16d18-189">Denne løsningen bruker [AppAuthentication](https://www.nuget.org/packages/Microsoft.Azure.Services.AppAuthentication) og [KeyVault](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) NuGet-biblioteker.</span><span class="sxs-lookup"><span data-stu-id="16d18-189">This solution uses [AppAuthentication](https://www.nuget.org/packages/Microsoft.Azure.Services.AppAuthentication) and [KeyVault](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) NuGet libraries.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="16d18-190">Kjør appen</span><span class="sxs-lookup"><span data-stu-id="16d18-190">Run the app</span></span>

<span data-ttu-id="16d18-191">Velg **Feilsøk** > **Start** uten feilsøking fra hovedmenyen i Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="16d18-191">From the main menu of Visual Studio 2017, select **Debug** > **Start** without debugging.</span></span> <span data-ttu-id="16d18-192">Når nettleseren vises, går du til **Om**-siden.</span><span class="sxs-lookup"><span data-stu-id="16d18-192">When the browser appears, go to the **About** page.</span></span> <span data-ttu-id="16d18-193">Verdien for **AppSecret** vises.</span><span class="sxs-lookup"><span data-stu-id="16d18-193">The value for **AppSecret** is displayed.</span></span>

## <a name="publish-the-web-application-to-azure"></a><span data-ttu-id="16d18-194">Publiser nettprogrammet i Azure</span><span class="sxs-lookup"><span data-stu-id="16d18-194">Publish the web application to Azure</span></span>

<span data-ttu-id="16d18-195">Publiser denne appen i Azure for å se den live som en nettapp, og for å se at du kan hente den hemmelige verdien:</span><span class="sxs-lookup"><span data-stu-id="16d18-195">Publish this app to Azure to see it live as a web app, and to see that you can fetch the secret value:</span></span>

1. <span data-ttu-id="16d18-196">Velg prosjektet **key-vault-dotnet-core-quickstart** i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16d18-196">In Visual Studio, select the **key-vault-dotnet-core-quickstart** project.</span></span>
2. <span data-ttu-id="16d18-197">Velg **Publiser** > **Start**.</span><span class="sxs-lookup"><span data-stu-id="16d18-197">Select **Publish** > **Start**.</span></span>
3. <span data-ttu-id="16d18-198">Opprett en ny **App Service**, og velg deretter **Publiser**.</span><span class="sxs-lookup"><span data-stu-id="16d18-198">Create a new **App Service**, and then select **Publish**.</span></span>
4. <span data-ttu-id="16d18-199">Endre appnavnet til **keyvaultdotnetcorequickstart**.</span><span class="sxs-lookup"><span data-stu-id="16d18-199">Change the app name to **keyvaultdotnetcorequickstart**.</span></span>
5. <span data-ttu-id="16d18-200">Velg **Opprett**.</span><span class="sxs-lookup"><span data-stu-id="16d18-200">Select **Create**.</span></span>

>[!VIDEO https://sec.ch9.ms/ch9/e93d/a6ac417f-2e63-4125-a37a-8f34bf0fe93d/KeyVault_high.mp4]
<span data-ttu-id="16d18-201">::: zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-201">::: zone-end</span></span>

## <a name="enable-managed-service-identities"></a><span data-ttu-id="16d18-202">Aktiver administrerte tjenesteidentiteter</span><span class="sxs-lookup"><span data-stu-id="16d18-202">Enable managed service identities</span></span>

<span data-ttu-id="16d18-203">Med Azure Key Vault kan du lagre legitimasjon og andre nøkler og hemmeligheter på en sikker måte, men koden må godkjenne Azure Key Vault for å hente dem.</span><span class="sxs-lookup"><span data-stu-id="16d18-203">Azure Key Vault provides a way to securely store credentials and other keys and secrets, but your code needs to authenticate to Azure Key Vault to retrieve them.</span></span> <span data-ttu-id="16d18-204">Administrert tjenesteidentitet gjør dette enklere ved å gi Azure-tjenester en automatisk administrert identitet i Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="16d18-204">Managed Service Identity makes this easier by giving Azure services an automatically managed identity in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="16d18-205">Du kan bruke denne identiteten til å godkjenne alle tjenester som støtter Azure AD-godkjenning, inkludert Key Vault, uten å ha legitimasjon i koden.</span><span class="sxs-lookup"><span data-stu-id="16d18-205">You can use this identity to authenticate to any service that supports Azure AD authentication, including Key Vault, without having any credentials in your code.</span></span>

1. <span data-ttu-id="16d18-206">Gå tilbake til Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="16d18-206">Return to the Azure CLI.</span></span>
2. <span data-ttu-id="16d18-207">Kjør assign-identity-kommandoen for å opprette identiteten for dette programmet:</span><span class="sxs-lookup"><span data-stu-id="16d18-207">Run the assign-identity command to create the identity for this application:</span></span>

   ```azurecli
   az webapp identity assign --name "keyvaultdotnetcorequickstart" --resource-group "<YourResourceGroupName>"
   ```

>[!NOTE]
><span data-ttu-id="16d18-208">Kommandoen i denne prosedyren tilsvarer det å gå til portalen og sette **Administrert tjenesteidentitet** til **På** i egenskapene for nettprogrammet.</span><span class="sxs-lookup"><span data-stu-id="16d18-208">The command in this procedure is the equivalent of going to the portal and switching **Managed service identity** to **On** in the web application properties.</span></span>

## <a name="assign-permissions-to-your-application-to-read-secrets-from-key-vault"></a><span data-ttu-id="16d18-209">Tilordne tillatelser til programmet for å lese hemmeligheter fra Key Vault</span><span class="sxs-lookup"><span data-stu-id="16d18-209">Assign permissions to your application to read secrets from Key Vault</span></span>

<span data-ttu-id="16d18-210">Legg merke til utdataene når du publiserer programmet i Azure.</span><span class="sxs-lookup"><span data-stu-id="16d18-210">Make a note of the output when you publish the application to Azure.</span></span> <span data-ttu-id="16d18-211">Det skal være i følgende format:</span><span class="sxs-lookup"><span data-stu-id="16d18-211">It should be of the format:</span></span>

```json
        {
          "principalId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
          "tenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
          "type": "SystemAssigned"
        }
```

<span data-ttu-id="16d18-212">Deretter kjører du denne kommandoen ved hjelp av navnet på nøkkelhvelvet og verdien til **PrincipalId**:</span><span class="sxs-lookup"><span data-stu-id="16d18-212">Then, run this command by using the name of your key vault and the value of **PrincipalId**:</span></span>

```azurecli
az keyvault set-policy --name '<YourKeyVaultName>' --object-id <PrincipalId> --secret-permissions get
```

<span data-ttu-id="16d18-213">::: zone pivot="nodejs"</span><span class="sxs-lookup"><span data-stu-id="16d18-213">::: zone pivot="nodejs"</span></span>
## <a name="deploy-the-node-app-to-azure-and-retrieve-the-secret-value"></a><span data-ttu-id="16d18-214">Distribuer Node-appen i Azure, og hent den hemmelige verdien</span><span class="sxs-lookup"><span data-stu-id="16d18-214">Deploy the Node App to Azure and retrieve the secret value</span></span>

<span data-ttu-id="16d18-215">Nå som alt er angitt.</span><span class="sxs-lookup"><span data-stu-id="16d18-215">Now that everything is set.</span></span> <span data-ttu-id="16d18-216">Kjør følgende kommando for å distribuere appen i Azure</span><span class="sxs-lookup"><span data-stu-id="16d18-216">Run the following command to deploy the app to Azure</span></span>

```bash
git push azure master
```

<span data-ttu-id="16d18-217">Etter dette, når du blar gjennom https://<app_name>.azurewebsites.net, ser du den hemmelige verdien.</span><span class="sxs-lookup"><span data-stu-id="16d18-217">After this when you browse https://<app_name>.azurewebsites.net you can see the secret value.</span></span>
<span data-ttu-id="16d18-218">Sørg for at du har erstattet navnet <YourKeyVaultName> med hvelvnavnet ::: zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-218">Make sure that you replaced the name <YourKeyVaultName> with your vault name</span></span>

<span data-ttu-id="16d18-219">::: zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-219">::: zone-end</span></span>

<span data-ttu-id="16d18-220">::: zone pivot="dotnet" Når du nå kjører programmet, skal du kunne se den hemmelige verdien som hentes.</span><span class="sxs-lookup"><span data-stu-id="16d18-220">::: zone pivot="dotnet" Now when you run the application, you should see your secret value retrieved.</span></span>
<span data-ttu-id="16d18-221">::: zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-221">::: zone-end</span></span>

## <a name="next-steps"></a><span data-ttu-id="16d18-222">Neste trinn</span><span class="sxs-lookup"><span data-stu-id="16d18-222">Next steps</span></span>

<span data-ttu-id="16d18-223">::: zone pivot="nodejs"</span><span class="sxs-lookup"><span data-stu-id="16d18-223">::: zone pivot="nodejs"</span></span>
* [<span data-ttu-id="16d18-224">Hjemmeside for Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="16d18-224">Azure Key Vault Home Page</span></span>](https://azure.microsoft.com/services/key-vault/)
* [<span data-ttu-id="16d18-225">Dokumentasjon for Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="16d18-225">Azure Key Vault Documentation</span></span>](https://docs.microsoft.com/azure/key-vault/)
* [<span data-ttu-id="16d18-226">Azure SDK for Node</span><span class="sxs-lookup"><span data-stu-id="16d18-226">Azure SDK For Node</span></span>](https://docs.microsoft.com/javascript/api/overview/azure/key-vault)
* <span data-ttu-id="16d18-227">[Azure REST-API-referanse](https://docs.microsoft.com/rest/api/keyvault/) ::: zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-227">[Azure REST API Reference](https://docs.microsoft.com/rest/api/keyvault/) ::: zone-end</span></span>

<span data-ttu-id="16d18-228">::: zone pivot="dotnet"</span><span class="sxs-lookup"><span data-stu-id="16d18-228">::: zone pivot="dotnet"</span></span>
* [<span data-ttu-id="16d18-229">Hjemmeside for Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="16d18-229">Azure Key Vault home page</span></span>](https://azure.microsoft.com/services/key-vault/)
* [<span data-ttu-id="16d18-230">Dokumentasjon for Azure Key Vault</span><span class="sxs-lookup"><span data-stu-id="16d18-230">Azure Key Vault documentation</span></span>](https://docs.microsoft.com/azure/key-vault/)
* [<span data-ttu-id="16d18-231">Azure SDK for .NET</span><span class="sxs-lookup"><span data-stu-id="16d18-231">Azure SDK For .NET</span></span>](https://github.com/Azure/azure-sdk-for-net)
* <span data-ttu-id="16d18-232">[Azure REST-API-referanse](https://docs.microsoft.com/rest/api/keyvault/) ::: zone-end</span><span class="sxs-lookup"><span data-stu-id="16d18-232">[Azure REST API reference](https://docs.microsoft.com/rest/api/keyvault/) ::: zone-end</span></span>
