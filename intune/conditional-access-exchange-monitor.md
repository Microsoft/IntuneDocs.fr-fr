---
title: Surveiller l’accès conditionnel Exchange dans Microsoft Intune | Microsoft Intune
description: Surveillez la conformité de l’accès conditionnel pour Exchange local et Exchange Online par le biais du portail Intune Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0078a8abfa6675d7df49b62b347fd5ede2a06d03
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233804"
---
# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune"></a>Surveiller la conformité des accès conditionnels pour Exchange local et Exchange Online dans Intune

À compter d’Intune version 1704, les administrateurs peuvent voir les informations de rapport liées aux enregistrements d’appareils Exchange ActiveSync qui sont synchronisés avec Intune via le Connecteur Exchange local ou le connecteur service à service Intune (connecteur Exchange Online). Les rapports de conformité de l’accès conditionnel offrent un résumé des appareils avec différents états de synchronisation :

-   **Autoriser**

-   **Bloquer**

-   **Quarantaine**

## <a name="to-monitor-conditional-access-compliance"></a>Surveiller la conformité de l’accès conditionnel

1.  Accédez au [portail Azure](https://portal.azure.com/) et connectez-vous avec vos informations d’identification Intune.

2.  Une fois correctement connecté, le **tableau de bord Azure** apparaît.

3.  Choisissez **Tous les services** dans le menu de gauche, puis entrez **Intune** dans le filtre de la zone de texte.

4.  Choisissez **Intune**, vous voyez le **tableau de bord Intune**.

5.  Choisissez **Accès conditionnel**, puis **Vue d’ensemble**.

6.  Choisissez l’une des trois zones (**Autorisé**, **Bloqué** ou **Quarantaine**) sur le graphique pour afficher vos rapports de conformité d’accès conditionnel.

    ![Image du tableau de bord d’accès conditionnel](./media/CA-reporting-intune-1.png)

Une fois que vous avez choisi l’une des trois zones, vous pouvez voir plus de détails sur les appareils autorisés, bloqués ou mis en quarantaine.

Vous pouvez également rechercher des appareils spécifiques pour afficher plus de détails. Par exemple, l’appareil sélectionné sur l’image ci-dessous est bloqué. Intune vous donne la possibilité de supprimer les données d’entreprise du volet de rapports de conformité de l’accès conditionnel.

![Image des rapports détaillés des appareils pour l’accès conditionnel](./media/CA-reporting-intune-3.png)

Dans le volet de détails de l’appareil, vous pouvez voir plus d’informations :

-   **Vue d’ensemble :** vous pouvez voir les propriétés de l’appareil comme la version du système d’exploitation, la propriété, le numéro de série, le fabricant, le numéro de téléphone et la dernière fois que l’appareil s’est connecté.

-   **Propriétés :** vous pouvez définir la propriété de l’appareil (personnel ou entreprise).

-   **Matériel :** fournit les informations affichées dans la vue d’ensemble, ainsi que les détails du stockage (espace total et espace libre), le boîtier système, les détails du réseau, le service réseau et plus de détails sur le blocage d’accès conditionnel.

-   **Applications découvertes :** affiche toutes les applications installées sur votre appareil. Vous pouvez également exporter la liste des applications installées au format CSV.

-   **Conformité :** indique les détails de la stratégie de conformité de l’appareil.

-   **Configuration de l’appareil :** affiche tous les détails de configuration de l’appareil.

-   **Accès à Exchange :** ici, vous pouvez en savoir plus sur l’état de l’appareil après l’application des stratégies d’accès conditionnel.
