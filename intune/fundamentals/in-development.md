---
title: En développement - Microsoft Intune
titleSuffix: ''
description: Fonctionnalités de Microsoft Intune en développement
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 009b9cf22bcdd73eb563c772cc9995047f05a9c1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735764"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>En développement pour Microsoft Intune - Octobre 2019

Pour faciliter votre préparation et votre planification, cette page liste les mises à jour et les fonctionnalités de l’interface utilisateur Intune qui sont en cours de développement, mais qui ne sont pas encore publiées. De plus :

- Si nous pensons que vous devez effectuer une action avant une modification, nous publierons un billet supplémentaire sur le Centre de messages Office.
- Quand une fonctionnalité est lancée en production, en préversion ou en disponibilité générale, la description de la fonctionnalité disparaît de cette page et de la [page Nouveautés](whats-new.md).
- Cette page et la [page Nouveautés](whats-new.md) sont mises à jour régulièrement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.
- Reportez-vous à la [feuille de route M365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) pour les livrables et les chronologies stratégiques.

> [!Note]
> Ces éléments reflètent les attentes actuelles de Microsoft sur les fonctionnalités Intune qui apparaîtront dans une version future. Les dates et les fonctionnalités individuelles peuvent changer. Certains éléments en développement n’ont pas de description de fonctionnalité sur cette page.

**Flux RSS** : recevez une notification quand cette page est mise à jour en copiant et collant l’URL suivante dans votre lecteur de flux : `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestion d'applications

### <a name="additional-app-configuration-variable-available----4969237----"></a>Variable de configuration d’application supplémentaire disponible <!-- 4969237  -->
Lorsque vous créez une stratégie de configuration des applications, vous pouvez inclure la variable de configuration `AAD Device ID` dans le cadre de vos paramètres de configuration. Dans Intune, sélectionnez **Applications clientes** > **Stratégies de configuration des applications** > **Ajouter**. Entrez les détails de votre stratégie de configuration, puis sélectionnez **paramètres** de configuration pour afficher le panneau **paramètres de configuration** .

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>Mode sombre pour iOS Portail d’entreprise <!-- 4911422  -->
Le mode sombre est prévu pour le Portail d’entreprise iOS. Téléchargez des applications d’entreprise, gérez vos appareils et bénéficiez d’un support informatique dans le modèle de couleurs de votre choix. Pour plus d’informations sur le portail d’entreprise iOS, consultez [Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune](../apps/company-portal-app.md).

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Empêcher l’installation d’applications à partir de sources inconnues sur des appareils d’entreprise Android <!-- 4760025  -->
Pour un appareil Android Enterprise Work Profile, il n’est jamais possible pour les utilisateurs finaux d’installer des applications provenant de sources inconnues dans le profil professionnel. Vous pouvez également étendre cette restriction sur le profil personnel également. Si vous activez cette restriction, les utilisateurs finaux sur les appareils Android Enterprise Work Profile sont également empêchés de charger des applications à partir de sources inconnues sur le côté personnel de leur appareil. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>Mettre à jour l’interface utilisateur de la protection des applications et l’interface utilisateur d’approvisionnement d’application iOS <!-- 4102027, 4102029  -->
L’interface utilisateur permettant de créer et de modifier des stratégies de protection des applications et des profils de provisionnement d’application iOS dans Intune sera mise à jour. Les modifications de l’interface utilisateur incluent :
- Une expérience simplifiée à l’aide d’un format de style Assistant condensé au sein d’un même panneau. 
- Une mise à jour du Flow créer pour inclure des affectations.
- Page récapitulative de tous les éléments définis lors de l’affichage des propriétés, avant la création d’une nouvelle stratégie ou lors de la modification d’une propriété. En outre, lorsque vous modifiez des propriétés, le résumé affiche uniquement une liste des éléments de la catégorie des propriétés en cours de modification.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>Créer des groupes d’objets de gestion appelés ensembles de stratégies <!-- 3762880  -->
Les ensembles de stratégies vous permettent de créer un ensemble de références à des entités de gestion existantes qui doivent être identifiées, ciblées et surveillées comme une seule unité conceptuelle. Les ensembles de stratégies ne remplacent pas les concepts ou les objets existants. Un administrateur peut continuer à assigner des objets individuels comme c’est le cas aujourd’hui. Les objets individuels sont référencés par un ensemble de stratégies. Par conséquent, toute modification apportée à ces objets individuels sera reflétée dans l’ensemble de stratégies.  Dans Intune, vous allez sélectionner **ensembles de stratégies** > **créer** pour créer un ensemble de stratégies. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Applications Win32 sur des appareils Windows 10 en mode S <!-- 3747604  --> 
Vous pouvez installer et exécuter des applications Win32 sur des appareils gérés par le mode S de Windows 10. Vous pouvez créer une ou plusieurs stratégies supplémentaires pour le mode S à l’aide des outils Windows Defender application Control (WDAC) PowerShell. Signez les stratégies supplémentaires avec le portail de signature Device Guard, puis chargez et distribuez les stratégies via Intune. Dans Intune, vous trouverez cette fonctionnalité en sélectionnant **applications clientes** > **stratégies supplémentaires Windows 10 S**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Définir la disponibilité de l’application en fonction d’une date et d’une heure <!-- 3510685  -->
En tant qu’administrateur, vous pouvez configurer l’heure de début et l’échéance d’une application requise. À l’heure de début, l’extension de gestion Intune démarre le téléchargement du contenu de l’application et le met en cache. L’application sera installée à l’heure d’échéance. Pour les applications disponibles, l’heure de début indiquera quand l’application sera visible dans Portail d’entreprise. Dans Intune, sélectionnez **Applications clientes** > **Applications**. Sélectionnez ensuite une application spécifique dans la liste ou cliquez sur **Ajouter** pour ajouter une nouvelle application. Dans le panneau de l’application, sélectionnez **affectations** > **Ajouter un groupe**. Définissez le **type d’affectation** sur **obligatoire** , puis sélectionnez **groupes inclus**. Définissez **rendre cette application obligatoire pour tous les utilisateurs** sur **Oui** , puis sélectionnez **modifier** pour modifier les options de l' **expérience utilisateur final** . Dans le panneau **expérience utilisateur final** , définissez le **temps disponible du logiciel** en fonction des besoins. Pour plus d’informations sur l’ajout d’applications, consultez [Ajouter des applications à Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Exiger le redémarrage des applications Win32 <!-- 3136567  -->
Vous serez en mesure de demander qu’une application Win32 doive redémarrer après une installation réussie. En outre, vous pourrez choisir la durée (la période de grâce) avant le redémarrage.

### <a name="company-portal-app-on-windows----1808082----"></a>Application Portail d’entreprise sur Windows <!-- 1808082  -->
L’application Portail d’entreprise sur les appareils Windows est mise à jour pour afficher les notifications Toast aux utilisateurs, même lorsque l’application est fermée. La mise à jour affichera uniquement les notifications pour les applications disponibles lorsque l’état d’installation est terminé ou a échoué. L’application Portail d’entreprise n’affichera pas les notifications pour les applications requises.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>Portail d’entreprise les messages d’état d’installation de l’application <!-- 2514416  -->
L’application Portail d’entreprise affiche des messages d’état d’installation d’application supplémentaires pour les utilisateurs finaux. Les conditions suivantes s’appliquent aux nouvelles fonctionnalités de dépendance Win32 :
- Échec d’installation de l’application. Les dépendances définies par l’administrateur n’ont pas été satisfaites.
- L’application a été correctement installée mais nécessite un redémarrage.
- L’application est en cours d’installation, mais nécessite un redémarrage pour continuer.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>Affecter Microsoft Edge Beta pour macOS <!-- 4678761  -->
Vous pourrez ajouter et affecter la dernière version de Microsoft Edge Beta à Intune pour les appareils macOS. Dans Intune, sélectionnez **applications clientes** > **applications** > **Ajouter une application** > **Microsoft Edge-MacOS**. Ensuite, affectez la version bêta de Microsoft Edge aux groupes prévus. Microsoft AutoUpdate (MAU) assure la mise à jour de Microsoft Edge. Pour plus d’informations sur Microsoft Edge, consultez [gérer l’accès Web à l’aide de Microsoft Edge avec Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurer le contenu de la notification d’application pour les comptes d’organisation <!-- 2576686 -->
Les stratégies de protection des applications Intune (application) sur les appareils Android et iOS vous permettront de contrôler le contenu des notifications d’application pour les comptes d’organisation. Cette fonctionnalité nécessite la prise en charge des applications et peut ne pas être disponible pour toutes les applications prenant en charge l’application. Pour plus d’informations sur APP, consultez [Que sont les stratégies de protection des applications ?](../apps/app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Application Google Play disponible créant des rapports pour des profils professionnels Android <!-- 3041956  -->
Pour les installations d’applications disponibles sur les appareils avec profil professionnel Android, vous pouvez afficher l’état d’installation des applications, ainsi que la version installée des applications Google Play managées. Pour plus d’informations, consultez [Guide pratique pour superviser les stratégies de protection des applications](../apps/app-protection-policies-monitor.md), [Gérer les appareils avec profil professionnel Android avec Intune](../enrollment/android-enterprise-overview.md) et [Type d’application Google Play gérée](../apps/apps-add-android-for-work.md#managed-google-play-app-types).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configuration des appareils


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>Nouveaux paramètres de configuration d’appareil pour les appareils iOS et iPad supervisé <!-- 5199328  -->
Sur les appareils iOS et iPados, vous pouvez créer un profil pour restreindre les fonctionnalités et les paramètres sur les appareils (configuration de l'**appareil** > **profils** > **créer un profil** > **iOS/ipados** pour l’appareil Platform >  **restrictions** pour le type de profil). Vous pouvez contrôler les nouveaux paramètres suivants : 
- Accès à un lecteur réseau dans l’application fichiers  
- Accès à un lecteur USB dans l’application fichiers 
- Wi-Fi toujours activé 

Pour voir les paramètres actuels, accédez à [Paramètres des appareils iOS pour autoriser ou restreindre les fonctionnalités avec Intune](../configuration/device-restrictions-ios.md).

S’applique à :
- iOS 13.0 et ultérieur
- iPadOS 13.0 et ultérieur

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>La valeur connexion automatique est supprimée dans les profils Wi-Fi sur Android et Android Enterprise <!-- 5021055  -->
Sur les appareils Android et Android Enterprise, vous pouvez créer un profil Wi-Fi pour configurer différents paramètres **(configuration**de l’appareil  > **profils** > **créer un profil** > **Android** ou **Android Enterprise** pour la plateforme > **Wi-Fi pour le** type de profil). Le paramètre **connexion automatique** sera supprimé, car il n’est [pas pris en charge par Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Si vous utilisez ce paramètre dans un profil Wi-Fi, vous remarquerez peut-être que la connexion ne fonctionnera pas **automatiquement** . Vous n’avez pas besoin d’effectuer aucune action, mais sachez que ce paramètre est supprimé de l’interface utilisateur Intune.

Pour afficher les paramètres actuels, accédez à [paramètres Wi-fi Android](../configuration/wi-fi-settings-android.md) ou [paramètres Wi-Fi d’Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

S’applique à :
- Android
- Android Entreprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Créer un proxy HTTP global sur des appareils Android Enterprise propriétaire d’appareils <!-- 4816339  -->
Sur les appareils Android Enterprise, vous pouvez créer un profil VPN avec différents clients VPN (configuration de l'**appareil** > **profils** > **créer un profil** > **Android Enterprise** pour la plateforme > propriétaire de l' **appareil > Restrictions d’appareil** pour le type de profil > **connectivité**). Vous pourrez configurer un proxy HTTP global pour répondre aux normes de navigation Web de votre organisation. Toutes les applications qui accèdent aux sites Web HTTP utilisent ce proxy.

S’applique à :
- Propriétaire d’appareil Android Entreprise

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Nouveau profil d’interface de configuration du microprogramme de l’appareil pour les appareils Windows 10 et versions ultérieures <!-- 2266073  -->
Sur Windows 10 et versions ultérieures, vous pouvez créer un profil de configuration d’appareil pour contrôler les paramètres et les fonctionnalités (configuration de l'**appareil** > **profils** > **créer un profil** > **Windows 10 et versions ultérieures** pour la plateforme). Il y aura un nouveau type de profil d’interface de configuration du microprogramme de l’appareil qui permet à Intune de gérer les paramètres UEFI (BIOS).

Pour obtenir une vue d’ensemble de tous les paramètres que vous pouvez configurer, consultez [appliquer des fonctionnalités et des paramètres sur vos appareils à l’aide de profils d’appareil dans Microsoft Intune](../configuration/device-profiles.md).

S’applique à :
- Windows 10 RS5 (1809) et versions ultérieures sur certains fabricants d’ordinateurs OEM

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>Certificats PKCS pour macOS  <!-- 1333650                -->
Nous allons ajouter une prise en charge complète des certificats PKCS sur les appareils qui exécutent macOS. Les utilisateurs seront en mesure de déployer des certificats d’utilisateur et d’appareil avec des champs objet de personnalisation et autre nom de l’objet. Nous aurons également un nouveau paramètre autoriser l’accès à toutes les applications, ce qui permet à toutes les applications associées d’accéder à la clé privée. Pour plus d’informations sur ce paramètre, consultez la documentation Apple suivante : https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>Informations d’identification dérivées pour approvisionner des appareils mobiles avec des certificats      <!--  1736036, 1736037, 1772050      --> 
Nous allons ajouter la prise en charge des informations d’identification dérivées, qui prennent en charge la norme *NIST (National Institute of Standards and Technology) 800-157* pour le déploiement de certificats sur les appareils.  Les informations d’identification dérivées reposent sur l’utilisation d’une carte de vérification de l’identité personnelle (PIV) ou d’une carte d’accès courant (CAC), comme une carte à puce. Les utilisateurs s’authentifient avec leur carte à puce sur un ordinateur, puis soumettent une demande de certificat pour leur appareil géré en suivant le processus requis par le fournisseur d’informations d’identification dérivé.   

Le processus d’utilisation des informations d’identification dérivées pour obtenir un certificat est différent de celui des profils de certificat SCEP ou PKCS, mais le résultat final est le même : les appareils mobiles avec des certificats pour l’authentification qui peuvent être utilisés pour l’authentification d’application, VPN, Wi-Fi ou e-mail. profils.   

Pour plus d’informations, consultez [informations d’identification PIV dérivées](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) sur www.nccoe.nist.gov.

La version initiale des informations d’identification dérivées prendra en charge Entrust Datacard, intercéder et DISA purebred sur iOS. Des plateformes et des fournisseurs d’informations d’identification dérivés supplémentaires seront pris en charge dans les versions ultérieures.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Inscription des appareils

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>Spécifier les versions de système d’exploitation de l’appareil Android inscrites avec le profil professionnel ou l’inscription de l’administrateur de l’appareil <!-- 4350697 -->
À l’aide des restrictions de type d’appareil Intune, vous pouvez utiliser la version du système d’exploitation de l’appareil pour spécifier les appareils utilisateur qui vont utiliser l’inscription au profil professionnel Android Enterprise ou l’inscription de l’administrateur des appareils Android. Pour ce faire, accédez à **Intune** > **inscription d’appareils** > **restrictions d’inscription** >  créer une**restriction** >  restriction de**type d’appareil** > **paramètres de plateforme**.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Modifier la valeur du nom de l’appareil pour les appareils AutoPilot <!-- 4816775 -->
Vous pouvez modifier la valeur du nom de l’appareil pour les appareils AutoPilot Azure AD joints. Pour ce faire, accédez à **Intune** > **inscription d’appareils** > **inscription Windows** > **appareils** **Windows autopilot** >  > Choisissez l’appareil > modifier la valeur du nom de l’appareil dans le volet droit > **Enregistrer** .

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>Pour les appareils iOS, personnalisez l’écran de confidentialité du processus d’inscription du Portail d’entreprise <!-- 4394993  -->
À l’aide de Markdown, vous pourrez personnaliser l’écran de confidentialité du Portail d’entreprise que les utilisateurs finaux voient lors de l’inscription à iOS. Plus précisément, vous serez en mesure de personnaliser la liste des éléments que votre organisation ne peut pas voir ou faire sur l’appareil.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestion des appareils


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Modifier la valeur de balise de groupe pour les appareils AutoPilot<!-- 4816775 -->
Vous pouvez modifier la valeur de balise de groupe pour les appareils AutoPilot. Pour ce faire, accédez à **Intune** > **inscription d’appareils** > **inscription Windows** > **appareils** **Windows autopilot** >  > Choisissez l’appareil > changer la valeur de balise de groupe dans le volet droit > **Enregistrer** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Mise à jour de l’IU pour la création et la modification des anneaux de mise à jour Windows 10  <!-- 4099089          -->   
Nous allons déployer une expérience d’interface utilisateur de création et de modification mise à jour pour les anneaux de mise à jour Windows 10 pour Intune.  Les modifications apportées à l’interface utilisateur sont les suivantes :  
- Simplifiez l’expérience existante en utilisant un format de style Assistant condensé au sein d’un même panneau. Cette mise à jour de l’interface utilisateur va à l’écart avec la prolifération des lames qui oblige les professionnels de l’informatique à explorer les parcours des lames.   
- Révisez le processus de création pour inclure des affectations.  
- Ajout d’une page résumée de tous les éléments définis lors de l’affichage des propriétés, avant la création d’un anneau de mise à jour et lors de la modification d’une propriété. Lors de la modification, la synthèse affiche uniquement la liste des éléments définis dans une catégorie de propriétés en cours de modification.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>Mise à jour de l’interface utilisateur pour la création et la modification des mises à jour logicielles iOS  <!-- 4099090        -->   
Nous allons déployer une expérience d’interface utilisateur de création et de modification mise à jour pour les mises à jour logicielles iOS sur Intune. Les modifications apportées à l’interface utilisateur sont les suivantes :
- Simplifiez l’expérience existante en utilisant un format de style Assistant condensé au sein d’un même panneau. Cette mise à jour de l’interface utilisateur va à l’écart avec la prolifération des lames qui oblige les professionnels de l’informatique à explorer les parcours des lames.  
- La stratégie de mise à jour logicielle iOS créer un Flow sera mise à jour pour inclure les affectations 
- La stratégie de mise à jour logicielle iOS inclut une page récapitulative de tous les éléments définis lors de l’affichage des propriétés, avant la création d’une nouvelle stratégie et lors de la modification d’une propriété. Lors de la modification, la synthèse affiche uniquement la liste des éléments définis dans une catégorie de propriétés en cours de modification.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Cibler des groupes d’utilisateurs macOS pour exiger la gestion de JAMF <!-- 4061739 -->
Vous pourrez cibler des groupes d’utilisateurs spécifiques pour exiger que leurs appareils macOS soient gérés par JAMF. Cette cible vous permet d’appliquer l’intégration de la conformité JAMF à un sous-ensemble d’appareils macOS, tandis que d’autres appareils continuent d’être gérés par Intune. Elle vous permet également de migrer progressivement les appareils des utilisateurs d’un MDM vers l’autre.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Nouvelles restrictions pour le changement de nom des appareils Windows <!-- 3478938 -->
Les noms des appareils doivent respecter les règles suivantes :
- 15 caractères ou moins (doit être inférieur ou égal à 63 octets, à l’exclusion de la valeur NULL de fin)
- Chaîne non null ou vide
- ASCII : lettres (a-z, A-Z), nombres (0-9) et traits d’Union autorisés
- Unicode autorisé : caractères > = 0x80, doit être un UTF8 valide, doit être un mappage IDN (RtlIdnToNameprepUnicode a été correctement mappé). consultez la RFC 3492.
- Les noms ne doivent pas contenir uniquement des chiffres ou commencer par un chiffre
- Aucun espace dans le nom
- Caractères non autorisés : {|} ~ [\] ^ ' :; < = >? & @ ! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Déployer des mises à jour logicielles sur des appareils macOS <!-- 3194876 -->
Vous serez en mesure de déployer des mises à jour logicielles sur des groupes d’appareils macOS. Cette fonctionnalité comprend des mises à jour critiques, de microprogramme, de fichier de configuration et autres. Vous pouvez envoyer des mises à jour lors de l’archivage suivant de l’appareil ou sélectionner une planification hebdomadaire pour déployer les mises à jour dans ou les fenêtres hors temps que vous définissez. Cette fonctionnalité vous aide quand vous souhaitez mettre à jour des appareils en dehors des heures de travail standard ou lorsque votre support technique est entièrement personnel. Vous obtiendrez également un rapport détaillé de tous les appareils macOS avec les mises à jour déployées. Vous pouvez affiner le rapport en fonction de l’appareil pour afficher les États des mises à jour particulières.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>Page vue d’ensemble des nouveaux rapports Android sur les appareils <!-- 2984353  -->
Nous allons ajouter un nouveau rapport à la page vue d’ensemble des appareils qui indique le nombre d’appareils Android inscrits dans chaque solution de gestion des appareils. Ce graphique montre le nombre d’appareils inscrits sur le profil professionnel, entièrement géré, dédié et administrateur de l’appareil. Pour afficher le rapport, choisissez **Intune** > **appareils** > **vue d’ensemble**.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Programme de déploiement Windows AutoPilot <!-- 3856172  -->
Un nouveau rapport détaillera chaque appareil déployé via Windows AutoPilot. Ces données seront disponibles pendant 30 jours après le déploiement. Pour afficher le rapport, accédez à **Intune** > **inscription d’appareils** > **analyser** > **déploiements automatiques**.

### <a name="updated-support-experience-------5012398------"></a>Expérience de support mise à jour   <!--  5012398    -->
Dans le cadre des améliorations continues, nous mettons à jour l’expérience de prise en charge dans la console pour Intune.  Nous allons améliorer la recherche et les commentaires dans la console pour les problèmes courants et rationaliser le flux de travail pour contacter le support technique.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Remarques

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.




