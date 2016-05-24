---
# required metadata

title: Configurer l’infrastructure de certificat | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3a435650-3891-4754-8abc-4bbac244f33b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configurer l’infrastructure de certificat
Cette rubrique décrit les éléments dont vous avez besoin pour créer et déployer des profils de certificat.

Pour effectuer une authentification basée sur certificat dans votre organisation, vous avez besoin d’une autorité de certification d’entreprise.

Pour utiliser des profils de certificat SCEP, en plus de l’autorité de certification d’entreprise, il vous faut également :

-   Un serveur qui exécute le service d'inscription d'appareil réseau

-   Intune Certificate Connector, qui est installé sur le serveur Windows Server 2012 R2 exécutant NDES

Pour utiliser des profils de certificat .PFX, en plus de l’autorité de certification d’entreprise, il vous faut également :

-  Un ordinateur capable de communiquer avec l'autorité de certification (ou utilisez l'ordinateur d'autorité de certification proprement dit)

-  Intune Certificate Connector, qui s'exécute sur l'ordinateur qui peut communiquer avec l'autorité de certification

## Infrastructure locale


-    **Domaine Active Directory** : tous les serveurs répertoriés dans cette section (à l’exception du serveur du proxy d’application web) doivent être joints à votre domaine Active Directory.

-  **Autorité de certification** : une autorité de certification d’entreprise qui s’exécute sur une édition Entreprise de Windows Server 2008 R2 ou version ultérieure. Une autorité de certification autonome n'est pas prise en charge. Pour savoir comment configurer une autorité de certification, consultez [Installer l’autorité de certification](http://technet.microsoft.com/library/jj125375.aspx).
    Si votre autorité de certification exécute Windows Server 2008 R2, vous devez [installer le correctif logiciel à partir de KB2483564](http://support.microsoft.com/kb/2483564/).

-  **Serveur NDES** (SCEP uniquement) : sur un serveur qui exécute Windows Server 2012 R2 ou version ultérieure, vous devez configurer le service d’inscription d’appareils réseau (NDES). Intune ne prend pas en charge le service NDES quand il s’exécute sur un serveur qui exécute également l’autorité de certification d’entreprise. Consultez le [Guide du service d’inscription d’appareils réseau](http://technet.microsoft.com/library/hh831498.aspx) pour obtenir des instructions sur la configuration de Windows Server 2012 R2 pour héberger le service d’inscription d’appareils réseau.|
-  **Un ordinateur capable de communiquer avec l’autorité de certification** (.PFX uniquement) : en guise d’alternative, utilisez l’ordinateur d’autorité de certification proprement dit.
-  **Microsoft Intune Certificate Connector** : vous utilisez la console d’administration Intune pour télécharger le programme d’installation de **Certificate Connector** (**ndesconnectorssetup.exe**). Vous pouvez ensuite exécuter **ndesconnectorssetup.exe** sur l'ordinateur où vous souhaitez installer Certificate Connector. Pour les profils de certificat .PFX, installez Certificate Connector sur l'ordinateur qui communique avec l'autorité de certification.
-  **Serveur proxy d’application web** (facultatif) : vous pouvez utiliser un serveur qui exécute Windows Server 2012 R2 ou version ultérieure comme serveur proxy d’application web. Cette configuration :
    -  Permet aux appareils de recevoir des certificats à l'aide d'une connexion Internet.
    -  Est une recommandation de sécurité lorsque les appareils se connectent via Internet pour recevoir et renouveler les certificats.

> [!NOTE]           
> -    Le serveur qui héberge le proxy d'application web [doit installer une mise à jour](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) qui permet la prise en charge des longues URL utilisées par le service d'inscription d'appareil réseau. Cette mise à jour est incluse dans le [correctif cumulatif de décembre 2014](http://support.microsoft.com/kb/3013769), ou individuellement à partir de l’article [KB3011135](http://support.microsoft.com/kb/3011135).
>-  En outre, le serveur qui héberge le proxy d’application web doit avoir un certificat SSL qui correspond au nom publié sur les clients externes, et approuver le certificat SSL utilisé sur le serveur NDES. Ces certificats permettent au serveur du proxy d'application web de mettre fin à la connexion SSL à partir des clients et de créer une nouvelle connexion SSL au serveur NDES.
    Pour plus d’informations sur les certificats du proxy d’application web, consultez la section **Planifier des certificats** dans [Planification de publication des applications à l’aide du proxy d’application web](https://technet.microsoft.com/library/dn383650.aspx) Pour obtenir des informations générales sur les serveurs de proxy d’application web, consultez [Utilisation d’un proxy d’application web](http://technet.microsoft.com/library/dn584113.aspx).|


### Certificats et modèles

|Objet|Détails|
|----------|-----------|
|**Modèle de certificat**|Vous configurez ce modèle sur votre autorité de certification émettrice.|
|**Certificat d'authentification client**|Demandé auprès de votre autorité de certification émettrice ou de votre autorité de certification publique, ce certificat doit être installé sur le serveur NDES.|
|**Certificat d'authentification serveur**|Demandé auprès de votre autorité de certification émettrice ou autorité de certification publique, ce certificat doit être installé et lié dans IIS sur le serveur NDES.|
|**Certificat d'autorité de certification racine approuvée**|Vous l'exportez en tant que fichier **.cer** à partir de l'autorité de certification émettrice ou de tout appareil qui approuve l'autorité de certification émettrice, puis le déployez sur des appareils à l'aide du profil de certificat d'autorité de certification approuvée.<br /><br />Vous utilisez un seul certificat d'autorité de certification racine approuvée par plateforme de système d'exploitation et l'associez à chaque profil de certificat racine approuvé que vous créez.<br /><br />Vous pouvez utiliser des certificats d'autorité de certification racine approuvée supplémentaires chaque fois que nécessaire. Par exemple, vous pouvez agir ainsi pour fournir une relation d'approbation à une autorité de certification qui signe les certificats d'authentification du serveur pour vos points d'accès Wi-Fi.|

### Comptes

|Nom|Détails|
|--------|-----------|
|**Compte de service NDES**|Vous spécifiez un compte d'utilisateur de domaine à utiliser comme compte de service NDES.|

## Configurer votre infrastructure
Avant de configurer les profils de certificat, vous devez effectuer les tâches suivantes, ce qui nécessite la connaissance de Windows Server 2012 R2 et des services de certificats Active Directory :

**Tâche 1** : configurer les modèles de certificats sur l’autorité de certification

**Tâche 2** (profil SCEP uniquement) : configurer les composants requis sur le serveur NDES

**Tâche 3** (profil SCEP uniquement) : configurer NDES pour une utilisation avec Intune

**Tâche 4** : activer, installer et configurer Intune Certificate Connector

## Tâche 1 : configurer les modèles de certificats sur l'autorité de certification
Dans cette tâche, vous allez :

-   Créer un compte de service NDES

    > [!NOTE]
    > Pour révoquer des certificats, le compte de service NDES a besoin de droits *Émettre et gérer des certificats* pour chaque modèle de certificat utilisé par un profil de certificat.

-   Configurer un modèle de certificat pour NDES

-   Publier le modèle de certificat pour NDES

##### Pour configurer l'autorité de certification

1.  Créez un compte d'utilisateur de domaine à utiliser comme compte de service NDES. Vous spécifiez ce compte lorsque vous configurez des modèles sur l'autorité de certification émettrice avant d'installer et de configurer NDES.

2.  Sur l'autorité de certification émettrice, utilisez le composant logiciel enfichable Modèles de certificats pour créer un modèle personnalisé ou copier un modèle existant, puis modifiez un modèle existant (comme le modèle de l'utilisateur), pour l'utiliser avec NDES.

    Le modèle doit avoir les configurations suivantes :

    -   Spécifiez un **Nom complet du modèle** convivial pour le modèle.

    -   Sous l'onglet **Nom de l'objet** , sélectionnez **Fournir dans la demande**. (La sécurité est appliquée par le module de stratégie Intune pour NDES.)

    -   Sous l’onglet **Extensions** , vérifiez que **Description des stratégies d’application** inclut **Authentification du client**.

        > [!IMPORTANT]
        > Pour les modèles de certificats iOS et Mac OS XOS, sous l’onglet **Extensions**, modifiez **Utilisation de la clé** et vérifiez que l’option **Signature faisant preuve de l’origine** n’est pas sélectionnée.

    -   Sous l’onglet **Sécurité** , ajoutez le compte de service NDES et attribuez-lui les autorisations **Inscription** sur le modèle.

3.  Examinez la **Période de validité** sous l'onglet **Général** du modèle. Par défaut, Intune utilise la valeur configurée dans le modèle. Toutefois, vous pouvez configurer l’autorité de certification pour permettre au demandeur de spécifier une valeur différente, que vous pouvez alors définir à partir de la console d’administration Intune. Si vous souhaitez toujours utiliser la valeur du modèle, ignorez le reste de l'étape.

    > [!IMPORTANT]
    > Les plateforme iOS et Mac OS X utilisent toujours la valeur définie dans le modèle, indépendamment des autres configurations que vous effectuez.

    Pour configurer l'autorité de certification et permettre au demandeur de spécifier la période de validité, sur l'autorité de certification, exécutez les commandes suivantes :

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  Sur l'autorité de certification émettrice, utilisez le composant logiciel enfichable Autorité de Certification pour publier le modèle de certificat.

    1.  Sélectionnez le nœud **Modèles de certificats**, cliquez sur **Action**-&gt; **Nouveau** &gt; **Modèle de certificat à délivrer**, puis sélectionnez le modèle que vous avez créé à l’étape 2.

    2.  Validez le modèle publié en l'affichant sous le dossier **Modèles de certificats** .

5.  Profils .PFX : sur l'ordinateur d'autorité de certification, vérifiez que l'ordinateur qui héberge Intune Certificate Connector a l'autorisation Inscription pour qu'il puisse accéder au modèle utilisé pour créer le profil .PFX. Définissez cette autorisation sous l'onglet **Sécurité** des propriétés de l'ordinateur d'autorité de certification.

## Tâche 2 (profil SCEP uniquement) : configurer les composants requis sur le serveur NDES
Dans cette tâche, vous allez :

-   Ajouter NDES à un serveur Windows Server et configurer IIS pour prendre en charge NDES

-   Ajouter le compte de service NDES au groupe IIS_IUSR

-   Définir le SPN pour le compte de service NDES

##### Pour configurer les composants requis du serveur NDES

1.  Sur le serveur qui héberge NDES, vous devez ouvrir une session en tant qu' **Administrateur d'entreprise**, puis utilisez l' [Assistant Ajout de rôles et de fonctionnalités](https://technet.microsoft.com/library/hh831809.aspx) pour installer NDES :

    1.  Dans l'Assistant, sélectionnez **Services de certificats Active Directory** pour accéder aux services de rôle AD CS. Sélectionnez **Service d'inscription d'appareil réseau**, décochez **Autorité de certification**, puis terminez l'Assistant.

        > [!TIP]
        > Dans la page **Progression de l'installation** de l'Assistant, ne cliquez pas sur **Fermer**. Cliquez à la place sur le lien **Configurer les services de certificats Active Directory sur le serveur de destination**. Cette opération ouvre l'Assistant **Configuration AD CS** que vous utilisez pour la tâche suivante. Une fois l'Assistant Configuration AD CS ouvert, vous pouvez fermer l'Assistant Ajout de rôles et de fonctionnalités.

    2.  Lorsque NDES est ajouté au serveur, l'Assistant installe également IIS. Vérifiez qu'IIS a les configurations suivantes :

        -   **Serveur Web** &gt; **Sécurité** &gt; **Filtrage des demandes**

        -   **Serveur Web** &gt; **Développement d’applications** &gt; **ASP.NET 3.5**. L'installation d'ASP.NET 3.5 installe le .NET Framework 3.5. Quand vous installez le .NET Framework 3.5, installez à la fois le **.NET Framework 3.5** de base et **Activation HTTP**.

        -   **Serveur Web** &gt; **Développement d’applications** &gt; **ASP.NET 4.5**. L'installation d'ASP.NET 4.5 installe .NET Framework 4.5. Quand vous installez le .NET Framework 4.5, installez à la fois la fonctionnalité **.NET Framework 4.5** de base, **ASP.NET 4.5** et la fonctionnalité **Services WCF** &gt; **Activation HTTP**.

        -   **Outils de gestion** &gt; **IIS 6 Management Compatibility** &gt; **Compatibilité avec la métabase de données IIS 6**

        -   **Outils de gestion** &gt; **IIS 6 Management Compatibility** &gt; **Compatibilité WMI d’IIS 6**

2.  Sur le serveur, ajoutez le compte de service NDES en tant que membre du groupe **IIS_IUSR**.

3.  Exécutez la commande suivante pour définir le SPN du compte de service NDES :

    -   **setspn -s http/&lt;nom DNS du serveur NDES&gt; &lt;nom du domaine&gt;\&lt;nom de compte du service NDES&gt;**

    Par exemple, si votre serveur NDES se nomme **Serveur01**, votre domaine **Contoso.com**et le compte de service **ServiceNDES**, utilisez :

    -   **setspn –s http/Serveur01.contoso.com contoso\ServiceNDES**

## Tâche 3 (profil SCEP uniquement) : configurer NDES pour une utilisation avec Microsoft Intune 
Dans cette tâche, vous allez :

-   Configurer NDES pour une utilisation avec l'autorité de certification émettrice

-   Lier le certificat du serveur d'authentification (SSL) dans IIS

-   Configurer le filtrage de demandes dans IIS

##### Pour configurer NDES pour une utilisation avec Intune

1.  Sur le serveur NDES, ouvrez l'Assistant Configuration AD CS et procédez aux configurations suivantes.

    > [!TIP]
    > Si vous avez cliqué sur le lien de la tâche précédente, l'Assistant est déjà ouvert. Sinon, ouvrez le Gestionnaire de serveur pour accéder à la configuration de post-déploiement pour les services de certificats Active Directory.

    -   Dans la page **Services de rôle**, sélectionnez le **Service d’inscription d’appareils réseau**.

    -   Dans la page **Compte de service pour NDES** , spécifiez le compte de service NDES.

    -   Dans la page **Autorité de certification pour NDES** , cliquez sur **Sélectionner**, puis sélectionnez l'autorité de certification émettrice où vous avez configuré le modèle de certificat.

    -   Dans la page **Chiffrement pour NDES** , définissez la longueur de la clé pour répondre aux besoins de votre entreprise.

    Dans la page **Confirmation** , cliquez sur **Configurer** pour terminer l'Assistant.

2.  Une fois l'Assistant terminé, modifiez la clé de Registre suivante sur le serveur NDES :

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\**

    Pour modifier cette clé, identifiez l’**Objet** du modèle de certificat, tel qu’indiqué sous l’onglet **Traitement de la demande**, puis modifiez l’entrée correspondante du Registre en remplaçant les données existantes par le nom du modèle de certificat (pas le nom d’affichage du modèle) que vous avez spécifié dans la tâche 1. Le tableau suivant mappe le rôle de modèle de certificat aux valeurs du Registre :

    |Rôle de modèle de certificat (onglet Traitement de la demande)|Valeur du Registre à modifier|Valeur indiquée dans la console d’administration Intune pour le profil SCEP|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Signature|SignatureTemplate|Signature numérique|
    |Chiffrement|EncryptionTemplate|Chiffrement de la clé|
    |Signature et chiffrement|GeneralPurposeTemplate|Chiffrement de la clé<br /><br />Signature numérique|
    Par exemple, si le rôle de votre modèle de certificat est **Chiffrement**, remplacez la valeur de **EncryptionTemplate** par le nom de votre modèle de certificat.

3.  Après avoir modifié le Registre, exécutez **iisreset** sur le serveur pour forcer le serveur à choisir les modifications de configuration récentes.

##### Pour installer et lier des certificats sur le serveur NDES

1.  Sur votre serveur NDES, demandez et installez un certificat d' **authentification serveur** auprès de votre autorité de certification interne ou autorité de certification publique. Vous allez ensuite lier ce certificat SSL dans IIS.

    > [!TIP]
    > Après avoir lié le certificat SSL dans IIS, vous allez également installer un certificat d'authentification client. Ce certificat peut être émis par toute autorité de certification approuvée par le serveur NDES. Bien que cette solution ne soit pas recommandée, vous pouvez utiliser le même certificat pour l'authentification serveur et l'authentification client aussi longtemps que le certificat possède les deux utilisations améliorées de la clé. Passez en revue les étapes suivantes pour plus d'informations sur ces certificats d'authentification.

    1.  Après avoir obtenu le certificat d'authentification serveur, ouvrez le **Gestionnaire IIS**, sélectionnez le **Site web par défaut** dans le volet **Connexions** , puis cliquez sur **Liaisons** dans le volet **Actions** .

    2.  Cliquez sur **Ajouter**, définissez **Type** avec la valeur **https**, puis vérifiez que le port est **443**. (Seul le port 443 est pris en charge pour la version autonome d’Intune).

    3.  Pour **Certificat SSL**, spécifiez le certificat d'authentification serveur.

        > [!NOTE]
        > Si le serveur NDES utilise un nom interne et un nom externe pour une même adresse réseau, le certificat d'authentification serveur doit avoir un **Nom de l'objet** avec un nom de serveur public externe et un **Autre nom de l'objet** incluant le nom du serveur interne.

2.  Sur votre serveur NDES, demandez et installez un certificat d' **authentification client** auprès de votre autorité de certification interne ou d'une autorité de certification publique. Cela peut être le même certificat que le certificat d'authentification serveur si ce certificat possède les deux fonctions.

    Le certificat d'authentification client doit avoir les propriétés suivantes :

    **Utilisation améliorée de la clé** : doit inclure l’**Authentification du client**.

    **Nom de l’objet** : doit être équivalent au nom DNS du serveur sur lequel vous installez le certificat (serveur NDES).

##### Pour configurer le filtrage des demandes IIS

1.  Sur le serveur NDES, ouvrez le **Gestionnaire IIS**, sélectionnez le **Site web par défaut** dans le volet **Connexions**, puis ouvrez **Filtrage des demandes**.

2.  Cliquez sur **Modifier les paramètres de la fonctionnalité**, puis définissez les éléments suivants :

    **Chaîne de requête (octets)** = **65534**

    **Longueur maximale des URL (octets)** = **65534**

3.  Vérifiez la clé de Registre suivante :

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Vérifiez que les valeurs suivantes sont définies en tant qu'entrées DWORD :

    Nom : **MaxFieldLength**, avec une valeur décimale de **65534**

    Nom : **MaxRequestBytes**, avec une valeur décimale de **65534**

4.  Redémarrez le serveur NDES. Le serveur est maintenant prêt à prendre en charge Certificate Connector.

## Tâche 4 : activer, installer et configurer Intune Certificate Connector (pour les certificats SCEP et .PFX)
Dans cette tâche, vous allez :

Activer la prise en charge de NDES dans Intune

Télécharger, installer et configurer Certificate Connector sur le serveur NDES

##### Pour activer la prise en charge de Certificate Connector

1.  Ouvrez la [console d’administration Intune](https://manage.microsoft.com), cliquez sur **Administration** &gt; **Certificate Connector**.

2.  Cliquez sur **Configurer On-premises Certificate Connector**.

3.  Sélectionnez **Activer Certificate Connector**, puis cliquez sur **OK**.

##### Pour télécharger, installer et configurer Certificate Connector

1.  Ouvrez la [console d’administration Intune](https://manage.microsoft.com), puis cliquez sur **Administration** &gt; **Gestion des appareils mobiles** &gt; **Certificate Connector** &gt; **Télécharger Certificate Connector**.

2.  Une fois le téléchargement terminé, exécutez le programme d'installation téléchargé (**ndesconnectorssetup.exe**) :

    -   Pour les certificats .PFX, exécutez le programme d'installation sur l'ordinateur en mesure de se connecter à l'autorité de certification. Choisissez l’option de distribution .PFX, puis cliquez sur Installer. Une fois l’installation terminée, créez un profil de certificat comme décrit dans [Configurer les profils de certificat](configure-intune-certificate-profiles.md).

    -   Pour les certificats SCEP, exécutez le programme d'installation sur un serveur Windows Server 2012 R2.

    Pour l'option SCEP, le programme d'installation installe également le module de stratégie pour NDES et le service web CRP. (Le service web CRP, CertificateRegistrationSvc, s'exécute en tant qu'application dans IIS.)

    > [!NOTE]
    > Quand vous installez NDES pour la version autonome d’Intune, le service CRP est installé automatiquement avec Certificate Connector. Quand vous utilisez Intune avec Configuration Manager, vous installez le Point d’enregistrement de certificat comme rôle de système de site distinct.

3.  Quand vous êtes invité à entrer le certificat client pour Certificate Connector, cliquez sur **Sélectionner**, puis sélectionnez le certificat d' **authentification client** installé sur votre serveur NDES à la tâche 3.

    Après avoir sélectionné le certificat d'authentification client, vous revenez au **Certificat client pour Microsoft Intune Certificate Connector** . Bien que le certificat sélectionné n'apparaisse pas, cliquez sur **Suivant** pour afficher les propriétés du certificat. Cliquez sur **Suivant**, puis sur **Installer**.

4.  Une fois l’Assistant terminé, mais avant de le fermer, cliquez sur **Lancer l’interface utilisateur de Certificate Connector**.

    > [!TIP]
    > Si vous fermez l'Assistant avant de lancer l'interface utilisateur de Certificate Connector, vous pouvez le rouvrir en exécutant la commande suivante :
    >
    > **&lt;chemin_installation&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  Dans l'interface utilisateur de **Certificate Connector** :

    Cliquez sur **Connexion** et entrez vos informations d’identification du service Intune ou les informations d’identification d’un administrateur client avec l’autorisation d’administration globale.

    Si votre organisation utilise un serveur proxy et que ce dernier est nécessaire au serveur NDES pour accéder à Internet, cliquez sur **Utiliser un serveur proxy**, puis indiquez le nom, le port et les informations d’identification de compte du serveur proxy pour vous connecter.

    Sélectionnez l’onglet **Avancé**, puis fournissez les informations d’identification d’un compte qui dispose de l’autorisation **Émettre et gérer des certificats** sur votre autorité de certification émettrice, puis cliquez sur **Appliquer**.

    Vous pouvez maintenant fermer l'interface utilisateur de Certificate Connector.

6.  Ouvrez une invite de commande et tapez **services.msc**, appuyez sur **Entrée**, cliquez avec le bouton droit sur **Service Certificate Connector**, puis cliquez sur **Redémarrer**.

Pour valider que le service s'exécute, ouvrez un navigateur et entrez l'URL suivante, ce qui doit retourner une erreur **403** :

**http:// &lt;nom_de_domaine_complet_de_votre_serveur_NDES&gt;/certsrv/mscep/mscep.dll**

### Étapes suivantes
Vous êtes maintenant prêt à configurer des profils de certificat, comme décrit dans [Configurer les profils de certificat](configure-intune-certificate-profiles.md).


<!--HONumber=May16_HO1-->

