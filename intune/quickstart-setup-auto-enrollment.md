---
title: Démarrage rapide - Configurer l’inscription automatique dans Intune
description: Démarrage rapide - Configurer l’inscription automatique pour les appareils Windows 10 dans Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b81525034f69b43abeb60f562e4d6ee6a46b866
ms.sourcegitcommit: d38ca1bf44e17211097aea481e00b6c1e87effae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514278"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Démarrage rapide : Configurer l’inscription automatique pour les appareils Windows 10

Dans ce guide de démarrage rapide, vous allez configurer Microsoft Intune pour inscrire automatiquement les appareils quand des utilisateurs spécifiques se connectent à des appareils Windows 10.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

- Abonnement Microsoft Intune : [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).
- Pour effectuer les opérations décrites dans ce guide de démarrage rapide, vous devez d’abord [créer un utilisateur](quickstart-create-user.md) et [créer un groupe](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune. Si vous avez créé un abonnement d’essai Intune, le compte utilisé à cette fin est l’administrateur général.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurer l’inscription automatique Windows 10

Dans cet exemple, vous allez utiliser l’inscription à MDM pour inscrire automatiquement les appareils d’entreprise et les appareils BYOD (Apportez votre propre appareil). Vous vous inscrirez à un abonnement Azure Active Directory Premium gratuit.

1. Dans Azure, choisissez **Azure Active Directory** > **Mobility (MDM et MAM)**.
2. Sélectionnez **Obtenir une version d’évaluation Premium gratuite pour utiliser cette fonctionnalité**. Cette option permet l’inscription automatique avec l’essai gratuit d’Azure Active Directory Premium. 

    ![Sélectionner l’essai gratuit d’Azure Active Directory Premium](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    Choisissez l’option d’essai gratuit **Enterprise Mobility + Security E5**. Vous devez aussi **activer** l’essai gratuit.

    ![Choisir l’option d’essai gratuit Enterprise Mobility + Security E5](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. Sélectionnez **Microsoft Intune**. 

    ![Choisir Microsoft Intune dans la liste](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. Sélectionnez **Certains** dans **Portée de l’utilisateur GDR** pour utiliser l’inscription automatique à MDM et gérer les données d’entreprise sur les appareils Windows de votre personnel. L’inscription automatique à MDM sera configurée pour les appareils joints à AAD et les scénarios d’appareils BYOD (Apportez votre propre appareil).

    ![Sélectionner « Certains » dans la liste Configurer](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. Choisissez **Sélectionner des groupes** > **Testeurs Contoso** > **Sélectionner** comme groupe attribué.

    ![Sélectionner le groupe à inscrire](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. Sélectionnez **Certains** dans **Portée de l’utilisateur Gestion des applications mobiles** pour gérer les données sur les appareils de votre personnel.
7. Choisissez **Sélectionner des groupes** > **Testeurs Contoso** > **Sélectionner** comme groupe attribué. 
8. Utilisez les valeurs par défaut pour les options de configuration restantes.
9. Choisissez **Enregistrer**.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Pour reconfigurer l’inscription automatique à Intune, consultez [Configurer l’inscription d’appareils Windows](windows-enroll.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à configurer l’inscription automatique pour des appareils Windows 10. Pour plus d’informations sur l’inscription des appareils, consultez [Qu’est-ce que l’inscription d’appareils ?](device-enrollment.md)

Pour continuer cette série de guides de démarrage rapide Intune, passez au suivant.

> [!div class="nextstepaction"]
> [Démarrage rapide : Inscrire votre appareil Windows 10](quickstart-enroll-windows-device.md)
