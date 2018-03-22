<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Exigences liées aux informations d’identification Azure AD et Intune

L’authentification et l’autorisation sont basées sur les informations d’identification Azure AD et le contrôle d’accès en fonction du rôle (RBAC). Par défaut, tous les administrateurs généraux et les administrateurs de service Intune de votre locataire ont accès à l’entrepôt de données. Utilisez des rôles Intune pour fournir un accès à plus d’utilisateurs en leur donnant accès à la ressource **Entrepôt de données Intune**.

Exigences liées à l’accès à l’entrepôt de données Intune (notamment l’API) :

  -  L’utilisateur doit appartenir à l’une des catégories suivantes :
      -  Administrateur général Azure AD
      -  Administrateur de service Intune
      -  Utilisateur avec accès en fonction du rôle à la ressource **Entrepôt de données Intune**
      -  Authentification sans utilisateur avec [authentification de l’application uniquement](../data-warehouse-app-only-auth.md) 
