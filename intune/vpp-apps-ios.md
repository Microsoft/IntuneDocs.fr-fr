---
title: Gérer les applications iOS achetées en volume dans Microsoft Intune
titleSuffix: ''
description: Découvrez comment synchroniser les applications que vous avez achetées en volume sur l’App Store iOS dans Microsoft Intune, puis comment gérer et suivre leur utilisation.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dca219f1593265e0bf6447c054969548d5d79351
ms.sourcegitcommit: 617bd653c34c1e6a4e2ad61811c5912f8dab775c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59570635"
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L’App Store iOS vous permet d’acheter plusieurs licences pour une application que vous souhaitez exécuter dans votre entreprise. Le fait d’acheter plusieurs copies aide à gérer efficacement les applications de l’entreprise.

Microsoft Intune vous permet de gérer plusieurs copies des applications achetées par le biais de ce programme en :

- Signalant les informations de licence de l’App Store.
- Effectuant le suivi du nombre de licences utilisées.
- Vous empêchant d’installer davantage de copies de l’application que vous n’en possédez.

Vous pouvez utiliser deux méthodes pour affecter les applications achetées en volume :

### <a name="device-licensing"></a>Gestion des licences des appareils

Quand vous affectez une application à des appareils, une licence d’application est utilisée et reste associée à l’appareil auquel vous l’avez attribuée.

Quand vous affectez des applications achetées en volume à un appareil, l’utilisateur final de l’appareil n’a pas à fournir un ID Apple pour accéder à l’App Store.

### <a name="user-licensing"></a>Licences utilisateur

Quand vous affectez une application à un utilisateur, une licence d’application est utilisée et est associée à l’utilisateur. L’application peut être exécutée sur plusieurs appareils détenus par l’utilisateur (avec une limite contrôlée par Apple).

Quand vous affectez une application achetée en volume à des utilisateurs, chaque utilisateur final doit avoir un identifiant Apple valide pour accéder à l’App Store.

Vous pouvez également synchroniser, gérer et affecter des livres que vous avez achetés dans le Store VPP (Programme d’achat en volume) d’Apple avec Intune. Pour plus d’informations, consultez [Guide pratique pour gérer les livres électroniques iOS que vous avez achetés par le biais d’un programme d’achat en volume](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gérer les applications pour appareils iOS achetées en volume

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>Prend en charge les applications achetées via le programme d’achat en volume (VPP) Apple pour les appareils iOS

Achetez plusieurs licences pour des applications iOS via le [Programme d’achat en volume Apple pour les entreprises](https://www.apple.com/business/vpp/) ou [Programme d’achat en volume Apple pour les organismes éducatifs](https://volume.itunes.apple.com/us/store). Cela implique la configuration d’un compte Apple VPP à partir du site web Apple et l’importation du jeton Apple VPP dans Intune.  Vous pouvez ensuite synchroniser vos informations d’achat en volume avec Intune et suivre votre utilisation des applications achetées en volume.

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>Prend en charge les applications achetées en volume B2B pour les appareils iOS

En outre, les développeurs tiers peuvent également distribuer des applications en privé aux membres autorisés du programme d’achat en volume pour les entreprises. Ces membres du programme d’achat en volume pour les entreprises peuvent se connecter à l’App Store du programme d’achat en volume et acheter leurs applications. Les applications du programme d’achat en volume pour les entreprises achetées par l’utilisateur final se synchronisent avec leurs locataires Intune.

## <a name="before-you-start"></a>Avant de commencer
Avant de commencer, vous devez obtenir un jeton VPP auprès d’Apple et l’importer dans votre compte Intune. En outre, vous devez comprendre les critères suivants :

* Vous pouvez associer plusieurs jetons VPP à votre compte Intune.
* Si vous avez déjà utilisé un jeton VPP avec un autre produit, vous devez en générer un nouveau à utiliser avec Intune.
* Chaque jeton est valide pendant un an.
* Par défaut, Intune se synchronise avec le service Apple VPP deux fois par jour. Vous pouvez lancer une synchronisation manuelle à tout moment.
* Avant de commencer à utiliser Apple VPP avec Intune, supprimez les comptes d’utilisateur VPP existants créés avec d’autres fournisseurs de gestion des appareils mobiles (MDM). Par mesure de sécurité, ces comptes d’utilisateur ne sont pas synchronisés dans Intune. Intune synchronise uniquement les données du service Apple VPP qui ont été créées par Intune.
* Avec Intune, vous pouvez ajouter jusqu’à 256 jetons VPP.
* Le programme Profil d’inscription des appareils d’Apple automatise l’inscription auprès de la gestion des appareils mobiles (MDM). Avec le Profil d’inscription des appareils, vous pouvez configurer des appareils d’entreprise sans les avoir en main. Vous pouvez inscrire avec le programme Profil d’inscription des appareils en utilisant le même compte d’agent du programme que celui que vous avez utilisé avec le programme d’achat en volume d’Apple. L’ID de programme de déploiement Apple est unique pour les programmes répertoriés dans le site web [Programmes de déploiement Apple](https://deploy.apple.com) et il ne peut pas être utilisé pour se connecter aux services Apple, comme iTunes Store.
* Quand vous affectez des applications VPP à l’aide du modèle de licence utilisateur à des utilisateurs ou des appareils (avec une affinité d’utilisateur), chaque utilisateur Intune doit être associé à un e-mail ou un ID Apple unique quand il accepte les conditions générales Apple sur son appareil.
* Vérifiez que, quand vous configurez un appareil pour un nouvel utilisateur Intune, vous le faites avec l’ID Apple unique ou l’adresse e-mail de cet utilisateur. L’ID Apple ou l’adresse e-mail et l’utilisateur Intune forment une paire unique. Ils peuvent être utilisés sur cinq appareils au maximum.
* Un jeton VPP est pris en charge pour une utilisation sur un seul compte Intune à la fois. Ne réutilisez pas le même jeton VPP pour plusieurs clients Intune.

>[!IMPORTANT]
>Après avoir importé le jeton VPP dans Intune, n’importez pas le même jeton dans une autre solution de gestion d’appareils, car cela peut entraîner la perte des enregistrements utilisateur et de l’attribution de licence.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Pour obtenir et charger un jeton Apple VPP

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3.  Dans le volet **Intune**, choisissez **Applications clientes** > **Jetons VPP iOS** sous **Installation**.
4.  Dans le volet qui présente la liste des jetons VPP, sélectionnez **Créer**.
5. Dans le volet **Créer un jeton VPP**, spécifiez les informations suivantes :
    - **Fichier de jeton VPP** : si vous ne l’avez pas encore fait, inscrivez-vous au Programme d’achat en volume Apple pour les entreprises ou au programme pour les organismes éducatifs. Après inscription, téléchargez le jeton VPP Apple de votre compte et sélectionnez-le ici.
    - **ID Apple** : saisissez l’ID Apple du compte associé au programme d’achats en volume.
    - **Pays/région** : sélectionnez le Store du pays VPP.  Intune synchronise les applications VPP pour tous les paramètres régionaux à partir du magasin du pays/région VPP spécifié.
        > [!WARNING]  
        > Si vous changez de pays/région, les métadonnées des applications et l’URL du Store sont mises à jour lors de la prochaine synchronisation avec le service Apple pour les applications créées avec ce jeton. L’application n’est pas mise à jour si elle n’existe pas dans le Store du nouveau pays/région.

    - **Type de compte VPP** : choisissez **Entreprise** ou **Éducation**.
    - **Application automatique des mises à jour** : choisissez **Activé** ou **Désactivé** pour activer les mises à jour automatiques. Quand elle est activée, Intune détecte les mises à jour des applications VPP dans l’App Store et les envoie automatiquement à l’appareil quand ce dernier s’enregistre. Les mises à jour d’applications automatiques pour les applications Apple VPP mettent automatiquement à jour uniquement les applications déployées avec l’intention d’installation **Obligatoire**. Pour les applications déployées avec l’intention d’installation **Disponible**, la mise à jour automatique génère une notification pour vous (l’administrateur) vous informant qu’une nouvelle version de l’application est disponible. L’utilisateur doit cliquer sur Installer pour installer la version la plus récente de l’application. En outre, l’utilisateur verra que l’application n’est pas installée sur le portail d’entreprise, même si une version antérieure de l’application est installée. Dans ce cas, l’utilisateur peut réinstaller l’application.
    
        > [!NOTE]
        > Les mises à jour automatiques des applications fonctionnent pour les applications sous licence d’appareil et d’utilisateur pour iOS version 11.0 et ultérieure.
6. Quand vous avez terminé, sélectionnez **Créer**.

Le jeton est affiché dans le volet de la liste de jetons.

Vous pouvez synchroniser les données détenues par Apple avec Intune à tout moment en sélectionnant **Synchroniser maintenant**.

## <a name="to-assign-a-volume-purchased-app"></a>Pour affecter une application achetée en volume

1.  Dans le volet **Intune**, choisissez **Applications clientes** > **Applications** sous **Gérer**.
2.  Dans le volet qui présente la liste des applications, choisissez l’application que vous voulez assigner, puis choisissez **Attributions**.
3.  Dans le volet ***Nom de l’application*** - **Attributions**, choisissez **Ajouter des groupes** puis, dans le volet **Ajouter des groupes**, choisissez un **Type d’attribution** et choisissez les groupes d’utilisateurs ou d’appareils Azure AD auxquels vous voulez assigner l’application.
5.  Pour chaque groupe que vous avez sélectionné, choisissez les paramètres suivants :
    - **Type** : indiquez si l’application sera **Disponible** (les utilisateurs finaux peuvent installer l’application à partir du portail d’entreprise) ou **Obligatoire** (l’application sera automatiquement installée sur les appareils des utilisateurs finaux).
    - **Type de licence** : choisissez entre **Gestion des licences des utilisateurs** et **Gestion des licences des appareils**.
6.  Une fois que vous avez terminé, choisissez **Enregistrer**.


>[!NOTE]
>La liste des applications affichées est associée à un jeton. Si vous avez une application qui est associée à plusieurs jetons VPP, la même application est affichée plusieurs fois (une fois pour chaque jeton).

## <a name="end-user-prompts-for-vpp"></a>Invites de l’utilisateur final concernant le programme VPP

L’utilisateur final reçoit des invites concernant l’installation d’applications VPP dans plusieurs scénarios. Le tableau suivant explique chaque condition :

| # | Scénario                                | Invite au programme Apple VPP                              | Invite d’installation d’application | Invite de saisie de l’identifiant Apple |
|---|--------------------------------------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------|-----------------------------------|
| 1 | BYOD – Licence associée à un utilisateur                             | O                                                                                               | O                                           | O                                 |
| 2 | Corp – Licence associée à un utilisateur (appareil non supervisé)     | O                                                                                               | O                                           | O                                 |
| 3 | Corp – Licence associée à un utilisateur (appareil supervisé)         | O                                                                                               | N                                           | O                                 |
| 4 | BYOD – Licence associée à un appareil                           | N                                                                                               | O                                           | N                                 |
| 5 | Corp – Licence associée à un appareil (appareil non supervisé)                           | N                                                                                               | O                                           | N                                 |
| 6 | Corp – Licence associée à un appareil (appareil supervisé)                           | N                                                                                               | N                                           | N                                 |
| 7 | Mode plein écran (appareil supervisé) – Licence associée à un appareil | N                                                                                               | N                                           | N                                 |
| 8 | Mode plein écran (appareil supervisé) – Licence associée à un utilisateur   | --- | ---                                          | ---                                |

> [!Note]  
> Il n’est pas recommandé d’affecter des applications VPP à des appareils en mode plein écran à l’aide de la gestion des licences utilisateur VPP.

## <a name="revoking-app-licenses-and-deleting-tokens"></a>Révocation des licences d’application et suppression des jetons 

Vous pouvez révoquer toutes les licences d’application VPP (programme d’achat en volume) iOS associées, en fonction d’un appareil, d’un utilisateur ou d’une application donnés. Vous pouvez notifier les utilisateurs quand une application ne leur est plus affectée. La révocation d’une licence d’application ne désinstalle pas l’application VPP de l’appareil. Pour désinstaller une application VPP et récupérer une licence d’application affectée à un utilisateur ou à un appareil, vous devez définir l’action d’affectation sur **Désinstaller**. Quand vous supprimez une application qui a été affectée à un utilisateur, Intune récupère la licence de l’utilisateur ou de l’appareil, et désinstalle l’application de l’appareil. Le nombre de licences récupérées est répercutée dans le nœud **Applications sous licence** dans la charge de travail **Application** d’Intune. Une fois une application VPP désinstallée et la licence d’application récupérée, vous pouvez choisir d’affecter la licence d’application à un autre utilisateur ou appareil. 

>[!NOTE]
>Intune récupère toutes les licences utilisateur d’applications VPP iOS quand un employé quitte l’entreprise et ne fait plus partie des groupes AAD.

<!-- 820879 -->  
Vous pouvez supprimer un jeton VPP iOS en utilisant la console. Ceci peut être nécessaire si vous avez des instances dupliquées d’un jeton VPP. La suppression d’un jeton entraîne la suppression des applications et l’affectation associées. Cependant, la suppression d’un jeton de ne révoque pas les licences des applications et ne désinstalle pas les applications. 

>[!NOTE]
>Intune ne peut pas révoquer de licences d’application après la suppression d’un jeton. 

<!-- 820870 -->  
Pour révoquer la licence de toutes les applications VPP pour un jeton VPP donné, vous devez d’abord révoquer toutes les licences d’application associées au jeton, puis supprimer le jeton.

## <a name="renewing-app-licenses"></a>Renouveler des licences d’application

Vous pouvez renouveler un jeton Apple VPP en en téléchargeant un nouveau sur le portail du Programme d’achat en volume d’Apple et en mettant à jour le jeton actuel dans Intune.

## <a name="deleting-an-ios-vpp-app"></a>Suppression d’une application VPP iOS

Actuellement, vous ne pouvez pas supprimer une application VPP iOS à partir de Microsoft Intune.

## <a name="additional-information"></a>Informations supplémentaires

Quand un utilisateur avec un appareil éligible essaie pour la première fois d’installer une application VPP sur un appareil, il est invité à participer au programme VPP d’Apple. Il doit accepter pour que l’installation de l’application se poursuive. L’invitation à participer au Programme d’achat en volume (VPP) Apple nécessite que l’utilisateur puisse utiliser l’application iTunes sur l’appareil iOS. Si vous avez défini une stratégie pour désactiver l’application iTunes Store, la gestion des licences par utilisateur pour le programme VPP ne fonctionne pas. La solution consiste à autoriser l’application iTunes en supprimant la stratégie ou à utiliser la gestion des licences par appareil.

Apple fournit une assistance directe pour créer et renouveler des jetons VPP. Pour plus d’informations, consultez [Distribuer du contenu à vos utilisateurs avec le programme VPP (Volume Purchase Program)](https://go.microsoft.com/fwlink/?linkid=2014661) dans la documentation Apple. 

Si **Affecté à une gestion MDM externe** est indiqué dans le portail Intune, vous (l’administrateur) devez supprimer le jeton VPP de la gestion MDM de tiers avant d’utiliser le jeton VPP dans Intune.

## <a name="frequently-asked-questions"></a>Forum aux questions

#### <a name="how-long-does-the-portal-take-to-update-the-license-count-once-an-app-is-installed-or-removed-from-the-device"></a>Combien de temps met le portail pour mettre à jour le nombre de licences, une fois qu’une application est installée ou supprimée de l’appareil ?
La licence doit être mise à jour dans les heures qui suivent l’installation ou la désinstallation d’une application. Notez que si l’utilisateur final supprime l’application de l’appareil, la licence reste affectée à cet utilisateur ou appareil.

#### <a name="is-it-possible-to-oversubscribe-an-app-and-if-so-in-what-circumstance"></a>Est-il possible de manquer d’abonnements pour une application et, si oui, dans quelles circonstances ?
Oui. L’administrateur Intune peut manquer d’abonnements pour une application. C’est le cas, par exemple, si l’administrateur achète 100 licences pour l’application XYZ, puis cible un groupe de 500 membres. Les 100 premiers membres (utilisateurs ou appareils) reçoivent la licence qui leur est affectée. En revanche, aucune licence n’est affectée aux membres restants.

#### <a name="i-understand-intune-automatically-syncs-app-licenses-each-day-with-apple-is-that-correct"></a>Je comprends qu’Intune synchronise automatiquement les licences d’application chaque jour auprès d’Apple, est-ce exact ?
Intune synchronise les licences d’application deux fois par jour auprès d’Apple.

## <a name="next-steps"></a>Étapes suivantes

Consultez la page [Guide pratique pour surveiller des applications](apps-monitor.md) pour plus d’informations pour vous aider à contrôler les affectations de l’application.
