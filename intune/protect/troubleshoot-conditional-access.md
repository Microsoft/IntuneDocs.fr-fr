---
title: Résoudre les problèmes d’accès conditionnel
titleSuffix: Microsoft Intune
description: Cette rubrique décrit les actions à entreprendre quand vos utilisateurs ne parviennent pas à accéder à des ressources par le biais de l’accès conditionnel Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c662de98ffa497c5fbc89ac1b78ed8537ff0d80c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71732696"
---
# <a name="troubleshoot-conditional-access"></a>Résoudre les problèmes d’accès conditionnel
Cet article décrit que faire quand vos utilisateurs ne parviennent pas à accéder aux ressources protégées avec l’accès conditionnel, ou quand des utilisateurs peuvent accéder aux ressources protégées alors qu’ils devraient être bloqués.

Avec Intune et l’accès conditionnel, vous pouvez protéger l’accès aux services comme :
- Services Office 365 comme Exchange Online, SharePoint Online et Skype entreprise Online
- Exchange sur site
- Divers autres services

Cette capacité vous permet de vérifier que seuls les périphériques inscrits avec Intune et conformes aux règles d’accès conditionnel que vous avez définies dans la console de l’administrateur Intune ou Azure Active Directory ont accès aux ressources de votre entreprise. 

## <a name="requirements-for-conditional-access"></a>Conditions requises pour l’accès conditionnel

Les conditions suivantes doivent être remplies pour que l’accès conditionnel fonctionne :

- Le périphérique doit être inscrit dans MDM et géré par Intune.

- L’utilisateur et l’appareil doivent être conformes aux stratégies de conformité Intune attribuées

- Par défaut, une stratégie de conformité doit être affectée à l’utilisateur. Cela peut dépendre de la configuration du paramètre **Marquer les périphériques sans stratégie de conformité comme étant** sous **Conformité de l’appareil** > **Paramètres de stratégie de conformité** dans le portail d’administration Intune.

- Exchange ActiveSync doit être activé sur l’appareil si l’utilisateur utilise le client d’e-mail natif de l’appareil plutôt qu’Outlook. Cela se produit automatiquement pour les périphériques iOS, Windows Phone et Android Knox.

- Pour Exchange sur site, votre connecteur Exchange Intune doit être correctement configuré. Pour plus d’informations, consultez [Résolution des problèmes liés au connecteur Exchange dans Microsoft Intune](troubleshoot-exchange-connector.md).

- Pour Skype sur site, vous devez configurer l’authentification hybride moderne. Consultez [vue d’ensemble de l’authentification moderne hybride](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview).

Vous pouvez consulter ces conditions sur chaque appareil dans le portail Azure et dans le rapport d’inventaire des appareils.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Les appareils apparaissent comme étant conformes, mais les utilisateurs sont quand même bloqués

- Assurez-vous que l’utilisateur dispose d’une licence Intune pour l’évaluation de la conformité.

- L’accès des périphériques Android non Knox ne sera pas accordé tant que l’utilisateur ne cliquera pas sur le lien **Démarrer maintenant** dans l’e-mail de mise en quarantaine reçu. Cela s’applique même si l’utilisateur est déjà inscrit dans Intune. Si l’utilisateur ne reçoit pas l’e-mail avec le lien sur son téléphone, il peut utiliser un PC pour accéder à ses e-mails et les transférer vers un compte de courrier sur son périphérique.

- Quand un appareil est inscrit pour la première fois, l’inscription des informations de conformité de l’appareil peut demander un certain temps. Attendez quelques minutes et réessayez.

- Pour les périphériques iOS, un profil de messagerie existant peut bloquer le déploiement d’un profil de messagerie créé par un administrateur Intune et affecté à cet utilisateur, rendant ainsi le périphérique non conforme. Dans ce scénario, l’application Portail d’entreprise signale à l’utilisateur qu’il n’est pas conforme en raison de son profil de messagerie configuré manuellement et elle l’invite à supprimer ce profil. Une fois que l’utilisateur a supprimé le profil de messagerie existant, le profil de messagerie Intune est déployé avec succès. Pour éviter ce problème, demandez à vos utilisateurs de supprimer les profils de messagerie existants sur leur appareil avant de s’inscrire.

- Un périphérique peut rester bloqué dans un état de vérification de conformité, ce qui empêche l’utilisateur de démarrer une autre vérification. Si vous avez un appareil dans cet État :
  - Vérifiez que l’appareil utilise la dernière version de l’application Portail d’entreprise.
  - Redémarrez l’appareil.
  - Vérifiez si le problème persiste sur différents réseaux (par exemple, cellulaire, Wi-Fi, et ainsi de suite).

  Si le problème persiste, contactez le support Microsoft comme décrit dans [Guide pratique pour obtenir un support technique pour Microsoft Intune](../fundamentals/get-support.md).

- Certains périphériques Android peuvent paraître chiffrés, alors que l’application Portail d’entreprise les reconnaît comme non chiffrés et les marque donc comme non conformes. Dans ce scénario, l’utilisateur reçoit une notification dans l’application Portail d’entreprise l’invitant à définir un code secret de démarrage pour l’appareil. Après avoir appuyé sur la notification et confirmé votre code PIN ou mot de passe existant, choisissez l’option **Exiger un code confidentiel pour démarrer l’appareil** dans l’écran **Démarrage sécurisé**, puis appuyez sur le bouton **Vérifier la conformité**  pour l’appareil dans l’application Portail d’entreprise. L’appareil doit maintenant être détecté comme chiffré. 

  > [!NOTE]
  > Certains fabricants de périphériques chiffrent leurs appareils à l’aide d’un code confidentiel par défaut au lieu du code confidentiel défini par l’utilisateur. Intune affiche le chiffrement qui utilise un code confidentiel par défaut comme non sécurisé et marque donc ces périphériques comme non conformes jusqu’à ce que l’utilisateur crée un nouveau code confidentiel différent du code par défaut.

- Un périphérique Android inscrit et conforme peut quand même être bloqué et recevoir une notification de mise en quarantaine quand vous tentez d’accéder pour la première fois à des ressources d’entreprise. Si cela se produit, vérifiez que l’application Portail d’entreprise n’est pas en cours d’exécution, sélectionnez le lien **Démarrer maintenant** dans l’e-mail de mise en quarantaine pour déclencher l’évaluation. Cette opération ne doit en principe être nécessaire que lors de l’activation initiale de l’accès conditionnel.

- Un appareil Android inscrit peut demander à l’utilisateur « aucun certificat trouvé » et ne pas être autorisé à accéder aux ressources O365. L’utilisateur doit activer l’option *Activer l’accès du navigateur* sur l’appareil inscrit comme suit :
  1. Ouvrez l'application Portail d'entreprise.
  2. Accéder à la page Paramètres à partir des trois points (...) ou du bouton de menu matériel.
  3. Sélectionnez le bouton *Activer l’accès du navigateur*.
  4. Dans le navigateur Chrome, se déconnecter d’Office 365 et redémarrer Chrome.  


## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Les appareils sont bloqués et aucun e-mail de mise en quarantaine n’est reçu

- Vérifiez que l’appareil est visible dans la console d’administration Intune comme appareil Exchange ActiveSync. Si ce n’est pas le cas, la découverte des appareils est certainement défaillante, probablement en raison d’un problème lié au connecteur Exchange. Pour plus d’informations, consultez [Résoudre les problèmes liés au connecteur Exchange local Intune](troubleshoot-exchange-connector.md).

- Avant de bloquer un appareil, le connecteur Exchange envoie un e-mail d’activation (mise en quarantaine). Si l’appareil est hors connexion, il risque de ne pas recevoir l’e-mail d’activation. 

- Vérifiez si le client de messagerie sur l’appareil est configuré pour récupérer le courrier à l’aide de **Push** plutôt que **Poll**. Si c’est le cas, l’utilisateur risque de ne pas voir l’e-mail. Basculez sur **Poll** et vérifiez si l’appareil reçoit l’e-mail.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Les appareils ne sont pas conformes, mais les utilisateurs ne sont pas bloqués

- Pour les PC Windows, l’accès conditionnel bloque uniquement l’application de messagerie native, Office 2013 avec authentification moderne ou Office 2016. Le blocage des versions antérieures d’Outlook ou de toutes les applications de messagerie sur les PC Windows nécessite de configurer l’inscription d’appareil AAD et AD FS (Active Directory Federation Services) conformément aux instructions fournies dans [Configurer SharePoint Online et Exchange Online pour l’accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication).

- Si l’appareil est réinitialisé de manière sélective ou supprimé d’Intune, il peut continuer à avoir accès pendant plusieurs heures après la mise hors service. En effet, Exchange met en cache les droits d’accès pendant 6 heures. Envisagez d’autres moyens de protéger les données sur les appareils mis hors service dans ce scénario.

- Surface Hub, les appareils Windows inscrits en bloc et DEM peuvent prendre en charge l’accès conditionnel lorsqu’un utilisateur auquel est attribuée une licence Intune est connecté. Toutefois, vous devez déployer la stratégie de conformité sur les groupes d’appareils (et non sur les groupes d’utilisateurs) pour une évaluation correcte.

- Vérifiez les affectations de vos stratégies de conformité et de vos stratégies d’accès conditionnel. Si un utilisateur n’est pas dans le groupe auquel sont affectées les stratégies, ou s’il appartient à un groupe exclu, l’utilisateur n’est pas bloqué. La conformité est vérifiée uniquement pour les appareils des utilisateurs appartenant à un groupe attribué.

## <a name="noncompliant-device-is-not-blocked"></a>Un appareil non conforme n’est pas bloqué

Si un appareil n’est pas conforme mais continue d’y accéder, effectuez les actions suivantes.

- Vérifiez vos groupes cibles et d’exclusion. Si un utilisateur n’est pas dans le bon groupe cible ou est dans le groupe d’exclusions, il n’est pas bloqué. Seuls les appareils des utilisateurs d’un groupe cible sont vérifiés pour la conformité.

- Assurez-vous que l’appareil est en cours de découverte. Le connecteur Exchange pointe-t-il sur la sécurité d’accès du code Exchange 2010 quand l’utilisateur est sur un serveur Exchange 2013 ? Dans ce cas, si la règle d’Exchange par défaut est Autoriser, même si l’utilisateur est dans le groupe cible, Intune ne peut pas savoir si l’appareil est connecté à Exchange.

- Vérifiez l’état Existence/accès de l’appareil dans Exchange :
  - Utilisez cette cmdlet PowerShell pour obtenir une liste de tous les appareils mobiles pour une boîte aux lettres : 'Get-ActiveSyncDeviceStatistics -mailbox mbx'. Si l’appareil n’est pas répertorié, cela signifie qu’il n’accède pas à Exchange.
  
  - Si le périphérique se trouve dans la liste, utilisez la cmdlet Get-CASmailbox -identity:’upn’ | fl' pour obtenir des informations détaillées sur son état d’accès que vous fournirez au Support Microsoft.

## <a name="next-steps"></a>Étapes suivantes
Si ces informations ne vous aident pas, vous pouvez également [obtenir du support technique pour Microsoft Intune](../fundamentals/get-support.md).
