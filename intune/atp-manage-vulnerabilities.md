---
title: Utiliser Intune pour corriger les vulnérabilités détectées par Microsoft Defender ATP – Azure | Microsoft Docs
description: Voir comment gérer des tâches de sécurité à partir de Threat & Vulnerability Management, qui fait partie de Microsoft Defender Advanced Threat Protection (ATP) dans la console Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 987e3171c4e5c5ba3f15097837e2c018ddc7a4b6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049196"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>Utiliser Intune pour corriger les vulnérabilités identifiées par Microsoft Defender ATP  

Lorsque vous intégrez Intune à Microsoft Defender Advanced Threat Protection (ATP), vous pouvez tirer parti de Threat & Vulnerability Management (TVM) d’ATP et utiliser Intune pour corriger la faiblesse de point de terminaison identifiée par TVM. Cette intégration permet une approche basée sur les risques de la découverte et de la hiérarchisation des vulnérabilités qui peut améliorer les temps de réponse de correction au sein de votre environnement.  

[Threat & Vulnerability Management](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt) fait partie de [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection).  

## <a name="how-integration-works"></a>Fonctionnement de l’intégration  

Une fois que vous vous connectez Intune à Microsoft Defender Advanced Threat Protection, ATP reçoit contre les détails des menaces et des vulnérabilités des appareils gérés.  

Dans la console Windows Defender Security Center, les administrateurs de sécurité ATP administrent les données de révision sur les vulnérabilités du point de terminaison. Ensuite, par un simple clic, les administrateurs créent des tâches de sécurité qui signalent les appareils vulnérables à corriger. Les tâches de sécurité sont immédiatement transmises à la console Intune, où les administrateurs Intune peuvent les afficher. La tâche de sécurité identifie le type de vulnérabilité, la priorité, l’état et les étapes à suivre pour corriger la vulnérabilité. L’administrateur Intune choisit d’accepter ou de rejeter la tâche.  

Lorsqu’une tâche est acceptée, l’administrateur Intune agit alors pour corriger la vulnérabilité dans tout Intune en suivant les instructions fournies dans le cadre de la tâche de sécurité.  

Les actions courantes de correction sont les suivantes :  
- **Bloquer** l’exécution d’une application  
- **Déployer** une mise à jour du système d’exploitation pour atténuer la vulnérabilité.  
- **Modifier** une valeur de Registre.  
- **Désactiver** ou **Activer** une configuration pour affecter la vulnérabilité.  
- Les alertes **Attention** avertissent l’administrateur de la menace lorsqu’aucune recommandation appropriée ne peut être fournie.  

Un exemple de flux de travail :  
- Au sein de Microsoft Defender ATP, une vulnérabilité est détectée pour une application nommée Contoso Media Player v4, et un administrateur crée une tâche de sécurité pour mettre à jour cette application. Le lecteur multimédia Contoso est une application non managée qui a été déployée avec Intune.  

  La tâche de sécurité s’affiche dans la console Intune avec l’état En attente :  
  ![Afficher la liste des tâches de sécurité dans la console Intune](./media/atp-manage-vulnerabilities/temp-security-tasks.png)
 
- L’administrateur Intune sélectionne la tâche de sécurité pour en afficher les détails.  L’administrateur sélectionne ensuite **Accepter**, qui met à jour l’état dans Intune et dans ATP pour que la tâche soit *Acceptée*.  
  ![Accepter ou rejeter une tâche de sécurité](./media/atp-manage-vulnerabilities/temp-accept-task.png) 
 
- L’administrateur corrige alors la tâche selon les instructions fournies.  Les instructions varient selon le type de correction nécessaire. Lorsqu’ils sont disponibles, les conseils de correction incluent des liens ouvrant les volets pertinents pour les configurations dans Intune. 

  Étant donné que le lecteur multimédia dans cet exemple n’est pas une application managée, Intune peut fournir uniquement des instructions sous forme de texte. Si l’application était managée, Intune peut fournir des instructions pour télécharger une version mise à jour et fournir un lien permettant d’ouvrir le déploiement de l’application afin que les fichiers mis à jour puissent être ajoutés au déploiement. 

- Après avoir effectué la correction, l’administrateur Intune ouvre la tâche de sécurité et sélectionne **Effectuer la tâche**.  L’état de correction est mis à jour pour Intune et dans ATP, où les administrateurs de sécurité confirment l’état révisé pour la vulnérabilité.  

## <a name="prerequisites"></a>Prérequis  

**Abonnements** :  
- Microsoft Intune  
- Microsoft Defender Advanced Threat Protection ([S’inscrire pour un essai gratuit](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink).)  

**Configurations Intune pour ATP** :  
- Configurer une connexion de service à service avec Microsoft Defender ATP.  
- Déployer une stratégie de conformité d’appareil avec un type de profil de **Microsoft Defender ATP (Windows 10 Desktop)** sur des appareils dont les risques sont évalués par ATP.
  Pour plus d’informations sur configuration d’Intune pour utiliser ATP, consultez [Appliquer la conformité pour Microsoft Defender ATP avec accès conditionnel dans Intune](https://docs.microsoft.com/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).  

## <a name="work-with-security-tasks"></a>Travailler avec des tâches de sécurité  

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et accédez à **Sécurité des appareils** > **Tâches de sécurité**.  
2. Sélectionnez une tâche dans la liste pour ouvrir une fenêtre de ressources qui affiche des détails supplémentaires sur cette tâche de sécurité.  
3. Lorsque vous affichez la fenêtre de ressource de la tâche de sécurité, vous pouvez sélectionner des liens supplémentaires :  
   - APPLICATIONS GÉRÉES : afficher l’application vulnérable. Lorsque la vulnérabilité s’applique à plusieurs applications, vous voyez une liste filtrée des applications.  
   - APPAREILS : afficher une liste des *Appareils vulnérables* à partir de laquelle vous pouvez accéder via un lien à une entrée contenant plus de détails sur la vulnérabilité de ces appareils.  
   - DEMANDEUR : utiliser le lien suivant pour envoyer du courrier à l’administrateur qui a envoyé cette tâche de sécurité.  
   - NOTES : lire des messages personnalisés envoyés par le demandeur lors de l’ouverture de la tâche de sécurité.  
4. Sélectionnez **Accepter** ou **Rejeter** pour envoyer à ATP une notification relative à votre action planifiée. Lorsque vous acceptez ou rejetez une tâche, vous pouvez envoyer des notes qui sont envoyées à ATP.  

5. Après avoir accepté une tâche, rouvrez la tâche de sécurité (si elle est fermée), puis suivez les détails de CORRECTION pour corriger la vulnérabilité.  Les instructions fournies par ATP dans les détails de la tâche de sécurité varient en fonction de la vulnérabilité concernée.  

   Lorsque c’est possible, les instructions de correction incluent des liens qui ouvrent les objets de configuration pertinents dans la console Intune.  

6. Après avoir effectué les étapes de correction, ouvrez la tâche de sécurité et sélectionnez **Effectuer la tâche**.  Cette action met à jour l’état de la tâche de sécurité dans Intune et dans ATP.  

Après la correction, le score de risque d’exposition dans ATP peut baisser en raison des nouvelles informations provenant des appareils corrigés. 

## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur Intune et sur [Microsoft Defender ATP](https://docs.microsoft.com/intune/advanced-threat-protection)  
Révision [Mobile Threat Defense](https://docs.microsoft.com/intune/mobile-threat-defense) d’Intune  
Examinez le [Tableau de bord de Threat & Vulnerability Management](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights) dans Microsoft Defender ATP
