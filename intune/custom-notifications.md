---
title: Envoyer des notifications personnalisées aux utilisateurs avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Utiliser Intune pour créer et envoyer des notifications Push personnalisées aux utilisateurs d’appareils iOS et Android
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bffbc96e945d522453c299717a6eb413354a4af4
ms.sourcegitcommit: 98f2597eec28c6096985d5a1acae72430c2afb1a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70878038"
---
# <a name="send-custom-notifications-in-intune"></a>Envoyer des notifications personnalisées dans Intune  

Utilisez Microsoft Intune pour envoyer des notifications personnalisées aux utilisateurs d’appareils iOS et Android gérés. Ces messages apparaissent sous la forme de notifications Push standard provenant de l’application Portail d’entreprise et de l’application Microsoft Intune sur l’appareil d’un utilisateur, tout comme les notifications d’autres applications apparaissent sur l’appareil. Les notifications personnalisées d’Intune ne sont pas prises en charge par les appareils Windows.   

Les messages de notification personnalisés incluent un titre court et un corps de message de 500 caractères au maximum. Ces messages peuvent être personnalisés à des fins de communication générale.

## <a name="common-scenarios-for-sending-custom-notifications"></a>Scénarios courants pour l’envoi de notifications personnalisées  

- Utilisez des notifications personnalisées pour alerter des utilisateurs spécifiques qu’une nouvelle application est disponible dans le Portail d’entreprise.  
- Notifiez tous les employés d’une modification de la planification, comme la fermeture des bâtiments en raison d’une mauvaise météo.  

## <a name="considerations-for-using-custom-notifications"></a>Considérations relatives à l’utilisation des notifications personnalisées  

**Configuration de l’appareil** :  
- L’application Portail d’entreprise ou l’application Microsoft Intune doit être installée sur les appareils avant que les utilisateurs puissent recevoir des notifications personnalisées. Ils doivent également avoir des autorisations configurées pour permettre à l’application Portail d’entreprise ou à l’application Microsoft Intune d’envoyer des notifications Push. Si nécessaire, l’application Portail d’entreprise et l’application Microsoft Intune peuvent inviter les utilisateurs à autoriser les notifications.  
- Sur Android, Google Play Services est une dépendance obligatoire.  
- L’appareil doit être inscrit auprès de MDM.

**Création de notifications** :  
- Pour créer un message, utilisez un compte qui est affecté à un rôle Intune incluant l’autorisation **Mettre à jour** pour **Organisation**. Pour affecter des autorisations à un utilisateur, consultez [Attributions de rôles](role-based-access-control.md#role-assignments).  
- Les notifications personnalisées sont limitées à 50 caractères pour les titres et à 500 caractères pour les messages.  
- Intune n’enregistre pas les messages envoyés. Pour renvoyer un message, vous devez le recréer.  
- Vous pouvez envoyer seulement jusqu’à 25 messages par heure. Cette restriction est au niveau du locataire.  
- Chaque notification peut cibler directement jusqu’à 25 groupes. Les groupes imbriqués ne sont pas comptabilisés dans ce total.  
- Les groupes peuvent inclure des utilisateurs ou des appareils, mais les messages sont envoyés seulement aux utilisateurs, et ils sont envoyés à chacun des appareils iOS ou Android que l’utilisateur a inscrits.  

**Remise** :  
- Intune envoie les messages à l’application Portail d’entreprise ou à l’application Microsoft Intune des utilisateurs, qui crée ensuite la notification Push. Les utilisateurs n’ont pas besoin d’être connectés à l’application pour que la notification soit envoyée sur l’appareil.  
- Intune, ainsi que l’application Portail d’entreprise et l’application Microsoft Intune ne peuvent pas garantir la remise d’une notification personnalisée. Les notifications personnalisées peuvent apparaître au bout de plusieurs heures, voire pas du tout : elles ne peuvent donc pas être utilisées pour des messages urgents.  
- Les messages de notification personnalisés d’Intune apparaissent sur les appareils en tant que notifications Push standard. Si l’application Portail d’entreprise est ouverte sur un appareil iOS lors de la réception de la notification, la notification s’affiche dans l’application au lieu d’être une notification Push.  
- Les notifications personnalisées peuvent être visibles sur les écrans de verrouillage sur les appareils iOS et Android en fonction des paramètres de l’appareil.  
- Sur les appareils Android, les autres applications peuvent avoir accès aux données de vos notifications personnalisées. Ne les utilisez pas pour les communications sensibles.  
- Les utilisateurs d’un appareil qui a été récemment désinscrit ou ceux qui ont été supprimés d’un groupe peuvent encore recevoir une notification personnalisée qui est envoyée par la suite à ce groupe.  De même, si vous ajoutez un utilisateur à un groupe après l’envoi d’une notification personnalisée au groupe, il est possible que l’utilisateur nouvellement ajouté reçoive ce message de notification précédemment envoyé.  

## <a name="send-a-custom-notification"></a>Envoyer une notification personnalisée  

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) avec un compte disposant des autorisations nécessaires pour créer et envoyer des notifications, puis accédez à **Appareils** > **Envoyer des notifications personnalisées**.  

2. Dans l’onglet De base, spécifiez les éléments suivants, puis sélectionnez **Suivant** pour continuer.  
   - **Titre** : Spécifiez un titre pour cette notification. Les titres sont limités à 50 caractères.  
   - **Corps** : Spécifiez le message. Les messages sont limités à 500 caractères.

   ![Créer une notification personnalisée](./media/custom-notifications/custom-notifications.png)  

3. Sous l’onglet **Affectations**, sélectionnez les groupes auxquels vous voulez envoyer cette notification personnalisée, puis sélectionnez Suivant pour continuer.  

4. Sous l’onglet **Vérifier + créer**, passez en revue les informations et, quand vous êtes prêt à envoyer la notification, sélectionnez **Créer**.  

Intune traite immédiatement les messages que vous créez. La seule confirmation indiquant que le message a été envoyé est la notification Intune qui confirme que la notification personnalisée a été envoyée.  

![Confirmation de l’envoi d’une notification](./media/custom-notifications/notification-sent.png)  

Intune ne fait pas le suivi des notifications personnalisées que vous envoyez, et les appareils ne journalisent pas la réception en dehors du centre de notifications de l’appareil.  

## <a name="receive-a-custom-notification"></a>Recevoir une notification personnalisée  

Sur un appareil, les utilisateurs voient les messages de notification personnalisés qui sont envoyés par Intune en tant que notification Push standard provenant de l’application Portail d’entreprise ou de l’application Microsoft Intune. Ces notifications sont similaires aux notifications Push que les utilisateurs reçoivent d’autres applications sur l’appareil.  

Sur les appareils iOS, si l’application Portail d’entreprise est ouverte lors de la réception de la notification, la notification s’affiche dans l’application au lieu d’être une notification Push.  

La notification est conservée jusqu’à ce que l’utilisateur la masque.  

## <a name="next-steps"></a>Étapes suivantes  
[Gérer les appareils](device-management.md)
