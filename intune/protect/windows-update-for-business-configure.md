---
title: Configurer Windows Update pour Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Mettez à jour les paramètres des mises à jour logicielles dans un profil pour créer un anneau de mise à jour, vérifiez la conformité et suspendez les mises à jour dans les paramètres de Windows Update pour Entreprise à l’aide de Microsoft Intune sur les appareils Windows 10.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa8cc396c05150006799c1e9b86ecb63351cdb36
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314706"
---
# <a name="manage-software-updates-in-intune"></a>Gérer les mises à jour logicielles dans Intune

Utilisez Intune pour définir des anneaux de mise à jour qui spécifient comment et quand Windows en tant que service met à jour vos appareils Windows 10. Les anneaux de mise à jour sont des stratégies que vous attribuez à des groupes d’appareils. En utilisant les anneaux de mise à jour, vous pouvez créer une stratégie de mise à jour qui reflète les besoins de votre entreprise. Pour plus d’informations, consultez [Gérer les mises à jour à l’aide de Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

Avec Windows 10, les nouvelles mises à jour de fonctionnalités et mises à jour qualité incluent le contenu de toutes les mises à jour précédentes. Du moment que vous avez installé la dernière mise à jour, vous savez que vos appareils Windows 10 sont à jour. À la différence des versions précédentes de Windows, vous devez maintenant installer la mise à jour complète au lieu d’une partie seulement.


Avec Windows Update pour Entreprise, vous simplifiez l’expérience utilisateur de gestion des mises à jour. Vous n’avez pas besoin d’approuver des mises à jour individuelles pour des groupes d’appareils. Vous pouvez gérer les risques dans vos environnements en configurant une stratégie de lancement des mises à jour. Intune vous permet de [configurer les paramètres de mise à jour](../windows-update-settings.md) des appareils et de reporter l’installation des mises à jour. Intune ne stocke pas les mises à jour, seulement l’attribution des stratégies de mise à jour. Les appareils accèdent directement à Windows Update pour les mises à jour. Cette collection de paramètres qui configure quand les mises à jour Windows 10 sont installées est appelée un *anneau de mise à jour Windows 10*.

Les anneaux de mise à jour Windows 10 prennent en charge les [balises d’étendue](../fundamentals/scope-tags.md). Vous pouvez utiliser des balises d’étendue avec des anneaux de mise à jour pour vous aider à filtrer et à gérer des ensembles de configurations que vous utilisez.

## <a name="prerequisites"></a>Prérequis  

Les conditions préalables suivantes doivent être remplies pour utiliser des mises à jour Windows pour des appareils Windows 10 dans Intune.  

- Les PC Windows 10 doivent exécuter au minimum Windows 10 Professionnel avec la mise à jour anniversaire de Windows ou version ultérieure (version 1607 ou ultérieure)
- Windows Update prend en charge les éditions de Windows 10 suivantes :
  - Windows 10
  - Windows 10 Collaboration (pour les appareils Surface Hub)
  - Windows Holographic for Business  

    Windows Holographic for Business prend en charge un sous-ensemble de paramètres pour les mises à jour Windows, notamment :
    - **Comportement des mises à jour automatiques**
    - **Mises à jour de produit Microsoft**
    - **Canal de maintenance** : Prend en charge les options **Canal semi-annuel** et **Canal semi-annuel (ciblé)** . Pour plus d’informations, consultez [Gérer Windows Holographic](../fundamentals/windows-holographic-for-business.md).  

    > [!NOTE]  
    > **Versions et éditions non prises en charge** :
    > - Windows 10 Mobile  
    > - Windows 10 Enterprise LTSC. Windows Update for Business (WUfB) ne prend actuellement pas en charge les versions *Long Term Service Channel (LTSC)* . Prévoyez d'utiliser d'autres méthodes de mise à jour, notamment WSUS ou Configuration Manager.  

- Sur les appareils Windows, le paramètre **Commentaires et diagnostics** > **Données de diagnostic et d’utilisation** doit être défini sur **De base**, **Amélioré** ou **Complet**.  

  Vous pouvez configurer manuellement le paramètre *Données de diagnostic et d’utilisation* pour les appareils Windows 10, ou utiliser un profil de restriction d’appareils Intune pour Windows 10 et versions ultérieures. Si vous utilisez un profil de restriction d’appareils, définissez la valeur de [restriction d’appareils](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) du paramètre **Partager les données d'utilisation** sur au moins **De base**. Ce paramètre se trouve dans la catégorie **Création de rapports et les données de télémétrie** lorsque vous configurez une stratégie de restriction d’appareils pour Windows 10 ou version ultérieure.

  Pour plus d’informations sur les profils d’appareils, consultez [Configurer des paramètres de restriction d’appareils](../configuration/device-restrictions-configure.md).  

- Si vous utilisez le portail Azure Classic, [migrez vos paramètres vers le portail Azure](#migrate-update-settings-to-the-azure-portal).  


## <a name="create-and-assign-update-rings"></a>Créer et affecter des anneaux de mise à jour

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Sélectionnez **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10** > **Créer**.
4. Entrez un nom, une description (facultatif), puis choisissez **Configurer**.
5. Dans **Paramètres**, configurer des paramètres pour les besoins de votre entreprise. Pour plus d’informations sur les paramètres disponibles, consultez [Paramètres de Windows Update](../windows-update-settings.md).  
6. Une fois que vous avez fini, sélectionnez **OK**. Dans **Créer un anneau de mise à jour**, sélectionnez **Créer**. Le nouvel anneau de mise à jour s’affiche dans la liste des anneaux de mises à jour.
7. Pour attribuer l’anneau, dans la liste des anneaux de mise à jour, sélectionnez un anneau puis, sous l’onglet du \<nom de l’anneau, choisissez **Affectations**.
8. Utilisez les onglets **Inclure** et **Exclure** pour définir les groupes auxquels cet anneau est attribué, puis sélectionnez **Enregistrer** pour terminer l’affectation.

## <a name="manage-your-windows-10-update-rings"></a>Gérer vos anneaux de mise à jour Windows 10
Dans le portail, vous pouvez sélectionner un anneau de mise à jour Windows 10 pour ouvrir son onglet **Vue d’ensemble**. Dans ce volet, vous pouvez consulter l’état d’affectation des anneaux et prendre des mesures supplémentaires pour gérer l’anneau. 
### <a name="to-view-an-updates-rings-overview-pane"></a>Pour afficher un volet de vue d’ensemble des anneaux de mise à jour : 
1. Connectez-vous au portail Azure.
2. Accédez à **Intune** > **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10**.
3. Sélectionnez l’anneau de mise à jour que vous souhaitez afficher ou gérer.  

En plus de pouvoir consulter l’état d’affectation, vous pouvez sélectionner les actions suivantes en haut du volet Vue d’ensemble pour gérer l’anneau de mise à jour :  
- [Supprimer](#delete)  
- [Pause](#pause)  
- [Reprendre](#resume)  
- [Prolonger](#extend)  
- [Désinstaller](#uninstall)  

![Actions disponibles](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Supprimer  
Sélectionnez **Supprimer** pour arrêter l’application des paramètres de l’anneau de mise à jour Windows 10 sélectionné. La suppression d’un anneau supprime sa configuration Intune afin qu’Intune n’applique plus ces paramètres.  

La suppression d’un anneau d’Intune ne modifie pas les paramètres sur les appareils auxquels l’anneau de mise à jour a été attribué.  L’appareil conserve ses paramètres actuels. Les appareils ne maintiennent pas un enregistrement historique des paramètres qu’ils détenaient précédemment. Les appareils peuvent également recevoir des paramètres d’anneaux de mise à jour supplémentaires qui restent actifs.  

#### <a name="to-delete-a-ring"></a>Pour supprimer un anneau  
1. Dans la page Vue d’ensemble d’un anneau de mise à jour, sélectionnez **Supprimer**.  
2. Sélectionnez **OK**.  

### <a name="pause"></a>Suspendre  
Sélectionnez **Suspendre** pour empêcher les appareils attribués de recevoir des mises à jour de fonctionnalité ou de qualité pendant une période jusqu’à 35 jours à partir du moment où vous suspendez l’anneau. Une fois que le nombre maximal de jours s’est écoulé, la fonctionnalité mise en pause expire automatiquement et l’appareil recherche les mises à jour applicables dans Windows Update. Suite à cette analyse, vous pouvez suspendre à nouveau les mises à jour. Si vous reprenez un anneau de mise à jour suspendu et que vous le suspendez à nouveau, la période de suspension est réinitialisée sur 35 jours.  

#### <a name="to-pause-a-ring"></a>Pour suspendre un anneau  
1. Dans la page Vue d’ensemble d’un anneau de mise à jour, sélectionnez **Suspendre**.  
2. Sélectionnez **Fonctionnalité** ou **Qualité** pour suspendre ce type de mise à jour, puis sélectionnez **OK**.  
3. Après la suspension d’un type de mise à jour, vous pouvez sélectionner Suspendre à nouveau pour suspendre l’autre type de mise à jour.  

Lorsqu’un type de mise à jour est suspendu, le volet Vue d’ensemble de cet anneau affiche le nombre de jours restants avant la reprise de ce type de mise à jour.

> [!IMPORTANT]  
> Lorsque vous exécutez une commande de suspension, les appareils la reçoivent à leur prochaine connexion au service. Il se peut qu’ils installent une mise à jour planifiée avant d’effectuer la vérification auprès du service. En outre, si un appareil cible est désactivé lorsque vous émettez la commande de suspension, lorsque vous l’allumez, il peut télécharger et installer les mises à jour planifiées avant d’effectuer les vérifications avec Intune.

### <a name="resume"></a>Reprendre  
Lorsqu’un anneau de mise à jour est suspendu, vous pouvez sélectionner **Reprendre** pour restaurer les mises à jour de fonctionnalité et de qualité pour cet anneau. Lorsque vous reprenez un anneau de mise à jour, vous pouvez le suspendre à nouveau.  

#### <a name="to-resume-a-ring"></a>Pour reprendre un anneau  
1. Dans la page Vue d’ensemble d’un anneau de mise à jour suspendu, sélectionnez **Reprendre**.  
2. Sélectionnez parmi les options disponibles pour reprendre les mises à jour de **fonctionnalité** ou de **qualité**, puis sélectionnez **OK**.  
3. Après la reprise d’un type de mise à jour, vous pouvez sélectionner Reprendre à nouveau pour reprendre l’autre type de mise à jour.  

### <a name="extend"></a>Extend  
Lorsqu’un anneau de mise à jour est suspendu, vous pouvez sélectionner **Prolonger** pour réinitialiser la période de suspension des mises à jour de fonctionnalité et de qualité de cet anneau de mise à jour sur 35 jours.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>Pour prolonger la période de suspension d’un anneau  
1. Dans la page Vue d’ensemble d’un anneau de mise à jour suspendu, sélectionnez **Prolonger**. 
2. Sélectionnez parmi les options disponibles pour reprendre les mises à jour de **fonctionnalité** ou de **qualité**, puis sélectionnez **OK**.  
3. Lorsque la suspension d’un type de mise à jour est prolongée, vous pouvez sélectionner Prolonger à nouveau pour prolonger l’autre type de mise à jour.  

### <a name="uninstall"></a>Désinstaller  
Un administrateur Intune peut utiliser **Désinstaller** pour désinstaller (restaurer) la dernière mise à jour de *fonctionnalité* ou la dernière mise à jour de *qualité* d’un anneau de mise à jour actif ou suspendu. Après la désinstallation d’un type, vous pouvez désinstaller l’autre type. Intune ne prend pas en charge ni ne gère pas la capacité des utilisateurs à désinstaller les mises à jour.  

> [!IMPORTANT] 
> Lorsque vous utilisez l’option *Désinstaller*, Intune transmet immédiatement la demande de désinstallation aux appareils. 
> - Les appareils Windows commencent la suppression des mises à jour dès qu’elles reçoivent la modification de la stratégie Intune. La suppression des mises à jour n’est pas limitée aux planifications de maintenance, même lorsqu’elle est configurée dans le cadre de l’anneau de mise à jour. 
> - Si la suppression des mises à jour nécessite un redémarrage de l’appareil, l’appareil redémarre sans offrir à l’utilisateur de l’appareil une option de délai.


Pour que la désinstallation réussisse :  
- Un appareil doit exécuter la mise à jour d’avril 2018 de Windows 10 (version 1803) ou ultérieure.  

La dernière mise à jour doit être installée sur un appareil. Les mises à jour étant cumulatives, les appareils qui installent la dernière mise à jour disposeront de la mise à jour de fonctionnalité et de qualité la plus récente. Un exemple du moment où vous pouvez utiliser cette option consiste à restaurer la dernière mise à jour si vous détectez un problème de rupture sur vos machines Windows 10.  

Tenez compte des éléments suivants lorsque vous utilisez Désinstaller :  
- La désinstallation d’une mise à jour des fonctionnalités ou d’une mise à jour qualité est disponible uniquement pour le canal de maintenance sur lequel se trouve l’appareil.  

- L’utilisation de la désinstallation de mises à jour de fonctionnalité ou de qualité déclenche une stratégie pour restaurer la mise à jour précédente sur vos machines Windows 10.  

- Sur un appareil Windows 10, après une restauration réussie de la mise à jour de qualité, les utilisateurs finaux continuent à voir la mise à jour répertoriée dans **Paramètres Windows** > **Mises à jour** > **Historique des mises à jour**.  

- Pour les mises à jour de fonctionnalité plus précisément, la durée pendant laquelle vous pouvez désinstaller la mise à jour de fonctionnalité est limitée à 2-60 jours, comme configuré par le paramètre de mise à jour des anneaux de mise à jour **Définir la période de désinstallation des mises à jour de fonctionnalité (2-60 jours)** . Vous ne pouvez pas restaurer une mise à jour de fonctionnalité qui a été installée sur un appareil après une durée d’installation supérieure à la période de désinstallation configurée.  

  Par exemple, considérez un anneau de mise à jour avec une période de désinstallation des mises à jour de fonctionnalités de 20 jours. Après 25 jours, vous décidez d’annuler la dernière mise à jour de fonctionnalité et d’utiliser l’option de désinstallation.  Les appareils qui ont installé la mise à jour de fonctionnalité il y a plus de 20 jours ne peuvent pas la désinstaller, puisqu’ils ont supprimé les bits nécessaires dans le cadre de leur maintenance. Cependant, les appareils qui n’ont installé la mise à jour des fonctionnalités qu’il y a 19 jours maximum peuvent désinstaller la mise à jour s’ils ont réussi à s’enregistrer pour recevoir la commande de désinstallation avant que la période de désinstallation de 20 jours n’ait expiré.  

Pour plus d’informations sur les stratégies Windows Update, consultez [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (Mettre à jour CSP) dans la documentation de gestion de client Windows.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>Pour désinstaller la dernière mise à jour de Windows 10  
1. Dans la page Vue d’ensemble d’un anneau de mise à jour suspendu, sélectionnez **Désinstaller**.  
2. Sélectionnez parmi les options disponibles pour désinstaller les mises à jour de **fonctionnalité** ou de **qualité**, puis sélectionnez **OK**.  
3. Après le déclenchement de la désinstallation d’un type de mise à jour, vous pouvez sélectionner Désinstaller à nouveau pour désinstaller le type de mise à jour restant.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Migrer les paramètres de mise à jour vers le portail Azure  
Le portail Azure Classic comporte également un nombre limité d’autres paramètres relatifs aux mises à jour Windows 10 dans le profil de configuration des appareils. Si vous avez configuré l’un de ces paramètres durant la migration vers le portail Azure, nous vous recommandons vivement d’effectuer les actions suivantes :  

1. Créez des anneaux de mise à jour Windows 10 dans le portail Azure avec les paramètres dont vous avez besoin. Le paramètre **Autoriser les fonctionnalités en version préliminaire** n’est pas pris en charge dans le portail Azure, car il n’est plus applicable aux dernières builds Windows 10. Lorsque vous créez des anneaux de mise à jour, vous pouvez configurer les trois autres paramètres, ainsi que d’autres paramètres de mises à jour Windows 10.  

   > [!NOTE]  
   > Les paramètres de mises à jour Windows 10 créés dans le portail classique ne sont pas affichés dans le portail Azure après la migration. Toutefois, ces paramètres sont appliqués. Si vous effectuez la migration de l’un de ces paramètres et si vous modifiez la stratégie migrée à partir du portail Azure, ces paramètres sont supprimés de la stratégie.  

2. Supprimez les paramètres de mise à jour dans le portail classique. Une fois que vous avez effectué la migration vers le portail Azure, et que vous avez ajouté les mêmes paramètres à un anneau de mise à jour, vous devez supprimer les paramètres du portail Azure Classic pour éviter d’éventuels conflits de stratégies. Par exemple, quand le même paramètre est configuré avec des valeurs différentes, un conflit se produit. Cela n’est pas facile à identifier, car le paramètre configuré dans le portail Azure Classic ne s’affiche pas dans le portail Azure.  

## <a name="next-steps"></a>Étapes suivantes
[Paramètres de Windows Update pris en charge par Intune](../windows-update-settings.md)  

[Rapports de conformité Intune pour les mises à jour](../windows-update-compliance-reports.md)

[Résolution des problèmes liés aux anneaux de mise à jour Windows 10](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

