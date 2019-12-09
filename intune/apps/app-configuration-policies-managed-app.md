---
title: Stratégies de configuration pour les applications gérées sans inscription des appareils
titleSuffix: Microsoft Intune
description: Découvrez comment configurer des stratégies de configuration pour les applications gérées sans inscription d’appareil.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68032f47be043e8c49b6ad922392d14549293c35
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564288"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous pouvez utiliser des stratégies de configuration d’applications avec des applications gérées qui prennent en charge le SDK d’application Intune, même sur les appareils qui ne sont pas inscrits. 

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter** > **Applications gérées**.
3. Définissez les détails suivants :
    - **Nom**  
      Nom du profil qui s’affiche dans le portail Azure.
    - **Description**  
      Description du profil qui s’affiche dans le portail Azure.
4. Choisissez **Sélectionner les applications publiques** ou **Sélectionner les applications personnalisées** pour choisir l’application que vous allez configurer. Sélectionnez l’application dans la liste d’applications que vous avez approuvées et synchronisées avec Intune.
5. Pour chaque paramètre de configuration pris en charge par l’application, tapez le **Nom**, puis la **Valeur**.  
    Pour supprimer une configuration, choisissez les points de suspension ( **...** ), puis sélectionnez **Supprimer**.  
    
Les applications compatibles avec le SDK d’application Intune prennent en charge les configurations de paires clé-valeur. Pour savoir quelles sont les configurations clé-valeur prises en charge, consultez la documentation de chaque application. Sachez que vous pouvez utiliser des jetons qui seront remplis dynamiquement avec les données générées par l’application. Pour plus d’informations sur les paramètres de stratégie de configuration de l’application Outlook pour iOS, consultez la section [Gérer Outlook pour la configuration d’applications iOS avec Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

## <a name="configuration-values-for-using-tokens"></a>Valeurs de configuration pour l’utilisation de jetons

Intune peut générer certains jetons et les envoyer à l’application gérée. Par exemple, si la configuration de votre application peut utiliser un paramètre d’e-mail, vous pouvez ajouter un e-mail dynamique à l’aide d’un jeton. Tapez le nom attendu par l’application dans le champ **Nom**, puis `\{\{mail\}\}` dans le champ **Valeur**.

Intune prend en charge les types de jetons suivants dans les paramètres de configuration. Aucune autre paire clé-valeur personnalisée n’est prise en charge.

- \{\{userprincipalname\}\} : par exemple, John@contoso.com
- \{\{mail\}\} : par exemple, John@contoso.com
- \{\{partialupn\}\} : par exemple, John
- \{\{accountid\}\} : par exemple, fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\} : par exemple, 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} : par exemple, John Doe
- \{\{PrimarySMTPAddress\}\} : par exemple, testuser@ad.domain.com


> [!Note]  
> Les caractères \{\{ et \}\} sont utilisés uniquement par les types de jetons. Ils ne doivent pas être utilisés à d’autres fins.

## <a name="next-steps"></a>Étapes suivantes

Continuez à [affecter](apps-deploy.md) et à [surveiller](apps-monitor.md) l’application comme d’habitude.
