---
title: Gérer les PC avec des logiciels clients dans Microsoft Intune - Azure | Microsoft Docs
description: Gérer des PC Windows en installant le logiciel du client Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb67cf2cb17b78c4034c3b73e229e160723d975e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73414391"
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Gérer des PC Windows en tant qu’ordinateurs via le logiciel client Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!WARNING]
> Microsoft a annoncé que le [support de Windows 7 prendra fin le 14 janvier 2020](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020). À cette date, Intune cessera également de prendre en charge les appareils exécutant Windows 7. Microsoft vous recommande vivement de passer à Windows 10 pour éviter toute interruption de service ou de support.
> 
> Pour plus d’informations, consultez [Calendrier des modifications Intune : le support pour Windows 7 touche à sa fin](../fundamentals/whats-new.md#intune-plan-for-change-nearing-end-of-support-for-windows-7).

> [!NOTE]
> Vous pouvez utiliser Microsoft Intune pour gérer les PC Windows comme [appareils mobiles avec la gestion des appareils mobiles (MDM)](../enrollment/windows-enroll.md) ou comme ordinateurs avec le logiciel client Intune, comme décrit ci-dessous. Cependant, Microsoft recommande aux clients [d’utiliser la solution de gestion MDM](../enrollment/windows-enroll.md) quand c’est possible. Pour plus d’informations, consultez [Comparer la gestion des PC Windows en tant qu’ordinateurs ou appareils mobiles](pc-management-comparison.md) 

Intune fournit une solution complète aux organisations pour gérer les appareils mobiles. Intune peut gérer les PC Windows en tant qu’appareils mobiles en utilisant les fonctionnalités de gestion des appareils modernes intégrées au système d’exploitation Windows 10. Pour répondre aux besoins en matière de gestion de votre organisation, Intune peut également gérer les PC Windows en tant qu’ordinateurs via le logiciel client Intune. Cette méthode de gestion utilise des fonctionnalités de gestion des ordinateurs traditionnelles dans le système d’exploitation Windows hérité.

Le logiciel client Intune est idéal pour les PC Windows exécutant des systèmes d’exploitation hérités tels que Windows 7 qui ne peuvent pas être gérés comme des appareils mobiles. Le logiciel client Intune utilise des fonctionnalités de gestion comme une stratégie de groupe pour gérer des PC à partir du cloud.

Intune prend en charge la gestion de 7 000 PC Windows au maximum en tant qu’ordinateurs avec le logiciel client. Pour les déploiements plus importants, gérez les PC Windows 10 comme des appareils mobiles. Chaque version d’Intune et mise à jour de Windows 10 inclut des fonctionnalités de gestion basées sur l’architecture de gestion des appareils mobiles. Nous vous recommandons vivement de mettre en œuvre la gestion des PC Windows 10 comme des appareils mobiles dans votre organisation.

> [!NOTE]
> Vous pouvez gérer des appareils Windows 8.1 et versions ultérieures en tant que PC avec le logiciel client Intune ou comme des appareils mobiles. Vous ne pouvez pas utiliser les deux méthodes sur le même appareil. Réfléchissez bien avant de décider de gérer les PC avec le logiciel client Intune. Cette rubrique concerne uniquement la gestion d’appareils comme PC en exécutant le logiciel client Intune.

## <a name="requirements-for-intune-pc-client-management"></a>Configuration requise pour la gestion du client Intune PC

**Matériel**:  
Voici la configuration matérielle minimale requise pour l’installation du logiciel client Intune :

|Condition requise|Plus d’informations|
|---------------|--------------------|
|Réseau|Le PC sur lequel est installé le client doit disposer d’une connexion à Internet.|
|Processeur et mémoire|Reportez-vous à la configuration requise du processeur et de la RAM pour le système d’exploitation du PC.|
|Espace disque|200 Mo d'espace disponible sur le disque avant l'installation du logiciel client.|

**Logiciels**:  
Voici la configuration logicielle requise pour l’installation du logiciel client :

|Condition requise|Plus d’informations|
|---------------|--------------------|
|Système d'exploitation | Appareil Windows sous Windows 7 SP1 et Windows 8.1 ou une version ultérieure. </br></br>**Les éditions familiales ne sont pas prises en charge.**|
|Autorisations administratives|Le compte qui installe le logiciel client doit disposer des autorisations d’administrateur local sur cet ordinateur.|
|Windows Installer 3.1|Le PC doit disposer de Windows Installer 3.1 au minimum.<br /><br />Pour afficher la version de Windows Installer sur un PC :<br /><br />  Sur le PC, cliquez avec le bouton droit sur **%windir%\System32\msiexec.exe**, puis cliquez sur **Propriétés**.<br /><br />Vous pouvez télécharger la dernière version de Windows Installer à partir de [Windows Installer Redistributables](https://go.microsoft.com/fwlink/?LinkID=234258) sur le site web Microsoft Developer Network.|
|Supprimer les logiciels clients incompatibles|Avant d’installer le logiciel client Intune, désinstallez tous les logiciels clients Configuration Manager, Operations Manager et Service Manager du PC.|

## <a name="deploying-the-intune-software-client"></a>Déploiement du logiciel client Intune
En tant qu’administrateur Intune, vous pouvez mettre le logiciel client Intune à la disposition des utilisateurs de plusieurs façons. Pour obtenir des instructions, consultez [Installer le logiciel client Intune sur des PC Windows](../install-the-windows-pc-client-with-microsoft-intune.md).

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Fonctionnalités de gestion des ordinateurs avec le logiciel client Intune
Dans la plupart des scénarios, vous inscrirez vos appareils avec Microsoft Intune, car cette approche offre davantage de fonctionnalités. Toutefois, vous pouvez également gérer des PC en utilisant le client logiciel Intune, qui fournit les fonctionnalités suivantes :

- **[Gestion des mises à jour logicielles](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)** : Vous pouvez maintenir les PC à jour et choisir à quel moment appliquer les mises à jour.

- **[Stratégie de Pare-feu Windows](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)**  : elle permet de garantir que tous les PC utilisés dans votre entreprise ont un Pare-feu Windows actif et correctement configuré.

- **[Protection contre les programmes malveillants](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)**  : Intune inclut la fonctionnalité Endpoint Protection, qui vous aide à protéger les PC contre les programmes malveillants.

- **[Assistance à distance](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)**  : Intune permet aux utilisateurs de contacter l’équipe du support informatique, qui peut ensuite les aider via une fonctionnalité de Bureau à distance intégrée à Intune (nécessite le logiciel TeamViewer).

- **[Gestion des licences logicielles](../manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)**  : suivez le nombre de licences logicielles disponibles et le nombre de ces licences utilisé.
- **[Déploiement d’applications](add-apps-for-windows-pcs-in-microsoft-intune.md)**  : déployez des logiciels sur les PC que vous gérez. Certaines fonctionnalités de gestion d'applications ne sont pas disponibles lorsque vous gérez des PC avec le client logiciel.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Stratégies et déploiements d’applications pour le logiciel client Intune

Bien que le logiciel client Intune prenne en charge des [fonctionnalités de gestion qui protègent vos PC](policies-to-protect-windows-pcs-in-microsoft-intune.md) en gérant les mises à jour logicielles, le Pare-feu Windows et Endpoint Protection, les PC gérés avec le logiciel client Intune ne peuvent pas être ciblés par d’autres stratégies Intune, notamment les paramètres de stratégie **Windows** spécifiques à la gestion des appareils mobiles.

Quand vous utilisez le logiciel client Intune pour gérer des PC Windows, vous pouvez utiliser uniquement les stratégies figurant dans la section **Gestion de l’ordinateur**.

Intune gère les PC Windows avec des stratégies, comme les objets de stratégie de groupe des services de domaine Active Directory de Windows Server. Si vous gérez des ordinateurs joints à un domaine Active Directory avec Intune, [vérifiez que les stratégies Intune ne sont pas en conflit avec d’autres objets de stratégie de groupe](resolve-gpo-and-microsoft-intune-policy-conflicts.md) utilisés dans votre organisation. Pour en savoir plus, consultez [Stratégie de groupe pour les débutants](https://technet.microsoft.com/library/hh147307.aspx).

  ![Sélection d'un modèle pour la nouvelle stratégie de PC Windows](./media/manage-windows-pcs-with-microsoft-intune/select-template-for-pc-policy.png)

Lors du déploiement d’applications, vous pouvez utiliser uniquement le programme Windows Installer (.exe, .msi).

  ![Sélection de la plateforme et de l’emplacement des fichiers logiciels du client PC](./media/manage-windows-pcs-with-microsoft-intune/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Tâches courantes pour les PC Windows

Vous pouvez utiliser la console d’administration Intune pour effectuer d’autres tâches courantes de gestion des ordinateurs sur les PC Windows sur lesquels le client est installé :
- [Utiliser des stratégies pour simplifier la gestion des PC](use-policies-to-simplify-windows-pc-management.md) : Décrit les stratégies de **gestion de l’ordinateur** d’Intune et répertorie les paramètres pour Microsoft Intune Center.

- [Afficher l’inventaire logiciel et matériel pour les PC Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) : Explique comment créer un rapport qui répertorie les informations sur les capacités matérielles des PC et les logiciels qui y sont installés. Explique également comment actualiser l’inventaire des PC pour vérifier qu’il est à jour.
- [Mettre hors service un PC Windows](retire-a-windows-pc-with-microsoft-intune.md) : Répertorie les étapes pour mettre hors service un PC Windows et décrit les conséquences d’une telle opération.
- [Gérer la liaison utilisateur-appareil pour les PC Windows](../manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) : Explique quand et comment vous devez associer un utilisateur à un ordinateur avant de déployer des logiciels sur l’utilisateur.
- [Demander et fournir une assistance à distance pour les PC Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) : Explique comment les utilisateurs de PC Intune obtiennent l’assistance à distance que vous proposez et décrit les conditions préalables ainsi que le programme d’installation de TeamViewer.

Pour plus d’informations sur les tâches ci-dessus, consultez les [tâches courantes de gestion des ordinateurs](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Limitations de la gestion du logiciel client Intune

Certaines options de gestion, qui peuvent être utilisées pour gérer des PC comme des appareils mobiles, ne peuvent pas être utilisées pour les PC qui sont gérés par le logiciel client Intune :

- Réinitialisation complète (la réinitialisation sélective est disponible)
- Accès conditionnel

Notez également que, dans la console d’administration Intune, certaines sections, telles que **Mises à jour**, **Protection** et **Licences** apparaissent uniquement si vous avez inscrit des appareils à l’aide du logiciel client Intune.

  ![Éléments de la console administrateur qui s’affichent uniquement pour le client PC](./media/manage-windows-pcs-with-microsoft-intune/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>Aide à la résolution des problèmes

Le logiciel client Intune s’exécute généralement en mode silencieux en arrière-plan sans avoir besoin de l’intervention de l’utilisateur ni de dépannage. Si vous avez besoin de résoudre des problèmes de gestion de PC, vous pouvez vérifier les journaux. Le logiciel client Intune et les journaux correspondants sont installés dans le répertoire %Program Files%\Microsoft\OnlineManagement.

Pour plus d’informations sur l’inscription des appareils avec Microsoft Intune, vous pouvez également consulter [Inscription des appareils](../enrollment/device-enrollment.md).
