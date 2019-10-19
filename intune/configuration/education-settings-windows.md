---
title: Paramètres Windows 10 Éducation dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres Éducation pour les appareils Windows 10. Utilisez ces paramètres dans un profil de configuration d’appareil avec l’application Take a Test, choisissez comment les utilisateurs ou les étudiants se connectent, surveillez l’écran pendant le test et plus encore dans Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d89f512c06dcfbf6f6ddaba5e17ac9ca6f0becf
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506806"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configurer l’application Take a Test sur les appareils Windows 10 à l’aide d’Intune

L’application Take a test vous permet d’administrer en toute sécurité les tests en ligne sur les appareils Windows 10 de votre classe. Pour configurer l’application Take a test, vous devez créer un profil de configuration d’appareil dans Intune et configurer les paramètres d’évaluation sécurisée. Cet article décrit les paramètres que vous trouverez pour l’application Take a test. 

Une fois que vous avez configuré le profil, attribuez-le et déployez-le pour vos élèves. 

[L’application Take a Test dans Intune](education-settings-configure.md) fournit plus d’informations sur cette fonctionnalité.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Paramètres Take a Test
Après avoir créé un profil de configuration d’appareil, accédez à **type de profil** , puis sélectionnez **évaluation sécurisée (éducation)** . Les paramètres de l’application de test sont les suivants : 


- **Type de compte** : choisissez la façon dont les utilisateurs se connectent au test. Les options disponibles sont les suivantes :
  - Compte Azure AD
  - Compte de domaine
  - Compte local
  - Compte invité local : disponible uniquement sur les appareils exécutant Windows 10, version 1903 et versions ultérieures.    
- **Nom d’utilisateur du compte** : entrez le nom d’utilisateur du compte utilisé avec l’application Take a Test. Vous pouvez entrer des comptes au format suivant :
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Nom du compte**: pour configurer un type de compte invité local, entrez le nom du compte utilisé avec l’application Take a test. Le nom du compte apparaît sous la forme d’une vignette sur l’écran de connexion. Les élèves cliquent sur la vignette pour lancer le test.  
- **URL de l’évaluation** : entrez l’URL du test que les utilisateurs doivent effectuer. Pour plus d’informations sur l’obtention de l’URL, consultez la [documentation Take a Test](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Connexion**à l’imprimante : choisissez **exiger** pour autoriser uniquement l’accès à l’application prendre un test à partir des appareils qui sont connectés à une imprimante. Ce paramètre rend également le bouton d’impression de l’application disponible pour test-interrogées. **Non configuré** permet aux élèves d’accéder à l’application à partir d’appareils qui ne sont pas connectés à une imprimante.  
- **Surveillance de l’écran** : choisissez **Autoriser** pour surveiller l’activité de l’écran pendant que les utilisateurs effectuent un test. L’option **Non configuré** vous empêche de surveiller l’écran pendant le test.
- **Suggestions de texte** : choisissez **Autoriser** pour que les personnes répondant au test puissent afficher des suggestions de texte. L’option **Non configuré** bloque les suggestions de texte pendant que les utilisateurs effectuent un test.

## <a name="next-steps"></a>Étapes suivantes

[Affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).
