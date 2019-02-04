---
title: Vérifier la réussite ou l’échec des bases de référence de la sécurité dans Microsoft Intune - Azure | Microsoft Docs
description: Vérifiez les états d’erreur, de conflit et de réussite quand vous déployez des bases de référence de la sécurité vers des utilisateurs et appareils dans Microsoft Intune MDM. Découvrez comment résoudre les problèmes à l’aide des journaux clients et des fonctionnalités de rapport dans Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 28a98a20e5f0b5181628da46ccd662f1f8f503dd
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55070213"
---
# <a name="monitor-the-security-baseline-and-profile-in-microsoft-intune"></a>Superviser la base de référence de la sécurité et le profil dans Microsoft Intune

Il existe différentes options de supervision avec les bases de référence de la sécurité. Vous pouvez superviser le profil des bases de référence de la sécurité qui s’applique à vos utilisateurs et appareils. Vous pouvez également superviser la base de référence réelle et tous les appareils qui correspondent (ou non) aux valeurs recommandées.

Cet article décrit progressivement ces deux options de supervision.

[Bases de référence de la sécurité dans Intune](security-baselines.md) fournit plus d’informations sur la fonctionnalité des bases de référence de la sécurité dans Microsoft Intune.

## <a name="monitor-the-baseline-and-your-devices"></a>Superviser la base de référence et vos appareils

Quand vous supervisez la base de référence, vous obtenez un aperçu de l’état de sécurité de vos appareils selon les recommandations de Microsoft.

> [!NOTE]
> Une fois que vous avez assigné une base de référence, les rapports peuvent prendre jusqu’à 24 heures pour se mettre à jour. Passé ce délai, ils peuvent prendre jusqu’à 6 heures pour se mettre à jour.

1. Dans le [portail Azure](https://portal.azure.com/), sélectionnez **Tous les services**, filtrez sur **Intune** et sélectionnez **Intune**.
2. Sélectionnez **Bases de référence de la sécurité (préversion)** > sélectionnez une base de référence.
3. Dans **Vue d’ensemble**, le graphe montre le nombre d’appareils impactés par la base de référence que vous avez choisie, ainsi que les différents états :

    ![Vérifier l’état des appareils](./media/security-baselines-monitor/overview.png)

    Les états suivants sont disponibles :

    - **Correspond à la base de référence** : Tous les paramètres de la base de référence correspondent aux paramètres recommandés.
    - **Ne correspond pas à la base de référence** : Au moins un paramètre de la base de référence ne correspond pas aux paramètres recommandés.
    - **Mal configuré** : Au moins un paramètre n’est pas correctement configuré. Cet état signifie que le paramètre se trouve dans un état de conflit, d’erreur ou d’attente.
    - **Non applicable** : Au moins un paramètre n’est pas applicable et n’est pas appliqué.

4. Sélectionnez l’un des états qui dispose d’appareils. Par exemple, sélectionnez l’état **Mal configuré**.

5. La liste de tous les appareils dans cet état s’affiche. Sélectionnez un appareil pour obtenir plus d’informations. 

    Dans l’exemple suivant, sélectionnez **Configuration de l’appareil** > sélectionnez le profil avec un état d’erreur :

    ![Vérifier l’état des appareils](./media/security-baselines-monitor/device-configuration-profile-list.png)

    Sélectionnez le profil d’erreur. La liste de tous les paramètres du profil et leur état s’affiche. Maintenant, vous pouvez faire défiler la liste pour trouver le paramètre à l’origine de l’erreur :

    ![Voir le paramètre à l’origine de l’erreur](./media/security-baselines-monitor/profile-with-error-status.png)

Utilisez ce compte-rendu pour voir tous les paramètres du profil qui sont à l’origine d’un problème. Obtenez aussi plus d’informations sur les stratégies et profils déployés sur les appareils.

> [!NOTE]
> Quand une propriété a la valeur **Non configuré** dans la base de référence, le paramètre est ignoré et aucune restriction n’est appliquée. La propriété ne figure dans aucun compte-rendu.

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
