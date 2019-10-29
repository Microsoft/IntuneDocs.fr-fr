---
title: Paramètres de conformité Android Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser lorsque vous configurez la conformité de vos appareils Android Entreprise dans Microsoft Intune. Définissez des règles de mot de passe, choisissez une version minimale ou maximale pour le système d’exploitation, appliquez des restrictions pour certaines applications, empêchez la réutilisation d’un même mot de passe, etc.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/16/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be1fbb72821b61566da84d6f98094c9a2f6ffef2
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810265"
---
# <a name="android-enterprise-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres Android Entreprise pour marquer les appareils comme étant conformes ou non conformes à l’aide d’Intune

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils Android Entreprise dans Intune. Dans le cadre de votre solution de gestion des appareils mobiles, vous pouvez utiliser ces paramètres pour marquer les appareils rootés (jailbreakés) comme étant non conformes, définir le niveau de menace autorisé, activer Google Play Protect, etc.

Cette fonctionnalité s’applique à :

- Android Entreprise

En tant qu’administrateur de service Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

> [!IMPORTANT]
> Les stratégies de conformité appliquent également des appareils Android dédiés à l’entreprise. Si une stratégie de conformité est affectée à un appareil dédié, l’appareil peut s’afficher comme étant **non conforme**. L’accès conditionnel et l’application de la conformité ne sont pas disponibles sur les appareils dédiés. Veillez à effectuer toutes les tâches ou actions pour obtenir des appareils dédiés conformes à vos stratégies attribuées.

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour **Plateforme**, sélectionnez **Android Entreprise**.

## <a name="device-owner"></a>Propriétaire de l’appareil

### <a name="device-health"></a>Intégrité de l’appareil

- **Exiger que l’appareil soit au niveau des menaces de l’appareil ou en dessous**: sélectionnez le niveau de menace maximal de l’appareil autorisé évalué par votre [service mobile Threat Defense](mobile-threat-defense.md). Les appareils qui dépassent ce niveau de menace sont marqués comme non conformes. Pour utiliser ce paramètre, choisissez le niveau de menace autorisé :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Sécurisé** : cette option est la plus sécurisée. Elle signifie que l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est évalué comme conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, car elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.
  
> [!NOTE] 
> Les fournisseurs de défense contre les menaces mobiles suivants prennent en charge les déploiements de propriétaires d’appareils Android Enterprise à l’aide de la configuration d’application :
> - Better Mobile 
> - Pradeo
> - Sophos Mobile
> - Zimperium 
>  
>  Vérifiez avec votre fournisseur MTD la configuration exacte nécessaire pour prendre en charge les plateformes propriétaires d’appareils Android Enterprise sur Intune. Cette liste est mise à jour, car les parties MTD prennent en charge les scénarios de propriétaire d’appareils Android Enterprise. 

#### <a name="google-play-protect"></a>Google Play Protect

- **Attestation d’appareil SafetyNet** : entrez le niveau d’[attestation SafetyNet](https://developer.android.com/training/safetynet/attestation.html) à respecter. Les options disponibles sont les suivantes :
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Vérifier l’intégrité de base**
  - **Vérifier l’intégrité de base et les appareils certifiés**

### <a name="device-properties"></a>Propriétés de l’appareil

#### <a name="operating-system-version"></a>Version du système d'exploitation

- **Version minimale du système d’exploitation** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut mettre à niveau son appareil, puis accéder aux ressources de l’organisation.

  *Par défaut, aucune version n’est configurée*.

- **Version maximale du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version présente dans la règle, l’accès aux ressources de l’organisation est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant qu’une règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’organisation.

  *Par défaut, aucune version n’est configurée*.

- **Niveau minimal du correctif de sécurité** : sélectionnez le niveau le plus ancien possible pour le correctif de sécurité d’un appareil. Les appareils qui ne sont pas au moins à ce niveau de correctif sont non conformes. Vous devez entrer la date au format AAAA-MM-JJ.

  *Par défaut, aucune date n’est configurée*.


### <a name="system-security"></a>Sécurité système

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : les utilisateurs doivent entrer un mot de passe pour pouvoir accéder à leur appareil. 

  Ce paramètre s’applique au niveau de l’appareil. Si vous avez besoin d’exiger un mot de passe uniquement au niveau du profil de travail, utilisez une stratégie de configuration. Consultez [Paramètres de configuration d’appareil Android Entreprise](../configuration/device-restrictions-android-for-work.md).

  - **Type de mot de passe obligatoire** : choisissez si un mot de passe doit inclure uniquement des caractères numériques, ou s’il doit comporter un mélange de caractères numériques et d’autres caractères. Les options disponibles sont les suivantes :
    - **Valeur par défaut** de l’appareil : pour évaluer la conformité du mot de passe, veillez à sélectionner une force de mot de passe autre que l' **appareil par défaut**.  
    - **Mot de passe requis, sans restriction**
    - **Biométrie faible** - [Biométrie forte et faible](https://android-developers.googleblog.com/2018/06/better-biometrics-in-android-p.html) (dirige sur le site web d’Android)
    - **Numérique** (*par défaut*) : le mot de passe ne doit comporter que des nombres, par exemple `123456789`. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
    - **Chiffres complexes** : les chiffres répétés ou consécutifs (comme « 1111 » ou « 1234 ») ne sont pas autorisés. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
    - **Alphabétique** : des lettres de l’alphabet sont nécessaires. Les nombres et symboles ne sont pas nécessaires. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
    - **Alphanumériques** : inclut des lettres majuscules, minuscules et des caractères numériques. Entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
    - **Alphanumérique avec symboles** : inclut des lettres majuscules, minuscules, des caractères numériques, des signes de ponctuation et des symboles. Entrez également :
    
    Selon le type de *mot de passe* que vous sélectionnez, les paramètres suivants sont disponibles :  
    - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe (entre 4 et 16 caractères).  

    - **Nombre de caractères requis** : entrez le nombre de caractères du mot de passe (entre 0 et 16 caractères).

    - **Nombre de caractères minuscules** : entrez le nombre de caractères minuscules du mot de passe (entre 0 et 16 caractères).

    - **Nombre de caractères majuscules** : entrez le nombre de caractères majuscules du mot de passe (entre 0 et 16 caractères).

    - **Nombre de caractères non lettres requis** : entrez le nombre de caractères non lettres (tout caractère hors lettres de l’alphabet) du mot de passe (entre 0 et 16 caractères).

    - **Nombre de caractères numériques requis** : entrez le nombre de caractères numériques (`1`, `2`, `3`, etc.) du mot de passe (entre 0 et 16 caractères).
    
    - **Nombre de symboles requis** : entrez le nombre de symboles (`&`, `#`, `%`, etc.) du mot de passe (entre 0 et 16 caractères).
 
- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe. Les options incluent la valeur par défaut *non configurée*et comprise entre *1 minute* et *8 heures*.

- **Nombre de jours avant expiration du mot de passe** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (entre 1 et 365). Par exemple, pour modifier le mot de passe après 60 jours, entrez `60`. Lorsque le mot de passe arrive à expiration, les utilisateurs sont invités à créer un mot de passe.

   *Par défaut, aucune valeur n’est configurée*.

- **Nombre de mots de passe requis avant que l’utilisateur puisse réutiliser un mot de passe** : entrez le nombre de mots de passe récents ne pouvant être réutilisés (entre 1 et 24). Utilisez ce paramètre pour empêcher l’utilisateur de créer des mots de passe déjà utilisés.  

    *Par défaut, aucune version n’est configurée*.

#### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** -chiffrer le stockage des données sur vos appareils.  

  Vous n’avez pas besoin de configurer ce paramètre, car les appareils Android Entreprise appliquent le chiffrement.

## <a name="work-profile"></a>Profil professionnel

### <a name="device-health"></a>Intégrité de l’appareil

- **Appareils rootés** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Bloquer** : marquer les appareils rootés (jailbreakés) comme étant non conformes.  

- **Exiger que l’appareil soit au niveau des menaces de l’appareil ou en dessous**: sélectionnez le niveau de menace maximal de l’appareil autorisé évalué par votre [service mobile Threat Defense](mobile-threat-defense.md). Les appareils qui dépassent ce niveau de menace sont marqués comme non conformes. Pour utiliser ce paramètre, choisissez le niveau de menace autorisé :

  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Sécurisé** : cette option est la plus sécurisée. Elle signifie que l’appareil ne doit présenter aucune menace. Si le moindre niveau de menace est détecté sur l’appareil, celui-ci est considéré comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est évalué comme conforme si les menaces détectées sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, car elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.

#### <a name="google-play-protect"></a>Google Play Protect

- **Google Play Services est configuré** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : l’application Google Play Services doit être installée et activée. Google Play Services autorise les mises à jour de sécurité et constitue une dépendance de niveau de base pour de nombreuses fonctionnalités de sécurité sur les appareils Google certifiés. 
  
- **Fournisseur de sécurité à jour** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : un fournisseur de sécurité à jour doit être en mesure de protéger un appareil contre les vulnérabilités connues. 
  
- **Attestation d’appareil SafetyNet** : entrez le niveau d’[attestation SafetyNet](https://developer.android.com/training/safetynet/attestation.html) à respecter. Les options disponibles sont les suivantes :
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Vérifier l’intégrité de base**
  - **Vérifier l’intégrité de base et les appareils certifiés**

> [!NOTE]
> Sur les appareils Android Entreprise, le paramètre **Analyse des menaces sur les applications** correspond à une stratégie de configuration des appareils. À l’aide d’une stratégie de configuration, les administrateurs peuvent activer ce paramètre sur un appareil. Consultez [Paramètres de restriction d’appareil Android Entreprise](../configuration/device-restrictions-android-for-work.md).

### <a name="device-properties"></a>Propriétés de l’appareil

#### <a name="operating-system-version"></a>Version du système d'exploitation

- **Version minimale du système d’exploitation** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut mettre à niveau son appareil, puis accéder aux ressources de l’organisation.

  *Par défaut, aucune version n’est configurée*.

- **Version maximale du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version présente dans la règle, l’accès aux ressources de l’organisation est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant qu’une règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’organisation.

  *Par défaut, aucune version n’est configurée*.

### <a name="system-security"></a>Sécurité système

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité. 
  - **Exiger** : les utilisateurs doivent entrer un mot de passe pour pouvoir accéder à leur appareil.  

  Ce paramètre s’applique au niveau de l’appareil. Si vous avez besoin d’exiger un mot de passe uniquement au niveau du profil de travail, utilisez une stratégie de configuration. Consultez [Paramètres de configuration d’appareil Android Entreprise](../configuration/device-restrictions-android-for-work.md).

- **Type de mot de passe obligatoire** : choisissez si un mot de passe doit inclure uniquement des caractères numériques, ou s’il doit comporter un mélange de caractères numériques et d’autres caractères. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Au moins numérique** (*par défaut*) : entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Chiffres complexes** : entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Au moins alphabétique** : entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Au moins alphanumérique** : entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).
  - **Au moins alphanumérique avec des symboles** : entrez la **longueur minimale du mot de passe** qu’un utilisateur doit saisir (entre 4 et 16 caractères).

  Selon le type de *mot de passe* que vous sélectionnez, les paramètres suivants sont disponibles :  
  - **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe. Les options incluent la valeur par défaut *non configurée*et comprise entre *1 minute* et *8 heures*.

  - **Nombre de jours avant expiration du mot de passe** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (entre 1 et 365). Par exemple, pour modifier le mot de passe après 60 jours, entrez `60`. Lorsque le mot de passe arrive à expiration, les utilisateurs sont invités à créer un mot de passe.

  - **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe (entre 4 et 16 caractères). 
  
  - **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre de mots de passe récents qui ne peuvent pas être réutilisés. Utilisez ce paramètre pour empêcher l’utilisateur de créer des mots de passe déjà utilisés.

#### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** -chiffrer le stockage des données sur vos appareils.  

  Vous n’avez pas besoin de configurer ce paramètre, car les appareils Android Entreprise appliquent le chiffrement.

#### <a name="device-security"></a>Sécurité du périphérique

- **Bloquer les applications provenant de sources inconnues** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - Bloquer **les appareils** avec **sécurité** > **sources inconnues** sources activées (*prises en charge sur Android 4,0 via Android 7. x. Non pris en charge par Android 8.0 et les versions ultérieures*).  

  Pour effectuer un chargement indépendant des applications, vous devez autoriser les sources inconnues. Si vous n’effectuez pas de chargement indépendant des applications Android, configurez la fonctionnalité sur **Bloquer** pour activer cette stratégie de conformité.

  > [!IMPORTANT]
  > Pour permettre le chargement indépendant des applications, le paramètre **Bloquer les applications provenant de sources inconnues** doit être activé. Appliquez cette stratégie de conformité uniquement si vous n’effectuez aucun chargement indépendant d’applications Android sur les appareils.

  Vous n’avez pas à configurer ce paramètre, car les appareils Android Entreprise appliquent toujours des restrictions quant aux installations effectuées à partir de sources inconnues.

- **Intégrité du runtime de l’application Portail d’entreprise** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : choisissez *Exiger* pour vérifier que l’application Portail d’entreprise remplit toutes les conditions suivantes :
    - Comporte l’installation de l’environnement d’exécution par défaut
    - Est signée correctement
    - N’est pas en mode de débogage
    - Est installée à partir d’une source connue

- **Bloquer le débogage USB sur l’appareil** : 
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Bloquer** : empêcher les appareils d’utiliser la fonctionnalité de débogage USB.  

  Vous n’avez pas besoin de configurer ce paramètre, car le débogage USB est déjà désactivé sur les appareils Android Entreprise.

- **Niveau minimal du correctif de sécurité** : sélectionnez le niveau le plus ancien possible pour le correctif de sécurité d’un appareil. Les appareils qui ne sont pas au moins à ce niveau de correctif sont non conformes. Vous devez entrer la date au format AAAA-MM-JJ.

  *Par défaut, aucune date n’est configurée*.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils Android](compliance-policy-create-android.md).
