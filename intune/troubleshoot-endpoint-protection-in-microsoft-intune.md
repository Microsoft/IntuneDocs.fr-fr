---
title: Résoudre les problèmes de protection de point de terminaison dans Intune - Azure | Microsoft Docs
description: Cette rubrique explique comment résoudre les problèmes en utilisant Microsoft Intune Endpoint Protection.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1d8794345f22b2c19cf89eca2d3603fe8ac68161
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49643057"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Résoudre les problèmes liés à la protection des points de terminaison dans Intune

Utilisez les informations pour vous aider à résoudre les problèmes liés à la protection des points de terminaison. Vous pouvez également [passer en revue les journaux des événements et codes d’erreur pour résoudre les problèmes avec Windows Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

Si ces informations ne vous aident pas, vous pouvez également [bénéficier d’un support technique pour Microsoft Intune](get-support.md).

### <a name="error-messages"></a>Messages d'erreur
Cette section décrit les causes et solutions possibles pour les erreurs et avertissements suivants.

|Élément d'état|Causes possibles|Solutions possibles|
|---------------|--------------------|-----------------------|
|**Moteur Endpoint Protection indisponible**|Le moteur Intune Endpoint Protection est endommagé ou a été supprimé.|Si le moteur Intune Endpoint Protection est endommagé, vous pouvez tenter de mettre à jour ou de réinstaller le logiciel.<br /><br />Pour forcer une mise à jour immédiate, choisissez **Mettre à jour** dans le logiciel client Endpoint Protection (figurant dans la barre des tâches sur les ordinateurs gérés).<br /><br />Si le moteur ne peut pas être mis à jour, vous devez réinstaller le moteur Endpoint Protection.<br /><br />Dans la liste des programmes installés dans le Panneau de configuration sur l’ordinateur géré, recherchez **Agent de Microsoft Intune Endpoint Protection**, puis désinstallez l’application.<br /><br />Lors de la prochaine synchronisation des mises à jour, le Gestionnaire de mise à jour de Microsoft Online Management détecte le programme manquant et le réinstalle au moment de l'installation planifiée.|
|**Endpoint Protection désactivé**|Intune Endpoint Protection a été désactivé par un administrateur à l’aide d’un profil de configuration ou par un utilisateur sur un ordinateur managé.|Activer la protection du point de terminaison. Consultez [Ajouter des paramètres de protection de point de terminaison](endpoint-protection-configure.md) dans Intune ou [Activer Windows Defender pour accéder aux ressources de la société](/intune-user-help/turn-on-defender-windows).|
|**Protection en temps réel désactivée**|La protection en temps réel a été désactivée par un administrateur à l’aide d’un profil ou par un utilisateur sur un ordinateur managé.|Activer la protection du point de terminaison. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) dans Intune, ou [Activer la protection en temps réel pour accéder aux ressources de la société](/intune-user-help/turn-on-defender-windows). |
|**Analyse des téléchargements désactivée**|L'analyse des téléchargements a été désactivée par un administrateur à l'aide d'un profil ou par un utilisateur sur un ordinateur managé.|Activer l’analyse. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) dans Intune, ou [Activer la protection en temps réel pour accéder aux ressources de la société](/intune-user-help/turn-on-defender-windows). |
|**Analyse de l’activité des fichiers et des programmes désactivée**|La surveillance de l'activité des fichiers et des programmes a été désactivée par un administrateur à l’aide d’un profil ou par un utilisateur sur un ordinateur managé.|Activer l’activité des fichiers et des programmes. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) dans Intune, ou [Activer la protection en temps réel pour accéder aux ressources de la société](/intune-user-help/turn-on-defender-windows). |
|**Analyse du comportement désactivée**|La surveillance du comportement a été désactivée par un administrateur à l’aide d’un profil ou par un utilisateur sur un ordinateur managé.|Activer la surveillance du comportement. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) dans Intune, ou [Activer la protection en temps réel pour accéder aux ressources de la société](/intune-user-help/turn-on-defender-windows). |
|**Analyse de scripts désactivée**|L’analyse de scripts a été désactivée par un administrateur à l’aide d’un profil ou par un utilisateur sur un ordinateur managé.|Activer l'analyse de scripts. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) dans Intune, ou [Activer la protection en temps réel pour accéder aux ressources de la société](/intune-user-help/turn-on-defender-windows). |
|**Système NIS (Network Inspection System) désactivé**|Le système NIS a été désactivé par un administrateur à l'aide d'un profil ou par un utilisateur sur un ordinateur managé.|Activer le système NIS (Network Inspection System). Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus) dans Intune, ou [Activer la protection en temps réel pour accéder aux ressources de la société](/intune-user-help/turn-on-defender-windows). |
|**Définitions de programmes malveillants obsolètes**|Il se peut que l'ordinateur soit déconnecté d'Internet depuis un certain temps et que ses définitions de programmes malveillants n'aient pas encore été mises à jour. Cet état s’affiche lorsque les définitions de programmes malveillants sur l’ordinateur sont obsolètes depuis au moins 14 jours.|Si les définitions de programmes malveillants sont obsolètes, vous pouvez les mettre à jour avec [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Analyse complète en retard**|Une analyse complète n'a pas été effectuée depuis 14 jours. Cela peut être dû à un redémarrage pendant une analyse complète.|Si une analyse complète est en retard, vous pouvez exécuter une analyse complète une fois ou planifier des analyses complètes régulières. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus). |
|**Analyse rapide en retard**|Une analyse rapide n'a pas été effectuée depuis 14 jours. Cela peut résulter d'un redémarrage lors d'une analyse rapide.|Si une analyse complète est en retard, vous pouvez exécuter une analyse complète une fois ou planifier des analyses complètes régulières. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Une autre application de protection de point de terminaison est en cours d’exécution**|Une autre application de protection de point de terminaison est en cours d'exécution et l'ordinateur est intègre.|Par défaut, si une autre application de protection de point de terminaison est installée est qu’elle est détectée par Intune, l’appareil peut devenir instable.|

### <a name="next-steps"></a>Étapes suivantes
Si ces informations ne vous aident pas, vous pouvez également [bénéficier d’un support technique pour Microsoft Intune](get-support.md).
