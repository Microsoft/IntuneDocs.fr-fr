---
title: Configurer l’application Microsoft Managed Home Screen
titleSuffix: Microsoft Intune
description: Découvrez comment configurer l’application Microsoft Managed Home Screen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 092920ddc680b37c365bd8095920ed4244e385ac
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725853"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Configurer l’application Microsoft Managed Home Screen pour Android Entreprise

Managed Home Screen est l’application utilisée pour les appareils d’entreprise Android Entreprise dédiés inscrits par le biais d’Intune et exécutés en mode kiosque multi-application. Pour ces appareils, Managed Home Screen joue le rôle de lanceur pour l’exécution d’autres applications approuvées par-dessus. Managed Home Screen offre aux administrateurs informatiques la possibilité de personnaliser leurs appareils et de limiter les fonctionnalités accessibles à l’utilisateur final. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Quand configurer l’application Microsoft Managed Home Screen ?

En règle générale, si les paramètres vous sont accessibles par le biais de la configuration de l’appareil, vous devez les configurer à cet endroit. Ceci vous permettra de gagner du temps, de limiter les erreurs et de bénéficier d’une meilleure expérience de support Intune. Toutefois, certains paramètres Managed Home Screen sont actuellement disponibles uniquement par le biais du panneau **Stratégies de configuration des applications** dans la console Intune. Dans ce document, vous allez découvrir comment configurer les différents paramètres à l’aide du concepteur de configuration ou d’un script JSON. 

> [!NOTE]
> Il est actuellement possible, et recommandé, de définir les applications répertoriées avec autorisation et les liens web épinglés par le biais d’**Applications clientes** et de **Configuration de l’appareil**. Pour obtenir la liste complète des paramètres disponibles dans **Configuration de l’appareil** ayant un impact sur Managed Home Screen, consultez [Paramètres de l’appareil dédié](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).  

Tout d’abord, accédez à la console Intune dans le portail Azure et accédez à **Applications clientes** > **Stratégies de configuration des applications**. Ajoutez une stratégie de configuration pour les **Appareils gérés** exécutant **Android** et choisissez **Managed Home Screen** comme application associée. Cliquez sur **Paramètres de configuration** pour configurer les différents paramètres Managed Home Screen disponibles. 

## <a name="choosing-a-configuration-settings-format"></a>Choix d’un format des paramètres de configuration

Deux méthodes sont à votre disposition pour définir les paramètres de configuration pour Managed Home Screen :

- Le **concepteur de configuration** vous permet de configurer des paramètres avec une interface utilisateur simple d’utilisation, dans laquelle vous pouvez activer ou désactiver des fonctionnalités et définir des valeurs. Avec cette méthode, il y a quelques clés de configuration désactivées avec le type de valeur `BundleArray`. Ces clés de configuration ne peuvent être configurées qu’en entrant des données JSON. 
- Les **données JSON** vous permettent de définir toutes les clés de configuration possibles à l’aide d’un script JSON. 

Si vous ajoutez des propriétés avec le concepteur de configuration, vous pouvez convertir automatiquement ces propriétés au format JSON en sélectionnant **Entrer des données JSON** dans la liste déroulante **Format des paramètres de configuration**.

![Capture d’écran des options de format de configuration](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Utilisation du concepteur de configuration

Le concepteur de configuration vous permet de sélectionner des paramètres prédéfinis et leurs valeurs associées. 

![Capture d’écran de paramètres de configuration ajoutés](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

Le tableau suivant liste les clés de configuration Managed Home Screen disponibles, les types valeur, les valeurs par défaut et les descriptions. La description indique le comportement attendu de l’appareil d’après les valeurs sélectionnées. Les clés de configuration qui sont désactivées dans le concepteur de configuration ne sont pas mentionnées dans le tableau.

| Clé de configuration | Type de valeur | Valeur par défaut | Description |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Set Grid Size (Définir la taille du quadrillage) | string | Auto | Vous permet de définir la taille du quadrillage pour le positionnement des applications sur l’écran d’accueil géré. Vous pouvez définir le nombre de lignes et de colonnes de l’application pour définir la taille du quadrillage au format suivant `columns;rows`. Si vous définissez la taille du quadrillage, le nombre maximal d’applications qui sont affichées sur une ligne sur l’écran d’accueil correspond au nombre de lignes que vous définissez, et le nombre maximal d’applications qui sont affichées dans une colonne sur l’écran d’accueil correspond au nombre de colonnes que vous définissez. |
| Enable Screen Header (Activer l’en-tête d’écran) | bool | TRUE | Active l’en-tête supérieur pour différentes vues offertes par Managed Home Screen, telles que le flux ou les cartes de flux. Si vous activez ce paramètre, les utilisateurs de l’appareil verront l’en-tête. |
| Enable device status bar (Activer la barre d’état de l’appareil) | bool | TRUE | Active la barre d’état sur l’écran d’accueil (barre supérieure qui affiche les connexions actuelles, telles que Wi-Fi). Si vous activez cette clé de configuration, l’utilisateur final pourra voir les icônes affichées dans les barres d’état qui représentent des connexions et des applications actives. |
| Enable notifications badge (Activer le badge de notification) | bool | FALSE | Active le badge de notification pour les icônes d’application, qui montre le nombre de nouvelles notifications sur l’application. Si vous activez ce paramètre, les utilisateurs finaux verront les badges de notification sur les applications qui ont des notifications non lues. Si vous laissez cette clé de configuration désactivée, l’utilisateur final ne verra aucun badge de notification pour les applications susceptibles d’avoir des notifications non lues. |
| Lock Home Screen (Verrouiller l’écran d’accueil) | bool | TRUE | Supprime la capacité de l’utilisateur final à déplacer des icônes d’application sur l’écran d’accueil. Si vous activez cette clé de configuration, les icônes d’application sur l’écran d’accueil seront verrouillées et l’utilisateur final ne pourra pas les glisser-déplacer vers différentes positions du quadrillage de l’écran d’accueil. Si vous affectez la valeur `false`, les utilisateurs finaux pourront déplacer les icônes d’application et les liens web vers l’écran d’accueil géré.  |
| Set device wall paper (Définir le papier-peint de l’appareil) | string | Par défaut | Vous permet de définir le papier peint de votre choix en entrant l’URL de l’image que vous souhaitez définir comme papier peint. |
| Set app icon size (Définir la taille de l’icône d’application) | integer | 2 | Vous permet de définir la taille d’icône pour les applications affichées sur l’écran d’accueil. Vous pouvez choisir parmi les valeurs suivantes dans cette configuration pour obtenir différentes tailles : 0 (la plus petite), 1 (petite), 2 (normale), 3 (grande) et 4 (la plus grande). |
| Set app folder icon (Définir l’icône du dossier d’application) | integer | 0 | Vous permet de définir l’apparence des dossiers d’application sur l’écran d’accueil. Vous pouvez choisir l’apparence parmi les valeurs suivantes : Carré sombre (0), Cercle sombre (1), Carré clair (2), Cercle clair (3) |
| Enable gestures (Activer les mouvements) | bool | FALSE | Permet à l’utilisateur final d’affecter des actions à différents mouvements tels que le balayage vers le haut ou vers le bas. Si vous désactivez cette clé de configuration, les utilisateurs finaux pourront seulement balayer vers la droite s’il existe une deuxième page et revenir à la page d’accueil. |
| Enable vertical scrolling (Activer le défilement vertical) | bool | FALSE | Active le défilement vertical sur l’écran d’accueil géré. Si vous activez cette clé de configuration, l’utilisateur final pourra uniquement naviguer vers différentes pages verticalement plutôt qu’en balayant horizontalement. |
| Set home screen theme (Définir le thème de l’écran d’accueil) | string | Theme.Light.Blue | Vous permet de choisir le thème de l’écran d’accueil parmi un ensemble prédéfini de thèmes avec différentes couleurs. Vous pouvez choisir les thèmes suivants en entrant la valeur de chaîne au format suivant.   Theme.Light.Green. Où Light peut être remplacé par Dark pour un thème sombre, et Green peut être remplacé par Blue, Yellow, Pink, Red, Orange et Purple. |
| Enable dock (Activer l’ancrage) | bool | FALSE | Active l’affichage de la section d’ancrage d’application au bas de l’écran d’accueil, avec affichage des applications persistantes et point d’entrée pour toutes les applications installées. Si vous activez cette clé de configuration, l’utilisateur final pourra accéder aux applications ancrées, et également à la section Toutes les applications afin d’accéder à la liste de toutes les applications installées sur les appareils, qu’elles aient été répertoriées avec autorisation ou non. |
| Set screen orientation (Définir l’orientation de l’écran) | integer | 1 | Vous permet de définir l’orientation de l’écran d’accueil (en mode portrait ou paysage) ou d’autoriser la rotation automatique. Vous pouvez définir l’orientation en entrant les valeurs 1 (pour le mode portrait), 2 (pour le mode paysage) ou 3 (pour la rotation automatique). |
| Enable home screen feed (Activer le flux d’écran d’accueil) | bool | FALSE | Active le flux de l’écran d’accueil, qui peut être consulté en balayant vers la gauche sur l’écran d’accueil. Ce flux affiche différents types de contenu, tels que des actualités, le calendrier, les applications utilisateur les plus utilisées, l’assistant vocal Cortana, et ainsi de suite. Si vous activez cette option, l’utilisateur final pourra accéder au flux en balayant vers la gauche sur l’écran d’accueil. |
| Enable overview mode (Activer le mode Vue d’ensemble) | bool | FALSE | Permet aux utilisateurs finaux d’ajouter ou de supprimer différentes pages sur l’écran d’accueil accessible en balayant vers la droite sur l’écran par défaut. Si vous activez cette option, l’utilisateur final pourra ajouter des pages à droite de la page par défaut de l’écran d’accueil, changer la page par défaut, et également accéder aux paramètres sur l’écran d’accueil géré. |
| Enable device telemetry (Activer la télémétrie d’appareil) | bool | FALSE | Active toutes les données de télémétrie capturées pour l’écran d’accueil géré. Si vous activez cette option, Microsoft pourra capturer les données de télémétrie de l’appareil, telles que le nombre de fois où une application particulière est lancée sur cet appareil. |
| Set whitelisted applications (Définir les applications répertoriées avec utilisation) | bundleArray | FALSE | Vous permet de définir le jeu d’applications visibles sur l’écran d’accueil parmi les applications installées sur l’appareil. Vous pouvez définir les applications en entrant le nom du package d’application des applications que vous souhaitez rendre visibles. Par exemple, com.microsoft.emmx rendrait les paramètres accessibles sur l’écran d’accueil. Les applications que vous répertoriez avec autorisation dans cette section doivent déjà être installées sur l’appareil afin d’être visibles sur l’écran d’accueil. |
| Set pinned web links (Définir les liens web épinglés) | bundleArray | FALSE | Vous permet d’épingler des sites web sous forme d’icônes de lancement rapide sur l’écran d’accueil. Avec cette configuration, vous pouvez définir l’URL et l’ajouter à l’écran d’accueil pour que l’utilisateur final puisse la lancer dans le navigateur avec un simple clic. |
| Enable search bar (Activer la barre de recherche) | bool | FALSE | Active la barre de recherche sur l’écran d’accueil. Si vous activez cette option, les utilisateurs de l’appareil verront la barre de recherche sur l’écran d’accueil, où ils pourront entrer ce qu’ils souhaitent rechercher sur le web. |
| Disable settings app (Désactiver l’application Paramètres) | bool | FALSE | Désactive la page des paramètres pour l’écran d’accueil géré. Si vous désactivez cette option, l’utilisateur final de l’appareil ne pourra pas accéder aux paramètres de l’écran d’accueil géré. |
| Enable screen saver (Activer l’écran de veille) | bool | FALSE | Pour activer ou pas le mode Écran de veille. Si la valeur est true, vous pouvez configurer **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver** et **media_detect_ screen_saver**. |
| Screen saver image (Image de l’écran de veille) | string |   | Définissez l’URL de l’image de l’écran de veille. Si aucune URL n’est définie, les appareils affichent l’image de l’écran de veille par défaut quand l’écran de veille est activé. L’image par défaut montre l’icône de l’application Managed Home Screen.  |
| Screen saver show time (Durée d’affichage de l’écran de veille) | integer | 0 | Permet de définir la durée (en secondes) d’affichage de l’écran de veille quand le mode Écran de veille est activé. Si la valeur est 0, l’écran de veille s’affichera en mode écran de veille indéfiniment jusqu’à ce que l’appareil redevienne actif.  |
| Inactive time to enable screen saver (Délai d’inactivité avant d’activer l’écran de veille) | integer | 30 | Nombre de secondes pendant lesquelles l’appareil doit être inactif avant le déclenchement de l’écran de veille. Si la valeur est 0, l’appareil ne basculera jamais en mode Écran de veille. |
| Media detect before showing screen saver (Détection de média avant affichage de l’écran de veille) | bool | TRUE | Choisissez si l’écran de l’appareil doit afficher l’écran de veille en cas de lecture audio/vidéo sur l’appareil. Si la valeur est true, l’appareil ne lira pas d’audio/vidéo, Quelle que soit la valeur fournie dans **inactive_time_to_show_scree_saver**. Si la valeur est false, l’écran de l’appareil affichera l’écran de veille conformément à la valeur définie dans **inactive_time_to_show_screen_saver**.   |
| Enable virtual home button (Activer le bouton d’accueil virtuel) | bool | FALSE | Affectez la valeur `True` à ce paramètre pour permettre à l’utilisateur final d’accéder à un bouton d’accueil Managed Home Screen qui le ramènera à l’écran d’accueil géré à partir de la tâche en cours.  |
| Type of virtual home button (Type de bouton d’accueil virtuel) | string | swipe_up | Utilisez **swipe_up** pour accéder au bouton d’accueil avec un mouvement de balayage. Utilisez **float** pour accéder à un bouton d’accueil permanent et persistant qui peut être déplacé sur l’écran par l’utilisateur final. |
| Battery and Signal Strength indicator bar (Barre d’indicateur de batterie et de puissance du signal) | bool | True  | L’affectation de la valeur `True` à ce paramètre permet d’afficher l’indicateur de batterie et de force du signal. |
| Exit lock task mode password (Mot de passe de sortie du mode de verrouillage de tâche) | string |   | Entrez un code de quatre à six chiffres à utiliser pour quitter temporairement le mode de verrouillage de tâche, à des fins de dépannage. |
| Show Wi-Fi setting (Afficher les paramètres Wi-Fi) | bool | FALSE | L’affectation de la valeur `True` à ce paramètre permet à l’utilisateur final d’activer ou de désactiver le Wi-Fi, ou de se connecter à différents réseaux Wi-Fi.  |
| Show Bluetooth setting (Afficher les paramètres Bluetooth) | bool | FALSE | L’affectation de la valeur `True` à ce paramètre permet à l’utilisateur final d’activer ou de désactiver le Bluetooth, ou de se connecter à différents appareils compatibles Bluetooth.   |
| Les applications dans le dossier sont classées par nom | bool | TRUE | L’activation `False` de ce paramètre permet l’affichage d’éléments d’un dossier dans l’ordre dans lequel ils sont spécifiés. Sinon, ils apparaîtront dans le dossier par ordre alphabétique.   |
| Ordre des applications activé | bool | FALSE | L’activation `True` de ce paramètre permet de définir l’ordre des applications, des liens web et des dossiers sur Managed Home Screen. Une fois activé, définissez l’ordre avec **app_order** selon lequel l’utilisateur final peut activer ou désactiver le Bluetooth et se connecter à différents appareils compatibles au Bluetooth.   |
| Ordre des applications | bundleArray | FALSE | Vous permet de spécifier l’ordre des applications, des liens Web et des dossiers sur Managed Home Screen. Pour utiliser ce paramètre, **Verrouiller l’écran d’accueil** doit être activé, **Définir la taille de la grille** doit être défini et **Ordre des applications activé** doit être défini sur `True`.   |

## <a name="enter-json-data"></a>Entrer des données JSON

Entrez des données JSON pour configurer tous les paramètres disponibles pour Managed Home Screen, ainsi que les paramètres désactivés dans le **concepteur de configuration**.

![Capture d’écran de données JSON ajoutées](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

Outre les paramètres configurables listés dans le tableau **Concepteur de configuration** (ci-dessus), le tableau suivant mentionne les clés de configuration que vous pouvez uniquement configurer par le biais de données JSON.

|    Clé de configuration    |    Type de valeur    |    Valeur par défaut    |    Description    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Set whitelisted applications (Définir les applications répertoriées avec utilisation)    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Vous permet de définir le jeu d’applications visibles sur l’écran d’accueil parmi les applications installées sur l’appareil. Vous pouvez définir les applications en entrant le nom du package d’application des applications que vous souhaitez rendre visibles. Par exemple, com.android.settings rendrait les paramètres accessibles sur l’écran d’accueil. Les applications que vous répertoriez avec autorisation dans cette section doivent déjà être installées sur l’appareil afin d’être visibles sur l’écran d’accueil.    |
|    Set pinned web links (Définir les liens web épinglés)    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Vous permet d’épingler des sites web sous forme d’icônes de lancement rapide sur l’écran d’accueil. Avec cette configuration, vous pouvez définir l’URL et l’ajouter à l’écran d’accueil pour que l’utilisateur final puisse la lancer dans le navigateur avec un simple clic.    |
|    Create Managed Folder for grouping apps (Créer un dossier géré pour le regroupement d’applications)    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Vous permet de créer et de nommer des dossiers, et de regrouper des applications au sein de ces dossiers. Les utilisateurs finaux ne pourront pas déplacer les dossiers, renommer les dossiers, ni déplacer les applications dans les dossiers.   Les dossiers apparaîtront dans l’ordre de création, et les applications dans les dossiers apparaîtront dans l’ordre alphabétique.         Remarque : Toutes les applications que vous souhaitez regrouper dans des dossiers doivent être affectées comme Obligatoires sur l’appareil, et doivent avoir été ajoutées à l’écran d’accueil géré.     |

Voici un exemple de script JSON avec toutes les clés de configuration disponibles incluses :

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "grid_size",
            "valueString": "4;5"
        },
        {
            "key": "app_order_enabled",
            "valueBool": true
        },
        {
            "key": "apps_in_folder_ordered_by_name",
            "valueBool": true
        },
        {
            "key": "app_orders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.Microsoft.emmx"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 1
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Work"
                        },
                        {
                            "key": "type",
                            "valueString": "managed_folder"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 2
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.launcher.enterprise"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "class",
                            "valueString": "com.microsoft.launcher.launcher"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 3
                        }
                    ]
                }
            ]
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="googles-android-device-policy-app"></a>Application Android Device Policy de Google
L’application Managed Home Screen permet désormais d’accéder à l’application Android Device Policy de Google. L’application Managed Home Screen est un lanceur personnalisé utilisé pour les appareils inscrits dans Intune en tant qu’appareils dédiés Android Enterprise (AE) utilisant le mode kiosque multi-application. Vous pouvez accéder à l’application Android Device Policy ou guider les utilisateurs vers cette application à des fins de support et de débogage. Cette fonctionnalité de lancement est disponible au moment de l’inscription et du verrouillage de l’appareil dans Managed Home Screen. Aucune installation supplémentaire n’est nécessaire pour utiliser cette fonctionnalité.

## <a name="managed-home-screen-debug-screen"></a>Écran de débogage de Managed Home Screen
Vous pouvez accéder à l’écran de débogage de Managed Home Screen en cliquant sur le bouton **Précédent** jusqu’à ce que l’écran de débogage s’affiche (cliquez sur le bouton **Précédent** 15 fois ou plus). À partir de cet écran de débogage, vous pouvez lancer l’application de stratégie d’appareil Android, afficher et charger des journaux ou suspendre temporairement le mode plein écran pour mettre à jour l’appareil. Pour plus d’informations sur la suspension du mode plein, consultez l’élément **Quitter le mode plein écran** dans les [paramètres de l’appareil dédié](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings) à Android Enterprise.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les appareils Android Entreprise dédiés, consultez [Configurer l’inscription Intune d’appareils Android Entreprise dédiés](../enrollment/android-kiosk-enroll.md).
