---
title: Édition préliminaire
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0500194f5afaba11f37b84bbdf606e6167632a71
ms.sourcegitcommit: afa2e84d5cadf5542ecabc26e61dc71919992a22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340176"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Édition préliminaire pour Microsoft Intune - Juillet 2018

> [!Note]
> Notification de l’accord de confidentialité : Les modifications suivantes sont en cours de développement pour Intune. Ces informations sont partagées selon les termes de l’accord de confidentialité, de façon très limitée. Ne publiez aucune de ces informations sur des médias sociaux ou des sites web publics comme Twitter, UserVoice, Reddit, etc. 

**L’édition préliminaire** fournit la liste des fonctionnalités, partagée selon les termes de l’accord de confidentialité, qui seront intégrées dans les prochaines versions de Microsoft Intune. Ces informations sont fournies de manière limitée et sont susceptibles de changer. Ne tweetez pas, ne publiez sur UserVoice et ne partagez pas ces informations en dehors de votre entreprise. Certaines fonctionnalités répertoriées ici risquent de ne pas être prêtes d’ici la date limite et d’être repoussées à une version ultérieure. D’autres fonctionnalités sont en cours de test dans un pilote (version d’évaluation) pour s’assurer qu'elles sont prêtes à l'emploi. Joignez votre contact de groupe de produits Microsoft si vous avez des questions ou rencontrez des problèmes.

Cette page est mise à jour périodiquement. Consultez-la régulièrement pour savoir si des mises à jour supplémentaires sont disponibles.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune dans le portail Azure

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Réinitialiser les codes secrets des appareils à partir de l’application Portail d’entreprise pour Windows 10 <!-- 2101282 --> 
Vos employés seront bientôt en mesure de réinitialiser le code PIN ou le code secret de leur appareil directement de l’application Portail d’entreprise pour Windows 10. Cette fonctionnalité sera disponible sur les appareils locaux et distants gérés par Intune qui prennent en charge les réinitialisations de codes secrets. Selon le type d’appareil, les demandes pour un appareil distant supprimeront le code secret actuel de l’appareil ou créeront un code secret temporaire. Les utilisateurs qui demanderont une réinitialisation pour un appareil local seront redirigés vers l’application des paramètres de l’appareil.

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Utiliser S/MIME pour chiffrer et signer les appareils d’un utilisateur  <!-- 1333642 -->
Une prochaine mise à jour va inclure le chiffrement S/MIME des e-mails à l’aide d’un nouveau profil de certificat importé (**Configuration de l’appareil** > **Profils** > **Créer un profil** > sélectionner la plateforme > **Certificat importé PKCS** type de profil). Dans Intune, vous pouvez importer des certificats au format PFX. Intune peut alors émettre ces mêmes certificats à plusieurs appareils inscrits par un seul utilisateur. Cela comprend également :

- Le profil de messagerie iOS natif prend en charge l’activation du chiffrement S/MIME avec des certificats importés au format PFX.
- L’application de messagerie native sur les appareils Windows Phone 10 utilise automatiquement le certificat S/MIME.
- Les certificats privés peuvent être émis sur plusieurs plateformes. Toutefois, les applications de messagerie ne prennent pas toutes en charge S/MIME.
- Sur d’autres plateformes, vous devrez peut-être configurer manuellement l’application de messagerie pour activer S/MIME.  
- Les applications de messagerie qui prennent en charge le chiffrement S/MIME peuvent gérer la récupération de certificats pour le chiffrement S/MIME des e-mails d’une manière que MDM ne peut pas prendre en charge, comme la lecture à partir du magasin de certificats de leur éditeur.

Prise en charge sur : Windows, Windows Phone 10, macOS, iOS, Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilisation de licences d’appareil VPP pour préprovisionner le portail d’entreprise lors d’une inscription DEP <!-- 1608345 -->
Vous allez pouvoir utiliser des licences d’appareil du programme VPP (Volume Purchase Program) pour préprovisionner le portail d’entreprise pendant les inscriptions DEP (Device Enrollment Program). Pour ce faire, lorsque vous créez ou modifiez un profil d’inscription, spécifiez le jeton VPP que vous souhaitez utiliser pour installer le portail d’entreprise. Assurez-vous que votre jeton n’expire pas et que vous avez suffisamment de licences pour l’application Portail d’entreprise. Si le jeton arrive à expiration ou s’il manque des licences, Intune pousse le Portail d’entreprise de l’App Store à la place (un identifiant Apple vous sera demandé).

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Suppression en bloc d’appareils dans le panneau Appareils <!-- 1793693 -->
Vous allez pouvoir supprimer plusieurs appareils à la fois dans le panneau Appareils. Choisissez **Appareils** > **Tous les appareils** > sélectionner les appareils à supprimer > **Supprimer**. Pour les appareils qui ne peuvent pas être supprimés, une alerte s’affiche.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nouveau profil de configuration d’appareils Wi-Fi pour Windows 10 et ultérieur <!-- 1879077 -->
Actuellement, vous pouvez importer et exporter des profils Wi-Fi à l’aide de fichiers XML. Vous allez pouvoir créer un profil de configuration d’appareils Wi-Fi directement dans Intune, tout comme dans certaines autres plateformes.

Pour créer le profil, ouvrez **Configuration de l’appareil** > **Profils** > **Créer un profil** > **Windows 10 et ultérieur** > **Wi-Fi**. 

S’applique à Windows 10 et versions ultérieures.

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Renommage des extensions de fichier des applications métier Windows <!-- 1884873 -->
Les extensions de fichier des applications métier Windows *.appx* et *.appxbundle* vont être renommées *.msix* et *.msixbundle*. Vous pouvez ajouter une application dans Microsoft Intune en sélectionnant **Applications mobiles** > **Applications** > **Ajouter**. Le volet **Ajouter une application** s’affiche et vous permet de sélectionner le **Type d’application**. Pour les applications métier Windows, sélectionnez **Métier** comme type d’application, sélectionnez **Fichier de package d’application**, puis entrez un fichier d’installation avec l’extension appropriée.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Ajout automatique du package de configuration de Windows Defender ATP au profil de configuration <!-- 2144658 -->
Actuellement, quand vous utilisez des appareils [ATP (Advanced Threat Protection) et d’intégration](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) dans Intune, vous téléchargez un package de configuration et vous l’ajoutez à votre profil de configuration. Dans une prochaine mise à jour, Intune prendra automatiquement le package dans le Centre de sécurité Windows Defender et l’ajoutera à votre profil.

S’applique à Windows 10 et versions ultérieures.

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kiosque (obsolète) est grisé et ne peut pas être modifié. <!-- 2149998 -->
La [fonctionnalité Kiosque](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuration de l’appareil** > **Profils** > **Créer un profil**  >  **Windows 10 et ultérieur** > **Restrictions d’appareil**) va devenir obsolète pour être remplacée par [Paramètres Kiosque pour Windows 10 et ultérieur](kiosk-settings.md). La fonctionnalité **Kiosque (obsolète)** va être grisée et il sera impossible de changer ou de mettre à jour l’interface utilisateur. 

Pour activer le mode Kiosque, consultez [Paramètres Kiosque pour Windows 10 et ultérieur](kiosk-settings.md).

S’applique à Windows 10 et ultérieur, Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>Utilisation d’autorités de certification tierces par les API <!-- 2184013 -->
Une API Java va être ajoutée pour l’intégration d’autorités de certification tierces dans Intune et SCEP. Ensuite, les utilisateurs pourront ajouter le certificat SCEP à un profil et l’appliqueront aux appareils avec MDM.

Actuellement, Intune prend en charge les [demandes SCEP avec les services de certificats Active Directory](certificates-scep-configure.md).

### <a name="check-for-sccm-compliance----2192052---"></a>Vérification de la conformité SCCM <!-- 2192052 -->
Une prochaine mise à jour va offrir un nouveau paramètre de conformité System Center Configuration Manager (SCCM) (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**   >  **Windows 10**). SCCM envoie des signaux pour la conformité Intune. À l’aide du paramètre Intune, vous pouvez exiger que tous les signaux SCCM retournent « conforme ».

Par exemple, vous voulez que toutes les mises à jour logicielles soient installées sur les appareils. Dans SCCM, cette exigence présente l’état « Installé ». Si les programmes de l’appareil sont dans un état inconnu, l’appareil est non conforme dans Intune.

S’applique à Windows 10 et ultérieur

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertes pour l’expiration du jeton VPP ou pour le nombre insuffisant de licences du portail d’entreprise <!-- 2237572 -->
Si vous utilisez le programme d’achat en volume (VPP) pour préprovisionner le portail d’entreprise lors de l’inscription DEP, Intune vous alerte quand le jeton VPP est sur le point d’expirer et qu’il ne reste plus beaucoup de licences pour le portail d’entreprise.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmation obligatoire pour supprimer un jeton VPP utilisé pour le préprovisionnement du portail d'entreprise <!-- 2237634 -->
Une confirmation sera obligatoire pour supprimer un jeton VPP (Volume Purchase Program) si celui-ci est utilisé pour préprovisionner le portail d’entreprise lors d’une inscription DEP.

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marquage automatique des appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile comme « entreprise » <!-- 2404851 -->
Par défaut, les appareils Android inscrits à l’aide de l’inscription Samsung Knox Mobile seront marqués **entreprise** sous **Propriété de l’appareil**. Vous n’aurez pas à identifier manuellement les appareils d’entreprise avec leur numéro IMEI ou de série avant de les inscrire à l’aide de l’inscription Knox Mobile.

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Affichage ou masquage du bouton Terminer la session sur un navigateur Kiosque <!-- 2455253 -->
Vous pourrez configurer les navigateurs Kiosque pour afficher ou non le bouton Terminer la session ou non. Vous pourrez voir la commande dans **Configuration de l’appareil** > **Kiosque (préversion)** > **Navigateur web kiosque**. Si elle est activée, quand un utilisateur clique sur le bouton, l’application demande une confirmation pour terminer la session. Lorsque vous confirmez, le navigateur efface toutes les données de navigation et retourne à l’URL par défaut.

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Créer un profil de configuration mobile eSIM <!-- 2564077 -->
Dans **Configuration de l’appareil**, vous pourrez créer un profil mobile eSIM. Vous pouvez importer un fichier qui contient les codes d’activation mobiles fournis par votre opérateur mobile. Vous pouvez ensuite déployer ces profils sur vos appareils Windows 10 eSIM LTE, tels que Surface Pro LTE et autres appareils compatibles eSIM.

Vérifiez si vos [appareils prennent en charge les profils eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

S’applique à Windows 10 et versions ultérieures. 




<!-- 1806 start -->

### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Affichage des profils de configuration d’appareil en conflit <!-- 1556983 -->
Dans **Configuration de l’appareil**, vous voyez une liste des profils existants. Avec cette mise à jour, une nouvelle colonne qui fournit des détails sur les profils en conflit a été ajoutée. Vous pouvez sélectionner une ligne en conflit pour voir le paramètre et le profil en conflit. 

Découvrez-en plus sur les [profils de configuration d’appareil](device-profiles.md).

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>Prise en charge des appareils Android COSU (corporate-owned, single use)<!-- 1630973 -->

Intune prend en charge les appareils Android hautement gérés, verrouillés et de style kiosque. Cela permet aux administrateurs de verrouiller davantage l’utilisation d’un appareil à une seule application ou à un petit ensemble d’applications, et empêche les utilisateurs d’activer d’autres applications ou d’effectuer d’autres actions sur l’appareil.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Prise en charge de macOS pour le Programme d’inscription des appareils Apple <!-- 747651 -->

Intune prend en charge l’inscription d’appareils macOS dans le Programme d’inscription des appareils (DEP) Apple. Pour cela :

1. Sur deploy.apple.com, affectez les numéros de série macOS à un serveur MDM.
2. Importez les numéros de série dans Intune.
3. Créez un profil de programme d’inscription propre aux appareils macOS.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Changement des noms Google pour Android for Work et Play for Work <!--842873 -->
Intune met à jour la terminologie « Android for Work » pour refléter les changements apportés à la personnalisation de Google.  Les termes « Android for Work » et « Play for Work » ne sont plus utilisés. Une terminologie différente sera utilisée en fonction du contexte :

- « Android Enterprise » fait référence à la pile de gestion Android moderne globale.
- « Profil professionnel » ou « Propriétaire du profil » fait référence à des appareils BYOD gérés avec des profils professionnels.
- « Google Play géré » fait référence à l’App Store Google.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Surveiller l’état de configuration d’applications iOS par appareil <!-- 880037 eeready eestaged -->

En tant qu’administrateur Microsoft Intune, vous pouvez surveiller l’état de configuration d’applications iOS pour chaque appareil géré. À partir de **Microsoft Intune** dans le portail Azure, sélectionnez **Appareils** > **Tous les appareils**. Dans la liste des appareils gérés, sélectionnez un appareil spécifique pour afficher le panneau correspondant. Dans le panneau de l’appareil, sélectionnez **Configuration de l’application**.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Les claviers tiers peuvent être bloqués par des paramètres APP sur iOS <!-- 1248481 -->
Sur les appareils iOS, les administrateurs Intune peuvent bloquer l’utilisation de claviers tiers lors de l’accès à des données d’entreprise dans des applications protégées par une stratégie. Quand la stratégie de protection d’application (APP, Application Protection Policy) est configurée pour bloquer les claviers tiers, l’utilisateur de l’appareil reçoit un message la première fois qu’il interagit avec des données d’entreprise en utilisant un clavier tiers. Toutes les options autres que celles du clavier natif sont bloquées et les utilisateurs d’appareils ne les voient pas. La boîte de message ne s’affiche qu’une seule fois aux utilisateurs. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Créer une stratégie de conformité des appareils à l’aide de paramètres de pare-feu sur ses appareils macOS <!-- 1497640 -->
Quand vous créez une stratégie de conformité macOS (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : macOS** > **Sécurité du système**), de nouveaux paramètres **Pare-feu** sont disponibles : 
- **Pare-feu** : configurez la façon dont les connexions entrantes sont traitées dans votre environnement.
- **Connexions entrantes** : **Bloquer** toutes les connexions entrantes, à l’exception de celles nécessaires aux services Internet de base, par exemple DHCP, Bonjour et IPsec. Ce paramètre bloque également tous les services de partage.
- **Mode furtif** : **Activer** le mode furtif pour empêcher l’appareil de répondre aux demandes de sondage. L’appareil continue de répondre aux requêtes entrantes des applications autorisées.

S’applique à : macOS 10.12 et versions ultérieures

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Utiliser SamAccountName comme nom d’utilisateur de compte pour les profils de messagerie <!-- 1500307 -->

Vous pouvez utiliser le **SamAccountName** local comme nom d’utilisateur de compte pour les profils de messagerie pour Android, iOS et Windows 10. Vous pouvez également obtenir le domaine à partir de l’attribut `domain` ou `ntdomain` dans Azure Active Directory (Azure AD). Il est également possible d’entrer un domaine statique personnalisé.

Pour utiliser cette fonctionnalité, vous devez synchroniser l’attribut `sAMAccountName` de votre environnement Active Directory local avec Azure AD.

S’applique à : Android, iOS et Windows 10 et versions ultérieures

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exiger un code secret non biométrique au lancement de l’application et après un délai d’expiration <!-- 1506985 -->

En exigeant un code secret non biométrique au lancement de l’application et après un délai d’expiration spécifié par l’administrateur, Intune offre une sécurité renforcée pour les applications compatibles avec la gestion des applications mobiles (MAM) en limitant l’utilisation de l’identification biométrique pour l’accès aux données d’entreprise. Les paramètres affectent les utilisateurs qui s’appuient sur Touch ID (iOS), Face ID (iOS), Android Biométrique ou d’autres méthodes d’authentification biométriques à venir pour accéder à leurs applications compatibles APP/MAM. Ces paramètres permettent aux administrateurs Intune d’avoir un contrôle plus précis sur l’accès utilisateur, en supprimant les cas où un appareil avec plusieurs empreintes digitales ou d’autres méthodes d’accès biométriques peut révéler des données d’entreprise à un utilisateur inapproprié. Dans le portail Azure, ouvrez **Microsoft Intune**. Sélectionnez **Applications mobiles** > **Stratégies de protection des applications** > **Ajouter une stratégie** > **Paramètres**. Recherchez la section **Accès** pour des paramètres spécifiques.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Réinitialisation sélective des données d’application de l’organisation <!-- 1507030 -->
Les administrateurs peuvent configurer une réinitialisation sélective des données de l’organisation comme une nouvelle action quand les conditions des paramètres d’accès APP (stratégies de protection d’application) ne sont pas remplies.  Cette fonctionnalité permet aux administrateurs de protéger et de supprimer automatiquement des données d’entreprise sensibles dans des applications en fonction de critères préconfigurés.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Révocation d’une application iOS achetée par le biais d’un programme VPP <!-- 1777384 -->
En tant qu’administrateur Microsoft Intune, vous pouvez révoquer la licence pour une application iOS sélectionnée achetée via le programme d’achat en volume (VPP). Vous pouvez notifier les utilisateurs quand une application ne leur est plus affectée. La révocation d’une licence d’application ne désinstalle pas l’application VPP de l’appareil. Pour désinstaller une application VPP, vous devez remplacer l’action d’attribution par **Désinstaller**. Le nombre de licences récupérées est répercutée dans le nœud **Applications sous licence** dans la charge de travail **Application** d’Intune. Pour plus d’informations sur les applications VPP iOS, consultez [Guide pratique pour gérer les applications iOS achetées par le biais d’un programme d’achat en volume avec Microsoft Intune](vpp-apps-ios.md).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Modules linguistiques Office 365 Pro Plus <!-- 1833450 -->
En tant qu’administrateur Intune, vous pouvez déployer des langues supplémentaires pour les applications Office 365 Pro Plus gérées par le biais d’Intune. La liste des langues disponibles inclut le **Type** du module linguistique (principal, partiel et de vérification). Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications mobiles** > **Applications** > **Ajouter**. Dans la liste **Type d’application** du panneau **Ajouter une application**, sélectionnez **Windows 10** sous la **Suite Office 365**. Sélectionnez **Langues** dans le panneau **Paramètres de la suite d’applications**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Révoquer une licence d’application VPP iOS <!-- 1863797 -->
En tant qu’administrateur, vous pouvez récupérer une licence d’application VPP iOS attribuée à un utilisateur ou un appareil. Désinstaller une application VPP iOS vous permet également de récupérer la licence de l’application. Vous pouvez ensuite choisir d’attribuer la licence de l’application à un autre utilisateur ou appareil. Pour plus d’informations sur les licences d’application VPP iOS, consultez [Gérer les applications iOS achetées en volume dans Microsoft Intune](vpp-apps-ios.md).

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Aperçu d’une nouvelle mise à jour de l’expérience utilisateur du site web Portail d’entreprise<!--2000968 -->
En nous basant sur les commentaires que nous ont envoyés des clients, nous ajoutons de nouvelles fonctionnalités au site web Portail d’entreprise/Catalogue d’applications iOS. Vous allez constater une nette amélioration des fonctionnalités existantes et de la facilité d’utilisation dans vos appareils Android, iOS et Windows. Les différentes zones du site, telles que les détails de l’appareil, les commentaires et le support, ainsi que la vue d’ensemble de l’appareil, vont bénéficier d’une nouvelle présentation interactive et moderne. Vous verrez également :

- Flux de travail simplifiés sur toutes les plateformes d’appareils
- Flux d’identification et d’inscription des appareils améliorés
- Plus de messages d’erreur utiles
- Langage plus convivial, avec moins de jargon technique
- Possibilité de partager des liens directs vers les applications
- Performances améliorées des grands catalogues d’applications
- Accessibilité accrue pour tous les utilisateurs

La mise à jour est actuellement en préversion. Vous pouvez vous inscrire pour accéder à la préversion http://aka.ms/webcpflighting

### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Mises à jour pour les messages de non-conformité dans l’application Portail d’entreprise <!-- 1832222 -->
Nous révisons les messages que les utilisateurs d’appareils voient quand un appareil est hors conformité. Les messages conserveront leur sens d’origine, mais ils seront formulés dans un style plus convivial et avec moins de jargon technique. Nous actualisons également les liens vers la documentation et les étapes de correction pour qu’ils soient à jour.  

Voici un exemple d’amélioration de message, avec le texte avant et après modification :  

Avant : *Cet appareil n’a pas contacté le service Intune dans l’intervalle de temps spécifié par votre administrateur informatique. Pour résoudre ce problème, ouvrez l’application Portail d’entreprise sur votre appareil et cliquez sur le bouton Vérifier la conformité.*  

Après : *Votre appareil ne s’est pas connecté à votre organisation depuis un certain temps. Pour rétablir la connexion, ouvrez l’application Portail d’entreprise sur votre appareil, puis appuyez sur Vérifier les paramètres de votre appareil*.  

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modifier vos déploiements d’applications Office 365 Pro Plus <!-- 2150145 -->
En tant qu’administrateur Microsoft Intune, vous avez une plus grande capacité de modification de vos déploiements d’applications Office 365 Pro Plus. Dans le portail Azure, sélectionnez **Microsoft Intune** > **Applications mobiles** > **Applications**. Dans la liste des applications, sélectionnez votre suite Office 365 Pro Plus.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Consultation par ligne des identificateurs d’appareil d’entreprise en double chargés <!-- 2203794 -->
Lors du chargement d’ID d’appareils d’entreprise, Intune fournit une liste de tous les doublons et vous donne la possibilité de remplacer ou de conserver les informations existantes. Le rapport s’affiche s’il existe des doublons après avoir choisi **Inscription de l’appareil** > **Identificateurs d’appareil d’entreprise** > **Ajouter des identificateurs**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Ajouter manuellement des identificateurs d’appareil d’entreprise <!-- 2203803 -->
Vous pouvez ajouter manuellement des ID d’appareil d’entreprise. Dans **Inscription de l’appareil** > **Identificateurs d’appareils d’entreprise** > **Ajouter**.

### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nouveaux états pour les appareils dans la conformité des appareils <!-- 2308882 -->
Dans **Conformité de l’appareil** > **Stratégies** > Sélectionner une stratégie > **Vue d’ensemble**, les nouveaux états suivants ont été ajoutés :
- réussi
- erreur
- conflit
- en attente
- non applicable

Une image indiquant le nombre d’appareils d’une autre plateforme est également affichée. Par exemple, si vous regardez un profil iOS, la nouvelle vignette indique le nombre d’appareils non iOS qui sont également attribués à ce profil. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>La conformité de l’appareil prend en charge les solutions antivirus tierces <!-- 2325484 -->
Quand vous créez une stratégie de conformité des appareils (**Conformité de l’appareil** > **Stratégies** > **Créer une stratégie** > **Plateforme : Windows 10 et versions ultérieures** > **Paramètres** > **Sécurité du système**), il existe de nouvelles options **Sécurité de l’appareil** : 
- **Antivirus** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions antivirus inscrites auprès du Centre de sécurité Windows, comme Symantec. 
- **Logiciel anti-espion** : quand la valeur définie est **Exiger**, vous pouvez vérifier la conformité en utilisant des solutions de logiciel anti-espion inscrites auprès du Centre de sécurité Windows, comme Symantec. 

S’applique à : Windows 10 et versions ultérieures 

<!-- 1805 start -->

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Amélioration de la résolution des problèmes d’installation des applications <!-- 928990 -->
Sur les appareils gérés par MDM Microsoft Intune, les installations d’applications peuvent parfois échouer. Quand ces installations d’applications échouent, il peut être difficile de comprendre la raison de l’échec ou de résoudre le problème. Nous publions une préversion publique de nos fonctionnalités de résolution des problèmes d’application. Vous remarquerez sous chaque appareil un nouveau nœud appelé **Applications gérées**. Il liste les applications qui ont été distribuées via MDM Intune. À l’intérieur du nœud figure une liste d’états d’installations d’applications. Si vous sélectionnez une application, vous verrez la vue de résolution des problèmes de cette application spécifique. Dans la vue de résolution des problèmes, vous verrez le cycle de vie de bout en bout de l’application, par exemple quand l’application a été créée, modifiée, ciblée et remise à un appareil. De plus, si l’installation de l’application a échoué, vous verrez le code d’erreur et un message utile sur la cause de l’erreur.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exiger un code secret non biométrique au lancement à froid de l’application et après un délai d’expiration <!-- 1506985 --> 

En exigeant un code secret non biométrique au lancement à froid de l’application et après un délai d’expiration spécifié par l’administrateur, Intune offre une sécurité renforcée pour les applications compatibles avec la gestion des applications mobiles (MAM) en limitant l’utilisation de l’identification biométrique pour l’accès aux données d’entreprise. Les paramètres affectent les utilisateurs qui s’appuient sur Touch ID (iOS), Face ID (iOS), Android Biométrique ou d’autres méthodes d’authentification biométriques à venir pour accéder à leurs applications compatibles APP/MAM. Ces paramètres permettent aux administrateurs Intune d’avoir un contrôle plus précis sur l’accès utilisateur, en supprimant les cas où un appareil avec plusieurs empreintes digitales ou d’autres méthodes d’accès biométriques peut révéler des données d’entreprise à un utilisateur inapproprié. Dans le portail Azure, ouvrez **Microsoft Intune**. Sélectionnez **Applications mobiles** > **Stratégies de protection des applications** > **Ajouter une stratégie** > **Paramètres**. Recherchez la section **Accès** pour des paramètres spécifiques.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloquer l’accès à l’application en fonction des modèles et des fournisseurs d’appareils non approuvés  <!-- 1425689 ! -->
L’administrateur informatique Intune pourra appliquer une liste de fabricants Android et/ou de modèles iOS par le biais de stratégies de protection des applications Intune. L’administrateur informatique peut fournir une liste de fabricants (séparés par des points-virgules) pour les stratégies Android et une liste de modèles d’appareils pour les stratégies iOS. Les stratégies de protection des applications Intune concernent uniquement Android et iOS. Deux actions distinctes pourront être effectuées sur cette liste spécifiée :
- Blocage de l’accès à l’application sur les appareils qui ne figurent pas dans la liste, ou
- Réinitialisation sélective des données d’entreprise sur les appareils qui ne figurent pas dans la liste 

L’utilisateur ne peut pas accéder à l’application cible si les conditions requises par la stratégie ne sont pas remplies. En fonction des paramètres, l’utilisateur peut être bloqué ou une réinitialisation sélective de ses données d’entreprise est effectuée dans l’application. Sur les appareils iOS, cette fonctionnalité nécessite la participation des applications (par exemple WXP, Outlook, Managed Browser, Yammer) pour intégrer le kit Intune APP SDK dans le but d’appliquer les paramètres de version minimale dans les applications ciblées. Cette intégration se produit par propagation et dépend des équipes d’application spécifiques. Sur Android, cette fonctionnalité nécessite la version la plus récente du portail d’entreprise. 

Sur les appareils de l’utilisateur final, le client Intune effectuerait une action sur la base d’une mise en correspondance simple des chaînes spécifiées dans le panneau Intune pour les stratégies de protection d’application. Cela dépend entièrement de la valeur signalée par l’appareil. Par conséquent, il est conseillé à l’administrateur informatique de vérifier que le comportement prévu est exact. Pour ce faire, vous pouvez tester ce paramètre en ciblant différents fabricants d’appareils et modèles sur un petit groupe d’utilisateurs. Dans Microsoft Intune, sélectionnez **Applications mobiles** > **Stratégies de protection des applications** pour afficher et ajouter des stratégies de protection des applications. Pour plus d’informations sur les stratégies de protection d’application, consultez [Que sont les stratégies de protection des applications](app-protection-policy.md).

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Actions d’accès pour les stratégies de protection des applications <!-- 1483510 EEready -->
Vous pourrez bientôt configurer des stratégies de protection des applications afin de réinitialiser explicitement, de bloquer ou d’avertir les appareils non conformes. La nouvelle action *Réinitialiser* supprime d’un appareil les données d’entreprise de votre société. Si une réinitialisation se produit, l’utilisateur de l’appareil est informé de la raison de la réinitialisation et des étapes de correction. Pour certains paramètres, comme la version minimale du système d’exploitation, vous pourrez appliquer plusieurs actions telles que le blocage et la réinitialisation. Ces actions sont déclenchées quand l’application est lancée.

<!-- 1804 start -->

### <a name="rules-for-removing-devices----1609459---"></a>Règles de suppression des appareils <!-- 1609459 -->
De nouvelles règles seront disponibles pour vous permettre de supprimer automatiquement les appareils qui n’ont fait l’objet d’aucun archivage pendant un nombre de jours défini par vous-même. Pour voir la nouvelle règle, accédez au volet **Intune**, sélectionnez **Appareils**, puis sélectionnez **Règles de suppression d’appareil**.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Possibilité de déployer les applications métier requises pour tous les utilisateurs sur les appareils Windows 10 Desktop <!-- 1627835 RS4 -->
Les clients pourront déployer les applications Windows 10 métier requises à installer dans les contextes d’appareils. Ces applications seront alors disponibles pour tous les utilisateurs sur l’appareil. Seuls les appareils Windows 10 Desktop sont concernés.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Mise à jour de l’expérience Aide et commentaires sur l’application Portail d’entreprise pour Android <!--1631531 -->

L’expérience Aide et commentaires sur l’application Portail d’entreprise pour Android sera mise à jour de manière à pour se conformer aux bonnes pratiques pour les applications Android. L’application Portail d’entreprise pour Android sera mise à jour dans les prochains mois de manière à scinder l’élément de menu **Aide et commentaires** en deux éléments distincts **Aide** et **Envoyer des commentaires**. La page **Aide** contiendra une section **Questions fréquentes (FAQ)** et un bouton **Assistance par e-mail** pour amener les utilisateurs finaux à transmettre les journaux à Microsoft et à envoyer un e-mail au service de support de l’entreprise décrivant le problème. L’élément de menu **Envoyer des commentaires** permettra à l’utilisateur d’envoyer des commentaires à Microsoft. L’utilisateur devra choisir entre « J’aime quelque chose », « Je n’aime pas quelque chose » ou « J’ai une idée ».

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Stratégies de protection des applications  <!-- 679615 -->
Les stratégies Intune App Protection permettent de créer des stratégies globales, par défaut, afin d’activer rapidement la protection pour tous les utilisateurs dans l’ensemble du locataire.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Remarques

Il n’existe aucun avis actif pour l’instant.

### <a name="see-also"></a>Voir aussi
Voir [Nouveautés de Microsoft Intune](whats-new.md) pour en savoir plus sur les derniers développements.