---
title: Guide pratique pour intégrer Windows Hello Entreprise à Microsoft Intune
titleSuffix: Microsoft Intune
description: Apprenez à créer une stratégie permettant de contrôler l’utilisation de Windows Hello Entreprise sur les appareils gérés.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: beb2043f2e32435d7e4ada3fcb1bb9918908dff9
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569465"
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>Intégrer Windows Hello Entreprise à Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Vous pouvez intégrer Windows Hello Entreprise (anciennement Microsoft Passport for Work) à Microsoft Intune.

 Hello Entreprise est une méthode de connexion alternative qui utilise Active Directory ou un compte Azure Active Directory en remplacement d’un mot de passe, d’une carte à puce ou d’une carte à puce virtuelle. Il vous permet d’utiliser un *mouvement de l’utilisateur* pour la connexion, au lieu d’un mot de passe. Un mouvement utilisateur peut être un simple code confidentiel, une authentification biométrique telle que Windows Hello ou un appareil externe tel qu’un lecteur d’empreintes digitales.

Intune s’intègre à Hello Entreprise de deux manières :

-   Une stratégie Intune peut être créée sous **Inscription des appareils**. Cette stratégie cible toute l’organisation (à l’échelle du locataire). Elle prend en charge l’OOBE (Out-Of-Box-Experience) Windows Autopilot et est appliquée quand un appareil est inscrit. 
-  Un profil de protection d’identité peut être créé sous **Configuration de l’appareil**. Ce profil cible les utilisateurs et les appareils affectés, et il est appliqué lors de l’enregistrement. 

Utilisez cet article pour créer une stratégie Windows Hello Entreprise par défaut, qui cible l’ensemble de votre organisation. Pour créer un profil de protection d’identité qui est appliqué pour sélectionner des groupes d’utilisateurs et d’appareils, consultez [Configurer un profil de protection d’identité](identity-protection-configure.md).  

<!--- -   You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> Dans les versions Windows 10 Desktop et Mobile antérieures à la mise à jour anniversaire, vous pouviez définir deux différents codes confidentiels pour l’authentification auprès de ressources :
> - Le **code confidentiel de l’appareil** pouvait être utilisé pour déverrouiller l’appareil et se connecter aux ressources de cloud.
> - Le **code confidentiel professionnel** servait à accéder aux ressources Azure AD sur les appareils personnels de l’utilisateur (BYOD).
> 
> Dans la mise à jour anniversaire, ces deux codes confidentiels ont été fusionnés dans un même code confidentiel d’appareil.
> Les stratégies de configuration Intune que vous définissez pour contrôler le code confidentiel de l’appareil, ainsi que toutes les stratégies Windows Hello Entreprise que vous avez configurées, définissent à présent la valeur de ce nouveau code confidentiel.
> Si vous avez défini ces deux types de stratégie pour contrôler le code PIN, la stratégie Windows Hello Entreprise est appliquée aux appareils Windows 10 Desktop et Mobile.
> Pour garantir la résolution des conflits de stratégie et l’application de la stratégie de code confidentiel, mettez à jour votre stratégie Windows Hello Entreprise en fonction des paramètres de votre stratégie de configuration, puis demandez à vos utilisateurs de synchroniser leurs appareils dans l’application Portail d’entreprise.



## <a name="create-a-windows-hello-for-business-policy"></a>Créer une stratégie Windows Hello Entreprise

1. Dans le [portail Azure](https://portal.azure.com), choisissez **Tous les services** > **Surveillance + Gestion** > **Intune**.

2. Dans le volet Intune, choisissez **Inscription de l’appareil**, puis **Inscription Windows** > **Windows Hello Entreprise**.

3. Dans le volet qui s’ouvre, choisissez les paramètres **Par défaut**.

4. Dans le volet **Tous les utilisateurs**, cliquez sur **Propriétés**, puis entrez un **Nom** et une **Description** facultative pour les paramètres de Windows Hello Entreprise.

5. Dans le volet **Tous les utilisateurs**, cliquez sur **Paramètres**, puis choisissez une des options suivantes pour **Configurer Windows Hello Entreprise** :

    - **Désactivé**. Si vous ne souhaitez pas utiliser Windows Hello Entreprise, sélectionnez ce paramètre. Tous les autres paramètres affichés à l’écran cessent d’être disponibles.
    - **Activée**. Sélectionnez ce paramètre si vous souhaitez configurer les paramètres Windows Hello Entreprise.
    - **Non configuré**. Sélectionnez ce paramètre si vous ne souhaitez pas utiliser Intune pour contrôler les paramètres Windows Hello Entreprise. Les paramètres Windows Hello Entreprise qui existent sur les appareils Windows 10 ne sont pas changés. Tous les autres paramètres du volet sont indisponibles.

6. Si vous avez sélectionné **Activé** à l’étape précédente, configurez les paramètres nécessaires qui sont appliqués à tous les appareils Windows 10 et Windows 10 Mobile inscrits.

   - **Utiliser un module de plateforme sécurisée (TPM)**. Une puce TPM fournit une couche supplémentaire de sécurité des données.<br>Choisissez l'une des valeurs suivantes :

     - **Requis** (par défaut). Seuls les appareils avec un module de plateforme sécurisée (TPM) accessible peuvent configurer Windows Hello Entreprise.
     - **Préféré**. Les appareils tentent d’abord d’utiliser un module de plateforme sécurisée. Si ce n’est pas possible, ils peuvent utiliser le chiffrement logiciel.

   - **Longueur minimale du PIN**/**Longueur maximale du PIN**. Ce paramètre configure les appareils pour qu’ils utilisent les longueurs minimale et maximale de code confidentiel que vous spécifiez, afin d’optimiser la sécurisation de la connexion. Le code PIN par défaut comporte six caractères, mais vous pouvez appliquer une longueur minimale de quatre caractères. La longueur maximale du code confidentiel est de 127 caractères.

   - **Lettres minuscules dans le PIN**/**Lettres majuscules dans le PIN**/**Caractères spéciaux dans le PIN**. Vous pouvez appliquer un code confidentiel plus puissant en exigeant l’utilisation de majuscules, de minuscules et de caractères spéciaux dans ce code. Choisissez parmi :

     - **Autorisé**. Les utilisateurs peuvent utiliser le type de caractère dans leur code confidentiel, mais cela n’est pas obligatoire.

     - **Requis**. Les utilisateurs doivent inclure au moins l’un des types de caractères dans leur code confidentiel. Par exemple, il est courant d’exiger au moins une majuscule et un caractère spécial.

     - **Non autorisé** (par défaut). Les utilisateurs ne doivent pas utiliser ces types de caractères dans leur code confidentiel. (Il s’agit également du comportement appliqué si le paramètre n’est pas configuré.)<br>Les caractères spéciaux comprennent : **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **Expiration du code confidentiel (en jours)**. Nous vous conseillons de spécifier une période d’expiration pour un code confidentiel, après laquelle les utilisateurs finaux doivent le modifier. La valeur par défaut est 41 jours.

   - **Conserver l’historique des codes confidentiels**. Limite la réutilisation des codes confidentiels précédemment utilisés. Par défaut, les 5 derniers codes confidentiels ne peuvent pas être réutilisés.

   - **Autoriser l’authentification biométrique**. Permet d’utiliser l’authentification biométrique, telle que la reconnaissance faciale ou les empreintes digitales, à la place d’un code confidentiel pour Windows Hello Entreprise. Les utilisateurs doivent toujours configurer un code confidentiel professionnel en cas d’échec de l’authentification biométrique. Choisissez parmi :

     - **Oui**. Windows Hello Entreprise autorise l’authentification biométrique.
     - **Non**. Windows Hello Entreprise empêche l’authentification biométrique (pour tous les types de compte).

   - **Utiliser la détection d’usurpation avancée, si disponible**. Détermine si les fonctionnalités d’anti-usurpation d’identité de Windows Hello sont utilisées sur les appareils qui les prennent en charge (par exemple, la détection d’une photo de visage au lieu d’un visage réel).<br>Si cette option est définie sur **Oui**, Windows nécessite que tous les utilisateurs utilisent la détection d’usurpation pour les fonctions de reconnaissance faciale, si disponible.

   - **Autoriser la connexion par téléphone**. Si cette option est définie sur **Oui**, les utilisateurs peuvent utiliser un appareil Remote Passport comme appareil mobile pour l’authentification d’ordinateur du bureau. L’ordinateur de bureau doit être joint à Azure Active Directory, et l’appareil mobile doit être configuré avec un code confidentiel Windows Hello Entreprise.

## <a name="windows-holographic-for-business-support"></a>Prise en charge de Windows Holographic for Business

Windows Holographic for Business prend en charge les paramètres Windows Hello Entreprise suivants :

- Utiliser un module de plateforme sécurisée (TPM)
- Longueur minimale du code PIN
- Longueur maximale du code PIN
- Lettres minuscules dans le code PIN
- Lettres majuscules dans le code PIN
- Caractères spéciaux dans le code PIN
- Expiration du code confidentiel (jours)
- Mémoriser l’historique des codes confidentiels

## <a name="further-information"></a>Informations supplémentaires
Pour plus d’informations sur Microsoft Passport, consultez [le guide](https://technet.microsoft.com/library/mt589441.aspx) dans la documentation de Windows 10.
