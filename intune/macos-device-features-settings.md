---
title: Paramètres des fonctionnalités d’appareil macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Passez en revue tous les paramètres permettant de configurer des appareils macOS pour AirPrint dans Microsoft Intune. Découvrez également les étapes à suivre pour obtenir les paramètres relatifs à l’adresse IP, au chemin et au port d’un serveur AirPrint dans votre réseau. Utilisez ces paramètres dans un profil de configuration d’appareil pour permettre aux appareils macOS d’utiliser des serveurs AirPrint dans votre réseau.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4973dc5038ecfe9a8e909df1a1db3feceb30979b
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565330"
---
# <a name="macos-device-feature-settings-in-intune"></a>Paramètres des fonctionnalités d’appareil macOS dans Intune

Intune intègre certains paramètres que vous pouvez configurer pour permettre aux utilisateurs macOS d’imprimer sur des imprimantes AirPrint de votre réseau. Cet article liste ces paramètres et décrit le rôle de chaque paramètre. Il liste également les étapes à suivre pour obtenir l’adresse IP, le chemin et le port des imprimantes AirPrint à l’aide de l’application Terminal (émulateur).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil macOS](device-features-configure.md).

## <a name="airprint-settings"></a>Paramètres AirPrint

1. Dans **Paramètres**, sélectionnez **AirPrint**. Entrez les propriétés suivantes pour le serveur AirPrint :

    - **Adresse IP** : entrez l’adresse IPv4 ou IPv6 de l’imprimante. Si vous utilisez des noms d’hôte pour identifier les imprimantes, vous pouvez effectuer un test ping dans l’application Terminal pour obtenir l’adresse IP de l’imprimante. Pour plus de détails, consultez [Obtenir l’adresse IP et le chemin](#get-the-ip-address-and-path) dans cet article.
    - **Chemin d’accès** : entrez le chemin de l’imprimante. Le chemin est généralement `ipp/print` pour les imprimantes de votre réseau. Pour plus de détails, consultez [Obtenir l’adresse IP et le chemin](#get-the-ip-address-and-path) dans cet article.
    - **Port** : entrez le port d’écoute de la destination AirPrint. Si vous ne renseignez pas cette propriété, AirPrint utilise le port par défaut. Disponible sur iOS 11.0 et ultérieur.
    - **Protocole TLS** : choisissez **Activer** pour sécuriser les connexions AirPrint à l’aide du protocole TLS (Transport Layer Security). Disponible sur iOS 11.0 et ultérieur.

2. Sélectionnez **Ajouter**. Le serveur AirPrint est ajouté à la liste. Vous pouvez ajouter plusieurs serveurs AirPrint.

    Vous pouvez également **importer** une liste d’imprimantes AirPrint séparées par des virgules dans un fichier .csv. Après avoir ajouté des imprimantes AirPrint dans Intune, vous pouvez **exporter** cette liste.

3. Quand vous avez terminé, sélectionnez **OK** pour enregistrer votre liste.

## <a name="get-the-ip-address-and-path"></a>Obtenir l’adresse IP et le chemin

Pour ajouter des serveurs AirPrinter, vous avez besoin de l’adresse IP de l’imprimante, du chemin de la ressource et du port. Les étapes suivantes vous montrent comment obtenir ces informations.

1. Sur un Mac connecté au même réseau local (sous-réseau) que les imprimantes AirPrint, ouvrez **Terminal** (à partir de **/Applications/Utilities**).
2. Dans l’application Terminal, tapez `ippfind` et appuyez sur Entrée.

    Notez les informations relatives à l’imprimante. La sortie obtenue peut ressembler à ceci : `ipp://myprinter.local.:631/ipp/port1`. La première partie est le nom de l’imprimante. La dernière partie (`ipp/port1`) est le chemin de la ressource.

3. Dans le Terminal, tapez `ping myprinter.local` et appuyez sur Entrée.

   Notez l’adresse IP. La sortie obtenue peut ressembler à ceci : `PING myprinter.local (10.50.25.21)`.

4. Utilisez les valeurs de l’adresse IP et du chemin de la ressource. Dans cet exemple, l’adresse IP est `10.50.25.21` et le chemin de ressource est `/ipp/port1`.

## <a name="next-steps"></a>Étapes suivantes

- Passez en revue tous les paramètres pour les appareils [iOS](ios-device-features-settings.md).
- Affectez ce profil à des groupes (découvrez comment [affecter des profils d’appareil](device-profile-assign.md)).
