---
title: Stratégies de protection d’applications pour les extensions
titleSuffix: Microsoft Intune
description: Cette rubrique décrit la stratégie de protection des applications (APP) pour les extensions.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a94f3d175fe5c036c5e90635a66467263b23122
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499117"
---
# <a name="protecting-application-extensions"></a>Protection des extensions d'applications

Cet article décrit les stratégies de protection des applications pour les extensions dans Microsoft Intune.

## <a name="add-ins-for-outlook-app"></a>Compléments d’application Outlook

Les compléments Outlook vous permettent d’intégrer des applications populaires au client de messagerie. Les compléments pour Outlook sont disponibles sur les versions web, Windows, Mac et Outlook pour Android et iOS. Le kit de développement logiciel (SDK) APP Intune et les stratégies de protection d’application Intune n’incluent pas la prise en charge de la gestion des compléments pour Outlook, mais il existe d’autres façons de limiter leur utilisation. Étant donné que les compléments sont gérés par Microsoft Exchange, vous pourrez partager des données et des messages entre Outlook et les applications complémentaires non gérées, sauf si les compléments sont désactivés pour l’utilisateur par Exchange.

Si vous décidez d’empêcher vos utilisateurs d’accéder à et d’installer des compléments Outlook (cela affecte tous les clients Outlook), assurez-vous que les modifications suivantes sont apportées aux rôles dans le centre d’administration Exchange :

- Pour empêcher les utilisateurs d’installer des compléments Office Store, retirez-leur le rôle Mon Marketplace.
- Pour empêcher les utilisateurs de charger des compléments, retirez-leur le rôle Mes applications personnalisées.
- Pour empêcher les utilisateurs d’installer l’ensemble des compléments, retirez-leur les deux rôles, Mes applications personnalisées et Mon Marketplace.

Ces instructions s’appliquent à Office 365, Exchange 2016, Exchange 2013 pour les versions web, Windows, Mac et mobiles d’Outlook.

- En savoir plus sur les [compléments pour Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Lisez-en davantage avec le [Guide pratique de spécification des administrateurs et utilisateurs pouvant installer et gérer les compléments d’application Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Connexions au compte LinkedIn pour les applications Microsoft

Les connexions au compte LinkedIn permettent aux utilisateurs de voir des informations de profil LinkedIn publiques au sein de certaines applications Microsoft. Par défaut, vos utilisateurs peuvent choisir de connecter leurs comptes LinkedIn et leurs comptes professionnels ou scolaires Microsoft pour voir des informations de profil LinkedIn supplémentaires. 

> [!NOTE]
> L’intégration de LinkedIn est actuellement indisponible pour les clients des organismes publics des États-Unis et pour les organisations avec des boîtes aux lettres Exchange Online hébergées dans les pays suivants : Australie, Canada, Chine, France, Allemagne, Inde, Corée du Sud, Royaume-Uni, Japon et Afrique du Sud.

Le SDK Intune et les stratégies de protection d’application Intune n’incluent pas la prise en charge de la gestion des connexions de compte LinkedIn, mais il existe d’autres façons de les gérer. Vous pouvez désactiver les connexions au compte LinkedIn pour toute votre organisation, ou vous pouvez les activer seulement pour des groupes d’utilisateurs sélectionnés dans votre organisation. Ces paramètres affectent les connexions à LinkedIn des applications Office 365 sur toutes les plateformes (web, mobiles et poste de travail). Vous pouvez :

- Activer ou désactiver les connexions au compte LinkedIn pour votre locataire dans le portail Azure. 
- Activer ou désactiver les connexions au compte LinkedIn pour les applications Office 2016 de votre organisation avec la stratégie de groupe.

Si l’intégration de LinkedIn est activée pour votre locataire, quand les utilisateurs de votre organisation connectent leur compte LinkedIn et leur compte professionnel ou scolaire Microsoft, ils ont deux options : 

- Ils peuvent donner l’autorisation de partager des données entre les deux comptes. Cela signifie qu’ils donnent leur autorisation pour que leur compte LinkedIn partage des données avec leur compte professionnel ou scolaire Microsoft, et pour que leur compte professionnel ou scolaire Microsoft partage des données avec leur compte LinkedIn. Les données qui sont partagées avec LinkedIn quittent les services en ligne. 
- Ils peuvent donner l’autorisation de partager des données seulement dans un sens, de leur compte LinkedIn vers leur compte professionnel ou scolaire Microsoft.

Si un utilisateur consent à partager des données entre des comptes, comme avec des compléments Office, l’intégration de LinkedIn utilise les API Microsoft Graph existantes. L’intégration de LinkedIn utilise seulement un sous-ensemble des API disponibles pour les compléments Office et prend en charge différentes exclusions.


|Autorisations Microsoft Graph  |Description  |
|---------|---------|
|Autorisations de lecture pour les [personnes](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)     |Permet à l’application de lire une liste avec scores de personnes ayant un lien avec l’utilisateur connecté. La liste peut inclure des contacts locaux, des contacts provenant des réseaux sociaux ou de l’annuaire de votre organisation, et des personnes contactées dans le cadre de communications récentes (par exemple par e-mail et via Skype).         |
|Autorisations de lecture pour des [calendriers](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)     |Permet à l’application de lire des événements dans les calendriers de l’utilisateur. Inclut les réunions dans les calendriers de l’utilisateur connecté, le moment et l’endroit où elles se déroulent, et leurs participants.         |
|Autorisations de lecture du [profil utilisateur](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)     |Permet aux utilisateurs de se connecter à l’application et permet à l’application de lire le profil des utilisateurs connectés. Elle permet également à l’application de lire des informations de base de l’entreprise pour les utilisateurs connectés.         |
|Subscriptions     |Cette étendue n’est pas disponible et n’est pas encore utilisée. Elle inclut des abonnements fournis par l’organisation de l’utilisateur pour des applications et des services Microsoft, comme Office 365.         |
|Insights     |Cette étendue n’est pas disponible et n’est pas encore utilisée. Elle inclut les intérêts associés au compte de l’utilisateur connecté, basés sur son utilisation des services Microsoft.         |

### <a name="learn-more"></a>En savoir plus

- Découvrez plus d’informations sur les [informations et fonctionnalités de LinkedIn dans vos applications Microsoft](https://go.microsoft.com/fwlink/?linkid=850740).
- Découvrez plus d’informations sur la disponibilité des connexions au compte LinkedIn sur la [page Feuille de route Office 365](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc). 
- Découvrez plus d’informations sur la [configuration des connexions au compte LinkedIn](https://docs.microsoft.com/azure/active-directory/linkedin-integration).
- Pour plus d’informations sur les données qui sont partagées entre les comptes LinkedIn et les comptes professionnels ou scolaires Microsoft des utilisateurs, consultez [Les applications et les services Microsoft en partenariat avec LinkedIn](https://www.linkedin.com/help/linkedin/answer/84077).

