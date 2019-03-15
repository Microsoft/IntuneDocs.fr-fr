---
title: 'Tutoriel : Utiliser le Programme d’inscription des appareils pour inscrire des appareils iOS dans Intune'
titleSuffix: Microsoft Intune
description: Dans ce tutoriel, vous allez configurer le Programme d’inscription des appareils (DEP, Device Enrollment Program) d’Apple pour inscrire des appareils iOS dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/30/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 88fe825b75e7717740e5a5ca4af4c52e9bb21768
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57400396"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>Tutoriel : Utiliser le Programme d’inscription des appareils pour inscrire des appareils iOS dans Intune
Le Programme d’inscription des appareils d’Apple simplifie l’inscription des appareils. Avec Microsoft Intune et DEP, les appareils sont inscrits automatiquement la première fois que l’utilisateur allume l’appareil. Vous pouvez par conséquent livrer des appareils à de nombreux utilisateurs sans avoir à configurer chaque appareil individuellement. 

Dans ce tutoriel, vous apprendrez à :
> [!div class="checklist"]
> * Obtenir un jeton DEP Apple
> * Créer un groupe d’appareils Autopilot
> * Créer un profil de déploiement Autopilot
> * Affecter le profil de déploiement Autopilot au groupe d’appareils
> * Distribuer des appareils Windows aux utilisateurs

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis
- Appareils achetés dans le cadre du [Programme d’inscription des appareils d’Apple](http://deploy.apple.com)
- Définir l’[autorité de gestion des appareils mobiles](mdm-authority-set.md)
- Obtenir un [certificat Push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Obtenir un jeton DEP Apple
Avant d’inscrire des appareils iOS avec DEP, vous avez besoin d’un fichier (.pem) de jeton DEP d’Apple. Ce jeton permet à Intune de synchroniser les informations sur les appareils DEP appartenant à votre entreprise. Il permet également à Intune de charger des profils d’inscription sur Apple et d’attribuer des appareils à ces profils.

Vous utilisez le portail DEP Apple pour créer un jeton DEP. Vous utilisez également le portail DEP pour affecter des appareils à Intune à des fins de gestion.

1. Dans [Intune, sur le Portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > **Ajouter**.

2. Autorisez Microsoft à envoyer des informations d’utilisateur et d’appareil à Apple en sélectionnant **J’accepte**.

   ![Capture d’écran du volet Jeton de programme d’inscription dans l’espace de travail Certificats Apple pour télécharger une clé publique.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Choisissez **Télécharger votre clé publique** pour télécharger et enregistrer le fichier de clé de chiffrement (.pem) en local. Le fichier .pem est utilisé pour demander un certificat de relation d'approbation à partir du portail du programme d'inscription d'appareils d'Apple.

4. Choisissez **Créer un jeton pour le Programme d’inscription des appareils d’Apple** pour ouvrir le portail du programme de déploiement d’Apple, et connectez-vous avec votre ID Apple d’entreprise. Vous pouvez utiliser cet ID Apple pour renouveler votre jeton DEP.

5.  Dans le portail des [programmes de déploiement](https://deploy.apple.com) d’Apple, choisissez **Get Started** (Prise en main) pour **Programme d’inscription des appareils**.

4. Dans la page **Gérer les serveurs** choisissez **Ajouter un serveur MDM**.

5. Pour **Nom du serveur MDM**, entrez *TestMDMServer*, puis choisissez **Suivant**. Le nom du serveur vous permet d’identifier le serveur de gestion des appareils mobiles (MDM) uniquement. Il ne s’agit pas du nom ou de l’URL du serveur Microsoft Intune.

6. La boîte de dialogue **Ajouter &lt;nom_serveur&gt;** s’ouvre avec le message **Charger votre clé publique**. Choisissez **Choisir un fichier** pour charger le fichier .pem, puis choisissez **Suivant**.

6. Accédez à **Programmes de déploiement** > **Programme d’inscription des appareils** > **Gérer les appareils**.
7. Sous **Choisir des appareils par**, choisissez **numéro de série**. <!--ask Tiffany about this-->

8. Pour **Choisir une action**, choisissez **Affecter au serveur**, le &lt;nom_serveur&gt; spécifié pour Microsoft Intune, puis **OK**. Le portail Apple affecte les appareils spécifiés au serveur Intune pour la gestion, puis affiche **Affectation terminée**.

   Dans le portail Apple, accédez à **Programmes de déploiement** &gt; **Programme d’inscription d’appareils** &gt; **Afficher l’historique d’affectation** pour afficher la liste des appareils et leur affectation aux serveurs MDM.

9. Pour y faire référence dans le futur, dans Intune, dans le portail Azure, spécifiez l’ID Apple utilisé pour créer ce jeton.

    ![Capture d’écran : spécification de l’ID Apple utilisé pour créer le jeton du programme d’inscription et accès à ce jeton.](./media/device-enrollment-program-enroll-ios/image03.png)

10. Dans la zone **Jeton Apple**, accédez au fichier du certificat (.pem), choisissez **Ouvrir**, puis **Créer**. 

## <a name="create-an-apple-enrollment-profile"></a>Créer un profil d’inscription Apple
Maintenant que vous avez installé votre jeton, vous pouvez créer un profil d’inscription pour les appareils DEP. Un profil d'inscription d'appareil définit les paramètres appliqués à un groupe d'appareils lors de l’inscription.

1. Dans Intune, sur le Portail Azure, choisissez **Inscription des appareil** > **Inscription Apple** > **Jetons du programme d’inscription**.

2. Sélectionnez le jeton que vous venez d’installer et choisissez **Profils** > **Créer un profil**.

3. Sous **Créer un profil**, entrez *TestDEPProfile* pour **Nom** et *Testing DEP for iOS devices* pour **Description** . Les utilisateurs ne voient pas ces détails.

4. Pour **Affinité utilisateur**, choisissez **Inscrire avec l’affinité utilisateur**. Cette option est destinée aux appareils appartenant à des utilisateurs qui doivent utiliser le Portail d’entreprise pour des services comme l’installation d’applications.

5. Choisissez **Non** sous **Authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration d’Apple**.

6. Choisissez **Paramètres de gestion des appareils** et choisissez **Non** sous **Supervisé**. Les appareils supervisés vous offrent davantage d’options de gestion, mais vous ne les utilisez pas dans le cadre de ce tutoriel.

7. Choisissez **OK**.

8. Choisissez **Personnalisation de l’Assistant Configuration** et entrez *Service des tutoriels* pour **Nom du service**. Cette chaîne est ce que les utilisateurs voient quand ils appuient sur **À propos de la configuration** lors de l’activation de l’appareil.

9. Sous **Téléphone du service**, entrez un numéro de téléphone. Ce numéro s’affiche quand l’utilisateur clique sur le bouton **Besoin d’aide** lors de l’activation.

10. Vous pouvez **Afficher** ou **Masquer** différents écrans lors de l’activation de l’appareil. Pour les besoins de ce tutoriel, définissez **Code secret** sur **Afficher** et tous les autres sur **Masquer**.

11. Choisissez **OK** > **Créer**.

## <a name="sync-managed-devices"></a>Synchroniser des appareils gérés

Vous pouvez désormais voir les appareils qui sont affectés à ce jeton.

1. Dans Intune, dans le portail Azure, choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez un jeton dans la liste > **Appareils** > **Synchroniser**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Affecter un profil d’inscription à des appareils iOS

Vous devez affecter un profil de programme d’inscription aux appareils pour pouvoir les inscrire.

1. Dans Intune, dans le portail Azure, choisissez **Inscription des appareils** > **Inscription Apple** > **Jetons du programme d’inscription** > choisissez votre jeton dans la liste.
2. Sélectionnez **Appareils** > choisissez des appareils dans la liste > **Attribuer un profil**.
3. Sous **Attribuer un profil**, choisissez un profil pour les appareils > **Attribuer**.

## <a name="distribute-devices-to-users"></a>Distribuer des appareils aux utilisateurs

Vous avez configuré la gestion et la synchronisation entre Apple et Intune, et vous avez affecté un profil pour permettre l’inscription de vos appareils DEP. Vous pouvez désormais distribuer les appareils aux utilisateurs. Pour les appareils avec affinité utilisateur, chaque utilisateur doit se voir attribuer une licence Intune.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Si vous ne voulez plus utiliser les appareils Autopilot, vous pouvez les supprimer.

- Si les appareils sont inscrits dans Intune, vous devez d’abord [les supprimer dans le portail Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>Étapes suivantes

Vous trouverez plus d’informations sur les autres options disponibles pour l’inscription des appareils iOS.

> [!div class="nextstepaction"]
> [Article détaillé sur l’inscription DEP iOS](device-enrollment-program-enroll-ios.md)
