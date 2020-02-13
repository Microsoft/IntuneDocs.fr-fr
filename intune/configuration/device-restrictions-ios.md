---
title: Paramètres d’appareil iOS dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Ajoutez, configurez ou créez des paramètres sur des appareils iOS pour restreindre les fonctionnalités, y compris définir des exigences de mot de passe, contrôler l’écran verrouillé, utiliser des applications intégrées, ajouter des applications restreintes ou approuvées, gérer des appareils Bluetooth, se connecter au cloud pour la sauvegarde et le stockage, activer le mode kiosque, ajouter des domaines, et contrôler la façon dont les utilisateurs interagissent avec le navigateur web Safari dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/04/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dc252068d963d75bf6ade79852d6ba01bda8800b
ms.sourcegitcommit: 9b29478f815e10c46c8030abe0146d601ce0e28c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051607"
---
# <a name="ios-and-ipados-device-settings-to-allow-or-restrict-features-using-intune"></a>Paramètres des appareils iOS et iPadOS pour autoriser ou restreindre les fonctionnalités avec Intune

Cet article liste et décrit les différents paramètres que vous pouvez contrôler sur les appareils iOS et iPadOS. Dans votre solution de gestion des appareils mobiles (MDM), utilisez ces paramètres pour autoriser ou désactiver certaines fonctionnalités, définir des règles de mot de passe, autoriser ou restreindre des applications spécifiques, et bien d’autres opérations.

Ces paramètres sont ajoutés à un profil de configuration d’appareil dans Intune, puis affectés ou déployés sur vos appareils iOS.

> [!TIP]
> Ces paramètres utilisent les paramètres MDM d’Apple. Pour plus d’informations sur ces paramètres, consultez [Réglages de la gestion des appareils mobiles d’Apple](https://support.apple.com/guide/mdm/welcome/web) (ouvre le site web d’Apple).

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration pour les restrictions appliquées aux appareils](../device-restrictions-configure.md).

> [!NOTE]
> Ces paramètres s’appliquent à différents types d’inscriptions, certains d’entre eux s’appliquant à toutes les options d’inscription. Pour plus d’informations sur les différents types d’inscriptions, consultez [Inscription iOS](../ios-enroll.md).

## <a name="general"></a>Général

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Partager les données d’utilisation** : choisissez **Bloquer** pour empêcher l’appareil d’envoyer des données de diagnostic et d’utilisation à Apple. L’option (par défaut) **Non configuré** autorise l’envoi de ces données.

- **Capture d’écran** : choisissez **Bloquer** pour empêcher les captures d’écran sur l’appareil. Dans iOS 9.0 et ultérieur, cette option bloque également les enregistrements à l’écran. L’option (par défaut) **Non configuré** autorise l’utilisateur à capturer le contenu de l’écran en tant qu’image ou vidéo.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Certificats TLS non approuvés** : choisissez l’option **Bloquer** pour empêcher l’utilisation de certificats TLS (Transport Layer Security) non autorisés sur l’appareil. L’option **Non configuré** (par défaut) autorise les certificats TLS.
- **Bloquer les mises à jour PKI à distance** : **Bloquer** empêche vos utilisateurs de recevoir des mises à jour de logiciel, sauf si l’appareil est connecté à un ordinateur. **Non configuré** (par défaut) : permet à un appareil de recevoir des mises à jour de logiciel sans être connecté à un ordinateur.
- **Limiter le suivi des publicités** : choisissez **Limiter** pour désactiver l’identificateur de publicité d’appareil. **Non configuré** (par défaut) maintient l’activation de l’identificateur.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Modification des paramètres d'envoi des diagnostics** : l’option **Bloquer** empêche l’utilisateur de modifier les paramètres d’envoi des diagnostics et d’analytique des applications du volet **Diagnostics et utilisation** (paramètres de l’appareil). L’option (par défaut) **Non configuré**permet à l’utilisateur de modifier ces paramètres d’appareil.

  Pour utiliser ce paramètre, affectez au paramètre **Partager les données d’utilisation** la valeur **Bloquer**.

  Cette fonctionnalité s’applique à :  
  - iOS 9.3.2 et versions ultérieures

- **Bloquer l’observation des écrans à distance par l’application Classroom** : choisissez l’option **Bloquer** pour empêcher l’application Classroom d’observer à distance l’écran de l’appareil. L’option (par défaut) **Non configuré** autorise l’application Apple Classroom à afficher l’écran.

  Pour utiliser ce paramètre, affectez au paramètre **Capture d’écran** la valeur **Bloquer**.

  Cette fonctionnalité s’applique à :  
  - iOS 9.3 et versions ultérieures

- **Observation des écrans sans invite par l'application Classroom** : si cette option est définie sur **Autoriser**, les enseignants peuvent observer l’écran des appareils iOS des étudiants qui utilisent l’application Classroom, sans que les étudiants en soient avertis. Les appareils des étudiants inscrits dans une classe et qui utilisent l’application Classroom accordent automatiquement une autorisation à l’enseignant de cette classe. **Non configuré** (par défaut) désactive cette fonctionnalité.

  Pour utiliser ce paramètre, affectez au paramètre **Capture d’écran** la valeur **Bloquer**.

- **Approbation d’applications d’entreprise** : choisissez l’option **Bloquer** pour supprimer le bouton **Approuver Enterprise Developer** du menu Paramètres > Général > Profils et gestion des appareils sur l’appareil. L’option (par défaut) **Non configuré** permet à l’utilisateur de choisir de faire confiance aux applications qui n’ont pas été téléchargées sur l’App Store.
- **Modification de compte** : choisissez l’option **Bloquer** pour empêcher l’utilisateur de mettre à jour les paramètres de l’appareil dans l’application Réglages d’iOS. Par exemple, l’utilisateur ne peut ni créer de nouveaux comptes d’appareils ni modifier le nom d’utilisateur ou le mot de passe. L’option (par défaut) **Non configuré** permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique également aux options accessibles à partir des applications iOS comme Mail, Contacts, Calendrier, Twitter, etc. Elle ne s’applique pas aux applications avec des paramètres de compte qui ne sont pas configurables à partir des applications iOS comme Microsoft Outlook.

- **Heure de l’écran** : choisissez **Bloquer** pour empêcher les utilisateurs de définir leurs propres restrictions concernant l’heure de l’écran (paramètres de l’appareil). L’option **Non configuré** permet à l’utilisateur de configurer des restrictions sur l’appareil (par exemple, le contrôle parental ou les restrictions liées au contenu et à la confidentialité).

  Ce paramètre s’appelait autrefois **Activation des restrictions dans les paramètres de l’appareil**. Impact de cette modification :  
  
  - iOS 11.4.1 et antérieur : **Bloquer** empêche les utilisateurs finaux de définir leurs propres restrictions dans les paramètres de l’appareil. Il s’agit du même comportement, et rien ne change pour les utilisateurs finaux.
  - iOS 12.0 et versions ultérieures : l’option **Bloquer** empêche les utilisateurs de définir leur propre **Heure de l’écran** dans les paramètres de l’appareil (Paramètres > Général > Heure de l’écran), notamment les restrictions de contenu et de confidentialité. Les appareils mis à niveau vers iOS 12.0 n’affichent plus l’onglet Restrictions dans les paramètres de l’appareil (Paramètres > Général > Gestion des appareils > Profil de gestion > Restrictions). Ces paramètres se trouvent dans **Heure de l’écran**.
  
- **Utilisation de l’option d’effacement de tout le contenu et de toutes les options sur l’appareil** : choisissez **Bloquer** pour empêcher les utilisateurs de sélectionner l’option permettant d’effacer tout le contenu et tous les paramètres sur l’appareil. L’option (par défaut) **Non configuré** permet aux utilisateurs d’accéder à ces paramètres.
- **Modification du nom de l’appareil** : choisissez **Bloquer** pour empêcher l’utilisateur de changer le nom de l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier le nom de l’appareil.
- **Modification des paramètres de notification** : choisissez **Bloquer** pour empêcher l’utilisateur de modifier les paramètres de notification. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier les paramètres de notification de l’appareil.
- **Modification du papier peint** : choisissez **Bloquer** pour empêcher l’utilisateur de modifier le papier peint. L’option (par défaut) **Non configuré** autorise l’utilisateur à modifier le fond d’écran de l’appareil.
- **Modification des paramètres d'approbation des applications d'entreprise** : choisissez **Bloquer** pour empêcher les utilisateurs de modifier les paramètres d’approbation des applications d’entreprise sur les appareils supervisés. L’option (par défaut) **Non configuré** autorise l’utilisateur à faire confiance aux applications qui n’ont pas été téléchargées sur l’App Store.
- **Modifications du profil de configuration** : choisissez **Bloquer** pour empêcher l’utilisateur de modifier le profil de configuration de l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisateur à installer des profils de configuration.
- **Verrou d'activation** : choisissez **Autoriser** pour activer le verrou d’activation sur les appareils iOS supervisés. Le verrouillage d'activation rend plus difficile la réactivation d'un appareil perdu ou volé.
- **Bloquer la suppression des applications** : choisissez **Bloquer** pour empêcher les utilisateurs de supprimer des applications. L’option (par défaut) **Non configuré** autorise les utilisateurs à supprimer des applications de l’appareil.
- **Autoriser les accessoires USB quand l'appareil est verrouillé** : **Autoriser** permet aux accessoires USB d’échanger des données avec un appareil qui a été verrouillé pendant plus d’une heure. **Non configuré** (par défaut) ne met pas à jour le mode restreint USB sur l’appareil et les accessoires USB ne peuvent pas transférer les données de l’appareil s’ils sont verrouillés pendant plus d’une heure.
- **Forcer la définition automatique de la date et de l’heure** : choisissez l’option **Exiger** pour forcer les appareils supervisés à définir automatiquement la date et l’heure. Le fuseau horaire de l’appareil est mis à jour quand l’appareil se connecte à des réseaux cellulaires ou si les services de localisation ont été activés en mode Wi-Fi.
- **Exiger que les élèves demandent une autorisation pour quitter un cours Classroom** : choisissez l’option **Exiger** pour obliger les étudiants inscrits à un cours non géré dans l’application Classroom à demander à l’enseignant l’autorisation de quitter le cours. L’option (par défaut) **Non configuré** dispense les étudiants de demander une autorisation.

  Cette fonctionnalité s’applique à :  
  - iOS 11.3 et versions ultérieures

- **Autoriser Classroom à verrouiller une application et à verrouiller l’appareil sans invite** : **Activer** permet aux enseignants de verrouiller les applications ou de verrouiller l’appareil à l’aide de l’application Classroom, sans en informer l’étudiant. Le verrouillage des applications signifie que l’appareil peut uniquement accéder aux applications qui ont été spécifiées par l’enseignant. **Non configuré** (par défaut) empêche les enseignants de verrouiller les applications ou les appareils à l’aide de l’application Classroom sans en informer l’étudiant.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Participer automatiquement aux cours Classroom sans envoyer d’invite** : **Activer** permet automatiquement aux étudiants de rejoindre un cours de l’application Classroom sans que l’enseignant ait à fournir son approbation. **Non configuré** (par défaut) demande à l’enseignant s’il souhaite autoriser les étudiants à rejoindre un cours dans l’application Classroom.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Bloquer la création de VPN** : choisissez l’option **Bloquer** pour empêcher les utilisateurs de créer des paramètres de configuration VPN. L’option (par défaut) **Non configuré** permet aux utilisateurs de créer des VPN sur l’appareil.
- **Modification des paramètres eSIM** : l’option **Bloquer** empêche les utilisateurs de supprimer ou d’ajouter un forfait mobile pour l’eSIM de l’appareil. L’option (par défaut) **Non configuré** permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique à :  
  - iOS 12.1 et versions ultérieures

- **Différer les mises à jour logicielles** : lorsque cette option est définie sur **Non configuré** (par défaut), les mises à jour logicielles sont affichées sur l’appareil dès leur publication par Apple. Par exemple, si une mise à jour iOS est publiée par Apple à une date spécifique, cette mise à jour s’affiche automatiquement sur l’appareil autour de la date de publication.

  **Activer** vous permet de différer l’affichage des mises à jour logicielles sur les appareils (de 0 à 90 jours). Ce paramètre ne permet pas de contrôler à quel moment les mises à jour sont installées. 

  - **Retarde la visibilité des mises à jour logicielles** : entrez une valeur comprise entre 0 et 90 jours. Quand le délai expire, les utilisateurs reçoivent une notification de mise à jour vers la version la plus récente du système d’exploitation disponible au moment du déclenchement du délai.

    Par exemple, si la version iOS 12.a est disponible le **1er janvier**, et si le **délai de visibilité** est défini sur **5 jours**, iOS 12.a ne s’affichera pas comme étant disponible sur les appareils des utilisateurs finaux. En revanche, le **sixième jour** suivant la publication, la mise à jour est disponible et les utilisateurs finaux peuvent l’installer.

    Ce paramètre s’applique à :  
    - iOS 11.3 et versions ultérieures

## <a name="password"></a>Mot de passe

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Mot de passe** : **Demande** à l’utilisateur final de saisir un mot de passe pour pouvoir accéder à l’appareil. L’option **Non configuré** (par défaut) autorise les utilisateurs à accéder à l’appareil sans entrer un mot de passe.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

> [!IMPORTANT]
> Sur les appareils avec inscription des utilisateurs, si vous configurez un paramètre de mot de passe, le paramètre **Mots de passe simples** est automatiquement défini sur **Bloquer**, et un code confidentiel à 6 chiffres est appliqué.
>
> Par exemple, vous configurez le paramètre **Expiration du mot de passe** et envoyez cette stratégie aux appareils avec inscription des utilisateurs. Sur les appareils, les événements suivants se produisent :
>
> - Le paramètre **Expiration du mot de passe** est ignoré.
> - Les mots de passe simples comme `1111` ou `1234` ne sont pas autorisés.
> - Un code PIN à 6 chiffres est appliqué.

- **Mots de passe simples** : choisissez l’option **Bloquer** pour exiger des mots de passe plus complexes. L’option **Non configuré** autorise les mots de passe simples comme `0000` et `1234`.

- **Type de mot de passe requis** : choisissez le type de mot de passe exigé par votre organisation. Les options disponibles sont les suivantes :
  - **Paramètre par défaut de l’appareil**
  - **Numérique**
  - **Alphanumérique**
- **Nombre de caractères non alphanumériques dans le mot de passe** : entrez le nombre de caractères de symbole, par exemple `#` ou `@`, devant être inclus dans le mot de passe.

- **Longueur minimale du mot de passe** : entrez la longueur minimale du mot de passe qu’un utilisateur doit entrer (entre 4 et 14 caractères). Sur les appareils inscrits par l’utilisateur, entrez une longueur comprise entre 4 et 6 caractères.
  
  > [!NOTE]
  > Pour les appareils inscrits par l’utilisateur, les utilisateurs peuvent définir un code PIN supérieur à 6 chiffres. Toutefois, 6 chiffres au maximum sont appliqués sur l’appareil. Par exemple, un administrateur définit la longueur minimale sur `8`. Sur les appareils inscrits par l’utilisateur, les utilisateurs sont uniquement tenus de définir un code PIN à 6 chiffres. Intune n’exige pas un code PIN supérieur à 6 chiffres sur les appareils inscrits par l’utilisateur.

- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : spécifie le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil (entre 4 et 11).
  
  iOS offre une sécurité intégrée qui peut avoir un impact sur ce paramètre. Par exemple, iOS peut retarder le déclenchement de la stratégie en fonction du nombre d’échecs de connexion. Il peut également considérer plusieurs saisies du même code secret comme une seule tentative. Le [guide de sécurité iOS](https://www.apple.com/business/site/docs/iOS_Security_Guide.pdf) d’Apple (ouvre le site web d’Apple) est une bonne ressource et fournit des détails plus spécifiques sur les codes secrets.
  
- **Nombre maximal de minutes entre le verrouillage de l’écran et la demande du mot de passe**<sup>1</sup> : entrez la durée d’inactivité de l’appareil au bout de laquelle l’utilisateur doit entrer à nouveau le mot de passe. Si la durée que vous entrez est supérieure à celle actuellement définie sur l’appareil, celui-ci ignore la valeur saisie. Option prise en charge sur les appareils iOS 8.0 et versions ultérieures.

- **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil**<sup>1</sup> : entrez le nombre maximal de minutes d’inactivité autorisées sur l’appareil avant le verrouillage de l’écran.

  **Options iOS** :  

  - **Non configuré** (par défaut) : Intune ne touche pas à ce paramètre.
  - **Immédiatement** : Verrouillage de l’écran après 30 secondes d’inactivité.
  - **1** : Verrouillage de l’écran après 1 minute d’inactivité.
  - **2** : Verrouillage de l’écran après 2 minutes d’inactivité.
  - **3** : Verrouillage de l’écran après 3 minutes d’inactivité.
  - **4** : Verrouillage de l’écran après 4 minutes d’inactivité.
  - **5** : Verrouillage de l’écran après 5 minutes d’inactivité.
    
  **Options iPadOS** :  

  - **Non configuré** (par défaut) : Intune ne touche pas à ce paramètre.
  - **Immédiatement** : Verrouillage de l’écran après 2 minutes d’inactivité.
  - **2** : Verrouillage de l’écran après 2 minutes d’inactivité.
  - **5** : Verrouillage de l’écran après 5 minutes d’inactivité.
  - **10** : Verrouillage de l’écran après 10 minutes d’inactivité.
  - **15** : Verrouillage de l’écran après 15 minutes d’inactivité.

  Si une valeur ne s’applique pas à iOS ni iPadOS, Apple utilise la valeur *la plus faible* la plus proche. Par exemple, si vous entrez `4` minutes, les appareils iPadOS utilisent `2` minutes. Si vous entrez `10` minutes, les appareils iOS utilisent `5` minutes. Il s’agit d’une limitation d’Apple.
  
  > [!NOTE]
  > L’interface utilisateur Intune pour ce paramètre ne sépare pas les valeurs iOS et iPadOS prises en charge. L’interface utilisateur peut être mise à jour dans une version ultérieure.

- **Expiration du mot de passe (en jours)** : entrez le nombre de jours après lesquels l’utilisateur doit changer le mot de passe de l’appareil.
- **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe.
- **Déverrouillage de Touch ID et Face ID** : Choisissez l’option **Bloquer** pour empêcher l’utilisateur de déverrouiller l’appareil avec une empreinte digitale ou son visage. L’option **Non configuré** autorise l’utilisateur à déverrouiller l’appareil à l’aide de ces méthodes.

  Le blocage de ce paramètre empêche également l’utilisation de l’authentification FaceID pour déverrouiller l’appareil.

  Face ID s’applique à :  
  - iOS 11.0 et versions ultérieures

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Modification du code secret** : choisissez l’option **Bloquer** pour empêcher la modification, l’ajout ou la suppression du code secret. Les modifications apportées aux restrictions du code secret sont ignorées sur les appareils supervisés après le blocage de cette fonctionnalité. L’option (par défaut) **Non configuré** permet d’ajouter, modifier ou supprimer des codes secrets.

  - **Modification de Touch ID et Face ID** : Choisissez l’option **Bloquer** pour empêcher la modification, l’ajout ou la suppression par l’utilisateur des empreintes digitales Touch ID et de Face ID. L’option **Non configuré** (par défaut) autorise l’utilisateur à mettre à jour les empreintes digitales Touch ID et Face ID sur l’appareil.

    Le blocage de ce paramètre empêche également l’utilisateur de modifier, d’ajouter ou de supprimer l’authentification FaceID.

    Face ID s’applique à :  
    - iOS 11.0 et versions ultérieures

- **Bloquer le remplissage automatique du mot de passe** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité de remplissage automatique des mots de passe sur iOS. L’option **Bloquer** a également les conséquences suivantes :

  - Les utilisateurs ne sont pas invités à utiliser un mot de passe enregistré dans Safari ni aucune autre application.
  - Les mots de passe forts automatiques sont désactivés. Les utilisateurs ne reçoivent pas de suggestions de mots de passe forts.

  L’option (par défaut)**Non configuré** autorise ces fonctionnalités.

- **Bloquer les demandes de mot de passe à proximité** : choisissez l’option **Bloquer** pour que l’appareil de l’utilisateur ne demande pas de mots de passe aux appareils à proximité. L’option (par défaut) **Non configuré** autorise ces demandes de mots de passe.
- **Bloquer le partage de mot de passe** : choisissez l’option **Bloquer** pour empêcher le partage des mots de passe entre les appareils avec AirDrop. L’option (par défaut) **Non configuré** autorise le partage de mots de passe.
- **Exiger une authentification Touch ID ou Face ID pour le remplissage automatique du mot de passe ou des informations de carte de crédit** : lorsque cette option est définie sur **Exiger**, les utilisateurs doivent s’authentifier à l’aide de TouchID ou de FaceID avant qu’un mot de passe ou des informations de carte de crédit ne puissent être automatiquement renseignés dans Safari et autres applications. **Non configuré** (par défaut) permet aux utilisateurs de contrôler cette fonctionnalité dans les paramètres de l’appareil.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures
  
<sup>1</sup> Quand vous configurez les paramètres **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** et **Nombre maximal de minutes entre le verrouillage de l’écran et la demande du mot de passe**, ceux-ci sont appliqués en séquence. Par exemple, si vous affectez aux deux paramètres une valeur de **5** minutes, l’écran s’éteint automatiquement après 5 minutes, et l’appareil se verrouille après 5 minutes de plus. Toutefois, si l'utilisateur désactive manuellement l'écran, le second paramètre est immédiatement appliqué. Dans le même exemple, une fois que l’utilisateur a désactivé l’écran, l’appareil se verrouille 5 minutes plus tard.

## <a name="locked-screen-experience"></a>Expérience d’écran verrouillé

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Accès au centre de contrôle quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’utilisateur d’accéder à l’application du centre de contrôle quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise les utilisateurs à accéder à l’application du centre de contrôle lorsque l’appareil est verrouillé.
- **Notifications quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès aux notifications quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisateur à accéder aux notifications sans déverrouiller l’appareil.
- **Mode Aujourd’hui quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès au mode Aujourd’hui quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisateur à afficher la vue Aujourd'hui lorsque l’appareil est verrouillé.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Notifications de Wallet quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès à l’application Wallet quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisateur à accéder à l’application Wallet lorsque l’appareil est verrouillé.

## <a name="app-store-doc-viewing-gaming"></a>App Store, affichage de document, jeux

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Affichage des documents d’entreprise dans les applications non gérées** : choisissez l’option **Bloquer** pour empêcher l’affichage de documents d’entreprise dans les applications non gérées. L’option **Non configuré** (par défaut) autorise l’affichage de documents d’entreprise depuis toute application. Par exemple, vous voulez empêcher les utilisateurs d’enregistrer des fichiers de OneDrive dans Dropbox. Attribuez la valeur **Bloquer** à ce paramètre. Une fois que l’appareil a reçu la stratégie (par exemple, après un redémarrage), il cesse d’autoriser l’enregistrement.


  > [!NOTE]
  > Quand ce paramètre est bloqué, les claviers tiers installés à partir de l’App Store sont également bloqués.

  - **Autoriser les applications non gérées à lire à partir de comptes de contacts gérés** : Quand la valeur est **Autoriser**, les applications non managées, comme l’application de contacts iOS intégrée, peuvent lire les informations de contact et y accéder à partir d’applications managées, notamment l’application mobile Outlook. L’option **Non configuré** (par défaut) empêche la lecture, y compris la suppression des doublons, dans l’application Contacts intégrée sur l’appareil.  
  
    Ce paramètre autorise ou empêche la lecture des informations de contact. Il ne contrôle pas la synchronisation des contacts entre les applications.
  
    Pour utiliser ce paramètre, définissez le paramètre **Affichage des documents d’entreprise dans les applications non gérées**  sur **Bloquer**.

  Pour plus d’informations sur ces deux paramètres et leur impact sur la synchronisation de l’exportation de contacts Outlook pour iOS, consultez [Support Tip: Use Intune custom profile settings with the iOS Native Contacts App](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Use-Intune-custom-profile-settings-with-the-iOS/ba-p/298453).

- **Traiter AirDrop comme une destination non gérée** : choisissez l’option **Exiger** pour qu’AirDrop soit toujours considéré comme une cible de déplacement non gérée. Cette option empêche les applications gérées d’envoyer des données à l’aide via Airdrop. 
- **Affichage de documents externes à l’entreprise dans les applications d’entreprise** : choisissez l’option **Bloquer** pour empêcher l’affichage de documents externes à l’entreprise dans les applications d’entreprise. L’option **Non configuré** (par défaut) autorise tout document à être affiché dans les applications d’entreprise gérées.

  L’affectation de la valeur **Bloquer** empêche également la synchronisation de l’exportation de contacts dans Outlook pour iOS. Pour plus d’informations, consultez [Support Tip: Enabling Outlook iOS Contact Sync with iOS12 MDM Controls](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Enabling-Outlook-iOS-Contact-Sync-with-iOS12-MDM/ba-p/298453).

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Exiger le mot de passe de l’iTunes Store pour tous les achats** : L’option **Exiger** demande à l’utilisateur d’entrer le mot de passe de l’ID Apple pour chaque achat iTunes ou dans l’application. **Non configuré** (par défaut) autorise les achats sans demander chaque fois un mot de passe.
- **Achats dans l’application** : choisissez l’option **Bloquer** pour empêcher les achats dans l’application sur l’App Store. L’option **Non configuré** (par défaut) autorise les achats au sein d’une application en cours d’exécution.
- **Télécharger du contenu de l’iBooks Store indiqué comme étant de la « Littérature érotique » (mode supervisé uniquement)**  : choisissez l’option **Bloquer** pour empêcher les utilisateurs de télécharger du contenu de l’iBooks Store indiqué comme étant de la littérature érotique. L’option **Non configuré** (par défaut) autorise l’utilisateur à télécharger des livres de la catégorie « Littérature érotique ».
- **Autoriser les applications gérées à écrire des contacts dans des comptes de contacts non gérés** : Quand la valeur est **Autoriser**, les applications managées, comme l’application mobile Outlook, peuvent enregistrer ou synchroniser les informations de contact, dont les contacts professionnels et d’entreprise, dans l’application de contacts iOS intégrée. Lorsque la valeur est **Non configuré** (par défaut), les applications managées ne peuvent pas enregistrer ni synchroniser les informations de contact dans l’application de contacts iOS intégrée sur l’appareil.
  
  Pour utiliser ce paramètre, définissez le paramètre **Affichage des documents d’entreprise dans les applications non gérées**  sur **Bloquer**.

- **Région des classifications** : choisissez la région des classifications que vous souhaitez utiliser pour les téléchargements autorisés. Puis choisissez les évaluations autorisées pour les catégories **Films**, **Émissions TV** et **Apps**.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **App Store** : choisissez l’option **Bloquer** pour empêcher l’accès à l’App Store sur les appareils supervisés. **Non configuré** (valeur par défaut) autorise l’accès.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

  - **Installation d’applications à partir de l’App Store** : choisissez l’option **Bloquer** pour empêcher l’accès à l’App Store à partir de l’écran d’accueil de l’appareil. Les utilisateurs finaux peuvent continuer à utiliser iTunes ou l’outil Apple Configurator pour installer des applications. L’option **Non configuré** (par défaut) permet d’accéder à l’App Store depuis l’écran d’accueil.
  - **Téléchargements automatiques d’applications** : choisissez l’option **Bloquer** pour empêcher le téléchargement automatique des applications achetées sur d’autres appareils. Cela n’affecte pas les mises à jour des applications existantes. L’option **Non configuré** (par défaut) autorise le téléchargement sur l’appareil des applications achetées sur d’autres appareils iOS.

- **Contenu iTunes explicite (musique, podcast ou actualités)** : choisissez l’option **Bloquer** pour bloquer la musique, les podcasts ou les actualités iTunes à contenu explicite. L’option **Non configuré** (par défaut) autorise l’appareil à accéder au contenu réservé aux adultes depuis le magasin. iOS 13 et versions ultérieures peuvent nécessiter des appareils supervisés uniquement. 

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

- **Ajout d’amis Game Center** : choisissez **Bloquer** pour empêcher les utilisateurs d’ajouter des amis Game Center. L’option **Non configuré** (par défaut) autorise l’utilisateur à ajouter des amis dans le Game Center.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

- **Game Center** : choisissez **Bloquer** pour empêcher l’utilisation de l’application Game Center. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application Game Center sur l’appareil.
- **Jeux multijoueurs** : choisissez l’option **Bloquer** pour empêcher les jeux multijoueurs. L’option **Non configuré** (par défaut) autorise l’utilisateur à jouer à des jeux multijoueur sur l’appareil.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

- **Accès à un lecteur réseau dans l’application Fichiers** : En utilisant le protocole SMB (Server Message Block), les appareils peuvent accéder à des fichiers ou à d’autres ressources sur un serveur réseau. **Désactiver** empêche l’accès aux fichiers sur un lecteur SMB réseau. **Non configuré** (valeur par défaut) autorise l’accès.

  Cette fonctionnalité s’applique à :  
  - iOS et iPadOS 13.0 et ultérieur

## <a name="built-in-apps"></a>Applications intégrées

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Siri** : choisissez l’option **Bloquer** pour empêcher l’accès à Siri. L’option **Non configuré** (par défaut) autorise l’utilisation de l’assistant vocal Siri sur l’appareil.
  - **Siri quand l’appareil est verrouillé** : choisissez l’option **Bloquer** pour empêcher l’accès à Siri quand l’appareil est verrouillé. L’option **Non configuré** (par défaut) autorise l’utilisation de l’assistant vocal Siri sur l’appareil verrouillé.

- **Avertissements de fraude Safari** : choisissez l’option **Exiger** pour forcer l’affichage d’avertissements en cas de fraude dans le navigateur web de l’appareil. **Non configuré** (valeur par défaut) désactive cette fonctionnalité.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **La recherche Spotlight peut retourner des résultats d’Internet** : choisissez l’option **Bloquer** pour empêcher Spotlight de retourner les résultats d’une recherche sur Internet. L’option (par défaut)**Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.

- **Cookies Safari** : choisissez la façon dont les cookies sont gérés sur l’appareil. Les options disponibles sont les suivantes :
  - Autoriser
  - Bloquer tous les cookies
  - Autoriser les cookies des sites web visités
  - Autoriser les cookies du site web actuel

- **JavaScript Safari** : choisissez l’option **Bloquer** pour empêcher l’exécution des scripts Java dans le navigateur sur l’appareil. **Non configuré** (par défaut) autorise les scripts Java.

- **Fenêtres contextuelles Safari** : choisissez l’option **Bloquer** pour désactiver le bloqueur de fenêtres contextuelles dans le navigateur web. **Non configuré** (par défaut) autorise le bloqueur de fenêtres publicitaires.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Appareil photo** : choisissez **Bloquer** pour empêcher l’accès à l’appareil photo de l’appareil. L’option (par défaut)**Non configuré** autorise l’accès à l’appareil photo de l’appareil.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

  - **FaceTime** : choisissez l’option **Bloquer** pour empêcher l’accès à l’application FaceTime. L’option **Non configuré** (par défaut) autorise l’accès à l’application FaceTime sur l’appareil.

    À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

- **Filtre de vulgarité de Siri** : choisissez l’option **Exiger** pour empêcher Siri de dicter ou d’employer un langage obscène.

  Pour utiliser ce paramètre, affectez au paramètre **Siri** la valeur **Bloquer**.

- **Utiliser Siri pour interroger le contenu généré par l’utilisateur à partir d’Internet** : choisissez l’option **Bloquer** pour empêcher Siri d’accéder à des sites web pour répondre aux questions. L’option **Non configuré** (par défaut) autorise Siri à accéder au contenu généré par les utilisateurs depuis Internet.

  Pour utiliser ce paramètre, affectez au paramètre **Siri** la valeur **Bloquer**.

- **Apple News** : choisissez l’option **Bloquer** pour empêcher l’accès à l’application Apple News sur l’appareil. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application Apple News.
- **iBooks Store** : choisissez l’option **Bloquer** pour empêcher l’accès à l’iBooks Store. L’option **Non configuré** (par défaut) autorise les utilisateurs à parcourir l’iBooks Store et à y acheter des livres.
- **Application Messages sur l’appareil** : **Bloquer** empêche les utilisateurs d’utiliser l’application Messages pour iMessage. Si l’appareil prend en charge la messagerie texte, l’utilisateur peut toujours envoyer et recevoir des messages texte à l’aide de SMS. **Non configuré** (par défaut) permet d’utiliser l’application Messages pour envoyer et lire des messages sur Internet.
- **Podcasts** : choisissez l’option **Bloquer** pour empêcher l’utilisation de l’application Podcasts. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application Podcasts.
- **Service Music** : choisissez l’option **Bloquer** pour rétablir l’application Music en mode classique et désactiver le service Music. L’option (par défaut) **Non configuré** autorise l’utilisation du service Apple Music.
- **Service iTunes Radio** : choisissez l’option **Bloquer** pour empêcher l’utilisation de l’application iTunes Radio. L’option **Non configuré** (par défaut) autorise l’utilisation de l’application iTunes Radio.
- **iTunes Store** : **Non configuré** (par défaut) autorise iTunes sur les appareils. **Bloquer** empêche les utilisateurs d’utiliser iTunes sur l’appareil. 

  Cette fonctionnalité s’applique à :  
  - iOS 4.0 et versions ultérieures

- **Localiser mon iPhone** : **Non configuré** (par défaut) permet d’utiliser cette fonctionnalité de l’application de localisation pour obtenir l’emplacement approximatif de l’appareil. **Bloquer** empêche d’utiliser cette fonctionnalité de l’application de localisation. 

  Cette fonctionnalité s’applique à :  
  - iOS 13.0 et iPadOS 13.0, et versions ultérieures

- **Localiser mes amis** : **Non configuré** (par défaut) permet d’utiliser cette fonctionnalité de l’application de localisation pour rechercher famille et amis sur un appareil Apple ou sur iCloud.com. **Bloquer** empêche d’utiliser cette fonctionnalité de l’application de localisation.

  Cette fonctionnalité s’applique à :  
  - iOS 13.0 et iPadOS 13.0, et versions ultérieures

- **Modifications des paramètres de l’application Localiser mes amis** : choisissez l’option **Bloquer** pour empêcher les modifications des paramètres de l’application Localiser mes amis. L’option **Non configuré** (par défaut) autorise l’utilisateur à modifier les paramètres de l’application Localiser mes amis.

- **La recherche Spotlight peut retourner des résultats d’Internet** : choisissez l’option **Bloquer** pour empêcher Spotlight de retourner les résultats d’une recherche sur Internet. L’option (par défaut)**Non configuré** autorise la recherche Spotlight à se connecter à Internet pour fournir des résultats.

- **Bloquer la suppression des applications système de l’appareil** : choisissez l’option **Bloquer** pour empêcher la suppression des applications système sur l’appareil. L’option **Non configuré** (par défaut) autorise les utilisateurs à supprimer des applications système.

- **Safari** : choisissez l’option **Bloquer** pour empêcher l’utilisation du navigateur Safari sur l’appareil. L’option **Non configuré** (par défaut) autorise l’utilisation du navigateur Safari.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

- **Remplissage automatique Safari** : choisissez l’option **Bloquer** pour désactiver la fonctionnalité de remplissage automatique dans Safari sur l’appareil. L’option (par défaut) **Non configuré** autorise les utilisateurs à modifier les paramètres de saisie semi-automatique dans le navigateur web.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

## <a name="restricted-apps"></a>Applications restreintes

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Type de liste d’applications restreintes** : Créez une liste d’applications que les utilisateurs ne sont pas autorisés à installer ou à utiliser. Les options disponibles sont les suivantes :

  - **Non configuré** (par défaut) : Il n’existe aucune restriction d’Intune. Les utilisateurs ont accès aux applications que vous attribuez et aux applications intégrées.
  - **Applications interdites** : applications non managées par Intune dont vous souhaitez empêcher l’installation sur l’appareil. Rien n’empêche les utilisateurs d’installer une application interdite. Toutefois, si un utilisateur installe une application de cette liste, cela est signalé dans Intune.
  - **Applications approuvées** : applications que les utilisateurs sont autorisés à installer. Les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement. Rien n’empêche les utilisateurs d’installer une application qui ne figure pas dans la liste approuvée. Toutefois, s’ils le font, cela est signalé dans Intune.

Pour ajouter des applications à ces listes, vous pouvez :

- **Ajouter** l’URL iTunes/App Store de l’application que vous souhaitez ajouter. Par exemple, pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- **Importez** un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Vous pouvez sinon **exporter** une liste existante comportant la liste des applications restreintes au même format.

> [!IMPORTANT]
> Les profils d’appareils qui utilisent les paramètres d’applications restreintes doivent être affectés à des groupes d’utilisateurs.

## <a name="show-or-hide-apps"></a>Afficher ou masquer des applications

S’applique aux appareils exécutant iOS 9.3 ou une version plus récente.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Type de liste d’appareils** : Créez une liste d’applications à montrer ou à masquer. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site web d’Apple contient une liste d’[applications Apple intégrées](https://support.apple.com/HT208094). Les options disponibles sont les suivantes :

  - **Applications masquées** : listez les applications que vous souhaitez masquer aux utilisateurs. Les utilisateurs ne peuvent ni afficher ni ouvrir ces applications.
  
    Apple empêche le masquage de certaines applications natives. Par exemple, vous ne pouvez pas masquer les applications **Paramètres** ni **Portefeuille** sur l’appareil. [Delete built-in Apple apps](https://support.apple.com/HT208094) (Supprimer les applications Apple intégrées) liste les applications qui peuvent être masquées.
  
  - **Applications visibles** : listez les applications que les utilisateurs sont autorisés à afficher et lancer. Aucune autre application ne peut être affichée ou lancée.

- **URL de l’application** : Entrez l’URL d’application de Store de l’application que vous voulez montrer ou masquer. Par exemple :

  - Pour ajouter l’application Dossiers de travail Microsoft, entrez `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`ou `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`. 

  - Pour ajouter l’application Microsoft Word, entrez `https://itunes.apple.com/de/app/microsoft-word/id586447913` ou `https://apps.apple.com/de/app/microsoft-word/id586447913`.

  Pour trouver l’URL d’une application, ouvrez iTunes ou l’App Store et recherchez l’application. Par exemple, recherchez `Microsoft Remote Desktop` ou `Microsoft Word`. Sélectionnez l’application et copiez l’URL.

  Vous pouvez également utiliser iTunes pour rechercher l’application, puis la tâche **Copier le lien** pour obtenir l’URL de l’application.

- **ID de l'ensemble d'applications** : entrez l’[ID d’ensemble d’applications](bundle-ids-built-in-ios-apps.md) pour l’application. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site web d’Apple contient une liste d’[applications Apple intégrées](https://support.apple.com/HT208094).
- **Nom de l’application** : entrez le nom de l’application. Vous pouvez afficher ou masquer les applications intégrées et les applications métier. Le site web d’Apple contient une liste d’[applications Apple intégrées](https://support.apple.com/HT208094).
- **Éditeur** : entrez l’éditeur de l’application souhaitée.

Pour ajouter des applications, vous pouvez :

- **Ajouter** : Sélectionnez cette option pour créer votre liste d’applications.
- **Importez** un fichier CSV comportant des détails sur l’application, notamment l’URL. Utilisez le format `<app url>, <app name>, <app publisher>`. Sinon, sélectionnez **Exporter** pour créer une liste des applications restreintes que vous avez ajoutées, au même format.

## <a name="wireless"></a>Sans fil

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

Remarque nécessaire pour l’itinérance des données (Conseil ou remarque importante pour éviter la confusion des clients) : Ce paramètre n’apparaît pas dans le profil de gestion de l’appareil ciblé. Cela est dû au fait que ce paramètre est traité comme une action d’appareil à distance et qu’il est de nouveau bloqué par le service Intune chaque fois que l’état de l’itinérance de données change sur l’appareil. Même s’il ne se trouve pas dans le profil de gestion, il fonctionne s’il apparaît comme réussite dans les rapports de la console d’administration. 
- **Itinérance de données** : choisissez **Bloquer** pour empêcher l’itinérance de données sur le réseau cellulaire. L’option (par défaut) **Non configuré** autorise l’itinérance de données quand l’appareil se trouve sur un réseau cellulaire.

  > [!IMPORTANT]
  > Ce paramètre est traité comme une action d’appareil à distance. Par conséquent, ce paramètre n’apparaît pas dans le profil de gestion sur l’appareil. Chaque fois que l’état de l’itinérance de données change sur l’appareil, le paramètre **Itinérance de données** est bloqué par le service Intune. Dans Intune, si l’état des rapports indique une réussite, sachez qu’il fonctionne, même si le paramètre n’apparaît pas dans le profil de gestion sur l’appareil.

- **Récupération en arrière-plan globale en cas d’itinérance** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité de récupération en arrière-plan globale lors de l’itinérance sur le réseau mobile. L’option (par défaut) **Non configuré** autorise l’appareil à récupérer des données comme les courriers électroniques lorsqu’il est en mode itinérance sur un réseau cellulaire.
- **Numérotation vocale** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité de numérotation vocale sur l’appareil. L’option (par défaut) **Non configuré** autorise la numérotation vocale sur l’appareil.
- **Itinérance vocale** : choisissez l’option **Bloquer** pour empêcher l’itinérance vocale sur le réseau mobile. L’option (par défaut) **Non configuré** autorise l’itinérance vocale quand l’appareil se trouve sur un réseau cellulaire.
- **Point d’accès personnel** : l’option **Bloquer** désactive le point d’accès personnel sur l’appareil de l’utilisateur à chaque synchronisation de l’appareil. Ce paramètre n’est peut-être pas compatible avec certains opérateurs. **Non configuré** (par défaut) conserve la configuration de point d’accès personnel comme la valeur par défaut définie par l’utilisateur.

  > [!IMPORTANT]
  > Ce paramètre est traité comme une action d’appareil à distance. Par conséquent, ce paramètre n’apparaît pas dans le profil de gestion sur l’appareil. Chaque fois que l’état du point d’accès personnel change sur l’appareil, le paramètre **Point d’accès personnel** est bloqué par le service Intune. Dans Intune, si l’état des rapports indique une réussite, sachez qu’il fonctionne, même si le paramètre n’apparaît pas dans le profil de gestion sur l’appareil.

- **Règles d’utilisation des données mobiles (applications gérées uniquement)**  : définissez les types de données que les applications managées peuvent utiliser sur les réseaux mobiles. Les options disponibles sont les suivantes :
  - **Bloquer l’utilisation des données mobiles** : bloquez l’utilisation des données mobiles dans **toutes les applications managées** ou uniquement dans les applications sélectionnées (avec **Choisir des applications spécifiques**).
  - **Bloquer l’utilisation des données mobiles en cas d’itinérance** : bloquez l’utilisation des données mobiles lors de l’itinérance dans **toutes les applications managées** ou uniquement dans les applications sélectionnées (avec **Choisir des applications spécifiques**).

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Modifications des paramètres d’utilisation des données mobiles des applications** : choisissez l’option **Bloquer** pour empêcher les modifications des paramètres d’utilisation des données mobiles des applications. L’option (par défaut) **Non configuré** permet à l’utilisateur de contrôler quelles applications sont autorisées à utiliser les données cellulaires.
- **Changements des paramètres de forfait mobile** : l’option **Bloquer** empêche les utilisateurs de modifier les paramètres du forfait mobile. L’option**Non configuré** (par défaut) permet aux utilisateurs de modifier ces paramètres.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Modification par l’utilisateur du point d’accès personnel** : Quand la valeur est **Bloquer**, l’utilisateur ne peut pas changer le paramètre de point d’accès personnel. **Non configuré** (par défaut) permet aux utilisateurs finaux d’activer ou de désactiver leur point d’accès personnel.

  Si vous bloquez ce paramètre et que vous bloquez le paramètre **Point d’accès personnel**, le point d’accès personnel est désactivé.

  Cette fonctionnalité s’applique à :  
  - iOS 12.2 et versions ultérieures

- **Rejoindre uniquement les réseaux Wi-Fi utilisant des profils de configuration** : choisissez l’option **Exiger** pour forcer l’appareil à utiliser uniquement les réseaux WiFi définis par les profils de configuration Intune. L’option (par défaut) **Non configuré** autorise l’appareil à utiliser d’autres réseaux Wi-Fi.

  Lorsque la valeur est **Exiger**, vérifiez que l’appareil possède un profil Wi-Fi. Si vous n’affectez pas de profil Wi-Fi, ce paramètre peut empêcher l’appareil de se connecter à Internet. En d’autres termes, si ce profil de restrictions d’appareil est attribué avant un profil Wi-Fi, il se peut que l’appareil ne puisse pas se connecter à Internet.
  
  S’il ne peut pas se connecter, désinscrivez l’appareil et réinscrivez-le avec un profil Wi-Fi. Ensuite, affectez à ce paramètre la valeur **Exiger** dans un profil de restrictions d’appareil et attribuez le profil à l’appareil.

- **Wi-Fi toujours activé** : Quand la valeur est **Exiger**, le Wi-Fi reste activé dans l’application Paramètres. Il ne peut pas être désactivé dans Paramètres ni dans le centre de contrôle, même lorsque l’appareil est en mode avion. **Non configuré** (par défaut) permet à l’utilisateur de contrôler l’activation ou la désactivation du Wi-Fi.

  La configuration de ce paramètre n’empêche pas les utilisateurs de sélectionner un réseau Wi-Fi.

  Cette fonctionnalité s’applique à :  
  - iOS et iPadOS 13.0 et ultérieur

## <a name="connected-devices"></a>Appareils connectés

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Détection du poignet pour une Apple Watch appairée** : choisissez l’option **Exiger** pour forcer l’Apple Watch appairée à utiliser la fonctionnalité de détection du poignet. Si cette option est activée, l’Apple Watch n’affiche pas de notification si elle n’est pas portée. 

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Exiger un mot de passe associé pour les demandes AirPlay sortantes** : choisissez l’option **Exiger** pour obliger l’utilisateur à entrer un mot de passe d’appairage quand il se sert d’AirPlay pour le streaming de contenu sur d’autres appareils Apple. L’option (par défaut) **Non configuré** permet à l’utilisateur de diffuser en continu du contenu à l’aide d’AirPlay, sans entrer de mot de passe.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **AirDrop** : choisissez l’option **Bloquer** pour empêcher l’utilisation d’AirDrop sur l’appareil. L’option (par défaut)**Non configuré** autorise l’utilisation de la fonctionnalité AirDrop pour échanger du contenu avec des appareils situés à proximité.
- **Jumelage de l’Apple Watch** : choisissez l’option **Bloquer** pour empêcher l’appairage avec une Apple Watch. L’option (par défaut) **Non configuré** autorise l’appairage avec une Apple Watch.
- **Modification Bluetooth** : choisissez l’option **Bloquer** pour empêcher l’utilisateur de modifier les paramètres Bluetooth sur l’appareil. L’option (par défaut) **Non configuré** permet à l’utilisateur de modifier ces paramètres.
- **Jumelage d’hôtes pour contrôler les appareils avec lesquels un appareil iOS peut être jumelé** : l’option **Non configuré** (par défaut) autorise l’appairage d’hôte pour laisser l’administrateur contrôler les appareils avec lesquels un appareil iOS peut être appairé. L’option **Bloquer** empêche l’appairage d’hôtes.
- **Bloquer AirPrint** : choisissez l’option **Bloquer** pour empêcher l’utilisation de la fonctionnalité AirPrint sur l’appareil. L’option (par défaut) **Non configuré** autorise l’utilisation d’AirPrint.
  - **Bloquer le stockage des informations d’identification AirPrint dans le trousseau** : choisissez l’option **Bloquer** pour empêcher le stockage du nom d’utilisateur et du mot de passe dans le trousseau sur l’appareil. L’option (par défaut) **Non configuré** permet de stocker le nom d’utilisateur et le mot de passe AirPrint dans l’application Trousseau.
  - **Exiger un certificat TLS approuvé pour AirPrint** : choisissez l’option **Exiger** pour forcer l’appareil à utiliser des certificats approuvés pour la communication de l’impression TLS.
  - **Bloquer la découverte par iBeacon des imprimantes AirPrint** : choisissez l’option **Bloquer** pour empêcher le hameçonnage du trafic réseau par des balises AirPrint Bluetooth malveillantes. L’option (par défaut) **Non configuré** permet de publier des imprimantes AirPrint sur l’appareil.
- **Bloquer la configuration de nouveaux appareils à proximité** : l’option **Bloquer** désactive le message qui invite l’utilisateur à configurer de nouveaux appareils situés à proximité. **Non configuré** (par défaut) affiche des messages invitant l’utilisateur à connecter d’autres appareils Apple situés à proximité.

  Cette fonctionnalité s’applique à :  
  - iOS 11.0 et versions ultérieures

- **Accès aux fichiers sur un lecteur USB** : Les appareils peuvent se connecter et ouvrir des fichiers sur un lecteur USB. **Désactiver** empêche l’accès de l’appareil au lecteur USB dans l’application Fichiers quand un lecteur USB est connecté à l’appareil. La désactivation de cette fonctionnalité empêche également les utilisateurs finaux de transférer des fichiers sur un lecteur USB connecté à un iPad. **Non configuré** (par défaut) autorise l’accès à un lecteur USB dans l’application Fichiers.

  Cette fonctionnalité s’applique à :  
  - iOS et iPadOS 13.0 et ultérieur

## <a name="keyboard-and-dictionary"></a>Clavier et dictionnaire

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Recherche de définition de mot** : choisissez l’option **Bloquer** pour empêcher l’utilisateur de mettre en surbrillance un mot, puis d’en consulter la définition sur l’appareil. L’option (par défaut) **Non configuré** autorise l’accès à la fonctionnalité de recherche de définition.
- **Claviers prédictifs** : l’option **Non configuré** (par défaut) autorise l’utilisation de claviers prédictifs pour suggérer des mots que l’utilisateur pourrait vouloir utiliser. L’option **Bloquer** empêche cette fonctionnalité.
- **Correction automatique** : l’option **Non configuré** (par défaut) autorise l’appareil à corriger automatiquement les mots mal orthographiés. Choisissez **Bloquer** pour désactiver la correction automatique.
- **Vérification orthographique du clavier** : **Non configuré** (par défaut) autorise l’utilisation du vérificateur orthographique sur l’appareil. Choisissez **Bloquer** pour désactiver le vérificateur d’orthographe.
- **Raccourcis clavier** : **Non configuré** (par défaut) autorise l’utilisation des raccourcis clavier sur l’appareil. Choisissez **Bloquer** pour empêcher l’utilisation des raccourcis clavier.
- **Dictée** : choisissez l’option **Bloquer** pour empêcher l’utilisateur d’entrer du texte par dictée vocale. L’option **Non configuré** autorise l’utilisation de la dictée.
- **QuickPath** : **Non configuré** (par défaut) autorise les utilisateurs à utiliser QuickPath, qui permet une entrée continue sur le clavier de l’appareil. Les utilisateurs peuvent taper en effectuant un mouvement de balayage sur les touches pour créer des mots. **Bloquer** empêche les utilisateurs d’utiliser QuickPath. 

  Cette fonctionnalité s’applique à :  
  - iOS 13.0 et iPadOS 13.0, et versions ultérieures

## <a name="cloud-and-storage"></a>Cloud et stockage

### <a name="settings-apply-to-all-enrollment-types"></a>Les paramètres s’appliquent à : Tous les types d’inscription

- **Sauvegarde chiffrée** : choisissez l’option **Exiger** pour rendre obligatoire le chiffrement des sauvegardes sur l’appareil.
- **Applications gérées synchronisées avec le cloud** : choisissez l’option **Non configuré** (par défaut) pour autoriser les applications managées par Intune à synchroniser les données dans le compte iCloud de l’utilisateur. Choisissez **Bloquer** pour empêcher cette synchronisation des données sur iCloud.
- **Bloquer la sauvegarde des livres d’entreprise** : choisissez l’option **Bloquer** pour empêcher les utilisateurs de sauvegarder des livres d’entreprise. L’option **Non configuré** (par défaut) autorise les utilisateurs à sauvegarder ces livres.
- **Bloquer la synchronisation des métadonnées des livres d’entreprise (notes et mises en surbrillance)**  : l’option **Bloquer** empêche la synchronisation des notes et mises en surbrillance dans les livres d’entreprise. choisissez l’option **Non configuré** (par défaut) pour autoriser la synchronisation.

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Synchronisation du flux de photos sur iCloud** : l’option **Non configuré** (par défaut) autorise les utilisateurs à activer **Mon flux de photos** sur leur appareil afin de synchroniser les photos sur iCloud et de les publier sur tous les appareils des utilisateurs. Choisissez **Bloquer** pour empêcher la synchronisation du flux de photos sur iCloud. Le blocage de cette fonctionnalité peut entraîner une perte de données. 
- **Photothèque iCloud** : choisissez l’option **Bloquer** pour empêcher le stockage de photos et vidéos dans le cloud à partir de la photothèque iCloud. Toutes les photos qui ne sont pas entièrement téléchargées de la Photothèque iCloud sur l’appareil sont supprimées de l’appareil. L’option **Non configuré** (par défaut) autorise l’utilisation de la photothèque iCloud.
- **Flux de photos partagé** : choisissez l’option **Bloquer** pour désactiver le **partage de photos iCloud** sur l’appareil. L’option **Non configuré** (par défaut) autorise la diffusion en continu des photos partagées.
- **Handoff** : **Non configuré** (par défaut) permet aux utilisateurs de commencer à travailler sur un appareil iOS, puis de poursuivre le travail qu’ils ont commencé sur un autre appareil iOS ou macOS. Choisissez **Bloquer** pour désactiver cette fonctionnalité.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Sauvegarder sur iCloud** : l’option **Non configuré** (par défaut) autorise l’utilisateur à sauvegarder les données de l’appareil sur iCloud. Choisissez **Bloquer** pour empêcher l’utilisateur de sauvegarder les données de l’appareil dans iCloud.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

- **Bloquer la synchronisation des documents iCloud** : L’option (par défaut) **Non configuré** autorise la synchronisation des documents et des pairs clé-valeur dans votre espace de stockage iCloud. Choisissez **Bloquer** pour empêcher iCloud de synchroniser les documents et des données.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

- **Bloquer la synchronisation du trousseau iCloud** : choisissez l’option **Bloquer** pour désactiver la synchronisation des identifiants stockés dans le trousseau sur iCloud. L’option (par défaut) **Non configuré** autorise les utilisateurs à synchroniser ces identifiants.

  À compter d’iOS 13.0, ce paramètre nécessite des appareils supervisés.

## <a name="autonomous-single-app-mode"></a>Mode Application unique autonome

Utilisez ces paramètres pour configurer les appareils iOS/iPadOS pour qu’ils exécutent des applications spécifiques en mode Application unique autonome. Quand ce mode est configuré et que l’utilisateur démarre une des applications configurées, l’appareil est verrouillé sur cette application. Le basculement d’application/tâche est désactivé jusqu’à ce que l’utilisateur quitte l’application autorisée.

Par exemple, dans un environnement scolaire ou universitaire, ajoutez une application qui permet aux utilisateurs d’effectuer un test sur l’appareil. Vous pouvez aussi verrouiller l’appareil dans l’application Portail d’entreprise jusqu’à ce que l’utilisateur final s’authentifie. Une fois les actions de l’application effectuées par l’utilisateur, ou si vous supprimez cette stratégie, l’appareil retourne à son état normal.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Nom de l’application** : entrez le nom de l’application de votre choix.
- **ID de l'ensemble d'applications** : Entrez l’[ID d’ensemble](bundle-ids-built-in-ios-apps.md) de l’application de votre choix.
- **Ajouter** : Sélectionnez cette option pour créer votre liste d’applications.

Vous pouvez également **importer** un fichier CSV contenant la liste des noms d’application et leur ID d’ensemble. Ou, **exporter** une liste existante incluant les applications.

## <a name="kiosk"></a>Kiosk

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Application à exécuter en mode kiosque** : choisissez le type d’applications que vous souhaitez exécuter en mode kiosque. Les options disponibles sont les suivantes :
  - **Non configuré** (par défaut) : les paramètres Kiosque ne sont pas appliqués. L’appareil ne s’exécute pas en mode Kiosque.
  - **Store App** : entrez l’URL vers une application de l’App Store iTunes.
  - **Application gérée** : choisissez une application que vous avez ajoutée à Intune.
  - **Application intégrée** : entrez l’[ID de bundle](bundle-ids-built-in-ios-apps.md) de l’application intégrée.

- **Assistance tactile** : choisissez l’option **Exiger** pour forcer l’activation du paramètre d’accessibilité Assistance tactile sur l’appareil. Cette fonctionnalité aide les utilisateurs à effectuer des gestes à l’écran qui peuvent être difficiles à réaliser pour eux. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Inverser les couleurs** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité qui permet aux utilisateurs ayant des troubles visuels de régler l’affichage. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Audio mono** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité sur l’appareil. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Contrôle vocal** : **Exiger** active le contrôle vocal sur l’appareil et permet aux utilisateurs de contrôler entièrement le système d’exploitation à l’aide des commandes Siri. **Non configuré** désactive le contrôle vocal sur l’appareil.

  Ce paramètre s’applique à :  
  - iOS 13.0 et ultérieur
  - iPadOS 13.0 et ultérieur
  
  > [!TIP]
  > Si des applications métier sont disponibles pour votre organisation et qu’elles ne sont pas prêtes pour le **contrôle vocal** le jour 0 de la publication d’iOS 13.0, nous vous recommandons de conserver la valeur **Non configuré** pour ce paramètre.

- **VoiceOver** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité sur l’appareil afin de permettre la lecture à voix haute du texte à l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Zoom** : choisissez l’option **Exiger** pour forcer l’activation de ce paramètre d’accessibilité sur l’appareil et permettre ainsi aux utilisateurs d’agrandir l’affichage en touchant l’écran. L’option **Non configuré** n’exécute ou n’active pas cette fonctionnalité en mode plein écran.
- **Verrouillage automatique** : **Bloquer** empêche le verrouillage automatique de l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Modification de sonnerie** : l’option **Bloquer** désactive le commutateur de sonnerie (désactivation du son) sur l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Rotation de l’écran** : **bloquer** empêche la modification de l’orientation de l’écran lorsque l’utilisateur fait pivoter l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Bouton de veille de l’écran** : choisissez l’option **Bloquer** pour désactiver le bouton de veille/sortie de veille de l’écran sur l’appareil. L’option **Non configuré** autorise cette fonctionnalité.
- **Tactile** : choisissez l’option **Bloquer** pour désactiver l’écran tactile sur l’appareil. L’option **Non configuré** permet l’utilisation de l’écran tactile.
- **Boutons de volume** : **Bloquer** empêche l’utilisation des boutons de volume sur l’appareil. **Non configuré** autorise les boutons de volume.
- **Commande d’assistance tactile** : choisissez l’option **Autoriser** pour permettre l’utilisation de la fonction d’assistance tactile. L’option **Non configuré** désactive cette fonctionnalité.
- **Inverser le contrôle des couleurs** : choisissez l’option **Autoriser** pour permettre les réglages de couleurs inversées afin que les utilisateurs puissent ajuster la fonction de couleurs inversées. L’option **Non configuré** désactive cette fonctionnalité.
- **Lire le texte sélectionné** : choisissez l’option **Autoriser** pour permettre l’activation des paramètres d’accessibilité de sélection de la reconnaissance vocale sur l’appareil. Cette fonctionnalité lit à voix haute le texte que l’utilisateur sélectionne. L’option **Non configuré** désactive cette fonctionnalité.
- **Modification du contrôle vocal** : **Autoriser** permet aux utilisateurs de changer l’état du contrôle vocal sur leurs appareils. **Non configuré** empêche les utilisateurs de changer l’état du contrôle vocal sur leurs appareils.

  Ce paramètre s’applique à :  
  - iOS 13.0 et ultérieur
  - iPadOS 13.0 et ultérieur

- **Contrôle de VoiceOver** : choisissez l’option **Autoriser** pour permettre aux utilisateurs de modifier la fonction VoiceOver, notamment la vitesse de lecture à voix haute du texte à l’écran. L’option **Non configuré** empêche toute modification de VoiceOver.
- **Réglage du zoom** : choisissez l’option **Autoriser** pour permettre aux utilisateurs de changer le zoom. L’option **Non configuré** empêche toute modification du zoom.

> [!NOTE]
> Avant de pouvoir configurer un appareil iOS pour le mode plein écran, vous devez utiliser l’outil Apple Configurator ou le Programme d’inscription des appareils Apple pour mettre l’appareil en mode supervisé. Consultez le guide Apple sur l’utilisation de l’outil Apple Configurator.
> Si l’application iOS que vous spécifiez est installée après l’attribution du profil, l’appareil ne bascule en mode plein écran qu’après son redémarrage.

## <a name="domains"></a>Domaines

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription des appareils, Inscription automatique des appareils (supervisée)

- **Domaines d’e-mail non marqués** > **URL de domaine marquées** : ajoutez une ou plusieurs URL à la liste. Quand les utilisateurs finaux reçoivent un e-mail provenant d’un domaine autre que ceux que vous avez saisis, l’e-mail est marqué comme non approuvé dans l’application iOS Mail.

- **Domaines web gérés** > **URL de domaine web** : ajoutez une ou plusieurs URL à la liste. Les documents téléchargés à partir des domaines que vous saisissez sont considérés comme gérés. Ce paramètre s’applique uniquement aux documents téléchargés à l’aide du navigateur Safari.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Les paramètres s’appliquent à : Inscription automatique des appareils (supervisée)

- **Domaines de remplissage automatique des mots de passe Safari** > **URL de domaine** : ajoutez une ou plusieurs URL à la liste. Les utilisateurs peuvent uniquement enregistrer les mots de passe web à partir des URL de cette liste. Ce paramètre s’applique uniquement au navigateur Safari et aux appareils en mode supervisé. Si vous n’entrez aucune URL, les mots de passe peuvent être enregistrés à partir de tous les sites web.

  Ce paramètre s’applique à :  
  - iOS 9.3 et versions ultérieures

## <a name="settings-that-require-supervised-mode"></a>Paramètres qui nécessitent le mode supervisé

Vous pouvez activer le mode supervisé iOS seulement pendant l’installation initiale de l’appareil par le biais du programme DEP d’Apple ou d’Apple Configurator. Une fois le mode supervisé activé, Intune peut configurer un appareil avec les fonctionnalités suivantes :

- Verrouillage d’application (Mode Application unique) 
- Proxy HTTP global 
- Désactiver le verrou d’activation 
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
