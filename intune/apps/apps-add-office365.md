---
title: Ajouter des applications Office 365 à des appareils Windows 10 à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez comment utiliser Microsoft Intune pour installer des applications Office 365 sur des appareils Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2cb247ec25b134fa9810a426be88b7fc90999394
ms.sourcegitcommit: 2c8a41ee95a3fde150667a377770e51b621ead65
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73635398"
---
# <a name="add-office-365-apps-to-windows-10-devices-with-microsoft-intune"></a>Ajouter des applications Office 365 à des appareils Windows 10 avec Microsoft Intune

Pour pouvoir affecter, surveiller, configurer ou protéger des applications, vous devez les ajouter à Intune. Les applications Office 365 pour appareils Windows 10 sont l’un des [types d’application](apps-add.md#app-types-in-microsoft-intune) disponibles. En sélectionnant ce type d’application dans Intune, vous pouvez affecter et installer des applications Office 365 sur des appareils Windows 10 que vous gérez. Vous pouvez également affecter et installer des applications pour le client de bureau Microsoft Project Online et Microsoft Visio Online - Plan 2 si vous disposez des licences appropriées. Les applications Office 365 disponibles sont affichées sous la forme d’une entrée unique dans la liste des applications dans la console Intune dans Azure.

> [!NOTE]
> Vous devez utiliser des licences Office 365 ProPlus pour activer les applications Office 365 ProPlus déployées par le biais Microsoft Intune. Office 365 Édition Business n’est pas pris en charge par Intune.

## <a name="before-you-start"></a>Avant de commencer

> [!IMPORTANT]
> S’il existe des applications Office .msi sur l’appareil de l’utilisateur final, utilisez la fonctionnalité **Supprimer MSI** pour les désinstaller en toute sécurité. Sinon, l’installation des applications Office 365 distribuées par Intune risque d’échouer.

- Les appareils sur lesquels vous déployez ces applications doivent exécuter Windows 10 Creators Update ou ultérieur.
- Intune prend uniquement en charge l’ajout d’applications Office provenant de la suite Office 365.
- Si des applications Office sont ouvertes au moment où Intune installe la suite d’applications, l’installation risque d’échouer et les utilisateurs risquent de perdre les données des fichiers non enregistrés.
- Cette méthode d’installation n’est pas prise en charge sur les appareils Windows Famille, Windows Collaboration, Windows Holographique ou Windows Holographic for Business.
- Intune ne prend pas en charge l’installation d’applications de bureau Office 365 à partir du Microsoft Store (appelées applications Office Centennial) sur un appareil sur lequel vous avez déjà déployé des applications Office 365 avec Intune. Si vous installez cette configuration, cela peut entraîner une perte ou une altération des données.
- Plusieurs affectations d’applications obligatoires ou disponibles ne s’additionnent pas. La dernière affectation d’applications remplace les affectations d’applications préexistantes installées. Par exemple, si le premier ensemble d’applications Office contient Word, mais que ce n’est pas le cas du dernier ensemble, Word est désinstallé. Cette condition ne s’applique pas aux applications Visio ou Project.
- Les déploiements multiples d’Office 365 ne sont pas actuellement pris en charge. Un seul déploiement est remis à l’appareil
- **Version d’Office** : choisissez si vous voulez affecter la version 32 bits ou 64 bits d’Office. Vous pouvez installer la version 32 bits sur des appareils 32 bits et 64 bits, mais vous ne pouvez installer la version 64 bits que sur des appareils 64 bits.
- **Supprimer MSI des appareils des utilisateurs finaux** : choisissez si vous voulez supprimer les applications .MSI Office préexistantes des appareils des utilisateurs finaux. L’installation échoue si des applications .MSI préexistantes sont présentes sur les appareils des utilisateurs finaux. Les applications à désinstaller ne sont pas limitées aux applications sélectionnées pour l’installation dans **Configurer la suite d’applications**, car cela supprime toutes les applications Office (MSI) de l’appareil des utilisateurs finaux. Pour plus d’informations, consultez [Supprimer les versions MSI existantes d’Office lors de la mise à niveau vers Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quand Intune réinstalle Office sur les machines de vos utilisateurs finaux, ceux-ci obtiennent automatiquement les mêmes modules linguistiques que ceux qu’ils avaient avec les installations .MSI Office précédentes.

## <a name="get-started"></a>Prise en main

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet de la charge de travail **Applications clientes**, sous **Gérer**, sélectionnez **Applications**.
5. Sélectionnez **Ajouter**.
6. Dans le volet **Ajouter des applications**, dans la liste **Type d’application**, sous **Suite Office 365**, sélectionnez **Windows 10**.

## <a name="select-settings-format"></a>Sélectionner le format des paramètres

Vous pouvez choisir une méthode pour configurer les paramètres d’application en sélectionnant un **Format des paramètres**. Les options de format des paramètres sont les suivantes :
- Concepteur de configuration
- Entrer des données XML

Quand vous choisissez **Concepteur de configuration**, le panneau **Ajouter une application** change pour vous proposer deux options de paramètres supplémentaires :
- Configurer la suite d’applications
- Paramètres de la suite d’applications

<img alt="Add Office 365 - Configuration designer" src="./media/apps-add-office365/apps-add-office365-02.png" width="700">

Quand vous choisissez **Entrer des données XML**, le panneau **Ajouter une application** affiche l’option **Entrer des données XML**. Sélectionnez-la pour afficher le panneau **Fichier de configuration**. 

![Ajouter le concepteur de configuration d’Office 365](./media/apps-add-office365/apps-add-office365-01.png)
    
Pour plus d’informations sur l’option **Entrer des données XML**, consultez [Entrer des données XML](apps-add-office365.md#enter-xml-format) ci-dessous.

## <a name="configure-app-suite-information"></a>Configurer les informations sur la suite d’applications

Dans cette étape, indiquez des informations sur la suite d’applications. Ces informations vous permettent d’identifier la suite d’applications dans Intune. Elles aident aussi les utilisateurs à trouver la suite d’applications dans le portail d’entreprise.

1. Dans le volet **Ajouter une application**, sélectionnez **Informations sur la suite d’applications**.
2. Dans le volet **Informations sur la suite d’applications**, procédez comme suit :
    - **Nom de la suite** : entrez le nom de la suite d’applications tel qu’il apparaît dans le portail d’entreprise. Vérifiez que chaque nom de suite que vous utilisez est unique. Si un même nom de suite d’applications est utilisé deux fois, une seule application est proposée aux utilisateurs du portail d’entreprise.
    - **Description de la suite** : Entrez une description pour la suite d’applications. Vous pouvez par exemple répertorier les applications que vous avez choisies d’inclure.
    - **Éditeur** : Microsoft apparaît comme éditeur.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Ce paramètre permet de faciliter la recherche de la suite d’applications pour les utilisateurs qui naviguent dans le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : Microsoft apparaît comme développeur.
    - **Propriétaire** : Microsoft apparaît comme propriétaire.
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Logo** : le logo Office 365 est affiché avec l’application quand les utilisateurs naviguent dans le portail d’entreprise.
3. Sélectionnez **OK**.

## <a name="configure-app-suite"></a>Configurer la suite d’applications

Si vous avez sélectionné l’option **Concepteur de configuration** dans la zone de liste déroulante **Format des paramètres**, vous verrez l’option **Configurer la suite d’applications** dans le panneau **Ajouter une application**. Sélectionnez les applications Office à affecter aux appareils.

1. Dans le volet **Ajouter une application**, sélectionnez **Configurer la suite d’applications**.
2. Dans le volet **Configurer la suite d’applications**, sélectionnez les applications Office standard à affecter aux appareils.  
    Vous pouvez également installer des applications pour Microsoft Project Online Desktop Client et Microsoft Visio Online - Plan 2, si vous disposez des licences appropriées.
3. Sélectionnez **OK**.

## <a name="configure-app-suite-settings"></a>Configurer les paramètres de la suite d’applications

Si vous avez sélectionné l’option **Concepteur de configuration** dans la zone de liste déroulante **Format des paramètres**, vous verrez l’option **Paramètres de la suite d’applications** dans le panneau **Ajouter une application**. Dans cette étape, configurez les options d’installation de la suite d’applications. Les paramètres s’appliquent à toutes les applications que vous avez ajoutées à la suite.

1. Dans le volet **Ajouter une application**, sélectionnez **Paramètres de la suite d’applications**.
2. Dans le volet **Paramètres de la suite d’applications**, procédez comme suit :
    - **Version d’Office** : choisissez si vous voulez affecter la version 32 bits ou 64 bits d’Office. Vous pouvez installer la version 32 bits sur des appareils 32 bits et 64 bits, mais vous ne pouvez installer la version 64 bits que sur des appareils 64 bits.
    - **Canal de mise à jour** : choisissez le mode de mise à jour d’Office sur les appareils. Pour plus d’informations sur les différents canaux de mise à jour, consultez [Vue d’ensemble des canaux de mise à jour pour Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus). Choisissez parmi :
        - **Tous les mois**
        - **Mensuel (ciblé)**
        - **Semestriel**
        - **Semestriel (ciblé)**

        Après avoir choisi un canal, vous pouvez aussi sélectionner **Spécifique** pour installer une version spécifique d’Office pour le canal sélectionné sur les appareils des utilisateurs finaux. Sélectionnez ensuite la **Version spécifique** d’Office à utiliser.
        
        Les versions disponibles changeront au fil du temps. Par conséquent, quand vous créez un déploiement, les versions disponibles peuvent être plus récentes et ne pas disposer de certaines versions antérieures. Les déploiements actuels continuent de déployer l’ancienne version, mais la liste des versions est en permanence actualisée par canal.
        
        Pour les appareils qui mettent à jour leur version épinglée (ou qui mettent à jour n’importe quelle autre propriété) et qui sont déployés comme étant disponibles, l’état de la création de rapports est « Installé » s’ils ont installé la version précédente jusqu’à ce que l’enregistrement de l’appareil se produise. Quand l’enregistrement de l’appareil se produit, l’état passe temporairement à « Inconnu », mais il n’est pas montré à l’utilisateur. Quand l’utilisateur lance l’installation pour la version plus récente disponible, l’utilisateur voit l’état passer à « Installé ».
        
        Pour plus d’informations, consultez [Présentation des canaux de mise à jour pour Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

    - **Supprimer MSI des appareils des utilisateurs finaux** : choisissez si vous voulez supprimer les applications .MSI Office préexistantes des appareils des utilisateurs finaux. L’installation échoue si des applications .MSI préexistantes sont présentes sur les appareils des utilisateurs finaux. Les applications à désinstaller ne sont pas limitées aux applications sélectionnées pour l’installation dans **Configurer la suite d’applications**, car cela supprime toutes les applications Office (MSI) de l’appareil des utilisateurs finaux. Pour plus d’informations, consultez [Supprimer les versions MSI existantes d’Office lors de la mise à niveau vers Office 365 ProPlus](https://docs.microsoft.com/deployoffice/upgrade-from-msi-version). Quand Intune réinstalle Office sur les machines de vos utilisateurs finaux, ceux-ci obtiennent automatiquement les mêmes modules linguistiques que ceux qu’ils avaient avec les installations .MSI Office précédentes. 
    - **Accepter automatiquement le contrat de licence utilisateur final (CLUF)** : sélectionnez cette option si vous n’obligez pas les utilisateurs finaux à accepter le contrat de licence. Intune accepte alors automatiquement le contrat.
    - **Utiliser l’activation d’ordinateurs partagés** : sélectionnez cette option quand plusieurs utilisateurs partagent un ordinateur. Pour plus d’informations, consultez [Vue d’ensemble de l’activation d’ordinateurs partagés pour Office 365](https://docs.microsoft.com/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus).
    - **Langues** : Office est automatiquement installé dans toute langue prise en charge installée avec Windows sur l’appareil de l’utilisateur final. Sélectionnez cette option pour installer des langues supplémentaires avec la suite d’applications. <p></p>
    Vous pouvez déployer des langues supplémentaires pour les applications Office 365 Pro Plus gérées par le biais d’Intune. La liste des langues disponibles inclut le **Type** du module linguistique (principal, partiel et de vérification). Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications clientes** > **Applications** > **Ajouter**. Dans la liste **Type d’application** du panneau **Ajouter une application**, sélectionnez **Windows 10** sous la **Suite Office 365**. Sélectionnez **Langues** dans le panneau **Paramètres de la suite d’applications**. Pour plus d’informations, consultez [Vue d’ensemble du déploiement de langues dans Office 365 ProPlus](https://docs.microsoft.com/deployoffice/overview-of-deploying-languages-in-office-365-proplus).

## <a name="select-scope-tags-optional"></a>Sélectionner les balises d’étendue (facultatif)
Vous pouvez utiliser des balises d’étendue pour déterminer qui peut afficher des informations sur l’application cliente dans Intune. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée](../fundamentals/scope-tags.md).

1. Sélectionnez **Étendue (balises)**  > **Ajouter**.
2. Utilisez la case **Sélectionner** pour rechercher les balises d’étendue.
3. Cochez la case en regard des balises d’étendue que vous souhaitez attribuer à cette application.
4. Choisissez **Sélectionner** > **OK**.

## <a name="enter-xml-format"></a>Entrer le format XML

Si vous avez sélectionné l’option **Entrer des données XML** dans la zone de liste déroulante **Format des paramètres**, vous verrez l’option **Entrer le format XML** dans le panneau **Ajouter une application**. Pour plus d’informations, consultez [Options de configuration pour l’outil Déploiement d’Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

## <a name="finish-up"></a>Terminer

Lorsque vous avez terminé, dans le volet **Ajouter une application**, sélectionnez **Ajouter**. L’application que vous avez créée s’affiche dans la liste des applications. L’étape suivante est d’assigner les applications aux groupes que vous choisissez. Pour plus d’informations, consultez [Affecter des applications à des groupes](~/apps/apps-deploy.md).

## <a name="deployment-details"></a>Détails du déploiement

Une fois que la stratégie de déploiement d’Intune est assignée aux ordinateurs cibles via le [fournisseur de services de configuration Office (CSP)](https://docs.microsoft.com/windows/client-management/mdm/office-csp), l’appareil final télécharge automatiquement le package d’installation à partir de l’emplacement *officecdn.microsoft.com*. Deux répertoires s’affichent dans le répertoire *Program Files* :

![Packages d’installation Office dans le répertoire Program Files](./media/apps-add-office365/office-folder.png)

Dans le répertoire *Microsoft Office*, un nouveau dossier est créé où sont stockés les fichiers d’installation :

![Nouveau dossier créé sous le répertoire Microsoft Office](./media/apps-add-office365/created-folder.png)

Dans le répertoire *Microsoft Office 15*, les fichiers du lanceur d’installation Office « Démarrer en un clic » sont stockés. L’installation démarre automatiquement si le type d’affectation est requis :

![Fichiers du lanceur d’installation « Démarrer en un clic »](./media/apps-add-office365/clicktorun-files.png)

L’installation s’effectue en mode silencieux si l’attribution de la suite O365 est configurée selon les besoins. Les fichiers d’installation téléchargés sont supprimés une fois que l’installation est terminée. Si l’attribution est configurée comme étant **disponible**, les applications Office s’affichent dans l’application Portail d’entreprise afin que les utilisateurs finaux puissent déclencher l’installation manuellement.

## <a name="troubleshooting"></a>Résolution des problèmes
Intune utilise l’[outil de déploiement d’Office](https://docs.microsoft.com/DeployOffice/overview-of-the-office-2016-deployment-tool) pour télécharger et déployer Office 365 ProPlus sur vos ordinateurs clients à l’aide de [Office 365 CDN](https://docs.microsoft.com/office365/enterprise/content-delivery-networks). Référencez les meilleures pratiques décrites dans [Gestion des points de terminaison Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints) pour vous assurer que votre configuration réseau permet aux clients d’accéder au CDN directement plutôt que d’acheminer le trafic par le biais de proxys centraux afin d’éviter la présentation de toute latence inutile.

Exécutez l’[Assistant Support et récupération de Microsoft pour Office 365](https://diagnostics.office.com) sur un appareil cible si vous rencontrez des problèmes d’installation ou d’exécution.

### <a name="additional-troubleshooting-details"></a>Détails des étapes de dépannage supplémentaires

Si vous ne parvenez pas à installer les applications O365 sur un appareil, vous devez déterminer si le problème est lié à Intune ou au système d’exploitation/à Office. Si vous pouvez voir les deux dossiers *Microsoft Office* et *Microsoft Office 15* dans le répertoire *Program Files* de l’appareil, vous pouvez confirmer qu’Intune a lancé le déploiement avec succès. Si les deux dossiers ne s’affichent pas sous *Program files*, vous devez confirmer les cas suivants :

- L’appareil est correctement inscrit à Microsoft Intune. 
- Une connexion réseau est active sur l’appareil. Si l’appareil est en mode avion, est désactivé ou se trouve dans un emplacement sans service, la stratégie ne s’applique pas tant que la connectivité réseau n’est pas établie.
- La configuration réseau requise pour Intune et Office 365 est satisfaite et les plages d’adresses IP associées sont accessibles. Consultez les articles suivants :

  - [Configuration requise pour le réseau Intune et bande passante](https://docs.microsoft.com/intune/network-bandwidth-use)
  - [URL et plages d’adresses IP Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

- La suite d’applications O365 a été attribuée aux groupes appropriés. 

En outre, surveillez la taille du répertoire *C:\Program Files\Microsoft Office\Updates\Download*. Le package d’installation téléchargé à partir du cloud Intune est stocké à cet emplacement. Si la taille n’augmente pas ou augmente très lentement, il est recommandé de vérifier la connectivité réseau et la bande passante.

Une fois que vous pouvez conclure qu’Intune et l’infrastructure réseau fonctionnent comme prévu, vous devez analyser plus en détail le problème du point de vue du système d’exploitation. Tenez compte des conditions suivantes :

- L’appareil cible doit s’exécuter sur Windows 10 Creators Update ou une version ultérieure.
- Aucune application Office existante n’est ouverte pendant que Intune déploie les applications.
- Les versions MSI existantes d’Office ont été correctement supprimées de l’appareil. Intune utilise le service Office « Démarrer en un clic » qui n’est pas compatible avec Office MSI. Ce comportement est abordé plus en détail dans ce document :<br>
  [L’installation d’Office à l’aide de Démarrer en un clic et de Windows Installer sur le même ordinateur n’est pas prise en charge](https://support.office.com/article/office-installed-with-click-to-run-and-windows-installer-on-same-computer-isn-t-supported-30775ef4-fa77-4f47-98fb-c5826a6926cd)
- L’utilisateur connecté doit avoir l’autorisation d’installer des applications sur l’appareil.
- Vérifiez qu’il n’existe aucun problème en vous basant sur le journal de l’Observateur d’événements Windows **Journaux Windows** -> **Applications**.
- Capturez les journaux détaillés de l’installation Office pendant l’installation. Pour ce faire, procédez comme suit :<br>
    1. Activez la journalisation documentée pour l’installation d’Office sur les ordinateurs cibles. Pour ce faire, exécutez la commande suivante pour modifier le Registre :<br>
        `reg add HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /t REG_DWORD /d 3`<br>
    2. Déployez de nouveau la suite Office 365 sur les appareils cibles.<br>
    3. Attendez environ 15 à 20 minutes et accédez au dossier **%temp%** et au dossier **%windir%\temp**, triez par **Date de modification**, puis sélectionnez les fichiers *{nom de l’ordinateur}-{TimeStamp}.log* modifiés en fonction de votre heure de reproduction.<br>
    4. Exécutez la commande suivante pour désactiver le journal détaillé :<br>
        `reg delete HKLM\SOFTWARE\Microsoft\ClickToRun\OverRide /v LogLevel /f`<br>
        Les journaux détaillés peuvent fournir des informations plus détaillées sur le processus d’installation.

## <a name="errors-during-installation-of-the-app-suite"></a>Erreurs durant l’installation de la suite d’applications

Consultez [Comment activer la journalisation d’Office 365 ProPlus ULS](https://blogs.technet.microsoft.com/odsupport/2018/06/18/how-to-enable-office-365-proplus-uls-logging) pour plus d’informations sur la façon d’afficher les journaux d’installation détaillée.

Les tableaux suivants répertorient les codes d’erreur fréquemment rencontrés et leur signification.

### <a name="status-for-office-csp"></a>État pour Office CSP

| État | Phase | Description |
|--------------------------------------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1460 (ERROR_TIMEOUT) | Télécharger | Échec du téléchargement de l’outil Déploiement d’Office |
| 13 (ERROR_INVALID_DATA) | - | Impossible de vérifier la signature de l’outil Déploiement d’Office téléchargé |
| Code d’erreur de CertVerifyCertificateChainPolicy | - | Échec de la vérification de certification pour l’outil Déploiement d’Office téléchargé |
| 997 | WIP | En cours d'installation |
| 0 | Après l’installation | Installation réussie |
| 1603 (ERROR_INSTALL_FAILURE) | - | Échec de la vérification des prérequis, par exemple : SxS (tentative d’installation alors que la version MSI 2016 est installée) La version ne correspond pas |
| 0x8000ffff (E_UNEXPECTED) | - | Tentative de désinstallation alors qu’aucune installation Office « Démarrer en un clic » n’est présente sur l’ordinateur |
| 17002 | - | Échec de l’exécution du scénario (installation). Raisons possibles : installation annulée par l’utilisation, installation annulée par une autre installation, espace disque insuffisant durant l’installation, ID de langue inconnu |
| 17004 | - | Références SKU inconnues |


### <a name="office-deployment-tool-error-codes"></a>Codes d’erreur de l’outil Déploiement d’Office

| Scénario | Code de retour | Interface utilisateur du service | Remarque |
|------------------------------------------------------------------------------------------------------------------|---------------------------------------|----------------------------------------------------|------------------------------------|
| Tentative de désinstallation en l’absence d’une installation Office « Démarrer en un clic » | -2147418113, 0x8000ffff ou 2147549183 | Code d’erreur : 30088-1008 Error Code : 30125-1011 (404) | Outil Déploiement d’Office |
| Installation alors qu’une version MSI est installée | 1603 | - | Outil Déploiement d’Office |
| Installation annulée par l’utilisateur ou par une autre installation | 17002 | - | Démarrer en un clic |
| Tentative de désinstallation d’une version 64 bits sur un appareil sur lequel la version 32 bits est installée. | 1603 | - | Code de retour de l’outil Déploiement d’Office |
| Tentative d’installation d’une référence SKU inconnue (il ne s’agit pas d’un cas d’usage légitime pour Office CSP puisque seules des références SKU valides doivent être passées) | 17004 | - | Démarrer en un clic |
| Espace insuffisant | 17002 | - | Démarrer en un clic |
| Échec du démarrage du client Office « Démarrer en un clic » (inattendu) | 17000 | - | Démarrer en un clic |
| Échec de la mise en file d’attente du scénario par le client Office « Démarrer en un clic » (inattendu) | 17001 | - | Démarrer en un clic |

## <a name="next-steps"></a>Étapes suivantes

- Pour assigner les applications aux groupes que vous choisissez, consultez [Assigner des applications à des groupes](/intune-azure/manage-apps/deploy-apps).
