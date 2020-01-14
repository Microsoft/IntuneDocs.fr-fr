---
title: Applications iOS avec stratégies de protection des applications
description: Cet article décrit ce qui se produit lorsque votre application iOS est gérée par des stratégies de protection d’application.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606619"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>Ce qui se passe quand votre application iOS est gérée par des stratégies de protection d'application

Les stratégies de protection des applications Intune s’appliquent aux applications utilisées à des fins professionnelles ou scolaires. Cela signifie que lorsque vos employés et élèves utilisent leurs applications dans un contexte personnel, ils ne remarquent aucune différence au sein de leur expérience. Dans le contexte professionnel ou scolaire, toutefois, ils peuvent recevoir des invitations à prendre des décisions de compte, à mettre à jour leurs paramètres ou à vous contacter pour obtenir de l’aide. Utilisez cet article pour découvrir les expériences de vos utilisateurs lorsqu’ils essaient d’accéder à des applications protégées par Intune et de les utiliser.  

## <a name="access-apps"></a>Accéder aux applications

Si l’appareil **n’est pas inscrit dans Intune**, l’utilisateur est invité à redémarrer l’application quand il l’utilise pour la première fois. Un redémarrage est nécessaire pour que les stratégies de protection d’application soient appliquées à l’application.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

Si l’appareil est **inscrit pour la gestion dans Intune**, l’utilisateur voit un message indiquant que son application est désormais gérée.

## <a name="use-apps-with-multi-identity-support"></a>Utiliser des applications avec prise en charge de plusieurs identités

Les applications qui prennent en charge plusieurs identités vous permettent d’utiliser différents comptes professionnels et personnels pour accéder aux mêmes applications. Les stratégies de protection des applications, comme l’entrée d’un code confidentiel d’appareil, sont activées lorsque les utilisateurs accèdent à ces applications dans un contexte professionnel ou scolaire.   

Les utilisateurs peuvent rencontrer l’invite de code confidentiel différemment dans l’ensemble de leurs applications, en fonction de la façon dont vous configurez les stratégies.  Par exemple, vous pouvez configurer vos stratégies pour que :       
* Microsoft Outlook invite l’utilisateur à entrer un code confidentiel quand il lance l’application. 
* OneDrive invite l’utilisateur d’entrer un code confidentiel au moment de la connexion sur leur compte professionnel.  
* Microsoft Word, PowerPoint et Excel invitent l’utilisateur à entrer un code confidentiel au moment de l’accès aux documents stockés à l’emplacement de l’entreprise OneDrive Entreprise.  

- En savoir plus sur les applications qui prennent en charge [la protection d’application et les identités multiples](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) avec Intune.  

## <a name="manage-user-accounts-on-the-device"></a>Gérer les comptes d’utilisateur sur l’appareil  

Les stratégies de protection des applications Intune limitent les utilisateurs à un compte professionnel ou scolaire managé par application. Les stratégies de protection des applications ne limitent pas le nombre de comptes non managés qu’un utilisateur peut ajouter.   

- Si un utilisateur tente d’ajouter un deuxième compte géré, il est invité à sélectionner le compte géré à utiliser. Si l’utilisateur ajoute le deuxième compte, le premier compte est supprimé.
- Si vous ajoutez des stratégies de protection à un autre de vos comptes d’utilisateur, l’utilisateur est invité à sélectionner le compte managé à utiliser. L’autre compte est supprimé. 

Certains utilisateurs n’ont pas la possibilité de basculer ou de sélectionner entre les comptes managés. L’option n’est pas disponible sur les appareils qui sont :
* managés par Intune  
* managés par des solutions de gestion de la mobilité de l’entreprise tierce et configurés avec le paramètre IntuneMAMUPN 

L’exemple de scénario suivant décrit comment plusieurs comptes d’utilisateur sont traités :  

L’utilisateur A travaille pour deux sociétés : **Société X** et **Société Y**. L’utilisateur A a un compte professionnel pour chaque société, et tous deux utilisent Intune pour déployer des stratégies de protection d'application. La **Société X** déploie des stratégies de protection d'application **avant** la  **Société Y**. Le compte qui est associé à **Société X** obtient la stratégie de protection d’application en premier. Si vous souhaitez que le compte d’utilisateur associé à Société Y soit géré par les stratégies de protection d’application, vous devez supprimer le compte d’utilisateur associé à Société X et ajouter le compte d’utilisateur associé à Société Y.  

## <a name="next-steps"></a>Étapes suivantes

[Ce qui se passe quand votre application Android est gérée par des stratégies de protection d'application](end-user-mam-apps-android.md)
