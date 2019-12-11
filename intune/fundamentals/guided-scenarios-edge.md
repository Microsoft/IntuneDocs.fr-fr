---
title: Scénario guidé – Déployer Microsoft Edge pour mobile
titleSuffix: Microsoft Intune
description: Aidez-vous du scénario guidé pour déployer Microsoft Edge pour mobile à partir du portail Gestion des appareils Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e86f3a469169e7a805cb3f56e570ba4d3a90e925
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585694"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Scénario guidé – Déployer Microsoft Edge pour mobile 

En suivant ce [scénario guidé](~/fundamentals/guided-scenarios-overview.md), vous pouvez affecter l’application Microsoft Edge aux appareils iOS ou Android des utilisateurs de votre organisation. L’affectation de cette application permet à vos utilisateurs de parcourir le contenu sans interruption à l’aide de leur appareil d’entreprise. 

Microsoft Edge permet aux utilisateurs de faire le tri sur le web à l’aide de fonctionnalités intégrées qui les aident à regrouper, organiser et gérer le contenu professionnel. Les utilisateurs d’appareils iOS et Android qui se connectent avec leur compte Azure AD d’entreprise dans l’application Microsoft Edge trouvent le navigateur préchargé avec les **Favoris** de l’espace de travail et les filtres de site web que vous définissez.

> [!NOTE]
> Si vous empêchez les utilisateurs d’inscrire les appareils iOS ou Android, ce scénario ne permettra pas l’inscription et les utilisateurs devront installer Edge pour eux-mêmes.
Les fonctionnalités d’entreprise Microsoft Edge suivantes activées par les stratégies Intune incluent : 

- **Double identité** : les utilisateurs peuvent ajouter à la fois un compte professionnel, mais aussi un compte personnel, pour la navigation. Il existe une séparation complète entre les deux identités, ce qui est similaire à l’architecture et à l’expérience proposées dans Microsoft Office 365 et Outlook. Les administrateurs Intune pourront définir les stratégies souhaitées pour une expérience de navigation protégée au sein du compte professionnel. 
- **Intégration de la stratégie de protection des applications Intune** : les administrateurs peuvent maintenant cibler des stratégies de protection des applications sur Microsoft Edge, y compris le contrôle des fonctions Couper, Copier et Coller, la prévention des captures d’écran et la vérification que les liens sélectionnés par l’utilisateur s’ouvrent uniquement dans d’autres applications managées.
- **Intégration des proxys Azure Application** : les administrateurs peuvent contrôler l’accès aux applications SaaS et web, afin de garantir que les applications basées sur le navigateur ne s’exécuteront que dans le navigateur Microsoft Edge sécurisé, que les utilisateurs finaux se connectent à partir du réseau d’entreprise ou à partir d’Internet. 
- **Raccourcis de la page d’accueil et favoris managés** : pour un accès facilité, les administrateurs peuvent définir des adresses URL pour qu’elles apparaissent dans les favoris lorsque les utilisateurs finaux sont dans le contexte de leur entreprise. Les administrateurs peuvent définir un raccourci de page d’accueil, qui s’affiche comme raccourci principal lorsque l’utilisateur d’entreprise ouvre une nouvelle page ou un nouvel onglet dans Microsoft Edge.

## <a name="prerequisites"></a>Prérequis

- [Définir l’autorité MDM sur Intune](mdm-authority-set.md#set-mdm-authority-to-intune) – Le paramètre d’autorité de gestion des appareils mobiles (MDM) détermine la façon dont vous gérez vos appareils. En tant qu’administrateur informatique, vous devez définir une autorité de gestion des appareils mobiles (MDM) avant que les utilisateurs puissent inscrire des appareils pour la gestion.
- Autorisations d’administrateur Intune nécessaires :
    - Autorisations de lecture, création, suppression et affectation des applications gérées
    - Autorisations de lecture, création et affectation des applications mobiles
    - Autorisations de lecture, création et affectation des ensembles de stratégies
    - Autorisations de lecture et mise à jour de l’organisation

## <a name="step-1---introduction"></a>Étape 1 – Introduction

En suivant le scénario guidé **Déployer Microsoft Edge pour mobile**, vous allez configurer un déploiement de base de Microsoft Edge pour un groupe déterminé d’utilisateurs iOS et Android. Ce déploiement implémente la **double identité** et les **raccourcis vers les favoris gérés et la page d’accueil**. Par ailleurs, Intune installe automatiquement l’application Microsoft Edge sur les appareils inscrits par les utilisateurs sélectionnés. Cette installation automatique se produit sur tous les types d’inscription gérés par l’utilisateur, à savoir : 
- L’inscription iOS via l’application Portail d’entreprise 
- L’inscription avec affinité utilisateur iOS via Apple Business Manager 
- L’inscription Android héritée via l’application Portail d’entreprise 

Ce scénario guidé fait automatiquement apparaître **MyApps** dans les favoris Microsoft Edge et configure le navigateur avec la même personnalisation que celle définie pour l’application Portail d’entreprise Intune. 

### <a name="what-you-will-need-to-continue"></a>Ce dont vous avez besoin pour continuer
Nous vous demanderons de nous communiquer les favoris de l’espace de travail dont vos utilisateurs ont besoin ainsi que les filtres à mettre en place pour la navigation web. Avant de continuer, veillez à effectuer les tâches suivantes :

- Ajoutez des utilisateurs à des groupes Azure AD. Pour plus d’informations, consultez [Créer un groupe de base et ajouter des membres avec Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458).
- Inscrivez des appareils iOS ou Android dans Intune. Pour plus d’informations, consultez [Inscription d’appareils](https://go.microsoft.com/fwlink/?linkid=2102547).
- Rassemblez dans une liste les favoris de l’espace de travail à ajouter dans Microsoft Edge.
- Rassemblez dans une liste les filtres de sites web à appliquer dans Microsoft Edge.

## <a name="step-2---basics"></a>Étape 2 – Tâches de base

Dans cette étape, vous devez entrer un nom et une description pour vos nouvelles stratégies Microsoft Edge. Ces stratégies peuvent être référencées par la suite si vous avez besoin de modifier les affectations et les configurations. Le scénario guidé ajoute et affecte une application Microsoft Edge iOS pour vos appareils iOS et une application Microsoft Edge Android pour vos appareils Android. Par ailleurs, cette étape crée des stratégies de configuration pour ces applications.

## <a name="step-3---configuration"></a>Étape 3 : Configuration

Dans cette étape, le scénario guidé configure Microsoft Edge pour afficher toutes les autres applications affectées aux utilisateurs via Intune et partager la même personnalisation que l’application Portail d’entreprise Microsoft Intune. Vous pouvez affiner la configuration de Microsoft Edge avec une **URL du raccourci de page d’accueil**, une liste de **Signets gérés** et une liste d’**URL bloquées**. L’**URL du raccourci de page d’accueil** est la première icône qui figure en dessous de la barre de recherche quand les utilisateurs ouvrent un nouvel onglet dans Microsoft Edge sur leur appareil. Les **Signets gérés** consistent en une liste d’URL favorites auxquelles les utilisateurs peuvent accéder quand ils utilisent Microsoft Edge dans leur contexte professionnel. Les **URL bloquées** spécifient les sites qui sont bloqués pour vos utilisateurs quand ils se trouvent dans leur contexte professionnel. Tous les autres sites sont autorisés. 

## <a name="step-4---assignments"></a>Étape 4 – Affectations

Dans cette étape, vous pouvez choisir les groupes d’utilisateurs à inclure pour que Microsoft Edge Mobile soit configuré pour le travail. Microsoft Edge est aussi installé sur tous les appareils iOS et Android inscrits par ces utilisateurs.

## <a name="step-5---review--create"></a>Étape 5 – Vérifier + créer

La dernière étape vous permet d’examiner un récapitulatif des paramètres que vous avez configurés. Une fois que vous avez examiné vos choix, cliquez sur **Créer** pour terminer le scénario guidé. 

> [!NOTE]
> Un délai de 12 heures peut être nécessaire avant que Microsoft Edge reçoive la configuration. Pour plus d’informations, consultez [Stratégies de configuration des applications pour Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> Une fois le scénario guidé terminé, vous obtenez un récapitulatif. Vous pouvez par la suite modifier les ressources listées dans le récapitulatif, mais le tableau qui affiche ces ressources n’est pas enregistré.

## <a name="next-steps"></a>Étapes suivantes

- Pour une utilisation plus sûre de Microsoft Edge, configurez l’intégration de la stratégie de protection des applications Intune. Pour plus d’informations, consultez [Stratégies de protection des applications pour Microsoft Edge](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Si vous avez des sites intranet à inclure, explorez la protection de l’accès avec l’intégration du proxy d’application Azure. Pour plus d’informations, consultez [Configurer les paramètres du proxy d’application pour Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

