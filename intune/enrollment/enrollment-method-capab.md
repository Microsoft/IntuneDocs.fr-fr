---
title: Fonctionnalités des méthodes d’inscription dans Intune pour les appareils Windows
titleSuffix: Microsoft Intune
description: Découvrez les fonctionnalités de chaque méthode d’inscription disponible pour les appareils Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11b93d41ac09f637d6c75a3f2f4b7f4213cecec7
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74819762"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Fonctionnalités des méthodes d’inscription dans Intune pour les appareils Windows
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Plusieurs méthodes permettent d’inscrire les appareils de votre personnel dans Intune. Chaque méthode a ses bonnes pratiques et fonctionnalités, comme indiqué dans les tableaux ci-dessous.

## <a name="best-practices-by-enrollment-method"></a>Bonnes pratiques par méthode d’inscription
| **Bonnes pratiques** | **[Joint à Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Joint à Azure AD avec Autopilot (mode Géré par l’utilisateur)](enrollment-autopilot.md)** |**[Joint à Azure AD avec Autopilot (mode Auto-déploiement)](enrollment-autopilot.md)** |**[En bloc](windows-bulk-enroll.md)**|**[GESTIONNAIRE D’INSCRIPTION D’APPAREIL](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[ Cogestion](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Couramment utilisé dans EDU|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Les appareils peuvent être utilisés en tant qu’appareils partagés|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Les appareils personnels doivent accéder aux ressources de l’entreprise|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Utilisation libre-service des applications|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Fonctionnalités par méthode d’inscription

| **Fonctionnalités** | **[Joint à Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Joint à Azure AD avec Autopilot (mode Géré par l’utilisateur)](enrollment-autopilot.md)** |**[Joint à Azure AD avec Autopilot (mode Auto-déploiement)](enrollment-autopilot.md)** |**[En bloc](windows-bulk-enroll.md)**|**[GESTIONNAIRE D’INSCRIPTION D’APPAREIL](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[ Cogestion](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Accès conditionnel                                      |![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)\*\*|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|
|L’utilisateur est associé à l’appareil                    |![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|
|Nécessite Azure AD Premium                               |![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|
|L’appareil peut accéder à des ressources protégées par une autorité de certification             |![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|
|Les utilisateurs ne doivent pas être administrateurs sur leurs appareils               |![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Possibilité de configurer l’expérience utilisateur d’installation de l’appareil        |![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Possibilité d’inscrire les appareils sans interaction de l’utilisateur      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|
|Possibilité d’exécuter des scripts PowerShell                       |![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/checkmark.png)\*| 
|Prend en charge l’inscription automatique après une jonction de domaine AD      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|
|Prend en charge l’inscription automatique après une jonction Azure AD Hybride|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|
|Prend en charge l’inscription automatique après une jonction Azure AD       |![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![Coche](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|

\* Les charges de travail des applications clientes dans Configuration Manager doivent être déplacées vers Intune Pilot ou Intune.

\** [Les appareils sont bloqués pour l’accès conditionnel à l’exception de Windows 10 1803+.](device-enrollment-manager-enroll.md)

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’inscription pour Windows](windows-enroll.md)

