---
title: Importer des paramètres Wi-Fi pour des appareils Windows dans Microsoft Intune - Azure | Microsoft Docs
description: Exportez des paramètres Wi-Fi à partir d’un appareil Windows dans un fichier XML à l’aide de netsh wlan. Ensuite, importez ce fichier dans Intune pour créer un profil Wi-Fi pour les appareils exécutant Windows 8.1, Windows 10 et Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f79ccdc71ddbfa3f25daef629515fb612de01852
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207007"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importer des paramètres Wi-Fi pour des appareils Windows dans Intune

Pour les appareils qui exécutent Windows, vous pouvez importer un profil de configuration Wi-Fi précédemment exporté vers un fichier. **Pour Windows 10 et versions ultérieures, vous pouvez aussi [créer un profil Wi-Fi](wi-fi-settings-windows.md) directement dans Intune**.

S’applique à :  
- Windows 8.1 et versions ultérieures
- Windows 10 et versions ultérieures
- Windows 10 Desktop ou Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportation des paramètres Wi-Fi depuis un appareil Windows

Dans Windows, utilisez `netsh wlan` pour exporter un profil Wi-Fi existant dans un fichier XML lisible par Intune. La clé doit être exportée en texte brut pour pouvoir utiliser le profil.

Sur un ordinateur Windows où le profil Wi-Fi nécessaire est déjà installé, suivez les étapes suivantes :

1. Créez un dossier local pour les profils Wi-Fi exportés, comme **c:\WiFi**.
2. Ouvrez une invite de commandes en tant qu’administrateur.
3. Exécutez la commande `netsh wlan show profiles`. Notez le nom du profil que vous souhaitez exporter. Dans cet exemple, le nom du profil est **WiFiName**.
4. Exécutez la commande `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Cette commande permet de créer un fichier de profil Wi-Fi nommé **Wi-Fi-WiFiName.xml** dans votre dossier cible.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importation des paramètres Wi-Fi dans Intune

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Saisissez les paramètres suivants :

    - **Nom** : Entrez un nom descriptif pour le profil. Le nom **doit** être identique à celui de l’attribut name du fichier XML du profil Wi-Fi. Sinon, l’opération est un échec.
    - **Description** : entrez une description qui présente le paramètre et tout autre détail important.
    - **Plateforme** : Sélectionnez **Windows 8.1 et versions ultérieures**.
    - **Type de profil** : Sélectionnez **Importation Wi-Fi**.

    > [!IMPORTANT]
    > - Si vous exportez un profil Wi-Fi contenant une clé prépartagée, vous **devez** ajouter `key=clear` à la commande. Par exemple, entrez : `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - Le fait d’utiliser une clé prépartagée avec Windows 10 provoque l’affichage d’une erreur de correction dans Intune. Quand cela se produit, le profil Wi-Fi est correctement affecté à l’appareil et fonctionne comme prévu.
    > - Si vous exportez un profil Wi-Fi incluant une clé prépartagée, vérifiez que le fichier est protégé. La clé est au format texte brut, vous êtes donc responsable de sa protection.

4. Saisissez les paramètres suivants :

    - **Nom de connexion** : Entrez un nom pour la connexion Wi-Fi. Ce nom est présenté aux utilisateurs lorsqu’ils parcourent les réseaux Wi-Fi disponibles.
    - **Profil XML** : sélectionnez le bouton Parcourir et choisissez le fichier XML qui contient les paramètres du profil Wi-Fi que vous voulez importer.
    - **Contenu du fichier** : affiche le code XML du profil de configuration que vous avez sélectionné.

5. Cliquez sur **OK** pour enregistrer vos modifications.
6. Une fois terminé, sélectionnez **OK** > **Créer** pour créer le profil Intune. Quand vous avez terminé, votre profil apparaît dans la liste **Appareils - Profils de configuration**.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien. Vous devez à présent [affecter le profil](../device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Consultez [Vue d’ensemble des paramètres Wi-Fi](wi-fi-settings-configure.md), notamment les autres plateformes disponibles.
