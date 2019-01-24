---
title: Mettre hors service ou réinitialiser des appareils avec Microsoft Intune - Azure | Microsoft Docs
description: Mettez hors service ou réinitialisez un appareil sur un appareil Android, Profil professionnel Android, iOS, macOS ou Windows avec Microsoft Intune. Découvrez également comment supprimer un appareil d’Azure Active Directory.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: ''
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fdb787e-084f-4507-9c63-c96b13bfcdf9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1866d658503cb2dcdf482a050d7bbd73a914858b
ms.sourcegitcommit: 398b8a0d98e928b3406f59ab3d061554643ef60b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2019
ms.locfileid: "54400022"
---
# <a name="remove-devices-by-using-wipe-retire-or-manually-unenrolling-the-device"></a>Supprimer des appareils avec la réinitialisation, la mise hors service ou la désinscription manuelle de l’appareil

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Avec les actions **Mettre hors service** et **Réinitialiser**, vous pouvez supprimer d’Intune les appareils dont vous n’avez plus besoin, qui ont été réaffectés ou qui sont manquants. Les utilisateurs peuvent également émettre une commande à distance à partir de l’application Portail d’entreprise Intune sur les appareils personnels inscrits dans Intune.

> [!NOTE]
> Avant de supprimer un utilisateur d’Azure Active Directory (Azure AD), utilisez l’action **Réinitialiser** ou **Mettre hors service** pour tous les appareils qui sont associés à cet utilisateur. Si vous supprimez d’Azure Active Directory des utilisateurs avec des appareils gérés, Intune ne peut plus réinitialiser ou mettre hors service ces appareils.

## <a name="wipe"></a>Réinitialisation

L’action **Réinitialiser** rétablit les paramètres d’usine d’un appareil. Les données utilisateur sont conservées si vous avez coché la case **Conserver le compte d’utilisateur et l’état d’inscription**. Sinon, le lecteur est effacé de manière sécurisée.

|Action Réinitialiser|**Conserver le compte d’utilisateur et l’état d’inscription**|Supprimé de la gestion Intune|Description|
|:-------------:|:------------:|:------------:|------------|
|**Réinitialisation**| Désactivée | Oui | Efface tous les comptes d’utilisateur, les données, les stratégies de gestion des appareils mobiles et les paramètres. Réinitialise le système d’exploitation à son état et ses paramètres par défaut.|
|**Réinitialisation**| Activée | Non | Réinitialise toutes les stratégies de gestion des appareils mobiles. Conserve les données et les comptes d’utilisateur. Réinitialise les paramètres utilisateur par défaut. Réinitialise le système d’exploitation à son état et ses paramètres par défaut.|

L’option **Conserver le compte d’utilisateur et l’état d’inscription** est disponible uniquement pour Windows 10 version 1709 ou ultérieure.

Les stratégies MDM seront réappliquées lors de la prochaine connexion de l’appareil à Intune.

Une réinitialisation est utile pour réinitialiser un appareil avant de le donner à un nouvel utilisateur, ou en cas de perte ou de vol de l’appareil. Soyez prudent quand vous sélectionnez **Réinitialiser**. Les données sur l’appareil ne peuvent pas être récupérées.

### <a name="wiping-a-device"></a>Réinitialisation d’un appareil

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Appareils** > **Tous les appareils**.
4. Sélectionnez le nom de l’appareil à réinitialiser.
5. Dans le volet qui montre le nom de l’appareil, sélectionnez **Réinitialiser**.
6. Pour Windows 10 version 1709 ou ultérieure, vous avez également l’option **Conserver le compte d’utilisateur et l’état d’inscription**. 
    
    |Éléments conservés lors d’une réinitialisation |Éléments non conservés|
    | -------------|------------|
    |Comptes d’utilisateur associés à l’appareil|Fichiers utilisateur|
    |État de l’ordinateur \(jonction de domaine, jonction à Azure AD)| Applications installées par l’utilisateur \(applications Win32 et du Store)|
    |Inscription à la Gestion des appareils mobiles (MDM)|Paramètres d’appareil autres que les paramètres par défaut|
    |Applications OEM installées \(applications Win32 et du Store)||
    |Profil utilisateur||
    |Données utilisateur hors du profil utilisateur||
    |Ouverture de session automatique de l’utilisateur|| 
    
         
7. Pour confirmer la réinitialisation, sélectionnez **Oui**.

Si l’appareil est allumé et connecté, la propagation de l’action **Réinitialiser** prend moins de 15 minutes, quel que soit le type de l’appareil.

## <a name="retire"></a>Mettre hors service

L’action **Mettre hors service** supprime les paramètres, les profils de messagerie et les données de l’application gérée (le cas échéant) qui ont été affectés avec Intune. L’appareil n’est plus géré par Intune. Cela se produit la prochaine fois que l’appareil s’enregistre et qu’il reçoit l’action **Mettre hors service** à distance.

**Mettre hors service** laisse les données personnelles de l’utilisateur sur l’appareil.  

Les tableaux suivants décrivent quelles données sont supprimées et l’effet de l’action **Mettre hors service** sur les données qui restent sur l’appareil après la suppression des données d’entreprise.

### <a name="ios"></a>iOS

|Type de données|iOS|
|-------------|-------|
|Applications d’entreprise et données associées installées par Intune|**Applications installées à l’aide du Portail d’entreprise :** Pour les applications épinglées au profil de gestion, toutes les applications et données de ces applications sont supprimées. Ces applications comprennent les applications installées à l’origine à partir de l’App Store et gérées par la suite comme applications d’entreprise. <br /><br /> **Applications Microsoft qui utilisent la gestion des applications mobiles et ont été installées à partir de l’App Store :** Pour les applications qui ne sont pas gérées par le Portail d’entreprise, les données d’entreprise protégées par le chiffrement de la gestion des applications mobiles (MAM) dans le stockage local des applications sont supprimées. Les données protégées par le chiffrement MAM extérieures à l’application restent chiffrées et inutilisables, mais ne sont pas supprimées. Les données d’application personnelles et les applications ne sont pas supprimées.|
|Paramètres|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|
|Paramètres de profil Wi-Fi et VPN|Supprimé.|
|Paramètres de profil de certificat|Les certificats sont supprimés et révoqués.|
|Agent de gestion|Le profil de gestion est supprimé.|
|E-mail|Les profils de messagerie provisionnés par le biais d’Intune sont supprimés. Les e-mails mis en cache sur l’appareil sont supprimés.|
|Disjonction d’Azure AD|L’enregistrement Azure AD est supprimé.|

### <a name="android"></a>Android

|Type de données|Android|Android Samsung Knox Standard|
|-------------|-----------|------------------------|
|Liens web|Supprimé.|Supprimé.|
|Applications Google Play non gérées|Les applications et les données sont toujours installées. <br /> <br />Les données d’applications d’entreprise protégées par le chiffrement de la gestion des applications mobiles (MAM) dans le stockage local des applications sont supprimées. Les données protégées par le chiffrement MAM extérieures à l’application restent chiffrées et inutilisables, mais ne sont pas supprimées. |Les applications et les données sont toujours installées. <br /> <br />Les données d’applications d’entreprise protégées par le chiffrement de la gestion des applications mobiles (MAM) dans le stockage local des applications sont supprimées. Les données protégées par le chiffrement MAM extérieures à l’application restent chiffrées et inutilisables, mais ne sont pas supprimées.|
|Applications métier non gérées|Les applications et les données sont toujours installées.|Les applications sont désinstallées et les données locales propres aux applications sont supprimées. Aucune donnée extérieure à l’application (par exemple, sur une carte SD) n’est supprimée.|
|Applications Google Play gérées|Les données d’application sont supprimées. L’application n’est pas supprimée. Les données protégées par le chiffrement MAM (Gestion des applications mobiles) extérieures à l’application (par exemple, une carte SD) restent chiffrées et inutilisables, mais ne sont pas supprimées.|Les données d’application sont supprimées. L’application n’est pas supprimée. Les données protégées par le chiffrement MAM extérieures à l’application (par exemple, une carte SD) restent chiffrées, mais ne sont pas supprimées.|
|Applications métier gérées|Les données d’application sont supprimées. L’application n’est pas supprimée. Les données protégées par le chiffrement MAM extérieures à l’application (par exemple, une carte SD) restent chiffrées et inutilisables, mais ne sont pas supprimées.|Les données d’application sont supprimées. L’application n’est pas supprimée. Les données protégées par le chiffrement MAM extérieures à l’application (par exemple, une carte SD) restent chiffrées et inutilisables, mais ne sont pas supprimées.|
|Paramètres|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|
|Paramètres de profil Wi-Fi et VPN|Supprimé.|Supprimé.|
|Paramètres de profil de certificat|Les certificats sont révoqués, mais pas supprimés.|Les certificats sont supprimés et révoqués.|
|Agent de gestion|Le privilège d'administrateur d'appareil est révoqué.|Le privilège d'administrateur d'appareil est révoqué.|
|E-mail|N/A (les profils de messagerie ne sont pas pris en charge par les appareils Android)|Les profils de messagerie provisionnés par le biais d’Intune sont supprimés. Les e-mails mis en cache sur l’appareil sont supprimés.|
|Disjonction d’Azure AD|L’enregistrement Azure AD est supprimé.|L’enregistrement Azure AD est supprimé.|

### <a name="android-work-profile"></a>Profil professionnel Android

La suppression des données d’entreprise d’un appareil avec profil professionnel Android supprime l’ensemble des données, applications et paramètres dans le profil professionnel de l’appareil. L’appareil est retiré de la gestion avec Intune. La réinitialisation n’est pas prise en charge pour les profils professionnels Android.

### <a name="android-enterprise-kiosk-devices"></a>Appareils kiosque Android Entreprise

Vous pouvez réinitialiser seulement des appareils en mode kiosque. Vous ne pouvez pas mettre hors service des appareils Android en mode kiosque.


### <a name="macos"></a>macOS

|Type de données|macOS|
|-------------|-------|
|Paramètres|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|
|Paramètres de profil Wi-Fi et VPN|Supprimé.|
|Paramètres de profil de certificat|Les certificats qui ont été déployées via MDM sont supprimés et révoqués.|
|Agent de gestion|Le profil de gestion est supprimé.|
|Outlook|Si l’accès conditionnel est activé, l’appareil ne reçoit pas de nouveau courrier.|
|Disjonction d’Azure AD|L’enregistrement Azure AD est supprimé.|

### <a name="windows"></a>Windows

|Type de données|Windows 8.1 (MDM) et Windows RT 8.1|Windows RT|Windows Phone 8.1 et Windows Phone 8|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Applications d’entreprise et données associées installées par Intune|Les clés sont révoquées pour les fichiers protégées par EFS. L’utilisateur ne peut pas ouvrir les fichiers.|Les applications d’entreprise ne sont pas supprimées.|Les applications installées à l’origine par le biais du portail d’entreprise sont désinstallées. Les données des applications de l'entreprise sont supprimées.|Les applications sont désinstallées. Les clés de chargement indépendant (sideloading) sont supprimées.<br>Pour Windows 10 versions 1703 (Creator Update) et ultérieures, les applications Office 365 ProPlus ne sont pas supprimées.|
|Paramètres|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|Les configurations qui ont été définies par la stratégie Intune ne sont plus appliquées. Les utilisateurs peuvent modifier les paramètres.|
|Paramètres de profil Wi-Fi et VPN|Supprimé.|Supprimé.|Non pris en charge.|Supprimé.|
|Paramètres de profil de certificat|Les certificats sont supprimés et révoqués.|Les certificats sont supprimés et révoqués.|Non pris en charge.|Les certificats sont supprimés et révoqués.|
|E-mail|Supprime les e-mails qui sont activés pour le système EFS. Cela comprend les e-mails et pièces jointes dans l’application Courrier pour Windows.|Non pris en charge.|Les profils de messagerie provisionnés par le biais d’Intune sont supprimés. Les e-mails mis en cache sur l’appareil sont supprimés.|Supprime les e-mails qui sont activés pour le système EFS. Cela comprend les e-mails et pièces jointes dans l’application Courrier pour Windows. Supprime les comptes de messagerie approvisionnés par Intune.|
|Disjonction d’Azure AD|Non.|Non.|L’enregistrement Azure AD est supprimé.|Non applicable. Sur Windows 10, vous ne pouvez pas mettre hors service des appareils joints à Azure AD.|

### <a name="retire"></a>Mettre hors service

1. Connectez-vous à [Intune dans le portail Azure](https://aka.ms/intuneportal).
2. Dans le volet **Appareils**, sélectionnez **Tous les appareils**.
3. Sélectionnez le nom de l’appareil à mettre hors service.
4. Dans le volet qui montre le nom de l’appareil, sélectionnez **Mettre hors service**. Pour confirmer, sélectionnez **Oui**.

Si l’appareil est allumé et connecté, la propagation de l’action **Mettre hors service** prend moins de 15 minutes, quel que soit le type de l’appareil.

## <a name="delete-devices-from-the-intune-portal"></a>Supprimer des appareils à partir du portail Intune

Pour supprimer des appareils à partir du portail Intune, vous pouvez accéder au volet de l’appareil spécifique. La prochaine fois que l’appareil se connecte, toutes les données d’entreprise qu’il contient seront supprimées.

1. Connectez-vous à [Intune dans le portail Azure](https://aka.ms/intuneportal).
2. Choisissez **Appareils** > **Tous les appareils** > choisissez les appareils à supprimer > **Supprimer**.

### <a name="automatically-delete-devices-with-cleanup-rules"></a>Supprimer automatiquement des appareils avec des règles de nettoyage
Vous pouvez configurer Intune pour supprimer automatiquement les appareils qui semblent inactifs, obsolètes ou non réactifs. Ces règles de nettoyage surveillent en continu votre parc d’appareils afin que les enregistrements les concernant restent à jour. Les appareils supprimés de cette façon sont enlevés de la gestion Intune.
1. Connectez-vous à [Intune dans le portail Azure](https://aka.ms/intuneportal).
2. Choisissez **Appareils** > **Règles de nettoyage d’appareil** > **Oui**.
3. Dans la zone **Supprimer les appareils que vous n’avez pas enregistrés depuis ce nombre de jours**, entrez un nombre compris entre 90 et 270.
4. Choisissez **Enregistrer**.



## <a name="delete-devices-from-the-azure-active-directory-portal"></a>Supprimer des appareils du portail Azure Active Directory

Vous devrez peut-être supprimer des appareils d’Azure AD en cas de problèmes de communication ou d’appareils manquants. Vous pouvez utiliser l’action **Supprimer** pour supprimer du portail Azure les enregistrements de l’appareil inaccessibles et peu susceptibles de recommuniquer avec Azure. L’action **Supprimer** ne retire pas un appareil de la gestion.

1.  Connectez-vous à [Azure Active Directory dans le portail Azure](http://aka.ms/accessaad) avec vos informations d’identification d’administrateur. Vous pouvez également vous connecter au [portail Office 365](https://portal.office.com). Dans le menu, sélectionnez **Centres d’administration** > **AD Azure**.
2.  Créez un abonnement Azure si vous n’en avez pas. Vous ne devriez pas avoir besoin de carte de crédit ni d’effectuer un paiement si vous disposez d’un compte payant (sélectionnez le lien d’abonnement **Enregistrer votre abonnement Azure Active Directory gratuit**).
3.  Sélectionnez **Azure Active Directory**, puis votre organisation.
4.  Sélectionnez l’onglet **Utilisateurs** .
5. Sélectionnez l’utilisateur associé à l’appareil que vous souhaitez supprimer.
6.  Sélectionnez **Appareils**.
7.  Supprimez les appareils appropriés. Par exemple, vous pouvez supprimer les appareils qui ne sont plus utilisés ou ceux dont les définitions sont incorrectes.

## <a name="retire-an-apple-dep-device-from-intune"></a>Mettre hors service un appareil Apple DEP à partir d’Intune

Si vous souhaitez supprimer complètement un appareil Apple DEP pour qu’il ne soit plus géré par Intune, effectuez les étapes suivantes :

1. Connectez-vous à [Intune dans le portail Azure](https://aka.ms/intuneportal).
2. Choisissez **Appareils** > **Tous les appareils** > choisissez l’appareil > **Mettre hors service**.
![Capture d’écran : Mettre hors service](./media/devices-wipe/retire.png)
3. Choisissez **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez le jeton > **Appareils** > cochez la case correspondant à l’appareil > **Supprimer** > **Oui**.
![Capture d’écran de suppression de l’appareil](./media/devices-wipe/delete-device.png)
4. Visitez [deploy.apple.com](http://deploy.apple.com) et recherchez l’appareil par son numéro de série.
5. Dans le menu **Assigned to** (Affecté à), choisissez **Unassigned** (Non affecté).

6. Choisissez **Reassign** (Réaffecter).

    ![Capture d’écran de réaffectation Apple](./media/devices-wipe/apple-reassign.png)

## <a name="fresh-start"></a>Nouvelle version

Applicable aux appareils Windows 10. Apprenez-en davantage sur [Nouvelle version](https://docs.microsoft.com/intune/device-fresh-start).

## <a name="next-steps"></a>Étapes suivantes

Si vous souhaitez réinscrire un appareil supprimé, consultez [Options d’inscription](enrollment-options.md).

