---
title: Comment vos utilisateurs Android obtiennent leurs applications
description: Méthodes de mise à disposition des applications Android pour les utilisateurs finaux
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4169f5625965ebc7d2bbbf9153cb4183fcd22b3
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57388079"
---
# <a name="how-your-android-users-get-their-apps"></a>Comment vos utilisateurs Android obtiennent leurs applications

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Utilisez ces informations pour comprendre comment et où vos utilisateurs finaux Android obtiennent les applications que vous distribuez via Microsoft Intune. Les informations peuvent différer selon le type d’appareil (appareils Android natifs ou appareils Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Appareils Android (non-Samsung Knox Standard) natifs

| Type d’application | Applications métier | Applications Play Store  |
| ------------- |-------------| -----|
| Applications disponibles      | Sur le site Portail d’entreprise, les utilisateurs appuient sur **Installer**. Une notification s’affiche, sur laquelle les utilisateurs appuient pour démarrer l’installation. Une fois l’installation effectuée, la notification disparaît. | Sur le site Portail d’entreprise, les utilisateurs appuient sur l’application et accèdent à une page d’application dans le Play Store, où ils peuvent démarrer l’installation.|
| Applications requises      | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification pour démarrer l’installation. Une fois l’installation effectuée, la notification disparaît.    | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification et accèdent à une page d’application dans le Play Store, où ils peuvent démarrer l’installation. Une fois l’installation effectuée, la notification disparaît. |

Vos utilisateurs finaux doivent autoriser l’installation à partir de sources inconnues afin d’installer des [applications métier](lob-apps-android.md). Celles-ci se trouvent généralement dans deux emplacements différents :

* **Android 7.1.2 et versions antérieures** : **Paramètres** > **Sécurité** > **Sources inconnues**
* **Android 8.0 et versions ultérieures** : **Paramètres** > **Applications et notifications** > **Accès spécial à l’application** > **Installer des applications inconnues** > **Portail d’entreprise Intune** > **Autoriser à partir de cette source**

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
