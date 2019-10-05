---
title: Paramètres de conformité des appareils macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser lorsque vous configurez la conformité de vos appareils macOS dans Microsoft Intune. Exigez la protection de l’intégrité des systèmes Apple, définissez des restrictions de mot de passe, exigez un pare-feu, autorisez Gatekeeper, etc.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22bd3dd50f6c2cbeba59aad4dd00683d52668f72
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733034"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres macOS pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils macOS dans Intune. Dans le cadre de votre solution de gestion des appareils mobiles, vous pouvez utiliser ces paramètres pour définir une version minimale ou maximale de système d’exploitation, définir l’expiration des mots de passe, etc.

Cette fonctionnalité s’applique à :

- macOS

En tant qu’administrateur de service Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour l’option **Plateforme**, sélectionnez **macOS**.

## <a name="device-health"></a>Intégrité de l’appareil

- **Exiger la protection de l’intégrité du système** : vous pouvez **exiger** que la [Protection de l’intégrité du système](https://support.apple.com/HT204899) soit activée sur les appareils macOS (ouvre le site web d’Apple). Quand vous définissez la valeur **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

## <a name="device-properties"></a>Propriétés des appareils

- **Version minimale du système d’exploitation** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau apparaît. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.
- **Version maximale du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant que la règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.
- **Version de build du système d’exploitation minimale** : quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, pas la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé minimal sur l’appareil.
- **Version de build du système d’exploitation maximale** : quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, pas la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé maximal sur l’appareil.

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil.
- **Mots de passe simples** : choisissez **Bloquer** pour que les utilisateurs ne puissent pas créer de mots de passe simples, par exemple **1234** ou **1111**. Choisissez **Non configuré** pour permettre aux utilisateurs de créer des mots de passe tels que **1234** ou **1111**.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe.
- **Type de mot de passe** : choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumériques**).
- **Nombre de caractères non alphanumériques dans le mot de passe** : entrez le nombre minimal de caractères spéciaux (`&`, `#`, `%`, `!`, etc.) à inclure dans le mot de passe.

    Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe.

- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et l’obligation d’en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre d’anciens mots de passe qui ne peuvent pas être réutilisés.

    > [!IMPORTANT]
    > Quand les exigences de mot de passe sont changées sur un appareil macOS, elles n’entrent pas en vigueur tant que l’utilisateur ne change pas son mot de passe. Par exemple, si vous fixez la longueur minimale du mot de passe à huit chiffres et si l’appareil macOS a un mot de passe de six chiffres, il reste conforme jusqu’à ce que l’utilisateur mette à jour son mot de passe.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** : choisissez **Exiger** pour chiffrer le stockage des données sur vos appareils.

### <a name="device-security"></a>Sécurité du périphérique

Le Pare-feu protège les appareils contre tout accès réseau non autorisé. Vous pouvez utiliser le Pare-feu afin de contrôler les connexions pour chaque application. 

- **Pare-feu** : sélectionnez **Activer** pour protéger les appareils contre tout accès non autorisé. L’activation de cette fonctionnalité vous permet de gérer les connexions Internet entrantes et d’utiliser le mode furtif. L’option **Non configuré** (par défaut) laisse le Pare-feu désactivé, et le trafic réseau est autorisé (non bloqué).
- **Connexions entrantes** : **bloque** toutes les connexions réseau entrantes, à l’exception des connexions nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Ce paramètre bloque également tous les services de partage, y compris le partage d’écran, l’accès à distance, le partage de musique iTunes, etc. L’option **Non configuré** (par défaut) autorise les connexions entrantes et les services de partage.
- **Mode furtif** : sélectionnez l’option **Activer** pour empêcher l’appareil de répondre aux requêtes de sondage, qui peuvent provenir d’utilisateurs malveillants. Quand cette option est activée, l’appareil continue de répondre aux requêtes entrantes des applications autorisées. L’option **Non configuré** (par défaut) laisse le mode furtif désactivé.

### <a name="gatekeeper"></a>Gatekeeper

Pour plus d’informations, consultez [Gatekeeper sur macOS](https://support.apple.com/HT202491) (ouvre le site web d’Apple).

**Autoriser les applications téléchargées à partir de ces emplacements** : autorise l’installation des applications prises en charge sur vos appareils à partir de différents emplacements. Options d’emplacement :

- **Non configuré** : par défaut. L’option Gatekeeper n’a aucun impact sur la conformité ou la non-conformité. 
- **Mac App Store** : installer uniquement des applications pour le Mac App Store. Les applications ne peuvent pas être installées par des tiers ou des développeurs non identifiés. Si un utilisateur sélectionne Gatekeeper pour installer des applications en dehors de Mac App Store, l’appareil est considéré comme non conforme.
- **Mac App Store et développeurs identifiés** : installer des applications pour le Mac App Store et par le biais de développeurs identifiés. macOS vérifie l’identité des développeurs et fait quelques autres vérifications portant sur l’intégrité de l’application. Si un utilisateur sélectionne Gatekeeper pour installer des applications en dehors de ces options, l’appareil est considéré comme non conforme.
- **Partout** : les applications peuvent être installées depuis n’importe où et par n’importe quel développeur. Cette option est la moins sécurisée.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils iOS](compliance-policy-create-ios.md).