---
title: Configuration de base de Microsoft Intune
description: Cet article décrit les étapes à suivre pour configurer Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08041a57ab52f395283e57cda596d00ba168aba1
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556480"
---
# <a name="basic-setup"></a>Configuration de base

Une fois que vous avez évalué votre environnement, vous devez configurer Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dépendances externes d’un déploiement Intune

### <a name="identity"></a>Identité

Intune requiert l’utilisation d’Azure Active Directory (Azure AD) en tant que fournisseur de groupes d’utilisateurs et d’identités. Informations supplémentaires :

- [Configuration requise pour les identités](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [Configuration requise pour la synchronisation d’annuaires](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [Authentification multifacteur (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [Planification de vos groupes d’utilisateurs et d’appareils](users-add.md)

- [Comment créer des groupes d’utilisateurs et d’appareils](groups-get-started.md)

Si votre organisation utilise déjà Office 365, Intune doit utiliser le même environnement Azure Active Directory.

### <a name="pki-optional"></a>Infrastructure PKI (facultatif)

Si vous comptez utiliser l’authentification basée sur un certificat pour valider des profils VPN, Wi-Fi ou de courrier électronique avec Intune, veillez à mettre en place une [infrastructure PKI](../protect/certificates-configure.md) prise en charge, prête à créer et à déployer des profils de certificat. Pour en savoir plus sur la configuration de certificats dans Intune, consultez les rubriques suivantes :

- [Comment configurer l’infrastructure de certificats pour SCEP](/intune/certificates-scep-configure)

- [Comment configurer l’infrastructure de certificats pour PFX](/intune/certficates-pfx-configure)

## <a name="task-list-for-an-intune-setup"></a>Liste des tâches de configuration de Microsoft Intune

### <a name="task-1-intune-subscription"></a>Tâche 1 : Abonnement Intune

Avant de pouvoir migrer vers Intune, vous avez d’abord besoin d’un [abonnement Intune](account-sign-up.md).

### <a name="task-2-assign-intune-user-licenses"></a>Tâche 2 : Attribuer des licences utilisateur Intune

- Découvrez comment [affecter des licences utilisateur Intune](licenses-assign.md).

- Si vous avez créé un locataire Azure Active Directory, découvrez comment [générer des utilisateurs ou synchroniser un utilisateur à partir de votre instance Active Directory locale.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Tâche 3 : Définir votre autorité MDM sur Intune

Nous vous recommandons de gérer Intune à l’aide du [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Définir votre autorité MDM sur **Intune**. En utilisant une autre autorité MDM, Intune peut transférer la gestion MDM à d’autres consoles de gestion Microsoft. Cependant, ces cas sont rares.

> [!IMPORTANT]
> Si vous transférez la fonction d’administration des appareils mobiles à Intune pour la première fois, vous devez définir l’autorité MDM sur Intune.

Découvrez comment [définir l’autorité de gestion des appareils mobiles](mdm-authority-set.md).

## <a name="next-step"></a>Étape suivante

Configurer des [stratégies de gestion des appareils mobiles et des applications](../migration-guide-configure-policies.md).
