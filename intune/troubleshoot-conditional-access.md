---
title: Résoudre les problèmes d’accès conditionnel
titleSuffix: Microsoft Intune
description: Cette rubrique décrit les actions à entreprendre quand vos utilisateurs ne parviennent pas à accéder à des ressources par le biais de l’accès conditionnel Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
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
ms.openlocfilehash: e8ebc708f76ed1f55f512edda75206d3ed5890a0
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530718"
---
# <a name="troubleshoot-conditional-access"></a>Résoudre les problèmes d’accès conditionnel

Vous pouvez protéger l’accès à des services Office 365 comme Exchange Online, SharePoint Online, Skype Entreprise Online, Exchange sur site et d’autres services à l’aide d’Intune et de l’accès conditionnel. Cette fonctionnalité vous permet de vous assurer que l’accès aux ressources d’entreprise est limité aux appareils qui sont inscrits auprès d’Intune et qui respectent les règles d’accès conditionnel que vous avez définies dans la console d’administration Intune ou Azure Active Directory. Cet article décrit que faire quand vos utilisateurs ne parviennent pas à accéder aux ressources protégées avec l’accès conditionnel, ou quand des utilisateurs peuvent accéder aux ressources protégées alors qu’ils devraient être bloqués.

## <a name="requirements-for-conditional-access"></a>Conditions requises pour l’accès conditionnel

Les conditions suivantes doivent être remplies pour que l’accès conditionnel fonctionne :

- L’appareil doit être inscrit et géré par Intune
- L’utilisateur et l’appareil doivent être conformes aux stratégies de conformité Intune attribuées
- Par défaut, une stratégie de conformité doit être affectée à l’utilisateur. Cela peut dépendre de la façon dont le paramètre **Marquer les appareils sans stratégie de conformité comme étant** est configuré sous **Conformité de l’appareil** > **Paramètres de stratégie de conformité** dans le portail d’administration Intune
- Exchange ActiveSync doit être activé sur l’appareil si l’utilisateur utilise le client d’e-mail natif de l’appareil plutôt qu’Outlook. Cela se fait automatiquement pour les appareils iOS, Windows Phone et Android
- Votre connecteur Exchange Intune doit être configuré correctement. Pour plus d’informations, consultez [Dépannage du connecteur Exchange dans Microsoft Intune](troubleshoot-exchange-connector.md).

Vous pouvez consulter ces conditions sur chaque appareil dans le portail Azure et dans le rapport d’inventaire des appareils.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Les appareils apparaissent comme étant conformes, mais les utilisateurs sont quand même bloqués

- L’accès n’est pas accordé aux appareils Android non-Knox tant que l’utilisateur n’a pas cliqué sur le lien **C’est parti !** contenu dans l’e-mail de quarantaine qu’il reçoit. Cela s’applique même si l’utilisateur est déjà inscrit dans Intune. Si l’utilisateur ne reçoit pas l’e-mail avec le lien sur son téléphone, il peut utiliser un PC pour accéder à son courrier électronique et le transférer vers un compte e-mail sur son appareil.
- Quand un appareil est inscrit pour la première fois, l’inscription des informations de conformité de l’appareil peut demander un certain temps. Attendez quelques minutes et réessayez.
- Pour les appareils iOS, un profil de messagerie existant peut bloquer le déploiement d’un profil de messagerie créé par un administrateur Intune et affecté à cet utilisateur, rendant ainsi l’appareil non conforme. Dans ce scénario, l’application Portail d’entreprise signale à l’utilisateur qu’il n’est pas conforme en raison de son profil de messagerie configuré manuellement, et elle l’invite à supprimer ce profil. Une fois que l’utilisateur a supprimé le profil de messagerie existant, le profil de messagerie Intune est déployé avec succès. Pour éviter ce problème, demandez à vos utilisateurs de supprimer les profils de messagerie existants sur leur appareil avant de s’inscrire.
- Un appareil peut rester bloqué dans un état de vérification de conformité, ce qui empêche l’utilisateur de lancer une autre vérification. Si vous avez un appareil dans cet état, essayez ce qui suit :
  - Vérifiez que l’appareil utilise la dernière version de l’application Portail d’entreprise.
  - Redémarrez l’appareil.
  - Vérifiez si le problème persiste sur différents réseaux (par exemple, cellulaire, Wi-Fi, et ainsi de suite).

  Si le problème persiste, contactez le support Microsoft comme décrit dans [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md).
- Certains appareils Android peuvent paraître chiffrés, alors que l’application Portail d’entreprise les reconnaît comme non chiffrés et les marque donc comme non conformes. Dans ce scénario, l’utilisateur reçoit une notification dans l’application Portail d’entreprise l’invitant à définir un code secret de démarrage pour l’appareil. Après avoir appuyé sur la notification et confirmé votre code PIN ou mot de passe existant, choisissez l’option **Exiger un code confidentiel pour démarrer l’appareil** dans l’écran **Démarrage sécurisé**, puis appuyez sur le bouton **Vérifier la conformité**  pour l’appareil dans l’application Portail d’entreprise. L’appareil doit maintenant être détecté comme chiffré. 
  > [!NOTE]
  > Certains fabricants d’appareils chiffrent leurs appareils à l’aide d’un code PIN par défaut au lieu du code PIN défini par l’utilisateur. Intune considère l’utilisation du code PIN par défaut comme non sécurisée, et marque donc ces appareils comme non conformes jusqu’à ce que l’utilisateur crée un nouveau code PIN différent du code PIN par défaut.
- Un appareil Android inscrit et conforme peut quand même être bloqué et recevoir une notification de mise en quarantaine quand vous tentez d’accéder pour la première fois à des ressources d’entreprise. Si cela se produit, vérifiez que l’application Portail d’entreprise n’est pas en cours d’exécution, puis cliquez sur le lien **C’est parti !** dans l’e-mail de mise en quarantaine pour déclencher l’évaluation. Cette opération ne doit en principe être nécessaire que lors de l’activation initiale de l’accès conditionnel.

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Les appareils sont bloqués et aucun e-mail de mise en quarantaine n’est reçu

- Vérifiez que l’appareil est visible dans la console d’administration Intune comme appareil Exchange ActiveSync. Si ce n’est pas le cas, la découverte des appareils est certainement défaillante, probablement en raison d’un problème lié au connecteur Exchange. Pour plus d’informations, consultez [Résoudre les problèmes liés au connecteur Exchange local Intune](troubleshoot-exchange-connector.md).
- Avant de bloquer un appareil, le connecteur Exchange envoie un e-mail d’activation (mise en quarantaine). Si l’appareil est hors connexion, il risque de ne pas recevoir l’e-mail d’activation. 
- Vérifiez si le client de messagerie sur l’appareil est configuré pour récupérer le courrier à l’aide de **Push** plutôt que **Poll**. Si c’est le cas, l’utilisateur risque de ne pas voir l’e-mail. Basculez sur **Poll** et vérifiez si l’appareil reçoit l’e-mail.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Les appareils ne sont pas conformes, mais les utilisateurs ne sont pas bloqués

- Pour les PC Windows, l’accès conditionnel bloque uniquement l’application de messagerie native, Office 2013 avec authentification moderne ou Office 2016. Le blocage des versions antérieures d’Outlook ou de toutes les applications de messagerie sur les PC Windows nécessite de configurer l’inscription d’appareil AAD et AD FS (Active Directory Federation Services) conformément aux instructions fournies dans [Configurer SharePoint Online et Exchange Online pour l’accès conditionnel Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication). 
- Si l’appareil est réinitialisé de manière sélective ou supprimé d’Intune, il peut continuer à avoir accès pendant plusieurs heures après la mise hors service. En effet, Exchange met en cache les droits d’accès pendant 6 heures. Envisagez d’autres moyens de protéger les données sur les appareils mis hors service dans ce scénario.
- Les appareils Surface Hub prennent en charge l’accès conditionnel ; toutefois, vous devez déployer la stratégie de conformité sur des groupes d’appareils (et non des groupes d’utilisateurs) pour que l’évaluation soit correcte.
- Vérifiez les affectations de vos stratégies de conformité et de vos stratégies d’accès conditionnel. Si un utilisateur ne figure pas dans le groupe auquel sont attribuées les stratégies, ou s’il est dans un groupe exclu, il ne sera pas bloqué. La conformité est vérifiée uniquement pour les appareils des utilisateurs appartenant à un groupe attribué.

## <a name="noncompliant-device-is-not-blocked"></a>Un appareil non conforme n’est pas bloqué

Si vous constatez qu’un appareil continue à avoir un accès alors qu’il n’est pas conforme, procédez comme suit.
- Vérifiez vos groupes cibles et d’exclusion. Si un utilisateur n’est pas dans le bon groupe cible ou est dans le groupe d’exclusions, il n’est pas bloqué. Seuls les appareils des utilisateurs d’un groupe cible sont vérifiés pour la conformité.
- Assurez-vous que l’appareil est en cours de découverte. Le connecteur Exchange pointe-t-il sur la sécurité d’accès du code Exchange 2010 quand l’utilisateur est sur un serveur Exchange 2013 ? Dans ce cas, si la règle d’Exchange par défaut est Autoriser, même si l’utilisateur est dans le groupe cible, Intune ne peut pas savoir si l’appareil est connecté à Exchange.
- Vérifiez l’état Existence/accès de l’appareil dans Exchange :
  - Utilisez cette applet de commande PowerShell pour obtenir la liste de tous les appareils mobiles d’une boîte aux lettres : "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Si l’appareil n’est pas répertorié, cela signifie qu’il n’accède pas à Exchange.
  - S’il est dans la liste, utilisez l’applet de commande Get-CASmailbox -identity:’upn’ | fl pour obtenir des informations détaillées sur son état d’accès que vous fournirez au support Microsoft.

## <a name="next-steps"></a>Étapes suivantes
Si ces informations ne vous aident pas, vous pouvez également [obtenir du support technique pour Microsoft Intune](get-support.md).
