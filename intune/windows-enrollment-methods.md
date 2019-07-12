---
title: Méthodes d’inscription dans Intune pour les appareils Windows
titleSuffix: Microsoft Intune
description: Découvrez les différentes manières d’inscrire des appareils Windows dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: cbe533e6a219adf1984c656506ceb7a3b95556ec
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67548665"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>Méthodes d’inscription dans Intune pour les appareils Windows

Pour gérer des appareils dans Intune, vous devez d’abord les inscrire auprès du service Intune. Vous pouvez inscrire des appareils d’entreprise et des appareils personnels pour la gestion Intune. 

Il existe deux façons d’inscrire des appareils dans Intune :
- Les utilisateurs peuvent inscrire eux-mêmes leurs PC Windows 
- Les administrateurs peuvent configurer des stratégies pour forcer l’inscription automatique sans l’intervention de l’utilisateur

## <a name="user-self-enrollment-in-intune"></a>Inscription par l’utilisateur dans Intune

Les utilisateurs peuvent inscrire eux-mêmes leur appareil Windows en appliquant l’une des méthodes suivantes :

- [Apportez votre propre appareil (BYOD)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device) : les utilisateurs inscrivent leurs appareils personnels en choisissant de connecter un compte **Professionnel et scolaire** à partir des **Paramètres** de l’appareil. Ce processus :
    - Inscrit l’appareil auprès d’Azure Active Directory pour accéder aux ressources d’entreprise telles que les e-mails.
    - Inscrit l’appareil dans Intune en tant qu’appareil personnel (BYOD).
Si un administrateur a configuré l’inscription automatique (disponible avec les abonnements Azure AD premium), l’utilisateur n’est obligé d’entrer ses informations d’identification qu’une seule fois. Sinon, il devra s’inscrire séparément par le biais de l’inscription à MDM uniquement, et entrer à nouveau ses informations d’identification.  
- L’**inscription à MDM uniquement** permet aux utilisateurs d’inscrire un PC existant joint à un annuaire Active Directory, à Azure Active Directory ou à un groupe de travail dans Intune. Les utilisateurs s’inscrivent à partir de Paramètres sur le PC Windows existant. Cette méthode n’est pas recommandée, car elle n’inscrit pas l’appareil auprès d’Azure Active Directory. Elle empêche également l’utilisation de fonctionnalités telles que l’accès conditionnel.
- [Jointure Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) : joint l’appareil à Azure Active Directory et permet aux utilisateurs de se connecter à Windows avec leurs informations d’identification Azure AD. Si l’inscription automatique est activée, l’appareil est inscrit automatiquement dans Intune. L’avantage de l’inscription automatique est qu’il s’agit d’un processus à étape unique pour l’utilisateur. Autrement, il devra s’inscrire séparément par le biais de l’inscription à MDM uniquement, et entrer à nouveau ses informations d’identification. Les utilisateurs s’inscrivent de cette façon pendant la phase OOBE Windows initiale ou à partir de Paramètres. L’appareil est marqué comme appareil d’entreprise dans Intune.
- [AutoPilot](enrollment-autopilot.md) : automatise la jonction à Azure AD et inscrit de nouveaux appareils d’entreprise dans Intune. Cette méthode simplifie l’expérience OOBE et élimine la nécessité d’appliquer des images de système d’exploitation personnalisées sur les appareils. Quand les administrateurs utilisent Intune pour gérer des appareils Autopilot, ils peuvent gérer des stratégies, des profils, des applications, et ainsi de suite, une fois les appareils inscrits.  Il existe quatre types de déploiement Autopilot : [Mode de déploiement automatique](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (pour les bornes, la signalisation numérique ou les appareils partagés), [Mode géré par l’utilisateur](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (pour les utilisateurs traditionnels), [White Glove] (https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permet aux partenaires ou au personnel informatique de préprovisionner un PC Windows 10 pour qu’il soit entièrement configuré et prêt à l’emploi, et [Autopilot pour les appareils existants] (https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) vous permet de déployer facilement la dernière version de Windows 10 sur vos appareils existants).

## <a name="administrator-based-enrollment-in-intune"></a>Inscription gérée par l’administrateur dans Intune

Les administrateurs peuvent configurer les méthodes d’inscription suivantes qui ne nécessitent aucune interaction utilisateur :

- La [jonction Azure AD Hybride](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) permet aux administrateurs de configurer la stratégie de groupe Active Directory pour inscrire automatiquement les appareils qui sont joints à Azure AD Hybride. 
- La [cogestion Configuration Manager](https://docs.microsoft.com/sccm/comanage/overview) permet aux administrateurs d’inscrire leurs appareils existants gérés par Configuration Manager dans Intune afin de bénéficier à la fois des avantages offerts par Intune et par Configuration Manager. 
- Le [Gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md) (DEM) est un compte de service spécial. Les comptes DEM disposent d’autorisations qui permettent aux utilisateurs autorisés d’inscrire et de gérer plusieurs appareils d’entreprise. Ces types d’appareils sont adaptés par exemple aux applications utilitaires ou de point de vente, mais ne conviennent pas pour les utilisateurs qui doivent accéder à la messagerie ou à des ressources de l’entreprise. Cette méthode n’autorise pas l’utilisation de fonctionnalités telles que l’accès conditionnel. 
- L’[inscription en bloc](windows-bulk-enroll.md) permet à un utilisateur autorisé de joindre un grand nombre de nouveaux appareils d’entreprise à Azure Active Directory et Intune. Vous créez un package de provisionnement avec l’application WCD (Windows Configuration Designer). Ensuite, à l’aide d’un support USB pendant l’expérience OOBE Windows initiale ou à partir d’un PC Windows existant, vous installez le package de provisionnement pour inscrire automatiquement les appareils dans Intune. Cette méthode n’autorise pas l’utilisation de l’accès conditionnel. 
- [L’inscription des appareils Windows IoT Core](https://docs.microsoft.com/windows/iot-core/manage-your-device/intunedeviceenrollment) s’effectue en utilisant le tableau de bord Windows IoT Core pour préparer l’appareil, puis en utilisant Windows Configuration Designer pour créer un package d’approvisionnement. Ensuite, à l’aide de la carte SD comme support lors du démarrage initial, il installe le package d’approvisionnement pour inscrire automatiquement les appareils dans Intune.

## <a name="next-steps"></a>Étapes suivantes

[Découvrez les fonctionnalités des méthodes d’inscription Windows](enrollment-method-capab.md)
