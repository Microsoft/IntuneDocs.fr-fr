---
title: Charger la version test des applications Windows et Windows Phone
titleSuffix: Microsoft Intune
description: Découvrez comment signer des applications métier afin de pouvoir utiliser Intune pour les déployer.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 09/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a89392dabe695cf49e989351cef822852676916
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507382"
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Signer des applications métier afin de pouvoir les déployer sur des appareils Windows avec Intune

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

En tant qu’administrateur Intune, vous pouvez déployer des applications métier sur des appareils Windows 8.1 Desktop ou Windows 10 Desktop et sur des appareils mobiles, notamment l’application Portail d’entreprise. Pour déployer des applications .appx sur Windows 8.1 Desktop ou Windows 10 Desktop et sur des appareils mobiles, vous pouvez utiliser un certificat de signature de code d’une autorité de certification publique déjà approuvée par votre propre autorité de certificat.

 > [!NOTE]
 > Windows 8.1 Desktop requiert une stratégie d’entreprise pour activer le chargement indépendant ou l’utilisation de clés de chargement indépendant (activé automatiquement pour les appareils joints à un domaine). Pour plus d’informations, consultez [Chargement indépendant sur Windows 8](https://blogs.technet.microsoft.com/scd-odtsp/2012/09/27/windows-8-sideloading-requirements-from-technet/).

## <a name="windows-10-sideloading"></a>Chargement indépendant de Windows 10

Dans Windows 10, le chargement indépendant est différent de celui des versions antérieures de Windows :

- Vous pouvez déverrouiller un appareil pour le chargement indépendant à l’aide d’une stratégie d’entreprise. Intune fournit une stratégie de configuration d’appareil appelée « installation d’applications approuvées ». L’attribution de <allow> la valeur est tout ce qui est nécessaire pour les appareils qui font déjà confiance au certificat utilisé pour signer l’application Appx.

- Les certificats de téléphone Symantec et les clés de chargement indépendant ne sont pas requis. Toutefois, si une autorité de certificat local n’est pas disponible, vous aurez peut-être besoin d’un certificat de signature de code d’une autorité de certification publique. Pour plus d’informations, consultez [Présentation de la signature de code](https://docs.microsoft.com/windows/desktop/SecCrypto/cryptography-tools#introduction-to-code-signing).

### <a name="code-sign-your-app"></a>Signer le code de votre application

La première étape consiste à signer votre package appx. Pour plus de détails, voir [Signer un package d’application à l’aide de SignTool](https://docs.microsoft.com/windows/uwp/packaging/sign-app-package-using-signtool).

### <a name="upload-your-app"></a>Charger votre application

Vous devez ensuite charger le fichier appx signé. Pour plus de détails, voir [Ajouter une application métier Windows à Microsoft Intune](lob-apps-windows.md).

Si vous déployez l’application en fonction des besoins des utilisateurs ou des appareils, vous n’avez pas besoin de l’application Portail d’entreprise Intune. Toutefois, si vous déployez l’application comme disponible pour les utilisateurs, ils peuvent utiliser l’application Portail d’entreprise à partir du Microsoft Store public, utiliser l’application Portail d’entreprise à partir du Microsoft Store privé pour entreprises. Sinon, vous devrez signer et déployer manuellement l’application Intune Portail d'entreprise.

### <a name="upload-the-code-signing-certificate"></a>Charger le certificat de signature de code

Si votre appareil Windows 10 n’approuve pas encore l’autorité de certification, après avoir signé votre package appx et l’avoir téléchargé vers le service Intune, vous devez télécharger le certificat de signature de code dans le portail Intune :
1. Cliquez sur Applications clientes
2. Cliquez sur Certificats d’entreprise Windows
3. Sélectionnez « Sélectionner un fichier » dans le certificat de signature de code
4. Sélectionnez votre fichier .cer, puis cliquez sur Télécharger

À présent, tous les appareils Windows 10 Desktop & mobiles avec un déploiement appx par le service Intune téléchargent automatiquement le certificat d’entreprise correspondant, et le lancement de l’application après son installation est autorisé.

Intune déploie uniquement le dernier fichier .cer chargé. Si vous avez plusieurs fichiers appx créés par différents développeurs qui ne sont pas associés à votre organisation, vous devez soit leur demander de fournir des fichiers appx non signés pour la signature avec votre certificat, soit leur fournir le certificat de signature de code utilisé par votre organisation.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Comment renouveler le certificat de signature du code d'entreprise Symantec

Le certificat utilisé pour déployer les applications mobiles Windows Phone 8.1 a été abandonné le 28 février 2019 et n’est plus disponible pour le renouvellement par Symantec. Si vous déployez sur Windows 10 Mobile, vous pouvez continuer à utiliser les certificats de signature de code Symantec Desktop Enterprise en suivant les instructions de la section [Chargement indépendant de Windows 10](app-sideload-windows.md#windows-10-sideloading).

## <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Comment installer le certificat mis à jour pour les applications métier

Windows Phone 8.1

Le service Intune ne peut plus déployer d’applications métier pour cette plateforme une fois que le certificat de signature de code Symantec Mobile Enterprise existant expire. Il reste possible d’effectuer un chargement indépendant de fichiers XAP/APPX non signés avec une carte SD ou en téléchargeant le fichier sur l’appareil. Pour en savoir plus, consultez [Installation de fichiers XAP sur Windows Phone](https://answers.microsoft.com/en-us/mobiledevices/forum/mdlumia-mdapps/how-to-install-xap-file-in-windows-phone-8/da09ee72-51ae-407c-9b85-bc148df89280).

Windows 8.1 Desktop/Windows 10 Desktop & Mobile

Si la période du certificat a expiré, les fichiers appx peuvent stopper son lancement. Vous devez obtenir un nouveau fichier .cer et suivre les instructions permettant de signer le code de chaque fichier appx déployé et de charger à nouveau tous les fichiers appx et le fichier .cer mis à jour dans la section de certificats d’entreprise Windows du portail Intune.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Déployer manuellement l’application Portail d’entreprise Windows 10
Si vous ne voulez pas donner accès au Microsoft Store, vous pouvez déployer manuellement l’application Portail d’entreprise Windows 10 directement à partir d’Intune, même si vous n’avez pas encore intégré Intune avec le Microsoft Store pour Entreprises (MSFB). Une alternative possible si vous avez intégré consiste à déployer l’application Portail d’entreprise à l’aide de [déployer des applications avec MSFB](store-apps-windows.md).

 > [!NOTE]
 > Cette option nécessite le déploiement manuel de mises à jour chaque fois qu’une mise à jour d’application est publiée.

1. Connectez-vous à votre compte dans le [Microsoft Store pour Entreprises](https://www.microsoft.com/business-store) et acquérez la version avec **licence hors connexion** de l’application Portail d’entreprise.  
2. Une fois que l’application a été acquise, sélectionnez l’application dans la page **Inventorier**.  
3. Sélectionnez **Tous les appareils Windows 10** comme **plateforme**, puis l’**architecture** appropriée et procédez au téléchargement. Un fichier de licence d’application n’est pas nécessaire pour cette application.
   ![Image des détails du package de Windows 10 X86 pour le téléchargement](./media/app-sideload-windows/Win10CP-all-devices.png)
4. Téléchargez tous les packages sous « Infrastructures requises ». Vous devez effectuer cette opération pour les architectures x86, x64 et ARM, soit un total de 9 packages, comme indiqué ci-dessous.

   ![Image des fichiers de dépendance à télécharger ](./media/app-sideload-windows/Win10CP-dependent-files.png)
5. Avant de charger l’application Portail d’entreprise dans Intune, créez un dossier (par exemple, C:/Portail Entreprise) avec les packages structurés de la manière suivante :
   1. Placez le package Portail d’entreprise dans C:\Portail Entreprise. Créez un sous-dossier Dépendances dans cet emplacement également.  
      ![Image du dossier Dépendances enregistré avec le fichier APPXBUN](./media/app-sideload-windows/Win10CP-Dependencies-save.png)
   2. Placez les neuf packages de dépendances dans le dossier Dépendances.  
      Si les dépendances ne sont pas placées dans ce format, Intune ne peut pas les reconnaître ni les charger et le chargement du package échoue avec l’erreur suivante.  
      ![Message d’erreur - la dépendance d’application Windows doit être fournie.](./media/app-sideload-windows/Win10CP-error-message.png)
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
