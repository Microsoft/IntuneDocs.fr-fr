---
title: Résoudre les problèmes de stratégie dans Microsoft Intune - Azure | Microsoft Docs
description: Problèmes courants et résolutions lors de l’utilisation de stratégies dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: bb55ddc283ce4633b5057d5b96ae2ed6973dcf8a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181766"
---
# <a name="troubleshoot-policies-in-intune"></a>Résoudre les problèmes de stratégie dans Intune

Si vous rencontrez des problèmes de déploiement et de gestion des stratégies Intune, lisez ce qui suit. Cet article décrit certains problèmes courants que vous pouvez rencontrer et les solutions possibles.

## <a name="general-issues"></a>Problèmes généraux

### <a name="was-a-deployed-policy-applied-to-the-device"></a>Une stratégie déployée a-t-elle été appliquée à l’appareil ?
**Problème :** vous ne savez pas si une stratégie est correctement appliquée.

Dans Intune > **Appareils** > **Tous les appareils** > Sélectionner l’appareil > **configuration de l’appareil**, chaque appareil répertorie ses stratégies. Chaque stratégie a un **état**. L’état est ce que vous appliquez quand toutes les stratégies qui s’appliquent à l’appareil, notamment les restrictions et la configuration requise du matériel et du système d’exploitation, sont regroupées. Les états possibles sont :

- **Conforme** : l’appareil a reçu la stratégie et indique au service qu’il est conforme au paramètre.

- **Non applicable** : le paramètre de stratégie n’est pas applicable. Par exemple, les paramètres de messagerie pour appareils iOS ne peuvent pas s’appliquer à un appareil Android.

- **En attente** : la stratégie a été envoyée à l’appareil, mais l’état n’a pas été communiqué au service. Tel est le cas notamment du chiffrement sur Android, qui impose à l’utilisateur de l’activer et peut être en attente.

> [!NOTE]
> Quand deux stratégies avec différents niveaux de restriction s’appliquent au même appareil ou utilisateur, la stratégie la plus restrictive prévaut.

## <a name="issues-with-enrolled-devices"></a>Problèmes liés aux appareils inscrits

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerte : L’enregistrement de règles d’accès dans Exchange a échoué
**Problème**: vous recevez l’alerte **L’enregistrement de règles d’accès dans Exchange a échoué** dans la console d’administration.

Si vous avez créé des stratégies dans l’espace de travail Stratégie Exchange sur site de la Console d’administration, mais que vous utilisez O365, les paramètres de stratégie configurés ne sont pas appliqués par Intune. Notez la source de la stratégie indiquée dans l’alerte.  Sous l’espace de travail stratégie Exchange sur site, supprimez les règles existantes. Les règles héritées sont les règles Exchange globales dans Intune pour Exchange sur site et ne sont pas pertinentes pour Office 365. Créez ensuite une stratégie pour O365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>Impossible de modifier la stratégie de sécurité pour différents appareils inscrits
Les appareils Windows Phone n’autorisent pas à assouplir les stratégies de sécurité définies via GPM ou EAS a posteriori. Tel est le cas, par exemple, si vous fixez le **nombre minimal de caractères des mots de passe** à 8, puis que vous essayez de le réduire à 4. La stratégie la plus restrictive a déjà été appliquée à l’appareil.

Selon la plateforme d’appareil, si vous voulez attribuer à la stratégie une valeur moins sûre, vous devrez peut-être réinitialiser les stratégies de sécurité.

Par exemple, dans Windows, sur le Bureau, balayez à partir de la droite pour ouvrir la barre **Icônes**. Choisissez **Paramètres** > **Panneau de configuration**, puis sélectionnez **Comptes d’utilisateur**. Sur la gauche, cliquez sur le lien **Réinitialiser les stratégies de sécurité**, puis choisissez **Réinitialiser les stratégies**.

Pour pouvoir appliquer une stratégie moins restrictive sur les autres appareils GPM (Android, Windows Phone 8.1 et versions ultérieures, et iOS), vous devez peut-être les mettre hors service, puis les réinscrire dans le service.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Problèmes liés aux ordinateurs qui exécutent le client logiciel Intune

S’applique au portail Classic.

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Erreurs liées aux stratégies Microsoft Intune dans policyplatform.log
Pour les appareils Windows gérés avec le client logiciel Intune, les erreurs de stratégie dans le fichier policyplatform.log peuvent être dues à des paramètres définis sur des valeurs autres que les valeurs par défaut dans le Contrôle de compte d’utilisateur Windows sur l’appareil. Certains paramètres de Contrôle de compte d’utilisateur autres que les paramètres par défaut peuvent affecter les installations du client Microsoft Intune et l’exécution des stratégies.

#### <a name="resolve-uac-issues"></a>Résoudre les problèmes liés au Contrôle de compte d’utilisateur

1. Mettre l’ordinateur hors service. Voir [Supprimer des appareils](devices-wipe.md).

2. Attendez 20 minutes que le logiciel client soit supprimé.

    > [!NOTE]
    > N’essayez pas de supprimer le client à partir de Programmes et de Fonctionnalités.

3. Dans le menu Démarrer, tapez **UAC** pour ouvrir les paramètres de Contrôle de compte d’utilisateur.

4. Déplacez le curseur de notification sur le paramètre par défaut.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>Erreur : Impossible d’obtenir la valeur de l’ordinateur, 0x80041013
Cela se produit si l’heure sur le système local présente un écart de synchronisation d’au moins cinq minutes. Si l’heure sur l’ordinateur local n’est pas synchronisée, les transactions sécurisées échouent car que les horodatages ne sont pas valides.

Pour résoudre ce problème, réglez l’heure du système local le plus proche possible de l’heure Internet ou à l’heure définie sur les contrôleurs de domaine du réseau.

### <a name="next-steps"></a>Étapes suivantes
Si ces informations de dépannage n’ont pas permis de vous aider, contactez le support Microsoft comme décrit dans [Bénéficier d’un support technique pour Microsoft Intune](get-support.md).
