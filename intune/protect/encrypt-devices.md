---
title: Chiffrer des appareils dans Microsoft Intune avec des méthodes de chiffrement prises en charge par les plateformes
titleSuffix: Microsoft Intune
description: Chiffrez des appareils avec des méthodes de chiffrement intégrées, comme BitLocker ou FileVault, et gérez les clés de récupération pour ces appareils chiffrés depuis le portail Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ad995a4b8b67a2ff7e3604f899fdbeebc2bad8cc
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721394"
---
# <a name="use-device-encryption-with-intune"></a>Utiliser le chiffrement d’appareil avec Intune  

Utilisez Intune pour gérer le chiffrement d’un disque ou d’un lecteur intégré d’un appareil pour protéger les données sur vos appareils.  

Configurez le chiffrement de disque dans le cadre d’un profil de configuration d’appareil pour la protection de point de terminaison. Les plateformes et technologies de chiffrement suivantes sont prises en charge par Intune :  
- macOS : FileVault   
- Windows 10 et ultérieur : BitLocker  

Intune fournit également un [rapport de chiffrement](encryption-monitor.md) intégré qui présente des informations détaillées sur l’état de chiffrement des appareils pour l’ensemble de vos appareils gérés.  

## <a name="filevault-encryption-for-macos"></a>Chiffrement FileVault pour macOS  

Utilisez Intune pour configurer le chiffrement de disque FileVault sur les appareils qui exécutent macOS. Ensuite, utilisez le rapport de chiffrement Intune pour voir les détails du chiffrement de ces appareils et pour gérer les clés de récupération des appareils chiffrés avec FileVault.  

FileVault est un programme de chiffrement de disque complet inclus avec macOS. Utilisez Intune pour configurer le FileVault sur les appareils qui exécutent **macOS 10.13 ou ultérieur**.  

Pour configurer FileVault, créez un [profil de configuration d’appareil](../configuration/device-profile-create.md) pour la protection de point de terminaison pour la plateforme macOS. Les paramètres de FileVault sont une des catégories de paramètres disponibles pour la protection de point de terminaison macOS.  

Une fois que vous avez créé une stratégie pour chiffrer des appareils avec FileVault, la stratégie est appliquée aux appareils en deux étapes. D’abord, l’appareil est préparé pour permettre à Intune de récupérer et de sauvegarder la clé de récupération. Ceci est désigné sous le nom de « mise en dépôt ». Une fois la clé mise en dépôt, le chiffrement de disque peut démarrer.

![Paramètres de FileVault](./media/encrypt-devices/filevault-settings.png)

Pour plus d’informations sur le paramètre de FileVault que vous pouvez gérer avec Intune, consultez [FileVault](endpoint-protection-macos.md#filevault) dans l’article sur Intune pour les paramètres de protection de point de terminaison macOS.  

### <a name="how-to-configure-macos-filevault"></a>Comment configurer macOS FileVault 

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), accédez à **Configuration de l’appareil** > **Profils** > **Créer un profil**.  

2. Spécifiez les options suivantes :  

   - Plateforme : macOS  
   - Type de profil : Endpoint Protection  

3. Sélectionnez **Paramètres** > **FileVault**.  

4. Pour *FileVault*, sélectionnez **Activer**.  

5. Pour *Type de clé de récupération*, seul **Clé personnelle** est pris en charge.  

   Envisagez d’ajouter un message pour aider les utilisateurs finaux à récupérer la clé de récupération pour leur appareil. Ces informations peuvent être utiles pour les utilisateurs finaux quand vous utilisez le paramètre Rotation de la clé de récupération personnelle, qui peut générer automatiquement une nouvelle clé de récupération pour un appareil à intervalles réguliers.  

   Par exemple : Pour récupérer une clé de récupération perdue ou ayant récemment fait l’objet d’une rotation, connectez-vous au site web Portail d’entreprise Intune à partir de n’importe quel appareil. Dans le portail, accédez à *Appareils*, sélectionnez l’appareil où FileVault est activé, puis sélectionnez *Obtenir la clé de récupération*. La clé de récupération actuelle est affichée.  

6. Configurez les [paramètres FileVault](endpoint-protection-macos.md#filevault) selon vos besoins métier, puis sélectionnez **OK**.  

   > [!IMPORTANT]  
   > Il existe un problème connu lorsque le paramètre **Désactiver l’invite à la déconnexion** est défini sur *Activer*. Lorsque cette option est définie sur *Activer*, le paramètre **Nombre d’autorisations de contournement** doit être défini sur une valeur, et non sur *Non configuré*. Si la valeur est *Non configuré*, le profil échoue sur l’appareil. Dans ce scénario, l’appareil signale son **résumé de l’état du profil** comme étant une **Erreur**, sans fournir d’informations supplémentaires.
   > 
   > Lorsque l’option **Désactiver l’invite à la déconnexion** a la valeur *Non configuré*, la zone **Nombre d’autorisations de contournement** peut avoir la valeur *Non configuré* ou avoir une valeur.  
   > 
   > Ce problème sera résolu dans une mise à jour ultérieure. 

7. Procédez à la configuration des autres paramètres, puis enregistrez le profil.  

### <a name="manage-filevault"></a>Gérer FileVault  

Une fois qu’Intune a chiffré un appareil macOS avec FileVault, vous pouvez voir et gérer les clés de récupération FileVault quand vous consultez le [rapport de chiffrement](encryption-monitor.md) d’Intune.  

Une fois qu’Intune a chiffré un appareil macOS avec FileVault, vous pouvez afficher la clé de récupération personnelle de l’appareil à partir du portail d’entreprise web sur n’importe quel appareil. Une fois que vous êtes dans le portail d’entreprise web, choisissez l’appareil macOS chiffré, puis sélectionnez « Obtenir la clé de récupération » comme action d’appareil à distance. 

## <a name="bitlocker-encryption-for-windows-10"></a>Chiffrement BitLocker pour Windows 10  

Utilisez Intune pour configurer le chiffrement de lecteur BitLocker sur les appareils qui exécutent Windows 10. Ensuite, utilisez le rapport de chiffrement Intune pour voir les détails du chiffrement de ces appareils. Vous pouvez également accéder à des informations importantes sur BitLocker à partir de vos appareils, telles qu’elles se trouvent dans Azure Active Directory (Azure AD).  

BitLocker est disponible sur les appareils qui exécutent **Windows 10 ou ultérieur**.  

Configurez BitLocker quand vous créez un [profil de configuration d’appareil](../configuration/device-profile-create.md) pour la protection de point de terminaison pour la plateforme Windows 10 ou ultérieur. Les paramètres de BitLocker se trouvent dans la catégorie Paramètres de chiffrement Windows pour la protection de point de terminaison Windows 10.    

![Paramètres de BitLocker](./media/encrypt-devices/bitlocker-settings.png) 

### <a name="how-to-configure-windows-10-bitlocker"></a>Comment configurer Windows 10 BitLocker  

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et accédez à Configuration de l’appareil > Profils > Créer un profil.  

2. Spécifiez les options suivantes :  
   - Plateforme : Windows 10 et versions ultérieures  
   - Type de profil : Endpoint Protection  

3. Sélectionnez **Paramètres** > **Chiffrement Windows**.

4. Configurez les paramètres pour BitLocker selon vos besoins métier, puis sélectionnez **OK**.  

5. Procédez à la configuration des autres paramètres, puis enregistrez le profil.  

### <a name="manage-bitlocker"></a>Gérer BitLocker  

Une fois qu’Intune a chiffré un appareil Windows 10 avec BitLocker, vous pouvez voir et récupérer les clés de récupération BitLocker quand vous consultez le [rapport de chiffrement](encryption-monitor.md) d’Intune.  

## <a name="next-steps"></a>Étapes suivantes  

Créer [une stratégie de conformité des appareils](compliance-policy-create-windows.md)  

Utilisez le rapport de chiffrement pour gérer les éléments suivants :  
- [Clés de récupération BitLocker](encryption-monitor.md#bitlocker-recovery-keys)
- [Clés de récupération FileVault](encryption-monitor.md#filevault-recovery-keys)

Passez en revue les paramètres de chiffrement que vous pouvez configurer avec Intune pour :  
- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)  
- [FileVault](endpoint-protection-macos.md#filevault)  
 
 
