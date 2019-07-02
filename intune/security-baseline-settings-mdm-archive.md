---
title: Archive - Intune MDM lignes de base des paramètres de sécurité pour Windows 10
titleSuffix: Microsoft Intune
description: Archive des versions précédentes de mise en production les gestion des appareils mobiles de référence des paramètres de sécurité pour la gestion de Windows 10 avec Microsoft Intune
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8e83aa6b13f192da87a78690b0040e545d8943e
ms.sourcegitcommit: 690e680e854b7d707421c5e06f134e493f4f4194
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67418957"
---
<!-- This article contains the exact baseline details for baseline versions that were previously published in security-baseline-settings-mdm.md.  -->

# <a name="archive-of-mdm-security-baseline-settings"></a>Archive des paramètres de ligne de base de sécurité de gestion des appareils mobiles  

Pour afficher les détails des versions archivées de la ligne de base de sécurité de gestion des appareils mobiles pour Intune.  

Lorsqu’une nouvelle ligne de base de sécurité de gestion des appareils mobiles libère, la liste précédente des paramètres déplacer à partir de l’article de paramètres de ligne de base de sécurité pour cette archive. Ces versions sont toujours pris en charge, et cette archive est fournie pour aider à comprendre les paramètres par défaut pour les anciennes versions de ligne de base.

Lorsqu’une version de référence n’est plus pris en charge pour une utilisation, il sera supprimé à partir de cet article.

- Afficher les paramètres qui sont disponibles dans [la ligne de base de sécurité actuel MDM](security-baseline-settings-mdm.md) 
- En savoir plus sur [bases de sécurité](security-baselines.md)et comment mettre à niveau la version de ligne de base dans vos profils de ligne de base de sécurité.

## <a name="preview-mdm-security-baseline-for-october-2018"></a>Préversion : base de référence de la sécurité GPM pour octobre 2018  

*Cette ligne de base est remplacé par [MDM Security Baseline pour Spring 2019 (19 H 1)](security-baseline-settings-mdm.md)*

### <a name="above-lock"></a>Au-dessus du verrouillage  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) dans la documentation Windows.  

- **Bloquer l’affichage des notifications toast**  
  Ce paramètre de stratégie vous permet d’empêcher les notifications des applications d’apparaître sur l’écran de verrouillage. Si vous activez ce paramètre de stratégie, aucune notification d’application ne s’affiche sur l’écran de verrouillage. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs peuvent choisir les applications qui affichent des notifications sur l’écran de verrouillage.
  
  **Par défaut** : Oui  

### <a name="app-runtime"></a>Runtime d’application  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) dans la documentation Windows.  

- **Comptes Microsoft facultatifs pour les applications du Windows Store**  
  Ce paramètre de stratégie vous permet de déterminer si les comptes Microsoft sont facultatifs pour les applications du Windows Store qui nécessitent un compte pour la connexion. Cette stratégie affecte uniquement les applications du Windows Store qui le prennent en charge. Si vous activez ce paramètre de stratégie, les applications du Windows Store qui nécessitent normalement un compte Microsoft pour la connexion autorisent les utilisateurs à se connecter avec un compte d’entreprise. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs doivent se connecter avec un compte Microsoft.  
  
  **Par défaut** : Activé  

### <a name="application-management"></a>Gestion des applications  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) dans la documentation Windows.  

- **Bloquer Jeux DVR (Desktop uniquement)**  
  Détermine si l’enregistrement et la diffusion des jeux sont autorisés ou non.
  
  **Par défaut** : oui  

### <a name="auto-play"></a>Lecture automatique  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) dans la documentation Windows.  

- **Comportement d’exécution automatique par défaut de la lecture automatique**  
  Ce paramètre affecte le comportement par défaut des commandes Autorun. Les commandes Autorun sont stockées dans des fichiers autorun.inf et peuvent lancer des programmes d’installation ou d’autres routines. Si ce paramètre est *activé*, les administrateurs peuvent changer le comportement d’Autorun par défaut sur un appareil qui exécute Windows Vista ou ultérieur. Le comportement peut : a) désactiver complètement les commandes Autorun, ou b) rétablir le comportement antérieur à Windows Vista qui consiste à exécuter automatiquement la commande Autorun. Si ce paramètre est *Désactivé* ou *Non configuré*, les appareils exécutant Windows Vista ou ultérieur demandent à l’utilisateur d’exécuter ou non la commande Autorun.
  
  **Par défaut** : ne pas exécuter  
  
- **Mode lecture automatique**  
  Ce paramètre de stratégie vous permet de désactiver la fonctionnalité de lecture automatique. La lecture automatique commence à lire le média d’un lecteur dès son insertion. Les fichiers d’installation des programmes et la musique des médias audio démarrent donc immédiatement. Avant Windows XP SP2, la lecture automatique était désactivée par défaut sur les lecteurs amovibles, tels que les lecteurs de disquettes (mais pas sur le lecteur de CD-ROM), ainsi que sur les lecteurs réseau. Depuis Windows XP SP2, la lecture automatique est également activée pour les lecteurs amovibles, notamment les lecteurs ZIP et certains périphériques de stockage de masse USB. Si vous activez ce paramètre de stratégie, vous désactivez la lecture automatique sur les lecteurs de CD-ROM et les lecteurs de médias amovibles, ou sur tous les lecteurs. Ce paramètre de stratégie désactive la lecture automatique sur les autres types de lecteurs. Vous ne pouvez pas utiliser ce paramètre pour activer la lecture automatique sur des lecteurs où elle est désactivée par défaut. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la lecture automatique est activée. Remarque : Ce paramètre de stratégie apparaît dans les dossiers Configuration ordinateur et Configuration utilisateur. Si les paramètres de stratégie sont en conflit, le paramètre de stratégie du dossier Configuration ordinateur a priorité sur le paramètre du dossier Configuration utilisateur.
  
  **Par défaut** : Désactivé

- **Bloquer la lecture automatique pour les périphériques autres que ceux du volume**  
  Ce paramètre de stratégie interdit la lecture automatique pour les périphériques MTP, tels que les appareils photo ou les téléphones. Si vous activez ce paramètre de stratégie, la lecture automatique est interdite pour les périphériques MTP, tels que les caméras ou les téléphones. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la lecture automatique est activée pour les périphériques autres que ceux du volume.
  
  **Par défaut** : Activé  

### <a name="bitlocker"></a>Bitlocker  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) dans la documentation Windows.  

- **Stratégie de lecteur amovible BitLocker**  
  Ce paramètre de stratégie permet de contrôler la méthode et le niveau de chiffrement. Les valeurs de cette stratégie déterminent la force du chiffrement utilisé par BitLocker pour le chiffrement. Les entreprises peuvent contrôler le niveau de chiffrement pour renforcer la sécurité (AES-256 est plus puissant que AES-128). Si vous activez ce paramètre, vous pouvez configurer un algorithme de chiffrement et la puissance de chiffrement clé pour les lecteurs de données fixes, les lecteurs de système d’exploitation et les lecteurs de données amovibles individuellement. Pour les lecteurs du système fixe et de fonctionnement, nous vous recommandons d’utiliser l’algorithme AES-XTS. Pour les lecteurs amovibles, vous devez utiliser AES-CBC 128 bits ou AES-CBC 256 bits si le lecteur est utilisé sur d’autres appareils qui n’exécutent pas la version 1511 de Windows 10 ou une version ultérieure. Le changement de la méthode de chiffrement est sans effet si le disque est déjà chiffré ou si le chiffrement est en cours. Dans ces cas, ce paramètre de stratégie est ignoré.

  Pour la stratégie de lecteur amovible BitLocker, configurez les paramètres suivants :

    - **Exiger le chiffrement pour l’accès en écriture**  
      **Par défaut** : oui  
  
    - **Méthode de chiffrement**  
      **Par défaut** : AES-CBC 256 bits  

- **Stratégie de lecteur fixe BitLocker**  
  Ce paramètre de stratégie permet de contrôler la méthode et le niveau de chiffrement. Les valeurs de cette stratégie déterminent la force du chiffrement utilisé par BitLocker pour le chiffrement. Les entreprises peuvent contrôler le niveau de chiffrement pour renforcer la sécurité (AES-256 est plus puissant que AES-128). Si vous activez ce paramètre, vous pouvez configurer un algorithme de chiffrement et la puissance de chiffrement clé pour les lecteurs de données fixes, les lecteurs de système d’exploitation et les lecteurs de données amovibles individuellement. Pour les lecteurs du système fixe et de fonctionnement, nous vous recommandons d’utiliser l’algorithme AES-XTS. Pour les lecteurs amovibles, vous devez utiliser AES-CBC 128 bits ou AES-CBC 256 bits si le lecteur est utilisé sur d’autres appareils qui n’exécutent pas la version 1511 de Windows 10 ou une version ultérieure. Le changement de la méthode de chiffrement est sans effet si le disque est déjà chiffré ou si le chiffrement est en cours. Dans ces cas, ce paramètre de stratégie est ignoré.  
 
   Pour la stratégie de lecteur fixe BitLocker, configurez les paramètres suivants : 
   - **Méthode de chiffrement**
     **par défaut**: AES-XTS 256 bits  

- **Stratégie de lecteur système BitLocker**  
  Ce paramètre de stratégie permet de contrôler la méthode et le niveau de chiffrement. Les valeurs de cette stratégie déterminent la force du chiffrement utilisé par BitLocker pour le chiffrement. Les entreprises peuvent contrôler le niveau de chiffrement pour renforcer la sécurité (AES-256 est plus puissant que AES-128). Si vous activez ce paramètre, vous pouvez configurer un algorithme de chiffrement et la puissance de chiffrement clé pour les lecteurs de données fixes, les lecteurs de système d’exploitation et les lecteurs de données amovibles individuellement. Pour les lecteurs du système fixe et de fonctionnement, nous vous recommandons d’utiliser l’algorithme AES-XTS. Pour les lecteurs amovibles, vous devez utiliser AES-CBC 128 bits ou AES-CBC 256 bits si le lecteur est utilisé sur d’autres appareils qui n’exécutent pas la version 1511 de Windows 10 ou une version ultérieure. Le changement de la méthode de chiffrement est sans effet si le disque est déjà chiffré ou si le chiffrement est en cours. Dans ces cas, ce paramètre de stratégie est ignoré.  

   Pour la stratégie de lecteur système BitLocker, configurez les paramètres suivants :
  - **Méthode de chiffrement**  
    **Par défaut** : AES-CBC 256 bits  

### <a name="browser"></a>Navigateur  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) dans la documentation Windows.  

- **Exiger SmartScreen pour Microsoft Edge**  

  Microsoft Edge utilise Windows Defender SmartScreen (activé) pour protéger les utilisateurs contre d’éventuels courriers indésirables d’hameçonnage et logiciels malveillants par défaut. Par ailleurs, les utilisateurs ne peuvent pas désactiver Windows Defender SmartScreen par défaut. L’activation de cette stratégie désactive Windows Defender SmartScreen et empêche les utilisateurs de l’activer. Ne configurez pas cette stratégie pour permettre aux utilisateurs de choisir d’activer ou non Windows Defender SmartScreen.  
  
  **Par défaut** : oui  
  
- **Bloquer l’accès aux sites malveillants**  

  Par défaut, Microsoft Edge permet aux utilisateurs de contourner (ignorer) les avertissements de Windows Defender SmartScreen relatifs aux fichiers potentiellement malveillants, leur permettant ainsi d’accéder au site. Toutefois, avec cette stratégie, vous pouvez configurer Microsoft Edge de manière à empêcher les utilisateurs de contourner les avertissements, les empêchant ainsi d’accéder au site.
  
  **Par défaut** : oui  
  
- **Télécharger des fichiers de bloc non vérifiés** Par défaut, Microsoft Edge permet aux utilisateurs de contourner (ignorer) les avertissements de Windows Defender SmartScreen relatifs aux fichiers potentiellement malveillants, leur permettant ainsi de continuer à télécharger le ou les fichiers non vérifiés. L’activation de cette stratégie empêche les utilisateurs de contourner les avertissements, ce qui leur interdit de télécharger le ou les fichiers non vérifiés.
  
  **Par défaut** : oui  
  
- **Bloquer le gestionnaire de mots de passe**  
  Par défaut, Microsoft Edge utilise automatiquement le gestionnaire de mots de passe, ce qui permet aux utilisateurs de gérer leurs mots de passe localement. Si vous désactivez cette stratégie, Microsoft Edge ne peut pas utiliser le gestionnaire de mots de passe. Si vous ne configurez pas cette stratégie, les utilisateurs peuvent choisir d’enregistrer et de gérer leurs mots de passe localement à l’aide du gestionnaire de mots de passe.
  
  **Par défaut** : oui  
  
- **Empêcher les utilisateurs de passer outre les erreurs de certificat**  
  Ce paramètre de stratégie empêche l’utilisateur d’ignorer les erreurs de certificat SSL/TLS (Secure Sockets Layer/Transport Layer Security) qui interrompent la navigation, telles que les erreurs relatives à l’expiration, à la révocation ou à une incohérence au niveau des noms dans Internet Explorer. Si vous activez ce paramètre de stratégie, l’utilisateur ne peut pas poursuivre la navigation. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut choisir d’ignorer les erreurs de certificat et poursuivre la navigation.
  
  **Par défaut** : oui  

### <a name="connectivity"></a>Connectivité  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) dans la documentation Windows.  

- **Bloquer le téléchargement à partir d’Internet pour les Assistants Publication de sites web et Commande en ligne**  
  Ce paramètre de stratégie indique si Windows doit télécharger une liste de fournisseurs pour les Assistants Publication de sites web et Commande en ligne. Ces Assistants permettent aux utilisateurs de choisir parmi une liste de sociétés offrant des services de stockage et d’impression photographique en ligne. Par défaut, Windows affiche les fournisseurs téléchargés à partir d’un site web Windows, en plus des fournisseurs spécifiés dans le Registre. Si vous activez ce paramètre de stratégie, Windows ne télécharge pas les fournisseurs, et seuls les fournisseurs de services mis en cache dans le Registre local sont affichés. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, une liste de fournisseurs est téléchargée lorsque l’utilisateur utilise les Assistants Publication de sites web ou Commande en ligne. Pour plus d’informations, consultez la documentation des Assistants Publication de sites web et Commande en ligne, notamment sur la façon de spécifier les fournisseurs de services dans le Registre.  
  
  **Par défaut** : Activé  

- **Bloquer le téléchargement des pilotes d’imprimantes sur HTTP**  
  Ce paramètre de stratégie indique si ce client est autorisé à télécharger les packages de pilotes d’imprimantes sur HTTP. Pour configurer l’impression HTTP, les pilotes non fournis avec Windows doivent être téléchargés sur HTTP. Remarque : Ce paramètre de stratégie n’empêche pas le client d’imprimer sur des imprimantes du réseau intranet ou Internet sur HTTP. Il empêche uniquement le téléchargement des pilotes qui ne sont pas déjà installés localement. Si vous activez ce paramètre de stratégie, il est impossible de télécharger les pilotes d’imprimantes sur HTTP. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs peuvent télécharger des pilotes d’imprimantes sur HTTP.
  
  **Par défaut** : Activé  

### <a name="credentials-delegation"></a>Délégation des informations d’identification  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) dans la documentation Windows.  

- **Délégation par l’hôte distant d’informations d’identification non exportables**  
  L’hôte distant autorise la délégation d’informations d’identification non exportables. Lorsque vous utilisez la délégation des informations d’identification, les appareils fournissent une version exportable d’informations d’identification à l’hôte distant, ce qui expose les utilisateurs à un risque de vol des informations d’identification par des attaquants sur l’hôte distant. Si vous activez ce paramètre de stratégie, l’hôte prend en charge le mode d’administration restreinte ou Credential Guard à distance. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les modes Administration restreinte et Credential Guard à distance ne sont pas pris en charge. L’utilisateur devra toujours passer ses informations d’identification à l’hôte.  

  
  **Par défaut** : Activé  

### <a name="credentials-ui"></a>Informations d’identification de l’interface utilisateur  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) dans la documentation Windows.  

- **Énumérer les administrateurs** Ce paramètre de stratégie détermine si les comptes Administrateur s’affichent lorsqu’un utilisateur tente d’élever une application en cours d’exécution. Par défaut, les comptes Administrateur ne s’affichent pas lorsque l’utilisateur tente d’élever une application en cours d’exécution. Si vous activez ce paramètre de stratégie, tous les comptes Administrateur locaux du PC s’affichent pour permettre à l’utilisateur d’en choisir un et d’entrer le mot de passe correspondant. Si vous désactivez ce paramètre de stratégie, les utilisateurs devront toujours entrer un nom d’utilisateur et un mot de passe pour avoir des privilèges élevés.  

  
  **Par défaut** : Désactivé  

### <a name="data-protection"></a>Protection des données  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) dans la documentation Windows.  

- **Bloquer l’accès direct à la mémoire**  
  Ce paramètre de stratégie vous permet de bloquer l’accès direct à la mémoire (DMA) pour tous les ports en aval PCI enfichables à chaud tant que l’utilisateur ne se connecte pas à Windows. Une fois l’utilisateur connecté, Windows énumère les périphériques PCI connectés aux ports PCI enfichables à chaud. À chaque verrouillage de l’ordinateur par l’utilisateur, l’Assistant Migration de données Microsoft est bloqué sur les ports PCI enfichables à chaud sans périphériques enfants, tant que l’utilisateur ne se reconnecte pas. Les périphériques déjà énumérés quand l’ordinateur a été déverrouillé continuent de fonctionner tant qu’ils sont branchés. Ce paramètre de stratégie est appliqué uniquement quand BitLocker ou le chiffrement de l’appareil est activé.
  
  
  **Par défaut** : oui  

### <a name="device-guard"></a>Device Guard  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) dans la documentation Windows.  

- **Credential Guard**  
  Ce paramètre permet aux utilisateurs d’activer Credential Guard avec la sécurité basée sur la virtualisation pour protéger les informations d’identification au prochain redémarrage.
   
  **Par défaut** : activer avec le verrouillage UEFI 

- **Activer la sécurité basée sur la virtualisation**  </br>
  Active la sécurité basée sur la virtualisation au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité.
  
  **Par défaut** : oui  

- **Lancer System Guard**    
  **Par défaut** : Activé  

### <a name="device-installation"></a>Installation de l’appareil  

Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) dans la documentation Windows.  

- **Installation de périphériques matériels par identificateurs d’appareil**  
  Ce paramètre de stratégie permet de spécifier une liste d’ID de matériel Plug-and-Play et d’ID compatibles de périphériques que Windows ne peut pas installer. Ce paramètre de stratégie prévaut sur tout autre paramètre de stratégie autorisant l’installation de périphériques par Windows. Si vous activez ce paramètre de stratégie, Windows n’est pas autorisé à installer un périphérique dont l’ID de matériel ou l’ID compatible figure dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur Bureau à distance, il a une incidence sur la redirection des périphériques spécifiés à partir d’un client Bureau à distance vers le serveur Bureau à distance. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, des périphériques peuvent être installés et mis à jour conformément aux autorisations ou interdictions prévues par d’autres paramètres de stratégie.
  
  **Par défaut** : Bloquer l’installation de périphériques matériels  

    Lorsque la case *Bloquer l’installation du périphérique matériel* est sélectionnée, les paramètres suivants sont disponibles.
  
    - **Supprimer les périphériques matériels correspondants**   
    Ce paramètre est disponible uniquement quand *Installation de périphériques matériels par identificateurs d’appareil* a la valeur *Bloquer l’installation de périphériques matériels*.
      
      **Par défaut** : oui
  
    - **Identificateurs de périphériques matériels bloqués**  
       Ce paramètre est disponible uniquement quand *Installation de périphériques matériels par identificateurs d’appareil* a la valeur *Bloquer l’installation de périphériques matériels*.
      
      **Par défaut** : oui  
  
- **Installation de périphériques matériels par classes d’installation**  
  Ce paramètre de stratégie permet de spécifier une liste de GUID de classe d’installation de périphériques décrivant les pilotes de périphériques que Windows ne peut pas installer. Ce paramètre de stratégie prévaut sur tout autre paramètre de stratégie autorisant l’installation de périphériques par Windows. Si vous activez ce paramètre, Windows ne peut pas installer ou mettre à jour les pilotes de périphériques dont les GUID de classe d’installation de périphériques figurent dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur Bureau à distance, il a une incidence sur la redirection des périphériques spécifiés à partir d’un client Bureau à distance vers le serveur Bureau à distance. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, Windows peut installer ou mettre à jour des périphériques conformément aux autorisations ou interdictions prévues par d’autres paramètres de stratégie.
  
  **Par défaut** : Bloquer l’installation de périphériques matériels  

    Lorsque la case *Bloquer l’installation du périphérique matériel* est sélectionnée, les paramètres suivants sont disponibles.
    - **Supprimer les périphériques matériels correspondants**    
    Ce paramètre est disponible seulement quand *Installation de périphériques matériels par classes d’installation* est défini sur *Bloquer l’installation de périphériques matériels*.  

      **Par défaut** : *Aucune configuration par défaut*  
  
    - **Identificateurs de périphériques matériels bloqués**  
      Ce paramètre est disponible seulement quand *Installation de périphériques matériels par classes d’installation* est défini sur *Bloquer l’installation de périphériques matériels*.
      
      **Par défaut** : *Aucune configuration par défaut*  

### <a name="device-lock"></a>Verrouillage d’appareil  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) dans la documentation Windows.  

- **Empêcher l’utilisation de l’appareil photo**  
  Désactive le commutateur de verrouillage de l’appareil photo sur l’écran dans Paramètres du PC et empêche l’appel de l’appareil photo sur l’écran de verrouillage. Par défaut, les utilisateurs peuvent activer l’appel d’une caméra disponible sur l’écran de verrouillage. Si vous activez ce paramètre, les utilisateurs ne sont plus en mesure d’activer ou de désactiver l’accès de la caméra sur l’écran de verrouillage dans Paramètres du PC, et la caméra ne peut pas être appelée sur l’écran de verrouillage. 
  
  **Par défaut** : Activé  

- **Exiger un mot de passe**  
  Spécifie si le verrouillage de l’appareil est activé.
  
  **Par défaut** : oui  
  
    Lorsque *Mot de passe requis* est défini sur *Oui*, les paramètres suivants sont disponibles.

    - **Nombre minimal de jeux de caractères du mot de passe**  
      Nombre de types d’éléments complexes (lettres majuscules et minuscules, chiffres et ponctuation) obligatoires pour un mot de passe ou un code PIN fort. Le PIN impose le comportement suivant aux appareils de bureau et mobiles : 1 - Chiffres uniquement 2 - Chiffres et lettres majuscules obligatoires 3 - Chiffres, lettres majuscules et lettres minuscules obligatoires. Non pris en charge dans les comptes Microsoft et les comptes de domaine des postes de travail. 4 : Chiffres, lettres minuscules, lettres majuscules et caractères spéciaux obligatoires. Non pris en charge sur les postes de travail. La valeur par défaut est 1. 
      
      **Par défaut** : 3  
  
    - **Nombre d’échecs de connexion avant réinitialisation de l’appareil**  
      Le nombre d’échecs d’authentification autorisé avant la réinitialisation de l’appareil. La valeur 0 désactive la fonctionnalité de réinitialisation de l’appareil.
        
      **Par défaut** : 10  
  
    - **Expiration du mot de passe (jours)**  
      Le paramètre de stratégie Antériorité maximale du mot de passe détermine la période (en jours) pendant laquelle un mot de passe peut être utilisé avant que le système oblige l’utilisateur à le changer. Vous pouvez définir l’expiration des mots de passe après un nombre de jours compris entre 1 et 999, ou vous pouvez spécifier que les mots de passe n’expirent jamais en définissant le nombre de jours sur 0. Si Antériorité maximale du mot de passe est compris entre 1 et 999 jours, l’antériorité minimale du mot de passe doit être inférieure à son antériorité maximale. Si Antériorité maximale du mot de passe est défini sur 0, Antériorité minimale du mot de passe peut avoir une valeur comprise entre 0 et 998 jours.
      
      **Par défaut** : 60  
  
    - **Type de mot de passe requis**  
      Détermine le type de code PIN ou de mot de passe exigé.
      
      **Par défaut** : alphanumérique  
  
    - **Longueur minimale du mot de passe**  
      Le paramètre de stratégie Longueur minimale du mot de passe détermine le plus petit nombre de caractères qui peuvent constituer un mot de passe pour un compte d’utilisateur. Vous pouvez définir une valeur comprise entre 1 et 14 caractères, ou vous pouvez établir qu’aucun mot de passe n’est exigé en définissant le nombre de caractères sur 0.
      
      **Par défaut** : 8  
  
    - **Bloquer les mots de passe simples**  
      Spécifie si les codes PIN ou les mots de passe comme « 1111 » ou « 1234 » sont autorisés. Pour le poste de travail, il contrôle également l’utilisation de mots de passe image.
      
      **Par défaut** : oui  
        *La valeur Oui empêche l’utilisation de mots de passe simples.* 

  - **Empêcher la réutilisation des mots de passe précédents**  
    Spécifie le nombre de mots de passe à stocker dans l’historique des mots de passe qui ne peuvent pas être utilisés. Ceci comprend le mot de passe actuel de l’utilisateur. Par exemple, avec un paramètre de *1* l’utilisateur ne peut pas réutiliser son mot de passe actuel lors du choix d’un nouveau mot de passe. Un paramètre de *5* signifie qu’un utilisateur ne peut pas définir son nouveau mot de passe sur leur mot de passe actuel ni l’un de ses quatre mots de passe précédents.
    
    **Par défaut** : 24  

- **Empêcher le diaporama**  
  Désactive les paramètres de diaporama de l’écran de verrouillage dans Paramètres du PC et empêche l’affichage d’un diaporama sur l’écran de verrouillage. Par défaut, les utilisateurs peuvent activer un diaporama qui s’exécute après avoir verrouillé l’ordinateur. Si vous activez ce paramètre, les utilisateurs ne peuvent plus modifier les paramètres du diaporama dans Paramètres du PC et aucun diaporama ne peut démarrer.
  
    **Par défaut** : Activé  
    *La valeur Activé empêche l’exécution des diaporamas.* 

- **Antériorité minimale du mot de passe en jours**  
  Le paramètre de stratégie Antériorité minimale du mot de passe détermine la période (en jours) pendant laquelle un mot de passe doit être utilisé avant que l’utilisateur puisse le changer. Vous pouvez définir une valeur comprise entre 1 et 998 jours, ou vous pouvez autoriser les changements de mot de passe immédiatement en définissant le nombre de jours sur 0. L’antériorité minimale du mot de passe doit être inférieure à l’antériorité maximale du mot de passe, sauf si celle-ci est définie sur 0, indiquant que les mots de passe n’expirent jamais. Si l’antériorité maximale du mot de passe est définie sur 0, l’antériorité minimale du mot de passe peut avoir une valeur comprise entre 0 et 998.
  
    **Par défaut** : 1  

### <a name="event-log-service"></a>Service Journal des événements  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) dans la documentation Windows.  

- **Taille de fichier maximale du journal de sécurité en Ko**  
  Ce paramètre de stratégie spécifie la taille maximale du fichier journal en Ko. Si vous activez ce paramètre de stratégie, vous pouvez configurer la taille maximale du fichier journal à une valeur comprise entre 1 Mo (1 024 Ko) et 2 To (2 147 483 647 Ko), par incréments d’un Ko. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la taille maximale du fichier journal est définie sur la valeur configurée localement. L’administrateur local peut changer cette valeur via la boîte de dialogue Propriétés du journal ; sa valeur par défaut est de 20 Mo.
  
   **Par défaut** : 196608  

- **Taille de fichier maximale du journal système en Ko**  
  Ce paramètre de stratégie spécifie la taille maximale du fichier journal en Ko. Si vous activez ce paramètre de stratégie, vous pouvez configurer la taille maximale du fichier journal à une valeur comprise entre 1 Mo (1 024 Ko) et 2 To (2 147 483 647 Ko), par incréments d’un Ko. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la taille maximale du fichier journal est définie sur la valeur configurée localement. L’administrateur local peut changer cette valeur via la boîte de dialogue Propriétés du journal ; sa valeur par défaut est de 20 Mo.
  
  **Par défaut** : 32768  

- **Taille de fichier maximale du journal des applications en Ko**  
  Ce paramètre de stratégie spécifie la taille maximale du fichier journal en Ko. Si vous activez ce paramètre de stratégie, vous pouvez configurer la taille maximale du fichier journal à une valeur comprise entre 1 Mo (1 024 Ko) et 2 To (2 147 483 647 Ko), par incréments d’un Ko. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la taille maximale du fichier journal est définie sur la valeur configurée localement. L’administrateur local peut changer cette valeur via la boîte de dialogue Propriétés du journal ; sa valeur par défaut est de 20 Mo.
  
  **Par défaut** : 32768  

### <a name="experience"></a>Expérience  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Expérience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) dans la documentation Windows.  

- **Bloquer Windows à la une**  
  Permet aux administrateurs informatiques de désactiver toutes les fonctionnalités de Windows à la une : Windows à la une sur l’écran de verrouillage, Conseils Windows, les fonctionnalités Microsoft grand public et d’autres fonctionnalités associées.
  
  **Par défaut** : oui  

  Lorsque *Bloquer les informations à la une Windows* est défini sur *Oui*, les paramètres suivants sont disponibles.
  
  - **Bloquer les suggestions de tiers dans Windows à la une**  
    Spécifie s’il faut autoriser les suggestions d’applications et de contenu provenant d’éditeurs de logiciels tiers dans les fonctionnalités de Windows à la une, comme la une sur l’écran de verrouillage, les applications suggérées dans le menu Démarrer et les conseils Windows. Les utilisateurs peuvent quand même voir les suggestions de fonctionnalités, d’applications et de services Microsoft.
      
    **Par défaut** : oui  
   - **Bloquer les fonctionnalités spécifiques au grand public**  
      Permet aux administrateurs informatiques d’activer les fonctionnalités destinées au grand public uniquement, comme les suggestions du démarrage, les notifications d’appartenance, l’installation d’application post-OOBE et les vignettes de redirection.
      
     **Par défaut** : oui  


### <a name="exploit-guard"></a>Exploit Guard  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) dans la documentation Windows.  

- **Protection contre le code malveillant XML**  
  Permet à l’administrateur informatique de diffuser une configuration qui représente les options souhaitées d’atténuation des risques pour le système et les applications auprès de tous les appareils de l’organisation. La configuration est représentée par du code XML. Exploit Protection aide à protéger les appareils contre les programmes malveillants qui utilisent du code malveillant exploitant une faille de sécurité pour se propager et les infecter. Utilisez l’application Sécurité Windows ou PowerShell pour créer un ensemble d’atténuations des risques (qui est appelé « configuration »). Vous pouvez ensuite exporter cette configuration dans un fichier XML et le partager sur plusieurs machines de votre réseau pour donner à toutes le même ensemble de paramètres d’atténuation des risques. Vous pouvez aussi convertir et importer un fichier XML de configuration EMET existant en un fichier XML de configuration de protection contre le code malveillant.
  
  **Par défaut** : *un exemple de code XML est fourni* 
 
### <a name="file-explorer"></a>Explorateur de fichiers  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) dans la documentation Windows.  

- **Bloquer la prévention de l’exécution des données**  
  La désactivation de la prévention de l’exécution des données peut permettre à certaines applications de plug-in héritées de fonctionner sans arrêter l’Explorateur.
  
  **Par défaut** : Désactivé  
   
- **Bloquer l’arrêt du tas en cas de défaillance**  
  La désactivation de l’arrêt du tas en cas de défaillance peut permettre à certaines applications de plug-in héritées de fonctionner sans arrêter immédiatement l’Explorateur, même si l’Explorateur peut néanmoins s’arrêter ultérieurement de façon inattendue.
  
  **Par défaut** : Désactivé  
    

### <a name="internet-explorer"></a>Internet Explorer  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) dans la documentation Windows.  

- **Internet Explorer > Zone Internet : accès aux sources de données**  
  Ce paramètre de stratégie vous permet d’indiquer si Internet Explorer peut accéder aux données provenant d’une autre zone de sécurité en utilisant le moteur d’analyse XML de Microsoft (MSXML) ou les objets ADO (ActiveX Data Objects). Si vous activez ce paramètre de stratégie, les utilisateurs peuvent charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement d’une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Faire glisser du contenu provenant de domaines différents dans les fenêtres**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs ne peuvent pas modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs ne peuvent pas modifier ce paramètre dans la boîte de dialogue Options Internet.
  
  **Par défaut** : Désactivé
  
- **Internet Explorer : Avertissement de non-correspondance d’adresse de certificat**  
  Ce paramètre de stratégie vous permet d’activer l’avertissement de sécurité de non-correspondance d’adresse de certificat. Quand ce paramètre de stratégie est activé, l’utilisateur est averti lors de la visite de sites web HTTP sécurisé (HTTPS) qui présentent des certificats émis pour une autre adresse de site web. Cet avertissement permet d’empêcher les attaques par usurpation d’identité. Si vous activez ce paramètre de stratégie, l’avertissement de non-correspondance d’adresse de certificat apparaît toujours. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut choisir d’afficher l’avertissement de non-correspondance d’adresse de certificat (en utilisant la page Avancé du Panneau de configuration Internet).
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone restreinte : Sites de moindre privilège**  
  Ce paramètre de stratégie vous permet de spécifier si des sites web de zones de moindre privilège, comme des sites Internet, peuvent accéder à cette zone. Si vous activez ce paramètre de stratégie, les sites web des zones de moindre privilège peuvent ouvrir de nouvelles fenêtres dans cette zone ou y accéder. La zone de sécurité fonctionne sans la couche de sécurité supplémentaire qui est fournie par la fonctionnalité Protection contre l’élévation de zone. Si vous sélectionnez Demander dans la zone de liste déroulante, l’utilisateur est averti qu’un accès potentiellement risqué est sur le point de se produire. Si vous désactivez ce paramètre de stratégie, les accès potentiellement dangereux sont empêchés. La fonctionnalité de sécurité d’Internet Explorer est activée sur cette zone comme défini par le contrôle de la fonctionnalité Protection contre l’élévation de zone. Si vous ne configurez pas ce paramètre de stratégie, les accès potentiellement dangereux sont empêchés. La fonctionnalité de sécurité d’Internet Explorer est activée sur cette zone comme défini par le contrôle de la fonctionnalité Protection contre l’élévation de zone.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Demande automatique pour les téléchargements de fichiers**  
  Ce paramètre de stratégie détermine si les utilisateurs sont invités à autoriser les téléchargements de fichiers qu’ils n’ont pas eux-mêmes demandés. Quelle que soit la valeur de ce paramètre, des boîtes de dialogue de téléchargement de fichier sont montrées aux utilisateurs pour les téléchargements demandés par eux-mêmes. Si vous activez ce paramètre, une boîte de dialogue de téléchargement de fichier est montrée aux utilisateurs pour les tentatives de téléchargement automatique. Si vous désactivez ce paramètre ou ne le configurez pas, les téléchargements de fichiers qui ne sont pas demandés par les utilisateurs sont bloqués, et les utilisateurs voient la barre de notification au lieu de la boîte de dialogue de téléchargement de fichier. Les utilisateurs peuvent alors cliquer sur la barre de notification pour voir l’invite de téléchargement de fichier.
  
  **Par défaut** : Désactivé
  
- **Internet Explorer > Zone Internet : Composants dépendant du .NET Framework**  
  Ce paramètre de stratégie vous permet d’indiquer si les composants .NET Framework non signés avec Authenticode peuvent s’exécuter dans Internet Explorer. Ces composants incluent les contrôles managés référencés par une balise objet et les exécutables managés référencés à partir d’un lien. Si vous activez ce paramètre de stratégie, Internet Explorer exécute les composants managés non signés. Si vous sélectionnez Demander dans la liste déroulante, Internet Explorer demande aux utilisateurs s’ils souhaitent exécuter les composants managés non signés. Si vous désactivez ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés non signés. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer exécute les composants managés non signés.
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Zone Internet : Autoriser uniquement les domaines approuvés à utiliser le contrôle ActiveX TDC**  
  Ce paramètre de stratégie contrôle si l’utilisateur est ou non autorisé à exécuter le contrôle ActiveX TDC sur des sites web. Si vous activez ce paramètre de stratégie, le contrôle ActiveX TDC n’est pas exécuté sur les sites web de cette zone. Si vous désactivez ce paramètre de stratégie, le contrôle ActiveX TDC s’exécute sur tous les sites de cette zone.
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone restreinte : Fenêtres lancées par des scripts**  
  Ce paramètre de stratégie permet de gérer les restrictions sur les fenêtres indépendantes lancées par des scripts, et sur celles qui incluent les barres de titre et d’état. Si vous activez ce paramètre de stratégie, la fonctionnalité de sécurité des Restrictions des fenêtres ne s’applique pas à cette zone. La zone de sécurité s’exécute sans la couche de sécurité supplémentaire fournie par cette fonctionnalité. Si vous désactivez ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts. Si vous ne configurez pas ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts.
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Internet : Inclure le chemin local lors du chargement de fichiers sur un serveur**  
  Ce paramètre de stratégie spécifie si les informations du chemin d’accès local sont envoyées ou non lorsque l’utilisateur charge un fichier via un formulaire HTML. Si les informations de chemin local sont envoyées, certaines informations peuvent être involontairement révélées au serveur. Par exemple, des fichiers envoyés à partir du Bureau de l’utilisateur peuvent avoir un chemin contenant le nom de l’utilisateur. Si vous activez ce paramètre de stratégie, les informations de chemin sont envoyées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous désactivez ce paramètre de stratégie, les informations de chemin sont supprimées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si les informations du chemin d’accès sont envoyées lorsqu’il charge un fichier via un formulaire HTML. Par défaut, les informations de chemin sont envoyées.
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Désactiver les processus en mode protégé amélioré**  
  Ce paramètre de stratégie détermine si Internet Explorer 11 utilise des processus 64 bits (pour une sécurité renforcée) ou des processus 32 bits (pour une meilleure compatibilité) lors de l’exécution en mode protégé amélioré sur les versions 64 bits de Windows. Important : Certains contrôles ActiveX et certaines barres d’outils risquent de ne pas être disponibles lorsque des processus 64 bits sont utilisés. Si vous activez ce paramètre de stratégie, Internet Explorer 11 utilise des processus d’onglet 64 bits lors de l’exécution en mode protégé amélioré sur les versions 64 bits de Windows. Si vous désactivez ce paramètre de stratégie, Internet Explorer 11 utilise des processus d’onglet 32 bits lors de l’exécution en mode protégé amélioré sur les versions 64 bits de Windows. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs peuvent activer ou désactiver cette fonctionnalité via les paramètres d’Internet Explorer. Cette fonctionnalité est désactivée par défaut.
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Ignorer les erreurs de certificat**  
  Ce paramètre de stratégie empêche l’utilisateur d’ignorer les erreurs de certificat SSL/TLS (Secure Sockets Layer/Transport Layer Security) qui interrompent la navigation, telles que les erreurs relatives à l’expiration, à la révocation ou à une incohérence au niveau des noms dans Internet Explorer. Si vous activez ce paramètre de stratégie, l’utilisateur ne peut pas poursuivre la navigation. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut choisir d’ignorer les erreurs de certificat et poursuivre la navigation.
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Internet : Chargement des fichiers XAML**  
  Ce paramètre de stratégie vous permet de gérer le chargement des fichiers XAML (Extensible Application Markup Language). Le langage XAML est un langage de balisage déclaratif basé sur le langage XML et couramment utilisé pour la création d’interfaces utilisateur et de graphismes avancés qui tirent parti de Windows Presentation Foundation. Si vous activez ce paramètre de stratégie et si vous affectez la valeur Activer à la zone de liste déroulante, les fichiers XAML sont automatiquement chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous affectez la valeur Demander à la zone de liste déroulante, l’utilisateur est invité à confirmer le chargement des fichiers XAML. Si vous désactivez ce paramètre de stratégie, les fichiers XAML ne sont pas chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur est libre de charger ou non les fichiers XAML dans Internet Explorer.
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Zone Internet : Demande automatique pour les téléchargements de fichiers**  
  Ce paramètre de stratégie détermine si les utilisateurs sont invités à autoriser les téléchargements de fichiers qu’ils n’ont pas eux-mêmes demandés. Quelle que soit la valeur de ce paramètre, des boîtes de dialogue de téléchargement de fichier sont montrées aux utilisateurs pour les téléchargements demandés par eux-mêmes. Si vous activez ce paramètre, une boîte de dialogue de téléchargement de fichier est montrée aux utilisateurs pour les tentatives de téléchargement automatique. Si vous désactivez ce paramètre ou ne le configurez pas, les téléchargements de fichiers qui ne sont pas demandés par les utilisateurs sont bloqués, et les utilisateurs voient la barre de notification au lieu de la boîte de dialogue de téléchargement de fichier. Les utilisateurs peuvent alors cliquer sur la barre de notification pour voir l’invite de téléchargement de fichier.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Avertissement de sécurité pour les fichiers potentiellement dangereux**  
  Ce paramètre de stratégie détermine si le message « Fichier ouvert : Avertissement de sécurité » s’affiche lorsque l’utilisateur essaie d’ouvrir des fichiers exécutables ou d’autres fichiers potentiellement non sécurisés (à partir d’un partage de fichiers intranet via l’Explorateur de fichiers, par exemple). Si vous activez ce paramètre de stratégie et affectez la valeur Activer à la zone de liste déroulante, les fichiers concernés s’ouvrent sans avertissement de sécurité préalable. Si vous affectez la valeur Demander à la zone de liste déroulante, un avertissement de sécurité s’affiche avant l’ouverture des fichiers. Si vous désactivez ce paramètre de stratégie, les fichiers concernés ne s’ouvrent pas. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut configurer la façon dont l’ordinateur gère ces fichiers. Par défaut, ces fichiers sont bloqués dans la zone restreinte, activés dans les zones Intranet et Ordinateur local, et définis sur Demander dans les zones Internet et de confiance.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Filtre anti-script de site à site**  
  Cette stratégie détermine si le filtre anti-script de site à site (XSS) détecte et évite les injections de script de site à site dans les sites web de cette zone. Si vous activez ce paramètre de stratégie, le filtre XSS est activé pour les sites de cette zone et tente de bloquer les injections de script de site à site. Si vous désactivez ce paramètre de stratégie, le filtre XSS est désactivé pour les sites de cette zone et Internet Explorer autorise les injections de script de site à site.
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Recours à SSL3**  
  Ce paramètre de stratégie vous permet de bloquer tout recours non sécurisé à SSL 3.0. Lorsque cette stratégie est activée, Internet Explorer tente de se connecter aux sites à l’aide de SSL 3.0 ou version antérieure lorsque TLS 1.0 ou version supérieure échoue. Nous vous recommandons de ne pas autoriser le recours non sécurisé afin d’empêcher les attaques de l’intercepteur. Cette stratégie n’a pas d’impact sur l’activation des protocoles de sécurité. Si vous désactivez cette stratégie, les paramètres système par défaut seront utilisés.
  
  **Par défaut** : aucun site 
  
- **Internet Explorer > Zone Internet verrouillée : SmartScreen**  
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone restreinte : Lancer les applications et les fichiers dans un iFrame**  
  Ce paramètre de stratégie permet d’indiquer si les applications peuvent s’exécuter et les fichiers être téléchargés depuis une référence IFRAME dans le code source HTML des pages de cette zone. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les applications et télécharger des fichiers depuis des IFRAME sans entrer de confirmation. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent exécuter des applications et télécharger des fichiers depuis des IFRAME des pages de cette zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter d’applications, ni télécharger des fichiers depuis les IFRAME des pages de cette zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter d’applications ni télécharger des fichiers depuis les IFRAME des pages de cette zone.
  
  **Par défaut**: désactiver 
  
- **Internet Explorer : ignorer les avertissements SmartScreen relatifs aux fichiers rares**  
  Ce paramètre de stratégie détermine si l’utilisateur peut ignorer les avertissements du filtre SmartScreen. Le filtre SmartScreen avertit l’utilisateur au sujet des fichiers exécutables que les utilisateurs d’Internet Explorer ne téléchargent généralement pas à partir d’Internet. Si vous activez ce paramètre de stratégie, les avertissements du filtre SmartScreen bloquent l’utilisateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut ignorer les avertissements du filtre SmartScreen.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : Bloqueur de fenêtres publicitaires**  
  Ce paramètre de stratégie permet d’indiquer si les fenêtres publicitaires s’affichent. Les fenêtres indépendantes qui sont ouvertes lorsque l’utilisateur final clique sur un lien ne sont pas bloquées. Si vous activez ce paramètre de stratégie, la plupart des fenêtres publicitaires sont bloquées. Si vous désactivez ce paramètre de stratégie, les fenêtres indépendantes ne sont pas bloquées. Si vous ne configurez pas ce paramètre de stratégie, la plupart des fenêtres indépendantes non désirées ne s’afficheront pas.
  
  **Par défaut** : activer  
  
- **Processus Internet Explorer > Gestion MIME cohérente**  
  Internet Explorer contient des comportements binaires dynamiques : les composants qui intègrent une fonctionnalité spécifique pour les éléments HTML auxquels ils sont attachés. Ce paramètre de stratégie indique si le paramètre Restriction de sécurité de comportement binaire est bloqué ou autorisé. Ce paramètre de stratégie permet aux administrateurs d’indiquer les applications pour lesquelles ils souhaitent bloquer ou activer cette fonctionnalité de sécurité. Si vous désactivez ce paramètre de stratégie, les comportements binaires sont autorisés dans les processus de l’Explorateur de fichiers et d’Internet Explorer. Si vous ne configurez pas ce paramètre de stratégie, les comportements binaires sont bloqués dans les processus de l’Explorateur de fichiers et d’Internet Explorer.
  
  **Par défaut** : Activé  
  
- **Internet Explorer : autorisations Java des zones restreintes**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.
  
  **Par défaut**: désactiver Java  
    
  
- **Internet Explorer > Contrôles ActiveX en mode protégé**  
  Ce paramètre de stratégie empêche l’exécution des contrôles ActiveX en mode protégé lorsque le mode protégé amélioré est activé. Lorsqu’un utilisateur a un contrôle ActiveX installé qui n’est pas compatible avec le mode protégé amélioré et qu’un site web tente de charger le contrôle, Internet Explorer avertit l’utilisateur et lui donne la possibilité d’exécuter le site web en mode protégé normal. Ce paramètre de stratégie désactive cette notification et force l’exécution de tous les sites Web en mode protégé amélioré. Le mode protégé amélioré renforce la protection contre les sites Web malveillants en utilisant des processus 64 bits sur des versions 64 bits de Windows. Pour les ordinateurs qui exécutent Windows 8 ou version ultérieure, le mode protégé amélioré limite également les emplacements à partir desquels Internet Explorer peut lire dans le Registre et le système de fichiers. Lorsque le mode protégé amélioré est activé et qu’un utilisateur rencontre un site web qui tente de charger un contrôle ActiveX qui n’est pas compatible avec le mode protégé amélioré, Internet Explorer avertit l’utilisateur et lui donne la possibilité de désactiver le mode protégé amélioré pour ce site web spécifique. Si vous activez ce paramètre de stratégie, Internet Explorer ne donne pas à l’utilisateur la possibilité de désactiver le mode protégé amélioré. Tous les sites Web en mode protégé sont exécutés en mode protégé amélioré. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, Internet Explorer avertit les utilisateurs et offre la possibilité d’exécuter des sites web avec des contrôles ActiveX incompatibles en mode protégé normal.  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Chargement des fichiers XAML**  
  Ce paramètre de stratégie vous permet de gérer le chargement des fichiers XAML (Extensible Application Markup Language). Le langage XAML est un langage de balisage déclaratif basé sur le langage XML et couramment utilisé pour la création d’interfaces utilisateur et de graphismes avancés qui tirent parti de Windows Presentation Foundation. Si vous activez ce paramètre de stratégie et si vous affectez la valeur Activer à la zone de liste déroulante, les fichiers XAML sont automatiquement chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous affectez la valeur Demander à la zone de liste déroulante, l’utilisateur est invité à confirmer le chargement des fichiers XAML. Si vous désactivez ce paramètre de stratégie, les fichiers XAML ne sont pas chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur est libre de charger ou non les fichiers XAML dans Internet Explorer.
  
  **Par défaut**: désactiver  
  
- **Processus Internet Explorer : Restrictions de sécurité de scripts de fenêtres**  
  Internet Explorer permet aux scripts d’ouvrir, de redimensionner et de déplacer des fenêtres de divers types. La fonctionnalité de sécurité de Restrictions des fenêtres limite les fenêtres indépendantes et empêche les scripts d’ouvrir des fenêtres dont les barres de titre et d’état sont invisibles pour l’utilisateur ou cachent d’autres barres de titre et d’état Windows. Si vous activez ce paramètre de stratégie, les fenêtres avec scripts sont restreintes pour tous les processus. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les fenêtres scriptées ne sont pas restreintes.
  
  **Par défaut** : Activé   
  
- **Internet Explorer > Zone restreinte : Exécuter les contrôles ActiveX et les plug-ins**  
  Ce paramètre de stratégie permet d’indiquer si les contrôles ActiveX et les plug-ins peuvent s’exécuter dans les pages d’une zone spécifiée. Si vous activez ce paramètre de stratégie, les contrôles et les plug-ins peuvent s’exécuter de façon automatique. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution des contrôles ou des plug-ins. Si vous désactivez ce paramètre de stratégie, l’exécution des contrôles et des plug-ins est bloquée. Si vous ne configurez pas ce paramètre de stratégie, l’exécution des contrôles et des plug-ins est bloquée.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Contrôles ActiveX reconnus comme étant sécurisés pour les scripts**  
  Ce paramètre de stratégie permet d’indiquer si un contrôle ActiveX marqué comme sûr pour les scripts peut interagir avec un script. Si vous activez ce paramètre de stratégie, l’interaction avec les scripts peut se produire automatiquement, sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser les interactions avec les scripts. Si vous désactivez ce paramètre de stratégie, l’interaction avec les scripts est interdite. Si vous ne configurez pas ce paramètre de stratégie, l’interaction avec les scripts ne se produit pas.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Options d’ouverture de session**  
  Ce paramètre de stratégie permet de gérer les paramètres des options de connexion. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options de connexion suivantes. 
  - *Anonyme* : utilisez la connexion anonyme pour désactiver l’authentification HTTP et n’utilisez le compte invité que pour le protocole CIFS (Common Internet File System). 
  - *Invite* : utilisez l’invite pour interroger les utilisateurs sur leurs identifiants utilisateur et leurs mots de passe. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées de manière silencieuse pour le reste de la session. 
  - *Connexion automatique uniquement dans la zone Intranet* : utilisez cette option pour demander aux utilisateurs leur identifiant utilisateur et leur mot de passe pour accéder à d’autres zones. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées de manière silencieuse pour le reste de la session. 
  - *Connexion automatique avec le nom d’utilisateur et le mot de passe actuels*  : utilisez cette option pour tenter une connexion à l’aide de l’authentification Stimulation/réponse de Windows NT (également connue sous le nom Authentification NTLM). Si le protocole Stimulation/réponse de Windows NT est pris en charge par le serveur, la connexion utilise le nom d’utilisateur réseau de l’utilisateur et son mot de passe pour l’ouverture de session. Si le protocole Stimulation/réponse de Windows NT n’est pas pris en charge par le serveur, l’utilisateur doit entrer son nom et son mot de passe. 

  Si vous désactivez ce paramètre de stratégie, la connexion est définie comme *Automatique uniquement dans la zone intranet*. Si vous ne configurez pas ce paramètre de stratégie, la connexion est définie sur *Invite* pour le nom d’utilisateur et le mot de passe.
  
  **Par défaut** : anonyme  
  
- **Internet Explorer > Zone de confiance : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Vérifier la révocation du certificat serveur**  
  Ce paramètre de stratégie permet d’administrer la vérification par Internet Explorer de l’état de révocation des certificats de serveur. Les certificats sont révoqués lorsqu’ils sont compromis ou qu’ils ne sont plus valides. Cette option protège les utilisateurs de l’envoi de données confidentielles vers un site qui pourrait être frauduleux ou non sécurisé. Si vous activez ce paramètre de stratégie, Internet Explorer vérifie si les certificats de serveur ont été révoqués. Si vous désactivez ce paramètre de stratégie, Internet Explorer ne vérifie pas si les certificats de serveur ont été révoqués. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer ne vérifie pas si les certificats de serveur ont été révoqués.
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone Internet : Sites de moindre privilège**  
  Ce paramètre de stratégie permet de spécifier si les sites web des zones moins privilégiées, tels que les sites sensibles, peuvent naviguer dans cette zone. Si vous activez ce paramètre de stratégie, les sites web des zones de moindre privilège peuvent ouvrir de nouvelles fenêtres dans cette zone ou y accéder. La zone de sécurité fonctionne sans la couche de sécurité supplémentaire qui est fournie par la fonctionnalité Protection contre l’élévation de zone. Si vous sélectionnez Demander dans la zone de liste déroulante, l’utilisateur est averti qu’un accès potentiellement risqué est sur le point de se produire. Si vous désactivez ce paramètre de stratégie, les accès potentiellement dangereux sont empêchés. La fonctionnalité de sécurité d’Internet Explorer est activée sur cette zone comme défini par le contrôle de la fonctionnalité Protection contre l’élévation de zone. Si vous ne configurez pas ce paramètre de stratégie, les sites web des zones moins privilégiées peuvent ouvrir de nouvelles fenêtres ou naviguer dans cette zone.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Téléchargements de fichiers**  
  Ce paramètre de stratégie permet d’indiquer si les téléchargements de fichiers sont autorisés depuis la zone. Cette option est définie par la zone de la page contenant le lien qui lance le téléchargement, et non pas la zone depuis laquelle le fichier est envoyé. Si vous activez ce paramètre de stratégie, les fichiers peuvent être téléchargés depuis la zone. Si vous désactivez ce paramètre de stratégie, les fichiers ne peuvent pas être téléchargés depuis la zone. Si vous ne configurez pas ce paramètre de stratégie, les fichiers ne peuvent pas être téléchargés depuis la zone.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Exécuter les composants dépendant du .NET Framework signés avec Authenticode**  
  Ce paramètre de stratégie vous permet d’indiquer si les composants .NET Framework qui sont signés avec Authenticode peuvent s’exécuter dans Internet Explorer. Ces composants incluent les contrôles managés référencés par une balise objet et les exécutables managés référencés à partir d’un lien. Si vous activez ce paramètre de stratégie, Internet Explorer exécute les composants managés signés. Si vous sélectionnez Demander dans la liste déroulante, Internet Explorer demande aux utilisateurs s’ils souhaitent exécuter les composants managés signés. Si vous désactivez ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Empêcher l’installation par utilisateur des contrôles ActiveX**  
  Ce paramètre de stratégie vous permet d’empêcher l’installation de contrôles ActiveX en fonction de chaque utilisateur. Si vous activez ce paramètre de stratégie, les contrôles ActiveX ne peuvent pas être installés pour chaque utilisateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les contrôles ActiveX peuvent être installés pour chaque utilisateur.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Empêcher la gestion du filtre SmartScreen**  
  Ce paramètre de stratégie empêche l’utilisateur de gérer le filtre SmartScreen, qui avertit l’utilisateur lorsque le site web visité est connu pour des tentatives frauduleuses de collecte d’informations personnelles par « hameçonnage », ou qu’il est connu pour héberger des programmes malveillants. Si vous activez ce paramètre de stratégie, l’utilisateur n’est pas invité à activer le filtre SmartScreen. Toutes les URL qui ne figurent pas dans la liste des URL autorisées par les filtres sont automatiquement envoyées à Microsoft, sans que l’utilisateur en soit informé. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur est invité à choisir s’il veut activer le filtre SmartScreen lors de l’expérience de première exécution.
  
  **Par défaut** : activer  
  
- **Processus Internet Explorer > Fonctionnalité de sécurité de détection MIME**  
  Ce paramètre de stratégie indique si la détection MIME dans Internet Explorer doit empêcher la promotion d’un fichier ou d’un type de fichier vers un type plus dangereux. Si vous activez ce paramètre de stratégie, la fonctionnalité de sécurité de détection MIME n’autorisera jamais la promotion d’un fichier vers un type de fichier plus dangereux. Si vous désactivez ce paramètre de stratégie, les processus Internet Explorer autoriseront la détection MIME à promouvoir un fichier vers un type de fichier plus dangereux. Si vous ne configurez pas ce paramètre de stratégie, la détection MIME n’autorise jamais la promotion d’un type de fichier vers un type de fichier plus dangereux.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Télécharger les contrôles ActiveX signés**  
  Ce paramètre de stratégie vous permet d’indiquer si les utilisateurs peuvent télécharger les contrôles ActiveX signés depuis une page de la zone. Si vous activez cette stratégie, les utilisateurs peuvent télécharger les contrôles signés de façon automatique. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation. Si vous désactivez ce paramètre de stratégie, les contrôles signés ne peuvent pas être téléchargés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Saisie semi-automatique**  
  Cette fonctionnalité de saisie semi-automatique peut se souvenir des noms d’utilisateurs et des mots de passe entrés dans des formulaires et les suggérer. Si vous activez ce paramètre, l’utilisateur ne peut pas modifier les options « Noms d’utilisateur et mots de passe sur les formulaires » ou « Demander l’enregistrement des mots de passe ». La fonctionnalité de saisie semi-automatique est activée pour l’option « Noms d’utilisateur et mots de passe sur les formulaires ». Vous devez décider de sélectionner ou non l’option « Demander l’enregistrement des mots de passe ». Si vous désactivez ce paramètre, l’utilisateur ne peut pas modifier les options « Noms d’utilisateur et mots de passe sur les formulaires » ou « Demander l’enregistrement des mots de passe ». La fonctionnalité de saisie semi-automatique est désactivée pour « Noms d’utilisateur et mots de passe sur les formulaires ». En outre, l’utilisateur ne peut pas choisir de demander l’enregistrement des mots de passe. Si vous ne configurez pas ce paramètre, l’utilisateur est libre d’activer la saisie semi-automatique pour l’option « Noms d’utilisateur et mots de passe sur les formulaires» et de choisir de demander l’enregistrement des mots de passe. Pour afficher cette option, les utilisateurs ouvrent la boîte de dialogue Options Internet, cliquent sur l’onglet Contenu, puis sur le bouton Paramètres.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Autoriser l’exécution de VBscript**  
  Ce paramètre de stratégie vous permet de décider si VBScript peut être exécuté sur les pages de certaines zones Internet Explorer. Les options sont les suivantes : 
  - *Activé* : VBScript s’exécute sur les pages de certaines zones, sans intervention de l’utilisateur. 
  - *Invite* : les employés sont invités à choisir s’il faut autoriser l’exécution de VBScript dans la zone. 
  - *Désactivé* : l’exécution de VBScript est empêchée dans la zone. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, VBScript s’exécute dans la zone spécifiée, sans que l’utilisateur n’ait à intervenir. 
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Autoriser uniquement les domaines approuvés à utiliser le contrôle Active X TDC**  
  Ce paramètre de stratégie contrôle si l’utilisateur est ou non autorisé à exécuter le contrôle ActiveX TDC sur des sites web. Si vous activez ce paramètre de stratégie, le contrôle ActiveX TDC n’est pas exécuté sur les sites web de cette zone. Si vous désactivez ce paramètre de stratégie, le contrôle ActiveX TDC s’exécute sur tous les sites de cette zone.
  
  **Par défaut** : Activé  
  
- **La zone de confiance Internet Explorer n’exécute pas de logiciels anti-programme malveillant sur les contrôles ActiveX**  
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer utilise toujours votre logiciel anti-programme malveillant pour vérifier si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Ordinateur local : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Sécurité moyenne ».
  
  **Par défaut**: désactiver Java 
  
- **La zone intranet Internet Explorer n’exécute pas de logiciel anti-programme malveillant sur les contrôles Active X** Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.
  
  **Par défaut** : Désactivé  

- **Internet Explorer > Zone restreinte : Scriptlets**  
  Ce paramètre de stratégie vous permet de déterminer si l’utilisateur peut exécuter des scriptlets. Si vous activez ce paramètre de stratégie, l’utilisateur peut exécuter des scriptlets. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne peut pas exécuter de scriptlets. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver les scriptlets.
  
  **Par défaut** : Désactivé  
  
- **Processus Internet Explorer > Barre de notification**  
  Ce paramètre de stratégie vous permet d’indiquer si la Barre de notification est affichée pour les processus Internet Explorer lorsque des installations de fichiers ou de code sont restreintes. Par défaut, la Barre de notification est affichée pour les processus Internet Explorer. Si vous activez ce paramètre de stratégie, la barre de notification s’affiche pour les processus Internet Explorer. Si vous désactivez ce paramètre de stratégie, la barre de notification ne s’affiche pas pour les processus Internet Explorer. Si vous ne configurez pas ce paramètre de stratégie, la barre de notification ne s’affiche pas pour les processus Internet Explorer.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone Internet : Télécharger les contrôles ActiveX signés**  
  Ce paramètre de stratégie vous permet d’indiquer si les utilisateurs peuvent télécharger les contrôles ActiveX signés depuis une page de la zone. Si vous activez cette stratégie, les utilisateurs peuvent télécharger les contrôles signés de façon automatique. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation. Si vous désactivez ce paramètre de stratégie, les contrôles signés ne peuvent pas être téléchargés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : SmartScreen**  
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Supprimer le bouton Exécuter une fois pour les contrôles ActiveX obsolètes**  
  Ce paramètre de stratégie vous permet d’empêcher les utilisateurs de voir le bouton « Exécuter une fois » et d’exécuter des contrôles ActiveX obsolètes spécifiques dans Internet Explorer. Si vous activez ce paramètre de stratégie, les utilisateurs ne voient pas le bouton « Exécuter une fois » sur le message d’avertissement qui s’affiche quand Internet Explorer bloque un contrôle ActiveX obsolète. Si vous désactivez ou ne configurez pas ce paramètre de stratégie, les utilisateurs voient le bouton « Exécuter une fois » sur le message d’avertissement qui s’affiche quand Internet Explorer bloque un contrôle ActiveX obsolète. Si l’utilisateur clique sur ce bouton, le contrôle ActiveX obsolète est exécuté une seule fois. Pour plus d’informations, consultez « Contrôles ActiveX obsolètes » dans la bibliothèque TechNet Internet Explorer.
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone Internet : Lancer les applications et les fichiers dans un iframe**  
  Ce paramètre de stratégie permet d’indiquer si les applications peuvent s’exécuter et les fichiers être téléchargés depuis une référence IFRAME dans le code source HTML des pages de cette zone. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les applications et télécharger des fichiers depuis des IFRAME sans entrer de confirmation. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent exécuter des applications et télécharger des fichiers depuis des IFRAME des pages de cette zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter d’applications, ni télécharger des fichiers depuis les IFRAME des pages de cette zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent indiquer s’ils souhaitent exécuter des applications et télécharger des fichiers depuis des IFRAME sur les pages de cette zone.
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Zone restreinte : Naviguer dans des fenêtres et des cadres sur différents domaines**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : SmartScreen**  
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone de confiance verrouillée : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.
  
  **Par défaut**: désactiver Java 
  
- **Internet Explorer > Vérifier les signatures des programmes téléchargés**  
  Ce paramètre de stratégie vous permet de décider si Internet Explorer recherche des signatures numériques (pour identifier l’éditeur du logiciel signé et vérifier qu’il n’a pas été modifié ni falsifié) sur les ordinateurs des utilisateurs avant de télécharger des programmes exécutables. Si vous activez ce paramètre de stratégie, Internet Explorer vérifie les signatures numériques des programmes exécutables et affiche leur identité avant de les télécharger sur les ordinateurs des utilisateurs. Si vous désactivez ce paramètre de stratégie, Internet Explorer ne vérifie pas les signatures numériques des programmes exécutables ou n’affiche pas leurs identités avant de les télécharger sur les ordinateurs des utilisateurs. Si vous ne configurez pas cette stratégie, Internet Explorer ne vérifie pas les signatures numériques des programmes exécutables ou n’affiche pas leurs identités avant de les télécharger sur les ordinateurs des utilisateurs.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Écriture de scripts pour les contrôles de navigateur web**  
  Ce paramètre de stratégie détermine si une page peut gérer les contrôles incorporés WebBrowser par script. Si vous activez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser est autorisé. Si vous désactivez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser n’est pas autorisé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver l’accès du script au contrôle WebBrowser. Par défaut, l’accès du script au contrôle WebBrowser est autorisé uniquement dans les zones Ordinateur local et Intranet.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Filtre anti-script de site à site**  
  Cette stratégie détermine si le filtre anti-script de site à site (XSS) détecte et évite les injections de script de site à site dans les sites web de cette zone. Si vous activez ce paramètre de stratégie, le filtre XSS est activé pour les sites de cette zone et tente de bloquer les injections de script de site à site. Si vous désactivez ce paramètre de stratégie, le filtre XSS est désactivé pour les sites de cette zone et Internet Explorer autorise les injections de script de site à site.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Comportements binaires et des scripts**  
  Ce paramètre de stratégie vous permet de gérer les comportements binaires et des scripts dynamiques : des composants qui encapsulent des fonctionnalités spécifiques pour les éléments HTML auxquels ils sont attachés. Si vous activez ce paramètre de stratégie, les comportements binaires et des scripts sont disponibles. Si vous sélectionnez Approuvé par l’administrateur dans la zone de liste déroulante, seuls les comportements listés dans les comportements approuvés par l’administrateur sous la stratégie Restriction de sécurité des comportements binaires sont disponibles. Si vous désactivez ce paramètre de stratégie, les comportements binaires et des scripts ne sont pas disponibles, sauf si les applications ont implémenté un gestionnaire de sécurité personnalisé. Si vous ne configurez pas ce paramètre de stratégie, les comportements binaires et des scripts ne sont pas disponibles, sauf si les applications ont implémenté un gestionnaire de sécurité personnalisé.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Vérification des paramètres de sécurité**  
  Ce paramètre de stratégie désactive la fonction de vérification des paramètres de sécurité, qui vérifie les paramètres de sécurité Internet Explorer pour déterminer quand les paramètres exposent Internet Explorer à des risques. Si vous activez ce paramètre de stratégie, la fonction est désactivée. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la fonctionnalité est activée.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone Internet : Avertissement de sécurité pour les fichiers potentiellement dangereux**  
  Ce paramètre de stratégie détermine si le message « Fichier ouvert : Avertissement de sécurité » s’affiche lorsque l’utilisateur essaie d’ouvrir des fichiers exécutables ou d’autres fichiers potentiellement non sécurisés (à partir d’un partage de fichiers intranet via l’Explorateur de fichiers, par exemple). Si vous activez ce paramètre de stratégie et affectez la valeur Activer à la zone de liste déroulante, les fichiers concernés s’ouvrent sans avertissement de sécurité préalable. Si vous affectez la valeur Demander à la zone de liste déroulante, un avertissement de sécurité s’affiche avant l’ouverture des fichiers. Si vous désactivez ce paramètre de stratégie, les fichiers concernés ne s’ouvrent pas. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut configurer la façon dont l’ordinateur gère ces fichiers. Par défaut, ces fichiers sont bloqués dans la zone restreinte, activés dans les zones Intranet et Ordinateur local, et définis sur Demander dans les zones Internet et de confiance.
  
  **Par défaut** : invite  
  
- **Internet Explorer > Zone Intranet : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Sécurité moyenne ».
  
  **Par défaut** : haute sécurité 
  
- **Internet Explorer > Bloquer les contrôles ActiveX obsolètes**  </br>
  Ce paramètre de stratégie détermine si Internet Explorer bloque des contrôles ActiveX obsolètes spécifiques. Les contrôles ActiveX obsolètes ne sont jamais bloqués dans la zone Intranet. Si vous activez ce paramètre de stratégie, Internet Explorer cesse de bloquer les contrôles ActiveX obsolètes. Si vous désactivez ou ne configurez pas ce paramètre de stratégie, Internet Explorer continue de bloquer des contrôles ActiveX obsolètes spécifiques. Pour plus d’informations, consultez « Contrôles ActiveX obsolètes » dans la bibliothèque TechNet Internet Explorer.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Bloqueur de fenêtres publicitaires**  
  Ce paramètre de stratégie permet d’indiquer si les fenêtres publicitaires s’affichent. Les fenêtres indépendantes qui sont ouvertes lorsque l’utilisateur final clique sur un lien ne sont pas bloquées. Si vous activez ce paramètre de stratégie, la plupart des fenêtres publicitaires sont bloquées. Si vous désactivez ce paramètre de stratégie, les fenêtres indépendantes ne sont pas bloquées. Si vous ne configurez pas ce paramètre de stratégie, la plupart des fenêtres indépendantes non désirées ne s’afficheront pas.
  
  **Par défaut** : activer  
  
- **Processus Internet Explorer > Restriction de sécurité du protocole MK**  
  Le paramètre de stratégie Restriction de sécurité du protocole MK réduit l’exposition aux attaques en empêchant l’utilisation du protocole MK. Cela se traduit par l’échec des ressources hébergées sur le protocole MK. Si vous activez ce paramètre de stratégie, l’utilisation du protocole MK est interdite dans l’Explorateur de fichiers et Internet Explorer, ce qui se traduit par l’échec des ressources hébergées sur le protocole MK. Si vous désactivez ce paramètre de stratégie, les applications peuvent utiliser l’API du protocole MK. Les ressources hébergées sur le protocole MK fonctionnent pour les processus de l’Explorateur de fichiers et d’Internet Explorer. Si vous ne configurez pas ce paramètre de stratégie, l’utilisation du protocole MK est interdite dans l’Explorateur de fichiers et Internet Explorer, ce qui se traduit par l’échec des ressources hébergées sur le protocole MK.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone de confiance : Autorisations Java**  </br>
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Basse sécurité ».
  
  **Par défaut** : haute sécurité  
  
- **Internet Explorer > Zone restreinte : Écriture de scripts pour les applets Java**  
  Ce paramètre de stratégie vous permet de décider si les applets sont exposées aux scripts dans la zone. Si vous activez ce paramètre de stratégie, les scripts peuvent accéder aux applets automatiquement, sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser les scripts à accéder aux applets. Si vous désactivez ce paramètre de stratégie, les scripts ne peuvent pas accéder aux applets. Si vous ne configurez pas ce paramètre de stratégie, les scripts ne peuvent pas accéder aux applets.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte verrouillée : Autorisations Java**  </br>
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.
  
  **Par défaut**: désactiver Java 
  
- **Internet Explorer > Zone Internet : Autoriser uniquement les domaines approuvés à utiliser les contrôles ActiveX**  </br>
  Ce paramètre de stratégie détermine si l’utilisateur est invité ou non à autoriser l’exécution des contrôles ActiveX sur des sites web autres que le site web qui a installé le contrôle ActiveX. Si vous activez ce paramètre de stratégie, l’utilisateur est invité à confirmer l’exécution des contrôles ActiveX à partir des sites web de cette zone. L’utilisateur peut choisir d’autoriser l’exécution du contrôle à partir du site actuel ou à partir de tous les sites. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne voit pas l’invite ActiveX propre au site, et les contrôles ActiveX peuvent s’exécuter à partir de tous les sites de cette zone.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Inclure tous les chemins réseau**  
  Internet Explorer > Inclure tous les chemins réseau
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Internet : Mode protégé**  
  Ce paramètre de stratégie vous permet d’activer le mode protégé. Le mode protégé favorise la protection d’Internet Explorer face à des vulnérabilités exploitées en réduisant les emplacements où Internet Explorer peut écrire dans le Registre et le système de fichiers. Si vous activez ce paramètre de stratégie, le mode protégé est activé. L’utilisateur ne peut pas désactiver le mode protégé. Si vous désactivez ce paramètre de stratégie, le mode protégé est désactivé. L’utilisateur ne peut pas activer le mode protégé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver le mode protégé.
  
  **Par défaut** : activer 
  
- **Internet Explorer > Zone Internet : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés.
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Zone restreinte verrouillée : SmartScreen**  </br>
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Détection des plantages**  
  Ce paramètre de stratégie vous permet de gérer la fonctionnalité de détection des plantages de la gestion des modules complémentaires. Si vous activez ce paramètre de stratégie, un plantage dans Internet Explorer aura le même comportement que pour Windows XP Professionnel Service Pack 1 et antérieur, à savoir l’affichage de la boîte de dialogue de rapport d’erreurs Windows. Tous les paramètres de stratégie du rapport d’erreurs Windows continuent à s’appliquer. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la fonctionnalité de détection des incidents pour la gestion des modules complémentaires est fonctionnelle.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Haute sécurité ».
  
  **Par défaut**: désactiver Java  
  
- **Internet Explorer > Zone restreinte : Active Scripting**  
  Ce paramètre de stratégie vous permet de gérer si le code de script dans les pages de la zone est exécuté. Si vous activez ce paramètre de stratégie, le code de script dans les pages de la zone peut s’exécuter automatiquement. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du code de script dans les pages de la zone. Si vous désactivez ce paramètre de stratégie, le code de script dans les pages de la zone ne peut pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, le code de script dans les pages de la zone ne peut pas s’exécuter.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Options d’ouverture de session**  
  Ce paramètre de stratégie permet de gérer les paramètres des options de connexion. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options de connexion suivantes. Ouverture de session anonyme, pour désactiver l’authentification HTTP et n’utiliser le compte Invité que pour le protocole CIFS (Common Internet File System). Demander aux utilisateurs leur nom d’utilisateur et leur mot de passe. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées pour le reste de la session. Ouverture de session automatique uniquement dans la zone Intranet, pour demander aux utilisateurs leur nom et leur mot de passe pour accéder aux autres zones. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées de manière silencieuse pour le reste de la session. Connexion automatique avec le nom d’utilisateur et le mot de passe actuels, pour tenter l’ouverture de session avec le protocole Stimulation/réponse de Windows NT (également connu sous le nom d’Authentification NTLM). Si l’authentification Stimulation/réponse de Windows NT est pris en charge par le serveur, la connexion utilise le nom d’utilisateur réseau de l’utilisateur et son mot de passe pour l’ouverture de session. Si le protocole Stimulation/réponse de Windows NT n’est pas pris en charge par le serveur, l’utilisateur doit entrer son nom et son mot de passe. Si vous désactivez ce paramètre de stratégie, l’ouverture de session est définie comme automatique uniquement dans la zone intranet. Si vous ne configurez pas ce paramètre de stratégie, la connexion est définie sur Connexion automatique uniquement dans la zone intranet.
  
  **Par défaut** : invite  
  
- **Internet Explorer > Zone restreinte : Autoriser l’exécution de VBScript**  </br>  
  Ce paramètre de stratégie permet d’indiquer si VBScript peut s’exécuter dans les pages d’une zone spécifiée dans Internet Explorer. Si vous sélectionnez Activer dans la zone de liste déroulante, VBScript peut s’exécuter sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution de VBScript. Si vous sélectionnez Désactiver dans la zone de liste déroulante, VBScript ne peut pas s’exécuter. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, VBScript ne peut pas s’exécuter.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Faire glisser du contenu provenant de domaines différents entre des fenêtres**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre.
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Intranet : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés.
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Télécharger des fichiers joints**  
  Ce paramètre de stratégie empêche l’utilisateur de télécharger des fichiers joints (pièces jointes) à partir d’un flux sur l’ordinateur de l’utilisateur. Si vous activez ce paramètre de stratégie, l’utilisateur ne peut pas définir le moteur de synchronisation de flux pour qu’il télécharge un fichier joint via la page des propriétés de flux. Un développeur ne peut pas modifier le paramètre de téléchargement via les interfaces de programmation d’applications de flux. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut définir le moteur de synchronisation de flux pour qu’il télécharge un fichier joint via la page des propriétés de flux. Un développeur peut modifier le paramètre de téléchargement via les API de flux.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Télécharger les contrôles ActiveX non signés**  </br>
  Ce paramètre de stratégie permet d’indiquer si les utilisateurs peuvent télécharger des contrôles ActiveX non signés à partir de la zone. Ce code est potentiellement dangereux, surtout s’il provient d’une zone non approuvée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les contrôles non signés sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du contrôle non signé. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Faire glisser du contenu provenant de domaines différents dans les fenêtres**  
  Ce paramètre de stratégie permet d’indiquer si les utilisateurs peuvent télécharger des contrôles ActiveX non signés à partir de la zone. Ce code est potentiellement dangereux, surtout s’il provient d’une zone non approuvée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les contrôles non signés sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du contrôle non signé. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés.
  
  **Par défaut** : Désactivé  
  
- **Processus Internet Explorer > Restreindre l’installation ActiveX**  </br>
  Ce paramètre de stratégie permet aux applications qui hébergent le contrôle de navigateur web de bloquer la demande automatique d’installation de contrôles ActiveX. Si vous activez ce paramètre de stratégie, le contrôle de navigateur web bloque la demande automatique d’installation de contrôles ActiveX pour tous les processus. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le contrôle de navigateur web ne bloque pas la demande automatique d’installation de contrôle ActiveX pour tous les processus.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone Internet : Scriptlets** Ce paramètre de stratégie vous permet de déterminer si l’utilisateur peut exécuter des scriptlets. Si vous activez ce paramètre de stratégie, l’utilisateur peut exécuter des scriptlets. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne peut pas exécuter de scriptlets. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver les scriptlets.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Glisser-déplacer ou copier et coller des fichiers**  
  Ce paramètre de stratégie vous permet de spécifier si les utilisateurs peuvent faire glisser ou copier et coller des fichiers à partir d’une source dans la zone. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent faire glisser ou copier et coller des fichiers à partir de cette zone automatiquement. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent faire glisser ou copier des fichiers à partir de cette zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas faire glisser ni copier et coller des fichiers à partir de cette zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent indiquer s’ils souhaitent faire glisser ou copier des fichiers à partir de cette zone.
  
  **Par défaut**: désactiver  
  
- **Logiciels Internet Explorer quand la signature n’est pas valide** </br>
  Ce paramètre de stratégie vous permet de spécifier si des logiciels, tels que les contrôles ActiveX et les téléchargements de fichiers, peuvent être installés ou exécutés par l’utilisateur, même si la signature n’est pas valide. Une signature non valide peut indiquer que quelqu’un a falsifié le fichier. Si vous activez ce paramètre de stratégie, les utilisateurs sont invités à installer ou exécuter des fichiers avec une signature non valide. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter ou installer des fichiers avec une signature non valide. Si vous ne configurez pas cette stratégie, les utilisateurs peuvent choisir d’exécuter ou d’installer des fichiers avec une signature non valide.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Copier et coller par le biais d’un script** </br> Ce paramètre de stratégie vous permet d’indiquer si les scripts peuvent utiliser le Presse-papiers (pour couper, copier, coller, etc.) dans une région spécifiée. Si vous activez ce paramètre de stratégie, un script peut effectuer une opération sur le Presse-papiers. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent effectuer des opérations sur le Presse-papiers. Si vous désactivez ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers. Si vous ne configurez pas ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Faire glisser du contenu provenant de domaines différents entre des fenêtres**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre.  <br><br>
  **Par défaut** : Désactivé  
  
- **Internet Explorer : utilisateurs ajoutant des sites**  
  Empêche les utilisateurs d’ajouter ou de supprimer des sites dans des zones de sécurité. Une zone de sécurité est un groupe de sites web partageant le même niveau de sécurité. Si vous activez cette stratégie, les paramètres de gestion de sites pour les zones de sécurité seront désactivés. (Pour voir les paramètres de gestion de sites pour les zones de sécurité, dans la boîte de dialogue Options Internet, cliquez sur l’onglet Sécurité, puis sur le bouton Sites.) Si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent non seulement ajouter ou supprimer des sites web dans les zones de Sites de confiance et de Sites sensibles, mais aussi modifier les paramètres de la zone intranet locale. Cette stratégie empêche les utilisateurs de changer les paramètres de gestion de sites pour les zones de sécurité définies par l’administrateur. Remarque : La stratégie « Désactiver la page Sécurité » (située dans \Configuration utilisateur\Modèles d’administration\Composants Windows\Internet Explorer\Panneau de configuration Internet), qui élimine l’onglet Sécurité de l’interface, est prioritaire sur cette stratégie. Si elle est activée, cette stratégie est ignorée. Consultez également la stratégie « Zones de sécurité : utiliser uniquement des paramètres machine ».
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : fenêtres initiées par des scripts**  
  Ce paramètre de stratégie permet de gérer les restrictions sur les fenêtres indépendantes lancées par des scripts, et sur celles qui incluent les barres de titre et d’état. Si vous activez ce paramètre de stratégie, la fonctionnalité de sécurité des Restrictions des fenêtres ne s’applique pas à cette zone. La zone de sécurité s’exécute sans la couche de sécurité supplémentaire fournie par cette fonctionnalité. Si vous désactivez ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts. Si vous ne configurez pas ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zones de sécurité : utiliser uniquement des paramètres machine**  
  Applique l’information sur les zones de sécurité à tous les utilisateurs du même ordinateur. Une zone de sécurité est un groupe de sites web partageant le même niveau de sécurité. Si vous activez ce paramètre de stratégie, les changements apportés par l’utilisateur à une zone de sécurité s’appliquent à tous les utilisateurs de cet ordinateur. Si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs du même ordinateur peuvent définir leurs propres paramètres de zone de sécurité. Utilisez cette stratégie pour garantir que les paramètres de zone de sécurité s’appliquent uniformément au même ordinateur et ne varient pas d’un utilisateur à l’autre. En outre, consultez la stratégie « Zones de sécurité : ne pas autoriser les utilisateurs à modifier les stratégies ».
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone Ordinateur local verrouillé : autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.
  
  **Par défaut**: désactiver Java 
  
- **Internet Explorer > Zone restreinte : ne pas exécuter de logiciels anti-programme malveillant sur les contrôles ActiveX**  </br>
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages en toute sécurité. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer utilise toujours votre logiciel anti-programme malveillant pour vérifier si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Exécuter les composants dépendant du .NET Framework signés avec Authenticode**  
  Ce paramètre de stratégie vous permet d’indiquer si les composants .NET Framework qui sont signés avec Authenticode peuvent s’exécuter dans Internet Explorer. Ces composants incluent les contrôles managés référencés par une balise objet et les exécutables managés référencés à partir d’un lien. Si vous activez ce paramètre de stratégie, Internet Explorer exécute les composants managés signés. Si vous sélectionnez Demander dans la liste déroulante, Internet Explorer demande aux utilisateurs s’ils souhaitent exécuter les composants managés signés. Si vous désactivez ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : accès aux sources de données**  
  Ce paramètre de stratégie vous permet d’indiquer si Internet Explorer peut accéder aux données provenant d’une autre zone de sécurité en utilisant le moteur d’analyse XML de Microsoft (MSXML) ou les objets ADO (ActiveX Data Objects). Si vous activez ce paramètre de stratégie, les utilisateurs peuvent charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement d’une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone.
  
  **Par défaut**: désactiver 
  
- **La zone internet Internet Explorer n’exécute pas de logiciels anti-programme malveillant sur les contrôles ActiveX**  </br>
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer utilise toujours votre logiciel anti-programme malveillant pour vérifier si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : copier et coller par le biais d’un script** </br> Ce paramètre de stratégie vous permet d’indiquer si les scripts peuvent utiliser le Presse-papiers (pour couper, copier, coller, etc.) dans une région spécifiée. Si vous activez ce paramètre de stratégie, un script peut effectuer une opération sur le Presse-papiers. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent effectuer des opérations sur le Presse-papiers. Si vous désactivez ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers. Si vous ne configurez pas ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer : utiliser le service de d’installation ActiveX**  </br>
  Ce paramètre de stratégie vous permet de spécifier la façon dont les contrôles ActiveX sont installés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont installés uniquement si le service de l’installateur ActiveX est présent et s’il a été configuré pour permettre l’installation de contrôles ActiveX. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les contrôles ActiveX, notamment les contrôles par utilisateur, sont installés par le biais du processus d’installation standard.
  
  **Par défaut** : Activé  
  
- **Processus Internet Explorer : protection contre l’élévation de zone**  
  Internet Explorer place des restrictions sur toutes les pages web qu’il ouvre. Les restrictions dépendent de l’emplacement de la page web (Internet, intranet, zone Ordinateur local, etc.). Par exemple, les pages web sur l’ordinateur local ont le moins de restrictions de sécurité et sont situées dans la zone Ordinateur local, faisant de cette zone une cible idéale pour les utilisateurs malveillants. Si vous activez ce paramètre de stratégie, toute zone peut être protégée contre l’élévation de zone pour tous les processus. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les processus autres qu’Internet Explorer ou ceux figurant dans la liste des processus ne reçoivent pas cette protection.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone internet : télécharger des contrôles ActiveX non signés**  </br>
  Ce paramètre de stratégie permet d’indiquer si les utilisateurs peuvent télécharger des contrôles ActiveX non signés à partir de la zone. Ce code est potentiellement dangereux, surtout s’il provient d’une zone non approuvée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les contrôles non signés sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du contrôle non signé. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Naviguer dans des fenêtres et des cadres sur différents domaines**  </br>
  Ce paramètre de stratégie vous permet de gérer l’ouverture de fenêtres et de cadres, ainsi que l’accès des applications sur différents domaines. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent ouvrir des fenêtres et des cadres à partir d’autres domaines et accéder aux applications à partir d’autres domaines. Si vous sélectionnez Demander dans la zone de liste déroulante, il est demandé aux utilisateurs s’il faut autoriser les fenêtres et les cadres à accéder aux applications à partir d’autres domaines. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas ouvrir de fenêtres et de cadres pour accéder aux applications à partir d’autres domaines. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs peuvent ouvrir des fenêtres et des cadres à partir d’autres domaines et accéder aux applications à partir d’autres domaines.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Mises à jour de la barre d’état via un script**  
  Ce paramètre de stratégie vous permet de spécifier si un script est autorisé à mettre à jour la barre d’état dans la zone. Si vous activez ce paramètre de stratégie, les scripts peuvent mettre à jour la barre d’état. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le script n’est pas autorisé à mettre à jour la barre d’état.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Inclure le chemin local lors du chargement des fichiers sur un serveur**  </br> Ce paramètre de stratégie spécifie si les informations du chemin d’accès local sont envoyées ou non lorsque l’utilisateur charge un fichier via un formulaire HTML. Si les informations de chemin local sont envoyées, certaines informations peuvent être involontairement révélées au serveur. Par exemple, des fichiers envoyés à partir du Bureau de l’utilisateur peuvent avoir un chemin contenant le nom de l’utilisateur. Si vous activez ce paramètre de stratégie, les informations de chemin sont envoyées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous désactivez ce paramètre de stratégie, les informations de chemin sont supprimées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si les informations du chemin d’accès sont envoyées lorsqu’il charge un fichier via un formulaire HTML. Par défaut, les informations de chemin sont envoyées.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Processus : Restreindre le téléchargement de fichiers**  </br> Ce paramètre de stratégie permet aux applications qui hébergent le contrôle de navigateur web de bloquer la demande automatique de confirmation des téléchargements de fichiers non lancés par l’utilisateur. Si vous activez ce paramètre de stratégie, le contrôle de navigateur web bloque la demande automatique de confirmation des téléchargements de fichiers non initiés par l’utilisateur pour tous les processus. Si vous désactivez ce paramètre de stratégie, le contrôle de navigateur web ne bloque pas la demande automatique de confirmation des téléchargements de fichiers non initiés par l’utilisateur pour tous les processus.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Autoriser uniquement les domaines approuvés à utiliser les contrôles Active X**  </br>
  Ce paramètre de stratégie détermine si l’utilisateur est invité ou non à autoriser l’exécution des contrôles ActiveX sur des sites web autres que le site web qui a installé le contrôle ActiveX. Si vous activez ce paramètre de stratégie, l’utilisateur est invité à confirmer l’exécution des contrôles ActiveX à partir des sites web de cette zone. L’utilisateur peut choisir d’autoriser l’exécution du contrôle à partir du site actuel ou à partir de tous les sites. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne voit pas l’invite ActiveX propre au site, et les contrôles ActiveX peuvent s’exécuter à partir de tous les sites de cette zone.
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés.
  
  **Par défaut**: désactiver  
  
- **Internet Explorer : modification des stratégies par les utilisateurs**  
    Empêche les utilisateurs de modifier les paramètres des zones de sécurité. Une zone de sécurité est un groupe de sites web partageant le même niveau de sécurité. Si vous activez cette stratégie, le bouton Personnaliser le niveau et le curseur de niveau de sécurité sont désactivés sous l’onglet Sécurité de la boîte de dialogue Options Internet. Si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent changer les paramètres des zones de sécurité. Cette stratégie empêche les utilisateurs de changer les paramètres des zones de sécurité configurés par l’administrateur. Remarque : La stratégie « Désactiver la page Sécurité » (située dans \Configuration utilisateur\Modèles d’administration\Composants Windows\Internet Explorer\Panneau de configuration Internet), qui supprime l’onglet Sécurité dans le Panneau de configuration Internet Explorer, est prioritaire sur cette stratégie. Si elle est activée, cette stratégie est ignorée. Consultez également la stratégie « Zones de sécurité : utiliser uniquement des paramètres machine ».
    
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Mode protégé**  
  Ce paramètre de stratégie vous permet d’activer le mode protégé. Le mode protégé favorise la protection d’Internet Explorer face à des vulnérabilités exploitées en réduisant les emplacements où Internet Explorer peut écrire dans le Registre et le système de fichiers. Si vous activez ce paramètre de stratégie, le mode protégé est activé. L’utilisateur ne peut pas désactiver le mode protégé. Si vous désactivez ce paramètre de stratégie, le mode protégé est désactivé. L’utilisateur ne peut pas activer le mode protégé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver le mode protégé.
  
  **Par défaut** : activer  
  
- **Internet Explorer > Zone Internet : Persistance des données utilisateur**  
  Ce paramètre de stratégie vous permet de gérer la conservation des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Quand un utilisateur revient à une page persistante, l’état de la page peut être restauré si ce paramètre de stratégie est configuré de façon appropriée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent conserver des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas conserver d’informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs peuvent conserver des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : Écriture de scripts pour les contrôles de navigateur Web**  
 
  Ce paramètre de stratégie détermine si une page peut gérer les contrôles incorporés WebBrowser par script. Si vous activez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser est autorisé. Si vous désactivez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser n’est pas autorisé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver l’accès du script au contrôle WebBrowser. Par défaut, l’accès du script au contrôle WebBrowser est autorisé uniquement dans les zones Ordinateur local et Intranet.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Persistance des données utilisateur**  
    Ce paramètre de stratégie vous permet de gérer la conservation des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Quand un utilisateur revient à une page persistante, l’état de la page peut être restauré si ce paramètre de stratégie est configuré de façon appropriée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent conserver des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas conserver d’informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas conserver d’informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque.  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Intranet verrouillée : autorisations Java**  
  Ce paramètre de stratégie vous permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.
  
  **Par défaut**: désactiver Java  
  
- **Internet Explorer : mode protégé amélioré**  
  Le mode protégé amélioré renforce la protection contre les sites Web malveillants en utilisant des processus 64 bits sur des versions 64 bits de Windows. Pour les ordinateurs qui exécutent Windows 8 ou version ultérieure, le mode protégé amélioré limite également les emplacements à partir desquels Internet Explorer peut lire dans le Registre et le système de fichiers. Si vous activez ce paramètre de stratégie, le mode protégé amélioré est activé. Toute zone pour laquelle le mode protégé est activé utilise le mode protégé amélioré. Les utilisateurs ne sont pas en mesure de désactiver le mode protégé amélioré. Si vous désactivez ce paramètre de stratégie, le mode protégé amélioré est activé. Toute zone pour laquelle le mode protégé est activé utilise la version du mode protégé introduite dans Internet Explorer 7 pour Windows Vista. Si vous ne configurez pas cette stratégie, les utilisateurs peuvent activer ou désactiver le mode protégé amélioré sur l’onglet Avancé de la boîte de dialogue Options Internet.
  
  **Par défaut** : Activé  
  
- **Internet Explorer : ignorer les avertissements SmartScreen**  
  Ce paramètre de stratégie détermine si l’utilisateur peut ignorer les avertissements du filtre SmartScreen. Le filtre SmartScreen avertit l’utilisateur au sujet des fichiers exécutables que les utilisateurs d’Internet Explorer ne téléchargent généralement pas à partir d’Internet. Si vous activez ce paramètre de stratégie, les avertissements du filtre SmartScreen bloquent l’utilisateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut ignorer les avertissements du filtre SmartScreen.
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : actualisation des métafichiers**  
  Ce paramètre de stratégie vous permet de spécifier si le navigateur d’un utilisateur peut être redirigé vers une autre page web si l’auteur de la page web utilise le paramètre (la balise) Meta Refresh pour rediriger les navigateurs vers une autre page web. Si vous activez ce paramètre de stratégie, le navigateur d’un utilisateur qui charge une page contenant un paramètre Meta Refresh actif peut être redirigé vers une autre page web. Si vous désactivez ce paramètre de stratégie, le navigateur d’un utilisateur qui charge une page contenant un paramètre Meta Refresh actif ne peut pas être redirigé vers une autre page web. Si vous ne configurez pas ce paramètre de stratégie, le navigateur d’un utilisateur qui charge une page contenant un paramètre Meta Refresh actif ne peut pas être redirigé vers une autre page web.
  
  **Par défaut** : Désactivé  
  
### <a name="local-policies-security-options"></a>Options de sécurité des stratégies locales
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) dans la documentation Windows. 

- **Restreindre l’accès anonyme aux canaux nommés et aux partages**  
  Lorsque l’option est activée, ce paramètre de sécurité restreint l’accès anonyme aux partages et aux canaux pour les paramètres : (1) canaux nommés qui peuvent être accessibles de manière anonyme (2) partages qui sont accessibles de manière anonyme
  
  **Par défaut** : Oui  
  
- **Sécurité de session minimale pour les serveurs basés sur NTLM SSP**  
  Ce paramètre de sécurité permet à un serveur d’exiger la négociation d’un chiffrement de 128 bits et/ou de la sécurité de session NTLMv2. Ces valeurs dépendent de la valeur du paramètre de sécurité Niveau d’authentification LAN Manager. Les options sont : nécessite une sécurité de session NTLMv2 : la connexion échoue si l’intégrité des messages n’est pas négociée. Exiger un chiffrement 128 bits : La connexion échoue si un chiffrement fort (128 bits) n’est pas négocié.
  
  **Par défaut** : exiger NTLM V2 et un chiffrement de 128 bits  
  
- **Minutes d’inactivité de l’écran de verrouillage avant l’activation de l’économiseur d’écran**  
  Windows identifie les sessions ouvertes inactives. Si le délai d’inactivité dépasse la limite d’inactivité définie, l’écran de veille s’exécute, ce qui entraîne le verrouillage de la session.
  
  **Par défaut** : 15
  
- **Exiger du client qu’il signe toujours numériquement les communications** Ce paramètre de sécurité détermine si tout le trafic d’un canal sécurisé initié par le membre du domaine doit être signé ou chiffré. Lorsqu’un ordinateur rejoint un domaine, un compte d’ordinateur est créé. Après cela, lorsque le système démarre, il utilise le mot de passe du compte d’ordinateur pour créer un canal sécurisé avec un contrôleur de domaine pour son domaine. Ce canal sécurisé est utilisé pour effectuer des opérations telles que l’authentification directe NTLM, la recherche de nom SID de l’autorité de sécurité locale (LSA), etc. Ce paramètre détermine si tout le trafic du canal sécurisé initialisé par le membre du domaine répond ou non aux exigences de sécurité minimales. Plus précisément, il détermine si tout le trafic du canal sécurisé initialisé par le membre du domaine doit être signé ou chiffré. Si cette stratégie est activée, le canal sécurisé ne sera établi que si la signature ou le chiffrement de tout le trafic du canal sécurisé est négocié. Si cette stratégie est désactivée, le chiffrement et la signature de tout le trafic du canal sécurisé sont négociés avec le contrôleur de domaine, auquel cas le niveau de signature et de chiffrement dépend de la version du contrôleur de domaine et des paramètres des deux stratégie suivantes : Membre de domaine : données de canal sécurisé par le chiffrement numérique (si possible) Membre de domaine : données de canal sécurisé par connexion numérique (si possible)
  
  **Par défaut** : Oui
  
- **Niveau d'authentification**  
  Ce paramètre de sécurité détermine le protocole d'authentification de stimulation/réponse utilisé pour les ouvertures de session réseau. Ce choix a une incidence sur le niveau du protocole d'authentification qu'utilisent les clients, le niveau de sécurité de session négocié et le niveau d'authentification qu'acceptent les serveurs, de la façon suivante :  
  - *Envoyer des réponses LM et NTLM* : les clients utilisent les authentifications LM et NTLM et n’ont jamais recours à la sécurité de session NTLMv2. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer des authentifications LM et NTLM, NTLMv2 si négociée* : les clients utilisent les authentifications LM et NTLM, ainsi que la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer une réponse NTLM uniquement* : les clients utilisent uniquement l’authentification NTLM et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer une réponse NTLMv2 uniquement* : les clients utilisent uniquement l’authentification NTLMv2 et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer uniquement une réponse NTLMv2. Refuser l’authentification LM* : les clients utilisent uniquement l’authentification NTLMv2 et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine refusent l’authentification LM (ils acceptent uniquement les authentifications NTLM et NTLMv2). 
  - *Envoyer uniquement une réponse NTLMv2. Refuser les authentifications LM et NTLM* : les clients utilisent uniquement l’authentification NTLMv2 et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine refusent les authentifications LM et NTLM (ils acceptent uniquement l’authentification NTLMv2). 
    
  **Par défaut** : envoyez uniquement une réponse NTLMv2. Refuser LM et NTLM
  
- **Empêcher les clients d’envoyer des mots de passe non chiffrés à des serveurs SMB tiers**  
  Si ce paramètre de sécurité est activé, le redirecteur SMB (Server Message Block) est autorisé à envoyer des mots de passe en clair à des serveurs qui ne sont pas des serveurs Microsoft SMB et qui ne prennent pas en charge le chiffrement des mots de passe lors de l’authentification. L'envoi de mots de passe non chiffrés constitue un risque pour la sécurité.
  
  **Par défaut** : Oui
  
- **Désactiver la signature numérique systématique des communications par le serveur**  
  Ce paramètre de sécurité détermine si le client SMB tente de négocier la signature des paquets SMB. Le protocole SMB (Server Message Block) représente la base sur laquelle s'appuient le partage des fichiers et des imprimantes Microsoft ainsi que beaucoup d'autres opérations de gestion de réseau, telles que l'administration à distance de Windows. Pour empêcher des attaques de l’intercepteur, susceptibles de modifier les paquets SMB en transit, le protocole SMB prend en charge la signature numérique des paquets SMB. Ce paramètre de stratégie détermine si le composant client SMB tente de négocier la signature des paquets SMB lorsqu'il se connecte à un serveur SMB. Si ce paramètre est activé, le client réseau Microsoft demandera au serveur de signer les paquets SMB lors de la configuration de la session. Si la signature de paquet a été activée sur le serveur, la signature de paquet est négociée. Si cette stratégie est désactivée, le client SMB ne négocie jamais la signature des paquets SMB.
  
  **Par défaut** : Oui
  
- **Comportement de l’invite d’élévation d’administrateur**  
  Ce paramètre de stratégie contrôle le comportement de l’invite d’élévation pour les administrateurs. Les options disponibles sont : 
    - *Élever les privilèges sans invite utilisateur* : permet aux comptes privilégiés d’effectuer une opération qui nécessite une élévation sans demander de consentement ou d’informations d’identification. Remarque : Utilisez cette option uniquement dans les environnements les plus contraints. 
    - *Demander des informations d’identification sur le bureau sécurisé* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à entrer un nom d’utilisateur et un mot de passe privilégié. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur. 
    - *Demander le consentement sur le bureau sécurisé* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à choisir Autoriser et Refuser. Si l’utilisateur sélectionne Autoriser, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur. 
    - *Demander des informations d’identification* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité à entrer un nom d’utilisateur et un mot de passe administrateur. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables. 
    - *Demander le consentement* : lorsqu’une opération requiert une élévation de privilège, l’utilisateur est invité à choisir entre Autoriser et Refuser. Si l’utilisateur sélectionne Autoriser, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur.  
    - *Demander le consentement pour les binaires non Windows* : lorsqu’une opération pour une application non Microsoft nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à choisir entre Autoriser et Refuser. Si l’utilisateur sélectionne Autoriser, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur.   
  
  **Par défaut** : demander le consentement sur le bureau sécurisé
  
- **Sécurité de session minimale pour les clients basés sur NTLM SSP**  
  Ce paramètre de sécurité permet à un client d’exiger la négociation d’un chiffrement de 128 bits et/ou de la sécurité de session NTLMv2. Ces valeurs dépendent de la valeur du paramètre de sécurité Niveau d’authentification LAN Manager. Les options disponibles sont :
  - Nécessite une sécurité de session NTLMv2 : la connexion échoue si le protocole NTLMv2 n’est pas négocié. 
  - *Nécessite un chiffrement 128 bits* : la connexion échoue si un chiffrement fort (128 bits) n’est pas négocié.
  - *Exiger l’authentification NTLMv2 et un chiffrement de 128 bits*. 

  **Par défaut** : exiger le chiffrement 128 de l’authentification NTLM V2
  
- **Comportement lorsque la carte à puce est retirée**  
    Ce paramètre de sécurité détermine ce qui se passe quand la carte à puce d’un utilisateur connecté est retirée du lecteur de cartes à puce. Les options disponibles sont :
     - *Aucune action*. 
     - *Verrouiller la station de travail* : la station de travail est verrouillée lorsque la carte à puce est supprimée, ce qui permet aux utilisateurs de quitter la zone, prendre leur carte à puce avec eux tout en conservant une session protégée.
     - *Forcer la fermeture de session* : l’utilisateur est automatiquement déconnecté lorsque la carte à puce est retirée.
     - *Déconnecter la session de Bureau à distance* : le retrait de la carte à puce déconnecte la session sans déconnecter l’utilisateur. Ceci permet à l'utilisateur d'insérer la carte à puce et de reprendre la session ultérieurement ou sur un autre ordinateur équipé d'un lecteur de cartes à puce, sans avoir à ouvrir de nouveau une session. Si la session est locale, cette stratégie fonctionne comme l’option Verrouiller la station de travail.  <br><br>
    
  **Par défaut** : verrouiller la station de travail
  
- **Bloquer l’énumération anonyme des comptes et partages SAM**  
  Ce paramètre de sécurité détermine si l’énumération anonyme des comptes et partages de gestion des actifs logiciels est autorisée. Windows autorise les utilisateurs anonymes à effectuer certaines activités, comme l'énumération des noms des comptes de domaine et des partages réseau. Cette possibilité est pratique, par exemple lorsqu’un administrateur veut accorder aux utilisateurs l’accès dans un domaine approuvé ne conservant pas une approbation réciproque. Si vous ne voulez pas autoriser l’énumération anonyme des comptes et partages de gestion des actifs logiciels, puis configurez cette stratégie sur *Oui*.
  
  **Par défaut** : Oui
  
- **Bloquer l’ouverture de session à distance avec un mot de passe vide**  
  Ce paramètre de sécurité détermine si les comptes locaux qui ne sont pas protégés par un mot de passe peuvent être utilisés pour ouvrir une session à partir d’emplacements autres que la console de l’ordinateur physique. S'il est activé, les comptes locaux qui ne sont pas protégés par mot de passe ne permettent une ouverture de session que sur le clavier de l'ordinateur. 

  *Avertissement* : les ordinateurs qui ne se trouvent pas à des emplacements physiquement sécurisés doivent toujours appliquer des stratégies de mot de passe fort pour tous les comptes d’utilisateur locaux. Dans le cas contraire, toute personne ayant un accès physique à l’ordinateur peut ouvrir une session en utilisant un compte d’utilisateur sans mot de passe. Ce paramètre est particulièrement important pour les ordinateurs portables. 

  Si vous appliquez cette stratégie de sécurité au groupe Tout le monde, personne ne peut ouvrir une session via les services Bureau à distance. Ce paramètre n’affecte pas les ouvertures de sessions qui utilisent des comptes de domaine. Les applications qui utilisent des ouvertures de session interactives à distance peuvent contourner ce paramètre.
  
  **Par défaut** : Oui
  
- **Comportement de l’invite d’élévation d’utilisateur standard**  
  Ce paramètre de stratégie contrôle le comportement de l’invite d’élévation pour les utilisateurs standard. 
  - *Refuser automatiquement les demandes d’élévation de privilèges* : lorsqu’une opération nécessite une élévation de privilège, un message d’erreur d’accès configurable refusé s’affiche. Une entreprise qui utilise des ordinateurs de bureau en tant qu’utilisateur standard peut choisir ce paramètre pour réduire les appels au support technique. 
  - *Demander des informations d’identification sur le bureau sécurisé* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à entrer un nom d’utilisateur et un mot de passe différent. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables. 
  - *Demander des informations d’identification* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité à entrer un nom d’utilisateur et un mot de passe administrateur. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables.  
  
  **Par défaut** : refuser automatiquement les demandes d’élévation de privilèges
  
- **Exiger le mode d’approbation Administrateur pour les administrateurs**  
  Ce paramètre de stratégie contrôle le comportement de tous les paramètres de stratégie de contrôle de compte d’utilisateur (UAC) pour l’ordinateur. Si vous modifiez ce paramètre de stratégie, vous devez redémarrer votre ordinateur. Les options disponibles sont :   
  - *Non configuré* : le mode d’approbation Administrateur et tous les paramètres de stratégie UAC associés sont désactivés. Remarque : Si ce paramètre de stratégie est désactivé, le Centre de sécurité vous avertit que la sécurité globale du système d’exploitation a été réduite. 
  - *Oui* : Le mode d’approbation Administrateur est activé. Cette stratégie doit être activée et les paramètres de stratégie UAC associés doivent également être définis en conséquence pour permettre au compte Administrateur intégré et à tous les autres utilisateurs membres du groupe Administrateurs de s’exécuter en mode d’approbation Administrateur.  
  
  **Par défaut** : Oui
  
- **Empêcher l’énumération anonyme des comptes SAM**  
  Ce paramètre de sécurité détermine quelles autorisations supplémentaires sont octroyées aux connexions anonymes à l’ordinateur. Windows autorise les utilisateurs anonymes à effectuer certaines activités, comme l'énumération des noms des comptes de domaine et des partages réseau. Cette possibilité est pratique, par exemple lorsqu’un administrateur veut accorder aux utilisateurs l’accès dans un domaine approuvé ne conservant pas une approbation réciproque. Cette option de sécurité permet d'imposer aux connexions anonymes les restrictions supplémentaires suivantes : 
  - *Oui* : Ne pas autoriser l’énumération des comptes de gestion des actifs logiciels. Cette option remplace Tout le monde par Utilisateurs authentifiés dans les autorisations de sécurité pour les ressources.
  - *Non configuré* : aucune autre restriction. Correspond aux autorisations par défaut.  
  
  **Par défaut** : Oui
  
- **Autoriser les appels distants au Gestionnaire des comptes de sécurité**  
  Ce paramètre de stratégie vous permet de limiter les connexions rpc à distance au gestionnaire SAM. S’il n’est pas sélectionné, le descripteur de sécurité par défaut est utilisé.
  
  **Par défaut** : *O:BAG:BAD:(A;;RC;;;BA)*

- **Utiliser le mode d’approbation Administrateur**  
  Ce paramètre de sécurité détermine le comportement du mode d’approbation Administrateur pour le compte Administrateur intégré. Les options disponibles sont : 
  - *Oui* : le compte Administrateur intégré utilise le mode d’approbation Administrateur. Par défaut, une invite d’approbation est présentée à l’utilisateur pour chaque opération nécessitant une élévation de privilège. 
  - *Non configuré* : le compte Administrateur intégré exécute toutes les applications avec des privilèges administratifs complets.  

  **Par défaut** : Oui
  
- **Autoriser les applications d’accès de l’interface utilisateur pour des emplacements sécurisés**  
  Ce paramètre de sécurité indique si les programmes d’accessibilité de l’interface utilisateur (UIAccess ou UIA) peuvent désactiver automatiquement le bureau sécurisé pour les invites d’élévation utilisées par un utilisateur standard. 
  - *Oui* : les programmes UIA, notamment l’Assistance à distance Windows, désactivent automatiquement le bureau sécurisé pour les invites d’élévation. Si vous ne désactivez pas le paramètre de stratégie « Contrôle de compte d’utilisateur : passer au bureau sécurisé lors d’une demande d’élévation », les invites s’affichent sur le bureau de l’utilisateur interactif et non sur le bureau sécurisé. 
  - *Non configuré* : le bureau sécurisé ne peut être désactivé que par l’utilisateur du bureau interactif ou en désactivant le paramètre de stratégie « Contrôle de compte d’utilisateur  : passer au bureau sécurisé lors d’une demande d’élévation ».  

  **Par défaut** : Oui

- **Détecter les installations d’applications et demander l’élévation**  
  Ce paramètre de stratégie contrôle le comportement de détection des installations d’applications pour l’ordinateur. Les options disponibles sont : 
  - *Activé* : lorsqu’un package d’installation d’application nécessitant une élévation de privilège est détecté, l’utilisateur est invité à entrer un nom d’utilisateur et un mot de passe administrateur. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables. 
  - *Désactivé* : les packages d’installation d’application ne sont pas détectés ni invités pour une élévation. Les entreprises qui utilisent des ordinateurs de bureau pour utilisateur standard et ont recours à des technologies d’installation déléguée telles que GPSI (Group Policy Software Install) ou SMS (Systems Management Server) doivent désactiver ce paramètre de stratégie. Dans ce cas, la détection d’un programme d’installation n’est pas nécessaire.  
  
  **Par défaut** : Oui
  
- **Empêcher le stockage d’une valeur de hachage LAN Manager lors du prochain changement de mot de passe**  
  Ce paramètre de sécurité détermine si, au prochain changement de mot de passe, la valeur de hachage LAN Manager (LM) est stockée pour le nouveau mot de passe. Le hachage LM est relativement faible et vulnérable aux attaques par rapport au hachage Windows NT, plus fort en matière de chiffrement. Étant donné que le hachage LM est stocké sur l’ordinateur local dans la base de données de sécurité, les mots de passe peuvent être compromis si la base de données de sécurité est attaquée.
  
  **Par défaut** : Oui

- **Virtualiser les échecs d’écriture de fichier et de Registre dans des emplacements par utilisateur**  
  Ce paramètre de stratégie détermine si les échecs d’écriture d’application sont redirigés vers des emplacements définis du système de fichiers et du Registre. Ce paramètre de stratégie atténue les applications qui s’exécutent en tant qu’administrateur et écrivent des données d’application au moment de l’exécution dans *%ProgramFiles%* , *%Windir%* , *%Windir%\system32*, or *HKLM\Software*.
  
  **Par défaut** : Oui

### <a name="ms-security-guide"></a>Guide de sécurité Microsoft  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) dans la documentation Windows.  

- **Appliquer des restrictions du contrôle de compte d’utilisateur à des comptes locaux lors de l’ouverture de session réseau**  
  **Par défaut** : Activé
  
- **Configuration de démarrage du pilote du client SMB v1**  
  **Par défaut** : pilote désactivé
  
- **Serveur SMB v1**  
  **Par défaut** : Désactivé
  
- **Authentification Digest**  
  **Par défaut** : Désactivé
  
- **Protection structurée contre le remplacement de la gestion des exceptions**  
  **Par défaut** : Activé
  
### <a name="mss-legacy"></a>MSS hérité  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) dans la documentation Windows.  

- **Niveau de protection du routage de source IP réseau**  
  **Par défaut** : protection la plus élevée  
  
- **Ignorer sur le réseau les demandes de libération de noms NetBIOS sauf à partir de serveurs WINS**  
  **Par défaut** : Activé
  
- **Niveau de protection du routage de source IPv6 réseau**  
  **Par défaut** : protection la plus élevée

- **Les redirections ICMP réseau remplacent les routes OSPF générées**  
  **Par défaut** : Désactivé
  
### <a name="power"></a>Puissance  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) dans la documentation Windows.  

- **Exiger un mot de passe à la sortie de veille quand l’appareil est branché**  
  Ce paramètre de stratégie spécifie si l’utilisateur doit entrer un mot de passe à la sortie du mode veille du système. Si vous activez ou ne configurez pas ce paramètre de stratégie, l’utilisateur est invité à entrer un mot de passe lorsque le système sort du mode veille. Si vous désactivez ce paramètre de stratégie, l’utilisateur n’est pas invité à entrer de mot de passe lorsque le système sort du mode veille.
  
  **Par défaut** : Activé
  
- **États de mise en attente lorsque l'appareil est en veille sur batterie**  
  Ce paramètre de stratégie indique si Windows est autorisé à utiliser les états de mise en attente lors de la mise en veille de l'ordinateur. Si vous activez ou ne configurez pas ce paramètre de stratégie, Windows utilise les états de mise en attente pour mettre l’ordinateur en veille. Si vous désactivez ce paramètre de stratégie, les états de mise en attente (S1-S3) ne sont pas autorisés.
  
  **Par défaut** : Désactivé
  
- **États de mise en attente lorsque l'appareil est en veille et branché**  
  Ce paramètre de stratégie indique si Windows est autorisé à utiliser les états de mise en attente lors de la mise en veille de l'ordinateur. Si vous activez ou ne configurez pas ce paramètre de stratégie, Windows utilise les états de mise en attente pour mettre l’ordinateur en veille. Si vous désactivez ce paramètre de stratégie, les états de mise en attente (S1-S3) ne sont pas autorisés.
  
  **Par défaut** : Désactivé
  
- **Exiger un mot de passe à la sortie de veille quand l’appareil est sur batterie**  
  Ce paramètre de stratégie spécifie si l’utilisateur doit entrer un mot de passe à la sortie du mode veille du système. Si vous activez ou ne configurez pas ce paramètre de stratégie, l’utilisateur est invité à entrer un mot de passe lorsque le système sort du mode veille. Si vous désactivez ce paramètre de stratégie, l’utilisateur n’est pas invité à entrer de mot de passe lorsque le système sort du mode veille.
  
  **Par défaut** : Activé
  
### <a name="remote-desktop-services"></a>Services Bureau à distance  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) dans la documentation Windows.  

- **Bloquer l’enregistrement de mot de passe**  
  Indique si les mots de passe peuvent être enregistrés sur cet ordinateur à partir de la connexion Bureau à distance. Si vous activez ce paramètre, la case à cocher proposant d’enregistrer le mot de passe dans Connexion Bureau à distance est désactivée et les utilisateurs ne peuvent plus enregistrer les mots de passe. Lorsqu’un utilisateur ouvre un fichier RDP à l’aide de la Connexion Bureau à distance et enregistre ses paramètres, tout mot de passe qui existait précédemment dans le fichier RDP est supprimé. Si vous désactivez ce paramètre ou ne le configurez pas, l’utilisateur peut enregistrer les mots de passe en utilisant la Connexion Bureau à distance.
  
   **Par défaut** : Activé
  
- **Sécuriser la communication RPC**  
  Spécifie si un serveur hôte de session Bureau à distance nécessite des communications RPC sécurisées avec tous les clients ou autorise les communications non sécurisées. Vous pouvez utiliser ce paramètre pour renforcer la sécurité des communications RPC avec les clients en n'autorisant que les demandes chiffrées et authentifiées. Si vous activez ce paramètre, les Services Bureau à distance acceptent les demandes des clients RPC qui prennent en charge les demandes sécurisées et n’autorisent pas les communications non sécurisées avec des clients non approuvés. Si vous désactivez ce paramètre, les services Bureau à distance demandent toujours des mesures de sécurité pour tout le trafic RPC. Toutefois, les communications non sécurisées sont autorisées pour les clients RPC qui ne répondent pas à la demande. Si vous ne configurez pas ce paramètre, les communications non sécurisées sont autorisées. Remarque : L’interface RPC sert à administrer et configurer les Services Bureau à distance.
  
  **Par défaut** : Activé
  
- **Bloquer la redirection des lecteurs**  
  Ce paramètre de stratégie spécifie s’il faut empêcher ou non le mappage des lecteurs client dans une session des services Bureau à distance (redirection de lecteur). Par défaut, un serveur hôte de session Bureau à distance mappe automatiquement les lecteurs client à la connexion. Les lecteurs mappés apparaissent dans l'arborescence des dossiers de sessions dans l'Explorateur de fichiers ou Poste de travail sous le format *\<lettre_lecteur>* dans *\<nom_ordinateur>* . Vous pouvez utiliser ce paramètre de stratégie pour remplacer ce comportement. Si vous activez ce paramètre de stratégie, la redirection des lecteurs client n’est pas autorisée dans les sessions des Services Bureau à distance, et la redirection de copie de fichiers du Presse-papiers n’est pas autorisée sur les ordinateurs exécutant Windows Server 2003, Windows 8 et Windows XP. Si vous désactivez ce paramètre de stratégie, la redirection des lecteurs client est toujours autorisée. En outre, la redirection de copie de fichiers du Presse-papiers est toujours autorisée si la redirection du Presse-papiers est autorisée. Si vous ne configurez pas ce paramètre de stratégie, la redirection de lecteurs client et la redirection de copie de fichiers du Presse-papiers ne sont pas spécifiées au niveau de la stratégie de groupe.
  
  **Par défaut** : Activé
  
- **Demander un mot de passe lors de la connexion**  
  Ce paramètre de stratégie spécifie si les services Bureau à distance demandent toujours au client de fournir un mot de passe lors de la connexion. Vous pouvez utiliser ce paramètre pour forcer la demande de mot de passe aux utilisateurs se connectant aux services Bureau à distance, même s'ils ont déjà fourni le mot de passe dans le client de connexion au Bureau à distance. Par défaut, les services Bureau à distance autorisent les utilisateurs à se connecter automatiquement en entrant un mot de passe dans le client de connexion au Bureau à distance. Si vous activez ce paramètre de stratégie, les utilisateurs ne peuvent pas se connecter automatiquement aux Services Bureau à distance en fournissant leurs mots de passe dans le client de la Connexion Bureau à distance. Un mot de passe leur est demandé pour ouvrir une session. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent toujours se connecter automatiquement aux services Bureau à distance en fournissant leurs mots de passe dans le client de connexion au Bureau à distance. Si vous ne configurez pas ce paramètre de stratégie, l’ouverture de session automatique n’est pas spécifiée au niveau de la stratégie de groupe. 
  
  **Par défaut** : Activé
  
- **Niveau de chiffrement de connexion des clients aux services Bureau à distance**  
  Spécifie s’il faut exiger l’utilisation d’un niveau de chiffrement spécifique pour sécuriser les communications entre les ordinateurs clients et les serveurs hôtes de session Bureau à distance lors de connexions RDP (Remote Desktop Protocol). Cette stratégie s’applique uniquement lorsque vous utilisez le chiffrement RDP natif. Toutefois, le chiffrement RDP natif (contrairement au chiffrement SSL) n’est pas recommandé. Cette stratégie ne s’applique pas au chiffrement SSL. Si vous activez ce paramètre de stratégie, toutes les communications entre les clients et les serveurs hôtes de session Bureau à distance au cours des connexions à distance doivent utiliser la méthode de chiffrement spécifiée dans ce paramètre. Par défaut, le niveau de chiffrement est défini sur Élevé. Vous pouvez utiliser les méthodes de chiffrement suivantes :  
  - *Élevé* : le paramètre Élevé chiffre les données envoyées du client au serveur et du serveur au client à l’aide d’un chiffrement de 128 bits renforcé. Utilisez ce niveau de chiffrement dans des environnements qui contiennent uniquement des clients 128 bits (par exemple, les clients qui exécutent la connexion Bureau à distance). Les clients qui ne prennent pas en charge ce niveau de chiffrement ne peuvent pas se connecter aux serveurs Hôte de session Bureau à distance.  
  - *Compatible client* : le paramètre Compatible client chiffre les données envoyées entre le client et le serveur à la puissance de clé maximale prise en charge par le client. Utilisez ce niveau de chiffrement dans les environnements qui incluent les clients qui ne prennent pas en charge le chiffrement de 128 bits.  
  - *Faible* : le paramètre Faible chiffre uniquement les données envoyées du client au serveur à l’aide d’un chiffrement de 56 bits.  
  
  Si vous désactivez ce paramètre ou ne le configurez pas, le niveau de chiffrement à utiliser pour les connexions à distance aux serveurs Hôte de session Bureau à distance n’est pas appliqué via la stratégie de groupe. Une conformité FIPS importante peut être configurée via le chiffrement système. Utilisez des algorithmes compatibles FIPS pour les paramètres de chiffrement, de hachage et de signature dans la stratégie de groupe (sous Configuration ordinateur\Paramètres Windows\Paramètres de sécurité\Stratégies locales\Options de sécurité). Le paramètre compatible FIPS chiffre et déchiffre les données envoyées du client au serveur et du serveur au client, avec les algorithmes de chiffrement FIPS (Federal Information Processing Standard) 140, à l’aide des modules de chiffrement Microsoft. Utilisez ce niveau de chiffrement lorsque les communications entre les clients et les serveurs hôtes de session Bureau à distance nécessitent le niveau de chiffrement le plus élevé.
  
  **Par défaut** : élevé
  
### <a name="remote-management"></a>Gestion à distance  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) dans la documentation Windows.  

- **Bloquer l’exécution du stockage en tant qu’informations d’identification**  
  Authentification de base client
  
  **Par défaut** : Activé
  
- **Authentification de base**  
  Ce paramètre de stratégie vous permet de spécifier si le service Windows Remote Management (WinRM) accepte l’authentification de base à partir d’un client distant. Si vous activez ce paramètre de stratégie, le service WinRM accepte l’authentification de base à partir d’un client distant. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le service WinRM n’accepte pas l’authentification de base à partir d’un client distant.
  
  **Par défaut** : Désactivé
  
- **Bloquer l’authentification Digest client**  
  Ce paramètre de stratégie vous permet de spécifier si le client Windows Remote Management (WinRM) utilise l’authentification Digest. Si vous activez ce paramètre de stratégie, le client WinRM n’utilise pas l’authentification Digest. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM utilise l’authentification Digest.
  
  **Par défaut** : Activé
  
- **Trafic non chiffré**  
  Ce paramètre de stratégie vous permet de spécifier si le service Windows Remote Management (WinRM) envoie et reçoit des messages non chiffrés via le réseau. Si vous activez ce paramètre de stratégie, le client WinRM envoie et reçoit des messages non chiffrés via le réseau. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM envoie ou reçoit uniquement des messages chiffrés via le réseau.  
  
  **Par défaut** : Désactivé
  
- **Trafic client non chiffré**  
  Ce paramètre de stratégie vous permet de spécifier si le client Windows Remote Management (WinRM) envoie et reçoit des messages non chiffrés via le réseau. Si vous activez ce paramètre de stratégie, le client WinRM envoie et reçoit des messages non chiffrés via le réseau. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM envoie ou reçoit uniquement des messages chiffrés via le réseau.
  
  **Par défaut** : Désactivé
  
- **Authentification de base client**  
  Ce paramètre de stratégie vous permet de spécifier si le client Windows Remote Management (WinRM) utilise l’authentification de base. Si vous activez ce paramètre de stratégie, le client WinRM utilise l’authentification de base. Si WinRM est configuré pour utiliser le transport HTTP, le nom d’utilisateur et le mot de passe sont envoyés via le réseau en texte clair. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM utilise l’authentification de base.
  
  **Par défaut** : Désactivé
  

### <a name="remote-procedure-call"></a>Appel de procédure distante  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) dans la documentation Windows.  

- **Options du client RPC non authentifié**  
  Ce paramètre de stratégie contrôle la façon dont le runtime du serveur RPC gère les clients RPC non authentifiés se connectant aux serveurs RPC. Ce paramètre de stratégie affecte toutes les applications RPC. Dans un environnement de domaine, utilisez ce paramètre de stratégie avec précaution, car il peut avoir un impact sur un large éventail de fonctionnalités, y compris sur le traitement de la stratégie de groupe lui-même. Le rétablissement d’une modification apportée à ce paramètre de stratégie peut nécessiter une intervention manuelle sur chaque machine affectée. Ce paramètre de stratégie ne doit jamais être appliqué à un contrôleur de domaine. Si vous désactivez ce paramètre de stratégie, le runtime du serveur RPC utilise la valeur « Authentifié » sur le client Windows et la valeur « Aucun » sur les versions de Windows Server qui prennent en charge ce paramètre de stratégie. Si vous ne configurez pas ce paramètre de stratégie, il reste désactivé. Le runtime du serveur RPC se comporte comme s’il avait été activé avec la valeur « Authentifié » utilisée pour le client Windows et la valeur « Aucun » utilisée pour les références SKU Server qui prennent en charge ce paramètre de stratégie. Si vous activez ce paramètre de stratégie, il indique au runtime du serveur RPC de limiter les clients RPC non authentifiés qui se connectent aux serveurs RPC s’exécutant sur une machine. Un client est considéré comme étant authentifié s’il utilise un canal nommé pour communiquer avec le serveur ou s’il utilise la sécurité RPC. Les interfaces RPC qui ont demandé spécifiquement à être accessible par des clients non authentifiés peuvent être exemptées de cette restriction, en fonction de la valeur sélectionnée pour ce paramètre de stratégie.  
  - *Aucun* permet à tous les clients RPC de se connecter aux serveurs RPC s’exécutant sur la machine sur laquelle le paramètre de stratégie est appliqué. 
  - *Authentifié* autorise seulement les clients RPC authentifiés (selon la définition ci-dessus) à se connecter aux serveurs RPC s’exécutant sur la machine sur laquelle le paramètre de stratégie est appliqué. Des exemptions sont accordées aux interfaces qui les ont demandées. 
  - *Authentifié sans exceptions* autorise seulement les clients RPC authentifiés (selon la définition ci-dessus) à se connecter aux serveurs RPC s’exécutant sur la machine sur laquelle le paramètre de stratégie est appliqué. Aucune exception n’est autorisée. Remarque : Ce paramètre de stratégie n’est pas appliqué tant que le système n’est pas redémarré.  

  **Par défaut** : authentifié

### <a name="search"></a>Recherche  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Recherche](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) dans la documentation Windows.  

- **Désactiver l’indexation des éléments chiffrés**  
  Autorise ou interdit l’indexation des éléments. Ce commutateur concerne l’indexeur Windows Search, qui contrôle s’il indexe les éléments chiffrés, comme les fichiers protégés par la Protection des informations Windows. Quand la stratégie est activée, les éléments protégés par la Protection des informations Windows sont indexés et leurs métadonnées sont stockées à un emplacement non chiffré. Les métadonnées incluent des éléments comme le chemin et la date de modification des fichiers. Lorsque la stratégie est désactivée, les éléments TEC protégés ne sont pas indexés et n’apparaissent pas dans les résultats de Cortana ou de l’Explorateur de fichiers. Il peut également y avoir un impact sur les performances pour les photos et les applications Groove si de nombreux fichiers multimédias sont protégés par la Protection des informations Windows sur l’appareil.
  
**Par défaut** : oui
  
### <a name="smart-screen"></a>SmartScreen  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) dans la documentation Windows.  

- **Bloquer l’exécution de fichiers non vérifiés**  
  Bloque l’exécution par l’utilisateur des fichiers non vérifiés. 
  - *Non configuré* : les employés peuvent ignorer les avertissements SmartScreen et exécuter des fichiers malveillants. 
  - *Oui* : les employés ne peuvent pas ignorer les avertissements SmartScreen et exécuter des fichiers malveillants.

  **Par défaut** : oui

<!-- Not currently available? - **Block unverified file download**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes
 --> 
- **Exiger SmartScreen pour les applications et les fichiers**  
  Permet aux administrateurs informatiques de configurer SmartScreen pour Windows.

  **Par défaut** : oui
  
### <a name="system"></a>Système  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Système](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) dans la documentation Windows.  

- **Système : Initialisation des pilotes de démarrage**  
  Ce paramètre de stratégie vous permet de spécifier quels pilotes de démarrage sont initialisés selon une classification déterminée par un pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé. Le pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé peut retourner les classifications suivantes pour chaque pilote de démarrage : 
  - *Bon* : le pilote a été signé et n’a pas été falsifié.  
  - *Mauvais* : Le pilote a été identifié comme étant un programme malveillant. Il est recommandé de ne pas autoriser l’initialisation des mauvais pilotes connus. 
  - *Mauvais, mais requis lors du démarrage* : le pilote a été identifié comme étant un programme malveillant, mais l’ordinateur ne peut pas démarrer correctement sans charger ce pilote. 
  - *Inconnu* : ce pilote n’a pas été confirmé par votre application de détection des programmes malveillants et n’a pas été classé par le pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé.  

  Si vous activez ce paramètre de stratégie, vous pouvez choisir les pilotes de démarrage à initialiser lors du prochain démarrage de l’ordinateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les pilotes de démarrage déterminés comme étant « Bons », « Inconnus » ou « Mauvais, mais critique pour le démarrage » sont initialisés. L’initialisation des pilotes déterminés comme étant « Mauvais » est ignorée. Si votre application de détection des programmes malveillants n’inclut pas un pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé ou si votre pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé a été désactivé, ce paramètre n’a aucun effet et tous les pilotes de démarrage sont initialisés.  
  
  **Par défaut** : Bon, Inconnu et Mauvais, mais critique


### <a name="wi-fi"></a>Wi-Fi  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) dans la documentation Windows.  

- **Bloquer le partage Internet**  
  Spécifie si le partage Internet est possible sur l’appareil.  

  **Par défaut** : oui  

- **Bloquer la connexion automatique aux points d’accès Wi-Fi**  
  Autorise ou interdit la connexion automatique de l’appareil aux points d’accès Wi-Fi.  

  **Par défaut** : oui  
  
### <a name="windows-connection-manager"></a>Gestionnaire de connexions Windows  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) dans la documentation Windows.  

- **Bloquer la connexion aux réseaux sans domaine**  
  Ce paramètre de stratégie empêche les ordinateurs de se connecter en même temps à un réseau avec domaine et à un réseau sans domaine. Si ce paramètre de stratégie est activé, l’ordinateur répond aux tentatives de connexion au réseau automatiques et manuelles selon les circonstances suivantes : 
  - Tentatives de connexion automatiques : quand l’ordinateur est déjà connecté à un réseau avec domaine, toutes les tentatives de connexion automatiques à des réseaux sans domaine sont bloquées. Quand l’ordinateur est déjà connecté à un réseau sans domaine, les tentatives de connexion automatiques à des réseaux avec domaine sont bloquées. 
  - Tentatives de connexion manuelles : lorsque l’ordinateur est déjà connecté à un réseau sans domaine ou à un réseau avec domaine via un média autre qu’Ethernet, et qu’un utilisateur tente de créer une connexion manuelle à un autre réseau en violation de ce paramètre de stratégie, la connexion réseau existante est déconnectée et la connexion manuelle est autorisée. Quand l’ordinateur est déjà connecté à un réseau sans domaine ou à un réseau avec domaine via Ethernet, et qu’un utilisateur tente de créer une connexion manuelle à un autre réseau en violation de ce paramètre de stratégie, la connexion Ethernet existante est maintenue et la tentative de connexion manuelle est bloquée.  

  Si ce paramètre de stratégie n’est pas configuré ou est désactivé, les ordinateurs sont autorisés à se connecter simultanément à des réseaux avec domaine et sans domaine.  

  **Par défaut** : Activé
  
### <a name="windows-defender"></a>Windows Defender  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) dans la documentation Windows.  

- **Analyser les e-mails entrants**  
  Autorise ou interdit l’analyse des e-mails.
  
  **Par défaut** : oui  

- **Les applications Office lancent un type de processus enfant**  
  Les applications Office ne sont pas autorisées à créer des processus enfants. Elles incluent Word, Excel, PowerPoint, OneNote et Access. Il s’agit d’un comportement malveillant typique, en particulier pour les attaques basées sur des macros qui tentent d’utiliser des applications Office pour lancer ou télécharger des fichiers exécutables malveillants.
  
  **Par défaut** : bloc
  
- **Type de consentement pour l’envoi d’exemples par Defender**  
  Vérifie le niveau de consentement de l’utilisateur dans Windows Defender pour envoyer des données. Si le consentement nécessaire a déjà été accordé, Windows Defender les envoie. Si ce n’est pas le cas (et si l’utilisateur a spécifié de ne jamais lui demander), l’interface utilisateur est lancée pour demander le consentement de l’utilisateur (quand Defender/AllowCloudProtection est autorisé) avant d’envoyer des données.
  
  **Par défaut** : Envoyer automatiquement des échantillons sécurisés 
  
- **Intervalle de mise à jour des signatures (en heures)**  
  Intervalle de mise à jour des signatures de Defender en heures
  
  **Par défaut** : 4
  
- **Script : type d’exécution de charge utile téléchargée**  
  Script Defender : type d’exécution de charge utile téléchargée
  
  **Par défaut** : bloc
  
- **Empêcher le vol d’informations d’identification**  
  Windows Defender Credential Guard utilise une sécurité basée sur la virtualisation pour isoler les secrets, afin que seuls les logiciels système privilégiés puissent y accéder. L’accès non autorisé à ces informations secrètes peut entraîner des vols, par exemple de type Pass-the-Hash ou Pass-the-Ticket. Windows Defender Credential Guard empêche ces attaques en protégeant les hachages de mot de passe NTLM, les TGT (Ticket Granting Ticket) Kerberos et les informations d’identification stockées par les applications comme informations d’identification de domaine.
  
  **Par défaut** : activer

- **Type d’exécution du contenu des e-mails**  
  Cette règle bloque les types de fichiers suivants pour qu’ils ne soient pas exécuter ou lancée à partir d’un email dans Microsoft Outlook ou d’une message sur le Web (par exemple, Gmail.com ou Outlook.com) : fichiers exécutables (par exemple, .exe, .dll ou .scr) fichiers de Script (par exemple, un fichier .ps PowerShell, .vbs VisualBasic, .js ou JavaScript) fichiers d’archive de Script.
  
  **Par défaut** : bloc
  
- **Type de protection réseau**  
  Cette stratégie vous permet d’activer la protection réseau (bloquer/auditer) ou de la désactiver dans Windows Defender Exploit Guard. La protection réseau est une fonctionnalité de Windows Defender Exploit Guard qui protège les employés utilisant une application d’accéder à des tentatives d’hameçonnage, à des sites hébergeant du code malveillant exploitant une faille de sécurité et à du contenu malveillant sur Internet. Cela inclut le fait d’empêcher des navigateurs tiers de se connecter à des sites dangereux. Le type de la valeur est un entier. Si vous activez ce paramètre, la protection réseau est activée et les employés ne peuvent pas la désactiver. Son comportement peut être contrôlé par les options suivantes : Bloquer et Auditer. Si vous activez cette stratégie avec l’option « Bloquer », la connexion des utilisateurs et des applications à des domaines dangereux est bloquée. Vous pouvez consulter cette activité dans Windows Defender Security Center. Si vous activez cette stratégie avec l’option « Auditer », la connexion des utilisateurs/applications à des domaines dangereux n’est pas bloquée. Vous pouvez néanmoins toujours voir cette activité dans le Centre de sécurité Windows Defender. Si vous désactivez cette stratégie, la connexion des utilisateurs/applications à des domaines dangereux n’est pas bloquée. Vous ne voyez pas cette activité réseau dans le Centre de sécurité Windows Defender. Si vous ne configurez pas cette stratégie, le blocage réseau est désactivé par défaut.
  
  **Par défaut** : activer
  
- **Defender : Planifier le jour de l’analyse**  
  Jour de l’analyse planifié dans Defender.
  
  **Par défaut** : tous les jours
  
- **Protection assurée par le cloud**  
  Pour protéger au mieux votre PC, Windows Defender envoie des informations à Microsoft sur les problèmes détectés. Microsoft analyse ces informations, en apprend plus sur les problèmes qui vous affectent ainsi que d’autres clients, et offre des solutions améliorées.
  
  **Par défaut** :  oui  

- **Defender : action contre les applications potentiellement indésirables**  
  La fonctionnalité de protection contre les applications potentiellement indésirables dans l’antivirus Windows Defender peut identifier et bloquer le téléchargement et l’installation des applications potentiellement indésirables sur les points de terminaison de votre réseau. Ces applications ne sont pas considérées comme des virus, des logiciels malveillants ou d’autres types de menaces, mais elles peuvent effectuer des actions sur les points de terminaison qui dégradent leurs performances ou leur utilisation. Les applications potentiellement indésirables peuvent également faire référence à des applications considérées comme ayant une mauvaise réputation. Le comportement typique des PUA est notamment : différents types de bundle de logiciels Injection de publicité dans les navigateurs web, Optimiseurs de pilotes et du Registre qui détectent des problèmes et proposent de corriger les erreurs moyennant finance, mais restent sur le point de terminaison et n'effectuent ni changements ni optimisations (connus aussi sous le nom de programmes « antivirus non fiables »). Ces applications peuvent augmenter le risque d'infection de votre réseau par des programmes malveillants, rendent les infections de programmes malveillants difficiles à identifier et peuvent utiliser à perte les ressources informatiques pour nettoyer les applications.  
  
  **Par défaut** : bloc  

- **Type de code de macro obfusqué dans les scripts**  
  Les logiciels malveillants et d’autres menaces peuvent tenter d’obfusquer ou de masquer leur code malveillant dans certains fichiers de script. Cette règle empêche l’exécution des scripts qui paraissent obfusqués.
  
  **Par défaut** : bloc
  
- **Analyser les disques amovibles lors d’une analyse complète**  
  Permet à Windows Defender rechercher les logiciels malveillants et indésirables dans les lecteurs amovibles (par exemple les lecteurs flash) lors d’une analyse complète. L’antivirus Windows Defender analyse tous les fichiers sur les périphériques USB avant exécution.
  
  **Par défaut** : oui  
  
- **Analyser les fichiers d’archive**  
  Defender : Analyser les fichiers d’archive.
  
  **Par défaut** : oui
  
- **Surveillance du comportement**  
  Autorise ou interdit la fonctionnalité de Surveillance du comportement de Windows Defender incorporée dans Windows 10, ces capteurs collectent et traitent les signaux comportementaux du système d’exploitation et envoient ces données de capteur à votre instance cloud, isolée et privée de Windows Defender ATP.
  
  **Par défaut** : oui

- **Analyser les fichiers ouverts à partir de dossiers réseau**  
  Si des fichiers sont en lecture seule, l’utilisateur ne peut pas supprimer les programmes malveillants détectés.
  
  **Par défaut** : oui

- **Type de processus USB non approuvés**  
  Avec cette règle, les administrateurs peuvent empêcher l’exécution des fichiers exécutables non signés ou non fiables partir de lecteurs USB amovibles, notamment les cartes SD.
  
  **Par défaut** : bloc
  
- **Applications Office : Type d’injection dans d’autres processus**  
  Les applications Office, notamment Word, Excel, PowerPoint et OneNote, ne peuvent pas injecter du code dans d’autres processus. Ceci est généralement utilisé par des programmes malveillants pour exécuter du code malveillant de façon à masquer l’activité aux moteurs d’analyse antivirus.
  
  **Par défaut** : bloc
  
- **Code de macro Office autorisant un type d’importation Win32**  
  Les programmes malveillants peuvent utiliser du code de macro dans des fichiers Office pour importer et charger des DLL Win32, qui peuvent alors être utilisées pour effectuer des appels d’API, permettant ensuite une infection de tout le système. Cette règle tente de bloquer les fichiers Office qui contiennent du code de macro capable d’importer des DLL Win32. Ceci inclut Word, Excel, PowerPoint et OneNote.
  
  **Par défaut** : bloc  
  
- **Defender : Niveau de blocage cloud**  
  Niveau de blocage cloud de Defender.
  
  **Par défaut** : non configuré

- **Surveillance en temps réel**  
  Defender requiert une surveillance en temps réel.
  
  **Par défaut** : oui
  
- **Applications Office : type de création ou de lancement de contenu exécutable**  
  Cette règle cible des comportements typiques utilisés par des modules complémentaires et des scripts suspects et malveillants (extensions) qui créent ou lancent des fichiers exécutables. Il s’agit d’une technique classique des programmes malveillants. L’utilisation des extensions par les applications Office est bloquée. En général, ces extensions utilisent l’hôte de script Windows (fichiers .wsh) pour exécuter des scripts qui automatisent certaines tâches ou fournissent des fonctionnalités de modules complémentaires créés par l’utilisateur
  
  **Par défaut** : bloc

### <a name="windows-ink-workspace"></a>Espace de travail Windows Ink  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) dans la documentation Windows.  

- **Espace de travail Ink**  
  Spécifie s’il faut autoriser l’utilisateur à accéder à l’espace de travail Ink. 
  - *Désactivé* : l’accès à l’espace de travail Ink est désactivé. La fonctionnalité est désactivée.
  - *Activé* : la fonctionnalité Espace de travail Ink est activée, mais l’utilisateur ne peut pas y accéder sur l’écran de verrouillage.
  - *Non configuré* : la fonctionnalité Espace de travail Ink est activée, mais l’utilisateur ne peut pas y accéder sur l’écran de verrouillage.  

  **Par défaut** : Activé
 
### <a name="windows-powershell"></a>Windows PowerShell  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) dans la documentation Windows.  

- **Journalisation de blocs de scripts PowerShell**  
  Ce paramètre de stratégie active la journalisation de toutes les entrées de script PowerShell dans le journal des événements Microsoft-Windows-PowerShell/Operational. Si vous activez ce paramètre de stratégie, Windows PowerShell journalise le traitement des commandes, les blocs de script, les fonctions et les scripts, qu’il soit appelé de façon interactive ou via l’automatisation. Si vous désactivez ce paramètre de stratégie, la journalisation des entrées de script PowerShell est désactivée. Si vous activez la journalisation des appels de bloc de script, PowerShell journalise en plus les événements lors de l’appel d’une commande, un bloc de script, d’une fonction, ou quand un script démarre ou s’arrête. L’activation de la journalisation des appels génère un grand volume de journaux des événements. Remarque : Ce paramètre de stratégie existe à la fois sous Configuration ordinateur et Configuration utilisateur dans l’Éditeur de stratégie de groupe. Le paramètre de stratégie de Configuration ordinateur est prioritaire sur le paramètre de stratégie Configuration utilisateur.
  
  **Par défaut** : Activé
 
## <a name="next-steps"></a>Étapes suivantes  

[Afficher la version actuelle de la ligne de base](security-baseline-settings-mdm.md)  
[Profils de mise à niveau pour utiliser une nouvelle version de ligne de base](security-baselines.md#change-the-baseline-instance-for-a-profile)