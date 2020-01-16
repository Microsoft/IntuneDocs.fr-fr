---
title: Résoudre des restrictions de point d’accès définies dans Intune
description: Examiner les 3 messages courants relatifs aux stratégies de restriction de point d’accès d’Intune et découvrir comment les résoudre
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: eeb47c072a4f34098bdebfd8766ab51b941d0bd3
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75858096"
---
# <a name="resolve-access-point-restrictions"></a>Résoudre des restrictions de point d’accès

Les organisations peuvent restreindre les emplacements à partir desquels les appareils accèdent aux données de l’entreprise.
Pour configurer ces *restrictions de point d’accès*, elles spécifient et définissent des emplacements réseau approuvés.  

Quand vous essayez de vous connecter à un réseau non reconnu ou non approuvé, un ou plusieurs des messages suivants peuvent s’afficher :

* Les restrictions de point d’accès ne sont pas configurées.
* Vous n’êtes pas connecté à un réseau approuvé.
* Une erreur s’est produite et les restrictions de point d’accès n’ont pas pu être appliquées.

 Les tableaux ci-dessous listent chaque message, leur signification et la façon d’accéder à nouveau à vos ressources de travail.

## <a name="access-point-restrictions-not-set-up"></a>Restrictions de point d’accès non configurées  
| Message du portail d’entreprise | Signification de ce message | Ce que vous devez faire                                                               
|------------------------|--------------------------|--------------------------|
| **Les restrictions de point d’accès ne sont pas configurées : les restrictions de point d’accès sont actives et doivent être configurées.** | Votre entreprise a appliqué des restrictions de point d’accès sur votre appareil. Ce paramètre oblige l’application Portail d’entreprise à vérifier certains paramètres réseau sur votre appareil. | Appuyez sur **Résoudre**. L’application Portail d’entreprise vérifie alors que vous êtes connecté à un réseau approuvé par l’entreprise. |

## <a name="not-connected-to-an-approved-network"></a>Non connecté à un réseau approuvé  

| Message du portail d’entreprise | Signification de ce message | Ce que vous devez faire                                                                   
|------------------------|-----------------------------------|--------------------------|
| **L’appareil n’est pas connecté à un réseau approuvé. Connectez-vous à un réseau sans fil approuvé.** | Vous êtes connecté à un réseau qui n’est pas approuvé pour un accès professionnel. Tant que vous êtes connecté à ce réseau, vous ne pouvez pas accéder à la messagerie professionnelle, aux applications de l’entreprise et à d’autres ressources protégées de l’entreprise. | Connectez-vous à un réseau approuvé par l’entreprise. Appuyez ensuite sur **Résoudre** pour réessayer. |

## <a name="restrictions-couldnt-be-enforced"></a>Impossible d’appliquer les restrictions  

| Message du portail d’entreprise | Signification de ce message | Ce que vous devez faire                                                                      
|------------------------|-----------------------------------|--------------------------|
| **Les restrictions de point d’accès n’ont pas pu être appliquées. Le portail d’entreprise a rencontré une erreur.** | Intune ne peut pas déterminer si vous êtes connecté à un réseau approuvé. Cette erreur peut être due à une mauvaise connectivité réseau, à une batterie faible, au mode Économiseur de batterie ou à une erreur du portail d’entreprise. | Veillez à disposer d’une réception réseau forte. Désactivez le mode Économiseur de batterie et vérifiez que votre batterie dispose encore d’au moins 30 %. Appuyez ensuite sur **Résoudre** pour réessayer. 

Encore besoin d’aide ? Nous vous recommandons de contacter le support de votre entreprise. Pour obtenir des informations de contact spécifiques, accédez au [site web Portail d’entreprise](https://portal.manage.microsoft.com/#HelpDeskDialog).
