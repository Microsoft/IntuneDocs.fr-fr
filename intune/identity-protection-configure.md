---
title: Configurer les paramètres Identity Protection dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez un profil d’appareil pour configurer les paramètres de Windows Hello Entreprise sur les appareils Windows 10 dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7012479023ece83ef475431c5cefe150ab2ef342
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317958"
---
# <a name="configure-identity-protection-settings-in-microsoft-intune"></a>Configurer les paramètres Identity Protection dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les profils Identity Protection contrôlent la façon dont Windows Hello Entreprise est provisionné et configuré sur les appareils Windows 10 gérés. Créez ce profil pour configurer :  
* La disponibilité de Windows Hello Entreprise pour les appareils et les utilisateurs
* Les exigences relatives aux codes PIN des appareils
* Les mouvements que les utilisateurs peuvent et ne peuvent pas utiliser pour se connecter à leurs appareils  

 Vous pouvez affecter ce profil à certains groupes d’utilisateurs et d’appareils, ou à tous les utilisateurs et tous les appareils. Les groupes reçoivent un profil Identity Protection lorsqu’ils s’enregistrent dans Intune.    

Utilisez les informations de cet article pour créer un profil Identity Protection. Ensuite, [affectez votre profil](device-profile-assign.md) aux groupes d’utilisateurs et d’appareils.

Cette fonctionnalité s’applique aux appareils qui exécutent :  
- Windows 10 et versions ultérieures
- Windows Holographic for Business  

## <a name="create-a-device-profile-with-identity-protection-settings"></a>Créer un profil d’appareil contenant les paramètres Identity Protection

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
3. Sélectionnez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
4. Entrez un **Nom** et une **Description** pour le profil Identity Protection.
5. Dans la liste déroulante **Plateforme**, sélectionnez **Windows 10 et versions ultérieures**. Windows Hello entreprise est uniquement pris en charge sur les appareils qui exécutent Windows 10 et versions ultérieures.
6. Dans la liste déroulante **Type de profil**, choisissez **Identity Protection**.
7. Dans le volet Windows Hello for Business, choisissez l’une des options suivantes pour configurer Windows Hello Entreprise :
    * Désactivé. Si vous ne souhaitez pas utiliser Windows Hello Entreprise, sélectionnez ce paramètre. Tous les autres paramètres affichés à l’écran cessent d’être disponibles.
    * Activé. Sélectionnez ce paramètre si vous souhaitez configurer les paramètres Windows Hello Entreprise.  

8. Si vous avez sélectionné **Activé** à l’étape précédente, configurez les paramètres nécessaires qui sont appliqués aux appareils et aux utilisateurs Windows 10 et Windows 10 Mobile inscrits ciblés.

> [!NOTE]
> Lorsque vous affectez des profils Identity Protection uniquement à des utilisateurs, le contexte d’appareil est défini par défaut sur **Non configuré**  

   - **Longueur minimale du PIN**/**Longueur maximale du PIN**. Ce paramètre configure les appareils pour qu’ils utilisent les longueurs minimale et maximale de code confidentiel que vous spécifiez, afin d’optimiser la sécurisation de la connexion. Le code PIN par défaut comporte six caractères, mais vous pouvez appliquer une longueur minimale de quatre caractères. La longueur maximale du code confidentiel est de 127 caractères.  

   - **Lettres minuscules dans le PIN**/**Lettres majuscules dans le PIN**/**Caractères spéciaux dans le PIN**. Vous pouvez appliquer un code confidentiel plus puissant en exigeant l’utilisation de majuscules, de minuscules et de caractères spéciaux dans ce code. Choisissez parmi :

     - **Autorisé**. Les utilisateurs peuvent utiliser le type de caractère dans leur code confidentiel, mais cela n’est pas obligatoire.

     - **Requis**. Les utilisateurs doivent inclure au moins l’un des types de caractères dans leur code confidentiel. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

     - **Non autorisé** (par défaut). Les utilisateurs ne doivent pas utiliser ces types de caractères dans leur code confidentiel. (cela se produit également si le paramètre n’est pas configuré).<br>Les caractères spéciaux comprennent : **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **Expiration du code confidentiel (en jours)**. Nous vous conseillons de spécifier une période d’expiration pour un code confidentiel, après laquelle les utilisateurs finaux doivent le modifier. La valeur par défaut est 41 jours.

   - **Conserver l’historique des codes confidentiels**. Limite la réutilisation des codes confidentiels précédemment utilisés. Par défaut, les 5 derniers codes confidentiels ne peuvent pas être réutilisés.  
   - **Activer la récupération du code PIN** : permet à l’utilisateur de modifier son code PIN à l’aide du service de récupération de code PIN de Windows Hello Entreprise. 
       - **Activer**. Le service cloud chiffre un secret de récupération de code PIN à stocker sur l’appareil. L’utilisateur peut modifier son code PIN si nécessaire.  
       - **Non configuré** (par défaut). Le secret de récupération de code PIN n’est pas créé ni stocké. Si l’utilisateur oublie son code PIN, la seule façon d’en obtenir un nouveau est de supprimer le code PIN existant et d’en créer un nouveau. L’utilisateur devra se réinscrire auprès des services auxquels il avait accès avec l’ancien code PIN.  
   
   - **Utiliser un module de plateforme sécurisée (TPM)**. Une puce TPM fournit une couche supplémentaire de sécurité des données. Choisissez l'une des valeurs suivantes :  
     - **Activer**. Seuls les appareils avec un module de plateforme sécurisée (TPM) accessible peuvent configurer Windows Hello Entreprise.
     - **Non configuré**. Tous les appareils peuvent provisionner Windows Hello Entreprise, même lorsqu’il n’existe aucun module de plateforme sécurisée (TPM) utilisable. Les appareils tentent d’abord d’utiliser un module de plateforme sécurisée, mais si celui-ci n’est pas disponible, les appareils peuvent utiliser le chiffrement logiciel.  

   - **Autoriser l’authentification biométrique**. Permet d’utiliser l’authentification biométrique, telle que la reconnaissance faciale ou les empreintes digitales, à la place d’un code confidentiel pour Windows Hello Entreprise. Les utilisateurs doivent toujours configurer un code confidentiel professionnel en cas d’échec de l’authentification biométrique. Choisissez parmi :

     - **Activer**. Windows Hello Entreprise autorise l’authentification biométrique.
     - **Non configuré** (par défaut). Windows Hello Entreprise empêche l’authentification biométrique (pour tous les types de compte).

   - **Utiliser la détection d’usurpation avancée, si disponible**. Détermine si les fonctionnalités d’anti-usurpation d’identité de Windows Hello sont utilisées sur les appareils qui les prennent en charge (par exemple, la détection d’une photo de visage au lieu d’un visage réel).
       - **Activer**. Windows nécessite que tous les utilisateurs utilisent la détection d’usurpation pour les fonctionnalités de reconnaissance faciale, si celles-ci sont prises en charge.  
       - **Non configuré** (par défaut). Windows applique les configurations de détection d’usurpation sur l’appareil.

   - **Certificat pour ressources locales**. 
       - **Activer**. Permet à Windows Hello Entreprise d’utiliser des certificats pour s’authentifier auprès de ressources locales.
       - **Non configuré** (par défaut). Empêche Windows Hello Entreprise d’utiliser des certificats pour s’authentifier auprès de ressources locales.  
9. Cliquez sur **OK**pour enregistrer votre profil.  

Le profil est créé et apparaît dans la liste **Configuration de l’appareil - Profils**. Pour affecter ce profil à des groupes, consultez [Guide pratique pour l’attribution de profils d’appareils](device-profile-assign.md).  

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
