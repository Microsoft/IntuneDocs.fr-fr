---
title: Décisions d’ordre informatique pour BYOD avec EMS
description: Principales décisions d’ordre informatique pour activer BYOD et protéger les données d’entreprise avec Microsoft Enterprise Mobility + Security.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/8/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 21257169e069a139ac94dcdecbe6074ab0778aeb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179556"
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Décisions d’ordre informatique pour activer BYOD avec Microsoft Enterprise Mobility + Security (EMS)

Quand vous développez votre stratégie permettant aux employés de travailler à distance sur leurs propres appareils (BYOD), vous devez prendre des décisions importantes dans les scénarios impliquant l’activation de BYOD et la protection des données de votre entreprise. Heureusement, EMS offre dans un ensemble complet de solutions toutes les fonctionnalités dont vous avez besoin.  

Dans cette rubrique, nous allons examiner le cas d’utilisation simple qui consiste à activer l’accès BYOD à l’e-mail de l’entreprise. Nous allons déterminer si vous devez gérer l’appareil dans son ensemble, ou uniquement les applications (sachant que ces choix sont tous deux tout à fait valides).

## <a name="assumptions"></a>Hypothèses
* Vous avez une connaissance élémentaire d’Azure Active Directory et de Microsoft Intune
* Vos comptes e-mail sont hébergés dans Exchange Online

## <a name="common-reasons-to-manage-the-device-mdm"></a>Raisons courantes pour gérer les appareils (MDM)
Vous pouvez facilement inciter les utilisateurs à inscrire leurs appareils à la gestion des appareils en déployant une stratégie [d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) sur Exchange Online. Voici les raisons pour lesquelles vous pourriez souhaiter gérer des appareils personnels :

**Wi-Fi/VPN** : si vos utilisateurs ont besoin d’un profil de connectivité d’entreprise pour être productifs, cela peut être configuré très facilement.

**Applications** : si vos utilisateurs ont besoin qu’un ensemble d’applications soit envoyé sur leur appareil, ces applications peuvent être remises très facilement. Cela comprend des applications dont vous pourriez avoir besoin pour des raisons de sécurité, par exemple une application Mobile Threat Defense.

**Conformité** : certaines organisations doivent se conformer à des normes ou à des stratégies qui exigent des contrôles MDM spécifiques. Par exemple, vous avez besoin de MDM pour chiffrer l’ensemble de l’appareil ou pour générer un rapport de toutes les applications de l’appareil.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>Raisons courantes pour gérer uniquement les applications (MAM)
La Gestion MAM sans MDM est très répandue dans les organisations qui prennent en charge BYOD. Vous pouvez amener les utilisateurs à accéder aux e-mails à partir d’Outlook Mobile (qui prend en charge les protections MAM) en déployant une stratégie d’accès conditionnel sur Exchange Online. Voici les raisons pour lesquelles vous pourriez souhaiter gérer uniquement les applications sur les appareils personnels :

**Expérience utilisateur** : l’inscription MDM génère de nombreux messages d’avertissement (appliqués par la plateforme) qui amènent souvent l’utilisateur à finalement préférer ne pas accéder du tout à ses e-mails sur son appareil personnel. La Gestion MAM est beaucoup moins inquiétante pour les utilisateurs : une fenêtre contextuelle s’affiche simplement une fois pour leur signaler que des protections de gestion des applications mobiles sont en place.

**Conformité** : certaines organisations doivent se conformer à des stratégies qui exigent moins de fonctions de gestion sur les appareils personnels. Par exemple, la Gestion MAM peut uniquement supprimer les données d’entreprise des applications, alors que la Gestion MDM peut supprimer toutes les données de l’appareil.

![Image comparant la gestion des appareils et la gestion des applications sur les appareils mobiles](./media/byod-app-device-mgmt.png)

En savoir plus sur les [cycles de vie de gestion d’applications et de gestion d’appareils](introduction-device-app-lifecycles.md).

## <a name="mdm-vs-mam-capability-comparison"></a>Comparaison des fonctionnalités MDM avec les fonctionnalités MAM
Comme mentionné plus haut, l’accès conditionnel peut inciter un utilisateur à inscrire son appareil ou à utiliser une application gérée comme Outlook Mobile. De nombreuses autres conditions peuvent être appliquées dans les deux cas, notamment :

* Quel utilisateur tente d’obtenir l’accès
* Si l’emplacement est approuvé ou non approuvé
*   Niveau de risque de connexion
* Plateforme d’appareils

De nombreuses organisations sont souvent soucieuses de certains risques spécifiques.  Le tableau ci-dessous liste les risques les plus courants et les réponses MDM et MAM correspondantes.

| Risque   |   GESTION DES APPAREILS MOBILES  |   MAM  |
|------------|--------|--------|
|Accès aux données non autorisé | Exiger l’appartenance à un groupe | Exiger l’appartenance à un groupe |
|Accès aux données non autorisé | Exiger l’inscription d’appareil | Exiger la protection d’application |
|Accès aux données non autorisé | Exiger un emplacement spécifique | Exiger un emplacement spécifique |
| | | |
|Compte d’utilisateur compromis| Exiger MFA | Exiger MFA|
|Compte d’utilisateur compromis | Bloquer les utilisateurs à haut risque | Bloquer les utilisateurs à haut risque |
|Compte d’utilisateur compromis | Code PIN d’appareil | Code PIN d’application |
| | | |
| Application ou appareil compromis | Exiger un appareil conforme | Vérification de jailbreak au démarrage de l’application |
| Application ou appareil compromis | Chiffrer les données de l’appareil | Chiffrer les données de l'application |
| | | |
|Perte ou vol d’appareil | Supprimer toutes les données de l’appareil | Supprimer toutes les données d’application|
| | | |
| Partage de données accidentel ou enregistrement à des emplacements non sécurisés | Restreindre les sauvegardes de données d’appareil | Restreindre les opérations de couper/copier/coller|
| Partage de données accidentel ou enregistrement à des emplacements non sécurisés | Restreindre Enregistrer sous | Restreindre Enregistrer sous |
|Partage de données accidentel ou enregistrement à des emplacements non sécurisés | Désactiver l’impression | Non applicable|

## <a name="next-steps"></a>Étapes suivantes
Il est maintenant temps de décider si vous allez activer BYOD dans votre organisation en vous concentrant sur la gestion des appareils, la gestion des applications ou une combinaison des deux. Le choix de l’implémentation dépend de vous. Vous aurez dans tous les cas la certitude que les fonctionnalités d’identité et de sécurité disponibles avec Azure AD seront disponibles.  

Utilisez le [Guide de planification](planning-guide.md) Intune pour identifier le niveau suivant de planification.
