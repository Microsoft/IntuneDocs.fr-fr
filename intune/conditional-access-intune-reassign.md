---
title: Migrer l’accès conditionnel vers le portail Azure | Microsoft Intune
description: Réaffectez les stratégies d’accès conditionnel précédemment créées dans le portail classique Intune vers le portail Azure.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83cc08af092f8715e2d69caf3fc1b1df607b0f4e
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845701"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Réaffecter les stratégies d’accès conditionnel à partir du portail classique Intune vers le portail Azure

Avec le nouveau portail Azure, l’accès conditionnel prend en charge plusieurs stratégies par application ainsi que davantage de possibilités de personnalisation. Si vous aviez créé des stratégies d’accès conditionnel dans le portail classique, vous pouvez les migrer vers le portail Azure. 

## <a name="before-you-begin"></a>Avant de commencer

Si vous êtes prêt à passer au portail Azure, suivez les étapes dans cette rubrique pour réaffecter les stratégies d’accès conditionnel précédemment créées dans le portail classique Intune :

- Regroupez les stratégies d’accès conditionnel déjà créées afin de savoir quels paramètres vous devez réaffecter ultérieurement.

- Suivez les étapes décrites dans cette rubrique pour recréer ces stratégies dans le portail Azure.

- Désactivez les stratégies conditionnelles dans le portail classique Intune une fois que vous avez vérifié que les nouvelles stratégies fonctionnent comme prévu dans le portail Azure.
<br /><br />
    - **Avant de désactiver** les stratégies d’accès conditionnel dans le portail classique Intune, planifiez le déplacement des utilisateurs vers la nouvelle stratégie. Il existe deux approches :
<br /><br />
        - **Utiliser le même groupe d’inclusions pour appliquer les stratégies créées dans le portail Azure et créer un groupe d’exemptions à utiliser avec les stratégies appliquées par le portail classique Intune**.
            - Déplacez progressivement certains utilisateurs dans le groupe d’exemptions indiqué dans le portail classique. Cela empêche l’application des stratégies ciblées par le portail classique Intune. Les stratégies créées et ciblées vers le même groupe d’utilisateurs dans le portail Azure sont appliquées en plus de celles appliquées dans le portail classique Intune. 
<br /><br />
        - **Créer un groupe pour cibler les stratégies d’accès conditionnel dans le portail Azure**. Si vous choisissez cette approche, vous devez effectuer les opérations suivantes :
            - Supprimez progressivement des utilisateurs des groupes de sécurité qui sont la cible des stratégies d’accès conditionnel dans le portail classique Intune.
            - Une fois que vous avez confirmé que la nouvelle stratégie fonctionne pour ces utilisateurs, vous pouvez désactiver la stratégie dans le portail classique Intune. 
<br /><br />
- Si vous avez des paramètres de stratégie d’accès conditionnel configurés pour utiliser EAS (Exchange Active Sync) dans le portail classique Intune, consultez les [instructions de cette rubrique](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) pour **réaffecter les paramètres de stratégie d’accès conditionnel EAS dans le portail Azure**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Pour vérifier vos stratégies d’accès conditionnel basé sur l’appareil dans le portail classique Intune

1.  Accédez au [portail classique Intune](https://manage.microsoft.com) et connectez-vous à l’aide de vos informations d’identification.

2.  Choisissez **Stratégie** dans le menu de gauche.

3.  Choisissez **Accès conditionnel**, puis sélectionnez le service cloud Microsoft (par exemple, Exchange Online ou SharePoint Online) pour lequel vous avez créé une stratégie d’accès conditionnel.

4.  Notez les paramètres d’accès conditionnel et faites-y référence quand vous créez les mêmes stratégies d’accès conditionnel dans le portail Azure.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>Utilisation conjointe de stratégies d’accès conditionnel basé sur l’application et sur l’appareil

Le panneau **Intune App Protection** dans le portail Azure permet aux administrateurs de définir des règles conditionnelles basées sur l’application afin que seules les applications qui prennent en charge les stratégies de protection des applications Intune soient autorisées à accéder aux ressources d’entreprise. Vous pouvez choisir de chevaucher ces stratégies d’accès conditionnel basé sur l’application avec des stratégies d’accès conditionnel basé sur l’appareil. Vous pouvez combiner les stratégies conditionnelles basées sur l’application et l’appareil (AND logique) ou fournir une option (OR logique). Si vos exigences de stratégie d’accès conditionnel sont :

- Exiger un appareil conforme **ET** utiliser l’application approuvée.
    - Vous devez définir votre stratégie d’accès conditionnel à l’aide du [panneau d’accès conditionnel Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) et du [panneau Intune App Protection](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Exiger un appareil conforme **OU** utiliser l’application approuvée.
    - Vous devez définir votre stratégie d’accès conditionnel à l’aide du [portail classique Intune](https://manage.microsoft.com) et du [panneau Intune App Protection](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Cette rubrique fournit des captures d’écran comparant l’expérience de l’utilisateur dans le portail classique Intune et le portail Azure.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Réaffecter des stratégies d’accès conditionnel basé sur l’appareil Intune

1. Accédez à [Conditional access in the Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) (Accès conditionnel dans le portail Azure) et connectez-vous avec vos informations d’identification.

2. Choisissez **Nouvelle stratégie**.

3. Spécifiez un nom pour la stratégie.

4. Sous la section **Affectations**, choisissez **Utilisateurs et groupes** pour cibler la nouvelle stratégie d’accès conditionnel.
    
    ![Image comparant l’interface utilisateur des groupes d’utilisateurs dans les portails Intune et Azure](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > La sélection que vous effectuez pour le portail Azure doit correspondre à celle que vous avez effectuée pour le portail Classic. Par exemple, si tous les utilisateurs sont sélectionnés dans le portail classique Intune, sélectionnez **Tous les utilisateurs** dans le portail Azure. En outre, si vous avez choisi l’option **Groupes exempts** dans le portail classique Intune, excluez aussi ces groupes sélectionnés dans le portail Azure.

5. Après avoir choisi votre groupe, cliquez sur **Sélectionner**, puis sur **Terminé**.

6. Sous la section **Affectations**, choisissez **Applications cloud**.

7. Dans le panneau **Applications cloud**, choisissez **Sélectionner les applications**.

8. Choisissez l’application à laquelle vous voulez appliquer la nouvelle stratégie d’accès conditionnel, puis cliquez sur **Sélectionner**.

9. Cliquez sur **Terminé**.

    ![Image comparant l’interface utilisateur des applications cloud dans les portails Intune et Azure](./media/reassign-ca-3.png)

    > [!TIP] 
    > Si vous avez plusieurs applications avec la même stratégie, envisagez de les regrouper dans une seule stratégie dans le portail Azure.

10. Sous la section **Affectations**, choisissez **Conditions**.

11. Dans le panneau **Conditions**, choisissez **Plateformes d’appareils**, puis les plateformes d’appareils applicables.

12. Une fois les plateformes d’appareils choisies, cliquez sur **Terminé** à deux reprises.

    ![Image comparant l’interface utilisateur des plateformes d’appareils dans les portails Intune et Azure](./media/reassign-ca-4.png)

    > [!TIP] 
    > Si vous avez choisi des plateformes individuelles dans le portail classique Intune, choisissez les plateformes individuelles dans le portail Azure.

    > [!NOTE] 
    > Vous pouvez spécifier les options de jonction de domaine ou de conformité pour Windows ultérieurement.

13. Sous la section **Affectations**, choisissez **Conditions**.

14. Dans le panneau **Conditions**, choisissez **Applications clientes**, puis l’application cliente applicable.

15. Une fois l’application cliente choisie, cliquez sur **Terminé** à deux reprises.

    ![Image comparant l’interface utilisateur des applications clientes dans les portails Intune et Azure](./media/reassign-ca-6.png)

16. Si vous avez choisi les paramètres du navigateur dans le portail classique Intune, sélectionnez à la fois **Navigateur** et **Applications mobiles et clients de bureau** dans le portail Azure. Si vous n’avez pas choisi les paramètres du navigateur dans le portail classique Intune, choisissez uniquement **Applications mobiles et clients de bureau**. 

17. Sous la section **Contrôles d’accès**, choisissez **Accorder**.

18. Sous **Accorder les contrôles d’accès**, choisissez **Exiger que l’appareil soit marqué comme conforme**, puis cliquez sur **Sélectionner**.

19. Si vous avez une stratégie pour exiger des appareils Windows joints au domaine et que vous autorisez également des appareils Windows conformes et inscrits auprès d’Intune, choisissez **Exiger un appareil joint au domaine** et **Exiger que l’appareil soit marqué comme conforme**, avec **Demander un des contrôles sélectionnés**.

20. Si vous n’autorisez pas les appareils Windows conformes et inscrits auprès d’Intune, exemptez la stratégie Windows de la stratégie actuelle. Créez ensuite une stratégie distincte avec **Windows** comme valeur de **Plateformes d’appareils**, incluez les autres conditions comme définies ci-dessus et choisissez **Exiger un appareil joint au domaine** sous **Accorder les contrôles d’accès**.

21. Dans le panneau de la stratégie d’accès conditionnel **Nouveau**, activez la bascule **Activer la stratégie**, puis cliquez sur **Créer**.

    ![Image comparant l’interface utilisateur des stratégies d’accès conditionnel dans Intune et Azure](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Réaffecter des stratégies d’accès conditionnel basé sur l’appareil Intune pour les clients EAS

Si vous avez configuré les paramètres EAS (Exchange Active Sync) dans le cadre d’une stratégie Exchange Online dans le portail classique Intune, vous devez créer une deuxième stratégie d’accès conditionnel dans le portail Azure.

1. Accédez à [Conditional access in the Azure portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) (Accès conditionnel dans le portail Azure) et connectez-vous avec vos informations d’identification.

2. Choisissez **Nouvelle stratégie**.

3. Spécifiez un nom pour la stratégie.

4. Sous la section **Affectations**, choisissez **Utilisateurs et groupes** pour cibler la nouvelle stratégie d’accès conditionnel.

    ![Image montrant une comparaison de l’interface utilisateur des groupes d’utilisateurs entre les portails Intune et Azure](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > La sélection que vous effectuez pour le portail Azure doit correspondre à celle que vous avez effectuée pour le portail Azure. Par exemple, si tous les utilisateurs sont sélectionnés dans le portail classique Intune, sélectionnez **Tous les utilisateurs** dans le portail Azure. En outre, si vous avez choisi l’option **Groupes exempts** dans le portail classique Intune, excluez aussi ces groupes sélectionnés dans le portail Azure.

5. Après avoir choisi votre groupe, cliquez sur **Sélectionner**, puis sur **Terminé**.

6. Sous la section **Affectations**, choisissez **Applications cloud**.

7. Dans le panneau **Applications cloud**, cliquez sur **Sélectionner les applications**, puis choisissez **Exchange Online**. Cliquez ensuite sur **Sélectionner**, puis sur **Terminé**.

    ![Image comparant l’interface utilisateur des applications cloud dans les portails Intune et Azure](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > Les stratégies d’accès conditionnel pour les clients EAS ne peuvent inclure aucune autre application cloud.

8. Dans le panneau **Conditions**, choisissez **Applications clientes**, puis l’application cliente applicable. Si vous avez choisi de bloquer les clients qui ne sont pas pris en charge par Intune, utilisez l’option **Appliquer la stratégie uniquement aux plateformes prises en charge**.

    ![Image montrant une comparaison de l’interface utilisateur des applications clientes entre les portails Intune et Azure](./media/reassign-ca-15.png)

9. Une fois l’application cliente choisie, cliquez sur **Terminé** à deux reprises.

10. Sous la section **Contrôles d’accès**, choisissez **Accorder**.

11. Sous **Accorder les contrôles d’accès**, choisissez **Exiger que l’appareil soit marqué comme conforme**, puis cliquez sur **Sélectionner**.

    ![Image comparant l’interface utilisateur pour accorder l’accès dans les portails Intune et Azure](./media/reassign-ca-16.png)

12. Dans le panneau de la stratégie d’accès conditionnel **Nouveau**, activez la bascule **Activer la stratégie**, puis cliquez sur **Créer**.

    ![Comparaison de l’interface utilisateur pour activer les stratégies d’accès conditionnel dans Intune et Azure](./media/reassign-ca-17.png)

> [!NOTE]
> Si vous configurez des **Plateformes d’appareils**, l’enregistrement de la stratégie échoue avec l’erreur « La configuration de la stratégie n’est pas prise en charge ». Exchange ActiveSync ne peut pas identifier la plateforme utilisée par l’appareil qui se connecte. Par conséquent, la configuration de plateformes d’appareils spécifiques n’est pas prise en charge lors de la création d’une stratégie pour les appareils Exchange ActiveSync.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Désactiver les stratégies d’accès conditionnel dans le portail classique Intune

Une fois que vous avez réaffecté vos stratégies d’accès conditionnel dans le portail Azure, il est important de désactiver progressivement les stratégies d’accès conditionnel créées précédemment dans le portail classique Intune. Vous devrez peut-être aussi utiliser le même groupe de sécurité pour appliquer les stratégies d’accès conditionnel créées dans le portail Azure.

> [!NOTE]
> Avant de désactiver vos stratégies d’accès conditionnel dans le portail classique Intune, consultez la section [Avant de commencer](#before-you-begin) au début de cette rubrique.

### <a name="to-disable-the-conditional-access-policies"></a>Pour désactiver les stratégies d’accès conditionnel

1.  Accédez au [portail classique Intune](https://manage.microsoft.com) et connectez-vous à l’aide de vos informations d’identification.

2.  Choisissez **Stratégie** dans le menu de gauche.

3.  Choisissez **Accès conditionnel**, puis sélectionnez le service cloud Microsoft (par exemple, Exchange Online ou SharePoint Online) pour lequel vous avez créé une stratégie d’accès conditionnel.

4.  Décochez l’option **Activer la stratégie d’accès conditionnel**, puis cliquez sur **Enregistrer**.

    ![Image de la désactivation des stratégies d’accès conditionnel dans le portail classique Intune](./media/reassign-ca-18.png)

## <a name="see-also"></a>Voir aussi

- [Utilisations courantes de l’accès conditionnel avec Intune](conditional-access-intune-common-ways-use.md)
- [accès conditionnel en fonction des applications avec Intune](app-based-conditional-access-intune.md)
- [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
