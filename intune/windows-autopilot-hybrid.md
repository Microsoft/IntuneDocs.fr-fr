---
title: Inscription pour les appareils joints à un domaine Active Directory hybride - Windows Autopilot
titleSuffix: ''
description: Utilisez Windows Autopilot pour inscrire des appareils joints à un domaine Active Directory hybride dans Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ced67b2dcdd5720a9708868808ec885938b8ddcd
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112440"
---
# <a name="deploy-hybrid-azure-ad-joined-devices-using-intune-and-windows-autopilot-preview"></a>Déployer des appareils joints à un domaine Azure AD hybride à l’aide d’Intune et de Windows Autopilot (préversion)
Vous pouvez utiliser Intune et Windows Autopilot pour configurer des appareils joints à un domaine Azure Active Directory hybride. Pour ce faire, suivez les étapes ci-dessous.

> [!NOTE]
> Cette fonctionnalité va être lancée parmi la base d’utilisateurs au cours des prochains jours. Vous ne pourrez donc peut-être pas suivre ces étapes tant que la fonctionnalité n’aura pas été lancée pour votre compte.

## <a name="prerequisites"></a>Conditions préalables

- Configurez correctement les [appareils joints à un domaine Azure Active Directory hybride](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan).
    - Veillez à [vérifier l’inscription à l’aide de l’applet de commande Get-MsolDevice]( https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains#verify-the-registration).

Les appareils à inscrire doivent également :
- Exécuter Windows 10 avec la [mise à jour d’octobre 2018](https://blogs.windows.com/windowsexperience/2018/10/02/how-to-get-the-windows-10-october-2018-update/)
- Avoir accès à Internet
- Avoir accès à votre domaine Active Directory (connexion VPN non prise en charge)
- Fournir l’expérience utilisateur OOBE (Out-of-Box Experience)

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurer l’inscription automatique Windows 10

1. Connectez-vous au [Portail Azure](https://portal.azure.com), puis sélectionnez **Azure Active Directory**.

   ![Capture d’écran montrant le portail Azure](./media/auto-enroll-azure-main.png)

2. Sélectionnez **Mobilité (gestion des données de référence et gestion des applications mobiles)**.

   ![Capture d’écran montrant le portail Azure](./media/auto-enroll-mdm.png)

3. Sélectionnez **Microsoft Intune**.

   ![Capture d’écran montrant le portail Azure](./media/auto-enroll-intune.png)

4. Vérifiez que les utilisateurs qui déploient des appareils joints à Azure Active Directory à l’aide d’Intune et de Windows sont membres d’un groupe inclus dans votre **étendue d’utilisateurs MDM**.

   ![Capture d’écran montrant le portail Azure](./media/auto-enroll-scope.png)

5. Utilisez les valeurs par défaut pour les URL suivantes :
    - **URL des conditions d’utilisation de la gestion des données de référence**
    - **URL de détection MDM**
    - **URL de conformité GAM**
6. Choisissez **Enregistrer**.

## <a name="increase-the-computer-account-limit-in-the-organizational-unit"></a>Augmenter la limite du nombre de comptes d’ordinateur dans l’unité d’organisation

Le connecteur Intune pour Active Directory crée des ordinateurs Autopilot inscrits dans le domaine Active Directory local. L’ordinateur qui héberge le connecteur Intune doit avoir les droits nécessaires pour créer des objets ordinateur dans le domaine. 

Sur certains domaines, les ordinateurs ne sont pas autorisés à créer des ordinateurs. De plus, les domaines ont une limite intégrée (10 par défaut) qui s’applique à tous les utilisateurs et ordinateurs auxquels des droits pour créer des objets ordinateur n’ont pas été délégués. Par conséquent, les droits doivent être délégués aux ordinateurs hébergeant le connecteur Intune sur l’unité d’organisation où les appareils joints à un domaine Azure AD hybride sont créés.

L’unité d’organisation autorisée à créer des ordinateurs doit correspondre :
- À l’unité d’organisation entrée dans le profil de jonction de domaine
- Ou, si aucun profil n’est sélectionné, au nom de domaine de l’ordinateur pour votre domaine

1. Ouvrez **Utilisateurs et ordinateurs Active Directory** (DSA.msc).

2. Cliquez avec le bouton droit sur l’unité d’organisation à utiliser pour créer des ordinateurs joints à un domaine Azure AD hybride > **Déléguer le contrôle**.

    ![Capture d’écran de la délégation de contrôle](media/windows-autopilot-hybrid/delegate-control.png)

3. Dans l’Assistant **Délégation de contrôle**, choisissez **Suivant** > **Ajouter** > **Types d’objet**.

4. Dans la boîte de dialogue **Types d’objet**, cochez **Ordinateurs**, puis choisissez **OK**.

    ![Capture d’écran de la délégation de contrôle](media/windows-autopilot-hybrid/object-types-computers.png)

5. Dans la boîte de dialogue **Sélectionnez les utilisateurs, les ordinateurs ou les groupes**, dans la zone **Entrez les noms des objets à sélectionner**, entrez le nom de l’ordinateur où le connecteur est installé.

    ![Capture d’écran de la délégation de contrôle](media/windows-autopilot-hybrid/enter-object-names.png)

6. Choisissez **Vérifier les noms** pour valider votre entrée, puis choisissez **OK** > **Suivant**.

7. Choisissez **Créer une tâche personnalisée à déléguer** > **Suivant**.

8. Choisissez **Seulement des objets suivants dans le dossier**, puis cochez les options suivantes :
    - **Objets ordinateur**
    - **Créer les objets sélectionnés dans ce dossier**
    - **Supprimer les objets sélectionnés dans ce dossier**

    ![Capture d’écran de la délégation de contrôle](media/windows-autopilot-hybrid/only-following-objects.png)
    
9. Choisissez **Suivant**.

10. Sous **Autorisations**, cochez **Contrôle total** (toutes les autres options sont alors cochées automatiquement) > **Suivant** > **Terminer**.

    ![Capture d’écran de la délégation de contrôle](media/windows-autopilot-hybrid/full-control.png)

## <a name="install-the-intune-connector"></a>Installer le connecteur Intune

Le connecteur Intune pour Active Directory doit être installé sur un ordinateur Windows Server 2016 ayant accès à Internet et à votre domaine Active Directory. Pour augmenter la scalabilité et la disponibilité, ou pour permettre la prise en charge de plusieurs domaines Active Directory, vous pouvez installer plusieurs connecteurs dans votre environnement. Nous vous recommandons d’installer le connecteur sur un serveur qui n’exécute aucun autre connecteur Intune.

1. Assurez-vous que vous disposez d’un module linguistique installé et configuré comme décrit dans [Spécifications de langue pour Intune Connector (préversion)](https://docs.microsoft.com/windows/deployment/windows-autopilot/intune-connector).
2. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription de l’appareil** > **Inscription Windows** > **Connecteur Intune pour Active Directory (préversion)** > **Ajouter un connecteur**. 
3. Suivez les instructions pour télécharger le connecteur.
4. Ouvrez le fichier d’installation du connecteur téléchargé pour installer le connecteur (ODJConnectorBootstrapper.exe).
5. À la fin de l’installation, choisissez **Configurer**.
6. Choisissez **Connexion**.
7. Entrez les informations d’identification du rôle utilisateur Administrateur général ou Administrateur Intune.
8. Accédez à **Inscription de l’appareil** > **Inscription Windows** > **Connecteur Intune pour Active Directory (préversion)**, puis vérifiez que l’état de la connexion indique **Actif**.

### <a name="configure-web-proxy-settings"></a>Configuration des paramètres de proxy web

Si vous avez un proxy web dans votre environnement réseau, suivez les instructions indiquées ici pour que le connecteur Intune pour Active Directory fonctionne correctement : [Utiliser des serveurs proxy locaux existants](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers).


## <a name="create-a-device-group"></a>Créer un groupe d'appareils
1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Groupes** > **Nouveau groupe**.
2. Dans le panneau **Groupe** :
    1. Pour **Type de groupe**, choisissez **Sécurité**.
    2. Renseignez les champs **Nom du groupe** et **Description du groupe**.
    3. Choisissez un **Type d’adhésion**.
3. Si vous avez choisi **Appareils dynamiques** pour **Type d’appartenance** ci-dessus, dans le panneau **Groupe**, choisissez **Membres de dispositif dynamique**, puis tapez le code suivant dans la zone **Règle avancée**.
    - Si vous souhaitez créer un groupe qui inclut tous vos appareils Autopilot, tapez `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Si vous souhaitez créer un groupe qui inclut tous vos appareils Autopilot associés à un ID de commande spécifique, tapez `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Si vous souhaitez créer un groupe qui inclut tous vos appareils Autopilot associés à un ID de bon de commande spécifique, tapez `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Après avoir ajouté le code dans la zone **Règle avancée**, choisissez **Enregistrer**.
5. Choisissez **Créer**.  

## <a name="register-your-autopilot-devices"></a>Inscrire vos appareils Autopilot

Choisissez l’une des méthodes suivantes pour inscrire vos appareils Autopilot :

### <a name="register-autopilot-devices-that-are-already-enrolled"></a>Inscrire les appareils Autopilot déjà inscrits

1. Créez un profil de déploiement Autopilot en affectant à **Convertir tous les appareils ciblés en Autopilot** la valeur **Oui**. 
2. Affectez le profil à un groupe contenant les membres que vous souhaitez inscrire automatiquement auprès d’Autopilot.

Pour plus d’informations, consultez [Créer un profil de déploiement Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile).

### <a name="register-autopilot-devices-that-arent-enrolled"></a>Inscrire les appareils Autopilot qui ne sont pas inscrits

Si vos appareils ne sont pas encore inscrits, vous pouvez les inscrire vous-même. Pour plus d’informations, consultez [Ajouter des appareils](enrollment-autopilot.md#add-devices).

### <a name="register-devices-from-an-oem"></a>Inscrire les appareils d’un OEM

Si vous achetez de nouveaux appareils, certains OEM peuvent les inscrire à votre place. Pour plus d’informations, consultez la [page Windows Autopilot](http://aka.ms/WindowsAutopilot).

Quand les appareils Autopilot sont inscrits (et avant qu’ils ne le soient dans Intune), vous les voyez à trois endroits (avec leurs noms définis en fonction de leur numéros de série) :
- Panneau des appareils Autopilot dans Intune, au sein du Portail Azure (**Inscription de l’appareil** > **Inscription Windows** > **Appareils**).
- Panneau des appareils Azure AD dans Intune, au sein du Portail Azure (**Appareils** > **Appareils Azure AD**).
- Panneau de tous les appareils AAD dans Azure Active Directory, au sein du Portail Azure (**Appareils** > **Tous les appareils**).

Une fois les appareils Autopilot inscrits, vous les voyez à quatre endroits :
- Panneau des appareils Autopilot dans Intune, au sein du Portail Azure (**Inscription de l’appareil** > **Inscription Windows** > **Appareils**).
- Panneau des appareils Azure AD dans Intune, au sein du Portail Azure (**Appareils** > **Appareils Azure AD**).
- Panneau de tous les appareils AAD dans Azure Active Directory, au sein du Portail Azure (**Appareils** > **Tous les appareils**).
- Panneau de tous les appareils dans Intune, au sein du Portail Azure (**Appareils** > **Tous les appareils**).

Une fois les appareils Autopilot inscrits, le nom d’appareil devient le nom d’hôte de l’appareil. Par défaut, il commence par « DESKTOP- ».




## <a name="create-and-assign-an-autopilot-deployment-profile"></a>Créer et affecter un profil de déploiement Autopilot
Les profils de déploiement Autopilot sont utilisés pour configurer les appareils Autopilot.

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil**.
2. Tapez un **Nom** et une **Description** facultative.
3. Pour **Mode de déploiement**, choisissez **Piloté par l’utilisateur**.
4. Dans la zone **Joindre à Azure AD comme**, choisissez **Avec jonction hybride à Azure AD (préversion)**.
5. Choisissez **OOBE (Out-Of-Box Experience)**, configurez les options selon les besoins, puis choisissez **Enregistrer**.
6. Choisissez **Créer** pour créer le profil. 
7. Dans le panneau du profil, choisissez **Affectations**.
8. Choisissez **Sélectionner des groupes** > dans le panneau **Sélectionner des groupes**, choisissez le groupe d’appareils > **Sélectionner**.

Environ 15 minutes sont nécessaires pour que l’état du profil de l’appareil passe de **Non affecté** à **Affectation**, puis à **Affecté**.

## <a name="turn-on-the-enrollment-status-page-optional"></a>Activer la page d’état d’inscription (facultatif)

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription de l’appareil** > **Inscription Windows** > **Page d’état d’inscription (préversion)**.
2. Dans le panneau **Page d’état d’inscription**, choisissez **Par défaut** > **Paramètres**.
3. Pour **Afficher la progression de l’installation des profils et des applications**, choisissez **Oui**.
4. Configurez les autres options selon les besoins.
5. Choisissez **Enregistrer**.

## <a name="create-and-assign-a-domain-join-profile"></a>Créer et affecter un profil de jonction de domaine

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
2. Entrez les propriétés suivantes :
   - **Nom** : Entrez un nom descriptif pour le nouveau profil.
   - **Description** : Entrez la description du profil.
   - **Plateforme** : Choisissez **Windows 10 et ultérieur**.
   - **Type de profil** : Choisissez **Jonction de domaine (préversion)**.
3. Choisissez **Paramètres**, puis indiquez un **Préfixe du nom d’ordinateur**, un **Nom de domaine** et une **Unité d’organisation** (facultatif). 
4. Choisissez **OK** > **Créer**. Le profil est créé et apparaît dans la liste.
5. Pour affecter le profil, suivez les étapes décrites dans [Attribuer un profil d’appareil](device-profile-assign.md#assign-a-device-profile). 

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez configuré Windows Autopilot, découvrez comment gérer les appareils. Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](device-management.md)
