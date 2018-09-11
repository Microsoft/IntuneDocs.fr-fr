---
title: Charger la version test des applications Windows et Windows Phone pour Intune
description: Découvrez comment signer des applications métier afin de pouvoir utiliser Intune pour les déployer.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
ms.custom: intune-classic
ms.openlocfilehash: 1c0c197536cb6d6b452ff5e3607ad1af2d5a4ca8
ms.sourcegitcommit: d047a692c798e1fb61ee43a487d6332bce344610
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44058895"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signer des applications métier afin de pouvoir les déployer sur des appareils Windows avec Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

En tant qu’administrateur Intune, vous pouvez déployer des applications métier sur des appareils Windows et Windows 10 Mobile, y compris l’application Portail d’entreprise. Pour déployer des applications .appx ou .xap sur des appareils Windows 10 et Windows 10 Mobile, ou déployer n’importe quelle application métier sur des appareils Windows 8.1 ou Windows Phone 8.1, vous devez obtenir un **certificat de signature de Code Symantec Enterprise Mobile**. Seul le certificat Symantec est approuvé pour ces applications pour les appareils Windows respectifs. Vous pouvez utiliser votre propre autorité de certification pour les applications Windows 10 et « universelles ». Ce certificat est requis pour :

-   Signer l’application Portail d’entreprise pour le déploiement sur des PC Windows, et sur des appareils Windows 10 Mobile et Windows Phone

-   Signer des applications métier pour que Intune puisse les déployer sur des appareils Windows

Les étapes ci-dessous vous aideront à obtenir les certificats requis et à signer les applications. Vous devrez vous inscrire en tant que développeur Microsoft, puis acheter un certificat Symantec.


1. **S'inscrire comme développeur Microsoft**<br>
   [Inscrivez-vous comme développeur Microsoft](http://go.microsoft.com/fwlink/?LinkId=268442) en utilisant les informations de compte d’entreprise que vous avez utilisées quand vous vous êtes connecté pour acheter votre compte d’entreprise. Cette demande devra être autorisée par un responsable de l'entreprise avant que vous ne receviez un certificat de signature de code.

2. **Obtenir un certificat Symantec d'entreprise**<br>
  Achetez un certificat sur le [site web de Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) à l'aide de votre identifiant Symantec. Après avoir acheté le certificat, l'approbateur d'entreprise que vous avez désigné lors de votre inscription en tant que développeur Microsoft recevra un e-mail lui demandant d'approuver la demande de certificat. Pour plus d’informations sur la nécessité d’obtenir un certificat Symantec, consultez la rubrique [Pourquoi Windows Phone requiert-il un certificat Symantec ?](https://technet.microsoft.com/library/dn764959.aspx#BKMK_Symantec) Forum Aux Questions sur l'inscription des appareils Windows.

3.  **Importer les certificats**<br>
    Une fois la demande approuvée, vous recevrez un e-mail contenant des instructions pour importer les certificats. Suivez les instructions de l'e-mail pour importer les certificats.

4.  **Vérifier les certificats importés**<br>
    Pour vérifier que les certificats ont été importés correctement, accédez au composant logiciel enfichable **Certificats** , cliquez avec le bouton droit sur **Certificats**, puis sélectionnez **Find Certificats**. Dans le champ **Contient** , indiquez « Symantec » et cliquez sur **Rechercher**. Les certificats que vous avez importés doivent apparaître dans les résultats.

    ![Rechercher le certificat Symantec](./media/wit.gif)

5. **Exporter un certificat de signature**<br>
    Après avoir vérifié que les certificats sont présents, vous pouvez exporter le fichier .pfx pour vous connecter au portail d'entreprise. Sélectionnez le certificat Symantec dont le **Rôle prévu** est « Signature du code ». Cliquez avec le bouton droit sur le certificat de signature de code et sélectionnez **Exporter**.

    ![Exporter le certificat de signature](./media/wit-walk-cert2.gif)

    Dans l' **Assistant Exportation de certificat**, sélectionnez **Oui, exporter la clé privée**, puis cliquez sur **Suivant**. Sélectionnez**Échange d’informations personnelles - PKCS #12 (.PFX)** et activez **Inclure tous les certificats dans le chemin d'accès de certification si possible**. Effectuez toutes les étapes de l'Assistant. Pour plus d'informations, voir [Comment exporter un certificat avec la clé privée](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Charger l’application sur Intune**<br>
    Chargez le fichier d’application signé et votre certificat de signature de code pour rendre l’application disponible pour vos utilisateurs finaux.

    1.  Dans le portail Azure, cliquez sur **Administration** &gt; **Windows Phone**.

    2.  Cliquez sur **Télécharger le fichier d’application signé** et connectez-vous avec votre ID d’administrateur Intune.

    3.  Ajoutez le fichier du certificat (.pfx) que vous avez exporté à **Certificat de signature de code** et créez un mot de passe pour le certificat.

    4.  Effectuez toutes les étapes de l'Assistant.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Exemple : Télécharger, signer et déployer l’application Portail d’entreprise pour les appareils Windows

Vous pouvez déployer l’application Portail d’entreprise sur les appareils Windows, y compris les appareils Windows Phone et Windows 10 Mobile avec Intune, au lieu de l’installer à partir du Microsoft Store. Vous devez télécharger l’application Portail d’entreprise et la signer avec votre certificat.  Cela n'est nécessaire que si vos utilisateurs ne sont pas appelés à utiliser le Store d'entreprise et si vous souhaitez déployer le Portail d'entreprise sur des appareils Windows Phone 8.1.


1.  **Télécharger le Portail d'entreprise**

    Pour déployer l’application Portail d’entreprise avec Intune, vous pouvez télécharger [l’application Portail d’entreprise Microsoft Intune pour Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) à partir du Centre de téléchargement et exécuter le fichier à extraction automatique (.exe). Ce fichier contient deux fichiers :

    -   CompanyPortal.appx : application d'installation du Portail d'entreprise pour Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1 : script PowerShell que vous pouvez utiliser pour signer le fichier de l'application Portail d'entreprise à des fins de déploiement vers des appareils Windows Phone 8.1

    Vous pouvez également télécharger le portail d’entreprise Windows Phone 8.1 (package sous licence hors connexion) ou le portail d’entreprise Windows 10 (package sous licence hors connexion) à partir du [Microsoft Store pour Entreprises](http://businessstore.microsoft.com/). L’application Portail d’entreprise doit être acquise avec une licence en mode hors connexion et le package approprié téléchargé pour une utilisation hors connexion. Les listes de plateformes Windows 8 et Windows Phone 8 dans la sélection font référence à leurs équivalents de la version 8.1. Pour plus d’informations sur la procédure à suivre avec Intune, consultez [Gérer les applications que vous avez achetées dans le Microsoft Store pour Entreprises](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune).

2.  **Télécharger le SDK Windows Phone** Téléchargez le SDK Windows Phone 8.0](http://go.microsoft.com/fwlink/?LinkId=615570) et installez-le sur votre ordinateur. Ce SDK est nécessaire pour générer un jeton d'inscription d'application.

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

6.  Déployez l'application Portail d'entreprise Windows Phone 8.1 (SSP.appx). Pour plus d’instructions, consultez [Guide pratique pour ajouter des applications métier Windows Phone](lob-apps-windows-phone.md) ([portail classique](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Comment renouveler le certificat de signature du code d'entreprise Symantec

Le certificat Symantec utilisé pour déployer des applications mobiles Windows et Windows Phone doit être renouvelé régulièrement.

1.  Recherchez un e-mail de renouvellement envoyé par Symantec 14 jours environ avant l'expiration du certificat. Ce courrier électronique contient les instructions de Symantec sur le renouvellement du certificat de votre entreprise.

    Pour plus d'informations sur les certificats Symantec, visitez [www.symantec.com](http://www.symantec.com) ou appelez le 1-877-438-8776 ou le 1-650-426-3400.

2.  Accédez au site web (exemple : [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) et connectez-vous à l’aide de l’ID d’éditeur Symantec et de l’adresse e-mail associée au certificat. Pensez à utiliser le même ordinateur pour démarrer le renouvellement que vous allez utiliser pour télécharger le certificat.

3.  Une fois le renouvellement approuvé et payé, téléchargez-le.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Comment installer le certificat mis à jour pour les applications métier

1.  Signez la dernière version de votre application métier.

2.  Ouvrez le portail Azure et accédez à **Admin** &gt; **Gestion des appareils mobiles** &gt; **Windows Phone**, puis cliquez sur **Télécharger l’application signée**.

3.  Téléchargez le portail d'entreprise nouvellement signé. Vous avez besoin du fichier SSP.xap qui vient d'être signé et du nouveau fichier .PFX que vous avez reçu de Symantec, ou du jeton d'inscription d'application qui a été créé avec ce nouveau fichier .PFX.

4.  Une fois le chargement terminé, supprimez l'ancienne version de l'application Portail d'entreprise dans l'espace de travail **Logiciel**  .

5.  Signez toutes les applications métier nouvelles et mises à jour de l'entreprise à l'aide du nouveau certificat. Les applications existantes ne doivent être ni resignées ni redéployées.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Déployer manuellement l’application Portail d’entreprise Windows 10
Vous pouvez déployer manuellement l’application Portail d’entreprise Windows 10 directement à partir d’Intune, même si vous n’avez pas encore intégré Intune avec le Microsoft Store pour Entreprises.

 > [!NOTE]
 > Cette option nécessite le déploiement manuel de mises à jour chaque fois qu’une mise à jour d’application est publiée.

1. Connectez-vous à votre compte dans le [Microsoft Store pour Entreprises](https://www.microsoft.com/business-store) et acquérez la version avec **licence hors connexion** de l’application Portail d’entreprise.  
2. Une fois que l’application a été acquise, sélectionnez l’application dans la page **Inventorier**.  
3. Sélectionnez **Tous les appareils Windows 10** comme **plateforme**, puis l’**architecture** appropriée et procédez au téléchargement. Un fichier de licence d’application n’est pas nécessaire pour cette application.
![Image de tous les appareils Windows 10 et des détails du package d’architecture X86 à télécharger](./media/Win10CP-all-devices.png)
4. Téléchargez tous les packages sous « Infrastructures requises ». Vous devez effectuer cette opération pour les architectures x86, x64 et ARM, soit un total de 9 packages, comme indiqué ci-dessous.

![Image des fichiers de dépendance à télécharger ](./media/Win10CP-dependent-files.png)
5. Avant de charger l’application Portail d’entreprise dans Intune, créez un dossier (par exemple, C:/Portail Entreprise) avec les packages structurés de la manière suivante :
   1. Placez le package Portail d’entreprise dans C:\Portail Entreprise. Créez un sous-dossier Dépendances dans cet emplacement également.  
   ![Image du dossier Dépendances enregistré avec le fichier APPXBUN](./media/Win10CP-Dependencies-save.png)
   2. Placez les neuf packages de dépendances dans le dossier Dépendances.  
   Si les dépendances ne sont pas placées dans ce format, Intune ne peut pas les reconnaître ni les charger et le chargement du package échoue avec l’erreur suivante.  
   ![La dépendance d’application Windows pour ce programme d’installation logicielle est introuvable dans le dossier de l’application. Vous pouvez poursuivre la création et le déploiement de l’application, mais cette dernière ne pourra pas fonctionner tant que la dépendance d’application Windows manquante ne sera pas spécifiée.](./media/Win10CP-error-message.png)
6. Revenez à Intune, puis chargez l’application Portail d’entreprise en tant que nouvelle application. Déployez-la en tant qu’application requise pour l’ensemble souhaité d’utilisateurs cibles.  

Pour plus d’informations sur la façon dont Intune gère les dépendances pour les applications universelles, consultez [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Déploiement d’un appxbundle avec dépendances via Microsoft Intune MDM).  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Comment modifier le portail d’entreprise sur les appareils de mes utilisateurs si ceux-ci ont déjà installé les applications plus anciennes à partir du Windows Store ?
Si vos utilisateurs ont déjà installé les applications Portail d’entreprise Windows 8.1 ou Windows Phone 8.1 à partir du Windows Store, ils doivent être automatiquement mis à jour vers la nouvelle version sans que l’utilisateur ou vous-même n’ayez à intervenir. Si la mise à jour ne se produit pas, demandez à vos utilisateurs de vérifier s’ils ont activé les mises à jour automatiques pour les applications du Windows Store sur leurs appareils.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Comment mettre à niveau mon application de portail d’entreprise Windows 8.1 chargée indépendamment vers l’application Portail d’entreprise Windows 10 ?
Nous vous recommandons de supprimer le déploiement de l’application Portail d’entreprise Windows 8.1 en définissant l’action de déploiement sur « Désinstaller ». Une fois cette opération effectuée, l’application Portail d’entreprise Windows 10 peut être déployée à l’aide d’une des options ci-dessus.  

Si vous avez besoin de charger indépendamment l’application et de déployer le portail d’entreprise Windows 8.1 sans le signer avec le certificat Symantec, suivez les étapes de la section Déployer directement via Intune ci-dessus pour terminer la mise à niveau.

Si vous souhaitez charger indépendamment l’application et que vous avez signé et déployé le portail d’entreprise Windows 8.1 avec le certificat de signature de code Symantec, suivez les étapes décrites dans la section ci-dessous.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Comment mettre à niveau mon application Portail d’entreprise Windows 8.1 ou Windows Phone 8.1 chargée indépendamment et signée vers l’application Portail d’entreprise Windows 10 ?
Nous vous recommandons de supprimer le déploiement existant de l’application Portail d’entreprise Windows Phone 8.1 ou Windows 8.1 en définissant l’action de déploiement sur « Désinstaller ». Une fois cette opération effectuée, l’application Portail d’entreprise Windows 10 peut être déployée normalement.  

Sinon, l’application Portail d’entreprise Windows 10 doit être mise à jour et signée de façon adéquate afin de respecter la procédure de mise à niveau.  

Si l’application Portail d’entreprise Windows 10 est signée et déployée de cette façon, vous devez répéter ce processus pour chaque nouvelle mise à jour de l’application lorsqu’elle est disponible dans le Windows Store. L’application ne se met pas automatiquement à jour lorsque le Windows Store est mis à jour.  

Voici comment signer et déployer l’application de cette façon :

1. Téléchargez le script de signature de l’application Portail d’entreprise Windows 10 Microsoft Intune à partir de la page [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Ce script nécessite que le SDK Windows pour Windows 10 soit installé sur l’ordinateur hôte. Pour télécharger le SDK Windows pour Windows 10, accédez à [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Téléchargez l’application Portail d’entreprise Windows 10 à partir du Microsoft Store pour Entreprises, comme indiqué ci-dessus.  
3. Exécutez le script avec les paramètres d’entrée détaillés dans l’en-tête de script pour signer l’application Portail d’entreprise Windows 10 (extraite ci-dessous). Les dépendances n’ont pas besoin d’être transmises au script. Elles sont uniquement requises lorsque l’application est en cours de téléchargement vers la console d’administration Intune.

|       Paramètre       |                                                                    Description                                                                    |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| InputWin10AppxBundle  |                                             Chemin d’accès au fichier appxbundle source.                                              |
| OutputWin10AppxBundle |                                                  Chemin de sortie du fichier appxbundle signé.                                                  |
|       Win81Appx       |                          Chemin d’accès au fichier Portail d’entreprise Windows 8.1 ou Windows Phone 8.1 (.APPX).                           |
|      PfxFilePath      |                                   Chemin d’accès au fichier (.PFX) de signature de code Symantec Enterprise Mobile.                                    |
|      PfxPassword      |                                     Mot de passe du fichier de signature de code Symantec Enterprise Mobile.                                      |
|      PublisherId      |      ID d’éditeur de l’entreprise. S'il n'est pas fourni, le champ 'Subject' du certificat de signature de code Symantec Enterprise Mobile est utilisé.       |
|        SdkPath        | Chemin du dossier racine du SDK Windows pour Windows 10. Cet argument est facultatif et sa valeur par défaut est ${env:ProgramFiles(x86)}\Windows Kits\10. |

Le script transmet la version de l’application Portail d’entreprise Windows 10 signée lorsque son exécution est terminée. Vous pouvez ensuite déployer la version signée de l’application en tant qu’application métier par le biais de Intune, ce qui met à niveau les versions actuellement déployées vers cette nouvelle application.  
