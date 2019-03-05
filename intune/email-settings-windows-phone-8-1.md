---
title: Paramètres de messagerie Microsoft Intune pour Windows Phone 8.1
titleSuffix: ''
description: Découvrez les paramètres Intune que vous pouvez utiliser pour configurer des connexions à la messagerie sur les appareils exécutant Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ec2ccddce5af20fb84ba9ac3a62a57b5566ea81
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231177"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Paramètres de profil de messagerie dans Microsoft Intune pour les appareils exécutant Windows Phone 8.1

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article liste les paramètres de profil de messagerie que vous pouvez configurer pour vos appareils exécutant Windows Phone 8.1.


- **Appliquer tous les paramètres à Windows Phone 8.1 uniquement** : il s’agit d’un paramètre que vous pouvez configurer dans le portail classique Intune. Dans le portail Azure, ce paramètre ne peut pas être modifié. Si la valeur est **Configuré**, les paramètres sont appliqués uniquement aux appareils Windows Phone 8.1. Si la valeur est **Non configuré**, ces paramètres s’appliquent également aux appareils Windows 10 Mobile.
- **Serveur de messagerie** : le nom d’hôte de votre serveur Exchange.
- **Nom du compte** : spécifiez le nom complet du compte de messagerie, tel qu’il apparaît aux utilisateurs sur leurs appareils.
- **Attribut de nom d’utilisateur d’AAD** : il s’agit de l’attribut dans Active Directory (AD) ou Azure AD, qui est utilisé pour générer le nom d’utilisateur de ce profil de messagerie. Sélectionnez **Adresse SMTP principale**, comme **user1@contoso.com** ou **Nom d’utilisateur principal**, comme **user1** ou **user1@contoso.com**.
- **Attribut d’adresse de messagerie d’AAD** : la façon dont l’adresse de messagerie de l’utilisateur est générée sur chaque appareil. Sélectionnez **Adresse SMTP principale** pour utiliser l’adresse SMTP principale pour vous connecter à Exchange ou **Nom d’utilisateur principal** pour utiliser le nom principal complet comme adresse de messagerie.


## <a name="security-settings"></a>Paramètres de sécurité

- **SSL** : utilisez la communication SSL (Secure Sockets Layer) pour envoyer et recevoir des e-mails, et communiquer avec le serveur Exchange.



## <a name="synchronization-settings"></a>Paramètres de synchronisation

- **Nombre d’e-mails à synchroniser** : sélectionnez le nombre de jours de courrier électronique à synchroniser ou sélectionnez **Illimité** pour synchroniser tous les messages disponibles.
- **Planification de la synchronisation** : sélectionnez la planification selon laquelle les appareils vont synchroniser les données à partir du serveur Exchange. Vous pouvez également sélectionner **À mesure que les messages arrivent** pour synchroniser les données dès qu’elles arrivent ou **Manuel** pour que ce soit l’utilisateur de l’appareil qui lance la synchronisation.

## <a name="content-sync-settings"></a>Paramètres de synchronisation du contenu

- **Type de contenu à synchroniser** : sélectionnez les types de contenu à synchroniser avec les appareils :
    - **Contacts**
    - **Calendrier**
    - **Tâches**
