---
title: Utiliser OEMConfig sur les appareils Android Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez Microsoft Intune pour gérer et utiliser des appareils exécutant Android Enterprise avec OEMConfig. Consultez toutes les étapes, y compris une vue d’ensemble, consultez les conditions préalables, créez le profil de configuration dans Intune et consultez la liste des applications OEMConfig prises en charge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
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
ms.openlocfilehash: e8747f3dfa9169a4f1f2de9dcf45db0f5cccadd1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73756760"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Utiliser et gérer des appareils Android Enterprise avec OEMConfig dans Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Dans Microsoft Intune, vous pouvez utiliser OEMConfig pour ajouter, créer et personnaliser des paramètres spécifiques aux OEM pour les appareils Android Enterprise. OEMConfig est généralement utilisé pour configurer les paramètres qui ne sont pas intégrés à Intune. Différents fabricants d’ordinateurs OEM (Original Equipment Manufacturers) incluent des paramètres différents. Les paramètres disponibles dépendent de ce que le fabricant d’ordinateurs OEM comprend dans leur application OEMConfig.

Cette fonctionnalité s’applique à :  

- Android Entreprise

Cet article décrit OEMConfig, répertorie les conditions préalables, montre comment créer un profil de configuration et répertorie les applications OEMConfig prises en charge dans Intune.

## <a name="overview"></a>Vue d’ensemble

Les stratégies OEMConfig sont un type spécial de stratégie de configuration d’appareil similaire à la [stratégie de configuration des applications](../apps/app-configuration-policies-overview.md). OEMConfig est une norme définie par Google qui tire parti de la configuration des applications dans Android pour envoyer des paramètres d’appareil à des applications écrites par des OEM (fabricants d’équipements originaux). Cette norme permet aux fabricants d’ordinateurs OEM et EMMs (gestion de la mobilité d’entreprise) de créer et de prendre en charge des fonctionnalités OEM de manière standardisée. [En savoir plus sur OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Historiquement, EMMs, comme Intune, crée manuellement la prise en charge des fonctionnalités OEM après qu’elles ont été introduites par l’OEM. Cette approche se traduit par des efforts dupliqués et une adoption lente.

Avec OEMConfig, un OEM crée un schéma qui définit les fonctionnalités de gestion spécifiques aux fabricants d’ordinateurs OEM. L’OEM incorpore le schéma dans une application, puis place cette application sur Google Play. Le modèle EMM lit le schéma à partir de l’application et expose le schéma dans la console administrateur EMM. La console permet aux administrateurs Intune de configurer les paramètres dans le schéma.

Lorsque l’application OEMConfig s’installe sur un appareil, elle utilise les paramètres configurés dans la console administrateur EMM pour gérer l’appareil. Les paramètres sur l’appareil sont exécutés par l’application OEMConfig, au lieu d’un agent MDM généré par le EMM.

Lorsque l’OEM ajoute et améliore les fonctionnalités de gestion, l’OEM met également à jour l’application dans Google Play. En tant qu’administrateur, vous bénéficiez de ces nouvelles fonctionnalités et mises à jour (y compris les correctifs) sans attendre que EMMs inclue ces mises à jour.

> [!TIP]
> Vous pouvez uniquement utiliser OEMConfig avec des appareils qui prennent en charge cette fonctionnalité et qui ont une application OEMConfig correspondante. Pour plus d’informations, consultez votre fabricant OEM.

## <a name="before-you-begin"></a>Avant de commencer

Lorsque vous utilisez OEMConfig, tenez compte des informations suivantes :

- Intune expose le schéma de l’application OEMConfig afin que vous puissiez le configurer. Intune ne valide pas ou ne modifie pas le schéma fourni par l’application. Par conséquent, si le schéma est incorrect ou contient des données inexactes, ces données sont toujours envoyées aux appareils. Si vous trouvez un problème qui provient du schéma, contactez le fabricant d’ordinateurs OEM pour obtenir de l’aide.
- Intune n’influence pas et ne contrôle pas le contenu du schéma d’application. Par exemple, Intune n’a aucun contrôle sur les chaînes, la langue, les actions autorisées et ainsi de suite. Nous vous recommandons de contacter le fabricant OEM pour obtenir des détails et les meilleures pratiques pour la gestion de leurs appareils avec OEMConfig.
- À tout moment, les fabricants OEM peuvent mettre à jour leurs fonctionnalités et schémas pris en charge, et charger une nouvelle application sur Google Play. Intune synchronise toujours la version la plus récente de l’application OEMConfig à partir de Google Play. Intune ne gère pas les versions antérieures du schéma ou de l’application. Si vous rencontrez des conflits de version, nous vous recommandons de contacter le fabricant d’ordinateurs OEM pour plus d’informations.
- Assigner un profil OEMConfig à un appareil. Si plusieurs profils sont affectés au même périphérique, vous pouvez constater un comportement incohérent. Le modèle OEMConfig prend uniquement en charge une seule stratégie par appareil.

## <a name="prerequisites"></a>Prérequis

Pour utiliser OEMConfig sur vos appareils, assurez-vous de disposer des éléments suivants :

- Un appareil Android Enterprise inscrit dans Intune.
- Une application OEMConfig générée par l’OEM et chargée sur Google Play. Si elle ne se trouve pas sur Google Play, contactez le fabricant d’ordinateurs OEM pour plus d’informations.
- L’administrateur Intune dispose des autorisations de contrôle d’accès en fonction du rôle (RBAC) pour les **applications mobiles**, les **configurations des appareils**et l’autorisation de « lecture » sous **Android for Work**. Ces autorisations sont nécessaires car les profils OEMConfig utilisent des configurations d’applications gérées pour gérer les configurations des appareils.

## <a name="prepare-the-oemconfig-app"></a>Préparer l’application OEMConfig

Assurez-vous que l’appareil prend en charge OEMConfig, que l’application OEMConfig correcte est ajoutée à Intune et que l’application est installée sur l’appareil. Pour plus d’informations, contactez le fabricant d’ordinateurs OEM.

> [!TIP] 
> Les applications OEMConfig sont spécifiques au fabricant d’ordinateurs OEM. Par exemple, une application Sony OEMConfig installée sur un appareil rayures technologies ne fait rien.

1. Récupérez l’application OEMConfig à partir de la Google Play Store gérée. La rubrique [Add Managed Google Play apps to Android enterprise devices (Ajouter des applications Google Play gérées aux appareils Android Entreprise)](../apps/apps-add-android-for-work.md) énumère les différentes étapes.
2. Certains fabricants d’ordinateurs OEM peuvent envoyer des appareils sur lesquels l’application OEMConfig est pré-installée. Si l’application n’est pas préinstallée, utilisez Intune pour [Ajouter et déployer l’application sur les appareils](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Créer un profil OEMConfig

1. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez les **appareils** > **profils de configuration** > créer un **Profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : attribuez un nom descriptif au nouveau profil.
    - **Description :** entrez une description pour le profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : sélectionnez **Android Entreprise**.
    - **Type de profil**: sélectionnez **OEMConfig**.

4. Sélectionnez **application associée**, sélectionnez une application OEMConfig existante que vous avez ajoutée précédemment > **OK**. Veillez à choisir l’application OEMConfig appropriée pour les appareils auxquels vous affectez la stratégie.

    Si vous ne voyez aucune application dans la liste, configurez les Google Play gérés et obtenez des applications à partir du magasin de Google Play géré. La rubrique [Add Managed Google Play apps to Android enterprise devices (Ajouter des applications Google Play gérées aux appareils Android Entreprise)](../apps/apps-add-android-for-work.md) énumère les différentes étapes.

    > [!IMPORTANT]
    > Si vous avez ajouté une application OEMConfig et que vous l’avez synchronisée pour Google Play, mais qu’elle n’est pas listée en tant qu' **application associée**, vous devrez peut-être contacter Intune pour intégrer l’application. Consultez [Ajout d’une nouvelle application](#supported-oemconfig-apps) (dans cet article).

5. Dans **configurer les paramètres avec**, choisissez d’utiliser le **Concepteur de configuration** ou l' **éditeur JSON**:

    > [!TIP]
    > Lisez la documentation OEM pour vérifier que vous configurez correctement les propriétés. Ces propriétés d’application sont incluses par l’OEM, et non par Intune. Intune effectue une validation minimale des propriétés, ou ce que vous entrez. Par exemple, si vous entrez `abcd` pour un numéro de port, le profil est enregistré tel quel et est déployé sur vos appareils avec les valeurs que vous configurez. Veillez à entrer les informations correctes.

    - **Concepteur de configuration**: lorsque vous sélectionnez cette option, vous pouvez configurer les propriétés disponibles dans le schéma de l’application.

      - Les menus contextuels du concepteur de configuration indiquent que d’autres options sont disponibles. Par exemple, le menu contextuel peut vous permettre d’ajouter, de supprimer et de réorganiser les paramètres. Ces options sont incluses par l’OEM. Veillez à lire la documentation de l’application OEM pour savoir comment utiliser ces options pour créer des profils.

      - De nombreux paramètres ont des valeurs par défaut fournies par l’OEM. Pour voir s’il existe une valeur par défaut, pointez sur l’icône d’informations en regard du paramètre. Une info-bulle affiche les valeurs par défaut pour ce paramètre (le cas échéant), ainsi que les détails fournis par l’OEM.

      - Cliquez sur **Effacer** pour supprimer un paramètre du profil. Si un paramètre n’est pas dans le profil, sa valeur sur l’appareil n’est pas modifiée lorsque le profil est appliqué.

      - Si vous créez un bundle vide (non configuré) dans le concepteur de configuration, il est supprimé lors du basculement vers l’éditeur JSON.

    - **Éditeur JSON**: lorsque vous sélectionnez cette option, un éditeur JSON s’ouvre avec un modèle pour le schéma de configuration complet incorporé dans l’application. Dans l’éditeur, personnalisez le modèle avec des valeurs pour les différents paramètres. Si vous utilisez le **Concepteur de configuration** pour modifier vos valeurs, l’éditeur JSON remplace le modèle par des valeurs du concepteur de configuration.

      - Si vous mettez à jour un profil existant, l’éditeur JSON affiche les paramètres qui ont été enregistrés avec le profil.

      - Les schémas OEMConfig peuvent être volumineux et complexes. Si vous préférez mettre à jour ces paramètres à l’aide d’un autre éditeur, sélectionnez le bouton **Télécharger le modèle JSON** . Utilisez un éditeur de votre choix pour ajouter vos valeurs de configuration au modèle. Puis, copiez et collez votre code JSON mis à jour dans la propriété de l' **éditeur JSON** .

      - Vous pouvez utiliser l’éditeur JSON pour créer une sauvegarde de votre configuration. Une fois que vous avez configuré vos paramètres, utilisez cette fonctionnalité pour récupérer les paramètres JSON avec vos valeurs. Copiez et collez le code JSON dans un fichier, puis enregistrez-le. Vous disposez maintenant d’un fichier de sauvegarde.

    Toutes les modifications apportées dans le concepteur de configuration sont également effectuées automatiquement dans l’éditeur JSON. De même, toutes les modifications apportées à l’éditeur JSON sont effectuées automatiquement dans le concepteur de configuration. Si votre entrée contient des valeurs non valides, vous ne pouvez pas basculer entre le concepteur de configuration et l’éditeur JSON tant que vous n’avez pas résolu les problèmes.

6. Sélectionnez **OK** > **Ajouter** pour enregistrer vos changements. La stratégie est créée et apparaît dans la liste.

[Affectez-le](device-profile-assign.md) et [supervisez son état](device-profile-monitor.md).

 > [!NOTE]
 > Attribuez un profil à chaque appareil. Le modèle OEMConfig prend uniquement en charge une seule stratégie par appareil.

La prochaine fois que l’appareil recherchera des mises à jour de configuration, les paramètres spécifiques à l’OEM que vous avez configurés sont appliqués à l’application OEMConfig.

> [!NOTE]
> Le standard OEMConfig n’inclut pas de rapports d’État. Par défaut, les profils affichent un état d' **attente** .

## <a name="supported-oemconfig-apps"></a>Applications OEMConfig prises en charge

Par rapport aux applications standard, les applications OEMConfig étendent les privilèges des configurations gérées accordées par Google pour prendre en charge des schémas plus complexes. Intune prend actuellement en charge les applications OEMConfig suivantes :

-----------------

| OEM | ID d’offre groupée | Documentation OEM (si disponible) |
| --- | --- | ---|
| Samsung | com. Samsung. Android. Knox. KPU | [Guide d’administration du plug-in de service Knox](https://docs.samsungknox.com/knox-service-plugin/admin-guide/welcome.htm) |
| Technologies rayures | com. rayures. oemconfig. Common | [Présentation de rayures OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. Datalogic. oemconfig | [Documentation utilisateur pour Datalogic OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |
| Kyocera | JP. Kyocera. enterprisedeviceconfig |  |

-----------------

Si une application OEMConfig existe pour votre appareil, mais qu’elle ne figure pas dans le tableau ci-dessus ou n’apparaît pas dans la console Intune, envoyez un e-mail à `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> Les applications OEMConfig doivent être intégrées à Intune avant de pouvoir être configurées avec des profils OEMConfig. Une fois qu’une application est prise en charge, vous n’avez pas besoin de contacter Microsoft pour la configurer dans votre locataire. Suivez simplement les instructions de cette page.

## <a name="next-steps"></a>Étapes suivantes

- [Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
