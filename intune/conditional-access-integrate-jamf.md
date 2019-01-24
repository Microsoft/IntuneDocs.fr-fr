---
title: Intégrer Jamf Pro à Microsoft Intune pour des raisons de conformité | Microsoft Intune
description: Utilisez des stratégies de conformité Microsoft Intune avec l’accès conditionnel Azure Active Directory pour permettre de sécuriser les appareils gérés par Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 971dc851714045a8a3b60dfe8ff6c6acc4419294
ms.sourcegitcommit: 7c41f42d6e398ed46aa602ec8aaa4f39aaf92772
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54325013"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Intégrer Jamf Pro à Intune pour des raisons de conformité

S'applique à : Intune dans le portail Azure

Si votre organisation utilise [Jamf Pro](https://www.jamf.com) pour gérer les Mac des utilisateurs finaux, vous pouvez vous servir des stratégies de conformité Microsoft Intune et de l’accès conditionnel Azure Active Directory pour vérifier que les appareils de votre organisation sont conformes.

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin des éléments suivants pour configurer l’accès conditionnel avec Jamf Pro :

- Jamf Pro 10.1.0 (ou une version ultérieure) ;
- [l’application Portail d’entreprise pour macOS](https://aka.ms/macoscompanyportal) ;
- des appareils macOS équipés d’OS X 10.11 Yosemite (ou une version ultérieure).

## <a name="connecting-intune-to-jamf-pro"></a>Connecter Intune à Jamf Pro

Pour connecter Intune à Jamf Pro, vous devez effectuer les actions suivantes :

1. Créer une application dans Azure
2. Autoriser l’intégration d’Intune à Jamf Pro
3. Configurer l’accès conditionnel dans Jamf Pro

## <a name="create-an-application-in-azure-active-directory"></a>Créer une application dans Azure Active Directory

1. Dans le [Portail Azure](https://portal.azure.com), accédez à **Azure Active Directory** > **Inscriptions d’applications**.
2. Sélectionnez **+ Nouvelle inscription d’application**.
3. Entrez un **nom d’affichage**, par exemple, **Accès conditionnel Jamf**.
4. Sélectionnez **Application web / API**.
5. Spécifiez **l’URL de connexion** à l’aide de l’URL de votre instance Jamf Pro.
6. Sélectionnez **Créer**. L’application est créée et le portail présente les détails relatifs à celle-ci.
7. Enregistrez une copie de l’**ID d’application** pour la nouvelle application. Vous allez spécifier cet ID plus tard dans une procédure. Sélectionnez ensuite **Paramètres**, puis accédez à **Accès API** > **Clés**.
8. Dans le volet *Clés*, spécifiez une **Description**, le délai d’attente avant l’**Expiration** de la clé, puis sélectionnez **Enregistrer** pour générer la clé d’application (valeur).

   > [!IMPORTANT]
   > La clé d’application ne s’affiche qu’une seule fois pendant ce processus. Veillez à l’enregistrer dans un endroit où vous pourrez facilement la récupérer.

8. Dans le volet *Paramètres* de l’application, accédez à **Accès API** > **Autorisations nécessaires**. Sélectionnez les autorisations existantes, puis cliquez sur **Supprimer** pour supprimer toutes les autorisations. La suppression des autorisations existantes est nécessaire quand vous ajoutez une nouvelle autorisation. L’application fonctionne uniquement si elle dispose de la seule autorisation nécessaire.  
9. Pour affecter une nouvelle autorisation, sélectionnez **+Ajouter** > **Sélectionner une API** > **API Microsoft Intune**, puis cliquez sur **Sélectionner**.
10. Dans le volet *Activer l’accès*, sélectionnez **Envoyer les attributs des appareils à Microsoft Intune**, cliquez sur **Sélectionner**, puis sur **Terminé**.
11. Dans le volet *Autorisations nécessaires*, sélectionnez **Accorder des autorisations**, puis **Oui** pour appliquer les autorisations nécessaires à l’application.

    > [!NOTE]
    > Si la clé d’application arrive à expiration, il vous faudra créer une nouvelle clé d’application dans Microsoft Azure, puis mettre à jour les données d’accès conditionnel dans Jamf Pro. Azure vous autorise à avoir à la fois l’ancienne et la nouvelle clés actives afin d’éviter toute interruption de service.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Autoriser l’intégration d’Intune à Jamf Pro

1. Dans le [Portail Azure](https://portal.azure.com), accédez à **Microsoft Intune** > **Conformité de l’appareil** > **Gestion des appareils partenaires**.
2. Activez le connecteur de conformité de Jamf en collant l’ID d’application que vous avez enregistré au cours de la procédure précédente dans le champ **ID d’application Jamf Azure Active Directory**.
3. Sélectionnez **Enregistrer**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurer l’intégration de Microsoft Intune dans Jamf Pro

1. Dans Jamf Pro, accédez à **Gestion globale** > **Accès conditionnel**. Cliquez sur le bouton **Modifier** sous l’onglet **Intégration de Microsoft Intune**.
2. Cochez la case **Activer l’intégration de Microsoft Intune**.
3. Saisissez les informations requises sur votre client Azure, notamment **Emplacement**, **Nom de domaine**, **ID d’application** et **Clé d’application** (tous deux enregistrés lors des étapes précédentes).
4. Sélectionnez **Enregistrer**. Jamf Pro teste vos paramètres et vérifie que tout fonctionne.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurer des stratégies de conformité et inscrire des appareils

Une fois que vous avez configuré l’intégration entre Intune et Jamf, vous devez [appliquer des stratégies de conformité aux appareils gérés par Jamf](conditional-access-assign-jamf.md).



## <a name="next-steps"></a>Étapes suivantes

- [Appliquer des stratégies de conformité aux appareils gérés par Jamf](conditional-access-assign-jamf.md)
- [Données envoyées par Jamf à Intune](data-jamf-sends-to-intune.md)
