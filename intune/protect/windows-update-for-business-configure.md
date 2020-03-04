---
title: Configurer Windows Update pour Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Gérer les mises à jour logicielles de Windows 10 à l’aide des anneaux de mise à jour et de la stratégie de mise à jour des fonctionnalités. Vous pouvez vérifier la conformité et suspendre l’installation des mises à jour avec les paramètres de Windows Update pour Entreprise à l’aide de Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9245ca028bdb5589df8c76b10560d9130a1108c
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181719"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>Gérer les mises à jour logicielles de Windows 10 dans Intune

Utilisez Intune pour gérer l’installation des mises à jour logicielles de Windows 10 à partir de Windows Update pour Entreprise.

Avec Windows Update pour Entreprise, vous simplifiez l’expérience utilisateur de gestion des mises à jour. Vous n’avez pas besoin d’approuver des mises à jour individuelles pour des groupes d’appareils. Vous pouvez gérer les risques dans vos environnements en configurant une stratégie de lancement des mises à jour. Intune vous permet de [configurer les paramètres de mise à jour](windows-update-settings.md) des appareils et de reporter l’installation des mises à jour. Vous pouvez également empêcher les appareils d’installer des fonctionnalités à partir de nouvelles versions de Windows afin qu’ils restent stables tout en les autorisant à continuer à installer les mises à jour de qualité et de sécurité.

Intune stocke uniquement les affectations de stratégie de mise à jour, pas les mises à jour proprement dites. Les appareils accèdent directement à Windows Update pour les mises à jour.

Intune fournit les types de stratégies suivants pour gérer les mises à jour :

- **Anneau de mise à jour de Windows 10** : cette stratégie est une collection de paramètres qui configure quand les mises à jour Windows 10 sont installées.

- **Mises à jour des fonctionnalités Windows 10 (préversion publique)**  : Cette stratégie met les appareils à la version de Windows que vous spécifiez et gèle l’ensemble des fonctionnalités sur ces appareils jusqu’à ce que vous choisissiez de les mettre à jour vers une version ultérieure de Windows.  Alors que la version des fonctionnalités reste statique, les appareils peuvent continuer à installer des mises à jour de qualité et de sécurité disponibles pour leur version de fonctionnalité.

Vous attribuez des stratégies pour les anneaux de mise à jour Windows 10 et des mises à jour de fonctionnalités Windows 10 à des groupes d’appareils. Vous pouvez utiliser les deux types de stratégies dans le même environnement Intune pour gérer les mises à jour logicielles pour vos appareils Windows 10 et créer une stratégie de mise à jour qui reflète les besoins de votre entreprise.

Pour plus d’informations, consultez [Gérer les mises à jour à l’aide de Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="prerequisites"></a>Prérequis

Les conditions préalables suivantes doivent être remplies pour utiliser des mises à jour Windows pour des appareils Windows 10 dans Intune.

- Les PC Windows 10 doivent exécuter les versions suivantes de Windows 10 :
  - **Anneaux de mise à jour Windows 10** : version 1607 ou ultérieure
  - **Mise à jour de fonctionnalités Windows 10** : version 1703 ou ultérieure

- Windows Update prend en charge les éditions de Windows 10 suivantes :
  - Windows 10
  - Windows 10 Collaboration-pour appareils Surface Hub (ne prend pas en charge les *mises à jour de fonctionnalités Windows 10*)
  - Windows Holographic for Business

    Windows Holographic for Business prend en charge un sous-ensemble de paramètres pour les mises à jour Windows, notamment :
    - **Comportement des mises à jour automatiques**
    - **Mises à jour de produit Microsoft**
    - **Canal de maintenance** : Prend en charge les options **Canal semi-annuel** et **Canal semi-annuel (ciblé)** . Pour plus d’informations, consultez [Gérer Windows Holographic](../fundamentals/windows-holographic-for-business.md).

  > [!NOTE]
  > **Versions et éditions non prises en charge** :
  > - Windows 10 Mobile  
  > - Windows 10 Enterprise LTSC. Windows Update for Business (WUfB) ne prend actuellement pas en charge les versions *Long Term Service Channel (LTSC)* . Prévoyez d'utiliser d'autres méthodes de mise à jour, notamment WSUS ou Configuration Manager.

- Sur les appareils Windows, le paramètre **Commentaires et diagnostics** > **Données de diagnostic et d’utilisation** doit être défini sur **De base**, **Amélioré** ou **Complet**.

  Vous pouvez configurer manuellement le paramètre *Données de diagnostic et d’utilisation* pour les appareils Windows 10, ou utiliser un profil de restriction d’appareils Intune pour Windows 10 et versions ultérieures. Si vous utilisez un profil de restriction d’appareils, définissez la valeur de [restriction d’appareils](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) du paramètre **Partager les données d'utilisation** sur au moins **De base**. Ce paramètre se trouve dans la catégorie **Création de rapports et les données de télémétrie** lorsque vous configurez une stratégie de restriction d’appareils pour Windows 10 ou version ultérieure.

  Pour plus d’informations sur les profils d’appareils, consultez [Configurer des paramètres de restriction d’appareils](../configuration/device-restrictions-configure.md).

## <a name="windows-10-update-rings"></a>Anneaux des mise à jour Windows 10

Créez des anneaux de mise à jour qui spécifient comment et quand Windows en tant que service met à jour vos appareils Windows 10 avec des mises à jour de fonctionnalité et de sécurité. Avec Windows 10, les nouvelles mises à jour de fonctionnalités et mises à jour qualité incluent le contenu de toutes les mises à jour précédentes. Du moment que vous avez installé la dernière mise à jour, vous savez que vos appareils Windows 10 sont à jour. À la différence des versions précédentes de Windows, vous devez maintenant installer la mise à jour complète au lieu d’une partie seulement.

Les anneaux de mise à jour Windows 10 prennent en charge les [balises d’étendue](../fundamentals/scope-tags.md). Vous pouvez utiliser des balises d’étendue avec des anneaux de mise à jour pour vous aider à filtrer et à gérer des ensembles de configurations que vous utilisez.

### <a name="create-and-assign-update-rings"></a>Créer et affecter des anneaux de mise à jour

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Windows** > **Anneaux de mise à jour Windows 10** > **Créer**.

3. Sous *De base*, spécifiez un nom, une description (facultatif), puis sélectionnez **Suivant**.
  ![Créer un anneau de mise à jour](./media/windows-update-for-business-configure/basics-tab.png)

4. Sous **Paramètres d’anneau de mise à jour**, configurez les paramètres conformément aux besoins de votre entreprise. Pour plus d’informations sur les paramètres disponibles, consultez [Paramètres de Windows Update](../protect/windows-update-settings.md). Après avoir configuré les paramètres *Mise à jour et Expérience utilisateur*, sélectionnez **Suivant**.

5. Sous **Balises d’étendue**, sélectionnez **+ Sélectionner des balises d’étendue** pour ouvrir le volet *Sélectionner des balises* si vous voulez appliquer des balises d’étendue à l’anneau de mise à jour. Choisissez une ou plusieurs balises, puis cliquez sur **Sélectionner** pour les ajouter à l’anneau de mise à jour et revenir au volet *Balises d’étendue*.

   Quand vous êtes prêt, sélectionnez **Suivant** pour accéder à *Affectations*.

6. Sous **Affectations**, choisissez **+ Sélectionner les groupes à inclure**, puis affectez l’anneau de mise à jour à un ou plusieurs groupes. Utilisez le paramètre **+ Sélectionner les groupes à exclure** pour affiner l’affectation. Sélectionnez **Suivant** pour continuer.

7. Sous **Vérifier + créer**, vérifiez les paramètres, puis sélectionnez **Créer** quand vous êtes prêt à enregistrer votre anneau de mise à jour Windows 10. Votre nouvel anneau de mise à jour s’affiche dans la liste des anneaux de mise à jour.

### <a name="manage-your-windows-10-update-rings"></a>Gérer vos anneaux de mise à jour Windows 10

Dans le portail, accédez à **Appareils** > **Windows** > **Anneaux de mise à jour Windows 10** et sélectionnez la stratégie que vous souhaitez gérer.  La stratégie s’ouvre sur sa page **Vue d’ensemble**.

À partir de cette page, vous pouvez afficher l’état d’attribution des annaux et sélectionner les actions suivantes en haut du volet Vue d’ensemble pour gérer l’anneau de mise à jour :

- [Supprimer](#delete)
- [Pause](#pause)
- [Reprendre](#resume)
- [Prolonger](#extend)
- [Désinstaller](#uninstall)

![Actions disponibles](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>Supprimer

Sélectionnez **Supprimer** pour arrêter l’application des paramètres de l’anneau de mise à jour Windows 10 sélectionné. La suppression d’un anneau supprime sa configuration Intune afin qu’Intune n’applique plus ces paramètres.

La suppression d’un anneau d’Intune ne modifie pas les paramètres sur les appareils auxquels l’anneau de mise à jour a été attribué.  L’appareil conserve ses paramètres actuels. Les appareils ne maintiennent pas un enregistrement historique des paramètres qu’ils détenaient précédemment. Les appareils peuvent également recevoir des paramètres d’anneaux de mise à jour supplémentaires qui restent actifs.

##### <a name="to-delete-a-ring"></a>Pour supprimer un anneau

1. Dans la page Vue d’ensemble d’un anneau de mise à jour, sélectionnez **Supprimer**.
2. Sélectionnez **OK**.

#### <a name="pause"></a>Suspendre

Sélectionnez **Suspendre** pour empêcher les appareils attribués de recevoir des mises à jour de fonctionnalité ou de qualité pendant une période jusqu’à 35 jours à partir du moment où vous suspendez l’anneau. Une fois que le nombre maximal de jours s’est écoulé, la fonctionnalité mise en pause expire automatiquement et l’appareil recherche les mises à jour applicables dans Windows Update. Suite à cette analyse, vous pouvez à nouveau suspendre les mises à jour.
Si vous reprenez un anneau de mise à jour suspendu et que vous le suspendez à nouveau, la période de suspension est réinitialisée sur 35 jours.

##### <a name="to-pause-a-ring"></a>Pour suspendre un anneau

1. Dans la page Vue d’ensemble d’un anneau de mise à jour, sélectionnez **Suspendre**.
2. Sélectionnez **Fonctionnalité** ou **Qualité** pour suspendre ce type de mise à jour, puis sélectionnez **OK**.
3. Après la suspension d’un type de mise à jour, vous pouvez sélectionner Suspendre à nouveau pour suspendre l’autre type de mise à jour.

Lorsqu’un type de mise à jour est suspendu, le volet Vue d’ensemble de cet anneau affiche le nombre de jours restants avant la reprise de ce type de mise à jour.

> [!IMPORTANT]
> Lorsque vous exécutez une commande de suspension, les appareils la reçoivent à leur prochaine connexion au service. Il se peut qu’ils installent une mise à jour planifiée avant d’effectuer la vérification auprès du service. En outre, si un appareil cible est désactivé lorsque vous émettez la commande de suspension, lorsque vous l’allumez, il peut télécharger et installer les mises à jour planifiées avant d’effectuer les vérifications avec Intune.

#### <a name="resume"></a>Reprendre

Lorsqu’un anneau de mise à jour est suspendu, vous pouvez sélectionner **Reprendre** pour restaurer les mises à jour de fonctionnalité et de qualité pour cet anneau. Lorsque vous reprenez un anneau de mise à jour, vous pouvez le suspendre à nouveau.

##### <a name="to-resume-a-ring"></a>Pour reprendre un anneau

1. Dans la page Vue d’ensemble d’un anneau de mise à jour suspendu, sélectionnez **Reprendre**.
2. Sélectionnez parmi les options disponibles pour reprendre les mises à jour de **fonctionnalité** ou de **qualité**, puis sélectionnez **OK**.
3. Après la reprise d’un type de mise à jour, vous pouvez sélectionner Reprendre à nouveau pour reprendre l’autre type de mise à jour.

#### <a name="extend"></a>Extend  

Lorsqu’un anneau de mise à jour est suspendu, vous pouvez sélectionner **Prolonger** pour réinitialiser la période de suspension des mises à jour de fonctionnalité et de qualité de cet anneau de mise à jour sur 35 jours.

##### <a name="to-extend-the-pause-period-for-a-ring"></a>Pour prolonger la période de suspension d’un anneau

1. Dans la page Vue d’ensemble d’un anneau de mise à jour suspendu, sélectionnez **Prolonger**.
2. Sélectionnez parmi les options disponibles pour reprendre les mises à jour de **fonctionnalité** ou de **qualité**, puis sélectionnez **OK**.
3. Lorsque la suspension d’un type de mise à jour est prolongée, vous pouvez sélectionner Prolonger à nouveau pour prolonger l’autre type de mise à jour.

#### <a name="uninstall"></a>Désinstaller  

Un administrateur Intune peut utiliser **Désinstaller** pour désinstaller (restaurer) la dernière mise à jour de *fonctionnalité* ou la dernière mise à jour de *qualité* d’un anneau de mise à jour actif ou suspendu. Après la désinstallation d’un type, vous pouvez désinstaller l’autre type. Intune ne prend pas en charge ni ne gère pas la capacité des utilisateurs à désinstaller les mises à jour.  

> [!IMPORTANT]
> Lorsque vous utilisez l’option *Désinstaller*, Intune transmet immédiatement la demande de désinstallation aux appareils.
>
> - Les appareils Windows commencent la suppression des mises à jour dès qu’elles reçoivent la modification de la stratégie Intune. La suppression des mises à jour n’est pas limitée aux planifications de maintenance, même lorsqu’elle est configurée dans le cadre de l’anneau de mise à jour.
> - Si la suppression des mises à jour nécessite un redémarrage de l’appareil, l’appareil redémarre sans offrir à l’utilisateur de l’appareil une option de délai.

Pour que la désinstallation réussisse :

- Un appareil doit exécuter la mise à jour d’avril 2018 de Windows 10 (version 1803) ou ultérieure.

La dernière mise à jour doit être installée sur un appareil. Les mises à jour étant cumulatives, les appareils qui installent la dernière mise à jour disposeront de la mise à jour de fonctionnalité et de qualité la plus récente. Un exemple du moment où vous pouvez utiliser cette option consiste à restaurer la dernière mise à jour si vous détectez un problème de rupture sur vos machines Windows 10.

Tenez compte des éléments suivants lorsque vous utilisez Désinstaller :

- La désinstallation d’une mise à jour des fonctionnalités ou d’une mise à jour qualité est disponible uniquement pour le canal de maintenance sur lequel se trouve l’appareil.

- L’utilisation de la désinstallation de mises à jour de fonctionnalité ou de qualité déclenche une stratégie pour restaurer la mise à jour précédente sur vos machines Windows 10.

- Sur un appareil Windows 10, après une restauration réussie de la mise à jour de qualité, les utilisateurs de l’appareil continuent à voir la mise à jour répertoriée dans **Paramètres Windows** > **Mises à jour** > **Historique des mises à jour**.

- Pour les mises à jour de fonctionnalités en particulier, le temps dont vous disposez pour désinstaller la mise à jour est limitée à 2 à 60 jours. Cette période est configurée par le paramètre Mise à jour des anneaux de mise à jour **Définir la période de désinstallation de la mise à jour des fonctionnalités (2 à 60 jours)** . Vous ne pouvez pas restaurer une mise à jour de fonctionnalité qui a été installée sur un appareil après une durée d’installation supérieure à la période de désinstallation configurée.

  Par exemple, considérez un anneau de mise à jour avec une période de désinstallation des mises à jour de fonctionnalités de 20 jours. Après 25 jours, vous décidez d’annuler la dernière mise à jour de fonctionnalité et d’utiliser l’option de désinstallation.  Les appareils qui ont installé la mise à jour de fonctionnalité il y a plus de 20 jours ne peuvent pas la désinstaller, puisqu’ils ont supprimé les bits nécessaires dans le cadre de leur maintenance. Cependant, les appareils qui ont installé la mise à jour des fonctionnalités il y a 19 jours maximum peuvent désinstaller la mise à jour s’ils ont réussi à s’enregistrer pour recevoir la commande de désinstallation avant que la période de désinstallation de 20 jours n’ait expiré.

Pour plus d’informations sur les stratégies Windows Update, consultez [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (Mettre à jour CSP) dans la documentation de gestion de client Windows.

##### <a name="to-uninstall-the-latest-windows-10-update"></a>Pour désinstaller la dernière mise à jour de Windows 10

1. Dans la page Vue d’ensemble d’un anneau de mise à jour suspendu, sélectionnez **Désinstaller**.
2. Sélectionnez parmi les options disponibles pour désinstaller les mises à jour de **fonctionnalité** ou de **qualité**, puis sélectionnez **OK**.
3. Après le déclenchement de la désinstallation d’un type de mise à jour, vous pouvez sélectionner Désinstaller à nouveau pour désinstaller le type de mise à jour restant.

## <a name="windows-10-feature-updates"></a>Mises à jour des fonctionnalités de Windows 10

*Cette fonctionnalité est disponible en préversion publique.*

Avec *Mises à jour des fonctionnalités de Windows 10*, vous sélectionnez la version de fonctionnalité Windows à laquelle vous souhaitez que les appareils soient conservés, comme Windows 10 version 1803 ou version 1809. Vous pouvez définir un niveau de fonctionnalité 1803 ou une version ultérieure.

Quand un appareil reçoit une stratégie de mise à jour des fonctionnalités de Windows 10 :

- l’appareil est mis à jour vers la version de Windows spécifiée dans la stratégie. Un appareil qui exécute déjà une version ultérieure de Windows conserve sa version actuelle. En figeant la version, l’ensemble des fonctionnalités des appareils reste stable pendant la durée de la stratégie.

- Alors que la version installée de Windows reste définie, les appareils peuvent toujours recevoir et installer des mises à jour de qualité et de sécurité pour leur version de Windows pendant la durée de la prise en charge de cette version, ce qui vous permet de maintenir les appareils à jour et sécurisés.

- Contrairement à l’utilisation de *Suspendre* avec un anneau de mise à jour, qui expire au bout de 35 jours, la stratégie de mise à jour des fonctionnalités de Windows 10 reste en vigueur. Tant que vous ne modifiez pas ou ne supprimez pas la stratégie de mise à jour des fonctionnalités de Windows 10, les appareils n’installent pas une nouvelle version de Windows. Si vous modifiez la stratégie pour spécifier une version plus récente, les appareils peuvent alors installer les fonctionnalités à partir de cette version de Windows.

### <a name="prerequisites-for-windows-10-feature-updates"></a>Conditions préalables pour les mises à jour des fonctionnalités Windows 10

Les conditions préalables suivantes doivent être remplies pour utiliser les mises à jour des fonctionnalités Windows 10 dans Intune.

- Les appareils doivent être inscrits dans Intune MDM et Azure AD joint ou Azure AD enregistré.
- Pour utiliser la stratégie de mise à jour des fonctionnalités avec Intune, les appareils doivent avoir la télémétrie activée, avec un paramètre minimal [*de base*](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry). La télémétrie est configurée sous *Création de rapports et télémétrie* dans le cadre d’une [stratégie de restriction des appareils](../configuration/device-restrictions-configure.md).
  
  Les appareils qui reçoivent une stratégie de mise à jour des fonctionnalités et dont la télémétrie est définie comme *Non configurée*, donc désactivée, peuvent installer une version de Windows plus récente que celle définie dans la stratégie de mise à jour des fonctionnalités. La condition préalable requise pour exiger la télémétrie est en cours d’examen, car cette fonctionnalité évolue vers une disponibilité générale.

### <a name="limitations-for-windows-10-feature-updates"></a>Limitations pour les mises à jour des fonctionnalités de Windows 10

- Lorsque vous déployez une *mise à jour de fonctionnalité Windows 10* sur un appareil qui reçoit également une stratégie d’ *anneau de mise à jour Windows10*, passez en revue les configurations suivantes de l’anneau de mise à jour :
  - La **période de report des mises à jour des fonctionnalités (jours)** doit être définie sur **0**.
  - Les mises à jour des fonctionnalités de l’anneau de mise à jour doivent être *en cours d’exécution*. Elles ne doivent pas être suspendues.

- Les stratégies de mise à jour des fonctionnalités Windows 10 ne peuvent pas être appliquées au cours de l’expérience OOBE (out of box experience) AutoPilot et s’appliquent uniquement à la première analyse de Windows Update une fois que l’appareil a été provisionné (généralement un jour après).

### <a name="create-and-assign-windows-10-feature-updates"></a>Créer et attribuer des mises à jour de fonctionnalités Windows 10

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Windows** > **Mises à jour des fonctionnalités Windows 10** > **Créer**.

3. Sous **De base**, spécifiez un nom, une description (facultatif) et, pour **Mise à jour de fonctionnalité à déployer**, sélectionnez la version de Windows avec l’ensemble de fonctionnalités souhaité, puis sélectionnez **suivant**.

4. Sous **Affectations**, choisissez **+ Sélectionner les groupes à inclure**, puis attribuez le déploiement de mise à jour des fonctionnalités à un ou plusieurs groupes. Sélectionnez **Suivant** pour continuer.

5. Sous **Vérifier + créer**, vérifiez les paramètres et sélectionnez **Créer** quand vous êtes prêt à enregistrer la stratégie des mises à jour des fonctionnalités de Windows 10.  

### <a name="manage-windows-10-feature-updates"></a>Gérer les mises à jour des fonctionnalités de Windows 10

Dans le centre d’administration, accédez à **Appareils** > **Windows** > **Mises à jour des fonctionnalités de Windows 10** et sélectionnez la stratégie que vous souhaitez gérer. La stratégie s’ouvre sur son volet **Vue d’ensemble**.

Dans ce volet, vous pouvez :

- Sélectionnez **supprimer** pour supprimer la stratégie d’Intune et des appareils.
- Sélectionnez **Propriétés** pour modifier le déploiement.  Dans le volet *Propriétés*, sélectionnez **Modifier** pour ouvrir les *paramètres de déploiement ou les affectations*, où vous pouvez ensuite modifier le déploiement.
- Sélectionnez **État des mises à jour de l’utilisateur final** pour afficher des informations sur la stratégie.

## <a name="validation-and-reporting-for-windows-10-updates"></a>Validation et création de rapports pour les mises à jour Windows 10

Pour les anneaux de mise à jour Windows 10 et les mises à jour des fonctionnalités Windows 10, utilisez les [rapports de conformité Intune pour les mises à jour](../windows-update-compliance-reports.md) afin de surveiller l'état de mise à jour des appareils. Cette solution utilise l’option [Conformité des mises à jour](https://docs.microsoft.com/windows/deployment/update/update-compliance-monitor) avec votre abonnement Azure.

## <a name="next-steps"></a>Étapes suivantes

[Paramètres de Windows Update pris en charge par Intune](../windows-update-settings.md)

[Résolution des problèmes liés aux anneaux de mise à jour Windows 10](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)
