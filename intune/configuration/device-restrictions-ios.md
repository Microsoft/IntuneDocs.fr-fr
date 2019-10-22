---
title: Paramètres d’appareil iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur des appareils iOS pour restreindre les fonctionnalités, y compris définir des exigences de mot de passe, contrôler l’écran verrouillé, utiliser des applications intégrées, ajouter des applications restreintes ou approuvées, gérer des appareils Bluetooth, se connecter au cloud pour la sauvegarde et le stockage, activer le mode kiosque, ajouter des domaines, et contrôler la façon dont les utilisateurs interagissent avec le navigateur web Safari dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a26af380ef00c85c681beccdcdf188c343da1b94
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584886"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils iOS et iPadOS pour autoriser ou restreindre les fonctionnalités avec Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils iOS et iPadOS. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, définir des règles de mot de passe, autoriser ou restreindre des applications spécifiques, et bien d’autres opérations.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils iOS.

> [!TIP]
> Ces paramètres utilisent les paramètres MDM d’Apple. Pour plus d’informations sur ces paramètres, consultez [paramètres de gestion des appareils mobiles d’Apple](https://support.apple.com/guide/mdm/welcome/web) (pour ouvrir le site Web d’Apple).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration pour les restrictions appliquées aux appareils](../device-restrictions-configure.md).

> [!NOTE]
> Ces paramètres s’appliquent à différents types d’inscription, avec certains paramètres s’appliquant à toutes les options d’inscription. Pour plus d’informations sur les différents types d’inscription, consultez [inscription iOS](../ios-enroll.md).

## <a name="general"></a>Général

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Partager des données d’utilisation** : choisissez **Bloquer** pour empêcher l’appareil d’envoyer des données de diagnostic et d’utilisation à Apple. L’option (par défaut) **Non configuré** autorise l’envoi de ces données.

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil. Dans iOS 9,0 et versions ultérieures, il bloque également les enregistrements à l’écran. L’option (par défaut) **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran en tant qu’image ou vidéo.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Certificats TLS non approuvés** : choisissez l’option **Bloquer** pour empêcher les certificats Transport Layer Security (TLS) non autorisés sur l’appareil. L’option **Non configuré** (par défaut) autorise les certificats TLS.
- **Autoriser les mises à jour PKI à distance** : l’option **Autoriser** permet à vos utilisateurs de recevoir des mises à jour logicielles sans connecter leurs appareils à un ordinateur.
- **Limiter le suivi des publicités** : choisissez **Limiter** pour désactiver l’identificateur de publicités de l’appareil. **Non configuré** (par défaut) maintient l’activation de l’identificateur.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Modification des paramètres d’envoi des diagnostics** : l’option **Bloquer** empêche l’utilisateur de modifier les paramètres d’envoi des diagnostics et d’analyse des applications du volet **Diagnostics et utilisation** (paramètres de l’appareil). L’option (par défaut) **Non configuré**permet à l’utilisateur de modifier ces paramètres d’appareil.

  Pour utiliser ce paramètre, définissez le paramètre **partager les données d’utilisation** sur **bloquer**.

  Cette fonctionnalité s’applique à :  
  - iOS 9.3.2 et versions ultérieures

- **Observation de l’écran à distance avec l’application Classroom** : choisissez l’option **Bloquer** pour empêcher l’application Classroom d’observer à distance l’écran de l’appareil. L’option (par défaut) **Non configuré** autorise l’application Apple Classroom à afficher l’écran.

  Pour utiliser ce paramètre, définissez le paramètre de **capture d’écran** sur **bloquer**.

  Cette fonctionnalité s’applique à :  
  - iOS 9.3 et versions ultérieures

- **Observation des écrans sans invite par l’application En classe** : si cette option est définie sur **Autoriser**, les enseignants peuvent observer en mode silencieux l’écran des appareils iOS des étudiants qui n’en sont pas avertis à l’aide de l’application En classe. Les appareils des étudiants inscrits dans une classe et qui utilisent l’application Classroom accordent automatiquement une autorisation à l’enseignant de cette classe. **Non configuré** (par défaut) désactive cette fonctionnalité.

  Pour utiliser ce paramètre, définissez le paramètre de **capture d’écran** sur **bloquer**.

- **Approbation des applications d’entreprise** : choisissez **Bloquer** pour supprimer le bouton **Approuver Enterprise Developer** du menu Paramètres > Général > Profils et gestion des appareils sur l’appareil. L’option (par défaut) **Non configuré** permet à l’utilisateur de choisir de faire confiance aux applications qui n’ont pas été téléchargées sur l’App Store.
- **Modification de compte** : si cette option est définie sur **Bloquer**, l’utilisateur ne peut pas mettre à jour les paramètres spécifiques à l’appareil dans l’application Réglages d’iOS. Par exemple, l’utilisateur ne peut ni créer de nouveaux comptes d’appareils ni modifier le nom d’utilisateur ou le mot de passe. L’option (par défaut) **Non configuré** permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique également aux options accessibles à partir des applications iOS comme Mail, Contacts, Calendrier, Twitter, etc. Elle ne s’applique pas aux applications avec des paramètres de compte qui ne sont pas configurables à partir des applications iOS comme Microsoft Outlook.

- **Heure de l’écran** : choisissez **Bloquer** pour empêcher les utilisateurs de définir leurs propres restrictions concernant l’heure de l’écran (paramètres de l’appareil). L’option **Non configuré** permet à l’utilisateur de configurer des restrictions sur l’appareil (par exemple, le contrôle parental ou les restrictions liées au contenu et à la confidentialité).

  Ce paramètre s’appelait autrefois **Activation des restrictions dans les paramètres de l’appareil**. Impact de cette modification :  
  
  - iOS 11.4.1 et versions antérieures : **Bloquer** empêche les utilisateurs finaux de définir leurs propres restrictions dans les paramètres de l’appareil. Il s’agit du même comportement, et rien ne change pour les utilisateurs finaux.
  - iOS 12.0 et versions ultérieures : l’option **Bloquer** empêche les utilisateurs de définir leur propre **Heure de l’écran** dans les paramètres de l’appareil (Paramètres > Général > Heure de l’écran), notamment les restrictions de contenu et de confidentialité. Les appareils mis à niveau vers iOS 12.0 n’affichent plus l’onglet Restrictions dans les paramètres de l’appareil (Paramètres > Général > Gestion des appareils > Profil de gestion > Restrictions). Ces paramètres se trouvent dans **Heure de l’écran**.
  
- **Utiliser la réinitialisation de tous les paramètres et du contenu sur l’appareil** : choisissez **Bloquer** pour empêcher les utilisateurs d’utiliser l’option de réinitialisation de tout le contenu et de tous les paramètres sur l’appareil. L’option (par défaut) **Non configuré** permet aux utilisateurs d’accéder à ces paramètres.
- **Modification du nom de l’appareil** : choisissez **Bloquer** pour empêcher toute modification du nom de l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier le nom de l’appareil.
- **Modification des paramètres de notification** : choisissez **Bloquer** pour empêcher toute modification des paramètres de notification. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier les paramètres de notification de l’appareil.
- **Modification du papier peint** : choisissez **Bloquer** pour empêcher toute modification du papier peint. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier le fond d’écran de l’appareil.
- **Modification des paramètres d’approbation d’application d’entreprise** : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les paramètres d’approbation d’application d’entreprise sur les appareils supervisés. L’option (par défaut) **Non configuré** autorise l’utilisateur à faire confiance aux applications qui n’ont pas été téléchargées sur l’App Store.
- **Modifications au profil de configuration** : choisissez **Bloquer** pour empêcher l’utilisateur de modifier le profil de configuration sur l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à installer des profils de configuration.
- **Verrou d’activation** : choisissez **Autoriser** pour activer le verrou d’activation sur les appareils iOS supervisés. Le verrouillage d'activation rend plus difficile la réactivation d'un appareil perdu ou volé.
- **Bloquer la suppression d’applications** : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des applications. L’option (par défaut) **Non configuré** autorise les utilisateurs à supprimer des applications de l’appareil.
- **Bloque le mode USB restreint** : choisissez **Bloquer** pour désactiver le mode USB restreint sur les appareils supervisés. Le mode USB restreint empêche les accessoires USB d'échanger des données avec un appareil verrouillé depuis plus d'une heure. L’option **Non configuré** (par défaut) autorise le mode USB restreint.
- **Application de la date et de l’heure automatique** : **activez** cette option pour forcer les appareils supervisés à définir automatiquement la date et l’heure. Le fuseau horaire de l’appareil est mis à jour quand l’appareil se connecte à des réseaux cellulaires ou si les services de localisation ont été activés en mode Wi-Fi.
- **Require students to request permission to leave Classroom course** (Obliger les élèves à demander l’autorisation de quitter le cours Classroom) : **activez** cette option pour obliger les élèves inscrits à un cours non managé et qui utilisent l’app Classroom à demander à l’enseignant l’autorisation de quitter le cours. L’option (par défaut) **Non configuré** dispense les étudiants de demander une autorisation.

  Cette fonctionnalité s’applique à :  
  - iOS 11.3 et versions ultérieures

- **Autoriser Classroom à verrouiller une application et verrouiller l’appareil sans envoyer d’invite** : **Activer** permet aux enseignants de verrouiller les applications ou de verrouiller l’appareil à l’aide de l’application Classroom, sans en informer l’étudiant. Le verrouillage des applications signifie que l’appareil peut uniquement accéder aux applications qui ont été spécifiées par l’enseignant. **Non configuré** (par défaut) empêche les enseignants de verrouiller les applications ou les appareils à l’aide de l’application Classroom sans en informer l’étudiant.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Participer automatiquement aux cours Classroom sans envoyer d’invite** : **Activer** permet automatiquement aux étudiants de rejoindre un cours de l’application Classroom sans que l’enseignant ait à fournir son approbation. **Non configuré** (par défaut) demande à l’enseignant s’il souhaite autoriser les étudiants à rejoindre un cours dans l’application Classroom.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Bloquer la création de VPN** : l’option **Bloquer** empêche les utilisateurs de créer des paramètres de configuration VPN. L’option (par défaut) **Non configuré** permet aux utilisateurs de créer des VPN sur l’appareil.
- **Modification des paramètres eSIM** : l’option **Bloquer** empêche les utilisateurs de supprimer ou d’ajouter un forfait mobile pour l’eSIM de l’appareil. L’option (par défaut) **Non configuré** permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique à :  
  - iOS 12.1 et versions ultérieures

- **Différer les mises à jour logicielles** : lorsque cette option est définie sur **Non configuré** (par défaut), les mises à jour logicielles sont affichées sur l’appareil dès leur publication par Apple. Par exemple, si une mise à jour iOS est publiée par Apple à une date spécifique, cette mise à jour s’affiche automatiquement sur l’appareil autour de la date de publication.

  **Activer** vous permet de différer l’affichage des mises à jour logicielles sur les appareils (de 0 à 90 jours). Ce paramètre ne permet pas de contrôler à quel moment les mises à jour sont installées. 

  - **Retarde la visibilité des mises à jour logicielles** : entrez une valeur comprise entre 0 et 90 jours. Quand le délai expire, les utilisateurs reçoivent une notification de mise à jour vers la version la plus récente du système d’exploitation disponible au moment du déclenchement du délai.

    Par exemple, si la version iOS 12.a est disponible le **1er janvier**, et si le **délai de visibilité** est défini sur **5 jours**, iOS 12.a ne s’affichera pas comme étant disponible sur les appareils des utilisateurs finaux. En revanche, le **sixième jour** suivant la publication, la mise à jour est disponible et les utilisateurs finaux peuvent l’installer.

    Ce paramètre s’applique à :  
    - iOS 11.3 et versions ultérieures

## <a name="password"></a>Mot de passe

> [!NOTE]
> Dans une version ultérieure, ces paramètres de mot de passe dans l’interface utilisateur Intune sont mis à jour pour correspondre au type d’inscription.

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Mot de passe** : **Exige** que l’utilisateur final entre un mot de passe pour accéder à l’appareil. L’option **Non configuré** (par défaut) autorise les utilisateurs à accéder à l’appareil sans entrer un mot de passe.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

> [!IMPORTANT]
> Sur les appareils avec inscription des utilisateurs, si vous configurez un paramètre de mot de passe, le paramètre **Mots de passe simples** est automatiquement défini sur **Bloquer**, et un code confidentiel à 6 chiffres est appliqué.
>
> Par exemple, vous configurez le paramètre **Expiration du mot de passe** et envoyez cette stratégie aux appareils avec inscription des utilisateurs. Sur les appareils, les événements suivants se produisent :
>
> - Le paramètre **Expiration du mot de passe** est ignoré.
> - Les mots de passe simples comme `1111` ou `1234` ne sont pas autorisés.
> - Un code PIN à 6 chiffres est appliqué.

- **Mots de passe simples** : choisissez **Bloquer** pour exiger des mots de passe plus complexes. L’option **Non configuré** autorise les mots de passe simples comme `0000` et `1234`.

- **Type de mot de passe requis** : choisissez le type de mot de passe dont votre organisation a besoin. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Numérique**
  - **Alphanumérique**
- **Nombre de caractères non alphanumériques dans le mot de passe** : entrez le nombre de caractères de symbole, par exemple `#` ou `@`, devant être inclus dans le mot de passe.

- **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe qu’un utilisateur doit saisir (entre 4 et 14 caractères). Sur les appareils inscrits par l’utilisateur, entrez une longueur comprise entre 4 et 6 caractères.
  
  > [!NOTE]
  > Pour les appareils inscrits par l’utilisateur, les utilisateurs peuvent définir un code confidentiel supérieur à 6 chiffres. Mais pas plus de 6 chiffres sont appliqués sur l’appareil. Par exemple, un administrateur définit la longueur minimale sur `8`. Sur les appareils inscrits par l’utilisateur, les utilisateurs sont uniquement tenus de définir un code PIN à 6 chiffres. Intune ne force pas un code confidentiel supérieur à 6 chiffres sur les appareils inscrits par l’utilisateur.

- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil (entre 4 et 11).
  
  iOS offre une sécurité intégrée qui peut avoir un impact sur ce paramètre. Par exemple, iOS peut retarder le déclenchement de la stratégie en fonction du nombre d’échecs de connexion. Il peut également envisager d’entrer plusieurs fois le même code secret comme une seule tentative. Le [Guide de sécurité iOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) d’Apple (qui ouvre le site Web d’Apple) est une bonne ressource et fournit des détails plus spécifiques sur les codes secrets.
  
- **Nombre maximal de minutes après verrouillage de l’écran avant de demander un mot de passe**<sup>1</sup> : spécifiez la durée pendant laquelle l’appareil reste inactif avant que l’utilisateur doive entrer à nouveau son mot de passe. Si la durée que vous entrez est supérieure à celle actuellement définie sur l’appareil, celui-ci ignore la valeur saisie. Option prise en charge sur les appareils iOS 8.0 et versions ultérieures.
- **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil**<sup>1</sup> : entrez le nombre maximal de minutes d’inactivité autorisée sur l’appareil avant le verrouillage de l’écran. Si la durée que vous entrez est supérieure à celle actuellement définie sur l’appareil, celui-ci ignore la valeur saisie. Lorsque la valeur est définie sur **immédiatement**, l’écran se verrouille en fonction de la durée minimale de l’appareil. Sur iPhone, il est de 30 secondes. Sur iPad, il s’agit de deux minutes.
- **Expiration du mot de passe (jours)** : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil.
- **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe.
- **Touch ID et face ID Unlock**: choisissez **bloquer** pour empêcher l’utilisation d’une empreinte digitale ou d’un visage pour déverrouiller l’appareil. L’option **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide de ces méthodes.

  Le blocage de ce paramètre empêche également l’utilisation de l’authentification FaceID pour déverrouiller l’appareil.

  L’ID de face s’applique à :  
  - iOS 11.0 et versions ultérieures

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Modification du code secret** : choisissez **Bloquer** pour empêcher la modification, l’ajout ou la suppression du code secret. Les modifications apportées aux restrictions du code secret sont ignorées sur les appareils supervisés après le blocage de cette fonctionnalité. L’option (par défaut) **Non configuré** permet d’ajouter, modifier ou supprimer des codes secrets.

  - Modification de l’ID **tactile et du visage**: le **blocage** empêche l’utilisateur de modifier, d’ajouter ou de supprimer des empreintes digitales et des ID de face TouchID. L’option **Non configuré** (par défaut) autorise l’utilisateur à mettre à jour les empreintes digitales Touch ID et Face ID sur l’appareil.

    Le blocage de ce paramètre empêche également l’utilisateur de modifier, d’ajouter ou de supprimer l’authentification FaceID.

    L’ID de face s’applique à :  
    - iOS 11.0 et versions ultérieures

- **Bloquer le remplissage automatique des mots de passe** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sous iOS. L’option **Bloquer** a également les conséquences suivantes :

  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option (par défaut)**Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mots de passe de proximité** : choisissez **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils situés à proximité. L’option (par défaut) **Non configuré** autorise ces demandes de mots de passe.
- **Bloquer le partage de mots de passe** : choisissez **Bloquer** pour empêcher le partage de mots de passe entre les appareils avec AirDrop. L’option (par défaut) **Non configuré** autorise le partage de mots de passe.
- **Exiger une authentification Touch ID ou Face ID pour le remplissage automatique du mot de passe ou des informations de carte de crédit** : lorsque cette option est définie sur **Exiger**, les utilisateurs doivent s’authentifier à l’aide de TouchID ou de FaceID avant qu’un mot de passe ou des informations de carte de crédit ne puissent être automatiquement renseignés dans Safari et autres applications. **Non configuré** (par défaut) permet aux utilisateurs de contrôler cette fonctionnalité dans les paramètres de l’appareil.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures
  
<sup>1</sup> Lorsque vous configurez les paramètres **Nombre maximal de minutes d'inactivité avant le verrouillage de l'appareil** et **Nombre maximal de minutes entre le verrouillage de l'écran et la demande du mot de passe**, ceux-ci sont appliqués de manière séquentielle. Par exemple, si vous affectez aux deux paramètres une valeur de **5** minutes, l’écran s’éteint automatiquement après 5 minutes, et l’appareil se verrouille après 5 minutes de plus. Toutefois, si l'utilisateur désactive manuellement l'écran, le second paramètre est immédiatement appliqué. Dans le même exemple, une fois que l’utilisateur a désactivé l’écran, l’appareil se verrouille 5 minutes plus tard.

## <a name="locked-screen-experience"></a>Expérience d’écran verrouillé

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Accès au centre de contrôle quand l'appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’utilisateur d’accéder à l’application du centre de contrôle lorsque l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise les utilisateurs à accéder à l’application du centre de contrôle lorsque l’appareil est verrouillé.
- **Notifications lorsque l’appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’accès aux notifications quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisateur à accéder aux notifications sans déverrouiller l’appareil.
- **Vue Aujourd'hui lors du verrouillage de l’appareil** : choisissez **Bloquer** pour empêcher l’accès à la vue Aujourd'hui lorsque l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisateur à afficher la vue Aujourd'hui lorsque l’appareil est verrouillé.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Notifications de Wallet quand l’appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’accès à l’application Wallet quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisateur à accéder à l’application Wallet lorsque l’appareil est verrouillé.

## <a name="app-store-doc-viewing-gaming"></a>App Store, affichage de document, jeux

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Affichage de documents d’entreprise dans les applications non gérées** : choisissez **Bloquer** pour empêcher l’affichage de documents d’entreprise dans les applications non gérées. L’option **Non configuré** (par défaut) autorise l’affichage de documents d’entreprise depuis toute application. Par exemple, vous voulez empêcher les utilisateurs d’enregistrer des fichiers de OneDrive dans Dropbox. Attribuez la valeur **Bloquer** à ce paramètre. Une fois que l’appareil a reçu la stratégie (par exemple, après un redémarrage), il cesse d’autoriser l’enregistrement.

  - **Autoriser les applications non gérées à lire à partir des comptes de contacts gérés**: lorsque la valeur est définie sur **autoriser**, les applications non gérées, telles que l’application de contacts iOS intégrée, peuvent lire et accéder aux informations de contact à partir d’applications gérées, y compris l’application mobile Outlook. L’option **Non configuré** (par défaut) empêche la lecture, y compris la suppression des doublons, dans l’application Contacts intégrée sur l’appareil.  
  
    Ce paramètre autorise ou empêche la lecture des informations de contact. Il ne contrôle pas la synchronisation des contacts entre les applications.
  
    Pour utiliser ce paramètre, définissez le paramètre **Affichage des documents d’entreprise dans les applications non gérées**  sur **Bloquer**.

  Pour plus d’informations sur ces deux paramètres et leur impact sur Outlook pour la synchronisation d’exportation de contact iOS, consultez [le Conseil de support : utiliser des paramètres de profil personnalisés Intune avec l’application contacts natives iOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Traiter AirDrop comme une destination non gérée** : **activez** cette option pour forcer AirDrop à être considéré comme une cible de dépôt non gérée. Cette option empêche les applications gérées d’envoyer des données à l’aide via Airdrop. 
- **Affichage des documents autres que ceux d’entreprise dans les applications d’entreprise** : choisissez **Bloquer** pour empêcher l’affichage de documents autres que ceux de l’entreprise dans les applications d’entreprise. L’option **Non configuré** (par défaut) autorise tout document à être affiché dans les applications d’entreprise gérées.

  L’affectation de la valeur **Block** empêche également la synchronisation de l’exportation dans Outlook pour iOS. Pour plus d’informations, consultez le [Conseil de support : activation de la synchronisation des contacts Outlook iOS avec les contrôles MDM iOS12](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Exiger le mot de passe du magasin iTunes pour tous les achats**: **demander** à l’utilisateur d’entrer le mot de passe d’ID Apple pour chaque achat dans une application ou iTunes. **Non configuré** (par défaut) autorise les achats sans demander un mot de passe à chaque fois.
- **Achats dans l’application** : choisissez **Bloquer** pour empêcher les achats sur l’App Store dans l’application. L’option **Non configuré** (par défaut) autorise les achats au sein d’une application en cours d’exécution.
- **Télécharger du contenu de l'iBook Store indiqué comme étant de la « Littérature érotique »**  : choisissez **Bloquer** pour empêcher les utilisateurs de télécharger du contenu de l’iBook Store indiqué comme étant de la littérature érotique. L’option **Non configuré** (par défaut) autorise l’utilisateur à télécharger des livres de la catégorie « Littérature érotique ».
- **Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés**: lorsque la valeur est définie sur **autoriser**, les applications gérées, telles que l’application mobile Outlook, peuvent enregistrer ou synchroniser les informations de contact, y compris les contacts professionnels et d’entreprise, dans les contacts iOS intégrés. lancement. Lorsque la valeur **n’est pas configurée** (valeur par défaut), les applications gérées ne peuvent pas enregistrer ou synchroniser les informations de contact avec l’application contacts iOS intégrée sur l’appareil.
  
  Pour utiliser ce paramètre, définissez le paramètre **Affichage des documents d’entreprise dans les applications non gérées**  sur **Bloquer**.

- **Région des classifications** : choisissez la région des classifications que vous souhaitez utiliser pour les téléchargements autorisés. Puis choisissez les évaluations autorisées pour les catégories **Films**, **Émissions TV** et **Apps**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **App Store** : l’option **Bloquer** empêche l’accès à l’App Store sur les appareils supervisés. **Non configuré** (valeur par défaut) autorise l’accès.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

  - **Installation d’applications à partir de l’App Store** : choisissez **Bloquer** pour bloquer l’App Store à partir de l’écran d’accueil des appareils. Les utilisateurs finaux peuvent continuer à utiliser iTunes ou l’outil Apple Configurator pour installer des applications. L’option **Non configuré** (par défaut) permet d’accéder à l’App Store depuis l’écran d’accueil.
  - **Téléchargements automatiques des applications** : choisissez **Bloquer** pour empêcher le téléchargement automatique des applications achetées sur d’autres appareils. Cela n’affecte pas les mises à jour des applications existantes. L’option **Non configuré** (par défaut) autorise le téléchargement sur l’appareil des applications achetées sur d’autres appareils iOS.

- **Contenu iTunes explicite (musique, podcast ou actualités)** : choisissez **Bloquer** pour empêcher l’affichage de contenu explicite dans la musique, les podcasts ou les actualités iTunes. L’option **Non configuré** (par défaut) autorise l’appareil à accéder au contenu réservé aux adultes depuis le magasin. iOS 13 et versions ultérieures peuvent nécessiter uniquement des appareils supervisés. 

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

- **Ajout d’amis Game Center** : choisissez **Bloquer** pour empêcher les utilisateurs d’ajouter des amis Game Center. L’option **Non configuré** (par défaut) autorise l’utilisateur à ajouter des amis dans le Game Center.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

- **Game Center** :choisissez **Bloquer** pour empêcher l’utilisation de l’application Game Center. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application Game Center sur l’appareil.
- **Jeux multijoueur**: choisissez un **bloc** pour empêcher les jeux multijoueur. L’option **Non configuré** (par défaut) autorise l’utilisateur à jouer à des jeux multijoueur sur l’appareil.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

- **Accès à un lecteur réseau dans l’application fichiers**: à l’aide du protocole SMB (Server Message Block), les appareils peuvent accéder à des fichiers ou à d’autres ressources sur un serveur réseau. **Désactiver** empêche l’accès aux fichiers sur un lecteur SMB réseau. **Non configuré** (valeur par défaut) autorise l’accès.

  Cette fonctionnalité s’applique à :  
  - iOS et iPados 13,0 et versions ultérieures

## <a name="built-in-apps"></a>Applications intégrées

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Siri** : choisissez **Bloquer** pour empêcher l’accès à Siri. L’option **Non configuré** (par défaut) autorise l’utilisation de l’assistant vocal Siri sur l’appareil.
  - **Siri quand l’appareil est verrouillé** : choisissez **Bloquer** pour empêcher l’accès à Siri quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisation de l’assistant vocal Siri sur l’appareil verrouillé.

- **Avertissements en cas de fraude dans Safari**  : **activez** cette option pour forcer l’affichage des avertissements en cas de fraude dans le navigateur web de l’appareil. **Non configuré** (valeur par défaut) désactive cette fonctionnalité.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Recherche Spotlight pour renvoyer des résultats à partir d’Internet** : choisissez **Bloquer** pour empêcher Spotlight de renvoyer des résultats à partir d’une recherche sur Internet. L’option (par défaut)**Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.

- **Cookies dans Safari**  : choisissez la façon dont les cookies sont gérés sur l’appareil. Les options disponibles sont les suivantes :
  - Autoriser
  - Bloquer tous les cookies
  - Autoriser les cookies des sites web visités
  - Autoriser les cookies du site web actuel

- **JavaScript dans Safari** : choisissez **Bloquer** pour empêcher que les scripts Java dans le navigateur s’exécutent sur l’appareil. **Non configuré** (valeur par défaut) autorise les scripts Java.

- **Fenêtres publicitaires dans Safari**  : choisissez **Bloquer** pour désactiver le bloqueur de fenêtres publicitaires dans le navigateur web. **Non configuré** (valeur par défaut) autorise le bloqueur de fenêtres publicitaires.

- **Journalisation côté serveur pour les commandes Siri**: lorsque la valeur est définie sur **Disable**, la journalisation Siri côté serveur est désactivée. Cela peut également empêcher la journalisation des requêtes des utilisateurs sur les serveurs Siri. **Non configuré** (par défaut) enregistre les commandes Siri côté serveur. Ce paramètre ne dépend pas du paramètre Siri bloqué ou non configuré.

  Cette fonctionnalité s’applique à :  
  - iOS 12.2 et versions ultérieures

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option (par défaut)**Non configuré** autorise l’accès à l’appareil photo de l’appareil.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

  - **FaceTime** : choisissez **Bloquer** pour empêcher l’accès à l’application FaceTime. L’option **Non configuré** (par défaut) autorise l’accès à l’application FaceTime sur l’appareil.

    À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

- **Filtre d’obscénités de Siri** : **activez** cette option pour empêcher Siri de dicter ou d’employer un langage obscène.

  Pour utiliser ce paramètre, définissez le paramètre **Siri** sur **bloquer**.

- **Siri à consulter le contenu généré par les utilisateurs depuis Internet** : choisissez **Bloquer** pour empêcher Siri d’accéder aux sites web pour répondre aux questions. L’option **Non configuré** (par défaut) autorise Siri à accéder au contenu généré par les utilisateurs depuis Internet.

  Pour utiliser ce paramètre, définissez le paramètre **Siri** sur **bloquer**.

- **Apple News** : choisissez l’option **Bloquer** pour empêcher l’accès à l’application Apple News sur l’appareil. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application Apple News.
- **iBooks Store** :choisissez l’option **Bloquer** pour empêcher l’accès à l’iBooks Store. L’option **Non configuré** (par défaut) autorise les utilisateurs à parcourir l’iBooks Store et à y acheter des livres.
- **Application messages sur l’appareil**: **bloquer** empêche les utilisateurs d’utiliser l’application messages pour IMessage. Si l’appareil prend en charge la messagerie texte, l’utilisateur peut toujours envoyer et recevoir des messages texte à l’aide de SMS. **Non configuré** (par défaut) permet d’utiliser l’application messages pour envoyer et lire des messages sur Internet.
- **Podcasts** : choisissez l’option **Bloquer** pour empêcher l’utilisation de l’application Podcasts. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application Podcasts.
- **Service Music** : choisissez l’option **Bloquer** pour rétablir l’application Music en mode classique et désactiver le service Music. L’option (par défaut) **Non configuré** autorise l’utilisation du service Apple Music.
- **Service iTunes Radio** : choisissez **Bloquer** pour empêcher l’utilisation de l’application iTunes Radio. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application iTunes Radio.
- **iTunes Store**: **non configuré** (par défaut) autorise iTunes sur les appareils. **Bloquer** empêche les utilisateurs d’utiliser iTunes sur l’appareil. 

  Cette fonctionnalité s’applique à :  
  - iOS 4.0 et versions ultérieures

- **Rechercher mon iPhone**: **non configuré** (par défaut) permet d’utiliser cette fonctionnalité de recherche de l’application pour obtenir l’emplacement approximatif de l’appareil. **Bloquer** empêche cette fonctionnalité dans l’application Rechercher mon application. 

  Cette fonctionnalité s’applique à :  
  - iOS 13,0 et iPados 13,0 et versions ultérieures

- **Rechercher mes amis**: **non configuré** (par défaut) permet d’utiliser cette fonctionnalité de recherche de l’application pour trouver la famille et les amis d’un appareil Apple ou iCloud.com. **Bloquer** empêche cette fonctionnalité dans l’application Rechercher mon application.

  Cette fonctionnalité s’applique à :  
  - iOS 13,0 et iPados 13,0 et versions ultérieures

- **Modifications aux paramètres de l’application Localiser mes amis** : choisissez **Bloquer** pour empêcher toute modification des paramètres de l’application Localiser mes amis. L’option **Non configuré** (par défaut) autorise l’utilisateur à modifier les paramètres de l’application Localiser mes amis.

- **Recherche Spotlight pour renvoyer des résultats à partir d’Internet** : choisissez **Bloquer** pour empêcher Spotlight de renvoyer des résultats à partir d’une recherche sur Internet. L’option (par défaut)**Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.

- **Bloquer la suppression d’applications système de l’appareil** : choisissez **Bloquer** pour empêcher la suppression d’applications système de l’appareil. L’option **Non configuré** (par défaut) autorise les utilisateurs à supprimer des applications système.

- **Safari** : choisissez l’option **Bloquer** pour empêcher l’utilisation du navigateur Safari sur l’appareil. L’option **Non configuré** (par défaut) autorise l’utilisation du navigateur Safari.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

- **Remplissage automatique dans Safari** : l’option **Bloquer** désactive la fonctionnalité de remplissage automatique dans Safari sur l’appareil. L’option (par défaut) **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur web.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

## <a name="restricted-apps"></a>Applications restreintes

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Type de liste d’applications restreintes**: créez une liste d’applications que les utilisateurs ne sont pas autorisés à installer ou utiliser. Les options disponibles sont les suivantes :

  - **Non configuré** (valeur par défaut) : il n’existe aucune restriction d’Intune. Les utilisateurs ont accès aux applications que vous attribuez et aux applications intégrées.
  - **Applications interdites** : applications non gérées par Intune dont vous ne souhaitez pas qu’elles soient installées sur l’appareil. Les utilisateurs ne sont pas autorisés à installer une application interdite. Toutefois, si un utilisateur installe une application à partir de cette liste, il est signalé dans Intune.
  - **Applications approuvées** : applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement. Rien n’empêche les utilisateurs d’installer une application qui ne figure pas dans la liste approuvée. Mais dans le cas contraire, elle est signalée dans Intune.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** l’URL iTunes/App Store de l’application que vous souhaitez ajouter. Par exemple, pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- **Importez** un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Vous pouvez sinon **exporter** une liste existante comportant la liste des applications restreintes au même format.

> [!IMPORTANT]
> Les profils d’appareils qui utilisent les paramètres d’applications restreintes doivent être affectés à des groupes d’utilisateurs.

## <a name="show-or-hide-apps"></a>Afficher ou masquer des applications

S’applique aux appareils exécutant iOS 9,3 ou une version plus récente.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Type de liste d’applications**: créer une liste d’applications à afficher ou à masquer. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site Web d’Apple contient une liste d' [applications Apple intégrées](https://support.apple.com/HT208094). Les options disponibles sont les suivantes :

  - **Applications masquées** : spécifiez une liste d’applications masquée aux utilisateurs. Les utilisateurs ne peuvent ni afficher ni ouvrir ces applications.
  - **Applications visibles** : spécifiez une liste d’applications que les utilisateurs peuvent voir et lancer. Aucune autre application ne peut être affichée ou lancée.

- **URL**de l’application : entrez l’URL de l’application de stockage de l’application que vous souhaitez afficher ou masquer. Par exemple :

  - Pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - Pour ajouter l’application Microsoft Word, entrez `https://itunes.apple.com/de/app/microsoft-word/id586447913` ou `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.
  
  Pour plus d’informations sur la localisation d’un ID de Bundle, consultez [Comment trouver l’ID de Bundle pour une application iOS](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app).

- **Ajouter un ID d’ensemble d’applications** : entrez l’[ID d’ensemble d’applications](bundle-ids-built-in-ios-apps.md) de l’application. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site Web d’Apple contient une liste d' [applications Apple intégrées](https://support.apple.com/HT208094).
- **Nom de l’application** : entrez le nom de l’application. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site Web d’Apple contient une liste d' [applications Apple intégrées](https://support.apple.com/HT208094).
- **Éditeur** : entrez le nom de l’éditeur de l’application.

Pour ajouter des applications, vous pouvez :

- **Ajouter**: sélectionnez cette option pour créer votre liste d’applications.
- **Importez** un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Ou **Exporter** pour créer une liste des applications restreintes que vous avez ajoutées, au même format.

## <a name="wireless"></a>Sans fil

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Itinérance de données** : choisissez **Bloquer** pour empêcher l’itinérance de données sur le réseau cellulaire. L’option (par défaut) **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.
- **Récupération en arrière-plan globale en cas d'itinérance**  : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de récupération en arrière-plan globale lors de l’itinérance sur le réseau cellulaire. L’option (par défaut) **Non configuré** autorise l’appareil à récupérer des données comme les courriers électroniques lorsqu’il est en mode itinérance sur un réseau cellulaire.
- **Numérotation vocale** : choisissez **Bloquer** pour empêcher l’utilisation de la fonctionnalité de numérotation vocale sur l’appareil. L’option (par défaut) **Non configuré** autorise la numérotation vocale sur l’appareil.
- **Itinérance vocale** : choisissez **Bloquer** pour empêcher l’itinérance vocale sur le réseau cellulaire. L’option (par défaut) **Non configuré** autorise l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
- **Point d’accès personnel** : l’option **Bloquer** désactive le point d’accès personnel sur l’appareil de l’utilisateur à chaque synchronisation de l’appareil. Ce paramètre n’est peut-être pas compatible avec certains opérateurs. **Non configuré** (par défaut) conserve la configuration de point d’accès personnel comme la valeur par défaut définie par l’utilisateur.
- **Règles d’utilisation des données mobiles (applications gérées uniquement)** : définissez les types de données que les applications gérées peuvent utiliser sur les réseaux mobiles. Les options disponibles sont les suivantes :
  - **Bloquer l’utilisation de données cellulaires** : bloquez l’utilisation de données cellulaires pour **toutes les applications managées** ou **Choisir des applications spécifiques**.
  - **Bloquer l’utilisation de données cellulaires en itinérance** : bloquez l’utilisation de données cellulaires en itinérance pour **toutes les applications managées** ou **Choisir des applications spécifiques**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Modifications des paramètres d'utilisation des données cellulaires des applications** : choisissez **Bloquer** pour empêcher toute modification des paramètres d’utilisation des données cellulaires des applications. L’option (par défaut) **Non configuré** permet à l’utilisateur de contrôler quelles applications sont autorisées à utiliser les données cellulaires.
- **Changements des paramètres de forfait mobile** : l’option **Bloquer** empêche les utilisateurs de modifier les paramètres du forfait mobile. L’option**Non configuré** (par défaut) permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Modification par l’utilisateur d'** un point d’accès personnel : lorsqu’il est défini sur **bloquer**, l’utilisateur ne peut pas modifier le paramètre de hotspot personnel. **Non configuré** (par défaut) permet aux utilisateurs finaux d’activer ou de désactiver leur point d’accès personnel.

  Si vous bloquez ce paramètre et que vous bloquez le paramètre de **hotspot personnel** , le point d’accès personnel est désactivé.

  Cette fonctionnalité s’applique à :  
  - iOS 12.2 et versions ultérieures

- **Rejoindre uniquement les réseaux Wi-Fi utilisant des profils de configuration** : **activez** cette option pour forcer l’appareil à rejoindre uniquement les réseaux Wi-Fi configurés à l’aide d’un profil de configuration Intune. L’option (par défaut) **Non configuré** autorise l’appareil à utiliser d’autres réseaux Wi-Fi.
- **Wi-Fi toujours activé**: lorsque la valeur est **Required**, le Wi-Fi reste activé dans l’application Settings. Elle ne peut pas être désactivée dans paramètres ou dans le centre de contrôle, même lorsque l’appareil est en mode avion. **Non configuré** (par défaut) permet à l’utilisateur de contrôler l’activation ou la désactivation du Wi-Fi.

  La configuration de ce paramètre n’empêche pas les utilisateurs de sélectionner un réseau Wi-Fi.

  Cette fonctionnalité s’applique à :  
  - iOS et iPados 13,0 et versions ultérieures

## <a name="connected-devices"></a>Appareils connectés

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Détection du poignet pour une Apple Watch appairée** : **activez** cette option pour forcer une Apple Watch appairée à utiliser la détection du poignet. Si cette option est activée, l’Apple Watch n’affiche pas de notification si elle n’est pas portée. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Exiger un mot de passe associé pour les demandes AirPlay sortantes** : **nécessite** un mot de passe de jumelage lorsque l’utilisateur a recours à AirPlay pour diffuser le contenu vers d’autres appareils Apple. L’option (par défaut) **Non configuré** permet à l’utilisateur de diffuser en continu du contenu à l’aide d’AirPlay, sans entrer de mot de passe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **AirDrop** : choisissez l’option **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option (par défaut)**Non configuré** autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Apple Watch appariement**: **bloquer** empêche le jumelage avec une Apple Watch. L’option (par défaut) **Non configuré** autorise l’appairage avec une Apple Watch.
- **Modification Bluetooth** : **Bloquer** empêche l’utilisateur final de modifier les paramètres Bluetooth sur l’appareil. L’option (par défaut) **Non configuré** permet à l’utilisateur de modifier ces paramètres.
- **Appairage d’hôtes pour contrôler les appareils avec lesquels un appareil iOS peut s’appairer** : l’option (par défaut) **Non configuré** autorise l’appairage d’hôtes afin que l’administrateur puisse déterminer les appareils avec lesquels un appareil iOS peut s’appairer. L’option **Bloquer** empêche l’appairage d’hôtes.
- **Bloquer AirPrint** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité AirPrint sur l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisation d’AirPrint.
  - **Bloquer le stockage des informations d'identification AirPrint dans le trousseau** : choisissez **Bloquer** afin d’empêcher l’utilisation du stockage Trousseau pour le nom d’utilisateur et le mot de passe sur l’appareil. L’option (par défaut) **Non configuré** permet de stocker le nom d’utilisateur et le mot de passe AirPrint dans l’application Trousseau.
  - **Exiger un certificat TLS approuvé pour AirPrint** : **activez** cette option pour forcer l’appareil à utiliser des certificats approuvés pour la communication de l'impression TLS.
  - **Bloquer la découverte par iBeacon des imprimantes AirPrint** : choisissez **Bloquer** pour empêcher les balises AirPrint Bluetooth malveillantes de lancer des attaques d’hameçonnage sur le réseau. L’option (par défaut) **Non configuré** permet de publier des imprimantes AirPrint sur l’appareil.
- **Bloquer la configuration de nouveaux appareils à proximité** : l’option **Bloquer** désactive le message qui invite l’utilisateur à configurer de nouveaux appareils situés à proximité. **Non configuré** (par défaut) affiche des messages invitant l’utilisateur à connecter d’autres appareils Apple situés à proximité.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Accès aux fichiers sur un lecteur USB**: les périphériques peuvent se connecter et ouvrir des fichiers sur un lecteur USB. **Désactiver** empêche l’accès de l’appareil au lecteur USB dans l’application fichiers lorsqu’un périphérique USB est connecté à l’appareil. La désactivation de cette fonctionnalité empêche également les utilisateurs finaux de transférer des fichiers sur un lecteur USB connecté à un iPad. **Non configuré** (par défaut) autorise l’accès à un lecteur USB dans l’application fichiers.

  Cette fonctionnalité s’applique à :  
  - iOS et iPados 13,0 et versions ultérieures

## <a name="keyboard-and-dictionary"></a>Clavier et dictionnaire

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Recherche de définition de mot** : choisissez **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option (par défaut) **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Claviers prédictifs** : l’option **Non configuré** (par défaut) autorise l’utilisation de claviers prédictifs pour suggérer des mots que l’utilisateur pourrait vouloir utiliser. L’option **Bloquer** empêche cette fonctionnalité.
- **Correction automatique** : l’option **Non configuré** (par défaut) permet à l’appareil de corriger automatiquement les mots mal orthographiés. Choisissez **Bloquer** pour désactiver la correction automatique.
- **Vérification orthographique du clavier**: **non configuré** (par défaut) autorise l’utilisation du vérificateur d’orthographe sur l’appareil. Choisissez **Bloquer** pour désactiver le vérificateur d’orthographe.
- **Raccourcis clavier**: **non configuré** (par défaut) permet l’utilisation de raccourcis clavier sur l’appareil. Choisissez **Bloquer** pour empêcher l’utilisation des raccourcis clavier.
- **Dictée** : choisissez **Bloquer** pour empêcher l’utilisateur d’entrer du texte par dictée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.
- **QuickPath**: **non configuré** (valeur par défaut) permet aux utilisateurs d’utiliser QuickPath, ce qui permet une entrée continue sur le clavier de l’appareil. Les utilisateurs peuvent taper en balayant les clés pour créer des mots. **Bloquer** empêche les utilisateurs d’utiliser QuickPath. 

  Cette fonctionnalité s’applique à :  
  - iOS 13,0 et iPados 13,0 et versions ultérieures

## <a name="cloud-and-storage"></a>Cloud et stockage

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : tous les types d’inscription

- **Sauvegarde chiffrée** : **activez** cette option pour exiger le chiffrement des sauvegardes d’appareil.
- **Applications gérées synchronisées avec le cloud** : l’option **Non configuré** (par défaut) autorise les applications que vous gérez avec Intune à synchroniser les données sur le compte iCloud de l’utilisateur. Choisissez **Bloquer** pour empêcher cette synchronisation des données sur iCloud.
- **Bloquer la sauvegarde des livres d'entreprise** : choisissez **Bloquer** pour empêcher les utilisateurs de sauvegarder des livres d’entreprise. L’option **Non configuré** (par défaut) autorise les utilisateurs à sauvegarder ces livres.
- **Bloquer la synchronisation des métadonnées des livres d'entreprise (notes et mises en surbrillance)**  : choisissez **Bloquer** pour empêcher la synchronisation des notes et des mises en surbrillance dans les livres d’entreprise. **Non configuré** (valeur par défaut) autorise la synchronisation.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Synchronisation du flux de photos sur iCloud** : l’option **Non configuré** (par défaut) permet aux utilisateurs d’activer **Mon flux de photos** sur leur appareil afin de synchroniser les photos avec iCloud et de les mettre à la disposition de tous les appareils des utilisateurs. Choisissez **Bloquer** pour empêcher la synchronisation du flux de photos sur iCloud. Le blocage de cette fonctionnalité peut entraîner une perte de données. 
- **Photothèque iCloud** : choisissez **Bloquer** pour empêcher la photothèque iCloud de stocker des photos et vidéos dans le cloud. Toutes les photos qui ne sont pas entièrement téléchargées de la Photothèque iCloud sur l’appareil sont supprimées de l’appareil. L’option **Non configuré** (par défaut) autorise l’utilisation de la photothèque iCloud.
- **Flux de photos partagé** : choisissez **Bloquer** pour désactiver le **partage de photos iCloud** sur l'appareil. L’option **Non configuré** (par défaut) autorise la diffusion en continu des photos partagées.
- **Remise**: **non configuré** (par défaut) permet aux utilisateurs de commencer à travailler sur un appareil iOS, puis de poursuivre le travail qu’ils ont démarré sur un autre appareil iOS ou MacOS. Choisissez **Bloquer** pour désactiver cette fonctionnalité.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Sauvegarder sur iCloud** : l’option **Non configuré** (par défaut) autorise l’utilisateur à sauvegarder les données de l’appareil dans iCloud. Choisissez **Bloquer** pour empêcher l’utilisateur de sauvegarder les données de l’appareil dans iCloud.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

- **Bloquer la synchronisation de document iCloud** : l’option **Non configuré** (par défaut) autorise la synchronisation des documents et des clés-valeurs sur votre espace de stockage iCloud. Choisissez **Bloquer** pour empêcher iCloud de synchroniser les documents et des données.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

- **Bloquer la synchronisation du trousseau iCloud** : choisissez **Bloquer** pour désactiver la synchronisation des identifiants stockés dans le trousseau sur iCloud. L’option (par défaut) **Non configuré** autorise les utilisateurs à synchroniser ces identifiants.

  À compter d’iOS 13,0, ce paramètre nécessite des appareils supervisés.

## <a name="autonomous-single-app-mode"></a>Mode Application unique autonome

Utilisez ces paramètres pour configurer les appareils iOS pour qu’ils exécutent des applications spécifiques en mode Application unique autonome. Quand ce mode est configuré et que l’application est exécutée, l’appareil est verrouillé. Il peut uniquement exécuter cette application. Par exemple, ajoutez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Une fois les actions de l’application terminées, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Nom de l’application** : entrez le nom de l’application.
- **Ajouter un ID d’ensemble d’applications** : entrez l’[ID d’ensemble d’applications](bundle-ids-built-in-ios-apps.md) de l’application.
- **Ajouter**: sélectionnez cette option pour créer votre liste d’applications.

Vous pouvez également **importer** un fichier CSV contenant la liste des noms d’application et leur ID d’ensemble. Ou, **exporter** une liste existante incluant les applications.

## <a name="kiosk"></a>Kiosk

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Application à exécuter en mode plein écran** : choisissez le type d’applications que vous souhaitez exécuter en mode plein écran. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : les paramètres Kiosque ne sont pas appliqués. L’appareil ne s’exécute pas en mode Kiosque.
  - **App Store** : entrez l’URL d’une application de l’App Store d’iTunes.
  - **Application gérée** : choisissez une application que vous avez ajoutée à Intune.
  - **Application intégrée** : entrez l’[ID d’ensemble](bundle-ids-built-in-ios-apps.md) de l’application intégrée.

- **Assistance tactile** : cette option **nécessite** le paramètre d’accessibilité Assistance tactile sur l’appareil. Cette fonctionnalité aide les utilisateurs à effectuer des gestes à l’écran qui peuvent être difficiles à réaliser pour eux. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Inverser les couleurs** : **activez** le paramètre d’accessibilité Inverser les couleurs pour permettre aux utilisateurs ayant des troubles visuels d’ajuster l’affichage. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Audio mono** : cette option **nécessite** le paramètre d’accessibilité Audio mono sur l’appareil. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Contrôle vocal**: **exige** active le contrôle vocal sur l’appareil et permet aux utilisateurs de contrôler entièrement le système d’exploitation à l’aide des commandes Siri. **Non configuré** désactive le contrôle vocal sur l’appareil.

  Ce paramètre s’applique à :  
  - iOS 13.0 et ultérieur
  - iPadOS 13.0 et ultérieur
  
  > [!TIP]
  > Si vous disposez d’applications LOB pour votre organisation et qu’elles ne sont **pas prêtes** à être configurées le jour 0 quand iOS 13,0 est publié, nous vous recommandons de conserver ce paramètre **non configuré**.

- **VoiceOver** : cette option **nécessite** le paramètre d’accessibilité VoiceOver sur l’appareil pour lire à voix haute le texte à l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Zoom** : cette option **nécessite** le paramètre d’accessibilité Zoom sur l’appareil pour effectuer un zoom avant à l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Verrouillage automatique**: **blocage** empêche le verrouillage automatique de l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Fonction de sonnerie** : **bloquer** active ou désactive le commutateur de sonnerie (désactivation du son) sur l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Rotation d’écran** : **bloquer** empêche la modification de l’orientation de l’écran lorsque l’utilisateur fait pivoter l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Bouton de mise en veille de l’écran** : choisissez **Bloquer** pour désactiver le bouton Veille/sortie de veille de l’écran sur l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Tactile** : choisissez **Bloquer** pour désactiver l'écran tactile sur l'appareil. L’option **Non configuré** permet l’utilisation de l’écran tactile.
- **Boutons de volume**: **bloquer** empêche l’utilisation des boutons de volume sur l’appareil. **Non configuré** autorise les boutons de volume.
- **Commande d’assistance tactile** : **autoriser** l’utilisation de la fonction d’assistance tactile. L’option **Non configuré** désactive cette fonctionnalité.
- **Réglages de couleurs inversées** : **Autoriser** les réglages de couleurs inversées pour permettre aux utilisateurs d’ajuster la fonction de couleurs inversées. L’option **Non configuré** désactive cette fonctionnalité.
- **Lire le texte sélectionné** : **autoriser** les paramètres d’accessibilité Sélection Speak sur l’appareil. Cette fonctionnalité lit à voix haute le texte que l’utilisateur sélectionne. L’option **Non configuré** désactive cette fonctionnalité.
- **Modification du contrôle vocal**: **permet** aux utilisateurs de modifier l’état du contrôle vocal sur leurs appareils. **Non configuré** empêche les utilisateurs de modifier l’état du contrôle vocal sur leurs appareils.

  Ce paramètre s’applique à :  
  - iOS 13.0 et ultérieur
  - iPadOS 13.0 et ultérieur

- **Contrôle de VoiceOver** : **autoriser** les modifications VoiceOver pour permettre aux utilisateurs de mettre à jour la fonction VoiceOver, notamment la vitesse de lecture à voix haute du texte à l’écran. L’option **Non configuré** empêche toute modification de VoiceOver.
- **Réglage du zoom** : **autoriser** l’utilisateur à régler le zoom. L’option **Non configuré** empêche toute modification du zoom.

> [!NOTE]
> Avant de pouvoir configurer un appareil iOS pour le mode plein écran, vous devez utiliser l’outil Apple Configurator ou le Programme d’inscription des appareils Apple pour mettre l’appareil en mode supervisé. Consultez le guide Apple sur l’utilisation de l’outil Apple Configurator.
> Si l’application iOS que vous spécifiez est installée après l’attribution du profil, l’appareil ne bascule en mode plein écran qu’après son redémarrage.

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription de l’appareil, inscription automatique des appareils (supervisé)

- **Domaines d’e-mail non marqués** > **URL de domaine d’e-mail** : ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs finaux reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez saisis, l’e-mail est marqué comme non approuvé dans l’application iOS Mail.

- **Domaines web gérés** > **URL de domaine web** : ajoutez une ou plusieurs URL à la liste. Les documents téléchargés à partir des domaines que vous saisissez sont considérés comme gérés. Ce paramètre s’applique uniquement aux documents téléchargés à l’aide du navigateur Safari.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : inscription automatique des appareils (supervisé)

- **Domaines de remplissage automatique des mots de passe Safari (en mode supervisé uniquement)**  > **URL de domaine** : ajoutez une ou plusieurs URL à la liste. Les utilisateurs peuvent uniquement enregistrer les mots de passe web à partir des URL de cette liste. Ce paramètre s’applique uniquement au navigateur Safari et aux appareils en mode supervisé. Si vous n’entrez aucune URL, les mots de passe peuvent être enregistrés à partir de tous les sites web.

  Ce paramètre s’applique à :  
  - iOS 9.3 et versions ultérieures

## <a name="settings-that-require-supervised-mode"></a>Paramètres qui nécessitent le mode supervisé

Vous pouvez activer le mode supervisé iOS seulement pendant l’installation initiale de l’appareil par le biais du programme DEP d’Apple ou d’Apple Configurator. Une fois le mode supervisé activé, Intune peut configurer un appareil avec les fonctionnalités suivantes :

- Verrouillage d’application (Mode Application unique) 
- Proxy HTTP global 
- Ignorer le verrouillage d’activation 
- Mode Application unique autonome 
- Filtrage de contenu web 
- Définition de l’écran d’arrière-plan et de verrouillage 
- Envoi (push) d’application en mode silencieux 
- VPN AlwaysOn 
- Autoriser l’installation d’applications gérées exclusivement 
- iBookstore 
- iMessages 
- Centre de jeux 
- AirDrop 
- AirPlay 
- Appairage d’hôtes 
- Synchronisation cloud 
- Recherche Spotlight 
- Handoff 
- Effacer l’appareil 
- Interface utilisateur - Restrictions 
- Installation de profils de configuration par l’interface utilisateur 
- Actualités 
- Raccourcis clavier 
- Modifications du code secret 
- Changements du nom de l’appareil 
- Téléchargements automatiques d’applications 
- Changements apportés à l’approbation d’applications d’entreprise 
- Apple Music 
- Mail Drop 
- Appairage avec Apple Watch 

> [!NOTE]
> Apple a confirmé que certains paramètres passeront en mode supervisé uniquement en 2019. Nous vous recommandons de prendre ceci en considération lors de l’utilisation de ces paramètres. Plutôt qu’attendre qu’ils soient migrés en mode supervisé uniquement par Apple :
>
> - Installation de l’application par les utilisateurs finaux
> - Suppression d’applications
> - FaceTime
> - Safari
> - iTunes
> - Contenu explicite
> - Documents et données iCloud
> - Jeux multijoueur
> - Ajouter des amis du centre de jeux
> - Siri

## <a name="next-steps"></a>Étapes suivantes

[Attribuer le profil](../device-profile-assign.md) et [suivre son état](../device-profile-monitor.md).

Vous pouvez également appliquer des restrictions sur les fonctionnalités ou les paramètres des appareils [macOS](device-restrictions-macos.md).
