---
title: S’inscrire ou se connecter à Microsoft Intune
description: Guide pratique pour souscrire un abonnement Microsoft Intune ou vous connecter et démarrer votre abonnement.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22e5c38be9dc5a8a09888651e471f64bf6739c72
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71238909"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>S’inscrire ou se connecter à Microsoft Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Cette rubrique explique aux administrateurs système comment ouvrir un compte Intune.

Avant de vous inscrire à Intune, déterminez si vous disposez déjà d’un compte Microsoft Online Services, d’un contrat Entreprise ou d’un contrat de licence en volume équivalent. Un contrat de licence en volume Microsoft ou un abonnement à d’autres services cloud Microsoft comme Office 365 s’accompagne généralement d’un compte professionnel ou scolaire.

Si vous disposez déjà d’un compte professionnel ou scolaire, **connectez-vous** avec ce compte et ajoutez Intune à votre abonnement. Sinon, vous pouvez **ouvrir** un nouveau compte pour utiliser Intune pour votre organisation.

>[!WARNING]
>Vous ne pouvez pas combiner un compte professionnel ou scolaire existant après avoir ouvert un nouveau compte.

## <a name="how-to-sign-up-for-intune"></a>Guide pratique pour s’inscrire à Intune

1. Visitez la [page d’inscription Intune](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20).

   ![Capture d’écran de la page web d’ouverture d’un compte d’évaluation Microsoft Intune](./media/account-sign-up-site.png)

2. Dans la page d’inscription, connectez-vous ou inscrivez-vous pour gérer un nouvel abonnement Intune.

## <a name="post-sign-up-considerations"></a>Éléments à prendre en considération après l’inscription
Après vous être inscrit pour obtenir un nouvel abonnement, vous recevez un message électronique contenant les informations de votre compte à l’adresse e-mail que vous avez fournie pendant l’inscription. Ce message confirme que votre abonnement est actif.

À la fin du processus d’inscription, vous êtes dirigé vers le centre d’administration Microsoft 365, qui permet d’ajouter des utilisateurs et de leur attribuer des licences. Si vous disposez uniquement de comptes cloud et qu’ils utilisent votre nom de domaine onmicrosoft.com par défaut, vous pouvez continuer et ajouter des utilisateurs et leur attribuer des licences à ce stade. Toutefois, si vous envisagez d’utiliser le [nom de domaine personnalisé](custom-domain-name-configure.md) de votre organisation ou de [synchroniser les informations du compte utilisateur](users-add.md#sync-active-directory-and-add-users-to-intune) à partir d’une instance Active Directory locale, vous pouvez fermer cette fenêtre de navigateur.

## <a name="sign-in-to-microsoft-intune"></a>Se connecter à Microsoft Intune
Une fois que vous êtes inscrit à Intune, vous pouvez utiliser n’importe quel appareil avec un [navigateur pris en charge](supported-devices-browsers.md#intune-supported-web-browsers) pour vous connecter à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) afin d’administrer le service.

Par défaut, votre compte doit posséder l'une des autorisations suivantes dans Azure AD :
- Administrateur général
- Administrateur du service Intune (également appelé Administrateur Intune)

Pour accorder l’accès aux utilisateurs disposant d’autres autorisations afin d’administrer le service, consultez [Contrôle d'accès basé sur un rôle](role-based-access-control.md)

### <a name="intune-admin-portal-url"></a>URL du portail d’administration Intune

Centre d’administration Microsoft 365 : https://devicemanagement.microsoft.com

Portail Azure Intune : https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune pour l’Éducation : https://intuneeducation.portal.azure.com

Portail classique Intune https://manage.microsoft.com Le portail classique Intune est utilisé uniquement pour gérer les appareils inscrits auprès du client logiciel Intune PC.

### <a name="urls-for-intune-services-provided-by-office-365"></a>URL pour les services Intune fournis par Office 365

Microsoft 365 Business : https://portal.microsoft.com/adminportal

Gestion des appareils mobiles Office 365 : https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>Voir aussi
[Vous ne pouvez pas vous connecter à Office 365, à Azure ou à Intune](https://support.microsoft.com/help/2412085)
