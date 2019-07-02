---
title: Paramètres des fonctionnalités d’appareil iOS dans Microsoft Intune - Azure | Microsoft Docs
description: 'Découvrez tous les paramètres à votre disposition pour configurer les fonctionnalités d’appareil iOS dans Microsoft Intune : AirPrint, disposition de l’écran d’accueil, notifications des applications, appareil partagé, authentification unique et filtre de contenu web. Définissez ces paramètres dans un profil de configuration d’appareil pour activer ces différentes fonctionnalités Apple sur les appareils iOS utilisés dans votre organisation.'
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43b87a90f90130a014817819b87ed5946b1ba15b
ms.sourcegitcommit: 9c06d8071b9affeda32e367bfe85d89bc524ed0b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413807"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>Paramètres des appareils iOS permettant d’utiliser les principales fonctionnalités d’iOS dans Intune

Intune inclut certains paramètres prédéfinis pour permettre aux utilisateurs d’utiliser différentes fonctionnalités Apple sur leurs appareils iOS. Par exemple, les administrateurs peuvent contrôler la façon dont les utilisateurs d’appareils iOS se servent des imprimantes AirPrint, ajoutent des applications et dossiers à l’écran d’accueil et aux pages de l’écran d’accueil, affichent les notifications d’applications, affichent les détails de l’étiquette d’inventaire sur l’écran de verrouillage, utilisent l’authentification unique et s’authentifient avec des certificats.

Utilisez ces fonctionnalités pour contrôler vos appareils iOS dans le cadre de votre solution de gestion des appareils mobiles.

Cet article liste ces paramètres et décrit le rôle de chaque paramètre.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil iOS](device-features-configure.md#create-a-device-profile).

## <a name="airprint"></a>AirPrint

- **Adresse IP** : entrez l’adresse IPv4 ou IPv6 de l’imprimante. Si vous utilisez des noms d’hôte pour identifier les imprimantes, vous pouvez obtenir l’adresse IP en effectuant un test ping sur l’imprimante dans le Terminal. Pour plus de détails, consultez Obtenir l’adresse IP et le chemin dans cet article.
- **Chemin d’accès** : de manière générale, le chemin est `ipp/print` pour les imprimantes de votre réseau. Pour plus de détails, consultez Obtenir l’adresse IP et le chemin dans cet article.
- **Port** : entrez le port d’écoute de la destination AirPrint. Si vous ne renseignez pas cette propriété, AirPrint utilise le port par défaut. Disponible sur iOS 11.0 et ultérieur.
- **Protocole TLS** : choisissez **Activer** pour sécuriser les connexions AirPrint à l’aide du protocole TLS (Transport Layer Security). Disponible sur iOS 11.0 et ultérieur.

L’option **Ajouter** ajoute le serveur AirPrint à la liste. Vous pouvez ajouter plusieurs serveurs AirPrint. Vous pouvez également **importer** un fichier de valeurs séparées par des virgules (.csv) contenant ces informations. Après avoir créé la liste, vous pouvez aussi **exporter** votre liste de serveurs AirPrint.

Sélectionnez **OK** pour enregistrer votre liste.

### <a name="get-server-ip-address-resource-path-and-port"></a>Obtenir l’adresse IP, le chemin de ressource et le port du serveur

Pour ajouter des serveurs AirPrinter, vous avez besoin de l’adresse IP de l’imprimante, du chemin de la ressource et du port. Les étapes suivantes vous montrent comment obtenir ces informations.

1. Sur un Mac connecté au même réseau local (sous-réseau) que les imprimantes AirPrint, ouvrez le **Terminal** (à partir de **/Applications/Utilities**).
2. Dans le Terminal, tapez `ippfind` et appuyez sur Entrée.

    Notez les informations relatives à l’imprimante. La sortie obtenue peut ressembler à ceci : `ipp://myprinter.local.:631/ipp/port1`. La première partie est le nom de l’imprimante. La dernière partie (`ipp/port1`) est le chemin de la ressource.

3. Dans le Terminal, tapez `ping myprinter.local` et appuyez sur Entrée.

   Notez l’adresse IP. La sortie obtenue peut ressembler à ceci : `PING myprinter.local (10.50.25.21)`.

4. Utilisez les valeurs de l’adresse IP et du chemin de la ressource. Dans cet exemple, l’adresse IP est `10.50.25.21` et le chemin de la ressource est `/ipp/port1`.

## <a name="home-screen-layout-settings"></a>Paramètres de disposition de l’écran d’accueil

Ces paramètres configurent la disposition des applications et des dossiers sur les écrans d’ancrage et d’accueil des appareils iOS. Pour utiliser cette fonctionnalité, les appareils iOS doivent être en mode supervisé et exécuter iOS 9.3 ou une version ultérieure.

### <a name="dock"></a>Ancrer

Utilisez les paramètres **Ancrer** pour ajouter jusqu’à six éléments ou dossiers à l’espace d’ancrage sur l’écran iOS. De nombreux appareils prennent cependant en charge moins d’éléments. Par exemple, les appareils iPhone acceptent un maximum de quatre éléments. Dans ce cas, seuls les quatre premiers éléments que vous avez ajoutés sont visibles sur l’appareil.

Vous pouvez ajouter jusqu’à **six** éléments (applications et dossiers combinés) à l’espace d’ancrage sur l’écran de l’appareil.

- **Ajouter** : ajoute des applications ou des dossiers à l’écran d’ancrage de l’appareil.
- **Type** : ajoute une **application** ou un **dossier**.

  - **Application** : cette option permet d’ajouter des applications à l’espace d’ancrage de l’écran. entrez :

    - **Nom de l’application** : entrez un nom pour l’application. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil iOS.
    - **ID d’ensemble d’applications** : entrez l’ID d’ensemble de l’application. La section [ID d’offres groupées pour des applications iOS intégrées que vous pouvez utiliser dans Intune](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

    Cliquez sur **OK** pour enregistrer vos modifications.

  - **Dossier** : choisissez cette option pour ajouter un dossier à l’espace d’ancrage de l’écran.

    Les applications que vous ajoutez à une page dans un dossier sont organisées de gauche à droite, dans le même ordre que dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une autre page.

    - **Nom du dossier** : entrez le nom du dossier. Ce nom est visible sur l’appareil des utilisateurs.
    - **Liste de pages** : **ajoutez** une page, puis indiquez les propriétés suivantes :

      - **Nom de la page** : entrez un nom pour la page. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil iOS.
      - **Nom de l’application** : entrez un nom pour l’application. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil iOS.
      - **ID d’ensemble d’applications** : entrez l’ID d’ensemble de l’application. La section [ID d’offres groupées pour des applications iOS intégrées que vous pouvez utiliser dans Intune](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

      Vous pouvez ajouter jusqu’à **20** pages à l’espace d’ancrage sur l’écran de l’appareil.

    Cliquez sur **OK** pour enregistrer vos modifications.

> [!NOTE]
> Lorsque vous ajoutez des icônes à l’aide des paramètres d’ancrage, les icônes présentes sur l’écran d’accueil et sur les pages sont verrouillées et ne peuvent pas être déplacées. Cet ancrage peut faire partie des stratégies de gestion des appareils mobiles iOS et Apple.

#### <a name="example"></a>Exemple

Dans l’exemple suivant, l’écran d’ancrage montre uniquement les applications Safari, Mail et Bourse. L’application Mail est sélectionnée et ses propriétés sont affichées :

![Exemples de paramètres d’ancrage iOS](./media/FfFiUcP.png)

Quand vous affectez la stratégie à un iPhone, l’espace d’ancrage est semblable à cette image :

![Exemple de disposition d’ancrage iOS sur iPhone](./media/bAgCe8F.png)

### <a name="pages"></a>Pages

Ajoutez les pages que vous souhaitez afficher sur l’écran d’accueil et les applications à afficher dans chaque page. Les applications que vous ajoutez à une page sont organisées de gauche à droite, dans le même ordre que dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une autre page.

> [!TIP]
> Pour réorganiser les éléments dans l’écran d’accueil et dans les listes de pages, vous pouvez les déplacer en les faisant glisser.

Vous pouvez ajouter jusqu’à **40** pages sur un appareil.

- **Liste de pages** : **ajoutez** une page, puis indiquez les propriétés suivantes :

  - **Nom de la page** : entrez un nom pour la page. Ce nom est utilisé à titre de référence dans le portail Azure, mais il *n’est pas* visible sur l’appareil iOS.

  Vous pouvez ajouter jusqu’à **60** éléments (applications et dossiers combinés) sur un appareil.

  - **Ajouter** : ajoute des applications ou des dossiers à une page sur l’appareil.

    - **Type** : ajoute une **application** ou un **dossier**.

      - **Application** : choisissez cette option pour ajouter des applications à une page sur l’écran. Entrez également :

        - **Nom de l’application** : entrez un nom pour l’application. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil iOS.
        - **ID d’ensemble d’applications** : entrez l’ID d’ensemble de l’application. La section [ID d’offres groupées pour des applications iOS intégrées que vous pouvez utiliser dans Intune](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

      Cliquez sur **OK** pour enregistrer vos modifications.

      - **Dossier** : choisissez cette option pour ajouter un dossier à l’espace d’ancrage de l’écran.

        Les applications que vous ajoutez à une page dans un dossier sont organisées de gauche à droite, dans le même ordre que dans la liste. Si vous ajoutez plus d’applications que la page ne peut en contenir, les applications sont déplacées vers une autre page.

        - **Nom** : indiquez un nom pour le dossier. Ce nom est visible sur l’appareil des utilisateurs.
        - **Ajouter** : ajoute des pages au dossier. Indiquez également les propriétés suivantes :

          - **Nom de la page** : entrez un nom pour la page. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil iOS.
          - **Nom de l’application** : entrez un nom pour l’application. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil iOS.
          - **ID d’ensemble d’applications** : entrez l’ID d’ensemble de l’application. La section [ID d’offres groupées pour des applications iOS intégrées que vous pouvez utiliser dans Intune](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.

      Cliquez sur **OK** pour enregistrer vos modifications.

#### <a name="example"></a>Exemple

Dans l’exemple suivant, une nouvelle page nommée **Contoso** est ajoutée. La page affiche les applications Trouver des amis et Réglages. L’application Réglages est sélectionnée et ses propriétés sont affichées :

![Exemple de paramètres d’écran d’accueil iOS](./media/Jc2OxyX.png)

Quand vous affectez la stratégie à un iPhone, la page est semblable à cette image :

![Appareil iOS avec écran d’accueil modifié](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Paramètres des notifications d’application

Choisissez la manière dont les applications installées sur les appareils iOS envoient des notifications. Ces paramètres prennent en charge les appareils supervisés exécutant iOS 9.3 et ultérieur.

- **Ajouter** : ajoutez des notifications pour les applications.

    ![Ajouter une notification d’application au profil iOS dans Intune](./media/ios-macos-app-notifications.png)

  - **Ajouter une ID d’ensemble d’applications** : entrez l’**ID d’ensemble d’applications** de l’application que vous voulez ajouter. La section [ID d’offres groupées pour des applications iOS intégrées que vous pouvez utiliser dans Intune](bundle-ids-built-in-ios-apps.md) fournit quelques exemples.
  - **Nom de l’application** : entrez le nom de l’application que vous voulez ajouter. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil.
  - **Éditeur** : entrez le nom de l’éditeur de l’application ajoutée. Ce nom est utilisé à titre de référence dans le portail Azure. Il *n’est pas* visible sur l’appareil.
  - **Notifications** : permet d’**Activer** ou de **Désactiver** l’envoi de notifications entre l’application et l’appareil.
    - **Afficher dans le centre de notifications** : **Activer** cette option permet à l’application d’afficher des notifications dans le centre de notifications de l’appareil. Choisissez **Désactiver** pour l’en empêcher.
    - **Afficher sur l’écran de verrouillage** : sélectionnez **Activer** pour afficher les notifications de l’application sur l’écran de verrouillage de l’appareil. Choisissez **Désactiver** pour l’en empêcher.
    - **Type d’alerte** : choisissez le mode d’affichage de la notification quand l’appareil est déverrouillé. Les options disponibles sont les suivantes :
      - **Aucune** : aucune notification ne s’affiche.
      - **Bannière** : une bannière contenant la notification s’affiche brièvement.
      - **Modal** : la notification s’affiche et l’utilisateur doit la fermer manuellement pour pouvoir continuer à utiliser l’appareil.
    - **Badge sur l’icône de l’application** : sélectionnez **Activer** pour ajouter un badge à l’icône de l’application. Le badge indique que l’application a envoyé une notification.
    - **Sons** : choisissez **Activer** pour qu’un son soit émis à la réception d’une notification.

Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="lock-screen-message-settings"></a>Paramètres du message d’écran de verrouillage

Utilisez ces paramètres pour afficher un texte ou un message personnalisé sur l’écran de verrouillage et dans la fenêtre de connexion, par exemple un message de type « En cas de perte, renvoyez à » et des informations d’étiquette d’inventaire. 

Ce paramètre prend en charge les appareils supervisés exécutant iOS 9.3 et plus.

- **Informations de l’étiquette d’inventaire** : entrez des informations sur l’étiquette d’inventaire de l’appareil. Par exemple, entrez `Owned by Contoso Corp` ou `Serial Number: {{serialnumber}}`.

  Le texte que vous entrez est affiché sur l’écran de verrouillage et dans la fenêtre de connexion de l’appareil.

- **Note de l’écran de verrouillage** : entrez une note qui pourrait vous aider à récupérer l’appareil en cas de perte ou de vol. Vous pouvez entrer n’importe quel texte. Par exemple, entrez quelque chose du genre `If found, call Contoso at ...`.

  Vous pouvez aussi utiliser des jetons d’appareil pour ajouter des informations propres à l’appareil dans ces champs. Par exemple, pour afficher le numéro de série, entrez `Serial Number: {{serialnumber}}`. L’écran de verrouillage affichera le texte `Serial Number 123456789ABC`. Quand vous entrez les variables, veillez à utiliser des accolades `{{ }}`. [Jetons de configuration d’application](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) inclut une liste de variables qui peuvent être utilisées. Vous pouvez également utiliser `deviceName` ou toute autre valeur propre à l’appareil.

  > [!NOTE]
  > Les variables ne sont pas validées dans l’interface utilisateur et respectent la casse. Par conséquent, vous pouvez voir des profils enregistrés avec une entrée incorrecte. Par exemple, si vous entrez `{{DeviceID}}` au lieu de `{{deviceid}}`, la chaîne littérale s’affiche à la place de l’ID unique de l’appareil. Veillez à entrer les informations correctes.

Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="single-sign-on-settings"></a>Paramètres de l’authentification unique

La plupart des applications métier nécessitent un certain niveau d’authentification utilisateur pour prendre en charge la sécurité. Dans de nombreux cas, le processus d’authentification oblige les utilisateurs à entrer les mêmes informations d’identification à plusieurs reprises, ce qui peut entraîner un sentiment de frustration. Pour améliorer l’expérience utilisateur, les développeurs peuvent créer des applications qui utilisent l’authentification unique (SSO). Ce type d’authentification permet de réduire le nombre de fois où l’utilisateur doit entrer ses informations d’identification.

L’authentification unique est possible si les conditions suivantes sont réunies :

- Vous devez avoir une application codée qui recherche le magasin d’informations d’identification utilisateur dans l’authentification unique sur l’appareil.
- Intune doit être configuré pour l’authentification unique des appareils iOS.

![Volet Authentification unique](./media/sso-blade.png)

- **Attribut de nom d’utilisateur d’AAD** : Intune recherche cet attribut pour chaque utilisateur dans Azure AD. Ensuite, Intune remplit le champ correspondant (par exemple, UPN) avant de générer le XML installé sur l’appareil. Les options disponibles sont les suivantes :

  - **Nom d’utilisateur principal** : l’UPN est analysé de la façon suivante :

    ![Attribut de nom d’utilisateur](media/User-name-attribute.png)

    Vous pouvez également remplacer le domaine par le texte que vous entrez dans la zone de texte **Domaine**.

    Par exemple, Contoso a plusieurs régions, dont Europe, Asie et Amérique du Nord. Contoso souhaite que les utilisateurs en Asie utilisent l’authentification unique et que l’application exige que le nom d’utilisateur principal soit au format `username@asia.contoso.com`. Quand vous sélectionnez **Nom d’utilisateur principal**, le domaine pour chaque utilisateur est extrait d’Azure AD (ici, c’est `contoso.com`). Par conséquent, pour les utilisateurs en Asie, sélectionnez **Nom d’utilisateur principal**, puis entrez `asia.contoso.com`. Le nom d’utilisateur principal de l’utilisateur final est maintenant `username@asia.contoso.com`, au lieu de `username@contoso.com`.

  - **ID d’appareil Intune** : Intune sélectionne automatiquement l’ID d’appareil Intune.

    Par défaut, les applications ont besoin d’utiliser uniquement l’ID d’appareil. Mais si votre application utilise le domaine et l’ID d’appareil, vous pouvez taper le domaine dans la zone de texte Domaine.

    > [!NOTE]
    > Par défaut, vous devez laisser le champ de domaine vide si vous utilisez l’ID d’appareil.

  - **ID d’appareil Azure AD**

- **Domaine** : entrez la partie domaine de l’URL. Par exemple, entrez `contoso.com`.
- **Préfixes d’URL qui utiliseront l’authentification unique** : **ajoutez** toutes les URL de votre organisation qui nécessitent une authentification unique de l’utilisateur.

  Par exemple, quand un utilisateur se connecte à l’un de ces sites, l’appareil iOS utilise les informations d’identification d’authentification unique. L’utilisateur n’a pas besoin d’entrer d’informations d’identification supplémentaires. Si l’authentification multifacteur est activée, les utilisateurs doivent entrer la deuxième authentification.

  > [!NOTE]
  > Ces URL doivent être spécifiées sous la forme de noms de domaine complets correctement mis en forme. Apple exige qu’elles soient spécifiées au format `http://<yourURL.domain>`.

  Les modèles de correspondance d’URL doivent commencer par `http://` ou `https://`. Une correspondance de chaîne simple est lancée pour que le préfixe d’URL `http://www.contoso.com/` ne corresponde pas à `http://www.contoso.com:80/`. Avec iOS 10.0 ou ultérieur, vous pouvez utiliser un seul caractère générique (\*) pour entrer toutes les valeurs correspondantes. Par exemple, `http://*.contoso.com/` correspond à la fois à `http://store.contoso.com/` et à `http://www.contoso.com`.

  Les modèles `http://.com` et `https://.com` correspondent respectivement à toutes les URL HTTP et HTTPS.

- **Applications qui utiliseront l’authentification unique** : **ajoutez** les applications sur les appareils de l’utilisateur final qui peuvent utiliser l’authentification unique.

  Le tableau `AppIdentifierMatches` doit inclure des chaînes qui correspondent aux ID de bundles d’applications. Ces chaînes peuvent être des correspondances exactes (comme `com.contoso.myapp`). Sinon, entrez une correspondance de préfixe sur l’ID de bundle à l’aide du caractère générique \*. Le caractère générique doit être placé après un point (.) et doit être utilisé une seule fois, à la fin de la chaîne, comme dans `com.contoso.*`. Quand un caractère générique est inclus, toute application dont l’ID de bundle commence par le préfixe bénéficie de l’accès au compte.

  Utilisez **Nom de l’application** pour entrer un nom convivial afin de faciliter l’identification de l’ID de bundle.

- **Certificat de renouvellement des informations d’identification** : si vous utilisez des certificats pour l’authentification (plutôt que des mots de passe), sélectionnez le certificat SCEP ou PFX existant en tant que certificat d’authentification. En général, ce certificat est le même que celui déployé pour l’utilisateur dans d’autres profils, tels que VPN, WiFi ou e-mail.

Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="web-content-filter-settings"></a>Paramètres du filtre de contenu web

Ces paramètres contrôlent l’accès aux URL par le navigateur sur les appareils iOS.

- **Type de filtre** : choisissez les sites web spécifiques que vous voulez autoriser. Les options disponibles sont les suivantes :

  - **Configurer les URL** : utilisez le filtre web intégré d’Apple qui recherche le contenu réservé aux adultes, par exemple des propos blasphématoires ou sexuellement explicites. Cette fonctionnalité analyse chaque page web qui est chargée afin de détecter et bloquer les contenus inappropriés. Vous pouvez également ajouter les URL que vous souhaitez exclure du filtrage, ou bien bloquer certaines URL, indépendamment des paramètres de filtre d’Apple.

    - **URL autorisées** : choisissez **Ajouter** pour ajouter les URL que vous souhaitez autoriser. Ces URL ignorent le filtre web d’Apple.

      > [!NOTE]
        > Les URL que vous entrez ici sont les URL qui ne seront pas analysées par le filtre web d’Apple. Elles ne correspondent pas à des sites web autorisés. Pour créer une liste des sites web autorisés, définissez **Type de filtre** sur **Sites web spécifiques uniquement**.

      Cliquez sur **OK** pour enregistrer vos modifications.

    - **URL bloquées** : choisissez **Ajouter** pour ajouter les URL dont vous souhaitez empêcher l’ouverture, indépendamment des paramètres de filtre web d’Apple.

      Cliquez sur **OK** pour enregistrer vos modifications.

  - **Sites web spécifiques uniquement** (pour le navigateur web Safari uniquement) : ces URL sont ajoutées aux signets du navigateur Safari. L’utilisateur est **uniquement** autorisé à accéder à ces sites ; il ne peut ouvrir aucun autre site. Utilisez cette option uniquement si vous connaissez la liste exacte des URL auxquelles les utilisateurs peuvent accéder.

    - **URL** : entrez l’URL du site web que vous souhaitez autoriser. Par exemple, entrez `https://www.contoso.com`.
    - **Chemin de signet** : entrez le chemin où stocker le signet. Par exemple, entrez `/Contoso/Business Apps`. Si vous n’ajoutez pas de chemin, le signet est ajouté au dossier de signets par défaut sur l’appareil.
    - **Titre** : entrez un titre descriptif pour le signet.

    Si vous n’entrez pas d’URL, les utilisateurs finaux ne pourront accéder à aucun site web à l’exception de `microsoft.com`, `microsoft.net` et `apple.com`. Ces URL sont automatiquement autorisées par Intune.

    Cliquez sur **OK** pour enregistrer vos modifications.

## <a name="wallpaper-settings"></a>Paramètres du papier peint

Ajoutez une image .png, .jpg ou .jpeg personnalisée sur vos appareils iOS supervisés. Par exemple, ajoutez un logo d’entreprise sur l’écran de verrouillage.

Vous pouvez constater un comportement inattendu quand un profil sans image est affecté à des appareils ayant une image existante. Par exemple, vous créez un profil sans image. Ce profil est affecté à des appareils qui disposent déjà d’une image. Dans ce scénario, l’image peut être remplacée par l’appareil par défaut, ou l’image d’origine peut rester sur l’appareil. Ce comportement est contrôlé et limité par la plateforme MDM d’Apple.

- **Emplacement d’affichage du papier peint** : choisissez un emplacement où afficher l’image sur l’appareil. Les options disponibles sont les suivantes :
  - **Non configuré** : aucune image personnalisée n’est ajoutée sur l’appareil. L’appareil utilise l’image par défaut du système d’exploitation.
  - **Écran de verrouillage** : ajoute l’image à l’écran de verrouillage.
  - **Écran d’accueil** : ajoute l’image à l’écran d’accueil.
  - **Écran de verrouillage et écran d’accueil** : la même image est utilisée sur l’écran de verrouillage et sur l’écran d’accueil.
- **Image de papier peint** : chargez une image .png, .jpg ou .jpeg existante à utiliser. La taille du fichier doit être inférieure à 750 Ko. Vous pouvez **supprimer** une image que vous aviez ajoutée.

> [!TIP]
> Pour afficher des images différentes sur l’écran de verrouillage et l’écran d’accueil, créez un profil avec l’image de l’écran de verrouillage, et un autre profil avec l’image de l’écran d’accueil. Affectez les deux profils à l’utilisateur ou aux groupes d’appareils iOS souhaités.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez aussi créer des profils de fonctionnalités d’appareil pour les appareils [macOS](macos-device-features-settings.md).
