---
title: Créer une stratégie de conformité des appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Créez ou configurez une stratégie de conformité des appareils Microsoft Intune pour les appareils iOS afin de pouvoir entrer un compte e-mail, vérifier les appareils jailbreakés, vérifier la version minimale et maximale du système d’exploitation, et définir les restrictions relatives au mot de passe, notamment la longueur du mot de passe et l’inactivité de l’appareil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 41ae1ffc17eee93b45f00e4eef5590f6a5d0b7b4
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112508"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Ajouter une stratégie de conformité des appareils pour les appareils iOS dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Une stratégie de conformité des appareils iOS Intune détermine les règles et les paramètres que les appareils iOS doivent satisfaire pour être conformes. Quand vous utilisez des stratégies de conformité de l’appareil avec l’accès conditionnel, vous pouvez autoriser ou bloquer l’accès aux ressources d’entreprise. Vous pouvez également obtenir des rapports sur les appareils et prendre des mesures en cas de non-conformité. Des stratégies de conformité de l’appareil pour chaque plateforme peuvent être créées dans le portail Intune Azure. Pour en savoir plus sur les stratégies de conformité et sur les prérequis, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

La table suivante décrit la façon dont les paramètres non conformes sont gérés quand une stratégie de conformité est utilisée avec une stratégie d’accès conditionnel.

---------------------------

| **Paramètre de stratégie** | **iOS 8.0 et versions ultérieures** |
| --- | --- |
| **Configuration d’un code confidentiel ou mot de passe** | Corrigé |
| **Chiffrement de l’appareil** | Corrigé (en définissant le code confidentiel) |
| **Appareil jailbroken ou rooté** | En quarantaine (pas un paramètre)
| **Profil de messagerie** | En quarantaine |
|**Version minimale du système d’exploitation** | En quarantaine |
| **Version maximale du système d’exploitation** | En quarantaine |
| **Attestation de l’intégrité Windows** | Non applicable |

---------------------------

**Corrigé** : le système d’exploitation de l’appareil applique la conformité. (Par exemple, l’utilisateur est obligé de définir un code confidentiel.)

**En quarantaine** : le système d’exploitation de l’appareil n’applique pas la conformité. (Par exemple, les appareils Android n’obligent pas l’utilisateur à chiffrer l’appareil.) Quand l’appareil n’est pas conforme, les actions suivantes se produisent :

- L’appareil est bloqué si une stratégie d’accès conditionnel s’applique à l’utilisateur.
- Le portail d’entreprise informe l’utilisateur des problèmes de conformité.

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Pour l’option **Plateforme**, sélectionnez **iOS**. 
5. Choisissez **Paramètres Configurer**, puis entrez les paramètres nécessaires pour les options **E-mail**, **Intégrité de l’appareil**, **Propriétés de l’appareil** et **Sécurité du système** décrites dans cette rubrique. Une fois que vous avez fini, sélectionnez **OK**, puis **Créer**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>E-mail

- **Exiger que les appareils mobiles aient un profil de messagerie géré** : si vous choisissez Exiger, les appareils qui n’ont pas de profil de messagerie géré par Intune sont considérés comme non conformes. Un appareil ne peut pas avoir de profil d’e-mail géré quand il n’est pas correctement ciblé, ou si l’utilisateur configure manuellement le compte e-mail sur cet appareil.

  L’appareil est considéré comme non conforme dans les situations suivantes :
  - Le profil de messagerie est déployé pour un groupe d’utilisateurs autre que celui ciblé par la stratégie de conformité.
  - L’utilisateur a déjà configuré sur l’appareil un compte e-mail qui correspond au profil de messagerie Intune déployé sur l’appareil. Intune ne peut pas remplacer le profil configuré par l'utilisateur et ne peut donc pas le gérer. Pour assurer la conformité, l’utilisateur doit supprimer les paramètres d’e-mail existants. Ensuite, Intune peut installer le profil de messagerie géré.

- **Sélectionner le profil de messagerie géré par Intune** : si le paramètre **Le compte de messagerie doit être géré par Intune** est sélectionné, choisissez **Sélectionner** pour spécifier le profil de messagerie Intune. Le profil de messagerie doit être présent sur l'appareil.

Pour plus d’informations sur les profils de messagerie, consultez [Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune](email-settings-configure.md).

## <a name="device-health"></a>Device health

- **Appareils jailbreakés** : si vous activez ce paramètre, les appareils jailbreakés ne sont pas conformes.
- **Exiger que l’appareil soit au niveau ou sous le niveau de défense contre les menaces mobiles** (iOS 8.0 et versions ultérieures) : Choisissez le niveau de menace maximal au-delà duquel les appareils sont marqués comme non conformes. Les appareils qui dépassent ce niveau de menace sont marqués comme non conformes :
  - **Sécurisé** : c’est l’option la plus sécurisée, car l’appareil ne peut présenter aucune menace. Si des menaces d’un autre niveau sont détectées sur l’appareil, celui-ci est évalué comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sont de niveau faible ou moyen. La présence de menaces de niveau élevé rend l’appareil non conforme.
  - **Élevé** : c’est l’option la moins sécurisée, car elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.

## <a name="device-properties"></a>Propriétés des appareils

- **Système d’exploitation minimal requis** : quand un appareil ne répond pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur peut choisir de mettre à niveau son appareil. Ensuite, il peut accéder aux ressources de l’entreprise.
- **Version maximale autorisée du système d’exploitation** : quand un appareil utilise une version du système d’exploitation ultérieure à celle qui est spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant que la règle pour autoriser la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.
- **Version de build du système d’exploitation minimale** : quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, et non la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé minimal sur l’appareil. Cette vérification de conformité prend en charge les appareils exécutant iOS 8.0 et versions ultérieures. 
- **Version de build du système d’exploitation maximale** : quand Apple publie des mises à jour de sécurité, le numéro de build est généralement mis à jour, et non la version du système d’exploitation. Cette fonctionnalité permet d’entrer un numéro de build autorisé maximal sur l’appareil. Cette vérification de conformité prend en charge les appareils exécutant iOS 8.0 et versions ultérieures.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

> [!NOTE]
> Une fois qu’une stratégie de conformité ou de configuration est appliquée à un appareil iOS, les utilisateurs sont invités à définir un code secret toutes les 15 minutes. Tant que les utilisateurs n’ont pas défini de code secret, ils sont invités à le faire.

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : **force** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil. Les appareils iOS utilisant un mot de passe sont chiffrés.
- **Mots de passe simples** : choisissez **Bloquer** pour que les utilisateurs ne puissent pas créer de mots de passe simples, comme **1234** ou **1111**. Choisissez **Non configuré** pour permettre aux utilisateurs de créer des mots de passe tels que **1234** ou **1111**.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères que doit comporter le mot de passe.
- **Type de mot de passe requis** : choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumérique**).
- **Nombre de caractères non alphanumériques dans le mot de passe** : entrez le nombre minimal de caractères spéciaux (&, #, %, !, etc.) qui doivent être inclus dans le mot de passe.

    Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe.

- **Durée d’inactivité maximale en minutes avant demande du mot de passe** : entrez la durée d’inactivité au terme de laquelle l’utilisateur doit entrer à nouveau son mot de passe.
- **Expiration du mot de passe (en jours)** : sélectionnez le nombre de jours avant que le mot de passe n’expire et que l’utilisateur ne doive en créer un autre.
- **Nombre de mots de passe précédents pour empêcher la réutilisation** : entrez le nombre de mots de passe précédemment utilisés qui ne peuvent pas être utilisés.

### <a name="restricted-applications"></a>Applications restreintes 
Vous pouvez restreindre les applications en ajoutant leurs ID de bundle à la stratégie. Ainsi, si l’application est installée sur l’appareil, celui-ci est marqué comme non conforme. 
- **Nom de l’application** : entrez un nom convivial pour faciliter l’identification de l’ID de l’ensemble d’applications. 
- **ID de l'ensemble d'applications** : entrez l’identificateur unique de l’ensemble d’applications affecté par le fournisseur de l’application. Pour trouver l’ID de bundle, consultez [Guide pratique pour trouver l’ID de bundle pour une application iOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).  

## <a name="assign-user-groups"></a>Affectation de groupes d’utilisateurs

1. Choisissez une stratégie que vous avez configurée. Les stratégies existantes se trouvent dans **Conformité de l’appareil** > **Stratégies**.
2. Choisissez la stratégie, puis **Affectations**. Vous pouvez inclure ou exclure des groupes de sécurité Azure AD (Azure Active Directory).
3. Choisissez **Groupes sélectionnés** pour voir vos groupes de sécurité Azure AD. Sélectionnez les groupes d’utilisateurs auxquels vous souhaitez appliquer cette stratégie, puis choisissez **Enregistrer** pour déployer la stratégie auprès des utilisateurs.

Vous avez appliqué la stratégie à des utilisateurs. La conformité des appareils utilisés par les utilisateurs ciblés par la stratégie est évaluée.

## <a name="next-steps"></a>Étapes suivantes
[Automatiser l’envoi d’un e-mail et ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md)  
[Surveiller les stratégies de conformité d’appareils Intune](compliance-policy-monitor.md)
