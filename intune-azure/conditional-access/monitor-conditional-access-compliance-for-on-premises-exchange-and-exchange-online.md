---
title: "Surveiller la conformité des accès conditionnels pour Exchange local et Exchange Online"
titleSuffix: Intune Azure preview
description: "Surveiller la conformité des accès conditionnels pour Exchange local et Exchange Online via le portail Intune Azure"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: c8715f96f532ee6bacda231e1147d03226ecbb48
ms.openlocfilehash: 9d5521de8709bf232dedfeeb1874f8db1898f2d0
ms.lasthandoff: 04/26/2017


---

# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune-azure-preview"></a>Surveiller la conformité des accès conditionnels pour Exchange local et Exchange Online dans la version préliminaire d’Intune Azure

À compter d’Intune version 1704, les administrateurs peuvent voir les informations de rapport liées aux enregistrements d’appareils Exchange ActiveSync qui sont synchronisés avec Intune via le Connecteur Exchange local ou le connecteur service à service Intune (connecteur Exchange Online). Les rapports de conformité de l’accès conditionnel offrent un résumé des appareils avec différents états de synchronisation :

-   **Autoriser**

-   **Bloquer**

-   **Quarantaine**

## <a name="to-monitor-conditional-access-compliance"></a>Surveiller la conformité de l’accès conditionnel

1.  Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous avec vos informations d’identification Intune.

2.  Une fois correctement connecté, le **tableau de bord Azure** apparaît.

3.  Choisissez **Autres services** dans le menu de gauche, puis tapez **Intune** dans le filtre de zone de texte.

4.  Choisissez **Intune**, vous voyez le **tableau de bord Intune**.

5.  Choisissez **Accès conditionnel**, puis **Vue d’ensemble**.

6.  Choisissez une des trois zones (**Bloqué**, **Quarantaine** ou **Autorisé**) sur le graphique pour afficher vos rapports de conformité d’accès conditionnel.

    ![Tableau de bord d’accès conditionnel](../media/CA-reporting-intune-1.png)

Une fois que vous choisissez une des trois zones, vous pouvez voir plus de détails sur les appareils autorisés, bloqués ou mis en quarantaine.

Vous pouvez également rechercher des appareils spécifiques pour afficher plus de détails. Par exemple, l’appareil sélectionné sur l’image ci-dessous est bloqué. Intune vous donne la possibilité de supprimer les données d’entreprise du panneau de rapports de conformité de l’accès conditionnel.

![Rapports détaillés des appareils pour l’accès conditionnel](../media/CA-reporting-intune-3.png)

Dans le panneau de détails de l’appareil, vous pouvez voir plus d’informations :

-   **Vue d’ensemble :** vous pouvez voir les propriétés de l’appareil comme : la version du système d’exploitation, la propriété, le numéro de série, le fabricant, le numéro de téléphone et la dernière fois que l’appareil s’est connecté.

-   **Propriétés :** vous pouvez définir la propriété de l’appareil (personnel ou entreprise).

-   **Matériel :** fournit les informations affichées dans la vue d’ensemble, ainsi que les détails du stockage (espace total et espace libre), le boîtier système, les détails du réseau, le service réseau et plus de détails sur le blocage d’accès conditionnel.

-   **Applications découvertes :** affiche toutes les applications installées sur votre appareil. Vous pouvez également exporter la liste des applications installées au format CSV.

-   **Conformité :** indique les détails de la stratégie de conformité de l’appareil.

-   **Configuration de l’appareil :** affiche tous les détails de configuration de l’appareil.

-   **Accès à Exchange :** ici, vous pouvez en savoir plus sur l’état de l’appareil après l’application des stratégies d’accès conditionnel.

