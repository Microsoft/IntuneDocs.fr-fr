---
title: Résoudre les problèmes des actions d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Trouvez de l’aide pour résoudre les problèmes liés aux actions d’appareil.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7d4517d89e3b7365834e904c815b30a362540906
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755593"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Résoudre les problèmes liés aux actions d’appareil dans Intune

Microsoft Intune propose de nombreuses actions qui facilitent la gestion des appareils. Cet article fournit des réponses à certaines questions courantes qui peuvent vous aider à résoudre les problèmes liés aux actions d’appareil.

## <a name="disable-activation-lock-action"></a>Action Désactiver le verrou d’activation

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>J’ai cliqué sur l’action « Désactiver le verrou d’activation » dans le portail, mais cela n’a eu aucun effet sur l’appareil.
Ce comportement est attendu. Après le démarrage de l’action Désactiver le verrou d’activation, Apple demande un code mis à jour au service Intune. Vous devez taper ce code dans le champ du code secret une fois que votre appareil apparaît dans l’écran Verrou d’activation. Ce code est valide pendant 15 jours seulement. Vous devez cliquer sur l’action et copier le code avant de lancer la réinitialisation.

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>Je ne vois pas le code Désactiver le verrou d’activation dans le panneau Vue d’ensemble sur mon appareil iOS ? Pourquoi ?
Les raisons les plus probables sont les suivantes :
- Le code a expiré et a été effacé du service.
- L’appareil n’est pas supervisé avec la stratégie de restriction d’appareil pour autoriser le verrou d’activation.

Vous pouvez vérifier le code dans l’afficheur Graph à l’aide de la requête suivante :

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-ios-device"></a>Pourquoi l’action Désactiver le verrou d’activation est-elle grisée sur mon appareil iOS ?
Les raisons les plus probables sont les suivantes : 
- Le code a expiré et a été effacé du service.
- L’appareil n’est pas supervisé avec la stratégie de restriction d’appareil pour autoriser le verrou d’activation.

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>Le code Désactiver le verrou d’activation respecte-il la casse ?
Non. Notez également que vous n’avez pas besoin de taper les tirets.

## <a name="remove-devices-action"></a>Action Supprimer les appareils

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Comment faire pour indiquer qui a démarré une mise hors service/réinitialisation ?
Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Administration de locataire** > **Journaux d’audit** et vérifiez la colonne **Lancé par**.
Si vous ne voyez aucune entrée, c’est sans doute l’utilisateur de l’appareil qui a lancé l’action. Cette personne a probablement utilisé l’application Portail d’entreprise ou portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Pourquoi mon application n’a-t-elle pas été désinstallée après l’action de mise hors service ?
Elle n’a pas été désinstallée, car elle n’était pas considérée comme une application managée. Dans ce contexte, une application managée est une application qui a été installée à l’aide du service Intune. Les opérations à effectuer sont les suivantes :
- L’application a été déployée comme obligatoire.
- L’application a été déployée comme disponible, puis installée par l’utilisateur final à partir de l’application Portail d’entreprise.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Pourquoi l’action Réinitialiser est-elle grisée sur les appareils Android Enterprise inscrits avec un profil professionnel ?
Ce comportement est normal. Google n’autorise pas la réinitialisation des paramètres d’usine des appareils avec profil professionnel à partir du fournisseur MDM.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Pourquoi puis-je encore me connecter à mes applications Office après la mise hors service de mon appareil ?
La mise hors service d’un appareil ne révoque pas les jetons d’accès. Vous pouvez utiliser des stratégies d’accès conditionnel pour atténuer cette condition.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Comment puis-je superviser une action de mise hors service/réinitialisation après son lancement ?
Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **Administration de locataire** > **Journaux d’audit**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Pourquoi les réinitialisations restent-elles parfois indéfiniment à l’état En attente ?
Les appareils ne retournent pas toujours leur état au service Intune avant le démarrage de la réinitialisation. Dans ce cas, l’action s’affiche comme en attente. Si vous avez confirmé la réussite de l’action, supprimez l’appareil du service.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Que se passe-t-il si je démarre une mise hors service/réinitialisation sur un appareil hors connexion ou sur un appareil qui ne s’est pas connecté au service récemment ?
L’appareil restera à l’état **Mise hors service/Réinitialisation en attente** jusqu’à l’expiration du certificat MDM. Le certificat MDM reste valide pendant un an à partir de l’inscription et il est automatiquement renouvelé chaque année. Si l’appareil se connecte au service avant l’expiration du certificat MDM, il sera mis hors service/réinitialisé. S’il ne se reconnecte pas au service avant l’expiration du certificat MDM, il ne pourra plus s’y connecter ensuite. 180 jours après l’expiration du certificat MDM, l’appareil sera automatiquement supprimé du portail Azure.


## <a name="reset-passcode-action"></a>Action Réinitialiser le code secret

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Pourquoi l’action Réinitialiser le code secret est-elle grisée sur mon appareil inscrit en tant qu’administrateur d’appareil Android ?
Pour lutter contre les rançongiciels (ransomware), Google a supprimé la fonctionnalité de réinitialisation du code secret dans l’API d’administration des appareils (s’applique aux appareils Android version 7.0 ou ultérieure).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Pourquoi le message « Non pris en charge » s’affiche-t-il quand je lance une réinitialisation du code secret sur un appareil Android version 8.0 ou antérieure inscrit avec un profil professionnel ?
Ce message s’affiche quand le jeton de réinitialisation n’a pas été activé sur l’appareil. Pour activer le jeton de réinitialisation :
1. Vous devez rendre le code secret de profil professionnel obligatoire dans votre stratégie de configuration.
2. L’utilisateur final doit définir un code secret approprié pour son profil professionnel.
3. L’utilisateur final doit accepter la deuxième invite pour autoriser la réinitialisation du code secret.
Une fois ces étapes terminées, vous ne devriez plus recevoir ce message.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>Pourquoi suis-je invité à définir un nouveau code secret sur mon appareil iOS quand je lance l’action Supprimer le code secret ?
Cette invite s’affiche si l’une de vos stratégies de conformité exige la définition d’un code secret.

## <a name="next-steps"></a>Étapes suivantes

Obtenir [l’aide de Microsoft](../fundamentals/get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
