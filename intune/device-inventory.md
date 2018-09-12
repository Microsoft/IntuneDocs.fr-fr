---
title: Afficher les détails de l’appareil avec Microsoft Intune - Azure | Microsoft Docs
description: Affichez les détails de votre appareil, notamment les systèmes d’exploitation, l’espace de stockage, le fabricant et le modèle. Obtenez une liste des applications installées, vérifiez les stratégies de conformité et configurez TeamViewer avec Microsoft Intune dans Azure. Identique à l’affichage de l’inventaire des appareils gérés.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a658182800f480f27097e078f28adc95c35aa3ea
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313176"
---
# <a name="see-device-details-in-intune"></a>Consultez les détails de l’appareil dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La fonctionnalité **Appareils** fournit des détails supplémentaires sur les appareils que vous gérez, notamment le matériel et les applications installées.

Cet article vous explique comment afficher tous les appareils, ainsi que leurs propriétés dans le portail Azure.

## <a name="view-the-device-details"></a>Afficher les détails de l’appareil

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Appareils** > **Tous les appareils** > sélectionnez l’un des appareils listés pour afficher les détails correspondants :

   - **Vue d’ensemble** permet d’afficher le nom de l’appareil et de lister certaines de ses propriétés clés, notamment s’il s’agit d’un appareil BYOD (« Apportez votre propre appareil »), la date/heure de son enregistrement, etc. Vous pouvez effectuer les actions suivantes sur l’appareil :
      - [Mettre hors service](devices-wipe.md#retire)
        - [Réinitialisation](devices-wipe.md#wipe)
        - [Verrouillage à distance](device-remote-lock.md)
        - [Synchroniser l’appareil](device-sync.md)
        - [Réinitialiser le code secret](device-passcode-reset.md)
        - [Redémarrer](device-restart.md) (Windows uniquement)
        - [Redémarrage à zéro](device-fresh-start.md) (Windows uniquement)
     - Démarrer une session d’assistance à distance
   - Utilisez **Propriétés** pour affecter une [catégorie d’appareil créée](device-group-mapping.md) et changer le type de propriété d’un appareil. Par exemple, remplacez un appareil personnel par un appareil d’entreprise.
   - **Matériel** comprend de nombreux détails sur l’appareil, notamment l’ID, le système d’exploitation et la version, l’espace de stockage, le modèle et le fabricant, les paramètres d’accès conditionnel et bien d’autres informations.
   - **Applications découvertes** permet de lister toutes les applications dont Intune a détecté l’installation sur l’appareil, ainsi que leurs versions. Vous pouvez également **Exporter** la liste des applications dans un fichier .csv.
   - **Conformité de l’appareil** permet de lister toutes les stratégies de conformité affectées, et de déterminer si l’appareil est conforme ou non conforme.
   - **Configuration de l’appareil** permet d’afficher toutes les stratégies de configuration affectées à l’appareil, et de déterminer si la stratégie a réussi ou non.

Intune collecte une liste des applications uniquement sur les appareils appartenant à l’entreprise. Les applications ne sont pas vérifiées sur les appareils personnels. Pour les PC Windows 10, seules les applications modernes sont répertoriées pour les appareils appartenant à l’entreprise. Intune ne collecte pas d’informations concernant les applications Win32 sur l’appareil. En fonction de l’opérateur utilisé par les appareils, toutes les applications peuvent ne pas être collectées.

|Plate-forme|Pour les appareils personnels|Pour les appareils d’entreprise|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (sans client Configuration Manager)|Uniquement les applications gérées|Uniquement les applications gérées|
|Windows 8.1 (sans client Configuration Manager)|Uniquement les applications gérées|Uniquement les applications gérées|  
|Windows Phone 8|Uniquement les applications gérées|Uniquement les applications gérées|  
|Windows RT|Uniquement les applications gérées|Uniquement les applications gérées|  
|iOS|Uniquement les applications gérées|Toutes les applications installées sur l’appareil|
|macOS|Toutes les applications installées sur l’appareil|Toutes les applications installées sur l’appareil|  
|Android|Uniquement les applications gérées|Toutes les applications installées sur l’appareil|  

## <a name="hardware-device-details"></a>Informations sur les appareils matériels

### <a name="windows-and-ios-device-details"></a>Informations sur les appareils Windows et iOS :
|Détail|Description|  
|--------------|----------------------|  
|Nom|Nom de l’appareil|
|Nom de la gestion|Nom de l’appareil utilisé uniquement dans la console. Changer ce nom ne change pas le nom sur l’appareil.|
|UDID|Identificateur unique de l’appareil|
|ID d’appareil Intune|GUID qui identifie de façon unique l’appareil|
|Numéro de série|Numéro de série de l’appareil attribué par le fabricant|
|Appareil partagé|Si l’option **Oui** est sélectionnée, l’appareil est partagé par plusieurs utilisateurs.|
|Inscription approuvée par l’utilisateur|Si l’option **Oui** est sélectionnée, l’appareil dispose d’une inscription approuvée par l’utilisateur, qui permet aux administrateurs de gérer certains paramètres de sécurité.|
|Système d'exploitation|Système d’exploitation utilisé sur l’appareil.|
|Version du système d'exploitation|Version du système d’exploitation de l’appareil.|
|Langue du système d’exploitation|Langue définie dans le système d’exploitation de l’appareil|
|Espace de stockage total|Espace de stockage total sur l’appareil (en Go).|
|Espace de stockage libre|Espace de stockage non utilisé sur l’appareil (en Go)|


### <a name="windows-ios-and-macos-device-details"></a>Informations sur les appareils Windows, iOS et macOS
|Détail|Description|  
|--------------|----------------------|  
|IMEI|IMEI (International Mobile Equipment Identity) de l’appareil|
|MEID|MEID (Mobile Equipment Identifier) de l’appareil|
|Fabricant|Fabricant de l’appareil|
|Modèle|Modèle de l’appareil|
|Numéro de téléphone|Numéro de téléphone attribué à l’appareil.|
|Opérateur de l’abonné|Opérateur sans fil de l’appareil|
|Technologie mobile|Système radio utilisé par l’appareil|
|Adresse MAC du réseau Wi-Fi|Adresse MAC de l’appareil|
|ICCID|Identifiant ICCID, qui correspond au numéro d’identification unique d’une carte SIM|
|Date d’inscription|Date et heure de l’inscription de l’appareil dans Intune|
|Dernier contact|Date et heure de dernière connexion de l’appareil à Intune|
|Code de contournement du verrou d’activation|Code qui peut être utilisé pour contourner le verrou d’activation|
|Inscrit à AAD|Si l’option **Oui** est sélectionnée, l’appareil est inscrit auprès d’Azure Active Directory.|
|Compatibilité|État de conformité de l’appareil.|
|Avec activation d’EAS|Si l’option **Oui** est sélectionnée, l’appareil est synchronisé avec une boîte aux lettres Exchange.|
|ID d’activation EAS|Identificateur Exchange ActiveSync de l’appareil|
|Supervisé|Si l’option **Oui** est sélectionnée, les administrateurs ont un meilleur contrôle sur l’appareil.|
|Chiffré|Si l’option **Oui** est sélectionnée, les données stockées sur l’appareil sont chiffrées.|



## <a name="next-steps"></a>Étapes suivantes
Consultez ce que vous pouvez faire d’autre pour [gérer vos appareils](device-management.md) avec Intune.