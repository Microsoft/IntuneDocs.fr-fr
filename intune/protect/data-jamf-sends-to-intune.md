---
title: Données envoyées par JAMF Pro à Intune
titleSuffix: Microsoft Intune
description: Passez en revue la liste des données que Jamf Pro envoie à Microsoft Intune quand vous intégrez Jamf Pro pour gérer des ordinateurs Mac avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4bf6df44335f3375d58d3c2c11da7cb3f982b3e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502424"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Données envoyées par Jamf Pro à Intune

Quand vous utilisez [Jamf Pro](https://www.jamf.com) pour gérer vos ordinateurs Mac pour utilisateurs finaux avec Intune, Jamf Pro capture des données d’inventaire sur les appareils macOS gérés. 

## <a name="data"></a>Niveau  
Pour la liste des données que Jamf Pro partage avec Intune, voir [Annexe : Données d'inventaire partagées avec Microsoft Intune](https://docs.jamf.com/technical-papers/jamf-pro/microsoft-intune/10.9.0/Appendix__Inventory_Information_Shared_with_Microsoft_Intune.html) dans la documentation technique de Jamf Pro. 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez obtenir des informations sur la façon de [supprimer un appareil géré par Jamf dans la documentation de Jamf Pro](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Vous pouvez aussi ouvrir un ticket de support auprès du [Support Jamf](https://www.jamf.com/support/) pour obtenir une aide supplémentaire. 

