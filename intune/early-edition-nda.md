---
title: Edition anticipée - Microsoft Intune
titlesuffix: ''
description: Edition anticipée de Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1ff65e1b48815cd5964aa7498fa6ba54df50e09
ms.sourcegitcommit: e5f501b396cb8743a8a9dea33381a16caadc51a9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56742293"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>Édition préliminaire de Microsoft Intune - Février 2019

> [!Note]
> Notification relative à l’accord de confidentialité : Les modifications suivantes sont en cours de développement pour Intune. Ces informations sont partagées selon les termes de l’accord de confidentialité, de façon très limitée. Ne publiez aucune de ces informations sur des médias sociaux ou des sites web publics comme Twitter, UserVoice, Reddit, etc. 

**L’édition préliminaire** fournit la liste des fonctionnalités, partagée selon les termes de l’accord de confidentialité, qui seront intégrées dans les prochaines versions de Microsoft Intune. Ces informations sont fournies de manière limitée et sont susceptibles de changer. Ne tweetez pas, ne publiez sur UserVoice et ne partagez pas ces informations en dehors de votre entreprise. Certaines fonctionnalités répertoriées ici risquent de ne pas être prêtes d’ici la date limite et d’être repoussées à une version ultérieure. D’autres fonctionnalités sont en cours de test dans un pilote (version d’évaluation) pour s’assurer qu'elles sont prêtes à l'emploi. Joignez votre contact de groupe de produits Microsoft si vous avez des questions ou rencontrez des problèmes.

Cette page est mise à jour périodiquement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune dans le portail Azure
<!-- 1902 start-->


<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Déploiement en ligne d’un Microsoft Store sous licence pour les applications métier <!-- 1672660  -->
Vous serez en mesure d’assigner un Microsoft Store sous licence en ligne obligatoire pour les applications métier dans le contexte d’appareil. Un Microsoft Store pour une application métier déployé de cette façon permet à l’application d’être installée pour tous les utilisateurs sur l’appareil. Seuls les appareils de bureau Windows 10 version RS4 et ultérieures sont concernés. L’option d’installation dans le contexte d’appareil est disponible dans la page d’affectation des applications clientes pour les applications sous licence en ligne MSFB.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Déploiement d’applications APP-WE Android pour les entreprises<!-- 1171203 -->
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie App Protection sans inscription) non inscrit, vous pourrez utiliser Google Play dans sa version gérée pour déployer des applications du Store et des applications métier auprès des utilisateurs. Plus précisément, le service informatique pourra proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle il ne sera plus nécessaire d’assouplir la posture de sécurité de appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Les stratégies Intune mettent à jour la méthode d’authentification et l’installation de l’application Portail d’entreprise<!-- 1927359 -->
Sur les appareils déjà inscrits via l’Assistant Configuration avec l’une des méthodes d’inscription des appareils d’entreprise d’Apple, Intune ne prendra plus en charge le Portail d’entreprise lorsqu’il est installé manuellement par les utilisateurs finaux à partir de l’App store. Cette modification n’est pertinente qu’en cas d’authentification avec l’Assistant Configuration Apple lors de l’inscription. Par ailleurs, elle n’affecte que les appareils iOS inscrits avec :  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Programme d’inscription des appareils (DEP) d’Apple

Les utilisateurs qui installeront l’application Portail d’entreprise à partir de l’App Store, puis essayeront d’inscrire ces appareils par ce biais recevront une erreur. Ces appareils ne devront utiliser le Portail d’entreprise que lorsqu’il est transmis, automatiquement, par Intune lors de l’inscription. Les profils d’inscription dans Intune sur le Portail Azure seront mis à jour : il sera ainsi possible de spécifier la façon dont les appareils s’authentifieront et d’indiquer s’ils recevront l’application Portail d’entreprise. Si vous souhaitez que les utilisateurs d’appareils DEP disposent du Portail d’entreprise, vous devrez spécifier vos préférences dans un profil d’inscription. Par ailleurs, l’écran **Identifier votre appareil** de l’application Portail d’entreprise sera bientôt obsolète.  
Pour installer le Portail d’entreprise sur des appareils DEP déjà inscrits, il faudra accéder à Intune > Applications clientes et le transmettre sous forme d’application managée avec les stratégies de configuration des applications. D’autres informations sur la procédure à suivre seront données dans la documentation à venir.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Les modèles d’administration, en préversion publique, sont déplacés vers leur propre profil de configuration<!-- 3322847 -->
Les modèles d’administration dans Intune (**Configuration de l’appareil** > **Modèles d’administration**) sont actuellement en préversion privée. Avec cette mise à jour : Les modèles administratifs comportent environ 300 paramètres qui peuvent être gérés dans Intune. Auparavant, ces paramètres se trouvaient uniquement dans l’Éditeur d’objets de stratégie de groupe.
Les modèles d’administration, disponibles en préversion publique, sont déplacés de **Configuration de l’appareil** > **Modèles d’administration** à **Configuration de l’appareil** > **Profils** >**Créer un profil** > dans **Plateforme**, choisissez **Windows 10 et versions ultérieures**, dans **Type de profil**, choisissez **Modèles d’administration**.
La création de rapports est activée. S’applique à : Windows 10 et versions ultérieures

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Mode sombre du Portail d’entreprise Intune macOS <!-- 3300524 -->
Le portail d’entreprise Intune macOS prend désormais en charge le Mode sombre pour macOS. Quand vous activez le Mode sombre sur un appareil macOS 10.14+, le portail d’entreprise ajuste son apparence à des couleurs reflétant ce mode.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Paramètres de stratégie de protection des applications pour les données du web <!-- 2662995 -->
Les paramètres de stratégie de protection des applications pour le contenu web sur les appareils iOS et Android seront mis à jour afin de mieux gérer les liens web http et https, ainsi que le transfert de données via des liens universels iOS et des liens d’application Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Jeton VPP Apple utilisé par une autre gestion MDM <!-- 1488946 -->
Intune détectera et affichera des détails si un jeton du Programme d’achat en volume (VPP) Apple est utilisé à la fois par Intune et une autre gestion MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Appareils mis hors service dans le tableau de bord de conformité des appareils <!-- 1981119 -->
Dans une prochaine mise à jour, les appareils mis hors service seront retirés du tableau de bord de conformité des appareils. Cela changera vos numéros de conformité.

## <a name="notices"></a>Remarques

Il n’existe aucun avis actif pour l’instant.

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.
