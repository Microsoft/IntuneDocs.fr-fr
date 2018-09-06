---
title: Que sont les stratégies de protection des applications ?
titleSuffix: Microsoft Intune
description: Découvrez comment les stratégies de protection d’application Microsoft Intune vous aident à protéger vos données d’entreprise et éviter les pertes de données.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 08/16/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e9dbda4c768bf9963a4ec168d6a613dca197995
ms.sourcegitcommit: c5cba0f4bf01eb9a9492e4e3fb6cd756f0737057
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2018
ms.locfileid: "40251756"
---
# <a name="what-are-app-protection-policies"></a>Que sont les stratégies de protection des applications ?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Les stratégies de protection d’application Microsoft Intune vous aident à protéger vos données d’entreprise et éviter les pertes de données.

## <a name="how-you-can-protect-app-data"></a>Comment protéger les données d’application
Vos employés utilisent des appareils mobiles pour des tâches à la fois personnelles et professionnelles.  Tout en veillant à ce que vos employés soient productifs, vous voulez éviter toute perte de données, qu’elle soit intentionnelle ou non.  Vous devez également avoir la possibilité de protéger des données d’entreprise accessibles à l’aide d’appareils même si vous ne les gérez pas.

Vous pouvez utiliser des stratégies de protection des applications Intune pour protéger les données de votre entreprise. Étant donné que les stratégies de gestion des applications mobiles Intune sont **indépendantes de toute solution de gestion des appareils mobiles (MDM)**, vous pouvez les utiliser pour protéger les données de votre entreprise en inscrivant ou non les appareils dans une solution de gestion des appareils. En implémentant des **stratégies au niveau de l’application**, vous pouvez restreindre l’accès aux ressources d’entreprise et conserver les données au sein de votre département informatique.

Vous pouvez configurer des stratégies de protection d’application pour les applications exécutées sur des appareils :

- **inscrits dans Microsoft Intune :** les appareils de cette catégorie sont généralement ceux possédés par une entreprise ;

- **inscrits dans une solution de gestion d’appareils mobiles tierce :** les appareils de cette catégorie sont généralement des appareils possédés par une entreprise.

  > [!NOTE]
  > Les stratégies de gestion des applications mobiles ne doivent pas être utilisées avec des solutions de gestion des applications mobiles tierces ni des solutions de conteneur sécurisé.

- **non inscrits dans une solution de gestion d’appareils mobiles :** les appareils de cette catégorie sont généralement la propriété d’employés et ne sont pas gérés ou inscrits dans Intune ou d’autres solutions de gestion des appareils mobiles.

> [!IMPORTANT]
> Vous pouvez créer des stratégies de gestion des applications mobiles pour les applications mobiles Office qui se connectent aux services Office 365. Vous pouvez également protéger l’accès aux boîtes aux lettres Exchange sur site en créant des stratégies Intune App Protection pour Outlook sous iOS et Android avec authentification moderne hybride. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux [exigences relatives à Outlook pour iOS et Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Les stratégies de protection d’applications ne sont pas prises en charge pour les autres applications qui se connectent à des services Exchange ou SharePoint sur site.

**Les principaux avantages de l’utilisation de stratégies de protection des applications sont les suivants :**

-   Protection des données de votre entreprise au niveau de l’application.  Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils.

-   La productivité des utilisateurs finaux n’est pas affectée et les stratégies ne sont pas appliquées pour une utilisation de l’application dans un contexte personnel.  Les stratégies sont appliquées uniquement dans un contexte professionnel, vous donnant ainsi la possibilité de protéger les données d’entreprise sans toucher aux données personnelles.

Il existe d’autres avantages à utiliser la gestion des appareils mobiles (MDM) avec des stratégies de protection des applications mobiles (GAM). Les entreprises peuvent avoir recours aux deux simultanément. Par exemple, un employé peut utiliser un téléphone fourni par l’entreprise ainsi qu’une tablette personnelle.  Dans ce cas, le téléphone de l’entreprise est inscrit dans la gestion des appareils mobiles et protégé par des stratégies de protection des applications, tandis que l’appareil personnel est protégé par des stratégies de protection des applications uniquement.

- **La gestion des appareils mobiles permet de s’assurer que l’appareil est protégé**.  Par exemple, vous pouvez demander un code confidentiel pour accéder à l’appareil ou déployer des applications gérées sur l’appareil. Vous pouvez également déployer des applications sur des appareils via votre solution MDM, pour mieux contrôler la gestion des applications.

- **Les stratégies de protection des applications permettent de veiller à ce que des protections de la couche application soient en place**. Par exemple, vous pouvez exiger un code confidentiel pour ouvrir une application dans un contexte professionnel, pour partager les données entre les applications ou pour empêcher les données d’application de l’entreprise d’être enregistrées dans un emplacement de stockage personnel.


### <a name="supported-platforms-for-app-protection-polices"></a>Plateformes prises en charge pour les stratégies de protection d’application
La prise en charge de la plateforme des stratégies de protection d’application Intune est alignée avec la prise en charge de la plateforme des applications Office. Pour plus d’informations, consultez [Configuration système requise pour Office](https://products.office.com/en-US/office-system-requirements).

Les appareils Windows ne sont pas pris en charge actuellement. Toutefois, quand vous inscrivez des appareils Windows 10 auprès d’Intune, vous pouvez utiliser la Protection des informations Windows, qui offre des fonctionnalités similaires. Pour plus d’informations, consultez [Protéger vos données d’entreprise à l’aide de la Protection des informations Windows (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
##  <a name="how-app-protection-policies-protect-app-data"></a>Comment les stratégies de protection d’application protègent les données d’application

####  <a name="apps-without-app-protection-policies"></a>Applications sans stratégies de protection des applications

![L’image qui affiche des données peut se déplacer librement entre les applications si aucune stratégie de protection des applications n’est mise en place](./media/apps-without-protection-policies.png)

Lorsque les applications sont utilisées sans aucune restriction, les données d’entreprise et personnelles peuvent se mélanger.  Les données d’entreprise peuvent alors finir dans des emplacements de stockage personnels ou être transmises à des applications hors de votre portée, entraînant une perte de données. Les flèches dans le diagramme indiquent un déplacement des données sans restriction entre les applications (professionnelles et personnelles) et vers des emplacements de stockage.


### <a name="data-protection-with-app-protection-policies"></a>Protection des données avec stratégies de protection des applications

![L’image qui montre comment les données d’entreprise sont protégées lorsque des stratégies de protection d’application sont appliquées ](./media/apps-with-protection-policies.png)


Vous pouvez utiliser des stratégies de protection d’application pour empêcher l’enregistrement des sur le stockage local de l’appareil et limiter le déplacement des données vers d’autres applications qui ne sont pas protégées par des stratégies de protection d’application. Les paramètres de stratégie de protection d’application comprennent :
- Stratégies de réadressage de données telles qu’**Interdire Enregistrer sous**, **Restreindre les opérations couper, copier et coller**.
- Paramètres de stratégie d’accès tels que **Demander un code confidentiel simple pour l'accès** et **Bloquer l’exécution des applications gérées sur les appareils jailbroken ou rootés**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>Protection des données avec des stratégies de protection d’application sur des appareils gérés par une solution de gestion des appareils mobiles

![L’image qui montre le fonctionnement des stratégies de protection d’application sur les appareils BYOD](./media/app-protection-policies-with-mdm.png)

**Pour les appareils inscrits dans une solution de gestion des appareils mobiles (MDM)**-

L’illustration ci-dessus montre les couches de protection offertes par les stratégies combinées de gestion des appareils mobiles et de protection d’application.

La solution de gestion des appareils mobiles :

-   Inscrit l’appareil.

-   Déploie les applications sur l’appareil.

-   Assure la gestion et la conformité de l’appareil en continu.

**Les stratégies de protection des applications ajoutent de la valeur des façons suivantes :**

-   Elles empêchent les données d’entreprise de s’échapper vers des applications et de services de particuliers.

-   Elles appliquent des restrictions (enregistrement sous, Presse-papiers, code confidentiel, etc.) aux applications mobiles.

-   Elles permettent d’effacer les données d’entreprise des applications sans supprimer ces applications de l’appareil.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Protection des données avec des stratégies de protection d’application pour les appareils sans inscription

![L’image qui montre le fonctionnement des stratégies de protection d’application sur les appareils gérés](./media/app-protection-policies-without-mdm.png)

Le diagramme ci-dessus illustre comment les stratégies de protection des données fonctionnent au niveau de l’application sans gestion des appareils mobiles.

Pour les appareils BYOD non inscrits dans une solution de protection d’application, les stratégies de gestion des applications mobiles peuvent faciliter la protection des données d’entreprise au niveau de l’application.
Cependant, il existe certaines limites à connaître, dont voici des exemples :

-   Vous ne pouvez déployer des applications sur l’appareil.  L’utilisateur final doit obtenir les applications depuis le Store.

-   Vous ne pouvez pas configurer des profils de certificat sur ces appareils.

-   Vous ne pouvez pas configurer des paramètres VPN et Wi-Fi d’entreprise sur ces appareils.


## <a name="multi-identity"></a>Prise en charge de plusieurs identités

Les applications qui prennent en charge plusieurs identités vous permettent d’utiliser des comptes différents (professionnels et personnels) pour accéder aux mêmes applications, alors que les stratégies de protection des applications sont appliquées uniquement quand les applications sont utilisées dans le contexte professionnel.

Par exemple, quand un utilisateur démarre l’application OneDrive à l’aide de son compte professionnel, il ne peut pas déplacer les fichiers vers un emplacement de stockage personnel. Toutefois, quand il utilise OneDrive avec son compte personnel, il peut copier et déplacer des données à partir de son compte personnel OneDrive sans restriction.

- En savoir plus sur les applications qui prennent en charge [GAM et plusieurs identités](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) avec Intune.

##  <a name="next-steps"></a>Étapes suivantes

[Guide pratique de création et déploiement des stratégies de protection d’application à l’aide de Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Voir aussi
Les applications tierces, comme l’application mobile Salesforce, fonctionnent avec Intune de façon à protéger les données d’entreprise. Pour plus d’informations sur le fonctionnement avec Intune de l’application Salesforce en particulier (notamment les paramètres de configuration de l’application MDM), consultez la section [Application Salesforce et Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
