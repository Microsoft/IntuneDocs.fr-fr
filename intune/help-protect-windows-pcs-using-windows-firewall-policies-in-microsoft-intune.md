---
title: Stratégies de pare-feu pour PC Windows
titlesuffix: Microsoft Intune
description: Intune peut vous aider à sécuriser les PC que vous gérez avec le client Intune de plusieurs façons, notamment en vous aidant à configurer les paramètres du Pare-feu Windows.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9549c072-ac3d-4d14-a931-a2eda8846217
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee84ca92d247a162653b398fd1332161fb887599
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461075"
---
# <a name="help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune"></a>Protéger les PC Windows à l'aide de stratégies de Pare-feu Windows dans Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune peut vous aider à sécuriser les PC Windows que vous gérez avec le client Intune et ce, de plusieurs façons. Par exemple, il peut fournir des stratégies vous permettant de configurer les paramètres du Pare-feu Windows sur des PC.

Si vous n’avez pas encore installé le client de PC Windows Intune sur vos ordinateurs, consultez [Installer le client de PC Windows avec Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Utilisez les informations des sections suivantes pour configurer, déployer et surveiller les stratégies du Pare-feu Windows sur les PC Windows.

## <a name="use-intune-policies-to-manage-windows-firewall"></a>Utiliser des stratégies Intune pour gérer le Pare-feu Windows
La stratégie du Pare-feu Windows vous permet de créer et de déployer les paramètres qui contrôlent le Pare-feu Windows sur les PC gérés. Vous ne pouvez pas gérer des exceptions personnalisées pour le Pare-feu Windows, et ces paramètres n’affectent pas les pare-feux tiers.

> [!NOTE]
> Si la stratégie Microsoft Intune et la stratégie de groupe sont configurées pour gérer le même paramètre sur le PC, le paramètre de la stratégie de groupe est prioritaire sur la stratégie Microsoft Intune. Pour en savoir plus sur la façon d’éviter des conflits entre la stratégie Intune et la stratégie de groupe, voir [Résoudre des conflits de stratégie entre les objets de stratégie de groupe et Microsoft Intune](resolve-gpo-and-microsoft-intune-policy-conflicts.md).
>
> Pour déployer les paramètres du Pare-feu Windows sur des ordinateurs exécutant Windows Vista, vous devez d’abord installer le [correctif logiciel KB971800](http://support2.microsoft.com/kb/971800) sur ces ordinateurs.

> [!IMPORTANT]
> Pour gérer le Pare-feu Windows à l’aide d’Intune, assurez-vous que les deux services suivants sont activés sur les ordinateurs que vous allez gérer :
>
> -   Pare-feu Windows
> -   Agent de stratégie IPsec

## <a name="configure-a-windows-firewall-policy"></a>Configurer une stratégie du Pare-feu Windows

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com/), choisissez **Stratégie** &gt; **Ajouter une stratégie**.

2.  Configurez et déployez une stratégie **Paramètres du Pare-feu Windows** . Vous pouvez utiliser les paramètres recommandés ou personnaliser les paramètres. Pour plus d’informations sur la création et le déploiement des stratégies, consultez [Tâches courantes de gestion des PC Windows avec le client Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

    La section suivante répertorie les valeurs que vous pouvez configurer dans la stratégie, ainsi que les valeurs par défaut qui seront utilisées si vous ne personnalisez pas la stratégie.

Après avoir déployé une stratégie du Pare-feu Windows, vous pouvez afficher son état dans la page **Toutes les stratégies** de l’espace de travail **Stratégie**.

## <a name="specify-policy-settings-for-windows-firewall"></a>Spécifier des paramètres de stratégie pour le Pare-feu Windows

### <a name="turn-on-windows-firewall"></a>Activer le Pare-feu Windows

Ces paramètres de stratégie activent le Pare-feu Windows sur les ordinateurs gérés qui sont :
- connectés à un domaine (par exemple, sur l’espace de travail) ;
- connectés à un réseau privé (approuvé), par exemple un réseau domestique ;
- connectés à un réseau public non approuvé (par exemple un café).

La valeur par défaut pour chacun de ces paramètres est **Oui**, qui est la valeur la plus sécurisée.



### <a name="block-all-incoming-connections-including-those-in-the-list-of-allowed-programs"></a>Bloquer toutes les connexions entrantes, y compris celles figurant dans la liste de programmes autorisés

Ces paramètres de stratégie configurent le Pare-feu Windows pour bloquer le trafic réseau entrant sur les ordinateurs gérés qui sont :
- connectés à un domaine (par exemple, sur l’espace de travail) ;
- connectés à un réseau privé (approuvé), par exemple un réseau domestique ;
- connectés à un réseau public non approuvé (par exemple un café).

La valeur par défaut pour chacun de ces paramètres est **Oui**, qui est la valeur la plus sécurisée.

> [!IMPORTANT]
> Si votre environnement comprend des ordinateurs gérés exécutant Windows Vista sans Service Pack installé, vous devez installer la mise à jour associée à l’[article 971800](http://go.microsoft.com/fwlink/?LinkId=188405) de la Base de connaissances Microsoft, ou bien désactiver les paramètres de la stratégie **Bloquer toutes les connexions entrantes** dans les stratégies déployées sur ces ordinateurs.

### <a name="notify-the-user-when-windows-firewall-blocks-a-new-program"></a>Informer l'utilisateur lorsque le Pare-feu Windows bloque un nouveau programme

Ces paramètres de stratégie déterminent si le Pare-feu Windows doit avertir l’utilisateur du PC en cas de blocage du trafic réseau entrant lorsque les ordinateurs gérés sont :
- connectés à un domaine (par exemple, sur l’espace de travail) ;
- connectés à un réseau privé (approuvé), par exemple un réseau domestique ;
- connectés à un réseau public non approuvé (par exemple un café).

La valeur par défaut pour chacun de ces paramètres est **Oui**.


### <a name="configure-predefined-exceptions"></a>Configurer des exceptions prédéfinies

Vous pouvez configurer des exceptions qui autorisent des types spécifiques de trafic réseau via le pare-feu, indépendamment des valeurs que vous avez configurées précédemment. Aucun de ces paramètres n’est configuré par défaut.

|Nom du paramètre|Détails|
|------------------|--------------------|
|**BranchCache - Récupération du contenu**<br>(Windows 7 ou version ultérieure)|Ce paramètre permet aux clients BranchCache d’utiliser le protocole HTTP pour récupérer le contenu d’autres clients BranchCache en mode distribué, et à partir du cache hébergé en mode cache hébergé. Ce paramètre utilise HTTP.|
|**BranchCache - Client de cache hébergé**<br>(Windows 7 ou version ultérieure)|Ce paramètre permet aux clients BranchCache d’utiliser un cache hébergé. Ce paramètre utilise le protocole HTTPS.|
|**BranchCache - Serveur de cache hébergé**|Ce paramètre permet aux clients BranchCache d’utiliser un cache hébergé pour communiquer avec d’autres clients. Ce paramètre utilise le protocole HTTPS.|
|**BranchCache - Découverte d'homologue**<br>(Windows 7 ou version ultérieure)|Ce paramètre permet aux clients BranchCache d’utiliser le protocole Web Services Dynamic Discovery (WS-Discovery) pour vérifier la disponibilité du contenu sur le sous-réseau local.|
|**BITS Peercaching**|Ce paramètre permet aux clients d’utiliser le service de transfert intelligent en arrière-plan (BITS) pour rechercher et partager des fichiers qui sont stockés dans le cache BITS sur les clients dans le même sous-réseau. Ce paramètre utilise les technologies Web Services on Devices (WSDAPI) et l’appel de procédure distante (RPC).|
|**Connexion à un projecteur réseau**|Ce paramètre permet aux utilisateurs de se connecter à des projecteurs via des réseaux câblés ou sans fil pour projeter des présentations. Ce paramètre utilise le WSDAPI.|
|**Accès au réseau de base**|Ce paramètre permet aux clients d’utiliser les protocoles IPv4 et IPv6 pour se connecter aux ressources réseau.|
|**Coordinateur de transactions distribuées**|Ce paramètre permet à des ordinateurs gérés de coordonner les transactions qui mettent à jour des ressources protégées par transaction, comme les bases de données, les files d’attente de messages et les systèmes de fichiers.|
|**Partage de fichiers et d'imprimantes**|Ce paramètre permet aux utilisateurs de partager des imprimantes et fichiers locaux avec d’autres utilisateurs sur le réseau. Ce paramètre utilise NetBIOS, la résolution LLMNR (Link Local Multicast Name Resolution), le protocole SMB (Server Message Block) et RPC.|
|**HomeGroup**<br>(Windows 7 ou version ultérieure)|Ce paramètre autorise les ordinateurs gérés à participer à un réseau HomeGroup.|
|**Service iSCSI**|Ce paramètre permet à des ordinateurs gérés de se connecter à des appareils et serveurs iSCSI.|
|**Service de gestion de clés**|Ce paramètre permet aux ordinateurs d’être comptabilisés pour la conformité des licences dans les environnements d’entreprise.|
|**Unités Media Center Extender**|Ce paramètre autorise les unités Media Center Extender à communiquer avec les ordinateurs qui exécutent Windows Media Center. Ce paramètre utilise qWave et le protocole SSDP (Simple Service Discovery Protocol).|
|**Service Netlogon**|Ce paramètre configure un canal de sécurité entre les clients de domaine et un contrôleur de domaine pour l’authentification des utilisateurs et des services. Ce paramètre utilise un RPC.|
|**Découverte du réseau**|Ce paramètre permet aux ordinateurs de détecter d’autres appareils et d’être détectés par d’autres appareils sur le réseau. Ce paramètre utilise les services de découverte, d'hôte et de publication de fonctions et les protocoles de réseau SSDP, NetBIOS, LLMNR et UPnP.|
|**Journaux et alertes de performances**|Ce paramètre permet la gestion à distance du service Journaux et alertes de performances. Ce paramètre utilise un RPC.|
|**Administration à distance**|Ce paramètre permet l’administration à distance de l’ordinateur.|
|**Assistance à distance**|Ce paramètre permet aux utilisateurs d’ordinateurs gérés de demander une assistance à distance par d’autres utilisateurs sur le réseau. Ce paramètre utilise les protocoles de réseau UPnP, SSDP, PNRP (Peer Name Resolution Protocol) et Teredo.|
|**Bureau à distance**|Ce paramètre permet à l’ordinateur d’utiliser le Bureau à distance pour accéder à d’autres ordinateurs.|
|**Gestion à distance du journal des événements**|Ce paramètre permet la consultation et la gestion à distance des journaux des événements des clients. Ce paramètre utilise les canaux nommés et un RPC.|
|**Gestion à distance des tâches planifiées**|Ce paramètre permet la gestion à distance du service de planification des tâches. Ce paramètre utilise un RPC.|
|**Gestion de services à distance**|Ce paramètre permet la gestion à distance des services locaux sur les clients. Ce paramètre utilise les canaux nommés et un RPC.|
|**Gestion des volumes à distance**|Ce paramètre permet la gestion à distance des volumes de disque au plan logiciel et matériel. Ce paramètre utilise un RPC.|
|**Routage et accès distant**|Ce paramètre autorise les connexions d’accès distant et VPN entrantes aux ordinateurs.|
|**Protocole SSTP (Secure Socket Tunneling Protocol)**|Ce paramètre autorise les connexions VPN entrantes aux ordinateurs gérés via le protocole SSTP (Secure Socket Tunneling Protocol). Ce paramètre utilise le protocole HTTPS.|
|**Interruption SNMP**|Ce paramètre permet aux ordinateurs gérés de recevoir le trafic du service d’interruption du protocole SNMP (Simple Network Management Protocol).|
|**Infrastructure UPnP**|Ce paramètre configure le service UPnP Framework sur les ordinateurs pour leur permettre de découvrir et d’utiliser les appareils certifiés UPnP.|
|**Service d'inscription de nom d'ordinateur Espace de collaboration Windows**|Ce paramètre permet aux ordinateurs de rechercher d’autres ordinateurs et de communiquer avec eux à l’aide des protocoles SSDP et PNRP.|
|**Lecteur Windows Media**|Ce paramètre permet aux utilisateurs d’accéder à la diffusion multimédia en continu via UDP (User Datagram Protocol).|
|**Service Partage réseau du Lecteur Windows Media**|Ce paramètre permet aux utilisateurs de partager des médias sur un réseau. Ce paramètre utilise les protocoles réseau SSDP, qWave et UPnP.|
|**Service Partage réseau du Lecteur Windows Media (Internet)**<br>(Windows 7 ou version ultérieure)|Ce paramètre permet aux utilisateurs de partager des médias personnels sur Internet.|
|**Espace de collaboration Windows**|Ce paramètre permet aux utilisateurs de collaborer sur un réseau pour partager des documents, des programmes et leur Bureau. Ce paramètre utilise la fonction de réplication du système de fichiers DFS (DFSR) et P2P.|
|**Windows Peer to Peer Collaboration Foundation**|Ce paramètre configure différents programmes et technologies pair à pair pour leur permettre de se connecter. Ce paramètre utilise SSDP et PNRP.|
|**Gestion à distance de Windows (compatibilité)**|Ce paramètre permet l’administration à distance des ordinateurs gérés via WS-Management, un protocole basé sur des services web pour la gestion à distance des systèmes d’exploitation et des appareils.|
|**Gestion à distance de Windows**<br>(Windows 8 ou version ultérieure)|Ce paramètre permet l’administration à distance des ordinateurs gérés via WS-Management, un protocole basé sur des services web pour la gestion à distance des systèmes d’exploitation et des appareils.|
|**Windows Virtual PC**<br>(Windows 7 ou version ultérieure)|Ce paramètre permet à des machines virtuelles de communiquer avec d’autres ordinateurs.|
|**Appareils mobiles sans fil**|Ce paramètre autorise le transfert de médias depuis un appareil multimédia ou une caméra compatible avec le réseau vers les ordinateurs gérés via le protocole MTP (Media Transfer Protocol). Ce paramètre utilise les protocoles de réseau SSDP et UPnP.|

### <a name="see-also"></a>Voir aussi
[Stratégies pour protéger les PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
