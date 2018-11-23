---
title: Inscrire des appareils avec un compte de gestionnaire d’inscription d’appareil
titlesuffix: Microsoft Intune
description: Utilisez le compte de gestionnaire d’inscription d’appareil pour inscrire des appareils dans Intune. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7ff5a63b6afb619fbbe762d23208c1058e99943
ms.sourcegitcommit: b96568a77d3cb6f602e7577446996fe7dde169bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51610139"
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>Inscrire des appareils avec un compte de gestionnaire d’inscription d’appareil

Vous pouvez inscrire jusqu’à 1 000 appareils mobiles avec un seul compte Azure Active Directory en utilisant un compte de gestionnaire d’inscription d’appareil (DEM). DEM est une autorisation Intune qui peut être appliquée à un compte d’utilisateur AAD, permettant à l’utilisateur d’inscrire jusqu’à 1 000 appareils. Un compte DEM est utile pour les scénarios où les appareils sont inscrits et préparés avant d’être remis à leurs utilisateurs.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitations des appareils qui sont inscrits avec un compte de gestionnaire d’inscription d’appareil

Les comptes d’utilisateur DEM et les appareils inscrits avec un compte d’utilisateur DEM ont les limitations suivantes :

  - La réinitialisation ne peut pas être effectuée à partir du Portail d’entreprise. La réinitialisation d’un appareil inscrit par un compte d’utilisateur DEM peut être effectuée à partir d’Intune dans le portail Azure.
  - Seul l’appareil local s’affiche dans l’application Portail d’entreprise ou le site web.
  - Les comptes d’utilisateur DEM ne peuvent pas utiliser les applications du programme d’achat en volume (VPP) Apple avec des licences utilisateur VPP Apple en raison des critères des identifiants Apple par utilisateur pour la gestion des applications.
  - Les appareils peuvent installer des applications VPP s’ils ont des licences d’appareil VPP Apple.
  - Les appareils sont bloqués pour l’accès conditionnel à l’exception de Windows 10 1803+


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

