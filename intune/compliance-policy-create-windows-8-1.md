---
title: Paramètres de conformité de Windows 8.1 dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser quand vous configurez la conformité de vos appareils Windows 8.1 et Windows Phone 8.1 dans Microsoft Intune. Vérifiez la conformité sur le système d’exploitation minimal et maximal, définissez des restrictions et une longueur de mot de passe, activez le chiffrement sur le stockage de données, etc.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57a860edd99bfbbd41ff7df8fd98d0343f4f5ba6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "71304111"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres de Windows 8.1 pour marquer les appareils comme étant conformes ou non conformes avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils Windows 8.1 dans Intune. Dans le cadre de votre solution MDM, utilisez ces paramètres pour bloquer les mots de passe simples, définir une version minimale ou maximale du système d’exploitation, etc.

Cette fonctionnalité s’applique à :

- Windows Phone 8.1
- Windows 8.1 et versions ultérieures

En tant qu’administrateur Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour **Plateforme**, sélectionnez **Windows Phone 8.1** ou **Windows 8.1 et ultérieur**.

## <a name="device-properties"></a>Propriétés des appareils

- **Système d’exploitation minimal exigé** : entrez la version minimale autorisée. Quand un appareil ne répond pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.
- **Système d’exploitation maximal autorisé** : entrez la version maximale autorisée. Quand un appareil utilise une version du système d’exploitation postérieure à la version entrée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. L’appareil ne peut pas accéder aux ressources de l’organisation jusqu’à ce que vous changiez la règle pour qu’elle autorise cette version du système d’exploitation.

Les PC Windows 8.1 retournent la version **3**. Si la règle de version du système d’exploitation est définie sur Windows 8.1 pour Windows, l’appareil est signalé comme non conforme, même si Windows 8.1 y est installé.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil.
- **Mots de passe simples** : choisissez **Bloquer** pour que les utilisateurs ne puissent pas créer de mots de passe simples, par exemple **1234** ou **1111**. Choisissez **Non configuré** pour permettre aux utilisateurs de créer des mots de passe tels que **1234** ou **1111**.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe.

  Pour les appareils Windows accessibles à l’aide d’un compte Microsoft, l’évaluation de la stratégie de conformité ne s’effectue pas correctement :
  - Si la longueur minimale du mot de passe est supérieure à huit caractères
  - Ou, si le nombre minimal de jeux de caractères est supérieur à deux

- **Type de mot de passe** : choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumériques**).
  
  - **Nombre de caractères non alphanumériques dans le mot de passe** : si **Type de mot de passe obligatoire** a la valeur **Alphanumérique**, ce paramètre spécifie le nombre minimal de jeux de caractères que le mot de passe doit contenir. Les quatre jeux de caractères sont :
    - Lettres minuscules
    - Lettres majuscules
    - Symboles
    - Nombres

    Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe. Pour les appareils accessibles à l’aide d’un compte Microsoft, l’évaluation de la stratégie de conformité ne s’effectue pas correctement :

    - Si la longueur minimale du mot de passe est supérieure à huit caractères
    - Ou si le nombre minimal de jeux de caractères est supérieur à deux

- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et l’obligation d’en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre d’anciens mots de passe qui ne peuvent pas être réutilisés.

### <a name="encryption"></a>Chiffrement

- **Exiger le chiffrement sur l’appareil mobile** : permet d’**imposer** le chiffrement de l’appareil pour la connexion aux ressources de stockage de données.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez les [paramètres de stratégie de conformité pour les appareils Windows 10 et ultérieur](compliance-policy-create-windows.md).