---
title: Portail de dépannage du centre de support technique
titleSuffix: Microsoft Intune
description: Les équipes de support technique utilisent le portail de résolution des problèmes pour résoudre les problèmes techniques des utilisateurs.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0094cdd12b2594cb60260d768daec8c5bed04c9c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510256"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Utiliser le portail de résolution des problèmes pour aider les utilisateurs dans votre entreprise

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

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

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, choisissez **Dépanner**.
4. Cliquez sur **Sélectionnez** pour sélectionner un utilisateur à dépanner.
5. Sélectionnez un utilisateur en tapant son nom ou son adresse e-mail. Cliquez sur **Sélectionner**. Les informations sur le dépannage pour l’utilisateur s’affichent dans le volet Dépannage. Le tableau suivant explique les informations.

> [!Note]  
> Vous pouvez également accéder au volet **Dépannage** en pointant votre navigateur sur [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Zones du tableau de bord de résolution des problèmes

Vous pouvez utiliser le volet **Dépanner** pour consulter les informations de l’utilisateur.

![Tableau de bord de dépannage, avec les zones numérotées décrites dans le tableau suivant](./media/help-desk-operators/troubleshooting-dash.png)

| Domaine | Nom | Description |
| ---  | ---  | ---         |
| 1.   | État du compte  | Affiche l’état du locataire Intune actif comme étant **Actif** ou **Inactif**.       |
| 2.   | Sélection de l'utilisateur  | Nom de l’utilisateur actuellement sélectionné. Cliquez sur **Changer d’utilisateur** pour choisir un autre utilisateur.       |
| 3.   | État de l’utilisateur  | Affiche pour cet utilisateur l’état de la licence Intune, le nombre d’appareils, la conformité de chaque appareil, le nombre d’applications et la conformité des applications.       |
| 4.   | Informations sur l'utilisateur  | Utilisez la liste pour sélectionner les détails à consulter dans le volet. <br>Vous pouvez sélectionner : <ul><li>Applications clientes<li>Stratégies de conformité<li> Stratégies de configuration<li>Stratégies de protection des applications <li>Restrictions d’inscription</ul>      |
| 5.   | Appartenance aux groupes  | Affiche les groupes dont l’utilisateur sélectionné est membre.       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

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
| Version d’appareil trop basse | L’administrateur a configuré une restriction d’inscription nécessitant une version plus élevée de l’appareil. |
| Version d’appareil trop élevée | L’administrateur a configuré une restriction d’inscription nécessitant une version plus basse de l’appareil. |
| L’appareil ne peut pas être inscrit comme appareil personnel | L’administrateur a configuré une restriction d’inscription afin de bloquer les inscriptions personnelles, et l’appareil défaillant n’a pas été prédéfini en tant qu’appareil d’entreprise. |
| Plateforme d’appareil bloquée | L’administrateur a configuré une restriction d’inscription qui bloque la plateforme de cet appareil. |
| Expiration du jeton en bloc | Le jeton en bloc dans le package de provisionnement a expiré. |
| Appareil Autopilot ou détails introuvables | L’appareil Autopilot n’a pas été trouvé lors de la tentative d’inscription. |
| Profil Autopilot introuvable ou non affecté | L’appareil n’a pas de profil Autopilot actif. |
| Méthode d’inscription Autopilot inattendue | L’appareil a tenté de s’inscrire à l’aide d’une méthode non autorisée. |
| Appareil Autopilot supprimé | L’appareil tentant de s’inscrire a été supprimé d’Autopilot pour ce compte. |
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
