---
title: 'Appareils : Entrepôt de données Intune'
titlesuffix: Microsoft Intune
description: Rubrique de référence sur la catégorie Appareils de collections d’entités dans l’API d’entrepôt de données Intune.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
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
ms.openlocfilehash: fe16111095051c1fddb4b87d5b4f815ae2798e92
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566367"
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
| 15 |HoloLens |Appareil HoloLens |
| 16 |SurfaceHub |Appareil Surface Hub |
| 17 |AndroidForWork |Appareil Android géré à l’aide du Propriétaire de profil Android |
| 100 |Blackberry |Appareil Blackberry |
| 101 |Palm |Appareil Palm |
| 255 |Unknown |Type d’appareil inconnu |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

L’entité **ClientRegistrationStateTypes** représente le type d’inscription référencé par d’autres tables d’entrepôt de données.

| Propriété  | Description |
|---------|------------|
| clientRegistrationStateID |Identificateur unique de l’état d’inscription |
| clientRegistrationStateKey |Identificateur unique de l’état d’inscription dans l’entrepôt de données (clé de substitution) |
| clientRegistrationStateName |État d’inscription |

### <a name="example"></a>Exemple

| ClientRegistrationStateID  | Nom | Description |
|---------|------------|--------|
| 0 |NotRegistered |Non inscrit |
| 1 |SMSIDConflict |Conflit d’ID SMS |
| 2 |Inscrit |Inscrit |
| 3 |Revoked |Cet état signifie que l’administrateur informatique a bloqué le client et que ce dernier peut être débloqué. Un appareil peut également être dans l’état Revoked après une réinitialisation ou une mise hors service. |
| 4 |KeyConflict |Conflit de clé |
| 5 |ApprovalPending |Approbation en attente |
| 6 |ResetCert |Réinitialiser le certificat |
| 7 |NotRegisteredPendingEnrollment |Non inscrit, inscription en attente |
| 8 |Unknown |État inconnu |

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

## <a name="enrollmenttypes"></a>EnrollmentTypes

L’entité **EnrollmentTypes** indique la façon dont un appareil a été inscrit. Le type d’inscription capture la méthode d’inscription. Les exemples répertorient les différents types d’inscription et leur signification.

| Propriété  | Description |
|---------|------------|
| managementStateID |Identificateur unique de l’état de gestion |
| managementStateKey |Identificateur unique de l’état de gestion dans l’entrepôt de données (clé de substitution) |
| managementStateName |Indique l’état de l’action à distance appliquée à cet appareil |

### <a name="example"></a>Exemple

| enrollmentTypeID  | Nom | Description |
|---------|------------|--------|
| 0 |Unknown |Le type d’inscription n’a pas été collecté |
| 1 |UserEnrollment |Inscription lancée par l’utilisateur |
| 2 |DeviceEnrollment |Inscription d’appareil avec un profil sans utilisateur |
| 3 |DeviceEnrollmentWithUDA |Inscription d’appareil avec un profil UDA |
| 4 |AzureDomainJoined |Inscription d’appareil lancée par l’utilisateur par le biais d’Azure Active Directory |
| 5 |UserEnrollmentWithServiceAccount |Inscription lancée par l’utilisateur par le biais d’un compte de service |
| 6 |DepDeviceEnrollment |Inscription d’appareil DEP avec un profil sans utilisateur |
| 7 |DepDeviceEnrollmentWithUDA |Inscription d’appareil DEP avec un profil UDA |
| 8 |AutoEnrollment |Inscription DRS et MDM combinée pour les scénarios BYOD |

## <a name="ownertypes"></a>OwnerTypes

L’entité **EnrollmentTypes** indique si un appareil est un appareil d’entreprise, personnel ou inconnu.

| Propriété  | Description | Exemple |
|---------|------------|--------|
| ownerTypeID |Identificateur unique du type de propriétaire. | |
| ownerTypeKey |Identificateur unique du type de propriétaire dans l’entrepôt de données (clé de substitution). | |
| ownerTypeName |Représente le type de propriétaire des appareils :  <br>Entreprise - appareil est appartient à l’entreprise. <br>Personnel : il s’agit d’un appareil personnel (BYOD).  <br>Inconnu : aucune information n’est disponible sur cet appareil. |Entreprise personnel inconnu |

> [!Note]  
> Pour le `ownerTypeName` dans Azure AD lors de la création de groupes dynamiques pour les appareils, vous devez définir la valeur de filtre `deviceOwnership` comme `Company`. Pour plus d’informations, consultez [règles pour les appareils](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="mdmstatuses"></a>MdmStatuses

L’entité **MdmStatuses** indique l’état de conformité de l’appareil.

| Propriété  | Description |
|---------|------------|
| MdmStatusID |Identificateur unique de l’état de conformité |
| MdmStatusKey |Identificateur unique de l’état de conformité dans l’entrepôt de données (clé de substitution) | 
| ComplianceStatus |État de conformité de l’appareil, qui doit adopter l’une des valeurs du tableau ci-dessous | 


### <a name="example"></a>Exemple

| MdmStatusID  | ComplianceStatus | Description |
|---------|------------|--------|
| 0 |Unknown |L’état de conformité de l’appareil est inconnu. |
| 1 |Conforme |L’appareil est conforme. |
| 2 |Non conforme |L’appareil n'est pas conforme. |
| 3 |Conflit |La conformité de l’appareil a généré un conflit. |
| 4 |Erreur |Une erreur s’est produite durant la lecture de l’état de conformité de l’appareil. |


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

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

L’entité **WorkPlaceJoinStateTypes** représente l’état d’Azure Active Directory Workplace Join de l’appareil.  Le flux de travail d’inscription peut utiliser un ou plusieurs certificats pour la vérification ou l’authentification. Au cours de l’inscription d’un appareil dans WorkPlace, ces certificats sont utilisés pour valider l’appareil et l’utilisateur. Les certificats sont émis par le biais d’un serveur SCEP (protocole d’inscription de certificats simple). Les valeurs de l’entité indiquent les différents états dans lesquels un appareil peut se trouver au cours de ce processus. Certains états indiquent l’échec de Workplace Join en raison de l’impossibilité d’émettre un certificat obligatoire (à partir d’un serveur SCEP). Si un appareil ne passe pas par ce flux de travail, la valeur est Unknown.

| Propriété  | Description |
|---------|------------|
| WorkPlaceJoinStateID | Identificateur unique de l’état de Workplace Join |
| WorkPlaceJoinStateKey | Identificateur unique de l’état de Workplace Join dans l’entrepôt de données (clé de substitution) |
| WorkPlaceJoinStateName | État de Workplace Join |

### <a name="example"></a>Exemple

| workPlaceJoinStateID  | Nom | Description |
|---------|------------|--------|
| 0 |Unknown |Si un appareil n’est pas rattaché à l’espace de travail, son état est Unknown |
| 1 |Réussi |Rattachement à l’espace de travail effectué |
| 2 |FailureToGetScepMetadata |Échec de l’obtention des métadonnées SCEP |
| 3 |FailureToGetScepChallenge |Échec de l’obtention du défi SCEP |
| 4 |DeviceFailureToInstallScepCommand |Échec de l’installation de la commande SCEP sur l’appareil |
| 5 |DeviceFailureToGetCertificate |Échec de l’obtention du certificat par le biais de SCEP |
| 6 |DeviceScepPending |État en attente ; l’appareil utilise encore SCEP |
| 7 |DeviceScepFailed |L’appareil n’a pas pu installer le certificat par le biais de SCEP |
| 8 |AADValidationFailed |Échec de la validation de l’appareil sur AAD |

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

| Propriété  | Description |
|---------|------------|
| DeviceKey | Identificateur unique de l’appareil dans l’entrepôt de données (clé de substitution). |
| DeviceId | Identificateur unique de l’appareil. |
| DeviceName | Nom de l’appareil sur les plateformes qui autorisent le nommage d’un appareil. Sur d’autres plateformes, Intune crée un nom à partir d’autres propriétés. Cet attribut ne peut pas être disponible pour tous les appareils. |
| DeviceTypeKey | Clé de l’attribut de type d’appareil pour cet appareil. |
| ClientRegisterationStateKey | Clé de l’attribut d’état d’inscription du client pour cet appareil. |
| OwnerTypeKey | Clé de l’attribut de type de propriétaire pour cet appareil : entreprise, personnel ou inconnu. |
| objectSourceKey | Ignorez cette colonne. |
| CreatedDate | Date d’inscription de l’appareil. |
| LastContact | Dernier enregistrement connu de l’appareil auprès d’Intune. |
| LastContactNotification | Heure de la dernière notification envoyée par Intune à l’appareil pour qu’il s’enregistre auprès d’Intune. |
| LastContactWorkplaceJoin | Timestamp indiquant le dernier état de Workplace Join connu pour cet appareil. |
| ManagementAgentKey | Clé de l’agent de gestion associé à cet appareil. |
| ManagementStateKey | Clé de l’état de gestion associé à cet appareil. Indique l’état le plus récent d’une action à distance ou indique si l’appareil a été jailbreaké/rooté. |
| ReferenceId | ID de l’appareil dans Azure Active Directory. |
| WorkPlaceJoinStateKey | Clé de l’état de WorkPlace Join associé à cet appareil. |
| CategoryId | Ignorez cette colonne. |
| EnrollmentTypeKey | Clé du type d’inscription associé à cet appareil. Indique la méthode d’inscription. |
| CertExpirationDate | Date d’expiration du certificat de gestion MDM. |
| MdmStatusKey | Clé à MdmStatus. |
| OSFamily | Famille du système d’exploitation (Windows, iOS, Android, etc.) |
| OSVersion | Version du système d'exploitation |
| OSMajorVersion | Composant « version majeure » de la version du système d’exploitation (majeure.mineure.build.révision). |
| OSMinorVersion | Composant « version mineure » de la version du système d’exploitation (majeure.mineure.build.révision). |
| OSBuildNumber | Composant « version de build » de la version du système d’exploitation (majeure.mineure.build.révision). |
| OSRevisionNumber | Composant « version de révision » de la version du système d’exploitation (majeure.mineure.build.révision). |
| EasID | ID EAS de l’appareil s’il est géré par Exchange Active Sync. |
| GraphDeviceIsManaged | Dernier état de gestion défini par Intune dans Azure AD. |
| GraphDeviceIsCompliant | Dernier état de conformité défini par Intune dans Azure AD. |
| SerialNumber | Numéro de série de l’appareil (le cas échéant). |
| EnrolledByUser | ID de l’utilisateur ayant inscrit cet appareil qui fait référence à la colonne userId dans la table User. |
| RowLastModifiedDateTimeUTC | Date et heure de la dernière modification de cet enregistrement. |
| ProcessorArchitecture | Architecture du processeur. |
| DeviceAction | Dernière action de l’appareil émise. Ignorez-la pour le moment. |
| Fabricant | Fabricant de l’appareil. |
| Modèle | Modèle de l’appareil. |
| LastPolicyUpdateUtc | Heure de la dernière mise à jour de la stratégie sur l’appareil. |
| LastExchangeStatusUtc | Heure de la dernière synchronisation de l’appareil avec Exchange. |
| IsDeleted | Affectez la valeur True si l’appareil n’est plus géré par Intune. Préserve le dernier état connu. |
| AndroidSecurityPatchLevel |Date du correctif de sécurité le plus récent sur l’appareil. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

L’entité **DevicePropertyHistory** a les mêmes propriétés que la table d’appareils et contient des instantanés quotidiens de chaque enregistrement d’appareil par jour au cours des 90 derniers jours. La colonne DateKey indique le jour pour chaque ligne.

| Propriété  | Description |
|---------|------------|
| DateKey |Référence à la table de dates indiquant le jour. |
| DeviceKey |Identificateur unique de l’appareil dans l’entrepôt de données (clé de substitution). Il s’agit d’une référence à la table d’appareils qui contient l’ID d’appareil Intune. |
| DeviceName |Nom de l’appareil sur les plateformes qui autorisent le nommage d’un appareil. Sur d’autres plateformes, Intune crée un nom à partir d’autres propriétés. Cet attribut ne peut pas être disponible pour tous les appareils. |
| DeviceTypeKey |Clé de l’attribut de type d’appareil pour cet appareil. |
| ClientRegisterationStateKey |Clé de l’attribut d’état d’inscription du client pour cet appareil. |
| OwnerTypeKey |Clé de l’attribut de type de propriétaire pour cet appareil : entreprise, personnel ou inconnu. |
| objectSourceKey |Ignorez cette colonne. |
| CreatedDate |Date d’inscription de l’appareil. |
| LastContact |Dernier enregistrement connu de l’appareil auprès d’Intune. |
| LastContactNotification |Heure de la dernière notification envoyée par Intune à l’appareil pour qu’il s’enregistre auprès d’Intune. |
| LastContactWorkplaceJoin |Timestamp indiquant le dernier état de Workplace Join connu pour cet appareil. |
| ManagementAgentKey |Clé de l’agent de gestion associé à cet appareil. |
| ManagementStateKey |Clé de l’état de gestion associé à cet appareil. Indique l’état le plus récent d’une action à distance ou indique si l’appareil a été jailbreaké/rooté. |
| ReferenceId |ID de l’appareil dans Azure Active Directory. |
| WorkPlaceJoinStateKey |Clé de l’état de WorkPlace Join associé à cet appareil. |
| CategoryId |Ignorez cette colonne. |
| EnrollmentTypeKey |Clé du type d’inscription associé à cet appareil. Indique la méthode d’inscription. |
| CertExpirationDate |Date d’expiration du certificat de gestion MDM. |
| MdmStatusKey |Clé à MdmStatus. |
| OSFamily |Famille du système d’exploitation (Windows, iOS, Android, etc.) |
| OSVersion |Version de système d’exploitation. |
| OSMajorVersion |Composant « version majeure » de la version du système d’exploitation (majeure.mineure.build.révision). |
| OSMinorVersion |Composant « version mineure » de la version du système d’exploitation (majeure.mineure.build.révision). |
| OSBuildNumber |Composant « version de build » de la version du système d’exploitation (majeure.mineure.build.révision). |
| OSRevisionNumber |Composant « version de révision » de la version du système d’exploitation (majeure.mineure.build.révision). |
| EasID |ID EAS de l’appareil s’il est géré par Exchange Active Sync. |
| GraphDeviceIsManaged |Dernier état de gestion défini par Intune dans Azure AD. |
| GraphDeviceIsCompliant |Dernier état de conformité défini par Intune dans Azure AD. |
| SerialNumber |Numéro de série de l’appareil (le cas échéant). |
| EnrolledByUser |ID de l’utilisateur ayant inscrit cet appareil qui fait référence à la colonne userId dans la table User. |
| RowLastModifiedDateTimeUTC |Date et heure de la dernière modification de cet enregistrement. |
| ProcessorArchitecture |Architecture du processeur. |
| DeviceAction |Dernière action de l’appareil émise. Ignorez-la pour le moment. |
| Fabricant |Fabricant de l’appareil. |
| Modèle |Modèle de l’appareil. |
| LastPolicyUpdateUtc |Heure de la dernière mise à jour de la stratégie sur l’appareil. |
| LastExchangeStatusUtc |Heure de la dernière synchronisation de l’appareil avec Exchange. |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

L’entité **MdmDeviceInventoryHistories** contient des instantanés quotidiens des données d’inventaire pour les appareils gérés par MDM au cours des 90 derniers jours. La colonne DateKey indique le jour de la ligne. Il est possible que certaines propriétés ne s’appliquent pas à tous les appareils ou qu’elles ne soient pas renseignées. Consultez cette page pour obtenir plus de détails. Pour plus d’informations, consultez [Comprendre vos appareils grâce à l’inventaire de Microsoft Intune](device-inventory.md).

| Propriété  | Description |
|---------|------------|
| DateKey | Référence à la table de dates indiquant le jour. |
| DeviceKey |Identificateur unique de l’appareil dans l’entrepôt de données (clé de substitution). Il s’agit d’une référence à la table d’appareils qui contient l’ID d’appareil Intune. |
| DeviceModel |Modèle de l’appareil. |
| Système d’exploitation |Système d’exploitation de l’appareil. |
| DeviceName |Nom de l’appareil sur les plateformes qui autorisent le nommage d’un appareil. Sur d’autres plateformes, Intune crée un nom à partir d’autres propriétés. Cet attribut ne peut pas être disponible pour tous les appareils. |
| SoftwareVersion |Dans la plupart des cas, il s’agit de la version du système d’exploitation, sauf sur les plateformes Apple. |
| Imei |Numéro IMEI |
| HardwareInventoryTimeUtc |Heure du premier inventaire signalé pour cet appareil. |
| InventoryModifiedTimeUtc |Heure du dernier stockage de l’inventaire quand cet instantané a été pris. |
| InventoryReportingTimeUtc |Heure du dernier inventaire sur cet appareil. |
| ExchangeActiveSyncId |ID d’appareil Exchange ActiveSync. |
| ComputerSystemDescription |Description du système. |
| ComputerSystemName |Nom du système. |
| ComputerSystemManufacturer |Fabricant du système. |
| ComputerSystemModel |Modèle du système. |
| UserName |Nom d’utilisateur. |
| OSType |Type de système d’exploitation. |
| OSCaption |Légende du système d’exploitation. |
| OSName |Nom du système d’exploitation. |
| OSManufacturer |Fabricant du système d’exploitation. |
| OSProductSuite |Suite de produits du système d’exploitation. |
| OSProductType |Type de produit du système d’exploitation. |
| Locale |Paramètres régionaux du système d’exploitation. |
| PhysicalMemoryCapacity |Capacité de mémoire physique (en octets). |
| PhysicalMemoryRemovable |Mémoire amovible physique (en octets). |
| SystemEnclosureChassisTypesInnerText |Définit le type de châssis du système pour cet appareil. Les nombres indiquent les valeurs suivantes :  <br>0 ou Vide = Inconnu   <br>1 = Ordinateur de bureau   <br>2 = Ordinateur portable  <br>3 = Station de travail  <br>4 = Serveur d’entreprise  <br>100 = Téléphone  <br>101 = Tablette  <br>102/103 = Autre type inconnu d’appareil mobile |
| SystemEnclosureModel |Modèle du boîtier système. |
| SystemEnclosureSerialNumber |Numéro de série du boîtier système. |
| NetworkAdapterConfigurationText |Texte de configuration de la carte réseau. |
| MacAddress |Adresse MAC. |
| SmsID |ID d’appareil Intune. |
| CertExpiry |Date d’expiration du certificat de gestion MDM. |
| DeviceClientAgentVersion |Version de l’agent du client. |
| DeviceClientID |ID du client de l’appareil. |
| SerialNumber |Numéro de série. |
| DeviceManufacturer |Fabricant de l’appareil. |
| DMVersion |Version de DM. |
| FirmwareVersion |Version du microprogramme. |
| HardwareVersion |Version du matériel. |
| PlatformType |Type de plateforme. |
| ProcessorLevel |Niveau du processeur. |
| ProcessorRevision |Révision du processeur. |
| Produit |Produit. |
| ProductVersion |Version du produit. |
| OEM |Fabricant d’ordinateurs OEM. |
| DeviceBuildVersion |Version de build de l’appareil. |
| Meid |Identificateur d’équipement mobile |
| PhoneNumber |Numéro de téléphone. |
| SubscriberCarrierNetwork |Nom du réseau de l’opérateur téléphonique. |
| CellularTechnology |Type de réseau de l’opérateur téléphonique (CDMA/GSM). |
| Imsi |Numéro IMSI. |
| JailBroken |True si l’appareil est jailbreaké ou rooté |
| IsActivationLockEnabled |True si le verrou d’activation est activé |
| DeviceType |Type d'appareil |
| IsSupervised |Est supervisé |
| DeviceDisplayNumberOfColors |Nombre de couleurs de l’affichage de l’appareil |
| HorizontalResolution |Résolution horizontale de l’écran de l’appareil |
| VerticalResolution |Résolution verticale de l’écran de l’appareil |
| StorageFree |Stockage disponible (en octets) |
| StorageTotal |Stockage total (en octets) |
| ProgramFree |Mémoire programme disponible (en octets) |
| ProgramTotal |Mémoire programme totale (en octets) |
| RemovableStorageFree |Stockage amovible disponible (en octets) |
| RemovableStorageTotal |Stockage amovible total (en octets) |
| DeviceMemoryDeviceCapacity |Capacité mémoire de l’appareil |
| DeviceMemoryAvailableDeviceCapacity |Capacité mémoire de l’appareil disponible |
| DeviceOSVersion |Version de système d'exploitation |
| DeviceOSPlatform |Plateforme du système d’exploitation |
| DeviceOSLanguage |Langue du système d’exploitation |
| PasswordMaxAttemptsBeforeWipe |Nombre maximum de tentatives de saisie du mot de passe avant la réinitialisation de l’appareil |
| PasswordMinComplexChars |Nombre minimal de caractères complexes nécessaires dans le mot de passe |
| PasswordMinLength |Longueur minimale du mot de passe |
| PasswordHistory |Nombre minimal de mots de passe de l’historique non acceptés |
| PasswordEnabled |Mot de passe activé ? |
| PasswordExpiration |Date d’expiration du mot de passe. |
| AllowRecoveryPassword |Autoriser la récupération du mot de passe. |
| PasswordAutoLockTimeout |Délai au bout duquel le mot de passe est automatiquement verrouillé. |
| PasswordType |Type de mot de passe. |
| BacklightACTimeout |Délai au bout duquel le rétroéclairage est coupé en cas de connexion à une source d’alimentation. |
| BacklightBatTimeout |Délai au bout duquel le rétroéclairage est coupé en cas de fonctionnement sur batterie. |
| PowerBackupPercent |Pourcentage de l’alimentation de secours. |
| BatteryPercent |Pourcentage de batterie restant |
| PlatformID |ID de plateforme. |
| ExchangeDeviceID |ID de l’appareil Exchange. |
| SmsProcessorDescription |Description du processeur. |
| OwnerEmailAddress |Adresse e-mail du propriétaire. |
| DeviceOSName |Nom du système d’exploitation. |
| WifiMac |Adresse Mac Wi-Fi. |
| EthernetMac |Adresse Mac Ethernet. |
| RequireEncryption |Indique si l’appareil est chiffré ou non |
| ActivationLockBypassCode |Code de contournement du verrou d’activation. |

## <a name="applicationinventory"></a>ApplicationInventory

L’entité **ApplicationInventory** répertorie les applications trouvées sur l’appareil au moment de l’inventaire.


|      Propriété      |                       Description                        |
|--------------------|----------------------------------------------------------|
|     DeviceKey      |              Référence à la table d’appareils.               |
|   ApplicationKey   | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |
|  ApplicationName   | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |
|     BundleSize     | ? (copié à partir de ExchangeDeviceService\DeviceApplication). |

