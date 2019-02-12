---
title: Résoudre les problèmes des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Problèmes courants liés aux profils d’appareil avec Microsoft Intune dans le portail Azure, notamment les changements de profil non appliqués à certains utilisateurs ou appareils, combien de temps il faut pour pousser une nouvelle stratégie sur des appareils, quels sont les paramètres appliqués en cas de stratégies multiples, que se passe-t-il quand un profil est supprimé ou retiré, etc.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 528e26ddca1b3327fb0afa2f5cff6f2dbdca1660
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55846483"
---
# <a name="common-issues-and-resolutions-with-device-profiles-in-microsoft-intune"></a>Problèmes courants avec les profils d’appareil dans Microsoft Intune et résolutions

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Résoudre les problèmes courants à l’aide des profils d’appareil Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Pourquoi un utilisateur n’obtient-il pas un nouveau profil lors de la modification d’un mot de passe ou d’une phrase secrète dans un profil Wi-Fi existant ? 
Vous créez un profil Wi-Fi d’entreprise, déployez le profil sur un groupe, changez le mot de passe et enregistrez le profil. Quand le profil change, certains utilisateurs n’ont pas le nouveau profil.

Pour résoudre ce problème, configurez un Wi-Fi invité. Si le Wi-Fi d’entreprise échoue, les utilisateurs peuvent se connecter au Wi-Fi invité. Activez tous les paramètres de connexion automatique. Déployez le profil Wi-Fi invité pour tous les utilisateurs.

Recommandations supplémentaires :  

- Comme le réseau Wi-Fi auquel vous vous connectez utilise un mot de passe ou une phrase secrète, vérifiez que vous pouvez vous connecter directement au routeur Wi-Fi. Vous pouvez faire le test avec un appareil iOS.
- Une fois que vous êtes connecté au point de terminaison Wi-Fi (routeur Wi-Fi), notez le SSID et les informations d’identification utilisées (il s’agit du mot de passe ou de la phrase secrète).
- Entrez le SSID et les informations d’identification (mot de passe ou phrase secrète) dans le champ Clé prépartagée. 
- Effectuez le déploiement sur un groupe de test avec un nombre d’utilisateurs limité, de préférence uniquement l’équipe informatique. 
- Synchronisez votre appareil iOS avec Intune. Procédez à l’inscription si ce n’est déjà fait. 
- Testez à nouveau la connexion au même point de terminaison Wi-Fi (comme indiqué à la première étape).
- Déployez sur des groupes plus volumineux, puis finalement sur tous les utilisateurs attendus dans votre organisation. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Combien de temps faut-il pour que les appareils mobiles obtiennent une stratégie ou les applications une fois que celles-ci ont été affectées ?
Quand une stratégie ou une application est affectée, Intune commence immédiatement par indiquer à l’appareil de s’enregistrer auprès du service Intune. La notification prend généralement moins de 5 minutes.

Si un appareil ne se manifeste pas pour obtenir la stratégie après l’envoi de la première notification, Intune effectue trois autres tentatives. Si l’appareil est hors connexion (par exemple, s’il est éteint ou n’est pas connecté à un réseau), il ne peut pas recevoir de notifications. Dans ce cas, l’appareil obtient la stratégie lors de son prochain enregistrement planifié auprès du service Intune de la manière suivante :

- iOS et macOS : toutes les six heures
- Android : toutes les huit heures
- Windows Phone : toutes les huit heures
- PC Windows 8.1 et Windows 10 inscrits en tant qu’appareils : toutes les huit heures

Si l’appareil vient d’être inscrit, la fréquence d’enregistrement est plus élevée :

- iOS et macOS : toutes les 15 minutes pendant six heures, puis toutes les six heures
- Android : toutes les trois minutes pendant 15 minutes, puis toutes les 15 minutes pendant deux heures, puis toutes les huit heures
- Windows Phone : toutes les cinq minutes pendant 15 minutes, puis toutes les 15 minutes pendant deux heures, puis toutes les huit heures
- PC Windows inscrits en tant qu’appareils : toutes les trois minutes pendant 30 minutes, puis toutes les huit heures

Pour rechercher la stratégie à tout moment, les utilisateurs peuvent ouvrir l’application Portail d’entreprise et synchroniser l’appareil.

Pour les appareils sans affinité utilisateur, la fréquence de synchronisation immédiatement après l’inscription peut varier entre quelques heures et un jour ou plus. Intune envoie des demandes à des intervalles différents pour qu’un appareil s’enregistre auprès du service. Toutefois, c’est à l’appareil de s’enregistrer. Après l’inscription initiale, selon le type d’inscription de l’appareil et les stratégies et profils qui lui sont affectés, la durée d’enregistrement de l’appareil est imprévisible. Toutefois, une fois que l’appareil est inscrit et que toutes les stratégies initiales sont appliquées, l’appareil recherche de nouvelles stratégies environ toutes les six heures.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quelles sont les actions qui déclenchent l’envoi immédiat d’une notification par Intune ?
Les appareils s’enregistrent auprès d’Intune quand ils reçoivent une notification d’enregistrement ou pendant leur enregistrement planifié régulièrement. Quand vous ciblez un appareil ou un utilisateur avec une action de type réinitialisation, verrouillage, réinitialisation de code secret, affectation d’application, affectation de profil ou affectation de stratégie, Intune notifie immédiatement l’appareil qu’il doit s’enregistrer auprès du service Intune pour recevoir ces mises à jour.

D’autres modifications, comme la modification des coordonnées dans le portail d’entreprise, ne déclenchent pas l’envoi immédiat d’une notification aux appareils.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Si plusieurs stratégies sont affectées au même utilisateur ou appareil, quels sont les paramètres appliqués ?
Quand plusieurs stratégies sont affectées au même utilisateur ou appareil, les paramètre à appliquer sont déterminés au niveau de chaque paramètre :

- Les paramètres de stratégie de conformité ont toujours priorité sur les paramètres de stratégie de configuration

- Si deux stratégies de conformité sont appliquées au même paramètre, le paramètre de la stratégie de conformité la plus restrictive s’applique.

- Si un paramètre de stratégie de configuration est en conflit avec un paramètre d’une autre stratégie de configuration, ce conflit apparaît dans le portail Azure. Dans ce scénario, vous pouvez corriger ces conflits manuellement.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Que se passe-t-il quand des stratégies de protection d’application entrent en conflit ? Laquelle est appliquée à l’application ?
Les valeurs en conflit sont les paramètres les plus restrictifs disponibles dans une stratégie de protection d’application, à l’exception des champs d’entrée numérique (comme le nombre de tentatives autorisées avant la réinitialisation du code PIN). Les champs d’entrée numérique sont définis sur les mêmes valeurs que quand vous créez une stratégie GAM dans la console en choisissant les paramètres recommandés.

Des conflits se produisent quand deux paramètres de profil sont identiques. Par exemple, vous avez configuré deux stratégies MAM identiques, à l’exception du paramètre de copier/coller. Dans ce scénario, le paramètre de copier/coller est défini sur la valeur la plus restrictive, mais le reste des paramètres est appliqué selon leur configuration.

Si un profil est affecté à l’application et entre en vigueur, puis qu’un deuxième profil est affecté, le premier est prioritaire et reste appliqué, tandis que le deuxième s’affiche comme étant en conflit. S’ils sont appliqués en même temps, ce qui signifie qu’il n’existe aucun profil précédent, ils sont alors tous deux en conflit. Tous les paramètres en conflit sont définis sur les valeurs les plus restrictives.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Que se passe-t-il quand les stratégies personnalisées iOS entrent en conflit ?
Intune n’évalue pas la charge utile des fichiers de configuration Apple ni le profil OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personnalisé. Son rôle se limite simplement au mécanisme de livraison.

Quand vous affectez un profil personnalisé, vérifiez que les paramètres configurés ne sont pas en conflit avec les stratégies de conformité, de configuration, ou d’autres stratégies personnalisées. Si un profil personnalisé et ses paramètres sont en conflit, les paramètres sont appliqués de façon aléatoire.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Que se passe-t-il quand un profil est supprimé ou n’est plus applicable ?
Quand vous supprimez un profil ou retirez un appareil d’un groupe qui a le profil, le profil et les paramètres sont supprimés de l’appareil conformément aux listes suivantes :

- Profils Wi-Fi, VPN, de certificat et de messagerie Ces profils sont supprimés de tous les appareils inscrits et pris en charge.
- Tous les autres types de profils :  

  - **Appareils Windows et Android** : les paramètres ne sont pas supprimés de l’appareil
  - **Appareils Windows Phone 8.1** : Les paramètres suivants sont supprimés :  
  
    - Exiger un mot de passe pour déverrouiller des appareils mobiles
    - Autoriser les mots de passe simples
    - Longueur minimale du mot de passe
    - Type de mot de passe requis
    - Expiration du mot de passe (jours)
    - Mémoriser l'historique des mots de passe
    - Nombre d'échecs de connexion répétée autorisé avant réinitialisation de l'appareil
    - Minutes d'inactivité avant demande du mot de passe
    - Type de mot de passe requis - Nombre minimum de jeux de caractères
    - Autoriser l'appareil photo
    - Exiger le chiffrement sur l'appareil mobile
    - Autoriser le stockage amovible
    - Autoriser le navigateur web
    - Autoriser la boutique d'applications
    - Autoriser la capture d'écran
    - Autoriser la géolocalisation
    - Autoriser le compte Microsoft
    - Autoriser la fonction copier-coller
    - Autoriser la connexion Wi-Fi
    - Autoriser la connexion automatique aux points d'accès Wi-Fi gratuits
    - Autoriser l'indication des points d'accès Wi-Fi
    - Autoriser la réinitialisation
    - Autoriser Bluetooth
    - Autoriser NFC
    - Autoriser le Wi-Fi

  - **iOS** : tous les paramètres sont supprimés, sauf :
  
    - Autoriser l'itinérance vocale
    - Autoriser l'itinérance des données
    - Autoriser la synchronisation automatique lors de l'itinérance

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>J’ai modifié un profil de restriction d’appareil, mais les modifications n’ont pas pris effet
Les appareils Windows Phone n’autorisent pas l’assouplissement des stratégies de sécurité définies par MDM ou EAS a posteriori. Par exemple, si vous définissez le **Nombre minimal de caractères des mots de passe** sur 8, vous ne pouvez plus le réduire à 4. Le profil le plus restrictif a déjà été appliqué à l’appareil.

Si vous voulez attribuer au profil une valeur moins sûre, réinitialisez les stratégies de sécurité. Par exemple, dans Windows 8.1, sur le Bureau, balayez à partir de la droite et sélectionnez **Paramètres** > **Panneau de configuration**. Sélectionnez l’applet **Comptes d’utilisateurs**. En bas du menu de navigation de gauche figure le lien **Réinitialiser les stratégies de sécurité**. Sélectionnez-le, puis choisissez **Réinitialiser les stratégies**.

Pour pouvoir appliquer un profil moins restrictif sur les autres appareils MDM (Android, Windows Phone 8.1 et ultérieur, iOS et Windows 10), vous devez peut-être les mettre hors service, puis les réinscrire au service.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Certains paramètres dans un profil Windows 10 retournent « Non Applicable »
Certains paramètres sur les appareils Windows 10 peuvent apparaître comme « Non Applicable ». Dans ce cas, ce paramètre spécifique n’est pas pris en charge sur la version ou l’édition de Windows en cours d’exécution sur l’appareil. Ce message peut apparaître pour les raisons suivantes :

- Le paramètre est disponible uniquement pour les versions les plus récentes de Windows, et pas pour la version actuelle du système d’exploitation sur l’appareil.
- Le paramètre est disponible uniquement pour des éditions de Windows ou des références SKU spécifiques, par exemple les éditions Familiale, Professionnel, Entreprise et Éducation.

Pour en savoir plus sur les exigences de version et de référence SKU pour les différents paramètres, consultez [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Étapes suivantes
Besoin d’aide supplémentaire ? Consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).
