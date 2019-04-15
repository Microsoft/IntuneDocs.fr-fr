---
title: Configurer les paramètres Endpoint Protection dans Microsoft Intune - Azure | Microsoft Docs
description: Créez des paramètres Endpoint Protection quand vous créez un profil d’appareil macOS ou Windows 10 dans Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 3/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: add75e252c8d49025ac01832e5fb12afea9ede67
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57398560"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Ajouter des paramètres Endpoint Protection dans Intune

Endpoint Protection vous permet de contrôler différentes fonctionnalités de sécurité sur vos appareils, notamment le pare-feu, BitLocker, l’autorisation et le blocage des applications, Windows Defender, le chiffrement, etc. Vous pouvez configurer ces paramètres dans Microsoft Intune à l’aide des profils d’appareil.

Par exemple, vous pouvez créer un profil Endpoint Protection qui autorise uniquement les utilisateurs macOS à installer des applications à partir du Mac App Store. Vous pouvez également activer Windows SmartScreen quand vous exécutez des applications sur des appareils Windows 10.

Cet article vous montre comment créer un profil. Sélectionnez ensuite la plateforme de votre appareil pour plus d’informations sur les paramètres disponibles.

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Créer un profil d’appareil contenant des paramètres Endpoint Protection

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
4. Entrez un **Nom** et une **Description** pour le profil Endpoint Protection.
5. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres personnalisés. Actuellement, vous pouvez choisir l’une des plateformes suivantes pour les paramètres de restriction de l’appareil :
   - **MacOS**
   - **Windows 10 et versions ultérieures**
6. Dans la liste déroulante **Type de profil**, choisissez **Endpoint Protection**. 
7. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Accédez à l’une des rubriques suivantes pour obtenir les paramètres détaillés pour chaque plateforme :
   - [Paramètres macOS](endpoint-protection-macos.md)
   - [Paramètres Windows 10](endpoint-protection-windows-10.md)
8. Quand vous avez terminé, revenez à la page **Créer un profil**, puis cliquez sur **Créer**.

Le profil est créé et apparaît dans la page de la liste des profils. Pour affecter ce profil à des groupes, consultez [Affecter des profils d’appareil](device-profile-assign.md).

## <a name="next-steps"></a>Étapes suivantes
Pour affecter un profil à des groupes, consultez [Affecter des profils d’appareil](device-profile-assign.md).
