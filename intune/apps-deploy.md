---
title: Attribuer des applications à des groupes dans Microsoft Intune
titlesuffix: ''
description: Apprenez à attribuer une application Intune à des groupes d’utilisateurs ou d’appareils en utilisant Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9258bf1847e83087404967c0ded50481da3a8dff
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290738"
---
# <a name="assign-apps-to-groups-with-microsoft-intune"></a>Attribuer des applications à des groupes avec Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Une fois que vous avez [ajouté une application](apps-add.md) à Microsoft Intune, vous pouvez l’attribuer à des utilisateurs et des appareils. Il est important de noter que vous pouvez attribuer une application à un appareil, que celui-ci soit géré par Intune ou pas. 

> [!NOTE]
> L’intention de déploiement disponible n’est pas prise en charge pour les groupes d’appareils, seuls les groupes d’utilisateurs sont pris en charge.

Le tableau suivant répertorie les différentes options disponibles pour attribuer des applications à des utilisateurs et des appareils :

|   | Appareils inscrits avec Intune | Appareils non inscrits avec Intune |
|-------------------------------------------------------------------------------------------|------------------------------|----------------------------------|
| Attribuer aux utilisateurs | Oui | Oui |
| Attribuer aux appareils | Oui | Non |
| Attribuer des applications encapsulées ou des applications incorporant le SDK Intune (pour les stratégies de protection d’application) | Oui | Oui |
| Attribuer des applications en tant qu’applications disponibles | Oui | Oui |
| Attribuer des applications en tant qu’applications requises | Oui | Non |
| Désinstallation d’applications | Oui | Non |
| Recevoir des mises à jour de l’application d’Intune | Oui | Non |
| Les utilisateurs finaux installent les applications disponibles à partir de l’application Portail d’entreprise | Oui | Non |
| Les utilisateurs finaux installent les applications disponibles à partir du Portail d’entreprise web | Oui | Oui |

> [!NOTE]
> Actuellement, vous pouvez attribuer des applications iOS et Android (applications métier ou achetées dans un Store) pour les appareils qui ne sont pas inscrits avec Intune.
>
> Pour recevoir des mises à jour d’applications sur des appareils qui ne sont pas inscrits auprès d’Intune, les utilisateurs des appareils doivent accéder à leur Portail d’entreprise et installer manuellement les mises à jour des applications.

## <a name="assign-an-app"></a>Attribuer une application

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le menu **Intune**, sélectionnez **Applications clientes**.
4. Dans la section **Gérer** du menu, sélectionnez **Applications**.
5. Dans le volet **Applications**, sélectionnez l’application que vous souhaitez attribuer.
6. Dans la section **Gérer** du menu, sélectionnez **Affectations**.
7. Sélectionnez **Ajouter un groupe** pour ouvrir le volet **Ajouter un groupe** lié à l’application.
8. Pour l’application spécifique, sélectionnez un **type d’affectation** :
   - **Disponible pour les appareils inscrits** : attribuez l’application à des groupes d’utilisateurs qui peuvent installer l’application à partir de l’application ou du site web Portail d’entreprise.
   - **Disponible avec ou sans inscription** : attribuez cette application à des groupes d’utilisateurs dont les appareils ne sont pas inscrits avec Intune. Les utilisateurs doivent disposer d’une licence Intune, consultez [Licences Intune](licenses.md).
   - **Requis** : l’application est installée sur les appareils dans les groupes sélectionnés. Certaines plateformes peuvent avoir des invites supplémentaires dont l’utilisateur final doit accuser réception avant le démarrage de l’installation.
   - **Désinstaller** : L’application est désinstallée des appareils dans les groupes sélectionnés si Intune a installé l’application sur l’appareil via une attribution « disponible pour les appareils inscrits » ou « Requis » en utilisant le même déploiement. Les liens Web ne peuvent pas être supprimés après le déploiement.

     > [!NOTE]
     > **Pour les applications iOS uniquement**  : si vous avez créé un profil VPN iOS qui contient des paramètres VPN par application, vous pouvez le sélectionner sous **VPN**. Quand l’application est exécutée, la connexion VPN est ouverte. Pour plus d’informations, consultez [Paramètres VPN pour les appareils iOS](vpn-settings-ios.md).
     >
     > **Pour les applications Android uniquement** : si vous déployez une application Android comme **Disponible avec ou sans inscription**, vous pourrez en connaître l’état uniquement sur les appareils inscrits.

9. Sélectionnez **Groupes inclus** pour choisir les groupes d’utilisateurs concernés par cette attribution d’application.
10. Cliquez sur **Sélectionner** une fois que vous avez sélectionné un ou plusieurs groupes à inclure.
11. Dans le volet **Attribuer**, sélectionnez **OK** pour terminer la sélection des groupes inclus.
12. Cliquez sur **Exclure des groupes** si vous voulez exclure des groupes d’utilisateurs d’un impact par cette attribution d’applications.
13. Si vous avez choisi d’exclure des groupes, dans **Sélectionner des groupes**, choisissez **Sélectionner**.
14. Dans le volet **Ajouter un groupe**, sélectionnez **OK**.
15. Dans le volet **Affectations** de l’application, sélectionnez **Enregistrer**.

L’application est maintenant attribuée aux groupes que vous avez sélectionnés. Pour en savoir plus sur l’inclusion et l’exclusion des attributions d’applications, consultez [Inclure et exclure des attributions d’applications](apps-inc-exl-assignments.md).

## <a name="how-conflicts-between-app-intents-are-resolved"></a>Résolution des conflits entre les intentions d’application

Parfois, la même application est attribuée à plusieurs groupes, mais avec des intentions différentes. Les informations contenues dans le tableau suivant peuvent vous aider à comprendre l’intention qui en résulte lorsque cela se produit :

| Intention du groupe 1 | Intention du groupe 2 | Intention résultante |
|-----------------------------------|-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|Utilisateur obligatoire|Utilisateur disponible|Obligatoire et disponible|
|Utilisateur obligatoire|Utilisateur non disponible|Obligatoire|
|Utilisateur obligatoire|Désinstallation utilisateur|Obligatoire|
|Utilisateur disponible|Utilisateur non disponible|Non disponible|
|Utilisateur disponible|Désinstallation utilisateur|Désinstaller|
|Utilisateur non disponible|Désinstallation utilisateur|Désinstaller
|Utilisateur obligatoire|Appareil obligatoire|Toutes deux existent, Intune traite Obligatoire
|Utilisateur obligatoire|Désinstallation appareil|Toutes deux existent, Intune résout Obligatoire
|Utilisateur disponible|Appareil obligatoire|Toutes deux existent, Intune résout Obligatoire (Obligatoire et Disponible)
|Utilisateur disponible|Désinstallation appareil|Toutes deux existent, Intune résout Disponible.<br><br>L’application apparaît dans le Portail d’entreprise.<br><br>Si l’application est déjà installée (en tant qu’application obligatoire avec intention précédente), elle est désinstallée.<br><br>Si l’utilisateur sélectionne **Installer à partir du Portail d’entreprise**, l’application est installée et l’intention de désinstallation n’est pas honorée.|
|Utilisateur non disponible|Appareil obligatoire|Obligatoire|
|Utilisateur non disponible|Désinstallation appareil|Désinstaller|
|Désinstallation utilisateur|Appareil obligatoire|Toutes deux existent, Intune résout Obligatoire|
|Désinstallation utilisateur|Désinstallation appareil|Toutes deux existent, Intune résout Désinstaller|
|Appareil obligatoire|Désinstallation appareil|Obligatoire|
|Utilisateur obligatoire et disponible|Utilisateur disponible|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Désinstallation utilisateur|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Utilisateur non disponible|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Appareil obligatoire|Toutes deux existent, Obligatoire et Disponible
|Utilisateur obligatoire et disponible|Appareil non disponible|Obligatoire et disponible|
|Utilisateur obligatoire et disponible|Désinstallation appareil|Toutes deux existent, Intune résout Obligatoire (Obligatoire et Disponible)
|Utilisateur non disponible|Appareil non disponible|Non disponible|
|Utilisateur disponible|Appareil non disponible|Disponible|
|Utilisateur obligatoire|Appareil non disponible|Obligatoire|
|Utilisateur disponible sans inscription|Utilisateur obligatoire et disponible|Obligatoire et disponible
|Utilisateur disponible sans inscription|Utilisateur obligatoire|Obligatoire
|Utilisateur disponible sans inscription|Utilisateur non disponible|Non disponible
|Utilisateur disponible sans inscription|Utilisateur disponible|Disponible|
|Utilisateur disponible sans inscription|Appareil obligatoire|Obligatoire et disponible sans inscription|
|Utilisateur disponible sans inscription|Appareil non disponible|Disponible sans inscription|
|Utilisateur disponible sans inscription|Désinstallation appareil|Désinstaller et disponible sans inscription.<br><br>Si l’utilisateur n’a pas installé l’application à partir du Portail d’entreprise, la désinstallation est honorée.<br><br>Si l’utilisateur installe l’application à partir du Portail d’entreprise, l’installation est prioritaire par rapport à la désinstallation.|

> [!NOTE]
> En ce qui concerne les applications du magasin iOS managées uniquement, une fois ajoutées à Microsoft Intune et assignées comme **Obligatoire**, elles sont automatiquement créées avec les intentions **Obligatoire** et **Disponible**.<br><br>
> Les applications iOS de l’App Store (et non les applications VPP iOS) qui sont ciblées intentionnellement sont appliquées sur l’appareil au moment où l’appareil s’enregistre et s’affichent également dans l’application Portail d’entreprise.

## <a name="android-enterprise-app-we-app-deployment"></a>Déploiement d’applications APP-WE Android pour les entreprises
Si vous disposez d’appareils Android dans un scénario de déploiement APP-WE (stratégie App Protection sans inscription) non inscrit, vous pouvez maintenant utiliser Google Play dans sa version gérée pour déployer des applications du Store et des applications métier pour les utilisateurs. Plus précisément, vous pouvez proposer aux utilisateurs finaux un catalogue d’applications et une expérience d’installation dans laquelle ils n’ont plus besoin d’assouplir la posture de sécurité de leurs appareils en autorisant les installations à partir de sources inconnues. Ce scénario de déploiement offrira par ailleurs une meilleure expérience utilisateur. Pour savoir comment attribuer une application, consultez [Attribuer une application](apps-deploy.md#assign-an-app).

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur le monitoring des affectations d’applications, consultez [Comment surveiller des applications](apps-monitor.md).
