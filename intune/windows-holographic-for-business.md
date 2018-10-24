---
title: Utiliser les appareils Windows Holographic avec Microsoft Intune - Azure | Microsoft Docs
description: Avec Microsoft Intune, vous pouvez gérer et effectuer différentes tâches sur des appareils exécutant Windows Holographic for Business et HoloLens, notamment configurer le Portail d’entreprise, créer une stratégie de conformité, personnaliser les paramètres OMA-URI, déployer des applications, catégoriser les appareils en groupes, créer des profils, imposer des restrictions aux appareils, activer les mises à jour logicielles, définir des conditions générales, configurer les paramètres VPN et Wi-Fi, et utiliser Hello Entreprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81a11ce35cbf0f256f59bf26d317933977750d6e
ms.sourcegitcommit: b33ff64514abdc5e939ff59ea722b3704cd56c78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49065762"
---
# <a name="manage-and-use-windows-holographic-and-hololens-devices-with-intune"></a>Gérer et utiliser les appareils Windows Holographic et HoloLens avec Intune

Microsoft Intune inclut de nombreuses fonctionnalités pour aider à gérer les appareils qui exécutent Windows Holographic for Business, comme [Microsoft HoloLens](https://docs.microsoft.com/hololens/). À l’aide d’Intune, vous pouvez vérifier que les appareils sont conformes aux règles de votre organisation, et vous pouvez personnaliser l’appareil en ajoutant un profil Wi-Fi ou VPN. Une autre fonctionnalité clé consiste à utiliser l’appareil comme une borne et exécuter une application spécifique, ou un ensemble spécifique d’applications.

Les tâches décrites dans cet article vous aident à gérer, personnaliser et sécuriser vos appareils exécutant Windows Holographic for Business, notamment les mises à jour logicielles et l’utilisation de Windows Hello for Business.

Pour utiliser des appareils Windows Holographic avec Intune, créez un profil Mise à niveau d’édition. Ce profil de mise à niveau permet de mettre à niveau les appareils de Windows Holographic vers Windows Holographic for Business. Pour Microsoft HoloLens, vous pouvez acheter Commercial Suite afin d’obtenir la licence nécessaire pour la mise à niveau. Pour plus d’informations, consultez [Mettre à niveau les appareils exécutant Windows Holographique vers Windows Holographic for Business](holographic-upgrade.md).

## <a name="azure-active-directory"></a>Azure Active Directory

Azure Active Directory (AD) est un bonne ressource pour vous aider à gérer et à contrôler vos appareils Windows Holographic for Business. À l’aide d’Intune et d’Azure AD, vous pouvez : 

- **[Configurer des appareils joints à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup)** : dans Azure Active Directory (AD), vous pouvez ajouter vos appareils Windows 10 professionnels, notamment ceux exécutant Windows Holographic for Business. Cette fonctionnalité permet à Azure AD de contrôler l’appareil. Elle permet de vérifier que les utilisateurs accèdent aux ressources de votre entreprise à partir d’appareils qui répondent à vos exigences de sécurité et de conformité.

  La [présentation de la gestion des appareils dans Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction) fournit plus de détails.

- **[Inscription en bloc des appareils Windows](windows-bulk-enroll.md)** : vous pouvez joindre un grand nombre de nouveaux appareils Windows à Azure AD et à Intune. Cette fonctionnalité, appelée « inscription en bloc », utilise des packages de provisionnement. Ces packages joignent les appareils exécutant Windows Holographic for Business à votre locataire Azure AD et les inscrivent auprès d’Intune.

## <a name="company-portal"></a>Portail d'entreprise
**[Configurer l’application Portail d’entreprise](company-portal-app.md)**

Intune comprend l’application Portail d’entreprise, qui permet aux utilisateurs d’accéder aux données de l’entreprise, d’inscrire des appareils, d’installer des applications, de contacter votre service informatique, etc. Vous pouvez personnaliser l’application Portail d’entreprise pour les appareils exécutant Windows Holographic for Business.

Dans l’application Portail d’entreprise, vous pouvez également effectuer l’une des actions suivantes :

- [Supprimer un appareil d’Intune](/intune-user-help/unenroll-your-device-from-intune-windows) à l’aide de l’application Paramètres ou de l’application Portail d’entreprise
- [Renommer un appareil](/intune-user-help/rename-your-device-cpapp)
- [Installer des applications](/intune-user-help/install-apps-cpapp-windows) sur un appareil
- [Synchroniser des appareils manuellement](/intune-user-help/sync-your-device-manually-windows) à partir de l’application Paramètres ou de l’application Portail d’entreprise


## <a name="compliance-policy"></a>Stratégie de conformité
**[Créer une stratégie de conformité des appareils](compliance-policy-create-windows.md)**

Les stratégies de conformité sont des règles et des paramètres que les appareils doivent respecter pour être conformes. Utilisez ces stratégies avec un accès conditionnel pour empêcher les appareils non conformes d’accéder aux ressources de l’entreprise. Dans Intune, créez des stratégies de conformité pour autoriser ou bloquer l’accès des appareils exécutant Windows Holographic for Business. Par exemple, vous pouvez créer une stratégie qui impose l’activation de BitLocker.

Voir aussi **[Bien démarrer avec les stratégies de conformité](device-compliance-get-started.md)**.

## <a name="deploy-and-manage-apps"></a>Déployer et gérer des applications
**[Ajouter des applications à Intune](apps-add.md)**

À l’aide d’Intune, vous pouvez ajouter des applications aux appareils exécutant Windows Holographic for Business. Il existe plusieurs façons de déployer des applications. Par exemple, vous pouvez :

- [Ajouter des applications Microsoft Store](store-apps-windows.md)
- [Ajouter des applications que vous créez](lob-apps-windows.md)
- [Affecter des applications à des groupes](apps-deploy.md)

Microsoft Intune peut déployer des applications Windows universelles sur les appareils Microsoft HoloLens exécutant Windows Holographic for Business. Vous pouvez charger directement vos packages d’application sur le portail Azure Intune, ou les déployer à partir du Microsoft Store pour Entreprises. Pour plus d’informations sur les domaines connexes, consultez les articles suivants :
- Pour déployer des applications métier à l’aide du portail Azure Intune, consultez [Guide pratique pour ajouter des applications métier Windows à Microsoft Intune](lob-apps-windows.md).
- Pour déployer des applications à l’aide du Microsoft Store pour Entreprises, consultez [Guide pratique pour gérer les applications que vous avez achetées dans le Microsoft Store pour Entreprises avec Microsoft Intune](windows-store-for-business.md). 
- Pour en savoir plus sur la gestion des applications avec Microsoft Intune, consultez [Qu’est-ce que la gestion des applications Microsoft Intune ?](app-management.md).
- Pour en savoir plus sur le développement d’applications pour Microsoft HoloLens, consultez [Applications de réalité mixte pour Microsoft HoloLens](https://www.microsoft.com/hololens/apps). 

> [!NOTE]
> Les appareils HoloLens exécutant Windows 10 Holographic for Business 1607 ne prennent pas en charge les applications sous licence en ligne du Microsoft Store pour Entreprises. Pour en savoir plus, consultez [Installer des applications sur HoloLens](https://docs.microsoft.com/en-us/hololens/hololens-install-apps).

## <a name="device-actions"></a>Actions de l’appareil
Intune intègre certaines actions qui permettent aux administrateurs informatiques d’effectuer différentes tâches : soit de manière locale sur l’appareil, soit à distance à l’aide d’Intune dans le portail Azure. Les utilisateurs peuvent également émettre une commande à distance à partir de l’application Portail d’entreprise Intune sur les appareils personnels inscrits dans Intune.

Si vous utilisez des appareils exécutant Windows Holographic for Business, les actions suivantes sont disponibles : 

- **[Réinitialiser](devices-wipe.md#wipe)** : l’action **Réinitialiser** supprime l’appareil d’Intune et restaure les paramètres par défaut de l’appareil. Utilisez cette action avant de donner l’appareil à un nouvel utilisateur, ou si l’appareil a été perdu ou volé.

- **[Mettre hors service](devices-wipe.md#retire)**: l’action **Mettre hors service** supprime l’appareil d’Intune. Elle supprime également les données, les paramètres et les profils de messagerie de l’application managée qui ont été affectés par Intune. Les données personnelles de l’utilisateur restent sur l’appareil.

- **[Synchroniser les appareils pour obtenir les dernières stratégies et actions](device-sync.md)** : l’action **Synchroniser** force l’appareil à s’enregistrer immédiatement auprès d’Intune. Quand un appareil s’enregistre, il reçoit immédiatement les actions ou les stratégies en attente qui sont affectées. Cette fonctionnalité vous aide à valider et à corriger les stratégies que vous avez affectées, sans attendre le prochain enregistrement planifié.

La ressource **[Qu’est-ce que la gestion des appareils Microsoft Intune ?](device-management.md)** est un bon point de départ pour découvrir comment gérer des appareils à l’aide du portail Azure. 

## <a name="device-categories-and-groups"></a>Catégories et groupes d’appareils
**[Catégoriser les appareils en groupes](device-group-mapping.md)**

À l’aide d’Intune, vous pouvez créer des catégories d’appareils pour ajouter automatiquement des appareils à des groupes en fonction des catégories créées, par exemple Ventes, Comptabilité, Ressources humaines, etc. L’idée est de faciliter la gestion de vos appareils exécutant Windows Holographic for Business.

## <a name="device-configuration-profiles"></a>Profils de configuration d’appareil 
**[Bien démarrer avec les profils de configuration](device-profiles.md) et [créer votre propre profil](device-profile-create.md)**

Intune inclut des paramètres et des fonctionnalités que vous pouvez activer ou désactiver sur différents appareils de votre organisation. Ces paramètres et fonctionnalités sont gérés à l’aide de profils. Par exemple, vous pouvez créer un profil qui active Cortana ou Windows Defender SmartScreen sur vos appareils exécutant Windows Holographic for Business.

Dans vos profils, vous pouvez utiliser OMA-URI pour personnaliser certains paramètres, imposer des restrictions aux appareils et configurer un réseau VPN (réseau privé virtuel) ou Wi-Fi.

#### <a name="custom-device-settingscustom-settings-windows-holographicmd"></a>[Paramètres d’appareil personnalisés](custom-settings-windows-holographic.md)

Pour configurer les paramètres OMA-URI (Open Mobile Alliance Uniform Resource Identifier), vous pouvez créer un profil personnalisé dans Intune. Utilisez les paramètres OMA-URI pour contrôler différentes fonctionnalités sur vos appareils Windows Holographic for Business, par exemple l’activation d’un VPN ou la recherche de mises à jour sur Microsoft Update.

#### <a name="configure-kiosk-modekiosk-settingsmdwindows-holographic-for-business"></a>[Configurer le mode kiosque](kiosk-settings.md#windows-holographic-for-business)

Avec les fonctionnalités de PC partagé ou invité qui sont disponibles dans Intune, vous pouvez configurer les appareils Windows Holographic for Business pour qu’ils s’exécutent en mode kiosque. Ces appareils peuvent exécuter une seule application (mode kiosque mono-application) ou plusieurs applications (mode kiosque multi-application).

#### <a name="device-restrictionsdevice-restrictions-windows-holographicmd"></a>[Restrictions relatives aux appareils](device-restrictions-windows-holographic.md)

Les restrictions imposées aux appareils vous permettent de contrôler différents paramètres et fonctionnalités sur vos appareils, notamment la saisie d’un mot de passe obligatoire, l’installation d’applications à partir du [Microsoft Store](https://www.microsoft.com/store/apps/windows?icid=CNavAppsWindowsApps), l’activation de Bluetooth, etc. Vous créez ces restrictions dans un profil Intune. Vous pouvez appliquer ce profil à plusieurs appareils exécutant Windows Holographic for Business.

#### <a name="configure-vpnvpn-settings-configuremd"></a>[Configurer un VPN](vpn-settings-configure.md)

Les réseaux privés virtuels (ou VPN) donnent à vos utilisateurs un accès distant sécurisé à votre réseau d’entreprise. Dans Intune, vous pouvez créer un profil VPN comprenant des paramètres spécifiques pour vos appareils Windows Holographic for Business. Par exemple, vous pouvez créer un profil VPN pour que tous les appareils Windows Holographic for Business utilisent une connexion de type VPN Citrix.

#### <a name="configure-wi-fiwi-fi-settings-configuremd"></a>[Configurer le Wi-Fi](wi-fi-settings-configure.md)

Vous pouvez également créer un profil Wi-Fi dans Intune pour affecter des paramètres de réseau sans fil à vos appareils Windows Holographic for Business. Quand vous affectez un profil Wi-Fi, vos utilisateurs finaux bénéficient d’un accès au réseau d’entreprise, sans aucune configuration réseau. Par exemple, vous pouvez créer un réseau Wi-Fi dédié uniquement aux appareils Windows Holographic for Business.

## <a name="software-updates"></a>Mises à jour logicielles
**[Gérer les mises à jour logicielles](windows-update-for-business-configure.md)**

Intune inclut une fonctionnalité appelée anneaux de mise à jour pour les appareils Windows 10. Ces anneaux de mise à jour comportent un groupe de paramètres qui déterminent l’installation des mises à jour. Par exemple, vous pouvez créer une fenêtre de maintenance pour installer les mises à jour, ou choisir de redémarrer l’appareil après l’installation des mises à jour. Vous pouvez appliquer un anneau de mise à jour à plusieurs appareils exécutant Windows Holographic for Business.

## <a name="terms-and-conditions"></a>Conditions générales
**[Définir les conditions générales de votre entreprise pour l’accès utilisateur](terms-and-conditions-create.md)**

Pour que les utilisateurs puissent inscrire des appareils et accéder aux applications de votre entreprise, notamment les e-mails, vous pouvez leur demander d’accepter d’abord les conditions générales de l’entreprise. Dans Intune, définissez la manière dont les conditions générales s’affichent dans le Portail d’entreprise, et affectez également ces conditions générales aux appareils exécutant Windows Holographic for Business.

## <a name="windows-hello-for-business"></a>Windows Hello Entreprise
**[Utiliser Windows Hello Entreprise](windows-hello.md)**

Hello Entreprise est une méthode de connexion alternative qui utilise un compte Azure Active Directory à la place d’un mot de passe, d’une carte à puce ou d’une carte à puce virtuelle. Avec Hello Entreprise, vos appareils Windows Holographic for Business peuvent se connecter à l’aide d’un code PIN de longueur minimale défini par vos soins.
