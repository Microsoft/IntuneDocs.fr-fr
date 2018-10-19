---
title: 'Démarrage rapide : Ajouter une stratégie de conformité des appareils pour un appareil Windows 10'
description: Utilisez ce guide de démarrage rapide pour créer des stratégies permettant de protéger les données d’entreprise et de gérer les appareils dont les utilisateurs finaux se servent pour accéder aux ressources de l’entreprise. Ensuite, affectez les stratégies à des groupes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73e1e0a27d128d567a924e6f2b343026b11f1a44
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581580"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>Démarrage rapide : Ajouter une stratégie de conformité des appareils pour un appareil Windows 10
Une stratégie de conformité de l’appareil Intune pour Windows spécifie les règles et les paramètres que les appareils Windows doivent satisfaire pour être considérés comme conformes. Vous pouvez utiliser ces stratégies avec un [accès conditionnel](https://docs.microsoft.com/intune/conditional-access) pour autoriser ou bloquer l’accès aux ressources de l’entreprise. Vous pouvez également obtenir des rapports sur les appareils et prendre des mesures en cas de non-conformité.

Dans ce guide de démarrage rapide, vous allez créer une stratégie de conformité des appareils pour un appareil Windows 10, puis affecter un groupe d’appareils à cette stratégie.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis
- Pour effectuer les opérations décrites dans ce guide de démarrage rapide, vous devez d’abord [créer un utilisateur](quickstart-create-user.md) et [créer un groupe](quickstart-create-group.md).


## <a name="sign-in-to-intune"></a>Se connecter à Intune
Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune.

## <a name="create-a-device-compliance-policy"></a>Créer une stratégie de conformité des appareils
1. Sélectionnez **Conformité de l’appareil** > **Stratégies** > **Créer une stratégie**.
2. Entrez **Conformité Windows 10** dans **Nom** et **Exemple de stratégie de conformité pour Windows 10** dans **Description**.
3. Pour **Plateforme**, sélectionnez **Windows 10 et ultérieur**.
4. Dans **Paramètres**, sélectionnez **Sécurité du système**, puis définissez **Exiger un mot de passe pour déverrouiller des appareils mobiles** sur **Exiger**. Une fois que vous avez fini de configurer votre stratégie, sélectionnez **OK**.
   ![Stratégie de conformité](/intune/media/quickstart-create-policy/compliance-policy.png)
5. Fermez le volet **Stratégie de conformité Windows 10**. 
6. Dans le volet **Créer une stratégie**, sélectionnez **Créer**. Cette étape crée la stratégie et la fait apparaître dans **Conformité de l’appareil** > **Stratégies**.
7. Sélectionnez votre nouvelle stratégie, puis choisissez **Affectations**. Vous pouvez inclure ou exclure des groupes de sécurité Azure AD (Azure Active Directory).
8. Choisissez **Groupes sélectionnés** pour voir vos groupes de sécurité Azure AD existants. Sélectionnez **Testeurs Contoso**, puis choisissez **Enregistrer** pour déployer la stratégie sur les utilisateurs du groupe. Si vous n’avez pas créé ce groupe dans [créer un groupe](quickstart-create-group.md), vous pouvez utiliser le groupe de votre choix. 

## <a name="clean-up-resources"></a>Nettoyer les ressources
Quand la stratégie n’est plus nécessaire, supprimez-la. Pour ce faire, sélectionnez la stratégie **Conformité Windows 10**, puis cliquez sur **Supprimer**. 

## <a name="next-steps"></a>Étapes suivantes
Dans ce guide de démarrage rapide, vous avez créé et affecté une stratégie de conformité des appareils toute simple. Pour inscrire un appareil Windows 10 destiné à recevoir la stratégie, suivez le guide de démarrage rapide jusqu’à la configuration de l’inscription automatique. 
 
> [!div class="nextstepaction"]
> [Configurer l’inscription automatique](quickstart-setup-auto-enrollment.md)