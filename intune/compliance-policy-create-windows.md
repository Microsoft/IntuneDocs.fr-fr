---
title: Créer une stratégie de conformité de l’appareil Windows dans Microsoft Intune - Azure | Microsoft Docs
description: Créez ou configurez une stratégie de conformité des appareils Microsoft Intune pour Windows Phone 8.1, Windows 8.1 et versions ultérieures, ainsi que Windows 10 et versions ultérieures. Vérifiez la conformité des versions minimale et maximale du système d’exploitation, définissez des restrictions et des longueurs pour les mots de passe, imposez BitLocker, vérifiez les solutions antivirus tierces, définissez le niveau de menace acceptable et activez le chiffrement du stockage de données, notamment pour Surface Hub et Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e38e6f615220135e9c4c9c786ab260f5921890ea
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49642878"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Ajouter une stratégie de conformité des appareils pour les appareils Windows dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Une stratégie de conformité de l’appareil Intune pour Windows spécifie les règles et les paramètres que les appareils Windows doivent satisfaire pour être considérés comme conformes. Vous pouvez utiliser ces stratégies avec un accès conditionnel pour autoriser ou bloquer l’accès aux ressources de l’entreprise. Vous pouvez également obtenir des rapports sur les appareils et prendre des mesures en cas de non-conformité. Vous créez des stratégies de conformité de l’appareil pour chaque plateforme dans le portail Intune Azure. Pour en savoir plus sur les stratégies de conformité et sur les prérequis, consultez [Bien démarrer avec la conformité des appareils](device-compliance-get-started.md).

La table suivante décrit la façon dont les paramètres non conformes sont gérés quand une stratégie de conformité est utilisée avec une stratégie d’accès conditionnel.

---------------------------

| **Paramètre de stratégie** | **Windows 8.1 et versions ultérieures** | **Windows Phone 8.1 et versions ultérieures** |
|----| ----| --- |
| **Configuration d’un code confidentiel ou mot de passe** | Corrigé | Corrigé |   
| **Chiffrement de l’appareil** | Non applicable | Corrigé |   
| **Appareil jailbroken ou rooté** | Non applicable | Non applicable |  
| **Profil de messagerie** | Non applicable | Non applicable |   
| **Version minimale du système d’exploitation** | En quarantaine | En quarantaine |   
| **Version maximale du système d’exploitation** | En quarantaine | En quarantaine |   
| **Attestation de l’intégrité Windows** | En quarantaine : Windows 10 et Windows 10 Mobile|Non applicable : Windows 8.1 |

-------------------------------

**Corrigé** : le système d’exploitation de l’appareil applique la conformité. (Par exemple, l’utilisateur est obligé de définir un code confidentiel.)

**En quarantaine** : le système d’exploitation de l’appareil n’applique pas la conformité. (Par exemple, les appareils Android n’obligent pas l’utilisateur à chiffrer l’appareil.) Quand l’appareil n’est pas conforme, les actions suivantes se produisent :

- L’appareil est bloqué si une stratégie d’accès conditionnel s’applique à l’utilisateur.
- Le portail d’entreprise informe l’utilisateur des problèmes de conformité.

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Pour l’option **Plateforme**, sélectionnez **Windows Phone 8.1**, **Windows 8.1 et ultérieur** ou **Windows 10 et ultérieur**.
6. Choisissez **Paramètres Configurer**, puis entrez les paramètres nécessaires pour les options **Intégrité de l’appareil**, **Propriétés de l’appareil** et **Sécurité du système**. Une fois que vous avez fini, sélectionnez **OK**, puis **Créer**.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Paramètres de stratégie des appareils Windows 8.1

Ces paramètres de stratégie s’appliquent aux appareils qui exécutent les plateformes suivantes :

- Windows Phone 8.1
- Windows 8.1 et versions ultérieures

### <a name="device-properties"></a>Propriétés des appareils

- **Système d’exploitation minimal requis** : quand un appareil ne répond pas aux exigences minimales relatives à la version du système d’exploitation, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil pour pouvoir accéder aux ressources de l’entreprise.
- **Version maximale autorisée du système d’exploitation** : quand un appareil utilise une version du système d’exploitation postérieure à la version spécifiée dans la règle, l’accès aux ressources de l’entreprise est bloqué. L’utilisateur est invité à contacter son administrateur informatique. Tant que la règle autorisant la version du système d’exploitation reste inchangée, cet appareil ne peut pas accéder aux ressources de l’entreprise.

Les PC Windows 8.1 retournent la version **3**. Si la règle de la version du système d’exploitation est définie sur Windows 8.1 pour Windows, l’appareil est signalé comme non conforme même si Windows 8.1 est installé dessus.

### <a name="system-security"></a>Sécurité système

#### <a name="password"></a>Mot de passe

- **Exiger un mot de passe pour déverrouiller les appareils mobiles** : permet d’**obliger** les utilisateurs à entrer un mot de passe pour pouvoir accéder à leur appareil.
- **Mots de passe simples** : choisissez **Bloquer** pour que les utilisateurs ne puissent pas créer de mots de passe simples, par exemple **1234** ou **1111**. Choisissez **Non configuré** pour permettre aux utilisateurs de créer des mots de passe tels que **1234** ou **1111**.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de chiffres ou de caractères du mot de passe.

  Pour les appareils Windows accessibles à l’aide d’un compte Microsoft, l’évaluation de la stratégie de conformité ne s’effectue pas correctement :
  - Si la longueur minimale du mot de passe est supérieure à huit caractères
  - Ou, si le nombre minimal de jeux de caractères est supérieur à deux

- **Type de mot de passe** : choisissez si un mot de passe doit comporter uniquement des caractères **numériques**, ou s’il doit comporter un mélange de chiffres et d’autres caractères (**alphanumériques**).
  
  - **Nombre de caractères non alphanumériques dans le mot de passe** : si **Type de mot de passe obligatoire** a la valeur **Alphanumérique**, ce paramètre spécifie le nombre minimal de jeux de caractères que le mot de passe doit contenir. Les quatre jeux de caractères sont :
    - Lettres minuscules
    - Lettres majuscules
    - Symboles
    - Nombres

    Si vous définissez un nombre plus élevé, l’utilisateur doit créer un mot de passe plus complexe. Pour les appareils qui exécutent Windows et qui sont utilisés avec un compte Microsoft, la stratégie de conformité n’est pas évaluée correctement si la longueur minimale du mot de passe a une valeur supérieure à huit caractères ou si le nombre minimum de jeux de caractères a une valeur supérieure à deux.

- **Nombre maximal de minutes d’inactivité avant demande du mot de passe** : entrez la durée d’inactivité après laquelle l’utilisateur doit rentrer son mot de passe.
- **Expiration du mot de passe (jours)**  : sélectionnez le nombre de jours avant l’expiration du mot de passe de l’utilisateur et l’obligation d’en créer un autre.
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre d’anciens mots de passe qui ne peuvent pas être réutilisés.

#### <a name="encryption"></a>Chiffrement

- **Exiger le chiffrement sur l’appareil mobile** : permet d’**imposer** le chiffrement de l’appareil pour la connexion aux ressources de stockage de données.

## <a name="windows-10-and-later-policy-settings"></a>Paramètres de stratégie pour Windows 10 et versions ultérieures

### <a name="device-health"></a>Intégrité des appareils

- **Exiger BitLocker** : quand BitLocker est activé, l’appareil peut protéger les données stockées sur le disque contre tout accès non autorisé au moment de la désactivation ou de la mise en veille prolongée du système. Le chiffrement de lecteur BitLocker Windows chiffre toutes les données stockées sur le volume hébergeant le système d’exploitation Windows. BitLocker utilise le module de plateforme sécurisée (TPM) pour protéger le système d’exploitation Windows et les données utilisateur. Il permet également de protéger l’ordinateur contre les tentatives de falsification, même si celui-ci est laissé sans surveillance, perdu ou volé. Si l’ordinateur est équipé d’un TPM compatible, BitLocker utilise celui-ci pour verrouiller les clés de chiffrement qui protègent les données. Par conséquent, les clés sont inaccessibles tant que le TPM n’a pas vérifié l’état de l’ordinateur.
- **Exiger l’activation du démarrage sécurisé sur l’appareil** : quand le démarrage sécurisé est activé, le système est obligé de démarrer dans un état approuvé basé sur les paramètres d’usine. En outre, lorsque le démarrage sécurisé est activé, les composants principaux utilisés pour démarrer la machine doivent avoir des signatures de chiffrement appropriées, approuvées par le fabricant de l’appareil. Le microprogramme UEFI vérifie la signature avant de laisser la machine démarrer. Si des fichiers ont été falsifiés, avec pour effet d’annuler leur signature, le système ne démarre pas.

  > [!NOTE]
  > Le paramètre **Exiger l’activation du démarrage sécurisé sur l’appareil** est pris en charge sur les appareils TPM 1.2 et 2.0. Pour les appareils qui ne prennent pas en charge TPM 2.0 ou une version ultérieure, l’état de la stratégie dans Intune s’affiche sous la forme **Non conforme**. Il s’agit d’une limitation du service [Attestation d’intégrité de l’appareil](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation) dans Windows 10.

- **Exiger l’intégrité du code** : l’intégrité du code est une fonctionnalité qui valide l’intégrité d’un fichier de pilote ou d’un fichier système, chaque fois qu’il est chargé en mémoire. L’intégrité du code détecte si un fichier système ou un pilote non signé est chargé dans le noyau. Cette fonctionnalité détecte également si un fichier système a été modifié par un logiciel malveillant exécuté par un compte d’utilisateur ayant des privilèges d’administrateur.

Pour plus d’informations sur le fonctionnement du service HAS, consultez [Health Attestation CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp).

### <a name="device-properties"></a>Propriétés des appareils

- **Version minimale du système d’exploitation** : entrez la version minimale autorisée, au format numérique **major.minor.build.CU**. Pour obtenir la valeur correcte, ouvrez une invite de commandes, puis tapez `ver`. La commande `ver` retourne la version au format suivant :

  `Microsoft Windows [Version 10.0.17134.1]`

  Si un appareil a une version antérieure à la version de système d’exploitation spécifiée, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil, après quoi il pourra accéder aux ressources de l’entreprise.

- **Version maximale du système d’exploitation** : entrez la valeur maximale autorisée, au format numérique **major.minor.build.revision**. Pour obtenir la valeur correcte, ouvrez une invite de commandes, puis tapez `ver`. La commande `ver` retourne la version au format suivant :

  `Microsoft Windows [Version 10.0.17134.1]`

  Quand un appareil utilise une version du système d’exploitation ultérieure à celle spécifiée dans la règle, accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur. Jusqu’à ce qu’il y ait une modification de la règle pour autoriser la version du système d’exploitation, cet appareil ne peut pas être utilisé pour accéder aux ressources de l’entreprise.

- **Version minimale du système d’exploitation pour les appareils mobiles** : entrez la version minimale autorisée au format numérique major.minor.build.

  Si un appareil a une version antérieure à la version de système d’exploitation spécifiée, il est signalé comme non conforme. Un lien avec des informations sur la mise à niveau s’affiche. L’utilisateur final peut choisir de mettre à niveau son appareil, après quoi il pourra accéder aux ressources de l’entreprise.

- **Version maximale du système d’exploitation pour les appareils mobiles** : entrez la version maximale autorisée au format numérique major.minor.build.

  Quand un appareil utilise une version du système d’exploitation ultérieure à celle spécifiée dans la règle, accès aux ressources de l’entreprise est bloqué et l’utilisateur est invité à contacter son administrateur. Jusqu’à ce qu’il y ait une modification de la règle pour autoriser la version du système d’exploitation, cet appareil ne peut pas être utilisé pour accéder aux ressources de l’entreprise.

- **Builds de système d’exploitation valides** : entrez une plage pour les versions de systèmes d’exploitation acceptables, notamment une valeur minimale et maximale. Vous pouvez également **exporter** une liste de fichiers de valeurs au format CSV de ces numéros de build de système d’exploitation acceptables.

### <a name="system-security-settings"></a>Paramètres de sécurité système

#### <a name="password"></a>Mot de passe

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
- **Nombre de mots de passe précédents avant d’autoriser leur réutilisation** : entrez le nombre d’anciens mots de passe qui ne peuvent pas être réutilisés.
- **Exiger un mot de passe quand l’appareil sort d’un état d’inactivité (Mobile et Holographic)**  : permet de forcer les utilisateurs à entrer le mot de passe chaque fois que l’appareil sort d’un état d’inactivité.

#### <a name="encryption"></a>Chiffrement

- **Chiffrement du stockage de données sur l’appareil** : choisissez **Exiger** pour chiffrer le stockage des données sur vos appareils.

#### <a name="device-security"></a>Sécurité du périphérique

- **Antivirus** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions antivirus inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. Quand la valeur est **Non configuré**, Intune ne vérifie pas les solutions antivirus installées sur l’appareil.
- **Logiciel anti-espion** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du Centre de sécurité Windows, comme Symantec et Windows Defender. Quand la valeur est **Non configuré**, Intune ne vérifie pas les solutions de logiciel anti-espion installées sur l’appareil.

### <a name="windows-defender-atp"></a>Windows Defender ATP

- **Exiger que l’appareil se situe au niveau du score de risque machine ou en dessous** : utilisez ce paramètre pour considérer l’évaluation des risques de vos services Threat Defense comme une condition de conformité. Choisissez le niveau de menace maximal autorisé :
  - **Sans risque** : cette option est la plus sécurisée, puisque l’appareil ne peut présenter aucune menace. Si des menaces d’un autre niveau sont détectées sur l’appareil, celui-ci est évalué comme non conforme.
  - **Faible** : l’appareil est évalué comme conforme uniquement si les menaces détectées sont de niveau faible. La présence de menaces de niveau supérieur rend l’appareil non conforme.
  - **Moyen** : l’appareil est jugé conforme si les menaces présentes sur celui-ci sont de niveau faible ou moyen. La présence de menaces de niveau élevé rend l’appareil non conforme.
  - **Élevé** : cette option est la moins sécurisée, elle autorise tous les niveaux de menace. Elle peut s’avérer utile si vous utilisez cette solution uniquement à des fins de création de rapports.
  
  Pour configurer Windows Defender ATP (Advanced Threat Protection) comme service de défense contre les menaces, consultez [Activer Windows Defender ATP avec l’accès conditionnel](advanced-threat-protection.md).

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business utilise la plateforme **Windows 10 et ultérieur**. Windows Holographic for Business prend en charge les paramètres suivants :

- **Sécurité du système** > **Chiffrement** > **Chiffrement du stockage de données sur l’appareil**.

Pour vérifier le chiffrement de l’appareil sur Microsoft HoloLens, consultez [Vérifier le chiffrement de l’appareil](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption).

## <a name="surface-hub"></a>Surface Hub
Surface Hub utilise la plateforme **Windows 10 et ultérieur**. La conformité et l’accès conditionnel des appareils Surface Hub sont pris en charge. Pour activer ces fonctionnalités sur les appareils Surface Hub, nous vous recommandons d’[activer l’inscription automatique Windows 10](windows-enroll.md) dans Intune (nécessite également AAD (Azure Active Directory)) et de cibler les appareils Surface Hub en tant que groupes d’appareils. Les appareils Surface Hub doivent être joints à Azure Active Directory pour permettre la prise en charge de la conformité et de l’accès conditionnel.

Pour obtenir de l’aide, consultez [Configurer l’inscription d’appareils Windows](windows-enroll.md).

## <a name="assign-user-or-device-groups"></a>Affecter des groupes d’utilisateurs ou d’appareils

1. Choisissez une stratégie que vous avez configurée. Les stratégies existantes se trouvent dans **Conformité de l’appareil** > **Stratégies**.
2. Choisissez la stratégie, puis **Affectations**. Vous pouvez inclure ou exclure des groupes de sécurité Azure AD.
3. Choisissez **Groupes sélectionnés** pour voir vos groupes de sécurité Azure AD. Sélectionnez les groupes d’utilisateurs ou d’appareils auxquels vous souhaitez appliquer cette stratégie, puis choisissez **Enregistrer** pour déployer la stratégie.

Vous avez appliqué la stratégie. La conformité des appareils utilisés par les utilisateurs ciblés par la stratégie est évaluée.

## <a name="next-steps"></a>Étapes suivantes
[Automatiser l’envoi d’un e-mail et ajouter des actions pour les appareils non conformes](actions-for-noncompliance.md)  
[Surveiller les stratégies de conformité d’appareils Intune](compliance-policy-monitor.md)
