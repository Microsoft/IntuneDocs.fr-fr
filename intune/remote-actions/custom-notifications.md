---
title: Envoyer des notifications personnalisées aux utilisateurs avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Création et envoi de notifications Push personnalisées aux utilisateurs d’appareils iOS/iPadOS et Android avec Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/25/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5195ee83efb68cea061e69f5cad49e9d43458450
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609353"
---
# <a name="send-custom-notifications-in-intune"></a>Envoyer des notifications personnalisées dans Intune  

Utilisez Microsoft Intune pour envoyer des notifications personnalisées aux utilisateurs d’appareils iOS/iPadOS et Android gérés. Ces messages apparaissent sous la forme de notifications Push standard provenant de l’application Portail d’entreprise et de l’application Microsoft Intune sur l’appareil d’un utilisateur, tout comme les notifications d’autres applications apparaissent sur l’appareil. Les notifications personnalisées d’Intune ne sont pas prises en charge par les appareils macOS et Windows.   

Les messages de notification personnalisés incluent un titre court et un corps de message de 500 caractères ou moins. Ces messages peuvent être personnalisés à des fins de communication générale.

### <a name="what-the-notification-looks-like-on-an-iosipados-device"></a>Apparence de la notification sur un appareil iOS/iPadOS

Si l’application Portail d’entreprise est ouverte sur l’appareil iOS/iPadOS, la notification se présente ainsi :

> [!div class="mx-imgBorder"]
> ![Notification de test sur le Portail d’entreprise iOS/iPadOS](./media/custom-notifications/105046-1.png)

Si l’appareil est verrouillé, la notification ressemble à la capture d’écran suivante :

> [!div class="mx-imgBorder"]
> ![Notification de test sur un appareil verrouillé iOS/iPadOS](./media/custom-notifications/105046-2.png)

### <a name="what-the-notification-looks-like-on-an-android-device"></a>Apparence de la notification sur un appareil Android

Si l’application Portail d’entreprise est ouverte sur un appareil Android, la notification ressemble à la capture d’écran suivante :

> [!div class="mx-imgBorder"]
> ![Notification de test Android](./media/custom-notifications/105046-3.png)

## <a name="common-scenarios-for-sending-custom-notifications"></a>Scénarios courants pour l’envoi de notifications personnalisées  

- Informer tous les employés d’une modification de la planification, comme la fermeture de bâtiments en raison d’une mauvaise météo.
- Envoyer une notification à l’utilisateur d’un seul appareil pour communiquer une demande urgente, telle que le redémarrage de l’appareil pour terminer l’installation d’une mise à jour.

## <a name="considerations-for-using-custom-notifications"></a>Considérations relatives à l’utilisation des notifications personnalisées

**Configuration de l’appareil**

- L’application Portail d’entreprise ou l’application Microsoft Intune doit être installée sur les appareils avant que les utilisateurs puissent recevoir des notifications personnalisées. Ils doivent également avoir des autorisations configurées pour permettre à l’application Portail d’entreprise ou à l’application Microsoft Intune d’envoyer des notifications Push. Si nécessaire, l’application Portail d’entreprise et l’application Microsoft Intune peuvent inviter les utilisateurs à autoriser les notifications.
- Sur Android, Google Play Services est une dépendance obligatoire.
- L’appareil doit être inscrit auprès de MDM.

**Autorisations** :

- Pour envoyer des notifications à des groupes, votre compte doit disposer de l’autorisation RBAC suivante dans Intune : *Organisation* > **Mises à jour**.
- Pour envoyer des notifications à un appareil, votre compte doit disposer de l’autorisation RBAC suivante dans Intune : *Tâche à distance* > **Envoyer des notifications personnalisées**.

**Création de notifications** :
 
- Pour créer un message, utilisez un compte qui est affecté à un rôle Intune qui inclut l’autorisation correcte, comme décrit dans la section précédente *Autorisations*. Pour affecter des autorisations à un utilisateur, consultez [Attributions de rôles](../fundamentals/role-based-access-control.md#role-assignments).
- Les notifications personnalisées sont limitées à 50 caractères pour les titres et à 500 caractères pour les messages.  
- Intune n’enregistre pas le texte des notifications personnalisées précédemment envoyées. Pour renvoyer un message, vous devez le recréer.  
- Vous pouvez envoyer seulement jusqu’à 25 messages par heure à des groupes. Cette restriction est au niveau du locataire. Cette limitation ne s’applique pas lors de l’envoi de notifications à des appareils individuels.
- Vous pouvez envoyer seulement jusqu’à 25 messages par heure à des groupes. Cette restriction est au niveau du locataire. Cette limitation ne s’applique pas lors de l’envoi de notifications à des personnes individuelles.
- Lors de l’envoi de messages à des appareils individuels, vous pouvez envoyer jusqu’à 10 messages par heure au même appareil.
- Vous pouvez envoyer des notifications à des utilisateurs dans des groupes. Lors de l’envoi de notifications à des groupes, chaque notification peut cibler directement jusqu’à 25 groupes. Les groupes imbriqués ne sont pas comptabilisés dans ce total. Lors de l’envoi d’une notification à un groupe, les messages ciblent seulement les utilisateurs du groupe, et sont envoyés à chaque appareil iOS ou Android inscrit par l’utilisateur. Les appareils du groupe sont ignorés lors du ciblage de la notification.
- Vous pouvez envoyer des notifications à un seul appareil. Au lieu d’utiliser des groupes, vous sélectionnez un appareil, puis vous utilisez une [action d’appareil](device-management.md#available-device-actions) à distance pour envoyer la notification personnalisée.  

**Remise** :

- Intune envoie les messages à l’application Portail d’entreprise ou à l’application Microsoft Intune des utilisateurs, qui crée ensuite la notification Push. Les utilisateurs n’ont pas besoin d’être connectés à l’application pour que la notification soit envoyée sur l’appareil, mais l’appareil doit avoir été inscrit par l’utilisateur ciblé.
- Intune, l’application Portail d’entreprise et l’application Microsoft Intune ne peuvent pas garantir la remise d’une notification personnalisée. Les notifications personnalisées peuvent apparaître au bout de plusieurs heures, voire pas du tout : elles ne peuvent donc pas être utilisées pour des messages urgents.  
- Les messages de notification personnalisés d’Intune apparaissent sur les appareils en tant que notifications Push standard. Si l’application Portail d’entreprise est ouverte sur un appareil iOS lors de la réception de la notification, la notification s’affiche dans l’application au lieu de le faire en tant que notification Push du système.  
- Les notifications personnalisées peuvent être visibles sur les écrans de verrouillage des appareils iOS/iPadOS et Android en fonction des paramètres des appareils.  
- Sur les appareils Android, les autres applications peuvent avoir accès aux données de vos notifications personnalisées. Ne les utilisez pas pour les communications sensibles.  
- Les utilisateurs d’un appareil qui a été récemment désinscrit ou ceux qui ont été supprimés d’un groupe peuvent continuer à recevoir une notification personnalisée envoyée ultérieurement à ce groupe.  De même, si vous ajoutez un utilisateur à un groupe après l’envoi d’une notification personnalisée au groupe, il est possible que l’utilisateur nouvellement ajouté reçoive ce message de notification précédemment envoyé.  

## <a name="send-a-custom-notification-to-groups"></a>Envoyer une notification personnalisée à des groupes

1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) avec un compte disposant des autorisations nécessaires pour créer et envoyer des notifications, puis accédez à **Administration de locataire** > **Notifications personnalisées**.  

2. Dans l’onglet De base, spécifiez les éléments suivants, puis sélectionnez **Suivant** pour continuer.  
   - **Titre** : Spécifiez un titre pour cette notification. Les titres sont limités à 50 caractères.  
   - **Corps** : Spécifiez le message. Les messages sont limités à 500 caractères.

   ![Créer une notification personnalisée](./media/custom-notifications/custom-notifications.png)  

3. Sous l’onglet **Affectations**, sélectionnez les groupes auxquels vous voulez envoyer cette notification personnalisée, puis sélectionnez Suivant pour continuer. L’envoi d’une notification à un groupe cible seulement les utilisateurs de ce groupe ; la notification est envoyée à tous les appareils iOS et Android inscrits par cet utilisateur.

4. Sous l’onglet **Vérifier + créer**, passez en revue les informations et, quand vous êtes prêt à envoyer la notification, sélectionnez **Créer**.  

Intune traite immédiatement les messages que vous créez. La seule confirmation indiquant que le message a été envoyé est la notification Intune qui confirme que la notification personnalisée a été envoyée.  

![Confirmation de l’envoi d’une notification](./media/custom-notifications/notification-sent.png)  

Intune ne fait pas le suivi des notifications personnalisées que vous envoyez, et les appareils ne journalisent pas la réception en dehors du centre de notifications de l’appareil. La notification peut être contenue dans un journal de diagnostic temporaire si un utilisateur demande du support dans l’application Portail d’entreprise ou l’application Intune.

## <a name="send-a-custom-notification-to-a-single-device"></a>Envoyer une notification personnalisée à un seul appareil

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) avec un compte disposant des autorisations nécessaires pour créer et envoyer des notifications, puis accédez à **Appareils** > **Tous les appareils**.

2. Double-cliquez sur le nom de l’appareil géré auquel vous souhaitez envoyer une notification pour ouvrir la page *Présentation*.

3. Dans la page **Vue d’ensemble** , sélectionnez l’action d’appareil **Envoyer une notification personnalisée** pour ouvrir le volet *Envoyer une notification personnalisée*. Si cette option n’est pas disponible, sélectionnez l’option **...** (ellipses) en haut à droite de la page, puis sélectionnez **Envoyer une notification personnalisée**.

4. Dans le volet **Envoyer une notification personnalisée**, spécifiez les détails du message suivants :  

   - **Titre** : Spécifiez un titre pour cette notification. Les titres sont limités à 50 caractères.  
   - **Corps** : Spécifiez le message. Les messages sont limités à 500 caractères.  

5. Sélectionnez **Envoyer** pour envoyer la notification personnalisée à l’appareil. Contrairement aux notifications que vous envoyez à des groupes, vous ne configurez pas d’attribution ni ne revoyez le message avant de l’envoyer.  

Intune traite le message immédiatement. La seule confirmation que le message a été envoyé est la notification Intune que vous recevez dans la console, qui affiche le texte du message que vous avez envoyé.  

## <a name="receive-a-custom-notification"></a>Recevoir une notification personnalisée

Sur un appareil, les utilisateurs voient les messages de notification personnalisés qui sont envoyés par Intune en tant que notification Push standard provenant de l’application Portail d’entreprise ou de l’application Microsoft Intune. Ces notifications sont similaires aux notifications Push que les utilisateurs reçoivent d’autres applications sur l’appareil.  

Sur les appareils iOS/iPadOS, si l’application Portail d’entreprise est ouverte à la réception de la notification, celle-ci s’affiche dans l’application au lieu de se présenter comme une notification Push.  

La notification est conservée jusqu’à ce que l’utilisateur la masque.  

## <a name="next-steps"></a>Étapes suivantes

[Gérer les appareils](device-management.md)
