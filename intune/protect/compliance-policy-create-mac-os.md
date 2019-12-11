---
title: Paramètres de conformité des appareils macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser lorsque vous configurez la conformité de vos appareils macOS dans Microsoft Intune. Exigez la protection de l’intégrité des systèmes Apple, définissez des restrictions de mot de passe, exigez un pare-feu, autorisez Gatekeeper, etc.
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
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813504"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres macOS pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils macOS dans Intune. Dans le cadre de votre solution de gestion des appareils mobiles, vous pouvez utiliser ces paramètres pour définir une version minimale ou maximale de système d’exploitation, définir l’expiration des mots de passe, etc.

Cette fonctionnalité s’applique à :

- macOS

En tant qu’administrateur de service Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour l’option **Plateforme**, sélectionnez **macOS**.

## <a name="device-health"></a>Intégrité de l’appareil

- **Exiger une protection de l’intégrité du système**:  
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** -exiger que les appareils MacOS bénéficient d’une [protection de l’intégrité du système](https://support.apple.com/HT204899) (ouvre le site Web d’Apple).  

## <a name="device-properties"></a>Propriétés de l’appareil

- **Système d’exploitation minimal requis** :  
  Quand un appareil ne répond pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur peut choisir de mettre à niveau son appareil. Ensuite, il peut accéder aux ressources de l’entreprise.

- **Version maximale autorisée du système d’exploitation** :  
  Quand un appareil utilise une version du système d’exploitation postérieure à la version dans la règle, l’accès aux ressources de l’organisation est bloqué. L’utilisateur de l’appareil est invité à contacter son administrateur informatique. L’appareil ne peut pas accéder aux ressources de l’organisation tant qu’une règle n’est pas modifiée pour autoriser cette version du système d’exploitation.

- **Version de build du système d’exploitation minimale** :  
  quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, et non la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé minimal sur l’appareil.

- **Version de build du système d’exploitation maximale** :  
  quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, et non la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé maximal sur l’appareil.

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** :  
  - **Non configuré** (*par défaut*)
  - **Exiger** : les utilisateurs doivent entrer un mot de passe pour pouvoir accéder à leur appareil.

- **Mots de passe simples** :  
  - **Non configuré** (*par défaut*) : les utilisateurs peuvent créer des mots de passe simples comme **1234** ou **1111**.
  - **Bloquer** : les utilisateurs ne peuvent pas créer de mots de passe simples, comme **1234** ou **1111**.

- **Longueur minimale du mot de passe** :  
  entrez le nombre minimal de chiffres ou de caractères que doit comporter le mot de passe.

- **Type de mot de passe** : choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumériques**).

- **Nombre de caractères non alphanumériques dans le mot de passe** :  
  Entrez le nombre minimal de caractères spéciaux (`&`, `#`, `%`, `!`, etc.) qui doivent être inclus dans le mot de passe.

  Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe.

- **Durée d’inactivité maximale en minutes avant demande du mot de passe** :  
  entrez la durée d’inactivité au terme de laquelle l’utilisateur doit entrer à nouveau son mot de passe.

- **Expiration du mot de passe (en jours)** :  
  sélectionnez le nombre de jours avant que le mot de passe n’expire et que l’utilisateur ne doive en créer un autre.

- **Nombre de mots de passe précédents pour empêcher la réutilisation** :  
  Entrez le nombre de mots de passe précédemment utilisés qui ne peuvent pas être utilisés.
> [!IMPORTANT]
> Quand les exigences de mot de passe sont changées sur un appareil macOS, elles n’entrent pas en vigueur tant que l’utilisateur ne change pas son mot de passe. Par exemple, si vous fixez la longueur minimale du mot de passe à huit chiffres et si l’appareil macOS a un mot de passe de six chiffres, il reste conforme jusqu’à ce que l’utilisateur mette à jour son mot de passe.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur un appareil** :  
  - **Non configuré** (*par défaut*)
  - **Exiger** : utilisez *Exiger* pour chiffrer le stockage de données sur vos appareils.

### <a name="device-security"></a>Sécurité du périphérique

Le Pare-feu protège les appareils contre tout accès réseau non autorisé. Vous pouvez utiliser le Pare-feu afin de contrôler les connexions pour chaque application. 

- **Pare-feu** :  
  - **Non configuré** (*par défaut*) : ce paramètre laisse le Pare-feu désactivé, et le trafic réseau est autorisé (non bloqué).
  - **Activer** : utilisez *Activer* pour protéger les appareils contre tout accès non autorisé. L’activation de cette fonctionnalité vous permet de gérer les connexions Internet entrantes et d’utiliser le mode furtif. 

- **Connexions entrantes** :  
  - **Non configuré** (*par défaut*) : autorise les connexions entrantes et les services de partage.
  - **Bloquer** : bloquer toutes les connexions réseau entrantes, à l’exception des connexions nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Ce paramètre bloque également tous les services de partage, y compris le partage d’écran, l’accès à distance, le partage de musique iTunes, etc.  

- **Mode furtif** :  
  - **Non configuré** (*valeur par défaut*) : ce paramètre laisse le mode furtif désactivé.
  - **Activer** : activer le mode furtif pour empêcher l’appareil de répondre aux requêtes de sondage, qui peuvent provenir d’utilisateurs malveillants. Quand cette option est activée, l’appareil continue de répondre aux requêtes entrantes des applications autorisées.  

### <a name="gatekeeper"></a>Gatekeeper

Pour plus d’informations, consultez [Gatekeeper sur macOS](https://support.apple.com/HT202491) (ouvre le site web d’Apple).

**Autoriser les applications téléchargées à partir de ces emplacements** : autorise l’installation des applications prises en charge sur vos appareils à partir de différents emplacements. Options d’emplacement :

- **Non configuré** (*valeur par défaut*) : l’option Gatekeeper n’a aucun impact sur la conformité ou la non-conformité.  
- **Mac App Store** : installer uniquement des applications pour le Mac App Store. Les applications ne peuvent pas être installées par des tiers ou des développeurs non identifiés. Si un utilisateur sélectionne Gatekeeper pour installer des applications en dehors de Mac App Store, l’appareil est considéré comme non conforme.
- **Mac App Store et développeurs identifiés** : installer des applications pour le Mac App Store et par le biais de développeurs identifiés. macOS vérifie l’identité des développeurs et fait quelques autres vérifications portant sur l’intégrité de l’application. Si un utilisateur sélectionne Gatekeeper pour installer des applications en dehors de ces options, l’appareil est considéré comme non conforme.
- **Partout** : les applications peuvent être installées depuis n’importe où et par n’importe quel développeur. Cette option est la moins sécurisée.
 

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils iOS](compliance-policy-create-ios.md).