---
title: Utiliser des certificats de clés publiques et privées dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des certificats PKCS (Public Key Cryptography Standards) avec Microsoft Intune. Cela inclut l’utilisation de certificats racines et de modèles de certificats, l’installation d’Intune Certificate Connector (NDES) et de profils de configuration d’appareil pour un certificat PKCS.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3db085e6e88f8f57eb0276afa77290df8574568f
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801706"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurer et utiliser des certificats PKCS avec Intune

Intune prend en charge l’utilisation de certificats de paires de clé privée et publique (PKCS). Cet article peut vous aider à configurer l’infrastructure requise, telle que les connecteurs de certificat locaux, à exporter un certificat PKCS, puis à ajouter le certificat à un profil de configuration d’appareil Intune.

Microsoft Intune inclut des paramètres intégrés afin d’utiliser les certificats PKCS pour l’accès aux ressources de votre organisation et l’authentification. Les certificats servent à authentifier et à sécuriser l’accès à vos ressources d’entreprise, telles qu’un réseau privé virtuel ou Wi-Fi. Vous déployez ces paramètres sur les appareils à l’aide de profils de configuration d’appareil dans Intune.

Pour plus d’informations sur l’utilisation des certificats PKCS importés, consultez [Certificats PFX importés](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Configuration requise

Pour utiliser des certificats PKCS avec Intune, vous devez disposer de l’infrastructure suivante :

- **Domaine Active Directory** :  
  tous les serveurs listés dans cette section doivent être joints à votre domaine Active Directory.

  Pour plus d’informations sur l’installation et la configuration des services AD DS (Active Directory Domain Services), consultez [Planification et conception des services AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autorité de certification** :  
   autorité de certification d’entreprise.

  Pour obtenir des informations sur l’installation et la configuration des services de certificats Active Directory (AD CS), consultez [Guide pas à pas des services de certificats Active Directory](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > Intune impose d’exécuter AD CS avec une autorité de certification (AC) d’entreprise, et non avec une AC autonome.

- **Un client** :  
  pour se connecter à l’autorité de certification d’entreprise.

- **Certificat racine** :  
  Une copie exportée de votre certificat racine provenant de votre AC d’entreprise.

- **Microsoft Intune Certificate Connector** (également appelé *connecteur de certificats NDES*) :  
  Dans le portail Intune, accédez à **Configuration de l’appareil** > **Connecteurs de certificat** > **Ajouter** et suivez les *Étapes d’installation du connecteur pour PKCS #12*. Utilisez le lien de téléchargement dans le portail pour démarrer le téléchargement du programme d’installation du connecteur de certificat **NDESConnectorSetup.exe**.  

  Intune prend en charge jusqu’à 100 instances de ce connecteur par locataire. Chaque instance du connecteur doit se trouver sur un serveur Windows distinct. Vous pouvez installer une instance de ce connecteur sur le même serveur qu’une instance du connecteur de certificats PFX pour Microsoft Intune. Lorsque vous utilisez plusieurs connecteurs, l’infrastructure des connecteurs prend en charge la haute disponibilité et l’équilibrage de charge, puisque n’importe quelle instance de connecteur disponible peut traiter vos demandes de certificat PKCS. 

  Ce connecteur traite les demandes de certificat PKCS utilisées pour l’authentification ou la signature des e-mails S/MIME.

  Microsoft Intune Certificate Connector prend également en charge le mode FIPS (Federal Information Processing Standard). FIPS n’est pas obligatoire, mais il vous permet d’émettre et de révoquer des certificats.

- **PFX Certificate Connector pour Microsoft Intune** :  
  Si vous envisagez d’utiliser le chiffrement d’e-mail S/MIME, recourez au portail Intune pour télécharger le connecteur *PFX Certificate Connector* qui prend en charge l’importation de certificats PFX.  Accédez à **Configuration de l’appareil** > **Connecteurs de certificat** > **Ajouter** et suivez les *Étapes d’installation du connecteur pour les certificats PFX importés*. Utilisez le lien de téléchargement dans le portail pour démarrer le téléchargement du programme d’installation **PfxCertificateConnectorBootstrapper.exe**. 

  Chaque abonné Intune prend en charge une seule instance de ce connecteur. Vous pouvez installer ce connecteur sur le même serveur qu’une instance de Microsoft Intune Certificate Connector.

  Ce connecteur gère les demandes des fichiers PFX importés dans Intune en vue de chiffrer les e-mails S/MIME pour un utilisateur spécifique.  

  Ce connecteur peut automatiquement se mettre à jour quand de nouvelles versions deviennent disponibles. Pour utiliser la fonctionnalité de mise à jour, vous devez :
  - Installez le connecteur PFX Certificate Connector pour Microsoft Intune sur votre serveur.  
  - Vérifier que des pare-feux sont ouverts autorisant le connecteur à contacter **autoupdate.msappproxy.net** sur le port **443**, pour recevoir automatiquement les mises à jour importantes.   

  Pour plus d’informations sur les points de terminaison réseau auxquels Intune et le connecteur accèdent, consultez [Points de terminaison réseau pour Microsoft Intune](../fundamentals/intune-endpoints.md).

- **Windows Server** :  
  Vous utilisez un serveur Windows pour héberger :

  - Microsoft Intune Certificate Connector pour les scénarios d’authentification et de signature des e-mails S/MIME
  - PFX Certificate Connector pour Microsoft Intune pour les scénarios de chiffrement des e-mails S/MIME

  Intune prend en charge l’installation du connecteur *PFX Certificate Connector* sur le même réseau que celui où est installé *Microsoft Intune Certificate Connector*.
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exporter le certificat racine à partir de l’AC d’entreprise

Pour l’authentification d’un appareil auprès d’un VPN, d’un réseau Wi-Fi ou d’autres ressources, cet appareil a besoin d’un certificat d’autorité de certification intermédiaire ou racine. Les étapes suivantes expliquent comment récupérer le certificat requis auprès de l’AC d’entreprise concernée.

**Utiliser une ligne de commande** :  
1. Connectez-vous au serveur d’autorité de certification racine avec un compte administrateur.
 
2. Accédez à **Démarrer** > **Exécuter**, puis entrez **Cmd** pour ouvrir l’invite de commandes. 
    
3. Spécifiez **certutil -ca.cert ca_name.cer** pour exporter le certificat racine dans un fichier nommé *ca_name.cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Configurer les modèles de certificats sur l’autorité de certification

1. Connectez-vous à votre AC d’entreprise avec un compte disposant de privilèges administratifs.
2. Ouvrez la console **Autorité de certification**, cliquez avec le bouton droit sur **Modèles de certificats** et sélectionnez **Gérer**.
3. Recherchez le modèle de certificat **Utilisateur**, cliquez dessus avec le bouton droit et choisissez **Dupliquer le modèle** pour ouvrir **Propriétés du nouveau modèle**.

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
11. Sélectionnez **Appliquer** > **OK** pour enregistrer le modèle de certificat. Fermez la **Console Modèles de certificat**.
12. Dans la console **Autorité de certification**, cliquez avec le bouton droit sur **Modèles de certificats** > **Nouveau** > **Modèle de certificat à délivrer**. Choisissez le modèle que vous avez créé dans les étapes précédentes. Sélectionnez **OK**.
13. Pour que le serveur gère les certificats pour les utilisateurs et appareils inscrits, suivez ces étapes :

    1. Cliquez avec le bouton droit sur l’autorité de certification et sélectionnez **Propriétés**.
    2. Sous l’onglet Sécurité, ajoutez le compte d’ordinateur du serveur sur lequel vous exécutez les connecteurs (**Microsoft Intune Certificate Connector** ou **PFX Certificate Connector pour Microsoft Intune**). 
    3. Accordez les autorisations **Émettre et gérer des certificats** et **Demander des certificats** au compte d’ordinateur.

14. Déconnectez-vous de l’AC d’entreprise.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Télécharger, installer et configurer Microsoft Intune Certificate Connector

> [!IMPORTANT]  
> Microsoft Intune Certificate Connector ne pouvant pas être installé sur l’autorité de certification émettrice, vous devez l’installer sur un serveur Windows distinct.  

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Administration client** > **Connecteurs et jetons** > **Connecteurs de certificat** >  **+ Ajouter**.

3. Cliquez sur *Téléchargez le logiciel du connecteur de certificat* pour le connecteur de PKCS #12, puis enregistrez le fichier à un emplacement accessible à partir du serveur où vous installerez le connecteur.

   ![Microsoft Intune Certificate Connector : télécharger](./media/certficates-pfx-configure/download-ndes-connector.png)
 
4. Une fois le téléchargement terminé, connectez-vous au serveur. Ensuite :

    1. Vérifiez que le .NET Framework 4.5 (ou version ultérieure) est installé, car il est nécessaire pour le connecteur NDES Certificate. Le .NET Framework 4.5 est automatiquement inclus avec Windows Server 2012 R2 et ses versions plus récentes.
    2. Exécutez le programme d’installation (NDESConnectorSetup.exe) et acceptez l’emplacement par défaut. Le connecteur est installé dans `\Program Files\Microsoft Intune\NDESConnectorUI`. Dans Options du programme d’installation, sélectionnez **Distribution PFX**. Continuez et terminez l’installation.
    3. Par défaut, le service du connecteur s’exécute sous le compte système local. Si un proxy est exigé pour accéder à Internet, vérifiez que le compte de service local peut accéder aux paramètres de proxy du serveur.

5. Microsoft Intune Certificate Connector prend en charge l’onglet **Inscription**. Pour activer la connexion à Intune, sélectionnez **Connexion** et spécifiez un compte disposant d’autorisations d’administrations globales.
6. Sous l’onglet **Avancé**, laissez l’option **Utiliser le compte SYSTÈME de cet ordinateur (par défaut)** sélectionnée.
7. **Appliquer** > **Fermer**
8. Revenez au portail Intune (**Intune** > **Configuration de l’appareil** > **Connecteurs de certification**). Après quelques instants, une coche verte apparaît et **État de la connexion** indique **Active**. Votre serveur de connecteur peut désormais communiquer avec Intune.
9. Si vous avez un proxy web dans votre environnement réseau, vous devrez peut-être procéder à des configurations supplémentaires pour que le connecteur fonctionne. Pour plus d’informations, consultez [Utiliser des serveurs proxy locaux existants](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) dans la documentation d’Azure Active Directory.

> [!NOTE]  
> Microsoft Intune Certificate Connector prend en charge TLS 1.2. Si TLS 1.2 est installé sur le serveur qui héberge le connecteur, ce dernier utilise TLS 1.2. Sinon, TLS 1.1 est utilisé. Actuellement, TLS 1.1 est utilisé pour l’authentification entre les appareils et le serveur.

## <a name="create-a-trusted-certificate-profile"></a>Créer un profil de certificat approuvé

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

   ![Accéder à Intune et créer un profil pour un certificat approuvé](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Entrez les propriétés suivantes :

    - le **Nom** du profil ;
    - une description (facultatif) ;
    - la **Plateforme** sur laquelle le profil sera déployé ;
    - **Type de profil** : **Certificat approuvé**.

4. Sélectionnez **Paramètres**, puis spécifiez le fichier .cer du certificat d’autorité de certification racine que vous avez exporté.

   > [!NOTE]
   > En fonction de la plateforme que vous avez choisie à l’**Étape 2**, vous n’aurez pas forcément la possibilité de choisir le **Magasin de destination** du certificat.

   ![Créer un profil et charger un certificat approuvé](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png)

5. Sélectionnez **OK** > **Créer** pour enregistrer votre profil.

6. Pour affecter le nouveau profil à un ou plusieurs appareils, consultez [Affecter des profils d’appareils Microsoft Intune](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Créer un profil de certificat PKCS

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez et accédez à **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Entrez les propriétés suivantes :

    - le **Nom** du profil ;
    - une description (facultatif) ;
    - la **Plateforme** sur laquelle le profil sera déployé ;
    - Définissez **Type de profil** sur **Certificat PKCS**.

4. Sélectionnez **Paramètres**, puis configurez les propriétés qui s’appliquent à la plateforme que vous avez sélectionnée :
   
   |Paramètre     | Plate-forme     | Détails   |
   |------------|------------|------------|
   |**Seuil de renouvellement (%)**        |Tous         |La valeur recommandée est 20 %  | 
   |**Période de validité du certificat**  |Tous         |si vous n’avez pas changé le modèle de certificat, cette option peut être définie sur un an. |
   |**Fournisseur de stockage de clés (KSP)**   |Windows 10  | pour Windows, sélectionnez l’emplacement où stocker les clés sur l’appareil. |
   |**Autorité de certification**      |Tous         |nom de domaine complet (FQDN) interne de l’autorité de certification d’entreprise.  |
   |**Nom de l’autorité de certification** |Tous         |indique le nom de l’autorité de certification d’entreprise, par exemple « Autorité de certification Contoso ». |
   |**Type de certificat**             |macOS       |Sélectionnez un type : <br> **-** L’objet et le SAN d’un certificat **Utilisateur** peuvent contenir des attributs d’utilisateur et d’appareil. <br><br>**-** L’objet et le SAN d’un certificat de type **Appareil** peuvent contenir uniquement des attributs d’appareil. Utilisez Appareil dans des scénarios de type appareils sans utilisateur, tels que des kiosques ou d’autres appareils partagés.  <br><br> Cette sélection affecte le format du nom de l’objet. |
   |**Format du nom de l’objet**          |Tous         |Pour la plupart des plateformes, définissez cette option sur **Nom commun**, sauf indication contraire.<br><br>Pour macOS, le format du nom de l’objet est déterminé par le type de certificat. Consultez [Format du nom de l’objet pour macOS](#subject-name-format-for-macos) plus loin dans cet article. |
   |**Autre nom de l’objet**     |Tous         |définissez cette option sur **Nom d’utilisateur principal (UPN)** , sauf indication contraire. |
   |**Utilisation avancée de la clé**           |**-** Administrateur d’appareil Android <br>**-** Android Entreprise (*Propriétaire d’appareil*, *Profil professionnel*) <br> **-** Windows 10 |Habituellement, les certificats exigent une *authentification client* afin que l’utilisateur ou l’appareil puisse s’authentifier auprès d’un serveur. |
   |**Autoriser toutes les applications à accéder à la clé privée** |macOS  |Affectez la valeur **Activer** pour accorder aux applications configurées pour l’appareil Mac associé l’accès à la clé privée des certificats PKCS. <br><br> Pour plus d’informations sur ce paramètre, consultez *AllowAllAppsAccess*, la section sur la charge utile de certificat de [référence de profil de configuration](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf), dans la documentation pour les développeurs Apple. |
   |**Certificat racine**             |**-** Administrateur d’appareil Android <br> **-** Android Entreprise (*Propriétaire d’appareil*, *Profil professionnel*) |Sélectionnez un profil de certificat d’autorité de certification racine qui a été précédemment affecté. |

5. Sélectionnez **OK** > **Créer** pour enregistrer votre profil.

6. Pour affecter le nouveau profil à un ou plusieurs appareils, consultez [Affecter des profils d’appareils Microsoft Intune](../configuration/device-profile-assign.md).

   > [!NOTE]
   > Sur les appareils dotés d’un profil Android Entreprise, les certificats installés à l’aide d’un profil de certificat PKCS ne sont pas visibles sur l’appareil. Pour confirmer le déploiement réussi du certificat, vérifiez l’état du profil dans la console Intune.

### <a name="subject-name-format-for-macos"></a>Format du nom de l’objet pour macOS

Quand vous créez un profil de certificat PKCS macOS, les options de format du nom de l’objet dépendent du type de certificat que vous sélectionnez, **Utilisateur** ou **Appareil**.  

> [!NOTE]  
> Il existe un problème connu lié à l’utilisation de PKCS pour obtenir des certificats [qui correspond au même problème détecté pour SCEP](certificates-profile-scep.md#avoid-certificate-signing-requests-with-escaped-special-characters), lorsque le nom d’objet dans la demande de signature de certificat (CSR) résultante inclut l’un des caractères suivants comme caractère d’échappement (suivi d’une barre oblique inverse \\) :
> - \+
> - ;
> - ,
> - =

- **Type de certificat Utilisateur**  
  Les options de *Format du nom de l’objet* incluent deux variables : **Nom commun (CN)** et **E-mail (E)** . **Nom courant (cn)** peut être défini sur une des variables suivantes :

  - **CN={{UserName}}** : Le nom d’utilisateur principal, par exemple, janedoe@contoso.com.
  - **CN={{AAD_Device_ID}}** : ID attribué quand vous inscrivez un appareil dans Azure Active Directory (AD). Cet ID est généralement utilisé pour l’authentification auprès d’Azure AD.
  - **CN={{SERIALNUMBER}}** : Numéro de série unique (SN) généralement utilisé par le fabricant pour identifier un appareil.
  - **CN={{IMEINumber}}** : Numéro IMEI (International Mobile Equipment Identity) unique utilisé pour identifier un téléphone mobile.
  - **CN={{OnPrem_Distinguished_Name}}** : Séquence de noms uniques relatifs séparés par une virgule, par exemple, *CN=Jane Doe,OU=UserAccounts,DC=Corp,DC=contoso,DC=com*.

    Pour utiliser la variable *{{OnPrem_Distinguished_Name}}* , synchronisez l’attribut utilisateur *onpremisesdistinguishedname* à l’aide d’[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) sur votre Azure AD.

  - **CN={{onPremisesSamAccountName}}** : Les administrateurs peuvent synchroniser l’attribut samAccountName d’Active Directory sur Azure AD à l’aide d’Azure AD Connect dans un attribut appelé *onPremisesSamAccountName*. Intune peut remplacer cette variable dans le cadre d’une demande d’émission de certificat dans l’objet d’un certificat. L’attribut samAccountName est le nom de connexion de l’utilisateur utilisé pour prendre en charge les clients et serveurs avec une version antérieure de Windows (antérieure à Windows 2000). Le format du nom de connexion de l’utilisateur est : *DomainName\testUser* ou simplement *testUser*.

    Pour utiliser la variable *{{onPremisesSamAccountName}}* , synchronisez l’attribut utilisateur *onPremisesSamAccountName* à l’aide d’[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) sur votre Azure AD.

  En combinant une ou plusieurs de ces variables et chaînes statiques, vous pouvez créer un format de nom d’objet personnalisé tel que :  
  - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**
  
  Cet exemple comprend un format de nom d’objet qui utilise les variables CN et E ainsi que des chaînes pour les valeurs Unité d’organisation, Organisation, Emplacement, Région et Pays. La page [CertStrToName function](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) (Fonction CertStrToName) illustre cette fonction et ses chaînes prises en charge.

- **Type de certificat Appareil**  
  Les options de format du nom de l’objet sont notamment les variables suivantes : 
  - **{{AAD_Device_ID}}**
  - **{{Device_Serial}}**
  - **{{Device_IMEI}}**
  - **{{SerialNumber}}**
  - **{{IMEINumber}}**
  - **{{AzureADDeviceId}}**
  - **{{WiFiMacAddress}}**
  - **{{IMEI}}**
  - **{{DeviceName}}**
  - **{{FullyQualifiedDomainName}}** *(Applicable uniquement aux appareils Windows et joints à un domaine)*
  - **{{MEID}}**

  Vous pouvez spécifier ces variables, suivies du texte de la variable, dans la zone de texte. Par exemple, le nom commun d’un appareil nommé *Device1* peut être ajouté sous la forme **CN={{DeviceName}}Device1**.

  > [!IMPORTANT]  
  > - Quand vous spécifiez une variable, mettez le nom de la variable entre accolades { }, comme indiqué dans l’exemple, pour éviter une erreur.  
  > - Les propriétés de l’appareil utilisées dans l’*objet* ou le *SAN* d’un certificat d’appareil, par exemple, **IMEI**, **SerialNumber** et **FullyQualifiedDomainName**, sont des propriétés qui peuvent être usurpées par quiconque a accès à l’appareil.
  > - Un appareil doit prendre en charge toutes les variables spécifiées dans un profil de certificat pour que ce profil s’installe sur cet appareil.  Par exemple, si **{{IMEI}}** est utilisé dans le nom d’objet d’un profil SCEP et correspond à un appareil qui n’a pas de numéro IMEI, l’installation du profil échoue.  
 


## <a name="whats-new-for-connectors"></a>Nouveautés des connecteurs

Des mises à jour pour les deux connecteurs de certificats sont régulièrement publiées. Quand nous mettons à jour un connecteur, vous pouvez découvrir ici les modifications apportées.

Le *connecteur de certificats PFX pour Microsoft Intune* [prend en charge les mises à jour automatiques](#requirements), tandis que le *conteneur de certificat Intune* est mis à jour manuellement.

### <a name="may-17-2019"></a>17 mai 2019

- **PFX Certificates Connector pour Microsoft Intune - version 6.1905.0.404**  
  Modifications de cette version :  
  - Correction d’un problème pouvant entraîner l’arrêt du traitement des nouvelles demandes par le connecteur en raison du retraitement continuel des certificats PFX existants. 

### <a name="may-6-2019"></a>6 mai 2019

- **Connecteur de certificats PFX pour Microsoft Intune - version 6.1905.0.402**  
  Modifications de cette version :  
  - L’intervalle d’interrogation pour le connecteur est réduit de cinq minutes à 30 secondes.
 
### <a name="april-2-2019"></a>2 avril 2019

- **Connecteur de certificat Intune - version 6.1904.1.0**  
  Modifications de cette version :  
  - Correction d’un problème pouvant entraîner l’échec de l’inscription du connecteur auprès d’Intune après la connexion au connecteur avec un compte d’administrateur général.  
  - Inclusion de correctifs de fiabilité pour la révocation de certificats.  
  - Inclusion de correctifs de performances pour augmenter la vitesse de traitement des demandes de certificat PKCS.  

- **Connecteur de certificats PFX pour Microsoft Intune - version 6.1904.0.401**
  > [!NOTE]  
  > La mise à jour automatique pour cette version du connecteur PFX n’est pas disponible avant le 11 avril 2019.  

  Modifications de cette version :  
  - Correction d’un problème pouvant entraîner l’échec de l’inscription du connecteur auprès d’Intune après la connexion au connecteur avec un compte d’administrateur général.  


## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](../configuration/device-profile-assign.md) et [superviser son état](../configuration/device-profile-monitor.md).

[Utilisez SCEP pour les certificats](certificates-scep-configure.md) ou [émettez des certificats PKCS à partir d’un service web du gestionnaire PKI Symantec](certificates-digicert-configure.md).
