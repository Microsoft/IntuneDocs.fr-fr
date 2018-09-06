---
title: Utiliser des certificats PKCS avec Microsoft Intune - Azure | Micrososft Docs
description: Découvrez comment ajouter ou créer des certificats PKCS (Public Key Cryptography Standards) avec Microsoft Intune, notamment comment exporter un certificat racine, configurer le modèle de certificat, télécharger et installer Microsoft Intune Certificate Connector (NDES), créer un profil de configuration d’appareil, créer un profil de certificat PKCS dans Azure et votre autorité de certification.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a86b53e34cc4fa24ec683657a646f8545396166e
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910834"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurer et utiliser des certificats PKCS avec Intune

> [!IMPORTANT]
> Nous apportons des améliorations à la fonctionnalité de S/MIME décrite dans cet article. Cette fonctionnalité est par conséquent temporairement supprimée d’Intune. Dès qu’elle sera publiée, nous supprimerons cette note.

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

  Le connecteur traite les demandes de certificat PKCS utilisées pour l’authentification ou la signature des e-mails S/MIME.

  Le connecteur NDES Certificate prend également en charge FIPS le mode FIPS (Federal Information Processing Standard). FIPS n’est pas obligatoire, mais vous pouvez émettre et révoquer des certificats quand il est activé.

- **PFX Certificate Connector pour Microsoft Intune** : si vous prévoyez d’utiliser le chiffrement des e-mails S/MIME, utilisez le portail Azure pour télécharger le programme d’installation **PFX Certificate Connector pour Microsoft Intune** ( **PfxCertificateConnectorBootstrapper.exe**). Le connecteur traite les demandes des fichiers PFX importés dans Intune en vue de chiffrer les e-mails S/MIME pour un utilisateur spécifique.

- **Windows Server** : Héberge :

  - Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) pour les scénarios d’authentification et de signature des e-mails S/MIME
  - PFX Certificate Connector pour Microsoft Intune (PfxCertificateConnectorBootstrapper.exe) pour les scénarios de chiffrement des e-mails S/MIME

  Vous pouvez exécuter les deux connecteurs (**Microsoft Intune Certificate Connector** et **PFX Certificate Connector pour Microsoft Intune**) sur le même serveur.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exporter le certificat racine à partir de l’AC d’entreprise

Pour l’authentification avec un VPN, un réseau Wi-Fi ou d’autres ressources, un certificat d’autorité de certification intermédiaire ou racine est nécessaire sur chaque appareil. Les étapes suivantes expliquent comment récupérer le certificat requis auprès de l’AC d’entreprise concernée.

1. Connectez-vous à votre AC d’entreprise avec un compte disposant de privilèges administratifs.
2. Ouvrez une invite de commandes en tant qu’administrateur.
3. Exportez le certificat d’AC racine (.cer) vers un emplacement où vous pourrez y accéder ultérieurement.
4. Une fois l'Assistant terminé, mais avant de fermer l'Assistant, cliquez sur **Lancer l'interface utilisateur de Certificate Connector**.

   `certutil -ca.cert certnew.cer`

   Pour plus d’informations, consultez la page [Tâches CertUtil pour la gestion des certificats](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurer les modèles de certificats sur l’autorité de certification

1. Connectez-vous à votre AC d’entreprise avec un compte disposant de privilèges administratifs.
2. Ouvrez la console **Autorité de certification**, cliquez avec le bouton droit sur **Modèles de certificats** et sélectionnez **Gérer**.
3. Recherchez le modèle de certificat **Utilisateur**, cliquez dessus avec le bouton droit et sélectionnez **Dupliquer le modèle**. La fenêtre **Propriétés du nouveau modèle** s’ouvre.

    > [!NOTE]
    > Pour les scénarios de signature et de chiffrement des e-mails S/MIME, de nombreux administrateurs utilisent des certificats différents pour la signature et le chiffrement. Si vous utilisez les Services de certificats Active Directory de Microsoft, vous pouvez utiliser le modèle **Signature Exchange uniquement** pour les certificats de signature des e-mails S/MIME, et le modèle **Utilisateur Exchange** pour les certificats de chiffrement S/MIME.  Si vous utilisez une autorité de certification tierce, il est recommandé de lire les instructions qui s’y rapportent pour configurer les modèles de signature et de chiffrement.

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
14. Pour que le serveur gère les certificats pour le compte des utilisateurs et des appareils inscrits auprès d’Intune, suivez ces étapes :

    1. Cliquez avec le bouton droit sur l’autorité de certification et sélectionnez **Propriétés**.
    2. Sous l’onglet Sécurité, ajoutez le compte d’ordinateur du serveur sur lequel vous exécutez les connecteurs (**Microsoft Intune Certificate Connector** ou **PFX Certificate Connector pour Microsoft Intune**). Accordez les autorisations **Émettre et gérer des certificats** et **Demander des certificats** au compte d’ordinateur.

15. Déconnectez-vous de l’AC d’entreprise.

## <a name="download-install-and-configure-the-certificate-connectors"></a>Télécharger, installer et configurer les connecteurs de certificats

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connecavec la valeurr

![Téléchargement de Connector][ConnectorDownload]

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil**, puis sélectionnez **Autorité de certification**.
4. Sélectionnez **Ajouter**, puis téléchargez Microsoft Intune Certificate Connector. Enregistrez le fichier téléchargé à un emplacement accessible à partir du serveur où vous effectuerez l’installation.
5. Une fois le téléchargement terminé, connectez-vous au serveur. Ensuite :

    1. Vérifiez que le .NET Framework 4.5 (ou version ultérieure) est installé, car il est nécessaire pour le connecteur NDES Certificate. Le .NET Framework 4.5 est automatiquement inclus avec Windows Server 2012 R2 et ses versions plus récentes.
    2. Exécutez le programme d’installation (NDESConnectorSetup.exe) et acceptez l’emplacement par défaut. Le connecteur est installé dans `\Program Files\Microsoft Intune\NDESConnectorUI`. Dans Options du programme d’installation, sélectionnez **Distribution PFX**. Continuez et terminez l’installation.
    3. Par défaut, le service du connecteur s’exécute sous le compte système local. Si un proxy est exigé pour accéder à Internet, vérifiez que le compte de service local peut accéder aux paramètres de proxy du serveur.

6. Le connecteur NDES ouvre l’onglet **Inscription**. Pour activer la connexion à Intune, sélectionnez **Connexion** et spécifiez un compte disposant d’autorisations d’administrations globales.
7. Sous l’onglet **Avancé**, il est recommandé de laisser l’option **Utiliser le compte SYSTÈME de cet ordinateur (par défaut)** sélectionnée.
8. Cliquez sur **Appliquer**, puis sur **Fermer**.
9. Revenez au portail Azure (**Intune** > **Configuration de l’appareil** > **Autorité de certification**). Après quelques minutes, une coche verte apparaît et **l’État de la connexion** est **Active**. Votre serveur de connecteur peut désormais communiquer avec Intune.

> [!NOTE]
> La prise en charge de TLS 1.2 est incluse dans Microsoft Intune Certificate Connector. Ainsi, si le serveur sur lequel est installé Microsoft Intune Certificate Connector prend en charge TLS 1.2, TLS 1.2 est utilisé. Si le serveur ne prend pas en charge TLS 1.2, TLS 1.1 est utilisé. Actuellement, TLS 1.1 est utilisé pour l’authentification entre les appareils et le serveur.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>PFX Certificate Connector pour Microsoft Intune

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil**, puis sélectionnez **Autorité de certification**.
4. Sélectionnez **Ajouter**, puis téléchargez PFX Certificate Connector pour Microsoft Intune. Enregistrez le fichier téléchargé à un emplacement accessible à partir du serveur où vous effectuerez l’installation.
5. Une fois le téléchargement terminé, connectez-vous au serveur. Ensuite :

    1. Vérifiez que le .NET Framework 4.6 (ou version ultérieure) est installé, car PFX Certificate Connector pour Microsoft Intune en a besoin. Si le .NET 4.6 Framework n’est pas installé, le programme d’installation l’installe automatiquement.
    2. Exécutez le programme d’installation (PfxCertificateConnectorBootstrapper.exe) et acceptez l’emplacement par défaut. Le connecteur est installé dans `Program Files\Microsoft Intune\PFXCertificateConnector`.
    3. Le service du connecteur s’exécute sous le compte système local. Si un proxy est exigé pour accéder à Internet, vérifiez que le compte de service local peut accéder aux paramètres de proxy du serveur.

6. Après l’installation, PFX Certificate Connector pour Microsoft Intune ouvre l’onglet **Inscription**. Pour activer la connexion à Intune, sélectionnez **Connexion** et spécifiez un compte disposant d’autorisations d’administrateur général ou d’administrateur Intune.
7. Fermez la fenêtre.
8. Revenez au portail Azure (**Intune** > **Configuration de l’appareil** > **Autorité de certification**). Après quelques minutes, une coche verte apparaît et **l’État de la connexion** est **Active**. Votre serveur de connecteur peut désormais communiquer avec Intune.

## <a name="create-a-trusted-certificate-profile"></a>Créer un profil de certificat approuvé

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
    - Définissez **Type de profil** sur **Certificat PKCS**.

4. Accédez à **Paramètres** et entrez les propriétés suivantes :

    - **Seuil de renouvellement (%)** : la valeur recommandée est 20 %.
    - **Période de validité du certificat** : si vous n’avez pas changé le modèle de certificat, cette option peut être définie sur un an.
    - **Fournisseur de stockage de clés (KSP)** : pour Windows, sélectionnez l’emplacement de l’appareil auquel stocker les clés.
    - **Autorité de certification** : nom de domaine complet (FQDN) interne de l’autorité de certification d’entreprise.
    - **Nom de l’autorité de certification** : indique le nom de l’autorité de certification d’entreprise, par exemple, «Autorité de certification Contoso ».
    - **Nom du modèle de certificat** : nom du modèle créé précédemment. Rappel : Par défaut, **Nom du modèle** est identique à **Nom complet du modèle**, *sans les espaces*.
    - **Format du nom de l’objet** : définissez cette option sur **Nom commun**, sauf indication contraire.
    - **Autre nom de l’objet** : définissez cette option sur **Nom d’utilisateur principal (UPN)**, sauf indication contraire.

5. Sélectionnez **OK**, puis **Créer** pour enregistrer votre profil.
6. Pour affecter le nouveau profil à un ou plusieurs appareils, consultez [Affecter des profils d’appareils Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Créer un profil de certificat importé PKCS

Vous pouvez importer dans Intune des certificats précédemment émis pour un utilisateur, à partir de n’importe quelle autorité de certification. Les certificats importés sont installés sur tous les appareils inscrits par l’utilisateur. Le chiffrement des e-mails S/MIME est le scénario le plus courant pour l’importation de certificats PFX existants dans Intune. Un utilisateur peut avoir plusieurs certificats pour chiffrer les e-mails. Les clés privées de ces certificats doivent se trouver sur tous les appareils d’un utilisateur, pour que celui-ci puisse déchiffrer les e-mails précédemment chiffrés.

Pour importer des certificats dans Intune, vous pouvez utiliser les [applets de commande PowerShell disponibles sur GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Après avoir importé les certificats dans Intune, créez un profil **Certificat PKCS importé** et affectez-le aux groupes Azure Active Directory.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Accédez à **Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - le **Nom** du profil ;
    - une description (facultatif) ;
    - la **Plateforme** sur laquelle le profil sera déployé ;
    - Définissez **Type de profil** sur **Certificat PKCS importé**.

4. Accédez à **Paramètres** et entrez les propriétés suivantes :

    - **Rôle prévu** : finalité des certificats qui sont importés pour ce profil. Un administrateur peut avoir des certificats importés avec différents rôles (par exemple, l’authentification, la signature S/MIME ou le chiffrement S/MIME). La finalité sélectionnée dans le profil de certificat correspond au profil de certificat comprenant les certificats importés associés.
    - **Période de validité du certificat** : si vous n’avez pas changé le modèle de certificat, cette option peut être définie sur un an.
    - **Fournisseur de stockage de clés (KSP)** : pour Windows, sélectionnez l’emplacement de l’appareil auquel stocker les clés.

5. Sélectionnez **OK**, puis **Créer** pour enregistrer votre profil.
6. Pour affecter le nouveau profil à un ou plusieurs appareils, consultez [Affecter des profils d’appareils Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Étapes suivantes
[Utilisez des certificats SCEP](certificates-scep-configure.md) ou [émettez des certificats PKCS à partir d’un service web du gestionnaire PKI Symantec](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Accéder à Intune sur le Portail Azure et créer un nouveau profil pour un certificat approuvé"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Créer un profil et charger un certificat approuvé"
[ConnectorDownload]: ./media/certificates-download-connector.png "Télécharger Certificate Connector sur le Portail Azure"  
