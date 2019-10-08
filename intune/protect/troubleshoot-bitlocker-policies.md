---
title: Conseils de dépannage pour les stratégies BitLocker dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Décrit comment activer le chiffrement BitLocker sur un appareil à l’aide de la stratégie Intune et comment vérifier que votre stratégie a été déployée avec succès sur un appareil.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 197ad888dc8a07cc35efbaec538fde93c76c81c3
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817623"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Résoudre les problèmes des stratégies BitLocker dans Microsoft Intune

Cet article peut aider les administrateurs Intune à comprendre comment les appareils Windows 10 configurent BitLocker sur la base de la stratégie Intune. Cet article fournit également des conseils sur la façon de résoudre les problèmes liés aux paramètres BitLocker sur les appareils que vous gérez avec Intune.  

## <a name="understanding-bitlocker"></a>Fonctionnement de BitLocker

Le chiffrement de lecteur BitLocker est un service proposé par les systèmes d’exploitation Microsoft Windows qui permet aux utilisateurs de chiffrer des données sur leurs disques durs. BitLocker prend en charge le chiffrement pour les lecteurs de système d’exploitation, les lecteurs de médias amovibles et les lecteurs de données fixes. BitLocker prend également en charge l’utilisation du chiffrement 256 bits pour une meilleure protection des données sensibles.  

Avec Microsoft Intune, vous disposez des méthodes suivantes pour gérer BitLocker sur les appareils Windows 10 :

- **Stratégies de configuration des appareils** : certaines options de stratégie intégrées sont disponibles dans la console d’administration Intune, à la configuration de l' **appareil** > **Endpoint Protection** > **stratégie de chiffrement Windows**. Vous trouverez tous les commutateurs et fonctionnalités disponibles ici : [chiffrement Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Lignes de base de sécurité** -  les[lignes de base de sécurité](security-baselines.md) sont des groupes connus de paramètres et de valeurs par défaut qui sont recommandés par l’équipe de sécurité appropriée pour sécuriser les appareils Windows. Différentes sources de référence, telles que la ligne de base de *sécurité MDM* ou la *ligne de base de Microsoft Defender ATP* , peuvent gérer les mêmes paramètres que les paramètres les uns avec les autres. Ils peuvent également gérer les mêmes paramètres que ceux que vous gérez avec les stratégies de configuration des appareils. 

En plus d’Intune, il est possible que les paramètres BitLocker soient gérés par d’autres moyens comme stratégie de groupe ou définis manuellement par un utilisateur de l’appareil.

Quelle que soit la façon dont les paramètres sont appliqués à un appareil, les stratégies BitLocker utilisent le [CSP BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) pour configurer le chiffrement sur l’appareil. Le CSP BitLocker est intégré à Windows et lorsqu’Intune déploie une stratégie BitLocker sur un appareil attribué, il s’agit du CSP BitLocker sur l’appareil qui écrit les valeurs appropriées dans le Registre Windows afin que les paramètres de la stratégie puissent prendre effet.

Si vous souhaitez en savoir plus sur BitLocker, consultez les ressources ci-dessous.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Présentation de BitLocker et FAQ sur la configuration requise](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Maintenant que vous avez une compréhension générale de ce que font ces stratégies et de leur fonctionnement, regardez comment vous pouvez vérifier si les paramètres BitLocker s’appliquent correctement à un client Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Vérifier la source des paramètres BitLocker

Lorsque vous examinez un problème BitLocker sur un appareil Windows 10, il est important de déterminer d’abord si le problème est lié à Intune ou à Windows. Une fois la source de défaillance probable connue, vous pouvez concentrer vos efforts de dépannage au bon endroit et, si nécessaire, prendre en charge l’équipe appropriée.  

Dans un premier temps, déterminez si la stratégie Intune a été déployée avec succès sur l’appareil cible. Dans l’exemple suivant, vous disposez d’une stratégie de configuration d’appareil qui déploie les paramètres de chiffrement Windows (BitLocker), comme indiqué ci-dessous : 

![Stratégie de configuration des appareils de chiffrement Windows avec les paramètres](./media/troubleshooting-bitlocker-policies/settings.png)

Comment vérifier que les paramètres ont été appliqués à l’appareil ciblé ? Voici quelques façons de procéder.

### <a name="device-configuration-policy-device-status"></a>État du périphérique de stratégie de configuration d’appareil  

Lorsque vous utilisez la stratégie de configuration d’appareil pour configurer BitLocker, vous pouvez vérifier l’état de la stratégie dans le portail Intune. Dans le portail, accédez à **configuration**de l’appareil  > **profils** > sélectionnez le profil contenant les paramètres BitLocker, puis sélectionnez état de l' **appareil**. Les appareils attribués au profil sont répertoriés, et la colonne État de l' *appareil* indique si un appareil a réussi à déployer le profil. 

N’oubliez pas qu’il peut y avoir un délai entre un appareil recevant une stratégie BitLocker et le lecteur entièrement chiffré.  

 
### <a name="use-control-panel-on-the-client"></a>Utiliser le panneau de configuration sur le client  

Sur un appareil qui a activé BitLocker et chiffré un lecteur, vous pouvez afficher l’état de BitLocker à partir d’un panneau de configuration des appareils. Sur l’appareil, ouvrez le **panneau de configuration** > **système et sécurité** > **chiffrement de lecteur BitLocker**. La confirmation s’affiche comme indiqué dans l’image suivante.  

![BitLocker est activé dans le panneau de configuration](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Utiliser une invite de commandes  

Sur un appareil qui a activé BitLocker et chiffré un lecteur, lancez l’invite de commandes avec les informations d’identification d’administrateur, puis exécutez `manage-bde -status`. Les résultats doivent ressembler à l’exemple suivant :  
![A résultat de la commande status](./media/troubleshooting-bitlocker-policies/command.png)

Dans l’exemple : 
- La **protection BitLocker** est **activée**,  
- Le **pourcentage chiffré** est de **100%**  
- La **méthode de chiffrement** est **XTS-AES 256**.  

Vous pouvez également vérifier les **protecteurs de clés** en exécutant la commande suivante :

```cmd
Manage-bde -protectors -get c:
```

Ou avec PowerShell :

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Examiner la configuration de la clé de Registre Devices   

Une fois que la stratégie BitLocker a été correctement déployée sur un appareil, affichez la clé de Registre suivante sur le périphérique dans lequel vous pouvez vérifier la configuration des paramètres BitLocker : *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker* . Voici un exemple :

![Clé de Registre BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Ces valeurs sont configurées par le fournisseur de services de chiffrement BitLocker. Vérifiez que les valeurs des clés correspondent aux paramètres spécifiés dans la source de votre stratégie de chiffrement Windows Intune. Pour plus d’informations sur chacun de ces paramètres, consultez [fournisseur CSP BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> Le observateur d’événements Windows contient également diverses informations relatives à BitLocker. Il y a trop d’informations à répertorier ici, mais la recherche de l' **API BitLocker** vous fournira de nombreuses informations utiles.

### <a name="check-the-mdm-diagnostics-report"></a>Vérifier le rapport de diagnostics MDM  

Sur un appareil sur lequel BitLocker est activé, vous pouvez générer et afficher un rapport de diagnostic MDM à partir de l’appareil ciblé pour confirmer la présence de la stratégie BitLocker. Si vous pouvez voir les paramètres de stratégie dans le rapport, il s’agit d’une autre indication que la stratégie a été déployée avec succès. *Microsoft vous aide* à accéder à la vidéo à l’adresse suivante : explique comment capturer un rapport de diagnostic MDM à partir d’un appareil Windows. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Lorsque vous analysez le rapport de diagnostics MDM, le contenu peut paraître un peu confus au préalable. Voici un exemple qui montre comment mettre en corrélation ce qui se trouve dans le rapport avec les paramètres d’une stratégie :

![Exemple de rapport de diagnostics MDM](./media/troubleshooting-bitlocker-policies/report.png)

Le résultat de la sortie affiche les valeurs qui correspondent aux valeurs de votre stratégie BitLocker :

![Résultat de la sortie affiche les valeurs ](./media/troubleshooting-bitlocker-policies/output.png)

Résultats de la sortie des diagnostics MDM :

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Vous pouvez référencer la [documentation du CSP BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) pour voir ce que signifie chaque valeur. Pour cet exemple, un extrait de code est partagé dans l’image suivante.

![Objectifs des valeurs](./media/troubleshooting-bitlocker-policies/shared-example.png)

 De même, vous pouvez voir toutes les valeurs et les vérifier à partir du lien BitLocker CSP.

> [!TIP]
> L’objectif principal du rapport de diagnostic MDM est d’aider Support Microsoft lors de la résolution des problèmes. Si vous ouvrez un dossier de support pour Intune et que le problème concerne les clients Windows, il est toujours judicieux de recueillir ce rapport et de l’inclure dans votre demande de support.

## <a name="troubleshooting-bitlocker-policy"></a>Résolution des problèmes de stratégie BitLocker

Vous devez maintenant avoir une bonne idée de vérifier que la stratégie BitLocker a été correctement déployée par Intune, ce qui permet de configurer BitLocker sur le CSP BitLocker dans WIndows.  

**La stratégie ne parvient pas à atteindre l’appareil** -quand votre stratégie Intune n’est pas présente dans une capacité :  
- **L’appareil est-il correctement inscrit dans Microsoft Intune ?** Si ce n’est pas le cas, vous devez résoudre ce problème avant de résoudre les problèmes spécifiques à la stratégie. Vous trouverez de l’aide pour le dépannage des problèmes d’inscription Windows [ici](../enrollment/troubleshoot-windows-enrollment-errors.md).  
- **Existe-t-il une connexion réseau active sur l’appareil ?** Si l’appareil est en mode avion ou s’il est éteint, ou si l’utilisateur dispose de l’appareil dans un emplacement sans service, la stratégie n’est pas remise ou s’applique tant que la connectivité réseau n’est pas restaurée.  
- **La stratégie BitLocker a-t-elle été déployée sur le groupe d’utilisateurs ou d’appareils approprié ?** Vérifiez que l’utilisateur ou le périphérique approprié est membre des groupes que vous ciblez.  

La **stratégie est présente, mais tous les paramètres ne sont pas configurés correctement** : lorsque votre stratégie Intune atteint l’appareil, mais que toutes les configurations ne sont pas définies :  
- **Le déploiement de l’ensemble de la stratégie échoue-t-il uniquement certains paramètres qui ne s’appliquent pas ?** Si vous êtes confronté à un scénario dans lequel seuls certains paramètres de stratégie ne s’appliquent pas, vérifiez les points suivants :

  1. Tous les **paramètres BitLocker ne sont pas pris en charge sur toutes les versions de Windows**.  
  La stratégie passe à un appareil en tant qu’unité unique. par conséquent, si certains paramètres s’appliquent et que d’autres ne le sont pas, vous pouvez être certain que la stratégie elle-même est reçue. Dans ce scénario, il est possible que la version de Windows sur l’appareil ne prenne pas en charge les paramètres problématiques. Pour plus d’informations sur la configuration requise pour chaque paramètre, consultez [CSP BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) dans la documentation de Windows.  

  1. **BitLocker n’est pas pris en charge sur tout le matériel**.  
  Même si vous disposez de la bonne version de Windows, il est possible que le matériel du périphérique sous-jacent ne réponde pas aux conditions requises pour le chiffrement BitLocker. Vous trouverez la [Configuration système requise pour BitLocker (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) dans la documentation Windows, mais les principaux éléments à vérifier sont que l’appareil dispose d’une puce TPM compatible (1,2 ou version ultérieure) et d’un microprogramme BIOS ou UEFI compatible Trusted Computing Group (TCG).

**Exemple d’investigation** : vous déployez une stratégie BitLocker sur un appareil Windows 10, et le paramètre **chiffrer les appareils** affiche l’état **erreur** dans le portail.

- Comme son nom l’indique, ce paramètre permet à un administrateur d’exiger que le chiffrement soit activé à l’aide de *BitLocker > le chiffrement*de l’appareil. À l’aide des conseils de dépannage mentionnés précédemment, commencez par vérifier le rapport de diagnostics MDM. Le rapport confirme que la stratégie correcte a été déployée sur l’appareil :

  ![Le rapport confirme que la stratégie correcte est déployée sur l’appareil](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Vous pouvez également vérifier la réussite dans le registre :

  ![La valeur de Registre RequiredDeviceEncryption affiche 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Ensuite, vérifiez l’état du module de plateforme sécurisée à l’aide de PowerShell et vérifiez que le module de plateforme sécurisée n’est pas disponible sur l’appareil :

  ![Vérification de l’état du module de plateforme sécurisée avec PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Étant donné que BitLocker s’appuie sur TPM, vous pouvez conclure que BitLocker n’échoue pas en raison d’un problème avec Intune ou la stratégie, mais plutôt parce que l’appareil lui-même n’a pas de puce TPM ou TPM est désactivé dans le BIOS.

  En guise d’astuce supplémentaire, vous pouvez vérifier les mêmes informations dans le observateur d’événements Windows sous **journaux des applications et des Services** > **Windows** > **API BitLocker**. Dans le journal des événements de l' **API BitLocker** , vous trouverez un ID d’événement 853 qui signifie que le module de plateforme sécurisée n’est pas disponible :

  ![ID d’événement 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Vous pouvez également vérifier l’état du module de plateforme sécurisée en exécutant **TPM. msc** sur l’appareil.



## <a name="summary"></a>Résumé

Lorsque vous résolvez les problèmes de stratégie BitLocker avec Intune et que vous pouvez vérifier que la stratégie atteint l’appareil prévu, il est possible de supposer que le problème n’est pas directement lié à Intune. Le problème est probablement lié à un problème avec le système d’exploitation Windows ou le matériel. Dans ce cas, commencez à regarder dans d’autres domaines tels que la configuration du module de plateforme sécurisée ou UEFI et le démarrage sécurisé).

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>Étapes suivantes  

Voici d’autres ressources qui peuvent vous aider lors de l’utilisation de BitLocker :

- [Documentation produit BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Configuration système requise pour BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Questions fréquentes sur BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentation du CSP BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Paramètres de la stratégie de chiffrement Windows Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Chiffrement BitLocker automatique indépendant du matériel à l’aide d’AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Stratégie CSP pour le chiffrement BitLocker sur les périphériques auto-pilotés](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Procédure pas à pas création et déploiement d’une stratégie BitLocker avec Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)