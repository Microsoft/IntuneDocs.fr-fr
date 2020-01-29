---
title: Résoudre les problèmes d’installation d’applications
titleSuffix: Microsoft Intune
description: Utilisez le volet de résolution des problèmes de Microsoft Intune pour vous aider à résoudre les problèmes d’installation d’applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: be66f99006b06dce9f9bfe21eafa9f2be302e7b9
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540977"
---
# <a name="troubleshoot-app-installation-issues"></a>Résoudre les problèmes d’installation d’applications

Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Microsoft Intune fournit des détails sur l’échec de l’installation d’applications qui permettent aux opérateurs du support technique et aux administrateurs Intune d’afficher des informations sur l’application pour répondre aux demandes d’assistance des utilisateurs. Le volet de résolution des problèmes dans Intune fournit des détails sur l’échec, notamment des détails sur les applications managées sur l’appareil d’un utilisateur. Des informations détaillées sur le cycle de vie de bout en bout d’une application sont fournies sous chaque appareil individuel dans le volet **Applications managées**. Vous pouvez afficher les problèmes d’installation, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. 

> [!NOTE]
> Pour plus d’informations spécifiques sur les codes d’erreur d’installation d’applications, consultez [Informations de référence sur les erreurs d’installation de l’application Intune](~/apps/app-install-error-codes.md).

## <a name="app-troubleshooting-details"></a>Résolution des problèmes liés aux applications

Intune fournit des informations de résolution des problèmes d’une application en fonction des applications installées sur l’appareil d’un utilisateur spécifique.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Sélectionnez **Dépannage + support**.
4. Cliquez sur **Sélectionner un utilisateur** pour sélectionner un utilisateur à aider. Le volet **Sélectionner les utilisateurs** s’affiche.
5. Sélectionnez un utilisateur en tapant son nom ou son adresse e-mail. Cliquez sur **Sélectionner** en bas du volet. Les informations sur la résolution des problèmes pour l’utilisateur s’affichent dans le volet **Résoudre les problèmes**. 
6. Sélectionnez dans la liste **Appareils** l’appareil sur lequel exécuter la résolution des problèmes.
    ![Volet de résolution des problèmes de Microsoft Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. Sélectionnez **Applications managées** dans le volet de l’appareil sélectionné. Une liste des applications managées s’affiche.
    ![Détails d’un appareil spécifique managé par Intune.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. Sélectionnez une application dans la liste où **l’état d’installation** indique un échec.
    ![Une application sélectionnée qui affiche les détails d’un échec d’installation.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > La même application peut être attribuée à plusieurs groupes, mais avec différentes actions prévues (intentions) pour l’application. Par exemple, une intention résolue pour une application affichera **exclue** si l’application est exclue pour un utilisateur lors de l’attribution de l’application. Pour plus d’informations, consultez [Résolution des conflits entre les intentions d’application](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Si un problème se produit lors de l’installation d’une application obligatoire, le support technique ou vous-même pouvez synchroniser l’appareil et retenter l’installation de l’application.

Les détails de l’erreur d’installation de l’application indiquent le problème. Vous pouvez utiliser ces informations pour déterminer la meilleure action à prendre pour résoudre le problème. Pour plus d’informations sur la résolution des problèmes d’installation de l’application, consultez [Erreurs d’installation de l’application Android](app-install-error-codes.md#android-app-installation-errors) et [Erreurs d’installation de l’application iOS](app-install-error-codes.md#ios-app-installation-errors).

> [!Note]  
> Vous pouvez également accéder au volet **Dépannage** en pointant votre navigateur sur [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>L’installation de l’application ciblant le groupe d’utilisateurs n’atteint pas l’appareil
Essayez les actions suivantes si vous rencontrez des problèmes lors de l’installation d’applications :
- Si vous ne voyez pas l’application dans le Portail d’entreprise, assurez-vous que l’application est déployée avec l’intention **Disponible** et que l’utilisateur accède au Portail d’entreprise avec le type d’appareil pris en charge par l’application.
- Pour les appareils BYOD Windows, l’utilisateur doit ajouter un compte professionnel à l’appareil.
- Vérifiez si l’utilisateur dépasse la limite d’appareils AAD :
  1. Accédez à [Paramètres des appareils Azure Active Directory](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId).
  2. Notez la valeur définie pour **Nombre maximal d’appareils par utilisateur**.
  3. Accédez à [Utilisateurs Azure Active Directory](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers).
  4. Sélectionnez l’utilisateur concerné, puis cliquez sur **Appareils**.
  5. Si l’utilisateur dépasse la limite définie, supprimez tous les enregistrements obsolètes qui ne sont plus nécessaires.
- Pour les appareils DEP iOS, assurez-vous que l’utilisateur apparaît dans la liste **Inscription effectuée par l’utilisateur** dans le volet Vue d’ensemble des appareils Intune. Si vous voyez « NA », déployez une stratégie de configuration pour le Portail d’entreprise Intune. Pour plus d’informations, consultez [Configurer l’application Portail d’entreprise](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Résolution des problèmes liés à l’installation des applications Win32

Sélectionnez l’application Win32 qui a été déployée à l’aide de l’extension de gestion Intune. Si l’installation de votre application Win32 échoue, vous pouvez sélectionner l’option **Collecter les journaux**. 

> [!IMPORTANT]
> L’option **Collecter les journaux** n’est pas activée si l’application Win32 a été installée correctement sur l’appareil.<p>Pour collecter les informations des journaux d’application Win32, vous devez avoir installé l’extension de gestion Intune sur le client Windows. L’extension de gestion Intune est installée lorsqu’un script PowerShell ou une application Win32 est déployé dans un groupe de sécurité d’utilisateurs ou d’appareils. Pour plus d’informations, consultez [Extension de gestion Intune - Prérequis](intune-management-extension.md#prerequisites).

### <a name="collect-log-file"></a>Collecter le fichier journal

Pour collecter vos journaux d’installation d’application Win32, vous devez d’abord suivre les étapes fournies dans la section [Résolution des problèmes liés aux applications](troubleshoot-app-install.md#app-troubleshooting-details). Ensuite, poursuivez avec les étapes suivantes :

1. Cliquez sur l’option **Collecter les journaux** située dans le volet **Détails de l’installation**.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. Pour démarrer le processus de collecte des fichiers journaux, indiquez leurs noms dans les chemins, puis cliquez sur **OK**.

    > [!NOTE]
    > La durée de collecte des journaux est inférieure à deux heures. Types de fichiers pris en charge : *.log, .txt, .dmp, .cab, .zip, .xml, .evtx et .evtl*. Le nombre de chemins de fichiers est limité à 25.

3. Une fois que les fichiers journaux ont été collectés, vous pouvez sélectionner le lien **Journaux** pour télécharger les fichiers journaux.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

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
- Les journaux stockés sont chiffrés afin de protéger les informations d’identification personnelle qu’ils contiennent.
- Lorsque vous créez un ticket de support pour un échec concernant une application Win32, envoyez les journaux d’erreurs associés à l’aide de la procédure décrite ci-dessus.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Résolution des problèmes liés aux applications du Microsoft Store

Les informations de la rubrique [Résolution des problèmes d’empaquetage, de déploiement et de requête des applications du Microsoft Store](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) vous aident à résoudre les problèmes courants que vous pouvez rencontrer durant l’installation d’applications du Microsoft Store, en utilisant Intune ou par tout autre moyen.

## <a name="app-troubleshooting-resources"></a>Ressources de dépannage des applications
- [Déploiement de Visio et de Project dans le cadre du déploiement d’Office Pro plus](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)
- [Faire en sorte que les applications Microsoft Store pour Entreprises déployées via l’installation Intune puissent être installées sur Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)
- [Résolution des problèmes de déploiement d’applications MSI dans Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)
- [Bonnes pratiques pour la distribution de logiciels vers l’agent Windows PC Intune classique](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations de résolution des problèmes Intune, consultez [Utiliser le portail de résolution des problèmes pour aider les utilisateurs dans votre entreprise](../fundamentals/help-desk-operators.md). 
- Découvrez plus d’informations sur les problèmes connus de Microsoft Intune. Pour plus d’informations, consultez [Réussite des clients Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess).
- Besoin d’aide supplémentaire ? Consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](../fundamentals/get-support.md).
