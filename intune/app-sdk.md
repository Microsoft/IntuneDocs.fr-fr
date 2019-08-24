---
title: Avantages du SDK d’application Intune
titleSuffix: Microsoft Intune
description: Le Kit SDK d’application Intune est disponible pour les plateformes iOS et Android. Il permet d’utiliser les fonctionnalités de gestion des applications mobiles avec Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a8722f5cef29dfec8b0d3eabcc6eeac0a188456
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69582873"
---
# <a name="microsoft-intune-app-sdk-overview"></a>Présentation du Kit SDK d’application Microsoft Intune
Le Kit de développement logiciel (SDK) d’application Intune, disponible pour iOS et Android, permet à votre application de prendre en charge des [stratégies de protection d’applications](app-protection-policy.md) Intune. Quand des stratégies de protection sont appliquées à votre application, elle peut être gérée par Intune et est reconnue par Intune comme application gérée. Le Kit de développement logiciel (SDK) s’efforce de minimiser la quantité de modifications du code pour les développeurs d’applications. Vous pouvez constater qu’il est possible d’activer la plupart des fonctionnalités du SDK sans changer le comportement de votre application. Pour une meilleure expérience de l’utilisateur final et de l’administrateur informatique, vous pouvez utiliser les API du Kit de développement logiciel (SDK) pour personnaliser le comportement de votre application et permettre la prise en charge des fonctionnalités nécessitant sa participation.

Une fois que vous avez configuré votre application pour qu’elle puisse prendre en charge les stratégies de protection d’applications Intune, les administrateurs informatiques peuvent déployer ces stratégies afin de protéger leurs données d’entreprise au sein de l’application.

## <a name="app-protection-features"></a>Fonctionnalités de protection des applications

Voici quelques exemples de fonctionnalités de protection des applications Intune qui peuvent être activées avec le Kit de développement logiciel (SDK).

### <a name="control-users-ability-to-move-corporate-files"></a>Contrôler la capacité des utilisateurs à déplacer des fichiers d’entreprise
Les administrateurs informatiques peuvent contrôler les dossiers vers lesquels les données professionnelles ou scolaires de l’application peuvent être déplacées. Par exemple, ils peuvent déployer une stratégie qui empêche l'application de sauvegarder les données d’entreprise dans le cloud.

### <a name="configure-clipboard-restrictions"></a>Configurer des restrictions de Presse-papiers
Les administrateurs informatiques peuvent configurer le comportement du Presse-papiers dans les applications gérées par Intune. Par exemple, ils peuvent déployer une stratégie qui empêche les utilisateurs finaux de couper ou de copier les données depuis l’application puis de les coller dans une application personnelle non managée.

### <a name="enforce-encryption-on-saved-data"></a>Appliquer un chiffrement aux données enregistrées
Les administrateurs informatiques peuvent appliquer une stratégie garantissant le chiffrement des données enregistrées sur l’appareil par l’application.

### <a name="remotely-wipe-corporate-data"></a>Réinitialiser à distance les données d’entreprise
Les administrateurs informatiques peuvent réinitialiser à distance des données d’entreprise dans une application gérée par Intune. Cette fonctionnalité est basée sur l’identité et supprime seulement les fichiers associés à l’identité d’entreprise de l’utilisateur final. Pour cela, la fonctionnalité nécessite la participation de l’application. L’application peut spécifier l’identité pour laquelle la réinitialisation doit se produire en fonction des paramètres utilisateur. Si ces paramètres utilisateur ne sont pas spécifiés dans l’application, le comportement par défaut est de réinitialiser le répertoire de l’application et d’avertir l’utilisateur final que l’accès a été supprimé.

### <a name="enforce-the-use-of-a-managed-browser"></a>Imposer l’utilisation de Managed Browser
Les administrateurs informatiques peuvent forcer l'ouverture des liens web dans l’application avec l'[application Intune Managed Browser](app-configuration-managed-browser.md). Cette fonctionnalité garantit que les liens qui apparaissent dans un environnement d’entreprise sont conservés dans le domaine des applications gérées par Intune.

### <a name="enforce-a-pin-policy"></a>Appliquer une stratégie de code confidentiel
Les administrateurs informatiques peuvent obliger l’utilisateur final à entrer un code confidentiel pour accéder aux données d’entreprise dans l’application. Ceci garantit que la personne qui utilise l’application est celle qui s’est initialement connectée avec un compte professionnel ou scolaire. Quand un utilisateur final configure son code confidentiel, le SDK d’application Intune utilise Azure Active Directory pour comparer les informations d’identification de l’utilisateur final à celles du compte Intune inscrit.

### <a name="require-users-to-sign-in-with-a-work-or-school-account-for-app-access"></a>Obliger les utilisateurs à se connecter avec un compte professionnel ou scolaire pour accéder à l’application
Les administrateurs informatiques peuvent obliger les utilisateurs à se connecter avec leur compte professionnel ou scolaire pour accéder à l’application. Le SDK d’application Intune utilise Azure Active Directory pour fournir une expérience d’authentification unique, dans laquelle les informations d’identification, une fois entrées, sont réutilisées pour les connexions suivantes. Nous prenons également en charge l’authentification des solutions de gestion d’identité fédérées à l’aide d’Azure Active Directory.

### <a name="check-device-health-and-compliance"></a>Vérifier l’intégrité et la conformité des appareils
Les administrateurs informatiques peuvent vérifier l’intégrité de l’appareil et sa conformité aux stratégies Intune avant que les utilisateurs finaux accèdent à l'application. Sur iOS, cette stratégie vérifie si l’appareil est jailbreakée. Sur Android, cette stratégie vérifie si l’appareil est rooté.

### <a name="support-multi-identity"></a>Prendre en charge plusieurs identités
La prise en charge de plusieurs identités est une fonctionnalité du Kit de développement logiciel (SDK) qui permet la coexistence de comptes gérés par stratégie (d’entreprise) et non gérés (personnels) dans une même application.

Par exemple, beaucoup d’utilisateurs configurent à la fois des comptes de messagerie d’entreprise et personnels dans les applications mobiles Office pour iOS et Android. Quand un utilisateur accède aux données avec son compte d’entreprise, l’administrateur informatique doit être certain que la stratégie de protection des applications sera appliquée. Toutefois, quand un utilisateur accède à un compte de messagerie personnel, ces données doivent être hors du contrôle de l’administrateur. Le Kit de développement logiciel (SDK) de l’application Intune réalise cette opération en ciblant la stratégie de protection des applications **uniquement** pour l’identité de l’entreprise dans l’application.

Cette fonctionnalité multi-identité permet de résoudre le problème de protection des données auquel les organisations sont confrontées avec des applications prenant en charge à la fois des comptes personnels et professionnels.
 
### <a name="app-protection-without-device-enrollment"></a>Protection des applications sans inscription de l’appareil

>[!IMPORTANT]
>La protection d’applications Intune sans inscription d’appareil est disponible avec les outils de wrapping d’applications Intune, le SDK d’application Intune pour Android, le SDK d’application Intune pour iOS et les liaisons Xamarin du SDK d’application Intune.

De nombreux utilisateurs dotés d’appareils personnels souhaitent accéder aux données d’entreprise sans inscrire leur appareil personnel auprès d'un fournisseur de gestion des appareils mobiles (MDM). Étant donné que l’inscription MDM nécessite un contrôle global de l’appareil, les utilisateurs hésitent souvent à donner ce contrôle de leur appareil personnel à leur entreprise.

La protection d'applications sans inscription d’appareil permet au service Microsoft Intune de déployer une stratégie de protection des applications directement sur une application, sans s’appuyer sur un canal de gestion des appareils pour déployer la stratégie.

### <a name="on-demand-application-vpn-connections-with-citrix-mvpn"></a>Connexions VPN d’application à la demande avec Citrix mVPN 
Vous pouvez gérer des appareils et des applications en combinant Citrix XenMobile MDX avec Microsoft Intune. Cette combinaison signifie que vous pouvez gérer des applications à l’aide d’une stratégie de protection des applications Intune tout en utilisant la technologie mVPN de Citrix. L’intégration avec Citrix est disponible pour le SDK d’application Intune pour iOS et Android, et avec Intune App Wrapping Tool pour iOS et Android (avec l’indicateur -citrix).
 
Pour en savoir plus sur Citrix MDX, consultez [À propos du MDX Toolkit](https://docs.citrix.com/en-us/mdx-toolkit/10/about-mdx-toolkit.html), [Encapsulation des applications mobiles iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) et [Encapsulation d’applications mobiles Android](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-android.html).

## <a name="next-steps"></a>Étapes suivantes

- [Prise en main du Kit de développement logiciel (SDK) d’applications Microsoft Intune](app-sdk-get-started.md).
