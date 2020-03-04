---
title: Guide pratique pour effacer uniquement les données d’entreprise des applications
titleSuffix: Microsoft Intune
description: Découvrez comment réinitialiser de manière sélective les données d’entreprise uniquement à partir d’applications gérées par Intune avec Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 66319fab8449ac1832f7796fbfdd470d2a52e88a
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781272"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Guide pratique pour effacer uniquement les données d’entreprise des applications gérées par Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Lorsqu'un appareil est perdu ou volé, ou si l'employé quitte votre entreprise, vous devez vous assurer que les données de l'application d’entreprise sont supprimées de l'appareil. Mais vous ne souhaitez peut-être pas supprimer les données personnelles contenues dans l’appareil, en particulier si celui-ci appartient à un employé.

>[!NOTE]
> Les plateformes iOS/iPadOS, Android et Windows 10 sont les seules plateformes prises en charge actuellement pour le nettoyage des données d’entreprise à partir d’applications gérées par Intune. Les applications gérées par Intune incluent le SDK d’application Intune et disposent d’un compte d’utilisateur sous licence pour votre organisation. Il n’est pas obligatoire d’activer la réinitialisation sélective des applications dans les stratégies de déploiement de la protection des applications.

Pour supprimer des données d’application d’entreprise de manière sélective, créez une demande de réinitialisation en suivant les étapes indiquées dans cette rubrique. Une fois la demande terminée, les données d’entreprise sont supprimées de l’application dès sa prochaine exécution sur l’appareil. En plus de créer une demande de réinitialisation, vous pouvez configurer une réinitialisation sélective des données de votre organisation comme nouvelle action quand les conditions des paramètres d’accès des stratégies de protection des applications ne sont pas remplies. Cette fonctionnalité vous permet de protéger et de supprimer automatiquement des données d’entreprise sensibles dans des applications en fonction de critères préconfigurés.

>[!IMPORTANT]
> Les contacts synchronisés avec le carnet d’adresses natif directement à partir de l’application sont supprimés. Les contacts synchronisés à partir du carnet d’adresses natif vers une autre source externe ne peuvent pas être réinitialisés. Actuellement, cela s’applique uniquement à l’application Microsoft Outlook.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Stratégies de protection des informations Windows déployées sans inscription de l’utilisateur
Les stratégies de protection des informations Windows peuvent être déployées sans que les utilisateurs MDM ne soient obligés d’inscrire leur appareil Windows 10. Cette configuration permet aux organisations de protéger leurs documents d’entreprise conformément à la configuration de la protection des informations Windows, tout en permettant à l’utilisateur de conserver la gestion de ses propres appareils Windows. Une fois les documents protégés par une stratégie de protection des informations Windows, les données protégées peuvent être réinitialisées de manière sélective par un administrateur Intune. En sélectionnant l’utilisateur et l’appareil, et en envoyant une demande de réinitialisation, vous rendrez inutilisables toutes les données qui étaient protégées par la stratégie de protection des informations Windows. À partir d’Intune dans le portail Azure, sélectionnez **Application cliente** > **Réinitialisation sélective des applications**. Pour plus d’informations, consultez [Créer et déployer une stratégie de protection d’application Protection des informations Windows (WIP) avec Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Créer une demande de réinitialisation

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Réinitialisation sélective de l’application** > **Créer une demande de réinitialisation**.<br>
   Le volet **Créer une demande de réinitialisation** s’affiche.
3. Cliquez sur **sélectionner l’utilisateur**, choisissez l’utilisateur dont vous souhaitez réinitialiser les données de l’application, puis cliquez sur **Sélectionner** en bas du volet **Sélectionner un utilisateur**.

    ![Capture d’écran du volet « Sélectionner un utilisateur »](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. Cliquez sur **Sélectionner l’appareil**, choisissez l’appareil, puis cliquez sur **Sélectionner** en bas du volet **Sélectionner l’appareil**.

    ![Capture d’écran du volet « Créer une demande de réinitialisation » où l’appareil est sélectionné](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. Cliquez sur **Créer** pour effectuer une demande de réinitialisation.

Le service crée une demande de réinitialisation distincte pour chaque application protégée sur l’appareil et l’utilisateur associé à la demande de réinitialisation, et en fait le suivi.

   ![Capture d’écran du volet 'Applications clientes - Réinitialisation sélective des applications'](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>Analyser vos demandes de réinitialisation

Vous pouvez obtenir un rapport de synthèse indique l’état global de la demande de réinitialisation et inclut le nombre de demandes en attente et d’échecs. Pour obtenir plus de détails, procédez comme suit :

1. Dans le volet **Applications** > **Réinitialisation sélective des applications**, vous pouvez voir la liste de vos demandes regroupées par utilisateurs. Étant donné que le système crée une demande de réinitialisation pour chaque application protégée en cours d’exécution sur l’appareil, vous pouvez voir plusieurs demandes pour un même utilisateur. L’état de la demande de réinitialisation est indiquée : **en attente**, **échec**ou **réussite**.

    ![Capture d’écran de l’état de demande de réinitialisation dans le volet Réinitialisation sélective des applications](./media/apps-selective-wipe/wipe-request-status-1.png)

En outre, vous pouvez voir le nom de l’appareil et son type, ce qui peut être utile lors de la lecture des rapports.

>[!IMPORTANT]
> L’utilisateur doit ouvrir l’application pour que la réinitialisation se produise. Cette opération peut prendre jusqu’à 30 minutes après l’envoi de la demande.

## <a name="delete-a-wipe-request"></a>Suppression d’une demande de réinitialisation

Les réinitialisations en attente sont affichées jusqu’à ce que vous les supprimiez manuellement. Pour supprimer manuellement une demande de réinitialisation :

1. Dans le volet **Applications clientes - Réinitialisation sélective des applications**.

2. Dans la liste, cliquez avec le bouton droit sur la demande de réinitialisation à supprimer, puis choisissez **Supprimer la demande de réinitialisation**.

    ![Capture d’écran de la liste de demandes de réinitialisation dans le volet Réinitialisation sélective des applications](./media/apps-selective-wipe/delete-wipe-request.png)

3. Vous êtes invité à confirmer la suppression. Choisissez **Oui** ou **Non**, puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
[Qu'est-ce qu'une stratégie de protection d’application](app-protection-policy.md)

[Qu’est-ce que la gestion des applications](app-management.md)
