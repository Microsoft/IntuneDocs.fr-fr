---
title: Vue d’ensemble des stratégies de protection des applications
titleSuffix: Microsoft Intune
description: Découvrez comment les stratégies de protection d’application Microsoft Intune vous aident à protéger vos données d’entreprise et éviter les pertes de données.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31bb0e2ff4379c55829afc65fb99b768c9099a47
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72498953"
---
# <a name="app-protection-policies-overview"></a>Vue d’ensemble des stratégies de protection des applications

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Les stratégies de protection des applications (APP) sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application. Une application gérée est une application à laquelle des stratégies de protection d’application sont appliquées et pouvant être gérée par Intune.

Les stratégies de protection des applications de gestion des applications mobiles vous permettent de gérer et de protéger les données de votre organisation au sein d’une application. La **gestion MAM sans inscription** (MAM-WE) permet de gérer les applications professionnelles et scolaires contenant des données sensibles sur pratiquement tous types [d’appareils](app-management.md#app-management-capabilities-by-platform), y compris les appareils personnels dans les scénarios **BYOD (Apportez votre propre appareil)** . Plusieurs applications de productivité, telles que les applications Microsoft Office, peuvent être gérées par la MAM Intune. Consultez la liste officielle des [applications protégées par Microsoft Intune](apps-supported-intune-apps.md) accessibles au public.

## <a name="how-you-can-protect-app-data"></a>Comment protéger les données d’application
Vos employés utilisent des appareils mobiles pour des tâches à la fois personnelles et professionnelles. En veillant à ce que vos employés soient productifs, vous voulez éviter toute perte de données, qu’elle soit intentionnelle ou non. Vous voulez également protéger les données d’entreprise qui sont accessible à partir d’appareils que vous ne gérez pas vous-même.

Vous pouvez utiliser des stratégies de protection des applications Intune **indépendamment de toute solution de gestion des appareils mobiles (GAM)** . Cette indépendance vous permet de protéger les données de votre entreprise avec ou sans l’inscription des appareils dans une solution de gestion des appareils. En implémentant des **stratégies au niveau de l’application**, vous pouvez restreindre l’accès aux ressources d’entreprise et conserver les données au sein de votre département informatique.

### <a name="app-protection-policies-on-devices"></a>Stratégies de protection des applications sur les appareils

Vous pouvez configurer des stratégies de protection des applications pour les applications qui s’exécutent sur des appareils qui sont :

- **Inscrits dans Microsoft Intune :** ces appareils appartiennent généralement à l’entreprise.

- **Inscrits dans une solution de gestion des appareils mobiles (MDM) tierce :** ces appareils appartiennent généralement à l’entreprise.

  > [!NOTE]
  > Les stratégies de gestion des applications mobiles ne doivent pas être utilisées avec des solutions de gestion des applications mobiles tierces ni des solutions de conteneur sécurisé.

- **Non inscrits dans une solution de gestion des appareils mobiles (MDM) :** Ces appareils sont généralement la propriété d’employés et ne sont pas gérés ou inscrits dans Intune ou d’autres solutions MDM.

> [!IMPORTANT]
> Vous pouvez créer des stratégies de gestion des applications mobiles pour les applications mobiles Office qui se connectent aux services Office 365. Vous pouvez également protéger l’accès aux boîtes aux lettres Exchange sur site en créant des stratégies Intune App Protection pour Outlook sous iOS et Android avec authentification moderne hybride. Avant d’utiliser cette fonctionnalité, vérifiez que vous répondez aux [exigences relatives à Outlook pour iOS et Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Les stratégies de protection d’applications ne sont pas prises en charge pour les autres applications qui se connectent à des services Exchange ou SharePoint sur site.

## <a name="benefits-of-using-app-protection-policies"></a>Avantages de l’utilisation de stratégies de protection des applications

Les principaux avantages de l’utilisation de stratégies de protection des applications sont les suivants :

- **Protection des données de votre entreprise au niveau de l’application.** Étant donné que la gestion des applications mobiles ne nécessite pas de gestion des appareils, vous pouvez protéger les données d’entreprise à la fois sur les appareils gérés et non gérés. La gestion est centrée autour de l’identité de l’utilisateur, ce qui supprime la nécessité de gérer les appareils.

- **La productivité des utilisateurs finaux n’est pas affectée et les stratégies ne s’appliquent pas en cas d’utilisation de l’application dans un contexte personnel.** Les stratégies sont appliquées uniquement dans un contexte professionnel, ce qui vous donne la possibilité de protéger les données d’entreprise sans toucher aux données personnelles.

- **Les stratégies de protection des applications permettent de veiller à ce que des protections de la couche application soient en place.** Par exemple, vous pouvez :
  - Exiger un code PIN pour ouvrir une application dans un contexte professionnel 
  - Contrôler le partage de données entre applications 
  - Empêcher l’enregistrement des données des applications de l’entreprise dans un emplacement de stockage personnel

- **La gestion des appareils mobiles, en plus de celle des applications mobiles, permet de s’assurer que l’appareil est protégé**. Par exemple, vous pouvez demander un code confidentiel pour accéder à l’appareil ou déployer des applications gérées sur l’appareil. Vous pouvez également déployer des applications sur des appareils via votre solution MDM, pour mieux contrôler la gestion des applications.

Il existe d’autres avantages à utiliser la gestion des appareils mobiles (MDM) avec des stratégies de protection des applications, et les entreprises peuvent, ou non, les utiliser simultanément. Considérons, par exemple, un employé qui utilise à la fois un téléphone fourni par l’entreprise et sa propre tablette personnelle. Le téléphone de l’entreprise est inscrit dans la gestion des appareils mobiles (MAM) et protégé par des stratégies de protection des applications, tandis que l’appareil personnel est protégé uniquement par des stratégies de protection des applications.

Si vous appliquez une stratégie de gestion MAM à l’utilisateur sans définir l’état de l’appareil, l’utilisateur reçoit la stratégie à la fois sur l’appareil BYOD et sur l’appareil géré par Intune. Il est également possible d’appliquer une stratégie de gestion MAM en fonction de l’état géré. Si vous créez une stratégie de protection d’applications, sélectionnez **Non** à côté de **Cibler tous les types d’application**. Ensuite, choisissez entre les deux solutions suivantes :
- Appliquer une stratégie de gestion MAM moins stricte aux appareils gérés par Intune et une autre plus stricte aux appareils non inscrits à la gestion MDM.
- Appliquer une stratégie de gestion MAM aux appareils non inscrits exclusivement.

## <a name="supported-platforms-for-app-protection-policies"></a>Plateformes prises en charge pour les stratégies de protection des applications

Intune propose toute une gamme de fonctionnalités qui vous permettent de gérer les applications dont vous avez besoin sur les appareils de votre choix. Pour plus d’informations, consultez [Fonctionnalités de gestion d’application par plateforme](app-management.md#app-management-capabilities-by-platform).

La prise en charge de la plateforme des stratégies de protection des applications Intune s’aligne sur la prise en charge de la plateforme des applications mobiles Office pour les appareils Android et iOS. Pour plus d’informations, consultez la section **Applications mobiles** de la [Configuration requise pour Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> Le Portail d’entreprise Intune est requis sur l’appareil pour recevoir des stratégies de protection des applications sur Android. Pour plus d’informations, consultez les [exigences d’applications d’accès au Portail d’entreprise Intune](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Comment les stratégies de protection d’application protègent les données d’application

### <a name="apps-without-app-protection-policies"></a>Applications sans stratégies de protection des applications

Lorsque les applications sont utilisées sans aucune restriction, les données d’entreprise et personnelles peuvent se mélanger. Les données de l’entreprise peuvent finir dans des emplacements de stockage personnels ou être transmises à des applications hors de votre portée, ce qui peut entraîner une perte de données. Dans le diagramme suivant, les flèches indiquent un déplacement des données sans restriction entre des applications aussi bien professionnelles que personnelles, et vers des emplacements de stockage.

![Image conceptuelle du déplacement des données entre des applications sans stratégies de protection](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Protection des données avec stratégies de protection des applications (APP)

Vous pouvez utiliser des stratégies de protection des applications pour empêcher l’enregistrement des données de l’entreprise sur le stockage local de l’appareil (voir l’image ci-dessous). Vous pouvez également limiter le déplacement de données vers d’autres applications qui ne sont pas protégées par des stratégies de protection des applications. Les paramètres de stratégie de protection d’application comprennent :
- Des stratégies de réadressage des données comme **Empêcher Enregistrer sous** et **Restreindre les opérations Couper, Copier et Coller**.
- Des paramètres de stratégie d’accès comme **Demander un code confidentiel simple pour l’accès** et **Bloquer l’exécution des applications gérées sur les appareils jailbreakés ou rootés**.

![Image conceptuelle montrant des données d’entreprise protégées par des stratégies](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Protection des données avec application sur des appareils gérés par une solution de gestion des appareils mobiles

L’illustration ci-dessous montre les couches de protection offertes par les stratégies combinées de gestion des appareils mobiles et de protection des applications.

![L’image qui montre le fonctionnement des stratégies de protection d’application sur les appareils BYOD](./media/app-protection-policy/app-protection-policies-with-mdm.png)

La solution de gestion des appareils mobiles ajoute de la valeur en fournissant les éléments suivants :

- Inscrit l’appareil.
- Déploie les applications sur l’appareil.
- Assure la gestion et la conformité de l’appareil en continu.

Les stratégies de protection des applications ajoutent de la valeur en fournissant les éléments suivants :

- Empêcher la fuite des données d’entreprise vers des applications et des services de particuliers
- Appliquer des restrictions comme *enregistrement sous*, *Presse-papiers* ou *code PIN* aux applications clientes
- Elles permettent d’effacer les données d’entreprise des applications lorsque cela est nécessaire sans supprimer ces applications de l’appareil

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Protection des données avec des stratégies de protection des données d’application pour les appareils sans inscription

Le schéma suivant illustre le fonctionnement des stratégies de protection des données au niveau de l’application sans gestion des appareils mobiles.

![Image qui montre comment les stratégies de protection des applications fonctionnent sur les appareils sans inscription (appareils non gérés)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

Pour les appareils BYOD non inscrits dans une solution de protection d’application, les stratégies de gestion des applications mobiles peuvent faciliter la protection des données d’entreprise au niveau de l’application.
Cependant, il existe certaines limites à connaître, dont les suivantes :

- Vous ne pouvez pas déployer des applications sur l’appareil. L’utilisateur final doit obtenir les applications depuis le Store.
- Vous ne pouvez pas configurer des profils de certificat sur ces appareils.
- Vous ne pouvez pas provisionner des paramètres VPN et Wi-Fi d’entreprise sur ces appareils.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Applications que vous pouvez gérer avec des stratégies de protection des applications

Toute application intégrée avec le [Kit de développement logiciel (SDK) d’applications Intune](../developer/app-sdk.md) ou packagée par [l’outil de création de packages d’applications Intune](../developer/apps-prepare-mobile-application-management.md) peut être gérée à l’aide de stratégies de protection des applications Intune. Reportez-vous à la liste officielle des [applications protégées par Microsoft Intune](apps-supported-intune-apps.md) qui ont été créées à l’aide de ces outils et qui sont disponibles pour une utilisation publique.

L’équipe de développement SDK Intune teste et maintient activement la prise en charge des applications générées avec les plateformes Android, iOS (Obj-C, Swift), Xamarin, Xamarin.Forms et Cordova natives. Bien que certains clients aient réussi l’intégration du SDK Intune avec d’autres plateformes comme React Native et NativeScript, nous ne fournissons pas de conseils explicites ou de plug-ins pour les développeurs d’applications utilisant d’autres plateformes que celles que nous prenons en charge.

Le [kit de développement logiciel (SDK) d’application Intune](../developer/app-sdk.md) utilise des fonctionnalités d’authentification modernes avancées des [bibliothèques d’authentification Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) pour les versions de première partie et tierces du SDK. En l’état, la [bibliothèque d’authentification Microsoft](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) ne fonctionne pas correctement dans la plupart de nos scénarios de base, comme l’authentification dans le service Intune App Protection et le lancement conditionnel. Étant donné que les instructions de l’équipe Microsoft Identity sont de passer à MSAL pour toutes les applications Microsoft Office, le [SDK d’application Intune](../developer/app-sdk.md) devra la prendre en charge, mais cela n’est pas prévu pour le moment.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Conditions requises par l’utilisateur final pour utiliser des stratégies de protection des applications

La liste suivante indique la configuration requise pour que l’utilisateur final puisse utiliser des stratégies de protection des applications sur une application gérée par Intune :

- L’utilisateur final doit avoir un compte Azure Active Directory (AAD). Consultez la page [Ajouter des utilisateurs et accorder une autorisation d’administration à Intune](../fundamentals/users-add.md) pour apprendre à créer des utilisateurs Intune dans Azure Active Directory.

- L’utilisateur final doit disposer d’une licence pour Microsoft Intune, attribuée à son compte Azure Active Directory. Consultez la section [Gérer les licences Intune](../fundamentals/licenses-assign.md) pour apprendre à attribuer des licences Intune à des utilisateurs finaux.

- L’utilisateur final doit appartenir à un groupe de sécurité ciblé par une stratégie de protection des applications. La même stratégie de protection des applications doit cibler l’application spécifique utilisée. Des stratégies de protection des applications peuvent être créées et déployées dans la console Intune dans le [portail Azure](https://portal.azure.com). Des groupes de sécurité peuvent actuellement être créés dans le [centre d’administration Microsoft 365](https://admin.microsoft.com).

- L’utilisateur final doit se connecter à l’application à l’aide de son compte AAD.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Stratégies de protection des applications pour les applications Microsoft Office

Il existe quelques exigences supplémentaires que vous devez connaître lorsque vous utilisez des stratégies de protection des applications avec des applications Microsoft Office.

### <a name="outlook-mobile-app"></a>Application mobile Outlook
Les exigences supplémentaires pour utiliser [l’application mobile Outlook](https://products.office.com/outlook) comprennent les suivantes :

- L’utilisateur final doit avoir installé l’application mobile Outlook sur son appareil.
- L’utilisateur final doit disposer d’une boîte aux lettres [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) et d’une licence associée à son compte Azure Active Directory.

  >[!NOTE]
  > L’application mobile Outlook prend actuellement en charge uniquement Intune App Protection pour Microsoft Exchange Online et [Exchange Server avec authentification moderne hybride](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) et ne prend pas en charge Exchange dédié à Office 365.

### <a name="word-excel-and-powerpoint"></a>Word, Excel et PowerPoint
Les exigences supplémentaires pour utiliser [les applications mobiles Word, Excel et PowerPoint](https://products.office.com/business/office) comprennent les suivantes :

- L’utilisateur final doit disposer d’une licence pour [Office 365 Business ou Entreprise](https://products.office.com/business/compare-more-office-365-for-business-plans), associée à son compte Azure Active Directory. L’abonnement doit inclure les applications Office sur des appareils mobiles et peut inclure un compte de stockage cloud avec [OneDrive Entreprise](https://onedrive.live.com/about/business/). Des licences Office 365 peuvent être attribuées dans le [centre d’administration Microsoft 365](https://admin.microsoft.com) en tenant compte des [instructions suivantes](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- L’utilisateur final doit avoir configuré un emplacement géré à l’aide de la fonctionnalité granulaire Enregistrer sous, qui se trouve sous le paramètre de stratégie de protection des applications « Empêcher Enregistrer sous ». Si, par exemple, l’emplacement géré est OneDrive, l’application [OneDrive](https://onedrive.live.com/about/) doit être configurée dans l’application Word, Excel ou PowerPoint de l’utilisateur final.

- Si l’emplacement géré est OneDrive, l’application doit être ciblée par la stratégie de protection des applications déployée pour l’utilisateur final.

  >[!NOTE]
  > Les applications mobiles Office prennent actuellement en charge uniquement SharePoint Online et SharePoint on-premises.

### <a name="managed-location-needed-for-office"></a>Emplacement géré requis pour Office
Un emplacement géré (p. ex., OneDrive) est nécessaire pour Office. Intune marque toutes les données de l’application en tant que données « d’entreprise » ou « personnelles ». Les données sont considérées comme « d’entreprise » lorsqu’elles proviennent d’un emplacement de l’entreprise. Pour les applications Office, Intune considère les sites d’entreprise suivants : e-mail (Exchange) ou stockage cloud (application OneDrive avec un compte OneDrive Entreprise).

### <a name="skype-for-business"></a>Skype pour Entreprises
Il existe des exigences supplémentaires pour utiliser Skype Entreprise. Voir les conditions requises pour les licences de [Skype Entreprise](https://products.office.com/skype-for-business/it-pros). Pour les configurations Skype Entreprise hybrides et locales, consultez l’article annonçant que [l’authentification moderne hybride pour Skype Entreprise et Exchange passe en disponibilité générale](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) et [Authentification moderne pour Skype Entreprise local avec AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910), respectivement.

## <a name="app-protection-global-policy"></a>Stratégie globale de protection des applications

Si un administrateur OneDrive accède à **admin.office.com** et sélectionne l’accès **Appareil**, il peut définir des contrôles **Gestion des applications mobiles** sur les applications clientes OneDrive et SharePoint. 

Les paramètres, disponibles dans la console d’administration de OneDrive, configurent une stratégie de protection des applications Intune spéciale appelée stratégie **Globale**. Applicable à tous les utilisateurs dans votre locataire, cette stratégie globale n’offre aucun moyen de contrôler le ciblage de stratégie. 

Une fois cette stratégie activée, les applications OneDrive et SharePoint pour iOS et Android sont protégées avec les paramètres sélectionnés par défaut. Un professionnel de l’informatique peut modifier cette stratégie dans la console Intune pour ajouter d’autres applications ciblées et modifier n’importe quel paramètre de la stratégie. 

Par défaut, il ne peut y avoir qu’une seule stratégie **Globale** par locataire. Toutefois, vous pouvez utiliser les [API Graph Intune](../developer/intune-graph-apis.md) pour créer des stratégies globales supplémentaires par locataire, mais nous vous le déconseillons. En effet, la résolution des problèmes liés à l’implémentation d’une telle stratégie peut s’avérer complexe.

Bien que la stratégie **Globale** s’applique à tous les utilisateurs dans votre locataire, toute stratégie de protection d’application Intune standard remplace ces paramètres.

## <a name="app-protection-features"></a>Fonctionnalités de protection des applications

### <a name="multi-identity"></a>Prise en charge de plusieurs identités

La prise en charge de plusieurs identités permet à une application de prendre en charge plusieurs publics. Ces publics sont à la fois des utilisateurs « d’entreprise » et des utilisateurs « personnels ». Les comptes professionnels et scolaires sont utilisés par les publics « d’entreprise », tandis que les comptes personnels sont utilisés pour les publics de consommateurs, comme les utilisateurs de Microsoft Office. Une application qui prend en charge la multi-identité peut être publiée publiquement ; les stratégies de protection des applications s’appliquent alors uniquement lorsque l’application est utilisée dans le contexte professionnel et scolaire (« entreprise »). La prise en charge de la multi-identité utilise le [Kit de développement logiciel (SDK) d’application Intune](../developer/app-sdk.md) d’appliquer des stratégies de protection des applications uniquement au compte professionnel ou scolaire connecté à l’application. Si un compte personnel est connecté à l’application, les données restent intactes.

Pour un exemple de contexte « personnel », pensez à un utilisateur qui démarre un nouveau document dans Word, ceci est considéré comme un contexte personnel, donc les stratégies Intune App Protection ne sont pas appliquées. Une fois que le document est enregistré sur le compte OneDrive « d’entreprise », il est considéré comme contexte « d’entreprise » et les stratégies Intune App Protection sont appliquées.

Pour un exemple de contexte « professionnel », pensez à un utilisateur qui démarre l’application OneDrive à l’aide de son compte professionnel. Dans le contexte professionnel, il ne peut pas déplacer des fichiers vers un emplacement de stockage personnel. Plus tard, quand il utilise OneDrive avec son compte personnel, il peut copier et déplacer des données à partir de son compte personnel OneDrive sans restrictions.

Outlook dispose d’une vue de messagerie combinée des e-mails « personnels » et « d’entreprise ». Dans ce cas, l’application Outlook vous invite à entrer le code confidentiel Intune au lancement.

Pour plus d’informations sur les identités multiples dans Intune, consultez [MAM et multi-identité](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>Code PIN d’application Intune

Le PIN (numéro d’identification personnel) est un code secret utilisé pour vérifier que l’utilisateur qui accède aux données de l’organisation dans une application y est autorisé.

**Invite à entrer le code PIN**<br>
Intune n’invite l’utilisateur à saisir le code PIN de l’application que s’il est sur le point d’accéder à des données « d’entreprise ». Dans les applications multi-identité telles que Word, Excel ou PowerPoint, l’utilisateur est invité à entrer son code PIN lorsqu’il tente d’ouvrir un fichier ou un document « d’entreprise ». Dans les applications à identité unique, par exemple, les applications métier gérées avec [l’outil de création de packages d’applications Intune](../developer/apps-prepare-mobile-application-management.md), le code PIN est demandé au lancement, car le [Kit de développement logiciel (SDK) d’applications Intune](../developer/app-sdk.md) sait que l’expérience utilisateur dans l’application est toujours de type « entreprise ».

**Fréquence de l’invite de code PIN**<br>
L’administrateur informatique peut définir le paramètre de stratégie de protection des applications Intune **Revérifier les exigences d’accès après (minutes)** dans la console d’administration Intune. Ce paramètre spécifie le délai avant que les conditions d’accès ne soient vérifiées sur l’appareil et que l’écran du code PIN de l’application ne réapparaisse. Voici cependant des informations importantes sur le code PIN qui affectent la fréquence à laquelle il est demandé à l’utilisateur :

- **Le code PIN est partagé entre les applications du même éditeur pour améliorer la facilité d’utilisation :**<br> Sur iOS, un code PIN d’application est partagé entre toutes les applications **du même éditeur d’application**. Sur Android, un même code PIN d’application est partagé entre toutes les applications.
  - **Le comportement *Revérifier les exigences d’accès après (minutes)* , après un redémarrage de l’appareil :**<br> Un « minuteur de code PIN » suit le nombre de minutes d’inactivité déterminant quand le code PIN d’application Intune suivant doit être affiché. Sur iOS, le minuteur de code PIN n’est pas affecté par le redémarrage de l’appareil. Ainsi, le redémarrage de l’appareil n’a pas d’effet sur le nombre de minutes d’inactivité de l’utilisateur pour une application iOS avec la stratégie de code PIN Intune. Sur Android, le minuteur de code PIN est réinitialisé au redémarrage de l’appareil. Ainsi, les applications Android avec la stratégie de code PIN Intune vont probablement demander le code PIN d’une application, quelle que soit la valeur du paramètre « Revérifier les exigences d’accès après (minutes) » **après un redémarrage de l’appareil**.  
  - **La nature cyclique du minuteur associé au code PIN :**<br> une fois qu’un code PIN est entré pour accéder à une application (l’application A) et que l’application quitte le premier plan (le focus d’entrée principal) sur l’appareil, le minuteur du code PIN est réinitialisé pour ce code PIN. Une application (l’application B) partageant ce code PIN ne demande pas à l’utilisateur d’entrer ce code parce que la minuterie a été réinitialisée. L’invite réapparaît une fois que la valeur de « Revérifier les exigences d’accès après (minutes) » est à nouveau atteinte.

Pour les appareils iOS, même si le code PIN est partagé entre les applications de différents éditeurs, l’invite s’affiche à nouveau quand la valeur de **Revérifier les spécifications requises pour l’accès après (minutes)** est à nouveau atteinte pour l’application qui n’a pas le focus d’entrée principal. Par exemple, un utilisateur a application _A_ de l’éditeur _X_ et l’application _B_ de l’éditeur _Y_, et ces deux applications partagent le même code PIN. L’utilisateur travaille avec l’application _A_ (au premier plan) et l’application _B_ est réduite. Une fois que la valeur de **Revérifier les spécifications requises pour l’accès après (minutes)** est atteinte et que l’utilisateur passe à l’application _B_, celui-ci doit entrer le code PIN.

  >[!NOTE]
  > Afin de vérifier plus souvent les exigences d’accès de l’utilisateur (p. ex., en demandant un code PIN), en particulier pour les applications fréquemment utilisées, il est recommandé de réduire la valeur du paramètre « Revérifier les exigences d’accès après (minutes) ».

**Codes PIN d’application intégrés pour Outlook et OneDrive**<br>
Le code PIN Intune fonctionne sur la base d’un minuteur d’inactivité (la valeur de **Revérifier les exigences d’accès après (minutes)** ). Ainsi, la demande de code PIN Intune s’affiche indépendamment des demandes de code PIN de l’application intégrée pour Outlook et OneDrive, qui sont souvent liées par défaut au démarrage de l’application. Si l’utilisateur reçoit en même temps les deux demandes de code PIN, le comportement attendu doit être que le code PIN Intune est prioritaire.

**Sécurité du code PIN Intune**<br>
Le code PIN sert à autoriser uniquement les utilisateurs adéquats à accéder aux données de leur organisation dans l’application. Par conséquent, un utilisateur final doit se connecter avec son compte professionnel ou scolaire pour pouvoir définir ou réinitialiser son code PIN d’application Intune. Cette authentification est gérée par Active Directory Azure par le biais d’un échange de jeton sécurisé et n’est pas transparente pour le [Kit de développement logiciel (SDK) d’application Intune](../developer/app-sdk.md). Du point de vue de la sécurité, la meilleure manière de protéger les données professionnelles ou scolaires consiste à les chiffrer. Le chiffrement n’est pas lié au code PIN de l’application, mais constitue sa propre stratégie de protection des applications.

**Code PIN Intune - Protection contre les attaques par force brute**<br>
Dans le cadre de la stratégie de code PIN d’application, l’administrateur peut définir un nombre maximal de tentatives d’authentification de son code PIN avant le verrouillage de l’application. Une fois que le nombre de tentatives atteint, le [Kit de développement logiciel (SDK) d’application Intune](../developer/app-sdk.md) peut réinitialiser les données « d’entreprise » dans l’application.
  
**Vous définissez deux fois un code PIN sur des applications du même éditeur ?**<br>
La gestion MAM (sous iOS) autorise actuellement les codes PIN d’application composés de caractères alphanumériques et spéciaux (nommés « codes secrets ») qui impliquent la participation d’applications (p. ex., WXP, Outlook, Managed Browser ou Yammer) pour intégrer le [Kit SDK d’applications Intune pour iOS](../developer/app-sdk-ios.md). Sans cela, les paramètres de code secret ne sont pas appliqués correctement pour les applications ciblées. Il s’agissait d’une fonctionnalité publiée dans le SDK Intune pour iOS version 7.1.12.

Pour prendre en charge cette fonctionnalité et garantir la compatibilité descendante avec les versions antérieures du Kit SDK Intune pour iOS, tous les codes PIN (numériques ou codes secrets) à partir de la version 7.1.12 sont gérés séparément du code PIN numérique des versions précédentes du Kit SDK. Par conséquent, si un appareil contient des applications avec le Kit SDK Intune pour des versions iOS antérieures à 7.1.12 et ultérieures à 7.1.12 du même éditeur, deux codes PIN doivent être définis. Les deux codes PIN (pour chaque application) ne sont liés d’aucune manière et doivent respecter la stratégie de protection appliquée à l’application. Par conséquent, *uniquement* si les applications A et B ont les mêmes stratégies de code PIN, l’utilisateur peut définir deux fois le même code PIN. 

Ce comportement est propre au code PIN sur les applications iOS activées avec la gestion des applications mobiles Intune. Au fil du temps, à mesure que les applications adoptent les versions ultérieures du Kit SDK Intune pour iOS, définir deux fois un code PIN sur les applications d’un même éditeur pose moins de problèmes. Consultez la remarque ci-dessous pour obtenir un exemple.

  >[!NOTE]
  > Par exemple, si l’application A est générée avec une version antérieure à 7.1.12 et que l’application B est générée avec une version supérieure ou égale à 7.1.12 du même éditeur, l’utilisateur final devra définir séparément les codes PIN pour A et B si ces deux apps sont installées sur un appareil iOS.
  > Si une application C avec le Kit SDK version 7.1.9 est installée sur l’appareil, elle utilisera le même code PIN que l’application A. Une application D avec une version 7.1.14 partagera le même code PIN que l’application B.  
  > Si seules les applications A et C sont installées sur un appareil, vous devez définir un seul code PIN. Il en va de même si seules les applications B et D sont installées sur un appareil.

### <a name="app-data-encryption"></a>Chiffrement des données d’application
Les administrateurs informatiques peuvent déployer une stratégie de protection des applications nécessitant un chiffrement des données d’application. Dans le cadre de la stratégie, l’administrateur informatique peut également spécifier quand le contenu est chiffré.

**Comment fonctionne le processus de chiffrement des données Intune**<br> Consultez les [paramètres de stratégie de protection des applications Android](app-protection-policy-settings-android.md) et les [paramètres de stratégie de protection des applications iOS](app-protection-policy-settings-ios.md) pour plus d’informations sur le paramètre de chiffrement de stratégie de protection des applications.

**Les données chiffrées**<br>
Seules les données marquées comme « d’entreprise » sont chiffrées en fonction de la stratégie de protection des applications de l’administrateur. Les données sont considérées comme « d’entreprise » lorsqu’elles proviennent d’un emplacement de l’entreprise. Pour les applications Office, Intune considère les éléments suivants comme des emplacements d’entreprise :

- E-mail (Exchange) 
- Stockage cloud (application OneDrive avec un compte OneDrive Entreprise)

Dans le cas des applications métier gérées par [l’outil de création de packages d’applications Intune](../developer/apps-prepare-mobile-application-management.md), toutes les données sont considérées comme étant de type « entreprise ».

**Réinitialiser les données à distance**<br>

Intune peut réinitialiser les données d’application de trois façons différentes : 
- Réinitialisation complète de l’appareil
- Réinitialisation sélective pour la gestion des appareils mobiles 
- Réinitialisation sélective pour gestion des applications mobiles

Pour plus d’informations sur la réinitialisation à distance pour la gestion MDM, consultez [Supprimer des appareils avec la réinitialisation ou la mise hors service](../remote-actions/devices-wipe.md). Pour plus d’informations sur la réinitialisation sélective avec la gestion des applications mobiles, consultez [Action Mettre hors service](../remote-actions/devices-wipe.md#retire) et [Guide pratique pour effacer uniquement les données d’entreprise dans les applications](apps-selective-wipe.md).

La [réinitialisation ](../remote-actions/devices-wipe.md) supprime toutes les données et tous les paramètres utilisateur de **l’appareil** en rétablissant les paramètres d’usine par défaut de l’appareil. L’appareil est supprimé d’Intune.

  >[!NOTE]
  > La réinitialisation est possible seulement sur les appareils inscrits auprès de la gestion MDM d’Intune.

**Réinitialisation sélective pour la gestion des appareils mobiles**<br>
Pour plus d’informations sur la suppression des données d’entreprise, consultez [Supprimer des appareils - Mettre hors service](../remote-actions/devices-wipe.md#retire).

**Réinitialisation sélective pour la gestion des applications mobiles**<br>
La réinitialisation sélective pour la gestion des applications mobiles supprime simplement les données d’applications d’entreprise à partir d’une application. La requête est lancée à l’aide du portail Intune Azure. Pour savoir comment effectuer une demande de réinitialisation, consultez la section [Guide pratique pour effacer uniquement les données d’entreprise des applications](apps-selective-wipe.md).

Si l’utilisateur utilise l’application lorsque la réinitialisation sélective est lancée, le [Kit de développement logiciel (SDK) d’application Intune](../developer/app-sdk.md) contrôle toutes les 30 minutes la présence d’une requête de réinitialisation sélective du service de GAM Intune. Il vérifie également la présence d’une réinitialisation sélective lorsque l’utilisateur lance l’application pour la première fois et se connecte avec son compte professionnel ou scolaire.

**Quand les services locaux (on-prem) ne fonctionnent pas avec des applications protégées par Intune**<br>
La protection d’applications Intune dépend de la cohérence de l’identité de l’utilisateur entre l’application et le [Kit de développement logiciel (SDK) d’application Intune](../developer/app-sdk.md). L’authentification moderne est la seule manière de la garantir. Il existe des scénarios dans lesquels les applications peuvent fonctionner avec une configuration locale. Mais elles ne sont ni cohérentes, ni garanties.

**Moyen sécurisé d’ouvrir des liens web depuis des applications gérées**<br>
L’administrateur informatique peut déployer et définir la stratégie de protection des applications pour [l’application Intune Managed Browser](app-configuration-managed-browser.md), un navigateur web développé par Microsoft Intune qui peut être géré facilement avec Intune. L’administrateur informatique peut exiger que tous les liens web dans les applications gérées par Intune soient ouverts à l’aide de l’application Managed Browser.

## <a name="examples-of-app-protection-policies"></a>Exemples de stratégies de protection des applications

Pour en savoir plus sur les exemples de stratégies de protection des applications et pour obtenir des informations détaillées sur chaque paramètre de stratégie de protection des applications, consultez [Paramètres de stratégie de protection d’application Android](app-protection-policy-settings-android.md) et [Paramètres de stratégie de protection d’applications iOS](app-protection-policy-settings-ios.md).

## <a name="app-protection-experience-for-ios-devices"></a>Expérience de protection des applications pour les appareils iOS

### <a name="device-fingerprint-or-face-ids"></a>Empreinte digitale de l’appareil ou ID de visage 
Les stratégies Intune de protection des applications permettent de restreindre l’accès aux utilisateurs qui disposent d’une licence Intune. L’un des moyens de contrôler l’accès à une application est d’exiger un Touch ID ou un Face ID Apple sur les appareils pris en charge. Le comportement suivant est implémenté: si un changement est apporté à la base de données biométrique de l’appareil, Intune invite l’utilisateur à entrer un code PIN la prochaine fois que le délai d’attente d’inactivité est atteint. Les changements apportés aux données biométriques incluent l’ajout et la suppression d’une empreinte digitale ou d’un visage. Si l’utilisateur Intune n’a pas défini de code PIN, il est dirigé vers la page de configuration d’un code PIN Intune.
 
L’objectif de ce processus est de sécuriser les données de votre organisation au sein de l’application. Cette fonctionnalité est uniquement disponible pour iOS et nécessite la participation d’applications qui intègrent le SDK d’application Intune pour iOS 9.0.1 ou version ultérieure. L’intégration du SDK est nécessaire afin que le comportement puisse être ajouté aux applications ciblées. Cette intégration se produit en continu et repose sur les équipes d’application spécifiques. Certaines applications participantes incluent WXP, Outlook, Managed Browser et Yammer.
  
### <a name="ios-share-extension"></a>Extension de partage iOS
Vous pouvez utiliser l’extension de partage iOS pour ouvrir les données professionnelles ou scolaires dans des applications non gérées, même si la stratégie de transfert de données est définie sur les **Applications gérées uniquement** ou sur **Aucune application.** La stratégie de protection des applications Intune ne peut pas contrôler l’extension de partage iOS sans gérer l’appareil. Par conséquent, Intune _**chiffre les données « d’entreprise » avant de les partager à l’extérieur de l’application**_ . Vous pouvez valider ce comportement de chiffrement en essayant d’ouvrir un fichier « d’entreprise » en dehors de l’application gérée. Le fichier doit être chiffré et ne peut pas être ouvert en dehors de l’application gérée.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Plusieurs paramètres d’accès à la protection des applications Intune pour le même ensemble d’applications et d’utilisateurs
Les stratégies de protection des applications Intune pour l’accès sont appliquées dans un ordre spécifique sur les appareils des utilisateurs finaux quand ceux-ci tentent d’accéder à une application cible à partir de leur compte d’entreprise. En règle générale, une réinitialisation est prioritaire, suivie d’un blocage, puis d’un message d’avertissement. Par exemple, si cela s’applique à l’utilisateur/application en question, un paramètre de système d’exploitation iOS minimal qui signale à un utilisateur qu’il doit mettre à niveau sa version d’iOS est appliqué après le paramètre de système d’exploitation iOS minimal qui bloque l’accès à l’utilisateur. Ainsi, dans le scénario où l’administrateur informatique configure le système d’exploitation iOS minimal sur 11.0.0.0 et le système d’exploitation iOS minimal (Avertissement uniquement) sur 11.1.0.0, alors que l’appareil qui tente d’accéder à l’application utilise iOS 10, l’utilisateur final est bloqué sur la base du paramètre le plus restrictif pour la version de système d’exploitation iOS minimal qui provoque un blocage de l’accès.

Lors du traitement de différents types de paramètres, une exigence de version de SDK d’application Intune est prioritaire, suivie d’une exigence de version d’application, puis d’une exigence de version de système d’exploitation iOS. Ensuite, tous les avertissements pour tous les types de paramètres dans le même ordre sont vérifiés. Nous vous recommandons de configurer l’exigence de version de SDK d’application Intune uniquement sur recommandation de l’équipe de produit Intune pour les principaux scénarios de blocage.

## <a name="app-protection-experience-for-android-devices"></a>Expérience de protection des applications pour les appareils Android

### <a name="company-portal-app-and-intune-app-protection"></a>Protection de l’application du portail d'entreprise et de l’application Intune
La plupart des fonctionnalités de protection des applications sont intégrées à l’application Portail d’entreprise. L’inscription d’appareil n’est _pas obligatoire_, même si l’application Portail d’entreprise est toujours nécessaire. Pour la gestion des applications mobiles sans inscription (MAM-WE), l’utilisateur final doit simplement disposer de l’application Portail d’entreprise installée sur l’appareil.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Plusieurs paramètres d’accès à la protection des applications Intune pour le même ensemble d’applications et d’utilisateurs
Les stratégies de protection des applications Intune pour l’accès sont appliquées dans un ordre spécifique sur les appareils des utilisateurs finaux quand ceux-ci tentent d’accéder à une application cible à partir de leur compte d’entreprise. En règle générale, un blocage est prioritaire, puis un message d’avertissement. Par exemple, si cela s’applique à l’utilisateur/application en question, un paramètre de version de correctif Android minimale qui signale à un utilisateur qu’il doit effectuer une mise à niveau de correctif sera appliqué après le paramètre de version de correctif Android minimale qui bloque l’accès à l’utilisateur. Ainsi, dans le scénario où l’administrateur informatique configure la version de correctif Android minimale sur 2018-03-01 et la version de correctif Android minimale (Avertissement uniquement) sur 2018-02-01, alors que l’appareil qui tente d’accéder à l’application utilise une version de correctif 2018-01-01, l’utilisateur final est bloqué sur la base du paramètre le plus restrictif pour la version de correctif Android minimale qui provoque un blocage de l’accès. 

Lors du traitement de différents types de paramètres, une exigence de version d’application est prioritaire, suivie de l’exigence de version de système d’exploitation Android, puis de l’exigence de version de correctif Android. Ensuite, tous les avertissements pour tous les types de paramètres dans le même ordre sont vérifiés.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Stratégies de protection des applications Intune et attestation SafetyNet de Google pour les appareils Android 
Les stratégies Intune App Protection permettent aux administrateurs d’exiger que les appareils des utilisateurs finaux obtiennent l’Attestation SafetyNet de Google pour les appareils Android. Une nouvelle détermination de service Google Play est signalée à l’administrateur informatique à un intervalle déterminé par le service Intune. La fréquence à laquelle l’appel de service est effectué est limitée en raison de la charge. Ainsi, cette valeur est tenue à jour en interne et n’est pas configurable. Toute action configurée par l’administrateur informatique pour le paramètre d’Attestation SafetyNet de Google sera effectuée en fonction du dernier résultat signalé au service Intune au moment du lancement conditionnel. En l’absence de données, l’accès sera autorisé à condition qu’aucun autre contrôle de lancement conditionnel n’échoue, et un « aller-retour » de Google Play Services pour déterminer les résultats d’attestation commencera dans le back-end et invitera l’utilisateur de façon asynchrone si l’attestation de l’appareil a échoué. S’il existe des données périmées, l’accès sera bloqué ou autorisé en fonction du dernier résultat signalé, et un « aller-retour » de Google Play Services pour déterminer les résultats d’attestation commencera également et invitera l’utilisateur de façon asynchrone si l’attestation de l’appareil a échoué.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Stratégies de protection des applications Intune et API de vérification des applications de Google pour les appareils Android
Les stratégies Intune App Protection permettent aux administrateurs d’exiger que les appareils des utilisateurs finaux envoient des signaux par le biais de l’API de vérification des applications de Google pour les appareils Android. La procédure à suivre varie légèrement en fonction de l’appareil. Le processus général implique d’accéder au Google Play Store, de cliquer sur **Mes jeux et applications**, puis de cliquer sur le résultat de la dernière analyse de l’application afin d’accéder au menu Play Protect. Vérifiez que l’option **Rechercher les menaces de sécurité sur l’appareil** est activée.

### <a name="googles-safetynet-attestation-api"></a>API d’attestation SafetyNet de Google 
Intune tire parti des API SafetyNet Google Play Protect à ajouter à nos contrôles de détection du rootage pour les appareils non inscrits. Google développe et gère cet ensemble d’API pour les applications Android, à adopter s’il ne souhaite pas que ses applications s’exécutent sur des appareils rootés. L’application Android Pay a par exemple incorporé cette fonctionnalité. Bien que Google ne partage pas publiquement l’intégralité des contrôles de détection du rootage effectués, nous estimons que ces API sont capables de détecter les appareils qui ont été rootés par l’utilisateur. L’accès de ces utilisateurs peut alors être bloqué, ou leurs comptes professionnels supprimés des applications pour lesquelles une stratégie est activée. **Vérifier l’intégrité de base** vous informe quant à l’intégrité générale de l’appareil. Les appareils rootés, les émulateurs, les appareils virtuels et les appareils présentant des signes d’altération échouent aux tests d’intégrité de base. **Vérifier l’intégrité de base et les appareils certifiés** vous informe quant à la compatibilité de l’appareil avec les services de Google. Seuls les appareils non modifiés qui ont été certifiés par Google peuvent satisfaire à ce contrôle. Les appareils suivants échoueront :

- Appareils qui échouent aux tests d’intégrité de base
- Appareils ayant un chargeur de démarrage déverrouillé
- Appareils ayant une image système/ROM personnalisée
- Appareils pour lesquels le fabricant n’a pas demandé ou obtenu la certification Google
- Appareils ayant une image système créée directement à partir des fichiers sources Android Open Source Program
- Appareils ayant une image système en préversion bêta/développeur

Pour obtenir des détails techniques, consultez la [documentation de Google concernant l’Attestation SafetyNet](https://developer.android.com/training/safetynet/attestation).

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Paramètres Attestation d’appareil SafetyNet et Appareils jailbreakés/rootés
Les contrôles de l’API SafetyNet Google Play Protect exigent que l’utilisateur final soit en ligne, au moins pendant la durée de l’exécution de l’« aller-retour » visant à déterminer les résultats de l’attestation. Si l’utilisateur final est hors connexion, l’administrateur informatique peut quand même s’attendre à ce qu’un résultat soit appliqué à cause du paramètre **Appareils jailbreakés/rootés**. Ceci étant dit, si l’utilisateur final est hors connexion depuis trop longtemps, la valeur **Période de grâce hors connexion** entre en jeu et tout accès aux données professionnelles ou scolaires est bloqué une fois cette valeur de minuteur atteinte, jusqu’à ce que l’accès réseau soit disponible. L’activation des deux paramètres permet d’adopter une approche multiniveau concernant l’intégrité des appareils des utilisateurs finaux, ce qui est important quand ceux-ci accèdent à des données professionnelles ou scolaires sur mobile.

### <a name="google-play-protect-apis-and-google-play-services"></a>API Google Play Protect et Google Play Services
Les paramètres de stratégie de protection des applications qui tirent parti des API Google Play Protect nécessitent Google Play Services. Les paramètres **Attestation d’appareil SafetyNet** et **Analyse des menaces sur les applications** exigent une version déterminée de Google Play Services pour fonctionner correctement. Dans la mesure où il s’agit de paramètres touchant la sécurité, l’utilisateur final sera bloqué s’il a été ciblé avec ces paramètres et qu’il ne dispose pas de la version appropriée des Services Google Play ou n’a pas accès à Google Play Services.

## <a name="next-steps"></a>Étapes suivantes

[Guide pratique de création et déploiement des stratégies de protection d’application à l’aide de Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Voir aussi
Des applications tierces, comme l’application mobile Salesforce, fonctionnent avec Intune dans le but spécifique de protéger les données de l’entreprise. Pour plus d’informations sur le fonctionnement avec Intune de l’application Salesforce en particulier (notamment les paramètres de configuration de l’application MDM), consultez la section [Application Salesforce et Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf).
