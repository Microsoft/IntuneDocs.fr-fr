---
title: Contournement du verrouillage d’activation iOS/iPadOS avec Intune
titleSuffix: Microsoft Intune
description: Découvrez comment utiliser Intune pour contourner le verrouillage d’activation iOS/iPadOS et ainsi accéder aux appareils verrouillés.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9ca3b0ba-e41c-45fb-af28-119dff47c59f
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af5bb1c95a15a5c52585278605e2f7a86307cb76
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782229"
---
# <a name="disable-activation-lock-on-supervised-iosipados-devices-with-intune"></a>Désactivation du verrouillage d’activation sur les appareils iOS/iPadOS supervisés avec Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune peut vous aider à gérer le verrouillage d’activation iOS/iPadOS, une fonctionnalité de l’application Rechercher mon iPhone disponible sur les appareils iOS/iPadOS 8.0 (et versions ultérieures). Le verrou d’activation est activé automatiquement lorsqu’un utilisateur ouvre l’application Rechercher mon iPhone sur un appareil. Une fois qu’il est activé, l’ID et le mot de passe Apple de l’utilisateur doivent être entrés pour pouvoir :

- Désactiver Rechercher mon iPhone
- Effacer l'appareil
- Réactiver l'appareil

## <a name="how-activation-lock-affects-you"></a>Impact du verrou d'activation

S’il permet de sécuriser les appareils iOS/iPadOS et d’améliorer les chances de récupération des données d’un appareil perdu ou volé, le verrouillage d’activation peut néanmoins présenter quelques difficultés pour les administrateurs informatiques. Par exemple :

- Un utilisateur configure le verrou d’activation sur un appareil. L'utilisateur quitte ensuite l'entreprise et rend l'appareil. Sans l’ID Apple et le mot de passe de l’utilisateur, il n’existe aucun moyen de réactiver l’appareil.
- Vous avez besoin d’un rapport répertoriant tous les appareils sur lesquels le verrou d’activation est activé.
- Vous voulez réaffecter certains appareils à un autre service lors de l’actualisation des appareils au sein de votre organisation. Vous ne pouvez réaffecter que les appareils sur lesquels le verrou d’activation n’est pas activé.

Pour résoudre ces problèmes, Apple a introduit la désactivation du verrouillage d’activation dans iOS/iPadOS 7.1. Désactiver le verrouillage d’activation vous permet de supprimer le verrouillage d’activation des appareils supervisés sans avoir l’ID Apple et le mot de passe de l’utilisateur. Les appareils supervisés peuvent générer un code de contournement du verrou d'activation spécifique à l'appareil, qui est stocké sur le serveur d'activation d'Apple.

>[!TIP]
>Le mode supervisé pour les appareils iOS/iPadOS permet d’utiliser Apple Configurator afin de verrouiller un appareil et ainsi de limiter ls fonctionnalités à des usages professionnels spécifiques. Le mode surveillé est destiné uniquement aux appareils appartenant à l’entreprise.

Vous pouvez en savoir plus sur le verrou d’Activation sur le [site web d’Apple](https://support.apple.com/HT201365).

## <a name="how-intune-helps-you-manage-activation-lock"></a>Gestion du verrou d'activation dans Intune
Intune peut demander l’état du verrouillage d’activation des appareils supervisés qui possèdent la version 8.0 ou une version ultérieure d’iOS/iPadOS. Pour les appareils supervisés uniquement, Intune peut récupérer le code de désactivation du verrouillage d’activation et le transmettre directement à l’appareil. Si l’appareil a été réinitialisé, vous pouvez y accéder directement en utilisant un mot de passe vide et le code comme nom d'utilisateur.

**L’utilisation d’Intune pour gérer le verrouillage d’activation présente les avantages suivants :**

- L’utilisateur bénéficie des avantages en termes de sécurité offerts par l’application Rechercher mon iPhone.
- Vous pouvez permettre à l’utilisateur d’effectuer son travail en sachant que l’appareil peut être mis hors service ou déverrouillé lorsque vous devez le réaffecter.

## <a name="before-you-start"></a>Avant de commencer
Avant de pouvoir désactiver le verrouillage d’activation sur les appareils, vous devez d’abord l’activer en suivant ces instructions :

1. Configurez un profil de restriction d’appareil Intune pour iOS/iPadOS suivant les informations du [Guide de configuration des paramètres de restriction d’appareil](/intune-azure/configure-devices/how-to-configure-device-restrictions).
2. Dans les [paramètres de restriction d’appareil pour iOS/iPadOS](../configuration/device-restrictions-ios.md), sous les paramètres **Général**, activez l’option **Verrouillage d’activation**.
3. Enregistrez le profil, puis [affectez-le](../configuration/device-profile-assign.md) aux appareils sur lesquels vous souhaitez gérer la désactivation du verrouillage d’activation.


## <a name="how-to-use-disable-activation-lock"></a>Comment désactiver le verrouillage d’activation

>[!IMPORTANT]
>Une fois que vous avez désactivé le verrouillage d’activation sur un appareil, un nouveau verrouillage d’activation est appliqué automatiquement si l’application Localiser mon iPhone est démarrée. Pour cette raison, **vous devez être en possession physique de l’appareil avant d’appliquer cette procédure**.

L’action d’appareil à distance **Désactiver le verrouillage d’activation** d’Intune permet de supprimer le verrouillage d’activation d’un appareil iOS/iPadOS sans avoir besoin de l’ID ni du mot de passe Apple de l’utilisateur. Une fois que vous avez désactivé le verrouillage d’activation, l’appareil le réactive au démarrage de l’application Localiser mon iPhone. Désactivez le verrouillage d’activation uniquement si vous avez un accès physique à l’appareil.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Dans le panneau **Intune**, sélectionnez **Appareils**.
4. Dans le panneau **Appareils**, sélectionnez **Tous les appareils**.
5. Dans la liste des appareils que vous gérez, sélectionnez l’action à distance **Désactiver le verrouillage d’activation**.
6. Accédez à la section « Matériel » de l’appareil, puis copiez la valeur **Code de contournement du verrou d’activation** sous **Accès conditionnel**.

    >[!NOTE]
    >Copiez le code de contournement avant de réinitialiser l’appareil. Si vous réinitialisez les paramètres de l’appareil avant de copier le code, celui-ci est supprimé d’Azure.

7. Accédez au panneau **Vue d’ensemble** de l’appareil, puis sélectionnez **Réinitialiser**.
8. Une fois l’appareil réinitialisé, vous êtes invité à fournir l’*ID Apple* et le *mot de passe*. Laissez le champ *ID* vide, puis entrez le **code de contournement** pour le *mot de passe*. Cela supprime le compte de l’appareil. 


## <a name="next-steps"></a>Étapes suivantes

Vous pouvez examiner l'état de la demande de déverrouillage dans la page de détails de l'appareil dans la charge de travail **Gérer des appareils**.
