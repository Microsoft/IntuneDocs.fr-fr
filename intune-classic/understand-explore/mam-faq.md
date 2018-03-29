---
title: Forum Aux Questions sur la Gestion des applications mobiles (MAM) et la protection des applications
description: Cet article fournit des réponses à certaines questions fréquemment posées sur la gestion des applications mobiles (MAM) Intune et la protection des applications Intune.
keywords: ''
author: oydang
ms.author: oydang
manager: dougeby
ms.date: 01/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7654e5235fc30f46f67d35544a92c4bd25ac5c86
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>Forum Aux Questions sur la Gestion des applications mobiles (MAM) et la protection des applications

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Cet article fournit des réponses à certaines questions fréquemment posées sur la gestion des applications mobiles (MAM) Intune et la protection des applications Intune.

## <a name="mam-basics"></a>Notions de base de la MAM


**Qu’est-ce-que la MAM ?** La [gestion des applications mobiles Intune](/intune/app-lifecycle) se rapporte à la suite de fonctionnalités de gestion Intune qui vous permettent de publier, d’envoyer des notifications Push, de configurer, de sécuriser, de surveiller et de mettre à jour des applications mobiles pour vos utilisateurs.

**Quels sont les avantages de la protection des applications MAM ?** La MAM protège les données d’une organisation au sein d’une application. Avec la gestion des applications mobiles MAM sans inscription, une application professionnelle ou scolaire qui contient des données sensibles peuvent être gérées sur pratiquement n’importe quel appareil, notamment les appareils personnels dans les scénarios BYOD (apportez votre propre appareil). Plusieurs applications de productivité, telles que les applications Microsoft Office, peuvent être gérées par la MAM Intune. Consultez la liste officielle des [applications gérées par Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) accessibles au public.

**Quelles configurations d’appareil la MAM prend-elle en charge ?** La MAM Intune prend en charge deux configurations :
  1. **MDM + MAM Intune** : c’est la première configuration prise en charge par la MAM à son premier lancement. Les administrateurs informatiques peuvent uniquement gérer des applications à l’aide de la MAM et des stratégies de protection des applications sur des appareils inscrits à la gestion des périphériques mobiles (MDM). Pour gérer des applications à l’aide MDM + MAM, les clients doivent utiliser la console Intune autonome à l’adresse https://manage.microsoft.com.

  2. **MAM sans inscription d’appareils** : la MAM sans inscription d’appareils (ou MAM-WE en anglais), permet aux administrateurs informatiques de gérer des applications à l’aide de la MAM et de stratégies de protection des applications sur les appareils qui ne sont ne pas inscrits à la MDM Intune. Cela signifie que les applications peuvent être gérées par Intune sur des appareils inscrits avec des fournisseurs EMM tiers. Pour gérer des applications à l’aide de la MAM sans inscription d’appareils, les clients doivent utiliser la console Intune dans le portail Azure à l’adresse http://portal.azure.com.


## <a name="app-protection-policies"></a>Stratégies de protection des applications

**Que sont les stratégies de protection des applications** ? Les stratégies de protection des applications sont des règles qui garantissent que les données d’une organisation sont sécurisées ou restent dans une application managée. Une stratégie peut être une règle qui est appliquée lorsque l’utilisateur tente d’accéder à des données « d’entreprise » ou de les déplacer, ou s’il tente un ensemble d’actions interdites ou surveillées lorsqu’il se trouve dans l’application.

**Des exemples de stratégies de protection des applications sont-ils disponibles ?** Consultez les [paramètres de stratégie de protection des applications Android](../deploy-use/android-mam-policy-settings.md) et les [paramètres de stratégie de protection des applications iOS](../deploy-use/ios-mam-policy-settings.md) pour plus d’informations sur chaque paramètre de stratégie de protection des applications.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>Applications que vous pouvez gérer avec des stratégies de protection des applications

**Quelles sont les applications qui peuvent être gérées par des stratégies de protection des applications ?** Toute application compatible avec le [Kit de développement logiciel (SDK) d’application Intune](/intune/app-sdk) ou encapsulée par [l’outil de création de package de restrictions d’application Intune](/intune/apps-prepare-mobile-application-management) peut être gérée à l’aide de stratégies de protection des applications Intune. Consultez la liste officielle des [applications gérées par Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) accessibles au public.

**Quels sont les critères de base pour utiliser des stratégies de protection des applications sur une application gérée par Intune ?**
  1. L’utilisateur final doit avoir un compte Azure Active Directory (AAD). Consultez la page [Ajouter des utilisateurs et accorder une autorisation d’administration à Intune](/intune/users-permissions-add) pour apprendre à créer des utilisateurs Intune dans Azure Active Directory.

  2. L’utilisateur final doit disposer d’une licence pour Microsoft Intune attribuée à son compte Azure Active Directory. Consultez la page [Gérer les licences Intune](/intune/licenses-assign) pour apprendre à attribuer des licences Intune à des utilisateurs finaux.

  3. L’utilisateur final doit appartenir à un groupe de sécurité qui est ciblé par une stratégie de protection des applications. La même stratégie de protection des applications doit cibler l’application spécifique utilisée. Des stratégies de protection des applications peuvent être créées et déployées dans la console Intune dans le [portail Azure](http://portal.azure.com). Des groupes de sécurité peuvent actuellement être créés dans le [portail Office](http://portal.office.com).

  4. L’utilisateur final doit se connecter à l’application à l’aide de son compte AAD.

**Quelles sont les exigences supplémentaires pour utiliser [l’application mobile Outlook ](https://www.microsoft.com/outlook-com/mobile/)?**

  1. L’utilisateur final doit avoir installé l’application mobile Outlook sur son appareil.

  2. L’utilisateur final doit disposer d’une boîte aux lettres [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) et d’une licence associée à son compte Azure Active Directory.

  >[!NOTE]
  > L’application mobile Outlook prend actuellement en charge uniquement Microsoft Exchange Online et ne prend pas en charge Exchange sur site ou Exchange dédié à Office 365.

**Quelles sont les exigences supplémentaires pour utiliser les applications [Word, Excel et PowerPoint](https://products.office.com/business/office) ?**

  1. L’utilisateur final doit disposer d’une licence pour [Office 365 Business ou Entreprise](https://products.office.com/business/compare-more-office-365-for-business-plans) associée à son compte Azure Active Directory. L’abonnement doit inclure les applications Office sur des appareils mobiles et peut inclure un compte de stockage cloud avec [OneDrive Entreprise](https://onedrive.live.com/about/business/). Des licences Office 365 peuvent être attribuées dans le [portail Office](http://portal.office.com) en tenant compte des [instructions suivantes](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

  2. L’utilisateur final doit avoir configuré un emplacement managé à l’aide de la fonctionnalité d’enregistrement granulaire sous le paramètre de stratégie de protection des applications « Empêcher Enregistrer sous ». Par exemple, si l’emplacement managé est OneDrive, l’application [OneDrive](https://onedrive.live.com/about/) doit être configurée dans les applications Word, Excel ou PowerPoint de l’utilisateur final.

  3. Si l’emplacement managé est OneDrive, l’application doit être ciblée par la stratégie de protection des applications déployée pour l’utilisateur final.

  >[!NOTE]
  > Les applications mobiles Office prennent actuellement en charge uniquement SharePoint Online et SharePoint on-premises.

**Pourquoi un emplacement managé (ex. OneDrive) est-il nécessaire pour Office ?** Intune marque toutes les données de l’application en tant que données « d’entreprise » ou « personnelles ». Les données sont considérées comme « d’entreprise » lorsqu’elles proviennent d’un emplacement de l’entreprise. Pour les applications Office, Intune considère les sites d’entreprise suivants : e-mail (Exchange) ou stockage cloud (application OneDrive avec un compte OneDrive Entreprise).

**Quelles sont les exigences supplémentaires pour utiliser Skype Entreprise ?** Voir les conditions requises pour les licences de [Skype Entreprise](https://products.office.com/skype-for-business/it-pros).
  >[!NOTE]
  > L’application mobile Skype Entreprise prend actuellement uniquement en charge Skype Entreprise Online.

## <a name="app-protection-features"></a>Fonctionnalités de protection des applications

**Qu’est-ce-que la prise en charge de la multi-identité ?** La prise en charge de la multi-identité est la capacité pour le Kit de développement logiciel (SDK) d’application Intune d’appliquer des stratégies de protection des applications uniquement au compte professionnel ou scolaire connecté à l’application. Si un compte personnel est connecté à l’application, les données restent intactes.

**Quel est l’objectif de la prise en charge de la multi-identité ?** La prise en charge de la multi-identité permet aux applications dédiées aux entreprises et au grand public (par exemple, les applications Office) d’être publiées publiquement avec des fonctionnalités de protection des applications Intune pour les comptes « d’entreprise ».

**Qu’en est-il d’Outlook et de la multi-identité ?** Étant donné qu’Outlook a une vue combinée des e-mails personnels et professionnels, l’application Outlook demande le PIN Intune à son lancement.

**Qu’est-ce-que le code PIN d’application Intune ?** Le PIN (numéro d’identification personnel) est un code secret utilisé pour vérifier que l’utilisateur qui accède aux données de l’organisation dans une application y est autorisé.

  1. **Quand l’utilisateur est-il invité à entrer son code PIN ?** Intune ne demande le PIN de l’utilisateur pour l’application que lorsque ce dernier est sur le point d’accès aux données « d’entreprise ». Dans les applications multi-identité telles que Word/Excel/PowerPoint, l’utilisateur est invité à entrer son code PIN lorsqu’il tente d’ouvrir un fichier ou un document « d’entreprise ». Dans les applications à identité unique, telles que les applications métier compatibles grâce à l’outil de création de package de restrictions d’application Intune, le code PIN est demandé au lancement, car le Kit de développement logiciel (SDK) d’application Intune sait que l’expérience utilisateur dans l’application est toujours « d’entreprise ».

2. **À quelle fréquence le code PIN Intune est-il demandé à l’utilisateur ?**
L’administrateur informatique peut définir le paramètre de stratégie de protection des applications Intune « Revérifier les exigences d’accès après (minutes) » dans la console d’administration Intune. Ce paramètre spécifie le délai avant que les conditions d’accès ne soient vérifiées sur l’appareil et que l’écran du code PIN de l’application ne réapparaisse. Voici cependant des informations importantes sur le code PIN qui affectent la fréquence à laquelle il est demandé à l’utilisateur : 

* **Le code PIN est partagé entre les applications du même éditeur pour améliorer la facilité d’utilisation :** sur iOS, un même code PIN d’application est partagé entre toutes les applications **du même éditeur**. Sur Android, un même code PIN d’application est partagé entre toutes les applications.
* **La nature cyclique du minuteur associé au code PIN :** une fois qu’un code PIN est entré pour accéder à une application (l’application A) et que l’application quitte le premier plan (le focus d’entrée principal) sur l’appareil, le minuteur du code PIN est réinitialisé pour ce code PIN. Une application (l’application B) partageant ce code PIN ne demande pas à l’utilisateur d’entrer ce code parce que la minuterie a été réinitialisée. L’invite réapparaît une fois que la valeur de « Revérifier les exigences d’accès après (minutes) » est à nouveau atteinte. 

>[!NOTE] 
> Pour vérifier plus souvent les conditions d’accès de l’utilisateur (en demandant un code PIN), en particulier pour une application fréquemment utilisée, il est recommandé de réduire la valeur du paramètre « Revérifier les exigences d’accès après (minutes) ». 

  3. **Le code PIN est-il sécurisé ?** Le code PIN sert à autoriser uniquement les utilisateurs adéquats à accéder aux données de leur organisation dans l’application. Par conséquent, un utilisateur final doit se connecter avec son compte professionnel ou scolaire avant de pouvoir définir ou réinitialiser son PIN d’application Intune. Cette authentification est gérée par Active Directory Azure par le biais d’un échange de jeton sécurisé et n’est pas transparente pour le Kit de développement logiciel (SDK) d’application Intune. Du point de vue de la sécurité, la meilleure manière de protéger les données professionnelles ou scolaires consiste à les chiffrer. Le chiffrement n’est pas lié au code PIN de l’application, mais constitue sa propre stratégie de protection des applications.

  4. **Comment Intune protège-t-il le code PIN contre les attaques en force brute ?** Dans le cadre de la stratégie de code PIN d’application, l’administrateur peut définir un nombre maximal de tentatives d’authentification de son code PIN avant le verrouillage de l’application. Une fois que le nombre de tentatives atteint, le Kit de développement logiciel (SDK) d’application Intune peut réinitialiser les données « d’entreprise » dans l’application.
  
  5. **Pourquoi dois-je définir un code PIN à deux reprises dans des applications provenant du même éditeur ?**
MAM (sur iOS) prend actuellement en charge les codes PIN au niveau de l’application avec des caractères alphanumériques et spéciaux (appelés « code secret ») qui nécessitent l’implication d’applications (ex. WXP, Outlook, Managed Browser, Yammer) pour intégrer le kit SDK d’application Intune pour iOS. Sans cela, les paramètres de code secret ne sont pas appliqués correctement pour les applications ciblées. Il s’agissait d’une fonctionnalité publiée dans le SDK Intune pour iOS version 7.1.12. <br> Pour prendre en charge cette fonctionnalité et garantir la compatibilité descendante avec les versions antérieures du Kit SDK Intune pour iOS, tous les codes PIN (numériques ou codes secrets) à partir de la version 7.1.12 sont gérés séparément du code PIN numérique des versions précédentes du Kit SDK. Par conséquent, si un appareil contient des applications avec le Kit SDK Intune pour des versions iOS antérieures à 7.1.12 et ultérieures à 7.1.12 du même éditeur, deux codes PIN doivent être définis. <br><br> Cela étant dit, les deux codes PIN (pour chaque application) ne sont liés d’aucune manière et doivent respecter la stratégie de protection appliquée à l’application. Par conséquent, *uniquement* si les applications A et B ont les mêmes stratégies de code PIN, l’utilisateur peut définir deux fois le même code PIN. <br><br> Ce comportement est spécifique au code PIN sur les applications iOS activées avec la gestion des applications mobiles Intune. Au fil du temps, à mesure que les applications adoptent les versions ultérieures du Kit SDK Intune pour iOS, définir deux fois un code PIN sur les applications d’un même éditeur pose moins de problèmes. Consultez la remarque ci-dessous pour obtenir un exemple.

>[!NOTE]
> Par exemple, si l’application A est générée avec une version antérieure à 7.1.12 et que l’application B est générée avec une version supérieure ou égale à 7.1.12 du même éditeur, l’utilisateur final devra définir séparément les codes PIN pour A et B si ces deux apps sont installées sur un appareil iOS. <br> Si une application C avec le Kit SDK version 7.1.9 est installée sur l’appareil, elle utilisera le même code PIN que l’application A. <br> Une application D avec une version 7.1.14 partagera le même code PIN que l’application B. <br> Si seules les applications A et C sont installées sur un appareil, vous devez définir un seul code PIN. Il en va de même si seules les applications B et D sont installées sur un appareil.

**Qu’en est-il du chiffrement ?** Les administrateurs informatiques peuvent déployer une stratégie de protection des applications nécessitant un chiffrement des données d’application. Dans le cadre de la stratégie, l’administrateur informatique peut également spécifier quand le contenu est chiffré.

  1. **Comment Intune chiffre-t-il des données ?** Consultez les [paramètres de stratégie de protection des applications Android](../deploy-use/android-mam-policy-settings.md) et les [paramètres de stratégie de protection des applications iOS](../deploy-use/ios-mam-policy-settings.md) pour plus d’informations sur le paramètre de chiffrement de stratégie de protection des applications.

  2. **Quelles sont les données chiffrées ?** Seules les données marquées comme « d’entreprise » sont chiffrées en fonction de la stratégie de protection des applications de l’administrateur. Les données sont considérées comme « d’entreprise » lorsqu’elles proviennent d’un emplacement de l’entreprise. Pour les applications Office, Intune considère les sites d’entreprise suivants : e-mail (Exchange) ou stockage cloud (application OneDrive avec un compte OneDrive Entreprise). Pour les applications métier rendues compatibles par l’outil de création de package de restrictions d’application Intune, toutes les données d’application sont considérées comme « d’entreprise ».

**Comment Intune réinitialise-t-il des données à distance ?** Intune peut effacer des données d’application de trois manières différentes : réinitialisation complète de l’appareil, réinitialisation sélective pour la gestion des appareils mobiles et réinitialisation sélective pour la gestion des applications mobiles. Pour plus d’informations sur la réinitialisation à distance pour la gestion des appareils mobiles, consultez [Protégez vos données avec la réinitialisation complète ou sélective à l’aide de Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md). Pour plus d’informations sur la réinitialisation sélective à l’aide de la gestion des applications mobiles, consultez [Réinitialiser les données d’applications d’entreprise managées avec Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  1. **Qu’est-ce-que la réinitialisation complète ?** La [réinitialisation complète](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#full-wipe) supprime toutes les données et paramètres utilisateur de **l’appareil** en restaurant les paramètres d’usine par défaut de l’appareil. L’appareil est supprimé d’Intune.
  >[!NOTE]
  > La réinitialisation complète est possible uniquement sur les appareils inscrits dans la gestion des périphériques mobiles (GPM).

  2. **Qu’est-ce que la réinitialisation sélective pour la gestion des appareils mobiles ?** Consultez la rubrique [Protégez vos données avec la réinitialisation complète ou sélective à l’aide de Microsoft Intune](../deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune.md#selective-wipe) pour en savoir plus sur la réinitialisation sélective.

  3. **Qu’est-ce que la réinitialisation sélective pour la gestion des applications mobiles ?** La réinitialisation sélective pour la gestion des applications mobiles supprime simplement les données d’applications d’entreprise à partir d’une application. La requête est lancée à l’aide du portail Intune Azure. Pour savoir comment lancer une requête de réinitialisation, consultez [Réinitialiser les données d’applications d’entreprise managées avec Microsoft Intune](../deploy-use/wipe-managed-company-app-data-with-microsoft-intune.md)

  4. **Quelle est la vitesse de la réinitialisation sélective pour la gestion des applications mobiles ?** Si l’utilisateur utilise l’application lorsque la réinitialisation sélective est lancée, le Kit de développement logiciel (SDK) d’application Intune contrôle toutes les 30 minutes la présence d’une requête de réinitialisation sélective du service MAM Intune. Il vérifie également la présence d’une réinitialisation sélective lorsque l’utilisateur lance l’application pour la première fois et se connecte avec son compte professionnel ou scolaire.

**Pourquoi les services locaux (on-prem) ne fonctionnent-ils pas avec des applications protégées par Intune ?** La protection d’applications Intune dépend de la cohérence de l’identité de l’utilisateur entre l’application et le Kit de développement logiciel (SDK) d’application Intune. L’authentification moderne est la seule manière de la garantir. Il existe des scénarios dans lesquels les applications peuvent fonctionner avec une configuration locale. Mais elles ne sont ni cohérentes, ni garanties.

**Existe-t-il un moyen sécurisé d’ouvrir des liens web depuis des applications gérées ?** Oui ! L’administrateur informatique peut déployer et définir la stratégie de protection des applications pour [l’application Intune Managed Browser](../deploy-use/manage-internet-access-using-managed-browser-policies.md), un navigateur web développé par Microsoft Intune qui peut être géré facilement avec Intune. L’administrateur informatique peut exiger que tous les liens web dans les applications gérées par Intune soient ouverts à l’aide de l’application Managed Browser.


## <a name="app-experience-on-android"></a>Expérience d'application sur Android

**Pourquoi l’application Portail d’entreprise est-elle nécessaire pour que la protection des applications Intune fonctionne sur des appareils Android ?** La plupart des fonctionnalités de protection des applications sont intégrées à l’application Portail d’entreprise. L’inscription d’appareil n’est _pas obligatoire_, même si l’application Portail d’entreprise est toujours nécessaire. Pour la gestion des applications mobiles MAM sans inscription, l’utilisateur final doit simplement disposer de l’application Portail d’entreprise installée sur l’appareil.

## <a name="app-experience-on-ios"></a>Expérience d'application sur iOS

 **Je suis en mesure d’utiliser l’extension de partage iOS pour ouvrir des données professionnelles ou scolaires dans des applications non gérées, même si la stratégie de transfert de données est définie sur les « applications gérées uniquement » ou sur « Aucune application ». Cela ne provoque-t-il pas de fuite de données ?** La stratégie de protection des applications Intune ne peut pas contrôler l’extension de partage iOS sans gérer l’appareil. Par conséquent, Intune _**chiffre les données « d’entreprise » avant de les partager à l’extérieur de l’application**_. Vous pouvez valider cette action en essayant d’ouvrir le fichier « d’entreprise » en dehors de l’application gérée. Le fichier doit être chiffré et ne peut pas être ouvert en dehors de l’application gérée.

### <a name="see-also"></a>Voir aussi
- [Paramètres de stratégie de gestion des applications mobiles Android dans Microsoft Intune](../deploy-use/android-mam-policy-settings.md)
- [Paramètres de stratégie de gestion des applications mobiles iOS](../deploy-use/ios-mam-policy-settings.md)
- [Validation de la configuration de la gestion des applications mobiles](../deploy-use/validate-mobile-application-management.md)
- [Se préparer à configurer des stratégies de gestion des applications mobiles avec Microsoft Intune](../deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
- [Comment obtenir un support technique pour Microsoft Intune](../troubleshoot/how-to-get-support-for-microsoft-intune.md)
