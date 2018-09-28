---
title: Collections Intune Data Warehouse
titlesuffix: Microsoft Intune
description: Les collections Intune Data Warehouse fournissent des détails sur l’API Data Warehouse.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/04/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune
ms.openlocfilehash: 4df55309587ac079cfeaec299d70635b090e300b
ms.sourcegitcommit: 443b4cb3390da47bf1e497b1f0c0137a5ddda7bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43821625"
---
#  <a name="intune-data-warehouse-collections"></a>Collections Intune Data Warehouse

Les collections Intune Data Warehouse suivantes fournissent les propriétés, les descriptions et les exemples de collections v1.0 d’entités de l’API Data Warehouse. 

## <a name="apprevisions"></a>appRevisions
Les listes d’entités **appRevision** répertorient toutes les versions des applications.

|          Propriété          |                                      Description                                      |                Exemple               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | Identificateur unique de l’application.                                                         | 123                                  |
| ApplicationId              | Identificateur unique de l’application (semblable à AppKey, sauf qu’il s’agit d’une clé naturelle).        | b66bc706-ffff-7437-0340-032819502773 |
| Révision                   | Version mentionnée par l’administrateur durant le chargement du binaire.                   | 2                                    |
| Titre                      | Titre de l’application.                                                                     | Excel                                |
| Éditeur                  | Éditeur de l’application.                                                                 | Microsoft                            |
| UploadState                | État de chargement de l’application.                                                              | 1                                    |
| AppTypeKey                 | Référence à AppType décrite dans la section suivante.                            | 1                                    |
| VppProgramTypeKey          | Référence à VppProgramType décrite ci-dessous.                                        | 30876                                |
| CreationTime               | Heure de création de cette révision.                                            | 23/11/2016 0:00                      |
| ModifiedTime               | Heure du dernier changement apporté à cette révision.                            | 23/11/2016 0:00                      |
| Size                       | Taille du binaire en octets.                                                          | 120 392 000                          |
| StartDateInclusiveUTC      | Date et heure UTC de création de la révision de cette application dans l’entrepôt de données.      | 23/11/2016 0:00                      |
| EndDateExclusiveUTC        | Date et heure UTC où cette révision d’application est devenue obsolète.                        | 23/11/2016 0:00                      |
| IsCurrent                  | Indique si cette version de l’application est active ou non dans l’entrepôt de données.         | Vrai/Faux                           |
| RowLastModifiedDateTimeUTC | Date et heure UTC de la dernière modification de cette version d’application dans l’entrepôt de données. | 23/11/2016 0:00                      |

## <a name="apptypes"></a>appTypes
L’entité **appTypes** répertorie la source d’installation d’une application.

|   Propriété  |        Description        |
|:-----------:|:-------------------------:|
| AppTypeID   | ID du type           |
| AppTypeKey  | Clé de substitution pour la clé |
| AppTypeName | Type d’application                  |

### <a name="example"></a>Exemple

| AppTypeID |                Nom               |                     Description                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Application de l’Android Store               | Une application de l’Android Store.                             |
| 1         | Application LOB Android                 | Une application métier Android.                  |
| 2         | Application de l’Android Store gérée (MAM) | Une application de l’Android Store activée pour la gestion. |
| 3         | Application de l’App Store iOS                   | Une application de l’App Store iOS.                                 |
| 4         | Application LOB iOS                     | Une application métier iOS.                      |
| 5         | Application de l’App Store iOS gérée (MAM)     | Une application de l’App Store iOS activée pour la gestion.       |
| 6         | Office 365 Pro Plus Suite             | Office 365 Pro Plus Suite pour Windows 10.     |
| 7         | Application Web                         | Une application web.                                        |
| 8         | Application du Windows Phone Store  8.1     | Une application du Windows Phone Store 8.1.                    |
| 9         | Application du Windows Store               | Une application du Windows Store.                              |
| 10        | Applications métier Windows                | Une application métier AppX Windows.              |
| 11        | Windows Mobile MSI              | Une application métier MSI.                      |
| 12        | Application métier Windows Phone           | Une application métier Windows Phone.             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
Le tableau suivant récapitule l’état d’affectation des stratégies de conformité pour les appareils. Il répertorie le nombre d’appareils dans chaque état de conformité.

|    Propriété   |                                                                                      Description                                                                                     |  Exemple |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | Clé de date de la création du récapitulatif pour la stratégie de conformité.                                                                                                                   | 20161204 |
| Unknown       | Nombre d’appareils hors connexion ou n’ayant pas pu communiquer avec Intune ou Azure AD pour d’autres raisons.                                                                           | 5        |
| NotApplicable | Nombre d’appareils pour lesquels des stratégies de conformité ciblées par l’administrateur ne sont pas applicables.                                                                                     | 201      |
| Conforme     | Nombre d’appareils qui ont appliqué une ou plusieurs stratégies de conformité d’appareil ciblées par l’administrateur.                                                                        | 4083     |
| InGracePeriod | Nombre d’appareils qui ne sont pas conformes, mais se trouvent dans la période de grâce définie par l’administrateur.                                                                                  | 57       |
| NonCompliant  | Nombre d’appareils qui n’ont pas pu appliquer une ou plusieurs stratégies de conformité d’appareil ciblées par l’administrateur, ou dont l’utilisateur n’a pas respecté les stratégies ciblées par l’administrateur. | 43       |
|    Erreur      |    Nombre d’appareils qui n’ont pas pu communiquer avec Intune ou Azure AD et ont retourné un message d’erreur.                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
Le tableau suivant récapitule l’état d’affectation des stratégies de conformité pour les appareils par stratégie et par type de stratégie. Il répertorie le nombre d’appareils dans chaque état de conformité pour chaque stratégie de conformité affectée.

|      Propriété     |                                                                                      Description                                                                                     |  Exemple |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | Clé de date de la création du récapitulatif pour la stratégie de conformité.                                                                                                                   | 20161219 |
| PolicyKey         | Clé de la stratégie de conformité pour laquelle le récapitulatif a été créé.                                                                                                                   | 10178    |
| PolicyPlatformKey | Clé du type de plateforme de la stratégie de conformité pour laquelle le récapitulatif a été créé.                                                                                            | 5        |
| Unknown           | Nombre d’appareils hors connexion ou n’ayant pas pu communiquer avec Intune ou Azure AD pour d’autres raisons.                                                                           | 13       |
| NotApplicable     | Nombre d’appareils pour lesquels des stratégies de conformité ciblées par l’administrateur ne sont pas applicables.                                                                                     | 3        |
| Conforme         | Nombre d’appareils qui ont appliqué une ou plusieurs stratégies de conformité d’appareil ciblées par l’administrateur.                                                                        | 45       |
| InGracePeriod     | Nombre d’appareils qui ne sont pas conformes, mais se trouvent dans la période de grâce définie par l’administrateur.                                                                                  | 3        |
| NonCompliant      | Nombre d’appareils qui n’ont pas pu appliquer une ou plusieurs stratégies de conformité d’appareil ciblées par l’administrateur, ou dont l’utilisateur n’a pas respecté les stratégies ciblées par l’administrateur. | 7        |
| Erreur             | Nombre d’appareils qui n’ont pas pu communiquer avec Intune ou Azure AD et ont retourné un message d’erreur.                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      Propriété      |                       Description                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | État de conformité des appareils avec mdmStatusKey       |
| complianceStateKey | Clé de conformité pour faire correspondre l’appareil et l’état de conformité |
| complianceStateID  | L’ID pour correspondre à cet état de conformité                |

### <a name="example"></a>Exemple

|  complianceStatus  |                       Description                      |
|:------------------:|:------------------------------------------------------:|
|    Unknown         |    Inconnue.                                                                        |
|    Conforme       |    Conforme.                                                                      |
|    Non conforme    |       L’appareil n’est pas conforme et est bloqué par les ressources d’entreprise.             |
|    Conflict        |    Conflit avec d'autres règles.                                                      |
|    Erreur           |       Erreur.                                                                       |
|    ConfigManager   |    Géré par Configuration Manager.                                                      |
|    InGracePeriod   |       L’appareil n’est pas conforme, mais a toujours accès aux ressources d’entreprise.          |

## <a name="dates"></a>dates
L’entité **date** représente les dates référencées dans plusieurs entités de l’entrepôt de données.

|     Propriété    |                       Description                      |    Exemple    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | Identificateur unique pour cette date dans l’entrepôt de données. | 20160703      |
| FullDate        | Date représentée au format Date/Heure complet.        | 3/7/2016 0:00 |
| DayOfWeek       | Jour de la semaine                                            | 1             |
| DayOfMonth      | Jour du mois                                           | 3             |
| DayOfYear       | Jour de l’année                                            | 185           |
| WeekOfYear      | Semaine de l’année                                           | 28            |
| MonthOfYear     | Mois de l’année                                      | 7             |
| CalendarQuarter | Trimestre civil                                       | 3             |
| CalendarYear    | Année civile                                          | 2016          |
| DateKey         | Identificateur unique pour cette date dans l’entrepôt de données. | 20160703      |
| FullDate        | Date représentée au format Date/Heure complet.        | 3/7/2016 0:00 |
| DayOfWeek       | Jour de la semaine                                            | 1             |
| DayOfMonth      | Jour du mois                                           | 3             |
| DayOfYear       | Jour de l’année                                            | 185           |
| WeekOfYear      | Semaine de l’année                                           | 28            |
| MonthOfYear     | Mois de l’année                                      | 7             |
| CalendarQuarter | Trimestre civil                                       | 3             |
| CalendarYear    | Année civile                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      Propriété      |                                    Description                                   |                Exemple               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | Identificateur unique de la catégorie d’appareil.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | Identificateur unique de la catégorie d’appareil dans l’entrepôt de données (clé de substitution). | 1                                    |
| deviceCategoryName | Nom complet de la catégorie d'appareil.                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
L’entité **DeviceConfigurationProfileDeviceActivity** répertorie le nombre d’appareils, par jour, dans un état de réussite, d’attente, d’échec ou d’erreur. Le nombre reflète les profils de configuration d’appareil affectés à l’entité. Par exemple, si toutes les stratégies affectées à un appareil sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si deux profils sont affectés à un appareil, l’un dans un état de réussite et l’autre dans un état d’erreur, l’entité incrémente le compteur de réussite et affecte à l’appareil un état d’erreur. L’entité répertorie le nombre d’appareils dans chaque état pour un jour donné au cours des 30 derniers jours.

|  Propriété |                                          Description                                          |  Exemple |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | Clé de date qui indique quand l’enregistrement du profil de configuration de l’appareil a été enregistré dans l’entrepôt de données. | 20160703 |
| Pending   | Nombre d’appareils uniques en état d’attente.                                                    | 123      |
| Réussi | Nombre d’appareils uniques en état de réussite.                                                    | 12       |
| Erreur     | Nombre d’appareils uniques en état d’erreur.                                                      | 10       |
| Failed    | Nombre d’appareils uniques en état d’échec.                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
L’entité  **DeviceConfigurationProfileUserActivity**  répertorie le nombre quotidien d’utilisateurs dans un état de réussite, d’attente, d’échec ou d’erreur. Le nombre reflète les profils de configuration d’appareil affectés à l’entité. Par exemple, si toutes les stratégies affectées à un utilisateur sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si un utilisateur a deux profils affectés, l’un dans un état de réussite et l’autre dans un état d’erreur, l’utilisateur dans l’état d’erreur est pris en compte. L’entité  **DeviceConfigurationProfileUserActivity**  répertorie le nombre d’utilisateurs dans chaque état à une date donnée au cours des 30 derniers jours. 

| Propriété  | Description  | Exemple  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil est enregistré dans l’entrepôt de données.  | 20160703  |
| Pending  | Nombre d’utilisateurs uniques en état d’attente.  | 123  |
| Réussi  | Nombre d’utilisateurs uniques en état de réussite.  | 12  |
| Erreur  | Nombre d’utilisateurs uniques en état d’erreur.  | 10  |
| Failed  | Nombre d’utilisateurs uniques en état d’échec.  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          Propriété          |                                                                                      Description                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Référence à la table de dates indiquant le jour.                                                                                                                                          |
| DeviceKey                  | Identificateur unique de l’appareil dans l’entrepôt de données (clé de substitution). Il s’agit d’une référence à la table d’appareils qui contient l’ID d’appareil Intune.                               |
| DeviceName                 | Nom de l’appareil sur les plateformes qui autorisent à nommer un appareil. Sur d’autres plateformes, Intune crée un nom à partir d’autres propriétés. Cet attribut ne peut pas être disponible pour tous les appareils. |
| DeviceRegistrationStateKey | Clé de l’attribut d’état d’inscription pour cet appareil.                                                                                                                    |
| OwnerTypeKey               | Clé de l’attribut de type de propriétaire pour cet appareil : entreprise, personnel ou inconnu.                                                                                                  |
| ManagementStateKey         | Clé de l’état de gestion associé à cet appareil. Indique l’état le plus récent d’une action à distance ou si l’appareil a été jailbreaké/rooté.                                                |
| AzureADRegistered          | Indique si l’appareil est inscrit dans Azure Active Directory.                                                                                                                             |
| ComplianceStateKey         | Une clé pour ComplianceState.                                                                                                                                                            |
| OSVersion                  | Version de système d’exploitation.                                                                                                                                                                          |
| JailBroken                 | Indique si l’appareil est jailbreaké ou rooté.                                                                                                                                         |
| DeviceCategoryKey          | Clé de l’attribut de type d’appareil pour cet appareil.                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
L’entité **DeviceRegistrationState** représente le type d’inscription référencé par d’autres collections d’entrepôt de données. 

|           Propriété          |                                     Description                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | Identificateur unique de l’état d’inscription                                            |
| deviceRegistrationStateKey  | Identificateur unique de l’état d’inscription dans l’entrepôt de données (clé de substitution) |
| deviceRegistrationStateName | État d’inscription                                                                  |
|    NotRegistered                     |    Non inscrit                                                                                                                                                                  |
|    Inscrit                        |       Inscrit                                                                                                                                                                   |
|    Revoked                           |       Cet état signifie que l’administrateur informatique a bloqué le client et que ce dernier peut être débloqué. Un appareil peut également être dans l’état Révoqué après une réinitialisation ou une mise hors service.        |
|    KeyConflict                       |    Conflit de clé                                                                                                                                                                    |
|    ApprovalPending                   |    Approbation en attente                                                                                                                                                                |
|    CertificateReset                  |    Réinitialiser le certificat                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    Non inscrit, inscription en attente                                                                                                                                               |
|    Unknown                           |    État inconnu                                                                                                                                                                   |

## <a name="devices"></a>périphériques
L’entité **device** répertorie tous les appareils inscrits à la gestion et leurs propriétés correspondantes.

|          Propriété          |                                                                                       Description                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Identificateur unique de l’appareil dans l’entrepôt de données (clé de substitution).                                                                                                               |
| DeviceId                   | Identificateur unique de l’appareil.                                                                                                                                                     |
| DeviceName                 | Nom de l’appareil sur les plateformes qui autorisent à nommer un appareil. Sur d’autres plateformes, Intune crée un nom à partir d’autres propriétés. Cet attribut ne peut pas être disponible pour tous les appareils. |
| DeviceTypeKey              | Clé de l’attribut de type d’appareil pour cet appareil.                                                                                                                                    |
| DeviceRegistrationState    | Clé de l’attribut d’état d’inscription du client pour cet appareil.                                                                                                                      |
| OwnerTypeKey               | Clé de l’attribut de type de propriétaire pour cet appareil : entreprise, personnel ou inconnu.                                                                                                    |
| EnrolledDateTime           | Date et heure de l’inscription de l’appareil.                                                                                                                                         |
| LastSyncDateTime           | Dernier enregistrement connu de l’appareil auprès d’Intune.                                                                                                                                              |
| ManagementAgentKey         | Clé de l’agent de gestion associé à cet appareil.                                                                                                                             |
| ManagementStateKey         | Clé de l’état de gestion associé à cet appareil. Indique l’état le plus récent d’une action à distance ou si l’appareil a été jailbreaké/rooté.                                                |
| AzureADDeviceId            | ID d’appareil Azure pour cet appareil.                                                                                                                                                  |
| AzureADRegistered          | Indique si l’appareil est inscrit dans Azure Active Directory.                                                                                                                             |
| DeviceCategoryKey          | Clé de l’agent de la catégorie associée à cet appareil.                                                                                                                                     |
| DeviceEnrollmentType       | Clé du type d’inscription associé à cet appareil. Indique la méthode d’inscription.                                                                                             |
| ComplianceStateKey         | Clé de l’état de conformité associée à cet appareil.                                                                                                                             |
| OSVersion                  | Version du système d’exploitation de l’appareil.                                                                                                                                                |
| EasDeviceId                | Identificateur Exchange ActiveSync de l’appareil.                                                                                                                                                  |
| SerialNumber               | SerialNumber                                                                                                                                                                           |
| UserId                     | Identificateur unique de l’utilisateur associé à l’appareil.                                                                                                                           |
| RowLastModifiedDateTimeUTC | Date et heure UTC de la dernière modification de cet appareil dans l’entrepôt de données.                                                                                                       |
| Fabricant               | Fabricant de l’appareil                                                                                                                                                             |
| Modèle                      | Modèle de l’appareil                                                                                                                                                                    |
| OperatingSystem            | Système d’exploitation de l’appareil. Windows, iOS,   etc.                                                                                                                                   |
| IsDeleted                  | Binaire pour indiquer si l’appareil est supprimé ou non.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Niveau des correctifs de sécurité Android                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| IsSupervised               | État de supervision de l’appareil                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Stockage disponible en octets.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Stockage total en octets.                                                                                                                                                                |
| EncryptionState            | État de chiffrement de l’appareil.                                                                                                                                                      |
| SubscriberCarrier          | Opérateur de l’abonné de l’appareil                                                                                                                                                       |
| PhoneNumber                | Numéro de téléphone de l’appareil                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Technologie cellulaire de l’appareil                                                                                                                                                    |
| WiFiMacAddress             | Adresse MAC du réseau Wi-Fi                                                                                                                                                                              |


## <a name="devicetypes"></a>DeviceTypes
L’entité **deviceTypes** représente le type d’appareil référencé par d’autres entités de l’entrepôt de données. Le type d’appareil décrit généralement le modèle de l’appareil, son fabricant ou une combinaison des deux.

|    Propriété    |                                  Description                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | Identificateur unique du type d’appareil                                       |
| DeviceTypeKey  | Identificateur unique du type d’appareil dans l’entrepôt de données (clé de substitution) |
| DeviceTypeName | Type d'appareil                                                                |

### <a name="example"></a>Exemple

| deviceTypeID |        Nom       |                      Description                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | Non disponible   | Le type d’appareil n’est pas disponible.                     |
| 0            | Bureau           | Appareil Windows Desktop                              |
| 1            | Windows           | Appareil Windows                                      |
| 2            | WinMO6            | Appareil Windows Mobile 6.0                           |
| 3            | Nokia             | Appareil Nokia                                        |
| 4            | WindowsPhone      | Appareil Windows Phone                                |
| 5            | Mac               | Appareil Mac                                          |
| 6            | WinCE             | Appareil Windows CE                                   |
| 7            | WinEmbedded       | Appareil Windows Embedded                             |
| 8            | IPhone            | Appareil iPhone                                       |
| 9            | IPad              | Appareil iPad                                         |
| 10           | IPod              | Appareil iPod                                         |
| 11           | Android           | Appareil Android géré à l’aide de l’administrateur d’appareil   |
| 12           | ISocConsumer      | Appareil iSoc grand public                                |
| 13           | Unix              | Appareil Unix                                         |
| 14           | MacMDM            | Appareil Mac OS X géré avec l’agent GPM intégré |
| 15           | HoloLens          | Appareil HoloLens                                    |
| 16           | SurfaceHub        | Appareil Surface Hub                                  |
| 17           | AndroidForWork    | Appareil Android géré à l’aide du propriétaire de profil Android  |
| 18           | AndroidEnterprise | Appareil Android Entreprise.                          |
| 100          | Blackberry        | Appareil Blackberry                                   |
| 101          | Palm              | Appareil Palm                                         |
| 255          | Unknown           | Type d’appareil inconnu                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
L’entité **deviceEnrollmentType** indique la façon dont un appareil a été inscrit. Le type d’inscription capture la méthode d’inscription. Les exemples répertorient les différents types d’inscription et leur signification.

|         Propriété         |                                    Description                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | Identificateur unique du type d’inscription.                                       |
| deviceEnrollmentTypeKey  | Identificateur unique du type d’inscription dans l’entrepôt de données (clé de substitution). |
| deviceEnrollmentTypeName | Nom du type d'inscription.                                                           |

### <a name="example"></a>Exemple

| enrollmentTypeID |                Nom                |                                        Description                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Unknown                            | Le type d’inscription n’a pas été collecté                                                      |
| 1                | UserEnrollment                     | Inscription pilotée par l’utilisateur via le canal BYOD.                                           |
| 2                | DeviceEnrollmentManager            | Inscription d’un utilisateur avec un compte de gestionnaire d’inscription des appareils.                              |
| 3                | AppleBulkWithUser                  | Inscription en bloc Apple avec demande d’accès utilisateur. (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | Inscription en bloc Apple sans demande d’accès utilisateur.   (DEP, Apple Configurator, Mobile Config) |
| 5                | WindowsAzureADJoin                 | Jonction Windows 10 Azure AD.                                                                |
| 6                | WindowsBulkUserless                | Inscription en bloc Windows 10 Bulk via ICD avec certificat.                               |
| 7                | WindowsAutoEnrollment              | Inscription automatique Windows 10.   (Ajouter un compte professionnel)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Jonction Azure AD en bloc sur Windows 10.                                                           |
| 9                | WindowsCoManagement                | Cogestion sur Windows 10 déclenchée par AutoPilot ou par une stratégie de groupe.                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | Jonction d’Azure AD sur Windows 10 avec autorisation de l’appareil.                                            |


## <a name="intunemanagementextensions"></a>intuneManagementExtensions
**intuneManagementExtension** répertorie l’intégrité d’**intuneManagementExtension** sur chaque appareil Windows 10 par jour. Les données sont conservées pendant les 60 derniers jours.

|       Propriété      |                          Description                          | Exemple |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | Identificateur unique de la date.                                | 123     |
| TenantKey           | Identificateur unique du locataire.                              | 456     |
| DeviceKey           | Identificateur unique de l’appareil.                              | 789 %     |
| ExtensionVersionKey | Identificateur unique de la version IntuneManagementExtension. | 1       |
| ExtensionStateKey   | Identificateur unique de l’état d’intégrité.                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
**IntuneManagementExtensionHealthState** répertorie tous les états d’intégrité possibles d’**IntuneManagementExtension**.

|      Propriété     |                   Description                  | Exemple |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | Identificateur unique de l’état d’intégrité.           | 2       |
| ExtensionState    | État d’intégrité d’IntuneManagementExtension. | Healthy |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
L’entité **IntuneManagementExtensionVersion** répertorie toutes les versions utilisées par **IntuneManagementExtension**.

|       Propriété      |                          Description                          | Exemple |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | Identificateur unique de la version IntuneManagementExtension. | 1       |
| ExtensionVersion    | Numéro de version à quatre chiffres.                                   | 1.0.2.0 |

## <a name="managementagenttypes"></a>managementAgentTypes
L’entité **ManagementAgentTypes** représente les agents utilisés pour gérer un appareil.

|         Propriété        |                                       Description                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | Identificateur unique du type d’agent de gestion.                                         |
| ManagementAgentTypeKey  | Identificateur unique du type d’agent de gestion dans l’entrepôt de données (clé de substitution). |
| ManagementAgentTypeName | Indique le type d’agent utilisé pour gérer l’appareil                              |

### <a name="example"></a>Exemple

| ManagementAgentTypeID |                Nom               |                                  Description                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | L’appareil est géré par le biais d’Exchange Active Sync.                         |
| 2                     | GESTION DES APPAREILS MOBILES                               | L’appareil est géré à l’aide d’un agent GPM.                                   |
| 3                     | EasMdm                            | L’appareil est géré à la fois par Exchange Active Sync et par un agent GPM.        |
| 4                     | IntuneClient                      | L’appareil est géré par l’agent Intune PC.                               |
| 5                     | EasIntuneClient                   | L’appareil est géré à la fois par Exchange Active Sync et par l’agent Intune PC. |
| 8                     | ConfigManagerClient               | L’appareil est géré par l’agent System Center Configuration Manager.     |
| 10                    | ConfigurationManagerClientMdm     | L’appareil est géré par Configuration Manager et par GPM.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | L’appareil est géré par Configuration Manager, GPM et Eas.               |
| 16                    | Unknown                           | Type d’agent de gestion inconnu                                              |
| 32                    | Jamf                              | Les attributs des appareils sont extraits de Jamf.                               |
| 64                    | GoogleCloudDevicePolicyController |  L’appareil est géré par les CloudDPC de Google.                                 |

## <a name="managementstates"></a>managementStates
L’entité **ManagementStates** fournit des détails sur l’état de l’appareil. Ces informations peuvent être utiles si des actions à distance sont appliquées ou si l’appareil est jailbreaké ou rooté.

|       Propriété      |                                     Description                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | Identificateur unique de l’état de gestion.                                       |
| managementStateKey  | Identificateur unique de l’état de gestion dans l’entrepôt de données (clé de substitution). |
| managementStateName | Indique l’état de l’action à distance appliquée à cet appareil.                 |

### <a name="example"></a>Exemple

| managementStateID |      Nom      |                                                   Description                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | Géré        | Géré sans action à distance en attente.                                                                       |
| 1                 | RetirePending  | Commande de mise hors service en attente pour l’appareil.                                                             |
| 2                 | RetireFailed   | Échec de la commande de mise hors service sur l’appareil.                                                                      |
| 3                 | WipePending    | Commande de réinitialisation en attente pour l’appareil.                                                               |
| 4                 | WipeFailed     | Échec de la commande de réinitialisation sur l’appareil.                                                                        |
| 5                 | Unhealthy      | État non sain.                                                                                              |
| 6                 | En attente de suppression  | Commande de suppression en attente pour l’appareil.                                                             |
| 7                 | RetireIssued   | Commande de mise hors service émise pour l’appareil.                                                               |
| 8                 | WipeIssued     | Commande de réinitialisation émise.                                                                               |
| 9                 | WipeCanceled   | Commande de réinitialisation annulée.                                                                               |
| 10                | RetireCanceled | Commande de mise hors service annulée.                                                                             |
| 11                | Discovered     | L’appareil a été récemment découvert par Intune. Une fois le premier enregistrement terminé, il passe à l’état Managé. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
L’entité MobileAppInstallState représente l’état d’installation d’une application mobile après qu’elle a été affectée à un groupe contenant des appareils, des utilisateurs ou les deux.

|       Propriété      |                        Description                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | ID unique de l’état d’installation de l’application pour votre compte. |
| AppInstallState     | Valeur d’énumération de l’état d’installation de l’application.                     |
| AppInstallStateName | Nom de l’état d’installation de l’application.                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
Représente l’état d’installation d’une application mobile pour un type d’appareil cible à l’aide de la gestion des applications mobiles via Microsoft Intune.

|      Propriété      |                                                          Description                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | Clé de la date à laquelle l’état d’installation d’une application a été enregistré.                                                                     |
| AppKey             | Clé de l’application mobile utilisée pour identifier une instance AppRevision.                                                          |
| DeviceTypeKey      | Clé du Type d’appareil associé à l’application mobile.                                                              |
| AppInstallStateKey | Clé de l’état d’installation de l’application utilisée pour identifier une instance de MobileAppInstallState.                                         |
| Code d'erreur          | Le code d’erreur retourné par le programme d’installation de l’application, la plateforme mobile ou le service lié à l’installation de l’application. |
| Count              | Nombre total.                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
L’entité **ownerType** indique si un appareil est un appareil d’entreprise, personnel ou inconnu.

|    Propriété   |                                                                                     Description                                                                                    |           Exemple          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | Identificateur unique du type de propriétaire.                                                                                                                                               |                            |
| ownerTypeKey  | Identificateur unique du type de propriétaire dans l’entrepôt de données (clé de substitution).                                                                                                       |                            |
| ownerTypeName | Représente le type de propriétaire des appareils. Entreprise : l’appareil appartient à l’entreprise.  Personnel : il s’agit d’un appareil personnel (BYOD).   Inconnu : aucune information sur cet appareil n’est disponible. | Entreprise Personnel Inconnu |

## <a name="policies"></a>stratégies
L’entité **Policy** répertorie les profils de configuration d’appareil, les profils de configuration d’application et les profils de conformité. Vous pouvez affecter les stratégies à un groupe de votre entreprise à l’aide de la gestion des appareils mobiles (MDM).

|          Propriété          |                                                                       Description                                                                      |                Exemple               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | Clé unique représentant la stratégie dans l’entrepôt de données.                                                                                              | 123                                  |
| PolicyId                   | Identificateur unique de la stratégie dans l’entrepôt de données.                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | Nom de la stratégie.                                                                                                                                    | « Ligne de base Windows 10 »                |
| PolicyVersion              | Version de la stratégie. Quand la stratégie est modifiée, une version plus récente est créée.                                                             | 1, 2, 3                              |
| IsDeleted                  | Indique si l’enregistrement de stratégie a été mis à jour.  True : la stratégie a un nouvel enregistrement avec des champs mis à jour.  False : dernier enregistrement de la stratégie. | Vrai/Faux                           |
| StartDateInclusiveUTC      | Date et heure UTC de création de la stratégie dans l’entrepôt de données.                                                                              | 23/11/2016 0:00                      |
| DeletedDateUTC             | Date et heure UTC de l’affectation de la valeur True à IsDeleted.                                                                                                   | 23/11/2016 0:00                      |
| RowLastModifiedDateTimeUTC | Date et heure UTC de la dernière modification de la stratégie dans l’entrepôt de données.                                                                        | 23/11/2016 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
Le tableau suivant répertorie le nombre d’appareils, par jour, dans un état de réussite, d’attente, d’échec ou d’erreur. Le nombre reflète les données par profil de type de stratégie. Par exemple, si toutes les stratégies affectées à un appareil sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si deux profils sont affectés à un appareil, l’un dans un état de réussite et l’autre dans un état d’erreur, l’entité incrémente le compteur de réussite et affecte à l’appareil un état d’erreur. L’entité **policyDeviceActivity** répertorie le nombre d’appareils dans chaque état à une date donnée au cours des 30 derniers jours.

|  Propriété |                                           Description                                           |        Exemple        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil a été enregistré dans l’entrepôt de données. | 20160703              |
| Pending   | Nombre d’appareils uniques en état d’attente.                                                    | 123                   |
| Réussi | Nombre d’appareils uniques en état de réussite.                                                    | 12                    |
| PolicyKey | Clé de stratégie pouvant être jointe à la stratégie pour obtenir le nom de l’entité policyName.                                  | Ligne de base Windows 10 |
| Erreur     | Nombre d’appareils uniques en état d’erreur.                                                      | 10                    |
| Failed    | Nombre d’appareils uniques en état d’échec.                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        Propriété        |                      Description                      |     Exemple    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | Clé unique du type de plateforme de stratégie.        | 20170519       |
| PolicyPlatformTypeId   | Identificateur unique du type de plateforme de stratégie. | 1              |
| PolicyPlatformTypeName | Nom du type de plateforme de stratégie.              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
L’entité **PolicyTypeActivity** répertorie le nombre cumulé d’appareils dans un état de réussite, d’attente, d’échec ou d’erreur. Elle répertorie ces états, par jour, par rapport à un profil de configuration d’appareil, un profil de configuration d’application ou une stratégie de conformité.

|    Propriété   |                                          Description                                          |           Exemple           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | Clé de date qui indique quand l’enregistrement du profil de configuration d’appareil a été enregistré dans l’entrepôt de données. | 20160703                    |
| PolicyKey     | Clé de stratégie pouvant être jointe à la stratégie pour obtenir le nom de l’entité policyName.                                | Ligne de base Windows 10         |
| PolicyTypeKey | Type de clé de stratégie pouvant être joint au type de stratégie pour obtenir le nom du type de la stratégie.             | Stratégie de conformité Windows 10 |
| Pending       | Nombre d’appareils uniques en état d’attente.                                                    | 123                         |
| Réussi     | Nombre d’appareils uniques en état de réussite.                                                    | 12                          |
| Erreur         | Nombre d’appareils uniques en état d’erreur.                                                      | 10                          |
| Failed        | Nombre d’appareils uniques en état d’échec.                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
L’entité **PolicyType** répertorie les types de profils de configuration d’appareil, de profils de configuration d’application et de profils de conformité. Vous pouvez affecter les stratégies à un groupe de votre entreprise à l’aide de la gestion des appareils mobiles (MDM).

|    Propriété    |                       Description                      |            Exemple            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | Identificateur unique de la stratégie dans le système source.  | 123                           |
| PolicyTypeKey  | Identificateur unique de la stratégie dans l’entrepôt de données. | 1                             |
| PolicyTypeName | Nom du type de stratégie                               | Stratégie de conformité Windows 10. |

## <a name="policyuseractivities"></a>policyUserActivities
Le tableau suivant répertorie le nombre d’utilisateurs, par jour, dans un état de réussite, d’attente, d’échec ou d’erreur. Le nombre reflète les données par profil de type de stratégie. Par exemple, si toutes les stratégies affectées à un utilisateur sont dans un état de réussite, le compteur de réussite augmente d’une unité pour ce jour-là. Si un utilisateur a deux profils affectés, l’un dans un état de réussite et l’autre dans un état d’erreur, l’utilisateur dans l’état d’erreur est pris en compte. L’entité **PolicyUserActivity** répertorie le nombre d’utilisateurs dans chaque état à une date donnée au cours des 30 derniers jours.

|  Propriété |                                          Description                                          |       Exemple       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | Clé de date qui indique quand l’enregistrement du profil de configuration de l’appareil a été enregistré dans l’entrepôt de données. | 20160703            |
| Pending   | Nombre d’appareils uniques en état d’attente.                                                    | 123                 |
| Réussi | Nombre d’appareils uniques en état de réussite.                                                    | 12                  |
| PolicyKey | Clé de stratégie pouvant être jointe à la stratégie pour obtenir le nom de l’entité policyName.                                | Ligne de base Windows 10 |
| Erreur     | Nombre d’appareils uniques en état d’erreur.                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
Une entité **termsAndConditions** représente les métadonnées et le contenu d’une stratégie donnée de Conditions générales. Les contenus des stratégies de conditions générales sont présentés aux utilisateurs lors de leur première tentative d’inscription à Intune et, par la suite, lors des modifications où un administrateur a demandé une nouvelle acceptation. Ils permettent aux administrateurs de communiquer les dispositions qu’un utilisateur doit accepter pour que les appareils soient inscrits dans Intune.

|    Propriété        |    Description    |    Exemple        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    Une clé correspondant à une entrée dans la collection 'userTermsAndConditionsAcceptances'    |    123    |
|    termsAndCondidionsId    |    L’ID pour cette entrée termsAndConditions    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    La version de cette entrée de conditions générales    |    1    |
|    name    |    Le nom de cette entrée termsAndConditions.        |    Conditions d’utilisation d’Intune     |
|    description    |    La description de ces conditions générales.     |         |
|    title    |    Le titre de ces conditions générales.     |    Stratégie d’entreprise pour la gestion des appareils        |
|    summaryOfTerms    |    Le résumé des termes du contrat donné à l’utilisateur.     |    J'accepte les conditions générales.    |
|    termsAndConditionsBodyText    |    Le corps de texte de ces conditions générales.       |    * Chiffrement de l’appareil * Mise en œuvre d’un code confidentiel de 6 chiffres    |
|    isDeleted    |    Valeur True ou false pour indique si cette valeur est supprimée.     |    False    |
|    startDateInclusiveUTC    |    La date de début de ces conditions générales.     |    23/8/2018 4:01:34    |
|    endDateEclusiveUTC    |    La date de fin de ces conditions générales.     |    31/12/9999 00:00:00    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
L’entité **UserDeviceAssociation** contient les associations appareil-utilisateur dans votre organisation.

|        Nom        |                                             Description                                            |     Exemple     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | Identificateur unique de l’utilisateur dans l’entrepôt de données.   (Clé de substitution).                            | 123             |
| DeviceKey          | Identificateur unique de l’appareil dans l’entrepôt de données.                                             | 123             |
| CreatedDateTimeUTC | Date et heure auxquelles l’association appareil-utilisateur a été créée. Utilise le format UTC.                     | 23/11/2016 0:00 |
| IsDeleted          | Indique que l’utilisateur a désinscrit cet appareil et que l’association n’est plus d’actualité. | Vrai/Faux      |
| EndedDateTimeUTC   | Date et heure UTC de l’affectation de la valeur True à IsDeleted.                                               | 23/6/2017 0:00  |

## <a name="users"></a>utilisateurs
L’entité **user** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise.

La collection d’entités **user** contient les données des utilisateurs. Parmi ces enregistrements figurent les états utilisateurs de la période de collecte de données, même si l’utilisateur a été supprimé. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données du mois précédent. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

|          Propriété          |                                                                                                           Description                                                                                                          |                Exemple               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Identificateur unique de l’utilisateur dans l’entrepôt de données (clé de substitution).                                                                                                                                                         | 123                                  |
| UserId                     | Identificateur unique de l’utilisateur (semblable à UserKey, sauf qu’il s’agit d’une clé naturelle).                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | Adresse e-mail de l’utilisateur.                                                                                                                                                                                                     | John@constoso.com                    |
| UPN                        | Nom d'utilisateur principal de l'utilisateur.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Nom d’affichage de l’utilisateur.                                                                                                                                                                                                      | Jean                                 |
| IntuneLicensed             | Spécifie si cet utilisateur dispose d’une licence Intune ou non.                                                                                                                                                                              | Vrai/Faux                           |
| IsDeleted                  | Indique si toutes les licences de l’utilisateur ont expiré et si ce dernier a, de ce fait, été supprimé d’Intune. Pour un enregistrement unique, cet indicateur ne change pas. En revanche, un autre enregistrement est créé pour le nouvel état de l’utilisateur. | Vrai/Faux                           |
| RowLastModifiedDateTimeUTC | Date et heure UTC de la dernière modification de l’enregistrement dans l’entrepôt de données                                                                                                                                                 | 23/11/2016 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
Une entité **userTermsAndConditionsAcceptance** représente l’état d’acceptation d’une stratégie de conditions d’utilisation donnée par un utilisateur donné. Les utilisateurs doivent accepter la version la plus récente des termes du contrat pour conserver l’accès au portail d’entreprise.

|    Propriété    |    Description    |    Exemple    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    Une clé correspondant aux valeurs d’une date dans la collection « dates ».     |    20180823    |
|    UserKey    |    Une clé d’utilisateur mappée à un utilisateur dans la collection « utilisateurs ».     |    20000    |
|    termsAndConditionsKey    |    Une clé correspondant à une entrée dans la collection « termsAndConditions »    |    1    |
|    acceptedDateTimeUTC    |    L’heure à laquelle l’utilisateur a accepté les conditions d’utilisation    |    23/8/2018 4:01:34    |
|    lastModifiedDateTimeUTC    |    Heure de la dernière modification apportée à l’entrée.     |    23/8/2018 4:01:34    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
L’entité **VppProgramTypes** répertorie les types de VPP possibles pour une application.

|      Propriété      |          Description         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | ID du type.           |
| VppProgramTypeKey  | Clé de substitution pour la clé. |
| VppProgramTypeName | Type de programme VPP.          |

### <a name="example"></a>Exemple

|             VppProgramID             |         Nom        | Description                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Programme VPP Microsoft. |
| 00000000-0000-0000-0000-000000000000 | Pas encore disponible | Valeur par défaut : aucun VPP.   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Programme VPP Apple.     |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur Intune Data Warehouse, consultez [modèle de données Data Warehouse](https://docs.microsoft.com/intune/reports-ref-data-model).

