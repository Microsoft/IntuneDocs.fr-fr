---
title: Paramètres personnalisés - Appareils Windows Holographic for Business - Microsoft Intune
description: Ajoutez ou créez un profil personnalisé pour utiliser les paramètres OMA-URI sur les appareils exécutant Windows Holographic for Business dans Microsoft Intune, y compris Microsoft HoloLens. Vous pouvez définir les paramètres du fournisseur de services de configuration de stratégies AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates et ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.article: article
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.topic: reference
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6547149a7de81b06ed82d308ece0527151225d28
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735023"
---
# <a name="use-custom-settings-for-windows-holographic-for-business-devices-in-intune"></a>Utiliser des paramètres personnalisés pour les appareils Windows Holographic for Business dans Intune

À l’aide de Microsoft Intune, vous pouvez ajouter ou créer des paramètres personnalisés pour vos appareils Windows Holographic for Business au moyen de « profils personnalisés ». Les profils personnalisés sont une fonctionnalité dans Intune. Ils sont conçus pour ajouter des paramètres et des fonctionnalités d’appareil qui ne sont pas intégrés à Intune.

Les profils personnalisés Windows Holographic for Business utilisent des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour configurer différentes fonctionnalités. Ces paramètres sont généralement utilisés par les fabricants d’appareils mobiles pour contrôler les fonctionnalités sur l’appareil.

Windows Holographic for Business rend disponibles de nombreux paramètres de fournisseurs de services de configuration. Pour avoir une vue d’ensemble des fournisseur de services de configuration, consultez [Présentation des fournisseurs de services de configuration pour les professionnels de l’informatique](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Pour connaître les fournisseurs de services de configuration pris en charge par Windows Holographique, consultez [Fournisseurs de services de configuration pris en charge dans Windows Holographique](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Si vous recherchez un paramètre spécifique, n’oubliez pas que le [profil de restriction d’appareil Windows Holographic for Business](device-restrictions-windows-holographic.md) comporte de nombreux paramètres intégrés. Vous n’aurez donc peut-être pas besoin d’entrer des valeurs personnalisées.

Cet article vous montre comment créer un profil personnalisé pour les appareils Windows Holographic for Business. Il inclut également une liste des paramètres OMA-URI recommandés.

## <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `hololens custom profile`.
    - **Description :** entrez une description pour le profil.
    - **Plateforme** : choisissez **Windows 10 et ultérieur**.
    - **Type de profil** : choisissez **Personnalisé**.

4. Dans **Paramètres OMA-URI personnalisés**, sélectionnez **Ajouter**. entrez les paramètres suivants :

    - **Nom** : entrez un nom unique pour paramètre OMA-URI, qui vous permette de l’identifier dans la liste des paramètres.
    - **Description** : entrez une description qui donne une vue d’ensemble du paramètre et tout autre détail important.
    - **OMA-URI (sensible à la casse)**  : entrez l’identificateur OMA-URI à utiliser comme paramètre.
    - **Type de données** : choisissez le type de données que vous allez utiliser pour ce paramètre OMA-URI. Les options disponibles sont les suivantes :

        - Chaîne
        - Chaîne (fichier XML)
        - Date et heure
        - Entier
        - Virgule flottante
        - Booléen
        - Base64 (fichier)

    - **Valeur** : entrez la valeur de données à associer à l’identificateur OMA-URI que vous avez entré. La valeur dépend du type de données que vous avez sélectionné. Par exemple, si vous choisissez **Date et heure**, sélectionnez la valeur à partir d’un sélecteur de dates.

    Une fois que vous avez ajouté des paramètres, vous pouvez sélectionner **Exporter**. L’option **Exporter** crée une liste de toutes les valeurs que vous avez ajoutées dans un fichier de valeurs séparées par des virgules (.csv).

5. Cliquez sur **OK** pour enregistrer vos modifications. Continuez à ajouter d’autres paramètres si besoin.
6. Quand vous avez terminé, choisissez **OK** > **Créer** pour créer le profil Intune. Quand vous avez terminé, votre profil apparaît dans la liste **Configuration de l’appareil - Profils**.

## <a name="recommended-custom-settings"></a>Paramètres personnalisés recommandés

Les paramètres suivants sont utiles pour les appareils exécutant Windows Holographic for Business :

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Entier<br/>0 : Non autorisé<br/>1 : Autorisé (par défaut)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Entier<br/>0 : Le service de mise à jour n’est pas autorisé <br/>1 – Le service de mise à jour est autorisé (par défaut)|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Entier<br/>0 : Non autorisé<br/>1 : Autorisé (par défaut)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Entier<br/>0 : Non configuré L’appareil installe toutes les mises à jour applicables.<br/>1 – L’appareil installe seulement les mises à jour applicables qui figurent dans la liste des mises à jour approuvées. Définissez cette stratégie sur 1 si le département informatique veut contrôler le déploiement des mises à jour sur les appareils, par exemple quand des tests sont nécessaires avant un déploiement.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Entier entre 0 et 23, où 0=minuit et 23=23h<br/>La valeur par défaut est 3.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Chaîne<br/>URL : L’appareil vérifie l’existence de mises à jour auprès du serveur WSUS à l’URL spécifiée.<br/>Non configuré : L’appareil vérifie l’existence de mises à jour auprès de Microsoft Update.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**Important**<br/>Vous devez lire et accepter le CLUF de la mise à jour pour le compte de vos utilisateurs finaux. Ne pas le faire constitue une violation des obligations légales ou contractuelles.|Nœud pour les approbations des mises à jour et l’acceptation du CLUF pour le compte de l’utilisateur final.<br/><br/>Pour plus d’informations, consultez [Mettre à jour le CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp).|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**Important**<br/>L’article Fournisseur de services de configuration AppLocker utilise des exemples XML avec une séquence d’échappement. Pour configurer les paramètres avec des profils personnalisés Intune, vous devez utiliser du XML brut.|Chaîne<br/>Pour plus d’informations, consultez [CSP AppLocker](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp).|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Entier<br/>0 - supprimer immédiatement quand l’appareil revient à un état sans utilisateur actif<br/>1 - supprimer au niveau du seuil de capacité de stockage (par défaut)<br/>2 - supprimer au niveau du seuil de capacité de stockage et du seuil d’inactivité du profil|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|Booléen<br/>True - activer<br/>False - désactiver (par défaut)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|Entier<br/>La valeur par défaut est 30.|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|Entier<br/>La valeur par défaut est 25.|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Type de données|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|Entier<br/>La valeur par défaut est 50.|

## <a name="find-the-policies-you-can-configure"></a>Trouver les stratégies que vous pouvez configurer

La liste complète de tous les fournisseurs de services de configuration pris en charge par Windows Holographique est disponible dans [Fournisseurs de services de configuration pris en charge dans Windows Holographique](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Les paramètres ne sont pas tous compatibles avec toutes les versions de Windows Holographique. Le tableau dans [Fournisseurs de services de configuration pris en charge dans Windows Holographique](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) liste les versions prises en charge pour chaque fournisseur de services de configuration.

De plus, Intune ne prend pas en charge tous les paramètres listés dans [Fournisseurs de services de configuration pris en charge dans Windows Holographique](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Pour savoir si Intune prend en charge le paramètre de votre choix, ouvrez l’article relatif à ce paramètre. Chaque page de paramètre indique ses opérations prises en charge. Pour fonctionner avec Intune, le paramètre doit prendre en charge les opérations **Ajouter** ou **Remplacer**.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](device-profile-assign.md).

Découvrez comment créer un profil personnalisé sur les [appareils Windows 10](../custom-settings-windows-10.md).
