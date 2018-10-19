---
title: Démarrage rapide - Configurer l’inscription automatique dans Intune
description: Démarrage rapide - Configurer l’inscription automatique pour les appareils Windows 10 dans Intune.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581575"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>Démarrage rapide : Configurer l’inscription automatique pour les appareils Windows 10

Dans ce guide de démarrage rapide, vous allez configurer Microsoft Intune pour inscrire automatiquement les appareils quand des utilisateurs spécifiques se connectent à des appareils Windows 10.

Si vous n’avez pas d’abonnement Intune, [inscrivez-vous à un compte d’essai gratuit](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prérequis

- Pour effectuer les opérations décrites dans ce guide de démarrage rapide, vous devez d’abord [créer un utilisateur](quickstart-create-user.md) et [créer un groupe](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Se connecter à Intune

Connectez-vous à [Intune](https://aka.ms/intuneportal) en tant qu’administrateur général ou en tant qu’administrateur de services fédérés Intune.

## <a name="set-up-windows-10-automatic-enrollment"></a>Configurer l’inscription automatique Windows 10

Pour cet exemple, vous allez utiliser l’inscription MDM afin de permettre l’inscription automatique des appareils d’entreprise et des appareils BYOD (Apportez votre propre appareil).

1. Dans Azure, choisissez **Azure Active Directory** > **Mobilité (gestion des données de référence et gestion des applications mobiles)** > **Microsoft Intune** > **Certain(e)s**.
![Navigateur](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. Choisissez **Sélectionner des groupes** > **Testeurs Contoso** > **Sélectionner**.
3. Utilisez les valeurs par défaut pour les URL suivantes :
    - URL des conditions d’utilisation de MDM
    - URL de détection MDM
    - URL de conformité de MDM
4. Choisissez **Enregistrer**.
5. Connectez-vous en tant qu’utilisateur du groupe sur un appareil Windows 10, puis suivez les instructions.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Pour reconfigurer l’inscription automatique à Intune, consultez [Configurer l’inscription d’appareils Windows](windows-enroll.md).

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à configurer l’inscription automatique pour des appareils Windows 10. Vous pouvez découvrir d’autres moyens d’inscrire des appareils sur toutes les plateformes.

> [!div class="nextstepaction"]
> [Article Qu’est-ce que l’inscription d’appareils ?](device-enrollment.md)