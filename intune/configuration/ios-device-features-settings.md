---
title: Paramètres des fonctionnalités d’appareil iOS/iPadOS dans Microsoft Intune - Azure | Microsoft Docs
description: 'Découvrez tous les paramètres à votre disposition pour configurer les fonctionnalités d’appareil iOS/iPadOS dans Microsoft Intune : AirPrint, disposition de l’écran d’accueil, notifications des applications, appareil partagé, authentification unique et filtre de contenu web. Utilisez ces paramètres dans un profil de configuration d’appareil pour configurer des appareils iOS/iPadOS et utiliser ces fonctionnalités Apple dans votre organisation.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7f19ccfb6949dbfa0de62a8b711436ab9cde8c9c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512940"
---
# <a name="ios-and-ipados-device-settings-to-use-common-iosipados-features-in-intune"></a>Paramètres des appareils iOS et iPadOS permettant d’utiliser les principales fonctionnalités d’iOS/iPadOS dans Intune

Intune inclut certains paramètres prédéfinis pour permettre aux utilisateurs d’utiliser différentes fonctionnalités Apple sur leurs appareils iOS/iPadOS. Par exemple, les administrateurs peuvent contrôler la façon dont les utilisateurs d’appareils iOS/iPadOS se servent des imprimantes AirPrint, ajoutent des applications et dossiers à l’écran d’accueil et aux pages de l’écran d’accueil, affichent les notifications d’applications, affichent les détails de l’étiquette d’inventaire sur l’écran de verrouillage, utilisent l’authentification unique et s’authentifient avec des certificats.

Utilisez ces fonctionnalités pour contrôler vos appareils iOS/iPadOS dans le cadre de votre solution de gestion des appareils mobiles.

Cet article liste ces paramètres et décrit le rôle de chaque paramètre. Pour plus d’informations sur ces fonctionnalités, consultez [Ajouter des paramètres de fonctionnalités d’appareils iOS/iPadOS ou macOS](../device-features-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil iOS/iPadOS](../device-features-configure.md).

> [!NOTE]
> Ces paramètres s’appliquent à différents types d’inscriptions, certains d’entre eux s’appliquant à toutes les options d’inscription. Pour plus d’informations sur les différents types d’inscriptions, consultez [Inscription iOS/iPadOS](../ios-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

> [!NOTE]
> Veillez à ajouter toutes les imprimantes au même profil. Apple empêche que plusieurs profils AirPrint ne ciblent le même appareil.

- **Adresse IP** : entrez l’adresse IPv4 ou IPv6 de l’imprimante. Si vous utilisez des noms d’hôte pour identifier les imprimantes, vous pouvez obtenir l’adresse IP en effectuant un test ping sur l’imprimante dans le Terminal. Pour plus de détails, consultez Obtenir l’adresse IP et le chemin dans cet article.
- **Chemin d’accès** : Le chemin est généralement `ipp/print` pour les imprimantes de votre réseau. Pour plus de détails, consultez Obtenir l’adresse IP et le chemin dans cet article.
- **Port** : entrez le port d’écoute de la destination AirPrint. Si vous ne renseignez pas cette propriété, AirPrint utilise le port par défaut. Disponible sur iOS 11.0+ et iPadOS 13.0+.
- **TLS** : choisissez **Activer** pour sécuriser les connexions AirPrint à l’aide du protocole TLS (Transport Layer Security). Disponible sur iOS 11.0+ et iPadOS 13.0+.

Pour ajouter des serveurs AirPrint, vous pouvez procéder comme suit :

- L’option **Ajouter** ajoute le serveur AirPrint à la liste. De nombreux serveurs AirPrint peuvent être ajoutés.
- **Importez** un fichier de valeurs séparées par des virgules (.csv) contenant ces informations. Ou **exportez** pour créer une liste des serveurs AirPrint que vous avez ajoutés.

### <a name="get-server-ip-address-resource-path-and-port"></a>Obtenir l’adresse IP, le chemin de ressource et le port du serveur

Pour ajouter des serveurs AirPrinter, vous avez besoin de l’adresse IP de l’imprimante, du chemin de la ressource et du port. Les étapes suivantes vous montrent comment obtenir ces informations.

1. Sur un Mac connecté au même réseau local (sous-réseau) que les imprimantes AirPrint, ouvrez le **Terminal** (à partir de **/Applications/Utilities**).
2. Dans le Terminal, tapez `ippfind` et appuyez sur Entrée.

    Notez les informations relatives à l’imprimante. La sortie obtenue peut ressembler à ceci : `ipp://myprinter.local.:631/ipp/port1`. La première partie est le nom de l’imprimante. La dernière partie (`ipp/port1`) est le chemin de la ressource.

3. Dans le Terminal, tapez `ping myprinter.local` et appuyez sur Entrée.

   Notez l’adresse IP. La sortie obtenue peut ressembler à ceci : `PING myprinter.local (10.50.25.21)`.

4. Utilisez les valeurs de l’adresse IP et du chemin de la ressource. Dans cet exemple, l’adresse IP est `10.50.25.21` et le chemin de ressource est `/ipp/port1`.

## <a name="home-screen-layout"></a>disposition de l’écran d’accueil

Cette fonctionnalité s’applique à :

- iOS 9.3 ou version ultérieure
- iPadOS 13.0 et ultérieur

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

### <a name="dock"></a>Ancrer

Utilisez les paramètres **Ancrer** pour ajouter jusqu’à six éléments ou dossiers à l’espace d’ancrage sur l’écran iOS/iPadOS. De nombreux appareils prennent cependant en charge moins d’éléments. Par exemple, les appareils iPhone acceptent un maximum de quatre éléments. Dans ce cas, seuls les quatre premiers éléments que vous avez ajoutés sont visibles sur l’appareil.

Vous pouvez ajouter jusqu’à **six** éléments (applications et dossiers combinés) à l’espace d’ancrage sur l’écran de l’appareil.

- **Ajouter** : ajoute des applications ou des dossiers à l’écran d’ancrage de l’appareil.
- **Type** : ajoutez une **application** ou un **dossier** :

  - **Application** : choisissez cette option pour ajouter des applications à l’espace d’ancrage sur l’écran. Entrez :

    - **Nom de l’application** : entrez le nom de l’application. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil iOS/iPadOS.
    - **ID de l'ensemble d'applications** : entrez l’ID de bundle de l’application. La section [ID de bundles pour des applications iOS/iPadOS intégrées](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

  - **Dossier** : choisissez cette option pour ajouter un dossier à l’espace d’ancrage sur l’écran.

    Les applications que vous ajoutez à une page dans un dossier sont organisées de gauche à droite, dans le même ordre que dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une autre page.

    - **Nom du dossier** : Entrez le nom du dossier. Ce nom est visible sur l’appareil des utilisateurs.
    - **Liste de pages** : **Ajoutez** une page et entrez les propriétés suivantes :

      - **Nom de la page** : entrez un nom pour la page. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil iOS/iPadOS.
      - **Nom de l’application** : entrez le nom de l’application. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil iOS/iPadOS.
      - **ID de l'ensemble d'applications** : entrez l’ID de bundle de l’application. La section [ID de bundles pour des applications iOS/iPadOS intégrées](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

      Vous pouvez ajouter jusqu’à **20** pages à l’espace d’ancrage sur l’écran de l’appareil.

> [!NOTE]
> Lorsque vous ajoutez des icônes à l’aide des paramètres d’ancrage, les icônes présentes sur l’écran d’accueil et sur les pages sont verrouillées et ne peuvent pas être déplacées. Cela peut faire partie des stratégies de gestion des appareils mobiles iOS/iPadOS et Apple.

#### <a name="example"></a>Exemple

Dans l’exemple suivant, l’écran d’ancrage montre uniquement les applications Safari, Mail et Bourse. L’application Mail est sélectionnée et ses propriétés sont affichées :

![Exemples de paramètres d’ancrage iOS/iPadOS](./media/ios-device-features-settings/FfFiUcP.png)

Quand vous affectez la stratégie à un iPhone, l’espace d’ancrage est semblable à cette image :

![Exemple de disposition d’ancrage iOS/iPadOS sur iPhone](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>Pages

Ajoutez les pages que vous souhaitez afficher sur l’écran d’accueil et les applications à afficher dans chaque page. Les applications que vous ajoutez à une page sont organisées de gauche à droite, dans le même ordre que dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une autre page.

> [!TIP]
> Pour réorganiser les éléments dans l’écran d’accueil et dans les listes de pages, vous pouvez les déplacer en les faisant glisser.

Vous pouvez ajouter jusqu’à **40** pages sur un appareil.

- **Liste de pages** : **Ajoutez** une page et entrez les propriétés suivantes :

  - **Nom de la page** : entrez un nom pour la page. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire des points de terminaison de Microsoft et *n’est pas* affiché sur l’appareil iOS/iPadOS.

  Vous pouvez ajouter jusqu’à **60** éléments (applications et dossiers combinés) sur un appareil.

  - **Ajouter** : ajoute des applications ou des dossiers à une page sur l’appareil.

    - **Type** : ajoutez une **application** ou un **dossier** :

      - **Application** : Choisissez cette option pour ajouter des applications à une page sur l’écran. Entrez également :

        - **Nom de l’application** : entrez le nom de l’application. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil iOS/iPadOS.
        - **ID de l'ensemble d'applications** : entrez l’ID de bundle de l’application. La section [ID de bundles pour des applications iOS/iPadOS intégrées](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

      - **Dossier** : choisissez cette option pour ajouter un dossier à l’espace d’ancrage sur l’écran.

        Les applications que vous ajoutez à une page dans un dossier sont organisées de gauche à droite, dans le même ordre que dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une autre page.

        - **Nom du dossier** : Entrez le nom du dossier. Ce nom est visible sur l’appareil des utilisateurs.
        - **Ajouter** : ajoute des pages au dossier. Indiquez également les propriétés suivantes :

          - **Nom de la page** : entrez un nom pour la page. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil iOS/iPadOS.
          - **Nom de l’application** : entrez le nom de l’application. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil iOS/iPadOS.
          - **ID de l'ensemble d'applications** : entrez l’ID de bundle de l’application. La section [ID de bundles pour des applications iOS/iPadOS intégrées](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

#### <a name="example"></a>Exemple

Dans l’exemple suivant, une nouvelle page nommée **Contoso** est ajoutée. La page affiche les applications Trouver des amis et Réglages. L’application Réglages est sélectionnée et ses propriétés sont affichées :

![Exemple de paramètres de l’écran d’accueil iOS/iPadOS dans Intune](./media/ios-device-features-settings/Jc2OxyX.png)

Quand vous affectez la stratégie à un iPhone, la page est semblable à cette image :

![Appareil iOS/iPadOS avec écran d’accueil modifié dans Intune](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>Notifications d’applications

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Ajouter** : ajoutez des notifications pour les applications :

    ![Ajouter une notification d’application au profil iOS/iPadOS dans Intune](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **ID de l’ensemble d’applications** : entrez l’**ID d’ensemble d’applications** pour l’application que vous souhaitez ajouter. La section [ID de bundles pour des applications iOS/iPadOS intégrées](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.
  - **Nom de l’application** : entrez le nom de l’application que vous voulez ajouter. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil.
  - **Éditeur** : entrez le nom de l’éditeur de l’application ajoutée. Ce nom est utilisé pour votre référence dans le centre d’administration du Gestionnaire de points de terminaison Microsoft. Il *n’est pas* visible sur l’appareil.
  - **Notifications** : choisissez **Activer** ou **Désactiver** pour autoriser ou empêcher l’envoi de notifications entre l’application et l’appareil.
    - **Afficher dans le centre de notifications** : choisissez **Activer** pour autoriser l’application à afficher des notifications dans le centre de notifications de l’appareil. Choisissez **Désactiver** pour l’en empêcher.
    - **Afficher dans l’écran de verrouillage** : choisissez **Activer** pour autoriser l’application à afficher des notifications dans l’écran de verrouillage de l’appareil. Choisissez **Désactiver** pour l’en empêcher.
    - **Type d’alerte** : choisissez le mode d’affichage de la notification quand l’appareil est déverrouillé. Les options disponibles sont les suivantes :
      - **Aucune** : aucune notification ne s’affiche.
      - **Bannière** : Une bannière s’affiche brièvement avec la notification.
      - **Modal** : la notification s’affiche et l’utilisateur doit la fermer manuellement pour pouvoir continuer à utiliser l’appareil.
    - **Badge sur l’icône de l’application** : sélectionnez **Activer** pour ajouter un badge à l’icône de l’application. Le badge indique que l’application a envoyé une notification.
    - **Sons** : choisissez **Activer** pour qu’un son soit émis à la réception d’une notification.

## <a name="lock-screen-message"></a>Message d’écran de verrouillage

Cette fonctionnalité s’applique à :

- iOS 9.3 et version ultérieure
- iPadOS 13.0 et ultérieur

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Informations de l’étiquette d’inventaire** : entrez des informations sur l’étiquette d’inventaire de l’appareil. Par exemple, entrez `Owned by Contoso Corp` ou `Serial Number: {{serialnumber}}`.

  Le texte que vous entrez est affiché sur l’écran de verrouillage et dans la fenêtre de connexion de l’appareil.

- **Note de l’écran de verrouillage** : entrez une note qui pourrait vous aider à récupérer l’appareil en cas de perte ou de vol. Vous pouvez entrer n’importe quel texte. Par exemple, entrez quelque chose du genre `If found, call Contoso at ...`.

  Vous pouvez aussi utiliser des jetons d’appareil pour ajouter des informations propres à l’appareil dans ces champs. Par exemple, pour afficher le numéro de série, entrez `Serial Number: {{serialnumber}}`. L’écran de verrouillage affichera le texte `Serial Number 123456789ABC`. Quand vous entrez les variables, veillez à utiliser des accolades `{{ }}`. [Jetons de configuration d’application](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) inclut une liste de variables qui peuvent être utilisées. Vous pouvez également utiliser `deviceName` ou toute autre valeur propre à l’appareil.

  > [!NOTE]
  > Les variables ne sont pas validées dans l’interface utilisateur et respectent la casse. Par conséquent, vous pouvez voir des profils enregistrés avec une entrée incorrecte. Par exemple, si vous entrez `{{DeviceID}}` au lieu de `{{deviceid}}`, la chaîne littérale s’affiche à la place de l’ID unique de l’appareil. Veillez à entrer les informations correctes.

## <a name="single-sign-on"></a>Authentification unique

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Attribut de nom d’utilisateur d’AAD** : Intune recherche cet attribut pour chaque utilisateur dans Azure AD. Ensuite, Intune remplit le champ correspondant (par exemple, UPN) avant de générer le XML installé sur l’appareil. Les options disponibles sont les suivantes :

  - **Nom d’utilisateur principal** : l’UPN est analysé de la façon suivante :

    ![Attribut SSO de nom d’utilisateur iOS/iPadOS dans Intune](./media/ios-device-features-settings/User-name-attribute.png)

    Vous pouvez également remplacer le domaine par le texte que vous entrez dans la zone de texte **Domaine**.

    Par exemple, Contoso a plusieurs régions, dont Europe, Asie et Amérique du Nord. Contoso souhaite que les utilisateurs en Asie utilisent l’authentification unique et que l’application exige que le nom d’utilisateur principal soit au format `username@asia.contoso.com`. Quand vous sélectionnez **Nom d’utilisateur principal**, le domaine pour chaque utilisateur est extrait d’Azure AD (ici, c’est `contoso.com`). Par conséquent, pour les utilisateurs en Asie, sélectionnez **Nom d’utilisateur principal**, puis entrez `asia.contoso.com`. Le nom d’utilisateur principal de l’utilisateur final est maintenant `username@asia.contoso.com`, au lieu de `username@contoso.com`.

  - **ID d’appareil Intune** : Intune sélectionne automatiquement l’ID d’appareil Intune.

    Par défaut, les applications ont besoin d’utiliser uniquement l’ID d’appareil. Mais si votre application utilise le domaine et l’ID d’appareil, vous pouvez taper le domaine dans la zone de texte Domaine.

    > [!NOTE]
    > Par défaut, vous devez laisser le champ de domaine vide si vous utilisez l’ID d’appareil.

  - **ID d’appareil Azure AD**

- **Domaine** : entrez la partie domaine de l’URL. Par exemple, entrez `contoso.com`.
- **Préfixes d’URL qui utiliseront l’authentification unique** : choisissez **Ajouter** pour ajouter les URL de votre organisation qui exigeront une authentification unique de l’utilisateur.

  Par exemple, quand un utilisateur se connecte à l’un de ces sites, l’appareil iOS/iPadOS utilise les informations d’identification d’authentification unique. L’utilisateur n’a pas besoin d’entrer d’informations d’identification supplémentaires. Si l’authentification multifacteur est activée, les utilisateurs doivent entrer la deuxième authentification.

  > [!NOTE]
  > Ces URL doivent être spécifiées sous la forme de noms de domaine complets correctement mis en forme. Apple exige qu’elles soient spécifiées au format `http://<yourURL.domain>`.

  Les modèles de correspondance d’URL doivent commencer par `http://` ou `https://`. Une correspondance de chaîne simple est lancée pour que le préfixe d’URL `http://www.contoso.com/` ne corresponde pas à `http://www.contoso.com:80/`. Avec iOS 10.0+ et iPadOS 13.0+, vous pouvez utiliser un seul caractère générique (\*) pour entrer toutes les valeurs correspondantes. Par exemple, `http://*.contoso.com/` correspond à la fois à `http://store.contoso.com/` et à `http://www.contoso.com`.

  Les modèles `http://.com` et `https://.com` correspondent respectivement à toutes les URL HTTP et HTTPS.

- **Applications qui utiliseront l’authentification unique** : choisissez **Ajouter** pour ajouter les applications sur les appareils des utilisateurs finaux qui seront autorisées à utiliser l’authentification unique.

  Le tableau `AppIdentifierMatches` doit inclure des chaînes qui correspondent aux ID de bundles d’applications. Ces chaînes peuvent être des correspondances exactes (comme `com.contoso.myapp`). Sinon, entrez une correspondance de préfixe sur l’ID de bundle à l’aide du caractère générique \*. Le caractère générique doit être placé après un point (.) et doit être utilisé une seule fois, à la fin de la chaîne, comme dans `com.contoso.*`. Quand un caractère générique est inclus, toute application dont l’ID de bundle commence par le préfixe bénéficie de l’accès au compte.

  Utilisez **Nom de l’application** pour entrer un nom convivial afin de faciliter l’identification de l’ID de bundle.

- **Certificat de renouvellement des informations d’identification** : si vous utilisez des certificats pour l’authentification (au lieu de mots de passe), sélectionnez le certificat SCEP ou PFX existant comme certificat d’authentification. En général, ce certificat est le même que celui déployé pour l’utilisateur dans d’autres profils, tels que VPN, WiFi ou e-mail.

## <a name="web-content-filter"></a>Filtrage de contenu web

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Type de filtre** : choisissez les sites web spécifiques que vous voulez autoriser. Les options disponibles sont les suivantes :

  - **Configurer les URL** : utilisez le filtre web intégré d’Apple qui recherche la présence de contenu pour adultes, notamment les propos blasphématoires et sexuellement explicites. Cette fonctionnalité analyse chaque page web qui est chargée afin de détecter et bloquer les contenus inappropriés. Vous pouvez également ajouter les URL que vous souhaitez exclure du filtrage, ou bien bloquer certaines URL, indépendamment des paramètres de filtre d’Apple.

    - **URL autorisées** : choisissez **Ajouter** pour ajouter les URL que vous souhaitez autoriser. Ces URL ignorent le filtre web d’Apple.

        > [!NOTE]
        > Les URL que vous entrez ici sont les URL qui ne seront pas analysées par le filtre web d’Apple. Elles ne correspondent pas à des sites web autorisés. Pour créer une liste des sites web autorisés, définissez **Type de filtre** sur **Sites web spécifiques uniquement**.

    - **URL bloquées** : choisissez **Ajouter** pour ajouter les URL dont vous souhaitez empêcher l’ouverture, indépendamment des paramètres de filtre web d’Apple.

  - **Sites web spécifiques uniquement** (pour le navigateur web Safari uniquement) : ces URL sont ajoutées aux signets du navigateur Safari. L’utilisateur est **uniquement** autorisé à accéder à ces sites ; il ne peut ouvrir aucun autre site. Utilisez cette option uniquement si vous connaissez la liste exacte des URL auxquelles les utilisateurs peuvent accéder.

    - **URL** : entrez l’URL du site web que vous souhaitez autoriser. Par exemple, entrez `https://www.contoso.com`.
    - **Chemin du signet** : Apple a modifié ce paramètre. Tous les signets sont placés dans le dossier **Sites approuvés**. Les signets n’entrent pas dans le chemin de signet que vous saisissez.
    - **Titre** : entrez un titre descriptif pour le signet.

    Si vous n’entrez pas d’URL, les utilisateurs finaux ne pourront accéder à aucun site web à l’exception de `microsoft.com`, `microsoft.net` et `apple.com`. Ces URL sont automatiquement autorisées par Intune.

## <a name="single-sign-on-app-extension"></a>Extension d’application d’authentification unique

Cette fonctionnalité s’applique à :

- iOS 13.0 et versions ultérieures
- IPadOS 13.0 et versions ultérieures

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Type d’extension d’application SSO** : choisissez le type d’extension d’application SSO. Les options disponibles sont les suivantes :

  - **Non configuré** : les extensions d’application ne sont pas utilisées. Pour désactiver une extension d’application, vous pouvez basculer le type d’extension d’application SSO sur **Non configuré**.
  - **Redirection** : utilisez une extension d’application de redirection générique et personnalisable pour effectuer une authentification unique avec des flux d’authentification modernes. Veillez à connaître l’ID d’extension de l’extension d’application de votre organisation.
  - **Informations d’identification** : utilisez une extension d’application d’informations d’identification générique et personnalisable pour exécuter l’authentification unique avec des flux d’authentification de type challenge et réponse. Veillez à connaître l’ID d’extension de l’extension d’application de votre organisation.
  - **Kerberos** : utilisez l’extension Kerberos intégrée d’Apple, qui est incluse dans iOS 13.0+ et iPadOS 13.0+. Cette option est une version spécifique à Kerberos de l’extension d’application **Informations d’identification**.

  > [!TIP]
  > Avec les types **Redirection** et **Informations d’identification**, vous ajoutez vos propres valeurs de configuration pour transférer directement l’extension. Si vous utilisez **Informations d’identification**, envisagez d’utiliser les paramètres de configuration intégrés fournis par Apple dans le type **Kerberos**.

- **ID d’extension** (Redirection et Informations d’identification) : entrez l’identificateur de bundle qui identifie votre extension d’application SSO, par exemple `com.apple.extensiblesso`.

- **ID d’équipe** (Redirection et Informations d’identification) : entrez l’identificateur d’équipe de votre extension d’application SSO. Un identificateur d’équipe est une chaîne de 10 caractères alphanumériques (nombres et lettres) générée par Apple, par exemple `ABCDE12345`. L’ID d’équipe n’est pas obligatoire.

  Pour plus d’informations, consultez [Rechercher votre ID d’équipe](https://help.apple.com/developer-account/#/dev55c3c710c) (qui ouvre le site web d’Apple).

- **Zone** (Informations d’identification et Kerberos) : entrez le nom de votre zone d’authentification. Le nom de zone doit être en majuscules, par exemple `CONTOSO.COM`. En règle générale, le nom de votre zone est le même que votre nom de domaine DNS, mais en majuscules.

- **Domaines** (Informations d’identification et Kerberos) : entrez les noms de domaine ou d’hôte des sites qui peuvent s’authentifier par le biais de l’authentification unique. Par exemple, si votre site web est `mysite.contoso.com`, alors `mysite` est le nom d’hôte et `contoso.com` est le nom de domaine. Lorsque les utilisateurs se connectent à l’un de ces sites, l’extension d’application gère le challenge d’authentification. Cette authentification permet aux utilisateurs d’utiliser Face ID, Touch ID ou le code PIN/code d’accès Apple pour se connecter.

  - Tous les domaines de vos profils Intune d’extension d’application d’authentification unique doivent être uniques. Vous ne pouvez pas répéter un domaine dans un profil d’extension d’application de connexion, même si vous utilisez différents types d’extensions d’application SSO.
  - Ces domaines ne respectent pas la casse.

- **URL** (Redirection uniquement) : entrez les préfixes d’URL de vos fournisseurs d’identité au nom desquels l’extension d’application de redirection effectue l’authentification unique. Lorsqu’un utilisateur est redirigé vers ces URL, l’extension de l’application SSO intervient et invite à effectuer l’authentification unique.

  - Toutes les URL dans vos profils d’extension d’application d’authentification unique Intune doivent être uniques. Vous ne pouvez pas répéter un domaine dans un profil d’extension d’application SSO, même si vous utilisez différents types d’extensions d’application SSO.
  - Les URL doivent commencer par http:// ou https://.

- **Configuration supplémentaire** (Redirection et Informations d’identification) : entrez les données supplémentaires spécifiques à l’extension à passer à l’extension de l’application SSO :
  - **Clé** : entrez le nom de l’élément que vous souhaitez ajouter, par exemple `user name`.
  - **Type** : entrez le type de données. Les options disponibles sont les suivantes :

    - Chaîne
    - Booléen : dans **Valeur de configuration**, entrez `True` ou `False`.
    - Entier : dans **Valeur de configuration**, entrez un nombre.
    
  - **Valeur** : entrez les données.

  - **Ajouter** : sélectionnez cette option pour ajouter vos clés de configuration.

- **Utilisation de trousseau** (Kerberos uniquement) : choisissez **Bloquer** pour empêcher l’enregistrement et le stockage des mots de passe dans le trousseau. **Non configuré** (valeur par défaut) permet d’enregistrer et de stocker les mots de passe dans le trousseau.
- **Face ID, Touch ID ou code d’accès** (Kerberos uniquement) : l’option **Exiger** oblige les utilisateurs à entrer leur code d’accès Face ID, Touch ID ou Apple pour se connecter aux domaines que vous avez ajoutés. **Non configuré** (valeur par défaut) n’oblige pas les utilisateurs à utiliser la biométrie ou le code d’accès pour se connecter.
- **Zone par défaut** (Kerberos uniquement) : choisissez **Activer** pour définir la valeur **Zone** que vous avez entrée comme zone par défaut. **Non configuré** (valeur par défaut) ne définit pas de zone par défaut.

  > [!TIP]
  > - **Activez** ce paramètre si vous configurez plusieurs extensions d’application SSO Kerberos dans votre organisation.
  > - **Activez** ce paramètre si vous utilisez plusieurs zones. Il définit la valeur **Zone** que vous avez entrée comme zone par défaut.
  > - Si vous n’avez qu’une seule zone, conservez l’option **Non configuré** (valeur par défaut).

- **Nom du principal** (Kerberos uniquement) : entrez le nom d’utilisateur du principal Kerberos. Vous n’avez pas besoin d’inclure le nom de zone. Par exemple, dans `user@contoso.com`, `user` est le nom du principal et `contoso.com` le nom de zone.

  > [!TIP]
  > - Vous pouvez également utiliser des variables dans le nom du principal en entrant des accolades `{{ }}`. Par exemple, pour afficher le nom d’utilisateur, entrez `Username: {{username}}`. 
  > - Toutefois, soyez vigilant avec la substitution de variable, car les variables ne sont pas validées dans l’interface utilisateur et sont sensibles à la casse. Veillez à entrer les informations correctes.

- **Code de site Active Directory** (Kerberos uniquement) : entrez le nom du site Active Directory que l’extension Kerberos doit utiliser. Vous n’aurez peut-être pas besoin de modifier cette valeur, car l’extension Kerberos peut trouver automatiquement le code de site Active Directory.
- **Nom du cache** (Kerberos uniquement) : entrez le nom des services de sécurité générique (GSS) du cache Kerberos. Vous n’avez probablement pas besoin de définir cette valeur.
- **ID de bundle d’applications** (Kerberos uniquement) : **ajoutez** les identificateurs de bundle d’applications qui doivent utiliser l’authentification unique sur vos appareils. Ces applications sont autorisées à accéder à Kerberos Ticket Granting Ticket, le ticket d’authentification, et à authentifier les utilisateurs auprès des services auxquels ils sont autorisés à accéder.
- **Mappage de zone de domaine** (Kerberos uniquement) : **ajoutez** les suffixes DNS de domaine qui doivent être mappés à votre zone. Utilisez ce paramètre lorsque les noms DNS des hôtes ne correspondent pas au nom de zone. Vous n’avez probablement pas besoin de créer ce mappage domaine-zone personnalisé.
- **Certificat PKINIT** (Kerberos uniquement) : **sélectionnez** le certificat PKINIT (chiffrement de clé publique pour l’authentification initiale) qui peut être utilisé pour l’authentification Kerberos. Vous pouvez choisir parmi les certificats [PKCS](../protect/certficates-pfx-configure.md) ou [SCEP](../protect/certificates-scep-configure.md) que vous avez ajoutés dans Intune. Pour plus d’informations sur les certificats, consultez [Utiliser des certificats pour l’authentification dans Microsoft Intune](../protect/certificates-configure.md).

## <a name="wallpaper"></a>Papier peint

Vous pouvez constater un comportement inattendu quand un profil sans image est affecté à des appareils ayant une image existante. Par exemple, vous créez un profil sans image. Ce profil est affecté à des appareils qui disposent déjà d’une image. Dans ce scénario, l’image peut être remplacée par l’appareil par défaut, ou l’image d’origine peut rester sur l’appareil. Ce comportement est contrôlé et limité par la plateforme MDM d’Apple.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Emplacement d’affichage du papier peint** : choisissez un emplacement où afficher l’image sur l’appareil. Les options disponibles sont les suivantes :
  - **Non configuré** : aucune image personnalisée n’est ajoutée sur l’appareil. L’appareil utilise l’image par défaut du système d’exploitation.
  - **Écran de verrouillage** : ajoute l’image à l’écran de verrouillage.
  - **Écran d’accueil** : ajoute l’image à l’écran d’accueil.
  - **Écran de verrouillage et écran d’accueil** : la même image est utilisée sur l’écran de verrouillage et l’écran d’accueil.
- **Image de papier peint** : chargez une image .png, .jpg ou .jpeg existante à utiliser. La taille du fichier doit être inférieure à 750 Ko. Vous pouvez **supprimer** une image que vous aviez ajoutée.

> [!TIP]
> Pour afficher des images différentes sur l’écran de verrouillage et l’écran d’accueil, créez un profil avec l’image de l’écran de verrouillage, et un autre profil avec l’image de l’écran d’accueil. Attribuez les deux profils à l’utilisateur ou aux groupes d’appareils iOS/iPadOS souhaités.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](../device-profile-assign.md) et [suivre son état](../device-profile-monitor.md).

Vous pouvez aussi créer des profils de fonctionnalités d’appareil pour les appareils [macOS](macos-device-features-settings.md).
