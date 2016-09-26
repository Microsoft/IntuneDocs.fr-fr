---
title: Inscrire des appareils | Microsoft Intune
description: "La gestion des appareils mobiles utilise l’inscription pour gérer les appareils et leur autoriser l’accès aux ressources."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d1b6fea5284f7825da412351f5b5d5f2a47857d
ms.openlocfilehash: caef9301c965704893b3a546429760cf779579f2


---

# Inscrire des appareils pour la gestion dans Intune
Vous pouvez inscrire des appareils, y compris des PC Windows, pour utiliser la gestion des appareils mobiles avec Microsoft Intune. Cette rubrique décrit différentes façons d’inscrire des appareils mobiles dans la gestion Intune. La méthode d’inscription utilisée dépend du type d’appareil, de son propriétaire et du niveau de gestion souhaité. L’inscription BYOD (« Bring your own device ») permet aux utilisateurs d’inscrire leurs téléphones, tablettes ou PC personnels. L’inscription COD (« Corporate-owned device ») permet de gérer des appareils d’entreprise en utilisant des fonctionnalités telles que la réinitialisation à distance, le partage d’appareils ou l’affinité utilisateur.

Si vous utilisez [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune) (soit localement, soit hébergé dans le cloud), vous pouvez choisir la gestion Intune simple sans inscription. Vous pouvez également gérer des PC Windows à l’aide du [logiciel client Intune](#manage-windows-pcs-with-intune).

## Présentation des méthodes d’inscription des appareils

Le tableau suivant présente les différentes méthodes d’inscription dans Intune et les fonctionnalités qu’elles prennent en charge. Ces fonctionnalités sont les suivantes :
- **Réinitialisation** : réinitialise l’appareil aux paramètres d’usine, en supprimant toutes les données. [Mettre des appareils hors service](retire-devices-from-microsoft-intune-management.md)
- **Affinité** : associe les appareils à des utilisateurs. Fonctionnalité nécessaire pour la gestion des applications mobiles (GAM) et l’accès conditionnel aux données d’entreprise. [Affinité utilisateur](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **Verrouillage** : empêche les utilisateurs de retirer leur appareil de la gestion. Les appareils iOS nécessitent le mode de verrouillage Supervisé. [Verrouillage à distance](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**Méthodes d’inscription iOS**

| **Méthode** |  **Réinitialisation** |  **Affinité**    |   **Verrouiller** | **Détails** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Non|    Oui |   Non | [plus](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[Gestionnaire d’inscription d’appareil](#dem)**|   Non |Non |Non  | [plus](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Oui |   Facultatif |  Facultatif|[plus](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Oui |   Facultatif |  Non| [plus](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| Non |    Non  | Non|[plus](ios-direct-enrollment-in-microsoft-intune.md)|

**Méthodes d’inscription Windows et Android**

| **Méthode** |  **Réinitialisation** |  **Affinité**    |   **Verrouiller** | **Détails**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Non|    Oui |   Non | [plus](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[Gestionnaire d’inscription d’appareil](#dem)**|   Non |Non |Non  |[plus](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Pour répondre à une série de questions qui vous aideront à déterminer la méthode appropriée, consultez [Choisir comment inscrire des appareils](/intune/get-started/choose-how-to-enroll-devices1).

## BYOD
Les utilisateurs d’appareils personnels installent l’application Portail d’entreprise et inscrivent leurs propres appareils. Ils peuvent ensuite se connecter au réseau d’entreprise et rejoindre le domaine ou Azure Active Directory. L’activation de la méthode d’inscription BYOD est nécessaire dans de nombreux scénarios COD pour la plupart des plateformes. Consultez [Conditions préalables à l’inscription d’appareils](prerequisites-for-enrollment.md). ([Retour au tableau](#overview-of-device-enrollment-methods))

## Appareils d’entreprise
Vous pouvez gérer les appareils d’entreprise (COD, Corporate-Owned Devices) avec la console Intune. Vous pouvez inscrire les appareils iOS directement par le biais d’outils fournis par Apple. Tous les types d’appareils peuvent être inscrits par un administrateur ou un gestionnaire à l’aide du Gestionnaire d’inscription d’appareil. Les appareils dotés d’un numéro IMEI peuvent également être identifiés et référencés comme appartenant à l’entreprise pour activer des scénarios COD.

[Inscrire des appareils d’entreprise](manage-corporate-owned-devices.md)

### Gestionnaire d’inscription d’appareil
Le gestionnaire d’inscription d’appareil est un compte Intune spécial permettant d’inscrire et de gérer plusieurs appareils d’entreprise. Les responsables peuvent installer le Portail d’entreprise et inscrire de nombreux appareils sans utilisateur. En savoir plus sur le [gestionnaire d’inscription d’appareil](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Retour au tableau](#overview-of-device-enrollment-methods))

### DEP
Le programme d’inscription d’appareils Apple (ou DEP) vous permet de créer et déployer une stratégie « à distance » sur des appareils iOS achetés et gérés avec DEP. L’appareil est inscrit quand l’utilisateur le démarre pour la première fois et exécute l’Assistant d’installation iOS. Cette méthode prend en charge le mode **iOS supervisé** qui permet à son tour ce qui suit :
  - Inscription verrouillée
  - Accès conditionnel
  - Détection de jailbreak
  - Gestion des applications mobiles

En savoir plus sur le programme [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Retour au tableau](#overview-of-device-enrollment-methods))

### USB-SA
Connexion USB, inscription avec l’Assistant Configuration. L’administrateur crée une stratégie Intune et l’exporte vers Apple Configurator. Les appareils d’entreprise connectés par USB sont préparés à l’aide d’une stratégie Intune. L’administrateur doit inscrire manuellement chaque appareil. Les utilisateurs reçoivent leur appareil et exécutent l’Assistant Configuration pour inscrire leur appareil. Cette méthode prend en charge le mode **iOS supervisé** qui permet à son tour ce qui suit :
  - Accès conditionnel
  - Détection de jailbreak
  - Gestion des applications mobiles

En savoir plus sur l’[inscription de l’Assistant Configuration avec Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Retour au tableau](#overview-of-device-enrollment-methods))

### USB-Direct
Inscription directe. L’administrateur crée une stratégie Intune et l’exporte vers Apple Configurator. Les appareils d’entreprise connectés par USB sont inscrits directement sans qu’une réinitialisation aux paramètres d’usine soit nécessaire. L’administrateur doit inscrire manuellement chaque appareil. Les appareils sont gérés comme des appareils sans utilisateur. Ils ne sont pas verrouillés ni supervisés et ne peuvent pas prendre en charge l’accès conditionnel, la détection de jailbreak ni la gestion des applications mobiles. En savoir plus sur l’[inscription directe avec Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Retour au tableau](#overview-of-device-enrollment-methods))

## Gestion des appareils mobiles à l’aide d’Exchange ActiveSync et d’Intune
Les appareils mobiles qui ne sont pas inscrits mais qui se connectent à Exchange ActiveSync (EAS) peuvent être gérés par Intune à l’aide de la stratégie de gestion des appareils mobiles EAS. Intune utilise un connecteur Exchange pour communiquer avec EAS, localement ou hébergé dans le cloud.

[Gestion des appareils mobiles à l’aide d’Exchange ActiveSync et d’Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Gérer des PC Windows avec Intune  
Vous pouvez également utiliser Microsoft Intune pour gérer des PC Windows à l’aide du logiciel client Intune. Les PC gérés avec le client Intune peuvent :

 - Fournir un inventaire logiciel et matériel
 - Installer des applications de bureau (par exemple des fichiers .exe et .msi)
 - Paramètres du pare-feu

Les PC gérés avec le logiciel client Intune ne peuvent pas être réinitialisés, et ne peuvent pas utiliser de nombreuses fonctionnalités de gestion Intune telles que l’accès conditionnel, les paramètres VPN et Wi-Fi, ou le déploiement de certificats et de configurations de messagerie.

[Gérer des PC Windows avec Intune](manage-windows-pcs-with-microsoft-intune.md)

##  Plateformes d’appareil prises en charge

Intune peut gérer les plateformes d’appareils suivantes :

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Étapes suivantes
- [Conditions préalables à l’inscription d’appareils](prerequisites-for-enrollment.md)
- [Gérer les appareils d’entreprise](manage-corporate-owned-devices.md)
- [Ordinateurs et appareils mobiles pris en charge](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Sep16_HO3-->


