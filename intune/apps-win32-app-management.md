---
title: Ajouter des applications Win32 à Microsoft Intune
titlesuffix: ''
description: Découvrez comment ajouter, livrer et gérer des applications Win32 avec Microsoft Intune. Cette rubrique fournit une vue d’ensemble des fonctionnalités de livraison et de gestion d’application Intune Win32, ainsi que des informations sur le dépannage des applications Win32.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 11a698628e3ca1342f10f088045012523c8ac745
ms.sourcegitcommit: f114eeba1909c7d4e157003b1a9e2232dd1c99e3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2018
ms.locfileid: "53734287"
---
# <a name="intune-standalone---win32-app-management-public-preview"></a>Intune autonome - Gestion des applications Win32 (préversion publique)

Intune autonome offre de meilleures fonctionnalités de gestion des applications Win32. S’il est possible pour les clients connectés au cloud d’utiliser Configuration Manager pour gérer les applications Win32, les clients Intune uniquement ont de meilleures fonctionnalités de gestion pour leurs applications métier Win32. Cette rubrique fournit une vue d’ensemble de la fonctionnalité de gestion d’application Win32 dans Intune ainsi que des informations de dépannage.

## <a name="prerequisites-for-public-preview"></a>Prérequis de la préversion publique

- Windows 10 version 1607 ou ultérieure (versions Entreprise, Professionnel et Éducation)
- Le client Windows 10 doit avoir les caractéristiques suivantes : 
    - Joint à Azure Active Directory (AAD) ou de manière hybride à Azure Active Directory et
    - Inscrit dans Intune (géré par MDM)
- La taille d’application Windows est limitée à 8 Go par application dans la préversion publique 

## <a name="prepare-the-win32-app-content-for-upload"></a>Préparer le contenu d’application Win32 pour le chargement

Utilisez [l’outil de préparation de chargement des applications Win32 de Microsoft Intune](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool) pour prétraiter les applications Win32. L’outil de packaging convertit les fichiers d’installation de l’application au format *.intunewin*. L’outil de packaging détecte également certains des attributs demandés par Intune pour déterminer l’état d’installation de l’application. Une fois que vous avez utilisé cet outil sur le dossier du programme d’installation de l’application, vous pouvez créer une application Win32 dans la console Intune.

Vous pouvez télécharger [l’outil de préparation de chargement des applications Win32 de Microsoft Intune](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool) à partir de GitHub.

### <a name="available-command-line-parameters"></a>Paramètres de ligne de commande disponibles 

|    **Paramètre de ligne de commande**    |    **Description**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Aide    |
|    `-c <setup_folder>`     |    Dossier d’installation de tous les fichiers d’installation.    |
|   ` -s <setup_file>`     |    Fichier d’installation (comme *setup.exe* ou *setup.msi*).    |
|    `-o <output_folder>`     |    Dossier de sortie du fichier *.intunewin* généré.    |
|    `-q`       |    Mode silencieux    |

### <a name="example-commands"></a>Exemples de commandes

|    **Exemple de commande**    |    **Description**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Cette commande affiche les informations d’utilisation de l’outil.    |
|    `IntuneWinAppUtil -c <setup_folder> -s <source_setup_file> -o <output_folder> <-q>`    |    Cette commande génère le fichier `.intunewin` à partir du fichier de configuration et du dossier source spécifiés. Pour le fichier d’installation MSI, cet outil récupère les informations nécessaires pour Intune. Si `-q` est spécifié, la commande s’exécute en mode silencieux et le fichier de sortie est remplacé s’il existe déjà. Si le dossier de sortie n’existe pas, il est créé automatiquement.    |

Lorsque vous générez un fichier *.intunewin*, placez les fichiers que vous devez référencer dans un sous-dossier du dossier d’installation. Ensuite, utilisez un chemin d’accès relatif pour référencer le fichier spécifique dont vous avez besoin. Par exemple :

**Dossier source d’installation :** *c:\testapp\v1.0*<br>
**Fichier de licence :** *c:\testapp\v1.0\licenses\license.txt*

Faites référence au fichier *license.txt* en utilisant le chemin d’accès relatif *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Créer, affecter et superviser une application Win32

Tout comme une application métier, vous pouvez ajouter une application Win32 à Microsoft Intune. Ce type d’application est généralement écrit en interne ou par un tiers. Les étapes suivantes fournissent des conseils pour ajouter une application Windows à Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Étape 1 : Spécifier le fichier d'installation de logiciel

1.  Connectez-vous au [portail Azure](https://portal.azure.com/).
2.  Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3.  Dans le volet **Intune**, sélectionnez **Applications clientes** > **Applications** > **Ajouter**.
4.  Dans le volet d’application **Ajouter**, sélectionnez **Application Windows (Win32) - préversion** dans la liste déroulante fournie.

    ![Capture d’écran du panneau Ajouter une application - Liste déroulante Ajouter un type](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Étape 2 : Charger le fichier de package d’application

1.  Dans le volet **Ajouter une application**, sélectionnez **Fichier de package d’application** pour sélectionner un fichier. Le volet Fichier de package d’application s’affiche.

    ![Capture d’écran du volet Fichier de package d’application](./media/apps-win32-app-02.png)

2.  Dans le volet **Fichier de package d’application**, sélectionnez le bouton Parcourir. Ensuite, sélectionnez un fichier d’installation Windows avec l’extension *.intunewin*.
3.  Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-3-configure-app-information"></a>Étape 3 : Configurer les informations de l’application

1.  Dans le volet **Ajouter une application**, sélectionnez **Informations sur l’application** pour configurer l’application.
2.  Dans le volet **Informations sur l’application**, configurez les informations suivantes. Certaines valeurs de ce volet sont éventuellement renseignées automatiquement.
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
3.  Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-4-configure-app-installation-details"></a>Étape 4 : Configurer les détails d’installation de l’application
1.  Dans le volet **Ajouter une application**, sélectionnez **Programme** pour configurer les commandes d’installation et de suppression de l’application.
2.  Ajoutez la ligne de commande d’installation complète pour installer l’application. 

    Par exemple, si le nom de fichier de votre application est **MyApp123**, ajoutez ce qui suit : `msiexec /i “MyApp123.msi”`

3.  Ajoutez la ligne de commande de désinstallation complète pour désinstaller l’application à partir de son GUID. 

    Par exemple : `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Vous pouvez configurer une application Win32 afin qu’elle soit installée dans le contexte **Utilisateur** ou **Système**. Le contexte **Utilisateur** fait référence uniquement à un utilisateur donné. Le contexte **Système** fait référence à tous les utilisateurs d’un appareil Windows 10.
    >
    > Les utilisateurs finaux ne sont pas obligés d’être connectés à l’appareil pour installer des applications Win32.

4.  Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-5-configure-app-requirements"></a>Étape 5 : Configurer les exigences de l’application

1.  Dans le volet **Ajouter une application**, sélectionnez **Exigences** afin de configurer les exigences que les appareils doivent satisfaire pour installer l’application.
2.  Dans le volet **Exigences**, configurez les informations suivantes. Certaines valeurs de ce volet sont éventuellement renseignées automatiquement.
    - **Architecture du système d'exploitation** : choisissez les architectures nécessaires pour installer l’application.
    - **Système d’exploitation minimal** : sélectionnez le système d’exploitation minimal nécessaire pour installer cette application.
    - **Espace disque nécessaire (Mo)** : vous pouvez ajouter l’espace disque sur le lecteur système nécessaire pour installer l’application.
    - **Mémoire physique nécessaire (Mo)** : vous pouvez ajouter la mémoire physique (RAM) nécessaire pour installer l’application.
    - **Nombre minimal de processeurs logiques nécessaires** : vous pouvez ajouter le nombre minimal de processeurs logiques nécessaires pour installer l’application.
    - **Vitesse minimale du processeur nécessaire (MHz)** : vous pouvez ajouter la vitesse de processeur minimale nécessaire pour installer l’application.
3.  Une fois que vous avez fini, sélectionnez **OK**.

### <a name="step-6-configure-app-detection-rules"></a>Étape 6 : Configurer des règles de détection d’application

1.  Dans le volet **Ajouter une application**, sélectionnez **Règles de détection** pour configurer les règles permettant de détecter la présence de l’application.
2.  Dans le champ **Format de règles**, sélectionnez le mode de détection de la présence de l’application. Vous pouvez choisir de configurer manuellement les règles de détection ou d’utiliser un script personnalisé pour détecter la présence de l’application. Vous devez choisir au moins une règle de détection. 

    > [!NOTE]
    > Dans le volet **Règles de détection**, vous pouvez choisir d’ajouter plusieurs règles. Les conditions de **toutes** les règles doivent être remplies pour détecter l’application.

    - **Configurer manuellement les règles de détection** : Vous pouvez sélectionner un des types de règle suivants :
        1.  **MSI** : Vérification à partir de la version MSI. Cette option peut être ajoutée une seule fois. Quand vous choisissez ce type de règle, vous avez deux paramètres :
            - **Code de produit MSI** : Ajoutez un code de produit MSI valide pour l’application.
            - **Vérification de la version de produit MSI** : Sélectionnez **Oui** pour vérifier la version de produit MSI en plus du code de produit MSI.
        2.  **Fichier** : Effectuez la vérification à partir de la détection de fichier ou dossier, de la date, de la version ou de la taille.
            - **Chemin** : Chemin complet du dossier contenant le fichier ou dossier à détecter.
            - **Fichier ou dossier** : Fichier ou dossier à détecter.
            - **Méthode de détection** : Sélectionnez le type de méthode de détection utilisée pour valider la présence de l’application.
            - **Associé à une application 32 bits sur des clients 64 bits** : Sélectionnez **Oui** pour développer des variables d’environnement de chemin dans le contexte 32 bits sur des clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour développer des variables de chemin dans le contexte 64 bits sur des clients 64 bits. Les clients 32 bits utilisent toujours le contexte 32 bits.
            
            **Exemples de détection à partir d’un fichier**
            1.  Vérifiez l’existence du fichier.
         
                ![Capture d’écran du volet de règle de détection - existence du fichier](./media/apps-win32-app-03.png)
        
            2.  Vérifiez l’existence du dossier.
         
                ![Capture d’écran du volet de règle de détection - existence du dossier](./media/apps-win32-app-04.png)
        
        3. **Registre** : Effectuez la vérification à partir des éléments suivants : valeur, chaîne, entier ou version.
            - **Chemin de clé** : Chemin complet de l’entrée de Registre contenant la valeur à détecter.
            - **Nom de valeur** : Nom de la valeur de Registre à détecter. Si cette valeur est vide, la détection se produit sur la clé. La valeur (par défaut) d’une clé est utilisée comme valeur de détection si la méthode de détection est autre que la vérification de l’existence d’un fichier ou dossier.
            - **Méthode de détection** : Sélectionnez le type de méthode de détection utilisée pour valider la présence de l’application.
            - **Associé à une application 32 bits sur des clients 64 bits** : Sélectionnez **Oui** pour effectuer la recherche dans le Registre 32 bits sur des clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour effectuer la recherche dans le Registre 64 bits sur des clients 64 bits. Les clients 32 bits recherchent toujours dans le Registre 32 bits.
            
            **Exemples de détection à partir du Registre**
            1.  Vérifiez si la clé de Registre existe.
            
                ![Capture d’écran du volet de règle de détection - la clé de Registre existe](./media/apps-win32-app-05.png)    
            
            2.  Vérifiez que la valeur de Registre existe (**non disponible dans la préversion**).
        
                ![Capture d’écran du volet de règle de détection - la valeur de Registre existe](./media/apps-win32-app-06.png)    
        
            3.  Vérifiez les égalités de chaînes de valeur de Registre.
        
                ![Capture d’écran du volet de règle de détection - égalités des chaînes de valeur de Registre](./media/apps-win32-app-07.png)    
     
    - **Utiliser un script de détection personnalisé** : Spécifiez le script PowerShell pour détecter cette application. 
    
        1.  **Fichier de script** : Sélectionner un script PowerShell pour détecter la présence de l’application sur le client. L’application est détectée quand le script retourne un code de sortie égal à 0 et écrit une valeur de chaîne dans STDOUT.

        2.  **Exécutez le script comme processus 32 bits sur les clients 64 bits** : sélectionnez **Oui** pour exécuter le script dans un processus 32 bits sur les clients 64 bits. Sélectionnez **Non** (valeur par défaut) pour exécuter le script dans un processus 64 bits sur les clients 64 bits. Les clients 32 bits exécutent le script dans un processus 32 bits.

        3.  **Appliquer la vérification de signature de script** : Sélectionnez **Oui** pour vérifier que le script est signé par un éditeur approuvé, ce qui permet d’exécuter le script sans avertissement ni invite. Le script s’exécute sans blocage. Sélectionnez **Non** (valeur par défaut) pour exécuter le script avec la confirmation de l’utilisateur final sans vérification de signature.
    
            L’agent Intune vérifie les résultats du script. Il lit les valeurs écrites par le script dans le flux de sortie standard (STDOUT), le flux d’erreurs standard (STDERR) et le code de sortie. Si le script se termine par une valeur non nulle, il échoue et l’état de la détection de l’application est Non installé. Si le code de sortie est égal à zéro et STDOUT contient des données, l’état de la détection d’application est installé. 

            > [!NOTE]
            > Quand le script se termine par la valeur 0, l’exécution du script est réussie. Le deuxième canal de sortie indique que l’application a été détectée : les données STDOUT indiquent que l’application a été trouvée sur le client. Nous ne recherchons pas de chaîne en particulier dans STDOUT.

        4.  Une fois que vous avez ajouté votre ou vos règles, sélectionnez **Ajouter** > **OK**.

### <a name="step-7-configure-app-return-codes"></a>Étape 7 : Configurer des codes de retour d’application

1.  Dans le volet **Ajouter une application**, sélectionnez **Codes de retour** pour ajouter les codes de retour permettant de spécifier le comportement de nouvelle tentative d’installation de l’application ou le comportement de postinstallation. Les entrées de code de retour sont ajoutées par défaut à la création de l’application. Toutefois, vous pouvez ajouter des codes de retour supplémentaires ou changer les codes de retour existants. 
2.  Dans le volet **Codes de retour**, ajoutez des codes de retour supplémentaires ou modifiez des codes de retour existants.
    - **Échec** : valeur de retour qui indique l’échec de l’installation de l’application.
    - **Redémarrage matériel** : Le code de retour du redémarrage matériel ne permet pas aux applications Win32 suivantes d’être installées sur le client sans redémarrage. 
    - **Redémarrage logiciel** : Le code de retour du redémarrage logiciel permet à la prochaine application Win32 d’être installée sans redémarrage du client. Le redémarrage est nécessaire pour terminer l’installation de l’application actuelle.
    - **Nouvelle tentative** : L’agent de code de retour de nouvelle tentative tente d’installer l’application trois fois. Il attend 5 minutes entre chaque tentative. 
    - **Réussite** : Valeur de retour qui indique que l’application a été installée.
3.  Sélectionnez **OK** une fois que vous avez ajouté ou modifié votre liste de codes de retour.

### <a name="step-8-add-the-app"></a>Étape 8 : Ajouter l’application

1.  Dans le volet **Ajouter une application**, vérifiez que vous avez correctement configuré les informations de l’application.
2.  Sélectionnez **Ajouter** pour charger l’application sur Intune.

### <a name="step-9-assign-the-app"></a>Étape 9 : Affecter l’application

1.  Dans le volet d’application, sélectionnez **Affectations**.
2.  Sélectionnez **Ajouter un groupe** pour ouvrir le volet **Ajouter un groupe** lié à l’application.
3.  Pour l’application spécifique, sélectionnez un **type d’affectation** :
    - **Disponible pour les appareils inscrits** : les utilisateurs effectuent l’installation de l’application à la demande à partir de l’application Portail d'entreprise ou du site web de portail d’entreprise.
    - **Requis** : l’application est installée sur les appareils dans les groupes sélectionnés.
    - **Désinstaller** : l’application est désinstallée des appareils dans les groupes sélectionnés.
4.  Sélectionnez **Groupes inclus** et affectez les groupes qui doivent utiliser cette application.
5.  Dans le volet **Attribuer**, sélectionnez **OK** pour terminer la sélection des groupes inclus.
6.  Cliquez sur **Exclure des groupes** si vous voulez exclure des groupes d’utilisateurs d’un impact par cette attribution d’applications.
7.  Dans le volet **Ajouter un groupe**, sélectionnez **OK**.
8.  Dans le volet **Affectations** de l’application, sélectionnez **Enregistrer**.

À ce stade, vous avez effectué les étapes permettant d’ajouter une application Win32 à Intune. Pour plus d’informations sur l’affectation et la supervision d’applications, consultez [Affecter des applications à des groupes avec Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) et [Superviser les informations et les affectations d’application avec Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="delivery-optimization"></a>Optimisation de la distribution

Les clients Windows 10 RS3 et versions ultérieures téléchargent du contenu d’application Intune Win32 à l’aide d’un composant de l’optimisation de distribution sur le client Windows 10. L’optimisation de la distribution fournit la fonctionnalité pair à pair qui est activée par défaut. L’optimisation de la distribution peut être configurée par la stratégie de groupe et à l’avenir via Intune MDM. Pour plus d’informations, consultez [Optimisation de la distribution pour Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Installer des applications obligatoires et disponibles sur les appareils

L’utilisateur final voit des notifications toast Windows pour l’installation des applications obligatoires et disponibles. L’image suivante montre un exemple de notification toast où l’installation de l’application n’est pas terminée tant que l’appareil n’est pas redémarré. 

![Capture d’écran de notifications toast Windows pour l’installation d’une application](./media/apps-win32-app-08.png)    

L’image suivante indique à l’utilisateur final que des changements sont effectués sur l’application sur l’appareil.

![Capture d’écran d’une notification faite à l’utilisateur concernant des modifications de l’application](./media/apps-win32-app-09.png)    

## <a name="troubleshoot-win32-app-issues"></a>Résoudre les problèmes d’application Win32
Les journaux de l’agent sur l’ordinateur client sont souvent dans `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Vous pouvez utiliser `CMTrace.exe` pour voir ces fichiers journaux. Vous pouvez télécharger *CMTrace.exe* à partir des [Outils du client SCCM](https://docs.microsoft.com/sccm/core/support/tools). 

![Capture d’écran des journaux de l’agent sur l’ordinateur client](./media/apps-win32-app-10.png)    

### <a name="troubleshooting-areas-to-consider"></a>Zones de résolution de problèmes à prendre en compte
- Vérifiez le ciblage pour être sûr que l’agent est installé sur l’appareil : une application Win32 ciblée sur un groupe ou un script PowerShell ciblé sur un groupe crée une stratégie d’installation d’agent pour le groupe de sécurité.
- Vérifiez la version du système d’exploitation : Windows 10 1607 et versions ultérieures.  
- Vérifiez la référence de Windows 10 : Windows 10 S, ou les versions de Windows s’exécutant avec le mode S activé, ne prend pas en charge l’installation de MSI.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur l’ajout d’applications à Intune, consultez [Ajouter des applications à Microsoft Intune](apps-add.md).
