---
title: Mettre à jour les fonctionnalités Windows BIOS à l’aide de stratégies MDM dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez un profil DFCI (interface de configuration du microprogramme de l’appareil) pour gérer les paramètres UEFI, tels que le processeur, le matériel intégré et les options de démarrage sur les appareils Windows 10 dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d07066bcd599dc0cdbaf8fcf90ac1ee76be45fa
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206684"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>Utiliser les profils d’interface de configuration du microprogramme des appareils Windows dans Microsoft Intune (préversion publique)



Quand vous utilisez Intune pour gérer des appareils Autopilot, vous pouvez gérer les paramètres UEFI (BIOS) une fois qu’ils sont inscrits, à l’aide de l’interface DFCI (interface de configuration du microprogramme de l’appareil). Pour une vue d’ensemble des avantages, des scénarios et des prérequis, consultez [Vue d’ensemble de l’interface DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/).

L’interface DFCI [permet à Windows](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) de transmettre des commandes de gestion d’Intune à l’interface UEFI (Unified Extensible Firmware Interface).

Dans Intune, utilisez cette fonctionnalité pour contrôler les paramètres BIOS. En règle générale, le microprogramme est plus résilient aux attaques malveillantes. Il limite le contrôle des utilisateurs finaux sur le BIOS, ce qui est parfait dans une situation compromise.

Supposons, par exemple, que vous utilisez des appareils Windows 10 dans un environnement sécurisé et que vous souhaitez désactiver la caméra. Vous pouvez désactiver la caméra au niveau de la couche du microprogramme, de sorte que les actions de l’utilisateur final soient sans effet. La réinstallation du système d’exploitation ou la réinitialisation de l’ordinateur ne réactive pas l’appareil photo. Dans un autre exemple, verrouillez les options de démarrage pour empêcher les utilisateurs de démarrer un autre système d’exploitation ou une version antérieure de Windows qui ne dispose pas des mêmes fonctionnalités de sécurité.

Lorsque vous réinstallez une ancienne version de Windows, installez un autre système d’exploitation ou formatez le disque dur, vous ne pouvez pas remplacer la gestion DFCI. Cette fonctionnalité peut empêcher les logiciels malveillants de communiquer avec les processus du système d’exploitation, y compris les processus OS élevés. La chaîne d’approbation de l’interface DFCI utilise le chiffrement à clé publique et ne dépend pas de la sécurité de mot de passe UEFI (BIOS) locale. Cette couche de sécurité empêche les utilisateurs locaux d’accéder aux paramètres gérés à partir des menus UEFI (BIOS) de l’appareil.

Cette fonctionnalité s’applique à :

- Windows 10 RS5 (1809) et versions ultérieures sur l’interface UEFI prise en charge

## <a name="before-you-begin"></a>Avant de commencer

- Le fabricant de l’appareil doit avoir ajouté l’interface DFCI à son microprogramme UEFI dans le processus de fabrication, ou en tant que mise à jour du microprogramme à installer. Collaborez avec vos fournisseurs d’appareils pour déterminer les [fabricants qui prennent en charge l’interface DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci) ou la version du microprogramme nécessaire pour utiliser DFCI.

- L’appareil doit être inscrit pour Windows Autopilot par un [partenaire fournisseur de solutions Microsoft Cloud (CSP)](https://partner.microsoft.com/cloud-solution-provider), ou inscrit directement par l’OEM. 

  Les appareils inscrits manuellement pour Autopilot, comme ceux [importés à partir d’un fichier CSV](../enrollment/enrollment-autopilot.md#add-devices), ne sont pas autorisés à utiliser DFCI. De par sa conception, la gestion DFCI requiert une attestation externe de l’acquisition commerciale de l’appareil par le biais d’un fabricant d’ordinateurs OEM ou via l’inscription à Windows Autopilot par un partenaire Microsoft CSP.

  Une fois votre appareil inscrit, son numéro de série est affiché dans la liste des appareils Windows Autopilot.

  Pour plus d’informations sur Autopilot, y compris les exigences qui s’y rapportent, consultez [Inscrire des appareils Windows dans Intune avec Windows Autopilot](../enrollment/enrollment-autopilot.md).

## <a name="create-your-azure-ad-security-groups"></a>Créer vos groupes de sécurité Azure AD

Les profils de déploiement Autopilot sont attribués aux groupes de sécurité Azure AD. Veillez à créer des groupes qui incluent vos appareils pris en charge par DFCI. Pour les appareils DFCI, la plupart des organisations peuvent créer des groupes d’appareils à la place de groupes d’utilisateurs. Tenez compte des scénarios suivants :

- Le département des ressources humaines (RH) possède différents appareils Windows. Pour des raisons de sécurité, vous voulez qu’aucun utilisateur de ce groupe n’utilise l’appareil photo sur ces appareils. Dans ce scénario, vous pouvez créer un groupe d’utilisateurs de sécurité RH afin que la stratégie s’applique aux utilisateurs du groupe RH, quel que soit le type d’appareil.
- Dans l’atelier de fabrication, vous avez 10 appareils. Vous voulez empêcher le démarrage de tous ces appareils à partir d’un périphérique USB. Dans ce scénario, vous pouvez créer un groupe d’appareils de sécurité et ajouter les 10 appareils dans ce groupe.

Pour plus d’informations sur la création de groupes dans Intune, consultez [Ajouter des groupes pour organiser des utilisateurs et des appareils](../fundamentals/groups-add.md).

## <a name="create-the-profiles"></a>Créer les profils

Pour utiliser DFCI, créez les profils suivants et affectez-les à votre groupe.

### <a name="create-an-autopilot-deployment-profile"></a>Créer un profil de déploiement Autopilot

Ce profil installe et préconfigure les nouveaux appareils. Le [profil de déploiement Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) répertorie les étapes de création du profil.

### <a name="create-an-enrollment-state-page-profile"></a>Créer un profil de page d’état d’inscription

Ce profil garantit que les appareils sont vérifiés et activés pour DFCI lors de l’installation de Windows. Il est fortement recommandé d’utiliser ce profil pour bloquer l’utilisation des appareils jusqu’à ce que toutes les applications et tous les profils soient installés. Le [profil de page d’état d’inscription](../enrollment/windows-enrollment-status.md) répertorie les étapes de création du profil.

### <a name="create-the-dfci-profile"></a>Créer le profil DFCI

Ce profil inclut les paramètres DFCI que vous configurez.

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Entrez un nom descriptif pour le profil. Nommez vos stratégies afin de pouvoir les identifier facilement ultérieurement. Par exemple, un nom de profil correct est **Windows : Configurer les paramètres DFCI sur les appareils Windows**.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez **Windows 10 et ultérieur**.
    - **Type de profil** : Sélectionnez **Interface de configuration du microprogramme d’appareil**.

4. Configurez les paramètres :

    - **Autoriser l’utilisateur local à modifier les paramètres UEFI (BIOS)**  : Les options disponibles sont les suivantes :
      - **Uniquement les paramètres non configurés** : L’utilisateur local peut modifier n’importe quel paramètre *sauf* les paramètres explicitement définis par Intune sur **Activer** ou **Désactiver**.
      - **Aucune** : L’utilisateur local ne peut modifier aucun paramètre UEFI (BIOS), pas même les paramètres qui n’apparaissent pas dans le profil DFCI.

    - **Virtualisation de l’UC et des E/S** : Les options disponibles sont les suivantes :
        - **Non configuré** : Intune ne touche pas cette fonctionnalité et conserve les paramètres en l’état.
        - **Activé** : Le BIOS active les fonctionnalités de virtualisation de l’UC et des E/S de la plateforme pour que le système d’exploitation les utilise. Il active les technologies Device Guard et de sécurité basée sur la virtualisation Windows.
        - **Désactiver** : Le BIOS désactive les fonctionnalités de virtualisation de l’UC et des E/S de la plateforme, et empêche leur utilisation.
    - **Appareils photo** : Les options disponibles sont les suivantes :
        - **Non configuré** : Intune ne touche pas cette fonctionnalité et conserve les paramètres en l’état.
        - **Activé** : Tous les appareils photo intégrés gérés directement par UEFI (BIOS) sont activés. Les périphériques, tels que les appareils photo USB, ne sont pas affectés.
        - **Disabled** : Tous les appareils photo intégrés gérés directement par UEFI (BIOS) sont désactivés. Les périphériques, tels que les appareils photo USB, ne sont pas affectés.
    - **Microphone et haut-parleurs** :  Les options disponibles sont les suivantes :
        - **Non configuré** : Intune ne touche pas cette fonctionnalité et conserve les paramètres en l’état.
        - **Activé** : Tous les microphones et haut-parleurs intégrés gérés directement par UEFI (BIOS) sont activés. Les périphériques, tels que les périphériques USB, ne sont pas affectés.
        - **Disabled** : Tous les microphones et haut-parleurs intégrés gérés directement par UEFI (BIOS) sont désactivés. Les périphériques, tels que les périphériques USB, ne sont pas affectés.
    - **Radios (Bluetooth, Wi-Fi, NFC, etc.)**  : Les options disponibles sont les suivantes :
        - **Non configuré** : Intune ne touche pas cette fonctionnalité et conserve les paramètres en l’état.
        - **Activé** : Toutes les radios intégrées gérées directement par UEFI (BIOS) sont activées. Les périphériques, tels que les périphériques USB, ne sont pas affectés.
        - **Disabled** : Toutes les radios intégrées gérées directement par UEFI (BIOS) sont désactivées. Les périphériques, tels que les périphériques USB, ne sont pas affectés.

        > [!WARNING]
        > Si vous désactivez le paramètre **Radios**, l’appareil requiert une connexion réseau câblée. Dans le cas contraire, l’appareil peut ne pas être gérable.

    - **Démarrer à partir d’un média externe (USB, SD)**  : Les options disponibles sont les suivantes :
        - **Non configuré** : Intune ne touche pas cette fonctionnalité et conserve les paramètres en l’état.
        - **Activé** : UEFI (BIOS) permet le démarrage à partir d’un stockage autre que sur disque dur.
        - **Disabled** : UEFI (BIOS) ne permet pas le démarrage à partir d’un stockage autre que sur disque dur.
    - **Démarrer à partir de cartes réseau** :  Les options disponibles sont les suivantes :
        - **Non configuré** : Intune ne touche pas cette fonctionnalité et conserve les paramètres en l’état.
        - **Activé** : UEFI (BIOS) permet le démarrage à partir d’interfaces réseau intégrées.
        - **Disabled** : UEFI (BIOS) ne permet pas le démarrage à partir d’interfaces réseau intégrées.

5. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications. Le profil est créé et apparaît dans la liste.

## <a name="assign-the-profiles-and-reboot"></a>Affecter les profils et redémarrer

Une fois que les profils ont été créés, ils sont [prêts à être affectés](../configuration/device-profile-assign.md). Veillez à affecter les profils à vos groupes de sécurité Azure AD qui incluent vos appareils DFCI.

Lorsque l’appareil exécute Windows Autopilot dans la page d’état d’inscription, DFCI peut forcer un redémarrage. Ce premier redémarrage inscrit UEFI dans Intune. 

Si vous souhaitez confirmer l’inscription de l’appareil, vous pouvez redémarrer l’appareil, mais ce n’est pas obligatoire. Utilisez les instructions du fabricant de l’appareil pour ouvrir le menu UEFI, puis confirmez la gestion d’UEFI.

La prochaine fois que l’appareil se synchronise avec Intune, Windows reçoit les paramètres DFCI. Redémarrez l’appareil. Ce troisième redémarrage est nécessaire pour permettre à l’UEFI de recevoir les paramètres DFCI de Windows.

## <a name="update-existing-dfci-settings"></a>Mettre à jour les paramètres DFCI

Vous pouvez modifier les paramètres DFCI configurés sur les appareils en cours d’utilisation, si vous le souhaitez. Dans votre profil DFCI, modifiez les paramètres et enregistrez vos modifications. Comme le profil est déjà attribué, les nouveaux paramètres DFCI prennent effet lorsque :

1. L’appareil s’enregistre auprès du service Intune pour passer en revue les mises à jour de profil. Ces opérations interviennent à des moments différents. Pour plus d’informations, vérifiez [quand des appareils obtiennent une stratégie, un profil ou des mises à jour d’application](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

2. Pour appliquer les nouveaux paramètres, redémarrez l’appareil [à distance](../remote-actions/device-restart.md) ou localement.

Vous pouvez également [signaler aux appareils de s’enregistrer](../remote-actions/device-sync.md). Après une synchronisation réussie, [signalez-leur de redémarrer](../remote-actions/device-restart.md).

>[!NOTE]
> La suppression du profil DFCI ou la suppression d’un appareil du groupe attribué au profil n’entraîne pas la suppression des paramètres DFCI ni la réactivation des menus UEFI (BIOS). Si vous souhaitez cesser d’utiliser DFCI, mettez à jour votre profil DFCI existant. Pour plus d’informations sur ces étapes, reportez-vous à la [mise hors service de l’appareil](#retire) dans cet article.

## <a name="reuse-retire-or-recover-the-device"></a>Réutiliser, mettre hors service ou récupérer l’appareil

### <a name="reuse"></a>Réutiliser

Si vous envisagez de réinitialiser Windows pour réaffecter l’appareil, [réinitialisez l’appareil](../remote-actions/devices-wipe.md). **Ne supprimez pas** l’enregistrement de l’appareil Autopilot.

Après avoir réinitialisé l’appareil, placez-le dans le groupe auquel les nouveaux profils DFCI et Autopilot sont affectés. Veillez à redémarrer l’appareil pour réexécuter le programme d’installation de Windows.

### <a name="retire"></a>Mettre hors service

Lorsque vous êtes prêt à mettre hors service l’appareil et à abandonner sa gestion, mettez à jour le profil DFCI avec les paramètres UEFI (BIOS) que vous souhaitez à l’état de sortie. En règle générale, tous les paramètres doivent être activés. Par exemple :

1. Ouvrez votre profil DFCI (**Appareils** > **Profils de configuration**).
2. Modifiez le paramètre **Autoriser l’utilisateur local à modifier les paramètres UEFI (BIOS)** en spécifiant **Uniquement les paramètres non configurés**.
3. Définissez tous les autres paramètres sur **Non configuré**.
4. Enregistrez vos paramètres.

Ces étapes déverrouillent les menus UEFI (BIOS) de l’appareil. Les valeurs restent les mêmes que celles du profil (**activées** ou **désactivées**) et ne sont pas redéfinies sur les valeurs par défaut du système d’exploitation.

Vous êtes maintenant prêt à réinitialiser l’appareil. Une fois l’appareil réinitialisé, supprimez l’enregistrement Autopilot. La suppression de cet enregistrement empêche l’appareil de se réinscrire automatiquement lorsqu’il redémarre.

### <a name="recover"></a>Récupérer

Si vous réinitialisez un appareil et supprimez l’enregistrement Autopilot avant de déverrouiller les menus UEFI (BIOS), ces menus restent verrouillés. Intune ne peut pas envoyer les mises à jour de profil pour les déverrouiller.

Pour déverrouiller l’appareil, ouvrez le menu UEFI (BIOS), puis actualisez la gestion à partir du réseau. La récupération déverrouille les menus, mais conserve tous les paramètres UEFI (BIOS) tels qu’ils étaient définis sur les valeurs du profil DFCI Intune précédent.

## <a name="end-user-impact"></a>Impact sur les utilisateurs finaux

Lorsque la stratégie DFCI est appliquée, les utilisateurs locaux ne peuvent pas modifier les paramètres configurés par DFCI, même si le menu UEFI (BIOS) est protégé par mot de passe. Selon les paramètres que vous configurez, les utilisateurs finaux peuvent recevoir des erreurs signalant que les composants matériels sont introuvables ou ne peuvent pas être diagnostiqués. Veillez à fournir aux utilisateurs finaux de la documentation expliquant les options que vous avez désactivées.  

## <a name="next-steps"></a>Étapes suivantes

Une fois le profil affecté, [supervisez son état](../device-profile-monitor.md).
