---
title: Rapport de chiffrement pour les appareils chiffrés dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Consultez un rapport sur l’état de chiffrement de votre appareil iOS ou Windows et accédez aux clés de récupération FileVault et BitLocker à partir du portail Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 64bdc59e08a2b17c82e1798d454f0a0403e61b13
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671060"
---
# <a name="monitor-device-encryption-with-intune"></a>Analyser le chiffrement d’appareil avec Intune   

Le rapport de chiffrement Microsoft Intune est un emplacement centralisé pour voir des détails sur l’état de chiffrement de vos appareils gérés. Affichez des détails sur l’état de chiffrement d’un appareil et accédez aux options de gestion des clés de récupération de l’appareil. Les options des clés de récupération disponibles dépendent du type d’appareil que vous visualisez.  

Pour trouver le rapport, connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et accédez à **Configuration de l’appareil**, puis sous *Surveiller*, sélectionnez **Rapport de chiffrement**.  

## <a name="view-encryption-details"></a>Afficher les détails du chiffrement  

Le rapport de chiffrement montre des détails courants sur les appareils pris en charge que vous gérez. Les sections suivantes fournissent des détails sur les informations présentées par Intune dans le rapport.  
 
### <a name="prerequisites"></a>Prérequis :  

Le rapport de chiffrement prend en charge les appareils qui exécutent les versions de système d’exploitation suivantes :  
- macOS 10.13 ou ultérieur  
- Windows version 1607 ou ultérieure  

### <a name="report-details"></a>Détails du rapport  

Le volet Rapport de chiffrement affiche une liste des appareils que vous gérez avec des informations générales sur ces appareils. Vous pouvez sélectionner un appareil dans la liste pour afficher des détails supplémentaires à partir du volet [État du chiffrement de l’appareil](#device-encryption-status) des appareils.  

- **Nom de l’appareil** : Nom de l’appareil.  
- **Système d’exploitation** : Plateforme de l’appareil, comme Windows ou macOS.  
- **Version du système d’exploitation** : Version de Windows ou de macOS sur l’appareil.  
- **Version TPM** *(S’applique seulement à Windows 10)*  : Version de la puce TPM (Module de plateforme sécurisée) sur l’appareil Windows 10.  
- **Préparation du chiffrement** : Évaluation de la préparation des appareils pour prendre en charge une technologie de chiffrement applicable, comme le chiffrement BitLocker ou FileVault. Les appareils sont identifiés de la manière suivante :  
  - **Prêt** : L’appareil peut être chiffré en utilisant une stratégie MDM, ce qui nécessite qu’il respecte les exigences suivantes :  
    
    **Pour les appareils macOS** :  
    - MacOS version 10.13 ou ultérieure  
    
    **Pour les appareils Windows 10** :  
    - Version 1703 ou ultérieure de l’édition *Professionnel*, *Entreprise*, *Éducation*, ou version 1809 de l’édition *Professionnel*  
    - L’appareil doit avoir une puce TPM  
    
    Pour plus d’informations, consultez le [fournisseur de service de configuration de BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) dans la documentation de Windows.  

  - **Non prêt** : L’appareil n’a pas toutes les fonctionnalités de chiffrement, mais il prend quand même en charge le chiffrement. Par exemple, un appareil Windows peut être chiffré manuellement par un utilisateur ou via une stratégie de groupe définie pour permettre le chiffrement sans TPM.
  - **Non applicable** : Les informations ne sont pas suffisantes pour classifier cet appareil.  

- **État du chiffrement** : indique si le lecteur du système d’exploitation est chiffré.  

- **Nom principal de l’utilisateur** : L’utilisateur principal de l’appareil.  

### <a name="device-encryption-status"></a>État du chiffrement de l’appareil  

Quand vous sélectionnez un appareil dans le rapport de chiffrement, Intune affiche le volet **État du chiffrement de l’appareil**. Ce volet fournit les détails suivants :  

- **Nom de l’appareil** : nom de l’appareil que vous visualisez.  

- **Préparation du chiffrement** : Évaluation de la préparation des appareils à la prise en charge du chiffrement via la stratégie MDM.  
  
  Par exemple : Quand un appareil Windows 10 a un état de préparation *Non prêt*, il peut néanmoins prendre en charge le chiffrement. Pour avoir la désignation*Prêt*, l’appareil Windows 10 doit avoir une puce TPM. Les puces TPM ne sont pas nécessaires pour prendre en charge le chiffrement. (Consultez Préparation du chiffrement dans la section précédente pour plus d’informations.)  

- **État du chiffrement** : indique si le lecteur du système d’exploitation est chiffré. Jusqu’à 24 heures peuvent être nécessaires pour qu’Intune signale l’état de chiffrement d’un appareil ou un changement de cet état.  

- **Profils** : Une liste des profils de *Configuration de l’appareil* qui s’appliquent à cet appareil et sont configurés avec les valeurs suivantes :  

  - macOS :
    - Type de profil = *Endpoint Protection*  
    - Paramètres > FileVault > FileVault = *Activer*

  - Windows 10 :
    - Type de profil = *Endpoint Protection*  
    - Paramètres > Chiffrement Windows > Chiffrer les appareils = *Obligatoire*  

  Vous pouvez utiliser la liste des profils pour identifier des stratégies individuelles à passer en revue si le *Résumé de l’état du profil* indique des problèmes.  

- **Résumé de l’état du profil** : résumé des profils qui s’appliquent à cet appareil. Le récapitulatif représente la condition la moins favorable parmi les profils applicables. Par exemple, si un seul profil parmi plusieurs profils applicables entraîne une erreur, le *Résumé de l’état du profil* indique *Erreur*.  

- **Informations d’état** : détails avancés sur l’état du chiffrement de l’appareil.  

  > [!IMPORTANT]  
  > Pour les appareils Windows 10, Intune montre les *Informations d’état* seulement pour les appareils qui exécutent la *mise à jour d’avril 2019 de Windows 10* ou une version ultérieure.  
  
  Ce champ présente des informations pour chaque erreur applicable pouvant être détectée. Vous pouvez utiliser ces informations pour comprendre pourquoi un appareil n’est pas prêt pour le chiffrement.  

  Voici quelques exemples d’informations d’état qu’Intune peut indiquer :  
  
  **macOS** :
  - Le profil ne peut pas être installé actuellement, car nous attendons un prérequis.  
 
    *Considérez ceci : Ce résultat ne représente pas nécessairement une condition d’erreur, mais un état temporaire qui peut être dû à la synchronisation sur l’appareil où la mise en dépôt pour les clés de récupération doit être configurée avant que la demande de chiffrement soit envoyée à l’appareil. Cela peut également indiquer que l’appareil reste verrouillé ou n’a pas fait l’objet d’un check-in récent avec Intune. Enfin, étant donné que le chiffrement FileVault ne démarre pas tant qu’un appareil n’est pas branché (en charge), il est possible qu’un utilisateur reçoive une clé de récupération pour un appareil qui n’est pas encore chiffré*.  

  - Le profil FileVault est installé, mais FileVault n’est pas activé sur l’appareil.  
 
    *Considérez ceci : L’utilisateur ne s’est pas encore déconnecté après avoir reçu la demande de chiffrement, ce qui est nécessaire avant que FileVault puisse chiffrer l’appareil, ou bien l’utilisateur a déchiffré l’appareil manuellement. Intune ne peut pas empêcher un utilisateur de déchiffrer son appareil.*  

  - FileVault est déjà activé par l’utilisateur et Intune ne peut donc pas gérer sa récupération.  
 
    *Considérez ceci : Intune ne peut pas configurer FileVault sur un appareil qui est déjà chiffré. Au lieu de cela, l’utilisateur doit déchiffrer son appareil manuellement pour qu’il puisse être géré par une stratégie de configuration d’appareil et par Intune*. 
 
  - FileVault nécessite que l’utilisateur approuve son profil de gestion dans macOS Catalina et ultérieur.  
 
    *Considérez ceci : À compter de macOS version 10.15 (Catalina), les paramètres d’inscription approuvés par l’utilisateur peuvent entraîner la nécessité pour les utilisateurs d’approuver manuellement le chiffrement FileVault. Pour plus d’informations, consultez [Inscription approuvée par l’utilisateur](macos-enroll.md) dans la documentation Intune*.  

  - L’appareil iOS a retourné « NotNow » (il est verrouillé).  

    *Considérez ceci : L’appareil est actuellement verrouillé et Intune ne peut pas démarrer le processus de mise en dépôt ou de chiffrement. Une fois l’appareil déverrouillé, la progression peut se poursuivre*.  

  **Windows 10** :  
  - La stratégie BitLocker nécessite le consentement de l’utilisateur pour lancer l’Assistant Chiffrement de lecteur BitLocker et démarrer le chiffrement du volume de système d’exploitation, mais l’utilisateur n’a pas donné son consentement.  
  
  - La méthode de chiffrement du volume de système d’exploitation ne correspond pas à la stratégie BitLocker.  
  
  - La stratégie BitLocker nécessite un protecteur par TPM pour protéger le volume de système d’exploitation, mais aucun TPM n’est utilisé.  
  
  - La stratégie BitLocker nécessite un protecteur uniquement par TPM pour le volume de système d’exploitation, mais aucune protection par TPM n’est utilisée.  
  
  - La stratégie BitLocker nécessite une protection par TPM+code PIN pour le volume de système d’exploitation, mais aucun protecteur de ce type n’est utilisé.  
  
  - La stratégie BitLocker nécessite une protection par TPM+clé de démarrage pour le volume de système d’exploitation, mais aucun protecteur de ce type n’est utilisé.  
  
  - La stratégie BitLocker nécessite une protection par TPM+code PIN+clé de démarrage pour le volume de système d’exploitation, mais aucun protecteur de ce type n’est utilisé.  
  
  - Le volume de système d’exploitation n’est pas protégé.  
  
  - La sauvegarde de la clé de récupération a échoué.  
  
  - Un lecteur fixe n’est pas protégé.  
  
  - La méthode de chiffrement du lecteur fixe ne correspond pas à la stratégie BitLocker.  
  
  - Pour chiffrer les lecteurs, la stratégie BitLocker exige que l’utilisateur se connecte en tant qu’administrateur ou, si l’appareil est joint à Azure AD, que la stratégie AllowStandardUserEncryption ait la valeur 1.  
  
  - L’environnement de récupération Windows (WinRE) n’est pas configuré.  
  
  - Un module de plateforme sécurisée (TPM) n’est pas disponible pour BitLocker, soit parce qu’il n’est pas présent car il est devenu indisponible dans le Registre, soit parce que le système d’exploitation se trouve sur un lecteur amovible.  
  
  - Le module de plateforme sécurisée (TPM) n’est pas prêt pour BitLocker.  
  
  - Le réseau n’est pas disponible, ce qui est nécessaire pour la sauvegarde des clés de récupération.  

## <a name="export-report-details"></a>Exporter les détails du rapport 
Quand vous affichez le volet Rapport de chiffrement , vous pouvez sélectionner **Exporter** pour créer un fichier *.csv* téléchargé des détails du rapport.  Ce rapport comprend les informations générales du volet *Rapport de chiffrement* et des détails sur l’*État du chiffrement de l’appareil* pour chaque appareil que vous gérez.   
 
  
![Exporter les détails](./media/encryption-monitor/export.png) 
 
Ce rapport peut être utilisé pour identifier les problèmes liés aux groupes d’appareils. Par exemple, vous pouvez utiliser le rapport pour identifier une liste d’appareils macOS indiquant tous *FileVault est déjà activé par l’utilisateur*, ce qui signifie que ces appareils doivent être déchiffrés manuellement avant qu’Intune puisse commencer à gérer leurs paramètres FileVault.  
 
## <a name="filevault-recovery-keys"></a>Clés de récupération FileVault   
Quand Intune chiffre un appareil macOS avec FileVault pour la première fois, une clé de récupération personnelle est créée. Lors du chiffrement, l’appareil affiche une seule fois la clé personnelle à l’utilisateur final.  
 
Pour les appareils gérés, Intune peut mettre en dépôt une copie de la clé de récupération personnelle. La mise en dépôt de clés permet aux administrateurs Intune d’effectuer une rotation des clés de façon à mieux protéger les appareils, et à faciliter la récupération par les utilisateurs d’une clé de récupération personnelle perdue ou ayant fait l’objet d’une rotation.  
 
Intune prend en charge plusieurs options pour la rotation et la récupération des clés de récupération personnelles. Une des raisons pour effectuer une rotation de clé est que la clé personnelle actuelle est perdue et que cela est considéré comme présentant un risque.  
 
> [!IMPORTANT]  
>  Les appareils chiffrés par les utilisateurs et non pas par Intune ne peuvent pas être gérés par Intune. Cela signifie qu’Intune ne peut pas mettre en dépôt la récupération personnelle de ces appareils, ni gérer la rotation de la clé de récupération.  Avant qu’Intune puisse gérer les FileVault et les clés de récupération pour l’appareil, l’utilisateur doit déchiffrer son appareil, puis laisser Intune chiffrer celui-ci.  

### <a name="rotate-recovery-keys"></a>Effectuer une rotation des clés de récupération  

- **Rotation automatique** : En tant qu’administrateur, vous pouvez configurer le paramètre FileVault « Rotation de la clé de récupération personnelle » pour générer automatiquement de nouvelles clés de récupération à intervalles réguliers.  Quand une nouvelle clé est générée pour un appareil, elle n’est pas montrée à l’utilisateur. Au lieu de cela, l’utilisateur doit obtenir la clé auprès d’un administrateur ou en utilisant l’application Portail d’entreprise.  

- **Rotation manuelle** : En tant qu’administrateur, vous pouvez voir des informations sur un appareil que vous gérez avec Intune et qui est chiffré avec FileVault. Vous pouvez ensuite choisir d’effectuer manuellement une rotation de cette clé de récupération pour les appareils d’entreprise. Vous ne pouvez pas effectuer une rotation des clés de récupération pour les appareils personnels.  

  Pour effectuer une rotation d’une clé de récupération : 
  1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), accédez à  **Appareils**  puis, sous Gérer, sélectionnez  **Tous les appareils**.  
  2. Dans la liste des appareils, sélectionnez l’appareil qui est chiffré et pour lequel vous voulez effectuer une rotation de sa clé. Ensuite, sous Surveiller, sélectionnez  **Clés de récupération**.  
  3. Dans le volet Clés de récupération, sélectionnez **Faire tourner la clé de récupération FileVault**.  
  
     La prochaine fois que l’appareil effectue un check-in avec Intune, la clé personnelle fait l’objet d’une rotation. Quand c’est nécessaire, la nouvelle clé peut être obtenue par l’utilisateur final via le portail d’entreprise. 


### <a name="recover-recovery-keys"></a>Récupérer les clés de récupération  
- **Administrateur** : Les administrateurs ne peuvent pas voir les clés de récupération personnelles pour les appareils qui sont chiffrés avec FileVault.  

- **Utilisateur final** : Les utilisateurs finaux utilisent le site web Portail d’entreprise à partir de n’importe quel appareil pour voir la clé de récupération personnelle actuelle d’un de leurs appareils gérés. Vous ne pouvez pas voir les clés de récupération à partir de l’application Portail d’entreprise.  

 
  Pour voir une clé de récupération :  
  1. Connectez-vous au site web *Portail d’entreprise Intune* à partir de n’importe quel appareil.  
  2. Dans le portail, accédez à **Appareils**, puis sélectionnez l’appareil macOS qui est chiffré avec FileVault.  
  3. Sélectionnez **Obtenir la clé de récupération**. La clé de récupération actuelle est affichée.  
  
     Sur un iPhone, vous devez sélectionner les *trois* points avant que l’option *Obtenir la clé de récupération* s’affiche.  

## <a name="bitlocker-recovery-keys"></a>Clés de récupération BitLocker  

Intune fournit l’accès au panneau Azure AD pour BitLocker pour que vous puissiez voir les ID de clé BitLocker et les clés de récupération de vos appareils Windows 10, à partir du portail Intune.  Pour être accessible, l’appareil doit avoir ses clés déposées dans Azure AD. 
1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), accédez à **Appareils**, puis sous *Gérer*, sélectionnez **Tous les appareils**.  

2. Sélectionnez un appareil dans la liste, puis sous *Surveiller*, sélectionnez **Clés de récupération**.  
  
Quand des clés sont disponibles dans Azure AD, les informations suivantes sont disponibles :
- ID de clé BitLocker  
- Clé de récupération BitLocker  
- Type de lecteur  

Quand les clés ne sont pas dans Azure AD, Intune indique *Aucune clé BitLocker trouvée pour cet appareil*.  

Les informations pour BitLocker sont obtenues en utilisant le [fournisseur de service de configuration BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp). Ce dernier est pris en charge sur Windows 10 versions 1703 et ultérieures et sur Windows 10 Pro versions 1809 et ultérieures.  

## <a name="next-steps"></a>Étapes suivantes  

Créer une stratégie de [conformité des appareils](compliance-policy-create-windows.md).
