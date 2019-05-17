---
title: Stratégies de conformité des appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Vous pouvez bien démarrer avec l’utilisation de stratégies de conformité, la vue d’ensemble des niveaux d’état et de gravité, l’utilisation de l’état InGracePeriod, l’utilisation de l’accès conditionnel, la gestion des appareils sans stratégie attribuée, et les différences de conformité dans le portail Azure et dans le portail Azure Classic au sein de Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbed6185abe7656c3269805d1d5ed09eccbaf05e
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570427"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Définir des règles sur les appareils pour autoriser l’accès aux ressources de votre organisation à l’aide d’Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

De nombreuses solutions de gestion des appareils mobiles vous permettent de protéger les données de l’organisation en obligeant les utilisateurs et les appareils à répondre à certaines exigences. Dans Intune, cette fonctionnalité est appelée « stratégies de conformité ». Les stratégies de conformité définissent les règles et les paramètres que les utilisateurs et les appareils doivent satisfaire pour être conformes. Quand elles sont associées à l’accès conditionnel, les administrateurs peuvent bloquer les utilisateurs et les appareils qui ne respectent pas les règles.

Par exemple, un administrateur Intune peut exiger ceci :

- Les utilisateurs finaux utilisent un mot de passe pour accéder aux données de l’organisation sur des appareils mobiles.
- L’appareil n’est pas jailbreaké ni rooté.
- Une version de système d’exploitation minimale ou maximale est installée sur l’appareil.
- L’appareil se situe à un certain niveau de menace ou en dessous.

Vous pouvez également utiliser cette fonctionnalité pour surveiller l’état de la conformité sur les appareils de votre organisation.

> [!IMPORTANT]
> Intune suit la planification des enregistrements de l’appareil pour toutes les évaluations de conformité sur l’appareil. [Découvrez-en plus sur la planification des enregistrements d’appareils](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>Les stratégies de conformité des appareils fonctionnent avec Azure AD

Intune utilise l’[accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) (ouvre un autre site web de docs) d’Azure Active Directory pour renforcer la conformité. Quand un appareil est inscrit dans Intune, le processus d’inscription Azure AD démarre, et les informations de l’appareil sont mises à jour dans Azure AD. Une information clé est l’état de conformité de l’appareil. Cet état de conformité est utilisé par les stratégies d’accès conditionnel pour bloquer ou autoriser l’accès aux e-mails et à d’autres ressources de l’entreprise.

- La rubrique [En quoi consiste la gestion des appareils dans Azure Active Directory ?](https://docs.microsoft.com/azure/active-directory/device-management-introduction) est une ressource précieuse pour comprendre pourquoi et comment les appareils sont inscrits dans Azure AD.

- Les sections [Accès conditionnel](conditional-access.md) et [Utilisations courantes de l’accès conditionnel](conditional-access-intune-common-ways-use.md) décrivent cette fonctionnalité par rapport à Intune.

## <a name="ways-to-use-device-compliance-policies"></a>Utilisations des stratégies de conformité des appareils

#### <a name="with-conditional-access"></a>Avec accès conditionnel

Vous pouvez accorder aux appareils conformes aux règles de stratégie un accès aux e-mails et aux autres ressources de l’organisation. Si les appareils ne sont pas conformes aux règles de stratégie, cet accès leur est refusé. Il s’agit d’un accès conditionnel.

#### <a name="without-conditional-access"></a>Sans accès conditionnel

Vous pouvez également utiliser des stratégies de conformité d’appareils sans accès conditionnel. Quand vous utilisez des stratégies de conformité indépendamment, les appareils ciblés sont évalués et signalés avec leur état de conformité. Par exemple, vous pouvez obtenir un rapport sur le nombre d’appareils qui ne sont pas chiffrés, ou sur les appareils jailbreakés ou rootés. Quand vous utilisez des stratégies de conformité sans accès conditionnel, il n’y a aucune restriction d’accès aux ressources de l’organisation.

## <a name="ways-to-deploy-device-compliance-policies"></a>Déploiement des stratégies de conformité des appareils

Vous pouvez déployer une stratégie de conformité pour des utilisateurs dans des groupes d’utilisateurs ou sur des appareils dans des groupes d’appareils. Quand une stratégie de conformité est déployée sur un utilisateur, la conformité de tous ses appareils est vérifiée. Sur les appareils Windows 10 version 1803 et les appareils plus récents, il est recommandé de déployer sur des groupes d’appareils *si* l’utilisateur principal n’a pas inscrit l’appareil. L’utilisation de groupes d’appareils dans ce scénario permet la création de rapports de conformité.

Intune inclut également un ensemble de paramètres de stratégie de conformité intégrés. Les stratégies intégrées suivantes sont évaluées sur tous les appareils inscrits dans Intune :

- **Marquer les appareils sans stratégie de conformité comme étant** : Cette propriété a deux valeurs :

  - **Conforme** : fonctionnalité de sécurité désactivée
  - **Non conforme** (par défaut) : fonctionnalité de sécurité activée

  Si un appareil n’a pas de stratégie de conformité attribuée, il est considéré comme non conforme. Par défaut, les appareils sont marqués comme **non conformes**. Si vous utilisez l’accès conditionnel, nous vous recommandons de modifier le paramètre en **Non conforme**. Si un utilisateur final n’est pas conforme en raison d’un défaut d’attribution de stratégie, [l’application du portail d’entreprise Intune](company-portal-app.md) indique `No compliance policies have been assigned`.

- **Détection de jailbreak améliorée** : Quand ce paramètre est activé, les appareils iOS sont enregistrés dans Intune plus fréquemment. L’activation de cette propriété utilise les services de localisation de l’appareil et a un impact sur l’utilisation de la batterie. Les données de localisation de l’utilisateur ne sont pas stockées par Intune.

  L’activation de ce paramètre nécessite que les appareils :
  - activent les services de localisation au niveau du système d’exploitation ;
  - autorisent le portail d’entreprise à utiliser les services de localisation.
  - Évaluent et signalent leur état jailbreak à Intune au moins une fois toutes les 72 heures. Sinon, l’appareil est marqué comme non conforme. L’évaluation est déclenchée soit par l’ouverture de l’application Portail d’entreprise Intune, soit lorsque vous éloignez physiquement l’appareil d’au moins 500 mètres. Si l’appareil ne se déplace pas de 500 mètres dans les 72 heures, l’utilisateur doit ouvrir l’application Portail d’entreprise pour une évaluation de jailbreak améliorée.

- **Période de validité de l’état de conformité (jours)**  : Entrez la période pendant laquelle les appareils signalent l’état de toutes les stratégies de conformité reçues. Les appareils qui ne retournent pas l’état au cours de cette période sont considérés comme non conformes. La valeur par défaut est de 30 jours.

Vous pouvez utiliser ces stratégies intégrées pour surveiller ces paramètres. De plus, Intune [actualise ou vérifie les mises à jour](create-compliance-policy.md#refresh-cycle-times) à des intervalles différents, selon la plateforme de l’appareil. La section [Problèmes courants avec les profils d’appareil dans Microsoft Intune et résolutions](device-profile-troubleshoot.md) constitue une bonne ressource.

Les rapports de conformité sont un excellent moyen de vérifier l’état des appareils. Voir [Surveiller les stratégies de conformité](compliance-policy-monitor.md) pour obtenir des conseils.

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>Non-conformité et accès conditionnel sur les différentes plateformes

La table suivante décrit la façon dont les paramètres non conformes sont gérés quand une stratégie de conformité est utilisée avec une stratégie d’accès conditionnel.

---------------------------

|**Paramètre de stratégie**| **Plateforme** |
| --- | ----|
| **Configuration d’un code confidentiel ou mot de passe** | - **Android 4.0 et versions ultérieures** : En quarantaine</br>- **Samsung Knox Standard 4.0 et versions ultérieures** : En quarantaine</br>- **Android Entreprise** : En quarantaine</br></br>- **iOS 8.0 et versions ultérieures** : Corrigé</br>- **macOS 10.11 et versions ultérieures** : Corrigé</br></br>- **Windows 8.1 et versions ultérieures** : Corrigé</br>- **Windows Phone 8.1 et versions ultérieures** : Corrigé|
| **Chiffrement de l’appareil** | - **Android 4.0 et versions ultérieures** : En quarantaine</br>- **Samsung Knox Standard 4.0 et versions ultérieures** : En quarantaine</br>- **Android Entreprise** : En quarantaine</br></br>- **iOS 8.0 et versions ultérieures** : Corrigé (en définissant le code confidentiel)</br>- **macOS 10.11 et versions ultérieures** : Corrigé (en définissant le code confidentiel)</br></br>- **Windows 8.1 et versions ultérieures** : Non applicable</br>- **Windows Phone 8.1 et versions ultérieures** : Corrigé |
| **Appareil jailbroken ou rooté** | - **Android 4.0 et versions ultérieures** : En quarantaine (pas un paramètre)</br>- **Samsung Knox Standard 4.0 et versions ultérieures** : En quarantaine (pas un paramètre)</br>- **Android Entreprise** : En quarantaine (pas un paramètre)</br></br>- **iOS 8.0 et versions ultérieures** : En quarantaine (pas un paramètre)</br>- **macOS 10.11 et versions ultérieures** : Non applicable</br></br>- **Windows 8.1 et versions ultérieures** : Non applicable</br>- **Windows Phone 8.1 et versions ultérieures** : Non applicable |
| **Profil de messagerie** | - **Android 4.0 et versions ultérieures** : Non applicable</br>- **Samsung Knox Standard 4.0 et versions ultérieures** : Non applicable</br>- **Android Entreprise** : Non applicable</br></br>- **iOS 8.0 et versions ultérieures** : En quarantaine</br>- **macOS 10.11 et versions ultérieures** : En quarantaine</br></br>- **Windows 8.1 et versions ultérieures** : Non applicable</br>- **Windows Phone 8.1 et versions ultérieures** : Non applicable |
| **Version minimale du système d’exploitation** | - **Android 4.0 et versions ultérieures** : En quarantaine</br>- **Samsung Knox Standard 4.0 et versions ultérieures** : En quarantaine</br>- **Android Entreprise** : En quarantaine</br></br>- **iOS 8.0 et versions ultérieures** : En quarantaine</br>- **macOS 10.11 et versions ultérieures** : En quarantaine</br></br>- **Windows 8.1 et versions ultérieures** : En quarantaine</br>- **Windows Phone 8.1 et versions ultérieures** : En quarantaine |
| **Version maximale du système d’exploitation** | - **Android 4.0 et versions ultérieures** : En quarantaine</br>- **Samsung Knox Standard 4.0 et versions ultérieures** : En quarantaine</br>- **Android Entreprise** : En quarantaine</br></br>- **iOS 8.0 et versions ultérieures** : En quarantaine</br>- **macOS 10.11 et versions ultérieures** : En quarantaine</br></br>- **Windows 8.1 et versions ultérieures** : En quarantaine</br>- **Windows Phone 8.1 et versions ultérieures** : En quarantaine |
| **Attestation de l’intégrité Windows** | - **Android 4.0 et versions ultérieures** : Non applicable</br>- **Samsung Knox Standard 4.0 et versions ultérieures** : Non applicable</br>- **Android Entreprise** : Non applicable</br></br>- **iOS 8.0 et versions ultérieures** : Non applicable</br>- **macOS 10.11 et versions ultérieures** : Non applicable</br></br>- **Windows 10 and Windows 10 Mobile** : En quarantaine</br>- **Windows 8.1 et versions ultérieures** : En quarantaine</br>- **Windows Phone 8.1 et versions ultérieures** : Non applicable |

---------------------------

**Corrigé** : Le système d’exploitation de l’appareil applique la conformité. Par exemple, l’utilisateur est obligé de définir un code PIN.

**En quarantaine** : Le système d’exploitation de l’appareil n’applique pas la conformité. Par exemple, les appareils Android et Android Entreprise ne forcent pas l’utilisateur à chiffrer l’appareil. Quand l’appareil n’est pas conforme, les actions suivantes se produisent :

  - Si une stratégie d’accès conditionnel s’applique à l’utilisateur, l’appareil est bloqué.
  - L’application du portail d’entreprise Intune informe l’utilisateur de tout problème de conformité.

## <a name="azure-classic-portal-vs-azure-portal"></a>Portail Azure Classic et Portail Azure

Principale différence au moment de l’utilisation de stratégies de conformité dans le portail Azure :

- Dans le portail Azure, les stratégies de conformité sont créées séparément pour chaque plateforme prise en charge
- Dans le portail Azure Classic, une stratégie de conformité des appareils est commune à toutes les plateformes prises en charge

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are initiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

Les stratégies de conformité des appareils créées dans le [portail classique](https://manage.microsoft.com) n’apparaissent pas dans le [portail Azure](https://portal.azure.com). Toutefois, elles continuent de cibler des utilisateurs et peuvent être gérées à l’aide du portail classique.

Pour utiliser les fonctionnalités liées à la conformité des appareils dans le portail Azure, vous devez créer des stratégies de conformité d’appareil dans le portail Azure. Si, dans le portail Azure, vous affectez une stratégie de conformité des appareils à un utilisateur auquel est déjà associée une stratégie de ce type dans le portail classique, les stratégies du portail Azure sont prioritaires par rapport aux stratégies qui sont créées dans le portail classique.

## <a name="next-steps"></a>Étapes suivantes

- [Créer une stratégie](create-compliance-policy.md) et afficher les conditions préalables.
- Consultez les paramètres de conformité pour les différentes plateformes d’appareils :

  - [Android](compliance-policy-create-android.md)
  - [Android Entreprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [MacOS](compliance-policy-create-mac-os.md)
  - [Windows 10 et versions ultérieures](compliance-policy-create-windows.md)
  - [Windows 8.1 et Windows Phone 8.1](compliance-policy-create-windows-8-1.md)

- La section [Informations de référence sur les entités de stratégie](reports-ref-policy.md) contient des informations sur les entités de stratégie Intune Data Warehouse.