---
title: Inscription au programme Apple School Manager pour les appareils iOS
titleSuffix: Microsoft Intune
description: Découvrez comment configurer l’inscription au programme Apple School Manager pour les appareils iOS d’entreprise avec Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 645cb2c920d3da56bb0267073c1951d0b72d73de
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505648"
---
# <a name="set-up-ios-device-enrollment-with-apple-school-manager"></a>Configurer l’inscription des appareils iOS avec Apple School Manager

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous pouvez configurer Intune pour inscrire des appareils iOS achetés dans le cadre du programme [Apple School Manager](https://school.apple.com/). En utilisant Intune avec Apple School Manager, vous pouvez inscrire de grandes quantités d’appareils iOS sans jamais les avoir en main. Quand un étudiant ou un enseignant active l’appareil, l’Assistant Configuration s’exécute avec les paramètres préconfigurés et l’appareil s’inscrit à la gestion.

Pour activer l’inscription Apple School Manager, vous utilisez à la fois les portails Intune et Apple School Manager. Une liste de numéros de série ou un numéro de bon de commande est nécessaire pour que vous puissiez affecter des appareils à Intune à des fins de gestion. Vous créez des profils d’inscription DEP contenant les paramètres appliqués aux appareils lors de l’inscription.

L’inscription à Apple School Manager n’est pas compatible avec le [Programme d’inscription des appareils d’Apple](device-enrollment-program-enroll-ios.md) ni avec le [gestionnaire d’inscription des appareils](device-enrollment-manager-enroll.md).

**Prérequis**
- [Certificat push Apple Mobile Device Management (MDM)](apple-mdm-push-certificate-get.md)
- [Autorité MDM](../fundamentals/mdm-authority-set.md)
- [Certificat Push MDM Apple](apple-mdm-push-certificate-get.md)
- Si vous utilisez ADFS, l’affinité utilisateur nécessite un [point de terminaison WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [En savoir plus](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Appareils achetés via le programme [Apple School Management](http://school.apple.com)

## <a name="get-an-apple-token-and-assign-devices"></a>Obtenir un jeton Apple et affecter des appareils

Avant de pouvoir inscrire des appareils iOS d’entreprise avec Apple School Manager, vous devez obtenir un fichier de jeton (.p7m) auprès d’Apple. Ce jeton permet à Intune de synchroniser les informations sur les appareils participant à Apple School Manager. Il permet également à Intune d'effectuer des chargements de profil d'inscription vers Apple et d'attribuer des appareils à ces profils. Lorsque vous vous trouvez dans le portail Apple, vous pouvez également affecter des numéros de série d’appareil à gérer.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>Étape 1. Télécharger le certificat de clé publique Intune nécessaire à la création d’un jeton Apple

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > **Ajouter**.

   ![Récupérez un jeton du programme d’inscription.](./media/apple-school-manager-set-up-ios/image01.png)

2. Dans le panneau **Jeton du programme d’inscription**, choisissez **Télécharger votre clé publique** pour télécharger et enregistrer le fichier de clé de chiffrement (.pem) localement. Le fichier .pem est utilisé pour demander un certificat de relation d'approbation à partir du portail Apple School Manager.
     ![Volet Jeton du programme d’inscription.](./media/apple-school-manager-set-up-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>Étape 2. Télécharger un jeton et affecter des appareils
1. Choisissez **Créer un jeton avec Apple School Manager** et connectez-vous à Apple School avec votre ID Apple d’entreprise. Vous pouvez utiliser cet ID Apple pour renouveler votre jeton Apple School Manager.
2. Dans le [portail Apple School Manager](https://school.apple.com), accédez à **Serveurs de gestion des appareils mobiles**, puis choisissez **Ajouter un serveur MDM** (en haut à droite).
3. Saisissez le **nom du serveur MDM**. Le nom du serveur vous permet d’identifier le serveur de gestion des appareils mobiles (MDM) uniquement. Il ne s’agit pas du nom ou de l’URL du serveur Microsoft Intune.
   ![Capture d’écran du portail Apple School Manager avec l’option Numéro de série sélectionnée](./media/apple-school-manager-set-up-ios/asm-server-assignment.png)

4. Choisissez **Télécharger un fichier...**  dans le portail Apple, recherchez le fichier .pem, puis choisissez **Enregistrer un serveur MDM** (en bas à droite).
5. Choisissez **Obtenir un jeton** puis téléchargez le fichier de jeton de serveur (.p7m) sur votre ordinateur.
6. Accédez à **Affectations d’appareil** et **Choisir appareil** par saisie manuelle des **numéros de série**, **numéro d’ordre**, ou **téléchargement de fichier CSV**.
     ![Capture d’écran du portail Apple School Manager avec l’option Numéro de série sélectionnée](./media/apple-school-manager-set-up-ios/asm-device-assignment.png)
7. Choisissez l’action **Affecter au serveur**, puis choisissez le **serveur MDM** que vous avez créé.
8. Spécifiez comment **choisir des appareils**, puis fournissez des informations et détails sur les appareils.
9. Choisissez **Attribuer au serveur** et le &lt;nom_serveur&gt; spécifié pour Microsoft Intune, puis **OK**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Étape 3. Enregistrer l’ID Apple utilisé pour créer le jeton

Dans le portail Azure d’Intune, fournissez l’ID Apple pour référence ultérieure.

![Capture d’écran : spécification de l’ID Apple utilisé pour créer le jeton du programme d’inscription et accès à ce jeton.](./media/apple-school-manager-set-up-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Étape 4. Charger le jeton
Dans la zone **Jeton Apple**, accédez au fichier du certificat (.pem), choisissez **Ouvrir**, puis **Créer**. Avec le certificat Push, Intune peut inscrire et gérer des appareils iOS en envoyant la stratégie aux appareils mobiles inscrits. Intune synchronise automatiquement les appareils Apple School Manager auprès d’Apple.

## <a name="create-an-apple-enrollment-profile"></a>Créer un profil d’inscription Apple
Maintenant que vous avez installé votre jeton, vous pouvez créer un profil d’inscription pour les appareils Apple School. Un profil d'inscription d'appareil définit les paramètres appliqués à un groupe d'appareils lors de l’inscription.

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription**.
2. Sélectionnez un jeton et choisissez **Profils**, puis **Créer un profil**.

3. Dans **Créer un profil**, entrez le **Nom** et la **Description** du profil qui serviront à des fins d’administration. Les utilisateurs ne voient pas ces détails. Vous pouvez utiliser ce champ **Nom** pour créer un groupe dynamique dans Azure Active Directory. Utilisez le nom du profil pour définir le paramètre enrollmentProfileName et attribuer des appareils avec ce profil d’inscription. En savoir plus sur les [groupes dynamiques Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices).

    ![Nom et description du profil.](./media/apple-school-manager-set-up-ios/image05.png)

4. Pour **Affinité utilisateur**, indiquez si les appareils possédant ce profil doivent être inscrits avec ou sans utilisateur attribué.
    - **Inscrire avec affinité utilisateur** : choisissez cette option pour les appareils qui appartiennent à des utilisateurs et qui veulent utiliser le Portail d’entreprise pour des services comme l’installation d’applications. Cette option permet également aux utilisateurs d’authentifier leurs appareils avec le Portail d’entreprise. Si vous utilisez ADFS, l’affinité utilisateur nécessite un [point de terminaison WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [En savoir plus](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).   Le mode iPad partagé d’Apple School Manager nécessite l’inscription de l’utilisateur sans une affinité utilisateur.

    - **Inscrire sans affinité utilisateur** : choisissez cette option pour les appareils non affiliés à un seul utilisateur, par exemple des appareils partagés, et pour les appareils qui effectuent des tâches sans accéder aux données de l’utilisateur local. Les applications telles que l’application Portail d’entreprise ne fonctionnent pas.

5. Si vous avez choisi **Inscrire avec affinité utilisateur**, vous pouvez autoriser les utilisateurs à s’authentifier avec le Portail d’entreprise au lieu de l’Assistant Configuration Apple.

    ![Authentification avec le Portail d’entreprise.](./media/apple-school-manager-set-up-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Si vous souhaitez effectuer l’une des options suivantes, définissez **S’authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration Apple** sur **Oui**.
    >    - utiliser l’authentification multifacteur
    >    - inviter les utilisateurs à changer leur mot de passe lors de leur première connexion
    >    - demander aux utilisateurs de réinitialiser leurs mots de passe arrivés à expiration lors de l’inscription
    >
    > Ces fonctionnalités ne sont pas prises en charge lors de l’authentification avec l’Assistant Configuration Apple.

6. Choisissez **Paramètres de gestion des appareils** et indiquez si vous souhaitez que les appareils utilisant ce profil soient supervisés ou non.
    Les appareils **supervisés** offrent plus d’options de gestion ; le Verrouillage d’activation est par défaut désactivé. Microsoft recommande l’utilisation du Programme d’inscription des appareils comme mécanisme d’activation du mode supervisé, en particulier pour les organisations qui déploient un grand nombre d’appareils iOS.

    Les utilisateurs sont informés du fait que leurs appareils sont supervisés de deux manières :

   - L’écran de verrouillage indique : « Cet iPhone est géré par Contoso. »
   - L’écran **Paramètres** > **Général** > **À propos de** indique : « Cet iPhone est supervisé. Contoso peut surveiller votre trafic Internet et localiser cet appareil. »

     > [!NOTE]
     > Seul Apple Configurator permet de rétablir la supervision sur un appareil inscrit sans supervision. Pour cela, l’appareil iOS doit être relié à un Mac par câble USB. Découvrez plus d’informations sur ceci dans la [documentation d’Apple Configurator](http://help.apple.com/configurator/mac/2.3).

7. Choisissez si vous souhaitez que l’inscription soit verrouillée pour les appareils possédant ce profil. **L’inscription verrouillée** désactive les paramètres iOS qui permettent de supprimer le profil de gestion du menu **Paramètres**. Une fois l’appareil inscrit, vous ne pouvez plus modifier ce paramètre sans réinitialiser l’appareil. Pour ces appareils, le Mode d’administration **Supervisé** doit avoir la valeur *Oui*. 

8. Vous pouvez autoriser plusieurs utilisateurs à se connecter à des iPad inscrits en utilisant un ID Apple géré. Pour cela, choisissez **Oui** sous  **iPad partagé** (cette option nécessite de définir **Inscription sans affinité utilisateur** et le mode **Supervisé** sur **Oui**). Les ID Apple gérés sont créés dans le portail Apple School Manager. En savoir plus sur l’option [iPad partagé](../fundamentals/education-settings-configure-ios-shared.md) et les [spécifications pour iPad partagé d’Apple](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

9. Choisissez si vous souhaitez que les appareils possédant ce profil puissent **Se synchroniser avec des ordinateurs**. Si vous choisissez **Autoriser Apple Configurator par certificat**, vous devez choisir un certificat sous **Certificats Apple Configurator**.

10. Si vous avez sélectionné **Autoriser Apple Configurator par certificat** à l’étape précédente, choisissez un certificat Apple Configurator à importer.

11. Vous pouvez spécifier pour les appareils un format d’attribution de noms qui est automatiquement appliqué lorsqu’ils s’inscrivent. Pour cela, choisissez **Oui** sous **Appliquer le modèle de nom d’appareil**. Ensuite, dans la zone **Modèle de nom d’appareil**, entrez le modèle à utiliser pour les noms à l’aide de ce profil. Vous pouvez spécifier un format de modèle incluant le type d’appareil et le numéro de série.

12. Choisissez **OK**.

13. Choisissez **Paramètres de l’Assistant Configuration** pour configurer les paramètres de profil suivants : ![Personnalisation de l’Assistant Configuration.](./media/apple-school-manager-set-up-ios/setupassistantcustom.png)


    |                 Paramètre                  |                                                                                               Description                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>Nom du service</strong>     |                                                             S’affiche quand l’utilisateur appuie sur <strong>À propos de la configuration</strong> pendant l’activation.                                                              |
    |    <strong>Numéro de téléphone du service</strong>     |                                                          S’affiche quand l’utilisateur clique sur le bouton <strong>Besoin d’aide</strong> pendant l’activation.                                                          |
    | <strong>Options de l’Assistant Configuration</strong> |                                                     Les paramètres facultatifs suivants pourront être configurés plus tard dans le menu <strong>Paramètres</strong> d’iOS.                                                      |
    |        <strong>Code secret</strong>         | Invite à saisir un code secret pendant l’activation. Exige toujours un code secret pour les appareils non sécurisés, sauf si l’accès est contrôlé d’une autre façon (par ex. en mode plein écran, qui limite l’appareil à une seule application). |
    |    <strong>Services d’emplacement</strong>    |                                                                 Si cette option est activée, l’Assistant Configuration invite à spécifier le service pendant l’activation.                                                                  |
    |         <strong>Restauration</strong>         |                                                                Si cette option est activée, l’Assistant Configuration invite à spécifier la sauvegarde iCloud pendant l’activation.                                                                 |
    |   <strong>ID Apple et iCloud</strong>   |                         Si cette option est activée, l’Assistant Configuration invite l’utilisateur à se connecter avec un ID Apple, et l’écran Applications et données autorisera la restauration de l’appareil à partir de la sauvegarde iCloud.                         |
    |  <strong>Conditions générales</strong>   |                                                   Si cette option est activée, l’Assistant Configuration invite l’utilisateur à accepter les conditions générales d’Apple pendant l’activation.                                                   |
    |        <strong>Touch ID</strong>         |                                                                 Si cette option est activée, l’Assistant Configuration invite à spécifier ce service pendant l’activation.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 Si cette option est activée, l’Assistant Configuration invite à spécifier ce service pendant l’activation.                                                                 |
    |          <strong>Zoom</strong>           |                                                                 Si cette option est activée, l’Assistant Configuration invite à spécifier ce service pendant l’activation.                                                                 |
    |          <strong>Siri</strong>           |                                                                 Si cette option est activée, l’Assistant Configuration invite à spécifier ce service pendant l’activation.                                                                 |
    |     <strong>Données de diagnostic</strong>     |                                                                 Si cette option est activée, l’Assistant Configuration invite à spécifier ce service pendant l’activation.                                                                 |


14. Choisissez **OK**.

15. Pour enregistrer le profil, choisissez **Créer**.

## <a name="connect-school-data-sync"></a>Connexion School Data Sync
(Facultatif) Apple School Manager prend en charge la synchronisation de données de liste de classe avec Azure Active Directory (AD) à l’aide de Microsoft School Data Sync (SDS). SDS ne permet de synchroniser qu’un seul jeton. Si vous configurez un autre jeton avec School Data Sync, SDS sera retiré du jeton qui l’avait précédemment. Une nouvelle connexion remplacera le jeton actuel. Effectuez les étapes suivantes pour utiliser SDS pour synchroniser les données d’école.

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription**.
2. Sélectionnez un jeton Apple School Manager, puis choisissez **School Data Sync**.
3. Sous **School Data Sync**, choisissez **Autoriser**. Ce paramètre permet à Intune de se connecter avec SDS dans Office 365.
4. Pour activer une connexion entre Apple School Manager et Azure AD, choisissez **Configurer Microsoft School Data Sync**. Découvrez-en davantage sur [la configuration de School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
5. Cliquez sur **Enregistrer** > **OK**.

## <a name="sync-managed-devices"></a>Synchroniser des appareils gérés

Une fois qu’Intune a reçu l’autorisation de gérer vos appareils Apple School Manager, synchronisez Intune avec le service Apple pour voir vos appareils gérés dans Intune.

Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste > **Appareils** > **Synchroniser**. ![Captures d’écran du nœud d’appareils du programme d'inscription et lien de synchronisation.](./media/apple-school-manager-set-up-ios/image06.png)

Pour respecter les conditions d’Apple relatives à un trafic de programme d’inscription acceptable, Intune impose les restrictions suivantes :
- Une synchronisation complète ne peut pas s’exécuter plus d’une fois tous les sept jours. Pendant une synchronisation complète, Intune actualise tous les numéros de série Apple affectés à Intune. Si une synchronisation complète est tentée dans les sept jours de la synchronisation complète précédente, Intune actualise seulement les numéros de série qui ne figurent pas déjà dans Intune.
- Toute demande de synchronisation doit se terminer dans un délai de 15 minutes. Pendant ce temps ou jusqu’au succès de la demande, le bouton **Synchroniser** est désactivé.
- Intune synchronise les nouveaux appareils et les appareils supprimés auprès d’Apple toutes les 24 heures.

>[!NOTE]
>Vous pouvez également affecter des numéros de série Apple School Manager aux profils à partir du panneau **Appareils du programme d’inscription**.

## <a name="assign-a-profile-to-devices"></a>Attribuer un profil aux appareils
Un profil d’inscription doit être affecté aux appareils Apple School Manager gérés par Intune avant leur inscription.

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste.
2. Sélectionnez **Appareils** > choisissez des appareils dans la liste > **Attribuer un profil**.
3. Sous **Attribuer un profil**, choisissez un profil pour les appareils, puis sélectionnez **Attribuer**.

## <a name="distribute-devices-to-users"></a>Distribuer des appareils aux utilisateurs

Vous avez activé la gestion et la synchronisation entre Apple et Intune, et attribué un profil permettant aux appareils Apple School de s’inscrire. Vous pouvez désormais distribuer les appareils aux utilisateurs. Quand un appareil Apple School Manager iOS est activé, il est inscrit pour être géré par Intune. Les profils ne peuvent pas être appliqués aux appareils activés en cours d'utilisation tant que l'appareil n'a pas été effacé.
