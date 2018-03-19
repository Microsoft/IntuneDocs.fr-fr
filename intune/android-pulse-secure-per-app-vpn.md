---
title: Profil VPN par application pour Android - Pulse Secure
titlesuffix: Azure portal
description: "Découvrez comment créer un profil VPN par application pour les appareils Android gérés par Intune."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2a207f15e7c5b678368eeb54e8452638ff5a01ef
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Utiliser un profil personnalisé Microsoft Intune pour créer un profil VPN par application pour les appareils Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Vous pouvez créer un profil VPN par application pour les appareils Android 5.0 et ultérieur gérés par Intune. Tout d’abord, créez un profil VPN qui utilise le type de connexion Pulse Secure. Ensuite, créez une stratégie de configuration personnalisée qui associe le profil VPN à des applications spécifiques.

Une fois que vous avez attribué la stratégie à votre appareil Android ou vos groupes d’utilisateurs, les utilisateurs doivent démarrer le VPN PulseSecure. PulseSecure autorise alors uniquement le trafic provenant des applications spécifiées à utiliser la connexion VPN ouverte.

> [!NOTE]
>
> Seul le type de connexion sécurisé Pulse Secure est pris en charge pour ce profil.


## <a name="step-1-create-a-vpn-profile"></a>Étape 1 : Créer un profil VPN


1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Configuration de l’appareil**.
2. Dans le volet **Configuration de l’appareil**, sous la section **Gérer**, choisissez **Profils**.
2. Dans le volet de la liste des profils, choisissez **Créer un profil**.
3. Dans le volet **Créer un profil**, entrez un **Nom** et éventuellement une **Description** pour le profil VPN.
4. Dans la liste déroulante **Plateforme**, choisissez **Android**.
5. Dans la liste déroulante **Type de profil**, choisissez **VPN**.
3. Choisissez **Paramètres** > **Configurer**, puis configurez le profil VPN selon les paramètres de la [configuration des paramètres VPN](vpn-settings-configure.md) et des [paramètres Intune VPN pour les appareils Android](vpn-settings-android.md).

Prenez note de la valeur de **Nom de connexion** que vous spécifiez lors de la création du profil VPN. Ce nom est nécessaire lors de l’étape suivante. Par exemple, **MonProfilVpnApp**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Étape 2 : Créer une stratégie de configuration personnalisée

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Configuration de l’appareil**.
2. Dans le volet **Configuration de l’appareil**, sous la section **Gérer**, choisissez **Profils**.
3. Dans le volet des profils, cliquez sur **Créer un profil**.
4. Dans le volet **Créer un profil**, tapez un **Nom** et une **Description** pour le profil personnalisé.
5. Dans la liste déroulante **Plateforme**, choisissez **Android**.
6. Dans la liste déroulante **Type de profil**, choisissez **Personnalisé**.
7. Choisissez **Paramètres** > **Configurer**.
3. Dans le volet **Paramètres OMA-URI personnalisés**, choisissez **Ajouter**.
    - Entrez un nom de paramètre.
    - Pour **OMA-URI**, spécifiez la chaîne suivante : **./Vendor/MSFT/VPN/Profile/*Nom*/PackageList**, où *Nom* est le nom du profil VPN que vous avez noté à l’étape 1. Dans cet exemple, la chaîne est **./Vendor/MSFT/VPN/Profile/MonProfilVpnApp/PackageList**.
    - Pour **Type de données**, spécifiez **Chaîne**.
    - Pour **Valeur**, créez une liste délimitée par des points-virgules des packages à associer au profil. Par exemple, si vous souhaitez qu’Excel et le navigateur Google Chrome utilisent la connexion VPN, entrez : **com.microsoft.office.excel;com.android.chrome**.

![Exemple de stratégie personnalisée de VPN par application Android](./media/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Définir votre liste d’applications comme liste rouge ou liste verte (facultatif)
  Vous pouvez spécifier une liste d’applications qui *ne peuvent pas* utiliser la connexion VPN en utilisant une valeur **BLACKLIST**. Toutes les autres applications se connectent par le biais du VPN.
Vous pouvez également utiliser la valeur **WHITELIST** pour spécifier une liste d’applications qui *peuvent* utiliser la connexion VPN. Les applications qui ne figurent pas dans la liste ne se connectent pas par le biais du VPN.
  1.    Dans le volet **Paramètres OMA-URI personnalisés**, choisissez **Ajouter**.
  2.    Entrez un nom de paramètre.
  3.    Pour **OMA-URI**, utilisez la chaîne suivante : **./Vendor/MSFT/VPN/Profile/*Nom*/Mode**, où *Nom* est le nom du profil VPN que vous avez noté à l’étape 1. Dans notre exemple, la chaîne est **./Vendor/MSFT/VPN/Profile/MonProfilVpnApp/Mode**.
  4.    Pour **Type de données**, spécifiez **Chaîne**.
  5.    Pour **Valeur**, entrez **BLACKLIST** ou **WHITELIST**.



## <a name="step-3-assign-both-policies"></a>Étape 3 : Affecter les deux stratégies

Suivez les instructions du [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md) pour affecter les deux profils aux utilisateurs ou appareils nécessaires.
