---
title: Démarrage rapide - Configurer l’inscription automatique dans Intune
description: Démarrage rapide - Configurer l’inscription automatique pour les appareils Windows 10 dans Intune.
services: microsoft-intune
author: ErikjeMS
manager: dougeby
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 01/17/2020
ms.author: erikje
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5cc7cf3661caa2b2640d9370d26402b7702d36b
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541024"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Démarrage rapide : Configurer l’inscription automatique pour les appareils Windows 10

Dans ce guide de démarrage rapide, vous allez configurer Microsoft Intune pour inscrire automatiquement les appareils quand des utilisateurs spécifiques se connectent à des appareils Windows 10.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

- Abonnement Microsoft Intune : [inscrivez-vous à un compte d’essai gratuit](../fundamentals/free-trial-sign-up.md).
- Pour effectuer les opérations décrites dans ce guide de démarrage rapide, vous devez d’abord [créer un utilisateur](../fundamentals/quickstart-create-user.md) et [créer un groupe](../fundamentals/quickstart-create-group.md).

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Connectez-vous à Intune au Gestionnaire de points de terminaison Microsoft

Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) comme Administrateur général ou Administrateur de service Intune. Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurer l’inscription automatique Windows 10

Dans cet exemple, vous allez utiliser l’inscription à MDM pour inscrire automatiquement les appareils d’entreprise et les appareils BYOD (Apportez votre propre appareil). Vous vous inscrirez à un abonnement Azure Active Directory Premium gratuit.

1. Dans le [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), choisissez **Tous les services** > **M365 Azure Active Directory** > **Azure Active Directory** > **Mobilité (MDM et GAM)** .
2. Sélectionnez **Obtenir une version d’évaluation Premium gratuite pour utiliser cette fonctionnalité**. Cette option permet l’inscription automatique avec l’essai gratuit d’Azure Active Directory Premium. 

    ![Sélectionner l’essai gratuit d’Azure Active Directory Premium](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

3. Choisissez l’option d’essai gratuit **Enterprise Mobility + Security E5**. 
4. Cliquez sur **Essai gratuit** > **Activer** l'essai gratuit.

    ![Choisir l’option d’essai gratuit Enterprise Mobility + Security E5](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

    > [!NOTE]
    > L'activation peut prendre une minute. 

3. Sélectionnez **Microsoft Intune** pour configurer Intune. 

    ![Choisir Microsoft Intune dans la liste](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Sélectionnez **Certains** dans **Portée de l’utilisateur GDR** pour utiliser l’inscription automatique à MDM et gérer les données d’entreprise sur les appareils Windows de votre personnel. L’inscription automatique à MDM sera configurée pour les appareils joints à AAD et les scénarios d’appareils BYOD (Apportez votre propre appareil).

    ![Sélectionner « Certains » dans la liste Configurer](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Cliquez sur **Sélectionner des groupes** > **Testeurs Contoso** > **Sélectionner** comme groupe attribué.

    ![Sélectionner le groupe à inscrire](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Sélectionnez **Certains** dans **Portée de l’utilisateur Gestion des applications mobiles** pour gérer les données sur les appareils de votre personnel.

    ![Sélectionner le groupe à inscrire](./media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-06.png)

7. Choisissez **Sélectionner des groupes** > **Testeurs Contoso** > **Sélectionner** comme groupe attribué. 
8. Utilisez les valeurs par défaut pour les options de configuration restantes.
9. Choisissez **Enregistrer**.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Pour reconfigurer l’inscription automatique à Intune, consultez [Configurer l’inscription d’appareils Windows](windows-enroll.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à configurer l’inscription automatique pour des appareils Windows 10. Pour plus d’informations sur l’inscription des appareils, consultez [Qu’est-ce que l’inscription d’appareils ?](device-enrollment.md)

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Inscrire votre appareil Windows 10](../quickstart-enroll-windows-device.md)
