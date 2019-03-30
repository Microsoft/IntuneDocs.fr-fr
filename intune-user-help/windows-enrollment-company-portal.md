---
title: L’inscription des appareils Windows dans le portail d’entreprise Intune | Microsoft Docs
description: Prise en main de l’inscription d’un appareil Windows dans le portail d’entreprise
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/12/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: a637b6eed162243d2be81ac08fbcc055e1fd5816
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58068988"
---
# <a name="windows-device-enrollment-in-intune-company-portal"></a>Inscription des appareils Windows dans le portail d’entreprise Intune  

Inscrire votre appareil Windows dans l’application portail d’entreprise Intune pour obtenir un accès sécurisé pour le travail et applications de l’école, e-mails et fichiers. Si votre organisation nécessite ou recommande certaines applications, par exemple Office ou OneDrive, vous allez les recevoir soit lors de l’inscription, ou elles seront disponibles dans le portail d’entreprise après l’inscription.  

Vous pouvez inscrire des appareils Windows 10 via le site Web portail d’entreprise *ou* application. Si vous inscrivez un appareil avec une version antérieure de Windows, vous devez inscrire l’appareil via le site Web portail d’entreprise.  

## <a name="install-company-portal-app"></a>Application portail d’entreprise de l’installation  
Vous disposez peut-être déjà l’application portail d’entreprise est installée sur votre appareil. Recherchez l’application dans votre __toutes les applications__ liste.  Si l'application Portail d'entreprise ne figure pas dans votre liste d'applications, procédez comme suit pour l'installer.  

1. Ouvrez **Microsoft Store** sur votre appareil.

2. Dans le **recherche** , tapez **portail d’entreprise**.

3. Dans la liste des résultats, sélectionnez **Portail d’entreprise** > **Installer**.

4. Sélectionnez **Installer** ou **Gratuit**. Il n’existe aucune différence entre ces deux options ; les mots s’affichent en fonction de la façon dont votre organisation a configuré l’application.  

## <a name="find-windows-10-version-number"></a>Rechercher le numéro de version de Windows 10  
Étapes d’inscription diffèrent pour les différentes versions des appareils Windows 10. Les étapes suivantes décrivent comment trouver le numéro de version sur Windows 10 desktop et les appareils mobiles. Une fois que vous connaissez votre version, passez aux étapes d’inscription recommandées.  

### <a name="windows-10-desktop-devices"></a>Appareils Windows 10 Desktop  

1. Accédez à **Démarrer**.

2. Dans la barre de recherche, tapez la phrase « sur votre PC. » Sélectionnez __sur votre PC__ à partir des résultats.  


   ![paramètres de recherche « à propos de votre PC »](media/searching_for_about_your_pc.png)  

3. Faites défiler jusqu'à **spécifications de Windows** pour trouver la **Version** de Windows 10 qui est installée sur votre PC.  


   ![À propos de votre PC dans Windows 10 Desktop](media/settings_about_pc.png)  

4. Si votre version est  

    *  __1607 ou ultérieure__: inscrire votre appareil par le biais de la [ **paramètres** > **compte** > **accès Professionnel ou scolaire**itinéraire](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 ou une version antérieure__: inscrire votre appareil par le biais de la [ **paramètres** > **compte** > **vos comptes** itinéraire](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

### <a name="windows-10-mobile-devices"></a>Appareils Windows 10 Mobile       

1.  Accédez à __toutes les applications__ et sélectionnez le __paramètres__ application.  
2.  Sélectionnez __Système__ > __À propos de__.      
3.  Sous __informations sur les appareils__, recherchez le __Version__.  
4. Si votre version est  

    *  __1607 ou ultérieure__: inscrire votre appareil à l’aide de la [ **paramètres** > **accès scolaire ou Professionnel** itinéraire](enroll-windows-10-device.md#enroll-windows-10-version-1607-and-later-device).   
    * __1511 ou une version antérieure__: inscrire votre appareil à l’aide de la [ **paramètres** > **comptes** itinéraire](enroll-windows-10-device.md#enroll-windows-10-version-1511-and-earlier-device).  

## <a name="enroll-non-windows-10-devices"></a>Inscrire des appareils non Windows 10  
Pour inscrire d’autres appareils pris en charge de Windows via le site Web portail d’entreprise, utilisez les articles suivants :   
* [Appareil Windows 8.1 ou Windows RT 8.1](enroll-your-W81-or-rt81-windows.md)  
* [Appareil Windows Phone 8.1](enroll-your-wp81-windows.md)    

## <a name="next-steps"></a>Étapes suivantes  
Maintenant que vous connaissez les appareils pris en charge et votre numéro de version de Windows 10, passez à l’article d’inscription recommandées.  
 
Pour plus d’informations sur la gestion des appareils, le portail d’entreprise, et comment les deux sont utilisés dans les écoles et au travail, consultez les articles suivants :  
* [Utiliser des appareils gérés pour accéder aux ressources professionnelles ou scolaires](use-managed-devices-to-get-work-done.md)  
* [Qu’est-ce qui se produit lorsque vous inscrivez votre appareil dans Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md)  
* [Quelles informations mon organisation peut-elle voir quand j’inscris mon appareil ?](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)  

Vous avez besoin d'aide ? Contactez le support technique de votre entreprise. [Accédez au site Web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour rechercher votre organisation informatique informations de contact.  
