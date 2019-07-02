---
title: Paramètres Windows Hello Entreprise dans Microsoft Intune - Azure | Microsoft Docs
description: Passez en revue la liste de tous les paramètres en rapport avec le code PIN, la biométrie et la détection d’usurpation dans un profil de protection d’identité pour utiliser et configurer Windows Hello Entreprise sur des appareils Windows 10 dans Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 1cbf45fc337cbe7d7a45081a3b9e05002ca126d8
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402939"
---
# <a name="windows-10-device-settings-to-enable-windows-hello-for-business-in-intune"></a>Paramètres des appareils Windows 10 permettant d’activer Windows Hello Entreprise dans Intune

Cet article liste et décrit les paramètres Windows Hello Entreprise que vous pouvez contrôler sur les appareils Windows 10 dans Intune. En tant qu’administrateur de service Intune, vous pouvez configurer ces paramètres et les affecter aux appareils Windows 10, dans le cadre de votre solution de gestion des appareils mobiles (MDM). 

Pour plus d’informations sur ces paramètres, consultez [Configurer les paramètres de stratégie Windows Hello for Business](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings) dans la documentation Windows Hello.


Pour en savoir plus sur les profils Windows Hello Entreprise dans Intune, consultez [Configurer la protection de l’identité](identity-protection-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration](identity-protection-configure.md#create-the-device-profile).

## <a name="windows-hello-for-business"></a>Windows Hello Entreprise
- **Configurer Windows Hello Entreprise** :
  - **Non configuré** : sélectionnez ce paramètre si vous ne souhaitez pas utiliser Intune pour contrôler les paramètres Windows Hello for Business. Les paramètres Windows Hello Entreprise qui existent sur les appareils Windows 10 ne sont pas changés. Tous les autres paramètres du volet sont indisponibles.

  - **Désactivé** : si vous ne souhaitez pas utiliser Windows Hello for Business, sélectionnez ce paramètre. Tous les autres paramètres affichés à l’écran cessent d’être disponibles.
  - **Activé** : sélectionnez ce paramètre si vous souhaitez configurer les paramètres Windows Hello for Business.  
  
  **Par défaut** : Non configuré

  Lorsque la valeur *activé*, les paramètres suivants sont disponibles :

    - **Longueur minimale du code confidentiel**  
     Spécifiez une longueur minimale du PIN pour les appareils, afin de faciliter la connexion sécurisée. Par défaut du périphérique Windows est six caractères, mais ce paramètre peut mettre en œuvre un minimum de quatre à 127 caractères. 
  
      **Par défaut** : *non configuré*

    - **Longueur maximale du code confidentiel**  
    Spécifiez une longueur maximale de code confidentiel pour les appareils, afin de faciliter la connexion sécurisée. Par défaut du périphérique Windows est six caractères, mais ce paramètre peut mettre en œuvre un minimum de quatre à 127 caractères.  

      **Par défaut** : *non configuré*  

    - **Lettres minuscules dans le code confidentiel**  
      vous pouvez demander aux utilisateurs finaux d’inclure des lettres minuscules pour créer un code PIN plus fort. Les options disponibles sont les suivantes :

      - **Non autorisé** : empêche les utilisateurs d’utiliser des minuscules dans le code confidentiel. (cela se produit également si le paramètre n’est pas configuré).
      - **Autorisé** : autorise les utilisateurs à utiliser des minuscules dans le code confidentiel, mais ce n’est pas obligatoire.
      - **Requis** : les utilisateurs doivent inclure au moins une lettre minuscule dans le code confidentiel. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

    - **Lettres majuscules dans le code confidentiel**  
    vous pouvez demander aux utilisateurs finaux d’inclure des lettres majuscules pour créer un code PIN plus fort. Les options disponibles sont les suivantes :

      - **Non autorisé** : empêche les utilisateurs d’utiliser des majuscules dans le code confidentiel. (cela se produit également si le paramètre n’est pas configuré).
      - **Autorisé** : autorise les utilisateurs à utiliser des majuscules dans le code confidentiel, mais ce n’est pas obligatoire.
      - **Requis** : les utilisateurs doivent inclure au moins une lettre majuscule dans le code confidentiel. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

    - **Caractères spéciaux dans le code confidentiel**  
    vous pouvez demander aux utilisateurs finaux d’inclure des caractères spéciaux pour créer un code PIN plus fort. Les caractères spéciaux comprennent : `! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~`  
 
      Les options disponibles sont les suivantes :
      - **Non autorisé** : empêche les utilisateurs d’utiliser des caractères spéciaux dans le code confidentiel. (cela se produit également si le paramètre n’est pas configuré).
      - **Autorisé** : autorise les utilisateurs à utiliser des majuscules dans le code confidentiel, mais ce n’est pas obligatoire.
      - **Requis** : les utilisateurs doivent inclure au moins une lettre majuscule dans le code confidentiel. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

      **Par défaut**: non autorisé

  - **Expiration du code confidentiel (en jours)**  
      Nous vous conseillons de spécifier une période d’expiration pour un code confidentiel, après laquelle les utilisateurs finaux doivent le modifier. Par défaut du périphérique Windows est 41 jours.

    **Par défaut** : non configuré

  - **Conserver l’historique des codes confidentiels**  
    Limite la réutilisation des codes confidentiels précédemment utilisés. Par défaut, les appareils Windows empêchant la réutilisation des cinq dernières broches.  

    **Par défaut** : non configuré  

  - **Activer la récupération du code confidentiel**   
    Permet à l’utilisateur pour le Windows Hello entreprise recovery service. 
    
    - **Activé** : code confidentiel de la récupération est stocké sur l’appareil et l’utilisateur peut modifier son code PIN si nécessaire.  
    - **Désactivé** -le secret de récupération n’est pas créé ou stocké.

    **Par défaut** : Non configuré

  - **Utiliser un module de plateforme sécurisée (TPM)**    
    Une puce TPM fournit une couche supplémentaire de sécurité des données.  

    - **Activé** : seuls les appareils avec un module de plateforme sécurisée (TPM) accessible peuvent configurer Windows Hello for Business.
    - **Non configuré** : les appareils tentent d’abord d’utiliser un module de plateforme sécurisée. Si ce n’est pas possible, ils peuvent utiliser le chiffrement logiciel.
    
    **Par défaut** : Non configuré

  - **Autoriser l’authentification biométrique**  
     Permet d’utiliser l’authentification biométrique, telle que la reconnaissance faciale ou les empreintes digitales, à la place d’un code confidentiel pour Windows Hello Entreprise. Les utilisateurs doivent toujours configurer un code confidentiel professionnel en cas d’échec de l’authentification biométrique. Choisissez parmi :

    - **Activer** : Windows Hello for Business autorise l’authentification biométrique.
    - **Non configuré** : Windows Hello for Business empêche l’authentification biométrique (pour tous les types de compte).

    **Par défaut** : Non configuré

  - **Utiliser la détection d’usurpation avancée, si disponible**  
    Détermine si les fonctionnalités d’anti-usurpation d’identité de Windows Hello sont utilisées sur les appareils qui les prennent en charge (par exemple, la détection d’une photo de visage au lieu d’un visage réel).  
    - **Activé** : Windows nécessite que tous les utilisateurs utilisent la détection d’usurpation pour les fonctionnalités de reconnaissance faciale, si celles-ci sont prises en charge.
    - **Non configuré** : Windows applique les configurations de détection d’usurpation sur l’appareil.

    **Par défaut** : Non configuré

  - **Certificat pour ressources locales**  

    - **Activé** : permet à Windows Hello for Business d’utiliser des certificats pour s’authentifier auprès de ressources locales.
    - **Non configuré** : empêche Windows Hello for Business d’utiliser des certificats pour s’authentifier auprès de ressources locales. Au lieu de cela, les appareils utilisent le comportement par défaut, qui est celui de l’*authentification locale par confiance de clé*. Pour plus d’informations, consultez [Certificat utilisateur pour l’authentification locale](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-cert-trust-policy-settings#use-certificate-for-on-premises-authentication) dans la documentation Windows Hello.  

  **Par défaut** : Non configuré

- **Utiliser des clés de sécurité pour la connexion**  
  Ce paramètre est disponible pour les appareils qui exécutent Windows 10 version 1903 ou version ultérieure. Il permet de gérer la prise en charge pour l’utilisation de clés de sécurité Windows Hello pour la connexion.  

  - **Activé** -les utilisateurs peuvent utiliser une clé de sécurité Windows Hello comme informations d’identification d’ouverture de session pour les PC ciblés avec cette stratégie. 
  - **Désactivé** - clés de sécurité sont désactivées et que les utilisateurs ne peuvent pas les utiliser pour se connecter à un PC.   

  **Par défaut** : Non configuré

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](device-profile-assign.md) et [suivre son état](device-profile-monitor.md).
