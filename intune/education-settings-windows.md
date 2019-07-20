---
title: Paramètres Windows 10 Éducation dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres Éducation pour les appareils Windows 10. Utilisez ces paramètres dans un profil de configuration d’appareil avec l’application Take a Test, choisissez comment les utilisateurs ou les étudiants se connectent, surveillez l’écran pendant le test et plus encore dans Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d5c78f72e7ffc580cce6cfec7237a3efe3ceb3e5
ms.sourcegitcommit: fd2499df5123758ecb093b4cdd486e35f713b040
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68230100"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Configurer l’application Take a Test sur les appareils Windows 10 à l’aide d’Intune

Cet article décrit tous les paramètres de l’application Take a Test Microsoft Intune Éducation que vous pouvez configurer pour les appareils exécutant Windows 10 et ultérieur. À l’aide de cette application, les étudiants peuvent se connecter à un appareil, puis effectuer un test.

Ces paramètres sont ajoutés à un profil de configuration d’appareil, puis affectés ou déployés sur les appareils avec Microsoft Intune.

[L’application Take a Test dans Intune](education-settings-configure.md) fournit plus d’informations sur cette fonctionnalité.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Paramètres Take a Test  

- **Type de compte** : choisissez la façon dont les utilisateurs se connectent au test. Les options disponibles sont les suivantes :
  - Compte Azure AD
  - Compte de domaine
  - Compte local
- **Nom d’utilisateur du compte** : entrez le nom d’utilisateur du compte utilisé avec l’application Take a Test. Vous pouvez entrer des comptes au format suivant :
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **URL de l’évaluation** : entrez l’URL du test que les utilisateurs doivent effectuer. Pour plus d’informations sur l’obtention de l’URL, consultez la [documentation Take a Test](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Surveillance de l’écran** : choisissez **Autoriser** pour surveiller l’activité de l’écran pendant que les utilisateurs effectuent un test. L’option **Non configuré** vous empêche de surveiller l’écran pendant le test.
- **Suggestion de texte** : choisissez **Autoriser** pour que les personnes répondant au test puissent afficher des suggestions de texte. L’option **Non configuré** bloque les suggestions de texte pendant que les utilisateurs effectuent un test.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il peut ne rien faire pour le moment. Veillez à [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).
