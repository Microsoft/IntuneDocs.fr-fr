---
title: Inscrire des appareils avec Windows Autopilot
titleSuffix: Microsoft Intune
description: Découvrez comment inscrire des appareils Windows 10 avec Windows Autopilot.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 92aa955558120f88afb31e787376fdd1281dd5f4
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723175"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Inscrire des appareils Windows dans Intune avec Windows Autopilot  
Windows Autopilot simplifie l’inscription des appareils dans Intune. La création et la maintenance des images de système d’exploitation personnalisées demandent beaucoup de temps. L’application de ces images de système d’exploitation personnalisées à de nouveaux appareils en vue de les préparer pour vos utilisateurs finaux peut être tout aussi longue. Avec Microsoft Intune et Autopilot, vous pouvez donner de nouveaux appareils à vos utilisateurs finaux sans devoir créer, gérer et appliquer des images de système d’exploitation personnalisées sur les appareils. Quand vous utilisez Intune pour gérer des appareils Autopilot, vous pouvez gérer des stratégies, des profils, des applications, etc., une fois les appareils inscrits. Pour une vue d’ensemble des avantages, des scénarios et des prérequis, consultez [Vue d’ensemble de Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot).

Il existe quatre types de déploiement Autopilot :
- [Mode de déploiement automatique](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) pour les kiosques, la signalisation numérique ou un appareil partagé
- [White Glove](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove) permet aux partenaires ou au personnel informatique de préprovisionner un PC Windows 10 pour qu’il soit entièrement configuré et prêt à l’emploi ; [Autopilot pour les appareils existants](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) vous permet de déployer facilement la dernière version de Windows 10 sur vos appareils existants
- [Mode piloté par l’utilisateur](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) pour les utilisateurs traditionnels 


## <a name="prerequisites"></a>Prérequis
- [Abonnement Intune](../fundamentals/licenses.md)
- [Inscription automatique Windows activée](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Abonnement à Azure Active Directory Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Comment obtenir le fichier CSV pour l’importation dans Intune

Pour plus d’informations, consultez la compréhension du cmdlet PowerShell.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>Ajouter des appareils

Vous pouvez ajouter des appareils Windows Autopilot en important un fichier CSV contenant leurs informations.

1. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > **Importer**.

    ![Capture d’écran d’appareils Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device.png)

2. Sous **Ajouter des appareils Windows AutoPilot**, accédez au fichier CSV répertoriant les appareils que vous souhaitez ajouter. Le fichier CSV doit lister les numéros de série, les ID de produit Windows, les hachages matériels, les étiquettes de groupe facultatives et l’utilisateur attribué facultatif. Vous pouvez avoir jusqu’à 500 lignes dans la liste. Utilisez le format d’en-tête et de ligne ci-dessous :

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Capture d’écran de l’ajout d’appareils Windows Autopilot](./media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > Lorsque vous utilisez le chargement CSV pour attribuer un utilisateur, assurez-vous que vous attribuez un nom d’utilisateur principal (UPN) valide. Si vous attribuez un UPN non valide (nom d’utilisateur incorrect), votre appareil peut être inaccessible jusqu’à ce que vous supprimiez l’attribution non valide. Pendant le chargement CSV, la seule validation que nous effectuons sur la colonne **Utilisateur attribué** est de vérifier que le nom de domaine est valide. Nous ne pouvons pas effectuer de validation UPN individuelle pour vous assurer que vous attribuez un utilisateur existant ou correct.

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
4. Si vous avez choisi **Appareils dynamiques** pour **Type d’appartenance** ci-dessus, dans le panneau **Groupe**, choisissez **Membres de dispositif dynamique**, puis tapez le code suivant dans la zone **Règle avancée**. Seuls les appareils AutoPilot sont rassemblés par ces règles, car elles ciblent des attributs qui n’appartiennent qu’à des appareils AutoPilot.
    - Si vous souhaitez créer un groupe comprenant tous vos appareils Autopilot, tapez `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`.
    - Le champ de balises de groupe d’Intune est mis en correspondance avec l’attribut OrderID sur les appareils Azure AD. Si vous voulez créer un groupe incluant tous vos appareils Autopilot ayant une étiquette de groupe spécifique (OrderID d’appareil Azure AD), vous devez saisir ceci : `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`
    - Si vous souhaitez créer un groupe qui inclut tous vos appareils Autopilot associés à un ID de bon de commande spécifique, tapez `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`
    
    Après avoir ajouté le code dans la zone **Règle avancée**, choisissez **Enregistrer**.
5. Choisissez **Créer**.  

## <a name="create-an-autopilot-deployment-profile"></a>Créer un profil de déploiement Autopilot
Les profils de déploiement Autopilot sont utilisés pour configurer les appareils Autopilot.
1. Accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription des appareils** > **Inscription Windows** > **Profils de déploiement** > **Créer un profil**.
2. Sur la page **Informations de base**, tapez un **Nom** et une **Description** facultative.

    ![Capture d’écran de la page Informations de base](./media/enrollment-autopilot/create-profile-basics.png)

3. Si vous souhaitez que tous les appareils des groupes affectés soient automatiquement convertis en appareils Autopilot, affectez à **Convertir tous les appareils ciblés en Autopilot** la valeur **Oui**. Tous les appareils appartenant à l’entreprise et non Autopilot des groupes affectés vont s’inscrire auprès du service de déploiement Autopilot. Les appareils personnels ne seront pas convertis en appareils Autopilot. Le traitement de l’enregistrement prend 48 heures. Quand l’appareil est désinscrit et réinitialisé, Autopilot l’inscrit. Une fois qu’un appareil est inscrit de cette manière, la désactivation de cette option ou la suppression de l’affectation de profil n’entraîne pas la suppression de l’appareil du service de déploiement Autopilot. À la place, vous devez [supprimer l’appareil directement](enrollment-autopilot.md#delete-autopilot-devices).
4. Sélectionnez **Suivant**.
5. Sur la page **Out-of-box experience (OOBE)** , choisissez entre ces deux options pour **Mode de déploiement** :
    - **Géré par l’utilisateur** : Les appareils avec ce profil sont associés à l’utilisateur qui inscrit l’appareil. Les informations d’identification de l’utilisateur sont obligatoires pour l’inscription de l’appareil.
    - **Auto-déploiement (préversion)**  : (nécessite Windows 10, version 1809 ou ultérieure) les appareils avec ce profil ne sont pas associés à l’utilisateur qui inscrit l’appareil. Les informations d’identification de l’utilisateur ne sont pas obligatoires pour l’inscription de l’appareil. Quand aucun utilisateur n’est associé à un appareil, les stratégies de conformité basées sur l’utilisateur ne s’appliquent pas à ce dernier. Lorsque vous utilisez le mode de déploiement automatique, seules les stratégies de conformité ciblant l’appareil sont appliquées.

    ![Capture d’écran de la page OOBE](./media/enrollment-autopilot/create-profile-outofbox.png)

6. Dans la zone **Joindre à Azure AD en tant que**, sélectionnez **Joint à Azure AD**.
7. Configurez les options suivantes :
    - **Contrat de Licence Utilisateur Final (CLUF)**  : (Windows 10, version 1709 ou ultérieure) choisissez de montrer ou non le CLUF aux utilisateurs.
    - **Paramètres de confidentialité** : choisissez de montrer ou non les paramètres de confidentialité aux utilisateurs.
    >[!IMPORTANT]
    >La valeur par défaut du paramètre Données de diagnostic varie selon la version de Windows. Pour les appareils exécutant Windows 10 version 1903, la valeur par défaut est définie sur Complet au cours de l’expérience OOBE (Out-Of-Box Experience). Pour plus d’informations, consultez [Données de diagnostic Windows](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data) <br>
    
    - **Masquer les options de changement de compte (nécessite Windows 10, version 1809 ou ultérieure)**  : choisissez **Masquer** pour empêcher l’affichage des options de changement de compte sur les pages de connexion et d’erreur de domaine de l’entreprise. Ces options nécessitent la [configuration de la marque de société dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding).
    - **Type de compte d’utilisateur** : choisissez le type de compte de l’utilisateur (**Administrateur** ou **Standard**). Nous autorisons l'utilisateur qui joint l'appareil à être un administrateur local en l’ajoutant au groupe Admin local. Nous n'autorisons pas l'utilisateur à être l’administrateur par défaut de l'appareil.
    - **Autoriser White Glove OOBE** (requiert Windows 10, version 1903 ou ultérieure ; [exigences physiques supplémentaires](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)) : choisissez **Oui** pour autoriser l’assistance.
    - **Appliquer le modèle de nom d’appareil (nécessite Windows 10, version 1809 ou ultérieure)**  : choisissez **Oui** pour créer un modèle à utiliser au moment du nommage de l’appareil durant l’inscription. Les noms ne doivent pas dépasser 15 caractères. Ils peuvent comporter des lettres, des chiffres et des traits d’union. Les noms ne peuvent pas être constitués uniquement de chiffres. Utilisez la [macro %SERIAL%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) pour ajouter un numéro de série spécifique au matériel. Sinon, utilisez la [macro %RAND:x%](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) pour ajouter une chaîne aléatoire de chiffres, où x représente le nombre de chiffres à ajouter. 
    - **Langue (région)** \* : choisissez la langue à utiliser pour l’appareil. Cette option est disponible uniquement si vous avez choisi **Auto-déploiement**  comme **Mode de déploiement**.
    - **Configurer automatiquement le clavier**\* : si une **Langue (région)** est sélectionnée, choisissez **Oui** pour ignorer la page de sélection du clavier. Cette option est disponible uniquement si vous avez choisi **Auto-déploiement**  comme **Mode de déploiement**.
8. Sélectionnez **Suivant**.
9. Sur la page **Balises d’étendue**, ajoutez les balises d’étendue que vous souhaitez appliquer à ce profil (facultatif). Pour plus d’informations sur les balises d’étendue, voir [Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée](../fundamentals/scope-tags.md).
10. Sélectionnez **Suivant**.
11. Sur la page **Affectations**, choisissez **Groupes sélectionnés** pour **Affecter à**.

    ![Capture d’écran de la page Affectations](./media/enrollment-autopilot/create-profile-assignments.png)

12. Choisissez **Sélectionner les groupes à inclure**, puis les groupes que vous souhaitez inclure dans ce profil.
13. Si vous souhaitez exclure des groupes, choisissez **sélectionner les groupes à exclure**, puis les groupes que vous souhaitez exclure.
14. Sélectionnez **Suivant**.
15. Sur la page **Vérifier + créer**, choisissez **Créer** pour créer le profil.

    ![Capture d’écran de la page Vérifier](./media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune recherche régulièrement de nouveaux appareils dans les groupes affectés, puis commence le processus d’affectation de profils à ces appareils. Ce processus peut prendre plusieurs minutes. Avant de déployer un appareil, vérifiez que ce processus est terminé.  Pour ce faire, accédez à **Inscription de l’appareil** > **Inscription Windows** > **Appareils** où vous devez voir l’état du profil passer de « Non affecté » à « Affectation » et enfin à « Affecté ».

## <a name="edit-an-autopilot-deployment-profile"></a>Modifier un profil de déploiement Autopilot
Une fois que vous avez créé un profil de déploiement Autopilot, vous pouvez en modifier certaines parties.   

1. Dans [Intune du portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils**.
2. Sous **Inscription Windows**, dans la section **Windows Autopilot**, choisissez **Profils de déploiement**.
3. Sélectionnez le profil que vous voulez modifier.
4. Cliquez sur **Propriétés** sur la gauche pour changer le nom ou la description du profil de déploiement. Cliquez sur **Enregistrer** après avoir apporté les modifications.
5. Cliquez sur **Paramètres** pour apporter des modifications aux paramètres OOBE. Cliquez sur **Enregistrer** après avoir apporté les modifications.

> [!NOTE]
> Les modifications apportées au profil sont appliquées aux appareils qui ont été affectés à ce profil. Cependant, il n’est pas appliqué aux appareils qui sont déjà inscrits à Intune tant que ceux-ci ne sont pas réinitialisés et réinscrits.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Alertes relatives aux appareils Windows Autopilot non affectés  <!-- 163236 -->  

Les alertes indiquent le nombre d’appareils du programme Autopilot qui n’ont pas de profils de déploiement Autopilot. Utilisez les informations de l’alerte pour créer des profils et les affecter aux appareils non affectés. Quand vous cliquez sur l’alerte, vous voyez s’afficher une liste complète d’appareils Windows Autopilot, ainsi que des informations détaillées les concernant.

Pour afficher les alertes concernant les appareils non affectés, accédez à [Intune dans le portail Azure](https://aka.ms/intuneportal), puis choisissez **Inscription d’appareil** > **Vue d’ensemble** > **Appareils non affectés**.  

## <a name="assign-a-user-to-a-specific-autopilot-device"></a>Affecter un utilisateur à un appareil Autopilot spécifique

Vous pouvez affecter un utilisateur à un appareil Autopilot spécifique. Cette affectation préremplit un utilisateur provenant d’Azure Active Directory dans la page de connexion [avec marque de société](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) lors de la configuration de Windows. Elle vous permet également de définir un nom d’accueil personnalisé. Elle ne préremplit pas ou ne modifie pas les informations de connexion Windows. Seuls les utilisateurs Intune sous licence peuvent être affectés de cette manière.

Prérequis : portail d’entreprise Azure Active Directory configuré et Windows 10, version 1809 ou ultérieure.

1. Dans [Intune dans le portail Azure](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Appareils** > choisissez l’appareil > **Affecter un utilisateur**.

    ![Capture d’écran : Affecter un utilisateur](./media/enrollment-autopilot/assign-user.png)

2. Choisissez un utilisateur Azure sous licence pour utiliser Intune et choisissez **Sélectionner**.

    ![Capture d’écran : Sélectionner un utilisateur](./media/enrollment-autopilot/select-user.png)

3. Dans la zone **Nom convivial de l’utilisateur**, tapez un nom convivial ou acceptez simplement la valeur par défaut. Cette chaîne est le nom convivial qui s’affiche quand l’utilisateur se connecte durant la configuration de Windows.

    ![Capture d’écran : Nom convivial](./media/enrollment-autopilot/friendly-name.png)

4. Choisissez **OK**.


## <a name="delete-autopilot-devices"></a>Supprimer des appareils Autopilot

Vous pouvez supprimer les appareils Windows Autopilot qui ne sont pas inscrits dans Intune :

- Supprimez les appareils Windows Autopilot dans **Inscription d’appareils** > **Inscription Windows** > **Appareils**. Sélectionnez les appareils que vous souhaitez supprimer, puis choisissez **Supprimer**. La suppression des appareils Windows Autopilot peut prendre quelques minutes.

La suppression totale d’un appareil de votre locataire vous oblige à supprimer l’appareil Intune, l’appareil Azure Active Directory et les enregistrements d’appareil Windows Autopilot. Vous pouvez effectuer toutes ces opérations à partir d’Intune :

1. Si les appareils sont inscrits dans Intune, vous devez d’abord [les supprimer à partir du panneau Tous les appareils](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

2. Supprimez les appareils d’Azure Active Directory dans **Appareils** > **Appareils Azure AD**.

3. Supprimez les appareils Windows Autopilot dans **Inscription d’appareils** > **Inscription Windows** > **Appareils**. Sélectionnez les appareils que vous souhaitez supprimer, puis choisissez **Supprimer**. La suppression des appareils Windows Autopilot peut prendre quelques minutes.

## <a name="using-autopilot-in-other-portals"></a>Utilisation d’Autopilot dans d’autres portails
Si la gestion des appareils mobiles ne vous intéresse pas, vous pouvez utiliser Autopilot dans d’autres portails. Bien que l’utilisation d’autres portails soit une option, nous vous recommandons d’utiliser seulement Intune pour gérer vos déploiements Autopilot. Quand vous utilisez Intune et un autre portail, Intune ne peut pas :  

- Afficher les modifications apportées aux profils créés dans Intune, mais modifiés dans un autre portail
- Synchroniser les profils créés dans un autre portail
- Afficher les modifications apportées aux attributions de profils effectuées dans un autre portail
- Synchroniser les attributions de profils effectuées dans un autre portail
- Afficher les modifications apportées à la liste des appareils effectuées dans un autre portail

## <a name="windows-autopilot-for-existing-devices"></a>Windows Autopilot pour les appareils existants

Vous pouvez regrouper des appareils Windows par ID de corrélation lors de l’inscription à l’aide d’[Autopilot pour les appareils existants](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) par le biais de Configuration Manager. L’ID de corrélation est un paramètre du fichier de configuration Autopilot. L’[attribut d’appareil Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) est automatiquement défini pour être égal à « OfflineAutopilotprofile-\<ID de corrélation\> ». Cela permet de créer des groupes dynamiques Azure AD arbitraires en fonction de l’ID de corrélation à l’aide de l’attribut enrollmentprofileName.

>[!WARNING] 
> Étant donné que l’ID de corrélation n’est pas prélisté dans Intune, l’appareil peut signaler l’ID de corrélation de son choix. Si l’utilisateur crée un ID de corrélation correspondant à un nom de profil DEP Apple ou Autopilot, l’appareil est ajouté à n’importe quel groupe d’appareils Azure AD dynamiques basé sur l’attribut enrollmentProfileName. Pour éviter ce conflit :
> - Créez toujours des règles de groupe dynamiques correspondant à la *totalité* de la valeur enrollmentProfileName
> - Ne faites jamais commencer les noms de profils DEP Apple ou Autopilot par « OfflineAutopilotprofile- ».

## <a name="next-steps"></a>Étapes suivantes
Une fois que vous avez configuré Windows Autopilot pour les appareils Windows 10 inscrits, découvrez comment les gérer. Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](../remote-actions/device-management.md)
