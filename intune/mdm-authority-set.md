---
title: Définir l’autorité de gestion des appareils mobiles
titlesuffix: Microsoft Intune
description: Définissez l’autorité de gestion des appareils mobiles dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 99b913b23638a507ed9b0a5cb32afff66679a164
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231908"
---
# <a name="set-the-mobile-device-management-authority"></a>Définir l’autorité de gestion des appareils mobiles

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le paramètre d’autorité de gestion des appareils mobiles (MDM) détermine la façon dont vous gérez vos appareils. En tant qu’administrateur informatique, vous devez définir une autorité de gestion des appareils mobiles (MDM) avant que les utilisateurs puissent inscrire des appareils pour la gestion.

Les configurations possibles sont les suivantes :

- **Intune autonome** : gestion cloud uniquement, que vous configurez à l’aide du portail Azure. Inclut l’ensemble complet de fonctionnalités d’Intune. [Configurez l’autorité MDM dans la console Intune](#set-mdm-authority-to-intune).

- **Intune hybride** : intégration de la solution cloud Intune à System Center Configuration Manager. Vous configurez Intune à l’aide de la console Configuration Manager. [Configurez l’autorité MDM dans Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription). 

    > [!Important]
    >L’intégration de nouveaux clients GPM hybrides sera désactivée dans une prochaine version. Pour plus d’informations, lisez le billet de blog [Passer de la gestion hybride des appareils mobiles à Intune sur Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

- **Gestion des appareils mobiles pour Office 365** : intégration d’Office 365 à la solution cloud Intune. Vous configurez Intune à partir de votre Centre d’administration Office 365. Comprend un sous-ensemble des fonctionnalités disponibles avec Intune autonome. Configurez l’autorité MDM dans le Centre d'administration Office 365.

> [!IMPORTANT]
> Dans Configuration Manager 1610 ou version ultérieure et Microsoft Intune version 1705, vous modifiez l’autorité MDM sans avoir à contacter le Support Microsoft et sans avoir à annuler l’inscription et à réinscrire vos appareils gérés existants. Pour plus de détails, consultez [Se préparer à utiliser Configuration Manager comme autorité MDM](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager).

## <a name="set-mdm-authority-to-intune"></a>Définir l'autorité MDM sur Intune

Si vous n’avez pas encore défini l’autorité MDM, suivez les étapes ci-dessous. Pour changer d’autorité MDM, consultez la section [Changer d’autorité MDM](#prepare-to-change-the-mdm-authority-to-configuration-manager) ci-dessous.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Sélectionnez la bannière orange pour ouvrir le paramètre **Autorité de gestion des appareils mobiles**. La bannière orange s’affiche seulement si vous n’avez pas encore défini l’autorité MDM.
4. Sous **Autorité de gestion des appareils mobiles**, choisissez votre autorité de gestion des appareils mobiles parmi les options suivantes :
   - **Autorité MDM Intune**
   - **Autorité MDM Configuration Manager**
   - **Aucune.**

   ![Capture de l’écran Intune Définir l’autorité de gestion des appareils mobiles](media/set-mdm-auth.png)

   Un message indique que vous avez défini Intune comme autorité de gestion des appareils mobiles.

### <a name="workflow-of-intune-administration-ui"></a>Flux de travail de l’interface utilisateur d’administration Intune
Quand la gestion des appareils Android ou Apple est activée, Intune envoie des informations relatives aux appareils et aux utilisateurs pour s’intégrer à ces services tiers et gérer leurs appareils respectifs.

Voici quelques-uns des scénarios dans lesquels une fenêtre de consentement de partage des données s’affiche :
- Vous activez les profils professionnels Android.
- Vous activez et chargez des certificats Push MDM Apple.
- Vous activez l’un des services Apple, notamment le Programme d’inscription des appareils (DEP), School Manager et le Programme d’achat en volume (VPP).

Dans chaque cas, le consentement est strictement lié à l’exécution d’un service de gestion des appareils mobiles. Par exemple, confirmer qu’un administrateur informatique a autorisé des appareils Google ou Apple à s’inscrire. Pour savoir quelles informations seront partagées quand les nouveaux flux de travail entreront en vigueur, consultez la documentation suivante :
- [Données envoyées par Intune à Google](https://aka.ms/Data-intune-sends-to-google)
- [Données envoyées par Intune à Apple](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Principales considérations
Après le passage à la nouvelle autorité MDM, une période de transition (jusqu'à huit heures) peut survenir avant que l’appareil n’effectue l’archivage et ne se synchronise avec le service. Il vous est demandé de configurer les paramètres de la nouvelle autorité GPM (hybride) pour garantir que les appareils inscrits continueront d’être gérés et protégés après le changement. 
- Les appareils doivent se connecter au service après le changement afin que les paramètres de la nouvelle autorité MDM (version autonome d’Intune) remplacent les paramètres existants sur l’appareil.
- Une fois le changement d’autorité MDM effectué, certains des paramètres de base (comme les profils) de l’autorité MDM précédente (version autonome d’Intune) restent sur l’appareil pendant sept jours ou jusqu’à ce que l’appareil se connecte au service pour la première fois. Il est recommandé de configurer dès que possible les applications et les paramètres (stratégies, profils, applications, etc.) de la nouvelle autorité GPM (hybride) et de déployer le paramètre sur les groupes d’utilisateurs contenant des utilisateurs qui ont des appareils inscrits existants. Dès qu’un appareil se connecte au service après le changement d’autorité MDM, il reçoit les nouveaux paramètres de la nouvelle autorité MDM, évitant ainsi toute interruption dans la gestion et la protection.
- Quand les mêmes catégories d’appareils existent à la fois dans Intune et dans Configuration Manager, les affectations de catégorie aux appareils ne sont pas effectuées après le passage à la nouvelle autorité MDM. Pour continuer à utiliser les catégories d’appareils, les appareils migrés doivent être ajoutés manuellement aux collections appropriées une fois que l’autorité MDM est changée et que les appareils s’affichent dans la console Configuration Manager.
- Les appareils qui n’ont pas d’utilisateurs associés (en général, lorsque vous utilisez le Programme d’inscription des appareils iOS ou des scénarios d’inscription en bloc) ne sont pas migrés vers la nouvelle autorité MDM. Pour ces appareils, vous devez contacter le support afin d’obtenir de l’aide pour déplacer ces appareils vers la nouvelle autorité MDM.

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>Se préparer à utiliser Configuration Manager comme autorité MDM

Passez en revue les informations suivantes pour préparer le passage à l’autorité MDM :
- Vous devez disposer de Configuration Manager 1610 ou version ultérieure pour pouvoir changer d’autorité MDM.
- Après le passage à la nouvelle autorité MDM, la connexion d’un appareil au service peut prendre jusqu’à huit heures.
- Créez un regroupement d’utilisateurs Configuration Manager contenant tous les utilisateurs actuellement gérés par Intune autonome, à utiliser quand vous configurez l’abonnement Intune dans la console Configuration Manager. Ce regroupement permet de garantir que l’utilisateur et ses appareils disposent d’une licence Configuration Manager et qu’ils sont gérés dans l’environnement hybride après le changement d’autorité GPM.
- Assurez-vous que l’utilisateur administrateur informatique figure également dans ce regroupement.  
- Avant le changement, l’autorité MDM apparaît sous la forme **Définir sur Microsoft Intune** (autonome) dans la console d’administration Intune.
- L’autorité MDM devrait s’afficher sous la forme **Définir sur Microsoft Intune** (locataire autonome) dans la console d’administration Microsoft Intune avant le changement d’autorité MDM.
    > [!NOTE]    
    > Si votre autorité MDM apparaît sous la forme **Géré par Intune et Office 365**, vos appareils MDM gérés par Office 365 ne sont plus gérés quand vous utilisez **Configuration Manager** (hybride) comme autorité MDM. Nous vous recommandons d’attribuer à ces utilisateurs une licence Intune ou Enterprise Mobility Suite avant de changer d’autorité MDM.   

- Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), supprimez le rôle Gestionnaire d’inscription d’appareil. Pour plus d’informations, consultez [Supprimer un gestionnaire d'inscription d'appareil d'Intune](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions).
- Désactivez tous les mappages de groupes d’appareils configurés. Pour plus d’informations, consultez [Catégoriser les appareils avec un mappage de groupes d’appareils dans Microsoft Intune](device-group-mapping.md).
- Le changement d’autorité MDM ne devrait avoir aucun impact significatif sur les utilisateurs finaux. Toutefois, vous pouvez en informer ces utilisateurs pour s’assurer que leurs appareils sont sous tension et qu’ils se connectent au service peu après le changement. Cette précaution permet de connecter et d’inscrire autant d’appareils que possible auprès du service aussitôt la nouvelle autorité sélectionnée.
- Si vous utilisez Intune autonome pour gérer des appareils iOS avant le changement d’autorité GPM, vous devez veiller à ce que le même certificat du service de notification push d'Apple (APNs) précédemment utilisé dans Intune soit renouvelé et utilisé pour réinstaller le locataire dans Configuration Manager (hybride).    

    > [!IMPORTANT]  
    > Si un autre certificat APNs est utilisé pour la version hybride, l’inscription de TOUS les appareils iOS précédemment inscrits est annulée et vous devez les réinscrire. Avant de changer d’autorité MDM, assurez-vous que vous savez exactement quel certificat APNs a été utilisé pour gérer les appareils iOS dans Intune. Recherchez le même certificat affiché dans le portail Apple Push Certificates (https://identity.apple.com)) et vérifiez que l’utilisateur dont l’ID Apple a été utilisé pour créer le certificat d’origine est identifié et disponible pour renouveler le même certificat APNs dans le cadre du changement d’autorité MDM.

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Utiliser Configuration Manager comme autorité MDM

1. Dans la console Configuration Manager, accédez à **Administration** &gt; **Vue d’ensemble** &gt; **Services Cloud** &gt; **Abonnement Microsoft Intune**, puis choisissez d’ajouter un abonnement Intune.
2. Connectez-vous au locataire Intune que vous avez utilisé lors de la première définition de l’autorité MDM dans Intune, puis cliquez sur **Suivant**.
3. Sélectionnez **Utiliser Configuration Manager comme autorité MDM**, puis cliquez sur **suivant**.
4. Sélectionnez le regroupement d’utilisateurs contenant tous les utilisateurs qui continuent d’être gérés par la nouvelle autorité MDM hybride.
5. Cliquez sur **Suivant** pour terminer l'Assistant. La nouvelle autorité MDM est désormais **Configuration Manager**.
6. Connectez-vous à la [console d’administration Microsoft Intune](http://manage.microsoft.com) en utilisant le même locataire Intune et vérifiez que l’autorité GPM a été changée en **Définir sur Configuration Manager**.
7. Après avoir changé l’autorité MDM pour Configuration Manager, vous pouvez configurer [l’inscription iOS](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac) et [l’inscription Android](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android).
8. Dans la console Configuration Manager, configurez et déployez les nouveaux réglages et les nouvelles applications à partir de la nouvelle autorité MDM (hybride).

La prochaine fois qu’ils se connecteront au service, les appareils se synchronisent et reçoivent les nouveaux paramètres à partir de la nouvelle autorité MDM.

## <a name="change-mdm-authority-to-office-365"></a>Changer l’autorité MDM pour Office 365

Pour activer MDM Office 365 en plus de votre service Intune existant, accédez à [https://protection.office.com](https://protection.office.com), choisissez **Protection contre la perte de données** > **Stratégies de sécurité des appareils** > **Afficher la liste des appareils gérés** > **Démarrer**.

Pour plus d’informations, consultez [Configurer MDM dans Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Si vous voulez que les utilisateurs soient gérés seulement dans MDM Office 365, supprimez les licences Intune et/ou EMS attribuées après l’activation de MDM Office 365.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Nettoyage de l’appareil mobile après expiration du certificat MDM

Le certificat MDM est renouvelé automatiquement lorsque les appareils mobiles communiquent avec le service Intune. Si des appareils mobiles sont réinitialisés ou ne parviennent pas à communiquer avec le service Intune pendant un certain temps, le certificat MDM n’est pas renouvelé. L’appareil est supprimé du portail Azure 180 jours après l’expiration du certificat MDM.

## <a name="remove-mdm-authority"></a>Supprimer l’autorité MDM

L’autorité MDM ne peut pas être rétablie à Inconnu. L’autorité MDM est utilisée par les serveurs de Microsoft pour déterminer à quel portail se rapportent les appareils inscrits (ConfigMGR, Azure Intune, MDM Office 365).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Ce qui se passe après un changement de l’autorité MDM

- Quand le service Intune détecte que l’autorité GPM d’un locataire a changé, il envoie un message de notification à tous les appareils inscrits pour qu’ils s’enregistrent et se synchronisent avec le service (cette notification a lieu en dehors de l’enregistrement régulier planifié). Par conséquent, une fois que l’autorité MDM du locataire est passée de la version autonome d’Intune à hybride, tous les appareils sous tension et en ligne se connecteront au service, recevront la nouvelle autorité MDM et seront désormais gérés par la version hybride. Il n’y a aucune interruption au niveau de la gestion et de la protection de ces appareils.
- Même si les appareils sont sous tension et en ligne pendant (ou juste après) le changement d’autorité MDM, un délai de huit heures maximum s’écoulera (selon l’heure du prochain enregistrement normal planifié) avant que les appareils soient inscrits auprès du service sous la nouvelle autorité MDM.    

  > [!IMPORTANT]    
  > Entre le moment où vous changez l’autorité MDM et celui où le certificat APNs renouvelé est chargé dans la nouvelle autorité, les inscriptions de nouveaux appareils et l’enregistrement d’appareils iOS échouent. Par conséquent, il est important de passer en revue et de charger le certificat APNs dans la nouvelle autorité dès que possible après le changement d’autorité GPM.

- Les utilisateurs peuvent rapidement basculer vers la nouvelle autorité MDM en lançant manuellement un enregistrement de l’appareil vers le service. Les utilisateurs peuvent facilement effectuer cette modification à l’aide de l’application du portail d’entreprise, en lançant une vérification de conformité d’appareil.
- Pour confirmer que tout fonctionne correctement une fois les appareils enregistrés et synchronisés avec le service après le changement d’autorité MDM, recherchez les appareils dans la console Configuration Manager. Les appareils précédemment gérés par Intune apparaissent désormais en tant qu’appareils gérés dans la console Configuration Manager.    
- Il existe une période temporaire pendant laquelle un appareil est hors ligne lors du changement d’autorité MDM et lorsque cet appareil s’enregistre auprès du service. Pour que l’appareil reste protégé et opérationnel pendant cet intervalle, les profils suivants y sont conservés pendant sept jours maximum (ou jusqu’à ce que l’appareil se connecte à la nouvelle autorité MDM et reçoive les nouveaux paramètres qui remplacent les paramètres existants) :
    - Profil de messagerie
    - Profil VPN
    - Profil de certificat
    - Profil Wi-Fi
    - Profils de configuration
- Après la sélection de la nouvelle autorité MDM, une semaine peut être nécessaire avant que les données de conformité s’affichent correctement dans la console d’administration Microsoft Intune. Cependant, les états de conformité dans Azure Active Directory et sur l’appareil restent corrects et l’appareil est ainsi toujours protégé.
- Vérifiez que les nouveaux paramètres destinés à remplacer les paramètres existants portent le même nom que les précédents pour s’assurer que les anciens paramètres sont remplacés. Sinon, les appareils risquent de contenir des stratégies et des profils redondants.    

  > [!TIP]    
  > Il est recommandé de créer tous les paramètres de gestion et toutes les configurations, ainsi que les déploiements, peu de temps après le changement d’autorité MDM. Ceci permet de garantir que les appareils sont protégés et activement gérés pendant la période temporaire.

-  Après avoir modifié l’autorité MDM, procédez comme suit pour confirmer que les nouveaux appareils sont inscrits correctement auprès de la nouvelle autorité :   
    - Inscrire un nouvel appareil
    - Assurez-vous que l’appareil qui vient d’être inscrit s’affiche dans la console Configuration Manager.
    - Effectuez une action, par exemple un verrouillage à distance, à partir de la console d’administration sur l’appareil. En cas de succès, l’appareil est géré par la nouvelle autorité MDM.
- Si vous rencontrez des problèmes avec des appareils spécifiques, vous pouvez annuler l’inscription puis réinscrire ces appareils pour les connecter à la nouvelle autorité et les gérer dès que possible.

## <a name="next-steps"></a>Étapes suivantes

Une fois l’autorité MDM définie, vous pouvez commencer à [inscrire des appareils](device-enrollment.md).
