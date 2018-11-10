---
title: Ajouter des applications à Microsoft Intune
titlesuffix: ''
description: Découvrez comment ajouter des applications à Microsoft Intune et affecter les applications à des utilisateurs et à des appareils. Intune prend en charge un large éventail de types d’applications.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0039223176afb3bed3a9ac2d2ada76b82096c26
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236626"
---
# <a name="add-apps-to-microsoft-intune"></a>Ajouter des applications à Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Avant de pouvoir assigner, analyser, configurer ou protéger des applications, vous devez les ajouter à Microsoft Intune.

Les utilisateurs des applications et des appareils de votre entreprise (le personnel de votre entreprise) peuvent avoir plusieurs exigences en matière d’applications. Avant d’ajouter des applications à Intune et de les rendre disponibles pour votre personnel, vous devez évaluer et comprendre quelques principes de base sur les applications. Vous devez comprendre les différents types d’applications disponibles pour Intune. Vous devez évaluer les exigences en matière d’applications, par exemple les plateformes et les fonctionnalités dont a besoin votre personnel. Vous devez déterminer si vous allez utiliser Intune pour gérer les appareils (et les applications) ou pour gérer les applications sans gérer les appareils. Enfin, vous devez déterminer les applications et les fonctionnalités nécessaires à votre personnel, et savoir qui en a besoin. Les informations contenues dans cet article vont vous aider à bien démarrer.

## <a name="app-types-in-microsoft-intune"></a>Types d’applications dans Microsoft Intune

Intune prend en charge un large éventail de types d’applications. Les options disponibles diffèrent pour chaque type d’application. Intune vous permet d’ajouter et d’affecter les types d’applications suivants :

| Types d’applications | Installation | Updates |
|---|---|---|
| Applications du magasin (applications Store) | Intune installe l’application sur l’appareil.  | Les mises à jour de l’application sont automatiques.   |
| Applications écrites en interne (cœur de métier)  | Intune installe l’application sur l’appareil (vous fournissez le fichier d’installation).     | Vous devez mettre à jour l’application.  |
| Applications intégrées    | Intune installe l’application sur l’appareil.  | Les mises à jour de l’application sont automatiques.  |
| Applications sur le web (lien Web) | Intune crée un raccourci vers l’application web sur l’écran d’accueil de l’appareil.  | Les mises à jour de l’application sont automatiques.    |

### <a name="specific-app-type-details"></a>Détails sur les type spécifiques d’application
 
Le tableau suivant répertorie les types d’applications spécifiques et la façon dont vous pouvez les ajouter dans le panneau Intune **Ajouter une application** :

| **Type spécifique à l’application** | **Type général** | **Procédures spécifiques à l’application** |
| --- | --- | --- |
| Applications de l’App Store Android  | Application de store  | Sélectionnez **Android** comme **type d’application**, puis entrez l’URL du Google Play Store de l’application. |
| Applications de l’App Store iOS  | Application de store  | Sélectionnez **iOS** comme **type d’application**, recherchez l’application, puis sélectionnez l’application dans Intune. |
| Application du Windows Phone 8.1 Store  | Application de store  | Sélectionnez **Windows Phone 8.1** comme **type d’application**, puis entrez l’URL du Microsoft Store de l’application. |
| Applications Microsoft Store  | Application de store  | Sélectionnez **Windows** comme **type d’application**, puis entrez l’URL du Microsoft Store de l’application. |
| Applications de profil professionnel Android | Application de store  | Recherchez et approuvez l’application avec profil professionnel Android à partir du Managed Google Play Store.  |
| Applications Office 365 pour Windows 10  | Application de store (Office 365) | Sélectionnez **Windows 10** sous la **Suite Office 365** comme **type d’application**, puis sélectionnez l’application Office 365 à installer.  |
| Applications Office 365 pour macOS | Application de store (Office 365) | Sélectionnez **macOS** sous la **Suite Office 365** comme **type d’application**, puis sélectionnez la suite d’applications Office 365. |
| Applications métier Android | Application métier | Sélectionnez l’application **Métier** comme **type d’application**, sélectionnez le **fichier Package d’application**, puis entrez un fichier d’installation Android avec l’extension **.apk**.  |
| Applications métier iOS | Application métier | Sélectionnez l’application **Métier** comme **type d’application**, sélectionnez le **fichier Package d’application**, puis entrez un fichier d’installation iOS avec l’extension **.ipa**.  |
| Applications métier Windows Phone | Application métier | Sélectionnez l’application **Métier** comme **Type d’application**, sélectionnez le **fichier de package d’application**, puis entrez un fichier d’installation Windows Phone avec l’extension **.xap**.  |
| Applications métier Windows | Application métier | Sélectionnez l’application **Métier** comme type d’application, sélectionnez le **fichier de package d’application**, puis entrez un fichier d’installation Windows avec l’extension **.msi**, **.appx**, **.appxbundle**, **.msix** ou **.msixbundle**. |
| Application iOS intégrée  | Application intégrée | Sélectionnez **Application intégrée** comme **type d’application**, puis sélectionnez l’application intégrée dans la liste des applications fournies.  |
| Application Android intégrée  | Application intégrée | Sélectionnez **Application intégrée** comme **type d’application**, puis sélectionnez l’application intégrée dans la liste des applications fournies.  |
| Applications web  | Application web  | Sélectionnez **Lien web** comme **type d’application**, puis entrez une URL valide pointant vers l’application web.  |
| Application Windows (Win32)  | Application métier  | Sélectionnez **Application Windows (Win32)** comme **type d’application**, sélectionnez le **fichier Package d’application**, puis sélectionnez un fichier d’installation avec l’extension **.intunewin**.  |

Vous pouvez ajouter une application dans Microsoft Intune en sélectionnant **Applications clientes** > **Applications** > **Ajouter**. Le panneau **Ajouter une application** s’affiche et vous permet de sélectionner le **type d’application**. 

>[!TIP]
> Une application métier est une application que vous ajoutez à partir d’un fichier d’installation d’application. Par exemple, pour installer une application métier iOS, ajoutez l’application en sélectionnant **Application métier** comme **Type d’application** dans le panneau **Ajouter une application**. Sélectionnez ensuite le fichier de package d’application (extension .ipa). Ces types d’applications sont généralement écrites en interne.

## <a name="assess-app-requirements"></a>Évaluer les exigences relatives aux applications
En tant qu’administrateur informatique, vous devez déterminer non seulement les applications que votre groupe doit utiliser, mais aussi les fonctionnalités nécessaires pour chaque groupe et sous-groupe. Pour chaque application, déterminez les plateformes nécessaires, les groupes d’utilisateurs qui ont besoin de l’application, les stratégies de configuration à appliquer à ces groupes et les stratégies de protection à appliquer.  

Vous devez également déterminer si vous devez vous concentrer sur la gestion des appareils mobiles (MDM) ou uniquement sur la gestion des applications mobiles (MAM). 

Il est utile de gérer l’appareil à l’aide d’Intune avec MDM dans les cas suivants :
- Les utilisateurs ont besoin d’un profil Wi-Fi ou de connectivité d’entreprise VPN pour être productifs.
- Les utilisateurs ont besoin qu’un ensemble d’applications soit envoyé sur leur appareil.
- Votre organisation doit se conformer à des normes ou à des stratégies qui exigent des contrôles MDM spécifiques, tels que la sécurité ou le chiffrement.

Il est utile de gérer les applications à l’aide d’Intune avec MAM sans gérer l’appareil dans les cas suivants :
- Vous voulez permettre aux utilisateurs d’utiliser leur propre appareil (BYOD).
- Plutôt qu’une notification permanente au niveau de l’appareil, vous voulez fournir un message contextuel qui ne s’affiche qu’une seule fois pour indiquer aux utilisateurs que des protections MAM sont en place.
- Vous voulez vous conformer à des stratégies qui exigent moins de fonctionnalités de gestion sur les appareils personnels. Par exemple, vous voulez gérer les données d’entreprise pour les applications, au lieu de les gérer pour l’ensemble de l’appareil.

Pour plus d’informations, consultez [Comparer MDM et MAM](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Déterminer qui utilisera l’application

À mesure que vous déterminez les applications dont a besoin votre personnel, tenez compte des différents groupes d’utilisateurs qui existent et des différentes applications qu’ils utilisent. Le fait de connaître ces groupes s’avère également utile après l’ajout d’une application. Après avoir ajouté une application, affectez un groupe d’utilisateurs qui peut utiliser l’application. 

Vous devez d’abord déterminer le groupe qui doit avoir accès à l’application en fonction de la sensibilité des données que l’application contient. Vous devrez peut-être inclure ou exclure certains types de rôles au sein de votre organisation. Par exemple, seules certaines applications métier peuvent être nécessaires pour votre groupe de ventes, alors que les personnes travaillant essentiellement dans l’ingénierie, la finance, les ressources humaines ou le secteur juridique n’ont peut-être pas besoin d’utiliser les applications métier. De plus, votre groupe de ventes peut nécessiter une protection des données supplémentaires et un accès aux services d’entreprise internes sur leurs appareils mobiles. Vous devez déterminer la façon dont ce groupe se connectera aux ressources à l’aide de l’application. Les données auxquelles l’application accède sont-elles dans le cloud ou locales ? Par ailleurs, comment les utilisateurs vont-ils se connecter aux ressources avec l’application ? 

Intune prend également en charge l’activation de l’accès aux applications clientes qui nécessitent un accès sécurisé aux données locales, comme un serveur d’applications métier. Vous fournissez généralement ce type d’accès à l’aide de [certificats gérés par Intune](certificates-configure.md) pour le contrôle d’accès, combinés à une passerelle VPN standard ou à un proxy dans le périmètre, comme le proxy d’application Azure Active Directory. [L’outil de création de wrapping d’applications et le SDK d’application](apps-prepare-mobile-application-management.md) Intune peuvent vous aider à limiter les données utilisées dans votre application métier pour ne pas transmettre des données d’entreprise à des applications ou services de particuliers.

Utilisez le [Guide de planification, de conception et d’implémentation du déploiement Intune](planning-guide.md) pour déterminer la façon dont vous identifiez les groupes d’organisation qui sont associés à chaque scénario d’utilisation d’application principal et secondaire. Pour plus d’informations sur l’affectation d’applications à des groupes, consultez [Affecter des applications à des groupes avec Microsoft Intune](apps-deploy.md).

### <a name="determine-the-type-of-app-for-your-solution"></a>Déterminer le type d’application pour votre solution

Vous pouvez choisir parmi les types d’applications suivants :
- **Applications du store** : il s’agit d’applications qui ont été chargées sur le store Microsoft, iOS ou Android. Le fournisseur d’une application de store gère et fournit les mises à jour sur l’application. Vous sélectionnez l’application dans la liste de stores et vous l’ajoutez à l’aide d’Intune comme application disponible pour vos utilisateurs.
- **Applications écrites en interne (métier)** : les applications créées en interne sont des applications métier. Les fonctionnalités de ce type d’application ont été créées pour l’une des plateformes Intune prises en charge, comme Windows, iOS ou Android. Votre organisation crée et vous fournit des mises à jour dans un fichier distinct. Vous fournissez des mises à jour de l’application aux utilisateurs en ajoutant et en déployant les mises à jour à l’aide d’Intune.
- **Applications sur le web** : les applications web sont des applications client-serveur. Le serveur fournit l’application web, qui englobe l’interface utilisateur, le contenu et les fonctionnalités. De plus, les plateformes d’hébergement web modernes offrent généralement, entre autres avantages, la sécurité et l’équilibrage de charge. Ce type d’application est géré séparément sur le web. Vous utilisez Intune pour pointer vers ce type d’application. Vous affectez également les groupes d’utilisateurs qui peuvent accéder à l’application. Notez qu’Android ne prend pas en charge les applications web.

À mesure que vous déterminez les applications dont a besoin votre organisation, tenez compte de la façon dont les applications s’intègrent aux services cloud, des données auxquelles les applications accèdent, si les applications sont disponibles pour les utilisateurs BYOD et si les applications nécessitent un accès à Internet.

Pour plus d’informations sur les types d’applications dont a besoin votre organisation, consultez « Applications » dans la section « Exigences concernant les fonctionnalités » de [Créer un design](planning-guide-design.md#feature-requirements).

### <a name="understanding-app-management-and-protection-policies"></a>Présentation de la gestion des applications et des stratégies de protection
Intune vous permet de modifier les fonctionnalités des applications que vous déployez pour les mettre en phase avec les stratégies de conformité et de sécurité de votre entreprise. Ce contrôle vous permet de déterminer la façon dont les données de votre entreprise sont protégées. Les applications gérées par Intune sont activées avec un ensemble complet de stratégies de protection des applications mobiles, comme les suivantes :

- Restriction des fonctions Copier-coller et Enregistrer sous.
- Configuration des liens web pour qu’ils s’ouvrent dans l’application Intune Managed Browser.
- Activation de l’utilisation de plusieurs identités et de l’accès conditionnel au niveau de l’application.

Les applications gérées par Intune peuvent également activer la protection des applications sans inscription obligatoire, ce qui vous permet d’appliquer des stratégies de protection contre la perte de données sans gérer l’appareil de l’utilisateur. De plus, vous pouvez incorporer la gestion des applications mobiles à vos applications mobiles et métier à l’aide du SDK d’application Intune et de l’outil de wrapping d’applications. Pour plus d’informations sur ces outils, consultez [Vue d’ensemble du Kit de développement logiciel (SDK) des applications Intune](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Présentation des applications sous licence
En plus des applications Web, des applications de store et des applications métier, vous devez avoir connaissance de la destination des applications du programme d’achat en volume et des applications sous licence, notamment : 
- **Programme d’achat en volume Apple pour les entreprises (iOS)**  : l’App Store iOS vous permet d’acheter plusieurs licences d’une application que vous voulez exécuter dans votre entreprise. Le fait d’acheter plusieurs copies aide à gérer efficacement les applications de l’entreprise. Pour plus d’informations, consultez [Gérer les applications iOS achetées en volume](vpp-apps-ios.md).
- **Profil professionnel Android** : la façon dont vous affectez des applications à des appareils de profil professionnel Android diffère de celle dont vous les affectez à des appareils Android standard. Toutes les applications que vous installez pour des profils professionnels Android proviennent du Managed Google Play Store. Vous vous connectez au store, recherchez les applications souhaitées et les approuvez. L’application apparaît ensuite dans le nœud **Applications sous licence** du portail Azure, et vous pouvez gérer l’affectation de l’application de la même façon que pour toute autre application.
- **Microsoft Store pour Entreprises (Windows 10)** : le Microsoft Store pour Entreprises vous permet de rechercher et d’acheter des applications pour votre organisation, individuellement ou en volume. En connectant le store à Microsoft Intune, vous pouvez gérer les applications achetées en volume dans le portail Azure. Pour plus d’informations, consultez [Gérer des applications à partir du Microsoft Store pour Entreprises](windows-store-for-business.md).

    > [!NOTE]
    > Les extensions de fichier des applications Windows sont **.msi**, **.appx**, **.appxbundle**, **.msix** et **.msixbundle**.  

## <a name="before-you-add-apps"></a>Avant d'ajouter des applications
Avant de commencer à ajouter et affecter des applications, tenez compte des points suivants :

- Quand vous ajoutez et affectez une application à partir d’un store, vos utilisateurs doivent avoir un compte sur ce store pour pouvoir installer l’application.
- Certaines applications ou certains éléments que vous affectez peuvent dépendre d’applications iOS intégrées. Par exemple, si vous affectez un livre dans le store iOS, l’application iBooks doit être présente sur l’appareil. Si vous avez supprimé l’application iBook intégrée, vous ne pouvez pas utiliser Intune pour la réactiver.

> [!IMPORTANT]
> Si vous modifiez le nom de l’application sur le portail Intune Azure après l’avoir déployée et installée, vous ne pourrez plus la cibler à l’aide de commandes.

## <a name="cloud-storage-space"></a>Espace de stockage cloud
Toutes les applications que vous créez en utilisant le type d’installation de programme d’installation de logiciel (par exemple, une application métier) sont empaquetées et chargées dans le stockage cloud Intune. Un abonnement d’essai à Intune inclut 2 Go de stockage cloud, utilisé pour stocker les applications gérées et les mises à jour. Un abonnement complet ne limite pas la quantité totale d’espace de stockage.

La configuration requise pour l’espace de stockage cloud est la suivante :

- Tous les fichiers d’installation de l’application doivent être dans le même dossier.
- La taille maximale de chaque fichier que vous chargez s’élève à 8 Go.

## <a name="create-and-edit-categories-for-apps"></a>Créer et modifier des catégories pour les applications

Vous pouvez utiliser les catégories d’applications pour trier les applications, afin que les utilisateurs finaux puissent les trouver plus facilement dans le portail d’entreprise. Vous pouvez affecter une ou plusieurs catégories à une application, par exemple *Applications pour développeurs* ou *Applications de communication*.

Lorsque vous ajoutez une application à Intune, vous avez la possibilité de sélectionner la catégorie souhaitée. Utilisez les rubriques spécifiques à la plateforme pour ajouter une application et affecter des catégories. Pour créer et modifier vos propres catégories, procédez comme suit :

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, sélectionnez **Applications clientes**.
4. Dans le volet de la charge de travail **Applications clientes**, sous **Installation**, sélectionnez **Catégories d’applications**.  
    Le volet **Catégories d’applications** affiche la liste des catégories actuelles. 
5. Effectuez l'une des opérations suivantes :
    - Pour ajouter une catégorie, dans le volet **Créer une catégorie**, sélectionnez **Ajouter**, puis entrez un nom de catégorie.  
    Les noms ne peuvent être entrés que dans une seule langue et ne sont pas traduits par Intune.
    - Pour modifier une catégorie, sélectionnez les points de suspension (**...** ) à côté de la catégorie, puis **Épingler au tableau de bord** ou **Supprimer**.
6. Sélectionnez **Créer**.

## <a name="apps-that-are-added-automatically-by-intune"></a>Applications automatiquement ajoutées par Intune

Intune contenait auparavant un nombre d’applications intégrées que vous pouviez affecter rapidement. Après examen des commentaires des clients d’Intune, nous avons décidé de supprimer cette liste. Les applications intégrées ne sont donc plus affichées. Toutefois, si vous avez déjà affecté des applications intégrées, celles-ci restent visibles dans la liste des applications. Vous pouvez continuer à affecter les applications en fonction de vos besoins.

> [!NOTE]
> Pour une application obligatoire qui n’est pas une application métier, Intune tente de l’installer en envoyant une commande d’installation chaque fois que l’appareil s’enregistre. En effet, l’application n’est pas détectée et son état d’installation n’est pas *Installation en attente*.

## <a name="installing-updating-or-removing-required-apps"></a>Installation, mise à jour ou suppression d’applications obligatoires

Intune réinstalle, met à jour ou supprime automatiquement une application obligatoire en moins de 24 heures au lieu d’attendre le cycle de réévaluation de 7 jours.

Intune réinstalle, met à jour ou supprime automatiquement une application obligatoire dans les cas suivants :
- Si un utilisateur final désinstalle une application dont l’installation est exigée sur son appareil, Intune réinstalle automatiquement l’application une fois ce délai écoulé.
- En cas d’échec de l’installation d’une application obligatoire ou si cette dernière, pour une raison quelconque, est absente de l’appareil, Intune évalue la conformité et réinstalle l’application une fois ce délai écoulé.  
- Un administrateur met une application à la disposition d’un groupe d’utilisateurs, et un utilisateur final l’installe à partir du Portail d’entreprise sur l’appareil. L’administrateur fait ensuite passer l’application de la version v1 à la version v2. Une fois ce délai écoulé, Intune met à jour l’application si une version précédente de celle-ci est encore présente sur l’appareil.
- Si l’administrateur déploie une intention de désinstallation et que la désinstallation de l’application, présente sur l’appareil, échoue, Intune évalue la conformité et désinstalle l’application une fois ce délai écoulé.   

## <a name="app-installation-errors"></a>Erreurs d’installation des applications

Pour plus d’informations sur les erreurs d’installation des applications Intune, voir [Erreurs d’installation des applications](troubleshoot-app-install.md#app-installation-errors).

## <a name="next-steps"></a>Étapes suivantes

Pour savoir comment ajouter des applications pour chaque plateforme à Intune, consultez :

- [Applications de l’App Store Android](store-apps-android.md)
- [Applications métier Android](lob-apps-android.md)
- [Applications de l’App Store iOS](store-apps-ios.md)
- [Applications métier iOS](lob-apps-ios.md)
- [Applications Web (pour toutes les plateformes)](web-app.md)
- [Application du Windows Phone 8.1 Store](store-apps-windows-phone-8-1.md)
- [Applications métier Windows Phone](lob-apps-windows-phone.md)
- [Applications Microsoft Store](store-apps-windows.md)
- [Application métier Windows](lob-apps-windows.md)
- [Applications Office 365 pour Windows 10](apps-add-office365.md)
- [Applications Office 365 pour macOS](apps-add-office365-macos.md)
- [Applications intégrées](apps-add-built-in.md)
- [Applications Win32](apps-win32-app-management.md) 
