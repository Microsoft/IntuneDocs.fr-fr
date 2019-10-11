---
title: Émettre des certificats DigiCert PKCS avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Installez et configurez Intune Certificate Connector de façon à émettre des certificats PKCS sur des appareils gérés par Intune, à partir de la plateforme PKI DigiCert.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1679eb656e04296e53d8994dcd47144621c99d0c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721771"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Configurer Intune Certificate Connector pour la plateforme DigiCert PKI  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Utilisez Intune Certificate Connector de façon à émettre des certificats PKCS sur des appareils gérés par Intune, à partir de la plateforme PKI DigiCert. Vous pouvez utiliser le connecteur avec une autorité de certification (AC) DigiCert uniquement, ou avec une AC DigiCert et une AC Microsoft.  
> [!TIP]  
> DigiCert a acquis les solutions de sécurité web de Symantec et les solutions PKI associées. Pour plus d’informations sur cette modification, consultez [l’article du support technique Symantec](https://support.symantec.com/en_US/article.INFO4722.html).

Si vous utilisez déjà Intune Certificate Connector pour émettre des certificats à partir d’une autorité de certification Microsoft à l’aide de PKCS ou de System Center Endpoint Protection, vous pouvez utiliser ce même connecteur pour configurer et émettre des certificats PKCS à partir d’une autorité de certification DigiCert. Une fois la configuration de la prise en charge de l’autorité de certification DigiCert terminée, Intune Certificate Connector peut émettre les certificats suivants :

* Certificats PKCS à partir d’une AC Microsoft
* Certificats PKCS d’une AC DigiCert
* Certificats Endpoint Protection d’une AC Microsoft

Si le connecteur n’est pas installé mais que vous envisagez de l’utiliser à la fois pour une AC Microsoft et une AC DigiCert, effectuez d’abord la configuration du connecteur pour l’AC Microsoft. Ensuite, revenez à cet article pour le configurer pour qu’il prenne également en charge DigiCert. Pour plus d’informations sur les profils de certificat et le connecteur, consultez [Configurer un profil de certificat pour vos appareils dans Microsoft Intune](certificates-configure.md).  

Si vous utilisez le connecteur uniquement avec l’AC DigiCert, vous pouvez suivre les instructions de cet article pour installer et configurer le connecteur. 

## <a name="prerequisites"></a>Prérequis  
- **Un abonnement actif auprès de l’AC DigiCert** : L’abonnement est nécessaire pour obtenir un certificat d’autorité d’inscription auprès de l’AC DigiCert.

## <a name="install-the-digicert-ra-certificate"></a>Installer le certificat d’autorité d’inscription DigiCert  
 
1. Enregistrez l’extrait de code suivant tel quel dans un fichier nommé **certreq.ini** et adaptez-le à vos besoins (par exemple : *Nom de l’objet au format CN*).
 
        [Version] 
        Signature="$Windows NT$" 
        
        [NewRequest] 
        ;Change to your,country code, company name and common name 
        Subject = "Subject Name in CN format"
        
        KeySpec = 1 
        KeyLength = 2048 
        Exportable = TRUE 
        MachineKeySet = TRUE 
        SMIME = False 
        PrivateKeyArchive = FALSE 
        UserProtected = FALSE 
        UseExistingKeySet = FALSE 
        ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
        ProviderType = 12 
        RequestType = PKCS10 
        KeyUsage = 0xa0 
        
        [EnhancedKeyUsageExtension] 
        OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication
        
        ;----------------------------------------------- 

2. Ouvrez une invite de commandes avec élévation de privilèges et générez une demande de signature de certificat (CSR) à l’aide de la commande suivante :

   `Certreq.exe -new certreq.ini request.csr`

3. Ouvrez le fichier request.csr dans le Bloc-notes et copiez le contenu CSR, qui est au format suivant :


        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Connectez-vous à l’autorité de certification DigiCert et accédez à **Obtenir un certificat RA** à partir des tâches.

   a. Dans la zone de texte, fournissez le contenu CSR de l’étape 3. 

   b. Fournissez un nom convivial pour le certificat.

   c. Sélectionnez **Continuer**. 

   d. Utilisez le lien fourni pour télécharger le certificat d’autorité d’inscription sur votre ordinateur local.

5. Importez le certificat d’autorité d’inscription dans le magasin de certificats Windows :

   a. Ouvrez une console MMC.

   b. Sélectionnez **Fichier** > **Ajouter ou supprimer des composants logiciels enfichables** > **Certificat** > **Ajouter**. 

   c. Sélectionnez **Compte de l’ordinateur** > **Suivant**.

   d. Sélectionnez **Ordinateur local** > **Terminer**. 

   e. Sélectionnez **OK** dans la fenêtre **Ajouter ou supprimer des composants logiciels enfichables**. Développez **Certificats (Ordinateur local)**  > **Personnel** > **Certificats**.

   f. Cliquez avec le bouton droit sur le nœud **Certificats**, et sélectionnez **Toutes les tâches** > **Importer**.  

   g. Sélectionnez l’emplacement du certificat d’autorité d’inscription que vous avez téléchargé à partir de l’AC DigiCert, puis sélectionnez **Suivant**.

   h. Sélectionnez **Magasin de certificats personel** > **Suivant**. 

   i. Sélectionnez **Terminer** pour importer le certificat RA et sa clé privée dans le magasin **Ordinateur local-Personnel**.  

6. Exportez et importez le certificat de clé privée : 

   a. Développez **Certificats (Ordinateur local)**  > **Personnel** > **Certificats**.

   b. Sélectionnez le certificat qui a été importé à l’étape précédente.

   c. Cliquez avec le bouton droit sur le certificat et sélectionnez **Toutes les tâches** > **Exporter**.

   d. Sélectionnez **Suivant**, puis entrez le mot de passe.

   e. Sélectionnez l’emplacement d’exportation et sélectionnez **Terminer**.

   f. Utilisez la même procédure qu’à l’étape 5 pour importer le certificat de clé privée dans le magasin **Ordinateur local-Personnel**.

   g. Enregistrez une copie de l’empreinte du certificat d’autorité d’inscription sans les espaces. Voici un exemple d’empreinte : 

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
    
    > [!NOTE]
    > Pour obtenir de l’aide pour récupérer le certificat RA auprès de l’autorité de certification DigiCert, contactez le [support client DigiCert](mailto:enterprise-pkisupport@digicert.com).  

## <a name="prepare-to-install-intune-certificate-connector"></a>Préparer l’installation d’Intune Certificate Connector
> [!TIP]  
> Cette section s’applique si vous utilisez Intune Certificate Connector avec une seule autorité de certification (AC) DigiCert. Si vous utilisez Intune Certificate Connector avec une autorité de certification Microsoft et souhaitez ajouter la prise en charge de l’autorité de certification DigiCert, passez directement à [Configurer le connecteur pour prendre en charge DigiCert](#configure-the-connector-to-support-digicert).  

1. Choisissez l’une des versions du système d’exploitation Windows de la liste suivante et installez-la sur un ordinateur :
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Créez un utilisateur avec des privilèges administratifs et utilisez-le pour suivre les étapes ci-dessous.

3. Vérifiez les dernières mises à jour Windows disponibles et installez-les. Après avoir installé les mises à jour Windows, redémarrez l’ordinateur.

4. Installez .NET Framework 3.5 :

   a. Ouvrez **Panneau de configuration** > **Programmes et fonctionnalités** > **Activer ou désactiver des fonctionnalités Windows**.

   b. Sélectionnez **.NET Framework 3.5** et installez-le.  

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Installer Intune Certificate Connector pour une utilisation avec DigiCert  

> [!TIP]  
> Si vous utilisez Intune Certificate Connector avec une AC Microsoft et souhaitez ajouter la prise en charge de l’AC DigiCert, passez directement à [Configurer le connecteur pour prendre en charge DigiCert](#configure-the-connector-to-support-digicert).  

Téléchargez la dernière version d’Intune Certificate Connector sur le portail d’administration Intune et suivez ces instructions.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  

2. Sélectionnez **Configuration de l’appareil** > **Connecteurs de certification** >  **+Ajouter**.  

3. Sélectionnez **Télécharger le logiciel de connecteur de certificats**. Enregistrez le logiciel à un emplacement accessible à partir du serveur où vous effectuerez l’installation.  

   ![Télécharger le logiciel Connecteur](./media/certificates-digicert-configure/connector-download.png)
   
4. Sur le serveur où vous souhaitez installer le connecteur, exécutez **NDESConnectorSetup.exe** avec des privilèges élevés. 

5. Sur la page **Options d'installation**, sélectionnez **Distribution PFX**.  
   
   ![Sélectionner la distribution PFX](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Si vous utilisez Intune Certificate Connector de façon à ce qu’il émette des certificats à partir d’une AC Microsoft et d’une AC DigiCert, sélectionnez **Distribution de profils SCEP et PFX**. 

6. Utilisez les sélections par défaut pour terminer la configuration du connecteur.

## <a name="configure-the-connector-to-support-digicert"></a>Configurer le connecteur pour prendre en charge DigiCert

Par défaut, Intune Certificate Connector est installé dans **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**.

1. Dans le dossier **NDESConnectorSvc**, ouvrez le fichier **NDESConnector.exe.config** dans le Bloc-notes.

   a. Remplacez la valeur de clé `RACertThumbprint` par celle de l’empreinte du certificat que vous avez copiée dans la section précédente. Par exemple :

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   
   b. Enregistrez et fermez le fichier.

2. Ouvrez **services.msc** :

   a. Sélectionnez **Service Intune Connector**.

   b. Arrêtez, puis démarrez le service.

   c. Fermez la fenêtre du service.

## <a name="set-up-the-intune-administrator-account"></a>Configurer le compte d’administrateur Intune  

> [!TIP]  
> Si vous utilisez Intune Certificate Connector avec une autorité de certification Microsoft et souhaitez ajouter la prise en charge de l’autorité de certification DigiCert, passez directement à [Créer un profil de certificat approuvé](#create-a-trusted-certificate-profile).   
 
1. Ouvrez l’interface utilisateur du connecteur NDES depuis **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.  

2. Sous l’onglet **Inscription**, sélectionnez **Se connecter**.

3. Saisissez vos informations d’identification d’administration de locataire Intune.

4. Sélectionnez **Se connecter**, puis **OK** pour confirmer une inscription réussie. Vous pouvez alors fermer l’interface utilisateur NDES Connector.
   
   ![L’interface du connecteur NDES avec le message d’inscription réussie](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)



## <a name="create-a-trusted-certificate-profile"></a>Créer un profil de certificat approuvé

Les certificats PKCS déployés pour les appareils gérés par Intune doivent être enchaînés avec un certificat racine approuvé. Pour établir cette chaîne, créez un profil de certificat approuvé Intune avec le certificat racine de l’autorité de certification DigiCert.

1. Récupérez un certificat racine approuvé auprès de l’AC DigiCert :

    a. Connectez-vous au portail d’administration de l’AC DigiCert.

    b. Sélectionnez **Gérer les AC** dans **Tâches**. 

    c. Sélectionnez l’AC correspondante dans la liste.  

    d. Sélectionnez **Télécharger le certificat racine** pour télécharger le certificat racine approuvé.

2. Créez un profil de certificat approuvé dans le portail Intune :

   a. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

   b. Sélectionnez **Configuration de l’appareil** > **Gérer** > **Profils** > **Créer un profil**.

   c. Entrez un **Nom** et une **Description** pour le profil de certificat approuvé.

   d. Dans la liste déroulante **Plateforme**, sélectionnez la plateforme d’appareil pour ce certificat approuvé.

   e. Dans la liste déroulante **Type de profil**, sélectionnez **Certificat approuvé**.

   f. Accédez au fichier .cer racine approuvé de l’autorité de certification que vous avez obtenu auprès de l’autorité de certification DigiCert à l’étape précédente, puis sélectionnez **OK**.

   g. Pour les appareils Windows 8.1 et Windows 10 uniquement, sélectionnez le magasin de destination pour le certificat approuvé à partir de :    
      - **Boutique de certificats de l’ordinateur - Racine**  
      - **Boutique de certificats de l’ordinateur - Intermédiaire**  
      - **Boutique de certificats de l’utilisateur - Intermédiaire** 

   h. Lorsque vous avez terminé, sélectionnez **OK**, revenez au volet **Créer un profil** et sélectionnez **Créer**.  
 
Le profil apparaît dans la liste des profils dans le volet **Configuration de l’appareil – Profils**, avec le type de profil **Certificat approuvé**.  Veillez à attribuer ce profil aux appareils qui recevront les certificats. Pour attribuer ce profil à des groupes, consultez [Attribuer des profils d’appareil](../configuration/device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>Récupérer l’OID du profil de certificat  

L’OID du profil de certificat est associé à un modèle de profil de certificat dans l’AC DigiCert. Pour créer un profil de certificat PKCS sur Intune, le nom du modèle de certificat doit être sous la forme d’un OID de profil de certificat associé à un modèle de certificat dans l’AC DigiCert.

1. Connectez-vous au portail d’administration de l’AC DigiCert.
2. Sélectionnez **Gérer les profils de certificats**.
3. Sélectionnez le profil de certificat que vous voulez utiliser.
4. Copiez l’OID du profil de certificat. Il se présente sous la forme suivante :

 
       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
 

> [!NOTE]
> Si vous avez besoin d’aide pour obtenir l’OID du profil de certificat, contactez le [support client DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="create-a-pkcs-certificate-profile"></a>Créer un profil de certificat PKCS

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  

2. Accédez à **Configuration de l’appareil** >  **Profils**, puis sélectionnez **Créer un profil**.

3. Entrez un **Nom** et une **Description** pour le profil de certificat PKCS.  

4. Dans la liste déroulante **Plateforme**, sélectionnez une plateforme d’appareil prise en charge.

5. Dans la liste déroulante **Type de profil**, sélectionnez **Certificat PKCS**.
 
6. Dans le volet **Certificat PKCS**, configurez les paramètres avec les valeurs du tableau suivant. Ces valeurs sont requises pour émettre des certificats PKCS à partir d’une autorité de certification DigiCert via Intune Certificate Connector. 

   |Paramètre du certificat PKCS | Valeur | Description |
   | --- | --- | --- |
   | Autorité de certification | pki-ws.symauth.com | Cette valeur doit être le nom de domaine complet du service de base de l’AC DigiCert, sans les barres obliques de fin. Si vous n’avez pas la certitude qu’il s’agisse du bon nom de domaine complet du service de base pour votre abonnement à l’AC DigiCert, contactez le service clientèle de DigiCert. <br><br>*Avec le passage de Symantec à DigiCert, cette URL reste inchangée*. <br><br> Si ce nom de domaine complet est incorrect, Intune Certificate Connector n’émet pas de certificats PKCS à partir de l’AC DigiCert.| 
   | Nom de l’autorité de certification | Symantec | Cette valeur doit être la chaîne **Symantec**. <br><br> Si elle est modifiée, Intune Certificate Connector n’émettra pas de certificats PKCS à partir de l’AC DigiCert.|
   | Nom du modèle de certificat | OID de profil de certificat de l’AC DigiCert. Par exemple : **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Cette valeur doit être un OID de profil de certificat [obtenu dans la section précédente](#get-the-certificate-profile-oid) à partir du modèle de profil de certificat de l’AC DigiCert. <br><br> Si Intune Certificate Connector ne trouve pas de modèle de certificat associé à cet OID de profil de certificat dans l’AC DigiCert, il n’émettra pas de certificats PKCS à partir de l’AC DigiCert.|  

   ![Sélections pour l’AC et le modèle de certificat](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)  

   > [!NOTE]
   > Il n’est pas nécessaire d’associer les profils de certificats PKCS des plateformes Windows à un profil de certificat approuvé. Cette opération est toutefois requise pour les profils de plateformes autres que Windows, comme Android.
7. Terminez la configuration du profil pour répondre aux besoins de votre entreprise, puis sélectionnez **OK** pour enregistrer le profil. 

8. Sélectionnez **Affectations** et configurez un groupe approprié qui recevra ce profil. Au moins un utilisateur ou un appareil doit faire partie du groupe affecté.
 
À l’issue des étapes précédentes, Intune Certificate Connector émettra des certificats PKCS à partir de l’AC DigiCert, sur les appareils gérés par Intune du groupe affecté. Ces certificats seront disponibles dans le magasin **Personnel** du magasin de certificats **Utilisateur actuel** de l’appareil géré par Intune.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>Attributs pris en charge par les profils de certificats PKCS

|Attribut | Formats pris en charge par Intune | Formats pris en charge par l’AC DigiCert Cloud | result |
| --- | --- | --- | --- |
| Nom d'objet |Intune prend en charge le nom de l’objet aux formats suivants uniquement : <br><br> 1. Nom commun <br> 2. Nom commun, adresse e-mail incluse <br> 3. Nom commun comme adresse e-mail <br><br> Par exemple : <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | L’AC DigiCert prend en charge davantage d’attributs.  Si vous souhaitez sélectionner d’autres attributs, ils doivent avoir des valeurs fixes dans le modèle de profil de certificat DigiCert.| Nous utilisons le Nom commun ou l’adresse e-mail de la demande de certificat PKCS. <br><br> La moindre différence de sélection d’attributs entre le profil de certificat Intune et le modèle de profil de certificat DigiCert empêche l’émission de certificats par l’AC DigiCert.|
| SAN | Intune prend en charge uniquement les valeurs de champs SAN suivantes : <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (valeur encodée) | L’AC DigiCert Cloud prend également en charge ces paramètres. Si vous souhaitez sélectionner d’autres attributs, ils doivent avoir des valeurs fixes dans le modèle de profil de certificat DigiCert. <br><br> **AltNameTypeEmail** : Si ce type est introuvable dans le champ SAN, Intune Certificate Connector utilise la valeur de **AltNameTypeUpn**.  Si **AltNameTypeUpn** est également introuvable dans le champ SAN, Intune Certificate Connector utilise la valeur Nom de l’objet, à condition que celle-ci soit au format adresse e-mail.  Si le type reste introuvable, Intune Certificate Connector ne parvient pas à émettre les certificats. <br><br> Exemple : `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn** : Si ce type est introuvable dans le champ SAN, Intune Certificate Connector utilise la valeur de **AltNameTypeEmail**. Si **AltNameTypeEmail** est également introuvable dans le champ SAN, Intune Certificate Connector utilise la valeur Nom de l’objet, à condition que celle-ci soit au format adresse e-mail. Si le type reste introuvable, Intune Certificate Connector ne parvient pas à émettre les certificats.  <br><br> Exemple : `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName** : Si ce type est introuvable dans le champ SAN, Intune Certificate Connector ne parvient pas à émettre les certificats. <br><br> Exemple : `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  Notez que la valeur de ce champ est prise en charge par l’AC DigiCert uniquement dans un format encodé (valeur hexadécimale). Quelle qu’elle soit, Intune Certificate Connector la convertit au codage base 64 avant d’envoyer la demande de certificat. *Intune Certificate Connector ne vérifie pas si cette valeur est déjà encodée.* | Aucune |

## <a name="troubleshooting"></a>Résolution des problèmes

Les journaux du service Intune Certificate Connector sont disponibles dans **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** sur l’ordinateur du connecteur NDES. Ouvrez-les dans [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) et recherchez les messages d’erreur et d’exception.

| Problème/message d’erreur | Étapes de résolution |
| --- | --- |
| Impossible de se connecter avec un compte Administrateur client Intune sur l’interface utilisateur NDES Connector. | Cela peut se produire lorsque Certificate Connector n’est pas activé en local sur le portail d’administration Intune. Pour résoudre ce problème, utilisez une des procédures suivantes : <br><br> À partir de l’interface utilisateur de Silverlight : <br> 1. Connectez-vous au [portail d’administration Intune](https://admin.manage.microsoft.com). <br> 2. Sélectionnez **ADMIN**. <br> 3. Sélectionnez **Gestion des appareils mobiles** > **Certificate Connector**. <br> 4. Sélectionnez **Configurer Certificate Connector en local**. <br> 5. Cochez la case **Activer Certificate Connector**. <br> 6. Sélectionnez **OK**. <br><br> Sur l’interface utilisateur du Portail Azure : <br> 1. Connectez-vous au [portail Azure](https://portal.azure.com). <br> 2. Accédez à Microsoft Intune. <br> 3. Sélectionnez **Configuration de l’appareil** > **Autorité de certification**. <br> 4. Sélectionnez **Activer**. <br><br> Après avoir suivi les étapes précédentes sur l’interface utilisateur Silverlight ou sur le Portail Azure, essayez de vous connecter avec le même compte Administrateur client Intune sur l’interface utilisateur NDES Connector. |
| Certificat NDES Connector introuvable. <br><br> System.ArgumentNullException : La valeur ne peut pas être null. | Intune Certificate Connector affiche cette erreur si le compte Administrateur client Intune n’a jamais été connecté à l’interface utilisateur NDES Connector. <br><br> Si cette erreur persiste, redémarrez Intune Service Connector. <br><br> 1. Ouvrez **services.msc**. <br> 2. Sélectionnez **Service Intune Connector**. <br> 3. Cliquez avec le bouton droit et sélectionnez **Redémarrer**.|
| NDES Connector - IssuePfx - Exception générique : <br> System.NullReferenceException : La référence d’objet n’a pas pour valeur une instance d’un objet. | Cette erreur est temporaire. Redémarrez Intune Service Connector. <br><br> 1. Ouvrez **services.msc**. <br> 2. Sélectionnez **Service Intune Connector**. <br> 3. Cliquez avec le bouton droit et sélectionnez **Redémarrer**. |
| Fournisseur DigiCert - Impossible d’obtenir la stratégie DigiCert. <br><br>« L’opération a expiré. » | Intune Certificate Connector a reçu une erreur d’expiration du délai d’attente de l’opération lors de la communication avec l’AC DigiCert. Si cette erreur persiste, augmentez la valeur du délai de connexion, puis réessayez. <br><br> Pour augmenter le délai de connexion : <br> 1. Accédez à l’ordinateur NDES Connector. <br>2. Ouvrez le fichier **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** dans le Bloc-notes. <br> 3. Augmentez la valeur du délai d’attente pour le paramètre suivant : <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Redémarrez le service Intune Certificate Connector. <br><br> Si le problème persiste, contactez le service clientèle de DigiCert. |
| Fournisseur DigiCert - Impossible de récupérer le certificat client. | Intune Certificate Connector n’est pas parvenu à récupérer le certificat d’autorisation d’accès aux ressources dans le magasin de certificats Ordinateur local-Personnel. Pour résoudre ce problème, installez le certificat d’autorisation d’accès aux ressources dans le magasin de certificats Ordinateur local-Personnel avec sa clé privée. <br><br> Le certificat d’autorisation d’accès aux ressources s’obtient auprès de l’AC DigiCert. Pour plus d’informations, contactez le service clientèle de DigiCert. | 
| Fournisseur DigiCert - Impossible d’obtenir la stratégie DigiCert. <br><br>« La demande a été abandonnée : Impossible de créer un canal sécurisé SSL/TLS. » | Cette erreur se produit dans les scénarios suivants : <br><br> 1. Le service Intune Certificate Connector ne dispose des autorisations pour lire le certificat d’autorisation d’accès aux ressources ainsi que sa clé privée dans le magasin de certificats Ordinateur local-Personnel. Pour résoudre ce problème, vérifiez le contexte d’exécution du service Connector dans services.msc. Le service doit s’exécuter sous le contexte NT AUTHORITY\SYSTEM. <br><br> 2. Le profil de certificat PKCS dans le portail d’administration Intune est peut-être configuré avec un nom de domaine complet non valide pour le service de base de l’AC DigiCert. Le nom de domaine complet est semblable à **pki-ws.symauth.com**. Pour résoudre ce problème, vérifiez auprès du service clientèle de DigiCert que l’URL est correcte pour votre abonnement. <br><br> 3. Intune Certificate Connector ne parvient pas à s’authentifier auprès de l’AC DigiCert via le certificat d’autorisation d’accès aux ressources, car il n’est pas en mesure de récupérer sa clé privée. Pour résoudre ce problème, veillez à installer le certificat d’autorisation d’accès aux ressources ainsi que sa clé privée dans le magasin de certificats Ordinateur local-Personnel. <br><br> Si le problème persiste, contactez le service clientèle de DigiCert. |
| Fournisseur DigiCert - Impossible d’obtenir la stratégie DigiCert. <br><br>« Un élément de requête n’est pas compris. » | Intune Certificate Connector n’est pas parvenu à récupérer le modèle de profil de certificat DigiCert, car l’OID du profil client ne correspond pas au profil de certificat Intune. Dans un autre cas de figure, Intune Certificate Connector ne parvient pas à trouver le modèle de profil de certificat associé à l’OID du profil client donné dans l’AC DigiCert. <br><br> Pour résoudre ce problème, récupérez le bon OID de profil client à partir du modèle de certificat DigiCert dans l’AC DigiCert. Ensuite, mettez à jour le profil de certificat PKCS dans le portail d’administration Intune. <br><br> Obtenez l’OID du profil client auprès de l’AC DigiCert : <br> 1. Connectez-vous au portail d’administration de l’AC DigiCert. <br> 2. Sélectionnez **Gérer les profils de certificats**. <br> 3. Sélectionnez le profil de certificat que vous voulez utiliser. <br> 4. Récupérez l’OID du profil de certificat. Il se présente sous la forme suivante : <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Mettez à jour le profil de certificat PKCS avec l’OID du profil de certificat correspondant : <br>1. Connectez-vous au portail d’administration Intune. <br> 2. Accédez au profil de certificat PKCS et sélectionnez **Modifier**. <br> 3. Mettez à jour l’OID du profil de certificat dans le champ du nom du modèle de certificat. <br> 4. Enregistrez le profil de certificat PKCS. |
| Fournisseur DigiCert - Échec de la vérification de la stratégie. <br><br> L’attribut ne fait pas partie de la liste d’attributs de modèle de certificat pris en charge par DigiCert. | L’AC DigiCert affiche ce message en cas de différence entre le modèle de profil de certificat DigiCert et le profil de certificat Intune. Ce problème est probablement dû à une incompatibilité d’attribut dans **SubjectName** ou **SubjectAltName**. <br><br> Pour résoudre ce problème, sélectionnez des attributs pris en charge par Intune pour **SubjectName** et **SubjectAltName** dans le modèle de profil de certificat DigiCert. Pour plus d’informations, consultez les attributs pris en charge par Intune dans la section **Paramètres des certificats**. |
| Certains appareils Utilisateur ne reçoivent pas de certificats PKCS de la part de l’AC DigiCert. | Ce problème se produit lorsque l’UPN utilisateur contient des caractères spéciaux comme des traits de soulignement (exemple : `global_admin@intune.onmicrosoft.com`). <br><br> L’AC DigiCert ne prend pas en charge les caractères spéciaux dans **mail_firstname** et **mail_lastname**. <br><br> Pour résoudre ce problème, suivez les étapes ci-dessous : <br><br> 1. Connectez-vous au portail d’administration de l’AC DigiCert. <br> 2. Accédez à **Gérer les profils de certificats**. <br> 3. Sélectionnez le profil de certificat utilisé pour Intune. <br> 4. Sélectionnez le lien **Options de personnalisation**. <br> 5. Sélectionnez le bouton **Options avancées**. <br> 6. Sous les champs **Certificat – Nom de domaine de l’objet**, ajoutez le champ **Nom commun (CN)** et supprimez le champ **Nom commun (CN)** existant. Les opérations d’ajout et de suppression doivent être réalisées simultanément. <br> 7. Sélectionnez **Enregistrer**. <br><br> Avec la modification précédente, le profil de certificat DigiCert demande **« CN = <upn>»** au lieu de **mail_firstname** et **mail_lastname**. |
| L’utilisateur a supprimé manuellement de l’appareil un certificat déjà déployé. | Intune redéploie le même certificat pendant l’archivage suivant ou l’application des stratégies suivante. Dans ce cas, NDES Connector ne reçoit pas de demande de certificat PKCS. |

## <a name="next-steps"></a>Étapes suivantes

Utilisez les informations de cet article et celles de la page [Qu’est-ce qu’un profil d’appareil Microsoft Intune ?](../configuration/device-profiles.md) pour gérer les appareils de votre organisation et les certificats dont ils disposent.

