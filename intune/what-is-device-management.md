---
title: Gestion des appareils dans Microsoft 365
description: Microsoft 365 Entreprise inclut Microsoft Intune. Découvrez comment Intune permet de gérer les appareils mobiles et les applications mobiles de votre organisation, notamment dans les scénarios courants, et comment Intune permet de déployer Microsoft 365 dans votre environnement.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
audience: ITPro
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 83ac68e1f6efa9e5b0c1ee0e031d36989b634edd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185217"
---
# <a name="what-is-device-management"></a>Qu’est-ce que la gestion des appareils ? 

L’une des tâches clés d’un administrateur est de protéger et sécuriser les ressources et les données d’une organisation. Cette tâche correspond à la gestion des appareils. Les utilisateurs ont de nombreux appareils à partir desquels ils ouvrent et partagent des fichiers personnels, visitent des sites web et installent des applications et des jeux. Ces mêmes utilisateurs sont également des employés et des étudiants, qui souhaitent utiliser leurs appareils pour accéder à des ressources professionnelles et scolaires, par exemple des e-mails et OneNote. La *gestion des appareils* permet aux organisations de protéger et sécuriser leurs ressources et leurs données. 

À l’aide d’un fournisseur de gestion des appareils, les organisations peuvent vérifier que seuls les utilisateurs et les appareils autorisés ont accès aux informations propriétaires. De même, les utilisateurs d’appareils peuvent facilement accéder aux données professionnelles à partir de leur téléphone, car ils savent que leur appareil répond aux exigences de sécurité de leur organisation. En tant qu’organisation, vous pouvez vous poser la question suivante : **que devons-nous utiliser pour protéger nos ressources ?**

C’est là que [Microsoft Intune](https://docs.microsoft.com/intune/introduction-intune) entre en jeu. Intune offre une solution MDM (gestion des appareils mobiles) et une solution GAM (gestion des applications mobiles). Voici certaines tâches clés d’une solution MDM ou GAM :

- Prendre en charge un environnement mobile varié (gérer des appareils iOS, Android, Windows et macOS de manière sécurisée)
- Vérifier que les appareils et les applications sont conformes aux exigences de sécurité de l’organisation
- Créer des stratégies qui contribuent à protéger les données de l’organisation sur les appareils personnels et ceux de l’entreprise
- Utiliser une seule solution mobile unifiée pour appliquer ces stratégies et faciliter la gestion des appareils, des applications, des utilisateurs et des groupes

Intune est inclus dans Microsoft 365 et s’intègre avec Azure Active Directory (Azure AD). Azure AD permet de contrôler l’accès des utilisateurs et du contenu.

## <a name="hello-intune"></a>Bonjour Intune !
De nombreuses organisations, telles que Microsoft, utilisent Intune pour sécuriser les données propriétaires auxquelles les utilisateurs ont accès à partir de leurs appareils mobiles personnels et ceux de l’entreprise. Intune comprend des fonctionnalités telles que les stratégies de configuration des appareils et des applications, les stratégies de mise à jour logicielle et les états d’installation (ainsi que des graphiques, tableaux et rapports) pour vous aider à sécuriser et superviser l’accès aux données.

Il est courant pour de nombreuses personnes d’utiliser plusieurs appareils basés sur différentes plateformes. Par exemple, un employé peut utiliser Surface Pro pour son travail, et un appareil mobile Android dans sa vie personnelle. De plus, il est courant qu’une personne accède aux ressources d’une organisation, par exemple Microsoft Outlook et SharePoint, à partir de ces multiples appareils.

Avec Intune, vous pouvez gérer plusieurs appareils par personne, ainsi que les différentes plateformes qui s’exécutent sur chaque appareil, notamment iOS, macOS, Android et Windows. Intune sépare les stratégies et les paramètres d’une plateforme à l’autre. Il est donc facile de gérer et de voir les appareils d’une plateforme spécifique.

La rubrique **[Scénarios courants](https://docs.microsoft.com/intune/common-scenarios)** est une excellente ressource pour savoir comment Intune répond aux questions courantes liées à l’utilisation des appareils mobiles. Vous y trouverez des scénarios sur les sujets suivants :  
- Protection des e-mails avec Exchange sur site
- Accès à Office 365 de manière sécurisée
- Utilisation d’appareils personnels pour accéder aux ressources de l’organisation

## <a name="integration-with-secure-and-protect-services"></a>Intégration avec des services de sécurisation et de protection
L’une des tâches clés de toute solution de gestion des appareils consiste à assurer la sécurité et la protection. Intune fait un excellent travail en s’intégrant avec d’autres services pour effectuer cette tâche. Par exemple :

- **Microsoft 365** est un composant clé pour la simplification des tâches informatiques courantes. À l’aide du Centre d’administration Microsoft 365, vous pouvez créer des utilisateurs, gérer des groupes et accéder à d’autres services, par exemple Intune, Azure Active Directory, etc. Par exemple, vous pouvez créer un groupe d’appareils iOS dans Microsoft 365. Vous pouvez ensuite utiliser Intune pour envoyer (push) au groupe d’appareils iOS des stratégies qui se concentrent sur des fonctionnalités iOS, par exemple l’accès à l’App Store, l’utilisation d’AirDrop, la sauvegarde sur iCloud, l’utilisation du filtre web d’Apple, etc.

- **Windows Defender** inclut de nombreuses fonctionnalités de sécurité qui permettent de protéger les appareils Windows 10. Par exemple, en utilisant Intune conjointement avec Windows Defender, vous pouvez : 

    - Activer [Windows Defender SmartScreen](https://docs.microsoft.com/intune/endpoint-protection-windows-10) pour rechercher des activités suspectes dans les fichiers et applications des appareils mobiles 
    - Utiliser [ATP (Windows Defender - Protection avancée contre les menaces)](https://docs.microsoft.com/intune/advanced-threat-protection) pour éviter les violations de la sécurité sur les appareils mobiles, et limiter l’impact d’une violation de la sécurité en bloquant l’accès d’un utilisateur aux ressources de l’entreprise

- L’**accès conditionnel** est une fonctionnalité d’Azure Active Directory, qui s’intègre parfaitement avec Intune. À l’aide de l’[accès conditionnel](https://docs.microsoft.com/intune/conditional-access), vous pouvez vérifier que seuls les appareils conformes ont accès à l’e-mail, à SharePoint et à d’autres applications. 

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>Choisir la solution de gestion des appareils qui vous convient

Il existe deux façons d’aborder la gestion des appareils. Tout d’abord, vous pouvez gérer tous les aspects des appareils à l’aide de l’ensemble des fonctionnalités intégrées à Intune. Il s’agit de l’approche **MDM (gestion des appareils mobiles)**. Dans cette approche, les utilisateurs « inscrivent » leurs appareils et utilisent des certificats pour communiquer avec Intune. En tant qu’administrateur informatique, vous pouvez envoyer (push) des applications sur des appareils, restreindre les appareils à un système d’exploitation spécifique, bloquer des appareils personnels, etc. Si un appareil est perdu ou volé, vous pouvez également supprimer toutes les données qu’il contient. 

Dans la seconde approche, vous gérez les applications situées sur les appareils. Il s’agit de l’approche **GAM (gestion des applications mobiles)**. Dans cette approche, les utilisateurs peuvent utiliser leurs appareils personnels pour accéder aux ressources de l’organisation. À l’ouverture d’une application, par exemple une application d’e-mail ou SharePoint, les utilisateurs sont invités à fournir une authentification supplémentaire. Si un appareil est perdu ou volé, vous pouvez supprimer toutes les données de l’organisation qu’il contient. 

Vous pouvez également utiliser conjointement les approches [MDM et GAM](https://docs.microsoft.com/intune/byod-technology-decisions).

Quand vous configurez Intune, vous choisissez également d’utiliser uniquement le Portail Azure pour gérer les appareils, ou d’utiliser simultanément Intune et Microsoft 365 pour gérer les appareils. Découvrez comment Microsoft IT a choisi une approche de gestion des appareils moderne, basée sur les enseignements tirés de l’étude de cas décrivant la [migration de la gestion des appareils mobiles vers Intune dans le Portail Azure](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal). 

## <a name="simplify-it-tasks-using-the-device-management-dashboard"></a>Simplifier les tâches informatiques à l’aide du tableau de bord de gestion des appareils

Le [tableau de bord de gestion des appareils](https://devicemanagement.portal.azure.com/) est l’emplacement qui permet de gérer et d’exécuter les tâches relatives à vos appareils mobiles. Ce tableau de bord inclut les services utilisés pour la gestion des appareils, notamment Intune et Azure Active Directory, ainsi que pour la gestion des applications clientes. 

Dans le tableau de bord de gestion des appareils, vous pouvez :

- [Inscrire des appareils](https://docs.microsoft.com/intune/device-enrollment)
- [Définir la conformité des appareils](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Gérer les appareils](https://docs.microsoft.com/intune/device-management)
- [Gérer les applications](https://docs.microsoft.com/intune/app-management)  
- [Livres électroniques iOS](https://docs.microsoft.com/intune/vpp-ebooks-ios)  
- [Installer le connecteur Exchange sur site](https://docs.microsoft.com/intune/exchange-connector-install)  
- [Gérer les rôles](https://docs.microsoft.com/intune/role-based-access-control)  
- Gérer les mises à jour logicielles
  - [Gérer les mises à jour Windows 10](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
  - [Gérer les mises à jour iOS](https://docs.microsoft.com/intune/software-updates-ios)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [Gérer les utilisateurs](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [Gérer les groupes et les membres](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [Dépannage](https://docs.microsoft.com/intune/help-desk-operators)

## <a name="next-step"></a>Étape suivante
Une fois que vous êtes prêt à utiliser une solution MDM ou GAM, à suivre les différentes étapes de configuration d’Intune, à inscrire des appareils et à créer des stratégies, consultez [Gestion des appareils mobiles pour Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure). 
