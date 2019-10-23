---
title: Configurer un connecteur Microsoft Intune Exchange
titleSuffix: Microsoft Intune
description: Utilisez le connecteur Intune Exchange local pour gérer l’accès de l’appareil aux boîtes aux lettres Exchange en fonction de l’inscription Intune et d’Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30b5debc6e1ab113a08d8930f96f6cbc9bf12b48
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509524"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>Configurer le connecteur Intune Exchange local
Pour protéger l'accès à Exchange, Intune s'appuie sur un composant local connu sous le nom de connecteur Microsoft Intune Exchange. Ce connecteur est aussi appelé connecteur *Exchange ActiveSync local* dans certaines parties de la console Intune. 

Les informations contenues dans cet article peuvent vous aider à installer et à surveiller le connecteur Intune Exchange. Vous pouvez utiliser le connecteur avec vos [stratégies d’accès conditionnel pour autoriser ou bloquer l’accès aux boîtes aux lettres locales Exchange](conditional-access-exchange-create.md). 

Le connecteur est installé et s’exécute sur votre matériel local. Il découvre les appareils qui se connectent à Exchange, communiquant des informations sur ces appareils au service Intune. Le connecteur autorise ou bloque les appareils en fonction de leur inscription et de leur conformité. Ces communications utilisent le protocole HTTPS.

Quand un appareil tente d’accéder à votre serveur Exchange local, le connecteur Exchange mappe les enregistrements Exchange Active Sync (EAS) dans le serveur Exchange aux enregistrements Intune pour vérifier l’inscription des appareils auprès d’Intune et la conformité aux stratégies de votre appareil. En fonction de vos stratégies d’accès conditionnel, l’accès peut être autorisé ou refusé à l’appareil. Pour plus d’informations, consultez [Quelles sont les utilisations courantes de l’accès conditionnel avec Intune ?](conditional-access-intune-common-ways-use.md).

Les opérations de *découverte* et d’*autorisation et de blocage* sont effectuées à l'aide d’applets PowerShell Exchange standard. Ces opérations utilisent le compte de service fourni lors de l'installation initiale du connecteur Exchange. 

Intune prend en charge l’installation de plusieurs connecteurs Exchange locaux par abonnement. Si vous avez plusieurs organisations Exchange locales, vous pouvez configurer un connecteur distinct pour chacune d’elles. Toutefois, un seul connecteur peut être installé pour chaque organisation Exchange.  

Voici les étapes générales à suivre pour configurer une connexion qui permet à Intune de communiquer avec le serveur Exchange Server local :

1. Téléchargez le connecteur local à partir du portail Intune.
2. Installez et configurez le connecteur Exchange sur un ordinateur de l’organisation Exchange locale.
3. Validez la connexion Exchange.
4. Répétez ces étapes pour chaque organisation Exchange supplémentaire que vous voulez connecter à Intune.

## <a name="intune-exchange-connector-requirements"></a>Configuration requise pour le connecteur Intune Exchange

Pour vous connecter à Exchange, vous avez besoin d'un compte avec une licence Intune utilisable par le connecteur. Vous spécifiez le compte lorsque vous installez le connecteur.  

Le tableau suivant indique la configuration requise pour l’ordinateur sur lequel vous installez le connecteur Intune Exchange.  

|  Condition requise  |   Plus d’informations     |
|---------------|------------------------|
|  Systèmes d'exploitation        | Intune prend en charge le connecteur Intune Exchange sur un ordinateur qui exécute une édition de Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />Le connecteur n’est pas pris en charge sur les installations Server Core.  |
| Microsoft Exchange          | Pour utiliser les connecteurs locaux, vous devez avoir Microsoft Exchange 2010 SP3 ou ultérieur ou la version de Microsoft Exchange Online Dedicated existante. Pour déterminer si votre environnement Exchange Online Dedicated présente la *nouvelle* configuration ou une configuration *héritée*, contactez votre responsable de comptes. |
| Autorité de gestion des appareils mobiles           | [Définit Intune comme autorité de gestion des appareils mobiles](../fundamentals/mdm-authority-set.md). |
| Matériel              | L’ordinateur sur lequel vous installez le connecteur nécessite un processeur 1,6 GHz avec 2 Go de mémoire RAM et 10 Go d’espace disque libre. |
|  Synchronisation Active Directory             | Avant d'utiliser le connecteur pour connecter Intune à votre serveur Exchange, [configurez la synchronisation Active Directory](../fundamentals/users-add.md). Vos utilisateurs et groupes de sécurité locaux doivent être synchronisés avec votre instance d'Azure Active Directory. |
| Logiciels supplémentaires         | L’ordinateur qui héberge le connecteur doit disposer d’une installation complète de Microsoft .NET Framework 4.5 et Windows PowerShell 2.0. |
| Réseau               | L’ordinateur sur lequel vous installez le connecteur doit être dans un domaine qui entretient une relation d’approbation avec le domaine qui héberge votre instance d’Exchange Server.<br /><br />Configurez l’ordinateur pour l’autoriser à accéder au service Intune à travers les pare-feu et les serveurs proxy sur les ports 80 et 443. Intune utilise ces domaines : <br> - manage.microsoft.com <br> - \*manage.microsoft.com<br> - \*.manage.microsoft.com <br><br> Le connecteur Intune Exchange communique avec les services suivants : <br> - Service Intune : Port HTTPS 443 <br> - Serveur d'accès au client Exchange (CAS) : Port de service WinRM 443<br> - Exchange Autodiscover 443<br> - Exchange Web Services (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Spécifications des applets de commande Exchange

Créez un compte d’utilisateur Active Directory pour le connecteur Intune Exchange. Le compte doit être autorisé à exécuter les applets de commande Windows PowerShell Exchange suivantes :  

- `Get-ActiveSyncOrganizationSettings`, `Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`, `Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`, `Set-ActiveSyncMailboxPolicy`, `New-ActiveSyncMailboxPolicy`, `Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`, `Set-ActiveSyncDeviceAccessRule`, `New-ActiveSyncDeviceAccessRule`, `Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`, `Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>Télécharger le package d'installation

1. Sur un serveur Windows prenant en charge le connecteur Intune Exchange, connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Utilisez un compte administrateur du serveur Exchange local et possédant une licence pour utiliser Exchange Server.

2. Accédez à **Intune** > **Accès à Exchange**.  

3. Sous **Installation**, choisissez **Connecteur local Exchange ActiveSync**, puis sélectionnez **Ajouter**.

4. Dans la page **Ajouter un connecteur**, sélectionnez **Télécharger le connecteur local**. Le connecteur Intune Exchange se trouve dans un dossier compressé (.zip) que vous pouvez ouvrir ou enregistrer. Dans la boîte de dialogue **Téléchargement de fichier**, choisissez **Enregistrer** pour stocker le dossier compressé dans un emplacement sécurisé.


## <a name="install-and-configure-the-intune-exchange-connector"></a>Installer et configurer le connecteur Intune Exchange

Suivez ces étapes pour installer le connecteur Intune Exchange. Si vous avez plusieurs organisations Exchange, répétez les étapes pour chaque connecteur Exchange que vous voulez configurer.

1. Sur un système d’exploitation pris en charge pour le connecteur Intune Exchange, extrayez les fichiers de **Exchange_Connector_Setup.zip** dans un emplacement sécurisé.
   > [!IMPORTANT]
   > Ne renommez pas et ne déplacez pas les fichiers du dossier *Exchange_Connector_Setup*. Ces modifications entraîneraient l'échec de l'installation du connecteur.

2. Une fois les fichiers extraits, ouvrez le dossier d’extraction et double-cliquez sur **Exchange_Connector_Setup.exe** pour installer le connecteur.

   > [!IMPORTANT]
   > Si le dossier de destination n’est pas un emplacement sécurisé, supprimez le fichier de certificat *MicrosoftIntune.accountcert* quand vous avez terminé d’installer vos connecteurs locaux.

3. Dans la boîte de dialogue **Microsoft Intune Exchange Connector**, sélectionnez **Serveur Microsoft Exchange sur site** ou **Serveur Microsoft Exchange hébergé**.

   ![Image montrant comment choisir le type de serveur Exchange](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Pour un serveur Exchange local, spécifiez le nom du serveur ou le nom de domaine complet du serveur Exchange qui héberge le rôle **Serveur d’accès au client**.

   Pour un serveur Exchange hébergé, spécifiez l’adresse du serveur Exchange. Pour trouver l'URL du serveur Exchange hébergé :

   1. Ouvrez Outlook pour Office 365.

   2. Choisissez l’icône **?** dans l’angle supérieur gauche et sélectionnez **À propos de**.

   3. Recherchez la valeur **Serveur externe POP**.

   4. Choisissez **Serveur proxy** pour spécifier les paramètres du serveur proxy pour votre serveur Exchange hébergé.

       1. Sélectionnez **Utiliser un serveur proxy lors de la synchronisation des informations de l'appareil mobile**.

       1. Entrez le **nom du serveur proxy** et le **numéro de port** à utiliser pour accéder au serveur.

       1. S’il est nécessaire de fournir des informations d’identification d’utilisateur pour accéder au serveur proxy, sélectionnez **Utiliser les informations d’identification pour la connexion au serveur proxy**. Ensuite, entrez le **domaine\utilisateur** et le **mot de passe**.

       1. Choisissez **OK**.

4. Dans les champs **Utilisateur (domaine\utilisateur)** et **Mot de passe**, entrez les informations d’identification pour la connexion à votre serveur Exchange. Le compte que vous spécifiez doit avoir une licence d’utilisation d’Intune. 

5. Fournissez les informations d’identification pour envoyer des notifications à la boîte aux lettres Exchange Server d’un utilisateur. Cet utilisateur peut être dédié aux notifications seulement. Il a besoin d’une boîte aux lettres Exchange pour envoyer des notifications par e-mail. Vous pouvez configurer ces notifications en utilisant des stratégies d’accès conditionnel dans Intune.  

   Vérifiez que le service de découverte automatique et les services web Exchange sont configurés sur le serveur d'accès au client (CAS) Exchange. Pour plus d’informations, consultez [Serveur d’accès au client](https://technet.microsoft.com/library/dd298114.aspx).

6. Dans le champ **Mot de passe** , entrez le mot de passe de ce compte pour permettre à Intune d’accéder au serveur Exchange Server.

   > [!NOTE]
   > Le compte que vous utilisez pour vous connecter au locataire doit être au moins un administrateur de service Intune. Sans ce compte administrateur, la connexion échouera avec l'erreur « Le serveur distant a renvoyé une erreur : (400) Demande incorrecte ».

7. Choisissez **Se connecter**.

   > [!NOTE]
   > La configuration de la connexion peut prendre quelques minutes.

Lors de la configuration, le connecteur Exchange stocke vos paramètres de proxy pour permettre l’accès à Internet. Si vos paramètres de proxy changent, reconfigurez le connecteur Exchange pour lui appliquer les nouveaux paramètres de proxy.

Une fois la connexion configurée par le connecteur Exchange, les appareils mobiles qui sont associés à des utilisateurs gérés dans Exchange sont automatiquement synchronisés et ajoutés au connecteur Exchange. Cette synchronisation peut prendre un certain temps.

> [!NOTE]
> Si vous installez le connecteur Intune Exchange et que vous devez ensuite supprimer la connexion Exchange, vous devez désinstaller le connecteur de l'ordinateur où il a été installé.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installer des connecteurs pour plusieurs organisations Exchange

Intune prend en charge plusieurs connecteurs Intune Exchange par abonnement. Pour un locataire disposant de plusieurs organisations Exchange, vous pouvez configurer un seul connecteur pour chaque organisation Exchange. 

Pour installer des connecteurs permettant de se connecter à plusieurs organisations Exchange, téléchargez le dossier .zip. Réutilisez ce même téléchargement pour chaque connecteur que vous installez. Pour chaque connecteur supplémentaire, suivez les étapes décrites dans la section précédente afin d’extraire et d’exécuter le programme d’installation sur un serveur de l’organisation Exchange.

Chaque organisation Exchange qui se connecte à Intune prend en charge la haute disponibilité, la surveillance et la synchronisation manuelle. Les sections suivantes décrivent ces différentes fonctionnalités.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>Prise en charge d’un haut niveau de disponibilité pour le connecteur Intune Exchange local  

Pour le connecteur local, la haute disponibilité signifie qu’en cas d’indisponibilité du serveur d’accès au client Exchange utilisé par le connecteur, ce dernier peut basculer vers un autre serveur d’accès au client pour cette organisation Exchange. Le connecteur Exchange lui-même ne prend pas en charge la haute disponibilité. La défaillance du connecteur n’entraîne aucun basculement automatique. Vous devez [installer un nouveau connecteur](#reinstall-the-intune-exchange-connector) pour remplacer le connecteur défaillant. 

Pour le basculement, le connecteur utilise le serveur d’accès au client spécifié afin d’établir une connexion réussie à Exchange. Il découvre ensuite d'autres serveurs d’accès au client pour cette organisation Exchange. Grâce à cette découverte, le connecteur peut basculer vers un d’entre eux, sous réserve qu’il soit disponible, jusqu’à ce que le serveur d’accès au client principal redevienne disponible. 

Par défaut, la découverte de serveurs d’accès au client supplémentaires est activée. Si vous devez désactiver le basculement :  
1. Sur le serveur où est installé le connecteur Exchange, accédez à **%*ProgramData*%\Microsoft\Windows Intune Exchange Connector**. 
2. À l’aide d’un éditeur de texte, ouvrez **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Remplacez **\<IsCasFailoverEnabled>*true*\</IsCasFailoverEnabled>** par **\<IsCasFailoverEnabled>*false*\</IsCasFailoverEnabled>** .  
 
## <a name="performance-tune-the-exchange-connector-optional"></a>Optimisation des performances pour le connecteur Exchange (optionnel)

Si Exchange ActiveSync prend en charge 5 000 appareils ou plus , vous pouvez configurer un paramètre facultatif pour améliorer les performances du connecteur. Vous pouvez améliorer les performances en permettant à Exchange d’utiliser plusieurs instances d’un espace d’exécution de commandes PowerShell. 

Avant de procéder à cette modification, vérifiez que le compte que vous utilisez pour exécuter le connecteur Exchange n’est pas utilisé à d’autres fins de gestion d’Exchange. Un compte Exchange comporte un nombre limité d'espaces d'exécution, et le connecteur utilisera la plupart d'entre eux. 

L’amélioration des performances n’est pas adaptée aux connecteurs qui s’exécutent sur du matériel plus ancien ou plus lent.  

Pour améliorer les performances du connecteur Exchange : 

1. Sur le serveur où le connecteur est installé, ouvrez le répertoire d’installation du connecteur.  L’emplacement par défaut est *C:\ProgramData\Microsoft\Windows Intune Exchange Connector*. 
2. Éditez le fichier *OnPremisesExchangeConnectorServiceConfiguration.xml*.
3. Recherchez **EnableParallelCommandSupport** et définissez sa valeur sur **true** :  
     
   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>
4. Enregistrez le fichier, puis redémarrez le service Microsoft Intune Exchange Connector.

## <a name="reinstall-the-intune-exchange-connector"></a>Réinstaller le connecteur Intune Exchange

Vous pouvez être amené à réinstaller un connecteur Intune Exchange. Un seul connecteur pouvant être connecté à chaque organisation Exchange, si vous installez un deuxième connecteur pour l’organisation, ce nouveau connecteur remplace le connecteur d’origine.

1. Pour installer le nouveau connecteur, suivez les étapes de la section [Installer et configurer le connecteur Exchange](#install-and-configure-the-intune-exchange-connector). 
2. Quand vous y êtes invité, sélectionnez **Remplacer** pour installer le nouveau connecteur.  
   ![Avertissement de configuration pour remplacer un connecteur](./media/exchange-connector-install/prompt-to-replace.png)

3. Continuez les étapes à partir de la section [Installer et configurer le connecteur Intune Exchange](#install-and-configure-the-intune-exchange-connector), puis reconnectez-vous à Intune.
4. Dans la dernière fenêtre, sélectionnez **Fermer** pour terminer l'installation.  
   ![Terminer l’installation](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-an-exchange-connector"></a>Superviser un connecteur Exchange

Une fois que vous avez correctement configuré le connecteur Exchange, vous pouvez afficher l’état de la connexion et la dernière tentative de synchronisation réussie. 

Pour valider la connexion du connecteur Exchange :

1. Dans le tableau de bord Intune, choisissez **Accès à Exchange**.
2. Sélectionnez **Accès à Exchange sur site** afin de vérifier l’état de connexion pour chaque connecteur Exchange.

Vous pouvez également vérifier la date et l'heure de la dernière tentative de synchronisation réussie.

À compter de la version 1710 d’Intune, vous pouvez utiliser le [pack d’administration System Center Operations Manager pour le connecteur Exchange et Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Le pack d’administration offre différents moyens de superviser le connecteur Exchange quand vous devez résoudre des problèmes.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forcer manuellement une synchronisation rapide ou une synchronisation complète

Un connecteur Intune Exchange synchronise automatiquement et régulièrement Intune et les enregistrements d’appareils EAS. Si l’état de conformité d’un appareil change, le processus de synchronisation automatique met régulièrement à jour les enregistrements afin que l’accès à l’appareil puisse être bloqué ou autorisé.

- Une **synchronisation rapide** est exécutée régulièrement, plusieurs fois par jour. Une synchronisation rapide récupère les informations sur l’appareil pour les utilisateurs sous licence Intune et ciblés par l’accès conditionnel Exchange local qui ont changé depuis la dernière synchronisation.

- Une **synchronisation complète** est exécutée par défaut une fois par jour. Une synchronisation complète récupère les informations sur l’appareil pour tous les utilisateurs sous licence Intune et ciblés par l’accès conditionnel Exchange local. Une synchronisation complète récupère également les informations du serveur Exchange et garantit que la configuration spécifiée par Intune dans le portail Azure est mise à jour sur le serveur Exchange. 


Vous pouvez forcer un connecteur à exécuter une synchronisation à l’aide des options **Synchronisation rapide** ou **Synchronisation complète** du tableau de bord Intune :

   1. Dans le tableau de bord Intune, choisissez **Accès à Exchange**.
   2. Sélectionnez **Accès à Exchange sur site**.
   3. Sélectionnez le connecteur à synchroniser, puis choisissez **Synchronisation rapide** ou **Synchronisation complète**.

## <a name="next-steps"></a>Étapes suivantes

Créez une [stratégie d’accès conditionnel pour les serveurs Exchange locaux](conditional-access-exchange-create.md).
