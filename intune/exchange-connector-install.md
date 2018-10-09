---
title: Configurer le connecteur Exchange local de Microsoft Intune
titleSuffix: ''
description: Utilisez le connecteur Exchange local pour gérer l’accès de l’appareil aux boîtes aux lettres Exchange en fonction de l’inscription Intune et d’Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e12ab106b44d217d7e7b4b1a466fd5b12a9fb528
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231829"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Configurer le connecteur Exchange local Intune dans Microsoft Intune Azure

Dans un environnement Exchange Server local, l’accès conditionnel Intune peut être utilisé pour autoriser ou bloquer l’accès à des boîtes aux lettres locales Exchange. Utilisez des connecteurs locaux Exchange Active Sync pour connecter Intune à vos organisations Exchange, et configurer l’accès conditionnel Intune ainsi que des stratégies de conformité des appareils. Ensuite, quand un appareil tente de se connecter à Exchange, Intune détermine si l’appareil est inscrit dans Intune et conforme. Pour déterminer quels appareils sont inscrits dans Intune, le connecteur Exchange local mappe les enregistrements Exchange Active Sync (EAS) dans Exchange Server à des enregistrements Intune. Pour plus d’informations sur la manière dont cela fonctionne, consultez [Pour Quelles sont les utilisations courantes de l’accès conditionnel avec Intune ?](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune prend désormais en charge plusieurs connecteurs Exchange locaux par abonnement. Si vous avez plusieurs organisations Exchange locales, vous pouvez configurer un connecteur distinct pour chacune d’elles.

Pour configurer une connexion qui permet à Microsoft Intune de communiquer avec le serveur Exchange Server local, voici les étapes générales à suivre :

1.  Téléchargez le connecteur Exchange local Intune à partir du portail Azure.
2.  Installez et configurez le connecteur Exchange sur un ordinateur de l’organisation Exchange locale.
3.  Validez la connexion Exchange.
4. Répétez ces étapes pour chaque organisation Exchange que vous voulez connecter à Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Configuration requise pour le connecteur Exchange local d’Intune
Le tableau suivant indique la configuration requise pour l’ordinateur sur lequel vous installez le connecteur Exchange local.


|            Condition requise             |                                                                                                                                                                                                        Plus d’informations                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Systèmes d'exploitation          |                                                               Intune prend en charge le connecteur Exchange local sur un ordinateur qui exécute une édition de Windows Server 2008 SP2 64 bits, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2016.<br /><br />Le connecteur n'est pas pris en charge sur une installation Server Core.                                                                |
|         Microsoft Exchange         |                                                                           Les connecteurs locaux exigent Microsoft Exchange 2010 SP1 ou ultérieur, ou la version de Microsoft Exchange Online Dedicated héritée. Pour déterminer si votre environnement Exchange Online Dedicated présente la <strong>nouvelle</strong> configuration ou une configuration <strong>héritée</strong>, contactez votre responsable de comptes.                                                                           |
| Autorité de gestion des appareils mobiles |                                                                                                                              [Définit Intune comme autorité de gestion des appareils mobiles](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).                                                                                                                               |
|              Matériel              |                                                                                                                                                     L’ordinateur sur lequel vous installez le connecteur nécessite un processeur 1,6 GHz avec 2 Go de mémoire RAM et 10 Go d’espace disque libre.                                                                                                                                                      |
|  Synchronisation Active Directory  |                                                                                      Avant de pouvoir utiliser le connecteur pour connecter Intune à votre serveur Exchange Server, vous devez [configurer la synchronisation Active Directory](users-add.md) pour que vos utilisateurs et groupes de sécurité locaux soient synchronisés avec votre instance d’Azure Active Directory.                                                                                      |
|        Logiciels supplémentaires         |                                                                                                                                           Une installation complète de Microsoft .NET Framework 4.5 et Windows PowerShell 2.0 doit exister sur l’ordinateur qui héberge le connecteur.                                                                                                                                           |
|              Réseau               | L’ordinateur sur lequel vous installez le connecteur doit être dans un domaine qui entretient une relation d’approbation avec le domaine qui héberge votre instance d’Exchange Server.<br /><br />L’ordinateur nécessite des configurations qui lui permettent d’accéder au service Intune à travers les pare-feu et les serveurs proxy sur les ports 80 et 443. Les domaines utilisés par Intune comprennent manage.microsoft.com, &#42;manage.microsoft.com et &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Spécifications des applets de commande Exchange

Vous devez créer un compte d’utilisateur Active Directory utilisé par le connecteur Exchange local. Le compte doit être autorisé à exécuter les applets de commande Windows PowerShell Exchange nécessaires suivantes :


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Télécharger le package d’installation du logiciel Connecteur Exchange local

1. Sur un système d’exploitation Windows Server pris en charge pour le connecteur Exchange local, ouvrez le [portail Azure](http://portal.azure.com) et connectez-vous avec un compte d’utilisateur administrateur dans le serveur Exchange local et disposant d’une licence d’utilisation d’Exchange Server.

2. Choisissez **Tous les services** dans le menu de gauche, puis entrez **Intune** dans le filtre de la zone de texte.

3. Choisissez **Intune**. Quand le tableau de bord Intune s’affiche, choisissez **Accès local**.

4. Sous **Configurer**, choisissez **Connecteurs Exchange ActiveSync**, puis **Télécharger le connecteur local**.

5.  Le connecteur Exchange local se trouve dans un dossier compressé (.zip) que vous pouvez ouvrir ou enregistrer. Dans la boîte de dialogue **Téléchargement de fichier**, choisissez **Enregistrer** pour stocker le dossier compressé dans un emplacement sécurisé.

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

   5. Dans les champs **Utilisateur (Domaine\utilisateur)** et **Mot de passe**, entrez les informations d’identification nécessaires pour la connexion à votre serveur Exchange.

   6.  Fournissez les informations d’identification nécessaires pour envoyer des notifications à la boîte aux lettres Exchange Server d’un utilisateur. Cet utilisateur peut être dédié aux notifications seulement. Il a besoin d’une boîte aux lettres Exchange pour pouvoir envoyer des notifications par e-mail. Vous pouvez configurer ces notifications avec des stratégies d’accès conditionnel dans Intune.  

       Vérifiez que le service de découverte automatique et les services web Exchange sont configurés sur le serveur d'accès au client Exchange. Pour plus d’informations, consultez [Serveur d’accès au client](https://technet.microsoft.com/library/dd298114.aspx).

   7.  Dans le champ **Mot de passe** , entrez le mot de passe de ce compte pour permettre à Intune d’accéder au serveur Exchange Server.

   8. Choisissez **Se connecter**.

   > [!NOTE]
   > La configuration de la connexion peut prendre quelques minutes.

Lors de la configuration, le connecteur Exchange stocke vos paramètres de proxy pour permettre l’accès à Internet. Si vos paramètres de proxy changent, vous devez reconfigurer le connecteur Exchange pour lui appliquer les paramètres de proxy mis à jour.

Une fois la connexion configurée par le connecteur Exchange, les appareils mobiles qui sont associés à des utilisateurs gérés dans Exchange sont automatiquement synchronisés et ajoutés au connecteur Exchange. Cette synchronisation peut prendre un certain temps.

> [!NOTE]
> Si vous avez installé le connecteur Exchange local et qu’à un moment donné, vous supprimez la connexion Exchange, vous devez désinstaller le connecteur Exchange local de l’ordinateur où il a été installé.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installer des connecteurs pour plusieurs organisations Exchange
Intune prend en charge plusieurs connecteurs Exchange locaux par abonnement. Pour un locataire disposant de plusieurs organisations Exchange, vous pouvez configurer un connecteur pour chaque organisation Exchange. Télécharger le dossier .zip une seule fois, puis suivez les étapes décrites dans la section précédente pour chaque organisation Exchange afin d’extraire et d’exécuter le programme d’installation sur un serveur de l’organisation.

Les fonctionnalités de haute disponibilité, de surveillance et de synchronisation manuelle décrites dans les sections suivantes sont prises en charge pour chaque organisation Exchange connectée à Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local 
Une fois que le connecteur Exchange crée une connexion à Exchange en utilisant l’autorité de certification spécifiée, le connecteur a la possibilité de découverte d’autres autorités de certification. Si l’autorité de certification principale est indisponible, le connecteur bascule vers une autre autorité de certification disponible, jusqu'à ce que l’autorité de certification principale redevienne disponible. Cette fonctionnalité est activée par défaut. Vous pouvez désactiver cette fonctionnalité en procédant comme suit :
1. Sur le serveur où est installé le connecteur Exchange, accédez à %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. À l’aide d’un éditeur de texte, ouvrez **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Remplacez &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; par &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; pour désactiver la fonctionnalité.    


## <a name="monitor-the-exchange-connector-activity"></a>Surveiller l’activité du connecteur Exchange

Une fois que vous avez correctement configuré les connecteurs Exchange, vous pouvez afficher l’état des connexions et la dernière tentative de synchronisation réussie. Pour valider les connexions des connecteurs Exchange :

1. Dans le tableau de bord Intune, choisissez **Accès local**.
2. Sous **Configurer**, sélectionnez **Connecteurs Exchange ActiveSync** pour vérifier l’état de connexion de chaque connecteur Exchange.

Vous pouvez également vérifier la date et l'heure de la dernière tentative de synchronisation réussie.

### <a name="system-center-operations-manager-scom-management-pack"></a>Pack d’administration de System Center Operations Manager (SCOM)

À partir de la version Intune 1710, vous pouvez utiliser le [pack d’administration SCOM pour le connecteur Exchange et Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Ce pack offre différents moyens de surveiller le connecteur Exchange quand vous devez résoudre des problèmes.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forcer manuellement une synchronisation rapide ou une synchronisation complète
Un connecteur Exchange local synchronise automatiquement les enregistrements d’appareils EAS et Intune de façon régulière. Si l’état de conformité d’un appareil change, le processus de synchronisation automatique met régulièrement à jour les enregistrements afin que l’accès à l’appareil puisse être bloqué ou autorisé en conséquence.

   - La **synchronisation rapide** est exécutée régulièrement, plusieurs fois par jour. Une synchronisation rapide récupère les informations sur l’appareil pour les utilisateurs sous licence Intune et ciblés par l’accès conditionnel Exchange local qui ont changés depuis la dernière synchronisation.

   - La **synchronisation complète** est exécutée par défaut une fois par jour. Une synchronisation complète récupère les informations sur l’appareil pour tous les utilisateurs sous licence Intune et ciblés par l’accès conditionnel Exchange local. Une synchronisation complète récupère également les informations du serveur Exchange et garantit que la configuration spécifiée par Intune dans le portail Azure est mise à jour sur le serveur Exchange. 

Vous pouvez forcer un connecteur à exécuter une synchronisation à l’aide des options **Synchronisation rapide** ou **Synchronisation complète** du tableau de bord Intune en effectuant les étapes suivantes :

   1. Dans le tableau de bord Intune, choisissez **Accès local**.
   2. Sous **Configurer**, choisissez **Connecteurs Exchange Active Sync**.
   3. Sélectionnez le connecteur à synchroniser, puis choisissez **Synchronisation rapide** ou **Synchronisation complète**.

## <a name="next-steps"></a>Étapes suivantes
[Création d’une stratégie d’accès conditionnel pour Exchange sur site](conditional-access-exchange-create.md)
