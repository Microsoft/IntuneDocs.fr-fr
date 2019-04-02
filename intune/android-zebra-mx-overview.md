---
title: Utiliser des Extensions de mobilité Zebra sur les appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Utiliser Microsoft Intune pour gérer et utiliser Zebra les appareils exécutant Android avec Zebra mobilité Extensions (MX). Voir toutes les étapes, notamment installer l’application portail d’entreprise, l’application de chargement indépendant, affecter le rôle d’administrateur de périphérique, créer un profil de StageNow et bien plus encore.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490602"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Utiliser et gérer des appareils Zebra avec des Extensions de mobilité Zebra dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune inclut un ensemble complet de fonctionnalités, notamment la gestion des applications et la configuration des paramètres de l’appareil. Ces fonctionnalités intégrées et les paramètres sont utilisés pour gérer les appareils Android fabriqués par des Technologies Zebra, également appelé « appareils Zebra ».

Si vous souhaitez personnaliser ou ajouter d’autres paramètres Zebra spécifiques, vous pouvez également utiliser Zebra **mobilité Extensions (MX)** sur ces appareils. 

Cette fonctionnalité s’applique à :

- Android

Votre entreprise peut utiliser les appareils Zebra pour la vente au détail, sur l’usine et bien plus encore. Par exemple, vous êtes un commerçant et votre environnement comprend des milliers d’appareils mobiles Zebra utilisés par les commerciaux. Intune peut aider à gérer ces appareils dans le cadre de votre solution de gestion des appareils mobiles.

À l’aide d’Intune, vous pouvez inscrire des appareils Zebra pour déployer vos applications line of business sur les appareils. Profils de « Configuration de l’appareil » vous permettent de créer des profils MX pour gérer vos paramètres Zebra spécifiques.

Cet article vous montre comment utiliser des Extensions de mobilité Zebra (MX) sur les appareils Zebra dans Microsoft Intune.

## <a name="before-you-begin"></a>Avant de commencer

- Veillez à que disposer de la dernière version de l’application de bureau StageNow à partir de Technologies Zebra.
- Veillez à consulter [matrice des fonctionnalités de Zebra complète MX](http://techdocs.zebra.com/mx/compatibility) (ouvre le site web de Zebra) pour confirmer les profils que vous créez sont compatibles avec la version de MX, version du système d’exploitation et modèle du périphérique.
- Certains appareils, tels que les appareils TC20/25, ne prennent en charge toutes les fonctionnalités disponibles MX dans StageNow. Veillez à consulter [matrice des fonctionnalités de Zebra](http://techdocs.zebra.com/mx/tc2x/) (ouvre le site web de Zebra) pour les informations de support technique de mise à jour.

## <a name="step-1-install-the-latest-company-portal-app"></a>Étape 1 : Installer la dernière application portail d’entreprise

Sur l’appareil, accédez à la Boutique Google Play et télécharger et installer l’application portail d’entreprise Intune de Microsoft. Lors de l’installation à partir de Google Play, l’application portail d’entreprise obtient les mises à jour et corrige automatiquement.

Si Google Play n’est pas disponible, téléchargez le [portail d’entreprise Microsoft Intune pour Android](https://www.microsoft.com/download/details.aspx?id=49140) (ouvre un autre site Web de Microsoft), et [charger une version test il](#sideload-the-company-portal-app) (dans cet article). Lors de l’installation de cette façon, l’application ne reçoit pas les mises à jour ou correctifs automatiquement. Vous devez régulièrement mettre à jour et l’application des correctifs manuellement.

### <a name="sideload-the-company-portal-app"></a>Charger une version test de l'application Portail d'entreprise

« Chargement de version test » est lorsque vous n’utilisez pas Google Play pour installer une application. Chargement de version test l’application portail d’entreprise, utilisez StageNow. 

Les étapes suivantes fournissent une vue d’ensemble. Pour plus d’informations spécifiques, consultez de Zebra. [S’inscrire à une gestion des appareils mobiles à l’aide de StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (ouvre le site web de Zebra) peut être une bonne ressource.

1. Dans StageNow, créer un profil pour **inscription dans une gestion des appareils mobiles**.
2. Dans **déploiement**, choisir de télécharger le fichier de l’agent de gestion des appareils mobiles.
3. Définir le **prise en charge application** et **Configuration télécharger** les étapes à **non**.
4. Dans **MDM télécharger**, sélectionnez **transfert/copier le fichier**. Ajouter la source et la destination du package Entreprise Portal Android (APK).
5. Dans **MDM lancer**, conservez les valeurs par défaut en tant que-est. Ajoutez les détails suivants :

    - **Nom du package** : `com.microsoft.windowsintune.companyportal`
    - **Nom de la classe** : `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Continuer au profil de publication et l’utiliser avec l’application StageNow sur l’appareil. L’application portail d’entreprise est installée et ouvert sur l’appareil.

> [!TIP]
> Pour plus d’informations sur StageNow et son fonctionnement, consultez [mise en lots des appareils Android de StageNow](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (ouvre le site web de Zebra).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Étape 2 : Vérifier que l’application portail d’entreprise a le rôle d’administrateur de périphérique

L’application portail d’entreprise nécessite un administrateur de l’appareil pour gérer des appareils Android. Pour activer le rôle d’administrateur de l’appareil, certains appareils Zebra incluent une interface utilisateur (IU) sur l’appareil. Si l’appareil inclut une interface utilisateur, l’application portail d’entreprise invite l’utilisateur final pour accorder l’administrateur de l’appareil pendant [inscription](#step-3-enroll-the-device-in-to-intune) (dans cet article).

Si une interface utilisateur n’est pas disponible, utilisez le **DevAdmin Manager** dans StageNow pour créer un profil qui accorde l’administrateur de l’appareil manuellement à l’application portail d’entreprise.

Les étapes suivantes fournissent une vue d’ensemble. Pour plus d’informations spécifiques, consultez de Zebra. 
[Définir le mode batterie échange en tant qu’administrateur de l’appareil](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (ouvre le site Web de Zebra) peut être une bonne ressource.

1. Dans StageNow, créez un profil et sélectionnez **Xpert Mode**.
2. Ajouter **DevAdmin Manager** au profil.
3. Définissez **Action d’Administration appareil** à **activer en tant qu’administrateur de l’appareil**.
4. Définissez **appareil Admin nom_package** à `com.microsoft.windowsintune.companyportal`.
5. Définissez **nom de la classe de l’administrateur appareil** à `com.microsoft.omadm.client.PolicyManagerReceiver`.

Continuer au profil de publication et l’utiliser avec l’application StageNow sur l’appareil. L’application portail d’entreprise reçoit le rôle d’administrateur de l’appareil.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Étape 3 : Inscrire l’appareil dans Intune

Après avoir effectué les deux premières étapes, l’application portail d’entreprise est installée sur l’appareil. L’appareil est prêt à être inscrits dans Intune.

[Inscrire des appareils Android](android-enroll.md) répertorie les étapes. Si vous avez de nombreux périphériques Zebra, il pouvez que vous souhaitez utiliser un [compte de gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md).

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Étape 4 : Créer un profil de gestion de périphérique dans StageNow

Utilisez StageNow pour créer un profil qui configure les paramètres que vous souhaitez gérer sur l’appareil. Pour plus d’informations spécifiques, consultez de Zebra. [Profils](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (ouvre le site Web de Zebra) peut être une bonne ressource.

Lorsque vous créez le profil dans StageNow, sur la dernière étape, sélectionnez **exporter vers MDM**. Cela génère un fichier XML. Enregistrez ce fichier. Vous en avez besoin dans une étape ultérieure.

> [!TIP]
> Il est recommandé de tester le profil avant de le déployer sur des appareils dans votre organisation. Pour tester, dans la dernière étape lors de la création de profils avec StageNow sur votre ordinateur, utilisez le **tester** options. Ensuite, utiliser le fichier StageNow généré avec l’application StageNow sur l’appareil. 
> 
> L’application de StageNow sur l’appareil affiche les journaux générés lorsque vous testez le profil. [Utilisez StageNow ouvre une session sur les appareils Zebra exécutant Android dans Intune](android-zebra-mx-logs-troubleshoot.md) a plus d’informations sur l’utilisation des journaux de StageNow pour comprendre les erreurs.

> [!NOTE]
> Si vous référencez des applications, mettre à jour des packages ou mettre à jour d’autres fichiers dans votre profil StageNow, vous souhaitez l’appareil pour obtenir ces mises à jour. Pour obtenir les mises à jour, l’appareil doit se connecter au serveur de déploiement StageNow lorsque le profil est appliqué. 
> 
> Ou bien, vous pouvez utiliser les fonctionnalités intégrées dans Intune pour obtenir ces modifications, notamment : 
> - Fonctionnalités de gestion des applications à [ajouter](apps-add.md), [déployer](apps-deploy.md), mettre à jour, et [moniteur](apps-monitor.md) applications.
> - Gérer [mises à jour système et application](device-restrictions-android-for-work.md#device-owner-only) sur les appareils exécutant Android Enterprise

Après avoir testé le fichier, l’étape suivante consiste à déployer le profil aux appareils à l’aide d’Intune.

> [!NOTE]
> Déployer un profil sur chaque appareil. S’il existe plusieurs profils StageNow que vous souhaitez déployer sur les appareils, puis exporter les profils StageNow et combiner les paramètres dans un fichier XML unique avant de l’ajouter à Intune. 
> 
> Vous ne voulez pas deux paramètres qui configurent la même propriété dans le même fichier XML. L’objectif consiste à éviter les conflits entre paramètres sur l’appareil.

## <a name="step-5-create-a-profile-in-intune"></a>Étape 5 : Créer un profil dans Intune

Dans Intune, créez un profil de configuration d’appareil :

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : attribuez un nom descriptif au nouveau profil.
    - **Description :** entrez une description pour le profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : sélectionnez **Android**.
    - **Type de profil**: sélectionnez **profil MX (Zebra uniquement)**.

4. Dans **profil MX au format .xml**, ajoutez le fichier de profil XML [que vous avez exporté à partir de StageNow](#step-4-create-a-device-management-profile-in-stagenow) (dans cet article).
5. Sélectionnez **OK** > **Créer** pour enregistrer vos modifications. La stratégie est créée et affichée dans la liste.

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

La prochaine fois que l’appareil vérifie les mises à jour de la configuration, le profil de MX est déployé sur l’appareil. Synchroniser les appareils avec Intune quand les appareils inscrits, puis toutes les 8 heures environ. Vous pouvez également [forcer une synchronisation dans Intune](device-sync.md). Ou, sur l’appareil, ouvrez le **application portail d’entreprise** > **paramètres** > **synchronisation**. 

> [!TIP]
> - Pour des raisons de sécurité, vous ne voyez le texte XML du profil après que l’avoir enregistrée. Le texte est chiffré, et vous voyez uniquement les astérisques (`****`). Pour référence, il est recommandé d’enregistrer des copies des profils MX avant de les ajouter à Intune.
> 
> - Pour mettre à jour un profil après que qu’elle est affectée aux appareils de Zebra, créer un fichier StageNow XML mis à jour, modifier le profil Intune existant et ajouter le nouveau fichier XML de StageNow. Ce nouveau fichier remplace la stratégie StageNow précédente dans le profil.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

[Utiliser les journaux de StageNow pour dépanner les appareils de Zebra](android-zebra-mx-logs-troubleshoot.md).
