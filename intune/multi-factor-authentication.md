---
title: Exiger l’authentification multifacteur pour l’inscription d’appareils dans Intune
titleSuffix: Microsoft Intune
description: Découvrez comment exiger l’authentification multifacteur dans Azure AD pour l’inscription d’appareils dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 94280c73-c05c-4e72-b0dd-a7cb997782f9
ROBOTS: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf5611b3b9292222582d66cae39b4f751279dcec
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568789"
---
# <a name="require-multi-factor-authentication-for-intune-device-enrollments"></a>Exiger l’authentification multifacteur pour l’inscription d’appareils dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune peut utiliser l’authentification multifacteur (MFA) Azure Active Directory (AD) pour l’inscription d’appareils afin de sécuriser vos ressources d’entreprise.

Elle nécessite au moins deux des méthodes de vérification suivantes :

- Quelque chose que vous connaissez (généralement un mot de passe ou code PIN).
- Quelque chose que vous possédez (un appareil de confiance difficilement copiable, comme un téléphone).
- Quelque chose qui vous représente (biométrie, comme une empreinte digitale).

L’authentification multifacteur est prise en charge sur les appareils iOS, Android, Windows 8.1 ou ultérieur, Windows Phone 8.1 ou Windows 10 Mobile ou ultérieur.

Quand vous activez MFA, les utilisateurs finaux doivent fournir deux formes d’informations d’identification pour inscrire un appareil.

## <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>Configurer Intune pour exiger une authentification multifacteur lors de l’inscription des appareils

Pour exiger l’authentification multifacteur à l’inscription d’un appareil, procédez comme suit :

>[!Important]
>Vous devez avoir un abonnement Azure Active Directory Premium P1 ou supérieur affecté à vos utilisateurs pour implémenter cette stratégie.

>[!Important]
>Ne configurez pas les **règles d’accès basées sur les appareils** pour l’inscription à Microsoft Intune.

1. Connectez-vous à votre [portail Microsoft Azure](https://portal.azure.com) avec vos informations d’identification.
2. Dans le portail, accédez à **Intune** et choisissez **Accès conditionnel**. Le nœud d’accès conditionnel accessible à partir d’*Intune* est le même nœud que celui accessible à partir d’*Azure AD*.
4. Choisissez **Nouvelle stratégie**.
5. Dans **Nouvelle** stratégie, tapez un nom descriptif pour la stratégie.
6. Dans la section **Affectations**, choisissez **Utilisateurs et groupes**. 
7. Dans **Utilisateurs et groupes**, choisissez **Sélectionner les utilisateurs ou les groupes** et cochez **Utilisateurs et groupes**. Sélectionnez ensuite les utilisateurs et/ou les groupes auxquels attribuer cette stratégie, puis choisissez **Terminé**.
8. Dans la section **Affectations**, choisissez **Applications cloud**.
9. Sous l’onglet **Inclure** des **Applications cloud**, choisissez **Sélectionner les applications**, puis **Sélectionner** > **Inscription à Microsoft Intune**, puis choisissez **OK**.
10. Dans la section **Affectations**, pour **Conditions**, vous n’avez pas besoin de configurer des paramètres MFA.
11. Dans la section **Contrôles d’accès**, choisissez **Accorder**.
12. Dans **Accorder**, choisissez **Accorder l’accès**, puis sélectionnez **Exiger l’authentification multifacteur**. Ne sélectionnez pas **Exiger que l’appareil soit marqué comme conforme**, car la conformité d’un appareil ne peut pas être évaluée tant que celui-ci n’est pas inscrit. Choisissez ensuite **Sélectionner**.
13. Dans **Nouvelle stratégie**, choisissez **Activer la stratégie** > **Activée**, puis choisissez **Créer**.



## <a name="next-steps"></a>Étapes suivantes

Quand les utilisateurs finaux inscrivent leur appareil, ils doivent maintenant s’authentifier avec une deuxième forme d’identification, comme un code PIN, un téléphone ou des données biométriques.
