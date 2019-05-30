---
title: Forum Aux Questions sur la Gestion des applications mobiles (MAM) et la protection des applications
description: Cet article fournit des réponses à certaines questions fréquemment posées sur la gestion des applications mobiles (GAM) Intune et la protection des applications Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fb3b02cd9d9b978f1de5e98634d647c4c81cde0
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041654"
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Forum Aux Questions sur la Gestion des applications mobiles (GAM) et la protection des applications

Cet article fournit des réponses à certaines questions fréquemment posées sur la gestion des applications mobiles (MAM) Intune et la protection des applications Intune.

## <a name="mam-basics"></a>Notions de base de la MAM


**Qu’est-ce-que la MAM ?**<br></br>
La [gestion des applications mobiles Intune](/intune/app-lifecycle) se rapporte à la suite de fonctionnalités de gestion Intune qui vous permettent de publier, d’envoyer des notifications Push, de configurer, de sécuriser, de surveiller et de mettre à jour des applications mobiles pour vos utilisateurs.

**Quels sont les avantages de la protection des applications MAM ?**<br></br>
La MAM protège les données d’une organisation au sein d’une application. La gestion MAM sans inscription (MAM-WE) permet de gérer les applications professionnelles et scolaires contenant des données sensibles sur pratiquement tous types d’appareils, y compris les appareils personnels dans les scénarios BYOD (Apportez votre propre appareil). Plusieurs applications de productivité, telles que les applications Microsoft Office, peuvent être gérées par la MAM Intune. Consultez la liste officielle des [applications gérées par Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) accessibles au public.

**Quelles configurations d’appareil la MAM prend-elle en charge ?**<br></br>
La MAM Intune prend en charge deux configurations :
- **Gestion des appareils mobiles et gestion des applications mobiles Intune** : Les administrateurs informatiques peuvent uniquement gérer des applications à l’aide de la MAM et des stratégies de protection des applications sur des appareils inscrits à la gestion des périphériques mobiles (MDM). Pour gérer des applications en utilisant à la fois la gestion MDM et la gestion MAM, les clients doivent utiliser la console Intune sur le portail Azure, à l’adresse https://portal.azure.com.

- **MAM sans inscription d’appareils** : la MAM sans inscription d’appareils (ou MAM-WE en anglais), permet aux administrateurs informatiques de gérer des applications à l’aide de la MAM et de stratégies de protection des applications sur les appareils qui ne sont ne pas inscrits à la MDM Intune. Cela signifie que les applications peuvent être gérées par Intune sur des appareils inscrits avec des fournisseurs EMM tiers. Pour gérer des applications à l’aide de la MAM sans inscription d’appareils, les clients doivent utiliser la console Intune dans le portail Azure à l’adresse https://portal.azure.com. Il est également possible de gérer les applications avec Intune sur les appareils inscrits auprès de fournisseurs tiers de gestion de la mobilité d’entreprise (EMM) ou non inscrits à un quelconque service de gestion MDM.


## <a name="app-protection-policies"></a>Stratégies de protection des applications

**Que sont les stratégies de protection des applications** ?<br></br>
Les stratégies de protection des applications sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application.

**Des exemples de stratégies de protection des applications sont-ils disponibles ?**<br></br>
Consultez les [paramètres de stratégie de protection des applications Android](app-protection-policy-settings-android.md) et les [paramètres de stratégie de protection des applications iOS](app-protection-policy-settings-ios.md) pour plus d’informations sur chaque paramètre de stratégie de protection des applications.

**Est-il possible d’appliquer en même temps des stratégies de gestion des appareils mobiles et de gestion des applications mobiles au même utilisateur, pour différents appareils ? Supposons par exemple qu’un utilisateur puisse accéder à ses ressources de travail sur son propre ordinateur MAM, mais aussi utiliser un appareil géré par Intune MDM au travail. Y a-t-il des limitations à cette idée ?**<br></br>
Si vous appliquez une stratégie de gestion MAM à l’utilisateur sans définir l’état de l’appareil, l’utilisateur reçoit la stratégie à la fois sur l’appareil BYOD et sur l’appareil géré par Intune. Il est également possible d’appliquer une stratégie de gestion MAM en fonction de l’état géré. Si vous créez une stratégie de protection d’applications, sélectionnez Non à côté de Cibler tous les types d’application. Ensuite, choisissez entre les deux solutions suivantes :
- Appliquer une stratégie de gestion MAM moins stricte aux appareils gérés par Intune et une autre plus stricte aux appareils non inscrits à la gestion MDM.
- Appliquer une stratégie de gestion MAM aux appareils non inscrits exclusivement.

Pour plus d’informations, voir [Guide pratique pour surveiller les stratégies de protection d’applications](app-protection-policies-monitor.md).

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Applications que vous pouvez gérer avec des stratégies de protection des applications

**Quelles sont les applications qui peuvent être gérées par des stratégies de protection des applications ?**<br></br>
Toute application intégrée avec le [Kit de développement logiciel (SDK) d’applications Intune](/intune/app-sdk) ou packagée par [l’outil de création de packages d’applications Intune](/intune/apps-prepare-mobile-application-management) peut être gérée à l’aide de stratégies de protection des applications Intune. Consultez la liste officielle des [applications gérées par Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) accessibles au public.

**Quels sont les critères de base pour utiliser des stratégies de protection des applications sur une application gérée par Intune ?**

- L’utilisateur final doit avoir un compte Azure Active Directory (AAD). Consultez la page [Ajouter des utilisateurs et accorder une autorisation d’administration à Intune](/intune/users-permissions-add) pour apprendre à créer des utilisateurs Intune dans Azure Active Directory.

- L’utilisateur final doit disposer d’une licence pour Microsoft Intune, attribuée à son compte Azure Active Directory. Consultez la section [Gérer les licences Intune](/intune/licenses-assign) pour apprendre à attribuer des licences Intune à des utilisateurs finaux.

- L’utilisateur final doit appartenir à un groupe de sécurité ciblé par une stratégie de protection des applications. La même stratégie de protection des applications doit cibler l’application spécifique utilisée. Des stratégies de protection des applications peuvent être créées et déployées dans la console Intune dans le [portail Azure](https://portal.azure.com). Des groupes de sécurité peuvent actuellement être créés dans le [centre d’administration Microsoft 365](https://admin.microsoft.com).

- L’utilisateur final doit se connecter à l’application à l’aide de son compte AAD.

**Quelles sont les exigences supplémentaires pour utiliser [l’application mobile Outlook ](https://products.office.com/outlook)?**

- L’utilisateur final doit avoir installé l’application mobile Outlook sur son appareil.

- L’utilisateur final doit disposer d’une boîte aux lettres [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) et d’une licence associée à son compte Azure Active Directory.

  >[!NOTE]
  > L’application mobile Outlook prend actuellement en charge uniquement Intune App Protection pour Microsoft Exchange Online et [Exchange Server avec authentification moderne hybride](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx) et ne prend pas en charge Exchange dédié à Office 365.

**Quelles sont les exigences supplémentaires pour pouvoir utiliser les applications [Word, Excel et PowerPoint](https://products.office.com/business/office) ?**

- L’utilisateur final doit disposer d’une licence pour [Office 365 Business ou Entreprise](https://products.office.com/business/compare-more-office-365-for-business-plans), associée à son compte Azure Active Directory. L’abonnement doit inclure les applications Office sur des appareils mobiles et peut inclure un compte de stockage cloud avec [OneDrive Entreprise](https://onedrive.live.com/about/business/). Des licences Office 365 peuvent être attribuées dans le [centre d’administration Microsoft 365](https://admin.microsoft.com) en tenant compte des [instructions suivantes](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- L’utilisateur final doit avoir configuré un emplacement géré à l’aide de la fonctionnalité granulaire Enregistrer sous, qui se trouve sous le paramètre de stratégie de protection des applications « Empêcher Enregistrer sous ». Si, par exemple, l’emplacement géré est OneDrive, l’application [OneDrive](https://onedrive.live.com/about/) doit être configurée dans l’application Word, Excel ou PowerPoint de l’utilisateur final.

- Si l’emplacement géré est OneDrive, l’application doit être ciblée par la stratégie de protection des applications déployée pour l’utilisateur final.

  >[!NOTE]
  > Les applications mobiles Office prennent actuellement en charge uniquement SharePoint Online et SharePoint on-premises.

**Pourquoi un emplacement géré (p. ex., OneDrive) est-il nécessaire pour Office ?**<br></br>
Intune marque toutes les données de l’application en tant que données « d’entreprise » ou « personnelles ». Les données sont considérées comme « d’entreprise » lorsqu’elles proviennent d’un emplacement de l’entreprise. Pour les applications Office, Intune considère les sites d’entreprise suivants : e-mail (Exchange) ou stockage cloud (application OneDrive avec un compte OneDrive Entreprise).

**Quelles sont les exigences supplémentaires pour utiliser Skype Entreprise ?**<br></br>
Voir les conditions requises pour les licences de [Skype Entreprise](https://products.office.com/skype-for-business/it-pros). Pour les configurations Skype Entreprise hybrides et locales, consultez l’article annonçant que [l’authentification moderne hybride pour Skype Entreprise et Exchange passe en disponibilité générale](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) et [Authentification moderne pour Skype Entreprise local avec AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910), respectivement.

## <a name="app-protection-features"></a>Fonctionnalités de protection des applications

**Qu’est-ce-que la prise en charge de la multi-identité ?**<br></br>
La prise en charge de la multi-identité est la capacité pour le Kit de développement logiciel (SDK) d’application Intune d’appliquer des stratégies de protection des applications uniquement au compte professionnel ou scolaire connecté à l’application. Si un compte personnel est connecté à l’application, les données restent intactes.

**Quel est l’objectif de la prise en charge de la multi-identité ?**<br></br>
La prise en charge de la multi-identité permet de publier à la fois des applications « d’entreprise » et des applications grand public (p. ex., les applications Office) avec les fonctionnalités de protection des applications Intune pour les comptes « d’entreprise ».

**Qu’en est-il d’Outlook et de la multi-identité ?**<br></br>
Étant donné qu’Outlook a une vue combinée des e-mails personnels et professionnels, l’application Outlook demande le PIN Intune à son lancement.

**Qu’est-ce-que le code PIN d’application Intune ?**<br></br>
Le PIN (numéro d’identification personnel) est un code secret utilisé pour vérifier que l’utilisateur qui accède aux données de l’organisation dans une application y est autorisé.

- **Quand l’utilisateur est-il invité à entrer son code PIN ?**<br></br> Intune n’invite l’utilisateur à saisir le code PIN de l’application que s’il est sur le point d’accéder à des données « d’entreprise ». Dans les applications multi-identité telles que Word/Excel/PowerPoint, l’utilisateur est invité à entrer son code PIN lorsqu’il tente d’ouvrir un fichier ou un document « d’entreprise ». Dans les applications à identité unique, par exemple, les applications métier gérées avec l’outil de création de packages d’applications Intune, le code PIN est demandé au lancement, car le Kit de développement logiciel (SDK) d’applications Intune sait que l’expérience utilisateur dans l’application est toujours de type « entreprise ».

- **À quelle fréquence le code PIN Intune est-il demandé à l’utilisateur ?**<br></br> L’administrateur informatique peut définir le paramètre de stratégie de protection des applications Intune « Revérifier les exigences d’accès après (minutes) » dans la console d’administration Intune. Ce paramètre spécifie le délai avant que les conditions d’accès ne soient vérifiées sur l’appareil et que l’écran du code PIN de l’application ne réapparaisse. Voici cependant des informations importantes sur le code PIN qui affectent la fréquence à laquelle il est demandé à l’utilisateur : 

    - **Le code PIN est partagé entre les applications du même éditeur pour améliorer la facilité d’utilisation :** Sur iOS, un code PIN d’application est partagé entre toutes les applications **du même éditeur d’application**. Sur Android, un même code PIN d’application est partagé entre toutes les applications.
    - **Le comportement « Revérifier les exigences d’accès après (minutes) », après un redémarrage de l’appareil :** Un « minuteur de code PIN » suit le nombre de minutes d’inactivité déterminant quand le code PIN d’application Intune suivant doit être affiché. Sur iOS, le minuteur de code PIN n’est pas affecté par le redémarrage de l’appareil. Ainsi, le redémarrage de l’appareil n’a pas d’effet sur le nombre de minutes d’inactivité de l’utilisateur pour une application iOS avec la stratégie de code PIN Intune. Sur Android, le minuteur de code PIN est réinitialisé au redémarrage de l’appareil. Ainsi, les applications Android avec la stratégie de code PIN Intune vont probablement demander le code PIN d’une application, quelle que soit la valeur du paramètre « Revérifier les exigences d’accès après (minutes) » **après un redémarrage de l’appareil**.  
    - **La nature cyclique du minuteur associé au code PIN :** une fois qu’un code PIN est entré pour accéder à une application (l’application A) et que l’application quitte le premier plan (le focus d’entrée principal) sur l’appareil, le minuteur du code PIN est réinitialisé pour ce code PIN. Une application (l’application B) partageant ce code PIN ne demande pas à l’utilisateur d’entrer ce code parce que la minuterie a été réinitialisée. L’invite réapparaît une fois que la valeur de « Revérifier les exigences d’accès après (minutes) » est à nouveau atteinte.

Pour les appareils iOS, même si le code PIN est partagé entre les applications de différents éditeurs, l’invite s’affiche à nouveau quand la valeur de **Revérifier les spécifications requises pour l’accès après (minutes)** est à nouveau atteinte pour l’application qui n’a pas le focus d’entrée principal. Par exemple, un utilisateur a application _A_ de l’éditeur _X_ et l’application _B_ de l’éditeur _Y_, et ces deux applications partagent le même code PIN. L’utilisateur travaille avec l’application _A_ (au premier plan) et l’application _B_ est réduite. Une fois que la valeur de **Revérifier les spécifications requises pour l’accès après (minutes)** est atteinte et que l’utilisateur passe à l’application _B_, celui-ci doit entrer le code PIN.

  >[!NOTE] 
  > Afin de vérifier plus souvent les exigences d’accès de l’utilisateur (p. ex., en demandant un code PIN), en particulier pour les applications fréquemment utilisées, il est recommandé de réduire la valeur du paramètre « Revérifier les exigences d’accès après (minutes) ». 
      
- **Comment fonctionne le code PIN Intune avec les codes PIN des applications intégrées pour Outlook et OneDrive ?**<br></br>
Le code PIN Intune fonctionne sur la base d’un minuteur d’inactivité (c’est-à-dire la valeur de « Revérifier les exigences d’accès après (minutes) »). Ainsi, la demande de code PIN Intune s’affiche indépendamment des demandes de code PIN de l’application intégrée pour Outlook et OneDrive, qui sont souvent liées par défaut au démarrage de l’application. Si l’utilisateur reçoit en même temps les deux demandes de code PIN, le comportement attendu doit être que le code PIN Intune est prioritaire. 

- **Le code PIN est-il sécurisé ?**<br></br> Le code PIN sert à autoriser uniquement les utilisateurs adéquats à accéder aux données de leur organisation dans l’application. Par conséquent, un utilisateur final doit se connecter avec son compte professionnel ou scolaire pour pouvoir définir ou réinitialiser son code PIN d’application Intune. Cette authentification est gérée par Active Directory Azure par le biais d’un échange de jeton sécurisé et n’est pas transparente pour le Kit de développement logiciel (SDK) d’application Intune. Du point de vue de la sécurité, la meilleure manière de protéger les données professionnelles ou scolaires consiste à les chiffrer. Le chiffrement n’est pas lié au code PIN de l’application, mais constitue sa propre stratégie de protection des applications.

- **Comment Intune protège-t-il le code PIN contre les attaques en force brute ?**<br></br> Dans le cadre de la stratégie de code PIN d’application, l’administrateur peut définir un nombre maximal de tentatives d’authentification de son code PIN avant le verrouillage de l’application. Une fois que le nombre de tentatives atteint, le Kit de développement logiciel (SDK) d’application Intune peut réinitialiser les données « d’entreprise » dans l’application.
  
- **Pourquoi dois-je définir un code PIN à deux reprises dans des applications provenant du même éditeur ?**<br></br> La gestion MAM (sous iOS) autorise actuellement les codes PIN d’applications composés de caractères alphanumériques et spéciaux (nommés « codes secrets ») qui impliquent la participation d’applications (p. ex., WXP, Outlook, Managed Browser ou Yammer) pour intégrer le Kit SDK d’applications Intune pour iOS. Sans cela, les paramètres de code secret ne sont pas appliqués correctement pour les applications ciblées. Il s’agissait d’une fonctionnalité publiée dans le SDK Intune pour iOS version 7.1.12. <br><br> Pour prendre en charge cette fonctionnalité et garantir la compatibilité descendante avec les versions antérieures du Kit SDK Intune pour iOS, tous les codes PIN (numériques ou codes secrets) à partir de la version 7.1.12 sont gérés séparément du code PIN numérique des versions précédentes du Kit SDK. Par conséquent, si un appareil contient des applications avec le Kit SDK Intune pour des versions iOS antérieures à 7.1.12 et ultérieures à 7.1.12 du même éditeur, deux codes PIN doivent être définis. <br><br> Cela étant dit, les deux codes PIN (pour chaque application) ne sont liés d’aucune manière et doivent respecter la stratégie de protection appliquée à l’application. Par conséquent, *uniquement* si les applications A et B ont les mêmes stratégies de code PIN, l’utilisateur peut définir deux fois le même code PIN. <br><br> Ce comportement est propre au code PIN sur les applications iOS activées avec la gestion des applications mobiles Intune. Au fil du temps, à mesure que les applications adoptent les versions ultérieures du Kit SDK Intune pour iOS, définir deux fois un code PIN sur les applications d’un même éditeur pose moins de problèmes. Consultez la remarque ci-dessous pour obtenir un exemple.

  >[!NOTE]
  > Par exemple, si l’application A est générée avec une version antérieure à 7.1.12 et que l’application B est générée avec une version supérieure ou égale à 7.1.12 du même éditeur, l’utilisateur final devra définir séparément les codes PIN pour A et B si ces deux apps sont installées sur un appareil iOS. <br><br> Si une application C avec le Kit SDK version 7.1.9 est installée sur l’appareil, elle utilisera le même code PIN que l’application A. <br><br> Une application D avec une version 7.1.14 partagera le même code PIN que l’application B. <br><br> Si seules les applications A et C sont installées sur un appareil, vous devez définir un seul code PIN. Il en va de même si seules les applications B et D sont installées sur un appareil.

**Qu’en est-il du chiffrement ?**<br></br>
Les administrateurs informatiques peuvent déployer une stratégie de protection des applications nécessitant un chiffrement des données d’application. Dans le cadre de la stratégie, l’administrateur informatique peut également spécifier quand le contenu est chiffré.

- **Comment Intune chiffre-t-il des données ?**<br></br> Consultez les [paramètres de stratégie de protection des applications Android](app-protection-policy-settings-android.md) et les [paramètres de stratégie de protection des applications iOS](app-protection-policy-settings-ios.md) pour plus d’informations sur le paramètre de chiffrement de stratégie de protection des applications.

- **Quelles sont les données chiffrées ?**<br></br> Seules les données marquées comme « d’entreprise » sont chiffrées en fonction de la stratégie de protection des applications de l’administrateur. Les données sont considérées comme « d’entreprise » lorsqu’elles proviennent d’un emplacement de l’entreprise. Pour les applications Office, Intune considère les sites d’entreprise suivants : e-mail (Exchange) ou stockage cloud (application OneDrive avec un compte OneDrive Entreprise). Dans le cas des applications métier gérées par l’outil de création de packages d’applications Intune, toutes les données sont considérées comme étant de type « entreprise ».

**Comment Intune réinitialise-t-il des données à distance ?**<br></br>
Intune peut effacer des données d’application de trois manières différentes : réinitialisation complète de l’appareil, réinitialisation sélective pour la gestion des appareils mobiles et réinitialisation sélective pour la gestion des applications mobiles. Pour plus d’informations sur la réinitialisation à distance pour la gestion MDM, consultez [Supprimer des appareils avec la réinitialisation ou la mise hors service](devices-wipe.md). Pour plus d’informations sur la réinitialisation sélective avec la gestion des applications mobiles, consultez [Action Mettre hors service](devices-wipe.md#retire) et [Guide pratique pour effacer uniquement les données d’entreprise dans les applications](apps-selective-wipe.md).

- **Présentation de la réinitialisation**<br></br> La [réinitialisation ](devices-wipe.md) supprime toutes les données et tous les paramètres utilisateur de **l’appareil** en rétablissant les paramètres d’usine par défaut de l’appareil. L’appareil est supprimé d’Intune.
  >[!NOTE]
  > La réinitialisation est possible seulement sur les appareils inscrits auprès de la gestion MDM d’Intune.

- **Qu’est-ce que la réinitialisation sélective pour la gestion des appareils mobiles ?**<br></br> Pour plus d’informations sur la suppression des données d’entreprise, consultez [Supprimer des appareils - Mettre hors service](devices-wipe.md#retire).

- **Qu’est-ce que la réinitialisation sélective pour la gestion des applications mobiles ?**<br></br> La réinitialisation sélective pour la gestion des applications mobiles supprime simplement les données d’applications d’entreprise à partir d’une application. La requête est lancée à l’aide du portail Intune Azure. Pour savoir comment effectuer une demande de réinitialisation, consultez la section [Guide pratique pour effacer uniquement les données d’entreprise des applications](apps-selective-wipe.md).

- **Quelle est la vitesse de la réinitialisation sélective pour la gestion des applications mobiles ?**<br></br> Si l’utilisateur utilise l’application lorsque la réinitialisation sélective est lancée, le Kit de développement logiciel (SDK) d’application Intune contrôle toutes les 30 minutes la présence d’une requête de réinitialisation sélective du service de GAM Intune. Il vérifie également la présence d’une réinitialisation sélective lorsque l’utilisateur lance l’application pour la première fois et se connecte avec son compte professionnel ou scolaire.

**Pourquoi les services locaux (on-prem) ne fonctionnent-ils pas avec des applications protégées par Intune ?**<br></br>
La protection d’applications Intune dépend de la cohérence de l’identité de l’utilisateur entre l’application et le Kit de développement logiciel (SDK) d’application Intune. L’authentification moderne est la seule manière de la garantir. Il existe des scénarios dans lesquels les applications peuvent fonctionner avec une configuration locale. Mais elles ne sont ni cohérentes, ni garanties.

**Existe-t-il un moyen sécurisé d’ouvrir des liens web depuis des applications gérées ?**<br></br>
Oui ! L’administrateur informatique peut déployer et définir la stratégie de protection des applications pour [l’application Intune Managed Browser](app-configuration-managed-browser.md), un navigateur web développé par Microsoft Intune qui peut être géré facilement avec Intune. L’administrateur informatique peut exiger que tous les liens web dans les applications gérées par Intune soient ouverts à l’aide de l’application Managed Browser.

**Le SDK d’application Intune prend-t-il en charge la bibliothèque d’authentification Microsoft (MSAL) ou des comptes de réseaux sociaux ?**
Le SDK d’application Intune utilise certaines fonctionnalités avancées de la bibliothèque ADAL pour les versions internes et de tiers du SDK. En l’état, MSAL ne fonctionne pas correctement dans la plupart de nos scénarios de base, comme l’authentification dans le service Intune App Protection et le lancement conditionnel. Il n’est pas prévu à ce jour de la prendre en charge.

## <a name="app-experience-on-android"></a>Expérience d'application sur Android

**Pourquoi l’application Portail d’entreprise est-elle nécessaire pour que la protection des applications Intune fonctionne sur des appareils Android ?**<br></br>
La plupart des fonctionnalités de protection des applications sont intégrées à l’application Portail d’entreprise. L’inscription d’appareil n’est _pas obligatoire_, même si l’application Portail d’entreprise est toujours nécessaire. Dans le cas de la gestion MAM-WE, l’utilisateur final doit simplement avoir installé l’application Portail d’entreprise sur l’appareil.

**Comment plusieurs paramètres d’accès de protection des applications Intune qui sont configurés pour le même ensemble d’applications et d’utilisateurs fonctionnent-ils sur Android ?**<br></br>
Les stratégies de protection des applications Intune pour l’accès sont appliquées dans un ordre spécifique sur les appareils des utilisateurs finaux quand ceux-ci tentent d’accéder à une application cible à partir de leur compte d’entreprise. En règle générale, un blocage est prioritaire, puis un message d’avertissement. Par exemple, si cela s’applique à l’utilisateur/application en question, un paramètre de version de correctif Android minimale qui signale à un utilisateur qu’il doit effectuer une mise à niveau de correctif sera appliqué après le paramètre de version de correctif Android minimale qui bloque l’accès à l’utilisateur. Ainsi, dans le scénario où l’administrateur informatique configure la version de correctif Android minimale sur 2018-03-01 et la version de correctif Android minimale (Avertissement uniquement) sur 2018-02-01, alors que l’appareil qui tente d’accéder à l’application utilise une version de correctif 2018-01-01, l’utilisateur final est bloqué sur la base du paramètre le plus restrictif pour la version de correctif Android minimale qui provoque un blocage de l’accès. 

Lors du traitement de différents types de paramètres, une exigence de version d’application est prioritaire, suivie de l’exigence de version de système d’exploitation Android, puis de l’exigence de version de correctif Android. Ensuite, tous les avertissements pour tous les types de paramètres dans le même ordre sont vérifiés.

**Les stratégies Intune App Protection permettent aux administrateurs d’exiger que les appareils des utilisateurs finaux obtiennent l’Attestation SafetyNet de Google pour les appareils Android. Quelle est la fréquence d’envoi des nouveaux résultats d’Attestation SafetyNet au service ?** <br><br> Une nouvelle détermination de service Google Play est signalée à l’administrateur informatique à un intervalle déterminé par le service Intune. La fréquence à laquelle l’appel de service est effectué est limitée en raison de la charge. Ainsi, cette valeur est tenue à jour en interne et n’est pas configurable. Toute action configurée par l’administrateur informatique pour le paramètre d’Attestation SafetyNet de Google sera effectuée en fonction du dernier résultat signalé au service Intune au moment du lancement conditionnel. En l’absence de données, l’accès sera autorisé à condition qu’aucun autre contrôle de lancement conditionnel n’échoue, et un « aller-retour » de Google Play Services pour déterminer les résultats d’attestation commencera dans le back-end et invitera l’utilisateur de façon asynchrone si l’attestation de l’appareil a échoué. S’il existe des données périmées, l’accès sera bloqué ou autorisé en fonction du dernier résultat signalé, et un « aller-retour » de Google Play Services pour déterminer les résultats d’attestation commencera également et invitera l’utilisateur de façon asynchrone si l’attestation de l’appareil a échoué.

**Les stratégies Intune App Protection permettent aux administrateurs d’exiger que les appareils des utilisateurs finaux envoient des signaux par le biais de l’API de vérification des applications de Google pour les appareils Android. Comment un utilisateur final peut-il activer l’analyse de l’application afin de ne pas se voir refuser l’accès pour cette raison ?**<br><br> La procédure à suivre varie légèrement en fonction de l’appareil. Le processus général implique d’accéder au Google Play Store, de cliquer sur **Mes jeux et applications**, puis de cliquer sur le résultat de la dernière analyse de l’application afin d’accéder au menu Play Protect. Vérifiez que l’option **Rechercher les menaces de sécurité sur l’appareil** est activée.

**Que vérifie exactement l’API d’Attestation SafetyNet de Google sur les appareils Android ? Quelle est la différence entre les valeurs configurables de « Vérifier l’intégrité de base » et « Vérifier l’intégrité de base et les appareils certifiés » ?** <br><br>
Intune tire parti des API SafetyNet Google Play Protect à ajouter à nos contrôles de détection du rootage pour les appareils non inscrits. Google développe et gère cet ensemble d’API pour les applications Android, à adopter s’il ne souhaite pas que ses applications s’exécutent sur des appareils rootés. L’application Android Pay a par exemple incorporé cette fonctionnalité. Bien que Google ne partage pas publiquement l’intégralité des contrôles de détection du rootage effectués, nous estimons que ces API sont capables de détecter les appareils qui ont été rootés par l’utilisateur. L’accès de ces utilisateurs peut alors être bloqué, ou leurs comptes professionnels supprimés des applications pour lesquelles une stratégie est activée. « Vérifier l’intégrité de base » vous informe quant à l’intégrité générale de l’appareil. Les appareils rootés, les émulateurs, les appareils virtuels et les appareils présentant des signes d’altération échouent aux tests d’intégrité de base. « Vérifier l’intégrité de base et les appareils certifiés » vous informe quant à la compatibilité de l’appareil avec les services de Google. Seuls les appareils non modifiés qui ont été certifiés par Google peuvent satisfaire à ce contrôle. Les appareils suivants échoueront :
* Appareils qui échouent aux tests d’intégrité de base
* Appareils ayant un chargeur de démarrage déverrouillé
* Appareils ayant une image système/ROM personnalisée
* Appareils pour lesquels le fabricant n’a pas demandé ou obtenu la certification Google 
* Appareils ayant une image système créée directement à partir des fichiers sources Android Open Source Program
* Appareils ayant une image système en préversion bêta/développeur

Pour obtenir des détails techniques, consultez la [documentation de Google concernant l’Attestation SafetyNet](https://developer.android.com/training/safetynet/attestation).

**Il existe deux contrôles similaires dans la section Lancement conditionnel lors de la création d’une stratégie Intune App Protection pour les appareils Android. Dois-je exiger le paramètre « Attestation d’appareil SafetyNet » ou « Appareils jailbreakés/rootés » ?** <br><br>
Les contrôles de l’API SafetyNet Google Play Protect exigent que l’utilisateur final soit en ligne, au moins pendant la durée de l’exécution de l’« aller-retour » visant à déterminer les résultats de l’attestation. Si l’utilisateur final est hors connexion, l’administrateur informatique peut quand même s’attendre à ce qu’un résultat soit appliqué à cause du paramètre « Appareils jailbreakés/rootés ». Ceci étant dit, si l’utilisateur final est hors connexion depuis trop longtemps, la valeur « Période de grâce hors connexion » entre en jeu et tout accès aux données professionnelles ou scolaires est bloqué une fois cette valeur de minuteur atteinte, jusqu’à ce que l’accès réseau soit disponible. L’activation des deux paramètres permet d’adopter une approche multiniveau concernant l’intégrité des appareils des utilisateurs finaux, ce qui est important quand ceux-ci accèdent à des données professionnelles ou scolaires sur mobile. 

**Les paramètres de stratégie de protection des applications qui tirent parti des API Google Play Protect nécessitent Google Play Services. Que se passe-t-il si Google Play Services n’est pas autorisé là où l’utilisateur final se trouve ?**<br><br>
Les paramètres « Attestation d’appareil SafetyNet » et « Analyse des menaces sur les applications » exigent une version déterminée de Google Play Services pour fonctionner correctement. Dans la mesure où il s’agit de paramètres touchant la sécurité, l’utilisateur final sera bloqué s’il a été ciblé avec ces paramètres et qu’il ne dispose pas de la version appropriée des Services Google Play ou n’a pas accès à Google Play Services. 

## <a name="app-experience-on-ios"></a>Expérience d'application sur iOS
**Que se passe-t-il si j’ajoute ou supprime une empreinte digitale ou un visage sur mon appareil ?**
Les stratégies Intune de protection des applications permettent de restreindre l’accès aux utilisateurs qui disposent d’une licence Intune. L’un des moyens de contrôler l’accès à une application est d’exiger un Touch ID ou un Face ID Apple sur les appareils pris en charge. Le comportement suivant est implémenté: si un changement est apporté à la base de données biométrique de l’appareil, Intune invite l’utilisateur à entrer un code PIN la prochaine fois que le délai d’attente d’inactivité est atteint. Les changements apportés aux données biométriques incluent l’ajout et la suppression d’une empreinte digitale ou d’un visage. Si l’utilisateur Intune n’a pas défini de code PIN, il est dirigé vers la page de configuration d’un code PIN Intune.
 
L’objectif est de sécuriser les données de votre organisation au sein de l’application. Cette fonctionnalité est uniquement disponible pour iOS et nécessite la participation d’applications qui intègrent le SDK d’application Intune pour iOS 9.0.1 ou version ultérieure. L’intégration du SDK est nécessaire afin que le comportement puisse être ajouté aux applications ciblées. Cette intégration se produit en continu et repose sur les équipes d’application spécifiques. Certaines applications participantes incluent WXP, Outlook, Managed Browser et Yammer. 
  
**Je suis en mesure d’utiliser l’extension de partage iOS pour ouvrir des données professionnelles ou scolaires dans des applications non gérées, même si la stratégie de transfert de données est définie sur les « applications gérées uniquement » ou sur « Aucune application ». Cela ne provoque-t-il pas de fuite de données ?**<br></br>
La stratégie de protection des applications Intune ne peut pas contrôler l’extension de partage iOS sans gérer l’appareil. Par conséquent, Intune _**chiffre les données « d’entreprise » avant de les partager à l’extérieur de l’application**_. Vous pouvez valider cette action en essayant d’ouvrir le fichier « d’entreprise » en dehors de l’application gérée. Le fichier doit être chiffré et ne peut pas être ouvert en dehors de l’application gérée.

**Comment plusieurs paramètres d’accès de protection des applications Intune qui sont configurés pour le même ensemble d’applications et d’utilisateurs fonctionnent-ils sur iOS ?**<br></br>
Les stratégies de protection des applications Intune pour l’accès sont appliquées dans un ordre spécifique sur les appareils des utilisateurs finaux quand ceux-ci tentent d’accéder à une application cible à partir de leur compte d’entreprise. En règle générale, une réinitialisation est prioritaire, suivie d’un blocage, puis d’un message d’avertissement. Par exemple, si cela s’applique à l’utilisateur/application en question, un paramètre de système d’exploitation iOS minimal qui signale à un utilisateur qu’il doit mettre à niveau sa version d’iOS est appliqué après le paramètre de système d’exploitation iOS minimal qui bloque l’accès à l’utilisateur. Ainsi, dans le scénario où l’administrateur informatique configure le système d’exploitation iOS minimal sur 11.0.0.0 et le système d’exploitation iOS minimal (Avertissement uniquement) sur 11.1.0.0, alors que l’appareil qui tente d’accéder à l’application utilise iOS 10, l’utilisateur final est bloqué sur la base du paramètre le plus restrictif pour la version de système d’exploitation iOS minimal qui provoque un blocage de l’accès.

Lors du traitement de différents types de paramètres, une exigence de version de SDK d’application Intune est prioritaire, suivie d’une exigence de version d’application, puis d’une exigence de version de système d’exploitation iOS. Ensuite, tous les avertissements pour tous les types de paramètres dans le même ordre sont vérifiés. Nous vous recommandons de configurer l’exigence de version de SDK d’application Intune uniquement sur recommandation de l’équipe de produit Intune pour les principaux scénarios de blocage.


## <a name="see-also"></a>Voir aussi
- [Implémenter un plan Intune](planning-guide-onboarding.md)
- [Tests et validation Intune](planning-guide-test-validation.md)
- [Paramètres de stratégie de gestion des applications mobiles Android dans Microsoft Intune](app-protection-policy-settings-android.md)
- [Paramètres de stratégie de gestion des applications mobiles iOS](app-protection-policy-settings-ios.md)
- [Stratégies de protection des applications - Actualisation des stratégies](app-protection-policy-delivery.md)
- [Valider les stratégies de protection des applications](app-protection-policy-delivery.md)
- [Ajouter des stratégies de configuration pour les applications gérées sans inscription des appareils](app-configuration-policies-managed-app.md)
- [Comment obtenir un support technique pour Microsoft Intune](get-support.md)
