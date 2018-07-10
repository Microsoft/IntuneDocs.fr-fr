---
title: Utiliser des certificats PKCS avec Microsoft Intune - Azure | Micrososft Docs
description: Découvrez comment ajouter ou créer des certificats PKCS (Public Key Cryptography Standards) avec Microsoft Intune, notamment comment exporter un certificat racine, configurer le modèle de certificat, télécharger et installer Microsoft Intune Certificate Connector (NDES), créer un profil de configuration d’appareil, créer un profil de certificat PKCS dans Azure et votre autorité de certification.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b3bfe76173eff76a3175952bef5c6e23ad5e429
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271539"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurer et utiliser des certificats PKCS avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les certificats servent à authentifier et à sécuriser l’accès à vos ressources d’entreprise, par exemple un réseau privé virtuel ou votre réseau Wi-Fi. Cet article explique comment exporter un certificat PKCS, puis l’ajouter à un profil Intune. 

## <a name="requirements"></a>Configuration requise

Pour utiliser des certificats PKCS avec Intune, veillez à disposer de l’infrastructure suivante :

- **Domaine Active Directory** : tous les serveurs répertoriés dans cette section doivent être joint à votre domaine Active Directory.

  Pour plus d’informations sur l’installation et la configuration des services AD DS, consultez [Planification et conception des services AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autorité de certification** : une autorité de certification d’entreprise

  Pour plus d’informations sur l’installation et la configuration des services de certificats Active Directory (AD CS), consultez [Guide pas à pas des services de certificats Active Directory](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune impose d’exécuter AD CS avec une autorité de certification (AC) d’entreprise, et non avec une AC autonome.

- **Un client** : pour se connecter à l’autorité de certification d’entreprise

- **Certificat racine** : une copie exportée de votre certificat racine provenant de votre autorité de certification d’entreprise.

- **Microsoft Intune Certificate Connector** : utilisez le portail Azure pour télécharger le programme d’installation de **Certificate Connector** (**NDESConnectorSetup.exe**). 

  Le connecteur NDES Certificate prend également en charge FIPS le mode FIPS (Federal Information Processing Standard). FIPS n’est pas obligatoire, mais vous pouvez émettre et révoquer des certificats quand il est activé.

- **Serveur Windows Server** : héberge Microsoft Intune Certificate Connector (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exporter le certificat racine à partir de l’AC d’entreprise

Pour l’authentification avec un VPN, un réseau Wi-Fi et d’autres ressources, un certificat d’autorité de certification intermédiaire ou racine est nécessaire sur chaque appareil. Les étapes suivantes expliquent comment récupérer le certificat requis auprès de l’AC d’entreprise concernée.

1. Connectez-vous à votre AC d’entreprise avec un compte disposant de privilèges administratifs.
2. Ouvrez une invite de commandes en tant qu’administrateur.
3. Exportez le certificat d’AC racine (.cer) vers un emplacement où vous pourrez y accéder ultérieurement.

   Par exemple :

4. Une fois l'Assistant terminé, mais avant de fermer l'Assistant, cliquez sur **Lancer l'interface utilisateur de Certificate Connector**.

   `certutil -ca.cert certnew.cer`

   Pour plus d’informations, consultez la page [Tâches CertUtil pour la gestion des certificats](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurer les modèles de certificats sur l’autorité de certification

1. Connectez-vous à votre AC d’entreprise avec un compte disposant de privilèges administratifs.
2. Ouvrez la console **Autorité de certification**, cliquez avec le bouton droit sur **Modèles de certificats** et sélectionnez **Gérer**.
3. Recherchez le modèle de certificat **Utilisateur**, cliquez dessus avec le bouton droit et sélectionnez **Dupliquer le modèle**. La fenêtre **Propriétés du nouveau modèle** s’ouvre.
4. Sous l’onglet **Compatibilité** :

  - **Autorité de certification** : **Windows Server 2008 R2**
  - **Destinataire du certificat** : **Windows 7 / Server 2008 R2**

5. Dans l’onglet **Général**, spécifiez un **Nom d’affichage du modèle** qui soit significatif pour vous.

   > [!WARNING]
   > Par défaut, **Nom du modèle** est identique à **Nom complet du modèle**, *sans les espaces*. Notez le nom du modèle, vous en aurez besoin plus tard.

6. Dans **Traitement de la demande**, sélectionnez **Autoriser l’exportation de la clé privée**.
7. Dans **Chiffrement**, vérifiez que **Taille de clé minimale** a la valeur 2048.
8. Dans **Nom du sujet**, choisissez **Fournir dans la requête**.
9. Dans **Extensions**, vérifiez que vous voyez bien Système de fichiers EFS, Messagerie sécurisée et Authentification client sous **Stratégies d’application**.

    > [!IMPORTANT]
    > Pour les modèles de certificats iOS, accédez à l’onglet **Extensions**, mettez à jour **Utilisation de la clé** et vérifiez que l’option **Signature faisant preuve de l’origine** n’est pas sélectionnée.

10. Dans **Sécurité**, ajoutez le compte d’ordinateur du serveur sur lequel vous avez installé Microsoft Intune Certificate Connector. Accordez les autorisations **Lecture** et **Inscription** à ce compte.
11. Sélectionnez **Appliquer**, puis **OK** pour enregistrer le modèle de certificat.
12. Fermez la **Console Modèles de certificat**.
13. Dans la console **Autorité de certification**, cliquez avec le bouton droit sur **Modèles de certificats**, **Nouveau** et **Modèle de certificat à délivrer**. Choisissez le modèle que vous avez créé dans les étapes précédentes, puis sélectionnez **OK**.
14. Pour que le serveur gère les certificats pour le compte des utilisateurs et appareils inscrits auprès d’Intune, suivez ces étapes :

    1. Cliquez avec le bouton droit sur l’autorité de certification et sélectionnez **Propriétés**.
    2. Dans l’onglet Sécurité, ajoutez le compte d’ordinateur du serveur sur lequel vous exécutez Microsoft Intune Certificate Connector. Accordez les autorisations **Émettre et gérer des certificats** et **Demander des certificats** au compte d’ordinateur.

15. Déconnectez-vous de l’AC d’entreprise.

## <a name="download-install-and-configure-the-certificate-connector"></a>Télécharger, installer et configurer le connecteur de certificats

![Téléchargement de Connector][ConnectorDownload]

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil**, puis sélectionnez **Autorité de certification**.
4. Sélectionnez **Ajouter**, puis **Télécharger le fichier du connecteur**. Enregistrez le fichier téléchargé à un emplacement accessible à partir du serveur où vous effectuerez l’installation.
5. Une fois le téléchargement terminé, connectez-vous au serveur. Ensuite :

    1. Vérifiez que le .NET Framework 4.5 est installé, car il est nécessaire pour le connecteur NDES Certificate. Le .NET Framework 4.5 est automatiquement inclus avec Windows Server 2012 R2 et ses versions plus récentes.
    2. Exécutez le programme d’installation (NDESConnectorSetup.exe) et acceptez l’emplacement par défaut. Le connecteur est installé dans `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`. Dans Options du programme d’installation, sélectionnez **Distribution PFX**. Continuez et terminez l’installation.

6. Le connecteur NDES ouvre l’onglet **Inscription**. Pour activer la connexion à Intune, sélectionnez **Connexion** et spécifiez un compte disposant d’autorisations d’administrations globales.
7. Sous l’onglet **Avancé**, laissez l’option **Utiliser le compte SYSTÈME de cet ordinateur (par défaut)** sélectionnée.
8. Cliquez sur **Appliquer**, puis sur **Fermer**.
9. Revenez au portail Azure (**Intune** > **Configuration de l’appareil** > **Autorité de certification**). Après quelques minutes, une coche verte apparaît et **l’État de la connexion** est **Active**. Votre serveur de connecteur peut désormais communiquer avec Intune.

> [!NOTE]
> La prise en charge de TLS 1.2 est incluse avec le connecteur NDES Certificate. Ainsi, si le serveur avec le connecteur NDES Certificate installé prend en charge TLS 1.2, TLS 1.2 est utilisé. Si le serveur ne prend pas en charge TLS 1.2, TLS 1.1 est utilisé. Actuellement, TLS 1.1 est utilisé pour l’authentification entre les appareils et le serveur.

## <a name="create-a-device-configuration-profile"></a>Créer un profil de configuration d’appareils

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Accédez à **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil**.

   ![Accès à Intune][NavigateIntune]

3. Entrez les propriétés suivantes :

  - le **Nom** du profil ;
  - une description (facultatif) ;
  - la **Plateforme** sur laquelle le profil sera déployé ;
  - **Type de profil** : **Certificat approuvé**.

4. Accédez à **Paramètres** et entrez le fichier .cer du certificat d’AC racine exporté précédemment.

   > [!NOTE]
   > En fonction de la plateforme que vous avez choisie à l’**Étape 3**, vous n’aurez pas forcément la possibilité de choisir le **Magasin de destination** du certificat.

   ![Paramètres du profil][ProfileSettings]

5. Sélectionnez **OK**, puis **Créer** pour enregistrer votre profil.
6. Pour affecter le nouveau profil à un ou plusieurs appareils, consultez [Affecter des profils d’appareils Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Créer un profil de certificat PKCS

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Accédez à **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

  - le **Nom** du profil ;
  - une description (facultatif) ;
  - la **Plateforme** sur laquelle le profil sera déployé ;
  - **Type de profil** : **Certificat PKCS**.

4. Accédez à **Paramètres** et entrez les propriétés suivantes :

  - **Seuil de renouvellement (%)** : la valeur recommandée est de 20 %.
  - **Période de validité du certificat** : si vous n’avez pas changé le modèle de certificat, cette option peut être réglée sur un an.
  - **Autorité de certification** : nom de domaine complet (FQDN) interne de l’AC d’entreprise.
  - **Nom de l’autorité de certification** : indique le nom de l’AC d’entreprise, qui peut être différent de l’élément précédent.
  - **Nom du modèle de certificat** : nom du modèle créé précédemment. Rappel : Par défaut, **Nom du modèle** est identique à **Nom complet du modèle**, *sans les espaces*.
  - **Format du nom de l’objet** : réglez cette option sur **Nom commun**, sauf indication contraire.
  - **Autre nom de l’objet** : réglez cette option sur **Nom d’utilisateur principal (UPN)**, sauf indication contraire.
  - **Utilisation améliorée de la clé** : à condition que vous ayez utilisé les paramètres par défaut à l’étape 10 de la section [Configurer les modèles de certificats sur l’autorité de certification](#configure-certificate-templates-on-the-certification-authority) (dans et article), ajoutez les **Valeurs prédéfinies** suivantes de la sélection :
    - **Tout objet**
    - **Authentification client**
    - **Messagerie sécurisée**
  - **Certificat racine** (pour les profils Android) : indique le fichier .cer exporté à l’Étape 3 de la section [Exporter le certificat racine à partir de l’AC d’entreprise](#export-the-root-certificate-from-the-enterprise-ca) (dans cet article).

5. Sélectionnez **OK**, puis **Créer** pour enregistrer votre profil.
6. Pour affecter le nouveau profil à un ou plusieurs appareils, consultez [Affecter des profils d’appareils Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Étapes suivantes
[Utilisez des certificats SCEP](certificates-scep-configure.md) ou [émettez des certificats PKCS à partir d’un service web du gestionnaire PKI Symantec](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Accéder à Intune sur le Portail Azure et créer un nouveau profil pour un certificat approuvé"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Créer un profil et charger un certificat approuvé"
[ConnectorDownload]: ./media/certificates-download-connector.png "Télécharger Certificate Connector sur le Portail Azure"  
