---
title: Personnaliser l’écran de verrouillage sur les appareils iOS à l’aide de Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Découvrez les paramètres Microsoft Intune que vous pouvez utiliser pour afficher des informations sur l’écran de verrouillage des appareils iOS à l’aide des paramètres de configuration des appareils partagés pour iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203074"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Ajouter des messages personnalisés à l’écran de verrouillage et à la fenêtre de connexion sur des appareils iOS avec Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article décrit les paramètres Microsoft Intune que vous pouvez utiliser pour afficher des informations sur l’écran de verrouillage et la fenêtre de connexion des appareils iOS. 

Utilisez ces paramètres pour afficher du texte ou un message personnalisé sur l’écran de verrouillage et la fenêtre de connexion, par exemple un message de type « En cas de perte, renvoyez à » et des informations d’étiquette d’inventaire.

Ces paramètres prennent en charge les appareils supervisés exécutant iOS 9.3 et ultérieur.

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services** > filtrez sur **Intune** > sélectionnez **Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez un **Nom** et une **Description** pour le profil.
4. Dans **Plateforme**, sélectionnez **iOS**. Dans **Type de profil**, sélectionnez **Fonctionnalités de l’appareil**.
5. Dans **Paramètres**, sélectionnez **Message d’écran de verrouillage (supervisé uniquement)**. Configurez les paramètres suivants :

    - **Informations de l’étiquette d’inventaire** : entrez des informations sur l’étiquette d’inventaire de l’appareil. Par exemple, entrez `123xyz`.

        Le texte que vous entrez est affiché sur l’écran de verrouillage et la fenêtre de connexion sur l’appareil.

    - **Note de l’écran de verrouillage** : entrez une note qui pourrait vous aider à récupérer l’appareil en cas de perte ou de vol. Vous pouvez entrer n’importe quel texte dans ce champ. Par exemple, entrez quelque chose du genre `If found, call Contoso at ...`.

    Vous pouvez aussi utiliser des jetons d’appareil pour ajouter des informations propres à l’appareil dans ces champs. Par exemple, pour afficher le numéro de série, entrez `Serial Number: {{serialnumber}}`. L’écran de verrouillage affichera le texte `Serial Number 123456789ABC`. Quand vous entrez les variables, veillez à utiliser des accolades `{{ }}`. [Jetons de configuration d’application](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) inclut une liste de variables qui peuvent être utilisées. Vous pouvez également utiliser `deviceName` ou toute autre valeur propre à l’appareil.

6. Quand vous avez terminé, sélectionnez **OK** > **OK** > **Créer**. Votre profil est affiché dans la liste.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Ensuite, [attribuez le profil](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).
