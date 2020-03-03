---
title: Chiffrer les appareils avec la méthode de chiffrement prise en charge par les plateformes
titleSuffix: Microsoft Intune
description: Chiffrez des appareils avec des méthodes de chiffrement intégrées, comme BitLocker ou FileVault, et gérez les clés de récupération pour ces appareils chiffrés depuis le portail Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: annovich
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a5c844377dcd69b6caf5ef9f72fcb8dbb4ef8bd0
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609304"
---
# <a name="use-device-encryption-with-intune"></a>Utiliser le chiffrement d’appareil avec Intune

Utilisez Intune pour gérer le chiffrement d’un disque ou d’un lecteur intégré d’un appareil pour protéger les données sur vos appareils.

Configurez le chiffrement de disque dans le cadre d’un profil de configuration d’appareil pour la protection de point de terminaison. Les plateformes et technologies de chiffrement suivantes sont prises en charge par Intune :

- macOS : FileVault
- Windows 10 et ultérieur : BitLocker

Intune fournit également un [rapport de chiffrement](encryption-monitor.md) intégré qui présente des informations détaillées sur l’état de chiffrement des appareils pour l’ensemble de vos appareils gérés.

## <a name="filevault-encryption-for-macos"></a>Chiffrement FileVault pour macOS

Utilisez Intune pour configurer le chiffrement de disque FileVault sur les appareils qui exécutent macOS. Ensuite, utilisez le rapport de chiffrement Intune pour voir les détails du chiffrement de ces appareils et pour gérer les clés de récupération des appareils chiffrés avec FileVault.

L’inscription d’appareils approuvés par l’utilisateur est nécessaire pour que FileVault fonctionne sur l’appareil. L’utilisateur doit approuver manuellement le profil de gestion à partir des préférences système pour que l’inscription soit considérée comme approuvée par l’utilisateur.

FileVault est un programme de chiffrement de disque complet inclus avec macOS. Utilisez Intune pour configurer le FileVault sur les appareils qui exécutent **macOS 10.13 ou ultérieur**.

Pour configurer FileVault, créez un [profil de configuration d’appareil](../configuration/device-profile-create.md) pour la protection de point de terminaison pour la plateforme macOS. Les paramètres de FileVault sont une des catégories de paramètres disponibles pour la protection de point de terminaison macOS.

Une fois que vous avez créé une stratégie pour chiffrer des appareils avec FileVault, la stratégie est appliquée aux appareils en deux étapes. D’abord, l’appareil est préparé pour permettre à Intune de récupérer et de sauvegarder la clé de récupération. Cette action est désignée sous le nom de « mise en dépôt ». Une fois la clé mise en dépôt, le chiffrement de disque peut démarrer.

![Paramètres de FileVault](./media/encrypt-devices/filevault-settings.png)

Pour plus d’informations sur le paramètre de FileVault que vous pouvez gérer avec Intune, consultez [FileVault](endpoint-protection-macos.md#filevault) dans l’article sur Intune pour les paramètres de protection de point de terminaison macOS.

### <a name="permissions-to-manage-filevault"></a>Autorisations pour gérer FileVault

Pour gérer FileVault dans Intune, votre compte doit disposer des autorisations de [contrôle d’accès en fonction du rôle (RBAC)](../fundamentals/role-based-access-control.md) Intune applicables.

Vous trouverez ci-dessous les autorisations FileVault, qui font partie de la catégorie **Tâches à distance**, ainsi que les rôles RBAC intégrés qui accordent l’autorisation :
 
- **Obtenir la clé FileVault** :
  - Opérateur du support technique
  - Gestionnaire de sécurité des points de terminaison

- **Permuter la clé FileVault**
  - Opérateur du support technique

### <a name="how-to-configure-macos-filevault"></a>Comment configurer macOS FileVault

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Spécifiez les options suivantes :

   - Plateforme : macOS
   - Type de profil : Endpoint Protection

4. Sélectionnez **Paramètres** > **FileVault**.

5. Pour *FileVault*, sélectionnez **Activer**.

6. Pour *Type de clé de récupération*, seul **Clé personnelle** est pris en charge.

   Envisagez d’ajouter un message pour aider les utilisateurs finaux à récupérer la clé de récupération pour leur appareil. Ces informations peuvent être utiles pour les utilisateurs finaux quand vous utilisez le paramètre Rotation de la clé de récupération personnelle, qui peut générer automatiquement une nouvelle clé de récupération pour un appareil à intervalles réguliers.

   Par exemple : Pour récupérer une clé de récupération perdue ou ayant récemment fait l’objet d’une rotation, connectez-vous au site web Portail d’entreprise Intune à partir de n’importe quel appareil. Dans le portail, accédez à *Appareils*, sélectionnez l’appareil où FileVault est activé, puis sélectionnez *Obtenir la clé de récupération*. La clé de récupération actuelle est affichée.

7. Configurez les [paramètres FileVault](endpoint-protection-macos.md#filevault) selon vos besoins métier, puis sélectionnez **OK**.

  8. Procédez à la configuration des autres paramètres, puis enregistrez le profil.  

### <a name="manage-filevault"></a>Gérer FileVault

Une fois qu’Intune a chiffré un appareil macOS avec FileVault, vous pouvez voir et gérer les clés de récupération FileVault quand vous consultez le [rapport de chiffrement](encryption-monitor.md) d’Intune.

Une fois qu’Intune a chiffré un appareil macOS avec FileVault, vous pouvez afficher la clé de récupération personnelle de l’appareil à partir du portail d’entreprise web sur n’importe quel appareil. Une fois que vous êtes dans le portail d’entreprise web, choisissez l’appareil macOS chiffré, puis sélectionnez « Obtenir la clé de récupération » comme action d’appareil à distance.

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices"></a>Récupérer une clé de récupération personnelle à partir d’appareils macOS chiffrés par MEM

Les utilisateurs finaux récupèrent leur clé de récupération personnelle (clé FileVault) à l’aide de l’application Portail d’entreprise iOS. L’appareil qui a la clé de récupération personnelle doit être inscrit auprès d’Intune et chiffré avec FileVault via Intune. À l’aide de l’application Portail d’entreprise iOS, l’utilisateur final peut ouvrir une page Web qui comprend la clé de récupération personnelle FileVault. Vous pouvez également récupérer la clé de récupération d’Intune en sélectionnant **Appareils** > *l’appareil macOS chiffré et inscrit* > **Obtenir une clé de récupération**. 

## <a name="bitlocker-encryption-for-windows-10"></a>Chiffrement BitLocker pour Windows 10

Utilisez Intune pour configurer le chiffrement de lecteur BitLocker sur les appareils qui exécutent Windows 10. Ensuite, utilisez le rapport de chiffrement Intune pour voir les détails du chiffrement de ces appareils. Vous pouvez également accéder à des informations importantes sur BitLocker à partir de vos appareils, telles qu’elles se trouvent dans Azure Active Directory (Azure AD).

BitLocker est disponible sur les appareils qui exécutent **Windows 10 ou ultérieur**.

Configurez BitLocker quand vous créez un [profil de configuration d’appareil](../configuration/device-profile-create.md) pour la protection de point de terminaison pour la plateforme Windows 10 ou ultérieur. Les paramètres de BitLocker se trouvent dans la catégorie Paramètres de chiffrement Windows pour la protection de point de terminaison Windows 10.

![Paramètres de BitLocker](./media/encrypt-devices/bitlocker-settings.png)

### <a name="how-to-configure-windows-10-bitlocker"></a>Comment configurer Windows 10 BitLocker

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Spécifiez les options suivantes :

   - Plateforme : Windows 10 et versions ultérieures
   - Type de profil : Endpoint Protection

4. Sélectionnez **Paramètres** > **Chiffrement Windows**.

5. Configurez les paramètres pour BitLocker selon vos besoins métier, puis sélectionnez **OK**.

6. Procédez à la configuration des autres paramètres, puis enregistrez le profil.

### <a name="manage-bitlocker"></a>Gérer BitLocker

Une fois qu’Intune a chiffré un appareil Windows 10 avec BitLocker, vous pouvez voir et récupérer les clés de récupération BitLocker quand vous consultez le [rapport de chiffrement](encryption-monitor.md) d’Intune.

### <a name="rotate-bitlocker-recovery-keys"></a>Rotation des clés de récupération BitLocker

Vous pouvez utiliser une action d’appareil Intune pour faire pivoter à distance la clé de récupération BitLocker d’un appareil qui exécute Windows 10 version 1909 ou une version ultérieure.

#### <a name="prerequisites"></a>Prérequis

Les appareils doivent remplir les conditions préalables suivantes pour prendre en charge la rotation de clés de récupération BitLocker :

- Les appareils doivent exécuter Windows 10, version 1909 ou ultérieure

- Les appareils joints à Azure AD et hybrides doivent prendre en charge l’activation de la rotation des clés :

  - **Rotation du mot de passe de récupération déclenchée par le client**

  Ce paramètre se trouve sous *Chiffrement Windows* dans le cadre d’une stratégie de configuration d’appareil pour Windows 10 Endpoint Protection.
  
#### <a name="to-rotate-the-bitlocker-recovery-key"></a>Faire pivoter la clé de récupération BitLocker

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Tous les appareils**.

3. Dans la liste des appareils que vous gérez, sélectionnez un appareil, sélectionnez **Plus**, puis l’action à distance **Rotation de clés BitLocker**.

## <a name="next-steps"></a>Étapes suivantes

Créez [une stratégie de conformité des appareils](compliance-policy-create-windows.md).

Utilisez le rapport de chiffrement pour gérer les éléments suivants :

- [Clés de récupération BitLocker](encryption-monitor.md#bitlocker-recovery-keys)
- [Clés de récupération FileVault](encryption-monitor.md#filevault-recovery-keys)

Passez en revue les paramètres de chiffrement que vous pouvez configurer avec Intune pour :

- [BitLocker](endpoint-protection-windows-10.md#windows-encryption)
- [FileVault](endpoint-protection-macos.md#filevault)
