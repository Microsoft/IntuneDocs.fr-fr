---
title: Utiliser des certificats SCEP avec Microsoft Intune - Azure | Microsoft Docs
description: Pour utiliser des certificats SCEP dans Microsoft Intune, configurez votre domaine AD local, créez une autorité de certification, configurez le serveur NDES et installez Intune Certificate Connector. Ensuite, créez un profil de certificat SCEP, puis affectez ce profil à des groupes. Consultez également les différents ID d’événement et leur description, ainsi que les codes de diagnostic pour le service du connecteur Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f5441bb15d6906257432afbfe51fffc6c11a6324
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745024"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Configurer et utiliser des certificats SCEP avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article vous montre comment configurer votre infrastructure, puis comment créer et affecter des profils de certificat SCEP (Simple Certificate Enrollment Protocol) avec Intune.

## <a name="configure-on-premises-infrastructure"></a>Configurer l’infrastructure locale

- **Domaine Active Directory** : tous les serveurs répertoriés dans cette section (à l’exception du serveur du proxy d’application web) doivent être joints à votre domaine Active Directory.

- **Autorité de certification** : une autorité de certification d’entreprise qui s’exécute sur une édition Entreprise de Windows Server 2008 R2 ou version ultérieure. Une autorité de certification autonome n'est pas prise en charge. Pour plus d’informations, consultez [Installer l’autorité de certification](http://technet.microsoft.com/library/jj125375.aspx).
    Si votre autorité de certification exécute Windows Server 2008 R2, vous devez [installer le correctif logiciel à partir de KB2483564](http://support.microsoft.com/kb/2483564/).

- **Serveur NDES** : sur un serveur qui exécute Windows Server 2012 R2 ou version ultérieure, vous devez configurer le service d’inscription de périphérique réseau (NDES). Intune ne prend pas en charge le service NDES quand il s’exécute sur un serveur qui exécute également l’autorité de certification d’entreprise. Consultez le [Guide du service d’inscription de périphérique réseau](http://technet.microsoft.com/library/hh831498.aspx) pour obtenir des instructions sur la configuration de Windows Server 2012 R2 pour héberger le service d’inscription de périphérique réseau.
Le serveur NDES doit être joint au domaine qui héberge l’autorité de certification et ne doit pas se trouver sur le même serveur que l’autorité de certification. Vous trouverez plus d’informations sur le déploiement du serveur NDES dans une forêt distincte, un réseau isolé ou un domaine interne dans [Utilisation d’un module de stratégie avec le service d’inscription de périphérique réseau](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector** : utilisez le portail Azure pour télécharger le programme d’installation de **Certificate Connector** (**ndesconnectorssetup.exe**). Vous pouvez ensuite exécuter **ndesconnectorssetup.exe** sur le serveur hébergeant le rôle de service d’inscription de périphériques réseau (NDES) où vous souhaitez installer Certificate Connector. 
- **Serveur proxy d’application web** (facultatif) : utilisez un serveur qui exécute Windows Server 2012 R2 ou version ultérieure comme serveur proxy d’application web (WAP). Cette configuration :
  -  Permet aux appareils de recevoir des certificats à l'aide d'une connexion Internet.
  -  Est une recommandation de sécurité lorsque les appareils se connectent via Internet pour recevoir et renouveler les certificats.

#### <a name="additional"></a>Supplémentaire
- Le serveur qui héberge le proxy d'application web [doit installer une mise à jour](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) qui permet la prise en charge des longues URL utilisées par le service d'inscription d'appareil réseau. Cette mise à jour est incluse dans le [correctif cumulatif de décembre 2014](http://support.microsoft.com/kb/3013769), ou individuellement à partir de l'article [KB3011135](http://support.microsoft.com/kb/3011135).
- Le serveur WAP doit avoir un certificat SSL qui correspond au nom publié sur les clients externes et approuver le certificat SSL utilisé sur le serveur NDES. Ces certificats permettent au serveur du proxy d'application web de mettre fin à la connexion SSL à partir des clients et de créer une nouvelle connexion SSL au serveur NDES.

Pour plus d’informations, consultez [Planification de certificats pour WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) et [Informations générales sur les serveurs WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="network-requirements"></a>Conditions requises en matière de réseau

Depuis Internet jusqu’au réseau de périmètre, autorisez le port 443 depuis tous les hôtes/adresses IP sur Internet vers le serveur NDES.

Depuis le réseau de périmètre jusqu’au réseau approuvé, autorisez tous les ports et protocoles requis pour l’accès au domaine sur le serveur NDES joint au domaine. Le serveur NDES a besoin d’un accès aux serveurs de certificats, aux serveurs DNS, aux serveurs Configuration Manager et aux contrôleurs de domaine.

Nous vous recommandons de publier le serveur NDES via un proxy, comme le [proxy de l’application Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), le [proxy de l’accès web](https://technet.microsoft.com/library/dn584107.aspx) ou un proxy tiers.

### <a name="certificates-and-templates"></a>Certificats et modèles

|Objet|Détails|
|----------|-----------|
|**Modèle de certificat**|Configurez ce modèle sur votre autorité de certification émettrice.|
|**Certificat d’authentification client**|Demandé auprès de votre autorité de certification émettrice ou de votre autorité de certification publique ; ce certificat doit être installé sur le serveur NDES.|
|**Certificat d’authentification serveur**|Demandé auprès de votre autorité de certification émettrice ou autorité de certification publique ; ce certificat doit être installé et lié dans IIS sur le serveur NDES.|
|**Certificat d’autorité de certification racine approuvée**|Vous devez exporter ce certificat en tant que fichier **.cer** à partir de l’autorité de certification racine ou de tout appareil qui approuve l’autorité de certification racine, puis l’affecter à des appareils à l’aide du profil de certificat d’autorité de certification approuvé.<br /><br />Vous utilisez un seul certificat d'autorité de certification racine approuvée par plateforme de système d'exploitation et l'associez à chaque profil de certificat racine approuvé que vous créez.<br /><br />Vous pouvez utiliser des certificats d'autorité de certification racine approuvée supplémentaires chaque fois que nécessaire. Par exemple, vous pouvez agir ainsi pour fournir une relation d'approbation à une autorité de certification qui signe les certificats d'authentification du serveur pour vos points d'accès Wi-Fi.|

### <a name="accounts"></a>Comptes

|Nom|Détails|
|--------|-----------|
|**Compte de service NDES**|Entrez un compte d’utilisateur de domaine à utiliser comme compte de service NDES.|

## <a name="configure-your-infrastructure"></a>Configurer votre infrastructure
Pour pouvoir configurer des profils de certificat, effectuez d’abord les tâches suivantes. Pour effectuer ces tâches, vous devez connaître Windows Server 2012 R2 et les services de certificats Active Directory (AD CS) :

**Étape 1** : créer un compte de service NDES

**Étape 2** : configurer les modèles de certificats sur l’autorité de certification

**Étape 3** : configurer les composants requis du serveur NDES

**Étape 4** : configurer NDES pour une utilisation avec Intune

**Étape 5** : activer, installer et configurer Intune Certificate Connector

#### <a name="step-1---create-an-ndes-service-account"></a>Étape 1 : créer un compte de service NDES

Créez un compte d'utilisateur de domaine à utiliser comme compte de service NDES. Vous entrez ce compte quand vous configurez des modèles sur l’autorité de certification émettrice avant d’installer et de configurer NDES. Vérifiez que l’utilisateur a les droits par défaut **d’ouverture d’une session locale**, **d’ouverture d’une session en tant que service** et **d’ouverture d’une session en tant que tâche**. Certaines organisations disposent de stratégies de sécurisation renforcée qui désactivent ces droits.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>Étape 2 : configurer les modèles de certificats sur l’autorité de certification
Dans cette tâche, vous allez :

- Configurer un modèle de certificat pour NDES
- Publier le modèle de certificat pour NDES

##### <a name="configure-the-certification-authority"></a>Configurer l’autorité de certification

1. Connectez-vous en tant qu’administrateur d’entreprise.

2. Sur l’autorité de certification émettrice, utilisez le composant logiciel enfichable Modèles de certificats pour créer un modèle personnalisé. Ou, copiez un modèle existant, puis mettez-le à jour (comme le modèle Utilisateur) afin de l’utiliser avec NDES.

   >[!NOTE]
   > Le modèle de certificat NDES doit être basé sur un modèle de certificat v2 (avec compatibilité de Windows 2003).

   Le modèle doit avoir les configurations suivantes :

   - Entrez un **Nom complet du modèle** convivial pour le modèle.

   - Dans **Nom du sujet**, sélectionnez **Fournir dans la requête**. (La sécurité est appliquée par le module de stratégie Intune pour NDES.)

   - Dans **Extensions**, vérifiez que **Description des stratégies d’application** inclut **Authentification du client**.

     > [!IMPORTANT]
     > Pour les modèles de certificats iOS et macOS, sous l’onglet **Extensions**, modifiez **Utilisation de la clé** et vérifiez que l’option **Signature faisant preuve de l’origine** n’est pas sélectionnée.

   - Dans **Sécurité**, ajoutez le compte de service NDES et attribuez-lui les autorisations **Inscription** sur le modèle. Les administrateurs Intune qui créent des profils SCEP exigent des droits **en lecture** pour pouvoir accéder au modèle durant la création des profils SCEP.

     > [!NOTE]
     > Pour révoquer des certificats, le compte de service NDES a besoin de droits *Émettre et gérer des certificats* pour chaque modèle de certificat utilisé par un profil de certificat.

3. Examinez la **Période de validité** sous l'onglet **Général** du modèle. Par défaut, Intune utilise la valeur configurée dans le modèle. Toutefois, vous pouvez configurer l’autorité de certification pour permettre au demandeur d’entrer une valeur différente, que vous pouvez alors définir à partir de la console d’administration Intune. Si vous souhaitez toujours utiliser la valeur du modèle, ignorez le reste de l'étape.

   > [!IMPORTANT]
   > iOS et macOS utilisent toujours la valeur définie dans le modèle, indépendamment des autres configurations que vous effectuez.

Exemple de configuration de modèle :

![Onglet Modèle, Traitement de la demande](./media/scep_ndes_request_handling.png)

![Onglet Modèle, Nom du sujet](./media/scep_ndes_subject_name.jpg)

![Onglet Modèle, Sécurité](./media/scep_ndes_security.jpg)

![Onglet Modèle, Extensions](./media/scep_ndes_extensions.jpg)

![Onglet Modèle, Conditions d’émission](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> Pour les stratégies d’application, ajoutez uniquement les stratégies d’application requises. Confirmez vos choix avec vos administrateurs de sécurité.

Configurer l’autorité de certification et permettre au demandeur d’entrer la période de validité :

1. Sur l’autorité de certification, exécutez les commandes suivantes :
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. Sur l'autorité de certification émettrice, utilisez le composant logiciel enfichable Autorité de Certification pour publier le modèle de certificat.
   Sélectionnez le nœud **Modèles de certificats**, cliquez sur **Action** > **Nouveau** > **Modèle de certificat à délivrer**, puis sélectionnez le modèle que vous avez créé à l’étape 2.

3. Validez le modèle publié en l'affichant sous le dossier **Modèles de certificats** .

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>Étape 3 : configurer les composants requis du serveur NDES
Dans cette tâche, vous allez :

- Ajouter NDES à un serveur Windows Server et configurer IIS pour prendre en charge NDES
- Ajouter le compte de service NDES au groupe IIS_IUSR
- Définir le SPN pour le compte de service NDES

1. Sur le serveur qui héberge NDES, connectez-vous en tant **qu’administrateur d’entreprise**, puis utilisez [l’Assistant Ajout de rôles et de fonctionnalités](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) pour installer NDES :

   1. Dans l'Assistant, sélectionnez **Services de certificats Active Directory** pour accéder aux services de rôle AD CS. Sélectionnez **Service d'inscription d'appareil réseau**, décochez **Autorité de certification**, puis terminez l'Assistant.

      > [!TIP]
      > Dans **Progression de l’installation**, ne cochez pas **Fermer**. Sélectionnez à la place le lien **Configurer les services de certificats Active Directory sur le serveur de destination**. L’Assistant **Configuration AD CS** s’ouvre, que vous utilisez pour la tâche suivante. Une fois l'Assistant Configuration AD CS ouvert, vous pouvez fermer l'Assistant Ajout de rôles et de fonctionnalités.

   2. Lorsque NDES est ajouté au serveur, l'Assistant installe également IIS. Vérifiez qu'IIS a les configurations suivantes :

   3. **Serveur Web** > **Sécurité** > **Filtrage des demandes**

   4. **Serveur Web** > **Développement d’applications** > **ASP.NET 3.5**. L’installation d’ASP.NET 3.5 installe le .NET Framework 3.5. Quand vous installez .NET Framework 3.5, installez à la fois le **.NET Framework 3.5** et **Activation HTTP**.

   5. **Serveur Web** > **Développement d’applications** > **ASP.NET 4.5**. L’installation d’ASP.NET 4.5 installe le .NET Framework 4.5. Quand vous installez le .NET Framework 4.5, installez à la fois la fonctionnalité **.NET Framework 4.5** de base, **ASP.NET 4.5** et la fonctionnalité **Services WCF** > **Activation HTTP**.

   6. **Outils de gestion** > **IIS 6 Management Compatibility** > **Compatibilité avec la métabase de données IIS 6**

   7. **Outils de gestion** > **IIS 6 Management Compatibility** > **Compatibilité WMI d’IIS 6**

   8. Sur le serveur, ajoutez le compte de service NDES en tant que membre du groupe **IIS_IUSR**.

2. Dans une invite de commandes avec élévation de privilèges, exécutez la commande suivante pour définir le SPN du compte de service NDES :

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    Par exemple, si votre serveur NDES se nomme **Serveur01**, votre domaine **Contoso.com**et le compte de service **ServiceNDES**, utilisez :

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>Étape 4 : configurer NDES pour une utilisation avec Intune
Dans cette tâche, vous allez :

- Configurer NDES pour une utilisation avec l'autorité de certification émettrice
- Lier le certificat du serveur d'authentification (SSL) dans IIS
- Configurer le filtrage de demandes dans IIS

1. Sur le serveur NDES, ouvrez l’Assistant Configuration des services de certificats Active Directory, puis procédez aux mises suivantes :

    > [!TIP]
    > Si vous avez cliqué sur le lien de la tâche précédente, l'Assistant est déjà ouvert. Sinon, ouvrez le Gestionnaire de serveur pour accéder à la configuration de post-déploiement pour les services de certificats Active Directory.

   - Dans **Services de rôle**, sélectionnez le **Service d’inscription d’appareil réseau**.
   - Dans **Compte de service pour NDES**, entrez le compte de service NDES.
   - Dans **Autorité de certification pour NDES**, cliquez sur **Sélectionner**, puis sélectionnez l’autorité de certification émettrice où vous avez configuré le modèle de certificat.
   - Dans **Chiffrement pour NDES**, définissez la longueur de la clé pour répondre aux besoins de votre entreprise.
   - Dans **Confirmation**, sélectionnez **Configurer** pour terminer l’Assistant.

2. Une fois l’Assistant terminé, mettez à jour la clé de Registre suivante sur le serveur NDES :

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    Pour mettre à jour cette clé, identifiez le **rôle** du modèle de certificat (qui se trouve sous son onglet **Traitement de la demande**). Ensuite, mettez à jour l’entrée de Registre correspondante en remplaçant les données existantes par le nom du modèle de certificat (pas par le nom d’affichage du modèle) que vous avez spécifié dans la tâche 1. Le tableau suivant mappe le rôle de modèle de certificat aux valeurs du Registre :

    |Rôle de modèle de certificat (onglet Traitement de la demande)|Valeur du Registre à modifier|Valeur indiquée dans la console d’administration Intune pour le profil SCEP|
    |---|---|---|
    |Signature|SignatureTemplate|Signature numérique|
    |Chiffrement|EncryptionTemplate|Chiffrement de la clé|
    |Signature et chiffrement|GeneralPurposeTemplate|Chiffrement de la clé<br/>Signature numérique|

    Par exemple, si le rôle de votre modèle de certificat est **Chiffrement**, remplacez la valeur de **EncryptionTemplate** par le nom de votre modèle de certificat.

3. Le serveur NDES reçoit de très longues URL (requêtes), qui nécessitent l’ajout de deux entrées au Registre :


   |                        Localisation                        |      Valeur      | Type  |      Niveau       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534 (décimal) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534 (décimal) |


4. Dans le Gestionnaire IIS, sélectionnez **Site web par défaut** > **Filtrage des demandes** > **Modifier les paramètres de la fonctionnalité**. Attribuez aux paramètres **Longueur maximale des URL** et **Longueur maximale des chaînes de requête** la valeur *65534*, comme indiqué ci-après :

    ![Longueur maximale des URL et des requêtes IIS](./media/SCEP_IIS_max_URL.png)

5. Redémarrez le serveur. L’exécution de **iisreset** sur le serveur ne suffit pas pour finaliser ces changements.
6. Accédez à `http://*FQDN*/certsrv/mscep/mscep.dll`. Vous devez voir une page NDES similaire à la suivante :

    ![Page NDES test](./media/SCEP_NDES_URL.png)

    Si vous obtenez une erreur **503 Service indisponible**, consultez l’Observateur d’événements. Il est probable que le pool d’applications soit arrêté en raison de l’absence d’un droit pour l’utilisateur NDES. Ces droits sont décrits dans la tâche 1.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>Installer et lier des certificats sur le serveur NDES

1. Sur votre serveur NDES, demandez et installez un certificat d' **authentification serveur** auprès de votre autorité de certification interne ou autorité de certification publique. Vous liez ensuite ce certificat SSL dans IIS.

    > [!TIP]
    > Après avoir lié le certificat SSL dans IIS, installez un certificat d’authentification client. Ce certificat peut être émis par toute autorité de certification approuvée par le serveur NDES. Bien qu’il ne s’agisse pas d’une bonne pratique, vous pouvez utiliser le même certificat pour l’authentification serveur et l’authentification cliente tant que le certificat a les deux utilisations améliorées de la clé. Passez en revue les étapes suivantes pour plus d'informations sur ces certificats d'authentification.

   1. Après avoir obtenu le certificat d’authentification serveur, ouvrez le **Gestionnaire IIS**, puis sélectionnez le **Site web par défaut**. Dans le volet **Actions**, sélectionnez **Liaisons**.

   2. Sélectionnez **Ajouter**, définissez **Type** avec la valeur **https**, puis vérifiez que le port est **443**. Seul le port 443 est pris en charge pour la version autonome d’Intune.

   3. Pour **Certificat SSL**, entrez le certificat d’authentification serveur.

      > [!NOTE]
      > Si le serveur NDES utilise un nom interne et externe pour une adresse réseau unique, le certificat d’authentification serveur doit avoir :
      > - Un **nom d’objet** avec un nom de serveur public externe
      > - Un **autre nom de l’objet** qui inclut le nom de serveur interne

2. Sur votre serveur NDES, demandez et installez un certificat d' **authentification client** auprès de votre autorité de certification interne ou d'une autorité de certification publique. Cela peut être le même certificat que le certificat d'authentification serveur si ce certificat possède les deux fonctions.

    Le certificat d'authentification client doit avoir les propriétés suivantes :

    - **Utilisation améliorée de la clé** : cette valeur doit inclure **l’Authentification du client**

    - **Nom de l’objet** : cette valeur doit être équivalente au nom DNS du serveur sur lequel vous installez le certificat (serveur NDES)

##### <a name="configure-iis-request-filtering"></a>Configurer le filtrage des demandes IIS

1. Sur le serveur NDES, ouvrez le **Gestionnaire IIS**, sélectionnez le **Site web par défaut** dans le volet **Connexions**, puis ouvrez **Filtrage des demandes**.

2. Sélectionnez **Modifier les paramètres de la fonctionnalité**, puis définissez les valeurs :

    - **Chaîne de requête (octets)** = **65534**
    - **Longueur maximale des URL (octets)** = **65534**

3. Vérifiez la clé de Registre suivante :

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    Vérifiez que les valeurs suivantes sont définies en tant qu’entrées DWORD :

    - Nom : **MaxFieldLength**, avec une valeur décimale de **65534**
    - Nom : **MaxRequestBytes**, avec une valeur décimale de **65534**

4. Redémarrez le serveur NDES. Le serveur est maintenant prêt à prendre en charge Certificate Connector.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>Étape 5 : activer, installer et configurer Intune Certificate Connector
Dans cette tâche, vous allez :

- activer la prise en charge de NDES dans Intune ;
- Téléchargez, installez et configurez Certificat Connector sur le serveur hébergeant le rôle de service d’inscription de périphériques réseau (NDES) dans votre environnement. Pour optimiser l’échelle de l’implémentation NDES dans votre organisation, vous pouvez installer plusieurs serveurs NDES avec Microsoft Intune Certificate Connector sur chaque serveur NDES.

##### <a name="download-install-and-configure-the-certificate-connector"></a>Télécharger, installer et configurer le connecteur de certificats
![Téléchargement de Connector](./media/certificates-download-connector.png)

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil**, puis sélectionnez **Autorité de certification**.
4. Sélectionnez **Ajouter** et **Télécharger le fichier du connecteur**. Enregistrez le fichier téléchargé à un emplacement accessible à partir du serveur où vous effectuerez l’installation.
5. Une fois le téléchargement terminé, exécutez le programme d'installation téléchargé (**ndesconnectorssetup.exe**) sur le serveur hébergeant le rôle de service d’inscription de périphériques réseau (NDES). Le programme d’installation installe également le module de stratégie pour NDES et le service web CRP. (Le service web CRP, CertificateRegistrationSvc, s'exécute en tant qu'application dans IIS.)

    > [!NOTE]
    > Quand vous installez NDES pour la version autonome d’Intune, le service CRP est installé automatiquement avec Certificate Connector. Quand vous utilisez Intune avec Configuration Manager, vous installez le Point d’enregistrement de certificat comme rôle de système de site distinct.

6. Quand vous êtes invité à entrer le certificat client pour le Certificate Connector, choisissez **Sélectionner**, puis sélectionnez le certificat **d'authentification client** installé sur votre serveur NDES à la tâche 3.

    Après avoir sélectionné le certificat d'authentification client, vous revenez au **Certificat client pour Microsoft Intune Certificate Connector** . Bien que le certificat sélectionné n’apparaisse pas, sélectionnez **Suivant** pour afficher les propriétés du certificat. Sélectionnez **Suivant**, puis **Installer**.
    
    > [!IMPORTANT]
    > Intune Certificate Connector ne peut pas être inscrit sur un appareil sur lequel la configuration de sécurité renforcée d’Internet Explorer est activée. Pour utiliser Intune Certificate Connector, [désactivez la configuration de sécurité renforcée d’Internet Explorer](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx).

7. Une fois l’Assistant terminé, mais avant de fermer l’Assistant, sélectionnez **Lancer l’interface utilisateur de Certificate Connector**.

    > [!TIP]
    > Si vous fermez l'Assistant avant de lancer l'interface utilisateur de Certificate Connector, vous pouvez le rouvrir en exécutant la commande suivante :
    >
    > <chemin_d'installation>\NDESConnectorUI\NDESConnectorUI.exe

8. Dans l'interface utilisateur de **Certificate Connector** :

    Sélectionnez **Connexion** et entrez vos informations d’identification du service Intune ou les informations d’identification d’un administrateur client avec l’autorisation d’administration globale.

    > [!IMPORTANT]
    > Une licence Intune valide doit être affectée au compte d’utilisateur. Si le compte d’utilisateur ne dispose pas d’une licence Intune valide, NDESConnectorUI.exe échoue.

    Si votre organisation utilise un serveur proxy et que ce dernier est nécessaire au serveur NDES pour accéder à Internet, sélectionnez **Utiliser un serveur proxy**, puis entrez le nom, le port et les informations d’identification de compte du serveur proxy pour vous connecter.

    Sélectionnez l’onglet **Avancé**, puis entrez les informations d’identification d’un compte qui possède l’autorisation **Émettre et gérer des certificats** sur votre autorité de certification émettrice. **Appliquez** vos modifications.

    Vous pouvez maintenant fermer l'interface utilisateur de Certificate Connector.

9. Ouvrez une invite de commandes, entrez **services.msc**, puis appuyez sur **Entrée**. Cliquez avec le bouton droit sur **Service du connecteur Intune**, puis sélectionnez **Redémarrer**.

Pour valider que le service s’exécute, ouvrez un navigateur et entrez l’URL suivante. Vous devriez obtenir une erreur **403** :

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

## <a name="create-a-scep-certificate-profile"></a>Créer un profil de certificat SCEP

1. Dans le portail Azure, ouvrez Microsoft Intune.
2. Sélectionnez **Configuration de l’appareil**, **Profils**, puis **Créer un profil**.
3. Entrez un **Nom** et une **Description** pour le profil de certificat SCEP.
4. Dans la liste déroulante **Plateforme**, sélectionnez la plateforme d’appareil pour ce certificat SCEP. Actuellement, vous pouvez sélectionner l’une des plateformes suivantes pour les paramètres de restriction de l’appareil :
   - **Android**
   - **iOS**
   - **MacOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 et versions ultérieures**
   - **Windows 10 et versions ultérieures**
5. Dans la liste déroulante **Type de profil**, sélectionnez **Certificat SCEP**.
6. Dans le volet **Certificat SCEP**, configurez les paramètres suivants :

   - **Période de validité du certificat** : si vous avez exécuté la commande `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` sur l’Autorité de certification émettrice, ce qui autorise une période de validité personnalisée, vous pouvez entrer le temps restant avant l’expiration du certificat.<br>Vous pouvez entrer une valeur inférieure à la période de validité du modèle de certificat, mais pas une valeur supérieure. Par exemple, si la période de validité du certificat dans le modèle de certificat est de 2 ans, vous pouvez entrer une valeur de 1 an, mais pas une valeur de 5 ans. La valeur doit également être inférieure à la période de validité restante du certificat de l’autorité de certification émettrice. 
   - **Fournisseur de stockage de clés** (Windows Phone 8.1, Windows 8.1, Windows 10) : entrez l’emplacement de stockage de la clé du certificat. Choisissez l'une des valeurs suivantes :
     - **Inscrire auprès du fournisseur de stockage de clés (KSP) du module de plateforme sécurisée (TPM) s’il est présent ; sinon, inscrire auprès du fournisseur de stockage de clés du logiciel**
     - **Inscrire auprès du fournisseur de stockage de clés (KSP) du module de plateforme sécurisée (TPM), sinon mettre en échec**
     - **Inscrire auprès de Passport, sinon mettre en échec (Windows 10 et versions ultérieures)**
     - **Inscrire auprès du fournisseur de stockage de clés du logiciel**

   - **Format du nom de l’objet** : dans la liste, sélectionnez comment Intune crée automatiquement le nom de l’objet dans la demande de certificat. Si le certificat est pour un utilisateur, vous pouvez également inclure l'adresse e-mail de cet utilisateur dans le nom de l'objet. Choisissez parmi :
     - **Non configuré**
     - **Nom commun**
     - **Nom commun (adresse e-mail incluse)**
     - **Nom commun comme adresse e-mail**
     - **IMEI (International Mobile Equipment Identity)**
     - **Numéro de série**
     - **Personnalisé** : quand vous sélectionnez cette option, un autre champ de liste déroulante s’affiche. Utilisez ce champ pour entrer un format de nom d’objet personnalisé. Le format personnalisé prend en charge deux variables : **Nom courant (cn)** et **Message électronique (e)**. **Nom courant (cn)** peut être défini sur une des variables suivantes :
       - **CN = {{UserName}}** : nom d’utilisateur principal de l’utilisateur, tel que janedoe@contoso.com
       - **CN={{AAD_Device_ID}}** : ID attribué quand vous inscrivez un appareil dans Azure Active Directory (AD). Cet ID est généralement utilisé pour l’authentification auprès d’Azure AD.
       - **CN={{SERIALNUMBER}}** : numéro de série unique (SN) généralement utilisé par le fabricant pour identifier un appareil
       - **CN={{IMEINumber}}** : numéro IMEI (International Mobile Equipment Identity) unique utilisé pour identifier un téléphone mobile
       - **CN={{OnPrem_Distinguished_Name}}** : séquence de noms uniques relatifs séparés par des virgules, par exemple `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`

          Pour utiliser la variable `{{OnPrem_Distinguished_Name}}`, veillez à synchroniser l’attribut utilisateur `onpremisesdistingishedname` qui utilise [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) avec Azure AD.

       - **CN = {{onPremisesSamAccountName}}**  : les administrateurs peuvent synchroniser l’attribut samAccountName d’Active Directory à Azure AD à l’aide d’Azure AD Connect dans un attribut appelé `onPremisesSamAccountName`. Intune peut remplacer cette variable dans le cadre d’une demande d’émission de certificat dans le sujet d’un certificat SCEP.  L’attribut samAccountName est le nom d’ouverture de session de l’utilisateur utilisé pour prendre en charge les clients et serveurs à partir d’une version antérieure de Windows (antérieure à Windows 2000). Le format du nom d’ouverture de session de l’utilisateur est : `DomainName\testUser`, ou uniquement `testUser`.

          Pour utiliser la variable `{{onPremisesSamAccountName}}`, veillez à synchroniser l’attribut utilisateur `onPremisesSamAccountName` qui utilise [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) avec Azure AD.

       En utilisant une combinaison d’une ou de plusieurs de ces variables et de chaînes statiques, vous pouvez créer un format de nom d’objet personnalisé, tel que : **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**. <br/> Dans cet exemple, vous avez créé un format de nom d’objet qui, en plus des variables CN et E, utilise des chaînes pour les valeurs de l’unité d’organisation, de l’organisation, de l’emplacement, de la région et du pays. La page [CertStrToName function](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) (Fonction CertStrToName) illustre cette fonction et ses chaînes prises en charge.

- **Autre nom de l’objet** : entrez comment Intune crée automatiquement les valeurs pour l’autre nom de l’objet dans la demande de certificat. Par exemple, si vous sélectionnez un type de certificat utilisateur, vous pouvez inclure le nom d’utilisateur principal (UPN) dans l’autre nom de l’objet. Si le certificat client est utilisé pour l’authentification sur un serveur de stratégie réseau, vous devez affecter le nom d’utilisateur principal à l’autre nom de l’objet.
- **Utilisation de la clé** : entrez les options d’utilisation de la clé pour le certificat. Les options disponibles sont les suivantes :
  - **Chiffrage de clés** : autorisez l’échange de clés uniquement quand la clé est chiffrée
  - **Signature numérique** : autorisez l’échange de clés uniquement quand une signature numérique contribue à protéger la clé
- **Taille de la clé (bits)** : sélectionnez le nombre de bits contenus dans la clé
- **Algorithme de hachage** (Android, Windows Phone 8.1, Windows 8.1, Windows 10) : sélectionnez l’un des types d’algorithme de hachage disponibles avec ce certificat. Permet de sélectionner le niveau le plus élevé de sécurité pris en charge par les appareils se connectant.
- **Certificat racine** : choisissez un profil de certificat d’autorité de certification racine que vous avez configuré et attribué à l’utilisateur ou à l’appareil. Ce certificat d’autorité de certification doit être le certificat racine de l’autorité de certification qui émet le certificat que vous configurez dans ce profil de certificat.
- **Utilisation de la clé étendue** : **ajoutez** des valeurs pour le rôle prévu du certificat. Dans la plupart des cas, le certificat demande une **authentification client** pour que l’utilisateur ou l’appareil puisse être authentifié auprès d’un serveur. Toutefois, vous pouvez ajouter d'autres utilisations de la clé en fonction de vos besoins.
- **Paramètres d’inscription**
  - **Seuil de renouvellement (%)** : entrez le pourcentage de durée de vie restante du certificat avant que l’appareil ne demande le renouvellement du certificat.
  - **URL du serveur SCEP** : entrez une ou plusieurs URL pour les serveurs NDES qui délivrent les certificats par le biais de SCEP.
  - Sélectionnez **OK** et **créez** votre profil.

Le profil est créé et apparaît dans le volet de la liste des profils.

## <a name="assign-the-certificate-profile"></a>Affecter le profil de certificat

Considérez les éléments suivants avant d’attribuer des profils de certificat aux groupes :

- Quand vous attribuez des profils de certificat aux groupes, le fichier de certificat issu du profil de certificat d’autorité de certification approuvée est installé sur l’appareil. L’appareil utilise le profil de certificat SCEP pour créer une demande de certificat par l’appareil.
- Les profils de certificat s’installent uniquement sur les appareils exécutant la plateforme que vous utilisez quand vous créez le profil.
- Vous pouvez affecter des profils de certificat sur des regroupements d’utilisateurs ou d’appareils.
- Pour publier un certificat sur un appareil rapidement après l’inscription de l’appareil, affectez le profil de certificat à un groupe d’utilisateurs plutôt qu’à un groupe d’appareils. Si vous l’affectez à un groupe d’appareils, une inscription complète des appareils est préalablement nécessaire pour qu’ils puissent recevoir des stratégies.
- Même si vous affectez chaque profil séparément, vous devez également affecter l’autorité de certification racine approuvée et le profil SCEP ou PKCS. Dans le cas contraire, la stratégie de certificat SCEP ou PKCS échoue.

    > [!NOTE]
    > Pour iOS, vous devriez voir plusieurs copies du certificat dans le profil de gestion si vous déployez plusieurs profils de ressources qui utilisent le même profil de certificat.
    
Pour plus d’informations sur la façon d’affecter des profils, consultez [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md).

## <a name="intune-connector-events-and-diagnostic-codes"></a>Événements et codes de diagnostic du connecteur Intune

À compter de la version 6.1803.x.x, le service du connecteur Intune journalise les événements dans l’**observateur d’événements**  (**Journaux des applications et des services** > **Connecteur Microsoft Intune**). Utilisez ces événements pour résoudre les problèmes potentiels dans la configuration du connecteur Intune. Ces événements journalisent les réussites et les échecs d’une opération. Ils contiennent également des codes de diagnostic avec des messages pour aider l’administrateur informatique à résoudre le problème.

### <a name="event-ids-and-descriptions"></a>ID d’événement et descriptions

> [!NOTE]
> Pour plus d’informations sur les codes de diagnostic associés pour chaque événement, utilisez le tableau **Codes de diagnostic** (dans cet article).

| ID d’événement      | Nom de l’événement    | Description de l’événement | Codes de diagnostic associés |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Service du connecteur démarré | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Service du connecteur arrêté | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Certificat d’inscription du connecteur correctement renouvelé | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Échec du renouvellement du certificat d’inscription du connecteur. Réinstallez le connecteur. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Impossible de récupérer le certificat d’inscription du connecteur à partir du Registre. Consultez les détails de l’événement pour connaître l’empreinte numérique de certificat liée à cet événement. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Vérifiez les informations de diagnostic dans les détails de l’événement. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Certificat PKCS correctement émis. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification, le nom du modèle de certificat et l’empreinte numérique de certificat associés à cet événement. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Échec de l’émission d’un certificat PKCS. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification, le nom du modèle de certificat et l’empreinte numérique de certificat associés à cet événement. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Certificat correctement révoqué. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification et le numéro de série du certificat associés à cet événement. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Échec de la révocation du certificat. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification et le numéro de série du certificat associés à cet événement. Pour plus d’informations, consultez les journaux SVC NDES.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Download_Success | Demande de signature d’un certificat, de téléchargement d’un certificat client ou de révocation d’un certificat correctement téléchargée. Consultez les détails de l’événement pour connaître les informations relatives au téléchargement.  | 0x00000000, 0x0FFFFFFF |
| 20302 | Download_Failure | Échec du téléchargement de la demande de signature d’un certificat, de téléchargement d’un certificat client ou de révocation d’un certificat. Consultez les détails de l’événement pour connaître les informations relatives au téléchargement. | 0x00000000, 0x0FFFFFFF |
| 20400 | Upload_Success | Données de demande ou de révocation du certificat correctement chargées. Consultez les détails de l’événement pour connaître les informations relatives au chargement. | 0x00000000, 0x0FFFFFFF |
| 20402 | Upload_Failure | Échec du chargement des données de demande ou de révocation du certificat. Consultez les détails de l’événement > État de chargement pour déterminer le point de défaillance.| 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Demande d’accès client correctement vérifiée par le point d’enregistrement de certificat | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Demande exécutée mais rejetée par le point d’enregistrement de certificat. Pour plus d’informations, consultez le code de diagnostic et le message. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Échec de la vérification d’une demande d’accès client par le point d’enregistrement de certificat. Pour plus d’informations, consultez le code de diagnostic et le message. Consultez les détails du message d’événement pour connaître l’ID d’appareil correspondant à la demande. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | Le point d’enregistrement de certificat a correctement terminé le processus de notification et a envoyé le certificat à l’appareil client. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | Le point d’enregistrement de certificat n’a pas pu terminer le processus de notification. Consultez les détails du message d’événement pour obtenir des informations sur la demande. Vérifiez la connexion entre le serveur NDES et l’autorité de certification. | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>Codes de diagnostic

| Code de diagnostic | Nom du diagnostic | Message de diagnostic |
| -------------   | -------------   | -------------      |
| 0x00000000 | Opération réussie  | Opération réussie |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | L’autorité de certification n’est pas valide ou est inaccessible. Vérifiez que l’autorité de certification est disponible et que votre serveur peut communiquer avec elle. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Le certificat d’authentification client Symantec est introuvable dans le magasin de certificats local. Pour plus d’informations, consultez [Installer le certificat d’autorisation d’inscription Symantec](https://docs.microsoft.com/en-us/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate).  |
| 0x00000402 | RevokeCert_AccessDenied  | Le compte spécifié ne dispose pas d’autorisations pour révoquer un certificat d’une autorité de certification. Pour déterminer l’autorité de certification émettrice, consultez le champ Nom de l’autorité de certification dans les détails du message d’événement.  |
| 0x00000403 | CertThumbprint_NotFound  | Impossible de trouver un certificat correspondant à votre entrée. Inscrivez le connecteur de certificat, puis réessayez. |
| 0x00000404 | Certificate_NotFound  | Impossible de trouver un certificat correspondant à l’entrée fournie. Réinscrivez le connecteur de certificat, puis réessayez. |
| 0x00000405 | Certificate_Expired  | Un certificat a expiré. Réinscrivez le connecteur de certificat pour renouveler le certificat, puis réessayez. |
| 0x00000408 | CRPSCEPCert_NotFound  | Certificat de chiffrement NDES introuvable. Vérifiez que le connecteur NDES et Intune sont configurés correctement. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Impossible de récupérer le certificat de signature. Vérifiez que le service du connecteur Intune est configuré correctement et qu’il est en cours d’exécution. Vérifiez également que les événements de téléchargement de certificat ont réussi. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Échec de la désérialisation de la demande de challenge SCEP. Vérifiez que le connecteur NDES et Intune sont configurés correctement. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Demande refusée en raison de l’expiration de la demande d’accès au certificat. L’appareil client peut réessayer après avoir obtenu une nouvelle demande d’accès à partir du serveur d’administration. |
| 0x0FFFFFFFF | Unknown_Error  | Nous ne pouvons pas traiter votre demande, car une erreur côté serveur s’est produite. Réessayez. |

## <a name="next-steps"></a>Étapes suivantes
[Utilisez des certificats PKCS](certficates-pfx-configure.md), ou [émettez des certificats PKCS à partir d’un service web du gestionnaire PKI](certificates-symantec-configure.md).
