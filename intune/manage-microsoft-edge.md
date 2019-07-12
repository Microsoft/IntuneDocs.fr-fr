---
title: Gérer l’accès web à l’aide de Microsoft Edge avec Microsoft Intune
titleSuffix: ''
description: Utilisez des stratégies de protection des applications Intune avec Microsoft Edge pour veiller à ce que les sites web d’entreprise soient toujours accessibles avec des dispositifs de protection en place.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 147547577615c6e74a9c5b3dd8b200ba387bad79
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67648463"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Gérer l’accès web à l’aide de Microsoft Edge avec Microsoft Intune

L’utilisation de stratégies de protection des applications Intune avec Microsoft Edge permet de veiller à ce que les sites web d’entreprise soient toujours accessibles avec des dispositifs de protection en place. Les fonctionnalités d’entreprise Microsoft Edge suivantes, activées par les stratégies Intune, sont disponibles :

- **Double identité.** Les utilisateurs peuvent ajouter à la fois un compte professionnel, mais aussi un compte personnel, pour la navigation. Il existe une séparation complète entre les deux identités, ce qui est similaire à l’architecture et à l’expérience proposées dans Microsoft Office 365 et Outlook. Les administrateurs Intune peuvent définir les stratégies souhaitées pour une expérience de navigation protégée au sein du compte professionnel.
- **Intégration d’une stratégie de protection des applications Intune.** Microsoft Edge étant intégré au Kit de développement logiciel (SDK) Intune, vous pouvez y cibler des stratégies de protection des applications afin d’éviter la perte de données. Ces fonctionnalités incluent le contrôle des opérations Copier, Couper et Coller, la prévention des captures d’écran et la vérification que les liens sélectionnés par les utilisateurs ne s’ouvrent que dans d’autres applications managées.
- **Intégration du Proxy Azure Application.** Vous pouvez contrôler l’accès aux applications SaaS (Software as a service) et applications web. Ceci permet de garantir que les applications basées sur le navigateur ne s’exécutent que dans le navigateur Microsoft Edge sécurisé, que les utilisateurs finaux se connectent à partir du réseau d’entreprise ou à partir d’Internet.
- **Configuration d’applications.** Vous pouvez utiliser les paramètres de configuration des applications pour renforcer la posture de sécurité de vos organisations et configurer des fonctionnalités faciles d’emploi pour vos utilisateurs finaux. Par exemple, vous pouvez définir des signets, un raccourci de page d’accueil, des sites autorisés/bloqués et un Proxy d’application Azure Active Directory (Azure AD).

Les stratégies de protection Microsoft Intune pour Microsoft Edge permettent de protéger les données et les ressources de votre organisation. L’utilisation de ces stratégies avec Microsoft Edge garantit que les ressources de votre entreprise sont protégées non seulement dans les applications installées en mode natif, mais aussi lors de l’accès via un navigateur web.

## <a name="getting-started"></a>Mise en route

Vous et vos utilisateurs finaux pouvez télécharger Microsoft Edge à partir des App Stores publics pour l’utiliser dans vos organisations. Les exigences relatives au système d’exploitation pour les stratégies de navigateur sont parmi les suivantes :
- Android 4 et versions ultérieures
- iOS 8.0 et versions ultérieures

## <a name="application-protection-policies-for-microsoft-edge"></a>Stratégies de protection des applications pour Microsoft Edge

Microsoft Edge étant intégré au Kit de développement logiciel (SDK) Intune, vous pouvez y appliquer des stratégies de protection des applications.

Vous pouvez appliquer ces paramètres :
- aux appareils inscrits auprès d’Intune ;
- aux appareils inscrits sur un autre produit de gestion des périphériques mobiles ;
- aux appareils non gérés.

Si Microsoft Edge n’est pas ciblé avec la stratégie Intune, les utilisateurs ne peuvent pas l’utiliser pour accéder aux données à partir d’autres applications managées par Intune telles que les applications Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Accès conditionnel pour Microsoft Edge

Vous pouvez utiliser l’accès conditionnel Azure AD pour rediriger vos utilisateurs vers du contenu d’entreprise uniquement par le biais de Microsoft Edge. Cela limite l’accès du navigateur mobile aux applications web connectées à Azure AD vers Microsoft Edge protégé par une stratégie. L’accès à partir de n’importe quel autre navigateur non protégé, comme Safari ou Chrome, est alors bloqué. Vous pouvez appliquer l’accès conditionnel aux ressources Azure comme Exchange Online et SharePoint Online, le Centre d’administration Microsoft 365 et même les sites locaux exposés aux utilisateurs externes par le biais du [Proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Pour obliger les applications web connectées à Azure AD à utiliser Microsoft Edge sur iOS et Android :
1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sous le nœud Intune, sélectionnez **Accès conditionnel** > **Nouvelle stratégie**.
3. Sélectionnez **Octroi** dans la section **Contrôles d’accès** du panneau.
4. Sélectionnez **Demander une application cliente approuvée**.
5. Choisissez **Sélectionner** dans le panneau **Octroi**. Cette stratégie doit être attribuée aux applications cloud à rendre accessibles uniquement pour l’application Intune Managed Browser.

    ![Capture d’écran de Stratégie d’accès conditionnel : octroi](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Dans la section Affectations, sélectionnez **Conditions** > **Applications clientes**. Le panneau **Applications clientes** s’affiche.
7. Sous **Configurer**, sélectionnez **Oui** pour appliquer la stratégie à des applications clientes spécifiques.
8. Vérifiez que **Browser** est sélectionné comme application cliente.

    ![Capture d’écran de Stratégie d’accès conditionnel : sélectionner des applications clientes](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Pour restreindre les applications natives (applications sans navigateur) qui peuvent accéder à ces applications cloud, vous pouvez également sélectionner **Applications mobiles et clients de bureau**.

9. Dans la section **Affectations**, sélectionnez **Utilisateurs et groupes**, puis choisissez les utilisateurs ou groupes à attribuer à cette stratégie.

    > [!NOTE]
    > Les utilisateurs doivent aussi être ciblés avec la stratégie Intune App Protection afin de recevoir des stratégies de configuration d’applications. Pour plus d’informations sur la création de stratégies de protection des applications Intune, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

10. Dans la section **Affectations**, sélectionnez **Applications cloud** pour choisir les applications à protéger avec cette stratégie.

Une fois la stratégie ci-dessus configurée, les utilisateurs sont obligés d’utiliser Microsoft Edge pour accéder aux applications web connectées à Azure AD que vous avez protégées avec cette stratégie. Si les utilisateurs essaient d’utiliser un navigateur non géré dans ce scénario, un message s’affiche pour les informer qu’ils doivent obligatoirement utiliser Microsoft Edge.

> [!TIP]
> L’accès conditionnel est une technologie Azure AD. Le nœud Accès conditionnel accessible à partir d’Intune est le même nœud que celui accessible à partir d’Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Authentification unique auprès des applications web connectées à Azure AD dans les navigateurs protégés par une stratégie

Microsoft Edge sur iOS et Android peut tirer parti de la fonctionnalité SSO (authentification unique) auprès de toutes les applications web (SaaS et locales) connectées à Azure AD. L’authentification unique permet aux utilisateurs d’accéder aux applications web connectées à Azure AD par le biais de Microsoft Edge sans avoir à retaper leurs informations d’identification.

Pour pouvoir utiliser l’authentification unique, votre appareil doit être inscrit par l’application Microsoft Authenticator sur iOS ou le Portail d’entreprise Intune sur Android. Lorsque les utilisateurs disposent de l’une de ces options, ils sont invités à inscrire leur appareil lorsqu’ils atteignent une application web connectées à Azure AD dans un navigateur protégé par une stratégie. (Cela est vrai uniquement si leur appareil n’a pas déjà été enregistré.) Une fois l’appareil inscrit avec le compte d’utilisateur géré par Intune, l’authentification unique est activée dans ce compte pour les applications web connectées à Azure AD.

> [!NOTE]
> L’inscription d’un appareil est un simple enregistrement auprès du service Azure AD. Il ne nécessite pas une inscription complète de l’appareil et ne donne au service informatique aucun autre privilège supplémentaire sur l’appareil.

## <a name="create-a-protected-browser-app-configuration"></a>Créer une configuration d’application de navigateur protégé

Pour les configurations d’application à appliquer, le navigateur protégé de l’utilisateur ou toute autre application sur l’appareil doit déjà être managé par la [stratégie de protection des applications Intune](app-protection-policy.md).

Pour créer la configuration d’application pour Microsoft Edge :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Applications clientes** > **Stratégies de configuration des applications** > **Ajouter**.
3. Dans le panneau **Ajouter une stratégie de configuration**, entrez un **Nom** et une **Description** facultative pour les paramètres de configuration de l’application.
4. Pour **Inscription de l’appareil**, choisissez **Applications gérées**.
5. Choisissez **Sélectionner l’application requise**. Puis, sur le panneau **Applications ciblées** choisissez **Managed Browser** ou **Edge** pour iOS, Android ou les deux.
6. Sélectionnez **OK** pour revenir au panneau **Ajouter une stratégie de configuration**.
7. Sélectionnez **Paramètres de configuration**. Dans le panneau **Configuration**, vous définissez des paires clé-valeur pour fournir des configurations pour Microsoft Edge. Consultez les sections plus bas dans cet article pour en savoir plus sur les différentes paires clé/valeur que vous pouvez définir.

    > [!NOTE]
    > Microsoft Edge utilise les mêmes paires clé/valeur que Managed Browser. 

8. Une fois ces opérations effectuées, sélectionnez **OK**.
9. Dans le panneau **Ajouter une stratégie de configuration**, choisissez **Ajouter**.<br>
    La nouvelle configuration est créée et s’affiche dans le panneau **Configuration des applications**.

## <a name="assign-the-configuration-settings-you-created"></a>Affecter les paramètres de configuration que vous avez créés 

Vous attribuez les paramètres à des groupes d’utilisateurs dans Azure AD. Si cet utilisateur a installé l’application de navigateur protégé ciblée, cette dernière est gérée par les paramètres que vous avez spécifiés.

1. Dans le panneau **Applications clientes** du tableau de bord de gestion des applications mobiles Intune, sélectionnez **Stratégies de configuration des applications**.
2. Dans la liste de configurations de l’application, sélectionnez celle que vous souhaitez affecter.
3. Dans le panneau suivant, sélectionnez **Affectations**.
4. Dans le panneau **Affectations**, sélectionnez le groupe Azure AD auquel vous voulez attribuer la configuration d’application, puis sélectionnez **OK**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Diriger les utilisateurs vers Microsoft Edge plutôt que vers Intune Managed Browser 

Intune Managed Browser et Microsoft Edge peuvent tous les deux être utilisés en tant que navigateurs protégés par une stratégie. Pour veiller à ce que vos utilisateurs soient dirigés vers l’utilisation de l’application du navigateur approprié, ciblez toutes vos applications managées par Intune (par exemple, Outlook, OneDrive et SharePoint) avec le paramètre de configuration suivant :

|    Clé    |    Valeur    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    La valeur `true` dirige vos utilisateurs vers le téléchargement et l’utilisation de Microsoft Edge.<br>La valeur `false` autorise vos utilisateurs à utiliser Intune Managed Browser.    |

Si cette valeur de configuration d’application **n’est pas** définie, la logique suivante définit le navigateur utilisé pour ouvrir des liens d’entreprise.

Sous Android :
- Si un utilisateur a téléchargé Intune Managed Browser et Microsoft Edge sur son appareil, c’est Intune Managed Browser qui est lancé. 
- Microsoft Edge est lancé si seul Microsoft Edge est téléchargé sur l’appareil et s’il est ciblé par la stratégie Intune.
- Managed Browser est lancé si seul Managed Browser est présent sur l’appareil et s’il est ciblé par la stratégie Intune.

Sur iOS, pour les applications qui intègrent le SDK Intune pour iOS v. 9.0.9+:
- Intune Managed Browser est lancé si Microsoft Edge et Managed Browser sont présents sur l’appareil.  
- Microsoft Edge est lancé si seul Microsoft Edge est présent sur l’appareil et s’il est ciblé par la stratégie Intune.
- Managed Browser est lancé si seul Managed Browser est présent sur l’appareil et s’il est ciblé par la stratégie Intune.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Configurer des paramètres du Proxy d’application pour Microsoft Edge

Vous pouvez utiliser Microsoft Edge et le [Proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) ensemble pour permettre aux utilisateurs d’accéder à des sites intranet sur leurs appareils mobiles. 

Voici quelques exemples de scénarios possibles avec la fonctionnalité Proxy d’application Azure AD activée : 

- Un utilisateur utilise l’application mobile Outlook, protégée par Intune. Il clique alors sur un lien vers un site intranet dans un e-mail et Microsoft Edge détecte que ce site intranet a été exposé à l’utilisateur par le biais du Proxy d’application. L’utilisateur est automatiquement acheminé par le biais du Proxy d’application, pour s’authentifier avec n’importe quelle authentification multifacteur applicable et l’accès conditionnel avant d’atteindre le site intranet. L’utilisateur peut à présent accéder à des sites internes, même sur ses appareils mobiles et le lien dans Outlook fonctionne comme prévu.
- Un utilisateur ouvre Microsoft Edge sur son appareil iOS ou Android. Si Microsoft Edge est protégé avec Intune, et que le proxy d’application est activé, l’utilisateur peut atteindre un site intranet à l’aide de l’URL interne à laquelle il est habitué. Microsoft Edge reconnaît que ce site intranet a été exposé à l’utilisateur via le Proxy d’application. L’utilisateur est automatiquement acheminé via le Proxy d’application, pour s’authentifier avant d’atteindre le site intranet. 

### <a name="before-you-start"></a>Avant de commencer

- Configurez vos applications internes à l’aide du Proxy d’application Azure AD.
    - Pour configurer le proxy d’application et publier des applications, consultez la [documentation d’installation](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- Une [stratégie de protection des applications Intune](app-protection-policy.md) doit être attribuée à l’application Microsoft Edge.

> [!NOTE]
> La mise à jour des données de redirection du proxy d’application dans Managed Browser et Microsoft Edge peut prendre jusqu’à 24 heures.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>Étape 1 : Activer la redirection automatique vers Microsoft Edge à partir d’Outlook
Configurez Outlook avec une stratégie de protection des applications qui active le paramètre **Partager du contenu web avec des navigateurs managés par une stratégie**.

![Capture d’écran de Stratégie de protection des applications : partager du contenu web avec des navigateurs managés par une stratégie](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Étape 2 : Définir le paramètre de configuration d’application pour activer le proxy d’application
Ciblez Microsoft Edge avec la paire clé-valeur suivante pour activer le Proxy d’application pour Microsoft Edge :

|    Clé    |    Valeur    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Pour plus d’informations sur la manière d’utiliser conjointement Microsoft Edge et le Proxy d’application Azure AD pour un accès fluide (et protégé) aux applications web locales, consultez [Meilleurs ensemble : Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access). Ce billet de blog fait référence à Intune Managed Browser, mais le contenu s’applique également à Microsoft Edge.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Configurer un raccourci de page d’accueil pour Microsoft Edge

Ce paramètre vous permet de configurer un raccourci de page d’accueil pour Microsoft Edge. Le raccourci de page d’accueil que vous configurez apparaît sous forme du premier icône sous la barre de recherche à l’ouverture par l’utilisateur d’un nouvel onglet dans Microsoft Edge. L’utilisateur ne peut pas modifier ni supprimer ce raccourci dans son contexte managé. Le raccourci de la page d’accueil affiche le nom de votre organisation pour la distinguer. 

Utilisez la paire clé-valeur suivante pour configurer un raccourci de page d’accueil :

|    Clé    |    Valeur    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Spécifiez une URL valide. Les URL incorrectes sont bloquées par mesure de sécurité.<br>**Exemple :**  <`https://www.bing.com`>
    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Configurer des signets managés pour Microsoft Edge

Pour une plus grande facilité d’accès, vous pouvez configurer les signets que vous souhaitez que vos utilisateurs aient à leur disposition quand ils utilisent Microsoft Edge. 

Voici plus de détails :

- Ces signets apparaissent uniquement pour les utilisateurs lorsqu’ils utilisent le mode entreprise de Microsoft Edge. 
- Ces signets ne peuvent pas être supprimés ni modifiés par les utilisateurs.
- Ces signets s’affichent en haut de la liste. Tous les signets créés par les utilisateurs sont affichés sous ces signets.
- Si vous avez activé la redirection du Proxy d’application, vous pouvez ajouter des applications web du Proxy d’application en utilisant leur URL interne ou externe.

Pour configurer des signets managés, utilisez la paire clé-valeur suivante :

|    Clé    |    Valeur    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    La valeur pour cette configuration est une liste de signets. Chaque signet comprend le titre et l’URL du signet. Séparez le titre et l’URL par le caractère `|`.      Exemple :<br>`Microsoft Bing|https://www.bing.com`<br>Pour configurer plusieurs signets, séparez chaque paire par deux caractères `||`.<p>Exemple :<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Afficher MyApps dans les signets Microsoft Edge

Par défaut, vos utilisateurs voient les sites MyApps configurés pour eux dans un dossier situés dans les signets Microsoft Edge. Ce dossier porte le nom de votre organisation.

|    Clé    |    Valeur    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** présente MyApps dans les signets Microsoft Edge.<p>**False** masque MyApps dans Microsoft Edge.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Spécifier la liste des sites autorisés ou bloqués pour Microsoft Edge
Vous pouvez utiliser la configuration des applications pour définir les sites auxquels vos utilisateurs peuvent accéder avec leur profil professionnel. Si vous utilisez une liste autorisée, vos utilisateurs peuvent uniquement accéder aux sites que vous avez explicitement répertoriés. Si vous utilisez une liste de sites bloqués, vos utilisateurs peuvent accéder à tous les sites, sauf à ceux que vous avez explicitement bloqués. Vous devez uniquement imposer une liste de sites autorisés ou une liste de sites bloqués, pas les deux. Si vous imposez les deux à la fois, la liste des sites autorisés est honorée.  

Vous pouvez utiliser les paires clé-valeur suivantes pour configurer une liste de sites autorisés ou une liste de sites bloqués pour Microsoft Edge. 

|    Clé    |    Valeur    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Choisissez parmi :<p>1. Spécifier des URL autorisées (seules ces URL sont autorisées ; aucun autre site n’est accessible) :<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Spécifier des URL bloquées (tous les autres sites sont accessibles) :<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    La valeur correspondante pour la clé est une liste d’URL. Vous entrez toutes les URL que vous souhaitez autoriser ou bloquer comme des valeurs uniques, séparées par des barres verticales `|`.<br>**Exemples :**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Format des URL dans les listes de sites autorisés et bloqués 
Vous pouvez utiliser divers formats d’URL pour créer vos listes de sites autorisés/bloqués. Ces modèles autorisés sont détaillés dans le tableau ci-dessous. Quelques remarques avant de commencer : 
- Veillez à faire précéder toutes les URL du préfixe **http** ou **https** quand vous les entrez dans la liste.
- Vous pouvez utiliser le caractère générique (\*) en fonction des règles de la liste des modèles autorisés, ci-dessous.
- Un caractère générique peut uniquement correspondre à un composant entier d’un nom d’hôte (séparés par des points) ou à des portions entières d’un chemin (séparées par des barres obliques). Par exemple, `http://*contoso.com` **n’est pas** pris en charge.
- Vous pouvez spécifier des numéros de port dans l'adresse. Si vous ne spécifiez pas un numéro de port, les valeurs suivantes sont utilisées :
    - Port 80 pour http
    - Port 443 pour https
- L’utilisation de caractères génériques n’est **pas** prise en charge pour les numéros de port. Par exemple, `http://www.contoso.com:*` et `http://www.contoso.com:*/` ne sont pas pris en charge. 

    |    Adresse URL    |    Détails    |    Correspond à    |    Ne correspond pas à    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Correspond à une page unique    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Correspond à une page unique    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    Correspond à toutes les URL commençant par `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Correspond à tous les sous-domaines sous `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    Correspond à un dossier unique    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Correspond à une page unique, par le biais de l’utilisation d’un numéro de port    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Correspond à une page unique sécurisée    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Correspond à un dossier unique et à tous ses sous-dossiers    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Voici quelques exemples d’entrées que vous ne pouvez pas spécifier :
    - `*.com`
    - `*.contoso/*`
    - `www.contoso.com/*images`
    - `www.contoso.com/*images*pigs`
    - `www.contoso.com/page*`
    - Adresses IP
    - `https://*`
    - `http://*`
    - `https://*contoso.com`
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="define-behavior-when-users-try-to-access-a-blocked-site"></a>Définir le comportement quand des utilisateurs essaient d’accéder à un site bloqué

Avec le modèle à double identité intégré à Microsoft Edge, vous pouvez rendre l’expérience plus flexible pour vos utilisateurs finaux, ce qui n’était pas possible avec Intune Managed Browser. Lorsque les utilisateurs atteignent un site bloqué dans Microsoft Edge, vous pouvez les inviter à ouvrir le lien dans leur contexte personnel plutôt que dans leur contexte professionnel. Cela leur permet de rester protégés, tout en conservant les ressources d’entreprise sécurisées. Par exemple, si un lien vers un article d’actualité est envoyé à un utilisateur via Outlook, ils peuvent ouvrir le lien dans leur contexte personnel ou dans un onglet InPrivate. Leur contexte professionnel n’autorise pas de sites web d’actualité. Par défaut, ces transitions sont autorisées.

Utilisez la paire clé-valeur ci-dessous pour configurer l’autorisation de ces transitions douces ou pas :

|    Clé    |    Valeur    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** autorise Microsoft Edge à effectuer une transition vers le contexte personnel des utilisateurs pour qu’ils puissent ouvrir des sites bloqués.<p>**Bloc** empêche la transition des utilisateurs par Microsoft Edge. Les utilisateurs reçoivent simplement un message indiquant que le site auquel ils tentent d’accéder est bloqué.    |

## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Utiliser Microsoft Edge sur iOS pour accéder aux journaux des applications managées 

Les utilisateurs finaux ayant installé Microsoft Edge sur leurs appareils iOS peuvent afficher l’état de gestion de toutes les applications Microsoft publiées. Ils peuvent envoyer des journaux afin de dépanner leurs applications iOS gérées. Voici comment procéder :
1. Ouvrez Microsoft Edge sur votre appareil iOS.
2. Tapez `about:intunehelp` dans la zone d’adresse. 
3. Microsoft Edge démarre en mode Résolution des problèmes.

Vous trouverez la liste des paramètres stockés dans les journaux d’applications sur la page [Consulter les journaux de protection des applications dans Managed Browser](app-protection-policy-settings-log.md).

Pour voir comment afficher des journaux sur des appareils Android, consultez [Envoyer des journaux à votre administrateur informatique par e-mail](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Sécurité et confidentialité pour Microsoft Edge

Voici d’autres considérations relatives à la sécurité et à la confidentialité pour Microsoft Edge :

- Microsoft Edge ne consomme pas de paramètres que les utilisateurs définissent pour le navigateur natif sur leurs appareils, car Microsoft Edge ne peut pas accéder à ces paramètres.
- Vous pouvez configurer l’option **Exiger un code confidentiel simple pour l’accès** ou **Exiger des informations d’identification d’entreprise pour l’accès** dans une stratégie de protection d’application associée à Microsoft Edge. Si un utilisateur sélectionne le lien d’aide sur la page d’authentification, il peut rechercher tous les sites internet, qu’ils aient été ajoutés ou pas à une liste bloquée dans la stratégie.
- Microsoft Edge peut uniquement bloquer l’accès aux sites lorsque l’utilisateur tente de les ouvrir directement. Il ne bloque pas l’accès lorsque des utilisateurs utilisent des services intermédiaires (tels qu’un service de traduction) pour accéder au site.
- Pour permettre l’authentification et accéder à la documentation Intune, le site * **.microsoft.com** n’est pas soumis aux paramètres de liste verte ou rouge. Il est toujours autorisé.
- Les utilisateurs peuvent désactiver la collecte de données. Microsoft recueille automatiquement des données anonymes sur les performances et l’utilisation de Managed Browser pour améliorer les produits et services Microsoft. Les utilisateurs peuvent désactiver la collecte de données à l’aide du paramètre **Données d’utilisation** de leurs appareils. Vous n’avez aucun contrôle sur la collecte de ces données. Sur les appareils iOS, les sites web visités par les utilisateurs possédant un certificat qui a expiré ou qui n’est pas approuvé ne peuvent pas être ouverts.

## <a name="next-steps"></a>Étapes suivantes

- [Que sont les stratégies de protection des applications ?](app-protection-policy.md) 
