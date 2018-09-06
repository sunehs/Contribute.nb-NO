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
# <a name="quickstart-set-and-retrieve-a-secret-from-azure-key-vault"></a>Hurtigstart: Angi og hent en hemmelighet fra Azure Key Vault

Denne hurtigstarten viser deg hvordan du lagrer en hemmelighet i Key Vault og henter den med en nettapp. Du må kjøre denne på Azure for å se den hemmelige verdien. Hurtigstarten bruker Node.js og administrerte tjenesteidentiteter (MSI-er)

> [!div class="checklist"]
> * Opprett en Key Vault.
> * Lagre en hemmelighet i Key Vault.
> * Hent en hemmelighet fra Key Vault.
> * Opprett et Azure-nettprogram.
> * [Aktiver administrerte tjenesteidentiteter](https://docs.microsoft.com/azure/active-directory/managed-service-identity/overview).
> * Gi nødvendige tillatelser til nettprogrammet for å lese data fra Key Vault.

Før du går videre, må du sørge for at du kjenner til de [grunnleggende konseptene](https://docs.microsoft.com/azure/key-vault/key-vault-whatis#basic-concepts).

> [!NOTE]
> For å kunne forstå hvorfor opplæringen nedenfor er beste fremgangsmåte må vi forstå visse konsepter. Key Vault er et sentralt repositorium for programmatisk lagring av hemmeligheter. Men for å kunne gjøre dette må programmer og brukere først godkjenne Key Vault, det vil si presentere en hemmelighet. For å kunne følge beste fremgangsmåte for sikkerhet må denne første hemmeligheten også roteres regelmessig. Men med [Administrert tjenesteidentitet](https://docs.microsoft.com/azure/active-directory/managed-service-identity/overview) får programmer som kjører i Azure en identitet som automatisk administreres av Azure. Dette hjelper for å løse **Hemmelig introduksjon-problemet** der brukere eller programmer kan følge beste fremgangsmåte, uten å måtte rotere den første hemmeligheten.

## <a name="prerequisites"></a>Forutsetninger

::: zone pivot="nodejs"
* [Node JS](https://nodejs.org/en/) ::: zone-end ::: zone pivot="dotnet"
* [Visual Studio 2017 versjon 15.7.3 eller nyere](https://www.microsoft.com/net/download/windows) med følgende arbeidsbelastninger:
  * ASP.NET og nettutvikling
  * .NET Core-utvikling på tvers av plattformer
* [.NET Core 2.1 SDK eller nyere](https://www.microsoft.com/net/download/windows) :::zone-end
* Git ([nedlasting](https://git-scm.com/downloads)).
* Et Azure-abonnement. Hvis du ikke har et Azure-abonnement, oppretter du en [gratis konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) før du begynner.
* [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) versjon 2.0.4 eller nyere. Dette er tilgjengelig for Windows, Mac og Linux.

## <a name="login-to-azure"></a>Azure-pålogging

Du kan logge deg på Azure med CLI ved å skrive inn:

```azurecli
az login
```

## <a name="create-resource-group"></a>Opprett ressursgruppe

Opprett en ressursgruppe med kommandoen [az group create](/cli/azure/group#az-group-create). En Azure-ressursgruppe er en logisk beholder der Azure-ressurser distribueres og administreres.

Velg navn på ressursgruppen, og fyll inn plassholderen.
Følgende eksempel oppretter en ressursgruppe som heter *<YourResourceGroupName>* i *eastus*-plasseringen.

```azurecli
# To list locations: az account list-locations --output table
az group create --name "<YourResourceGroupName>" --location "East US"
```

Ressursgruppen du nettopp har opprettet, brukes gjennom hele denne opplæringen.

## <a name="create-an-azure-key-vault"></a>Opprett en Azure Key Vault

Deretter oppretter du en Key Vault ved hjelp av ressursgruppen du opprettet i forrige trinn. Selv om ContosoKeyVault brukes som navnet på Key Vault gjennom hele denne artikkelen, må du bruke et unikt navn. Angi følgende informasjon:

* Hvelvnavn – **Velg Key Vault-navn her**.
* Ressursgruppenavn – **Velg et ressursgruppenavn her**.
* Plassering – **USA, øst**.

```azurecli
az keyvault create --name "<YourKeyVaultName>" --resource-group "<YourResourceGroupName>" --location "East US"
```

Nå er det bare Azure-kontoen din som er autorisert til å utføre operasjoner på dette nye hvelvet.

## <a name="add-a-secret-to-key-vault"></a>Legg til en hemmelighet i nøkkelhvelvet

Vi legger til en hemmelighet for å illustrere hvordan dette fungerer. Du kan lagre en SQL-tilkoblingsstreng eller annen informasjon som må være sikker, men også tilgjengelig for programmet. I denne opplæringen kalles passordet **AppSecret** og har verdien til **MySecret** lagret i passordet.

Skriv inn kommandoene nedenfor for å opprette en hemmelighet i Key Vault som kalles **AppSecret**, og som lagrer verdien **MySecret**:

```azurecli
az keyvault secret set --vault-name "<YourKeyVaultName>" --name "AppSecret" --value "MySecret"
```

Du viser verdien i hemmeligheten som ren tekst, slik:

```azurecli
az keyvault secret show --name "AppSecret" --vault-name "<YourKeyVaultName>"
```

Denne kommandoen viser den hemmelige informasjonen, inkludert URI-en. Når du har fullført disse trinnene, skal du ha en URI til en hemmelighet i en Azure Key Vault. Skriv ned denne informasjonen. Du trenger den i et senere trinn.

## <a name="clone-the-repo"></a>Klon repositoriet

Klon repositoriet, slik at du kan lage en lokal kopi der du kan redigere kilden ved å kjøre følgende kommando:

```bash
git clone https://github.com/Azure-Samples/key-vault-node-quickstart.git
```

::: zone pivot="nodejs"

## <a name="install-dependencies"></a>Installer avhengigheter

Her installerer vi avhengighetene. Kjør følgende kommandoer cd-key-vault-node-quickstart npm install

Dette prosjektet brukte 2 node-moduler:

* [ms-rest-azure](https://www.npmjs.com/package/ms-rest-azure) 
* [azure-keyvault](https://www.npmjs.com/package/azure-keyvault)

## <a name="publish-the-web-application-to-azure"></a>Publiser nettprogrammet i Azure

Nedenfor er de få trinnene vi må følge

* Det første trinnet er å opprette en plan for [Azure App Service](https://azure.microsoft.com/services/app-service/). Du kan lagre flere nettapper i denne planen.

    ```azurecli
    az appservice plan create --name myAppServicePlan --resource-group myResourceGroup
    ```
* Deretter oppretter vi en nettapp. I følgende eksempel erstatter du <app_name> med et globalt unikt appnavn (gyldige tegn er a-z, 0–9, og -). Kjøretiden er angitt til NODE|6.9. Du ser alle støttede kjøretider ved å kjøre az webapp list-kjøretider

    ```azurecli
    az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name <app_name> --runtime "NODE|6.9" --deployment-local-git
    ```

    Når nettappen har blitt opprettet, viser Azure CLI utdata som ser ut som følgende eksempel:

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
    Bla gjennom nettappen som nylig er opprettet, og du skal kunne se en fungerende nettapp. Erstatt <app_name> med et unikt appnavn.

    ```text
    http://<app name>.azurewebsites.net
    ```
    Kommandoen over oppretter også en Git-aktivert app, som gjør at du kan distribuere i Azure fra den lokale git-en. 
    Den lokale git-en er konfigurert med nettadressen https://<username>@<app_name>.scm.azurewebsites.net/<app_name>.git

* Opprett en distribusjonsbruker. Når forrige kommando er fullført, kan du legge til en ekstern Azure i det lokale Git-repositoriet. Erstatt <url> med nettadressen til den eksterne Git-en som du fikk fra den aktiverte Git-en for appen.

    ```bash
    git remote add azure <url>
    ```
    
::: zone-end

::: zone pivot="dotnet"
## <a name="open-and-edit-the-solution"></a>Åpne og rediger løsningen

Rediger program.cs-filen til å kjøre eksemplet med det bestemte nøkkelhvelvnavnet:

1. Bla gjennom til mappen key-vault-dotnet-core-quickstart.
2. Åpne filen key-vault-dotnet-core-quickstart.sln i Visual Studio 2017.
3. Åpne Program.cs-filen, og oppdater plassholderen *YourKeyVaultName* med navnet på nøkkelhvelvet du opprettet tidligere.

Denne løsningen bruker [AppAuthentication](https://www.nuget.org/packages/Microsoft.Azure.Services.AppAuthentication) og [KeyVault](https://www.nuget.org/packages/Microsoft.Azure.KeyVault) NuGet-biblioteker.

## <a name="run-the-app"></a>Kjør appen

Velg **Feilsøk** > **Start** uten feilsøking fra hovedmenyen i Visual Studio 2017. Når nettleseren vises, går du til **Om**-siden. Verdien for **AppSecret** vises.

## <a name="publish-the-web-application-to-azure"></a>Publiser nettprogrammet i Azure

Publiser denne appen i Azure for å se den live som en nettapp, og for å se at du kan hente den hemmelige verdien:

1. Velg prosjektet **key-vault-dotnet-core-quickstart** i Visual Studio.
2. Velg **Publiser** > **Start**.
3. Opprett en ny **App Service**, og velg deretter **Publiser**.
4. Endre appnavnet til **keyvaultdotnetcorequickstart**.
5. Velg **Opprett**.

>[!VIDEO https://sec.ch9.ms/ch9/e93d/a6ac417f-2e63-4125-a37a-8f34bf0fe93d/KeyVault_high.mp4]
::: zone-end

## <a name="enable-managed-service-identities"></a>Aktiver administrerte tjenesteidentiteter

Med Azure Key Vault kan du lagre legitimasjon og andre nøkler og hemmeligheter på en sikker måte, men koden må godkjenne Azure Key Vault for å hente dem. Administrert tjenesteidentitet gjør dette enklere ved å gi Azure-tjenester en automatisk administrert identitet i Azure Active Directory (Azure AD). Du kan bruke denne identiteten til å godkjenne alle tjenester som støtter Azure AD-godkjenning, inkludert Key Vault, uten å ha legitimasjon i koden.

1. Gå tilbake til Azure CLI.
2. Kjør assign-identity-kommandoen for å opprette identiteten for dette programmet:

   ```azurecli
   az webapp identity assign --name "keyvaultdotnetcorequickstart" --resource-group "<YourResourceGroupName>"
   ```

>[!NOTE]
>Kommandoen i denne prosedyren tilsvarer det å gå til portalen og sette **Administrert tjenesteidentitet** til **På** i egenskapene for nettprogrammet.

## <a name="assign-permissions-to-your-application-to-read-secrets-from-key-vault"></a>Tilordne tillatelser til programmet for å lese hemmeligheter fra Key Vault

Legg merke til utdataene når du publiserer programmet i Azure. Det skal være i følgende format:

```json
        {
          "principalId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
          "tenantId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
          "type": "SystemAssigned"
        }
```

Deretter kjører du denne kommandoen ved hjelp av navnet på nøkkelhvelvet og verdien til **PrincipalId**:

```azurecli
az keyvault set-policy --name '<YourKeyVaultName>' --object-id <PrincipalId> --secret-permissions get
```

::: zone pivot="nodejs"
## <a name="deploy-the-node-app-to-azure-and-retrieve-the-secret-value"></a>Distribuer Node-appen i Azure, og hent den hemmelige verdien

Nå som alt er angitt. Kjør følgende kommando for å distribuere appen i Azure

```bash
git push azure master
```

Etter dette, når du blar gjennom https://<app_name>.azurewebsites.net, ser du den hemmelige verdien.
Sørg for at du har erstattet navnet <YourKeyVaultName> med hvelvnavnet ::: zone-end

::: zone-end

::: zone pivot="dotnet" Når du nå kjører programmet, skal du kunne se den hemmelige verdien som hentes.
::: zone-end

## <a name="next-steps"></a>Neste trinn

::: zone pivot="nodejs"
* [Hjemmeside for Azure Key Vault](https://azure.microsoft.com/services/key-vault/)
* [Dokumentasjon for Azure Key Vault](https://docs.microsoft.com/azure/key-vault/)
* [Azure SDK for Node](https://docs.microsoft.com/javascript/api/overview/azure/key-vault)
* [Azure REST-API-referanse](https://docs.microsoft.com/rest/api/keyvault/) ::: zone-end

::: zone pivot="dotnet"
* [Hjemmeside for Azure Key Vault](https://azure.microsoft.com/services/key-vault/)
* [Dokumentasjon for Azure Key Vault](https://docs.microsoft.com/azure/key-vault/)
* [Azure SDK for .NET](https://github.com/Azure/azure-sdk-for-net)
* [Azure REST-API-referanse](https://docs.microsoft.com/rest/api/keyvault/) ::: zone-end
