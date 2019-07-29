---
title: Points de terminaison réseau pour les déploiements du gouvernement américain - Microsoft Intune
titleSuffix: ''
description: Passez en revue les points de terminaison du gouvernement américain pour Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9828b04ae30d8f35313564b93dfc9b997795bf76
ms.sourcegitcommit: 8d12ab22e23552f9addaef4c28b732fb211945a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68306716"
---
# <a name="us-government-endpoints-for-microsoft-intune"></a>Points de terminaison du gouvernement américain pour Microsoft Intune

Cette page liste les points de terminaison du gouvernement américain nécessaires pour les paramètres de proxy dans vos déploiements Intune.

Pour gérer les appareils qui se trouvent derrière des pare-feu et des serveurs proxy, vous devez activer la communication pour Intune.

- Le serveur proxy doit prendre en charge les protocoles **HTTP (80)** et **HTTPS (443)** , car les clients Intune utilisent ces deux protocoles
- Pour certaines tâches (telles que le téléchargement des mises à jour logicielles), Intune nécessite un accès de serveur proxy non authentifié à manage.microsoft.com

Vous pouvez modifier les paramètres du serveur proxy sur des ordinateurs clients. Vous pouvez également utiliser des paramètres de stratégie de groupe pour modifier les paramètres pour tous les ordinateurs clients situés derrière un serveur proxy spécifié.

Les appareils gérés nécessitent des configurations qui permettent à **Tous les utilisateurs** d’accéder à des services à travers des pare-feu.

Les tableaux suivants répertorient les ports et services auxquels le client Intune accède :

|**Point de terminaison**|**Adresse IP**|
|---------------------|-----------|
|*.manage.microsoft.us | 52.243.26.209 <br> 52.247.173.11 <br> 52.227.183.12 <br>52.227.180.205 <br> 52.227.178.107 <br> 13.72.185.168 <br> 52.227.173.179 <br> 52.227.175.242 <br> 13.72.39.209 <br> 52.243.26.209 <br> 52.247.173.11 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239 <br> 13.72.55.179 |

## <a name="us-government-customer-designated-endpoints"></a>Points de terminaison désignés par les clients du gouvernement américain :
- Portail Azure : https:\//portal.azure.us/ 
- Office 365 : https:\//portal.office365.us/ 
- Portail d’entreprise Intune : https:\//portal.manage.microsoft.us/ 

## <a name="partner-service-endpoints-that-intune-depends-on"></a>Points de terminaison de services partenaires dont dépend Intune :
- Service de synchronisation AAD : https:\//syncservice.gov.us.microsoftonline.com/DirectoryService.svc
- Evo STS : https:\//login.microsoftonline.us
- Proxy d’annuaire : https:\//directoryproxy.microsoftazure.us/DirectoryProxy.svc
- AAD Graph : https:\//directory.microsoftazure.us and https:\//graph.microsoftazure.us
- MS Graph : https:\//graph.microsoft.us
- ADRS : https:\//enterpriseregistration.microsoftonline.us
