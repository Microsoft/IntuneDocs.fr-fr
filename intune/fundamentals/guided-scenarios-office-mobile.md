---
title: Scénario guidé – Applications mobiles Microsoft Office sécurisées
titleSuffix: Microsoft Intune
description: Aidez-vous du scénario guidé pour déployer des applications mobiles Microsoft Office sécurisées à partir du portail Gestion des appareils Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0232855773626693d848f77e561c51d281739215
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514606"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Scénario guidé – Applications mobiles Microsoft Office sécurisées 

En suivant ce scénario guidé du portail Gestion des appareils, vous pouvez activer la protection des applications Intune de base sur les appareils iOS/iPadOS et Android.

La protection des applications que vous activez applique les actions suivantes : 
- Chiffrer les fichiers de travail.
- Exiger un code PIN pour accéder aux fichiers de travail.
- Exiger la réinitialisation du code PIN après cinq tentatives infructueuses.
- Bloquer la sauvegarde des fichiers de travail dans iTunes, iCloud ou les services de sauvegarde Android.  
- Autoriser l’enregistrement des fichiers de travail sur OneDrive ou SharePoint uniquement.
- Empêcher les applications protégées de charger des fichiers de travail sur des appareils jailbreakés ou rootés.
- Bloquer l’accès aux fichiers de travail si l’appareil est hors connexion pendant 720 minutes.
- Supprimer les fichiers de travail si l’appareil est hors connexion pendant 90 jours. 

## <a name="background"></a>Contexte

Les applications mobiles Office, à l’instar de Microsoft Edge pour mobile, prennent en charge la double identité. La double identité permet aux applications de gérer les fichiers de travail indépendamment des fichiers personnels. 

![Image de données d’entreprise et de données personnelles](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

Les [stratégies de protection des applications Intune](~/apps/app-protection-policy.md) vous aident à protéger vos fichiers de travail sur les appareils inscrits dans Intune. Vous pouvez également utiliser des stratégies de protection des applications sur les appareils détenus par l’employé qui ne sont pas inscrits pour la gestion dans Intune. Dans ce cas, même si votre entreprise ne gère pas l’appareil, vous devez quand même veiller à que les fichiers de travail et les ressources soient protégés.

Vous pouvez utiliser des stratégies de protection des applications pour empêcher les utilisateurs d’enregistrer les fichiers de travail à des emplacements non protégés. Vous pouvez également limiter le déplacement de données vers d’autres applications qui ne sont pas protégées par des stratégies de protection des applications. Les paramètres de stratégie de protection d’application comprennent :
- Des stratégies de réadressage des données comme **Enregistrer des copies de données d’organisation** et **Restreindre les opérations de couper, copier et coller**.
- Des paramètres de stratégie d’accès pour exiger un code PIN simple pour l’accès et bloquer l’exécution des applications gérées sur les appareils jailbreakés ou rootés.

L’accès conditionnel basé sur l’application et la gestion d’applications clientes ajoutent une couche de sécurité en vous assurant que seules les applications clientes qui prennent en charge les stratégies de protection des applications Intune peuvent accéder aux services Exchange en ligne et autres services d’Office 365.

Vous pouvez bloquer les applications de messagerie intégrées sur iOS/iPadOS et Android quand vous autorisez seulement l’application Microsoft Outlook à accéder à Exchange Online. En outre, vous pouvez bloquer les applications qui n’ont pas de stratégies de protection des applications Intune appliquées lors de l’accès à SharePoint Online.

Dans cet exemple, l’administrateur a appliqué des stratégies de protection des applications à l’application Outlook suivies d’une règle d’accès conditionnel qui ajoute l’application Outlook à une liste approuvée d’applications qui peuvent être utilisées lors de l’accès aux e-mails d’entreprise.

![Flux de processus d’accès conditionnel à l’application Outlook](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Prérequis

Vous devez disposer des autorisations d’administration Intune suivantes :

   - Autorisations de lecture, création, suppression et affectation des applications gérées
   - Autorisations de lecture, création et affectation des ensembles de stratégies
   - Autorisations de lecture de l’organisation

## <a name="step-1---introduction"></a>Étape 1 – Introduction

En suivant le scénario guidé **Intune App Protection**, vous empêcherez le partage ou la fuite de données en dehors de votre organisation. 

Les utilisateurs iOS/iPadOS et Android affectés doivent entrer un code PIN chaque fois qu’ils ouvrent une application Office. Après cinq tentatives d’identification avortées, les utilisateurs doivent réinitialiser leur code PIN. Si vous exigez déjà un code PIN d’appareil, les utilisateurs ne seront pas impactés.

### <a name="what-you-will-need-to-continue"></a>Ce dont vous avez besoin pour continuer

Nous vous demanderons de nous indiquer les applications dont vos utilisateurs ont besoin ainsi que les conditions pour y accéder. Tenez les informations suivantes à portée de main :
- Liste des applications Office approuvées pour une utilisation dans l’entreprise.
- L’utilisation d’un code PIN est-elle obligatoire pour lancer les applications approuvées sur les appareils non gérés ?

## <a name="step-2---basics"></a>Étape 2 – Tâches de base

Dans cette étape, vous devez entrer un**préfixe** et une **description** pour la nouvelle stratégie de protection des applications. Les détails concernant les ressources créées par le scénario guidé sont mis à jour à mesure que vous ajoutez le **préfixe**. Si vous avez besoin par la suite de modifier les affectations et la configuration, ces détails vous permettront de retrouver facilement vos stratégies. 

> [!TIP]
> Pensez à noter les ressources qui sont créées pour vous y reporter ultérieurement.

## <a name="step-3---apps"></a>Étape 3 – Applications

Pour vous aider à démarrer, ce scénario guidé présélectionne les applications mobiles suivantes à protéger sur les appareils iOS/iPadOS et Android :
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

Ce scénario guidé configure également ces applications pour qu’elles ouvrent les liens web dans Microsoft Edge et donc que les sites de travail s’ouvrent dans un navigateur protégé.

Modifiez la liste des applications gérées par une stratégie que vous souhaitez protéger. Ajoutez ou supprimez des applications dans cette liste. 

Une fois que vous avez sélectionné les applications, cliquez sur **Suivant**.

## <a name="step-4---configuration"></a>Étape 4 – Configuration

Dans cette étape, vous devez configurer les conditions d’accès et de partage des fichiers et des e-mails de l’entreprise dans ces applications. Par défaut, les utilisateurs peuvent enregistrer des données dans les comptes OneDrive et SharePoint de votre organisation.

| Paramètre | Description | Valeur par défaut |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| Type de code PIN | Les codes PIN numériques sont composés uniquement de chiffres. Les codes secrets sont constitués de caractères alphanumériques et de caractères spéciaux.  Sur iOS/iPadOS, pour configurer le type de code secret, l’application doit avoir la version 7.1.12 du SDK Intune ou une version supérieure. Le type numérique n’a aucune restriction de version du Kit de développement logiciel (SDK) Intune. | Numérique |
| Sélectionner la longueur minimale du code PIN | spécifiez le nombre minimal de chiffres que doit contenir un code PIN. | 6 |
| Revérifier les exigences d’accès après (minutes d’inactivité) | Si l’application gérée par la stratégie est inactive plus longtemps que le nombre de minutes d’inactivité spécifié, l’application demande à ce que les conditions d’accès (c’est-à-dire, le code PIN, les paramètres de lancement conditionnel) soient revérifiées après le lancement de l’application. | 30 |
| Impression des données de l’organisation | En cas de blocage, l’application ne peut pas imprimer les données protégées. | Bloquer |
| Ouvrir les liens d’applications gérées par stratégie dans des navigateurs non gérés | En cas de blocage, les liens d’applications gérées par la stratégie doivent être ouverts dans un navigateur géré. | Bloquer |
| Copier les données dans des applications non gérées | En cas de blocage, les données gérées sont conservées dans les applications gérées. | Autoriser |

## <a name="step-5---assignments"></a>Étape 5 – Affectations

Dans cette étape, vous pouvez choisir les groupes d’utilisateurs à inclure pour faire en sorte qu’ils aient accès aux données de votre entreprise. La protection des applications étant affectée aux utilisateurs, et non aux appareils, les données de votre entreprise sont sécurisées, indépendamment de l’appareil utilisé et de son état d’inscription.

Les utilisateurs sans affectation de stratégies de protection des applications et de paramètres d’accès conditionnel peuvent enregistrer les données de leur profil d’entreprise dans des applications personnelles et dans le stockage local non géré de leurs appareils mobiles. De même, ils peuvent se connecter à des services de données d’entreprise, comme Microsoft Exchange, avec des applications personnelles.

## <a name="step-6---review--create"></a>Étape 6 – Vérifier + créer

La dernière étape vous permet d’examiner un récapitulatif des paramètres que vous avez configurés. Une fois que vous avez examiné vos choix, cliquez sur **Créer** pour terminer le scénario guidé. Une fois le scénario guidé terminé, un tableau des ressources s’affiche. Vous pouvez modifier ces ressources par la suite, mais une fois que vous quittez le récapitulatif, le tableau n’est pas enregistré.

> [!IMPORTANT]
> Une fois le scénario guidé terminé, vous obtenez un récapitulatif. Vous pouvez par la suite modifier les ressources listées dans le récapitulatif, mais le tableau qui affiche ces ressources n’est pas enregistré.
## <a name="next-steps"></a>Étapes suivantes

- Améliorez la sécurité des fichiers de travail en affectant aux utilisateurs une stratégie d’accès conditionnel basé sur l’application pour empêcher les services cloud d’envoyer des fichiers de travail à des applications non protégées. Pour plus d’informations, consultez [Configurer des stratégies d’accès conditionnel basé sur l’application avec Intune](~/protect/app-based-conditional-access-intune-create.md).

