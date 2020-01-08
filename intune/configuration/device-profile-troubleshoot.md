---
title: Résoudre les problèmes des profils d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Questions et réponses courantes liées aux stratégies et profils d’appareil avec Microsoft Intune, notamment les changements de profil non appliqués aux utilisateurs ou appareils, le temps de transmission nécessaire d’une nouvelle stratégie sur des appareils, les paramètres appliqués en cas de stratégies multiples, ce qui se passe lorsqu’un profil est supprimé ou retiré, etc.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95186e4d1e54737ffeaa5e4c9728d188c2f867d6
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206633"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Questions, problèmes et solutions concernant les stratégies et les profils d’appareil dans Microsoft Intune



Obtenez des réponses aux questions courantes lorsque vous utilisez des profils et des stratégies d’appareil dans Intune. Cet article répertorie également les intervalles d’archivage, fournit plus de détails sur les conflits, et bien plus encore.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Pourquoi un utilisateur n’obtient-il pas un nouveau profil lors de la modification d’un mot de passe ou d’une phrase secrète dans un profil Wi-Fi existant ?

Vous créez un profil Wi-Fi d’entreprise, déployez le profil sur un groupe, changez le mot de passe et enregistrez le profil. Quand le profil change, certains utilisateurs n’ont pas le nouveau profil.

Pour résoudre ce problème, configurez un Wi-Fi invité. Si le Wi-Fi d’entreprise échoue, les utilisateurs peuvent se connecter au Wi-Fi invité. Activez tous les paramètres de connexion automatique. Déployez le profil Wi-Fi invité pour tous les utilisateurs.

Recommandations supplémentaires :  

- Si le réseau Wi-Fi auquel vous vous connectez utilise un mot de passe ou une phrase secrète, vérifiez que vous pouvez vous connecter directement au routeur Wi-Fi. Vous pouvez faire le test avec un appareil iOS.
- Une fois que vous êtes connecté au point de terminaison Wi-Fi (routeur Wi-Fi), notez le SSID et les informations d’identification utilisées (il s’agit du mot de passe ou de la phrase secrète).
- Entrez le SSID et les informations d’identification (mot de passe ou phrase secrète) dans le champ Clé prépartagée. 
- Effectuez le déploiement sur un groupe de test avec un nombre d’utilisateurs limité, de préférence uniquement l’équipe informatique. 
- Synchronisez votre appareil iOS avec Intune. Procédez à l’inscription si ce n’est déjà fait. 
- Testez à nouveau la connexion au même point de terminaison Wi-Fi (comme indiqué à la première étape).
- Déployez sur des groupes plus volumineux, puis finalement sur tous les utilisateurs attendus dans votre organisation. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Combien de temps faut-il pour que les appareils obtiennent une stratégie, un profil ou une application une fois que ceux-ci ont été attribués ?

Intune indique à l’appareil de s’enregistrer auprès du service Intune. Les délais de notification varient, allant d’un délai immédiat à quelques heures. Ces délais de notification varient également d’une plateforme à l’autre.

Si un appareil ne se manifeste pas pour obtenir la stratégie ou le profil après la première notification, Intune effectue trois autres tentatives. Un appareil est hors connexion, par exemple, s’il est éteint ou n’est pas connecté à un réseau, ne peut pas recevoir de notifications. Dans ce cas, l’appareil obtient la stratégie ou le profil lors de son prochain archivage planifié auprès du service Intune. Il en va de même pour les vérifications de non-conformité, y compris les appareils qui passent d’un état conforme à un état non conforme.

Fréquences **estimées** :

| Plate-forme | Cycle d’actualisation|
| --- | --- |
| iOS | Environ toutes les 8 heures |
| macOS | Environ toutes les 8 heures |
| Android | Environ toutes les 8 heures |
| PC Windows 10 inscrits en tant qu’appareils | Environ toutes les 8 heures |
| Windows Phone | Environ toutes les 8 heures |
| Windows 8.1 | Environ toutes les 8 heures |

Si l’appareil vient d’être inscrit, la vérification de la conformité et de la non-conformité et l’archivage de la configuration s’exécutent plus fréquemment, ce qui est **estimé** comme suit :

| Plate-forme | Fréquence |
| --- | --- |
| iOS | Toutes les 15 minutes pendant 1 heures, puis environ toutes les 8 heures |  
| macOS | Toutes les 15 minutes pendant 1 heures, puis environ toutes les 8 heures | 
| Android | Toutes les 3 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis environ toutes les 8 heures | 
| PC Windows 10 inscrits en tant qu’appareils | Toutes les 3 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis environ toutes les 8 heures | 
| Windows Phone | Toutes les 5 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis environ toutes les 8 heures | 
| Windows 8.1 | Toutes les 5 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis environ toutes les 8 heures | 

Les utilisateurs peuvent ouvrir l’application Portail d’entreprise, **Paramètres** > **Synchroniser** à tout moment pour rechercher immédiatement les mises à jour de stratégie ou de profil.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quelles sont les actions qui déclenchent l’envoi immédiat d’une notification par Intune ?

Il existe différentes actions qui déclenchent une notification, par exemple lorsqu’une stratégie, un profil ou une application est attribué(e) (ou non attribué(e)), mis(e) à jour, supprimé(e), etc. La durée de ces actions varient d’une plateforme à l’autre.

Les appareils s’enregistrent auprès d’Intune lorsqu’ils reçoivent une notification d’enregistrement ou pendant leur enregistrement planifié. Lorsque vous ciblez un appareil ou un utilisateur avec une action telle que verrouillage, réinitialisation de code secret, attribution d’application, de profil ou de stratégie, Intune notifie immédiatement l’appareil qu’il doit s’enregistrer pour recevoir ces mises à jour.

D’autres modifications, comme la modification des coordonnées dans l’application Portail d’entreprise, ne déclenchent pas l’envoi immédiat d’une notification aux appareils.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Si plusieurs stratégies sont affectées au même utilisateur ou appareil, quels sont les paramètres appliqués ?

Lorsque deux stratégies ou plus sont attribuées au même utilisateur ou appareil, le paramètre s’applique au niveau de chaque paramètre :

- Les paramètres de stratégie de conformité ont toujours la priorité sur les paramètres de profil de configuration.

- Si une stratégie de conformité s’applique au même paramètre d’une autre stratégie de conformité, le paramètre de la stratégie de conformité la plus restrictive s’applique.

- Si un paramètre de stratégie de configuration est en conflit avec un paramètre d’une autre stratégie de configuration, ce conflit est signalé dans Intune. Corrigez ces conflits manuellement.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Que se passe-t-il quand des stratégies de protection d’application entrent en conflit ? Laquelle est appliquée à l’application ?

Les valeurs en conflit sont les paramètres les plus restrictifs disponibles dans une stratégie de protection d’application, *à l’exception* des champs d’entrée numérique tels que le nombre de tentatives autorisées avant la réinitialisation du code PIN. Les champs d’entrée numérique sont définis sur les mêmes valeurs que lorsque vous créez une stratégie GAM en choisissant les paramètres recommandés.

Des conflits se produisent lorsque deux paramètres de profil sont identiques. Par exemple, vous avez configuré deux stratégies MAM identiques, à l’exception du paramètre de copier/coller. Dans ce scénario, le paramètre Copier/Coller est défini sur la valeur la plus restrictive, mais les autres paramètres sont appliqués selon leur configuration.

Une stratégie est déployée sur l’application et entre en vigueur. Une deuxième stratégie est déployée. Dans ce scénario, la première stratégie est prioritaire et reste appliquée. La deuxième stratégie est signalée comme conflictuelle. Si les deux sont appliquées en même temps, ce qui signifie qu’aucune d’elles n’est prioritaire, elles sont toutes les deux en conflit. Tous les paramètres en conflit sont définis sur les valeurs les plus restrictives.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Que se passe-t-il quand les stratégies personnalisées iOS entrent en conflit ?

Intune n’évalue pas la charge utile des fichiers de configuration Apple ni la stratégie OMA-URI personnalisée. Son rôle se limite simplement au mécanisme de livraison.

Lorsque vous attribuez une stratégie personnalisée, vérifiez que les paramètres configurés ne sont pas en conflit avec les stratégies de conformité, de configuration ou d’autres stratégies personnalisées. Si une stratégie personnalisée et ses paramètres sont en conflit, les paramètres sont appliqués de façon aléatoire.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Que se passe-t-il quand un profil est supprimé ou n’est plus applicable ?

Lorsque vous supprimez un profil ou retirez un appareil d’un groupe qui a le profil, le profil et les paramètres sont supprimés de l’appareil tel que décrit :

- Profils Wi-Fi, VPN, de certificat et de messagerie Ces profils sont supprimés de tous les appareils inscrits et pris en charge.
- Tous les autres types de profils :  

  - **Appareils Windows et Android** : Les paramètres ne sont pas supprimés de l’appareil
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

Une fois définis, les appareils Windows Phone n’autorisent pas l’assouplissement des stratégies de sécurité définies par GPM ou EAS a posteriori. Par exemple, vous définissez le **Nombre minimal de caractères des mots de passe** sur 8. Vous essayez de le réduire à 4. Le profil le plus restrictif est déjà appliqué à l’appareil.

Pour attribuer au profil une valeur moins sûre, réinitialisez les stratégies de sécurité. Par exemple, dans Windows 8.1, sur le Bureau, balayez à partir de la droite > sélectionnez **Paramètres** > **Panneau de configuration**. Sélectionnez l’applet **Comptes d’utilisateurs**. En bas du menu de navigation de gauche figure le lien **Réinitialiser les stratégies de sécurité**. Sélectionnez-le, puis choisissez **Réinitialiser les stratégies**.

Pour pouvoir appliquer un profil moins restrictif sur les autres appareils GPM (Android, Windows Phone 8.1 et ultérieur, iOS et Windows 10), vous devrez peut-être les retirer, puis les réinscrire à Intune.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Certains paramètres dans un profil Windows 10 retournent « Non Applicable »

Certains paramètres sur les appareils Windows 10 peuvent apparaître comme « Non Applicable ». Dans ce cas, ce paramètre spécifique n’est pas pris en charge sur la version ou l’édition de Windows en cours d’exécution sur l’appareil. Ce message peut apparaître pour les raisons suivantes :

- Le paramètre est disponible uniquement pour les versions les plus récentes de Windows, et pas pour la version actuelle du système d’exploitation sur l’appareil.
- Le paramètre est disponible uniquement pour des éditions de Windows ou des références SKU spécifiques, par exemple les éditions Familiale, Professionnel, Entreprise et Éducation.

Pour en savoir plus sur les exigences de version et de référence SKU pour les différents paramètres, consultez [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Étapes suivantes

Besoin d’aide supplémentaire ? Consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](../fundamentals/get-support.md).
