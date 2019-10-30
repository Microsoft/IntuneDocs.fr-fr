---
title: Lier des appareils Android par emplacement réseau dans Microsoft Intune - Azure | Microsoft Docs
description: Créez ou configurez des emplacements réseau dans Microsoft Intune pour les appareils Android. Vous pouvez marquer des appareils comme non conformes en fonction de l’emplacement réseau de l’appareil. Si l’appareil sort de l’emplacement réseau, vous pouvez bloquer l’accès aux ressources de l’entreprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 648ccd889714c2ee4f7ee1fa04301490ad9fd001
ms.sourcegitcommit: c2e62f1ebdf75599c8e544287123c602f0f15f2b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72749439"
---
# <a name="use-locations-network-fence-in-intune"></a>Utiliser des emplacements (délimitation du réseau) dans Intune

Vous pouvez bloquer l’accès à un réseau d’entreprise si un appareil quitte un emplacement. La fonctionnalité **Emplacements** dans Intune fournit cette fonction. 

Vous pouvez créer une stratégie de conformité basée sur l’emplacement réseau, également appelée « délimitation du réseau ». La stratégie garantit que les appareils doivent être connectés à un réseau professionnel pour être conformes. Cette stratégie peut être utilisée avec les stratégies d’accès conditionnel afin que les appareils puissent accéder aux ressources de travail *uniquement* quand l’appareil est connecté au réseau professionnel. Quand l’appareil n’est pas connecté au réseau professionnel, il devient non conforme et perd l’accès aux ressources de travail.

Considérez le scénario suivant :

Dans votre site de production, certains employés utilisent des appareils Android. Un employé emmène un appareil Android à l’extérieur du site ou de l’usine. Pour empêcher tout accès non autorisé, vous pouvez effectuer les opérations suivantes :

1. Créez un emplacement avec une plage IPv4 appelé **Atelier de fabrication**.
2. Créez une stratégie de conformité qui exige que ces appareils soient connectés à votre réseau d’entreprise et affectez cette stratégie.
3. Si l’appareil sort de l’usine de fabrication, il est considéré comme non conforme et n’a pas accès aux ressources de l’entreprise.

En outre, vous pouvez ajouter des [actions pour la non-conformité](#configure-the-actions-for-noncompliance). Quand l’appareil est de retour sur site et à l’emplacement réseau, il récupère l’accès aux ressources de l’entreprise.

## <a name="prerequisites"></a>Prérequis

Pour créer une stratégie de conformité basée sur l’emplacement :

- Créer un emplacement réseau sous la forme de plages de réseau IPv4 pour le serveur de passerelle, le serveur DHCP et/ou le serveur DNS que les appareils connectent
- Créer la stratégie de conformité qui utilise ces emplacements, puis définir l’action entreprise quand l’appareil n’est plus connecté à l’emplacement réseau
- Appareils Android 6.0 et ultérieur, avec l’application Portail d’entreprise mise à jour

## <a name="create-a-location"></a>Créer un emplacement

1. Dans Intune, sélectionnez **Conformité de l’appareil** > **Emplacements** > **Créer**.

2. Entrez les propriétés suivantes :  

   - Obligatoire. Entrez un **Nom** pour l’emplacement, comme **Atelier de fabrication** ou **Bâtiment 44 sécurisé**.
   - Facultatif. Entrez une **Plage IPv4** avec la notation CIDR (Classless Interdomain Routing), par exemple `aaa.bbb.ccc.ddd/n`.
   - Facultatif. Entrez l’adresse de la **Passerelle IPv4**, par exemple `aaa.bbb.ccc.ddd`.
   - Facultatif. Entrez l’adresse du **Serveur DHCP IPv4**, par exemple `aaa.bbb.ccc.ddd`.
   - Facultatif. Entrez une liste d’adresses de **Serveurs DNS IPv4**. Ce paramètre utilise la **correspondance des sous-ensembles**. Si les serveurs DNS IPv4 sur l’appareil sont des sous-ensembles de valeurs définies, l’appareil est considéré comme se trouvant dans la délimitation. Veillez à entrer une seule adresse par ligne, par exemple :  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - Facultatif. Entrez une liste de **Suffixes DNS**. Ce paramètre utilise la **correspondance des sous-ensembles**. Si les suffixes DNS sur l’appareil sont des sous-ensembles de valeurs définies, l’appareil est considéré comme se trouvant dans la délimitation. Veillez à entrer un seul nom de domaine par ligne, par exemple :  
     `contoso.com`  
     `contoso.org`

3. **Enregistrez** les changements apportés.

## <a name="create-the-location-compliance-policy"></a>Créer la stratégie de conformité des emplacements

Quand vous [créez la stratégie de conformité](create-compliance-policy.md), sélectionnez **Android** pour **Plateforme**. Dans **Emplacements**, vous pouvez choisir un ou plusieurs des emplacements réseau que vous avez ajoutés. Ces emplacements font partie de la délimitation du réseau que vous créez pour vos appareils. 


## <a name="configure-the-actions-for-noncompliance"></a>Configurer les actions en cas de non-conformité

Une fois la stratégie de conformité créée, l’action par défaut en cas de non-conformité s’applique à l’appareil. Vous pouvez ajouter d’autres actions. Par exemple, ajoutez une action qui envoie un e-mail à l’utilisateur quand l’appareil n’est plus conforme aux emplacements.

L’article [Ajouter des actions en cas de non-conformité](actions-for-noncompliance.md) fournit quelques conseils.

## <a name="company-portal-app"></a>Application Portail d’entreprise

Quand l’appareil est connecté à vos emplacements, il est affiché comme étant conforme dans l’application Portail d’entreprise. Quand l’appareil n’est pas connecté à l’un de vos emplacements, il est indiqué comme étant non conforme.

## <a name="next-steps"></a>Étapes suivantes
[Surveiller les stratégies de conformité des appareils](compliance-policy-monitor.md)  
[Bien démarrer avec les stratégies de conformité](device-compliance-get-started.md)
