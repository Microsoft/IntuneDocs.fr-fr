---
title: "Protéger les données d’application à l’aide des stratégies de gestion des applications mobiles | Microsoft Intune"
description: "Cette rubrique explique comment les stratégies de gestion des applications mobiles peuvent vous aider à protéger les données de votre entreprise, empêcher toute perte de données et séparer les informations personnelles des informations professionnelles."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 87c1f90f41ec72ff74c23bfa270efade31890fc0


---

# <a name="protect-app-data-using-mobile-application-management-policies-with-microsoft-intune"></a>Protéger les données d’application à l’aide des stratégies de gestion des applications mobiles avec Microsoft Intune

## <a name="how-you-can-protect-app-data"></a>Comment protéger les données d’application
Vos employés utilisent des appareils mobiles pour des tâches à la fois personnelles et professionnelles. Vous voulez qu’ils restent productifs, mais vous voulez éviter toute perte de données intentionnelle ou non.  Vous voulez aussi pouvoir protéger les données de votre entreprise auxquelles les employés accèdent sur des appareils que vous ne gérez pas.

Vous pouvez utiliser des stratégies de gestion des applications mobiles Intune pour protéger les données de votre entreprise. Étant donné que les stratégies de gestion des applications mobiles Intune sont **indépendantes de toute solution de gestion des appareils mobiles**, vous pouvez les utiliser pour protéger les données de votre entreprise en inscrivant ou non les appareils dans une solution de gestion des appareils. En implémentant des **stratégies au niveau de l’application**, vous pouvez restreindre l’accès aux ressources d’entreprise et conserver les données au sein de votre département informatique.

Vous pouvez configurer des stratégies de gestion des applications mobiles pour les applications exécutées sur les appareils :

-   **Inscrits dans Microsoft Intune :** les appareils de cette catégorie sont généralement des appareils qui appartiennent à une entreprise.

-   **Inscrits dans une solution de gestion des appareils mobiles tierce :** les appareils de cette catégorie sont généralement des appareils qui appartiennent à une entreprise.

  > [!NOTE]
  > Nous ne recommandons pas d’utiliser des stratégies de gestion des applications mobiles avec des solutions de gestion des applications mobiles tierces ou solutions de conteneur sécurisé.

-   **Non inscrits dans une solution de gestion des appareils mobiles :** les appareils de cette catégorie sont généralement des appareils qui appartiennent à des employés et ne sont pas gérés ni inscrits dans Intune ou d’autres solutions de gestion des appareils mobiles.

> [!IMPORTANT]
> Vous pouvez créer des stratégies de gestion des applications mobiles pour les applications mobiles Office qui se connectent aux services Office 365. Les stratégies de gestion des applications mobiles ne sont pas prises en charge pour les applications qui se connectent à des services Exchange, Skype Entreprise ou SharePoint locaux.

## <a name="benefits-of-using-mam-policies"></a>Avantages de l’utilisation de stratégies de gestion des applications mobiles

-   **Elles permettent de protéger les données de votre entreprise au niveau de l’application.** Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils.

-   **La productivité des utilisateurs n’est pas affectée et les stratégies ne sont pas appliquées quand vous utilisez l’application dans un contexte personnel.** Les stratégies sont appliquées uniquement dans un contexte professionnel, ce qui vous donne la possibilité de protéger les données d’entreprise sans toucher aux données personnelles.

Il existe d’autres avantages à utiliser la gestion des appareils mobiles avec des stratégies de gestion des applications mobiles. Les entreprises peuvent avoir recours aux deux simultanément. Par exemple, un employé peut utiliser un téléphone fourni par l’entreprise ainsi qu’une tablette personnelle. Dans ce cas, le téléphone de l’entreprise est inscrit dans la gestion des appareils mobiles et protégé par des stratégies de gestion des applications mobiles, tandis que l’appareil personnel est protégé par des stratégies de gestion des applications mobiles uniquement.

- **La gestion des appareils mobiles permet de s’assurer que l’appareil est protégé.** Par exemple, vous pouvez demander un code confidentiel pour accéder à l’appareil ou déployer des applications gérées sur l’appareil. Vous pouvez également déployer des applications sur des appareils via votre solution de gestion des appareils mobiles pour mieux contrôler la gestion des applications.

- **Les stratégies de gestion des applications mobiles permettent de vérifier que les protections de la couche d’application sont en place.** Par exemple, vous pouvez avoir une stratégie qui exige un code confidentiel pour ouvrir une application dans un contexte professionnel, empêche le partage des données entre les applications ainsi que l’enregistrement des données d’application de l’entreprise dans un emplacement de stockage personnel.

## <a name="devices-that-support-mam"></a>Appareils qui prennent en charge la gestion des applications mobiles
Les stratégies de gestion des applications mobiles sont prises en charge sur :
-   iOS 8.1 ou version ultérieure
-   Android 4 ou version ultérieure

Les appareils Windows ne sont pas pris en charge actuellement.
##  <a name="how-mam-policies-protect-app-data"></a>Comment les stratégies de gestion des applications mobiles protègent les données d’application

###  <a name="apps-without-mam-policies"></a>Applications sans stratégies de gestion des applications mobiles

![Image qui illustre comment les données peuvent se déplacer librement entre les applications si aucune stratégie de gestion des applications mobiles n’est mise en place](../media/Apps_without_MAM_policies.png)

Quand vous utilisez des applications sans aucune restriction, les données d’entreprise et personnelles peuvent se mélanger. Les données d’entreprise peuvent alors finir dans des emplacements de stockage personnel ou être transmises à des applications hors de votre portée, ce qui peut entraîner une perte de données. Les flèches dans le diagramme indiquent un déplacement des données sans restriction entre les applications (professionnelles et personnelles) et vers des emplacements de stockage.

### <a name="data-protection-with-mam-policies"></a>Protection des données avec les stratégies de gestion des applications mobiles

![Image qui illustre comment les données d’entreprise sont protégées quand des stratégies de gestion des applications mobiles sont appliquées](../media/Apps_with_mobile_app_policies.png)

Vous pouvez utiliser des stratégies de gestion des applications mobiles pour empêcher l’enregistrement des données sur le stockage local de l’appareil et limiter le déplacement des données vers d’autres applications qui ne sont pas protégées par des stratégies de gestion des applications mobiles. Les paramètres de stratégie de gestion des applications mobiles sont entre autres :
- Stratégies de réadressage des données comme **Empêcher Enregistrer sous** et **Restreindre les opérations de couper, copier et coller**.
- Paramètres de stratégie d’accès comme **Exiger un code confidentiel simple pour l’accès** et **Bloquer l’exécution des applications gérées sur les appareils jailbreakés ou rootés**.

### <a name="data-protection-with-mam-policies-on-devices-that-are-managed-by-a-mdm-solution"></a>Protection des données avec des stratégies de gestion des applications mobiles sur des appareils gérés par une solution de gestion des appareils mobiles

![Image qui illustre le fonctionnement des stratégies de gestion des applications mobiles sur les appareils BYOD (Bring Your Own Devices)](../media/MAM_BYOD_November.png)

**Pour les appareils inscrits dans une solution de gestion des appareils mobiles** : le schéma précédent illustre les couches de protection fournies par les stratégies de gestion des appareils mobiles et de gestion des applications mobiles.

La solution de gestion des appareils mobiles :

-   Inscrit l’appareil.

-   Déploie les applications sur l’appareil.

-   Assure la gestion et la conformité de l’appareil en continu.

**Les stratégies de gestion des applications mobiles sont synonymes de valeur ajoutée car :**

-   Elles empêchent la fuite des données d’entreprise vers des applications et des services de particuliers.

-   Elles appliquent des restrictions (enregistrement sous, Presse-papiers, code confidentiel, etc.) aux applications mobiles.

-   Elles permettent d’effacer les données d’entreprise des applications sans supprimer ces applications de l’appareil.


### <a name="data-protection-with-mam-policies-for-devices-without-enrollment"></a>Protection des données avec des stratégies de gestion des applications mobiles pour les appareils sans inscription

![L’image qui montre le fonctionnement des stratégies de gestion des applications mobiles sur des appareils gérés](../media/MAM_ManagedDevices_November.png)

Le schéma précédent illustre le fonctionnement des stratégies de protection des données au niveau de l’application sans gestion des appareils mobiles.

Pour les appareils BYOD non inscrits dans une solution de gestion des appareils mobiles, les stratégies de gestion des applications mobiles peuvent faciliter la protection des données d’entreprise au niveau de l’application.

Cependant, il existe certaines limites à connaître :

-   Vous ne pouvez pas déployer des applications sur l’appareil. L’utilisateur doit obtenir les applications depuis le Store.

-   Vous ne pouvez pas configurer des profils de certificat sur ces appareils.

-   Vous ne pouvez pas configurer des paramètres VPN et Wi-Fi d’entreprise sur ces appareils.


## <a name="multi-identity"></a>Prise en charge de plusieurs identités

Les applications qui prennent en charge plusieurs identités vous permettent d’utiliser des comptes différents (professionnels et personnels) pour accéder aux mêmes applications, alors que les stratégies de gestion des applications mobiles sont appliquées uniquement quand les applications sont utilisées dans le contexte professionnel.  

Par exemple, quand un utilisateur démarre l’application OneDrive à l’aide de son compte professionnel, il ne peut pas déplacer les fichiers vers un emplacement de stockage personnel. Toutefois, quand il utilise OneDrive avec son compte personnel, il peut copier et déplacer des données à partir de son compte personnel OneDrive sans restriction.  

Toutes les applications mobiles Office prennent en charge l’accès de plusieurs identités.

##  <a name="next-steps"></a>Étapes suivantes
- [Se préparer à configurer des stratégies de gestion des applications mobiles](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Créer et déployer des stratégies de gestion des applications mobiles à l’aide de Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Nov16_HO5-->


