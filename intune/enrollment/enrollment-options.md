---
title: Options d’inscription pour les appareils gérés par Microsoft Intune
titleSuffix: ''
description: Liste des options d’inscription que les administrateurs peuvent définir pour les appareils gérés par Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8c502bd42d3290bd03c0ce954d55de3073c3f2d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503216"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Options d’inscription pour les appareils gérés par Intune

En tant qu’administrateur Intune, vous pouvez faciliter l’inscription des appareils des utilisateurs et activer des fonctionnalités Intune.  Intune propose les options d’inscription suivantes :

## <a name="terms-and-conditions"></a>Conditions générales

Vous pouvez demander aux utilisateurs d’accepter les conditions générales de votre entreprise avant d’utiliser le portail d’entreprise pour inscrire leurs appareils et accéder à des ressources telles que les applications et la messagerie de l’entreprise. La configuration des conditions générales est facultative. En savoir plus sur les [conditions générales](terms-and-conditions-create.md).

## <a name="enrollment-restrictions"></a>Restrictions d’inscription

Vous pouvez choisir de restreindre l’inscription d’appareils par :
- Plateforme d’appareils
- Nombre d’appareils par utilisateur
- Appareils personnels (blocage)

En savoir plus sur les [restrictions d’inscription](enrollment-restrictions-set.md).

## <a name="enable-apple-device-enrollment"></a>Autoriser l’inscription des appareils Apple

L’inscription des appareils iOS et macOS nécessite un certificat Push MDM. En savoir plus sur les [certificats Push MDM](apple-mdm-push-certificate-get.md).

## <a name="corporate-identifiers"></a>Identificateurs d’entreprise

Vous pouvez recenser les numéros IMEI (International Mobile Equipment Identifier) et les numéros de série pour identifier les appareils qui appartiennent à l’entreprise. En savoir plus sur les [identificateurs d’entreprise](corporate-identifiers-add.md).
## <a name="multi-factor-authentication"></a>Authentification multifacteur

Vous pouvez demander aux utilisateurs d’utiliser une méthode de vérification supplémentaire, comme un téléphone, un code PIN ou des données biométriques, quand ils inscrivent un appareil. Découvrez plus d’informations sur [l’authentification multifacteur](multi-factor-authentication.md).

## <a name="device-enrollment-manager"></a>Gestionnaire d'inscription d'appareils
Vous pouvez attribuer le rôle de gestionnaire d’inscription d’appareils à des utilisateurs.  Ceux-ci peuvent alors inscrire un grand nombre d’appareils mobiles avec un même compte d’utilisateur. Un compte de gestionnaire d’inscription d’appareils permet d’inscrire jusqu’à 1 000 appareils. En savoir plus sur les [gestionnaires d’inscription d’appareils](device-enrollment-manager-enroll.md).

## <a name="device-categories"></a>Catégories d’appareils

Vous pouvez utiliser des catégories d’appareil pour ajouter automatiquement des appareils à des groupes en fonction des catégories que vous définissez. Le fait d’organiser les appareils dans des groupes permet de faciliter leur gestion. En savoir plus sur les [catégories d’appareil](device-group-mapping.md).
