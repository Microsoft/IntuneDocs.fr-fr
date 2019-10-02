---
title: Inscrire des appareils iOS - Programme d’inscription d’appareils
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils iOS d’entreprise à l’aide du programme d’inscription des appareils.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2e9b5eb15cf446b317818a93baa075cdbd33afd2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723305"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Inscrire automatiquement des appareils iOS avec le Programme d’inscription des appareils d’Apple

Vous pouvez configurer Intune de façon à inscrire des appareils iOS achetés dans le cadre du [Programme d’inscription des appareils (DEP)](https://deploy.apple.com) d’Apple. DEP vous permet d’inscrire un grand nombre d’appareils sans jamais les toucher. Des appareils tels que des iPhone et des iPad peuvent être envoyés directement aux utilisateurs. Quand l’utilisateur active l’appareil, l’Assistant Configuration s’exécute avec les paramètres préconfigurés et l’appareil s’inscrit à la gestion.

Pour activer l’inscription DEP, vous utilisez à la fois le portail Intune et le portail DEP Apple. Une liste de numéros de série ou un numéro de bon de commande est nécessaire pour que vous puissiez affecter des appareils à Intune à des fins de gestion. Vous créez des profils d’inscription DEP contenant les paramètres appliqués aux appareils lors de l’inscription.

D’ailleurs, l’inscription DEP ne fonctionne pas avec le [gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md).

## <a name="dep-and-the-company-portal"></a>DEP et le Portail d'entreprise

Les inscriptions DEP ne sont pas compatibles avec la version de l’App Store de l’application Portail d’entreprise. Vous pouvez autoriser les utilisateurs à accéder à l’application Portail d’entreprise sur un appareil DEP. Pour leur permettre l’accès, envoyez l’application à l’appareil à l’aide de **Installer le Portail d’entreprise avec VPP** (programme d’achat en volume) dans le profil DEP. Pour en savoir plus, voir [Inscrire automatiquement des appareils iOS avec le Programme d’inscription des appareils d’Apple](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

 Vous pouvez installer l’application Portail d’entreprise sur des appareils déjà inscrits avec DEP. Pour ce faire, déployez l’application Portail d’entreprise via Intune avec une [stratégie de configuration d’application](../apps/app-configuration-policies-use-ios.md) appliquée.

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
- [Autorité de gestion des appareils mobiles (MDM)](../fundamentals/mdm-authority-set.md)
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

   ![Capture d’écran du volet Jeton de programme d’inscription dans l’espace de travail Certificats Apple pour télécharger une clé publique.](./media/device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Choisissez **Télécharger votre clé publique** pour télécharger et enregistrer le fichier de clé de chiffrement (.pem) en local. Le fichier .pem est utilisé pour demander un certificat de relation d'approbation à partir du portail du programme d'inscription d'appareils d'Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Étape 2. Utilisez votre clé pour télécharger un jeton auprès d’Apple.

1. Choisissez **Créer un jeton pour le Programme d’inscription des appareils d’Apple** pour ouvrir le portail du programme de déploiement d’Apple, et connectez-vous avec votre ID Apple d’entreprise. Vous pouvez utiliser cet ID Apple pour renouveler votre jeton DEP.
2. Dans le portail des [programmes de déploiement](https://deploy.apple.com) d’Apple, choisissez **Get Started** (Prise en main) pour **Programme d’inscription des appareils**.

3. Dans la page **Gérer les serveurs** choisissez **Ajouter un serveur MDM**.
4. Entrez le **Nom du serveur MDM**, puis choisissez **Suivant**. Le nom du serveur vous permet d’identifier le serveur de gestion des appareils mobiles (MDM) uniquement. Il ne s’agit pas du nom ou de l’URL du serveur Microsoft Intune.

5. La boîte de dialogue **Ajouter &lt;nom_serveur&gt;** s’ouvre avec le message **Charger votre clé publique**. Sélectionnez **Choisir un fichier...** pour charger le fichier .pem, puis choisissez **Suivant**.

6. Accédez à **Programme de déploiement** &gt; **Programme d’inscription d’appareils** &gt; **Gérer les appareils**.
7. Sous **Choisir les appareils par**, spécifiez comment les appareils sont identifiés :
    - **Numéro de série**
    - **Numéro de commande**
    - **Télécharger un fichier CSV**

   ![Capture d’écran montrant le choix des appareils par numéro de série, la définition de Attribuer au serveur comme paramètre Choisir l’action, et la sélection du nom du serveur.](./media/device-enrollment-program-enroll-ios/enrollment-program-token-specify-serial.png)

8. Pour **Choisir une action**, choisissez **Affecter au serveur**, le &lt;nom_serveur&gt; spécifié pour Microsoft Intune, puis **OK**. Le portail Apple affecte les appareils spécifiés au serveur Intune pour la gestion, puis affiche **Affectation terminée**.

   Dans le portail Apple, accédez à **Programmes de déploiement** &gt; **Programme d’inscription d’appareils** &gt; **Afficher l’historique d’affectation** pour afficher la liste des appareils et leur affectation aux serveurs MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Étape 3. Enregistrez l’ID Apple utilisé pour créer le jeton.

Dans le portail Azure d’Intune, fournissez l’ID Apple pour référence ultérieure.

![Capture d’écran : spécification de l’ID Apple utilisé pour créer le jeton du programme d’inscription et accès à ce jeton.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>Étape 4. Chargez votre jeton et choisissez des balises d’étendue.

1. Dans la zone **Jeton Apple**, accédez au fichier du certificat (.pem) et choisissez **Ouvrir**.
2. Pour appliquer des [balises d’étendue](../fundamentals/scope-tags.md) à ce jeton DEP, choisissez **Étendue (balises)** , puis sélectionnez les balises d’étendue souhaitées. Les balises d’étendue appliquées à un jeton seront héritées par les profils et les appareils ajoutés à ce jeton.
3. Choisissez **Créer**.

Avec le certificat Push, Intune peut inscrire et gérer des appareils iOS en envoyant la stratégie aux appareils mobiles inscrits. Intune se synchronise automatiquement avec Apple pour afficher votre compte de programme d’inscription.

## <a name="create-an-apple-enrollment-profile"></a>Créer un profil d’inscription Apple

Maintenant que vous avez installé votre jeton, vous pouvez créer un profil d’inscription pour les appareils DEP. Un profil d'inscription d'appareil définit les paramètres appliqués à un groupe d'appareils lors de l’inscription. Il y a une limite de 100 profils d’inscription par jeton DEP.

> [!NOTE]
> Les appareils sont bloqués s’il n’y a pas suffisamment de licences Portail d’entreprise pour un jeton VPP, ou si le jeton a expiré. Intune affiche une alerte lorsqu’un jeton est sur le point d’expirer ou qu’il n’y a presque plus de licences.
 

1. Dans Intune, sur le Portail Azure, choisissez **Inscription des appareil** > **Inscription Apple** > **Jetons du programme d’inscription**.
2. Sélectionnez un jeton, choisissez **Profils** > **Créer un profil** > **iOS**.

    ![Capture d’écran de création d’un profil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Sur la page **de base**, entrez un **nom** et une **description** du profil qui serviront à des fins d’administration. Les utilisateurs ne voient pas ces détails. Vous pouvez utiliser ce champ **Nom** pour créer un groupe dynamique dans Azure Active Directory. Utilisez le nom du profil pour définir le paramètre enrollmentProfileName et attribuer des appareils avec ce profil d’inscription. En savoir plus sur les [groupes dynamiques Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![Nom et description du profil.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Sélectionnez **Suivant : paramètres de gestion des appareils**.

5. Pour **Affinité utilisateur**, indiquez si les appareils possédant ce profil doivent être inscrits avec ou sans utilisateur attribué.
    - **Inscrire avec affinité utilisateur** : choisissez cette option pour les appareils qui appartiennent à des utilisateurs et qui veulent utiliser le Portail d’entreprise pour des services comme l’installation d’applications. En cas d’utilisation d’ADFS et si le profil d’inscription a l’option **S’authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration** définie sur **Non**, [Point de terminaison mixte/Nom d’utilisateur WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) [En savoir plus](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint) est requis.

    - **Inscrire sans affinité utilisateur** : choisissez cette option pour les appareils non affiliés à un seul utilisateur, Utilisez cette option pour les appareils qui n’accèdent pas aux données utilisateur locales. Les applications telles que l’application Portail d’entreprise ne fonctionnent pas.

5. Si vous avez choisi **Inscrire avec affinité utilisateur**, vous pouvez autoriser les utilisateurs à s’authentifier avec le Portail d’entreprise au lieu de l’Assistant Configuration Apple.

    ![Authentification avec le Portail d’entreprise.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Si vous souhaitez effectuer l’une des opérations suivantes, définissez **Sélectionnez où les utilisateurs doivent s'authentifier** sur **Portail d’entreprise**.
    >    - utiliser l’authentification multifacteur
    >    - inviter les utilisateurs à changer leur mot de passe lors de leur première connexion
    >    - demander aux utilisateurs de réinitialiser leurs mots de passe arrivés à expiration lors de l’inscription
    >
    > Ces fonctionnalités ne sont pas prises en charge lors de l’authentification avec l’Assistant Configuration Apple.

6. Si vous avez choisi **Portail d’entreprise** pour **Sélectionnez où les utilisateurs doivent s'authentifier**, vous pouvez utiliser un jeton VPP pour installer automatiquement le Portail d’entreprise sur l’appareil. Dans ce cas, l’utilisateur n’a pas besoin de fournir un ID Apple. Pour installer le portail d’entreprise avec un jeton VPP, choisissez un jeton sous **Installer le portail d’entreprise avec un jeton VPP**. Requiert que le Portail d’entreprise ait déjà été ajouté au jeton VPP. Ne configurez pas une stratégie pour exiger l’application pour les utilisateurs. Intune installe automatiquement le Portail d’entreprise sur les appareils auxquels ce profil d’inscription est appliqué. Vérifiez que le jeton n’arrive pas à expiration et que vous avez suffisamment de licences d’appareil pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune installe le portail d’entreprise de l’App Store à la place (et demande un identifiant Apple). 

    > [!NOTE]
    > Lorsque **Sélectionnez où les utilisateurs doivent s'authentifier** est défini sur **Portail d'entreprise**, assurez-vous que le processus d’inscription de l’appareil est effectué dans les 24 premières heures suivant le téléchargement du portail d’entreprise vers l’appareil DEP. Sinon, l’inscription peut échouer et une réinitialisation aux paramètres d’usine est alors nécessaire pour inscrire l’appareil.
    
    ![Capture d’écran de l’installation du portail d’entreprise avec un jeton VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Si vous avez choisi **Assistant Configuration** pour **Sélectionnez où les utilisateurs doivent s'authentifier** mais que vous souhaitez également utiliser l’accès conditionnel ou déployer des applications d’entreprise sur les appareils, vous devez installer le Portail d’entreprise sur les appareils. Pour ce faire, choisissez **Oui** pour **Installer le Portail d'entreprise**.  Si vous souhaitez que les utilisateurs reçoivent le Portail d’entreprise sans avoir à s’authentifier dans l’App Store, choisissez d’**installer portail d’entreprise** avec VPP et sélectionnez un jeton VPP. Vérifiez que le jeton n’arrive pas à expiration et que vous avez suffisamment de licences d’appareils pour que l’application Portail d’entreprise se déploie correctement.

8. Si vous avez choisi un jeton pour **Installer le Portail d’entreprise avec VPP**, vous pouvez verrouiller l’appareil en mode Application unique (plus précisément l’application Portail d’entreprise) immédiatement après la fin de l’Assistant Configuration. Choisissez **Oui** pour **Exécuter le portail d’entreprise en mode Application unique jusqu’à l’authentification** pour définir cette option. Pour utiliser l’appareil, l’utilisateur doit d’abord s’authentifier en se connectant avec le portail d’entreprise.

    L’authentification multifacteur n’est pas prise en charge sur un appareil unique verrouillé en mode Application unique. Cette limitation existe parce que l’appareil ne peut pas basculer vers une autre application pour effectuer le deuxième facteur d’authentification. Par conséquent, si vous souhaitez une authentification multifacteur sur un appareil en mode Application unique, le second facteur doit se trouver sur un autre appareil.

    Cette fonctionnalité est uniquement pris en charge pour iOS 11.3.1 et versions ultérieures.

   ![Capture d’écran du mode Application unique.](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. Si vous souhaitez que les appareils qui ont ce profil soient supervisés, choisissez **Oui** pour **Supervisé**.

    ![Capture d’écran Paramètres de gestion des appareils.](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

    Les appareils **supervisés** offrent plus d’options de gestion ; le Verrouillage d’activation est par défaut désactivé. Microsoft recommande l’utilisation du Programme d’inscription des appareils comme mécanisme d’activation du mode supervisé, en particulier si vous déployez un grand nombre d’appareils iOS.

    Les utilisateurs sont informés du fait que leurs appareils sont supervisés de deux manières :

   - L’écran de verrouillage indique : « Cet iPhone est géré par Contoso. »
   - L’écran **Paramètres** > **Général** > **À propos de** indique : « Cet iPhone est supervisé. Contoso peut surveiller votre trafic Internet et localiser cet appareil. »

     > [!NOTE]
     > Seul Apple Configurator permet de rétablir la supervision sur un appareil inscrit sans supervision. Pour cela, l’appareil iOS doit être relié à un Mac par câble USB. Découvrez plus d’informations sur ceci dans la [documentation d’Apple Configurator](http://help.apple.com/configurator/mac/2.3).

10. Choisissez si vous souhaitez que l’inscription soit verrouillée pour les appareils possédant ce profil. **L’inscription verrouillée** désactive les paramètres iOS qui permettent de supprimer le profil de gestion du menu **Paramètres**. Une fois l’appareil inscrit, vous ne pouvez plus modifier ce paramètre sans réinitialiser l’appareil. Pour ces appareils, le Mode d’administration **Supervisé** doit avoir la valeur *Oui*. 

11. Choisissez si vous souhaitez que les appareils possédant ce profil puissent **Se synchroniser avec des ordinateurs**. Si vous choisissez **Autoriser Apple Configurator par certificat**, vous devez choisir un certificat sous **Certificats Apple Configurator**.

12. Si vous avez sélectionné **Autoriser Apple Configurator par certificat** à l’étape précédente, choisissez un certificat Apple Configurator à importer.

13. Vous pouvez spécifier pour les appareils un format d’attribution de noms qui est automatiquement appliqué lorsqu’ils s’inscrivent et à chaque archivage successif. Pour créer un modèle de nom, sélectionnez **Oui** sous **Appliquer le modèle de nom d'appareil**. Ensuite, dans la zone **Modèle de nom d’appareil**, entrez le modèle à utiliser pour les noms à l’aide de ce profil. Vous pouvez spécifier un format de modèle incluant le type d’appareil et le numéro de série. 

14. Choisissez **Suivant : Personnalisation de l’Assistant Configuration**.

15. À la page **Personnalisation de l’Assistant Configuration**, configurez les paramètres de profil suivants : ![Personnalisation de l’Assistant Configuration](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Paramètres du service | Description |
    |---|---|
    | <strong>Nom du service</strong> | S’affiche quand l’utilisateur appuie sur <strong>À propos de la configuration</strong> pendant l’activation. |
    |    <strong>Numéro de téléphone du service</strong>     | S’affiche quand l’utilisateur clique sur le bouton <strong>Besoin d’aide</strong> pendant l’activation. |

    Vous pouvez choisir de masquer les écrans de l’Assistant Configuration sur l’appareil lors de l’installation de l’utilisateur.
    - Si vous choisissez **Masquer**, l’écran ne s’affiche pas pendant la configuration. Après avoir configuré l’appareil, l’utilisateur peut toujours accéder au menu **Paramètres** pour configurer la fonctionnalité.
    - Si vous choisissez **Afficher**, l’écran s’affiche pendant la configuration. L’utilisateur peut parfois ignorer l’écran et n’entreprendre aucune action. Mais il pourra ensuite accéder au menu **Paramètres** de l’appareil pour configurer la fonctionnalité. 


    | Paramètres de l’écran de l’Assistant Configuration | Si vous choisissez **Afficher**, pendant la configuration, l’appareil... |
    |------------------------------------------|------------------------------------------|
    | <strong>Code secret</strong> | Invite l’utilisateur à entrer un code secret. Exige toujours un code secret pour les appareils non sécurisés, sauf si l’accès est contrôlé d’une autre façon (par ex. en mode plein écran, qui limite l’appareil à une seule application). |
    | <strong>Services d’emplacement</strong> | Invite l’utilisateur à entrer son emplacement. |
    | <strong>Restauration</strong> | Afficher l’écran Applications et données. Cet écran donne à l’utilisateur la possibilité de restaurer ou de transférer des données à partir de la sauvegarde iCloud pendant la configuration de l’appareil. |
    | <strong>ID Apple et iCloud</strong> | Donner à l’utilisateur la possibilité de se connecter avec son ID Apple et d’utiliser iCloud.                         |
    | <strong>Conditions générales</strong> | Oblige l’utilisateur à accepter les conditions générales d’Apple. |
    | <strong>Touch ID</strong> | Donne à l’utilisateur la possibilité de configurer l’identification par empreinte digitale sur l’appareil. |
    | <strong>Apple Pay</strong> | Donne à l’utilisateur la possibilité de configurer Apple Pay sur l’appareil. |
    | <strong>Zoom</strong> | Donne à l’utilisateur la possibilité d’effectuer un zoom sur l’affichage pendant la configuration de l’appareil. |
    | <strong>Siri</strong> | Donne à l’utilisateur la possibilité de configurer Siri. |
    | <strong>Données de diagnostic</strong> | Afficher l’écran Diagnostics. Cet écran permet à l’utilisateur d’envoyer des données de diagnostic à Apple. |
    | <strong>Afficher la sonnerie</strong> | Donner à l’utilisateur la possibilité d’activer Afficher la sonnerie |
    | <strong>Confidentialité</strong> | Afficher l’écran de confidentialité. |
    | <strong>Migration Android</strong> | Donner à l’utilisateur la possibilité de migrer des données à partir d’un appareil Android. |
    | <strong>iMessage et FaceTime</strong> | Donner à l’utilisateur la possibilité de configurer iMessage et FaceTime. |
    | <strong>Intégration</strong> | Afficher des écrans d’information sur l’intégration à des fins de formation des utilisateurs, par exemple pour Cover Sheet, le multitâche et le centre de contrôle. |
    | <strong>Surveiller la migration</strong> | Donner à l’utilisateur la possibilité de migrer des données à partir d’une montre. |
    | <strong>Heure de l’écran</strong> | Afficher l’écran Heure de l’écran. |
    | <strong>Mise à jour logicielle</strong> | Afficher l’écran de mise à jour logicielle obligatoire. |
    | <strong>Configuration SIM</strong> | Donner à l’utilisateur la possibilité d’ajouter un plan de téléphonie mobile. |
    | <strong>Apparence</strong> | Afficher l’écran Apparence. |
    | <strong>Langage Express</strong>| Afficher l’écran Langage Express. |
    | <strong>Langage par défaut</strong> | Donner à l’utilisateur la possibilité de choisir sa **Langue par défaut**. |
    | <strong>Migration d’un appareil vers un autre</strong> | Donner à l’utilisateur la possibilité de migrer des données de leur ancien appareil vers cet appareil.|
    

16. Choisissez **Suivant** pour accéder à la page **Vérifier + créer**.

17. Pour enregistrer le profil, choisissez **Créer**.

## <a name="sync-managed-devices"></a>Synchroniser des appareils gérés
Maintenant qu’Intune est autorisé à gérer vos appareils, vous pouvez synchroniser Intune avec Apple pour voir vos appareils gérés dans le portail Azure d’Intune.

1. Dans Intune, sur le Portail Azure, sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste > **Appareils** > **Synchroniser**. ![Captures d’écran du nœud d’appareils du programme d'inscription et lien de synchronisation.](./media/device-enrollment-program-enroll-ios/image06.png)

   Pour respecter les conditions d’Apple relatives à un trafic de programme d’inscription acceptable, Intune impose les restrictions suivantes :
   - Une synchronisation complète ne peut pas s’exécuter plus d’une fois tous les sept jours. Pendant une synchronisation complète, Intune extrait toute la liste actualisée des numéros de série attribués au serveur MDM Apple connecté à Intune. Si un appareil DEP est supprimé du portail Intune, son affectation au serveur Apple MDM dans le portail DEP doit être supprimée. Si ce n’est pas le cas, il ne sera pas réimporté dans Intune tant que la synchronisation complète n’aura pas été exécutée.   
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
