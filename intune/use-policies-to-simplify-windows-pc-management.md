---
title: Utiliser des stratégies pour simplifier la gestion des PC Windows
titleSuffix: Microsoft Intune
description: Décrit les stratégies de gestion des PC Windows et les paramètres de Microsoft Intune Center.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f0afda7e-f4c3-4bcd-b4bf-4304103cf73e
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: b612a245e0a12384f8f9e7ec4a2c970afc2fd628
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67548822"
---
# <a name="use-policies-to-simplify-windows-pc-management"></a>Utiliser des stratégies pour simplifier la gestion des PC Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Pour gérer les ordinateurs de bureau Windows en tant que PC en y exécutant le client logiciel Intune, vous pouvez utiliser uniquement les stratégies qui se trouvent sous **Gestion de l'ordinateur** dans la console d’administration Intune. Toutes les autres stratégies répertoriées dans la console d’administration sont réservés aux appareils mobiles uniquement. Utilisez les stratégies de la **Gestion de l’ordinateur** pour configurer les paramètres de Microsoft Intune Center, contrôler les mises à jour apportées aux PC et configurer le Pare-feu Windows pour les PC.

![Modèle de stratégies pour les PC Windows](media/pc_policy_template.png)

### <a name="manage-the-microsoft-intune-center"></a>Gérer Microsoft Intune Center
Pour les utilisateurs, le client logiciel Intune apparaît comme **Microsoft Intune Center**. Microsoft Intune Center permet aux utilisateurs d’effectuer les opérations suivantes :

- Obtenir des applications à partir du portail d'entreprise.

- Rechercher des mises à jour.

- Gérer Microsoft Intune Endpoint Protection.

- Demander l'assistance à distance.

Microsoft Intune Center est installé sur tous les ordinateurs gérés. Vous pouvez configurer les paramètres suivants dans une stratégie Intune. Ceux-ci s’affichent pour les utilisateurs dans Microsoft Intune Center :

|Paramètre de stratégie|Détails|
|------------------|--------------------|
|**Nom**|Nom de l'administrateur responsable de la gestion de l'ordinateur.<br />Longueur maximale : 40 caractères|
|**Numéro de téléphone**|Numéro de téléphone de l'administrateur responsable de la gestion de l'ordinateur.<br />Longueur maximale : 20 caractères|
|**Adresse de messagerie**|Adresse e-mail de l'administrateur responsable de la gestion de l'ordinateur.<br />Longueur maximale : 40 caractères|
|**Nom du site web**|Nom de votre site web de support pour les utilisateurs.<br />>Longueur maximale : 40 caractères|
|**URL du site web**|L'URL de votre site web de support.<br />Longueur maximale : 150 caractères|
|**Remarques**|Remarque affichée pour les utilisateurs.<br />Longueur maximale : 120 caractères|

Consultez les ressources suivantes pour plus d’informations sur les stratégies et les paramètres que vous pouvez configurer pour les PC Windows :

- [Maintenir à jour des PC Windows avec les mises à jour logicielles dans Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) : Ces stratégies permettent aux ordinateurs gérés de rechercher et télécharger les mises à jour logicielles auprès de Microsoft et de tiers. Ces mises à jour ne comprennent pas les mises à niveau du système d’exploitation (par exemple, la mise à niveau de Windows 7 vers Windows 10, ni les mises à niveau d’une version de Windows 10 vers une version ultérieure).

- [Mieux sécuriser les PC Windows avec Endpoint Protection pour Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) : ces paramètres incluent les planifications d’analyse et les mesures à prendre quand un programme malveillant est détecté.

- [Protéger les PC Windows à l’aide des stratégies du Pare-feu Windows dans Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) : ces stratégies simplifient l’administration des paramètres du Pare-feu Windows sur les ordinateurs gérés.


### <a name="see-also"></a>Voir aussi

[Tâches courantes de gestion des PC Windows avec le client logiciel Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
