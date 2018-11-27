---
title: Surveiller la conformité des appareils
titlesuffix: Microsoft Intune
description: Apprenez à surveiller la conformité des appareils.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0790934b-48b9-435b-a8aa-e83ed5b73191
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b6c86b8f365f5ac3e65e91725e9fcd29ccd9ef58
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187020"
---
# <a name="monitor-device-compliance-in-intune"></a>Surveiller la conformité des appareils dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez afficher le résumé de l’état de vos **profils de conformité** dans le panneau **Vue d'ensemble**.
Vous pouvez cliquer de manière interactive sur les graphiques pour explorer les détails. Si plusieurs profils de conformité sont configurés, vous pouvez afficher l’état des stratégies dans le panneau des stratégies sous **Gérer** > **Rapports**.

##  <a name="device-compliance"></a>Conformité de l’appareil

La vue récapitulative du rapport de conformité des appareils présente une liste d’informations agrégées sur le nombre d’appareils qui se signalent avec un des états suivants :

- **Conforme** : l’appareil a été évalué récemment et il est conforme aux paramètres du profil de conformité spécifié.
- **Non conforme**: l’appareil a été évalué comme non conforme.  Si une période de grâce a été définie dans le profil, elle a expiré et l'appareil passe dans un état non conforme.
- **Période de grâce**: l’appareil a été évalué comme non conforme. Cependant, la période de grâce continue de s’appliquer avant que l’appareil soit marqué comme non conforme.

Vous pouvez rechercher dans chaque section pour afficher plus de détails sur les appareils et utilisateurs individuels.

## <a name="setting-compliance"></a>Configuration de la conformité

Le rapport de conformité aux paramètres fournit des détails pour chaque paramètre de conformité, notamment :

- Le nombre d'appareils non compatibles avec le paramètre.
- La plateforme à laquelle le paramètre est appliqué.

Vous pouvez rechercher dans chaque paramètre pour afficher plus d’informations sur les profils dans lesquels ces paramètres ont été activés, ainsi que la valeur du paramètre.
