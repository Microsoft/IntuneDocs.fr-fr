---
title: Inscrire les appareils macOS – Programme d’inscription des appareils ou Apple School Manager
titleSuffix: ''
description: Découvrez comment inscrire des appareils macOS d’entreprise à l’aide du Programme d’inscription des appareils.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ab95d04403166781594f88ec98db11b281494b2a
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839904"
---
# <a name="automatically-enroll-macos-devices-with-the-device-enrollment-program-or-apple-school-manager"></a>Inscrire automatiquement les appareils macOS avec le Programme d’inscription des appareils ou Apple School Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez configurer l’inscription Intune des appareils macOS achetés dans le cadre du [Programme d’inscription des appareils (DEP)](https://deploy.apple.com) d’Apple ou d’[Apple School Manager](https://school.apple.com/). Vous pouvez utiliser ces deux types d’inscriptions pour un grand nombre d’appareils sans jamais avoir à les manipuler. Vous pouvez expédier les appareils macOS directement aux utilisateurs. Quand l’utilisateur active l’appareil, l’Assistant Configuration s’exécute avec les paramètres préconfigurés et l’appareil s’inscrit à la gestion Intune.

Pour configurer l’inscription, on utilise à la fois le portail Intune et le portail DEP Apple. Des profils d’inscription contenant les paramètres appliqués aux appareils lors de l’inscription sont créés.

Ni l’inscription DEP ni Apple School Manager ne fonctionnent avec le [gestionnaire d’inscription des appareils](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Prérequis
- Appareils achetés dans le cadre [d’Apple School Manager](https://school.apple.com/) ou du [Programme d’inscription des appareils d’Apple](http://deploy.apple.com)
- Liste de numéros de série ou numéro de bon de commande. 
- [Autorité MDM](mdm-authority-set.md)
- [Certificat Push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obtenir un jeton DEP Apple

Pour pouvoir inscrire des appareils macOS à l’aide du programme DEP ou d’Apple School Manager, vous devez obtenir un fichier de jeton (.p7m) DEP auprès d’Apple. Ce jeton permet à Intune de synchroniser les informations sur les appareils appartenant à l’entreprise. Il permet également à Intune de charger des profils d’inscription sur Apple et d’attribuer des appareils à ces profils.

Le portail Apple permet de créer un jeton et d’affecter des appareils à Intune à des fins de gestion.

> [!NOTE]
> Si vous supprimez le jeton du portail classique Intune avant de migrer vers Azure, Intune risque de restaurer le jeton Apple supprimé. Vous pouvez supprimer à nouveau le jeton sur le Portail Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Étape 1. Téléchargez le certificat de clé publique Intune nécessaire à la création du jeton.

1. Dans [Intune sur le portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > **Ajouter**.

    ![Récupérez un jeton du programme d’inscription.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Autorisez Microsoft à envoyer des informations d’utilisateur et d’appareil à Apple en sélectionnant **J’accepte**.

   ![Capture d’écran du volet Jeton de programme d’inscription dans l’espace de travail Certificats Apple pour télécharger une clé publique.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Choisissez **Télécharger votre clé publique** pour télécharger et enregistrer le fichier de clé de chiffrement (.pem) en local. Le fichier .pem est utilisé pour demander un certificat de relation d’approbation auprès du portail Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Étape 2. Utilisez votre clé pour télécharger un jeton auprès d’Apple.

1. Choisissez **Créer un jeton pour le Programme d’inscription des appareils d’Apple** ou **Créer un jeton avec Apple School Manager** pour ouvrir le portail Apple correspondant, et connectez-vous avec votre ID Apple d’entreprise. Vous pouvez utiliser cet ID Apple pour renouveler votre jeton.
2.  Côté programme DEP, choisissez **Bien démarrer** pour **Programme d’inscription des appareils** > **Gérer les serveurs** > **Ajouter un serveur de gestion des appareils mobiles (MDM)** sur le portail Apple.
3.  Pour Apple School Manager, choisissez **Serveurs de gestion des appareils mobiles (MDM)** > **Ajouter un serveur de gestion des appareils mobiles (MDM)** sur le portail Apple.
4. Entrez le **Nom du serveur MDM**, puis choisissez **Suivant**. Le nom du serveur vous permet d’identifier le serveur de gestion des appareils mobiles (MDM) uniquement. Il ne s’agit pas du nom ou de l’URL du serveur Microsoft Intune.

5. La boîte de dialogue **Ajouter &lt;nom_serveur&gt;** s’ouvre avec le message **Charger votre clé publique**. Choisissez **Choisir un fichier** pour charger le fichier .pem, puis choisissez **Suivant**.

6. Accédez à **Programme de déploiement** &gt; **Programme d’inscription d’appareils** &gt; **Gérer les appareils**.
7. Sous **Choisir les appareils par**, spécifiez comment les appareils sont identifiés :
    - **Numéro de série**
    - **Numéro de commande**
    - **Télécharger un fichier CSV**

   ![Capture d’écran montrant le choix des appareils par numéro de série, la définition de Attribuer au serveur comme paramètre Choisir l’action, et la sélection du nom du serveur.](./media/enrollment-program-token-specify-serial.png)

8. Pour **Choisir une action**, choisissez **Affecter au serveur**, le &lt;nom_serveur&gt; spécifié pour Microsoft Intune, puis **OK**. Le portail Apple affecte les appareils spécifiés au serveur Intune pour la gestion, puis affiche **Affectation terminée**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Étape 3. Enregistrer l’ID Apple utilisé pour créer le jeton

Dans le portail Azure d’Intune, fournissez l’ID Apple pour référence ultérieure.

![Capture d’écran : spécification de l’ID Apple utilisé pour créer le jeton du programme d’inscription et accès à ce jeton.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Étape 4. Chargez votre jeton.
Dans la zone **Jeton Apple**, accédez au fichier du certificat (.pem), choisissez **Ouvrir**, puis **Créer**. Avec le certificat Push, Intune peut inscrire et gérer des appareils macOS en envoyant la stratégie aux appareils inscrits. Intune se synchronise automatiquement avec Apple pour afficher votre compte de programme d’inscription.

## <a name="create-an-apple-enrollment-profile"></a>Créer un profil d’inscription Apple

Maintenant que vous avez installé votre jeton, vous pouvez créer un profil d’inscription pour les appareils. Un profil d'inscription d'appareil définit les paramètres appliqués à un groupe d'appareils lors de l’inscription.

1. Dans Intune, sur le Portail Azure, choisissez **Inscription des appareil** > **Inscription Apple** > **Jetons du programme d’inscription**.
2. Sélectionnez un jeton et choisissez **Profils**, puis **Créer un profil**.

    ![Capture d’écran de création d’un profil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Dans **Créer un profil**, entrez le **Nom** et la **Description** du profil qui serviront à des fins d’administration. Les utilisateurs ne voient pas ces détails. Vous pouvez utiliser ce champ **Nom** pour créer un groupe dynamique dans Azure Active Directory. Utilisez le nom du profil pour définir le paramètre enrollmentProfileName et attribuer des appareils avec ce profil d’inscription. En savoir plus sur les [groupes dynamiques Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nom et description du profil.](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. Pour **Plateforme**, choisissez **macOS**.

5. Pour **Affinité utilisateur**, indiquez si les appareils possédant ce profil doivent être inscrits avec ou sans utilisateur attribué.
    - **Inscrire avec affinité utilisateur** : choisissez cette option pour les appareils qui appartiennent à des utilisateurs et qui veulent utiliser l’application Portail d’entreprise pour des services comme l’installation d’applications. Si vous utilisez ADFS, l’affinité utilisateur nécessite un [point de terminaison WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [En savoir plus](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint). Les appareils DEP macOS avec l’affinité utilisateur ne prennent pas en charge l’authentification multifacteur.

    - **Inscrire sans affinité utilisateur** : choisissez cette option pour les appareils non affiliés à un seul utilisateur, qui effectuent des tâches sans accéder aux données de l’utilisateur local. Les applications telles que l’application Portail d’entreprise ne fonctionnent pas.

6. Choisissez **Paramètres de gestion des appareils** et indiquez si vous souhaitez que l’inscription soit verrouillée pour les appareils possédant ce profil. **L’inscription verrouillée** désactive les paramètres macOS qui permettent de supprimer le profil de gestion du menu **Préférences système** ou via le **Terminal**. Une fois l’appareil inscrit, vous ne pouvez plus modifier ce paramètre sans réinitialiser l’appareil.

    ![Capture d’écran Paramètres de gestion des appareils.](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. Choisissez **OK**.

8. Choisissez **Paramètres de l’Assistant Configuration** pour configurer les paramètres de profil suivants :  ![Personnalisation de l’Assistant Configuration.](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)

    | Paramètres du service | Description |
    |---|---|
    | <strong>Nom du service</strong> | S’affiche quand l’utilisateur appuie sur <strong>À propos de la configuration</strong> pendant l’activation. |
    | <strong>Numéro de téléphone du service</strong> | S’affiche quand l’utilisateur clique sur le bouton <strong>Besoin d’aide</strong> pendant l’activation. |

  Vous pouvez choisir d’afficher ou de masquer différents écrans de l’Assistant Configuration sur l’appareil quand l’utilisateur le configure.
  - Si vous choisissez **Masquer**, l’écran ne s’affiche pas pendant la configuration. Après avoir configuré l’appareil, l’utilisateur peut toujours accéder au menu **Paramètres** pour configurer la fonctionnalité.
  - Si vous choisissez **Afficher**, l’écran s’affiche pendant la configuration. L’utilisateur peut parfois ignorer l’écran et n’entreprendre aucune action. Mais il pourra ensuite accéder au menu **Paramètres** de l’appareil pour configurer la fonctionnalité. 


    | Paramètres de l’écran de l’Assistant Configuration | Si vous choisissez **Afficher**, pendant la configuration, l’appareil... |
    |------------------------------------------|------------------------------------------|
    | <strong>Code secret</strong> | Invite l’utilisateur à entrer un code secret. Exige toujours un code secret, sauf si l’appareil doit être sécurisé ou si son accès doit être contrôlé d’une autre façon (c’est-à-dire, en mode plein écran qui limite l’appareil à une seule application). |
    | <strong>Services d’emplacement</strong> | Invite l’utilisateur à entrer son emplacement. |
    | <strong>Restauration</strong> | Affiche l’écran **Applications et données**. Cet écran donne à l’utilisateur la possibilité de restaurer ou de transférer des données à partir de la sauvegarde iCloud pendant la configuration de l’appareil. |
    | <strong>ID Apple et iCloud</strong> | Donne à l’utilisateur la possibilité de se connecter avec son **Identifiant Apple** et d’utiliser **iCloud**.                         |
    | <strong>Conditions générales</strong> | Oblige l’utilisateur à accepter les conditions générales d’Apple. |
    | <strong>Touch ID</strong> | Donne à l’utilisateur la possibilité de configurer l’identification par empreinte digitale sur l’appareil. |
    | <strong>Apple Pay</strong> | Donne à l’utilisateur la possibilité de configurer Apple Pay sur l’appareil. |
    | <strong>Zoom</strong> | Donne à l’utilisateur la possibilité d’effectuer un zoom sur l’affichage pendant la configuration de l’appareil. |
    | <strong>Siri</strong> | Donne à l’utilisateur la possibilité de configurer Siri. |
    | <strong>Données de diagnostic</strong> | Affiche l’écran **Diagnostics**. Cet écran permet à l’utilisateur d’envoyer des données de diagnostic à Apple. |
    | <strong>FileVault</strong> | Donne à l’utilisateur la possibilité de configurer le chiffrement FileVault. |
    | <strong>Diagnostics iCloud</strong> | Donne à l’utilisateur la possibilité d’envoyer des données de diagnostic iCloud à Apple. |
    | <strong>Inscription</strong>| Oblige l’utilisateur à inscrire l’appareil. |
    
   

10. Choisissez **OK**.

11. Pour enregistrer le profil, choisissez **Créer**.

## <a name="sync-managed-devices"></a>Synchroniser des appareils gérés
Maintenant qu’Intune est autorisé à gérer vos appareils, vous pouvez synchroniser Intune avec Apple pour voir vos appareils gérés dans le portail Azure d’Intune.

1. Dans Intune, sur le Portail Azure, sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste > **Appareils** > **Synchroniser**. ![Capture d’écran du nœud Appareils du programme d’inscription sélectionné, avec choix du lien Synchroniser.](./media/device-enrollment-program-enroll-ios/image06.png)

   Pour être conforme aux conditions d’Apple relatives à un trafic de programme d’inscription acceptable, Intune impose les restrictions suivantes :
   - Une synchronisation complète ne peut pas s’exécuter plus d’une fois tous les sept jours. Pendant une synchronisation complète, Intune extrait toute la liste actualisée des numéros de série attribués au serveur MDM Apple connecté à Intune. Si vous supprimez un appareil faisant partie du Programme d’inscription dans le portail Intune sans l’avoir désinscrit du serveur MDM Apple dans le portail DEP, il ne sera pas réimporté dans Intune tant que la synchronisation ne sera pas terminée.   
   - Une synchronisation est exécutée automatiquement toutes les 24 heures. Vous pouvez également synchroniser en cliquant sur le bouton **Synchroniser** (pas plus d’une fois toutes les 15 minutes). Toutes les demandes de synchronisation doivent se terminer en 15 minutes. Le bouton **Synchroniser** est désactivé tant que la synchronisation n’est pas terminée. Cette synchronisation actualise l’état existant de l’appareil et importe les nouveaux appareils affectés au serveur MDM Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Affecter un profil d’inscription à des appareils
Vous devez affecter un profil de programme d’inscription aux appareils pour pouvoir les inscrire.

1. Dans Intune, sur le Portail Azure, sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste.
2. Sélectionnez **Appareils** > choisissez des appareils dans la liste > **Attribuer un profil**.
3. Sous **Attribuer un profil**, choisissez un profil pour les appareils > **Attribuer**.

### <a name="assign-a-default-profile"></a>Attribuer un profil par défaut

Vous pouvez choisir un profil macOS et iOS à appliquer par défaut à tous les appareils qui s’inscrivent avec un jeton spécifique. 

1. Dans Intune, sur le portail Azure, sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste.
2. Sélectionnez **Définir un profil par défaut**, choisissez un profil dans la liste déroulante, puis sélectionnez **Enregistrer**. Ce profil s’appliquera à tous les appareils qui s’inscriront avec ce jeton.

## <a name="distribute-devices"></a>Distribuer des appareils
Vous avez activé la gestion et la synchronisation entre Apple et Intune, et affecté un profil permettant d’inscrire les appareils. Vous pouvez désormais distribuer les appareils aux utilisateurs. Pour les appareils avec affinité utilisateur, chaque utilisateur doit se voir attribuer une licence Intune. Les appareils sans affinité utilisateur nécessitent une licence d’appareil. Un appareil activé ne peut pas appliquer un profil d’inscription tant qu’il n’est pas réinitialisé.

## <a name="renew-a-dep-token"></a>Renouveler un jeton DEP  
1. Accédez à deploy.apple.com.  
2. Sous **Gérer les serveurs**, choisissez votre serveur MDM associé au fichier de jeton que vous voulez renouveler.
3. Choisissez **Générer un nouveau jeton**.

    ![Capture d’écran du nouveau jeton généré.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Choisissez **Votre jeton de serveur**.  
5. Dans [Intune sur le portail Azure](https://aka.ms/intuneportal), choisissez **Inscription de l’appareil** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez le jeton.
    ![Capture d’écran des jetons du programme d’inscription](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Choisissez **Renouveler le jeton**, puis entrez l’identifiant Apple qui a été utilisé pour créer le jeton d’origine.  
    ![Capture d’écran du nouveau jeton généré.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Chargez le jeton qui vient d’être téléchargé.  
9. Choisissez **Renouveler le jeton**. Vous verrez la confirmation que le jeton a été renouvelé.   
    ![Capture d’écran de la confirmation.](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>Étapes suivantes

Après l’inscription d’appareils macOS, vous pouvez commencer à [les gérer](device-management.md).
