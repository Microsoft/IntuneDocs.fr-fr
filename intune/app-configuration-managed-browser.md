---
title: Gérer l’accès web avec l’application Managed Browser
titlesuffix: Microsoft Intune
description: Déployez l’application Managed Browser pour limiter la navigation sur le web et le transfert de données du web vers d’autres applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8b647e7b2a4d252041e60792b6fc49df8b961066
ms.sourcegitcommit: e01945bff19157fa7acaa4f7975b0f2a8b3a73f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37967232"
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Managed Browser est une application de navigation web que vous pouvez télécharger à partir des App Stores publics pour l’utiliser dans votre organisation. Configuré avec Intune, Managed Browser peut être :
- Utilisé pour accéder aux sites d’entreprise et aux applications SaaS avec l’authentification unique via le service MyApps, tout en assurant la protection des données web.
- Préconfiguré avec une liste d’URL et de domaines pour restreindre les sites auxquels l’utilisateur peut accéder dans le contexte de l’entreprise.
- Préconfiguré avec une page d’accueil et des signets que vous spécifiez.

Cette application étant intégrée au SDK Intune, vous pouvez également lui appliquer des stratégies de protection des applications, notamment :
- Contrôle de l’utilisation des fonctions Copier, Couper et Coller
- Prévention des captures d’écran
- Vérification que les liens vers du contenu que les utilisateurs sélectionnent s’ouvrent uniquement dans d’autres applications gérées

Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

Vous pouvez appliquer ces paramètres :

- aux appareils inscrits auprès d’Intune ;
- aux appareils inscrits auprès d’un autre produit MDM ;
- aux appareils qui ne sont pas gérés.

Si les utilisateurs installent Managed Browser à partir de l’App Store et qu’Intune ne le prend pas en charge, vous pouvez l’utiliser comme navigateur web de base, avec prise en charge de l’authentification unique via le site Microsoft MyApps. Les utilisateurs sont directement dirigés vers le site MyApps, où ils peuvent voir toutes leurs applications SaaS provisionnées.
Quand Managed Browser n’est pas géré par Intune, il ne peut pas accéder aux données d’autres applications gérées par Intune. 

Managed Browser ne prend pas en charge le protocole de chiffrement SSLv3 (Secure Sockets Layer version 3).

Vous pouvez créer des stratégies Managed Browser pour les types d'appareils suivants :

-   Appareils qui exécutent Android 4 et versions ultérieures

-   Appareils qui exécutent iOS 8.0 et versions ultérieures

>[!IMPORTANT]
>À compter d’octobre 2017, l’application Intune Managed Browser sur l’application Android prend en charge seulement les appareils exécutant Android 4.4 et ultérieur. L’application Intune Managed Browser sur iOS prendra en charge seulement les appareils exécutant iOS 9.0 et ultérieur.
>Les versions antérieures d’Android et d’iOS pourront encore utiliser Managed Browser, mais elles ne pourront pas installer les nouvelles versions de l’application et n’auront peut-être pas accès à toutes les fonctionnalités. Nous vous encourageons à mettre à jour le système d’exploitation de ces appareils avec une version prise en charge.


Intune Managed Browser prend en charge l’ouverture de contenu web des [partenaires de l’application Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="conditional-access-for-the-intune-managed-browser"></a>Accès conditionnel pour Intune Managed Browser

Managed Browser est à présent une application cliente approuvée pour l’accès conditionnel. Cela signifie que vous pouvez restreindre l’accès au navigateur mobile pour les applications web connectées à Azure AD. Les utilisateurs peuvent ainsi uniquement utiliser Managed Browser, l’accès à partir de tout autre navigateur non protégé, comme Safari ou Chrome, étant bloqué. Cette protection est applicable aux ressources Azure comme Exchange Online et SharePoint Online, le portail Office et même les sites locaux exposés aux utilisateurs externes par le biais du [Proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Pour obliger les applications web connectées à Azure AD à utiliser Intune Managed Browser sur des plateformes mobiles, vous pouvez créer une stratégie d’accès conditionnel Azure AD qui exige des applications clientes approuvées. 

1. Dans le portail Azure, sélectionnez **Azure Active Directory** > **Applications d’entreprise** > **Accès conditionnel** > **Nouvelle stratégie**. 
2. Ensuite, sélectionnez **Accorder** à partir de la section **Contrôles d’accès** du panneau. 
3. Cliquez sur **Demander une application cliente approuvée**. 
4. Cliquez sur **Sélectionner** dans le panneau **Accorder**. Cette stratégie doit être attribuée aux applications cloud à rendre accessibles uniquement pour l’application Intune Managed Browser.

    ![Azure AD - Stratégie d’accès conditionnel Managed Browser](./media/managed-browser-conditional-access-01.png)

5. Dans la section **Affectations**, sélectionnez **Conditions** > **Applications clientes**. Le panneau **Applications clientes** s’affiche.
6. Cliquez sur **Oui** sous **Configurer** pour appliquer la stratégie à des applications clientes spécifiques.
7. Vérifiez que **Browser** est sélectionné en tant qu’application cliente.

    ![Azure AD - Managed Browser - Sélectionner des applications clientes](./media/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Pour restreindre les applications natives (applications sans navigateur) qui peuvent accéder à ces applications cloud, vous pouvez également sélectionner **Applications mobiles et clients de bureau**.

8. Dans la section **Affectations**, sélectionnez **Utilisateurs et groupes**, puis choisissez les utilisateurs ou groupes à affecter à cette stratégie. 

    > [!NOTE]
    > Les utilisateurs doivent aussi être ciblés avec la stratégie de protection des applications Intune. Pour plus d’informations sur la création de stratégies Intune App Protection, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

9. Dans la section **Affectations**, sélectionnez **Applications cloud** pour choisir les applications à protéger avec cette stratégie.

Une fois que la stratégie ci-dessus est configurée, les utilisateurs sont obligés d’utiliser Intune Managed Browser pour accéder aux applications web connectées à Azure AD que vous avez protégées avec cette stratégie. Si les utilisateurs essaient d’utiliser un navigateur non géré dans ce scénario, ils sont informés qu’ils doivent plutôt utiliser Intune Managed Browser.

Managed Browser ne prend pas en charge les stratégies d’accès conditionnel classiques. Pour plus d’informations, consultez [Migrer les stratégies classiques dans le portail Azure](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

##  <a name="single-sign-on-to-azure-ad-connected-web-apps-in-the-intune-managed-browser"></a>Authentification unique auprès des applications web connectées à Azure AD dans Intune Managed Browser

L’application Intune Managed Browser sur iOS et Android peut à présent exploiter l’authentification unique auprès de toutes les applications web (locales et SaaS) connectées à Azure AD. Quand l’application Microsoft Authenticator sur iOS ou Portail d’entreprise Intune sur Android est installée, les utilisateurs d’Intune Managed Browser peuvent accéder aux applications web connectées à AD Azure sans avoir à retaper leurs informations d’identification.

L’authentification unique dans Intune Managed Browser exige l’inscription de votre appareil par l’application Microsoft Authenticator sur iOS ou Portail d’entreprise Intune sur Android. Les utilisateurs dotés de l’application Authenticator ou Portail d’entreprise Intune sont invités à inscrire leur appareil quand ils accèdent à une application web connectée à Azure AD dans Intune Managed Browser, si ce dernier n’est pas déjà inscrit par une autre application. Une fois que l’appareil est inscrit avec le compte géré par Intune, l’authentification unique est activée dans ce compte pour les applications web connectées à Azure AD. 

> [!NOTE]
> L’inscription d’un appareil est un simple enregistrement auprès du service Azure AD. Elle ne nécessite pas une inscription complète et ne donne aucun autre privilège supplémentaire sur l’appareil.

## <a name="create-a-managed-browser-app-configuration"></a>Créer une configuration d’application Managed Browser

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3.  Dans le panneau **Applications mobiles** de la liste Gérer, choisissez **Stratégies de configuration des applications**.
4.  Dans le panneau **Stratégies de configuration des applications**, choisissez **Ajouter**.
5.  Dans le panneau **Ajouter une stratégie de configuration**, entrez un **Nom** et une **Description** facultative pour les paramètres de configuration de l’application.
6.  Pour **Inscription de l’appareil**, choisissez **Applications gérées**.
7.  Choisissez **Sélectionner l’application requise** puis, dans le panneau **Applications ciblées**, choisissez **Managed Browser** pour iOS, pour Android ou pour les deux.
8.  Choisissez **OK** pour revenir au panneau **Ajouter une stratégie de configuration**.
9.  Choisissez **Paramètres de configuration**. Dans le panneau **Configuration**, vous définissez des paires clé / valeur pour fournir des configurations pour Managed Browser. Consultez les sections plus bas dans cet article pour en savoir plus sur les différentes paires clé/valeur que vous pouvez définir.
10. Une fois que vous avez terminé, choisissez **Enregistrer**.
11. Dans le panneau **Ajouter une stratégie de configuration**, choisissez **Ajouter**.
12. La nouvelle configuration est créée et s’affiche dans le panneau **Configuration des applications**.

>[!IMPORTANT]
>Actuellement, Managed Browser s’appuie sur l’inscription automatique. Pour les configurations d’application à appliquer, une autre application sur l’appareil doit déjà être gérée par les stratégies de protection des applications Intune.

## <a name="assign-the-configuration-settings-you-created"></a>Affecter les paramètres de configuration que vous avez créés

Vous affectez les paramètres à des groupes d’utilisateurs Azure AD. Si cet utilisateur a installé l’application Managed Browser, l’application est gérée par les paramètres que vous avez spécifiés.

1. Dans le panneau **Applications mobiles** du tableau de bord de gestion des applications mobiles Intune, choisissez **Stratégies de configuration des applications**.
2. Dans la liste de configurations de l’application, sélectionnez celle que vous souhaitez affecter.
3. Dans le panneau suivant, choisissez **Affectations**.
4. Dans le panneau **Affectations**, sélectionnez le groupe Azure AD auquel vous voulez affecter la configuration d’application, puis choisissez **OK**.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Comment configurer des paramètres de proxy d’application pour Managed Browser

Intune Managed Browser et le [proxy d’application Azure AD]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) peuvent être utilisés ensemble pour prendre en charge les scénarios suivants pour les utilisateurs d’appareils iOS et Android :

- Un utilisateur télécharge l’application Microsoft Outlook et s’y connecte. Les stratégies de protection des applications Intune sont automatiquement appliquées. Elles chiffrent les données enregistrées et empêchent l’utilisateur de transférer des fichiers d’entreprise vers des applications non gérées ou des emplacements sur l’appareil. Quand l’utilisateur clique ensuite sur un lien vers un site intranet dans Outlook, vous pouvez spécifier que le lien s’ouvre dans l’application Managed Browser plutôt que dans un autre navigateur. Managed Browser reconnaît que ce site intranet a été exposé à l’utilisateur via le proxy d’application. L’utilisateur est automatiquement acheminé via le proxy d’application, pour s’authentifier avec n’importe quelle authentification multifacteur applicable, et l’accès conditionnel avant d’atteindre le site intranet. Ce site, introuvable quand l’utilisateur était distant, est désormais accessible et le lien dans Outlook fonctionne comme prévu.
- Un utilisateur distant ouvre l’application Managed Browser et accède à un site intranet à l’aide de l’URL interne. Managed Browser reconnaît que ce site intranet a été exposé à l’utilisateur via le proxy d’application. L’utilisateur est automatiquement acheminé via le proxy d’application, pour s’authentifier avec n’importe quelle authentification multifacteur applicable, et l’accès conditionnel avant d’atteindre le site intranet. Ce site, introuvable quand l’utilisateur était distant, est désormais accessible.

### <a name="before-you-start"></a>Avant de commencer

- Configurez vos applications internes à l’aide du proxy d’application Azure AD.
    - Pour configurer le proxy d’application et publier des applications, consultez la [documentation d’installation](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started). 
- Vous devez utiliser au minimum la version 1.2.0 de l’application Managed Browser.
- Les utilisateurs de l’application Managed Browser ont une [stratégie de protection des applications Intune]( app-protection-policy.md) affectée à l’application.

    > [!NOTE]
    > La mise à jour des données de redirection du proxy d’application dans Managed Browser peut prendre jusqu’à 24 heures.


#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Étape 1 : Activer la redirection automatique vers Managed Browser à partir d’Outlook
Outlook doit être configuré avec une stratégie de protection des applications qui active le paramètre **Restreindre le contenu web à afficher dans Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Étape 2 : Attribuer une stratégie de configuration d’application affectée pour Managed Browser
Cette procédure configure l’application Managed Browser pour utiliser la redirection de proxy d’application. À l’aide de la procédure pour créer une configuration d’application Managed Browser, fournissez les paires clé/valeur suivantes :

| Clé                                                             | Valeur    |
|-----------------------------------------------------------------|----------|
| **com.microsoft.intune.mam.managedbrowser.AppProxyRedirection** | **true** |

Pour plus d’informations sur la manière d’utiliser conjointement Managed Browser et le proxy d’application Azure AD pour un accès transparent (et protégé) à des applications web locales, consultez le billet de blog Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access).

## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Comment configurer la page d’accueil de Managed Browser

Ce paramètre vous permet de configurer la page d’accueil que les utilisateurs voient quand ils démarrent Managed Browser ou créent un onglet. À l’aide de la procédure pour créer une configuration d’application Managed Browser, fournissez les paires clé/valeur suivantes :

|                                Clé                                |                                                           Valeur                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Spécifiez une URL valide. Les URL incorrectes sont bloquées par mesure de sécurité.<br>Exemple : `<https://www.bing.com>` |

## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Comment configurer des signets pour Managed Browser

Ce paramètre vous permet de configurer un ensemble de signets pour les utilisateurs de Managed Browser.

- Ces signets ne peuvent pas être supprimés ni modifiés par les utilisateurs
- Ces signets s’affichent en haut de la liste. Tous les signets créés par les utilisateurs sont affichés sous ces signets.
- Si vous avez activé la redirection de proxy d’application, vous pouvez ajouter des applications web de proxy d’application en utilisant leur URL interne ou externe.

À l’aide de la procédure pour créer une configuration d’application Managed Browser, fournissez les paires clé/valeur suivantes :

|                                Clé                                 |                                                                                                                                                                                                                                                         Valeur                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | La valeur de cette configuration est une liste de signets. Chaque signet comprend le titre et l’URL du signet. Séparez le titre et l’URL par le caractère <strong>&#124;</strong>.<br><br>Exemple :<br> `Microsoft Bing|https://www.bing.com`<br><br>To configure multiple bookmarks, separate each pair with the double character, <strong>&#124;&#124;</strong><br><br>Example:<br> `Bing|https://www.bing.com||Contoso|https://www.contoso.com` |

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Guide de spécification des URL autorisées et bloquées pour Managed Browser

À l’aide de la procédure pour créer une configuration d’application Managed Browser, fournissez les paires clé/valeur suivantes :

|Clé|Valeur|
|-|-|
|Choisissez parmi :<br><ul><li>Spécifier des URL autorisées (seules ces URL sont autorisées ; aucun autre site n’est accessible) :<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Spécifier des URL bloquées (tous les autres sites sont accessibles) :<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|La valeur correspondante pour la clé est une liste d’URL. Vous entrez toutes les URL que vous souhaitez autoriser ou bloquer comme des valeurs uniques, séparées par des barres verticales **&#124;**.<br><br>Exemples :<br><br>`URL1|URL2|URL3`<br>`http://*.contoso.com/*|https://*.bing.com/*|https://expenses.contoso.com`|

>[!IMPORTANT]
>Ne spécifiez pas les deux clés. Si les deux clés sont destinées au même utilisateur, la clé allow est utilisée parce qu’il s’agit de l’option la plus restrictive.
>En outre, évitez de bloquer des pages importantes, comme les sites web de votre entreprise.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Format des URL autorisées et des URL bloquées
Utilisez les informations suivantes pour en savoir plus sur les formats et les caractères génériques que vous pouvez utiliser pour spécifier des URL dans les listes bloquées et autorisées :

- Vous pouvez utiliser le caractère générique (**&#42;**) en fonction des règles de la liste des modèles autorisés ci-dessous :

- Veillez à faire précéder toutes les URL du préfixe **http** ou **https** quand vous les entrez dans la liste.

- Vous pouvez spécifier des numéros de port dans l'adresse. Si vous ne spécifiez pas un numéro de port, les valeurs suivantes sont utilisées :

  -   Port 80 pour http

  -   Port 443 pour https

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

-   Managed Browser n’utilise pas les paramètres que les utilisateurs définissent pour le navigateur intégré sur leur appareil. Managed Browser n’a pas accès à ces paramètres.

-   Si vous configurez l’option **Exiger un code confidentiel simple pour l’accès** ou **Exiger des informations d’identification d’entreprise pour l’accès** dans une stratégie de protection des applications associée à Managed Browser et qu’un utilisateur clique sur le lien d’aide de la page d’authentification, il peut accéder à n’importe quel site Internet, même si celui-ci a été ajouté à une liste rouge dans la stratégie.

-   Managed Browser peut uniquement bloquer l’accès aux sites lorsque l’utilisateur tente de les ouvrir directement. Il ne bloque pas l’accès quand des services intermédiaires (tels qu’un service de traduction) sont utilisés pour accéder au site.

-   Pour permettre l’authentification et accéder à la documentation d’Intune, le site **&#42;.microsoft.com** n’est pas soumis aux paramètres de liste verte ou rouge. Ce site est toujours autorisé.

### <a name="turn-off-usage-data"></a>Désactiver les données d’utilisation
Microsoft recueille automatiquement des données anonymes sur les performances et l’utilisation de Managed Browser pour améliorer les produits et services Microsoft. Les utilisateurs peuvent désactiver la collecte de données à l’aide du paramètre **Données d’utilisation** de leurs appareils. Vous n’avez aucun contrôle sur la collecte de ces données.


-   Sur les appareils iOS, les utilisateurs ne peuvent pas ouvrir les sites web possédant un certificat qui a expiré ou qui n’est pas approuvé.
-   Managed Browser n’utilise pas les paramètres que les utilisateurs définissent pour le navigateur intégré sur leur appareil. Managed Browser n’a pas accès à ces paramètres.

-   Si vous configurez l’option **Exiger un code confidentiel simple pour l’accès** ou **Exiger des informations d’identification d’entreprise pour l’accès** dans une stratégie de protection des applications associée à Managed Browser et qu’un utilisateur clique sur le lien d’aide de la page d’authentification, il peut accéder à n’importe quel site Internet, même si celui-ci a été ajouté à une liste rouge dans la stratégie.

-   Managed Browser peut uniquement bloquer l’accès aux sites lorsque l’utilisateur tente de les ouvrir directement. Il ne bloque pas l’accès quand des services intermédiaires (tels qu’un service de traduction) sont utilisés pour accéder au site.

-   Pour permettre l’authentification et accéder à la documentation d’Intune, le site **&#42;.microsoft.com** n’est pas soumis aux paramètres de liste verte ou rouge. Ce site est toujours autorisé.

### <a name="turn-off-usage-data"></a>Désactiver les données d’utilisation
Microsoft recueille automatiquement des données anonymes sur les performances et l’utilisation de Managed Browser pour améliorer les produits et services Microsoft. Les utilisateurs peuvent désactiver la collecte de données à l’aide du paramètre **Données d’utilisation** de leurs appareils. Vous n’avez aucun contrôle sur la collecte de ces données.

## <a name="next-steps"></a>Étapes suivantes

- [Que sont les stratégies de protection des applications ?](app-protection-policy.md) 
