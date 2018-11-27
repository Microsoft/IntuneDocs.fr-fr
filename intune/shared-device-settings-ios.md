---
title: Paramètres de configuration des appareils Microsoft Intune partagés pour iOS
titlesuffix: ''
description: Découvrez les paramètres Microsoft Intune que vous pouvez utiliser pour afficher des informations sur l’écran de verrouillage des appareils iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 638b4b3ebc83917faae0d34ec407b8ad47b4a4fb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183381"
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Paramètres de configuration des appareils partagés permettant d’afficher des messages sur l’écran de verrouillage d’un appareil iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article décrit les paramètres Microsoft Intune que vous pouvez utiliser pour afficher des informations sur l’écran de verrouillage des appareils iOS.

Les paramètres de configuration des appareils partagés vous permettent de spécifier le texte facultatif affiché sur la fenêtre de connexion et l’écran de verrouillage, par exemple un message de type « Si perdu, renvoyez à » et des informations d’étiquette d’inventaire. 

>[!IMPORTANT]
> Cette fonctionnalité est prise en charge sur les appareils supervisés exécutant iOS 9.3 et ultérieur.

## <a name="create-shared-device-settings"></a>Créer des paramètres d’appareils partagés

1. À partir de [Intune dans le portail Azure](https://portal.azure.com), naviguez vers [**Fonctionnalités de l’appareil** dans la zone de configuration de l’appareil](device-features-configure.md). 
1. Dans le volet **Fonctionnalités de l’appareil**, sélectionnez **Configuration des appareils partagés (mode supervisé uniquement)**.
2. Dans le volet **Configuration des appareils partagés (mode supervisé uniquement)**, configurez les paramètres suivants :
    - **Informations de l’étiquette d’inventaire** : entrez des informations sur l’étiquette d’inventaire de l’appareil. Par exemple : **Appartient à Contoso Corp**. Les informations que vous entrez sont appliquées à tous les appareils auxquels vous affectez ce profil.
    - **Note de l’écran de verrouillage** : entrez une note qui pourrait vous aider à récupérer l’appareil en cas de perte ou de vol. Par exemple : **Si vous trouvez cet appareil, appelez le « numéro »**.
3. Quand vous avez terminé, cliquez sur **OK** plusieurs fois pour revenir au volet **Créer un profil**, puis choisissez **Créer**. 


## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant affecter le profil d’appareil aux groupes que vous choisissez. Pour plus d’informations, consultez [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md).
