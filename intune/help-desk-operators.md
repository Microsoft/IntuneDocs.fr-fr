---
title: "Portail de dépannage du support technique | Microsoft Docs"
titlesuffix: Azure portal
description: "Les équipes du centre de support technique utilisent le portail de dépannage pour résoudre les problèmes techniques des utilisateurs"
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 09/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 845b225fe60ecde71f364b224a0984638662a3db
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>Utilisation du portail de résolution des problèmes pour aider les utilisateurs

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le portail de résolution des problèmes permet aux opérateurs du support technique et aux administrateurs Intune d’afficher les informations utilisateur pour répondre aux demandes d’assistance des utilisateurs. Les organisations qui ont un support technique peuvent affecter **l’opérateur de support technique** à un groupe d’utilisateurs. Le rôle Opérateur de support technique peut utiliser le panneau **Résoudre les problèmes**.

Le panneau **Résolution des problèmes** montre également les problèmes d’inscription des utilisateurs. Des détails sur les problèmes et des suggestions de correction peuvent aider les administrateurs et les agents du support technique à résoudre les problèmes. Certains problèmes d’inscription ne sont pas capturés et certaines erreurs peuvent ne pas avoir de suggestions de correction. 

Pour obtenir la procédure d’ajout d’un rôle Opérateur de support technique, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Intune](/intune/role-based-access-control)

Quand un utilisateur contacte le support technique pour signaler un problème avec Intune, l’opérateur entre le nom de l’utilisateur. Intune affiche des données utiles qui peuvent aider à résoudre de nombreux problèmes de niveau 1, notamment :

- État de l’utilisateur
- Attributions
- Problèmes de conformité
- L’appareil ne répond pas
- L’appareil ne reçoit pas les paramètres VPN ou Wi-Fi
- Échec d’installation de l’application

## <a name="to-review-troubleshooting-details"></a>Pour examiner les informations de résolution des problèmes

Dans le panneau de résolution des problèmes, choisissez **Sélectionner un utilisateur** pour afficher les informations d’un utilisateur. Les informations de l’utilisateur peuvent vous aider à comprendre l’état actuel des utilisateurs et de leurs appareils.  

1. Connectez-vous au portail Azure.
2. Choisissez **Autres services** > **Surveillance + Gestion** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Résoudre les problèmes**.
4. Cliquez sur **Sélectionner un utilisateur**.
5. Sélectionnez un utilisateur en tapant son nom ou son adresse e-mail. Cliquez sur **Sélectionner**. Les informations de résolution des problèmes pour l’utilisateur apparaissent dans le panneau Résolution des problèmes. Les tableaux qui suivent expliquent les informations.

> [!Note]  
> Vous pouvez également accéder au panneau **Résoudre les problèmes** en faisant pointer votre navigateur sur [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Zones du tableau de bord de résolution des problèmes

Vous pouvez utiliser le panneau **Résoudre les problèmes** pour examiner les informations de l’utilisateur. 

![](/intune/media/troubleshooting-dash.png)

| Domaine | Nom | Description |
| ---  | ---  | ---         |
| 1.   | État du compte  | Affiche l’état du locataire Intune actif comme étant **Actif** ou **Inactif**.       |
| 2.   | Sélection de l'utilisateur  | Nom de l’utilisateur actuellement sélectionné. Cliquez sur **Changer d’utilisateur** pour choisir un autre utilisateur.       |
| 3.   | État de l’utilisateur  | Affiche pour cet utilisateur l’état de la licence Intune, le nombre d’appareils, la conformité de chaque appareil, le nombre d’applications et la conformité des applications.       |
| 4.   | Informations utilisateur  | Utilisez la liste pour sélectionner les détails à examiner dans le panneau. <br>Vous pouvez sélectionner : <ul><li>Applications mobiles<li>Stratégies de protection des applications<li>Stratégies de conformité<li> Stratégies de configuration</ul>      |
| 5.   | Appartenance aux groupes  | Yadda       |

## <a name="mobile-apps-reference"></a>Informations de référence sur les applications mobiles

Applications qui s’exécutent sur les appareils, ou les appareils appartenant aux utilisateurs gérés par Intune et Azure Active Directory (AD).

### <a name="properties"></a>Propriétés

Propriétés des applications mobiles.

| Propriété      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nom          | Nom de l’application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Système d’exploitation            | Système d’exploitation installé sur l’appareil.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | Vous pouvez choisir un type d’attribution pour chaque application.  <br> **Disponible** : les utilisateurs effectuent l’installation de l’application à la demande à partir de l’application ou du site web de portail d’entreprise.  <br> **Non applicable** : l’application n’est pas installée ni affichée dans le portail d’entreprise. <br> **Désinstaller** : l’application est désinstallée des appareils dans les groupes sélectionnés.  <br> **Disponible avec ou sans inscription** : affectez cette application à des groupes d’utilisateurs dont les appareils ne sont pas inscrits avec Intune. |
| Dernière modification le | Nom du type d’appareil.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Périphériques

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom de l'appareil        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**.                                               |
| Conforme à Intune   | Nom du type d’appareil.                                                                                                     |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Système d’exploitation                 | Système d’exploitation installé sur l’appareil.                                                                                       |
| Version du système d'exploitation         | Numéro de version du système d’exploitation de l’appareil.                                                                                  |
| Dernier archivage      | Nom du type d’appareil.                                                                                                     |

### <a name="app-protection-status"></a>État de protection des applications

Une stratégie de protection des applications est disponible pour les applications mobiles qui s’intègrent aux technologies Enterprise Mobility Solution (EMS). Ceci donne une base de référence de protection pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

| Propriété    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| État      | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**. |
| Nom de l’application    | Nom de l’application                                                           |
| Nom de l'appareil | Nom du type d’appareil.                                                       |
| Type d'appareil | Nom du type d’appareil.                                                       |
| Stratégies    | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**. |
| Dernière synchronisation   | Horodatage de la dernière synchronisation de l’appareil avec Intune.                   |

## <a name="app-protection-policies-reference"></a>Informations de référence sur les stratégies de protection des applications

Une stratégie de protection des applications est disponible pour les applications mobiles qui s’intègrent aux technologies EMS. Ceci donne une base de référence de protection pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

### <a name="properties"></a>Propriétés

Le tableau récapitule l’état des stratégies de protection des applications pour les appareils gérés par Intune.

| Propriété    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom        | Nom de l’application.                                                                                                        |
| Déployé    | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Plate-forme    | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**.                                               |
| Inscription  | Nom du type d’appareil.                                                                                                     |
| Dernière mise à jour | Horodatage de la modification de la stratégie.                                                                                              |

### <a name="devices"></a>Périphériques

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Texte                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom du périphérique        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**.                                               |
| Conforme à Intune   | Nom du type d’appareil.                                                                                                     |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Système d’exploitation                 | Système d’exploitation installé sur l’appareil.                                                                                       |
| Version du système d'exploitation         | Numéro de version du système d’exploitation de l’appareil.                                                                                  |
| Dernier archivage      | Nom du type d’appareil.                                                                                                     |

## <a name="compliance-policies-reference"></a>Informations de référence sur les stratégies de conformité

Permet de garantir que les appareils utilisés pour accéder aux applications et aux données de l’entreprise sont conformes à certaines règles, comme utiliser un code PIN pour accéder à l’appareil et chiffrer les données qui y sont stockées.

### <a name="properties"></a>Propriétés

Propriétés des stratégies de conformité.

| Propriété      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Affectation    | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Nom          | Nom de l’application.                                                                                                        |
| Système d’exploitation            | Système d’exploitation installé sur l’appareil.                                                                                       |
| Type de stratégie   | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**.                                               |
| Dernière modification le | Nom du type d’appareil.                                                                                                     |

### <a name="devices"></a>Périphériques

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom de l'appareil        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**.                                               |
| Conforme à Intune   | Nom du type d’appareil.                                                                                                     |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Système d’exploitation                 | Système d’exploitation installé sur l’appareil.                                                                                       |
| Version du système d'exploitation         | Numéro de version du système d’exploitation de l’appareil.                                                                                  |
| Dernier archivage      | Nom du type d’appareil.                                                                                                     |

### <a name="app-protection-policies"></a>Stratégies de protection des applications

Une stratégie de protection des applications est disponible pour les applications mobiles qui s’intègrent aux technologies EMS. Ceci donne une base de référence de protection pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

| Propriété    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| État      | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**. |
| Nom de l’application    | Nom de l’application                                                           |
| Nom de l'appareil | Nom du type d’appareil.                                                       |
| Type d'appareil | Nom du type d’appareil.                                                       |
| Stratégies    | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**. |
| Dernière synchronisation   | Horodatage de la dernière synchronisation de l’appareil avec Intune.                   |

## <a name="configuration-policies-reference"></a>Informations de référence sur les stratégies de configuration

Une stratégie de configuration des applications est disponible pour les applications mobiles avec des configurations spécifiques au fournisseur. 

### <a name="properties"></a>Propriétés

Propriétés des stratégies de configuration.

| Propriété      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Affectation    | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Nom          | Nom de l’application.                                                                                                        |
| Système d’exploitation            | Système d’exploitation installé sur l’appareil.                                                                                       |
| Type de stratégie   | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**.                                               |
| Dernière modification le | Nom du type d’appareil.                                                                                                     |

### <a name="devices"></a>Périphériques

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom de l'appareil        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**.                                               |
| Conforme à Intune   | Nom du type d’appareil.                                                                                                     |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Système d’exploitation                 | Système d’exploitation installé sur l’appareil.                                                                                       |
| Version du système d'exploitation         | Numéro de version du système d’exploitation de l’appareil.                                                                                  |
| Dernier archivage      | Nom du type d’appareil.                                                                                                     |


### <a name="app-protection-policies"></a>Stratégies de protection des applications

Une stratégie de protection des applications est disponible pour les applications mobiles qui s’intègrent aux technologies EMS. Ceci donne une base de référence de protection pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

| Propriété    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| État      | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**. |
| Nom de l’application    | Nom de l’application                                                           |
| Nom de l'appareil | Nom du type d’appareil.                                                       |
| Type d'appareil | Nom du type d’appareil.                                                       |
| Stratégies    | Type de propriété des appareils. Les valeurs peuvent être **Entreprise**, **Personnel**, et **Inconnu**. |
| Dernière synchronisation   | Horodatage de la dernière synchronisation de l’appareil avec Intune.                   |

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez découvrir plus d’informations sur le contrôle d’accès en fonction du rôle (RBAC) pour définir des rôles dans les tâches de gestion des appareils et des applications mobiles de votre organisation, et de protection des données. Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Intune](/intune/role-based-access-control).

Découvrez plus d’informations sur les problèmes connus de Microsoft Intune. Pour plus d’informations, consultez [Problèmes connus dans Microsoft Intune](/intune/known-issues).

Découvrez comment créer un ticket de support et obtenir de l’aide quand vous en avez besoin. [Obtenez du support](/intune/get-support).