---
title: Message courants sur Endpoint Protection dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez les messages courants et les solutions possibles lorsque vous utilisez et dépannez Endpoint Protection et Windows Defender dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c76466acb375fe49afefc542606350733970f416
ms.sourcegitcommit: 18be0ccc6e51073af32c44abeba421d69a5ae21a
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302348"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Problèmes Endpoint Protection et solutions possibles dans Microsoft Intune

Cet article répertorie les causes et solutions possibles pour quelques erreurs et avertissements. Utilisez les informations pour vous aider à résoudre les problèmes liés à la protection des points de terminaison.

## <a name="windows-defender-error-codes"></a>Codes d’erreur Windows Defender

Passez en revue les journaux des événements et les codes d’erreur pour [résoudre les problèmes avec Windows Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Erreurs courantes liées à Intune et solutions possibles

### <a name="endpoint-protection-engine-unavailable"></a>Moteur Endpoint Protection indisponible

**Cause potentielle** : Le moteur Intune Endpoint Protection est endommagé ou a été supprimé.

**Solutions possibles** :

- Si Endpoint Protection est endommagé ou ne se met pas à jour, alors mettez à jour ou réinstallez le programme.
- Forcez une mise à jour immédiate. Dans le programme client Endpoint Protection (éventuellement dans la barre des tâches), choisissez **Mettre à jour**.
- Dans le Panneau de configuration > Programmes, sélectionnez **Agent Microsoft Intune Endpoint Protection**. Désinstallez l’application.
- Lors de la prochaine synchronisation des mises à jour, le Gestionnaire de mise à jour de Microsoft Online Management détecte le programme manquant et le réinstalle au moment de l'installation planifiée.

### <a name="features-are-disabled"></a>Les fonctionnalités sont désactivées

Vous pouvez recevoir un message indiquant que certaines fonctionnalités sont désactivées. Ces messages peuvent se produire si Intune Endpoint Protection ou Windows Defender est désactivé par un administrateur à l’aide d’un profil de configuration. Ou bien, il est désactivé par un utilisateur final sur l’appareil. Messages possibles :

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Solutions possibles** : Activez ces fonctionnalités. Pour obtenir des instructions, consultez :

- [Ajouter des paramètres Endpoint Protection](endpoint-protection-configure.md)
- [Antivirus Windows Defender](device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [Utilisateurs finaux : activer la protection en temps réel pour accéder aux ressources d’entreprise](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>Définitions de programmes malveillants obsolètes

Cet état s’affiche lorsque les définitions de programmes malveillants sur l’appareil sont obsolètes depuis au moins 14 jours. Par exemple, le message peut s’afficher si l’appareil est déconnecté d’Internet ou si les définitions de programmes malveillants sont obsolètes.

**Solutions possibles** : Si les définitions de programmes malveillants sont obsolètes, mettez-les à jour avec [Antivirus Windows Defender](device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>Analyse complète en retard ou analyse rapide en retard

Une analyse complète ou une analyse rapide n’a pas été effectuée depuis 14 jours. Ce scénario peut se produire si l’appareil redémarre lors d’une analyse complète.

**Solutions possibles** : Si une analyse complète est en retard, vous pouvez exécuter une analyse une fois ou planifier des analyses régulières. Consultez [Antivirus Windows Defender](device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="another-endpoint-protection-application-running"></a>Une autre application de protection de point de terminaison est en cours d'exécution

Une autre application de protection de point de terminaison est en cours d’exécution et l’appareil est intègre.

**Solutions possibles** : Si une autre application de protection de point de terminaison est installée est qu’elle est détectée par Intune, l’appareil peut devenir instable.

## <a name="next-steps"></a>Étapes suivantes

Obtenir [l’aide de Microsoft](get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
