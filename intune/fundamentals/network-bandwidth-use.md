---
title: Configuration réseau requise et informations détaillées sur la bande passante pour Microsoft Intune
titleSuffix: ''
description: Passez en revue la configuration réseau requise et les informations détaillées sur la bande passante pour Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0507d607bfac6c084f1ce0b1f59d7474810ec8b7
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415107"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Configuration requise pour le réseau Intune et bande passante

Vous pouvez utiliser ces informations pour comprendre les besoins en bande passante de vos déploiements Intune.

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

Pour en savoir plus sur BITS et les ordinateurs Windows, consultez [Background Intelligent Transfer Service](https://technet.microsoft.com/library/bb968799.aspx) (Service de transfert intelligent en arrière-plan) dans la bibliothèque TechNet.

### <a name="delivery-optimization"></a>Optimisation de la distribution

L’optimisation de la distribution vous permet d’utiliser Intune pour réduire la consommation de bande passante quand vos appareils Windows 10 téléchargent des applications et des mises à jour. Grâce à l’utilisation d’un cache distribué en libre-emploi, les téléchargements peuvent être extraits de serveurs traditionnels et de sources secondaires (comme les peers réseau).

Pour afficher la liste complète des versions de Windows 10 et des types de contenu pris en charge par l’optimisation de la distribution, consultez [l’article Optimisation de la distribution pour les mises à jour de Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements).

Vous pouvez [configurer l’optimisation de la distribution](../configuration/delivery-optimization-settings.md) dans le cadre de vos profils de configuration d’appareil.

### <a name="use-branchcache-on-computers"></a>Utiliser BranchCache sur les ordinateurs

Les clients Intune peuvent utiliser BranchCache pour réduire le trafic WAN. Les systèmes d’exploitation suivants prennent en charge BranchCache :

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

Pour utiliser BranchCache, il doit être activé sur l’ordinateur client et ce dernier doit être configuré pour le **mode cache distribué**.

Lorsque le client Intune est installé sur des ordinateurs, BranchCache et le mode cache distribué sont activés par défaut. Toutefois, si la stratégie de groupe a désactivé BranchCache, Intune ne remplace pas cette stratégie et BranchCache reste désactivé.

Si vous utilisez BranchCache, contactez les autres administrateurs de votre organisation pour gérer la stratégie de groupe et la stratégie de pare-feu Intune. Vérifiez qu’ils ne déploient pas une stratégie qui désactive BranchCache ou des exceptions de pare-feu. Pour plus d’informations sur BranchCache, consultez [Vue d’ensemble de BranchCache](https://technet.microsoft.com/library/hh831696.aspx).

> [!NOTE]
> Vous pouvez utiliser Microsoft Intune pour gérer les PC Windows [en tant qu’appareils mobiles avec la gestion des appareils mobiles (MDM)](../enrollment/windows-enroll.md) ou en tant qu’ordinateurs avec le logiciel client Intune. Microsoft recommande que les clients [utilisent la solution MDM](../enrollment/windows-enroll.md) dans la mesure du possible. Si la gestion est effectuée de cette manière, BranchCache n’est pas pris en charge. Pour plus d’informations, consultez [Comparer la gestion des PC Windows en tant qu’ordinateurs ou qu’appareils mobiles](../pc-management-comparison.md).


## <a name="next-steps"></a>Étapes suivantes

[Passer en revue les points de terminaison pour Intune](../intune-endpoints.md)

