---
title: Conseils de dépannage pour les stratégies BitLocker dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Explique comment activer le chiffrement BitLocker sur un appareil à l’aide d’une stratégie Intune et comment vérifier que la stratégie a bien été déployée sur l’appareil.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556497"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Résoudre les problèmes de stratégies BitLocker dans Microsoft Intune

Cet article peut aider les administrateurs Intune à comprendre de quelle manière les appareils Windows 10 configurent BitLocker sur la base d’une stratégie Intune. Il donne également des conseils sur la résolution des problèmes de configuration de BitLocker sur les appareils gérés avec Intune.  

## <a name="understanding-bitlocker"></a>Fonctionnement de BitLocker

Le chiffrement de lecteur BitLocker est un service disponible sur les systèmes d’exploitation Microsoft Windows qui permet aux utilisateurs de chiffrer les données stockées sur leurs disques durs. BitLocker prend en charge le chiffrement sur les lecteurs de système d’exploitation, les lecteurs de média amovible et les lecteurs de données fixes. BitLocker prend également en charge l’utilisation du chiffrement 256 bits pour renforcer la protection des données sensibles.  

Avec Microsoft Intune, vous disposez des méthodes suivantes pour gérer BitLocker sur les appareils Windows 10 :

- **Stratégies de configuration des appareils** : certaines options de stratégie intégrées sont proposées dans Intune quand vous créez un profil de configuration d’appareil pour gérer les paramètres Endpoint Protection. Pour utiliser ces options, [créez un profil d’appareil pour Endpoint Protection](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings), sélectionnez **Windows 10 et ultérieur** comme *Plateforme*, puis sélectionnez la catégorie **Chiffrement Windows** dans *Paramètres*. 

   Vous trouverez ici plus d’informations sur les options et fonctionnalités disponibles : [Chiffrement Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Bases de référence de sécurité** - Les [bases de référence de sécurité](security-baselines.md) représentent des groupes connus de paramètres et de valeurs par défaut qui sont recommandés par l’équipe de sécurité appropriée pour mieux sécuriser les appareils Windows. Différentes sources de référence, comme la *base de référence de la sécurité MDM* ou la *base de référence de Microsoft Defender ATP*, peuvent gérer les mêmes paramètres ainsi que des paramètres qui leur sont propres. Elles peuvent également gérer les mêmes paramètres que ceux que vous gérez à l’aide de stratégies de configuration des appareils. 

En plus d’Intune, pour le matériel compatible avec Modern Standby et HSTI, lorsque vous utilisez l’une de ces fonctionnalités, le chiffrement de l’appareil BitLocker est automatiquement activé chaque fois que l’utilisateur joint un appareil à Azure AD. Azure AD fournit un portail dans lequel les clés de récupération sont également sauvegardées, afin que les utilisateurs puissent récupérer leur propre clé de récupération en libre-service, si nécessaire.

Il est également possible que les paramètres BitLocker soient gérés par d’autres moyens comme une stratégie de groupe ou qu’ils soient définis manuellement par un utilisateur de l’appareil.

Quelle que soit la méthode utilisée pour appliquer les paramètres sur un appareil, les stratégies BitLocker ont toujours recours au [fournisseur de services de chiffrement BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) pour configurer le chiffrement sur l’appareil. Le fournisseur de services de chiffrement BitLocker est intégré à Windows. Quand Intune déploie une stratégie BitLocker sur un appareil attribué, c’est ce fournisseur de services de chiffrement sur l’appareil qui écrit les valeurs appropriées dans le Registre Windows afin que les paramètres de la stratégie soient ensuite appliqués.

Pour en savoir plus sur BitLocker, consultez les ressources suivantes :

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [FAQ sur le fonctionnement et la configuration requise de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Maintenant que vous savez globalement à quoi servent et comment fonctionnent ces stratégies, vous allez voir de quelle manière vous pouvez vérifier que les paramètres de BitLocker sont correctement appliqués sur un client Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Vérifier la source des paramètres de BitLocker

Lorsque vous examinez un problème avec BitLocker sur un appareil Windows 10, il est important de déterminer d’abord si le problème est lié à Intune ou à Windows. Une fois que vous avez identifié la source probable du problème, vous pouvez vous concentrer sur le point à résoudre et, si nécessaire, demander de l’aide à l’équipe appropriée.  

Dans un premier temps, vérifiez si la stratégie Intune a été correctement déployée sur l’appareil cible. L’exemple suivant montre une stratégie de configuration d’appareil qui déploie les paramètres de chiffrement Windows (BitLocker) comme ci-dessous :

![Stratégie de configuration d’appareil avec les paramètres de chiffrement Windows](./media/troubleshooting-bitlocker-policies/settings.png)

Comment vérifier que les paramètres ont bien été appliqués sur l’appareil ciblé ? Voici quelques façons de procéder.

### <a name="device-configuration-policy-device-status"></a>État de la stratégie de configuration de l’appareil  

Quand vous utilisez une stratégie de configuration d’appareil pour configurer BitLocker, vous pouvez vérifier l’état de la stratégie dans le portail Intune.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profils de configuration**, puis sélectionnez le profil contenant les paramètres de BitLocker.

3. Après avoir sélectionné le profil qui vous intéresse, sélectionnez **État des appareils**. Les appareils affectés au profil sont listés, et la colonne *État de l’appareil* indique si un appareil a bien déployé le profil.

N’oubliez pas qu’il peut y avoir un délai entre le déploiement d’une stratégie BitLocker sur un appareil et la fin complète du chiffrement du lecteur.  

### <a name="use-control-panel-on-the-client"></a>Utiliser le Panneau de configuration sur le client  

Sur un appareil où BitLocker est activé et où le lecteur est chiffré, vous pouvez voir l’état de BitLocker à partir d’un Panneau de configuration des appareils. Sur l’appareil, ouvrez **Panneau de configuration** > **Système et sécurité** > **Chiffrement de lecteur BitLocker**. La confirmation s’affiche comme dans l’image suivante.  

![BitLocker est activé dans le Panneau de configuration](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Utiliser une invite de commandes  

Sur un appareil où BitLocker est activé et où le lecteur est chiffré, lancez l’invite de commandes avec des informations d’identification d’administrateur, puis exécutez `manage-bde -status`. Les résultats doivent ressembler à l'exemple suivant :  
![A résultat de la commande status](./media/troubleshooting-bitlocker-policies/command.png)

Dans l'exemple :

- La **protection BitLocker** est **activée** (On)
- Le **pourcentage chiffré** est de **100 %**
- La **méthode de chiffrement** est **XTS-AES 256**

Vous pouvez également vérifier les **protecteurs de clés** en exécutant la commande suivante :

```cmd
Manage-bde -protectors -get c:
```

Ou avec PowerShell :

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Vérifier la configuration de la clé de Registre des appareils

Une fois que la stratégie BitLocker a été correctement déployée sur un appareil, affichez la clé de Registre suivante sur l’appareil, puis vérifiez la configuration des paramètres de BitLocker :  *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. Voici un exemple :

![Clé de Registre BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Ces valeurs sont configurées par le fournisseur de services de chiffrement BitLocker. Vérifiez que les valeurs des clés correspondent aux paramètres spécifiés dans la source de votre stratégie de chiffrement Windows dans Intune. Pour plus d’informations sur chacun de ces paramètres, consultez [Fournisseur de services de chiffrement BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> L’Observateur d’événements Windows fournit également diverses informations relatives à BitLocker. Ces informations sont trop nombreuses pour être décrites ici, mais une simple recherche dans l’**API BitLocker** vous permettra de trouver beaucoup d’informations utiles.

### <a name="check-the-mdm-diagnostics-report"></a>Consulter le rapport de diagnostics MDM

Sur un appareil sur lequel BitLocker est activé, vous pouvez générer et afficher un rapport de diagnostics MDM de l’appareil ciblé afin d’y vérifier la présence de la stratégie BitLocker. Si le rapport indique les paramètres de la stratégie, c’est une preuve supplémentaire que la stratégie a bien été déployée. La vidéo *Microsoft Helps* disponible à partir du lien suivant explique comment générer un rapport de diagnostics MDM à partir d’un appareil Windows.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Le contenu du rapport de diagnostics MDM à analyser vous paraîtra peut-être un peu confus au départ. Voici un exemple qui montre comment mettre en corrélation les éléments du rapport avec les paramètres d’une stratégie :

![Exemple de rapport de diagnostics MDM](./media/troubleshooting-bitlocker-policies/report.png)

Dans les résultats, vous voyez les valeurs qui correspondent aux valeurs de votre stratégie BitLocker :

![Résultats montrant les valeurs ](./media/troubleshooting-bitlocker-policies/output.png)

Résultats des diagnostics MDM :

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Vous pouvez vous reporter à la [documentation du fournisseur de services de chiffrement BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) pour connaître la signification de chaque valeur. À titre d’exemple, l’image suivante présente un extrait de code.

![Signification des valeurs](./media/troubleshooting-bitlocker-policies/shared-example.png)

Vous pouvez également consulter et vérifier toutes les valeurs à partir du lien du fournisseur de services de chiffrement BitLocker.

> [!TIP]
> Le rapport de diagnostics MDM est principalement destiné à aider le support Microsoft lors de la résolution des problèmes. Si vous ouvrez une demande de support pour Intune et que le problème concerne des clients Windows, il est conseillé de générer ce rapport et de le joindre à votre demande de support.

## <a name="troubleshooting-bitlocker-policy"></a>Résolution des problèmes avec la stratégie BitLocker

Vous devez maintenant savoir à peu près comment vérifier que la stratégie BitLocker a été correctement déployée par Intune, après quoi la configuration de BitLocker est prise en charge par le fournisseur de services de chiffrement dans Windows.

**La stratégie ne parvient pas jusqu’à l’appareil**. Si votre stratégie Intune n’est présente dans aucune capacité :

- **L’appareil est-il correctement inscrit à Microsoft Intune ?** Si ce n’est pas le cas, vous devez régler ce problème avant de tenter de résoudre des problèmes afférents à la stratégie. Vous trouverez [ici](../enrollment/troubleshoot-windows-enrollment-errors.md) de l’aide pour résoudre les problèmes d’inscription d’appareils Windows.

- **Une connexion réseau est-elle active sur l’appareil ?** Si l’appareil est en mode avion ou s’il est éteint, ou si l’utilisateur s’en sert hors connexion, la stratégie ne peut pas être déployée ni appliquée tant que la connectivité réseau n’est pas rétablie.

- **La stratégie BitLocker a-t-elle été déployée sur le groupe d’utilisateurs ou d’appareils approprié ?** Vérifiez que l’utilisateur ou l’appareil en question est membre des groupes que vous ciblez.

**La stratégie est déployée, mais les paramètres ne sont pas tous configurés correctement**. Si votre stratégie Intune est présente sur l’appareil, mais que les configurations ne sont pas toutes définies :

- **Est-ce la stratégie entière qui n’a pas été déployée ou est-ce uniquement certains paramètres qui n’ont pas été appliqués ?** Si vous êtes confronté à un scénario où seuls certains paramètres de la stratégie n’ont pas été appliqués, tenez compte des points suivants :

  1. **Les paramètres de BitLocker ne sont pas tous pris en charge sur toutes les versions de Windows**.
     La stratégie est déployée sur un appareil comme une seule unité. Par conséquent, même si certains paramètres sont appliqués et que d’autres ne le sont pas, vous pouvez considérer en toute sécurité que la stratégie elle-même a été déployée. Dans ce scénario, il est possible que la version de Windows sur l’appareil ne prenne pas en charge les paramètres problématiques. Pour plus d’informations sur la version requise pour chaque paramètre, consultez [Fournisseur de services de chiffrement BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) dans la documentation Windows.

  2. **BitLocker n’est pas pris en charge sur tous les types de matériel**.
     Même si vous disposez de la bonne version de Windows, il est possible que le matériel sous-jacent de l’appareil ne remplisse pas les conditions requises pour le chiffrement BitLocker. Vous trouverez la [configuration système requise pour BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) dans la documentation Windows, mais sachez que les points principaux à vérifier sont que l’appareil soit équipé d’une puce TPM compatible (version 1.2 ou ultérieure) et d’un microprogramme BIOS ou UEFI conforme aux normes TCG (Trusted Computing Group).
     
Le **chiffrement BitLocker n’est pas exécuté en mode silencieux** : vous avez configuré une stratégie Endpoint Protection avec le paramètre « Avertissement pour tout autre chiffrement de disque » défini sur Bloquer et l’Assistant de chiffrement s’affiche toujours :

- **Vérifiez que la version de Windows prend en charge le chiffrement silencieux** Cela nécessite au minimum la version 1803. Si l’utilisateur n’est pas un administrateur sur l’appareil, une version minimale 1809 est requise. La version 1809 ajoutée ne prend pas en charge la mise Modern Standby

L' **appareil chiffré avec BitLocker s’affiche comme non conforme pour les stratégies de conformité Intune** : le problème se produit lorsque le chiffrement BitLocker n’est pas terminé. En fonction de facteurs tels que la taille du disque, le nombre de fichiers et les paramètres BitLocker, le chiffrement BitLocker peut prendre beaucoup de temps. Une fois le chiffrement terminé, l’appareil s’affiche comme étant conforme. Les appareils peuvent également devenir temporairement non conformes immédiatement après une installation récente de mises à jour Windows.

**Les appareils sont chiffrés à l’aide d’un algorithme 128 bits alors que la stratégie spécifie 256 bits** : par défaut, Windows 10 chiffre un lecteur avec le chiffrement XTS-AES 128 bits. Consultez ce guide pour [définir le chiffrement 256 bits pour BitLocker pendant AutoPilot](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#).


**Exemple d’examen**

- Vous déployez une stratégie BitLocker sur un appareil Windows 10, mais le paramètre **Chiffrer les appareils** affiche l’état **Erreur** dans le portail.

- Comme son nom le laisse supposer, ce paramètre permet à un administrateur d’exiger l’activation du chiffrement par le biais de la fonctionnalité *BitLocker > Chiffrement d’appareil*. En vous aidant des conseils de dépannage donnés plus haut, vous commencez par examiner le rapport de diagnostics MDM. Le rapport confirme que la stratégie correcte a été déployée sur l’appareil :

  ![Rapport confirmant le déploiement de la stratégie correcte sur l’appareil](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Vous vérifiez également le déploiement dans le Registre :

  ![La valeur de Registre RequiredDeviceEncryption est 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Ensuite, vous vérifiez l’état du module de plateforme sécurisée (TPM) à l’aide de PowerShell et vous constatez que le module n’est pas disponible sur l’appareil :

  ![Vérification de l’état du module TPM avec PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Étant donné que BitLocker repose sur le module TPM, vous pouvez en conclure que BitLocker n’échoue pas en raison d’un problème avec Intune ou avec la stratégie, mais plutôt parce que l’appareil ne comporte pas de puce TPM ou que TPM est désactivé dans le BIOS.

  Autre conseil : vous pouvez vérifier les mêmes informations dans l’Observateur d’événements Windows sous **Journaux des applications et services** > **Microsoft** > **Windows** > **API BitLocker**. Dans le journal des événements de l’**API BitLocker**, vous trouverez un ID d’événement 853 qui signifie que le module TPM n’est pas disponible :

  ![ID d’événement 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Vous pouvez également vérifier l’état du module TPM en exécutant **tpm.msc** sur l’appareil.

## <a name="summary"></a>Résumé

Quand vous essayez de résoudre des problèmes liés à une stratégie BitLocker avec Intune et que vous avez la preuve que la stratégie est bien déployée sur l’appareil prévu, vous pouvez supposer en toute sécurité que le problème n’est pas directement lié à Intune. Le problème rencontré relève probablement du système d’exploitation Windows ou du matériel. Dans ce cas, orientez vos recherches sur d’autres éléments, comme la configuration du TPM ou l’UEFI et le démarrage sécurisé.

## <a name="next-steps"></a>Étapes suivantes  

Voici d’autres ressources qui peuvent vous aider lors de l’utilisation de BitLocker :

- [Documentation du produit BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Configuration système requise pour BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Questions fréquentes sur BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentation du fournisseur de services de chiffrement BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Paramètres de stratégie de chiffrement Windows dans Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Chiffrement BitLocker automatique indépendant du matériel avec AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Stratégie CSP pour le chiffrement BitLocker sur les appareils auto-pilotés](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Procédure pas à pas pour créer et déployer une stratégie BitLocker avec Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
