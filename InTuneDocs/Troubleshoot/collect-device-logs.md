---
title: Collecter les journaux des appareils | Microsoft Docs
description: "Découvrez comment collecter des journaux à partir de vos appareils gérés."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 211b996263aae7a42f8370eb343c7e759ef87790
ms.openlocfilehash: 5aae8edd2b851eb94156e82bc9b6e604644cb900
ms.lasthandoff: 02/08/2017


---

# <a name="device-logs"></a>Journaux des appareils

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Dans le cadre de vos efforts de dépannage, vous pouvez collecter les journaux des appareils utilisateur. Les instructions permettant de collecter ces journaux sont décrites ici. En règle générale, vous devez accéder à l’appareil pour obtenir ces journaux ou demander à l’utilisateur de les collecter et de vous les envoyer.

### <a name="android-logs"></a>Journaux Android
Les journaux Android se trouvent dans *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

Parfois, les fichiers n’apparaissent pas, surtout sur les appareils Android plus récents. Dans ce cas, demandez à vos utilisateurs d’ouvrir l’application Portail d’entreprise pour Android. Ils doivent ensuite sélectionner **Paramètres**>**Copier les journaux** et redémarrer leur appareil.

Pour plus d’informations sur la façon dont les utilisateurs peuvent vous envoyer des journaux de données, consultez les articles suivants :

- [Utiliser la journalisation détaillée pour aider votre administrateur informatique à résoudre les problèmes liés aux appareils](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) : décrit comment les utilisateurs peuvent activer la journalisation détaillée pour vous envoyer automatiquement tous les journaux de données. La journalisation détaillée est activée par défaut.

- [Envoyer des journaux de données de diagnostic Android à votre administrateur informatique par e-mail](/intune/enduser/send-logs-to-your-it-admin-by-email-android)

- [Envoyer les journaux de données de diagnostic à votre administrateur informatique par câble USB](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Journaux iOS

Les utilisateurs peuvent vous envoyer les erreurs d’inscription, comme décrit dans [Envoyer les erreurs d’inscription iOS à votre administrateur informatique](/intune/enduser/send-errors-to-your-it-admin-ios).

### <a name="mac-os-x-logs"></a>Journaux Mac OS X

1. Ouvrez l’application **Console**.
2. Sous **FICHIERS**, choisissez **system.log**.
3. Dans la barre de menus en haut, choisissez **Fichier** > **Enregistrer une copie sous…**. Ensuite, enregistrez le fichier.

### <a name="windows-phone"></a>Windows Phone

Dans l’application Portail d’entreprise Windows Phone, les utilisateurs choisissent les trois points (**...**) pour accéder au menu, puis **Envoyer les journaux**. Cette option est disponible avant et après la connexion à l’application Portail d’entreprise.

### <a name="windows"></a>Windows

Pour le portail d’entreprise Windows, les journaux sont situés dans *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.

