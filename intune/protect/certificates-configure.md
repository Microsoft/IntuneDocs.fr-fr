---
title: Créer un profil de certificat dans Microsoft Intune - Azure | Microsoft Docs
description: Pour vos appareils, ajouter ou créer un profil de certificat en configurant un environnement de certificat SCEP ou PKCS, exporter le certificat public, créer le profil dans le portail Azure, puis affecter SCEP ou PKCS aux profils de certificat dans Microsoft Intune dans le portail Azure
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 74b920deeb5255f6f938f0c8b07eaab6d765e68e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722967"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Utiliser des certificats pour l’authentification dans Microsoft Intune  

Utilisez des certificats avec Intune pour authentifier vos utilisateurs dans les applications et les ressources de l’entreprise avec des profils VPN, Wi-Fi ou e-mail. Quand vous utilisez des certificats pour authentifier ces connexions, vos utilisateurs finaux n’ont pas besoin d’entrer un nom d’utilisateur et un mot de passe, ce qui leur permet de bénéficier d’un accès transparent. Les certificats sont également utilisés pour signer et chiffrer les e-mails à l’aide de S/MIME.

Intune prend en charge les types de certificat suivants :  

- Protocole SCEP (Simple Certificate Enrollment Protocol)  
- PKCS#12 (ou PFX)  
- Certificats PKCS importés

Pour déployer ces certificats, vous créez des profils de certificat et les attribuez à des appareils.  

Chaque profil de certificat que vous créez prend en charge une seule plateforme. Par exemple, si vous utilisez des certificats PKCS, vous créez un profil de certificat PKCS pour Android et un autre profil de certificat PKCS pour iOS. Si vous utilisez également des certificats SCEP pour ces deux plateformes, vous créez un profil de certificat SCEP pour Android et un autre pour iOS.  

**Éléments généraux à prendre en compte** :  
- Si vous n’avez pas d’autorité de certification d’entreprise, vous devez la créer ou utiliser [celle d’un de nos partenaires pris en charge](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- Si vous utilisez des profils de certificat SCEP à l’aide des services de certificats Active Directory, vous configurez un serveur de service d’inscription de périphérique réseau (NDES).
- Si vous utilisez SCEP avec l’un de nos partenaires d’autorité de certification, vous devez [l’intégrer à Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Les profils de certificat SCEP et PKCS impliquent le téléchargement, l’installation et la configuration de Microsoft Intune Certificate Connector. 
- Les certificats PCKS importés impliquent le téléchargement, l’installation et la configuration de PFX Certificate Connector pour Microsoft Intune.
- Les certificats PKCS importés impliquent l’exportation des certificats de votre autorité de certification et leur importation dans Microsoft Intune. Voir le [projet PowerShell PFXImport](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- Pour qu’un appareil utilise des profils de certificat SCEP, PCKS ou PKCS importés, il doit approuver votre autorité de certification racine. Vous utilisez un *profil de certificat approuvé* pour déployer votre certificat d’autorité de certification racine de confiance sur les appareils.  

## <a name="supported-platforms-and-certificate-profiles"></a>Profils de certificat et plateformes prises en charge  
| Plate-forme              | Profil de certificat approuvé | Profil de certificat PKCS | Profil de certificat SCEP | Profil de certificat PKCS importé  |
|--|--|--|--|---|
| Administrateur d’appareil Android | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png)|  ![Pris en charge](./media/certificates-configure/green-check.png) |
| Android Entreprise <br> - Propriétaire de l’appareil   | ![Pris en charge](./media/certificates-configure/green-check.png) |   |  |   |
| Android Entreprise <br> - Profil professionnel    | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) |
| iOS                   | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) |
| macOS                 | ![Pris en charge](./media/certificates-configure/green-check.png) |   |![Pris en charge](./media/certificates-configure/green-check.png)|![Pris en charge](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Pris en charge](./media/certificates-configure/green-check.png)  |  | ![Pris en charge](./media/certificates-configure/green-check.png)| ![Pris en charge](./media/certificates-configure/green-check.png) |
| Windows 8.1 et versions ultérieures |![Pris en charge](./media/certificates-configure/green-check.png)  |  |![Pris en charge](./media/certificates-configure/green-check.png) |   |
| Windows 10 et versions ultérieures  | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) | ![Pris en charge](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exporter le certificat d’autorité de certification racine de confiance  
Pour utiliser des certificats PKCS, SCEP et PKCS importés, les appareils doivent approuver votre autorité de certification racine. Pour établir cette approbation, vous exportez le certificat d’autorité de certification racine de confiance, ainsi que les certificats d’autorité de certification intermédiaire ou émettrice, sous la forme d’un certificat public (.cer). Vous pouvez obtenir ces certificats auprès de l’autorité de certification émettrice ou de n’importe quel appareil qui approuve votre autorité de certification émettrice.  

Pour exporter le certificat, consultez la documentation de votre autorité de certification. Vous devez exporter le certificat public dans un fichier .cer.  N’exportez pas la clé privée (fichier .pfx).  

Vous utilisez ce fichier .cer pour [créer des profils de certificat approuvé](#create-trusted-certificate-profiles) afin de déployer ce certificat sur vos appareils.  

## <a name="create-trusted-certificate-profiles"></a>Créer des profils de certificat approuvés  
Créez un profil de certificat approuvé pour pouvoir créer un profil de certificat SCEP, PKCS ou PKCS importé. Le déploiement d’un profil de certificat approuvé garantit que chaque appareil reconnaît la légitimité de votre autorité de certification. Les profils de certificat SCEP référencent directement un profil de certificat approuvé. Les profils de certificat PKCS ne référencent pas directement le profil de certificat approuvé, mais référencent directement le serveur qui héberge votre autorité de certification. Les profils de certificat PKCS importé ne référencent pas directement le profil de certificat approuvé, mais peuvent l’utiliser sur l’appareil. Le déploiement d’un profil de certificat approuvé sur des appareils garantit que cette confiance est établie. Quand un appareil ne fait pas confiance à l’autorité de certification racine, la stratégie de profil de certificat SCEP ou PKCS échoue.  

Créez un profil de certificat approuvé distinct pour chaque plateforme d’appareil que vous voulez prendre en charge, tout comme pour les profils de certificat SCEP, PCKS et PKCS importés.  


### <a name="to-create-a-trusted-certificate-profile"></a>Pour créer un profil de certificat approuvé  

1. Connectez-vous au [portail Intune](https://aka.ms/intuneportal).  
2. Sélectionnez **Configuration de l’appareil** > **Gérer** > **Profils** > **Créer un profil**.  
3. Entrez un **nom et une description** pour le profil de certificat approuvé.  
4. Dans la liste déroulante **Plateforme**, sélectionnez la plateforme d’appareil pour ce certificat approuvé.  
5. Dans la liste déroulante **Type de profil**, choisissez **Certificat approuvé**.  
6. Accédez au fichier .cer du certificat d’autorité de certification racine de confiance que vous avez exporté pour l’utiliser avec ce profil de certificat, puis sélectionnez **OK**.  
7. Pour les appareils Windows 8.1 et Windows 10 uniquement, sélectionnez le **Magasin de destination** pour le certificat approuvé à partir de :  
   - **Boutique de certificats de l’ordinateur - Racine**
   - **Boutique de certificats de l’ordinateur - Intermédiaire**
   - **Boutique de certificats de l’utilisateur - Intermédiaire**
8. Lorsque vous avez terminé, choisissez **OK**, revenez au volet **Créer un profil** et sélectionnez **Créer**.
Le profil apparaît dans la liste des profils dans le volet de la vue *Configuration de l’appareil – Profils*, avec le type de profil **Certificat approuvé**.  Veillez à attribuer ce profil aux appareils qui utilisent des certificats SCEP ou PCKS. Pour attribuer ce profil à des groupes, consultez [Attribuer des profils d’appareil](../configuration/device-profile-assign.md).

> [!NOTE]  
> Les appareils Android peuvent afficher un message indiquant qu’un tiers a installé un certificat approuvé.  

## <a name="additional-resources"></a>Ressources supplémentaires  
- [Attribuer des profils d’appareils](../configuration/device-profile-assign.md)  
- [Utiliser S/MIME pour signer et chiffrer des e-mails](certificates-s-mime-encryption-sign.md)  
- [Utiliser l’autorité de certification tierce](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Étapes suivantes  
Une fois que vous avez créé et attribué des profils de certificat approuvé, créez des profils de certificat SCEP, PKCS ou PKCS importé pour chaque plateforme que vous voulez utiliser. Pour continuer, consultez les articles suivants :  
- [Configurer l’infrastructure pour prendre en charge les certificats SCEP avec Intune](certificates-scep-configure.md)  
- [Configurer et gérer les certificats PKCS avec Intune](certficates-pfx-configure.md)  
- [Créer un profil de certificat PKCS importé](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

