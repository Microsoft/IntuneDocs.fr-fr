---
title: Restrictions d’appareils pour les profils professionnels Android dans Microsoft Intune - Azure | Microsoft Docs
description: Sur les appareils avec profil professionnel Android, vous pouvez restreindre certains paramètres, notamment les opérations de copier-coller, l’affichage des notifications, les autorisations d’application, le partage de données, la longueur de mot de passe, les échecs de connexion, l’utilisation d’empreintes digitales pour le déverrouillage, la réutilisation des mots de passe et l’activation du partage Bluetooth des contacts professionnels.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 51e52e26357143d214c4bcf7856dfdb75a68653c
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329767"
---
# <a name="work-device-restriction-settings-in-intune"></a>Paramètres de restriction appareil professionnel dans Intune

Cet article répertorie les paramètres de restriction d’appareil de Microsoft Intune que vous pouvez configurer pour les appareils avec profil professionnel Android.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Paramètres de profil professionnel

### <a name="general-settings"></a>Paramètres généraux

- **Copier-coller entre les profils professionnel et personnel** : contrôle les opérations copier et coller entre les applications professionnelles et personnelles. Choisissez **Bloquer** pour activer le blocage. Choisissez **Non configuré** pour désactiver le blocage.
- **Partage des données entre les profils professionnels et personnels** : contrôlez si les applications associées au profil professionnel peuvent ou non partager avec des applications du profil personnel. Ce paramètre contrôle les actions de partage dans les applications (par exemple, l’option **Patager...** dans l’application de navigateur Chrome), et ne s’applique pas au comportement copier-coller du Presse-papiers. Contrairement aux [paramètres de stratégie de protection des applications](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), les paramètres de restriction d’appareil sont gérés à partir du portail Intune et utilisent la partition du profil professionnel Android pour isoler les applications gérées. Choisissez parmi :
  - **Restrictions de partage par défaut** : comportement de partage par défaut de l’appareil, qui varie en fonction de la version d’Android. Par défaut, le partage du profil personnel vers le profil professionnel est autorisé. Le partage du le profil professionnel vers le profil personnel est aussi bloqué par défaut. Ce paramètre empêche les partages de données du profil professionnel vers le profil personnel. Google ne fournit aucun moyen de bloquer le partage du profil personnel vers le profil professionnel sur les appareils exécutant des versions antérieures à 6.0.
  - **Les applications du profil professionnel peuvent gérer une demande de partage provenant d’un profil personnel** : active la fonctionnalité Android intégrée qui autorise le partage entre le profil personnel et le profil professionnel. Lorsque cette option est activée, une demande de partage à partir d’une application du profil personnel peut partager avec les applications associées au profil professionnel. Ce paramètre est le comportement par défaut des appareils Android exécutant des versions antérieures à 6.0.
  - **Autoriser le partage en dehors des limites** : permet le partage dans les deux sens au-delà de la limite du profil professionnel. Lorsque vous sélectionnez ce paramètre, les applications du profil de travail peuvent partager des données avec des applications sans badge du profil personnel. Utilisez ce paramètre avec précaution, car il autorise le partage des applications gérées dans le profil professionnel vers des applications du côté non géré de l’appareil.

- **Notifications du profil professionnel quand l’appareil est verrouillé** : permet de déterminer si les applications du profil professionnel peuvent afficher des données dans des notifications quand l’appareil est verrouillé.
- **Autorisations des applications par défaut** : définit la stratégie d’autorisation par défaut pour toutes les applications du profil professionnel. À compter d’Android 6, l’utilisateur est invité à accorder certaines autorisations requises par les applications lorsque l’application est lancée. Ce paramètre de stratégie vous permet de décider si les utilisateurs sont invités à accorder des autorisations pour toutes les applications du profil professionnel. Par exemple, vous pouvez affecter au profil professionnel une application qui nécessite un accès à l’emplacement. Normalement, cette application invite l’utilisateur à approuver ou refuser l’accès à l’emplacement pour l’application. Cette stratégie vous permet de décider si toutes les autorisations doivent être accordées automatiquement sans invite, refusées automatiquement sans invite ou déterminées par l’utilisateur. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Demander**
  - **Accorder automatiquement**
  - **Refuser automatiquement**

    L’état de l’octroi des autorisations peut être défini plus précisément pour des applications spécifiques en utilisant une stratégie de configuration d’application pour une application individuelle (sous **Applications clientes** > **Stratégies de configuration des applications**).

- **Ajouter et supprimer des comptes**

   Empêche les utilisateurs finaux d’ajouter ou de supprimer manuellement des comptes dans le profil professionnel.

   Par exemple, quand vous déployez l’application Gmail dans un profil professionnel Android, vous pouvez empêcher les utilisateurs finaux d’ajouter ou de supprimer des comptes dans ce profil professionnel.

- **Partage de contacts via Bluetooth** : permet d’accéder aux contacts professionnels à partir d’un autre appareil, par exemple une voiture, qui est apparié à l’aide de Bluetooth. Ce paramètre n’étant pas configuré par défaut, les contacts de profil professionnel ne sont pas visibles. Sélectionnez **Activer** pour autoriser ce partage et afficher les contacts de profil professionnel. Ce paramètre s’applique aux appareils avec profil professionnel Android sur le système d’exploitation Android 6.0 et versions ultérieures. L’activation de cette option peut permettre à certains appareils Bluetooth de mettre en cache des contacts professionnels à la première connexion. La désactivation de cette stratégie après un jumelage/une synchronisation initiale ne supprime pas toujours les contacts professionnels d’un appareil Bluetooth.

- **Capture d’écran** : bloque la capture d’écran sur l’appareil dans le profil professionnel. Cela empêche également que le contenu soit affiché sur les écrans dépourvus de sortie vidéo sécurisée.

- **Afficher l’ID d’appelant du contact professionnel dans le profil personnel** : quand ce paramètre est activé (non configuré), les détails de l’ID d’appelant du contact professionnel sont affichés dans le profil personnel. Quand ce paramètre est désactivé, le numéro d’appelant du contact professionnel ne s’affiche pas dans le profil personnel. S’applique à Android OS v6.0 et versions plus récentes.

- **Appareil photo** : bloque l’appareil photo sur l’appareil dans le profil professionnel. L’appareil photo dans le profil personnel n’est pas affectée par ce paramètre.

### <a name="work-profile-password"></a>Mot de passe de profil professionnel

- **Exiger le mot de passe du profil professionnel** : s’applique à Android 7.0 et ultérieur avec profil professionnel activé. Définissez une stratégie de mot de passe qui s’applique uniquement aux applications dans le profil professionnel. Par défaut, l’utilisateur final peut utiliser les deux codes PIN définis séparément ou choisir de combiner les deux codes PIN définis dans le plus sécurisé des deux.
- **Longueur minimale du mot de passe** : entrez le nombre minimal de caractères devant figurer dans le mot de passe des utilisateurs (**4**-**16**)
- **Nombre maximal de minutes d’inactivité avant le verrouillage du profil professionnel** : sélectionnez le délai de verrouillage du profil professionnel. L’utilisateur doit ensuite entrer ses informations d’identification pour rétablir l’accès.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre de saisies possibles d’un mot de passe incorrect avant que le profil professionnel soit supprimé.
- **Expiration du mot de passe (jours)**  : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (**1**-**255**).
- **Type de mot de passe requis** : sélectionnez le type de mot de passe qui doit être défini sur l’appareil. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Obligatoire**
  - **Au moins numérique**
  - **Chiffres complexes** : les chiffres répétés ou consécutifs tels que « 1111 » ou « 1234 » ne sont pas autorisés.
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**
- **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe (**1**-**24**).
- **Déverrouillage par empreinte digitale** : empêche les utilisateurs d’utiliser le lecteur d’empreintes digitales de l’appareil pour le déverrouiller.
- **Smart Lock et autres agents de confiance** : contrôle la fonctionnalité Smart Lock sur les appareils compatibles. Cette fonctionnalité du téléphone, parfois appelée agents de confiance, vous permet de désactiver ou de contourner le mot de passe de profil professionnel si celui-ci se trouve à un emplacement approuvé. Par exemple, quand il est connecté à un appareil Bluetooth spécifique ou quand il se trouve à proximité d’une balise NFC. Utilisez ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.

## <a name="device-password"></a>Mot de passe de l’appareil

- **Longueur minimale du mot de passe** : entrez le nombre minimal de caractères devant figurer dans le mot de passe des utilisateurs (**4**-**14**)
- **Nombre maximal de minutes d’inactivité avant le verrouillage de l’appareil** : sélectionnez le délai de verrouillage automatique d’un appareil inactif.
- **Nombre d’échecs de connexion avant réinitialisation de l’appareil** : entrez le nombre de saisies possibles d’un mot de passe incorrect avant que toutes les données de l’appareil soient supprimées.
- **Expiration du mot de passe (jours)**  : entrez le nombre de jours avant que l’utilisateur ne doive modifier le mot de passe de l’appareil (**1**-**255**).
- **Type de mot de passe requis** : sélectionnez le type de mot de passe qui doit être défini sur l’appareil. Choisissez parmi :
  - **Paramètre par défaut de l’appareil**
  - **Sécurité biométrique faible**
  - **Obligatoire**
  - **Au moins numérique**
  - **Chiffres complexes** : les chiffres répétés ou consécutifs tels que « 1111 » ou « 1234 » ne sont pas autorisés.
  - **Au moins alphabétique**
  - **Au moins alphanumérique**
  - **Au moins alphanumérique avec des symboles**
- **Empêcher la réutilisation des mots de passe précédents** : entrez le nombre de nouveaux mots de passe devant être utilisés avant de pouvoir réutiliser un ancien mot de passe (**1**-**24**).
- **Déverrouillage par empreinte digitale** : empêche les utilisateurs d’utiliser le lecteur d’empreintes digitales de l’appareil pour le déverrouiller.
- **Smart Lock et autres agents de confiance** : contrôle la fonctionnalité Smart Lock sur les appareils compatibles. Cette fonctionnalité du téléphone, parfois appelée agents de confiance, vous permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil si celui-ci se trouve à un emplacement approuvé. Par exemple, quand il est connecté à un appareil Bluetooth spécifique ou quand il se trouve à proximité d’une balise NFC. Utilisez ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.

## <a name="system-security"></a>Sécurité système

- **Analyse des menaces sur les applications** : appliquer la règle indiquant que le paramètre **Vérifier les applications** est activé pour les profils professionnels et personnels.

   > [!Note]
   > Ce paramètre ne fonctionne que pour les appareils Android O et versions supérieures.

## <a name="next-step"></a>Étape suivante

Pour enregistrer le profil et l’affecter à des utilisateurs et appareils, consultez [Configurer des paramètres de restriction d’appareil](device-restrictions-configure.md).
