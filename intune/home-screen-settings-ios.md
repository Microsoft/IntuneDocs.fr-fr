---
title: Paramètres de disposition de l’écran d’accueil Microsoft Intune pour les appareils exécutant iOS
titleSuffix: ''
description: Découvrez les paramètres Microsoft Intune que vous pouvez utiliser pour personnaliser l’écran d’accueil et l’écran d’ancrage sur des appareils exécutant iOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65ecff2a21fa814c3b3518eb92e0378301dbd606
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189265"
---
# <a name="microsoft-intune-home-screen-layout-settings-for-devices-running-ios"></a>Paramètres de disposition de l’écran d’accueil Microsoft Intune pour les appareils exécutant iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Utilisez ces paramètres pour configurer la disposition des applications et des dossiers sur l’écran d’ancrage et l’écran d’accueil des appareils exécutant iOS.

Les appareils exécutant iOS avec un profil affecté doivent être en mode supervisé et exécuter iOS 9.3 ou ultérieur.

1. À partir de [Intune dans le portail Azure](https://portal.azure.com), naviguez vers [**Fonctionnalités de l’appareil** dans la zone de configuration de l’appareil](device-features-configure.md).
2. Dans le volet **Fonctionnalités de l’appareil**, sélectionnez **Disposition de l’écran d’accueil (supervisé uniquement)**.
3. Dans le volet **Disposition de l’écran d’accueil (supervisé uniquement)**, choisissez si vous voulez configurer les dispositions **Ancrer** ou **Pages**.

## <a name="add-items-to-the-dock"></a>Ajouter des éléments à l’écran d’ancrage

Dans le volet **Ancrer**, vous pouvez ajouter jusqu’à six éléments ou dossiers à l’ancrage de l’écran iOS. De nombreux appareils prennent cependant en charge moins d’éléments (par exemple, les appareils iPhone acceptent un maximum de quatre éléments). Dans ce cas, seuls les quatre premiers éléments que vous avez configurés s’affichent sur l’appareil.

1. Choisissez **Ajouter** pour ajouter un élément à l’écran d’ancrage.
2. Dans le volet **Ajouter une ligne**, indiquez si vous souhaitez ajouter une **Application** ou un **Dossier**.
3. En utilisant les informations de cette rubrique, configurez les applications et les dossiers que vous souhaitez voir apparaître dans l’écran d’ancrage.
4. Continuez à ajouter des éléments. Une fois terminé, cliquez sur **OK** dans chaque volet jusqu’à ce que vous reveniez au volet **Créer un profil**. Choisissez **Créer**.

>[!TIP]
> Vous pouvez faire glisser et déplacer des éléments dans l’écran d’accueil et dans les listes de pages pour les réorganiser.

### <a name="example"></a>Exemple

Dans cet exemple, vous avez configuré l’écran d’ancrage pour afficher uniquement les applications Safari, Mail et Bourse. Dans l’image suivante, l’application Mail est sélectionnée pour illustrer ses propriétés :

![Exemples de paramètres d’ancrage iOS](./media/FfFiUcP.png)

Quand vous affectez la stratégie à un iPhone, vous obtenez un espace d’ancrage semblable à cette capture d’écran :

![Exemple de disposition d’ancrage iOS sur iPhone](./media/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>Ajouter des pages à l’écran d’accueil

Ajoutez les pages que vous souhaitez afficher sur l’écran d’accueil et les applications qui s’affichent dans chaque page. Les applications que vous ajoutez à une page sont organisées de gauche à droite, dans l’ordre selon lequel elles sont spécifiées dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une page suivante.

1. Dans le volet **Pages**, choisissez **Ajouter**.
2. Dans le volet **Ajouter une ligne**, entrez un **Nom de page**. Ce nom est utilisé à titre de référence dans le portail Azure, mais il *n’est pas affiché* sur l’appareil iOS.
3. Cliquez sur **Ajouter** et indiquez si vous souhaitez ajouter une **Application** ou un **Dossier** à la page.
4. En utilisant les informations de cette rubrique, configurez les applications et les dossiers que vous souhaitez voir apparaître dans la page.

### <a name="example"></a>Exemple

Dans cet exemple, vous avez configuré une page nommée **Contoso**. La page affiche uniquement les applications Trouver des amis et Réglages. Dans l’image suivante, l’application Réglages est sélectionnée pour illustrer ses propriétés :

![Exemple de paramètres d’écran d’accueil iOS](./media/Jc2OxyX.png)

Quand vous affectez la stratégie à un iPhone, vous obtenez une page semblable à cette capture d’écran :

![Appareil iOS avec écran d’accueil modifié](./media/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>Comment ajouter une application à la liste

1. Entrez le **Nom de l’application**. Ce nom est utilisé à titre de référence dans le portail Azure, mais il *n’est pas affiché* sur l’appareil iOS.
2. Entrez **l’ID d’ensemble d’applications** de l’application que vous souhaitez déployer. Pour obtenir de l’aide, consultez la section **Référence à un ID d’ensemble pour les applications iOS intégrées** de cette rubrique.
3. Cliquez sur **OK**, puis continuer à ajouter des éléments, sans dépasser **6** éléments pour l’ancrage et **60** éléments pour une page de l’appareil.
4. Lorsque vous avez terminé, cliquez sur **OK**.

## <a name="how-to-add-a-folder-to-the-list"></a>Comment ajouter un dossier à la liste

Les applications que vous ajoutez à une page dans un dossier sont organisées de gauche à droite, dans l’ordre selon lequel elles sont spécifiées dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une page suivante.

1. Entrez le **Nom du dossier**. Ce nom apparaît aux utilisateurs sur leur appareil.
2. Cliquez sur **Ajouter** pour créer une page dans le dossier. Vous pouvez ajouter jusqu’à 20 pages.
3. Dans le volet **Ajouter une ligne**, entrez un nom pour de page. Ce nom est utilisé à titre de référence dans le portail Azure, mais il *n’est pas affiché* sur l’appareil iOS.
3. Entrez le **Nom de l’application**. Ce nom est utilisé à titre de référence dans le portail Azure, mais il *n’est pas affiché* sur l’appareil iOS.
2. Entrez **l’ID d’ensemble d’applications** de l’application que vous souhaitez déployer. Consultez la section **Comment ajouter une application à la liste** pour plus d’informations.
3. Choisissez **Ajouter**. Vous pouvez ajouter jusqu’à 60 éléments.
4. Lorsque vous avez terminé, cliquez sur **OK**.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Référence à un ID d’ensemble pour les applications iOS intégrées

Cette liste affiche l’ID d’ensemble de quelques applications iOS intégrées parmi les plus courantes. Pour rechercher l’ID d’ensemble d’autres applications, contactez votre éditeur de logiciels.

|||
|-|-|
|Nom de l’application|ID d’ensemble|
|App Store|com.apple.AppStore|
|Calculatrice|com.apple.calculator|
|Calendrier|com.apple.mobilecal|
|Appareil photo|com.apple.camera|
|Horloge|com.apple.mobiletimer|
|Boussole|com.apple.compass|
|Contacts|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Trouver des amis|com.apple.mobileme.fmf1|
|Trouver un iPhone|com.apple.mobileme.fmip1|
|Centre de jeux|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Intégrité|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|Mail|com.apple.mobilemail|
|Mappages|com.apple.Maps|
|Messages|com.apple.MobileSMS|
|Musique|com.apple.Music|
|Actualités|com.apple.news|
|Remarques|com.apple.mobilenotes|
|Nombres|com.apple.Numbers|
|Pages|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Photo|com.apple.mobileslideshow|
|Podcasts|com.apple.podcasts|
|Rappels|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Paramètres|com.apple.Preferences|
|Bourse|com.apple.stocks|
|Conseils|com.apple.tips|
|Vidéos|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Portefeuille|com.apple.Passbook|
|Regardez|com.apple.Bridge|
|Météo|com.apple.weather|


## <a name="next-steps"></a>Étapes suivantes

Vous pouvez maintenant affecter le profil d’appareil aux groupes que vous choisissez. Pour plus d’informations, consultez [Guide pratique pour attribuer des profils d’appareils](device-profile-assign.md).
