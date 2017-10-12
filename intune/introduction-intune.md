---
title: Qu'est-ce que Microsoft Intune
description: "Découvrez comment Intune constitue le composant de gestion des appareils mobiles et de gestion des applications mobiles de la solution Enterprise Mobility + Security, et comment il permet de protéger les données d’entreprise."
keywords: "définition d’Intune"
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 07/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 527a2a1578fcf9ef8e8f80c68091e582f8f2ebd2
ms.sourcegitcommit: 6fae2dfb3a5c8f2e5ccfd120fd15656b26e5d302
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2017
---
# <a name="what-is-intune"></a>Qu’est-ce qu’Intune ?

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Intune est un service cloud dans l’espace de gestion de la mobilité en entreprise qui permet à votre force de travail de rester productive tout en protégeant vos données d’entreprise. Avec Intune, vous pouvez :
* gérer les appareils mobiles que votre personnel utilise pour accéder aux données d’entreprise ;
* gérer les applications mobiles que votre personnel utilise ;
* protéger vos informations d’entreprise en contrôlant la façon dont votre personnel y accède et les partage ;
* vérifier que les appareils et les applications sont conformes aux exigences de sécurité de l’entreprise.

## <a name="common-business-problems-that-intune-helps-solve"></a>Problématiques courantes auxquelles Intune permet de répondre

* [Protéger votre messagerie et vos données locales pour qu’elles soient accessibles par les appareils mobiles](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Protéger votre messagerie et vos données Office 365 pour qu’elles soient accessibles en toute sécurité par les appareils mobiles](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Fournir des téléphones d’entreprise à votre personnel](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Offrir un programme BYOD (Apportez votre propre appareil) à tous les employés](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Permettre à vos employés d’accéder en toute sécurité à Office 365 à partir d’une borne publique non gérée](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Fournir des tablettes partagées à utilisation limitée à vos employés](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)


## <a name="how-does-intune-work"></a>Comment fonctionne Intune ?
Intune est le composant de la solution Enterprise Mobility + Security (EMS) qui gère les applications et les appareils mobiles. Intune s’intègre étroitement à d’autres composants EMS comme Azure Active Directory (Azure AD) pour le contrôle d’identité et d’accès, et Azure Information Protection pour la protection des données. Quand vous l’utilisez avec Office 365, vous pouvez permettre à votre force de travail d’être productive sur tous les appareils, tout en assurant la protection des informations de votre organisation.

![Image de l'architecture Intune](./media/intunearch_sm.png)

Affichez une [version agrandie](./media/intunearchitecture.svg) du diagramme d’architecture Intune.

La façon d’utiliser les fonctionnalités d’Intune de gestion des appareils et des applications mobiles et la protection des données EMS dépend du [besoin auquel vous essayez de répondre](#common-business-problems-that-intune-helps-solve). Exemple :
* Vous allez très souvent recourir à la gestion des appareils si vous créez un pool d’appareils à usage unique à partager entre les employés d’un magasin de vente au détail.
* Si vous autorisez votre personnel à utiliser ses appareils personnels pour accéder aux données d’entreprise (BYOD), vous allez vous appuyer sur la gestion des applications et la protection des données.  
* Si vous fournissez des téléphones aux employés, vous allez faire appel à toutes ces technologies.

## <a name="intune-device-management-explained"></a>Fonctionnement de la gestion des appareils Intune
La gestion des appareils Intune fonctionne en utilisant les protocoles ou les API disponibles dans les systèmes d’exploitation mobiles. Elle inclut des tâches comme les suivantes :
* Inscription d’appareils à des fins de gestion pour permettre au service informatique de disposer d’un inventaire des appareils qui accèdent aux services de l’entreprise
* Configuration des appareils pour vérifier qu’ils respectent les normes de contrôle d’intégrité et de sécurité de l’entreprise
* Fourniture de certificats et de profils Wi-Fi/VPN pour accéder aux services de l’entreprise
* Création de rapports et mesure de la conformité aux normes de l’entreprise
* Suppression des données d’entreprise des appareils gérés  

Certains pensent parfois que le **contrôle d’accès aux données d’entreprise** est une fonctionnalité de gestion des appareils. Or, ce n’est pas le cas, car ce contrôle d’accès n’est pas fourni par le système d’exploitation mobile. C’est plutôt le fournisseur d’identité qui le propose. Dans notre cas, le fournisseur d’identité est Azure Active Directory (Azure AD), système de gestion des identités et des accès de Microsoft.  

Intune s’intègre à Azure AD pour gérer un large éventail de scénarios de contrôle d’accès. Par exemple, vous pouvez exiger qu’un appareil mobile soit conforme aux normes de l’entreprise que vous définissez dans Intune pour que l’appareil puisse accéder à un service d’entreprise comme Exchange. De même, vous pouvez verrouiller le service d’entreprise pour qu’il soit accessible à un ensemble spécifique d’applications mobiles. Par exemple, vous pouvez verrouiller Exchange Online pour qu’il soit uniquement accessible par Outlook ou Outlook Mobile.

## <a name="intune-app-management-explained"></a>Fonctionnement de la gestion des applications Intune
Par gestion des applications, nous entendons :
* Attribution d’applications mobiles aux employés
* Configuration d’applications avec des paramètres standard qui sont utilisés lors de l’exécution de l’application
* Contrôle de la manière dont les données d’entreprise sont utilisées et partagées dans les applications mobiles
* Suppression des données d’entreprise dans les applications mobiles   
* Mise à jour des applications
* Création de rapports sur l’inventaire des applications mobiles
* Suivi de l’utilisation des applications mobiles

Nous avons vu que l’expression « gestion des applications mobiles » sert à la fois à désigner l’une de ces tâches individuellement ou des combinaisons spécifiques. Par exemple, il est d’usage d’associer le concept de configuration des applications à celui de la sécurisation des données d’entreprise au sein des applications mobiles. Cette association vient du fait que certaines applications mobiles exposent des paramètres qui permettent de configurer leurs fonctionnalités de sécurité des données.

Quand nous parlons de configuration des applications et d’Intune, nous faisons spécifiquement référence à des technologies comme la [configuration d’applications gérées sur iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

Quand vous utilisez Intune avec les autres services dans EMS, vous pouvez accroître la sécurité des applications mobiles de votre organisation bien au-delà de celle fournie par le système d’exploitation mobile et les applications mobiles elles-mêmes par le biais de la configuration des applications. Une application gérée avec EMS a accès à un ensemble plus large de mesures de protection des applications mobiles et des données :

* [Authentification unique](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Authentification multifacteur](https://docs.microsoft.com/multi-factor-authentication/multi-factor-authentication)
* [Accès conditionnel de l’application, pour autoriser l’accès si l’application mobile contient des données d’entreprise](app-based-conditional-access-intune.md)
* [Isolement des données d’entreprise des données personnelles dans la même application](app-protection-policy.md)
* [Stratégie de protection des applications (code confidentiel, chiffrement, Enregistrer sous, Presse-papiers, etc.)](app-protection-policies.md)
* [Réinitialisation des données d’entreprise à partir d’une application mobile](apps-selective-wipe.md)
* [Prise en charge de la gestion des droits](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Image qui présente les niveaux de sécurité des données de gestion des applications](./media/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Sécurité des applications Intune
Assurer la sécurité des applications fait partie de la gestion des applications et, dans Intune, quand nous parlons de sécurité des applications mobiles, voici ce que nous voulons dire :
* Isolement des informations personnelles pour ne pas les exposer au service informatique de l’entreprise
* Limitation des actions que les utilisateurs peuvent effectuer avec les informations d’entreprise, comme copier, couper/coller, enregistrer et afficher
* Suppression des données d’entreprise dans les applications mobiles, également appelée réinitialisation sélective ou réinitialisation d’entreprise

Intune assure la sécurité des applications mobiles par le biais de sa fonctionnalité de **stratégie de protection des applications**. La stratégie de protection des applications utilise l’identité Azure AD pour isoler les données d’entreprise des données personnelles. Les données accessibles à l’aide des informations d’identification d’entreprise reçoivent des protections d’entreprise supplémentaires.

Par exemple, quand un utilisateur se connecte à son appareil avec ses informations d’identification d’entreprise, son identité d’entreprise lui donne accès à des données auxquelles son identité personnelle ne peut pas accéder. À mesure que ces données d’entreprise sont utilisées, les stratégies de protection d’application contrôlent la façon dont elles sont enregistrées et partagées. Ces mêmes protections ne sont pas appliquées aux données auxquelles l’utilisateur accède quand il se connecte à son appareil avec son identité personnelle. Ainsi, le service informatique contrôle les données d’entreprise tandis que l’utilisateur final garde le contrôle et préserve la confidentialité de ses données personnelles.

## <a name="emm-with-and-without-device-enrollment"></a>Gestion de la mobilité d’entreprise avec et sans inscription d’appareils
La plupart des solutions de gestion de la mobilité d’entreprise prennent en charge des technologies d’appareils mobiles et d’applications mobiles basiques. Celles-ci sont généralement liées à l’appareil inscrit dans la solution de gestion des appareils mobiles (MDM) de votre organisation. Intune prend en charge ces scénarios et prend également en charge de nombreux scénarios « sans inscription ».  

Les organisations se distinguent selon qu’elles adoptent ou non des scénarios « sans inscription ». Certaines organisations en font leur norme. D’autres les autorisent pour les appareils personnels comme les tablettes. D’autres encore ne les prennent pas du tout en charge. Même dans ce dernier cas, où une organisation exige que tous les appareils de son personnel soient inscrits dans MDM, des scénarios « sans inscription » sont généralement pris en charge pour les sous-traitants, les fournisseurs et d’autres appareils bénéficiant d’une exemption spécifique.

Vous pouvez même utiliser la technologie « sans inscription » d’Intune sur des appareils inscrits. Par exemple, un appareil inscrit dans MDM peut bénéficier de protections « Open In » fournies par le système d’exploitation mobile. La protection « Open In » est une fonctionnalité iOS qui vous empêche d’ouvrir un document à partir d’une application, comme Outlook, dans une autre application, comme Word, sauf si les deux applications sont gérées par le fournisseur MDM. De plus, le service informatique peut appliquer la stratégie de protection des applications aux applications mobiles gérées par EMS pour contrôler la fonctionnalité Enregistrer sous ou fournir une authentification multifacteur.

Quelle que soit la position de votre organisation vis-à-vis des appareils et applications mobiles inscrits et non inscrits, Intune, dans le cadre d’EMS, dispose d’outils qui vous permettent d’augmenter la productivité de votre personnel tout en protégeant les données de votre entreprise.



### <a name="next-steps"></a>Étapes suivantes
* En savoir plus sur certaines des [façons courantes d’utiliser Intune](common-scenarios.md).
* Se familiariser avec le produit [grâce à une période d’essai d’Intune de 30 jours](free-trial-sign-up.md).
* Explorer [les spécifications techniques et les fonctionnalités](supported-devices-browsers.md) d’Intune.
