---
title: Résoudre les problèmes d’installation d’applications
titlesuffix: Microsoft Intune
description: Utilisez le volet de résolution des problèmes de Microsoft Intune pour vous aider à résoudre les problèmes d’installation d’applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: 6e25149199c9362f628fa108d20247bb6b86d895
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075827"
---
# <a name="troubleshoot-app-installation-issues"></a>Résoudre les problèmes d’installation d’applications

Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Microsoft Intune fournit des détails sur l’échec de l’installation d’applications qui permettent aux opérateurs du support technique et aux administrateurs Intune d’afficher des informations sur l’application pour répondre aux demandes d’assistance des utilisateurs. Le volet de résolution des problèmes dans Intune fournit des détails sur l’échec, notamment des détails sur les applications managées sur l’appareil d’un utilisateur. Des informations détaillées sur le cycle de vie de bout en bout d’une application sont fournies sous chaque appareil individuel dans le volet **Applications managées**. Vous pouvez afficher les problèmes d’installation, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. 

## <a name="to-review-app-troubleshooting-details"></a>Pour examiner les informations de résolution des problèmes d’une application

Intune fournit des informations de résolution des problèmes d’une application en fonction des applications installées sur l’appareil d’un utilisateur spécifique.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Dépanner**.
4. Cliquez sur **Sélectionner un utilisateur** pour sélectionner un utilisateur à aider. Le volet **Sélectionner les utilisateurs** s’affiche.
5. Sélectionnez un utilisateur en tapant son nom ou son adresse e-mail. Cliquez sur **Sélectionner** en bas du volet. Les informations sur la résolution des problèmes pour l’utilisateur s’affichent dans le volet **Résoudre les problèmes**. 
6. Sélectionnez dans la liste **Appareils** l’appareil sur lequel exécuter la résolution des problèmes.
    ![Volet de résolution des problèmes de Microsoft Intune.](media/troubleshoot-app-install-01.png)
7. Sélectionnez **Applications managées** dans le volet de l’appareil sélectionné. Une liste des applications managées s’affiche.
    ![Détails d’un appareil spécifique managé par Intune.](media/troubleshoot-app-install-02.png)
8. Sélectionnez une application dans la liste où **l’état d’installation** indique un échec.
    ![Une application sélectionnée qui affiche les détails d’un échec d’installation.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > La même application peut être attribuée à plusieurs groupes, mais avec différentes actions prévues (intentions) pour l’application. Par exemple, une intention résolue pour une application affichera **exclue** si l’application est exclue pour un utilisateur lors de l’attribution de l’application. Pour plus d’informations, consultez [Résolution des conflits entre les intentions d’application](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Si un problème se produit lors de l’installation d’une application obligatoire, le support technique ou vous-même pouvez synchroniser l’appareil et retenter l’installation de l’application.

Les détails de l’erreur d’installation de l’application indiquent le problème. Vous pouvez utiliser ces informations pour déterminer la meilleure action à prendre pour résoudre le problème. Pour plus d’informations sur la résolution des problèmes d’installation d’une application, consultez [Codes d’erreur pour la résolution des problèmes d’installation d’une application](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues).

> [!Note]  
> Vous pouvez également accéder au volet **Dépannage** en pointant votre navigateur sur [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="app-installation-errors"></a>Erreurs d’installation des applications

Les messages d’erreur et les descriptions ci-dessous fournissent des informations sur les erreurs d’installation iOS et Android. 

### <a name="android-errors"></a>Erreurs Android

|    Message/Code d’erreur    |    Description    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    L’installation de l’application a échoué. (0xC7D14FB5)    |    Ce message d’erreur s’affiche quand Intune ne peut pas déterminer la cause de l’erreur d’installation de l’application Android. Android n’a pas fourni d’informations lors de l’échec.       Cette erreur est retournée lorsque le téléchargement du fichier APK a réussi, mais que l’installation de l’application a échoué. Cette erreur se produit le plus souvent lorsqu’un fichier APK endommagé ne peut pas être installé sur l’appareil. Cela peut être dû à Google Play Protect qui bloque l’installation de l’application pour des raisons de sécurité. Il est aussi possible que l’appareil ne prenne pas en charge l’application. Par exemple, si l’application nécessite la version d’API 21+ alors que la version 19 est installée sur l’appareil.         Intune retourne cette erreur pour les appareils DA et Knox. Même si une notification s’affiche et propose à l’utilisateur de cliquer pour réessayer, si le fichier APK est endommagé, l’installation continue d’échouer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.        |
|    L’installation de l’application a été annulée car le fichier d’installation (APK) a été supprimé après le téléchargement, mais avant l’installation. (0xC7D14FBA)    |    Le téléchargement du fichier APK a réussi, mais le fichier a été supprimé de l’appareil avant que l’utilisateur n’ait pu installer l’application. Cela peut se produire lorsqu’une longue période s’est écoulée entre le moment du téléchargement et celui de l’installation. Par exemple, l’utilisateur a peut-être annulé l’installation d’origine, puis a attendu et a cliqué sur la notification pour réessayer.         Ce message d’erreur est retourné uniquement dans les scénarios DA. Dans les scénarios Knox, l’installation peut être effectuée sans assistance. Une notification s’affiche pour proposer à l’utilisateur de réessayer. Il peut ainsi l’accepter au lieu d’annuler. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    L’installation de l’application a été annulée car le processus a été redémarré pendant l’installation. (0xC7D14FBB)    |    L’appareil a été redémarré pendant le processus d’installation du fichier APK, ce qui a annulé l’installation.        Ce message d’erreur est retourné pour les appareils DA et Knox. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Application non détectée une fois l’installation terminée. (0x87D1041C)    |    L’utilisateur a explicitement désinstallé l’application. Cette erreur n’est pas retournée par le client. Cette erreur se produit lorsque l’application a été installée, puis désinstallée entre temps par l’utilisateur. Cette erreur se produit uniquement pour les applications obligatoires. Les utilisateurs peuvent désinstaller les applications qui ne sont pas obligatoires. Cette erreur se produit uniquement avec les appareils DA. Les appareils Knox bloquent la désinstallation des applications managées.       La prochaine synchronisation réaffichera la notification sur l’appareil pour que l’utilisateur installe l’application.   L’utilisateur peut ignorer cette notification. Cette erreur continuera d’être signalée tant que l’utilisateur n’aura pas installé l’application.    |
|    Le téléchargement a échoué en raison d’une erreur inconnue. (0xC7D14FB2)    |    Cette erreur se produit lorsque le téléchargement échoue. Cette erreur se produit souvent en cas de problème avec la connexion Wi-Fi ou de connexion lente.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Le téléchargement a échoué en raison d’une erreur inconnue. La stratégie sera retentée lors de la prochaine synchronisation de l’appareil. (0xC7D15078)    |    Cette erreur se produit lorsque le téléchargement échoue. Cette erreur se produit souvent en cas de problème avec la connexion Wi-Fi ou de connexion lente.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance.    |
|    L’utilisateur final a annulé l’installation de l’application. (0xC7D14FB1)    |    L’utilisateur a explicitement désinstallé l’application. Cette erreur est retournée lorsque l’installation du système d’exploitation Android a été annulée par l’utilisateur. L’utilisateur a appuyé sur le bouton Annuler dans l’invite d’installation du système d’exploitation ou a cliqué en dehors de l’invite.        Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Le processus de téléchargement de fichiers s’est arrêté de manière inattendue. (0xC7D15015)    |    Le système d’exploitation a arrêté le processus de téléchargement avant la fin. Cette erreur peut se produire si l’appareil a une batterie faible ou si le téléchargement est trop long.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Le service de téléchargement de fichiers s’est arrêté de manière inattendue. La stratégie sera retentée lors de la prochaine synchronisation de l’appareil. (0xC7D1507C)    |    Le système d’exploitation a arrêté le processus de téléchargement avant la fin. Cette erreur peut se produire si l’appareil a une batterie faible ou si le téléchargement est trop long.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance.    |

### <a name="ios-errors"></a>Erreurs iOS

|    Message/Code d’erreur    |    Description    |
|:----------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    (0x87D12906)    |    L’agent MDM d’Apple signale que la commande d’installation a échoué.        |
|    (0x87D1313C)    |    La connexion réseau a été perdue pendant l’envoi de l’URL mise à jour du service de téléchargement vers l’appareil. Pour être plus précis, le serveur avec le nom d’hôte spécifié n’a pas été trouvé.    |
|    L’appareil iOS est actuellement occupé. (0x87D11388)    |    L’appareil iOS était occupé, ce qui a entraîné une erreur.    |
|    L’installation de l’application a échoué. (0x87D13B64)    |    L’installation de l’application a échoué. Les journaux XCODE sont nécessaires pour résoudre cette erreur.    |
|    L’application est managée, mais elle a expiré ou a été supprimée par l’utilisateur. (0x87D13B66)    |    L’utilisateur a explicitement désinstallé l’application. Il est possible aussi que l’application ait expiré, mais que son téléchargement ait échoué, ou que l’application détectée ne corresponde pas à la réponse de l’appareil.   En outre, cette erreur peut se produire en raison d’un bogue de la plateforme iOS 9.2.2.    |
|    L’installation de l’application est planifiée, mais un code d’échange est nécessaire pour effectuer la transaction.   (0x87D13B60)    |    Cette erreur se produit généralement avec les applications payantes du Store iOS.     |
|    Application non détectée une fois l’installation terminée. (0x87D1041C)    |    L’application détectée ne correspond pas à la réponse de l’appareil.    |
|    L’utilisateur a refusé l’installation de l’application. (0x87D13B62)    |    Lors de la première installation de l’application, l’utilisateur a cliqué sur Annuler.    |
|    L’utilisateur a refusé la mise à jour de l’application. (0x87D13B63)    |    L’utilisateur final a cliqué sur Annuler pendant le processus de mise à jour.     |
|    Erreur inconnue   (0x87D103E8)    |    Une erreur inconnue liée à l’installation de l’application s’est produite. C’est l’erreur qui s’affiche lorsqu’une erreur autre que celles connues se produit.    |


## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations de résolution des problèmes Intune, consultez [Utiliser le portail de résolution des problèmes pour aider les utilisateurs dans votre entreprise](help-desk-operators.md). 
- Découvrez plus d’informations sur les problèmes connus de Microsoft Intune. Pour plus d’informations, consultez [Problèmes connus dans Microsoft Intune](known-issues.md).
- Besoin d’aide supplémentaire ? Consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).
