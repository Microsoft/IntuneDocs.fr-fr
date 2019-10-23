---
title: Définir l’autorité de gestion des appareils mobiles
titleSuffix: Microsoft Intune
description: Définissez l’autorité de gestion des appareils mobiles dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19d02694ab5e53dc43e0861c6a427a044bf50648
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502639"
---
# <a name="set-the-mobile-device-management-authority"></a>Définir l’autorité de gestion des appareils mobiles

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Le paramètre d’autorité de gestion des appareils mobiles (MDM) détermine la façon dont vous gérez vos appareils. En tant qu’administrateur informatique, vous devez définir une autorité de gestion des appareils mobiles (MDM) avant que les utilisateurs puissent inscrire des appareils pour la gestion.

Les configurations possibles sont les suivantes :

- **Intune autonome** : gestion cloud uniquement, que vous configurez à l’aide du portail Azure. Inclut l’ensemble complet de fonctionnalités d’Intune. [Configurez l’autorité MDM dans la console Intune](#set-mdm-authority-to-intune).

- **Cogestion Intune** : intégration de la solution cloud Intune à System Center Configuration Manager pour les appareils Windows 10. Vous configurez Intune à l’aide de la console Configuration Manager. [Configurez l’inscription automatique des appareils dans Intune](https://docs.microsoft.com/sccm/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune). 

    > [!Important]
    >L’intégration des nouveaux clients MDM hybrides est dépréciée. Pour plus d’informations, lisez le billet de blog [Passer de la gestion hybride des appareils mobiles à Intune sur Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

- **Gestion des appareils mobiles pour Office 365** : intégration d’Office 365 à la solution cloud Intune. Vous configurez Intune à partir de votre Centre d’administration Microsoft 365. Comprend un sous-ensemble des fonctionnalités disponibles avec Intune autonome. Configurez l’autorité MDM dans le Centre d’administration Microsoft 365.

- **Coexistence avec Office 365 MDM** Vous pouvez activer et utiliser simultanément MDM pour Office 365 et Intune sur votre locataire et choisir Intune ou MDM pour Office 365 comme autorité de gestion pour chaque utilisateur afin de spécifier quel service sera utilisé pour gérer leurs appareils mobiles. L'autorité de gestion de l'utilisateur est définie en fonction de la licence attribuée à l'utilisateur. Pour plus d'informations, voir [Microsoft Intune Co-existence with MDM for Office 365 (Coexistence de Microsoft Intune avec MDM pour Office 365)](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365)

## <a name="set-mdm-authority-to-intune"></a>Définir l'autorité MDM sur Intune

Si vous n’avez pas encore défini l’autorité MDM, suivez les étapes ci-dessous. Pour remplacer SCCM, consultez [Faire migrer des utilisateurs et appareils MDM hybrides vers la version autonome d’Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

1. Dans [Intune dans le portail Azure](https://aka.ms/intuneportal), sélectionnez la bannière orange pour ouvrir le paramètre **Autorité de gestion des appareils mobiles**. La bannière orange s’affiche seulement si vous n’avez pas encore défini l’autorité MDM.
2. Sous **Autorité de gestion des appareils mobiles**, choisissez votre autorité de gestion des appareils mobiles parmi les options suivantes :
   - **Autorité MDM Intune**
   - **Aucune.**

   ![Capture de l’écran Intune Définir l’autorité de gestion des appareils mobiles](./media/mdm-authority-set/set-mdm-auth.png)

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

## <a name="change-mdm-authority-to-office-365"></a>Changer l’autorité MDM pour Office 365

Pour activer MDM Office 365 (ou pour activer la coexistence de MDM en plus de votre service Intune existant), accédez à [https://protection.office.com](https://protection.office.com), choisissez **Protection contre la perte de données** > **Stratégies de sécurité des appareils** > **Afficher la liste des appareils gérés** > **Démarrer**.

Pour plus d’informations, consultez [Configurer MDM dans Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Si vous voulez que les utilisateurs soient gérés seulement dans MDM Office 365, supprimez les licences Intune et/ou EMS attribuées après l’activation de MDM Office 365.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Nettoyage de l’appareil mobile après expiration du certificat MDM

Le certificat MDM est renouvelé automatiquement lorsque les appareils mobiles communiquent avec le service Intune. Si des appareils mobiles sont réinitialisés ou ne parviennent pas à communiquer avec le service Intune pendant un certain temps, le certificat MDM n’est pas renouvelé. L’appareil est supprimé du portail Azure 180 jours après l’expiration du certificat MDM.

## <a name="remove-mdm-authority"></a>Supprimer l’autorité MDM

L’autorité MDM ne peut pas être rétablie à Inconnu. L’autorité MDM est utilisée par le service pour déterminer à quel portail se rapportent les appareils inscrits (Microsoft Intune ou MDM Office 365).

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

- Après avoir modifié l’autorité MDM, procédez comme suit pour confirmer que les nouveaux appareils sont inscrits correctement auprès de la nouvelle autorité :   
  - Inscrire un nouvel appareil
  - Assurez-vous que l’appareil qui vient d’être inscrit s’affiche dans la console Configuration Manager.
  - Effectuez une action, par exemple un verrouillage à distance, à partir de la console d’administration sur l’appareil. En cas de succès, l’appareil est géré par la nouvelle autorité MDM.
- Si vous rencontrez des problèmes avec des appareils spécifiques, vous pouvez annuler l’inscription puis réinscrire ces appareils pour les connecter à la nouvelle autorité et les gérer dès que possible.

## <a name="next-steps"></a>Étapes suivantes

Une fois l’autorité MDM définie, vous pouvez commencer à [inscrire des appareils](../enrollment/device-enrollment.md).
