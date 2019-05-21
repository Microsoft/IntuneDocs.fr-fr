---
title: fichier descriptif
description: fichier descriptif
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: ffcef5b4d78856709f8563ee1f667ec7e5d993b3
ms.sourcegitcommit: d2e04a38e024b0f5afb0ca202823227de9da3ad1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65732598"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Modifier le flux de travail d’inscription avec le Portail d’entreprise Intune sur les appareils iOS d’entreprise qui s’authentifient avec l’Assistant Configuration <!-- 1927359 -->
Il existe une modification à venir dans le flux de travail pour l’inscription des appareils iOS via une des méthodes d’inscription des appareils d’entreprise Apple : Apple Configurator, Apple Business Manager, Apple School Manager ou le Programme d’inscription des appareils (DPE) Apple, lorsque vous utilisez l’Assistant Configuration pour l’authentification. Cette modification s’applique uniquement aux appareils inscrits sans affinité utilisateur.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Lorsque cette modification est déployée, des profils d’inscription dans Intune sur le Portail Azure sont mis à jour afin qu’il soit possible de spécifier la façon dont les appareils sont authentifiés et d’indiquer s’ils peuvent recevoir l’application Portail d’entreprise. Il y aura un flux de travail amélioré pour inscrire des appareils iOS via les méthodes répertoriées ci-dessus. 

- Lors de l’inscription de nouveaux appareils et de l’authentification avec l’Assistant Configuration, vous serez en mesure de choisir s’il faut ou pas déployer automatiquement l’application Portail d’entreprise. Les utilisateurs finaux ne verront plus l’écran « Identifiez votre appareil » ni l’écran « Confirmez votre appareil » dans la procédure d’inscription.  
- Sur les appareils déjà inscrits via l’Assistant Configuration à partir d’une des méthodes d’inscription des appareils d’entreprise d’Apple, vous devez agir si vous souhaitez activer l’accès conditionnel. Vous devrez [configurer une stratégie de configuration d’application](https://aka.ms/enrollment_setup_assistant) avec un fichier xml spécifique pour envoyer le Portail d’entreprise à ces appareils.  Si vous décidez d’envoyer le Portail d'entreprise de cette manière, les utilisateurs finaux ne verront plus l’écran « Identifiez votre appareil » ni l’écran « Confirmez votre appareil » dans la procédure d’inscription. 
- Une fois cette modification déployée, si vous n’avez pas déployé le Portail d’entreprise avec le profil de configuration d’application mentionné ci-dessus et si les utilisateurs finaux téléchargent l’application Portail d’entreprise à partir de l’App Store, ils peuvent se connecter, mais ils recevront un message d’erreur. Ils ne pourront pas utiliser l’application pour l’accès conditionnel. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Si vous prévoyez d’utiliser le flux de travail modifié, il faudra alors mettre à jour votre Guide de l’utilisateur final pour indiquer que :

- Les utilisateurs finaux ne verront plus les deux écrans indiqués plus haut dans la procédure d’inscription. 
- Ils devront se connecter au Portail d’entreprise lorsqu’il est automatiquement déployé et non téléchargé à partir de l’App Store. 

Vous pouvez choisir de créer une stratégie de configuration d’application maintenant, si nécessaire, lors de la préparation de cette modification. Lorsque ce nouveau flux de travail se déploie, vous verrez des profils d’inscription mis à jour dans la console. Nous vous informerons également de ce déploiement via le centre de messages. Ensuite, vous devrez agir afin que vos utilisateurs finaux puissent s’inscrire via le programme DEP en s’authentifiant avec l’Assistant Configuration et vous pourrez utiliser le Portail d’entreprise pour l’accès conditionnel.

#### <a name="additional-information"></a>Informations supplémentaires 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Mettre à jour votre application de Portail d’entreprise Android vers la dernière version <!--4536963-->
Intune publie régulièrement des mises à jour vers l’application Portail d’entreprise Android. En novembre 2018, nous avons publié une mise à jour du portail d’entreprise, incluant un commutateur principal pour vous préparer à la modification de Google à partir de leur plateforme de notification existante vers Firebase Cloud Messaging (FCM) de Google. Une fois que Google a retiré sa plateforme de notification et s’est déplacé vers FCM, les utilisateurs finaux doivent avoir mis à jour leur application Portail d’entreprise au moins vers la version de novembre 2018 pour continuer à communiquer avec Google Play Store.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Notre télémétrie indique que vous avez des appareils avec une version du Portail d’entreprise antérieure à 5.0.4269.0. Si cette version ou une version ultérieure de l’application Portail d’entreprise n’est pas installée, les professionnels de l’informatique lancent des actions telles que la réinitialisation de tout l’appareil, la réinitialisation du mot de passe, l’installation des applications disponibles et requises et l’inscription des certificats peut ne pas fonctionner comme prévu. Si vos appareils sont inscrits à la Gestion des données de référence dans Intune, vous pouvez voir les versions du portail d’entreprise et les utilisateurs en accédant à des applications clientes – applications découvertes. En sélectionnant les versions antérieures du Portail d’entreprise, vous pourrez voir ce quels utilisateurs finaux disposent des appareils qui n’ont pas de mises à jour du portail d’entreprise.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Demandez aux utilisateurs finaux d’appareils Android qui n’ont pas été mis à jour de mettre à jour le portail d’entreprise via Google Play. Informez le support technique au cas où un utilisateur n’a pas conservé la mise à jour automatique de l’application Portail d’entreprise. Consultez le lien informations supplémentaires pour en savoir plus sur la plateforme FCM et les modifications apportées par Google.

#### <a name="additional-information"></a>Informations supplémentaires
https://firebase.google.com/docs/cloud-messaging/