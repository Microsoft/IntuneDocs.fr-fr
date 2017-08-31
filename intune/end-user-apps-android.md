---
title: Comment vos utilisateurs Android obtiennent leurs applications
description: "Méthodes de mise à disposition des applications Android pour les utilisateurs finaux"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: fac1ce49584af299face679270dcc43decc4d2f5
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2017
---
# <a name="how-your-android-users-get-their-apps"></a>Comment vos utilisateurs Android obtiennent leurs applications

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Utilisez ces informations pour comprendre comment et où vos utilisateurs finaux Android obtiennent les applications que vous distribuez via Microsoft Intune. Les informations peuvent différer selon le type d’appareil (appareils Android natifs ou appareils Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Appareils Android (non-Samsung Knox Standard) natifs

| Type d’application | Applications métier | Applications Play Store  |
| ------------- |-------------| -----|
| Applications disponibles      | Sur le site Portail d’entreprise, les utilisateurs appuient sur **Installer**. Une notification s’affiche, sur laquelle les utilisateurs appuient pour démarrer l’installation. Une fois l’installation effectuée, la notification disparaît. | Sur le site Portail d’entreprise, les utilisateurs appuient sur l’application et accèdent à une page d’application dans le Play Store, où ils peuvent démarrer l’installation.|
| Applications requises      | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification pour démarrer l’installation. Une fois l’installation effectuée, la notification disparaît.    | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification et accèdent à une page d’application dans le Play Store, où ils peuvent démarrer l’installation. Une fois l’installation effectuée, la notification disparaît. |

Vos utilisateurs finaux doivent autoriser l’installation à partir de sources inconnues afin d’installer des [applications métier](lob-apps-android.md). Celles-ci se trouvent généralement dans deux emplacements différents :

* **Android 7.1.2 et versions inférieures** : **Paramètres** > **Sécurité** > **Sources inconnues**
* **Android 8.0 et versions supérieures** : **Paramètres** > **Applications et notifications** > **Accès spécial à l’application** > **Installer des applications inconnues** > **Portail d’entreprise** > **Autoriser à partir de cette source**

Si cela se produit, l’application Portail d’entreprise avertit l’utilisateur final et le guide directement vers le paramètre approprié. 


## <a name="samsung-knox-standard-android-devices"></a>Appareils Android Samsung Knox Standard

| Type d’application | Applications métier | Applications Play Store  |
| ------------- |-------------| -----|
| Applications disponibles      | Sur le site Portail d’entreprise, les utilisateurs appuient sur **Installer**. L’application est installée sans autre intervention de l’utilisateur. | Sur le site Portail d’entreprise, les utilisateurs appuient sur l’application et accèdent à une page d’application dans le Play Store, où ils peuvent démarrer l’installation.|
| Applications requises      | L’application est installée sans intervention de l’utilisateur.    | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification et accèdent à une page d’application dans le Play Store, où ils peuvent démarrer l’installation. Une fois l’installation effectuée, la notification disparaît. |

Les applications peuvent être gérées ou non gérées, comme décrit ci-dessous. Le processus de fabrication d’applications gérées est le même pour tous les types d’appareil Android.

**Applications gérées** - Il s’agit d’applications gérables par l’intermédiaire de stratégies. Elles ont été « enveloppées » par Intune ou intégrées au SDK d’application Intune. Ces applications peuvent être gérées par Intune et faire l'objet de stratégies d'application.

**Applications non gérées** - Il s’agit d’applications qui ne sont pas gérables par l’intermédiaire de stratégies. Elles n’ont pas été « enveloppées » par Intune ou ne sont pas intégrées au SDK d’application Intune. Vous ne pouvez pas appliquer de stratégies d'application à ces applications.

### <a name="see-also"></a>Voir aussi
[Ajouter des applications avec Microsoft Intune](apps-add.md)

[Comment vos utilisateurs iOS obtiennent leurs applications](end-user-apps-ios.md)

[Comment vos utilisateurs Windows obtiennent leurs applications](end-user-apps-windows.md)
