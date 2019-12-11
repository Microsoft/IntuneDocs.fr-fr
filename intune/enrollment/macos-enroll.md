---
title: Configurer l’inscription des appareils macOS
titleSuffix: Microsoft Intune
description: Découvrez comment configurer l’inscription des appareils macOS dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 684e9602e66842e26a7f8e233a8cee6db73f132d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74098208"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configurer l’inscription des appareils macOS dans Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune permet de gérer les appareils macOS de façon à donner aux utilisateurs l’accès aux applications et à la messagerie d’entreprise.

En tant qu’administrateur Intune, vous pouvez configurer l’inscription des appareils macOS détenus par l’entreprise et par les employés (« Apportez votre propre appareil » ou BYOD). 

## <a name="prerequisites"></a>Prérequis

Avant de configurer l’inscription des appareils macOS, effectuez les prérequis suivants :

- [Assurez-vous que votre appareil est pris en charge par la procédure d’inscription d’appareils Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurer des domaines](../fundamentals/custom-domain-name-configure.md)
- [Configurer l’autorité MDM](../fundamentals/mdm-authority-set.md)
- [Créer des groupes](../fundamentals/groups-add.md)
- [Configurer le portail d’entreprise](../apps/company-portal-app.md)
- Attribuer des licences utilisateur dans le [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtenir un certificat Push MDM Apple](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Appareils macOS de l’utilisateur (BYOD)

Vous pouvez permettre aux utilisateurs d’inscrire leurs propres appareils personnels dans la gestion Intune. C’est ce que l’on appelle le BYOD (« apportez votre propre appareil »). Une fois les prérequis remplis et les licences affectées aux utilisateurs, ces derniers peuvent inscrire leurs appareils de deux manières :
- en accédant au [site web Portail d’entreprise](https://portal.manage.microsoft.com) ;
- téléchargement de l’application Mac Portail d’entreprise sur [aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac).

Vous pouvez également envoyer un lien vers les étapes d’inscription en ligne à vos utilisateurs : [Inscrire votre appareil macOS dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Pour plus d’informations sur les autres tâches de l’utilisateur final, consultez les articles suivants :

- [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](../fundamentals/end-user-educate.md)
- [Utiliser un appareil macOS avec Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>Appareils macOS détenus par l’entreprise
Dans le cas des organisations qui achètent des appareils pour leurs utilisateurs, Intune prend en charge les méthodes d’inscription des appareils macOS détenus par l’entreprise suivantes :
- [Programme d’inscription des appareils Apple (DEP)](device-enrollment-program-enroll-macos.md) : les organisations peuvent acheter des appareils macOS par le biais du Programme d’inscription des appareils (DEP) d’Apple. DEP vous permet de déployer un profil d’inscription « à distance » pour inscrire des appareils à la gestion.
- [Gestionnaire d’inscription d’appareil (DEM)](device-enrollment-manager-enroll.md) : avec un compte DEM, vous pouvez inscrire jusqu’à 1 000 appareils.

## <a name="block-macos-enrollment"></a>Bloquer l’inscription macOS
Par défaut, Intune permet aux appareils macOS de s’inscrire. Pour empêcher l’inscription des appareils Mac OS, consultez [Définir des restrictions de type d’appareil](enrollment-restrictions-set.md).

## <a name="enroll-virtual-macos-machines-for-testing"></a>Inscrire des machines virtuelles macOS à des fins de test

> [!NOTE]
> Les machines virtuelles macOS sont uniquement prises en charge à des fins de test. Vous ne devez pas utiliser des machines virtuelles macOS en tant qu’appareils de production pour vos utilisateurs finaux. 

Vous pouvez inscrire des machines virtuelles macOS à des fins de test à l’aide de Parallels Desktop ou de VMware Fusion. 

Pour Parallels Desktop, vous avez besoin de définir le type de matériel et le numéro de série des machines virtuelles pour qu’Intune puisse les reconnaître. Suivez les instructions de Parallels pour définir le type de matériel et le [numéro de série](http://kb.parallels.com/123455) afin de configurer les paramètres nécessaires au test. Nous vous recommandons de faire correspondre le type de matériel de l’appareil qui exécute les machines virtuelles à celui des machines virtuelles que vous créez. Vous pouvez trouver ce type de matériel dans le **menu Pomme** > **À propos de ce Mac** > **Rapport système** > **Identifiant du modèle**. 

Pour VMware Fusion, vous devez [modifier le fichier .vmx](https://kb.vmware.com/s/article/1014782) pour définir le modèle matériel et le numéro de série de la machine virtuelle. Nous vous recommandons de faire correspondre le type de matériel de l’appareil qui exécute les machines virtuelles à celui des machines virtuelles que vous créez. Vous pouvez trouver ce type de matériel dans le **menu Pomme** > **À propos de ce Mac** > **Rapport système** > **Identifiant du modèle**. 

## <a name="user-approved-enrollment"></a>Inscription approuvée de l’utilisateur
L’inscription approuvée de l’utilisateur est un type d’inscription macOS que vous pouvez utiliser pour gérer certains paramètres sensibles du point de vue de la sécurité. Pour plus d’informations, consultez la [documentation de prise en charge d’Apple](https://support.apple.com/HT208019).

À partir de novembre 2019, toutes les inscriptions macOS appartenant à des utilisateurs seront approuvées par ces derniers, car l’utilisateur doit installer manuellement le profil de gestion pour pouvoir s’inscrire. Pendant [le processus d’inscription](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp), l’utilisateur installe le profil de gestion Apple dans **Préférences système** > **Profils**.  Les instructions d’installation du profil de gestion sont disponibles dans l’application macOS Portail d'entreprise.

Les appareils inscrits avant novembre 2019 peuvent ne pas être approuvés par l’utilisateur si ce dernier n’a pas approuvé manuellement le profil de gestion. Toutefois, les utilisateurs peuvent revenir en arrière et approuver le profil de gestion en accédant à **Préférences système** > **Profils** > choisir le **profil de gestion** > **Approuver**.

### <a name="find-out-if-a-device-is-user-approved"></a>Déterminer si un appareil est approuvé par l’utilisateur
1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Choisissez **Appareils** > **Tous les appareils** > choisir l’appareil > **Matériel**.
3. Cochez le champ **L’utilisateur a approuvé l’inscription**.


## <a name="next-steps"></a>Étapes suivantes

Une fois les appareils macOS inscrits, vous pouvez [créer des paramètres personnalisés pour les appareils macOS](../configuration/custom-settings-macos.md).
