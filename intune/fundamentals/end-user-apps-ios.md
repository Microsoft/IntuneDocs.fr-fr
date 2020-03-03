---
title: Comment vos utilisateurs iOS/iPadOS obtiennent leurs applications
description: Méthodes de mise à disposition des applications iOS/iPadOS pour les utilisateurs finaux
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344c2e3f3ed53852aa6b749c9ebf6d451dd313ff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514385"
---
# <a name="how-your-iosipados-users-get-their-apps"></a>Comment vos utilisateurs iOS/iPadOS obtiennent leurs applications

Utilisez ces informations pour comprendre comment et où vos utilisateurs finaux obtiennent les applications que vous distribuez via Microsoft Intune.

**Applications requises** : applications requises par l’administrateur qui sont installées sur l’appareil avec une intervention minime de l’utilisateur, qui varie selon la plateforme.

**Applications disponibles** : applications fournies dans la liste de l’application Portail d’entreprise et qu’un utilisateur peut choisir d’installer.

**Applications gérées** : applications pouvant être gérées avec des stratégies et qui ont été « enveloppées » par Intune, ou qui ont été créées à l’aide du kit SDK d’application Intune. Ces applications peuvent être gérées par Intune et faire l’objet de stratégies de protection des applications.

**Applications non gérées** : applications que les utilisateurs peuvent télécharger depuis l’App Store iOS/iPadOS et qui ne sont pas intégrées au SDK Intune. Intune n’a aucun contrôle sur la distribution, la gestion ou la réinitialisation sélective de ces applications.  

Les restrictions d’Apple n’autorisent pas l’affichage des applications métier et gérées de l’App Store dans l’application Portail d’entreprise. Pour contourner ce problème, les vignettes dans l’application Portail d’entreprise pour iOS/iPadOS dirigent les utilisateurs vers différentes vues à un même emplacement (le site web Portail d’entreprise) pour toutes leurs applications.

Les utilisateurs inscrits obtiennent leurs applications en appuyant sur les vignettes suivantes dans l’écran Applications de l’application Portail d’entreprise :

- **Toutes les applications** pointe vers une liste de toutes les applications sous l’onglet TOUT du [site web Portail d’entreprise](https://portal.manage.microsoft.com).

- **Applications proposées** pointe vers l’onglet SÉLECTION du site web Portail d’entreprise.

- **Catégories** pointe vers l’onglet CATÉGORIES du site web Portail d’entreprise.

![Écran des applications du Portail d’entreprise iOS](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

Pour savoir plus en détail comment ajouter des applications, consultez la page [Guide pratique pour ajouter une application à Microsoft Intune](../apps/apps-add.md).

## <a name="see-also"></a>Voir aussi

[Comment vos utilisateurs Android obtiennent leurs applications](end-user-apps-android.md)

[Comment vos utilisateurs Windows obtiennent leurs applications](end-user-apps-windows.md)
