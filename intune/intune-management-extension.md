---
title: Ajouter des scripts PowerShell dans Microsoft Intune sur des appareils Windows 10 - Azure | Microsoft Docs
description: Ajouter des scripts PowerShell, attribuer la stratégie de script à des groupes Azure Active Directory, utiliser des rapports pour surveiller les scripts, et consulter les étapes permettant de supprimer les scripts que vous ajoutez sur des appareils Windows 10 dans Microsoft Intune. Consultez également les solutions aux problèmes courants.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 444fd63f8c582d35891dfa5aedb9eadd6626e541
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303393"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Gérer des scripts PowerShell dans Intune pour des appareils Windows 10

Utilisez l’extension de gestion Intune pour charger des scripts PowerShell dans Intune en vue de les exécuter sur des appareils Windows 10. L’extension de gestion améliore la gestion des appareils mobiles Windows 10 et facilite l’adoption d’une gestion moderne.

## <a name="moving-to-modern-management"></a>Vers une gestion moderne

Actuellement, l’informatique de l’utilisateur final connaît une transformation numérique. L’informatique classique et traditionnelle se caractérise par une plateforme d’appareils unique, des appareils d’entreprise, des utilisateurs travaillant depuis leur bureau et de nombreux processus informatiques manuels et réactifs. Le lieu de travail moderne compte plusieurs plateformes d’appareils, à la fois personnelles et professionnelles. Il permet aux utilisateurs de travailler où qu’ils se trouvent et offre des processus informatiques automatisés et proactifs.

Les services de gestion des appareils mobiles, tels que Microsoft Intune, peuvent gérer les appareils mobiles et de bureau qui exécutent Windows 10. Le client de gestion Windows 10 intégré communique avec Intune pour effectuer des tâches de gestion d’entreprise. Vous pouvez avoir besoin d’effectuer certaines tâches, telles que la configuration avancée des appareils, le dépannage et la gestion des applications Win32 héritée, qui ne sont pas disponibles dans la gestion des appareils mobiles Windows 10. Pour cela, vous pouvez exécuter le logiciel client Intune sur vos appareils Windows 10. L’article [Comparer la gestion des PC Windows en tant qu’ordinateurs ou appareils mobiles](pc-management-comparison.md) est très utile.

L’extension de gestion Intune vient en complément des fonctionnalités intégrées de gestion des appareils mobiles Windows 10. Vous pouvez créer des scripts PowerShell à exécuter sur les appareils Windows 10. Par exemple, vous pouvez créer un script PowerShell qui installe une application Win32 héritée, charger le script dans Intune, affecter le script à un groupe Azure Active Directory (AD) et exécuter le script. Vous pouvez ensuite superviser l’état d’exécution du script du début à la fin.

## <a name="prerequisites"></a>Prérequis

L’extension de gestion Intune est soumise aux prérequis suivants :

- Les appareils doivent être joints ou inscrits auprès d’Azure AD. De plus, Azure AD est configuré pour l’[inscription automatique dans Intune](windows-enroll.md#enable-windows-10-automatic-enrollment). L’extension de gestion Intune prend en charge les appareils joints à Azure AD, les appareils joints à un domaine hybrides et les appareils Windows inscrits cogérés.
- Les appareils doivent exécuter Windows 10, version 1607 ou ultérieure.
- L’agent Extension de gestion Intune est installé lorsqu’un script PowerShell ou une application Win32 est déployée dans un groupe de sécurité d’utilisateurs ou d’appareils.

## <a name="create-a-powershell-script-policy"></a>Créer une stratégie de script PowerShell 

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Scripts PowerShell** > **Ajouter**.
3. Entrez un **Nom** et une **Description** pour le script PowerShell. Pour l’**Emplacement du script**, accédez au script PowerShell. La taille du script doit être inférieure à 200 Ko (ASCII) ou 100 Ko (Unicode).
4. Choisissez **Configurer**. Indiquez ensuite si vous souhaitez exécuter le script avec les informations d’identification de l’utilisateur sur l’appareil (**Oui**) ou dans le contexte du système (**Non**). Par défaut, le script s’exécute dans le contexte du système. Sélectionnez **Oui**, sauf si le script doit s’exécuter dans le contexte du système. 
  ![Volet Ajouter un script PowerShell](./media/mgmt-extension-add-script.png)
5. Indiquez si le script doit être signé par un éditeur approuvé (**Oui**). Par défaut, il n’est pas nécessaire que le script soit signé. 
6. Sélectionnez **OK**, puis **Créer** pour enregistrer le script.

## <a name="assign-a-powershell-script-policy"></a>Assigner une stratégie de script PowerShell

1. Dans **Scripts PowerShell**, sélectionnez le script à affecter, puis choisissez **Gérer** > **Affectations**.

    ![Volet Ajouter un script PowerShell](./media/mgmt-extension-assignments.png)

2. Choisissez **Sélectionner des groupes** pour répertorier les groupes Azure AD disponibles. 
3. Sélectionnez un ou plusieurs groupes contenant les utilisateurs dont les appareils reçoivent le script. Choisissez **Sélectionner** pour affecter la stratégie aux groupes sélectionnés.

> [!NOTE]
> - Les utilisateurs finaux ne sont pas obligés d’être connectés à l’appareil pour exécuter des scripts PowerShell.
> - Dans Intune, les scripts PowerShell peuvent cibler des groupes de sécurité des appareils Azure AD.
> - Dans Intune, les scripts PowerShell peuvent cibler des groupes de sécurité des utilisateurs Azure AD.

Le client d’extension de gestion Intune vérifie Intune une fois par heure. Une fois la stratégie affectée aux groupes Azure AD, le script PowerShell s’exécute, puis les résultats de l’exécution sont consignés dans un rapport.

## <a name="monitor-run-status-for-powershell-scripts"></a>Surveiller l’état de l’exécution des scripts PowerShell

Vous pouvez surveiller l’état de l’exécution des scripts PowerShell pour les utilisateurs et les appareils dans le portail Azure.

Dans **Scripts PowerShell**, sélectionnez le script à surveiller, choisissez **Surveiller**, puis choisissez l’un des rapports suivants :

- **État de l’appareil**
- **État de l’utilisateur**

## <a name="troubleshoot-powershell-scripts"></a>Résoudre les problèmes des scripts PowerShell

Les journaux de l’agent sur l’ordinateur client se trouvent généralement dans `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Vous pouvez utiliser [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) pour afficher ces fichiers journaux. 

![Capture d’écran des journaux de l’agent](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>Supprimer un script PowerShell

Dans **Scripts PowerShell**, cliquez avec le bouton droit sur le script, puis sélectionnez **Supprimer**.

## <a name="common-issues-and-resolutions"></a>Solutions aux problèmes courants

Les scripts PowerShell ne s’exécutent pas à chaque connexion. Ils s’exécutent uniquement après le redémarrage, ou si le service **Extension de gestion Microsoft Intune** est redémarré. Toutes les heures, le client d’extension de gestion Intune vérifie la présence de modifications de script ou de stratégie dans Intune.

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problème : Impossible de télécharger l’extension de gestion Intune

**Solutions possibles :**

- Vérifiez que les appareils ont bien été inscrits automatiquement dans Azure AD. Pour le vérifier : 

  1. Accédez à **Paramètres** > **Comptes** > **Accès scolaire ou professionnel**.
  2. Sélectionnez le compte joint > **Infos**.
  3. Sous le **rapport Diagnostics avancés**, sélectionnez **Créer un rapport**.
  4. Ouvrez `MDMDiagReport` dans un navigateur web et accédez à la section **Enrolled configuration sources** (Sources de configuration inscrites).
  5. Recherchez la propriété **MDMDeviceWithAAD**. Si cette propriété n’existe pas, votre appareil n’a pas été inscrit automatiquement.

    La section [Activer l’inscription automatique Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment) fournit les étapes nécessaires.

#### <a name="issue-the-powershell-scripts-do-not-run"></a>Problème : Les scripts PowerShell ne s’exécutent pas

**Solutions possibles :**

- Vérifiez que l’extension de gestion Intune a été téléchargée à l’emplacement suivant : `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Les scripts ne s’exécutent pas sur les appareils Surface Hub.
- Vérifiez la présence d’erreurs dans les journaux situés sous `\ProgramData\Microsoft\IntuneManagementExtension\Logs`.
- En cas de problème lié aux autorisations, vérifiez que les propriétés du script PowerShell sont bien définies sur `Run this script using the logged on credentials`. Vérifiez également que l’utilisateur connecté dispose des autorisations nécessaires pour exécuter le script.
- Pour isoler les problèmes de script, exécutez un exemple de script. Par exemple, créez le répertoire `C:\Scripts` et accordez à tout le monde un contrôle complet. Exécutez le script suivant :

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  Si cela réussit, le fichier output.txt doit être créé et doit inclure le texte « Script worked » (Le script a fonctionné).

- Pour tester l’exécution des scripts sans Intune, exécutez les scripts localement sous le contexte système à l’aide de l’[outil psexec](https://docs.microsoft.com/sysinternals/downloads/psexec) :

  `psexec -i -s`

## <a name="next-steps"></a>Étapes suivantes

[Supervisez](device-profile-monitor.md) et [dépannez](device-profile-troubleshoot.md) vos profils.
