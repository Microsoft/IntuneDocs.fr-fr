---
title: Que sont les stratégies de protection des applications ?
titleSuffix: Microsoft Intune
description: Découvrez comment les stratégies de protection d’application Microsoft Intune vous aident à protéger vos données d’entreprise et éviter les pertes de données.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbb6a8f159aebe837fabf671a84dd96223298227
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836351"
---
# <a name="what-are-app-protection-policies"></a>Que sont les stratégies de protection des applications ?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les stratégies de protection d’application Microsoft Intune vous aident à protéger vos données d’entreprise et éviter les pertes de données.

## <a name="how-you-can-protect-app-data"></a>Comment protéger les données d’application
Vos employés utilisent des appareils mobiles pour des tâches à la fois personnelles et professionnelles. En veillant à ce que vos employés soient productifs, vous voulez éviter toute perte de données, qu’elle soit intentionnelle ou non. Vous voulez également protéger les données d’entreprise qui sont accessible à partir d’appareils que vous ne gérez pas vous-même.

Vous pouvez utiliser des stratégies de protection des applications Intune **indépendamment de toute solution de gestion des appareils mobiles (GAM)**. Cette indépendance vous permet de protéger les données de votre entreprise avec ou sans l’inscription des appareils dans une solution de gestion des appareils. En implémentant des **stratégies au niveau de l’application**, vous pouvez restreindre l’accès aux ressources d’entreprise et conserver les données au sein de votre département informatique.

Vous pouvez configurer des stratégies de protection des applications pour les applications qui s’exécutent sur des appareils qui sont :

- **Inscrits dans Microsoft Intune :** ces appareils appartiennent généralement à l’entreprise.

- **Inscrits dans une solution de gestion des appareils mobiles (MDM) tierce :** ces appareils appartiennent généralement à l’entreprise.

  > [!NOTE]
  > Les stratégies de gestion des applications mobiles ne doivent pas être utilisées avec des solutions de gestion des applications mobiles tierces ni des solutions de conteneur sécurisé.

- **Non inscrits dans une solution de gestion des appareils mobiles (MDM) :** ces appareils sont généralement la propriété d’employés et ne sont pas gérés ou inscrits dans Intune ou d’autres solutions MDM.

> [!IMPORTANT]
> Vous pouvez créer des stratégies de gestion des applications mobiles pour les applications mobiles Office qui se connectent aux services Office 365. Vous pouvez également protéger l’accès aux boîtes aux lettres Exchange sur site en créant des stratégies Intune App Protection pour Outlook sous iOS et Android avec authentification moderne hybride. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux [exigences relatives à Outlook pour iOS et Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Les stratégies de protection d’applications ne sont pas prises en charge pour les autres applications qui se connectent à des services Exchange ou SharePoint sur site.

**Les principaux avantages de l’utilisation de stratégies de protection des applications sont les suivants :**

-   Protection des données de votre entreprise au niveau de l’application. Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils.

-   La productivité des utilisateurs finaux n’est pas affectée et les stratégies ne s’appliquent pas en cas d’utilisation de l’application dans un contexte personnel. Les stratégies sont appliquées uniquement dans un contexte professionnel, ce qui vous donne la possibilité de protéger les données d’entreprise sans toucher aux données personnelles.

Il existe d’autres avantages à utiliser la gestion des appareils mobiles (MDM) avec des stratégies de protection des applications, et les entreprises peuvent, ou non, les utiliser simultanément. Considérons, par exemple, un employé qui utilise à la fois un téléphone fourni par l’entreprise et sa propre tablette personnelle. Le téléphone de l’entreprise est inscrit dans la gestion des appareils mobiles (MAM) et protégé par des stratégies de protection des applications, tandis que l’appareil personnel est protégé uniquement par des stratégies de protection des applications.

- **La gestion des appareils mobiles permet de s’assurer que l’appareil est protégé**. Par exemple, vous pouvez demander un code confidentiel pour accéder à l’appareil ou déployer des applications gérées sur l’appareil. Vous pouvez également déployer des applications sur des appareils via votre solution MDM, pour mieux contrôler la gestion des applications.

- **Les stratégies de protection des applications permettent de veiller à ce que des protections de la couche application soient en place**. Par exemple, vous pouvez :
  - Exiger un code PIN pour ouvrir une application dans un contexte professionnel 
  - Contrôler le partage de données entre applications 
  - Empêcher l’enregistrement des données des applications de l’entreprise dans un emplacement de stockage personnel


### <a name="supported-platforms-for-app-protection-policies"></a>Plateformes prises en charge pour les stratégies de protection des applications
La prise en charge de la plateforme des stratégies de protection des applications Intune s’aligne sur la prise en charge de la plateforme des applications mobiles Office pour les appareils Android et iOS. Pour plus d’informations, consultez la section **Applications mobiles** de la [Configuration requise pour Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

Les appareils Windows ne sont pas pris en charge actuellement. Toutefois, vous pouvez utiliser Windows Information Protection, qui offre des fonctionnalités similaires. Pour plus d’informations, consultez [Protéger vos données d’entreprise à l’aide de la Protection des informations Windows (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


## <a name="how-app-protection-policies-protect-app-data"></a>Comment les stratégies de protection d’application protègent les données d’application

#### <a name="apps-without-app-protection-policies"></a>Applications sans stratégies de protection des applications

![Image conceptuelle du déplacement des données entre des applications sans stratégies de protection](./media/apps-without-protection-policies.png)

Lorsque les applications sont utilisées sans aucune restriction, les données d’entreprise et personnelles peuvent se mélanger. Les données de l’entreprise peuvent finir dans des emplacements de stockage personnels ou être transmises à des applications hors de votre portée, ce qui peut entraîner une perte de données. Dans le diagramme précédent, les flèches indiquent un déplacement des données sans restriction entre des applications aussi bien professionnelles que personnelles, et vers des emplacements de stockage.


### <a name="data-protection-with-app-protection-policies"></a>Protection des données avec stratégies de protection des applications

![Image conceptuelle montrant des données d’entreprise protégées par des stratégies](./media/apps-with-protection-policies.png)


Vous pouvez utiliser des stratégies de protection des applications pour empêcher l’enregistrement des données de l’entreprise sur le stockage local de l’appareil. Vous pouvez également limiter le déplacement de données vers d’autres applications qui ne sont pas protégées par des stratégies de protection des applications. Les paramètres de stratégie de protection d’application comprennent :
- Des stratégies de réadressage des données comme **Empêcher Enregistrer sous** et **Restreindre les opérations Couper, Copier et Coller**.
- Des paramètres de stratégie d’accès comme **Demander un code confidentiel simple pour l’accès** et **Bloquer l’exécution des applications gérées sur les appareils jailbreakés ou rootés**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>Protection des données avec des stratégies de protection des applications sur des appareils gérés par une solution de gestion des appareils mobiles

![L’image qui montre le fonctionnement des stratégies de protection d’application sur les appareils BYOD](./media/app-protection-policies-with-mdm.png)

**Pour les appareils inscrits dans une solution de gestion des appareils mobiles (MDM)**-

L’illustration précédente montre les couches de protection offertes par les stratégies combinées de gestion des appareils mobiles et de protection des applications.

La solution de gestion des appareils mobiles :

-   Inscrit l’appareil.

-   Déploie les applications sur l’appareil.

-   Assure la gestion et la conformité de l’appareil en continu.

**Les stratégies de protection des applications ajoutent de la valeur des façons suivantes :**

-   Elles empêchent les données d’entreprise de s’échapper vers des applications et des services de particuliers.

-   Elles appliquent des restrictions comme *enregistrement sous*, *Presse-papiers* ou *code PIN* aux applications clientes.

-   Elles permettent d’effacer les données d’entreprise des applications sans supprimer ces applications de l’appareil.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Protection des données avec des stratégies de protection d’application pour les appareils sans inscription

![L’image qui montre le fonctionnement des stratégies de protection d’application sur les appareils gérés](./media/app-protection-policies-without-mdm.png)

Le schéma précédent illustre le fonctionnement des stratégies de protection des données au niveau de l’application sans gestion des appareils mobiles.

Pour les appareils BYOD non inscrits dans une solution de protection d’application, les stratégies de gestion des applications mobiles peuvent faciliter la protection des données d’entreprise au niveau de l’application.
Cependant, il existe certaines limites à connaître, dont voici des exemples :

-   Vous ne pouvez pas déployer des applications sur l’appareil. L’utilisateur final doit obtenir les applications depuis le Store.

-   Vous ne pouvez pas configurer des profils de certificat sur ces appareils.

-   Vous ne pouvez pas provisionner des paramètres VPN et Wi-Fi d’entreprise sur ces appareils.

## <a name="app-protection-global-policy"></a>Stratégie globale de protection des applications

Si un administrateur OneDrive accède à **admin.office.com** et sélectionne l’accès **Appareil**, il peut définir des contrôles **Gestion des applications mobiles** sur les applications clientes OneDrive et SharePoint. 

Les paramètres, disponibles dans la console d’administration de OneDrive, configurent une stratégie de protection des applications Intune spéciale appelée stratégie **Globale**. Applicable à tous les utilisateurs dans votre locataire, cette stratégie globale n’offre aucun moyen de contrôler le ciblage de stratégie. 

Une fois cette stratégie activée, les applications OneDrive et SharePoint pour iOS et Android sont protégées avec les paramètres sélectionnés par défaut. Un professionnel de l’informatique peut modifier cette stratégie dans la console Intune pour ajouter d’autres applications ciblées et modifier n’importe quel paramètre de la stratégie. 

Par défaut, il ne peut y avoir qu’une seule stratégie **Globale** par locataire. Toutefois, vous pouvez utiliser les [API Graph Intune](intune-graph-apis.md) pour créer des stratégies globales supplémentaires par locataire, mais nous vous le déconseillons. En effet, la résolution des problèmes liés à l’implémentation d’une telle stratégie peut s’avérer complexe.

Bien que la stratégie **Globale** s’applique à tous les utilisateurs dans votre locataire, toute stratégie de protection d’application Intune standard remplace ces paramètres.


## <a name="multi-identity"></a>Prise en charge de plusieurs identités

Les applications qui prennent en charge plusieurs identités vous permettent d’utiliser des comptes différents (professionnels et personnels) pour accéder aux mêmes applications, alors que les stratégies de protection des applications s’appliquent uniquement quand les applications sont utilisées dans le contexte professionnel.

Pour un exemple de contexte personnel, pensez à un utilisateur qui démarre un nouveau document dans Word, ceci est considéré comme un contexte personnel, donc les stratégies Intune App Protection ne sont pas appliquées. Une fois que le document est enregistré sur le compte OneDrive d’entreprise, il est considéré comme contexte d’entreprise et les stratégies Intune App Protection sont appliquées.

Pour un exemple de contexte professionnel, pensez à un utilisateur qui démarre l’application OneDrive à l’aide de son compte professionnel. Dans le contexte professionnel, il ne peut pas déplacer des fichiers vers un emplacement de stockage personnel. Plus tard, quand il utilise OneDrive avec son compte personnel, il peut copier et déplacer des données à partir de son compte personnel OneDrive sans restrictions.

- En savoir plus sur les applications qui prennent en charge [GAM et plusieurs identités](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) avec Intune.

## <a name="next-steps"></a>Étapes suivantes

[Guide pratique de création et déploiement des stratégies de protection d’application à l’aide de Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Voir aussi
Des applications tierces, comme l’application mobile Salesforce, fonctionnent avec Intune dans le but spécifique de protéger les données de l’entreprise. Pour plus d’informations sur le fonctionnement avec Intune de l’application Salesforce en particulier (notamment les paramètres de configuration de l’application MDM), consultez la section [Application Salesforce et Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
