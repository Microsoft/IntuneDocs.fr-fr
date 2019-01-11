---
title: Intégrer Jamf Pro à Microsoft Intune pour des raisons de conformité | Microsoft Intune
description: Utilisez des stratégies de conformité Microsoft Intune avec l’accès conditionnel Azure Active Directory pour permettre de sécuriser les appareils gérés par Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cc547926d95e3fa1bec54b4ea55f764b5701b3b7
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816818"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Intégrer Jamf Pro à Intune pour des raisons de conformité

S'applique à : Intune dans le portail Azure

Si votre organisation utilise [Jamf Pro](https://www.jamf.com) pour gérer les Mac des utilisateurs finaux, vous pouvez vous servir des stratégies de conformité Microsoft Intune et de l’accès conditionnel Azure Active Directory pour faire en sorte que les appareils de votre organisation soient conformes.

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin des éléments suivants pour configurer l’accès conditionnel avec Jamf Pro :

- Jamf Pro 10.1.0 (ou une version ultérieure) ;
- [l’application Portail d’entreprise pour macOS](https://aka.ms/macoscompanyportal) ;
- des appareils macOS équipés d’OS X 10.11 Yosemite (ou une version ultérieure).

## <a name="connecting-intune-to-jamf-pro"></a>Connecter Intune à Jamf Pro

Vous pouvez connecter Intune à Jamf Pro en :

1. Créant une application dans Visual Studio.
2. Autorisant l’intégration d’Intune à Jamf Pro.
3. Configurant l’accès conditionnel dans Jamf Pro.

## <a name="create-a-new-application-in-azure-active-directory"></a>Créer une application dans Azure Active Directory

1. Ouvrez **Azure Active Directory** > **Inscriptions des applications**.
2. Cliquez sur **+ Inscription d’une nouvelle application**.
3. Entrez un **nom d’affichage**, par exemple, **Accès conditionnel Jamf**.
4. Sélectionnez **Application web / API**.
5. Spécifiez **l’URL de connexion** à l’aide de l’URL de votre instance Jamf Pro.
6. Cliquez sur **Créer une application**.
7. Enregistrez **l’ID d’application** ainsi créé, puis ouvrez **Paramètres** et accédez à **Accès d’API** > **Clés** pour créer une clé d’application. Entrez une **description**, le délai d’attente avant son **expiration**, puis enregistrez la clé d’application.

   > [!IMPORTANT]
   > La clé d’application ne s’affiche qu’une seule fois pendant ce processus. Veillez à l’enregistrer dans un endroit où vous pourrez facilement la récupérer.

8. Ouvrez **Paramètres**, puis accédez à **Accès d’API** > **Autorisations nécessaires** et supprimez toutes les autorisations.

   > [!NOTE]
   > Ajoutez une nouvelle autorisation requise. L’application ne peut fonctionner correctement qu’avec l’unique autorisation requise.

9. Sélectionnez **API Microsoft Intune** et cliquez sur **Sélectionner**.
10. Sélectionnez **Envoyer les attributs des appareils à Microsoft Intune** et cliquez sur **Sélectionner**.
11. Cliquez sur le bouton **Accorder des autorisations** après avoir enregistré les autorisations requises de l’application.

    > [!NOTE]
    > Si la clé d’application arrive à expiration, il vous faudra créer une nouvelle clé d’application dans Microsoft Azure, puis mettre à jour les données d’accès conditionnel dans Jamf Pro. Azure vous autorise à avoir à la fois l’ancienne et la nouvelle clés actives afin d’éviter toute interruption de service.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Autoriser l’intégration d’Intune à Jamf Pro

1. Dans le portail Microsoft Azure, ouvrez **Microsoft Intune** > **Conformité de l’appareil** > **Gestions des appareils de partenaire**.
2. Activez le connecteur de conformité de Jamf en collant l’ID d’application dans le champ **ID d’application Jamf Azure Active Directory**.
3. Cliquez sur **Save**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurer l’intégration de Microsoft Intune dans Jamf Pro

1. Dans Jamf Pro, accédez à **Gestion globale** > **Accès conditionnel**. Cliquez sur le bouton **Modifier** sous l’onglet **Intégration de Microsoft Intune**.
2. Cochez la case **Activer l’intégration de Microsoft Intune**.
3. Saisissez les informations requises sur votre client Azure, notamment **Emplacement**, **Nom de domaine**, **ID d’application** et **Clé d’application** (tous deux enregistrés lors des étapes précédentes).
4. Cliquez sur **Save**. Jamf Pro testera vos paramètres et vérifiera que tout fonctionne.

## <a name="set-up-compliance-policies-and-register-devices"></a>Configurer des stratégies de conformité et inscrire des appareils

Quand vous avez terminé de configurer l’intégration entre Intune et Jamf, vous devez [appliquer des stratégies de conformité aux appareils gérés par Jamf](conditional-access-assign-jamf.md).

## <a name="information-shared-from-jamf-pro-to-intune"></a>Informations partagées par Jamf Pro avec Intune

Jamf Pro capture des données d’inventaire sur les appareils macOS gérés. Jamf Pro fournit les informations suivantes à Intune :

* ID d’appareil Azure AD
* État de l’inventaire Jamf (état de l’inventaire d’un ordinateur enregistré auprès de Jamf Pro au cours des dernières 24 heures)
* Version de système d'exploitation
* ID d’utilisateur Azure AD
* Chiffré (FileVault 2)
* État de l’opérateur de contrôle d’appels
* Mot de passe : nombre minimal de jeux de caractères
* Expiration du mot de passe (jours)
* Type de mot de passe : simple, alphanumérique ou inconnu
* Empêcher la connexion automatique
* Longueur de mot de passe requise
* Mot de passe : nombre de mots de passe précédents pour empêcher la réutilisation
* Protection de l’intégrité du système
* Dernière heure d’enregistrement
* Type d’architecture
* Emplacements de mémoire RAM disponibles
* Capacité de la batterie
* ROM de démarrage
* Vitesse du bus
* Taille de cache
* Nom du périphérique
* Jonction de domaine
* ID Jamf
* Adresse MAC
* Make
* Modèle
* Identificateur du modèle
* Vitesse de la carte réseau
* Nombre de cœurs
* Nombre de processeurs
* Système d’exploitation
* Plate-forme
* vitesse du processeur
* Type de processeur
* Adresse MAC secondaire
* Numéro de série
* Version SMC
* RAM totale
* UDID
* Adresse e-mail de l’utilisateur

## <a name="next-steps"></a>Étapes suivantes

- [Appliquer des stratégies de conformité aux appareils gérés par Jamf](conditional-access-assign-jamf.md)
