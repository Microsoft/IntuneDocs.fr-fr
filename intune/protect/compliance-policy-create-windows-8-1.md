---
title: Paramètres de conformité de Windows 8.1 dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser quand vous configurez la conformité de vos appareils Windows 8.1 et Windows Phone 8.1 dans Microsoft Intune. Vérifiez la conformité sur le système d’exploitation minimal et maximal, définissez des restrictions et une longueur de mot de passe, activez le chiffrement sur le stockage de données, etc.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813218"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres de Windows 8.1 pour marquer les appareils comme étant conformes ou non conformes avec Intune

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils Windows 8.1 dans Intune. Dans le cadre de votre solution MDM, utilisez ces paramètres pour bloquer les mots de passe simples, définir une version minimale ou maximale du système d’exploitation, etc.

Cette fonctionnalité s’applique à :

- Windows Phone 8.1
- Windows 8.1 et versions ultérieures

En tant qu’administrateur Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour **Plateforme**, sélectionnez **Windows Phone 8.1** ou **Windows 8.1 et ultérieur**.

## <a name="device-properties"></a>Propriétés de l’appareil

### <a name="operating-system-version"></a>Version du système d'exploitation

**Windows phone 8.1 et ultérieur**
- **Version minimale du système d’exploitation pour les appareils mobiles**:  
  Entrez la version minimale autorisée. Quand un appareil ne répond pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.

- **Version maximale du système d’exploitation pour les appareils mobiles**:  
  Entrez la version maximale autorisée. Quand un appareil utilise une version du système d’exploitation postérieure à la version entrée dans la règle, l’accès aux ressources de l’organisation est bloqué. L’utilisateur de l’appareil est invité à contacter son administrateur informatique. L’appareil ne peut pas accéder aux ressources de l’organisation tant qu’une règle n’est pas modifiée pour autoriser cette version du système d’exploitation.

**Windows 8.1 et versions ultérieures**
- **Version minimale du système d’exploitation** :  
  Entrez la version minimale autorisée. Quand un appareil ne répond pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.

- **Version maximale du système d’exploitation** :  
  Entrez la version maximale autorisée. Quand un appareil utilise une version du système d’exploitation postérieure à la version entrée dans la règle, l’accès aux ressources de l’organisation est bloqué. L’utilisateur de l’appareil est invité à contacter son administrateur informatique. L’appareil ne peut pas accéder aux ressources de l’organisation tant qu’une règle n’est pas modifiée pour autoriser cette version du système d’exploitation.

Les PC Windows 8.1 retournent la version **3**. Si la règle de version du système d’exploitation est définie sur Windows 8.1 pour Windows, l’appareil est signalé comme non conforme, même si Windows 8.1 y est installé.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** :  
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : les utilisateurs doivent entrer un mot de passe pour pouvoir accéder à leur appareil.

- **Mots de passe simples** :  
  - **Non configuré** (*par défaut*) : les utilisateurs peuvent créer des mots de passe simples comme **1234** ou **1111**.
  - **Bloquer** : les utilisateurs ne peuvent pas créer de mots de passe simples, comme **1234** ou **1111**.  

- **Longueur minimale du mot de passe** :  
  entrez le nombre minimal de chiffres ou de caractères que doit comporter le mot de passe.

  Pour les appareils qui exécutent Windows et qui sont accessibles avec un compte Microsoft, la stratégie de conformité ne peut pas être évaluée correctement si l’une des conditions suivantes est remplie :  
  - La longueur minimale du mot de passe est supérieure à huit caractères
  - Le nombre minimal de jeux de caractères est supérieur à deux

- **Type de mot de passe** :  
  choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumérique**).

  Lorsque la valeur est *alphanumérique*, le paramètre suivant est disponible.  

  - **Nombre de caractères non alphanumériques dans le mot de passe** :  
    Lorsque le *type de mot de passe* est défini sur **alphanumérique**, spécifiez le nombre minimal de jeux de caractères que le mot de passe doit contenir. Les options incluent **0** à **4** sets, avec **1**comme valeur par défaut.
    
    Les quatre jeux de caractères sont :
    - Lettres minuscules
    - Lettres majuscules
    - Symboles
    - Nombres

    Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe. Pour les appareils accessibles avec un compte Microsoft, la stratégie de conformité ne peut pas être évaluée correctement si l’une des conditions suivantes est remplie :

    - La longueur minimale du mot de passe est supérieure à huit caractères
    - Le nombre minimal de jeux de caractères est supérieur à deux

- **Durée d’inactivité maximale en minutes avant demande du mot de passe** :  
  entrez la durée d’inactivité au terme de laquelle l’utilisateur doit entrer à nouveau son mot de passe.

- **Expiration du mot de passe (en jours)** :  
  Sélectionnez le nombre de jours avant que le mot de passe n’expire et que les utilisateurs ne doivent en créer un autre.

- **Nombre de mots de passe précédents pour empêcher la réutilisation** :  
  Entrez le nombre de mots de passe précédemment utilisés qui ne peuvent pas être utilisés.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** :  
  - **Non configuré** (*par défaut*)
  - **Exiger** : utilisez *Exiger* pour chiffrer le stockage de données sur vos appareils.


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez les [paramètres de stratégie de conformité pour les appareils Windows 10 et ultérieur](compliance-policy-create-windows.md).