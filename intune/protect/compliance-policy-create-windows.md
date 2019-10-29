---
title: Paramètres de conformité de Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser quand vous configurez la conformité de vos appareils Windows 10, Windows Holographic et Surface Hub dans Microsoft Intune. Vérifiez la conformité sur le système d’exploitation minimal et maximal, définissez des restrictions et une longueur de mot de passe, recherchez les solutions anti-virus de partenaires, activez le chiffrement sur le stockage de données, etc.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3c6c029a5c5864eda46a68832b2f9f655553846
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889539"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres Windows de 10 et ultérieur pour marquer les appareils comme étant conformes ou non conformes avec Intune

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils Windows 10 et ultérieur dans Intune. Dans le cadre de votre solution MDM, utilisez ces paramètres pour exiger BitLocker, définir un système d’exploitation minimal et maximal, définir un niveau de risque avec Microsoft Defender Advanced Threat Protection (ATP), etc.

Cette fonctionnalité s’applique à :

- Windows 10 et versions ultérieures
- Windows Holographic for Business
- Surface Hub

En tant qu’administrateur Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.

## <a name="device-health"></a>Intégrité de l’appareil

### <a name="windows-health-attestation-service-evaluation-rules"></a>Règles d’évaluation du service d’attestation d’intégrité Windows

- **Exiger BitLocker** :  
   Le Chiffrement de lecteur BitLocker Windows chiffre toutes les données stockées sur le volume de système d’exploitation Windows. BitLocker utilise le Module de plateforme sécurisée (TPM) (TPM) pour protéger le système d’exploitation Windows et les données utilisateur. Il contribue également à prévenir la falsification d’un ordinateur, même si celui-ci est laissé sans assistance, perdu ou volé. Si l’ordinateur est équipé d’un module de plateforme sécurisée compatible, BitLocker utilise ce module pour verrouiller les clés de chiffrement qui protègent les données. Par conséquent, les clés sont inaccessibles tant que le TPM n’a pas vérifié l’état de l’ordinateur.  

   - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
   - **Exiger** : l’appareil peut protéger les données stockées sur le lecteur contre tout accès non autorisé quand le système est à l’arrêt ou en veille prolongée.  


- **Exiger l’activation du démarrage sécurisé sur l’appareil** :  
    - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
    - **Exiger** : le système est contraint de démarrer à un État approuvé par défaut. Les principaux composants utilisés pour démarrer la machine doivent avoir des signatures de chiffrement appropriées qui sont approuvées par l’organisation ayant fabriqué l’appareil. Le microprogramme UEFI vérifie la signature avant de laisser la machine démarrer. Si tous les fichiers sont falsifiés, ce qui interrompt leur signature, le système ne démarre pas.

  > [!NOTE]
  > Le paramètre **Exiger l’activation du démarrage sécurisé sur l’appareil** est pris en charge sur les appareils TPM 1.2 et 2.0. Pour les appareils qui ne prennent pas en charge TPM 2.0 ou une version ultérieure, l’état de la stratégie dans Intune s’affiche sous la forme **Non conforme**. Pour plus d’informations sur les versions prises en charge, consultez [Attestation d’intégrité de l’appareil](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Exiger l’intégrité du code** :  
  L’intégrité du code est une fonctionnalité qui valide l’intégrité d’un pilote ou d’un fichier système chaque fois qu’il est chargé en mémoire.
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  -  **Exiger** : exiger l’intégrité du code, qui détecte si un fichier système ou un pilote non signé est chargé dans le noyau. Cette fonctionnalité détecte également si un fichier système a été modifié par un logiciel malveillant ou exécuté par un compte d’utilisateur ayant des privilèges d’administrateur.

Autres ressources :

- Pour plus d’informations sur le fonctionnement du service d’attestation d’intégrité, consultez [CSP attestation d’intégrité](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).
- [Info de prise en charge : utilisation des paramètres d'attestation d’intégrité de l'appareil dans le cadre de votre stratégie de conformité Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643).

## <a name="device-properties"></a>Propriétés de l’appareil

### <a name="operating-system-version"></a>Version du système d'exploitation

- **Version minimale du système d’exploitation** :  
  Entrez la version minimale autorisée au format numérique **majeure.mineure.build.CU**. Pour obtenir la valeur correcte, ouvrez une invite de commandes, puis tapez `ver`. La commande `ver` retourne la version au format suivant :

  `Microsoft Windows [Version 10.0.17134.1]`

  Quand un appareil a une version antérieure à la version du système d’exploitation que vous entrez, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil. Une fois la mise à niveau effectuée, il peut accéder aux ressources de l’entreprise.

- **Version maximale du système d’exploitation** :  
  Entrez la valeur maximale autorisée au format numérique **majeure.mineure.build.révision**. Pour obtenir la valeur correcte, ouvrez une invite de commandes, puis tapez `ver`. La commande `ver` retourne la version au format suivant :

  `Microsoft Windows [Version 10.0.17134.1]`

  Quand un appareil utilise une version du système d’exploitation postérieure à la version entrée, l’accès aux ressources de l’organisation est bloqué. L’utilisateur final est invité à contacter son administrateur informatique. Cet appareil ne peut pas accéder aux ressources de l’organisation tant que la règle autorisant la version du système d’exploitation reste inchangée.

- **Système d’exploitation minimal requis pour les appareils mobiles** :  
  Entrez la version minimale autorisée au format numérique majeure.mineure.build.

  Quand un appareil a une version antérieure à la version du système d’exploitation que vous entrez, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil. Une fois la mise à niveau effectuée, il peut accéder aux ressources de l’entreprise.

- **Système d’exploitation maximal requis pour les appareils mobiles** :  
  Entrez la version maximale autorisée au format numérique majeure.mineure.build.

  Quand un appareil utilise une version du système d’exploitation postérieure à la version entrée, l’accès aux ressources de l’organisation est bloqué. L’utilisateur final est invité à contacter son administrateur informatique. Cet appareil ne peut pas accéder aux ressources de l’organisation tant que la règle autorisant la version du système d’exploitation reste inchangée.

- **Builds de système d’exploitation valides** :  
  Entrez la plage des versions de systèmes d’exploitation acceptées, notamment une valeur minimale et une valeur maximale. Vous pouvez également **exporter** une liste de fichiers de valeurs au format CSV de ces numéros de build de système d’exploitation acceptables.

## <a name="configuration-manager-compliance"></a>Conformité de Configuration Manager

S’applique uniquement aux appareils cogérés exécutant Windows 10 et versions ultérieures. Les appareils Intune uniquement retournent un état non disponible.

- **Exiger la conformité des appareils dans System Center Configuration Manager** :  
  - **Non configuré** (*par défaut*) : Intune ne vérifie la conformité d’aucun paramètre de Configuration Manager.
  - **Exiger** : obliger tous les paramètres (éléments de configuration) dans System Center Configuration Manager à être conformes.  

    Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** :  
  - **Non configuré** (*par défaut*) : ce paramètre n’est pas évalué pour la conformité ou la non-conformité.
  - **Exiger** : les utilisateurs doivent entrer un mot de passe pour pouvoir accéder à leur appareil. 

- **Mots de passe simples** :  
  - **Non configuré** (*par défaut*) : les utilisateurs peuvent créer des mots de passe simples, tels que **1234** ou **1111**.
  - **Bloquer** : les utilisateurs ne peuvent pas créer de mots de passe simples, comme **1234** ou **1111**.

- **Type de mot de passe** :  
  Choisissez le type de mot de passe ou de code PIN requis. Les options disponibles sont les suivantes :
  - **Valeur par défaut** de l’appareil (*par défaut*)-exiger un mot de passe, un code confidentiel numérique ou un code PIN alphanumérique
  - **Numérique** -exiger un mot de passe ou un code confidentiel numérique
  - **Alphanumérique** : exige un mot de passe ou un code PIN alphanumérique.  
  
  Lorsque la valeur est *alphanumérique*, les paramètres suivants sont disponibles :  
  - **Complexité du mot de passe** :  
    Les options disponibles sont les suivantes : 
    - **Exiger des chiffres et des lettres minuscules** (*par défaut*)
    - **Exiger des chiffres, des lettres minuscules et des lettres majuscules**
    - **Exiger des chiffres, des lettres minuscules, des lettres majuscules et des caractères spéciaux**

    > [!TIP]
    > Les stratégies de mot de passe alphanumériques peuvent être complexes. Nous encourageons les administrateurs à lire les CSP pour plus d’informations :
    >
    > - [CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [CSP DeviceLock/MinDevicePasswordComplexCharacters](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **Longueur minimale du mot de passe** :  
  entrez le nombre minimal de chiffres ou de caractères que doit comporter le mot de passe.

- **Durée d’inactivité maximale en minutes avant demande du mot de passe** :  
  entrez la durée d’inactivité au terme de laquelle l’utilisateur doit entrer à nouveau son mot de passe.

- **Expiration du mot de passe (en jours)** :  
  Entrez le nombre de jours, compris entre 1 et 730, avant que le mot de passe n’expire et que l’utilisateur ne doive en créer un autre.

- **Nombre de mots de passe précédents pour empêcher la réutilisation** :  
  Entrez le nombre de mots de passe précédemment utilisés qui ne peuvent pas être utilisés.

- **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité (Mobile et Holographic)**  :  
  - **Non configuré** (*par défaut*)
  - **Exiger** : forcer les utilisateurs à entrer le mot de passe chaque fois que l’appareil sort d’un état d’inactivité.

  > [!IMPORTANT]
  > Lorsque la configuration requise du mot de passe est modifiée sur un ordinateur de bureau Windows, les utilisateurs sont affectés lors de leur prochaine connexion, car c’est à ce moment-là que l’appareil passe d’inactif à actif. Les utilisateurs dont les mots de passe sont conformes à la configuration requise sont toujours invités à modifier leur mot de passe.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur un appareil** :  
  - **Non configuré** (*par défaut*)
  - **Exiger** : utilisez *Exiger* pour chiffrer le stockage de données sur vos appareils.

  > [!NOTE]
  > Le paramètre **Chiffrement du stockage de données sur l’appareil** vérifie de manière générique la présence du chiffrement sur l’appareil. Pour renforcer le chiffrement, utilisez l’option **Exiger BitLocker**, qui tire parti de l’Attestation d’intégrité de l’appareil Windows pour valider l’état de BitLocker au niveau du TPM.

### <a name="device-security"></a>Sécurité du périphérique  

- **Pare-feu** :  
  - **Non configuré** (*par défaut*) : Intune ne contrôle pas le pare-feu Microsoft Defender et ne modifie pas les paramètres existants.
  - **Exiger** : activez le pare-feu Microsoft Defender et empêchez les utilisateurs de le désactiver.  

  [CSP de pare-feu](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > Si l’appareil se synchronise immédiatement après un redémarrage ou synchronise immédiatement la sortie du mode veille, ce paramètre peut signaler une **erreur**. Ce scénario peut ne pas affecter l’état général de conformité de l’appareil. Pour réévaluer l’état de conformité, [synchronisez manuellement l’appareil](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

- **Module de plateforme sécurisée** :  
  - **Non configuré** (*par défaut*)-Intune ne vérifie pas la version de la puce TPM sur l’appareil.
  - **Require** -Intune vérifie la conformité de la version du processeur TPM. L’appareil est conforme si la version de la puce du module de plateforme sécurisée est supérieure à **0** (zéro). L’appareil n’est pas conforme s’il n’existe pas de version TPM sur l’appareil.  

  [DeviceStatus CSP-DeviceStatus/TPM/SpecificationVersion node](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **Antivirus** :  
  - **Non configuré** (*par défaut*) : Intune ne vérifie pas les solutions antivirus installées sur l’appareil. 
  - **Exiger** : vérifier la conformité en utilisant des solutions antivirus inscrites auprès du [Centre de sécurité Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), comme Symantec et Microsoft Defender.

- **Logiciel anti-espion** :  
  - **Non configuré** (*par défaut*) : Intune ne vérifie pas les solutions de logiciel anti-espion installées sur l’appareil.
  - **Exiger** : vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du [Centre de sécurité Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), comme Symantec et Microsoft Defender.  

### <a name="defender"></a>Defender

*Les paramètres de compatibilité suivants sont pris en charge avec Windows 10 Desktop.*

- **Logiciel anti-programme malveillant de Microsoft Defender**:  
  - **Non configuré** (*par défaut*) : Intune ne contrôle pas le service et ne modifie pas les paramètres existants.
  - **Exiger** : activez le service anti-programme malveillant de Microsoft Defender et empêchez les utilisateurs de le désactiver. 

- **Version minimale de Microsoft Defender anti-programme malveillant**:  
  Entrez la version minimale autorisée du service Microsoft Defender anti-malware. Par exemple, entrez `4.11.0.0`. Si ce champ n’est pas renseigné, vous pouvez utiliser n’importe quelle version du service anti-programme malveillant de Microsoft Defender.  

  *Par défaut, aucune version n’est configurée*.

- **Intelligence de sécurité anti-programme malveillant de Microsoft Defender à jour**:  
  Contrôle les mises à jour de la protection contre les virus et les menaces de sécurité Windows sur les appareils.  
  - **Non configuré** (*par défaut*)-Intune n’impose aucune exigence.
  - **Require** -force la mise à jour de l’intelligence de sécurité de Microsoft Defender. 

  Pour plus d’informations, consultez [mises à jour de sécurité pour l’antivirus Microsoft Defender et d’autres logiciels anti-programme malveillant de Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates).

- **Protection en temps réel** :  
  - **Non configuré** (*par défaut*) : Intune ne contrôle pas cette fonctionnalité et ne modifie pas les paramètres existants.
  - **Exiger** : activez la protection en temps réel, qui analyse les logiciels malveillants, les logiciels espions et autres logiciels indésirables.  

  [CSP Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Règles de Microsoft Defender Advanced Threat Protection

- **Exiger que l’appareil ait un score inférieur ou égal au score de risque machine** :  
  Utilisez ce paramètre pour prendre comme condition de conformité l’évaluation des risques effectuée par vos services de protection contre les menaces. Choisissez le niveau de menace maximal autorisé :
  - **Non configuré** (*par défaut*)  
  - **Sans risque** : cette option est la plus sécurisée, puisque l’appareil ne peut présenter aucune menace. Si des menaces d’un autre niveau sont détectées sur l’appareil, celui-ci est évalué comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sur celui-ci sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.
  
  Pour configurer Microsoft Defender ATP (Advanced Threat Protection) comme service de défense contre les menaces, consultez [Activer Microsoft Defender ATP avec l’accès conditionnel](advanced-threat-protection.md).


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business utilise la plateforme **Windows 10 et ultérieur**. Windows Holographic for Business prend en charge les paramètres suivants :

- **Sécurité du système** > **Chiffrement** > **Chiffrement du stockage de données sur l’appareil**.

Pour vérifier le chiffrement de l’appareil sur Microsoft HoloLens, consultez [Vérifier le chiffrement de l’appareil](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub utilise la plateforme **Windows 10 et ultérieur**. La conformité et l’accès conditionnel des appareils Surface Hub sont pris en charge. Pour activer ces fonctionnalités sur les appareils Surface Hub, nous vous recommandons d’[activer l’inscription automatique Windows 10](../enrollment/windows-enroll.md) dans Intune (nécessite Azure Active Directory) et de cibler les appareils Surface Hub en tant que groupes d’appareils. Les appareils Surface Hub doivent être joints à Azure AD pour que la conformité et l’accès conditionnel fonctionnent.

Pour obtenir de l’aide, consultez [Configurer l’inscription d’appareils Windows](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](../fundamentals/scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils Windows 8.1](compliance-policy-create-windows-8-1.md).
