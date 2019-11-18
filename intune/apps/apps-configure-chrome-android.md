---
title: Configurer Google Chrome pour les appareils Android à l’aide d’Intune
titleSuffix: Microsoft Intune
description: Utilisez des stratégies de configuration Intune avec Google Chrome pour les appareils Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14e9aa6e82d7b3e24350de8770f02b0a08695e1a
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801661"
---
# <a name="configure-google-chrome-for-android-devices-using-intune"></a>Configurer Google Chrome pour les appareils Android à l’aide d’Intune 

Vous pouvez utiliser une stratégie de configuration d’application Intune pour configurer Google Chrome pour les appareils Android. Les paramètres de l’application peuvent être appliqués automatiquement. Par exemple, vous pouvez définir spécifiquement les signets et URL que vous souhaitez bloquer ou autoriser.

## <a name="prerequisites"></a>Prérequis

- L’appareil Android Entreprise de l’utilisateur doit être inscrit dans Intune. Pour plus d’informations, consultez [Configurer l’inscription des appareils avec profil professionnel Android Entreprise](~/enrollment/android-work-profile-enroll.md).
- Google Chrome est ajouté en tant qu’application Google Play géré. Pour en savoir plus sur Google Play géré, voir [Connecter votre compte Intune à votre compte professionnel Android](~/enrollment/connect-intune-android-enterprise.md).

## <a name="add-the-google-chrome-app-to-intune"></a>Ajouter l’application Google Chrome à Intune

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications** > **Ajouter**, puis ajoutez l’application **Google Play géré**.
3. Accédez à Google Play géré, recherchez **Google Chrome**, puis approuvez.

    ![Rechercher et approuver Google Chrome](~/apps/media/apps-configure-chrome-android/search.png)

4. Affectez Google Chrome à un groupe d’utilisateurs en tant qu’application de type obligatoire. Google Chrome est déployé automatiquement lorsque l’appareil est inscrit dans Intune.

Pour plus d’informations sur l’ajout d’une application de Google Play géré à Intune, consultez [Applications Google Play Store gérées](~/apps/apps-add-android-for-work.md#managed-google-play-store-apps).

## <a name="add-app-configuration-for-managed-ae-devices"></a>Ajouter une configuration d’applications pour les appareils AE managés

1. Dans le volet [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), sélectionnez **Stratégies de configuration d’application** > **Ajouter**.
2. Ajoutez le nom de votre stratégie, choisissez **Appareils gérés** pour le type d’inscription d’appareil, et **Android** pour la plateforme.

    ![Ajouter une stratégie de configuration Google Chrome](~/apps/media/apps-configure-chrome-android/add-policy.png)

3. Cliquez sur **Application associée**, puis sélectionnez **Google Chrome**.

    ![Sélectionner Google Chrome sous Application associée](~/apps/media/apps-configure-chrome-android/associated-app.png)

4. Cliquez sur **Paramètres de configuration**, sélectionnez **Utiliser le concepteur de configuration**, puis cliquez sur **Ajouter** pour sélectionner les clés de configuration.

    ![Ajouter Utiliser le concepteur de configuration](~/apps/media/apps-configure-chrome-android/configuration.png)

    Voici l’exemple des paramètres communs :
    - **Bloquer l’accès à une liste d’URL** : `["*"]`
    - **Autoriser l’accès à une liste d’URL** : `["baidu.com", "youtube.com", "chromium.org", "chrome://*"]`
    - **Signets gérés** : `[{"toplevel_name": "My managed bookmarks folder"  },  {"url": "baidu.com",   "name": "Baidu"},  {"url": "youtube.com", "name": "Youtube"},  {"name": "Chrome links",  "children": [{"url": "chromium.org", "name": "Chromium"},    {"url": "dev.chromium.org", "name": "Chromium Developers"}]}]`
    - **Disponibilité du mode Incognito** : `Incognito mode disabled`

    Une fois que les paramètres de configuration sont ajoutés à l’aide du concepteur de configuration, ils sont répertoriés dans un tableau. 

    ![Paramètres communs](~/apps/media/apps-configure-chrome-android/common-settings.png)

    Les paramètres ci-dessus créent des signets et bloquent l’accès à toutes les URL, à l’exception de `baidu.com`, `yahoo.com`, `chromium.org` et `chrome://`.

5. Cliquez sur **OK**  et **Ajouter** pour ajouter votre stratégie de configuration à Intune.
6. Affectez cette stratégie de configuration à un groupe d’utilisateurs. Pour plus d’informations, consultez [Affecter des applications à des groupes avec Microsoft Intune](~/apps/apps-deploy.md). 

## <a name="verify-the-device-settings"></a>Vérifier les paramètres de l’appareil

Une fois que l’appareil Android est inscrit auprès d’Android Entreprise, l’application Google Chrome gérée avec l’icône de portefeuille est déployée automatiquement.
 
   <img alt="Managed Google Chrome with the portfolio icon" src="~/apps/media/apps-configure-chrome-android/chrome-icon.png" width="350">

Lancez Google Chrome et vous trouverez les paramètres appliqués.

   Signets :<br>
   <img alt="Bookmarks" src="~/apps/media/apps-configure-chrome-android/bookmarks.png" width="350">

   URL bloquée :<br>
   <img alt="Blocked URL" src="~/apps/media/apps-configure-chrome-android/blocked-url.png" width="350">

   Autoriser une URL :<br>
   <img alt="Allow URL" src="~/apps/media/apps-configure-chrome-android/allowed-url.png" width="350">

   Onglet Incognito :<br>
   <img alt="Incognito tab" src="~/apps/media/apps-configure-chrome-android/incognito-tab.png" width="350">

## <a name="troubleshooting"></a>Résolution des problèmes

1. Vérifiez le portail Intune pour surveiller l’état du déploiement de la stratégie.

    ![Surveiller l’état du déploiement de la stratégie](~/apps/media/apps-configure-chrome-android/monitor-status.png)

2. Lancez Google Chrome et accédez à **chrome://policy**. Nous pouvons confirmer si les paramètres sont correctement appliqués.

    ![Confirmer que les paramètres sont correctement appliqués](~/apps/media/apps-configure-chrome-android/confirm.png)

## <a name="additional-information"></a>Informations supplémentaires

- [Ajouter des stratégies de configuration d’applications pour les appareils Android Entreprise gérés](~/app-configuration-policies-use-android.md)
- [Liste des stratégies d’entreprise pour Chrome](https://cloud.google.com/docs/chrome-enterprise/policies/)

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les appareils Android Entreprise entièrement gérés, consultez [Configurer l’inscription Intune d’appareils Android Entreprise entièrement gérés](~/enrollment/android-fully-managed-enroll.md).
