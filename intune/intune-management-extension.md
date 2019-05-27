---
title: Ajouter des scripts PowerShell à des appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Créez et exécutez des scripts PowerShell, affectez la stratégie de script à des groupes Azure Active Directory, utilisez des rapports pour superviser les scripts et consultez les étapes permettant de supprimer les scripts que vous ajoutez sur des appareils Windows 10 dans Microsoft Intune. Consultez également les solutions aux problèmes courants.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/14/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7ea047daca5dad327b431986840a59074614d1
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65732632"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune

Utilisez l’extension de gestion Microsoft Intune pour charger des scripts PowerShell dans Intune en vue de les exécuter sur des appareils Windows 10. L’extension de gestion améliore la gestion des appareils mobiles Windows 10 et facilite l’adoption d’une gestion moderne.

Cette fonctionnalité s’applique à :

- Windows 10 et versions ultérieures

## <a name="move-to-modern-management"></a>Passer à une gestion moderne

Actuellement, l’informatique de l’utilisateur final connaît une transformation numérique. L’informatique classique et traditionnelle se caractérise par une plateforme d’appareils unique, des appareils d’entreprise, des utilisateurs travaillant depuis leur bureau et différents processus informatiques manuels et réactifs. Le lieu de travail moderne compte plusieurs plateformes d’appareils, à la fois personnelles et professionnelles. Il permet aux utilisateurs de travailler où qu’ils se trouvent et offre des processus informatiques automatisés et proactifs.

Les services de gestion des appareils mobiles, tels que Microsoft Intune, peuvent gérer les appareils mobiles et de bureau qui exécutent Windows 10. Le client de gestion Windows 10 intégré communique avec Intune pour effectuer des tâches de gestion d’entreprise. Vous pouvez avoir besoin de certaines tâches, telles que la configuration avancée d’appareils et la résolution de problèmes. Pour la gestion des applications Win32, vous pouvez utiliser la fonctionnalité [Gestion des applications Win32](apps-win32-app-management.md) sur vos appareils Windows 10.

L’extension de gestion Intune vient en complément des fonctionnalités intégrées de gestion des appareils mobiles Windows 10. Vous pouvez créer des scripts PowerShell à exécuter sur les appareils Windows 10. Par exemple, vous pouvez créer un script PowerShell qui effectue une configuration avancée de l’appareil, charge le script dans Intune, affecte le script à un groupe Azure Active Directory (AD) et exécute le script. Vous pouvez ensuite superviser l’état d’exécution du script du début à la fin.

## <a name="prerequisites"></a>Prérequis

L’extension de gestion Intune est soumise aux prérequis suivants :

- Les appareils doivent être joints ou inscrits auprès d’Azure AD. De plus, Azure AD et Intune sont configurés pour l’[inscription automatique](quickstart-setup-auto-enrollment.md). L’extension de gestion Intune prend en charge les appareils joints à Azure AD, les appareils hybrides joints à un domaine Azure AD et les appareils Windows inscrits cogérés.
- Les appareils doivent exécuter Windows 10, version 1607 ou ultérieure.
- L’agent Extension de gestion Intune est installé lorsqu’un script PowerShell ou une application Win32 est déployée dans un groupe de sécurité d’utilisateurs ou d’appareils.

## <a name="create-a-script-policy"></a>Créer une stratégie de script 

1. Dans le [portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.
2. Sélectionnez **Configuration de l’appareil** > **Scripts PowerShell** > **Ajouter**.
3. Entrez les propriétés suivantes :
    - **Nom** : Entrez un nom pour le script PowerShell. 
    - **Description** : Entrez une description pour le script PowerShell. Ce paramètre est facultatif, mais recommandé. 
    - **Emplacement du script** : Accédez au script PowerShell. La taille du script doit être inférieure à 200 Ko (ASCII).
4. Choisissez **Configurer** et entrez les propriétés suivantes :
    - **Exécutez ce script en utilisant les informations d’identification d’ouverture de session** : Sélectionnez **Oui** pour exécuter le script avec les informations d’identification de l’utilisateur sur l’appareil. Choisissez **Non** (valeur par défaut) pour exécuter le script dans le contexte système. De nombreux administrateurs choisissent **Oui**. Si le script doit s’exécuter dans le contexte système, choisissez **Non**.
    - **Appliquer la vérification de la signature du script** : Sélectionnez **Oui** si le script doit être signé par un éditeur approuvé. Sélectionnez **Non** (valeur par défaut) s’il n’est pas nécessaire que le script soit signé. 
    - **Exécuter le script dans un hôte PowerShell 64 bits** : Sélectionnez **Oui** pour exécuter le script dans un hôte PowerShell (PS) 64 bits sur une architecture cliente 64 bits. Sélectionnez **Non** (valeur par défaut) pour exécuter le script dans un hôte PowerShell 32 bits.

      Quand vous choisissez **Oui** ou **Non**, utilisez le tableau suivant pour connaître le comportement nouveau et existant de la stratégie :

      | Exécuter le script dans un hôte PS 64 bits | Architecture cliente | Nouveau script PS | Script PS de la nouvelle stratégie |
      | --- | --- | --- | --- | 
      | Non | 32 bits  | Hôte PS 32 bits pris en charge | S’exécute uniquement dans un hôte PS 32 bits, qui fonctionne sur les architectures 32 bits et 64 bits. |
      | Oui | 64 bits | Exécute le script dans un hôte PS 64 bits pour les architectures 64 bits. Exécuté sur 32 bits, le script s’exécute dans un hôte PS 32 bits. | Exécute le script dans un hôte PS 32 bits. Si ce paramètre passe à 64 bits, le script s’ouvre (il ne s’exécute pas) dans un hôte PS 64 bits, puis signale les résultats. Exécuté sur 32 bits, le script s’exécute dans un hôte PS 32 bits. |

    ![Ajouter et utiliser des scripts PowerShell dans Microsoft Intune](./media/mgmt-extension-add-script.png)
5. Sélectionnez **OK** > **Créer** pour enregistrer le script.

> [!NOTE]
> Le script PowerShell s’exécute sous le privilège Administrateur (par défaut) lorsque le script est défini pour le contexte de l’utilisateur et que l’utilisateur final de l’appareil a des privilèges d’administrateur.

## <a name="assign-the-policy"></a>Affecter la stratégie

1. Dans **Scripts PowerShell**, sélectionnez le script à affecter, puis choisissez **Gérer** > **Affectations**.

    ![Affecter ou déployer un script PowerShell dans des groupes d’appareils dans Microsoft Intune](./media/mgmt-extension-assignments.png)

2. Choisissez **Sélectionner des groupes** pour répertorier les groupes Azure AD disponibles. 
3. Sélectionnez un ou plusieurs groupes contenant les utilisateurs dont les appareils reçoivent le script. Choisissez **Sélectionner** pour affecter la stratégie aux groupes sélectionnés.

> [!NOTE]
> - Les utilisateurs finaux ne sont pas obligés d’être connectés à l’appareil pour exécuter des scripts PowerShell.
> - Dans Intune, les scripts PowerShell peuvent cibler des groupes de sécurité des appareils Azure AD.
> - Dans Intune, les scripts PowerShell peuvent cibler des groupes de sécurité des utilisateurs Azure AD.

Toutes les heures et après chaque redémarrage, le client d’extension de gestion Intune vérifie auprès d’Intune s’il existe de nouveaux scripts ou si des modifications ont été apportées. Une fois la stratégie affectée aux groupes Azure AD, le script PowerShell s’exécute, puis les résultats de l’exécution sont consignés dans un rapport. Une fois que le script s’exécute, il ne se réexécute pas sauf si une modification est apportée au script ou à la stratégie.

## <a name="monitor-run-status"></a>Superviser l’état de l’exécution

Vous pouvez surveiller l’état de l’exécution des scripts PowerShell pour les utilisateurs et les appareils dans le portail Azure.

Dans **Scripts PowerShell**, sélectionnez le script à surveiller, choisissez **Surveiller**, puis choisissez l’un des rapports suivants :

- **État de l’appareil**
- **État de l’utilisateur**

## <a name="troubleshoot-scripts"></a>Résoudre les problèmes liés aux scripts

Les journaux de l’agent sur l’ordinateur client se trouvent généralement dans `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Vous pouvez utiliser [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) pour afficher ces fichiers journaux. 

![Capture d’écran ou exemples de journaux de l’agent cmtrace dans Microsoft Intune](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Supprimer un script

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

#### <a name="issue-powershell-scripts-do-not-run"></a>Problème : Les scripts PowerShell ne s’exécutent pas

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
