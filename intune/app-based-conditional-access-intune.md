---
title: Accès conditionnel basé sur l’application avec Intune
titleSuffix: Microsoft Intune
description: Découvrez le fonctionnement de l’accès conditionnel basé sur l’application avec Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/11/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b4c39a1d95a10c96b8f34703f99c4d8414efbbf0
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567372"
---
# <a name="app-based-conditional-access-with-intune"></a>Accès conditionnel basé sur l’application avec Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les [stratégies de protection des applications Intune](app-protection-policy.md) vous aident à protéger vos données d’entreprise sur les appareils qui sont inscrits dans Intune. Vous pouvez également utiliser des stratégies de protection des applications sur les appareils détenus par l’employé qui ne sont pas inscrits pour la gestion dans Intune. Dans ce cas, même si votre entreprise ne gère pas l’appareil, vous devez toujours vous assurer que les données et ressources de votre entreprise sont protégées.

L’accès conditionnel basé sur l’application et la gestion d’applications clientes ajoutent une couche de sécurité en vous assurant que seules les applications clientes qui prennent en charge les stratégies de protection des applications Intune peuvent accéder aux services Exchange en ligne et autres services d’Office 365.

> [!NOTE]
> Une application gérée est une application à laquelle des stratégies de protection d’application sont appliquées et pouvant être gérée par Intune.

Vous pouvez bloquer les applications de messagerie intégrées sur iOS et Android quand vous autorisez seulement l’application Microsoft Outlook à accéder à Exchange Online. En outre, vous pouvez bloquer les applications qui n’ont pas de stratégies de protection des applications Intune appliquées lors de l’accès à SharePoint Online.

## <a name="prerequisites"></a>Prérequis
Avant de créer une stratégie d’accès conditionnel basé sur l’application, vous devez avoir :

- **Enterprise Mobility + Security (EMS)** ou un **abonnement Azure Active Directory (AD) Premium**
- Les utilisateurs doivent avoir une licence pour EMS ou Azure AD

Pour plus d’informations, consultez [Tarifs d’Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou [Tarifs d’Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Applications prises en charge

Vous trouverez une liste des applications prenant en charge l’accès conditionnel basé sur l’application dans la [documentation de référence technique sur l’accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).

L’accès conditionnel basé sur l’application [prend également en charge les applications métier](app-modern-authentication-block.md), mais ces dernières doivent utiliser [l’authentification moderne Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a). 

## <a name="how-app-based-conditional-access-works"></a>Fonctionnement de l’accès conditionnel basé sur l’application

Dans cet exemple, l’administrateur a appliqué des stratégies de protection des applications à l’application Outlook suivies d’une règle d’accès conditionnel qui ajoute l’application Outlook à une liste approuvée d’applications qui peuvent être utilisées lors de l’accès aux e-mails d’entreprise.

> [!NOTE]
> La structure de l’organigramme ci-dessous peut être utilisée pour d’autres applications gérées.

![Processus d’accès conditionnel basé sur l’application illustré dans un organigramme](./media/ca-intune-common-ways-3.png)

1. L’utilisateur tente de s’authentifier sur Azure AD à partir de l’application Outlook.

2. L’utilisateur est redirigé vers l’App Store pour installer une application broker lors de sa première tentative d’authentification. L’application broker peut être Microsoft Authenticator pour iOS, ou le portail d’entreprise Microsoft pour les appareils Android.

   Si des utilisateurs tentent d’utiliser une application de messagerie native, ils sont redirigés vers l’App Store pour installer l’application Outlook.

3. L’application broker est installée sur l’appareil.

4. L’application broker démarre le processus d’inscription dans Azure AD, qui crée un enregistrement d’appareil dans Azure AD. Cela diffère du processus d’inscription pour la gestion GPM, mais cet enregistrement est nécessaire pour que les stratégies d’accès conditionnel puissent être appliquées sur l’appareil.

5. L’application broker vérifie l’identité de l’application. Il existe une couche de sécurité, afin que l’application broker puisse vérifier que l’utilisateur est autorisé à exécuter l’application.

6. L’application broker envoie l’ID de client d’application à Azure AD dans le cadre du processus d’authentification utilisateur pour vérifier sa présence dans liste approuvée par stratégie.

7. Azure AD permet à l’utilisateur de s’authentifier et d’utiliser l’application en fonction de la liste approuvée par stratégie. Si l’application n’est pas sur la liste, Microsoft Azure Active Directory refuse l’accès à l’application.

8. L’application Outlook communique avec le service cloud d’Outlook pour établir la communication avec Exchange Online.

9. Le service cloud d’Outlook communique avec Azure AD pour récupérer le jeton d’accès du service Exchange Online pour l’utilisateur.

10. L’application Outlook communique avec Exchange Online pour récupérer les e-mails professionnels de l’utilisateur.

11. Les e-mails professionnels sont remis dans la boîte de réception de l’utilisateur.

## <a name="next-steps"></a>Étapes suivantes
[Créer une stratégie d’accès conditionnel basée sur l’application](app-based-conditional-access-intune-create.md)

[Bloquer les applications sans authentification moderne](app-modern-authentication-block.md)
