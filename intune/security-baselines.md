---
title: Utiliser des bases de référence de sécurité dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou configurez des paramètres de sécurité de groupe recommandés pour protéger les données et l’utilisateur sur les appareils à l’aide de Microsoft Intune pour la gestion des appareils mobiles. Activez BitLocker, configurez Windows Defender - Protection avancée contre les menaces, contrôlez Internet Explorer, utilisez SmartScreen, définissez des stratégies de sécurité locales, exigez un mot de passe, bloquez les téléchargements Internet et bien plus encore.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70638228875f1fb063a2ea22dc424c00f3940a30
ms.sourcegitcommit: ef4bc7318449129af3dc8c0154e54a264b7bf4e5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65197625"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>Créer une base de référence de sécurité Windows 10 dans Intune

Les bases de référence de sécurité sont une fonctionnalité en préversion disponible pour les appareils exécutant Windows 10 et versions ultérieures. Cette fonctionnalité inclut de nombreux paramètres pris en charge par Intune que vous pouvez utiliser pour mieux sécuriser et protéger vos utilisateurs et vos appareils. Elle définit également automatiquement ces paramètres sur les valeurs recommandées par les équipes de sécurité. Par exemple, la base de référence active automatiquement BitLocker, requiert automatiquement un mot de passe pour déverrouiller un appareil, désactive automatiquement l’authentification de base et bien plus encore.

Cette fonctionnalité s’applique à :

- Windows 10 1809 et versions ultérieures

> [!NOTE]
> Tandis que les bases de référence de sécurité sont disponibles en préversion, Microsoft ne recommande pas l’utilisation de profils dans un environnement de production, car les bases de référence peuvent changer au cours de la préversion. Quand les bases de référence de la sécurité sont en disponibilité générale, les profils existants ne sont pas convertis en profils les plus récemment pris en charge.

L’objectif de l’utilisation des bases de référence de sécurité consiste à fournir un flux de travail sécurisé de bout en bout lorsque vous travaillez avec Microsoft 365. Vous trouverez ci-dessous certains des avantages :

- Une base de référence de sécurité inclut les meilleures pratiques et des recommandations sur les paramètres qui affectent la sécurité. Intune collabore avec la même équipe de sécurité Windows qui crée les bases de référence de sécurité de la stratégie de groupe. Ces recommandations sont basées sur des conseils et une grande expérience.
- Si vous débutez dans Intune et ne savez pas par où commencer, alors les bases de référence de sécurité vous donnent un avantage. Vous pouvez rapidement créer et déployer un profil sécurisé, en sachant que vous aidez à protéger les données et les ressources de votre organisation.
- Si vous utilisez actuellement la stratégie de groupe, il est beaucoup plus facile de migrer vers Intune pour la gestion avec ces bases de référence. Ces bases de référence sont intégrées en mode natif à Intune et incluent une expérience de gestion moderne.

Les bases de référence de sécurité créent un « profil de configuration » dans Intune. Ce profil inclut tous les paramètres de la base de référence. Vous pouvez ensuite appliquer ou attribuer ce profil à vos utilisateurs, groupes et appareils.

Une fois que le profil est attribué, vous pouvez le surveiller, ainsi que la base de référence. Par exemple, vous pouvez voir quels appareils correspondent à la base de référence ou pas.

Cet article vous montre comment utiliser des bases de référence de sécurité pour créer un profil, attribuer le profil et le surveiller.

Les [bases de référence de sécurité Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) sont une ressource précieuse pour en savoir plus sur cette fonctionnalité. La [Gestion des appareils mobiles](https://docs.microsoft.com/windows/client-management/mdm/) est une ressource précieuse sur la gestion des appareils mobiles, et ce que vous pouvez faire sur les appareils Windows.

## <a name="prerequisites"></a>Prérequis
Pour gérer les bases de référence dans Intune, votre compte doit avoir le rôle intégré [Gestionnaire de stratégie et de profils](role-based-access-control.md#built-in-roles).


## <a name="co-managed-devices"></a>Appareils cogérés

Les bases de référence de sécurité sur les appareils managés par Intune sont similaires aux appareils comanagés avec Configuration Manager. Les appareils comanagés utilisent System Center Configuration Manager et Microsoft Intune pour gérer les appareils Windows 10 simultanément. Cela vous permet de joindre via le cloud votre investissement dans Configuration Manager existant aux avantages d’Intune. [Vue d’ensemble de la cogestion](https://docs.microsoft.com/sccm/comanage/overview) est une excellente ressource si vous utilisez Configuration Manager et souhaitez également bénéficier des avantages du cloud.

Lorsque vous utilisez des appareils comanagés, vous devez basculer la charge de travail **Configuration de l’appareil** (ses paramètres) vers Intune. Vous trouverez des informations supplémentaires dans [Charges de travail de configuration d’appareil](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration).

## <a name="create-the-profile"></a>Créer le profil

1. Dans le [portail Azure](https://portal.azure.com/), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.
2. Sélectionnez **Sécurité des appareils** > **Bases de référence de sécurité (préversion)**. Vous obtenez la liste des bases de référence disponibles. Au fur et à mesure que davantage de bases de référence sont ajoutées, vous les verrez ici :

    ![Afficher la liste des bases de référence de sécurité actuellement disponibles dans Intune](./media/security-baselines/available-baselines.png)

3. Sélectionnez la base de référence que vous souhaitez utiliser > **Créer un profil**.
4. Dans **Informations de base**, entrez les propriétés suivantes :

    - **Nom** : Entrez un nom pour votre profil de base de référence de sécurité. Par exemple, entrez `pilot Windows 10 MDM baseline - Oct 2018`.
    - **Description** : Entrez du texte qui décrit ce que fait cette base de référence. La description vous permet d’entrer n’importe quel texte. Cela est facultatif, mais sans aucun doute recommandé.

5. Développez **Paramètres**. Dans la liste, vous voyez tous les paramètres de cette base de référence de sécurité, ainsi que la valeur sur laquelle le paramètre est automatiquement défini. Les paramètres et leurs valeurs sont recommandés et peuvent être modifiés.

    ![Développer pour afficher tous les paramètres de cette base de référence de sécurité dans Intune](./media/security-baselines/sample-list-of-settings.png)

    Développez certains des paramètres pour vérifier leurs valeurs. Par exemple, développez **Windows Defender**. Notez certains des paramètres, ainsi que la valeur sur laquelle ils sont définis :

    ![Consulter la valeur de certains paramètres Windows Defender dans Intune](./media/security-baselines/expand-windows-defender.png)

6. **Créez** le profil. 
7. Sélectionnez **Profils**. Votre profil est créé et apparaît dans la liste. Toutefois, il ne fait rien pour le moment. Ensuite, attribuez le profil.

## <a name="assign-the-profile"></a>Attribuer le profil

Une fois créé, le profil est prêt à être attribué à vos utilisateurs, appareils et groupes. Une fois attribué, le profil et ses paramètres sont appliqués aux utilisateurs, appareils et groupes de votre choix.

1. Dans Intune, sélectionnez **Bases de référence de sécurité** > choisir une base de référence > **Profils**.
2. Sélectionnez votre profil > **Attributions**.

    ![Choisissez votre profil de base de référence de sécurité dans Intune, puis cliquez sur Attributions pour déployer le profil](./media/security-baselines/assignments.png)

3. Dans l’onglet **Inclure**, ajoutez les groupes, utilisateurs ou appareils auxquels vous souhaitez appliquer cette stratégie.

    > [!TIP]
    > Notez que vous pouvez également **exclure** des groupes. Si vous appliquez une stratégie à **Tous les utilisateurs**, envisagez d’exclure les groupes d’administration. En cas de problème, vous ne voulez sans doute pas que vous ou vos administrateurs soyez verrouillés.

4. **Enregistrez** les changements apportés.

Dès que vous enregistrez, le profil est envoyé (push) aux appareils lorsque ceux-ci se connectent à Intune. Par conséquent, cela peut se produire immédiatement.

## <a name="available-security-baselines"></a>Bases de référence de la sécurité disponibles  

Les bases de référence de la sécurité suivantes sont disponibles pour une utilisation avec Intune.
- **Préversion : Base de référence de la sécurité MDM**
  - Version : [Octobre 2018](security-baseline-settings-windows.md)

## <a name="q--a"></a>Questions et réponses

#### <a name="why-these-settings"></a>Pourquoi ces paramètres ?

L’équipe de sécurité Microsoft travaille directement avec les développeurs Windows et de la communauté de sécurité depuis des années pour créer ces recommandations. Les paramètres de cette base de référence sont considérées comme les options de configuration liées à la sécurité les plus pertinentes. Dans chaque nouvelle build de Windows, l’équipe ajuste ses recommandations en fonction des nouvelles fonctionnalités.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Existe-t-il une différence dans les recommandations pour les bases de référence de sécurité Windows pour la stratégie de groupe et Intune ?

La même équipe de sécurité Microsoft a choisi et organisé les paramètres pour chaque base de référence. Intune inclut tous les paramètres pertinents dans la base de référence de sécurité Intune. Il existe certains paramètres dans la base de référence de la stratégie de groupe qui sont spécifiques à un contrôleur de domaine local. Ces paramètres sont exclus des recommandations d’Intune. Tous les autres paramètres sont les mêmes.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Les bases de référence de sécurité d’Intune sont-elles conformes à CIS ou NSIT ?

À strictement parler, non. L’équipe de sécurité Microsoft consulte des organisations, comme CIS, pour compiler ses recommandations. Toutefois, il n’existe pas de correspondance directe entre les bases de référence « conformes à CIS » et les bases de référence Microsoft.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Quelles sont les certifications des bases de référence de sécurité Microsoft ? 

- Microsoft continue de publier des bases de référence de sécurité pour les stratégies de groupe (GPO) et la [Boîte à outils de conformité de la sécurité](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), comme depuis de nombreuses années. Ces bases de référence sont utilisées par de nombreuses organisations. Les recommandations contenues dans ces bases de référence sont issues de l’engagement de l’équipe de sécurité Microsoft avec des clients d’entreprise et des agences externes, notamment le DOD (Department of Defense), le NIST (National Institute of Standards et Technology) et bien plus encore. Nous partageons nos recommandations et bases de référence avec ces organisations. Ces organisations ont également leurs propres recommandations qui reflètent celles de Microsoft. Alors que la gestion des appareils mobiles continue de croître dans le cloud, Microsoft a créé des recommandations de gestion des appareils mobiles équivalentes à ces bases de référence de la stratégie de groupe. Ces bases de référence supplémentaires sont intégrées à Microsoft Intune et incluent des rapports de conformité sur les utilisateurs, groupes et appareils qui respectent (ou pas) la base de référence.

- De nombreux clients utilisent les recommandations de référence de base d’Intune comme point de départ, puis la personnalisent pour répondre à leur besoins informatiques et de sécurité. La **MDM Security Baseline** (Base de référence de sécurité MDM) Windows 10 RS5 de Microsoft est la première base de référence à être publiée. Cette base de référence est conçue sous la forme d’une infrastructure générique qui permet aux clients d’importer les autres bases de référence de sécurité basées sur CIS, NIST et autres normes. Actuellement, elle est disponible pour Windows et bientôt pour iOS et Android.

- La migration à partir de stratégies de groupe Active Directory locales vers une solution cloud pure à l’aide d’Azure Active Directory (AD) avec Microsoft Intune est un parcours. Pour vous aider, il existe des GPO publiés pour les appareils joints à Azure AD et AD hybrides. Ces appareils peuvent obtenir les paramètres de gestion des appareils mobiles à partir du cloud (Intune) et les paramètres de stratégie de groupe à partir de contrôleurs de domaine locaux.

## <a name="next-steps"></a>Étapes suivantes
- Consultez les [Paramètres de base de référence de la sécurité Windows](security-baseline-settings-windows.md) pris en charge par Intune.  
- Vérifiez l’état et surveillez [la base de référence et le profil](security-baselines-monitor.md).
