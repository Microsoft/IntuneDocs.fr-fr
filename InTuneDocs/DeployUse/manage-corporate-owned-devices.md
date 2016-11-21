---
title: "Gérer les appareils d’entreprise | Microsoft Intune"
description: "Inscrivez les appareils d’entreprise de différentes façons, selon le type d’appareil, la méthode utilisée pour son achat et les besoins de l’organisation."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 7577cbab528d88635e8551bf8de1ffd49becaa84


---

# <a name="enroll-corporateowned-devices-by-using-intune"></a>Inscrire des appareils d’entreprise à l’aide d’Intune

Vous pouvez inscrire des appareils d’entreprise ou d’organisation en vue de les gérer avec Intune de diverses façons en fonction du type d’appareil, de la méthode utilisée pour son achat et des besoins de l’organisation. Vous pouvez également installer l’application Portail d’entreprise pour inscrire et gérer les appareils d’entreprise, comme dans un scénario BYOD (« Apportez votre propre appareil »).

## <a name="enroll-corporateowned-ios-devices"></a>Inscrire des appareils iOS d'entreprise

Les méthodes d’inscription d’appareil d’entreprise constituent un bon choix dans le cadre des scénarios CYOD (« Choisissez votre propre appareil »). Dans un environnement CYOD, l’organisation paie pour un appareil que l’utilisateur sélectionne et elle gère l’appareil.

Si vous proposez aux utilisateurs de choisir parmi des appareils iOS, vous pouvez préconfigurer l’inscription afin que l’appareil soit géré avec Intune dès que l’utilisateur l’allume pour la première fois. Intune prend en charge l’inscription à l’aide du service [Apple DEP (Device Enrollment Program)](ios-device-enrollment-program-in-microsoft-intune.md) ou de l’outil Apple Configurator sur un ordinateur Mac pour l’inscription [directe](ios-direct-enrollment-in-microsoft-intune.md) ou avec l’[Assistant de configuration](ios-setup-assistant-enrollment-in-microsoft-intune.md).

Découvrez comment [inscrire des appareils iOS d’entreprise](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Créer un compte de gestionnaire d’inscription d’appareil

Vous pouvez créer un compte de gestionnaire d’inscription d’appareil pour utilisateur unique dans Intune pour gérer un grand nombre d’appareils mobiles pour votre organisation. Après avoir créé un compte de gestionnaire d’inscription d’appareil, un gestionnaire de compte désigné peut inscrire plus d’appareils que les 15 pouvant être inscrits par un utilisateur standard.

Vous pouvez utiliser un compte de gestionnaire d’inscription d’appareil pour inscrire uniquement des appareils qui ne sont pas utilisés par un utilisateur spécifique. Ces types d’appareils sont adaptés aux applications utilitaires ou de point de vente, par exemple, mais ne le sont pas pour les utilisateurs qui doivent accéder à des e-mails ou ressources de l’entreprise.

Découvrez comment [inscrire des appareils d’entreprise en utilisant un compte de gestionnaire d’inscription d’appareil](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporateowned-windows-10-enterprise-devices"></a>Inscrire des appareils d’entreprise Windows 10 Entreprise

Si vous utilisez Azure Active Directory Premium ou Microsoft Enterprise Mobility Suite dans votre organisation, vous pouvez [inscrire des appareils Windows 10 Entreprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Quand un utilisateur ajoute un compte professionnel ou scolaire sur un appareil, celui-ci est automatiquement marqué comme « appartenant à l’entreprise ».

## <a name="import-imei-numbers"></a>Importer des numéros IMEI

De nombreux fabricants d’appareils mobiles utilisent un numéro unique appelé IMEI sur leurs appareils. Vous pouvez importer les numéros IMEI des appareils appartenant à votre organisation. Quand l’appareil est géré par Intune, il est marqué comme appareil appartenant à l’entreprise.

Découvrez comment [marquer des appareils d’entreprise en utilisant des numéros IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporateowned"></a>Identifier un appareil comme appartenant à l’entreprise

Dans une liste d’appareils, **Propriété** a pour valeur **Entreprise**. Un appareil d’entreprise a l’une des caractéristiques suivantes :

 - Il a été [inscrit à l’aide d’un compte de gestionnaire d’inscription d’appareil](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).
 - Il a été inscrit à l’aide du service [Apple DEP](ios-device-enrollment-program-in-microsoft-intune.md) ou de l’outil [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md).
 - Son fabricant l’a [prédéclaré à l’aide de numéros IMEI](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).
 - Il est inscrit dans [Azure Active Directory ou Enterprise Mobility Suite comme appareil Windows 10 Entreprise](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview).



<!--HONumber=Nov16_HO2-->


