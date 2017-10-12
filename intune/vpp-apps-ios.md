---
title: "Gérer les applications iOS achetées en volume | Microsoft Docs"
titlesuffix: Azure portal
description: "Découvrez comment synchroniser les applications que vous avez achetées en volume à partir de l’App Store iOS dans Intune et ensuite gérer et suivre leur utilisation."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 09/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51d45ce2-d81b-4584-8bc4-568c8c62653d
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dc3160d40d4ddabcd0a7d8d5557b07b4086eea7c
ms.sourcegitcommit: 4184db38d1a9a223e680bcb4c9b732f7069bf510
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2017
---
# <a name="how-to-manage-ios-apps-purchased-through-a-volume-purchase-program-with-microsoft-intune"></a>Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L’App Store iOS vous permet d’acheter plusieurs licences pour une application que vous souhaitez exécuter dans votre entreprise. L’achat de plusieurs licences d’une application aide à réduire les coûts d’administration liés au suivi de plusieurs copies d’application achetées.

Microsoft Intune vous permet de gérer les applications que vous avez achetées par le biais de ce programme en :

- Signalant les informations de licence de l’App Store
- Effectuant le suivi du nombre de licences que vous avez utilisées
- Vous empêchant d’installer davantage de copies de l’application que vous n’en possédez

Vous pouvez utiliser deux méthodes pour affecter les applications achetées en volume :

### <a name="device-licensing"></a>Gestion des licences des appareils

Quand vous affectez une application à des appareils, une licence d’application est utilisée et reste associée à l’appareil auquel vous l’avez attribuée.
Quand vous affectez des applications achetées en volume à un appareil, l’utilisateur final de l’appareil n’a pas à fournir un ID Apple pour accéder à l’App Store. 



### <a name="user-licensing"></a>Licences utilisateur

Quand vous affectez une application à des utilisateurs, une licence d’application est utilisée et est associée à l’utilisateur. L’application peut être exécutée sur plusieurs appareils détenus par l’utilisateur (avec une limite contrôlée par Apple).
Quand vous attribuez une application achetée en volume à des utilisateurs, chaque utilisateur final doit avoir un ID Apple valide pour accéder à l’App Store.

Vous pouvez également synchroniser, gérer et affecter des livres que vous avez achetés dans le Store VPP (Programme d’achat en volume) d’Apple avec Intune. Pour plus d’informations, consultez [Guide pratique pour gérer les livres électroniques iOS que vous avez achetés par le biais d’un programme d’achat en volume](vpp-ebooks-ios.md).

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>Gérer les applications pour appareils iOS achetées en volume

### <a name="supports-apple-volume-purchase-program-volume-purchased-apps-for-ios-devices"></a>Prend en charge les applications achetées via le programme d’achat en volume (VPP) Apple pour les appareils iOS

Achetez plusieurs licences pour des applications iOS via le [Programme d’achat en volume Apple pour les entreprises](http://www.apple.com/business/vpp/) ou [Programme d’achat en volume Apple pour les organismes éducatifs](http://volume.itunes.apple.com/us/store). Cela implique la configuration d’un compte Apple VPP à partir du site web Apple et l’importation du jeton Apple VPP dans Intune.  Vous pouvez ensuite synchroniser vos informations d’achat en volume avec Intune et suivre votre utilisation des applications achetées en volume.

### <a name="supports-business-to-business-volume-purchased-apps-for-ios-devices"></a>Prend en charge les applications achetées en volume B2B pour les appareils iOS

En outre, les développeurs tiers peuvent également distribuer des applications en privé aux membres autorisés du programme d’achat en volume pour les entreprises. Ces membres du programme d’achat en volume pour les entreprises peuvent se connecter à l’App Store du programme d’achat en volume et acheter leurs applications. Les applications du programme d’achat en volume pour les entreprises achetées par l’utilisateur final se synchronisent avec leurs locataires Intune.

## <a name="before-you-start"></a>Avant de commencer
Avant de commencer, vous devez obtenir un jeton VPP auprès d’Apple et l’importer dans votre compte Intune. En outre, vous devez comprendre les critères suivants :

* Vous pouvez associer plusieurs jetons de programme d’achat de volume à votre compte Intune.
* Si vous avez déjà utilisé un jeton VPP avec un autre produit, vous devez en générer un nouveau à utiliser avec Intune.
* Chaque jeton est valide pendant un an.
* Par défaut, Intune se synchronise avec le service Apple VPP deux fois par jour. Vous pouvez lancer une synchronisation manuelle à tout moment.
* Avant de commencer à utiliser iOS VPP avec Intune, supprimez les comptes d’utilisateur VPP existants créés avec d’autres fournisseurs de gestion des appareils mobiles. Par mesure de sécurité, ces comptes d’utilisateur ne sont pas synchronisés dans Intune. Intune synchronise uniquement les données du service Apple VPP qui ont été créées par Intune.
* Avec Intune, vous pouvez ajouter jusqu’à 256 jetons VPP.
* Le programme Profil d’inscription des appareils d’Apple automatise l’inscription auprès de la gestion des appareils mobiles (MDM). Avec le Profil d’inscription des appareils, vous pouvez configurer des appareils d’entreprise sans les avoir en main. Vous pouvez inscrire avec le programme Profil d’inscription des appareils en utilisant le même compte d’agent du programme que celui que vous avez utilisé avec le programme d’achat en volume d’Apple. L’ID de programme de déploiement Apple est unique pour les programmes répertoriés dans le site web [Programmes de déploiement Apple](https://deploy.apple.com) et il ne peut pas être utilisé pour se connecter aux services Apple, comme iTunes Store. 
* Un jeton VPP est pris en charge pour une utilisation sur un seul compte Intune à la fois. Ne réutilisez pas le même jeton VPP pour plusieurs clients Intune.
* Quand vous affectez des applications VPP à l’aide du modèle de licence utilisateur à des utilisateurs ou des appareils (avec une affinité d’utilisateur), chaque utilisateur Intune doit être associé à un e-mail ou un ID Apple unique quand il accepte les conditions générales Apple sur son appareil. N’utilisez pas l’ID Apple utilisé pour l’ID de programme de déploiement d’Apple. Vérifiez que, quand vous configurez un appareil pour un nouvel utilisateur Intune, vous le faites avec l’ID Apple unique ou l’adresse e-mail de cet utilisateur. L’ID Apple ou l’adresse e-mail et l’utilisateur Intune forment une paire unique. Ils peuvent être utilisés sur cinq appareils au maximum.

>[!IMPORTANT]
>Après avoir importé le jeton VPP dans Intune, n’importez pas le même jeton dans une autre solution de gestion d’appareils, car cela peut entraîner la perte des enregistrements utilisateur et de l’attribution de licence.

## <a name="to-get-and-upload-an-apple-vpp-token"></a>Pour obtenir et charger un jeton Apple VPP

1. Connectez-vous au portail Azure.
2. Choisissez **Autres services** > **Surveillance + Gestion** > **Intune**.
2.  Dans la liste du panneau des jetons VPP, cliquez sur **Créer**.
4. Dans le panneau **Créer un jeton VPP**, spécifiez les informations suivantes :
    - **Fichier de jeton VPP** : si vous ne l’avez pas encore fait, inscrivez-vous au Programme d’achat en volume Apple pour les entreprises ou au programme pour les organismes éducatifs. Après inscription, téléchargez le jeton VPP Apple de votre compte et sélectionnez-le ici.
    - **Application automatique des mises à jour** : choisissez **Activé** ou **Désactivé** pour activer les mises à jour automatiques. Quand elle est activée, Intune met à jour toutes les applications achetées pour le jeton spécifié via le service Intune quand l’appareil s’enregistre. détecte les mises à jour des applications VPP dans l’App Store et les envoie (push) automatiquement à l’appareil quand celui-ci s’enregistre.
4. Une fois ces opérations effectuées, cliquez sur **Télécharger**.

Le jeton est affiché dans le panneau de liste de jetons.

Vous pouvez synchroniser les données détenues par Apple avec Intune à tout moment en sélectionnant **Synchroniser maintenant**.

> [!NOTE]
> Microsoft Intune synchronise uniquement les informations des applications qui disponibles de manière publique par l’intermédiaire de l’iTunes Store. **Les applications B2B personnalisées pour iOS** ne sont pas encore prises en charge. Si votre scénario cible ce type d’application, les informations de l’application ne sont pas synchronisées.

## <a name="to-assign-a-volume-purchased-app"></a>Pour affecter une application achetée en volume

1.  Dans le panneau **Intune**, choisissez **Applications mobiles** > **Applications** sous **Gérer**.
2.  Dans le panneau avec la liste d’applications, choisissez l’application que vous voulez affecter, puis choisissez **Affectations**.
3.  Dans le panneau ***Nom de l’application*** - **Affectations**, choisissez **Sélectionner des groupes** puis, dans le panneau **Sélectionner des groupes**, choisissez les groupes d’utilisateurs ou d’appareils Azure AD auxquels vous voulez affecter l’application.
5.  Pour chaque groupe que vous avez sélectionné, choisissez les paramètres suivants :
    - **Type** : indiquez si l’application sera **Disponible** (les utilisateurs finaux peuvent installer l’application à partir du portail d’entreprise) ou **Obligatoire** (l’application sera automatiquement installée sur les appareils des utilisateurs finaux).
    - **Type de licence** : choisissez entre **Gestion des licences des utilisateurs** et **Gestion des licences des appareils**.
6.  Une fois que vous avez terminé, choisissez **Enregistrer**.


>[!NOTE]
>La liste des applications affichées est associée à un jeton. Si vous avez une application qui est associée à plusieurs jetons VPP, la même application est affichée plusieurs fois (une fois pour chaque jeton).

## <a name="further-information"></a>Informations supplémentaires

Pour récupérer une licence, vous devez remplacer l’action d’attribution par Désinstaller. La licence est récupérée une fois l’application désinstallée. Si vous supprimez une application qui était attribuée à un utilisateur, Intune tente de récupérer toutes les licences d’application qui étaient associées à cet utilisateur.

Quand un utilisateur avec un appareil éligible essaie pour la première fois d’installer une application VPP sur un appareil, il est invité à participer au programme VPP d’Apple. Il doit accepter pour que l’installation de l’application se poursuive. L’invitation à participer au Programme d’achat en volume (VPP) Apple nécessite que l’utilisateur puisse utiliser l’application iTunes sur l’appareil iOS. Si vous avez défini une stratégie pour désactiver l’application iTunes Store, la gestion des licences par utilisateur pour le programme VPP ne fonctionne pas. La solution consiste à autoriser l’application iTunes en supprimant la stratégie ou à utiliser la gestion des licences par appareil.



## <a name="next-steps"></a>Étapes suivantes

Consultez la page [Guide pratique pour surveiller des applications](apps-monitor.md) pour plus d’informations pour vous aider à contrôler les affectations de l’application.