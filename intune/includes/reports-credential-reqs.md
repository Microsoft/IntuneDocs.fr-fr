---
ms.openlocfilehash: 6ec8f8a613d3b0a0b17f2615de634e70fa282fd7
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68229296"
---
<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Exigences liées aux informations d’identification Azure AD et Intune

L’authentification et l’autorisation sont basées sur les informations d’identification Azure AD et le contrôle d’accès en fonction du rôle (RBAC). Par défaut, tous les administrateurs généraux et les administrateurs de service Intune de votre locataire ont accès à l’entrepôt de données. Utilisez des rôles Intune pour fournir un accès à plus d’utilisateurs en leur donnant accès à la ressource **Entrepôt de données Intune**.

Exigences liées à l’accès à l’entrepôt de données Intune (notamment l’API) :

- L’utilisateur doit appartenir à l’une des catégories suivantes :
  - Administrateur général Azure AD
  - Administrateur de service Intune
  - Utilisateur avec accès en fonction du rôle à la ressource **Entrepôt de données Intune**
  - Authentification sans utilisateur avec [authentification de l’application uniquement](../data-warehouse-app-only-auth.md) 
