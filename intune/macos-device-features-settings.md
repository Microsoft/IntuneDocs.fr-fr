---
title: Paramètres des fonctionnalités d’appareil macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez les paramètres pour configurer des appareils macOS pour AirPrint et personnalisez la fenêtre de connexion pour qu’elle affiche ou masque les boutons d’alimentation dans Microsoft Intune. Consultez les étapes à suivre pour obtenir les paramètres relatifs à l’adresse IP, au chemin et au port d’un serveur AirPrint dans votre réseau. Utilisez ces paramètres dans un profil de configuration d’appareil pour configurer les fonctionnalités d’un appareil macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1826498b3bfa2191900d7574f79051af8f758558
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041702"
---
# <a name="macos-device-feature-settings-in-intune"></a>Paramètres des fonctionnalités d’appareil macOS dans Intune

Intune inclut certains paramètres intégrés afin de personnaliser les fonctionnalités de vos appareils macOS. Cet article liste ces paramètres et décrit le rôle de chaque paramètre. Il liste également les étapes à suivre pour obtenir l’adresse IP, le chemin et le port des imprimantes AirPrint à l’aide de l’application Terminal (émulateur).

Cette fonctionnalité s’applique à :

- macOS

Dans le cadre de votre solution de gestion des périphériques mobiles (GPM), utilisez ces paramètres pour créer une bannière, choisir la méthode de connexion des utilisateurs, ajouter un serveur AirPrint, et plus encore.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils macOS.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil macOS](device-features-configure.md).

## <a name="airprint"></a>AirPrint

- **Adresse IP** : entrez l’adresse IPv4 ou IPv6 de l’imprimante. Si vous utilisez des noms d’hôte pour identifier les imprimantes, vous pouvez effectuer un test ping dans l’application Terminal pour obtenir l’adresse IP de l’imprimante. Pour plus de détails, consultez [Obtenir l’adresse IP et le chemin](#get-the-ip-address-and-path) dans cet article.
- **Chemin d’accès** : entrez le chemin de l’imprimante. Le chemin est généralement `ipp/print` pour les imprimantes de votre réseau. Pour plus de détails, consultez [Obtenir l’adresse IP et le chemin](#get-the-ip-address-and-path) dans cet article.
- **Port** (iOS 11.0 et supérieure) : entrez le port d’écoute de la destination AirPrint. Si vous ne renseignez pas cette propriété, AirPrint utilise le port par défaut.
- **Protocole TLS** (iOS 11.0 et supérieure) : choisissez **Activer** pour sécuriser les connexions AirPrint à l’aide du protocole TLS (Transport Layer Security).

**Ajoutez** le serveur AirPrint. Vous pouvez ajouter plusieurs serveurs AirPrint.

- **Importer** (facultatif) : vous pouvez également **importer** une liste d’imprimantes AirPrint séparées par des virgules dans un fichier .csv. Après avoir ajouté des imprimantes AirPrint dans Intune, vous pouvez **exporter** cette liste.

Sélectionnez **OK** pour enregistrer vos paramètres.

### <a name="get-the-ip-address-and-path"></a>Obtenir l’adresse IP et le chemin

Pour ajouter des serveurs AirPrinter, vous avez besoin de l’adresse IP de l’imprimante, du chemin de la ressource et du port. Les étapes suivantes vous montrent comment obtenir ces informations.

1. Sur un Mac connecté au même réseau local (sous-réseau) que les imprimantes AirPrint, ouvrez **Terminal** (à partir de **/Applications/Utilities**).
2. Dans l’application Terminal, tapez `ippfind` et appuyez sur Entrée.

    Notez les informations relatives à l’imprimante. La sortie obtenue peut ressembler à ceci : `ipp://myprinter.local.:631/ipp/port1`. La première partie est le nom de l’imprimante. La dernière partie (`ipp/port1`) est le chemin de la ressource.

3. Dans le Terminal, tapez `ping myprinter.local` et appuyez sur Entrée.

   Notez l’adresse IP. La sortie obtenue peut ressembler à ceci : `PING myprinter.local (10.50.25.21)`.

4. Utilisez les valeurs de l’adresse IP et du chemin de la ressource. Dans cet exemple, l’adresse IP est `10.50.25.21` et le chemin de ressource est `/ipp/port1`.

## <a name="login-window"></a>Fenêtre de connexion

### <a name="window-layout"></a>Disposition de la fenêtre

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

### <a name="login-screen-power-settings"></a>Paramètres d’alimentation de l’écran de connexion

- **Bouton Arrêt** : **Masquer** pour masquer le bouton d’arrêt sur l’écran de connexion. **Non configuré** (par défaut) affiche le bouton d’arrêt.
- **Bouton Redémarrer** : **Masquer** pour masquer le bouton de redémarrage sur l’écran de connexion. **Non configuré** (par défaut) affiche le bouton de redémarrage.
- **Bouton Veille** : **Masquer** pour masquer le bouton de mise en veille sur l’écran de connexion. **Non configuré** (par défaut) affiche le bouton de mise en veille.

### <a name="other"></a>Autre

- **Désactiver la connexion utilisateur à partir de la console** : **Désactiver** masque la ligne de commande macOS utilisée pour se connecter. Pour des utilisateurs normaux, **désactivez** ce paramètre. **Non configuré** (par défaut) permet à des utilisateurs avancés de se connecter à l’aide de la ligne de commande macOS. Pour passer en mode console, les utilisateurs doivent saisir `>console` dans le champ Nom d'utilisateur puis s’authentifier dans la fenêtre de la console.

### <a name="apple-menu"></a>Menu Apple

Une fois que les utilisateurs se sont connectés à leurs appareils, les paramètres suivants affectent ce qu’ils peuvent faire.

- **Désactiver l’arrêt** : **Désactiver** empêche les utilisateurs de sélectionner l’option **Arrêt** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Arrêt** sur l’appareil.
- **Désactiver le redémarrage** : **Désactiver** empêche les utilisateurs de sélectionner l’option **Redémarrage** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Redémarrage** sur l’appareil.
- **Désactiver la mise hors tension** : **Désactiver** empêche les utilisateurs de sélectionner l’option **Mise hors tension** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Mise hors tension** sur l’appareil.
- **Désactiver la déconnexion** (macOS 10.13 et versions ultérieures) : **Désactiver** empêche les utilisateurs de sélectionner l’option **Déconnexion** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Déconnexion** sur l’appareil.
- **Désactiver le verrouillage d’écran** (macOS 10.13 et versions ultérieures) : **Désactiver** empêche les utilisateurs de sélectionner l’option **Verrouillage de l’écran** après leur connexion. **Non configuré** (par défaut) permet aux utilisateurs de sélectionner l’élément de menu **Verrouillage de l’écran** sur l’appareil.

Sélectionnez **OK** pour enregistrer vos paramètres.

## <a name="next-steps"></a>Étapes suivantes

- Passez en revue tous les paramètres pour les appareils [iOS](ios-device-features-settings.md).
- [Affectez ce profil](device-profile-assign.md) à vos groupes et [supervisez son état](device-profile-monitor.md).
