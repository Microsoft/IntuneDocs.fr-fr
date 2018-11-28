---
title: Ajouter des scripts PowerShell dans Microsoft Intune sur des appareils Windows 10 - Azure | Microsoft Docs
description: Ajouter des scripts PowerShell, attribuer la stratégie de script à des groupes Azure Active Directory, utiliser des rapports pour surveiller les scripts, et consulter les étapes permettant de supprimer les scripts que vous ajoutez sur des appareils Windows 10 dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 29a3f6c6e320f970ef7b2b086b8d25ab82453199
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179403"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Gérer des scripts PowerShell dans Intune pour des appareils Windows 10
L’extension de gestion Intune vous permet de charger des scripts PowerShell dans Intune pour les exécuter sur des appareils Windows 10. L’extension de gestion vient en complément des fonctionnalités de gestion des appareils mobiles (MDM) Windows 10 et facilite l’adoption d’une gestion moderne.

## <a name="moving-to-modern-management"></a>Vers une gestion moderne
Actuellement, l’informatique de l’utilisateur final connaît une transformation numérique. L’informatique classique et traditionnelle se caractérise par une plateforme d’appareils unique, des appareils d’entreprise, des utilisateurs travaillant depuis leur bureau et de nombreux processus informatiques manuels et réactifs. En revanche, un lieu de travail moderne compte plusieurs plateformes d’appareils à la fois personnelles et professionnelles, permet aux utilisateurs de travailler où qu’ils se trouvent et offre des processus informatiques automatisés et proactifs. 

Les services MDM, tels que Microsoft Intune, peuvent gérer les appareils Windows 10 en utilisant le protocole MDM. Le client de gestion Windows 10 intégré peut communiquer avec Intune pour effectuer des tâches de gestion d’entreprise. Il facilite la gestion moderne sur les appareils Windows 10. Il existe toutefois certaines fonctionnalités susceptibles de vous être nécessaires, telles que la configuration avancée des appareils, qui ne sont pas disponibles dans les fonctionnalités MDM intégrées de Windows 10.

L’extension de gestion Intune vient en complément des fonctionnalités MDM de Windows 10 intégrées. Vous pouvez créer des scripts PowerShell à exécuter sur les appareils Windows 10 qui fournissent les fonctionnalités dont vous avez besoin. Vous pouvez créer un script PowerShell qui configure vos paramètres personnalisés, charger le script sur Intune, affecter le script à un groupe Azure Active Directory (AD) et exécuter le script sur les appareils Windows 10. Le script peut être supervisé pour voir l’état de son exécution sur les appareils Windows 10 du début à la fin.

## <a name="prerequisites"></a>Prérequis
L’extension de gestion Intune est soumise aux prérequis suivants :
- Les appareils doivent être joints à Azure AD. L’extension de gestion Intune prend en charge les appareils joints à Azure Active Directory, les appareils joints à un domaine hybrides et les appareils Windows inscrits cogérés.
- Les appareils doivent exécuter Windows 10, version 1607 ou ultérieure.
- L’inscription MDM automatique doit être [activée dans Azure AD](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) et les appareils doivent être inscrits automatiquement auprès d’Intune.

## <a name="create-a-powershell-script-policy"></a>Créer une stratégie de script PowerShell 
1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Scripts PowerShell** > **Ajouter**.
4. Entrez un **Nom** et une **Description** pour le script PowerShell. Pour l’**Emplacement du script**, accédez au script PowerShell. La taille du script doit être inférieure à 200 Ko (ASCII) ou à 100 Ko (Unicode).
5. Choisissez **Configurer**. Indiquez ensuite si vous souhaitez exécuter le script avec les informations d’identification de l’utilisateur sur l’appareil (**Oui**) ou dans le contexte du système (**Non**). Par défaut, le script s’exécute dans le contexte du système. Sélectionnez **Oui**, sauf si le script doit s’exécuter dans le contexte du système. 
  ![Volet Ajouter un script PowerShell](./media/mgmt-extension-add-script.png)
6. Indiquez si le script doit être signé par un éditeur approuvé (**Oui**). Par défaut, il n’est pas nécessaire que le script soit signé. 
7. Sélectionnez **OK**, puis **Créer** pour enregistrer le script.

## <a name="assign-a-powershell-script-policy"></a>Assigner une stratégie de script PowerShell
1. Dans **Scripts PowerShell**, sélectionnez le script à affecter, puis choisissez **Gérer** > **Affectations**.
  ![Volet Ajouter un script PowerShell](./media/mgmt-extension-assignments.png)
 
2. Choisissez **Sélectionner des groupes** pour répertorier les groupes Azure AD disponibles. 
3. Sélectionnez un ou plusieurs groupes contenant les utilisateurs dont les appareils reçoivent le script. Choisissez **Sélectionner** pour affecter la stratégie aux groupes sélectionnés.

> [!NOTE]
> - Les utilisateurs finaux ne sont pas obligés d’être connectés à l’appareil pour exécuter des scripts PowerShell. 
> - Les scripts PowerShell dans Intune peuvent être ciblés sur les groupes de sécurité des appareils AAD.

L’extension de gestion Intune se synchronise avec Intune une fois par heure. Une fois la stratégie affectée aux groupes Azure AD, le script PowerShell s’exécute, puis les résultats de l’exécution sont consignés dans un rapport. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Surveiller l’état de l’exécution des scripts PowerShell
Vous pouvez surveiller l’état de l’exécution des scripts PowerShell pour les utilisateurs et les appareils dans le portail Azure.

Dans **Scripts PowerShell**, sélectionnez le script à surveiller, choisissez **Surveiller**, puis choisissez l’un des rapports suivants :
   - **État de l’appareil**
   - **État de l’utilisateur**

## <a name="delete-a-powershell-script"></a>Supprimer un script PowerShell
Dans **Scripts PowerShell**, cliquez avec le bouton droit sur le script, puis sélectionnez **Supprimer**.
