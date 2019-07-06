---
title: Mettre hors service un PC Windows
titleSuffix: Microsoft Intune
description: Comment mettre hors service un PC Windows géré par Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b6326d30650aa62777ac9ce9c70394904b678f3
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549157"
---
# <a name="retire-a-windows-pc"></a>Mettre hors service un PC Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Procédez comme suit pour mettre hors service les ordinateurs de bureau que vous gérez comme PC en y exécutant le client logiciel Intune. Lorsque vous mettez un PC hors service, celui-ci est supprimé de la gestion Intune. Vous ne pouvez pas mettre hors service un PC depuis Intune pour le rétablir à ses paramètres d’usine.

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Groupes** &gt; **Tous les appareils** (ou un autre groupe qui contient l’ordinateur que vous voulez mettre hors service).

2. Sélectionnez les appareils que vous souhaitez mettre hors service, puis choisissez **Mettre hors service/Réinitialiser**.

Pour réinscrire un ordinateur dans Intune, réinstallez le client logiciel sur le PC en suivant les instructions données dans [Installer le client de PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Si un ordinateur ne peut pas se connecter à Intune, un message s’affiche dans l’espace de travail **Tableau de bord**.

Lorsque vous mettez hors service un ordinateur :

- Il est supprimé de la gestion et de l’inventaire Intune, et la licence associée à l’ordinateur devient disponible pour une réutilisation. La mise hors service et la réinitialisation ont pour effet de supprimer le logiciel client Intune, mais elles ne suppriment pas les données et les applications de l’ordinateur. Cette mise hors service n’effectue pas une réinitialisation complète sur l’ordinateur.

- Son état ne s’affiche plus dans la console Intune.

- Intune supprime le client logiciel de l’ordinateur. Si l’ordinateur n’est pas connecté au service Intune, le client logiciel est supprimé à la prochaine connexion.

- Microsoft Intune Endpoint Protection est supprimé de l’ordinateur. Si l’ordinateur dispose d’une autre application de point de terminaison installée et qu’elle est désactivée, cette application peut être réactivée après la suppression de Microsoft Intune Endpoint Protection pour garantir la protection de vos ordinateurs.

- Toutes les stratégies sont supprimées de l'ordinateur et les valeurs qui ont été définies par les stratégies vont être modifiées.

- L’ordinateur ne reçoit plus les mises à jour de logiciels ou les mises à jour de définition des programmes malveillants à partir du service Intune.

- Selon la façon dont ils sont configurés, les ordinateurs mis hors service peuvent continuer à recevoir des mises à jour à l'aide de Windows Server Update Services, Windows Update ou Microsoft Update.

    > [!IMPORTANT]
    > Si le logiciel client a été installé à l'aide d'un objet de stratégie de groupe, vous devez supprimer celui-ci pour pouvoir supprimer le logiciel client afin d'empêcher la réinstallation du logiciel.

    Si la désinstallation du client Endpoint Protection échoue, lisez [Résoudre les problèmes de protection de point de terminaison](/intune/troubleshoot-endpoint-protection-in-microsoft-intune) pour obtenir une aide supplémentaire.

### <a name="see-also"></a>Voir aussi

[Tâches courantes de gestion des PC Windows avec le client logiciel Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
