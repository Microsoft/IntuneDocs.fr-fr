---
title: Intégration du contrôle d’accès réseau dans Microsoft Intune - Azure | Microsoft Docs
description: Les solutions de contrôle d’accès réseau vérifient la conformité et l’inscription des appareils auprès d’Intune. Le contrôle d’accès réseau inclut certains comportements et fonctionne avec l’accès conditionnel. Consultez les étapes d’inscription, et obtenez une liste de solutions partenaires.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bda8512bd28351c384bfe53b46db62e5a86fe9bd
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817277"
---
# <a name="network-access-control-nac-integration-with-intune"></a>Intégration du contrôle d’accès réseau avec Intune

Intune s’intègre avec les partenaires de contrôle d’accès réseau pour aider les organisations à sécuriser les données d’entreprise quand des appareils tentent d’accéder à des ressources locales.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Comment les solutions de contrôle d’accès réseau et Intune aident-ils à protéger les ressources de votre organisation ?

Les solutions de contrôle d’accès réseau vérifient l’état de conformité et d’inscription des appareils auprès d’Intune pour prendre les décisions relatives au contrôle d’accès. Si l’appareil n’est pas inscrit, ou s’il est inscrit mais qu’il ne respecte pas les stratégies de conformité des appareils Intune, il doit être redirigé vers Intune pour l’inscription ou pour une vérification de conformité.

### <a name="example"></a>Exemple

Si l’appareil est inscrit et conforme avec Intune, la solution de contrôle d’accès réseau doit autoriser l’accès aux ressources d’entreprise à l’appareil. Par exemple, l’accès peut être accordé ou refusé aux utilisateurs quand ils tentent d’accéder aux ressources d’entreprise par Wi-Fi ou VPN.

## <a name="feature-behaviors"></a>Comportements des fonctionnalités

Les appareils qui se synchronisent activement avec Intune ne peuvent pas passer de l’état **Conforme** / **Non conforme** à l’état **Non synchronisé** (ou **Inconnu**). L’état **Inconnu** est réservé aux appareils récemment inscrits, dont la conformité n’a pas encore été évaluée.

Pour les appareils dont l’accès aux ressources est bloqué, le service de blocage doit rediriger tous les utilisateurs vers le [portail de gestion](https://portal.manage.microsoft.com) pour déterminer l’origine du blocage de l’appareil.  Si les utilisateurs consultent cette page, la conformité de leurs appareils est réévaluée de façon synchrone.

## <a name="nac-and-conditional-access"></a>Contrôle d’accès réseau et accès conditionnel

Le contrôle d’accès réseau fonctionne avec l’accès conditionnel pour fournir des décisions en matière de contrôle d’accès. Pour plus d’informations, consultez [Utilisations courantes de l’accès conditionnel avec Intune](conditional-access-intune-common-ways-use.md).

## <a name="how-the-nac-integration-works"></a>Fonctionnement de l’intégration du contrôle d’accès réseau

La liste suivante présente le fonctionnement du contrôle d’accès réseau quand il est intégré à Intune. Les trois premières étapes (1 à 3) expliquent le processus d’intégration. Une fois la solution de contrôle d’accès réseau intégrée à Intune, les étapes 4 à 9 décrivent l’opération en cours.

![Image conceptuelle du fonctionnement du contrôle d’accès réseau avec Intune](./media/ca-intune-common-ways-2.png)

1. Inscrivez la solution du partenaire de contrôle d’accès réseau auprès d’Azure Active Directory (AAD) et accordez des autorisations déléguées à l’API de contrôle d’accès réseau Intune.
2. Configurez la solution du partenaire de contrôle d’accès réseau avec les paramètres appropriés, notamment l’URL de découverte Intune.
3. Configurez la solution du partenaire de contrôle d’accès réseau pour l’authentification par certificat.
4. L’utilisateur se connecte au point d’accès Wi-Fi d’entreprise ou effectue une demande de connexion VPN.
5. La solution du partenaire de contrôle d’accès réseau transfère les informations de l’appareil à Intune et demande à Intune quel est l’état d’inscription et de conformité de l’appareil.
6. Si l’appareil n’est pas conforme ou pas inscrit, la solution du partenaire de contrôle d’accès réseau demande à l’utilisateur d’inscrire l’appareil ou de corriger sa conformité.
7. Le cas échéant, l’appareil essaie de revérifier ses conformité et état d’inscription.
8. Une fois l’appareil inscrit et conforme, la solution du partenaire de contrôle d’accès réseau obtient l’état auprès d’Intune.
9. La connexion est établie, ce qui permet à l’appareil d’accéder aux ressources d’entreprise.

## <a name="use-nac-for-vpn-on-your-ios-devices"></a>Utiliser le contrôle d’accès réseau pour un VPN sur vos appareils iOS  
Le contrôle d’accès réseau pour Cisco Legacy AnyConnect, F5 Access Legacy et Citrix VPN est pris en charge sans avoir à activer le contrôle d’accès réseau dans le profil VPN.

Le contrôle d’accès réseau pour Citrix SSO est également pris en charge. Pour activer le contrôle d’accès réseau pour Citrix SSO pour iOS :
- Utilisez Citrix Gateway 12.0.59 ou une version ultérieure.  
- Les utilisateurs doivent avoir Citrix SSO 1.1.6 ou version ultérieure.
- [Intégrez NetScaler avec Intune pour le contrôle d’accès réseau](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html) comme décrit dans la documentation de produit Citrix.
- Dans la configuration des paramètres VPN de base, pour **Activer le contrôle d’accès réseau (NAC)**, cochez la case **J’accepte**.

Lorsque vous utilisez Citrix SSO pour iOS, la connexion VPN est déconnectée toutes les 24 heures pour des raisons de sécurité. Le VPN peut être immédiatement reconnecté.


**Le contrôle d’accès réseau n’est pas pris en charge pour les clients VPN suivants sur iOS** :
-   Cisco AnyConnect
-   Accès F5

Nous travaillons avec nos partenaires à la publication d’une solution de contrôle d’accès réseau pour ces clients plus récents. Quand des solutions seront prêtes, nous mettrons à jour cet article avec des détails supplémentaires. 


## <a name="next-steps"></a>Étapes suivantes

- [Intégrer Cisco ISE avec Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Intégrer Citrix NetScaler avec Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Intégrer HP Aruba ClearPass à Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=31271)
- [Intégrer Squadra secRMM (security Removable Media Manager) à Intune](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)
