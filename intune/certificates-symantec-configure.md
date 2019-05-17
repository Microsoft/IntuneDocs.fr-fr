---
title: Émettre des certificats Symantec PKCS avec Microsoft Intune
titleSuffix: ''
description: Installez et configurez Intune Certificate Connector de façon à émettre des certificats PKCS sur des appareils gérés par Intune, à partir du service web Symantec PKI Manager.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: da57b14f8196251ee8c77de3ffcd48f5b586a12f
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567710"
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Configurer Intune Certificate Connector pour le service web Symantec PKI Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article explique comment installer et configurer Intune Certificate Connector de façon à ce qu’il émette des certificats PKCS sur des appareils gérés par Intune, à partir d’un service web Symantec PKI Manager.

Le service web Symantec PKI Manager est appelé AC Symantec tout au long de cet article. Si vous déjà configuré Intune Certificate Connector de façon à ce qu’il émette des certificats PKCS et des certificats SCEP à partir de l’autorité de certification (AC) Microsoft, Connector peut également servir à configurer et à émettre des certificats PKCS à partir d’une AC Symantec. Dans ce cas, Intune Certificate Connector peut émettre les certificats suivants :

* certificats PKCS à partir d’une AC Microsoft ;
* certificats SCEP à partir d’une AC Microsoft ;
* certificats PKCS à partir d’une AC Symantec.

Si vous souhaitez utiliser Intune Certificate Connector pour les AC Microsoft et Symantec, vous devez au préalable effectuer la configuration Intune Certificate Connector pour l’AC Microsoft, puis suivre ces étapes afin de le configurer pour l’AC Symantec.  Pour plus d’informations sur la configuration d’Intune Certificate Connector pour une AC Microsoft, consultez [Guide pratique pour configurer des certificats dans Microsoft Intune](certificates-configure.md).

## <a name="prepare-to-install-intune-certificate-connector"></a>Préparer l’installation d’Intune Certificate Connector

Si vous utilisez déjà Intune Certificate Connector pour une AC Microsoft existante et que vous souhaitez ajouter la prise en charge de l’AC Symantec, ignorez cette étape et passez aux étapes restantes après avoir installé la dernière version d’Intune Certificate Connector sur le portail d’administration Intune. Cette étape n’est requise que pour pouvoir utiliser Intune Certificate Connector pour une AC Symantec autonome.

1. Choisissez l’une des versions du système d’exploitation Windows de la liste suivante et installez-la sur un ordinateur :
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Créez un utilisateur avec des privilèges administratifs et utilisez-le pour suivre les étapes ci-dessous.

3. Récupérez les dernières mises à jour Windows Update disponibles et installez-les.

   > [!IMPORTANT]
   > Après avoir installé les mises à jour Windows Update, redémarrez l’ordinateur.

4. Installez .NET Framework 3.5 :

    a. Ouvrez **Panneau de configuration** > **Programmes et fonctionnalités** > **Activer ou désactiver des fonctionnalités Windows**.

    b. Sélectionnez **.NET Framework 3.5** et installez-le.

## <a name="install-the-symantec-registration-authorization-certificate"></a>Installer le certificat d’autorisation d’inscription Symantec

Suivez les étapes ci-dessous pour récupérer le certificat d’autorisation d’inscription auprès de l’AC Symantec. Vous devez pour cela disposer d’un abonnement actif à l’AC Symantec.

1. Enregistrez l’extrait de code suivant tel quel dans un fichier nommé **certreq.ini** et adaptez-le à vos besoins (par exemple : *Nom de l’objet au format CN*).

   ```
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
   ```

2. Ouvrez une invite de commandes avec élévation de privilèges et générez du contenu CSR avec la commande suivante :

   `Certreq.exe -new certreq.ini request.csr`

3. Ouvrez le fichier request.csr dans le Bloc-notes et copiez le contenu CSR, qui est au format suivant :

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Ouvrez une session auprès de l’AC Symantec et accédez à **Obtenir un certificat d’autorité d’inscription** dans les tâches.

   a. Saisissez le contenu CSR de l’étape 3 dans la zone de texte correspondante.

   b. Entrez le nom convivial du certificat dans la zone de texte correspondante.

   c. Cliquez sur **Continue** (Continuer).

      Un lien de téléchargement du certificat d’autorité d’inscription s’affiche.

   d. Téléchargez le certificat d’autorité d’inscription sur l’ordinateur local.

5. Importez le certificat d’autorité d’inscription dans le magasin de certificats Windows :

    a. Ouvrez une console MMC.

    b. Cliquez sur **Fichier** > **Ajouter ou supprimer des composants logiciels enfichables** > **Certificat**, puis sur **Ajouter**.

    c. Sélectionnez **Compte d’ordinateur**, puis cliquez sur **Suivant**.

    d. Sélectionnez **Ordinateur local**, puis cliquez sur **Terminer**.

    e. Cliquez sur **OK** dans la fenêtre **Ajouter ou supprimer des composants logiciels enfichables**. Développez **Certificats (Ordinateur local)** > **Personnel** > **Certificats**.

    f. Cliquez avec le bouton droit sur le nœud **Certificats**, et sélectionnez **Toutes les tâches** > **Importer**.

    g. Sélectionnez l’emplacement du certificat d’autorité d’inscription que vous avez téléchargé à partir de l’AC Symantec, puis cliquez sur **Suivant**.

    h. Sélectionnez **Magasin de certificats personnel**, puis cliquez sur **Suivant**.

    i. Cliquez sur **Terminer**. Cette opération importe le certificat d’autorité d’inscription dans le magasin Ordinateur local-Personnel, ainsi que sa clé privée.  

6. Exportez et importez le certificat de clé privée :

    a. Développez **Certificats (Ordinateur local)** > **Personnel** > **Certificats**.

    b. Sélectionnez le certificat qui a été importé à l’étape précédente.

    c. Cliquez avec le bouton droit sur le certificat et sélectionnez **Toutes les tâches** > **Exporter**.

    d. Cliquez sur **Suivant** et tapez le mot de passe.

    e. Sélectionnez l’emplacement d’exportation et cliquez sur **Terminer**.

    f. Suivez la même procédure qu’à l’étape 5 pour importer le certificat de clé privée dans le magasin Ordinateur local-Personnel.

7. Copiez l’empreinte du certificat d’autorité d’inscription sans les espaces.  Voici un exemple d’empreinte :

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > Si vous rencontrez des problèmes pour récupérer le certificat d’autorité d’inscription auprès de l’AC Symantec, contactez le service clientèle de Symantec.

## <a name="install-intune-certificate-connector"></a>Installer Intune Certificate Connector

Si vous utilisez déjà la dernière version d’Intune Certificate Connector pour une AC Microsoft existante et que vous souhaitez ajouter la prise en charge de l’AC Symantec, ignorez cette étape. Sinon, téléchargez la dernière version d’Intune Certificate Connector sur le portail d’administration Intune et suivez ces instructions.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, sélectionnez **Configuration de l’appareil**.
4. Dans le volet **Configuration de l’appareil**, sélectionnez **Autorité de certification**.
5. Cliquez sur **Ajouter** et sélectionnez **Télécharger le fichier du connecteur**. Enregistrez le fichier téléchargé à un emplacement accessible à partir du serveur où vous effectuerez l’installation. 
3. Exécutez NDESConnectorSetup.exe avec des privilèges élevés.

    a. Sur l’écran **Options d’installation**, sélectionnez **Distribution PFX** comme dans la capture d’écran suivante.  Terminez le reste de la configuration avec les sélections par défaut.

   > [!IMPORTANT]
   > Si vous souhaitez configurer Intune Certificate Connector de façon à ce qu’il émette des certificats à partir d’une AC Microsoft et d’une AC Symantec, sélectionnez **Distribution de profils SCEP et PFX**. Terminez le reste de la configuration avec les sélections par défaut.

   ![Installation de Connector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Configurer Intune Certificate Connector

Par défaut, Intune Certificate Connector est installé à l’emplacement `%ProgramFiles%\Microsoft Intune`.

1. Ouvrez le fichier %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config dans le Bloc-notes.

    a. Remplacez la valeur de clé RACertThumbprint par celle de l’empreinte du certificat que vous avez copiée dans la section précédente.  Voici un exemple :

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. Enregistrez et fermez le fichier.

2. Ouvrez services.msc.

    a. Sélectionnez **Service Intune Connector**.

    b. Arrêtez, puis démarrez le service.

    c. Fermez la fenêtre Services.

## <a name="setup-the-intune-administrator-account"></a>Configurer le compte d’administrateur Intune

Si vous utilisez déjà Intune Certificate Connector pour une AC Microsoft existante et que vous souhaitez ajouter la prise en charge de l’AC Symantec, ignorez cette étape et passez aux étapes restantes. 

1. Démarrez l’interface utilisateur NDES Connector à cet emplacement : ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe `.

    a. Cliquez sur l’onglet **Inscription**, puis sur **Se connecter**.

    b. Saisissez vos informations d’identification d’administration de client Intune dans les zones de texte correspondantes.

    c. Cliquez sur **Se connecter**.  Une boîte de dialogue de confirmation s’affiche, avec un message **Inscription réussie** comme dans la capture d’écran suivante.
2. Fermez l’interface utilisateur NDES Connector.

![Configuration de Connector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>Créer un profil de certificat approuvé

Les certificats PKCS déployés pour les appareils gérés par Intune doivent être enchaînés avec un certificat racine approuvé. Cela oblige à créer un profil de certificat approuvé Intune avec le certificat racine obtenu auprès de l’AC Symantec.

1. Récupérez un certificat racine approuvé auprès de l’AC Symantec :

    a. Ouvrez une session sur le portail d’administration de l’AC Symantec.

    b. Cliquez sur Gérer les AC dans Tâches :

    c. Sélectionnez l’AC correspondante dans la liste des AC.

    d. Cliquez sur Télécharger le certificat racine pour télécharger le certificat racine approuvé.

2. Créez un profil de certificat approuvé dans le portail d’administration Intune :

    a. Connectez-vous au [Portail Azure](https://portal.azure.com) avec les informations d’identification d’administration du client Intune et recherchez les ressources Intune.

    b. Créez un profil de certificat approuvé dans **Microsoft Intune** > **Configuration de l’appareil** > **Profils** > **Créer un profil**.

    c. Saisissez les informations requises dans les champs **Nom** et **Description**, puis sélectionnez la plateforme cible. 

    d. Sélectionnez le Profil de certificat approuvé dans la liste déroulante Type de profil.

    e. Téléchargez le certificat racine approuvé que vous avez obtenu auprès de l’AC Symantec, à l’étape précédente.

    f. Suivez les étapes restantes de création du profil. 

    g. Cliquez sur **Affectations** et sélectionnez le groupe concerné.  Au moins un utilisateur ou un appareil doit faire partie du groupe affecté.

## <a name="get-the-certificate-profile-oid"></a>Récupérer l’OID du profil de certificat

L’OID du profil de certificat est associé à un modèle de profil de certificat dans l’AC Symantec.  Pour créer un profil de certificat PKCS sur le portail d’administration Intune, le nom du modèle de certificat doit être fourni sous la forme d’un OID de profil de certificat associé à un modèle de certificat dans l’AC Symantec.

1. Ouvrez une session sur le portail d’administration de l’AC Symantec.
2. Cliquez sur Gérer les profils de certificats.
3. Sélectionnez le profil de certificat que vous voulez utiliser.
4. Copiez l’OID du profil de certificat. Il se présente sous la forme suivante :

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > Si vous rencontrez des problèmes pour récupérer l’OID du profil de certificat, contactez le service clientèle de Symantec.

## <a name="create-a-pkcs-certificate-profile"></a>Créer un profil de certificat PKCS

1. Connectez-vous au [Portail Azure](https://portal.azure.com) avec vos informations d’identification d’administration de client Intune et recherchez les ressources Intune.
2. Créez un profil de certificat PKCS dans **Microsoft Intune** > **Configuration de l’appareil > Profils** > **Créer un profil**.

    a. Saisissez les informations requises dans les champs **Nom** et **Description**, puis sélectionnez la plateforme cible.

    b. Sélectionnez le **Profil de certificat PKCS** dans la liste déroulante **Type de profil**.  

    c. Suivez les étapes restantes pour créer le profil.

   ![Configuration du profile][ConfigureProfile]

   > [!IMPORTANT]
   > Les paramètres suivants du profil de certificat PKCS doivent être configurés avec les valeurs spécifiées dans le tableau suivant, comme dans la capture d’écran ci-dessous, pour pouvoir émettre des certificats PKCS par le biais d’Intune Certificate Connector à partir de l’AC Symantec. 

    |Paramètre du certificat PKCS | Valeur | Description |
    | --- | --- | --- |
    | Autorité de certification | pki-ws.symauth.com | Cette valeur doit être le nom de domaine complet du service de base de l’AC Symantec, sans les barres obliques de fin.  Si vous n’avez pas la certitude qu’il s’agisse du bon nom de domaine complet du service de base pour votre abonnement à l’AC Symantec, contactez le service clientèle de Symantec. <br><br> Si ce nom de domaine complet est incorrect, Intune Certificate Connector n’émet pas de certificats PKCS à partir de l’AC Symantec.| 
    | Nom de l’autorité de certification | Symantec | Cette valeur doit être la chaîne **Symantec**. <br><br> Si elle est modifiée, Intune Certificate Connector n’émettra pas de certificats PKCS à partir de l’AC Symantec.|
    | Nom du modèle de certificat | OID du profil de certificat provenant de l’AC Symantec. <br><br> Ex. : `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| Cette valeur doit être un OID de profil de certificat obtenu dans la section précédente à partir du modèle de profil de certificat de l’AC Symantec. <br><br> Si Intune Certificate Connector ne trouve pas de modèle de certificat associé à cet OID de profil de certificat dans l’AC Symantec, il n’émettra pas de certificats PKCS à partir de l’AC Symantec.|

   > [!NOTE]
   > Il n’est pas nécessaire d’associer les profils de certificats PKCS des plateformes Windows à un profil de certificat approuvé. Cette opération est toutefois requise pour les profils de plateformes autres que Windows, comme Android.

3. Cliquez sur **Affectations** et sélectionnez le groupe concerné.  Au moins un utilisateur ou un appareil doit faire partie du groupe affecté.
 
À l’issue des étapes précédentes, Intune Certificate Connector émettra des certificats PKCS à partir de l’AC Symantec, sur les appareils gérés par Intune du groupe affecté. Ces certificats seront disponibles dans le magasin Personnel du magasin de certificats Utilisateur actuel de l’appareil géré par Intune.

### <a name="pkcs-certificate-profile-supported-attributes"></a>Attributs pris en charge par les profils de certificats PKCS

|Attribut | Formats pris en charge par Intune | Formats pris en charge par l’AC Symantec Cloud | Résultat |
| --- | --- | --- | --- |
| Nom de sujet |Intune prend en charge le nom de l’objet aux formats suivants uniquement : <br><br> 1. Nom commun <br> 2. Nom commun (adresse e-mail incluse) <br> 3. Nom commun comme adresse e-mail <br><br> Voici un exemple : <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | L’AC Symantec prend en charge des attributs supplémentaires.  Si vous souhaitez sélectionner des attributs supplémentaires, ils doivent avoir des valeurs fixes dans le modèle de profil de certificat Symantec.| Nous utilisons le Nom commun ou l’adresse e-mail de la demande de certificat PKCS. <br><br> La moindre différence de sélection d’attributs entre le profil de certificat Intune et le modèle de profil de certificat Symantec empêche l’émission de certificats par l’AC Symantec.|
| SAN | Intune prend en charge uniquement les valeurs de champs SAN suivantes : <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (valeur encodée) | L’AC Symantec Cloud prend également en charge ces paramètres. Si vous souhaitez sélectionner des attributs supplémentaires, ils doivent avoir des valeurs fixes dans le modèle de profil de certificat Symantec. <br><br> AltNameTypeEmail : Si ce type est introuvable dans le champ SAN, il utilise la valeur d’AltNameTypeUpn.  Si AltNameTypeUpn est également introuvable dans le champ SAN, il utilise la valeur Nom de l’objet, à condition que celle-ci soit au format adresse e-mail.  Si elle est elle aussi introuvable, Intune Certificate Connector ne parvient pas à émettre les certificats. <br><br> Ex. : `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn : Si ce type est introuvable dans le champ SAN, il utilise la valeur d’AltNameTypeEmail. Si AltNameTypeEmail est également introuvable dans le champ SAN, il utilise la valeur Nom de l’objet, à condition que celle-ci soit au format adresse e-mail.  Si elle est elle aussi introuvable, Intune Certificate Connector ne parvient pas à émettre les certificats.  <br><br> Ex. : `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName : Si ce type est introuvable dans le champ SAN, Intune Certificate Connector ne parvient pas à émettre les certificats. <br><br> Ex. : `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **Remarque importante :** La valeur de ce champ est prise en charge par l’AC Symantec uniquement dans un format encodé (valeur hexadécimale). Quelle qu’elle soit, Intune Certificate Connector la convertit donc au codage base 64 avant d’envoyer la demande de certificat. **Intune Certificate Connector ne vérifie pas si cette valeur est déjà encodée.** | Aucune |

## <a name="troubleshooting"></a>Résolution des problèmes

Les journaux du service Intune Certificate Connector sont disponibles à l’emplacement `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` sur l’ordinateur NDES Connector. Ouvrez-les dans [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) et recherchez les messages d’erreur et d’exception.

| Émission/message d’erreur | Étapes de résolution |
| --- | --- |
| Impossible de se connecter avec un compte Administrateur client Intune sur l’interface utilisateur NDES Connector | Cela peut se produire lorsque Certificate Connector n’est pas activé en local sur le portail d’administration Intune. Pour résoudre ce problème, procédez comme suit : <br><br> Sur l’interface utilisateur Silverlight : <br> 1. Ouvrez une session sur le [Portail d’administration Intune](https://admin.manage.microsoft.com). <br> 2. Cliquez sur ADMIN. <br> 3. Sélectionnez Gestion des appareils mobiles > Certificate Connector. <br> 4. Cliquez sur **Configurer Certificate Connector en local**. <br> 5. Cochez la case **Activer Certificate Connector**. <br> 6. Cliquez sur **OK**. <br><br>Ou <br><br> Sur l’interface utilisateur du Portail Azure : <br> 1. Connectez-vous au [Portail Azure](https://portal.azure.com). <br> 2. Accédez à Microsoft Intune. <br> 3. Sélectionnez **Configuration de l’appareil** > **Autorité de certification** <br> 4. Cliquez sur **Activer**. <br><br> Après avoir suivi les étapes précédentes sur l’interface utilisateur Silverlight ou sur le Portail Azure, essayez de vous connecter avec le même compte Administrateur client Intune sur l’interface utilisateur NDES Connector. |
| Certificat NDES Connector introuvable. <br><br> System.ArgumentNullException : La valeur ne peut pas être null. | Intune Certificate Connector affiche cette erreur si le compte Administrateur client Intune n’a jamais été connecté à l’interface utilisateur NDES Connector. <br><br> Si cette erreur persiste, redémarrez Intune Service Connector. <br><br> 1. Ouvrez services.msc. <br> 2. Sélectionnez **Service Intune Connector**. <br> 3. Cliquez avec le bouton droit et sélectionnez **Redémarrer**.|
| NDES Connector - IssuePfx - Exception générique : <br> System.NullReferenceException : La référence d’objet n’a pas pour valeur une instance d’un objet. | Cette erreur est temporaire. Redémarrez Intune Service Connector. <br><br> 1. Ouvrez services.msc. <br> 2. Sélectionnez **Service Intune Connector**. <br> 3. Cliquez avec le bouton droit et sélectionnez **Redémarrer**. |
| Fournisseur Symantec - Impossible de récupérer la stratégie Symantec « L’opération a expiré. » | Intune Certificate Connector a reçu une erreur d’expiration du délai d’attente de l’opération lors de la communication avec l’AC Symantec. Si cette erreur persiste, augmentez la valeur du délai de connexion, puis réessayez. <br><br> Pour augmenter le délai de connexion : <br> 1. Accédez à l’ordinateur NDES Connector. <br>2. Ouvrez le fichier `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` dans le Bloc-notes. <br> 3. Augmentez la valeur du délai d’attente pour le paramètre suivant : <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Redémarrez le service Intune Connector. <br><br> Si le problème persiste, contactez le service clientèle de Symantec. |
| Fournisseur Symantec - Impossible de récupérer le certificat client | Intune Certificate Connector n’est pas parvenu à récupérer le certificat d’autorisation d’accès aux ressources dans le magasin de certificats Ordinateur local-Personnel. Pour résoudre ce problème, veillez à installer le certificat d’autorisation d’accès aux ressources dans le magasin de certificats Ordinateur local-Personnel avec sa clé privée. <br><br> **Remarque :** Le certificat d’autorisation d’accès aux ressources s’obtient auprès de l’AC Symantec. Pour plus d’informations, contactez le service clientèle de Symantec. | 
| Fournisseur Symantec - Impossible de récupérer la stratégie Symantec « La requête a été interrompue : Impossible de créer un canal sécurisé SSL/TLS. » | Cette erreur se produit dans les scénarios suivants : <br><br> 1. Le service Intune Certificate Connector ne dispose des autorisations suffisantes pour lire le certificat d’autorisation d’accès aux ressources ainsi que sa clé privée dans le magasin de certificats Ordinateur local-Personnel. Pour résoudre ce problème, vérifiez le contexte d’exécution du service Connector dans services.msc. Le service doit s’exécuter sous le contexte NT AUTHORITY\SYSTEM. <br><br> 2. Le profil de certificat PKCS dans le portail d’administration Intune est peut-être configuré avec un nom de domaine complet non valide pour le service de base de l’AC Symantec. Le nom de domaine complet se présente ainsi : `pki-ws.symauth.com`. Pour résoudre ce problème, vérifiez auprès du service clientèle de Symantec que l’URL est correcte pour votre abonnement. <br><br> 3. Intune Certificate Connector ne parvient pas à s’authentifier auprès de l’AC Symantec avec le certificat d’autorisation d’accès aux ressources, car il n’est pas en mesure de récupérer sa clé privée. Pour résoudre ce problème, veillez à installer le certificat d’autorisation d’accès aux ressources ainsi que sa clé privée dans le magasin de certificats Ordinateur local-Personnel. <br><br> Si le problème persiste, contactez le service clientèle de Symantec. |
| Fournisseur Symantec - Impossible de récupérer la stratégie de Symantec « L’un des éléments de la demande n’est pas compréhensible. » | Intune Certificate Connector n’est pas parvenu à récupérer le modèle de profil de certificat Symantec, car l’OID du profil client ne correspond pas au profil de certificat Intune. Dans un autre cas de figure, Intune Certificate Connector ne parvient pas à trouver le modèle de profil de certificat associé à l’OID du profil client donné dans l’AC Symantec. <br><br> Pour résoudre ce problème, veillez à récupérer le bon OID de profil client à partir du modèle de certificat Symantec dans l’AC Symantec. Ensuite, mettez à jour le profil de certificat PKCS dans le portail d’administration Intune. <br><br> Récupérez l’OID du profil de certificat provenant de l’AC Symantec : <br> 1. Ouvrez une session sur le portail d’administration de l’AC Symantec. <br> 2. Cliquez sur Gérer les profils de certificats. <br> 3. Sélectionnez le profil de certificat que vous voulez utiliser. <br> 4. Récupérez l’OID du profil de certificat. Il se présente sous la forme suivante : <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Mettez à jour le profil de certificat PKCS avec l’OID du profil de certificat correspondant : <br>1. Ouvrez une session sur le portail d’administration Intune. <br> 2. Accédez au profil de certificat PKCS et cliquez sur **Modifier**. <br> 3. Mettez à jour l’OID du profil de certificat dans le champ Nom du modèle de certificat. <br> 4. Enregistrez le profil de certificat PKCS. |
| Fournisseur Symantec - Échec de la vérification de la stratégie. <br><br> L’attribut ne fait pas partie de la liste d’attributs de modèle de certificat pris en charge par Symantec. | L’AC Symantec affiche ce message en cas de différence entre le modèle de profil de certificat Symantec et le profil de certificat Intune. Ce problème est probablement dû à une incompatibilité d’attribut dans SubjectName ou SubjectAltName. <br><br> Pour résoudre ce problème, veillez à sélectionner des attributs pris en charge par Intune pour SubjectName et SubjectAltName dans le modèle de profil de certificat Symantec. Pour plus d’informations, consultez les attributs pris en charge par Intune dans la section Paramètres des certificats. |
| Certains appareils Utilisateur ne reçoivent pas de certificats PKCS de la part de l’AC Symantec. | Ce problème se produit lorsque l’UPN Utilisateur contient des caractères spéciaux comme des traits de soulignement (exemple : `global_admin@intune.onmicrosoft.com`). <br><br> L’AC Symantec ne prend pas en charge les caractères spéciaux dans mail_firstname et mail_lastname. <br><br> Pour résoudre ce problème, suivez les étapes ci-dessous : <br><br> 1.   Ouvrez une session sur le portail d’administration de l’AC Symantec. <br> 2. Accédez à Gérer les profils de certificats. <br> 3.   Cliquez sur le profil de certificat utilisé pour Intune. <br> 4.  Cliquez sur le lien Options de personnalisation. <br> 5.   Cliquez sur le bouton Options Avancées. <br> 6.  Sous les champs Certificat – Nom de domaine de l’objet, ajoutez le champ Nom commun (CN) et supprimez le champ Nom commun (CN) existant. L’ajout et la suppression doivent être réalisés simultanément. <br> 7.    Cliquez sur Enregistrer. <br><br> Avec la modification précédente, le profil de certificat Symantec demande « CN =<upn> » au lieu de mail_firstname et mail_lastname. |
| L’utilisateur a supprimé manuellement de l’appareil un certificat déjà déployé. | Intune redéploie le même certificat pendant l’archivage suivant ou l’application des stratégies suivante. Dans ce cas, NDES Connector ne reçoit pas de demande de certificat PKCS. |

## <a name="next-steps"></a>Étapes suivantes

- Utilisez les informations de cet article et celles de la page [Qu’est-ce qu’un profil d’appareil Microsoft Intune ?](device-profiles.md) pour gérer les appareils de votre organisation et les certificats dont ils disposent.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Installer Intune Certificate Connector et sélectionner Distribution PFX"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Configurer Intune Certificate Connector"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Créer un profil de certificat PKCS sur le Portail Azure"
