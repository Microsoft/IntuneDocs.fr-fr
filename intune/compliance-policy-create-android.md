---
title: Créer une stratégie de conformité des appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Créez ou configurez une stratégie de conformité des appareils Microsoft Intune pour les appareils Android. Choisissez d’autoriser les appareils jailbreakés, définissez le niveau de menace acceptable, vérifiez la présence de Google Play, entrez la version minimale et maximale du système d’exploitation, choisissez vos exigences de mot de passe et autorisez le chargement indépendant des applications.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0dc4fc0a0f16717bd0c21db3a9e7e57daf7867bc
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069039"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Ajouter une stratégie de conformité des appareils pour les appareils Android dans Intune

Une stratégie de conformité de l’appareil Intune pour Android spécifie les règles et les paramètres que les appareils Android doivent satisfaire pour être considérés comme conformes. Vous pouvez utiliser ces stratégies avec un [accès conditionnel](conditional-access.md) pour autoriser ou bloquer l’accès aux ressources de l’organisation. Vous pouvez également obtenir des rapports sur les appareils et prendre des mesures en cas de non-conformité. 

Pour en savoir plus sur les stratégies de conformité et sur les prérequis, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

Cette rubrique liste les paramètres que vous pouvez utiliser dans une stratégie de conformité pour les appareils Android.

## <a name="non-compliance-and-conditional-access"></a>Non-conformité et accès conditionnel

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

**Corrigé** : le système d’exploitation de l’appareil applique la conformité. Par exemple, l’utilisateur est obligé de définir un code PIN.

**En quarantaine** : le système d’exploitation de l’appareil n’applique pas la conformité. Par exemple, les appareils Android ne forcent pas l’utilisateur à chiffrer l’appareil. Quand l’appareil n’est pas conforme, les actions suivantes se produisent :

  - L’appareil est bloqué si une stratégie d’accès conditionnel s’applique à l’utilisateur.
  - Le portail d’entreprise informe l’utilisateur des problèmes de conformité.

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Pour l’option **Plateforme**, sélectionnez **Android**. 
5. Choisissez**Paramètres Configurer**. Entrez les paramètres nécessaires pour les options **Intégrité de l’appareil**, **Propriétés de l’appareil** et **Sécurité du système**, comme décrit dans cet article.

## <a name="device-health"></a>Device health

- **Appareils rootés** : choisissez **Bloquer** pour marquer les appareils rootés (jailbreakés) comme étant non conformes. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Exiger que l’appareil se situe au niveau de menace d’appareil ou en dessous** : utilisez ce paramètre pour considérer l’évaluation des risques de la solution Lookout MTP comme une condition de conformité. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Pour utiliser ce paramètre, choisissez le niveau de menace autorisé :
  - **Sécurisé** : cette option est la plus sécurisée, car l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sur celui-ci sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.
- **Google Play Services est configuré** : l’application Google Play Services **doit être impérativement** installée et activée. Google Play Services autorise les mises à jour de sécurité et constitue une dépendance de niveau de base pour de nombreuses fonctionnalités de sécurité sur les appareils Google certifiés. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Fournisseur de sécurité à jour** : un fournisseur de sécurité à jour **doit** protéger l’appareil contre les vulnérabilités connues. Quand vous choisissez **Non configuré** (option par défaut), ce paramètre n’est pas évalué pour déterminer la conformité ou la non-conformité.
- **Analyse des menaces sur les applications** : la fonctionnalité Android **Vérifier les applications** **doit** être impérativement activée. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

  > [!NOTE]
  > Sur la plateforme Android héritée, cette fonctionnalité constitue un paramètre de conformité. Intune ne peut que vérifier si ce paramètre est activé au niveau de l’appareil.

- **Attestation d’appareil SafetyNet** : entrez le niveau d’[attestation SafetyNet](https://developer.android.com/training/safetynet/attestation.html) à respecter. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : le paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Vérifier l’intégrité de base**
  - **Vérifier l’intégrité de base et les appareils certifiés**

## <a name="device-property-settings"></a>Paramètres de propriétés d’appareils

- **Version minimale du système d’exploitation** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.
- **Version maximale du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant que la règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe de l’utilisateur.
- **Type de mot de passe obligatoire** : choisissez si un mot de passe doit inclure uniquement des caractères numériques, ou s’il doit comporter un mélange de caractères numériques et d’autres caractères. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Au moins numérique** (par défaut)
  - **Chiffres complexes** : les chiffres répétés ou consécutifs, comme `1111` ou `1234`, ne sont pas autorisés.
  - **Au moins alphabétique** 
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**

- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant que le mot de passe n’expire et que l’utilisateur ne doive en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre de mots de passe récents qui ne peuvent pas être réutilisés. Utilisez ce paramètre pour empêcher l’utilisateur de créer des mots de passe déjà utilisés.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** (Android 4.0 et versions ultérieures ou KNOX 4.0 et versions ultérieures) : choisissez **Exiger** pour chiffrer le stockage des données sur vos appareils. Les appareils sont chiffrés quand vous choisissez le paramètre **Exiger un mot de passe pour déverrouiller les appareils mobiles**. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

### <a name="device-security"></a>Sécurité du périphérique

- **Bloquer les applications provenant de sources inconnues** : choisissez de **bloquer** les appareils où « Sécurité > Sources inconnues » est activé (pris en charge par Android 4.0 - Android 7.x ; non pris en charge par Android 8.0 et les versions ultérieures). Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

  Pour effectuer un chargement indépendant des applications, vous devez autoriser les sources inconnues. Si vous n’effectuez pas de chargement indépendant des applications Android, configurez la fonctionnalité sur **Bloquer** pour activer cette stratégie de conformité. 

  > [!IMPORTANT]
  > Pour permettre le chargement indépendant des applications, le paramètre **Bloquer les applications provenant de sources inconnues** doit être activé. Appliquez cette stratégie de conformité uniquement si vous n’effectuez aucun chargement indépendant d’applications Android sur les appareils.

- **Intégrité du runtime de l’application Portail d’entreprise** : choisissez **Exiger** pour vérifier que l’application Portail d’entreprise remplit toutes les conditions suivantes :

  - Comporte l’installation de l’environnement d’exécution par défaut
  - Est signée correctement
  - N’est pas en mode de débogage
  - Est installée à partir d’une source connue

  Quand vous choisissez **Non configuré** (option par défaut), ce paramètre n’est pas évalué pour déterminer la conformité ou la non-conformité.

- **Bloquer le débogage USB sur l’appareil** (Android 4.2 ou version ultérieure) : choisissez **Bloquer** pour empêcher les appareils d’utiliser la fonctionnalité de débogage USB. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Niveau minimal du correctif de sécurité** (Android 6.0 ou version ultérieure) : sélectionnez le niveau le plus ancien possible pour le correctif de sécurité d’un appareil. Les appareils qui ne sont pas au moins à ce niveau de correctif sont non conformes. Vous devez entrer la date au format `YYYY-MM-DD`.
- **Applications restreintes** : entrez le **Nom de l’application** et l’**ID d’ensemble d’applications** des applications à restreindre. Choisissez **Ajouter**. Un appareil doté d’au moins une application limitée est marqué comme non conforme.

Une fois que vous avez terminé, sélectionnez **OK** > **OK** pour enregistrer vos changements.

## <a name="locations"></a>Emplacements

Dans votre stratégie, faites votre choix parmi les emplacements existants. Vous n’avez pas encore d’emplacement ? L’article [Utiliser des emplacements (délimitation du réseau) dans Intune](use-network-locations.md) fournit quelques conseils.

1. Choisir **Emplacements**.
2. Dans la liste, vérifiez votre emplacement, puis choisissez **Sélectionner**.
3. **Enregistrez** la stratégie.

## <a name="actions-for-noncompliance"></a>Actions en cas de non-conformité

Sélectionnez **Actions en cas de non-conformité**. L’action par défaut marque immédiatement l’appareil comme étant non conforme.

Vous pouvez changer la planification quand l’appareil est marqué comme non conforme, par exemple après un jour. Vous pouvez également configurer une deuxième action qui envoie un e-mail à l’utilisateur quand l’appareil n’est pas conforme.

L’article [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) fournit plus d’informations, notamment sur la création d’un e-mail de notification pour vos utilisateurs.

Par exemple, vous utilisez la fonctionnalité Emplacements et ajoutez un emplacement à une stratégie de conformité. L’action par défaut en cas de non-conformité s’applique quand vous sélectionnez au moins un emplacement. Si l’appareil n’est pas connecté aux emplacements sélectionnés, il est immédiatement considéré comme non conforme. Vous pouvez accorder aux utilisateurs une période de grâce, par exemple un jour.

## <a name="scope-tags"></a>Balises d'étendue

Les étiquettes de délimitation sont un excellent moyen d’affecter des stratégies à des groupes spécifiques, par exemple Ventes, Ingénierie, Ressources humaines, etc. Vous pouvez ajouter des étiquettes de délimitation aux stratégies de conformité. Consultez [Utiliser des étiquettes de délimitation pour filtrer les stratégies](scope-tags.md). 

## <a name="assign-user-groups"></a>Affectation de groupes d’utilisateurs

Une fois qu’une stratégie est créée, elle ne fait rien tant que vous ne l’avez pas affectée. Pour affecter la stratégie : 

1. Choisissez une stratégie que vous avez configurée. Les stratégies existantes se trouvent dans **Conformité de l’appareil** > **Stratégies**.
2. Choisissez la stratégie, puis **Affectations**. Vous pouvez inclure ou exclure des groupes de sécurité Azure AD (Azure Active Directory).
3. Choisissez **Groupes sélectionnés** pour voir vos groupes de sécurité Azure AD. Sélectionnez les groupes d’utilisateurs auxquels vous souhaitez appliquer cette stratégie, puis choisissez **Enregistrer** pour déployer la stratégie auprès des utilisateurs.

Vous avez appliqué la stratégie aux utilisateurs. La conformité des appareils utilisés par les utilisateurs ciblés par la stratégie est évaluée.

## <a name="next-steps"></a>Étapes suivantes
[Automatiser l’envoi d’un e-mail et ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md)  
[Surveiller les stratégies de conformité d’appareils Intune](compliance-policy-monitor.md)  
[Paramètres de stratégie de conformité pour Android Entreprise](compliance-policy-create-android-for-work.md)
