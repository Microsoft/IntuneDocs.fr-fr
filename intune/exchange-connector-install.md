---
title: Configurer le connecteur Exchange local de Microsoft Intune
titleSuffix: Microsoft Intune
description: Utilisez le connecteur Exchange local pour gérer l’accès de l’appareil aux boîtes aux lettres Exchange en fonction de l’inscription Intune et d’Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bc5f8a3f0094c363a705b37b904435ef9e91781
ms.sourcegitcommit: 47b06bf2d32e2f84c382dec3366d6f4a31d98012
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70864480"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Configurer le connecteur Exchange local Intune dans Microsoft Intune
Les informations contenues dans cet article vous aident à installer, puis à superviser le connecteur local Exchange Active Sync pour Intune.  Vous utilisez le connecteur Exchange local Intune avec vos [stratégies d’accès conditionnel pour autoriser ou bloquer l’accès aux boîtes aux lettres locales Exchange](conditional-access-exchange-create.md). 

Quand un appareil tente d’accéder à votre serveur Exchange local, le connecteur Exchange mappe les enregistrements Exchange Active Sync (EAS) dans le serveur Exchange aux enregistrements Intune pour vérifier l’inscription des appareils auprès d’Intune et la conformité à vos stratégies de conformité d’appareil. En fonction de vos stratégies d’accès conditionnel, l’accès peut être autorisé ou refusé à l’appareil. Pour plus d’informations, consultez [Quelles sont les utilisations courantes de l’accès conditionnel avec Intune ?](conditional-access-intune-common-ways-use.md)

Intune prend en charge l’installation de plusieurs connecteurs Exchange locaux par abonnement. Si vous avez plusieurs organisations Exchange locales, vous pouvez configurer un connecteur distinct pour chacune d’elles. Toutefois, un seul connecteur peut être installé pour chaque organisation Exchange. 

Voici les étapes générales à suivre pour configurer une connexion qui permet à Intune de communiquer avec le serveur Exchange Server local :

1. Téléchargez le connecteur Exchange local Intune à partir du portail Intune.
2. Installez et configurez le connecteur Exchange sur un ordinateur de l’organisation Exchange locale.
3. Validez la connexion Exchange.
4. Répétez ces étapes pour chaque organisation Exchange supplémentaire que vous voulez connecter à Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Configuration requise pour le connecteur Exchange local d’Intune
Vous aurez besoin d’un compte avec une licence Intune qui peut être utilisé par le connecteur pour la connexion à Exchange. Le compte est spécifié quand vous installez le connecteur.  

Le tableau suivant indique la configuration requise pour l’ordinateur sur lequel vous installez le connecteur Exchange local.  

|  Condition requise  |   Plus d’informations     |
|---------------|------------------------|
|  Systèmes d'exploitation        | Intune prend en charge le connecteur Exchange local sur un ordinateur qui exécute une édition de Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />Le connecteur n’est pas pris en charge sur les installations Server Core.  |
| Microsoft Exchange          | Pour utiliser les connecteurs locaux, vous devez avoir Microsoft Exchange 2010 SP3 ou ultérieur ou la version de Microsoft Exchange Online Dedicated existante. Pour déterminer si votre environnement Exchange Online Dedicated présente la <strong>nouvelle</strong> configuration ou une configuration <strong>héritée</strong>, contactez votre responsable de comptes. |
| Autorité de gestion des appareils mobiles           | [Définit Intune comme autorité de gestion des appareils mobiles](mdm-authority-set.md). |
| Matériel              | L’ordinateur sur lequel vous installez le connecteur nécessite un processeur 1,6 GHz avec 2 Go de mémoire RAM et 10 Go d’espace disque libre. |
|  Synchronisation Active Directory             | Avant de pouvoir utiliser le connecteur pour connecter Intune à votre serveur Exchange Server, vous devez [configurer la synchronisation Active Directory](users-add.md) pour que vos utilisateurs et groupes de sécurité locaux soient synchronisés avec votre instance d’Azure Active Directory. |
| Logiciels supplémentaires         | Une installation complète de Microsoft .NET Framework 4.5 et Windows PowerShell 2.0 doit exister sur l’ordinateur qui héberge le connecteur. |
| Réseau               | L’ordinateur sur lequel vous installez le connecteur doit être dans un domaine qui entretient une relation d’approbation avec le domaine qui héberge votre instance d’Exchange Server.<br /><br />L’ordinateur nécessite des configurations qui lui permettent d’accéder au service Intune à travers les pare-feu et les serveurs proxy sur les ports 80 et 443. Les domaines utilisés par Intune comprennent manage.microsoft.com, &#42;manage.microsoft.com et &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Spécifications des applets de commande Exchange

Créez un compte d’utilisateur Active Directory destiné à être utilisé par le connecteur Exchange local. Le compte doit être autorisé à exécuter les applets de commande Windows PowerShell Exchange nécessaires suivantes :


- Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
- Get-CasMailbox, Set-CasMailbox
- Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
- Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
- Get-ActiveSyncDeviceStatistics
- Get-ActiveSyncDevice
- Get-ExchangeServer
- Get-ActiveSyncDeviceClass
- Get-Recipient
- Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
- Set-ADServerSettings
- Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Télécharger le package d’installation du logiciel Connecteur Exchange local

1. Sur un système d’exploitation Windows Server pris en charge pour le connecteur Exchange local, ouvrez le [portail Azure](https://portal.azure.com) et connectez-vous avec un compte d’utilisateur administrateur dans le serveur Exchange local et disposant d’une licence d’utilisation d’Exchange Server.

2. Accédez à **Intune** > **Accès à Exchange**.  

3. Sous **Installation**, choisissez **Connecteur local Exchange ActiveSync**, puis sélectionnez **Ajouter**.

4. Dans la page **Ajouter un connecteur**, sélectionnez **Télécharger le connecteur local**. Le connecteur Exchange local se trouve dans un dossier compressé (.zip) que vous pouvez ouvrir ou enregistrer. Dans la boîte de dialogue **Téléchargement de fichier**, choisissez **Enregistrer** pour stocker le dossier compressé dans un emplacement sécurisé.

    > [!IMPORTANT]
    > Ne renommez pas et ne déplacez pas les fichiers du dossier du connecteur Exchange local. Déplacer ou renommer le contenu du dossier entraîne l’échec de l’installation du connecteur Exchange.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installer et configurer le connecteur Exchange local d’Intune
Effectuez les étapes suivantes pour installer le connecteur Exchange local d’Intune. Si vous avez plusieurs organisations Exchange, répétez ces étapes pour chaque connecteur Exchange supplémentaire que vous voulez configurer.

1. Sur un système d’exploitation pris en charge pour le connecteur Exchange local, extrayez les fichiers de **Exchange_Connector_Setup.zip** dans un emplacement sécurisé.

2. Une fois les fichiers extraits, ouvrez le dossier d’extraction et double-cliquez sur **Exchange_Connector_Setup.exe** pour installer le connecteur Exchange local.

   > [!IMPORTANT]
   > Si le dossier de destination n’est pas un emplacement sécurisé, vous devez supprimer le fichier de certificat **MicrosoftIntune.accountcert** quand vous avez terminé d’installer vos connecteurs locaux.

3. Dans la boîte de dialogue **Microsoft Intune Exchange Connector**, sélectionnez **Serveur Microsoft Exchange sur site** ou **Serveur Microsoft Exchange hébergé**.

   ![Image montrant comment choisir le type de serveur Exchange](./media/intune-sa-exchange-connector-config.png)

   Pour un serveur Exchange local, spécifiez le nom du serveur ou le nom de domaine complet du serveur Exchange qui héberge le rôle **Serveur d’accès au client**.

   Pour un serveur Exchange hébergé, spécifiez l’adresse du serveur Exchange. Pour trouver l'URL du serveur Exchange hébergé :

   1. Ouvrez Outlook sur le web pour Office 365.

   2. Choisissez l’icône **?** dans l’angle supérieur gauche et sélectionnez **À propos de**.

   3. Recherchez la valeur **Serveur externe POP**.

   4. Choisissez **Serveur proxy** pour spécifier les paramètres du serveur proxy pour votre serveur Exchange hébergé.
       1. Sélectionnez **Utiliser un serveur proxy lors de la synchronisation des informations de l'appareil mobile**.

       2. Entrez le **nom du serveur proxy** et le **numéro de port** à utiliser pour accéder au serveur.

       3. S’il est nécessaire de fournir des informations d’identification d’utilisateur pour accéder au serveur proxy, sélectionnez **Utiliser les informations d’identification pour la connexion au serveur proxy**. Ensuite, entrez le **domaine\utilisateur** et le **mot de passe**.

       4. Choisissez **OK**.

4. Dans les champs **Utilisateur (Domaine\utilisateur)** et **Mot de passe**, entrez les informations d’identification nécessaires pour la connexion à votre serveur Exchange. Le compte que vous spécifiez doit avoir une licence d’utilisation d’Intune. 

5. Fournissez les informations d’identification nécessaires pour envoyer des notifications à la boîte aux lettres Exchange Server d’un utilisateur. Cet utilisateur peut être dédié aux notifications seulement. Il a besoin d’une boîte aux lettres Exchange pour envoyer des notifications par e-mail. Vous pouvez configurer ces notifications avec des stratégies d’accès conditionnel dans Intune.  

   Vérifiez que le service de découverte automatique et les services web Exchange sont configurés sur le serveur d'accès au client Exchange. Pour plus d’informations, consultez [Serveur d’accès au client](https://technet.microsoft.com/library/dd298114.aspx).

6. Dans le champ **Mot de passe** , entrez le mot de passe de ce compte pour permettre à Intune d’accéder au serveur Exchange Server.

   > [!NOTE]
   > Pour que la connexion réussisse, le compte que vous utilisez pour vous connecter au locataire doit être au moins un Administrateur de service Intune. Sans cela, vous obtiendrez une connexion qui a échoué avec l’erreur : « Le serveur distant a retourné une erreur : (400) Demande incorrecte ».

7. Choisissez **Se connecter**.

   > [!NOTE]
   > La configuration de la connexion peut prendre quelques minutes.

Lors de la configuration, le connecteur Exchange stocke vos paramètres de proxy pour permettre l’accès à Internet. Si vos paramètres de proxy changent, vous devez reconfigurer le connecteur Exchange pour lui appliquer les nouveaux paramètres de proxy.

Une fois la connexion configurée par le connecteur Exchange, les appareils mobiles qui sont associés à des utilisateurs gérés dans Exchange sont automatiquement synchronisés et ajoutés au connecteur Exchange. Cette synchronisation peut prendre un certain temps.

> [!NOTE]
> Si vous avez installé le connecteur Exchange local et qu’à un moment donné, vous supprimez la connexion Exchange, vous devez désinstaller le connecteur Exchange local de l’ordinateur où il a été installé.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installer des connecteurs pour plusieurs organisations Exchange
Intune prend en charge plusieurs connecteurs Exchange locaux par abonnement. Dans le cas d’un locataire avec plusieurs organisations Exchange, vous pouvez configurer un et un seul connecteur pour chaque organisation Exchange. 

Si vous devez installer des connecteurs pour établir une connexion à plusieurs organisations Exchange, téléchargez le dossier .zip une seule fois, puis réutilisez le même téléchargement pour chaque connecteur à installer. Pour chaque connecteur supplémentaire, suivez les étapes décrites dans la section précédente afin d’extraire et d’exécuter le programme d’installation sur un serveur de l’organisation Exchange.

Les fonctionnalités de haute disponibilité, de supervision et de synchronisation manuelle décrites dans les sections suivantes sont prises en charge pour chaque organisation Exchange qui se connecte à Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local 
Avec la haute disponibilité, le connecteur Exchange local peut, en cas d’indisponibilité du serveur d’accès au client Exchange qu’il utilise, basculer vers un autre serveur d’accès au client pour cette organisation Exchange. Le connecteur Exchange lui-même ne prend pas en charge la haute disponibilité. Si le connecteur échoue, il n’y a pas de basculement automatique ; vous devez alors remplacer ce connecteur en [installant un nouveau connecteur](#reinstall-the-on-premises-exchange-connector). 

Pour effectuer le basculement, après avoir correctement créé une connexion à Exchange à l’aide du serveur d’accès au client spécifié, le connecteur découvre des serveurs d’accès au client supplémentaires pour cette organisation Exchange. Connaissant des serveurs d’accès au client supplémentaires, le connecteur peut basculer vers un d’entre eux, sous réserve qu’il soit disponible, jusqu’à ce que le serveur d’accès au client principal redevienne disponible. Par défaut, la découverte de serveurs d’accès au client supplémentaires est activée. Vous pouvez désactiver le basculement en procédant de la façon suivante :  
1. Sur le serveur où est installé le connecteur Exchange, accédez à %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. À l’aide d’un éditeur de texte, ouvrez **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Remplacez &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; par &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; pour désactiver la fonctionnalité.  
 
## <a name="optional-performance-tuning-for-the-exchange-connector"></a>Optimisation des performances facultative pour le connecteur Exchange  

Quand vous prenez en charge 5 000 appareils ou plus avec Exchange ActiveSync, vous pouvez configurer un paramètre facultatif pour améliorer les performances du connecteur. Les performances améliorées sont obtenues en permettant à Exchange d’utiliser plusieurs instances d’un espace d’exécution de commandes PowerShell. 

Avant de procéder à cette modification, vérifiez que le compte que vous utilisez pour exécuter le connecteur Exchange n’est pas utilisé à d’autres fins de gestion d’Exchange. Cela est dû au fait qu’Exchange a un nombre limité d’espaces d’exécution par compte, dont la plupart seront utilisés par le connecteur. 

Cette modification des performances n’est pas adaptée aux connecteurs qui s’exécutent sur du matériel plus ancien ou plus lent.  

1. Sur le serveur où le connecteur est installé, ouvrez le répertoire d’installation des connecteurs.  L’emplacement par défaut est *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Éditez le fichier *OnPremisesExchangeConnectorServiceConfiguration.xml*.
3. Recherchez **EnableParallelCommandSupport** et définissez sa valeur sur **true** :  
     
   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>
4. Enregistrez le fichier, puis redémarrez le service Microsoft Intune Exchange Connector.

## <a name="reinstall-the-on-premises-exchange-connector"></a>Réinstaller le connecteur Exchange local
Vous pouvez être amené à réinstaller un connecteur Exchange. Un seul connecteur étant pris en charge pour la connexion à chaque organisation Exchange, si vous installez un deuxième connecteur pour une organisation, ce nouveau connecteur remplace le connecteur d’origine.

1. Suivez les étapes indiquées dans la section [Installer et configurer le connecteur Exchange local d’Intune](#install-and-configure-the-intune-on-premises-exchange-connector) pour démarrer l’installation du nouveau connecteur. 
2. Quand vous y êtes invité, sélectionnez **Remplacer** pour installer le nouveau connecteur.  
   ![Invite de configuration pour remplacer un connecteur](./media/exchange-connector-install/prompt-to-replace.png)

3. Reprenez les étapes de la procédure précédente et reconnectez-vous à Intune.
4. Quand le dernier écran apparaît, sélectionnez **Fermer** pour terminer l’installation.  
   ![Installation terminée](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Surveiller l’activité du connecteur Exchange

Une fois que vous avez correctement configuré le connecteur Exchange, vous pouvez afficher l’état de la connexion et la dernière tentative de synchronisation réussie. Pour valider la connexion du connecteur Exchange :

1. Dans le tableau de bord Intune, choisissez **Accès à Exchange**.
2. Sélectionnez **Accès à Exchange sur site** afin de vérifier l’état de connexion pour chaque connecteur Exchange.

Vous pouvez également vérifier la date et l'heure de la dernière tentative de synchronisation réussie.
--> 

### <a name="system-center-operations-manager-management-pack"></a>Pack d’administration de System Center Operations Manager

À compter de la version 1710 d’Intune, vous pouvez utiliser le [pack d’administration Operations Manager pour le connecteur Exchange et Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). L’utilisation du pack d’administration offre différents moyens de superviser le connecteur Exchange quand vous devez résoudre des problèmes.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forcer manuellement une synchronisation rapide ou une synchronisation complète
Un connecteur Exchange local synchronise automatiquement et régulièrement Intune et les enregistrements d’appareils EAS. Si l’état de conformité d’un appareil change, le processus de synchronisation automatique met régulièrement à jour les enregistrements afin que l’accès à l’appareil puisse être bloqué ou autorisé.

- La **synchronisation rapide** est exécutée régulièrement, plusieurs fois par jour. Une synchronisation rapide récupère les informations sur l’appareil pour les utilisateurs sous licence Intune et ciblés par l’accès conditionnel Exchange local qui ont changés depuis la dernière synchronisation.

- La **synchronisation complète** est exécutée par défaut une fois par jour. Une synchronisation complète récupère les informations sur l’appareil pour tous les utilisateurs sous licence Intune et ciblés par l’accès conditionnel Exchange local. Une synchronisation complète récupère également les informations du serveur Exchange et garantit que la configuration spécifiée par Intune dans le portail Azure est mise à jour sur le serveur Exchange. 


Vous pouvez forcer un connecteur à exécuter une synchronisation à l’aide des options **Synchronisation rapide** ou **Synchronisation complète** du tableau de bord Intune en effectuant les étapes suivantes :

   1. Dans le tableau de bord Intune, choisissez **Accès à Exchange**.
   2. Sélectionnez **Accès à Exchange sur site**.
   3. Sélectionnez le connecteur à synchroniser, puis choisissez **Synchronisation rapide** ou **Synchronisation complète**.

## <a name="next-steps"></a>Étapes suivantes
[Créer une stratégie d’accès conditionnel pour Exchange sur site](conditional-access-exchange-create.md)
