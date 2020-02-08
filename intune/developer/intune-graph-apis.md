---
title: Guide pratique pour utiliser Azure AD afin d’accéder aux API Intune dans Microsoft Graph
titleSuffix: Microsoft Intune
description: Décrit les étapes nécessaires pour que les applications puissent utiliser Azure AD afin d’accéder aux API Intune dans Microsoft Graph.
keywords: rôles d’autorisation intune graphapi c# powershell
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac63ef1f35e7b4730e275c6c9e566c53463c72ce
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754794"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Guide pratique pour utiliser Azure AD afin d’accéder aux API Intune dans Microsoft Graph

[L’API Microsoft Graph](https://developer.microsoft.com/graph/) prend désormais en charge Microsoft Intune avec des API et rôles d’autorisation spécifiques.  L’API Microsoft Graph utilise Azure AD (Azure Active Directory) pour l’authentification et le contrôle d’accès.  
L’accès aux API Intune dans Microsoft Graph nécessite :

- Un ID d’application avec :

  - L’autorisation d’appeler Azure AD et les API Microsoft Graph.
  - Les étendues d’autorisation pertinentes pour les tâches spécifiques de l’application.

- Informations d'identification d'utilisateur avec :

  - L’autorisation d’accéder au client Azure AD associé à l’application.
  - Les autorisations de rôle requises pour prendre en charge les étendues d’autorisation de l’application.

- L’utilisateur final doit accorder une autorisation à l’application pour qu’elle puisse effectuer des tâches d’application pour leur client Azure.

Cet article :

- Montre comment inscrire une application avec un accès à l’API Microsoft Graph et aux rôles d’autorisation pertinents.

- Décrit les rôles d’autorisation de l’API Intune.

- Fournit des exemples d’authentification de l’API Intune pour C# et PowerShell.

- Décrit comment prendre en charge plusieurs clients.

Pour en savoir plus, consultez :

- [Autoriser l’accès aux applications web à l’aide d’OAuth 2.0 et d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Prise en main de l’authentification Azure AD](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Intégration d'applications avec Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [Comprendre OAuth 2.0](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Inscrire des applications pour utiliser l’API Microsoft Graph

Pour inscrire une application pour qu’elle utilise l’API Microsoft Graph :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) en utilisant les informations d’identification d’administration.

    Selon le cas, vous pouvez utiliser :
    - Le compte d’administrateur du client.
    - Un compte d’utilisateur du client avec le paramètre **Les utilisateurs peuvent inscrire des applications** activé.

2. Dans le menu, choisissez **Azure Active Directory**&gt;**Inscriptions d’applications**.

    <img src="../media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3. Choisissez **Nouvelle inscription d’application** pour créer une nouvelle application ou choisissez une application existante.  (Si vous choisissez une application existante, ignorez l’étape suivante).

4. Dans le panneau **Créer**, spécifiez les valeurs suivantes :

    1. Un **nom** pour l’application (qui s’affiche lorsque les utilisateurs se connectent).

    2. Les valeurs de **Type d’application** et **d’URI de redirection**.

        Ces paramètres varient en fonction de vos besoins. Par exemple, si vous utilisez une [bibliothèque d’authentification](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) Azure AD (ADAL), définissez **Type d’application** sur `Native` et **URI de redirection** sur `urn:ietf:wg:oauth:2.0:oob`.

        <img src="../media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        Pour en savoir plus, consultez les [Scénarios d’authentification pour Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

5. À partir du panneau de l’application :

    1. Notez la valeur **ID d’application**.

    2. Choisissez **Paramètres** &gt; **Accès d’API** &gt; **Autorisations nécessaires**.

    <img src="../media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6. Dans le panneau **Autorisations nécessaires**, choisissez **Ajouter** &gt; **Ajouter un accès d’API** &gt; **Sélectionner une API**.

    <img src="../media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7. Dans le panneau **Sélectionner une API**, choisissez **Microsoft Graph** &gt; **Sélectionner**.  Le panneau **Activer l’accès** s’ouvre et répertorie les étendues d’autorisation disponibles pour votre application.

    <img src="../media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    Sélectionnez les rôles requis pour votre application en plaçant une coche à gauche des noms appropriés.  Pour en savoir plus sur les étendues d’autorisation propres à Intune, consultez [Étendues d’autorisation Intune](#intune-permission-scopes).  Pour en savoir plus sur les autres étendues d’autorisation de l’API Graph, consultez [Référence des autorisations Microsoft Graph](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

    Pour de meilleurs résultats, choisissez le minimum de rôles nécessaires pour implémenter votre application.

    Lorsque vous avez terminé, choisissez **Sélectionner** et **Terminé** pour enregistrer les modifications.

À ce stade, vous pouvez également :

- Choisir d’accorder une autorisation à tous les comptes client pour utiliser l’application sans fournir d’informations d’identification.  

    Pour ce faire, choisissez **Accorder des autorisations** et acceptez l’invite de confirmation.

    Lorsque vous exécutez l’application pour la première fois, vous êtes invité à lui accorder l’autorisation d’utiliser les rôles sélectionnés.

    <img src="../media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- Rendez l’application disponible aux utilisateurs extérieurs à votre client.  (Cela est généralement nécessaire uniquement pour les partenaires prenant en charge plusieurs clients ou organisations.)  

    Pour cela :

  1. Choisissez **Manifeste** dans le panneau de l’application, ce qui ouvre le panneau **Modifier le manifeste**.

     <img src="../media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. Modifiez la valeur du paramètre `availableToOtherTenants` sur `true`.

  3. Enregistrez vos modifications.

## <a name="intune-permission-scopes"></a>Étendues d’autorisation Intune

Azure AD et Microsoft Graph utilisent des étendues d’autorisation pour contrôler l’accès aux ressources d’entreprise.  

Les étendues d’autorisation (également appelées _étendues OAuth_) contrôlent l’accès à des entités Intune spécifiques et à leurs propriétés. Cette section résume les étendues d’autorisation pour les fonctionnalités de l’API Intune.

Pour en savoir plus :
- [Authentification Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Étendues d’autorisation d’application](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

Quand vous accordez des autorisations à Microsoft Graph, vous pouvez spécifier les étendues suivantes pour contrôler l’accès aux fonctionnalités d’Intune : Le tableau suivant récapitule les étendues des autorisations de l’API Intune.  La première colonne affiche le nom de la fonctionnalité telle qu’il apparaît dans le portail Azure, et la deuxième colonne fournit le nom de l’étendue d’autorisation.

Paramètre _Activer l’accès_ | Nom de l’étendue
:--|:--
__Effectuer des actions à distance affectant les utilisateurs sur les appareils Microsoft Intune__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Lire et écrire sur des appareils Microsoft Intune__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Lire des appareils Microsoft Intune__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Lire et écrire des paramètres Microsoft Intune RBAC__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Lire des paramètres Microsoft Intune RBAC__ | DeviceManagementRBAC.Read.All
__Lire et écrire dans des applications Microsoft Intune__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Lire des applications Microsoft Intune__ | [DeviceManagementApps.Read.All](#app-ro)
__Lire et écrire la configuration et les stratégies d’appareil Microsoft Intune__ | DeviceManagementConfiguration.ReadWrite.All
__Lire la configuration et les stratégies d’appareil Microsoft Intune__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Lire et écrire la configuration Microsoft Intune__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Lire la configuration Microsoft Intune__ | DeviceManagementServiceConfig.Read.All

Le tableau liste les paramètres dans leur ordre d’apparition dans le portail Azure. Les sections suivantes décrivent les étendues par ordre alphabétique.

À ce stade, toutes les étendues d’autorisation Intune requièrent un accès administrateur.  Cela signifie que vous avez besoin des informations d’identification correspondantes lors de l’exécution des applications ou des scripts qui accèdent aux ressources de l’API Intune.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- Paramètre **Activer l’accès** : __Lire des applications Microsoft Intune__

- Autorise l’accès en lecture aux propriétés suivantes de l’entité et à son état :
  - Applications clientes
  - Catégories d’applications mobiles
  - Stratégies de protection des applications
  - Configurations d’application

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- Paramètre **Activer l’accès** : __Lire et écrire dans des applications Microsoft Intune__

- Autorise les mêmes opérations que __DeviceManagementApps.Read.All__

- Autorise également les modifications aux entités suivantes :

  - Applications clientes
  - Catégories d’applications mobiles
  - Stratégies de protection des applications
  - Configurations d’application

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- Paramètre **Activer l’accès** : __Lire les stratégies et la configuration d’appareil Microsoft Intune__

- Autorise l’accès en lecture aux propriétés suivantes de l’entité et à son état :
  - Configuration des appareils
  - Stratégie de conformité des appareils
  - Messages de notification

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- Paramètre **Activer l’accès** : __Lire et écrire les stratégies et la configuration de l’appareil Microsoft Intune__

- Autorise les mêmes opérations que __DeviceManagementConfiguration.Read.All__

- Les applications peuvent également créer, affecter, supprimer et modifier les entités suivantes :
  - Configuration des appareils
  - Stratégie de conformité des appareils
  - Messages de notification

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- Paramètre **Activer l’accès** : __Effectuer des actions à distance affectant les utilisateurs sur les appareils Microsoft Intune__

- Permet les actions à distance suivantes sur un appareil géré :
  - Mettre hors service
  - Réinitialisation
  - Code secret de réinitialisation/restauration
  - Verrouillage à distance
  - Activer/Désactiver le mode de perte d'appareil
  - PC propre
  - Redémarrage
  - Supprimer un utilisateur d’un appareil partagé

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- Paramètre **Activer l’accès** : __Lire des appareils Microsoft Intune__

- Autorise l’accès en lecture aux propriétés suivantes de l’entité et à son état :
  - Appareil géré
  - Catégorie d’appareil
  - Application détectée
  - Actions à distance
  - Informations de programme malveillant

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- Paramètre **Activer l’accès** : __Lire et écrire sur des appareils Microsoft Intune__

- Autorise les mêmes opérations que __DeviceManagementManagedDevices.Read.All__

- Les applications peuvent également créer, supprimer et modifier les entités suivantes :
  - Appareil géré
  - Catégorie d’appareil

- Les actions à distance suivantes sont également autorisées :
  - Localiser des appareils
  - Désactiver le verrou d’activation
  - Demander l'assistance à distance

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- Paramètre **Activer l’accès** : __Lire des paramètres Microsoft Intune RBAC__

- Autorise l’accès en lecture aux propriétés suivantes de l’entité et à son état :
  - Attributions de rôles
  - Définitions de rôle
  - Opérations sur les ressources

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- Paramètre **Activer l’accès** : __Lire et écrire des paramètres Microsoft Intune RBAC__

- Autorise les mêmes opérations que __DeviceManagementRBAC.Read.All__

- Les applications peuvent également créer, affecter, supprimer et modifier les entités suivantes :
  - Attributions de rôles
  - Définitions de rôle

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- Paramètre **Activer l’accès** : __Lire la configuration Microsoft Intune__

- Autorise l’accès en lecture aux propriétés suivantes de l’entité et à son état :
  - Inscription d’appareil
  - Certificat de notification Apple Push
  - Programme d'inscription d'appareils Apple
  - Programme d’achats en volume (VPP) Apple
  - Connecteur Exchange
  - Conditions générales
  - Gestion des dépenses de télécommunications
  - Infrastructure à clé publique cloud
  - Marque
  - Protection contre les menaces mobiles

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- Paramètre **Activer l’accès** : __Lire et écrire la configuration Microsoft Intune__

- Autorise les mêmes opérations que DeviceManagementServiceConfig.Read.All_

- Les applications peuvent également configurer les fonctionnalités Intune suivantes :
  - Inscription d’appareil
  - Certificat de notification Apple Push
  - Programme d'inscription d'appareils Apple
  - Programme d’achats en volume (VPP) Apple
  - Connecteur Exchange
  - Conditions générales
  - Gestion des dépenses de télécommunications
  - Infrastructure à clé publique cloud
  - Marque
  - Protection contre les menaces mobiles

## <a name="azure-ad-authentication-examples"></a>Exemples d’authentification Azure AD

Cette section montre comment intégrer vos projets C# et PowerShell avec Azure AD.

Dans chaque exemple, vous devez spécifier un ID d’application qui a au moins l’étendue d’autorisation `DeviceManagementManagedDevices.Read.All` (décrite précédemment).

Lorsque vous testez l’exemple, vous pourriez recevoir des erreurs d’état HTTP 403 (interdit) semblables à ce qui suit :

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

Si cela se produit, vérifiez que :

- Vous avez mis à jour l’ID d’application sur une valeur autorisée à utiliser l’API Microsoft Graph et l’étendue d’autorisation `DeviceManagementManagedDevices.Read.All`.

- Vos informations d’identification au client prennent en charge les fonctions d’administration.

- Votre code est similaire aux exemples affichés.


### <a name="authenticate-azure-ad-in-c"></a>Authentification Azure AD en C\#

Cet exemple montre comment utiliser C# pour récupérer la liste des appareils associés à votre compte Intune.

1. Démarrez Visual Studio, puis créez un projet d’application de console Visual C# (.NET Framework).

2. Saisissez un nom pour votre projet et fournissez d’autres informations selon vos besoins.

    <img src="../media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3. Utilisez l’Explorateur de solutions pour ajouter le package NuGet de la bibliothèque Microsoft ADAL au projet.

    1. Cliquez avec le bouton droit sur l’Explorateur de solutions.
    2. Choisir **Gérer les packages NuGet...** &gt; **Parcourir**.
    3. Sélectionnez `Microsoft.IdentityModel.Clients.ActiveDirectory`, puis choisissez **Installer**.

    <img src="../media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4. Ajoutez les instructions suivantes au début de **Program.cs** :

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5. Ajoutez une méthode pour créer l’en-tête d’autorisation :

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    N’oubliez pas d’utiliser une valeur de `application_ID` qui dispose au moins de l’étendue d’autorisation `DeviceManagementManagedDevices.Read.All`, comme décrit précédemment.

6. Ajoutez une méthode pour récupérer la liste des appareils :

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7. Mettez à jour **Main** pour appeler **GetMyManagedDevices** :

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8. Compilez et exécutez votre programme.  

Lorsque vous exécutez votre programme pour la première fois, vous recevez deux messages.  Le premier demande vos informations d’identification et le second accorde des autorisations pour la requête `managedDevices`.  

Pour référence, voici le programme complet :

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Authentification Azure AD (PowerShell)

Le script PowerShell suivant utilise le module PowerShell de AzureAD pour l’authentification.  Pour plus d’informations, consultez [Azure Active Directory PowerShell Version 2](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) et [Exemples PowerShell Intune](https://github.com/microsoftgraph/powershell-intune-samples).

Dans cet exemple, mettez à jour la valeur de `$clientID` pour correspondre à un ID d’application valide.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>Prise en charge de plusieurs clients et partenaires

Si votre organisation prend en charge des organisations avec leurs propres clients Azure AD, vous pouvez choisir d’autoriser vos clients à utiliser votre application avec leurs clients respectifs.

Pour cela :

1. Vérifiez que le compte client existe dans le locataire Azure AD cible.

2. Vérifiez que votre compte de client permet aux utilisateurs d’enregistrer des applications (consultez les **Paramètres utilisateur**).

3. Établissez une relation entre chaque client.  

    Pour ce faire, vous pouvez soit :

    a. Utiliser le [Centre pour partenaires Microsoft](https://partnercenter.microsoft.com/) pour définir une relation avec votre client et son adresse e-mail.

    b. Inviter l’utilisateur à devenir un invité de votre client.

Pour inviter l’utilisateur à être un invité de votre client :

1. Choisissez **Ajouter un utilisateur invité** à partir du panneau **Tâches rapides**.

    <img src="../media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2. Saisissez l’adresse e-mail du client et ajoutez (éventuellement) un message personnalisé pour l’invitation.

    <img src="../media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3. Choisissez **Inviter**.

Cela envoie une invitation à l’utilisateur.

   <img src="../media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   L’utilisateur doit choisir le lien **Commencer** pour accepter votre invitation.

Lorsque la relation est établie (ou que votre invitation a été acceptée), ajoutez le compte d’utilisateur pour le **Rôle d’annuaire**.

Pensez à ajouter l’utilisateur à d’autres rôles en fonction des besoins. Par exemple, pour autoriser l’utilisateur à gérer les paramètres Intune, il doit être soit un **Administrateur global** soit un **Administrateur du service Intune**.

En outre :

- Utilisez https://admin.microsoft.com pour attribuer une licence Intune à votre compte d’utilisateur.

- Mettez à jour le code d’application pour s’authentifier sur le domaine du client Azure AD de votre client, au lieu du vôtre.

    Par exemple, supposons que votre domaine de client est `contosopartner.onmicrosoft.com` et que le domaine du client de votre client est `northwind.onmicrosoft.com`, vous devez mettre à jour votre code pour s’authentifier auprès du client de votre client.

    Pour ce faire dans une application C# sur la base de l’exemple précédent, vous devez modifier la valeur de la variable `authority` :

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    par

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
