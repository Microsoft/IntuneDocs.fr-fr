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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f6682cb-5fcd-4018-b7f7-71768ad3152e
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d876c0268f38a09ea3729a7e19ee00b321ae897a
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000395"
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

## <a name="windows-push-notification-services"></a>Services de notifications Push Windows
Sur les appareils gérés par Intune à l’aide de la gestion des appareils mobiles (MDM), les Services de notifications Push Windows (WNS) sont requis pour les actions des appareils et d’autres activités immédiates. Pour plus d’informations, consultez [Pare-feu d’entreprise et configurations de proxy pour prendre en charge le trafic WNS](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config).

## <a name="apple-device-network-information"></a>Informations réseau de l’appareil Apple

|**Utilisé pour**|**Nom d’hôte (adresse IP/sous-réseau)**|**Protocole**|**Port**|
|------------|-----------|------------|-----------|
|Récupération et affichage de contenu de serveurs Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br>\*.phobos.itunes-apple.com.akadns.net|HTTP|80|
|Communication avec des serveurs APNS|#-courier.push.apple.com<br>« # » est un nombre aléatoire compris entre 0 et 50.|TCP|5223 et 443|
|Diverses fonctions, dont l’accès à Internet, iTunes Store, macOS App Store, iCloud, la messagerie, etc.|phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net|HTTP/HTTPS|80 ou 443|

Pour plus d'informations, voir :

- [Ports TCP et UDP utilisés par les produits logiciels Apple](https://support.apple.com/HT202944)
- [À propos des connexions de macOS, iOS et iTunes aux serveurs hôtes et des processus exécutés en arrière-plan par iTunes](https://support.apple.com/HT201999)
- [Si vos clients macOS et iOS ne reçoivent pas les notifications Push Apple](https://support.apple.com/HT203609)

## <a name="next-steps"></a>Étapes suivantes
[Points de terminaison réseau pour Microsoft Intune](intune-endpoints.md)

[Inscription d’appareil et inscription automatique Windows 10](../enrollment/windows-enroll.md#registration-and-enrollment-cnames)