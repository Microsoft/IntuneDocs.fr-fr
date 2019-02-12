---
title: Paramètres Windows Hello Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Passez en revue la liste de tous les paramètres en rapport avec le code PIN, la biométrie et la détection d’usurpation dans un profil de protection d’identité pour utiliser et configurer Windows Hello Entreprise sur des appareils Windows 10 dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9bbdb56770c154a482ad004f1f3f980809424caf
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848506"
---
# <a name="windows-10-and-newer-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Paramètres des appareils Windows 10 (et ultérieur) pour activer Windows Hello Entreprise dans Intune

Cet article liste et décrit les paramètres Windows Hello Entreprise que vous pouvez contrôler sur les appareils Windows 10 dans Intune. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour utiliser un code PIN ou une empreinte digitale pour vous connecter et plus.

En tant qu’administrateur Intune, vous pouvez créer ces paramètres et les affecter à des appareils Windows 10 et ultérieur.

Pour en savoir plus sur les profils Windows Hello Entreprise dans Intune, consultez [Configurer la protection de l’identité](identity-protection-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello Entreprise

- **Configurez Windows Hello Entreprise** : Pour utiliser cette fonctionnalité et configurer ses paramètres, choisissez **Activer**.
- **Longueur minimale du code PIN** : entrez la longueur minimale du code PIN que vous souhaitez autoriser sur les appareils. La longueur par défaut du code PIN est de 6 caractères. La longueur minimale du code PIN est de 4 caractères.
- **Longueur maximale du code PIN** : entrez la longueur maximale du code PIN que vous souhaitez autoriser sur les appareils. La longueur par défaut du code PIN est de 6 caractères. La longueur maximale du code confidentiel est de 127 caractères.  
- **Lettres minuscules dans le code PIN** : vous pouvez demander aux utilisateurs finaux d’inclure des lettres minuscules pour créer un code PIN plus fort. Les options disponibles sont les suivantes :

  - **Non autorisé** (par défaut) : empêche les utilisateurs d’utiliser des minuscules dans le code PIN (cela se produit également si le paramètre n’est pas configuré).
  - **Autorisé** : autorise les utilisateurs à utiliser des minuscules dans le code PIN, mais ce n’est pas obligatoire.
  - **Requis** : les utilisateurs doivent inclure au moins une lettre minuscule dans le code PIN. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

- **Lettres majuscules dans le code PIN** : vous pouvez demander aux utilisateurs finaux d’inclure des lettres majuscules pour créer un code PIN plus fort. Les options disponibles sont les suivantes :

  - **Non autorisé** (par défaut) : empêche les utilisateurs d’utiliser des majuscules dans le code PIN (cela se produit également si le paramètre n’est pas configuré).
  - **Autorisé** : autorise les utilisateurs à utiliser des majuscules dans le code PIN, mais ce n’est pas obligatoire.
  - **Requis** : les utilisateurs doivent inclure au moins une lettre majuscule dans le code PIN. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

- **Caractères spéciaux dans le code PIN** : vous pouvez demander aux utilisateurs finaux d’inclure des caractères spéciaux pour créer un code PIN plus fort. Les options disponibles sont les suivantes :

  - **Non autorisé** (par défaut) : empêche les utilisateurs d’utiliser des caractères spéciaux dans le code PIN (cela se produit également si le paramètre n’est pas configuré).
    Les caractères spéciaux comprennent : `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`
  - **Autorisé** : autorise les utilisateurs à utiliser des majuscules dans le code PIN, mais ce n’est pas obligatoire.
  - **Requis** : les utilisateurs doivent inclure au moins une lettre majuscule dans le code PIN. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

- **Expiration du code PIN (en jours)**  : Nous vous conseillons de spécifier une période d’expiration pour un code confidentiel, après laquelle les utilisateurs finaux doivent le modifier. La valeur par défaut est 41 jours.

- **Conserver l’historique des codes PIN** : Limite la réutilisation des codes confidentiels précédemment utilisés. Par défaut, les 5 derniers codes PIN ne peuvent pas être réutilisés.  
- **Activer la récupération du code PIN** : permet à l’utilisateur de changer son code PIN à l’aide du service de récupération de code PIN de Windows Hello Entreprise.

       - **Enable**: The cloud service encrypts a PIN recovery secret to store on the device. The user can change their PIN if needed.  
       - **Not configured** (default): A PIN recovery secret is not created or stored. If the user's PIN is forgotten, the only way to get a new PIN is by deleting the existing PIN and creating a new one. The user will need to re-register with any services the old PIN provided access to.  

- **Utiliser un module de plateforme sécurisée (TPM)**  : Une puce TPM fournit une couche supplémentaire de sécurité des données. Choisissez l'une des valeurs suivantes :  
  - **Activer** : Seuls les appareils avec un module de plateforme sécurisée (TPM) accessible peuvent configurer Windows Hello Entreprise.
  - **Non configuré** : Tous les appareils peuvent provisionner Windows Hello Entreprise, même lorsqu’il n’existe aucun module de plateforme sécurisée (TPM) utilisable. Les appareils tentent d’abord d’utiliser un module de plateforme sécurisée, mais si celui-ci n’est pas disponible, les appareils peuvent utiliser le chiffrement logiciel.  

- **Autoriser l’authentification biométrique** : Permet d’utiliser l’authentification biométrique, telle que la reconnaissance faciale ou les empreintes digitales, à la place d’un code confidentiel pour Windows Hello Entreprise. Les utilisateurs doivent toujours configurer un code confidentiel professionnel en cas d’échec de l’authentification biométrique. Choisissez parmi :

  - **Activer** : Windows Hello Entreprise autorise l’authentification biométrique.
  - **Non configuré** (par défaut) : Windows Hello Entreprise empêche l’authentification biométrique (pour tous les types de compte).

- **Utiliser la détection d’usurpation avancée, si disponible** : choisissez si les fonctionnalités de détection d’usurpation de Windows Hello sont utilisées sur les appareils qui les prennent en charge. Vous pouvez ainsi détecter si un visage est réel ou s’il provient d’une photo.

  - **Activer** : Windows nécessite que tous les utilisateurs utilisent la détection d’usurpation pour les fonctionnalités de reconnaissance faciale, si celles-ci sont prises en charge.  
  - **Non configuré** (par défaut) : Windows applique les configurations de détection d’usurpation sur l’appareil.

- **Certificat pour ressources locales** : 

  - **Activer** : Permet à Windows Hello Entreprise d’utiliser des certificats pour s’authentifier auprès de ressources locales.
  - **Non configuré** (par défaut) : Empêche Windows Hello Entreprise d’utiliser des certificats pour s’authentifier auprès de ressources locales.  

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
