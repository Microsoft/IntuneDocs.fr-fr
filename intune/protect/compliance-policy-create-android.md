---
title: Paramètres de conformité des appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser lors de la configuration de la conformité pour vos appareils Android dans Microsoft Intune. Définissez des règles de mot de passe, choisissez une version minimale ou maximale pour le système d’exploitation, appliquez des restrictions pour certaines applications, empêchez la réutilisation d’un même mot de passe, etc.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4237b54b3ea89fcf75ce5a21f08012f384eed95c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502523"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres Android pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils Android dans Intune. Dans le cadre de votre solution MDM, vous pouvez utiliser ces paramètres pour marquer les appareils rootés (jailbreakés) comme étant non conformes, définir le niveau de menace autorisé, activer Google Play Protect, etc.

Cette fonctionnalité s’applique à :

- Android

En tant qu’administrateur Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour l’option **Plateforme**, sélectionnez **Android**.

## <a name="device-health"></a>Device health

- **Appareils rootés** : choisissez **Bloquer** pour marquer les appareils rootés (jailbreakés) comme étant non conformes. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Exiger que l’appareil se situe au niveau de menace d’appareil ou en dessous** : utilisez ce paramètre pour considérer l’évaluation des risques de la solution Lookout Mobile Endpoint Security comme une condition de conformité. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Pour utiliser ce paramètre, choisissez le niveau de menace autorisé :
  - **Sécurisé** : cette option est la plus sécurisée, car l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sur celui-ci sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.

### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services est configuré** : l’application Google Play Services **doit être impérativement** installée et activée. Google Play Services autorise les mises à jour de sécurité et constitue une dépendance de niveau de base pour de nombreuses fonctionnalités de sécurité sur les appareils Google certifiés. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Fournisseur de sécurité à jour** : un fournisseur de sécurité à jour **doit** protéger l’appareil contre les vulnérabilités connues. Quand vous choisissez **Non configuré** (option par défaut), ce paramètre n’est pas évalué pour déterminer la conformité ou la non-conformité.
- **Analyse des menaces sur les applications** : la fonctionnalité Android **Vérifier les applications** **doit** être impérativement activée. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

  > [!NOTE]
  > Sur la plateforme Android héritée, cette fonctionnalité constitue un paramètre de conformité. Intune ne peut que vérifier si ce paramètre est activé au niveau de l’appareil.

- **Attestation d’appareil SafetyNet** : entrez le niveau d’[attestation SafetyNet](https://developer.android.com/training/safetynet/attestation.html) à respecter. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : le paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Vérifier l’intégrité de base**
  - **Vérifier l’intégrité de base et les appareils certifiés**

> [!NOTE]
> Pour configurer les paramètres de Google Play Protect en utilisant des stratégies de protection des applications, consultez [Paramètres de stratégie de protection des applications Intune](../apps/app-protection-policy-settings-android.md#conditional-launch) sur Android.

## <a name="device-property-settings"></a>Paramètres de propriétés d’appareils

- **Version minimale du système d’exploitation** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.
- **Version maximale du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant que la règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe de l’utilisateur.
- **Type de mot de passe obligatoire** : choisissez si un mot de passe doit inclure uniquement des caractères numériques, ou s’il doit comporter un mélange de caractères numériques et d’autres caractères. Les options disponibles sont les suivantes :
  - **Valeur par défaut**de l’appareil : pour évaluer la conformité du mot de passe, veillez à sélectionner une force de mot de passe autre que l' **appareil par défaut**.
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

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

## <a name="locations"></a>Emplacements

Dans votre stratégie, vous pouvez forcer la conformité selon l’emplacement de l’appareil. Choisissez parmi les emplacements existants. Vous n’avez pas encore d’emplacement ? L’article [Utiliser des emplacements (délimitation du réseau)](use-network-locations.md) dans Intune fournit des conseils.

1. Choisissez **Emplacements** > **Sélectionner les emplacements**.
2. Dans la liste, vérifiez votre emplacement > **Sélectionner**.
3. **Enregistrez** la stratégie.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils Android Entreprise](compliance-policy-create-android-for-work.md).
