---
title: Définir des restrictions d’inscription dans Microsoft Intune
titlesuffix: ''
description: Restriction de l’inscription par la plateforme et définition d’une limite d’inscriptions d’appareils dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 76c0b96a1759caad4a1052a7233c7dcc8cecfa3b
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313715"
---
# <a name="set-enrollment-restrictions"></a>Définir des restrictions d’inscription

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez créer et gérer des restrictions d’inscription qui définissent le nombre et les types d’appareils qui peuvent être inscrits en vue d’être gérés par Intune. Vous pouvez créer plusieurs restrictions et les appliquer à différents groupes d’utilisateurs. Vous pouvez définir [l’ordre de priorité](#change-enrollment-restriction-priority) pour vos différentes restrictions.

>[!NOTE]
>Les restrictions d’inscription ne sont pas des fonctionnalités de sécurité. Des appareils compromis peuvent falsifier leur caractère. Ces restrictions représentent une barrière de meilleur effort pour les utilisateurs non malveillants.

Parmi les restrictions d’inscription spécifiques que vous pouvez créer, citons les suivantes :

- Nombre maximal d’appareils inscrits
- Plateformes d’appareils qui peuvent s’inscrire :
  - Android
  - Profil professionnel Android
  - iOS
  - macOS
  - Windows
- Version du système d’exploitation des plateformes pour iOS, Android, Profil professionnel Android et Windows. (Seules les versions de Windows 10 peuvent être utilisées. Laissez ce champ vide si Windows 8.1 est autorisé.)
  - Version minimale
  - Version maximale
- Restreignez les appareils personnels (iOS, Android, Profil professionnel Android, macOS et Windows uniquement).

## <a name="default-restrictions"></a>Restrictions par défaut

Les restrictions par défaut sont automatiquement fournies pour les restrictions d’inscription de type d’appareil et de limite d’appareils. Vous pouvez changer les options pour les valeurs par défaut. Les restrictions par défaut s’appliquent à l’ensemble des inscriptions utilisateur et sans utilisateur. Vous pouvez remplacer ces valeurs par défaut en créant de nouvelles restrictions avec des priorités plus élevées.

## <a name="create-a-restriction"></a>Créer une restriction

1. Connectez-vous au portail Azure.
2. Sélectionnez **Autres services**, recherchez **Intune**, puis choisissez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sélectionnez **Créer une restriction**.
5. Donnez un nom et une description à la restriction.
6. Choisissez un **Type de restriction**, puis sélectionnez **Créer**.
7. Pour les restrictions de limite d’appareils, sélectionnez **Limite d’appareils** pour définir le nombre maximal d’appareils qu’un utilisateur peut inscrire.
8. Pour les restrictions de type d’appareil, sélectionnez **Plateformes** et **Configurations de plateforme** pour autoriser ou bloquer des plateformes et des versions.
9. Sélectionnez **Affectations** > **+ Sélectionner des groupes**.
10. Sous **Sélectionner des groupes**, sélectionnez un ou plusieurs groupes, puis choisissez **Sélectionner**. La restriction s’applique uniquement aux groupes auxquels elle est affectée. Si vous n’affectez pas une restriction à au moins un groupe, elle n’a aucun effet.
11. Sélectionnez **Enregistrer**.
12. La nouvelle restriction est créée avec une priorité juste au-dessus de la valeur par défaut. Vous pouvez [changer la priorité](#change-enrollment-restriction-priority).

## <a name="set-device-type-restrictions"></a>Définition des restrictions de type d'appareil

Pour changer les paramètres d’une restriction de type d’appareil, effectuez les étapes ci-dessous. Ces restrictions n’ont pas d’effet sur les appareils qui ont déjà été inscrits. Les appareils inscrits avec [l’agent de PC Intune](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune.md) ne peuvent pas être bloqués avec cette fonctionnalité.

1. Connectez-vous au portail Azure.
2. Sélectionnez **Autres services**, recherchez **Intune**, puis choisissez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **Restrictions de type d’appareil** > choisissez la restriction à définir > **Propriétés** > **.Sélectionner des plateformes**. Choisissez **Autoriser** ou **Bloquer** pour chaque plateforme répertoriée.
    ![Capture d’écran : Autoriser ou bloquer une plateforme](media/enrollment-restrictions-set/platform-allow-block.png)
5. Choisissez **OK**.
6. Choisissez **Configurer des plateformes**.
    ![Capture d’écran : Configurer des plateformes](media/enrollment-restrictions-set/configure-platforms.png)
7. Choisissez les **Versions** minimale et maximale pour les plateformes listées. Les formats de version pris en charge sont notamment :
    - Profil professionnel Android prend en charge majeur.mineur.révision.build.
    - iOS prend en charge major.minor.rev. Les versions du système d’exploitation ne s’appliquent pas aux appareils Apple inscrits par le biais du Programme d’inscription des appareils, d’Apple School Manager ou de l’application Apple Configurator.
    - Windows prend en charge major.minor.rev.build pour Windows 10 uniquement.
8. Choisissez s’il faut **Autoriser** ou **Bloquer** les appareils **personnels** pour chaque plateforme listée.
9. Choisissez **OK**.

### <a name="android-device-type-restrictions"></a>Restrictions des types d’appareils Android
- Si vous bloquez l’inscription des appareils Android personnels, les appareils avec profil professionnel Android personnels peuvent quand même être inscrits.
- Par défaut, les paramètres de vos appareils avec profil professionnel Android sont identiques à ceux de vos appareils Android. Ce ne sera plus le cas une fois que vous aurez modifié vos paramètres de profil professionnel Android.
- Si vous bloquez l’inscription du profil professionnel Android personnel, seuls les appareils Android d’entreprise peuvent s’inscrire en tant que profil professionnel Android.

### <a name="windows-device-type-restrictions"></a>Restrictions des types d’appareils Windows
Une fois que la restriction des types d’appareils Windows est définie sur **Bloquer**, Intune vérifie que chaque nouvelle demande d’inscription Windows a été autorisée comme inscription d’entreprise. Les inscriptions non autorisées seront bloquées.

Les méthodes suivantes sont qualifiées comme étant autorisées en tant qu’inscription d’entreprise Windows :
 - L’utilisateur qui s’inscrit utilise un [compte de gestionnaire d’inscription d’appareil]( device-enrollment-manager-enroll.md).
- L’appareil s’inscrit via [Windows AutoPilot](enrollment-autopilot.md).
- Le numéro IMEI de l’appareil est listé dans **Inscription de l’appareil** > **[Identificateurs d’appareil d’entreprise](corporate-identifiers-add.md)**. (Non pris en charge pour Windows Phone 8.1)
- L’appareil s’inscrit via un [package de provisionnement en bloc](windows-bulk-enroll.md).
- L’appareil s’inscrit via [l’inscription automatique à partir de SCCM pour la cogestion](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md).
 
Les inscriptions suivantes sont marquées comme étant d’entreprise par Intune mais, dans la mesure où elles n’offrent pas le contrôle par appareil d’administrateur Intune, elles seront bloquées :
 - [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [jonction Azure Active Directory lors de la configuration de Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
- [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [jonction Azure Active Directory à partir des paramètres Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-setup.md).
 
Les méthodes d’inscription personnelle suivantes seront également bloquées :
- [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [Ajouter un compte professionnel à partir de Paramètres Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-registered-devices-windows10-setup.md).
- Option [Inscription à MDM uniquement]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) à partir de Paramètres Windows.


## <a name="set-device-limit-restrictions"></a>Définition des restrictions de limite d'appareil

Pour changer les paramètres d’une restriction de limite d’appareils, effectuez les étapes suivantes :

1. Connectez-vous au portail Azure.
2. Sélectionnez **Autres services**, recherchez **Intune**, puis choisissez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **Restrictions de type d’appareils**, choisissez la restriction à définir.
5. Sélectionnez **Limite d’appareils** puis, dans la liste déroulante, sélectionnez le nombre maximal d’appareils qu’un utilisateur peut inscrire.
    ![Panneau des restrictions de limite d’appareils avec les restrictions de limite d’appareils](./media/device-restrictions-limit.png)
6. Sélectionnez **Enregistrer**.


Les utilisateurs reçoivent une notification qui leur indique qu’ils ont atteint le nombre limite d’appareils inscrits. Par exemple, sur iOS, la notification ressemble à ce qui suit :

![Notification du nombre limite d’appareils iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>Changer la priorité des restrictions d’inscription

Une priorité est utilisée quand un utilisateur existe dans plusieurs groupes auxquels des restrictions sont affectées. Les utilisateurs sont uniquement soumis à la restriction avec la priorité le plus élevée affectée à un groupe dans lequel ils se trouvent. Par exemple, Jean est dans un groupe A affecté à des restrictions de priorité 5 et aussi dans un groupe B affecté à des restrictions de priorité 2. Jean n’est soumis qu’aux restrictions de priorité 2.

Quand vous créez une restriction, elle est ajoutée à la liste juste au-dessus de la valeur par défaut.

L’inscription d’appareil inclut les restrictions par défaut pour les restrictions de type d’appareil et de limite d’appareils. Ces deux restrictions s’appliquent à tous les utilisateurs, sauf si elles sont remplacées par des restrictions avec une priorité plus élevée.

Vous pouvez changer la priorité d’une restriction différente de celle par défaut.

1. Connectez-vous au portail Azure.
2. Sélectionnez **Autres services**, recherchez **Intune**, puis choisissez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Pointez sur la restriction dans la liste des priorités.
5. À l’aide des trois points verticaux, faites glisser la priorité à la position souhaitée dans la liste.
