---
title: 'Appareils : Entrepôt de données Intune'
titleSuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Appareils de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: c361c6054cf52c802155587084eaea76e024f78c
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429180"
---
# <a name="reference-for-devices-entities"></a>Référence pour les entités d’appareils

La catégorie **Appareils** contient des entités pour appareils mobiles qui font le suivi d’informations, notamment les suivantes :

  -  Type d'appareil
  -  État de l’inscription des appareils
  -  Propriété des appareils
  -  État de la gestion des appareils
  -  État de l’appartenance des appareils à Azure AD
  -  État de l'inscription
  -  Informations d’historique sur l’appareil
  -  Inventaire des applications sur l’appareil

## <a name="devicetypes"></a>DeviceTypes

L’entité **DeviceTypes** représente le type d’appareil référencé par d’autres entités d’entrepôt de données. Le type d’appareil décrit généralement le modèle de l’appareil, son fabricant ou une combinaison des deux.

| Propriété  | Description |
|---------|------------|
| DeviceTypeID |Identificateur unique du type d’appareil |
| DeviceTypeKey |Identificateur unique du type d’appareil dans l’entrepôt de données (clé de substitution) |
| DeviceTypeName |Type d'appareil |

### <a name="example"></a>Exemple

| deviceTypeID  | Nom | Description |
|---------|------------|--------|
| 0 |Bureau |Appareil Windows Desktop |
| 1 |WindowsRT |Appareil Windows RT |
| 2 |WinMO6 |Appareil Windows Mobile 6.0 |
| 3 |Nokia |Appareil Nokia |
| 4 |WindowsPhone |Appareil Windows Phone |
| 5 |Mac |Appareil Mac |
| 6 |WinCE |Appareil Windows CE |
| 7 |WinEmbedded |Appareil Windows Embedded |
| 8 |IPhone |Appareil iPhone |
| 9 |IPad |Appareil iPad |
| 10 |IPod |Appareil iPod |
| 11 |Android |Appareil Android géré à l’aide de l’Administrateur d’appareil |
| 12 |ISocConsumer |Appareil grand public iSoc |
| 14 |MacMDM |Appareil Mac OS X géré avec l’agent MDM intégré |
| 15 |HoloLens |Appareils HoloLens |
| 16 |SurfaceHub |Appareil Surface Hub |
| 17 |AndroidForWork |Appareil Android géré à l’aide du Propriétaire de profil Android |
| 100 |Blackberry |Appareil Blackberry |
| 101 |Palm |Appareil Palm |
| 255 |Unknown |Type d’appareil inconnu |

## <a name="enrollmentactivities"></a>enrollmentActivities 
L’entité **EnrollmentActivity** indique l’activité d’une inscription d’appareil.

| Propriété                      | Description                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Clé de la date d’enregistrement de cette activité d’inscription.               |
| deviceEnrollmentTypeKey       | Clé du type de l’inscription.                                        |
| deviceTypeKey                 | Clé du type d’appareil.                                                |
| enrollmentEventStatusKey      | Clé de l’état indiquant la réussite ou l’échec de l’inscription.    |
| enrollmentFailureCategoryKey  | Clé de la catégorie d’échec d’inscription (en cas d’échec de l’inscription).        |
| enrollmentFailureReasonKey    | Clé de la raison de l’échec d’inscription (en cas d’échec de l’inscription).          |
| osVersion                     | Version du système d’exploitation de l’appareil.                               |
| count                         | Nombre total d’activités d’inscription correspondant aux classifications ci-dessus.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
L’entité **EnrollmentEventStatus** indique le résultat d’une inscription d’appareil.

| Propriété                   | Description                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Identificateur unique de l’état d’inscription dans l’entrepôt de données (clé de substitution).  |
| enrollmentEventStatusName  | Nom de l’état d’inscription. Voir les exemples ci-dessous.                            |

### <a name="example"></a>Exemple

| enrollmentEventStatusName  | Description                            |
|----------------------------|----------------------------------------|
| Opération réussie                    | Une inscription d’appareil ayant réussi         |
| Failed                     | Une inscription d’appareil ayant échoué             |
| Non disponible              | L’état de l’inscription n’est pas disponible.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
L’entité **EnrollmentFailureCategory** indique pourquoi une inscription d’appareil a échoué. 

| Propriété                       | Description                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Identificateur unique de la catégorie d’échec d’inscription dans l’entrepôt de données (clé de substitution).  |
| enrollmentFailureCategoryName  | Nom de la catégorie d’échec d’inscription. Voir les exemples ci-dessous.                            |

### <a name="example"></a>Exemple

| enrollmentFailureCategoryName   | Description                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Non applicable                  | La catégorie d’échec d’inscription n’est pas applicable.                                                            |
| Non disponible                   | La catégorie d’échec d’inscription n’est pas disponible.                                                             |
| Unknown                         | Erreur inconnue.                                                                                                |
| Authentification                  | Échec de l’authentification.                                                                                        |
| Autorisation                   | L’appel a été authentifié, mais l’inscription n’a pas été autorisée.                                                         |
| AccountValidation               | Impossible de valider le compte pour l’inscription. (Compte bloqué, inscription non activée)                      |
| UserValidation                  | Impossible de valider l’utilisateur. (L’utilisateur n’existe pas, absence de licence)                                           |
| DeviceNotSupported              | L’appareil n’est pas pris en charge pour la gestion des appareils mobiles.                                                         |
| InMaintenance                   | Le compte est en maintenance.                                                                                    |
| BadRequest                      | Le client a envoyé une requête qui n’est pas comprise/prise en charge par le service.                                        |
| FeatureNotSupported             | Les fonctionnalités utilisées par cette inscription ne sont pas prises en charge pour ce compte.                                        |
| EnrollmentRestrictionsEnforced  | Des restrictions d’inscription configurées par l’administrateur ont bloqué l’inscription.                                          |
| ClientDisconnected              | Le délai d’attente du client a expiré ou l’inscription a été abandonnée par l’utilisateur final.                                                        |
| UserAbandonment                 | L’inscription a été abandonnée par l’utilisateur final. (L’utilisateur final a commencé l’intégration mais ne l’a pas terminée en temps voulu)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
L’entité **EnrollmentFailureReason** indique une raison plus détaillée pour un échec d’inscription d’appareil au sein d’une catégorie d’échec donnée.  

| Propriété                     | Description                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Identificateur unique de la raison de l’échec d’inscription dans l’entrepôt de données (clé de substitution).  |
| enrollmentFailureReasonName  | Nom de la raison de l’échec d’inscription. Voir les exemples ci-dessous.                            |

### <a name="example"></a>Exemple

| enrollmentFailureReasonName      | Description                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Non applicable                   | La raison de l’échec d’inscription n’est pas applicable.                                                                                                                                                       |
| Non disponible                    | La raison de l’échec d’inscription n’est pas disponible.                                                                                                                                                        |
| Unknown                          | Erreur inconnue.                                                                                                                                                                                         |
| UserNotLicensed                  | L’utilisateur est introuvable dans Intune ou ne dispose pas d’une licence valide.                                                                                                                                     |
| UserUnknown                      | Intune ne connaît pas l’utilisateur.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Un seul utilisateur peut inscrire un appareil. Cet appareil a déjà été inscrit par un autre utilisateur.                                                                                                                |
| EnrollmentOnboardingIssue        | Aucune autorité de gestion des appareils mobiles (MDM) Intune n’a encore été configurée.                                                                                                                                 |
| AppleChallengeIssue              | L’installation du profil de gestion iOS a été retardée ou a échoué.                                                                                                                                         |
| AppleOnboardingIssue             | Un certificat Push MDM Apple est nécessaire pour l’inscription dans Intune.                                                                                                                                       |
| DeviceCap                        | L’utilisateur a tenté d’inscrire plus d’appareils que la quantité maximale autorisée.                                                                                                                                        |
| AuthenticationRequirementNotMet  | Le service d’inscription Intune n’a pas pu autoriser cette requête.                                                                                                                                            |
| UnsupportedDeviceType            | Cet appareil ne répond pas aux exigences minimales de l’inscription à Intune.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | Échec de l’inscription de cet appareil en raison d’une règle de restriction d’inscription configurée.                                                                                                                          |
| BulkDeviceNotPreregistered       | Le numéro de série ou numéro IMEI (International Mobile Equipment Identifier) de cet appareil est introuvable.  Sans cet identificateur, les appareils sont identifiés comme des appareils personnels actuellement bloqués.  |
| FeatureNotSupported              | L’utilisateur a tenté d’accéder à une fonctionnalité qui n’a pas encore été publiée pour tous les clients ou n’est pas compatible avec votre configuration Intune.                                                            |
| UserAbandonment                  | L’inscription a été abandonnée par l’utilisateur final. (L’utilisateur final a commencé l’intégration mais ne l’a pas terminée en temps voulu)                                                                                           |
| APNSCertificateExpired           | Les appareils Apple ne peuvent pas être gérés avec un certificat Push MDM Apple ayant expiré.                                                                                                                            |
## <a name="ownertypes"></a>OwnerTypes

L’entité **EnrollmentTypes** indique si un appareil est un appareil d’entreprise, personnel ou inconnu.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| ownerTypeID |Identificateur unique du type de propriétaire. | |
| ownerTypeKey |Identificateur unique du type de propriétaire dans l’entrepôt de données (clé de substitution). | |
| ownerTypeName |Représente le type de propriétaire des appareils :  <br>Entreprise - appareil est appartient à l’entreprise. <br>Personnel : il s’agit d’un appareil personnel (BYOD).  <br>Inconnu : aucune information n’est disponible sur cet appareil. |Entreprise personnel inconnu |

> [!Note]  
> Pour le `ownerTypeName` dans Azure AD lors de la création de groupes dynamiques pour les appareils, vous devez définir la valeur de filtre `deviceOwnership` comme `Company`. Pour plus d’informations, consultez [règles pour les appareils](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="managementstates"></a>ManagementStates

L’entité **ManagementStates** fournit des détails sur l’état de l’appareil. Ces informations peuvent être utiles si des actions à distance sont appliquées ou si l’appareil est jailbreaké ou rooté.

| Propriété  | Description |
|---------|------------|
| managementStateID | Identificateur unique de l’état de gestion |
| managementStateKey | Identificateur unique de l’état de gestion dans l’entrepôt de données (clé de substitution) |
| managementStateName | Indique l’état de l’action à distance appliquée à cet appareil |

### <a name="example"></a>Exemple

| managementStateID  | Nom | Description |
|---------|------------|--------|
| 0 |Géré | Géré sans action à distance en attente. |
| 1 |RetirePending | Commande de mise hors service en attente pour l’appareil. |
| 2 |RetireFailed | Échec de la commande de mise hors service sur l’appareil. |
| 3 |WipePending | Commande de réinitialisation en attente pour l’appareil. |
| 4 |WipeFailed | Échec de la commande de réinitialisation sur l’appareil. |
| 5 |Unhealthy | État non sain. |
| 6 |En attente de suppression | Commande de suppression en attente pour l’appareil. |
| 7 |RetireIssued | Commande de mise hors service émise pour l’appareil. |
| 8 |WipeIssued | Commande de réinitialisation émise. |
| 9 |WipeCanceled | Commande de réinitialisation annulée. |
| 10 |RetireCanceled | Commande de mise hors service annulée. |
| 11 |Discovered | L’appareil a été récemment découvert par Intune. Une fois le premier enregistrement terminé, il passe à l’état Managed. |

## <a name="managementagenttypes"></a>ManagementAgentTypes

L’entité **ManagementAgentTypes** représente les agents utilisés pour gérer un appareil.

| Propriété  | Description |
|---------|------------|
| ManagementAgentTypeID | Identificateur unique du type d’agent de gestion. |
| ManagementAgentTypeKey | Identificateur unique du type d’agent de gestion dans l’entrepôt de données (clé de substitution). |
| ManagementAgentTypeName |Indique le type d’agent utilisé pour gérer l’appareil |

### <a name="example"></a>Exemple

| ManagementAgentTypeID  | Nom | Description |
|---------|------------|--------|
| 1 |EAS | L’appareil est géré par le biais d’Exchange Active Sync |
| 2 |GESTION DES APPAREILS MOBILES | L’appareil est géré à l’aide d’un agent MDM |
| 3 |EasMdm | L’appareil est géré à la fois par Exchange Active Sync et par un agent MDM |
| 4 |IntuneClient | L’appareil est géré par l’agent Intune PC |
| 5 |EasIntuneClient | L’appareil est géré à la fois par Exchange Active Sync et par l’agent Intune PC |
| 8 |ConfigManagerClient | L’appareil est géré par l’agent System Center Configuration Manager |
| 16 |Unknown | Type d’agent de gestion inconnu |

## <a name="devices"></a>Appareils

L’entité **Devices** répertorie tous les appareils inscrits à la gestion et leurs propriétés correspondantes.

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
| EasDeviceId                | ID Exchange ActiveSync de l’appareil.                                                                                                                                                  |
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

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

L’entité **DevicePropertyHistory** a les mêmes propriétés que la table d’appareils et contient des instantanés quotidiens de chaque enregistrement d’appareil par jour au cours des 90 derniers jours. La colonne DateKey indique le jour pour chaque ligne.

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
| DeviceCategoryKey          | Clé de l’attribut de type d’appareil pour cet appareil. 

## <a name="applicationinventory"></a>ApplicationInventory

L’entité **ApplicationInventory** répertorie les applications trouvées sur l’appareil au moment de l’inventaire.


|      Propriété      |                       Description                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              Référence à la table d’appareils.               |
|   ApplicationKey   | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |
|  ApplicationName   | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |
|     BundleSize     | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |

