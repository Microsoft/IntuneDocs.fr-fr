---
title: Collecte des données dans Intune
titleSuffix: Microsoft Intune
description: Découvrez comment les données personnelles sont collectées dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd204271b9ae3e57e15a101647444913749f4109
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514232"
---
# <a name="data-collection-in-intune"></a>Collecte des données dans Intune

Quand les utilisateurs inscrivent leurs appareils personnels ou d’entreprise à l’aide d’Intune, Intune collecte et partage certaines données personnelles. Intune collecte les données personnelles à partir des sources suivantes :

- Utilisation d’Intune par l’administrateur dans le portail Azure.
- Appareils des utilisateurs finaux (quand ils s’inscrivent à la gestion Intune et pendant l’utilisation).
- Comptes client sur des services tiers (comme indiqué dans les instructions de l’administrateur).
- Informations de diagnostic, de performances et d’utilisation.

À partir de ces sources, Intune collecte des informations qui sont réparties dans les trois catégories suivantes : [identifiées](#identified-data), [pseudonymes](#pseudonymized-data) et [agrégées](#aggregated-data).

> [!NOTE]
> Nous ne vendons pas les données collectées par notre service à des tiers pour une raison quelconque.

## <a name="identified-data"></a>Données identifiées

La plupart des données personnelles collectées par Intune sont des données identifiées. Ces données sont liées à un utilisateur, un appareil ou une application, et elles sont essentielles à la nature de la gestion. Les données identifiées sont utilisées pour gérer l’appareil et les applications d’un utilisateur, ainsi que pour provisionner le service Intune.

Les données identifiées collectées par Intune peuvent inclure notamment, mais pas exclusivement, les informations suivantes : 

- Informations sur l'utilisateur
  - Nom de propriétaire/Nom d’affichage de l’utilisateur (nom de l’utilisateur inscrit par Azure, tel qu’identifié par la valeur AzureUserID)
  - Nom principal ou adresse e-mail de l’utilisateur
  - Identificateur d’utilisateur tiers (comme l’ID Apple)
- Informations sur l’inventaire matériel
  - Nom de l’appareil
  - Fabricant
  - Système d'exploitation
  - Numéro de série
  - Numéro IMEI
  - Adresse IP
  - Adresse MAC Wi-Fi
  - ICCID
  - Numéro de téléphone
- Informations du journal d’audit, notamment les données concernant les activités suivantes
  - Gestion
  - Créer
  - Mettre à jour (modifier)
  - Supprimer
  - Affecter
  - Tâches à distance
- Informations concernant le support
  - Informations de contact (nom, numéro de téléphone, adresse e-mail)
  - Discussions par e-mail avec les membres de l’équipe du support technique, de produit et/ou de l’expérience utilisateur Microsoft
- Informations de contrôle d’accès (Intune utilise ces données pour gérer l’accès à des rôles et fonctions d’administration comme le [Contrôle d’accès en fonction du rôle](../fundamentals/role-based-access-control.md))
  - Authentificateurs statiques (mot de passe du client)
  - Clés de confidentialité pour les certificats 
- Informations d’administration et de compte
  - Prénom et nom de l’utilisateur administrateur
  - Nom de l’utilisateur administrateur
  - Nom d’utilisateur principal (e-mail)
  - Numéro de téléphone
  - Adresse e-mail du propriétaire du compte
  - ID Active Directory de chaque administrateur informatique du client
  - Données de paiement pour la facturation au client
  - Clé de l’abonnement
- Inventaire des applications, comme
  - nom de l’application
  - Version
  - ID de l’application
  - est
  - emplacement d’installation
  - Les données de l’inventaire des applications sont collectées uniquement quand elles sont marquées par l’administrateur comme étant un appareil d’entreprise ou que la fonctionnalité d’application compatible est activée.  
- ID de locataires tiers des clients, comme l’ID Apple 

## <a name="pseudonymized-data"></a>Données pseudonymes

Les données pseudonymes sont associées à un identificateur unique, généralement un nombre généré par le système. Ce nombre ne peut pas, à lui seul, identifier une personne spécifique, mais il est utilisé pour fournir les services d’entreprise aux utilisateurs. 

Les données pseudonymes collectées par Intune peuvent inclure notamment, mais pas exclusivement, les informations suivantes : 

- Données de diagnostic, de performances et d’utilisation liées à un utilisateur et/ou un appareil
  - Nombre de fois où une fonctionnalité est utilisée
  - Commandes fournies à la fonctionnalité
  - Temps de réponse d’un service
  - Taux de réussite des installations et d’autres processus
  - Erreurs des applications du portail d’entreprise Intune
  - Identificateurs d’utilisateurs et d’appareils
  - Identificateurs à des fins de référence, de corrélation et de gestion 
- Données d’appareil non liées à un appareil ou à un utilisateur (si ces données sont liées à un appareil ou à un utilisateur, Intune les traite comme des données identifiées)
  - ID d’appareil Intune
  - ID d’appareil Azure Active Directory
  - ID de gestion d’appareils Intune
  - ID de locataire
  - ID de compte
  - ID d’appareil EAS
  - ID spécifique à la plateforme
  - ID Apple pour les appareils iOS/iPadOS
  - Adresse MAC pour appareils Mac
  - ID Windows pour appareils Windows
- Informations d’application managée
  - ID d’application managée
  - Balise d’appareil avec applications managées
  - ID de gestion d’appareils Intune
  - ID d’appareil Azure Active Directory
  - Clés de chiffrement

## <a name="aggregated-data"></a>Données agrégées

Les données agrégées sont utilisées pour provisionner et améliorer le service Intune. 

Les données agrégées collectées par Intune peuvent inclure notamment, mais pas exclusivement, les informations suivantes : 

- Données d’utilisation de l’administrateur provenant de tous les locataires Intune (par exemple, les contrôles d’administration sélectionnés lors de l’interaction avec la console d’administration)
- Informations de compte de locataire (ces données sont disponibles dans le panneau Intune)
  - Nombre d’appareils ou d’utilisateurs inscrits
  - Nombre de plateformes d’appareils identifiées  
  - Nombre d’appareils installés
  - installedDeviceCount : nombre d’appareils sur lesquels l’application est installée.
  - notApplicableDeviceCount : nombre d’appareils pour lesquels l’application n’est pas applicable.
  - notInstalledDeviceCount : nombre d’appareils pour lesquels l’application est applicable mais pas installée.
  - pendingInstallDeviceCount : nombre d’appareils pour lesquels l’application est applicable et l’installation en attente.

## <a name="next-steps"></a>Étapes suivantes

Découvrez des informations supplémentaires sur la façon dont Intune [stocke, traite](privacy-data-store-process.md) et [partage](privacy-data-secure-share.md) les données personnelles. 
