---
title: Activer les connexions de données eSIM dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou utilisez eSIM pour obtenir l’accès à Internet et aux données à l’aide de différents forfaits de données. Dans Intune, ajoutez ou importez des codes d’activation, puis affectez-les à l’aide d’un profil de configuration. Vous pouvez également surveiller les profils eSIM et vérifier l’état des appareils compatibles avec eSIM.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 863d8d03836573a7425f2958e52a1e0331b34a10
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71080068"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>Configurer des profils de téléphonie mobile eSIM dans Intune - préversion publique

eSIM est une puce SIM intégrée qui vous permet de vous connecter à Internet par le biais d’une connexion de données cellulaires sur un appareil compatible avec eSIM, tel que la [LTE Surface Pro](https://www.microsoft.com/surface/business/surface-pro). Avec une eSIM, il n’est pas nécessaire de vous procurer une carte SIM auprès de votre opérateur mobile. En tant que voyageur dans le monde entier, vous pouvez aussi basculer entre divers opérateurs mobiles et forfaits de données pour rester toujours connecté.

Par exemple, imaginez que vous avez un forfait de données cellulaires pour le travail, et un autre forfait avec un autre opérateur mobile pour votre usage personnel. En déplacement, vous pouvez accéder à Internet en recherchant les opérateurs de téléphonie mobile avec des forfaits de données dans la région.

Dans Intune, vous pouvez importer des codes d’activation à usage unique fournis par votre opérateur mobile. Pour configurer des forfaits de données cellulaires sur le module eSIM, déployez ces codes d’activation sur vos appareils prenant en charge eSIM. Quand Intune installe le code d’activation, le module matériel eSIM utilise les données dans le code d’activation pour contacter l’opérateur mobile. Une fois terminé, le profil eSIM est téléchargé sur l’appareil et configuré pour l’activation de téléphonie mobile.

Pour déployer eSIM sur vos appareils à l’aide d’Intune, les éléments suivants sont nécessaires :

- Des **appareils compatibles avec les cartes eSIM**, comme la Surface LTE : Vérifiez [si votre appareil prend en charge les cartes eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). Vous pouvez aussi consulter une liste de [certains appareils compatibles avec eSIM](#esim-capable-devices) (dans cet article)
- **PC avec Mise à jour Windows 10 Fall Creators** (1709 ou version ultérieure) inscrit auprès d’Intune et géré par MDM
- **Codes d’activation** fournis par votre opérateur mobile. Ces codes d’activation à usage unique sont ajoutés à Intune et déployés sur vos appareils compatibles avec eSIM. Contactez votre opérateur mobile pour acquérir des codes d’activation eSIM

## <a name="deploy-esim-to-devices---overview"></a>Déployer eSIM sur des appareils - Vue d’ensemble

Pour déployer eSIM sur des appareils, un administrateur effectue les tâches suivantes :

1. Importation de codes d’activation fournis par votre opérateur mobile
2. Création d’un groupe d’appareils Azure Active Directory (Azure AD) qui comprend vos appareils compatibles avec eSIM
3. Affectation du groupe Azure AD à votre pool d’abonnements importé
4. Surveillance du déploiement

Cet article explique comment effectuer ces étapes.

## <a name="esim-capable-devices"></a>Appareils compatibles avec eSIM

Les appareils suivants ont été annoncés comme compatibles avec eSIM, ou sont aujourd’hui disponibles sur le marché. Vérifiez également si [votre appareil prend en charge eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre Folio 13
- Lenovo Yoga C630

## <a name="step-1-add-cellular-activation-codes"></a>Étape 1 : Ajouter des codes d’activation de téléphonie mobile

Les codes d’activation de téléphonie mobile sont fournis par votre opérateur mobile dans un fichier de valeurs séparées par des virgules (csv). Une fois en possession de ce fichier, ajoutez-le à Intune en effectuant les étapes suivantes :

1. Connectez-vous au [portail Azure](https://portal.azure.com/).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Profils cellulaires eSIM** > **Ajouter**.
4. Sélectionnez le fichier CSV contenant vos codes d’activation.
5. Cliquez sur **OK** pour enregistrer vos modifications.

### <a name="csv-file-requirements"></a>Exigences relatives au fichier CSV

Lors de l’utilisation du fichier csv contenant les codes d’activation, veillez à ce que votre opérateur mobile ou vous-même remplissiez les conditions suivantes :

- Le fichier doit être au format csv (nom_fichier.csv)
- La structure de fichiers doit respecter un format strict. Sinon, l’importation échoue. Intune vérifie le fichier lors de l’importation, et celle-ci échoue si des erreurs sont détectées
- Les codes d’activation ne sont utilisés qu’une seule fois. Nous vous déconseillons d’importer des codes d’activation que vous avez déjà importés auparavant, car cela peut provoquer des problèmes lors du déploiement sur le même appareil ou sur un appareil différent
- Chaque fichier doit être propre à un seul opérateur mobile, et tous les codes d’activation doivent être propres à un même plan de facturation. Intune distribue aléatoirement les codes d’activation aux appareils ciblés. Il n’y a aucune garantie quant à l’appareil qui obtiendra un code d’activation spécifique
- Vous pouvez importer un maximum de 1000 codes d’activation dans un fichier csv

### <a name="csv-file-example"></a>Exemple de fichier CSV

1. La première ligne et la première cellule du fichier csv correspondent à l’URL du service d’activation eSIM de l’opérateur mobile, appelé SM-DP+ (serveur Subscription Manager Data Preparation). L’URL doit être un nom de domaine complet (FQDN) sans virgule.
2. La deuxième ligne et toutes les suivantes correspondent à des codes d’activation à usage unique qui incluent deux valeurs :

    1. La première colonne correspond à l’ICCID unique (l’identificateur de la puce SIM)
    2. La deuxième colonne correspond à l’ID de mise en correspondance, avec uniquement une virgule de séparation (pas de virgule à la fin) Consultez l'exemple suivant :

        ![Exemple de fichier csv de code d’activation d’opérateur mobile](./media/esim-device-configuration/url-activation-code-examples.png)

3. Le nom du fichier csv devient le nom du pool d’abonnements cellulaires dans le portail Azure. Dans l’image précédente, le nom de fichier est `UnlimitedDataSkynet.csv`. Par conséquent, Intune nomme le pool d’abonnements `UnlimitedDataSkynet.csv` :

    ![Le pool d’abonnements cellulaires porte le nom de l’exemple de fichier csv de code d’activation](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>Étape 2 : Créer un groupe d’appareils Azure AD

Créez un groupe d’appareils qui comprend les appareils compatibles avec eSIM. [Ajouter des groupes](groups-add.md) répertorie les étapes.

> [!NOTE]
> - Seuls les appareils sont ciblés ; les utilisateurs ne sont pas ciblés.
> - Nous vous recommandons de créer un groupe d’appareils Azure AD statique qui comprend vos appareils eSIM. L’utilisation d’un groupe permet de confirmer que vous ciblez uniquement des appareils eSIM.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>Étape 3 : Affecter des codes d’activation eSIM aux appareils

Affectez le profil au groupe Azure AD qui comprend vos appareils eSIM.

1. Dans le [Portail Azure](https://portal.azure.com/), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Sélectionnez **configuration de l’appareil** > **eSIM cellulaire** > **profils**.
3. Dans la liste des profils, sélectionnez le pool d’abonnements cellulaires eSIM que vous souhaitez affecter, puis sélectionnez **Affectations**.
4. Choisissez d’**Inclure** des groupes ou d’**Exclure** des groupes, puis sélectionnez les groupes.

    ![Inclure le groupe d’appareils pour attribuer le profil](./media/esim-device-configuration/include-exclude-groups.png)

5. Quand vous sélectionnez vos groupes, vous choisissez un groupe Azure AD. Pour sélectionner plusieurs groupes, appuyez sur la touche **Ctrl**, puis sélectionnez les groupes.
6. Une fois terminé, **enregistrez** vos changements.

Les codes d’activation eSIM ne sont utilisés qu’une seule fois. Une fois qu’Intune a installé un code d’activation sur un appareil, le module eSIM contacte l’opérateur mobile pour télécharger le profil de téléphonie mobile. Ce contact termine l’inscription de l’appareil auprès du réseau de l’opérateur mobile.

## <a name="step-4-monitor-deployment"></a>Étape 4 : Superviser le déploiement

### <a name="review-the-deployment-status"></a>Consulter l’état du déploiement

Une fois que vous avez affecté le profil, vous pouvez surveiller l’état du déploiement d’un pool d’abonnements.

1. Connectez-vous au [portail Azure](https://portal.azure.com/).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Profils cellulaires eSIM**. Tous vos pools d’abonnements cellulaires eSIM existants sont répertoriés.
4. Sélectionnez un abonnement et consultez l’**État du déploiement**.

### <a name="check-the-profile-status"></a>Vérifier l’état du profil
Une fois le profil d’appareil créé, Intune fournit des graphiques. Ces graphiques affichent l’état d’un profil, à savoir s’il a été attribué correctement à des appareils ou si le profil indique un conflit.

1. Sélectionnez **Configuration de l’appareil** > **Profils cellulaires eSIM** > Sélectionner un abonnement existant.
2. Sous l’onglet **Vue d’ensemble**, le graphique supérieur affiche le nombre d’appareils affectés au déploiement de pool d’abonnements cellulaires eSIM spécifique.

    Il indique également le nombre d’appareils pour d’autres plateformes ayant le même profil d’appareil.

    Intune affiche l’état de remise et d’installation pour le code d’activation ciblant des appareils.

    - **Appareil non synchronisé** : l’appareil ciblé n’a pas contacté Intune depuis la création de la stratégie de déploiement eSIM
    - **Activation en attente** : état temporaire pendant lequel Intune installe activement le code d’activation sur l’appareil
    - **Actif** : installation du code d’activation réussie
    - **Échec de l’activation** : l’installation du code d’activation a échoué ; consultez le guide de dépannage.

#### <a name="view-the-detailed-device-status"></a>Afficher l’état détaillé de l’appareil

Vous pouvez surveiller et afficher une liste détaillée des appareils dans État de l’appareil.**

1. Sélectionnez **Configuration de l’appareil** > **Profils cellulaires eSIM** > Sélectionner un abonnement existant.
2. Sélectionnez **État de l’appareil**. Intune affiche des détails supplémentaires sur l’appareil :

    - **Nom de l’appareil** : nom de l’appareil ciblé
    - **Utilisateur** : utilisateur de l’appareil inscrit
    - **ICCID** : code unique fourni par l’opérateur de téléphonie dans le code d’activation installé sur l’appareil
    - **État d’activation** : état de mise à disposition et d’installation Intune du code d’activation sur l’appareil
    - **État du réseau mobile** : état fourni par l’opérateur de téléphonie. Contactez l’opérateur mobile pour résoudre les problèmes.
    - **Dernier archivage** : date de dernière communication de l’appareil avec Intune

### <a name="monitor-esim-profile-details-on-the-actual-device"></a>Surveiller les détails du profil eSIM sur l’appareil

1. Sur votre appareil, ouvrez **Paramètres** > accédez à **Réseau & Internet**.
2. Sélectionnez **Cellulaire** > **Gérer les profils eSIM**.
3. Les profils eSIM sont répertoriés :

    ![Visualisez les profils eSIM dans les paramètres de votre appareil](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>Supprimer le profil d’eSIM de l’appareil

Quand vous supprimez l’appareil du groupe Azure AD, le profil eSIM est également supprimé. Veillez à :

1. Confirmer que vous utilisez le groupe Azure AD d’appareils eSIM.
2. Accéder au groupe Azure AD et supprimer l’appareil du groupe.
3. Quand l’appareil supprimé contacte Intune, la stratégie mise à jour est évaluée et le profil eSIM est supprimé.

Le profil eSIM est également supprimé quand l’appareil est [mis hors service](devices-wipe.md#retire) ou désinscrit par l’utilisateur, ou quand [l’action à distance Réinitialiser l’appareil](devices-wipe.md#wipe) est exécutée sur l’appareil.

> [!NOTE]
> La suppression du profil peut ne pas arrêter la facturation. Contactez votre opérateur mobile pour vérifier l’état de la facturation pour votre appareil.

## <a name="best-practices--troubleshooting"></a>Bonnes pratiques et dépannage

- Veillez à ce que votre fichier csv soit correctement mis en forme. Vérifiez que le fichier ne contient pas de codes en double, ne contient pas plusieurs opérateurs de téléphonie mobile, ou ne contient pas différents forfaits de données. N’oubliez pas que chaque fichier doit être unique à un opérateur mobile et à un forfait de données cellulaires.
- Créez un groupe d’appareils Azure AD statique qui comprend uniquement les appareils eSIM ciblés.
- En cas de problème avec l’état du déploiement, vérifiez les points suivants :
  - **Format de fichier incorrect** : Voir **Étape 1 : Ajouter des codes d’activation de téléphonie mobile** (dans cet article) pour savoir comment formater correctement votre fichier.
  - **Échec de l’activation de téléphonie mobile, contactez l’opérateur de téléphonie** : le code d’activation n’est peut-être pas activé sur son réseau. Il se peut aussi que le téléchargement du profil et l’activation de téléphonie mobile aient échoué.

## <a name="next-steps"></a>Étapes suivantes
[Configurer un profil d’appareil](device-profiles.md)
