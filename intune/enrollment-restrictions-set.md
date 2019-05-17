---
title: Définir des restrictions d’inscription dans Microsoft Intune
titleSuffix: ''
description: Restriction de l’inscription par la plateforme et définition d’une limite d’inscriptions d’appareils dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/17/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1080ae8a73223ad16445d0d2233434faa818b04b
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569114"
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
  - Windows Mobile
- Version du système d’exploitation des plateformes pour iOS, Android, Profil professionnel Android , Windows et Windows Mobile. (Seules les versions de Windows 10 peuvent être utilisées. Laissez ce champ vide si Windows 8.1 est autorisé.)
  - Version minimale
  - Version maximale
- Restreignez les appareils personnels (iOS, Android, Profil professionnel Android, macOS, Windows et Windows Mobile uniquement).

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

Pour changer les paramètres d’une restriction de type d’appareil, effectuez les étapes ci-dessous. Ces restrictions n’ont pas d’effet sur les appareils qui ont déjà été inscrits. Les appareils inscrits avec [l’agent de PC Intune](manage-windows-pcs-with-microsoft-intune.md) ne peuvent pas être bloqués avec cette fonctionnalité.

1. Connectez-vous au portail Azure.
2. Sélectionnez **Autres services**, recherchez **Intune**, puis choisissez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **Restrictions de type d’appareil**, choisissez la restriction à définir > **Propriétés** > **Sélectionner des plateformes**. Choisissez **Autoriser** ou **Bloquer** pour chaque plateforme répertoriée.
    ![Capture d’écran : Autoriser ou bloquer une plateforme](media/enrollment-restrictions-set/platform-allow-block.png)
5. Choisissez **OK**.
6. Choisissez **Configurer des plateformes**.
    ![Capture d’écran : Configurer des plateformes](media/enrollment-restrictions-set/configure-platforms.png)
7. Choisissez les **Versions** minimale et maximale pour les plateformes listées. Les formats de version pris en charge sont notamment :
    - Profil professionnel Android prend en charge majeur.mineur.révision.build.
    - iOS prend en charge major.minor.rev. Les versions du système d’exploitation ne s’appliquent pas aux appareils Apple inscrits par le biais du Programme d’inscription des appareils, d’Apple School Manager ou de l’application Apple Configurator.
    - Windows prend en charge major.minor.rev.build pour Windows 10 uniquement.
> [!Note]
> Windows 10 ne fournit pas le numéro de build au cours de l’inscription. Par conséquent, si vous entrez par exemple 10.0.17134.100 et que l’appareil correspond à 10.0.17134.174, il est bloqué lors de l’inscription.
8. Choisissez s’il faut **Autoriser** ou **Bloquer** les appareils **personnels** pour chaque plateforme listée.
9. Choisissez **OK**.

### <a name="blocking-personal-android-devices"></a>Blocage des appareils Android personnels
- Si vous bloquez l’inscription des appareils Android personnels, les appareils avec profil professionnel Android personnels peuvent quand même être inscrits.
- Par défaut, les paramètres de vos appareils avec profil professionnel Android sont identiques à ceux de vos appareils Android. Ce ne sera plus le cas une fois que vous aurez modifié vos paramètres de profil professionnel Android.
- Si vous bloquez l’inscription du profil professionnel Android personnel, seuls les appareils Android d’entreprise peuvent s’inscrire en tant que profil professionnel Android.

### <a name="blocking-personal-windows-devices"></a>Blocage des appareils Windows personnels
Si vous bloquez l’inscription d’appareils Windows personnels, Intune vérifie que chaque nouvelle demande d’inscription Windows est autorisée en tant qu’inscription d’entreprise. Les inscriptions non autorisées seront bloquées.

Les méthodes suivantes sont qualifiées comme étant autorisées en tant qu’inscription d’entreprise Windows :
 - L’utilisateur qui s’inscrit utilise un [compte de gestionnaire d’inscription d’appareil]( device-enrollment-manager-enroll.md).
- L’appareil s’inscrit via [Windows AutoPilot](enrollment-autopilot.md).
- L’appareil est inscrit auprès de Windows Autopilot mais cela ne représente pas la seule option d’inscription MDM dans les paramètres Windows.
- Le numéro IMEI de l’appareil est listé dans **Inscription de l’appareil** > **[Identificateurs d’appareil d’entreprise](corporate-identifiers-add.md)**. (Non pris en charge pour Windows Phone 8.1)
- L’appareil s’inscrit via un [package de provisionnement en bloc](windows-bulk-enroll.md).
- L’appareil s’inscrit avec un objet de stratégie de groupe ou par [inscription automatique à partir de SCCM pour la cogestion](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management.md).
 
Les inscriptions suivantes sont marquées comme étant d’entreprise par Intune. Mais dans la mesure où elles ne permettent pas à l’administrateur Intune de contrôler par appareil, elles seront bloquées :
 - [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [jonction Azure Active Directory durant la configuration de Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [jonction Azure Active Directory à partir des paramètres Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Les méthodes d’inscription personnelle suivantes seront également bloquées :
- [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [ajout de compte professionnel à partir des paramètres Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Option [Inscription à MDM uniquement]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) à partir de Paramètres Windows.

\* Ces appareils ne sont pas bloqués s’ils sont inscrits auprès d’Autopilot.

## <a name="set-device-limit-restrictions"></a>Définition des restrictions de limite d'appareil

Pour changer les paramètres d’une restriction de limite d’appareils, effectuez les étapes suivantes :

1. Connectez-vous au portail Azure.
2. Sélectionnez **Autres services**, recherchez **Intune**, puis choisissez **Intune**.
3. Sélectionnez **Inscription de l’appareil** > **Restrictions d’inscription**.
4. Sous **Restrictions de type d’appareils**, choisissez la restriction à définir.
5. Sélectionnez **Limite d’appareils** puis, dans la liste déroulante, sélectionnez le nombre maximal d’appareils qu’un utilisateur peut inscrire.
    ![Panneau des restrictions de limite d’appareils avec les restrictions de limite d’appareils](./media/device-restrictions-limit.png)
6. Sélectionnez **Enregistrer**.


Durant des inscriptions BYOD, les utilisateurs reçoivent une notification qui les informe qu’ils ont atteint le nombre limite d’appareils inscrits. Par exemple, sur iOS :

![Notification du nombre limite d’appareils iOS](./media/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> Les restrictions de limite d’appareil ne s’appliquent pour les types d’inscription Windows suivants :
> - Inscriptions cogérées
> - Inscriptions GPO
> - Inscriptions jointes Azure Active Directory
> - Inscriptions jointes Azure Active Directory en bloc
> - Inscriptions Autopilot
>
> Les restrictions de limite d’appareil ne s’appliquent pas à ces types d’inscription car ils sont considérés comme des scénarios d’appareil partagé.
> Vous pouvez définir des limites strictes pour ces types d’inscription [dans Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).

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
