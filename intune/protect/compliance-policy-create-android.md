---
title: Paramètres de conformité des appareils Android dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser lors de la configuration de la conformité pour vos appareils Android dans Microsoft Intune. Définissez des règles de mot de passe, choisissez une version minimale ou maximale pour le système d’exploitation, appliquez des restrictions pour certaines applications, empêchez la réutilisation d’un même mot de passe, etc.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8efb9dcf9129375252b5d9a7d1e6255dce39625c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801408"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres Android pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils Android dans Intune. Dans le cadre de votre solution MDM, vous pouvez utiliser ces paramètres pour marquer les appareils rootés (jailbreakés) comme étant non conformes, définir le niveau de menace autorisé, activer Google Play Protect, etc.

Cette fonctionnalité s’applique à :

- Administrateur d’appareil Android

En tant qu’administrateur de service Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour **plateforme**, sélectionnez **administrateur d’appareil Android**.

## <a name="device-health"></a>Intégrité de l’appareil

- **Appareils rootés** :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Bloquer** : marquer les appareils rootés (jailbreakés) comme étant non conformes.

- **Exiger que l’appareil soit au niveau ou sous le niveau de défense contre les menaces mobiles** :

  Utilisez ce paramètre pour effectuer l’évaluation des risques d’un service mobile Threat Defense connecté en tant que condition de conformité.
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité. 
  - **Sécurisé** : cette option est la plus sécurisée, car l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sur celui-ci sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.

### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services est configuré** :

  Google Play Services autorise les mises à jour de sécurité et constitue une dépendance de niveau de base pour de nombreuses fonctionnalités de sécurité sur les appareils Google certifiés.

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.  
  - **Exiger** : l’application Google Play Services doit être installée et activée.  

- **Fournisseur de sécurité à jour** :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : un fournisseur de sécurité à jour doit être en mesure de protéger un appareil contre les vulnérabilités connues.

- **Exiger l’analyse des menaces sur les applications** :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : la fonctionnalité **Vérifier les applications** Android doit être activée.

  > [!NOTE]
  > Sur la plateforme Android héritée, cette fonctionnalité constitue un paramètre de conformité. Intune ne peut que vérifier si ce paramètre est activé au niveau de l’appareil.

- **Attestation d’appareil SafetyNet** :

  entrez le niveau d’[attestation SafetyNet](https://developer.android.com/training/safetynet/attestation.html) à respecter. Les options disponibles sont les suivantes :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Vérifier l’intégrité de base**
  - **Vérifier l’intégrité de base et les appareils certifiés**

> [!NOTE]
> Pour configurer les paramètres de Google Play Protect en utilisant des stratégies de protection des applications, consultez [Paramètres de stratégie de protection des applications Intune](../apps/app-protection-policy-settings-android.md#conditional-launch) sur Android.

## <a name="device-properties"></a>Propriétés de l’appareil

### <a name="operating-system-version"></a>Version du système d'exploitation 

- **Version minimale du système d’exploitation** :

  quand un appareil ne répond pas à la condition de version minimale du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.

  *Par défaut, aucune version n’est configurée*.

- **Version maximale du système d’exploitation** :

  Quand un appareil utilise une version du système d’exploitation postérieure à la version spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant que la règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.

  *Par défaut, aucune version n’est configurée*.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

<!-- Removed
- **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.   


- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password. When you choose **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.

- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

-->

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : les utilisateurs doivent entrer un mot de passe pour pouvoir accéder à leur appareil.

- **Type de mot de passe requis** :

  Choisissez si un mot de passe doit inclure uniquement des caractères numériques, ou s’il doit comporter un mélange de caractères numériques et d’autres caractères. Les options disponibles sont les suivantes :

  - **Valeur par défaut** de l’appareil : pour évaluer la conformité du mot de passe, veillez à sélectionner une force de mot de passe autre que l' **appareil par défaut**.
  - **Sécurité biométrique faible**
  - **Au moins numérique**
  - **Chiffres complexes** : les chiffres répétés ou consécutifs, comme `1111` ou `1234`, ne sont pas autorisés.
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur un appareil** :  
  *Prise en charge sur Android 4,0 et versions ultérieures, ou KNOX 4,0 et versions ultérieures.*

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** -chiffrer le stockage des données sur vos appareils. Les appareils sont chiffrés quand vous choisissez le paramètre **Exiger un mot de passe pour déverrouiller les appareils mobiles**.

### <a name="device-security"></a>Sécurité du périphérique

- **Bloquer les applications provenant de sources inconnues** :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - Bloquer **les appareils** avec **sécurité > sources inconnues** sources activées (*prises en charge sur Android 4,0 via Android 7. x. Non pris en charge par Android 8.0 et les versions ultérieures*).

  Pour effectuer un chargement indépendant des applications, vous devez autoriser les sources inconnues. Si vous n’effectuez pas de chargement indépendant des applications Android, configurez la fonctionnalité sur **Bloquer** pour activer cette stratégie de conformité.

  > [!IMPORTANT]
  > Pour permettre le chargement indépendant des applications, le paramètre **Bloquer les applications provenant de sources inconnues** doit être activé. Appliquez cette stratégie de conformité uniquement si vous n’effectuez aucun chargement indépendant d’applications Android sur les appareils.

- **Intégrité du runtime de l’application Portail d’entreprise** :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : choisissez *Exiger* pour vérifier que l’application Portail d’entreprise remplit toutes les conditions suivantes :

    - Comporte l’installation de l’environnement d’exécution par défaut
    - Est signée correctement
    - N’est pas en mode de débogage
    - Est installée à partir d’une source connue

- **Bloquer le débogage USB sur l’appareil** *(Android 4,2 ou version ultérieure)* :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Bloquer** : empêcher les appareils d’utiliser la fonctionnalité de débogage USB.

- **Niveau de correctif de sécurité minimal** *(Android 6,0 ou version ultérieure)* :

  sélectionnez le niveau le plus ancien possible pour le correctif de sécurité d’un appareil. Les appareils qui ne sont pas au moins à ce niveau de correctif sont non conformes. Vous devez entrer la date au format `YYYY-MM-DD`.

  *Par défaut, aucune date n’est configurée*.

- **Applications restreintes** :

  Entrez le **Nom de l’application** et **l’ID d’ensemble d’applications** des applications à restreindre, puis sélectionnez **Ajouter**. Un appareil doté d’au moins une application limitée est marqué comme non conforme.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils Android Entreprise](compliance-policy-create-android-for-work.md).
