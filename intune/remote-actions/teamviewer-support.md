---
title: Administrer à distance des appareils dans Microsoft Intune - Azure | Microsoft Docs
description: Afficher les rôles nécessaires pour utiliser TeamViewer, découvrir comment installer le connecteur TeamViewer et obtenir des instructions pas à pas pour administrer à distance des appareils à l’aide de Microsoft Intune dans le portail Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fede9e67e77804ca293bbe9889d5a6623e4ea90c
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781119"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>Utiliser TeamViewer pour administrer à distance des appareils Intune

Il est possible d’administrer à distance des appareils gérés par Intune à l’aide de [TeamViewer](https://www.teamviewer.com). TeamViewer est un programme tiers que vous achetez séparément. Cette rubrique vous montre comment configurer TeamViewer dans Intune et comment administrer à distance un appareil. 

## <a name="prerequisites"></a>Prérequis

- Utilisez un appareil pris en charge. Les appareils Administrateur d’appareils Android managés par Intune, Profil professionnel Android, Windows, iOS/iPadOS et macOS prennent en charge l’administration à distance. TeamViewer peut ne pas prendre en charge Windows Holographique (HoloLens), Windows Collaboration (Surface Hub) ou Windows 10 S. Pour obtenir les dernières informations sur la prise en charge, visitez [TeamViewer](https://www.teamviewer.com).

> [!NOTE]
> Les paramètres Android dédié et Complètement managé ne sont plus pris en charge.

- L’administrateur Intune dans le portail Azure doit avoir les [rôles Intune](../fundamentals/role-based-access-control.md) suivants :  

  - **Mettre à jour l’assistance à distance** : permet aux administrateurs de modifier les paramètres du connecteur TeamViewer.
  - **Demander une assistance à distance** : permet aux administrateurs de démarrer une nouvelle session d’assistance à distance pour n’importe quel utilisateur. Les utilisateurs ayant ce rôle ne sont pas limités par un rôle Intune dans une étendue. Par ailleurs, les groupes d’utilisateurs ou d’appareils affectés à un rôle Intune dans une étendue peuvent demander une assistance à distance. 

- Un compte [TeamViewer](https://www.teamviewer.com) avec les informations d’identification de connexion. Seules certaines licences TeamViewer peuvent prendre en charge l’intégration à Intune. Pour des besoins TeamViewer spécifiques, consultez [Partenaire d’intégration TeamViewer : Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/).

En utilisant TeamViewer, vous autorisez le connecteur TeamViewer pour Intune à créer des sessions TeamViewer, lire les données Active Directory et enregistrer le jeton d’accès de compte TeamViewer.

## <a name="configure-the-teamviewer-connector"></a>Configurer le connecteur TeamViewer

Pour fournir une assistance à distance sur des appareils, configurez le connecteur TeamViewer Intune à l’aide des étapes suivantes :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Administration de locataire** > **Connecteurs et jetons** > **Connecteur TeamViewer**.
3. Sélectionnez **Connexion**, puis acceptez le contrat de licence.
4. Sélectionnez **Se connecter à TeamViewer pour autoriser**.
5. Une page web s’ouvre sur le site TeamViewer. Entrez les informations d’identification de votre licence TeamViewer, puis cliquez sur **Connexion**.

## <a name="remotely-administer-a-device"></a>Administrer un appareil à distance

Après avoir configuré le connecteur, vous êtes prêt à administrer à distance un appareil. Effectuez les étapes suivantes : 

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils**, puis **Tous les appareils**.
3. Dans la liste, sélectionnez l’appareil à administrer à distance > **...**  > **Nouvelle session d’assistance à distance**.
4. Une fois Intune connecté au service TeamViewer, des informations sur l’appareil s’affichent. **Connectez-vous** pour démarrer la session à distance.

![Utiliser TeamViewer pour administrer à distance un appareil Android (exemple)](./media/teamviewer-support/android-teamviewer.png)

Quand vous démarrez une session à distance, les utilisateurs finaux voient un indicateur de notification sur l’icône de l’application Portail d’entreprise sur leur appareil. Une notification apparaît également quand l’application s’ouvre. Les utilisateurs peuvent alors accepter la demande d’assistance à distance.

> [!NOTE]
> Les appareils Windows qui sont inscrits à l’aide de méthodes « sans utilisateur », comme DEM et WCD, n’affichent pas la notification TeamViewer dans l’application Portail d’entreprise. Dans ces scénarios, il est recommandé d’utiliser le portail TeamViewer pour générer la session.

Dans TeamViewer, vous pouvez effectuer diverses actions sur l’appareil, notamment prendre son contrôle. Pour tout savoir sur ce que vous pouvez faire, consultez [l’aide de TeamViewer](https://www.teamviewer.com/support/documents/).

Une fois que vous avez terminé, fermez la fenêtre TeamViewer.
