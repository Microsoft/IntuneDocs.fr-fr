---
title: Utiliser des appareils gérés pour réaliser vos tâches | Microsoft Docs
description: Découvrez ce que signifie d’inscrire votre appareil à la gestion avec Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883872"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Inscrire un appareil pour accéder à des ressources professionnelles ou scolaires
Pour inscrire votre appareil et accéder à la messagerie et aux applications, vous devez installer l’application Portail d’entreprise Intune ou Microsoft Intune. Lorsque vous vous inscrivez, les stratégies de gestion de base que votre organisation a configurées, telles que le mot de passe, le code confidentiel et le chiffrement, sont appliquées à votre appareil. Une fois que les paramètres de votre appareil répondent à toutes les exigences de votre organisation, vous pouvez accéder en toute sécurité à vos informations de travail depuis quasiment n’importe où.  

Les applications Portail d’entreprise et Microsoft Intune maintiennent votre appareil inscrit sécurisé en vous assurant que les paramètres de votre appareil correspondent aux stratégies de votre organisation. 

L'application Portail d’entreprise effectue également les tâches suivantes :  
* Permet de séparer vos informations personnelles et professionnelles.  
* Facilite la recherche et l’installation des applications professionnelles et scolaires pertinentes.   

## <a name="get-the-apps"></a>Récupération des applications
Pour obtenir Portail d’entreprise :

- Installez l’application Portail d’entreprise à partir de l’App Store spécifique à la plateforme. Dans certains cas, votre organisation installe l’application Portail d’entreprise pour vous.  
- Accédez au [site web portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour accéder à l’application à partir d’un navigateur.  

Si vous devez utiliser l’application Microsoft Intune, votre organisation l’installe pour vous.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Quelles informations mon entreprise peut-elle voir quand je m’inscris?
Une fois votre appareil inscrit, les utilisateurs du support technique de votre organisation peuvent voir uniquement les informations pertinentes pour travailler. Vos informations personnelles ne sont pas visibles. Si vous êtes en train d’inscrire un appareil personnel pour l’utiliser au travail, [Découvrez exactement ce qui peut et ne peut pas être vu](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Quelle est la différence entre les applications et le site web ?
L’application Portail d’entreprise est disponible pour les appareils Windows 10, iOS, macOS et Android. Il s’intègre parfaitement à la plateforme de votre appareil. La version sur le site web est accessible à partir de n’importe quel appareil et vous donne la même expérience universelle, quel que soit l’appareil que vous utilisez. 

L’application Microsoft Intune est destinée aux appareils Android appartenant à l’entreprise.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Quels types d’appareils pouvez-vous inscrire avec Portail d’entreprise?
- Appareils Apple utilisant iOS (par ex., iPhone et iPad) et Mac OS (par ex., MacBook et iMac)
- Appareils Android
- Appareils Windows
  - Windows 10 Mobile
  - Windows 10 Desktop
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Quels types d’appareils pouvez-vous inscrire avec l’application Microsoft Intune?  
Vous pouvez inscrire des appareils Android appartenant à l’entreprise que votre organisation a configurés pour utiliser l’application. L’application prend en charge Android 6,0 et versions ultérieures. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>Pouvez-vous supprimer un ordinateur ou un appareil du Portail d’entreprise ?
Vous pouvez supprimer ou réinitialiser un ordinateur ou un appareil à partir du Portail d’entreprise. Il existe une différence entre **supprimer** et **réinitialiser**.

Quand vous supprimez un ordinateur ou un appareil du portail d’entreprise, vous désinscrivez votre appareil dans Intune. Une fois l’appareil désinscrit, vous ne pouvez plus accéder au portail d’entreprise à partir de cet appareil et certaines données d’entreprise peuvent également être supprimées de l’appareil. Pour savoir comment supprimer votre appareil du Portail d’entreprise, consultez les liens suivants:  

- [Désinscription de votre appareil Android](unenroll-your-device-from-intune-android.md)
- [Désinscription de votre appareil iOS](unenroll-your-device-from-intune-ios.md)
- [Désinscription de votre appareil macOS](unenroll-your-device-from-intune-macos.md)
- [Désinscription de votre appareil Windows](unenroll-your-device-from-intune-windows.md)

Quand vous réinitialisez un ordinateur ou un appareil, le portail d’entreprise tente de rétablir les paramètres par défaut d’origine sur votre ordinateur ou votre appareil. La réinitialisation de votre appareil supprime toutes les données personnelles et d’entreprise figurant sur l’appareil. Si vous avez perdu votre appareil, vous pouvez le réinitialiser à distance à partir du site web Portail d’entreprise.  

Pour savoir comment réinitialiser votre appareil, consultez [Réinitialiser votre appareil à partir du site web portail d’entreprise](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>Pouvez-vous supprimer un ordinateur ou un appareil de l’application Microsoft Intune?
Non, vous n’avez aucun moyen de supprimer un appareil appartenant à l’entreprise de l’application Microsoft Intune.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>Que se passe-t-il si je ne vois pas mon appareil dans l’application Portail d’entreprise ou Microsoft Intune?
Pour que vous puissiez voir un appareil, il doit d’abord être ajouté au Portail d’entreprise. Accédez au portail d’entreprise recommandé par votre administrateur et suivez les étapes pour votre appareil. Vous ne verrez pas non plus les appareils détenus et gérés par votre entreprise.

Si vous utilisez l’application Microsoft Intune, vous voyez uniquement l’appareil que vous utilisez actuellement. Les autres appareils inscrits ne seront pas visibles dans l’application.  

## <a name="where-else-can-i-go-for-help"></a>Où puis-je encore trouver de l’aide ?  
Pour résoudre les problèmes courants et les questions, consultez les documents spécifiques à la plateforme suivante:  

- [Résoudre les problèmes courants rencontrés avec votre appareil Android](check-compliance-on-your-device-android.md)  
- [Résoudre les problèmes courants rencontrés avec votre appareil iOS](troubleshoot-your-device-ios.md)
- [Résoudre les problèmes courants rencontrés avec votre appareil macOS](troubleshoot-your-device-macos.md)
- [Résoudre les problèmes courants rencontrés avec votre appareil Windows](troubleshoot-your-device-windows.md)

Vous pouvez également contacter votre personne du support technique. L’application Portail d’entreprise et Microsoft Intune proposent des pages d’aide et de support qui répertorient les informations de contact et les moyens de signaler un problème. Les informations de contact sont également disponibles sur le [site web portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980)de votre organisation.  

## <a name="next-steps"></a>Étapes suivantes  

Obtenir de l’aide en commençant par l’inscription, qui est spécifique à la plateforme de votre appareil:  

- [Utilisation de votre appareil Android](using-your-android-device-with-intune.md)
- [Utilisation de votre appareil iOS](using-your-ios-device-with-intune.md)
- [Utilisation de votre appareil macOS](using-your-macos-device-with-intune.md)
- [Utilisation de votre appareil Windows](using-your-windows-device-with-intune.md)
- [Utilisation du site web du portail de l'entreprise](using-the-intune-company-portal-website.md)


