---
title: Auditer, exporter ou supprimer des données personnelles
titleSuffix: Microsoft Intune
description: Découvrez comment auditer, exporter ou supprimer des données personnelles.
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
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cfb0f69d74cc6146b2497cd53be3e123f79cc70
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504358"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Auditer, exporter ou supprimer des données personnelles dans Intune

Les administrateurs Intune peuvent utiliser des journaux d’audit pour effectuer le suivi des activités se rapportant à des données personnelles. Ils peuvent également exporter et supprimer des données personnelles.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Effectuer un audit des données personnelles

Les journaux d’audit indiquent aux administrateurs de locataires les activités qui génèrent un changement dans Intune. Ces journaux sont disponibles pour de nombreuses activités de gestion et généralement pour les actions de création, de mise à jour (modification), de suppression et d’affectation. Les tâches à distance qui génèrent des événements d’audit peuvent également être examinées. Ces journaux d’audit peuvent contenir des données personnelles des utilisateurs dont les appareils sont inscrits dans Intune.  

Pour des raisons de sécurité, Intune peut conserver les journaux d’audit des actions utilisateur et des actions des appareils pendant un an. Ces journaux sont automatiquement supprimés après la période de rétention d’un an.

Pour consulter les journaux d’audit, consultez [Journaux d’audit pour les activités Intune](../fundamentals/monitor-audit-logs.md). 

Les administrateurs ne peuvent pas supprimer les journaux d’audit.

Ces événements d’audit sont conservés pendant un an. Les administrateurs de locataires peuvent demander des journaux d’audit à l’aide de [ce formulaire de demande de support](https://privacy.microsoft.com/en-US/privacy-questions?).

## <a name="export-personal-data"></a>Exporter les données personnelles

Les administrateurs peuvent exporter des données personnelles des utilisateurs finaux, notamment les comptes, les données de service et les journaux associés, pour se conformer aux demandes de droits de la personne concernée. Il vous revient, à vous et à votre organisation, de décider de fournir, ou non, les droits de la personne concernée avec une copie des données personnelles ou si vous avez une raison commerciale légitime de ne pas les divulguer. Si vous décidez de les fournir, vous pouvez le faire avec une copie du document réel, une version rédigée de façon appropriée ou une capture d’écran des parties qui vous ont semblé opportun de partager.

Pour exporter les données personnelles d’un utilisateur, vous pouvez utiliser les éléments suivants : 
- Le panneau des appareils MDM Intune pour exporter une liste d’appareils. Vous pouvez également copier directement les données des appareils.
- Le [script Export-IntuneData.ps1](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>Supprimer des données personnelles des utilisateurs finaux

Il existe trois façons de supprimer des données personnelles de la gestion Intune :
- Supprimer l’utilisateur d’Azure Active Directory
- Réinitialiser les paramètres d’usine de l’appareil
- Auto-suppression des utilisateurs

### <a name="delete-a-user-from-intune"></a>Supprimer un utilisateur d’Intune

Pour supprimer les données personnelles de l’utilisateur final d’Intune, un administrateur doit [supprimer l’utilisateur d’Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user). Quand l’utilisateur est supprimé d’AAD (supprimé de manière définitive), Intune reçoit le signal de suppression d’AAD, puis commence automatiquement à purger toutes les données personnelles de cet utilisateur du service Intune. Les informations de l’utilisateur sont supprimées du service Intune dans les 30 jours suivant l’action de suppression.

### <a name="reset-device-to-factory-settings"></a>Réinitialiser les paramètres d’usine de l’appareil
La réinitialisation des paramètres d’usine restaure tous les paramètres et données d’entreprise et personnelles par défaut. Cette option est utile pour fournir un appareil à l’employé suivant. Les fichiers utilisateur, les applications installées par l’utilisateur et les paramètres définis sur des valeurs autres que les valeurs par défaut sont supprimés, et ces données sont supprimées du service Intune dans les 30 jours suivant l’action de suppression.

### <a name="user-self-removal-from-intune-management"></a>Auto-suppression des utilisateurs de la gestion Intune
Les utilisateurs peuvent supprimer leurs appareils personnel [Android, Apple ou Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) de la gestion Intune sans l’assistance d’un administrateur.   

### <a name="retire"></a>Mettre hors service
L’action **Mettre hors service** supprime les données provisionnées par Intune telles que les applications d’entreprise, les données relatives aux applications gérées par Intune, les paramètres de stratégie, ainsi que les profils d’e-mail provisionnés via Intune. Cette action laisse les données personnelles de l’utilisateur sur l’appareil.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Supprimer un locataire de Microsoft Intune

Si un client de locataire Intune annule son compte Intune, toutes les données du locataire sont supprimées dans les 180 jours suivant la fermeture du compte Intune par le client. Si le locataire AAD est associé avec d’autres abonnements d’entreprise Microsoft (Azure, Office 365), seules les données du client Intune sont supprimées. La ressource du locataire AAD est conservée pour être utilisées par les autres abonnements. Si le compte Intune est le seul abonnement associé au locataire AAD, ce dernier est supprimé, de même que toutes les ressources et données client.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Supprimer un utilisateur dans un environnement de gestion des appareils mobiles (MDM) hybride
Quand vous avez un environnement MDM hybride (Intune intégré à Configuration Manager), vous devez effectuer les actions suivantes (dans l’ordre) pour supprimer totalement un utilisateur et le retirer complètement de votre annuaire Active Directory local, de Configuration Manager et d’Intune.

1. Supprimez l’utilisateur de votre annuaire Active Directory local (AD). Cela empêche la synchronisation de l’utilisateur avec Azure AD, ainsi que sa détection par la découverte de Configuration Manager. 
2. Supprimez l’utilisateur de la console Configuration Manager pour supprimer les données utilisateur et les données associées de Configuration Manager. Dans la console, accédez à **Biens et conformité** > **Utilisateurs**, cliquez avec le bouton droit sur l’utilisateur à supprimer, puis cliquez sur **Supprimer**.
3. [Supprimez l’utilisateur d’AAD](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user), ce qui supprime l’utilisateur et les données associées simultanément d’Azure Active Directory et d’Intune. Quand l’utilisateur est supprimé d’AAD (supprimé de manière définitive), Intune reçoit le signal de suppression d’AAD, puis commence automatiquement à purger toutes les données personnelles de cet utilisateur du service Intune. Les informations de l’utilisateur sont supprimées du service Intune dans les 30 jours suivant l’action de suppression.

> [!Important]
>L’intégration des nouveaux clients MDM hybrides est dépréciée. Pour plus d’informations, lisez le billet de blog [Passer de la gestion hybride des appareils mobiles à Intune sur Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [auditer, exporter ou supprimer](privacy-data-audit-export-delete.md) des données personnelles dans Intune.
