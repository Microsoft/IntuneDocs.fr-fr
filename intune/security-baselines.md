---
title: Utiliser des bases de référence de sécurité dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez les paramètres de sécurité Windows recommandés pour protéger les données et l’utilisateur sur les appareils avec Microsoft Intune pour la gestion des périphériques mobiles. Activez le chiffrement, configurez Microsoft Defender Advanced Threat Protection, contrôlez Internet Explorer, définissez des stratégies de sécurité locales, exigez un mot de passe, bloquez les téléchargements Internet et bien plus encore.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26ad26fedc6fe0e44328f5c77fa5f093c1230a28
ms.sourcegitcommit: 6f84e880411a202c5500eb460779b7ef63a7f430
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68978504"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Utiliser les bases de référence de la sécurité pour configurer des appareils Windows 10 dans Intune

Utilisez les bases de référence de la sécurité Intune pour sécuriser et protéger vos utilisateurs et les appareils. Les bases de référence de la sécurité représentent des groupes préconfigurés de paramètres Windows qui vous aident à appliquer un groupe connu de paramètres et de valeurs par défaut, recommandé par les équipes de sécurité correspondantes. Lorsque vous créez un profil de base de référence de la sécurité dans Intune, vous créez un profil de *configuration d’appareil*.

Cette fonctionnalité s’applique à :

- Windows 10 1809 et versions ultérieures

Vous déployez des lignes de base de référence de sécurité sur des groupes d’utilisateurs ou d’appareils dans Intune, et les paramètres s’appliquent aux appareils qui exécutent Windows 10 ou version ultérieure. Par exemple, la *base de référence de sécurité MDM* active automatiquement BitLocker pour les lecteurs amovibles, requiert automatiquement un mot de passe pour déverrouiller un appareil, désactive automatiquement l’authentification de base et bien plus encore. Lorsque la valeur par défaut ne fonctionne pas pour votre environnement, personnalisez la base de référence pour appliquer les paramètres nécessaires.  

Des types de base de référence distincts peuvent inclure les mêmes paramètres mais utiliser différentes valeurs par défaut pour ces paramètres. Il est important de comprendre les valeurs par défaut dans les bases de référence que vous choisissez d’utiliser, puis de modifier chaque ligne de base pour l’ajuster aux besoins de votre organisation.  

> [!NOTE]
> Microsoft déconseille l’utilisation de préversions de bases de référence de sécurité dans un environnement de production. Les paramètres d’une base de référence en préversion peuvent changer au cours de la préversion. 

Les bases de référence de sécurité peuvent vous aider à fournir un flux de travail sécurisé de bout en bout lorsque vous travaillez avec Microsoft 365. Vous trouverez ci-dessous certains des avantages :

- Une base de référence de sécurité inclut les meilleures pratiques et des recommandations sur les paramètres qui affectent la sécurité. Intune collabore avec la même équipe de sécurité Windows qui crée les bases de référence de sécurité de la stratégie de groupe. Ces recommandations sont basées sur des conseils et une grande expérience.
- Si vous débutez dans Intune et ne savez pas par où commencer, alors les bases de référence de sécurité vous donnent un avantage. Vous pouvez rapidement créer et déployer un profil sécurisé, en sachant que vous aidez à protéger les données et les ressources de votre organisation.
- Si vous utilisez actuellement la stratégie de groupe, il est beaucoup plus facile de migrer vers Intune pour la gestion avec ces bases de référence. Ces bases de référence sont intégrées en mode natif à Intune et incluent une expérience de gestion moderne.



Les [bases de référence de sécurité Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) sont une ressource précieuse pour en savoir plus sur cette fonctionnalité. La [Gestion des appareils mobiles](https://docs.microsoft.com/windows/client-management/mdm/) est une ressource précieuse sur la gestion des appareils mobiles, et ce que vous pouvez faire sur les appareils Windows.

## <a name="about-baseline-versions-and-instances"></a>Versions et instances des bases de référence

Chaque nouvelle instance d’une version de base de référence peut ajouter ou supprimer des paramètres ou introduire d'autres modifications. Par exemple, à mesure que de nouveaux paramètres Windows 10 sont disponibles avec les nouvelles versions de Windows 10, la base de référence de sécurité MDM peut recevoir une nouvelle instance de version qui inclut les derniers paramètres.  

Dans la console Intune, la vignette de chaque base de référence indique le nom de la référence de base et les informations de base sur cette base de référence. Les informations incluent le nombre de profils qui utilisent ce type de base de référence, le nombre d'instances distinctes (versions) du type de base de référence disponibles et une date de *Dernière publication* qui identifie quand ce modèle de base de référence a été ajouté à votre abonné. L’exemple suivant montre la vignette d’une base de référence de sécurité MDM bien utilisée :  

![Vignette de la base de référence](./media/security-baselines/baseline-tile.png)

Pour afficher plus d’informations sur les versions de base de référence que vous utilisez, sélectionnez une vignette de base de référence pour ouvrir son volet *Vue d'ensemble*, puis sélectionnez **Versions**. Intune affiche des détails sur les versions de la base de référence utilisée par vos profils. Dans le volet Versions, vous pouvez sélectionner une version unique pour afficher plus de détails sur les profils qui utilisent cette version. Vous pouvez également sélectionner deux versions différentes, puis choisir **Comparer les bases de référence** pour télécharger un fichier CSV qui détaille ces différences.  

![Comparer les bases de référence](./media/security-baselines/compare-baselines.png)

Lorsque vous créez un *profil* de base de référence de sécurité, ce profil utilise automatiquement l’instance de base de référence de sécurité la plus récente.  Vous pouvez continuer à utiliser et à modifier les profils que vous avez créés précédemment et qui utilisent une instance de version de base de référence antérieure, y compris des bases de référence créées à l’aide d’une préversion. 

Vous pouvez choisir [de modifier la version](#change-the-baseline-version-for-a-profile) d’une base de référence utilisée avec un profil donné. Ainsi, à la sortie d’une nouvelle version, vous n’êtes pas obligé de créer un profil de base pour tirer parti de cette nouvelle version. Au lieu de cela, lorsque vous êtes prêt, vous pouvez sélectionner un profil de base puis utiliser l’option intégrée pour remplacer la version de l’instance pour ce profil par une nouvelle version.  

## <a name="available-security-baselines"></a>Bases de référence de la sécurité disponibles 

Les instances de bases de référence de sécurité suivantes sont disponibles pour une utilisation avec Intune. Utilisez les liens pour afficher les paramètres de l’instance la plus récente de chaque base de référence. 

- **Base de référence de la sécurité MDM**
  - [Base de référence de la sécurité MDM pour mai 2019](security-baseline-settings-mdm.md)
  - [Préversion : Base de référence de la sécurité MDM pour octobre 2018](security-baseline-settings-mdm-archive.md)

- **Base de référence Microsoft Defender ATP**  
  *(Pour utiliser cette base de référence, votre environnement doit répondre à la configuration requise pour l’utilisation de [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites))* .
  - [Préversion : Base de référence Microsoft Defender ATP](security-baseline-settings-defender-atp.md)  

  > [!NOTE]
  > La base de référence de la sécurité Microsoft Defender ATP a été optimisée pour les appareils physiques et n’est actuellement pas recommandée pour une utilisation sur des machines virtuelles ou des points de terminaison VDI. Certains paramètres de la base de référence peuvent impacter les sessions interactives à distance sur les environnements virtualisés.  Pour plus d’informations, consultez [Améliorer la conformité à la base de référence de la sécurité de Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) dans la documentation Windows.

Vous pouvez continuer à utiliser et à modifier des profils que vous avez créés précédemment en fonction d’une préversion de modèle, même lorsque cette préversion n’est plus disponible pour la création de nouveaux profils. 

## <a name="manage-baselines"></a>Gérer les bases de référence  

Les tâches courantes lorsque vous travaillez avec des bases de référence de sécurité sont notamment les suivantes :
- [Créer un profil](#create-the-profile) : pour configurer les paramètres que vous souhaitez utiliser, puis affectez la base de référence à des groupes.
- [Modifier la version](#change-the-baseline-version-for-a-profile) : modifiez la version de la base de référence utilisée par un profil.
- [Supprimer une attribution de base de référence](#remove-a-security-baseline-assignment) : découvrez ce qui se passe lorsque vous cessez de gérer les paramètres avec une base de référence de sécurité.


### <a name="prerequisites"></a>Prérequis
- Pour gérer les bases de référence dans Intune, votre compte doit avoir le rôle intégré [Gestionnaire de stratégie et de profils](role-based-access-control.md#built-in-roles).

- L’utilisation de certaines bases de référence peut nécessiter un abonnement actif à des services supplémentaires tels que Microsoft Defender ATP.  


### <a name="create-the-profile"></a>Créer le profil

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), puis sélectionnez **Sécurité des appareils** > **Bases de référence de sécurité** pour afficher la liste des bases de référence disponibles.


    ![Sélectionnez une base de référence de sécurité pour configurer](./media/security-baselines/available-baselines.png)

2. Sélectionnez la base de référence que vous souhaitez utiliser, puis sélectionnez **Créer un profil**.  

3. Dans l'onglet **Notions de base**, spécifiez les propriétés suivantes :

    - **Nom** : Entrez un nom pour votre profil de base de référence de sécurité. Par exemple, entrez *Profil standard pour Defender ATP*.

    - **Description** : Entrez du texte qui décrit ce que fait cette base de référence. La description vous permet d’entrer n’importe quel texte. Elle est facultative mais recommandée.  

   Sélectionnez **Suivant** pour passer à l’onglet suivant. Lorsque vous accédez à un nouvel onglet, vous pouvez sélectionner le nom de l’onglet pour revenir à un onglet affiché précédemment.  

4. Sous l’onglet Paramètres de configuration, affichez les groupes de **paramètres** disponibles dans la base de référence que vous avez sélectionnée. Vous pouvez développer un groupe pour afficher les paramètres de celui-ci ainsi que les valeurs par défaut pour ces paramètres dans la base de référence. Pour rechercher des paramètres spécifiques :
   - Sélectionnez un groupe à développer et passez en revue les paramètres disponibles.  
   - Utilisez la barre de *recherche* et spécifiez des mots clés qui filtrent la vue afin d’afficher uniquement les groupes qui contiennent vos critères de recherche.  
 
   Chaque paramètre d’une base de référence propose une configuration par défaut pour cette version de base de référence. Reconfigurez les paramètres de valeurs par défaut pour répondre aux besoins de votre entreprise. Différentes bases de référence peuvent contenir le même paramètre. Utilisez par conséquent différentes valeurs par défaut pour le paramètre, selon l’objectif de la base de référence. 

    ![Développez un groupe pour afficher ses paramètres](./media/security-baselines/sample-list-of-settings.png)

5. Dans l’onglet **Balises d’étendue**, sélectionnez **Sélectionner les balises d’étendue** pour ouvrir l’onglet *Sélectionner des balises* afin d’attribuer des balises d’étendue au profil. 

6. Dans l’onglet **Attributions**, sélectionnez **Sélectionner les groupes à inclure**, puis attribuez la base de référence à un ou plusieurs groupes. Utilisez le paramètre **Sélectionner des groupes à inclure** pour affiner l’attribution.  

   ![Attribuer un profil](./media/security-baselines/assignments.png)
  
7. Lorsque vous êtes prêt à déployer la base de référence, ouvrez l’onglet **Réviser + créer** et consultez les détails de la base de référence. Sélectionnez **Créer** pour enregistrer et déployer le profil.  

   Dès que vous créez le profil, celui-ci est placé dans le groupe attribué et peut-être aussitôt appliqué.

   > [!TIP]  
   > Si vous enregistrez un profil sans l'attribuer au préalable à des groupes, vous pouvez le modifier ultérieurement.  

   ![Réviser la base de référence](./media/security-baselines/review.png) 

  
8. Après avoir créé un profil, modifiez-le en accédant à **Sécurité des appareils** > **Bases de référence de la sécurité**, sélectionnez le type de base de référence que vous avez configuré, puis sélectionnez **Profils**. Sélectionnez le profil dans la liste des profils disponibles, puis choisissez **Propriétés**. Vous pouvez modifier les paramètres de tous les onglets de configuration disponibles, puis sélectionnez **Réviser + enregistrer** pour valider vos modifications.  

### <a name="change-the-baseline-version-for-a-profile"></a>Modifier la version de base de référence pour un profil  

Vous pouvez modifier la version de l’instance de base de référence utilisée avec un profil.  Lorsque vous modifiez la version, vous sélectionnez une instance disponible de la même base de référence. Vous ne pouvez pas passer d'un type de base de référence à l’autre, par exemple changer un profil d'une base de référence pour Defender ATP à une base de référence de sécurité MDM. 

Lors de la configuration d'une modification de la version de la base de référence, vous pouvez télécharger un fichier CSV qui répertorie les différences entre les deux versions de base de référence concernées. Vous pouvez également choisir de conserver toutes vos personnalisations de la version d’origine de la base de référence ou d’implémenter la nouvelle version à l’aide de toutes ses valeurs par défaut. Vous ne pouvez pas apporter de modifications à des paramètres individuels lorsque vous modifiez la version d’une base de référence pour un profil. 

Lors de l’enregistrement, une fois la conversion terminée, la base de référence est immédiatement redéployée vers les groupes attribués.  

**Pendant la conversion** :
- Les nouveaux paramètres qui ne figuraient pas dans la version d’origine que vous utilisiez sont ajoutés et configurés pour utiliser les valeurs par défaut.  

- Les paramètres qui ne figurent pas dans la nouvelle version de la base de référence que vous sélectionnez sont supprimés et ne sont plus appliqués par ce profil de base de référence de sécurité.  

  Lorsqu'un paramètre n'est plus géré par un profil de base de référence, ce paramètre n'est pas réinitialisé sur l'appareil. Au lieu de cela, le réglage sur l'appareil reste réglé sur sa dernière configuration jusqu'à ce qu'un autre processus gère le réglage pour le modifier. Parmi les exemples de processus pouvant modifier un paramètre après la fin de sa gestion, citons un profil de base de référence différent, un paramètre de stratégie de groupe ou une configuration manuelle effectuée sur l'appareil. 

#### <a name="to-change-the-baseline-version-for-a-profile"></a>Pour modifier la version de base de référence pour un profil  

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), puis sélectionnez **Sécurité des appareils** > **Bases de référence de sécurité**, puis sélectionnez la vignette du type de base de référence contenant le profil que vous souhaitez modifier.  

2. Sélectionnez ensuite **Profils**, cochez la case correspondant au profil que vous souhaitez modifier, puis choisissez **Modifier la version**.  

   ![sélectionner une base de référence](./media/security-baselines/select-baseline.png)  

3. Dans le volet **Modifier la version**, utilisez la liste déroulante **Sélectionner une base de référence de sécurité à mettre à jour**, puis sélectionnez l'instance de version que vous souhaitez utiliser.  

   ![sélectionner une version](./media/security-baselines/select-instance.png)  
   
4. Sélectionnez **Review update** (Examiner la mise à jour) pour télécharger un fichier CSV qui affiche la différence entre la version actuelle du profil et la nouvelle version que vous avez sélectionnée. Consultez ce fichier afin de comprendre quels paramètres sont nouveaux ou ont été supprimés et quelles sont les valeurs par défaut de ces paramètres dans le profil mis à jour.  

   Lorsque vous êtes prêt, passez à l’étape suivante.  

5. Choisissez l'une des deux options pour le paramètre **Sélectionner une méthode pour mettre à jour le profil** : 
   - **Accept baseline changes but keep my existing setting customizations** (Accepter les changements de base de référence mais conserver mes personnalisations de paramètres existantes) : cette option conserve les personnalisations que vous avez apportées au profil de la base de référence et les applique à la nouvelle version que vous avez sélectionnée.
   - **Accept baseline changes and discard existing setting customizations** (Accepter les changements de base de référence et ignorer les personnalisations de paramètres existantes) : cette option écrase complètement votre profil original. Le profil mis à jour utilisera les valeurs par défaut pour tous les paramètres.  

6. Sélectionnez **Envoyer**. Le profil est mis à jour avec la version de base de référence sélectionnée, et une fois la conversion terminée, la base de référence est immédiatement redéployée vers les groupes attribués.

### <a name="remove-a-security-baseline-assignment"></a>Supprimer une attribution de base de référence de sécurité
Lorsqu'un paramètre de base de référence de sécurité ne s'applique plus à un appareil ou que les paramètres d'une base de référence sont définis sur *Non configuré*, ces paramètres sur un appareil ne sont pas rétablis avec une configuration prégérée. Au lieu de cela, les paramètres précédemment gérés sur l'appareil conservent leurs dernières configurations reçues depuis la base de référence, jusqu'à ce qu'un autre processus mette à jour ces paramètres sur l’appareil.  

Parmi les autres processus susceptibles de modifier ultérieurement les paramètres de l’appareil, nous pouvons citer une base de référence de sécurité différente ou nouvelle, un profil de configuration de l’appareil, des configurations de stratégie de groupe ou la modification manuelle des paramètres sur l’appareil.  

## <a name="co-managed-devices"></a>Appareils cogérés

Les bases de référence de sécurité sur les appareils managés par Intune sont similaires aux appareils comanagés avec Configuration Manager. Les appareils comanagés utilisent System Center Configuration Manager et Microsoft Intune pour gérer les appareils Windows 10 simultanément. Cela vous permet de joindre via le cloud votre investissement dans Configuration Manager existant aux avantages d’Intune. [Vue d’ensemble de la cogestion](https://docs.microsoft.com/sccm/comanage/overview) est une excellente ressource si vous utilisez Configuration Manager et souhaitez également bénéficier des avantages du cloud.

Lorsque vous utilisez des appareils comanagés, vous devez basculer la charge de travail **Configuration de l’appareil** (ses paramètres) vers Intune. Vous trouverez des informations supplémentaires dans [Charges de travail de configuration d’appareil](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration).  

## <a name="q--a"></a>Questions et réponses

### <a name="why-these-settings"></a>Pourquoi ces paramètres ?

L’équipe de sécurité Microsoft travaille directement avec les développeurs Windows et de la communauté de sécurité depuis des années pour créer ces recommandations. Les paramètres de cette base de référence sont considérées comme les options de configuration liées à la sécurité les plus pertinentes. Dans chaque nouvelle build de Windows, l’équipe ajuste ses recommandations en fonction des nouvelles fonctionnalités.

### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Existe-t-il une différence dans les recommandations pour les bases de référence de sécurité Windows pour la stratégie de groupe et Intune ?

La même équipe de sécurité Microsoft a choisi et organisé les paramètres pour chaque base de référence. Intune inclut tous les paramètres pertinents dans la base de référence de sécurité Intune. Il existe certains paramètres dans la base de référence de la stratégie de groupe qui sont spécifiques à un contrôleur de domaine local. Ces paramètres sont exclus des recommandations d’Intune. Tous les autres paramètres sont les mêmes.

### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Les bases de référence de sécurité d’Intune sont-elles conformes à CIS ou NSIT ?

À strictement parler, non. L’équipe de sécurité Microsoft consulte des organisations, comme CIS, pour compiler ses recommandations. Toutefois, il n’existe pas de correspondance directe entre les bases de référence « conformes à CIS » et les bases de référence Microsoft.

### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Quelles sont les certifications des bases de référence de sécurité Microsoft ? 

- Microsoft continue de publier des bases de référence de sécurité pour les stratégies de groupe (GPO) et la [Boîte à outils de conformité de la sécurité](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), comme depuis de nombreuses années. Ces bases de référence sont utilisées par de nombreuses organisations. Les recommandations contenues dans ces bases de référence sont issues de l’engagement de l’équipe de sécurité Microsoft avec des clients d’entreprise et des agences externes, notamment le DOD (Department of Defense), le NIST (National Institute of Standards et Technology) et bien plus encore. Nous partageons nos recommandations et bases de référence avec ces organisations. Ces organisations ont également leurs propres recommandations qui reflètent celles de Microsoft. Alors que la gestion des appareils mobiles continue de croître dans le cloud, Microsoft a créé des recommandations de gestion des appareils mobiles équivalentes à ces bases de référence de la stratégie de groupe. Ces bases de référence supplémentaires sont intégrées à Microsoft Intune et incluent des rapports de conformité sur les utilisateurs, groupes et appareils qui respectent (ou pas) la base de référence.

- De nombreux clients utilisent les recommandations de référence de base d’Intune comme point de départ, puis la personnalisent pour répondre à leur besoins informatiques et de sécurité. La **MDM Security Baseline** (Base de référence de sécurité MDM) Windows 10 RS5 de Microsoft est la première base de référence à être publiée. Cette base de référence est conçue sous la forme d’une infrastructure générique qui permet aux clients d’importer les autres bases de référence de sécurité basées sur CIS, NIST et autres normes. Actuellement, elle est disponible pour Windows et bientôt pour iOS et Android.

- La migration à partir de stratégies de groupe Active Directory locales vers une solution cloud pure à l’aide d’Azure Active Directory (AD) avec Microsoft Intune est un parcours. Des modèles de politiques de groupe sont inclus dans la boîte à outils [Conformité de la sécurité](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) et peuvent vous aider à gérer les appareils hybrides joints à AD et Azure AD. Ces appareils peuvent obtenir les paramètres de gestion des appareils mobiles à partir du cloud (Intune) et les paramètres de stratégie de groupe à partir de contrôleurs de domaine locaux.

## <a name="next-steps"></a>Étapes suivantes
- Affichez les paramètres dans les dernières versions des bases de référence disponibles :  
  - [Base de référence de la sécurité MDM](security-baseline-settings-mdm.md)  
  - [Base de référence Microsoft Defender ATP](security-baseline-settings-defender-atp.md)  

- Vérifier l’état et surveiller [la base de référence et le profil](security-baselines-monitor.md)

