---
title: Afficher l’inventaire logiciel et matériel pour les PC Windows
titleSuffix: Microsoft Intune
description: Comment afficher les informations matérielles et logicielles sur les ordinateurs de bureau Windows que vous gérez comme PC avec le client logiciel Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b9d17426bf3dde3fd1684c12113adf0c5095d5f
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353302"
---
# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Afficher l’inventaire logiciel et matériel pour les PC Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> Les informations de cette rubrique s’appliquent uniquement aux bureaux Windows que vous gérez en tant que PC à l’aide du client logiciel Intune. Si vous souhaitez afficher l’inventaire des PC Windows inscrits en tant qu’appareils mobiles, consultez [afficher les détails des appareils dans Intune](device-inventory.md).

Intune collecte des informations détaillées sur le matériel et les logiciels pour les ordinateurs de bureau que vous gérez en tant que PC à l’aide du client logiciel Intune. Utilisez les informations contenues dans les procédures suivantes pour apprendre à créer :

- Un rapport qui répertorie les informations sur les capacités matérielles des PC que vous gérez.

- Un rapport qui répertorie les logiciels installés sur chaque PC.

- Guide pratique d'actualisation d'un inventaire de PC pour vous assurer que les données du rapport sont récentes.

## <a name="to-display-information-about-pcs-you-manage"></a>Pour afficher des informations sur les PC que vous gérez

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Rapports** &gt; **Rapports d’inventaire des ordinateurs**.

2. Dans la page **Créer un rapport** , acceptez les valeurs par défaut ou personnalisez-les pour filtrer les résultats qui seront renvoyés par le rapport. Par exemple, vous pouvez déterminer que seuls les PC qui exécutent Windows 8.1 s'affichent dans le rapport.

3. Choisissez **Afficher le rapport** pour ouvrir le **Rapport d’inventaire informatique** dans une nouvelle fenêtre.

    Vous pouvez trier le rapport en fonction des différentes colonnes, telles que le **Nom**, le **Type de châssis** ou le **Fabricant** en sélectionnant chaque en-tête de colonne.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>Pour afficher les logiciels installés sur les PC que vous gérez

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Rapports** &gt; **Rapports de logiciels détectés**.

2. Dans la page **Créer un rapport** , acceptez les valeurs par défaut ou personnalisez-les pour filtrer les résultats qui seront renvoyés par le rapport. Par exemple, vous pouvez décider que seuls les logiciels publiés par Microsoft seront affichés dans le rapport.

3. Choisissez **Afficher le rapport** pour ouvrir le **Rapport de logiciels détectés** dans une nouvelle fenêtre.

    Vous pouvez trier le rapport en fonction des différentes colonnes, telles que le **Nom**, l’**Éditeur** ou la **Catégorie** en sélectionnant chaque en-tête de colonne. Vous pouvez développer les mises à jour dans la liste pour afficher plus de détails (par exemple les PC sur lesquels elles sont installées) en choisissant la flèche directionnelle à côté de l’élément de liste.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Pour actualiser les ressources de l'ordinateur pour vérifier qu'elles sont récentes

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Groupes** &gt; **Tous les appareils** (ou un autre groupe qui contient le PC dont vous souhaitez actualiser l’inventaire).

2. Sélectionnez un ordinateur ou maintenez la touche **Ctrl** enfoncée pour sélectionner plusieurs PC.

3. Dans la barre des tâches, choisissez **Tâches à distance** &gt; **Actualiser l’inventaire**.

4. Pour afficher l’état des tâches, choisissez **Tâches à distance** dans le coin inférieur droit de la page.

    La boîte de dialogue **État de la tâche** affiche les tâches à distance en cours, l'état de la tâche, le nom de l'appareil et toutes les erreurs signalées et fournit un lien permettant de corriger ces informations.

## <a name="see-also"></a>Voir aussi

[Tâches courantes de gestion des PC Windows avec le client logiciel Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
