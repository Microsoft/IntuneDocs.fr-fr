---
title: "Applications iOS avec stratégies de protection des applications"
description: "Cet article décrit ce qui se produit lorsque votre application iOS est gérée par des stratégies de protection d’application."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9e1b11f9bf644b2e92dad0d0281bf11febae622b
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

 Cette rubrique décrit l’expérience utilisateur des applications auxquelles des stratégies de protection des applications sont appliquées. Les stratégies de protection des applications ne s’appliquent que quand les applications sont utilisées dans le contexte professionnel, par exemple quand l’utilisateur accède à des applications à l’aide d’un compte professionnel ou accède à des fichiers stockés à l’emplacement OneDrive Entreprise d’une société.

##  <a name="access-apps"></a>Accéder aux applications

Si l’appareil **n’est pas inscrit dans Intune**, l’utilisateur est invité à redémarrer l’application quand il l’utilise pour la première fois. Un redémarrage est nécessaire pour que les stratégies de protection d’application soient appliquées à l’application.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

Si l’appareil est **inscrit pour la gestion dans Intune**, l’utilisateur voit un message indiquant que son application est désormais gérée.

##  <a name="use-apps-with-multi-identity-support"></a>Utiliser des applications avec prise en charge de plusieurs identités

Les applications qui prennent en charge plusieurs identités vous permettent d’utiliser des comptes différents (professionnels et personnels) pour accéder aux mêmes applications, alors que les stratégies de protection des applications sont appliquées uniquement quand les applications sont utilisées dans le contexte professionnel.  

Par exemple, l’utilisateur reçoit une invite de code confidentiel quand il accède à des données professionnelles. Pour l’**application Outlook**, l’utilisateur est invité à entrer un code confidentiel quand il lance l’application. Pour l’**application OneDrive**, l’utilisateur est invité à entrer un code confidentiel quand il entre son compte professionnel.  Pour Microsoft **Word**, **PowerPoint** et **Excel**, l’utilisateur est invité à entrer un code confidentiel quand il accède à des documents stockés à l’emplacement OneDrive Entreprise de la société.

- En savoir plus sur les applications qui prennent en charge [la protection d’application et les identités multiples](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) avec Intune.

Les stratégies de protection d’application s’appliquent uniquement dans le contexte professionnel. Ainsi, l’application peut se comporter différemment selon qu’il s’agit d’un contexte professionnel ou personnel.

##  <a name="manage-user-accounts-on-the-device"></a>Gérer les comptes d’utilisateur sur l’appareil

Intune prend en charge le déploiement de stratégies de protection d’application sur un seul compte d’utilisateur par appareil.

* Il est possible que le deuxième utilisateur soit bloqué sur l’appareil, mais cela dépend de l’application utilisée. Toutefois, dans tous les cas, seul le premier utilisateur sujet aux stratégies de protection d'application est affecté par la stratégie.
  * **Microsoft Word**, **Excel** et **PowerPoint** ne bloquent pas un deuxième compte d’utilisateur, mais celui-ci n’est pas affecté par les stratégies de protection d'application.  

  * Pour les applications **OneDrive** et **Outlook**, vous ne pouvez utiliser qu’un seul compte professionnel. Vous ne pouvez pas ajouter plusieurs comptes professionnels pour ces applications. Toutefois, vous pouvez supprimer un utilisateur et en ajouter un autre sur l’appareil.

* Si un appareil possède plusieurs comptes d’utilisateurs existants avant le déploiement des stratégies de protection d’application, le premier compte sur lequel les stratégies de protection d’application sont déployées est géré par les stratégies de protection d’application Intune.


Lisez l’exemple de scénario suivant pour mieux comprendre le comportement quand il existe plusieurs comptes d’utilisateur.

L’utilisateur A travaille pour deux sociétés : **Société X** et **Société Y**. L’utilisateur A a un compte professionnel pour chaque société, et tous deux utilisent Intune pour déployer des stratégies de protection d'application. **Société X** déploie des stratégies de protection d'application **avant** **Société Y**. Le compte associé à **Société X** est soumis à la stratégie de protection d’application, contrairement au compte associé à Société Y. Si vous souhaitez que le compte d’utilisateur associé à Société Y soit géré par les stratégies de protection d’application, vous devez supprimer le compte d’utilisateur associé à Société X.

### <a name="add-a-second-account"></a>Ajouter un deuxième compte

Sur un appareil iOS, si vous essayez d’ajouter un deuxième compte professionnel, un message de blocage peut s’afficher. Les comptes s’affichent et vous pouvez choisir le compte à supprimer.

## <a name="next-steps"></a>Étapes suivantes
[Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](end-user-mam-apps-android.md)
