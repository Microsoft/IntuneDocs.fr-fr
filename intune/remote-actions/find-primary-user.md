---
title: Rechercher l’utilisateur principal d’un appareil Microsoft Intune.
titleSuffix: ''
description: Rechercher l’utilisateur principal (ou l’affinité entre utilisateur et appareil) d’un appareil Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6f594e20abf1a507d1d4e00641a4821fe1ba9b0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509329"
---
# <a name="find-the-primary-user-of-an-intune-device"></a>Rechercher l’utilisateur principal d’un appareil Intune

L’utilisateur principal, également appelé affinité entre utilisateur et périphérique, est une propriété de chaque appareil Intune. Un appareil Intune peut avoir zéro ou un utilisateur principal qui lui est assigné. Lorsqu’aucun utilisateur principal n’est attribué, l’appareil est appelé « appareil partagé ».

## <a name="how-to-find-a-devices-primary-user"></a>Comment trouver l’utilisateur principal d’un appareil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Choisissez **appareils** > choisir un appareil.
3. À la page **Vue d’ensemble**, choisissez **Afficher plus** et vous verrez l’utilisateur principal indiqué.

## <a name="what-is-the-primary-user"></a>Qu’est-ce que l’utilisateur principal ?
La propriété d’utilisateur principal est utilisée pour mapper un utilisateur Intune sous licence à ses appareils dans :
- l'application Portail d’entreprise
- le site web de l’utilisateur final
- les expériences des professionnels de l’informatique, telles que les pages de résolution des problèmes dans le portail Azure. Ces pages mappent les comptes d’utilisateurs à des appareils à l’aide de l’utilisateur principal.    

### <a name="company-portal-app"></a>Application Portail d’entreprise
L’application Portail d’entreprise s’attend à ce que le compte d’utilisateur connecté au portail d’entreprise soit l’utilisateur principal de cet appareil. Si un autre utilisateur a été attribué en tant qu’utilisateur principal, le portail d’entreprise affiche un avertissement :

« Cet appareil est déjà attribué à quelqu’un dans votre organisation. Contactez le support de l’entreprise pour devenir l’utilisateur principal de l’appareil. Vous pouvez continuer à utiliser le Portail d’entreprise, mais les fonctionnalités seront limitées ».

Si aucun utilisateur principal n’est attribué à un appareil Intune, l’application portail d’entreprise le détecte comme un appareil partagé. Les appareils partagés sont visuellement identifiables avec une étiquette « partagé » qui apparaît sur la vignette de l’appareil. Dans ce mode, le portail d’entreprise peut toujours être utilisé pour demander et installer des applications disponibles. Toutefois, les actions en libre-service (réinitialiser/renommer/mettre hors service) ne sont pas disponibles.  

Pour apparaître dans le portail d’entreprise sur les appareils partagés, les applications disponibles doivent être attribuées à un groupe d’utilisateurs. Elles sont installées dans le contexte du système ou le contexte de l’utilisateur, en fonction de la façon dont l’application a été configurée par l’administrateur informatique. Pour plus d’informations sur le contexte de l’application, consultez [Installation d’applications sur les appareils Windows 10](../apps/apps-windows-10-app-deploy.md). La version 10.3.4651.0 de portail d’entreprise ou une version ultérieure est requise pour utiliser cette fonctionnalité.


## <a name="who-is-assigned-as-the-primary-user"></a>Qui est affecté en tant qu’utilisateur principal ?
Intune ajoute automatiquement un utilisateur principal aux appareils pendant ou juste après l’inscription. La méthode d’inscription détermine le moment où l’utilisateur principal est ajouté à un appareil.

| Plate-forme | Méthode d’inscription | Utilisateur principal affecté | Un utilisateur principal est affecté |
| ---- | ---- | ---- | ---- |
| Windows | Ajouter professionnel ou scolaire (par utilisateur) | Inscription de l’utilisateur | Pendant l’inscription |   
| Windows | Connexion modernes à l’application (par utilisateur) | Inscription de l’utilisateur | Pendant l’inscription | 
| Windows | Inscrire dans la gestion des appareils mobiles (par utilisateur) | Inscription de l’utilisateur | Pendant l’inscription | 
| Windows | Jonction Azure AD (prête à l’emploi) | Inscription de l’utilisateur | Pendant l’inscription | 
| Windows | Jonction Azure AD (Autopilot prêt à l’emploi) | Inscription de l’utilisateur | Pendant l’inscription | 
| Windows | Inscrire dans la gestion des appareils mobiles uniquement | Inscription de l’utilisateur | Pendant l’inscription | 
| Windows | AADJ hybride + GPO à inscription automatique | Premier utilisateur à se connecter à Windows | Quand le premier utilisateur se connecte à Windows| 
| Windows | Cogestion | Premier utilisateur à se connecter à Windows | Quand le premier utilisateur se connecte à Windows | 
| Windows | Jonction Azure AD (jeton d’inscription en bloc) | Aucune | Non applicable | 
| Windows | Jonction Azure AD (mode de déploiement automatique Autopilot) | Aucune | Non applicable | 
| Multiplateforme | Inscription par utilisateur avec l’application portail d’entreprise | Inscription de l’utilisateur | Pendant l’inscription |
| Multiplateforme | Gestionnaire d’inscription d’appareil (DEM) | Inscription d’utilisateur DEM | Pendant l’inscription |
| iOS, macOS | Inscription d’appareils automatisée Apple (DEP avec affinité utilisateur) | Inscription de l’utilisateur | Pendant l’inscription |
| iOS, macOS | Inscription d’appareils automatisée Apple (DEP sans affinité utilisateur) | Aucune | Non applicable |
| Android | Appareils Android d’entreprise dédiés | Aucune | Non applicable |

## <a name="primary-user-and-azure-ad-device-owner"></a>Utilisateur principal et propriétaire d’appareil Azure AD
Dans certains cas, l’utilisateur principal Intune peut être différent de la propriété **Propriétaire** de l’appareil Azure AD (visible sous **Appareils** > **Appareils Azure AD**). Le propriétaire de l’appareil Azure AD est ajouté lors de l’inscription d’un appareil dans Azure Active Directory.

## <a name="next-steps"></a>Étapes suivantes
[Gérer vos appareils Intune.](device-management.md)
