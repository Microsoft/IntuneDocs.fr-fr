---
title: Rapport de chiffrement et clés BitLocker dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Consultez un rapport sur l’état de chiffrement de votre appareil et accédez aux clés de récupération BitLocker à partir du portail Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d90bc17d01a76c9c566210edc3bdc265511fa16d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047822"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>Superviser le chiffrement des appareils et BitLocker  
Intune offre un emplacement centralisé pour identifier l’état de chiffrement de vos appareils Windows 10 et vous permet d’accéder à des informations importantes pour BitLocker à partir de vos appareils, comme dans Azure Active Directory (Azure AD).  

- Le [rapport de chiffrement](#encryption-report) fournit des détails sur l’état de chiffrement et de préparation d’un appareil. Les détails du rapport peuvent vous aider à identifier les problèmes qui empêchent le chiffrement correct des appareils que vous voulez protéger.  
- [Affichez des détails BitLocker](#bitlocker-recovery-keys) comme l’ID de clé et les clés de récupération de vos appareils à partir du portail Intune.  

## <a name="encryption-report"></a>Rapport de chiffrement
Vous pouvez utiliser le rapport de chiffrement pour voir des détails sur l’état de chiffrement de vos appareils Windows 10.  

Pour trouver le rapport, connectez-vous à [Intune](https://aka.ms/intuneportal) et accédez à **Configuration de l’appareil**, puis sous *Surveiller*, sélectionnez **Rapport de chiffrement**.  

### <a name="prerequisites"></a>Prérequis :
Pour apparaître dans le rapport de chiffrement, un appareil doit exécuter Windows version 1607 ou ultérieure.  

### <a name="report-details"></a>Détails du rapport
Le rapport présente le **nom** de vos appareils Windows 10 et des informations générales sur chacun d’eux, notamment les suivantes :  
- **Version du système d’exploitation** : version de Windows.  
- **Version du module de plateforme sécurisée** : version de la puce TPM (module de plateforme sécurisée) sur l’appareil.  
- **Préparation du chiffrement** : évaluation de la préparation des appareils à la prise en charge du chiffrement BitLocker. Les appareils peuvent être identifiés de la manière suivante :
  - **Prêt** : L’appareil peut être chiffré à l’aide d’une stratégie MDM, ce qui l’oblige à avoir un module de plateforme sécurisée (TPM) et à respecter les exigences de référence SKU et de version de Windows 10 suivantes :
    - Version 1703 ou ultérieure de Business, Enterprise, Education
    - Version 1809 ou ultérieure de Pro  
  
    Pour plus d’informations, consultez le [fournisseur de service de configuration de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) dans la documentation de Windows.  

  - **Non prêt** : L’appareil n’a pas toutes les fonctionnalités de chiffrement, mais il prend quand même en charge le chiffrement. Par exemple, l’appareil peut être chiffré manuellement par un utilisateur ou par le biais d’une stratégie de groupe définie pour permettre le chiffrement sans TMP.
  - **Non applicable** : Les informations ne sont pas suffisantes pour classer cet appareil.  

- **État du chiffrement** : indique si le lecteur du système d’exploitation est chiffré.  


### <a name="device-encryption-status"></a>État du chiffrement de l’appareil
Quand vous sélectionnez un appareil, Intune affiche le volet **État du chiffrement de l’appareil**.

Ce volet fournit les détails suivants :  
- **Nom de l’appareil** : nom de l’appareil que vous visualisez.  
- **Préparation du chiffrement** : évaluation de la préparation des appareils à la prise en charge du chiffrement BitLocker. L’état du chiffrement d’un appareil peut être *Chiffré* même si la préparation du chiffrement a la valeur *Non prêt*, car il lui manque un module de plateforme sécurisée (TPM). (Consultez Préparation du chiffrement dans la section précédente pour plus d’informations.)
- **État du chiffrement** : indique si le lecteur du système d’exploitation est chiffré.  
- **Profils** : liste des profils de *configuration de l’appareil* qui s’appliquent à cet appareil et incluent les paramètres et le type de profil suivants :  
  - Type de profil = *Endpoint Protection*  
  - Paramètres > Chiffrement Windows > Chiffrer les appareils = *Obligatoire*  

  Cette liste peut s’avérer utile pour localiser des stratégies individuelles à passer en revue, si le résumé de l’état du profil indique des problèmes.  

- **Résumé de l’état du profil** : résumé des profils qui s’appliquent à cet appareil. Le résumé représente la condition la moins favorable parmi tous les profils applicables. Par exemple, si un seul profil entraîne une erreur, le résumé de l’état du profil indique *Erreur*.  
- **Informations d’état** : détails avancés sur l’état du chiffrement de l’appareil. 
  > [!NOTE]  
  > Intune présente uniquement les *informations d’état* pour les appareils qui exécutent la *mise à jour du d’avril 2019 de Windows 10* ou une version ultérieure.
  
  Ce champ présente des informations pour chaque erreur applicable pouvant être détectée. Vous pouvez utiliser ces informations pour comprendre pourquoi un appareil n’est pas prêt pour le chiffrement.  

  Voici quelques exemples d’informations d’état qu’Intune peut indiquer :  

   - La stratégie BitLocker nécessite le consentement de l’utilisateur pour lancer l’Assistant Chiffrement de lecteur BitLocker et démarrer le chiffrement du volume de système d’exploitation, mais l’utilisateur n’a pas donné son consentement.  
   - La méthode de chiffrement du volume de système d’exploitation ne correspond pas à la stratégie BitLocker.  
   - La stratégie BitLocker nécessite un protecteur par TPM pour protéger le volume de système d’exploitation, mais aucun TPM n’est utilisé.  
   - La stratégie BitLocker nécessite un protecteur uniquement par TPM pour le volume de système d’exploitation, mais aucune protection par TPM n’est utilisée.  
   - La stratégie BitLocker nécessite une protection par TPM+code PIN pour le volume de système d’exploitation, mais aucun protecteur de ce type n’est utilisé.  
   - La stratégie BitLocker nécessite une protection par TPM+clé de démarrage pour le volume de système d’exploitation, mais aucun protecteur de ce type n’est utilisé.  
   - La stratégie BitLocker nécessite une protection par TPM+code PIN+clé de démarrage pour le volume de système d’exploitation, mais aucun protecteur de ce type n’est utilisé.  
   - Le volume de système d’exploitation n’est pas protégé.  
   - La sauvegarde de la clé de récupération a échoué.  
   - Un lecteur fixe n’est pas protégé.  
   - La méthode de chiffrement du lecteur fixe ne correspond pas à la stratégie BitLocker.  
   - Pour chiffrer les lecteurs, la stratégie BitLocker exige que l’utilisateur se connecte en tant qu’administrateur ou, si l’appareil est joint à Azure AD, que la stratégie AllowStandardUserEncryption ait la valeur 1.  
   - L’environnement de récupération Windows (WinRE) n’est pas configuré.  
   - Aucun module de plateforme sécurisée (TPM) n’est disponible pour BitLocker, soit parce qu’il n’est pas présent car il est devenu indisponible dans le Registre, soit parce que le système d’exploitation se trouve sur un lecteur amovible.  
   - Le module de plateforme sécurisée (TPM) n’est pas prêt pour BitLocker.  
   - Le réseau n’est pas disponible, ce qui est nécessaire pour la sauvegarde des clés de récupération.  

## <a name="bitlocker-recovery-keys"></a>Clés de récupération BitLocker
Intune fournit l’accès au panneau Azure AD pour BitLocker pour que vous puissiez voir les ID de clé BitLocker et les clés de récupération de vos appareils Windows 10, à partir du portail Intune.  Pour être accessible, l’appareil doit avoir ses clés déposées dans Azure AD. 
1. Connectez-vous à [Intune](https://aka.ms/intuneportal), accédez à **Appareils**, puis sous *Gérer*, sélectionnez **Tous les appareils**.
2. Sélectionnez un appareil dans la liste, puis sous *Surveiller*, sélectionnez **Clés de récupération**.  
  
Quand des clés sont disponibles dans Azure AD, les informations suivantes sont disponibles :
- ID de clé BitLocker
- Clé de récupération BitLocker
- Type de lecteur  

Quand les clés ne sont pas dans Azure AD, Intune indique *Aucune clé BitLocker trouvée pour cet appareil*.  

Les informations pour BitLocker sont obtenues en utilisant le [fournisseur de service de configuration BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp). Ce dernier est pris en charge sur Windows 10 versions 1703 et ultérieures et sur Windows 10 Pro versions 1809 et ultérieures. 

## <a name="next-steps"></a>Étapes suivantes
Créez une stratégie de [conformité des appareils](compliance-policy-create-windows.md) pour les appareils Windows 10 afin de configurer BitLocker et le chiffrement.
