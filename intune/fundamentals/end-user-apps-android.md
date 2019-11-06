---
title: Comment vos utilisateurs Android obtiennent leurs applications
description: Méthodes de mise à disposition des applications Android pour les utilisateurs finaux
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40e8dd8409f70a70934684c56ed9e9729f4ebf0f
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414598"
---
# <a name="how-your-android-users-get-their-apps"></a>Comment vos utilisateurs Android obtiennent leurs applications

Cet article vous aide à comprendre comment et où vos utilisateurs finaux Android obtiennent les applications que vous distribuez via Microsoft Intune. Les informations peuvent différer selon le type d’appareil (appareils Android natifs ou appareils Samsung Knox Standard).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Appareils Android (non-Samsung Knox Standard) natifs

| Type d’application | Applications métier | Applications Play Store  |
| ------------- |-------------| -----|
| Applications disponibles      | Sur le site Portail d’entreprise, les utilisateurs appuient sur **Installer**. Une notification s’affiche, sur laquelle les utilisateurs appuient pour démarrer l’installation. Une fois l’installation effectuée, la notification disparaît. | Sur le site Portail d’entreprise, les utilisateurs appuient sur l’application et accèdent à une page d’application dans le Play Store. C’est ici qu’ils démarrent l’installation.|
| Applications requises      | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification pour démarrer l’installation. Une fois l’installation effectuée, la notification disparaît.    | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification et accèdent à une page d’application dans le Play Store. C’est ici qu’ils démarrent l’installation. Une fois l’installation effectuée, la notification disparaît. |

Vos utilisateurs finaux doivent autoriser l’installation à partir de sources inconnues pour installer des [applications métier](../apps/lob-apps-android.md). Ce paramètre se trouve généralement à deux emplacements différents :

* **Android 7.1.2 et versions antérieures** : **Paramètres** > **Sécurité** > **Sources inconnues**
* **Android 8.0 et versions ultérieures** : **Paramètres** > **Applications et notifications** > **Accès spécial à l’application** > **Installer des applications inconnues** > **Portail d’entreprise Intune** > **Autoriser à partir de cette source**

Si cela se produit, l’application Portail d’entreprise avertit l’utilisateur final et le guide directement vers le paramètre approprié. 

## <a name="samsung-knox-standard-android-devices"></a>Appareils Android Samsung Knox Standard

| Type d’application | Applications métier | Applications Play Store  |
| ------------- |-------------| -----|
| Applications disponibles      | Sur le site Portail d’entreprise, les utilisateurs appuient sur **Installer**. L’application est installée sans autre intervention de l’utilisateur. | Sur le site Portail d’entreprise, les utilisateurs appuient sur l’application et accèdent à une page d’application dans le Play Store. C’est ici qu’ils démarrent l’installation.|
| Applications requises      | L’application est installée sans intervention de l’utilisateur.    | Les utilisateurs reçoivent une notification qu’ils ne peuvent pas masquer et qui leur indique qu’ils doivent installer une application. Les utilisateurs appuient sur la notification et accèdent à une page d’application dans le Play Store. C’est ici qu’ils démarrent l’installation. Une fois l’installation effectuée, la notification disparaît. |

Les applications peuvent être gérées ou non gérées, comme décrit ci-dessous. Le processus de fabrication d’applications gérées est le même pour tous les types d’appareil Android.

**Applications gérées** : ces applications sont gérées par l’intermédiaire de stratégies. Elles ont été incluses dans un wrapper par Intune ou intégrées au kit de développement logiciel (SDK) de l’application Intune. Ces applications peuvent être gérées par Intune et faire l'objet de stratégies d'application.

**Applications non gérées** : ces applications ne sont pas gérées par l’intermédiaire de stratégies. Elles n’ont pas été incluses dans un wrapper par Intune, ou elles n’incorporent pas le kit de développement logiciel (SDK) Intune. Vous ne pouvez pas appliquer de stratégies d'application à ces applications.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Appareils Zebra avec extensions de mobilité Zebra

Intune utilise la boîte à outils d’extensions de mobilité (MX) Zebra pour installer des applications en mode silencieux sur des appareils Zebra gérés par l’administrateur de l’appareil. Cette fonctionnalité vous permet de déployer et de mettre à jour des applications sur des appareils Zebra sans intervention de l’utilisateur. Si la version MX sur votre appareil est 4.2 ou une version antérieure, les applications ne sont pas installées en mode silencieux. Pour plus d’informations, consultez [Matrice de fonctionnalités MX complète](http://techdocs.zebra.com/mx/compatibility/) sur le site web de Zebra.

Les applications métier déployées sur des appareils Zebra doivent être installées sur l’appareil à partir d’un emplacement public. Le package d’application .apk peut être accessible à d’autres applications et services qui ont également accès au stockage public sur l’appareil. En règle générale, cet accès est une petite fenêtre entre la fin du téléchargement de l’application et le début de l’installation. Cette fenêtre peut permettre une attaque de synchronisation. Par exemple, un package .apk peut être modifié pendant cette fenêtre. Intune minimise le temps que le package .apk passe dans le stockage public et n’autorise pas l’installation d’applications non signées. Pour réduire le risque de sécurité, vérifiez que les fichiers .apk que vous téléchargez ne contiennent pas d’informations sensibles.

## <a name="see-also"></a>Voir aussi

[Ajouter des applications avec Microsoft Intune](../apps/apps-add.md)

[Comment vos utilisateurs iOS obtiennent leurs applications](end-user-apps-ios.md)

[Comment vos utilisateurs Windows obtiennent leurs applications](end-user-apps-windows.md)
