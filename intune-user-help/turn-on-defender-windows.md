---
title: Activer Windows Defender | Microsoft Docs
description: Découvrez comment activer Windows Defender pour accéder aux ressources de l’entreprise.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d51e9db367925442c7b6c735b1de86891e05856
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "55845276"
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>Activer Windows Defender pour accéder aux ressources de l’entreprise

Votre entreprise ou établissement scolaire souhaite s’assurer que les appareils accédant à leurs ressources sont sécurisés. Pour cela, il ou elle peut utiliser [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx), protection intégrée de Windows contre les logiciels malveillants, de plusieurs manières.

Vous devrez peut-être modifier quelques paramètres de Windows Defender afin de résoudre les problèmes d’accès. Ces étapes peuvent nécessiter d’accéder à quelques emplacements différents sur votre ordinateur.

## <a name="turn-on-windows-defender"></a>Activer Windows Defender

1. Dans **Démarrer**, ouvrez le **Panneau de configuration**.
2. Ouvrez **Outils d’administration** > **Modifier la stratégie de groupe**. Cela ouvre **l’Éditeur de stratégie de groupe locale** dans une nouvelle fenêtre.
3. Ouvrez **Configuration ordinateur** > **Modèles d’administration** > **Composants Windows** > **Antivirus Windows Defender**. Le paramètre **Désactiver l’antivirus Windows Defender** se trouve sous les dossiers d’autres paramètres. 
4. Ouvrez **Désactiver l’antivirus Windows Defender** et vérifiez que ce paramètre a la valeur **Désactivé** ou **Non configuré**.

## <a name="turn-on-real-time-protection"></a>Activer la protection en temps réel

Pour vérifier que la protection en temps réel est activée, accédez à **Démarrer** et recherchez **Centre de sécurité Windows Defender**. Sélectionnez **Paramètres de protection contre les virus et menaces** et vérifiez que **Protection en temps réel** et **Protection assurée par le cloud** ont tous deux la valeur **Activé**. Si ces options ne sont pas visibles, effectuez les étapes suivantes pour les activer :

1. Dans **Démarrer**, ouvrez le **Panneau de configuration**.
2. Ouvrez **Outils d’administration** > **Modifier la stratégie de groupe**. Cela ouvre **l’Éditeur de stratégie de groupe locale** dans une nouvelle fenêtre.
3. Ouvrez **Configuration ordinateur** > **Modèles d’administration** > **Composants Windows** > **Centre de sécurité Windows Defender** > **Protection contre les virus et menaces**.
4. Ouvrez le paramètre **Protection contre les virus et menaces** et affectez-lui la valeur **Désactivé**.

## <a name="update-your-antivirus-definitions"></a>Mettre à jour vos définitions d’antivirus

Pour vérifier que vos définitions d’antivirus sont à jour, accédez à **Démarrer** et recherchez **Centre de sécurité Windows Defender**. Sélectionnez **Mises à jour de la protection** et **Rechercher les mises à jour** pour vous assurer que votre appareil dispose d’une protection à jour contre les virus. Si cette option n’est pas visible, suivez les étapes fournies dans [Activer la protection en temps réel](turn-on-defender-windows.md#turn-on-real-time-protection).

Encore besoin d’aide ? Contactez le support technique de votre entreprise. Pour obtenir ses informations de contact, consultez le [site web du Portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980).
