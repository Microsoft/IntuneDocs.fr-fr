---
title: Ajouter des scripts PowerShell à des appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Créez et exécutez des scripts PowerShell, affectez la stratégie de script à des groupes Azure Active Directory, utilisez des rapports pour superviser les scripts et consultez les étapes permettant de supprimer les scripts que vous ajoutez sur des appareils Windows 10 dans Microsoft Intune. Consultez également les solutions aux problèmes courants.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3da8e89679f974c7d91cf19ae37365f75217d153
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548025"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Utiliser des scripts PowerShell sur des appareils Windows 10 dans Intune

Utilisez l’extension de gestion Microsoft Intune pour charger des scripts PowerShell dans Intune en vue de les exécuter sur des appareils Windows 10. L’extension de gestion améliore la gestion des appareils mobiles Windows 10 et facilite l’adoption d’une gestion moderne.

Cette fonctionnalité s’applique à :

- Windows 10 et versions ultérieures

## <a name="move-to-modern-management"></a>Passer à une gestion moderne

Actuellement, l’informatique de l’utilisateur final connaît une transformation numérique. L’informatique classique et traditionnelle se caractérise par une plateforme d’appareils unique, des appareils d’entreprise, des utilisateurs travaillant depuis leur bureau et différents processus informatiques manuels et réactifs. Le lieu de travail moderne compte plusieurs plateformes d’appareils, à la fois personnelles et professionnelles. Il permet aux utilisateurs de travailler où qu’ils se trouvent et offre des processus informatiques automatisés et proactifs.

Les services de gestion des appareils mobiles, tels que Microsoft Intune, peuvent gérer les appareils mobiles et de bureau qui exécutent Windows 10. Le client de gestion Windows 10 intégré communique avec Intune pour effectuer des tâches de gestion d’entreprise. Vous pouvez avoir besoin de certaines tâches, telles que la configuration avancée d’appareils et la résolution de problèmes. Pour la gestion des applications Win32, vous pouvez utiliser la fonctionnalité [Gestion des applications Win32](app-management.md) sur vos appareils Windows 10.

L’extension de gestion Intune vient en complément des fonctionnalités intégrées de gestion des appareils mobiles Windows 10. Vous pouvez créer des scripts PowerShell à exécuter sur des appareils Windows 10. Par exemple, créez un script PowerShell qui effectue des configurations avancées d’un appareil. Ensuite, chargez le script sur Intune, affectez le script à un groupe Azure Active Directory (AD), puis exécutez le script. Vous pouvez ensuite superviser l’état d’exécution du script du début à la fin.

## <a name="prerequisites"></a>Prérequis

L’extension de gestion Intune est soumise aux prérequis suivants : Une fois ces prérequis satisfaits, l’extension de gestion Intune s’installe automatiquement quand un script PowerShell ou une application Win32 est affectée à l’utilisateur ou à l’appareil.

- Appareils exécutant Windows 10 version 1607 ou ultérieure Si l’appareil est inscrit via [l’inscription automatique en bloc](../enrollment/windows-bulk-enroll.md), les appareils doivent exécuter Windows 10 version 1703 ou ultérieure. L’extension de gestion Intune n’est pas prise en charge sur Windows 10 en mode S, car le mode S n’autorise pas l’exécution d’applications non-Store. 
  
- Appareils joints à Azure Active Directory, notamment :  
  
  - Joint à Azure AD Hybride : Appareils joints à Azure Active Directory et également joints à Active Directory local. Pour obtenir de l’aide, consultez [Planifier l’implémentation de la jonction à Azure Active Directory Hybride](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)

- Appareils inscrits dans Intune, notamment :

  - Appareils inscrits dans une stratégie de groupe. Pour obtenir de l’aide, consultez [Inscrire un appareil Windows 10 automatiquement en utilisant la stratégie de groupe](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy).
  
  - Appareils inscrits manuellement dans Intune, ce qui se fait quand :
  
    - [L’inscription automatique à Intune](../enrollment/quickstart-setup-auto-enrollment.md) est activée dans Azure AD. L’utilisateur final se connecte à l’appareil en utilisant un compte d’utilisateur local, joint manuellement l’appareil à Azure AD, puis se connecte à l’appareil avec son compte Azure AD.
    
    OU  
    
    - L’utilisateur se connecte à l’appareil en utilisant son compte Azure AD, puis qu’il s’inscrit dans Intune.

  - Appareils cogérés qui utilisent Configuration Manager et Intune. Vérifiez que la charge de travail des **applications** est définie sur **Piloter Intune**  ou sur **Intune**. Consultez les articles suivants pour obtenir des conseils : 
  
    - [Qu’est-ce que la cogestion ?](https://docs.microsoft.com/configmgr/comanage/overview) 
    - [Charge de travail des applications clientes](https://docs.microsoft.com/configmgr/comanage/workloads#client-apps)
    - [Comment basculer les charges de travail de Configuration Manager vers Intune](https://docs.microsoft.com/configmgr/comanage/how-to-switch-workloads)
  
> [!TIP]
> Vérifiez que les appareils sont [joints](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) à Azure AD. Les appareils qui sont uniquement [inscrits](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) dans Azure AD ne recevront pas vos scripts.

## <a name="create-a-script-policy-and-assign-it"></a>Créer une stratégie de script et l’affecter

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Scripts PowerShell** > **Ajouter**.

    ![Ajouter et utiliser des scripts PowerShell dans Microsoft Intune](./media/intune-management-extension/mgmt-extension-add-script.png)

3. Dans **Informations de base**, entrez les propriétés suivantes, puis sélectionnez **Suivant** :
    - **Nom** : Entrez un nom pour le script PowerShell. 
    - **Description** : Entrez une description pour le script PowerShell. Ce paramètre est facultatif, mais recommandé.
4. Dans **Paramètres du script**, entrez les propriétés suivantes, puis sélectionnez **Suivant** :
    - **Emplacement du script** : Accédez au script PowerShell. La taille du script doit être inférieure à 200 Ko (ASCII).
    - **Exécutez ce script en utilisant les informations d’identification d’ouverture de session** : Sélectionnez **Oui** pour exécuter le script avec les informations d’identification de l’utilisateur sur l’appareil. Choisissez **Non** (valeur par défaut) pour exécuter le script dans le contexte système. De nombreux administrateurs choisissent **Oui**. Si le script doit s’exécuter dans le contexte système, choisissez **Non**.
    - **Appliquer la vérification de la signature du script** : Sélectionnez **Oui** si le script doit être signé par un éditeur approuvé. Sélectionnez **Non** (valeur par défaut) s’il n’est pas nécessaire que le script soit signé. 
    - **Exécuter le script dans un hôte PowerShell 64 bits** : Sélectionnez **Oui** pour exécuter le script dans un hôte PowerShell (PS) 64 bits sur une architecture cliente 64 bits. Sélectionnez **Non** (valeur par défaut) pour exécuter le script dans un hôte PowerShell 32 bits.

      Quand vous choisissez **Oui** ou **Non**, utilisez le tableau suivant pour connaître le comportement nouveau et existant de la stratégie :

      | Exécuter le script dans un hôte PS 64 bits | Architecture cliente | Nouveau script PS | Script PS de la nouvelle stratégie |
      | --- | --- | --- | --- | 
      | Non | 32 bits  | Hôte PS 32 bits pris en charge | S’exécute uniquement dans un hôte PS 32 bits, qui fonctionne sur les architectures 32 bits et 64 bits. |
      | Oui | 64 bits | Exécute le script dans un hôte PS 64 bits pour les architectures 64 bits. Exécuté sur 32 bits, le script s’exécute dans un hôte PS 32 bits. | Exécute le script dans un hôte PS 32 bits. Si ce paramètre passe à 64 bits, le script s’ouvre (il ne s’exécute pas) dans un hôte PS 64 bits, puis signale les résultats. Exécuté sur 32 bits, le script s’exécute dans un hôte PS 32 bits. |

5. Sélectionnez **Balises d’étendue**. Les balises d’étendue sont facultatives. [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée](../fundamentals/scope-tags.md) contient plus d’informations.

    Pour ajouter une balise d’étendue :

    1. Choisissez **Sélectionner des balises d’étendue** > sélectionnez une balise d’étendue existante dans la liste > **Sélectionner**.

    2. Quand vous avez terminé, sélectionnez **Suivant**.

6. Sélectionnez **Affectations** > **Sélectionner les groupes à inclure**. Une liste des groupes Azure AD existants est affichée.

    1. Sélectionnez un ou plusieurs groupes contenant les utilisateurs dont les appareils reçoivent le script. Choisissez **Sélectionner**. Les groupes que vous avez choisis apparaissent dans la liste ; ils recevront votre stratégie.

        > [!NOTE]
        > Dans Intune, les scripts PowerShell peuvent cibler des groupes de sécurité d’appareils Azure AD ou des groupes de sécurité d’utilisateurs Azure AD.

    2. Sélectionnez **Suivant**.

        ![Affecter ou déployer un script PowerShell dans des groupes d’appareils dans Microsoft Intune](./media/intune-management-extension/mgmt-extension-assignments.png)

7. Dans **Passer en revue + ajouter**, vous voyez un récapitulatif des paramètres que vous avez configurés. Sélectionnez **Ajouter** pour enregistrer le script. Quand vous sélectionnez **Ajouter**, la stratégie est déployée sur les groupes que vous avez choisis.

## <a name="important-considerations"></a>Considérations importantes

- Lorsque les scripts sont définies sur le contexte de l’utilisateur et que l’utilisateur final a des droits d’administrateur, par défaut, le script PowerShell s’exécute sous le privilège d’administrateur.

- Les utilisateurs finaux ne sont pas obligés d’être connectés à l’appareil pour exécuter des scripts PowerShell.

- Toutes les heures et après chaque redémarrage, le client d’extension de gestion Intune vérifie auprès d’Intune s’il existe de nouveaux scripts ou si des modifications ont été apportées. Une fois la stratégie affectée aux groupes Azure AD, le script PowerShell s’exécute, puis les résultats de l’exécution sont consignés dans un rapport. Une fois que le script s’exécute, il ne se réexécute pas sauf si une modification est apportée au script ou à la stratégie.

## <a name="monitor-run-status"></a>Superviser l’état de l’exécution

Vous pouvez surveiller l’état de l’exécution des scripts PowerShell pour les utilisateurs et les appareils dans le portail Azure.

Dans **Scripts PowerShell**, sélectionnez le script à surveiller, choisissez **Surveiller**, puis choisissez l’un des rapports suivants :

- **État de l’appareil**
- **État de l’utilisateur**

## <a name="intune-management-extension-logs"></a>Journaux de l’extension de gestion Intune

Les journaux de l’agent sur l’ordinateur client se trouvent généralement dans `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Vous pouvez utiliser [CMTrace.exe](https://docs.microsoft.com/configmgr/core/support/cmtrace) pour afficher ces fichiers journaux.

![Capture d’écran ou exemples de journaux de l’agent cmtrace dans Microsoft Intune](./media/apps-win32-app-management/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Supprimer un script

Dans **Scripts PowerShell**, cliquez avec le bouton droit sur le script, puis sélectionnez **Supprimer**.

## <a name="common-issues-and-resolutions"></a>Solutions aux problèmes courants

### <a name="issue-intune-management-extension-doesnt-download"></a>Problème : Impossible de télécharger l’extension de gestion Intune

**Solutions possibles :**

- L’appareil n’est pas joint à Azure AD. Vérifiez que les appareils répondent aux [prérequis](#prerequisites) (de cet article). 
- Aucun script PowerShell ou aucune application Win32 ne sont affectés aux groupes auxquels appartient l’utilisateur ou l’appareil.
- L’appareil ne peut pas se connecter au service Intune, car il n’a pas d’accès à Internet, pas d’accès aux services de notifications Push Windows, etc.
- L’appareil est en mode S. L’extension de gestion Intune n’est pas prise en charge sur les appareils s’exécutant en mode S. 

Pour voir si l’appareil est inscrit automatiquement, vous pouvez :

  1. Accédez à **Paramètres** > **Comptes** > **Accès scolaire ou professionnel**.
  2. Sélectionnez le compte joint > **Infos**.
  3. Sous le **rapport Diagnostics avancés**, sélectionnez **Créer un rapport**.
  4. Ouvrez le `MDMDiagReport` dans un navigateur web.
  5. Recherchez la propriété **MDMDeviceWithAAD**. Si la propriété existe, c’est que l’appareil est inscrit automatiquement. Si cette propriété n’existe pas, c’est que votre appareil n’est pas inscrit automatiquement.

[Activer l’inscription automatique Windows 10](../enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) inclut les étapes pour configurer l’inscription automatique dans Intune.

### <a name="issue-powershell-scripts-do-not-run"></a>Problème : Les scripts PowerShell ne s’exécutent pas

**Solutions possibles :**

- Les scripts PowerShell ne s’exécutent pas à chaque connexion. Ils s’exécutent :

  - Quand le script est affecté à un appareil
  - Si vous modifiez le script, chargez-le et affectez-le à un utilisateur ou à un appareil
  
    > [!TIP]
    > L’**extension de gestion Microsoft Intune** est un service qui s’exécute sur l’appareil, tout comme n’importe quel autre service listé dans l’application Services (services.msc). Après le redémarrage d’un appareil, ce service peut également redémarrer et rechercher des scripts PowerShell affectés avec le service Intune. Si le service **Extension de gestion Microsoft Intune** est défini sur Manuel, le service ne peut pas redémarrer après un redémarrage de l’appareil.

- Vérifiez que les appareils sont [joints à Azure AD](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network). Les appareils qui sont joints uniquement à votre espace de travail ou à votre organisation ([inscrits](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) dans Azure AD) ne recevront pas les scripts.
- Toutes les heures, le client d’extension de gestion Intune vérifie s’il y a des modifications du script ou de la stratégie dans Intune.
- Vérifiez que l’extension de gestion Intune a été téléchargée à l’emplacement suivant : `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Les scripts ne s’exécutent pas sur les appareils Surface Hub ou Windows 10 en mode S.
- Examinez les éventuelles erreurs dans les journaux. Consultez [Journaux de l’extension de gestion Intune](#intune-management-extension-logs) (dans cet article).
- En cas de problème lié aux autorisations, vérifiez que les propriétés du script PowerShell sont bien définies sur `Run this script using the logged on credentials`. Vérifiez également que l’utilisateur connecté dispose des autorisations nécessaires pour exécuter le script.

- Pour isoler les problèmes des scripts, procédez comme suit :

  - Examinez la configuration de l’exécution de PowerShell sur vos appareils. Pour obtenir de l’aide, consultez [Stratégie d’exécution de PowerShell](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6).
  - Exécutez un exemple de script en utilisant l’extension de gestion Intune. Par exemple, créez le répertoire `C:\Scripts` et accordez à tout le monde un contrôle complet. Exécutez le script suivant :

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Si cela réussit, le fichier output.txt doit être créé et doit inclure le texte « Script worked » (Le script a fonctionné).

  - Pour tester l’exécution des scripts sans Intune, exécutez les scripts localement dans le compte système avec l’[outil psexec](https://docs.microsoft.com/sysinternals/downloads/psexec) :

    `psexec -i -s`  
    
  - Si le script signale qu’il a réussi, mais qu’il n’a pas réussi, il est possible que votre service antivirus place AgentExecutor dans le bac à sable (sandbox). Le script suivant signale toujours une défaillance dans Intune. En guise de test, vous pouvez utiliser ce script :
  
    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```

    Si le script signale une réussite, examinez `AgentExecutor.log` pour confirmer la sortie de l’erreur. Si le script s’exécute, la longueur doit être >2.

  - Pour capturer les fichiers .error et .output, l’extrait de code suivant exécute le script via AgentExecutor vers PSx86 (`C:\Windows\SysWOW64\WindowsPowerShell\v1.0`). Il conserve les journaux pour que vous puissiez les vérifier. N’oubliez pas que l’extension de gestion Intune nettoie les journaux après l’exécution du script :
  
    ```powershell
    $scriptPath = read-host "Enter the path to the script file to execute"
    $logFolder = read-host "Enter the path to a folder to output the logs to"
    $outputPath = $logFolder+"\output.output"
    $errorPath =  $logFolder+"\error.error"
    $timeoutPath =  $logFolder+"\timeout.timeout"
    $timeoutVal = 60000 
    $PSFolder = "C:\Windows\SysWOW64\WindowsPowerShell\v1.0"
    $AgentExec = "C:\Program Files (x86)\Microsoft Intune Management Extension\agentexecutor.exe"
    &$AgentExec -powershell  $scriptPath $outputPath $errorPath $timeoutPath $timeoutVal $PSFolder 0 0
    ```

## <a name="next-steps"></a>Étapes suivantes

[Supervisez](../device-profile-monitor.md) et [dépannez](../device-profile-troubleshoot.md) vos profils.
