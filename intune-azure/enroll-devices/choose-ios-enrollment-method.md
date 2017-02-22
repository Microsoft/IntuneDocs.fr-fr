---
title: "Choisir comment inscrire des appareils iOS dans Intune | Version préliminaire d’Intune Azure | Microsoft Docs"
description: "Version préliminaire d’Intune Azure : découvrez comment configurer l’inscription des appareils iOS dans Microsoft Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: c228601451b33238d0f6929987dcdec3a5e56e8d


---

# <a name="choose-how-to-enroll-ios-devices"></a>Choisir comment inscrire des appareils iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Cette rubrique décrit les méthodes que vous pouvez utiliser pour inscrire des appareils iOS, ainsi que la configuration requise pour l’inscription.

Utilisez les informations suivantes pour déterminer la méthode à utiliser pour l’inscription des appareils iOS. Toutes les méthodes suivantes, à l’exception des appareils BYOD, sont destinées à l’inscription d’appareils d’entreprise.

**Conditions préalables :** un [certificat des services de notification Push Apple](get-an-apple-mdm-push-certificate.md) est obligatoire.

## <a name="user-owned-ios-devices-byod"></a>Appareils iOS de l’utilisateur (BYOD)

Si les utilisateurs souhaitent inscrire leurs appareils BYOD (appareils personnels), la seule méthode d’inscription disponible pour les utilisateurs est de télécharger l’application de portail d’entreprise pour iOS depuis l’App Store et de suivre les instructions d’inscription de l’application. Une fois inscrits, les utilisateurs peuvent se connecter au réseau d’entreprise, rejoindre le domaine ou Azure Active Directory et obtenir l’accès aux ressources d’entreprise.

## <a name="apple-configurator"></a>Apple Configurator

Vous pouvez inscrire des appareils iOS en exportant un profil d’inscription de l’entreprise, puis en connectant ces appareils mobiles à un Mac exécutant [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017). Apple Configurator prend en charge deux formes d’inscription :

- **Inscription Assistant Configuration** : rétablit les paramètres d’usine de l’appareil et le prépare à l’installation par le nouvel utilisateur. Cette méthode oblige l’administrateur à connecter l’appareil iOS par voie USB à un ordinateur Mac qui exécute l’outil Apple Configurator pour préconfigurer l’inscription. Les appareils sont alors remis à leurs utilisateurs, qui exécutent la procédure de l’Assistant Configuration. Cette procédure configure l’appareil avec les informations d’identification professionnelles ou scolaires de l’utilisateur et termine le processus d’inscription. Pour plus d’informations, consultez [Inscrire des appareils iOS avec Apple Configurator et l’Assistant Configuration](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md).

- **Inscription directe** : crée un fichier compatible avec Apple Configurator, à utiliser durant la préparation de l’appareil. Les paramètres d’usine de l’appareil inscrit ne sont pas rétablis et aucun utilisateur n’y est affilié. Pour inscrire des appareils, l’administrateur doit connecter l’appareil iOS par voie USB à un ordinateur Mac qui exécute l’outil Apple Configurator. Pour plus d’informations, consultez [Inscrire des appareils iOS en utilisant l’inscription directe Apple Configurator](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md).

## <a name="use-the-device-enrollment-program-dep"></a>Programme d’inscription des appareils (DEP)

Le programme DEP déploie un profil d’inscription selon le procédé OTA (Over The Air) sur les appareils achetés par son biais. Quand un utilisateur exécute l’Assistant Configuration sur l’appareil, celui-ci est inscrit dans Intune. Les appareils inscrits via le programme DEP ne peuvent pas être désinscrits par les utilisateurs. Pour plus d’informations, consultez [Inscrire des appareils iOS avec DEP](enroll-ios-devices-using-device-enrollment-program.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Utilisation du gestionnaire d’inscription d’appareil (DEM)
Le gestionnaire d’inscription est un type de compte d’utilisateur qui peut inscrire et gérer jusqu’à 1 000 appareils. Vous ajoutez des utilisateurs existants au compte de gestionnaire d’inscription d’appareil afin qu’ils puissent bénéficier de ces fonctionnalités. Chaque appareil que l’utilisateur DEM inscrit utilise une seule licence Intune. Pour plus d’informations, consultez [Inscrire des appareils avec le gestionnaire d’inscription d’appareils](enroll-devices-using-device-enrollment-manager.md).



<!--HONumber=Feb17_HO1-->


