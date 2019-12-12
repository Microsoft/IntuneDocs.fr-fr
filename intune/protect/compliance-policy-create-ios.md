---
title: Paramètres de conformité des appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser lorsque vous configurez la conformité de vos appareils iOS dans Microsoft Intune. Exigez une adresse e-mail, vérifiez les appareils jailbreakés ou rootés, définissez les versions minimale et maximale autorisées pour le système d’exploitation, définissez des restrictions de mot de passe (concernant notamment sa longueur et la durée d’inactivité de l’appareil), définissez des restrictions d’applications, etc.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b83b764af415349b287df2a09f9b4c355734c28
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810241"
---
# <a name="ios-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres iOS pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils iOS dans Intune. Dans le cadre de votre solution de gestion des appareils mobiles (MDM), vous pouvez utiliser ces paramètres pour exiger une adresse e-mail, marquer les appareils rootés (jailbreakés) comme étant non conformes, définir le niveau de menace autorisé, définir l’expiration des mots de passe, etc.

Cette fonctionnalité s’applique à :

- iOS
- iPados

En tant qu’administrateur de service Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour l’option **Plateforme**, sélectionnez **iOS/iPadOS**.

## <a name="email"></a>E-mail

- **Exiger que les appareils mobiles aient un profil de messagerie géré** :  
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : les appareils qui n’ont pas de profil de messagerie géré par Intune sont considérés comme non conformes. Un appareil ne peut pas avoir de profil de messagerie géré quand il n’est pas correctement ciblé, ou si l’utilisateur configure manuellement le compte e-mail sur cet appareil.

  L’appareil est considéré comme non conforme dans les situations suivantes :  
  - Le profil de messagerie est affecté à un groupe d’utilisateurs autre que celui ciblé par la stratégie de conformité.
  - L’utilisateur a déjà configuré sur l’appareil un compte e-mail qui correspond au profil de messagerie Intune déployé sur l’appareil. Intune ne peut pas remplacer le profil configuré par l’utilisateur et ne peut pas le gérer. Pour garantir la conformité, l’utilisateur final doit supprimer les paramètres d’e-mail existants. Ensuite, Intune peut installer le profil de messagerie géré.  

Pour plus d’informations sur les profils de messagerie, consultez [Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Intune](../configuration/email-settings-configure.md).

## <a name="device-health"></a>Intégrité de l’appareil

- **Appareils jailbreakés** :  
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Bloquer** : marquer les appareils rootés (jailbreakés) comme étant non conformes.  

- **Exiger que l’appareil soit au niveau ou sous le niveau de défense contre les menaces mobiles** *(iOS 8.0 et versions ultérieures)* :  
  Utilisez ce paramètre pour prendre l’évaluation des risques comme condition de conformité. Choisissez le niveau de menace autorisé :  
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Sécurisé** : cette option est la plus sécurisée. Elle signifie que l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est évalué comme conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, car elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.

## <a name="device-properties"></a>Propriétés de l’appareil

### <a name="operating-system-version"></a>Version du système d'exploitation  

- **Système d’exploitation minimal requis** *(iOS 8,0 et versions ultérieures)* :  
  Quand un appareil ne répond pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil. Ensuite, il peut accéder aux ressources de l’entreprise.

- **Version maximale autorisée du système d’exploitation** *(iOS 8,0 et versions ultérieures)* :  
  Quand un appareil utilise une version du système d’exploitation postérieure à la version dans la règle, l’accès aux ressources de l’organisation est bloqué. L’utilisateur final est invité à contacter son administrateur informatique. L’appareil ne peut pas accéder aux ressources de l’organisation tant qu’une règle n’est pas modifiée pour autoriser cette version du système d’exploitation.

- **Version minimale de la build du système d’exploitation** *(iOS 8,0 et versions ultérieures)* :  
  quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, et non la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé minimal sur l’appareil.

- **Version maximale de la build du système d’exploitation** *(iOS 8,0 et versions ultérieures)* :  
  quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, et non la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé maximal sur l’appareil.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

> [!NOTE]
> Une fois qu’une stratégie de conformité ou de configuration est appliquée à un appareil iOS, les utilisateurs sont invités à définir un code secret toutes les 15 minutes. Tant que les utilisateurs n’ont pas défini de code secret, ils sont invités à le faire. Lorsqu’un code secret est défini pour l’appareil iOS, le processus de chiffrement démarre automatiquement. L’appareil reste chiffré jusqu’à ce que le code secret soit désactivé.

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** :  
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.  
  - **Exiger** : les utilisateurs doivent entrer un mot de passe pour pouvoir accéder à leur appareil. Les appareils iOS utilisant un mot de passe sont chiffrés.

- **Mots de passe simples** :  
  - **Non configuré** (*par défaut*) : les utilisateurs peuvent créer des mots de passe simples comme **1234** ou **1111**.
  - **Bloquer** : les utilisateurs ne peuvent pas créer de mots de passe simples, comme **1234** ou **1111**. 

- **Longueur minimale du mot de passe** :  
  entrez le nombre minimal de chiffres ou de caractères que doit comporter le mot de passe.  

- **Type de mot de passe requis** :  
  choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumérique**).

- **Nombre de caractères non alphanumériques dans le mot de passe** :  
  Entrez le nombre minimal de caractères spéciaux (`&`, `#`, `%`, `!`, etc.) qui doivent être inclus dans le mot de passe. 

  Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe.

- **Nombre maximal de minutes entre le verrouillage de l’écran et la demande du mot de passe** *(iOS 8.0 et versions ultérieures)*  :  
  Spécifiez le délai de verrouillage de l’écran avant qu’un utilisateur doive entrer un mot de passe pour accéder à l’appareil. Les options incluent la valeur par défaut *non configurée*, *immédiatement*et entre *1 minute* et *4 heures*.

- **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** :  
  Entrez la durée d’inactivité avant que l’appareil ne verrouille son écran. Les options incluent la valeur par défaut *non configurée* *immédiatement*, et de *1 minute* à *15 minutes*.

- **Expiration du mot de passe (en jours)** :  
  sélectionnez le nombre de jours avant que le mot de passe n’expire et que l’utilisateur ne doive en créer un autre. 

- **Nombre de mots de passe précédents pour empêcher la réutilisation** *(iOS 8.0 et versions ultérieures)* :   
  Entrez le nombre de mots de passe précédemment utilisés qui ne peuvent pas être utilisés.

### <a name="device-security"></a>Sécurité du périphérique

- **Applications restreintes** :  
  Vous pouvez restreindre les applications en ajoutant leurs ID de bundle à la stratégie. Si l’application est installée sur l’appareil, celui-ci est marqué comme non conforme.

  - **Nom de l’application** : entrez un nom convivial pour faciliter l’identification de l’ID de bundle.
  - **ID d’ensemble d’applications** : entrez l’identificateur unique du bundle affecté par le fournisseur de l’application. Pour trouver l’ID de bundle, consultez [Guide pratique pour trouver l’ID de bundle pour une application iOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app) (ouvre un autre site web Microsoft).  

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils macOS](compliance-policy-create-mac-os.md).
