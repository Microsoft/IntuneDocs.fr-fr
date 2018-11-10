---
title: Abandon de l’inscription sur le portail d’entreprise dans Intune
titlesuffix: Microsoft Intune
description: Découvrez le rapport d’abandon du portail d’entreprise.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: ba1ee5a6811457b8c6e7343de7355261a2fcecdb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236748"
---
# <a name="company-portal-abandonment-report"></a>Rapport d’abandon du portail d’entreprise

Ce rapport vous indique où dans l’inscription sur l’application Portail d’entreprise les utilisateurs abandonnent le processus d’inscription.

Pour afficher le rapport, choisissez **Intune** > **Inscription de l’appareil** > **Abandon du portail d’entreprise**.

À l’aide de ces informations d’abandon, vous pouvez mettre à jour vos documents d’intégration pour aider les utilisateurs à effectuer l’inscription. Par exemple, si de nombreux utilisateurs quittent au niveau des Conditions d’utilisation, vous pouvez examiner cette partie et la rendre plus intuitive pour les utilisateurs.

## <a name="what-is-abandonment"></a>Présentation de l’abandon

L’abandon est caractérisé par l’une des opérations suivantes de la part d’un utilisateur :

-   Il choisit explicitement une action pour arrêter l’inscription
-   Il ferme le Portail d’entreprise pendant l’inscription
-   Il consacre plus de 30 minutes à une des sections de l’inscription avant de passer à la suivante

Si un utilisateur arrête l’inscription et la redémarre plusieurs fois, cela compte pour autant de tentatives et d’abandons. Si un utilisateur attend 30 minutes entre différents écrans d’inscription, cela est considéré comme plusieurs abandons.

## <a name="what-does-the-report-show"></a>Informations affichées par le rapport

Les rapports d’inscription incluent des données relatives aux appareils iOS et Android.

Les données des rapports couvrent les deux dernières semaines, mais vous pouvez filtrer le rapport pour afficher une période de 30 jours dans le passé.

Vous pouvez filtrer la plage de dates, le système d’exploitation et la section d’inscription en choisissant **Filtrer**.

### <a name="number-and-percentage-tiles"></a>Vignettes de nombre et de pourcentage

En haut du rapport, vous pouvez voir le nombre et le pourcentage de rapports abandonnés par rapport à toutes les inscriptions.

-   Inscriptions lancées : nombre d’inscriptions tentées.
-   Inscriptions abandonnées : nombre d’inscriptions tentées qui n’ont pas abouti à un appareil entièrement inscrit et conforme.
-   Taux d’abandon : pourcentage de tentatives d’inscription qui ont été abandonnées (Inscriptions abandonnées/Inscriptions lancées).

### <a name="line-graph"></a>Graphique linéaire

Le graphique linéaire affiche les abandons quotidiens pour chacune des quatre sections d’inscription principales :

-   Liste de contrôle de configuration
-   Écrans de plateforme
-   Conditions d'utilisation
-   Conformité/activation

### <a name="user-abandonment-actions"></a>Actions d’abandon par l’utilisateur

Les tableaux suivants présentent la liste des actions de l’utilisateur considérées comme un abandon. Pour voir des exemples d’écrans d’inscription, vous pouvez regarder les vidéos d’inscription pour [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment) et [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment). 


#### <a name="setup-checklist-section"></a>Section Liste de contrôle de configuration

| Nom de l’abandon | Écran ou flux | Plate-forme | Action |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Invite d’ouverture de page sur le Portail d’entreprise | iOS/Android | **Annuler** |
| EnrollmentWrapUp | Écran d’inscription de l’appareil jusqu’à la fin du **chargement des ressources d’entreprise** | iOS/Android | A duré plus de 30 minutes |
| DeviceCategory | Sélection de la catégorie d’appareil (si l’administrateur l’a configurée) jusqu’au clic **Terminé** | iOS/Android | A duré plus de 30 minutes |
| PreEnrollmentWizard | Retour à l’écran de configuration de l’accès après avoir commencé l’inscription | iOS/Android| **Reporter** |
| PreEnrollmentWizard | Écran de configuration de l’accès jusqu’au clic sur **Suivant** dans l’écran **Quelle est la prochaine étape ?** | iOS/Android | A duré plus de 30 minutes |

#### <a name="platform-screens-section"></a>Section Écrans de plateforme

| Nom de l’abandon | Écran ou flux | Plate-forme | Action |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Invite d’affichage d’un profil de configuration | iOS | **Ignorer** |
| iOSProfileLaunch | Écran d’installation de profil | iOS | **Annuler** |
| iOSProfileLaunch | Invite d’approbation de la source du profil pour inscrire l’appareil | iOS | **Annuler** |
| iOSProfileLaunch | Écran Installer un profil jusqu’à ce que le profil soit installé | iOS | A duré plus de 30 minutes |
| AndroidPermissions | Écran d’activation de l’administrateur d’appareils | Android | **Annuler** |
| AndroidPermissions | Depuis l’invite d’approbation pour passer et gérer les appels téléphoniques jusqu’à l’**activation** de l’administrateur d’appareils | Android | A duré plus de 30 minutes |
| KnoxActivation | Activation de l’agent KLMS (Samsung uniquement) | Android| **Annuler** |
| KnoxActivation | Activation de l’agent KLMS jusqu’à **Confirmer** | Android | A duré plus de 30 minutes|

#### <a name="terms-of-use-section"></a>Section Conditions d’utilisation

| Nom de l’abandon | Écran ou flux | Plate-forme | Action |
| ---- |---- |---- |---- |
| TermsofUse | Conditions d’utilisation (si l’administrateur les a configurées) | iOS/Android | **Refuser tout** |
| TermsofUse | Conditions d’utilisation jusqu’à **Accepter tout** | iOS/Android | A duré plus de 30 minutes |

#### <a name="complianceactivation-section"></a>Section Conformité/activation

| Nom de l’abandon | Écran ou flux | Plate-forme | Action |
| ---- |---- |---- |---- |
| Compatibilité | La conformité de l’appareil (si l’administrateur l’a configurée) n’apparaît pas en vert lors de la configuration de l’accès post-inscription| iOS/Android | **Reporter** |
| Compatibilité | La conformité de l’appareil n’apparaît pas en vert jusqu’à ce qu’elle soit mise à jour | iOS/Android | A duré plus de 30 minutes |
| Activation | L’activation de l’inscription (si l’administrateur l’a configurée) n’apparaît pas en vert lors de la configuration de l’accès | iOS/Android | **Reporter** |
| Compatibilité | L’activation de l’appareil n’apparaît pas en vert jusqu’à ce qu’elle soit mise à jour | iOS/Android | A duré plus de 30 minutes |

## <a name="next-steps"></a>Étapes suivantes

Après avoir vérifié vos taux d’abandon, vous pouvez consulter les [options d’inscription](enrollment-options.md) pour voir si vous pouvez apporter des modifications afin d’améliorer l’inscription.