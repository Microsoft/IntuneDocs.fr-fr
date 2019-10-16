---
title: Stratégies de configuration pour les applications gérées sans inscription des appareils
titleSuffix: Microsoft Intune
description: Découvrez comment configurer des stratégies de configuration pour les applications gérées sans inscription d’appareil.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7716eeb496567eb4e4a35a703b66597ed47e87a6
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725840"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous pouvez utiliser des stratégies de configuration d’applications avec des applications gérées qui prennent en charge le SDK d’application Intune, même sur les appareils qui ne sont pas inscrits. 

> [!NOTE]
> Les applications doivent être ciblées avec la stratégie Intune App Protection afin de recevoir des stratégies de configuration d’applications. Pour plus d’informations sur la création de stratégies Intune App Protection, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md)

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Choisissez la charge de travail **Applications clientes**.
4. Choisissez **Stratégies de configuration des applications** dans le groupe **Gérer**, puis choisissez **Ajouter**.
5. Définissez les détails suivants :
    - **Nom**  
      Nom du profil qui s’affiche dans le portail Azure.
    - **Description**  
      Description du profil qui s’affiche dans le portail Azure.
    - **Type d’inscription de l’appareil**  
      Choisissez **Gérer les applications**.
6. Sélectionnez **Application associée** pour choisir l’application que vous vous apprêtez à configurer. Sélectionnez l’application dans la liste d’applications que vous avez approuvées et synchronisées avec Intune.
7. Pour chaque paramètre de configuration pris en charge par l’application, tapez le **Nom** et la **Valeur**, puis choisissez les points de suspension ( **...** ).  
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