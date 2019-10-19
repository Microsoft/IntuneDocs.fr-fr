---
title: Paramètres d’appareil personnalisés Windows 10 - Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez et utilisez Windows 10 pour configurer des appareils qui sont partagés, ou utilisés par plusieurs utilisateurs dans Microsoft Intune. Découvrez la liste de tous les paramètres et leur fonction sur les appareils, notamment Microsoft Surface. Contrôlez les comptes invités, gérez les comptes et supprimez les comptes inactifs, autorisez ou empêchez l’enregistrement dans le stockage local, définissez les options d’alimentation et de mise en veille, choisissez quand les mises à jour sont installées, et utilisez des appareils dans des environnements de formation dans un profil de configuration d’appareil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 588b6d39f1e3dc86f76279ef0446d9d58dc3e1df
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506624"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Paramètres Windows 10 et ultérieur pour gérer les appareils partagés à l’aide d’Intune

Les appareils Windows 10 et ultérieur, tels que Microsoft Surface, peuvent être utilisés par de nombreux utilisateurs. Les appareils ayant plusieurs utilisateurs sont appelés « appareils partagés » et font partie des solutions de gestion des appareils mobiles (MDM).

À l’aide de Microsoft Intune, les utilisateurs finaux peuvent se connecter à ces appareils partagés avec un compte invité. Quand ils utilisent l’appareil, ils peuvent uniquement accéder aux fonctionnalités que vous autorisez. En tant qu’administrateur Intune, vous configurez l’accès, choisissez quand les comptes sont supprimés, contrôlez les paramètres de gestion de l’alimentation, et bien plus encore pour vos appareils Windows 10 partagés.

Cet article liste et décrit les paramètres que vous utilisez dans un profil de configuration d’appareil Windows 10 (et ultérieur). Quand le profil est créé dans Intune, vous le déployez ou l’affectez à des groupes d’appareils de votre organisation. Vous pouvez également affecter ce profil à des groupes d’appareils contenant différentes combinaisons de types d’appareils et de versions de système d’exploitation.

Pour plus d’informations sur cette fonctionnalité dans Intune, consultez [Contrôler l’accès, les comptes et les fonctionnalités d’alimentation sur des PC partagés ou des appareils multi-utilisateurs](shared-user-device-settings.md). Pour plus d’informations sur le fournisseur de services de configuration Windows, consultez [Fournisseur de services de configuration SharedPC](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp).

## <a name="before-your-begin"></a>Avant de commencer

[Créez le profil](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>Paramètres d’appareils partagés multi-utilisateurs

- **Mode PC partagé** : choisissez **Activer** pour activer le mode PC partagé. Dans ce mode, un seul utilisateur à la fois se connecte à l’appareil. Aucun autre utilisateur ne peut se connecter tant que le premier ne s’est pas déconnecté. **Non configuré** (par défaut) laisse ce paramètre non géré par Intune et n’envoie pas de stratégie pour contrôler ce paramètre sur un appareil.
- **Compte invité** : choisissez cette option pour créer une option Invité sur l’écran de connexion. Les comptes invités ne nécessitent aucune information d’identification de l’utilisateur ou authentification. Ce paramètre crée un compte local chaque fois qu’il est utilisé. Les options disponibles sont les suivantes :
  - **Invité** : crée un compte invité localement sur l’appareil.
  - **Domaine** : crée un compte invité dans Azure Active Directory (AD).
  - **Invité et domaine** : crée un compte invité localement sur l’appareil et dans Azure Active Directory (AD).
- **Gestion du compte** : affectez la valeur **Activer** pour supprimer automatiquement les comptes locaux créés par des invités et les comptes dans AD et Azure Active Directory. Quand un utilisateur se déconnecte de l’appareil, ou lors de l’exécution de la maintenance du système, ces comptes sont supprimés. Quand cette option est activée, définissez également :
  - **Suppression du compte** : choisissez quand les comptes doivent être supprimés : **Au niveau du seuil d’espace de stockage**, **Au niveau du seuil d’espace de stockage et du seuil d’inactivité** ou **Immédiatement après la déconnexion**. Entrez également :
    - **Seuil de démarrage de suppression (%)**  : entrez un pourcentage (0-100) d’espace disque. Quand l’espace de stockage/disque total est inférieur à la valeur entrée, les comptes mis en cache sont supprimés. Les comptes sont supprimés de manière continue afin de récupérer l’espace disque. Les comptes inactifs depuis le plus longtemps sont supprimés en premier.
    - **Seuil d’arrêt de suppression (%)**  : entrez un pourcentage (0-100) d’espace disque. Quand l’espace de stockage/disque total atteint la valeur entrée, la suppression cesse.

  Affectez la valeur **Désactiver** pour conserver les comptes locaux, AD et Azure AD créés par des invités.

- **Stockage local** : choisissez **Activé** pour empêcher les utilisateurs d’enregistrer et d’afficher des fichiers sur le disque dur de l’appareil. Choisissez **Désactivé** pour permettre aux utilisateurs d’afficher et d’enregistrer les fichiers localement à l’aide de l’Explorateur de fichiers. **Non configuré** (par défaut) laisse ce paramètre non géré par Intune et n’envoie pas de stratégie pour contrôler ce paramètre sur un appareil.
- **Stratégies d’alimentation** : lorsque cette option a la valeur **Activé**, les utilisateurs ne peuvent pas désactiver la veille prolongée, remplacer toutes les actions de mise en veille (par exemple la fermeture du capot) et modifier les paramètres d’alimentation. Quand elle a la valeur **Désactivé**, les utilisateurs peuvent mettre l’appareil en veille prolongée, fermer le capot pour mettre l’appareil en veille et changer les paramètres d’alimentation. **Non configuré** (par défaut) laisse ce paramètre non géré par Intune et n’envoie pas de stratégie pour contrôler ce paramètre sur un appareil.
- **Délai d’attente avant la veille (en secondes)**  : entrez le nombre de secondes inactives (0-100) avant que l’appareil bascule en mode veille. Si vous ne définissez pas de délai, l’appareil se met en veille après 60 minutes.
- **Se connecter lorsque le PC sort du mode veille** : affectez la valeur **Activé** pour exiger que les utilisateurs se connectent avec un mot de passe lorsque l’appareil sort du mode veille. Choisissez **Désactivé** pour que les utilisateurs n’aient pas à entrer leur nom d’utilisateur et leur mot de passe. **Non configuré** (par défaut) laisse ce paramètre non géré par Intune et n’envoie pas de stratégie pour contrôler ce paramètre sur un appareil.
- **Heure de début de la maintenance (en minutes après minuit)**  : entrez l’heure en minutes (0-1440) à laquelle s’exécutent les tâches de maintenance automatique, telles que Windows Update. L’heure de début par défaut est minuit, soit zéro (`0`) minute. Pour la changer, entrez une heure de début en minutes à partir de minuit. Par exemple, si vous souhaitez que la maintenance commence à 2 heures du matin, entrez `120`. Si vous souhaitez que la maintenance commence à 20h00, entrez `1200`.
- **Stratégie d’éducation** : choisissez **Activé** afin d’utiliser les paramètres recommandés pour les appareils des établissements scolaires, qui sont plus restrictifs. Choisissez **Désactivé** pour ne pas utiliser les stratégies d’éducation par défaut et recommandées. **Non configuré** (par défaut) laisse ce paramètre non géré par Intune et n’envoie pas de stratégie pour contrôler ce paramètre sur un appareil.

  Pour plus d’informations sur ce que font les stratégies d’éducation, consultez [Recommandations de configuration de Windows 10 pour les clients de l’enseignement](https://docs.microsoft.com/education/windows/configure-windows-for-education).

> [!TIP]
> [Configurer un PC partagé ou invité](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc) (ouvre un autre site web Docs) est une ressource très intéressante de cette fonctionnalité Windows 10, qui comprend des concepts et des stratégies de groupe qui peuvent être définies en mode partagé.

## <a name="next-steps"></a>Étapes suivantes

- [Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
- Consultez les paramètres pour [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md).
