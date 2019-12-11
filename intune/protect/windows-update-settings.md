---
title: Paramètres Windows Update pour Entreprise pour Microsoft Intune - Azure | Microsoft Docs
description: Paramètres WUfB pour les appareils Windows 10 que vous pouvez déployer à l’aide d’Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f3359bc5544b3a353271ea17083c8c3acb49742
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72584462"
---
# <a name="windows-update-settings-for-intune"></a>Paramètres de mise à jour Windows pour Intune  

Afficher les paramètres de Windows 10 Update que vous pouvez [configurer et gérer](windows-update-for-business-configure.md) avec Microsoft Intune.  

Lorsque vous configurez des paramètres pour des anneaux de mise à jour Windows 10 dans Intune, vous configurez les paramètres de Windows Update. Si un paramètre de mise à jour Windows dépend d’une version de Windows 10, la dépendance de version est indiquée dans les détails des paramètres.  

## <a name="update-settings"></a>Paramètres de mise à jour  

Les paramètres de mise à jour contrôlent quels bits un appareil va télécharger, et quand. Pour plus d’informations sur le comportement de chaque paramètre, consultez la documentation de référence de Windows.  

- **Canal de maintenance**  
  **Par défaut** : canal semi-annuel  
  CSP Windows Update : [Update/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

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
 
- **Mises à jour de produit Microsoft**  
  **Valeur Par défaut** : Autoriser  
  CSP Windows Update : [Update/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **Autoriser** : sélectionnez *autoriser* pour rechercher des mises à jour d’application à partir de Microsoft Update.  
  - **Bloc-sélectionnez** bloquer pour empêcher l’analyse des mises à jour d’application.  

- **Pilotes Windows**  
  **Valeur Par défaut** : Autoriser  
  CSP Windows Update : [Update/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **Autoriser** : sélectionnez *autoriser* inclure les pilotes de Windows Update lors des mises à jour.  
  - **Bloc** -sélectionnez bloquer pour empêcher l’analyse des pilotes.  

- **Période de report des mises à jour de qualité (jours)**  
  **Par défaut** : 0  
  CSP Windows Update : [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  Spécifiez le nombre de jours (entre 0 et 30) durant lesquels les mises à jour de qualité sont reportées. Cette période s’ajoute à toute période de report faisant partie de la couche de service sélectionnée. La période de report commence lorsque la stratégie est reçue par l’appareil.  

  En règle générale, les mises à jour qualité sont des correctifs et des améliorations apportées aux fonctionnalités existantes de Windows.  

- **Période de report des mises à jour des fonctionnalités (jours)**  
  **Par défaut** : 0  
  CSP Windows Update : [Update/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  Spécifiez le nombre de jours durant lesquels les mises à jour de fonctionnalités sont différées. Cette période s’ajoute à toute période de report faisant partie de la couche de service sélectionnée. La période de report commence lorsque la stratégie est reçue par l’appareil.  

  Période de report prise en charge :  

  - *Windows version 1709 et versions ultérieures* -de 0 à 365 jours  
  - *Windows version 1703* : 0 à 180 jours  

  En règle générale, les mises à jour de fonctionnalités correspondent à de nouvelles fonctionnalités de Windows.  

- **Définissez la période de désinstallation des mises à jour de fonctionnalités (2 à 60 jours)**  
  **Par défaut** : 10  
  CSP Windows Update : [Update/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  Configurer une période après laquelle les mises à jour de fonctionnalités ne peuvent pas être désinstallées.  

  Après expiration de cette période, les bits de mise à jour précédentes sont supprimés de l’appareil et une désinstallation vers une version de mise à jour précédente n’est plus possible.  

  Par exemple, considérez un anneau de mise à jour avec une période de désinstallation des mises à jour de fonctionnalités de 20 jours. Après 25 jours, vous décidez d’annuler la dernière mise à jour de fonctionnalité et d’utiliser l’option de désinstallation.  Les appareils qui ont installé la mise à jour de fonctionnalité il y a plus de 20 jours ne peuvent pas la désinstaller, puisqu’ils ont supprimé les bits nécessaires dans le cadre de leur maintenance. Cependant, les appareils qui ont installé la mise à jour des fonctionnalités il y a 19 jours maximum peuvent désinstaller la mise à jour s’ils ont réussi à s’enregistrer pour recevoir la commande de désinstallation avant que la période de désinstallation de 20 jours n’ait expiré.  

## <a name="user-experience-settings"></a>Paramètres d’expérience utilisateur  

Paramètres de l’expérience utilisateur contrôlent l’expérience de l’utilisateur final en matière de redémarrage de l’appareil et de rappels. Pour plus d’informations sur le comportement de chaque paramètre, consultez la documentation Windows Update CSP.  

- **Comportement des mises à jour automatiques**  
  **Par défaut** : installer automatiquement au moment de la maintenance  
  CSP Windows Update : [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  Choisissez le mode d’installation des mises à jour automatiques et, si nécessaire, le moment où l’appareil redémarre.  

  Options prises en charge :  

  - **Notification de téléchargement** : informer l’utilisateur avant de télécharger la mise à jour. Les utilisateurs choisissent de télécharger et d’installer les mises à jour.  

  - **Installer automatiquement au moment de la maintenance** : téléchargement automatique des mises à jour, puis installation lors de la maintenance automatique quand l’appareil n’est pas utilisé ou fonctionne sur batterie. Lorsqu’un redémarrage est nécessaire, les utilisateurs sont invités à redémarrer l’appareil pendant sept jours, après quoi un redémarrage forcé a lieu.  

    Cette option peut redémarrer un appareil automatiquement après l’installation de la mise à jour. Utilisez les paramètres **Heures actives** pour définir une période pendant laquelle les redémarrages automatiques sont bloqués :  

    - **Début des heures d’activité** : spécifiez une heure de début pour la suppression des redémarrages liés aux installations de mise à jour.  
      **Par défaut** : 8h00  
      CSP Windows Update : [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fin des heures d’activité** : spécifiez une heure de fin pour la suppression des redémarrages liés aux installations de mise à jour.  
      **Par défaut** : 5 PM  
      CSP Windows Update : [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Installer automatiquement et redémarrer au moment de la maintenance** : téléchargement automatique des mises à jour, puis installation lors de la maintenance automatique lorsque l’appareil n’est pas utilisé ou fonctionne sur batterie. Lorsque le redémarrage est nécessaire, l’appareil redémarre lorsqu’il n’est pas utilisé. (C’est la valeur par défaut pour les appareils non gérés.)  

    Cette option peut redémarrer un appareil automatiquement après l’installation de la mise à jour. L’utilisation des paramètres **Heures actives** n’est pas décrite dans les paramètres de mise à jour de Windows, mais Intune s’en sert pour définir une période pendant laquelle les redémarrages automatiques sont bloqués :  

    - **Début des heures d’activité** : spécifiez une heure de début pour la suppression des redémarrages liés aux installations de mise à jour.  
      **Par défaut** : 8h00  
      CSP Windows Update : [Update/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **Fin des heures d’activité** : spécifiez une heure de fin pour la suppression des redémarrages liés aux installations de mise à jour.  
      **Par défaut** : 5 PM  
      CSP Windows Update : [Update/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **Installer automatiquement et redémarrer à l’heure planifiée** : spécifier le jour et l’heure pour une installation. Si rien n’est spécifié, installation s’exécute à 15 heures tous les jours et est suivie d’un compte à rebours de 15 minutes avant un redémarrage. Les utilisateurs connectés peuvent retarder le compte à rebours et redémarrer.   
  CSP Windows Update : [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    Cette option prend en charge des paramètres supplémentaires.  

    - **Fréquence automatique de comportement** : utilisez ce paramètre pour planifier l’installation des mises à jour, notamment la semaine, le jour et l’heure.  
      **Par défaut** : Toutes les semaines

    - **Jour d’installation planifié** : spécifiez quel jour de la semaine vous souhaitez installer les mises à jour.  
      **Par défaut**: N’importe quel jour  

    - **Heure d’installation planifiée** : spécifiez l’heure de la journée souhaitée pour l’installation des mises à jour.  
      **Par défaut** : 3h00  

  - **Installer automatiquement et redémarrer sans contrôle de l’utilisateur final** : téléchargement automatique des mises à jour, puis installation lors de la maintenance automatique lorsque l’appareil n’est pas utilisé ou fonctionne sur batterie. Lorsque le redémarrage est nécessaire, l’appareil redémarre lorsqu’il n’est pas utilisé. Cette option définit le volet de contrôle des utilisateurs en mode de lecture seule.  

  - **Rétablir les valeurs par défaut** restaure les paramètres de mise à jour automatique d’origine sur les machines Windows 10 qui exécutent la mise à jour d’octobre 2018 ou version ultérieure.  


- **Vérifications de redémarrage**  
  **Valeur Par défaut** : Autoriser  
  CSP Windows Update : [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  Pour ignorer ces vérifications quand vous redémarrez un appareil, sélectionnez **Ignorer**. 
  
  Ce paramètre a des résultats différents selon la version de Windows sur les appareils :  
 
  - *Version 1703 de Windows et versions antérieures* : lorsque vous redémarrez un appareil, certaines vérifications sont effectuées : utilisateurs actifs, niveaux de batterie, jeux en cours d’exécution, etc.  
  
  - *À compter de la version 1709 de Windows*: pendant les heures d’activité, les processus suivants n’exécutent pas de mises à jour : analyse, téléchargement, installation et redémarrage. Après les heures d’activité, les processus de mise à jour sont exécutés et peuvent sortir l’appareil de veille, analyser, télécharger, installer et redémarrer l’appareil tant que les vérifications de la batterie et de l’alimentation électrique donnent de bons résultats. 

- **Empêcher l’utilisateur de suspendre les mises à jour Windows**  
  **Valeur Par défaut** : Autoriser  
  CSP Windows Update : [Update/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **Autoriser** : autoriser les utilisateurs d’appareils à suspendre l’installation d’une mise à jour.  
  - **Bloquer** : empêche les utilisateurs de l’appareil de suspendre l’installation d’une mise à jour.  

- **Empêcher l’utilisateur de rechercher les mises à jour de Windows**  
  **Valeur Par défaut** : Autoriser  
  CSP Windows Update : [Update/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **Autoriser** : autoriser les utilisateurs d’appareils à utiliser Windows Update analyser pour rechercher et télécharger des mises à jour, et installer des fonctionnalités.
  - **Bloquer** : empêche les utilisateurs de l’appareil d’accéder à l’analyse Windows Update, de télécharger des mises à jour et d’installer des fonctionnalités.  

- **Exiger l’approbation de l’utilisateur pour redémarrer en dehors des heures de travail**  
  **Par défaut** : Non configuré  
  CSP Windows Update : [Update/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **Non configuré**  
  - **Requis** : pour exiger qu’un utilisateur approuve un redémarrage de l’appareil en dehors des heures de travail.  
   
- **Adresser un rappel pouvant être ignoré à l’utilisateur avant le redémarrage automatique requis (heures)**  
  **Par défaut** : 4  
  CSP Windows Update : [Update/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  Spécifiez combien de temps avant un redémarrage automatique adresser une notification pouvant être ignorée à l’utilisateur d’un appareil. Des valeurs de **2**, **4**, **8**, **12** ou **24** heures sont prises en charge.  
  
  Lorsque vous désactivez la valeur par défaut, ce paramètre *n’est pas configuré*.  

- **Adresser un rappel permanent à l’utilisateur avant le redémarrage automatique requis (minutes)**  
  **Par défaut** : 15  
  CSP Windows Update : [Update/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  Spécifiez combien de temps avant un redémarrage automatique adresser un avertissement ne pouvant pas être ignoré à l’utilisateur d’un appareil. Des valeurs de **15**, **30** ou **60** minutes sont prises en charge.  

  Lorsque vous désactivez la valeur par défaut, ce paramètre *n’est pas configuré*.  

- **Modifier le niveau de notification de mise à jour**  
  **Par défaut** : utiliser les notifications Windows Update par défaut  
  CSP Windows Update : [Update/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  Spécifiez le niveau de notifications Windows Update que voient les utilisateurs. Ce paramètre ne contrôle pas comment et quand les mises à jour sont téléchargées et installées.  

  Options prises en charge :
  - **Non configuré**
  - **Utiliser les notifications Windows Update par défaut**
  - **Désactiver toutes les notifications, à l’exception des avertissements de redémarrage**
  - **Désactiver toutes les notifications, y compris les avertissements de redémarrage**  

- **Utiliser les paramètres d’échéance**  
  **Par défaut** : Non configuré  
 
  Permet à l’utilisateur d’utiliser les paramètres d’échéance.  

  - **Non configuré**
  - **Autoriser**

  Lorsque cette valeur est définie sur *autoriser*, vous pouvez configurer les paramètres suivants pour les échéances :

  - **Échéance des mises à jour de fonctionnalités**  
    **Par défaut** : *non configuré*  
    CSP Windows Update : [Update/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    Spécifie le nombre de jours avant que les mises à jour de fonctionnalités soient installées automatiquement sur leurs appareils (2-30).

  - **Échéance des mises à jour qualité**  
    **Par défaut** : *non configuré*  
    CSP Windows Update : [Update/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    Spécifie le nombre de jours pendant lesquels un utilisateur peut installer automatiquement les mises à jour qualité sur leurs appareils (2-30).

  - **Période de grâce**  
    **Valeur par défaut**: *non configuré* Windows Update CSP : [Update/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    Spécifie un nombre minimal de jours après l’échéance jusqu’à ce que les redémarrages se produisent automatiquement (2-7).

  - **Redémarrage automatique avant l’échéance**  
    **Valeur par défaut**: Oui Windows Update CSP : [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    Spécifie si l’appareil doit redémarrer automatiquement avant l’échéance.
    - **Oui**
    - **Non**

### <a name="delivery-optimization-download-mode"></a>Mode de téléchargement de l’optimisation de la livraison  

L’optimisation de la distribution n’est plus configurée dans le cadre d’une boucle de mise à jour Windows 10 sous Mises à jour logicielles. L’optimisation de la distribution est maintenant définie via la configuration de l’appareil. Toutefois, les configurations précédentes restent disponibles dans la console. Vous pouvez supprimer ces configurations précédentes en les modifiant pour être *Non configurées*, mais elles ne peuvent pas être changées autrement. 

Pour éviter les conflits entre l’ancienne et la nouvelle stratégie, consultez [Passer des boucles de mise à jour à l’optimisation de la distribution](../configuration/delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization), puis déplacez vos paramètres vers un profil d’optimisation de la distribution.
