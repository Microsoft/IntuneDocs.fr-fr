---
title: Configurer une page d’état d’inscription
titleSuffix: Microsoft Intune
description: Configurez une page d’accueil pour les utilisateurs qui inscrivent des appareils Windows 10.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2a6b427552e545421e329b900833c889e67bf35
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503021"
---
# <a name="set-up-an-enrollment-status-page"></a>Configurer une page d’état d’inscription
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
La page d’état d’inscription (ESP) affiche des informations d’installation sur les appareils Windows 10 (version 1803 et versions ultérieures) lors de l’inscription initiale de l’appareil. Par exemple :
- lors de l’utilisation de [l’AutoPilot Windows](https://docs.microsoft.com/windows/deployment/windows-autopilot/) 
- ou chaque fois qu’un appareil géré est démarré pour la première fois après l’application d’une stratégie de page d’état d’inscription. 

La page d’état d’inscription aide les utilisateurs à comprendre l’état de leur appareil pendant la configuration de ce dernier. Vous pouvez créer plusieurs profils de page d’état d’inscription et les appliquer à différents groupes contenant des utilisateurs. Vous pouvez définir des profils pour :
- Afficher la progression de l’installation.
- Bloquer l’utilisation jusqu’à ce que l’installation soit terminée.
- Spécifier ce qu’un utilisateur peut faire si la configuration de l’appareil échoue.

Vous pouvez également définir l’ordre de priorité de chaque profil pour éviter que les profils affectés à un même utilisateur n’entrent en conflit.

> [!NOTE]
> La page d’état d’inscription ne peut être ciblée que sur un utilisateur qui appartient à un groupe attribué, et la stratégie est définie sur l’appareil au moment de l’inscription pour tous les utilisateurs qui utilisent l’appareil.  

## <a name="available-settings"></a>Paramètres disponibles

 Les paramètres suivants peuvent être configurés pour personnaliser le comportement de la page d’état d’inscription :

<table>
<th align="left">Paramètre<th align="left">Oui<th align="left">Non
<tr><td>Afficher la progression de l’installation des profils et des applications<td>La page d’état d’inscription s’affiche.<td>La page d’état d’inscription ne s’affiche pas.
<tr><td>Bloquer l’utilisation de l’appareil jusqu’à ce que toutes les applications et tous les profils soient installés<td>Les paramètres de ce tableau sont disponibles pour personnaliser le comportement de la page d’état d’inscription, afin que l’utilisateur puisse résoudre les problèmes d’installation potentiels.
<td>La page d’état d’inscription s’affiche sans aucune option supplémentaire pour résoudre les échecs d’installation.
<tr><td>Autoriser les utilisateurs à réinitialiser l’appareil si une erreur d’installation se produit<td>Un bouton <b>Réinitialiser l’appareil</b> s’affiche en cas d’échec de l’installation.<td>Le bouton <b>Réinitialiser l’appareil</b> ne s’affiche pas en cas d’échec de l’installation.
<tr><td>Autoriser les utilisateurs à utiliser l’appareil si une erreur d’installation se produit<td>Un bouton <b>Continuer quand même</b> s’affiche en cas d’échec de l’installation.<td>Le bouton <b>Continuer quand même</b> ne s’affiche pas en cas d’échec de l’installation.
<tr><td>Afficher l’erreur de délai d’expiration lorsque l’installation prend plus de minutes que le nombre de minutes spécifié<td colspan="2">Spécifiez le nombre de minutes à attendre avant la fin de l’installation. Une valeur par défaut de 60 minutes est entrée.
<tr><td>Afficher un message personnalisé lorsqu’une erreur se produit<td>Vous disposez d’une zone de texte dans laquelle vous pouvez spécifier un message personnalisé à afficher si une erreur d’installation se produit.<td>Le message par défaut s’affiche : <br><b>L’installation a dépassé la limite de temps définie par votre organisation. Réessayez ou contactez la personne chargée du support technique pour obtenir de l’aide.<b>
<tr><td>Autoriser les utilisateurs à collecter des journaux sur les erreurs d’installation<td>En cas d’erreur d’installation, un bouton <b>Collecter les journaux</b> s’affiche. <br>Si l’utilisateur clique sur ce bouton, il est invité à choisir un emplacement pour enregistrer le fichier journal <b>MDMDiagReport.cab</b><td>Le bouton <b>Collecter les journaux</b> ne s’affiche pas en cas d’erreur d’installation.
<tr><td>Bloquer l’utilisation de l’appareil jusqu’à ce que ces applications requises soient installées si elles sont affectées à l’utilisateur/l’appareil<td colspan="2">Choisissez <b>Tous</b> ou <b>Sélection</b>. <br><br>Si vous choisissez <b>Sélection</b>, un bouton <b>Sélectionner les applications</b> s’affiche et vous permet de choisir les applications qui doivent être installées avant d’activer l’appareil.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Activer la page d’état d’inscription par défaut pour tous les utilisateurs

Pour activer la page d’état d’inscription, suivez les étapes ci-dessous.
 
1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Page d’état d’inscription**.
2. Dans le panneau **Page d’état d’inscription**, choisissez **Par défaut** > **Paramètres**.
3. Pour **Afficher la progression de l’installation des profils et des applications**, choisissez **Oui**.
4. Choisissez les autres paramètres que vous voulez activer, puis choisissez **Enregistrer**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Créer un profil de page d’état d’inscription et l’affecter à un groupe

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Page d’état d’inscription** > **Créer un profil**.
2. Indiquez un **Nom** et une **Description**.
3. Choisissez **Créer**.
4. Choisissez le nouveau profil dans la liste **Page d’état d’inscription**.
5. Choisissez **Affectations** > **Sélectionner des groupes** > choisissez les groupes qui doivent adopter ce profil > **Sélectionner** > **Enregistrer**.
6. Choisissez **Paramètres** > choisissez les paramètres à appliquer à ce profil > **Enregistrer**.

## <a name="set-the-enrollment-status-page-priority"></a>Définir la priorité d’une page d’état d’inscription

Un utilisateur peut se trouver dans de nombreux groupes et avoir de nombreux profils de page d’état d’inscription. Pour résoudre ces conflits, vous pouvez définir les priorités de chaque profil. Lors de l’inscription, si un utilisateur possède plusieurs profils de page d’état d’inscription, seul le profil à la priorité la plus élevée est appliqué à l’appareil d’inscription.

1. Dans [Intune](https://aka.ms/intuneportal), choisissez **Inscription des appareils** > **Inscription Windows** > **Page d’état d’inscription**.
2. Pointez sur le profil dans la liste.
3. À l’aide des trois points verticaux, faites glisser le profil à la position souhaitée dans la liste.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Bloquer l’accès à un appareil tant qu’une certaine application n’est pas installée

Vous pouvez spécifier quelles applications doivent être installés pour que l’utilisateur puisse accéder au bureau.

1. Dans Intune, choisissez **Inscription des appareils** > **Inscription Windows** > **Page d’état d’inscription**.
2. Choisissez un profil > **Paramètres**.
3. Choisissez **Oui** pour **Afficher la progression de l’installation des profils et des applications**.
4. Choisissez **Oui** pour **Bloquer l’utilisation de l’appareil jusqu’à ce que toutes les applications et tous les profils soient installés**.
5. Choisissez **Sélectionnées** pour **Bloquer l’utilisation de l’appareil jusqu’à ce que ces applications requises soient installées si elles sont affectées à l’utilisateur/l’appareil**.
6. Choisissez **Sélectionner des applications** > choisissez les applications > **Sélectionner** > **Enregistrer**.

## <a name="enrollment-status-page-tracking-information"></a>Informations de suivi de la page d’état d’inscription

La page d’état d’inscription effectue le suivi des informations pour trois phases : la préparation de l’appareil, la configuration de l’appareil et la configuration du compte.

### <a name="device-preparation"></a>Préparation de l’appareil

Pour la préparation de l’appareil, la page d’état d’inscription effectue le suivi des éléments suivants :
- Attestations de clé du Module de plateforme sécurisée (TPM) (TPM) (le cas échéant)
- progression dans la jointure d’Azure Active Directory
- inscription dans Intune
- installation des extensions de gestion Intune

### <a name="device-setup"></a>Configuration de l’appareil

La page d’état d’inscription effectue le suivi des éléments de configuration d’appareil suivants (s’ils sont affectés à Tous les appareils ou à un groupe d’appareils dans lequel l’appareil inscrit est membre) :
- Stratégies de sécurité
  - Un fournisseur de services de configuration pour toutes les inscriptions.
  - Les fournisseurs de solutions Cloud réels configurés par Intune ne sont pas suivis ici.
- Applications
  - Applications MSI métier par machine.
  - Applications du Store métier avec contexte d’installation = Appareil.
  - Applications du Store métier et du Store hors connexion avec contexte d’installation = Appareil.
  - Applications Win32 (Windows 10 version 1903 et versions ultérieures uniquement) 
- Profils de connectivité
  - Profils Wi-Fi ou VPN qui sont affectés à **Tous les appareils** ou à un groupe d’appareils dont est membre l’appareil à inscrire, mais uniquement pour les appareils Autopilot
- Profils de certificat qui sont affectés à **Tous les appareils** ou à un groupe d’appareils dont est membre l’appareil à inscrire, mais uniquement pour les appareils Autopilot

### <a name="account-setup"></a>Configuration du compte
Pour la configuration du compte, la page d’état d’inscription indique le suivi des éléments suivants, s’ils sont affectés à l’utilisateur actuellement connecté :
- Stratégies de sécurité
  - Un seul fournisseur de services de configuration pour toutes les inscriptions.
  - Les fournisseurs de solutions Cloud réels configurés par Intune ne sont pas suivis ici.
- Applications
  - Applications MSI métier par utilisateur qui sont affectées à Tous les appareils, à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.
  - Applications MSI métier par machine qui sont affectées à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.
  - Les applications de Store métier, les applications de Store en ligne et les applications de Store hors connexion sont affectées à l’un des objets suivants :
    - Tous les appareils
    - Tous les utilisateurs
    - Groupe d’utilisateurs dans lequel l’utilisateur qui inscrit l’appareil est un membre dont le contexte d’installation est Utilisateur.
  - Applications Win32 (Windows 10 version 1903 et versions ultérieures uniquement) 
- Profils de connectivité
  - Profils VPN ou Wi-Fi qui sont affectés à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.
- Certificats
  - Profils de certificat qui sont affectés à Tous les utilisateurs ou à un groupe d’utilisateurs dont est membre l’utilisateur inscrivant l’appareil.

### <a name="troubleshooting"></a>Résolution des problèmes
Questions principales sur la résolution des problèmes.

- Pourquoi mes applications n’ont-elles pas été installées lors de la phase de configuration de l’appareil lors du déploiement AutoPilot qui utilise la page d’état d’inscription ?
  - Pour garantir que les applications sont installées pendant la phase de configuration d’un appareil AutoPilot, assurez-vous que 
        1. L’application est sélectionnée pour bloquer l’accès dans la liste des applications sélectionnées
        2. Vous ciblez les applications pour le même groupe d’appareils Azure AD que celui auquel votre profil AutoPilot est affecté. 

- Pourquoi la page d’état d’inscription s’ouvre-t-elle pour les déploiements autres qu’AutoPilot, par exemple lorsqu’un utilisateur se connecte pour la première fois sur un appareil inscrit pour la cogestion Configuration Manager ?  
  - La page d’état d’inscription répertorie l’état d’installation de toutes les méthodes d’inscription, y compris
      - Autopilot
      - Cogestion Configuration Manager
      - Quand un nouvel utilisateur se connecte à l’appareil pour lequel la stratégie de page d’état d’inscription est appliquée pour la première fois

- Comment puis-je désactiver la page d’état d’inscription si elle a été configurée sur l’appareil ?
  - La stratégie de page d’état d’inscription est définie sur un appareil au moment de l’inscription. Pour désactiver la page d’état d’inscription, vous devez désactiver les sections de la page d’état d’inscription des utilisateurs et des appareils. Vous désactivez les sections en créant des paramètres OMA-URI personnalisés avec les configurations suivantes.

      Page Désactiver l’état d’inscription de l’utilisateur :

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      Page Désactiver l’état d’inscription de l’appareil :

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- Comment puis-je collecter les fichiers journaux ?
  - Il existe deux façons de collecter les fichiers journaux des pages d’état d’inscription :
      - Autorisez les utilisateurs à collecter les journaux dans la stratégie ESP. Lorsqu’une expiration du délai d’attente se produit dans la page d’état d’inscription, l’utilisateur final peut choisir l’option **Collecter les journaux**. En insérant un lecteur USB, les fichiers journaux peuvent être copiés sur le lecteur
      - Ouvrez une invite de commandes en entrant la séquence de touches Maj + F10, puis entrez la ligne de commande suivante pour générer les fichiers journaux : 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>Problèmes connus
Vous trouverez ci-dessous des problèmes connus. 
- La désactivation du profil ESP ne supprime pas la stratégie ESP des appareils, et les utilisateurs ont toujours la protection ESP lorsqu’ils se connectent à l’appareil pour la première fois. La stratégie n’est pas supprimée lorsque le profil ESP est désactivé. Vous devez déployer OMA-URI pour désactiver la protection ESP. Voir ci-dessus pour obtenir des instructions sur la façon de désactiver ESP avec OMA-URI. 
- Un redémarrage en attente entraînera toujours un délai d’expiration. Le délai d'expiration se produit car l’appareil doit être redémarré. Le redémarrage est nécessaire pour permettre l’exécution de l’objet suivi sur la page d’état d’inscription. Un redémarrage entraîne la fermeture de la page d’état d’inscription et, après le redémarrage, l’appareil n’entre pas dans la configuration du compte après le redémarrage.  Envisagez de ne pas exiger un redémarrage avec l’installation de l’application. 
- Un redémarrage lors de la configuration de l’appareil force l’utilisateur à entrer ses informations d’identification avant de passer à la phase de configuration du compte. Les informations d’identification de l’utilisateur ne sont pas conservées lors du redémarrage. Demandez à l’utilisateur d’entrer ses informations d’identification avant que la page d’état d’inscription puisse continuer. 
- Les certificats SCEP avec des stratégies Windows Hello Entreprise entraînent un délai d’expiration, car l’utilisateur ne peut pas terminer la configuration du code confidentiel Hello pour permettre l’installation simultanée du certificat SCEP.  Aucune solution de contournement. La date de correction estimée est l’été 2019. 
- La page d’état d’inscription expirera toujours pendant l’inscription d’un compte professionnel ou scolaire sur les versions Windows 10 inférieures à 1903. La page d’état d’inscription attend la fin de l’inscription d’Azure AD. Le problème est résolu dans Windows 10 version 1903 et les versions ultérieures.  
- Le déploiement Autopilot Azure AD Hybride avec ESP prend plus de temps que le délai d’expiration défini dans le profil ESP. Sur les déploiements Autopilot Azure AD Hybride, le protocole ESP prend 40 minutes de plus que la valeur définie dans le profil ESP. Ce délai permet au connecteur AD local de créer le nouvel enregistrement d’appareil pour Azure AD. 
- La page d’ouverture de session Windows n’est pas préremplie avec le nom d’utilisateur en mode piloté par l’utilisateur AutoPilot. En cas de redémarrage au cours de la phase de configuration de l’appareil d’ESP :
    - les informations d’identification de l’utilisateur ne sont pas conservées
    - l’utilisateur doit à nouveau entrer les informations d’identification avant de passer de la phase de configuration de l’appareil à la phase de configuration du compte
- ESP est bloqué pendant une longue période ou ne termine jamais la phase d’identification. Intune calcule les stratégies ESP au cours de la phase d’identification. Un appareil peut ne jamais terminer le calcul des stratégies ESP si l’utilisateur actuel n’a pas de licence Intune affectée.  
- La configuration du contrôle d’application Windows Defender provoque une invite de redémarrage lors de l’Autopilot. La configuration de l’application Windows Defender (Fournisseur de services de configuration AppLocker) requiert un redémarrage. Lorsque cette stratégie est configurée, elle peut entraîner le redémarrage d’un appareil pendant l’Autopilot. Actuellement, il n’existe aucun moyen de supprimer ou de différer le redémarrage.
- Lorsque la stratégie DeviceLock (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) est activée dans le cadre d’un profil ESP, l’OOBE ou l’ouverture automatique de session du bureau de l’utilisateur peut échouer de façon inattendue pour deux raisons.
  - Si l’appareil n’a pas redémarré avant de quitter la phase de configuration de l’appareil ESP, l’utilisateur peut être invité à entrer ses informations d’identification Azure AD. Cette invite s’affiche au lieu d’une ouverture de session automatique réussie où l’utilisateur voit l’animation de la première connexion à Windows.
  - L’ouverture automatique de session échoue si l’appareil a redémarré une fois que l’utilisateur a entré ses informations d’identification Azure AD, mais avant de quitter la phase de configuration de l’appareil ESP. Cet échec se produit car la phase de configuration de l’appareil ESP ne s’est jamais terminée. La solution de contournement consiste à réinitialiser l’appareil.

## <a name="next-steps"></a>Étapes suivantes
Après avoir configuré les pages d’inscription Windows, découvrez comment gérer les appareils Windows. Pour plus d’informations, consultez [Qu’est-ce que la gestion des appareils Microsoft Intune ?](../remote-actions/device-management.md)
