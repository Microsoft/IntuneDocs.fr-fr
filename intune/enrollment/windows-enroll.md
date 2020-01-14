---
title: Configurer l’inscription d’appareils Windows à l’aide de Microsoft Intune
titleSuffix: ''
description: Configurer l’inscription d’appareils Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: add92c038e33ba1b5873eb0e9588242f8f3d0f57
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207432"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Configurer l’inscription d’appareils Windows

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cet article aide les administrateurs informatiques à simplifier l’inscription Windows pour leurs utilisateurs. Une fois que vous avez [configuré Intune](../fundamentals/setup-steps.md), les utilisateurs inscrivent des appareils Windows en [se connectant](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) avec leur compte professionnel ou scolaire.  

En tant qu’administrateur Intune, vous pouvez simplifier l’inscription de plusieurs manières :

- [Activer l’inscription automatique](#enable-windows-10-automatic-enrollment) (Azure AD Premium est nécessaire)
- [Inscription CNAME](#simplify-windows-enrollment-without-azure-ad-premium)
- [Activer l’inscription en bloc](../windows-bulk-enroll.md) (Azure AD Premium et le Concepteur de configuration Windows sont nécessaires)

Deux facteurs déterminent la façon dont vous pouvez simplifier l’inscription des appareils Windows :

- **Utilisez-vous Azure Active Directory Premium ?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) est inclus avec Enterprise Mobility + Security et d’autres plans de licence.
- **Quelles versions des clients Windows les utilisateurs vont-ils inscrire ?** <br>Les appareils Windows 10 peuvent s’inscrire automatiquement quand vous ajoutez un compte professionnel ou scolaire. L’inscription des versions antérieures doit s’effectuer à l’aide de l’application Portail d’entreprise.

||**Azure AD Premium**|**Autre AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Inscription automatique](#enable-windows-10-automatic-enrollment) |Inscription des utilisateurs|
|**Versions précédentes de Windows**|Inscription des utilisateurs|Inscription des utilisateurs|

Les organisations qui peuvent utiliser l’inscription automatique peuvent également configurer [l’inscription en bloc des appareils](../windows-bulk-enroll.md) à l’aide de l’application Concepteur de configuration Windows.

## <a name="device-enrollment-prerequisites"></a>Prérequis pour l’inscription d’appareils

Avant qu'un administrateur puisse inscrire des appareils dans Intune pour la gestion, les licences doivent déjà avoir été attribuées au compte de l'administrateur. [En savoir plus sur l'attribution de licences pour l'inscription d’appareils](../fundamentals/licenses-assign.md)

## <a name="multi-user-support"></a>Prise en charge multiutilisateur

Intune prend en charge plusieurs utilisateurs sur les appareils qui :

- exécutent la mise à jour Windows 10 Creator
- sont joints au domaine Azure Active Directory.

Quand des utilisateurs standard se connectent avec leurs informations d’identification Azure AD, ils reçoivent les applications et stratégies affectées à leur nom d’utilisateur. Seul l'[utilisateur principal](../remote-actions/find-primary-user.md) de l’appareil peut utiliser le portail d'entreprise pour des scénarios en libre-service tels que l'installation d'applications et l'exécution d'actions sur l’appareil (Supprimer, Réinitialiser). Pour les appareils Windows 10 partagés qui n'ont pas d'utilisateur principal assigné, le portail d'entreprise peut toujours être utilisé pour installer les applications disponibles.

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Simplifier l’inscription Windows sans Azure AD Premium
Pour simplifier l’inscription, créez un alias DNS (serveur de noms de domaine), avec type d’enregistrement CNAME, qui redirige les demandes d’inscription vers les serveurs Intune. Sinon, les utilisateurs qui tentent de se connecter à Intune doivent entrer le nom du serveur Intune durant l’inscription.

**Étape 1 : Créer des enregistrements CNAME** (facultatif)<br>
Créez des enregistrements de ressources CNAME DNS pour le domaine de votre entreprise. Par exemple, si le site web de votre entreprise est contoso.com, vous devez créer un enregistrement CNAME DNS qui redirige EnterpriseEnrollment.contoso.com vers EnterpriseEnrollment-s.manage.microsoft.com.

La création d’entrées CNAME dans DNS est facultative, mais les enregistrements CNAME facilitent l’inscription pour les utilisateurs. Si aucun enregistrement CNAME d’inscription n’est trouvé, les utilisateurs sont invités à taper le nom du serveur de gestion des appareils mobiles (enrollment.manage.microsoft.com).

|Type|Nom de l'hôte|Pointe vers|TTL|
|----------|---------------|---------------|---|
|CNAME|enterpriseenrollment.domaine_entreprise.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 heure|
|CNAME|EnterpriseRegistration.domaine_entreprise.com|EnterpriseRegistration.windows.net|1 heure|

Si l’entreprise utilise plusieurs suffixes UPN, vous devez créer un enregistrement CNAME pour chaque nom de domaine et le faire pointer vers EnterpriseEnrollment-s.manage.microsoft.com. Par exemple, les utilisateurs de Contoso emploient les formats suivants pour l’e-mail/UPN :

- name@contoso.com
- name@us.contoso.com
- name@eu.contoso.com

L’administrateur DNS Contoso doit créer les enregistrements CNAME suivants :

|Type|Nom de l'hôte|Pointe vers|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 heure|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 heure|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 heure|

`EnterpriseEnrollment-s.manage.microsoft.com` : prend en charge une redirection vers le service Intune avec reconnaissance du domaine à partir du nom de domaine de l’e-mail.

La propagation des modifications DNS peut prendre jusqu’à 72 heures. Vous ne pouvez pas vérifier le changement au niveau du DNS dans Intune tant que l’enregistrement DNS ne s’est pas propagé.

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>Les points de terminaison supplémentaires sont pris en charge, mais ne sont pas recommandés
EnterpriseEnrollment-s.manage.microsoft.com est le nom de domaine complet par défaut pour l’inscription, mais il existe deux autres points de terminaison qui ont été utilisés par des clients dans le passé et qui sont pris en charge. EnterpriseEnrollment.manage.microsoft.com (sans le « -s ») et manage.microsoft.com fonctionnent tous deux comme cible pour le serveur de découverte automatique, mais l’utilisateur doit appuyer sur OK sur un message de confirmation. Si vous pointez sur EnterpriseEnrollment-s.manage.microsoft.com, l’utilisateur ne doit pas effectuer l’étape de confirmation supplémentaire : il s’agit donc de la configuration recommandée.

## <a name="alternate-methods-of-redirection-are-not-supported"></a>Les autres méthodes de redirection ne sont pas prises en charge
L’utilisation d’une méthode autre que la configuration CNAME n’est pas prise en charge. Par exemple, l’utilisation d’un serveur proxy pour rediriger enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc vers enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc ou manage.microsoft.com/EnrollmentServer/Discovery.svc n’est pas prise en charge.

**Étape 2 : Vérifier les enregistrements CNAME** (facultatif)<br>
1. Dans le [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Appareils** > **Windows** > **Inscription Windows** > **Validation CNAME**.
2. Dans la zone **Domaine**, entrez le site web de l’entreprise, puis choisissez **Tester**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Indiquer aux utilisateurs comment inscrire des appareils Windows
Informez vos utilisateurs sur la manière d’inscrire leurs appareils Windows et sur les principes de gestion des appareils.

> [!NOTE]
> Les utilisateurs finaux doivent accéder au site web du Portail d’entreprise par le biais de Microsoft Edge pour afficher les applications Windows que vous avez affectées pour des versions spécifiques de Windows. D’autres navigateurs, notamment Google Chrome, Mozilla Firefox et Internet Explorer, ne prennent pas en charge ce type de filtrage.

Pour obtenir des instructions d’inscription pour l’utilisateur final, consultez [Inscrire un appareil Windows dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Vous pouvez également diriger les utilisateurs vers la rubrique [Que voit mon administrateur informatique quand j’inscris mon appareil ?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Si vous n’avez pas activé l’inscription MDM automatique, alors que des appareils Windows 10 sont joints à Azure AD, deux enregistrements sont visibles dans la console Intune après l’inscription. Vous pouvez mettre fin à ce double affichage en vérifiant que les utilisateurs dotés d’appareils joints à Azure AD accèdent à **Comptes** > **Accès Professionnel ou Scolaire** et **Connect** en utilisant le même compte. 

Pour plus d’informations sur les tâches de l’utilisateur final, consultez [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](../fundamentals/end-user-educate.md).

## <a name="registration-and-enrollment-cnames"></a>Enregistrements CNAME d’enregistrement et d’inscription
Azure Active Directory a un CNAME (enregistrement de nom canonique) différent, utilisé pour l’enregistrement des appareils iOS, Android et Windows. L’accès conditionnel Intune nécessite l’inscription d’appareils, également appelée « rattachement à l’espace de travail ». Si vous prévoyez d’utiliser l’accès conditionnel, vous devez également configurer le CNAME EnterpriseRegistration pour chaque nom de société.

| Type | Nom de l'hôte | Pointe vers | TTL |
| --- | --- | --- | --- |
| NOM | EnterpriseRegistration. company_domain. com | EnterpriseRegistration.windows.net | 1 heure|

Pour plus d’informations sur l’inscription des appareils, consultez [Gérer les identités des appareils à l’aide du portail Azure](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal)

## <a name="windows-10-auto-enrollment-and-device-registration"></a>Inscription d’appareil et inscription automatique Windows 10

Cette section s’applique aux clients du cloud US Government.

La création d’entrées CNAME dans DNS est facultative, mais les enregistrements CNAME facilitent l’inscription pour les utilisateurs. Si aucun enregistrement CNAME d’inscription n’est trouvé, les utilisateurs sont invités à taper le nom du serveur MDM (enrollment.manage.microsoft.us).

| Type | Nom de l'hôte | Pointe vers | TTL |
| --- | --- | --- | --- |
| CNAME | enterpriseenrollment.domaine_entreprise.com | EnterpriseEnrollment-s.manage.microsoft.us | 1 heure|
|CNAME | EnterpriseRegistration.domaine_entreprise.com | EnterpriseRegistration.windows.net | 1 heure |


## <a name="next-steps"></a>Étapes suivantes

- [Considérations relatives à la gestion d’appareils Windows avec Intune dans Azure](../fundamentals/intune-legacy-pc-client.md).
