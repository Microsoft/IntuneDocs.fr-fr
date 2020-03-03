---
title: Ajouter Microsoft Defender ATP sur les appareils macOS à l’aide de Microsoft Intune
titleSuffix: ''
description: Découvrez des informations sur l’ajout de Microsoft Defender ATP sur les appareils macOS à l’aide de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569558"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Ajouter Microsoft Defender ATP sur les appareils macOS à l’aide de Microsoft Intune

Pour pouvoir déployer, configurer, superviser ou protéger des applications, vous devez les ajouter au préalable à Intune. Microsoft Defender Advanced Threat Protection (ATP) est un des [types d’applications disponibles](~/apps/apps-add.md#app-types-in-microsoft-intune). En sélectionnant ce type d’application dans Intune, vous pouvez affecter et installer Microsoft Defender ATP sur les appareils macOS que vous gérez. Ce type d’application vous permet d’affecter facilement Microsoft Defender ATP à des appareils macOS sans avoir besoin d’utiliser l’outil de wrapping d’applications macOS. L’application est accompagnée de Microsoft AutoUpdate (MAU) qui garantit que les applications resteront sécurisées et à jour.

## <a name="prerequisites"></a>Prérequis
- L’appareil macOS doit exécuter macOS 10.13 ou ultérieur.
- L’appareil macOS doit avoir au moins 650 Mo d’espace disque.
- Déployez l’extension de noyau dans Intune. Pour plus d’informations, consultez [Ajouter des extensions de noyau macOS dans Intune](~/configuration/kernel-extensions-overview-macos.md).

> [!IMPORTANT]
> L’extension de noyau peut être approuvée automatiquement seulement si elle est présente sur l’appareil avant l’installation de l’application Microsoft Defender ATP. Sinon, les utilisateurs voient le message « Extension système bloquée » sur les Mac et doivent approuver l’extension en accédant à **Préférences de sécurité** ou **Préférences système** > **Sécurité et confidentialité**, puis en sélectionnant **Autoriser**. Pour plus d’informations, consultez [Résoudre les problèmes d’extension de noyau dans Microsoft Defender ATP pour Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext).

## <a name="add-microsoft-defender-atp-to-intune"></a>Ajouter Microsoft Defender ATP à Intune
Vous pouvez ajouter Microsoft Defender ATP à Intune en effectuant les étapes suivantes :

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Applications** > **Toutes les applications** > **Ajouter**.
3. Dans la liste **Type d’application**, sous **Microsoft Defender ATP**, sélectionnez **macOS**.

## <a name="configure-app-information"></a>Configurer les informations de l’application
Dans cette étape, vous fournissez des informations sur le déploiement de cette application. Ces informations vous permettent d’identifier l’application dans Intune et aux utilisateurs de trouver l’application dans le portail d’entreprise.

1. Cliquez sur **Informations sur l’application** pour afficher le volet **Informations sur l’application**.
2. Dans le volet **Informations sur l’application**, vous fournissez des informations sur le déploiement de cette application. Ces informations vous permettent d’identifier l’application dans Intune et aux utilisateurs de trouver l’application dans le portail d’entreprise.
    - **Nom** : Entrez le nom de l'application tel qu'il s'affichera dans le portail d'entreprise. Assurez-vous que tous les noms sont uniques. Si le même nom d’application existe deux fois, une seule application est proposée aux utilisateurs du portail d’entreprise.
    - **Description** : Entrez une description de l'application. Par exemple, vous pouvez lister les utilisateurs ciblés dans la description.
    - **Éditeur** : Microsoft apparaît comme éditeur.
    - **Catégorie** : si vous le souhaitez, sélectionnez une ou plusieurs des catégories d’applications intégrées ou sélectionnez une catégorie que vous avez créée. Ce paramètre facilite la recherche de l’application pour les utilisateurs qui parcourent le portail d’entreprise.
    - **Afficher en tant qu’application proposée dans le portail d’entreprise** : sélectionnez cette option pour afficher l’application en premier sur la page principale du portail d’entreprise lorsque les utilisateurs parcourent des applications.
    - **URL d'information** : Entrez éventuellement l’URL d’un site web qui contient des informations sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **URL de la déclaration de confidentialité** : Entrez éventuellement l’URL d’un site web qui contient des informations de confidentialité sur cette application. Cette URL est présentée aux utilisateurs du portail d’entreprise.
    - **Développeur** : Microsoft apparaît comme développeur.
    - **Propriétaire** : Microsoft apparaît comme propriétaire.
    - **Remarques** : entrez les éventuelles remarques à associer à cette application.
3. Sélectionnez **OK**.

## <a name="select-scope-tags-optional"></a>Sélectionner les balises d’étendue (facultatif)
Vous pouvez utiliser des balises d’étendue pour déterminer qui peut afficher des informations sur l’application cliente dans Intune. Pour plus d’informations sur les balises d’étendue, consultez Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée.
1.  Sélectionnez **Étendue (balises)** > **Ajouter**.
2.  Utilisez la case **Sélectionner** pour rechercher les balises d’étendue.
3.  Cochez la case en regard des balises d’étendue que vous souhaitez attribuer à cette application.
4.  Cliquez sur **Sélectionner** > **OK**.

## <a name="add-the-app"></a>Ajouter l’application
Une fois que vous avez terminé la configuration, sélectionnez **Ajouter** dans le volet **Ajouter une application**. 

L’application créée s’affiche dans la liste des applications, où vous pouvez l’affecter aux groupes de votre choix. 

> [!NOTE]
> Actuellement, Apple n’offre aucun moyen permettant à Intune de désinstaller Microsoft Defender ATP sur les appareils macOS.

## <a name="next-steps"></a>Étapes suivantes
- Pour découvrir comment configurer Microsoft Defender ATP sur les appareils macOS, consultez [Configurer Microsoft Defender ATP sur les appareils macOS](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences).
- Pour en savoir plus sur l’inclusion et l’exclusion d’affectations d’application pour des groupes d’utilisateurs, consultez [Inclure et exclure des affectations d’applications](~/apps/apps-inc-exl-assignments.md).
- [Affecter des applications à des groupes](~/apps/apps-deploy.md)

