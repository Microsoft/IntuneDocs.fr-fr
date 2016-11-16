---
title: Ajouter des applications pour les appareils inscrits | Microsoft Intune
description: "Avant de déployer une application, vous devez l’ajouter à Intune. Vous la retrouverez ensuite dans la console Intune, où vous pourrez la déployer et la gérer."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: 239a4b932eed61fc0b2b870892730330565eac93


---

# Ajouter des applications pour les appareils inscrits à Intune

Avant de déployer ou de gérer une application, vous devez l’ajouter à Microsoft Intune. Cette rubrique vous montre comment ajouter des applications pour les appareils inscrits.


> [!IMPORTANT]
> Les informations contenues dans cette rubrique vous aident à ajouter des applications que vous souhaitez déployer sur des appareils et des PC Windows inscrits. Si vous souhaitez ajouter des applications pour des PC Windows que vous gérez à l’aide du logiciel client Intune, consultez [Ajouter des applications pour des PC Windows dans Microsoft Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

## Ajouter l’application
Vous utiliserez l'Éditeur de logiciel Intune pour configurer les propriétés de l'application et, le cas échéant, effectuer son chargement vers votre espace de stockage cloud. Utilisez la procédure suivante :

1.  Dans la [console Administrateur Microsoft Intune](https://manage.microsoft.com), sélectionnez **Applications** &gt; **Ajouter des applications** pour démarrer l’éditeur de logiciel Microsoft Intune.

    > [!TIP]
    > Vous devrez peut-être entrer votre nom d’utilisateur et votre mot de passe Intune avant le démarrage de l’éditeur.

2.  Dans la page **Installation du logiciel** de l’Éditeur de logiciel, choisissez l’une des options suivantes pour **Spécifier comment ce logiciel doit être mis à disposition des appareils** :
    - **Programme d’installation du logiciel**, pour les applications avec l’extension **.msi** ou **.exe** :
        - **Sélectionnez le type de fichier du programme d’installation du logiciel**. Cela indique le type de logiciel que vous souhaitez déployer. Par exemple, si vous souhaitez installer une application iOS, sélectionnez **Package d’application pour iOS (fichier &#42;.ipa)**.
        - **Spécifier l’emplacement des fichiers d’installation du logiciel**. Entrez l’emplacement des fichiers d’installation ou choisissez **Parcourir** pour sélectionner l’emplacement dans la liste.
        - **Inclure les autres fichiers et sous-dossiers du dossier**. Cette option est réservée au type de fichier **Windows Installer** uniquement.<br>Certains logiciels qui utilisent Windows Installer nécessitent la prise en charge des fichiers qui se trouvent généralement dans le même dossier que les fichiers d'installation. Sélectionnez cette option si vous souhaitez également déployer ces fichiers.<br>Ce type d'installation utilise une partie de votre espace de stockage cloud.

  -   **Lien externe**, pour les applications que vous souhaitez créer en spécifiant un lien vers un magasin d’applications :

        - **Spécifiez l’URL**. Spécifiez l’URL de l’un des éléments suivants :
            - L’URL du magasin d’applications de l’application que vous souhaitez déployer. Par exemple, si vous souhaitez déployer l’application Bureau à distance Microsoft pour Android, spécifiez **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android**.<br>Pour rechercher l'URL de l'application, utilisez un moteur de recherche pour rechercher la page du magasin d’applications contenant l'application. Par exemple, pour trouver l’application Bureau à distance, vous pouvez rechercher **Bureau à distance Microsoft Android**.
            - Un site web. Intune déploiera une icône de raccourci vers le site de l’appareil (clip web).
            - Application sur le web. Intune déploiera une icône de raccourci vers l’application sur l’appareil.
        - **Demander un navigateur géré pour ouvrir ce lien (Android et iOS uniquement)**. Lorsque vous déployez un lien vers un site web ou une application web pour les utilisateurs, ils ne peuvent l’ouvrir que dans le navigateur géré Intune. Ce navigateur doit être installé sur leur appareil.<br>Pour plus d’informations sur Managed Browser, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).<br>Ce type d'installation n'utilise pas du tout votre espace de stockage cloud.

  -   **Application iOS gérée à partir de l’App Store**, pour les applications gratuites du magasin iTunes que vous souhaitez gérer avec des stratégies de gestion des applications mobiles (GAM) :

        - **Spécifiez l’URL**. Saisissez l’URL du magasin d’applications de l’application que vous souhaitez déployer. Par exemple, si vous souhaitez déployer l’application Dossiers de travail Microsoft pour iOS, spécifiez **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8**.<br>Ce type d'installation n'utilise pas du tout votre espace de stockage cloud.

        Par exemple, si vous souhaitez déployer l’application Microsoft Word à partir du magasin iTunes vers des appareils, la page ressemble à ceci :

        ![Éditeur de logiciel Intune](./media/publisher-for-mobile.png)

3.  Dans la page **Description du logiciel**, configurez ce qui suit :

    > [!TIP]
    > Selon le type de programme d’installation que vous utilisez, certaines de ces valeurs ont peut-être été entrées automatiquement.

    - **Éditeur**. Entrez le nom de l'éditeur de l'application.
    - **Nom**. Entrez le nom de l'application tel qu'il s'affichera dans le portail d'entreprise.<br>Assurez-vous que tous les noms d'application que vous utilisez sont uniques. Si le même nom d'application existe deux fois, seule l'une des applications sera proposée aux utilisateurs du portail d'entreprise.
    - **Description**. Entrez une description de l'application. Ce libellé s'affichera dans le portail d'entreprise.
    - **URL des informations sur le logiciel**. Il est disponible uniquement si vous avez sélectionné **Programme d’installation du logiciel**. Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL s'affichera dans le portail d'entreprise.
    - **URL de déclaration de confidentialité**. Il est disponible uniquement si vous avez sélectionné **Programme d’installation du logiciel**. Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL s'affichera dans le portail d'entreprise.
    - **Catégorie** (facultatif). Sélectionnez l’une des catégories d’applications intégrées. Cela permettra aux utilisateurs de trouver aisément l'application lorsqu'ils parcourront le portail d'entreprise.
    - **Afficher en tant qu’application proposée et la mettre en exergue sur le portail de l’entreprise**. Afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **Icône** (facultatif). Chargez une icône qui sera associée à l’application. Il s'agit de l'icône qui s'affichera avec l'application lorsque les utilisateurs parcourront le portail d'entreprise.

        Dans cet exemple, vous avez configuré une description pour l’application Microsoft Word pour iOS :

        ![Exemple de description de logiciel](./media/ios-software-description.png)

4.  Dans la page **Configuration requise**, sélectionnez les conditions à remplir avant l’installation de l’application sur un appareil. Par exemple, pour un package d’application pour iOS, vous pouvez sélectionner la version minimale d’E/S requise. En outre, vous pouvez sélectionner le type d’appareil nécessaire, tel qu’un iPhone ou un iPad.

    > [!TIP]
    > La page **Configuration requise** n’est pas affichée pour tous les types d’applications.

5.  D’autres pages de l’Assistant s’affichent quand vous choisissez le type de fichier **Windows Installer**. Ce type de fichier est utilisé quand vous déployez des logiciels vers des PC exécutant Windows 10 ou version ultérieure qui sont inscrits sur Intune.

6.  Dans la page **Résumé**, passez en revue les informations que vous avez spécifiées. Quand vous êtes prêt, sélectionnez **Charger**.

7.  Sélectionnez **Fermer** pour terminer.

L’application s’affiche sur le nœud **Applications** de l’espace de travail **Applications**.

## Exemple - Déploiement d’applications .msi sur des appareils Windows 10
Dans cette vidéo de quatre minutes, vous allez découvrir comment déployer des applications Windows Installer (.msi) sur les appareils inscrits qui exécutent Windows 10.<br><br>

<iframe src="https://channel9.msdn.com/Series/How-to-Control-the-Uncontrolled/6--How-to-Deploy-MSI-Applications-to-Windows-10-Using-Intune-and-Mobile-Device-Management-MDM/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>

## Étapes suivantes

Une fois l’application créée, l’étape suivante consiste à la déployer. Pour en savoir plus, consultez [Déployer des applications avec Microsoft Intune](deploy-apps.md).



<!--HONumber=Oct16_HO4-->


