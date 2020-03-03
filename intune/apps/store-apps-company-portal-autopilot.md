---
title: Ajouter et affecter l’application Portail d’entreprise Windows 10 pour les appareils provisionnés pour AutoPilot
titleSuffix: Microsoft Intune
description: Ajouter et affecter l’application Portail d’entreprise Windows 10 à Intune pour les appareils provisionnés pour AutoPilot
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77577283"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>Ajouter et affecter l’application Portail d’entreprise Windows 10 pour les appareils provisionnés pour AutoPilot

Pour gérer des appareils et installer des applications, vos utilisateurs peuvent utiliser l’application Portail d’entreprise. Vous pouvez affecter l’application Portail d’entreprise Windows 10 directement à partir d’Intune. 

## <a name="prerequisites"></a>Prérequis

Pour les appareils provisionnées pour Windows 10 AutoPilot, il est recommandé d’associer votre compte Microsoft Store pour Entreprises à Intune. Pour plus d’informations, consultez [Guide pratique pour gérer les applications achetées en volume dans le Microsoft Store pour Entreprises avec Microsoft Intune](~/apps/windows-store-for-business.md).

Portail d’entreprise (hors connexion) est choisi pour être installé à l’aide des étapes ci-dessous. L’application Portail d’entreprise est installée dans le contexte d’appareil quand elle est affectée au groupe AutoPilot ; elle est installée sur l’appareil avant que l’utilisateur se connecte. 

## <a name="configure-settings-to-show-offline-apps"></a>Configurer les paramètres permettant d’afficher les applications hors connexion
1. Connectez-vous au [Microsoft Store pour Entreprises](https://www.microsoft.com/business-store) avec votre compte d’administrateur.
2. Sélectionnez l’onglet **Gérer** en haut de la fenêtre.
3. Dans le volet gauche, sélectionnez **Paramètres**.
4. Sous **Expérience d’achat**, définissez **Afficher les applications hors connexion** avec la valeur **Activé**.  
    Les applications sous licence hors connexion sont affichées.

## <a name="get-the-offline-company-portal-app"></a>Obtenir l’application Portail d’entreprise hors connexion
1. Recherchez l’application **Portail d’entreprise** et sélectionnez-la.
2. Définissez le **Type de licence** sur **Hors connexion**.
3. Sélectionnez **Obtenir l’application** pour acquérir l’application Portail d’entreprise hors connexion et l’ajouter à votre inventaire.

## <a name="assign-the-company-portal-app"></a>Affecter l’application Portail d’entreprise
1. Connectez-vous au  [centre d’administration du gestionnaire de points de terminaison](https://go.microsoft.com/fwlink/?linkid=2109431)  avec votre compte d’administrateur. 
2. Sélectionnez l’onglet  **Applications** dans le volet droit. 
3. Sous  **Par plateforme**, sélectionnez **Windows**. 
4. Sélectionnez  **Portail d’entreprise (hors connexion)**.   
5. Vous devez attendre que la planification de la synchronisation soit terminée ou effectuer une synchronisation manuelle à partir du centre d’administration du gestionnaire de points de terminaison.
6. Affectez l’application Portail d’entreprise comme application obligatoire à vos groupes d’appareils AutoPilot sélectionnés.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur l’affectation d’applications à des groupes, consultez [Affecter des applications à des groupes](apps-deploy.md).

