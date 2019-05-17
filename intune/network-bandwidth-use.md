---
title: Configuration réseau requise et informations détaillées sur la bande passante pour Microsoft Intune
titleSuffix: ''
description: Passez en revue la configuration réseau requise et les informations détaillées sur la bande passante pour Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40f9ada715570de7b5b2f95292b7ed0d238242d2
ms.sourcegitcommit: 04d29d47b61486b3586a0e0e5e8e48762351f2a3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570791"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Configuration requise pour le réseau Intune et bande passante

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Ce guide aide les administrateurs Intune à comprendre la configuration réseau requise pour le service Intune. Vous pouvez utiliser ces informations pour comprendre les besoins en bande passante et les paramètres d’adresse IP et de port nécessaires pour les paramètres de proxy.

## <a name="average-network-traffic"></a>Trafic réseau moyen
Ce tableau répertorie la taille et la fréquence approximatives du contenu commun qui transite sur le réseau pour chaque client.

> [!NOTE]
> Pour garantir que les appareils reçoivent les mises à jour et le contenu nécessaires d’Intune, ils doivent être régulièrement connectés à Internet. Le temps nécessaire pour recevoir des mises à jour ou du contenu varie, mais les appareils doivent être connectés en continu à Internet au moins une heure par jour.

|Type de contenu|Taille approximative|Fréquence et détails|
|----------------|--------------------|-------------------------|
|Installation du client Intune<br /><br />**Les conditions requises suivantes s’ajoutent à l’installation du client Intune**|125 Mo|**Une fois**<br /><br />La taille du téléchargement du client varie en fonction du système d'exploitation de l'ordinateur client.|
|Package d'inscription du client|15 Mo|**Une fois**<br /><br />D'autres téléchargements sont possibles lorsqu'il existe des mises à jour pour ce type de contenu.|
|Agent Endpoint Protection|65 Mo|**Une fois**<br /><br />D'autres téléchargements sont possibles lorsqu'il existe des mises à jour pour ce type de contenu.|
|Agent Operations Manager|11 Mo|**Une fois**<br /><br />D'autres téléchargements sont possibles lorsqu'il existe des mises à jour pour ce type de contenu.|
|Agent de stratégie|3 Mo|**Une fois**<br /><br />D'autres téléchargements sont possibles lorsqu'il existe des mises à jour pour ce type de contenu.|
|Assistance à distance via l'agent Microsoft Easy Assist|6 Mo|**Une fois**<br /><br />D'autres téléchargements sont possibles lorsqu'il existe des mises à jour pour ce type de contenu.|
|Opérations quotidiennes du client|6 Mo|**Tous les jours**<br /><br />Le client Intune communique régulièrement avec le service Intune pour vérifier l’existence de mises à jour et stratégies, et pour signaler l’état du client au service.|
|Mises à jour des définitions de logiciels malveillants pour Endpoint Protection|Varie<br /><br />Généralement entre 40 Ko et 2 Mo|**Tous les jours**<br /><br />Jusqu'à trois fois par jour.|
|Mise à jour du moteur Endpoint Protection|5 Mo|**Tous les mois**|
|Mises à jour logicielles|Varie<br /><br />La taille varie selon les mises à jour que vous déployez.|**Tous les mois**<br /><br />En règle générale, les mises à jour logicielles sont publiées le deuxième mardi de chaque mois.<br /><br />Un ordinateur nouvellement inscrit ou déployé peut utiliser plus de bande passante lors du téléchargement de l'ensemble des mises à jour précédemment publiées.|
|Service Packs ;|Varie<br /><br />La taille varie pour chaque Service Pack que vous déployez.|**Varie**<br /><br />Dépend du moment auquel vous déployez les Service Pack.|
|Distribution de logiciels|Varie<br /><br />La taille varie selon les logiciels que vous déployez.|**Varie**<br /><br />Dépend du moment auquel vous déployez les logiciels.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Possibilités de réduction de la bande passante réseau
Vous pouvez utiliser une ou plusieurs des méthodes suivantes pour réduire l’utilisation de la bande passante réseau par les clients Intune.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Utiliser un serveur proxy pour mettre en cache les requêtes de contenu
Un serveur proxy peut mettre en cache du contenu pour réduire les téléchargements en double et la bande passante réseau utilisée par le contenu Internet.

Un serveur proxy de mise en cache qui reçoit des requêtes de contenu en provenance de clients peut récupérer ce contenu et mettre en cache les téléchargements et les réponses web. Le serveur utilise les données mises en cache pour répondre aux requêtes ultérieures des clients.

Voici les paramètres par défaut à utiliser pour un serveur proxy mettant en cache du contenu pour les clients Intune.


|          Paramètre           |           Valeur recommandée           |                                                                                                  Détails                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Taille du cache         |             De 5 à 30 Go             | La valeur varie en fonction du nombre d'ordinateurs clients dans votre réseau et des configurations que vous utilisez. Pour éviter que des fichiers soient supprimés trop tôt, ajustez la taille du cache pour votre environnement. |
| Taille du fichier de cache individuel |                950 Mo                 |                                                                     Ce paramètre n'est peut-être pas disponible dans tous les serveurs proxy de mise en cache.                                                                     |
|   Types d'objet à mettre en cache    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Les packages Intune sont des fichiers CAB extraits par téléchargement BITS (Service de transfert intelligent en arrière-plan) via HTTP.                                               |
> [!NOTE]
> Si vous utilisez un serveur proxy pour mettre en cache les requêtes de contenu, la communication est chiffrée uniquement entre le client et le proxy et du proxy à Intune. La connexion du client à Intune n’est pas chiffrée de bout en bout.

Pour plus d'informations sur l'utilisation d'un serveur proxy pour mettre en cache du contenu, consultez la documentation de votre solution de serveur proxy.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Utiliser le service de transfert intelligent en arrière-plan (BIST) sur les ordinateurs
Pendant les périodes que vous configurez, vous pouvez utiliser BITS sur un ordinateur Windows afin de réduire la bande passante réseau. Vous pouvez configurer une stratégie BITS dans la page **Bande passante réseau** de la stratégie de l’agent Intune.

> [!NOTE]
> Pour la GPM sur Windows, seule l’interface de gestion du système d’exploitation pour le type d’application MobileMSI utilise BITS pour télécharger. AppX/MsiX utilisent leur propre pile de téléchargement non BITS et les applications Win32 via l’agent Intune utilisent l’optimisation de livraison au lieu des BITS.

Pour en savoir plus sur BITS et les ordinateurs Windows, consultez [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx) (Service de transfert intelligent en arrière-plan) dans la bibliothèque TechNet.

### <a name="use-branchcache-on-computers"></a>Utiliser BranchCache sur les ordinateurs
Les clients Intune peuvent utiliser BranchCache pour réduire le trafic WAN. Les systèmes d’exploitation suivants prennent en charge BranchCache :

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Pour utiliser BranchCache, il doit être activé sur l’ordinateur client et ce dernier doit être configuré pour le **mode cache distribué**.

Lorsque le client Intune est installé sur des ordinateurs, BranchCache et le mode cache distribué sont activés par défaut. Toutefois, si la stratégie de groupe a désactivé BranchCache, Intune ne remplace pas cette stratégie et BranchCache reste désactivé.

Si vous utilisez BranchCache, contactez les autres administrateurs de votre organisation pour gérer la stratégie de groupe et la stratégie de pare-feu Intune. Vérifiez qu’ils ne déploient pas une stratégie qui désactive BranchCache ou des exceptions de pare-feu. Pour plus d’informations sur BranchCache, consultez [Vue d’ensemble de BranchCache](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Configuration requise des communications du réseau

Activez les communications réseau entre les appareils que vous gérez et les points de terminaison nécessaires pour les services cloud.

En tant que service cloud uniquement, Intune ne nécessite pas d’infrastructure sur site telle que des serveurs ou des passerelles.

Pour gérer les appareils qui se trouvent derrière des pare-feu et des serveurs proxy, vous devez activer la communication pour Intune.

- Le serveur proxy doit prendre en charge les protocoles **HTTP (80)** et **HTTPS (443)**, car les clients Intune utilisent ces deux protocoles
- Pour certaines tâches (telles que le téléchargement des mises à jour logicielles), Intune nécessite un accès de serveur proxy non authentifié à manage.microsoft.com

Vous pouvez modifier les paramètres du serveur proxy sur des ordinateurs clients. Vous pouvez également utiliser des paramètres de stratégie de groupe pour modifier les paramètres pour tous les ordinateurs clients situés derrière un serveur proxy spécifié.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Les appareils gérés nécessitent des configurations qui permettent à **Tous les utilisateurs** d’accéder à des services à travers des pare-feu.

Les tableaux suivants répertorient les ports et services auxquels le client Intune accède :

|**Domaines**|**Adresse IP**|
|---------------------|-----------|
|login.microsoftonline.com | Plus d’informations [URL et plages d’adresses IP Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
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






### <a name="apple-device-network-information"></a>Informations réseau de l’appareil Apple


|Utilisé pour|Nom d’hôte (adresse IP/sous-réseau)|Protocole|Port|
|-----|--------|------|-------|
|Réception de notifications Push du service Intune via Apple Push Notification Service (APNS). Consultez la documentation d’Apple [ici](https://support.apple.com/en-us/HT203609)|                                    gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |
|Envoi de commentaires au service Intune via Apple Push Notification Service (APNS)|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|Récupération et affichage de contenu de serveurs Apple|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Communications avec des serveurs APNS|#-courier.push.apple.com (17.0.0.0/8)<br>« # » est un nombre aléatoire compris entre 0 et 50.|    TCP     |  5223 et 443  |
|Diverses fonctionnalités telles que l’accès au World Wide Web, iTunes Store, macOS App Store, iCloud, messagerie, etc. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 ou 443   |

Pour plus d’informations, consultez des documents Apple relatifs aux [ports TCP et UDP utilisés par les produits logiciels Apple](https://support.apple.com/en-us/HT202944), aux [connexions hôtes serveurs macOS, iOS et iTunes et processus d’arrière-plan iTunes](https://support.apple.com/en-us/HT201999) et [si vos clients macOS et iOS reçoivent des notifications Push Apple](https://support.apple.com/en-us/HT203609).
