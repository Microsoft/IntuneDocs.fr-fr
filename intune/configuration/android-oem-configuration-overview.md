---
title: Utiliser OEMConfig sur les appareils Android Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez Microsoft Intune pour gérer et utiliser des appareils exécutant Android Entreprise avec OEMConfig. Examinez toutes les étapes, notamment une vue d’ensemble, examinez les prérequis, créez le profil de configuration dans Intune et consultez la liste des applications OEMConfig prises en charge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/02/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1bc811bcac80f8321284ece8d3860efc7164a270
ms.sourcegitcommit: a25f556aa9df4fcd9fdacccd12c9029bc6c5fe20
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78256320"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Utiliser et gérer des appareils Android Entreprise avec OEMConfig dans Microsoft Intune

Dans Microsoft Intune, vous pouvez utiliser OEMConfig pour ajouter, créer et personnaliser des paramètres spécifiques aux OEM pour les appareils Android Entreprise. OEMConfig est généralement utilisé pour configurer les paramètres qui ne sont pas intégrés dans Intune. Les différents fabricants d’ordinateurs OEM incluent des paramètres différents. Les paramètres disponibles dépendent de ce que le fabricant d’ordinateurs OEM inclut dans son application OEMConfig.

Cette fonctionnalité s’applique à :  

- Android Entreprise

Cet article décrit OEMConfig, liste les prérequis, montre comment créer un profil de configuration et liste les applications OEMConfig prises en charge dans Intune.

## <a name="overview"></a>Vue d’ensemble

Les stratégies OEMConfig sont un type spécial de stratégie de configuration des appareils similaire à la [stratégie de configuration des applications](../apps/app-configuration-policies-overview.md). OEMConfig est un standard défini par Google, qui utilise la configuration d’application dans Android pour envoyer des paramètres d’appareil à des applications écrites par des OEM. Ce standard permet aux OEM et aux EMM (Enterprise mobility management) de créer et de prendre en charge des fonctionnalités spécifiques aux OEM de façon standardisée. [Découvrez plus d’informations sur OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Historiquement, les EMM, comme Intune, ont permis de créer manuellement la prise en charge des fonctionnalités spécifiques à un OEM après avoir été introduits par l’OEM. Cette approche se traduit par des efforts en double et une adoption lente.

Avec OEMConfig, un OEM crée un schéma qui définit les fonctionnalités de gestion spécifiques à l’OEM. L’OEM incorpore le schéma dans une application, puis place cette application sur Google Play. L’EMM lit le schéma à partir de l’application, puis expose le schéma dans la console administrateur de la gestion de la mobilité d’entreprise. La console permet aux administrateurs Intune de configurer les paramètres dans le schéma.

Quand l’application OEMConfig s’installe sur un appareil, elle utilise les paramètres configurés dans l’administrateur EMM pour gérer l’appareil. Les paramètres de l’appareil sont exécutés par l’application OEMConfig au lieu d’un agent MDM créé par l’EMM.

Quand l’OEM ajoute et améliore les fonctionnalités de gestion, l’OEM met également à jour l’application dans Google Play. En tant qu’administrateur, vous bénéficiez de ces nouvelles fonctionnalités et mises à jour (y compris les correctifs) sans devoir attendre que les EMM incluent ces mises à jour.

> [!TIP]
> Vous pouvez utiliser OEMConfig seulement avec des appareils qui prennent en charge cette fonctionnalité et qui ont une application OEMConfig correspondante. Pour plus d’informations, consultez votre OEM.

## <a name="before-you-begin"></a>Avant de commencer

Quand vous utilisez OEMConfig, tenez compte des informations suivantes :

- Intune expose le schéma de l’application OEMConfig pour vous permettre de le configurer. Intune ne valide pas ni ne modifie le schéma fourni par l’application. Ainsi, si le schéma est incorrect ou contient des données inexactes, ces données sont néanmoins envoyées aux appareils. Si vous trouvez un problème qui provient du schéma, contactez l’OEM pour obtenir de l’aide.
- Intune n’influence pas et ne contrôle pas le contenu du schéma d’application. Par exemple, Intune n’a aucun contrôle sur les chaînes, la langue, les actions autorisées, etc. Nous vous recommandons de contacter l’OEM pour plus d’informations sur la gestion de ses appareils avec OEMConfig.
- À tout moment, les OEM peuvent mettre à jour leurs fonctionnalités et schémas pris en charge, et charger une nouvelle application sur Google Play. Intune synchronise toujours la version la plus récente de l’application OEMConfig à partir de Google Play. Intune ne gère pas les versions antérieures du schéma ou de l’application. Si vous rencontrez des conflits de version, nous vous recommandons de contacter l’OEM pour plus d’informations.
- Affectez un profil OEMConfig à un appareil. Si plusieurs profils sont affectés au même appareil, vous pouvez voir apparaître un comportement incohérent. Le modèle OEMConfig ne prend en charge qu’une seule stratégie par appareil.

## <a name="prerequisites"></a>Prérequis

Pour utiliser OEMConfig sur vos appareils, vérifiez que les conditions suivantes sont satisfaites :

- Un appareil Android Entreprise inscrit dans Intune.
- Une application OEMConfig générée par l’OEM et chargée sur Google Play. Si elle ne se trouve pas sur Google Play, contactez l’OEM pour plus d’informations.
- L’administrateur Intune dispose des autorisations de contrôle d’accès en fonction du rôle (RBAC) pour les **Applications mobiles** et **Configurations d’appareil**, et l’autorisation « Lecture » sous **Android for Work**. Ces autorisations sont nécessaires, car les profils OEMConfig utilisent des configurations d’applications managées pour gérer les configurations des appareils.

## <a name="prepare-the-oemconfig-app"></a>Préparer l’application OEMConfig

Vérifiez que l’appareil prend en charge OEMConfig, que l’application OEMConfig correcte est ajoutée à Intune et que l’application est installée sur l’appareil. Pour plus d’informations à ce sujet, contactez l’OEM.

> [!TIP] 
> Les applications OEMConfig sont spécifiques à l’OEM. Par exemple, une application OEMConfig de Sony installée sur un appareil Zebra Technologies ne fait rien.

1. Obtenez l’application OEMConfig auprès du store Google Play géré. La rubrique [Add Managed Google Play apps to Android enterprise devices (Ajouter des applications Google Play gérées aux appareils Android Entreprise)](../apps/apps-add-android-for-work.md) énumère les différentes étapes.
2. Certains OEM peuvent livrer des appareils sur lesquels l’application OEMConfig est préinstallée. Si l’application n’est pas préinstallée, utilisez Intune pour [ajouter et déployer l’application sur les appareils](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Créer un profil OEMConfig

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Plateforme** : sélectionnez **Android Entreprise**.
    - **Type de profil** : sélectionnez **OEMConfig**.

4. Sélectionnez **Créer**.
5. Dans **Informations de base**, entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le nouveau profil.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Application OEMConfig** : choisissez **Sélectionner une application OEMConfig**.

6. Dans **Application associée**, sélectionnez une application OEMConfig existante que vous avez ajoutée précédemment > **Sélectionner**. Veillez à choisir l’application OEMConfig appropriée pour les appareils auxquels vous affectez la stratégie.

    Si vous ne voyez aucune application dans la liste, configurez Google Play géré et obtenez des applications auprès du store Google Play géré. La rubrique [Ajouter des applications de Google Play géré à des appareils Android Entreprise](../apps/apps-add-android-for-work.md) liste les différentes étapes.

    > [!IMPORTANT]
    > Si vous avez ajouté une application OEMConfig et que vous l’avez synchronisée avec Google Play, mais qu’elle n’est pas listée en tant qu’**Application associée**, il peut être nécessaire de contacter Intune pour intégrer l’application. Consultez [Ajout d’une nouvelle application](#supported-oemconfig-apps) (dans cet article).

7. Sélectionnez **Suivant**.
8. Dans **Configurer les paramètres**, sélectionnez le **Concepteur de configuration** ou l’**Éditeur JSON** :

    > [!TIP]
    > Lisez la documentation de l’OEM pour être sûr de configurer correctement les propriétés. Ces propriétés d’application sont incluses par l’OEM, et non pas par Intune. Intune effectue une validation minimale des propriétés ou de ce que vous entrez. Par exemple, si vous entrez `abcd` pour un numéro de port, le profil est enregistré tel quel et est déployé sur vos appareils avec les valeurs que vous configurez. Veillez donc à entrer les informations correctes.

    - **Concepteur de configuration** : quand vous sélectionnez cette option, vous pouvez configurer les propriétés disponibles dans le schéma de l’application.

      - Les menus contextuels du concepteur de configuration indiquent que d’autres options sont disponibles. Par exemple, le menu contextuel peut vous permettre d’ajouter, de supprimer et de réorganiser les paramètres. Ces options sont incluses par l’OEM. Veillez à lire la documentation de l’application OEM pour savoir comment utiliser ces options pour créer des profils.

      - De nombreux paramètres ont des valeurs par défaut fournies par l’OEM. Pour voir s’il existe une valeur par défaut, pointez sur l’icône d’informations en regard du paramètre. Une info-bulle montre les valeurs par défaut pour ce paramètre (le cas échéant), ainsi que des informations détaillées fournies par l’OEM.

      - Cliquez sur **Effacer** pour supprimer un paramètre du profil. Si un paramètre n’est pas dans le profil, sa valeur sur l’appareil n’est pas modifiée quand le profil est appliqué.

      - Si vous créez un bundle vide (non configuré) dans le concepteur de configuration, il est supprimé quand vous passez à l’éditeur JSON.

    - **Éditeur JSON** : quand vous sélectionnez cette option, un éditeur JSON s’ouvre avec un modèle pour le schéma de configuration complet incorporé dans l’application. Dans l’éditeur, personnalisez le modèle avec des valeurs pour les différents paramètres. Si vous utilisez le **Concepteur de configuration** pour modifier vos valeurs, l’éditeur JSON remplace le modèle par les valeurs provenant du concepteur de configuration.

      - Si vous mettez à jour un profil existant, l’éditeur JSON montre les paramètres qui ont été enregistrés en dernier avec le profil.

      - Les schémas OEMConfig peuvent être grands et complexes. Si vous préférez mettre à jour ces paramètres avec un autre éditeur, sélectionnez le bouton **Télécharger le modèle JSON**. Utilisez un éditeur de votre choix pour ajouter vos valeurs de configuration au modèle. Ensuite, copiez et collez votre code JSON mis à jour dans la propriété de l’**Éditeur JSON** .

      - Vous pouvez utiliser l’éditeur JSON pour créer une sauvegarde de votre configuration. Une fois que vous avez configuré vos paramètres, utilisez cette fonctionnalité pour récupérer les paramètres JSON avec vos valeurs. Copiez et collez le code JSON dans un fichier, puis enregistrez-le. Vous disposez maintenant d’un fichier de sauvegarde.

    Toutes les modifications apportées dans le concepteur de configuration sont également effectuées automatiquement dans l’éditeur JSON. De même, toutes les modifications apportées dans l’éditeur JSON sont effectuées automatiquement dans le concepteur de configuration. Si votre entrée contient des valeurs non valides, vous ne pouvez pas basculer entre le concepteur de configuration et l’éditeur JSON tant que vous n’avez pas résolu les problèmes.

9. Sélectionnez **Suivant**.
10. Dans **Balises d’étendue** (facultatif), affectez une balise pour filtrer le profil sur des groupes informatiques spécifiques, par exemple `US-NC IT Team` ou `JohnGlenn_ITDepartment`. Pour plus d’informations sur les balises d’étendue, consultez [Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour l’informatique distribuée](../fundamentals/scope-tags.md).

    Sélectionnez **Suivant**.

11. Dans **Affectations**, sélectionnez les utilisateurs ou les groupes qui recevront votre profil. Attribuez un profil à chaque appareil. Le modèle OEMConfig ne prend en charge qu’une seule stratégie par appareil.

    Pour plus d’informations sur l’affectation de profils, consultez [Affecter des profils d’utilisateur et d’appareil](device-profile-assign.md).

    Sélectionnez **Suivant**.

12. Dans **Vérifier + créer**, passez en revue vos paramètres. Quand vous sélectionnez **Créer**, vos modifications sont enregistrées et le profil est affecté. La stratégie apparaît également dans la liste des profils.

La prochaine fois que l’appareil recherche des mises à jour de configuration, les paramètres spécifiques à l’OEM que vous avez configurés sont appliqués à l’application OEMConfig.

> [!NOTE]
> Le standard OEMConfig n’inclut actuellement pas de rapports d’état. Par défaut, les profils montrent donc un état **En attente**.

## <a name="supported-oemconfig-apps"></a>Applications OEMConfig prises en charge

Par rapport aux applications standard, les applications OEMConfig étendent les privilèges des configurations gérées accordés par Google pour prendre en charge des schémas plus complexes. Intune prend actuellement en charge les applications OEMConfig suivantes :

-----------------

| OEM | ID d’offre groupée | Documentation OEM (si disponible) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Knox Service Plugin Admin Guide](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Zebra OEMConfig overview](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [User Documentation for Datalogic OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink - Barcodes | com.spectralink.barcode.service |  |
| Spectralink - Buttons | com.spectralink.buttons |  |
| Spectralink - Device | com.spectralink.slnkdevicesettings  |  |
| Spectralink - Logging | com.spectralink.slnklogger |  |
| Spectralink - VQO | com.spectralink.slnkvqo |  |
| Seuic | com.seuic.seuicoemconfig | |
| Unitech Electronics | com.unitech.oemconfig | |

-----------------

Si une application OEMConfig existe pour votre appareil, mais qu’elle ne figure pas dans le tableau ci-dessus ou n’apparaît pas dans la console Intune, envoyez un e-mail à `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Les applications OEMConfig doivent être intégrées à Intune avant de pouvoir être configurées avec des profils OEMConfig. Une fois qu’une application est prise en charge, vous n’avez pas besoin de contacter Microsoft pour la configurer dans votre locataire. Suivez simplement les instructions de cette page.
>
> Si vous constatez qu’une application OEMConfig ne se comporte pas correctement, contactez ses développeurs. Intune n’est pas responsable des problèmes techniques liés aux applications OEMConfig individuelles.

## <a name="next-steps"></a>Étapes suivantes

[Superviser l’état du profil](device-profile-monitor.md).
