---
title: Obtenir des données à partir de l’API d’entrepôt de données avec un client REST
titleSuffix: Microsoft Intune
description: Cette rubrique décrit comment récupérer des données à partir de l’entrepôt de données Microsoft Intune à l’aide d’une API RESTful.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b449dcc0ba0fc33f66db54c4cfd158aaefa8032e
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69582973"
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>Obtenir des données à partir de l’API d’entrepôt de données Intune avec un client REST

Vous pouvez accéder au modèle de données de l’entrepôt de données Intune par le biais de points de terminaison RESTful. Pour accéder à vos données, votre client doit obtenir l’autorisation sur Microsoft Azure Active Directory (Azure AD) à l’aide d’OAuth 2.0. Pour activer l’accès, configurez d’abord une application native dans Azure et accordez-lui des autorisations sur l’API Microsoft Intune. Votre client local obtient l’autorisation, puis le client peut communiquer avec les points de terminaison de l’entrepôt de données à travers l’application native.

Les étapes de configuration d’un client pour obtenir des données à partir de l’API d’entrepôt de données impliquent les actions suivantes :

1. Créer une application cliente sous forme d’application native dans Azure
3. Accorder à l’application cliente l’accès à l’API Microsoft Intune
3. Créer un client REST local pour obtenir les données

Utilisez les étapes suivantes pour découvrir comment autoriser et accéder à l’API avec un client REST. Tout d’abord, vous allez examiner l’utilisation d’un client REST générique à l’aide de Postman. Postman est un outil couramment utilisé pour résoudre les problèmes et développer les clients REST pour qu’ils utilisent des API. Pour plus d’informations sur Postman, consultez le site [Postman](https://www.getpostman.com). Vous pourrez ensuite examiner un exemple de code C#. L’exemple illustre l’autorisation d’un client et l’obtention de données à partir de l’API.

## <a name="create-a-client-app-as-a-native-app-in-azure"></a>Créer une application cliente sous forme d’application native dans Azure

Créez une application native dans Azure. Cette application native est l’application cliente. Le client qui s’exécute sur votre ordinateur local référence l’API d’entrepôt de données Intune quand le client local demande des informations d’identification.

1. Connectez-vous au portail Azure pour votre locataire. Choisissez **Azure Active Directory** > **Inscriptions des applications** pour ouvrir le volet **Inscriptions des applications**.
2. Sélectionnez **Nouvelle inscription d’application**.
3. Tapez les détails de l’application.
    1. Tapez un nom convivial, par exemple, Client de l’entrepôt de données Intune, pour le **Nom**.
    2. Sélectionnez **Natif** pour le **Type d’application**.
    3. Tapez une URL pour **l’URL de connexion**. L’URL de connexion dépend du scénario. Toutefois, si vous prévoyez d’utiliser Postman, tapez `https://www.getpostman.com/oauth2/callback`. Vous utilisez le rappel pour l’étape d’authentification du client au moment de l’authentification à Azure AD.
4. Sélectionnez **Créer**.

     ![Application cliente Intune Data Warehouse](./media/reports-get_rest_data_client_overview.png)

5. Notez **l’ID d’application** de cette application. Vous utilisez l’ID à l'étape suivante.

## <a name="grant-the-client-app-access-to-the-microsoft-intune-api"></a>Accorder à l’application cliente l’accès à l’API Microsoft Intune

Vous avez maintenant une application définie dans Azure. Accordez à l’application native l’accès à l’API Microsoft Intune.

1. Sélectionnez l’application native. Vous avez donné à l’application un nom du type **Client de l’entrepôt de données Intune**.
2. Sélectionnez **Autorisations nécessaires** dans le volet **Paramètres**.
3. Sélectionnez **Ajouter** dans le volet **Autorisations nécessaires**.
4. Sélectionnez **Sélectionner une API**.
5. Recherchez le nom de l’application web. Son nom est **API Microsoft Intune**.
6. Sélectionnez l’application dans la liste.
7. Sélectionnez **Sélectionner**.
8. Cochez la case **Autorisations déléguées** pour ajouter **Obtenir des informations de l’entrepôt de données à partir de Microsoft Intune**.

    ![Activer l’accès - API Microsoft Intune](./media/reports-get_rest_data_client_access.png)

9. Sélectionnez **Sélectionner**.
10. Sélectionnez **Terminé**.
11. Vous pouvez sélectionner **Accorder des autorisations** dans le volet Autorisations nécessaires. Cette option accorde l’accès à tous les comptes de l’annuaire actif. La boîte de dialogue de consentement ne s’affiche plus pour chaque utilisateur du locataire. Pour plus d’informations, consultez [Intégration d’applications à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).
12. Sélectionnez **Oui**.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Obtenir des données de l’API Microsoft Intune avec Postman

Vous pouvez utiliser l’API d’entrepôt de données Intune avec un client REST générique comme Postman. Postman fournit des insights sur les fonctionnalités de l’API, le modèle de données OData sous-jacent et résout les problèmes de connexion aux ressources de l’API. Cette section présente des informations sur la génération d’un jeton Auth2.0 pour votre client local. Le client a besoin du jeton pour s’authentifier auprès d’Azure AD et accéder aux ressources de l’API.

### <a name="information-you-will-need-to-make-the-call"></a>Informations nécessaires pour effectuer l’appel

Vous avez besoin des informations suivantes pour effectuer un appel REST à l’aide de Postman :

| Attribut        | Description                                                                                                                                                                          | Exemple                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| URL de rappel     | Définissez cette URL comme URL de rappel dans la page de paramètres de votre application.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| Nom du jeton       | Chaîne utilisée pour transmettre les informations d’identification à l’application Azure. Le processus génère votre jeton pour vous permettre d’effectuer un appel à l’API d’entrepôt de données.                          | Porteur                                                                                        |
| URL d’authentification         | Il s’agit de l’URL utilisée pour l’authentification. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/ |
| URL de jeton d'accès | Il s’agit de l’URL utilisée pour accorder le jeton.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| ID client        | Vous l’avez créé, et l’avez noté, quand vous avez créé l’application native dans Azure.                                                                                               | 4184c61a-e324-4F51-83d7-022b6a81b991                                                          |
| Étendue (facultatif) | Vide                                                                                                                                                                               | Vous pouvez laisser le champ vide.                                                                     |
| Type d’autorisation       | Le jeton est un code d'autorisation.                                                                                                                                                  | Code d’autorisation                                                                            |

### <a name="odata-endpoint"></a>Point de terminaison OData

Vous avez également besoin du point de terminaison. Pour obtenir votre point de terminaison d’entrepôt de données, vous avez besoin de l’URL de flux personnalisée. Vous pouvez obtenir le point de terminaison OData à partir du volet Entrepôt de données.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Ouvrez le volet **Intune Data Warehouse** en sélectionnant le lien Data Warehouse sous **Autres tâches** sur le côté droit du panneau **Microsoft Intune - Vue d’ensemble**.
4. Copiez l’URL de flux personnalisée sous **Utiliser des services de rapports tiers**. Elle doit ressembler à ceci : `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0`

Le point de terminaison suit le format suivant : `https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity}?api-version={verson-number}`

Par exemple, l’entité **dates** ressemble à : `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`

Pour plus d’informations, consultez [Point de terminaison de l’API d’entrepôt de données Intune](reports-api-url.md).

### <a name="make-the-rest-call"></a>Effectuer l’appel REST

Pour obtenir un nouveau jeton d’accès pour Postman, vous devez ajouter l’URL d’autorisation Azure AD, ajouter votre ID Client et le secret client. Postman charge la page d’autorisation dans laquelle vous tapez vos informations d’identification.

#### <a name="add-the-information-used-to-request-the-token"></a>Ajouter les informations utilisées pour demander le jeton

1. Téléchargez Postman si vous ne l’avez pas déjà installé. Pour télécharger Postman, consultez [www.getpostman](https://www.getpostman.com).
2. Ouvrez Postman. Choisissez l’opération HTTP **GET**.
3. Collez l’URL de point de terminaison dans l’adresse. Vous devez obtenir quelque chose de ce type :  

    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. Choisissez l’onglet **Autorisation** et sélectionnez **OAuth 2.0** dans la liste **Type**.
5. Sélectionnez **Obtenir un nouveau jeton d’accès**.
6. Vérifiez que vous avez déjà ajouté l’URL de rappel à votre application dans Azure. L’URL de rappel est `https://www.getpostman.com/oauth2/callback`.
7. Tapez Bearer pour le **Nom du jeton**.
8. Ajoutez **l’URL d’authentification**. Vous devez obtenir quelque chose de ce type :  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/`
9. Ajoutez **l’URL du jeton d'accès**. Vous devez obtenir quelque chose de ce type :  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Ajoutez **l’ID Client** de l’application native que vous avez créée dans Azure et qui s’appelle `Intune Data Warehouse Client`. Vous devez obtenir quelque chose de ce type :  

     `88C8527B-59CB-4679-A9C8-324941748BB4`

11. Sélectionnez **Code d’autorisation** et demandez le jeton d’accès localement.

12. Sélectionnez **Demander un jeton**.

    ![Informations pour le jeton d’accès](./media/reports-postman_getnewtoken.png)

13. Tapez vos informations d’identification dans la page d’autorisation Azure AD. La liste des jetons dans Postman contient désormais le jeton nommé `Bearer`.
14. Sélectionnez **Utiliser le jeton**. La liste des en-têtes contient la nouvelle valeur de clé d’autorisation et la valeur `Bearer <your-authorization-token>`.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Envoyer l’appel au point de terminaison à l’aide de Postman

1. Sélectionnez **Envoyer**.
2. Les données de retour s’affichent dans le corps de la réponse Postman.

    ![L’état du client postman est égal à 200 OK](./media/reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>Créer un client REST (C#) pour obtenir des données de l’entrepôt de données Intune

L’exemple suivant contient un client REST simple. Le code utilise la classe **httpClient** de la bibliothèque .Net. Une fois que le client obtient des informations d’identification pour Azure AD, il génère un appel GET REST pour récupérer l’entité dates de l’API d’entrepôt de données.

> [!Note]  
> Vous pouvez accéder au code suivant [Exemple sur GitHub](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs). Reportez-vous au dépôt GitHub pour connaître les dernières modifications et mises à jour de l’exemple.

1. Ouvrez **Microsoft Visual Studio**.
2. Choisissez **Fichier** > **Nouveau projet**. Développez **Visual C#** , puis choisissez **Application console (.Net Framework)** .
3. Nommez le projet `IntuneDataWarehouseSamples`, accédez à l’emplacement où vous voulez enregistrer le projet, puis sélectionnez **OK**.
4. Cliquez avec le bouton droit sur le nom de la solution dans l’Explorateur de solutions, puis sélectionnez **Gérer les packages NuGet pour la solution**. Sélectionnez **Parcourir**, puis tapez `Microsoft.IdentityModel.Clients.ActiveDirectory` dans la zone de recherche.
5. Choisissez le package, sélectionnez le projet **IntuneDataWarehouseSamples** sous Gérer les packages pour votre solution, puis sélectionnez **Installer**.
6. Sélectionnez **J’accepte** pour accepter la licence du package NuGet.
7. Ouvrez `Program.cs` dans l’Explorateur de solutions.

    ![Program.cs et l’Explorateur de solutions dans Visual Studio](./media/reports-get_rest_data_in.png)

8. Remplacez le code dans *Program.cs* par le code suivant :  

   ```csharp
   namespace IntuneDataWarehouseSamples
   {
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;
   using Microsoft.IdentityModel.Clients.ActiveDirectory;

   class Program
   {
    static void Main(string[] args)
   {
   /**
   * TODO: Replace the below values with your own.
   * emailAddress - The email address of the user that you will authenticate as.
   *
   * password  - The password for the above email address.
   *    This is inline only for simplicity in this sample. We do not
   *    recommend storing passwords in plaintext.
   *
   * applicationId - The application ID of the native app that was created in AAD.
   *
   * warehouseUrl   - The data warehouse URL for your tenant. This can be found in
   *      the Azure portal.
   *
   * collectionName - The name of the warehouse entity collection you would like to
   *      access.
   */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
   resource: "https://api.manage.microsoft.com/",
   clientId: applicationId,
   userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
   }
   }
   ```

9. Mettez à jour `TODO` dans l’exemple de code.
10. Appuyez sur **Ctrl + F5** pour générer et exécuter le client Intune.DataWarehouseAPIClient en mode débogage.

    ![Entité Date récupérée au format JSON.](./media/reports-get_rest_data_output.png)

11. Examinez la sortie de console. La sortie contient des données au format JSON tirées de l’entité **dates** dans votre locataire Intune.

## <a name="next-steps"></a>Étapes suivantes

Des détails sur l’autorisation, la structure URL de l’API et les points de terminaison OData sont disponibles dans [Utiliser l’API d’entrepôt de données Intune](reports-api-url.md).

Vous pouvez également consulter le modèle de données de l’entrepôt de données Intune pour rechercher les entités de données contenues dans l’API. Pour plus d’informations, consultez [Modèle de données de l’API d’entrepôt de données Intune](reports-ref-data-model.md)
