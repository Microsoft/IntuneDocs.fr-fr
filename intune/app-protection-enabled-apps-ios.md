---
title: Applications iOS avec stratégies de protection des applications
titlesuffix: Microsoft Intune
description: Découvrez ce qui vous attend dans le cas d’une application iOS associée à des stratégies de protection.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 667d5df5d53a9248137274cf7abe5b7fde5bf8bb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181936"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Découvrez l’expérience utilisateur relative aux applications iOS associées à des stratégies de protection d’application. Les stratégies de protection d’application ne sont appliquées que si les applications sont utilisées dans le contexte professionnel. C’est le cas par exemple quand vous accédez à une application avec un compte professionnel ou à des fichiers stockés dans l’emplacement OneDrive de votre entreprise.
##  <a name="accessing-apps"></a>Accès aux applications

Si l’appareil **n’est pas inscrit dans Intune**, l’utilisateur est invité à redémarrer l’application quand il l’utilise pour la première fois.  Un redémarrage est nécessaire pour que les stratégies de protection d'application soient appliquées à l’application. La capture d’écran suivante illustre cela avec l’application Skype :


![capture d’écran de l’appareil iOS affichant l’invite du code confidentiel](./media/ios-pin-prompt.png)

Si l’appareil est **inscrit pour la gestion dans Intune**, l’utilisateur voit un message indiquant que son application est désormais gérée :

![capture d’écran de l’appareil iOS montrant le message Géré par votre entreprise avec l’invite du code confidentiel](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>Utilisation d’applications avec prise en charge de plusieurs identités

Les stratégies de protection d’application entrent en vigueur uniquement quand un utilisateur tente d’accéder à des données professionnelles. Vous pouvez constater un comportement différent si l’utilisateur tente d’accéder à l’application pour une utilisation personnelle. Les stratégies ne s’appliquent pas non plus à un nouveau contenu qui n’est pas encore enregistré. Un contenu nouveau est considéré comme informations de l’entreprise uniquement après avoir été enregistré dans un emplacement d’entreprise, comme SharePoint ou OneDrive Entreprise.

Pour les applications qui prennent en charge plusieurs identités, Intune applique uniquement les stratégies de protection d’application si un utilisateur accède à des données professionnelles.  Par exemple, un utilisateur peut recevoir une invite lui demandant d’entrer un code PIN.  Dans **l’application Outlook**, une invite s’affiche quand un utilisateur lance l’application. Dans **l’application OneDrive**, une invite s’affiche quand un utilisateur tape le compte professionnel.  Dans Microsoft **Word**, **PowerPoint** et **Excel**, une invite s’affiche quand un utilisateur accède à des documents d’entreprise sur OneDrive.
##  <a name="managing-user-accounts-on-the-device"></a>Gestion des comptes d’utilisateur sur l’appareil

Intune prend en charge le déploiement de stratégies de protection d'application vers un seul compte d’utilisateur par appareil.

* Il est possible que le deuxième utilisateur soit bloqué sur l’appareil, mais cela dépend de l’application utilisée. Toutefois, dans tous les cas, seul le premier utilisateur sujet aux stratégies de protection d’application est affecté par la stratégie.
  * **Microsoft Word**, **Excel** et **PowerPoint** ne bloquent pas l’accès à un compte d’utilisateur supplémentaire. Toutefois, le compte d’utilisateur n’est pas affecté par les stratégies de protection d’application.

  * Pour les **applications OneDrive et Outlook**, vous ne pouvez utiliser qu’un seul compte professionnel.  L’ajout de plusieurs comptes professionnels est bloqué sur ces applications.  Toutefois, vous pouvez supprimer un utilisateur d’un appareil, puis en ajouter un autre.

* Un appareil peut avoir plusieurs comptes d’utilisateur existants avant le déploiement de stratégies de protection application. Dans ce cas, le premier compte sur lequel les stratégies de protection d’application sont déployées est géré par les stratégies de protection d’application Intune.


Lisez l’exemple de scénario suivant pour découvrir comment Intune gère plusieurs comptes d’utilisateur.

L’utilisateur A travaille pour deux sociétés : **Société X** et **Société Y**. L’utilisateur A a un compte professionnel pour chaque société, et tous deux utilisent Intune pour déployer des stratégies de protection d'application. **Société X** déploie des stratégies de protection d'application **avant** **Société Y**. Le compte associé à **Société X** est soumis à la stratégie de protection d’application, contrairement au compte associé à Société Y. Pour que le compte d’utilisateur associé à Société Y soit géré par les stratégies de protection d’application, l’utilisateur A doit supprimer le compte d’utilisateur de la Société X.
### <a name="adding-a-second-account"></a>Ajout d’un deuxième compte

Sur un appareil iOS, si vous essayez d’ajouter un deuxième compte professionnel, un message de blocage peut s’afficher.  Les comptes s’affichent et vous pouvez choisir le compte à supprimer.

![Capture d’écran de la boîte de dialogue avec le message de blocage et les options Oui et Non](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>Étapes suivantes
[Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>Voir aussi
[Créer et déployer des stratégies de protection d’application à l’aide de Microsoft Intune](app-protection-policies.md)
