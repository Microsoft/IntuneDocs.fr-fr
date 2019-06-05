---
title: fichier descriptif
description: fichier descriptif
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 1073a38da8a5b2467b1ff8c97b32b93f92e34e4c
ms.sourcegitcommit: f90cba0b2c2672ea733052269bcc372a80772945
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454131"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune. 

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Mettre à jour votre application de Portail d’entreprise Android vers la dernière version <!--4536963-->
Intune publie régulièrement des mises à jour vers l’application Portail d’entreprise Android. En novembre 2018, nous avons publié une mise à jour du portail d’entreprise, incluant un commutateur principal pour vous préparer à la modification de Google à partir de leur plateforme de notification existante vers Firebase Cloud Messaging (FCM) de Google. Une fois que Google a retiré sa plateforme de notification et s’est déplacé vers FCM, les utilisateurs finaux doivent avoir mis à jour leur application Portail d’entreprise au moins vers la version de novembre 2018 pour continuer à communiquer avec Google Play Store.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Notre télémétrie indique que vous avez des appareils avec une version du Portail d’entreprise antérieure à 5.0.4269.0. Si cette version ou une version ultérieure de l’application Portail d’entreprise n’est pas installée, les professionnels de l’informatique lancent des actions telles que la réinitialisation de tout l’appareil, la réinitialisation du mot de passe, l’installation des applications disponibles et requises et l’inscription des certificats peut ne pas fonctionner comme prévu. Si vos appareils sont inscrits à la Gestion des données de référence dans Intune, vous pouvez voir les versions du portail d’entreprise et les utilisateurs en accédant à des applications clientes – applications découvertes. En sélectionnant les versions antérieures du Portail d’entreprise, vous pourrez voir ce quels utilisateurs finaux disposent des appareils qui n’ont pas de mises à jour du portail d’entreprise.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Demandez aux utilisateurs finaux d’appareils Android qui n’ont pas été mis à jour de mettre à jour le portail d’entreprise via Google Play. Informez le support technique au cas où un utilisateur n’a pas conservé la mise à jour automatique de l’application Portail d’entreprise. Consultez le lien informations supplémentaires pour en savoir plus sur la plateforme FCM et les modifications apportées par Google.

#### <a name="additional-information"></a>Informations supplémentaires
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-fullscreen-experience-coming-to-intune---4593669--"></a>Nouvelle expérience plein écran prochainement disponible sur Intune <!--4593669-->
Nous déployons actuellement une mise à jour des options de création et d’édition dans l’interface utilisateur Intune sur le portail Azure. Cette nouvelle expérience simplifiera les flux de travail existants grâce à un format de style assistant condensé au sein d’un seul panneau. Cette mise à jour fera disparaître la « prolifération de panneaux » ainsi que tous les flux de création et d’édition qui vous obligent à parcourir de façon approfondie une multitude de panneaux. Les flux de travail de création seront également à jour pour inclure des affectations (à l’exception de l’affectation d’applications).

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
L’expérience plein écran sera déployée sur Intune à la fois sur portal.azure.com et sur devicemanagement.microsoft.com dans les prochains mois. Cette mise à jour de l’interface utilisateur n’aura aucune incidence sur la fonctionnalité de vos stratégies et profils existants : vous bénéficierez simplement d’un flux de travail légèrement modifié. Lorsque vous créez des stratégies, par exemple, vous pourrez définir certaines attributions dans le cadre de ce flux au lieu d’effectuer cette opération après la création de la stratégie. Consultez le billet de blog de la section Informations supplémentaires pour obtenir des captures d’écran présentant la nouvelle expérience dans la console.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Vous n’avez rien à faire, mais nous vous recommandons de mettre à jour vos ressources informatiques professionnelles. Nous mettrons à jour notre documentation à mesure que cette expérience est déployée sur les différents panneaux Intune dans le portail Azure.

#### <a name="additional-information"></a>Informations supplémentaires 
https://aka.ms/intune_fullscreen
