---
title: Configurer les paramètres Endpoint Protection dans Microsoft Intune - Azure | Microsoft Docs
description: Créez des paramètres Endpoint Protection quand vous créez un profil d’appareil macOS ou Windows 10 dans Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: c13c5d71d1ff631d7a3c84cd3f62037569757917
ms.sourcegitcommit: bc5e4dff18f5f9b79077a888f8a58dcc490708c0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975775"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Ajouter des paramètres Endpoint Protection dans Intune

Avec Intune, vous pouvez utiliser des profils de configuration d’appareils pour gérer différentes fonctionnalités de sécurité Endpoint Protection courantes sur les appareils :
- Pare-feu 
- BitLocker
- Autorisation ou blocage des applications  
- Windows Defender et chiffrement

Par exemple, vous pouvez créer un profil Endpoint Protection qui autorise uniquement les utilisateurs macOS à installer des applications à partir du Mac App Store. Vous pouvez également activer Windows SmartScreen quand vous exécutez des applications sur des appareils Windows 10.

Avant de créer un profil, consultez les articles suivants. Ils détaillent les paramètres Endpoint Protection qu’Intune peut gérer pour chacune des plateformes prises en charge : 
   - [Paramètres macOS](endpoint-protection-macos.md)
   - [Paramètres Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Créer un profil d’appareil contenant des paramètres Endpoint Protection

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=20909).
3. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
4. Entrez un **Nom** et une **Description** pour le profil Endpoint Protection.
5. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres personnalisés. Actuellement, vous pouvez choisir l’une des plateformes suivantes pour les paramètres de restriction de l’appareil :
   - **MacOS**
   - **Windows 10 et versions ultérieures**
6. Dans la liste déroulante **Type de profil**, choisissez **Endpoint Protection**. 
7. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Consultez :
   - [Paramètres macOS](endpoint-protection-macos.md)
   - [Paramètres Windows 10](endpoint-protection-windows-10.md)  

8. Après avoir configuré les paramètres applicables, sélectionnez **Créer** sur la page **Créer un profil**.

   Le profil est créé et apparaît dans la page de la liste des profils. Pour affecter ce profil à des groupes, consultez [Affecter des profils d’appareil](device-profile-assign.md).


## <a name="next-steps"></a>Étapes suivantes  

Pour affecter un profil à des groupes, consultez [Affecter des profils d’appareil](device-profile-assign.md).
