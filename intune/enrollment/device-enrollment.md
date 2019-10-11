---
title: Qu’est-ce que l’inscription des appareils Microsoft Intune ?
titleSuffix: Microsoft Intune
description: En savoir plus sur l’inscription pour les appareils iOS, Android et Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3fb9af260b8fddc78b644b8ede056c90bac24d0
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999355"
---
# <a name="what-is-device-enrollment"></a>Qu’est-ce que l’inscription d’appareils ?
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune vous permet de gérer les appareils et les applications des membres de votre personnel, et comment ils accèdent aux données de votre entreprise. Pour utiliser cette gestion des appareils mobiles (MDM), les appareils doivent d’abord être inscrits auprès du service Intune. Quand un appareil est inscrit, il reçoit un certificat MDM. Ce certificat est utilisé pour communiquer avec le service Intune.

Comme vous pouvez le voir dans les tableaux suivants, il existe plusieurs méthodes pour inscrire les appareils des membres de votre personnel. Chaque méthode dépend de la propriété de l’appareil (personnel ou d’entreprise), du type d’appareil (iOS, Windows, Android) et des exigences de gestion (réinitialisations, affinité, verrouillage).

Par défaut, les appareils de toutes les plateformes peuvent être inscrits dans Intune. Cependant, vous pouvez [limiter les appareils par plateforme](enrollment-restrictions-set.md#create-a-device-type-restriction).

## <a name="ios-enrollment-methods"></a>Méthodes d’inscription iOS

| **Méthode** | **Réinitialisation requise** | [**Affinité utilisateur**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **Verrouillé** | **Détails** |
|:---:|:---:|:---:|:---:|:---:|
| | Les appareils sont réinitialisés lors de l’inscription. | Associe chaque appareil à un utilisateur.| Dans ce cas, les utilisateurs ne peuvent pas désinscrire les appareils. | |
|**[BYOD](#bring-your-own-device)** | Non| Oui | Non | [Plus d’informations](apple-mdm-push-certificate-get.md)|
|**[GESTIONNAIRE D’INSCRIPTION D’APPAREIL](#device-enrollment-manager)**| Non |Non |Non | [Plus d’informations](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| Oui | Facultatif | Facultatif|[Plus d’informations](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Oui | Facultatif | Non| [Plus d’informations](apple-configurator-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| Non | Non | Non|[Plus d’informations](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>Méthodes d’inscription macOS
| **Méthode** |  **Réinitialisation requise** |  **Affinité utilisateur** | **Verrouillé** | **Détails**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Non| Oui | Non | [Plus d’informations](macos-enroll.md)|
|**[GESTIONNAIRE D’INSCRIPTION D’APPAREIL](#device-enrollment-manager)**| Non |Non |Non  | [Plus d’informations](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| Oui | Facultatif | Facultatif|[Plus d’informations](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Méthodes d’inscription de Windows

| **Méthode** | **Réinitialisation requise** | **Affinité utilisateur** | **Verrouillé** | **Détails**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Non | Oui | Non | [Plus d’informations](windows-enroll.md)|
|**[GESTIONNAIRE D’INSCRIPTION D’APPAREIL](#device-enrollment-manager)**| Non |Non |Non |[Plus d’informations](device-enrollment-manager-enroll.md)|
|**Inscription automatique** | Non |Oui |Non | [Plus d’informations](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |Oui |Oui |Non | [Plus d’informations](enrollment-autopilot.md)
|**Inscription en bloc** |Non |Non |Non | [Plus d’informations](windows-bulk-enroll.md) |
|**Cogestion** |Non |Oui |Non | [Plus d’informations](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)
|**GPO** |Non |Oui |Non | [Plus d’informations](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Méthodes d’inscription d’Android

| **Personnel** | **Méthodes d’inscription** | **Réinitialisation requise** | **Affinité utilisateur** | **Verrouillé** | **Détails**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Administration des appareils Android**|**Lancée par l’utilisateur par le biais du portail d’entreprise** | Non | Oui | Non | [Plus d’informations](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Profil professionnel Android Entreprise**|**Lancée par l’utilisateur par le biais du portail d’entreprise**| Non | Oui | Non | [Plus d’informations](android-work-profile-enroll.md)|


| **Entreprise** | **Méthodes d’inscription** | **Réinitialisation requise** | **Affinité utilisateur** | **Verrouillé** | **Détails**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Administration des appareils Android**|**Lancée par le [GESTIONNAIRE D’INSCRIPTION D’APPAREIL](#device-enrollment-manager) par le biais du portail d’entreprise**| Non | Non | Non |[Plus d’informations](device-enrollment-manager-enroll.md)|
|**Administration des appareils Android**|**(IMEI ou SN prédéclaré) Lancée par l’utilisateur par le biais du portail d’entreprise**| Non | Oui | Non | [Plus d’informations](./../corporate-identifiers-add.md)|
|**Administration des appareils Android avec Extensions de mobilité Zebra**|**Lancée par l’utilisateur ou par le [GESTIONNAIRE D’INSCRIPTION D’APPAREIL](#device-enrollment-manager) par le biais du portail d’entreprise**| Non | Oui si lancée par l’utilisateur, non si lancée par le [GESTIONNAIRE D’INSCRIPTION D’APPAREIL](#device-enrollment-manager) | Non | [Plus d’informations](../configuration/android-zebra-mx-overview.md)|
|**Android Entreprise dédié**|**NFC, jeton, code QR, Zero Touch**| Oui | Non | Configurable par le biais de la stratégie | [Plus d’informations](android-kiosk-enroll.md)|
|**Android Enterprise complètement managé**|**NFC, jeton, code QR, Zero Touch**| Oui | Oui | Configurable par le biais de la stratégie | [Plus d’informations](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>(Apportez votre propre appareil)
Les appareils BYOD incluent les téléphones, les tablettes et les PC personnels. Les utilisateurs installent et exécutent l’application Portail d’entreprise pour inscrire des appareils BYOD. Ce programme permet aux utilisateurs d’accéder aux ressources de l’entreprise, comme la messagerie électronique.

## <a name="corporate-owned-device"></a>Appareil d’entreprise
Les [appareils de l’entreprise](corporate-identifiers-add.md) incluent les téléphones, les tablettes et les PC appartenant à l’organisation et distribués aux employés. L’inscription des appareils d’entreprise prend en charge des scénarios comme l’inscription automatique, les appareils partagés ou les exigences d’inscription pré-autorisée. Une méthode courante pour inscrire des appareils d’entreprise est l’utilisation du gestionnaire de l’inscription d’appareil par un administrateur ou un responsable. Vous pouvez inscrire des appareils iOS directement via les outils du Programme d’inscription des appareils fournis par Apple. Les appareils avec un numéro IMEI peuvent également être identifiés et référencés comme appartenant à l’entreprise.

### <a name="device-enrollment-manager"></a>Gestionnaire d'inscription d'appareils
Le gestionnaire d’inscription d’appareil est un compte d’utilisateur spécial permettant d’inscrire et de gérer plusieurs appareils d’entreprise. Les responsables peuvent installer le Portail d’entreprise et inscrire de nombreux appareils sans utilisateur. Ces types d’appareils sont adaptés par exemple aux applications utilitaires ou de point de vente, mais ne conviennent pas pour les utilisateurs qui doivent accéder à la messagerie ou à des ressources de l’entreprise. En savoir plus sur le [gestionnaire d’inscription d’appareil](device-enrollment-manager-enroll.md).

### <a name="apple-device-enrollment-program"></a>Programme d'inscription d'appareils Apple
Le programme d’inscription d’appareils Apple (ou DEP) vous permet de créer et déployer une stratégie « à distance » sur des appareils iOSet macOS achetés et gérés avec DEP. L’appareil est inscrit quand l’utilisateur le démarre pour la première fois et exécute l’Assistant d’installation. Cette méthode prend en charge le mode iOS supervisé, qui permet la configuration d’un appareil avec des fonctionnalités spécifiques.

Pour en savoir plus sur l’inscription DEP iOS :

- [Choisir comment inscrire des appareils iOS](ios-enroll.md)
- [Inscrire des appareils iOS à l’aide du programme d’inscription d’appareils](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
Les administrateurs utilisent Apple Configurator, via un port USB, pour préparer manuellement chaque appareil d’entreprise à l’inscription à l’aide de l’Assistant Configuration. Ils créent un profil d’inscription et l’exportent vers Apple Configurator. Lorsque les utilisateurs reçoivent leurs appareils, ils sont invités à exécuter l’Assistant Configuration pour inscrire leurs appareils. Cette méthode prend en charge le mode **iOS supervisé**, qui active les fonctionnalités suivantes :
- Inscription verrouillée
- Mode plein écran et autres configurations et restrictions avancées

Découvrez l’inscription d’Apple Configurator iOS avec l’Assistant Configuration :

- [Choisir la méthode d’inscription des appareils iOS](ios-enroll.md)
- [Inscrire des appareils iOS avec Configurator et l’Assistant Configuration](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
Pour les inscriptions directes, l’administrateur doit inscrire manuellement chaque appareil en créant une stratégie d’inscription et en l’exportant vers Apple Configurator. Les appareils d’entreprise connectés via USB sont inscrits directement et ne nécessitent pas de réinitialisation. Les appareils sont gérés comme des appareils sans utilisateur. Ils ne sont pas verrouillés ni supervisés et ne peuvent pas prendre en charge l’accès conditionnel, la détection de jailbreak ou la gestion des applications mobiles.

Pour en savoir plus sur l’inscription d’appareils iOS, consultez :

- [Choisir la méthode d’inscription des appareils iOS](ios-enroll.md)
- [Inscrire des appareils iOS avec Apple Configurator et l’inscription directe](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Nettoyage de l’appareil mobile après expiration du certificat MDM

Le certificat MDM est renouvelé automatiquement lorsque les appareils mobiles communiquent avec le service Intune. Si des appareils mobiles sont réinitialisés ou ne parviennent pas à communiquer avec le service Intune pendant un certain temps, le certificat MDM n’est pas renouvelé. L’appareil est supprimé du portail Azure 180 jours après l’expiration du certificat MDM.
