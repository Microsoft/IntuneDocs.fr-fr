---
title: Il manque un certificat obligatoire à votre appareil | Microsoft Docs
titlesuffix: Microsoft Intune
description: Un certificat exigé par le support technique de votre entreprise est manquant sur votre appareil.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser; seodec18
ms.openlocfilehash: e40ac2fd81375b84084dd229f4cb5a6ab3e9915f
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032212"
---
# <a name="your-device-is-missing-a-required-certificate"></a>Un certificat obligatoire est manquant sur votre appareil

## <a name="whats-a-certificate"></a>Qu’est-ce qu’un certificat ?

Le [chiffrement](https://technet.microsoft.com/library/cc962030.aspx) est la science de la sécurisation des informations. Traditionnellement, le chiffrement a été utilisé pour transmettre des messages codés afin de [vous assurer que la communication est gardée secrète](https://technet.microsoft.com/library/cc962019.aspx). Dans sa forme la plus simple, le chiffrement remplace ou transpose des lettres pour créer un message codé dans un message illisible, brouillé ou masqué. Seule une personne disposant d’une clé de décodage ou d’un _certificat_ peut reconvertir le message codé dans sa forme d’origine et lisible. Votre appareil Android utilise des certificats avec Intune pour garantir que les communications entre votre périphérique et vos ressources organisationnelles telles que les e-mails et les documents sont sécurisées d’une extrémité à l’autre.

## <a name="fixing-certificate-issues"></a>Résolution des problèmes liés aux certificats

Si votre appareil Android n’est pas inscrit dans Intune et qu’il manque un certificat exigé par le support technique de votre entreprise, vous ne pouvez pas vous connecter à l’application Portail d’entreprise. Quand vous essayez de vous connecter, le message suivant s’affiche :

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

La première étape consiste à vérifier si [un certificat qui est généralement préinstallé sur votre appareil manque](your-device-is-missing-a-preinstalled-certificate-android.md).

Si la résolution des problèmes liés aux certificats ne fonctionne pas, le support de votre entreprise peut [vous demander à installer un deuxième certificat pour renforcer la sécurité](your-device-is-missing-an-IT-required-certificate-android.md).

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses coordonnées, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
