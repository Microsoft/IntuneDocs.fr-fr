---
title: Bloquer les applications sans authentification moderne sur Intune
titleSuffix: Microsoft Intune
description: Apprenez à bloquer les applications qui n’utilisent pas l’authentification moderne (ADAL).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 354109cc4d84e34eebd5df6df86919f386e143f6
ms.sourcegitcommit: 9f99b4a7f20ab4175d6fa5735d9f4fd6a03e0d3a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40251964"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Bloquer les applications qui n’utilisent pas l’authentification moderne (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les stratégies d’accès conditionnel basé sur l’application avec protection des applications reposent sur l’utilisation, par les applications, de l’[authentification moderne](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), qui est une implémentation d’OAuth2. Les applications mobiles et de bureau Office les plus récentes utilisent l’authentification moderne ; cependant, il existe des applications tierces et des applications Office plus anciennes qui utilisent d’autres méthodes d’authentification telles que l’authentification de base et l’authentification basée sur les formulaires.

Pour bloquer l’accès à ces applications, nous vous recommandons de procéder comme suit :

* Configurez des règles de revendications AD FS pour bloquer les protocoles autres que l’authentification moderne. Des instructions détaillées sont fournies dans le scénario 3 : [bloquer tout accès à O365, à l’exception des applications basées sur un navigateur](https://technet.microsoft.com/library/dn592182.aspx).
* Pour **Exchange et SharePoint Online**, utilisez l’accès conditionnel Azure Active Directory et la cmdlet PowerShell Set-SPOTenant pour SharePoint Online. Pour des instructions détaillées, voir [Configurer SharePoint Online et Exchange Online pour l’accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>L’accès conditionnel basé sur l’application ne doit pas être utilisé avec l’authentification basée sur un certificat Azure Active Directory (Azure AD). Seule l’une ou l’autre peut être configurée à la fois.

### <a name="see-also"></a>Voir aussi
[Accès conditionnel basé sur l’application avec Intune](app-based-conditional-access-intune.md)
