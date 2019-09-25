---
title: Utiliser des certificats PFX importés dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des certificats PKCS (Public Key Cryptography Standards) importés avec Microsoft Intune, notamment l’importation de certificats, la configuration du modèle de certificat, l’installation du connecteur Intune Imported PFX Certificate Connector et la création d’un profil Imported PKCS Certificate.
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 09/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f68ee794ce1fce2fbdbae8898c412309906b3f5c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167080"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Configurer et utiliser des certificats PKCS importés avec Intune

Microsoft Intune prend en charge l’utilisation de certificats de paire de clés publiques (PKCS) importés, couramment utilisés pour le chiffrement S/MIME avec les profils de messagerie. Certains profils de messagerie dans Intune prennent en charge une option permettant d’activer S/MIME dans laquelle vous pouvez définir un certificat de signature S/MIME et un certificat de chiffrement S/MIME.

Le chiffrement S/MIME est difficile, car le courrier électronique est chiffré avec un certificat spécifique. Vous devez disposer de la clé privée du certificat qui a chiffré le courrier électronique sur l’appareil sur lequel vous lisez le courrier afin de pouvoir le déchiffrer. Les certificats de chiffrement sont régulièrement renouvelés, ce qui signifie que vous aurez peut-être besoin de votre historique de chiffrement sur tous vos appareils pour vous assurer de pouvoir lire les e-mails plus anciens.  Étant donné que le même certificat doit être utilisé sur les appareils, il n’est pas possible d’utiliser des profils de certificat [SCEP](certificates-scep-configure.md) ou [PKCS](certficates-pfx-configure.md) à cet effet, car ces mécanismes de remise de certificat offrent des certificats uniques par appareil. 

Pour plus d’informations sur l’utilisation de S/MIME avec Intune, consultez [Utiliser S/MIME pour chiffrer les e-mails](certificates-s-mime-encryption-sign.md).

## <a name="requirements"></a>Configuration requise

Pour utiliser des certificats PKCS importés avec Intune, vous devez disposer de l’infrastructure suivante :

- **PFX Certificate Connector pour Microsoft Intune** :  
  Chaque abonné Intune prend en charge une seule instance de ce connecteur. Vous pouvez installer ce connecteur sur le même serveur qu’une instance de Microsoft Intune Certificate Connector.

  Ce connecteur gère les demandes des fichiers PFX importés dans Intune en vue de chiffrer les e-mails S/MIME pour un utilisateur spécifique.  

  Ce connecteur peut automatiquement se mettre à jour quand de nouvelles versions deviennent disponibles. Pour utiliser la fonctionnalité de mise à jour, vous devez vous assurer que des pare-feux sont ouverts autorisant le connecteur à contacter **autoupdate.msappproxy.net** sur le port **443**, pour recevoir automatiquement les mises à jour importantes.  

  Pour plus d’informations sur tous les points de terminaison réseau auxquels le connecteur accède, consultez [Configuration requise pour le réseau Intune et bande passante](network-bandwidth-use.md).


- **Windows Server** :  
  Vous utilisez un serveur Windows Server pour héberger PFX Certificate Connector pour Microsoft Intune.  Le connecteur permet de traiter les demandes de certificats importés dans Intune.

  Intune prend en charge l’installation de *Microsoft Intune Certificate Connector* sur le même réseau que celui où est installé *PFX Certificate Connector pour Microsoft Intune*.

  Pour prendre en charge le connecteur, le serveur doit exécuter .NET 4.6 Framework ou une version ultérieure. Si .NET 4.6 Framework n’est pas installé lorsque vous démarrez l’installation du connecteur, celle-ci l’installe automatiquement.

- **Visual Studio 2015 ou version ultérieure** (facultatif) : Vous utilisez Visual Studio pour générer le module d’assistance PowerShell avec des cmdlets pour l’importation de certificats PFX dans Microsoft Intune. Pour obtenir les cmdlets PowerShell d’assistance, consultez [Projet PowerShell PFXImport dans GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Fonctionnement

Quand vous utilisez Intune pour déployer un **certificat PFX importé** pour un utilisateur, deux composants sont impliqués en plus de l’appareil : 

- **Service Intune** : Stocke les certificats PFX dans un état chiffré et gère le déploiement du certificat sur l’appareil de l’utilisateur.  Les mots de passe protégeant les clés privées des certificats sont chiffrés avant d’être chargés à l’aide d’un module de sécurité matériel (HSM) ou du chiffrement Windows, ce qui garantit qu’Intune ne peut jamais accéder à la clé privée.
- **PFX Certificate Connector pour Microsoft Intune** : Quand un appareil demande un certificat PFX importé dans Intune, le mot de passe chiffré, le certificat et la clé publique de l’appareil sont envoyés au connecteur.  Le connecteur déchiffre le mot de passe à l’aide de la clé privée locale, puis chiffre à nouveau le mot de passe (et tous les profils plist si vous utilisez iOS) avec la clé de l’appareil avant de renvoyer le certificat à Intune.  Intune remet ensuite le certificat à l’appareil et l’appareil est en mesure de le déchiffrer avec la clé privée de l’appareil et d’installer le certificat.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Télécharger, installer et configurer PFX Certificate Connector pour Microsoft Intune

1. Dans le portail [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), sélectionnez **Configuration de l’appareil** > **Connecteurs de certification** > **Ajouter**.

   ![Téléchargement de PFX Certificate Connector pour Microsoft Intune](media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

2. Suivez les instructions pour télécharger *PFX Certificate Connector pour Microsoft Intune* vers un emplacement accessible à partir du serveur sur lequel vous allez installer le connecteur.
3. Une fois le téléchargement terminé, connectez-vous au serveur et exécutez le programme d’installation (PfxCertificateConnectorBootstrapper.exe).  
   - Lorsque vous acceptez l’emplacement d’installation par défaut, le connecteur est installé dans `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - Le service du connecteur s’exécute sous le compte système local. Si un proxy est exigé pour accéder à Internet, vérifiez que le compte de service local peut accéder aux paramètres de proxy du serveur.

4. Après l’installation, PFX Certificate Connector pour Microsoft Intune ouvre l’onglet **Inscription**. Pour activer la connexion à Intune, sélectionnez **Connexion** et spécifiez un compte disposant d’autorisations d’administrateur général ou d’administrateur Intune.

   > [!WARNING]
   > Par défaut, dans Windows Server **Configuration de sécurité renforcée d’Internet Explorer** est définie sur **Activé** ce qui peut entraîner des problèmes avec la connexion à Office 365.

5. Fermez la fenêtre.
6. Dans le portail Intune, revenez à **Configuration de l’appareil** > **Connecteurs de certification**. Après quelques minutes, une coche verte apparaît et **l’État de la connexion** est **Actif**. Le serveur de connecteur peut désormais communiquer avec Intune.

## <a name="import-pfx-certificates-to-intune"></a>Importer des certificats PFX dans Intune

Vous utilisez [Microsoft Graph](https://docs.microsoft.com/graph) pour importer les certificats PFX de vos utilisateurs dans Intune. Le [projet d’assistance PowerShell PFXImport sur GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) fournit des cmdlets pour faciliter les opérations.

Si vous préférez utiliser votre propre solution personnalisée à l’aide de Graph, utilisez le [type de ressource userPFXCertificate](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>Cmdlets de création de 'Projet PowerShell PFXImport'

Pour utiliser les cmdlets PowerShell, vous générez le projet vous-même à l’aide de Visual Studio. Le processus est simple et même s’il peut s’exécuter sur le serveur, nous vous recommandons de l’exécuter sur votre station de travail.  

1. Accédez à la racine du référentiel [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) sur GitHub, puis téléchargez ou clonez le référentiel avec Git sur votre ordinateur.

   ![Bouton de téléchargement GitHub](media/certificates-imported-pfx-configure/github-download.png)

2. Accédez à `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` et ouvrez le projet avec Visual Studio à l’aide du fichier **PFXImportPS.sln**.
3. En haut, passez de **Déboguer** à **Publier**.
4. Accédez à **Build**, puis sélectionnez **Générer PFXImportPS**. Après quelques instants, la confirmation de **Build réussie** s’affiche en bas à gauche de Visual Studio.

   ![Option de build de Visual Studio](media/certificates-imported-pfx-configure/vs-build-release.png)

5. Le processus de build crée un nouveau dossier avec le module PowerShell dans `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Vous utiliserez ce dossier **Publier** pour les étapes suivantes.

### <a name="create-the-encryption-public-key"></a>Créer la clé publique de chiffrement

Vous importez des certificats PFX et leurs clés privées dans Intune. Le mot de passe protégeant la clé privée est chiffré avec une clé publique stockée localement. Vous pouvez utiliser le chiffrement Windows, un module de sécurité matériel ou un autre type de chiffrement pour générer et stocker les paires de clés publiques/privées.  Selon le type de chiffrement utilisé, la paire de clés publique/privée peut être exportée dans un format de fichier à des fins de sauvegarde.

Le module PowerShell fournit des méthodes pour créer une clé à l’aide du chiffrement Windows. Vous pouvez également utiliser d’autres outils pour créer une clé.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Pour créer la clé de chiffrement à l’aide du chiffrement Windows

1. Copiez le dossier *Publier* créé par Visual Studio sur le serveur où vous avez installé **PFX Certificate Connector pour Microsoft Intune**. Ce dossier contient le module PowerShell.  
2. Sur le serveur, ouvrez *PowerShell* en tant qu’administrateur, puis accédez au dossier *Publier* qui contient le module PowerShell.
3. Pour importer le module, exécutez `Import-Module .\IntunePfxImport.psd1` pour importer le module.
4. Ensuite, exécutez `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]  
   > Le fournisseur que vous utilisez doit être sélectionné à nouveau lorsque vous importez des certificats PFX. Vous pouvez utiliser le **fournisseur de stockage de clés logicielles Microsoft**, bien qu’il soit possible d’utiliser un autre fournisseur. Le nom de la clé est également fourni à titre d’exemple et vous pouvez utiliser un autre nom de clé de votre choix.  

   Si vous prévoyez d’importer le certificat à partir de votre station de travail, vous pouvez exporter cette clé vers un fichier à l’aide de la commande suivante :  `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`

   La clé privée doit être importée sur le serveur qui héberge PFX Certificate Connector pour Microsoft Intune afin que les certificats PFX importés puissent être traités correctement.  

#### <a name="to-use-a-hardware-security-module-hsm"></a>Pour utiliser un module de sécurité matériel (HSM)  

Vous pouvez utiliser un module de sécurité matériel (HSM) pour générer et stocker la paire de clés publique/privée. Pour plus d'informations, consultez la documentation du fournisseur HSM.

### <a name="import-pfx-certificates"></a>Importer des certificats PFX 

Le processus suivant utilise les cmdlets PowerShell comme exemple d’importation des certificats PFX. Vous pouvez choisir différentes options en fonction de vos besoins.

Les options sont les suivantes :  
- Objectif prévu (regroupe les certificats en fonction d’une balise) :  
  - non attribué
  - smimeEncryption
  - smimeSigning


- Schéma de remplissage :  
  - pkcs1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

Sélectionnez le fournisseur de stockage de clés qui correspond au fournisseur que vous avez utilisé pour créer la clé.

#### <a name="to-import-the-pfx-certificate"></a>Pour importer le certificat PFX  

1. Exportez les certificats d’une autorité de certification en suivant la documentation du fournisseur.  Pour les services de certificats Microsoft Active Directory Certificate Services, vous pouvez utiliser [cet exemple de script](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b).   
2. Sur le serveur, ouvrez *PowerShell* en tant qu’administrateur, puis accédez au dossier *Publier* qui contient le module PowerShell.
3. Pour importer le module, exécutez `Import-Module .\IntunePfxImport.psd1`  
4. Pour vous authentifier auprès d’Intune Graph, exécutez `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`

   > [!NOTE]
   > Comme l’authentification est exécutée sur Graph, vous devez fournir des autorisations à l’AppID. Si c’est la première fois que vous utilisez cet utilitaire, un *administrateur général* est requis. Les cmdlets PowerShell utilisent le même AppID que celui utilisé avec les [exemples Intune PowerShell](https://github.com/microsoftgraph/powershell-intune-samples).   
5. Convertissez le mot de passe pour chaque fichier PFX que vous importez dans une chaîne sécurisée en exécutant `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`.  
6. Pour créer un objet **UserPFXCertificate**, exécutez `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`

   Par exemple : `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`

   > [!NOTE]  
   > Lorsque vous importez le certificat à partir d’un système autre que le serveur sur lequel le connecteur est installé, utilisez la commande suivante, qui comprend le chemin d’accès au fichier de clé : `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. Importez l’objet **UserPFXCertificate** dans Intune en exécutant `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`

8. Pour valider que le certificat a été importé, exécutez `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UsertList "<UserUPN>"`

Pour plus d’informations sur les autres commandes disponibles, consultez le fichier Lisez-moi dans [Projet PowerShell PFXImport sur GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Créer un profil de certificat importé PKCS

Après avoir importé les certificats dans Intune, créez un profil **Certificat PKCS importé** et affectez-le aux groupes Azure Active Directory.

1. Dans le portail [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), accédez à **Configuration de l’appareil** > **Profils** > **Créer un profil**.
2. Entrez les propriétés suivantes :

   - le **Nom** du profil ;
   - une description (facultatif) ;
   - la **Plateforme** sur laquelle le profil sera déployé ;
   - Définissez **Type de profil** sur **Certificat PKCS importé**.

3. Accédez à **Paramètres** et entrez les propriétés suivantes :

   - **Rôle prévu** : Indiquez la finalité des certificats qui sont importés pour ce profil. Les administrateurs peuvent importer des certificats avec différents rôles (par exemple, l’authentification, la signature S/MIME ou le chiffrement S/MIME). La finalité sélectionnée dans le profil de certificat correspond au profil de certificat comprenant les certificats importés associés. Le rôle prévu est une balise permettant de regrouper les certificats importés et ne garantit pas que les certificats importés avec cette balise seront conformes au rôle prévu.  
   - **Période de validité du certificat** : À moins que la période de validité n’ait été modifiée dans le modèle de certificat, cette option est définie par défaut sur un an.  
   - **Fournisseur de stockage de clés (KSP)**  : pour Windows, sélectionnez l’emplacement où stocker les clés sur l’appareil.  

4. Sélectionnez **OK** > **Créer** pour enregistrer votre profil.
5. Pour affecter le nouveau profil à un ou plusieurs appareils, consultez [Affecter des profils d’appareils Microsoft Intune](device-profile-assign.md).



