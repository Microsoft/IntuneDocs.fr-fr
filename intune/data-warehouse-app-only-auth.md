---
title: Authentification Intune Data Warehouse des applications uniquement
titleSuffix: Microsoft Intune
description: Cette rubrique décrit l’authentification Data Warehouse des applications uniquement.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b72a0bf1a5f5c996ad299bd84ff6f927ef780059
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185200"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Authentification Intune Data Warehouse des applications uniquement

Vous pouvez configurer une application avec Azure Active Directory (Azure AD) et l’authentifier auprès d’Intune Data Warehouse. Ce processus est utile pour les sites web, les applications et les processus d’arrière-plan pour lesquels l’application ne doit pas avoir accès aux informations d’identification de l’utilisateur. Les étapes suivantes permettent d’autoriser une application auprès d’Azure AD avec OAuth 2.0.

## <a name="authorization"></a>Autorisation

Azure Active Directory (Azure AD) utilise OAuth 2.0 pour vous permettre d'autoriser l'accès aux applications et API Web dans votre locataire Azure AD. Ce guide montre comment authentifier une application avec C#. Le flux du code d’autorisation OAuth 2.0 est décrit dans la section 4.1 de la spécification OAuth 2.0. Pour plus d’informations, consultez [Autoriser l’accès aux applications web à l’aide d’OAuth 2.0 et d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).


## <a name="azure-keyvault"></a>Azure Key Vault

Le processus suivant utilise une méthode privée, nommée SecureString, pour traiter et convertir une clé d’application. Vous pourriez également utiliser Azure Key Vault pour stocker la clé d’application. Pour plus d’informations, consultez la section [Key Vault](https://azure.microsoft.com/services/key-vault/).

## <a name="create-a-web-app"></a>Créer une application web

Dans cette section, vous allez donner quelques informations sur l’application web vers laquelle vous souhaitez pointer sur Intune. Une application web est une application client-serveur. Le serveur fournit l’application web, qui englobe l’interface utilisateur, le contenu et les fonctionnalités. Ce type d’application est géré séparément sur le web. Intune vous permet d’accorder l’accès à Intune à l’application web. Le flux de données est lancé par l’application web. 

1.  Connectez-vous au [portail Azure](https://portal.azure.com).
2.  À l’aide du champ **Rechercher des ressources, des services et des documents** en haut du Portail Azure, recherchez **Azure Active Directory**.
3.  Dans le menu déroulant, sélectionnez **Azure Active Directory** sous **Services**.
4.  Sélectionnez **Inscription des applications**.
5.  Cliquez sur **Inscription d’une nouvelle application** pour afficher le panneau **Créer**.
6.  Dans le panneau **Créer**, ajoutez les informations relatives à votre application :

    - Le nom d’une application, par exemple, *Intune App-Only Auth*.
    - Le **Type d’application**. Choisissez **API/application web** pour ajouter une application qui représente une application web, une API web ou les deux.
    - **L’URL de connexion** de l’application. Il s’agit de l’emplacement auquel les utilisateurs accèdent automatiquement pendant le processus d’authentification. Il est nécessaire pour prouver leur identité. Pour plus d’informations, consultez la section [Qu’est-ce que l’accès aux applications et l’authentification unique auprès d’Azure Active Directory ?](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

7.  Cliquez sur **Créer** en bas du panneau **Créer**.

    >[!NOTE] 
    > Copiez **l’ID d’application** dans le panneau **Application inscrite** pour plus tard.

## <a name="create-a-key"></a>Création d'une clé

Dans cette section, Azure AD génère une valeur de clé pour votre application.

1.  Sur le panneau **Inscription des applications**, sélectionnez l’application que vous venez de créer pour afficher le panneau de l’application.
2.  Sélectionnez **Paramètres** en haut du panneau pour afficher le panneau **Paramètres**.
3.  Sélectionnez **Clés** dans le panneau **Paramètres**.
4.  Ajoutez la **Description**, la durée **d’Expiration** et la **Valeur** de la clé.
5.  Cliquez sur **Enregistrer** pour enregistrer et mettre à jour les clés de l’application.
6.  Vous devez copier la valeur de la clé générée (codée base 64).

    >[!NOTE] 
    > La valeur de la clé disparaîtra quand vous quitterez le panneau **clés**. Après cela, vous ne pourrez plus la récupérer sur ce panneau. Copiez-la pour plus tard.

## <a name="grant-application-permissions"></a>Ajouter des autorisations aux applications

Dans cette section, vous allez accorder des autorisations aux applications.

1.  Sélectionnez **Autorisations nécessaires** dans le panneau **Paramètres**.
2.  Cliquez sur **Ajouter**.
3.  Sélectionnez **Ajouter une API** pour afficher le panneau **Sélectionner une API**.
4.  Sélectionnez **API Microsoft Intune (MicrosoftIntuneAPI)**, puis cliquez sur **Sélectionner** dans le panneau **Sélectionner une API**. L’étape **Sélectionner les autorisations** est sélectionnée, et le panneau **Activer l’accès** s’affiche.
5.  Choisissez l’option **Obtenir des informations de l’entrepôt de données auprès de Microsoft Intune** dans la section **Autorisations des applications**.
6.  Cliquez sur **Sélectionner** dans le panneau **Activer l’accès**.
7.  Cliquez sur **Terminé** dans le panneau **Ajouter l’accès aux API**.
8.  Cliquez sur **Accorder des autorisations** dans le panneau **Autorisations nécessaires**, et cliquez sur **Oui** lorsqu’il vous sera demandé de mettre à jour les autorisations existantes de cette application.

## <a name="generate-token"></a>Générer le jeton

Avec Visual Studio, créez un projet d’application console (.NET Framework) qui prend en charge .NET Framework et utilise le langage de codage C#.

1.  Sélectionnez **Fichier** > **Nouveau** > **Projet** pour afficher la boîte de dialogue **Nouveau projet**.
2.  Sur la gauche, sélectionnez **Visual C#** pour afficher tous les projets .NET Framework.
3.  Sélectionnez **Application console (.NET Framework)**, ajoutez un nom d’application, puis cliquez sur **OK** pour créer l’application.
4.  Dans **l’Explorateur de solutions**, sélectionnez **Program.cs** pour afficher le code.
5.  Dans le menu contextuel, sélectionnez **Ajouter** > **Nouvel élément**. La boîte de dialogue **Ajouter un élément** s’affiche.
6.  Sur la gauche, sous **Visual C#**, sélectionnez **Code**.
7.  Sélectionnez **Classe**, modifiez le nom de la classe en choisissant *IntuneDataWarehouseClass.cs*, puis cliquez sur **Ajouter**.
8.  Ajoutez le code suivant dans la méthode <code>Main</code> :

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

9. Ajoutez des espaces de noms supplémentaires en intégrant le code suivant en haut du fichier de code :

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

10. Après la méthode <code>Main</code>, ajoutez la méthode privée suivante pour traiter et convertir la clé d’application :

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

11. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Références**, puis sélectionnez **Gérer les packages NuGet**.
12. Recherchez *Microsoft.IdentityModel.Clients.ActiveDirectory* et installez le package NuGet Microsoft associé.
13. Dans **Explorateur de solutions**, sélectionnez et ouvrez le fichier *App.config*.
14. Ajouter la section <code>appSettings</code> afin que le code XML se présente ainsi :

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

15. Remplacez les valeurs <code>appId</code>, <code>appKey</code> et <code>tenantDomain</code> par les valeurs uniques propres à votre application.
16. Créez votre application.

    >[!NOTE] 
    > Vous trouverez d’autres extraits de code d’implémentation dans la section [Exemple de code Intune Data Warehouse](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp ).

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur Azure Key Vault, consultez la section [Qu’est-ce qu’Azure Key Vault ?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis).

