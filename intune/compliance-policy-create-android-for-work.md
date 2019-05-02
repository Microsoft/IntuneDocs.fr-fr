---
title: Paramètres d’appareil Android Enterprise dans Microsoft Intune - Azure | Microsoft Docs
description: Afficher la liste de tous les paramètres que vous pouvez utiliser lors de la définition de conformité pour vos appareils d’entreprise Android dans Microsoft Intune. Définir des règles de mot de passe, choisissez une version du système d’exploitation minimale ou maximale, restreindre des applications spécifiques, empêcher la réutilisation des mots de passe et bien plus encore.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 16db0acab84a1095c40e9a92648c75c2581187cd
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423558"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres d’entreprise Android pour marquer les appareils conformes ou non conformes à l’aide d’Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article répertorie et décrit les paramètres de conformité différents que vous pouvez configurer sur les appareils d’entreprise Android dans Intune. Dans le cadre de votre solution de gestion des appareils mobiles, utilisez ces paramètres pour marquer les appareils rootés (jailbroken) comme non conforme, définissez un niveau de menace autorisée, activer Google Play Protect et bien plus encore.

Cette fonctionnalité s’applique à :

- Android Entreprise

En tant qu’administrateur Intune, utilisez ces paramètres de conformité pour vous aider à protéger vos ressources de l’organisation. Pour en savoir plus sur les stratégies de conformité et sur les prérequis, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour **Plateforme**, sélectionnez **Android Entreprise**.

## <a name="device-health"></a>Device health

- **Appareils rootés** : choisissez **Bloquer** pour marquer les appareils rootés (jailbreakés) comme étant non conformes. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Exiger que l’appareil se situe au niveau de menace d’appareil ou en dessous** : utilisez ce paramètre pour considérer l’évaluation des risques de la solution Lookout MTP comme une condition de conformité. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Pour utiliser ce paramètre, choisissez le niveau de menace autorisé :
  - **Sécurisé** : cette option est la plus sécurisée. Elle signifie que l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est évalué comme conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, car elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.

### <a name="google-play-protect"></a>Protéger de Google Play

- **Google Play Services est configuré** : l’application Google Play Services **doit être impérativement** installée et activée. Google Play Services autorise les mises à jour de sécurité et constitue une dépendance de niveau de base pour de nombreuses fonctionnalités de sécurité sur les appareils Google certifiés. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Fournisseur de sécurité à jour** : un fournisseur de sécurité à jour **doit** protéger l’appareil contre les vulnérabilités connues. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Attestation d’appareil SafetyNet** : entrez le niveau d’[attestation SafetyNet](https://developer.android.com/training/safetynet/attestation.html) à respecter. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : le paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Vérifier l’intégrité de base**
  - **Vérifier l’intégrité de base et les appareils certifiés**

> [!NOTE]
> Sur les appareils Android Enterprise, **analyse des menaces sur les applications** est une stratégie de configuration de périphérique. À l’aide d’une stratégie de configuration, les administrateurs peuvent activer le paramètre sur un appareil. Consultez [Paramètres de restriction d’appareil Android Entreprise](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Paramètres de propriétés des appareils

- **Version minimale du système d’exploitation** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.
- **Version maximale du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version présente dans la règle, l’accès aux ressources de l’entreprise est bloqué. De plus, l’utilisateur est invité à contacter son administrateur informatique. Tant que la règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.

## <a name="system-security-settings"></a>Paramètres de sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. Ce paramètre est appliqué au niveau de l’appareil. Si vous avez besoin d’exiger un mot de passe uniquement au niveau du profil de travail, utilisez une stratégie de configuration. Consultez [Paramètres de configuration d’appareil Android Entreprise](device-restrictions-android-for-work.md).
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe de l’utilisateur.
- **Type de mot de passe obligatoire** : choisissez si un mot de passe doit inclure uniquement des caractères numériques, ou s’il doit comporter un mélange de caractères numériques et d’autres caractères. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Au moins numérique** (par défaut)
  - **Chiffres complexes**
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**

- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et l’obligation d’en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre de mots de passe récents qui ne peuvent pas être réutilisés. Utilisez ce paramètre pour empêcher l’utilisateur de créer des mots de passe déjà utilisés.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** : choisissez **Exiger** pour chiffrer le stockage des données sur vos appareils. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité. 

  Vous n’avez pas besoin de configurer ce paramètre, car les appareils avec profil professionnel Android appliquent le chiffrement.

### <a name="device-security"></a>Sécurité du périphérique

- **Bloquer les applications provenant de sources inconnues** : choisissez de **bloquer** les appareils où « Sécurité > Sources inconnues » est activé (pris en charge par Android 4.0 - Android 7.x ; non pris en charge par Android 8.0 et les versions ultérieures). Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

  Pour effectuer un chargement indépendant des applications, vous devez autoriser les sources inconnues. Si vous n’effectuez pas de chargement indépendant des applications Android, configurez la fonctionnalité sur **Bloquer** pour activer cette stratégie de conformité. 

  > [!IMPORTANT]
  > Pour permettre le chargement indépendant des applications, le paramètre **Bloquer les applications provenant de sources inconnues** doit être activé. Appliquez cette stratégie de conformité uniquement si vous n’effectuez aucun chargement indépendant d’applications Android sur les appareils.

  Vous n’avez pas à configurer ce paramètre, car les appareils avec profil professionnel Android limitent toujours l’installation à partir de sources inconnues.

- **Intégrité du runtime de l’application Portail d’entreprise** : choisissez **Exiger** pour vérifier que l’application Portail d’entreprise remplit toutes les conditions suivantes :

  - Comporte l’installation de l’environnement d’exécution par défaut
  - Est signée correctement
  - N’est pas en mode de débogage
  - Est installée à partir d’une source connue

  Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

- **Bloquer le débogage USB sur l’appareil** : choisissez **Bloquer** pour empêcher les appareils d’utiliser la fonctionnalité de débogage USB. Quand vous choisissez **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

  Vous n’avez pas besoin de configurer ce paramètre, car le débogage USB est déjà désactivé sur les appareils avec profil professionnel Android.

- **Niveau minimal du correctif de sécurité** : sélectionnez le niveau le plus ancien possible pour le correctif de sécurité d’un appareil. Les appareils qui ne sont pas au moins à ce niveau de correctif sont non conformes. Vous devez entrer la date au format *AAAA-MM-JJ*.

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [utiliser des balises d’étendue pour filtrer les stratégies](scope-tags.md).
- [Surveiller vos stratégies de conformité](compliance-policy-monitor.md).
- [Paramètres de stratégie de conformité pour les appareils Android](compliance-policy-create-android.md)
