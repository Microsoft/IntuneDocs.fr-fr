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
ms.openlocfilehash: c1a255391a2cf27a764da6122031fd0c9cbb64cf
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751357"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>Gérer l’accès web à l’aide de Microsoft Edge avec Microsoft Intune

L’utilisation de stratégies de protection des applications Intune avec Microsoft Edge permet de veiller à ce que les sites web d’entreprise soient toujours accessibles avec des dispositifs de protection en place. Les fonctionnalités d’entreprise Microsoft Edge suivantes, activées par les stratégies Intune, sont disponibles. Ces fonctionnalités d’entreprise comprennent :

1.  **Double identité** : les utilisateurs peuvent ajouter à la fois un compte professionnel, mais aussi un compte personnel, pour la navigation. Il existe une séparation complète entre les deux identités, ce qui est similaire à l’architecture et à l’expérience proposées dans Microsoft Office 365 et Outlook. Les administrateurs Intune pourront définir les stratégies souhaitées pour une expérience de navigation protégée au sein du compte professionnel.
2.  **Intégration des stratégies de protection des applications Intune** : dans la mesure où Microsoft Edge est intégré au SDK Intune, vous pouvez cibler des stratégies de protection des applications pour garantir une protection contre la perte de données. Ces fonctionnalités incluent le contrôle des opérations Copier, Couper et Coller, la prévention des captures d’écran et la vérification que les liens sélectionnés par les utilisateurs ne s’ouvrent que dans d’autres applications gérées.
3.  **Intégration des proxys Azure Application** : vous pouvez contrôler l’accès aux applications SaaS et web, afin de garantir que les applications basées sur le navigateur ne s’exécuteront que dans le navigateur Microsoft Edge sécurisé, que les utilisateurs finaux se connectent à partir du réseau d’entreprise ou à partir d’Internet.
4.  **Configuration des applications** : vous pouvez exploiter les paramètres de configuration des applications pour renforcer la posture de sécurité de vos organisations et configurer des fonctionnalités de facilité d’emploi pour vos utilisateurs finaux. Par exemple, vous pouvez définir des signets, un raccourci de page d’accueil, des sites autorisés/bloqués, un proxy Azure Application, etc.
Les stratégies de protection Microsoft Intune pour Microsoft Edge permettent de protéger les données et les ressources de votre organisation. L’utilisation de ces stratégies avec Microsoft Edge garantit que les ressources de votre entreprise sont protégées non seulement dans les applications installées en mode natif, mais aussi lors de l’accès via un navigateur web.

## <a name="getting-started"></a>Mise en route

Vous et vos utilisateurs finaux pouvez télécharger Microsoft Edge à partir des App Stores publics pour l’utiliser dans vos organisations. Configuration requise du système d’exploitation pour les stratégies de navigateur :
- Android 4 et ultérieur ou
- iOS 8.0 et versions ultérieures

## <a name="application-protection-policies-for-microsoft-edge"></a>Stratégies de protection des applications pour Microsoft Edge

Microsoft Edge étant intégré au SDK Intune, vous pouvez y appliquer des stratégies de protection des applications, notamment :
- Contrôle de l’utilisation des fonctions Copier, Couper et Coller.
- Blocage des captures d’écran.
- Garantie que les liens d’entreprise s’ouvrent uniquement dans les applications et les navigateurs gérés.

Pour plus d’informations, consultez Que sont les stratégies de protection des applications ?
Vous pouvez appliquer ces paramètres :
- aux appareils inscrits auprès d’Intune ;
- aux appareils inscrits auprès d’un autre produit MDM ;
- aux appareils qui ne sont pas gérés.

Si Microsoft Edge n’est pas ciblé avec la stratégie Intune, les utilisateurs ne peuvent pas l’utiliser pour accéder aux données à partir d’autres applications gérées par Intune telles que les applications Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Accès conditionnel pour Microsoft Edge

Vous pouvez exploiter l’accès conditionnel Azure AD pour rediriger vos utilisateurs vers du contenu d’entreprise uniquement par le biais de Microsoft Edge. Vous restreignez ainsi l’accès par navigateur mobile pour les applications web connectées à Azure AD à Microsoft Edge protégé par des stratégies. L’accès à partir de tout autre navigateur non protégé, comme Safari ou Chrome est alors bloqué. L’accès conditionnel est applicable aux ressources Azure comme Exchange Online et SharePoint Online, le Centre d’administration Microsoft 365, et même les sites locaux exposés aux utilisateurs externes par le biais du [proxy d’application Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Pour obliger les applications web connectées à AD Azure à utiliser Microsoft Edge sur iOS et Android, effectuez les étapes ci-dessous :
1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sous le nœud Intune, sélectionnez **Accès conditionnel** > **Nouvelle stratégie**.
3. Ensuite, sélectionnez **Accorder** à partir de la section **Contrôles d’accès** du panneau.
4. Cliquez sur **Demander une application cliente approuvée**.
5. Cliquez sur **Sélectionner** dans le panneau **Accorder**. Cette stratégie doit être attribuée aux applications cloud à rendre accessibles uniquement pour l’application Intune Managed Browser.

    ![Stratégie d’accès conditionnel : octroyer](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Dans la section Affectations, sélectionnez Conditions > Applications clientes. Le panneau Applications clientes s’affiche.
7. Cliquez sur Oui sous Configurer pour appliquer la stratégie à des applications clientes spécifiques.
8. Vérifiez que Browser est sélectionné comme application cliente.

    ![Stratégie d’accès conditionnel : sélectionner des applications clientes](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Pour restreindre les applications natives (applications sans navigateur) qui peuvent accéder à ces applications cloud, vous pouvez également sélectionner **Applications mobiles et clients de bureau**.

9. Dans la section **Affectations**, sélectionnez **Utilisateurs et groupes**, puis choisissez les utilisateurs ou groupes à affecter à cette stratégie.

    > [!NOTE]
    > Les utilisateurs doivent aussi être ciblés avec la stratégie Intune App Protection afin de recevoir des stratégies de configuration d’applications. Pour plus d’informations sur la création de stratégies Intune App Protection, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

10. Dans la section **Affectations**, sélectionnez **Applications cloud** pour choisir les applications à protéger avec cette stratégie.

Une fois que la stratégie ci-dessus est configurée, les utilisateurs sont obligés d’utiliser Microsoft Edge pour accéder aux applications web connectées à Azure AD que vous avez protégées avec cette stratégie. Si les utilisateurs essaient d’utiliser un navigateur non géré dans ce scénario, un message s’affiche pour les informer qu’ils doivent utiliser Microsoft Intune.

> [!TIP]
> L’accès conditionnel est une technologie Azure Active Directory (Azure AD). Le nœud Accès conditionnel accessible à partir d’Intune est le même nœud que celui accessible à partir d’Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Authentification unique auprès des applications web connectées à Azure AD dans les navigateurs protégés par une stratégie

Microsoft Edge sur iOS et Android peut tirer parti de la fonctionnalité SSO (authentification unique) auprès de toutes les applications web (SaaS et locales) connectées à Azure AD. L’authentification unique permet aux utilisateurs d’accéder aux applications web connectées à AD Azure par le biais de Microsoft Edge sans avoir à retaper leurs informations d’identification.

Pour pouvoir utiliser l’authentification unique, votre appareil doit être inscrit par l’application Microsoft Authenticator sur iOS ou le Portail d’entreprise Intune sur Android. Quand les utilisateurs disposent de l’application Authenticator ou Portail d’entreprise Intune, ils sont invités à inscrire leur appareil quand ils accèdent à une application web connectée à Azure AD dans un navigateur protégé par une stratégie, si ce dernier n’est pas déjà inscrit. Une fois que l’appareil est inscrit avec le compte d’utilisateur géré par Intune, l’authentification unique est activée dans ce compte pour les applications web connectées à Azure AD.

> [!NOTE]
> L’inscription d’un appareil est un simple enregistrement auprès du service Azure AD. Elle ne nécessite pas une inscription complète et ne donne aucun autre privilège supplémentaire sur l’appareil.

## <a name="create-a-protected-browser-app-configuration"></a>Créer une configuration d’application de navigateur protégé

Pour les configurations d’application à appliquer, le navigateur protégé de l’utilisateur ou une autre application sur l’appareil doivent déjà être gérés par la [stratégie de protection des applications Intune](app-protection-policy.md).

Les étapes suivantes permettent de créer une configuration d’application de navigateur protégé :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Applications clientes** > **Stratégies de configuration des applications** > **Ajouter**.
3. Dans le panneau **Ajouter une stratégie de configuration**, entrez un **Nom** et une **Description** facultative pour les paramètres de configuration de l’application.
4. Pour **Inscription de l’appareil**, choisissez **Applications gérées**.
5. Choisissez **Sélectionner l’application requise** puis, dans le panneau **Applications ciblées**, choisissez **Managed Browser**, **Edge** ou les deux, pour iOS, Android ou les deux.
6. Choisissez **OK** pour revenir au panneau **Ajouter une stratégie de configuration**.
7. Choisissez **Paramètres de configuration**. Dans le panneau **Configuration**, vous définissez des paires clé-valeur pour fournir des configurations pour Microsoft Edge. Consultez les sections plus bas dans cet article pour en savoir plus sur les différentes paires clé/valeur que vous pouvez définir.

    > [!NOTE]
    > Microsoft Edge utilise les mêmes paires clé/valeur que Managed Browser. 

8.  Une fois terminé, cliquez sur **OK**.
9.  Dans le panneau **Ajouter une stratégie de configuration**, choisissez **Ajouter**.<br>
    La nouvelle configuration est créée et s’affiche dans le panneau **Configuration des applications**.

## <a name="assign-the-configuration-settings-you-created"></a>Affecter les paramètres de configuration que vous avez créés 

Vous affectez les paramètres à des groupes d’utilisateurs Azure AD. Si cet utilisateur a installé l’application de navigateur protégé ciblée, cette dernière est gérée par les paramètres que vous avez spécifiés.

1. Dans le panneau **Applications clientes** du tableau de bord de gestion des applications mobiles Intune, choisissez **Stratégies de configuration des applications**.
2. Dans la liste de configurations de l’application, sélectionnez celle que vous souhaitez affecter.
3. Dans le panneau suivant, choisissez **Affectations**.
4. Dans le panneau **Affectations**, sélectionnez le groupe Azure AD auquel vous voulez affecter la configuration d’application, puis choisissez **OK**.

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Configurer des paramètres de proxy d’application pour les navigateurs protégés

Microsoft Edge et la fonctionnalité [Proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) peuvent être utilisés ensemble pour permettre aux utilisateurs d’accéder à des sites intranet sur leurs appareils mobiles. 

Voici quelques exemples de scénarios possibles avec la fonctionnalité Proxy d’application AD : 

- Un utilisateur utilise l’application mobile Outlook, protégée par Intune. Il clique ur un lien vers un site intranet dans un e-mail et Microsoft Edge détecte que ce site intranet a été exposé à l’utilisateur par le biais du proxy d’application. L’utilisateur est automatiquement routé par le biais du proxy d’application, pour s’authentifier avec n’importe quelle authentification multifacteur applicable et l’accès conditionnel avant d’atteindre le site intranet. L’utilisateur peut à présent accéder à des sites internes même sur ses appareils mobiles, et le lien dans Outlook fonctionne comme prévu.
- Un utilisateur ouvre Microsoft Edge sur son appareil iOS ou Android. Si Microsoft Edge est protégé avec Intune, et que le proxy d’application est activé, l’utilisateur peut accéder à un site intranet à l’aide de l’URL interne à laquelle il est habitué. Microsoft Edge détecte que ce site intranet a été exposé à l’utilisateur par le biais du proxy d’application et l’utilisateur est automatiquement routé par le biais du proxy d’application, pour s’authentifier avant d’atteindre le site intranet. 

### <a name="before-you-start"></a>Avant de commencer

- Configurez vos applications internes à l’aide du proxy d’application Azure AD.
    - Pour configurer le proxy d’application et publier des applications, consultez la [documentation d’installation](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- Une [stratégie de protection des applications Intune ](app-protection-policy.md) doit être affectée à l’application Microsoft Edge.

> [!NOTE]
> La mise à jour des données de redirection du proxy d’application dans Managed Browser et Microsoft Edge peut prendre jusqu’à 24 heures.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Étape 1 : Activer la redirection automatique vers un navigateur protégé à partir d’Outlook
Outlook doit être configuré avec une stratégie de protection des applications qui active le paramètre **Partager du contenu web avec des navigateurs gérés par stratégie**.

![Stratégie de protection des applications : partager du contenu web avec des navigateurs gérés par stratégie](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Étape 2 : Définir le paramètre de configuration d’application pour activer le proxy d’application
Ciblez Microsoft Edge avec la paire clé-valeur ci-dessous pour activer le proxy d’application pour Microsoft Edge :

|    Clé    |    Valeur    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Pour plus d’informations sur la manière d’utiliser conjointement Microsoft Edge et la fonctionnalité Proxy d’application Azure AD pour un accès fluide (et protégé) aux applications web locales, consultez le billet de blog Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access). Ce billet de blog fait référence à Intune Managed Browser, mais le contenu s’applique également à Microsoft Edge.

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>Comment configurer un raccourci de page d’accueil pour Microsoft Edge

Ce paramètre vous permet de configurer un raccourci de page d’accueil pour Microsoft Edge.  Le raccourci de page d’accueil que vous configurez apparaît en premier sous forme d’icône sous la barre de recherche à l’ouverture d’un nouvel onglet dans Microsoft Edge. L’utilisateur ne peut pas modifier ni supprimer ce raccourci dans son contexte managé. Le raccourci de la page d’accueil affiche le nom de votre organisation pour le distinguer. 

Utilisez la paire clé-valeur pour ci-dessous pour configurer un raccourci de page d’accueil :

|    Clé    |    Valeur    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Spécifiez une URL valide. Les URL incorrectes sont bloquées par mesure de sécurité.<br>**Exemple :** `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>Comment configurer des signets managés pour Microsoft Edge

Pour une plus grande facilité d’accès, vous pouvez configurer les signets que vous souhaitez que vos utilisateurs aient à leur disposition quand ils utilisent Microsoft Edge. Voici plus de détails :

- Ces signets apparaissent uniquement pour les utilisateurs quand ils utilisent le mode entreprise de Microsoft Edge. 
- Ces signets ne peuvent pas être supprimés ni modifiés par les utilisateurs.
- Ces signets s’affichent en haut de la liste. Tous les signets créés par les utilisateurs sont affichés sous ces signets.
- Si vous avez activé la redirection de proxy d’application, vous pouvez ajouter des applications web de proxy d’application en utilisant leur URL interne ou externe.

Pour configurer des signets managés, utilisez la paire clé-valeur suivante :

|    Clé    |    Valeur    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    La valeur pour cette configuration est une liste de signets. Chaque signet comprend le titre et l’URL du signet. Séparez le titre et l’URL par le caractère `|`.      **Exemple :**<br>`Microsoft Bing|https://www.bing.com`<p>Pour configurer plusieurs signets, séparez chaque paire par deux caractères `||`.<p>**Exemple :**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>Comment afficher MyApps dans les signets Microsoft Edge

Par défaut, vos utilisateurs voient les sites MyApps configurés pour eux dans un dossier situés dans les signets Microsoft Edge. Ce dossier porte le nom de votre organisation.

|    Clé    |    Valeur    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** présente MyApps dans les signets Microsoft Edge.<p>**False** masque MyApps dans Microsoft Edge.    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Comment spécifier la liste des sites autorisés ou bloqués pour Microsoft Edge
Vous pouvez utiliser la configuration des applications pour définir les sites auxquels vos utilisateurs peuvent accéder avec leur profil professionnel. Si vous utilisez une liste de sites autorisés, vos utilisateurs peuvent uniquement accéder aux sites que vous avez explicitement listés. Si vous utilisez une liste de sites bloqués, vos utilisateurs peuvent accéder à tous les sites, sauf à ceux que vous avez explicitement bloqués. Vous devez uniquement imposer une liste de sites autorisés ou une liste de sites bloqués, pas les deux. Si les deux sont ciblées sur l’appareil, la liste de sites autorisés est respectée.  

Vous pouvez utiliser les paires clé-valeur ci-dessous pour configurer une liste de sites autorisés ou une liste de sites bloqués pour Microsoft Edge. Poursuivez votre lecture pour plus d’informations sur les formats d’URL valides. 

|    Clé    |    Valeur    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Choisissez parmi :<p>1. Spécifier des URL autorisées (seules ces URL sont autorisées ; aucun autre site n’est accessible) :<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Spécifier des URL bloquées (tous les autres sites sont accessibles) :<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    La valeur correspondante pour la clé est une liste d’URL. Vous entrez toutes les URL que vous souhaitez autoriser ou bloquer comme des valeurs uniques, séparées par des barres verticales `|`.<p>**Exemples :**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Format des URL dans les listes de sites autorisés et bloqués 
Vous pouvez utiliser divers formats d’URL pour créer vos listes de sites autorisés/bloqués. Ces modèles autorisés sont détaillés dans le tableau ci-dessous. Quelques remarques avant de commencer : 
- Veillez à faire précéder toutes les URL du préfixe **http** ou **https** quand vous les entrez dans la liste.
- Vous pouvez utiliser le caractère générique (*) en fonction des règles de la liste des modèles autorisés, ci-dessous.
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
    |    `http://www.contoso.com:80`    |    Correspond à une page unique, par le biais de l’utilisation d’un numéro de port    |    http://www.contoso.com:80    |         |
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
    - `http://www.contoso.com:*`
    - `http://www.contoso.com: /*`
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>Définition du comportement quand des utilisateurs essaient d’accéder à un site bloqué

Avec le modèle à double identité intégré à Microsoft Edge, vous pouvez rendre l’expérience plus flexible pour vos utilisateurs finaux, ce qui n’était pas possible avec Intune Managed Browser. Quand des utilisateurs accèdent à un site bloqué dans Microsoft Edge, ils peuvent être invités à ouvrir le lien dans leur contexte personnel plutôt que leur contexte professionnel, ce qui leur permet de rester protégé, tout en maintenant sécurisées les ressources d’entreprise. Par exemple, si un utilisateur reçoit un lien vers un article d’actualités par le biais de son Outlook, il est en mesure d’ouvrir le lien dans son contexte personnel ou sous un onglet InPrivate plutôt que dans son contexte professionnel, qui n’autorise pas les sites web d’actualités. Par défaut, ces transitions sont autorisées.

Utilisez la paire clé-valeur ci-dessous pour configurer ou non l’autorisation de ces transitions douces :

|    Clé    |    Valeur    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** autorise Microsoft Edge à effectuer une transition vers le contexte personnel des utilisateurs pour qu’ils puissent ouvrir des sites bloqués.<p>**Block** empêche Microsoft Edge d’effectuer une transition pour les utilisateurs. Ces derniers reçoivent simplement un message stipulant que le site auquel ils essaient d’accéder est bloqué.    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Diriger les utilisateurs vers Microsoft Edge au lieu d’Intune Managed Browser 

Intune Managed Browser et Microsoft Edge sont à présent tous les deux utilisables en tant que navigateurs protégés par stratégie. Pour veiller à ce que vos utilisateurs soient dirigés vers l’utilisation du navigateur approprié, cibler toutes vos applications gérées par Intune (par exemple, Outlook et OneDrive) avec le paramètre de configuration suivant :

|    Clé    |    Valeur    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    La valeur `true` dirige vos utilisateurs vers l’utilisation de Microsoft Edge.<p>La valeur `false` dirige vos utilisateurs vers l’utilisation d’Intune Managed Browser.    |

Si cette valeur de configuration d’application n’est pas définie, la logique suivante définit le navigateur utilisé pour ouvrir des liens d’entreprise.

Sous Android :
- Si l’utilisateur a téléchargé Intune Managed Browser et Microsoft Edge sur son appareil, c’est Intune Managed Browser qui est lancé. 
- Microsoft Edge s’ouvre s’il est téléchargé sur l’appareil et s’il est ciblé par la stratégie Intune.
- Managed Browser s’ouvre s’il est seul présent sur l’appareil et s’il est ciblé par la stratégie Intune.

Sur iOS, pour les applications qui intègrent le SDK Intune pour iOS v. 9.0.9+:
- Intune Managed Browser est lancé si Microsoft Edge et Managed Browser sont présents sur l’appareil.  
- Microsoft Edge est lancé s’il est seul présent sur l’appareil et s’il est ciblé par la stratégie Intune.
- Managed Browser est lancé si seul Managed Browser est présent sur l’appareil et s’il est ciblé par la stratégie Intune.

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Utilisation de Microsoft Edge sur iOS pour accéder aux journaux des applications gérées 

Les utilisateurs finaux ayant installé Microsoft Edge sur leurs appareils iOS peuvent afficher l’état de gestion de toutes les applications Microsoft publiées. Ils peuvent envoyer des journaux afin de dépanner leurs applications iOS gérées.
1. Ouvrez Microsoft Edge sur votre appareil iOS.
2. Tapez `about:intunehelp` dans la zone d’adresse. 
3. Le mode de résolution des problèmes est lancé depuis Microsoft Edge.

Vous trouverez la liste des paramètres stockés dans les journaux d’applications sur la page [Consulter les journaux de protection des applications dans Managed Browser](app-protection-policy-settings-log.md).

Pour voir comment afficher des journaux sur des appareils Android, consultez [Envoyer des journaux à votre administrateur informatique par e-mail](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Sécurité et confidentialité pour Microsoft Edge

Autres considérations relatives à la sécurité et à la confidentialité pour Microsoft Edge :

- Microsoft Edge ne consomme pas de paramètres que les utilisateurs définissent pour le navigateur natif sur leurs appareils, car il ne peut pas accéder à ces paramètres.
- Si vous configurez l’option **Exiger un code confidentiel simple pour l’accès** ou **Exiger des informations d’identification d’entreprise pour l’accès** dans une stratégie de protection des applications associée à Microsoft Edge et qu’un utilisateur clique sur le lien d’aide de la page d’authentification, il peut accéder à n’importe quel site Internet, même si celui-ci a été ajouté à une liste rouge dans la stratégie.
- Microsoft Edge peut uniquement bloquer l’accès aux sites lorsque l’utilisateur tente de les ouvrir directement. Il ne bloque pas l’accès quand des services intermédiaires (tels qu’un service de traduction) sont utilisés pour accéder au site.
- Pour permettre l’authentification et accéder à la documentation Intune, le site * **.microsoft.com** n’est pas soumis aux paramètres de liste verte ou rouge. Ce site est toujours autorisé.
Désactivez les données d’utilisation que Microsoft recueille automatiquement sur les performances et l’utilisation de Managed Browser pour améliorer les produits et services Microsoft. Les utilisateurs peuvent désactiver la collecte de données à l’aide du paramètre **Données d’utilisation** de leurs appareils. Vous n’avez aucun contrôle sur la collecte de ces données. Sur les appareils iOS, les utilisateurs ne peuvent pas ouvrir les sites web possédant un certificat qui a expiré ou qui n’est pas approuvé.

## <a name="next-steps"></a>Étapes suivantes

- [Que sont les stratégies de protection des applications ?](app-protection-policy.md) 
