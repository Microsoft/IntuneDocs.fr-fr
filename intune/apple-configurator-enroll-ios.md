---
title: Inscription d’appareils iOS - Apple Configurator - Assistant Configuration
titleSuffix: Microsoft Intune
description: Découvrez comment utiliser Apple Configurator pour inscrire des appareils iOS d’entreprise à l’aide de l’Assistant Configuration.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d91e92b561bbf7b574e0d8271374c0d8c6bd4a64
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230395"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>Configurer l’inscription des appareils iOS avec Apple Configurator

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune prend en charge l’inscription d’appareils iOS à l’aide d’[Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) s’exécutant sur un ordinateur Mac. L’inscription avec Apple Configurator requiert que vous connectiez par USB chaque appareil iOS à un ordinateur Mac pour configurer l’inscription d’entreprise. Vous pouvez inscrire des appareils sur Intune avec Apple Configurator de deux manières :
- **Inscription de l’Assistant Configuration** : réinitialise l’appareil et le prépare à l’inscription avec l’Assistant Configuration.
- **Inscription directe** : ne réinitialise pas l’appareil et l’inscrit avec les paramètres iOS. Cette méthode prend seulement en charge les appareils **sans affinité utilisateur**.

Vous ne pouvez pas utiliser les méthodes d’inscription Apple Configurator avec le [gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Prérequis

- Accès physique aux appareils iOS
- [Définir l’autorité MDM](mdm-authority-set.md)
- [Un certificat Push MDM Apple](apple-mdm-push-certificate-get.md)
- Numéros de série des appareils (inscription Assistant Configuration uniquement)
- Câbles de connexion USB
- Ordinateur macOS exécutant [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Créer un profil Apple Configurator pour les appareils

Un profil d’inscription d’appareil définit les paramètres appliqués durant l’inscription. Ces paramètres ne sont appliqués qu’une seule fois. Suivez ces étapes pour créer un profil d’inscription en vue d’inscrire des appareils iOS avec Apple Configurator.

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Apple Configurator**  >  **Profils** > **Créer**.

    ![Créer un profil pour Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. Dans **Créer un profil d’inscription**, tapez le **Nom** et la **Description** du profil qui serviront à des fins d’administration. Les utilisateurs ne voient pas ces détails. Vous pouvez utiliser ce champ Nom pour créer un groupe dynamique dans Azure Active Directory. Utilisez le nom du profil pour définir le paramètre enrollmentProfileName et affecter des appareils avec ce profil d’inscription. Découvrez plus en détail les groupes dynamiques Azure Active Directory.

    ![Capture d’écran de l’écran de création d’un profil avec l’option Inscrire avec l’affinité utilisateur sélectionnée](./media/apple-configurator-profile-create.png)

3. Pour **Affinité utilisateur**, indiquez si les appareils possédant ce profil doivent être inscrits avec ou sans utilisateur attribué.

    - **Inscrire avec affinité utilisateur** : choisissez cette option pour les appareils qui appartiennent à des utilisateurs et qui veulent utiliser le Portail d’entreprise pour des services comme l’installation d’applications. L’appareil doit être affilié à un utilisateur avec l’Assistant Configuration. Il pourra alors accéder aux données et à la messagerie de l’entreprise. Prise en charge seulement pour l’inscription de l’Assistant Configuration. L’affinité utilisateur nécessite un [point de terminaison WS-Trust 1.3 Username/Mixed](https://technet.microsoft.com/library/adfs2-help-endpoints). [En savoir plus](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Inscrire sans affinité utilisateur** : choisissez cette option pour les appareils non affiliés à un seul utilisateur, qui effectuent des tâches sans accéder aux données de l’utilisateur local. Les applications qui nécessitent l’affiliation d’un utilisateur (y compris l’application Portail d’entreprise utilisée pour l’installation des applications métier) ne fonctionneront pas. Obligatoire pour l’inscription directe.

4. Si vous avez choisi **Inscrire avec affinité utilisateur**, vous avez la possibilité d’autoriser les utilisateurs à s’authentifier avec le Portail d’entreprise au lieu de l’Assistant Configuration Apple.

    > [!NOTE]
    > Si vous souhaitez effectuer l’une des options suivantes, définissez **S’authentifier avec le portail d’entreprise au lieu de l’Assistant Configuration Apple** sur **Oui**.
    >    - utiliser l’authentification multifacteur
    >    - inviter les utilisateurs à changer leur mot de passe lors de leur première connexion
    >    - demander aux utilisateurs de réinitialiser leurs mots de passe arrivés à expiration lors de l’inscription
    >
    > Ces fonctionnalités ne sont pas prises en charge lors de l’authentification avec l’Assistant Configuration Apple.


6. Sélectionnez **Créer** pour enregistrer le profil.

## <a name="setup-assistant-enrollment"></a>Inscription Assistant Configuration

### <a name="add-apple-configurator-serial-numbers"></a>Ajouter des numéros de série Apple Configurator

1. Créez une liste de valeurs, séparées par des virgules (.csv) avec deux colonnes, sans en-tête. Ajoutez le numéro de série dans la colonne de gauche, et les détails dans celle de droite. Le maximum actuel pour la liste est de 5 000 lignes. Dans un éditeur de texte, la liste .csv ressemble à ceci :

    F7TLWCLBX196,détails de l’appareil</br>
    DLXQPCWVGHMJ,détails de l’appareil

   Découvrez [comment trouver le numéro de série d’un appareil iOS](https://support.apple.com/HT204073).
2. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Apple** > **Apple Configurator**  >  **Appareils** > **Ajouter**.

5. Sélectionnez un **Profil d’inscription** à appliquer aux numéros de série que vous importez. Si vous souhaitez que le nouveau numéro de série remplace toutes les informations existantes, choisissez **Remplacer les informations des identificateurs existants**.
6. Sous **Importer des appareils**, accédez au fichier CSV de numéros de série, puis sélectionnez **Ajouter**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Réaffecter un profil à des numéros de série d’appareils

Il est possible d’attribuer un profil d’inscription en important des numéros de série iOS dans le cadre de l’inscription Apple Configurator. L’attribution de profils peut également se faire à deux endroits différents du Portail Azure :
- **Appareils Apple Configurator**
- **Profils AC**

#### <a name="assign-from-apple-configurator-devices"></a>Affecter un profil à partir d’appareils Apple Configurator
1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Apple** > **Apple Configurator** > **Appareils** > choisissez les numéros de série > **Attribuer le profil**.
2. Sous **Attribuer un profil**, choisissez le **Nouveau profil** à attribuer, puis **Attribuer**.

#### <a name="assign-from-profiles"></a>Affecter à partir de profils
1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Apple** > **Apple Configurator**  >  **Profils** > choisissez un profil.
2. Dans le profil, choisissez **Appareils affectés**, puis **Affecter**.
3. Appliquez un filtre pour trouver les numéros de série des appareils à affecter au profil, sélectionnez les appareils, puis choisissez **Affecter**.

### <a name="export-the-profile"></a>Exporter le profil
Une fois que vous avez créé le profil et affecté des numéros de série, vous devez exporter le profil d’Intune comme URL. Ensuite, importez-le dans Apple Configurator sur un Mac pour le déployer sur des appareils.

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Apple** > **Apple Configurator**  >  **Profils** > choisissez le profil à exporter.
2. Dans le profil, sélectionnez **Exporter le profil**.
3. Copiez **l’URL du profil**. Vous pourrez l’ajouter dans Apple Configurator pour définir le profil Intune utilisé par les appareils iOS.

   Ensuite, importez ce profil dans Apple Configurator au cours de la procédure suivante pour définir le profil Intune utilisé par les appareils iOS.

### <a name="enroll-devices-with-setup-assistant"></a>Inscrire des appareils avec l’Assistant Configuration

1. Sur un ordinateur Mac, ouvrez **Apple Configurator 2**. Dans la barre de menus, choisissez **Apple Configurator 2**, puis cliquez sur **Préférences**.
    > [!WARNING]
    > Les appareils sont réinitialisés aux paramètres d’usine durant le processus d’inscription. En guise de bonne pratique, vous devez réinitialiser l’appareil et l’allumer. Les appareils doivent afficher l’écran **Hello** quand vous les connectez.

2. Dans le volet **Préférences**, sélectionnez **Serveurs** et cliquez sur le symbole plus (« + ») pour lancer l’Assistant de serveur MDM. Choisissez **Suivant**.
3. Entrez le **Nom d’hôte ou l’URL** et l’**URL d’inscription** du serveur MDM sous Inscription Assistant Configuration pour les appareils iOS avec Microsoft Intune. Pour l’URL d’inscription, entrez l’URL du profil d’inscription exporté depuis Intune. Choisissez **Suivant**.  
    Vous pouvez ignorer sans risque un avertissement indiquant « L’URL du serveur n’est pas vérifiée ». Pour continuer, cliquez sur **Suivant** jusqu’à ce que l’Assistant soit terminé.
4.  Connectez les appareils mobiles iOS à l’ordinateur Mac à l’aide d’un adaptateur USB.
5.  Sélectionnez les appareils iOS que vous voulez gérer, puis choisissez **Préparer**. Dans le volet **Préparer l’appareil iOS**, sélectionnez **Manuel**, puis **Suivant**.
6. Dans le panneau **Enroll in MDM Server** (Inscription dans un serveur MDM), sélectionnez le nom du serveur que vous avez créé, puis cliquez sur **Next** (Suivant).
7. Dans le volet **Supervise Devices** (Surveiller les appareils), sélectionnez le niveau de surveillance, puis cliquez sur **Next** (Suivant).
8. Dans le panneau **Create an Organization** (Créer une organisation), choisissez **l’organisation** ou créez-en une, puis cliquez sur **Next** (Suivant).
9. Dans le panneau **Configure iOS Setup Assistant** (Configurer l’Assistant Configuration iOS), choisissez les étapes à présenter à l’utilisateur, puis sélectionnez **Prepare** (Préparer). Si vous y êtes invité, authentifiez-vous pour mettre à jour les paramètres d’approbation.  
10. Une fois la préparation de l’appareil iOS terminée, déconnectez le câble USB.  

### <a name="distribute-devices"></a>Distribuer des appareils
Les appareils sont désormais prêts pour l'inscription d'entreprise. Éteignez les appareils et distribuez-les aux utilisateurs. Quand les utilisateurs allument leur appareil, l’Assistant Configuration démarre.

Après avoir reçu leur appareil, les utilisateurs doivent exécuter l’Assistant Configuration. Des appareils configurés avec une affinité utilisateur peuvent installer et exécuter l’application Portail d’entreprise pour télécharger des applications et gérer des appareils.

## <a name="direct-enrollment"></a>Inscription directe
Quand vous inscrivez directement des appareils iOS avec Apple Configurator, vous pouvez inscrire un appareil sans obtenir son numéro de série. Vous pouvez également nommer l’appareil à des fins d’identification avant qu’Intune capture son nom lors de l’inscription. L’application Portail d’entreprise n’est pas prise en charge pour les appareils inscrits directement. Cette méthode ne réinitialise pas l’appareil.

Vous ne pouvez pas installer d’applications nécessitant l’affiliation de l’utilisateur (notamment l’application Portail d’entreprise utilisée pour installer des applications métier).

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exporter le profil en tant que fichier .mobileconfig sur les appareils iOS

1. Dans [Intune](https://aka.ms/intuneportal), sélectionnez **Inscription des appareils** > **Inscription Apple** > **Apple Configurator**  >  **Profils** > choisissez le profil à exporter > **Exporter le profil**.
2. Sous **Inscription directe**, choisissez **Télécharger le profil** et enregistrez le fichier. Un fichier de profil d’inscription n’est valide que pendant deux semaines. Au bout de cette période, vous devez le recréer.
3. Transférez le fichier sur un ordinateur Mac exécutant [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) pour l’envoyer (push) directement comme profil de gestion sur les appareils iOS.
4. Préparez l’appareil avec Apple Configurator en suivant les étapes ci-dessous :
    1. Sur un ordinateur Mac, ouvrez Apple Configurator 2.0.
    2. Connectez l’appareil iOS à l’ordinateur Mac avec un câble USB. Fermez Photos, iTunes et toutes les autres applications qui s’ouvrent quand l’appareil est détecté.
    3. Dans Apple Configurator, choisissez l’appareil iOS connecté, puis cliquez sur le bouton **Ajouter**. Les options qui peuvent être ajoutées à l’appareil s’affichent dans la liste déroulante. Choisissez **Profils**.

        ![Capture d’écran Exporter le profil pour l’inscription de l’Assistant Installation avec l’URL du profil mise en surbrillance](./media/ios-apple-configurator-add-profile.png)

    4. Utilisez le sélecteur de fichiers pour sélectionner le fichier .mobileconfig que vous avez exporté à partir d’Intune, puis choisissez **Ajouter**. Le profil est ajouté à l’appareil. Si l’appareil est Non supervisé, l’installation doit être acceptée sur l’appareil.
5. Utilisez la procédure suivante pour installer le profil sur l’appareil iOS. L’appareil doit avoir terminé l’Assistant Configuration et être prêt à l’emploi. Si l’inscription entraîne des déploiements d’applications, un identifiant Apple doit être configuré sur l’appareil, car le déploiement d’applications nécessite que vous soyez connecté à l’App Store avec un identifiant Apple.
    1. Déverrouillez l’appareil iOS.
    2. Dans la boîte de dialogue **Install profile** (Installer le profil) de **Management profile** (Gestion du profil), choisissez **Install** (Installer).
    3. Spécifiez le code secret de l’appareil ou l’Apple ID, si nécessaire.
    4. Acceptez l’avertissement (**Warning**), puis choisissez **Install** (Installer).
    5. Acceptez l’avertissement distant (**Remote Warning**), puis choisissez **Trust** (Approuver).
    6. Quand la boîte de dialogue **Profile Installed** (Profil installé) confirme que le profil est installé, cliquez sur **Done** (Terminé).

6. Sur l’appareil iOS, ouvrez **Settings** (Réglages) et accédez à **General (Général)** > **Device Management (Gestion des appareils)** > **Management Profile (Profil de gestion)**. Assurez-vous que l’installation du profil est répertoriée, puis vérifiez les restrictions de stratégie iOS et les applications installées. L’affichage des applications et des restrictions de stratégie sur l’appareil peut prendre jusqu’à dix minutes.

7. Distribuez des appareils. L’appareil iOS est maintenant inscrit et géré dans Intune.





