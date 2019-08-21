---
title: Inscription pour les appareils joints à un domaine Azure AD Hybride - Windows Autopilot
titleSuffix: ''
description: Utilisez Windows Autopilot pour inscrire des appareils joints à un domaine Azure AD Hybride dans Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 399b0c6065c51343e4802d4e8aec29381c6dc468
ms.sourcegitcommit: 549352bdea93cc2809e3e0010bfcc10bd44dc728
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68861849"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-by-using-intune-and-windows-autopilot"></a>Déployer des appareils joints à un domaine Azure AD Hybride à l’aide d’Intune et de Windows Autopilot
Vous pouvez utiliser Intune et Windows Autopilot pour configurer des appareils joints à un domaine Azure Active Directory (Azure AD) hybride. Pour cela, effectuez les étapes de cet article.

## <a name="prerequisites"></a>Prérequis

Configurez correctement vos [appareils joints à Azure AD Hybride](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan). Veillez à [vérifier l’inscription de votre appareil](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration) avec l’applet de commande Get-MsolDevice.

Les appareils à inscrire doivent également :
- Être en cours d’exécution de Windows 10 v1809 ou version ultérieure.
- Accédez à internet [en suivant les exigences de réseau Windows Autopilot documentées](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements#networking-requirements).
- Accédez à un contrôleur de domaine Active Directory, pour qu’il puisse être connecté au réseau de l’organisation (où il peut résoudre les enregistrements DNS pour le domaine AD et le contrôleur de domaine AD et communiquer avec le contrôleur de domaine pour authentifier l’utilisateur. La connexion VPN n’étant pas prise en charge pour l’instant).
- Pouvoir effectuer un test ping sur le contrôleur de domaine du domaine que vous tentez de joindre.
- Si vous utilisez un Proxy, l’option des paramètres Proxy de WPAD doit être activée et configurée.
- Fournir l’expérience utilisateur OOBE (Out-of-Box Experience).

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurer l’inscription automatique Windows 10

1. Connectez-vous au [Portail Azure](https://portal.azure.com) puis, dans le volet gauche, sélectionnez **Azure Active Directory**.

   ![Le portail Azure](./media/auto-enroll-azure-main.png)

1. Sélectionnez **Mobilité (MDM et GAM)** .

   ![Le volet Azure Active Directory](./media/auto-enroll-mdm.png)

1. Sélectionnez **Microsoft Intune**.

   ![Le volet Mobilité (MDM et MAM)](./media/auto-enroll-intune.png)

1. Vérifiez que les utilisateurs qui déploient des appareils joints à Azure AD à l’aide d’Intune et de Windows sont membres d’un groupe inclus dans votre **étendue d’utilisateurs MDM**.

   ![Le volet Configurer la mobilité (MDM et MAM)](./media/auto-enroll-scope.png)

1. Utilisez les valeurs par défaut des zones **URL des conditions d’utilisation de GDR**, **URL de détection MDM** et **URL de conformité GDR**, puis sélectionnez **Enregistrer**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Augmenter la limite du nombre de comptes d’ordinateur dans l’unité d’organisation

Le connecteur Intune pour votre annuaire Active Directory crée des ordinateurs inscrits par Autopilot dans le domaine Active Directory local. L’ordinateur qui héberge le connecteur Intune doit avoir les droits nécessaires pour créer des objets ordinateur dans le domaine. 

Dans certains domaines, les ordinateurs n’ont pas les droits pour créer des ordinateurs. De plus, les domaines ont une limite intégrée (10 par défaut) qui s’applique à tous les utilisateurs et ordinateurs auxquels des droits pour créer des objets ordinateur n’ont pas été délégués. Par conséquent, les droits doivent être délégués aux ordinateurs hébergeant le connecteur Intune sur l’unité d’organisation où les appareils joints à un domaine Azure AD Hybride sont créés.

L’unité d’organisation qui a les droits de créer des ordinateurs doit correspondre :
- À l’unité d’organisation entrée dans le profil de jonction de domaine.
- Si aucun profil n’est sélectionné, au nom de domaine de l’ordinateur pour votre domaine.

1. Ouvrez **Utilisateurs et ordinateurs Active Directory (DSA.msc)** .

1. Cliquez avec le bouton droit sur l’unité d’organisation à utiliser pour créer des ordinateurs joints à un domaine Azure AD Hybride, puis sélectionnez **Déléguer le contrôle**.

    ![La commande Déléguer le contrôle](media/windows-autopilot-hybrid/delegate-control.png)

1. Dans l’Assistant **Délégation de contrôle**, sélectionnez **Suivant** > **Ajouter** > **Types d’objets**.

1. Dans le volet **Types d’objets**, cochez la case **Ordinateurs**, puis sélectionnez **OK**.

    ![Le volet Types d’objets](media/windows-autopilot-hybrid/object-types-computers.png)

1. Dans le volet **Sélectionner des utilisateurs, des ordinateurs ou des groupes**, dans la zone **Entrez les noms des objets à sélectionner**, entrez le nom de l’ordinateur où le connecteur est installé.

    ![Le volet Sélectionner des utilisateurs, des ordinateurs ou des groupes](media/windows-autopilot-hybrid/enter-object-names.png)

1. Sélectionnez **Vérifier les noms** pour valider votre entrée, sélectionnez **OK**, puis sélectionnez **Suivant**.

1. Sélectionnez **Créer une tâche personnalisée à déléguer** > **Suivant**.

1. Cochez la case **Seulement des objets suivants dans le dossier**, puis cochez les cases **Objets ordinateur**, **Créer les objets sélectionnés dans ce dossier** et **Supprimer les objets sélectionnés dans ce dossier**.

    ![Le volet Type d’objet Active Directory](media/windows-autopilot-hybrid/only-following-objects.png)
    
1. Sélectionnez **Suivant**.

1. Sous **Autorisations**, cochez la case **Contrôle total**.  
    Cette action sélectionne toutes les autres options.

    ![Le volet Autorisations](media/windows-autopilot-hybrid/full-control.png)

1. Sélectionnez **Suivant**, puis **Terminer**.

## <a name="install-the-intune-connector"></a>Installer le connecteur Intune

Le connecteur Intune pour Active Directory doit être installé sur un ordinateur qui exécute Windows Server 2016 ou ultérieur. L’ordinateur doit également avoir accès à Internet et à votre annuaire Active Directory. Pour augmenter la scalabilité et la disponibilité, ou pour permettre la prise en charge de plusieurs domaines Active Directory, vous pouvez installer plusieurs connecteurs dans votre environnement. Nous vous recommandons d’installer le connecteur sur un serveur qui n’exécute aucun autre connecteur Intune.

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription de l’appareil** > **Inscription Windows** > **Connecteur Intune pour Active Directory (préversion)**  > **Ajouter un connecteur**. 
2. Suivez les instructions pour télécharger le connecteur.
3. Ouvrez le fichier d’installation du connecteur téléchargé *ODJConnectorBootstrapper.exe* pour installer le connecteur.
4. À la fin de l’installation, sélectionnez **Configurer**.
5. Sélectionnez **Se connecter**.
6. Entrez les informations d’identification du rôle utilisateur Administrateur général ou Administrateur Intune.  
   Le compte d’utilisateur doit avoir une licence Intune.
7. Accédez à **Inscription de l’appareil** > **Inscription Windows** > **Connecteur Intune pour Active Directory (préversion)** , puis vérifiez que l’état de la connexion indique **Actif**.

> [!NOTE]
> Une fois que vous êtes connecté au connecteur, il peut être nécessaire d’attendre quelques minutes avant qu’il apparaisse dans [Intune](https://aka.ms/intuneportal). Il apparaît seulement s’il peut communiquer avec le service Intune.

### <a name="turn-off-ie-enhanced-security-configuration"></a>Désactivez la configuration de sécurité renforcée d’Internet Explorer
Par défaut, sous Windows Server la configuration de sécurité renforcée d’Internet Explorer est activée. Si vous ne parvenez pas à vous connecter au connecteur Intune pour Active Directory, désactivez la configuration de sécurité renforcée d’Internet Explorer pour l’administrateur. [Comment désactiver la configuration de sécurité renforcée d’Internet Explorer](https://blogs.technet.microsoft.com/chenley/2011/03/10/how-to-turn-off-internet-explorer-enhanced-security-configuration)

### <a name="configure-web-proxy-settings"></a>Configuration des paramètres de proxy web

Si vous avez un proxy web dans votre environnement réseau, vérifiez que le connecteur Intune pour Active Directory fonctionne correctement en vous référant à [Utiliser des serveurs proxy locaux existants](autopilot-hybrid-connector-proxy.md).


## <a name="create-a-device-group"></a>Créer un groupe d'appareils
1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Groupes** > **Nouveau groupe**.

1. Dans le volet **Groupe**, effectuez ceci :

    a. Pour **Type de groupe**, sélectionnez **Sécurité**.

    b. Renseignez les champs **Nom du groupe** et **Description du groupe**.

    c. Sélectionnez un **Type d’adhésion**.

1. Si vous avez sélectionné **Appareils dynamiques** pour le type d’adhésion, dans le volet **Groupe**, sélectionnez **Membres de dispositif dynamique** puis, dans la zone **Règle avancée**, effectuez une des actions suivantes :
    - Pour créer un groupe qui inclut tous vos appareils Autopilot, entrez `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - Le champ Balise de groupe d’Intune est mappé à l’attribut OrderID sur les appareils Azure AD. Si vous voulez créer un groupe incluant tous vos appareils Autopilot ayant une étiquette de groupe spécifique (OrderID), vous devez saisir ceci : `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Pour créer un groupe qui inclut tous vos appareils Autopilot avec un ID de bon de commande spécifique, entrez `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`.
    
1. Sélectionnez **Enregistrer**.

1. Sélectionnez **Créer**.  

## <a name="register-your-autopilot-devices"></a>Inscrire vos appareils Autopilot

Sélectionnez une des méthodes suivantes pour inscrire vos appareils Autopilot.

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Inscrire les appareils Autopilot déjà inscrits

1. Créez un profil de déploiement Autopilot en affectant à **Convertir tous les appareils ciblés en Autopilot** la valeur **Oui**. 
2. Affectez le profil à un groupe contenant les membres que vous voulez inscrire automatiquement avec Autopilot.

Pour plus d’informations, consultez [Créer un profil de déploiement Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Inscrire les appareils Autopilot qui ne sont pas inscrits

Si vos appareils ne sont pas encore inscrits, vous pouvez les inscrire vous-même. Pour plus d’informations, consultez [Ajouter des appareils](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Inscrire les appareils d’un OEM

Si vous achetez de nouveaux appareils, certains OEM peuvent les inscrire à votre place. Pour plus d’informations, consultez la [page Windows Autopilot](https://aka.ms/WindowsAutopilot).

Quand vos appareils Autopilot sont *inscrits*, avant qu’ils ne le soient dans Intune, vous les voyez à trois endroits (avec des noms définis sur leur numéro de série) :
- Le volet **Appareils Autopilot** dans Intune, dans le portail Azure. Sélectionnez **Inscription d’appareils** > **Inscription Windows** > **Appareils**.
- Le volet **Appareils Azure AD** dans Intune, dans le portail Azure. Sélectionnez **Appareils** > **Appareils Azure AD**.
- Le volet **Tous les appareils Azure AD** dans Azure Active Directory, dans le portail Azure en sélectionnant **Appareils** > **Tous les appareils**.

Une fois vos appareils Autopilot *inscrits*, ceux-ci apparaissent à quatre endroits :
- Le volet **Appareils Autopilot** dans Intune, dans le portail Azure. Sélectionnez **Inscription d’appareils** > **Inscription Windows** > **Appareils**.
- Le volet **Appareils Azure AD** dans Intune, dans le portail Azure. Sélectionnez **Appareils** > **Appareils Azure AD**.
- Le volet **Tous les appareils Azure AD** dans Azure Active Directory, dans le portail Azure. Sélectionnez **Appareils** > **Tous les appareils**.
- Le volet **Tous les appareils** dans Intune, dans le portail Azure. Sélectionnez **Appareils** > **Tous les appareils**.

Une fois vos appareils Autopilot inscrits, leur nom devient le nom d’hôte de l’appareil. Par défaut, le nom d’hôte commence par *DESKTOP-* .


## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Créer et affecter un profil de déploiement Autopilot
Les profils de déploiement Autopilot sont utilisés pour configurer les appareils Autopilot.

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil**.
1. Tapez un **Nom** et (éventuellement) une **Description**.
1. Pour **Mode de déploiement**, sélectionnez **Piloté par l’utilisateur**.
1. Dans la zone **Joindre à Azure AD comme**, sélectionnez **Joint à Azure AD Hybride (préversion)** .
1. Sélectionnez **OOBE (Out-Of-Box Experience)** , configurez les options selon les besoins, puis sélectionnez **Enregistrer**.
1. Sélectionnez **Créer** pour créer le profil. 
1. Dans le volet du profil, sélectionnez **Affectations**.
1. Sélectionnez **Sélectionner des groupes**.
1. Dans le volet **Sélectionner des groupes**, sélectionnez le groupe d’appareils, puis cliquez sur **Sélectionner**.

Environ 15 minutes sont nécessaires pour que l’état du profil de l’appareil passe de *Non affecté* à *Affectation*, puis à *Affecté*.

## <a name="optional-turn-on-the-enrollment-status-page"></a>(Facultatif) Activer la page d’état d’inscription

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Windows** > **Page d’état d’inscription**.
1. Dans le volet **Page d’état d’inscription**, sélectionnez **Par défaut** > **Paramètres**.
1. Pour **Afficher la progression de l’installation des applications et des profils**, sélectionnez **Oui**.
1. Configurez les autres options selon les besoins.
1. Sélectionnez **Enregistrer**.

## <a name="create-and-assign-a-domain-join-profile"></a>Créer et affecter un profil de jonction de domaine

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
1. Entrez les propriétés suivantes :
   - **Nom** : Entrez un nom descriptif pour le nouveau profil.
   - **Description** : Entrez la description du profil.
   - **Plateforme** : Sélectionnez **Windows 10 et ultérieur**.
   - **Type de profil** : Sélectionnez **Jonction de domaine (préversion)** .
1. Sélectionnez **Paramètres**, puis indiquez un **Préfixe du nom d’ordinateur**, un **Nom de domaine** et (facultatif) une **Unité d’organisation** au [Format DN](https://docs.microsoft.com/windows/desktop/ad/object-names-and-identities#distinguished-name). 
1. Sélectionnez **OK** > **Créer**.  
    Le profil est créé et apparaît dans la liste.
1. Pour attribuer le profil, suivez les étapes fournies dans [Attribuer un profil d’appareil](device-profile-assign.md#assign-a-device-profile), et affectez le profil au même groupe que celui utilisé à l’étape [Créer un groupe d’appareils](windows-autopilot-hybrid.md#create-a-device-group).
   - Déploiement de plusieurs profils joints à un domaine
   
     a. Créez un groupe dynamique incluant tous vos appareils Autopilot avec un profil de déploiement Autopilot spécifique, et entrez (device.enrollmentProfileName -eq "nom_profil_Autopilot"). 
     
     b. Remplacez « nom_profil_Autopilot » par le nom complet du profil créé sous [Créer et attribuer un profil de déploiement Autopilot](windows-autopilot-hybrid.md#create-and-assign-an-autopilot-deployment-profile). 
     
     c. Créez plusieurs profils de déploiement Autopilot et affectez cet appareil au profil spécifié dans ce groupe dynamique.

> [!NOTE]
> Les capacités de nommage pour Windows Autopilot pour la jonction Azure AD Hybride ne prennent pas en charge les variables telles que %SERIAL% et prennent uniquement en charge les préfixes pour le nom d’ordinateur.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez configuré Windows Autopilot, découvrez comment gérer les appareils. Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](device-management.md).
