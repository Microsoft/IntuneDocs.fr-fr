---
title: Inscrire des appareils Android dans Intune
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff005ddded4178801e7e334f604280ef4408aaff
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505666"
---
# <a name="enroll-android-devices"></a>Inscrire des appareils Android

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez enregistrer des appareils Android comme suit :
- Android Enterprise (offre un ensemble d’options d’inscription qui fournissent aux utilisateurs les fonctionnalités les plus à jour et sécurisées) :
    - [**Profil professionnel Android Enterprise**](android-work-profile-enroll.md) : Pour les appareils personnels autorisés à accéder aux données d’entreprise. Les administrateurs peuvent gérer les applications, données et comptes professionnels. Les données personnelles sur l’appareil sont séparées des données professionnelles. Les administrateurs n’ont aucun contrôle sur les paramètres et données à caractère personnel. 
    - [**Android Enterprise dédié**](android-kiosk-enroll.md) : Pour les appareils à usage unique appartenant à l’entreprise, utilisés notamment pour la signalisation numérique, l’impression de billets ou la gestion des stocks. Les administrateurs verrouillent l’utilisation d’un appareil pour un ensemble limité d’applications et de liens web. Les utilisateurs ne peuvent pas non plus ajouter d’autres applications ou effectuer d’autres actions sur l’appareil.
    - [**Android Enterprise complètement managé**](android-fully-managed-enroll.md) : Pour les appareils mono-utilisateur appartenant à l’entreprise utilisés exclusivement à des fins professionnelles. Les administrateurs peuvent gérer entièrement l’appareil et appliquer des contrôles de stratégie non disponibles dans les profils professionnels. 
- [**Administrateur des appareils Android**](android-enroll-device-administrator.md), notamment des appareils Samsung Knox Standard et [Zebra](../configuration/android-zebra-mx-overview.md). 

## <a name="prerequisites"></a>Prérequis

Pour préparer la gestion des appareils mobiles, vous devez définir l’autorité de gestion des appareils mobiles (MDM) sur **Microsoft Intune**. Consultez la page [Configurer l’autorité MDM](../fundamentals/mdm-authority-set.md) pour obtenir des instructions. Cet élément ne se définit qu’une seule fois, quand vous configurez pour la première fois Intune pour la gestion des appareils mobiles.

Pour les appareils fabriqués par Zebra Technologies, vous devrez peut-être accorder des permissions supplémentaires au portail d'entreprise en fonction des capacités de l'appareil spécifique. Consultez [Mobility Extensions sur les appareils Zebra](../configuration/android-zebra-mx-overview.md) pour plus de détails.

D’[autres conditions préalables](android-samsung-knox-mobile-enroll.md) s’appliquent aux appareils Samsung Knox Standard.

## <a name="next-steps"></a>Étapes suivantes

- [Configurer les inscriptions de profil professionnel Android Entreprise](android-work-profile-enroll.md)
- [Configurer les inscriptions d’appareil dédié Android Entreprise](android-kiosk-enroll.md)
- [Configurer les inscriptions d’appareil complètement géré Android Entreprise](android-fully-managed-enroll.md)
- [Configurer l’inscription de l’administrateur d’appareil Android](android-enroll-device-administrator.md)

