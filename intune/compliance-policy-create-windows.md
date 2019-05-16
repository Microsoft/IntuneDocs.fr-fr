---
title: Paramètres de conformité de Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Découvrez la liste de tous les paramètres que vous pouvez utiliser quand vous configurez la conformité de vos appareils Windows 10, Windows Holographic et Surface Hub dans Microsoft Intune. Vérifiez la conformité sur le système d’exploitation minimal et maximal, définissez des restrictions et une longueur de mot de passe, recherchez les solutions anti-virus de partenaires, activez le chiffrement sur le stockage de données, etc.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d956526d483a74ca5929180a48ea2dcd8b3eab7
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423626"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Paramètres Windows de 10 et ultérieur pour marquer les appareils comme étant conformes ou non conformes avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres de conformité que vous pouvez configurer sur les appareils Windows 10 et ultérieur dans Intune. Dans le cadre de votre solution MDM, utilisez ces paramètres pour exiger BitLocker, définir un système d’exploitation minimal et maximal, définir un niveau de risque avec Windows Defender Advanced Threat Protection (ATP), etc.

Cette fonctionnalité s’applique à :

- Windows 10 et versions ultérieures
- Windows Holographic for Business
- Surface Hub

En tant qu’administrateur Intune, utilisez ces paramètres de conformité pour protéger les ressources de votre organisation. Pour plus d’informations sur les stratégies de conformité et ce qu’elles permettent de faire, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créer une stratégie de conformité](create-compliance-policy.md#create-the-policy). Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.

## <a name="device-health"></a>Device health

- **Exiger BitLocker** : quand la valeur est **Exiger**, l’appareil peut protéger les données stockées sur le lecteur contre tout accès non autorisé quand le système est à l’arrêt ou en veille prolongée. Le Chiffrement de lecteur BitLocker Windows chiffre toutes les données stockées sur le volume de système d’exploitation Windows. BitLocker utilise le module de plateforme sécurisée (TPM) pour protéger le système d’exploitation Windows et les données utilisateur. Il contribue également à prévenir la falsification d’un ordinateur, même si celui-ci est laissé sans assistance, perdu ou volé. Si l’ordinateur est équipé d’un module de plateforme sécurisée compatible, BitLocker utilise ce module pour verrouiller les clés de chiffrement qui protègent les données. Par conséquent, les clés sont inaccessibles tant que le TPM n’a pas vérifié l’état de l’ordinateur.

  Quand vous définissez la valeur **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

- **Exiger l’activation du démarrage sécurisé sur l’appareil** : quand la valeur est **Exiger**, le système est obligé de démarrer dans un état approuvé basé sur les paramètres d’usine. Quand ce paramètre est activé, les principaux composants utilisés pour démarrer la machine doivent avoir des signatures de chiffrement appropriées qui sont approuvées par l’organisation ayant fabriqué l’appareil. Le microprogramme UEFI vérifie la signature avant de laisser la machine démarrer. Si tous les fichiers sont falsifiés, ce qui interrompt leur signature, le système ne démarre pas.

  Quand vous définissez la valeur **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

  > [!NOTE]
  > Le paramètre **Exiger l’activation du démarrage sécurisé sur l’appareil** est pris en charge sur les appareils TPM 1.2 et 2.0. Pour les appareils qui ne prennent pas en charge TPM 2.0 ou une version ultérieure, l’état de la stratégie dans Intune s’affiche sous la forme **Non conforme**. Pour plus d’informations sur les versions prises en charge, consultez [Attestation d’intégrité de l’appareil](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation).

- **Exiger l’intégrité du code** : l’intégrité du code est une fonctionnalité qui valide l’intégrité d’un fichier de pilote ou d’un fichier système, chaque fois qu’il est chargé en mémoire. Quand ce paramètre est défini sur **Exiger**, l’intégrité du code détecte si un fichier système ou un pilote non signé est chargé dans le noyau. Cette fonctionnalité détecte également si un fichier système a été modifié par un logiciel malveillant exécuté par un compte d’utilisateur ayant des privilèges d’administrateur.

  Quand vous définissez la valeur **Non configuré** (par défaut), ce paramètre n’est pas évalué pour la conformité ou la non-conformité.

Autres ressources :

- La section [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp) détaille le fonctionnement du service HAS.
- [Support Tip: Using Device Health Attestation Settings as Part of Your Intune Compliance Policy ](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>Propriétés des appareils

- **Version minimale du système d’exploitation** : entrez la version minimale autorisée, au format numérique **major.minor.build.CU**. Pour obtenir la valeur correcte, ouvrez une invite de commandes, puis tapez `ver`. La commande `ver` retourne la version au format suivant :

  `Microsoft Windows [Version 10.0.17134.1]`

  Quand un appareil a une version antérieure à la version du système d’exploitation que vous entrez, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil. Une fois la mise à niveau effectuée, il peut accéder aux ressources de l’entreprise.

- **Version maximale du système d’exploitation** : entrez la valeur maximale autorisée, au format numérique **major.minor.build.revision**. Pour obtenir la valeur correcte, ouvrez une invite de commandes, puis tapez `ver`. La commande `ver` retourne la version au format suivant :

  `Microsoft Windows [Version 10.0.17134.1]`

  Quand un appareil utilise une version du système d’exploitation postérieure à la version entrée, l’accès aux ressources de l’organisation est bloqué. L’utilisateur final est invité à contacter son administrateur informatique. Cet appareil ne peut pas accéder aux ressources de l’organisation tant que la règle autorisant la version du système d’exploitation reste inchangée.

- **Version minimale du système d’exploitation pour les appareils mobiles** : entrez la version minimale autorisée au format numérique major.minor.build.

  Quand un appareil a une version antérieure à la version du système d’exploitation que vous entrez, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil. Une fois la mise à niveau effectuée, il peut accéder aux ressources de l’entreprise.

- **Version maximale du système d’exploitation pour les appareils mobiles** : entrez la version maximale autorisée au format numérique major.minor.build.

  Quand un appareil utilise une version du système d’exploitation postérieure à la version entrée, l’accès aux ressources de l’organisation est bloqué. L’utilisateur final est invité à contacter son administrateur informatique. Cet appareil ne peut pas accéder aux ressources de l’organisation tant que la règle autorisant la version du système d’exploitation reste inchangée.

- **Builds de système d’exploitation valides** : entrez une plage pour les versions de systèmes d’exploitation acceptables, notamment une valeur minimale et maximale. Vous pouvez également **exporter** une liste de fichiers de valeurs au format CSV de ces numéros de build de système d’exploitation acceptables.

## <a name="configuration-manager-compliance"></a>Conformité de Configuration Manager

S’applique uniquement aux appareils cogérés exécutant Windows 10 et versions ultérieures. Les appareils Intune uniquement retournent un état non disponible.

- **Exiger la conformité des appareils dans System Center Configuration Manager** : choisissez **Exiger** pour obliger tous les paramètres (éléments de configuration) dans System Center Configuration Manager à être conformes. 

  Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans Configuration Manager, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.
  
  Lorsque l’état est **Non configuré**, Intune ne vérifie la conformité d’aucun paramètre de Configuration Manager.

## <a name="system-security"></a>Sécurité système

### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil.
- **Mots de passe simples** : choisissez **Bloquer** pour que les utilisateurs ne puissent pas créer de mots de passe simples, par exemple **1234** ou **1111**. Choisissez **Non configuré** pour permettre aux utilisateurs de créer des mots de passe tels que **1234** ou **1111**.
- **Type de mot de passe** : choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumériques**).

  - **Nombre de caractères non alphanumériques dans le mot de passe** : si **Type de mot de passe obligatoire** a la valeur **Alphanumérique**, ce paramètre spécifie le nombre minimal de jeux de caractères que le mot de passe doit contenir. Les quatre jeux de caractères sont :
    - Lettres minuscules
    - Lettres majuscules
    - Symboles
    - Nombres

    Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe.

- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe.
- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et l’obligation d’en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre d’anciens mots de passe qui ne peuvent pas être réutilisés.
- **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité (Mobile et Holographic)**  : permet de forcer les utilisateurs à entrer le mot de passe chaque fois que l’appareil sort d’un état d’inactivité.

### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** : choisissez **Exiger** pour chiffrer le stockage des données sur vos appareils.

  > [!NOTE]
  > Le paramètre **Chiffrement du stockage de données sur l’appareil** vérifie de manière générique la présence du chiffrement sur l’appareil. Pour renforcer le chiffrement, utilisez l’option **Exiger BitLocker**, qui tire parti de l’Attestation d’intégrité de l’appareil Windows pour valider l’état de BitLocker au niveau du TPM.

### <a name="device-security"></a>Sécurité du périphérique

- **Antivirus** : lorsque la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions antivirus inscrites auprès du [Centre de sécurité Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), comme Symantec et Windows Defender. Quand la valeur est **Non configuré**, Intune ne vérifie pas les solutions antivirus installées sur l’appareil.
- **Logiciel anti-espion** : lorsque la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du [Centre de sécurité Windows](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/), comme Symantec et Windows Defender. Quand la valeur est **Non configuré**, Intune ne vérifie pas les solutions de logiciel anti-espion installées sur l’appareil.

## <a name="windows-defender-atp"></a>Windows Defender ATP

- **Exiger que l’appareil se situe au niveau du score de risque machine ou en dessous** : utilisez ce paramètre pour considérer l’évaluation des risques de vos services Threat Defense comme une condition de conformité. Choisissez le niveau de menace maximal autorisé :

  - **Sans risque** : cette option est la plus sécurisée, puisque l’appareil ne peut présenter aucune menace. Si des menaces d’un autre niveau sont détectées sur l’appareil, celui-ci est évalué comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sur celui-ci sont de niveau faible ou moyen. Si des menaces de niveau élevé sont détectées sur l’appareil, celui-ci est considéré comme non conforme.
  - **Élevé** : cette option est la moins sécurisée, elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.
  
  Pour configurer Windows Defender ATP (Advanced Threat Protection) comme service de défense contre les menaces, consultez [Activer Windows Defender ATP avec l’accès conditionnel](advanced-threat-protection.md).

Sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business utilise la plateforme **Windows 10 et ultérieur**. Windows Holographic for Business prend en charge les paramètres suivants :

- **Sécurité du système** > **Chiffrement** > **Chiffrement du stockage de données sur l’appareil**.

Pour vérifier le chiffrement de l’appareil sur Microsoft HoloLens, consultez [Vérifier le chiffrement de l’appareil](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub

Surface Hub utilise la plateforme **Windows 10 et ultérieur**. La conformité et l’accès conditionnel des appareils Surface Hub sont pris en charge. Pour activer ces fonctionnalités sur les appareils Surface Hub, nous vous recommandons d’[activer l’inscription automatique Windows 10](windows-enroll.md) dans Intune (nécessite Azure Active Directory) et de cibler les appareils Surface Hub en tant que groupes d’appareils. Les appareils Surface Hub doivent être joints à Azure AD pour que la conformité et l’accès conditionnel fonctionnent.

Pour obtenir de l’aide, consultez [Configurer l’inscription d’appareils Windows](windows-enroll.md).

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md) et [Utiliser des étiquettes d’étendue pour filtrer les stratégies](scope-tags.md).
- [Superviser vos stratégies de conformité](compliance-policy-monitor.md).
- Consultez [Paramètres de stratégie de conformité pour les appareils Windows 8.1](compliance-policy-create-windows-8-1.md).