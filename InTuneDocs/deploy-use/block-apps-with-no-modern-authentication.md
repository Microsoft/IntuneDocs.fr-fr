---
title: Bloquer les applications sans authentification moderne | Microsoft Intune
description: 
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5083cb49e7a98f19ff21c1972149b00aee4ec93e
ms.openlocfilehash: 8c2718da6f90f18ffbaa6a977dfca7fbc9a1bb09


---

# Bloquer les applications qui n’utilisent pas l’authentification moderne (ADAL)
Dans le cadre de l’accès conditionnel pour les applications avec des stratégies GAM (accès conditionnel pour la gestion des applications mobiles), les applications utilisent l’[authentification moderne](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a), qui est une implémentation d’OAuth2. Les applications mobiles et de bureau Office les plus récentes utilisent l’authentification moderne ; cependant, il existe des applications tierces et des applications Office plus anciennes qui utilisent d’autres méthodes d’authentification telles que l’authentification de base et l’authentification basée sur les formulaires.

Pour bloquer l’accès à ces applications, nous recommandons l’opération suivante :

* Configurez des règles de revendications AD FS pour bloquer les protocoles autres que l'authentification moderne. Des instructions détaillées sont fournies dans le scénario 3 : [bloquer tout accès à O365, à l’exception des applications basées sur un navigateur](https://technet.microsoft.com/library/dn592182.aspx).

>[!IMPORTANT]
>L’accès conditionnel pour la gestion des applications mobiles ne doit pas être utilisé avec l’authentification basée sur un certificat Azure Active Directory (Azure AD). Seule l’une ou l’autre peut être configurée à la fois.



### Voir aussi
[Autoriser uniquement les applications prises en charge par Intune à accéder aux services O365](allow-policy-managed-apps-access-to-o365.md)



<!--HONumber=Oct16_HO4-->


