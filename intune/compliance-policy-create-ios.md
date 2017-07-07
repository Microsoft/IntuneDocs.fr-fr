---
title: "Guide pratique pour créer une stratégie de conformité pour iOS"
titleSuffix: Intune on Azure
description: "Apprenez à créer une stratégie de conformité pour les appareils iOS."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9337586ad5daa909f38aba2b25fc159b44f55e65
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-create-a-device-compliance-policy-for-ios-devices-in-intune"></a>Guide pratique pour créer une stratégie de conformité pour des appareils iOS dans Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Des stratégies de conformité sont créées pour chaque plateforme.  Vous pouvez créer une stratégie de conformité dans le portail Azure. Pour en savoir plus sur ce qu'est la stratégie de conformité, consultez la rubrique [Qu'est-ce-que la compatibilité des appareils ?](device-compliance.md). Pour en savoir plus sur les conditions préalables à prendre en compte avant de créer une stratégie, consultez la rubrique [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

La table ci-dessous décrit également la façon dont les paramètres non conformes sont gérés quand une stratégie de conformité est utilisée avec une stratégie d’accès conditionnel.

-------------------------------


| **Paramètre de stratégie** | **iOS 8.0 et versions ultérieures** |
| --- | --- |
| **Configuration d’un code confidentiel ou mot de passe** | Corrigé |   
| **Chiffrement de l’appareil** | Corrigé (en définissant le code confidentiel) |
| **Appareil jailbroken ou rooté** | En quarantaine (pas un paramètre)
| **Profil de messagerie** | En quarantaine |
|**Version minimale du système d’exploitation** | En quarantaine |
| **Version maximale du système d’exploitation** | En quarantaine |  
| **Attestation de l’intégrité Windows** | Non applicable |  
----------------------------


**Corrigé** : le système d’exploitation de l’appareil applique la conformité. (Par exemple, l’utilisateur est obligé de définir un code confidentiel.)

**En quarantaine** : le système d’exploitation de l’appareil n’applique pas la conformité. (Par exemple, les appareils Android n’obligent pas l’utilisateur à chiffrer l’appareil.) Quand l’appareil n’est pas conforme, les actions suivantes se produisent :

- L’appareil est bloqué si une stratégie d’accès conditionnel s’applique à l’utilisateur.
- Le portail d’entreprise informe l’utilisateur des problèmes de conformité.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Création d'une stratégie de conformité dans le portail Azure

1. Dans le panneau **Intune**, choisissez **Définir la conformité des appareils**. Sous **Gérer**, choisissez **Toutes les stratégies de conformité d'appareil**, puis **Créer**.
2. Tapez un nom et une description, puis sélectionnez la plateforme à laquelle vous souhaitez appliquer cette stratégie.
3. Choisissez **Critères de conformité** pour spécifier les paramètres **Sécurité**, **Intégrité de l'appareil** et la **propriété de l'appareil** ici. Lorsque vous avez terminé, choisissez **Ok**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Affectation de groupes d’utilisateurs

Pour attribuer une stratégie de conformité à des utilisateurs, choisissez une stratégie que vous avez configurée. Vous trouverez les stratégies existantes dans le panneau **Stratégie de conformité**.

1. Choisissez la stratégie que vous souhaitez attribuer aux utilisateurs, puis **Affectations**. Cette opération ouvre le panneau dans lequel vous pouvez sélectionner des **groupes de sécurité Azure Active Directory** que vous attribuez à la stratégie.
2. Choisissez **Sélectionner des groupes** pour ouvrir le panneau qui affiche les groupes de sécurité Azure AD.  Si vous choisissez **Sélectionner**, la stratégie est déployée pour les utilisateurs.

Vous avez appliqué la stratégie à des utilisateurs.  La conformité des appareils utilisés par les utilisateurs ciblés par la stratégie de conformité sera évaluée.

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller des appareils mobiles** : définissez cette option sur **Oui** pour obliger l’utilisateur à entrer un mot de passe pour accéder à son appareil. Les appareils iOS utilisant un mot de passe sont chiffrés.
- **Autoriser les mots de passe simples** : définissez cette option sur **Oui** pour permettre à l’utilisateur de créer un mot de passe simple tel que **1234** ou **1111**.
- **Longueur minimale du mot de passe** : spécifie le nombre minimal de chiffres ou de caractères devant figurer dans le mot de passe.
- **Type de mot de passe requis** : spécifiez si l’utilisateur doit créer un mot de passe **Alphanumérique** ou un mot de passe **Numérique**.
- **Nombre minimum de jeux de caractères** : si le paramètre **Type de mot de passe requis** a la valeur **Alphanumérique**, ce paramètre spécifie le nombre minimal de jeux de caractères que le mot de passe doit avoir. Les quatre jeux de caractères sont :
  - Lettres minuscules
  - Lettres majuscules
  - Symboles
  - Nombres

Définir un nombre plus élevé oblige l’utilisateur à créer un mot de passe plus complexe.

Pour les appareils iOS, ce paramètre indique le nombre de caractères spéciaux (par exemple, **!** , **#**, **&amp;**) qui doivent être inclus dans le mot de passe.

- **Minutes d’inactivité avant demande du mot de passe** : spécifiez la durée d’inactivité au terme de laquelle l’utilisateur doit entrer à nouveau son mot de passe.
- **Expiration du mot de passe (jours)** : sélectionnez le nombre de jours avant que le mot de passe de l’utilisateur n’expire et qu’il ne doive en créer un autre.
- **Mémoriser l’historique des mots de passe** : utilisez ce paramètre conjointement avec le paramètre **Empêcher la réutilisation des mots de passe précédents** pour empêcher l’utilisateur de créer des mots de passe qui ont déjà été utilisés.
- **Empêcher la réutilisation des mots de passe précédents** : si vous avez sélectionné l’option **Mémoriser l’historique des mots de passe**, spécifiez le nombre de mots de passe précédemment utilisés qui ne peuvent pas être réutilisés.
- **Exiger un mot de passe quand l’appareil quitte un état inactif** : utilisez ce paramètre conjointement avec le paramètre **Minutes d’inactivité avant demande du mot de passe**. L’utilisateur est invité à entrer un mot de passe pour accéder à un appareil qui a été inactif pendant la durée spécifiée par le paramètre **Minutes d’inactivité avant demande du mot de passe**.

### <a name="email-profile"></a>Profil de messagerie

- **Le compte de messagerie doit être géré par Intune** : quand cette option est définie sur **Oui**, l’appareil doit utiliser le profil de messagerie qui y est déployé. L’appareil est considéré comme non conforme dans les situations suivantes :
  - Le profil de messagerie est déployé pour un groupe d’utilisateurs autre que celui ciblé par la stratégie de conformité.
  - L’utilisateur a déjà configuré sur l’appareil un compte e-mail qui correspond au profil de messagerie Intune déployé sur l’appareil. Intune ne peut pas remplacer le profil configuré par l'utilisateur et ne peut donc pas le gérer. Pour assurer la conformité, l’utilisateur doit supprimer les paramètres d’e-mail existants. Ensuite, Intune peut installer le profil de messagerie géré.
- **Sélectionnez le profil de messagerie géré par Intune** : si vous sélectionnez l’option **Le compte de messagerie doit être géré par Intune**, choisissez **Sélectionner** pour spécifier le profil de messagerie Intune. Le profil de messagerie doit être présent sur l'appareil.

Pour plus d’informations sur les profils de messagerie, consultez [Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune).

## <a name="device-health-settings"></a>Paramètres d’intégrité des appareils

- **L’appareil ne doit pas être jailbreaké ou rooté** : si vous activez ce paramètre, les appareils jailbreakés ne sont pas conformes.

## <a name="device-properties"></a>Propriétés des appareils

- **Système d’exploitation minimal requis** : quand un appareil ne satisfait pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau apparaît. L’utilisateur peut choisir de mettre à niveau son appareil. Ensuite, il peut accéder aux ressources de l’entreprise.
- **Version maximale autorisée du système d’exploitation** : quand un appareil utilise une version du système d’exploitation ultérieure à celle spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur informatique. Jusqu’à ce qu’il y ait une modification de la règle pour autoriser la version du système d’exploitation, cet appareil ne peut pas être utilisé pour accéder aux ressources de l’entreprise.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
