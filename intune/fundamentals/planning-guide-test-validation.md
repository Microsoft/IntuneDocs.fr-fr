---
title: Test et validation Intune
titleSuffix: Microsoft Intune
description: Découvrez comment tester et valider dans votre solution Intune cloud uniquement dans votre environnement.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2ce184a2dbd0ca4b66740f0687302d1ed007878
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505019"
---
# <a name="intune-testing-and-validation"></a>Test et validation Intune

Quand vous testez l’implémentation de Microsoft Intune, pensez à la validation fonctionnelle et à la validation des cas d’usage. La validation fonctionnelle consiste à tester chaque composant et configuration pour vérifier son fonctionnement. La validation des cas d’usage implique des tests pour vérifier que les scénarios impliquant une série de tâches fonctionnent comme prévu. 

Nous vous recommandons d’impliquer votre personnel de support et d’assistance informatique dans la phase de test afin de créer une documentation de support et permettre au personnel de se familiariser avec le produit. Si un composant ou scénario ne fonctionne pas dans un cas d’utilisation, veillez à documenter les modifications nécessaires et à inclure la raison pour laquelle une modification a été apportée.

## <a name="before-you-begin"></a>Avant de commencer

Nous vous recommandons de documenter les éléments suivants :

- **Critères de test** : ils identifient les tests d’évaluation à effectuer.

- **Composants de conception** : ils doivent figurer dans au moins un des critères de test.

Si un composant de conception ne figure pas dans au moins un des critères de test en adéquation avec une exigence ou un scénario, déterminez si ce composant de conception est nécessaire ou non. En outre, assurez-vous de disposer des éléments suivants :

- **Comptes** : comptes de test EMS et Office 365 concédés sous licence pour tester tous les scénarios de cas d’usage.

- **Appareils** : appareils de test qui peuvent être réinitialisés ou dont les paramètres d’usine peuvent être rétablis.

- **Composants d’intégration** : Tous les composants d’intégration (connecteurs de certificat et connecteur local Exchange d’Intune) doivent être installés et configurés, si nécessaire.

Des modifications de conception peuvent s’avérer nécessaires pour prendre en compte les problèmes imprévus. En outre, toutes les modifications de conception doivent être entièrement documentées en justifiant chaque changement. Voici un exemple de modification :

<blockquote>Vous réalisez que vous ne répondez pas aux exigences du Service d’inscription de périphérique réseau (NDES) et apprenez aussi que les profils VPN et Wi-Fi peuvent être configurés avec une autorité de certification racine qui répond aux mêmes exigences sans nécessiter d’implémentation NDES.</blockquote>

Vous pouvez rencontrer des difficultés qui requièrent des conseils techniques ou un dépannage spécialisé pendant le processus de test et de validation. Nous vous recommandons de demander de l’aide via les canaux de support Microsoft.

- [Découvrir comment obtenir du support Intune](../get-support.md)

- [Contacter le support par téléphone pour Microsoft Intune](../get-support.md)

## <a name="functional-validation-testing"></a>Test de validation fonctionnel

La validation fonctionnelle consiste à tester chaque composant et configuration pour vérifier son fonctionnement. Vous trouverez un exemple de test de validation dans le tableau ci-dessous.

![Section 9 tableau 1](./media/planning-guide-test-validation/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>Test de validation de cas d'utilisation

Procédez à un test de validation de cas d’utilisation pour vérifier que les scénarios sont complets et fonctionnels. Il y a deux types de scénarios : administrateur informatique et utilisateur final.

### <a name="it-admin"></a>Administrateur informatique

Procédez à un test de validation administrateur informatique pour vérifier que les actions d’administration effectuées sur un appareil ou un utilisateur fonctionnent correctement. Voici un exemple de scénario de validation administrateur informatique de bout en bout.

![Section 9 tableau 2](./media/planning-guide-test-validation/section-9-image-2-table.PNG)

### <a name="end-user"></a>Utilisateur final

Procédez à un test de validation utilisateur final pour vérifier que l’expérience de l’utilisateur final se déroule et se présente comme prévu dans toutes les communications de l’utilisateur. Il est important de vérifier que l’expérience de l’utilisateur final est correcte. À défaut, vous risquez d’enregistrer des taux d’adoption plus faibles et un nombre d’appels au support technique plus élevé.

![Section 9 tableau 3](./media/planning-guide-test-validation/section-9-image-3-table.PNG)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez testé et validé vos scénarios fonctionnels et de cas d’utilisation Intune, vous êtes prêt pour le [déploiement de production Intune](../planning-guide-rollout-plan.md).

Pour obtenir des informations et des modèles de planification supplémentaires, consultez [Ressources supplémentaires](../planning-guide-resources.md).
