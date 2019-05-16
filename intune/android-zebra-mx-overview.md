---
title: Utiliser des Extensions de mobilité Zebra sur des appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez Microsoft Intune pour gérer et utiliser des appareils Zebra avec Android avec les Extensions de mobilité Zebra (MX). Consultez toutes les étapes à suivre, dont l’installation de l’application du portail d'entreprise, le chargement d’une version test de l’application, l’affectation de rôle administrateur sur l’appareil, la création d’un profil StageNow, et bien plus encore.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69814b91978aa3cd74c4dc239b099883ae402af9
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764774"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Utiliser et gérer des appareils Zebra avec des Extensions de mobilité Zebra dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune comprend un jeu complet de fonctionnalités, dont la gestion d’applications et la configuration des paramètres d’appareils. Ces fonctionnalités et paramètres intégrés servent à gérer des appareils Android fabriqués par Zebra Technologies, aussi appelé « appareils Zebra ».

Sur les appareils Android, utilisez les profils **Extensions de mobilité (MX)** pour personnaliser ou ajouter des paramètres plus spécifiques à Zebra.

Cet article présente comment utiliser les Extensions de mobilité Zebra (MX) sur des appareils Zebra dans Microsoft Intune.

Cette fonctionnalité s’applique à :

- Android

Votre entreprise peut utiliser des appareils Zebra pour la vente, dans ses ateliers et plus encore. Par exemple, vous êtes un revendeur et votre environnement compte des milliers d’appareils mobiles Zebra utilisés par des collaborateurs. Intune peut vous aider à gérer ces appareils dans le cadre de votre solution de gestion des périphériques mobiles (MDM).

À l’aide d’Intune, vous pouvez inscrire des appareils Zebra pour déployer vos applications cœur de métier sur les appareils. Les profils de « configuration d’appareil » vous permettent de créer des profils MX pour gérer vos paramètres spécifiques à Zebra.

## <a name="before-you-begin"></a>Avant de commencer

- Veillez à posséder la dernière version de l’application pour bureau StageNow de Zebra Technologies.
- Consultez [Matrice de fonctionnalités complète MX Zebra](http://techdocs.zebra.com/mx/compatibility) (dirige sur le site web de Zebra) afin de confirmer que les profils créés sont compatibles avec la version MX, la version du système d’exploitation et le modèle de l’appareil.
- Certaines appareils comme les TC20/25 ne prennent pas en charge toutes les fonctionnalités MX disponibles dans StageNow. Consultez la [matrice de fonctionnalités Zebra](http://techdocs.zebra.com/mx/tc2x/) (dirige sur le site web de Zebra) pour les dernières informations de prise en charge.

## <a name="step-1-install-the-latest-company-portal-app"></a>Étape 1 : installer la dernière application de portail d’entreprise

Sur l’appareil, allez dans le Google Play Store et téléchargez et installez l’application de portail d'entreprise Intune de Microsoft. Lorsqu’elle est installée depuis Google Play, l’application de portail d'entreprise effectue les mises à jour et correctifs automatiquement.

Si Google Play n’est pas disponible, téléchargez le [Portail d'entreprise Microsoft Intune pour Android](https://www.microsoft.com/download/details.aspx?id=49140) (ouvre un autre site web Microsoft) puis [charger une version test](#sideload-the-company-portal-app) (dans cet article). Installée de cette façon, l’application ne reçoit pas automatiquement les mises à jour ou correctifs. Vous devez régulièrement mettre à jour votre application et lui appliquer des correctifs manuellement.

### <a name="sideload-the-company-portal-app"></a>Charger une version test de l'application Portail d'entreprise

Le chargement d’une version test intervient lorsque vous n’installez pas une application via Google Play. Pour charger une version test de l'application Portail d'entreprise, utilisez StageNow. 

Les étapes suivantes offrent une vue d’ensemble. Pour plus d’informations spécifiques, consultez la documentation sur Zebra. La documentation [Inscrire une gestion des périphériques mobiles à l’aide de StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (ouvre un site web de Zebra) peut être utile.

1. Dans StageNow, créez un profil pour **Inscrire une gestion des périphériques mobiles**.
2. Dans **Déploiement**, choisissez de télécharger le fichier d’agent GPM.
3. Définissez les étapes **Prendre en charge une application** et **Téléchargement la configuration** sur **Non**.
4. Dans **Télécharger GPM**, sélectionnez **Transférer/copier le fichier**. Ajoutez la source et la destination du package Android du portail d'entreprise (APK).
5. Dans **Démarrer GPM**, laissez la valeur par défaut telle quelle. Ajoutez les détails suivants :

    - **Nom du package** : `com.microsoft.windowsintune.companyportal`
    - **Nom de la classe** : `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Continuez à publier le profil, puis consommez-le avec l’application StageNow sur l’appareil. L’application du portail d'entreprise est installée et s’ouvre sur l’appareil.

> [!TIP]
> Pour plus d’informations sur StageNow et son utilité, consultez [Processus d’un appareil Android StageNow](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (ouvre le site web de Zebra).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Étape 2 : vérifier que l’application Portail d’entreprise dispose du rôle Administrateur d’appareil

L’application Portail d’entreprise nécessite un administrateur d’appareil pour gérer des appareils Android. Pour activer le rôle Administrateur d’appareil, certains appareils Zebra incluent une interface utilisateur sur l’appareil. Si l’appareil inclut une interface utilisateur, l’application Portail d'entreprise invite l’utilisateur final à accorder le rôle Administrateur d’appareil lors de l’[inscription](#step-3-enroll-the-device-in-to-intune) (dans cet article).

Si aucune interface utilisateur n’est disponible, utilisez le **gestionnaire DevAdmin** dans StageNow pour créer un profil qui accorde manuellement le rôle Administrateur d’appareil dans l’application Portail d'entreprise.

Les étapes suivantes offrent une vue d’ensemble. Pour plus d’informations spécifiques, consultez la documentation sur Zebra. 
L’article [Définir le mode d’échange de batterie en tant qu’administrateur de l’appareil](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (ouvre le site web de Zebra) peut constituer une bonne ressource.

1. Dans StageNow, créez un profil et sélectionnez **Mode Xpert**.
2. Ajoutez **Gestionnaire DevAdmin** au profil.
3. Définissez **Action d’Administration de l’appareil** sur **Activer en tant qu’administrateur de l’appareil**.
4. Définissez **Nom du package de l’administrateur de l’appareil** sur `com.microsoft.windowsintune.companyportal`.
5. Définissez **Nom de la classe de l’administrateur de l’appareil** sur `com.microsoft.omadm.client.PolicyManagerReceiver`.

Continuez à publier le profil, puis consommez-le avec l’application StageNow sur l’appareil. L’application Portail d’entreprise dispose du rôle Administrateur d’appareil.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Étape 3 : inscrire l’appareil dans Intune

Après avoir effectué les deux premières étapes, l’application Portail d’entreprise est installée sur l’appareil. L’appareil est prêt à être inscrit dans Intune.

[Inscrire des appareils Android](android-enroll.md) répertorie les étapes. Si vous disposez de nombreux appareils Zebra, utilisez plutôt un [compte de gestionnaire d’inscription d’appareil (DEM)](device-enrollment-manager-enroll.md). L’utilisation d’un compte DEM supprime également l’option de désinscription depuis l’application Portail d'entreprise, de sorte que les utilisateurs ne puissent pas désinscrire l’appareil aussi facilement.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Étape 4 : créer un profil de gestion des appareils dans StageNow

Utilisez StageNow pour créer un profil qui configure les paramètres que vous souhaitez gérer sur l’appareil. Pour plus d’informations spécifiques, consultez la documentation sur Zebra. L’article [Profils](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (ouvre le site web de Zebra) peut constituer une bonne ressource.

Lorsque vous créez le profil dans StageNow, à la dernière étape, sélectionnez **Exporter en GPM**. Cette action génère un fichier XML. Enregistrez ce fichier. Vous en aurez besoin plus tard.

> [!TIP]
> Nous vous recommandons de tester le profil avant de le déployer sur des appareils de votre organisation. Pour le tester, utilisez l’option **Tester** lors de la dernière étape de création d’un profil avec StageNow sur votre ordinateur. Utilisez ensuite le fichier généré par StageNow avec l’application StageNow sur l’appareil. 
> 
> L’application StageNow sur l’appareil présente les journaux générés lors du test du profil. L’article [Utiliser des journaux StageNow sur des appareils Zebra sous Android dans Intune](android-zebra-mx-logs-troubleshoot.md) contient des informations sur l’utilisation des journaux StageNow pour en comprendre les erreurs.

> [!NOTE]
> Si vous référencez des applications, mettez à jour des packages ou d’autres fichiers dans votre profil StageNow, votre appareil doit avoir ces mises à jour. Pour obtenir les mises à jour, l’appareil doit se connecter au serveur de déploiement StageNow lorsque le profil est appliqué. 
> 
> Vous pouvez aussi utiliser les fonctionnalités intégrés à Intune pour obtenir ces modifications, dont : 
> - Les fonctionnalités de gestion d’application pour [ajouter](apps-add.md), [déployer](apps-deploy.md), mettre à jour et [surveiller](apps-monitor.md) les applications.
> - Gérer les [mises à jour système et application](device-restrictions-android-for-work.md#device-owner-only) sur les appareils sous Android Enterprise

Après avoir testé le fichier, l’étape suivante consiste à déployer le profil sur les appareils à l’aide d’Intune.

> [!NOTE]
> Déployez un profil sur chaque appareil. Si vous souhaitez déployer plusieurs profils StageNow sur les appareils, exportez les profils et combinez les paramètres en un seul fichier XML avant de les ajouter à Intune. 
> 
> Évitez d’avoir deux paramètres qui configurent la même propriété dans le même fichier XML. L’objectif consiste à éviter les conflits entre paramètres sur l’appareil.

## <a name="step-5-create-a-profile-in-intune"></a>Étape 5 : créer un profil dans Intune

Dans Intune, créez un profil de configuration d’appareil :

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : attribuez un nom descriptif au nouveau profil.
    - **Description :** entrez une description pour le profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : sélectionnez **Android**.
    - **Type de profil** : sélectionnez **Profil MX (Zebra uniquement)**.

4. Dans **Profil MX au format .xml**, ajoutez le fichier de profil XML [que vous avez exporté à partir de StageNow](#step-4-create-a-device-management-profile-in-stagenow) (dans cet article).
5. Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. La stratégie est créée et apparaît dans la liste.

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

La prochaine fois que l’appareil recherche des mises à jour de configuration, le profil MX sera déployé sur l’appareil. Les appareils se synchronisent avec Intune lors de leur inscription, puis toutes les 8 heures environ. Vous pouvez également [forcer une synchronisation dans Intune](device-sync.md). Sinon, sur l’appareil, ouvrez l’**application Portail d’entreprise** > **Paramètres** > **Synchronisation**. 

> [!TIP]
> - Pour des raisons de sécurité, vous ne voyez pas le texte XML du profil après que l’avoir enregistré. Le texte est chiffré, et vous voyez uniquement les astérisques (`****`). Pour votre information, nous recommandons d’enregistrer des copies des profils MX avant de les ajouter à Intune.
> 
> - Pour mettre à jour un profil après son affectation à des appareils Zebra, créez un fichier XML StageNow mis à jour, et ajoutez le nouveau fichier XML StageNow. Ce nouveau fichier remplace la stratégie StageNow précédente dans le profil.

## <a name="next-steps"></a>Étapes suivantes

- [Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
- [Utilisez les journaux StageNow pour résoudre les problèmes liés aux appareils Zebra](android-zebra-mx-logs-troubleshoot.md).
