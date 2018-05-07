---
title: Créer une stratégie de conformité des appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Créez ou configurez une stratégie de conformité des appareils Microsoft Intune pour les appareils Android. Choisissez d’autoriser les appareils jailbreakés, définissez le niveau de menace acceptable, vérifiez la présence de Google Play, entrez la version minimale et maximale du système d’exploitation, choisissez vos exigences de mot de passe et autorisez le chargement indépendant des applications.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: afc8edb38b667d744bb586d1ed5c82df8ab10f49
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Ajouter une stratégie de conformité des appareils pour les appareils Android dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Une stratégie de conformité de l’appareil Intune pour Android spécifie les règles et les paramètres que les appareils Android doivent satisfaire pour être considérés comme conformes. Vous pouvez utiliser ces stratégies avec un accès conditionnel pour autoriser ou bloquer l’accès aux ressources de l’entreprise. Vous pouvez également obtenir des rapports sur les appareils et prendre des mesures en cas de non-conformité. Vous créez des stratégies de conformité de l’appareil pour chaque plateforme dans le portail Intune Azure. Pour en savoir plus sur les stratégies de conformité et sur les prérequis, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

La table suivante décrit la façon dont les paramètres non conformes sont gérés quand une stratégie de conformité est utilisée avec une stratégie d’accès conditionnel.

--------------------

|**Paramètre de stratégie**| **Android 4.0 et versions ultérieures, Samsung Knox Standard 4.0 et versions ultérieures** |
| --- | ----|
| **Configuration d’un code confidentiel ou mot de passe** |  En quarantaine |
| **Chiffrement de l’appareil** | En quarantaine |
| **Appareil jailbroken ou rooté** | En quarantaine (pas un paramètre) |
| **profil de messagerie** | Non applicable |
| **Version minimale du système d’exploitation** | En quarantaine |
| **Version maximale du système d’exploitation** |   En quarantaine |
| **Attestation de l’intégrité Windows** | Non applicable |

--------------------------

**Corrigé** : le système d’exploitation de l’appareil applique la conformité. (Par exemple, l’utilisateur est obligé de définir un code confidentiel.)

**En quarantaine** : le système d’exploitation de l’appareil n’applique pas la conformité. (Par exemple, les appareils Android n’obligent pas l’utilisateur à chiffrer l’appareil.) Quand l’appareil n’est pas conforme, les actions suivantes se produisent :

- L’appareil est bloqué si une stratégie d’accès conditionnel s’applique à l’utilisateur.
- Le portail d’entreprise informe l’utilisateur des problèmes de conformité.

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Pour l’option **Plateforme**, sélectionnez **Android**. Choisissez **Paramètres Configurer**, puis entrez les paramètres nécessaires pour les options **Intégrité de l’appareil**, **Propriétés de l’appareil** et **Sécurité du système**. Une fois que vous avez fini, sélectionnez **OK**, puis **Créer**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant based on the configured settings in this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **OK** when you are finished creating all the actions.--->

<!---##  Compliance policy settings--->

## <a name="device-health"></a>Device health

- **Appareils rootés** : si vous activez ce paramètre, les appareils jailbreakés sont considérés comme non conformes.
- **Exiger que l’appareil se situe au niveau de menace d’appareil ou en dessous** : utilisez ce paramètre pour considérer l’évaluation des risques de la solution Lookout MTP comme une condition de conformité. Choisissez le niveau de menace maximal autorisé :
  - **Sécurisé** : cette option est la plus sécurisée, car l’appareil ne doit présenter aucune menace. Si des menaces d’un autre niveau sont détectées sur l’appareil, celui-ci est évalué comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sur celui-ci sont de niveau faible ou moyen. La présence de menaces de niveau élevé rend l’appareil non conforme.
  - **Élevé** : cette option est la moins sécurisée, elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.
- **Google Play Services est configuré** : l’application Google Play Services doit être impérativement installée et activée. Google Play Services autorise les mises à jour de sécurité et constitue une dépendance de niveau de base pour de nombreuses fonctionnalités de sécurité sur les appareils Google certifiés.
- **Fournisseur de sécurité à jour** : un fournisseur de sécurité à jour doit protéger l’appareil contre les vulnérabilités connues.
- **Analyse des menaces sur les applications** : la fonctionnalité Android **Vérifier les applications** doit être impérativement activée.

  > [!NOTE]
  > Sur la plateforme Android héritée, cette fonctionnalité constitue un paramètre de conformité. Intune ne peut que vérifier si ce paramètre est activé au niveau de l’appareil. Sur les appareils dotés de profils professionnels (Android for Work), ce paramètre correspond à un paramètre de stratégie de configuration. Ceci permet aux administrateurs d’activer le paramètre pour un appareil.

  Si votre entreprise utilise des profils professionnels Android, vous pouvez activer **Analyse des menaces sur les applications** pour vos appareils inscrits. Établissez un profil d’appareil et demandez le paramètre de sécurité système. Pour plus d’informations sur les profils d’appareils, consultez [Paramètres de restriction des appareils Android for Work dans Intune](device-restrictions-android-for-work.md).

- **Attestation d’appareil SafetyNet** : entrez le niveau d’[attestation SafetyNet](https://developer.android.com/training/safetynet/attestation.html) à respecter. Les options disponibles sont les suivantes :
  - **Non configuré**
  - **Vérifier l’intégrité de base**
  - **Vérifier l’intégrité de base et les appareils certifiés**

## <a name="device-property-settings"></a>Paramètres de propriétés d’appareils

- **Version minimale du système d’exploitation** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.
- **Version maximale du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant que la règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe de l’utilisateur.
- **Type de mot de passe obligatoire** : choisissez si un mot de passe doit comportement uniquement des caractères numériques, ou s’il doit comporter un mélange de chiffres et d’autres caractères. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Au moins numérique**
  - **Chiffres complexes**
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**
- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et l’obligation d’en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre de mots de passe récents qui ne peuvent pas être réutilisés. Utilisez ce paramètre pour empêcher l’utilisateur de créer des mots de passe déjà utilisés.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** (Android 4.0 et versions ultérieures ou KNOX 4.0 et versions ultérieures) : choisissez **Exiger** pour chiffrer le stockage des données sur vos appareils. Les appareils sont chiffrés quand vous choisissez le paramètre **Exiger un mot de passe pour déverrouiller les appareils mobiles**.

### <a name="device-security"></a>Sécurité du périphérique

- **Bloquer les applications provenant de sources inconnues** : choisissez de bloquer les appareils où « Sécurité > Sources inconnues » est activé (Android 4.0 - Android 7.x. Non pris en charge par Android 8.0 et les versions ultérieures). Pour effectuer un chargement indépendant des applications, vous devez autoriser les sources inconnues. Si vous n’effectuez pas de chargement indépendant des applications Android, activez cette stratégie de conformité.

  > [!IMPORTANT]
  > Pour permettre le chargement indépendant des applications, le paramètre **Bloquer les applications provenant de sources inconnues** doit être activé. Appliquez cette stratégie de conformité uniquement si vous n’effectuez aucun chargement indépendant d’applications Android sur les appareils.

- **Intégrité du runtime de l’application Portail d’entreprise** : vérifie si l’environnement de runtime par défaut de l’application Portail d’entreprise est installé, s’il est correctement signé, s’il n’est pas en mode de débogage et s’il est installé à partir d’une source connue.
- **Bloquer le débogage USB sur l’appareil** (Android 4.2 ou version ultérieure) : choisissez d’empêcher les appareils d’utiliser la fonctionnalité de débogage USB.
- **Niveau minimal du correctif de sécurité** (Android 6.0 ou version ultérieure) : sélectionnez le niveau le plus ancien possible pour le correctif de sécurité d’un appareil. Les appareils qui ne sont pas au moins à ce niveau de correctif sont non conformes. Vous devez entrer la date au format `YYYY-MM-DD`.

## <a name="assign-user-groups"></a>Affectation de groupes d’utilisateurs

1. Choisissez une stratégie que vous avez configurée. Les stratégies existantes se trouvent dans **Conformité de l’appareil** > **Stratégies**.
2. Choisissez la stratégie, puis **Affectations**. Vous pouvez inclure ou exclure des groupes de sécurité Azure AD (Azure Active Directory).
3. Choisissez **Groupes sélectionnés** pour voir vos groupes de sécurité Azure AD. Sélectionnez les groupes d’utilisateurs auxquels vous souhaitez appliquer cette stratégie, puis choisissez **Enregistrer** pour déployer la stratégie auprès des utilisateurs.

Vous avez appliqué la stratégie à des utilisateurs. La conformité des appareils utilisés par les utilisateurs ciblés par la stratégie est évaluée.

## <a name="next-steps"></a>Étapes suivantes
[Automatiser l’envoi d’un e-mail et ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md)  
[Surveiller les stratégies de conformité d’appareils Intune](compliance-policy-monitor.md)