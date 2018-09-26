---
title: Ajouter manuellement l’application Portail d’entreprise Windows 10
titleSuffix: Microsoft Intune
description: Découvrez comment ajouter manuellement l’application Portail d’entreprise Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109ba2ddeca3af3f1dbb9834e206330f6146b819
ms.sourcegitcommit: 445a54dc6826a549d770a9953549ae2191d391c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45727558"
---
# <a name="manually-add-the-windows-10-company-portal-app-by-using-microsoft-intune"></a>Ajouter manuellement l’application Portail d’entreprise Windows 10 à l’aide de Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Pour gérer des appareils et installer des applications, vos utilisateurs peuvent installer eux-mêmes l’application Portail d’entreprise à partir du Microsoft Store. Toutefois, si votre entreprise l’exige, vous pouvez affecter manuellement à vos utilisateurs l’application Portail d’entreprise Windows 10 directement à partir d’Intune. Cette opération est possible même si vous n’avez pas intégré Intune au Microsoft Store pour Entreprises.

 > [!NOTE]
 > L’option décrite dans cet article vous oblige à affecter des mises à jour manuelles chaque fois qu’une mise à jour d’application est publiée.

## <a name="configure-settings-to-show-offline-apps"></a>Configurer les paramètres permettant d’afficher les applications hors connexion
1. Connectez-vous au [Microsoft Store pour Entreprises](https://www.microsoft.com/business-store) avec votre compte d’administrateur.
2. Sélectionnez l’onglet **Gérer** en haut de la fenêtre.
3. Dans le volet gauche, sélectionnez **Paramètres**.
4. Sous **Expérience d’achat**, définissez **Afficher les applications hors connexion** avec la valeur **Activé**.  
    Les applications sous licence hors connexion sont affichées.

## <a name="download-the-offline-company-portal-app"></a>Télécharger l’application Portail d’entreprise hors connexion
1. Recherchez l’application **Portail d’entreprise** et sélectionnez-la.
2. Définissez le **Type de licence** sur **Hors connexion**.
3. Sélectionnez **Obtenir l’application** pour acquérir l’application Portail d’entreprise hors connexion et l’ajouter à votre inventaire.
4. Dans la page de l’application **Portail d’entreprise**, sélectionnez **Gérer**.
5. Sélectionnez **Tous les appareils Windows 10** comme **Plateforme**, puis sélectionnez les valeurs appropriées pour **Version minimale**, **Architecture** et **Télécharger les métadonnées de l’application**. 
6. Sélectionnez **Télécharger** pour enregistrer le fichier sur votre ordinateur local.

    ![Détails du package à télécharger : « Tous les appareils Windows 10 » et architecture X86](./media/Win10CP-all-devices.png)

7. Sélectionnez **Télécharger** pour télécharger tous les packages sous « Infrastructures requises ».  
    Vous devez effectuer cette opération pour les architectures x86, x64 et ARM, soit un total de 12 packages.
8. Avant de charger l’application Portail d’entreprise dans Intune, créez un dossier (par exemple, C:\Portail Entreprise) en structurant les packages comme ceci :
   - Placez le package Portail d’entreprise dans C:\Portail Entreprise. Créez également un sous-dossier *Dépendances* à cet emplacement.  

     ![Dossier Dépendances enregistré avec le fichier APPXBUN](./media/Win10CP-Dependencies-save.png)

   - Placez les packages de dépendances dans le dossier *Dépendances*. 

     > [!NOTE]
     > Si les dépendances ne sont pas placées au bon format, Intune ne peut pas reconnaître et charger les fichiers pendant le chargement du package, ce qui entraîne l’échec du chargement et l’affichage d’une erreur.

9. Dans Microsoft Intune, dans le portail Azure, chargez l’application Portail d’entreprise comme nouvelle application. 
10. Affectez l’application Portail d’entreprise comme application obligatoire à l’ensemble d’utilisateurs cibles sélectionné.  

Pour plus d’informations sur la façon dont Intune gère les dépendances pour les applications universelles, consultez [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/).  

## <a name="frequently-asked-questions"></a>Forum aux questions 
### <a name="how-do-i-update-the-company-portal-app-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>Comment mettre à jour l’application Portail d’entreprise sur les appareils de mes utilisateurs si ceux-ci ont déjà installé des applications plus anciennes à partir du Store ?
Si vos utilisateurs ont déjà installé les applications Portail d’entreprise Windows 8.1 ou Windows Phone 8.1 à partir du Microsoft Store, ces applications doivent être automatiquement mises à jour vers la nouvelle version sans aucune intervention de votre part ou de la part des utilisateurs. Si la mise à jour ne se produit pas, demandez à vos utilisateurs de confirmer qu’ils ont bien activé les mises à jour automatiques pour les applications du Store sur leurs appareils.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Comment mettre à niveau mon application de portail d’entreprise Windows 8.1 chargée indépendamment vers l’application Portail d’entreprise Windows 10 ?
Nous vous recommandons de supprimer l’affectation de l’application Portail d’entreprise Windows 8.1 en définissant **Désinstaller** comme action d’affectation. Après avoir sélectionné ce paramètre, vous pouvez affecter l’application Portail d’entreprise Windows 10 en utilisant l’une des options décrite précédemment.  

Si vous avez besoin de charger indépendamment l’application et que vous avez affecté le Portail d’entreprise Windows 8.1 sans le signer avec le certificat Symantec, effectuez les étapes de mise à niveau décrites dans les sections précédentes de cet article.

Si vous avez besoin de charger indépendamment l’application et que vous avez signé et affecté l’application Portail d’entreprise Windows 8.1 avec le certificat de signature de code Symantec, effectuez les étapes décrites dans la section suivante.

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>Comment mettre à niveau mon application Portail d’entreprise Windows 8.1 ou Windows Phone 8.1 chargée indépendamment et signée vers l’application Portail d’entreprise Windows 10 ?
La procédure de migration recommandée consiste à supprimer l’affectation existante de l’application Portail d’entreprise Windows Phone 8.1 ou de l’application Portail d’entreprise Windows 8.1 en définissant **Désinstaller** comme action d’affectation. Après avoir sélectionné ce paramètre, vous pouvez affecter l’application Portail d’entreprise Windows 10 normalement.  

Sinon, l’application Portail d’entreprise Windows 10 doit être mise à jour et signée de façon adéquate pour veiller au respect de la procédure de mise à niveau.  

Si vous signez et affectez l’application Portail d’entreprise Windows 10 de cette façon, vous devez répéter ce processus pour chaque nouvelle mise à jour de l’application quand elle est disponible dans le Store. L’application n’est pas automatiquement mise à jour quand le Store est mis à jour.  

Voici comment signer et affecter l’application de cette façon :

1. Téléchargez le [script de signature de l’application Portail d’entreprise Windows 10 Microsoft Intune](https://aka.ms/win10cpscript).  
    Ce script nécessite que le SDK Windows pour Windows 10 soit installé sur l’ordinateur hôte. Téléchargez le [SDK Windows pour Windows 10](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Téléchargez l’application Portail d’entreprise Windows 10 à partir du Microsoft Store pour Entreprises, comme indiqué précédemment.  
3. Pour signer l’application Portail d’entreprise Windows 10, exécutez le script avec les paramètres d’entrée détaillés dans l’en-tête de script, comme indiqué dans le tableau suivant.  
    Les dépendances n’ont pas besoin d’être transmises au script. Elles sont uniquement exigées quand l’application est en cours de chargement dans la console d’administration Intune.

| Paramètre |  Description  |
|---|---|
| InputWin10AppxBundle  |  Chemin au fichier appxbundle source. |
| OutputWin10AppxBundle | Chemin de sortie du fichier appxbundle signé. 
| Win81Appx  | Chemin au fichier Portail d’entreprise Windows 8.1 ou Windows Phone 8.1 (.APPX). |
| PfxFilePath  |  Chemin au fichier de signature de code Symantec Enterprise Mobile (.PFX).  |
| PfxPassword  | Mot de passe du fichier de signature de code Symantec Enterprise Mobile. |
| PublisherId | ID d’éditeur de l’entreprise. S’il est absent, le champ Subject du certificat de signature de code Symantec Enterprise Mobile est utilisé. |
| SdkPath | Chemin du dossier racine du SDK Windows pour Windows 10. Cet argument est facultatif et sa valeur par défaut est ${env:ProgramFiles(x86)}\Windows Kits\10.  |

Une fois l’exécution du script terminée, il produit en sortie la version signée de l’application Portail d’entreprise Windows 10. Vous pouvez ensuite affecter la version signée de l’application en tant qu’application métier par le biais d’Intune, ce qui met à niveau les versions actuellement affectées vers cette nouvelle application.  

## <a name="next-steps"></a>Étapes suivantes

- [Affecter des applications à des groupes](apps-deploy.md)

