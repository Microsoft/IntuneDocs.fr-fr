---
title: "Gérer les appareils d’entreprise | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69cf07aa0747448e0ef3384b5b5132e0e76aed45
ms.openlocfilehash: e07053b9b26afacc03e45f2cb104eda6088a1e05


---

# Inscrire les appareils d’entreprise avec Microsoft Intune
Les appareils d’entreprise ou d’organisation peuvent être placés sous gestion par Intune de diverses façons en fonction de l’appareil, de la méthode utilisée pour son achat et des besoins de l’organisation.

## Appareils iOS d’entreprise
Ces méthodes d’inscription sont adaptées aux scénarios CYOD (Choisissez votre propre appareil) dans lesquels l’organisation achète les appareils pour les utilisateurs mais souhaite conserver la gestion de l’appareil. Si votre organisation a acheté des appareils iOS, vous pouvez préconfigurer l’inscription afin que l’appareil soit géré dès la première fois que l’utilisateur l’allume. Intune prend en charge l’inscription à l’aide du programme d’inscription d’appareils (DEP, Device Enrollment Program) d’Apple ou de l’outil [Apple Configurator](ios-device-enrollment-program-in-microsoft-intune.md) à exécuter sur un ordinateur Mac pour l’inscription [directe](ios-direct-enrollment-in-microsoft-intune.md) ou avec l’[Assistant de configuration](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Inscrire des appareils iOS d'entreprise](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Gestionnaire d'inscription d'appareil
Les organisations peuvent utiliser Intune pour gérer un grand nombre d’appareils mobiles avec un seul compte de gestionnaire des inscriptions d’appareils. Après avoir créé un compte de gestionnaire d’inscription d’appareils, ce compte peut être utilisé par un gestionnaire pour inscrire plus que les cinq appareils standards autorisés par défaut pour les utilisateurs normaux. L’inscription d’appareils avec un gestionnaire d’inscription des appareils ne fonctionne que pour les appareils qui ne sont pas utilisés par un utilisateur spécifique. Ces appareils sont adaptés aux applications utilitaires ou de point de vente, par exemple, mais ne le sont pas pour les utilisateurs qui doivent accéder à des messages électroniques ou ressources de l’entreprise.

[Inscrire des appareils d’entreprise avec le gestionnaire d’inscription d’appareil](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Numéro d’identité internationale d’équipement mobile (IMEI, International Mobile Equipment Identity)
Les numéros IMEI uniques sont une propriété d’appareil commune pour de nombreux fabricants d’appareils mobiles. Les administrateurs Intune peuvent importer des numéros IMEI pour les appareils appartenant à l’entreprise. Lorsque l’appareil est géré par Intune, il peut être marqué comme appareil de l’entreprise et être ciblé avec la stratégie appropriée.

[Spécifier des appareils d’entreprise avec des numéros IMEI (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jun16_HO5-->


