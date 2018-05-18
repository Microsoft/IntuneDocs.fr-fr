---
title: Nouveautés de Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Découvrez les nouveautés du portail Intune Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/02/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 9004441a41c5e7458447b5c5f7e1d91e630bd412
ms.sourcegitcommit: 2b5d88c434bda7f1cdc32d1ccacc6b341a9a399b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Nouveautés de Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Découvrez les nouveautés hebdomadaires dans Microsoft Intune. Vous pouvez également découvrir les [modifications à venir](#whats-coming), les [avis importants](#notices) sur le service et des informations sur les [versions précédentes](whats-new-archive.md). Le lancement de certaines fonctionnalités peut s’étaler sur plusieurs semaines. Ces fonctionnalités risquent de ne pas être accessibles à tous les clients la première semaine.

> [!Note]
> Pour plus d’informations sur les nouvelles fonctionnalités de gestion des appareils mobiles (MDM) hybride, consultez la page sur les [nouveautés de la gestion hybride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### App management
  ### Device enrollment
  ### Device management
  ### Device configuration
  ### Intune apps
  ### Monitor and troubleshoot
  ### Role-based access control

-->   

## <a name="week-of-may-7-2018"></a>Semaine du 7 Mai 2018

### Gestion des applications

#### Prise en charge de l'inscription mobile Samsung Knox <!--1112863-->

Lorsque vous utilisez Intune avec Samsung Knox Mobile Enrollment (KME), vous pouvez enregistrer un nombre important d'appareils Android appartenant à l'entreprise. Les utilisateurs connectés au réseau Wi-Fi ou cellulaire peuvent s'inscrire en quelques clics lorsqu'ils démarrent leur appareil pour la première fois. Lorsque vous utilisez l'application de déploiement Knox, les périphériques peuvent être inscrits via Bluetooth ou NFC. Pour plus d'informations, consultez la documentation pour configurer Intune avec Samsung KME [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md).

#### Effectuer une demande de support via le portail de l'entreprise pour Windows 10 <!-- 1874137 -->

Le portail d'entreprise pour Windows 10 envoie désormais les journaux d'application directement à Microsoft lorsque l'utilisateur initie le processus pour obtenir de l'aide sur un problème. Cela facilitera le dépannage et la résolution des problèmes remontés à Microsoft.

## <a name="week-of-april-23-2018"></a>Semaine du 23 avril 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Prise en charge des codes secrets pour les codes PIN MAM sur Android<!-- 1438086 -->

Les administrateurs Intune peuvent définir une condition de lancement d’application pour appliquer un code secret au lieu d’un code PIN MAM numérique. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Intune prend en charge un code secret comme le code PIN numérique existant, pouvant définir une longueur minimale et autorisant la répétition des caractères et des séquences par le biais de la console d’administration. Cette fonctionnalité nécessite la version la plus récente du Portail d’entreprise sur Android. Cette fonctionnalité est déjà disponible pour iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Prise en charge des applications métier pour macOS <!-- 1473977 -->
Microsoft Intune permettra d’installer des applications métier macOS à partir du portail Azure. Vous pourrez ajouter une application métier macOS à Intune après qu’elle a été prétraitée par l’outil disponible dans GitHub. Dans le portail Azure, choisissez **Applications mobiles** à partir du panneau **Intune**. Dans le panneau **Applications mobiles**, choisissez **Applications** > **Ajouter**. Dans le panneau **Ajouter une application**, sélectionnez **Application métier**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Intégration des groupes Tous les utilisateurs et Tous les appareils pour l’affectation d’applications Android for Work (AFW) <!-- 1813073 -->
Vous pouvez tirer parti des groupes intégrés **Tous les utilisateurs** et **Tous les appareils** pour l’affectation d’applications AFW. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune réinstalle les applications nécessaires qui sont désinstallées par les utilisateurs <!-- 1947010 -->
Si un utilisateur final désinstalle une application obligatoire, Intune la réinstalle automatiquement en moins de 24 heures au lieu d’attendre le cycle de réévaluation de 7 jours.

### <a name="device-configuration"></a>Configuration des appareils

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Le graphique des profils d’appareil et la liste d’états affichent tous les appareils contenus dans un groupe <!-- 1449153 eeready -->
Quand vous configurez un profil d’appareil (**Configuration de l’appareil** > **Profils**), vous choisissez le profil d’appareil, par exemple iOS. Vous affectez ce profil à un groupe qui inclut les appareils iOS et les appareils non-iOS. Le nombre sur le graphique indique que le profil est appliqué aux appareils iOS *et* non-iOS (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble**). Quand vous sélectionnez le graphique sous l’onglet **Vue d’ensemble**, la section **État de l’appareil** liste tous les appareils contenus dans le groupe, au lieu des appareils iOS uniquement. 

Avec cette mise à jour, le graphique (**Configuration de l’appareil** > **Profils** > sélectionnez un profil existant > **Vue d’ensemble**) affiche uniquement le nombre associé à un profil d’appareil spécifique. Par exemple, si le profil d’appareil de la configuration s’applique aux appareils iOS, le graphique indique uniquement le nombre des appareils iOS. Quand l’utilisateur sélectionne le graphique et ouvre la section **État de l’appareil**, seuls les appareils iOS sont listés.

Le graphique utilisateur est supprimé le temps que cette mise à jour soit effectuée. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN Always On pour Windows 10 <!--1333666 -->

Actuellement, [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) peut être utilisé sur les appareils Windows 10 à l’aide d’un profil de réseau privé virtuel (VPN) personnalisé créé à l’aide d’OMA-URI.

Avec cette mise à jour, les administrateurs peuvent activer les profils VPN Always On pour Windows 10 directement dans Intune au sein du portail Azure. Les profils VPN Always On se connecteront automatiquement :

- À la connexion des utilisateurs à leurs appareils
- Au changement du réseau sur l’appareil
- À la réactivation de l’écran de l’appareil

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nouveaux paramètres d’imprimante pour les profils Éducation <!-- 1308900 -->

Pour les profils Éducation, de nouveaux paramètres sont disponibles sous la catégorie **Imprimantes** : **Imprimantes**, **Imprimante par défaut**, **Ajouter de nouvelles imprimantes**.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Afficher l’ID d’appelant dans un profil personnel - Android for Work <!--1098984 -->
Quand vous utilisez un profil personnel sur un appareil, les utilisateurs finaux ne voient pas forcément les détails relatifs à l’ID d’appelant d’un contact professionnel. 

Avec cette mise à jour, il existe un nouveau paramètre dans **Android for Work** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
- Afficher l’ID d’appelant du contact professionnel dans le profil personnel

Quand ce paramètre est activé (non configuré), les détails de l’ID d’appelant du contact professionnel sont affichés dans le profil personnel. Quand ce paramètre est désactivé, le numéro d’appelant du contact professionnel ne s’affiche pas dans le profil personnel. 

S’applique aux appareils avec profil professionnel Android pour le système d’exploitation Android v6.0 et les versions ultérieures

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nouveaux paramètres Windows Defender Credential Guard ajoutés aux paramètres Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Avec cette mise à jour, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configuration de l’appareil** > **Profils** > **Endpoint Protection**) présente les paramètres suivants : 

- **Windows Defender Credential Guard** : Active Credential Guard avec une sécurité basée sur la virtualisation. L’activation de cette fonctionnalité permet de protéger les informations d’identification au prochain redémarrage quand **Niveau de sécurité de plateforme avec démarrage sécurisé** et **Sécurité basée sur la virtualisation** sont activés. Les options sont les suivantes :
  - **Désactivé** : Si Credential Guard était activé avec l’option **Activé sans verrouillage**, cette option désactive Credential Guard à distance.

  - **Activé avec le verrouillage UEFI** : Garantit que Credential Guard ne peut pas être désactivé en utilisant une clé de Registre ou une stratégie de groupe. Pour désactiver Credential Guard après avoir utilisé ce paramètre, vous devez définir la stratégie de groupe sur « Désactivé ». Ensuite, supprimez la fonctionnalité de sécurité de chaque ordinateur, avec un utilisateur physiquement présent. Ces étapes effacent la configuration persistante dans UEFI. Tant que la configuration UEFI persiste, Credential Guard est activé.

  - **Activé sans verrouillage** : Permet de désactiver Credential Guard à distance à l’aide d’une stratégie de groupe. Les appareils utilisant ce paramètre doivent exécuter au moins Windows 10 (version 1511).

Les technologies dépendantes suivantes sont automatiquement activées lors de la configuration de Credential Guard : 

  - **Activer la sécurité basée sur la virtualisation (VBS)**  : Active la sécurité basée sur la virtualisation (VBS) au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité et nécessite le démarrage sécurisé.
  - **Démarrage sécurisé avec accès direct à la mémoire (DMA)**  : Active VBS avec démarrage sécurisé et accès direct à la mémoire. Les protections DMA nécessitent une prise en charge matérielle et ne sont activées que sur des appareils configurés correctement. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Utiliser un nom d’objet personnalisé sur le certificat SCEP <!-- 2064190 -->
Vous pouvez utiliser le nom courant **OnPremisesSamAccountName** dans un objet personnalisé sur un profil de certificat SCEP. Par exemple, vous pouvez utiliser `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Blocage des appareils photo et des captures d’écran sur Android for Work <!-- 1098977 eeready-->
Vous disposez de deux nouvelles propriétés de blocage au moment de configurer des restrictions d’appareil pour les appareils Android : 
- Appareil photo : bloque l’accès à tous les appareils photo sur l’appareil
- Capture d’écran : bloque la capture d’écran et empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée

S’applique à Android for Work.


### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nouvelles étapes d’inscription pour les utilisateurs sur les appareils dotés de macOS High Sierra 10.13.2+ <!--1734567 -->
macOS High Sierra 10.13.2 a introduit le concept d’inscription MDM « approuvée par l’utilisateur ». Les inscriptions approuvées permettent à Intune de gérer certains paramètres sensibles au niveau sécurité. Pour plus d’informations, consultez la documentation de prise en charge d’Apple ici : https://support.apple.com/HT208019.

Les appareils inscrits à l’aide du Portail d’entreprise macOS sont considérés comme « non approuvés par l’utilisateur », sauf si l’utilisateur final ouvre les préférences système et fournit une approbation manuellement. À cette fin, le Portail d’entreprise macOS invite désormais les utilisateurs sur macOS 10.13.2 et ultérieur à approuver manuellement leur inscription à la fin du processus d’inscription. La console d’administration Intune indiquera si un appareil inscrit est approuvé par l’utilisateur.



### <a name="device-management"></a>Gestion des appareils

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>ATP (Protection avancée contre les menaces) et Intune sont entièrement intégrés <!-- EEready 1629303 -->

[Protection avancée contre les menaces (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) indique le niveau de risque des appareils Windows 10. Dans le Centre de sécurité Windows Defender (portail ATP), vous pouvez créer une connexion à Microsoft Intune. Une fois créée, une stratégie de conformité Intune permet de déterminer un niveau de menace acceptable. Si le niveau de menace est dépassé, une stratégie d’accès conditionnel Azure AD (Active Directory) peut bloquer l’accès à différentes applications au sein de votre organisation.

Cette fonctionnalité permet à ATP d’analyser les fichiers, de détecter les menaces et de signaler tout risque sur vos appareils Windows 10.

Consultez [Activer ATP avec accès conditionnel dans Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Prise en charge des appareils sans utilisateurs <!-- 1637553 -->
Intune permet d’évaluer la conformité sur un appareil sans utilisateur, comme Microsoft Surface Hub. La stratégie de conformité peut cibler des appareils spécifiques. Ainsi, la conformité, et la non-conformité, peuvent être déterminées pour les appareils auxquels aucun utilisateur n’est associé.

#### <a name="delete-autopilot-devices----1713650---"></a>Supprimer les appareils AutoPilot <!-- 1713650 -->
Les administrateurs Intune peuvent [supprimer les appareils AutoPilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Amélioration de l’expérience de suppression d’appareil <!--1832333 -->
Vous n’avez plus besoin de supprimer les données d’entreprise ou de réinitialiser un appareil aux paramètres d’usine avant de le [supprimer d’Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Pour voir la nouvelle expérience, connectez-vous à Intune et sélectionnez **Appareils** > **Tous les appareils** > nom de l’appareil > **Supprimer**.

Si vous souhaitez toujours la confirmation de réinitialisation/mise hors service, vous pouvez suivre le cycle de vie d’appareil standard en utilisant les commandes **Supprimer les données d’entreprise** et **Réinitialisation aux paramètres d’usine** avant la commande **Supprimer**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Lire les sons sur iOS en mode Perdu <!-- 1947769 -->
Quand les appareils iOS supervisés sont en [mode Perdu](device-lost-mode.md) MDM (Mobile Device Management), vous pouvez [lire un son](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Appareils** > **Tous les appareils** > sélectionnez un appareil iOS > **Vue d’ensemble** > **Plus**). La lecture du son se poursuit jusqu’à ce que l’appareil soit retiré du mode Perdu ou qu’un utilisateur désactive le son sur l’appareil. S’applique aux appareils iOS 9.3 et ultérieur.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloquer ou autoriser les résultats web dans les recherches effectuées sur un appareil Intune <!--1972804-->

Les administrateurs peuvent maintenant bloquer les résultats web des recherches effectuées sur un appareil.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Amélioration des messages d’erreur liés à l’échec du chargement du certificat Push MDM Apple <!-- 2172331 -->

Le message d’erreur explique que le même identifiant Apple doit être utilisé au moment du renouvellement d’un certificat MDM existant.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Tester le portail d’entreprise pour macOS sur des machines virtuelles <!-- 2216679 -->

Nous avons publié des conseils pour aider les administrateurs informatiques à tester l’application Portail d’entreprise pour macOS sur des machines virtuelles dans Parallels Desktop et VMware Fusion. Découvrez-en plus dans [Inscrire des machines virtuelles macOS à des fins de test](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interface utilisateur

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Amélioration des vignettes d’appareil dans le portail d’entreprise Windows 10 <!--2213364 -->

Les vignettes ont été mises à jour pour être plus accessibles aux utilisateurs malvoyants et proposer un meilleur rendu pour les outils de lecture d’écran.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Envoyer des rapports de diagnostic dans l’application Portail d’entreprise pour macOS <!-- 2216677 -->
L’application Portail d’entreprise pour les appareils macOS est mise à jour pour améliorer la façon dont les utilisateurs signalent les erreurs relatives à Intune. À partir de l’application Portail d’entreprise, vos employés peuvent :

- Charger des rapports de diagnostic directement remis à l’équipe de développement Microsoft.
- Envoyer par e-mail un ID d’incident à l’équipe de support informatique de votre entreprise.

Pour plus d’informations, consultez [Envoyer les erreurs pour macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune s’adapte à Fluent Design System dans l’application Portail d’entreprise pour Windows 10 <!-- 1195010 WNready -->
L’application Portail d’entreprise Intune pour Windows 10 a été mise à jour avec le [mode de navigation de Fluent Design System](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). Le long de l’application, vous remarquerez une liste verticale statique de toutes les pages de niveau supérieur. Cliquez sur n’importe quel lien pour afficher des pages et passer de l’une à l’autre rapidement. Il s’agit de la première d’une série de mises à jour que vous verrez dans le cadre de nos efforts constants pour créer une expérience plus adaptive, empathique et familière dans Intune. Pour voir à quoi ressemble la mise à jour, accédez à [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Semaine du 16 avril 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Utiliser le client Cisco AnyConnect pour iOS <!-- EEready 1333708 -->

Quand vous créez un profil VPN pour iOS, vous disposez désormais de deux options : **Cisco AnyConnect** et **Cisco Legacy AnyConnect**. Les profils Cisco AnyConnect prennent en charge les versions 4.0.7x et ultérieures. Les profils VPN Cisco AnyConnect pour iOS existants se nomment **Cisco Legacy AnyConnect** et continuent de fonctionner avec Cisco AnyConnect 4.0.5x et les versions antérieures, comme c’est le cas aujourd’hui.

> [!NOTE]
> Ce changement s’applique uniquement à iOS. Il existe toujours une seule option Cisco AnyConnect pour les plateformes Android, Android for Work et macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>Les appareils macOS inscrits auprès de Jamf peuvent désormais s’inscrire auprès d’Intune <!-- 2370684 -->

Les versions 1.3 et 1.4 du portail d’entreprise macOS n’ont pas réussi à inscrire les appareils Jamf auprès d’Intune. Ce problème est résolu dans la version 1.4.2 du portail macOS.


## <a name="week-of-april-9-2018"></a>Semaine du 9 avril 2018

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Mise à jour de l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android <!-- 1631531 -->

Nous avons mis à jour l’expérience utilisateur de l’aide dans l’application Portail d’entreprise pour Android afin de l’harmoniser avec les bonnes pratiques relatives à la plateforme Android. Désormais, quand les utilisateurs rencontrent un problème dans l’application, ils peuvent appuyer sur **Menu** > **Aide** et :
- Charger les journaux de diagnostic sur le site de Microsoft
- Envoyer un e-mail décrivant le problème et indiquant l’ID d’incident à une personne du support de l’entreprise  

Pour découvrir à quoi ressemble la mise à jour de l’expérience utilisateur de l’aide, accédez à [Envoyer des journaux à l’aide de la messagerie](/intune-user-help/send-logs-to-your-it-admin-by-email-android) et [Envoyer les erreurs à Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nouveau graphique de tendance des échecs d’inscription et tableau des raisons de ces échecs <!-- 1471783 -->

Dans la page Vue d’ensemble de l’inscription, vous pouvez voir la tendance des échecs d’inscription et les cinq premières causes d’échecs. En cliquant sur le graphique ou le tableau, vous pouvez explorer les détails et trouver des conseils de dépannage, ainsi que des suggestions de correction.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Mise à jour de l’emplacement de configuration de vos stratégies de protection des applications <!-- 2144597 -->

Dans le portail Azure du service Microsoft Intune, nous allons vous rediriger temporairement du panneau de service **Intune App Protection** vers le panneau **Application mobile**. Notez que toutes vos stratégies de protection d’application sont déjà sur le panneau **Application mobile** dans Intune, sous la configuration de l’application. Au lieu d’accéder à Intune App Protection, vous accédez simplement à Intune. En avril 2018, nous mettrons fin à la redirection et nous la supprimerons complètement du panneau du service **Intune App Protection** : il n’y aura alors plus qu’un seul emplacement pour les stratégies de protection d’application dans Intune. 

**Comment cela m’affecte-t-il ?**
Ce changement affecte les clients autonomes et les clients hybrides Intune (Intune avec Configuration Manager). Cette intégration permet de simplifier l’administration de la gestion de votre cloud.

**Que faire pour se préparer à ce changement ?**
Mettez **Intune** en favori à la place du panneau de service **Intune App Protection**, et veillez à vous familiariser avec le workflow de stratégie de protection des applications dans le panneau **Application mobile** d’Intune. Pendant une courte période, nous allons assurer la redirection, puis nous supprimerons le panneau **Protection d’applications**. N’oubliez pas que toutes les stratégies de protection des applications sont déjà dans Intune, et que vous pouvez modifier vos stratégies d’accès conditionnel. Pour plus d’informations sur la modification des stratégies d’accès conditionnel, consultez [Accès conditionnel dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Pour plus d’informations, consultez [Que sont les stratégies de protection des applications ?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Semaine du 2 avril 2018

### <a name="intune-apps"></a>Applications Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Mise à jour de l’expérience utilisateur dans l’application Portail d’entreprise pour iOS <!--1412866 -->
Nous avons publié une mise à jour majeure de l’expérience utilisateur de l’application Portail d’entreprise pour iOS. La mise à jour comporte une refonte visuelle complète incluant une apparence plus moderne. Nous avons conservé les fonctionnalités de l’application, mais nous avons étendu sa facilité d’utilisation et son accessibilité.  

Vous découvrirez également les points suivants :
- Prise en charge de l’iPhone X.
- Lancement et chargement plus rapides des applications, pour faire gagner du temps aux utilisateurs.
- Barres de progression supplémentaires pour fournir aux utilisateurs les toutes dernières informations d’état.
- Améliorations de la façon dont les utilisateurs chargent les journaux pour faciliter le signalement des problèmes.  

Pour voir à quoi ressemble la mise à jour, accédez à [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

#### <a name="protect-on-premise-exchange-data-using-intune-app-and-ca----1056954---"></a>Protéger les données Exchange sur site à l’aide de la stratégie de protection des applications et de l’accès conditionnel d’Intune <!-- 1056954 -->
Vous pouvez désormais utiliser les fonctionnalités APP (stratégie de protection des applications) et CA (accès conditionnel) d’Intune pour protéger l’accès aux données Exchange sur site avec Outlook Mobile. Pour ajouter ou modifier une stratégie de protection des applications dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications mobiles** > **Stratégies de protection des applications**. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux [exigences relatives à Outlook pour iOS et Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="week-of-march-26-2018"></a>Semaine du 26 mars 2018

### <a name="app-management"></a>Gestion d'applications

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Alertes relatives à l’expiration des applications métier iOS pour Microsoft Intune <!-- 748789 -->

Dans le portail Azure, Intune vous alerte quand des applications métier iOS arrivent à expiration. Quand vous chargez une nouvelle version de l’application métier iOS, Intune supprime la notification d’expiration de la liste des applications. Cette notification d’expiration est active uniquement pour les dernières applications métier iOS chargées. Un avertissement apparaît 30 jours avant l’expiration du profil de provisionnement de l’application métier iOS. Une fois que l’expiration a eu lieu, l’état de l’alerte passe à Expiré.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personnaliser vos thèmes de portail d’entreprise avec des codes hexadécimaux<!--1049561 -->

Vous pouvez personnaliser la couleur du thème des applications Portail d’entreprise à l’aide de codes hexadécimaux. Quand vous entrez votre code hexadécimal, Intune détermine la couleur de texte qui offre le plus haut niveau de contraste entre la couleur de texte et la couleur d’arrière-plan. Vous pouvez afficher un aperçu de la couleur du texte et du logo de votre société par rapport à la couleur dans **Applications mobiles** > **Portail d’entreprise**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusion et exclusion d’affectations d’applications en fonction de groupes pour Android Enterprise <!-- 1813081 -->

Android Enterprise (anciennement Android for Work) prend en charge l’inclusion et l’exclusion de groupes, mais ne prend pas en charge les groupes prédéfinis **Tous les utilisateurs** et **Tous les appareils**. Pour plus d’informations, consultez [Inclure et exclure des affectations d’applications dans Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestion des appareils

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nouvelles améliorations de la sécurité dans le service Intune <!-- 1637539 -->   

Nous avons introduit un bouton bascule dans Intune sur Azure, qui permet aux clients autonomes Intune de définir un appareil auquel aucune stratégie n’est affectée comme étant **Conforme** (fonctionnalité de sécurité désactivée) ou **Non conforme** (fonctionnalité de sécurité activée). Cela permet de garantir l’accès aux ressources uniquement après l’évaluation de la conformité de l’appareil.

Cette fonctionnalité vous impacte différemment selon que vous avez déjà affecté ou non des stratégies de conformité.

- Si vous êtes un nouveau compte ou un compte existant, et si vous n’avez affecté aucune stratégie de conformité à vos appareils, le bouton bascule est automatiquement défini sur **Conforme**. La fonctionnalité est désactivée par défaut dans la console. L’impact est inexistant pour l’utilisateur final.
- Si vous êtes un compte existant, et si vous avez des appareils auxquels vous avez affecté une stratégie de conformité, le bouton bascule est automatiquement défini sur **Non conforme**. La fonctionnalité est activée par défaut avec le déploiement de la mise à jour de mars.

Si vous utilisez des stratégies de conformité avec un accès conditionnel, et si cette fonctionnalité est activée, les appareils auxquels aucune stratégie de conformité n’a été affectée sont désormais bloqués par l’accès conditionnel. Les utilisateurs finaux associés à ces appareils, qui étaient autorisés à accéder aux e-mails, perdent leur accès, sauf si vous affectez au moins une stratégie de conformité à tous les appareils.   

Notez que même si l’état par défaut du bouton bascule est affiché dans l’IU avec les mises à jour de mars du service Intune, cet état n’est pas appliqué immédiatement. Les changements apportés au bouton bascule n’ont aucun impact sur la conformité des appareils tant que nous n’activons pas la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Nous vous informerons via le Centre de messages quand nous aurons activé la fonctionnalité pour votre compte dans le cadre de la version d’évaluation. Cela peut prendre quelques jours, une fois que la mise à jour de mars aura été appliquée à votre service Intune.

**Informations supplémentaires** : [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Détection de jailbreak améliorée <!-- 846515 -->

La détection de jailbreak améliorée est un nouveau paramètre de conformité qui améliore la manière dont Intune évalue les appareils jailbreakés. Avec ce paramètre, l’appareil s’enregistre plus fréquemment auprès d’Intune, lequel utilise les services de géolocalisation de l’appareil, ce qui impacte la durée de vie de la batterie.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Réinitialiser les mots de passe pour les appareils Android O <!-- 1238299 -->
Vous pouvez réinitialiser les mots de passe des appareils Android 8.0 inscrits à l’aide des profils professionnels. Quand vous envoyez une demande de réinitialisation de mot de passe à un appareil Android 8.0, cela entraîne la définition d’un nouveau mot de passe de déverrouillage de l’appareil ou d’une vérification du profil managé pour l’utilisateur actuel. La vérification ou le mot de passe est envoyé et prend effet immédiatement.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ciblage des stratégies de conformité pour les appareils dans des groupes d’appareils <!--1307012 -->

Vous pouvez appliquer des stratégies de conformité en ciblant des utilisateurs au sein de groupes d’utilisateurs. Avec cette mise à jour, vous pouvez appliquer des stratégies de conformité en ciblant des appareils au sein de groupes d’appareils. Les appareils ciblés dans le cadre de groupes d’appareils ne reçoivent aucune action de conformité.

#### <a name="new-management-name-column----1333586---"></a>Nouvelle colonne Nom d’administration <!-- 1333586 -->
 Une nouvelle colonne nommée **Nom de la gestion** est disponible dans le panneau des appareils. Il s’agit d’un nom généré automatiquement, non modifiable affecté par appareil, reposant sur la formule suivante :
- Nom par défaut pour tous les appareils : <username><em><devicetype></em><enrollmenttimestamp>
- Pour les appareils ajoutés en bloc : <ID_de_package/ID_de_profil><em><DeviceType></em><EnrollmentTime>

Il s’agit d’une colonne facultative dans le panneau Appareils. Elle n’est pas disponible par défaut. Vous pouvez y accéder uniquement via le sélecteur de colonne. Le nom de l’appareil n’est pas affecté par cette nouvelle colonne.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>Les appareils iOS sont invités à entrer un code confidentiel toutes les 15 minutes <!--1550837 -->
Une fois qu’une stratégie de conformité ou de configuration est appliquée à un appareil iOS, les utilisateurs sont invités à définir un code PIN toutes les 15 minutes. Les utilisateurs sont continuellement sollicités jusqu’à ce qu’un code PIN soit défini.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Planifier vos mises à jour automatiques <!--1805514 -->
Intune vous permet de contrôler l’installation des mises à jour automatiques à l’aide des [paramètres des anneaux de mise à jour Windows](windows-update-for-business-configure.md). Avec cette mise à jour, vous pouvez planifier des mises à jour récurrentes : hebdomadaires, quotidiennes et horaires.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Utiliser le nom unique en tant que sujet de certificat SCEP <!--2221763 -->
Quand vous créez un profil de certificat SCEP, vous entrez le nom du sujet. Avec cette mise à jour, vous pouvez utiliser le nom unique complet en tant que sujet. Dans **Nom du sujet**, sélectionnez **Personnalisé**, puis entrez `CN={{OnPrem_Distinguished_Name}}`. Pour utiliser la variable `{{OnPrem_Distinguished_Name}}`, veillez à synchroniser l’attribut utilisateur `onpremisesdistingishedname` qui utilise [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) avec Azure AD.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Activer le partage de contacts Bluetooth - Android for Work <!--1098983 -->
Par défaut, Android empêche les contacts inclus dans le profil professionnel de se synchroniser avec des appareils Bluetooth. Ainsi, les contacts de profil professionnel ne s’affichent pas sur l’ID de l’appelant des appareils Bluetooth.

Avec cette mise à jour, il existe un nouveau paramètre dans **Android for Work** > **Restrictions sur l’appareil** > **Paramètres du profil professionnel** :
- Partage de contacts via Bluetooth

L’administrateur Intune peut configurer ces paramètres pour activer le partage. Cette démarche s’avère utile lors de l’appariement d’un appareil avec un appareil Bluetooth de voiture qui affiche l’ID de l’appelant à des fins d’utilisation en mode mains libres. Quand ce paramètre est activé, les contacts de profil professionnel sont affichés. Dans le cas contraire, ils n’apparaissent pas.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Configurer Gatekeeper pour contrôler la source de téléchargement des applications macOS <!-- 1690459 -->

Vous pouvez configurer Gatekeeper pour protéger vos appareils en contrôlant les sources de téléchargement des applications. Vous pouvez configurer les sources de téléchargement suivantes : **Mac App Store**, **Mac App Store et développeurs identifiés** ou **N’importe où**. Vous pouvez déterminer si les utilisateurs peuvent installer une application en appuyant de façon prolongée sur la touche Ctrl pour remplacer ces contrôles Gatekeeper.

Ces paramètres se trouvent sous **Configuration de l’appareil** -> **Créer un profil** -> **macOS**  ->  **Endpoint protection**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurer le coupe-feu applicatif Mac <!-- 1690461 -->

Vous pouvez configurer le pare-feu d’applications Mac. Vous serez ainsi en mesure de contrôler les connexions au niveau de chaque application, plutôt qu’au niveau de chaque port. Il permet ainsi d’empêcher les applications indésirables de contrôler les ports réseau ayant été ouverts pour des applications légitimes, et de profiter d’une protection optimale.

Cette fonctionnalité se trouve sous **Configuration de l’appareil** -> **Créer un profil** -> **macOS**  ->  **Endpoint protection**.

Une fois le paramètre de coupe-feu activé, vous pouvez configurer le coupe-feu à l’aide de deux stratégies :

- Bloquer toutes les connexions entrantes

   Vous pouvez bloquer toutes les connexions entrantes pour les appareils ciblés. Si vous procédez ainsi, les connexions entrantes sont bloquées pour toutes les applications.

- Autoriser ou bloquer des applications spécifiques

   Vous pouvez autoriser ou bloquer la réception de connexions entrantes pour des applications spécifiques. Vous pouvez également activer le mode furtif de manière à empêcher les réponses aux demandes de détection.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Codes et messages d’erreur détaillés <!-- 1376342 -->

Dans Configuration de l’appareil, vous trouverez des codes d’erreur et des messages d’erreur plus détaillés. Cette amélioration du compte-rendu permet de voir les paramètres, leur état et les détails relatifs au dépannage.

##### <a name="more-information"></a>Plus d’informations

- Bloquer toutes les connexions entrantes

   La réception de connexions entrantes est bloquée pour tous les services de partage (par exemple, le partage de fichiers et le partage d’écran). Les services système qui sont toujours autorisés à recevoir des connexions entrantes sont :
  - configd : implémente DHCP et d’autres services de configuration réseau
  - mDNSResponder : implémente Bonjour
  - racoon : implémente IPSec

    Pour utiliser les services de partage, assurez-vous que **Connexions entrantes** a la valeur **Non configuré** (pas **Bloquer**).

- Mode furtif

   Activez cette option pour empêcher l’ordinateur de répondre aux demandes de détection. L’ordinateur continue de répondre aux demandes entrantes pour les applications autorisées. Les demandes inattendues, comme ICMP (ping), sont ignorées.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Désactiver les vérifications au redémarrage de l’appareil <!--1805490 -->
Intune vous permet de [gérer les mises à jour logicielles]](windows-update-for-business-configure.md). Avec cette mise à jour, la propriété <strong>Vérifications de redémarrage</strong> est disponible et activée par défaut. Pour ignorer les vérifications usuelles qui se produisent au redémarrage d’un appareil (comme les utilisateurs actifs, les niveaux de batterie, etc.), sélectionnez <strong>Ignorer</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nouveaux canaux Windows 10 Insider Preview disponibles pour les anneaux de déploiement <!-- 1746293 -->
Vous pouvez désormais sélectionner les canaux de maintenance Windows 10 Insider Preview suivants quand vous créez un anneau de déploiement Windows 10 :
- Version Windows Insider &#8208; Rapide
- Version Windows Insider &#8208; Lente
- Publier la version Windows Insider 

Pour plus d’informations sur ces canaux, consultez [Gérer les versions Insider Preview](https://insider.windows.com/en-us/for-business-organization-admin/).   
Pour plus d’informations sur la création de canaux de déploiement dans Intune, consultez [Gérer les mises à jour logicielles dans Intune](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>Applications Intune

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Inscription par le biais de l’application Portail d’entreprise améliorée <!-- 1874230 eeready-->
Les utilisateurs qui inscrivent un appareil à l’aide du Portail d’entreprise sur Windows 10 (build 1703) et versions ultérieures peuvent désormais effectuer la première étape de l’inscription sans quitter l’application.

#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens et Surface Hub apparaissent désormais dans les listes d’appareils <!--1725868 -->
Nous avons ajouté la prise en charge de l’affichage des appareils HoloLens et Surface Hub inscrits auprès d’Intune dans l’application Portail d’entreprise pour Android.

#### <a name="custom-book-categories-for-volume-purchase-progream-vpp-ebooks----1488911---"></a>Catégories de livres personnalisées pour les livres électroniques achetés dans le cadre d’un VPP (programme d’achat en volume) <!-- 1488911 -->
Vous pouvez créer des catégories de livres électroniques personnalisées, puis leur affecter des livres électroniques achetés en volume. Les utilisateurs finaux pourront ensuite voir les nouvelles catégories de livres électroniques et les livres affectés à ces catégories. Pour plus d’informations, consultez [Gérer les applications et les livres achetés en volume avec Microsoft Intune](vpp-apps.md).

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nouveaux paramètres Windows Defender Application Guard <!-- 1631890 -->

- **Activer l’accélération graphique** : les administrateurs peuvent activer un processeur graphique virtuel pour Windows Defender Application Guard. Ce paramètre permet à l’UC de décharger l’affichage graphique sur l’unité de traitement graphique virtuelle. Cela peut améliorer les performances quand vous utilisez des sites web qui consomment beaucoup de graphiques ou regardez une vidéo au sein du conteneur.

- **SaveFilestoHost** : les administrateurs peuvent autoriser le passage des fichiers depuis Microsoft Edge, qui s’exécute dans le conteneur, vers le système de fichiers hôte. L’activation de ce paramètre permet aux utilisateurs de télécharger des fichiers à partir de Microsoft Edge, dans le conteneur, vers le système de fichiers hôte.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Stratégies de protection MAM ciblées en fonction de l’état de gestion <!-- 1665993 -->
Vous pouvez cibler des stratégies MAM en fonction de l’état de gestion de l’appareil :
- **Appareils Android** : vous pouvez cibler des appareils non gérés, des appareils gérés par Intune et des profils d’entreprise Android gérés par Intune (anciennement Android for Work).
- **Appareils iOS** : vous pouvez cibler des appareils non gérés (MAM uniquement) ou des appareils gérés par Intune.

    > [!NOTE]
    > - La prise en charge de cette fonctionnalité par iOS est déployée tout au long du mois d’avril 2018.

Pour plus d’informations, consultez [Cibler des stratégies de protection des applications en fonction de l’état de gestion des appareils](app-protection-policies.md).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Améliorations du langage utilisé dans l’application Portail d’entreprise pour Windows <!-- 1683758 -->
Nous avons amélioré le langage utilisé dans le Portail d’entreprise pour Windows 10 pour qu’il soit plus convivial et plus spécifique à votre entreprise. Pour voir nos exemples d’images, consultez [Nouveautés de l’interface utilisateur des applications](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Nouveaux ajouts à notre documentation sur la confidentialité des utilisateurs <!-- 1440709 -->
Dans le cadre de nos efforts pour donner aux utilisateurs finaux un plus grand contrôle sur la confidentialité de leurs données, nous avons publié des mises à jour de notre documentation expliquant comment afficher et supprimer les données stockées localement par les applications du Portail d’entreprise. Vous pouvez trouver ces mises à jour aux emplacements suivants :

- **Android** : [Guide pratique pour supprimer un appareil Android d’Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, si l’utilisateur a refusé les conditions d’utilisation** : [Guide pratique pour supprimer la gestion de votre appareil si vous avez refusé les « Conditions d’utilisation »](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS** : [Guide pratique pour supprimer votre appareil iOS d’Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows** : [Guide pratique pour supprimer votre appareil Windows d’Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>Semaine du 19 mars 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Exporter tous les appareils vers des fichiers CSV dans Internet Explorer, Edge ou Chrome <!-- 2258071 -->
Dans **Appareils** > **Tous les appareils**, vous pouvez **Exporter** les appareils vers une liste au format CSV. Les utilisateurs Internet Explorer ayant plus de 10 000 appareils peuvent exporter leurs appareils correctement dans plusieurs fichiers. Chaque fichier contient jusqu’à 10 000 appareils.

Les utilisateurs Edge et Chrome ayant plus de 30 000 appareils peuvent exporter leurs appareils correctement dans plusieurs fichiers. Chaque fichier contient jusqu’à 30 000 appareils.

La rubrique [Gérer des appareils](device-management.md) fournit plus de détails sur ce que vous pouvez faire avec les appareils que vous gérez.

## <a name="week-of-march-12-2018"></a>Semaine du 12 mars 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Les sites web Azure Active Directory peuvent nécessiter l’application Intune Managed Browser et la prise en charge de l’authentification unique pour Managed Browser (préversion publique) <!-- 710595 -->

Avec Azure AD (Azure Active Directory), vous pouvez désormais restreindre l’accès aux sites web pour l’application Intune Managed Browser sur les appareils mobiles. Dans Managed Browser, les données de site web restent sécurisées et séparées des données personnelles de l’utilisateur final. Par ailleurs, Managed Browser prend en charge les fonctionnalités d’authentification unique pour les sites protégés par Azure AD. Si vous vous connectez à Managed Browser ou que vous utilisez Managed Browser sur un appareil avec une autre application gérée par Intune, Managed Browser peut accéder aux sites d’entreprise protégés par Azure AD sans que l’utilisateur ne doive entrer ses informations d’identification. Cette fonctionnalité s’applique aux sites comme Outlook Web Access (OWA) et SharePoint Online, ainsi qu’à d’autres sites d’entreprise tels que les ressources intranet accessibles par le proxy de l’application Azure.

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Mises à jour visuelles de l’application Portail d’entreprise pour Android <!--976944 -->

Nous avons mis à jour l’application Portail d’entreprise pour Android afin de suivre les recommandations de [Material Design](https://material.io/). Vous pouvez voir les images des nouvelles icônes dans l’article [Nouveautés de l’interface utilisateur d’application](whats-new-app-ui.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Nouveaux paramètres Windows Defender Exploit Guard <!-- 1631893 -->

Six nouveaux paramètres de <strong>réduction de la surface d’attaque</strong> et fonctionnalités étendues <strong>d’accès contrôlé aux dossiers : Protection des dossiers</strong> sont maintenant disponibles. Ces paramètres se trouvent dans : Configuration de l’appareil\Profils\
Créez profil\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque

|Nom du paramètre  |Options du paramètre  |Description  |
|---------|---------|---------|
|Protection avancée contre les ransomware|Activé, Auditer, Non configuré|Utiliser une protection agressive contre les ransomware.|
|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows|Activé, Auditer, Non configuré|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows (lsass.exe).|
|Création de processus à partir des commandes PSExec et WMI|Bloquer, Auditer, Non configuré|Bloquer les créations de processus issues des commandes PSExec et WMI.|
|Processus non approuvés et non signés exécutés à partir d’USB|Bloquer, Auditer, Non configuré|Bloquer les processus non approuvés et non signés exécutés à partir d’USB.|
|Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée|Bloquer, Auditer, Non configuré|Bloquer l’exécution des fichiers exécutables sauf s’ils répondent à des critères de prédominance, d’âge ou de liste approuvée.|

#### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

|              Nom du paramètre               |                                                              Options du paramètre                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protection des dossiers (déjà implémenté) | Non configuré, Activer, Auditer uniquement (déjà implémentées)<br><br> <strong>Nouveau</strong><br>Bloquer la modification du disque, Auditer la modification du disque |             |

Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.<br><br>**Activer** : Empêcher les applications non approuvées de modifier ou supprimer des fichiers dans des dossiers protégés et d’écrire dans des secteurs de disque.<br><br>
**Bloquer la modification du disque uniquement** :<br>Empêcher les applications non approuvées d’écrire dans des secteurs de disque. Les applications non approuvées peuvent toujours modifier ou supprimer des fichiers dans des dossiers protégés.

## <a name="week-of-february-19-2018"></a>Semaine du 19 février 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Prise en charge d’Intune pour plusieurs comptes DEP / Apple School Manager <!-- 747685 -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du [Programme d’inscription des appareils (DEP)](device-enrollment-program-enroll-ios.md) ou [Apple School Manager](apple-school-manager-set-up-ios.md). Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Afficher les restrictions d’inscription par utilisateur <!-- 1634444 eeready wnready -->
Le panneau **Résoudre les problèmes** vous permet désormais de voir les [restrictions d’inscription](enrollment-restrictions-set.md) en vigueur pour chaque utilisateur. Pour cela, sélectionnez **Restrictions d’inscription** dans la liste **Affectations**.

### <a name="device-management"></a>Gestion des appareils
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Rapports sur l’état des menaces et l’état d’intégrité de Windows Defender<!--854704 -->

Il est essentiel de comprendre l’état et l’intégrité de Windows Defender pour gérer des PC Windows.  Avec cette mise à jour, Intune ajoute de nouveaux rapports et de nouvelles actions à l’état et à l’intégrité de l’agent Windows Defender. Grâce à un rapport de cumul d’état dans la [charge de travail Conformité de l’appareil](compliance-policy-monitor.md), vous pouvez voir les appareils qui nécessitent les actions suivantes :
- mise à jour des signatures
- Redémarrer
- intervention manuelle
- analyse complète
- autres états de l’agent nécessitant une intervention

Un rapport détaillé pour chaque catégorie d’état liste les PC individuels nécessitant une attention particulière, ou ceux qui sont signalés comme **sans problème**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nouveaux paramètres de confidentialité pour les restrictions de l’appareil <!--1308926 -->
[Deux nouveaux paramètres de confidentialité](device-restrictions-windows-10.md#privacy) sont désormais disponibles pour les appareils :
- **Publier les activités de l’utilisateur** : affectez la valeur **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches.
- **Activités locales uniquement** : affectez la valeur **Bloquer** pour empêcher les expériences partagées et la découverte des ressources récemment utilisées dans le sélecteur de tâches en fonction uniquement de l’activité locale.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nouveaux paramètres pour le navigateur Microsoft Edge <!--1469166 -->
[Deux nouveaux paramètres](device-restrictions-windows-10.md#edge-browser) sont désormais disponibles pour les appareils avec le navigateur Microsoft Edge : **Chemin vers le fichier de favoris** et **Modifications des favoris**.

### <a name="app-management"></a>Gestion d'applications
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Exceptions de protocoles pour les applications<!--1035509 -->

Vous pouvez à présent créer des exceptions à la stratégie de transfert de données de gestion des applications mobiles (MAM) Intune pour ouvrir des applications non gérées spécifiques. De telles applications doivent être approuvées par le service informatique. Hormis les exceptions que vous créez, le transfert de données est toujours limité aux applications qui sont gérées par Intune quand votre stratégie de transfert de données est définie pour les **applications gérées uniquement**. Vous pouvez créer les restrictions à l’aide de protocoles (iOS) ou de packages (Android).

Par exemple, vous pouvez ajouter le package Webex en tant qu’exception à la stratégie de transfert de données MAM. Cela permet d’ouvrir les liens Webex dans un e-mail Outlook géré directement dans l’application Webex. Le transfert de données sera toujours limité dans d’autres applications non gérées. Pour plus d’informations, consultez [Exceptions de la stratégie de transfert de données pour les applications](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Données chiffrées Windows Information Protection (WIP) dans les résultats de la recherche Windows <!-- 1469193 -->
La stratégie Protection des informations Windows comprend désormais un paramètre vous permettant d’inclure ou non les données chiffrées par cette stratégie dans les résultats de la recherche Windows. Pour définir cette option de stratégie de protection d’application, sélectionnez **Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés** dans les **Paramètres avancés** de la stratégie Protection des informations Windows. La stratégie de protection d’application doit être définie pour la plateforme *Windows 10* et **l’état de l’inscription** de la stratégie d’application doit indiquer **Avec inscription**. Pour plus d’informations, consultez [Autoriser l’indexeur de recherche Windows à rechercher les éléments chiffrés](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configuration d’une application MSI mobile avec mise à jour automatique <!-- 1740840 -->
Vous pouvez configurer une application MSI mobile connue avec mise à jour automatique pour ignorer le processus de vérification de version. Cette fonctionnalité est utile pour éviter d’introduire une condition de concurrence. Une condition de concurrence peut notamment se produire quand l’application est mise à jour automatiquement par le développeur de l’application et aussi par Intune. Les deux peuvent essayer d’appliquer une version de l’application sur un client Windows, générant ainsi un conflit. Pour ces applications MSI mises à jour automatiquement, vous pouvez configurer le paramètre **Ignorer la version de l’application** dans le panneau **Informations sur l’application**. Quand vous basculez ce paramètre sur **Oui**, Microsoft Intune ignore la version de l’application installée sur le client Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Jeux liés de licences d’application pris en charge dans Intune <!-- 1864117 -->
Dans le portail Azure, Intune prend désormais en charge les jeux liés de licences d’application comme élément d’application unique dans l’interface utilisateur. En outre, toutes les applications sous licence en mode hors connexion synchronisées à partir de Microsoft Store pour Entreprises seront consolidées dans une entrée d’application unique et les détails du déploiement des packages individuels seront migrés sur l’entrée unique. Pour afficher les jeux liés de licences d’application dans le portail Azure, sélectionnez **Licences d’application** dans le panneau **Applications mobiles**.

### <a name="device-configuration"></a>Configuration des appareils
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Extensions de fichier Protection des informations de Windows pour le chiffrement automatique <!-- 1463582 -->
La stratégie Protection des informations Windows comprend désormais un paramètre vous permettant de spécifier des extensions de fichier. Les fichiers avec ces extensions sont automatiquement chiffrés durant la copie à partir d’un partage SMB (Server Message Block) dans les limites de l’entreprise, telles que définies dans la stratégie Protection des informations Windows.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurer les paramètres de compte de ressource pour les appareils Surface Hub

Vous pouvez à présent configurer à distance les paramètres de compte de ressource pour les appareils Surface Hub.

Le compte de ressource est utilisé par un appareil Surface Hub pour l’authentification sur Skype/Exchange afin de prendre part à une réunion.
Vous pouvez créer un compte de ressource unique afin que l’appareil Surface Hub puisse s’afficher dans la réunion en tant que salle de conférence,
par exemple un compte de ressource tel que **Salle de conférence B41/6233**.

> [!NOTE]
> - Si vous laissez les champs vides, vous allez remplacer les attributs précédemment configurés sur l’appareil.
>
> - Les propriétés de compte de ressource peuvent changer dynamiquement sur l’appareil Surface Hub, par exemple si la rotation de mot de passe est activée. Par conséquent, il est possible que les valeurs dans la console Azure prennent un certain temps avant de refléter la réalité sur l’appareil.
>
>   Pour comprendre ce qui est actuellement configuré sur l’appareil Surface Hub, les informations de compte de ressource peuvent être incluses dans l’inventaire matériel (qui dispose déjà d’un intervalle de 7 jours) ou en tant que propriétés en lecture seule. Pour améliorer la précision une fois que l’action à distance a eu lieu, vous pouvez obtenir l’état des paramètres immédiatement après l’exécution de l’action pour mettre à jour les paramètres/le compte sur l’appareil Surface Hub.


##### <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque


|Nom du paramètre  |Options du paramètre  |Description  |
|---------|---------|---------|
|Exécution du contenu d’un exécutable protégé par mot de passe à partir d’un e-mail|Bloquer, Auditer, Non configuré|Empêcher l’exécution de fichiers exécutables téléchargés à partir d’un e-mail et protégés par mot de passe.|
|Protection avancée contre les ransomware|Activé, Auditer, Non configuré|Utiliser une protection agressive contre les ransomware.|
|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows|Activé, Auditer, Non configuré|Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows (lsass.exe).|
|Création de processus à partir des commandes PSExec et WMI|Bloquer, Auditer, Non configuré|Bloquer les créations de processus issues des commandes PSExec et WMI.|
|Processus non approuvés et non signés exécutés à partir d’USB|Bloquer, Auditer, Non configuré|Bloquer les processus non approuvés et non signés exécutés à partir d’USB.|
|Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée|Bloquer, Auditer, Non configuré|Bloquer l’exécution des fichiers exécutables sauf s’ils répondent à des critères de prédominance, d’âge ou de liste approuvée.|

##### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

|              Nom du paramètre               |                                                              Options du paramètre                                                              | Description |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protection des dossiers (déjà implémenté) | Non configuré, Activer, Auditer uniquement (déjà implémentées)<br><br> <strong>Nouveau</strong><br>Bloquer la modification du disque, Auditer la modification du disque |             |

Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.<br><br>**Activer** : Empêcher les applications non approuvées de modifier ou supprimer des fichiers dans des dossiers protégés et d’écrire dans des secteurs de disque.<br><br>
**Bloquer la modification du disque uniquement** :<br>Empêcher les applications non approuvées d’écrire dans des secteurs de disque. Les applications non approuvées peuvent toujours modifier ou supprimer des fichiers dans des dossiers protégés.

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Ajouts aux paramètres de sécurité du système pour les stratégies de conformité Windows 10 et versions ultérieures <!--1704133-->

Des ajouts apportés aux paramètres de conformité Windows 10 sont désormais disponibles, comme l’obligation d’utiliser le pare-feu et l’antivirus Windows Defender.


### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle
### <a name="intune-apps"></a>Applications Intune
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Prise en charge des applications hors connexion à partir du Microsoft Store pour Entreprises <!--1222672-->
Les applications en mode hors connexion que vous avez achetées sur le Microsoft Store pour Entreprises sont désormais synchronisées avec le portail Azure. Vous pouvez déployer ces applications sur des groupes d’utilisateurs ou d’appareils. Les applications hors connexion sont installées par Intune et non pas par le Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Empêcher des utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel <!-- 1728700 -->

Quand vous déployez l’application Gmail dans un profil Android for Work, vous pouvez désormais empêcher les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel à l’aide du paramètre **Ajouter et supprimer des comptes** du profil de restrictions d’appareil Android for Work.

## <a name="week-of-february-5-2018"></a>Semaine du 5 février 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nouvelle option pour l’authentification utilisateur dans le cadre de l’inscription en bloc Apple <!-- 747625 eeready -->

> [!NOTE]
> Les nouveaux locataires la verront tout de suite. Pour les locataires existants, cette fonctionnalité sera déployée en avril. Tant que ce déploiement ne sera pas terminé, vous n’aurez peut-être pas accès à ces nouvelles fonctionnalités.

Intune vous donne maintenant la possibilité d’authentifier les appareils à l’aide de l’application Portail d’entreprise pour les méthodes d’inscription suivantes :

- Programme d'inscription d'appareils Apple
- Apple School Manager
- Inscription à Apple Configurator

Lorsque vous utilisez l’option Portail d’entreprise, l’authentification multifacteur Azure Active Directory peut être appliquée sans bloquer ces méthodes d’inscription.

Lorsque vous utilisez l’option Portail d’entreprise, Intune ignore l’authentification utilisateur dans l’Assistant Réglages iOS pour l’inscription d’affinité utilisateur. Cela signifie que l’appareil est initialement inscrit comme appareil sans utilisateur et, par conséquent, vous ne recevez pas les configurations ou stratégies des groupes d’utilisateurs. Il reçoit uniquement les configurations et les stratégies des groupes d’appareils. Toutefois, Intune installera automatiquement l’application Portail d’entreprise sur l’appareil. Le premier utilisateur à lancer l’application Portail d’entreprise et à s’y connecter sera associé à l’appareil dans Intune. À ce stade, l’utilisateur reçoit les configurations et les stratégies de ses groupes d’utilisateurs. L’association de l’utilisateur ne peut pas être modifiée sans réinscription.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Prise en charge d’Intune pour plusieurs comptes DEP / Apple School Manager <!-- 747685 eeready -->

Intune prend maintenant en charge l’inscription des appareils jusqu'à la limite de 100 comptes dans le cadre du Programme d’inscription des appareils (DEP) ou Apple School Manager. Chaque jeton téléchargé peut être géré séparément pour les profils d’inscription et les appareils. Un profil d’inscription différent peut être affecté automatiquement pour chaque jeton DEP/School Manager téléchargé. Si plusieurs jetons School Manager sont téléchargés, un seul jeton peut être partagé avec Microsoft School Data Sync à la fois.

Après la migration, les API Graph en version bêta et les scripts publiés pour la gestion DEP Apple ou ASM via Graph ne fonctionneront plus. De nouvelles versions bêta des API Graph sont en cours de développement et seront publiées après la migration.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Impression à distance sur un réseau sécurisé <!-- 1709994  -->
Les solutions d’impression mobiles sans fil PrinterOn permettront aux utilisateurs d’imprimer à distance depuis n’importe où et à tout moment via un réseau sécurisé. PrinterOn s’intégrera au Kit SDK APP d’Intune à la fois pour iOS et Android. Vous pourrez cibler les stratégies de protection d’application pour cette application via le panneau des **stratégies de protection d’application** d’Intune, dans la console d’administration. Les utilisateurs finaux pourront télécharger l’application « PrinterOn for Microsoft » via le Google Play Store ou iTunes afin de l’utiliser dans leur écosystème Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Prise en charge du portail d’entreprise macOS pour les inscriptions qui utilisent le gestionnaire d’inscription d’appareil <!-- 1352411 -->

Les utilisateurs peuvent désormais utiliser le Gestionnaire d’inscription d’appareil durant l’inscription auprès du portail d’entreprise macOS.

## <a name="week-of-january-29-2018"></a>Semaine du 29 janvier 2018

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Alertes pour les jetons expirés et les jetons qui arrivent à expiration <!-- 1639263 -->
La page de vue d’ensemble affiche maintenant des alertes pour les jetons expirés et ceux qui arrivent à expiration. Lorsque vous cliquez sur une alerte pour un jeton unique, vous accéderez à la page des détails de ce jeton.  Si vous cliquez sur une alerte comportant plusieurs jetons, vous accéderez à une liste de tous les jetons avec leur état. Les administrateurs doivent renouveler leurs jetons avant la date d’expiration.

### <a name="device-management"></a>Gestion des appareils

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Prise en charge de la commande d’effacement à distance pour les appareils macOS <!-- 1438084 -->

Les administrateurs peuvent exécuter une commande d’effacement à distance pour les appareils macOS.

> [!IMPORTANT]
> La commande d’effacement ne peut pas être annulée et doit être utilisée avec précaution.

La commande d’effacement supprime toutes les données, y compris le système d’exploitation, d’un appareil. Elle entraîne aussi la suppression de l'appareil de la gestion Intune. Aucun avertissement n’est envoyé à l’utilisateur, et l’effacement se produit dès l’envoi de la commande.

Vous pouvez configurer un code PIN de récupération à 6 chiffres. Ce code PIN peut servir à déverrouiller l’appareil effacé avant de lancer la réinstallation du système d’exploitation. Une fois que l’effacement a démarré, le code PIN apparaît dans une barre d’état sur le panneau de présentation de l’appareil dans Intune. Le code PIN restera affiché tant que l’effacement est en cours. Une fois l’effacement terminé, l’appareil disparaît totalement de la gestion Intune. Veillez à enregistrer le code PIN de récupération afin que toute personne qui restaure l’appareil puisse l’utiliser.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Révoquer des licences pour un jeton Programme d’achat en volume iOS <!-- 820870 -->
Vous pouvez révoquer la licence de toutes les applications de Programme d’achat en volume (VPP) iOS pour un jeton VPP donné.

### <a name="app-management"></a>Gestion d'applications

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Révocation des applications du Programme d’achat en volume iOS  <!-- 820863 -->
Pour un appareil donné qui a une ou plusieurs applications de Programme d’achat en volume (VPP) iOS, vous pouvez révoquer pour l’appareil la licence d’application associée basée sur l’appareil. La révocation d’une licence d’application ne désinstalle pas l’application VPP de l’appareil. Pour désinstaller une application VPP, vous devez remplacer l’action d’attribution par **Désinstaller**. Pour plus d’informations, consultez [Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Affecter des applications mobiles Office 365 aux appareils iOS et Android à l’aide du type d’application intégré <!-- 1332318 -->
Le type d’application **Intégré** facilite la création d’applications Office 365 et leur affectation aux appareils iOS et Android gérés. Ces applications incluent les applications Office 365 telles que Word, Excel, PowerPoint et OneDrive. Vous pouvez affecter des applications spécifiques au type d’application et modifier la configuration des informations des applications.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusion et exclusion d’affectations d’applications en fonction de groupes <!-- 1406920 -->

Pendant l’affectation d’une application et après avoir sélectionné un type d’affectation, vous pouvez sélectionner les groupes à inclure et ceux à exclure.

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>Vous pouvez attribuer une stratégie de configuration d’application à des groupes en incluant et excluant des affectations  <!-- 1480316 -->

Vous pouvez attribuer une stratégie de configuration d’application à un groupe d’utilisateurs et d’appareils à l’aide d’une combinaison d’affectations d’inclusion et d’exclusion. Les affectations peuvent être choisies sous la forme d’une sélection personnalisée de groupes ou d’un groupe virtuel. Un groupe virtuel peut être notamment **Tous les utilisateurs**, **Tous les appareils** ou **Tous les utilisateurs + Tous les appareils**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Prise en charge de la stratégie de mise à niveau de l’édition Windows 10   <!-- 903672(archived), 1119689 -->  
Vous pouvez créer une stratégie de mise à niveau d’édition Windows 10 qui met à niveau les appareils Windows 10 vers Windows 10 Éducation, Windows 10 Éducation N, Windows 10 Professionnel, Windows 10 Professionnel N, Windows 10 Professionnel Éducation et Windows 10 Professionnel Éducation N. Pour plus d’informations sur les mises à niveau d’édition Windows 10, consultez [Guide pratique pour configurer les mises à niveau d’édition Windows 10 ](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Les stratégies d’accès conditionnel pour Intune sont disponibles uniquement à partir du portail Azure <!-- 1737088 1634311 -->

À partir de cette version, vous pouvez configurer et gérer vos stratégies d’accès conditionnel dans le [portail Azure](https://portal.azure.com) en accédant à **Azure Active Directory** > **Accès conditionnel**. Pour des raisons pratiques, vous pouvez également accéder à ce panneau à partir d’Intune dans le portail Azure, depuis **Intune** > **Accès conditionnel**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Mises à jour des e-mails de conformité <!--1637547 -->

Quand un e-mail est envoyé pour signaler un appareil non conforme, des informations sur cet appareil non conforme sont ajoutées.


## <a name="week-of-january-22-2018"></a>Semaine du 22 janvier 2018

### <a name="intune-apps"></a>Applications Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nouvelles fonctionnalités de l’action « Résoudre » pour les appareils Android <!--1583480-->

L’application Portail d’entreprise pour Android étend l’action « Résoudre » sur **Mettre à jour les paramètres d’appareil** afin de résoudre les [problèmes de chiffrement d’appareil](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Verrouillage à distance disponible dans l’application Portail d’entreprise pour Windows 10 <!--676506-->
Les utilisateurs finaux peuvent désormais verrouiller à distance leurs appareils à partir de l’application Portail d’entreprise pour Windows 10. Cela ne s’affichera pas pour l’appareil local qu’ils utilisent de manière active.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Résolution plus rapide des problèmes de conformité affectant l’application Portail d’entreprise pour Windows 10 <!--676546-->
Les utilisateurs finaux d’appareils Windows peuvent choisir la raison de la non-conformité dans l’application Portail d’entreprise. Quand c’est possible, ils sont directement positionnés à l’emplacement approprié dans l’application Paramètres pour corriger le problème.

## <a name="week-of-december-11-2017"></a>Semaine du 11 décembre 2017

### <a name="device-configuration"></a>Configuration des appareils

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nouveau paramètre de redéploiement automatique <!-- 1469168 -->
Le paramètre **Redéploiement automatique** permet aux utilisateurs avec des droits d’administration de supprimer l’ensemble des données et des paramètres utilisateur à l’aide des touches **Ctrl+Win+R** sur l’écran de verrouillage de l’appareil. L’appareil est automatiquement reconfiguré et réinscrit dans la gestion. Ce paramètre se trouve sous Windows 10 -> Restrictions sur l’appareil -> Général -> Redéploiement automatique. Pour plus d’informations, consultez [Paramètres de restriction d’appareil Intune pour Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Prise en charge d’éditions source supplémentaires dans la stratégie de mise à niveau de l’édition Windows 10 <!-- 903672,  1119689 -->
Vous pouvez maintenant utiliser la stratégie de mise à niveau de l’édition Windows 10 pour effectuer une mise à niveau à partir d’autres éditions de Windows 10 (Windows 10 Professionnel, Windows10 Professionnel Éducation, Windows 10 Cloud, etc.). Avant cette version, les chemins de mise à niveau de l’édition pris en charge étaient plus limités. Pour plus d’informations, consultez le [Guide pratique de configuration des mises à niveau Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Nouveaux paramètres pour le profil de configuration d’appareil Windows Defender Security Center (WDSC) <!-- 1335507 -->

Intune ajoute une nouvelle section de paramètres pour le profil de configuration d’appareil, sous la Protection du point de terminaison, nommée **Windows Defender Security Center**. Les administrateurs informatiques peuvent configurer les éléments de base auxquels les utilisateurs finaux de l’application Windows Defender Security Center peuvent accéder. Si un administrateur informatique masque un élément de base dans l’application Windows Defender Security Center, les notifications liées à l’élément de base masqué ne s’affichent pas sur l’appareil de l’utilisateur.

Vous trouverez ci-dessous les éléments de base que les administrateurs peuvent masquer dans les paramètres du profil de configuration d’appareil Windows Defender Security Center :
- Protection contre les menaces et les virus
- Performances et intégrité de l’appareil
- Protections du pare-feu et du réseau
- Contrôle d’application et du navigateur
- Options Famille

Les administrateurs informatiques peuvent également personnaliser les notifications que les utilisateurs reçoivent. Par exemple, vous pouvez décider si les utilisateurs reçoivent toutes les notifications générées par les éléments de base visibles dans WDSC ou uniquement les notifications critiques. Les notifications non critiques incluent des résumés périodiques sur l’activité de l’antivirus Windows Defender et des notifications indiquant lorsque des analyses sont terminées. Toutes les autres notifications sont considérées comme critiques. En outre, vous pouvez aussi personnaliser le contenu même de la notification. Par exemple, vous pouvez fournir les coordonnées du service informatique à inclure dans les notifications qui s’affichent sur les appareils des utilisateurs.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Prise en charge de connecteurs multiples pour le traitement des certificats SCEP et PFX <!-- 1361755 -->

Les clients qui utilisent le connecteur NDES local pour présenter des certificats à des appareils peuvent désormais configurer plusieurs connecteurs dans un seul locataire.

Cette nouvelle fonctionnalité prend en charge le scénario suivant :

- **Haute disponibilité**

Chaque connecteur NDES extraie des demandes de certificat d’Intune.  Si un connecteur NDES a l’état hors connexion, l’autre connecteur peut continuer à traiter les requêtes.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Le nom d’objet du client peut utiliser la variable AAD_DEVICE_ID <!-- 1468599 -->

Lorsque vous créez un profil de certificat SCEP dans Intune, vous pouvez désormais utiliser la variable AAD_DEVICE_ID lorsque vous générez le nom d’objet du client.   Lorsque le certificat est demandé à l’aide de ce profil SCEP, la variable est remplacée par l’ID AAD de l’appareil qui effectue la demande de certificat.


### <a name="device-management"></a>Gestion des appareils

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gérer les appareils macOS inscrits auprès de Jamf avec le moteur de conformité des appareils d’Intune<!-- 1592747 -->
Vous pouvez utiliser Jamf pour envoyer des informations sur l’état des appareils macOS à Intune, qui évaluera alors la conformité avec les stratégies définies dans la console Intune. En fonction de cet état et d’autres conditions (notamment, l’emplacement, les risques de l’utilisateur, etc.), l’accès conditionnel appliquera des stratégies de conformité aux appareils macOS qui accèdent aux applications cloud et locales reliées à Azure AD, y compris Office 365. En savoir plus sur la [configuration de l’intégration de Jamf](conditional-access-integrate-jamf.md) et la [mise en application de la conformité des appareils Jamf gérés](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nouvelle action sur appareil iOS   <!-- 1424701 -->

Vous pouvez maintenant arrêter les appareils supervisés iOS 10.3. Cette action arrête immédiatement l’appareil sans avertir l’utilisateur final. L’action **Arrêter (supervisé uniquement)** se trouve dans les propriétés de l’appareil lorsque vous sélectionnez un appareil dans la charge de travail **Appareil**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Interdire les changements de date/heure sur les appareils Samsung Knox <!-- 1468103 -->

Nous avons ajouté une nouvelle fonctionnalité qui vous permet d’empêcher les changements de date et d’heure sur les appareils Samsung Knox. Vous la trouverez dans **Profils de configuration d’appareil** > **Restrictions d’appareil (Android)** > **Général**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Compte de ressource Surface Hub pris en charge <!-- 1566442  -->

Une nouvelle action d’appareil a été ajoutée pour permettre aux administrateurs de définir et de mettre à jour le compte de ressource associé à un Surface Hub.

Le compte de ressource est utilisé par un Surface Hub pour l’authentification avec Skype/Exchange afin de prendre part à une réunion. Vous pouvez créer un compte de ressource unique afin que le Surface Hub s’affiche dans la réunion en tant que salle de conférence. Par exemple, le compte de ressource peut s’afficher comme *Salle de conférence B41/6233*. Le compte de ressource (également appelé compte de l’appareil) pour le Surface Hub doit en général être configuré pour l’emplacement de la salle de conférence et également lorsque d’autres paramètres du compte de ressource sont modifiés.

Lorsque les administrateurs veulent mettre à jour le compte de ressource sur un appareil, ils doivent fournir les informations d’identification Active Directory/Azure Active Directory actuelles associées à l’appareil. Si la rotation de mot de passe est activée sur l’appareil, les administrateurs doivent accéder à Azure Active Directory pour trouver le mot de passe.

> [!NOTE]
> Tous les champs sont transmis sous forme de package et écrasent tous les champs précédemment configurés. Les champs vident écrasent également les champs existants.

Vous trouverez ci-dessous les paramètres que les administrateurs peuvent configurer :

- **Compte de ressource**
   - **Utilisateur Active Directory**

      Nomdedomaine\nomd’utilisateur ou Nom d’utilisateur principal (UPN) : user@domainname.com

   - **Mot de passe**

- **Paramètres facultatifs du compte de ressource** (à définir à l’aide du compte de ressource spécifié)

   - **Période de rotation du mot de passe**

     Permet de s’assurer que le mot de passe du compte est automatiquement mis à jour par le Surface Hub chaque semaine à des fins de sécurité. Pour configurer des paramètres une fois cette option activée, il est nécessaire tout d’abord de réinitialiser le mot de passe du compte dans Azure Active Directory.

   - **Adresse du protocole d’initiation de session (SIP)**

     Utilisée uniquement en cas d’échec de la découverte automatique.

   - **Courrier électronique**

     Adresse e-mail de l’appareil/du compte de ressource.

   - **Serveur Exchange**

     Requis uniquement en cas d’échec de la découverte automatique.

   - **Synchronisation du calendrier**

     Permet de spécifier si la synchronisation du calendrier et d’autres services Exchange Server sont activés. Par exemple : synchronisation de réunion.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installer des applications Office sur des appareils macOS <!-- 1494311 -->
Vous pourrez maintenant installer des applications Office sur des appareils macOS. Ce nouveau type d’application vous permettra d’installer Word, Excel, PowerPoint, Outlook et OneNote. Ces applications bénéficient également de Microsoft AutoUpdate (MAU) qui garantit que vos applications sont sécurisées et à jour.

### <a name="app-management"></a>Gestion d'applications

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Supprimer un jeton Programme d’achat en volume iOS <!-- 820879 -->
Vous pouvez supprimer le jeton Programme d’achat en volume (VPP) iOS à l’aide de la console. Ceci peut être nécessaire si vous avez des instances dupliquées d’un jeton VPP.

### <a name="intune-apps"></a>Applications Intune


### <a name="role-based-access-control"></a>Contrôle d'accès en fonction du rôle

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Nouvelle collection d’entités, nommée Utilisateur actuel, limitée aux données des utilisateurs actuellement actifs<!-- 1667026 -->

La collecte d’entités **User** répertorie tous les utilisateurs Azure Active Directory (Azure AD) auxquels des licences ont été attribuées dans votre entreprise. Il est possible, par exemple, qu’un utilisateur soit ajouté à Intune, puis supprimé au cours du mois précédent. Cet utilisateur n’est pas présent au moment du rapport, mais lui et l’état apparaissent quand même dans les données. Vous pourriez créer un rapport qui afficherait la durée de la présence passée de l’utilisateur dans vos données.

En revanche, la nouvelle collection d’entités **Utilisateur actuel** contient uniquement les utilisateurs qui n’ont pas été supprimés. La collection d'entités **Utilisateur actuel** ne contient que des utilisateurs actuellement actifs. Pour plus d’informations sur la collection d’entités **Utilisateur actuel**, consultez la page [Informations de référence sur l’entité Utilisateur actuel](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>API Graph mises à jour <!-- 1736360 -->

Dans cette version, nous avons mis à jour quelques-unes des API Graph pour Intune (actuellement en version bêta). Consultez le [journal mensuel des modifications de l’API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) pour plus d’informations.

## <a name="week-of-december-4-2017"></a>Semaine du 4 décembre 2017

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune prend en charge les applications refusées dans Protection des informations Windows <!-- 1479103 -->
Vous pouvez spécifier les applications refusées dans Intune. Si une application est refusée, son accès aux informations d’entreprise est bloqué (ce qui correspond à l’inverse de la liste des applications autorisées). Pour plus d’informations, consultez [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Liste d’exclusion recommandée pour la Protection des informations Windows).


## <a name="week-of-november-27-2017"></a>Semaine du 27 novembre 2017

### <a name="device-enrollment"></a>Inscription des appareils

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>Résoudre les problèmes d’inscription  <!-- 746324 -->

L’espace de travail **Résolution des problèmes** montre désormais les problèmes d’inscription des utilisateurs. Des détails sur les problèmes et des suggestions de correction peuvent aider les administrateurs et les agents du support technique à résoudre les problèmes. Certains problèmes d’inscription ne sont pas capturés et certaines erreurs peuvent ne pas avoir de suggestions de correction.

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrictions d’inscription assignées aux groupes <!-- 747598 -->

En tant qu’administrateur Intune, vous pouvez désormais [créer des restrictions d’inscription Type d’appareil et Limite d’appareils personnalisées pour des groupes d’utilisateurs](enrollment-restrictions-set.md).

Le portail Azure Intune vous permet de créer jusqu’à 25 instances de chaque type de restriction qui peuvent ensuite être assignées aux groupes d’utilisateurs. Les restrictions assignées aux groupes remplacent les restrictions par défaut.

Toutes les instances d’un type de restriction sont conservées dans une liste classée de manière stricte. Cet ordre définit une valeur de priorité pour la résolution des conflits. Un utilisateur impacté par plusieurs instances de restriction est uniquement limité par l’instance ayant la valeur de priorité la plus élevée. Vous pouvez modifier la priorité d’une instance donnée en la faisant glisser vers un autre emplacement de la liste.

Cette fonctionnalité sera disponible quand les paramètres Android for Work seront migrés depuis le menu Inscription Android for Work vers le menu Restrictions d’inscription. Cette migration pouvant prendre plusieurs jours, votre compte peut être mis à niveau pour d’autres parties de la version de novembre avant que l’affectation aux groupes ne soit activée pour les restrictions d’inscription.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Prise en charge de plusieurs connecteurs NDES (Service d’inscription de périphérique réseau)<!-- 1528104 -->

NDES permet aux appareils mobiles s’exécutant sans informations d’identification de domaine d’obtenir des certificats basés sur le protocole d’inscription de certificats simple (SCEP).
Cette mise à jour prend en charge plusieurs connecteurs NDES.

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gérer les appareils Android for Work indépendamment des appareils Android <!-- 1490731 EEready-->

Intune prend en charge la gestion de l’inscription des appareils Android for Work indépendamment de la plateforme Android. Ces paramètres sont gérés sous **Inscription de l’appareil** > **Restrictions d’inscription** > **Restrictions de type d’appareil**. (Ils se trouvaient sous **Inscription de l’appareil** > **Inscription Android for Work** > **Paramètres d’inscription d’Android for Work**.)

Par défaut, les paramètres de vos appareils Android for Work sont identiques à ceux de vos appareils Android. Toutefois, ce ne sera plus le cas une fois que vous aurez modifié vos paramètres Android for Work.

Si vous bloquez l’inscription Android for Work personnelle, seuls les appareils Android d’entreprise peuvent s’inscrire en tant qu’Android for Work.

Quand vous utilisez les nouveaux paramètres, tenez compte des points suivants :

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Si vous n’avez jamais intégré l’inscription Android for Work

La nouvelle plateforme Android for Work est bloquée dans les restrictions de type d’appareil par défaut. Une fois la fonctionnalité intégrée, vous pouvez autoriser les appareils à s’inscrire auprès d’Android for Work. Pour ce faire, changez le paramétrage par défaut ou créez une restriction de type d’appareil afin de remplacer la restriction de type d’appareil par défaut.

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Si vous avez intégré l’inscription Android for Work

Votre situation varie selon le paramètre que vous avez choisi :

| Paramètre | État Android for Work dans la restriction de type d’appareil par défaut | Remarques |
| --- | --- | --- |
| **Gérer tous les appareils comme Android** | Bloqué | Tous les appareils Android doivent s’inscrire sans Android for Work. |
| **Gérer les appareils pris en charge comme Android for Work** | Autorisé | Tous les appareils Android qui prennent en charge Android for Work doivent s’inscrire auprès d’Android for Work. |
| **Gérer les appareils pris en charge pour les utilisateurs uniquement dans ces groupes comme Android for Work** | Bloqué | Une stratégie de restriction de type d’appareil distincte a été créée pour remplacer le paramétrage par défaut. Cette stratégie définit les groupes que vous avez choisis pour autoriser l’inscription Android for Work. Les utilisateurs dans les groupes sélectionnés continueront à être autorisés à inscrire leurs appareils Android for Work. Tous les autres utilisateurs ne peuvent pas s’inscrire auprès Android for Work. |

Dans tous les cas, les règles que vous avez envisagées sont conservées. Aucune action n’est requise de votre part pour gérer l’autorisation globale ou par groupe d’Android for Work dans votre environnement.

### <a name="app-management"></a>Gestion d'applications

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Mise à jour du rapport d’installation de l’application pour inclure l’état Installation en attente <!-- 1249446 -->  

Le rapport **État de l’installation de l’application** accessible pour chaque application par le biais de la liste **Application** dans la charge de travail **Applications mobiles** contient désormais un nombre **Installation en attente** pour les utilisateurs et les appareils.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API d’inventaire des applications iOS 11 pour la détection des menaces mobiles <!-- 1391759 -->

Intune collecte les informations d’inventaire des applications à partir des appareils personnels et d’entreprise et les met à la disposition des fournisseurs de détection des menaces mobiles, comme Lookout for Work. Vous pouvez collecter un inventaire des applications auprès des utilisateurs d’appareils iOS 11+.

**Inventaire des applications**  
Les inventaires à partir des appareils personnels et d’entreprise iOS 11 sont envoyés à votre fournisseur de service de détection des menaces mobiles. Les données de l’inventaire des applications comprennent les informations suivantes :

 - ID de l’application
 - Version de l’application
 - Version abrégée de l’application
 - Nom de l’application
 - Taille du bundle d’applications
 - Taille dynamique de l’application
 - Application validée ou non
 - Application gérée ou non


### <a name="device-management"></a>Gestion des appareils

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Faire migrer des utilisateurs et appareils MDM hybrides vers la version autonome d’Intune <!-- 1463747 wnready -->
De nouveaux processus et de nouveaux outils sont maintenant disponibles pour déplacer les utilisateurs et leurs appareils de MDM hybride vers Intune dans le portail Azure. Vous pouvez ainsi effectuer les tâches suivantes :
- Copier des stratégies et des profils de la console Configuration Manager vers Intune dans le portail Azure
- Déplacer une partie des utilisateurs vers Intune dans le portail Azure, tout en conservant le reste dans un environnement MDM hybride
- Migrer des appareils vers Intune dans le portail Azure sans avoir à les réinscrire

Pour plus d’informations, consultez [Faire migrer des utilisateurs et appareils MDM hybrides vers la version autonome d’Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local <!-- 676614 -->
Une fois que le connecteur Exchange crée une connexion à Exchange en utilisant l’autorité de certification spécifiée, le connecteur a désormais la possibilité de découverte d’autres autorités de certification. Si l’autorité de certification principale est indisponible, le connecteur bascule vers une autre autorité de certification disponible, jusqu'à ce que l’autorité de certification principale redevienne disponible. Pour plus de détails, voir [Prise en charge d’un haut niveau de disponibilité pour le connecteur Exchange local](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Redémarrer à distance un appareil iOS (supervisé uniquement) <!-- 1424595 -->

Vous pouvez désormais déclencher le redémarrage d’un appareil iOS 10.3+ supervisé au moyen d’une action d’appareil. Pour plus d’informations sur l’utilisation de l’action de redémarrage d’appareil, consultez [Redémarrer à distance des appareils avec Intune](device-restart.md).

> [!Note]
> Cette commande nécessite un appareil supervisé et le droit d’accès **Verrouillage de l’appareil**. L’appareil redémarre immédiatement. Après le redémarrage, les appareils iOS verrouillés par un code secret ne rejoignent pas un réseau Wi-Fi et peuvent se trouver dans l’impossibilité de communiquer avec le serveur.

#### <a name="single-sign-on-support-for-ios----1333645---"></a>Prise en charge de l’authentification unique pour iOS <!-- 1333645 -->  

Vous pouvez utiliser l’authentification unique pour les utilisateurs d’iOS. Les applications iOS qui sont codées pour rechercher les informations d’identification de l’utilisateur dans la charge utile d’authentification unique fonctionnent avec cette mise à jour de la configuration de la charge utile. Vous pouvez également utiliser un UPN et un ID d’appareil Intune pour configurer le nom du principal et le domaine. Pour plus d’informations, consultez [Configurer Intune pour l’authentification unique des appareils iOS](sso-ios.md).

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Ajouter « Rechercher mon iPhone » pour les appareils personnels <!--1427287-->
Vous pouvez désormais savoir si la fonctionnalité Verrou d’activation est activée pour les appareils iOS. Cette fonctionnalité se trouvait avant dans le portail classique.


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Verrouiller à distance un appareil macOS géré avec Intune <!-- 1437691 -->

Vous pouvez verrouiller un appareil macOS perdu et définir un code PIN de récupération à 6 chiffres. Une fois le verrouillage effectué, le panneau **Vue d’ensemble des appareils** affiche le code PIN jusqu’à ce qu’une autre action d’appareil soit envoyée.

Pour plus d’informations, consultez [Verrouiller à distance des appareils gérés avec Intune](device-remote-lock.md).

#### <a name="new-scep-profile-details-supported----1559808---"></a>Nouveaux détails de profil SCEP pris en charge <!-- 1559808 -->

Les administrateurs peuvent désormais définir des paramètres supplémentaires durant la création d’un profil SCEP sur les plateformes Windows, iOS, macOS et Android.  Les administrateurs peuvent définir un IMEI, un numéro de série ou un nom commun (adresse e-mail incluse) dans le format du nom de l’objet.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>Conserver les données pendant une réinitialisation des paramètres d’usine <!--1588489 -->
Une nouvelle fonctionnalité est disponible durant la réinitialisation de Windows 10 version 1709 et ultérieure aux paramètres d’usine. Les administrateurs peuvent spécifier si les données d’inscription des appareils et d’autres données provisionnées sont conservées sur un appareil en cas de réinitialisation aux paramètres d’usine.

Les données suivantes sont conservées pendant une réinitialisation des paramètres d’usine :
- Comptes d’utilisateur associés à l’appareil
- État de l’ordinateur (jonction de domaine, joint à Azure Active Directory)
- Inscription MDM
- Applications OEM installées (applications Win32 et du Store)
- Profil utilisateur
- Données utilisateur hors du profil utilisateur
- Ouverture de session automatique de l’utilisateur

Les données suivantes ne sont pas conservées :
- Fichiers utilisateur
- Applications utilisateur installées (applications Win32 et du Store)
- Paramètres d’appareil autres que les paramètres par défaut

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Les affectations de boucles de mise à jour de Windows 10 sont affichées <!-- 1621837 -->
Pendant une **résolution de problèmes**, vous pouvez voir les affectations de boucles de mise à jour de Windows 10 pour l’utilisateur affiché.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Paramètres de la fréquence d’émission des rapports Windows Defender - Protection avancée contre les menaces <!-- 1455974  -->
Le service Windows Defender - Protection avancée contre les menaces permet aux administrateurs de gérer la fréquence d’émission des rapports sur les appareils gérés. Avec la nouvelle option **Augmenter la fréquence des rapports de télémétrie**, Windows Defender ATP collecte les données et évalue les risques plus fréquemment. Par défaut, l’émission de rapports optimise le niveau de performance et la vitesse. Augmenter la fréquence d’émission des rapports peut être utile pour les appareils à haut risque. Ce paramètre se trouve dans le profil **Windows Defender ATP** dans **Configurations d’appareil**.

#### <a name="audit-updates----1412961---"></a>Auditer les mises à jour <!-- 1412961 -->  
La fonctionnalité d’audit d’Intune enregistre les opérations de modification relatives à Intune.  Tous les opérations de création, de mise à jour, de suppression et de tâche à distance sont capturées et conservées pendant un an.  Le portail Azure fournit une vue filtrable des 30 derniers jours de données d’audit dans chaque charge de travail.  Une API Graph correspondante permet de récupérer les données d’audit stockées pendant l’année écoulée.

La fonctionnalité d’audit se trouve sous le groupe **SURVEILLER**. Il existe un élément de menu **Journaux d’audit** par charge de travail.




## <a name="week-of-november-20-2017"></a>Semaine du 20 novembre 2017

### <a name="app-management"></a>Gestion d'applications

#### <a name="google-play-protect-support-on-android----908720---"></a>Support de Google Play Protect sur Android <!-- 908720 -->

Avec la publication d’Android Oreo, Google introduit une suite de fonctionnalités de sécurité appelée Google Play Protect qui permet aux utilisateurs et aux organisations d’exécuter des applications sécurisées et des images Android sécurisées. Intune prend maintenant en charge les fonctionnalités de Google Play Protect, notamment l’attestation SafetyNet distante. Les administrateurs peuvent définir des critères de stratégie de conformité pour que Google Play Protect soit configuré et sain.
Le paramètre **Attestation d’appareil SafetyNet** nécessite que l’appareil se connecte à un service Google pour vérifier que l’appareil est intègre et qu’il n’est pas compromis. Les administrateurs peuvent également définir un paramètre de profil de configuration pour qu’Android for Work exige que les applications installées soient vérifiées par les services Google Play. Si un appareil n’est pas conforme aux exigences de Google Play Protect, l’accès conditionnel peut empêcher les utilisateurs d’accéder aux ressources de l’entreprise.

- Découvrez comment [créer une stratégie de conformité des appareils pour activer Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocole de texte autorisé à partir des applications gérées <!-- 1414050  -->

Les applications gérées par le SDK d’application Intune peuvent envoyer des SMS.

## <a name="week-of-november-13-2017"></a>Semaine du 13 novembre 2017

### <a name="intune-apps"></a>Applications Intune
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>L’application Portail d’entreprise pour macOS est disponible<!--1541700-->
L’expérience du Portail d’entreprise Intune sous macOS a été mise à jour. Elle a été optimisée pour afficher clairement toutes les informations et notifications de conformité dont les utilisateurs ont besoin pour tous les appareils qu’ils ont inscrits. Une fois que le Portail d’entreprise Intune a été déployé sur un appareil, il bénéficie de la mise à jour automatique Microsoft (AutoUpdate) pour macOS. Vous pouvez télécharger le nouveau Portail d’entreprise Intune pour macOS en ouvrant une session sur le site web du Portail d’entreprise Intune sur un appareil macOS.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner fait maintenant partie de la liste des applications approuvées de la gestion des applications mobiles (MAM)<!-- 1248473 -->
L’application Microsoft Planner pour iOS et Android fait à présent partie des applications approuvées pour la gestion des applications mobiles (MAM). Elle est configurable par le biais du panneau Intune App Protection sur le Portail Azure de tous les clients.
- Pour plus de détails, consultez la page [Liste MAM des applications approuvées](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Fréquence de mise à jour des exigences du VPN par application sur les appareils iOS<!-- 1547061 -->  
Les administrateurs peuvent à présent supprimer des exigences du VPN par application pour les applications installées sur des appareils iOS ; les appareils concernés seront mis à jour après l’archivage Intune suivant, ce qui se produit généralement dans les 15 minutes.  

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Prise en charge du pack d’administration de System Center Operations Manager pour le connecteur Exchange<!-- 885457 -->
Le pack d’administration de System Center Operations Manager (SCOM) pour le connecteur Exchange est maintenant disponible pour vous aider à analyser les journaux du connecteur Exchange. Cette fonctionnalité offre différents moyens de surveiller le service à des fins de résolution des problèmes.

## <a name="week-of-november-6-2017"></a>Semaine du 6 novembre 2017

### <a name="device-enrollment"></a>Inscription des appareils
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Cogestion pour les appareils Windows 10 <!-- 1243445 -->
La cogestion est une solution qui propose une passerelle entre la gestion classique et la gestion moderne tout en vous donnant la possibilité d’opérer cette transition selon une approche en plusieurs phases. À la base, la cogestion est une solution qui permet aux appareils Windows 10 d’être gérés simultanément par Configuration Manager et Microsoft Intune, et d’être joints à Active Directory (AD) et à Azure Active Directory (Azure AD).  Cette configuration vous offre un moyen de vous moderniser à un rythme qui convient à votre organisation si vous ne pouvez pas le faire d’un coup.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Limiter l’inscription Windows par version de système d’exploitation<!-- 245498 -->
En tant qu’administrateur Intune, vous pouvez maintenant spécifier une version minimale et maximale de Windows 10 pour les inscriptions d’appareils. Vous pouvez définir ces restrictions dans le panneau **Configurations de plateforme**.

Intune continue à prendre en charge l’inscription des PC et téléphones Windows 8.1. Toutefois, seules les versions de Windows 10 peuvent être configurées avec des limites minimale et maximale. Pour autoriser l’inscription d’appareils 8.1, laissez vide la limite minimale.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Alertes pour les appareils non affectés Windows AutoPilot  <!-- 1631236 -->
Une nouvelle alerte est disponible pour les appareils non attribués Windows AutoPilot dans la page **Microsoft Intune** > **Inscription de l’appareil** > **Vue d’ensemble**. Cette alerte indique combien d’appareils du programme AutoPilot n’ont pas de profils de déploiement AutoPilot affectés. Utilisez les informations de l’alerte pour créer des profils et les affecter aux appareils non affectés. Quand vous cliquez sur l’alerte, une liste complète des appareils Windows AutoPilot et des informations détaillées les concernant s’affichent. Pour plus d’informations, consultez [Inscrire des appareils Windows à l’aide du programme de déploiement Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Gestion des appareils

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Bouton Actualiser pour la liste des appareils    <!-- 1333581 -->
La liste des appareils ne s’actualisant pas automatiquement, vous pouvez utiliser le bouton Actualiser pour mettre à jour les appareils affichés dans la liste.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Prise en charge de l’Autorité de certification Symantec Cloud  <!-- 1333638 -->    
Intune prend désormais en charge l’Autorité de certification Symantec Cloud qui permet à Intune Certificate Connector d’émettre des certificats PKCS de l’Autorité de certification Symantec Cloud sur des appareils gérés par Intune. Si vous utilisez déjà Intune Certificate Connector avec l’Autorité de certification Microsoft, vous pouvez utiliser la configuration existante d’Intune Certificate Connector en y ajoutant la prise en charge de l’Autorité de certification de Symantec.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nouveaux éléments ajoutés à l’inventaire des appareils   <!--1404455 -->
Les nouveaux éléments suivants sont maintenant disponibles dans [l’inventaire effectué par les appareils inscrits](device-inventory.md) :

- Adresse MAC Wi-Fi
- Espace de stockage total
- Espace libre total
- MEID
- Opérateur de l’abonné


### <a name="app-management"></a>Gestion d'applications
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Définir l’accès pour les applications avec un correctif de sécurité Android minimal sur l’appareil<!-- 1278463 -->   
Un administrateur peut définir le correctif de sécurité Android minimal qui doit être installé sur l’appareil pour obtenir l’accès à une application gérée sous un compte géré.

> [!Note]  
> Cette fonctionnalité restreint uniquement les correctifs de sécurité publiés par Google sur les appareils Android 6.0 +.

#### <a name="app-conditional-launch-support----1193313---"></a>Prise en charge du lancement conditionnel d’applications<!-- 1193313 -->
Les administrateurs informatiques peuvent désormais définir une condition dans le portail d’administration Azure permettant d’appliquer un code secret à la place d’un code PIN numérique via la gestion des applications mobiles (MAM) lors du lancement de l’application. Selon la configuration, l’utilisateur doit définir et utiliser un code secret quand il y est invité avant d’obtenir l’accès à des applications compatibles MAM. Un code secret est défini comme un code PIN numérique avec au moins un caractère spécial ou une lettre majuscule/minuscule. Cette version d’Intune propose cette fonctionnalité **sur iOS uniquement**. Intune prend en charge un code secret comme un code PIN numérique, il définit une longueur minimale et autorise la répétition des caractères et des séquences. Cette fonctionnalité nécessite la participation des applications (c’est-à-dire, WXP, Outlook, Managed Browser, Yammer) pour intégrer le kit SDK Intune App avec le code de cette fonctionnalité en place dans le but d’appliquer les paramètres du code secret dans les applications ciblées.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Numéro de version des applications métier dans le rapport d’état d’installation de l’appareil<!-- 1233999 -->
Avec cette version, le rapport d’état d’installation de l’appareil affiche le numéro de version des applications métier pour iOS et Android. Vous pouvez utiliser cette information pour dépanner vos applications ou trouver les appareils qui exécutent des versions d’application anciennes.


### <a name="device-configuration"></a>Configuration des appareils
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Les administrateurs peuvent désormais configurer les paramètres du Pare-feu d’un appareil avec un profil de configuration d’appareil <!-- 951708 -->   
Les administrateurs peuvent activer le Pare-feu sur les appareils et configurer divers protocoles pour les réseaux privés, publics et de domaine.  Ces paramètres de pare-feu se trouvent dans le profil « Endpoint protection ».

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard permet de protéger les appareils des sites web non approuvés, comme défini par votre organisation <!-- 958257 -->   
Les administrateurs peuvent définir les sites comme « approuvés » ou « appartenant à l’entreprise » à l’aide d’un flux de travail Protection des informations Windows ou du nouveau profil « Limite réseau » dans les configurations de l’appareil. S’ils sont consultés dans Microsoft Edge, les sites qui ne sont pas listés dans la limite réseau approuvée d’un appareil Windows 10 64 bits s’ouvrent à la place dans un navigateur d’une machine virtuelle Hyper-V.

Application Guard se trouve dans les profils de configuration de l’appareil, dans le profil « Endpoint protection ». À partir de là, les administrateurs peuvent configurer une interaction entre le navigateur virtualisé et la machine hôte, les sites non approuvés et les sites approuvés, puis stocker les données générées dans le navigateur virtualisé. Pour utiliser Application Guard sur un appareil, une limite réseau doit d’abord être configurée. Il est important de définir une seule limite réseau pour un appareil.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows Defender Application Control sur Windows 10 Entreprise offre un mode permettant d’approuver uniquement les applications autorisées <!-- 1031096 -->    
Avec des milliers de nouveaux fichiers malveillants créés chaque jour, l’utilisation d’une détection antivirus basée sur les signatures pour lutter contre les programmes malveillants ne constitue probablement plus une défense suffisante contre les nouvelles attaques. En utilisant Windows Defender Application Control sur Windows 10 Entreprise, vous pouvez changer la configuration de l’appareil et passer d’un mode où les applications sont approuvées sauf si elles sont bloquées par un antivirus ou une autre solution de sécurité à un mode où le système d’exploitation approuve uniquement les applications autorisées par votre entreprise. Vous approuvez les applications dans Windows Defender Application Control.

Avec Intune, vous pouvez configurer des stratégies de contrôle d’application en mode « audit uniquement » ou en mode d’application. Les applications ne sont pas bloquées quand vous exécutez le mode « audit uniquement ». Le mode « Audit uniquement » enregistre tous les événements dans les journaux du client local. Vous pouvez également autoriser uniquement l’exécution des composants Windows et des applications du Microsoft Store, ou autoriser l’exécution d’autres applications avec une bonne réputation telle que définie par Intelligent Security Graph.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender Exploit Guard est un nouvel ensemble de fonctionnalités de prévention d’intrusion pour Windows 10 <!-- 1063615 -->   
Windows Defender Exploit Guard propose des règles personnalisées permettant de réduire l’exploitabilité des applications, empêche les menaces provenant de macros et de scripts, bloque automatiquement les connexions réseau à des adresses IP de mauvaise réputation et peut sécuriser les données contre des ransomware et des menaces inconnues. Windows Defender Exploit Guard présente les composants suivants :

- **Réduction de la surface d’attaque (ASR)** fournit des règles vous permettant d’empêcher les menaces de macro, de script et d’e-mail.
- **Accès contrôlé au dossier** bloque automatiquement l’accès au contenu des dossiers protégés.
- **Filtre de réseau** bloque la connexion sortante de toutes les applications à une adresse IP/domaine de faible réputation
- **Exploit Protection** fournit la mémoire, le flux de contrôle et les restrictions de stratégie pouvant être utilisés pour protéger les applications contre des attaques.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gérer des scripts PowerShell dans Intune pour des appareils Windows 10 <!-- 790537 -->

L’extension de gestion Intune vous permet de charger des scripts PowerShell dans Intune pour les exécuter sur des appareils Windows 10. L’extension vient en complément des fonctionnalités de gestion des appareils mobiles (MDM) Windows 10 et facilite l’adoption d’une gestion moderne. Pour plus d’informations, consultez [Gérer des scripts PowerShell dans Intune pour des appareils Windows 10](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nouveaux paramètres de restriction d’appareil pour Windows 10      <!-- 1308850 -->
-    Messagerie (mobile uniquement) - désactivation des tests ou des messages MMS
-    Mot de passe - paramètres pour activer FIPS et l’utilisation d’appareils secondaires Windows Hello pour l’authentification 
-    Affichage - paramètres pour activer ou désactiver la mise à l’échelle GDI pour les applications héritées

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Restrictions des appareils en mode plein écran Windows 10<!-- 1308872 -->   
Vous pouvez restreindre les utilisateurs d’appareils Windows 10 au mode plein écran, ce qui limite les utilisateurs à un ensemble d’applications prédéfinies.  Pour ce faire, créez un profil de restriction d’appareil Windows 10 et définissez les paramètres de plein écran.

Le mode plein écran prend en charge deux modes : **application unique** (permet à l’utilisateur d’exécuter une seule application) ou **applications multiples** (permet l’accès à un ensemble d’applications).  Vous définissez le compte d’utilisateur et le nom de l’appareil, ce qui détermine les applications prises en charge.  Lorsque l’utilisateur est connecté, il est limité aux applications définies.  Pour en savoir plus, consultez [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp). 

Conditions requises du mode plein écran :

- Intune doit être l’autorité MDM.
- Les applications doivent déjà être installées sur l’appareil cible.
- L’appareil doit être [correctement provisionné](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions).

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nouveau profil de configuration d’appareil pour la création de limites réseau<!-- 1311967 -->   
Vous trouverez un nouveau profil de configuration d’appareil appelé **Limite réseau** avec vos autres profils de configuration d’appareil. Utilisez ce profil pour définir des ressources en ligne à considérer comme approuvées et appartenant à l’entreprise. Vous devez définir une limite réseau pour un appareil *avant* de pouvoir utiliser les fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows sur l’appareil. Il est important de définir une seule limite réseau pour chaque appareil.

Vous pouvez définir des ressources cloud d’entreprise, des plages d’adresses IP et des serveurs proxy internes à considérer comme approuvées. Une fois définie, la limite réseau peut être utilisée par d’autres fonctionnalités comme Windows Defender Application Guard et Protection des informations Windows.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Deux paramètres supplémentaires pour Windows Defender Antivirus<!-- 1338409 -->  
**Niveau de blocage des fichiers**

| | |
|---|---|
| non configuré | **Non configuré** utilise le niveau de blocage de Windows Defender Antivirus par défaut et offre une détection solide sans augmenter le risque de détection des fichiers légitimes. |
| Importante | **Haut** s’applique à un niveau fort de détection.
| Élevé +  | **Haut +** fournit le niveau Haut avec des mesures de protection supplémentaires pouvant impacter les performances du client.
| Tolérance zéro  | **Tolérance zéro** bloque tous les exécutables inconnus. |

Bien qu’improbable, la définition sur **Haut** risque d’entraîner la détection de certains fichiers légitimes.
Nous vous recommandons de définir le niveau de blocage des fichiers avec la valeur par défaut, **Non configuré**.

**Extension du délai d’attente pour l’analyse des fichiers par le cloud**  

| | |
|--|--|
| Nombre de secondes (0-50) | Spécifiez la durée maximale avant que Windows Defender Antivirus ne bloque un fichier lors de l’attente d’un résultat du cloud. La durée par défaut est de 10 secondes : tout temps supplémentaire spécifié ici (jusqu'à 50 secondes) est ajouté à ces 10 secondes. Dans la plupart des cas, l’analyse prend beaucoup moins de temps que la valeur maximale. Prolonger la durée permet au cloud de rechercher des fichiers suspects de manière plus approfondie. Nous vous recommandons d’activer ce paramètre et de spécifier au moins 20 secondes supplémentaires. |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix ajouté pour les appareils Windows 10 <!-- 1512457 -->  
Vous pouvez configurer un VPN Citrix pour les appareils Windows 10. Vous pouvez choisir le VPN Citrix dans la liste *Sélectionner un type de connexion* du panneau **VPN de base** quand vous configurez un VPN pour Windows 10 et ultérieur.

> [!Note]
> Une configuration de Citrix existait pour iOS et Android.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Les connexions Wi-Fi prennent en charge les clés prépartagées sur iOS <!-- 1550823 -->
Les clients peuvent configurer des profils Wi-Fi pour utiliser des clés prépartagées pour les connexions personnelles WPA/WPA2 sur les appareils iOS. Ces profils sont envoyés à l’appareil de l’utilisateur quand l’appareil est inscrit dans Intune.

Quand le profil a été envoyé à l’appareil, l’étape suivante varie en fonction de la configuration du profil.  S’il est configuré pour se connecter automatiquement, il le fait quand l’accès réseau est nécessaire.  Quand le profil se connecte manuellement, l’utilisateur doit activer la connexion manuellement.  

### <a name="intune-apps"></a>Applications Intune

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Accès aux journaux d’applications gérées pour iOS <!-- 1469920 -->
Les utilisateurs finaux disposant de Managed Browser peuvent désormais afficher l’état de gestion de toutes les applications Microsoft publiées, et envoyer les journaux afin de dépannage leurs applications iOS gérées.

Pour découvrir comment activer le mode de dépannage dans Managed Browser sur un appareil iOS, consultez [Comment accéder aux journaux des applications gérées à l’aide de Managed Browser sur iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Améliorations apportées au workflow de configuration des appareils sur le Portail d’entreprise pour iOS dans la version 2.9.0<!-- 1417174 -->

Le workflow de configuration des appareils a été amélioré dans l’application Portail d’entreprise pour iOS. La langue est plus conviviale, et nous avons regroupé des écrans dans la mesure du possible. La langue est également plus adaptée à l’entreprise, car nous utilisons à chaque fois son nom dans le texte de configuration. Vous pouvez voir ce workflow mis à jour sur la page  [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md).

### <a name="monitor-and-troubleshoot"></a>Surveiller et dépanner

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>L’entité Utilisateur contient les données utilisateur les plus récentes dans le modèle de données de l’entrepôt de données <!-- 1544273 -->
La première version du modèle de données de l’entrepôt de données Intune ne contenait que des données Intune historiques récentes. Les auteurs de rapports ne pouvaient pas capturer l’état actuel d’un utilisateur. Dans cette mise à jour, **l’entité Utilisateur** est renseignée avec les données utilisateur les plus récentes.


## <a name="notices"></a>Remarques

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>Modification planifiée : nouveau paramètre Windows 10 pour la configuration plein écran dans Intune <!-- 1560072 -->
Nous allons changer le mode et l’emplacement de configuration des postes de travail Windows 10 1709 et versions ultérieures (RS3 et versions ultérieures) dans le portail Azure Intune.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ? 
Selon nos informations, vous utilisez le paramètre Windows 10 > Restrictions de l’appareil > Plein écran (préversion). Ce paramètre sera renommé en mai de la façon suivante : Windows 10 > Restrictions de l’appareil > Plein écran (obsolète) dans l’IU pour indiquer que son utilisation n’est plus recommandée. Toutefois, il continuera de fonctionner jusqu’à la mise à jour de juillet d’Intune. Ensuite, il sera rendu obsolète dans le backend et ne fonctionnera plus. À la place, nous publions un nouveau profil de configuration d’appareil en mai : Windows 10 > Plein écran, qui contient les paramètres de configuration des modes plein écran sur Windows 10 RS4 et les versions ultérieures.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?  
Quand Intune publiera la mise à jour du service vers la fin du mois de mai, nous vous communiquerons les instructions nécessaires pour tester et vérifier si vous pouvez effectuer la migration de votre configuration Plein écran de Windows 10 RS3 vers Windows 10 RS4. Suivez ces instructions pour configurer le mode plein écran de vos appareils à l’aide du nouveau profil de configuration d’appareil pour mode plein écran.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Cette modification affecte à la fois les clients autonomes Intune et les clients hybrides (Intune avec Configuration Manager). Cette intégration permet de simplifier l’administration de votre gestion cloud. En effet, vous n’avez plus qu’un seul panneau dans Azure – le panneau Intune – pour gérer des groupes, des stratégies, des applications et toute gestion d’appareils mobiles.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Mettez Intune en favori à la place du panneau du service Protection d’application Intune et veillez à vous familiariser avec le workflow de stratégie de protection d’application dans le panneau Application mobile dans Intune. Pendant une courte période, nous assurerons la redirection puis nous supprimerons le panneau Protection d’application. N’oubliez pas que toutes les stratégies de protection d’application sont déjà hors service dans Intune et que vous pouvez modifier les stratégies d’accès conditionnel en suivant la documentation ici : [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Informations supplémentaires** : [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-windows-company-portal-send-feedback-option-may-no-longer-work"></a>Modification planifiée : l’option d’envoi de commentaires du Portail d’entreprise Windows risque de ne plus fonctionner  
L’application Portail d’entreprise Windows dispose d’une option **Envoyer des commentaires**, qui permet aux utilisateurs d’adresser à Microsoft des commentaires sur l’application. À partir du 30 avril 2018, cette option continuera d’être prise en charge uniquement sur l’application Portail d’entreprise Windows 10 exécutée sur Windows 10 1607 (Mise à jour anniversaire) et les versions ultérieures.  

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?  
Si l’application Portail d’entreprise Windows n’est pas installée pour les utilisateurs finaux, ignorez ce message. Si l’un de vos utilisateurs finaux dispose de l’application Portail d’entreprise, notez qu’à partir du 30 avril, le bouton **Envoyer des commentaires** ne fonctionnera plus pour l’application dans les scénarios suivants :  
- Application Portail d’entreprise Windows 10 utilisée dans les versions Windows 10 1507 et 1511  
- Application Portail d’entreprise Windows Phone 8.1  

Pour les appareils impactés, l’option **Envoyer des commentaires** ne fonctionnera pas, même après plusieurs tentatives. Pour envoyer des commentaires à Microsoft sur l’expérience utilisateur relative à ces plateformes, consultez les autres canaux de commentaires listés ci-dessous.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?  
Informez vos utilisateurs de ce changement et mettez à jour les conseils d’aide qui leur sont destinés, si nécessaire. Informez les utilisateurs finaux sur Windows Phone 8.1, Windows 10 1507 et Windows 10 1511 à l’aide du Portail d’entreprise qu’ils disposent de deux autres canaux de commentaires. Ils peuvent :  
- Utiliser l’application Hub de commentaires sur Windows 10
- Envoyer un e-mail à WinCPfeedback@microsoft.com  

Demandez aux utilisateurs finaux sur Windows 10 RS1 ou version ultérieure d’effectuer une mise à jour vers la dernière version du Portail d’entreprise Windows disponible dans le Store.

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Modification prévue : modification de la prise en charge du plug-in Cordova dans le SDK de l’application Microsoft Intune
Intune met fin au support du [plug-in Cordova du SDK de l’application Microsoft Intune](app-sdk-cordova.md) le 1er mai 2018. Nous vous recommandons d’utiliser l’outil de création de package de restrictions d’application Intune à la place, pour préparer vos applications basées sur Cordova afin qu’elles soient gérables et disponibles dans Intune. À la prise d’effet de ce changement, le SDK de l’application Microsoft Intune pour le plug-in Cordova ne sera plus tenu à jour et ne recevra pas de mises à jour. Les développeurs d’applications ne pourront pas utiliser ce plug-in. Intune prévoit de continuer la prise en charge des applications créées avec Cordova. Toutefois, toutes les applications créées avec le SDK de l’application Microsoft Intune pour le plug-in Cordova auront des fonctionnalités réduites dans Intune. Une fois traitées avec l’outil de création de package de restrictions d’application Intune, les applications peuvent être déployées pour les utilisateurs finaux de façon habituelle. Pour les applications Android basées sur Cordova publiées dans Google Play Store :
- Les utilisateurs finaux sont invités à indiquer leurs informations d’identification pour recevoir la stratégie Intune au premier lancement.
- Les applications doivent être publiées dans l’App Store ciblé pour les utilisateurs Intune, par exemple « Application Contoso pour Intune ».

Pour plus d’informations sur l’outil de création de package de restrictions d’application, consultez [Outil de création de package de restrictions d’application pour iOS](app-wrapper-prepare-ios.md) et [Outil de création de package de restrictions d’application pour Android](app-wrapper-prepare-android.md). Pour tout problème ou toute question, contactez [ msintuneappsdk@microsoft.com ](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Modification planifiée : utiliser Intune sur Azure maintenant pour la gestion des appareils mobiles<!-- 1227338 -->
Il y a plus d’un an, nous avons annoncé une [préversion publique d’Intune sur Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) et avons donné suite six mois auparavant avec la [disponibilité générale de la nouvelle expérience d’administration](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) pour Intune. À partir du 31 août 2018, la gestion des périphériques mobiles (GPM) sera désactivée sur la console Silverlight classique pour les clients qui utilisent Intune autonome. Vous pouvez utiliser à la place [Intune sur Azure](https://aka.ms/Intune_on_Azure) pour vos besoins de gestion des appareils mobiles. Si vous utilisez toujours la console classique pour la gestion des appareils mobiles, arrêtez et familiarisez-vous avec Intune sur Azure. Cette modification ne devrait pas avoir d’impact sur les utilisateurs finaux. La gestion classique des PC restera dans Silverlight. Vous trouverez plus d’informations sur cette modification et la façon dont elle vous affecte [ici](https://aka.ms/Intune_on_Azure_mdm).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accès direct aux scénarios d’inscription d’Apple <!--951869-->
Pour les comptes Intune créés après janvier 2017, Intune a activé un accès direct aux scénarios d’inscription Apple à l’aide de la charge de travail Inscrire des appareils dans le portail Azure. Auparavant, la version préliminaire de l’inscription Apple était uniquement accessible à partir de liens dans le portail classique Intune. Les comptes Intune créés avant janvier 2017 nécessitent une migration unique pour que ces fonctionnalités deviennent disponibles dans Azure. La planification de la migration n’a pas encore été annoncée, mais les détails correspondants seront diffusés dès que possible. Si votre compte existant ne peut pas accéder au portail Azure, nous vous recommandons vivement de créer un compte d’essai afin de tester la nouvelle expérience.

## <a name="whats-coming"></a>Nouveautés à venir

### <a name="local-device-security-option-settings----1251887---"></a>Paramètres d’option de sécurité d’appareil local <!-- 1251887 -->
Vous pourrez activer les paramètres de sécurité sur les appareils Windows 10 à l’aide des nouveaux paramètres présents dans Options de sécurité locales de l’appareil. Recherchez ces paramètres dans la catégorie Endpoint Protection quand vous créez une stratégie de configuration d’appareil Windows 10.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Nouvelle mise à jour de l’expérience utilisateur du site web Portail d’entreprise<!--2000968-->

Nous avons introduit une nouvelle expérience du site web Portail d’entreprise en avril, avec des mises à jour de l’interface utilisateur, des workflows simplifiés et des améliorations apportées à l’accessibilité. Cette nouvelle expérience inclut des améliorations demandées par les clients comme le partage d’applications et l’amélioration des performances globales pour plus de convivialité.
Nous avons ajouté de nouvelles fonctionnalités en nous basant sur les commentaires que nous ont envoyés des clients comme vous, afin d’améliorer considérablement les fonctionnalités existantes et leur mode d’utilisation :

-   Améliorations de l’interface utilisateur dans l’ensemble du site web
-   Possibilité de partager des liens directs vers les applications
- Performances améliorées des grands catalogues d’applications

Vous n’avez rien à faire pour vous préparer à ce changement. Nous vous informerons quand le site web Portail d’entreprise sera mis à jour et à votre disposition. Toutefois, vous devrez éventuellement mettre à jour les documents destinés aux utilisateurs finaux avec des captures d’écran actualisées. Notez que vous devez également mettre à jour la documentation de l’application Portail d’entreprise sur iOS, étant donné que le site web alimente la section **Applications** de l’application iOS. Vous pouvez voir un exemple d’image sur la page [Nouveautés de l’interface utilisateur de l’application](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Mises à jour requises par Apple pour Application Transport Security <!--748318-->
La société Apple a annoncé qu’elle appliquera des exigences spécifiques pour ATS (Application Transport Security). ATS est utilisé pour renforcer la sécurité de toutes les communications d’application via le protocole HTTPS. Cette modification a une incidence sur les clients Intune qui utilisent les applications de portail d’entreprise iOS. Nous donnerons tous les détails nécessaires sur notre [Blog pour le support Intune](https://aka.ms/compportalats).



## <a name="see-also"></a>Voir aussi
* [Blog Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Feuille de route de la plateforme cloud](https://www.microsoft.com/cloud-platform/roadmap)
* [Nouveautés de l’interface utilisateur du portail d’entreprise](whats-new-app-ui.md)
* [Nouveautés des mois précédents](whats-new-archive.md)
