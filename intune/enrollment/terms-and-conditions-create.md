---
title: Définir les conditions générales dans Microsoft Intune
titleSuffix: ''
description: Définissez les conditions générales que les utilisateurs voient dans le Portail d’entreprise pour Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ef002b508e484d6967bbdd0908729332d866046
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726360"
---
# <a name="terms-and-conditions-for-user-access"></a>Conditions générales de l’accès utilisateur

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez demander aux utilisateurs d’accepter les conditions générales de votre entreprise avant d’utiliser l’application Portail d’entreprise pour :
- Inscrire des appareils
- Accéder à des ressources telles que les applications et l’e-mail de l’entreprise

La configuration des conditions générales est facultative.

Vous pouvez créer plusieurs ensembles de conditions générales et les affecter à différents groupes, par exemple pour prendre en charge différentes langues.

Il existe deux façons de créer les conditions générales de votre entreprise :
- À l’aide d’Intune, comme décrit dans cet article.
- À l’aide de la [fonctionnalité Conditions d’utilisation d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)

Pour savoir quelle est la méthode qui vous convient le mieux, consultez le billet de blog sur le [choix de la solution des Conditions générales pour votre organisation](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409). 

## <a name="create-terms-and-conditions"></a>Créer des conditions générales
Effectuez ces étapes pour créer les conditions générales. Le nom d’affichage et la description sont destinés à un usage administratif, tandis que les propriétés des conditions générales sont présentées aux utilisateurs du portail d’entreprise.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Dans le volet **Intune**, choisissez **Inscription de l’appareil** > **Conditions générales**.
3. Choisissez **Créer**.
4. Dans la page **Informations de base**, spécifiez les informations suivantes :

   - **Nom** : Nom donné aux conditions générales dans le portail Azure. Les utilisateurs ne voient pas ce nom.
   - **Description** : Informations facultatives qui vous aident à identifier cet ensemble de conditions générales dans le portail Azure.

    ![Capture d’écran du portail Azure montrant la page Informations de base des conditions générales](./media/terms-and-conditions-create/terms-basics-page.png)

5. Choisissez **Suivant** pour accéder à la page **Conditions** et fournir les informations suivantes :

   - **Titre** : Nom de vos conditions générales que les utilisateurs voient dans le portail d’entreprise, au-dessus du **résumé**.
   - **Conditions générales** : Conditions générales que les utilisateurs voient et doivent accepter ou refuser.
   - **Résumé des conditions** : Texte qui explique la signification de l’acceptation des conditions générales par les utilisateurs. Par exemple, « En inscrivant votre appareil, vous acceptez les conditions d’utilisation définies par Contoso. Lisez les termes du contrat avec soin avant de continuer. ».

6. Choisissez **Suivant** pour accéder à la page **Balises d'étendue**.

7. Cliquez sur **Sélectionner des balises d’étendue**, choisissez les balises d’étendue que vous souhaitez affecter à ces conditions générales, puis cliquez sur **Sélectionner**. 

8. Choisissez **Suivant** pour accéder à la page **Attributions**, puis sélectionnez une des options suivantes pour **Attribuer à** :
    - **Tous les utilisateurs** : Choisissez cette option pour attribuer ces conditions générales à tous les utilisateurs.
    - **Sélectionner des groupes** : Choisissez cette option pour attribuer ces conditions générales à tous les membres des groupes que vous identifiez en choisissant **Sélectionner les groupes à inclure**.

9. Choisissez **Suivant** > **Créer**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Découvrez comment vos utilisateurs voient les conditions générales
L’exemple suivant montre le **titre** et le **résumé des conditions** dans la console d’administration et le portail d’entreprise.

![Capture d’écran du titre et du résumé des conditions générales dans la console d’administration et le portail d’entreprise.](./media/terms-and-conditions-create/terms-summary-terms.png)

L’exemple suivant montre les conditions générales dans la console d’administration et le portail d’entreprise.

![Capture d’écran des conditions générales dans la console d’administration et le portail d’entreprise.](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>Surveiller des conditions générales

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). 
1. Dans le volet Intune, choisissez **Inscription de l’appareil** > **Conditions générales**.
2. Dans la liste des conditions générales, choisissez les conditions dont vous souhaitez voir l’acceptation > **Rapport d’acceptation**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Utiliser plusieurs versions des conditions générales
Vous pouvez modifier vos conditions générales et gérer leurs versions. Chaque fois que vous apportez un changement significatif aux conditions générales, vous devez :
- Augmenter le numéro de version.
- Obliger les utilisateurs à accepter les nouvelles conditions générales.

Conserver le numéro de version actuel si, par exemple, vous corrigez des fautes de frappe ou modifiez la mise en forme.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Dans le volet Intune, choisissez **Inscription de l’appareil** > **Conditions générales** > choisissez les conditions générales à modifier > **Propriétés**.

4. Dans le volet **Propriétés**, choisissez **Conditions générales**, puis modifiez le **Titre**, le **Résumé des conditions** et les **Conditions générales** selon les besoins. Si vos changements imposent aux utilisateurs d’accepter les nouvelles conditions générales, choisissez **Demandez aux utilisateurs de réaccepter les conditions et passez au numéro de version**

4. Choisissez **OK** > **Enregistrer**.

Il suffit aux utilisateurs d’accepter une seule fois les conditions générales mises à jour. Les utilisateurs de plusieurs appareils n’ont pas besoin d’accepter les conditions générales sur chaque appareil.
