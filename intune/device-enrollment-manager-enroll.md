---
title: Inscrire des appareils avec un compte de gestionnaire d’inscription d’appareil
titleSuffix: Microsoft Intune
description: Utilisez le compte de gestionnaire d’inscription d’appareil pour inscrire des appareils dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8bbb1c7ec7151a09c8eeae33f4252781e5338f7
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048324"
---
# <a name="enroll-devices-in-intune-by-using-a-device-enrollment-manager-account"></a>Inscrire des appareils dans Intune avec un compte de gestionnaire d’inscription d’appareil

Vous pouvez inscrire jusqu’à 1 000 appareils mobiles avec un seul compte Azure Active Directory en utilisant un compte de gestionnaire d’inscription d’appareil (DEM). DEM est une autorisation Intune qui peut être appliquée à un compte d’utilisateur AAD, permettant à l’utilisateur d’inscrire jusqu’à 1 000 appareils. Un compte DEM est utile pour les scénarios où les appareils sont inscrits et préparés avant d’être remis à leurs utilisateurs.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitations des appareils qui sont inscrits avec un compte de gestionnaire d’inscription d’appareil

Les comptes d’utilisateur DEM et les appareils inscrits avec un compte d’utilisateur DEM ont les limitations suivantes :

  - Une licence Intune doit être attribuée à un utilisateur de compte DEM.
  - La réinitialisation ne peut pas être effectuée à partir du Portail d’entreprise. La réinitialisation d’un appareil inscrit par un compte d’utilisateur DEM peut être effectuée à partir d’Intune dans le portail Azure.
  - Seul l’appareil local s’affiche dans l’application Portail d’entreprise ou le site web.
  - Les comptes d’utilisateur DEM ne peuvent pas utiliser les applications du programme d’achat en volume (VPP) Apple avec des licences utilisateur VPP Apple en raison des critères des identifiants Apple par utilisateur pour la gestion des applications.
  - Les appareils peuvent installer des applications VPP s’ils ont des licences d’appareil VPP Apple.
  - Les appareils sont bloqués pour l’accès conditionnel à l’exception de Windows 10 1803+
  - Tout appareil inscrit auprès de comptes DEM doit bénéficier de la licence appropriée pour être géré par Intune. La licence peut être une licence d’utilisateur Intune ou une licence d’appareil Intune.



## <a name="add-a-device-enrollment-manager"></a>Ajouter un gestionnaire d’inscription d’appareil

1.  Dans le [portail Azure d’Intune](https://aka.ms/intuneportal), choisissez **Inscription d’appareil** > **Gestionnaires d’inscription d’appareil**.

2.  Sélectionnez **Ajouter**.

3.  Dans le panneau **Ajouter un utilisateur**, entrez le nom d’utilisateur principal de l’utilisateur DEM, puis sélectionnez **Ajouter**. L’utilisateur DEM est ajouté à la liste des utilisateurs DEM.

## <a name="permissions-for-dem"></a>Autorisations pour DEM

Les rôles Administrateur de services Intune ou Administrateur général Azure AD sont nécessaires pour :
- Attribuer une autorisation DEM à un compte d’utilisateur Azure AD
- Voir tous les utilisateurs DEM

Si un utilisateur n’a pas le rôle Administrateur général ou Administrateur de services Intune, mais qu’il dispose des autorisations en lecture pour le rôle Gestionnaires d’inscription des appareils, il peut voir seulement les utilisateurs DEM qu’il a créés.


## <a name="remove-device-enrollment-manager-permissions"></a>Supprimer des autorisations de gestionnaire d’inscription d’appareil

La suppression d’un gestionnaire d’inscription d’appareil n’affecte pas les appareils inscrits.

**Pour supprimer un gestionnaire d’inscription d’appareil**

1. Dans le [portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils**, puis choisissez **Gestionnaires d’inscription des appareils**.
2. Dans le panneau **Gestionnaires d’inscription d’appareil**, sélectionnez l’utilisateur gestionnaire d’inscription d’appareil, puis sélectionnez **Supprimer**.

