---
title: Mises à jour logicielles pour PC Windows
titleSuffix: Microsoft Intune
description: Intune vous aide à maintenir à jour vos ordinateurs gérés en vérifiant que les derniers correctifs et mises à jour logicielles sont rapidement installés.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68f8b814084328fdc5aed954cb71b9ce8dcedc63
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798949"
---
# <a name="keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune"></a>Maintenir des PC Windows à jour avec les mises à jour logicielles dans Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune peut vous aider à sécuriser vos ordinateurs gérés de plusieurs façons, notamment en gérant les mises à jour logicielles qui maintiennent votre ordinateur à jour et en garantissant une installation rapide des derniers correctifs et mises à jour logicielles.

Si vous n’avez pas encore installé le client Intune sur vos ordinateurs, consultez [Installer le client de PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Quand de nouvelles mises à jour sont disponibles via Microsoft Update ou que vous avez créé une mise à jour tierce, et que celles-ci sont applicables à vos ordinateurs gérés, une notification s’affiche dans la page **Vue d’ensemble** de l’espace de travail **Mises à jour**. Après avoir choisi le lien de cette notification, vous pouvez effectuer plusieurs opérations comme afficher des informations supplémentaires sur la mise à jour, approuver ou refuser la mise à jour et afficher les ordinateurs qui installeront la mise à jour si elle est approuvée.

> [!IMPORTANT]
> L'espace de travail **Mises à jour** n'est pas affiché dans la console d'administration tant que vous n'y avez pas installé le client et que vous n'y gérez pas au moins un ordinateur client.

À mesure que les mises à jour sont approuvées et installées, vous pouvez examiner la réussite et l’échec de l’installation dans l’espace de travail **Mises à jour** de la console Intune.

Les sections suivantes vous aident à maintenir à jour les logiciels installés sur vos ordinateurs gérés.

## <a name="before-you-start"></a>Avant de commencer
Avant de commencer à créer et à approuver les mises à jour logicielles, configurez et déployez des stratégies sur vos ordinateurs afin de contrôler quand et comment les mises à jour sont installées.

### <a name="to-configure-update-policy-settings"></a>Pour configurer les paramètres de la stratégie de mise à jour

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), sélectionnez **Stratégie** &gt; **Vue d’ensemble** &gt; **Ajouter une stratégie**.

2.  Configurez et déployez une stratégie **Paramètres de l'Agent Microsoft Intune** pour les paramètres de mise à jour. Vous pouvez utiliser les paramètres recommandés ou personnaliser les paramètres. Pour plus d’informations sur la création et le déploiement des stratégies, consultez [Tâches courantes de gestion des PC Windows avec le client Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

Le tableau suivant montre les valeurs que vous pouvez configurer dans la stratégie, ainsi que les valeurs recommandées qui seront utilisées si vous ne personnalisez pas la stratégie. Vous pouvez rechercher ces paramètres dans la section **Mises à jour** .

  |Paramètre de stratégie|Détails|
    |------------------|--------------------|
    |**Fréquence de détection des applications et mises à jour (heures)** |Spécifie la fréquence (entre 8 et 22 heures) à laquelle Intune recherche de nouvelles mises à jour et applications.<br /><br />Valeur recommandée : **8** heures|
    |**Installation automatisée ou demandée d'applications et de mises à jour** |Spécifie si les mises à jour sont installées automatiquement ou si l'utilisateur est invité avant l'installation. De plus, ce paramètre permet de planifier l'installation des mises à jour et des applications.<br /><br />**Installer automatiquement les mises à jour et applications planifiées** : installe les mises à jour et les applications selon la planification spécifiée.<br /><br />Le paramètre **Utiliser Maintenance automatique pour les ordinateurs Windows**  , qui dépend de la stratégie, indique que les mises à jour et les applications sont installées pendant la fenêtre de maintenance automatique de Windows.<br /><br />L’option **Inviter l’utilisateur à accepter l’installation** propose à l’utilisateur d’installer les mises à jour quand elles sont prêtes.<br /><br />Valeurs recommandées :<br /><br />Option **Installer automatiquement les mises à jour et applications planifiées** sélectionnée<br /><br />**Jour planifié : tous les jours**<br /><br />**Heure prévue : 3:00**<br /><br />Option **Utiliser Maintenance automatique pour les ordinateurs Windows** sélectionnée|
    |**Autoriser l'installation immédiate des mises à jour qui ne nécessitent pas une interruption de Windows** |L’option **Autoriser** installe les mises à jour immédiatement après leur téléchargement, sauf pour les mises à jour qui impliquent l’interruption ou le redémarrage de Windows. Ces mises à jour sont installées en fonction de la configuration du paramètre **Installation automatisée ou demandée des mises à jour** .<br /><br />L’option **Ne pas autoriser** installe les mises à jour en fonction de la configuration du paramètre **Installation automatisée ou demandée des mises à jour**.<br /><br />Valeur recommandée : **Autoriser** |
    |**Délai de redémarrage de Windows après l'installation d'applications et de mises à jour planifiées (minutes)** |Spécifie (entre 1 et 30 minutes) le délai d'attente avant le redémarrage de Windows après l'installation des applications et des mises à jour planifiées.<br /><br />Valeur recommandée : **15 minutes** |
    |**Délai entre le redémarrage de Windows et le début de l'installation des applications et mises à jour planifiées manquées (minutes)** |Spécifie le délai d'attente (entre 1 et 60 minutes) avant l'installation de mises à jour et d'applications à l'issue d'un redémarrage de Windows lorsqu'une mise à jour planifiée a été ignorée.<br /><br />Valeur recommandée : **5 minutes**|
    |**Autoriser l'utilisateur connecté à contrôler le redémarrage de Windows après l'installation d'applications et de mises à jour planifiées** |Spécifie si l’utilisateur connecté peut retarder le redémarrage de Windows (si la valeur est **Oui**) ou s’il doit être averti du redémarrage automatique de Windows (si la valeur est **Non**). Si aucun utilisateur n'est connecté à la fin de l'installation des mises à jour et des applications, Windows redémarre automatiquement dès que nécessaire. Par défaut, lorsque la valeur est définie sur **Non**, le délai avant le redémarrage de Windows est défini sur 5 minutes.<br /><br />Valeur recommandée : **Oui**|
    |**Inviter l’utilisateur à redémarrer pendant les mises à jour obligatoires de l’agent du client Windows Intune** |Indique si les utilisateurs connectés sont invités à redémarrer Windows lorsqu’une mise à jour obligatoire du client Intune exige le redémarrage de Windows.<br /><br />Valeur recommandée : **Oui**|
    |**Planification de l'installation des mises à jour obligatoires des agents clients Microsoft Intune** |Planifie le moment où l'installation des mises à jour du client a lieu.<br /><br />Valeur recommandée : non configuré|
    |**Attente entre les invites pour le redémarrage de Windows après l'installation de mises à jour planifiées et d'applications (minutes)** |Spécifie la fréquence (entre 1 et 1440 minutes) à laquelle l'utilisateur est invité à redémarrer Windows lorsqu'une mise à jour ou une application planifiée nécessitant un redémarrage de Windows est installée et que l'utilisateur retarde ce redémarrage.<br /><br />Valeur recommandée : **30 minutes** |

## <a name="update-software-made-by-microsoft"></a>Mise à jour de logiciels Microsoft
La mise à jour de logiciels Microsoft requiert très peu de travail de votre part. Toutefois, avant de commencer, il existe deux éléments que vous devez configurer :

-   **Catégories de produits et classifications des mises à jour** : définit les catégories et classifications des mises à jour que vous souhaitez rendre disponibles pour les ordinateurs. Par exemple, vous pouvez décider que seules les mises à jour critiques de Microsoft Office doivent être installées.

-   **Règles d'approbation automatique** : ces règles approuvent automatiquement les types spécifiés de mise à jour et réduisent vos frais administratifs. Par exemple, vous pouvez souhaiter approuver automatiquement toutes les mises à jour critiques.

Utilisez les deux procédures suivantes pour vous aider à préparer l'utilisation des mises à jour logicielles :

### <a name="configure-the-product-categories-and-update-classifications-you-want-to-make-available-to-managed-computers"></a>Configurer les catégories de produit et les classifications de mise à jour que vous souhaitez rendre disponibles sur les ordinateurs gérés

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Administration** &gt; **Mises à jour**.

2.  Dans la page **Paramètres du service : mises à jour** , dans la liste **Catégories de produits** , sélectionnez les catégories de mise à jour que vous voulez mettre à disposition sur les ordinateurs. Notez que les mises à jour courantes sont sélectionnées par défaut.

    > [!IMPORTANT]
    > Pour s’assurer que les ordinateurs reçoivent les mises à jour approuvées par l’administrateur, le paramètre de stratégie de groupe WSUS (Windows Server Update Services) **Spécifier l’emplacement intranet du service de mise à jour Microsoft** ne doit pas s’appliquer aux ordinateurs inscrits auprès d’Intune.

3.  Dans la liste **Classification de la mise à jour** , sélectionnez les classes de mise à jour que vous souhaitez rendre disponibles sur les ordinateurs gérés. Là encore, les options les plus courantes sont sélectionnées par défaut.

4.  Choisissez**Enregistrer** pour stocker vos sélections.

### <a name="to-configure-automatic-approval-rules-for-software-updates"></a>Pour configurer des règles d'approbation automatique pour les mises à jour logicielles

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Administration** &gt; **Mises à jour**.

2.  Dans la section **Règles d’approbation automatique** de la page **Paramètres du serveur : mises à jour**, choisissez **Nouveau**.

3.  Dans la page **Général** de l'Assistant Créer une règle d'approbation automatique, spécifiez un nom et éventuellement une description pour la règle.

4.  Dans la page **Catégories de produits** , sélectionnez les produits dont vous souhaitez que les mises à jour soient approuvées automatiquement.

5.  Dans la page **Classifications de mise à jour** , spécifiez les classifications de mise à jour que vous souhaitez approuver automatiquement.

6.  Dans la page **Déploiement** , procédez comme suit :

    -   Sélectionnez le groupe d’ordinateurs sur lesquels vous souhaitez déployer la nouvelle règle, puis choisissez **Ajouter**.

    -   Pour spécifier un délai d'installation des mises à jour, cochez la case **Imposer une échéance d'installation pour ces mises à jour** , puis, dans la liste **Délai d'installation** , sélectionnez un délai d'installation.

        > [!NOTE]
        > Si vous spécifiez un délai d'installation, l'ordinateur géré peut nécessiter un ou plusieurs redémarrages une fois l'intervalle d'échéance dépassé.

    -   Quand vous avez terminé, choisissez **Suivant**.

7.  Dans la page **Résumé**, passez en revue les paramètres de la nouvelle règle, puis choisissez **Terminer**.

La nouvelle règle est affichée dans la section **Règles d’approbation automatique** de la page **Paramètres du service : mises à jour** .

> [!NOTE]
> La création d’une règle d’approbation automatique ne concerne que les mises à jour à venir et non les mises à jour préexistantes dans Intune. Pour approuver ces mises à jour, vous devez exécuter la règle d'approbation automatique.


### <a name="to-edit-run-or-delete-an-automatically-approved-update-rule"></a>Pour modifier, exécuter ou supprimer une règle de mise à jour approuvée automatiquement

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Administration** &gt; **Mises à jour**.

2.  Dans la section **Règles d'approbation automatique** , sélectionnez une règle, puis effectuez l'une des opérations suivantes :

    -   Pour modifier la règle, choisissez **Modifier**, puis modifiez ses paramètres dans l’**Assistant Règle d’approbation automatique des mises à jour**.

    -   Pour exécuter la règle, choisissez **Exécuter les éléments sélectionnés**.

    -   Pour supprimer la règle, choisissez **Supprimer**.

        > [!NOTE]
        > La suppression d'une règle n'affecte pas les mises à jour précédentes approuvées par la règle supprimée.

## <a name="update-software-not-made-by-microsoft"></a>Mise à jour de logiciels non Microsoft
Vous pouvez déployer des mises à jour pour des logiciels qui n'ont pas été créés par Microsoft. Pour ce faire, utilisez l'Assistant **Télécharger mis à jour** pour ajouter la mise à jour à votre espace de stockage en cloud. Après cela, vous pouvez approuver ou refuser la mise à jour de la même façon que pour un logiciel Microsoft.

### <a name="to-upload-and-configure-a-third-party-update"></a>Pour télécharger et configurer une mise à jour tierce

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Mises à jour** &gt; **Vue d’ensemble** &gt; **Télécharger**.

2.  Sur la page **Fichiers de mise à jour**, choisissez **Parcourir** pour sélectionner les fichiers d’installation requis pour installer le package de mise à jour. Il peut s'agir d'un fichier Windows Installer (.msi), d'un fichier correctif (.msp) de Windows Installer ou d'un fichier programme .exe. Vous pouvez également inclure des fichiers ou dossiers supplémentaires qui se trouvent dans le même dossier que le fichier d'installation.

    La taille totale des fichiers sélectionnés à télécharger s'affiche. Notez que cette taille n'inclut pas la taille non compressée ou développée des fichiers d'installation.

3.  Une fois les fichiers d’installation spécifiés, la page **Description de la mise à jour** affiche le nom, la description et la classification des informations du logiciel que Intune a extraites des fichiers d’installation de logiciel. Vous pouvez sélectionner une classification pour étiqueter le type de mise à jour déployée (mises à jour, mises à jour critiques, mises à jour de sécurité, correctifs cumulatifs ou Service Packs). Choisissez **Suivant** lorsque vous avez terminé.

4.  Dans la page **Configuration requise** de l’Assistant, sélectionnez l’architecture (32 bits, 64 bits ou les deux), ainsi que les systèmes d’exploitation des ordinateurs gérés auxquels cette mise à jour sera appliquée.

5.  Dans la page **Règles de détection**, spécifiez comment Intune détermine si la mise à jour existe déjà sur les ordinateurs gérés. Si vous utilisez l’option par défaut, **Utiliser les règles de détection par défaut**, Intune installera toujours le package de mise à jour une seule fois sur chaque ordinateur ciblé.

    > [!NOTE]
    > Si le fichier d'installation de mise à jour que vous avez spécifié est un fichier Windows Installer ou .msi, la page **Règles de détection** de l'Assistant ne s'affiche pas. En effet, les fichiers Windows Installer et .msp contiennent leurs propres instructions leur permettant de détecter les installations de mises à jour précédentes.

    Parmi les règles suivantes, sélectionnez-en une ou plusieurs pour déterminer si la mise à jour est déjà installée sur les ordinateurs gérés :

    -   **Le fichier existe**

    -   **Le code de produit MSI existe déjà**

    -   **Cette clé du Registre existe**

6.  Spécifiez toute information supplémentaire requise pour configurer la règle de détection, notamment un nom de fichier et un chemin d’accès à celui-ci, le code de produit Windows Installer ou une clé de Registre, puis choisissez **Suivant**.

7.  Dans la page **Conditions préalables** de l'Assistant, vous spécifiez un logiciel qui doit déjà être installé pour pouvoir installer cette mise à jour. Vous pouvez spécifier la valeur **Aucune**, sélectionner un package logiciel qui a déjà été ajouté à Intune et qui est géré par celui-ci. Vous pouvez aussi spécifier l’une des règles suivantes pour décrire le logiciel :

    -   **Le fichier existe**

    -   **Le code de produit MSI existe déjà**

    -   **Cette clé du Registre existe**

8.  Spécifiez toute information supplémentaire requise pour configurer la règle de détection, par exemple un nom de fichier est un chemin d’accès à celui-ci, le code de produit Windows Installer ou une clé de Registre, puis choisissez **Suivant**.

9. Dans la page **Arguments de ligne de commande** de l'Assistant, vous pouvez ajouter toutes les propriétés d'installation requises à la ligne de commande d'installation pour modifier le comportement du fichier d'installation. Par exemple, certains logiciels prennent en charge la propriété **/q** afin d’activer l’installation en mode silencieux. Reportez-vous à la documentation de votre package logiciel pour obtenir des informations sur les arguments de ligne de commande pris en charge. Spécifiez les arguments de ligne de commande dont vous avez besoin, puis choisissez **Suivant**.

    > [!NOTE]
    > Si la mise à jour ne prend pas en charge l’installation en mode silencieux, vous ne pouvez pas installer la mise à jour à l’aide d’Intune

10. Dans la page **Codes de retour** de l'Assistant, vous pouvez spécifier comment les codes de retour provenant de l'installation de la mise à jour sont interprétés. Par défaut, Intune utilise les codes de retour standard pour signaler une installation réussie ou non d’un package de mise à jour. Les codes de retour fournis sont les suivants :

|Code de retour|Détails|
|---------------|------------------|
|**0**|Opération réussie|
|**3010**|Redémarrage réussi|

11. Tout code de retour non répertorié est considéré comme un échec.
Certaines mises à jour utilisent des interprétations non standard pour les codes de retour. Dans ce cas, vous pouvez spécifier votre propre interprétation du code de retour.

12. Spécifiez ou modifiez les codes de retour requis, puis choisissez **Suivant**.

13. Dans la page **Résumé** de l’Assistant, passez en revue les actions à entreprendre, puis choisissez **Télécharger** pour compléter l’Assistant.

La mise à jour téléchargée est enregistrée dans votre stockage cloud Intune. Si vous disposez d’un espace libre insuffisant pour télécharger le package d’application, vous en êtes informé pendant le processus de téléchargement. Intune ne peut pas déterminer si l’espace libre est suffisant avant le début du téléchargement de la mise à jour, car les fichiers d’installation et de configuration compressés nécessitent davantage d’espace quand ils sont décompressés.

Quand une mise à jour tierce est téléchargée dans Intune, elle s’affiche dans l’espace de travail **Mises à jour** du volet **Toutes les mises à jour**. Vous pouvez ensuite approuver et déployer la mise à jour. Pour plus d’informations, consultez la section « Approuver et refuser des mises à jour » suivante.

## <a name="approve-and-decline-updates"></a>Approuver ou refuser des mises à jour
Lorsque des mises à jour sont prêtes à être installées, un message s'affiche sur la page **Vue d'ensemble des mises à jour** de l'espace de travail **Mises à jour** sous **État de la mise à jour**. Choisissez ce message pour ouvrir la page **Toutes les mises à jour** pour voir les mises à jour prêtes pour l’approbation.

Vous pouvez utiliser la liste **Filtres** pour faciliter la recherche des mises à jour. Par exemple, vous pouvez afficher uniquement les mises à jour qui ont échoué ou les mises à jour qui sont remplacées.

Lorsque vous sélectionnez une mise à jour dans la liste, d'autres commandes sont disponibles pour vous permettre de gérer les mises à jour comme indiqué dans le tableau suivant :

|Tâche|Détails|
|--------|--------------------|
|**Afficher les propriétés**|Affiche des informations détaillées sur la mise à jour, y compris le nombre d'ordinateurs auxquels elle s'applique.|
|**Éditer**|Pour les mises à jour non Microsoft uniquement. Vous permet de modifier les propriétés de la mise à jour.|
|**Approuver**|Approuve la mise à jour sélectionnée et vous permet de configurer les groupes sur lesquels elle va être déployée. Pour plus d’informations, voir la procédure **Pour approuver des mises à jour** de cette rubrique.|
|**Refuser**|Supprime les approbations précédentes de la mise à jour et masque la mise à jour des vues par défaut. En outre, les données du rapport pour la mise à jour seront supprimées.<br /><br />Si vous voulez localiser plus tard une mise à jour refusée, définissez le filtre sur la valeur **Refusé** dans la page **Toutes les mises à jour**. Vous pouvez ensuite approuver cette mise à jour si nécessaire.<br /><br />Si une mise à jour a été refusée en raison de son expiration dans Microsoft Update, vous ne pouvez pas l’approuver dans la console d’administration d’Intune.<br /><br />Si vous supprimez une stratégie de mise à jour déployée sur des ordinateurs, les valeurs de ces paramètres sont rétablies à leur état par défaut prévu pour le système d'exploitation installé sur les ordinateurs.|
|**Supprimer**|Pour les mises à jour non Microsoft uniquement. Supprime la mise à jour sélectionnée.|
|**Télécharger**|Démarre l’Assistant **Télécharger la mise à jour** qui vous permet de télécharger des mises à jour non-Microsoft que vous souhaitez déployer.|

### <a name="to-approve-updates"></a>Pour approuver des mises à jour

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Mises à jour** &gt; **Vue d’ensemble** &gt; **Nouvelles mises à jour à approuver**.

    Dans l’espace de travail **Mises à jour**, choisissez **Vue d’ensemble** &gt; **Nouvelles mises à jour à approuver**.

    > [!NOTE]
    > Le lien **Nouvelles mises à jour à approuver** apparaît dans la zone **État de la mise à jour** uniquement s'il existe au moins un ordinateur géré nécessitant une mise à jour à approuver.

2.  Sélectionnez une mise à jour, examinez ses propriétés en bas de la page pour vous assurer que vous souhaitez bien l’approuver, puis choisissez **Approuver**. Vous pouvez sélectionner plusieurs mises à jour en maintenant la touche **CTRL** enfoncée quand vous sélectionnez chaque élément.

3.  Dans la page **Sélectionner des groupes** , sélectionnez un groupe sur lequel vous souhaitez déployer les mises à jour, puis choisissez **Ajouter**. Une fois la sélection des groupes terminée, choisissez **Suivant**.

4.  Sur la page **Action de déploiement** , procédez comme suit pour chaque groupe de la liste :

    -   Dans la liste **Approbation** , sélectionnez l'une des valeurs suivantes :

        -   **Installation requise** : installe la mise à jour sur les ordinateurs du groupe spécifié.

        -   **Ne pas installer** : signale l’applicabilité uniquement et n’installe pas la mise à jour.

        -   **Installation disponible** : l'utilisateur peut installer l'application à la demande à partir du portail d'entreprise.

        -   **Désinstaller** : supprime les mises à jour des ordinateurs du groupe ciblé.

            > [!IMPORTANT]
            > La mise à jour est retirée même si elle n’a pas été installée par Intune.

    -   Dans la liste **Échéance** , sélectionnez l'une des valeurs suivantes :

        -   **Aucun** : indique qu’aucune date d’échéance n’est imposée pour l’installation de la mise à jour et les utilisateurs peuvent la refuser à chaque fois.

        -   **Dès que possible** : installe la mise à jour sur les ordinateurs ciblés dès que l’occasion se présente.

        -   **Personnalisé** : spécifie la date et l’heure auxquelles les mises à jour approuvées sont installées.

        -   **Une semaine**, **Deux semaines**, **Un mois** : installe la mise à jour au cours de la période spécifiée.

5.  Choisissez **Terminer** pour enregistrer les paramètres ou sur **Annuler** pour les ignorer et revenir à la liste des mises à jour.

    > [!IMPORTANT]
    > Tant que les opérations **Ne pas installer**, **Installation requise**ou **Désinstaller** n'ont pas été configurées de façon explicite pour un groupe enfant, une opération configurée pour un groupe parent est toujours héritée par tous ses éléments enfants.

6.  Vous pouvez consulter le volet des détails au bas de la page **Toutes les mises à jour** pour connaître les messages de rappel relatifs à la mise à jour.


### <a name="see-also"></a>Voir aussi
[Stratégies pour protéger les PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
