---
title: Stratégies de configuration pour les applications gérées sans inscription des appareils
titleSuffix: Microsoft Intune
description: Découvrez comment configurer des stratégies de configuration pour les applications gérées sans inscription d’appareil.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
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
ms.openlocfilehash: 4301afca471d0aa56fa1a0826ad7f88bcdf23de2
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414867"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Ajouter des stratégies de configuration pour les applications gérées sans inscription d’appareil

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Vous pouvez utiliser des stratégies de configuration d’applications avec des applications gérées qui prennent en charge le SDK d’application Intune, même sur les appareils qui ne sont pas inscrits. 

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter** > **Applications gérées**.
3. Dans la page **De base**, définissez les informations suivantes :
    - **Nom** : Nom du profil qui s’affiche dans le portail Azure.
    - **Description** : Description du profil qui s’affiche dans le portail Azure.
    - **Type d’inscription de l’appareil** : Les applications gérées sont sélectionnées.
4. Choisissez **Sélectionner les applications publiques** ou **Sélectionner les applications personnalisées** pour choisir l’application que vous allez configurer. Sélectionnez l’application dans la liste d’applications que vous avez approuvées et synchronisées avec Intune.
5. Cliquez sur **Suivant** pour afficher la page **Paramètres**.
6. Pour chaque paramètre de configuration pris en charge par l’application, tapez le **Nom**, puis la **Valeur**. 

   Les applications compatibles avec le SDK d’application Intune prennent en charge les configurations de paires clé-valeur. Pour savoir quelles sont les configurations clé-valeur prises en charge, consultez la documentation de chaque application. Sachez que vous pouvez utiliser des jetons qui seront remplis dynamiquement avec les données générées par l’application. Pour plus d’informations, consultez [Valeurs de configuration pour l’utilisation de jetons](~/apps/app-configuration-policies-managed-app.md#configuration-values-for-using-tokens). Pour plus d’informations sur les paramètres de stratégie de configuration des applications Outlook pour iOS/iPadOS, consultez [Gestion de la configuration des applications Outlook pour iOS/iPadOS avec Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

    Pour supprimer une configuration, choisissez les points de suspension ( **...** ), puis sélectionnez **Supprimer**.  

7. Cliquez sur **Suivant** pour afficher la page **Affectations**.
8. Cliquez sur **Sélectionner les groupes à inclure**.
9. Sélectionnez un groupe dans le volet **Sélectionner les groupes à inclure**, puis cliquez sur **Sélectionner**.
10. Cliquez sur **Sélectionner des groupes à exclure** pour afficher le volet correspondant.
11. Choisissez les groupes à exclure, puis cliquez sur **Sélectionner**.

    >[!NOTE]
    >Quand vous ajoutez un groupe, si un autre groupe a déjà été inclus pour un type d’affectation donnée, il est présélectionné et ne peut pas être affecté à un autre type d’affectation d’inclusion. Par conséquent, ce groupe déjà utilisé ne peut pas être sélectionné comme groupe à exclure.

12. Cliquez sur **Suivant** pour afficher la page **Vérifier + créer**.
13. Cliquez sur **Créer** pour ajouter la stratégie de configuration de l'application à Intune.

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
