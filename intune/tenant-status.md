---
title: Page État du locataire Microsoft Intune
titleSuffix: Microsoft Intune
description: La page État du locataire Intune permet de voir les détails importants sur le locataire sans quitter le portail Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8bdb74c19e6b996bafc9284bfedaf0608fdf8fb
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834617"
---
# <a name="intune-tenant-status-page"></a>Page État du locataire Intune
Utilisez la page État du locataire comme un hub centralisé pour rester au fait des informations importantes sur votre locataire, la disponibilité et l’utilisation des licences, l’état du connecteur et les communications importantes sur le service Intune.  

Pour voir le tableau de bord, dans le portail Azure, accédez à **Intune > État du locataire**.  La page État du locataire s’affiche sous le **groupe Aide et support**.  

La page est divisée en quatre zones :

## <a name="tenant-details"></a>Détails du locataire
La zone Détails du locataire fournit des informations instantanées sur votre locataire. Affichez des détails tels que le nom et l’emplacement de votre locataire, votre autorité MDM et le numéro de version de service de votre locataire. Le numéro de version de service est un lien qui ouvre l’article *Nouveautés d’Intune* sur Microsoft Docs, où vous pouvez découvrir les dernières fonctionnalités et mises à jour du service Intune.  

Cette section fournit également des informations de base sur vos licences disponibles et le nombre affecté aux utilisateurs. Les licences pour les appareils ne sont pas affichées.

## <a name="connector-status"></a>État du connecteur
La zone État du connecteur est un emplacement unique pour consulter l’état de tous les connecteurs disponibles pour Intune.  

Les connecteurs sont :
- **Des connexions à des services externes que vous configurez**. Citons, par exemple, le service *Programme d’achats en volume (VPP) Apple* ou le service *Windows Autopilot*.  L’état pour ce type de connecteur est basé sur l’heure de la dernière synchronisation réussie.
- **Certificats ou informations d’identification nécessaires pour se connecter à un service non managé externe**, comme les certificats APNS *Apple Push Notification Services*. L’état pour ce type de connecteur est basé sur l’horodatage d’expiration du certificat ou des informations d’identification.  

Par défaut, seuls cinq connecteurs s’affichent. Vous pouvez sélectionner **Voir tous les connecteurs** pour développer cette liste afin d’afficher tous les connecteurs disponibles, notamment ceux que vous n’avez pas configurés pour être utilisés.  

Quand il existe plusieurs connecteurs d’un type donné, l’état est un résumé pour tous ces connecteurs identiques. L’état le moins sain de n’importe quel connecteur est utilisé comme état d’intégrité pour le groupe.  

Les connecteurs non sains s’affichent toujours en haut de la liste. Suivent les connecteurs avec des avertissements, puis la liste des connecteurs sains. Les connecteurs que vous n’avez pas encore configurés apparaissent en dernier.

**État du connecteur :**
- **Non sain :**
    - Le certificat ou les informations d’identification ont expiré
    - La dernière synchronisation remonte à au moins trois jours
- **Avertissement :**
    - Le certificat ou les informations d’identification expirent dans les 7 jours
    - La dernière synchronisation remonte à plus d’une journée
- **Sain :**
    - Le certificat ou les informations d’identification ne vont pas expirer dans les sept prochains jours
    - La dernière synchronisation remonte à moins d’une journée  

Quand vous sélectionnez un connecteur dans la liste, le portail affiche la page qui se rapporte à la création ou la configuration de ce connecteur.  Par exemple, lorsque vous sélectionnez le connecteur **Date d’expiration de VPP**, la page **Jetons du programme d’achat en volume iOS**, dans laquelle vous pouvez afficher plus de détails sur ce connecteur, s’ouvre. Vous pouvez ensuite créer une configuration ou modifier une configuration existante et en résoudre les problèmes.  

## <a name="intune-service-health"></a>Intégrité du service Intune  
Vous pouvez afficher des détails sur les conseils et incidents actifs sans avoir à accéder au tableau de bord d’état du service Microsoft 365 ni au Centre de messages, tous deux situés dans le centre d’administration Microsoft 365 à l’adresse https://portal.office.com. Seuls les incidents où un impact sur votre locataire a été observé sont affichés.  

Quand vous sélectionnez un incident, les détails associés sont présentés directement dans la page État du locataire. Pour afficher les anciens conseils et incidents, sélectionnez **Afficher les anciens incidents/conseils**. Le centre d’administration Microsoft 365 s’ouvre et vous pouvez alors afficher les conseils et les incidents des 30 derniers jours pour votre locataire.  

Pour afficher des informations pour *Intégrité du service Intune*, votre compte doit avoir le rôle **Administrateur général** ou **Administrateur de service** dans Azure Active Directory ou le portail d’administration Office. Pour affecter ces autorisations, connectez-vous au [centre d’administration Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) avec les autorisations d’administrateur général. Sélectionnez **Utilisateurs > Utilisateurs actifs**, puis le compte qui nécessite l’accès. Sélectionnez **Modifier** pour les rôles, *Administrateur de service* ou *Administrateur général*, puis **enregistrez** votre modification pour affecter les autorisations.  

Vous pouvez uniquement définir vos préférences de communication pour Intégrité du service Intune via le centre d’administration Microsoft 365.

## <a name="intune-news"></a>Actualités Intune  
Affichez les communications d’information de l’équipe du service Intune sans avoir à accéder au Centre de messages Office. Les communications incluent des messages sur les modifications apportées récemment au service Intune ou qui sont prévues pour votre locataire.  

Par défaut, les 10 derniers messages actifs s’affichent. Pour afficher les messages plus anciens, sélectionnez **Afficher les anciens messages** pour ouvrir le *Centre de messages* dans le portail du centre d’administration Microsoft 365.  

Pour afficher des informations pour Actualités Intune, votre compte doit avoir le rôle **Administrateur général** ou **Administrateur de service** dans Azure Active Directory, ou recevoir le rôle **Lecteur du Centre de messages**  dans le portail d’administration Office.  Pour affecter cette autorisation, connectez-vous au [centre d’administration Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) avec les autorisations d’administrateur. Sélectionnez **Utilisateurs > Utilisateurs actifs**, puis le compte qui nécessite l’accès. Sélectionnez **Modifier** pour *Rôles*, *Administrateur des communications Teams*, puis **enregistrez** votre modification pour affecter les autorisations.  

Vous pouvez uniquement définir vos préférences de communication pour Actualités Intune via le centre d’administration Microsoft 365.
