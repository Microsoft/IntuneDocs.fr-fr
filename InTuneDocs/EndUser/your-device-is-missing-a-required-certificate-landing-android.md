---
title: "Il manque un certificat obligatoire à votre appareil | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- Company Portal
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 207297601634f390051a6345b96bf09e1d031747
ms.openlocfilehash: 6b37cede797f965b82c067b274517277d8597939

---


# <a name="your-device-is-missing-a-required-certificate"></a>Un certificat obligatoire est manquant sur votre appareil

## <a name="whats-a-certificate"></a>Qu’est-ce qu’un certificat ?

Le [chiffrement](https://technet.microsoft.com/en-us/library/cc962030.aspx) est la science de la sécurisation des informations. Traditionnellement, le chiffrement a été utilisé pour transmettre des messages codés afin de [vous assurer que la communication est gardée secrète](https://technet.microsoft.com/en-us/library/cc962019.aspx). Dans sa forme la plus simple, le chiffrement remplace ou transpose des lettres pour créer un message codé dans un message illisible, brouillé ou masqué. Seule une personne disposant d’une clé de décodage ou d’un _certificat_ peut reconvertir le message codé dans sa forme d’origine et lisible. Votre appareil Android utilise des certificats avec Intune pour garantir que les communications entre votre périphérique et vos ressources organisationnelles telles que les e-mails et les documents sont sécurisées d’une extrémité à l’autre.

## <a name="fixing-certificate-issues"></a>Résolution des problèmes liés aux certificats

Si votre appareil Android n’est pas inscrit dans Intune et qu’il manque un certificat exigé par votre administrateur informatique, vous ne pouvez pas vous connecter à l’application Portail d’entreprise. Quand vous essayez de vous connecter, le message suivant s’affiche :

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

La première étape consiste à vérifier si [un certificat qui est généralement préinstallé sur votre appareil manque](your-device-is-missing-a-preinstalled-certificate-android.md).

Si cela ne fonctionne pas, votre administrateur informatique peut [vous obliger à installer un deuxième certificat pour renforcer la sécurité](your-device-is-missing-an-IT-required-certificate-android.md).

Encore besoin d’aide ? Contactez votre administrateur informatique. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](http://portal.manage.microsoft.com).



<!--HONumber=Jan17_HO2-->


