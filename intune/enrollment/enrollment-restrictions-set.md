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
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4246dab0cf22053d76fdd50f99de53e827332a23
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547816"
---
# <a name="set-enrollment-restrictions"></a>Définir des restrictions d’inscription

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En tant qu’administrateur Intune, vous pouvez créer et gérer des restrictions d’inscription qui définissent quels appareils peuvent être inscrits en vue d’être gérés par Intune, notamment :
- Le nombre d’appareils.
- Les systèmes d’exploitation et les versions.

Vous pouvez créer plusieurs restrictions et les appliquer à différents groupes d’utilisateurs. Vous pouvez définir [l’ordre de priorité](#change-enrollment-restriction-priority) pour vos différentes restrictions.

>[!NOTE]
>Les restrictions d’inscription ne sont pas des fonctionnalités de sécurité. Des appareils compromis peuvent falsifier leur caractère. Ces restrictions représentent une barrière de meilleur effort pour les utilisateurs non malveillants.

Parmi les restrictions d’inscription spécifiques que vous pouvez créer, citons les suivantes :

- Nombre maximal d’appareils inscrits
- Plateformes d’appareils qui peuvent s’inscrire :
  - Administrateur d’appareil Android
  - Profil professionnel Android Entreprise
  - iOS
  - macOS
  - Windows
  - Windows Mobile
- Version du système d’exploitation des plateformes pour iOS, administrateur d’appareil Android, profil professionnel Android Entreprise, Windows et Windows Mobile. (Seules les versions de Windows 10 peuvent être utilisées. Laissez ce champ vide si Windows 8.1 est autorisé.)
  - Version minimale
  - Version maximale
- Restreignez les [appareils personnels](device-enrollment.md#bring-your-own-device) (iOS, administrateur d’appareil Android, profil professionnel Android Entreprise, macOS, Windows et Windows Mobile uniquement).

## <a name="default-restrictions"></a>Restrictions par défaut

Les restrictions par défaut sont automatiquement fournies pour les restrictions d’inscription de type d’appareil et de limite d’appareils. Vous pouvez changer les options pour les valeurs par défaut. Les restrictions par défaut s’appliquent à l’ensemble des inscriptions utilisateur et sans utilisateur. Vous pouvez remplacer ces valeurs par défaut en créant de nouvelles restrictions avec des priorités plus élevées.

## <a name="create-a-device-type-restriction"></a>Créer une restriction de type d’appareil

1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Appareils** > **Restrictions d’inscription** > **Créer une restriction** > **Restriction du type d’appareil**.
2. Sur la page **Informations de base**, donnez un **Nom** à la restriction, ainsi qu’une **Description** facultative.
3. Choisissez **Suivant** pour atteindre la page **Paramètres de la plateforme**.
4. Sous **Plateforme**, choisissez **Autoriser** pour les plateformes qui doivent autoriser cette restriction.
    ![Capture d’écran du choix des paramètres de plateforme](./media/enrollment-restrictions-set/choose-platform-settings.png)
5. Sous **Versions**, sélectionnez les versions minimale et maximale que vous souhaitez que les plateformes autorisées prennent en charge. Les restrictions de version s’appliquent uniquement aux appareils inscrits avec le Portail d’entreprise.
     Les formats de version pris en charge sont notamment :
    - L’administrateur d’appareil Android et le profil professionnel Android Entreprise prennent en charge major.minor.rev.build.
    - iOS prend en charge major.minor.rev. Les versions du système d’exploitation ne s’appliquent pas aux appareils Apple inscrits par le biais du Programme d’inscription des appareils, d’Apple School Manager ou de l’application Apple Configurator.
    - Windows prend en charge major.minor.build.rev pour Windows 10 uniquement.
    
    > [!IMPORTANT]
    > Les plateformes Android Entreprise (profil professionnel) et Administrateur d’appareil Android présentent le comportement suivant :
    > - Si les deux plateformes sont autorisées pour le même groupe, les utilisateurs sont inscrits avec un profil professionnel si leur appareil le prend en charge, sinon ils sont inscrits en tant qu’administrateur d’appareil. 
    > - Si les deux plateformes sont autorisées pour le groupe et affinées pour des versions spécifiques ne se chevauchant pas, les utilisateurs reçoivent le flux d’inscription défini pour leur version du système d’exploitation. 
    > - Si les deux plateformes sont autorisées, mais bloquées pour les mêmes versions, les utilisateurs sur les appareils avec les versions bloquées sont descendus jusqu’au flux d’inscription de l’administrateur d’appareil Android, puis voient leur inscription bloquée et sont invités à se déconnecter. 
    >
    > Notez que ni le profil professionnel, ni l’inscription de l’administrateur d’appareil ne fonctionneront, à moins d’avoir respecté les prérequis appropriés dans l’inscription Android. 
    
   > [!Note]
   > Windows 10 ne fournit pas le numéro de rev au cours de l’inscription. Par conséquent, si vous entrez par exemple 10.0.17134.100 et que l’appareil correspond à 10.0.17134.174, il est bloqué lors de l’inscription.

6. Sous **Appareils personnels**, choisissez **Autoriser** pour les plateformes que vous souhaitez autoriser comme appareils personnels.
7. Choisissez **Suivant** pour accéder à la page **Attributions**.
8. Choisissez **Sélectionner les groupes à inclure**, puis utilisez la zone de recherche pour rechercher les groupes que vous souhaitez inclure dans cette restriction. La restriction s’applique uniquement aux groupes auxquels elle est affectée. Si vous n’affectez pas une restriction à au moins un groupe, elle n’a aucun effet. Choisissez ensuite **Sélectionner**. 
    ![Capture d’écran du choix des paramètres de plateforme](./media/enrollment-restrictions-set/select-groups.png)
9. Sélectionnez **Suivant** pour accéder à la page **Vérifier + créer**.
10. Sélectionnez **Créer** pour créer la restriction.
11. La nouvelle restriction est créée avec une priorité juste au-dessus de la valeur par défaut. Vous pouvez [changer la priorité](#change-enrollment-restriction-priority).


## <a name="create-a-device-limit-restriction"></a>Créer une restriction de limite d’appareils

1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Appareils** > **Restrictions d’inscription** > **Créer une restriction** > **Restriction du nombre limite d’appareils**.
2. Sur la page **Informations de base**, donnez un **Nom** à la restriction, ainsi qu’une **Description** facultative.
3. Choisissez **Suivant** pour accéder à la page **Limite d’appareils**.
4. Sélectionnez le nombre maximal d’appareils qu’un utilisateur peut inscrire sous **Limite d’appareils**.
    ![Capture d’écran du choix de la limite d’appareils](./media/enrollment-restrictions-set/choose-device-limit.png)
5. Choisissez **Suivant** pour accéder à la page **Attributions**.
6. Choisissez **Sélectionner les groupes à inclure**, puis utilisez la zone de recherche pour rechercher les groupes que vous souhaitez inclure dans cette restriction. La restriction s’applique uniquement aux groupes auxquels elle est affectée. Si vous n’affectez pas une restriction à au moins un groupe, elle n’a aucun effet. Choisissez ensuite **Sélectionner**. 
    ![Capture d’écran de la sélection des groupes](./media/enrollment-restrictions-set/select-groups-device-limit.png)
7. Sélectionnez **Suivant** pour accéder à la page **Vérifier + créer**.
8. Sélectionnez **Créer** pour créer la restriction.
9. La nouvelle restriction est créée avec une priorité juste au-dessus de la valeur par défaut. Vous pouvez [changer la priorité](#change-enrollment-restriction-priority).

Durant des inscriptions BYOD, les utilisateurs reçoivent une notification qui les informe qu’ils ont atteint le nombre limite d’appareils inscrits. Par exemple, sur iOS :

![Notification du nombre limite d’appareils iOS](./media/enrollment-restrictions-set/enrollment-restrictions-ios-set-limit-notification.png)

> [!IMPORTANT]
> Les restrictions de limite d’appareil ne s’appliquent pour les types d’inscription Windows suivants :
> - Inscriptions cogérées
> - Inscriptions GPO
> - Inscriptions jointes Azure Active Directory
> - Inscriptions jointes Azure Active Directory en bloc
> - Inscriptions Autopilot
> - Inscriptions au Gestionnaire d’inscription d’appareil (DEM)
>
> Les restrictions de limite d’appareil ne s’appliquent pas à ces types d’inscription car ils sont considérés comme des scénarios d’appareil partagé.
> Vous pouvez définir des limites strictes pour ces types d’inscription [dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal#configure-device-settings).


## <a name="change-enrollment-restrictions"></a>Modifier les restrictions d’inscription

Pour changer les paramètres d’une restriction d’inscription, effectuez les étapes ci-dessous. Ces restrictions n’ont pas d’effet sur les appareils qui ont déjà été inscrits. Les appareils inscrits avec [l’agent de PC Intune](../fundamentals/manage-windows-pcs-with-microsoft-intune.md) ne peuvent pas être bloqués avec cette fonctionnalité.

1. Connectez-vous au [centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) > **Appareils** > **Restrictions d’inscription** > choisissez la restriction à modifier > **Propriétés**.
2. Choisissez **Modifier** en regard des paramètres que vous souhaitez modifier.
3. Sur la page **Modifier**, apportez les modifications souhaitées et passez à la page **Vérifier + enregistrer**, puis choisissez **Enregistrer**.


## <a name="blocking-personal-android-devices"></a>Blocage des appareils Android personnels
- Si vous bloquez l’inscription des appareils d’administrateur d’appareil Android personnels, les appareils avec profil professionnel Android Entreprise personnels peuvent quand même être inscrits.
- Par défaut, les paramètres de vos appareils avec profil professionnel Android Entreprise sont identiques à ceux de vos appareils d’administrateur d’appareil Android. Une fois que vous avez modifié votre profil professionnel Android Entreprise ou les paramètres d’administrateur d’appareil Android, ce n’est plus le cas.
- Si vous bloquez l’inscription du profil professionnel Android Entreprise personnel, seuls les appareils Android appartenant à l’entreprise peuvent s’inscrire avec des profils professionnels Android Entreprise.

## <a name="blocking-personal-windows-devices"></a>Blocage des appareils Windows personnels
Si vous bloquez l’inscription d’appareils Windows personnels, Intune vérifie que chaque nouvelle demande d’inscription Windows est autorisée en tant qu’inscription d’entreprise. Les inscriptions non autorisées seront bloquées.

Les méthodes suivantes sont qualifiées comme étant autorisées en tant qu’inscription d’entreprise Windows :
- L’utilisateur qui s’inscrit utilise un [compte de gestionnaire d’inscription d’appareil]( device-enrollment-manager-enroll.md).
- L’appareil s’inscrit via [Windows Autopilot](enrollment-autopilot.md).
- L’appareil est inscrit auprès de Windows Autopilot mais cela ne représente pas la seule option d’inscription MDM dans les paramètres Windows.
- Le numéro IMEI de l’appareil est listé dans **Inscription de l’appareil** >  **[Identificateurs d’appareil d’entreprise](corporate-identifiers-add.md)** . (Non pris en charge pour Windows Phone 8.1)
- L’appareil s’inscrit via un [package de provisionnement en bloc](windows-bulk-enroll.md).
- L’appareil s’inscrit avec un GPO ou une [inscription automatique à partir de Configuration Manager pour la cogestion](https://docs.microsoft.com/configmgr/comanage/quickstart-paths#bkmk_path1).
 
Les inscriptions suivantes sont marquées comme étant d’entreprise par Intune. Mais dans la mesure où elles ne permettent pas à l’administrateur Intune de contrôler par appareil, elles seront bloquées :
- [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [jonction Azure Active Directory durant la configuration de Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx)\*.
- [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [jonction Azure Active Directory à partir des paramètres Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)*.
 
Les méthodes d’inscription personnelle suivantes seront également bloquées :
- [Inscription automatique à MDM](windows-enroll.md#enable-windows-10-automatic-enrollment) avec [ajout de compte professionnel à partir des paramètres Windows](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)\*.
- Option [Inscription à MDM uniquement]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) à partir de Paramètres Windows.

\* Ces appareils ne sont pas bloqués s’ils sont inscrits auprès d’Autopilot.


## <a name="blocking-personal-ios-devices"></a>Blocage des appareils iOS personnels
Par défaut, Intune classe les appareils iOS comme personnels. Pour être classé comme appartenant à l’entreprise, un appareil iOS doit respecter l’une des conditions suivantes :
- Inscrit avec un numéro de série ou IMEI.
- Inscrit à l’aide de l’inscription automatique des appareils (anciennement programme d’inscription d’appareils)


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
