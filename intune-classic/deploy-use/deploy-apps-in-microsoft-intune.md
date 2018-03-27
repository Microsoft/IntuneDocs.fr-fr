---
title: Comment déployer des applications
description: Utilisez les informations de cette rubrique pour déployer des applications avec Microsoft Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b42019e-73da-4538-a496-212f11d5bf9b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ed098a22da1def82c90fbb159d54be9b1a369ba8
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="deploy-apps-in-microsoft-intune"></a>Déploiement d’applications dans Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilisez les informations de cette rubrique pour déployer des applications avec Microsoft Intune.


## <a name="deploy-an-app"></a>Déployer une application
Dans cette procédure, vous allez déployer une application sur des groupes d’appareils ou d’utilisateurs sélectionnés.

### <a name="to-deploy-an-app"></a>Pour déployer une application

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **Applications** &gt; **Applications** pour afficher la liste des applications que vous gérez.

2.  Sélectionnez l’application à déployer, puis cliquez sur **Gérer le déploiement**.

3.  Dans la boîte de dialogue *&lt;Nom de l’application&gt;*, dans la page **Sélectionner des groupes**, sélectionnez les groupes d’utilisateurs ou d’appareils sur lesquels vous souhaitez déployer l’application.

4.  Dans la page **Action de déploiement**, configurez les paramètres suivants :

    - **Approbation** : indiquez si le déploiement est :
        - **Requis** (installation obligatoire)
        - **Disponible** (les utilisateurs effectuent l’installation à la demande à partir du portail d’entreprise)
        - **Non applicable** (l’application n’est pas installée ni affichée dans le portail d’entreprise)
        - **Désinstaller** (l’application est désinstallée des appareils ciblés)
    - **Échéance** : pour les installations requises, choisissez le délai de déploiement de l’application. Vous pouvez choisir l’une des valeurs prédéfinies ou sélectionner l’option **Personnalisé** pour configurer votre propre échéance.

5. Si l’application que vous déployez peut être configurée par une stratégie de gestion des applications mobiles, la page **Gestion des applications mobiles** s’affiche. Dans cette page, choisissez la stratégie de gestion des applications mobiles que vous souhaitez associer à cette application.

    [Découvrez quelles applications Microsoft sont compatibles avec les stratégies de gestion des applications mobiles.](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx)

6. Si l’application que vous déployez est compatible avec les profils VPN Intune, la page **Profil VPN** s’affiche. Dans cette page, vous pouvez choisir d’associer des applications iOS à un profil VPN que vous avez déployé. La connexion VPN s’ouvre automatiquement lorsque l’application est lancée. Pour rendre un profil VPN disponible, le paramètre de profil **Par VPN d’application** doit être activé.
 Pour obtenir des informations sur la configuration des profils VPN, y compris sur l’association de profils à des applications, consultez la page [Connexions VPN dans Microsoft Intune](vpn-connections-in-microsoft-intune.md).

<!---
>[!TIP]
>If an end user previously installed an iOS app and you now deploy it with a deployment action of **Available**, Intune will automatically begin to manage that app with no further action required by you, or the end-user.
--->

## <a name="example"></a>Exemple

Dans cet exemple, vous avez déployé l’application en tant qu’application **Disponible** sur un appareil iOS.
L’application s’affiche sur les appareils des utilisateurs dans le Portail d’entreprise, et les utilisateurs peuvent l’installer depuis cet emplacement.

Par exemple, dans cette capture d’écran, l’application Bing pour iOS a été déployée via le type d’installation **Lien externe**, avec une icône personnalisée. L’option **Affiche comme application proposée et la met en avant dans le portail d’entreprise** a été sélectionnée.  
![Application disponible iOS](./media/available-install-on-iOS.png)

Si vous avez déployé l’application comme application **Requise** sur un appareil iOS, l’utilisateur recevra une notification indiquant qu’une application est prête à être installée. Par exemple, dans cette capture d’écran, l’application Dossiers de travail pour iOS a été déployée via le type d’installation **Application iOS gérée à partir de l’App Store**.  
![Application requise iOS](./media/iOS-Required-install.PNG)

## <a name="next-steps"></a>Étapes suivantes

Après avoir déployé une application, vous pouvez surveiller sa progression. Pour plus d’informations, consultez [Monitor apps in Microsoft Intune](monitor-apps-in-microsoft-intune.md) (Surveiller des applications dans Microsoft Intune).
