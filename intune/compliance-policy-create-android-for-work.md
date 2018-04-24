---
title: Créer une stratégie de conformité Android for Work
titleSuffix: Microsoft Intune
description: Créez une stratégie de conformité de l’appareil Intune pour les appareils Android for Work afin de pouvoir spécifier des exigences qu’un appareil doit respecter pour être conforme.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 00fa4508cdd4e74a20205ce46025b414cc0bb4cf
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Guide pratique pour créer une stratégie de conformité pour des appareils Android for Work dans Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Une stratégie de conformité de l’appareil Intune pour Android for Work spécifie les règles et les paramètres que les appareils Android for Work doivent satisfaire pour être considérés comme conformes. Vous pouvez utiliser ces stratégies avec l’accès conditionnel pour autoriser ou bloquer l’accès aux ressources d’entreprise, et vous pouvez générer des rapports sur les appareils et prendre des mesures en cas de non-conformité. Vous créez des stratégies de conformité de l’appareil pour chaque plateforme dans le portail Intune Azure. Pour en savoir plus sur les stratégies de conformité et sur les prérequis à prendre en compte avant de créer une stratégie, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

La table suivante décrit la façon dont les paramètres non conformes sont gérés quand une stratégie de conformité est utilisée avec une stratégie d’accès conditionnel.

--------------------------

|**paramètre de stratégie**| **Android for Work** |
| --- | --- |
| **Configuration d’un code confidentiel ou mot de passe** |  En quarantaine |
| **Chiffrement de l’appareil** |  En quarantaine |
| **Appareil jailbroken ou rooté** | En quarantaine (pas un paramètre) |
| **profil de messagerie** | Non applicable |
| **Version minimale du système d’exploitation** | En quarantaine |
| **Version maximale du système d’exploitation** | En quarantaine |
| **Attestation de l’intégrité Windows** |Non applicable |

**Corrigé** : le système d’exploitation de l’appareil applique la conformité. (Par exemple, l’utilisateur est obligé de définir un code PIN.)+

**En quarantaine** : le système d’exploitation de l’appareil n’applique pas la conformité. (Par exemple, les appareils Android n’obligent pas l’utilisateur à chiffrer l’appareil.) Quand l’appareil n’est pas conforme, les actions suivantes se produisent :

- Si une stratégie d’accès conditionnel s’applique à l’utilisateur, l’appareil est bloqué.
- Le portail d’entreprise informe l’utilisateur des problèmes de conformité.

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>Création d'une stratégie de conformité dans le portail Azure

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
1. Dans le volet **Intune**, choisissez **Conformité de l’appareil**. Sous **Gérer**, choisissez **Stratégies**, puis **Créer une stratégie**.
2. Tapez un nom et une description, puis sélectionnez la plateforme à laquelle vous souhaitez appliquer cette stratégie.
3. Choisissez **Configurer les paramètres** pour spécifier les paramètres **Sécurité du système**, **Intégrité de l’appareil** et **Propriétés de l’appareil**. Une fois que vous avez terminé, choisissez **Enregistrer**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>Affectation de groupes d’utilisateurs

Pour attribuer une stratégie de conformité à des utilisateurs, choisissez une stratégie que vous avez configurée. Vous trouverez les stratégies existantes dans le volet **Conformité de l’appareil – Stratégies**.

1. Choisissez la stratégie que vous souhaitez attribuer aux utilisateurs, puis **Affectations**. Cette opération ouvre le volet dans lequel vous pouvez sélectionner des **groupes de sécurité Azure Active Directory** que vous affectez à la stratégie.
2. Choisissez **Groupes sélectionnés** pour ouvrir la page qui affiche les groupes de sécurité Azure AD.  Si vous choisissez **Enregistrer**, la stratégie est déployée pour les utilisateurs.

Vous avez appliqué la stratégie à des utilisateurs.  La conformité des appareils utilisés par les utilisateurs ciblés par la stratégie de conformité sera évaluée.

<!--- ##  Compliance policy settings--->

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller des appareils mobiles** : définissez cette option sur **Oui** pour obliger les utilisateurs à entrer un mot de passe pour accéder à leur appareil.
- **Longueur minimale du mot de passe** : spécifie le nombre minimal de chiffres ou de caractères devant figurer dans le mot de passe.
- **Qualité du mot de passe :** ce paramètre détecte si les critères de mot de passe que vous spécifiez sont configurés sur l’appareil. Activez ce paramètre pour que les utilisateurs configurent certains critères de mot de passe pour les appareils Android. Choisissez parmi :
  - **Sécurité biométrique faible**
  - **Obligatoire**
  - **Au moins numérique**
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Alphanumérique avec symboles**
- **Minutes d’inactivité avant demande du mot de passe** : spécifie la durée d’inactivité au terme de laquelle l’utilisateur doit entrer à nouveau son mot de passe.
- **Expiration du mot de passe (jours)** : sélectionnez le nombre de jours avant que le mot de passe de l’utilisateur n’expire et qu’il ne doive en créer un autre.
- **Mémoriser l’historique des mots de passe** : utilisez ce paramètre conjointement avec le paramètre **Empêcher la réutilisation des mots de passe précédents** pour empêcher l’utilisateur de créer des mots de passe qui ont déjà été utilisés.
- **Empêcher la réutilisation des mots de passe précédents** : si l’option **Mémoriser l’historique des mots de passe** est sélectionnée, spécifiez le nombre de mots de passe précédemment utilisés qui ne peuvent pas être réutilisés.
- **Exiger un mot de passe quand l’appareil quitte un état inactif :** ce paramètre doit être utilisé avec le paramètre **Minutes d’inactivité avant demande du mot de passe**. Les utilisateurs finaux sont invités à entrer un mot de passe pour accéder à un appareil qui a été inactif pendant la durée spécifiée par le paramètre **Minutes d’inactivité avant demande du mot de passe**.


### <a name="encryption"></a>Chiffrement

- **Exiger le chiffrement sur l’appareil mobile** : vous n’êtes pas obligé de configurer ce paramètre parce que les appareils Android for Work appliquent le chiffrement.


## <a name="device-health-and-security-settings"></a>Paramètres d’intégrité et de sécurité de l’appareil

- **L’appareil ne doit pas être jailbreaké ou rooté** : si vous activez ce paramètre, les appareils jailbreakés ne sont pas détectés comme conformes.
- **Exiger que les appareils interdisent l’installation des applications provenant de sources inconnues** : vous n’êtes pas obligé de configurer ce paramètre, car les appareils Android for Work limitent systématiquement l’installation à partir de sources inconnues.
- **Exiger que le débogage USB soit désactivé** : vous n’êtes pas obligé de configurer ce paramètre parce que le débogage USB est déjà désactivé sur les appareils Android for Work.
- **Niveau minimal du correctif de sécurité Android** : Utilisez ce paramètre pour spécifier le niveau de correctif Android minimal. Les appareils qui ne sont pas au moins à ce niveau de correctif sont non conformes. La date doit être spécifiée au format suivant : AAAA-MM-JJ.
- **Exiger l’activation de la protection de l’appareil contre les menaces**: utilisez ce paramètre pour sélectionner l’évaluation des risques de la solution Lookout MTP comme une condition de conformité. Choisissez le niveau de menace maximal autorisé parmi les options suivantes :
  - **Aucun (sécurisé)**  : c’est le niveau de sécurité le plus haut. L’appareil ne peut présenter aucune menace. Si des menaces d’un autre niveau sont détectées sur l’appareil, celui-ci est évalué comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est évalué comme conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, il est déterminé comme non conforme.
  - **Élevé** : cette option est la moins sécurisée. Cette option permet en fait tous les niveaux de menaces. Elle peut être utile si vous utilisez cette solution uniquement pour la génération de rapports.

## <a name="device-property-settings"></a>Paramètres de propriétés d’appareils

- **Système d’exploitation minimal requis** : quand un appareil ne satisfait pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil, après quoi il pourra accéder aux ressources de l’entreprise.
- **Version maximale autorisée du système d’exploitation** : quand un appareil utilise une version du système d’exploitation ultérieure à celle spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur informatique. Jusqu’à ce qu’il y ait une modification de la règle pour autoriser la version du système d’exploitation, cet appareil ne peut pas être utilisé pour accéder aux ressources de l’entreprise.

<!--- ## Next steps

[How to monitor device compliance](device-compliance-monitor.md)--->
