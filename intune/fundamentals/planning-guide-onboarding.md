---
title: Processus d’intégration Intune
titleSuffix: Microsoft Intune
description: Cet article fournit tous les détails à prendre en compte quand vous intégrez une solution cloud uniquement Microsoft Intune dans votre environnement.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 82cd13a2d60e589c5e9a7fcbccff8841a9a8aca2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727296"
---
# <a name="implement-your-microsoft-intune-plan"></a>Implémenter votre plan Microsoft Intune

Pendant la phase d’intégration, vous déployez Intune dans votre environnement de production. Le processus d’implémentation consiste à paramétrer et configurer Intune et les dépendances externes (si nécessaire) en fonction des [exigences de vos cas d’utilisation](planning-guide-requirements.md).

La section suivante fournit une vue d’ensemble du processus d'implémentation Intune qui englobe des éléments requis et des tâches générales.

## <a name="intune-requirements"></a>Éléments requis Intune

Les principaux éléments requis autonomes pour Intune sont les suivants :

- Abonnement Enterprise Mobility + Security (EMS)/Intune

- Abonnement Office 365 (pour les applications Office et les applications gérées par la stratégie de protection des applications)

- Certificat d'APN Apple (pour permettre la gestion de la plate-forme d'appareils iOS)

- Azure AD Connect (pour la synchronisation d'annuaires)

- Connecteur local Microsoft Intune pour Exchange (pour l’accès conditionnel sur site à Exchange, si nécessaire)

- Intune Certificate Connector (pour le déploiement du certificat SCEP, si nécessaire)

>[!TIP]
> Pour obtenir la liste complète des appareils que vous pouvez gérer avec Intune, consultez la liste [Appareils pris en charge](supported-devices-browsers.md).

## <a name="intune-implementation-process"></a>Processus d'implémentation d'Intune

Nous avons identifié 13 tâches discrètes à effectuer pour implémenter un déploiement Intune. Selon vos besoins professionnels, votre infrastructure existante et votre stratégie de gestion d’appareils, certaines de ces tâches ont peut-être été déjà effectuées. D’autres peuvent ne pas être adaptées à votre plan.

### <a name="task-1-get-an-intune-subscription"></a>Tâche 1 : Se procurer un abonnement Intune

Comme nous l’avons vu dans la section précédente sur les éléments requis Intune, vous avez besoin d’un abonnement EMS ou Intune. Si votre organisation n’en a pas, contactez Microsoft ou votre équipe des comptes Microsoft pour lui signifier votre souhait d’acheter Enterprise Mobility + Security (EMS) ou Intune.

- En savoir plus sur [comment acheter Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing).

### <a name="task-2-add-office-365-subscription"></a>Tâche 2 : Ajouter un abonnement Office 365

Cette étape est facultative. Si vous envisagez d’utiliser Exchange Online et de gérer les applications mobiles Office avec des stratégies de protection des applications, vous avez besoin d’un abonnement Office 365. Si votre organisation ne dispose pas d’un abonnement Office 365, contactez Microsoft ou votre équipe des comptes Microsoft pour lui signifier votre souhait d’acheter Office 365.

- En savoir plus sur [comment acheter Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

### <a name="task-3-add-users-groups-in-azure-ad"></a>Tâche 3 : Ajouter des groupes d’utilisateurs dans Azure AD

Vous serez peut-être amené à ajouter des utilisateurs ou des groupes de sécurité dans Active Directory ou Azure Active Directory selon les scénarios de cas d’utilisation et les exigences de votre déploiement Intune. Passez en revue vos utilisateurs et groupes de sécurité actuels dans Active Directory ou Azure Active Directory et déterminez s’ils répondent entièrement à vos besoins. Si vous devez ajouter de nouveaux utilisateurs et groupes de sécurité, nous vous recommandons de le faire dans Active Directory et de procéder à une synchronisation avec Azure Active Directory via Azure AD Connect.

- En savoir plus sur [comment ajouter des utilisateurs/groupes dans Intune](users-add.md).
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect--->


### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Tâche 4 : Attribuer des licences utilisateur Intune et Office 365

Vous devez attribuer une licence à tous les utilisateurs que vous ciblez pour le déploiement EMS/Intune et Office 365. Vous pouvez attribuer les licences EMS/Intune et Office 365 dans le centre d’administration Microsoft 365.

- En savoir plus sur [comment attribuer des licences Intune](licenses-assign.md).

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Tâche 5 : Définir Intune comme autorité de gestion des appareils mobiles

Avant de commencer l’installation, la configuration, la gestion et l’inscription des appareils avec Intune, vous devez définir Intune comme autorité de gestion des appareils.

- En savoir plus sur la [définition de l’autorité de gestion des appareils](mdm-authority-set.md).

### <a name="task-6-enable-device-platforms"></a>Tâche 6 : Activer les plateformes d’appareils mobiles

Par défaut, la plupart des plateformes d’appareils sont activées, à l’exception des appareils Apple (iOS et Mac). Avant de pouvoir inscrire et gérer les appareils iOS dans Intune, la plateforme d'appareils doit être activée. Pour ce faire, vous devez créer un certificat Push MDM et l’ajouter à Intune.

- En savoir plus sur l’[activation des appareils Apple pour l’inscription](../enrollment/apple-mdm-push-certificate-get.md).

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Tâche 7 : Ajouter et déployer des stratégies de conditions générales

Intune prend en charge les stratégies de conditions générales. Ajoutez les stratégies de conditions générales adéquates et déployez-les sur des groupes ciblés en fonction des cas d’utilisation et exigences de votre déploiement Intune.

- En savoir plus sur l'[ajout et le déploiement des stratégies de conditions générales](../enrollment/terms-and-conditions-create.md).

### <a name="task-8-add-and-deploy-configuration-policies"></a>Tâche 8 : Ajouter et déployer des stratégies de configuration

Intune prend en charge deux types de stratégie de configuration : générale et personnalisée. Ajoutez les stratégies de configuration adéquates et déployez-les sur des groupes ciblés en fonction des cas d’utilisation et exigences de votre déploiement Intune.

- En savoir plus sur l'[ajout et le déploiement des stratégies de configuration](../configuration/device-profiles.md).

### <a name="task-9-add-and-deploy-resource-profiles"></a>Tâche 9 : Ajouter et déployer des profils de ressources

Intune prend en charge les profils de messagerie, Wi-Fi et VPN. Ajoutez ces profils selon les besoins et déployez-les sur des groupes ciblés en fonction des cas d’utilisation et exigences de votre déploiement Intune.

- En savoir plus sur l’[activation de l’accès aux ressources d’entreprise avec Intune](../configuration/device-profiles.md).

### <a name="task-10-add-and-deploy-apps"></a>Tâche 10 : Ajouter et déployer des applications

Intune prend en charge le déploiement d’applications web, métier et de Store public. Vous pouvez aussi gérer les applications qui intègrent le kit SDK Intune en les associant à des stratégies de protection des applications. Ajoutez les applications adéquates et déployez-les sur des groupes ciblés en fonction des cas d’utilisation et exigences de votre déploiement Intune.

- En savoir plus sur l’[ajout et le déploiement d’applications](../apps/app-management.md).

### <a name="task-11-add-and-deploy-compliance-policies"></a>Tâche 11 : Ajouter et déployer des stratégies de conformité

Intune prend en charge les stratégies de conformité. Ajoutez les stratégies de conformité adéquates et déployez-les sur des groupes ciblés en fonction des cas d’utilisation et exigences de votre déploiement Intune.

- En savoir plus sur les [stratégies de conformité](../protect/device-compliance-get-started.md).

### <a name="task-12-enable-conditional-access-policies"></a>Tâche 12 : Activer des stratégies d’accès conditionnel

Intune prend en charge l’accès conditionnel pour Exchange Online, Exchange sur site, SharePoint Online, Skype Entreprise Online et Dynamics CRM Online. Activez et configurez l’accès conditionnel comme il se doit en fonction des cas d’utilisation et exigences de votre déploiement Intune.

- En savoir plus sur l'[accès conditionnel](../protect/conditional-access.md).

### <a name="task-13-enroll-devices"></a>Tâche 13 : Inscrire des appareils

Intune prend en charge les plateformes d’appareils iOS, Mac OS, Android, Windows Desktop et Windows Mobile. Inscrivez les plateformes d’appareils mobiles adéquates en fonction des cas d’utilisation et exigences de votre déploiement Intune.

- En savoir plus sur [comment inscrire des appareils](../enrollment/device-enrollment.md).


## <a name="next-steps"></a>Étapes suivantes
Consultez les conseils en matière de [test et de validation des déploiements Intune](planning-guide-test-validation.md).
