---
title: Connecteur Intune Exchange pour Exchange Online
titleSuffix: ''
description: Connectez Intune au service Office 365 Exchange pour prendre en charge la gestion des appareils mobiles via Exchange ActiveSync.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 318bde24e42bfdf9bbcf15d83f42405fc06f7901
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184206"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Configurer le connecteur de service Exchange pour Intune et Exchange Online
Cet article explique comment connecter le service Microsoft Intune à Exchange Online ou au nouveau service Exchange Online Dedicated. Pour déterminer si votre environnement Microsoft Exchange Online Dedicated est la version **nouvelle** ou **héritée**, contactez votre responsable de comptes.

Avec le **Connecteur service à service**, vous pouvez gérer Exchange ActiveSync (EAS) et Intune à partir d’une console d’administration unique.  Le connecteur n’est pas requis pour activer l’accès conditionnel à Exchange Online.

## <a name="service-to-service-connector-requirements"></a>Configuration requise pour le connecteur de service à service
Le **connecteur de service à service** prend en charge seulement Exchange Online ou Exchange Online Dedicated, et n’a pas de configuration requise pour une infrastructure locale. 


|              Condition requise               |                                                                                                            Plus d’informations                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Le serveur Exchange Online configuré et en cours d’exécution |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   Autorité de gestion des appareils mobiles   |                                                       [Définir Microsoft Intune comme autorité de gestion des appareils mobiles](mdm-authority-set.md)                                                       |
|       Version Microsoft Exchange       |                                                                                      Exchange Online ou le nouveau service Exchange Online Dedicated                                                                                      |
|    Synchronisation Active Directory    | Avant de pouvoir utiliser le connecteur Intune, vous devez [configurer la synchronisation Active Directory](/intune/users-add) pour que vos utilisateurs et groupes de sécurité locaux soient synchronisés avec votre instance d’Azure Active Directory. |

### <a name="exchange-cmdlet-requirements"></a>Spécifications des applets de commande Exchange

Vous devez aussi créer un compte d’utilisateur Exchange Online utilisé par le connecteur de service Intune Exchange. Le compte doit être autorisé à exécuter les applets de commande Windows PowerShell Exchange nécessaires suivantes :

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Configurer Service to Service Connector

1. Connectez-vous au [Portail Azure](http://portal.azure.com) avec un compte d’utilisateur disposant des droits d’administrateur Exchange, des autorisations pour les cmdlets décrites [plus haut](#exchange-cmdlet-requirements), d’une licence Intune valide et du rôle Administrateur général. Microsoft Intune utilise l’adresse e-mail de l’utilisateur actuellement connecté pour configurer la connexion.

2. Choisissez **Tous les services** dans le menu de gauche, puis entrez **Intune** dans le filtre de la zone de texte.

3. Choisissez **Intune** pour ouvrir le tableau de bord Microsoft Intune. Choisissez **Accès conditionnel** puis, sous **Configurer**, choisissez **Connecteur de service Exchange**.

4.  Dans la page **Accès conditionnel - Connecteur de service Exchange**, choisissez **Configurer le connecteur de service à service**. 
   
     ![Image montrant la sélection du lien Configurer le connecteur de service à service](media/exchange_service_connector.png)

Le connecteur de service à service configure et synchronise automatiquement votre environnement Exchange Online ou votre nouvel environnement Exchange Online Dedicated.

## <a name="validate-your-exchange-connection"></a>Valider votre connexion Exchange

Après avoir configuré le connecteur de service à service Exchange, validez les informations du serveur de connecteur Exchange dans la page **Accès conditionnel - Connecteur de service Exchange**.

Vous pouvez également vérifier l’**État de la connexion** et la date et l’heure de la dernière tentative de synchronisation réussie.

 