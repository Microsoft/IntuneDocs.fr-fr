---
title: Inscrire des appareils avec Windows Autopilot
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Windows 10 avec Windows Autopilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: aa51cbea1ab1ea5f1bfc903a17638192aca59326
ms.sourcegitcommit: f69f2663ebdd9c1def68423e8eadf30f86575f7e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49075895"
---
# <a name="enroll-windows-devices-by-using-the-windows-autopilot"></a>Inscrire des appareils Windows avec Windows Autopilot  
Windows Autopilot simplifie l’inscription des appareils. La création et la maintenance des images de système d’exploitation personnalisées demandent beaucoup de temps. L’application de ces images de système d’exploitation personnalisées à de nouveaux appareils en vue de les préparer pour vos utilisateurs finaux peut être tout aussi longue. Avec Microsoft Intune et Autopilot, vous pouvez donner de nouveaux appareils à vos utilisateurs finaux sans devoir créer, gérer et appliquer des images de système d’exploitation personnalisées sur les appareils. Quand vous utilisez Intune pour gérer des appareils Autopilot, vous pouvez gérer des stratégies, des profils, des applications, etc., une fois les appareils inscrits. Pour une vue d’ensemble des avantages, des scénarios et des prérequis, consultez [Vue d’ensemble de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).


## <a name="prerequisites"></a>Prérequis
- [Inscription automatique Windows activée](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Abonnement à Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="add-devices"></a>Ajouter des appareils

Vous pouvez ajouter des appareils Windows Autopilot en important un fichier CSV contenant leurs informations.

1. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > **Importer**.

    ![Capture d’écran d’appareils Windows Autopilot](media/enrollment-autopilot/autopilot-import-device.png)

2. Sous **Ajouter des appareils Windows AutoPilot**, accédez au fichier CSV répertoriant les appareils que vous souhaitez ajouter. Le fichier doit lister les numéros de série, les ID produit Windows, les codes de hachage du matériel, ainsi que les ID de commande facultatifs des appareils.

    ![Capture d’écran de l’ajout d’appareils Windows Autopilot](media/enrollment-autopilot/autopilot-import-device2.png)

3. Choisissez **Importer** pour démarrer l’importation des informations sur les appareils. L’importation peut prendre plusieurs minutes.

4. Une fois l’importation effectuée, choisissez **Inscription de l’appareil** > **Inscription Windows** > **Windows Autopilot** > **Appareils** > **Synchroniser**. Un message indique que la synchronisation est en cours. Le processus peut durer quelques minutes, en fonction du nombre d’appareils à synchroniser.

5. Actualisez la vue pour voir les nouveaux appareils.

## <a name="create-an-autopilot-device-group"></a>Créer un groupe d’appareils Autopilot

1. Dans [Intune dans le Portail Azure](https://aka.ms/intuneportal), choisissez **Groupes** > **Nouveau groupe**.
2. Dans le panneau **Groupe** :
    1. Pour **Type de groupe**, choisissez **Sécurité**.
    2. Renseignez les champs **Nom du groupe** et **Description du groupe**.
    3. Pour **Type d’appartenance**, choisissez **Affecté** ou **Appareil dynamique**.
3. Si vous avez choisi **Affecté** pour **Type d’appartenance** à l’étape précédente, dans le panneau **Groupe**, choisissez **Membres**, puis ajoutez les appareils Autopilot au groupe.
    Les appareils Autopilot qui ne sont pas encore inscrits sont ceux dont le nom correspond au numéro de série de l’appareil.
4. Si vous avez choisi **Appareils dynamiques** pour **Type d’appartenance** ci-dessus, dans le panneau **Groupe**, choisissez **Membres de dispositif dynamique**, puis tapez le code suivant dans la zone **Règle avancée**.
    - Si vous souhaitez créer un groupe qui inclut tous vos appareils Autopilot, tapez `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`
    - Si vous souhaitez créer un groupe qui inclut tous vos appareils Autopilot associés à un ID de commande spécifique, tapez `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881") `
    - Si vous souhaitez créer un groupe qui inclut tous vos appareils Autopilot associés à un ID de bon de commande spécifique, tapez `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Après avoir ajouté le code dans la zone **Règle avancée**, choisissez **Enregistrer**.
5. Choisissez **Créer**.  

## <a name="create-an-autopilot-deployment-profile"></a>Créer un profil de déploiement Autopilot
Les profils de déploiement Autopilot sont utilisés pour configurer les appareils Autopilot.
1. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil**.
2. Tapez un **Nom** et une **Description** facultative.
3. Si vous souhaitez que tous les appareils des groupes affectés soient automatiquement convertis en appareils Autopilot, affectez à **Convertir tous les appareils ciblés en Autopilot** la valeur **Oui**. Tous les appareils non Autopilot des groupes affectés vont s’inscrire auprès du service de déploiement Autopilot. Le traitement de l’enregistrement prend 48 heures. Quand l’appareil est désinscrit et réinitialisé, Autopilot l’inscrit. Une fois qu’un appareil est inscrit de cette manière, la désactivation de cette option ou la suppression de l’affectation de profil n’entraîne pas la suppression de l’appareil du service de déploiement Autopilot. À la place, vous devez [supprimer l’appareil directement](enrollment-autopilot.md#delete-autopilot-devices).
4. Pour **Mode de déploiement**, choisissez l’une de ces deux options :
    - **Géré par l’utilisateur** : les appareils avec ce profil sont associés à l’utilisateur qui inscrit l’appareil. Les informations d’identification de l’utilisateur sont obligatoires pour l’inscription de l’appareil.
    - **Auto-déploiement (préversion)**  : (requiert [le build Windows 10 Insider Preview](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent) Les appareils avec ce profil ne sont pas associés à l’utilisateur qui inscrit l’appareil. Les informations d’identification de l’utilisateur ne sont pas obligatoires pour l’inscription de l’appareil.
5. Dans la zone **Joindre à Azure AD en tant que**, sélectionnez **Joint à Azure AD**.
6. Choisissez **OOBE (Out-Of-Box Experience)**, configurez les options suivantes, puis choisissez **Enregistrer** :
    - **Langue (région)*** : choisissez la langue à utiliser pour l’appareil. Cette option est disponible uniquement si vous avez choisi **Auto-déploiement**  comme **Mode de déploiement**.
    - **Configurer le clavier automatiquement***: si **Langue (région)** est sélectionné, choisissez **Oui** pour ignorer la page de sélection du clavier. Cette option est disponible uniquement si vous avez choisi **Auto-déploiement**  comme **Mode de déploiement**.
    - **Contrat de Licence Utilisateur Final (CLUF)**  : (Windows 10, version 1709 ou ultérieure) choisissez de montrer ou non le CLUF aux utilisateurs.
    - **Paramètres de confidentialité** : choisissez de montrer ou non les paramètres de confidentialité aux utilisateurs.
    - **Masquer les options de changement de compte (Windows Insider uniquement)**  : choisissez **Masquer** pour empêcher l’affichage des options de changement de compte sur les pages de connexion et d’erreur de domaine de l’entreprise. Ces options nécessitent la [configuration de la marque de société dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Type de compte d’utilisateur** : choisissez le type de compte de l’utilisateur (**Administrateur** ou **Standard**).
    - **Appliquer le modèle de nom d’ordinateur (Windows Insider uniquement)**  : choisissez **Oui** pour créer un modèle à utiliser au moment du nommage de l’appareil durant l’inscription. Les noms ne doivent pas dépasser 15 caractères. Ils peuvent comporter des lettres, des chiffres et des traits d’union. Les noms ne peuvent pas être constitués uniquement de chiffres. Utilisez la [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) pour ajouter un numéro de série spécifique au matériel. Sinon, utilisez la [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) pour ajouter une chaîne aléatoire de chiffres, où x représente le nombre de chiffres à ajouter. 

6. Choisissez **Créer** pour créer le profil. Le profil de déploiement Autopilot peut désormais être affecté aux appareils.

* Les options **Langue (région)** et **Configurer le clavier automatiquement** ne sont disponibles que si vous avez choisi **Auto-déploiement (préversion)** comme **Mode de déploiement**  (requiert le build [Windows 10 Insider Preview](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent).


## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>Affecter un profil de déploiement Autopilot à un groupe d’appareils

1. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Profils de déploiement** > Choisir un profil.
2. Dans le panneau du profil, choisissez **Affectations**. 
3. Choisissez **Sélectionner des groupes** puis, dans le panneau **Sélectionner des groupes**, sélectionnez les groupes auxquels vous souhaitez affecter le profil, puis choisissez **Sélectionner**.

## <a name="edit-an-autopilot-deployment-profile"></a>Modifier un profil de déploiement Autopilot
Une fois que vous avez créé un profil de déploiement Autopilot, vous pouvez en modifier certaines parties.   

1. Dans [Intune du portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils**.
2. Sous **Inscription Windows**, dans la section **Windows Autopilot**, choisissez **Profils de déploiement**.
3. Sélectionnez le profil que vous voulez modifier.
4. Cliquez sur **Propriétés** sur la gauche pour changer le nom ou la description du profil de déploiement. Cliquez sur **Enregistrer** après avoir apporté les modifications.
5. Cliquez sur **Paramètres** pour apporter des modifications aux paramètres OOBE. Cliquez sur **Enregistrer** après avoir apporté les modifications.

> [!NOTE]
> Les modifications apportées au profil sont appliquées aux appareils qui ont été affectés à ce profil. Cependant, il n’est pas appliqué aux appareils qui sont déjà inscrits à Intune tant que ceux-ci ne sont pas réinitialisés et réinscrits.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertes relatives aux appareils Windows Autopilot non affectés <!-- 163236 -->  

Les alertes indiquent le nombre d’appareils du programme Autopilot qui n’ont pas de profils de déploiement Autopilot. Utilisez les informations de l’alerte pour créer des profils et les affecter aux appareils non affectés. Quand vous cliquez sur l’alerte, vous voyez s’afficher une liste complète d’appareils Windows Autopilot, ainsi que des informations détaillées les concernant.


Pour afficher les alertes concernant les appareils non affectés, accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription d’appareil** > **Vue d’ensemble** > **Appareils non affectés**.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Affecter un utilisateur à un appareil Autopilot spécifique

Vous pouvez affecter un utilisateur à un appareil Autopilot spécifique. Cette affectation préremplit un utilisateur provenant d’Azure Active Directory dans la page de connexion [avec marque de société](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) lors de la configuration de Windows. Elle vous permet également de définir un nom d’accueil personnalisé. Elle ne préremplit pas ou ne modifie pas les informations de connexion Windows. Seuls les utilisateurs Intune sous licence peuvent être affectés de cette manière.

Conditions préalables : le portail d'entreprise Azure Active Directory a été configuré et vous disposez du [build Windows 10 Insider Preview](https://docs.microsoft.com/windows-insider/at-work-pro/) le plus récent.

1. Dans [Intune dans le portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > choisissez l’appareil > **Affecter un utilisateur**.

    ![Capture d’écran : Affecter un utilisateur](media/enrollment-autopilot/assign-user.png)

2. Choisissez un utilisateur Azure sous licence pour utiliser Intune et choisissez **Sélectionner**.

    ![Capture d’écran : Sélectionner un utilisateur](media/enrollment-autopilot/select-user.png)

3. Dans la zone **Nom convivial de l’utilisateur**, tapez un nom convivial ou acceptez simplement la valeur par défaut. Cette chaîne est le nom convivial qui s’affiche quand l’utilisateur se connecte durant la configuration de Windows.

    ![Capture d’écran : Nom convivial](media/enrollment-autopilot/friendly-name.png)

4. Choisissez **OK**.


## <a name="delete-autopilot-devices"></a>Supprimer des appareils Autopilot

Vous pouvez supprimer les appareils Windows Autopilot qui ne sont pas inscrits.

1. Si les appareils sont inscrits dans Intune, vous devez d’abord [les supprimer dans le portail Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Dans [Intune dans le portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils**.

3. Sous **Appareils Windows Autopilot**, choisissez les appareils à supprimer, puis choisissez **Supprimer**.

4. Confirmez la suppression en choisissant **Oui**. La suppression peut prendre quelques minutes.

## <a name="using-autopilot-in-other-portals"></a>Utilisation d’Autopilot dans d’autres portails
Si la gestion des appareils mobiles ne vous intéresse pas, vous pouvez utiliser Autopilot dans d’autres portails. Bien que l’utilisation d’autres portails soit une option, nous vous recommandons d’utiliser seulement Intune pour gérer vos déploiements Autopilot. Quand vous utilisez Intune et un autre portail, Intune ne peut pas :  

- Afficher les modifications apportées aux profils créés dans Intune, mais modifiés dans un autre portail
- Synchroniser les profils créés dans un autre portail
- Afficher les modifications apportées aux attributions de profils effectuées dans un autre portail
- Synchroniser les attributions de profils effectuées dans un autre portail
- Afficher les modifications apportées à la liste des appareils effectuées dans un autre portail

## <a name="redeploying-windows-autopilot"></a>Redéploiement de Windows Autopilot

Vous pouvez regrouper des appareils Windows par ID de corrélation lors de l’inscription à l’aide d’[Autopilot pour les appareils existants](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) par le biais de Configuration Manager. L’ID de corrélation est un paramètre du fichier de configuration Autopilot. [L’attribut d’appareil Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) est automatiquement défini pour être égal à « OfflineAutopilotprofile-<correlator ID> ». Cela permet de créer des groupes dynamiques Azure AD arbitraires en fonction de l’ID de corrélation à l’aide de l’attribut enrollmentprofileName pour les inscriptions Autopilot hors connexion.

Si vous mettez à niveau des anciennes versions de Windows qui ne prennent pas en charge l’inscription Autopilot, vous pouvez utiliser un profil Autopilot hors connexion. Autopilot peut faciliter une nouvelle installation de Windows 10 version 1809 ou supérieure. Dans le cadre du profil hors connexion, vous pouvez spécifier un ID de corrélation. 

AVERTISSEMENT : Étant donné que l’ID de corrélation n’est pas prélisté dans Intune, les utilisateurs peuvent choisir de s’inscrire sous n’importe quel ID de corrélation de leur choix. Si l’utilisateur crée un ID de corrélation correspondant à un nom de profil DEP Apple ou Autopilot, l’appareil est ajouté à n’importe quel groupe d’appareils Azure AD dynamiques basé sur l’attribut enrollmentProfileName. Pour éviter ce conflit :
- Créez toujours des règles de groupe dynamiques correspondant à la *totalité* de la valeur enrollmentProfileName
- Ne faites jamais commencer les noms de profils DEP Apple ou Autopilot par « OfflineAutopilotprofile- ».

## <a name="next-steps"></a>Étapes suivantes
Une fois que vous avez configuré Windows Autopilot pour les appareils Windows 10 inscrits, découvrez comment les gérer. Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](https://docs.microsoft.com/intune/device-management)
