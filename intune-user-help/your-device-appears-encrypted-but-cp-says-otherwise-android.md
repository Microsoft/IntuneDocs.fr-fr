---
title: Votre appareil Android semble être chiffré | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55935b2f69f9573d8df5ea5ca32fb4587c652b26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389464"
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>Votre appareil Android semble être chiffré, mais le portail d’entreprise dit que non

Quand vous chiffrez un appareil, vous encodez les informations qu’il contient à l’aide d’une clé secrète connue de vous seul. Cela empêche les personnes non autorisées d’y accéder. Nombreuses sont les organisations à exiger de leurs utilisateurs qu’ils chiffrent leurs appareils Android avant de pouvoir accéder aux fichiers, à la messagerie ou aux données d’entreprise.

## <a name="common-issues"></a>Problèmes courants

Les versions plus récentes d’Android, en particulier à partir de la v7.0, requièrent un code secret de démarrage pour garantir que votre appareil est entièrement chiffré. Les fabricants d’appareils ont des différentes descriptions et différents emplacements pour le code secret de démarrage. La plupart du temps, ce paramètre est appelé « Démarrage sécurisé ». 

## <a name="solutions"></a>Solutions

### <a name="add-a-startup-pin"></a>Ajouter un code confidentiel de démarrage

Certains appareils Android exigent la création d’un code de démarrage pour en garantir la sécurité. Il existe de nombreuses versions d’Android, proposées par de nombreux fabricants différents. Vous pouvez essayer de résoudre ce problème en recherchant un emplacement dans votre application de paramètres pour activer cette option. Par exemple, sur le Galaxy S7 de Samsung, vous activez le démarrage sécurisé en accédant à **Paramètres** > **Écran de verrouillage et sécurité** > **Démarrage sécurisé**.  

### <a name="encrypt-the-entire-device"></a>Chiffrer l’appareil entier

Certains appareils vous offrent le choix entre le chiffrement de l’appareil entier ou juste de l’espace utilisé. Choisissez l’option permettant de chiffrer l’appareil entier plutôt que l’option permettant de chiffrer « uniquement l’espace utilisé. » Si vous avez déjà chiffré uniquement l’espace utilisé :

1. [Supprimer cet appareil du portail d’entreprise](unenroll-your-device-from-intune-android.md)
2. Déchiffrer l’espace utilisé
3. Chiffrer l’appareil entier
4. Réinscrire l’appareil

### <a name="downgrade-your-version-of-android"></a>Rétrograder votre version d’Android

Si votre appareil vous offre la possibilité de passer à la version antérieure Android 6.0+, faites-le. Si vous essayez de passer votre appareil à une version antérieure, vous risquez de perdre des données. Sinon, nous vous recommandons de contacter le support technique de votre entreprise pour résoudre ce problème. Vous pouvez obtenir les informations de contact du support technique de votre entreprise sur le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).

## <a name="specific-manufacturer-issues"></a>Problèmes propres à certains fabricants

Certains appareils Android sur la version 7.0+ chiffrent les données de manière non conforme à certaine normes de la plateforme Android. Ces appareils peuvent sembler chiffrés même quand ils sont neufs. Intune considère que les méthodes de chiffrement de ces appareils risquent de compromettre leurs informations. Ce risque vient essentiellement des utilisateurs malveillants qui ont un accès physique à l’appareil.

> [!Note]
> Microsoft travaille avec les fabricants pour résoudre les problèmes que nous identifions lors des tests ou que les utilisateurs nous signalent. Cet article est mis à jour chaque fois que de nouvelles informations sont disponibles. 

## <a name="known-devices"></a>Appareils connus

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Appareils connus pouvant être mis à jour pour résoudre ce problème

Si vous n’avez pas mis à jour votre appareil à la version la plus récente d’Android, accédez à de votre appareil **paramètres** application et sélectionnez **mise à jour**. Ces appareils peuvent apparaître comme non conformes jusqu'à ce que vous mettez à jour :  

- Huawei Honor 8
- Huawei P9

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Appareils connus ne pouvant actuellement pas être mis à jour pour résoudre ce problème
Les appareils suivants apparaîtront toujours chiffrés et ne peut pas être utilisés pour accéder aux ressources de l’entreprise. Pour accéder aux ressources d’entreprise, vous devez utiliser un autre appareil.  

- Huawei Mate 8
- Appareils OPPO
- Appareils Vivo
- Smartphones Xiaomi Mi
