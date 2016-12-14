---
title: "Charger la version test des applications pour Windows et Windows Phone | Microsoft Intune"
description: "Découvrez comment connecter des applications métier afin de pouvoir utiliser Intune pour les déployer."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 938e3a1914f379d115bf24ebd7d990f6e1d319a9


---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signer des applications métier afin de pouvoir les déployer sur des appareils Windows avec Intune

En tant qu’administrateur Intune, vous pouvez déployer des applications métier sur des appareils Windows et Windows 10 Mobile, y compris l’application Portail d’entreprise. Pour déployer des applications .appx ou .xap sur des appareils Windows 10 et Windows 10 Mobile, ou déployer n’importe quelle application métier sur des appareils Windows 8.1 ou Windows Phone 8.1, vous devez obtenir un **certificat de signature de Code Symantec Enterprise Mobile**. Seul le certificat Symantec est approuvé pour ces applications pour les appareils Windows respectifs. Vous pouvez utiliser votre propre autorité de certification pour les applications Windows 10 et « universelles ». Ce certificat est requis pour :

-   Signer l’application Portail d’entreprise pour le déploiement sur des PC Windows, et sur des appareils Windows 10 Mobile et Windows Phone

-   Signer des applications métier pour que Intune puisse les déployer sur des appareils Windows

Les étapes ci-dessous vous aideront à obtenir les certificats requis et à signer les applications. Vous aurez besoin d'un compte du Centre de développement Windows Phone, puis vous devrez acheter un certificat Symantec.


1. **Rejoindre le centre de développement Windows Phone**<br>
   Rejoignez le [Centre de développement Windows Phone](http://go.microsoft.com/fwlink/?LinkId=268442) en utilisant des informations de compte d'entreprise quand vous vous connectez pour acheter votre compte d'entreprise. Cette demande devra être autorisée par un responsable de l'entreprise avant que vous ne receviez un certificat de signature de code.

2. **Obtenir un certificat Symantec d'entreprise**<br>
  Achetez un certificat sur le [site web de Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) à l'aide de votre identifiant Symantec. Après avoir acheté le certificat, l'approbateur d'entreprise que vous avez désigné dans votre compte Centre de développement Windows Phone recevra un e-mail lui demandant d'approuver la demande de certificat. Pour plus d’informations sur la nécessité d’obtenir un certificat Symantec, consultez la rubrique [Pourquoi Windows Phone requiert-il un certificat Symantec ?](https://technet.microsoft.com/en-us/library/dn764959.aspx#BKMK_Symantec) Forum Aux Questions sur l'inscription des appareils Windows.

3.  **Importer les certificats**<br>
    Une fois la demande approuvée, vous recevrez un e-mail contenant des instructions pour importer les certificats. Suivez les instructions de l'e-mail pour importer les certificats.

4.  **Vérifier les certificats importés**<br>
    Pour vérifier que les certificats ont été importés correctement, accédez au composant logiciel enfichable **Certificats** , cliquez avec le bouton droit sur **Certificats**, puis sélectionnez **Find Certificats**. Dans le champ **Contient** , indiquez « Symantec » et cliquez sur **Rechercher**. Les certificats que vous avez importés doivent apparaître dans les résultats.

    ![Rechercher le certificat Symantec](./media/wit.gif)

5. **Exporter un certificat de signature**<br>
    Après avoir vérifié que les certificats sont présents, vous pouvez exporter le fichier .pfx pour vous connecter au portail d’entreprise. Sélectionnez le certificat Symantec dont le **Rôle prévu** est « Signature du code ». Cliquez avec le bouton droit sur le certificat de signature de code et sélectionnez **Exporter**.

    ![Exporter le certificat de signature](./media/wit-walk-cert2.gif)

    Dans l' **Assistant Exportation de certificat**, sélectionnez **Oui, exporter la clé privée**, puis cliquez sur **Suivant**. Sélectionnez**Échange d’informations personnelles - PKCS #12 (.PFX)** et activez **Inclure tous les certificats dans le chemin d'accès de certification si possible**. Effectuez toutes les étapes de l'Assistant. Pour plus d'informations, voir [Comment exporter un certificat avec la clé privée](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Charger l’application sur Intune**<br>
    Chargez le fichier d’application signé et votre certificat de signature de code pour rendre l’application disponible pour vos utilisateurs finaux.

    1.  Dans la [console d’administration Intune](http://manage.microsoft.com), cliquez sur **Administration** &gt; **Windows Phone**.

    2.  Cliquez sur **Télécharger le fichier d’application signé** et connectez-vous avec votre ID d’administrateur Intune.

    3.  Ajoutez le fichier du certificat (.pfx) que vous avez exporté à **Certificat de signature de code** et créez un mot de passe pour le certificat.

    4.  Effectuez toutes les étapes de l'Assistant.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Exemple : Télécharger, signer et déployer l’application Portail d’entreprise pour les appareils Windows

Vous pouvez déployer l’application Portail d’entreprise sur les appareils Windows, y compris les appareils Windows Phone et Windows 10 Mobile avec Intune, au lieu de l’installer à partir du Windows Store. Vous devez télécharger l’application Portail d’entreprise et la signer avec votre certificat.  Cela n'est nécessaire que si vos utilisateurs ne sont pas appelés à utiliser le Store d'entreprise et si vous souhaitez déployer le Portail d'entreprise sur des appareils Windows Phone 8.1.


1.  **Télécharger le Portail d'entreprise**

    Pour déployer l’application Portail d’entreprise avec Intune, vous pouvez télécharger [l’application Portail d’entreprise Microsoft Intune pour Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) à partir du Centre de téléchargement et exécuter le fichier à extraction automatique (.exe). Ce fichier contient deux fichiers :

    -   CompanyPortal.appx : application d'installation du Portail d'entreprise pour Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1 : script PowerShell que vous pouvez utiliser pour signer le fichier de l'application Portail d'entreprise à des fins de déploiement vers des appareils Windows Phone 8.1

    Vous pouvez également télécharger le portail d’entreprise Windows Phone 8.1 (package sous licence hors connexion) ou le portail d’entreprise Windows 10 (package sous licence hors connexion) à partir du [Windows Store pour Entreprises](http://businessstore.microsoft.com/). L’application Portail d’entreprise doit être acquise avec une licence en mode hors connexion et le package approprié téléchargé pour une utilisation hors connexion. Les listes de plateformes Windows 8 et Windows Phone 8 dans la sélection font référence à leurs équivalents de la version 8.1. Pour plus d’informations sur la procédure à suivre avec Intune, consultez [Gérer les applications que vous avez achetées dans le Windows Store pour Entreprises](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).

2.  **Télécharger le Kit Windows Phone SDK** Téléchargez le Kit Windows Phone 8.0 SDK] (http://go.microsoft.com/fwlink/?LinkId=615570) et installez-le sur votre ordinateur. Ce SDK est nécessaire pour générer un jeton d'inscription d'application.

3.  **Générer un fichier AETX** Générez un fichier de jeton d’inscription d’application (.aetx) à partir du fichier PFX Symantec. Pour cela, utilisez le fichier AETGenerator.exe inclus dans Windows Phone 8.0 SDK. Pour obtenir des instructions sur la création d'un fichier AETX, consultez [Comment générer un jeton d'inscription d'application pour Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx).

4.  **Télécharger le SDK Windows pour Windows 8.1** Téléchargez et installez le [SDK Windows Phone](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Notez que le script PowerShell inclus avec l'application Portail d'entreprise utilise l'emplacement d'installation par défaut, à savoir `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Si vous effectuez l'installation à un autre emplacement, vous devez inclure celui-ci dans un paramètre d'applet de commande.

5.  **Signer le code de l’application à l’aide de PowerShell** En tant qu’administrateur, ouvrez **Windows PowerShell** sur l’ordinateur hôte sur lequel sont installés le SDK Windows et le certificat de signature de code Symantec Enterprise Mobile, accédez au fichier Sign-WinPhoneCompanyPortal.ps1, puis exécutez le script.

    **Exemple 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    Cet exemple signe le fichier CompanyPortal.appx à l'emplacement C:\temp\ et produit le fichier CompanyPortalEnterpriseSigned.appx. Il utilise le mot de passe PFX 1234 et lit l'ID d'éditeur dans le fichier PFX. Il lit aussi l'ID d'entreprise dans le fichier cert.aetx.

    **Exemple 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    Cet exemple signe le fichier CompanyPortal.appx à l'emplacement C:\temp\ et produit le fichier CompanyPortalEnterpriseSigned.appx. Il utilise le mot de passe PFX 1234 et utilise l'ID d'éditeur spécifié.

    **Paramètres :**

    -   `-InputAppx` : chemin d'accès local au fichier CompanyPortal.appx (entre guillemets simples). Par exemple, 'C:\temp\CompanyPortal.appx'.

    -   `-OutputAppx` : chemin d'accès local et nom de fichier de l'application Portail d'entreprise signée (entre guillemets simples). Par exemple, 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` : chemin d'accès local et nom du fichier PFX exporté du certificat Symantec. Par exemple, 'C:\signing\cert.pfx'.

    -   `-PfxPassword` : mot de passe utilisé pour signer le fichier PFX (entre guillemets simples). Par exemple, '1234'.

    -   `-AetxPath` : chemin d'accès local au fichier .aetx utilisé pour lire l'ID d'entreprise si l'argument 'EnterpriseId' n'est pas défini. Vous devez spécifier cet argument ou EnterpriseId. Par exemple, 'C:\signing\cert.aetx'.

    -   `-PublisherId` : ID d’éditeur de l’entreprise. S'il n'est pas fourni, le champ 'Subject' du certificat de signature de code Symantec Enterprise Mobile est utilisé. Par exemple, 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1'.

    -   `-SdkPath` : chemin du dossier racine du Kit SDK Windows pour Windows 8.1. Cet argument est facultatif et sa valeur par défaut est ${env:ProgramFiles(x86)}\Windows Kits\8.1.

    -   `-EnterpriseId` : ID d’entreprise. Vous devez spécifier cet argument ou 'AetxPath'. Si cet argument n'est pas fourni, l'ID d'entreprise est lu dans le fichier AETX. Par exemple, 1000000001.

6.  Déployez l'application Portail d'entreprise Windows Phone 8.1 (SSP.appx). Pour obtenir des instructions, consultez [Déployer des applications dans Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Comment renouveler le certificat de signature du code d'entreprise Symantec

Le certificat Symantec utilisé pour déployer des applications mobiles Windows et Windows Phone doit être renouvelé régulièrement.

1.  Recherchez un e-mail de renouvellement envoyé par Symantec 14 jours environ avant l'expiration du certificat. Ce courrier électronique contient les instructions de Symantec sur le renouvellement du certificat de votre entreprise.

    Pour plus d'informations sur les certificats Symantec, visitez [www.symantec.com](http://www.symantec.com) ou appelez le 1-877-438-8776 ou le 1-650-426-3400.

2.  Accédez au site web (par exemple, [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) et connectez-vous à l'aide de l'identifiant d'éditeur Symantec et de l'adresse e-mail associée au certificat. Pensez à utiliser le même ordinateur pour démarrer le renouvellement que vous allez utiliser pour télécharger le certificat.

3.  Une fois le renouvellement approuvé et payé, téléchargez-le.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Comment installer le certificat mis à jour pour les applications métier

1.  Signez la dernière version de votre application métier.

2.  Ouvrez la [console d’administration Intune](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com) et accédez à **Admin** &gt; **Gestion des appareils mobiles** &gt; **Windows Phone**, puis cliquez sur **Télécharger l’application signée**.

3.  Téléchargez le portail d'entreprise nouvellement signé. Vous avez besoin du fichier SSP.xap qui vient d'être signé et du nouveau fichier .PFX que vous avez reçu de Symantec, ou du jeton d'inscription d'application qui a été créé avec ce nouveau fichier .PFX.

4.  Une fois le chargement terminé, supprimez l'ancienne version de l'application Portail d'entreprise dans l'espace de travail **Logiciel**  .

5.  Signez toutes les applications métier nouvelles et mises à jour de l'entreprise à l'aide du nouveau certificat. Les applications existantes ne doivent être ni resignées ni redéployées.



<!--HONumber=Dec16_HO2-->


