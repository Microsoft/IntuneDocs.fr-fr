---
title: Guide pratique pour effacer uniquement les données d’entreprise des applications
titleSuffix: Microsoft Intune
description: Découvrez comment réinitialiser de manière sélective les données d’entreprise uniquement à partir d’applications gérées par Intune avec Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 51d1c477f490cb23c35ef54a0a5099ee4b4b035b
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55068252"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Guide pratique pour effacer uniquement les données d’entreprise des applications gérées par Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Lorsqu'un appareil est perdu ou volé, ou si l'employé quitte votre entreprise, vous devez vous assurer que les données de l'application d’entreprise sont supprimées de l'appareil. Mais vous ne souhaitez peut-être pas supprimer les données personnelles contenues dans l’appareil, en particulier si celui-ci appartient à un employé.

>[!NOTE]
> Les plateformes iOS et Android sont les deux plateformes prises en charge actuellement pour le nettoyage des données d’entreprise à partir d’applications gérées par Intune. Les applications gérées par Intune incluent le SDK d’application Intune et disposent d’un compte d’utilisateur sous licence pour votre organisation. Il n’est pas obligatoire d’activer la réinitialisation sélective des applications dans les stratégies de déploiement de la protection des applications.

Pour supprimer des données d’application d’entreprise de manière sélective, créez une demande de réinitialisation en suivant les étapes indiquées dans cette rubrique. Une fois la demande terminée, les données d’entreprise sont supprimées de l’application dès sa prochaine exécution sur l’appareil. En plus de créer une demande de réinitialisation, vous pouvez configurer une réinitialisation sélective des données de votre organisation comme nouvelle action quand les conditions des paramètres d’accès des stratégies de protection des applications ne sont pas remplies. Cette fonctionnalité vous permet de protéger et de supprimer automatiquement des données d’entreprise sensibles dans des applications en fonction de critères préconfigurés.

>[!IMPORTANT]
> Les contacts synchronisés avec le carnet d’adresses natif directement à partir de l’application sont supprimés. Les contacts synchronisés à partir du carnet d’adresses natif vers une autre source externe ne peuvent pas être réinitialisés. Actuellement, cela s’applique uniquement à l’application Microsoft Outlook.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Stratégies de protection des informations Windows déployées sans inscription de l’utilisateur
Les stratégies de protection des informations Windows peuvent être déployées sans que les utilisateurs MDM ne soient obligés d’inscrire leur appareil Windows 10. Cette configuration permet aux organisations de protéger leurs documents d’entreprise conformément à la configuration de la protection des informations Windows, tout en permettant à l’utilisateur de conserver la gestion de ses propres appareils Windows. Une fois les documents protégés par une stratégie de protection des informations Windows, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie de protection des informations Windows. À partir d’Intune dans le portail Azure, sélectionnez **Application cliente** > **Réinitialisation sélective des applications**. Pour plus d’informations, consultez [Créer et déployer une stratégie de protection d’application Protection des informations Windows (WIP) avec Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Créer une demande de réinitialisation

1.  Connectez-vous au [portail Azure](https://portal.azure.com).

2.  Choisissez **Tous les services**, saisissez **Intune** dans la zone de texte de filtre, puis sélectionnez **Intune**. Le volet Intune s’ouvre. Choisissez le volet **Applications clientes**.

    ![Capture d’écran du volet Microsoft Intune](./media/apps-selective-wipe01.png)

3.  Dans le volet **Applications clientes**, choisissez **Réinitialisation sélective des applications**.

4.  Choisissez **Nouvelle demande de réinitialisation**. Le volet **Nouvelle demande de réinitialisation** s’ouvre.

    ![Capture d’écran du panneau Nouvelle demande de réinitialisation](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Choisissez un utilisateur, puis choisissez **Sélectionnez** pour sélectionner l’utilisateur dont vous souhaitez réinitialiser les données d’application.

6.  Ensuite, choisissez **Appareil** dans le volet **Nouvelle demande de réinitialisation**. Cette opération ouvre le volet **Sélectionner un appareil**, qui répertorie tous les appareils associés à l’utilisateur sélectionné et fournit également deux colonnes : le nom de l’appareil, qui est un nom convivial défini par l’utilisateur et le type d’appareil, à savoir sa plateforme. Sélectionnez l’appareil à réinitialiser.

7.  Vous voilà revenu dans le volet **Nouvelle demande de réinitialisation**. Choisissez **Ok** pour effectuer une demande de réinitialisation.

Le service crée une demande de réinitialisation distincte pour chaque application protégée sur l’appareil et l’utilisateur associé à la demande de réinitialisation, et en fait le suivi.

## <a name="monitor-your-wipe-requests"></a>Analyser vos demandes de réinitialisation

Vous pouvez obtenir un rapport de synthèse indique l’état global de la demande de réinitialisation et inclut le nombre de demandes en attente et d’échecs. Pour obtenir plus de détails, procédez comme suit :

1.  Dans le volet **Applications clientes - Réinitialisation sélective des applications**, vous pouvez voir la liste de vos demandes regroupées par utilisateurs. Étant donné que le système crée une demande de réinitialisation pour chaque application protégée en cours d’exécution sur l’appareil, vous pouvez voir plusieurs demandes pour un même utilisateur. L’état de la demande de réinitialisation est indiquée : **en attente**, **échec**ou **réussite**.

    ![Capture d’écran de l’état de demande de réinitialisation dans le volet Réinitialisation sélective des applications](./media/wipe-request-status-1.png)

En outre, vous pouvez voir le nom de l’appareil et son type, ce qui peut être utile lors de la lecture des rapports.

>[!IMPORTANT]
> L’utilisateur doit ouvrir l’application pour que la réinitialisation se produise. Cette opération peut prendre jusqu’à 30 minutes après l’envoi de la demande.

## <a name="delete-a-wipe-request"></a>Suppression d’une demande de réinitialisation

Les réinitialisations en attente sont affichées jusqu’à ce que vous les supprimiez manuellement. Pour supprimer manuellement une demande de réinitialisation :

1.  Dans le volet **Applications clientes - Réinitialisation sélective des applications**.

2.  Dans la liste, cliquez avec le bouton droit sur la demande de réinitialisation à supprimer, puis choisissez **Supprimer la demande de réinitialisation**.

    ![Capture d’écran de la liste de demandes de réinitialisation dans le volet Réinitialisation sélective des applications](./media/delete-wipe-request.png)

3.  Vous êtes invité à confirmer la suppression. Choisissez **Oui** ou **Non**, puis cliquez sur **OK**.

### <a name="see-also"></a>Voir aussi
[Qu'est-ce qu'une stratégie de protection d’application](app-protection-policy.md)

[Qu’est-ce que la gestion des applications](app-management.md)
