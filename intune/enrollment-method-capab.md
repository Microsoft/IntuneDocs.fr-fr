---
title: Fonctionnalités des méthodes d’inscription dans Intune pour les appareils Windows
titlesuffix: Microsoft Intune
description: Découvrez les fonctionnalités de chaque méthode d’inscription disponible pour les appareils Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa71461b136243262146502adc0f7b925b345a0b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55839326"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Fonctionnalités des méthodes d’inscription dans Intune pour les appareils Windows
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Plusieurs méthodes permettent d’inscrire les appareils de votre personnel dans Intune. Chaque méthode a ses bonnes pratiques et fonctionnalités, comme indiqué dans les tableaux ci-dessous.

## <a name="best-practices-by-enrollment-method"></a>Bonnes pratiques par méthode d’inscription
| **Bonnes pratiques** | **[Joint à Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Joint à Azure AD avec Autopilot](enrollment-autopilot.md)** |**[En bloc](windows-bulk-enroll.md)**|**[GESTIONNAIRE D’INSCRIPTION D’APPAREIL](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Couramment utilisé dans EDU|![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Les appareils peuvent être utilisés en tant qu’appareils partagés|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Les appareils personnels doivent accéder aux ressources de l’entreprise|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|
|Utilisation libre-service des applications|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Fonctionnalités par méthode d’inscription

| **Fonctionnalités** | **[Joint à Azure AD](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Joint à Azure AD avec Autopilot](enrollment-autopilot.md)** |**[En bloc](windows-bulk-enroll.md)**|**[GESTIONNAIRE D’INSCRIPTION D’APPAREIL](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Accès conditionnel                                      |![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|
|L’utilisateur est associé à l’appareil                    |![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|
|Nécessite Azure AD Premium                               |![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|
|L’appareil peut accéder à des ressources protégées par une autorité de certification             |![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|
|Les utilisateurs ne doivent pas être administrateurs sur leurs appareils               |![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Possibilité de configurer l’expérience utilisateur d’installation de l’appareil        |![X](media/xmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Possibilité d’inscrire les appareils sans interaction de l’utilisateur      |![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|
|Possibilité d’exécuter des scripts PowerShell                       |![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Prend en charge l’inscription automatique après une jonction de domaine AD      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|
|Prend en charge l’inscription automatique après une jonction Azure AD Hybride|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Coche](media/checkmark.png)|
|Prend en charge l’inscription automatique après une jonction Azure AD       |![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![Coche](media/checkmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’inscription pour Windows](windows-enroll.md)

