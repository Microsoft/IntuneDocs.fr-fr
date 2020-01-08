---
title: Mettre à jour Office 365 à l’aide de modèles d’administration dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez les modèles d’administration de Microsoft Intune pour mettre à jour les applications Office 365 vers la dernière version, puis choisissez la fréquence à laquelle Office recherche les mises à jour. Consultez les clés de registre de l’appareil qui sont mises à jour lors de l’application d’une stratégie Intune à une mise à jour Office.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63ebbc22c5452c99439d34813509b5652daef1f0
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548088"
---
# <a name="use-update-channel-and-target-version-settings-to-update-office-365-with-microsoft-intune-administrative-templates"></a>Utilisez les paramètres Canal de mise à jour et Version cible pour mettre à jour Office 365 avec les modèles d'administration Microsoft Intune

Dans Intune, vous pouvez utiliser des [modèles Windows 10 pour configurer les paramètres de stratégie de groupe](administrative-templates-windows.md). Cet article explique comment mettre à jour Office 365 à l’aide d’un modèle d’administration dans Intune. Il fournit également des conseils pour confirmer que vos stratégies s’appliquent avec succès. Ces informations vous aideront également lors du dépannage.

Dans ce scénario, vous créez un modèle d’administration dans Intune qui met à jour Office 365 sur vos appareils.

Pour en savoir plus sur les modèles d’administration, consultez [Modèles Windows 10 pour configurer les paramètres de stratégie de groupe](administrative-templates-windows.md).

S’applique à :

- Windows 10 et versions ultérieures
- Office 365

## <a name="prerequisites"></a>Prérequis

Veillez à [activer les mises à jour automatiques Office 365 ProPlus](https://docs.microsoft.com/deployoffice/configure-update-settings-for-office-365-proplus) pour vos applications Office. Pour ce faire, vous pouvez utiliser la stratégie de groupe ou le modèle Intune Office 2016 ADMX :

![Dans le modèle d’administration Intune, définissez le paramètre Activer les mises à jour automatiques pour Office](./media/administrative-templates-update-office/admx-enable-automatic-updates.png)

## <a name="set-the-update-channel-in-the-intune-administrative-template"></a>Définissez le canal de mise à jour dans le modèle d’administration Intune

1. Dans votre [modèle d’administration Intune](administrative-templates-windows.md#create-a-template), accédez au paramètre **Canal de mise à jour**, puis entrez le canal souhaité. Par exemple, choisissez `Semi-Annual Channel` :

    ![Dans le modèle d’administration Intune, définissez le paramètre Canal de mise à jour pour Office](./media/administrative-templates-update-office/admx-enable-update-channel-setting.png)

    > [!NOTE]
    > Il est recommandé de mettre à jour plus fréquemment. Semi-annuel est utilisé uniquement à titre d’exemple.

2. Veillez à [affecter la stratégie](device-profile-assign.md) à vos appareils Windows 10. Pour tester votre stratégie plus tôt, vous pouvez également synchroniser la stratégie :

    - [Synchroniser la stratégie dans Intune](../remote-actions/device-sync.md)
    - [Synchroniser manuellement la stratégie sur l’appareil](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows#sync-from-settings-app)

## <a name="check-the-intune-registry-keys"></a>Vérifier les clés de Registre Intune

Une fois que vous avez affecté la stratégie et que l’appareil se synchronise, vous pouvez vérifier que la stratégie est appliquée :

1. Sur l’appareil, ouvrez l’application **Éditeur du Registre**.
2. Accédez au chemin d’accès à la stratégie Intune : `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`.

    > [!TIP]
    > La valeur `<Provider ID>` dans la clé de Registre est modifiée. Pour trouver l’ID de fournisseur de votre appareil, ouvrez l’application **Éditeur du Registre**, puis accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\AdmxInstalled`. L’ID du fournisseur s’affiche.

    Lorsque la stratégie est appliquée, les clés de Registre suivantes s’affichent :

    - `L_UpdateBranch`
    - `L_UpdateTargetVersion`

    Si vous observez l’exemple suivant, `L_UpdateBranch` a une valeur semblable à `<enabled /><data id="L_UpdateBranchID" value="Deferred" />`. Cette valeur signifie qu’elle est définie sur Canal semi-annuel :

    ![Exemple de clé de Registre L_Updatebranch de modèle d’administration](./media/administrative-templates-update-office/admx-update-branch-registry-key.png)

    > [!TIP]
    > [Gérer Office 365 ProPlus avec Configuration Manager](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) répertorie les valeurs et leur signification. Les valeurs de Registre sont basées sur le canal de distribution sélectionné :
    >
    >- Canal mensuel                - value="Current"
    >- Canal mensuel (ciblé)                - value="Current"
    >- Canal semi-annuel            - value="Current"
    >- Canal semi-annuel (ciblé) - value="FirstReleaseDeferred"
    >- Insider Fast                   - value="InsiderFast"

À ce stade, la stratégie Intune est correctement appliquée à l’appareil.

## <a name="check-the-office-registry-keys"></a>Vérifier les clés de Registre Office

1. Sur l’appareil, ouvrez l’application **Éditeur du Registre**.
2. Accédez au chemin d’accès à la stratégie Office : `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`.

    Vous voyez les clés de Registre suivantes :

    - `UpdateChannel` : Clé dynamique qui change selon les paramètres configurés.
    - `CDNBaseUrl` : Définissez le moment où Office 365 s’installe sur l’appareil.

3. Examinez la valeur `UpdateChannel`. La valeur indique la fréquence à laquelle Office est mis à jour. [Gérer Office 365 ProPlus avec Configuration Manager](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel) répertorie les valeurs telles qu’elles sont définies.

    Si vous observez l’exemple suivant, `UpdateChannel` est défini sur `http://officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60`, à savoir **mensuel**  :

    ![Exemple de clé de Registre Office UpdateChannel de modèle d’administration](./media/administrative-templates-update-office/admx-update-channel-office-registry-key.png)

    Cet exemple signifie que la stratégie n’est pas encore appliquée, car elle est toujours définie sur **Mensuel** au lieu de **Semi-annuel**.

Cette clé de Registre est mise à jour lorsque le **Planificateur de tâches** > **Mises à jour automatiques d’Office 2.0** s’exécute ou lorsqu’un utilisateur se connecte à l’appareil. Pour confirmer, ouvrez la tâche **Mises à jour automatiques d’Office 2.0** > **Déclencheurs**. Selon vos déclencheurs, la mise à jour de la clé de Registre `UpdateChannel` peut prendre au moins un jour.

## <a name="force-office-automatic-updates-to-run"></a>Forcer l’exécution des mises à jour automatiques d’Office

Pour tester votre stratégie, vous pouvez forcer les paramètres de stratégie sur l’appareil. Les étapes suivantes mettent à jour le Registre. Comme toujours, faites preuve de prudence lors de la mise à jour du Registre.

1. Effacez la clé de Registre :

    1. Accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Updates`.
    2. Double-sélectionnez la clé `UpdateDetectionLastRunTime`, supprimez la valeur > **OK**.

2. Exécutez la tâche Mises à jour automatiques d’Office :

    1. Ouvrez l’application **Planificateur de tâches** sur l’appareil.
    2. Développez **Bibliothèque du Planificateur de tâches** > **Microsoft** > **Office**.
    3. Sélectionnez **Mises à jour automatiques d’office 2.0** > **Exécuter** :

        ![Ouvrir la planification des tâches et exécuter les mises à jour automatiques d’Office](./media/administrative-templates-update-office/admx-task-scheduler-office-automatic-updates.png)

        Attendez que la tâche se termine, ce qui peut prendre plusieurs minutes.

3. Dans l’application **Éditeur du Registre**, accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration`. Vérifiez la valeur `UpdateChannel`.

    Elle doit être mise à jour avec la valeur définie dans la stratégie. Dans notre exemple, la valeur doit être définie sur `http://officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114`.

À ce stade, le canal de mise à jour Office est correctement modifié sur l’appareil. Vous pouvez ouvrir une application Office 365 pour un utilisateur qui reçoit cette mise à jour pour vérifier l’état.

## <a name="force-the-office-synchronization-to-update-account-information"></a>Forcer la synchronisation Office à mettre à jour les informations de compte  

Si vous souhaitez en faire plus, vous pouvez forcer Office à obtenir la dernière mise à jour. Les étapes suivantes doivent être effectuées uniquement à titre de confirmation, ou si vous avez besoin que les appareils obtiennent rapidement la dernière mise à jour de ce canal. Dans le cas contraire, laissez Office effectuer son travail et se mettre à jour automatiquement.

### <a name="step-1-force-the-office-version-to-update"></a>Étape 1 : Forcer la mise à jour de la version d’Office

1. Vérifiez que la version d’Office prend en charge le canal de mise à jour que vous avez choisi. [L’historique des mises à jour pour Office 365 ProPlus](https://docs.microsoft.com/officeupdates/update-history-office365-proplus-by-date) répertorie les numéros de version qui prennent en charge les différents canaux de mise à jour.

2. Dans votre [modèle d’administration Intune](administrative-templates-windows.md#create-a-template), accédez au paramètre **Version cible**, puis entrez la version souhaitée.

    Le paramètre **Version cible** se présente comme suit :

    ![Dans le modèle d’administration Intune, définissez le paramètre Version cible pour Office](./media/administrative-templates-update-office/admx-enable-target-version-setting.png)

> [!IMPORTANT]
>
> - Veillez à affecter la stratégie.
> - Si vous modifiez une stratégie existante, vos modifications affectent tous les utilisateurs affectés.
> - Si vous testez cette fonctionnalité, il est recommandé de créer une stratégie de test et de l’affecter à un groupe d’utilisateurs de test.

### <a name="step-2-check-the-office-version"></a>Étape 2 : Vérifier la version d’Office

Envisagez d’utiliser ces étapes pour tester votre stratégie avant de la déployer pour tous les utilisateurs.

1. Dans l’application **Éditeur du Registre**, accédez à `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\Providers\<Provider ID>\default\Device\office16~Policy~L_MicrosoftOfficemachine~L_Updates`

2. Examinez la valeur `L_UpdateTargetVersion`. Une fois la stratégie appliquée, la valeur est définie sur la version que vous avez entrée, par exemple `<enabled /><data id="L_UpdateTargetVersionID" value="16.0.10730.20344" />`.

    À ce stade, la stratégie Intune est correctement appliquée à l’appareil.

3. Ensuite, vous pouvez forcer Office à se mettre à jour. Ouvrez une application Office, telle qu’Excel. Choisissez Mettre à jour maintenant (peut-être dans le menu **Compte**).

    La mise à jour prend quelques minutes. Vous pouvez confirmer qu’Office tente d’accéder à la version que vous entrez :

      1. Sur l’appareil, accédez à `C:\Program Files (x86)\Microsoft Office\Updates\Detection\Version`.
      2. Ouvrez le fichier `VersionDescriptor.xml` et passez à la section `<Version>`. La version disponible doit être la même que celle que vous avez entrée dans la stratégie Intune, par exemple :

          ![Vérifiez la section Version dans le fichier XML Office du descripteur de version](./media/administrative-templates-update-office/office-version-descriptor-xml-example.png)

4. Une fois la mise à jour installée, l’application Office doit afficher la nouvelle version (par exemple dans le menu **Compte**)

## <a name="next-steps"></a>Étapes suivantes

[Valeurs de canal de mise à jour pour les clients Office 365](https://docs.microsoft.com/configmgr/sum/deploy-use/manage-office-365-proplus-updates#bkmk_channel)

[Vue d’ensemble du service de stratégie de cloud d’Office pour Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-office-cloud-policy-service)

[Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe (modèles ADMX) dans Microsoft Intune](administrative-templates-windows.md)
