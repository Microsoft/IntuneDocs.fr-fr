---
title: Points de terminaison réseau pour Microsoft Intune
titleSuffix: ''
description: Passez en revue les points de terminaison pour Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/22/2019
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
ms.openlocfilehash: b836e754b8c08397fccb0c74b40ba9fe0675076e
ms.sourcegitcommit: 97a46f0f6a27eda0592ff6518fac46bc2447b622
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68411589"
---
# <a name="network-endpoints-for-microsoft-intune"></a>Points de terminaison réseau pour Microsoft Intune  

Cette page liste les adresses IP et les paramètres de port nécessaires pour les paramètres de proxy dans vos déploiements Intune.

En tant que service cloud uniquement, Intune ne nécessite pas d’infrastructure sur site telle que des serveurs ou des passerelles.

## <a name="access-for-managed-devices"></a>Accès pour les appareils gérés  

Pour gérer les appareils qui se trouvent derrière des pare-feu et des serveurs proxy, vous devez activer la communication pour Intune.

- Le serveur proxy doit prendre en charge les protocoles **HTTP (80)** et **HTTPS (443)** , car les clients Intune les utilisent tous les deux. La Protection des informations Windows utilise le port 444.
- Pour certaines tâches (telles que le téléchargement des mises à jour logicielles pour l’agent de PC classique), Intune nécessite un accès de serveur proxy non authentifié à manage.microsoft.com

Vous pouvez modifier les paramètres du serveur proxy sur des ordinateurs clients. Vous pouvez également utiliser des paramètres de stratégie de groupe pour modifier les paramètres pour tous les ordinateurs clients situés derrière un serveur proxy spécifié.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Les appareils gérés nécessitent des configurations qui permettent à **Tous les utilisateurs** d’accéder à des services à travers des pare-feu.

Les tableaux suivants répertorient les ports et services auxquels le client Intune accède :

|Domains    |Adresse IP      |
|-----------|----------------|
|login.microsoftonline.com | Plus d’informations [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|

## <a name="network-requirements-for-powershell-scripts-and-win32-apps"></a>Configuration réseau requise pour les scripts PowerShell et les applications Win32  

Si vous utilisez Intune pour déployer des scripts PowerShell ou des applications Win32, vous devez également accorder l’accès aux points de terminaison où votre locataire se trouve actuellement.

|ASU | Nom de stockage | CDN |
| --- | --- |--- |
| AMSUA0601 | prodmsua06data | https:\//prodmsua06data.azureedge.net |
| AMSUA0602 | prodamsua0602data | https:\//prodamsua0602data.azureedge.net |
| AMSUA0101 | prodmsua01data | https:\//prodmsua01data.azureedge.net |
| AMSUA0201 | prodmsua02data | https:\//prodmsua02data.azureedge.net |
| AMSUA0202 | Prodmsua0202rcdata | https:\//prodamsua0202data.azureedge.net/ |
| AMSUA0401 | prodmsua04data | https:\//prodmsua04data.azureedge.net |
| AMSUA0402 | Prodmsua0402rcdata | https:\//prodamsua0402data.azureedge.net/ |
| AMSUA0501 | prodmsua05data | https:\//prodmsua05data.azureedge.net |
| AMSUA0502 | prodmsua0502data | https:\//prodmsua0502data.azureedge.net |
| AMSUB0101 | prodmsub01data | https:\//prodmsub01data.azureedge.net |
| AMSUB0102 | prodamsub0102data | https:\//prodamsub0102data.azureedge.net |
| AMSUB0201 | prodmsub02data | https:\//prodmsub02data.azureedge.net |
| AMSUB0202 | Prodmsub0202rcdata | https:\//prodamsub0202data.azureedge.net |
| AMSUB0301 | Prodmsub03data2 | https:\//prodmsub03data2.azureedge.net |
| AMSUB0302 | Prodmsub0302rcdata | https:\//prodamsub0302data.azureedge.net |
| AMSUB0501 | prodmsub05data | https:\//prodmsub05data.azureedge.net |
| AMSUC0101 | prodmsuc01data | https:\//prodmsuc01data.azureedge.net |
| AMSUC0201 | prodmsuc02data | https:\//prodmsuc02data.azureedge.net |
| AMSUC0301 | prodmsuc03data | https:\//prodmsuc03data.azureedge.net |
| AMSUC0501 | prodmsuc05data | https:\//prodmsuc05data.azureedge.net |
| AMSUA0701 | pemsua07rcdata | https:\//pemsua07data.azureedge.net |

## <a name="windows-push-notification-services-wns"></a>Services de notifications Push Windows (WNS)  

Pour les appareils Windows gérés par Intune à l’aide de la gestion des appareils mobiles (MDM), les actions et d’autres activités immédiates exigent l’utilisation des Services de notifications Push Windows (WNS). Pour plus d’informations, consultez [Autorisation du passage du trafic de notification Windows à travers des pare-feu d’entreprise](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config).  

## <a name="delivery-optimization-port-requirements"></a>Configuration requise des ports pour l’optimisation de la distribution  

### <a name="port-requirements"></a>Configuration requise des ports  

Pour le trafic pair à pair, l’optimisation de la distribution utilise le port 7680 pour TCP/IP ou 3544 pour la traversée NAT (éventuellement Teredo). Pour la communication client-service, elle utilise le protocole HTTP ou HTTPS sur le port 80/443.

### <a name="proxy-requirements"></a>Configuration requise du proxy  

Pour utiliser l’optimisation de la distribution, vous devez autoriser les demandes de plage d’octets. Pour plus d’informations, consultez [Configuration requise du proxy pour Windows Update](https://docs.microsoft.com/windows/deployment/update/windows-update-troubleshooting).

### <a name="firewall-requirements"></a>Configuration requise du pare-feu  

Autorisez les noms d’hôte suivants à traverser votre pare-feu pour prendre en charge l’optimisation de la distribution.
Pour la communication entre les clients et le service cloud d’optimisation de la distribution :
- \*.do.dsp.mp.microsoft.com

Pour les métadonnées d’optimisation de la distribution :
- \*.dl.delivery.mp.microsoft.com
- \*.emdl.ws.microsoft.com

## <a name="apple-device-network-information"></a>Informations réseau de l’appareil Apple  

|Utilisé pour|Nom d’hôte (adresse IP/sous-réseau)|Protocole|Port|
|-----|--------|------|-------|
|Récupération et affichage de contenu de serveurs Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Communications avec des serveurs APNS|#-courier.push.apple.com<br>« # » est un nombre aléatoire compris entre 0 et 50.|    TCP     |  5223 et 443  |
|Diverses fonctionnalités telles que l’accès au World Wide Web, iTunes Store, macOS App Store, iCloud, messagerie, etc. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 ou 443   |

Pour plus d’informations, consultez des documents Apple relatifs aux [ports TCP et UDP utilisés par les produits logiciels Apple](https://support.apple.com/en-us/HT202944), aux [connexions hôtes serveurs macOS, iOS et iTunes et processus d’arrière-plan iTunes](https://support.apple.com/en-us/HT201999) et [si vos clients macOS et iOS reçoivent des notifications Push Apple](https://support.apple.com/en-us/HT203609).  

## <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune Certificate Connecavec la valeurr  

Le serveur qui héberge le Microsoft Intune Certificate Connector doit avoir accès via le port **TCP** **443** aux emplacements IP publics listés dans le tableau suivant.  

|Domains                             |Adresse IP       |
|---------------|--------------------------------------|
|Manage.microsoft.com <br> i.manage.microsoft.com <br> r.manage.microsoft.com <br> a.manage.microsoft.com <br> p.manage.microsoft.com <br> EnterpriseEnrollment.manage.microsoft.com <br> EnterpriseEnrollment-s.manage.microsoft.com|13.76.177.110  |
|fef.msua06.manage.microsoft.com  |13.78.185.97  |
|Manage.microsoft.com <br> i.manage.microsoft.com <br> r.manage.microsoft.com <br> a.manage.microsoft.com <br> p.manage.microsoft.com <br> EnterpriseEnrollment.manage.microsoft.com <br> EnterpriseEnrollment-s.manage.microsoft.com |13.82.96.212  |
|fef.amsua0502.manage.microsoft.com |13.85.68.142   |
| portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msuc01.manage.microsoft.com <br> m.fei.msuc01.manage.microsoft.com <br> portal.fei.msuc02.manage.microsoft.com <br> m.fei.msuc02.manage.microsoft.com <br> portal.fei.msuc03.manage.microsoft.com <br> m.fei.msuc03.manage.microsoft.com <br> portal.fei.msuc05.manage.microsoft.com <br> m.fei.msuc05.manage.microsoft.com |20.188.107.228|
|fef.msua04.manage.microsoft.com  |23.96.112.28  |
|fef.amsua0402.manage.microsoft.com|40.69.157.122    |
|Manage.microsoft.com <br> i.manage.microsoft.com <br> r.manage.microsoft.com <br> a.manage.microsoft.com <br> p.manage.microsoft.com <br> EnterpriseEnrollment.manage.microsoft.com <br> EnterpriseEnrollment-s.manage.microsoft.com |40.83.123.72    |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msub01.manage.microsoft.com <br> m.fei.msub01.manage.microsoft.com <br> portal.fei.amsub0102.manage.microsoft.com <br> m.fei.amsub0102.manage.microsoft.com <br> fei.msub02.manage.microsoft.com <br> portal.fei.msub02.manage.microsoft.com <br> m.fei.msub02.manage.microsoft.com <br> portal.fei.msub03.manage.microsoft.com <br> m.fei.msub03.manage.microsoft.com <br> portal.fei.msub05.manage.microsoft.com <br> m.fei.msub05.manage.microsoft.com <br> portal.fei.amsub0202.manage.microsoft.com <br> m.fei.amsub0202.manage.microsoft.com <br> portal.fei.amsub0302.manage.microsoft.com <br> m.fei.amsub0302.manage.microsoft.com |51.144.161.187 |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msub01.manage.microsoft.com <br> m.fei.msub01.manage.microsoft.com <br> portal.fei.amsub0102.manage.microsoft.com <br> m.fei.amsub0102.manage.microsoft.com <br> fei.msub02.manage.microsoft.com <br> portal.fei.msub02.manage.microsoft.com <br> m.fei.msub02.manage.microsoft.com <br> portal.fei.msub03.manage.microsoft.com <br> m.fei.msub03.manage.microsoft.com <br> portal.fei.msub05.manage.microsoft.com <br> m.fei.msub05.manage.microsoft.com <br> portal.fei.amsub0202.manage.microsoft.com <br> m.fei.amsub0202.manage.microsoft.com <br> portal.fei.amsub0302.manage.microsoft.com <br> m.fei.amsub0302.manage.microsoft.com  |52.138.193.149  |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msua01.manage.microsoft.com <br> m.fei.msua01.manage.microsoft.com <br> portal.fei.msua02.manage.microsoft.com <br> m.fei.msua02.manage.microsoft.com <br> portal.fei.msua04.manage.microsoft.com <br> m.fei.msua04.manage.microsoft.com <br> portal.fei.msua05.manage.microsoft.com <br> m.fei.msua05.manage.microsoft.com <br> portal.fei.amsua0502.manage.microsoft.com <br> m.fei.amsua0502.manage.microsoft.com <br> portal.fei.msua06.manage.microsoft.com <br> m.fei.msua06.manage.microsoft.com <br> portal.fei.amsua0602.manage.microsoft.com <br> m.fei.amsua0602.manage.microsoft.com <br> fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0202.manage.microsoft.com <br> m.fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0402.manage.microsoft.com <br> m.fei.amsua0402.manage.microsoft.com |52.160.70.20  |
|fef.amsua0602.manage.microsoft.com |52.161.28.64   |
|fef.amsua0202.manage.microsoft.com |52.165.165.17   |
|portal.manage.microsoft.com <br> m.manage.microsoft.com <br> portal.fei.msua01.manage.microsoft.com <br> m.fei.msua01.manage.microsoft.com <br> portal.fei.msua02.manage.microsoft.com <br> m.fei.msua02.manage.microsoft.com <br> portal.fei.msua04.manage.microsoft.com <br> m.fei.msua04.manage.microsoft.com <br> portal.fei.msua05.manage.microsoft.com <br> m.fei.msua05.manage.microsoft.com <br> portal.fei.amsua0502.manage.microsoft.com <br> m.fei.amsua0502.manage.microsoft.com <br> portal.fei.msua06.manage.microsoft.com <br> m.fei.msua06.manage.microsoft.com <br> portal.fei.amsua0602.manage.microsoft.com <br> m.fei.amsua0602.manage.microsoft.com <br> fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0202.manage.microsoft.com <br> m.fei.amsua0202.manage.microsoft.com <br> portal.fei.amsua0402.manage.microsoft.com <br> m.fei.amsua0402.manage.microsoft.com |52.168.54.64   |
|r.manage.microsoft.com |52.169.9.87    |
|.manage.microsoft.com  |52.174.26.23   |
|portal.fei.msuc01.manage.microsoft.com <br> m.fei.msuc01.manage.microsoft.com <br> portal.fei.msuc02.manage.microsoft.com <br> m.fei.msuc02.manage.microsoft.com <br> portal.fei.msuc03.manage.microsoft.com <br> m.fei.msuc03.manage.microsoft.com <br> portal.fei.msuc05.manage.microsoft.com <br> m.fei.msuc05.manage.microsoft.com |52.175.12.209  |
|fef.msua07.manage.microsoft.com |52.175.208.218     |
|fef.msua02.manage.microsoft.com |52.177.194.236    |
|sts.manage.microsoft.com        |104.40.82.191    |
|fef.msua01.manage.microsoft.com |138.91.243.97     |
|fef.msua05.manage.microsoft.com |138.91.244.151     |





