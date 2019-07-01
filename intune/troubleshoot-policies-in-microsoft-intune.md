---
title: Résoudre les problèmes de stratégie dans Microsoft Intune - Azure | Microsoft Docs
description: Apprenez à utiliser la fonctionnalité de résolution des problèmes intégrée et découvrez les problèmes courants et la façon de les résoudre quand vous utilisez des stratégies de conformité et des profils de configuration dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9314617640d0bfd7f3a7b0cd0ba572e99ede53f9
ms.sourcegitcommit: cd451ac487c7ace18ac9722a28b9facfba41f6d3
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298396"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Résoudre les problèmes de stratégies et de profils dans Intune

Microsoft Intune propose des fonctionnalités de résolution des problèmes intégrée. Celles-ci permettent de résoudre les problèmes liés aux stratégies de conformité et aux profils de configuration dans votre environnement.

Cet article présente certaines techniques de dépannage courantes et décrit certains problèmes que vous êtes susceptible de rencontrer.

## <a name="check-tenant-status"></a>Vérification du statut de client
Vérifier le [état du locataire](tenant-status.md) et confirmez l’abonnement est actif. Vous pouvez également afficher les détails pour les incidents actifs et conseils qui peuvent affecter votre déploiement de stratégie ou de profil.

## <a name="use-built-in-troubleshooting"></a>Utiliser la fonctionnalité de résolution des problèmes intégrée

1. Dans [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), sélectionnez **Résoudre les problèmes** :

    ![Dans Intune, accéder à Aide et support, puis sélectionner Résoudre les problèmes](./media/help-and-support-troubleshoot.png)

2. Choisissez **Sélectionner un utilisateur** > sélectionnez l’utilisateur qui rencontre un problème > **Sélectionner**.
3. Vérifiez que **Licence Intune** et **État du compte** présentent tous deux une coche verte :

    ![Dans Intune, sélectionner l’utilisateur et vérifier que Licence Intune et État du compte présentent une coche verte](./media/account-status-intune-license-show-green.png)

    **Liens utiles** :

    - [Affecter des licences aux utilisateurs pour qu’ils puissent inscrire des appareils](licenses-assign.md)
    - [Ajouter des utilisateurs à Intune](users-add.md)

4. Sous **Appareils**, recherchez l’appareil qui rencontre un problème. Examinez les différentes colonnes :

    - **Managé** : pour permettre à un appareil de recevoir des stratégies de conformité ou de configuration, cette propriété doit indiquer **GPM** ou **EAS/GPM**.

      - Si **Géré** n’est pas défini sur **MDM** ou **EAS/MDM**, l’appareil n’est pas inscrit. Il ne reçoit pas les stratégies de conformité ou de configuration tant qu’il n’est pas inscrit.

      - Les stratégies de protection des applications (gestion des applications mobiles) n’exigent pas l’inscription des appareils. Pour plus d’informations, consultez [Créer et affecter des stratégies de protection des applications](app-protection-policies.md).

    - **Type de jonction à Azure AD** : doit être défini sur **Espace de travail** ou **AzureAD**.
 
      - Si cette colonne indique **Non inscrit**, il y a peut-être un problème d’inscription. En règle générale, le fait de désinscrire et de réinscrire l’appareil suffit à résoudre cet état.

    - **Conforme Intune** : doit être défini sur **Oui**. Si la valeur **Non** est indiquée, il se peut qu’il existe un problème au niveau des stratégies de conformité, ou l’appareil ne se connecte pas au service Intune. Par exemple, l’appareil est peut-être éteint ou ne dispose pas de connexion réseau. L’appareil finit par devenir non conforme après 30 jours, vraisemblablement.

      Pour plus d’informations, consultez [Bien démarrer avec les stratégies de conformité des appareils](device-compliance-get-started.md).

    - **Conforme Azure AD** : doit être défini sur **Oui**. Si la valeur **Non** est indiquée, il se peut qu’il existe un problème au niveau des stratégies de conformité, ou l’appareil ne se connecte pas au service Intune. Par exemple, l’appareil est peut-être éteint ou ne dispose pas de connexion réseau. L’appareil finit par devenir non conforme après 30 jours, vraisemblablement.

      Pour plus d’informations, consultez [Bien démarrer avec les stratégies de conformité des appareils](device-compliance-get-started.md).

    - **Dernier archivage** : doit indiquer une date et une heure récentes. Par défaut, les appareils Intune sont archivés toutes les 8 heures.

      - Si le **Dernier archivage** remonte à plus de 24 heures, l’appareil a peut-être un problème. Un appareil qui ne peut pas s’archiver ne peut pas recevoir vos stratégies d’Intune.

      - Pour forcer l’archivage :
        - Sur l’appareil Android, ouvrez l’application Portail d’entreprise Intune > **Appareils** > Choisissez l’appareil à partir dans la liste > **Vérifier les paramètres de l’appareil**.
        - Sur l’appareil iOS, ouvrez l’application Portail d’entreprise Intune > **Appareils** > Choisissez l’appareil dans la liste > **Vérifier les paramètres**. 
        - Sur un appareil Windows, ouvrez **Paramètres** > **Comptes** > **Accès Professionnel ou Scolaire** > Sélectionnez le compte ou l’inscription MDM > **Informations** > **Synchronisation**.

    - Sélectionnez l’appareil pour afficher les informations propres à la stratégie.

      **Conformité de l’appareil** présente les différents états des stratégies de conformité affectées à l’appareil.

      **Configuration de l’appareil** présente les différents états des stratégies de configuration affectées à l’appareil.

      Si les stratégies attendues ne figurent pas sous **Conformité de l’appareil** ou **Configuration de l’appareil**, les stratégies ne sont pas correctement ciblées. Ouvrez la stratégie et affectez-la stratégie à l’utilisateur ou à l’appareil en question.

      **États de stratégie** :

      - **Non applicable** : cette stratégie n’est pas prise en charge sur cette plateforme. Par exemple, les stratégies iOS ne fonctionnent pas sur Android. Les stratégies Samsung Knox ne fonctionnent pas sur les appareils Windows.
      - **Conflit** : un paramètre existant sur l’appareil ne peut pas être remplacé par Intune. Ou bien, vous avez déployé deux stratégies qui ont un même paramètre mais avec des valeurs différentes.
      - **En attente** : l’appareil n’a pas encore été enregistré dans Intune afin d’obtenir la stratégie. Ou bien, l’appareil a reçu la stratégie mais n’a pas communiqué l’état à Intune.
      - **Erreurs** : recherchez les erreurs et les résolutions possibles dans [Résoudre les problèmes d’accès aux ressources d’entreprise](troubleshoot-company-resource-access-problems.md).

      **Liens utiles** : 

      - [Déploiement des stratégies de conformité des appareils](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
      - [Surveiller les stratégies de conformité des appareils](compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>Vous ne savez pas avec certitude si une stratégie est correctement appliquée

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Sélectionnez **Appareils** > **Tous les appareils** > sélectionnez l’appareil > **Configuration de l’appareil**. 

    Chaque appareil liste ses profils. Chaque profil a un **État**. L’état s’applique quand tous les profils affectés, notamment les exigences et les restrictions en matière de système d’exploitation et de matériel, sont considérés ensemble. Les états possibles sont :

    - **Conforme** : l’appareil a reçu le profil et indique à Intune qu’il est conforme au paramètre.

    - **Non applicable** : le paramètre du profil n’est pas applicable. Par exemple, les paramètres de messagerie pour les appareils iOS ne s’appliquent pas à un appareil Android.

    - **En attente** : le profil est envoyé à l’appareil, mais l’état n’a pas été communiqué à Intune. Tel est le cas notamment du chiffrement sur Android, qui impose à l’utilisateur de l’activer et peut être en attente.

**Lien utile** : [Suivre les profils d’appareil dans Microsoft Intune](device-profile-monitor.md)

> [!NOTE]
> Quand deux stratégies avec différents niveaux de restriction s’appliquent au même appareil ou utilisateur, la stratégie la plus restrictive prévaut.

## <a name="policy-troubleshooting-resources"></a>Ressources de dépannage des stratégies

- [Résolution des problèmes iOS ou Android stratégies ne s’appliquent aux appareils](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154) (ouvre un autre site de Microsoft)
- [Résolution des problèmes de stratégie de Windows 10 Intune](http://configmgrdogsarchive.com/2018/08/09/troubleshooting-windows-10-intune-policy-failures/) (ouvre un blog)
- [Résoudre les problèmes de paramètres personnalisés de fournisseur de services cryptographiques pour Windows 10](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune) (ouvre un autre site de Microsoft)
- [Stratégie de groupe Windows 10 vs MDM Intune stratégie](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/) (ouvre un autre site de Microsoft)

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerte : L’enregistrement de règles d’accès dans Exchange a échoué

**Problème**: vous recevez l’alerte **L’enregistrement de règles d’accès dans Exchange a échoué** dans la console d’administration.

Si vous créez des stratégies dans l’espace de travail Stratégie Exchange sur site (console d’administration), mais que vous utilisez Office 365, les paramètres de stratégie configurés ne sont pas appliqués par Intune. Notez la source de la stratégie indiquée dans l’alerte. Sous l’espace de travail Stratégie Exchange sur site, supprimez les règles existantes. Les règles existantes sont les règles Exchange globales dans Intune pour Exchange sur site et ne concernent pas Office 365. Par conséquent, créez une stratégie pour Office 365.

La ressource [Résoudre les problèmes liés au connecteur Exchange local Intune](troubleshoot-exchange-connector.md) peut vous être utile.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>Impossible de modifier les stratégies de sécurité pour les appareils inscrits

Les appareils Windows Phone n’autorisent pas l’assouplissement des stratégies de sécurité définies par MDM ou EAS a posteriori. Par exemple, si vous définissez **Nombre minimal de caractères des mots de passe** sur 8, vous ne pouvez plus le réduire à 4. La stratégie la plus restrictive est appliquée à l’appareil.

Appareils Windows 10 ne peuvent pas supprimer les stratégies de sécurité lorsque vous dissociez la stratégie (arrêter le déploiement). Vous devrez peut-être laisser la stratégie affectée et modifiez les paramètres de sécurité les valeurs par défaut.

Selon la plateforme de l’appareil, si vous voulez attribuer à la stratégie une valeur moins sûre, vous devrez peut-être réinitialiser les stratégies de sécurité.

Par exemple, dans Windows 8.1, sur le Bureau, balayez à partir de la droite pour ouvrir la barre **Icônes**. Choisissez **Paramètres** > **Panneau de configuration** > **Comptes d’utilisateurs**. Sur la gauche, cliquez sur le lien **Réinitialiser les stratégies de sécurité**, puis choisissez **Réinitialiser les stratégies**.

Pour pouvoir appliquer une stratégie moins restrictive sur d’autres plateformes, comme Android, iOS et Windows Phone 8.1, vous devez peut-être les mettre hors service, puis les réinscrire.

La ressource [Résoudre les problèmes d’inscription d’appareils](troubleshoot-device-enrollment-in-intune.md) peut vous être utile.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>PC utilisant le client logiciel Intune - portail Classic

> [!NOTE]
> Cette section s’applique au portail Classic. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Erreurs liées aux stratégies Microsoft Intune dans policyplatform.log

Pour les appareils Windows gérés avec le client logiciel Intune, les erreurs de stratégie dans le fichier `policyplatform.log` peuvent être dues à des paramètres définis sur des valeurs autres que les valeurs par défaut dans le Contrôle de compte d’utilisateur Windows sur l’appareil. Certains paramètres de Contrôle de compte d’utilisateur autres que les paramètres par défaut peuvent affecter les installations du client Microsoft Intune et l’exécution des stratégies.

#### <a name="resolve-uac-issues"></a>Résoudre les problèmes liés au Contrôle de compte d’utilisateur

1. Mettre l’ordinateur hors service. Voir [Supprimer des appareils](devices-wipe.md).

2. Attendez 20 minutes que le logiciel client soit supprimé.

    > [!NOTE]
    > N’essayez pas de supprimer le client à partir de Programmes et de Fonctionnalités.

3. Dans le menu Démarrer, tapez **UAC** pour ouvrir les paramètres de Contrôle de compte d’utilisateur.

4. Déplacez le curseur de notification sur le paramètre par défaut.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>Erreur : Impossible d’obtenir la valeur de l’ordinateur, 0x80041013

Cela se produit si l’heure sur le système local présente un écart de synchronisation d’au moins cinq minutes. Si l’heure n’est pas synchronisée sur l’ordinateur local, les transactions sécurisées échouent, car les horodatages ne sont pas valides.

Pour résoudre ce problème, définissez sur le système local une heure la plus proche possible de l’heure Internet. Ou bien, affectez-lui l’heure des contrôleurs de domaine du réseau.


## <a name="next-steps"></a>Étapes suivantes

[Problèmes courants avec les profils de messagerie et résolutions](troubleshoot-email-profiles-in-microsoft-intune.md)

Obtenir [l’aide de Microsoft](get-support.md) ou utiliser les [forums des communautés](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
