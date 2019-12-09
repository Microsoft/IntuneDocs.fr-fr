---
title: Gérer l’accès web de l’entreprise avec un navigateur protégé par une stratégie
titleSuffix: Microsoft Intune
description: Utilisez un navigateur protégé par une stratégie affecté par Intune pour gérer la navigation sur Internet ainsi que le transfert de données web au sein de l’entreprise.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 52f907b8762322684ec9e21910745a197c3dbe4e
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564310"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Gérer l’accès web de l’entreprise à l’aide d’un navigateur protégé par une stratégie Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En utilisant un navigateur protégé par une stratégie Intune (Microsoft Edge ou Intune Managed Browser), vous avez la garantie que les sites web d’entreprise sont toujours accessibles avec des dispositifs de protection en place.  Quand ils sont configurés avec Intune, les navigateurs protégés peuvent tirer parti des avantages suivants :

- Stratégies de protection des applications
- Accès conditionnel
- Authentification unique
- Paramètres de configuration d’application
- Intégration du proxy d’application Azure

## <a name="microsoft-edge-support"></a>Prise en charge de Microsoft Edge

Vous pouvez utiliser Microsoft Edge pour des scénarios d’entreprise sur des appareils iOS et Android. Microsoft Edge prend en charge les mêmes scénarios de gestion que la fonction Intune Managed Browser, avec en plus des améliorations apportées à l’expérience de l’utilisateur final. Les fonctionnalités d’entreprise Microsoft Edge suivantes activées par les stratégies Intune incluent :

- **Double identité** : les utilisateurs peuvent ajouter à la fois un compte professionnel, mais aussi un compte personnel, pour la navigation. Il existe une séparation complète entre les deux identités, ce qui est similaire à l’architecture et à l’expérience proposées dans Microsoft Office 365 et Outlook. Les administrateurs Intune pourront définir les stratégies souhaitées pour une expérience de navigation protégée au sein du compte professionnel. 
- **Intégration de la stratégie de protection des applications Intune** : les administrateurs peuvent maintenant cibler des stratégies de protection des applications sur Microsoft Edge, y compris le contrôle des fonctions Couper, Copier et Coller, la prévention des captures d’écran et la vérification que les liens sélectionnés par l’utilisateur s’ouvrent uniquement dans d’autres applications managées.
- **Intégration des proxys Azure Application** : les administrateurs peuvent contrôler l’accès aux applications SaaS et web, afin de garantir que les applications basées sur le navigateur ne s’exécuteront que dans le navigateur Microsoft Edge sécurisé, que les utilisateurs finaux se connectent à partir du réseau d’entreprise ou à partir d’Internet. 
- **Raccourcis de la page d’accueil et favoris managés** : pour un accès facilité, les administrateurs peuvent définir des adresses URL pour qu’elles apparaissent dans les favoris lorsque les utilisateurs finaux sont dans le contexte de leur entreprise. Les administrateurs peuvent définir un raccourci de page d’accueil, qui s’affiche comme raccourci principal lorsque l’utilisateur d’entreprise ouvre une nouvelle page ou un nouvel onglet dans Microsoft Edge.

Les stratégies de protection Microsoft Intune pour Microsoft Edge permettent de protéger les données et les ressources de votre organisation. Le navigateur Microsoft Edge, protégé par Intune, garantit que les ressources de votre entreprise sont protégées non seulement dans les applications installées en mode natif, mais aussi lors de l’accès via un navigateur web.

## <a name="getting-started"></a>Mise en route

Microsoft Edge et Intune Managed Browser sont des applications de navigation web que vos utilisateurs finaux et vous-même pouvez télécharger dans les app stores publics pour les utiliser dans votre organisation. 

Configuration requise du système d’exploitation pour les stratégies de navigateur :
- Android 4 et ultérieur ou
- iOS 8.0 et ultérieur.

Les versions antérieures d’Android et d’iOS pourront encore utiliser Managed Browser, mais elles ne pourront pas installer les nouvelles versions de l’application et n’auront peut-être pas accès à toutes les fonctionnalités. Nous vous encourageons à mettre à jour le système d’exploitation de ces appareils avec une version prise en charge.

>[!NOTE]
>Managed Browser ne prend pas en charge le protocole de chiffrement SSLv3 (Secure Sockets Layer version 3).


## <a name="application-protection-policies-for-protected-browsers"></a>Stratégies de protection d’application pour les navigateurs protégés

Microsoft Edge et Managed Browser étant intégrés au kit SDK Intune, vous pouvez également leur appliquer des stratégies de protection d’applications, notamment :
- Contrôle de l’utilisation des fonctions Copier, Couper et Coller.
- Blocage des captures d’écran.
- Garantie que les liens d’entreprise s’ouvrent uniquement dans les applications et les navigateurs gérés.

Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

Vous pouvez appliquer ces paramètres :

- aux appareils inscrits auprès d’Intune ;
- aux appareils inscrits auprès d’un autre produit MDM ;
- aux appareils qui ne sont pas gérés.

>[!NOTE]
>Si les utilisateurs installent Managed Browser à partir de l’App Store et qu’Intune ne le prend pas en charge, vous pouvez l’utiliser comme navigateur web de base, avec prise en charge de l’authentification unique via le site Microsoft MyApps. Les utilisateurs sont directement dirigés vers le site MyApps, où ils peuvent voir toutes leurs applications SaaS provisionnées.
Quand Managed Browser et Microsoft Edge ne sont pas gérés par Intune, ils ne peuvent pas accéder aux données des applications gérées par Intune. 


## <a name="conditional-access-for-protected-browsers"></a>Accès conditionnel pour les navigateurs protégés

Managed Browser est à présent une application cliente approuvée pour l’accès conditionnel. Cela signifie que vous pouvez restreindre l’accès au navigateur mobile pour les applications web connectées à Azure AD. Les utilisateurs peuvent ainsi uniquement utiliser Managed Browser, l’accès à partir de tout autre navigateur non protégé, comme Safari ou Chrome, étant bloqué. Cette protection est applicable aux ressources Azure comme Exchange Online et SharePoint Online, le Centre d’administration Microsoft 365, et même les sites locaux exposés aux utilisateurs externes par le biais du [proxy d’application Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Pour obliger les applications web connectées à Azure AD à utiliser Intune Managed Browser sur des plateformes mobiles, vous pouvez créer une stratégie d’accès conditionnel qui exige des applications clientes approuvées. 

> [!TIP]  
> L’accès conditionnel est une technologie Azure Active Directory (Azure AD). Le nœud d’accès conditionnel accessible à partir d’*Intune* est le même nœud que celui accessible à partir d’*Azure AD*.  

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Accès conditionnel** > **Nouvelle stratégie**.
3. Ajoutez le **nom** de la stratégie. 
4. Dans la section **Affectations**, sélectionnez **Conditions** > **Applications clientes**. Le volet **Applications clientes** s’affiche.
5. Cliquez sur **Oui** sous **Configurer** pour appliquer la stratégie à des applications clientes spécifiques.
6. Vérifiez que **Browser** est sélectionné comme application cliente.

    ![Azure AD - Managed Browser - Sélectionner des applications clientes](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Pour restreindre les applications natives (applications sans navigateur) qui peuvent accéder à ces applications cloud, vous pouvez également sélectionner **Applications mobiles et clients de bureau**.

7. Cliquez sur **Terminé** > **Terminé**.
8. Dans la section **Affectations**, sélectionnez **Utilisateurs et groupes**, puis choisissez les utilisateurs ou groupes à affecter à cette stratégie. Cliquez sur **Terminé** pour fermer le volet.
9. Dans la section **Affectations**, sélectionnez **Applications ou actions cloud** pour choisir les applications à protéger avec cette stratégie. Cliquez sur **Terminé** pour fermer le volet.
10. Sélectionnez **Octroi** dans la section **Contrôles d’accès** du volet. 
11. Cliquez sur **Accorder l’accès**, puis sur **Demander une application cliente approuvée**. 
12. Cliquez sur **Sélectionner** dans le volet **Accorder**. Cette stratégie doit être attribuée aux applications cloud à rendre accessibles uniquement pour l’application Intune Managed Browser.

    ![Azure AD - Stratégie d’accès conditionnel Managed Browser](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)



Une fois que la stratégie ci-dessus est configurée, les utilisateurs sont obligés d’utiliser Intune Managed Browser pour accéder aux applications web connectées à Azure AD que vous avez protégées avec cette stratégie. Si les utilisateurs essaient d’utiliser un navigateur non géré dans ce scénario, ils sont informés qu’ils doivent plutôt utiliser Intune Managed Browser.

Managed Browser ne prend pas en charge les stratégies d’accès conditionnel classiques. Pour plus d’informations, consultez [Migrer les stratégies classiques dans le portail Azure](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Authentification unique auprès des applications web connectées à Azure AD dans les navigateurs protégés par une stratégie

Microsoft Edge et Intune Managed Browser sur iOS et Android peuvent tirer parti de la fonctionnalité SSO (authentification unique) auprès de toutes les applications web (SaaS et locales) connectées à Azure AD. Quand l’application Microsoft Authenticator est présente sur iOS ou l’application Portail d’entreprise Intune sur Android, les utilisateurs d’un navigateur protégé par une stratégie peuvent accéder aux applications web connectées à Azure AD sans avoir à entrer de nouveau leurs informations d’identification.

Pour permettre l’utilisation de SSO, votre appareil doit être inscrit par l’application Microsoft Authenticator sur iOS ou le Portail d’entreprise Intune sur Android. Les utilisateurs disposant de l’application Authenticator ou Portail d’entreprise Intune sont invités à inscrire leur appareil quand ils accèdent à une application web connectée à Azure AD dans un navigateur protégé par une stratégie, si ce dernier n’est pas déjà inscrit par une autre application. Une fois que l’appareil est inscrit avec le compte géré par Intune, l’authentification unique est activée dans ce compte pour les applications web connectées à Azure AD. 

> [!NOTE]
> L’inscription d’un appareil est un simple enregistrement auprès du service Azure AD. Elle ne nécessite pas une inscription complète et ne donne aucun autre privilège supplémentaire sur l’appareil.

## <a name="create-a-protected-browser-app-configuration"></a>Créer une configuration d’application de navigateur protégé

>[!IMPORTANT]
>Pour les configurations d’application à appliquer, le navigateur protégé de l’utilisateur ou une autre application sur l’appareil doivent déjà être gérés par la [stratégie de protection des applications Intune]( ../app-protection-policy.md).

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter** > **Applications gérées**.
3. Dans la page **Concepts de base** du volet **Créer une stratégie de configuration d’application**, entrez un **Nom** et une **Description facultative** pour les paramètres de configuration de l’application.
4. Choisissez **Sélectionner l’application publique**, puis **Managed Browser** et/ou **Edge** pour iOS, pour Android, ou les deux.
5. Cliquez sur **Sélectionner** pour revenir au volet **Créer une stratégie de configuration d'application**.
6. Cliquez sur **Suivant** pour afficher la page **Paramètres**.
7. Dans la page **Paramètres**, vous définissez des paires clé / valeur afin de fournir des configurations pour l’application. Consultez les sections plus bas dans cet article pour en savoir plus sur les différentes paires clé/valeur que vous pouvez définir.
8. Cliquez sur **Suivant** pour afficher la page **Assignation**, puis cliquez sur **Sélectionner les groupes à inclure** et/ou **Sélectionner les groupes à exclure**.
9. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**.
10. Cliquez sur **Créer** après avoir passé en revue la stratégie de configuration de l'application.

La nouvelle configuration est créée et s’affiche dans le volet **Stratégie de configuration des applications**.


## <a name="assign-the-configuration-settings-you-created"></a>Affecter les paramètres de configuration que vous avez créés

Vous affectez les paramètres à des groupes d’utilisateurs Azure AD. Si cet utilisateur a installé l’application de navigateur protégé ciblée, cette dernière est gérée par les paramètres que vous avez spécifiés.

1. Dans le volet **Applications** du tableau de bord de gestion des applications mobiles Intune, choisissez **Stratégies de configuration des applications**.
2. Dans la liste de configurations de l’application, sélectionnez celle que vous souhaitez affecter.
3. Dans le volet suivant, choisissez **Affectations**.
4. Dans le volet **Affectations**, sélectionnez le groupe Azure AD auquel vous voulez affecter la configuration d’application, puis choisissez **OK**.

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>Comment définir Microsoft Edge comme navigateur protégé pour votre organisation

Ce paramètre vous permet de configurer si vos utilisateurs seront dirigés vers Microsoft Edge ou Intune Managed Browser, en supposant que les deux navigateurs sont ciblés avec la stratégie de protection des applications. **Ce paramètre de stratégie de configuration des applications doit être ciblé sur les applications gérées par Intune à partir desquelles le lien web est ouvert.** 

Si ce paramètre est défini sur « True » :

- Vos utilisateurs seront dirigés vers Microsoft Edge lors de l’ouverture des liens à partir d’applications gérées par Intune ciblées avec ce paramètre. 
- S’ils n’ont pas encore l’application, ils seront invités à télécharger Microsoft Edge à partir du Store, qu’ils disposent ou non du navigateur Intune Managed Browser téléchargé.

Si ce paramètre est défini sur « False » :

- Si vos utilisateurs ont téléchargé Managed Browser **et** Microsoft Edge, Managed Browser est lancé. 
- Si vos utilisateurs ont téléchargé **soit** Managed Browser, **soit** Microsoft Edge, cette application de navigateur est lancée. 
- Si vos utilisateurs n’ont pas d’application de navigateur téléchargée, ils sont invités à télécharger Managed Browser.

Utilisation de la procédure ci-dessus pour créer une configuration d’application Microsoft Edge. Fournissez la paire clé/valeur suivante lorsque vous sélectionnez les **paramètres de configuration** dans le volet **Configuration** (étape 9) :

| Clé                              |  Valeur   |
|----------------------------------|----------|
| **com.microsoft.intune.useEdge** | **true** |

> [!NOTE]
> Dans la stratégie de protection des applications qui gère Microsoft Edge et les applications associées spécifiées dans la configuration de l’application, vérifiez que les paramètres de la stratégie de protection des données suivants sont définis :
> - Envoyer les données d’organisation à d’autres applications : **Applications gérées par la stratégie**
> - Restreindre le transfert de contenu web à d’autres applications : **Navigateurs gérés par la stratégie**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Configurer des paramètres de proxy d’application pour les navigateurs protégés

Microsoft Edge, Intune Managed Browser et le [Proxy d’application Azure AD]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) peuvent être utilisés ensemble afin de prendre en charge les scénarios suivants pour les utilisateurs d’appareils iOS et Android :

- Un utilisateur télécharge l’application Microsoft Outlook et s’y connecte. Les stratégies de protection des applications Intune sont automatiquement appliquées. Elles chiffrent les données enregistrées et empêchent l’utilisateur de transférer des fichiers d’entreprise vers des applications non gérées ou des emplacements sur l’appareil. Quand l’utilisateur clique alors sur un lien vers un site intranet dans Outlook, vous pouvez spécifier que ce lien s’ouvre dans l’application de navigateur protégé plutôt que dans un autre navigateur. Le navigateur protégé reconnaît que ce site intranet a été exposé à l’utilisateur via le proxy d’application. L’utilisateur est automatiquement routé par le biais du proxy d’application, pour s’authentifier avec n’importe quelle authentification multifacteur applicable et l’accès conditionnel avant d’atteindre le site intranet. Ce site, introuvable quand l’utilisateur était distant, est désormais accessible et le lien dans Outlook fonctionne comme prévu.
- Un utilisateur distant ouvre l’application de navigateur protégé et accède à un site intranet avec l’URL interne. Le navigateur protégé reconnaît que ce site intranet a été exposé à l’utilisateur via le proxy d’application. L’utilisateur est automatiquement routé par le biais du proxy d’application, pour s’authentifier avec n’importe quelle authentification multifacteur applicable et l’accès conditionnel avant d’atteindre le site intranet. Ce site, introuvable quand l’utilisateur était distant, est désormais accessible.

### <a name="before-you-start"></a>Avant de commencer

- Configurez vos applications internes à l’aide du proxy d’application Azure AD.
  - Pour configurer le proxy d’application et publier des applications, consultez la [documentation d’installation](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). 
  - [Les utilisateurs doivent être attribués](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing) à l’application d’entreprise pour laquelle la redirection doit se produire. Cela doit être fait même si l’application est configurée en mode Passthrough pour la pré-authentification et si l’exigence d’attribution d’utilisateur a été désactivée dans les paramètres du proxy d’application.
- Vous devez utiliser au minimum la version 1.2.0 de l’application Managed Browser.
- Les utilisateurs de l’application Managed Browser ou Microsoft Edge ont une [stratégie Intune App Protection](app-protection-policy.md) affectée à l’application.

    > [!NOTE]
    > La mise à jour des données de redirection du proxy d’application dans Managed Browser et Microsoft Edge peut prendre jusqu’à 24 heures.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Étape 1 : Activer la redirection automatique vers un navigateur protégé à partir d’Outlook
Outlook doit être configuré avec une stratégie de protection des applications qui active le paramètre **Restreindre le contenu web à afficher dans Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>Étape 2 : Attribuer une stratégie de configuration d’application affectée pour le navigateur protégé
Cette procédure configure l’application Managed Browser ou Microsoft Edge de façon à utiliser la redirection de proxy d’application. 

Ouvrez l’onglet **Edge** dans les paramètres de configuration de la stratégie et sélectionnez **Activer** pour la valeur de redirection du proxy d’application. L’activation de ce paramètre permet aux utilisateurs d’accéder aux liens d’entreprise et aux applications web locales publiées via le proxy d’application Azure.

Pour plus d’informations sur la manière d’utiliser conjointement Managed Browser, Microsoft Edge et le proxy d’application Azure AD pour un accès fluide (et protégé) aux applications web locales, consultez le billet de blog Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access).

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>Configurer la page d’accueil d’un navigateur protégé

Ce paramètre permet de configurer la page d’accueil que voient les utilisateurs quand ils lancent un navigateur protégé ou créent un onglet. 
- Ce paramètre affiche la page web dans Managed Browser.  Edge affiche à la place un raccourci de la page d’accueil.
- L’icône de raccourci de page d’accueil s’affiche en tant qu’icône sous la commande de recherche.  Elle ne peut pas être modifiée ou supprimée.
- Le raccourci de la page d’accueil affiche le nom de votre organisation pour le distinguer.  Il apparaît toujours comme la première icône.

Suivant la procédure de création d’une configuration d’application Managed Browser ou Microsoft Edge, indiquez la paire clé/valeur suivante :

|                                Clé                                |                                                           Valeur                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Spécifiez une URL valide. Les URL incorrectes sont bloquées par mesure de sécurité.<br>Exemple : `https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>Configurer des signets pour un navigateur protégé

Ce paramètre permet de configurer un ensemble de signets pour les utilisateurs de Microsoft Edge ou de Managed Browser.

- Ces signets ne peuvent pas être supprimés ni modifiés par les utilisateurs
- Ces signets s’affichent en haut de la liste. Tous les signets créés par les utilisateurs sont affichés sous ces signets.
- Si vous avez activé la redirection de proxy d’application, vous pouvez ajouter des applications web de proxy d’application en utilisant leur URL interne ou externe.

Suivant la procédure de création d’une configuration d’application Managed Browser ou Microsoft Edge, indiquez la paire clé/valeur suivante :

|                                Clé                                 |                                                                                                                                                                                                                                                         Valeur                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | La valeur de cette configuration est une liste de signets. Chaque signet comprend le titre et l’URL du signet. Séparez le titre et l’URL par le caractère <strong>&#124;</strong>.<br><br>Exemple :<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>Pour configurer plusieurs signets, séparez chaque paire par deux caractères, <strong>&#124;&#124;</strong><br><br>Exemple :<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>Spécifier des URL autorisées et bloquées pour un navigateur protégé

Suivant la procédure de création d’une configuration d’application Managed Browser ou Microsoft Edge, indiquez la paire clé/valeur suivante :

|Clé|Valeur|
|-|-|
|Choisissez parmi :<br><ul><li>Spécifier des URL autorisées (seules ces URL sont autorisées ; aucun autre site n’est accessible) :<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Spécifier des URL bloquées (tous les autres sites sont accessibles) :<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|La valeur correspondante pour la clé est une liste d’URL. Vous entrez toutes les URL que vous souhaitez autoriser ou bloquer comme des valeurs uniques, séparées par des barres verticales **&#124;** .<br><br>Exemples :<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>Ne spécifiez pas les deux clés. Si les deux clés sont destinées au même utilisateur, la clé allow est utilisée parce qu’il s’agit de l’option la plus restrictive.
>En outre, évitez de bloquer des pages importantes, comme les sites web de votre entreprise.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Format des URL autorisées et des URL bloquées
Utilisez les informations suivantes pour en savoir plus sur les formats et les caractères génériques que vous pouvez utiliser pour spécifier des URL dans les listes bloquées et autorisées :

- Vous pouvez utiliser le caractère générique ( **&#42;** ) en fonction des règles de la liste des modèles autorisés ci-dessous :

- Veillez à faire précéder toutes les URL du préfixe **http** ou **https** quand vous les entrez dans la liste.

- Vous pouvez spécifier des numéros de port dans l'adresse. Si vous ne spécifiez pas un numéro de port, les valeurs suivantes sont utilisées :

  - Port 80 pour http

  - Port 443 pour https

  L’utilisation de caractères génériques n’est pas prise en charge pour les numéros de port. Par exemple, `http://www.contoso.com:;` et `http://www.contoso.com: /;` ne sont pas pris en charge.

- Utilisez le tableau suivant pour en savoir plus sur les modèles autorisés que vous pouvez utiliser pour spécifier des URL :

|                  Adresse URL                  |                     Détails                      |                                                Correspond à                                                |                                Ne correspond pas à                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              Correspond à une page unique               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              Correspond à une page unique               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | Correspond à toutes les URL commençant par `www.contoso.com` |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     Correspond à tous les sous-domaines sous contoso.com     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             Correspond à un dossier unique              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  Correspond à une page unique, via l’utilisation d’un numéro de port   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          Correspond à une page unique sécurisée           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    Correspond à un dossier unique et à tous ses sous-dossiers    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- Voici quelques exemples d’entrées que vous ne pouvez pas spécifier :

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - Adresses IP

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>Transitions douces entre comptes professionnels et comptes personnels

La pierre angulaire de l’expérience entreprise mobile Microsoft Edge est le modèle à double identité, ce qui signifie que Microsoft Edge prend en charge les identités professionnelles et personnelles. Comme avec les applications Office 365 et Outlook, ce modèle à double identité permet aux utilisateurs finaux d’utiliser Microsoft Edge pour tous leurs besoins de navigation et pour se déplacer facilement entre les deux expériences en fonction des stratégies de contenu définies par l’administrateur. L’exploration dans le contexte personnel n’est pas affectée et les informations de l’entreprise sont entièrement contenues dans le contexte professionnel de Microsoft Edge. 

L’un des avantages de ce modèle est que lorsque les utilisateurs essaient d’ouvrir un lien (par exemple, un article de journal, etc.) sur un site qui n’est pas autorisé par votre organisation, ils peuvent le faire dans leur contexte personnel, qui est entièrement séparé du contexte professionnel. Ces transitions douces sont activées par défaut. 

Suivant la procédure de création d’une configuration d’application Managed Browser ou Microsoft Edge, indiquez la paire clé/valeur suivante :

| Clé                                                                | Valeur                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock** | Le paramètre **False** empêche ces transitions douces de se produire |

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Guide pratique pour accéder aux journaux d’applications gérées à l’aide de Managed Browser sur iOS

Les utilisateurs finaux ayant installé Managed Browser sur leurs appareils iOS peuvent afficher l’état de gestion de toutes les applications Microsoft publiées. Ils peuvent envoyer des journaux afin de dépanner leurs applications iOS gérées.

1. Ouvrez **Paramètres iOS**.
2. Sélectionnez les paramètres de l’application **Managed Browser**.
3. Cliquez sur **Activer les diagnostics Intune** pour configurer le navigateur en mode dépannage.
4. Ouvrez **Managed Browser**. Cliquez sur **Afficher l’état de l’application Intune** pour passer en revue les différents paramètres de stratégie d’application.
5. Appuyez sur **Prise en main** et **Partager les journaux** ou **Envoyer les journaux à Microsoft** pour envoyer les journaux de dépannage à votre administrateur informatique ou à Microsoft.

Vous pouvez également ouvrir le navigateur en mode dépannage à partir de l’application.

1. Ouvrez Managed Browser.
2. Tapez `about:intunehelp` dans la zone d’adresse.
Le navigateur démarre en mode dépannage.

Vous trouverez la liste des paramètres stockés dans les journaux d’applications sur la page [Consulter les journaux de protection des applications dans Managed Browser](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Sécurité et confidentialité de Managed Browser

- Managed Browser n’utilise pas les paramètres que les utilisateurs définissent pour le navigateur intégré sur leur appareil. Managed Browser n’a pas accès à ces paramètres.

- Si vous configurez l’option **Exiger un code confidentiel simple pour l’accès** ou **Exiger des informations d’identification d’entreprise pour l’accès** dans une stratégie de protection des applications associée à Managed Browser et qu’un utilisateur clique sur le lien d’aide de la page d’authentification, il peut accéder à n’importe quel site Internet, même si celui-ci a été ajouté à une liste rouge dans la stratégie.

- Managed Browser peut uniquement bloquer l’accès aux sites lorsque l’utilisateur tente de les ouvrir directement. Il ne bloque pas l’accès quand des services intermédiaires (tels qu’un service de traduction) sont utilisés pour accéder au site.

- Pour permettre l’authentification et accéder à la documentation d’Intune, le site **&#42;.microsoft.com** n’est pas soumis aux paramètres de liste verte ou rouge. Ce site est toujours autorisé.

### <a name="turn-off-usage-data"></a>Désactiver les données d’utilisation
Microsoft recueille automatiquement des données anonymes sur les performances et l’utilisation de Managed Browser pour améliorer les produits et services Microsoft. Les utilisateurs peuvent désactiver la collecte de données à l’aide du paramètre **Données d’utilisation** de leurs appareils. Vous n’avez aucun contrôle sur la collecte de ces données.

- Sur les appareils iOS, les utilisateurs ne peuvent pas ouvrir les sites web possédant un certificat qui a expiré ou qui n’est pas approuvé.

## <a name="next-steps"></a>Étapes suivantes

- [Que sont les stratégies de protection des applications ?](app-protection-policy.md) 
