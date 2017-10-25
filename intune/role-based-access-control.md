---
title: RBAC avec Intune
titleSuffix: Azure portal
description: "Préversion Intune Azure : Découvrez comment le contrôle d’accès en fonction du rôle (RBAC) vous permet de contrôler qui peut exécuter des actions et apporter des modifications."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e9dc65389485d2a77e351b5e781824eed0612054
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2017
---
# <a name="role-based-administration-control-rbac-with-intune"></a>Contrôle d’accès en fonction du rôle (RBAC) avec Intune

Le RBAC permet de contrôler qui peut effectuer diverses tâches Intune au sein de votre organisation, et à qui s’appliquent ces tâches. Vous pouvez utiliser les rôles intégrés, qui couvrent des scénarios courants dans Intune, ou vous pouvez créer vos propres rôles. Un rôle est défini par :

- **Définition de rôle** : le nom d’un rôle, les ressources qu’il gère et les autorisations accordées pour chaque ressource.
- **Membres** : les groupes d’utilisateurs à qui sont accordées les autorisations.
- **Étendue**: les groupes d’utilisateurs ou d’appareils que les membres peuvent gérer.
- **Affectation** : lorsque la définition, les membres et l'étendue ont été configurés, le rôle est affecté.

![Exemple de RBAC Intune](./media/intune-rbac-1.PNG)

À partir du nouveau portail Azure, **Azure Active Directory (Azure AD)** fournit deux rôles d’annuaire utilisables avec Intune. Ils ont l’autorisation d’effectuer toutes les activités possibles dans Intune :

- **Administrateur général :** les utilisateurs disposant de ce rôle ont accès à toutes les fonctionnalités d’administration d’Azure AD, ainsi qu’aux services fédérés à Azure AD, comme Exchange Online, SharePoint Online et Skype Entreprise Online. La personne qui ouvre un client Azure AD devient administrateur général. Seuls les administrateurs généraux peuvent affecter d’autres rôles d'administrateur Azure AD. Votre organisation peut compter plusieurs administrateurs généraux. Ils peuvent réinitialiser le mot de passe de tous les utilisateurs et de tous les autres administrateurs.

- **Administrateur du service Intune :** les utilisateurs qui possèdent ce rôle ont des autorisations générales dans Intune lorsque ce service est présent. En outre, ce rôle fournit la possibilité de gérer les utilisateurs et les appareils et de créer et gérer les groupes.

- **Administrateur de l’accès conditionnel :** les utilisateurs disposant de ce rôle sont autorisés uniquement à afficher, créer, modifier et supprimer des stratégies d’accès conditionnel.

    > [!IMPORTANT]
    > Le rôle d’administrateur du service Intune ne donne pas la possibilité de gérer les paramètres d’accès conditionnel d’Azure AD.

    > [!TIP]
    > Intune présente également trois extensions d’Azure AD, **Utilisateurs**, **Groupes** et **Accès conditionnel**, qui sont contrôlées à l’aide du contrôle d’accès en fonction du rôle (RBAC) d’Azure AD. En outre, **l’administrateur de comptes d’utilisateurs** accomplit uniquement les activités relatives aux groupes et aux utilisateurs AAD ; il n’a pas l’autorisation d’effectuer toutes les activités possibles dans Intune. Reportez-vous à [RBAC avec Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles) pour plus d’informations.

## <a name="roles-created-in-the-intune-classic-portal"></a>Rôles créés dans le portail classique Intune

Seuls les utilisateurs de type **Administrateurs de Service** d’Intune disposant de toutes les autorisations sont migrés du portail classique Intune vers Intune dans le portail Azure. Vous devez les réaffecter**Administrateurs de Service**avec l’accès « Lecture seule » ou « Support technique » dans les rôles Intune sur le Portail Azure, et les supprimer du Portail Classic.

> [!IMPORTANT]
> Vous devrez peut-être conserver l’accès Administrateur du service Intune dans le portail classique si vos administrateurs ont encore besoin d’un accès pour gérer les PC avec Intune.

## <a name="built-in-roles"></a>Rôles intégrés

Les rôles suivants sont intégrés dans Intune ; vous pouvez les affecter à des groupes sans configuration supplémentaire :

- **Opérateur du support technique** : effectue des tâches à distance sur les utilisateurs et les appareils, et peut attribuer des applications ou des stratégies aux utilisateurs ou aux appareils.
- **Gestionnaire de stratégie et de profils** : gère la stratégie de conformité, les profils de configuration, l’inscription auprès d’Apple et les identificateurs d’appareils d’entreprise.
- **Opérateur en lecture seule** : affiche des informations sur les utilisateurs, les appareils, l’inscription, la configuration et les applications. Il ne peut pas apporter de modifications à Intune.
- **Gestionnaire d’applications** : gère les applications mobiles et gérées, et peut lire les informations sur les appareils.

### <a name="to-assign-a-built-in-role"></a>Pour affecter un rôle intégré

1. Dans **Rôles Intune**, choisissez le rôle intégré que vous souhaitez affecter.

2. Sur le panneau <*nom de rôle*> - **Propriétés**, choisissez **Gérer**, puis **Affectations**.

    > [!NOTE]
    > Il n’est pas possible de supprimer ou de modifier les rôles intégrés.

3. Sur le panneau de rôle personnalisé, choisissez **Affecter**.

4. Dans le panneau **Attributions de rôle**, entrez un **Nom** et éventuellement une **Description** pour l’attribution, puis choisissez les éléments suivants :
    - **Membres** : sélectionnez un groupe qui contient l’utilisateur auquel vous souhaitez accorder les autorisations.
    - **Étendue** : sélectionnez un groupe contenant les utilisateurs que le membre ci-dessus sera autorisé à gérer.
<br></br>
5. Une fois terminé, cliquez sur **OK**. La nouvelle affectation s’affiche dans la liste des affectations.

### <a name="intune-rbac-table"></a>Tableau RBAC d’Intune

- Téléchargez le [Tableau RBAC d’Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) pour plus d’informations sur ce que chaque rôle peut effectuer.

## <a name="custom-roles"></a>Rôles personnalisés

Vous pouvez créer un rôle personnalisé qui inclut toutes les autorisations requises pour une fonction de tâche donnée. Par exemple, si un groupe du service informatique gère les applications, les stratégies et les profils de configuration, vous pouvez ajouter toutes ces autorisations ensemble à un même rôle personnalisé.

> [!IMPORTANT]
> Pour créer, modifier ou affecter des rôles, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
> - **Administrateur général**
> - **Administrateur du service Intune**

### <a name="to-create-a-custom-role"></a>Pour créer un rôle personnalisé

1. Connectez-vous au [Portail Azure](https://portal.azure.com) avec vos informations d’identification Intune.

2. Choisissez **Autres services** dans le menu de gauche, puis tapez **Intune** dans le filtre de zone de texte.

3. Choisissez **Intune**. Le tableau de bord d’Intune s’affiche : sélectionnez alors **Rôles Intune**.

4. Sur le panneau **Rôles Intune**, choisissez **Rôles Intune**, puis **Ajouter un rôle personnalisé**.

5. Sur le panneau **Ajouter un rôle personnalisé**, entrez le nom et la description du nouveau rôle, puis cliquez sur **Autorisations**.

3. Dans le panneau **Autorisations**, sélectionnez les autorisations que vous souhaitez utiliser avec ce rôle. Utilisez le [Tableau RBAC d’Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) comme référence pour déterminer quelles autorisations vous souhaitez appliquer.

4. Une fois que vous avez terminé, choisissez **Enregistrer**.

5. Dans le panneau **Ajouter un rôle personnalisé**, cliquez sur **Créer**. Le nouveau rôle s’affiche dans la liste sur le panneau **Rôles Intune**.

### <a name="to-assign-a-custom-role"></a>Pour affecter un rôle personnalisé

1. Dans **Rôles Intune**, choisissez le rôle personnalisé que vous souhaitez affecter.

2. Sur le panneau <*nom de rôle*> - **Propriétés**, choisissez **Gérer**, puis **Affectations**. Dans ce panneau, vous pouvez aussi modifier ou supprimer des rôles existants.

3. Sur le panneau de rôle personnalisé, choisissez **Affecter**.

4. Dans le panneau **Attributions de rôle**, entrez un **Nom** et éventuellement une **Description** pour l’attribution, puis choisissez les éléments suivants :
    - **Membres** : sélectionnez un groupe qui contient l’utilisateur auquel vous souhaitez accorder les autorisations.
    - **Étendue** : sélectionnez un groupe contenant les utilisateurs que le membre ci-dessus sera autorisé à gérer.
<br></br>
5. Une fois terminé, cliquez sur **OK**. La nouvelle affectation s’affiche dans la liste des affectations.

## <a name="next-steps"></a>Étapes suivantes

[Utiliser le rôle d’opérateur du support technique d’Intune avec le portail de résolution des problèmes](help-desk-operators.md)

## <a name="see-also"></a>Voir aussi

[Affecter des rôles avec Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
