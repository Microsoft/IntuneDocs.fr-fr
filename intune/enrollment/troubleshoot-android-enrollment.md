---
title: Résoudre les problèmes liés aux appareils Android Entreprise dans Microsoft Intune
description: Suggestions pour résoudre les problèmes les plus courants lors de l’inscription d’appareils Android dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04c726c1dc6af7e92b75335d105de605ef00e712
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652366"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>Résoudre les problèmes liés aux appareils Android Entreprise dans Microsoft Intune

Cet article aide les administrateurs Intune à comprendre et à résoudre les problèmes liés à l’inscription d’appareils Android Entreprise dans Intune.

## <a name="apps-on-android-enterprise-devices"></a>Applications sur des appareils Android Entreprise

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>Les applications Google Play géré qui ne sont pas déployées par le biais d’Intune apparaissent dans le profil professionnel
Les applications système peuvent être activées dans le profil professionnel par le fabricant OEM de l’appareil au moment de la création du profil professionnel. Le fournisseur MDM n’a aucun contrôle dessus.

Pour résoudre le problème, effectuez les étapes suivantes :

  1. Collectez les journaux du portail d’entreprise.
  2. Notez les applications qui apparaissent dans le profil professionnel de manière inattendue.
  3. Désinscrivez l’appareil d’Intune et désinstallez le Portail d’entreprise.
  4. Installez l’application [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc), celle-ci permettant de créer un profil professionnel sans EMM à des fins de test.
  5. Suivez les instructions fournies dans [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) pour créer un profil professionnel sur l’appareil.
  6. Passez en revue les applications qui apparaissent dans le profil professionnel. 
  7. Si les mêmes applications figurent dans l’application Test DPC, elles sont donc attendues par le fabricant OEM de cet appareil.

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>Les applications non approuvées du store Google Play for Work géré ne sont pas supprimées de la page Applications clientes dans Intune
Ce comportement est normal.

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>Les applications Google Play gérées ne sont pas signalées sous le panneau Applications découvertes dans le portail Intune
Ce comportement est normal. Seules les applications système installées dans le profil professionnel sont inventoriées dans le panneau Applications découvertes. Pour voir les applications installées du Google Play géré, utilisez le panneau **Applications gérées**.

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>Les applications web sont-elles prises en charge pour les appareils inscrits avec un profil professionnel ?
Oui. Pour plus d’informations, consultez [Liens web Google Play gérés](../apps/apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="device-management"></a>Gestion des appareils

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>Chemin de fichier Internal storage/Android/Data.com.microsoft.windowsintune.companyportal/files manquant sur les appareils inscrits avec un profil professionnel

  **Réponse** : Ce comportement est normal. Ce chemin est créé uniquement pour le scénario d’administrateur d’appareil (inscription Android héritée).

  Pour collecter les journaux du portail d’entreprise, effectuez les étapes suivantes :

  1. Dans l’application Portail d’entreprise avec le badge, appuyez sur **Menu** > **Aide** > **Envoyer un e-mail au support**, puis sur **Envoyer un e-mail et charger les journaux**. 
  2. À l’invite **Envoyer une demande d’aide avec**, sélectionnez l’une des applications de messagerie.
  3. Un e-mail est généré pour votre administrateur informatique avec un ID d’incident qui peut être fourni au support produit de Microsoft.

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>L’heure de la dernière synchronisation de Google Play géré n’a pas été mise à jour depuis plusieurs jours
Ce comportement est normal. La synchronisation ne se produit que si vous la déclenchez manuellement.

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>Le chiffrement est obligatoire lors de l’inscription d’un appareil. Peut-il être désactivé ?
Non, Google exige que l’appareil soit chiffré pour créer un profil professionnel. 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>Les appareils Samsung bloquent l’utilisation de claviers tiers comme SwiftKey
Samsung a commencé à appliquer cette restriction sur les appareils Android 8.0+. Microsoft travaille actuellement avec Samsung sur ce problème et publiera de nouvelles informations quand elles seront disponibles.

## <a name="remote-actions"></a>Actions à distance

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>L’option Effacer (réinitialisation aux paramètres d’usine) n’est pas disponible pour un appareil inscrit avec un profil professionnel
Ce comportement est normal. Dans le scénario d’un profil professionnel, le fournisseur MDM n’a pas un contrôle total sur l’appareil. La seule option disponible est Mettre hors service (Supprimer les données de l’entreprise), qui supprime le profil professionnel en entier et tout son contenu.

### <a name="is-device-passcode-reset-supported"></a>La réinitialisation du code secret d’un appareil est-elle prise en charge ?
Pour les appareils inscrits avec un profil professionnel, vous pouvez uniquement réinitialiser le code secret du profil sur les appareils Android 8.0 ou ultérieur dans les cas suivants :
- Le code secret du profil professionnel est géré.
- L’utilisateur final vous a autorisé à le réinitialiser.

Pour les appareils dédiés (COSU) et entièrement gérés, la réinitialisation du code secret de l’appareil est prise en charge.


## <a name="next-steps"></a>Étapes suivantes

- [Résoudre les problèmes d’inscription d’appareils dans Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Posez une question sur le forum Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Lire le blog de l’équipe de support Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Lire le blog Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)