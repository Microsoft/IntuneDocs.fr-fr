---
title: Paramètres Windows Update pour Entreprise pour Microsoft Intune - Azure | Microsoft Docs
description: Paramètres WUfB pour les appareils Windows 10 que vous pouvez déployer à l’aide d’Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c5a0ee88a24804294346888facef523f89fee816
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046651"
---
# <a name="windows-update-settings-for-intune"></a>Paramètres de mise à jour Windows pour Intune  

Afficher les paramètres de Windows 10 Update que vous pouvez [configurer et gérer](windows-update-for-business-configure.md) avec Microsoft Intune.  

Lorsque vous configurez des paramètres pour des anneaux de mise à jour Windows 10 dans Intune, vous configurez les paramètres de Windows Update. Si un paramètre de mise à jour Windows dépend d’une version de Windows 10, la dépendance de version est indiquée dans les détails des paramètres.  

## <a name="update-settings"></a>Paramètres de mise à jour  

Les paramètres de mise à jour contrôlent quels bits un appareil va télécharger, et quand. Pour plus d’informations sur le comportement de chaque paramètre, consultez la documentation de référence de Windows.  

### <a name="servicing-channel"></a>Canal de maintenance  

- **Par défaut** : canal semi-annuel (ciblé)  
- **Documentation de référence de Windows** : [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  
Définissez le canal (la branche) à partir duquel l’appareil reçoit les mises à jour Windows. Différents canaux peuvent utiliser des points de report différents avant la livraison des mises à jour.  

Par exemple, le *canal semi-annuel* a un report de six mois. Si vous utilisez ce canal sans report supplémentaire à partir de ce corps de paramètres, l’appareil installe la mise à jour six mois après sa publication.  

Canaux de mise à jour pris en charge :  

- Canal semi-annuel  
- Canal semi-annuel (ciblé)  
- Windows Insider — Rapide  
- Windows Insider — Lent  
- Publier Windows Insider  

Si vous sélectionnez un canal Insider, Intune configure automatiquement le paramètre de mise à jour Windows [mise à jour/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds) afin que le build Insider fonctionne.  


> [!IMPORTANT]  
> À partir de Windows version 1903, l’utilisation du *canal semi-annuel (ciblé)* (SAC-T) est supprimée. Avec cette modification, la console SAC-T fusionne avec le *canal semi-annuel*. Pour en savoir plus sur cette modification et sur la manière dont elle affecte Windows Update pour Entreprise, consultez le billet de Blog de Windows IT Pro [Windows Update pour les entreprises et retrait de la console SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523).
 


### <a name="microsoft-product-updates"></a>Mises à jour de produits Microsoft  

- **Valeur Par défaut** : Autoriser
- **Documentation de référence de Windows** : [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

Choisissez si vous souhaitez *Autoriser* une recherche de mises à jour d’applications à partir de Microsoft Update.    

### <a name="windows-drivers"></a>Pilotes Windows  

- **Valeur Par défaut** : Autoriser
- **Documentation de référence de Windows** : [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)

Choisissez *Autoriser* pour inclure des pilotes Windows Update pendant les mises à jour

### <a name="quality-update-deferral-period-days"></a>Période de report des mises à jour de qualité (jours)  

- **Par défaut** : 0  
- **Documentation de référence de Windows** : [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

Spécifiez le nombre de jours (entre 0 et 30) durant lesquels les mises à jour de qualité sont reportées. Cette période s’ajoute à toute période de report faisant partie de la couche de service sélectionnée. La période de report commence lorsque la stratégie est reçue par l’appareil.  

En règle générale, les mises à jour qualité sont des correctifs et des améliorations apportées aux fonctionnalités existantes de Windows.  

### <a name="feature-update-deferral-period-days"></a>Période de report des mises à jour des fonctionnalités (jours)  

- **Par défaut** : 0  
- **Documentation de référence de Windows** : [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

Spécifiez le nombre de jours durant lesquels les mises à jour de fonctionnalités sont différées. Cette période s’ajoute à toute période de report faisant partie de la couche de service sélectionnée. La période de report commence lorsque la stratégie est reçue par l’appareil.  
Période de report prise en charge :  

- *Windows version 1709 ou ultérieure*: 0 à 365 jours  
- *Windows version 1703*: 0 à 180 jours  

En règle générale, les mises à jour de fonctionnalités correspondent à de nouvelles fonctionnalités de Windows.  

### <a name="set-feature-update-uninstall-period-2--60-days"></a>Définissez la période de désinstallation des mises à jour de fonctionnalités (2 à 60 jours)  

- **Par défaut** : 10  
- **Documentation de référence de Windows** : [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

Configurer une période après laquelle les mises à jour de fonctionnalités ne peuvent pas être désinstallées.  

Après expiration de cette période, les bits de mise à jour précédentes sont supprimés de l’appareil et une désinstallation vers une version de mise à jour précédente n’est plus possible.  

Par exemple, considérez un anneau de mise à jour avec une période de désinstallation des mises à jour de fonctionnalités de 20 jours. Après 25 jours, vous décidez d’annuler la dernière mise à jour de fonctionnalité et d’utiliser l’option de désinstallation.  Les appareils qui ont installé la mise à jour de fonctionnalité il y a plus de 20 jours ne peuvent pas la désinstaller, puisqu’ils ont supprimé les bits nécessaires dans le cadre de leur maintenance. Cependant, les appareils qui ont installé la mise à jour des fonctionnalités il y a 19 jours maximum peuvent désinstaller la mise à jour s’ils ont réussi à s’enregistrer pour recevoir la commande de désinstallation avant que la période de désinstallation de 20 jours n’ait expiré.  


## <a name="user-experience-settings"></a>Paramètres d’expérience utilisateur  

Paramètres de l’expérience utilisateur contrôlent l’expérience de l’utilisateur final en matière de redémarrage de l’appareil et de rappels. Pour plus d’informations sur le comportement de chaque paramètre, consultez la documentation de référence de Windows.  

### <a name="automatic-update-behavior"></a>Comportement des mises à jour automatiques  

- **Par défaut** : installer et redémarrer automatiquement à un moment planifié  
- **Documentation de référence de Windows** : [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

Choisissez le mode d’installation des mises à jour automatiques et, si nécessaire, le moment où l’appareil redémarre.  

Reportez-vous à la documentation de référence de Windows pour la divulgation intégrale des options prises en charge suivantes :  

- **Notification de téléchargement** : informer l’utilisateur avant de télécharger la mise à jour. Les utilisateurs choisissent de télécharger et d’installer les mises à jour.  

- **Installer automatiquement au moment de la maintenance** : téléchargement automatique des mises à jour, puis installation lors de la maintenance automatique quand l’appareil n’est pas utilisé ou fonctionne sur batterie. Lorsqu’un redémarrage est nécessaire, les utilisateurs sont invités à redémarrer l’appareil pendant sept jours, après quoi un redémarrage forcé a lieu.  

  Cette option peut redémarrer un appareil automatiquement après l’installation de la mise à jour. Utilisez les paramètres **Heures actives** pour définir une période pendant laquelle les redémarrages automatiques sont bloqués :  

  - **Début des heures d’activité** : spécifiez une heure de début pour la suppression des redémarrages liés aux installations de mise à jour.  
    **Documentation de référence de Windows** : [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Par défaut** : 8h00  
  
  - **Fin des heures d’activité** : spécifiez une heure de fin pour la suppression des redémarrages liés aux installations de mise à jour.  
    **Documentation de référence de Windows** : [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Par défaut** : 5 PM  

- **Installer automatiquement et redémarrer au moment de la maintenance** : téléchargement automatique des mises à jour, puis installation lors de la maintenance automatique lorsque l’appareil n’est pas utilisé ou fonctionne sur batterie. Lorsque le redémarrage est nécessaire, l’appareil redémarre lorsqu’il n’est pas utilisé. (C’est la valeur par défaut pour les appareils non gérés.)  

  Cette option peut redémarrer un appareil automatiquement après l’installation de la mise à jour. L’utilisation des paramètres **Heures actives** n’est pas décrite dans les paramètres de mise à jour de Windows, mais Intune s’en sert pour définir une période pendant laquelle les redémarrages automatiques sont bloqués :  

  - **Début des heures d’activité** : spécifiez une heure de début pour la suppression des redémarrages liés aux installations de mise à jour.  
    **Documentation de référence de Windows** : [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
    **Par défaut** : 8h00  

  - **Fin des heures d’activité** : spécifiez une heure de fin pour la suppression des redémarrages liés aux installations de mise à jour.  
    **Documentation de référence de Windows** : [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  
    **Par défaut** : 5 PM  

- **Installer automatiquement et redémarrer à l’heure planifiée** : spécifier le jour et l’heure pour une installation. Si rien n’est spécifié, installation s’exécute à 15 heures tous les jours et est suivie d’un compte à rebours de 15 minutes avant un redémarrage. Les utilisateurs connectés peuvent retarder le compte à rebours et redémarrer.  
  
  Cette option prend en charge des paramètres supplémentaires.  
  **Documentation de référence de Windows** : [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  - **Fréquence automatique de comportement** : utilisez ce paramètre pour planifier l’installation des mises à jour, notamment la semaine, le jour et l’heure.  
    **Par défaut** : Toutes les semaines

  - **Jour d’installation planifié** : spécifiez quel jour de la semaine vous souhaitez installer les mises à jour.  
    **Par défaut**: N’importe quel jour  

  - **Heure d’installation planifiée** : spécifiez l’heure de la journée souhaitée pour l’installation des mises à jour.  
    **Par défaut** : 3h00  

- **Installer automatiquement et redémarrer sans contrôle de l’utilisateur final** : téléchargement automatique des mises à jour, puis installation lors de la maintenance automatique lorsque l’appareil n’est pas utilisé ou fonctionne sur batterie. Lorsque le redémarrage est nécessaire, l’appareil redémarre lorsqu’il n’est pas utilisé. Cette option définit le volet de contrôle des utilisateurs en mode de lecture seule.  

- **Rétablir les valeurs par défaut** restaure les paramètres de mise à jour automatique d’origine sur les machines Windows 10 qui exécutent la mise à jour d’octobre 2018 ou version ultérieure.  


### <a name="restart-checks"></a>Vérifications de redémarrage  

- **Valeur Par défaut** : Autoriser  
- **Documentation de référence de Windows** : [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

Ce paramètre a des résultats différents selon la version de Windows sur les appareils :  

- Version 1703 de Windows et versions antérieures : lorsque vous redémarrez un appareil, certaines vérifications sont effectuées : utilisateurs actifs, niveaux de batterie, jeux en cours d’exécution, etc. Pour ignorer ces vérifications quand vous redémarrez un appareil, sélectionnez **Ignorer**.  
- À compter de Windows version 1709 : pendant les heures d’activité, les processus suivants n’exécutent pas de mises à jour : analyse, téléchargement, installation et redémarrage. Après les heures d’activité, les processus de mise à jour sont exécutés et peuvent sortir l’appareil de veille, analyser, télécharger, installer et redémarrer l’appareil tant que les vérifications de la batterie et de l’alimentation électrique donnent de bons résultats. Pour plus d’informations, consultez [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart).  

### <a name="block-user-from-pausing-windows-updates"></a>Empêcher l’utilisateur de suspendre les mises à jour Windows  

- **Valeur Par défaut** : Autoriser  
- **Documentation de référence de Windows** : [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

Autoriser un utilisateur de l’appareil à suspendre l’installation d’une mise à jour ou l’en empêcher. 

### <a name="block-user-from-scanning-for-windows-updates"></a>Empêcher l’utilisateur de rechercher les mises à jour de Windows  
 - **Valeur Par défaut** : Autoriser
 - **Documentation de référence de Windows** : [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

Spécifie s’il faut autoriser ou bloquer l’accès d’un utilisateur à l’analyse Windows Update. Par exemple, si vous configurez un *blocage*, l’utilisateur ne peut pas accéder aux fonctionnalités Windows Update d’analyse, de téléchargement et d’installation.  

### <a name="require-users-approval-to-restart-outside-of-work-hours"></a>Exiger l’approbation de l’utilisateur pour redémarrer en dehors des heures de travail  

- **Par défaut** : Non configuré  
- **Documentation de référence de Windows** : [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
Sélectionnez *Requis* pour exiger qu’un utilisateur approuve un redémarrage de l’appareil en dehors des heures de travail.  
   
### <a name="remind-user-prior-to-required-auto-restart-with-dismissible-reminder-hours"></a>Adresser un rappel pouvant être ignoré à l’utilisateur avant le redémarrage automatique requis (heures)  

- **Par défaut** : *ce paramètre n’est pas configuré par défaut, et aucun rappel n’est adressé aux utilisateurs*.  
- **Documentation de référence de Windows** : [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

Spécifiez combien de temps avant un redémarrage automatique adresser une notification pouvant être ignorée à l’utilisateur d’un appareil. Des valeurs de **2**, **4**, **8**, **12** ou **24** heures sont prises en charge.  

### <a name="remind-user-prior-to-required-auto-restart-with-permanent-reminder-minutes"></a>Adresser un rappel permanent à l’utilisateur avant le redémarrage automatique requis (minutes)  

- **Par défaut** : *ce paramètre n’est pas configuré par défaut, et aucun rappel n’est adressé aux utilisateurs*.  
- **Documentation de référence de Windows** : [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning) 

Spécifiez combien de temps avant un redémarrage automatique adresser un avertissement ne pouvant pas être ignoré à l’utilisateur d’un appareil. Des valeurs de **15**, **30** ou **60** minutes sont prises en charge.  

### <a name="windows-update-notification-level"></a>Niveau de notification Windows Update  
- **Par défaut** : utiliser les notifications Windows Update par défaut 
- **Documentation de référence de Windows** : [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)

Spécifiez le niveau de notifications Windows Update que voient les utilisateurs. Ce paramètre ne contrôle pas comment et quand les mises à jour sont téléchargées et installées.

### <a name="allow-user-to-restart-engaged-restart"></a>Autoriser l’utilisateur à redémarrer (redémarrage engagé)  

- **Par défaut** : Non configuré  
- **Documentation de référence de Windows**: *Non applicable*  
- **Version de Windows** : Prise en charge pour Windows 10 versions 1803 et ultérieures  

  > [!NOTE]  
  > Windows 10 version 1809 introduit des paramètres de redémarrage engagé supplémentaires permettant d’appliquer des paramètres distincts aux mises à jour de qualité et de fonctionnalité. Toutefois, les paramètres gérés par Intune ne s’appliquent pas séparément pour les types de mise à jour différents. Au lieu de cela, Intune applique les mêmes valeurs aux mises à jour de qualité et de fonctionnalité.  

La valeur **Requis** vous permet d’utiliser les options de redémarrage engagé pour les mises à jour Windows 10. Ces options engagent l’utilisateur d’un appareil pour aider à gérer quand redémarrer un appareil après l’installation d’une mise à jour qui nécessite un redémarrage.  

Pour plus d’informations sur cette option, consultez [Redémarrage engagé](https://docs.microsoft.com/windows/deployment/update/waas-restart#engaged-restart) dans la documentation de Windows 10 sur le déploiement des mises à jour.  

Les paramètres suivants sont utilisés pour contrôler quand les actions de redémarrage engagé se produisent.  

- **Transition des utilisateurs vers un redémarrage engagé après un redémarrage automatique (jours)**  
  - **Par défaut** : par défaut, ce paramètre n’est pas configuré, mais prend en charge une valeur comprise entre **2** et **30**.  
  - **Documentation de référence de Windows** : [Update/EngagedRestartTransitionSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestarttransitionschedule)  
  Spécifiez combien de temps après l’installation de la mise à jour l'appareil entre dans le comportement de redémarrage engagé. Après le nombre de jours configuré, les utilisateurs reçoivent une invite de redémarrage de l’appareil.  

- **Répéter le rappel de redémarrage engagés (jours)**  
  - **Par défaut** : par défaut, ce paramètre n’est pas configuré, mais prend en charge une valeur comprise entre **1** et **3**.  
  - **Documentation de référence de Windows** : [Update/EngagedRestartSnoozeSchedule](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartsnoozeschedule)  
  Spécifiez la durée pendant laquelle une invite de redémarrage peut être répétée.  Après la période de répétition, l’invite de redémarrage est à nouveau proposée. L’utilisateur peut continuer à répéter le rappel jusqu'à ce que l’échéance d’installation soit atteinte.  

- **Définir une échéance pour les redémarrages en attente (jours)**  
  - **Par défaut** : par défaut, ce paramètre n’est pas configuré, mais prend en charge une valeur comprise entre **2** et **30**.  
  - **Documentation de référence de Windows**: [Update/EngagedRestartDeadline](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-engagedrestartdeadline)  
  Spécifiez un nombre maximal de jours d’attente après le début du comportement de redémarrage engagé avant qu’un appareil n’applique un redémarrage requis. Ce redémarrage invite les utilisateurs à enregistrer leur travail.

### <a name="delivery-optimization-download-mode"></a>Mode de téléchargement de l’optimisation de la livraison  

L’optimisation de la distribution n’est plus configurée dans le cadre d’une boucle de mise à jour Windows 10 sous Mises à jour logicielles. L’optimisation de la distribution est maintenant définie via la configuration de l’appareil. Toutefois, les configurations précédentes restent disponibles dans la console. Vous pouvez supprimer ces configurations précédentes en les modifiant pour être *Non configurées*, mais elles ne peuvent pas être changées autrement. 

Pour éviter les conflits entre l’ancienne et la nouvelle stratégie, consultez [Passer des boucles de mise à jour à l’optimisation de la distribution](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization), puis déplacez vos paramètres vers un profil d’optimisation de la distribution.
