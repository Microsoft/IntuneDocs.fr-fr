---
title: Configurer l’infrastructure pour prendre en charge des profils de certificat SCEP avec Microsoft Intune - Azure | Microsoft Docs
description: Pour utiliser SCEP dans Microsoft Intune, configurez votre domaine AD local, créez une autorité de certification, configurez le serveur NDES et installez Intune Certificate Connector.
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
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86640c831e8836a72ad5a0a7d5023ff7d836a43a
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801583"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Configurer l’infrastructure pour prendre en charge SCEP avec Intune

Intune prend en charge l’utilisation du Protocole d’inscription de certificats simple (SCEP) pour [authentifier les connexions à vos applications et aux ressources de l’entreprise](certificates-configure.md). SCEP utilise le certificat d’autorité de certification afin de sécuriser l’échange de messages pour la demande de signature de certificat. Quand votre infrastructure prend en charge SCEP, vous pouvez utiliser des profils de *certificat SCEP* Intune (un type de profil d’appareil dans Intune) pour déployer les certificats sur vos appareils. Microsoft Intune Certificate Connector est nécessaire pour utiliser des profils de certificat SCEP avec Intune en cas d’utilisation d’une autorité de certification des services de certificats Active Directory. Le connecteur n’est pas nécessaire en cas d’utilisation d’[autorités de certification tierces](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration). 

Les informations contenues dans cet article peuvent vous aider à configurer votre infrastructure pour prendre en charge SCEP en cas d’utilisation des services de certificats Active Directory. Une fois votre infrastructure configurée, vous pouvez [créer et déployer des profils de certificat SCEP](certificates-profile-scep.md) avec Intune.

> [!TIP]
> Intune prend également en charge l’utilisation des [certificats standards PKCS #12](certficates-pfx-configure.md).

## <a name="prerequisites-for-using-scep-for-certificates"></a>Prérequis de l’utilisation de SCEP pour les certificats

Avant de continuer, vous devez avoir [créé et déployé un *profil de* certificat approuvé](certificates-configure.md#export-the-trusted-root-ca-certificate) sur les appareils qui doivent utiliser des profils de certificat SCEP. Les profils de certificat SCEP référencent directement le profil de certificat approuvé que vous utilisez pour provisionner des appareils avec un certificat d’autorité de certification racine de confiance.

### <a name="servers-and-server-roles"></a>Serveurs et rôles serveur

L’infrastructure locale suivante doit s’exécuter sur des serveurs joints à votre domaine Active Directory, à l’exception du serveur proxy d’application web.

- **Autorité de certification** : Utilisez une autorité de certification d’entreprise des services de certificats Active Directory Microsoft qui s’exécute sur une édition Entreprise de Windows Server 2008 R2 avec Service Pack 1 ou ultérieur. La version de Windows Server que vous utilisez doit toujours bénéficier du support Microsoft. Une autorité de certification autonome n'est pas prise en charge. Pour plus d’informations, consultez [Installer l’autorité de certification](https://technet.microsoft.com/library/jj125375.aspx). Si votre autorité de certification exécute Windows Server 2008 R2 SP1, vous devez [installer le correctif logiciel de KB2483564](https://support.microsoft.com/kb/2483564/).

- **Rôle serveur NDES** : Vous devez configurer un rôle serveur de service d’inscription de périphérique réseau (NDES) sur Windows Server 2012 R2 ou ultérieur. Dans une section ultérieure de cet article, nous vous guidons tout au long de l’[installation de NDES](#set-up-ndes).

  - Le serveur qui héberge NDES doit être joint à un domaine et se trouver dans la même forêt que votre AC d’entreprise.
  - Vous ne pouvez pas utiliser le service NDES installé sur le serveur qui héberge l’AC d’entreprise.
  - Vous installez Microsoft Intune Certificate Connector sur le même serveur qui héberge NDES.

  Pour plus d'informations sur NDES, consultez [Guide du service d’inscription de périphérique réseau](https://technet.microsoft.com/library/hh831498.aspx) dans la documentation de Windows Server et [Utilisation d’un module de stratégie avec le service d’inscription de périphérique réseau](https://technet.microsoft.com/library/dn473016.aspx).

- **Microsoft Intune Certificate Connector** : nécessaire pour utiliser des profils de certificat SCEP avec Intune. Cet article vous guide tout au long de l’[installation de ce connecteur](#install-the-intune-certificate-connector).

  Le connecteur prend également en charge le mode FIPS (Federal Information Processing Standard). FIPS n’est pas obligatoire, mais vous permet d’émettre et de révoquer des certificats quand il est activé.
  - Le connecteur doit s’exécuter sur le même serveur que le rôle serveur NDES, un serveur qui exécute Windows Server 2012 R2 ou version ultérieure.
  - .NET Framework 4.5 est exigé par le connecteur et automatiquement inclus avec Windows Server 2012 R2.
  - La configuration de sécurité renforcée d’Internet Explorer [doit être désactivée sur le serveur qui héberge NDES](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx) et Microsoft Intune Certificate Connector.

L’infrastructure locale suivante est facultative :

Pour permettre aux appareils sur Internet d’obtenir des certificats, vous devez publier votre URL NDES externe sur votre réseau d’entreprise. Vous pouvez utiliser le proxy d’application Azure AD, le serveur proxy d’application web ou un autre proxy inverse.

- **Proxy d’application Azure AD** (facultatif) : Vous pouvez utiliser le proxy d’application Azure AD à la place d’un serveur proxy d’application web dédié pour publier votre URL NDES sur Internet. Cela permet à la fois aux appareils sur intranet et Internet d’obtenir des certificats. Pour plus d’informations, consultez le [Guide pratique pour offrir un accès à distance sécurisé aux applications locales](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).

- **Serveur proxy d’application web** (facultatif) : Utilisez un serveur qui exécute Windows Server 2012 R2 ou ultérieur comme serveur proxy d’application web pour publier votre URL NDES sur Internet.  Cela permet à la fois aux appareils sur intranet et Internet d’obtenir des certificats.

  Le serveur qui héberge le proxy d'application web [doit installer une mise à jour](https://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) qui permet la prise en charge des longues URL utilisées par le service d'inscription d'appareil réseau. Cette mise à jour est incluse dans le [correctif cumulatif de décembre 2014](https://support.microsoft.com/kb/3013769), ou individuellement à partir de l'article [KB3011135](https://support.microsoft.com/kb/3011135).

  Le serveur proxy d’application web doit avoir un certificat SSL qui correspond au nom publié sur les clients externes et approuver le certificat SSL utilisé sur l’ordinateur qui héberge le service NDES. Ces certificats permettent au serveur proxy d’application web de mettre fin à la connexion SSL à partir des clients et de créer une connexion SSL au service NDES.

  Pour plus d’informations, consultez [Planification de certificats pour WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates) et [Informations générales sur les serveurs WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11)).

### <a name="accounts"></a>Comptes

- **Compte de service NDES** : Avant de configurer NDES, identifiez un compte d’utilisateur de domaine à utiliser comme compte de service NDES. Vous spécifiez ce compte quand vous configurez des modèles sur votre autorité de certification émettrice avant de configurer NDES.

  Ce compte doit avoir les droits suivants sur le serveur qui héberge NDES :

  - **Ouvrir une session localement**
  - **Ouvrir une session en tant que service**
  - **Ouvrir une session en tant que tâche**

  Pour plus d’informations, consultez [Créer un compte d’utilisateur de domaine faisant office de compte de service NDES](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account).

- **Accès à l’ordinateur qui héberge le service NDES** : Vous avez besoin d’un compte d’utilisateur de domaine avec les autorisations nécessaires pour installer et configurer des rôles serveur Windows sur le serveur où vous installez NDES.

- **Accès à l’autorité de certification** : Vous avez besoin d’un compte d’utilisateur de domaine avec les droits nécessaires pour gérer votre autorité de certification.

### <a name="network-requirements"></a>Conditions requises en matière de réseau

Nous vous recommandons de publier le service NDES par le biais d’un proxy inverse, comme le [proxy d’application Azure AD, le proxy d’accès web](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/) ou un proxy tiers. Si vous n’utilisez pas de proxy inverse, autorisez le trafic TCP sur le port 443 en provenance de l’ensemble des hôtes/adresses IP sur Internet et à destination du service NDES.

Autorisez tous les ports et protocoles nécessaires pour assurer la communication entre le service NDES et toute infrastructure de prise en charge dans votre environnement. Par exemple, l’ordinateur qui héberge le service NDES doit communiquer avec l’autorité de certification, les serveurs DNS, les contrôleurs de domaine et éventuellement d’autres services ou serveurs au sein de votre environnement, comme Configuration Manager.

### <a name="certificates-and-templates"></a>Certificats et modèles

Les certificats et les modèles suivants sont utilisés avec SCEP.

|Objet    |Détails    |
|----------|-----------|
|**Modèle de certificat SCEP**         |Modèle que vous configurez sur l’autorité de certification émettrice que vous utilisez pour répondre aux demandes SCEP des appareils. |
|**Certificat d’authentification client** |Demandé auprès de votre autorité de certification émettrice ou de votre autorité de certification publique.<br /> Vous installez ce certificat sur l’ordinateur qui héberge le service NDES pour qu’il soit utilisé par Intune Certificate Connector.<br /> Si le certificat utilise des clés pour l’*authentification serveur* et *client* (**utilisations améliorées de la clé**) sur le modèle d’autorité de certification que vous utilisez pour émettre ce certificat, vous pouvez utiliser le même certificat pour l’authentification serveur et client. |
|**Certificat d’authentification serveur** |Certificat de serveur web demandé auprès de votre autorité de certification émettrice ou de votre autorité de certification publique.<br /> Vous installez et liez ce certificat SSL dans IIS sur l’ordinateur qui héberge NDES.<br />Si le certificat utilise des clés pour l’*authentification serveur* et *client* (**utilisations améliorées de la clé**) sur le modèle d’autorité de certification que vous utilisez pour émettre ce certificat, vous pouvez utiliser le même certificat pour l’authentification serveur et client. |
|**Certificat d’autorité de certification racine approuvée**       |Pour utiliser un profil de certificat SCEP, les appareils doivent approuver votre autorité de certification racine de confiance. Utilisez un *profil de certificat approuvé* dans Intune afin de provisionner le certificat d’autorité de certification racine de confiance pour les utilisateurs et les appareils. <br/><br/> **-**  Utilisez un seul certificat d’autorité de certification racine de confiance par plateforme de système d’exploitation et associez-le à chaque profil de certificat approuvé que vous créez. <br /><br /> **-**  Vous pouvez utiliser des certificats d’autorité de certification racine de confiance supplémentaires selon vos besoins. Par exemple, vous pouvez le faire pour approuver une autorité de certification qui signe les certificats d’authentification serveur pour vos points d’accès Wi-Fi. Créez des certificats d’autorité de certification racine de confiance supplémentaires pour les autorités de certification émettrices.  Dans le profil de certificat SCEP que vous créez dans Intune, veillez à spécifier le profil d’autorité de certification racine de confiance pour l’autorité de certification émettrice.<br/><br/> Pour plus d’informations sur le profil de certificat approuvé, consultez [Exporter le certificat d’autorité de certification racine de confiance](certificates-configure.md#export-the-trusted-root-ca-certificate) et [Créer des profils de certificat approuvés](certificates-configure.md#create-trusted-certificate-profiles) dans *Utiliser des certificats pour l’authentification dans Intune*. |

## <a name="configure-the-certification-authority"></a>Configurer l’autorité de certification

Dans les sections suivantes, vous voyez comment :

- Configurer et publier le modèle nécessaire pour NDES.
- Définir les autorisations nécessaires pour la révocation des certificats.

Pour suivre les sections suivantes, vous devez connaître Windows Server 2012 R2 ou ultérieur, ainsi que les services de certificats Active Directory (AD CS).

### <a name="access-your-issuing-ca"></a>Accéder à votre autorité de certification émettrice

1. Pour vous connecter à votre autorité de certification émettrice, utilisez un compte de domaine avec des droits suffisants pour gérer l’autorité de certification.

2. Ouvrez la console Microsoft Management Console (MMC) Autorité de certification. **Exécutez** « certsrv.msc » ou, dans **Gestionnaire de serveur**, cliquez sur **Outils** et **Autorité de certification**.

3. Sélectionnez le nœud **Modèles de certificat**, cliquez sur **Action** > **Gérer**.

### <a name="create-the-scep-certificate-template"></a>Créer un modèle de certificat SCEP

1. Créez un modèle de certificat v2 (avec une compatibilité Windows 2003) à utiliser comme modèle de certificat SCEP. Vous pouvez :

   - Utilisez le composant logiciel enfichable *Modèles de certificat* pour créer un modèle personnalisé.
   - Copiez un modèle existant (comme le modèle utilisateur), puis mettez à jour la copie pour l’utiliser comme modèle NDES.

2. Configurez les paramètres suivants sur les onglets spécifiés du modèle :

   - **Général** :

     - Décochez **Publier le certificat dans Active Directory**.
     - Spécifiez un **nom d’affichage de modèle** convivial pour pouvoir identifier ce modèle par la suite.

   - **Nom de l’objet** :

     - Sélectionnez **Fournir dans la demande**. La sécurité est appliquée par le module de stratégie Intune pour NDES.

       ![Onglet Modèle, Nom du sujet](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)

   - **Extensions** :

     - Vérifiez que **Description des stratégies d’application** inclut **Authentification client**.

       > [!IMPORTANT]
       > Ajoutez uniquement les stratégies d’application dont vous avez besoin. Confirmez vos choix avec vos administrateurs de sécurité.

     - Pour les modèles de certificat iOS et macOS, modifiez aussi **Utilisation de la clé** et vérifiez que **Signature faisant preuve de l’origine** n’est pas sélectionnée.

     ![Onglet Modèle, Extensions](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **Sécurité** :

     - Ajoutez le **compte de service NDES**. Ce compte nécessite les autorisations **Lire** et **Inscrire** sur ce modèle.

     - Ajoutez des comptes supplémentaires pour les administrateurs Intune qui doivent créer des profils SCEP. Ces comptes nécessitent les autorisations **Lire** sur le modèle pour permettre à ces administrateurs d’accéder au modèle afin de créer des profils SCEP.

     ![Onglet Modèle, Sécurité](./media/certificates-scep-configure/scep-ndes-security.jpg)

   - **Traitement de la demande** :

     L’image suivante est un exemple. Votre configuration peut varier.  

     ![Onglet Modèle, Traitement de la demande](./media/certificates-scep-configure/scep-ndes-request-handling.png)

   - **Conditions d’émission** :

     L’image suivante est un exemple. Votre configuration peut varier.

     ![Onglet Modèle, Conditions d’émission](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)

3. Enregistrez le modèle de certificat.

### <a name="create-the-client-certificate-template"></a>Créer le modèle de certificat client

Intune Certificate Connector nécessite un certificat avec utilisation améliorée de la clé pour l’*authentification client* et un nom d’objet égal au nom de domaine complet de l’ordinateur où est installé le connecteur. Un modèle avec les propriétés suivantes est nécessaire :

- **Extensions** > **Les stratégies d’application** doivent contenir une **Authentification du client**
- **Nom de l’objet** > **Fourni dans la demande**.

Si vous avez déjà un modèle avec ces propriétés, vous pouvez le réutiliser, sinon créez-en un en dupliquant un modèle existant ou en créant un modèle personnalisé.

### <a name="create-the-server-certificate-template"></a>Créer le modèle de certificat de serveur

Les communications entre les appareils gérés et IIS sur le serveur NDES utilisent le protocole HTTPS, qui nécessite l’utilisation d’un certificat. Vous pouvez utiliser le modèle de certificat **Serveur web** pour émettre ce certificat. Sinon, si vous préférez avoir un modèle dédié, vous devez configurer les propriétés suivantes :

- **Extensions** > **Les stratégies d’application** doivent contenir une **Authentification serveur**
- **Nom de l’objet** > **Fourni dans la demande**.

> [!NOTE]
> Si vous avez un certificat conforme aux exigences des modèles de certificat du client et du serveur, vous pouvez utiliser un seul certificat pour IIS et Intune Certificate Connector.

### <a name="grant-permissions-for-certificate-revocation"></a>Accorder des autorisations pour la révocation des certificats

Pour qu’Intune puisse révoquer les certificats qui ne sont plus nécessaires, vous devez accorder des autorisations dans l’autorité de certification.

Sur Intune Certificate Connector, vous pouvez utiliser le **compte système** du serveur NDES ou un compte spécifique comme le **compte de service NDES**.

1. Dans la console Autorité de certification, cliquez avec le bouton droit sur le nom de l’autorité de certification et sélectionnez **Propriétés**.

2. Sous l’onglet **Sécurité**, cliquez sur **Ajouter**.

3. Accordez l’autorisation **Émettre et gérer des certificats** :

   - Si vous choisissez d’utiliser le **compte système** du serveur NDES, fournissez les autorisations au serveur NDES.
   - Si vous choisissez d’utiliser le **compte de service NDES**, fournissez les autorisations pour ce compte à la place.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>Modifier la période de validité du modèle de certificat

Vous n’êtes pas obligé de modifier la période de validité du modèle de certificat.  

Après avoir [créé le modèle de certificat SCEP](#create-the-scep-certificate-template), vous pouvez modifier le modèle pour vérifier la **Période de validité** sous l’onglet **Général**.

Par défaut, Intune utilise la valeur configurée dans le modèle. Toutefois, vous pouvez configurer l’autorité de certification pour permettre au demandeur d’entrer une valeur différente, que vous pouvez alors définir à partir de la console d’administration Intune.

> [!IMPORTANT]
> Pour iOS et macOS, utilisez toujours une valeur définie dans le modèle.

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Pour configurer une valeur qui peut être définie à partir de la console Intune

1. Dans l’autorité de certification, exécutez les commandes suivantes :

   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   -**net stop certsvc**
   -**net start certsvc**

2. Sur l'autorité de certification émettrice, utilisez le composant logiciel enfichable Autorité de Certification pour publier le modèle de certificat. Sélectionnez le nœud **Modèles de certificat**, sélectionnez **Action** > **Nouveau** > **Modèle de certificat à délivrer**, puis sélectionnez le modèle de certificat que vous avez créé dans la section précédente.

3. Vérifiez que le modèle est publié en le consultant dans le dossier **Modèles de certificat**.

## <a name="set-up-ndes"></a>Configurer NDES

Les procédures suivantes peuvent vous aider à configurer le service d’inscription de périphériques réseau (NDES) pour l’utiliser avec Intune. Pour plus d’informations sur NDES, consultez [Guide du service d’inscription de périphériques réseau](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11)).

### <a name="install-the-ndes-service"></a>Installer le service NDES

1. Sur le serveur qui héberge votre service NDES, connectez-vous comme **Administrateur d’entreprise**, puis utilisez l’[Assistant Ajout de rôles et de fonctionnalités](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11)) pour installer NDES :

   1. Dans l'Assistant, sélectionnez **Services de certificats Active Directory** pour accéder aux services de rôle AD CS. Sélectionnez **Service d’inscription de périphériques réseau**, décochez **Autorité de certification**, puis exécutez l’Assistant.

      > [!TIP]
      > Dans **Progression de l’installation**, ne sélectionnez pas **Fermer**. Sélectionnez à la place le lien **Configurer les services de certificats Active Directory sur le serveur de destination**. L’Assistant **Configuration des services AD CS** s’ouvre. Vous l’utilisez dans la procédure suivante de cet article, *Configurer le service NDES*. Une fois l'Assistant Configuration AD CS ouvert, vous pouvez fermer l'Assistant Ajout de rôles et de fonctionnalités.

   2. Lorsque NDES est ajouté au serveur, l'Assistant installe également IIS. Vérifiez qu’IIS a les configurations suivantes :

      - **Serveur Web** > **Sécurité** > **Filtrage des demandes**
      - **Serveur Web** > **Développement d’applications** > **ASP.NET 3.5**.

        L’installation d’ASP.NET 3.5 installe le .NET Framework 3.5. Quand vous installez .NET Framework 3.5, installez à la fois le **.NET Framework 3.5** et **Activation HTTP**.

      - **Serveur Web** > **Développement d’applications** > **ASP.NET 4.5**.

        L’installation d’ASP.NET 4.5 installe le .NET Framework 4.5. Quand vous installez le .NET Framework 4.5, installez à la fois la fonctionnalité **.NET Framework 4.5** de base, **ASP.NET 4.5** et la fonctionnalité **Services WCF** > **Activation HTTP**.

      - **Outils de gestion** > **IIS 6 Management Compatibility** > **Compatibilité avec la métabase de données IIS 6**
      - **Outils de gestion** > **IIS 6 Management Compatibility** > **Compatibilité WMI d’IIS 6**
      - Sur le serveur, ajoutez le compte de service NDES comme membre du groupe **IIS_IUSR** local.

2. Sur l’ordinateur qui héberge le service NDES, exécutez la commande suivante dans une invite de commandes avec élévation de privilèges. La commande suivante définit le SPN du compte de service NDES :

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`

   Par exemple, si l’ordinateur qui héberge le service NDES s’appelle **Server01**, que votre domaine est **Contoso.com** et que le compte de service est **NDESService**, utilisez :

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>Configurer le service NDES

1. Sur l’ordinateur qui héberge le service NDES, ouvrez l’Assistant **Configuration des services AD CS**, puis effectuez les mises à jour suivantes :

   > [!TIP]
   > Si vous avez effectué la procédure précédente et que vous avez cliqué sur le lien **Configurer les services de certificats Active Directory sur le serveur de destination**, cet Assistant doit déjà être ouvert. Sinon, ouvrez le Gestionnaire de serveur pour accéder à la configuration de post-déploiement pour les services de certificats Active Directory.

   - Dans **Services de rôle**, sélectionnez le **Service d’inscription de périphériques réseau**.
   - Dans **Compte de service pour NDES**, spécifiez le compte de service NDES.
   - Dans **Autorité de certification pour NDES**, cliquez sur **Sélectionner**, puis sélectionnez l’autorité de certification émettrice où vous avez configuré le modèle de certificat.
   - Dans **Chiffrement pour NDES**, définissez la longueur de la clé pour répondre aux besoins de votre entreprise.
   - Dans **Confirmation**, sélectionnez **Configurer** pour terminer l’Assistant.

2. Une fois l’Assistant exécuté, mettez à jour la clé de Registre suivante sur l’ordinateur qui héberge le service NDES :

   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

   Pour mettre à jour cette clé, identifiez le **rôle** des modèles de certificat (qui se trouvent sous l’onglet **Traitement de la demande**). Ensuite, mettez à jour l’entrée de Registre correspondante en remplaçant les données existantes par le nom du modèle de certificat (et pas par le nom d’affichage du modèle) que vous avez spécifié quand vous avez [créé le modèle de certificat](#create-the-scep-certificate-template).

   Le tableau suivant mappe le rôle de modèle de certificat aux valeurs du Registre :

   |Rôle de modèle de certificat (onglet Traitement de la demande)|Valeur du Registre à modifier|Valeur indiquée dans la console d’administration Intune pour le profil SCEP|
   |------------------------|-------------------------|---|
   |Signature               |SignatureTemplate        |Signature numérique |
   |Chiffrement              |EncryptionTemplate       |Chiffrement de la clé  |
   |Signature et chiffrement|GeneralPurposeTemplate   |Chiffrement de la clé <br/> Signature numérique |

   Par exemple, si le rôle de votre modèle de certificat est **Chiffrement**, remplacez la valeur de **EncryptionTemplate** par le nom de votre modèle de certificat.

3. Configurez le filtrage des demandes IIS pour ajouter la prise en charge dans IIS des URL longues (requêtes) que le service NDES reçoit.

   1. Dans le Gestionnaire IIS, sélectionnez **Site web par défaut** > **Filtrage des demandes** > **Modifier les paramètres de la fonctionnalité** pour ouvrir la page **Modifier les paramètres de filtrage des demandes**.

   2. Configurez les paramètres suivants :

      - **Longueur maximale des URL (octets)** = 65534
      - **Longueur maximale des chaînes de requête (octets)** = 65534

   3. Sélectionnez **OK** pour enregistrer cette configuration et fermer le Gestionnaire IIS.

   4. Validez cette configuration en consultant la clé de Registre suivante pour confirmer qu’elle a les valeurs indiquées :

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

      Les valeurs suivantes sont définies comme des entrées DWORD :

      - Nom : **MaxFieldLength**, avec une valeur décimale de **65534**
      - Nom : **MaxRequestBytes**, avec une valeur décimale de **65534**

4. Redémarrez le serveur qui héberge le service NDES. N’utilisez pas **iisreset**, car iireset n’effectue pas les changements nécessaires.

5. Accédez à *http://* Server_FQDN */certsrv/mscep/mscep.dll*. Vous devez voir une page NDES similaire à l’image suivante :

   ![Page NDES test](./media/certificates-scep-configure/scep-ndes-url.png)

   Si l’adresse web retourne une erreur **503 Service non disponible**, consultez l’observateur d’événements de l’ordinateur. Cette erreur se produit généralement quand le pool d’applications est arrêté en raison de l’absence d’une [autorisation pour le compte de service NDES](#accounts).
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>Installer et lier des certificats sur le serveur qui héberge NDES

> [!TIP]
> Dans la procédure suivante, vous pouvez utiliser un seul certificat pour l’*authentification serveur* et l’*authentification client* quand ce certificat est configuré pour répondre aux critères des deux utilisations. Les critères de chaque utilisation sont décrits dans les étapes 1 et 3 de la procédure suivante.

1. Demandez un certificat d’**authentification serveur** auprès de votre autorité de certification interne ou autorité de certification publique, puis installez le certificat sur le serveur.

   Si le serveur utilise un nom interne et externe pour une même adresse réseau, le certificat d’authentification serveur doit avoir :

   - Un **nom d’objet** avec un nom de serveur public externe.
   - Un **autre nom de l’objet** qui inclut le nom de serveur interne.

2. Liez le certificat d’authentification serveur dans IIS :

   1. Après avoir installé le certificat d’authentification serveur, ouvrez le **Gestionnaire IIS**, puis sélectionnez le **Site web par défaut**. Dans le volet **Actions**, sélectionnez **Liaisons**.

   1. Sélectionnez **Ajouter**, définissez **Type** avec la valeur **https**, puis vérifiez que le port est **443**.
   
   1. Pour **Certificat SSL**, spécifiez le certificat d'authentification serveur.

3. Sur votre serveur NDES, demandez et installez un certificat d' **authentification client** auprès de votre autorité de certification interne ou d'une autorité de certification publique.

   Le certificat d'authentification client doit avoir les propriétés suivantes :

   - **Utilisation améliorée de la clé** : Cette valeur doit inclure l’**authentification client**.
   - **Nom de l’objet** : La valeur doit être équivalente au nom DNS du serveur où vous installez le certificat (serveur NDES).

4. Le serveur qui héberge le service NDES est maintenant prêt à prendre en charge Intune Certificate Connector.

## <a name="install-the-intune-certificate-connector"></a>Installer Intune Certificate Connector

Microsoft Intune Certificate Connector s’installe sur le serveur qui exécute votre service NDES. Vous ne pouvez pas utiliser NDES ou Intune Certificate Connector sur le même serveur que celui de votre autorité de certification émettrice.

### <a name="to-install-the-certificate-connector"></a>Installer Certificate Connector

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Administration client** > **Connecteurs et jetons** > **Connecteurs de certificat** > **Ajouter**.

3. Téléchargez et enregistrez le fichier du connecteur pour SCEP. Enregistrez-le dans un emplacement accessible à partir du serveur où vous allez installer le connecteur.

   ![Téléchargement de Connector](./media/certificates-scep-configure/download-certificates-connector.png)

4. Une fois le téléchargement terminé, accédez au serveur qui héberge le rôle Service d’inscription de périphériques réseau (NDES). Ensuite :

   1. Vérifiez que .NET Framework 4.5 est installé, car il est demandé par Intune Certificate Connector. .NET Framework 4.5 est automatiquement inclus avec Windows Server 2012 R2 et ses versions plus récentes.

   2. Exécutez le programme d’installation (**NDESConnectorSetup.exe**). Le programme d’installation installe également le module de stratégie pour NDES et le service web Point d’enregistrement de certificat (CRP). Le service web CRP, *CertificateRegistrationSvc*, s’exécute comme une application dans IIS.

      - Quand vous installez NDES pour la version autonome d’Intune, le service CRP est installé automatiquement avec Certificate Connector.
      - Quand vous utilisez Intune avec Configuration Manager, vous installez le Point d’enregistrement de certificat comme un rôle de système de site Configuration Manager.

5. Quand vous êtes invité à entrer le certificat client pour Certificate Connector, choisissez **Sélectionner**, puis sélectionnez le certificat d’**authentification client** que vous avez installé sur votre serveur NDES à l’étape 3 de la procédure [Installer et lier des certificats sur le serveur qui héberge NDES](#install-and-bind-certificates-on-the-server-that-hosts-ndes), plus haut dans cet article.

   Après avoir sélectionné le certificat d’authentification client, vous êtes redirigé vers **Certificat client pour Microsoft Intune Certificate Connector**. Bien que le certificat sélectionné n’apparaisse pas, sélectionnez **Suivant** pour voir les propriétés du certificat. Sélectionnez **Suivant**, puis **Installer**.

6. Une fois l’Assistant terminé, mais avant de fermer l’Assistant, sélectionnez **Lancer l’interface utilisateur de Certificate Connector**.

   Si vous avez fermé l’Assistant avant de lancer l’interface utilisateur de Certificate Connector, vous pouvez le rouvrir en exécutant la commande suivante :

   *<chemin_installation>\NDESConnectorUI\NDESConnectorUI.exe*

7. Dans l'interface utilisateur de **Certificate Connector** :

   1. Sélectionnez **Connexion** et entrez vos informations d’identification du service Intune ou les informations d’identification d’un administrateur client avec l’autorisation d’administration globale.

   2. Une licence Intune valide doit être attribuée au compte que vous utilisez.

   3. Une fois la connexion établie, Intune Certificate Connector télécharge un certificat d’Intune. Ce certificat est utilisé pour l’authentification entre le connecteur et Intune. Si le compte que vous avez utilisé n’a pas de licence Intune, le connecteur (NDESConnectorUI.exe) ne parvient pas à obtenir le certificat auprès d’Intune.  

      Si votre organisation utilise un serveur proxy et que ce dernier est nécessaire au serveur NDES pour accéder à Internet, sélectionnez **Utiliser un serveur proxy**. Ensuite, entrez le nom, le port et les informations d’identification de compte du serveur proxy pour vous connecter.

   4. Sélectionnez l’onglet **Avancé**, puis entrez les informations d’identification d’un compte qui possède l’autorisation **Émettre et gérer des certificats** sur votre autorité de certification émettrice. **Appliquez** vos modifications.  

    5. Vous pouvez maintenant fermer l'interface utilisateur de Certificate Connector.

8. Ouvrez une invite de commandes, entrez **services.msc**, puis appuyez sur **Entrée**. Cliquez avec le bouton droit sur **Service du connecteur Intune** > **Redémarrer**.

Pour valider que le service s’exécute, ouvrez un navigateur et entrez l’URL suivante. Vous devez obtenir une erreur **403** : `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> Intune Certificate Connector prend en charge TLS 1.2. TLS 1.2 est utilisé si le serveur qui héberge le connecteur le prend en charge. Si le serveur ne prend pas en charge TLS 1.2, TLS 1.1 est utilisé. Actuellement, TLS 1.1 est utilisé pour l’authentification entre les appareils et le serveur.

## <a name="next-steps"></a>Étapes suivantes

[Créer un profil de certificat SCEP](certificates-profile-scep.md)  
[Résoudre les problèmes d’Intune Certificate Connector](troubleshoot-certificate-connector-events.md)
