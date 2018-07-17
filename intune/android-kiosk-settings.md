---
title: Paramètres kiosque pour Android dans Microsoft Intune - Azure | Microsoft Docs
description: Configurez vos appareils kiosque Android comme kiosques à une ou plusieurs applications.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f1aa88264ef277863f58d21baaa136c140c5c287
ms.sourcegitcommit: e01945bff19157fa7acaa4f7975b0f2a8b3a73f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37949541"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Paramètres kiosque pour les appareils Android dans Intune

Vous pouvez configurer un appareil kiosque avec une ou plusieurs applications à l’aide des paramètres de configuration d’appareil. Quand un appareil est en mode kiosque, son utilisation est limitée aux applications ou liens web définis par le profil de restriction. 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>Restreindre un appareil Android kiosque à une seule application

Si le profil de restriction d’un appareil kiosque est défini sur **Mode kiosque** = **Kiosque à application unique**, les utilisateurs ne peuvent accéder qu’à une seule application. Quand un appareil configuré dans ce mode démarre, l’application spécifique démarre. Les utilisateurs ne peuvent pas ouvrir de nouvelles applications ou basculer vers une autre application.

1. Vérifiez que l’application que vous souhaitez utiliser sur l’appareil kiosque a été [déployée sur l’appareil](apps-deploy.md) et que vous avez affecté l’application au groupe d’appareils que vous avez créé pour vos appareils kiosque.
2. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Dans le panneau **Créer un profil**, définissez les champs suivants :
     - **Nom**
     - **Plateforme** : Android Entreprise
     - **Type de profil** : Propriétaire de l’appareil uniquement > Restrictions de l’appareil
4. Choisissez **Paramètres** > **Kiosque**.
5. Pour **Mode kiosque**, choisissez **Kiosque à application unique**.
6. Choisissez **Sélectionner une application gérée**, puis sélectionnez l’application Google Play gérée qui doit être la seule application disponible pour les appareils utilisant ce profil.
7. Choisissez **OK** > **OK** > **OK** > **Créer**.
8. Choisissez le profil que vous venez de créer > **Affectations**.
9. Sous **Affecter à**, choisissez **Groupes sélectionnés**.
10. Choisissez **Sélectionner les groupes à inclure** > choisissez le groupe d’appareils que vous avez créé pour vos appareils kiosque > **Sélectionner**.

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>Restreindre un appareil kiosque à un ensemble d’applications ou de liens web

Si le profil de restriction d’un appareil kiosque est défini sur **Mode kiosque** = **Kiosque multi-application**, les utilisateurs peuvent accéder uniquement au nombre limité d’applications que vous configurez. Vous pouvez également définir un ensemble de liens web que les utilisateurs peuvent visiter. Quand la stratégie est appliquée, les utilisateurs voient des icônes pour les applications autorisées dans l’écran d’accueil.

Pour configurer un appareil kiosque Android avec plusieurs applications, suivez ces étapes principales :

1. [Importer et déployer l’application Managed Home Screen à partir de Google Play géré](#import-and -deploy-the-managed-home-screen-app)
2. [Ajouter et affecter des applications qui peuvent être utilisées en mode kiosque](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (Facultatif) [Ajouter des liens web qui peuvent être utilisés en mode kiosque](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deply-the-managed-home-screen-app"></a>Importer et déployer l’application Managed Home Screen

1. Accédez à la [page Managed Home Screen sur Google Play](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise) et connectez-vous avec le même compte que celui que vous utilisez pour d’autres applications Google Play gérées.
2. Choisissez **Approuver**.
3. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Applications mobiles** > **Google Play géré** > **Synchroniser**.
4. Choisissez **Applications** > **Managed Home Screen** > **Affectations** > **Ajouter un groupe**.
5. Sous **Type d’affectation**, choisissez **Obligatoire**.
6. Choisissez **Groupes inclus** > **Sélectionner les groupes à inclure** > choisissez le groupe d’appareils que vous avez créé pour vos appareils kiosque > **Sélectionner** > **OK** > **OK** > **Enregistrer**.

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>Ajouter et affecter des applications qui peuvent être utilisées en mode kiosque

Pour chaque application que vous souhaitez rendre disponible sur les appareils kiosque, effectuez les étapes suivantes :

1. [Ajoutez l’application à Intune](store-apps-android.md).
2. Choisissez **Applications mobiles** > **Applications** > choisissez l’application > **Affectations** > **Ajouter un groupe**.
3. Sous **Type d’affectation**, choisissez **Obligatoire**.
4. Choisissez **Groupes inclus** > **Sélectionner les groupes à inclure** > choisissez le groupe d’appareils que vous avez créé pour vos appareils kiosque > **Sélectionner** > **OK** > **OK** > **Enregistrer**.

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>Ajouter des liens web qui peuvent être utilisés en mode kiosque

1. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Applications mobiles** > **Applications** > **Ajouter**.
2. Sous **Type d’application**, choisissez **Lien web**.
3. Choisissez **Configurer** et fournissez les informations requises. Vous n’avez pas besoin d’ajouter une image de logo, car elle est récupérée automatiquement à partir de favicon.ico sur le site web.
4. Choisissez **OK** > **Ajouter**.

Vérifiez que vous avez déployé une application de navigateur web sur les appareils kiosque à l’aide de [Mobile Apps](apps-add.md).

### <a name="create-a-multi-app-kiosk-profile"></a>Créer un profil de kiosque multi-application

1. Accédez au [portail Intune](https://portal.azure.com) et choisissez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Dans le panneau **Créer un profil**, définissez les champs suivants :
     - **Nom** : tapez un nom intuitif
     - **Plateforme** : Android Entreprise
     - **Type de profil** : Propriétaire de l’appareil uniquement > Restrictions de l’appareil
4. Choisissez **Paramètres** > **Kiosque**.
5. Pour **Mode kiosque**, choisissez **Kiosque multi-application**.
6. Choisissez **Ajouter**, puis sélectionnez les applications ou liens web que vous souhaitez rendre accessibles aux appareils utilisant ce profil.
7. Choisissez **OK** > **OK** > **OK** > **Créer**.
8. Choisissez le profil que vous venez de créer > **Affectations**.
9. Sous **Affecter à**, choisissez **Groupes sélectionnés**.
10. Choisissez **Sélectionner les groupes à inclure** > choisissez le groupe d’appareils que vous avez créé pour vos appareils kiosque > **Sélectionner** > **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes
[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
