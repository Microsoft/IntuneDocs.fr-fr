---
title: "Importation des paramètres Wi-Fi pour Windows 8.1 et versions ultérieures | Version préliminaire d’Intune Azure | Microsoft Docs"
description: "Version préliminaire d’Intune Azure : guide pratique d’importation des paramètres Wi-Fi de Windows dans un profil Wi-Fi Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c4e9b19-b268-4f6d-9663-7cdbe4e4a8dd
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 938129f210d1a4a6b4719deb63d1dc47dad21b29
ms.openlocfilehash: 132ce1c8e6ad69c5d8998f233c114f912cb4bf8b


---

# <a name="how-to-import-wi-fi-settings-for-windows-81-and-later-devices-in-intune-azure-preview"></a>Guide pratique d’importation des paramètres Wi-Fi pour appareils Windows 8.1 et versions ultérieures dans la version préliminaire d’Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Pour les appareils qui exécutent un appareil de bureau ou mobile Windows 8.1 ou Windows 10 , vous pouvez importer un profil de configuration Wi-Fi précédemment exporté vers un fichier.

## <a name="export-wi-fi-settings-from-a-windows-device"></a>Exportation des paramètres Wi-Fi depuis un appareil Windows

Dans Windows, recourez à l’utilitaire **netsh wlan** pour exporter un profil Wi-Fi existant dans un fichier XML lisible par Intune. Sur un ordinateur Windows où le profil Wi-Fi requis est déjà installé, utilisez la procédure suivante.
1. Créez un dossier local pour les profils Wi-Fi exportés, comme **c:\WiFi**.
1. Ouvrez une invite de commandes en tant qu’administrateur.
1. Exécutez la commande **netsh wlan show profiles** et notez le nom du profil que vous voulez exporter. Dans cet exemple, le nom du profil est **WiFiName**.
1. Exécutez la commande suivante : **netsh wlan export profile name="ProfileName" folder=c:\Wifi**. Celle-ci crée un fichier de profil Wi-Fi nommé **Wi-Fi-WiFiName.xml** dans le dossier de destination.

## <a name="import-the-wi-fi-settings-into-intune"></a>Importation des paramètres Wi-Fi dans Intune

1. Connectez-vous au portail Azure.
2. Choisissez **Plus de services** > **Autres** > **Intune**.
3. Dans le panneau **Intune**, choisissez **Configurer des appareils**.
2. Dans le panneau **Configuration de l’appareil**, choisissez **Gérer** > **Profils**.
3. Dans le panneau de profils, cliquez sur **Créer un profil**.
4. Dans le panneau **Créer un profil**, entrez un **Nom** et une **Description** pour le profil de restriction d'appareil.
5. À partir de la liste déroulante **Plateforme**, sélectionnez **Windows 8.1 et versions ultérieures**.
6. À partir de la liste déroulante de types **Profil**, choisissez **Importation Wi-Fi**.
7. Dans le panneau **Wi-Fi de base**, configurez les éléments suivants :
    - **Nom de connexion** : saisissez le nom de la connexion Wi-Fi. Ce nom s’affichera pour les utilisateurs finaux lorsqu’ils parcourent les réseaux Wi-Fi disponibles.
    - **XML du profil** : cliquez sur le bouton Parcourir pour sélectionner le fichier XML contenant les paramètres de profil Wi-Fi que vous voulez importer dans Intune.
    - **Contenu du fichier** : affiche le code XML du profil de configuration que vous avez sélectionné.
8. Lorsque vous avez terminé, revenez au panneau **Créer un profil** et appuyez sur **Créer**.

Le profil est créé et s’affiche dans le volet de la liste des profils.



<!--HONumber=Feb17_HO1-->


