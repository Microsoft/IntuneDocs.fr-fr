---
title: Gérer les applications Apple achetées en volume
titleSuffix: Microsoft Intune
description: Découvrez comment synchroniser les applications que vous avez achetées en volume sur les App Store iOS et macOS dans Microsoft Intune, puis comment gérer et suivre leur utilisation.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d965ac35719d809ab922d28f76dec1754e9a4c6b
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051624"
---
# <a name="how-to-manage-ios-and-macos-apps-purchased-through-apple-volume-purchase-program-with-microsoft-intune"></a>Guide pratique pour gérer les applications iOS et macOS achetées par le biais d’un programme d’achat en volume Apple avec Microsoft Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Apple vous permet d’acheter plusieurs licences pour une application que vous souhaitez utiliser dans votre organisation sur des appareils iOS et macOS à l’aide d’[Apple Business Manager](https://business.apple.com/) ou d’[Apple School Manager](https://school.apple.com/). Vous pouvez ensuite synchroniser vos informations d’achat en volume avec Intune et suivre votre utilisation des applications achetées en volume. L’achat de licences d’application vous aide à gérer efficacement les applications au sein de votre entreprise et à conserver la propriété et le contrôle des applications achetées. 

Microsoft Intune vous permet de gérer les applications achetées par le biais de ce programme en :

- synchronisant des jetons d’emplacement que vous téléchargez à partir d’Apple Business Manager ;
- suivant le nombre de licences disponibles et utilisées pour les applications achetées ;
- vous aidant à installer des applications correspondant au nombre de licences maximal que vous possédez.

Vous pouvez également synchroniser, gérer et affecter des livres que vous avez achetés dans Apple Business Manager avec Intune sur des appareils iOS. Pour plus d’informations, consultez [Guide pratique pour gérer les livres électroniques iOS que vous avez achetés par le biais d’un programme d’achat en volume](vpp-ebooks-ios.md).

## <a name="what-are-location-tokens"></a>Les jetons d’emplacement, qu’est-ce que c’est ?
Les jetons d’emplacement sont également appelés jetons de programme d’achat en volume (VPP) Apple. Ces jetons sont utilisés pour attribuer et gérer les licences achetées à l’aide d’Apple Business Manager. Les gestionnaires de contenu peuvent acheter des licences et les associer à l’aide de jetons d’emplacement pour lesquels ils disposent d’autorisations dans Apple Business Manager. Ces jetons d’emplacement sont ensuite téléchargés à partir d’Apple Business Manager et chargés dans Microsoft Intune. Microsoft Intune prend en charge le chargement de plusieurs jetons d’emplacement par locataire. Chaque jeton est valide pendant un an.

## <a name="how-are-purchased-apps-licensed"></a>Comment des licences sont-elles octroyées à des applications achetées ?
Les applications achetées peuvent être attribuées à des groupes à l’aide de deux types de licences proposés par Apple pour les appareils iOS et macOS.

|   | Gestion des licences des appareils | Gestion des licences des utilisateurs |
|-----|------------------|----------------|
| **Connexion à l’App Store** | Non obligatoire. | Chaque utilisateur final doit utiliser un ID Apple unique lorsqu’il est invité à se connecter à l’App Store. |
| **Configuration de l’appareil bloquant l’accès à l’App Store** | Les applications peuvent être installées et mises à jour à l’aide du Portail d’entreprise. | L’invitation à rejoindre Apple VPP requiert l’accès à l’App Store. Si vous avez défini une stratégie pour désactiver App Store, la gestion des licences des utilisateurs pour le programme VPP ne fonctionne pas. |
| **Mise à jour automatique des applications** | Telle que configurée par l’administrateur Intune dans les paramètres de jeton VPP Apple où le **type d’affectation** de l’application est **requis**. <br> <br> Si le **type d’affectation** est **disponible pour les appareils inscrits**, les mises à jour d’application disponibles peuvent être installées à partir du Portail d’entreprise. | Telle que configurée par l’utilisateur final dans les paramètres de l’App Store personnel. Ceci ne peut pas être géré par l’administrateur Intune. |
| **Inscription des utilisateurs** | Non pris en charge. | Pris en charge à l’aide des ID Apple gérés. |
| **Livres** | Non pris en charge. | Pris en charge. |
| **Licences utilisées** | 1 licence associée par appareil. La licence est associée à l’appareil. | 1 licence pour un maximum de 5 appareils utilisant le même ID Apple personnel. La licence est associée à l’utilisateur. <br> <br> Un utilisateur final associé à un ID Apple personnel et à un ID Apple géré dans Intune utilise 2 licences d’application.|
| **Migration de la licence** | Les applications peuvent migrer en mode silencieux des licences d’utilisateurs vers des licences d’appareils. | Les applications ne peuvent pas migrer des licences d’appareils vers des licences d’utilisateur. |

> [!NOTE]  
> Portail d’entreprise n’affiche pas les applications sous licence d’appareils sur les appareils d’inscription d’utilisateurs, car seules les applications sous licence d’utilisateurs peuvent être installées sur des appareils d’inscription d’utilisateurs.

## <a name="what-app-types-are-supported"></a>Quels sont les types d’applications pris en charge ?
Vous pouvez acheter et distribuer des applications publiques et privées à l’aide d’Apple Business Manager.
- **Applications du Store** : À l’aide d’Apple Business Manager, les gestionnaires de contenu peuvent acheter des applications gratuites et payantes qui sont disponibles dans l’App Store.
- **Applications personnalisées :** à l’aide d’Apple Business Manager, les gestionnaires de contenu peuvent également acheter des applications personnalisées mises à la disposition de votre organisation en privé. Ces applications sont adaptées aux besoins spécifiques de votre organisation par les développeurs avec lesquels vous travaillez directement. En savoir plus sur [la façon de distribuer des applications personnalisées](https://developer.apple.com/business/custom-apps/).

## <a name="prerequisites"></a>Prérequis
- Un compte [Apple Business Manager](https://business.apple.com/) ou [Apple School Manager](https://school.apple.com/) pour votre organisation. 
- Licences d’application achetées affectées à un ou plusieurs jetons d’emplacement. 
- Jetons d’emplacement téléchargés. 

> [!IMPORTANT]
> - Un jeton d’emplacement ne peut être utilisé qu’avec une seule solution de gestion des appareils à la fois. Avant de commencer à utiliser des applications achetées avec Intune, révoquez et supprimez les jetons d’emplacement existants utilisés avec un autre fournisseur de gestion d’appareils mobiles (MDM). 
> - Un jeton d’emplacement est pris en charge pour une utilisation sur un seul client Intune à la fois. Ne réutilisez pas le même jeton pour plusieurs clients Intune.
> - Par défaut, Intune synchronise les jetons d’emplacement avec Apple deux fois par jour. Vous pouvez lancer une synchronisation manuelle à tout moment à partir d’Intune.
> - Après avoir importé le jeton d’emplacement dans Intune, n’importez pas le même jeton dans une autre solution de gestion d’appareils, car cela peut entraîner la perte des enregistrements utilisateur et de l’attribution de licence.

## <a name="migrate-from-volume-purchase-program-vpp-to-apps-and-books"></a>Migrer du programme d’achat en volume (VPP) vers des applications et des livres
Si votre organisation n’a pas encore migré vers Apple Business Manager ou Apple School Manager, passez en revue le [Guide d’Apple sur la migration vers des applications et des livres](https://support.apple.com/HT208257) avant de continuer à gérer les applications achetées dans Intune.

> [!IMPORTANT]
> - Pour la meilleure expérience de migration possible, migrez un seul acheteur VPP par emplacement. Si chaque acheteur migre vers un emplacement unique, toutes les licences, attribuées ou non, sont déplacées vers des applications et des livres.
> - Ne supprimez ni le jeton VPP hérité existant dans Intune ni des applications et des affectations associées au jeton VPP hérité existant dans Intune. Ces actions nécessitent la recréation de toutes les affectations d’applications dans Intune.

Migrez le contenu et les jetons VPP achetés existants vers des applications et des livres dans Apple Business Manager ou Apple School Manager comme suit :

1. Invitez les acheteurs VPP à rejoindre votre organisation et demandez à chaque utilisateur de sélectionner un emplacement unique. 
2. Assurez-vous que tous les acheteurs VPP au sein de votre organisation ont terminé l’étape 1 avant de continuer.
3. Vérifiez que toutes les applications et licences achetées ont été migrées vers des applications et des livres dans Apple Business Manager ou Apple School Manager.
4. Téléchargez un nouveau jeton d’emplacement en accédant à **Apple Business (ou School)**  > **Paramètres** > **Applications et livres** > **Mes jetons de serveur**.
5. Mettez à jour le jeton d’emplacement dans le centre d’administration Microsoft Endpoint Manager en accédant à **Administration des locataires** > **Connecteurs et jetons** > **Jetons Apple VPP** et synchronisez le jeton.

## <a name="upload-an-apple-vpp-or-location-token"></a>Chargez un jeton VPP Apple ou un jeton d’emplacement

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Sélectionnez **Administration client** > **Connecteurs et jetons** > **Jetons VPP Apple**.
4. Dans le volet qui présente la liste des jetons VPP, sélectionnez **Créer**.
5. Dans le volet **Créer un jeton VPP**, spécifiez les informations suivantes :
    - **Fichier de jeton VPP** : si vous ne l’avez pas déjà fait, inscrivez-vous à Apple Business Manager ou à Apple School Manager. Après inscription, téléchargez le jeton VPP Apple de votre compte et sélectionnez-le ici.
    - **ID Apple** : saisissez l’ID Apple gérée du compte associé au jeton chargé.
    - **Prenez le contrôle du jeton à partir d’un autre MDM** : donnez à cette option la valeur **Oui** pour réaffecter le jeton à Intune à partir d’une autre solution MDM.
    - **Nom du jeton** : champ d’administration permettant de définir le nom du jeton.    
    - **Pays/région** : sélectionnez le Store du pays/de la région VPP.  Intune synchronise les applications VPP pour tous les paramètres régionaux à partir du magasin du pays/de la région VPP spécifié(e).
        > [!WARNING]  
        > Si vous changez de pays/région, les métadonnées des applications et l’URL d’App Store sont mises à jour lors de la synchronisation suivante avec le service Apple pour les applications créées avec ce jeton. L’application n’est pas mise à jour si elle n’existe pas dans le Store du nouveau pays/région.

    - **Type de compte VPP** : choisissez **Entreprise** ou **Éducation**.
    - **Application automatique des mises à jour** : choisissez **Activé** ou **Désactivé** pour activer les mises à jour automatiques. Quand elle est activée, Intune détecte les mises à jour des applications VPP dans l’App Store et les envoie automatiquement à l’appareil quand ce dernier s’enregistre. 
        
        > [!NOTE] 
        > Les mises à jour d’applications automatiques pour les applications Apple VPP mettent automatiquement à jour uniquement les applications déployées avec l’intention d’installation **Obligatoire**. Pour les applications déployées avec l’intention d’installation **Disponible**, la mise à jour automatique génère un message d’état pour l’administrateur informatique l’informant qu’une nouvelle version de l’application est disponible. Ce message d’état peut être consulté en sélectionnant l’application, en sélectionnant État de l’installation de l’appareil et en vérifiant les détails du statut.  

    - **J’autorise Microsoft à envoyer des informations sur l’utilisateur et l’appareil à Apple.** : vous devez sélectionner **J’accepte** pour continuer. Pour vérifier les données que Microsoft envoie à Apple, consultez [Données envoyées par Intune à Apple](~/protect/data-intune-sends-to-apple.md).

6. Quand vous avez terminé, sélectionnez **Créer**. Le jeton est affiché dans le volet de la liste de jetons.

## <a name="synchronize-a-vpp-token"></a>Synchroniser un jeton VPP
Vous pouvez synchroniser les noms des applications, les métadonnées et les informations de licence de vos applications achetées dans Intune en choisissant **Synchroniser** pour un jeton sélectionné.

## <a name="assign-a-volume-purchased-app"></a>Affecter une application achetée en volume

1. Sélectionnez **Applications** > **Toutes les applications**.
2. Dans le volet qui présente la liste des applications, choisissez l’application que vous voulez assigner, puis choisissez **Attributions**.
3. Dans le volet **Nom de l’application** - **Attributions**, choisissez **Ajouter des groupes** puis, dans le volet **Ajouter des groupes**, choisissez un **Type d’attribution** et choisissez les groupes d’utilisateurs ou d’appareils Azure AD auxquels vous voulez assigner l’application.
5. Pour chaque groupe que vous avez sélectionné, choisissez les paramètres suivants :
    - **Type** : indiquez si l’application sera **Disponible** (les utilisateurs finaux peuvent installer l’application à partir du portail d’entreprise) ou **Obligatoire** (l’application sera automatiquement installée sur les appareils des utilisateurs finaux).
    - **Type de licence** : choisissez entre **Gestion des licences des utilisateurs** et **Gestion des licences des appareils**.
6. Une fois que vous avez terminé, choisissez **Enregistrer**.


>[!NOTE]
>L’intention de déploiement disponible n’est pas prise en charge pour les groupes d’appareils, seuls les groupes d’utilisateurs sont pris en charge. La liste des applications affichées est associée à un jeton. Si vous avez une application qui est associée à plusieurs jetons VPP, la même application est affichée plusieurs fois (une fois pour chaque jeton).

> [!NOTE]  
> Intune (ou toute autre gestion des appareils mobiles) n’installe pas réellement les applications VPP. Au lieu de cela, Intune se connecte à votre compte VPP et indique à Apple les licences d’application à attribuer aux appareils. À partir de là, toutes les installations réelles sont gérées entre Apple et l’appareil.
> 
> [Informations de référence sur le protocole MDM Apple, page 135](https://developer.apple.com/business/documentation/MDM-Protocol-Reference.pdf)

## <a name="end-user-prompts-for-vpp"></a>Invites de l’utilisateur final concernant le programme VPP

L’utilisateur final reçoit des invites concernant l’installation d’applications VPP dans plusieurs scénarios. Le tableau suivant explique chaque condition :

| # | Scénario                                | Invite au programme Apple VPP                              | Invite d’installation d’application | Invite de saisie de l’identifiant Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD : utilisateur sous licence (pas d’appareil d’inscription d’utilisateur)                             | O                                                                                               | O                                           | O                                 |
| 2 | Corp – Licence associée à un utilisateur (appareil non supervisé)     | O                                                                                               | O                                           | O                                 |
| 3 | Corp – Licence associée à un utilisateur (appareil supervisé)         | O                                                                                               | N                                           | O                                 |
| 4 | BYOD – Licence associée à un appareil                           | N                                                                                               | O                                           | N                                 |
| 5 | Corp – Licence associée à un appareil (appareil non supervisé)                           | N                                                                                               | O                                           | N                                 |
| 6 | Corp – Licence associée à un appareil (appareil supervisé)                           | N                                                                                               | N                                           | N                                 |
| 7 | Mode plein écran (appareil supervisé) – Licence associée à un appareil | N                                                                                               | N                                           | N                                 |
| 8 | Mode plein écran (appareil supervisé) – Licence associée à un utilisateur   | --- | ---                                          | ---                                |

> [!Note]  
> Il n’est pas recommandé d’affecter des applications VPP à des appareils en mode plein écran à l’aide de la gestion des licences utilisateur.

## <a name="revoking-app-licenses"></a>Révoquer des licences d’application

Vous pouvez révoquer toutes les licences d’application VPP (programme d’achat en volume) iOS ou macOS associées, en fonction d’un appareil, d’un utilisateur ou d’une application donnés.  Toutefois, il existe des différences entre les plateformes iOS et macOS. 

|   | iOS | macOS |
|-----|------------------|----------------|
| **Supprimer une affectation d’application** | Quand vous supprimez une application qui a été affectée à un utilisateur, Intune récupère la licence de l’utilisateur ou de l’appareil, et désinstalle l’application de l’appareil. | Quand vous supprimez une application qui a été affectée à un utilisateur, Intune récupère la licence de l’utilisateur ou de l’appareil. L’application n’est pas désinstallée de l’appareil. |
| **Révoquer la licence de l'application** | La révocation d’une licence d’application récupère la licence de l’application auprès de l’utilisateur ou sur l’appareil. Vous devez définir l’affectation sur **Désinstaller** pour supprimer l’application de l’appareil. | La révocation d’une licence d’application récupère la licence de l’application auprès de l’utilisateur ou sur l’appareil. L’application macOS avec licence révoquée reste utilisable sur l’appareil, mais ne peut pas être mise à jour tant qu’une licence n’a pas été réaffectée à l’utilisateur ou à l’appareil. D’après Apple, ces applications sont supprimées après une période de grâce de 30 jours. Toutefois, Apple ne fournit pas de moyen à Intune pour supprimer l’application à l’aide d’une action d’affectation Désinstaller.

>[!NOTE]
> - Intune récupère les licences d’applications quand un employé quitte l’entreprise et ne fait plus partie des groupes AAD.
> - Lors de l’affectation d’une application achetée avec l’intention **Désinstaller**, Intune récupère la licence et désinstalle l’application.
> - Les licences d’applications ne sont pas récupérées lorsqu’un appareil est supprimé de la gestion Intune. 

## <a name="deleting-vpp-tokens"></a>Suppression de jetons VPP
<!-- 820879 -->  
Vous pouvez supprimer un jeton VPP Apple en utilisant la console. Ceci peut être nécessaire si vous avez des instances dupliquées d’un jeton VPP. La suppression d’un jeton entraîne la suppression des applications et l’affectation associées. Cependant, la suppression d’un jeton de ne révoque pas les licences des applications et ne désinstalle pas les applications. 

>[!NOTE]
>Intune ne peut pas révoquer de licences d’application après la suppression d’un jeton. 

<!-- 820870 -->  
Pour révoquer la licence de toutes les applications VPP pour un jeton VPP donné, vous devez d’abord révoquer toutes les licences d’application associées au jeton, puis supprimer le jeton.

## <a name="renewing-app-licenses"></a>Renouveler des licences d’application

Vous pouvez renouveler un jeton Apple VPP en en téléchargeant un nouveau sur Apple Business Manager ou sur Apple School Manager et en mettant à jour le jeton actuel dans Intune.

## <a name="deleting-a-vpp-app"></a>Suppression d’une application VPP

Actuellement, vous ne pouvez pas supprimer une application VPP iOS à partir de Microsoft Intune.

## <a name="assigning-custom-role-permissions-for-vpp"></a>Attribution d’autorisations de rôle personnalisées pour VPP

L’accès aux jetons VPP Apple et aux applications VPP peut être contrôlé indépendamment à l’aide d’autorisations affectées à des rôles d’administrateur personnalisés dans Intune.

* Pour permettre à un rôle personnalisé Intune de gérer des jetons VPP Apple sous **Applications** > **Jetons VPP Apple**, affectez des autorisations pour les **applications gérées**.
* Pour permettre à un rôle personnalisé Intune de gérer des applications achetées avec des jetons VPP iOS sous **Applications** > **Toutes les applications**, affectez des autorisations pour les **applications mobiles**. 

## <a name="additional-information"></a>Informations supplémentaires

Apple fournit une assistance directe pour créer et renouveler des jetons VPP. Pour plus d’informations, consultez [Distribuer du contenu à vos utilisateurs avec le programme VPP (Volume Purchase Program)](https://go.microsoft.com/fwlink/?linkid=2014661) dans la documentation Apple. 

Si **Affecté à une gestion MDM externe** est indiqué dans le portail Intune, vous (l’administrateur) devez supprimer le jeton VPP de la gestion MDM de tiers avant d’utiliser le jeton VPP dans Intune.

## <a name="frequently-asked-questions"></a>Forum aux questions

### <a name="how-many-tokens-can-i-upload"></a>Combien de jetons puis-je charger ?
Vous pouvez charger jusqu’à 3 000 jetons dans Intune.

### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Combien de temps met le portail pour mettre à jour le nombre de licences, une fois qu’une application est installée ou supprimée de l’appareil ?
La licence doit être mise à jour dans les heures qui suivent l’installation ou la désinstallation d’une application. Notez que si l’utilisateur final supprime l’application de l’appareil, la licence reste affectée à cet utilisateur ou appareil.

### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Est-il possible de manquer d’abonnements pour une application et, si oui, dans quelles circonstances ?
Oui. L’administrateur Intune peut manquer d’abonnements pour une application. C’est le cas, par exemple, si l’administrateur achète 100 licences pour l’application XYZ, puis cible un groupe de 500 membres. Les 100 premiers membres (utilisateurs ou appareils) reçoivent la licence qui leur est affectée. En revanche, aucune licence n’est affectée aux membres restants.


## <a name="next-steps"></a>Étapes suivantes

Consultez la page [Guide pratique pour surveiller des applications](apps-monitor.md) pour plus d’informations pour vous aider à contrôler les affectations de l’application.

Consultez [Comment résoudre les problèmes liés aux applications](~/apps/troubleshoot-app-install.md) pour plus d’informations sur la résolution des problèmes liés aux applications.
