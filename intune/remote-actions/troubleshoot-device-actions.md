---
title: Résoudre les problèmes des actions d’appareil dans Microsoft Intune - Azure | Microsoft Docs
description: Obtenir de l’aide pour résoudre les problèmes d’action de l’appareil.
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
ms.openlocfilehash: 239dd8630eb361da8609e3a34eb2c9346a64dab0
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907183"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Résoudre les problèmes liés aux actions d’appareil dans Intune

Microsoft Intune comporte de nombreuses actions qui vous aident à gérer les appareils. Cet article fournit des réponses à certaines questions courantes qui peuvent vous aider à résoudre les problèmes liés aux actions de l’appareil.

## <a name="bypass-activation-lock-action"></a>Action Contourner le verrou d’activation

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>J’ai cliqué sur l’action « contourner Verrouillage d’activation » dans le portail, mais rien ne s’est produit sur l’appareil.
Ce comportement est attendu. Après le démarrage de l’action de contournement Verrouillage d’activation, Intune demande un code mis à jour à Apple. Vous devez entrer manuellement le code dans le champ code secret une fois que votre appareil se trouve sur l’écran Verrouillage d’activation. Ce code n’est valide que pendant 15 jours. Veillez donc à cliquer sur l’action et à copier le code avant d’émettre la réinitialisation.

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>Pourquoi ne puis-je pas voir le contournement Verrouillage d’activation code dans le panneau vue d’ensemble du matériel de mon appareil iOS ?
Les raisons les plus probables sont les suivantes :
- Le code a expiré et a été effacé du service.
- L’appareil n’est pas supervisé avec la stratégie de restriction de l’appareil pour autoriser Verrouillage d’activation.

Vous pouvez vérifier le code dans l’Explorateur graphique avec la requête suivante :

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>Pourquoi l’action de contournement Verrouillage d’activation grisée pour mon appareil iOS ?
Les raisons les plus probables sont les suivantes : 
- Le code a expiré et a été effacé du service.
- L’appareil n’est pas supervisé avec la stratégie de restriction de l’appareil pour autoriser Verrouillage d’activation.

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>Le contournement Verrouillage d’activation respect de la casse du code ?
Non. Et vous n’avez pas besoin d’entrer les tirets.

## <a name="remove-devices-action"></a>Action de suppression d’appareils

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Comment faire indiquer qui a démarré une mise hors service/réinitialisation ?
Dans le [Centre d’administration du gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à administration des **clients** > **journaux d’audit** > Vérifiez la colonne **initié par** .
Si vous ne voyez pas d’entrée, la personne la plus susceptible d’être à l’origine de l’action est l’utilisateur de l’appareil. Ils ont probablement utilisé l’application Portail d’entreprise ou portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Pourquoi mon application n’a-t-elle pas été désinstallée après l’utilisation du retrait ?
Parce qu’il n’était pas considéré comme une application managée. Dans ce contexte, une application managée est une application qui a été installée à l’aide du service Intune. Les opérations à effectuer sont les suivantes :
- L’application a été déployée en fonction des besoins
- L’application a été déployée comme disponible, puis installée par l’utilisateur final à partir de l’application Portail d’entreprise.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Pourquoi la réinitialisation est-elle grisée pour les appareils Android Enterprise Work Profile ?
Ce comportement est normal. Google n’autorise pas la réinitialisation des paramètres d’usine des appareils de profil professionnel à partir du fournisseur MDM.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Pourquoi puis-je me reconnecter à mes applications Office après la mise hors service de mon appareil ?
Parce que le retrait d’un appareil ne révoque pas les jetons d’accès. Vous pouvez utiliser des stratégies d’accès conditionnel pour atténuer cette condition.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Comment puis-je surveiller une action de mise hors service/réinitialisation après son émission ?
Dans le [Centre d’administration du gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à administration des **clients** > **journaux d’audit**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Pourquoi les nettoyages apparaissent-ils parfois comme étant en attente indéfiniment ?
Les appareils ne signalent pas toujours leur état au service Intune avant le démarrage de la réinitialisation. L’action apparaît donc comme étant en attente. Si vous avez confirmé que l’opération a réussi, supprimez l’appareil du service.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Que se passe-t-il si je démarre une mise hors service/réinitialisation sur un appareil hors connexion ou sur un appareil qui n’a pas communiqué avec le service depuis un moment ?
L’appareil restera en état de mise hors service **/réinitialisation** jusqu’à l’expiration du certificat MDM. Le certificat MDM est valable pendant un an à partir de l’inscription et est automatiquement renouvelé chaque année. Si l’appareil Archive avant l’expiration du certificat MDM, il sera mis hors service/réinitialisé. Si l’appareil n’est pas vérifié avant l’expiration du certificat MDM, il ne peut pas s’archiver dans le service. 180 jours après l’expiration du certificat MDM, l’appareil est automatiquement supprimé du Portail Azure.


## <a name="reset-passcode-action"></a>Action de réinitialisation du code secret

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Pourquoi l’action de réinitialisation du code secret est-elle grisée sur mon appareil Android de l’administrateur de l’appareil ?
Pour lutter contre les ransomware, Google a supprimé la fonctionnalité de réinitialisation du code secret sur l’API d’administration des appareils (s’applique aux appareils Android version 7,0 ou ultérieures).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Pourquoi le message « non pris en charge » s’affiche-t-il lorsque j’émet une réinitialisation du code d’accès à mon appareil Android 8,0 ou à un appareil inscrit sur un profil professionnel ?
Car le jeton de réinitialisation n’a pas été activé sur l’appareil. Pour activer le jeton de réinitialisation :
1. Vous devez exiger un code secret de profil professionnel dans votre stratégie de configuration.
2. L’utilisateur final doit définir un code secret de profil professionnel approprié.
3. L’utilisateur final doit accepter l’invite secondaire pour autoriser la réinitialisation du code d’accès.
Une fois ces étapes terminées, vous ne devriez plus recevoir cette réponse.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>Pourquoi suis-je invité à définir un nouveau code d’accès sur mon appareil iOS lorsque j’émette l’action supprimer le code secret ?
Parce que l’une de vos stratégies de conformité requiert un code secret.

## <a name="next-steps"></a>Étapes suivantes

Obtenir [l’aide de Microsoft](../fundamentals/get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
