---
title: Configurer l’intégration de Symantec avec Microsoft Intune
titleSuffix: Microsoft Intune
description: Comment configurer la solution Symantec Endpoint Protection Mobile avec Microsoft Intune pour contrôler l’accès des appareils mobiles aux ressources de votre entreprise.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/21/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 359448d9-2384-42ac-a21c-a25148c20a7b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b44164ff31be89e01eb895a8b889e07bb3f704f
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61506595"
---
# <a name="set-up-symantec-endpoint-protection-mobile-integration-with-intune"></a>Configurer l’intégration de Symantec Endpoint Protection Mobile avec Intune

Effectuez les étapes suivantes pour intégrer la solution Symantec Endpoint Protection Mobile (SEP Mobile) avec Intune. Vous devez ajouter des applications SEP Mobile à Azure AD pour disposer de fonctionnalités à authentification unique.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="azure-ad-account-used-to-integrate-intune-and-sep-mobile"></a>Compte Azure AD permettant d’intégrer Intune et SEP Mobile

-   Vérifiez que vous avez correctement configuré le compte Azure AD configuré dans la [console de gestion Symantec Endpoint Protection Mobile ](https://aad.skycure.com) avant de démarrer le processus de configuration SEP Mobile de base.
- Le compte Azure AD doit être un compte d’administrateur général pour effectuer l’intégration.
### <a name="network-setup"></a>Configuration du réseau

Vous pouvez vous assurer que votre réseau est correctement configuré pour l’intégration avec SEP Mobile en faisant référence à l’article Symantec [Définition de votre configuration réseau](https://portal.skycure.com/articles/Documentation/Setting-up-your-network-configuration-26-8-2016).

### <a name="full-integration-vs-read-only"></a>Intégration complète et Lecture seule

SEP Mobile prend en charge deux modes d’intégration avec Intune :

-   **Intégration en lecture seule (configuration de base) :** répertorie uniquement les appareils d’Azure Active Directory et les charge dans la console de gestion Symantec Endpoint Protection Mobile.
<br>
    -   Si les cases **Report the health and risk of devices to Intune** (Signaler l’intégrité et les risques des appareils à Intune) et **Also report security incidents to Intune** (Signaler également les incidents de sécurité à Intune) ne sont pas cochées dans la console de gestion Symantec Endpoint Protection Mobile, l’intégration s’effectue en lecture seule et par conséquent ne change jamais l’état d’un appareil (conforme ou non conforme) dans Intune.
<br></br>
-   **Intégration complète :** permet à SEP Mobile de signaler les appareils à risques et les détails des incidents de sécurité à Intune, créant ainsi une communication bidirectionnelle entre les deux services de cloud.

### <a name="how-are-the-sep-mobile-apps-used-with-azure-ad-and-intune"></a>Comment les applications SEP Mobile sont-elles utilisées avec Azure AD et Intune ?

-   **Application iOS :** permet aux utilisateurs finaux de se connecter à Azure AD à l’aide d’une application iOS.

-   **Application Android :** permet aux utilisateurs finaux de se connecter à Azure AD à l’aide d’une application Android.

-   **Application de gestion :** application SEP Mobile Azure AD multilocataire qui permet la communication de service à service avec Intune.

## <a name="to-set-up-the-read-only-integration-between-intune-and-sep-mobile"></a>Pour configurer l’intégration en lecture seule entre Intune et SEP Mobile

> [!IMPORTANT]
> Les informations d’identification de l’administrateur SEP Mobile figurent dans un compte de messagerie qui appartient à un utilisateur valide dans Azure Active Directory, sinon la connexion échouera. SEP Mobile utilise Azure Active Directory pour authentifier ses administrateurs à l’aide d’une authentification unique Single Sign On (SSO).

1.  Accédez à [Console de gestion Symantec Endpoint Protection Mobile](https://aad.skycure.com).

2.  Entrez vos **informations d'identification de l’administrateur SEP Mobile**, puis choisissez **Continuer**.

3.  Sélectionnez **Paramètres**, puis choisissez **Configuration de base** sous **Intégration à Intune**.

4.  En regard de l’**application iOS**, choisissez **Ajouter à Active Directory**.

    ![Image de la console de gestion Symantec Endpoint Protection Mobile](./media/symantec-portal-basic-add.png)

5.  Lorsque la page de connexion s’affiche, entrez vos informations d’identification Intune, puis cliquez sur **Accepter**.

    ![Image de l’invite de connexion Intune à l’application iOS](./media/symantec-portal-basic-accept.png)

6.  Une fois l’application ajoutée à Azure AD, vous verrez une indication que l’application a été ajoutée avec succès.

    ![Image de l’écran de finalisation de l’application iOS](./media/symantec-portal-basic-added.png)

7. Répétez ces étapes pour les applications **SEP Mobile Android** et **Gestion** applications.

### <a name="add-an-azure-ad-security-group-into-sep-mobile"></a>Ajouter un groupe de sécurité Azure AD dans SEP Mobile

Vous devez ajouter un groupe de sécurité Azure AD qui contient tous les appareils exécutant SEP Mobile.

-  Entrez et sélectionnez tous les groupes de sécurité des appareils qui exécutent SEP Mobile, puis enregistrez les modifications.

    ![Image des groupes d’utilisateurs pour les applications SEP Mobile](./media/symantec-portal-basic-groups.png)   

SEP Mobile synchronise les appareils exécutant son service Mobile Threat Defense avec les groupes de sécurité Azure AD.

![Image de la configuration du groupe de sécurité sur la console de gestion SEP Mobile](./media/symantec-portal-basic-status.png)

## <a name="to-set-up-the-full-integration-between-intune-and-sep-mobile"></a>Configurer l’intégration complète entre Intune et SEP Mobile

### <a name="retrieve-the-directory-id-in-azure-ad"></a>Récupérer l’ID de répertoire dans Azure AD

1. Connectez-vous au [portail Azure](https://portal.azure.com).

2. Tapez « Active Directory » dans la zone de recherche, puis sélectionnez **Azure Active Directory**.

3. Choisissez **Propriétés**.

4. À côté de l’**ID du répertoire**, choisissez l’icône de copie, puis collez-la à un emplacement sûr. Vous aurez besoin de cet identificateur à une étape ultérieure.

    ![Image de l’ID du répertoire dans le portail Azure](./media/symantec-azure-portal-directory-ID.png)

### <a name="optional-create-a-dedicated-security-group-for-devices-that-need-to-run-the-sep-mobile-apps"></a>(Facultatif) Créer un groupe de sécurité dédié pour les appareils qui doivent exécuter les applications SEP Mobile
1. Dans le [portail Azure](https://portal.azure.com), sous **Gérer**, choisissez **Utilisateurs et groupes**, puis choisissez **Tous les groupes**.

2. Choisissez le bouton **Ajouter**. Tapez un **nom** de groupe. Sous **Type d’appartenance**, choisissez **Affecté**.

3. Dans le panneau **Membres**, sélectionnez les membres du groupe, puis choisissez le **Sélectionner**.

4. Dans le panneau **Groupe**, choisissez **Créer**.

### <a name="set-up-the-integration-between-symantec-endpoint-protection-mobile-and-intune"></a>Configurer l’intégration entre Symantec Endpoint Protection Mobile et Intune

1.  Accédez à [Console de gestion Symantec Endpoint Protection Mobile](https://aad.skycure.com).

2.  Entrez vos **informations d'identification de l’administrateur SEP Mobile**, puis choisissez **Continuer**.

3.  Accédez à la section **Paramètres** > **Intégrations** > **Intune** > **Sélection d’intégration EMM**.

4. Dans la case **ID de répertoire**, collez l’ID de répertoire que vous avez copié à partir d’Azure Active Directory dans la section précédente et enregistrez les paramètres.

    ![Image de l’ID du répertoire dans le portail SEP Mobile](./media/symantec-portal-directory-ID.png)     

5. Accédez à la section **Paramètres** > **Intégrations** > **Intune** > **Configuration de base**.

6. En regard de l’**application iOS**, choisissez le bouton **Ajouter à Active Directory**.

    ![Image de l’ajout de l’application iOS à Active Directory](./media/symantec-portal-basic-add.png)   

7.  Connectez-vous en utilisant les informations d’identification Azure Active Directory pour le compte Office 365 qui gère le répertoire.

8.  Choisissez le bouton **Accepter** pour ajouter l’application iOS SEP Mobile à Azure Active Directory.

    ![Image du bouton Accepter](./media/symantec-portal-basic-accept.png)     

9.  Répétez ce processus pour l’**application Android** et pour l’**applications de gestion**.

10. Sélectionnez tous les groupes d’utilisateurs qui doivent exécuter les applications SEP Mobile, par exemple, le groupe de sécurité que vous avez créé précédemment.

    ![Image des groupes d’utilisateurs pour les applications SEP Mobile](./media/symantec-portal-basic-groups.png)   

11.  SEP Mobile synchronise les appareils dans les groupes sélectionnés et commence à transmettre des informations à Intune. Vous pouvez afficher ces données dans la section Intégration complète. Accédez à la section **Paramètres** > **Intégrations** > **Intune** > **Intégration complète**.

     ![Image de l’intégration complète SEP Mobile terminée](media/symantec-portal-basic-status.PNG)
## <a name="next-steps"></a>Étapes suivantes

[Configurer des applications SEP Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)
