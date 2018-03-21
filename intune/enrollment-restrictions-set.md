---
title: "Définir des restrictions d’inscription dans Microsoft Intune"
titlesuffix: 
description: "Restriction de l’inscription par la plateforme et définition d’une limite d’inscriptions d’appareils dans Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6466d62cf8af4e6b8a14980db5e9a244deb45c4
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="set-enrollment-restrictions"></a>Définir des restrictions d’inscription

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez créer et gérer des restrictions d’inscription. Ces restrictions définissent le nombre et le type des appareils qui peuvent s’inscrire à la gestion Intune. Vous pouvez créer plusieurs restrictions et les appliquer à différents groupes d’utilisateurs. Vous pouvez définir [l’ordre de priorité](#change-enrollment-restriction-priority) pour vos différentes restrictions.

>[!NOTE]
>Les restrictions d’inscription ne sont pas des fonctionnalités de sécurité. Des appareils compromis peuvent falsifier leur caractère. Ces restrictions représentent une barrière de meilleur effort pour les utilisateurs non malveillants.

>[!NOTE]
>Les fonctionnalités de priorité et de restriction d’inscription appliquées aux groupes et mentionnées ci-dessous sont en cours de déploiement parmi la clientèle Intune. Tant que ce déploiement ne sera pas terminé, vous n’aurez peut-être pas accès aux fonctionnalités de groupe et de priorité.

Parmi les restrictions d’inscription spécifiques que vous pouvez créer, citons les suivantes :

- Nombre maximal d’appareils inscrits
- Plateformes d’appareils qui peuvent s’inscrire :
  - Android
  - Android for Work
  - iOS
  - macOS
  - Windows
- Version de système d’exploitation de plateforme pour iOS, Android, Android for Work et Windows (seules les versions Windows 10 peuvent être utilisées ; laissez ce champ vide si Windows 8.1 est autorisé)
  - Version minimale
  - Version maximale
- Restreindre les appareils personnels (iOS, Android, Android for Work, macOS uniquement)

## <a name="default-restrictions"></a>Restrictions par défaut

Les restrictions par défaut sont automatiquement fournies pour les restrictions d’inscription de type d’appareil et de limite d’appareils. Vous pouvez changer les options pour les valeurs par défaut. Les restrictions par défaut s’appliquent à l’ensemble des inscriptions utilisateur et sans utilisateur. Vous pouvez remplacer ces valeurs par défaut en créant de nouvelles restrictions avec des priorités plus élevées.

## <a name="create-a-restriction"></a>Créer une restriction

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Monitoring + Gestion**.
3. Choisissez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Choisissez **Créer une restriction**.
5. Donnez un nom et une description à la restriction.
6. Choisissez un **Type de Restriction**, puis cliquez sur **Créer**.
7. Pour les restrictions de limite d’appareils, cliquez sur **Limite d’appareils** pour définir le nombre maximal d’appareils qu’un utilisateur peut inscrire.
8. Pour les restrictions de type d’appareil, cliquez sur **Plateformes** et **Configurations de plateforme** pour autoriser ou bloquer des plateformes et des versions.
9. Cliquez sur **Affectations** > **+ Sélectionner des groupes**.
10. Sous **Sélectionner des groupes**, sélectionnez un ou plusieurs groupes, puis cliquez sur **Sélectionner**. La restriction s’applique uniquement aux groupes auxquels elle est affectée. Si vous n’affectez pas une restriction à au moins un groupe, elle n’a aucun effet.
11. Cliquez sur **Save**.
12. La nouvelle restriction est créée avec une priorité juste au-dessus de la valeur par défaut. Vous pouvez [changer la priorité](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Définition des restrictions de type d'appareil

Pour changer les paramètres d’une restriction de type d’appareil, effectuez les étapes suivantes :

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Monitoring + Gestion**.
3. Choisissez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **Restrictions de type d’appareil**, choisissez la restriction à définir.
5. Sous le nom de la restriction (**Tous les utilisateurs** pour la restriction par défaut), sélectionnez **Plateformes**. Choisissez **Autoriser** ou **Bloquer** pour chaque plateforme répertoriée.
6. Cliquez sur **Save**.
7. Sous le nom de la restriction (**Tous les utilisateurs** pour la restriction par défaut), sélectionnez **Configurations de plateforme** et sélectionnez les **Versions** minimale et maximale pour les plateformes répertoriées. Les versions prises en charge incluent les suivantes :
  - Android et Android for Work prennent en charge major.minor.rev.build.
  - iOS prend en charge major.minor.rev.
  - Windows prend en charge major.minor.rev.build pour Windows 10 uniquement.
  Les versions du système d’exploitation ne s’appliquent pas aux appareils Apple inscrits par le biais du Programme d’inscription des appareils, d’Apple School Manager ou de l’application Apple Configurator.
6. Spécifiez s’il faut **Autoriser** ou **Bloquer** les appareils **personnels** pour chaque plateforme répertoriée.

    ![Capture d’écran de l’espace de travail de restrictions des appareils avec la plateforme d’appareil par défaut configurée pour les appareils personnels](media/device-restrictions-platform-configurations.png)
7. Cliquez sur **Save**.

>[!NOTE]
>- Si vous bloquez l’inscription des appareils Android personnels, les appareils Android for Work personnels peuvent quand même être inscrits.
>- Par défaut, les paramètres de vos appareils Android for Work seront identiques aux paramètres de vos appareils Android. Toutefois, ce ne sera plus le cas une fois que vous aurez modifié vos paramètres Android for Work.
>- Si vous bloquez l’inscription Android for Work personnelle, seuls les appareils Android d’entreprise peuvent s’inscrire en tant qu’Android for Work.

## <a name="set-device-limit-restrictions"></a>Définition des restrictions de limite d'appareil

Pour changer les paramètres d’une restriction de limite d’appareils, effectuez les étapes suivantes :

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Monitoring + Gestion**.
3. Choisissez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **Restrictions de type d’appareils**, choisissez la restriction à définir.
5. Choisissez **Limite d’appareils** puis, dans la liste déroulante, sélectionnez le nombre maximal d’appareils qu’un utilisateur peut inscrire.
    ![Capture d’écran du panneau des restrictions du nombre limite d’appareils](./media/device-restrictions-limit.png)
4. Cliquez sur **Save**.

Votre utilisateur final reçoit une notification qui lui indique qu’il a atteint le nombre limite d’appareils inscrits. Par exemple, sur iOS, la notification ressemble à ce qui suit :

![Capture d’écran de la notification du nombre limite d’appareils iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Changer la priorité des restrictions d’inscription

Une priorité est utilisée quand un utilisateur existe dans plusieurs groupes auxquels des restrictions sont affectées. Les utilisateurs sont uniquement soumis à la restriction avec la priorité le plus élevée affectée à un groupe dans lequel ils se trouvent. Par exemple, Jean est dans un groupe A affecté à des restrictions de priorité 5 et dans un groupe B affecté à des restrictions de priorité 2. Jean n’est soumis qu’aux restrictions de priorité 2.

Quand vous créez une restriction, elle est ajoutée à la liste juste au-dessus de la valeur par défaut.

L’inscription d’appareil inclut les restrictions par défaut pour les restrictions de type d’appareil et de limite d’appareils. Ces deux restrictions s’appliquent à tous les utilisateurs, sauf si elles sont remplacées par des restrictions avec une priorité plus élevée.

Vous pouvez changer la priorité d’une restriction différente de celle par défaut.

**Pour changer la priorité d’une restriction**

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Monitoring + Gestion**.
3. Choisissez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Pointez sur la restriction dans la liste des priorités.
5. À l’aide des trois points verticaux sur la gauche, glissez la priorité dans la position désirée dans la liste.
