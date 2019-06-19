---
title: Où se trouve ma fonctionnalité Intune dans Azure ?
titleSuffix: Microsoft Intune
description: Vous aide à trouver les fonctionnalités Microsoft Intune dans le portail Azure.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/4/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 052190185159dfdee4adee94d4c43c72ce6f41d4
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67046325"
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>Où se trouve ma fonctionnalité Intune dans Azure ?
Lors du transfert d’Intune vers le portail Azure, nous en avons profité pour organiser certaines tâches de manière plus logique. Toutefois, ces améliorations nécessitent de se familiariser avec la nouvelle organisation. Ce guide de référence est destiné à ceux d’entre vous qui connaissent parfaitement Intune dans le portail classique et qui se demandent comment effectuer certaines tâches spécifiques dans Intune dans le portail Azure. Si cet article ne couvre pas l’une des fonctionnalités que vous recherchez, laissez-nous un commentaire à la fin de l’article pour que nous puissions le mettre à jour.
## <a name="quick-reference-guide"></a>Guide de référence rapide

|Composant |Chemin dans le portail classique|Chemin dans Intune dans le portail Azure|
|------------|---------------|---------------|
|Programme d’inscription des appareils [iOS uniquement]|Administration > Gestion des appareils mobiles > iOS > Programme d’inscription des appareils|[Inscription de l’appareil > Inscription Apple > Jeton du programme d’inscription](#where-did-apple-dep-go) |
|Programme d’inscription des appareils [iOS uniquement]| Administrateur > Gestion des appareils mobiles > iOS et Mac OS X > Programme d’inscription des appareils |[Inscription de l’appareil > Inscription Apple > Numéros de série du programme d’inscription](#where-did-apple-dep-go) |
|Règles d’inscription |Administrateur > Gestion des appareils mobiles > Règles d’inscription|[Inscription de l’appareil > Restrictions d’inscription](#where-did-enrollment-rules-go) |
|Groupes par numéro de série iOS |Groupes > Tous les appareils > Appareils d’entreprise préinscrits > Par numéro de série iOS|[Inscription de l’appareil > Inscription Apple > Numéros de série du programme d’inscription](#where-did-corporate-pre-enrolled-devices-go) |
|Groupes par numéro de série iOS |Groupes > Tous les appareils > Appareils d’entreprise préinscrits > Par numéro de série iOS| [Inscription de l’appareil > Inscription Apple > Numéros de série AC](#where-did-corporate-pre-enrolled-devices-go)|
|Groupes par IMEI (toutes les plateformes)| Groupes > Tous les appareils > Appareils d’entreprise préinscrits > Par IMEI (Toutes les plateformes) | [Inscription de l’appareil > Identificateurs d’appareil d’entreprise](#by-imei-all-platforms)|
| Profil d’inscription des appareils d’entreprise| Stratégie > Inscription des appareils d’entreprise | [Inscription de l’appareil > Inscription Apple > Profils du programme d’inscription](#where-did-corporate-pre-enrolled-devices-go) |
| Profil d’inscription des appareils d’entreprise | Stratégie > Inscription des appareils d’entreprise | [Inscription de l’appareil > Inscription Apple > Profils AC](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | Administrateur > Gestion des appareils mobiles > Android for Work | Inscription de l’appareil > Inscription Android |
| Conditions générales | Stratégie > Conditions générales | Inscription de l’appareil > Conditions générales |
Paramètres du portail d'entreprise|Admin > Portail d’entreprise|**Gérer** > Applications mobiles<br> **Configuration** > Personnalisation du portail d’entreprise


## <a name="where-do-i-manage-groups"></a>Où gérer les groupes ?
Intune dans le portail Azure utilise [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) pour gérer les groupes.

## <a name="where-did-enrollment-rules-go"></a>Où sont passées les règles d’inscription ?
Dans le portail classique, vous pouviez définir des règles régissant l’inscription MDM des appareils mobiles et des appareils macOS et Windows modernes.

![Image des règles d’inscription des appareils mobiles classiques](./media/01-classic-rules.png)

Ces règles s’appliquaient à tous les utilisateurs de votre compte Intune sans exception. Dans le portail Azure, ces règles apparaissent désormais dans deux types de stratégies distincts : les restrictions de type d’appareil et les restrictions de limite d’appareils.

![Image des restrictions d’inscription d’appareils mobiles Azure](./media/02-azure-enroll-restrictions.png)

La restriction de limite d’appareils par défaut correspond à la limite d’inscription d’appareils dans le portail classique.

![Image des restrictions de limite d’appareils Azure](./media/03-azure-device-limit.png)

La restriction de type d’appareil par défaut correspond aux restrictions de plateforme dans le portail classique.

![Image des restrictions de type d’appareils Azure](./media/04-azure-platform-restrictions.png)

La capacité à autoriser ou à bloquer les appareils personnels est désormais gérée sous les configurations de plateforme de restriction de type d’appareil.

![Image des paramètres de blocage des appareils personnels Azure](./media/05-azure-personal-block.png)

Les nouvelles fonctionnalités de restriction sont ajoutées uniquement au portail Azure.

## <a name="where-did-my-conditional-access-policies-go"></a>Où se trouvent mes stratégies d’accès conditionnel ?
Une fois que votre locataire migre vers le portail Azure, ses stratégies d’accès conditionnel continuent d’être appliquées. Toutefois, vous ne pouvez pas les afficher ou les modifier à partir d’Intune dans le portail Azure.

Si vous voulez afficher des stratégies d’accès conditionnel et leur apporter des modifications à partir du portail Azure, vous devez supprimer les anciennes stratégies du portail classique. Recréez-les ensuite dans le portail Azure. Pour plus d’informations sur la migration de stratégies d’accès conditionnel, consultez [Migrer des stratégies classiques dans le portail Azure](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration). 

## <a name="where-did-my-compliance-policies-go"></a>Où se trouvent mes stratégies de conformité ?
Une fois que votre locataire migre vers le portail Azure, ses stratégies de conformité continuent d’être appliquées. Toutefois, vous ne pouvez pas les afficher ou les modifier à partir d’Intune dans le portail Azure.

Si vous voulez afficher des stratégies de conformité et leur apporter des modifications à partir du portail Azure, vous devez supprimer les anciennes stratégies du portail classique. Recréez-les ensuite dans le portail Azure. Pour en savoir plus sur les stratégies de conformité des appareils, consultez [Bien démarrer avec les stratégies de conformité des appareils dans Intune](https://docs.microsoft.com/intune/device-compliance-get-started). 

## <a name="where-did-apple-dep-go"></a>Où est passé le programme Apple DEP ?
Dans le portail classique, vous pouviez configurer Intune pour l’intégrer au programme DEP (Programme d’inscription des appareils) d’Apple et demander manuellement la synchronisation avec le service d’Apple :

![Image de jeton DEP classique](./media/06-classic-dep-token.png)

Dans le portail Azure, vous configurez le Programme d’inscription des appareils Apple en effectuant les mêmes étapes que dans Intune classique :

![Image de jeton DEP Azure](./media/07-azure-dep-token.png)

Toutefois, l’option **Synchroniser** dans le portail classique a été déplacée vers le flux de travail de gestion de numéro de série, car c’est là qu’apparaissent les résultats d’une synchronisation manuelle :

![Image de synchronisation DEP Azure](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>Où sont passés les appareils d’entreprise pré-inscrits ?
### <a name="by-ios-serial-number"></a>Par numéro de série iOS
Dans le portail classique, vous pouviez inscrire des appareils iOS dans le cadre du programme DEP d’Apple et de l’outil Apple Configurator. Ces deux méthodes permettent d’inscrire des appareils par numéro de série et impliquent l’affectation de profils Inscription des appareils d’entreprise spéciaux. Avant l’inscription, l’affectation de profil d’inscription peut être gérée par l’intermédiaire du groupe d’appareils **Appareils d’entreprise préinscrits - Par numéro de série iOS** :

![Image des numéros de série Apple classiques](./media/09-classic-apple-serials.png)

Cette fenêtre répertorie dans une même liste les numéros de série pour l’inscription Apple DEP et Apple Configurator. Pour réduire les risques de non-concordance d’affectation de profil (profil DEP vers numéro de série AC, et vice versa), nous avons réparti les numéros de série en deux listes dans le portail Azure :

**Numéros de série DEP**
![Image des numéros de série Azure DEP](./media/10-azure-dep-serials.png)

**Numéros de série Apple Configurator**
![Image des numéros de série Azure Apple Configurator](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>Par IMEI (toutes les plateformes)

Dans le portail classique, vous pouvez prélister les numéros IMEI des appareils pour les marquer comme appareils d’entreprise lors de leur inscription sur Intune :

![Image de la liste classique des numéros IMEI](./media/12-classic-corp-imei.png)

Dans le portail Azure, vous devez charger le même IMEI dans la liste Identificateurs d’appareil d’entreprise avec un fichier de valeurs séparées par des virgules (CSV). Le nouveau portail ne prend pas en charge la saisie manuelle de numéros IMEI :

![Image de la liste des numéros IMEI dans Azure](./media/13-azure-corp-imei.png)

Intune dans le portail Azure est conçu pour prendre en charge ultérieurement d’autres types d’identificateurs en plus de l’IMEI, mais n’autorise actuellement que les numéros IMEI pour la préliste.

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>Où sont passés les profils Inscription d’appareil professionnel ?
Pour inscrire des appareils iOS dans le cadre du Programme d’inscription des appareils Apple ou avec l’outil Apple Configurator, vous devez fournir un profil Inscription d’appareil professionnel à affecter à l’appareil. Dans le portail classique, la création et la gestion de ces profils s’effectuaient dans une même liste :

![Image de profils d’inscription d’appareils classiques](./media/14-classic-corp-profiles.png)

Cette liste affiche les profils activés pour une utilisation avec le Programme d’inscription des appareils Apple (**DEP Activé**) et ceux activés uniquement pour une utilisation avec l’outil Apple Configurator (**DEP Désactivé**).

Pour éviter toute confusion entre les deux types de profils et les éventuels non-concordances d’affectation (profil DEP vers appareils Configurator, et vice versa), nous avons séparé la création et la gestion des profils du Programme d’inscription (prise en charge à la fois du Programme d’inscription des appareils Apple et d’Apple School Manager) et des profils Apple Configurator :

**Profils DEP**
![Image de profils DEP Azure](./media/15-azure-dep-profiles.png)

**Profils Apple Configurator**
![Image de profils Azure Apple Configurator](./media/16-azure-ac-profiles.png)
