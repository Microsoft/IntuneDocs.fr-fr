---
title: Paramètres des fonctionnalités d’appareil macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez les paramètres pour configurer des appareils macOS pour AirPrint et personnalisez la fenêtre de connexion pour qu’elle affiche ou masque les boutons d’alimentation dans Microsoft Intune. Consultez les étapes à suivre pour obtenir les paramètres relatifs à l’adresse IP, au chemin et au port d’un serveur AirPrint dans votre réseau. Utilisez ces paramètres dans un profil de configuration d’appareil pour configurer les fonctionnalités d’un appareil macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2019
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
ms.openlocfilehash: 3d0cff4ad624d35843f3388535b60549d1893eeb
ms.sourcegitcommit: c38a856725993a4473ada75e669a57f75ab376f8
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73143163"
---
# <a name="macos-device-feature-settings-in-intune"></a>Paramètres des fonctionnalités d’appareil macOS dans Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune inclut certains paramètres intégrés afin de personnaliser les fonctionnalités de vos appareils macOS. Par exemple, les administrateurs peuvent ajouter des imprimantes, choisir la manière dont les utilisateurs se connectent, configurer les contrôles de l’alimentation, utiliser l’authentification unique et bien plus encore.

Utilisez ces fonctionnalités pour contrôler vos appareils macOS dans le cadre de votre solution de gestion des appareils mobiles.

Cet article liste ces paramètres et décrit le rôle de chaque paramètre. Il liste également les étapes à suivre pour obtenir l’adresse IP, le chemin et le port des imprimantes AirPrint à l’aide de l’application Terminal (émulateur). Pour plus d’informations sur les fonctionnalités de l’appareil, consultez [Ajouter des paramètres de fonctionnalités d’appareils iOS ou MacOS](device-features-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil macOS](device-features-configure.md).

> [!NOTE]
> Ces paramètres s’appliquent à différents types d’inscription, avec certains paramètres s’appliquant à toutes les options d’inscription. Pour plus d’informations sur les différents types d’inscription, consultez [inscription MacOS](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : inscription des appareils et inscription automatique des appareils 

- **Adresse IP** : entrez l’adresse IPv4 ou IPv6 de l’imprimante. Si vous utilisez des noms d’hôte pour identifier les imprimantes, vous pouvez effectuer un test ping dans l’application Terminal pour obtenir l’adresse IP de l’imprimante. Pour plus de détails, consultez [Obtenir l’adresse IP et le chemin](#get-the-ip-address-and-path) dans cet article.
- **Chemin d’accès** : entrez le chemin de l’imprimante. Le chemin est généralement `ipp/print` pour les imprimantes de votre réseau. Pour plus de détails, consultez [Obtenir l’adresse IP et le chemin](#get-the-ip-address-and-path) dans cet article.
- **Port** (iOS 11.0 et supérieure) : entrez le port d’écoute de la destination AirPrint. Si vous ne renseignez pas cette propriété, AirPrint utilise le port par défaut.
- **Protocole TLS** (iOS 11.0 et supérieure) : choisissez **Activer** pour sécuriser les connexions AirPrint à l’aide du protocole TLS (Transport Layer Security).

- **Ajoutez** le serveur AirPrint. Vous pouvez ajouter plusieurs serveurs AirPrint.

Vous pouvez également **importer** une liste d’imprimantes AirPrint séparées par des virgules dans un fichier .csv. Après avoir ajouté des imprimantes AirPrint dans Intune, vous pouvez **exporter** cette liste.

### <a name="get-the-ip-address-and-path"></a>Obtenir l’adresse IP et le chemin

Pour ajouter des serveurs AirPrinter, vous avez besoin de l’adresse IP de l’imprimante, du chemin de la ressource et du port. Les étapes suivantes vous montrent comment obtenir ces informations.

1. Sur un Mac connecté au même réseau local (sous-réseau) que les imprimantes AirPrint, ouvrez **Terminal** (à partir de **/Applications/Utilities**).
2. Dans l’application Terminal, tapez `ippfind` et appuyez sur Entrée.

    Notez les informations relatives à l’imprimante. La sortie obtenue peut ressembler à ceci : `ipp://myprinter.local.:631/ipp/port1`. La première partie est le nom de l’imprimante. La dernière partie (`ipp/port1`) est le chemin de la ressource.

3. Dans le Terminal, tapez `ping myprinter.local` et appuyez sur Entrée.

   Notez l’adresse IP. La sortie obtenue peut ressembler à ceci : `PING myprinter.local (10.50.25.21)`.

4. Utilisez les valeurs de l’adresse IP et du chemin de la ressource. Dans cet exemple, l’adresse IP est `10.50.25.21` et le chemin de ressource est `/ipp/port1`.

## <a name="login-items"></a>Éléments de connexion

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Fichiers, dossiers et applications personnalisées**: **Ajoutez** le chemin d’accès d’un fichier, d’un dossier, d’une application personnalisée ou d’une application système que vous souhaitez ouvrir lorsqu’un utilisateur se connecte à l’appareil. Les applications système ou les applications générées ou personnalisées pour votre organisation se trouvent généralement dans le dossier `Applications`, avec un chemin d’accès similaire à `/Applications/AppName.app`. 

  Vous pouvez ajouter de nombreux fichiers, dossiers et applications. Par exemple, entrez :  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Lors de l’ajout d’une application, d’un dossier ou d’un fichier, veillez à entrer le chemin d’accès correct. Tous les éléments ne se trouvent pas dans le dossier `Applications`. Si un utilisateur déplace un élément d’un emplacement à un autre, alors le chemin d’accès change. Cet élément déplacé ne s’ouvre pas lorsque l’utilisateur se connecte.

## <a name="login-window"></a>Fenêtre de connexion

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Les paramètres s’appliquent à : inscription des appareils et inscription automatique des appareils 

#### <a name="window-layout"></a>Disposition de la fenêtre

- **Afficher des informations supplémentaires dans la barre de menus** : lorsque la zone d’heure de la barre de menus est sélectionnée, **Autoriser** affiche le nom de l’hôte et la version macOS. **Non configuré** (par défaut) n’affiche pas ces informations dans la barre de menus.
- **Bannière** : entrez un message à afficher à l’écran de connexion de l’appareil. Par exemple, entrez les informations de votre organisation, un message d’accueil, les informations sur les objets perdus et retrouvés, etc.
- **Choisir le format de connexion** : choisissez la façon dont les utilisateurs se connectent à l’appareil. Les options disponibles sont les suivantes :
  - **Demander le nom d’utilisateur et le mot de passe** (par défaut) : demande aux utilisateurs de saisir un nom d'utilisateur et un mot de passe.
  - **Répertorier tous les utilisateurs, demander mot de passe** : demande aux utilisateurs de sélectionner leur nom d'utilisateur depuis une liste d’utilisateurs avant de saisir leur mot de passe. Configurez également :

    - **Utilisateurs locaux** : **Masquer** pour masquer les comptes utilisateurs locaux dans la liste des utilisateurs, ce qui peut inclure les comptes administrateurs et standards. Seuls les comptes d'utilisateur système et réseau sont affichés. **Non configuré** (par défaut) affiche les comptes d'utilisateur locaux dans la liste des utilisateurs.
    - **Comptes mobiles** : **Masquer** pour masquer les comptes mobiles dans la liste des utilisateurs. **Non configuré** (par défaut) affiche les comptes mobiles dans la liste des utilisateurs. Certains comptes mobiles peuvent apparaître comme utilisateurs réseau.
    - **Utilisateurs réseau** : sélectionnez **Afficher** pour afficher les utilisateurs réseau dans la liste des utilisateurs. **Non configuré** (par défaut) masque les comptes d’utilisateurs réseau dans la liste des utilisateurs.
    - **Utilisateurs administrateurs** : **Masquer** pour masquer les comptes d’utilisateurs administrateurs dans la liste des utilisateurs. **Non configuré** (par défaut) affiche les comptes d’utilisateurs réseau dans la liste des utilisateurs.
    - **Autres utilisateurs** : sélectionnez **Afficher** pour afficher les **Autres...** utilisateurs dans la liste des utilisateurs. **Non configuré** (par défaut) masque les comptes d’autres utilisateurs dans la liste des utilisateurs.

#### <a name="login-screen-power-settings"></a>Paramètres d’alimentation de l’écran de connexion

- **Bouton Arrêt** : **Masquer** pour masquer le bouton d’arrêt sur l’écran de connexion. **Non configuré** (par défaut) affiche le bouton d’arrêt.
- **Bouton Redémarrer** : **Masquer** pour masquer le bouton de redémarrage sur l’écran de connexion. **Non configuré** (par défaut) affiche le bouton de redémarrage.
- **Bouton Veille** : **Masquer** pour masquer le bouton de mise en veille sur l’écran de connexion. **Non configuré** (par défaut) affiche le bouton de mise en veille.

#### <a name="other"></a>Autre

- **Désactiver la connexion utilisateur à partir de la console** : **Désactiver** masque la ligne de commande macOS utilisée pour se connecter. Pour des utilisateurs normaux, **désactivez** ce paramètre. **Non configuré** (par défaut) permet à des utilisateurs avancés de se connecter à l’aide de la ligne de commande macOS. Pour passer en mode console, les utilisateurs doivent saisir `>console` dans le champ Nom d'utilisateur puis s’authentifier dans la fenêtre de la console.

#### <a name="apple-menu"></a>Menu Apple

Une fois que les utilisateurs se sont connectés à leurs appareils, les paramètres suivants affectent ce qu’ils peuvent faire.

- **Désactiver l’arrêt** : **Désactiver** empêche les utilisateurs de sélectionner l’option **Arrêt** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Arrêt** sur l’appareil.
- **Désactiver le redémarrage** : **Désactiver** empêche les utilisateurs de sélectionner l’option **Redémarrage** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Redémarrage** sur l’appareil.
- **Désactiver la mise hors tension** : **Désactiver** empêche les utilisateurs de sélectionner l’option **Mise hors tension** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Mise hors tension** sur l’appareil.
- **Désactiver la déconnexion** (macOS 10.13 et versions ultérieures) : **Désactiver** empêche les utilisateurs de sélectionner l’option **Déconnexion** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Déconnexion** sur l’appareil.
- **Désactiver le verrouillage d’écran** (macOS 10.13 et versions ultérieures) : **Désactiver** empêche les utilisateurs de sélectionner l’option **Verrouillage de l’écran** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Verrouillage de l’écran** sur l’appareil.

## <a name="single-sign-on-app-extension"></a>Extension d’application d’authentification unique

Cette fonctionnalité s’applique à :

- macOS 10.15 et ultérieur

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription 

- **Type d’extension d’application SSO**: choisissez le type d’extension d’application SSO d’informations d’identification. Les options disponibles sont les suivantes :

  - **Non configuré**: les extensions d’application ne sont pas utilisées. Pour désactiver une extension d’application SSO, basculez le type d’extension de l’application SSO de **Kerberos** ou des **informations d’identification** sur **non configuré**.
  - **Informations d’identification**: utilisez une extension d’application d’informations d’identification générique et personnalisable pour utiliser l’authentification unique. Vérifiez que vous connaissez l’ID d’extension et l’ID d’équipe pour l’extension de l’application SSO de votre organisation.  
  - **Kerberos**: utilisez l’extension Kerberos intégrée d’Apple, qui est incluse sur macOS Catalina 10,15 et versions ultérieures. Cette option est une version spécifique à Kerberos de l’extension **d’application d’informations d’identification** .

  > [!TIP]
  > Avec le type **d’informations d’identification** , vous ajoutez vos propres valeurs de configuration pour transmettre l’extension. Au lieu de cela, envisagez d’utiliser les paramètres de configuration intégrés fournis par Apple dans le type **Kerberos** .

- **ID d’extension** (informations d’identification uniquement) : entrez l’identificateur de bundle qui identifie votre extension d’application SSO, par exemple `com.apple.ssoexample`.
- **ID d’équipe** (informations d’identification uniquement) : entrez l’identificateur d’équipe de votre extension d’application SSO. Un identificateur d’équipe est une chaîne de 10 caractères alphanumériques (nombres et lettres) générée par Apple, par exemple `ABCDE12345`. 

  Pour plus d’informations, [recherchez votre ID d’équipe](https://help.apple.com/developer-account/#/dev55c3c710c) (qui ouvre le site Web d’Apple).

- **Domaine**: entrez le nom de votre domaine d’authentification. Le nom de domaine doit être en majuscules, par exemple `CONTOSO.COM`. En règle générale, le nom de votre domaine est le même que votre nom de domaine DNS, mais en majuscules.
- **Domaines**: entrez les noms de domaine ou d’hôte des sites qui peuvent s’authentifier par le biais de l’authentification unique. Par exemple, si votre site Web est `mysite.contoso.com`, `mysite` est le nom d’hôte et `contoso.com` est le nom de domaine. Lorsque les utilisateurs se connectent à l’un de ces sites, l’extension d’application gère la demande d’authentification. Cette authentification permet aux utilisateurs d’utiliser l’ID de face, Touch ID ou Apple pincode/code d’accès pour se connecter.

  - Tous les domaines de vos profils Intune d’extension d’application d’authentification unique doivent être uniques. Vous ne pouvez pas répéter un domaine dans n’importe quel profil d’extension d’application de connexion, même si vous utilisez différents types d’extensions d’application SSO.
  - Ces domaines ne respectent pas la casse.

- **Configuration supplémentaire** (informations d’identification uniquement) : entrez des données supplémentaires spécifiques à l’extension à passer à l’extension de l’application SSO :
  - **Clé de configuration**: entrez le nom de l’élément que vous souhaitez ajouter, par exemple, `user name`.
  - **Type de valeur**: entrez le type de données. Les options disponibles sont les suivantes :

    - Chaîne
    - Booléen : dans la **valeur de configuration**, entrez `True` ou `False`.
    - Entier : dans **valeur de configuration**, entrez un nombre.
    
  - **Valeur de configuration**: entrez les données.
  
  - **Ajouter**: sélectionnez cette option pour ajouter vos clés de configuration.

- **Utilisation de trousseau** (Kerberos uniquement) : choisissez **bloquer** pour empêcher l’enregistrement et le stockage des mots de passe dans le trousseau. **Non configuré** (valeur par défaut) permet d’enregistrer et de stocker les mots de passe dans le trousseau.  
- **ID de face, Touch ID ou code secret** (Kerberos uniquement) : **exiger** oblige les utilisateurs à entrer leur ID de face, Touch ID ou code secret Apple pour se connecter aux domaines que vous avez ajoutés. **Non configuré** (par défaut) n’oblige pas les utilisateurs à utiliser la biométrie ou le code secret pour se connecter.
- **Domaine par défaut** (Kerberos uniquement) : choisissez **activer** pour définir la valeur de **domaine** que vous avez entrée comme domaine par défaut. **Non configuré** (par défaut) ne définit pas de domaine par défaut.

  > [!TIP]
  > - **Activez** ce paramètre si vous configurez plusieurs extensions d’application SSO Kerberos dans votre organisation.
  > - **Activez** ce paramètre si vous utilisez plusieurs domaines. Il définit la valeur de **domaine** que vous avez entrée comme domaine par défaut.
  > - Si vous n’avez qu’un seul domaine, laissez-le **non configuré** (par défaut).

- **Découverte** automatique (Kerberos uniquement) : lorsqu’elle est définie sur **bloquer**, l’extension Kerberos n’utilise pas automatiquement LDAP et DNS pour déterminer son nom de site Active Directory. **Non configuré** (valeur par défaut) permet à l’extension de rechercher automatiquement le nom du site Active Directory.
- **Modification du mot de passe** (Kerberos uniquement **) : empêche** les utilisateurs de modifier les mots de passe qu’ils utilisent pour se connecter aux domaines que vous avez entrés. **Non configuré** (valeur par défaut) permet de modifier le mot de passe.  
- **Synchronisation de mot de passe** (Kerberos uniquement) : choisissez **activer** pour synchroniser les mots de passe locaux de vos utilisateurs sur Azure ad. **Non configuré** (par défaut) désactive la synchronisation de mot de passe pour Azure ad. Utilisez ce paramètre comme alternative ou sauvegarde pour l’authentification unique. Ce paramètre ne fonctionne pas si les utilisateurs sont connectés avec un compte mobile Apple.
- **Windows Server Active Directory la complexité du mot de passe** (Kerberos uniquement) : choisissez **exiger** pour forcer les mots de passe utilisateur à répondre aux exigences de complexité du mot de passe de Active Directory. Pour plus d’informations, consultez le [mot de passe doit respecter des exigences de complexité](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **Non configuré** (par défaut) n’oblige pas les utilisateurs à respecter les exigences de mot de passe de Active Directory.
- **Longueur minimale du mot de passe** (Kerberos uniquement) : entrez le nombre minimal de caractères pouvant commettre le mot de passe d’un utilisateur. **Non configuré** (par défaut) n’impose pas une longueur minimale de mot de passe aux utilisateurs.
- **Limite de réutilisation du mot de passe** (Kerberos uniquement) : entrez le nombre de nouveaux mots de passe, à partir de 1-24, qui doivent être utilisés jusqu’à ce qu’un mot de passe précédent puisse être réutilisé sur le domaine. **Non configuré** (par défaut) n’impose pas de limite de réutilisation du mot de passe.
- **Durée de vie minimale du mot de passe** (Kerberos uniquement) : entrez le nombre de jours pendant lesquels un mot de passe doit être utilisé sur le domaine pour qu’un utilisateur puisse le changer. **Non configuré** (par défaut) n’impose pas une ancienneté minimale des mots de passe avant de pouvoir les modifier.
- **Notification d’expiration du mot de passe** (Kerberos uniquement) : entrez le nombre de jours avant l’expiration d’un mot de passe, afin que les utilisateurs soient avertis que leur mot de passe expirera. **Non configuré** (par défaut) utilise `15` jours.
- **Expiration du mot de passe** (Kerberos uniquement) : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil. **Non configuré** (valeur par défaut) signifie que les mots de passe des utilisateurs n’expirent jamais.
- **Nom principal** (Kerberos uniquement) : entrez le nom d’utilisateur du principal Kerberos. Vous n’avez pas besoin d’inclure le nom de domaine. Par exemple, dans `user@contoso.com`, `user` est le nom principal et `contoso.com` est le nom de domaine.
- **Code de site Active Directory** (Kerberos uniquement) : entrez le nom du site Active Directory que l’extension Kerberos doit utiliser. Vous n’avez peut-être pas besoin de modifier cette valeur, car l’extension Kerberos peut trouver automatiquement le code de site Active Directory.
- **Nom du cache** (Kerberos uniquement) : entrez le nom du service de sécurité générique (GSS) du cache Kerberos. Vous n’avez probablement pas besoin de définir cette valeur.  
- **Message** sur les exigences de mot de passe (Kerberos uniquement) : entrez une version textuelle des exigences de mot de passe de votre organisation, qui est présentée aux utilisateurs. Le message s’affiche si vous n’avez pas besoin de Active Directory exigences de complexité du mot de passe ou si vous n’entrez pas une longueur minimale pour le mot de passe.  
- **ID d’ensemble d’applications** (Kerberos uniquement) : **Ajoutez** les identificateurs de bundle d’applications qui doivent utiliser l’authentification unique sur vos appareils. Ces applications sont autorisées à accéder au ticket d’accord de ticket Kerberos, au ticket d’authentification et à authentifier les utilisateurs auprès des services auxquels ils sont autorisés à accéder.
- **Mappage** de domaine Kerberos (Kerberos uniquement) : **Ajoutez** les suffixes DNS de domaine qui doivent être mappés à votre domaine. Utilisez ce paramètre lorsque les noms DNS des hôtes ne correspondent pas au nom de domaine. Vous n’avez probablement pas besoin de créer ce mappage de domaine à domaine personnalisé.

## <a name="associated-domains"></a>Domaines associés

Dans Intune, vous pouvez :

- Ajoutez de nombreuses associations application-à-domaine.
- Associer de nombreux domaines à la même application.

Cette fonctionnalité s’applique à :

- macOS 10.15 et ultérieur

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **ID**de l’application : entrez l’identificateur d’application de l’application à associer à un site Web. L’identificateur d’application comprend l’ID d’équipe et un ID de Bundle : `TeamID.BundleID`.

  L’ID d’équipe est une chaîne de 10 caractères alphanumériques (lettres et chiffres) générée par Apple pour les développeurs d’applications, comme `ABCDE12345`. Pour plus d’informations, [recherchez votre ID d’équipe](https://help.apple.com/developer-account/#/dev55c3c710c)   (ouvre le site Web d’Apple).

  L’ID de Bundle identifie de façon unique l’application, et est généralement mis en forme dans la notation de nom de domaine inverse. Par exemple, l’ID de Bundle du Finder est `com.apple.finder`. Pour trouver l’ID de Bundle, utilisez l’AppleScript dans le terminal :

  `osascript -e 'id of app "ExampleApp"'`

- **Domaine**: entrez le domaine de site Web à associer à une application. Le domaine comprend un type de service et un nom d’hôte complet, par exemple `webcredentials:www.contoso.com`.

  Vous pouvez faire correspondre tous les sous-domaines d’un domaine associé en entrant `*.` (caractère générique astérisque et point) avant le début du domaine. La période est requise. Les domaines exacts ont une priorité plus élevée que les domaines génériques. Par conséquent, les modèles des domaines parents sont mis en correspondance *si* aucune correspondance n’est trouvée dans le sous-domaine complet.

  Le type de service peut être :

  - **authsrv** : extension d’application d’authentification unique
  - **applink**: lien universel
  - **informations d’identification**: remplissage automatique du mot de passe

- **Ajouter**: sélectionnez cette option pour ajouter vos applications et les domaines associés.

> [!TIP]
> Pour résoudre le problèmes, sur votre appareil macOS, ouvrez **Préférences système**  > **profils**. Confirmez que le profil que vous avez créé figure dans la liste des profils d’appareil. S’il est listé, vérifiez que la **Configuration des domaines associés** se trouve dans le profil et qu’elle comprend l’ID d’application et les domaines appropriés.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).

Vous pouvez également configurer des fonctionnalités d’appareil sur [iOS](ios-device-features-settings.md).
