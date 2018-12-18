---
title: Inscrire des appareils iOS - Programme d’inscription d’appareils
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils iOS d’entreprise à l’aide du programme d’inscription des appareils.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 9f27d8b2334ff38146949c28898040da6a714e0a
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032478"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Inscrire automatiquement des appareils iOS avec le Programme d’inscription des appareils d’Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez configurer Intune de façon à inscrire des appareils iOS achetés dans le cadre du [Programme d’inscription des appareils (DEP)](https://deploy.apple.com) d’Apple. Vous pouvez activer l’inscription DEP pour un grand nombre d’appareils sans jamais les toucher. Vous pouvez expédier des appareils tels que des iPhone et iPad directement aux utilisateurs. Quand l’utilisateur active l’appareil, l’Assistant Configuration s’exécute avec les paramètres préconfigurés et l’appareil s’inscrit à la gestion.

Pour activer l’inscription DEP, vous utilisez à la fois le portail Intune et le portail DEP Apple. Une liste de numéros de série ou un numéro de bon de commande est nécessaire pour que vous puissiez affecter des appareils à Intune à des fins de gestion. Vous créez des profils d’inscription DEP contenant les paramètres appliqués aux appareils lors de l’inscription.

Notez que l’inscription DEP ne fonctionne pas avec le [gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>Qu’est-ce que le mode supervisé ?
Apple a introduit le mode supervisé dans iOS 5. Un appareil iOS en mode supervisé peut être géré avec plus de contrôles. Il est donc particulièrement utile pour les appareils d’entreprise. Intune prend en charge la configuration des appareils pour le mode supervisé dans le cadre du Programme d’inscription des appareils Apple. 

La prise en charge d’appareils DEP non supervisés a été dépréciée dans iOS 11. Dans iOS 11 et versions ultérieures, les appareils DEP configurés doivent toujours être supervisés. L’indicateur DEP is_supervised sera ignoré dans une version ultérieure d’iOS.

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Prérequis
- Appareils achetés dans le cadre du [Programme d’inscription des appareils d’Apple](http://deploy.apple.com)
- [Autorité MDM](mdm-authority-set.md)
- [Certificat Push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obtenir un jeton DEP Apple

Avant de pouvoir inscrire des appareils iOS à l’aide du programme DEP, vous devez obtenir un fichier de jeton (.p7m) DEP auprès d’Apple. Ce jeton permet à Intune de synchroniser les informations sur les appareils DEP appartenant à votre entreprise. Il permet également à Intune de charger des profils d’inscription sur Apple et d’attribuer des appareils à ces profils.

Vous utilisez le portail DEP Apple pour créer un jeton DEP. Vous utilisez également le portail DEP pour affecter des appareils à Intune à des fins de gestion.

> [!NOTE]
> Si vous supprimez le jeton du portail classique Intune avant de migrer vers Azure, Intune risque de restaurer le jeton Apple DEP supprimé. Vous pouvez supprimer à nouveau le jeton DEP du portail Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Étape 1. Téléchargez le certificat de clé publique Intune nécessaire à la création du jeton.

1. Dans [Intune, sur le Portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > **Ajouter**.

    ![Récupérez un jeton du programme d’inscription.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Autorisez Microsoft à envoyer des informations d’utilisateur et d’appareil à Apple en sélectionnant **J’accepte**.

   ![Capture d’écran du volet Jeton de programme d’inscription dans l’espace de travail Certificats Apple pour télécharger une clé publique.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Choisissez **Télécharger votre clé publique** pour télécharger et enregistrer le fichier de clé de chiffrement (.pem) en local. Le fichier .pem est utilisé pour demander un certificat de relation d'approbation à partir du portail du programme d'inscription d'appareils d'Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Étape 2. Utilisez votre clé pour télécharger un jeton auprès d’Apple.

1. Choisissez **Créer un jeton pour le Programme d’inscription des appareils d’Apple** pour ouvrir le portail du programme de déploiement d’Apple, et connectez-vous avec votre ID Apple d’entreprise. Vous pouvez utiliser cet ID Apple pour renouveler votre jeton DEP.
2.  Dans le portail des [programmes de déploiement](https://deploy.apple.com) d’Apple, choisissez **Get Started** (Prise en main) pour **Programme d’inscription des appareils**.

3. Dans la page **Gérer les serveurs** choisissez **Ajouter un serveur MDM**.
4. Entrez le **Nom du serveur MDM**, puis choisissez **Suivant**. Le nom du serveur vous permet d’identifier le serveur de gestion des appareils mobiles (MDM) uniquement. Il ne s’agit pas du nom ou de l’URL du serveur Microsoft Intune.

5. La boîte de dialogue **Ajouter &lt;nom_serveur&gt;** s’ouvre avec le message **Charger votre clé publique**. Choisissez **Choisir un fichier** pour charger le fichier .pem, puis choisissez **Suivant**.

6. Accédez à **Programme de déploiement** &gt; **Programme d’inscription d’appareils** &gt; **Gérer les appareils**.
7. Sous **Choisir les appareils par**, spécifiez comment les appareils sont identifiés :
    - **Numéro de série**
    - **Numéro de commande**
    - **Télécharger un fichier CSV**

   ![Capture d’écran montrant le choix des appareils par numéro de série, la définition de Attribuer au serveur comme paramètre Choisir l’action, et la sélection du nom du serveur.](./media/enrollment-program-token-specify-serial.png)

8. Pour **Choisir une action**, choisissez **Affecter au serveur**, le &lt;nom_serveur&gt; spécifié pour Microsoft Intune, puis **OK**. Le portail Apple affecte les appareils spécifiés au serveur Intune pour la gestion, puis affiche **Affectation terminée**.

   Dans le portail Apple, accédez à **Programmes de déploiement** &gt; **Programme d’inscription d’appareils** &gt; **Afficher l’historique d’affectation** pour afficher la liste des appareils et leur affectation aux serveurs MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Étape 3. Enregistrez l’ID Apple utilisé pour créer le jeton.

Dans le portail Azure d’Intune, fournissez l’ID Apple pour référence ultérieure.

![Capture d’écran : spécification de l’ID Apple utilisé pour créer le jeton du programme d’inscription et accès à ce jeton.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Étape 4. Chargez votre jeton.
Dans la zone **Jeton Apple**, accédez au fichier du certificat (.pem), choisissez **Ouvrir**, puis **Créer**. Avec le certificat Push, Intune peut inscrire et gérer des appareils iOS en envoyant la stratégie aux appareils mobiles inscrits. Intune se synchronise automatiquement avec Apple pour afficher votre compte de programme d’inscription.

## <a name="create-an-apple-enrollment-profile"></a>Créer un profil d’inscription Apple

Maintenant que vous avez installé votre jeton, vous pouvez créer un profil d’inscription pour les appareils DEP. Un profil d'inscription d'appareil définit les paramètres appliqués à un groupe d'appareils lors de l’inscription.

> [!NOTE]
> Les appareils seront bloqués s’il n’y a pas suffisamment de licences Portail d’entreprise pour un jeton VPP, ou si le jeton a expiré. Intune affiche une alerte lorsqu’un jeton est sur le point d’expirer ou qu’il n’y a presque plus de licences.
 

1. Dans Intune, sur le Portail Azure, choisissez **Inscription des appareil** > **Inscription Apple** > **Jetons du programme d’inscription**.
2. Sélectionnez un jeton et choisissez **Profils**, puis **Créer un profil**.

    ![Capture d’écran de création d’un profil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Dans **Créer un profil**, entrez le **Nom** et la **Description** du profil qui serviront à des fins d’administration. Les utilisateurs ne voient pas ces détails. Vous pouvez utiliser ce champ **Nom** pour créer un groupe dynamique dans Azure Active Directory. Utilisez le nom du profil pour définir le paramètre enrollmentProfileName et attribuer des appareils avec ce profil d’inscription. En savoir plus sur les [groupes dynamiques Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nom et description du profil.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Pour **Affinité utilisateur**, indiquez si les appareils possédant ce profil doivent être inscrits avec ou sans utilisateur attribué.
    - **Inscrire avec affinité utilisateur** : choisissez cette option pour les appareils qui appartiennent à des utilisateurs et qui veulent utiliser le Portail d’entreprise pour des services comme l’installation d’applications. En cas d’utilisation d’ADFS et si le profil d’inscription a l’option **S’authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration** définie sur **Non**, [Point de terminaison mixte/Nom d’utilisateur WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) [En savoir plus](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint) est requis.

    - **Inscrire sans affinité utilisateur** : choisissez cette option pour les appareils non affiliés à un seul utilisateur, et pour les appareils qui effectuent des tâches sans accéder aux données de l’utilisateur local. Les applications telles que l’application Portail d’entreprise ne fonctionnent pas.

5. Si vous avez choisi **Inscrire avec affinité utilisateur**, vous avez la possibilité d’autoriser les utilisateurs à s’authentifier avec le Portail d’entreprise au lieu de l’Assistant Configuration Apple.

    ![Authentification avec le Portail d’entreprise.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Si vous souhaitez effectuer l’une des options suivantes, définissez **S’authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration Apple** sur **Oui**.
    >    - utiliser l’authentification multifacteur
    >    - inviter les utilisateurs à changer leur mot de passe lors de leur première connexion
    >    - demander aux utilisateurs de réinitialiser leurs mots de passe arrivés à expiration lors de l’inscription
    >
    > Ces fonctionnalités ne sont pas prises en charge lors de l’authentification avec l’Assistant Configuration Apple.

6. Si vous avez choisi **Oui** pour l’option **S’authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration Apple**, vous avez la possibilité d’utiliser un jeton du programme d’achat en volume (VPP, Volume Purchase Program) pour installer automatiquement le portail d’entreprise sur l’appareil sans que l’utilisateur ne fournisse un identifiant Apple. Pour installer le portail d’entreprise avec un jeton VPP, choisissez un jeton sous **Installer le portail d’entreprise avec un jeton VPP**. Vérifiez que le jeton n’arrive pas à expiration et que vous avez suffisamment de licences d’appareil pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune installe le portail d’entreprise de l’App Store à la place (et demande un identifiant Apple).

    ![Capture d’écran de l’installation du portail d’entreprise avec un jeton VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Si vous avez choisi un jeton pour **Installer le portail d’entreprise avec VPP**, vous avez la possibilité de verrouiller l’appareil en mode Application unique (plus précisément l’application Portail d’entreprise) immédiatement après la fin de l’Assistant Configuration. Choisissez **Oui** pour **Exécuter le portail d’entreprise en mode Application unique jusqu’à l’authentification** pour définir cette option. Pour utiliser l’appareil, l’utilisateur doit d’abord s’authentifier en se connectant avec le portail d’entreprise.
    Cette fonctionnalité est uniquement pris en charge pour iOS 11.3.1 et versions ultérieures.

8. Choisissez **Paramètres de gestion des appareils** et indiquez si vous souhaitez que les appareils possédant ce profil soient supervisés ou non.

    ![Capture d’écran Paramètres de gestion des appareils.](./media/device-enrollment-program-enroll-ios/devicemanagementsettingsblade.png)

    Les appareils **supervisés** offrent plus d’options de gestion ; le Verrouillage d’activation est par défaut désactivé. Microsoft recommande l’utilisation du Programme d’inscription des appareils comme mécanisme d’activation du mode supervisé, en particulier pour les organisations qui déploient un grand nombre d’appareils iOS.

    Les utilisateurs sont informés du fait que leurs appareils sont supervisés de deux manières :

   - L’écran de verrouillage indique : « Cet iPhone est géré par Contoso. »
   - L’écran **Paramètres** > **Général** > **À propos de** indique : « Cet iPhone est supervisé. Contoso peut surveiller votre trafic Internet et localiser cet appareil. »

     > [!NOTE]
     > Seul Apple Configurator permet de rétablir la supervision sur un appareil inscrit sans supervision. Pour cela, l’appareil iOS doit être relié à un Mac par câble USB. Découvrez plus d’informations sur ceci dans la [documentation d’Apple Configurator](http://help.apple.com/configurator/mac/2.3).

9. Choisissez si vous souhaitez ou non que l’inscription soit verrouillée pour les appareils possédant ce profil. **L’inscription verrouillée** désactive les paramètres iOS qui permettent de supprimer le profil de gestion du menu **Paramètres**. Une fois l’appareil inscrit, vous ne pouvez plus modifier ce paramètre sans réinitialiser l’appareil. Pour ces appareils, le Mode d’administration **Supervisé** doit avoir la valeur *Oui*. 

10. Choisissez si vous souhaitez ou non que les appareils possédant ce profil puissent **Se synchroniser avec des ordinateurs**. Si vous choisissez **Autoriser Apple Configurator par certificat**, vous devez choisir un certificat sous **Certificats Apple Configurator**.

11. Si vous avez sélectionné **Autoriser Apple Configurator par certificat** à l’étape précédente, choisissez un certificat Apple Configurator à importer.

12. Choisissez **OK**.

13. Choisissez **Personnalisation de l’Assistant Configuration** pour configurer les paramètres de profil suivants : ![Personnalisation de l’Assistant Configuration](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Paramètres du service | Description |
    |---|---|
    | <strong>Nom du service</strong> | S’affiche quand l’utilisateur appuie sur <strong>À propos de la configuration</strong> pendant l’activation. |
    |    <strong>Numéro de téléphone du service</strong>     | S’affiche quand l’utilisateur clique sur le bouton <strong>Besoin d’aide</strong> pendant l’activation. |

  Vous pouvez choisir d’afficher ou de masquer différents écrans de l’Assistant Configuration sur l’appareil quand l’utilisateur le configure.
  - Si vous choisissez **Masquer**, l’écran ne s’affiche pas pendant la configuration. Après avoir configuré l’appareil, l’utilisateur pourra toujours accéder au menu **Paramètres** pour configurer la fonctionnalité.
  - Si vous choisissez **Afficher**, l’écran s’affiche pendant la configuration. L’utilisateur peut parfois ignorer l’écran et n’entreprendre aucune action. Mais il pourra ensuite accéder au menu **Paramètres** de l’appareil pour configurer la fonctionnalité. 


    | Paramètres des écrans de l’Assistant Configuration | Si vous choisissez **Afficher**, pendant la configuration, l’appareil… |
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


14. Choisissez **OK**.

15. Pour enregistrer le profil, choisissez **Créer**.

## <a name="sync-managed-devices"></a>Synchroniser des appareils gérés
Maintenant qu’Intune est autorisé à gérer vos appareils, vous pouvez synchroniser Intune avec Apple pour voir vos appareils gérés dans le portail Azure d’Intune.

1. Dans Intune, sur le Portail Azure, sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste > **Appareils** > **Synchroniser**. ![Capture d’écran du nœud Appareils du programme d’inscription sélectionné, avec choix du lien Synchroniser.](./media/device-enrollment-program-enroll-ios/image06.png)

   Pour être conforme aux conditions d’Apple relatives à un trafic de programme d’inscription acceptable, Intune impose les restrictions suivantes :
   - Une synchronisation complète ne peut pas s’exécuter plus d’une fois tous les sept jours. Pendant une synchronisation complète, Intune extrait toute la liste actualisée des numéros de série attribués au serveur MDM Apple connecté à Intune. Une fois qu’un appareil du Programme d’inscription est supprimé du portail Intune sans avoir été désinscrit du serveur MDM Apple dans le portail DEP, il n’est pas réimporté dans Intune tant que la synchronisation complète n’a pas été exécutée.   
   - Une synchronisation est exécutée automatiquement toutes les 24 heures. Vous pouvez également synchroniser en cliquant sur le bouton **Synchroniser** (pas plus d’une fois toutes les 15 minutes). Toutes les demandes de synchronisation doivent se terminer en 15 minutes. Le bouton **Synchroniser** est désactivé tant que la synchronisation n’est pas terminée. Cette synchronisation actualise l’état existant de l’appareil et importe les nouveaux appareils affectés au serveur MDM Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Affecter un profil d’inscription à des appareils
Vous devez affecter un profil de programme d’inscription aux appareils pour pouvoir les inscrire.

>[!NOTE]
>Vous pouvez également affecter des numéros de série aux profils à partir du panneau **Numéros de série Apple**.

1. Dans Intune, sur le Portail Azure, sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste.
2. Sélectionnez **Appareils** > choisissez des appareils dans la liste > **Attribuer un profil**.
3. Sous **Attribuer un profil**, choisissez un profil pour les appareils > **Attribuer**.

### <a name="assign-a-default-profile"></a>Attribuer un profil par défaut

Vous pouvez choisir un profil à appliquer par défaut à tous les appareils qui s’inscrivent avec un jeton spécifique.

1. Dans Intune, sur le Portail Azure, sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste.
2. Sélectionnez **Définir un profil par défaut**, choisissez un profil dans la liste déroulante, puis sélectionnez **Enregistrer**. Ce profil s’appliquera à tous les appareils qui s’inscriront avec ce jeton.

## <a name="distribute-devices"></a>Distribuer des appareils
Vous avez activé la gestion et la synchronisation entre Apple et Intune, et affecté un profil pour permettre d’inscrire vos appareils DEP. Vous pouvez désormais distribuer les appareils aux utilisateurs. Pour les appareils avec affinité utilisateur, chaque utilisateur doit se voir attribuer une licence Intune. Les appareils sans affinité utilisateur nécessitent une licence d’appareil. Un appareil activé ne peut pas appliquer un profil d’inscription tant qu’il n’est pas réinitialisé.

Consultez [Inscrire un appareil iOS dans Intune avec le Programme d’inscription des appareils](/intune-user-help/enroll-your-device-dep-ios).

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
