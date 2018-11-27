---
title: Paramètres Intune AirPrint pour appareils iOS et Mac OS
titlesuffix: Microsoft Intune
description: Découvrez comment utiliser Microsoft Intune pour connecter automatiquement des appareils iOS et macOS à des imprimantes compatibles AirPrint.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 850c61868cc5404d1645482a6998856e465b4070
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186288"
---
# <a name="airprint-settings-for-ios-and-macos-devices"></a>Paramètres AirPrint pour appareils iOS et Mac OS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilisez ces paramètres pour configurer les appareils iOS ou Mac OS afin qu’ils se connectent automatiquement aux imprimantes compatibles AirPrint sur votre réseau. Vous avez besoin de l’adresse IP et du chemin de la ressource de vos imprimantes pour continuer.

## <a name="find-airprint-printer-information"></a>Rechercher les informations relatives à l’imprimante AirPrint

Utilisez cette procédure pour ajouter des informations AirPrint à la charge utile AirPrint afin que les utilisateurs d’appareils iOS puissent effectuer des impressions sur des imprimantes AirPrint connues.

1. Sur un Mac connecté au même réseau local (sous-réseau) que les imprimantes AirPrint, ouvrez le Terminal (à partir de **/Applications/Utilities**)
2. Dans le Terminal, tapez **ippfind**, puis appuyez sur Entrée.
3. Notez toutes les informations sur l’imprimante retournées par la commande, par exemple : **ipp://myprinter.local.:631/ipp/port1**. La première partie des informations correspond au nom de votre imprimante, la dernière partie au chemin d’accès de la ressource.
4. Dans le Terminal, tapez **ping myprinter.local**, puis appuyez sur Entrée.
5. Notez l’adresse IP renvoyée par la commande, par exemple **PING myprinter.local (10.50.25.21)**.
6. Enfin, utilisez l’adresse IP et le chemin d’accès de la ressource contenus dans les paramètres de la charge utile AirPrint. Une adresse IP peut être, par exemple, **10.50.25.21**, et un chemin de ressource **/ipp port1**.

## <a name="configure-an-airprint-profile"></a>Configurer un profil AirPrint

1. À partir de [Intune dans le portail Azure](https://portal.azure.com), naviguez vers [**Fonctionnalités de l’appareil** dans la zone de configuration de l’appareil](device-features-configure.md). 
1. Dans le volet **Fonctionnalités de l’appareil**, sélectionnez **AirPrint**.
2. Dans le volet **AirPrint**, pour ajouter une destination AirPrint, entrez son **adresse IP** et le **chemin de la ressource**, puis cliquez sur **Ajouter**.
3. Continuez à ajouter autant de destinations que nécessaire. Quand vous avez terminé, cliquez sur **OK**.

Vous pouvez également importer une liste d’imprimantes à partir d’un fichier .csv, ou encore exporter la liste.


## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant affecter le profil d’appareil aux groupes que vous choisissez. Pour plus d’informations, consultez [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md).