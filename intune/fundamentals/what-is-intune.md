---
title: Qu’est-ce que Microsoft Intune ? - Azure | Microsoft Docs
description: Découvrez comment Microsoft Intune constitue le composant de gestion des appareils mobiles (MDM) et de gestion des applications mobiles (MAM) de la solution Enterprise Mobility + Security, et comment il permet de protéger les données de l’entreprise.
keywords: définition d’Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3c03c67a99b78804c999250f8d1148a4b3d1d97
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504769"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune est un fournisseur MDM et GAM pour vos appareils

Microsoft Intune est un service cloud qui se concentre sur la gestion des appareils mobiles (MDM) et la gestion des applications mobiles (GAM). Intune est inclus dans la suite [Enterprise Mobility + Security (EMS)](https://www.microsoft.com/microsoft-365/enterprise-mobility-security) de Microsoft, et permet aux utilisateurs d’être productifs tout en protégeant les données de votre organisation. Il s’intègre à d’autres services, dont Microsoft 365 et Azure Active Directory (Azure AD) pour contrôler qui a accès à quoi, et Azure Information Protection pour la protection des données. Si vous l’utilisez avec Microsoft 365, vous offrez à vos employés la possibilité de rester productifs sur tous leurs appareils, tout en assurant la protection des informations de votre organisation.

![Image de l'architecture Intune](./media/what-is-intune/intunearch_sm.png)

Affichez une [version agrandie](./media/what-is-intune/intunearchitecture.svg) du diagramme d’architecture Intune.

Avec Intune, vous pouvez :

- Choisir une solution 100 % cloud % avec Intune, ou [cogérée](https://docs.microsoft.com/sccm/comanage/overview) avec Configuration Manager et Intune.
- Définir des règles et configurer des paramètres sur des appareils personnels et appartenant à l’organisation pour l’accès aux données et aux réseaux.
- Déployer et authentifier des applications sur des appareils locaux et mobiles.
- Protéger les informations de votre entreprise en contrôlant la façon dont les utilisateurs accèdent aux informations et les partagent.
- Vérifier que les appareils et les applications sont conformes à vos exigences de sécurité.

## <a name="manage-devices"></a>Gérer des unités

Dans Intune, vous gérez les appareils à l’aide d’une approche qui vous convient. Pour les appareils appartenant à l’organisation, vous souhaiterez peut-être disposer d’un contrôle total sur les appareils, notamment les paramètres, les fonctionnalités et la sécurité. Dans cette approche, les appareils et les utilisateurs de ces appareils « s’inscrivent » dans Intune. Une fois inscrits, ils reçoivent vos règles et paramètres par le biais de stratégies configurées dans Intune. Par exemple, vous pouvez définir des exigences de mot de passe et de code confidentiel, créer une connexion VPN, configurer la protection contre les menaces, et bien plus encore.

Pour les appareils personnels ou BYOD, les utilisateurs peuvent ne pas souhaiter que leurs administrateurs d’organisation aient un contrôle total. Dans cette approche, donnez aux utilisateurs des options. Par exemple, les utilisateurs [inscrivent](../enrollment/device-enrollment.md) leurs appareils s’ils veulent un accès total aux ressources de votre organisation. Ou, si ces utilisateurs veulent uniquement accéder à la messagerie ou à Microsoft Teams, utilisez des stratégies de protection des applications qui requièrent l’authentification multifacteur (MFA) pour utiliser ces applications.

Lorsque les appareils sont inscrits et gérés dans Intune, les administrateurs peuvent :

- Consulter les appareils inscrits et obtenir un inventaire des appareils qui accèdent aux ressources de l’organisation.
- Configurer les appareils pour qu’ils respectent vos normes de sécurité et d’intégrité. Par exemple, vous souhaitez probablement bloquer les appareils jailbroken.
- Envoyer des certificats aux appareils pour que les utilisateurs puissent accéder facilement à votre réseau Wi-Fi ou utiliser un VPN pour se connecter à votre réseau.
- Consulter les rapports sur les utilisateurs et les appareils conformes et non conformes.
- Supprimer les données de l’organisation si un appareil est perdu, volé ou n’est plus utilisé.

**Ressources en ligne** :

- [Qu’est-ce que l’inscription d’appareils ?](../enrollment/device-enrollment.md)

- [Appliquer des fonctionnalités et des paramètres sur vos appareils à l’aide des profils d’appareil](../configuration/device-profiles.md)

- [Protéger des appareils avec Microsoft Intune](../protect/device-protect.md)

## <a name="manage-apps"></a>Gérer des applications

La gestion des applications mobiles (GAM) dans Intune est conçue pour protéger les données de l’organisation au niveau de l’application, y compris les applications personnalisées et les applications du Windows Store. La gestion des applications peut être utilisée sur des appareils appartenant à l’organisation et sur des appareils personnels.

Lorsque les applications sont gérées dans Intune, les administrateurs peuvent :

- Ajouter et affecter des applications mobiles à des groupes d’utilisateurs et à des appareils, y compris des utilisateurs dans des groupes spécifiques, des appareils dans des groupes spécifiques, et plus encore.
- Configurer des applications pour qu’elles démarrent ou s’exécutent avec des paramètres spécifiques activés, et mettre à jour les applications existantes déjà présentes sur l’appareil.
- Consultez les rapports sur les applications utilisées et suivez leur utilisation.
- Effectuez une réinitialisation sélective en supprimant uniquement les données d’entreprise des applications.

Intune assure la sécurité des applications mobiles par le biais de ses **[stratégies de protection des applications](../apps/app-protection-policy.md)** . Stratégies de protection des applications :

- Utiliser l’identité Azure AD pour isoler les données d’entreprise des données personnelles. Les informations personnelles ne sont donc pas exposées au service informatique de l’organisation. Une protection de sécurité supplémentaire est accordée aux données accessibles à l’aide des informations d’identification de l’organisation.
- Sécuriser l’accès aux appareils personnels en restreignant les actions que les utilisateurs peuvent effectuer, comme le copier-coller, l’enregistrement et l’affichage.
- Vous pouvez créer et déployer cela sur les appareils qui sont inscrits dans Intune, inscrits dans un autre service MDM ou non inscrits dans un service MDM. Sur les appareils inscrits, les stratégies de protection des applications peuvent ajouter une couche de protection supplémentaire.

Par exemple, un utilisateur se connecte à un appareil avec ses informations d’identification d’organisation. Son identité d’organisation lui permet d’accéder aux données qui sont refusées à son identité personnelle. À mesure que ces données de l’organisation sont utilisées, les stratégies de protection d’application contrôlent la façon dont elles sont enregistrées et partagées. Lorsque les utilisateurs se connectent avec leur identité personnelle, ces mêmes protections ne sont pas appliquées. Ainsi, le service informatique contrôle les données de l’organisation tandis que l’utilisateur final garde le contrôle et préserve la confidentialité de ses données personnelles.

Et vous pouvez utiliser Intune avec les autres services dans EMS. Cette fonctionnalité fournit à l’application mobile de votre organisation une sécurité qui va au-delà de ce qui est inclus avec le système d’exploitation et les applications. Les applications gérées avec EMS ont accès à un ensemble plus large de fonctionnalités de protection des applications mobiles et des données.

![Image qui présente les niveaux de sécurité des données de gestion des applications](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>Conformité et accès conditionnel

Intune s’intègre à Azure AD pour gérer un large éventail de scénarios de contrôle d’accès. Par exemple, les appareils mobiles doivent être conformes aux normes de l’organisation définies dans Intune avant d’accéder aux ressources réseau, comme la messagerie ou SharePoint. De même, vous pouvez verrouiller les services afin qu’ils soient uniquement disponibles pour un ensemble spécifique d’applications mobiles. Par exemple, vous pouvez verrouiller Exchange Online pour qu’il soit uniquement accessible par Outlook ou Outlook Mobile.

**Ressources en ligne** :

- [Définir des règles sur les appareils pour autoriser l’accès aux ressources de votre organisation](../protect/device-compliance-get-started.md)

- [Utilisations courantes de l’accès conditionnel avec Intune](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>Comment obtenir Intune

Intune est disponible :

- En tant que [service Azure](https://go.microsoft.com/fwlink/?linkid=2090973) autonome
- Inclus avec [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) et [Microsoft 365 pour le gouvernement](https://www.microsoft.com/microsoft-365/government)
- En tant que [Gestion des appareils mobiles dans Office 365](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22), qui comprend certaines fonctionnalités Intune limitées

Intune est utilisé dans de nombreux secteurs, notamment [le gouvernement](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description), [l’éducation](https://www.microsoft.com/en-us/education/intune) et [les kiosques ou appareils dédiés](../configuration/kiosk-settings.md) pour la fabrication et la vente au détail, et bien plus encore.

## <a name="next-steps"></a>Étapes suivantes

- Découvrez certains [problèmes courants en entreprise qu’Intune vous aide à résoudre](https://docs.microsoft.com/intune/common-scenarios).
- Commencez avec une [version d’évaluation de 30 jours d’Intune](free-trial-sign-up.md).
- Planifiez votre [migration sur Intune](migration-guide.md).
- À l’aide de votre abonnement ou de votre version d’évaluation gratuite, effectuez le [Démarrage rapide : créer un profil d’appareil de messagerie pour iOS](../configuration/quickstart-email-profile.md).
