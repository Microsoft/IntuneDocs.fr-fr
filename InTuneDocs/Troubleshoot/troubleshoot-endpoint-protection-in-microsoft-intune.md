---
# required metadata

title: Résoudre les problèmes liés à Endpoint Protection | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Troubleshoot Endpoint Protection in Microsoft Intune

Utilisez les informations indiquées dans cette section pour vous aider à résoudre les problèmes liés à l’utilisation de Microsoft Intune Endpoint Protection.

Si ces informations ne vous permettent pas de remédier à votre problème, consultez [Comment obtenir un support technique pour Microsoft Intune](how-to-get-support-for-microsoft-intune.md) pour accéder à d’autres types d’assistance.


### Messages d'erreur d'Endpoint Protection
Cette section décrit les causes et solutions possibles pour les erreurs et avertissements suivants, apparaissant dans le volet **État Endpoint Protection** de la [console d’administration Intune](https://manage.microsoft.com).

|Élément d'état|Causes possibles|Solutions possibles|
|---------------|--------------------|-----------------------|
|**Moteur Endpoint Protection indisponible**|Le moteur Intune Endpoint Protection est endommagé ou a été supprimé.|Si le moteur Intune Endpoint Protection est endommagé, vous pouvez tenter de mettre à jour ou de réinstaller le logiciel.<br /><br />Pour forcer une mise à jour immédiate, cliquez sur **Mettre à jour** dans le logiciel client Endpoint Protection (figurant dans la barre des tâches sur les ordinateurs gérés).<br /><br />Si le moteur ne peut pas être mis à jour, vous devez réinstaller le moteur Endpoint Protection.<br /><br />Dans la liste des programmes installés dans le Panneau de configuration sur l’ordinateur géré, recherchez **Agent de Microsoft Intune Endpoint Protection**, puis désinstallez l’application.<br /><br />Lors de la prochaine synchronisation des mises à jour, le Gestionnaire de mise à jour de Microsoft Online Management détecte le programme manquant et le réinstalle au moment de l'installation planifiée.|
|**Endpoint Protection désactivé**|Intune Endpoint Protection a été désactivé par un administrateur à l’aide d’une stratégie ou par un utilisateur sur un ordinateur géré.|Si Endpoint Protection est désactivé, vous pouvez l’activer à partir de la [console d’administration Intune](https://manage.microsoft.com) ou d’un ordinateur géré. Effectuez l'une des opérations suivantes :<br /><br />Pour activer Endpoint Protection à partir de la [console d’administration Intune](https://manage.microsoft.com), ouvrez l’espace de travail **Stratégie** et modifiez le paramètre **Activer Endpoint Protection** dans les stratégies qui s’appliquent à l’ordinateur.<br /><br />ou<br /><br />Pour activer Endpoint Protection à partir d’un ordinateur géré, démarrez le client Intune Endpoint Protection à partir de la zone de notification et vous serez invité à activer Endpoint Protection.|
|**Protection en temps réel désactivée**|La protection en temps réel a été désactivée par un administrateur (à l’aide d’une stratégie) ou par un utilisateur sur un ordinateur géré.|Si la protection en temps réel est désactivée, vous pouvez l’activer à partir de la [console d’administration Intune](https://manage.microsoft.com) ou d’un ordinateur géré. Effectuez l'une des opérations suivantes :<br /><br />Pour activer la protection en temps réel à partir de la [console d’administration Intune](https://manage.microsoft.com), ouvrez l’espace de travail **Stratégie** et redéfinissez le paramètre **Activer la protection en temps réel** sur **Oui** au niveau des stratégies qui s’appliquent à l’ordinateur.<br /><br />ou<br /><br />Pour activer la protection en temps réel à partir d’un ordinateur géré, démarrez le logiciel client Endpoint Protection à partir de la zone de notification. Vous êtes invité à activer la protection en temps réel à ce moment-là.|
|**Analyse des téléchargements désactivée**|L'analyse des téléchargements a été désactivée par un administrateur à l'aide d'une stratégie ou par un utilisateur sur un ordinateur géré.|Si l’analyse des téléchargements est désactivée, vous pouvez l’activer à partir de la [console d’administration Intune](https://manage.microsoft.com) ou d’un ordinateur géré. Effectuez l'une des opérations suivantes :<br /><br />Pour activer l’analyse des téléchargements à partir de la [console d’administration Intune](https://manage.microsoft.com), ouvrez l’espace de travail **Stratégie**, puis réglez le paramètre **Analyser tous les téléchargements** sur **Oui** dans les stratégies qui s’appliquent à l’ordinateur.<br /><br />ou<br /><br />Pour activer l’analyse des téléchargements à partir d’un ordinateur géré, démarrez le logiciel client Endpoint Protection à partir de la zone de notification. Cliquez sur l’onglet **Paramètres**, cliquez sur **Protection en temps réel**, cochez la case **Analyser tous les téléchargements**, puis cliquez sur **Enregistrer les modifications**.|
|**Analyse de l'activité des fichiers et des programmes désactivée**|L'analyse de l'activité des fichiers et des programmes a été désactivée par un administrateur qui a utilisé une stratégie ou par un utilisateur sur un ordinateur géré.|Si l’analyse de l’activité des fichiers et des programmes est désactivée, vous pouvez l’activer à partir de la [console d’administration Intune](https://manage.microsoft.com) ou à partir d’un ordinateur géré. Effectuez l'une des opérations suivantes :<br /><br />Pour activer l’analyse de l’activité des fichiers et des programmes à partir de la [console d’administration Intune](https://manage.microsoft.com), ouvrez l’espace de travail **Stratégie** et redéfinissez le paramètre **Surveiller l’activité des fichiers et des programmes installés sur les ordinateurs** sur **Oui** au niveau des stratégies qui s’appliquent à l’ordinateur.<br /><br />ou<br /><br />Pour activer l’analyse de l’activité des fichiers et des programmes à partir d’un ordinateur géré, démarrez le logiciel client Endpoint Protection à partir de la zone de notification. Cliquez sur l’onglet **Paramètres**, cliquez sur **Protection en temps réel**, cochez la case **Surveiller l’activité des fichiers et des programmes installés sur votre ordinateur**, puis cliquez sur **Enregistrer les modifications**.|
|**Analyse du comportement désactivée**|L’analyse du comportement a été désactivée par un administrateur (à l’aide d’une stratégie) ou par un utilisateur sur un ordinateur géré.|Si l’analyse du comportement est désactivée, vous pouvez l’activer à partir de la [console d’administration Intune](https://manage.microsoft.com) ou d’un ordinateur géré. Effectuez l'une des opérations suivantes :<br /><br />Pour activer l’analyse du comportement à partir de la [console d’administration Intune](https://manage.microsoft.com), ouvrez l’espace de travail **Stratégie**, réglez le paramètre **Activer l’analyse du comportement** sur **Oui** dans les stratégies qui s’appliquent à l’ordinateur, puis redémarrez l’ordinateur géré.<br /><br />ou<br /><br />Pour activer l’analyse du comportement à partir d’un ordinateur géré, démarrez le logiciel client Endpoint Protection à partir de la zone de notification. Cliquez sur l’onglet **Paramètres**, cliquez sur **Protection en temps réel**, sélectionnez la case **Activer l’analyse du comportement**, puis cliquez sur **Enregistrer les modifications**. Ensuite, redémarrez l'ordinateur.|
|**Analyse de scripts désactivée**|L’analyse de scripts a été désactivée par un administrateur (à l’aide d’une stratégie) ou par un utilisateur sur un ordinateur géré.|Si l’analyse de scripts est désactivée, vous pouvez l’activer à partir de la [console d’administration Intune](https://manage.microsoft.com) ou d’un ordinateur géré. Effectuez l'une des opérations suivantes :<br /><br />Pour activer l’analyse de scripts à partir de la [console d’administration Intune](https://manage.microsoft.com), ouvrez l’espace de travail **Stratégie**, puis réglez le paramètre **Activer l’analyse de scripts** sur **Oui** dans les stratégies qui s’appliquent à l’ordinateur.<br /><br />ou<br /><br />Pour activer l’analyse de scripts à partir d’un ordinateur géré, démarrez le logiciel client Endpoint Protection à partir de la zone de notification. Cliquez sur l’onglet **Paramètres**, cliquez sur **Protection en temps réel**, sélectionnez la case **Activer l’analyse de scripts**, puis cliquez sur **Enregistrer les modifications**..|
|**Système NIS (Network Inspection System) désactivé**|Le système NIS a été désactivé par un administrateur à l'aide d'une stratégie ou par un utilisateur sur un ordinateur géré.|Si le système NIS est désactivé, vous pouvez l’activer à partir de la [console d’administration Intune](https://manage.microsoft.com) ou d’un ordinateur géré. Effectuez l'une des opérations suivantes :<br /><br />Pour activer le système NIS à partir de la [console d’administration Intune](https://manage.microsoft.com), ouvrez l’espace de travail **Stratégie**, réglez le paramètre **Activer le système d’inspection du réseau** sur **Oui** dans les stratégies qui s’appliquent à l’ordinateur, puis redémarrez l’ordinateur géré.<br /><br />ou<br /><br />Pour activer le système NIS à partir d’un ordinateur géré, démarrez le logiciel client Endpoint Protection à partir de la zone de notification. Cliquez sur l’onglet **Paramètres**, cliquez sur **Protection en temps réel**, sélectionnez la case **Activer le système d’inspection du réseau**, puis cliquez sur **Enregistrer les modifications**. Redémarrez l'ordinateur.|
|**Définitions de programmes malveillants obsolètes**|Il se peut que l'ordinateur soit déconnecté d'Internet depuis un certain temps et que ses définitions de programmes malveillants n'aient pas encore été mises à jour. Cet état s’affiche lorsque les définitions de programmes malveillants sur l’ordinateur sont obsolètes depuis au moins 14 jours.|Si les définitions de programmes malveillants sont obsolètes, vous pouvez les mettre à jour à partir de la [console d’administration Intune](https://manage.microsoft.com) ou à partir de l’ordinateur géré.<br /><br />Pour plus d’informations, consultez la rubrique [Contribuer à la sécurisation des PC Windows avec Endpoint Protection pour Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**Analyse complète en retard**|Une analyse complète n'a pas été effectuée depuis 14 jours. Cela peut être dû à un redémarrage pendant une analyse complète.|Si une analyse complète est en retard, vous pouvez exécuter une analyse complète unique ou planifier des analyses complètes périodiques à partir de la [console d’administration Intune](https://manage.microsoft.com) en utilisant les informations dans la rubrique [Tâches courantes de gestion des PC Windows avec le client Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).|
|**Analyse rapide en retard**|Une analyse rapide n'a pas été effectuée depuis 14 jours. Cela peut résulter d'un redémarrage lors d'une analyse rapide.|Si une analyse rapide est en retard, vous pouvez exécuter une analyse rapide unique ou planifier des analyses rapides périodiques à partir de la [console d’administration Intune](https://manage.microsoft.com) en utilisant les informations dans la rubrique [Tâches courantes de gestion des PC Windows avec le client Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).|
|**Une autre application de protection de point de terminaison est en cours d'exécution**|Une autre application de protection de point de terminaison est en cours d'exécution et l'ordinateur est intègre.|Par défaut, si une autre application de protection de point de terminaison est installée et Intune détecte cette application, Endpoint Protection se désactive automatiquement. Si Intune ne détecte pas l’autre application, Endpoint Protection reste activé. Pour plus d’informations, consultez [Contribuer à la sécurisation des PC Windows avec Endpoint Protection pour Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|

### Étapes suivantes
Si ces informations de dépannage n’ont pas permis de vous aider, contactez le Support Microsoft comme décrit dans [Comment obtenir un support technique pour Microsoft Intune](how-to-get-support-for-microsoft-intune.md).


<!--HONumber=May16_HO1-->

