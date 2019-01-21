---
title: Configurer Windows Update pour Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Mettez à jour les paramètres des mises à jour logicielles dans un profil pour créer un anneau de mise à jour, vérifiez la conformité et suspendez les mises à jour dans les paramètres de Windows Update pour Entreprise à l’aide de Microsoft Intune sur les appareils Windows 10.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: ccb91082a3226ec4091a139d31796fd77bdf0616
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297381"
---
# <a name="manage-software-updates-in-intune"></a>Gérer les mises à jour logicielles dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows en tant que service permet de mettre à jour des appareils Windows 10. Avec Windows 10, les nouvelles mises à jour de fonctionnalités et mises à jour qualité incluent le contenu de toutes les mises à jour précédentes. Du moment que vous avez installé la dernière mise à jour, vous savez que vos appareils Windows 10 sont à jour. À la différence des versions précédentes de Windows, vous devez maintenant installer la mise à jour complète au lieu d’une partie seulement.

Avec Windows Update pour Entreprise, vous simplifiez l’expérience utilisateur de gestion des mises à jour. Vous n’avez pas besoin d’approuver des mises à jour individuelles pour des groupes d’appareils. Vous pouvez gérer les risques dans vos environnements en configurant une stratégie de lancement des mises à jour. Windows Update vérifie que les mises à jour sont installées au bon moment. Microsoft Intune vous permet de configurer les paramètres de mise à jour des appareils et de reporter l’installation des mises à jour. Intune ne stocke pas les mises à jour, seulement l’attribution des stratégies de mise à jour. Les appareils accèdent directement à Windows Update pour les mises à jour. Utilisez Intune pour configurer et gérer les **anneaux de mise à jour de Windows 10**. Un anneau de mise à jour contient un groupe de paramètres qui permettent de configurer la planification et le mode d’installation des mises à jour de Windows 10. Par exemple, vous pouvez configurer les paramètres suivants :

- **Canal de maintenance Windows 10** : choisissez le canal de maintenance à partir duquel vous souhaitez que les groupes d’appareils reçoivent des mises à jour. Les canaux suivants sont disponibles : 
  - Canal semi&#8208;annuel
  - Canal semi&#8208;annuel (ciblé)
  - Windows Insider &#8208; Rapide
  - Windows Insider &#8208; Lent
  - Publier Windows Insider 
      
  Pour plus d’informations sur les canaux de maintenance disponibles, consultez [Vue d’ensemble de Windows as a Service](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels).
- **Paramètres de report** : configurez les paramètres de report des mises à jour si vous souhaitez différer l’installation des mises à jour pour des groupes d’appareils. Utilisez ces paramètres pour organiser le déploiement de vos mises à jour par étapes et suivre leur progression.
- **Suspension** : si un problème se produit durant le lancement de la mise à jour, vous pouvez reporter son installation. 
- **Fenêtre de maintenance** : configurez les heures d’installation des mises à jour.
- **Type de mise à jour** : choisissez le type des mises à jour installées. Par exemple, les mises à jour qualité, des fonctionnalités ou des pilotes.
- **Comportement d’installation** : permet de configurer la façon dont la mise à jour est installée. Par exemple, l’appareil redémarre-t-il automatiquement après l’installation ?
- **Téléchargement par des pairs** : vous pouvez configurer le téléchargement par des pairs. Si cette option est activée, lorsqu’un appareil a terminé le téléchargement d’une mise à jour, les autres appareils peuvent télécharger la mise à jour à partir de celui-ci. Ce paramètre accélère le processus de téléchargement.

Une fois que vous avez créé les anneaux de mise à jour, affectez-les à des groupes d’appareils. En utilisant les anneaux de mise à jour, vous pouvez créer une stratégie de mise à jour qui reflète les besoins de votre entreprise. Pour plus d’informations, consultez [Gérer les mises à jour à l’aide de Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Avant de commencer

- Pour mettre à jour les PC Windows 10, ceux-ci doivent exécuter au minimum Windows 10 Professionnel avec la mise à jour anniversaire de Windows.

- Windows Update prend en charge les versions suivantes de Windows 10 :
  - Windows 10
  - Windows 10 Collaboration (pour les appareils Surface Hub)
  - [Windows Holographic for Business](#windows-holographic-for-business-support)

  Les appareils qui exécutent Windows 10 Mobile ne sont pas pris en charge.

- Sur les appareils Windows, le paramètre **Commentaires et diagnostics** > **Données de diagnostic et d’utilisation** doit être défini au minimum sur **De base**.

    ![Paramètre Windows pour les données de diagnostic et d’utilisation](./media/telemetry-basic.png)

    Vous pouvez configurer ce paramètre manuellement ou utiliser un profil Intune pour Windows 10 et ultérieur (**Restrictions sur l’appareil** > **Création de rapports et télémétrie** > Définir **Partager les données d’utilisation** avec au moins la valeur **De base**). Pour plus d’informations sur les profils d’appareils, consultez [Configurer des paramètres de restriction d’appareils](device-restrictions-configure.md).

- Le portail Azure Classic comporte également un nombre limité d’autres paramètres relatifs aux mises à jour Windows 10 dans le profil de configuration des appareils. Si l’un de ces paramètres est configuré durant la migration vers le portail Azure, nous vous recommandons vivement d’effectuer les tâches suivantes :

  1. Créez des anneaux de mise à jour Windows 10 dans le portail Azure avec les paramètres dont vous avez besoin. Le paramètre **Autoriser les fonctionnalités en version préliminaire** n’est pas pris en charge dans le portail Azure, car il n’est plus applicable aux dernières builds Windows 10. Quand vous créez des anneaux de mise à jour, vous pouvez configurer les autres paramètres ainsi que d’autres paramètres associés aux mises à jour de Windows 10.

   > [!NOTE]
   > Les paramètres de mises à jour Windows 10 créés dans le portail classique ne sont pas affichés dans le portail Azure après la migration. Toutefois, ces paramètres sont appliqués. Si vous effectuez la migration de l’un de ces paramètres et si vous modifiez la stratégie migrée à partir du portail Azure, ces paramètres sont supprimés de la stratégie.

  2. Supprimez les paramètres de mise à jour dans le portail classique. Après avoir effectué la migration vers le portail Azure et ajouté les mêmes paramètres à un anneau de mise à jour, supprimez les paramètres du portail Azure Classic pour éviter d’éventuels conflits de stratégies. Par exemple, quand le même paramètre est configuré avec des valeurs différentes, un conflit se produit. Ce n’est pas facile à identifier, car le paramètre configuré dans le portail Classic n’est pas dans le portail Azure.

## <a name="create-and-assign-update-rings"></a>Créer et affecter des anneaux de mise à jour

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10** > **Créer**.
3. Entrez un nom, une description (facultatif), puis choisissez **Configurer**.
4. Dans **Paramètres**, entrez les informations suivantes :  

   **Paramètres de mise à jour**  
   - **Canal de maintenance** : définissez le canal à partir duquel l’appareil reçoit les mises à jour Windows.
   - **Mises à jour de produits Microsoft** : choisissez si vous souhaitez rechercher les mises à jour d’applications à partir de Microsoft Update.
   - **Pilotes Windows** : choisissez si vous souhaitez exclure des pilotes Windows Update pendant les mises à jour.
   - **Période de report des mises à jour qualité (jours)**  : entrez le nombre de jours durant lesquels les mises à jour qualité sont différées. Vous pouvez différer la réception de ces mises à jour qualité jusqu’à 30 jours après leur publication.

     En règle générale, les mises à jour qualité sont des correctifs et des améliorations apportées aux fonctionnalités existantes de Windows. Elles sont publiées le deuxième mardi de chaque mois. Les mises à jour qualité proposées par Windows Update pour Entreprise reçoivent uniquement ces mises à jour (version « B »). Toutefois, Microsoft peut en publier d’autres à tout moment. Vous pouvez définir si, et pendant combien de temps, vous souhaitez différer la réception des mises à jour qualité après leur mise à disposition sur Windows Update. Pour plus d’informations, consultez [Déployer les mises à jour à l’aide de Windows Update pour Entreprise](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb).

   - **Période de report des mises à jour des fonctionnalités (jours)**  : entrez le nombre de jours durant lesquels les mises à jour de fonctionnalités sont différées. Vous pouvez différer la réception de ces mises à jour de fonctionnalités jusqu’à 180 jours après leur publication.

     En règle générale, les mises à jour de fonctionnalités correspondent à de nouvelles fonctionnalités de Windows. Après avoir configuré le paramètre **Canal de maintenance**, vous pouvez définir si, et pendant combien de temps, vous souhaitez différer la réception des mises à jour de fonctionnalités après leur mise à disposition sur Windows Update.

     Par exemple : **Si le canal de maintenance est défini sur Canal semi-annuel (ciblé) et la période de report sur 30 jours** : partons de l’hypothèse que la mise à jour de fonctionnalité X est d’abord disponible publiquement sur Windows Update comme canal semi-annuel (ciblé) en janvier. L’appareil ne reçoit pas la mise à jour avant février (soit 30 jours plus tard).

     **Si le canal de maintenance est défini sur Canal semi-annuel et la période de report sur 30 jours** : partons de l’hypothèse que la mise à jour de fonctionnalité X est d’abord disponible publiquement sur Windows Update comme canal semi-annuel (ciblé) en janvier. Quatre mois plus tard, en avril, la mise à jour de fonctionnalité X est publiée sur le Canal semi-annuel. L’appareil reçoit la mise à jour de fonctionnalité 30 jours après cette publication sur le Canal semi-annuel et se met à jour en mai.  

   **Paramètres d’expérience utilisateur**
   
   - **Comportement des mises à jour automatiques** : choisissez le mode d’installation des mises à jour automatiques, ainsi que la planification du redémarrage. Pour plus d’informations, consultez [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).

     Le paramètre *Rétablir les valeurs par défaut* restaure les paramètres de mise à jour automatique d’origine sur les machines Windows 10 qui exécutent la *mise à jour d’octobre 2018* ou version ultérieure.  

     - **Fréquence de comportement automatique** : si vous sélectionnez **Installation et redémarrage automatiques à l’heure planifiée** pour les mises à jour, ce paramètre s’affiche. Utilisez ce paramètre pour planifier l’installation des mises à jour, notamment la semaine, le jour et l’heure.

   - **Vérifications de redémarrage** : Activé par défaut. Quand vous redémarrez un appareil, certaines vérifications sont effectuées : utilisateurs actifs, niveau de batterie, jeux en cours d’exécution, etc. Pour ignorer ces vérifications quand vous redémarrez un appareil, sélectionnez **Ignorer**.

   - **Block user from pausing Windows updates** (Empêcher l’utilisateur de suspendre l’installation des mises à jour Windows) : Autorisé par défaut. Utilisez ce paramètre pour refuser ou permettre aux utilisateurs de suspendre l’installation des mises à jour dans les *Paramètres* de leurs ordinateurs. 
      
   - **Mode de téléchargement de l’optimisation de la distribution** : L’optimisation de la distribution n’est plus configurée dans le cadre d’une boucle de mise à jour Windows 10 sous Mises à jour logicielles. L’optimisation de la distribution est maintenant définie via la configuration de l’appareil. Toutefois, les configurations précédentes restent disponibles dans la console. Vous pouvez supprimer ces configurations précédentes en les modifiant pour être *Non configurées*, mais elles ne peuvent pas être changées autrement. Pour éviter les conflits entre l’ancienne et la nouvelle stratégie, consultez [Passer des boucles de mise à jour à l’optimisation de la distribution](delivery-optimization-windows.md#move-from-existing-update-rings-to-delivery-optimization), puis déplacez vos paramètres vers un profil d’optimisation de la distribution. 

5. Une fois que vous avez fini, sélectionnez **OK**. Dans **Créer un anneau de mise à jour**, sélectionnez **Créer**.

Le nouvel anneau de mise à jour s’affiche dans la liste des anneaux de mises à jour.

1. Pour affecter l’anneau, dans la liste des anneaux de mise à jour, sélectionnez un anneau, puis sous l’onglet *Ring name (Nom de l’anneau)*, choisissez **Affectations**.
2. Sous l’onglet suivant, choisissez **Sélectionner des groupes à inclure**, puis choisissez les groupes auxquels vous souhaitez affecter cet anneau.
3. Quand vous avez terminé, choisissez **Sélectionner** pour terminer l’affectation.

## <a name="update-compliance-reporting"></a>Création de rapports sur la conformité des mises à jour
Vous pouvez afficher la conformité des mises à jour dans Intune ou avec une solution gratuite nommée Update Compliance.

### <a name="review-update-compliance-in-intune"></a>Examiner la conformité des mises à jour dans Intune 
<!-- 1352223 --> Consultez un rapport sur la stratégie pour voir l’état de déploiement des boucles de mise à jour Windows 10 que vous avez configurées.

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Mises à jour logicielles** > **Vue d’ensemble**. Vous pouvez voir des informations générales sur l’état des anneaux de mise à jour que vous avez affectés.
3. Ouvrez un des rapports suivants :

   **Pour tous les anneaux de déploiement** :  
   1. Dans **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10**
   2. Dans la section **Surveiller**, choisissez **Par état d’anneau de déploiement de mises à jour**.

   **Pour des anneaux de déploiement spécifiques** :  
   1. Dans **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10**, choisissez l’anneau de déploiement à examiner.
   2. Dans la section **Surveiller**, choisissez les rapports suivants pour voir des informations plus détaillées sur l’anneau de mise à jour :
      - **État de l’appareil**
      - **État de l’utilisateur**

### <a name="review-update-compliance-using-oms"></a>Examiner la conformité des mises à jour en utilisant OMS
Pour surveiller les déploiements de mises à jour Windows 10, vous pouvez utiliser une solution gratuite nommée Update Compliance. Pour plus d’informations, consultez [Analyse des mises à jour Windows avec la conformité de la mise à jour](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor). Lorsque vous utilisez cette solution, vous pouvez déployer un ID commercial dans un des appareils Windows 10 gérés par Intune pour lequel vous souhaitez générer des rapports sur la conformité des mises à jour.

Dans Intune, vous pouvez utiliser les paramètres OMA-URI d’une stratégie personnalisée pour configurer l’ID commercial. Pour plus d’informations, consultez [Paramètres de stratégie Intune pour les appareils Windows 10 dans Microsoft Intune](custom-settings-windows-10.md).   

Le chemin OMA-URI (qui respecte la casse) pour la configuration de l’ID commercial est : ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

Par exemple, vous pouvez utiliser les valeurs suivantes dans **Ajouter ou modifier un paramètre OMA-URI** :

- **Nom du paramètre** : ID commercial Windows Analytics
- **Description du paramètre** : configuration d’un ID commercial pour les solutions Windows Analytics
- **OMA-URI** (sensible à la casse) : ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Type de données** : Chaîne
- **Valeur** : *utilisez le GUID indiqué sous l’onglet Télémétrie Windows dans votre espace de travail OMS*>

![Paramètres OMA-URI - Modifier une ligne](./media/commID-edit.png)

> [!NOTE]
> Pour plus d’informations sur MS DM Server, consultez [Fournisseur de services de configuration DMClient](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="pause-updates"></a>Suspendre les mises à jour
Vous pouvez suspendre la réception des mises à jour qualité ou de fonctionnalités d’un appareil pendant une période allant jusqu’à 35 jours à partir du moment où vous interrompez les mises à jour. Une fois que le nombre maximal de jours s’est écoulé, la fonctionnalité mise en pause expire automatiquement et l’appareil recherche les mises à jour applicables dans Windows Update. Suite à cette analyse, vous pouvez suspendre à nouveau les mises à jour.

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Mises à jour logicielles** > **Anneaux de mise à jour Windows 10**.
3. Dans la liste des anneaux de mise à jour, choisissez l’anneau à suspendre, puis choisissez **...** > **Suspendre la qualité** > ou **Suspendre la mise à jour de la fonctionnalité**, selon le type de mise à jour que vous souhaitez suspendre.

> [!IMPORTANT]
> Quand vous exécutez une commande de suspension, les appareils la reçoivent à leur prochaine connexion au service. Il se peut qu’ils installent une mise à jour planifiée avant d’effectuer la vérification auprès du service.
> En outre, si un appareil cible est désactivé lorsque vous émettez la commande de suspension, lorsque vous l’allumez, il peut télécharger et installer les mises à jour planifiées avant d’effectuer les vérifications avec Intune.

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Désinstaller la dernière version à partir de mises à jour logicielles Windows 10 
Si un problème important se produit sur vos machines Windows 10, vous pouvez choisir de désinstaller (restaurer) la dernière mise à jour des fonctionnalités ou la dernière mise à jour qualité. La désinstallation d’une mise à jour des fonctionnalités ou d’une mise à jour qualité est disponible uniquement pour le canal de maintenance sur lequel se trouve l’appareil. La désinstallation déclenche une stratégie pour restaurer la mise à jour précédente sur vos machines Windows 10. Pour les mises à jour des fonctionnalités en particulier, vous pouvez limiter de 2 à 60 jours la durée pendant laquelle une désinstallation de la version la plus récente peut être appliquée. Pour définir les options de désinstallation de mise à jour logicielle :

1. Dans Intune, sélectionnez **Mises à jour logicielles**.
2. Sélectionnez **Anneaux de mise à jour Windows 10** > sélectionnez un anneau de la mise à jour existant > **Désinstaller**.

> [!NOTE]
> Sur les machines Windows 10, après la restauration réussie de la mise à jour qualité, les utilisateurs finaux continuent à voir la mise à jour répertoriée dans **Paramètres Windows** > **Mises à jour** > **Historique des mises à jour**.

## <a name="windows-holographic-for-business-support"></a>Prise en charge de Windows Holographic for Business

Windows Holographic for Business prend en charge les paramètres suivants :

- **Comportement des mises à jour automatiques**
- **Mises à jour de produit Microsoft**
- **Canal de maintenance** : prend en charge les options **Canal semi-annuel** et **Canal semi-annuel (ciblé)**
