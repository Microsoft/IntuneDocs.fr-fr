---
title: Installer le logiciel client PC.
description: Utilisez ce guide pour que votre PC Windows soit géré par le logiciel client Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
ms.date: 07/13/2017
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45a88e4cc1f84c157b5ece1204bddfb7ebe01b57
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736089"
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Installer le logiciel client Intune sur des PC Windows

[!INCLUDE [classic-portal](../../intune-classic/includes/classic-portal.md)]

> [!NOTE]
> Vous pouvez utiliser Microsoft Intune pour gérer les PC Windows comme [appareils mobiles avec la gestion des appareils mobiles (MDM)](../enrollment/windows-enroll.md) ou comme ordinateurs avec le logiciel client Intune, comme décrit ci-dessous. Cependant, Microsoft recommande aux clients [d’utiliser la solution de gestion MDM](../enrollment/windows-enroll.md) quand c’est possible. Pour plus d’informations, consultez [Comparer la gestion des PC Windows en tant qu’ordinateurs ou appareils mobiles](pc-management-comparison.md) 


Les PC Windows peuvent être inscrits en installant le logiciel client Intune. Le logiciel client Intune peut être installé à l'aide des méthodes suivantes :

- Par l’administrateur informatique : installation manuelle, installation à l’aide de la stratégie de groupe ou installation intégrée dans une image de disque

- Par les utilisateurs finaux, qui installent manuellement le logiciel client

Le logiciel client Intune contient la configuration logicielle minimale nécessaire pour inscrire le PC dans la gestion Intune. Une fois le PC inscrit, le logiciel client Intune télécharge le logiciel client complet nécessaire pour la gestion du PC.

Cette série de téléchargements réduit l’impact sur la bande passante du réseau et réduit le temps nécessaire pour l'inscription initiale du PC dans Intune. Elle garantit également que le client dispose du logiciel plus récent disponible une fois le second téléchargement terminé.

Une seule licence Intune permet d’installer le logiciel client Intune sur cinq PC au maximum.

## <a name="download-the-intune-client-software"></a>Téléchargement du logiciel client Intune

Toutes les méthodes, à l’exception de celles où les utilisateurs installent le logiciel client Intune eux-mêmes, nécessitent le téléchargement préalable du logiciel par des administrateurs informatiques pour qu'il puisse être ensuite déployé pour les utilisateurs finaux.

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **Admin** &gt; **Téléchargement du logiciel client**.

   ![Télécharger le client PC Intune](./media/install-the-windows-pc-client-with-microsoft-intune/pc-sa-client-download.png)

2. Dans la page **Téléchargement du logiciel client**, cliquez sur **Télécharger le logiciel client**. Enregistrez ensuite le package **Windows_Intune_Setup.zip** contenant le logiciel à un emplacement sécurisé sur votre réseau.

   Le package d’installation du logiciel client Intune contient des informations uniques et spécifiques disponibles par le biais d'un certificat incorporé associé à votre compte. Si des utilisateurs non autorisés arrivent à accéder au package d’installation, ils peuvent inscrire des PC dans le compte représenté par le certificat intégré et obtenir ainsi l’accès aux ressources de l’entreprise.

3. Extrayez le contenu du package d'installation dans l'emplacement sécurisé de votre réseau.

    > [!IMPORTANT]
    > Ne renommez pas ou ne supprimez pas le fichier **ACCOUNTCERT** extrait, au risque de faire échouer l’installation du logiciel client.

## <a name="deploy-the-client-software-manually"></a>Déployer manuellement le logiciel client

Sur les ordinateurs sur lesquels le logiciel client doit être installé, accédez au dossier dans lequel se trouvent les fichiers d’installation du logiciel client. Exécutez ensuite **Microsoft_Intune_Setup.exe** pour installer le logiciel client.

> [!NOTE]
> L’état de l’installation s’affiche quand vous placez le curseur sur l’icône de la barre des tâches du PC client.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Déployer le logiciel client à l’aide de la stratégie de groupe

1. Dans le dossier contenant les fichiers **Microsoft_Intune_Setup.exe** et **MicrosoftIntune.accountcert**, exécutez la commande suivante pour extraire les programmes d’installation Windows Installer des ordinateurs 32 et 64 bits :

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2. Copiez les fichiers **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** et **MicrosoftIntune.accountcert** à un emplacement réseau accessible à tous les ordinateurs sur lesquels le logiciel client doit être installé.

    > [!IMPORTANT]
    > Ne séparez ou ne renommez pas les fichiers, au risque de faire échouer l'installation du logiciel client.

3. Utilisez la stratégie de groupe pour déployer les logiciels sur les ordinateurs de votre réseau.

    Pour plus d’informations sur l’utilisation de stratégies de groupe pour déployer automatiquement des logiciels, consultez [Introduction aux stratégies de groupe](https://technet.microsoft.com/library/hh147307.aspx).

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Déployer le logiciel client comme partie d’une image
Vous pouvez déployer le logiciel client Intune sur des ordinateurs dans le cadre d’une image de système d’exploitation en utilisant comme guide la procédure suivante :

1. Copiez les fichiers d’installation du client, **Microsoft_Intune_Setup.exe** et **MicrosoftIntune.accountcert**, dans le dossier **%Systemdrive%\Temp\Microsoft_Intune_Setup** sur l’ordinateur de référence.

2. Créez l'entrée de Registre **WindowsIntuneEnrollPending** en ajoutant la commande suivante au script **SetupComplete.cmd** :

    ```cmd
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3. Ajoutez la commande suivante à **setupcomplete.cmd** pour exécuter le package d’inscription avec l’argument de ligne de commande /PrepareEnroll :

    ```cmd
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```

    > [!TIP]
    > Le script **SetupComplete.cmd** permet au programme d’installation de Windows d’apporter des modifications au système avant qu’un utilisateur se connecte. L’argument de ligne de commande **/PrepareEnroll** prépare un ordinateur ciblé afin qu’il soit automatiquement inscrit dans Intune une fois l’installation de Windows terminée.

4. Placez **SetupComplete.cmd** dans le dossier **%Windir%\Setup\Scripts** sur l’ordinateur de référence.

5. Capturez une image de l'ordinateur de référence et déployez-la sur les ordinateurs ciblés.

    Au redémarrage de l'ordinateur ciblé à la fin des opérations du programme d'installation de Windows, la clé de Registre **WindowsIntuneEnrollPending** est créée. Le package d’inscription vérifie si l’ordinateur est inscrit. Si l'ordinateur est inscrit, aucune action n'est exécutée. Si l’ordinateur n’est pas inscrit, le package d’inscription crée une tâche d’inscription automatique Microsoft Intune.

    Quand la tâche d’inscription automatique s’exécute à l’heure planifiée suivante, elle vérifie l’existence de la valeur de Registre **WindowsIntuneEnrollPending** et tente d’inscrire l’ordinateur ciblé dans Intune. Si l'inscription échoue pour une raison quelconque, l'inscription est tentée à nouveau lors de la prochaine exécution de la tâche. Les nouvelles tentatives continuent pendant un mois.

    La tâche d’inscription automatique Intune, la valeur de Registre **WindowsIntuneEnrollPending** et le certificat du compte sont supprimés de l’ordinateur ciblé quand l’inscription est réussie ou après un délai d’un mois (selon ce qui advient en premier).

## <a name="instruct-users-to-self-enroll"></a>Indiquer aux utilisateurs de s’inscrire eux-mêmes

Les utilisateurs installent le logiciel client Intune en accédant au [site web Portail d’entreprise](https://portal.manage.microsoft.com). Les informations exactes que les utilisateurs voient dans le portail web varient selon l’autorité MDM de votre compte et la plateforme/version du système d’exploitation du PC de l’utilisateur.

Si aucune licence Intune n’a été attribuée aux utilisateurs ou si l’autorité MDM de l’organisation n’a pas été définie sur Intune, aucune option d’inscription n’est visible par les utilisateurs.

Si les utilisateurs ont reçu une licence Intune et que l’autorité MDM de l’organisation a été définie sur Intune :

- Les utilisateurs de PC Windows 7 ou Windows 8 voient UNIQUEMENT l’option d’inscription à Intune en téléchargeant et en installant le logiciel client PC qui est propre à leur organisation.

- Deux options d’inscription s’affichent pour les utilisateurs de PC Windows 10 ou Windows 8.1 :

  - **Inscrire le PC comme appareil mobile** : les utilisateurs choisissent le bouton **En savoir plus sur l’inscription** et accèdent à des instructions pour inscrire leur PC comme appareil mobile. Ce bouton s’affiche bien en évidence, car l’inscription MDM est considérée comme étant l’option d’inscription par défaut et préférée. Toutefois, l’option MDM n’est pas applicable à cette rubrique, qui couvre uniquement l’installation du logiciel client.
  - **Inscrire le PC à l’aide du logiciel client Intune** : vous devez indiquer à vos utilisateurs de sélectionner le lien **Cliquez ici pour télécharger**, qui les guidera tout au long de l’installation du logiciel client.

Le tableau suivant récapitule les options.

  ![Options d’inscription par défaut par plateforme](./media/install-the-windows-pc-client-with-microsoft-intune/default-enrollment-options-table.png)

Les captures d’écran suivantes montrent ce que les utilisateurs voient quand ils inscrivent leurs appareils à l’aide du logiciel client.

Les utilisateurs sont tout d’abord invités à s’identifier ou à inscrire leur appareil.

  ![identifier ou inscrire l’appareil](./media/install-the-windows-pc-client-with-microsoft-intune/identify-device-or-enroll.png)

Pour que vos utilisateurs installent le logiciel client PC, vous devez leur dire de sélectionner le lien **Cliquez ici pour télécharger**, qui leur permet de le télécharger et les guide tout au long du processus d’installation. Le bouton **En savoir plus sur l’inscription** permet aux utilisateurs d’accéder à la documentation sur la façon de s’inscrire avec l’inscription MDM, qui ne s’applique pas à ces instructions du logiciel client.

  ![choisir le lien Cliquez ici pour télécharger](./media/install-the-windows-pc-client-with-microsoft-intune/enroll-your-windows-device.png)

Quand les utilisateurs cliquent sur le lien, le bouton **Télécharger le logiciel** s’affiche ; ils peuvent le sélectionner pour démarrer l’installation du logiciel client PC.

  ![choisir le bouton Télécharger le logiciel](./media/install-the-windows-pc-client-with-microsoft-intune/download-pc-client-software.png)

Les utilisateurs sont ensuite invités à se connecter avec leurs informations d’identification d’entreprise.

  ![Se connecter avec les informations d’identification](./media/install-the-windows-pc-client-with-microsoft-intune/sign-in-to-intune.png)

Les utilisateurs sont dirigés vers la page d’accueil de l’installation.

  ![Page d’accueil pour l’installation du client PC](./media/install-the-windows-pc-client-with-microsoft-intune/welcome-to-pc-agent-install-wizard.png)

Les utilisateurs choisissent **Suivant** et l’installation démarre.

  ![Page d’accueil pour l’installation du client PC](./media/install-the-windows-pc-client-with-microsoft-intune/welcome-to-pc-agent-install-wizard.png)

Quand l’installation est terminée, les utilisateurs choisissent **Terminer**.

  ![Terminer l’installation du client PC](./media/install-the-windows-pc-client-with-microsoft-intune/completed-the-setup-wizard.png)

Si les utilisateurs tentent d’inscrire leur PC comme appareil mobile après l’avoir déjà inscrit à l’aide du logiciel client PC Intune, l’écran d’erreur suivant s’affiche.

  ![Écran indiquant si le PC est déjà inscrit](./media/install-the-windows-pc-client-with-microsoft-intune/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>Surveiller et valider la réussite du déploiement du client
Utilisez l'une des procédures suivantes pour surveiller et valider la réussite du déploiement du client.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Pour vérifier l'installation du logiciel client depuis la console d'administration Microsoft Intune

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **Groupes** &gt; **Tous les appareils** &gt; **Tous les ordinateurs**.

2. Dans la liste, recherchez les ordinateurs qui communiquent avec Intune ou recherchez un ordinateur géré spécifique en tapant le nom de l’ordinateur (ou une partie de son nom) dans la zone **Rechercher des appareils**.

3. Examinez l’état de l’ordinateur dans le volet inférieur de la console. Résolvez les éventuelles erreurs.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>Pour créer un rapport d'inventaire informatique afin d'afficher tous les ordinateurs inscrits

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), cliquez sur **Rapports** &gt; **Rapports d’inventaire informatique**.

2. Dans la page **Créer un rapport**, laissez les valeurs par défaut renseignées dans tous les champs (sauf si vous voulez appliquer des filtres), puis cliquez sur **Afficher le rapport**.

3. La page **Rapport d’inventaire des ordinateurs** s’ouvre dans une nouvelle fenêtre et affiche tous les ordinateurs inscrits avec succès dans Intune.

    > [!TIP]
    > Cliquez sur n'importe quel en-tête de colonne dans le rapport pour trier la liste en fonction du contenu de cette colonne.

## <a name="uninstall-the-windows-client-software"></a>Désinstaller le logiciel client Windows

Il existe deux façons d’annuler l’inscription du logiciel client Windows :

- À partir de la console d’administration Intune (méthode recommandée)
- À partir d’une invite de commandes sur le client

### <a name="unenroll-by-using-the-intune-admin-console"></a>Annuler l’inscription à l’aide de la console d’administration Intune

Pour annuler l’inscription du logiciel client à l’aide de la console d’administration Intune, accédez à **Groupes** > **Tous les ordinateurs** > **Appareils**. Cliquez avec le bouton droit sur le client, puis sélectionnez **Mettre hors service/Réinitialiser**.

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>Annuler l’inscription à l’aide d’une invite de commandes sur le client

À partir d’une invite de commandes avec élévation de privilèges, exécutez l’une des commandes suivantes.

**Méthode 1** :

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**Méthode 2** Notez que ces agents ne sont pas tous installés sur chaque référence (SKU) de Windows :

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall
    wmic product where name="Microsoft Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall
    wmic product where name="Microsoft Policy Platform" call uninstall
    wmic product where name="Microsoft Security Client" call uninstall
    wmic product where name="Microsoft Online Management Client" call uninstall
    wmic product where name="Microsoft Online Management Client Service" call uninstall
    wmic product where name="Microsoft Easy Assist v2" call uninstall
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Microsoft Intune Center" call uninstall
    wmic product where name="Microsoft Online Management Update Manager" call uninstall
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall
    wmic product where name="Microsoft Intune" call uninstall
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall
    wmic product where name="Windows Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Windows Online Management Policy Agent" call uninstall
    wmic product where name="Windows Policy Platform" call uninstall
    wmic product where name="Windows Security Client" call uninstall
    wmic product where name="Windows Online Management Client" call uninstall
    wmic product where name="Windows Online Management Client Service" call uninstall
    wmic product where name="Windows Easy Assist v2" call uninstall
    wmic product where name="Windows Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Windows Intune Center" call uninstall
    wmic product where name="Windows Online Management Update Manager" call uninstall
    wmic product where name="Windows Online Management Agent Installer" call uninstall
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> L’annulation de l’inscription du client laisse un enregistrement obsolète côté serveur pour le client concerné. Le processus d’annulation de l’inscription est asynchrone. Il y a neuf agents à désinstaller, et cette opération peut prendre jusqu'à 30 minutes.

### <a name="check-the-unenrollment-status"></a>Vérifier l’état de l’annulation de l’inscription

Consultez « %ProgramFiles%\Microsoft\OnlineManagement » et vérifiez que seuls les répertoires suivants sont affichés sur la gauche :

- AgentInstaller
- Logs
- Mises à jour
- Common

### <a name="remove-the-onlinemanagement-folder"></a>Supprimer le dossier OnlineManagement

Le processus d’annulation de l’inscription ne supprime pas le dossier OnlineManagement. Attendez 30 minutes après la désinstallation, puis exécutez cette commande. Si vous l’exécutez trop tôt, la désinstallation peut rester dans un état inconnu. Pour supprimer le dossier, démarrez une invite de commandes avec élévation des privilèges et exécutez :

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

## <a name="next-steps"></a>Étapes suivantes
[Tâches courantes de gestion des PC Windows avec le client logiciel Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
