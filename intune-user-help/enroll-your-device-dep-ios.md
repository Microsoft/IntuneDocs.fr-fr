---
title: Inscrivez l’appareil iOS fourni par votre organisation dans la gestion. | Microsoft Docs
description: Explique comment inscrire dans Intune un appareil iOS qui a été acheté et fourni par votre organisation.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f4e7d87e-56d1-43e4-8e88-2f62cf0999e2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: japoehlm
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e5ce83d20958f3ba4c818e49b0c226e07851d03
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506224"
---
# <a name="enroll-your-organization-provided-ios-device-in-management"></a>Inscrire l’appareil iOS fourni par votre organisation dans la gestion

Découvrez comment passer votre appareil iOS en mode géré dans Intune.  

Les appareils iOS qui vous sont fournis par votre entreprise ou votre établissement scolaire sont souvent préconfigurés quand vous les recevez. Votre organisation envoie ces paramètres préconfigurés à votre appareil la première fois que vous l’activez et que vous vous connectez. Une fois la configuration de votre appareil terminée, vous recevez l’accès aux ressources de votre entreprise ou de votre établissement scolaire.  

Pour commencer la configuration, mettez votre appareil sous tension, puis connectez-vous avec vos informations d’identification professionnelles ou scolaires. Le reste de cet article décrit les étapes à suivre et les écrans qui s’affichent quand vous parcourez l’Assistant Configuration.

## <a name="what-is-apple-dep"></a>Qu’est-ce qu’Apple DEP ?

Il se peut que votre organisation ait acheté ses appareils par le biais du *Programme d’inscription des appareils Apple (DEP, Device Enrollment Program)* . Le programme DEP Apple permet aux organisations d’acheter de grandes quantités d’appareils iOS ou macOS. Elles peuvent ensuite configurer et gérer ces appareils dans leur fournisseur de gestion des appareils mobiles préféré, comme Intune. Si vous êtes administrateur et que vous souhaitez obtenir des informations supplémentaires sur le programme DEP Apple, consultez [Inscrire automatiquement des appareils iOS avec le Programme d’inscription des appareils d’Apple](/intune/enrollment/device-enrollment-program-enroll-ios).

## <a name="set-up-your-ios-device"></a>Configurer votre appareil iOS

Si vous utilisez votre propre appareil iOS, plutôt qu’un appareil d’entreprise, suivez les étapes relatives aux [appareils personnels et BYOD](enroll-your-device-in-intune-ios.md).  

1. Allumez votre appareil iOS.
2. Après avoir sélectionné votre langue (**Language**), connectez votre appareil en Wi-Fi.
3. Dans l’écran **Configurer l’appareil iOS**, indiquez ce que vous voulez faire :
   - **Configurer en tant que nouvel appareil**
   - **Restaurer à partir d’une sauvegarde iCloud**
   - **Restaurer à partir d’une sauvegarde iTunes**

4. Une fois que vous êtes connecté en Wi-Fi, l’écran **Configuration** s’affiche. Vous pouvez y lire que **[Votre entreprise] configurera automatiquement votre appareil.**

   **La configuration permet à [Votre entreprise] de gérer cet appareil à distance. Un administrateur peut vous aider à configurer des comptes e-mail et réseau, à installer et configurer des applications, et à gérer les paramètres à distance. Un administrateur peut désactiver des fonctionnalités, installer et supprimer des applications, surveiller et limiter le trafic Internet, et effacer à distance cet appareil.**

   **La configuration est fournie par : [Adresse] de l’équipe iOS de [Votre entreprise]**

5. Connectez-vous avec votre ID Apple. La connexion vous permet d’installer l’application Portail d’entreprise et le profil de gestion permettant à votre entreprise d’accéder à ses ressources, comme les e-mails et les applications.
6. Acceptez les conditions générale (**Terms and Conditions**) et indiquez si vous souhaitez envoyer des informations de diagnostic à Apple.
7. Une fois l’inscription terminée, votre appareil peut vous demander d’effectuer d’autres actions. Certaines de ces étapes peuvent nécessiter l’entrée de votre mot de passe pour accéder aux e-mails ou la configuration d’un code secret.

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
