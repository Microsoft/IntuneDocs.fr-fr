---
title: Configurer une page d’état d’inscription
titleSuffix: Microsoft Intune
description: Configurez une page d’accueil pour les utilisateurs qui inscrivent des appareils Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: f01009a0cb35f4270bdb1e768ee781172c8bfa2f
ms.sourcegitcommit: 17f58d35a6bdff3e179662f3731fc74d39144470
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55105185"
---
# <a name="set-up-an-enrollment-status-page"></a>Configurer une page d’état d’inscription
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Durant la configuration de l’appareil à l’aide d’Intune, la page État d’inscription affiche des informations relatives à l’installation sur l’appareil. Il est possible que des applications, profils et certificats ne soient pas installés avant qu’un utilisateur effectue l’inscription automatisée et se connecte à l’appareil. Une page d’état d’inscription peut aider les utilisateurs à comprendre l’état de leur appareil pendant la configuration de ce dernier. Vous pouvez créer plusieurs profils de page d’état d’inscription et les appliquer à différents groupes. Vous pouvez définir des profils pour :
- Afficher la progression de l’installation.
- Bloquer l’utilisation jusqu’à ce que l’installation soit terminée.
- Spécifier ce qu’un utilisateur peut faire si la configuration de l’appareil échoue.

Vous pouvez également définir l’ordre de priorité de chaque profil pour éviter que les profils affectés à un même utilisateur ou appareil n’entrent en conflit.

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Activer la page d’état d’inscription par défaut pour tous les utilisateurs

Pour activer la page d’état d’inscription, suivez les étapes ci-dessous.
 
1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription de l’appareil** > **Inscription Windows** > **Page d’état d’inscription (préversion)**.
2. Dans le panneau **Page d’état d’inscription**, choisissez **Par défaut** > **Paramètres**.
3. Pour **Afficher la progression de l’installation des profils et des applications**, choisissez **Oui**.
4. Choisissez les autres paramètres que vous voulez activer, puis choisissez **Enregistrer**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Créer un profil de page d’état d’inscription et l’affecter à un groupe

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription de l’appareil** > **Inscription Windows** > **Page d’état d’inscription (préversion)** > **Créer un profil**.
2. Indiquez un **Nom** et une **Description**.
3. Choisissez **Créer**.
4. Choisissez le nouveau profil dans la liste **Page d’état d’inscription**.
5. Choisissez **Affectations** > **Sélectionner des groupes** > choisissez les groupes qui doivent adopter ce profil > **Sélectionner** > **Enregistrer**.
6. Choisissez **Paramètres** > choisissez les paramètres à appliquer à ce profil > **Enregistrer**.

## <a name="set-the-enrollment-status-page-priority"></a>Définir la priorité d’une page d’état d’inscription

Un appareil ou un utilisateur peut se trouver dans plusieurs groupes et avoir plusieurs profils de page d’état d’inscription. Pour résoudre ces conflits, vous pouvez définir les priorités de chaque profil. Si quelqu’un a plusieurs profils de page d’état d’inscription, seul le profil ayant la priorité la plus élevée s’applique.

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription de l’appareil** > **Inscription Windows** > **Page d’état d’inscription (préversion)**.
2. Pointez sur le profil dans la liste.
3. À l’aide des trois points verticaux, faites glisser le profil à la position souhaitée dans la liste.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Bloquer l’accès à un appareil tant qu’une certaine application n’est pas installée

Vous pouvez spécifier quelles applications doivent être installés pour que l’utilisateur puisse accéder au bureau.

1. Dans Intune, choisissez **Inscription des appareils** > **Inscription Windows** > **Page d’état d’inscription (préversion)**.
2. Choisissez un profil > **Paramètres**.
3. Choisissez **Oui** pour **Afficher la progression de l’installation des profils et des applications**.
4. Choisissez **Oui** pour **Bloquer l’utilisation de l’appareil jusqu’à ce que toutes les applications et tous les profils soient installés**.
5. Choisissez **Sélectionnées** pour **Bloquer l’utilisation de l’appareil jusqu’à ce que ces applications requises soient installées si elles sont affectées à l’utilisateur/l’appareil**.
 6. Choisissez **Sélectionner des applications** > choisissez les applications > **Sélectionner** > **Enregistrer**.

## <a name="enrollment-status-page-tracking-information"></a>Informations de suivi de la page d’état d’inscription

La page d’état montre le suivi des informations de préparation de l’appareil, de configuration de l’appareil et de configuration du compte.

### <a name="device-preparation"></a>Préparation de l’appareil

Pour la préparation de l’appareil, la page d’état d’inscription montre le suivi des attestations de clé du Module de plateforme sécurisée (TPM) (le cas échéant), ainsi que la progression de la jonction à Azure Active Directory et de l’inscription dans Intune.

### <a name="device-setup"></a>Configuration de l’appareil

Pour la configuration de l’appareil, la page d’état d’inscription indique le suivi des éléments suivants, s’ils sont affectés à Tous les appareils :
- Stratégies de sécurité
    - Un fournisseur de services de configuration pour toutes les inscriptions.
    - Les fournisseurs de solutions Cloud réels configurés par Intune ne sont pas suivis ici.
- Applications
    - Applications MSI métier par machine.
    - Applications du Store métier avec contexte d’installation = Appareil.
    - Applications du Store métier et du Store hors connexion avec contexte d’installation = Appareil.
- Profils de connectivité
    - Profils Wi-Fi ou VPN qui sont affectés à **Tous les appareils** ou à un groupe d’appareils dont est membre l’appareil à inscrire, mais uniquement pour les appareils Autopilot
- Profils de certificat qui sont affectés à **Tous les appareils** ou à un groupe d’appareils dont est membre l’appareil à inscrire, mais uniquement pour les appareils Autopilot

### <a name="account-setup"></a>Configuration du compte
Pour la configuration du compte, la page d’état d’inscription montre le suivi des éléments suivants :
- Stratégies de sécurité
    - Un seul fournisseur de services de configuration pour toutes les inscriptions.
    - Les fournisseurs de solutions Cloud réels configurés par Intune ne sont pas suivis ici.
- Applications
    - Applications MSI métier par utilisateur qui sont affectées à Tous les appareils, à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.
    - Applications MSI métier par machine qui sont affectées à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.
    - Les applications de Store métier, les applications de Store en ligne et les applications de Store hors connexion sont affectées à l’un des éléments suivants :
        - Tous les appareils
        - Tous les utilisateurs
        - Groupe d’utilisateurs dans lequel l’utilisateur qui inscrit l’appareil est un membre dont le contexte d’installation est Utilisateur
- Profils de connectivité
    - Profils VPN ou Wi-Fi qui sont affectés à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.
- Certificats
    - Profils de certificat qui sont affectés à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.

## <a name="next-steps"></a>Étapes suivantes
Après avoir configuré les pages d’inscription Windows, découvrez comment gérer les appareils Windows. Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](https://docs.microsoft.com/intune/device-management)
