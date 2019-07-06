---
title: Supprimer votre appareil de la gestion si vous avez refusé les conditions d’utilisation | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb4ac87bef7c822111e95c18f149fa8d0598c36e
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546637"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>Supprimer votre appareil de la gestion si vous avez refusé les conditions d’utilisation

Si vous avez refusé les conditions d’utilisation durant la tentative de connexion à l’application Portail d’entreprise, vous ne pourrez plus vous connecter à l’application Portail d’entreprise. Vous devez donc utiliser ces instructions de contournement pour supprimer de votre appareil d’Intune.

Quand vous désinstallez l’application Portail d’entreprise, vous supprimez également votre appareil d’Intune. Votre appareil ne peut alors plus accéder aux ressources de l’entreprise. Pour plus d’informations sur ce qui se passe lors de la suppression de votre appareil de la gestion, consultez [Que se passe-t-il quand vous désinscrivez votre appareil d’Intune ?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Avant de pouvoir désinstaller l’application Portail d’entreprise, vous devez accéder au paramètre **Administrateurs de l’appareil** et désactiver **Portail d’entreprise**. Les étapes peuvent être légèrement différentes selon l’appareil Android que vous utilisez.

## <a name="removing-the-device-from-the-company-portal-app"></a>Suppression de l’appareil de l’application Portail d’entreprise

Pour supprimer votre appareil d’Intune et désinstaller l’application Portail d’entreprise :

1. Accédez à **Paramètres** &gt; **Sécurité &amp;Verrouillage d’écran** &gt; **Administrateurs de l’appareil**.

    Cette étape désinscrit immédiatement votre appareil.

2. Désactivez **Portail d’entreprise** ou décochez la case qui se trouve à côté.

    Vous pouvez désormais désinstaller l’application Portail d’entreprise.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Suppression des données collectées par l’application Portail d’entreprise

Pour supprimer toutes les données que stocke l’application Portail d’entreprise pour Android sur votre appareil :

  - Effacer les données d’application dans Applications -> Cliquer sur l’application -> bouton « Effacer les données »
  - Supprimer le dossier '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal'


Encore besoin d’aide ? Contactez le support technique de votre entreprise (consultez le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour les informations de contact) ou écrivez à <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">l’équipe Microsoft Android</a>.
