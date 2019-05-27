---
title: Résoudre les problèmes d’installation d’applications
titleSuffix: Microsoft Intune
description: Utilisez le volet de résolution des problèmes de Microsoft Intune pour vous aider à résoudre les problèmes d’installation d’applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/19/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 47115fcb2662439bff867043c2fb58bc3550dbbb
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044878"
---
# <a name="troubleshoot-app-installation-issues"></a>Résoudre les problèmes d’installation d’applications

Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Microsoft Intune fournit des détails sur l’échec de l’installation d’applications qui permettent aux opérateurs du support technique et aux administrateurs Intune d’afficher des informations sur l’application pour répondre aux demandes d’assistance des utilisateurs. Le volet de résolution des problèmes dans Intune fournit des détails sur l’échec, notamment des détails sur les applications managées sur l’appareil d’un utilisateur. Des informations détaillées sur le cycle de vie de bout en bout d’une application sont fournies sous chaque appareil individuel dans le volet **Applications managées**. Vous pouvez afficher les problèmes d’installation, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. 

## <a name="app-troubleshooting-details"></a>Résolution des problèmes liés aux applications

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

Les détails de l’erreur d’installation de l’application indiquent le problème. Vous pouvez utiliser ces informations pour déterminer la meilleure action à prendre pour résoudre le problème. Pour plus d’informations sur la résolution des problèmes d’installation d’une application, consultez [Erreurs d’installation d’applications](troubleshoot-app-install.md#app-installation-errors).

> [!Note]  
> Vous pouvez également accéder au volet **Dépannage** en pointant votre navigateur sur [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="win32-app-installation-troubleshooting"></a>Résolution des problèmes liés à l’installation des applications Win32

Sélectionnez l’application Win32 qui a été déployée à l’aide de l’extension de gestion Intune. Si l’installation de votre application Win32 échoue, vous pouvez sélectionner l’option **Collecter les journaux**. 

> [!IMPORTANT]
> L’option **Collecter les journaux** n’est pas activée si l’application Win32 a été installée correctement sur l’appareil.<p>Pour collecter les informations des journaux d’application Win32, vous devez avoir installé l’extension de gestion Intune sur le client Windows. L’extension de gestion Intune est installée lorsqu’un script PowerShell ou une application Win32 est déployé dans un groupe de sécurité d’utilisateurs ou d’appareils. Pour plus d’informations, consultez [Extension de gestion Intune - Prérequis](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Collecter le fichier journal

Pour collecter vos journaux d’installation d’application Win32, vous devez d’abord suivre les étapes fournies dans la section [Résolution des problèmes liés aux applications](troubleshoot-app-install.md#app-troubleshooting-details). Ensuite, poursuivez avec les étapes suivantes :

1. Cliquez sur l’option **Collecter les journaux** située dans le panneau **Détails de l’installation**.

    <image alt="Win32 app installation details - Collect log option" src="media/troubleshoot-app-install-04.png" width="500" />

2. Pour démarrer le processus de collecte des fichiers journaux, indiquez leurs noms dans les chemins, puis cliquez sur **OK**.
    
    > [!NOTE]
    > La durée de collecte des journaux est inférieure à deux heures. Types de fichiers pris en charge : *.log, .txt, .dmp, .cab, .zip, .xml, .evtx et .evtl*. Le nombre de chemins de fichiers est limité à 25.

3. Une fois que les fichiers journaux ont été collectés, vous pouvez sélectionner le lien **Journaux** pour télécharger les fichiers journaux.

    <image alt="Win32 app log details - Download logs" src="media/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > Une notification s’affiche pour indiquer que la collecte des journaux d’application a bien été effectuée.

#### <a name="win32-log-collection-requirements"></a>Conditions de collecte des journaux Win32

Vous devez respecter certaines conditions pour collecter les fichiers journaux :

- Vous devez spécifier le chemin complet du fichier journal. 
- Vous pouvez spécifier des variables d’environnement pour la collecte de journaux, par exemple :<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- Seules les extensions de fichier exactes sont autorisées, par exemple :<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- Le nombre de fichiers journaux pouvant être chargés est limité à 25, et leur taille totale est limitée à 60 Mo. 
- La collecte des journaux d’installation des applications Win32 est activée pour les applications qui répondent aux affectations d’applications de type « obligatoire », « disponible » et « désinstaller ».
- Les journaux stockés sont chiffrés pour protéger les informations d’identification personnelle qu’ils peuvent contenir.
- Lorsque vous créez un ticket de support pour un échec concernant une application Win32, envoyez les journaux d’erreurs associés à l’aide de la procédure décrite ci-dessus.

## <a name="app-installation-errors"></a>Erreurs d’installation des applications

Les messages d’erreur et les descriptions ci-dessous fournissent des informations sur les erreurs d’installation iOS et Android. 

### <a name="android-errors"></a>Erreurs Android

|    Message/Code d’erreur    |    Description    |
|----------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    L’installation de l’application a échoué. (0xC7D14FB5)    |    Ce message d’erreur s’affiche quand Intune ne peut pas déterminer la cause de l’erreur d’installation de l’application Android. Android n’a pas fourni d’informations lors de l’échec.       Cette erreur est retournée lorsque le téléchargement du fichier APK a réussi, mais que l’installation de l’application a échoué. Cette erreur se produit le plus souvent lorsqu’un fichier APK endommagé ne peut pas être installé sur l’appareil. Cela peut être dû à Google Play Protect qui bloque l’installation de l’application pour des raisons de sécurité. Il est aussi possible que l’appareil ne prenne pas en charge l’application. Par exemple, si l’application nécessite la version d’API 21+ alors que la version 19 est installée sur l’appareil.         Intune retourne cette erreur pour les appareils DA et Knox. Même si une notification s’affiche et propose à l’utilisateur de cliquer pour réessayer, si le fichier APK est endommagé, l’installation continue d’échouer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.        |
|    L’installation de l’application a été annulée car le fichier d’installation (APK) a été supprimé après le téléchargement, mais avant l’installation. (0xC7D14FBA)    |    Le téléchargement du fichier APK a réussi, mais le fichier a été supprimé de l’appareil avant que l’utilisateur n’ait pu installer l’application. Cela peut se produire lorsqu’une longue période s’est écoulée entre le moment du téléchargement et celui de l’installation. Par exemple, l’utilisateur a peut-être annulé l’installation d’origine, puis a attendu et cliqué sur la notification pour réessayer.         Ce message d’erreur est retourné uniquement dans les scénarios DA. Dans les scénarios Knox, l’installation peut être effectuée sans assistance. Une notification s’affiche pour proposer à l’utilisateur de réessayer. Il peut ainsi l’accepter au lieu d’annuler. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    L’installation de l’application a été annulée car le processus a été redémarré pendant l’installation. (0xC7D14FBB)    |    L’appareil a été redémarré pendant le processus d’installation du fichier APK, ce qui a annulé l’installation.        Ce message d’erreur est retourné pour les appareils DA et Knox. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Application non détectée une fois l’installation terminée. (0x87D1041C)    |    L’utilisateur a explicitement désinstallé l’application. Cette erreur n’est pas retournée par le client. Cette erreur se produit lorsque l’application a été installée, puis désinstallée entre temps par l’utilisateur. Cette erreur se produit uniquement pour les applications obligatoires. Les utilisateurs peuvent désinstaller les applications qui ne sont pas obligatoires. Cette erreur se produit uniquement avec les appareils DA. Les appareils Knox bloquent la désinstallation des applications managées.       La prochaine synchronisation réaffichera la notification sur l’appareil pour que l’utilisateur installe l’application.   L’utilisateur peut ignorer cette notification. Cette erreur continuera d’être signalée tant que l’utilisateur n’aura pas installé l’application.    |
|    Le téléchargement a échoué en raison d’une erreur inconnue. (0xC7D14FB2)    |    Cette erreur se produit lorsque le téléchargement échoue. Cette erreur se produit souvent en cas de problème avec la connexion Wi-Fi ou de connexion lente.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Le téléchargement a échoué en raison d’une erreur inconnue. La stratégie sera retentée lors de la prochaine synchronisation de l’appareil. (0xC7D15078)    |    Cette erreur se produit lorsque le téléchargement échoue. Cette erreur se produit souvent en cas de problème avec la connexion Wi-Fi ou de connexion lente.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance.    |
|    L’utilisateur final a annulé l’installation de l’application. (0xC7D14FB1)    |    L’utilisateur a explicitement désinstallé l’application. Cette erreur est retournée lorsque l’installation du système d’exploitation Android a été annulée par l’utilisateur. L’utilisateur a appuyé sur le bouton Annuler dans l’invite d’installation du système d’exploitation ou a cliqué en dehors de l’invite.        Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Le processus de téléchargement de fichiers s’est arrêté de manière inattendue. (0xC7D15015)    |    Le système d’exploitation a arrêté le processus de téléchargement avant la fin. Cette erreur peut se produire si l’appareil a une batterie faible ou si le téléchargement est trop long.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance. Intune affiche une notification proposant à l’utilisateur de cliquer pour réessayer. Si l’application est disponible, vous pouvez ignorer la notification. Toutefois, si l’application est obligatoire, elle ne peut pas être ignorée.    |
|    Le service de téléchargement de fichiers s’est arrêté de manière inattendue. La stratégie sera retentée lors de la prochaine synchronisation de l’appareil. (0xC7D1507C)    |    Le système d’exploitation a arrêté le processus de téléchargement avant la fin. Cette erreur peut se produire si l’appareil a une batterie faible ou si le téléchargement est trop long.       Cette erreur est retournée uniquement dans les scénarios DA. Dans les scénarios Knox, l’utilisateur n’est pas invité à installer l’application, puisque celle-ci est installée sans assistance.    |

### <a name="ios-errors"></a>Erreurs iOS

| Message/Code d’erreur | Description/Conseils de dépannage |
|------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| (0x87D12906) | L’agent GPM d’Apple signale que la commande d’installation a échoué. |
| (0x87D1313C) | La connexion réseau a été perdue pendant l’envoi de l’URL mise à jour du service de téléchargement vers l’appareil. Pour être plus précis, aucun serveur portant le nom d’hôte spécifié n’a été trouvé. |
| L’appareil iOS est actuellement occupé. (0x87D11388) | L’appareil iOS était occupé, ce qui a entraîné une erreur. |
| L’installation de l’application a échoué. (0x87D13B64) | Échec de l’installation de l’application. Les journaux XCODE sont nécessaires pour résoudre cette erreur. |
| L’application est managée, mais elle a expiré ou a été supprimée par l’utilisateur. (0x87D13B66) | L’utilisateur a explicitement désinstallé l’application. Il est possible aussi que l’application ait expiré, mais que son téléchargement ait échoué, ou que l’application détectée ne corresponde pas à la réponse de l’appareil.   En outre, cette erreur peut se produire en raison d’un bogue de la plateforme iOS 9.2.2. |
| L’installation de l’application est planifiée, mais un code d’échange est nécessaire pour effectuer la transaction. (0x87D13B60) | Cette erreur se produit généralement avec les applications payantes de l’App Store iOS. |
| L’application n’a pas été détectée une fois l’installation terminée.   (0x87D1041C) | L’application détectée ne correspond pas à la réponse de l’appareil. |
| L’utilisateur a refusé l’installation de l’application. (0x87D13B62) | Lors de la première installation de l’application, l’utilisateur a cliqué sur Annuler. |
| L’utilisateur a refusé la mise à jour de l’application. (0x87D13B63) | L’utilisateur final a cliqué sur Annuler pendant le processus de mise à jour. |
| Erreur inconnue (0x87D103E8) | Une erreur inconnue liée à l’installation de l’application s’est produite. Cette erreur s’affiche lorsqu’une erreur autre que celles connues se produit. |
| Peut installer uniquement les applications VPP sur un iPad partagé (-2016330861). | Vous devez passer par le programme d’achat en volume (VPP) Apple pour obtenir les applications si vous voulez les installer sur un iPad partagé. |
| Impossible d’installer des applications si l’App Store est désactivé (-2016330860).  | L’App Store doit être activé pour que l’utilisateur puisse installer l’application. |
| La licence VPP de l’application est introuvable (-2016330859).  | Essayez de révoquer puis de réaffecter la licence de l’application. |
| Échec de l’installation d’applications système avec le fournisseur MDM (-2016330858). | L’installation d’applications préinstallées par le système d’exploitation iOS n’est pas prise en charge. |
| Échec de l’installation d’applications quand l’appareil est en mode Perdu (-2016330857). | En mode Perdu, vous bloquez toute utilisation de l’appareil.   Désactivez le mode Perdu pour pouvoir installer des applications. |
| Échec de l’installation d’applications quand l’appareil est en mode Kiosque (-2016330856). | Pour installer des applications, essayez d’ajouter cet appareil à un groupe d’exclusion de la stratégie de configuration du mode Kiosque. |
| Impossible d’installer des applications 32 bits sur cet appareil (-2016330852). | L’appareil ne prend pas en charge l’installation des applications 32 bits. Essayez de déployer la version 64 bits de l’application. |
| L’utilisateur doit se connecter à l’App Store (-2016330855). | L’utilisateur doit se connecter à l’App Store avant de pouvoir installer l’application. |
| Problème inconnu. Veuillez recommencez (-2016330854). | L’installation de l’application a échoué en raison d’un problème inconnu.   Réessayez plus tard. |
| Échec de l’installation de l’application. Intune retentera l’installation lors de la prochaine synchronisation de l’appareil (-2016330853). | Une erreur s’est produite lors de l’installation de l’application sur l’appareil. Synchronisez l’appareil pour retenter l’installation de l’application. |

### <a name="other-installation-errors"></a>Autres erreurs d’installation

|    Message/Code d’erreur    |    Description    |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    0x80073CFF,   0x80CF201C (erreur du client)    |    Pour installer cette application, vous devez disposer d'un système compatible avec le chargement de versions tests. Assurez-vous que le package d’application dispose d’une signature approuvée et qu’il est installé sur un ordinateur appartenant à un domaine sur lequel la stratégie **AllowAllTrustedApps** est activée ou sur un ordinateur qui a une licence de chargement indépendant Windows sur lequel la stratégie **AllowAllTrustedApps** est activée. Pour plus d’informations, consultez [Résolution des problèmes de conditionnement, de déploiement et de requête des applications Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).     |
|    0x80073CF0    |    Le package n'a pas pu être ouvert. Causes possibles :<ul><li> Le package n'est pas signé.</li><li> Le nom de l'éditeur ne correspond pas à l'objet de signature du certificat.</li></ul> Consultez le journal des événements **AppxPackagingOM** pour plus d'informations. Pour plus d’informations, consultez [Résolution des problèmes de conditionnement, de déploiement et de requête des applications Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CF3    |    Échec de la mise à jour du package, d'une dépendance ou validation de conflit. Causes possibles :<ul><li> Le package entrant est en conflit avec un package installé.</li><li> Une dépendance de package spécifiée est introuvable.</li><li> Ce package ne prend pas en charge la bonne architecture de processeur.</li></ul> Consultez le journal des événements **AppXDeployment-Server** pour plus d'informations. Pour plus d’informations, consultez [Résolution des problèmes de conditionnement, de déploiement et de requête des applications Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x80073CFB    |    Le package fourni est déjà installé, et la réinstallation du package est bloquée. Cette erreur peut s'afficher si vous installez un package qui n'est pas identique au package déjà installé. Confirmez que la signature numérique fait également partie du package. Lorsqu'un package est reconstruit ou resigné, ce package n'est plus identique au niveau des bits au package déjà installé. Deux options possibles s'offrent à vous pour corriger cette erreur :<ul><li> incrémenter le numéro de version de l'application, puis reconstruire et resigner le package ;</li><li> supprimer l'ancien package pour chaque utilisateur sur le système avant d'installer le nouveau package.</li></ul> Pour plus d’informations, consultez [Résolution des problèmes de conditionnement, de déploiement et de requête des applications Windows Store](https://docs.microsoft.com/windows/desktop/appxpkg/troubleshooting).    |
|    0x87D1041C    |    Installation de l’application réussie mais l’application n’est pas détectée. L’application a été déployée correctement par Intune, puis désinstallée par la suite. Voici quelques raisons pour lesquelles l’application est désinstallée :<ul><li> L’utilisateur final a désinstallé l’application.</li><li> Les informations d’identité dans le package ne correspondent pas à ce que l’appareil signale pour les applications incorrectes.</li><li>Pour les fichiers MSI à mise à jour automatique, la version du produit ne correspond pas aux informations de l’application après une mise à jour externe à Intune.</li></ul> Demandez à l’utilisateur de réinstaller l’application depuis le portail d’entreprise. Notez que les applications obligatoires sont automatiquement réinstallées au prochain enregistrement de l’appareil.    |

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Résolution des problèmes liés aux applications du Microsoft Store

Les informations de la rubrique [Résolution des problèmes d’empaquetage, de déploiement et de requête des applications du Microsoft Store](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) vous aident à résoudre les problèmes courants que vous pouvez rencontrer durant l’installation d’applications du Microsoft Store, en utilisant Intune ou par tout autre moyen.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations de résolution des problèmes Intune, consultez [Utiliser le portail de résolution des problèmes pour aider les utilisateurs dans votre entreprise](help-desk-operators.md). 
- Découvrez plus d’informations sur les problèmes connus de Microsoft Intune. Pour plus d’informations, consultez [Problèmes connus dans Microsoft Intune](known-issues.md).
- Besoin d’aide supplémentaire ? Consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).
