---
title: Page État du locataire Microsoft Intune
titleSuffix: Microsoft Intune
description: La page État du locataire Intune permet de voir les détails importants sur le locataire sans quitter le portail Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 7954a686-25dc-4fce-b395-324816f46d3b
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c79f24d44ad0aed78ed0ae6fce0873a080b2904d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504846"
---
# <a name="use-the-intune-tenant-status-page"></a>Utiliser la page État du locataire Intune
La page État du locataire Microsoft Intune est un hub centralisé où vous pouvez voir les détails actuels et importants sur votre locataire, notamment la disponibilité et l’utilisation des licences, l’état du connecteur ainsi que des communications importantes sur le service Intune.  

Pour afficher le tableau de bord, connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), puis sélectionnez **État du locataire**.  La page *État du locataire* s’affiche sous **Aide et support**.  

La page est divisée en trois onglets :

## <a name="tenant-details"></a>Détails du locataire
La zone Détails du locataire fournit des informations instantanées sur votre locataire. Affichez des détails tels que le nom et l’emplacement de votre locataire, votre autorité MDM et le numéro de version de service de votre locataire. Le numéro de version de service est un lien qui ouvre l’article *Nouveautés d’Intune* sur Microsoft docs. Dans *Nouveautés*, vous pouvez découvrir les dernières fonctionnalités et mises à jour du service Intune.  

Cet onglet fournit des informations de base sur vos licences disponibles et le nombre affecté aux utilisateurs. Les licences pour les appareils ne sont pas affichées.

## <a name="connector-status"></a>État du connecteur
La zone État du connecteur est un emplacement unique pour consulter l’état de tous les connecteurs disponibles pour Intune.  

Les connecteurs sont :
- **Des connexions à des services externes que vous configurez**. Citons, par exemple, le service *Programme d’achats en volume (VPP) Apple* ou le service *Windows Autopilot*.  L’état pour ce type de connecteur est basé sur l’heure de la dernière synchronisation réussie.
- **Certificats ou informations d’identification nécessaires pour se connecter à un service non managé externe**, comme les certificats APNS *Apple Push Notification Services*. L’état pour ce type de connecteur est basé sur l’horodatage d’expiration du certificat ou des informations d’identification.  

Lorsque vous ouvrez l’onglet *État du connecteur*, les connecteurs non intègres s’affichent en haut de la liste. Suivent les connecteurs avec des avertissements, puis la liste des connecteurs sains. Les connecteurs que vous n’avez pas encore configurés apparaissent en dernier avec l’état *Non activé*.

Quand il existe plusieurs connecteurs d’un type donné, l’état est un résumé pour tous ces connecteurs identiques. L’état le moins sain de n’importe quel connecteur est utilisé comme état d’intégrité pour le groupe.  

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

Quand vous sélectionnez un connecteur dans la liste, le portail affiche la page qui se rapporte à ce connecteur. À partir de la page des connecteurs, vous pouvez afficher l’état des connecteurs précédemment configurés ou sélectionner des options pour ajouter ou créer un nouveau connecteur de ce type.

Par exemple, si vous sélectionnez le connecteur **Date d’expiration de VPP**, la page **Jetons du programme d’achat en volume iOS**, dans laquelle vous pouvez afficher plus de détails sur ce connecteur, s’ouvre. Vous pouvez aussi créer une configuration ou modifier une configuration existante et en résoudre les problèmes.

## <a name="service-health-dashboard"></a>Tableau de bord État du service  
Dans le tableau de bord État du service, vous pouvez afficher les détails des *incidents de service qui affectent votre locataire, et les* *actualités Intune* qui fournissent des informations sur les mises à jour et les modifications planifiées.

### <a name="intune-service-health"></a>Intégrité du service Intune
Affichez des détails sur les conseils et incidents actifs sans avoir à accéder au tableau de bord d’état du service Microsoft 365 ni au Centre de messages, tous deux situés dans le [centre d’administration Microsoft 365](https://admin.microsoft.com). Seuls les incidents qui affectent votre locataire sont affichés.  

Quand vous sélectionnez un incident, les détails associés sont présentés directement dans la page État du locataire. Pour afficher les anciens conseils et incidents, sélectionnez **Afficher les anciens incidents/conseils**. Le centre d’administration Microsoft 365 s’ouvre et vous pouvez alors afficher les conseils et les incidents des 30 derniers jours pour votre locataire.  

Pour voir des informations pour *Intégrité du service Intune*, votre compte doit avoir le rôle **Administrateur général** ou **Administrateur de service** dans Azure Active Directory ou le centre d’administration Microsoft 365. Pour affecter ces autorisations, connectez-vous au [centre d’administration Microsoft 365](https://admin.microsoft.com) avec les autorisations d’administrateur général. Sélectionnez **Utilisateurs > Utilisateurs actifs**, puis le compte qui nécessite l’accès. Sélectionnez **Modifier** pour les rôles, *Administrateur de service* ou *Administrateur général*, puis **enregistrez** votre modification pour affecter les autorisations.  

Vous pouvez uniquement définir vos préférences de communication pour Intégrité du service Intune via le centre d’administration Microsoft 365.

### <a name="intune-news"></a>Actualités Intune  
Affichez les communications d’information de l’équipe du service Intune sans avoir à accéder au Centre de messages Office. Les communications incluent des messages sur les modifications apportées récemment au service Intune ou qui sont prévues pour votre locataire.  

Par défaut, les 10 messages actifs les plus récents apparaissent. Pour voir les messages plus anciens, sélectionnez **Afficher les anciens messages** pour ouvrir le *Centre de messages* dans le centre d’administration Microsoft 365.  

Pour voir des informations pour Actualités Intune, votre compte doit avoir le rôle **Administrateur général** ou **Administrateur de service** dans Azure Active Directory, ou le rôle **Lecteur du Centre de messages** dans le centre d’administration Microsoft 365.  Pour affecter cette autorisation, connectez-vous au [centre d’administration Microsoft 365](https://admin.microsoft.com) avec les autorisations d’administrateur. Sélectionnez **Utilisateurs > Utilisateurs actifs**, puis le compte qui nécessite l’accès. Sélectionnez **Modifier** pour *Rôles*, *Administrateur des communications Teams*, puis **enregistrez** votre modification pour affecter les autorisations.  

Vous pouvez uniquement définir vos préférences de communication pour Actualités Intune via le centre d’administration Microsoft 365.
