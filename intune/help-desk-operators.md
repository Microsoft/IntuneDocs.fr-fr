---
title: Portail de dépannage du centre de support technique
titlesuffix: Microsoft Intune
description: Les équipes de support technique utilisent le portail de résolution des problèmes pour résoudre les problèmes techniques des utilisateurs.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 90756da72ecdcbd049b14b45014433bb5843a5ed
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236660"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Utiliser le portail de résolution des problèmes pour aider les utilisateurs dans votre entreprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le portail de résolution des problèmes permet aux opérateurs du support technique et aux administrateurs Intune d’afficher les informations utilisateur pour répondre aux demandes d’assistance des utilisateurs. Les organisations qui ont un support technique peuvent affecter **l’opérateur de support technique** à un groupe d’utilisateurs. Le rôle Opérateur de support technique peut utiliser le volet **Dépanner**.

Le volet **Dépanner** affiche également les problèmes d’inscription des utilisateurs. Des détails sur les problèmes et des suggestions de correction peuvent aider les administrateurs et les agents du support technique à résoudre les problèmes. Certains problèmes d’inscription ne sont pas capturés et certaines erreurs peuvent ne pas avoir de suggestions de correction.

Pour obtenir la procédure d’ajout d’un rôle Opérateur de support technique, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Intune](/intune/role-based-access-control)

Quand un utilisateur contacte le support technique pour signaler un problème avec Intune, l’opérateur entre le nom de l’utilisateur. Intune affiche des données utiles qui peuvent aider à résoudre de nombreux problèmes de niveau 1, notamment :

- État de l’utilisateur
- Attributions
- Problèmes de conformité
- L’appareil ne répond pas
- L’appareil ne reçoit pas les paramètres VPN ou Wi-Fi
- Échec d’installation de l’application

## <a name="to-review-troubleshooting-details"></a>Pour examiner les informations de résolution des problèmes

Dans le volet de dépannage, choisissez **Sélectionner un utilisateur** pour afficher les informations d’un utilisateur. Les informations de l’utilisateur peuvent vous aider à comprendre l’état actuel des utilisateurs et de leurs appareils.  

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Dépanner**.
4. Cliquez sur **Sélectionnez** pour sélectionner un utilisateur à dépanner.
5. Sélectionnez un utilisateur en tapant son nom ou son adresse e-mail. Cliquez sur **Sélectionner**. Les informations sur le dépannage pour l’utilisateur s’affichent dans le volet Dépannage. Le tableau suivant explique les informations.

> [!Note]  
> Vous pouvez également accéder au volet **Dépannage** en pointant votre navigateur sur [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Zones du tableau de bord de résolution des problèmes

Vous pouvez utiliser le volet **Dépanner** pour consulter les informations de l’utilisateur.

![](/intune/media/troubleshooting-dash.png)

| Domaine | Nom | Description |
| ---  | ---  | ---         |
| 1.   | État du compte  | Affiche l’état du locataire Intune actif comme étant **Actif** ou **Inactif**.       |
| 2.   | Sélection de l'utilisateur  | Nom de l’utilisateur actuellement sélectionné. Cliquez sur **Changer d’utilisateur** pour choisir un autre utilisateur.       |
| 3.   | État de l’utilisateur  | Affiche pour cet utilisateur l’état de la licence Intune, le nombre d’appareils, la conformité de chaque appareil, le nombre d’applications et la conformité des applications.       |
| 4.   | Informations utilisateur  | Utilisez la liste pour sélectionner les détails à consulter dans le volet. <br>Vous pouvez sélectionner : <ul><li>Applications clientes<li>Stratégies de conformité<li> Stratégies de configuration<li>Stratégies de protection des applications <li>Restrictions d’inscription</ul>      |
| 5.   | Appartenance aux groupes  | Affiche les groupes dont l’utilisateur sélectionné est membre.       |

## <a name="client-apps-reference"></a>Informations de référence sur les applications clientes

Applications qui exécutent des appareils
- Gérés par Intune et Azure Active Directory (AD) 
- Appartenant à des utilisateurs et gérés par Intune et Azure Active Directory (AD)

### <a name="properties"></a>Propriétés

Propriétés des applications clientes.

| Propriété      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nom          | Nom de l’application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Système d’exploitation            | Système d’exploitation installé sur l’appareil.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | Vous pouvez choisir un type d’attribution pour chaque application.  <br> **Disponible** : les utilisateurs effectuent l’installation de l’application à la demande à partir de l’application ou du site web de portail d’entreprise.  <br> **Non applicable** : l’application n’est pas installée ni affichée dans le portail d’entreprise. <br> **Désinstaller** : l’application est désinstallée des appareils dans les groupes sélectionnés.  <br> **Disponible avec ou sans inscription** : affectez cette application à des groupes d’utilisateurs dont les appareils ne sont pas inscrits avec Intune. |
| Dernière modification le | Nom du type d’appareil.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Appareils

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom de l'appareil        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**).                                               |
| Conforme à Intune   | Nom du type d’appareil.                                                                                                     |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Installation de l’application | Indique si l’installation d’une application a échoué ou réussi sur l’appareil individuel. |
| Système d’exploitation                 | Système d’exploitation installé sur l’appareil.                                                                                       |
| Version du système d'exploitation         | Numéro de version du système d’exploitation de l’appareil.                                                                                  |
| Dernier archivage      | Nom du type d’appareil.                                                                                                     |

### <a name="app-protection-status"></a>État de protection des applications

Une stratégie de protection des applications est disponible pour les applications mobiles qui s’intègrent aux technologies Enterprise Mobility Solution (EMS). Ces stratégies fournissent une base de référence de protection pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

| Propriété    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| État      | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**). |
| Nom de l’application    | Nom de l’application                                                           |
| Nom de l'appareil | Nom du type d’appareil.                                                       |
| Type d'appareil | Nom du type d’appareil.                                                       |
| Stratégies    | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**). |
| Dernière synchronisation   | Horodatage de la dernière synchronisation de l’appareil avec Intune.                   |

## <a name="app-protection-policies-reference"></a>Informations de référence sur les stratégies de protection des applications

Une stratégie de protection d’application est disponible pour les applications mobiles qui s’intègrent aux technologies EMS. Ces stratégies fournissent une protection de base de référence pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

### <a name="properties"></a>Propriétés

Le tableau récapitule l’état des stratégies de protection des applications pour les appareils gérés par Intune.

| Propriété    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom        | Nom de l’application.                                                                                                        |
| Déployé    | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Plate-forme    | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**).                                               |
| Inscription  | Nom du type d’appareil.                                                                                                     |
| Dernière mise à jour | Horodatage de la modification de la stratégie.                                                                                              |

### <a name="devices"></a>Appareils

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom du périphérique        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**).                                               |
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
| Type de stratégie   | Type de propriété des appareils (**Société**, **Personnel** et **Inconnu**).                                               |
| Dernière modification le | Nom du type d’appareil.                                                                                                     |

### <a name="devices"></a>Appareils

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom de l'appareil        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils (**Société**, **Personnel** et **Inconnu**).                                               |
| Conforme à Intune   | Nom du type d’appareil.                                                                                                     |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Système d’exploitation                 | Système d’exploitation installé sur l’appareil.                                                                                       |
| Version du système d'exploitation         | Numéro de version du système d’exploitation de l’appareil.                                                                                  |
| Dernier archivage      | Nom du type d’appareil.                                                                                                     |

### <a name="app-protection-policies"></a>Stratégies de protection des applications

Une stratégie de protection des applications est disponible pour les applications mobiles qui s’intègrent aux technologies EMS. Ces stratégies fournissent une base de référence de protection pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

| Propriété    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| État      | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**). |
| Nom de l’application    | Nom de l’application                                                           |
| Nom de l'appareil | Nom du type d’appareil.                                                       |
| Type d'appareil | Nom du type d’appareil.                                                       |
| Stratégies    | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**). |
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
| Type de stratégie   | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**).                                               |
| Dernière modification le | Nom du type d’appareil.                                                                                                     |

### <a name="devices"></a>Appareils

Appareils gérés par Intune, ou par les utilisateurs gérés par Intune ou Azure AD.

| Propriété           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nom de l'appareil        | Nom du type d’appareil.                                                                                                     |
| Géré par         | Horodatage de la modification de la stratégie.                                                                                              |
| Type de jonction à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Propriété          | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**).                                               |
| Conforme à Intune   | Nom du type d’appareil.                                                                                                     |
| Conforme à Azure AD | L’état de chacune des applications de protection d’application des utilisateurs. Les états possibles des applications sont **Archivé** et **Non archivé**. |
| Système d’exploitation                 | Système d’exploitation installé sur l’appareil.                                                                                       |
| Version du système d'exploitation         | Numéro de version du système d’exploitation de l’appareil.                                                                                  |
| Dernier archivage      | Nom du type d’appareil.                                                                                                     |


### <a name="app-protection-policies"></a>Stratégies de protection des applications

Une stratégie de protection des applications est disponible pour les applications mobiles qui s’intègrent aux technologies EMS. Ces stratégies fournissent une base de référence de protection pour vos données d’entreprise quand elles sont téléchargées vers des applications mobiles, notamment les applications mobiles Office. 

| Propriété    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| État      | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**). |
| Nom de l’application    | Nom de l’application                                                           |
| Nom de l'appareil | Nom du type d’appareil.                                                       |
| Type d'appareil | Nom du type d’appareil.                                                       |
| Stratégies    | Type de propriété des appareils (**Société**, **Personnel** ou **Inconnu**). |
| Dernière synchronisation   | Horodatage de la dernière synchronisation de l’appareil avec Intune.                   |

## <a name="enrollment-failure-reference"></a>Informations de référence sur les échecs d’inscription

Le tableau Erreurs d’inscription liste les tentatives d’inscription qui n’ont pas pu s’effectuer correctement. Un appareil listé dans le tableau ci-dessous peut réussir à s’inscrire par la suite au cours d’une nouvelle tentative. Certaines tentatives infructueuses ne sont peut-être pas listées. Les informations d’atténuation ne sont pas disponibles pour tous les échecs.

| Colonne de tableau | Description |
|-------------|----------|
| Début de l’inscription | Heure de début de l’inscription effectuée pour la première fois par l’utilisateur. |
| Système d’exploitation | Système d’exploitation de l’appareil. |
| Version du système d'exploitation | Version du système d’exploitation de l’appareil. |
| Échec | Cause de l’échec. |

### <a name="failure-details"></a>Détails de l’échec

Quand vous choisissez une ligne d’échec, des détails supplémentaires sont fournis.

| Section | Description |
|-------------|----------|
| Détails de l’échec | Explication plus détaillée de l’échec. |
| Corrections potentielles | Étapes suggérées pour résoudre l’erreur. Il est possible que certains échecs ne puissent pas être corrigés. |
| Ressources (facultatif) | Liens vers de la documentation supplémentaires ou vers des zones du portail permettant d’entreprendre des actions. |

### <a name="enrollment-errors"></a>Erreurs d’inscription

| Erreur | Détails |
|-------------|----------|
| Délai d’expiration ou échec d’iOS | Expiration du délai d’attente entre l’appareil et Intune en raison de la lenteur de l’utilisateur à effectuer l’inscription. |
| Utilisateur introuvable ou avec licence | Il manque une licence à l’utilisateur, ou celle-ci a été supprimée du service. |
| Appareil déjà inscrit | Une personne a tenté d’inscrire un appareil à l’aide du Portail d’entreprise sur un appareil encore inscrit par un autre utilisateur. |
| Non intégré à Intune | Une inscription a été tentée alors que l’autorité MDM (Gestion des appareils mobiles) Intune n’était pas configurée. |
| Échec de l’autorisation d’inscription | Une inscription a été tentée à l’aide d’une ancienne version du Portail d’entreprise. |
| Appareil non pris en charge | L’appareil ne répond pas aux exigences minimales de l’inscription à Intune. |
| Restrictions d’inscription non respectées | Cette inscription a été bloquée en raison d’une restriction d’inscription, configurée par un administrateur. |
| Plafond d’appareils atteint | Cette inscription a été bloquée en raison d’une restriction du nombre limite d’appareils, configurée par un administrateur. |
| Intégration d’Apple | L’inscription de tous les appareils iOS a été bloquée pour le moment en raison de l’absence ou de l’expiration d’un certificat Push MDM Apple dans Intune. |
| Appareil non préinscrit | L’appareil n’a pas été préinscrit en tant qu’appareil de société, et toutes les inscriptions personnelles ont été bloquées par un administrateur. |
| Fonctionnalité non prise en charge | L’utilisateur a probablement tenté de s’inscrire via une méthode non compatible avec votre configuration d’Intune. |

## <a name="collect-available-data-from-mobile-device"></a>Collecter les données disponibles à partir d’un appareil mobile

Utilisez les ressources suivantes pour collecter les données d’un appareil lors de la résolution des problèmes de l’appareil de l’utilisateur :
  - [Envoyer les erreurs d’inscription iOS à votre administrateur informatique](/intune-user-help/send-errors-to-your-it-admin-ios)
  - [Aider le support technique de votre entreprise à résoudre les problèmes de l’appareil grâce à la journalisation détaillée](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)
  - [Envoyer des journaux Android au support technique de votre entreprise via un câble USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Envoyer les journaux de données de diagnostic Android à votre administrateur informatique par e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
  - [Envoyer les erreurs d’inscription Android à votre administrateur informatique](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez découvrir plus d’informations sur le contrôle d’accès en fonction du rôle (RBAC) pour définir des rôles dans les tâches de gestion des appareils et des applications mobiles de votre organisation, et de protection des données. Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Intune](/intune/role-based-access-control).

Découvrez plus d’informations sur les problèmes connus de Microsoft Intune. Pour plus d’informations, consultez [Problèmes connus dans Microsoft Intune](/intune/known-issues).

Découvrez comment créer un ticket de support et obtenir de l’aide quand vous en avez besoin. [Obtenez du support](/intune/get-support).
