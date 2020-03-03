---
title: Créer un profil de certificat dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez comment utiliser des certificats et des profils de certificat SCEP (Simple Certificate Enrollment Protocol) et PKCS (Public Key Cryptography Standards) avec Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63fa9f461fc9884d8c21e40cb4b5e3831f3b4b03
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576529"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Utiliser des certificats pour l’authentification dans Microsoft Intune

Utilisez des certificats avec Intune pour authentifier vos utilisateurs dans les applications et les ressources de l’entreprise avec des profils VPN, Wi-Fi ou e-mail. Quand vous utilisez des certificats pour authentifier ces connexions, vos utilisateurs finaux n’ont pas besoin d’entrer un nom d’utilisateur et un mot de passe, ce qui leur permet de bénéficier d’un accès transparent. Les certificats sont également utilisés pour signer et chiffrer les e-mails à l’aide de S/MIME.

## <a name="intune-supported-certificates-and-usage"></a>Certificats pris en charge par Intune et utilisation

| Type              | Authentification | Signature S/MIME | Chiffrement S/MIME  |
|--|--|--|--|
| Certificat importé PKCS (Public Key Cryptography Standards) |  | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png)|
| PKCS#12 (ou PFX)    | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) |  |
| Protocole SCEP (Simple Certificate Enrollment Protocol)  | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | |

Pour déployer ces certificats, vous créez des profils de certificat et les attribuez à des appareils.

Chaque profil de certificat que vous créez prend en charge une seule plateforme. Par exemple, si vous utilisez des certificats PKCS, vous créez un profil de certificat PKCS pour Android et un autre profil de certificat PKCS pour iOS/iPadOS. Si vous utilisez également des certificats SCEP pour ces deux plateformes, vous créez un profil de certificat SCEP pour Android et un autre pour iOS/iPadOS.

### <a name="general-considerations-when-you-use-a-microsoft-certification-authority"></a>Considérations générales relatives à l’utilisation d’une autorité de certification Microsoft

Quand vous utilisez une autorité de certification Microsoft (CA) :

- Pour utiliser les profils de certificat SCEP, vous devez [configurer un serveur de service d’inscription de périphérique réseau (NDES)](certificates-scep-configure.md#set-up-ndes) pour une utilisation avec Intune.
- Pour utiliser les types de profils de certificat suivants, vous devez [installer Microsoft Intune Certificate Connector](certificates-scep-configure.md#install-the-intune-certificate-connector) :
  - Profil de certification SCEP
  - Profil de certificat PKCS

- Pour utiliser les certificats PKCS importés :
  - [Installez PFX Certificate Connector pour Microsoft Intune](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
  - Exportez les certificats de l’autorité de certification, puis importez-les dans Microsoft Intune. Voir le [projet PowerShell PFXImport](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

- Déployez des certificats à l’aide des mécanismes suivants :
  - [Profils de certificat approuvés](certificates-configure.md#create-trusted-certificate-profiles) pour déployer le certificat d’autorité de certification racine approuvé de votre autorité de certification racine ou intermédiaire (émettrice) sur les appareils
  - Profils de certificat SCEP
  - Profil de certificat PKCS
  - Profils de certificat PKCS importés

### <a name="general-considerations-when-you-use-a-third-party-certification-authority"></a>Considérations générales relatives à l’utilisation d’une autorité de certification tierce

Quand vous utilisez une autorité de certification tierce (hors Microsoft) :

- Pour utiliser des profils de certificat SCEP :
  - Configurez l’intégration avec une autorité de certification tierce à partir d’un de [nos partenaires pris en charge](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners). La configuration comprend les instructions de l’autorité de certification tierce pour terminer l’intégration de leur autorité de certification à Intune.
  - [Créez une application dans Azure AD](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration) qui délègue des droits à Intune pour effectuer la validation de demande de certificat SCEP.

- Les certificats importés PKCS impliquent [l’installation de PFX Certificate Connector pour Microsoft Intune](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).

- Déployez des certificats à l’aide des mécanismes suivants :
  - [Profils de certificat approuvés](certificates-configure.md#create-trusted-certificate-profiles) pour déployer le certificat d’autorité de certification racine approuvé de votre autorité de certification racine ou intermédiaire (émettrice) sur les appareils
  - Profils de certificat SCEP
  - Profils de certificat PKCS *(pris en charge uniquement avec la plateforme [DigiCert PKI](certificates-digicert-configure.md))*
  - Profils de certificat PKCS importés

## <a name="supported-platforms-and-certificate-profiles"></a>Profils de certificat et plateformes prises en charge

| Plate-forme              | Profil de certificat approuvé | Profil de certificat PKCS | Profil de certificat SCEP | Profil de certificat PKCS importé  |
|--|--|--|--|---|
| Administrateur d’appareil Android | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png)|  ![Pris en charge](./media/certificates-configure/green-check.png) |
| Android Entreprise <br> - Entièrement géré (propriétaire de l’appareil)   | ![Pris en charge](./media/certificates-configure/green-check.png) |   | ![Pris en charge](./media/certificates-configure/green-check.png) |   |
| Android Entreprise <br> - Dédié (propriétaire de l’appareil)   | ![Pris en charge](./media/certificates-configure/green-check.png)  |   | ![Pris en charge](./media/certificates-configure/green-check.png)  |   |
| Android Entreprise <br> - Profil professionnel    | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) |
| iOS/iPadOS                   | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) |
| macOS                 | ![Pris en charge](./media/certificates-configure/green-check.png) |  ![Pris en charge](./media/certificates-configure/green-check.png) |![Pris en charge](./media/certificates-configure/green-check.png)|![Pris en charge](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Pris en charge](./media/certificates-configure/green-check.png)  |  | ![Pris en charge](./media/certificates-configure/green-check.png)| ![Pris en charge](./media/certificates-configure/green-check.png) |
| Windows 8.1 et versions ultérieures |![Pris en charge](./media/certificates-configure/green-check.png)  |  |![Pris en charge](./media/certificates-configure/green-check.png) |   |
| Windows 10 et versions ultérieures  | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exporter le certificat d’autorité de certification racine de confiance

Pour utiliser des certificats PKCS, SCEP et PKCS importés, les appareils doivent approuver votre autorité de certification racine. Pour établir l’approbation, exportez le certificat d’autorité de certification racine de confiance, ainsi que les certificats d’autorité de certification intermédiaire ou émettrice, sous la forme d’un certificat public (.cer). Vous pouvez obtenir ces certificats auprès de l’autorité de certification émettrice ou de n’importe quel appareil qui approuve votre autorité de certification émettrice.

Pour exporter le certificat, consultez la documentation de votre autorité de certification. Vous devez exporter le certificat public dans un fichier .cer.  N’exportez pas la clé privée (fichier .pfx).

Vous utilisez ce fichier .cer pour [créer des profils de certificat approuvé](#create-trusted-certificate-profiles) afin de déployer ce certificat sur vos appareils.

## <a name="create-trusted-certificate-profiles"></a>Créer des profils de certificat approuvés

Créez un profil de certificat approuvé pour pouvoir créer un profil de certificat SCEP, PKCS ou PKCS importé. Le déploiement d’un profil de certificat approuvé garantit que chaque appareil reconnaît la légitimité de votre autorité de certification. Les profils de certificat SCEP référencent directement un profil de certificat approuvé. Les profils de certificat PKCS ne référencent pas directement le profil de certificat approuvé, mais référencent directement le serveur qui héberge votre autorité de certification. Les profils de certificat PKCS importé ne référencent pas directement le profil de certificat approuvé, mais peuvent l’utiliser sur l’appareil. Le déploiement d’un profil de certificat approuvé sur des appareils garantit que cette confiance est établie. Quand un appareil ne fait pas confiance à l’autorité de certification racine, la stratégie de profil de certificat SCEP ou PKCS échoue.

Créez un profil de certificat approuvé distinct pour chaque plateforme d’appareil que vous voulez prendre en charge, tout comme pour les profils de certificat SCEP, PKCS et PKCS importés.

### <a name="to-create-a-trusted-certificate-profile"></a>Pour créer un profil de certificat approuvé

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.

   ![Accéder à Intune et créer un profil pour un certificat approuvé](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Entrez les propriétés suivantes :

   - le **Nom** du profil ;
   - une **Description** (facultatif) ;
   - la **Plateforme** sur laquelle le profil sera déployé ;
   - **Type de profil** : **Certificat approuvé**.

4. Sélectionnez **Paramètres**, puis accédez au fichier .cer du certificat d’autorité de certification racine de confiance que vous avez exporté pour l’utiliser avec ce profil de certificat et sélectionnez **OK**.

5. Pour les appareils Windows 8.1 et Windows 10 uniquement, sélectionnez le **Magasin de destination** pour le certificat approuvé à partir de :

   - **Boutique de certificats de l’ordinateur - Racine**
   - **Boutique de certificats de l’ordinateur - Intermédiaire**
   - **Boutique de certificats de l’utilisateur - Intermédiaire**

6. Lorsque vous avez terminé, choisissez **OK**, revenez au volet **Créer un profil** et sélectionnez **Créer**.

Le profil apparaît dans la liste des profils de la page *Appareils – Profils de configuration*, avec le type de profil **Certificat approuvé**. Veillez à affecter ce profil aux appareils qui utilisent des certificats SCEP ou PKCS. Pour attribuer ce profil à des groupes, consultez [Attribuer des profils d’appareil](../configuration/device-profile-assign.md).

> [!NOTE]
> Les appareils Android peuvent afficher un message indiquant qu’un tiers a installé un certificat approuvé.

## <a name="additional-resources"></a>Ressources supplémentaires

- [Attribuer des profils d’appareils](../configuration/device-profile-assign.md)  
- [Utiliser S/MIME pour signer et chiffrer des e-mails](certificates-s-mime-encryption-sign.md)  
- [Utiliser l’autorité de certification tierce](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Étapes suivantes

Créez des profils de certificat SCEP, PKCS ou PKCS importé pour chaque plateforme que vous voulez utiliser. Pour continuer, consultez les articles suivants :

- [Configurer l’infrastructure pour prendre en charge les certificats SCEP avec Intune](certificates-scep-configure.md)  
- [Configurer et gérer les certificats PKCS avec Intune](certficates-pfx-configure.md)  
- [Créer un profil de certificat PKCS importé](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)
