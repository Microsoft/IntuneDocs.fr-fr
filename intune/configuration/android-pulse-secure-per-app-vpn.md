---
title: Profil VPN par application personnalisé pour Android
titleSuffix: Microsoft Intune
description: Découvrez comment créer un profil VPN par application pour les appareils Android gérés par Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f044d42a36717e970abba37009df2e3d0516a046
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73756740"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Utiliser un profil personnalisé Microsoft Intune pour créer un profil VPN par application pour les appareils Android

[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Vous pouvez créer un profil VPN par application pour les appareils Android 5.0 et ultérieur gérés par Intune. Commencez par créer un profil VPN qui utilise le type de connexion Pulse Secure ou Citrix. Ensuite, créez une stratégie de configuration personnalisée qui associe le profil VPN à des applications spécifiques.

Une fois que vous avez affecté la stratégie à votre appareil Android ou à des groupes d’utilisateurs, ces derniers doivent démarrer le client VPN Pulse Secure ou Citrix. Le client VPN autorise ensuite uniquement le trafic provenant des applications spécifiées à utiliser la connexion VPN ouverte.

> [!NOTE]
>
> Seul les types de connexions Pulse Secure et Citrix sont pris en charge pour ce profil.

## <a name="step-1-create-a-vpn-profile"></a>Étape 1 : Créer un profil VPN

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, **Profil VPN par application Android pour toute l’entreprise** est un bon nom de profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Android**.
    - **Type de profil** : sélectionnez **VPN**.

4. Choisissez **Paramètres** > **Configurer**, puis configurez le profil VPN selon les paramètres de la [configuration des paramètres VPN](vpn-settings-configure.md) et des [paramètres Intune VPN pour les appareils Android](vpn-settings-android.md).

Prenez note de la valeur de **Nom de connexion** que vous spécifiez lors de la création du profil VPN. Ce nom est nécessaire lors de l’étape suivante. Par exemple, **MonProfilVpnApp**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Étape 2 : Créer une stratégie de configuration personnalisée

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Donnez un nom explicite au profil personnalisé. Nommez vos profils afin de pouvoir les identifier facilement ultérieurement. Par exemple, **Profil VPN Android OMA-URI personnalisé pour toute l’entreprise** est un bon nom de profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Sélectionnez **Android**.
    - **Type de profil** : Sélectionnez **Personnalisé**.

4. Choisissez **Paramètres** > **Configurer**.
5. Dans le volet **Paramètres OMA-URI personnalisés**, choisissez **Ajouter**.
    - **Nom** : Donnez un nom à votre paramètre.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **OMA-URI** : Entrez `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, où *Name* est le nom de la connexion que vous avez noté à l’étape 1. Dans cet exemple, la chaîne est `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Type de données** : Entrez **Chaîne**.
    - **Valeur** : Entrez une liste séparée par des points-virgules des packages à associer au profil. Par exemple, si vous souhaitez qu’Excel et le navigateur Google Chrome utilisent la connexion VPN, entrez : `com.microsoft.office.excel;com.android.chrome`.

![Exemple de stratégie personnalisée de VPN par application Android](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Définir votre liste d’applications comme liste rouge ou liste verte (facultatif)

Pour entrer une liste d’applications qui *ne peuvent pas* utiliser la connexion VPN, utilisez la valeur **BLACKLIST**. Toutes les autres applications se connectent par le biais du VPN. Vous pouvez également utiliser la valeur **WHITELIST** pour entrer une liste d’applications qui *peuvent* utiliser la connexion VPN. Les applications qui ne figurent pas dans la liste ne se connectent pas par le biais du VPN.

1. Dans le volet **Paramètres OMA-URI personnalisés**, choisissez **Ajouter**.
2. Entrez un nom de paramètre.
3. Dans **OMA-URI**, entrez `./Vendor/MSFT/VPN/Profile/*Name*/Mode`, où *Name* est le nom du profil VPN que vous avez noté à l’étape 1. Dans notre exemple, la chaîne est `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. Dans **Type de données**, entrez **Chaîne**.
5. Dans **Valeur**, entrez **BLACKLIST** ou **WHITELIST**.

## <a name="step-3-assign-both-policies"></a>Étape 3 : Affecter les deux stratégies

[Affectez les deux profils d’appareil](device-profile-assign.md) aux utilisateurs ou appareils nécessaires.
