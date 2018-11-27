---
title: Glossaire Microsoft Intune
titleSuffix: Microsoft Intune
description: Découvrez la signification de la terminologie utilisée dans Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 07/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd7b5613-ee9f-4dc3-990c-ab4c1d40720d
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bfab6f5f9c3b083ebcb0cee8820149fed7ce5c94
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188053"
---
# <a name="microsoft-intune-glossary"></a>Glossaire Microsoft Intune
Découvrez les définitions des termes courants utilisés dans Microsoft Intune.

## <a name="a"></a>Objet

|||
|-|-|
|Affectation d’applications|Permet aux utilisateurs de [rechercher, télécharger et installer](/intune/app-management) les applications dont ils ont besoin. Cela était précédemment appelé *déploiement d’applications*.|
|Profil de configuration d’application <br/><br/>Stratégie de configuration des applications|Disponible pour les applications mobiles présentant des configurations spécifiques à leur fournisseur. Configure une application [iOS](/intune/app-configuration-policies-use-ios) ou [Android](/intune/app-configuration-policies-use-android) avec des paramètres spécifiques avant son exécution.|
|Surveillance des applications|Vous permet de [passer en revue les activités et l’état récents](/intune/apps-monitor) liés à l’affectation de l’application.|
|Tâche de suppression des données de protection d’application|[Supprime les données d’application](/intune/app-protection-policies) de l’appareil de l’utilisateur.|
|Stratégie de protection des applications|Disponible pour les applications mobiles qui s’intègrent aux technologies Enterprise Mobility + Security (EMS). Permet de s’assurer que les applications de l’utilisateur sont conformes avec vos [stratégies de protection des données d’entreprise](/intune/app-protection-policies).|
|SDK d’application|Le [SDK d’application Microsoft Intune](/intune/app-sdk) vous permet d’ajouter des fonctionnalités à vos applications développées en interne, qui leur permettent d’être gérées par des stratégies de protection des applications.|
|Action de désinstallation d’application|Vous permet de [désinstaller des applications](/intune/apps-deploy) des appareils des utilisateurs.|
|Outil de création de package de restrictions d’application|[Application de ligne de commande](/intune/apps-prepare-mobile-application-management) qui crée un wrapper autour d’une application métier, lui permettant ainsi d’être gérée par une stratégie de protection des applications Intune.|
|Action d’affectation|Choix que vous faites quand vous [affectez une application](/intune/apps-deploy). Vous pouvez choisir de rendre l’installation de l’application obligatoire (requise), facultative (disponible), ou vous pouvez désinstaller l’application.|
|Installation disponible|Quand vous affectez une application avec cette action, elle apparaît sur le portail d’entreprise et les utilisateurs peuvent [l’installer à la demande](/intune/apps-deploy).|
|Portail Azure|La nouvelle console pour Intune [En savoir plus](/intune/what-is-intune).|

## <a name="b"></a>B

|||
|-|-|
|BYOD|[Apportez votre propre appareil (Bring Your Own Device)](/intune/device-enrollment). Les utilisateurs peuvent installer sur leur appareil l’application Portail d’entreprise Intune, puis inscrire leur appareil pour pouvoir accéder aux ressources d’entreprise comme la messagerie, les applications d’entreprise, les données d’entreprise et le support.|

## <a name="c"></a>C

|||
|-|-|
|Profil de certificat|Vous utilisez ce type de stratégie pour [sécuriser l’accès aux ressources d’entreprise](/intune/certificates-configure) avec des certificats quand vous utilisez des profils Wi-Fi, E-mail ou VPN.|
|COD|Les [appareils d’entreprise](/intune/device-enrollment) peuvent être inscrits de différentes façons, selon les besoins de l’entreprise et les types d’appareils gérés.|
|Portail d'entreprise|Application ou site web qui permet aux utilisateurs [d’accéder aux données et applications de l’entreprise](/intune/company-portal-customize).|
|Stratégie de conformité|Vérifiez que les appareils utilisés [sont conformes à certaines règles](/intune/device-compliance), comme utiliser un code confidentiel pour accéder à l’appareil et chiffrer les données qui y sont stockées.|
|Applications conformes et non conformes|Dans le cadre d’un [profil de restriction d’appareil](/intune/device-restrictions-configure), ces paramètres vous permettent de définir une liste des applications que les utilisateurs peuvent ou non exécuter. Intune vous en informe ensuite via. des rapports qu’une application non conforme a été installée ou exécutée. Pour certaines plateformes, Intune peut également bloquer l’installation d’une application non conforme.|
|Accès conditionnel|[Permet d’accéder à la messagerie d’entreprise, à Office 365 et à d’autres services](/intune/conditional-access) seulement depuis des appareils qui sont conformes à des règles que vous définissez.|
|Stratégie personnalisée|Vous [utilisez ces stratégies](/intune/custom-settings-configure) quand une stratégie de configuration générale ne contient pas un paramètre prédéfini répondant à vos besoins. Vous serez peut-être en mesure d’utiliser une stratégie personnalisée pour créer un paramètre par d’autres moyens, comme Apple Configurator ou OMA-URI.|

## <a name="d"></a>D

|||
|-|-|
|Déploiement|Fait d’envoyer une application ou une stratégie à un appareil ou à un utilisateur que vous gérez. Cette action est maintenant appelée *affectation*.|
|Gestionnaire d'inscription d'appareils|Les organisations peuvent utiliser Intune pour gérer un grand nombre d'appareils mobiles avec un seul compte d’utilisateur. Le compte du [gestionnaire d’inscription d’appareils](/intune/device-enrollment-program-enroll-ios) est un compte Intune spécial qui peut inscrire jusqu’à 1 000 appareils.|
|Profils d’appareils|[Ces profils](/intune/device-profile-create) vous permettent de configurer de nombreux paramètres de sécurité, de fonctionnalités et d’accès sur les appareils que vous gérez.|

## <a name="e"></a>E

|||
|-|-|
|Profil de messagerie|Cette stratégie peut être utilisée pour configurer les [paramètres d’accès à la messagerie](/intune/email-settings-configure) sur des appareils mobiles, en minimisant la configuration que l’utilisateur final doit effectuer.|
|EMS|Microsoft Enterprise Mobility + Security (anciennement Enterprise Mobility Suite) conserve les données de votre entreprise protégées tout en permettant à vos utilisateurs d’[accéder aux applications et au contenu dont ils ont besoin](https://www.microsoft.com/cloud-platform/enterprise-mobility).|
|Utilisateur final|[Utilisateurs d’appareils comme des téléphones et des PC](/intune/end-user-educate) gérés à l’aide d’Intune.|
|Inscription|Microsoft Intune utilise l’[inscription](/intune/device-enrollment) pour intégrer des appareils dans la gestion et pour autoriser l’accès à des ressources.|

## <a name="f"></a>F

|||
|-|-|
|FastTrack|[Service Microsoft](https://technet.microsoft.com/library/mt228265.aspx) pour les utilisateurs Intune avec 150 licences dans un forfait éligible. Avec ce service, des spécialistes Microsoft travaillent avec vous pour vous rendre opérationnel avec Intune.|

## <a name="g"></a>G

|||
|-|-|
|Groupes|Les groupes vous permettent de [regrouper logiquement des utilisateurs ou des appareils](/intune/groups-get-started). Par exemple, vous pouvez créer un groupe avec tous les PC Windows. Vous pouvez ensuite affecter des applications et des profils à ces groupes.|

## <a name="h"></a>H

|||
|-|-|
|Hybride|Configuration où vous pouvez gérer des appareils inscrits avec Intune via la console System Center Configuration Manager.|

## <a name="i"></a>I

|||
|-|-|
|Portail Azure|Le portail Azure que vous utilisez pour la plupart des opérations de gestion Intune.|
|Client logiciel Intune|Autre mode de [gestion de PC Windows](/intune-classic/get-started/choose-how-to-manage-devices) pour vous aider à décider quelle méthode utiliser.|
|Éditeur de logiciel Intune|Outil que vous utilisez pour [définir les applications que vous voulez déployer et les télécharger dans votre espace de stockage cloud](/intune-classic/deploy-use/add-apps).|
|Inventaire|Utilisé pour afficher le [matériel et les logiciels installés](/intune/device-inventory) sur les appareils que vous gérez.|

## <a name="k"></a>K

|||
|-|-|
|Mode plein écran|Configuré dans le cadre d’un [profil de restriction d’appareil](/intune/device-restrictions-configure), ce mode vous permet de verrouiller des appareils. Par exemple, vous pouvez configurer un appareil destiné à la vente au détail pour y autoriser l’exécution de certaines applications.|

## <a name="m"></a>M

|||
|-|-|
|Managed Browser|[Application de navigation web](/intune/app-configuration-managed-browser)que vous pouvez affecter dans votre organisation à l’aide de Intune. Une stratégie Managed Browser configure une liste verte ou une liste rouge, qui restreint les sites web auxquels les utilisateurs de Managed Browser ont accès.|
|Autorité MDM|L’[autorité de gestion d’appareils mobiles](/intune/mdm-authority-set) définit le service de gestion habilité à gérer un ensemble d’appareils. Les options en matière d’autorité de gestion des appareils mobiles incluent Intune en version autonome et Configuration Manager avec Intune.|
|Stratégies de configuration des applications mobiles|Disponible pour les applications mobiles présentant des configurations spécifiques à leur fournisseur. Par exemple, une stratégie [iOS](/intune/app-configuration-policies-use-ios) ou [Android](/intune/app-configuration-policies-use-android) qui est utilisée pour fournir des paramètres aux applications compatibles quand celles-ci sont exécutées, comme un nom de société ou l’adresse d’un serveur.|
|Stratégie d’approvisionnement des applications mobiles|Stratégie iOS qui permet de garantir que les [profils de configuration](/intune/app-provisioning-profile-ios) pour les applications iOS que vous affectez n’expirent pas.|
|Gestion des applications mobiles|La [gestion des applications mobiles (GAM)](/intune/app-lifecycle) vous permet de publier, envoyer des notifications Push, configurer, sécuriser, surveiller et mettre à jour des applications mobiles pour vos utilisateurs.
|Gestion des appareils mobiles|La [gestion des appareils mobiles (MDM)](/intune/device-lifecycle) vous permet d’inscrire des appareils dans Intune pour approvisionner, configurer, surveiller et gérer ces appareils.



## <a name="o"></a>O

|||
|-|-|
|OMA-DM|Open Mobile Alliance Device Management. Protocole de gestion d’appareils qui est un standard de l’industrie et qui est utilisé par de nombreux fabricants de matériel pour permettre le contrôle des fonctionnalités des appareils mobiles et des PC.|
|OMA-URI|Open Mobile Alliance Uniform Resource Identifier. Ces éléments identifient les paramètres d’appareils individuels qui sont conformes à la norme OMA-DM. Ces paramètres peuvent être utilisés dans des [profils personnalisés Intune](/intune/custom-settings-configure) quand aucun paramètre prédéfini ne répond à vos besoins.|

## <a name="p"></a>P

|||
|-|-|
|Réinitialiser le code secret|Fonctionnalité Intune qui vous permet de forcer l’utilisateur final à [réinitialiser le code secret](/intune/device-passcode-reset) sur des appareils pris en charge.|

## <a name="r"></a>R

|||
|-|-|
|Verrouillage à distance|Fonctionnalité Intune qui vous permet de [verrouiller des appareils pris en charge](/intune/device-remote-lock), même si vous n’êtes pas en possession de l’appareil.|
|Installation requise|Lorsque vous affectez une application avec cette action, [aucune intervention de l’utilisateur](/intune/apps-deploy) n’est nécessaire pour terminer l’installation. Sur certaines plateformes, l’utilisateur final peut avoir à accepter l’installation).|


## <a name="s"></a>S

|||
|-|-|
|Réinitialisation sélective|Une [réinitialisation sélective](/intune/device-company-data-remove) ne supprime d’un appareil que les données d’entreprise protégées par une stratégie de protection des applications, notamment les paramètres et les profils de messagerie. La réinitialisation sélective conserve les données personnelles de l’utilisateur sur l’appareil.|
|Chargement indépendant|L’action d’installer une application métier sans y accéder à partir d’un App Store.|
|Abonnement|L’accord que vous acceptez qui vous permet d’accéder à un client Intune.|

## <a name="t"></a>T

|||
|-|-|
|TeamViewer|Une application de tiers qui fonctionne avec Intune pour fournir [des fonctionnalités d’assistance à distance](/intune/device-profile-android-teamviewer) pour un appareil Android que vous gérez avec Intune.|
|Client|Une seule instance du service Intune auquel vous pouvez accéder à l’aide d’un abonnement.|
|Conditions générales|Type de stratégie que vous affectez aux utilisateurs et qui contient des informations que les utilisateurs doivent [lire et accepter](/intune/terms-and-conditions-create) avant de pouvoir utiliser le portail d’entreprise pour s’inscrire et accéder à leur travail.|

## <a name="v"></a>V

|||
|-|-|
|Applications et livres achetés en volume|Certains App Stores vous permettent d’acheter plusieurs licences pour une application ou un livre que vous voulez utiliser dans votre entreprise. Intune vous permet de gérer des applications et livres que vous avez [achetés par le biais d’un tel programme](/intune/vpp-apps). Vous pouvez importer les informations de licence depuis n’importe quel App Store, suivre le nombre de licences utilisées et éviter d’installer plus de copies de l’application que vous n’en possédez.|
|Profil VPN|Stratégie qui affecte des [paramètres VPN](/intune/vpn-settings-configure) sur les appareils que vous gérez, qui réduit la configuration que les utilisateurs finaux doivent effectuer.|

## <a name="w"></a>W

|               |                                                                                                                                                                                                 |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Profil Wi-Fi | Stratégie qui affecte des [paramètres de réseau sans fil](/intune/wi-fi-settings-configure) sur les appareils pour permettre aux utilisateurs de se connecter à votre réseau d’entreprise sans avoir à connaître ou à configurer des paramètres. |

