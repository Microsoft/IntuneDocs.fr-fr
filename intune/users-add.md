---
title: Ajouter des utilisateurs et accorder des autorisations
description: "Synchroniser des utilisateurs locaux avec Azure AD et octroyer des autorisations d’administrateur pour votre abonnement Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/19/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7873481ccd33d2eaf4ec1a4c7fadf30c61b8d42e
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2017
---
# <a name="add-users-and-give-administrative-permission-to-intune"></a>Ajouter des utilisateurs et accorder une autorisation d’administration à Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Cette rubrique explique aux administrateurs comment ajouter des utilisateurs à Intune et décrit les autorisations d’administration disponibles dans le service Intune.

En tant qu’administrateur, vous pouvez ajouter directement des utilisateurs ou synchroniser des utilisateurs à partir de votre annuaire Active Directory local. Une fois ajoutés, les utilisateurs peuvent inscrire des appareils et accéder aux ressources de l’entreprise. Vous pouvez aussi accorder aux utilisateurs des autorisations supplémentaires, notamment *administrateur général* et *administrateur de service*.

## <a name="add-users-to-intune"></a>Ajouter des utilisateurs à Intune
Vous pouvez ajouter manuellement des utilisateurs à votre abonnement Intune via le [portail Office 365](https://www.office.com/signin) ou le [portail Intune Azure](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). Un administrateur peut modifier les comptes d’utilisateurs pour attribuer des licences Intune. Vous pouvez attribuer des licences dans le portail Office 365 ou le portail Intune Azure. Pour plus d’informations sur l’utilisation du portail Office 365, consultez [Ajouter des utilisateurs individuellement ou en bloc au portail Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Ajouter des utilisateurs Intune dans le centre d’administration Office 365
1. Connectez-vous au [portail Office 365](https://www.office.com/signin) avec un compte d’administrateur général ou d’administrateur de gestion des utilisateurs.
2. Dans le menu Office 365, sélectionnez **Admin**.
3. Dans le centre d’administration, sélectionnez **Ajouter un utilisateur**.

  ![Capture d’écran Office 365 Admin](media/office-add-user.png)

4. Spécifiez les détails d’utilisateur suivants :
  - **Prénom**
  - **Nom**
  - **Nom d’affichage**
  - **Nom d’utilisateur** : nom UPN stocké dans Azure Active Directory et utilisé pour accéder au service
  - **Emplacement**
  - **Coordonnées** (facultatives)
  - **Mot de passe** : généré automatiquement ou spécifié

     ![Capture d’écran Office 365 Admin](media/office-add-user-details.png)

5. Attribuez une licence Intune. Sélectionnez **Licences de produit** et choisissez la licence de produit. Une licence incluant Intune est nécessaire.
6. Choisissez **Ajouter** pour créer l’utilisateur.

### <a name="add-intune-users-in-the-azure-intune-portal"></a>Ajouter des utilisateurs Intune dans le portail Azure Intune
1. Connectez-vous au [portail Azure](https://portal.azure.com) et accédez à **Plus de services** > **Surveillance + gestion** > **Intune**. Vous pouvez aussi rechercher **Intune** dans les *ressources*.
2. Sélectionnez **Utilisateurs**.
3. Dans le centre d’administration, sélectionnez **Nouvel utilisateur**.
  ![Capture d’écran Office 365 Admin](media/intune-add-user.png)
4. Spécifiez les détails d’utilisateur suivants :
  - **Nom**
  - **Nom d’utilisateur** : nouveau nom dans le portail Azure Active Directory ![Capture d’écran Office 365 Admin](media/intune-add-user-info.png) Choisissez **OK** pour continuer.
5. Si vous le souhaitez, vous pouvez spécifier les propriétés utilisateur suivantes :
  - **Profil** : informations professionnelles, notamment la **Fonction** et le **Service**
  -  **Groupes** : sélectionnez les groupes à ajouter pour l’utilisateur
  - **Rôle d’annuaire** : accordez à l’utilisateur des autorisations d’administration incluant un rôle Administrateur de services fédérés Intune.

  Sélectionnez **Créer** pour ajouter le nouvel utilisateur à Intune.
6. Sélectionnez **Profil**, puis choisissez un **Lieu d’utilisation** pour le nouvel utilisateur. Le lieu d’utilisation est obligatoire pour pouvoir affecter une licence Intune au nouvel utilisateur. Choisissez **Enregistrer** pour continuer.
    ![Capture d’écran Office 365 Admin](media/intune-add-user-loc.png)
7. Sélectionnez **Licences**, puis **Affecter** pour affecter une licence Intune à cet utilisateur. Une licence Intune est nécessaire pour inscrire des appareils ou accéder aux ressources de l’entreprise. Sélectionnez **Produits**, puis choisissez successivement le type de licence, **Sélectionner** et **Affecter**.

## <a name="grant-admin-permissions"></a>Accorder des autorisations d’administration

Après avoir ajouté des utilisateurs à votre abonnement Intune, nous vous recommandons d’attribuer une autorisation d’administration à quelques utilisateurs.  Pour accorder des autorisations d’administrateur, effectuez les étapes suivantes :

### <a name="give-admin-permissions-in-office-365"></a>Accorder des autorisations d’administrateur dans Office 365
1. Connectez-vous au [portail Office 365](https://www.office.com/signin) avec un compte d’administrateur général.
2. Dans le menu Office 365, sélectionnez **Admin**.
3. Dans le centre d’administration, choisissez **Utilisateurs actifs**, puis l’utilisateur auquel accorder des autorisations d’administrateur.
4. Dans la colonne **Rôles**, choisissez **Modifier**.
  ![Capture de l’écran d’attribution des rôles dans Office 365](./media/office-assign-roles-open.png)
5. Choisissez l’autorisation d’administrateur à accorder à partir de la liste des rôles disponibles.
![Image de l’affectation de rôles dans le portail Office 365.](./media/office-assign-roles.png)
6. Choisissez **Enregistrer**.

### <a name="give-admin-permissions-in-the-intune-portal"></a>Accorder des autorisations d’administrateur dans le portail Intune
1. Connectez-vous au [portail Intune](https://www.office.com/signin) avec un compte d’administrateur général.
2. Dans le portail Intune, choisissez **Utilisateur**, puis l’utilisateur auquel vous voulez accorder des autorisations d’administrateur.
3. Sélectionnez **Rôle d’annuaire**, puis l’autorisation.
  ![Capture d’écran](./media/add-intune-directory-role.png)
4. Choisissez **Enregistrer**.

### <a name="types-of-administrators"></a>Types d’administrateurs

Affectez une ou plusieurs autorisations d’administrateur à des utilisateurs. Ces autorisations définissent l’étendue administrative des utilisateurs et les tâches qu’ils peuvent gérer. Les autorisations d’administrateur sont communes aux différents services cloud Microsoft, même si certains services peuvent ne pas prendre en charge certaines autorisations. Le portail Office 365 et le portail Intune répertorient tous deux les rôles d’administrateur limités qui ne sont pas utilisés par Intune. Les autorisations d’administrateur Intune incluent les options suivantes :

- **Administrateur général** (Office 365 et Intune) : accède à toutes les fonctionnalités d’administration dans Intune. Par défaut, la personne qui s’inscrit à Intune devient un administrateur général. Les administrateurs généraux sont les seuls administrateurs qui peuvent affecter d’autres rôles d’administrateur. Vous pouvez avoir plusieurs administrateurs généraux dans votre organisation. En guise de bonne pratique, nous vous recommandons d’attribuer ce rôle à seulement quelques personnes au sein de votre entreprise pour réduire les risques.
- **Administrateur de mots de passe** (Office 365 et Intune) : réinitialise les mots de passe, gère les demandes de service et surveille l’intégrité des services. Les administrateurs de mots de passe sont limités à la réinitialisation des mots de passe des utilisateurs.
- **Administrateur de service** (Office 365 et Intune) : ouvre les demandes de support auprès de Microsoft et visualise le tableau de bord du service et le centre de messages. Il dispose d’une autorisation « Afficher uniquement », sauf pour l’ouverture et la lecture des tickets de support.
- **Administrateur de facturation** (Office 365 et Intune) : effectue des achats, gère les abonnements et les tickets de support et surveille l’intégrité des services.
- **Administrateur d’utilisateurs** (Office 365 et Intune) : réinitialise les mots de passe, surveille l’intégrité du service, ajoute et supprime des comptes d’utilisateurs, et gère les demandes de service. L’administrateur de gestion des utilisateurs ne peut pas supprimer un administrateur général, créer d’autres rôles d’administrateur ou réinitialiser le mot de passe des autres administrateurs.
- **Administrateur de services fédérés Intune** : toutes les autorisations d’administrateur général Intune, sauf celle de créer des administrateurs avec des options **Rôle d’annuaire**.

Le compte que vous utilisez pour créer votre abonnement Microsoft Intune est un administrateur général. Nous vous recommandons de ne pas utiliser un administrateur général pour les tâches de gestion quotidiennes. Un administrateur n’a pas besoin d’une licence Intune pour accéder au portail Intune. 

Pour accéder au portail Office 365, l’option **Connecter les utilisateurs autorisés** doit être activée pour votre compte. Dans le portail Intune, sous **Profil**, affectez la valeur **Non** à **Bloquer la connexion** pour autoriser l’accès. Cet état diffère de celui défini pour la possession d’une licence pour l’abonnement. Par défaut, tous les comptes d’utilisateur sont définis avec l’état **Autorisé**. Les utilisateurs sans autorisations d’administrateur peuvent utiliser le portail Office 365 pour réinitialiser les mots de passe Intune.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Synchroniser Active Directory et ajouter des utilisateurs à Intune
Vous pouvez configurer la synchronisation d’annuaires pour importer des comptes d’utilisateur de votre instance Active Directory locale vers Microsoft Azure Active Directory (Azure AD), qui comprend les utilisateurs Intune. Le fait que votre service Active Directory local soit connecté à tous vos services Azure Active Directory facilite grandement la gestion des identités des utilisateurs. Vous pouvez aussi configurer les fonctionnalités d'authentification unique pour permettre à vos utilisateurs de s'authentifier de manière simple et naturelle. Si vous liez le même [locataire Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) à plusieurs services, les comptes d’utilisateur que vous avez précédemment synchronisés sont accessibles à tous les services cloud.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Guide pratique pour synchroniser les utilisateurs locaux avec Azure AD
Le seul outil dont vous avez besoin pour synchroniser vos comptes d’utilisateur avec Azure AD est l’[Assistant Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). L’Assistant Azure AD Connect vous offre une expérience simplifiée qui vous guide pour connecter votre infrastructure d’identité locale au cloud.  Choisissez votre topologie en fonction de vos besoins (un ou plusieurs annuaires, synchronisation des mots de passe ou fédération). L’Assistant déploie et configure tous les composants nécessaires au fonctionnement de votre connexion. Notamment les services de synchronisation, les services AD FS et le module PowerShell Azure AD.

> [!TIP]
> Azure AD Connect comporte des fonctionnalités qui étaient auparavant connues sous les noms Dirsync et Azure AD Sync. Obtenez des informations plus détaillées sur l’[intégration d’annuaire](http://technet.microsoft.com/library/jj573653.aspx). Pour plus d’informations sur la synchronisation des comptes d’utilisateurs entre un annuaire local et Azure AD, consultez [Ressemblances entre Active Directory et Azure AD](http://technet.microsoft.com/library/dn518177.aspx).
