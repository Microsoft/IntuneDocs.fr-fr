---
title: Définir les conditions générales dans Microsoft Intune
titlesuffix: ''
description: Définissez les conditions générales que les utilisateurs voient dans le Portail d’entreprise pour Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 550d9c457335f212f0b60c16249e45f22f5baaf5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="manage-your-companys-terms-and-conditions-for-user-access"></a>Gérer les conditions générales de votre entreprise pour l’accès utilisateur

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez exiger que les utilisateurs acceptent les conditions générales de votre société avant de pouvoir utiliser le portail d’entreprise pour inscrire leurs appareils et accéder aux ressources telles que les applications et la messagerie d’entreprise. La configuration des conditions générales est facultative.

Vous pouvez créer plusieurs ensembles de conditions générales et les affecter à différents groupes, par exemple pour prendre en charge différentes langues.

## <a name="create-terms-and-conditions"></a>Créer des conditions générales
Effectuez ces étapes pour créer les conditions générales. Le nom d’affichage et la description sont destinés à un usage administratif, tandis que les propriétés des conditions générales sont présentées aux utilisateurs du portail d’entreprise.

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Inscription de l’appareil**, puis **Conditions générales**.
2. Sélectionnez **Créer**.
![Capture d’écran du portail Azure montrant le bouton Créer pour les conditions générales](media/terms-create-terms.png)
3. Dans le volet étendu, spécifiez les informations suivantes :

   - **Nom d’affichage** : nom pour les conditions générales dans le portail Azure. Les utilisateurs ne voient pas ce nom.

   - **Description** : détails facultatifs qui vous aident à identifier cet ensemble de conditions générales dans le portail Azure.

4. Sélectionnez la flèche en regard de **Définir la condition d’utilisation** pour ouvrir le volet des Conditions générales, puis entrez les informations suivantes :

   ![Capture de l’écran d’acceptation des conditions générales de l’utilisateur final avec récapitulatif des conditions](./media/terms-summary-create.png)

   - **Titre** : nom de vos conditions générales que les utilisateurs voient dans le portail d’entreprise, au-dessus du **résumé**.
   - **Résumé des conditions** : texte qui explique la signification de l'acceptation par les utilisateurs des conditions générales. Par exemple, « En inscrivant votre appareil, vous acceptez les conditions d’utilisation définies par Contoso. Lisez les termes du contrat avec soin avant de continuer. ».
   - **Conditions générales** : conditions générales que les utilisateurs voient et doivent accepter ou rejeter.

5. Sélectionnez **OK**, puis **Créer**.

## <a name="see-how-terms-are-displayed-to-your-users"></a>Découvrez comment vos utilisateurs voient les conditions générales
L’exemple suivant montre le **titre** et le **résumé des conditions** dans la console d’administration et le portail d’entreprise.

![Capture d’écran du titre et du résumé des conditions générales dans la console d’administration et le portail d’entreprise.](./media/terms-summary-terms.png)

L’exemple suivant montre les conditions générales dans la console d’administration et le portail d’entreprise.

![Capture d’écran des conditions générales dans la console d’administration et le portail d’entreprise.](./media/terms-properties-terms.png)

## <a name="assign-terms-and-conditions"></a>Affecter des conditions générales

Vous pouvez affecter des conditions générales à des groupes d’utilisateurs qui doivent les accepter avant d’utiliser le Portail d’entreprise.

1. Dans le portail Azure, choisissez **Inscription de l’appareil**, puis **Conditions générales**.
2. Dans la liste des conditions générales, sélectionnez celles à affecter, puis sélectionnez **Gérer** > **Affectations**.
![Capture d’écran du volet Affecter un groupe du portail Azure montrant le bouton Sélectionner un groupe et un bouton Sélectionner pour l’affectation des conditions générales](media/terms-assign-groups.png)
3. Cliquez sur **Sélectionner les groupes à inclure** et sélectionnez les groupes auxquels vous souhaitez affecter les conditions générales, puis cliquez sur **Sélectionner**. Vous ne pouvez pas affecter des conditions générales à des groupes dynamiques.
4. Dans le volet **Groupes affectés**, cliquez sur **Enregistrer**.  Les conditions générales sont maintenant affectées aux utilisateurs dans les groupes sélectionnés. Les utilisateurs seront invités à accepter les conditions générales la prochaine fois qu’ils accèderont au portail d’entreprise. Il suffit d’accepter une seule fois les conditions générales. Les utilisateurs de plusieurs appareils n’ont pas besoin d’accepter ces conditions sur chaque appareil.


## <a name="monitor-terms-and-conditions"></a>Surveiller des conditions générales

1. Dans le portail Azure, choisissez **Tous les services** > **Surveillance + Gestion** > **Intune**. 
1. Dans le volet Intune, choisissez **Inscription de l’appareil**, puis **Conditions générales**.
2. Dans la liste des conditions générales, sélectionnez celles pour lesquelles vous souhaitez voir l’acceptation, puis sélectionnez **Rapport d’acceptation**.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>Utiliser plusieurs versions des conditions générales
Vous pouvez modifier vos conditions générales et gérer leurs versions. Nous vous recommandons d’incrémenter le numéro de version et d’exiger l’acceptation chaque fois que vous apportez des modifications majeures à vos conditions générales. Conservez le numéro de version actuel si, par exemple, vous corrigez des fautes de frappe ou modifiez la mise en forme.

1. Dans le portail Azure, choisissez **Tous les services** > **Surveillance + Gestion** > **Intune**.

2. Dans le volet Intune, choisissez **Inscription de l’appareil**, **Conditions générales**, sélectionnez les conditions générales que vous souhaitez modifier, puis sélectionnez **Propriétés**.

4. Dans le volet **Propriétés**, sélectionnez **Conditions générales**, puis modifiez le **Titre**, le **Résumé des conditions** et les **Conditions générales** en fonction des besoins. Si ces modifications exigent que les utilisateurs acceptent les nouvelles conditions générales, cliquez sur **Demandez aux utilisateurs de réaccepter les conditions et passez au numéro de version**

4.  Sélectionnez **OK**, puis **Enregistrer**.

Il suffit aux utilisateurs d’accepter une seule fois les conditions générales mises à jour. Les utilisateurs de plusieurs appareils n’ont pas besoin d’accepter les conditions générales sur chaque appareil.
