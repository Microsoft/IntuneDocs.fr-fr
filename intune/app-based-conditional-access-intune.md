---
title: "Accès conditionnel basé sur l’application avec Intune"
description: "Comprendre les concepts du fonctionnement de l’accès conditionnel basé sur l’application avec Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0893d511c73e4154c61063d96e26937ea2825467
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2017
---
# <a name="app-based-conditional-access-with-intune"></a>Accès conditionnel basé sur l’application avec Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Les [stratégies de protection des applications Intune](app-protection-policy.md) vous aident à protéger vos données d’entreprise sur les appareils qui sont inscrits dans Intune. Vous pouvez également utiliser des stratégies de protection des applications sur les appareils détenus par l’employé qui ne sont pas inscrits pour la gestion dans Intune. Dans ce cas, même si votre entreprise ne gère pas l’appareil, vous devez toujours vous assurer que les données et ressources de votre entreprise sont protégées.

L’accès conditionnel basé sur l’application et la gestion d’applications mobiles ajoute une couche de sécurité en vous assurant que seules les applications mobiles qui prennent en charge les stratégies de protection des applications Intune peuvent accéder aux services Exchange en ligne et autres services d’Office 365.

> [!NOTE]
> Une application gérée est une application à laquelle des stratégies de protection d’application sont appliquées et pouvant être gérée par Intune.

Vous pouvez bloquer les applications de messagerie intégrées sur iOS et Android lorsque vous autorisez seulement l’application Microsoft Outlook à accéder à Exchange Online. En outre, vous pouvez bloquer les applications qui n’ont pas de stratégies de protection des applications Intune appliquées lors de l’accès à SharePoint Online.

## <a name="prerequisites"></a>Conditions préalables
Avant de créer une stratégie d’accès conditionnel basé sur l’application, vous devez avoir :

- **Un abonnement Enterprise Mobility + Security ou Azure Active Directory Premium**, et les utilisateurs doivent disposer d’une licence EMS ou Azure AD.
    - Pour plus d’informations, consultez la [page de tarification d’Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) ou la [page de tarification d’Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Applications prises en charge

- **Exchange Online** :
    - Microsoft Outlook pour Android et iOS.
<br></br>
- **SharePoint Online**
    - Microsoft Word pour iOS et Android
    - Microsoft Excel pour iOS et Android
    - Microsoft PowerPoint pour iOS et Android
    - Microsoft OneDrive Entreprise pour iOS et Android
    - Microsoft OneNote pour iOS
<br></br>
- **Microsoft Teams**

    > [!NOTE] 
    > L’accès conditionnel basé sur l’application [prend également en charge les applications métier](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication), mais ces applications doivent utiliser [l’authentification moderne Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).

## <a name="how-app-based-conditional-access-works"></a>Fonctionnement de l’accès conditionnel basé sur l’application

Dans cet exemple, l’administrateur a des stratégies de protection des applications appliquées à l’application Outlook suivies d’une règle d’accès conditionnel qui ajoute l’application Outlook à une liste approuvée d’applications qui peuvent être utilisées lors de l’accès à la messagerie de l’entreprise.

> [!NOTE] 
> La structure de l’organigramme ci-dessous peut être utilisée pour d’autres applications gérées.

![Autorité de certification basée sur l’application avec organigramme Intune](./media/ca-intune-common-ways-3.png)

1.  L’utilisateur tente de s’authentifier sur Azure AD à partir de l’application Outlook.

2.  L’utilisateur est redirigé vers l’App Store pour installer une application broker lors de sa première tentative d’authentification. L’application broker peut être Microsoft Authenticator pour iOS, ou le portail d’entreprise Microsoft pour les appareils Android.

    > [!NOTE]
    > Dans ce scénario, si des utilisateurs tentent d’utiliser une application de messagerie native, ils sont redirigés vers l’App Store pour installer l’application Outlook.

3.  L’application broker est installée sur l’appareil.

4.  L’application broker démarre le processus d’inscription d’Azure AD, qui crée un enregistrement d’appareil dans Azure AD. Cela diffère du processus d’inscription de gestion des appareils mobiles, mais cet enregistrement est nécessaire pour que les stratégies d’accès conditionnel puissent être appliquées sur l’appareil.

5.  L’application broker vérifie l’identité de l’application. Il existe une couche de sécurité pour que l’application broker puisse valider que l’application est autorisée à être utilisée par l’utilisateur.

6.  L’application broker envoie l’ID de client d’application à Azure AD dans le cadre du processus d’authentification utilisateur pour vérifier sa présence dans liste approuvée par stratégie.

7.  Azure AD permet à l’utilisateur de s’authentifier et d’utiliser l’application en fonction de la liste approuvée par stratégie. Si l’application n’est pas dans la liste approuvée par stratégie, AD Azure refuse l’accès à l’application.

8.  L’application Outlook communique avec le service cloud d’Outlook pour initialiser la communication avec Exchange Online.

9.  Le service cloud d’Outlook communique avec Azure AD pour récupérer le jeton d’accès du service Exchange Online pour l’utilisateur.

10.  L’application Outlook communique avec Exchange Online pour récupérer les e-mails professionnels de l’utilisateur.

11.  Les e-mails professionnels sont remis dans la boîte de réception de l’utilisateur.

## <a name="next-steps"></a>Étapes suivantes
[Créer une stratégie d’accès conditionnel basée sur l’application](app-based-conditional-access-intune-create.md)

[Bloquer les applications sans authentification moderne](app-modern-authentication-block.md)
