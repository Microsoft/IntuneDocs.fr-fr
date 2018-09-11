---
title: Introduction à Intune dans le portail Azure
titlesuffix: ''
description: Microsoft Intune est disponible dans le portail Azure. Découvrez les concepts de base d’Intune dans le portail Azure.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: get-started
ms.openlocfilehash: 3f8f0dce416c943dbc244d0e2a4366b12b305708
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253780"
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Introduction à Microsoft Intune dans le portail Azure


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Comme d’autres services Azure, Microsoft Intune est disponible dans le portail Azure. En sélectionnant **Intune** dans le portail Azure, vous pouvez gérer les appareils mobiles, les PC et les applications de votre organisation.

> [!NOTE]
> Si vous avez utilisé une version antérieure de Microsoft Intune, les informations suivantes peuvent vous êtres utiles :
>     * [Où se trouvent mes fonctionnalités dans Azure ?](ui-changes.md) est une référence qui vous montre les flux de travail et interfaces utilisateur spécifiques qui ont été modifiés au cours du passage à Azure.
>     * [Groupes classiques Intune dans le portail Azure](groups-get-started.md) explique les implications du passage aux groupes de sécurité Azure Active Directory pour la gestion des groupes.

Voici quelques points clés de l’expérience Microsoft Intune dans le portail Azure :

- Une console intégrée pour tous vos composants Enterprise Mobility + Security (EMS)
- Une console HTML basée sur les normes web
- Prise en charge de l’API Microsoft Graph pour automatiser de nombreuses actions
- Groupes Azure AD (Active Directory) pour assurer la compatibilité dans toutes vos applications Azure
- Prise en charge des navigateurs web les plus récents

## <a name="before-you-start"></a>Avant de commencer

Pour utiliser Intune dans le portail Azure, vous devez disposer d’un compte d’administration et d’un compte client Intune. [Inscrivez-vous pour obtenir un compte](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) si vous n’en avez pas déjà un.

## <a name="supported-web-browsers-for-the-azure-portal"></a>Navigateurs web pris en charge pour le portail Azure

Le portail Azure s’exécute sur la plupart des PC, Mac et tablettes. Les téléphones mobiles ne sont pas pris en charge.
Actuellement, les navigateurs suivants sont pris en charge :

- Microsoft Edge (dernière version)
- Microsoft Internet Explorer 11
- Safari (dernière version, Mac uniquement)
- Chrome (dernière version)
- Firefox (dernière version)

Pour obtenir les informations les plus récentes sur les navigateurs pris en charge, consultez le [portail Azure](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices).

## <a name="microsoft-intune-in-the-azure-portal"></a>Microsoft Intune dans le portail Azure

Le [portail Azure](https://portal.azure.com) est l’endroit où se trouve le service Microsoft Intune. Il existe plusieurs services dans Azure que vous n’utilisez peut-être pas régulièrement. Pour obtenir un guide rapide afin de personnaliser votre expérience du portail, consultez [Bien démarrer avec Intune dans le portail Azure](get-started-azure.md).

## <a name="the-microsoft-intune-documentation"></a>Documentation de Microsoft Intune

Cette rubrique, ainsi que l’ensemble de la documentation de Microsoft Intune, est régulièrement mise à jour. Si vous avez des suggestions, n’hésitez pas à laisser des commentaires dans la section dédiée de la rubrique. Nous sommes à votre écoute.

La documentation reflète la disposition de Microsoft Intune dans le portail Azure (illustré ci-dessous) pour faciliter la recherche des informations dont vous avez besoin.

![Charges de travail sur le portail Azure](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>Guide de la documentation

Utilisez le tableau suivant pour rapidement rechercher et comprendre les principales zones de Microsoft Intune.

| Section                                                      | Description                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Introduction et prise en main](introduction-intune.md)       | Comprendre les notions de base d’Intune, notamment :<br /> - Solutions courantes<br /> - Fonctionnement de Microsoft Intune<br /> - Gestion des appareils dans Intune<br /> - Gestion des applications dans Intune<br /> - Gestion de la mobilité d’entreprise (EMM, Enterprise Mobility Management) avec et sans inscription d’appareils                                                         |
| [Planifier et concevoir](planning-guide.md)                         | Conseils pour vous aider à planifier et concevoir votre environnement Microsoft Intune.                                                                                                                                                                                                             |
| [Inscription des appareils](device-enrollment.md)                    | Découvrez comment Microsoft Intune vous permet de gérer les appareils de votre personnel en inscrivant les appareils au service Intune. Plusieurs méthodes permettent d’inscrire les appareils de votre personnel.                                                                                                         |
| [Conformité de l’appareil](device-compliance.md)                    | Les stratégies de conformité des appareils Intune définissent les règles et les paramètres auxquels doit se conformer un appareil pour être considéré comme conforme par Microsoft Intune. Voici des exemples de conformité : exiger un mot de passe pour accéder aux appareils, chiffrer les appareils ou exiger une version de système d’exploitation minimale. |
| [Configuration des appareils](device-profiles.md)                   | Configurez les paramètres et fonctionnalités sur tous les appareils que vous gérez à l’aide de Microsoft Intune en créant des profils d’appareil. Par exemple, vous pouvez configurer des fonctionnalités comme les notifications, le partage de données, la prise en charge de la messagerie, la connectivité Wi-Fi, les certificats et Endpoint Protection.              |
| [Appareils](device-management.md)                              | Vérifiez que les appareils gérés fournissent les ressources dont vos utilisateurs finaux ont besoin pour effectuer leur travail, tout en protégeant les données de l’entreprise contre les risques. Gérez les appareils en examinant l’inventaire des appareils du personnel et en effectuant des actions à distance sur l’appareil.                                                      |
| [Applications mobiles](app-management.md)                             | Découvrez comment ajouter, déployer, surveiller, configurer et protéger des applications.                                                                                                                                                                                                                             |
| [Accès conditionnel](conditional-access.md)                  | Définissez des conditions basées sur l’application ou l’appareil pour accéder aux données de l’entreprise.                                                                                                                                                                                                            |
| [Utilisateurs](users-add.md)                                        | Découvrez comment ajouter des utilisateurs pour les appareils et les applications que vous gérez.                                                                                                                                                                                                                                           |
| [Groupes](groups-get-started.md)                              | Découvrez comment créer et gérer des groupes avec Intune. À l’aide de groupes, vous pouvez affecter rapidement une configuration d’appareil et d’application, et des stratégies de protection.                                                                                                                                             |
| [Rôles Intune](role-based-access-control.md)                 | Découvrez comment contrôler les utilisateurs qui peuvent effectuer des actions Intune et comment ces actions s’appliquent. Vous pouvez utiliser les rôles intégrés, qui couvrent des scénarios courants dans Intune, ou vous pouvez créer vos propres rôles.                                                                                 |
| [Mises à jour logicielles](windows-update-for-business-configure.md) | Découvrez comment configurer les mises à jour logicielles pour les appareils Windows 10.                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>Nouveautés

Pour en savoir plus sur les dernières fonctionnalités de Microsoft Intune, consultez [Nouveautés](whats-new.md).
