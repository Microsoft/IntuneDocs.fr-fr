---
title: Bloquer les applications sans authentification moderne sur Intune
titleSuffix: Microsoft Intune
description: Apprenez-en plus sur les applications et l’authentification moderne (ADAL) à l’aide de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ca96f36f8813d80c7ebb07bfb3bd65f8aa0b392
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569101"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Bloquer les applications qui n’utilisent pas l’authentification moderne (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les stratégies d’accès conditionnel basé sur l’application avec protection des applications reposent sur l’utilisation, par les applications, de [l’authentification moderne](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), qui est une implémentation d’OAuth2. Les applications mobiles et de bureau Office les plus récentes utilisent l’authentification moderne. Cependant, il existe des applications tierces et des applications Office plus anciennes qui utilisent d’autres méthodes d’authentification telles que l’authentification de base et l’authentification basée sur les formulaires.

## <a name="block-access-to-apps"></a>Bloquer l’accès aux applications

Pour bloquer l’accès aux applications qui n’utilisent pas l’authentification moderne, utilisez des stratégies de protection des applications Intune pour implémenter un accès conditionnel. Pour plus d’informations, consultez [Accès conditionnel basé sur l’application avec Intune](app-based-conditional-access-intune.md).

## <a name="additional-information"></a>Informations supplémentaires

Pour plus d’informations sur l’accès conditionnel Azure AD, consultez les rubriques suivantes :
- [Qu’est-ce que l’accès conditionnel dans Azure Active Directory ?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Fonctionnement de l’accès conditionnel basé sur l’application](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [Configurer SharePoint Online et Exchange Online pour l’accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo)

## <a name="next-steps"></a>Étapes suivantes

- [Accès conditionnel basé sur l’application avec Intune](app-based-conditional-access-intune.md)
