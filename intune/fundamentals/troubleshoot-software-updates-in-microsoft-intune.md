---
title: Résoudre les problèmes de mise à jour logicielle dans Microsoft Intune - Azure | Microsoft Docs
description: Résoudre les problèmes de mise à jour logicielle dans Microsoft Intune.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7da927754971fb66a5d8442d0cdf18e0ebfbcd4a
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059075"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Résoudre les problèmes de mise à jour logicielle dans Microsoft Intune

Aidez à résoudre les problèmes de mise à jour logicielle dans Microsoft Intune. Pour afficher la liste des codes d’erreur et les descriptions, accédez à [Codes d’erreur de l’agent de mise à jour logicielle dans Microsoft Intune](../protect/software-update-agent-error-codes.md).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>Les appareils Windows 7 avec de nombreuses mises à jour remplacées arrêtent d’envoyer des rapports à Intune

Les clients Microsoft Intune peuvent rencontrer un ou plusieurs des problèmes suivants :

- Les appareils cessent subitement d’envoyer des rapports à Intune.  
- Les appareils subissent une utilisation élevée du processeur.
- L’installation des applications via Intune est lente.
- Microsoft Intune Center affiche l’erreur suivante : `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- L’état de Console d’administration Intune > Groupes > Tous les appareils > affiche : `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Ce problème peut se produire si des mises à jour remplacées (des mises à jour remplacées par une autre mise à jour) n’ont pas été suspendues pendant une période prolongée. Au cours de certains processus, tels que l’installation d’une application, Windows vérifie toutes les mises à jour remplacées dans l’ordre afin que les mises à jour et celles qui leur succèdent soient être correctement mappées. Si la liste des mises à jour remplacées devient trop importante, cette tâche de vérification peut entraîner une utilisation élevée du processeur en raison de la charge de traitement et du temps requis. Ce problème affecte principalement les appareils Windows 7 en raison du grand nombre de mises à jour remplacées qui sont disponibles pour Windows 7. Les systèmes d’exploitation plus récents peuvent ne pas avoir autant de mises à jour remplacées et peuvent ne pas être vulnérables à ce problème.

**Résolution**

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Mises à jour logicielles**.
3. Refusez toutes les mises à jour remplacées qui peuvent s’appliquer à Windows 7 ou aux applications (comme Microsoft Office) qui ont été installées sur les clients concernés.
4. Redémarrez les clients concernés.

Si vous utilisez Windows 7, vérifiez que vous disposez de la mise à jour suivante installée :[3050265 Client de mise à jour Windows pour Windows 7 : juin 2015](https://support.microsoft.com/kb/3050265).

## <a name="next-steps"></a>Étapes suivantes

Obtenir [l’aide de Microsoft](get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).