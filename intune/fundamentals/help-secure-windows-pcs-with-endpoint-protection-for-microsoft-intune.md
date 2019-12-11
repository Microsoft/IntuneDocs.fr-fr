---
title: Protection de point de terminaison pour PC Windows
titleSuffix: Microsoft Intune
description: Sécurisez vos ordinateurs gérés avec Endpoint Protection, qui fournit une protection en temps réel contre les menaces de logiciels malveillants.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/12/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: f00a680d8d7799e0307021926677d1e0ed1e9a12
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059681"
---
# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>Contribuer à la sécurisation des PC Windows avec Endpoint Protection pour Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Le service Endpoint Protection de Microsoft Intune vous aide à sécuriser vos ordinateurs gérés. Il offre une protection en temps réel contre les menaces posées par les programmes malveillants, maintient à jour les définitions de logiciels malveillants et analyse automatiquement les ordinateurs. Endpoint Protection fournit également des outils qui vous aident à gérer et à surveiller les attaques de logiciels malveillants.

Si vous n’avez pas encore installé le client Intune sur vos ordinateurs, consultez [Installer le client de PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Utilisez les informations des sections suivantes pour configurer, déployer et surveiller Endpoint Protection.

## <a name="choose-when-to-use-endpoint-protection"></a>Choisir quand utiliser Endpoint Protection
En tant qu’administrateur informatique, l’une de vos principales priorités est de maintenir les ordinateurs que vous gérez exempts de programmes malveillants et virus. Avant de déployer Intune sur les PC Windows de votre organisation, vous devez déterminer comment protéger les ordinateurs en sélectionnant l’une des options suivantes et en configurant ses paramètres de stratégie associée :


|                                                                                                                                                                       Vous souhaitez :                                                                                                                                                                        |                                                                                                       Paramètres de stratégie Endpoint Protection                                                                                                        |                                                                                                                                                  Plus d’informations                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                             Utiliser Microsoft Intune Endpoint Protection uniquement si aucune application tierce de protection de point de terminaison n’est installée.<br /><br />Vous pouvez utiliser Microsoft Intune Endpoint Protection sur tous les ordinateurs sur lesquels aucune application tierce de protection de point de terminaison n’est installée.                                              | Installer Endpoint Protection = <strong>Oui</strong><br /><br />Activer Endpoint Protection = <strong>Oui</strong><br /><br />Installer Endpoint Protection même si une application tierce de protection de point de terminaison est installée = <strong>Non</strong>  |                                                                      Si une application tierce de protection de point de terminaison est détectée, Microsoft Intune Endpoint Protection n’est pas installé, et il est désinstallé s’il était déjà installé.                                                                       |
| Utiliser Microsoft Intune Endpoint Protection même si une application tierce de protection de point de terminaison est installée.<br /><br />Avec cette approche, vous allez exécuter simultanément Microsoft Intune Endpoint Protection et l’application tierce de protection de point de terminaison. Cette configuration n’est pas recommandée, car elle peut entraîner des problèmes de performances potentiels. | Installer Endpoint Protection = <strong>Oui</strong><br /><br />Activer Endpoint Protection = <strong>Oui</strong><br /><br />Installer Endpoint Protection même si une application tierce de protection de point de terminaison est installée = <strong>Oui</strong> |                        Contexte d'utilisation :<br /><br />-   Vous souhaitez passer à l’utilisation de Microsoft Intune Endpoint Protection.<br />-   Vous déployez un nouveau client qui utilise Microsoft Intune Endpoint Protection.<br />-   Vous mettez à niveau un client qui utilise Microsoft Intune Endpoint Protection.                         |
|                                                                                                             Utiliser Intune sans Microsoft Intune Endpoint Protection. À la place, vous devrez vous fier à une application tierce de protection de point de terminaison.                                                                                                             |                                                                                                Installer Endpoint Protection = <strong>Non</strong>                                                                                                 | Si vous n’utilisez aucune application tierce de protection de point de terminaison, cette configuration n’est pas recommandée, car elle peut exposer les ordinateurs de votre organisation aux attaques de programmes malveillants ou d’autre nature.<br /><br />Microsoft Intune Endpoint Protection n’est pas installé, et il est désinstallé s’il était déjà installé. |

Pour passer de votre application de protection de point de terminaison actuelle à Microsoft Intune Endpoint Protection, procédez comme suit :

1. Continuez d’exécuter votre application de protection de point de terminaison actuelle lors du déploiement du logiciel client Intune vers ces ordinateurs.

2. Vérifiez que Microsoft Intune Endpoint Protection est installé et contribue à sécuriser les ordinateurs clients.

3. Supprimez le logiciel tiers de protection de point de terminaison en procédant comme suit :

    - Utilisez la fonction de distribution de logiciels Intune pour déployer un outil de suppression de logiciels fourni par le fabricant de l’application tierce de protection de point de terminaison. Pour plus d’informations, consultez [Déployer des applications avec Microsoft Intune](../apps/apps-deploy.md).

    - Supprimez manuellement l'application tierce de protection de point de terminaison.

> [!NOTE]
> Intune ne désinstalle pas automatiquement les applications tierces de protection de point de terminaison.

## <a name="configure-microsoft-intune-endpoint-protection"></a>Configurer Microsoft Intune Endpoint Protection
Procédez comme suit pour configurer Endpoint Protection pour Microsoft Intune.

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Stratégie** > **Ajouter une stratégie**.

2. Développez **Gestion des ordinateurs** et sélectionnez **Paramètres de l’Agent Microsoft Intune**. Sélectionnez **Créer et déployer une stratégie personnalisée** pour spécifier la stratégie des paramètres Endpoint Protection. Choisissez ensuite le bouton **Créer une stratégie**.

Vous pouvez utiliser les paramètres recommandés ou personnaliser les paramètres. Pour plus d’informations sur la création et le déploiement des stratégies, consultez la rubrique [Tâches courantes de gestion des PC Windows avec le client Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Paramètres Endpoint Protection](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-pc-endpoint-policy.png)

Vous pouvez afficher la stratégie Endpoint Protection déployée dans la page **Toutes les stratégies** de l’espace de travail **Stratégie**.

## <a name="specify-endpoint-protection-service-settings"></a>Spécifier les paramètres du service Endpoint Protection

|                                                 Paramètre de stratégie                                                  |                                                                                                                                                                                                                                                                                                                                                                                                             Détails                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                  <strong>Installer Endpoint Protection</strong>                                   | Attribuez la valeur <strong>Oui</strong> pour installer Endpoint Protection sur des ordinateurs gérés. Si une application de protection de point de terminaison tierce est détectée pendant l’installation, Endpoint Protection n’est pas installé, sauf si le paramètre <strong>Installer Endpoint Protection même si une application tierce de protection de point de terminaison est installée</strong> est défini sur <strong>Oui</strong>. <strong>Remarque :</strong> Intune Endpoint Protection est installé par défaut sur les ordinateurs gérés. Si vous ne souhaitez pas installer Endpoint Protection sur vos ordinateurs gérés, vous devez affecter explicitement à cette stratégie la valeur <strong>Non</strong>. Si Endpoint Protection a déjà été installé et que la stratégie est mise à jour sur <strong>Non</strong>, le client Endpoint Protection est désinstallé.<br />Valeur recommandée : <strong>Oui</strong> |
| <strong>Installer Endpoint Protection même si une application tierce de protection du point de terminaison est installée</strong> |                                                                                                                                                                                                                                                                                                                Attribuez la valeur <strong>Oui</strong> pour installer Microsoft Intune Endpoint Protection même si une application tierce de protection de point de terminaison est détectée.<br /><br />Valeur recommandée : <strong>Oui</strong>                                                                                                                                                                                                                                                                                                                |
|                                   <strong>Activer Endpoint Protection</strong>                                   |                                                                                                                                                                                                            Attribuez la valeur <strong>Oui</strong> pour activer Microsoft Intune Endpoint Protection sur les ordinateurs avec le client Endpoint Protection.<br /><br />Si la valeur est <strong>Non</strong> et que Microsoft Intune Endpoint Protection est installé, l’interface utilisateur du client Endpoint Protection n’est pas accessible aux utilisateurs et toutes les fonctions de protection sont inactives.<br /><br />Valeur recommandée : <strong>Oui</strong>                                                                                                                                                                                                             |
|                                       <strong>Désactiver l’interface utilisateur du client</strong>                                        |                                                                                                                                                                                                                                                                                                      Attribuez la valeur <strong>Oui</strong> pour masquer l’interface utilisateur du client Microsoft Intune Endpoint Protection aux utilisateurs (nécessite le redémarrage de l’ordinateur client pour entrer en vigueur).<br /><br />Valeur recommandée : <strong>Non</strong>                                                                                                                                                                                                                                                                                                       |
| <strong>Installer Endpoint Protection même si une application tierce de protection du point de terminaison est installée</strong> |                                                                                                                                                                                                                                                                                                       Attribuez la valeur <strong>Oui</strong> pour forcer l’installation de Microsoft Intune Endpoint Protection, même si une application tierce de protection de point de terminaison est détectée.<br /><br />Valeur recommandée : <strong>Non</strong>                                                                                                                                                                                                                                                                                                       |
|                    <strong>Créer un point de restauration système avant de remédier au(x) programme(s) malveillant(s)</strong>                    |                                                                                                                                                                                                                                                                                                                                 Attribuez la valeur <strong>Oui</strong> pour créer un point de restauration du système Windows avant de démarrer une correction de programmes malveillants.<br /><br />Valeur recommandée : <strong>Oui</strong>                                                                                                                                                                                                                                                                                                                                  |
|                                 <strong>Assurer le suivi des programmes malveillants résolus (jours)</strong>                                  |                                                                                                                                                                                                                                                                                      Permet à Endpoint Protection de suivre les programmes malveillants dont le cas a été résolu pendant une période donnée pour que vous puissiez vérifier manuellement les ordinateurs précédemment infectés.<br /><br />Vous pouvez spécifier une valeur comprise entre 0 et 30 jours.<br /><br />Valeur recommandée : <strong>7 jours</strong>                                                                                                                                                                                                                                                                                       |

Si vous avez attribué la valeur **Oui** aux paramètres de stratégie **Installer Endpoint Protection** et **Activer Endpoint Protection**, et la valeur **Non** au paramètre de stratégie **Installer Endpoint Protection même si une application tierce de protection de point de terminaison est installée**, Microsoft Intune Endpoint Protection détecte qu’une autre application de point de terminaison est installée. Cela signifie que Endpoint Protection ne sera pas installé, ou qu’il sera désinstallé s’il est déjà présent. Toutefois, Microsoft Intune Endpoint Protection n’établit pas de rapport sur l’intégrité de l’autre application de protection de point de terminaison dans Intune.

  Microsoft Security Essentials vous avertit avec la protection en temps réel quand des menaces telles que des virus et des logiciels espions tentent de s’installer ou de s’exécuter sur votre PC. Au moment où cela se produit, un message s’affiche dans la zone de notification à droite de la barre des tâches.

### <a name="specify-real-time-protection-settings"></a>Spécifier les paramètres de la protection en temps réel

|Paramètre de stratégie|Détails|
|------------------|--------------------|
|**Activer la protection en temps réel**|Permet de surveiller et d'analyser tous les fichiers et toutes les applications accessibles. Il bloque également tous les fichiers et applications malveillants avant qu'ils ne s'exécutent sur des ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Analyser tous les téléchargements**|Permet d'analyser tous les fichiers et toutes les pièces jointes qui sont téléchargés à partir d'Internet sur les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Analyser l’activité des fichiers et des programmes sur les ordinateurs**|Permet d’analyser les fichiers entrants et sortants, ainsi que l’activité des programmes sur les ordinateurs. Grâce à ce paramètre, Endpoint Protection peut contrôler le moment où des fichiers et des programmes commencent à s’exécuter, et vous alerter s’ils effectuent des opérations ou si certaines opérations sont effectuées sur ceux-ci.<br /><br />Valeur recommandée : **Oui**|
|**Fichiers surveillés**|Vous permet de choisir si seuls les fichiers entrants ou sortants, ou tous les fichiers, doivent être analysés.<br /><br />Valeur recommandée : **Contrôler tous les fichiers**|
|**Activer l'analyse du comportement**|Permet à Microsoft Intune Endpoint Protection de rechercher certains schémas d’activité suspecte sur les ordinateurs clients.<br /><br />Valeur recommandée : **Oui**|
|**Activer le système NIS (Network Inspection System)**|Active le Système NIS (Network Inspection System) sur les ordinateurs clients. Le système NIS utilise des signatures de vulnérabilités connues disponibles auprès du [Centre de protection Microsoft contre les programmes malveillants](https://go.microsoft.com/fwlink/?LinkId=234249) pour faciliter la détection et le blocage du trafic réseau malveillant.<br /><br />Valeur recommandée : **Oui**|

  ![Paramètres en temps réel pour Endpoint Protection](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>Spécifier les paramètres de la planification d’analyse

|Paramètre de stratégie|Plus d’informations|
|------------------|--------------------|
|**Planifier une analyse quotidienne rapide**|Permet de planifier une analyse quotidienne rapide des fichiers fréquemment utilisés et des fichiers système importants sur les ordinateurs. Cette analyse rapide n'a qu'une incidence minime sur les performances.<br /><br />Valeur recommandée : **Oui**|
|**Lancer une analyse rapide à l’issue de deux analyses rapides consécutives non effectuées**|Configure Endpoint Protection pour exécuter automatiquement une analyse rapide sur les ordinateurs sur lesquels deux analyses rapides consécutives n’ont pas été effectuées.<br /><br />Valeur recommandée : **Oui**|
|**Planifier une analyse complète**|Configure une analyse complète de l’ensemble des fichiers et des ressources sur les disques durs locaux des ordinateurs. Cette analyse peut prendre du temps et peut avoir une incidence sur les performances des ordinateurs (la durée de l’analyse dépend du nombre de fichiers et de ressources à analyser).<br /><br />Valeur recommandée : **Non**|
|**Lancer une analyse complète à l’issue de deux analyses complètes consécutives non effectuées**|Configure Endpoint Protection pour exécuter automatiquement une analyse complète sur les ordinateurs sur lesquels deux analyses complètes consécutives n’ont pas été effectuées.<br /><br />Valeur recommandée : non configuré|

### <a name="specify-scan-options-settings"></a>Spécifier les paramètres des options d’analyse

|Paramètre de stratégie|Détails|
|------------------|--------------------|
|**Exécuter une analyse complète après l’installation d’Endpoint Protection**|Attribuez la valeur **Oui** pour permettre à Endpoint Protection d’exécuter automatiquement une analyse complète du système après son installation sur les ordinateurs. Cette analyse ne s'effectue que lorsque les ordinateurs sont inactifs afin de minimiser son impact sur la productivité de l'utilisateur.<br /><br />Valeur recommandée : **Oui**|
|**Exécuter automatiquement une analyse complète lorsque cela est nécessaire pour suivre l’élimination de programmes malveillants**|Attribuez la valeur **Oui** pour permettre à Endpoint Protection d’exécuter automatiquement une analyse complète du système sur les ordinateurs après l’élimination de programmes malveillants pour confirmer que d’autres fichiers n’étaient pas affectés.<br /><br />Valeur recommandée : **Oui**|
|**Lancer une analyse planifiée uniquement lorsque l’ordinateur est en état d’attente**|Attribuez la valeur **Oui** pour empêcher le démarrage d'analyses planifiées lorsque des ordinateurs sont en activité afin d'éviter toute perte de productivité pour les utilisateurs.<br /><br />Valeur recommandée : **Oui**|
|**Rechercher les dernières définitions de programmes malveillants avant de lancer une analyse**|Attribuez la valeur **Oui** pour permettre à Endpoint Protection de rechercher automatiquement les récentes définitions de programmes malveillants avant de lancer une analyse sur les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Analyser les fichiers d’archive**|Attribuez la valeur **Oui** pour configurer Endpoint Protection de sorte qu’il recherche des programmes malveillants dans les fichiers d’archive (fichiers .zip ou .cab) stockés sur les ordinateurs.<br /><br />Valeur recommandée : **Non**|
|**Analyser les messages électroniques**|Attribuez la valeur **Oui** pour configurer Endpoint Protection de sorte qu’il analyse le courrier électronique entrant quand celui-ci arrive sur les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Analyser les fichiers ouverts à partir de dossiers partagés sur le réseau**|Attribuez la valeur **Oui** pour configurer Endpoint Protection de sorte qu’il analyse les fichiers ouverts à partir de dossiers partagés sur le réseau. Il s’agit généralement de fichiers accessibles à l’aide d’un chemin UNC (Universal Naming Convention). L'activation de cette fonctionnalité peut engendrer des problèmes pour les utilisateurs disposant d'un accès en lecture seule, car ils ne sont pas en mesure de supprimer les programmes malveillants.<br /><br />Valeur recommandée : **Non**|
|**Analyser les lecteurs réseau mappés**|Attribuez la valeur **Oui** pour configurer Endpoint Protection de sorte qu’il analyse les fichiers sur les lecteurs réseau mappés. L'activation de cette fonctionnalité peut engendrer des problèmes pour les utilisateurs disposant d'un accès en lecture seule, car ils ne sont pas en mesure de supprimer les programmes malveillants.<br /><br />Valeur recommandée : **Non**|
|**Analyser les lecteurs amovibles**|Attribuez la valeur **Oui** pour configurer Endpoint Protection de sorte qu’il recherche des programmes malveillants et indésirables sur les lecteurs amovibles, comme les disques mémoire flash USB, lors d’une analyse complète sur les ordinateurs.<br /><br />Valeur recommandée : **Oui**|
|**Limiter l’utilisation du processeur pendant une analyse**|Définissez le pourcentage maximal d’utilisation du processeur pendant les analyses planifiées sur les ordinateurs. Vous pouvez définir cette valeur entre 1 et 100 %.<br /><br />Valeur recommandée : **50 %**|

### <a name="choose-default-actions-settings"></a>Choisir les paramètres des actions par défaut

Le paramètre **Choisir comment Endpoint Protection agit sur les logiciels malveillants pour les niveaux d’alerte suivants** spécifie l’action par défaut effectuée par Endpoint Protection quand des programmes malveillants de différents niveaux d’alerte sont détectés. Pour chaque niveau d'alerte, vous pouvez supprimer le logiciel malveillant, le mettre en quarantaine ou effectuer l'action recommandée par Microsoft.

Valeur recommandée : **Action recommandée**, qui permet à Endpoint Protection de conseiller une action.   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>Décider s’il faut choisir les paramètres de fichiers et dossiers exclus

Le paramètre **Fichiers et dossiers à exclure lors de l’exécution d’une analyse ou de l’utilisation de la protection en temps réel** exclut les fichiers ou dossiers spécifiques lors de l’exécution d’une analyse ou quand la protection en temps réel est utilisée sur les ordinateurs.

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>Décider s’il faut choisir les paramètres de processus exclus

Le paramètre **Processus à exclure pendant l’exécution d’une analyse ou l’utilisation de la protection en temps réel** vous permet d’exclure certains processus lors de l’exécution d’une analyse ou quand la protection en temps réel est utilisée sur les ordinateurs. Vous pouvez exclure uniquement les fichiers avec les extensions suivantes : **.exe**, **.com** ou **.scr**.

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>Décider s’il faut choisir les paramètres de types de fichiers exclus

Le paramètre **Extensions de fichier à exclure pendant l’exécution d’une analyse ou l’utilisation de la protection en temps réel** vous permet d’exclure certaines extensions de noms de fichiers lors de l’exécution d’une analyse ou quand la protection en temps réel est utilisée sur les ordinateurs.

### <a name="specify-microsoft-active-protection-service-settings"></a>Spécifier les paramètres de Microsoft Active Protection Service
Microsoft Active Protection Service est une communauté en ligne qui vous aide à décider comment répondre aux menaces potentielles. En outre, la communauté aide à arrêter la propagation de nouvelles infections par des programmes malveillants. Vous pouvez **rejoindre Microsoft Active Protection Service** en sélectionnant **Oui** et en spécifiant votre **niveau d’adhésion** :
- **De base** : envoie des informations de base à Microsoft sur les logiciels malveillants détectés. Ces informations sont les suivantes : origine des logiciels détectés, actions appliquées par vous-même ou appliquées automatiquement par Endpoint Protection, indication de la réussite éventuelle de ces actions.
- **Options avancées** : envoie plus d’informations à Microsoft sur les programmes malveillants, les logiciels espions et les logiciels potentiellement indésirables. Ces informations sont les suivantes : emplacement des logiciels détectés, noms de fichier, mode de fonctionnement des logiciels détectés et indication de leur impact sur votre ordinateur.

Vous pouvez également **Recevoir des définitions dynamiques basées sur les rapports Microsoft Active Protection Service**.

## <a name="choose-management-tasks-for-endpoint-protection"></a>Choisir les tâches de gestion pour Endpoint Protection
Les tâches suivantes vous aident à effectuer différentes tâches de gestion sur les ordinateurs gérés qui exécutent Endpoint Protection :
- Mettre à jour les définitions de programmes malveillants
  - Console Intune : dans l’espace de travail **Groupes**, sélectionnez les ordinateurs que vous souhaitez mettre à jour. Choisissez **Tâches à distance** &gt; **Mettre à jour les définitions de programmes malveillants**.
  - Ordinateur géré : démarrez le logiciel client Endpoint Protection à partir de la zone de notification Windows. Choisissez l’onglet **Mise à jour**, puis choisissez **Mettre à jour**.
- Effectuer une analyse des programmes malveillants :
  - Console Intune : dans l’espace de travail **Groupes**, sélectionnez les ordinateurs que vous souhaitez analyser. Choisissez **Effectuer une analyse complète des programmes malveillants** ou **Effectuer une analyse rapide des programmes malveillants**.
  - Ordinateur géré : démarrez le logiciel client Endpoint Protection à partir de la zone de notification Windows. Choisissez **Rapide**, **Complète** ou **Personnalisée**, puis choisissez **Analyser maintenant**.

Vous pouvez afficher l’état d’une tâche à distance en choisissant le lien **Tâches à distance** dans le coin inférieur droit de la console Intune. La boîte de dialogue **État de tâche à distance** affiche les tâches à distance actuelles, l’état de chaque tâche, le nom de l’appareil et les erreurs signalées. Elle fournit également un lien vers des informations sur la correction des erreurs, le cas échéant.

## <a name="monitor-endpoint-protection"></a>Surveiller Endpoint Protection
Vous pouvez contrôler l'état des logiciels malveillants sur vos ordinateurs en utilisant l'espace de travail **Protection** de la [console d'administration Microsoft Intune](https://manage.microsoft.com/). Cet espace de travail comporte deux pages :
- **Vue d’ensemble de la protection** : affiche les problèmes importants sous forme de liens qui vous permettent d’obtenir plus d’informations. Les problèmes pouvant être affichés sont les suivants :
  - **Instances de programme malveillant nécessitant un suivi** : cliquez sur ce lien pour afficher une liste des problèmes relatifs à des logiciels malveillants, ainsi que les mesures à prendre pour résoudre le problème. Vous pouvez explorer cette liste pour voir quels ordinateurs sont concernés.
  - **Ordinateurs avec programme malveillant nécessitant un suivi** : cliquez sur ce lien pour afficher tous les ordinateurs ayant des problèmes non résolus relatifs à des logiciels malveillants, ainsi que les mesures à prendre pour résoudre le problème.
  - **Appareils non protégés** : cliquez sur ce lien pour afficher les ordinateurs qui ne sont pas protégés par un logiciel de protection de point de terminaison parce qu’aucun logiciel n’est installé ou en raison d’une erreur. Sélectionnez un ordinateur pour afficher plus de détails.
  - **Appareils avec une autre application Endpoint Protection en cours d’exécution** : cliquez sur le lien pour afficher les ordinateurs qui exécutent une application tierce de protection de point de terminaison.
- **Tous les programmes malveillants** : affiche une liste de tous les programmes malveillants actifs ayant été trouvés sur vos ordinateurs. Vous pouvez explorer cette liste pour voir tous les ordinateurs affectés par un programme malveillant spécifique, ou vous pouvez sélectionner l’une des tâches suivantes :
  - **Afficher les propriétés** : ouvre une page qui contient plus d’informations sur le programme malveillant sélectionné.
  - **En savoir plus sur ce programme malveillant** : ouvre une rubrique du Centre de protection Microsoft contre les programmes malveillants qui contient plus d’informations sur le logiciel malveillant.

> [!IMPORTANT]
> L’espace de travail **Protection** n’est pas affiché dans la console d’administration tant que vous n’avez pas installé le client et que vous ne gérez pas au moins un ordinateur client.

  ![Surveiller Endpoint Protection](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>Comment afficher les chemins d'accès de détection récents pour les programmes malveillants sur des ordinateurs
Intune peut afficher au maximum les chemins des 10 dernières instances de programme malveillant détectées sur un appareil. L'option **Chemins d'accès de détection récents** est désactivée par défaut. Pour activer cet affichage :

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Groupes** > **Tous les appareils** > **Tous les ordinateurs**.
2. Cliquez avec le bouton droit sur l’ordinateur dont vous souhaitez visualiser les chemins d’accès de détection récents, puis sélectionnez **Propriétés**.
3. Sélectionnez **Programme malveillant** parmi les onglets situés dans la partie supérieure.

   ![Sélection de l’onglet Programme malveillant, puis clic sur la case à cocher Chemins d’accès de détection récents](./media/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune/malware-path-column.png)
4. Cliquez avec le bouton droit sur l’en-tête de colonne. Une liste des colonnes disponibles s'affiche. Cochez la case **Chemins d’accès de détection récents** dans la liste. La colonne **Chemins d’accès de détection récents** apparaît et affiche au maximum les 10 dernières instances de programme malveillant surveillées sur l’appareil.

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>Effectuer une analyse des programmes malveillants ou mettre à jour les définitions de programmes malveillants sur un ordinateur
Intune peut effectuer une analyse complète ou rapide des programmes malveillants en utilisant Endpoint Protection ou Microsoft Defender sur un PC géré à distance où le client Intune est installé.

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), accédez à **Groupes** > **Présentation** > **Tous les appareils** > **Tous les ordinateurs**, puis sélectionnez l’ordinateur que vous souhaitez cibler.

2. Choisissez la liste déroulante **Tâches à distance**, puis sélectionnez la tâche à exécuter sur l’ordinateur distant.

## <a name="need-more-help"></a>Besoin d'aide ?
Pour obtenir de l’aide et une assistance, consultez [Résoudre les problèmes liés à Endpoint Protection dans Microsoft Intune](troubleshoot-endpoint-protection-in-microsoft-intune.md).

## <a name="see-also"></a>Voir aussi
[Stratégies pour protéger les PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
