---
title: 'Tutoriel : Utiliser Apple Business Manager ou le Programme d’inscription des appareils pour inscrire des appareils iOS dans Intune'
titleSuffix: Microsoft Intune
description: Dans ce tutoriel, vous allez configurer les fonctionnalités d’inscription des appareils d’entreprise d’Apple en utilisant ABM pour inscrire des appareils iOS dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: cc950f9e60f5549a7a74c2963f33c36369d3ebd3
ms.sourcegitcommit: 5c52879f3653e22bfeba4eef65e2c86025534dab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74126173"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-ios-devices-in-intune"></a>Tutoriel : Utiliser les fonctionnalités d’inscription des appareils d’entreprise d’Apple dans Apple Business Manager (ABM) pour inscrire des appareils iOS dans Intune
Les fonctionnalités d’inscription des appareils dans Apple Business Manager simplifient l’inscription des appareils. Intune prend également en charge l’ancien portail du Programme d’inscription des appareils (DEP) d’Apple, mais nous vous encourageons à utiliser Apple Business Manager. Avec Microsoft Intune et l’inscription des appareils d’entreprise d’Apple, les appareils sont inscrits de façon automatique et sécurisée la première fois que l’utilisateur allume l’appareil. Vous pouvez par conséquent livrer des appareils à de nombreux utilisateurs sans avoir à configurer chaque appareil individuellement. 

Dans ce tutoriel, vous apprendrez à :
> [!div class="checklist"]
> * Obtenir un jeton d’inscription des appareils Apple
> * Synchroniser les appareils gérés avec Intune
> * Créer un profil d’inscription
> * Affecter un profil d’inscription à des appareils

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis
- Appareils achetés dans le cadre d’[Apple Business Manager](https://business.apple.com) ou du [Programme d’inscription des appareils d’Apple](http://deploy.apple.com)
- Définir l’[autorité de gestion des appareils mobiles](../fundamentals/mdm-authority-set.md)
- Obtenir un [certificat Push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>Obtenir un jeton d’inscription des appareils Apple
Avant d’inscrire des appareils iOS avec les fonctionnalités d’inscription des appareils d’entreprise d’Apple, vous avez besoin d’un fichier de jeton (.pem) d’inscription des appareils Apple. Ce jeton permet à Intune de synchroniser les informations sur les appareils Apple appartenant à votre entreprise. Il permet également à Intune de charger des profils d’inscription sur Apple et d’attribuer des appareils à ces profils.

Vous utilisez le portail ABM ou DEP pour créer un jeton d’inscription d’appareil. Vous utilisez également les portails pour affecter des appareils à Intune en vue de les gérer.

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > **Ajouter**.

2. Autorisez Microsoft à envoyer des informations d’utilisateur et d’appareil à Apple en sélectionnant **J’accepte**.

   ![Capture d’écran du volet Jeton de programme d’inscription dans l’espace de travail Certificats Apple pour télécharger une clé publique.](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Choisissez **Télécharger votre clé publique** pour télécharger et enregistrer le fichier de clé de chiffrement (.pem) en local. Le fichier .pem est utilisé pour demander un certificat de relation d’approbation sur le portail ABM ou DEP.

4. Choisissez **Créer un jeton pour le Programme d’inscription des appareils d’Apple** pour ouvrir le portail du programme de déploiement d’Apple, et connectez-vous avec votre ID Apple d’entreprise. Vous pouvez utiliser cet ID Apple pour renouveler votre jeton DEP.

5. Dans le portail des [programmes de déploiement](https://deploy.apple.com) d’Apple, choisissez **Get Started** (Prise en main) pour **Programme d’inscription des appareils**. Votre procédure peut être légèrement différente des étapes suivantes dans [Apple Business Manager](https://business.apple.com).

4. Dans la page **Gérer les serveurs** choisissez **Ajouter un serveur MDM**.

5. Pour **Nom du serveur MDM**, entrez *TestMDMServer*, puis choisissez **Suivant**. Le nom du serveur vous permet d’identifier le serveur de gestion des appareils mobiles (MDM) uniquement. Il ne s’agit pas du nom ou de l’URL du serveur Microsoft Intune.

6. La boîte de dialogue **Ajouter &lt;nom_serveur&gt;** s’ouvre avec le message **Charger votre clé publique**. Sélectionnez **Choisir un fichier...** pour charger le fichier .pem, puis choisissez **Suivant**.

6. Accédez à **Programmes de déploiement** > **Programme d’inscription des appareils** > **Gérer les appareils**.
7. Sous **Choisir des appareils par**, choisissez **numéro de série**. <!--ask Tiffany about this-->

8. Pour **Choisir une action**, choisissez **Affecter au serveur**, le &lt;nom_serveur&gt; spécifié pour Microsoft Intune, puis **OK**. Le portail Apple affecte les appareils spécifiés au serveur Intune pour la gestion, puis affiche **Affectation terminée**.

   Dans le portail Apple, accédez à **Programmes de déploiement** &gt; **Programme d’inscription d’appareils** &gt; **Afficher l’historique d’affectation** pour afficher la liste des appareils et leur affectation aux serveurs MDM.

9. Pour y faire référence dans le futur, dans Intune, dans le portail Azure, spécifiez l’ID Apple utilisé pour créer ce jeton.

    ![Capture d’écran : spécification de l’ID Apple utilisé pour créer le jeton du programme d’inscription et accès à ce jeton.](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. Dans la zone **Jeton Apple**, accédez au fichier du certificat (.pem), choisissez **Ouvrir**, puis **Créer**. 

11. Si vous souhaitez appliquer des balises d’étendue pour limiter les administrateurs qui ont accès à ce jeton, sélectionnez les étendues.

## <a name="create-an-apple-enrollment-profile"></a>Créer un profil d’inscription Apple
Maintenant que vous avez installé votre jeton, vous pouvez créer un profil d’inscription pour les appareils iOS appartenant à l’entreprise. Un profil d'inscription d'appareil définit les paramètres appliqués à un groupe d'appareils lors de l’inscription.

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription**.

2. Sélectionnez le jeton que vous venez d’installer et choisissez **Profils** > **Créer un profil**.

3. Sous **Créer un profil**, entrez *TestDEPProfile* pour **Nom** et *Testing DEP for iOS devices* pour **Description** . Les utilisateurs ne voient pas ces détails.

4. Choisissez **iOS** sous **Plateforme**.

5. Déterminez si vous voulez inscrire vos appareils avec ou sans **Affinité utilisateur**. L’affinité utilisateur est conçue pour les appareils qui seront utilisés par des utilisateurs particuliers. Si vos utilisateurs souhaitent utiliser le Portail d’entreprise pour des services comme l’installation d’applications, choisissez **Inscrire avec l’affinité utilisateur**. Si vos utilisateurs n’ont pas besoin du Portail d’entreprise ou si vous souhaitez provisionner l’appareil pour de nombreux utilisateurs, choisissez **Inscrire sans l’affinité utilisateur**.

6. Si vous avez choisi d’inscrire avec l’affinité utilisateur, déterminez si vous souhaitez vous authentifier avec le Portail d’entreprise ou l’Assistant Configuration d’Apple. Si vous souhaitez utiliser l’authentification multifacteur, autoriser les utilisateurs à changer de mot de passe lors de leur première connexion, ou leur demander de réinitialiser leur mots de passe expiré lors de l’inscription, choisissez **Oui** sous **Authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration d’Apple** . Si vous êtes habitué à utiliser l’authentification HTTP de base fournie par Apple via l’Assistant Configuration d’Apple, choisissez **Non**. Si vous choisissez **Oui** et que vous souhaitez que l’application Portail d’entreprise soit mise à jour automatiquement sur les appareils des utilisateurs finaux, vous devez déployer séparément Portail d’entreprise en tant qu’application requise pour ces utilisateurs par le biais du programme d’achat en volume (VPP) d’Apple.

7. Si vous avez choisi d’inscrire avec l’affinité utilisateur et de vous authentifier avec le Portail d’entreprise, déterminez si vous souhaitez installer le Portail d’entreprise avec le Programme d’achat en volume (VPP) Apple. Si vous installez le Portail d’entreprise avec un jeton VPP, votre utilisateur n’a pas à entrer d’identifiant ni de mot de passe Apple pour télécharger le Portail d’entreprise à partir de l’App store lors de l’inscription. Choisissez **Utiliser un jeton :** sous **Installer le portail d’entreprise avec VPP** pour sélectionner un jeton VPP qui a des licences gratuites disponibles du Portail d’entreprise. Si vous ne souhaitez pas utiliser VPP pour déployer le Portail d’entreprise, choisissez **Ne pas utiliser VPP** sous **Installer le portail d’entreprise avec VPP**. 

8. Si vous avez choisi d’inscrire avec l’affinité utilisateur, de vous authentifier avec le Portail d’entreprise et d’installer le Portail d’entreprise avec VPP, décidez si vous souhaitez exécuter le Portail d’entreprise en mode mono-application jusqu’à l’authentification. Ce paramètre vous permet de vous assurer que l’utilisateur n’a pas accès à d’autres applications tant qu’il n’a pas terminé l’inscription d’entreprise. Si vous souhaitez limiter l’utilisateur à ce flux tant que l’inscription n’est pas terminée, choisissez **Oui** sous **Exécuter le Portail d’entreprise en mode mono-application jusqu’à l’authentification**. 

9. Choisissez **Paramètres de gestion des appareils** et choisissez **Oui** sous **Supervisé**. Les appareils supervisés vous donnent la plupart des options de gestion pour vos appareils iOS d’entreprise.

10. Choisissez **Oui** sous **Inscription verrouillée** pour être sûr que vos utilisateurs ne peuvent pas supprimer la gestion de l’appareil d’entreprise. 

11. Choisissez une option sous **Synchroniser avec des ordinateurs** pour déterminer si les appareils iOS peuvent être synchronisés avec les ordinateurs.

12. Par défaut, Apple nomme l’appareil avec le type d’appareil (par exemple, iPad). Si vous souhaitez fournir un modèle de nom différent, choisissez **Oui** sous **Appliquer le modèle de nom d’appareil**. Entrez le nom que vous souhaitez appliquer aux appareils, où les chaînes *{{SERIAL}}* et *{{DEVICETYPE}}* sont remplacées par le numéro de série et le type de chaque appareil. Sinon, choisissez **Non** sous **Appliquer le modèle de nom d’appareil**.

13. Choisissez **OK**.

14. Choisissez **Personnalisation de l’Assistant Configuration** et entrez *Service des tutoriels* pour **Nom du service**. Cette chaîne est ce que les utilisateurs voient quand ils appuient sur **À propos de la configuration** lors de l’activation de l’appareil.

15. Sous **Téléphone du service**, entrez un numéro de téléphone. Ce numéro s’affiche quand l’utilisateur clique sur le bouton **Besoin d’aide** lors de l’activation.

16. Vous pouvez **Afficher** ou **Masquer** différents écrans lors de l’activation de l’appareil. Pour bénéficier de l’expérience d’inscription la plus fluide, définissez tous les écrans sur **Masquer**.

17. Choisissez **OK** > **Créer**.

## <a name="sync-managed-devices-to-intune"></a>Synchroniser les appareils gérés avec Intune

Après avoir configuré un jeton du programme d’inscription avec le portail DEP ABM ou ASM et affecté des appareils sur le serveur MDM, vous pouvez attendre que ces appareils soient synchronisés avec le service Intune ou lancer manuellement une synchronisation. Sans synchronisation manuelle, les appareils peuvent prendre jusqu’à 24 heures pour apparaître dans le portail Azure.

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste > **Appareils** > **Synchroniser**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Affecter un profil d’inscription à des appareils iOS

Vous devez affecter un profil de programme d’inscription aux appareils pour pouvoir les inscrire. Ces appareils sont synchronisés avec Intune à partir d’Apple et doivent se voir affectés le bon jeton de serveur MDM dans le portail ABM, ASM ou DEP.

1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez votre jeton dans la liste.
2. Sélectionnez **Appareils** > choisissez des appareils dans la liste > **Attribuer un profil**.
3. Sous **Attribuer un profil**, choisissez un profil pour les appareils > **Attribuer**.

## <a name="distribute-devices-to-users"></a>Distribuer des appareils aux utilisateurs

Vous avez configuré la gestion et la synchronisation entre Apple et Intune, et vous avez affecté un profil pour permettre l’inscription de vos appareils DEP. Vous pouvez désormais distribuer les appareils aux utilisateurs. Pour les appareils avec affinité utilisateur, chaque utilisateur doit se voir attribuer une licence Intune.

## <a name="next-steps"></a>Étapes suivantes

Vous trouverez plus d’informations sur les autres options disponibles pour l’inscription des appareils iOS.

> [!div class="nextstepaction"]
> [Article détaillé sur l’inscription DEP iOS](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
