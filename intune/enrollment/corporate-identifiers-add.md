---
title: Ajouter des identificateurs d’entreprise à Intune
titleSuffix: ''
description: Découvrez comment ajouter des identificateurs d’entreprise (méthode d’inscription, numéros IMEI et numéros de série) à Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51538f8994557bba718f0e8344b1da8d3c7193fa
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414402"
---
# <a name="identify-devices-as-corporate-owned"></a>Identifier les appareils comme appartenant à l’entreprise

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez identifier les appareils comme étant propriété de l’entreprise, ce qui en permet une gestion et une identification plus précises. Intune peut effectuer d’autres tâches d’administration et collecter des informations supplémentaires, comme le numéro de téléphone complet et un inventaire des applications des appareils d’entreprise. Vous pouvez également définir des restrictions au niveau des appareils pour bloquer l’inscription des appareils qui n’appartiennent pas à l’entreprise.

Au moment de l’inscription, Intune affecte automatiquement l’état « Appartenant à l’entreprise » aux appareils qui sont :

- Appareil inscrit avec un compte de [gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md) (toutes les plateformes)
- Appareil inscrit avec le [programme d’inscription des appareils](device-enrollment-program-enroll-ios.md) Apple, [Apple School Manager](apple-school-manager-set-up-ios.md) ou [Apple Configurator](apple-configurator-enroll-ios.md) (iOS uniquement)
- [Appareil identifiés comme appartenant à l’entreprise avant l’inscription](#identify-corporate-owned-devices-with-imei-or-serial-number) avec un numéro IMEI (International Mobile Equipment Identifier) (pour toutes les plateformes avec des numéros IMEI) ou un numéro de série (iOS et Android)
- Joint à Azure Active Directory avec des informations d’identification professionnelles ou scolaires. [Les appareils qui sont inscrits dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/overview) sont marqués comme personnels.
- Définis comme appartenant à l’entreprise dans la [liste des propriétés de l’appareil](#change-device-ownership)

Après l’inscription, vous pouvez [changer le paramètre de propriété](#change-device-ownership) en **Personnel** ou **Entreprise**.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identifier des appareils d’entreprise à l’aide de leur numéro IMEI ou de leur numéro de série

Les administrateurs Intune peuvent créer et importer un fichier de valeurs séparées par des virgules (.csv) qui liste les numéros de série ou les numéros IMEI de 14 chiffres. Intune utilise ces identificateurs pour spécifier l’entreprise comme propriétaire des appareils lors de l’inscription de l’appareil. Chaque numéro IMEI ou numéro de série peut contenir des détails spécifiés dans la liste pour des raisons administratives.

Cette fonctionnalité est prise en charge pour les plates-formes suivantes :

| Plate-forme | Numéros IMEI | Numéros de série |
|---|---|---|
| Windows | Pris en charge (Windows Phone) | Non prise en charge |
| iOS/macOS | Non prise en charge | Pris en charge |
| Device admin managed Android OS v10 | Non prise en charge | Non prise en charge |
| Autre Android | Non prise en charge | Pris en charge |

<!-- When you upload serial numbers for corporate-owned iOS/iPadOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Découvrez comment trouver un numéro de série d’appareil Apple](https://support.apple.com/HT204308).<br>
[Découvrez comment trouver votre numéro de série d’appareil Android](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Ajouter des identificateurs d’entreprise à l’aide d’un fichier .csv
Pour créer la liste, préparez une liste à deux colonnes de valeurs séparées par des virgules (.csv), sans en-tête. Ajoutez les numéros de série ou IMEI de 14 chiffres dans la colonne de gauche, et les détails dans celle de droite. Vous ne pouvez importer qu’un seul type d’ID, numéro IMEI ou numéro de série dans un fichier .csv. Les détails sont limités à 128 caractères et sont réservés à des fins d’administration. Les détails ne sont pas affichés sur l’appareil. La limite actuelle est de 5 000 lignes par fichier .csv.

**Chargez un fichier .csv qui contient les numéros de série** : créez une liste de valeurs séparées par des virgules (.csv) de deux colonnes sans en-tête, limitée à 5 000 appareils ou à 5 Mo par fichier .csv.

|||
|-|-|
|&lt;ID 1&gt;|&lt;Détails de l’appareil 1&gt;|
|&lt;ID 2&gt;|&lt;Détails de l’appareil 2&gt;|

Dans un éditeur de texte, ce fichier .csv s'affiche comme suit :

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Certains appareils Android et iOS/iPadOS possèdent plusieurs numéros IMEI. Intune ne lit qu’un seul numéro IMEI par appareil inscrit. Si vous importez un numéro IMEI, mais qu’il ne s’agit pas du numéro IMEI inventorié par Intune, l’appareil est classé comme appareil personnel plutôt que comme appareil d’entreprise. Si vous importez plusieurs numéros IMEI pour un appareil, les numéros non inventoriés présentent l’état d’inscription **Inconnu**.<br>
>Autres points à noter : les numéros de série représentent la forme d’identification recommandée pour les appareils iOS/iPadOS.
>Les numéros de série Android ne sont pas nécessairement uniques ou présents. Vérifiez auprès du fournisseur de votre appareil si le numéro de série est un ID d’appareil fiable.
>Les numéros de série signalés à Intune par l’appareil peuvent ne pas correspondre à l’ID affiché dans les menus Paramètres/À propos d’Android de l’appareil. Vérifiez le type de numéro de série signalé par le fabricant de l’appareil.
>Si vous tentez de charger un fichier avec des numéros de série contenant des points (.), le chargement échoue. Les numéros de série comportant des points ne sont pas pris en charge.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Charger une liste .csv d’identificateurs d’entreprise

1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Inscrire des appareils** > **Identificateurs d’appareil d’entreprise** > **Ajouter** > **Charger un fichier CSV**.

2. Dans le panneau **Ajouter des identificateurs**, spécifiez le type d’identificateur : **IMEI** ou **Série**.

3. Cliquez sur l’icône du dossier et spécifiez le chemin de la liste que vous voulez importer. Accédez au fichier .csv, puis choisissez **Ajouter**. 

4. Si le fichier .csv contient des identificateurs d’entreprise qui sont déjà dans Intune, mais dont les détails diffèrent, la fenêtre contextuelle **Examiner les identificateurs en double** s’affiche. Sélectionnez les identificateurs que vous souhaitez remplacer dans Intune et choisissez **Ok** pour les ajouter. Pour chaque identificateur, seul le premier doublon est comparé.

## <a name="manually-enter-corporate-identifiers"></a>Entrer manuellement les identificateurs d’entreprise

1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Inscrire des appareils** > **Identificateurs d’appareil d’entreprise** > **Ajouter** > **Entrer manuellement**.

2. Dans le panneau **Ajouter des identificateurs**, spécifiez le type d’identificateur : **IMEI** ou **Série**.

3. Renseignez les champs **Identificateur** et **Détails** pour chaque identificateur que vous souhaitez ajouter. Une fois que vous avez terminé d’entrer des identificateurs, choisissez **Ajouter**.

5. Si vous avez entré des identificateurs d’entreprise qui sont déjà dans Intune, mais dont les détails diffèrent, la fenêtre contextuelle **Examiner les identificateurs en double** s’affiche. Sélectionnez les identificateurs que vous souhaitez remplacer dans Intune et choisissez **Ok** pour les ajouter. Pour chaque identificateur, seul le premier doublon est comparé.

Vous pouvez cliquer sur **Actualiser** pour afficher les nouveaux identificateurs d’appareils.

Les appareils importés ne sont pas nécessairement inscrits. Les appareils peuvent avoir l’état **Inscrit** ou l’état **Non contacté**. **N’a pas contacté** signifie que l’appareil n’a jamais communiqué avec le service Intune.

## <a name="delete-corporate-identifiers"></a>Supprimer des identificateurs d’entreprise

1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Inscrire des appareils** > **Identificateurs d’appareil d’entreprise**.
2. Sélectionnez les identificateurs d’appareil que vous voulez supprimer, puis choisissez **Supprimer**.
3. Confirmez la suppression.

La suppression d’un identificateur d’entreprise pour un appareil inscrit ne change pas la propriété de l’appareil. Pour modifier la propriété d’un appareil, allez à **Appareils**, sélectionnez l’appareil, choisissez **Propriétés** et modifiez **Propriété des appareil**.

## <a name="imei-specifications"></a>Spécifications IMEI
Pour obtenir des spécifications détaillées sur les IMEI (International Mobile Equipment Identifiers), consultez [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Changer la propriété des appareils

Les propriétés des appareils affichent **Propriété** pour chaque enregistrement d’appareil dans Intune. En tant qu’administrateur, vous pouvez spécifier des appareils comme étant **Personnel** ou d’**Entreprise**. Lorsque le type de propriété d’un appareil passe d’Entreprise à Personnel, Intune supprime toutes les informations d’applications préalablement collectées à partir de cet appareil dans les 7 jours. Le cas échéant, Intune supprime également le numéro de téléphone enregistré. 

**Pour changer la propriété d’un appareil :**
1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Tous les appareils** > choisissez l’appareil.
2. Choisissez **Propriétés**.
3. Spécifiez pour **Propriété de l’appareil** l’option **Personnel** ou **Entreprise**.

   ![Propriétés de l’appareil montrant la catégorie Appareil et les options Propriété de l’appareil](./media/corporate-identifiers-add/device-properties.png)
