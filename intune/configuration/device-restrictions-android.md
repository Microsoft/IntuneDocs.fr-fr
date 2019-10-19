---
title: Paramètres de restriction des appareils pour Android dans Microsoft Intune - Azure | Microsoft Docs
description: Affichez la liste de tous les paramètres d’appareil Android que vous pouvez contrôler et limiter dans Microsoft Intune. Utilisez ces paramètres pour contrôler le mot de passe, accéder à Google Play, autoriser ou interdire des applications, contrôler les paramètres du navigateur, bloquer des applications, sauvegarder sur le cloud Google et contrôler les options message, voix, itinérance des données, Wi-Fi et de connexion Bluetooth.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dfc791450eec9f17be68228bb291ca89fd7d88ce
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506812"
---
# <a name="android-and-samsung-knox-standard-device-restriction-settings-lists-in-intune"></a>Listes des paramètres de restriction des appareils Android et Samsung Knox Standard dans Intune

Cet article décrit tous les paramètres des restrictions d’appareils de Microsoft Intune que vous pouvez configurer pour les appareils exécutant Android.

>[!TIP]
>Si les paramètres souhaités ne sont pas disponibles, vous pouvez normalement configurer vos appareils à l’aide un [profil personnalisé](../custom-settings-android.md).

## <a name="general"></a>Général

- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo. L’option **Non configuré** autorise l’accès à l’appareil photo de l’appareil.
- **Copier et coller (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher le copier-coller. L’option **Non configuré** autorise les fonctions de copier-coller sur l’appareil.
- **Partage du Presse-papiers entre applications (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation du Presse-papiers dans le but d’effectuer des copier-coller entre applications. L’option **Non configuré** autorise l’utilisation du Presse-papiers pour effectuer des copier-coller entre les applications.
- **Envoi des données de diagnostic (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisateur d’envoyer les données de diagnostic de l’appareil. L’option **Non configuré** autorise l’utilisateur à envoyer les données.
- **Réinitialiser (Samsung Knox uniquement)** : autorise l’utilisateur à effectuer une [réinitialisation](../remote-actions/devices-wipe.md) sur l’appareil.
- **Géolocalisation (Samsung Knox uniquement)** : choisissez **Bloquer** pour désactiver l’utilisation des informations d’emplacement sur l’appareil. L’option **Non configuré** autorise l’appareil à utiliser les informations d’emplacement.
- **Mettre hors tension (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisateur de mettre l’appareil hors tension. Si ce paramètre est désactivé, le paramètre **Nombre d’échecs de connexion avant réinitialisation de l’appareil** ne peut pas être défini et ne fonctionne pas. L’option **Non configuré** autorise l’utilisateur à mettre l’appareil hors tension.
- **Capture d’écran (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher les captures d’écran. L’option **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran sous forme d’image.
- **Assistant vocal (Samsung Knox uniquement)** : choisissez **Bloquer** pour désactiver le service S Voice. L’option **Non configuré** autorise l’utilisation du service et de l’application S Voice sur l’appareil. Ce paramètre ne s’applique pas à Bixby ou à l’assistant vocal d’accessibilité qui lit le contenu de l’écran à haute voix.
- **YouTube (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de l’application YouTube. L’option **Non configuré** autorise l’utilisation de l’application YouTube sur l’appareil.
- **Appareils partagés (Samsung Knox uniquement)** : configurer un appareil Samsung Knox Standard géré en tant qu’appareil partagé. Si ce paramètre est défini sur **Autoriser**, les utilisateurs finaux peuvent se connecter et se déconnecter de l’appareil avec leurs informations d’identification Azure AD. L’appareil reste géré, qu’il soit en cours d’utilisation ou non.</br>Utilisée avec un profil de certificat SCEP, cette fonctionnalité autorise les utilisateurs finaux à partager un appareil avec le même ensemble d’applications pour tous les utilisateurs, mais avec leur propre certificat d’utilisateur SCEP. Quand les utilisateurs se déconnectent, toutes les données d’application sont effacées. Cette fonctionnalité est limitée aux applications métier. </br>L’option **Non configuré** empêche plusieurs utilisateurs finaux de se connecter à l’application Portail d’entreprise sur l’appareil avec leurs informations d’identification Azure AD.
- **Empêcher les changements de date et d’heure (Samsung Knox)** : choisissez **Bloquer** pour empêcher l’utilisateur de modifier les paramètres de date et d’heure sur l’appareil. L’option **Non configuré** autorise les utilisateurs à modifier les paramètres de date et d’heure.

## <a name="password"></a>Mot de passe

- **Mot de passe** : **Exige** que l’utilisateur final entre un mot de passe pour accéder à l’appareil. L’option **Non configuré** autorise les utilisateurs à accéder à l’appareil sans entrer de mot de passe.

    > [!NOTE]
    > Les appareils Samsung Knox demandent automatiquement un code PIN à 4 chiffres lors de l’inscription à MDM. Les appareils Android natifs peuvent demander automatiquement un code PIN pour devenir conforme à l’accès conditionnel.

- **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe qu’un utilisateur doit entrer (entre 4 et 16 caractères).
- **Nombre maximal de minutes d’inactivité avant verrouillage de l’écran** : entrez le nombre maximal de minutes d’inactivité autorisées sur l’appareil avant verrouillage de l’écran. Sur un appareil, un utilisateur final ne peut pas définir une valeur de temps supérieure à la durée configurée dans le profil. Un utilisateur final peut définir une valeur de temps inférieure. Par exemple, si le profil est défini sur 15 minutes, un utilisateur final peut définir la valeur sur 5 minutes. Un utilisateur final ne peut pas définir la valeur sur 30 minutes. 
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil.
- **Expiration du mot de passe (jours)** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil.
- **Type de mot de passe obligatoire** : entrez le niveau de complexité du mot de passe exigé, et spécifiez si les appareils biométriques peuvent être utilisés. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Au moins numérique**
  - **Chiffres complexes** : les chiffres répétés ou consécutifs (comme « 1111 » ou « 1234 ») ne sont pas autorisés<sup>1</sup>.
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**
- **Empêcher la réutilisation des mots de passe précédents** : empêche l’utilisateur final de créer un mot de passe qu’il a déjà utilisé.
- **Déverrouillage par empreinte digitale (Samsung Knox uniquement)** : choisissez **Bloquer** afin d’empêcher l’utilisation d’une empreinte digitale pour déverrouiller l’appareil. L’option **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide d’une empreinte digitale.
- **Smart Lock et autres agents de confiance** : choisissez **Bloquer** pour empêcher Smart Lock ou d’autres agents de confiance d’ajuster les paramètres d’écran de verrouillage (Samsung Knox Standard 5.0+). Cette fonctionnalité de téléphone, également connue sous le nom d’agent de confiance, permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil, si ce dernier se trouve dans un emplacement approuvé. Par exemple, elle peut servir lorsque l’appareil est connecté à un appareil Bluetooth spécifique ou quand il se trouve à proximité d’une balise NFC. Vous pouvez utiliser ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.
- **Chiffrement** : choisissez **Exiger** pour que les fichiers soient chiffrés sur l’appareil. Tous les appareils ne prennent pas en charge le chiffrement. Pour pouvoir utiliser cette fonctionnalité, effectuez également les actions suivantes : 
  1. Définissez **Mot de passe** sur **Exiger**.
  2. Définissez **Type de mot de passe requis** sur **Au moins numérique**.
  3. Définissez **Longueur minimale du mot de passe** sur au moins 4 pour signaler correctement la conformité à ce paramètre.

  > [!NOTE]
  > Si une stratégie de chiffrement est appliquée, les appareils Samsung Knox demandent aux utilisateurs de définir un mot de passe complexe de 6 caractères comme code secret de l’appareil.

<sup>1</sup> Avant d’affecter ce paramètre à des appareils, veillez à mettre à jour l’application Portail d’entreprise sur ces appareils.

Si vous définissez **Type de mot de passe requis** sur **Chiffres complexes** et l’affectez à un appareil Android antérieur à la version 5.0, le comportement suivant s’applique :

- Si l’application Portail d’entreprise exécute une version antérieure à 1704, aucune stratégie de code PIN ne s’applique à l’appareil et une erreur s’affiche sur le Portail Azure.
- Si l’application Portail d’entreprise fonctionne avec la version 1704 ou une version ultérieure, un simple code PIN peut être appliqué. Les versions d’Android antérieures à 5.0 ne gèrent pas ce paramètre. Aucune erreur ne s’affiche sur le Portail Azure.

## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de Google Play Store. L’option **Non configuré** autorise l’utilisateur à accéder à Google Play Store sur l’appareil.

## <a name="restricted-apps"></a>Applications restreintes

Utilisez ces paramètres pour autoriser ou empêcher l’utilisation de certaines applications sur l’appareil. Cette fonctionnalité est prise en charge sur les appareils Android et Samsung Knox Standard :

- **Applications interdites** : la liste des applications non gérées par Intune dont vous ne souhaitez pas qu’elles soient installées sur l’appareil. Si un utilisateur installe l’une des applications de cette liste, Intune vous envoie une notification.
- **Applications approuvées** : la liste des applications que les utilisateurs sont autorisés à installer. Pour rester conformes, ils ne doivent pas installer d’autres applications. Les applications qui sont gérées par Intune sont autorisées automatiquement.

Pour ajouter une application à ces listes, vous pouvez :

- **Ajouter** l’URL Google Play Store de l’application que vous souhaitez. Par exemple, pour ajouter l’application Bureau à distance Microsoft pour Android, entrez `https://play.google.com/store/apps/details?id=com.microsoft.rdc.android`. Pour trouver l’URL d’une application, ouvrez [Google Play Store](https://play.google.com/store/apps) et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop Play Store` ou `Microsoft Planner`. Sélectionnez l’application et copiez l’URL.
- Importez un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format <*URL de l’application*>, <*nom de l’application*>, <*éditeur de l’application*>. Vous pouvez sinon **exporter** une liste existante comportant la liste des applications restreintes au même format.

> [!IMPORTANT]
> Les profils d’appareils qui utilisent les paramètres d’applications restreintes doivent être affectés à des groupes d’utilisateurs.

## <a name="browser"></a>Navigateur

- **Navigateur Web (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation du navigateur web par défaut sur l’appareil. L’option **Non configuré** autorise l’utilisation du navigateur web par défaut de l’appareil.
- **Remplissage automatique (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher le remplissage automatique du texte dans le navigateur. L’option **Non configuré** autorise l’utilisation de la fonction de remplissage automatique du navigateur web.
- **Cookies (Samsung Knox uniquement)** : choisissez la façon dont vous souhaitez gérer les cookies des sites web sur l’appareil. Les options disponibles sont les suivantes :
  - Autoriser
  - Bloquer tous les cookies
  - Autoriser les cookies des sites web visités
  - Autoriser les cookies du site web actuel
- **JavaScript (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher le navigateur web d’exécuter des scripts Java. L’option **Non configuré** autorise le navigateur web de l’appareil à exécuter des scripts Java.
- **Fenêtres contextuelles (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’affichage de fenêtres contextuelles dans le navigateur web. L’option **Non configuré** autorise les fenêtres contextuelles dans le navigateur web.

## <a name="allow-or-block-apps"></a>Autoriser ou bloquer des applications

Utilisez ces paramètres pour autoriser, bloquer ou masquer des applications spécifiques sur des appareils Samsung Knox Standard. Il n’est pas possible d’ouvrir ou d’exécuter des applications masquées.

Les options disponibles sont les suivantes :

- **Applications dont l’installation est autorisée (Samsung Knox Standard uniquement)**
- **Applications dont le lancement est bloqué (Samsung Knox Standard uniquement)**
- **Applications masquées pour l’utilisateur (Samsung Knox Standard uniquement)**

Pour chaque paramètre, ajoutez une liste d’applications. Les options disponibles sont les suivantes :

- **Ajouter des applications par nom de package** : principalement utilisé pour les applications métier. Entrez le nom de l’application et le nom du package de l’application.
- **Ajouter des applications par URL** : entrez le nom de l’application et son URL dans Google Play Store.
- **Ajouter une application du Store** : sélectionnez une application dans la liste des applications gérées dans Intune.

## <a name="cloud-and-storage"></a>Cloud et stockage

- **Sauvegarde Google (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’appareil de se synchroniser avec la sauvegarde Google. L’option **Non configuré** autorise l’utilisation de la sauvegarde Google.
- **Synchronisation automatique de compte Google (Samsung Knox uniquement)** : choisissez **Bloquer** pour bloquer la fonctionnalité de synchronisation automatique de compte Google sur l’appareil. L’option **Non configuré** autorise la synchronisation automatique des paramètres du compte Google.
- **Stockage amovible (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’appareil d’utiliser le stockage amovible. L’option **Non configuré** autorise l’appareil à utiliser du stockage amovible, comme une carte mémoire Secure Digital.
- **Chiffrement sur des cartes de stockage (Samsung Knox uniquement)** : l’option **Exiger** spécifie que les cartes de stockage doivent être chiffrées. L’option **Non configuré** autorise l’utilisation de cartes de stockage non chiffrées. Tous les appareils ne prennent pas en charge le chiffrement des cartes de stockage. Vérifiez auprès du fabricant de l’appareil.

## <a name="cellular-and-connectivity"></a>Cellulaire et connectivité

- **Itinérance de données (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’itinérance de données sur le réseau cellulaire. L’option **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.
- **Messagerie SMS/MMS (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de la messagerie texte sur l’appareil. L’option **Non configuré** autorise l’utilisation de la messagerie SMS et MMS sur l’appareil.
- **Numérotation vocale (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de numérotation vocale sur l’appareil. L’option **Non configuré** autorise la numérotation vocale sur l’appareil.
- **Itinérance vocale (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’itinérance vocale sur le réseau cellulaire. L’option **Non configuré** autorise l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
- **Bluetooth (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation du Bluetooth sur l’appareil. L’option **Non configuré** autorise l’utilisation du Bluetooth sur l’appareil.
- **NFC (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation de la technologie de communication en champ proche (NFC). L’option **Non configuré** autorise les opérations qui utilisent la communication en champ proche sur les appareils pris en charge.
- **Wi-Fi (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation du Wi-Fi sur l’appareil. L’option **Non configuré** autorise l’utilisation des fonctionnalités Wi-Fi de l’appareil.
- **Partage de connexion Wi-Fi (Samsung Knox uniquement)** : choisissez **Bloquer** pour empêcher l’utilisation du partage de connexion Wi-Fi sur l’appareil. L’option **Non configuré** autorise l’utilisation du partage de connexion Wi-Fi sur l’appareil.

## <a name="kiosk"></a>Kiosk

Les paramètres Kiosk s’appliquent uniquement aux appareils Samsung Knox Standard et uniquement aux applications que vous gérez à l’aide d’Intune.

- Ajoutez les applications à exécuter quand l’appareil est en mode plein écran. Dans ce mode, seules les applications ajoutées sont exécutées ; les applications non ajoutées ne s’exécutent pas. Les navigateurs pré-installés ne s’exécutent pas en tant qu’applications quand l’appareil est en mode plein écran. Si un navigateur est requis, considérez l’utilisation de [Managed Browser](../apps/app-configuration-managed-browser.md).

  Options de l’application :

  - **Ajouter des applications par nom de package** : principalement utilisé pour les applications métier. Entrez le nom de l’application et le nom du package de l’application.
  - **Ajouter des applications par URL** : entrez le nom de l’application et son URL dans Google Play Store.
  - **Ajouter une application du Store** : sélectionnez une application dans la liste des applications gérées dans Intune.

- **Bouton de mise en veille de l’écran** : choisissez **Bloquer** pour bloquer ou masquer le bouton de mise en veille de l’écran. L’option **Non configuré** autorise le bouton de sortie de veille de l’écran sur l’appareil.
- **Boutons de volume** : choisissez **Bloquer** pour empêcher l’utilisateur d’ajuster le volume en désactivant les boutons de volume. L’option **Non configuré** autorise l’utilisation des boutons de volume sur l’appareil.

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](../device-profile-assign.md) et [suivre son état](../device-profile-monitor.md).

Vous pouvez également créer des profils plein écran pour des appareils [Android pour les entreprises](device-restrictions-android-for-work.md#dedicated-device-settings) et [Windows 10](kiosk-settings.md).
