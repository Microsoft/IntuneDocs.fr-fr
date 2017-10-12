---
title: "Votre appareil Android semble être chiffré"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 09/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 208cf6eb2d29ec5458d97d0a4481cec420acc281
ms.sourcegitcommit: 59811bf1183b3ef9c9e81eded634bd0d3124d0bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Votre appareil Android semble être chiffré, mais le portail d’entreprise dit que non

Quand vous chiffrez un appareil, vous encodez les informations qu’il contient à l’aide d’une clé secrète connue de vous seul. Cela empêche les personnes non autorisées d’y accéder. Nombreuses sont les organisations à exiger de leurs utilisateurs qu’ils chiffrent leurs appareils Android avant de pouvoir accéder aux fichiers, à la messagerie ou aux données d’entreprise.

## <a name="common-issues"></a>Problèmes courants

Les versions plus récentes d’Android, en particulier à partir de la v7.0, requièrent un code secret de démarrage pour garantir que votre appareil est entièrement chiffré. Les fabricants d’appareils ont des différentes descriptions et différents emplacements pour le code secret de démarrage. La plupart du temps, ce paramètre est appelé « Démarrage sécurisé ». 

## <a name="solutions"></a>Solutions

### <a name="add-a-startup-pin"></a>Ajouter un code confidentiel de démarrage

Certains appareils Android exigent la création d’un code de démarrage pour en garantir la sécurité. Il existe de nombreuses versions d’Android, proposées par de nombreux fabricants différents. Vous pouvez essayer de résoudre ce problème en recherchant un emplacement dans votre application de paramètres pour activer cette option. Par exemple, sur le Galaxy S7 de Samsung, vous activez le démarrage sécurisé en accédant à **Paramètres** > **Écran de verrouillage et sécurité** > **Démarrage sécurisé**.  

### <a name="downgrade-your-version-of-android"></a>Rétrograder votre version d’Android

Si votre appareil vous offre la possibilité de passer à la version antérieure Android 6.0+, faites-le. Si vous essayez de passer votre appareil à une version antérieure, vous risquez de perdre des données. Sinon, nous vous recommandons de contacter le support technique de votre entreprise pour résoudre ce problème. Vous pouvez obtenir les informations de contact du support technique de votre entreprise sur le [site web du portail d’entreprise](https://portal.manage.microsoft.com).

## <a name="specific-manufacturer-issues"></a>Problèmes propres à certains fabricants

Certains appareils Android sur la version 7.0+ chiffrent les données de manière non conforme à certaine normes de la plateforme Android. Ces appareils peuvent sembler chiffrés même quand ils sont neufs. Intune considère que les méthodes de chiffrement de ces appareils risquent de compromettre leurs informations. Ce risque vient essentiellement des utilisateurs malveillants qui ont un accès physique à l’appareil.

> [!Note]
> Microsoft travaille avec les fabricants pour résoudre les problèmes que nous identifions lors des tests ou que les utilisateurs nous signalent. Cet article est mis à jour chaque fois que de nouvelles informations sont disponibles. 

## <a name="known-devices"></a>Appareils connus

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Appareils connus pouvant être mis à jour pour résoudre ce problème

Si vous avez un des appareils suivants, vous pouvez rencontrer ce problème si vous n'avez pas mis à jour votre appareil vers la version la plus récente d’Android. Vous pouvez installer des mises à jour pour ces appareils en accédant à **Paramètres** > **Mise à jour**. 

- [Huawei Honor 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [Huawei P9](http://consumer.huawei.com/en/phones/p9/)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Appareils connus ne pouvant actuellement pas être mis à jour pour résoudre ce problème

Vous ne pouvez pas résoudre ce problème pour les appareils ci-dessous. Vous devrez peut-être utiliser un autre appareil pour accéder aux ressources de l’entreprise. 

- [Huawei Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [Smartphones Xiaomi Mi](https://xiaomi-mi.com/mi-smartphones/)
