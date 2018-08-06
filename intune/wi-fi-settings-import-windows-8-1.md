---
title: Importer des paramètres Wi-Fi pour des appareils Windows dans Microsoft Intune - Azure | Microsoft Docs
description: Exportez des paramètres Wi-Fi à partir d’un appareil Windows dans un fichier XML à l’aide de netsh wlan. Ensuite, importez ce fichier dans Intune pour créer un profil Wi-Fi pour les appareils exécutant Windows 8.1, Windows 10 et Windows Holographic for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ce5cdd9509ed3407491714ccfa853613eb43973
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321133"
---
# <a name="import-wi-fi-settings-for-windows-devices-in-intune"></a>Importer des paramètres Wi-Fi pour des appareils Windows dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pour les appareils qui exécutent Windows, vous pouvez importer un profil de configuration Wi-Fi précédemment exporté vers un fichier. **Pour Windows 10 et versions ultérieures, vous pouvez [créer un profil Wi-Fi](wi-fi-settings-windows.md) directement dans Intune**.

S'applique à :  
- Windows 8.1 et versions ultérieures
- Windows 10 et versions ultérieures
- Windows 10 Desktop ou Mobile
- Windows Holographic for Business

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportation des paramètres Wi-Fi depuis un appareil Windows

Dans Windows, utilisez **netsh wlan** pour exporter un profil Wi-Fi existant dans un fichier XML lisible par Intune. La clé doit être exportée en texte brut pour pouvoir utiliser le profil.

Sur un ordinateur Windows où le profil Wi-Fi nécessaire est déjà installé, suivez les étapes suivantes :

1. Créez un dossier local pour les profils Wi-Fi exportés, comme **c:\WiFi**.
2. Ouvrez une invite de commandes en tant qu’administrateur.
3. Exécutez la commande `netsh wlan show profiles` et notez le nom du profil à exporter. Dans cet exemple, le nom du profil est **WiFiName**.
4. Exécutez la commande `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Elle permet de créer un fichier de profil Wi-Fi nommé **Wi-Fi-WiFiName.xml** dans votre dossier cible.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importation des paramètres Wi-Fi dans Intune

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
4. Entrez un **Nom** et une **Description** pour le profil de restriction de l’appareil.

    > [!IMPORTANT]
    > - Le nom **doit** être identique à celui de l’attribut name du fichier XML du profil Wi-Fi. Sinon, l’opération est un échec.
    > - Si vous exportez un profil Wi-Fi contenant une clé prépartagée, vous **devez** ajouter `key=clear` à la commande. Par exemple, entrez : `netsh wlan export profile name="ProfileName" key=clear folder=c:\Wifi`
    > - L’utilisation d’une clé prépartagée avec Windows 10 entraîne l’apparition d’une erreur de correction dans Intune. Quand cela se produit, le profil Wi-Fi est correctement affecté à l’appareil et fonctionne comme prévu.
    > - Si vous exportez un profil Wi-Fi incluant une clé prépartagée, vérifiez que le fichier est protégé. La clé est au format texte brut, vous êtes donc responsable de sa protection.

5. Dans **Plateforme**, sélectionnez **Windows 8.1 et ultérieur**.
6. Dans **Type de profil**, sélectionnez **Importation Wi-Fi**.
7. Configurez les paramètres suivants :
  - **Nom de la connexion** : entrez le nom de la connexion Wi-Fi. Ce nom s’affiche pour les utilisateurs finaux quand ils parcourent les réseaux Wi-Fi disponibles.
  - **Profil XML** : cliquez sur le bouton Parcourir pour sélectionner le fichier XML contenant les paramètres de profil Wi-Fi à importer dans Intune.
  - **Contenu du fichier** : permet d’afficher le code XML du profil de configuration sélectionné.
8. Une fois que vous avez fini, choisissez **OK**, puis **Créer** pour créer le profil.

Le profil est créé et apparaît dans la liste des profils.
