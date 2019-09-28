---
title: Paramètres de conformité des appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser lorsque vous configurez la conformité de vos appareils iOS dans Microsoft Intune. Exigez une adresse e-mail, vérifiez les appareils jailbreakés ou rootés, définissez les versions minimale et maximale autorisées pour le système d’exploitation, définissez des restrictions de mot de passe (concernant notamment sa longueur et la durée d’inactivité de l’appareil), définissez des restrictions d’applications, etc.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bde1c296abb99e8c0c81b44908e78b204c62388e
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "71304125"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres iOS pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils iOS dans Intune. Dans le cadre de votre solution de gestion des appareils mobiles (MDM), vous pouvez utiliser ces paramètres pour exiger une adresse e-mail, marquer les appareils rootés (jailbreakés) comme étant non conformes, définir le niveau de menace autorisé, définir l’expiration des mots de passe, etc.

Cette fonctionnalité s’applique à :

- iOS

En tant qu’administrateur de service Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour l’option **Plateforme**, sélectionnez **iOS**.

## <a name="email"></a>E-mail

- **Exiger un profil de messagerie géré pour les appareils mobiles** : si vous définissez cette option sur **Exiger**, les appareils qui n’ont pas de profil de messagerie géré par Intune sont considérés comme non conformes. Un appareil ne peut pas avoir de profil de messagerie géré quand il n’est pas correctement ciblé, ou si l’utilisateur configure manuellement le compte e-mail sur cet appareil. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

  L’appareil est considéré comme non conforme dans les situations suivantes :

  - Le profil de messagerie est affecté à un groupe d’utilisateurs autre que celui ciblé par la stratégie de conformité.
  - L’utilisateur a déjà configuré sur l’appareil un compte e-mail qui correspond au profil de messagerie Intune déployé sur l’appareil. Intune ne peut pas remplacer le profil configuré par l’utilisateur et ne peut pas le gérer. Pour garantir la conformité, l’utilisateur final doit supprimer les paramètres d’e-mail existants. Ensuite, Intune peut installer le profil de messagerie géré.

- **Sélectionnez le profil de messagerie géré par Intune** : si vous sélectionnez l’option **Le compte e-mail doit être géré par Intune**, choisissez **Sélectionner** pour spécifier le profil de messagerie Intune. Le profil de messagerie doit exister sur l’appareil.

Pour plus d’informations sur les profils de messagerie, consultez [Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Intune](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Appareils jailbreakés** : choisissez **Bloquer** pour marquer les appareils rootés (jailbreakés) comme étant non conformes. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Exiger que l’appareil se situe au niveau de menace d’appareil ou en dessous** (iOS 8.0 et ultérieur) : utilisez ce paramètre pour considérer l’évaluation des risques comme une condition de conformité. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Pour utiliser ce paramètre, choisissez le niveau de menace autorisé :
  - **Sécurisé** : cette option est la plus sécurisée. Elle signifie que l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est évalué comme conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, car elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.

## <a name="device-properties"></a>Propriétés des appareils

- **Version minimale du système d’exploitation** (iOS 8.0 et ultérieur) : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil. Ensuite, il peut accéder aux ressources de l’entreprise.
- **Version maximale du système d’exploitation** (iOS 8.0 et ultérieur) : quand un appareil utilise une version du système d’exploitation ultérieure à celle spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur final est invité à contacter son administrateur informatique. L’appareil ne peut pas accéder aux ressources de l’organisation tant qu’une règle n’est pas modifiée pour autoriser cette version du système d’exploitation.
- **Version de build minimale du système d’exploitation** (iOS 8.0 et ultérieur) : quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, mais pas la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé minimal sur l’appareil.
- **Version de build maximale du système d’exploitation** (iOS 8.0 et ultérieur) : quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, mais pas la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé maximal sur l’appareil.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

> [!NOTE]
> Une fois qu’une stratégie de conformité ou de configuration est appliquée à un appareil iOS, les utilisateurs sont invités à définir un code secret toutes les 15 minutes. Tant que les utilisateurs n’ont pas défini de code secret, ils sont invités à le faire.

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil. Les appareils iOS utilisant un mot de passe sont chiffrés.
- **Mots de passe simples** : choisissez **Bloquer** pour que les utilisateurs ne puissent pas créer de mots de passe simples, par exemple **1234** ou **1111**. Choisissez **Non configuré** pour permettre aux utilisateurs de créer des mots de passe tels que **1234** ou **1111**.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe.
- **Type de mot de passe obligatoire** : choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumériques**).
- **Nombre de caractères non alphanumériques dans le mot de passe** : entrez le nombre minimal de caractères spéciaux (`&`, `#`, `%`, `!`, etc.) à inclure dans le mot de passe.

    Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe.

- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et l’obligation d’en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre d’anciens mots de passe qui ne peuvent pas être réutilisés.

### <a name="device-security"></a>Sécurité des appareils

- **Applications restreintes** : vous pouvez restreindre les applications en ajoutant leurs ID de bundle à la stratégie. Si l’application est installée sur l’appareil, celui-ci est marqué comme non conforme.

  - **Nom de l’application** : entrez un nom convivial pour faciliter l’identification de l’ID de bundle.
  - **ID d’ensemble d’applications** : entrez l’identificateur unique du bundle affecté par le fournisseur de l’application. Pour trouver l’ID de bundle, consultez [Guide pratique pour trouver l’ID de bundle pour une application iOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (ouvre un autre site web Microsoft).  

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils macOS](compliance-policy-create-mac-os.md).
