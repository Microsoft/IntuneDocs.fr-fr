---
title: Votre appareil Android semble être chiffré | Microsoft Docs
description: Résoudre l’état du chiffrement dans Portail d’entreprise et Microsoft Intune application
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/14/2019
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
ms.openlocfilehash: caae22e59e8adb6952e9a69ff03c575ae4467b2d
ms.sourcegitcommit: 6a946a055a2014e00a4ca9d71986727a4ebbc777
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238971"
---
# <a name="device-encrypted-but-apps-say-otherwise"></a>Appareil chiffré, mais les applications disent autrement

Si Portail d’entreprise ou l’application Microsoft Intune indiquent que votre appareil n’est pas chiffré, mais que vous êtes sûr que c’est le cas, essayez les étapes décrites dans cet article.  

## <a name="add-a-startup-pin"></a>Ajouter un code confidentiel de démarrage

Certains appareils Android exigent la création d’un code de démarrage pour en garantir la sécurité. L’emplacement de ce paramètre se trouve dans l’application **paramètres** de votre appareil. Le nom et l’emplacement du paramètre peuvent varier. Par exemple, sur le S7 Samsung Galaxy, le paramètre est appelé **Démarrage sécurisé**. Pour l’activer et créer un code secret, accédez à **paramètres** > **écran de verrouillage et sécurité** > -**Démarrage sécurisé**.  

## <a name="encrypt-the-entire-device"></a>Chiffrer l’appareil entier

Cette section s’applique uniquement à l’application Portail d’entreprise. Certains appareils vous offrent le choix entre le chiffrement de l’appareil entier ou juste de l’espace utilisé. Choisissez l’option permettant de chiffrer la totalité de l’appareil. Si vous avez choisi de chiffrer uniquement l’espace utilisé :

1. [Supprimez cet appareil du portail d’entreprise](unenroll-your-device-from-intune-android.md).
2. Déchiffrez l’espace utilisé.  
3. Chiffrez l’appareil entier.  
4. Réinscrire le périphérique.  

## <a name="downgrade-your-version-of-android"></a>Rétrograder votre version d’Android

Cette section s’applique uniquement à l’application Portail d’entreprise. Si votre appareil vous offre la possibilité de passer à la version antérieure Android 6.0+ et versions supérieures, faites-le. Si vous essayez de passer votre appareil à une version antérieure, vous risquez de perdre des données. Sinon, nous vous recommandons de contacter le support technique de votre entreprise pour résoudre ce problème. Obtenez les coordonnées du support de votre entreprise sur le [site web Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).  

## <a name="specific-manufacturer-issues"></a>Problèmes propres à certains fabricants

Certains appareils Android exécutant la version 7.0+ et des versions ultérieures chiffrent les données de manière non conforme à certaine normes de la plateforme Android. Ces méthodes de chiffrement placent les informations sur les appareils en danger. Par conséquent, ces appareils ne sont pas pris en charge.

Pour obtenir une liste non exhaustive des appareils Android pris en charge, consultez l’article [systèmes d’exploitation et navigateurs pris en charge dans Intune](https://docs.microsoft.com/intune/supported-devices-browsers#supported-samsung-knox-standard-devices). Si votre appareil n’est pas listé, reportez-vous au fabricant de l’appareil ou contactez votre personne de support.

> [!Note]
> Microsoft travaille avec les fabricants pour résoudre les problèmes que nous identifions lors des tests ou que les utilisateurs nous signalent. Cet article est mis à jour chaque fois que de nouvelles informations sont disponibles.

## <a name="update-devices"></a>Mettre à jour les appareils

Si vous n’avez pas mis à jour votre appareil vers la version la plus récente d’Android, accédez à l’application **paramètres** de votre appareil, puis sélectionnez **mettre à jour**.  

## <a name="next-steps"></a>Étapes suivantes

Encore besoin d’aide ? Contactez le support technique de votre entreprise (consultez le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour les informations de contact) ou écrivez à <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">l’équipe Microsoft Android</a>.  
