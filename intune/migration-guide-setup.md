---
title: Configuration de base de Microsoft Intune
description: Cet article décrit les étapes à suivre pour configurer Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 4cec5c593fd4191a9d73e77b13fd38df81a7fe8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179743"
---
# <a name="basic-setup"></a>Configuration de base

Une fois que vous avez évalué votre environnement, vous devez configurer Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dépendances externes d’un déploiement Intune

### <a name="identity"></a>Fournisseur

Intune requiert l’utilisation d’Azure Active Directory (Azure AD) en tant que fournisseur de groupes d’utilisateurs et d’identités. Informations supplémentaires :

-  [Configuration requise pour les identités](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

-   [Configuration requise pour la synchronisation d’annuaires](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

-   [Configuration requise pour l’authentification multifacteur (MFA)](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

-   [Planification de vos groupes d’utilisateurs et d’appareils](users-add.md)

-   [Comment créer des groupes d’utilisateurs et d’appareils](groups-get-started.md)

Si votre organisation utilise déjà Office 365, Intune doit utiliser le même environnement Azure Active Directory.

### <a name="pki-optional"></a>Infrastructure PKI (facultatif)

Si vous comptez utiliser l’authentification basée sur un certificat pour valider des profils VPN, Wi-Fi ou de courrier électronique avec Intune, veillez à mettre en place une [infrastructure PKI](certificates-configure.md) prise en charge, prête à créer et à déployer des profils de certificat. Pour en savoir plus sur la configuration de certificats dans Intune, consultez les rubriques suivantes :

-   [Comment configurer l’infrastructure de certificats pour SCEP](/intune/certificates-scep-configure)

-   [Comment configurer l’infrastructure de certificats pour PFX](/intune/certficates-pfx-configure)


## <a name="task-list-for-an-intune-setup"></a>Liste des tâches de configuration de Microsoft Intune

### <a name="task-1-intune-subscription"></a>Tâche 1 : Abonnement Intune

Avant de pouvoir migrer vers Intune, vous devez créer un abonnement Intune.

-   Vous pouvez consulter [cette page](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0), qui fournit des instructions sur les opérations suivantes :

    -   Création d’un abonnement Intune lié à un nouveau locataire AAD

    -   Liaison de l’abonnement Intune via la connexion à un locataire AAD existant

### <a name="task-2-assign-intune-user-licenses"></a>Tâche 2 : Affecter des licences utilisateur Intune

-   Découvrez comment [affecter des licences utilisateur Intune](licenses-assign.md).

-   Si vous avez créé un locataire Azure Active Directory, découvrez comment [générer des utilisateurs ou synchroniser un utilisateur à partir de votre instance Active Directory locale.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Tâche 3 : Définir votre autorité MDM sur Intune

Vous pouvez gérer Intune via le portail Azure ou la console Configuration Manager Current Branch. Nous vous recommandons de gérer Intune via le [portail Azure](https://portal.azure.com), sauf si vous avez besoin d’intégrer Intune dans un déploiement Configuration Manager Current Branch.

Définissez l’autorité MDM sur **Intune** pour activer le portail Intune Azure. En utilisant une autre autorité MDM, Intune peut transférer la gestion MDM à d’autres consoles de gestion Microsoft. Cependant, ces cas sont rares.

> [!IMPORTANT]
> Si vous transférez la fonction d’administration des appareils mobiles à Intune pour la première fois, vous devez définir l’autorité MDM sur Intune.

Découvrez comment [définir l’autorité de gestion des appareils mobiles](mdm-authority-set.md).

## <a name="next-step"></a>Étape suivante

Configurer des [stratégies de gestion des appareils mobiles et des applications](migration-guide-configure-policies.md).
