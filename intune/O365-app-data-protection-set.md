---
title: Gestion des données des applications Office 365 dans Microsoft Intune
titlesuffix: ''
description: Découvrez-en plus sur la gestion des données des applications Office 365 dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a3eed03deb3f619f75502e8a9d1d66fefc38a081
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180069"
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps-in-microsoft-intune"></a>Quelle sera l’expérience de protection de base de vos utilisateurs sur des applications Office 365 gérées dans Microsoft Intune ?

L'Assistant **Gestion des applications Office 365** crée une stratégie de protection des applications pour chaque plateforme d'appareil.

L’Assistant active les stratégies suivantes :

**iOS**
* Chiffrer les données de l'application

**Android**
* Chiffrer les données de l'application
* Demander un code confidentiel simple pour l'accès

Ces stratégies garantissent que vous pouvez gérer les applications Office 365, ce qui vous donne la possibilité de réinitialiser les données de travail à partir des applications Office lorsque vous avez besoin. Elles garantissent également une protection de base au cas où un appareil est perdu ou volé en veillant à ce que vos données de travail soient chiffrées et à ce qu’un code confidentiel doive être entré pour afficher les données dans les applications Office 365.


Cet article utilise OneDrive Entreprise comme exemple pour montrer l’expérience utilisateur sur une application gérée par Intune.


>[!NOTE]
>En règle générale, sur un appareil personnel, l’utilisateur final téléchargerait l’application. Si l’appareil est géré par une solution de gestion des appareils mobiles (MDM), vous pouvez déployer l’application sur l’appareil.

## <a name="user-experience-on-an-ios-device"></a>Expérience utilisateur sur un appareil iOS

1. Lancez l’application OneDrive Entreprise pour ouvrir la page de connexion.  
2. Tapez votre nom d’utilisateur de compte professionnel. Vous êtes redirigé vers la page d’authentification Office 365 pour entrer vos informations d’identification professionnelles. 
3. Une fois vos informations d’identification correctement authentifiées par Azure Active Directory, les stratégies de protection des applications sont appliquées et il vous est demandé de redémarrer l’application OneDrive Entreprise. 

   > [!NOTE]
   > Le message de redémarrage nécessaire s’affiche uniquement sur les appareils qui ne sont pas inscrits dans Intune.

4. Redémarrez l’application OneDrive Entreprise. L’application démarre avec les stratégies de protection des applications activées et vous êtes invité à définir un code PIN pour l’appareil (si un code PIN n’est pas déjà configuré pour l’appareil).  

   > [!NOTE]
   > La plupart de vos utilisateurs ne verront pas cette invite. Seuls les utilisateurs qui n’ont pas activé de code PIN sur leur appareil iOS voient cette invite.

5. Une fois que vous avez défini le code PIN et l'avez confirmé, revenez à l’application OneDrive Entreprise. Vous verrez s'afficher un avertissement unique vous informant que votre administrateur informatique protège maintenant vos données de travail dans OneDrive. 
6. Cliquez sur cet avertissement pour accéder aux fichiers sur votre OneDrive Entreprise. 

>[!NOTE]
>Lorsque vous modifiez une stratégie déployée, les modifications sont appliquées la prochaine fois que vous ouvrez l’application.

## <a name="user-experience-on-an-android-device"></a>Expérience utilisateur sur un appareil Android

1. Lancez l’application OneDrive Entreprise pour ouvrir la page de connexion.  <br/> ![Image de l’écran de bienvenue de l’application OneDrive](./media/onedrive-android-welcome.png)
2. Tapez votre nom d’utilisateur de compte professionnel. Vous êtes redirigé vers la page d’authentification Office 365 pour entrer vos informations d’identification professionnelles. <br/> ![Image de la connexion à O365 sur Android](./media/o365-sign-in-android.png)
3. Une fois vos informations d’identification correctement authentifiées par Azure Active Directory, un message s’affiche, stipulant les instructions d’installation de l’application Portail d’entreprise, si celle-ci n’est pas encore installée sur l’appareil. Cliquez sur **Accéder au Store** pour continuer. <br/> ![Image du message permettant d'obtenir l’application Portail d’entreprise](./media/get-company-portal-android.png) <br/>Si vous avez déjà installé l’application Portail d’entreprise sur votre téléphone, l’application OneDrive Entreprise démarre automatiquement et vous pouvez ignorer la remarque finale.   

   > [!IMPORTANT]
   > Sur Android, une fois que vous avez défini les applications Office devant être gérées par une stratégie de protection des applications, l’utilisateur de l’appareil **doit** installer l’application Portail d’entreprise pour accéder à des e-mails et à des documents professionnels, même si l’utilisateur final n’a pas besoin d’ouvrir l’application ni de s’y connecter pour les lire vraiment.

4. Vous êtes maintenant dans Google Play Store, où vous pouvez télécharger et installer l’application Portail d’entreprise. L’application permet de sécuriser et de protéger les données. <br/> ![Image de l’application dans Google Play Store](./media/google-play-get-app-android.png)
5. Une fois l’installation de l'application terminée, choisissez **Accepter** pour accepter les termes du contrat. L’application OneDrive Entreprise démarre automatiquement.


>[!NOTE]
>La prochaine fois que vous ouvrez OneDrive Entreprise, vous pouvez être invité à définir un code PIN si votre service informatique l'exige. Une fois que vous avez défini et confirmé le code PIN, vous pouvez travailler avec OneDrive Entreprise.

![Image de l'invite de commande pour le code PIN](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>Quelles sont les stratégies définies par cet Assistant ?

|     |       | |
|----|--------|-|
|**Nom**|Gérer les applications Office 365| |
| **Description**|Créé par l’Assistant d’applications Gérer Office 365| |
| |  | |
| **Nom du paramètre** |**Valeur de la stratégie iOS** | **Valeur de la stratégie Android** |
|Interdire les sauvegardes iTunes et iCloud| Non | N/A |
|Interdire les sauvegardes Android |N/A | Non|
|Autoriser l'application à transférer des données vers d'autres applications | Toutes les applications | Toutes les applications|
|Autoriser l'application à recevoir des données d'autres applications| Toutes les applications | Toutes les applications|
|Interdire l’option Enregistrer sous | Non | Non|
|Restreindre les opérations Couper, Copier et Coller avec d’autres applications | N’importe quelle application | N’importe quelle application |
|Afficher le contenu web uniquement dans Managed Browser | Non| Non|
|Chiffrer les données de l'application | Quand l’appareil est verrouillé | Oui|
|Désactiver la synchronisation des contacts | Non| Non|
|Désactiver l’impression | Non | Non|
|Exiger un code confidentiel d’accès | Non | Oui|
|Nombre de tentatives avant réinitialisation du code confidentiel | N/A |5|
|Autoriser un code PIN simple | N/A |Oui|
|Longueur du code PIN | N/A | 4|
|Autoriser une empreinte digitale à la place du code confidentiel | N/A | Oui |
|Exiger des informations d'identification d'entreprise pour l'accès | Non | Non|
|Bloquer l’exécution des applications gérées sur les appareils jailbroken ou rootés | Non | Non|
|Revérifier les exigences d'accès après (minutes) - Délai | 30 | 30|
|Revérifier les exigences d'accès après (minutes) - Période de grâce hors connexion | 720 |720|
|Intervalle hors connexion (jours) avant la réinitialisation des données d'application | 90 | 90|
|Bloquer la capture d'écran (appareils Android uniquement) | N/A | Non |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>Pourquoi une stratégie de code PIN d'application est-elle configurée uniquement pour les appareils Android ?
Le chiffrement fonctionne différemment sur iOS et Android.

Sur iOS, pour les applications associées à une stratégie de protection des applications Intune, les données sont chiffrées au repos par le biais du chiffrement au niveau de l’appareil fourni par le système d’exploitation. Par conséquent, lorsque vous activez la stratégie de chiffrement d’application, vous obligez automatiquement également l’utilisateur à entrer un code PIN pour l'appareil afin d'accéder aux données de travail. Les utilisateurs qui n’ont pas déjà configuré un code PIN sur l'appareil seront invités à créer un code PIN pour l'appareil.

Sur Android, pour les applications associées à une stratégie de protection des applications Intune, les données sont chiffrées de manière synchrone lors des tâches d’E/S de fichier. Le contenu figurant sur le stockage de l’appareil est toujours chiffré. Sur les appareils qui ne sont pas gérés par MDM, une stratégie de protection des applications ne peut pas imposer la nécessité d’un code PIN de l’appareil. Pour vous assurer que les utilisateurs doivent utiliser un code PIN pour accéder à des données de travail, l'Assistant active la stratégie de code PIN d’application.

Vous pouvez toujours modifier ces paramètres de stratégie pour répondre aux besoins de votre organisation.

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>Comment puis-je afficher et modifier les stratégies créées par l’Assistant ?
Pour afficher ou mettre à jour ces stratégies ou des stratégies que vous créez dans le portail Intune Azure, choisissez, dans le tableau de bord, **Gérer les applications** > **Stratégies de protection des applications**. La liste des stratégies s’ouvre à droite. Choisissez la stratégie que vous souhaitez afficher pour afficher et modifier les paramètres. <br/>
![Image du chemin de l’interface utilisateur pour afficher les stratégies](./media/image-for-faq.png)

## <a name="next-steps"></a>Étapes suivantes
- En savoir plus sur les [stratégies de protection des applications](app-protection-policy.md).
