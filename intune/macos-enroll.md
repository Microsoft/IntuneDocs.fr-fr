---
title: Configurer l’inscription des appareils macOS
titlesuffix: Microsoft Intune
description: Découvrez comment configurer l’inscription des appareils macOS dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 32055e4370669de15342ab97dc71f91ee57426e4
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850996"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configurer l’inscription des appareils macOS dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune permet de gérer les appareils macOS de façon à donner aux utilisateurs l’accès aux applications et à la messagerie d’entreprise.

En tant qu’administrateur Intune, vous pouvez configurer l’inscription des appareils macOS détenus par l’entreprise et par les employés (« Apportez votre propre appareil » ou BYOD). 

## <a name="prerequisites"></a>Prérequis

Avant de configurer l’inscription des appareils macOS, effectuez les prérequis suivants :

- [Configurer des domaines](custom-domain-name-configure.md)
- [Configurer l’autorité MDM](mdm-authority-set.md)
- [Créer des groupes](groups-add.md)
- [Configurer le portail d’entreprise](company-portal-app.md)
- Attribuer des licences utilisateur dans le [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Obtenir un certificat Push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Appareils macOS de l’utilisateur (BYOD)

Vous pouvez laisser les utilisateurs inscrire leurs appareils personnels à la gestion Intune, approche communément appelée BYOD (« Apportez votre propre appareil »). Une fois les prérequis remplis et les licences affectées aux utilisateurs, ces derniers peuvent inscrire leurs appareils de deux manières :
- en accédant au [site web Portail d’entreprise](https://portal.manage.microsoft.com) ;
- en téléchargeant l'application du Portail d'entreprise.
Vous pouvez également leur envoyer un lien vers les étapes d’inscription en ligne : [Inscrire votre appareil macOS dans Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Pour plus d’informations sur les autres tâches de l’utilisateur final, consultez les articles suivants :

- [Ressources concernant l’expérience utilisateur final avec Microsoft Intune](end-user-educate.md)
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

Pour être un utilisateur approuvé, l’utilisateur final doit, après inscription via le Portail d’entreprise macOS, fournir manuellement une approbation à l’aide de préférences système. Les instructions nécessaires sont fournies par le Portail d’entreprise macOS pour les utilisateurs sur macOS 10.13.2 et versions ultérieures.

Pour savoir si un appareil est approuvé par l’utilisateur, accédez au portail Intune, puis sélectionnez **Appareils** > **Tous les appareils**> sélectionnez le périphérique > **matériel**. Cochez le champ **Utilisateur approuvé**. champ.

## <a name="next-steps"></a>Étapes suivantes

Une fois les appareils macOS inscrits, vous pouvez [créer des paramètres personnalisés pour les appareils macOS](custom-settings-macos.md).
