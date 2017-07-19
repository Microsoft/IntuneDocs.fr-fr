---
title: "Contourner le verrou d’activation iOS avec Intune"
titleSuffix: Intune on Azure
description: "Apprenez à utiliser Intune pour contourner le verrou d’activation iOS pour accéder aux appareils verrouillés."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b92949efca2e4dac5836755e2f32b0527d4762d
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2017
---
# <a name="bypass-activation-lock-on-supervised-ios-devices-with-intune"></a>Contourner le verrou d’activation sur des appareils iOS supervisés avec Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune peut vous aider à gérer le verrou d’activation iOS, une fonctionnalité de l’application Rechercher mon iPhone pour les appareils iOS 8.0 et versions ultérieures. Le verrou d’activation est activé automatiquement lorsqu’un utilisateur ouvre l’application Rechercher mon iPhone sur un appareil. Une fois qu’il est activé, l’ID et le mot de passe Apple de l’utilisateur doivent être entrés pour pouvoir :

- Désactiver Rechercher mon iPhone
- Effacer l'appareil
- Réactiver l'appareil

## <a name="how-activation-lock-affects-you"></a>Impact du verrou d'activation

Bien qu’il permette de sécuriser les appareils iOS et améliore les chances de récupération des données d’un appareil perdu ou volé, le verrou d’activation peut présenter quelques défis pour les administrateurs informatiques. Exemple :

- Un utilisateur configure le verrou d’activation sur un appareil. L'utilisateur quitte ensuite l'entreprise et rend l'appareil. Sans l’ID Apple et le mot de passe de l’utilisateur, il n’existe aucun moyen de réactiver l’appareil.
- Vous avez besoin d’un rapport répertoriant tous les appareils sur lesquels le verrou d’activation est activé.
- Vous voulez réaffecter certains appareils à un autre service lors de l’actualisation des appareils au sein de votre organisation. Vous ne pouvez réaffecter que les appareils sur lesquels le verrou d’activation n’est pas activé.

Pour résoudre ces problèmes, Apple a introduit le contournement du verrou d'activation dans iOS 7.1. Il vous permet de supprimer le verrou d'activation des appareils supervisés sans avoir l'ID Apple et le mot de passe de l'utilisateur. Les appareils supervisés peuvent générer un code de contournement du verrou d'activation spécifique à l'appareil, qui est stocké sur le serveur d'activation d'Apple.

>[!TIP]
>Le mode supervisé pour les appareils iOS vous permet d’utiliser l’outil Apple Configurator pour verrouiller un appareil et limiter ainsi la fonctionnalité à des usages professionnels spécifiques. Le mode surveillé est généralement destiné uniquement aux appareils appartenant à l'entreprise.

Vous pouvez en savoir plus sur le verrou d’Activation sur le [site web d’Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Gestion du verrou d'activation dans Intune
Intune peut demander l’état du verrou d’activation des appareils supervisés qui exécutent iOS 8.0 et versions ultérieures. Pour les appareils supervisés uniquement, Intune peut récupérer le code de contournement du verrou d’activation et le transmettre directement à l’appareil. Si l’appareil a été réinitialisé, vous pouvez y accéder directement en utilisant un mot de passe vide et le code comme nom d'utilisateur.

**Les avantages sont les suivants :**

- L’utilisateur bénéficie des avantages en termes de sécurité offerts par l’application Rechercher mon iPhone.
- Vous pouvez permettre à l’utilisateur d’effectuer son travail en sachant que l’appareil peut être mis hors service ou déverrouillé lorsque vous devez le réaffecter.

## <a name="before-you-start"></a>Avant de commencer
Avant de pouvoir contourner le verrou d’activation sur les appareils, vous devez d’abord l’activer. Pour cela :

1. Configurez un profil de restriction d’appareil Intune pour iOS avec les informations de [Guide de configuration des paramètres de restriction d’appareil](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Activez le paramètre de mode **plein écran** **Verrou d’activation**.
3. Enregistrez le profile et affectez-le à des appareils sur lesquels vous souhaitez gérer le contournement du verrou d’activation.


## <a name="how-to-use-activation-lock-bypass"></a>Comment utiliser le contournement du verrou d’activation

>[!IMPORTANT]
>Une fois que vous avez contourné le verrou d’activation sur un appareil, un nouveau verrou d’activation est automatiquement appliqué lorsque l’application Rechercher mon iPhone est lancée. Pour cette raison, **vous devez être en possession physique de l’appareil avant d’appliquer cette procédure**.

L’action d’appareil à distance **Contourner le verrou d’activation** d’Intune vous permet de supprimer le verrou d'activation des appareils iOS sans avoir l'ID Apple et le mot de passe de l'utilisateur. Une fois que vous contournez le verrou d’activation, l’appareil l’active à nouveau au démarrage de l’application Trouver mon iPhone. Contournez le verrou d’activation uniquement si vous avez un accès physique à l’appareil.

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de Services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Appareils**.
4. Dans le panneau **Appareils et groupes**, choisissez **Tous les appareils**.
5. Dans la liste des appareils que vous gérez, choisissez un appareil iOS supervisé, puis choisissez l’action à distance d’appareil **Contourner le verrou d’activation**.

Vous pouvez examiner l'état de la demande de déverrouillage dans la page de détails de l'appareil dans la charge de travail **Gérer des appareils**.