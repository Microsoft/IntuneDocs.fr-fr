---
title: Configurer les paramètres Endpoint Protection dans Microsoft Intune - Azure | Microsoft Docs
description: Créez des paramètres Endpoint Protection quand vous créez un profil d’appareil macOS ou Windows 10 dans Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 45cdbfe98bca8f7b0e307ed47ad3f78193e6d04c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74164567"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Ajouter des paramètres Endpoint Protection dans Intune

Avec Intune, vous pouvez utiliser des profils de configuration d’appareils pour gérer différentes fonctionnalités de sécurité Endpoint Protection courantes sur les appareils :

- Pare-feu
- BitLocker
- Autorisation ou blocage des applications
- Microsoft Defender et chiffrement

Par exemple, vous pouvez créer un profil Endpoint Protection qui autorise uniquement les utilisateurs macOS à installer des applications à partir du Mac App Store. Vous pouvez également activer Windows SmartScreen quand vous exécutez des applications sur des appareils Windows 10.

Avant de créer un profil, consultez les articles suivants. Ils détaillent les paramètres Endpoint Protection qu’Intune peut gérer pour chacune des plateformes prises en charge :

- [Paramètres macOS](endpoint-protection-macos.md)
- [Paramètres Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Créer un profil d’appareil contenant des paramètres Endpoint Protection

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Entrez un **Nom** et une **Description** pour le profil Endpoint Protection.

4. À partir de la liste déroulante **Plateforme**, sélectionnez la plateforme de l’appareil auquel vous souhaitez appliquer les paramètres personnalisés. Actuellement, vous pouvez choisir l’une des plateformes suivantes pour les paramètres de restriction de l’appareil :

   - **MacOS**
   - **Windows 10 et versions ultérieures**

5. Dans la liste déroulante **Type de profil**, choisissez **Endpoint Protection**.

6. Selon la plateforme que vous choisissez, les paramètres que vous pouvez configurer diffèrent. Consultez :

   - [Paramètres macOS](endpoint-protection-macos.md)
   - [Paramètres Windows 10](endpoint-protection-windows-10.md)

7. Après avoir configuré les paramètres applicables, sélectionnez **Créer** sur la page **Créer un profil**.

   Le profil est créé et apparaît dans la page de la liste des profils. Pour affecter ce profil à des groupes, consultez [Affecter des profils d’appareil](../configuration/device-profile-assign.md).

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Ajouter des règles de pare-feu personnalisées pour les appareils Windows 10

Quand vous configurez le pare-feu Microsoft Defender dans le cadre d’un profil qui inclut des règles de protection de point de terminaison pour Windows 10, vous pouvez configurer des règles personnalisées pour les pare-feu. Les règles personnalisées vous permettent d’étendre l’ensemble prédéfini de règles de pare-feu prises en charge pour Windows 10.

Quand vous planifiez des profils avec des règles de pare-feu personnalisées, prenez en compte les informations suivantes, qui peuvent affecter la façon dont vous choisissez de regrouper les règles de pare-feu dans vos profils :

- Chaque profil prend en charge jusqu’à 150 règles de pare-feu. Quand vous utilisez plus de 150 règles, créez des profils supplémentaires, chacun étant limité à 150 règles.

- Pour chaque profil, si l’application d’une seule règle échoue, toutes les règles sont considérées en échec et aucune des règles n’est appliquée à l’appareil.

- Quand l’application d’une règle échoue, toutes les règles du profil sont signalées comme étant en échec. Intune ne peut pas identifier la règle qui a échoué.  

Les règles de pare-feu qu’Intune peut gérer sont détaillées dans le [fournisseur de services de configuration du pare-feu]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) Windows. Pour consulter la liste des paramètres de pare-feu personnalisés pour les appareils Windows 10 pris en charge par Intune, consultez [Règles de pare-feu personnalisées](endpoint-protection-windows-10.md#firewall-rules).

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Pour ajouter des règles de pare-feu personnalisées à un profil Endpoint Protection

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Pour *Plateforme*, sélectionnez **Windows 10 et ultérieur** puis, pour *Type de profil*, sélectionnez **Endpoint protection**.

4. Sélectionnez **Pare-feu Microsoft Defender** pour ouvrir la page de configuration puis, pour *Règles de pare-feu*, sélectionnez **Ajouter** pour ouvrir la règle **Créer une règle**.

5. Spécifiez les paramètres de la règle de pare-feu, puis sélectionnez **OK** pour l’enregistrer. Pour passer en revue les options des règles de pare-feu personnalisées disponibles dans la documentation, consultez [Règles de pare-feu personnalisées](endpoint-protection-windows-10.md#firewall-rules).

6. Une fois la règle enregistrée, elle apparaît dans la page *Pare-feu Microsoft Defender*, dans la liste des règles.

7. Pour modifier une règle, sélectionnez la règle dans la liste pour ouvrir la page **Modifier la règle**.

8. Pour supprimer une règle dans un profil, sélectionnez les points de suspension **(...)** pour la règle, puis sélectionnez **Supprimer**.

9. Pour changer l’ordre d’affichage des règles, sélectionnez l’icône de *flèche vers le haut, flèche vers le bas* en haut de la liste des règles.

## <a name="next-steps"></a>Étapes suivantes

Pour affecter un profil à des groupes, consultez [Affecter des profils d’appareil](../configuration/device-profile-assign.md).
