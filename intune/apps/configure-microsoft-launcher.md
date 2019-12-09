---
title: Configurer Microsoft Launcher pour Android Entreprise avec Intune
titleSuffix: ''
description: Utiliser des stratégies de configuration Intune avec Microsoft Launcher.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1dc2e2ce7e19933accdb1063ccacf99fa3f54b09
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563964"
---
# <a name="configure-microsoft-launcher"></a>Configurer Microsoft Launcher

Microsoft Launcher est une application Android qui permet aux utilisateurs de personnaliser leur téléphone, de rester organisés pendant leurs déplacements et de passer du travail sur leur téléphone au travail sur leur ordinateur. 

Sur les appareils Android Entreprise entièrement gérés, Launcher permet aux administrateurs informatiques de l’entreprise de personnaliser les écrans d’accueil des appareils gérés en sélectionnant le papier peint, les applications et les positions des icônes. Cela permet de standardiser l’apparence de tous les appareils Android gérés sur différents appareils OEM et versions système. 

## <a name="how-to-configure-the-microsoft-managed-home-screen-app"></a>Procédure de configuration de l’application Microsoft Managed Home Screen 

Ouvrez le [Centre d’administration de Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), puis sélectionnez **Applications** > **Stratégies de configuration des applications**. Ajoutez une stratégie de configuration pour les **Appareils gérés** exécutant **Android** et choisissez **Microsoft Launcher** comme application associée. Cliquez sur **Paramètres de configuration** pour configurer les différents paramètres Managed Home Screen disponibles. 

## <a name="choosing-a-configuration-settings-format"></a>Choix d’un format des paramètres de configuration 

Deux méthodes sont à votre disposition pour définir les paramètres de configuration pour Managed Home Screen : 

- Le **concepteur de configuration** vous permet de configurer des paramètres avec une interface utilisateur simple d’utilisation, dans laquelle vous pouvez activer ou désactiver des fonctionnalités et définir des valeurs. Avec cette méthode, il y a quelques clés de configuration désactivées avec le type de valeur BundleArray. Ces clés de configuration ne peuvent être configurées qu’en entrant des données JSON. 

- Les **données JSON** vous permettent de définir toutes les clés de configuration possibles à l’aide d’un script JSON. 

Si vous ajoutez des propriétés avec le **concepteur de configuration**, vous pouvez convertir automatiquement ces propriétés au format JSON en sélectionnant **Entrer des données JSON** dans la liste déroulante **Format des paramètres de configuration**, comme indiqué ci-dessous.

   ![Format des paramètres de configuration : utiliser le concepteur de configuration](./media/configure-microsoft-launcher/configure-microsoft-launcher-01.png)

## <a name="using-configuration-designer"></a>Utilisation du concepteur de configuration

Le concepteur de configuration vous permet de sélectionner des paramètres prédéfinis et leurs valeurs associées.

   ![Format des paramètres de configuration : entrer les données JSON](./media/configure-microsoft-launcher/configure-microsoft-launcher-02.png)

Le tableau suivant liste les clés de configuration Microsoft Launcher disponibles, les types valeur, les valeurs par défaut et les descriptions. La description indique le comportement attendu de l’appareil d’après les valeurs sélectionnées. Les clés de configuration qui sont désactivées dans le concepteur de configuration ne sont pas mentionnées dans le tableau.

|    Clé Configuration    |    Type de valeur    |    Valeur par défaut    |    Description     |
|---------------------------------------------------|------------------|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Type d'inscription    |    Chaîne     |    Par défaut    |    Vous permet de définir le type d’inscription auquel cette stratégie doit s’appliquer. Actuellement, la valeur **Par défaut** fait référence à **CorporateOwnedBuisnessOnly**. Actuellement, aucun autre type d’inscription n’est pris en charge.        Nom de la clé JSON : management_mode_key        |
|    Changement de l’ordre des applications de l’écran d’accueil par l’utilisateur autorisé    |    Booléen    |    True    |    Vous permet de spécifier si le paramètre **Ordre des applications de l’écran d’accueil** peut être modifié par l’utilisateur final.<ul><li>Si la valeur est **True**, l’ordre des applications défini dans la stratégie ne sera appliqué que pour le déploiement initial. Par la suite, la stratégie ne sera pas appliquée pour respecter les modifications éventuellement apportées par l’utilisateur.</li><li>Si la valeur est **False**, l’ordre des applications sera appliqué à chaque synchronisation.</li></ul><br>**Remarque :** L’ordre des applications de l’écran d’accueil ne peut être configuré qu’à l’aide de l’éditeur JSON.<br><br>Nom de la clé JSON :<br>`com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed`    |
|    Set Grid Size (Définir la taille du quadrillage)    |    Chaîne    |    Auto    |    Vous permet de définir la taille du quadrillage pour le positionnement des applications sur l’écran d’accueil géré. Vous pouvez définir le nombre de lignes et de colonnes de l’application pour définir la taille du quadrillage au format suivant : `columns;rows`. Si vous définissez la taille du quadrillage, le nombre maximal d’applications qui sont affichées sur une ligne sur l’écran d’accueil correspond au nombre de lignes que vous définissez, et le nombre maximal d’applications qui sont affichées dans une colonne sur l’écran d’accueil correspond au nombre de colonnes que vous définissez.<br><br>        Nom de la clé JSON :<br>`com.microsoft.launcher.HomeScreen.GridSize`    |
|    Définir le papier peint de l’appareil    |    Chaîne    |    Null    |    Vous permet de définir le papier peint de votre choix en entrant l’URL de l’image que vous souhaitez définir comme papier peint.<br><br>Nom de la clé JSON :<br>`com.microsoft.launcher.Wallpaper.URL`    |
|    Définir la modification du papier peint de l’appareil par utilisateur comme autorisée    |    Bool    |    True    |    Vous permet de spécifier si le paramètre de papier peint défini de l’appareil peut être modifié par l’utilisateur final.<ul><li>Si la valeur est **True**, le papier peint de la stratégie ne sera appliqué que pour le déploiement initial. Par la suite, la stratégie ne sera pas appliquée pour respecter les modifications éventuellement apportées par l’utilisateur.</li><li>Si la valeur est **False**, le papier peint sera appliqué à chaque synchronisation.</li></ul><br>Nom de la clé JSON :<br>`com.microsoft.launcher.Wallpaper.URL.UserChangeAllowed`        |
|    Activation du flux    |    Booléen    |    True    |    Vous permet d’activer le flux de lancement sur l’appareil lorsque l’utilisateur passe à droite sur l’écran d’accueil.<ul><li>Si la valeur est **True**, le flux sera activé.</li><li>Si la valeur est **False**, le flux sera désactivé.</li></ul><br>Nom de la clé JSON :<br>`com.microsoft.launcher.Feed.Enabled`    |
|    Changement d’activation de flux autorisé par l’utilisateur    |    Booléen    |    True    |     Vous permet de spécifier si l’**Activation de flux** peut être modifiée par l’utilisateur final.<ul><li>Si la valeur est **True**, le flux ne sera appliqué que pour le déploiement initial. Par la suite, la stratégie ne sera pas appliquée pour respecter les modifications éventuellement apportées par l’utilisateur.</li><li>Si la valeur est **False**, le flux sera appliqué à chaque synchronisation.</li></ul><br>Nom de la clé JSON : `com.microsoft.launcher.Feed.Enabled.UserChangeAllowed`    |

## <a name="enter-json-data"></a>Entrer des données JSON

Entrez des données JSON pour configurer tous les paramètres disponibles pour Microsoft Launcher, ainsi que les paramètres désactivés dans le **concepteur de configuration**, comme indiqué ci-dessous.

   ![Concepteur de configuration : données JSON](./media/configure-microsoft-launcher/configure-microsoft-launcher-03.png)

Outre les paramètres configurables listés dans le tableau Concepteur de configuration (ci-dessus), le tableau suivant mentionne les clés de configuration que vous pouvez uniquement configurer par le biais de données JSON.

|    Clé Configuration    |    Type de valeur    |    Valeur par défaut    |    Description     |
|----------------------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Set Allow-Listed Applications (Définir les applications répertoriées comme autorisées)<br>Clé JSON :`com.microsoft.launcher.HomeScreen.Applications`    |    BundleArray    | Consultez : [Set whitelisted applications](configure-microsoft-launcher.md#set-allow-listed-applications)</sup> (Définir les applications répertoriées avec utilisation)    |    Vous permet de définir le jeu d’applications visibles sur l’écran d’accueil parmi les applications installées sur l’appareil. Vous pouvez définir les applications en entrant le nom du package d’application des applications que vous souhaitez rendre visibles. Par exemple, `com.android.settings` rendrait les paramètres accessibles sur l’écran d’accueil. Les applications que vous répertoriez avec autorisation dans cette section doivent déjà être installées sur l’appareil afin d’être visibles sur l’écran d’accueil.<p>Propriétés :<ul><li>**Package :** le nom du package d'application</li><li>**Classe :** l’activité de l’application, qui est spécifique à une certaine page d’application. Elle utilise la page d’application par défaut si cette valeur est vide.</li></ul>      |
|    Ordre des applications de l’écran d’accueil<br>Clé JSON : `com.microsoft.launcher.HomeScreen.AppOrder`    |    BundleArray    |    Consultez : [Ordre des applications de l’écran d’accueil](configure-microsoft-launcher.md#home-screen-app-order)      |    Vous permet de spécifier l’ordre des applications sur l’écran d’accueil.<p>Propriétés :<br><ul><li>**Type :** Le seul type pris en charge est `application`.</li><li>**Position :** L’emplacement de l’icône d’application sur l’écran d’accueil. Cela part de la position 1 en haut à gauche, et se déplace de la gauche vers la droite, de haut en bas.</li><li>**Package :** le nom du package d'application.</li><li>**Classe :** l’activité de l’application, qui est spécifique à une certaine page d’application. La page d’application par défaut est utilisée si cette valeur est vide.</li></ul>    |

### <a name="set-allow-listed-applications"></a>Set whitelisted applications (Définir les applications répertoriées avec utilisation)

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.Applications",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

### <a name="home-screen-app-order"></a>Ordre des applications de l’écran d’accueil

```JSON
{
    "key": "com.microsoft.launcher.HomeScreen.AppOrder",
    "valueBundleArray": 
    [
        {
            "managedProperty": [
                {
                    "key": "type",
                    "valueString": "application"
                },
                {
                    "key": "position",
                    "valueInteger": 0
                },
                {
                    "key": "package",
                    "valueString": ""
                },
                {
                    "key": "class",
                    "valueString": ""
                }
            ]
        }
    ]
}
```

Voici un exemple de script JSON avec toutes les clés de configuration disponibles incluses :

```JSON
{
    "kind": "androidenterprise#managedConfiguration", 
    "productId": "app:com.microsoft.launcher", 
    "managedProperty": [
        {
            "key": "management_mode_key", 
            "valueString": "Default"
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Feed.Enable", 
            "valueBool": true
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.Wallpaper.Url", 
            "valueBool": "http://www.contoso.com/wallpaper.png"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.GridSize", 
            "valueString": "5;5"
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.Applications", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder.UserChangeAllowed", 
            "valueBool": false
        }, 
        {
            "key": "com.microsoft.launcher.HomeScreen.AppOrder", 
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 17
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.ups.mobile.android"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 18
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.teams"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }, 
                {
                    "managedProperty": [
                        {
                            "key": "type", 
                            "valueString": "application"
                        }, 
                        {
                            "key": "position", 
                            "valueInteger": 19
                        }, 
                        {
                            "key": "package", 
                            "valueString": "com.microsoft.bing"
                        }, 
                        {
                            "key": "class", 
                            "valueString": ""
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les appareils Android Entreprise entièrement gérés, consultez [Configurer l’inscription Intune d’appareils Android Entreprise entièrement gérés](../enrollment/android-fully-managed-enroll.md).
