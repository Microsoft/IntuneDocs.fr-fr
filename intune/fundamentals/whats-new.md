---
title: Nouveautés de Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Découvrez les nouveautés du portail Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2f984392983d81bc64edb7206469babdb806d63
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609282"
---
# <a name="whats-new-in-microsoft-intune"></a>Nouveautés de Microsoft Intune

Découvrez les nouveautés hebdomadaires dans Microsoft Intune. Vous pouvez également trouver des [annonces importantes](#notices), des [publications précédentes](whats-new-archive.md) et des informations sur [le mode de publication des mises à jour par le service Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> Chaque [mise à jour mensuelle](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728) peut mettre jusqu'à trois jours pour être déployée et le sera dans l’ordre suivant :
>
> - Jour 1 : Asie-Pacifique (APAC)
> - Jour 2 : Europe, Moyen-Orient et Afrique (EMEA)
> - Jour 3 : Amérique du Nord
> - Jour 4+ : Intune pour le secteur public
>
> Certaines fonctionnalités peuvent être lancées sur plusieurs semaines et peuvent ne pas être disponibles pour tous les clients la première semaine.
>
> Consultez la [page En développement](in-development.md) pour obtenir une liste des fonctionnalités à venir dans une version.

**Flux RSS** : Recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-february-24-2020"></a>Semaine du 24 février 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>améliorations de l’expérience utilisateur du Portail d’entreprise macOS<!-- 5568987 -->
Nous avons apporté des améliorations à l’expérience d’inscription des appareils macOS et à l’application Portail d’entreprise pour Mac. Voici ce que vous allez voir :
- Une meilleure expérience de Microsoft **AutoUpdate** lors de l’inscription, afin de garantir que vos utilisateurs disposent de la dernière version du Portail d’entreprise.
- Une étape de vérification de la conformité améliorée lors de l’inscription.
- La prise en charge de la copie des ID d’incident, pour que vos utilisateurs puissent envoyer plus rapidement les erreurs de leurs appareils à l’équipe de support technique de votre entreprise.

Pour plus d’informations sur l’inscription et l’application Portail d’entreprise pour Mac, consultez [Inscrire votre appareil macOS en utilisant l’application Portail d’entreprise](/intune-user-help/enroll-your-device-in-intune-macos-cp). 

<!-- ########################## -->
## <a name="week-of-february-17-2020-2002-service-release"></a>Semaine du 17 janvier 2020 (version du service 2002)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424618---"></a>Application Microsoft Defender Advanced Threat Protection pour macOS<!-- 5424618 -->
Intune offre un moyen simple de déployer l’application Microsoft Defender Advanced Threat Protection pour macOS sur les appareils Mac gérés. Pour plus d’informations, consultez [Ajouter Microsoft Defender ATP à des appareils macOS avec Microsoft Intune](~/apps/apps-advanced-threat-protection-macos.md) et [Microsoft Defender Advanced Threat Protection pour Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac).  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111----"></a>Activer le contrôle d’accès réseau (NAC) avec Cisco AnyConnect VPN sur les appareils iOS<!-- 4860111  -->
Sur les appareils iOS, vous pouvez créer un profil VPN et utiliser différents types de connexion, notamment Cisco AnyConnect (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS** pour la plateforme > **VPN** pour le type de profil > **Cisco AnyConnect** pour le type de connexion). 

Vous pouvez activer le contrôle d’accès réseau (NAC) avec Cisco AnyConnect. Pour utiliser cette fonctionnalité :

1. Dans [Cisco Identity Services Engine Administrator Guide](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html), suivez les étapes décrites dans **Configuring Microsoft Intune as an MDM Server** pour configurer le moteur ISE (Identity Services Engine) Cisco dans Azure.
2. Dans le profil de configuration d’appareil Intune, sélectionnez le paramètre **Activer le contrôle d’accès réseau (NAC)** .

Pour voir tous les paramètres VPN disponibles, accédez à [Configurer les paramètres VPN sur les appareils iOS](../configuration/vpn-settings-ios.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765----"></a>Numéro de série sur la page Certificat Push MDM Apple<!--5947765  -->
La page Certificat Push MDM Apple montre désormais le numéro de série. Le numéro de série est nécessaire pour accéder à nouveau au certificat Push MDM Apple si l’accès à l’ID Apple qui a créé le certificat est perdu. Pour voir le numéro de série, accédez à **Appareils** > **iOS** > **Inscription iOS** > **Certificat Push MDM Apple**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des périphériques

#### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689----"></a>Nouvelles options de planification des mises à jour pour l’envoi des mises à jour du système d’exploitation aux appareils iOS/iPadOS inscrits<!--5879689  -->
Vous pouvez choisir parmi les options suivantes lors de la planification des mises à jour du système d’exploitation pour les appareils iOS/iPadOS. Ceci s’applique aux appareils qui ont utilisé les types d’inscription Apple Business Manager ou Apple School Manager.
- Mettre à jour lors du check-in suivant
- Mettre à jour pendant l’intervalle planifié
- Mettre à jour en dehors de l’intervalle planifié

Pour les deux dernières options, vous pouvez créer plusieurs fenêtres de temps.

Pour voir les nouvelles options, accédez à MEM > **Appareils** > **iOS** > **Mettre à jour les stratégies pour iOS/iPadOS** > **Créer un profil**.

#### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689----"></a>Choisir les mises à jour iOS/iPadOS à envoyer aux appareils inscrits<!--5879689  -->
Vous pouvez choisir une mise à jour iOS/iPadOS (excepté pour la mise à jour la plus récente) à envoyer aux appareils qui ont été inscrits avec Apple Business Manager ou Apple School Manager. Ces appareils doivent avoir une stratégie de configuration d’appareil définie pour retarder la visibilité des mises à jour logicielles pendant un certain nombre de jours. Pour voir cette fonctionnalité, accédez à MEM > **Appareils** > **iOS** > **Mettre à jour les stratégies pour iOS/iPadOS** > **Créer un profil**.

### <a name="all-devices-list-improved-search-sort-and-filter--6179023--"></a>Recherche, tri et filtrages améliorés dans la liste Tous les appareils<!--6179023-->
Les performances, la recherche, le tri et le filtrage ont été améliorés dans la liste Tous les appareils.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sécurité des appareils

#### <a name="improved-intune-reporting-experience---3791418-----"></a>Amélioration de l’expérience de création de rapports Intune<!-- 3791418   -->
Intune offre désormais une meilleure expérience de création de rapports, avec notamment de nouveaux types de rapports, une meilleure organisation des rapports, des vues plus ciblées, des fonctionnalités de rapport améliorées, ainsi que des données plus cohérentes et ponctuelles. L’expérience de création de rapports passe de la préversion à la disponibilité générale. En outre, la version en disponibilité générale fournit une prise en charge de la localisation, des correctifs de bogues, des améliorations de conception et des données de conformité d’appareil agrégées sur les vignettes dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). 

Les nouveaux types de rapport se concentrent sur les éléments suivants :
- **Opérationnel** : fournit des enregistrements actualisés en se concentrant sur les éléments d’intégrité négatifs. 
- **Organisationnel** : fournit un résumé plus large de l’état global.
- **Historique** : fournit les modèles et tendances sur une période donnée.
- **Spécialiste** : vous permet d’utiliser des données brutes pour créer vos propres rapports personnalisés.

Le premier ensemble de nouveaux rapports se concentre sur la conformité des appareils. Pour plus d’informations, consultez [Blog - Infrastructure de création de rapports Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) et [Rapports Intune](~/fundamentals/reports.md).

#### <a name="consolidated-the-location-of-security-baselines-in-the-ui---6177074-----"></a>Consolidation de l’emplacement des bases de référence de sécurité dans l’interface utilisateur<!-- 6177074   -->
Nous avons consolidé les chemins pour trouver des [bases de référence de sécurité](../protect/security-baselines.md) dans le centre d’administration du gestionnaire de points de terminaison Microsoft en supprimant *Bases de référence de sécurité* de plusieurs endroits de l’interface utilisateur. Pour trouver des base de référence de sécurité, vous utilisez maintenant le chemin suivant :  **Sécurité du point de terminaison** > **Bases de référence de sécurité**.

#### <a name="expanded-support-for-imported-pkcs-certificates---6044197-wnready---"></a>Prise en charge étendue des certificats PKCS importés<!-- 6044197 WNReady -->
Nous avons étendu la prise en charge de l’utilisation de [certificats PKCS importés](../protect/certificates-imported-pfx-configure.md#supported-platforms) pour prendre en charge les *Appareils Android Entreprise complètement gérés*. En règle générale, l’importation de certificats PFX est utilisée pour les scénarios de chiffrement S/MIME, où les certificats de chiffrement d’un utilisateur sont nécessaires sur tous ses appareils afin que le déchiffrement des e-mails puisse se faire.

Les plateformes suivantes prennent en charge l’importation de certificats PFX :
- Android - Administrateur d’appareil
- Android Entreprise - Complètement géré
- Android Entreprise - Profil de travail
- iOS
- Mac
- Windows 10

#### <a name="view-the-endpoint-security-configuration-for-devices---6206460----"></a>Afficher la configuration de la sécurité du point de terminaison pour les appareils<!-- 6206460  -->
Nous avons mis à jour le nom de l’option dans le centre d’administration du gestionnaire de points de terminaison Microsoft permettant d’afficher les [configurations de sécurité de point de terminaison qui s’appliquent à un appareil spécifique](../protect/security-baselines-monitor.md#view-endpoint-security-configurations-per-device). Cette option est renommée **Configuration de la sécurité du point de terminaison**, car elle montre les bases de référence de sécurité applicables et les stratégies supplémentaires créées en dehors des bases de référence de sécurité. Avant, cette option était nommée *Bases de référence de sécurité*. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="intune-roles-user-interface-changes-coming--5801612-----"></a>Modifications à venir de l’interface utilisateur des rôles Intune<!--5801612   -->
L’interface utilisateur du [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Administration de locataire** > **Rôles** a été améliorée en faveur d’une conception plus conviviale et plus intuitive. Cette expérience fournit les mêmes paramètres et les mêmes informations détaillées que celles que vous utilisez maintenant, mais la nouvelle expérience utilise un processus de type Assistant.

<!-- ########################## -->
## <a name="week-of-february-17-2020"></a>Semaine du 17 février 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="microsofts-new-office-app---5859926---"></a>Nouvelle application Office de Microsoft<!-- 5859926 -->
La nouvelle application Office de Microsoft est maintenant en disponibilité générale pour le téléchargement et l’utilisation. L’application Office est une expérience centralisée dans laquelle vos utilisateurs peuvent travailler sur Word, Excel et PowerPoint au sein d’une même application. Vous pouvez cibler l’application avec une stratégie de protection des applications pour garantir que les données auxquelles elles accèdent sont protégées.

Pour plus d’informations, consultez [Comment activer des stratégies de protection des applications Intune avec l’application mobile Office en préversion](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-how-to-enable-intune-app-protection-policies-with/ba-p/1045493).

<!-- ########################## -->
## <a name="week-of-february-10-2020"></a>Semaine du 10 février 2020

### <a name="windows-7-ends-extended-support--3042987---"></a>Fin du support étendu Windows 7<!--3042987 -->
Windows 7 a atteint la fin du support étendu le 14 janvier 2020. Intune déconseille depuis cette date la prise en charge des appareils Windows 7. L’assistance technique et les mises à jour automatiques qui vous permettent de protéger votre PC ne sont plus disponibles. Nous vous recommandons de passer à Windows 10. Pour plus d’informations, consultez le [billet de blog Calendrier des modifications](https://aka.ms/Windows7_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>Microsoft Edge version 77 et ultérieures sur des appareils Windows 10<!-- 5843584 -->
Intune prend désormais en charge la désinstallation de Microsoft Edge version 77 et ultérieures sur les appareils Windows 10. Pour plus d’informations, consultez [Ajouter Microsoft Edge pour Windows 10 à Microsoft Intune](~/apps/apps-windows-edge.md).

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Écran supprimé du portail d’entreprise, inscription de profil professionnel Android<!--6103987 -->
L’écran **Quelle est la prochaine étape**  a été supprimé du flux d’inscription de profil professionnel Android dans le portail d’entreprise, afin de faciliter l’expérience utilisateur. Accédez à [Inscrire avec un profil professionnel Android](/intune-user-help/enroll-device-android-work-profile) pour voir la mise à jour du flux d’inscription de profil professionnel Android.  

#### <a name="company-portal-app-improved-performance---6178652---"></a>Amélioration des performances de l’application Portail d’entreprise<!-- 6178652 -->
L’application Portail d’entreprise a été mise à jour pour prendre en charge les performances améliorées des appareils qui utilisent des processeurs ARM64, notamment Surface Pro X. Auparavant, Portail d’entreprise fonctionnait dans un mode ARM32 émulé. À présent, dans la version 10.4.7080.0 et les versions ultérieures, l’application Portail d’entreprise est compilée en mode natif pour ARM64. Pour plus d’informations sur l’application Portail d’entreprise, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](~/apps/company-portal-app.md).

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>Semaine du 27 janvier 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>Prise en charge d’Intune pour un autre canal de déploiement Microsoft Edge version 77 pour macOS<!-- 5983950  -->
Microsoft Intune prend maintenant en charge le canal de déploiement **Stable** supplémentaire pour l’application Microsoft Edge pour macOS. Le canal **Stable** est le canal recommandé pour le déploiement à grande échelle de Microsoft Edge dans des environnements d’entreprise. Il est mis à jour toutes les six semaines, chaque version intégrant des améliorations du canal **bêta**. En plus des canaux **Stable** et **bêta**, Intune prend en charge un canal **dev**. La préversion publique offre des canaux Stable et dev pour Microsoft Edge version 77 et versions ultérieures pour macOS. Les mises à jour automatiques du navigateur sont activées par défaut. Pour plus d’informations, consultez [Ajouter Microsoft Edge pour les appareils macOS qui utilisent Microsoft Intune](~/apps/apps-edge-macos.md).

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Mise hors service d’Intune Managed Browser<!--5728447 -->
Intune Managed Browser va être mis hors service. Utilisez Microsoft Edge pour votre expérience Protected Intune Browser. Pour plus d'informations, consultez l’entrée '[Action nécessaire : Utilisez Microsoft Edge pour votre expérience Protected Intune Browser](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience)' dans la section [Remarques](~/fundamentals/whats-new.md#notices) ci-dessous.

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>Semaine du 20 janvier 2020 (version 2001)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Modification de l’expérience utilisateur lors de l’ajout d’applications à Intune<!-- 4705829   -->
Vous constaterez une nouvelle expérience utilisateur lors de l’ajout d’applications à Intune. Cette expérience fournit les mêmes paramètres et les mêmes informations détaillées que ceux que vous avez utilisés auparavant, mais la nouvelle expérience utilise un processus de type Assistant avant l’ajout d’une application à Intune. Cette nouvelle expérience fournit également une page de vérification avant l’ajout de l’application. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Applications** > **Toutes les applications** > **Ajouter**. Pour plus d’informations, consultez [Ajouter des applications à Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Exiger le redémarrage des applications Win32 <!-- 5622282   -->
Vous pouvez exiger le redémarrage d’une application Win32 après son installation réussie. Vous pouvez également choisir la durée (période de grâce) avant le redémarrage.

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Modification de l’expérience utilisateur lors de la configuration d’applications dans Intune<!-- 4207990   -->
Vous constaterez une nouvelle expérience utilisateur lors de la création de stratégies de configuration des applications dans Intune. Cette expérience fournit les mêmes paramètres et les mêmes informations détaillées que ceux que vous avez utilisés auparavant, mais la nouvelle expérience utilise un processus de type Assistant avant l’ajout d’une stratégie à Intune. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter**. Pour plus d’informations, consultez [Stratégies de configuration des applications pour Microsoft Intune](~/apps/app-configuration-policies-overview.md). 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>Prise en charge d’Intune pour le canal de déploiement supplémentaire Microsoft Edge pour Windows 10<!-- 5861774 -->
Microsoft Intune prend maintenant en charge le canal de déploiement **Stable** supplémentaire pour l’application Microsoft Edge (version 77 et versions ultérieures) pour Windows 10. Le canal **Stable** est le canal recommandé pour le déploiement à grande échelle de Microsoft Edge pour Windows 10 dans des environnements d’entreprise. Ce canal est mis à jour toutes les six semaines, chaque version intégrant des améliorations du canal **bêta**. En plus des canaux **Stable** et **bêta**, Intune prend en charge un canal **dev**. Pour plus d’informations, consultez [Microsoft Edge pour Windows 10 - Configurer les paramètres de l’application](~/apps/apps-windows-edge.md#configure-app-settings).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Amélioration de l’interface utilisateur lors de la configuration de l’interface utilisateur du connecteur local Exchange ActiveSync<!-- 5695492   -->
Nous avons mis à jour l’expérience de [configuration du connecteur local Exchange ActiveSync](../protect/exchange-connector-install.md). L’expérience mise à jour utilise un seul volet pour configurer, modifier et synthétiser les détails de vos connecteurs locaux. 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Ajouter des paramètres de proxy automatique aux profils Wi-Fi pour les profils professionnels Android Enterprise<!-- 4490822   -->
Vous pouvez créer des profils Wi-Fi sur des appareils avec profil professionnel Android Entreprise. Lorsque vous choisissez le type Wi-Fi d’entreprise, vous pouvez également entrer le type de protocole EAP (Extensible Authentication Protocol) utilisé sur votre réseau Wi-Fi.

Désormais, lorsque vous choisissez le type Entreprise, vous pouvez également entrer des paramètres de proxy automatiques, y compris une URL de serveur proxy, par exemple `proxy.contoso.com`.

Pour afficher les paramètres Wi-Fi actuels que vous pouvez configurer, consultez [Configurer des paramètres Wi-Fi pour des appareils exécutant Android Entreprise et Android Kiosk dans Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

S’applique à :
- Profil professionnel Android Entreprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>Bloquer les inscriptions Android par le fabricant de l’appareil<!--5197392  -->
Vous pouvez empêcher l’inscription des appareils en fonction du fabricant de l’appareil. Cette règle s’applique à l’administrateur d’appareil Android et aux appareils avec profil professionnel Android Enterprise. Pour afficher les restrictions d’inscription, sélectionnez [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Appareils** > **Restrictions d’inscription**.

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>Améliorations apportées à l’interface utilisateur Créer un profil de type d'inscription iOS/iPadOS<!-- 6055005 -->
Pour l’inscription des utilisateurs iOS/iPadOS, la page **Créer un profil de type d’inscription** **Paramètres** a été simplifiée pour améliorer le processus de sélection du **type d’inscription** tout en conservant la même fonctionnalité. Pour afficher la nouvelle interface utilisateur, sélectionnez [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Appareils** > **iOS** > **Inscription iOS** > **Types d’inscription** > **Créer un profil**  > **Paramètres**. Pour en savoir plus, voir [Créer un profil d'inscription des utilisateurs dans Intune](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des périphériques

#### <a name="new-information-in-device-details---4471759-5604099----"></a>Nouvelles informations dans les détails de l’appareil<!-- 4471759 5604099  -->
Les informations suivantes apparaissent maintenant sur la page **Vue d’ensemble** des appareils :
- Capacité de mémoire (quantité de mémoire physique sur l’appareil)
- Capacité de stockage (quantité de stockage physique sur l’appareil) 
- Architecture UC

#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>Action à distance Contourner le verrou d’activation iOS renommée Désactiver le verrouillage d’activation <!--5904591  -->
L’action à distance **Contourner le verrou d’activation** a été renommée **Désactiver le verrouillage d’activation**. Pour plus d’informations, consultez [Désactiver le verrouillage d’activation iOS avec Intune](../remote-actions/device-activation-lock-bypass.md).

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Prise en charge du déploiement des mises à jour de fonctionnalités Windows 10 pour les appareils AutoPilot<!-- 5948137   -->
Intune prend désormais en charge le ciblage d’appareils AutoPilot inscrits à l’aide de [déploiements de mises à jour de fonctionnalités Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates).

Les stratégies de mise à jour des fonctionnalités Windows 10 ne peuvent pas être appliquées au cours de l’expérience OOBE (out of box experience) AutoPilot et s’appliquent uniquement à la première analyse de Windows Update une fois que l’appareil a été provisionné (généralement un jour après).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Rapports de déploiement Windows AutoPilot (préversion) <!-- 3856172   -->
Un nouveau rapport détaille chaque appareil déployé via Windows Autopilot. Pour plus d’informations, consultez [Rapport de déploiement Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>Nouveau gestionnaire de sécurité des points de terminaison avec rôle intégré Intune<!--4253397   -->
Un nouveau rôle intégré Intune est disponible : le gestionnaire de sécurité des points de terminaison. Ce nouveau rôle donne aux administrateurs un accès complet au nœud Gestionnaire des points de terminaison dans Intune et un accès en lecture seule à d’autres zones. Ce rôle est une extension du rôle « Administrateur de la sécurité » d’Azure AD. Si vous avez actuellement des administrateurs généraux en tant que rôles, aucune modification n’est nécessaire. Si vous utilisez des rôles et que vous souhaitez la granularité fournie par le gestionnaire de sécurité des points de terminaison, attribuez alors ce rôle lorsqu’il est disponible. Pour plus d’informations sur les rôles intégrés, consultez [Contrôle d’accès en fonction du rôle](role-based-access-control.md).

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>Semaine du 6 janvier 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>Support de S/MIME pour Microsoft Outlook pour iOS<!-- 2669398 -->
Intune prend en charge la remise de certificats de chiffrement et de signature S/MIME qui peuvent être utilisés avec Outlook pour iOS sur des appareils iOS. Pour plus d’informations, voir [Étiquetage et protection de la confidentialité dans Outlook pour iOS et Android](https://aka.ms/omsmime).

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Mettre en cache le contenu de l’application Win32 à l’aide du serveur Microsoft Connected Cache<!-- 6030314 -->
Vous pouvez installer un serveur Microsoft Connected Cache sur vos points de distribution Configuration Manager pour mettre en cache le contenu de l’application Win32 Intune. Pour plus d’informations, consultez [Cache connecté à Microsoft dans Configuration Manager - Support pour les applications Intune Win32](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>Les profils de modèles d’administration (ADMX) Windows 10 prennent désormais en charge les étiquettes d’étendue de support <!--5137390 -->
Vous pouvez maintenant affecter des étiquettes d’étendue aux profils de modèles d’administration (ADMX). Pour ce faire, accédez à **Intune** > **Appareils** > **Profils de configuration** > choisissez un profil de modèles d’administration dans la liste > **Propriétés** > **Étiquettes d’étendue**. Pour plus d’informations sur les étiquettes d'étendue, consultez [Affecter des étiquettes d’étendue à d’autres objets](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects).

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>Semaine du 30 décembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Récupérer une clé de récupération personnelle à partir d’appareils macOS chiffrés par MEM<!-- 4851745 -->
Les utilisateurs finaux peuvent récupérer leur clé de récupération personnelle (clé FileVault) à l’aide de l’application Portail d'entreprise iOS. L’appareil qui a la clé de récupération personnelle doit être inscrit auprès d’Intune et chiffré avec FileVault via Intune. À l’aide de l’application Portail d’entreprise iOS, un utilisateur final peut récupérer sa clé de récupération personnelle sur son appareil macOS chiffré en cliquant sur **Obtenir la clé de récupération**. Vous pouvez également récupérer la clé de récupération d’Intune en sélectionnant **Appareils** > *l’appareil macOS chiffré et inscrit* > **Obtenir une clé de récupération**. Pour plus d’informations sur FileVault, consultez [Chiffrement FileVault pour macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>Applications VPP avec licences utilisateurs iOS et iPadOS<!-- 5619268 -->
Pour les appareils iOS et iPadOS inscrits par l’utilisateur, les utilisateurs finaux ne seront plus présentés avec les applications VPP sous licence d’appareils nouvellement créées et déployées comme disponibles. Toutefois, les utilisateurs finaux continuent de voir toutes les applications VPP sous licence utilisateur au sein du Portail d’entreprise. Pour plus d’informations sur les applications VPP, consultez [Guide pratique pour gérer les applications iOS et macOS achetées par le biais d’un programme d’achat en volume Apple avec Microsoft Intune](~/apps/vpp-apps-ios.md).

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>Semaine du 23 décembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>Remarque : Windows 10 1703 (RS2) ne sera plus pris en charge <!-- 5026679 -->
À partir du 9 octobre 2018, Windows 10 1703 (RS2) a sorti de la prise en charge des plateformes Microsoft pour les Éditions Familiales, Pro et Pro pour stations de travail. Pour les éditions Windows 10 entreprise et éducation, Windows 10 1703 (RS2) a dépassé la prise en charge de la plateforme le 8 octobre 2019. À compter du 26 décembre 2019, nous allons mettre à jour la version minimale de l’application Windows Portail d’entreprise vers Windows 10 1709 (RS3). Les ordinateurs exécutant des versions antérieures à 1709 ne recevront plus de versions mises à jour pour l’application à partir de Microsoft Store. Nous avons précédemment communiqué ces modifications aux clients qui gèrent des versions plus anciennes de Windows 10 via le centre de messages. Pour plus d’informations, consultez [Fiche technique du cycle de vie Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>Semaine du 16 décembre 2019

### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Mises à jour vers les Modèles d’administration pour les appareils Windows 10 <!-- 5941568 -->

Vous pouvez utiliser des modèles ADMX dans Microsoft Intune pour contrôler et gérer les paramètres de Microsoft Edge, Office et Windows. Des modèles d’administration dans Intune ont effectués les mises à jour de paramètres de stratégie suivantes :

- Ajout de la prise en charge des versions 78 et 79 de Microsoft Edge.
- Comprend les fichiers ADMX du 11 novembre 2019 dans [Fichiers de modèles d’administration (ADMX/ADML) et outil de personnalisation Office pour Office 365 ProPlus, Office 2019 et Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

Pour plus d’informations sur des modèles ADMX dans Intune, consultez [Utiliser des modèles Windows 10 pour configurer les paramètres de stratégie de groupe dans Microsoft Intune](../configuration/administrative-templates-windows.md).

S’applique à :

- Windows 10 et versions ultérieures

## <a name="week-of-december-9-2019-1912-service-release"></a>Semaine du 9 novembre 2019 (mise en production du service 1912)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migration vers Microsoft Edge pour les scénarios de navigation gérés<!-- 5173762 -->
Nous nous rapprochons du retrait d’Intune Managed Browser et nous avons apporté des modifications aux stratégies de protection des applications pour simplifier les étapes nécessaires à la transition de vos utilisateurs vers Edge. Nous avons mis à jour les options du paramètre de stratégie de protection des applications **Restreindre le transfert de contenu web à d’autres applications** pour qu’elles correspondent à :

- N’importe quelle application
- Intune Managed Browser
- Microsoft Edge
- Navigateur non géré 

Lorsque vous sélectionnez **Microsoft Edge**, des messages d’accès conditionnel avertissent vos utilisateurs finaux que Microsoft Edge est requis pour les scénarios de navigation gérés. Ils sont invités à télécharger Microsoft Edge et à s’y connecter avec leurs comptes AAD, s’ils ne l’ont pas encore fait.  Cela revient à avoir ciblé vos applications prenant en charge la gestion MAM avec le paramètre de configuration d’application `com.microsoft.intune.useEdge` défini sur **True**. Les stratégies de protection des applications existantes qui utilisaient le paramètre **Navigateurs gérés par stratégie** ont maintenant le paramètre **Intune Managed Browser** sélectionné, et vous ne verrez aucun changement de comportement. Cela signifie que vos utilisateurs verront des messages les incitant à utiliser Microsoft Edge si vous avez défini le paramètre de configuration d’application **useEdge** sur **True**. Nous encourageons tous les clients qui tirent parti des scénarios de navigation gérés à mettre à jour leurs stratégies de protection des applications avec **Restreindre le transfert de contenu web à d’autres applications** pour s’assurer que les utilisateurs voient les recommandations appropriées de transition vers Microsoft Edge, quelle que soit l’application avec laquelle ils lancent des liens. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation<!-- 2576686  -->
Les stratégies de protection des applications Intune (APP) sur les appareils Android et iOS vous permettent de contrôler le contenu des notifications d’application pour les comptes d’organisation. Vous pouvez sélectionner une option (Autoriser, Bloquer les données de l’organisation ou Bloqué) pour spécifier la façon dont les notifications pour les comptes d’organisation sont affichées pour l’application sélectionnée. Cette fonctionnalité requiert la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge APP. Outlook pour iOS version 4.15.0 (ou ultérieure) et Outlook pour Android 4.83.0 (ou version ultérieure) prend en charge ce paramètre. Le paramètre est disponible dans la console, mais la fonctionnalité prendra effet après le 16 décembre 2019. Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md).

#### <a name="microsoft-app-icons-update--4677605----"></a>Mise à jour des icônes d’application Microsoft<!--4677605  -->
Les icônes utilisées pour les applications Microsoft dans le volet de ciblage de l’application pour les stratégies de protection des applications et les stratégies de configuration des applications ont été mises à jour.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Exiger l’utilisation de claviers approuvés sur Android<!--4761794  -->
Dans le cadre d’une stratégie de protection des applications, vous pouvez spécifier le paramètre [**Claviers approuvés**](../apps/app-protection-policy-settings-android.md#data-protection) pour gérer les claviers Android pouvant être utilisés avec les applications Android managées. Lorsqu’un utilisateur ouvre l’application managée et qu’il n’utilise pas déjà un clavier approuvé pour cette application, il est invité à basculer vers l’un des claviers approuvés déjà installés sur leur appareil. Si nécessaire, ils disposent d’un lien permettant de télécharger un clavier approuvé à partir du Google Play Store, qu’ils peuvent installer et configurer. L’utilisateur ne peut modifier les champs de texte que dans une application managée quand son clavier actif n’est pas l’un des claviers approuvés.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>Expérience d’authentification unique mise à jour pour les applications et sites web sur vos appareils iOS, iPadOS et macOS<!-- 4999578  -->
Intune a ajouté d’autres paramètres d’authentification unique pour les appareils iOS, iPados et macOS. Vous pouvez désormais configurer des extensions d’application SSO de redirection écrites par votre organisation ou par votre fournisseur d’identité. Utilisez ces paramètres pour configurer une expérience d’authentification unique transparente pour les applications et les sites Web qui utilisent des méthodes d’authentification modernes, telles que OAuth et SAML2. 

Ces nouveaux paramètres développent les paramètres précédents pour les extensions d’application SSO et l’extension Kerberos intégrée d’Apple (**Appareils** > **Configuration des appareils** > **Profils** > **Créer un profil** > **iOS/iPados** ou **macOS** pour le type de plate-forme > **Fonctionnalités d’appareil** pour le type de profil). 

Pour afficher la gamme complète des paramètres d’extension d’application SSO que vous pouvez configurer, accédez à [SSO sur iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) et [SSO sur macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

S’applique à :

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>Nous avons mis à jour deux paramètres de restriction d’appareil pour les appareils iOS et iPadOS pour corriger leur comportement<!-- 5701352    -->
Pour les appareils iOS, vous pouvez créer des profils de restriction d’appareil qui **Autorisent les mises à jour PKI à distance** et **Bloquent le mode USB restreint** (**Appareils** > **Configuration d’appareils** > **Profils** > **Créer un profil** > **iOS/iPadOS** pour la plateforme > **Restrictions d’appareil** pour le type de profil). Avant cette mise en production, les paramètres d’interface utilisateur et les descriptions des paramètres suivants étaient incorrects et ont été corrigés. À partir de cette mise en production, le comportement des paramètres est le suivant :

**Bloquer les mises à jour PKI à distance** : **Bloquer** empêche vos utilisateurs de recevoir des mises à jour de logiciel, sauf si l’appareil est connecté à un ordinateur. **Non configuré** (par défaut) : permet à un appareil de recevoir des mises à jour de logiciel sans être connecté à un ordinateur.
- Précédemment, ce paramètre vous permet de le configurer comme suit : **Autoriser**, pour permettre aux utilisateurs de recevoir les mises à jour de logiciel sans avoir à connecter leurs appareils à un ordinateur.
**Autoriser les accessoires USB quand l'appareil est verrouillé** : **Autoriser** permet aux accessoires USB d’échanger des données avec un appareil qui a été verrouillé pendant plus d’une heure. **Non configuré** (par défaut) ne met pas à jour le mode restreint USB sur l’appareil et les accessoires USB ne peuvent pas transférer les données de l’appareil s’ils sont verrouillés pendant plus d’une heure.
- Précédemment, ce paramètre vous permet de le configurer comme suit : **Bloquer** pour désactiver le mode USB restreint sur les appareils supervisés.

Pour plus d’informations sur les paramètres que vous pouvez configurer, consultez [Paramètres des appareils iOS et iPadOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md).

Cette fonctionnalité s’applique à :

- iOS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profils de configuration d’appareil de réseau câblé pour les appareils macOS<!-- 3508686  -->
   > [!NOTE]
   > Cette fonctionnalité a été retardée, mais sera bientôt disponible.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Empêche les utilisateurs de configurer des informations de connexion de certificat dans le magasin de clés managé sur les appareils propriétaires de l’appareil Android Enterprise<!-- 3311998 -->
Sur les appareils de propriétaires de l’appareil Android Enterprise, vous pouvez configurer un nouveau paramètre qui empêche les utilisateurs de configurer leurs informations de connexion dans le magasin de clés managé ( **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour la plateforme > **Propriétaire de l’appareil uniquement > Restrictions d’appareil** pour le type de profil > **Utilisateurs + comptes**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des périphériques

#### <a name="protected-wipe-action-now-available--51150000---"></a>Action de réinitialisation protégée désormais disponible<!--51150000 -->
Vous avez maintenant la possibilité d’utiliser l’action Réinitialiser l’appareil pour effectuer une réinitialisation protégée d’un appareil. Les réinitialisations protégées sont identiques aux réinitialisations standard, à ceci près qu’elles ne peuvent pas être contournées en éteignant l’appareil. Une réinitialisation protégée continuera d’essayer de réinitialiser l’appareil jusqu’à ce que cela réussisse. Dans certaines configurations, cette action peut empêcher l’appareil de redémarrer. Pour plus d’informations, consultez [Retirer ou réinitialiser des appareils](../remote-actions/devices-wipe.md).

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>Adresse MAC Ethernet de l’appareil ajoutée à la page Vue d’ensemble de l’appareil<!--5562275 -->
Vous pouvez maintenant voir l’adresse MAC Ethernet d’un appareil sur la page Détails de l’appareil (**Appareils** > **Tous les appareils** > choisissez un appareil > **Vue d’ensemble**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sécurité des appareils

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>Amélioration de l’expérience sur un appareil partagé quand les stratégies d’accès conditionnel basées sur les appareils sont activées<!-- 1734096  -->
Nous avons amélioré l’expérience sur un appareil partagé avec plusieurs utilisateurs ciblés par la stratégie d’accès conditionnel basée sur les appareils en vérifiant la dernière évaluation de conformité pour l’utilisateur lors de la mise en application de la stratégie. Pour plus d’informations, consultez les articles de vue d’ensemble suivants :
- [Vue d’ensemble de l’accès conditionnel Azure](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Vue d’ensemble de la conformité des appareils Intune](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>Utiliser des profils de certificat PKCS pour approvisionner des appareils avec des certificats<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
Vous pouvez désormais utiliser des profils de certificat PKCS pour émettre des certificats pour des *appareils* qui exécutent Android for Work, iOS/iPadOS et Windows quand ils sont associés à des profils comme des profils pour Wi-Fi et VPN. Auparavant, ces trois plateformes ne prenait en charge que les certificats basés sur l’utilisateur, avec une prise en charge basée sur les appareils limitée à macOS.

> [!NOTE]
> Les profils de certificat PKCS ne sont pas pris en charge avec les profils Wi-Fi. Au lieu de cela, utilisez des profils de certificat SCEP quand vous utilisez un [type EAP](../configuration/wi-fi-settings-windows.md#enterprise-profile).

Pour utiliser un certificat basé sur un appareil, pendant que [la création d’un profil de certificat PKCS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) pour les plateformes prises en charge, sélectionnez **Paramètres**. Vous voyez maintenant le paramètre pour **Type de certificat**, qui prend en charge les options pour Appareil ou Utilisateur.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="centralized-audit-logs--5603185-5697164---"></a>Journaux d’audit centralisés<!--5603185, 5697164 -->
Une nouvelle expérience de journal d’audit centralisée collecte désormais les journaux d’audit de toutes les catégories dans une seule page. Vous pouvez filtrer les journaux pour obtenir les données que vous recherchez. Pour afficher les journaux d’audit, accédez à **Administration des abonnés** > **Journaux d’audit**. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>Informations sur les balises d’étendue incluses dans les détails de l’activité du journal d’audit<!--5763534 -->
Les détails de l’activité du journal d’audit incluent désormais des informations sur les balises d’étendue (pour les objets Intune prenant en charge les balises d’étendue). Pour plus d’informations sur les journaux d’audit, consultez [Utiliser les journaux d’audit pour suivre et surveiller les événements](monitor-audit-logs.md).

<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>Semaine du 2 décembre 2019

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Nouvelle licence de cogestion de Microsoft Endpoint Configuration Manager<!--5027281-->
Les clients Configuration Manager avec Software Assurance peuvent obtenir la cogestion Intune pour les PC Windows 10 sans avoir à acheter de licence Intune supplémentaire pour la cogestion. Les clients n’ont plus besoin d’attribuer des licences Intune/EMS individuelles à leurs utilisateurs finaux pour la cogestion de Windows 10.
- Les appareils gérés par Configuration Manager et inscrits pour la cogestion ont quasiment les mêmes droits que les PC gérés par MDM de manière autonome dans Intune. Toutefois, après réinitialisation, ils ne peuvent pas être reprovisionnés en utilisant Autopilot.
- Les appareils Windows 10 inscrits dans Intune par d’autres moyens demandent des licences Intune complètes.
- Les appareils sur d’autres plateformes nécessitent toujours des licences Intune complètes.

Pour plus d’informations, consultez [Termes des contrats de licence](https://www.microsoft.com/en-us/Licensing/product-licensing/products).

<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>Semaine du 18 novembre 2019 (version 1911)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Mise à jour de l’interface utilisateur lors du nettoyage sélectif des données d’application<!-- 4102028 -->
L’interface utilisateur permettant de réinitialiser de manière sélective les données d’application dans Intune a été mise à jour. Les modifications de l’interface utilisateur incluent :
- Une expérience simplifiée qui s’apparente à un Assistant condensé dans un seul volet.
- Une mise à jour du flux de création pour inclure les affectations.
- Une page récapitulative de tous les éléments définis pendant l’affichage des propriétés, préalablement à la création d’une stratégie ou pendant la modification d’une propriété. Par ailleurs, pendant la modification de propriétés, le récapitulatif présente uniquement la liste des éléments de la catégorie des propriétés modifiées.

Pour plus d’informations, consultez le [Guide pratique pour effacer uniquement les données d’entreprise des applications gérées par Intune](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>Prise en charge des claviers tiers iOS et iPadOS<!-- 4922950 -->
En mars 2019, nous avons annoncé la suppression de la prise en charge du paramètre de stratégie de protection des applications iOS « Claviers tiers ». Cette fonctionnalité est de retour sur Intune avec la prise en charge d’iOS et d’iPadOS. Pour activer ce paramètre, accédez à l’onglet **Protection des données** d’une stratégie de protection des applications iOS/iPadOS nouvelle ou existante, et recherchez le paramètre **Claviers tiers** sous **Transfert de données**.

Le comportement de ce paramètre de stratégie diffère légèrement de l’implémentation précédente. Dans les applications à plusieurs identités utilisant le kit de développement logiciel (SDK) version 12.0.16 et ultérieure, et ciblées par des stratégies de protection des applications avec ce paramètre configuré sur **Bloquer**, les utilisateurs finaux ne pourront pas choisir de claviers tiers dans leurs comptes professionnels et personnels. Les applications qui utilisent le SDK 12.0.12 ou versions antérieures continuent d’exposer le comportement indiqué dans le titre de notre billet de blog, [Problème connu : Les claviers tiers ne sont pas bloqués dans iOS pour les comptes personnels](https://aka.ms/3rdparty_iOS_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configuration de l’appareil

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Cibler des groupes d’utilisateurs macOS pour exiger la gestion par Jamf<!-- 4061739  --> 
Vous pouvez cibler des groupes d’utilisateurs spécifiques qui verront leurs [appareils macOS gérés par Jamf](../protect/conditional-access-integrate-jamf.md). Cela vous permet d’appliquer l’intégration de la conformité Jamf à un sous-ensemble d’appareils macOS tandis que d’autres sont gérés par Intune. Si vous utilisez déjà l’intégration Jamf, tous les utilisateurs seront ciblés pour l’intégration par défaut.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>Nouveaux paramètres Exchange ActiveSync lors de la création d’un profil de configuration d’appareil de messagerie sur les appareils iOS<!-- 4892824   --> 
Sur les appareils iOS/iPadOS, vous pouvez configurer la connectivité de la messagerie dans un profil de configuration d’appareil (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS/iPadOS** pour la plateforme > **E-mail** pour le type de profil). 

De nouveaux paramètres Exchange ActiveSync sont disponibles, notamment :
- **Données Exchange à synchroniser** : Choisissez les services Exchange à synchroniser (ou pour lesquels bloquer la synchronisation) pour Calendrier, Contacts, Rappels, Notes et Messagerie.
- **Autoriser les utilisateurs à modifier les paramètres de synchronisation** : Choisissez d’autoriser ou non les utilisateurs à modifier les paramètres de synchronisation de ces services sur leurs appareils.  

Pour plus d’informations sur ces paramètres, accédez à [Paramètres de profil e-mail pour les appareils iOS dans Intune](../configuration/email-settings-ios.md). 

S’applique à :

- iOS 13.0 et ultérieur
- iPadOS 13.0 et ultérieur

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Empêcher les utilisateurs d’ajouter des comptes Google personnels aux appareils Android Enterprise entièrement gérés et dédiés<!-- 5353228   -->
Sur les appareils Android Enterprise entièrement gérés et dédiés, il existe un nouveau paramètre qui empêche les utilisateurs de créer des comptes Google personnels (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **Android Enterprise** pour la plateforme > **Propriétaire de l’appareil uniquement > Restrictions d’appareil** pour le type de profil > **Paramètres des utilisateurs et des comptes** > **Comptes Google personnels**).

Pour voir les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils Android Entreprise pour autoriser ou restreindre les fonctionnalités à l’aide d’Intune](../configuration/device-restrictions-android-for-work.md).

S’applique à :

- Appareils Android Entreprise complètement gérés
- Appareils dédiés Android Entreprise

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>La journalisation côté serveur pour les commandes de Siri est supprimée dans le profil de restrictions des appareils iOS/iPadOS <!-- 5468501   -->
Sur les appareils iOS et iPadOS, le paramètre la **journalisation côté serveur pour les commandes de Siri** est supprimé de la console d’administration de Microsoft Endpoint Manager (**Configuration de l’appareil** > **Profils** > **Créer un profil** > **iOS/iPadOS** pour la plateforme > **Restrictions d’appareil** pour le type de profil > **Applications intégrées**). 

Ce paramètre n’a aucun effet sur les appareils. Pour supprimer le paramètre des profils existants, ouvrez le profil, apportez une modification quelconque, puis enregistrez le profil. Le profil est mis à jour et le paramètre est supprimé des appareils.

Pour voir tous les paramètres que vous pouvez configurer, accédez à [Paramètres des appareils iOS et iPadOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md).

S’applique à :

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Mises à jour des fonctionnalités Windows 10 (préversion publique)<!-- 2384877 -->
Vous pouvez maintenant déployer des [mises à jour de fonctionnalités Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) sur des appareils Windows 10. Les mises à jour des fonctionnalités de Windows 10 sont une nouvelle stratégie de mise à jour logicielle qui définit la version de Windows 10 que les appareils doivent installer et conserver. Vous pouvez utiliser ce nouveau type de stratégie avec vos anneaux de mise à jour Windows 10 existants.

Les appareils qui reçoivent la stratégie de mises à jour des fonctionnalités de Windows 10 installent la version spécifiée de Windows, puis restent à cette version jusqu’à ce que la stratégie soit modifiée ou supprimée. Les appareils qui exécutent une version ultérieure de Windows restent à leur version actuelle. Les appareils qui sont conservés sur une version spécifique de Windows peuvent toujours installer des mises à jour de qualité et de sécurité pour cette version à partir d’anneaux de mise à jour Windows 10.

Le déploiement de ce nouveau type de stratégie sur les locataires commence cette semaine. Si cette stratégie n’est pas encore à la disposition de votre locataire, elle le sera bientôt.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Ajouter et modifier des informations de clé dans les fichiers plist pour les applications macOS<!-- 4736278 -->
Sur les appareils macOS, vous pouvez maintenant créer un profil de configuration d’appareil qui charge un fichier de liste de propriétés (.plist) associé à une application ou à l’appareil (**Appareils** > **Profils de configuration** > **Créer un profil** > **macOS** pour la plateforme > **Fichier de préférences** pour le type de profil).

Seules certaines applications prennent en charge les préférences gérées, et ces applications peuvent ne pas vous permettre de gérer tous les paramètres. Veillez à charger un fichier de liste de propriétés qui configure les paramètres de canal de l’appareil, et non les paramètres de canal utilisateur.

Pour plus d’informations sur cette fonctionnalité, consultez [Ajouter un fichier de liste de propriétés aux appareils macOS à l’aide de Microsoft Intune](../configuration/preference-file-settings-macos.md).

S’applique à :

- Appareils macOS exécutant la version 10.7 ou une version ultérieure

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestion des périphériques

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Modifier la valeur du nom de l’appareil pour les appareils AutoPilot<!-- 2640074 -->
Vous pouvez modifier la valeur du nom de l’appareil pour les appareils AutoPilot joints à Azure AD.  Pour plus d’informations, consultez [Modifier les attributs d’un appareil Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Modifier la valeur de balise de groupe pour les appareils AutoPilot<!-- 4816775   -->
Vous pouvez modifier la valeur de balise de groupe pour les appareils AutoPilot. Pour plus d’informations, consultez [Modifier les attributs d’un appareil Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="updated-support-experience---5012398---"></a>Mise à jour de l’expérience de support<!-- 5012398 -->

À partir d’aujourd’hui, une expérience mise à jour et rationalisée dans la console pour [obtenir de l’aide et du support pour Intune](get-support.md) est déployée sur les locataires. Si cette nouvelle expérience n’est pas encore à votre disposition, elle le sera bientôt.

Nous avons amélioré la recherche dans la console et les commentaires concernant les problèmes courants, ainsi que le workflow à suivre pour contacter le support. En ouvrant un problème de support, vous verrez apparaître une estimation en temps réel du délai d’attente à prévoir pour un rappel ou une réponse par e-mail ; les clients du Support Premier et du Support Unifié pourront facilement indiquer la gravité de leur problème afin de bénéficier d’un support plus rapide.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Amélioration de l’expérience de création de rapports Intune (préversion publique) <!-- 3791418 -->
Intune offre désormais une meilleure expérience de création de rapports, avec notamment de nouveaux types de rapports, une meilleure organisation des rapports, des vues plus ciblées, des fonctionnalités de rapport améliorées, ainsi que des données plus cohérentes et ponctuelles. Les nouveaux types de rapport se concentrent sur les éléments suivants :
- **Opérationnel** : fournit des enregistrements actualisés en se concentrant sur les éléments d’intégrité négatifs. 
- **Organisationnel** : fournit un résumé plus large de l’état global.
- **Historique** : fournit les modèles et tendances sur une période donnée.
- **Spécialiste** : vous permet d’utiliser des données brutes pour créer vos propres rapports personnalisés.

Le premier ensemble de nouveaux rapports se concentre sur la conformité des appareils. Pour plus d’informations, consultez [Blog - Infrastructure de création de rapports Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) et [Rapports Intune](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Contrôle d'accès en fonction d'un rôle

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Dupliquer des rôles personnalisés ou intégrés <!-- 1081938   -->
Vous pouvez maintenant copier des rôles intégrés ou personnalisés. Pour plus d’informations, voir [Copier un rôle](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>Nouvelles autorisations pour le rôle d’administrateur scolaire <!-- 5621805  -->  
Deux nouvelles autorisations, **Affecter le profil** et **Synchroniser l’appareil**, ont été ajoutées au rôle d’administrateur scolaire > **Autorisations** > **Programmes d’inscription**. L’autorisation de profil de synchronisation permet aux administrateurs de groupe de synchroniser les appareils Windows AutoPilot. L’autorisation Affecter le profil permet de supprimer les profils d’inscription Apple initiés par l’utilisateur. Il leur donne également l’autorisation de gérer les affectations d’appareils AutoPilot et les affectations de profils de déploiement AutoPilot. Pour obtenir la liste de toutes les autorisations d’administrateur scolaire/administrateur de groupe, consultez [Assigner des administrateurs de groupe](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Sécurité

#### <a name="bitlocker-key-rotation---2564951----"></a>Rotation de clés BitLocker<!-- 2564951  -->
Vous pouvez utiliser une action d’appareil Intune pour [faire pivoter les clés de récupération BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) à distance pour les appareils gérés qui exécutent Windows version 1909 ou ultérieure. Pour pouvoir faire pivoter les clés de récupération, les appareils doivent être configurés pour prendre en charge la rotation des clés de récupération.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>Mises à jour pour l’inscription d’appareils dédiés pour prendre en charge le déploiement de certificats d’appareil SCEP <!-- 5198878  -->
Intune, prend désormais en charge le déploiement de certificats d’appareil SCEP sur les appareils Android Enterprise dédiés pour activer l’accès par certificat aux profils Wi-Fi. L’application Microsoft Intune doit être présente sur l’appareil pour que le déploiement fonctionne. Par conséquent, nous avons mis à jour l’expérience d’inscription pour les appareils Android Enterprise dédiés. Les nouvelles inscriptions commencent toujours de la même façon (avec code QR, NFC, Zero Touch ou identificateur d’appareil), mais ont à présent une étape qui requiert que les utilisateurs installent l’application Intune. Les appareils existants commenceront progressivement à installer l’application, de façon automatique.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>Journaux d’audit Intune pour la collaboration interentreprises<!--5670211 -->
La collaboration B2B Azure AD vous permet de partager en toute sécurité les applications et services de votre entreprise avec des utilisateurs invités à partir de n’importe quelle autre organisation, tout en conservant le contrôle sur vos propres données d’entreprise. Intune prend désormais en charge les journaux d’audit pour les utilisateurs invités B2B. Par exemple, lorsque les utilisateurs invités apportent des modifications, Intune peut capturer ces données par le biais des journaux d’audit. Pour plus d’informations, consultez [Qu’est-ce que l’accès utilisateur invité dans Azure Active Directory B2B ?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)

<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>Semaine du 11 novembre 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestion des applications  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Amélioration de l’expérience d’inscription macOS dans Portail d’entreprise <!-- 5074349  -->  
L’expérience d’inscription pour l’application Portail d’entreprise macOS a un processus d’inscription plus simple, qui est plus proche de l’expérience d’inscription de Portail d’entreprise iOS. Maintenant, les utilisateurs de l'appareil bénéficient des caractéristiques et des fonctionnalités suivantes :  

* Interface utilisateur épurée.  
* Liste de contrôle d’inscription améliorée.  
* Instructions plus claires sur la façon d’inscrire leurs appareils.  
* Amélioration des options de résolution des problèmes.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Lancement des applications web à partir de l’application Windows Portail d’entreprise<!-- 5030972 -->
Les utilisateurs finaux peuvent désormais lancer des applications web directement à partir de l’application Windows Portail d’entreprise. Les utilisateurs finaux peuvent sélectionner l’application web, puis choisir l’option **Ouvrir dans le navigateur**. L’URL web publiée est ouverte directement dans un navigateur web. Cette fonctionnalité sera déployée au cours de la semaine prochaine. Pour plus d’informations sur les d’applications web, consultez [Ajouter des applications web à Microsoft Intune](~/apps/web-app.md).  

#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Nouvelle colonne de type d’attribution dans Portail d’entreprise pour Windows 10 <!-- 5459950  -->
La colonne Portail d’entreprise > **Applications installées** > **Type d’affectation** a été renommée **Obligatoire par votre organisation**.  Dans cette colonne, les utilisateurs voient une valeur **Oui** ou **Non** pour indiquer qu’une application est obligatoire ou rendue facultative par leur organisation. Ces modifications ont été apportées suite à une confusion d’utilisateurs des appareils concernant le concept des applications disponibles. Vos utilisateurs peuvent trouver plus d’informations sur l’installation des applications de Portail d’entreprise dans [Installer et partager des applications sur votre appareil](/intune-user-help/install-apps-cpapp-windows). Pour plus d’informations sur la configuration de l’application Portail d’entreprise pour vos utilisateurs, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Semaine du 4 novembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sécurité des appareils

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Les bases de référence de sécurité sont prises en charge dans Microsoft Azure Government<!-- 4062552 -->

Les instances d’Intune hébergées sur *Microsoft Azure Government* peuvent désormais utiliser des [bases de référence de sécurité](../protect/security-baselines.md) pour vous aider à sécuriser et à protéger vos utilisateurs et appareils.

## <a name="whats-new-archive"></a>Archive des nouveautés
Pour consulter les mois précédents, reportez-vous à l’[archive des nouveautés](whats-new-archive.md).

## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]


