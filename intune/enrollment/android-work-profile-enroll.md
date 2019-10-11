---
title: Inscrire des appareils avec profil professionnel Android Entreprise dans Intune
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils avec profil professionnel Android Entreprise dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c447b6b21021573d95a5ece3297e548f216b7a0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723526"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Configurer l’inscription des appareils avec profil professionnel Android Entreprise

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune vous permet de déployer des applications et des paramètres sur des appareils avec profil professionnel Android Entreprise de manière à ce que les informations professionnelles soient séparées des informations personnelles. Pour plus d’informations sur Android Entreprise, consultez [Exigences Android Entreprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Pour configurer la gestion des profils professionnels Android Entreprise, effectuez les étapes suivantes :

1. [Connectez votre compte de locataire Intune à votre compte Android Entreprise](connect-intune-android-enterprise.md).
2. Spécifiez les paramètres d’inscription de profil professionnel Android Entreprise. Les profils professionnels Android Entreprise sont [pris en charge uniquement sur certains appareils Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Tout appareil qui prend en charge les profils professionnels Android Entreprise prend également en charge la gestion administrateur d’appareil Android. Intune vous permet de spécifier la façon dont les appareils qui prennent en charge les profils professionnels Android Entreprise doivent être gérés dans [Restrictions d’inscription](enrollment-restrictions-set.md).
    - **Bloquer** :  Tous les appareils Android, notamment les appareils qui prennent en charge les profils professionnels Android Entreprise, seront inscrits en tant qu’appareils d’administrateur d’appareil Android, sauf si l’inscription de l’administrateur d’appareil Android est également bloquée. 
    - **Autoriser (défini par défaut)** : Tous les appareils qui prennent en charge les profils professionnels Android Entreprise sont inscrits comme des appareils avec profil professionnel Android Entreprise. Tous les appareils Android qui ne prennent pas en charge les profils professionnels Android Entreprise, seront inscrits en tant qu’appareils d’administrateur d’appareil Android, sauf si l’inscription de l’administrateur d’appareil Android est bloquée. 
> [!NOTE]
> La valeur par défaut attribuée à **Autoriser** est True pour les nouveaux locataires à partir de juillet 2019. Tous les locataires précédents ne subiront aucune modification de leurs restrictions d’inscription et verront toutes les stratégies qu’ils ont définies dans Restrictions d’inscription. Pour les locataires précédents qui n’ont subi aucune modification des Restrictions d’inscription, le paramètre **Bloquer** sera toujours la valeur par défaut pour les profils professionnels Android Entreprise.

3. [Indiquez à vos utilisateurs comment inscrire leurs appareils](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  

Si vous voulez inscrire des appareils avec des profils professionnels Android Entreprise, mais que ces appareils étaient auparavant inscrits avec l’administrateur d’appareil Android, vous devez d’abord les désinscrire, puis les réinscrire.
> [!NOTE]
> En tant qu’administrateur, vous pouvez effectuer cette opération à distance à l’aide de la fonction **Mettre hors service**. Cette fonction se trouve dans le menu Actions une fois l’appareil sélectionné dans le panneau **Tous appareils**.

Si vous inscrivez des appareils avec profils professionnels Android Entreprise à l’aide d’un compte de [Gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md), il existe une limite de 10 appareils pouvant être inscrits par compte.

Pour plus d’informations, consultez [Données envoyées par Intune à Google](../protect/data-intune-sends-to-google.md).

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Étapes suivantes pour les profils professionnels Android Entreprise
- [Déplacer des applications avec profil professionnel Android Entreprise](../apps/apps-add-android-for-work.md)
- [Ajouter des stratégies de configuration de profil professionnel Android Entreprise](../configuration/device-profiles.md)

## <a name="see-also"></a>Voir aussi

[Configuration et dépannage des appareils Android Entreprise dans Microsoft Intune](https://support.microsoft.com/help/4476974)
