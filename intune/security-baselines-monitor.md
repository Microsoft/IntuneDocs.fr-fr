---
title: Vérifier la réussite ou l’échec des bases de référence de la sécurité dans Microsoft Intune - Azure | Microsoft Docs
description: Vérifiez les états d’erreur, de conflit et de réussite quand vous déployez des bases de référence de la sécurité vers des utilisateurs et appareils dans Microsoft Intune MDM. Découvrez comment résoudre les problèmes à l’aide des journaux clients et des fonctionnalités de rapport dans Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/19/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc82653355ae57830684270fc8f7b9f1f3ae2491
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61506986"
---
# <a name="monitor-security-baseline-and-profiles-in-microsoft-intune"></a>Superviser la base de référence de la sécurité et les profils dans Microsoft Intune  

Intune propose plusieurs options pour superviser vos bases de référence de la sécurité. Vous pouvez superviser le profil des bases de référence de la sécurité qui s’applique à vos utilisateurs et appareils. Vous pouvez également superviser la base de référence réelle et tous les appareils qui correspondent (ou non) aux valeurs recommandées.

Cet article décrit progressivement ces deux options de supervision.

[Bases de référence de la sécurité dans Intune](security-baselines.md) fournit plus d’informations sur la fonctionnalité des bases de référence de la sécurité dans Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Superviser la base de référence et vos appareils  

Quand vous supervisez une base de référence, vous obtenez un aperçu de l’état de sécurité de vos appareils selon les recommandations de Microsoft. Vous pouvez afficher ces informations à partir du volet Vue d’ensemble de la base de référence de la sécurité dans la console Intune.  L’affichage des données peut prendre jusqu’à 24 heures après l’affectation initiale d’une base de référence. L’affichage des modifications ultérieures prend jusqu’à six heures.  

Pour afficher les données de supervision de la base de référence et des appareils, connectez-vous au [portail Intune](https://aka.ms/intuneportal). Ensuite, sélectionnez **Bases de référence de la sécurité (préversion)** et sélectionnez une base de référence pour afficher le volet **Vue d’ensemble**.

Le volet **Vue d’ensemble** propose deux méthodes pour superviser l’état :
- **Vue de l’appareil** : synthèse du nombre d’appareils figurant dans chaque catégorie d’état pour la base de référence.  
- **Par catégorie** : vue qui montre chaque catégorie dans la base de référence et inclut le pourcentage d’appareils pour chaque groupe d’état pour chaque catégorie de base de référence. 

Chaque appareil est représenté par l’un des états suivants, qui sont utilisés à la fois dans la vue *appareil* et dans les vues *par catégorie* :  
- **Correspond à la base de référence** : tous les paramètres de la base de référence correspondent aux paramètres recommandés.
- **Ne correspond pas à la base de référence** : au moins un paramètre de la base de référence ne correspond pas aux paramètres recommandés.
- **Mal configuré** : au moins un paramètre n’est pas correctement configuré. Cet état signifie que le paramètre se trouve dans un état de conflit, d’erreur ou d’attente.
- **Non applicable** : au moins un paramètre n’est pas applicable et n’est pas appliqué.


### <a name="device-view"></a>Vue de l’appareil
Le volet Vue d’ensemble affiche une synthèse sous forme de graphique du nombre d’appareils ayant un état spécifique pour la base de référence ; **Position vis à vis de la base de référence pour les appareils Windows 10 attribués**.  

![Vérifier l’état des appareils](./media/security-baselines-monitor/overview.png)

Quand un appareil a un état différent dans différentes catégories dans la base de référence, il est représenté par un seul état. L’état qui représente l’appareil est déterminé d’après l’ordre de priorité suivant : **Mal configuré**, **Ne correspond pas à la base de référence**, **Non applicable**, **Correspond à la base de référence**.  

Par exemple, si un appareil a un paramètre classé comme *Mal configuré* et un ou plusieurs paramètres classés comme *Ne correspond pas à la base de référence*, il est classé comme *Mal configuré*.  

Vous pouvez cliquer sur le graphique pour voir les détails et afficher la liste des appareils avec différents états. Vous pouvez ensuite sélectionner un appareil dans cette liste pour en afficher les détails. Par exemple :
- Sélectionnez **Configuration de l’appareil** > sélectionnez le profil avec un état d’erreur :

  ![Vérifier l’état des appareils](./media/security-baselines-monitor/device-configuration-profile-list.png)

- Sélectionnez le profil d’erreur. La liste de tous les paramètres du profil et leur état s’affiche. Maintenant, vous pouvez faire défiler la liste pour trouver le paramètre à l’origine de l’erreur :

  ![Voir le paramètre à l’origine de l’erreur](./media/security-baselines-monitor/profile-with-error-status.png)

Utilisez ce compte-rendu pour voir tous les paramètres du profil qui sont à l’origine d’un problème. Obtenez aussi plus d’informations sur les stratégies et profils déployés sur les appareils.

> [!NOTE]
> Quand une propriété a la valeur **Non configuré** dans la base de référence, le paramètre est ignoré et aucune restriction n’est appliquée. La propriété ne figure dans aucun compte-rendu.

### <a name="per-category-view"></a>Vue par catégorie
Le volet Vue d’ensemble affiche un graphique par catégorie pour la base de référence ; **Position vis à vis de la base de référence par catégorie**.  Cette vue affiche chaque catégorie de la base de référence et identifie le pourcentage d’appareils appartenant à une classification d’état pour chacune de ces catégories. 
 
![Vue de l’état par catégorie](./media/security-baselines-monitor/monitor-baseline-per-category.png)

L’état de **Correspond à la base de référence** s’affiche seulement une fois que 100 % des appareils signalent cet état pour la catégorie.   

Vous pouvez trier l’affichage par catégorie en fonction de chaque colonne, en sélectionnant l’icône de flèche verticale en haut de la colonne.  


## <a name="monitor-the-profile"></a>Superviser le profil

La supervision du profil permet d’obtenir un aperçu de l’état du déploiement de vos appareils, mais pas de l’état de la sécurité conformément aux recommandations de la base de référence.

1. Dans Intune, sélectionnez **Bases de référence de la sécurité** > sélectionnez une base de référence > **Profils créés**.

2. Sélectionnez un profil. Dans **Vue d’ensemble**, l’image montre le nombre d’appareils et d’utilisateurs auxquels ce profil est assigné :

    ![Voir le nombre d’appareils et d’utilisateurs auxquels le profil des bases de référence de la sécurité est assigné](./media/security-baselines-monitor/existing-profile-overview.png)

3. Sous **Gérer** > **Propriétés** figure la liste de tous les paramètres de la base de référence. Vous pouvez également changer ces paramètres :

    ![Voir et mettre à jour les paramètres dans le profil des bases de référence de la sécurité](./media/security-baselines-monitor/manage-settings.png)

4. Dans **Surveiller**, vous pouvez voir l’état de déploiement du profil sur des appareils individuels, l’état de chaque utilisateur et l’état de chaque paramètre de la base de référence :

    ![Voir les différentes options de supervision disponibles pour un profil de base de référence de la sécurité](./media/security-baselines-monitor/monitor-status-options.png)

## <a name="troubleshoot-using-per-setting-status"></a>Résoudre les problèmes à l’aide de l’état par paramètre

Vous avez déployé une base de référence de la sécurité, mais l’état du déploiement indique une erreur. Les étapes suivantes vous guident dans la résolution de l’erreur.

1. Dans Intune, sélectionnez **Bases de référence de la sécurité** > sélectionnez une base de référence > **Profils créés**.
2. Sélectionnez un profil > sous **Surveiller** > **État par paramètre**.
3. Le tableau montre tous les paramètres et l’état de chacun d’eux. Sélectionnez la colonne **Erreur** ou la colonne **Conflit** pour voir le paramètre à l’origine de l’erreur.

### <a name="mdm-diagnostic-information"></a>Informations de diagnostic de la gestion des appareils mobiles

À présent, vous connaissez le paramètre qui pose problème. L’étape suivante consiste à déterminer pourquoi ce paramètre entraîne une erreur ou un conflit. 

Sur les appareils Windows 10, il existe un rapport d’informations de diagnostic de gestion des appareils mobiles intégré. Ce rapport inclut les valeurs par défaut, les valeurs actuelles, la stratégie, une indication de son déploiement ou non sur l’appareil ou l’utilisateur, etc. Utilisez-le pour déterminer pourquoi le paramètre entraîne un conflit ou une erreur.

1. Sur l’appareil, accédez à **Paramètres** > **Comptes** > **Accès Professionnel ou Scolaire**.
2. Sélectionnez le compte > **Informations** > **Rapport Diagnostics avancés** > **Créer un rapport**.
3. Choisissez **Exporter** et ouvrez le fichier généré.
4. Dans le rapport, recherchez le paramètre en état d’erreur ou de conflit dans les différentes sections.

  Par exemple, examinez la section **Sources de configuration et ressources cibles inscrites** ou la section **Stratégies non gérées**. Vous pourrez peut-être vous faire une idée de la raison pour laquelle il entraîne une erreur ou un conflit.

[Diagnostiquer les échecs de gestion des appareils mobiles dans Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) fournit plus d’informations sur ce rapport intégré.

> [!TIP]
> - Certains paramètres listent également le GUID. Vous pouvez rechercher ce GUID dans le Registre local (regedit) pour toutes les valeurs définies.
> - Les journaux de l’observateur d’événements peuvent également inclure des informations d’erreur sur le paramètre qui pose problème (**Observateur d’événements** > **Journaux des applications et des services** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider** > **Admin**).

## <a name="next-steps"></a>Étapes suivantes

[Supervisez des profils d’appareil](device-profile-monitor.md) et [découvrez certains problèmes courants et leurs solutions](device-profile-troubleshoot.md).
