---
title: Journal des modifications de l’entrepôt de données Intune
titlesuffix: Microsoft Intune
description: Cette rubrique fournit une liste des modifications pour l’API Entrepôt de données Intune de Microsoft.
keywords: Entrepôt de données Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/21/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7d69c602471e8508744f2a00008294cbd335204
ms.sourcegitcommit: 93286c22426dcb59191a99e3cf2af4ff6ff16522
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58358256"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Journal des modifications pour l’API de l’entrepôt de données Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Suivez les mises à jour de l’entrepôt de données Intune.

## <a name="1903"></a>1903
_Date de publication : mars 2019_

### <a name="v10-changes-reflecting-back-to-beta"></a>Modifications v1.0 reflétant vers la version bêta
Lors de la version 1.0 a été introduite dans 1808, il est différent dans certaines différences significatives à partir de la version bêta d’API. Ces modifications apparaîtront dans la version bêta d’API dans 1903. Si vous avez des rapports importants qui utilisent la version bêta d’API, nous vous recommandons vivement de passer ces rapports à V1.0 pour éviter les modifications avec rupture. Reportez-vous à [les informations de version API](reports-api-url.md) pour plus d’informations sur les versions d’API d’entrepôt de données et vers l’arrière compatibilité. 

## <a name="1902"></a>1902 
_Date de publication : février 2019_

### <a name="power-bi-compliance-app"></a>Application de la conformité de Power BI 

Accéder à votre entrepôt de données Intune à l’aide de Power BI en ligne le [conformité Intune (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) application. Avec cette application Power BI, vous pouvez maintenant accéder à et partager des rapports créés au préalable, sans configuration et sans quitter votre navigateur web. 

> [!NOTE]
> Il existe deux filtres supplémentaires, que vous pouvez appliquer à l’application de conformité Intune.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Ajouter des filtres supplémentaires pour l’application de conformité Intune
1. Ouvrez le [conformité Intune (Data Warehouse)](https://app.powerbi.com/groups/me/getapps/services/Intune_dw_compliance) application dans votre navigateur web.
2. Cliquez sur **les appareils Non conformes** et sélectionnez **Non conforme** dans le **complianceStatus** filtre. 
3. Cliquez sur **périphériques inconnus** et sélectionnez **pas encore disponible** dans le **complianceStatus** filtre. 

## <a name="1812"></a>1812 
_Publication : décembre 2018_

### <a name="enrollment-activities-collection-released-to-v10"></a>Collection des activités d’inscription version 1.0 

La collection des activités d’inscription est désormais disponible en version 1.0. Vous pouvez utiliser cette collection pour mieux comprendre le volume des échecs d’inscription et les tendances de votre environnement. Pour plus d’informations, consultez [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) et [enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons).

## <a name="1808"></a>1808
_Publication : août 2018_

### <a name="v10-collections"></a>Collections v1.0  

Vous pouvez maintenant utiliser la version v1.0 d’Intune Data Warehouse en définissant le paramètre de requête `api-version=v1.0`. Les mises à jour de collections dans l’entrepôt de données sont additives par nature et n’interrompent pas les scénarios existants.

### <a name="enrollment-activities-collection-released-to-beta"></a>Collection des activités d’inscription version bêta

La nouvelle collection `Enrollment Activities` est mise en production comme version bêta. Vous pouvez utiliser cette collection pour comprendre comment votre inscription se déroule en affichant les échecs les plus courants. 


## <a name="1805"></a>1805
_Publication : mai 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Correction du nombre d’appareils dans la collection **Appareils** 

Un correctif a été apporté à la collection **Appareils** qui est susceptible de réduire les nombres totaux d’appareils filtrés par l’attribut `isDeleted`. Cette baisse résulte de la correction et n’est pas une erreur. Pour plus d’informations concernant la collection **Appareils**, consultez [Informations de référence sur les entités d’appareil](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Publiée en janvier 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Authentification Intune Data Warehouse des applications uniquement <!-- 1867540 -->

Vous pouvez configurer une application avec Azure Active Directory (Azure AD) et l’authentifier auprès d’Intune Data Warehouse. Pour plus d’informations, consultez [Authentification des applications uniquement auprès de l’entrepôt de données Intune](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Exigences liées aux informations d’identification Azure AD et Intune <!-- 2077525 -->

- Il n’est plus nécessaire d’affecter une licence Intune à l’utilisateur pour accéder à l’entrepôt de données Intune (notamment à l’API).
- Le nom du rôle Intune a été changé de **Rapports** en **Entrepôt de données Intune**. 

    Pour plus d’informations, consultez [Exigences liées aux informations d’identification Azure AD et Intune](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>Options de requête OData <!-- 2077711 -->

Vous pouvez utiliser <code>$select</code> comme paramètre de requête OData. La version actuelle prend en charge les paramètres de requête OData suivants : <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> et <code>$top</code>. Pour plus d’informations, consultez [Options de requête OData](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Nouvelles entités dans le modèle de données de l’entrepôt de données <!-- 2077804 -->

 - L’entité [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) a été ajoutée. L’entité **MobileAppDeviceUserInstallStatus** représente l’état d’installation d’une application mobile pour un appareil et un utilisateur.
 - L’entité [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) a été ajoutée. L’entité **MobileAppInstallState** représente l’état d’installation d’une application mobile après qu’elle a été affectée à un groupe contenant des appareils, des utilisateurs ou les deux. 

## <a name="1710"></a>1710
_Publication : novembre 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>Une nouvelle collection d’entités nommée Utilisateur actuel se limite aux données des utilisateurs actuellement actifs <!-- 1544273 -->

La collecte d’entités **User** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise. Parmi ces enregistrements figurent les états utilisateurs de la période de collecte de données, même si l’utilisateur a été supprimé. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

En revanche, la nouvelle collection d’entités **Utilisateur actuel** contient uniquement les utilisateurs qui n’ont pas été supprimés. La collection d'entités **Utilisateur actuel** ne contient que des utilisateurs actuellement actifs. Pour plus d’informations sur la collection d’entités **Utilisateur actuel**, consultez la page [Informations de référence sur l’entité Utilisateur actuel](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Publication : octobre 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Collection d’entités d’association appareil-utilisateur ajoutée au modèle de données de l’entrepôt de données Intune <!-- 1187917 -->

Vous pouvez désormais générer des rapports et des visualisations des données en utilisant les informations d’association appareil-utilisateur qui associent les collections d’entité utilisateur et appareil. Le modèle de données est accessible par le biais du fichier Power BI (PBIX) extrait de la page Intune Data Warehouse, via le point de terminaison OData, ou en développant un client personnalisé. Pour plus d’informations, consultez la page [Association appareil-utilisateur](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nouvelles entités dans le modèle de données de l’entrepôt de données <!-- 1479526 --><!-- -->

 - L’entité [**UserDeviceAssociation**](reports-ref-user-device.md) est ajoutée. **UserDeviceAssociation** contient les associations appareil-utilisateur dans votre organisation. Vous pouvez désormais générer des rapports et des visualisations des données en utilisant les informations d’association appareil-utilisateur qui associent les collections d’entité utilisateur et appareil.  
 - L’entité [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md) a été ajoutée. **IntuneManagementExtension** contient des entités pour les appareils mobiles qui effectuent le suivi d’informations telles que l’état d’installation et la version.

## <a name="next-steps"></a>Étapes suivantes
 - Découvrez les [nouveautés hebdomadaires dans Intune](whats-new.md). Vous pouvez également découvrir les modifications à venir, les annonces importantes sur le service et des informations sur les versions précédentes.
 - Consultez le [Blog de Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
