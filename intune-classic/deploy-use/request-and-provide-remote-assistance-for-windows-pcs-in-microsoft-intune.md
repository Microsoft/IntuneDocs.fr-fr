---
title: Demander et fournir une assistance à distance pour les PC Windows
description: Décrit les étapes de l’utilisateur final et de l’administrateur informatique permettant de fournir une assistance à distance pour les bureaux Windows gérés et de démarrer un PC à distance.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 245d18b89be9b9884df6c7ee41436e747c0557fe
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31019736"
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Demander et fournir une assistance à distance pour les PC Windows

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Les informations de cette rubrique s’appliquent uniquement aux bureaux Windows que vous gérez en tant que PC à l’aide du client logiciel Intune.

Intune peut utiliser le logiciel [TeamViewer](https://www.teamviewer.com), acheté séparément, pour vous permettre de fournir une assistance à distance aux utilisateurs qui exécutent le client logiciel Intune. Lorsqu’un utilisateur demande de l’aide à partir de Microsoft Intune Center, vous êtes informé par une alerte, vous pouvez accepter la demande, puis fournir une assistance. Cette fonctionnalité remplace la fonctionnalité Assistance à distance Windows existante dans Intune.


## <a name="before-you-start"></a>Avant de commencer

Avant de pouvoir établir des demandes d’assistance à distance et d’y répondre, vérifiez que les conditions préalables suivantes sont respectées :

- Vous devez vous être [inscrit pour obtenir un compte TeamViewer](https://login.teamviewer.com/LogOn#register) permettant de vous connecter au site web TeamViewer.
- Les PC Windows que vous souhaitez administrer doivent être [gérés par le client logiciel Windows](manage-windows-pcs-with-microsoft-intune.md)
- Tous les systèmes d’exploitation des PC Windows pris en charge par Intune peuvent être administrés.

## <a name="configure-the-teamviewer-connector"></a>Configurer le connecteur TeamViewer

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **Administration**
2. Dans l’espace de travail **Administration**, choisissez **TeamViewer**.
3. Sur la page **TeamViewer**, sous **Connecteur TeamViewer**, choisissez **Activer**.
4. Dans la boîte de dialogue **Activer TeamViewer**, consultez les termes du contrat de licence, puis choisissez **Accepter**. Si vous n’avez pas encore de licence TeamViewer, choisissez **Acheter une licence TeamViewer**.
5. Après l’ouverture de la fenêtre du navigateur TeamViewer, connectez-vous au site avec vos informations d’identification TeamViewer.
6. Sur le site TeamViewer, lisez et acceptez les options pour permettre à Intune de se connecter avec TeamViewer.
7. Dans la console Intune, vérifiez que l’élément **Connecteur TeamViewer** apparaît comme **Activé**.


## <a name="open-a-remote-assistance-request-end-user"></a>Ouvrir une demande d’assistance à distance (utilisateur final)

1. Sur un PC Windows client, ouvrez **Microsoft Intune Center**.
2. Sous **Assistance à distance**, choisissez **Demander une assistance à distance**.
3. Une fois que vous avez approuvé la demande (voir ci-dessous), TeamViewer s’ouvre sur le client. L’utilisateur doit accepter les messages indiquant que le navigateur web tente d’ouvrir l’application TeamViewer.
4. L’utilisateur voit un message lui demandant si vous pouvez contrôler son PC. Il doit accepter ce message pour continuer.
5. Au cours de la session d’assistance à distance, l’utilisateur voit une fenêtre lui indiquant que vous êtes connecté. S’il ferme cette fenêtre, la session à distance se termine.

## <a name="respond-to-a-remote-assistance-request"></a>Répondre à une demande d’assistance à distance

1. Lorsqu’un utilisateur soumet une demande d’assistance à distance, vous pouvez l’afficher dans l’espace de travail **Alertes**, sous **Analyse** > **Assistance à distance**. Par exemple :
   > ![Capture d’écran d’une demande d’assistance à distance](./media/team-viewer.png)

<br>Si une demande reste sans réponse plus de 4 heures, elle est supprimée.
2. Pour accepter la demande, choisissez **Approuver une demande et lancer l’assistance à distance**.
3. Dans la boîte de dialogue **Une nouvelle demande d’assistance à distance est en attente**, choisissez **Accepter la demande d’assistance à distance**. Si elles ne sont pas déjà installées, TeamViewer installe les applications nécessaires sur votre ordinateur.
4. TeamViewer informe ensuite l’utilisateur final que vous souhaitez prendre le contrôle de son ordinateur. Une fois que l’utilisateur a accepté la demande, la fenêtre TeamViewer s’ouvre et vous pouvez contrôler le PC.

Au cours d’une session d’assistance à distance, vous pouvez utiliser toutes les commandes TeamViewer disponibles pour contrôler le PC distant. Pour obtenir de l’aide avec ces commandes, téléchargez le [Manuel pour le contrôle à distance](http://www.teamviewer.com/en/support/documents/) depuis le site web TeamViewer.

## <a name="close-the-remote-assistance-session"></a>Fermer la session d’assistance à distance

Dans le menu **Actions** de la fenêtre **TeamViewer**, choisissez **Fin de session**.

## <a name="remotely-restart-a-windows-pc"></a>Redémarrer à distance un PC Windows
Quand vous aidez les utilisateurs à résoudre leurs problèmes, vous pouvez être amené à redémarrer leur PC à distance de temps en temps. Procédez comme suit pour redémarrer un PC Windows à distance.

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Groupes** &gt; **Tous les appareils** (ou un autre groupe qui contient l’ordinateur que vous voulez redémarrer).

2.  Sélectionnez un ou plusieurs ordinateurs, puis choisissez **Tâches à distance** &gt; **Redémarrer l’ordinateur**.

3.  Pour afficher l’état des tâches, choisissez **Tâches à distance** dans le coin inférieur droit de la page.

4.  Dans la boîte de dialogue **État de tâche** , passez en revue les tâches à distance en cours, l'état de la tâche, le nom d'appareil et les erreurs signalées.

### <a name="see-also"></a>Voir aussi

[Tâches courantes de gestion des PC Windows avec le client logiciel Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)