---
title: Paramètres personnalisés pour les appareils Windows Holographic for Business dans Microsoft Intune - Azure | Microsoft Docs
description: Créez un profil personnalisé pour utiliser les paramètres OMA-URI sur les appareils exécutant Windows Holographic for Business dans Microsoft Intune. Vous pouvez définir les paramètres du fournisseur de services de configuration de stratégies AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates et ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8ba5078d304c0e9d6b10e4efb868642323c901c
ms.sourcegitcommit: 2795255e89cbe97d0b17383d446cca57c7335016
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47403576"
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Paramètres personnalisés pour les appareils exécutant Windows Holographic for Business dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Utilisez le profil Microsoft Intune **personnalisé** pour Windows Holographic for Business pour déployer des paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pouvant servir à contrôler les fonctionnalités sur des appareils. Windows Holographic for Business rend disponibles de nombreux paramètres de fournisseurs de services de configuration. Pour avoir une vue d’ensemble des fournisseur de services de configuration, consultez [Présentation des fournisseurs de services de configuration pour les professionnels de l’informatique](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers). Pour connaître les fournisseurs de services de configuration pris en charge par Windows Holographique, consultez [Fournisseurs de services de configuration pris en charge dans Windows Holographique](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens).

Si vous recherchez un paramètre particulier, n’oubliez pas que le [profil de restriction d’appareil Windows Holographic for Business](device-restrictions-windows-holographic.md) contient de nombreux paramètres intégrés et ne nécessite pas de spécifier des valeurs personnalisées.

## <a name="create-the-custom-oma-uri-profile"></a>Créer le profil OMA-URI personnalisé

1. Suivez les instructions dans [Configurer des paramètres d'appareil personnalisés dans Microsoft Intune](custom-settings-configure.md) pour commencer.
2. Dans **Créer un profil**, choisissez **Paramètres** pour ajouter un ou plusieurs paramètres OMA-URI.
3. Dans **Paramètres OMA-URI personnalisés**, cliquez sur **Ajouter** pour ajouter une nouvelle valeur. Vous pouvez également cliquer sur **Exporter** pour créer une liste de toutes les valeurs que vous avez configurées dans un fichier de valeurs séparées par des virgules (.csv).
4. Pour chaque paramètre OMA-URI à ajouter, entrez les informations suivantes :
  - **Nom du paramètre** : Affectez un nom unique au paramètre OMA-URI pour mieux l’identifier dans la liste des paramètres.
  - **Description du paramètre** : Si vous le souhaitez, entrez une description du paramètre.
  - **Type de données** : Choisissez parmi :
    - **Chaîne**
    - **Chaîne (XML)**
    - **Date et heure**
    - **Entier**
    - **Virgule flottante**
    - **Booléen**
  - **OMA-URI (sensible à la casse)**  : Entrez l’identificateur OMA-URI pour lequel vous voulez fournir un paramètre.
  - **Valeur** : Entrez la valeur à associer à l’identificateur OMA-URI que vous avez entré.
5. Quand vous avez terminé, revenez à **Créer un profil** et cliquez sur **Créer**. Le profil est créé et apparaît dans la liste des profils.

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

La liste complète de tous les fournisseurs de services de configuration pris en charge par Windows Holographique est disponible dans [Fournisseurs de services de configuration pris en charge dans Windows Holographique](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Les paramètres ne sont pas tous compatibles avec toutes les versions de Windows Holographique. Le tableau de l’article Windows indique quelles versions sont prises en charge pour chaque fournisseur de services de configuration.

En outre, Intune ne prend pas en charge tous les paramètres mentionnés dans l’article. Pour savoir si Intune prend en charge le paramètre de votre choix, ouvrez l’article relatif à ce paramètre. Chaque page de paramètre indique ses opérations prises en charge. Pour fonctionner avec Intune, le paramètre doit prendre en charge les opérations **Ajouter** ou **Remplacer**.
