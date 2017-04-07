---
title: "Problèmes connus dans la préversion de Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Préversion Intune Azure : en savoir plus sur les problèmes connus dans la préversion"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Problèmes connus dans la préversion de Microsoft Intune


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Utilisez cette rubrique pour en savoir plus sur les problèmes connus dans la préversion d’Intune.

Si vous souhaitez signaler un bogue qui n’est pas répertorié ici, [créez une demande de support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

Si vous souhaitez ajouter une nouvelle fonctionnalité à Intune, envisagez d’envoyer un rapport sur notre site [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console).

## <a name="administration-and-accounts"></a>Administration et comptes

- Les administrateurs globaux (également appelés administrateurs de clients) peuvent continuer à effectuer des tâches d’administration quotidiennes sans licence Intune ou Enterprise Mobility Suite (EMS) distincte. Toutefois, si les administrateurs généraux souhaitent utiliser le service, par exemple pour inscrire leur propre appareil ou un appareil d’entreprise, ou pour utiliser le portail d’entreprise Intune, ils doivent avoir une licence Intune ou EMS comme tout autre utilisateur.

## <a name="apple-enrollment-profile-migration"></a>Migration d’un profil d’inscription Apple
- Dans quelques mois, Intune vous permettra de gérer les inscriptions au programme DEP (Device Enrollment Program) et à Apple Configurator par le biais du nouveau portail Azure. Si vous supprimez le jeton du programme DEP d’Apple et que vous ne chargez pas de jeton mis à jour, le jeton d’origine est restauré dans le nouveau portail Azure dans le cadre de la migration de votre compte Intune. Pour supprimer ce jeton et empêcher l’inscription au programme DEP, supprimez simplement le jeton dans le portail Azure. 

