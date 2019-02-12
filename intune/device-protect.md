---
title: Protéger des appareils avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Découvrez certaines méthodes permettant à Intune de vous aider à protéger vos appareils contre les accès non autorisés et d’autres menaces.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5743e1d24e878a84413c23c8309cda2ab0dda90
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55844477"
---
# <a name="protect-devices-with-microsoft-intune"></a>Protéger des appareils avec Microsoft Intune

Microsoft Intune vous permet de protéger les appareils que vous gérez et les données stockées sur ces appareils.

## <a name="device-configuration"></a>Configuration des appareils
Les [stratégies de configuration](device-profiles.md) Intune vous permettent de protéger et de configurer des appareils en contrôlant une multitude de paramètres et de fonctionnalités. Par exemple :
- Vous pouvez limiter l’utilisation des fonctionnalités matérielles sur l’appareil, comme l’appareil photo ou le Bluetooth.
- Vous pouvez configurer les applications conformes et non conformes. Vous recevez une alerte lorsqu’une application non conforme est installée (et certaines plateformes peuvent même bloquer l’installation).

## <a name="reset-passcodes-when-users-are-locked-out-of-their-devices"></a>Réinitialiser les codes secrets quand les utilisateurs ne peuvent plus accéder à leur appareil
Sachant que la première mesure à prendre pour protéger les données de l’entreprise sur les appareils mobiles est d’exiger un code secret pour utiliser l’appareil, vous êtes parfois amené à [réinitialiser un code secret](device-passcode-reset.md) ou à aider un employé à le faire en supprimant le code secret ou en définissant un code secret temporaire à distance. Vous pouvez également [verrouiller un appareil à distance](device-remote-lock.md) en cas de perte ou de vol.

## <a name="retire-devices-and-remove-data"></a>Mettre des appareils hors service et supprimer des données
Quand un appareil doit être [retiré de la gestion Intune](devices-wipe.md) (par exemple, quand un utilisateur quitte l’entreprise ou quand l’appareil est perdu ou volé), les données qu’il contient doivent généralement être supprimées. Intune propose tout un éventail de méthodes pour veiller à ce que vos données d’entreprise restent sécurisées.

## <a name="require-devices-to-be-compliant"></a>Exiger la conformité des appareils
Intune comprend des [stratégies de conformité des appareils](device-compliance-get-started.md) qui vous permettent d’évaluer (et dans certains cas corriger) des appareils qui ne sont pas conformes aux règles que vous spécifiez. Par exemple, vous pouvez générer des rapports concernant :
- Les appareils iOS jailbreakés
- Les appareils chiffrés ou non chiffrés
- L’intégrité des appareils Windows 10 (tel que déterminé par le Service d’attestation d’intégrité)

## <a name="protect-apps-and-the-data-they-use"></a>Protéger les applications et les données qu’elles utilisent
Intune vous propose tout un éventail de fonctionnalités pour vous permettre de protéger les applications et leurs données. Par exemple, les stratégies de gestion des applications mobiles peuvent :
- Empêcher les données d’être sauvegardées à partir d’une application protégée
- Restreindre les opérations de copier-coller pour les autres applications
- Exiger un PIN pour accéder à une application Pour plus d’informations, consultez [Protéger les données et les applications avec Microsoft Intune](app-protection-policy.md).

## <a name="add-an-additional-layer-of-protection-to-devices"></a>Ajouter une couche supplémentaire de protection sur des appareils
L’[authentification multifacteur (MFA)](multi-factor-authentication.md) est un moyen plus sûr d’authentifier les utilisateurs d’appareils sur le réseau.  Avec MFA, les utilisateurs doivent confirmer leur identité au-delà du nom d’utilisateur et du mot de passe, via un appel téléphonique ou un message texte.

## <a name="control-windows-hello-for-business-settings-on-windows-devices"></a>Contrôler les paramètres Windows Hello Entreprise sur des appareils Windows
Intune vous permet d’intégrer [Windows Hello Entreprise](windows-hello.md) et de disposer ainsi d’une autre méthode de connexion pour Windows 10 et ultérieur utilisant Active Directory ou un compte Azure Active Directory pour remplacer un mot de passe, une carte à puce ou une carte à puce virtuelle.

## <a name="bypass-activation-lock-on-ios-devices"></a>Contourner le verrou d’activation sur les appareils iOS
Le verrou d’activation est une fonctionnalité qui permet de protéger les appareils. Cette fonctionnalité demande aux utilisateurs d’entrer leur identifiant et leur mot de passe Apple avant d’effacer ou de réactiver l’appareil. Toutefois, elle peut engendrer des problèmes, par exemple, si l’utilisateur quitte l’entreprise sans supprimer le verrou. [Le contournement du verrou d’activation iOS]( device-activation-lock-bypass.md) peut vous aider en supprimant le verrou des appareils iOS supervisés pour vous permettre de les réaffecter ou de les effacer.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur [Mobile Threat Defense](mobile-threat-defense.md)


