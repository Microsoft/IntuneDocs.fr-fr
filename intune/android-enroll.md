---
title: Inscrire des appareils Android dans Intune
titlesuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Android dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 3d86afec4e501533ab0048e866969a5bf73c2c57
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2019
ms.locfileid: "54387042"
---
# <a name="enroll-android-devices"></a>Inscrire des appareils Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez gérer les appareils Android suivants :
- Appareils Android, notamment les appareils Samsung Knox Standard.
- Appareils Android Entreprise, notamment :
    - **Appareils avec profil professionnel Android** : appareils personnels autorisés à accéder aux données d’entreprise. Les administrateurs peuvent gérer les applications, données et comptes professionnels. Les données personnelles sur l’appareil sont séparées des données professionnelles. Les administrateurs n’ont aucun contrôle sur les paramètres et données à caractère personnel. 
    - **Appareils Android dédiés** : appareils à usage unique appartenant à l’entreprise, utilisés notamment pour la signalisation numérique, l’impression de billets ou la gestion des stocks. Les administrateurs verrouillent l’utilisation d’un appareil pour un ensemble limité d’applications et de liens web. Les utilisateurs ne peuvent pas non plus ajouter d’autres applications ou effectuer d’autres actions sur l’appareil.
    - **Appareils Android entièrement gérés** : appareils mono-utilisateur appartenant à l’entreprise utilisés exclusivement à des fins professionnelles. Les administrateurs peuvent gérer entièrement l’appareil et appliquer des contrôles de stratégie non disponibles dans les profils professionnels. 

## <a name="prerequisite"></a>Prérequis

Pour préparer la gestion des appareils mobiles, vous devez définir l’autorité de gestion des appareils mobiles (MDM) sur **Microsoft Intune**. Consultez la page [Configurer l’autorité MDM](mdm-authority-set.md) pour obtenir des instructions. Cet élément ne se définit qu’une seule fois, quand vous configurez pour la première fois Intune pour la gestion des appareils mobiles.

## <a name="set-up-android-enrollment"></a>Configurer l’inscription Android

Par défaut, Intune autorise l’inscription des appareils Android et Samsung Knox Standard. Après avoir rempli les prérequis, les administrateurs doivent simplement [indiquer à leurs utilisateurs comment inscrire leurs appareils](/intune-user-help/enroll-your-device-in-intune-android).

Une fois qu’un utilisateur est inscrit, vous pouvez commencer à gérer ses appareils dans Intune, notamment [affecter des stratégies de conformité](compliance-policy-create-android.md), [gérer les applications](app-management.md), etc.

Pour plus d’informations sur les autres tâches de l’utilisateur, consultez les articles suivants :

- [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](end-user-educate.md)
- [Utilisation de votre appareil Android avec Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Pour empêcher l’inscription des appareils Android, ou uniquement des appareils personnels Android, consultez [Définir des restrictions de type d’appareil](enrollment-restrictions-set.md).

## <a name="set-up-android-enterprise-enrollment"></a>Configurer l’inscription d’Android Entreprise

Android Entreprise est un ensemble de fonctionnalités et de services pour les appareils Android, qui séparent les applications et les données personnelles d’un profil professionnel contenant des applications et des données professionnelles. Les appareils Android Entreprise incluent les appareils avec profil professionnel, les appareils entièrement gérés et les appareils dédiés. 

- [Configurer les inscriptions d’appareils avec profil professionnel Android](android-work-profile-enroll.md)
- [Configurer les inscriptions d’appareils dédiés Android](android-kiosk-enroll.md)
- [Configurer les inscriptions d’appareils Android entièrement gérés](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Expérience utilisateur final au moment de l’inscription d’un appareil Samsung Knox

Les appareils Samsung Knox Standard sont pris en charge pour la gestion multi-utilisateur par Intune. Cela signifie que les utilisateurs finaux peuvent se connecter et se déconnecter d’un appareil avec leurs informations d’identification Azure AD. L’appareil est géré de manière centralisée, qu’il soit en cours d’utilisation ou non. Quand les utilisateurs se connectent, ils ont accès aux applications et les éventuelles stratégies sont appliquées à ces applications. Quand les utilisateurs se déconnectent, toutes les données d’application sont effacées.

Les points suivants doivent être pris en compte au moment de l’inscription d’appareil Samsung Knox :
-   Même si aucune stratégie ne demande de code PIN, l’appareil doit avoir au moins un code PIN à quatre chiffres pour s’inscrire. Si l’appareil ne dispose pas d’un code PIN, l’utilisateur est invité à en créer un.
-   Il n’existe aucune interaction utilisateur pour les certificats Workplace Join (WPJ).
-   L’utilisateur est invité à indiquer les informations d’inscription au service et ce que l’application peut faire.
-   L’utilisateur est invité à indiquer les informations d’inscription Knox et ce que Knox peut faire.
-   Si une stratégie de chiffrement est appliquée, les utilisateurs doivent définir un mot de passe complexe à six caractères pour le code secret de l’appareil.
-   Il n’y a aucune invite utilisateur supplémentaire pour installer des certificats émis par un service pour l’accès aux ressources d’entreprise.
- Certains anciens appareils Knox invitent l’utilisateur à fournir des certificats supplémentaires utilisés pour l’accès aux ressources d’entreprise.
- Si un appareil Samsung Mini ne parvient pas à installer WPJ et affiche l’erreur **Certificate Not Found** (Certificat introuvable) ou **Unable to Register Device** (Impossible d’inscrire l’appareil), installez les dernières mises à jour du microprogramme Samsung.

## <a name="next-steps"></a>Étapes suivantes

- [Configurer les inscriptions d’appareils avec profil professionnel Android](android-work-profile-enroll.md)
- [Configurer les inscriptions d’appareils dédiés Android](android-kiosk-enroll.md)
- [Configurer les inscriptions d’appareils Android entièrement gérés](android-fully-managed-enroll.md)
