---
title: Ajouter et affecter des applications Win32 à Microsoft Intune
titleSuffix: ''
description: Découvrez comment ajouter, affecter et gérer des applications Win32 avec Microsoft Intune. Cette rubrique fournit une vue d’ensemble des fonctionnalités de livraison et de gestion d’application Intune Win32, ainsi que des informations sur le dépannage des applications Win32.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cfe2aef93fb8b7c420ee6513945f11bee5bd0be
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67529709"
---
# <a name="intune-standalone---win32-app-management"></a>Intune autonome - Gestion des applications Win32

[Intune autonome](mdm-authority-set.md) offre à présent de meilleures fonctionnalités de gestion des applications Win32. S’il est possible pour les clients connectés au cloud d’utiliser Configuration Manager pour gérer les applications Win32, les clients Intune uniquement ont de meilleures fonctionnalités de gestion pour leurs applications métier Win32. Cette rubrique fournit une vue d’ensemble de la fonctionnalité de gestion d’application Win32 dans Intune ainsi que des informations de dépannage.

> [!NOTE]
> Cette fonctionnalité de gestion d’application prend en charge les architectures de système d’exploitation 32 bits et 64 bits pour les applications Windows.

## <a name="prerequisites"></a>Prérequis

Pour utiliser la gestion des applications Win32, veillez à respecter les critères suivants :

- Windows 10 version 1607 ou ultérieure (versions Entreprise, Professionnel et Éducation)
- Le client Windows 10 doit avoir les caractéristiques suivantes : 
    - Les appareils doivent être joints à Azure AD et automatiquement inscrits. L’extension de gestion Intune prend en charge les appareils joints à Azure AD, les appareils hybrides joints à un domaine et les appareils inscrits dans une stratégie de groupe. 
    > [!NOTE]
    > Dans le cadre du scénario d’inscription dans une stratégie de groupe, l’utilisateur final utilise le compte d’utilisateur local pour joindre à AAD son appareil Windows 10. Il doit se connecter à l’appareil à l’aide de son compte d’utilisateur AAD et s’inscrire à Intune. Intune installe l’extension de gestion Intune sur l’appareil si un script PowerShell ou une application Win32 cible l’utilisateur ou l’appareil.
- La taille d’application Windows est limitée à 8 Go par application.

## <a name="prepare-the-win32-app-content-for-upload"></a>Préparer le contenu d’application Win32 pour le chargement

Utilisez l’[outil de préparation de contenu Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) pour prétraiter les applications Windows classiques (Win32). L’outil convertit les fichiers d’installation d’application au format *.intunewin*. L’outil détecte aussi certains des attributs nécessaires à Intune pour déterminer l’état d’installation de l’application. Une fois que vous avez utilisé cet outil sur le dossier du programme d’installation de l’application, vous pouvez créer une application Win32 dans la console Intune.

> [!IMPORTANT]
> L’[outil de préparation de contenu Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) compresse tous les fichiers et sous-dossiers lors de la création du fichier *.intunewin*. Veillez à séparer l’outil de préparation de contenu Microsoft Win32 des fichiers et dossiers du programme d’installation, afin de ne pas inclure l’outil ni d’autres fichiers et dossiers inutiles dans votre fichier *.intunewin*.

Vous pouvez télécharger l’[outil de préparation de contenu Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730) à partir de GitHub sous forme de fichier zip. Le fichier compressé contient un dossier nommé **Microsoft-Win32-Content-Prep-Tool-master**. Le dossier contient l’outil de préparation, la licence, un fichier Lisez-moi et les notes de publication. 

### <a name="process-flow-to-create-intunewin-file"></a>Flux du processus de création du fichier .intunewin

   ![Flux du processus de création d’un fichier .intunewin](./media/prepare-win32-app.svg)

### <a name="run-the-microsoft-win32-content-prep-tool"></a>Exécuter l’outil de préparation de contenu Microsoft Win32

Si vous exécutez `IntuneWinAppUtil.exe` à partir de la fenêtre de commandes sans paramètres, l’outil vous guide pour entrer les paramètres obligatoires étape par étape. Vous pouvez aussi ajouter les paramètres à la commande en fonction des paramètres de ligne de commande disponibles suivants.

### <a name="available-command-line-parameters"></a>Paramètres de ligne de commande disponibles 

|    **Paramètre de ligne de commande**    |    **Description**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Aide    |
|    `-c <setup_folder>`     |    Dossier de tous les fichiers d’installation. Tous les fichiers inclus dans ce dossier sont compressés dans le fichier *.intunewin*.    |
|    `-s <setup_file>`     |    Fichier d’installation (comme *setup.exe* ou *setup.msi*).    |
|    `-o <output_folder>`     |    Dossier de sortie du fichier *.intunewin* généré.    |
|    `-q`       |    Mode silencieux    |

### <a name="example-commands"></a>Exemples de commandes

|    **Exemple de commande**    |    **Description**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Cette commande affiche les informations d’utilisation de l’outil.    |
|    `IntuneWinAppUtil -c c:\testapp\v1.0 -s c:\testapp\v1.0\setup.exe -o c:\testappoutput\v1.0 -q`    |    Cette commande génère le fichier `.intunewin` à partir du fichier de configuration et du dossier source spécifiés. Pour le fichier d’installation MSI, cet outil récupère les informations nécessaires pour Intune. Si `-q` est spécifié, la commande s’exécute en mode silencieux et le fichier de sortie est remplacé s’il existe déjà. Si le dossier de sortie n’existe pas, il est créé automatiquement.    |

Quand vous générez un fichier *.intunewin*, placez les fichiers que vous devez référencer dans un sous-dossier du dossier d’installation. Ensuite, utilisez un chemin d’accès relatif pour référencer le fichier spécifique dont vous avez besoin. Par exemple :

**Dossier source d’installation :** *c:\testapp\v1.0*<br>
**Fichier de licence :** *c:\testapp\v1.0\licenses\license.txt*

Faites référence au fichier *license.txt* en utilisant le chemin d’accès relatif *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Créer, affecter et superviser une application Win32

Tout comme une application métier, vous pouvez ajouter une application Win32 à Microsoft Intune. Ce type d’application est généralement écrit en interne ou par un tiers. 

### <a name="process-flow-to-add-a-win32-app-to-intune"></a>Flux de processus pour ajouter une application Win32 à Intune

   ![Flux de processus pour ajouter une application Win32 à Intune](./media/add-win32-app.svg)

### <a name="add-a-win32-app-to-intune"></a>Ajouter une application Win32 à Intune

Les étapes suivantes fournissent des conseils pour ajouter une application Windows à Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Étape 1 : Spécifier le fichier d'installation de logiciel

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications** > **Ajouter**.
4. Dans le volet d’application **Ajouter**, sélectionnez **Application Windows (Win32)** dans la liste déroulante fournie.

    ![Capture d’écran du panneau Ajouter une application - Liste déroulante Ajouter un type](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Étape 2 : Charger le fichier de package d’application

1. Dans le volet **Ajouter une application**, sélectionnez **Fichier de package d’application** pour sélectionner un fichier. Le volet Fichier de package d’application s’affiche.

    ![Capture d’écran du volet Fichier de package d’application](./media/apps-win32-app-02.png)

2. Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Ensuite, sélectionnez un fichier d’installation Windows avec l’extension *.intunewin*.

    > [!IMPORTANT]
    > Veillez à utiliser la dernière version de l’outil de préparation de contenu Microsoft Win32. Si vous n’utilisez pas la version la plus récente, vous obtiendrez un avertissement indiquant que l’application a été empaquetée avec une ancienne version de l’outil de préparation de contenu Microsoft Win32. 

3. Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-3-configure-app-information"></a>Étape 3 : Configurer les informations de l’application

1. Dans le volet **Ajouter une application**, sélectionnez **Informations sur l’application** pour configurer l’application.
2. Dans le volet **Informations sur l’application**, configurez les informations suivantes. Certaines valeurs de ce volet sont éventuellement renseignées automatiquement.
    - **Nom** : Entrez le nom de l’application, tel qu’il apparaît dans le portail d’entreprise. Si le nom d’application existe deux fois, chaque application s’affiche dans le portail d’entreprise.
    - **Description** : Entrez une description de l'application. La description s’affiche dans le portail d’entreprise.
    - **Éditeur** : Entrez le nom de l'éditeur de l'application.
    - **Catégorie** : sélectionnez une ou plusieurs catégories d’application intégrées, ou sélectionnez une catégorie que vous avez créée. Les catégories permettent aux utilisateurs de trouver l’application plus facilement quand ils parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : Afficher l'application en premier sur la page principale du portail d'entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : entrez éventuellement l’URL d’un site web qui contient des informations sur l’application. L’URL s’affiche dans le portail d’entreprise.
    - **URL de déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur l’application. L’URL s’affiche dans le portail d’entreprise.
    - **Développeur** : si vous le souhaitez, entrez le nom du développeur de l’application.
    - **Propriétaire** : si vous le souhaitez, entrez le nom du propriétaire de cette application. Exemple : **Service des ressources humaines**.
    - **Remarques** : entrez les remarques à associer à cette application.
    - **Logo** : chargez une icône associée à l’application. Cette icône s’affiche avec l’application quand les utilisateurs parcourent le portail d’entreprise.
3. Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-4-configure-app-installation-details"></a>Étape 4 : Configurer les détails d’installation de l’application
1. Dans le volet **Ajouter une application**, sélectionnez **Programme** pour configurer les commandes d’installation et de suppression de l’application.
2. Ajoutez la ligne de commande d’installation complète pour installer l’application. 

    Par exemple, si le nom de fichier de votre application est **MyApp123**, ajoutez ce qui suit :<br>
    `msiexec /p “MyApp123.msp”`<p>
    Et, si l’application est `ApplicationName.exe`, la commande correspond au nom de l’application suivi des arguments de commande (commutateurs) pris en charge par le package. <br>Par exemple :<br>
    `ApplicationName.exe /quiet`<br>
    Dans la commande ci-dessus, le package `ApplicationName.exe` prend en charge l’argument de commande `/quiet`.<p> 
    Pour connaître les arguments spécifiques pris en charge par le package d’application, contactez le fournisseur de l’application.

3. Ajoutez la ligne de commande de désinstallation complète pour désinstaller l’application à partir de son GUID. 

    Par exemple : `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Vous pouvez configurer une application Win32 afin qu’elle soit installée dans le contexte **Utilisateur** ou **Système**. Le contexte **Utilisateur** fait référence uniquement à un utilisateur donné. Le contexte **Système** fait référence à tous les utilisateurs d’un appareil Windows 10.
    >
    > Les utilisateurs finaux ne sont pas obligés d’être connectés à l’appareil pour installer des applications Win32.
    > 
    > L’installation et la désinstallation de Win32 sont exécutées exécutée sous le privilège Administrateur (par défaut) lorsque l’application est définie pour être installée dans le contexte de l’utilisateur et que l’utilisateur final de l’appareil a des privilèges Administrateur.

4. Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-5-configure-app-requirements"></a>Étape 5 : Configurer les exigences de l’application

1. Dans le volet **Ajouter une application**, sélectionnez **Exigences** afin de configurer les exigences que les appareils doivent satisfaire pour installer l’application.
2. Dans le volet **Ajouter une règle de spécification**, configurez les informations suivantes. Certaines valeurs de ce volet sont éventuellement renseignées automatiquement.
    - **Architecture du système d'exploitation** : choisissez les architectures nécessaires pour installer l’application.
    - **Système d’exploitation minimal** : sélectionnez le système d’exploitation minimal nécessaire pour installer cette application.
    - **Espace disque nécessaire (Mo)** : vous pouvez ajouter l’espace disque sur le lecteur système nécessaire pour installer l’application.
    - **Mémoire physique nécessaire (Mo)** : vous pouvez ajouter la mémoire physique (RAM) nécessaire pour installer l’application.
    - **Nombre minimal de processeurs logiques nécessaires** : vous pouvez ajouter le nombre minimal de processeurs logiques nécessaires pour installer l’application.
    - **Vitesse minimale du processeur nécessaire (MHz)** : vous pouvez ajouter la vitesse de processeur minimale nécessaire pour installer l’application.

3. Cliquez sur **Ajouter** pour afficher le panneau **Ajouter une règle de spécification** et configurez d’autres règles de spécification. Sélectionnez le **type de spécification** pour choisir le type de règle que vous allez utiliser pour déterminer le mode de validation d’une spécification. Les règles de spécification peuvent se baser sur des informations du système de fichiers, des valeurs de Registre ou des scripts PowerShell. 
    - **Fichier** : Quand vous choisissez **Fichier** en tant que **type de spécification**, la règle de spécification doit détecter un fichier ou dossier, une date, une version ou une taille. 
        - **Chemin** : Chemin complet du dossier contenant le fichier ou dossier à détecter.
        - **Fichier ou dossier** : Fichier ou dossier à détecter.
        - **Propriété** : Sélectionnez le type de règle utilisé pour valider la présence de l’application.
        - **Associé à une application 32 bits sur des clients 64 bits** : Sélectionnez **Oui** pour développer des variables d’environnement de chemin dans le contexte 32 bits sur des clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour développer des variables de chemin dans le contexte 64 bits sur des clients 64 bits. Les clients 32 bits utilisent toujours le contexte 32 bits.
    - **Registre** : Quand vous choisissez **Registre** en tant que **type de spécification**, la règle de spécification doit détecter un paramètre de Registre en fonction d’une valeur, d’une chaîne, d’un entier ou d’une version.
        - **Chemin de clé** : Chemin complet de l’entrée de Registre contenant la valeur à détecter.
        - **Nom de valeur** : Nom de la valeur de Registre à détecter. Si cette valeur est vide, la détection se produit sur la clé. La valeur (par défaut) d’une clé est utilisée comme valeur de détection si la méthode de détection est autre que la vérification de l’existence d’un fichier ou dossier.
        - **Spécification de clé de Registre** : Sélectionnez le type de comparaison de clé de Registre utilisé pour déterminer le mode de validation de la règle de spécification.
        - **Associé à une application 32 bits sur des clients 64 bits** : Sélectionnez **Oui** pour effectuer la recherche dans le Registre 32 bits sur des clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour effectuer la recherche dans le Registre 64 bits sur des clients 64 bits. Les clients 32 bits recherchent toujours dans le Registre 32 bits.
    - **Script** : Choisissez **Script** en tant que **type de spécification**, quand vous ne pouvez pas créer une règle de spécification basée sur un fichier, le Registre ou toute autre méthode disponible dans la console Intune.
        - **Fichier de script** : Pour une règle de spécification basée sur un script PowerShell, si le code de sortie est 0, nous détectons le STDOUT de façon plus détaillée. Par exemple, nous pouvons détecter STDOUT sous forme d’entier qui a la valeur 1.
        - **Exécutez le script comme processus 32 bits sur les clients 64 bits** : sélectionnez **Oui** pour exécuter le script dans un processus 32 bits sur les clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour exécuter le script dans un processus 64 bits sur les clients 64 bits. Les clients 32 bits exécutent le script dans un processus 32 bits.
        - **Exécutez ce script en utilisant les informations d’identification d’ouverture de session** : Sélectionnez **Oui** pour exécuter le script à l’aide des informations d’identification de l’appareil connecté**.
        - **Appliquer la vérification de signature de script** : Sélectionnez **Oui** pour vérifier que le script est signé par un éditeur approuvé, ce qui permet d’exécuter le script sans avertissement ni invite. Le script s’exécute sans blocage. Sélectionnez **Non** (valeur par défaut) pour exécuter le script avec la confirmation de l’utilisateur final sans vérification de signature.
        - **Sélectionner un type de données de sortie** : Sélectionnez le type de données utilisé pour déterminer une correspondance de règle de spécification.
4. Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-6-configure-app-detection-rules"></a>Étape 6 : Configurer des règles de détection d’application

1. Dans le volet **Ajouter une application**, sélectionnez **Règles de détection** pour configurer les règles permettant de détecter la présence de l’application.
2. Dans le champ **Format de règles**, sélectionnez le mode de détection de la présence de l’application. Vous pouvez choisir de configurer manuellement les règles de détection ou d’utiliser un script personnalisé pour détecter la présence de l’application. Vous devez choisir au moins une règle de détection. 

    > [!NOTE]
    > Dans le volet **Règles de détection**, vous pouvez choisir d’ajouter plusieurs règles. Les conditions de **toutes** les règles doivent être remplies pour détecter l’application.

    - **Configurer manuellement les règles de détection** : Vous pouvez sélectionner un des types de règle suivants :
        1. **MSI** : Vérification à partir de la version MSI. Cette option peut être ajoutée une seule fois. Quand vous choisissez ce type de règle, vous avez deux paramètres :
            - **Code de produit MSI** : Ajoutez un code de produit MSI valide pour l’application.
            - **Vérification de la version de produit MSI** : Sélectionnez **Oui** pour vérifier la version de produit MSI en plus du code de produit MSI.
        2. **Fichier** : Effectuez la vérification à partir de la détection de fichier ou dossier, de la date, de la version ou de la taille.
            - **Chemin** : Chemin complet du dossier contenant le fichier ou dossier à détecter.
            - **Fichier ou dossier** : Fichier ou dossier à détecter.
            - **Méthode de détection** : Sélectionnez le type de méthode de détection utilisée pour valider la présence de l’application.
            - **Associé à une application 32 bits sur des clients 64 bits** : Sélectionnez **Oui** pour développer des variables d’environnement de chemin dans le contexte 32 bits sur des clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour développer des variables de chemin dans le contexte 64 bits sur des clients 64 bits. Les clients 32 bits utilisent toujours le contexte 32 bits.
            
            **Exemples de détection à partir d’un fichier**
            1. Vérifiez l’existence du fichier.
         
                ![Capture d’écran du volet de règle de détection - existence du fichier](./media/apps-win32-app-03.png)
        
            2. Vérifiez l’existence du dossier.
         
                ![Capture d’écran du volet de règle de détection - existence du dossier](./media/apps-win32-app-04.png)
        
        3. **Registre** : Effectuez la vérification à partir des éléments suivants : valeur, chaîne, entier ou version.
            - **Chemin de clé** : Chemin complet de l’entrée de Registre contenant la valeur à détecter.
            - **Nom de valeur** : Nom de la valeur de Registre à détecter. Si cette valeur est vide, la détection se produit sur la clé. La valeur (par défaut) d’une clé est utilisée comme valeur de détection si la méthode de détection est autre que la vérification de l’existence d’un fichier ou dossier.
            - **Méthode de détection** : Sélectionnez le type de méthode de détection utilisée pour valider la présence de l’application.
            - **Associé à une application 32 bits sur des clients 64 bits** : Sélectionnez **Oui** pour effectuer la recherche dans le Registre 32 bits sur des clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour effectuer la recherche dans le Registre 64 bits sur des clients 64 bits. Les clients 32 bits recherchent toujours dans le Registre 32 bits.
            
            **Exemples de détection à partir du Registre**
            1. Vérifiez si la clé de Registre existe.
            
                ![Capture d’écran du volet de règle de détection - la clé de Registre existe](./media/apps-win32-app-05.png)    
            
            2. Vérifiez si la valeur de Registre existe.
        
                ![Capture d’écran du volet de règle de détection - la valeur de Registre existe](./media/apps-win32-app-06.png)    
        
            3. Vérifiez les égalités de chaînes de valeur de Registre.
        
                ![Capture d’écran du volet de règle de détection - égalités des chaînes de valeur de Registre](./media/apps-win32-app-07.png)    
     
    - **Utiliser un script de détection personnalisé** : Spécifiez le script PowerShell pour détecter cette application. 
    
        1. **Fichier de script** : Sélectionner un script PowerShell pour détecter la présence de l’application sur le client. L’application est détectée quand le script retourne un code de sortie égal à 0 et écrit une valeur de chaîne dans STDOUT.

        2. **Exécutez le script comme processus 32 bits sur les clients 64 bits** : sélectionnez **Oui** pour exécuter le script dans un processus 32 bits sur les clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour exécuter le script dans un processus 64 bits sur les clients 64 bits. Les clients 32 bits exécutent le script dans un processus 32 bits.

        3. **Appliquer la vérification de signature de script** : Sélectionnez **Oui** pour vérifier que le script est signé par un éditeur approuvé, ce qui permet d’exécuter le script sans avertissement ni invite. Le script s’exécute sans blocage. Sélectionnez **Non** (valeur par défaut) pour exécuter le script avec la confirmation de l’utilisateur final sans vérification de signature.
    
            L’agent Intune vérifie les résultats du script. Il lit les valeurs écrites par le script dans le flux de sortie standard (STDOUT), le flux d’erreurs standard (STDERR) et le code de sortie. Si le script se termine par une valeur non nulle, il échoue et l’état de la détection de l’application est Non installé. Si le code de sortie est égal à zéro et STDOUT contient des données, l’état de la détection d’application est installé. 

            > [!NOTE]
            > Microsoft recommande d’encoder votre script en tant qu’UTF-8. Quand le script se termine par la valeur 0, l’exécution du script est réussie. Le deuxième canal de sortie indique que l’application a été détectée : les données STDOUT indiquent que l’application a été trouvée sur le client. Nous ne recherchons pas de chaîne en particulier dans STDOUT.

        4. Une fois que vous avez ajouté votre ou vos règles, sélectionnez **Ajouter** > **OK**.

### <a name="step-7-configure-app-return-codes"></a>Étape 7 : Configurer des codes de retour d’application

1. Dans le volet **Ajouter une application**, sélectionnez **Codes de retour** pour ajouter les codes de retour permettant de spécifier le comportement de nouvelle tentative d’installation de l’application ou le comportement de postinstallation. Les entrées de code de retour sont ajoutées par défaut à la création de l’application. Toutefois, vous pouvez ajouter des codes de retour supplémentaires ou changer les codes de retour existants. 
2. Dans le volet **Codes de retour**, ajoutez des codes de retour supplémentaires ou modifiez des codes de retour existants.
    - **Échec** : valeur de retour qui indique l’échec de l’installation de l’application.
    - **Redémarrage matériel** : Le code de retour du redémarrage matériel ne permet pas aux applications Win32 suivantes d’être installées sur le client sans redémarrage. 
    - **Redémarrage logiciel** : Le code de retour du redémarrage logiciel permet à la prochaine application Win32 d’être installée sans redémarrage du client. Le redémarrage est nécessaire pour terminer l’installation de l’application actuelle.
    - **Nouvelle tentative** : L’agent de code de retour de nouvelle tentative tente d’installer l’application trois fois. Il attend 5 minutes entre chaque tentative. 
    - **Réussite** : Valeur de retour qui indique que l’application a été installée.
3. Sélectionnez **OK** une fois que vous avez ajouté ou modifié votre liste de codes de retour.

### <a name="step-8-add-the-app"></a>Étape 8 : Ajouter l’application

1. Dans le volet **Ajouter une application**, vérifiez que vous avez correctement configuré les informations de l’application.
2. Sélectionnez **Ajouter** pour charger l’application sur Intune.

### <a name="step-9-assign-the-app"></a>Étape 9 : Affecter l’application

1. Dans le volet d’application, sélectionnez **Affectations**.
2. Sélectionnez **Ajouter un groupe** pour ouvrir le volet **Ajouter un groupe** lié à l’application.
3. Pour l’application spécifique, sélectionnez un **type d’affectation** :
    - **Disponible pour les appareils inscrits** : les utilisateurs effectuent l’installation de l’application à la demande à partir de l’application Portail d'entreprise ou du site web de portail d’entreprise.
    - **Requis** : l’application est installée sur les appareils dans les groupes sélectionnés.
    - **Désinstaller** : l’application est désinstallée des appareils dans les groupes sélectionnés.
4. Sélectionnez **Groupes inclus** et affectez les groupes qui doivent utiliser cette application.
5. Dans le volet **Attribuer**, sélectionnez **OK** pour terminer la sélection des groupes inclus.
6. Cliquez sur **Exclure des groupes** si vous voulez exclure des groupes d’utilisateurs d’un impact par cette attribution d’applications.
7. Dans le volet **Ajouter un groupe**, sélectionnez **OK**.
8. Dans le volet **Affectations** de l’application, sélectionnez **Enregistrer**.

À ce stade, vous avez effectué les étapes permettant d’ajouter une application Win32 à Intune. Pour plus d’informations sur l’affectation et la supervision d’applications, consultez [Affecter des applications à des groupes avec Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) et [Superviser les informations et les affectations d’application avec Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="app-dependencies"></a>Dépendances d’application

Les dépendances d’application sont des applications que vous devez installer avant votre application Win32. Vous pouvez exiger que d’autres applications soient installées en tant que dépendances. Plus précisément, l’appareil doit installer la ou les applications dépendantes avant d’installer l’application Win32. Le nombre maximal de dépendances s’élève à 100. Il inclut les dépendances de toutes les dépendances incluses, ainsi que l’application elle-même. Vous pouvez ajouter des dépendances d’application Win32 uniquement une fois que votre application Win32 a été ajoutée et chargée dans Intune. Une fois que votre application Win32 a été ajoutée, l’option **Dépendances** apparaît dans le panneau de votre application Win32. 

Quand vous ajoutez une dépendance d’application, vous pouvez la rechercher avec le nom de l’application et son éditeur. De plus, vous pouvez trier vos dépendances ajoutées selon le nom de l’application et l’éditeur. Les dépendances d’application précédemment ajoutées ne sont pas sélectionnables dans la liste des dépendances d’application ajoutées. 

Vous pouvez choisir d’installer automatiquement ou non chaque application dépendante. Par défaut, l’option **Installer automatiquement** a la valeur **Oui** pour chaque dépendance. En installant automatiquement une application dépendante, même si l’application dépendante ne cible pas l’utilisateur ou l’appareil, Intune installe l’application sur l’appareil pour satisfaire la dépendance avant d’installer votre application Win32. Il est important de noter qu’une dépendance peut avoir des sous-dépendances récursives et que chaque sous-dépendance est installée avant d’installer la dépendance principale. De plus, l’installation des dépendances ne suit pas un ordre d’installation à un niveau de dépendance donné.

Pour ajouter une dépendance d’application à votre application Win32, utilisez les étapes suivantes :

1. Dans Intune, sélectionnez **Applications clientes** > **Applications** pour voir la liste de vos applications clientes ajoutées. 
2. Sélectionnez une **application Windows (Win32)** ajoutée. 
3. Sélectionnez **Dépendances** pour ajouter la ou les applications dépendantes à installer avant l’application Win32. 
4. Cliquez sur **Ajouter** pour ajouter une dépendance d’application.
5. Une fois que vous avez ajouté la ou les applications dépendantes, cliquez sur **Sélectionner**.
6. Indiquez si vous voulez installer automatiquement l’application dépendante en sélectionnant **Oui** ou **Non** sous **Installer automatiquement**.
7. Cliquez sur **Save**.

L’utilisateur final voit des notifications toast Windows indiquant que les applications dépendantes sont en cours de téléchargement et d’installation dans le cadre du processus d’installation de l’application Win32. De plus, quand une application dépendante n’est pas installée, l’utilisateur final reçoit généralement l’une des notifications suivantes :
- Au moins 1 application dépendante n’a pas pu être installée.
- Les conditions d’au moins 1 application dépendante ne sont pas remplies.
- Au moins 1 application dépendante est en attente du redémarrage de l’appareil.

Si vous choisissez de ne pas **installer automatiquement** une dépendance, l’installation de l’application Win32 n’est pas tentée. De plus, les rapports de l’application indiquent que la dépendance a été marquée comme `failed` et fournissent aussi un motif de l’échec. Vous pouvez consulter l’échec d’installation de la dépendance en cliquant sur un échec (ou avertissement) fourni dans les [détails de l’installation](troubleshoot-app-install.md#win32-app-installation-troubleshooting) de l’application Win32. 

Chaque dépendance adopte la logique de nouvelle tentative de l’application Win32 Intune (3 tentatives d’installation après un délai d’attente de 5 minutes) et la planification de réévaluation globale. En outre, les dépendances sont uniquement applicables au moment de l’installation de l’application Win32 sur l’appareil. Les dépendances ne sont pas applicables pour la désinstallation d’une application Win32. Pour supprimer une dépendance, vous devez cliquer sur les points de suspension situés en fin de ligne à gauche de l’application dépendante dans la liste des dépendances. 

## <a name="delivery-optimization"></a>Optimisation de la distribution

Les clients Windows 10 1709 et versions ultérieures téléchargent du contenu d’applications Win32 Intune à l’aide d’un composant d’optimisation de la distribution sur le client Windows 10. L’optimisation de la distribution fournit la fonctionnalité pair à pair qui est activée par défaut. Elle peut être configurée par la stratégie de groupe et par le biais de la configuration de l’appareil Intune. Pour plus d’informations, voir [Optimisation de la distribution pour Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Installer des applications obligatoires et disponibles sur les appareils

L’utilisateur final voit des notifications toast Windows pour l’installation des applications obligatoires et disponibles. L’image suivante montre un exemple de notification toast où l’installation de l’application n’est pas terminée tant que l’appareil n’est pas redémarré. 

![Capture d’écran de notifications toast Windows pour l’installation d’une application](./media/apps-win32-app-08.png)    

L’image suivante indique à l’utilisateur final que des changements sont effectués sur l’application sur l’appareil.

![Capture d’écran d’une notification faite à l’utilisateur concernant des modifications de l’application](./media/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Notifications toast pour les applications Win32 
Si nécessaire, vous pouvez supprimer l’affichage des notifications toast à l’utilisateur final par affectation d’applications. Dans Intune, sélectionnez **Applications clientes** > **Applications** > sélectionnez l’application > **Affectations** > **Inclure les groupes**. 

> [!NOTE]
> Les applications Win32 installées par l’extension de gestion Intune ne sont pas désinstallées sur les appareils non inscrits. Les administrateurs peuvent exploiter l’exclusion des affectations pour ne pas offrir les applications Win32 aux appareils BYOD.

## <a name="troubleshoot-win32-app-issues"></a>Résoudre les problèmes d’application Win32
Les journaux de l’agent sur l’ordinateur client sont souvent dans `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Vous pouvez utiliser `CMTrace.exe` pour voir ces fichiers journaux. Vous pouvez télécharger *CMTrace.exe* à partir des [Outils du client Configuration Manager](https://docs.microsoft.com/sccm/core/support/tools). 

![Capture d’écran des journaux de l’agent sur l’ordinateur client](./media/apps-win32-app-10.png)    

> [!IMPORTANT]
> Pour permettre une installation et une exécution correctes des applications Win32 métier, les paramètres de logiciel anti-programme malveillant doivent exclure les répertoires suivants de l’analyse :<p>
> **Sur des ordinateurs clients X64** :<br>
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*
>  
> **Sur des ordinateurs clients X86** :<br>
> *C:\Program Files\Microsoft Intune Management Extension\Content*<br>
> *C:\windows\IMECache*

### <a name="detecting-the-win32-app-file-version-using-powershell"></a>Détection de la version du fichier d’application Win32 à l’aide de PowerShell

Si vous rencontrez des difficultés pour détecter la version du fichier d’application Win32, envisagez d’utiliser ou de modifier la commande PowerShell suivante :

``` PowerShell

$FileVersion = [System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion
#The below line trims the spaces before and after the version name
$FileVersion = $FileVersion.Trim();
if ("<file version of successfully detected file>" -eq $FileVersion)
{
#Write the version to STDOUT by default
$FileVersion
exit 0
}
else
{
#Exit with non-zero failure code
exit 1
}

```
Dans la commande PowerShell ci-dessus, remplacez la chaîne `<path to binary file>` par le chemin de votre fichier d’application Win32. Voici un exemple de chemin :<br>
`C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe`

De plus, remplacez la chaîne `<file version of successfully detected file>` par la version du fichier que vous avez besoin de détecter. Voici un exemple de chaîne de version du fichier :<br>
`2019.0150.18118.00 ((SSMS_Rel).190420-0019)`

Si vous avez besoin d’obtenir les informations de version de votre application Win32, vous pouvez utiliser la commande PowerShell suivante :

``` PowerShell

[System.Diagnostics.FileVersionInfo]::GetVersionInfo("<path to binary file>").FileVersion

```

Dans la commande PowerShell ci-dessus, remplacez `<path to binary file>` par le chemin de votre fichier.

### <a name="additional-troubleshooting-areas-to-consider"></a>Autres domaines de résolution des problèmes à prendre en compte
- Vérifiez le ciblage pour être sûr que l’agent est installé sur l’appareil : une application Win32 ciblée sur un groupe ou un script PowerShell ciblé sur un groupe crée une stratégie d’installation d’agent pour le groupe de sécurité.
- Vérifiez la version du système d’exploitation : Windows 10 1607 et versions ultérieures.  
- Vérifiez la référence de Windows 10 : Windows 10 S, ou les versions de Windows s’exécutant avec le mode S activé, ne prend pas en charge l’installation de MSI.

Pour plus d’informations sur la résolution des problèmes liés aux applications Win32, consultez [Résolution des problèmes d’installation des applications Win32](troubleshoot-app-install.md#win32-app-installation-troubleshooting).

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur l’ajout d’applications à Intune, consultez [Ajouter des applications à Microsoft Intune](apps-add.md).
