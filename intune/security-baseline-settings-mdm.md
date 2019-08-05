---
title: Paramètres de base de référence de la sécurité Intune pour Windows 10
titleSuffix: Microsoft Intune
description: Passez en revue les valeurs par défaut et les paramètres disponibles qui se trouvent dans la ligne de base de sécurité Windows MDM pour les appareils Windows 10 que vous gérez avec Intune.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5565ce7a355136a749d79b52e4830af91684440a
ms.sourcegitcommit: 864fdf995c2b41f104a98a7e2665088c2864774f
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68680037"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Paramètres de base de référence de la sécurité GPM pour Intune  

Affichez les paramètres de ligne de base de sécurité MDM pris en charge par Microsoft Intune pour les appareils qui exécutent Windows 10 ou version ultérieure. Les valeurs par défaut des paramètres de cette base de référence représentent la configuration recommandée pour les appareils applicables et peuvent ne pas correspondre aux valeurs par défaut de référence des autres lignes de base de sécurité.  

La dernière version de référence est la **ligne de base de sécurité MDM pour mai 2019**  

Pour en savoir plus sur les modifications apportées à la version la plus récente de cette base de référence à partir de la version précédente, consultez [ce qui a changé dans le nouveau modèle](#whats-changed-in-the-new-template).  

> [!NOTE]  
> En juin 2019, la ligne de base de sécurité MDM préliminaire a été remplacée par la publication de la *ligne de base de sécurité MDM pour le modèle mai 2019* , qui est généralement disponible (pas en version préliminaire). Les profils qui ont été créés avant la disponibilité de la ligne de base de *sécurité MDM pour la ligne de base de mai 2019* ne sont pas mis à jour pour refléter les paramètres et valeurs de la ligne de base de sécurité MDM pour la version de mai 2019.  Bien que vous ne puissiez pas créer de nouveaux profils basés sur le modèle d’aperçu, vous pouvez modifier et continuer à utiliser les profils que vous avez créés précédemment, basés sur le modèle d’aperçu.   
  
Pour en savoir plus sur l’utilisation des lignes de base de sécurité avec Intune, consultez [utiliser des lignes de base de sécurité](security-baselines.md).  


   
## <a name="above-lock"></a>Au-dessus du verrouillage  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) dans la documentation Windows.  

- **Bloquer l’affichage des notifications toast**  
  Ce paramètre de stratégie vous permet d’empêcher les notifications des applications d’apparaître sur l’écran de verrouillage. Si vous activez ce paramètre de stratégie, aucune notification d’application ne s’affiche sur l’écran de verrouillage. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs peuvent choisir les applications qui affichent des notifications sur l’écran de verrouillage.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Par défaut** : oui  

- **Activer les applications vocales à partir de l’écran verrouillé**  

  **Par défaut** : Désactivé

## <a name="app-runtime"></a>Runtime d’application    
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) dans la documentation Windows.  

- **Comptes Microsoft facultatifs pour les applications du Windows Store**  
  Ce paramètre de stratégie vous permet de déterminer si les comptes Microsoft sont facultatifs pour les applications du Windows Store qui nécessitent un compte pour la connexion. Cette stratégie affecte uniquement les applications du Windows Store qui le prennent en charge. Si vous activez ce paramètre de stratégie, les applications du Windows Store qui nécessitent normalement un compte Microsoft pour la connexion autorisent les utilisateurs à se connecter avec un compte d’entreprise. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs doivent se connecter avec un compte Microsoft.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Par défaut** : Activé  

## <a name="application-management"></a>Gestion des applications   
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) dans la documentation Windows.  

- **Bloquer le contrôle utilisateur sur les installations**  
  Ce paramètre de stratégie permet aux utilisateurs de modifier les options d’installation qui ne sont généralement disponibles que pour les administrateurs système. Si vous activez ce paramètre de stratégie, certaines des fonctionnalités de sécurité de Windows Installer sont ignorées. Il permet d’effectuer des installations qui, sinon, sont interrompues en raison d’une violation de sécurité. Si vous désactivez ou ne configurez pas ce paramètre de stratégie, les fonctionnalités de sécurité de Windows Installer empêchent les utilisateurs de modifier les options d’installation généralement réservées aux administrateurs système, par exemple en spécifiant le répertoire dans lequel les fichiers sont installés. Si Windows Installer détecte qu’un package d’installation a autorisé l’utilisateur à modifier une option protégée, il arrête l’installation et affiche un message. Ces fonctionnalités de sécurité fonctionnent uniquement lorsque le programme d’installation s’exécute dans un contexte de sécurité privilégié dans lequel il a accès aux répertoires refusés à l’utilisateur. Ce paramètre de stratégie est conçu pour les environnements moins restrictifs. Il peut être utilisé pour contourner les erreurs dans un programme d’installation qui empêche l’installation de logiciels.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Par défaut** : oui

- **Bloquer les installations d’applications MSI avec des privilèges élevés**  
  Ce paramètre de stratégie dirige Windows Installer pour utiliser des autorisations élevées quand il installe un programme sur le système.  
  - *Si vous activez ce paramètre de stratégie*, les privilèges sont étendus à tous les programmes. Ces privilèges sont généralement réservés pour les programmes qui ont été attribués à l’utilisateur (proposés sur le bureau), attribués à l’ordinateur (installé automatiquement) f ou mis à disposition dans Ajout/suppression de programmes dans le panneau de configuration. Ce paramètre de profil permet aux utilisateurs d’installer des programmes qui requièrent l’accès à des répertoires que l’utilisateur n’a pas l’autorisation d’afficher ou de modifier, y compris les répertoires sur les ordinateurs à haut niveau de restriction.
  - *Si vous désactivez ou ne configurez pas ce paramètre de stratégie*, le système applique les autorisations de l’utilisateur actuel lors de l’installation de programmes qu’un administrateur système ne distribue pas ou n’offre pas. Remarque : ce paramètre de stratégie apparaît dans les dossiers Configuration ordinateur et Configuration utilisateur. Pour que ce paramètre de stratégie soit effectif, vous devez l’activer dans les deux dossiers. ATTENTION: les utilisateurs expérimentés peuvent tirer parti des autorisations accordées par ce paramètre de stratégie pour modifier leurs privilèges et obtenir un accès permanent aux fichiers et dossiers restreints. Notez que la sécurité de la version de la configuration utilisateur de ce paramètre de stratégie n’est pas garantie.  
  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Par défaut** : oui

- **Bloquer Jeux DVR (Desktop uniquement)**  
  Détermine si l’enregistrement et la diffusion des jeux sont autorisés ou non.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Par défaut** : oui  

## <a name="auto-play"></a>Lecture automatique   
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) dans la documentation Windows.  

- **Comportement d’exécution automatique par défaut de la lecture automatique**  
  Ce paramètre affecte le comportement par défaut des commandes Autorun. Les commandes Autorun sont stockées dans des fichiers autorun.inf et peuvent lancer des programmes d’installation ou d’autres routines. Si ce paramètre est *activé*, les administrateurs peuvent changer le comportement d’Autorun par défaut sur un appareil qui exécute Windows Vista ou ultérieur. Le comportement peut : a) désactiver complètement les commandes Autorun, ou b) rétablir le comportement antérieur à Windows Vista qui consiste à exécuter automatiquement la commande Autorun. Si ce paramètre est *Désactivé* ou *Non configuré*, les appareils exécutant Windows Vista ou ultérieur demandent à l’utilisateur d’exécuter ou non la commande Autorun.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Par défaut** : ne pas exécuter  
  
- **Mode lecture automatique**  
  Ce paramètre de stratégie vous permet de désactiver la fonctionnalité de lecture automatique. La lecture automatique commence à lire le média d’un lecteur dès son insertion. Les fichiers d’installation des programmes et la musique des médias audio démarrent donc immédiatement. Avant Windows XP SP2, la lecture automatique était désactivée par défaut sur les lecteurs amovibles, tels que les lecteurs de disquettes (mais pas sur le lecteur de CD-ROM), ainsi que sur les lecteurs réseau. Depuis Windows XP SP2, la lecture automatique est également activée pour les lecteurs amovibles, notamment les lecteurs ZIP et certains périphériques de stockage de masse USB. Si vous activez ce paramètre de stratégie, vous désactivez la lecture automatique sur les lecteurs de CD-ROM et les lecteurs de médias amovibles, ou sur tous les lecteurs. Ce paramètre de stratégie désactive la lecture automatique sur les autres types de lecteurs. Vous ne pouvez pas utiliser ce paramètre pour activer la lecture automatique sur des lecteurs où elle est désactivée par défaut. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la lecture automatique est activée. Remarque : Ce paramètre de stratégie apparaît dans les dossiers Configuration ordinateur et Configuration utilisateur. Si les paramètres de stratégie sont en conflit, le paramètre de stratégie du dossier Configuration ordinateur a priorité sur le paramètre du dossier Configuration utilisateur.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Par défaut** : Désactivé

- **Bloquer la lecture automatique pour les périphériques autres que ceux du volume**  
  Ce paramètre de stratégie interdit la lecture automatique pour les périphériques MTP, tels que les appareils photo ou les téléphones. Si vous activez ce paramètre de stratégie, la lecture automatique est interdite pour les périphériques MTP, tels que les caméras ou les téléphones. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la lecture automatique est activée pour les périphériques autres que ceux du volume.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Par défaut** : Activé  

## <a name="bitlocker"></a>Bitlocker    
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) dans la documentation Windows.  

- **Stratégie de lecteur amovible BitLocker**  
  Ce paramètre de stratégie permet de contrôler la méthode et le niveau de chiffrement. Les valeurs de cette stratégie déterminent la force du chiffrement utilisé par BitLocker pour le chiffrement. Les entreprises peuvent contrôler le niveau de chiffrement pour renforcer la sécurité (AES-256 est plus puissant que AES-128). Si vous activez ce paramètre, vous pouvez configurer un algorithme de chiffrement et la puissance de chiffrement clé pour les lecteurs de données fixes, les lecteurs de système d’exploitation et les lecteurs de données amovibles individuellement. Pour les lecteurs du système fixe et de fonctionnement, nous vous recommandons d’utiliser l’algorithme AES-XTS. Pour les lecteurs amovibles, vous devez utiliser AES-CBC 128 bits ou AES-CBC 256 bits si le lecteur est utilisé sur d’autres appareils qui n’exécutent pas la version 1511 de Windows 10 ou une version ultérieure. Le changement de la méthode de chiffrement est sans effet si le disque est déjà chiffré ou si le chiffrement est en cours. Dans ces cas, ce paramètre de stratégie est ignoré.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Pour la stratégie de lecteur amovible BitLocker, configurez le paramètre suivant :

  - **Exiger le chiffrement pour l’accès en écriture**  
    **Par défaut** : oui  
  

## <a name="browser"></a>Navigateur  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) dans la documentation Windows.  

- **Exiger SmartScreen pour Microsoft Edge**  
  Microsoft Edge utilise Windows Defender SmartScreen (activé) pour protéger les utilisateurs contre d’éventuels courriers indésirables d’hameçonnage et logiciels malveillants par défaut. Par ailleurs, les utilisateurs ne peuvent pas désactiver Windows Defender SmartScreen par défaut. L’activation de cette stratégie désactive Windows Defender SmartScreen et empêche les utilisateurs de l’activer. Ne configurez pas cette stratégie pour permettre aux utilisateurs de choisir d’activer ou non Windows Defender SmartScreen.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Par défaut** : oui  
  
- **Bloquer l’accès aux sites malveillants**  
  Par défaut, Microsoft Edge permet aux utilisateurs de contourner (ignorer) les avertissements de Windows Defender SmartScreen relatifs aux fichiers potentiellement malveillants, leur permettant ainsi d’accéder au site. Toutefois, avec cette stratégie, vous pouvez configurer Microsoft Edge de manière à empêcher les utilisateurs de contourner les avertissements, les empêchant ainsi d’accéder au site.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Par défaut** : oui  
  
- **Bloquer le téléchargement des fichiers non vérifiés**  
  Par défaut, Microsoft Edge permet aux utilisateurs de contourner (ignorer) les avertissements de Windows Defender SmartScreen relatifs aux fichiers potentiellement malveillants, leur permettant ainsi de continuer à télécharger le ou les fichiers non vérifiés. L’activation de cette stratégie empêche les utilisateurs de contourner les avertissements, ce qui leur interdit de télécharger le ou les fichiers non vérifiés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Par défaut** : oui  
  
- **Bloquer le gestionnaire de mots de passe**  
  Par défaut, Microsoft Edge utilise automatiquement le gestionnaire de mots de passe, ce qui permet aux utilisateurs de gérer leurs mots de passe localement. Si vous désactivez cette stratégie, Microsoft Edge ne peut pas utiliser le gestionnaire de mots de passe. Si vous ne configurez pas cette stratégie, les utilisateurs peuvent choisir d’enregistrer et de gérer leurs mots de passe localement à l’aide du gestionnaire de mots de passe.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Par défaut** : oui  
  
- **Empêcher les utilisateurs de passer outre les erreurs de certificat**  
  Ce paramètre de stratégie empêche l’utilisateur d’ignorer les erreurs de certificat SSL/TLS (Secure Sockets Layer/Transport Layer Security) qui interrompent la navigation, telles que les erreurs relatives à l’expiration, à la révocation ou à une incohérence au niveau des noms dans Internet Explorer. Si vous activez ce paramètre de stratégie, l’utilisateur ne peut pas poursuivre la navigation. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut choisir d’ignorer les erreurs de certificat et poursuivre la navigation.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Par défaut** : oui  

## <a name="connectivity"></a>Connectivité  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) dans la documentation Windows.  

- **Bloquer le téléchargement à partir d’Internet pour les Assistants Publication de sites web et Commande en ligne**  
  Ce paramètre de stratégie indique si Windows doit télécharger une liste de fournisseurs pour les Assistants Publication de sites web et Commande en ligne. Ces Assistants permettent aux utilisateurs de choisir parmi une liste de sociétés offrant des services de stockage et d’impression photographique en ligne. Par défaut, Windows affiche les fournisseurs téléchargés à partir d’un site web Windows, en plus des fournisseurs spécifiés dans le Registre. Si vous activez ce paramètre de stratégie, Windows ne télécharge pas les fournisseurs, et seuls les fournisseurs de services mis en cache dans le Registre local sont affichés. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, une liste de fournisseurs est téléchargée lorsque l’utilisateur utilise les Assistants Publication de sites web ou Commande en ligne. Pour plus d’informations, consultez la documentation des Assistants Publication de sites web et Commande en ligne, notamment sur la façon de spécifier les fournisseurs de services dans le Registre.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Par défaut** : Activé  

- **Bloquer le téléchargement des pilotes d’imprimantes sur HTTP**  
  Ce paramètre de stratégie indique si ce client est autorisé à télécharger les packages de pilotes d’imprimantes sur HTTP. Pour configurer l’impression HTTP, les pilotes non fournis avec Windows doivent être téléchargés sur HTTP. Remarque : Ce paramètre de stratégie n’empêche pas le client d’imprimer sur des imprimantes du réseau intranet ou Internet sur HTTP. Il empêche uniquement le téléchargement des pilotes qui ne sont pas déjà installés localement. Si vous activez ce paramètre de stratégie, il est impossible de télécharger les pilotes d’imprimantes sur HTTP. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs peuvent télécharger des pilotes d’imprimantes sur HTTP.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Par défaut** : Activé  

## <a name="credentials-delegation"></a>Délégation des informations d’identification  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) dans la documentation Windows.  

- **Délégation par l’hôte distant d’informations d’identification non exportables**  
  L’hôte distant autorise la délégation d’informations d’identification non exportables. Lorsque vous utilisez la délégation des informations d’identification, les appareils fournissent une version exportable d’informations d’identification à l’hôte distant, ce qui expose les utilisateurs à un risque de vol des informations d’identification par des attaquants sur l’hôte distant. Si vous activez ce paramètre de stratégie, l’hôte prend en charge le mode d’administration restreinte ou Credential Guard à distance. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les modes Administration restreinte et Credential Guard à distance ne sont pas pris en charge. L’utilisateur devra toujours passer ses informations d’identification à l’hôte.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Par défaut** : Activé  

## <a name="credentials-ui"></a>Informations d’identification de l’interface utilisateur  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) dans la documentation Windows.  

- **Énumérer les administrateurs** Ce paramètre de stratégie détermine si les comptes Administrateur s’affichent lorsqu’un utilisateur tente d’élever une application en cours d’exécution. Par défaut, les comptes Administrateur ne s’affichent pas lorsque l’utilisateur tente d’élever une application en cours d’exécution. Si vous activez ce paramètre de stratégie, tous les comptes Administrateur locaux du PC s’affichent pour permettre à l’utilisateur d’en choisir un et d’entrer le mot de passe correspondant. Si vous désactivez ce paramètre de stratégie, les utilisateurs devront toujours entrer un nom d’utilisateur et un mot de passe pour avoir des privilèges élevés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Par défaut** : Désactivé  

## <a name="data-protection"></a>Protection des données  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) dans la documentation Windows.  

- **Bloquer l’accès direct à la mémoire**  
  Ce paramètre de stratégie vous permet de bloquer l’accès direct à la mémoire (DMA) pour tous les ports en aval PCI enfichables à chaud tant que l’utilisateur ne se connecte pas à Windows. Une fois l’utilisateur connecté, Windows énumère les périphériques PCI connectés aux ports PCI enfichables à chaud. À chaque verrouillage de l’ordinateur par l’utilisateur, l’Assistant Migration de données Microsoft est bloqué sur les ports PCI enfichables à chaud sans périphériques enfants, tant que l’utilisateur ne se reconnecte pas. Les périphériques déjà énumérés quand l’ordinateur a été déverrouillé continuent de fonctionner tant qu’ils sont branchés. Ce paramètre de stratégie est appliqué uniquement quand BitLocker ou le chiffrement de l’appareil est activé.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Par défaut** : oui  

## <a name="device-guard"></a>Device Guard  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) dans la documentation Windows.  

- **Credential Guard**  
  Ce paramètre permet aux utilisateurs d’activer Credential Guard avec la sécurité basée sur la virtualisation pour protéger les informations d’identification au prochain redémarrage.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Par défaut** : activer avec le verrouillage UEFI 

- **Activer la sécurité basée sur la virtualisation**   
  Active la sécurité basée sur la virtualisation au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Par défaut** : oui  


- **Lancer System Guard**    
  **Par défaut** : Activé  

## <a name="device-installation"></a>Installation de l’appareil  
Pour plus d’informations, consultez [Fournisseur de services de configuration Policy - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) dans la documentation Windows.  

- **Installation de périphériques matériels par identificateurs d’appareil**  
  Ce paramètre de stratégie permet de spécifier une liste d’ID de matériel Plug-and-Play et d’ID compatibles de périphériques que Windows ne peut pas installer. Ce paramètre de stratégie prévaut sur tout autre paramètre de stratégie autorisant l’installation de périphériques par Windows. Si vous activez ce paramètre de stratégie, Windows n’est pas autorisé à installer un périphérique dont l’ID de matériel ou l’ID compatible figure dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur Bureau à distance, il a une incidence sur la redirection des périphériques spécifiés à partir d’un client Bureau à distance vers le serveur Bureau à distance. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, des périphériques peuvent être installés et mis à jour conformément aux autorisations ou interdictions prévues par d’autres paramètres de stratégie.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
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
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Par défaut** : Bloquer l’installation de périphériques matériels  

  Lorsque la case *Bloquer l’installation du périphérique matériel* est sélectionnée, les paramètres suivants sont disponibles.
  - **Supprimer les périphériques matériels correspondants**    
    Ce paramètre est disponible seulement quand *Installation de périphériques matériels par classes d’installation* est défini sur *Bloquer l’installation de périphériques matériels*.  

    **Par défaut** : *Aucune configuration par défaut*  

  - **Identificateurs de périphériques matériels bloqués**  
    Ce paramètre est disponible seulement quand *Installation de périphériques matériels par classes d’installation* est défini sur *Bloquer l’installation de périphériques matériels*.
    
    **Par défaut** : *Aucune configuration par défaut*  

## <a name="device-lock"></a>Verrouillage d’appareil  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) dans la documentation Windows.  

- **Empêcher l’utilisation de l’appareil photo**  
  Désactive le commutateur de verrouillage de l’appareil photo sur l’écran dans Paramètres du PC et empêche l’appel de l’appareil photo sur l’écran de verrouillage. Par défaut, les utilisateurs peuvent activer l’appel d’une caméra disponible sur l’écran de verrouillage. Si vous activez ce paramètre, les utilisateurs ne sont plus en mesure d’activer ou de désactiver l’accès de la caméra sur l’écran de verrouillage dans Paramètres du PC, et la caméra ne peut pas être appelée sur l’écran de verrouillage.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Par défaut** : Activé  

- **Exiger un mot de passe**  
  Spécifie si le verrouillage de l’appareil est activé.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Par défaut** : oui  
  
  Lorsque *Mot de passe requis* est défini sur *Oui*, les paramètres suivants sont disponibles.

  - **Nombre minimal de jeux de caractères du mot de passe**  
    Nombre de types d’éléments complexes (lettres majuscules et minuscules, chiffres et ponctuation) obligatoires pour un mot de passe ou un code PIN fort. Le PIN impose le comportement suivant aux appareils de bureau et mobiles : 1 - Chiffres uniquement 2 - Chiffres et lettres majuscules obligatoires 3 - Chiffres, lettres majuscules et lettres minuscules obligatoires. Non pris en charge dans les comptes Microsoft et les comptes de domaine des postes de travail. 4 : Chiffres, lettres minuscules, lettres majuscules et caractères spéciaux obligatoires. Non pris en charge sur les postes de travail. La valeur par défaut est 1.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **Par défaut** : 3  

  - **Nombre d’échecs de connexion avant réinitialisation de l’appareil**  
    Le nombre d’échecs d’authentification autorisé avant la réinitialisation de l’appareil. La valeur 0 désactive la fonctionnalité de réinitialisation de l’appareil.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **Par défaut** : 10  

  - **Expiration du mot de passe (jours)**  
    Le paramètre de stratégie Antériorité maximale du mot de passe détermine la période (en jours) pendant laquelle un mot de passe peut être utilisé avant que le système oblige l’utilisateur à le changer. Vous pouvez définir l’expiration des mots de passe après un nombre de jours compris entre 1 et 999, ou vous pouvez spécifier que les mots de passe n’expirent jamais en définissant le nombre de jours sur 0. Si Antériorité maximale du mot de passe est compris entre 1 et 999 jours, l’antériorité minimale du mot de passe doit être inférieure à son antériorité maximale. Si Antériorité maximale du mot de passe est défini sur 0, Antériorité minimale du mot de passe peut avoir une valeur comprise entre 0 et 998 jours.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **Par défaut** : 60  

  - **Type de mot de passe requis**  
    Détermine le type de code PIN ou de mot de passe exigé.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **Par défaut** : alphanumérique  

  - **Longueur minimale du mot de passe**  
    Le paramètre de stratégie Longueur minimale du mot de passe détermine le plus petit nombre de caractères qui peuvent constituer un mot de passe pour un compte d’utilisateur. Vous pouvez définir une valeur comprise entre 1 et 14 caractères, ou vous pouvez établir qu’aucun mot de passe n’est exigé en définissant le nombre de caractères sur 0.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **Par défaut** : 8  

  - **Bloquer les mots de passe simples**  
    Spécifie si les codes PIN ou les mots de passe comme « 1111 » ou « 1234 » sont autorisés. Pour le poste de travail, il contrôle également l’utilisation de mots de passe image.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **Par défaut** : oui  
      *La valeur Oui empêche l’utilisation de mots de passe simples.* 

  - **Empêcher la réutilisation des mots de passe précédents**  
    Spécifie le nombre de mots de passe à stocker dans l’historique des mots de passe qui ne peuvent pas être utilisés. Ceci comprend le mot de passe actuel de l’utilisateur. Par exemple, avec un paramètre de *1* l’utilisateur ne peut pas réutiliser son mot de passe actuel lors du choix d’un nouveau mot de passe. Un paramètre de *5* signifie qu’un utilisateur ne peut pas définir son nouveau mot de passe sur leur mot de passe actuel ni l’un de ses quatre mots de passe précédents.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Par défaut** : 24  

- **Empêcher le diaporama**  
  Désactive les paramètres de diaporama de l’écran de verrouillage dans Paramètres du PC et empêche l’affichage d’un diaporama sur l’écran de verrouillage. Par défaut, les utilisateurs peuvent activer un diaporama qui s’exécute après avoir verrouillé l’ordinateur. Si vous activez ce paramètre, les utilisateurs ne peuvent plus modifier les paramètres du diaporama dans Paramètres du PC et aucun diaporama ne peut démarrer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Par défaut** : Activé  
  *La valeur Activé empêche l’exécution des diaporamas.* 

- **Antériorité minimale du mot de passe en jours**  
  Le paramètre de stratégie Antériorité minimale du mot de passe détermine la période (en jours) pendant laquelle un mot de passe doit être utilisé avant que l’utilisateur puisse le changer. Vous pouvez définir une valeur comprise entre 1 et 998 jours, ou vous pouvez autoriser les changements de mot de passe immédiatement en définissant le nombre de jours sur 0. L’antériorité minimale du mot de passe doit être inférieure à l’antériorité maximale du mot de passe, sauf si celle-ci est définie sur 0, indiquant que les mots de passe n’expirent jamais. Si l’antériorité maximale du mot de passe est définie sur 0, l’antériorité minimale du mot de passe peut avoir une valeur comprise entre 0 et 998.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Par défaut** : 1  

## <a name="dma-guard"></a>Protection de DMA  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) dans la documentation Windows.
- **Énumération des périphériques externes incompatibles avec la protection DMA de noyau**  
  Cette stratégie est conçue pour fournir une sécurité supplémentaire sur les périphériques externes qui prennent en charge l’accès direct. Elle permet de mieux contrôler l’énumération des appareils compatibles DMA externes qui sont incompatibles avec le sandboxing et l’isolation de la mémoire de l’appareil / du remappage DMA. Cette stratégie n’entre en vigueur que lorsque la protection DMA de noyau est prise en charge et activée par le microprogramme système. La protection DMA du noyau est une fonctionnalité de plateforme qui ne peut pas être contrôlée via une stratégie ou par un utilisateur final. Il doit être pris en charge par le système au moment de la fabrication. Pour vérifier si le système prend en charge la protection DMA du noyau, consultez le champ protection DMA du noyau dans la page Résumé de MSINFO32. exe.  
  [En savoir plus](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Par défaut** : tout bloquer   

## <a name="event-log-service"></a>Service Journal des événements  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) dans la documentation Windows.  

- **Taille de fichier maximale du journal de sécurité en Ko**  
  Ce paramètre de stratégie spécifie la taille maximale du fichier journal en Ko. Si vous activez ce paramètre de stratégie, vous pouvez configurer la taille maximale du fichier journal à une valeur comprise entre 1 Mo (1 024 Ko) et 2 To (2 147 483 647 Ko), par incréments d’un Ko. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la taille maximale du fichier journal est définie sur la valeur configurée localement. L’administrateur local peut changer cette valeur via la boîte de dialogue Propriétés du journal ; sa valeur par défaut est de 20 Mo.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Par défaut** : 196608  

- **Taille de fichier maximale du journal système en Ko**  
  Ce paramètre de stratégie spécifie la taille maximale du fichier journal en Ko. Si vous activez ce paramètre de stratégie, vous pouvez configurer la taille maximale du fichier journal à une valeur comprise entre 1 Mo (1 024 Ko) et 2 To (2 147 483 647 Ko), par incréments d’un Ko. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la taille maximale du fichier journal est définie sur la valeur configurée localement. L’administrateur local peut changer cette valeur via la boîte de dialogue Propriétés du journal ; sa valeur par défaut est de 20 Mo.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Par défaut** : 32768  

- **Taille de fichier maximale du journal des applications en Ko**  
  Ce paramètre de stratégie spécifie la taille maximale du fichier journal en Ko. Si vous activez ce paramètre de stratégie, vous pouvez configurer la taille maximale du fichier journal à une valeur comprise entre 1 Mo (1 024 Ko) et 2 To (2 147 483 647 Ko), par incréments d’un Ko. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la taille maximale du fichier journal est définie sur la valeur configurée localement. L’administrateur local peut changer cette valeur via la boîte de dialogue Propriétés du journal ; sa valeur par défaut est de 20 Mo.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Par défaut** : 32768  

## <a name="experience"></a>Expérience  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Expérience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) dans la documentation Windows.  

- **Bloquer Windows à la une**  
  Permet aux administrateurs informatiques de désactiver toutes les fonctionnalités de Windows à la une : Windows à la une sur l’écran de verrouillage, Conseils Windows, les fonctionnalités Microsoft grand public et d’autres fonctionnalités associées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Par défaut** : oui  

  Lorsque *Bloquer les informations à la une Windows* est défini sur *Oui*, les paramètres suivants sont disponibles.
  
  - **Bloquer les suggestions de tiers dans Windows à la une**  
    Spécifie s’il faut autoriser les suggestions d’applications et de contenu provenant d’éditeurs de logiciels tiers dans les fonctionnalités de Windows à la une, comme la une sur l’écran de verrouillage, les applications suggérées dans le menu Démarrer et les conseils Windows. Les utilisateurs peuvent quand même voir les suggestions de fonctionnalités, d’applications et de services Microsoft.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Par défaut** : oui  
  - **Bloquer les fonctionnalités spécifiques au grand public**  
    Permet aux administrateurs informatiques d’activer les fonctionnalités destinées au grand public uniquement, comme les suggestions du démarrage, les notifications d’appartenance, l’installation d’application post-OOBE et les vignettes de redirection.  
    [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Par défaut** : oui  

## <a name="exploit-guard"></a>Exploit Guard  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) dans la documentation Windows.  

- **Protection contre le code malveillant XML**  
  Permet à l’administrateur informatique de diffuser une configuration qui représente les options souhaitées d’atténuation des risques pour le système et les applications auprès de tous les appareils de l’organisation. La configuration est représentée par du code XML. Exploit Protection aide à protéger les appareils contre les programmes malveillants qui utilisent du code malveillant exploitant une faille de sécurité pour se propager et les infecter. Utilisez l’application Sécurité Windows ou PowerShell pour créer un ensemble d’atténuations des risques (qui est appelé « configuration »). Vous pouvez ensuite exporter cette configuration dans un fichier XML et le partager sur plusieurs machines de votre réseau pour donner à toutes le même ensemble de paramètres d’atténuation des risques. Vous pouvez aussi convertir et importer un fichier XML de configuration EMET existant en un fichier XML de configuration de protection contre le code malveillant.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Par défaut** : *un exemple de code XML est fourni* 
 
## <a name="file-explorer"></a>Explorateur de fichiers  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) dans la documentation Windows.  

- **Bloquer la prévention de l’exécution des données**  
  La désactivation de la prévention de l’exécution des données peut permettre à certaines applications de plug-in héritées de fonctionner sans arrêter l’Explorateur.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Par défaut** : Désactivé  
   
- **Bloquer l’arrêt du tas en cas de défaillance**  
  La désactivation de l’arrêt du tas en cas de défaillance peut permettre à certaines applications de plug-in héritées de fonctionner sans arrêter immédiatement l’Explorateur, même si l’Explorateur peut néanmoins s’arrêter ultérieurement de façon inattendue.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Par défaut** : Désactivé  
    

## <a name="internet-explorer"></a>Internet Explorer  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) dans la documentation Windows.  

- **La zone restreinte Internet Explorer met à jour la barre d’état via un script**  
  Ce paramètre de stratégie vous permet de spécifier si un script est autorisé à mettre à jour la barre d’état dans la zone. 
  - *Si vous activez ce paramètre de stratégie*, le script est autorisé à mettre à jour la barre d’état.
  - *Si vous désactivez ou ne configurez pas ce paramètre de stratégie*, le script n’est pas autorisé à mettre à jour la barre d’état.  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Par défaut** : Désactivé

- **Fichiers glisser et déplacer ou copier et coller de la zone internet Internet Explorer**  
  Ce paramètre de stratégie vous permet de spécifier si les utilisateurs peuvent faire glisser ou copier et coller des fichiers à partir d’une source dans la zone. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent faire glisser ou copier et coller des fichiers à partir de cette zone automatiquement. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent faire glisser ou copier des fichiers à partir de cette zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas faire glisser ni copier et coller des fichiers à partir de cette zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs peuvent faire glisser ou copier et coller des fichiers à partir de cette zone automatiquement.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Par défaut**: désactiver

- **Composants dépendants du .NET Framework de la zone restreinte Internet Explorer**    
  Ce paramètre de stratégie vous permet d’indiquer si les composants .NET Framework qui ne sont pas signés avec Authenticode peuvent être exécutés à partir d’Internet Explorer. Ces composants incluent les contrôles managés référencés à partir d’une balise object et les exécutables managés référencés à partir d’un lien. Si vous activez ce paramètre de stratégie, Internet Explorer exécute les composants managés non signés. Si vous sélectionnez Demander dans la liste déroulante, Internet Explorer demande aux utilisateurs s’ils souhaitent exécuter les composants managés non signés. Si vous désactivez ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés non signés. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés non signés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Par défaut**: désactiver


- **La zone de l’ordinateur local Internet Explorer n’exécute pas de logiciel anti-programme malveillant sur les contrôles ActiveX**  
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Par défaut** : Désactivé

- **Internet Explorer > Zone Internet : accès aux sources de données**  
  Ce paramètre de stratégie vous permet d’indiquer si Internet Explorer peut accéder aux données provenant d’une autre zone de sécurité en utilisant le moteur d’analyse XML de Microsoft (MSXML) ou les objets ADO (ActiveX Data Objects). Si vous activez ce paramètre de stratégie, les utilisateurs peuvent charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement d’une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Faire glisser du contenu provenant de domaines différents dans les fenêtres**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs ne peuvent pas modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans la même fenêtre. Les utilisateurs ne peuvent pas modifier ce paramètre dans la boîte de dialogue Options Internet.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Par défaut** : Désactivé
  
- **Internet Explorer : Avertissement de non-correspondance d’adresse de certificat**  
  Ce paramètre de stratégie vous permet d’activer l’avertissement de sécurité de non-correspondance d’adresse de certificat. Quand ce paramètre de stratégie est activé, l’utilisateur est averti lors de la visite de sites web HTTP sécurisé (HTTPS) qui présentent des certificats émis pour une autre adresse de site web. Cet avertissement permet d’empêcher les attaques par usurpation d’identité. Si vous activez ce paramètre de stratégie, l’avertissement de non-correspondance d’adresse de certificat apparaît toujours. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut choisir d’afficher l’avertissement de non-correspondance d’adresse de certificat (en utilisant la page Avancé du Panneau de configuration Internet).  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone restreinte : Sites de moindre privilège**  
  Ce paramètre de stratégie vous permet de spécifier si des sites web de zones de moindre privilège, comme des sites Internet, peuvent accéder à cette zone. Si vous activez ce paramètre de stratégie, les sites web des zones de moindre privilège peuvent ouvrir de nouvelles fenêtres dans cette zone ou y accéder. La zone de sécurité fonctionne sans la couche de sécurité supplémentaire qui est fournie par la fonctionnalité Protection contre l’élévation de zone. Si vous sélectionnez Demander dans la zone de liste déroulante, l’utilisateur est averti qu’un accès potentiellement risqué est sur le point de se produire. Si vous désactivez ce paramètre de stratégie, les accès potentiellement dangereux sont empêchés. La fonctionnalité de sécurité d’Internet Explorer est activée sur cette zone comme défini par le contrôle de la fonctionnalité Protection contre l’élévation de zone. Si vous ne configurez pas ce paramètre de stratégie, les accès potentiellement dangereux sont empêchés. La fonctionnalité de sécurité d’Internet Explorer est activée sur cette zone comme défini par le contrôle de la fonctionnalité Protection contre l’élévation de zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Demande automatique pour les téléchargements de fichiers**  
  Ce paramètre de stratégie détermine si les utilisateurs sont invités à autoriser les téléchargements de fichiers qu’ils n’ont pas eux-mêmes demandés. Quelle que soit la valeur de ce paramètre, des boîtes de dialogue de téléchargement de fichier sont montrées aux utilisateurs pour les téléchargements demandés par eux-mêmes. Si vous activez ce paramètre, une boîte de dialogue de téléchargement de fichier est montrée aux utilisateurs pour les tentatives de téléchargement automatique. Si vous désactivez ce paramètre ou ne le configurez pas, les téléchargements de fichiers qui ne sont pas demandés par les utilisateurs sont bloqués, et les utilisateurs voient la barre de notification au lieu de la boîte de dialogue de téléchargement de fichier. Les utilisateurs peuvent alors cliquer sur la barre de notification pour voir l’invite de téléchargement de fichier.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Par défaut** : Désactivé
  
- **Internet Explorer > Zone Internet : Composants dépendant du .NET Framework**  
  Ce paramètre de stratégie vous permet d’indiquer si les composants .NET Framework non signés avec Authenticode peuvent s’exécuter dans Internet Explorer. Ces composants incluent les contrôles managés référencés par une balise objet et les exécutables managés référencés à partir d’un lien. Si vous activez ce paramètre de stratégie, Internet Explorer exécute les composants managés non signés. Si vous sélectionnez Demander dans la liste déroulante, Internet Explorer demande aux utilisateurs s’ils souhaitent exécuter les composants managés non signés. Si vous désactivez ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés non signés. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer exécute les composants managés non signés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Zone Internet : Autoriser uniquement les domaines approuvés à utiliser le contrôle ActiveX TDC**  
  Ce paramètre de stratégie contrôle si l’utilisateur est ou non autorisé à exécuter le contrôle ActiveX TDC sur des sites web. Si vous activez ce paramètre de stratégie, le contrôle ActiveX TDC n’est pas exécuté sur les sites web de cette zone. Si vous désactivez ce paramètre de stratégie, le contrôle ActiveX TDC s’exécute sur tous les sites de cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone restreinte : Fenêtres lancées par des scripts**  
  Ce paramètre de stratégie permet de gérer les restrictions sur les fenêtres indépendantes lancées par des scripts, et sur celles qui incluent les barres de titre et d’état. Si vous activez ce paramètre de stratégie, la fonctionnalité de sécurité des Restrictions des fenêtres ne s’applique pas à cette zone. La zone de sécurité s’exécute sans la couche de sécurité supplémentaire fournie par cette fonctionnalité. Si vous désactivez ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts. Si vous ne configurez pas ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Internet : Inclure le chemin local lors du chargement de fichiers sur un serveur**  
  Ce paramètre de stratégie spécifie si les informations du chemin d’accès local sont envoyées ou non lorsque l’utilisateur charge un fichier via un formulaire HTML. Si les informations de chemin local sont envoyées, certaines informations peuvent être involontairement révélées au serveur. Par exemple, des fichiers envoyés à partir du Bureau de l’utilisateur peuvent avoir un chemin contenant le nom de l’utilisateur. Si vous activez ce paramètre de stratégie, les informations de chemin sont envoyées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous désactivez ce paramètre de stratégie, les informations de chemin sont supprimées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si les informations du chemin d’accès sont envoyées lorsqu’il charge un fichier via un formulaire HTML. Par défaut, les informations de chemin sont envoyées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Désactiver les processus en mode protégé amélioré**  
  Ce paramètre de stratégie détermine si Internet Explorer 11 utilise des processus 64 bits (pour une sécurité renforcée) ou des processus 32 bits (pour une meilleure compatibilité) lors de l’exécution en mode protégé amélioré sur les versions 64 bits de Windows. Important : Certains contrôles ActiveX et certaines barres d’outils risquent de ne pas être disponibles lorsque des processus 64 bits sont utilisés. Si vous activez ce paramètre de stratégie, Internet Explorer 11 utilise des processus d’onglet 64 bits lors de l’exécution en mode protégé amélioré sur les versions 64 bits de Windows. Si vous désactivez ce paramètre de stratégie, Internet Explorer 11 utilise des processus d’onglet 32 bits lors de l’exécution en mode protégé amélioré sur les versions 64 bits de Windows. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs peuvent activer ou désactiver cette fonctionnalité via les paramètres d’Internet Explorer. Cette fonctionnalité est désactivée par défaut.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Ignorer les erreurs de certificat**  
  Ce paramètre de stratégie empêche l’utilisateur d’ignorer les erreurs de certificat SSL/TLS (Secure Sockets Layer/Transport Layer Security) qui interrompent la navigation, telles que les erreurs relatives à l’expiration, à la révocation ou à une incohérence au niveau des noms dans Internet Explorer. Si vous activez ce paramètre de stratégie, l’utilisateur ne peut pas poursuivre la navigation. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut choisir d’ignorer les erreurs de certificat et poursuivre la navigation.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Internet : Chargement des fichiers XAML**  
  Ce paramètre de stratégie vous permet de gérer le chargement des fichiers XAML (Extensible Application Markup Language). Le langage XAML est un langage de balisage déclaratif basé sur le langage XML et couramment utilisé pour la création d’interfaces utilisateur et de graphismes avancés qui tirent parti de Windows Presentation Foundation. Si vous activez ce paramètre de stratégie et si vous affectez la valeur Activer à la zone de liste déroulante, les fichiers XAML sont automatiquement chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous affectez la valeur Demander à la zone de liste déroulante, l’utilisateur est invité à confirmer le chargement des fichiers XAML. Si vous désactivez ce paramètre de stratégie, les fichiers XAML ne sont pas chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur est libre de charger ou non les fichiers XAML dans Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Zone Internet : Demande automatique pour les téléchargements de fichiers**  
  Ce paramètre de stratégie détermine si les utilisateurs sont invités à autoriser les téléchargements de fichiers qu’ils n’ont pas eux-mêmes demandés. Quelle que soit la valeur de ce paramètre, des boîtes de dialogue de téléchargement de fichier sont montrées aux utilisateurs pour les téléchargements demandés par eux-mêmes. Si vous activez ce paramètre, une boîte de dialogue de téléchargement de fichier est montrée aux utilisateurs pour les tentatives de téléchargement automatique. Si vous désactivez ce paramètre ou ne le configurez pas, les téléchargements de fichiers qui ne sont pas demandés par les utilisateurs sont bloqués, et les utilisateurs voient la barre de notification au lieu de la boîte de dialogue de téléchargement de fichier. Les utilisateurs peuvent alors cliquer sur la barre de notification pour voir l’invite de téléchargement de fichier.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Avertissement de sécurité pour les fichiers potentiellement dangereux**  
  Ce paramètre de stratégie détermine si le message « Fichier ouvert : Avertissement de sécurité » s’affiche lorsque l’utilisateur essaie d’ouvrir des fichiers exécutables ou d’autres fichiers potentiellement non sécurisés (à partir d’un partage de fichiers intranet via l’Explorateur de fichiers, par exemple). Si vous activez ce paramètre de stratégie et affectez la valeur Activer à la zone de liste déroulante, les fichiers concernés s’ouvrent sans avertissement de sécurité préalable. Si vous affectez la valeur Demander à la zone de liste déroulante, un avertissement de sécurité s’affiche avant l’ouverture des fichiers. Si vous désactivez ce paramètre de stratégie, les fichiers concernés ne s’ouvrent pas. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut configurer la façon dont l’ordinateur gère ces fichiers. Par défaut, ces fichiers sont bloqués dans la zone restreinte, activés dans les zones Intranet et Ordinateur local, et définis sur Demander dans les zones Internet et de confiance.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Filtre anti-script de site à site**  
  Cette stratégie détermine si le filtre anti-script de site à site (XSS) détecte et évite les injections de script de site à site dans les sites web de cette zone. Si vous activez ce paramètre de stratégie, le filtre XSS est activé pour les sites de cette zone et tente de bloquer les injections de script de site à site. Si vous désactivez ce paramètre de stratégie, le filtre XSS est désactivé pour les sites de cette zone et Internet Explorer autorise les injections de script de site à site.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Recours à SSL3**  
  Ce paramètre de stratégie vous permet de bloquer tout recours non sécurisé à SSL 3.0. Lorsque cette stratégie est activée, Internet Explorer tente de se connecter aux sites à l’aide de SSL 3.0 ou version antérieure lorsque TLS 1.0 ou version supérieure échoue. Nous vous recommandons de ne pas autoriser le recours non sécurisé afin d’empêcher les attaques de l’intercepteur. Cette stratégie n’a pas d’impact sur l’activation des protocoles de sécurité. Si vous désactivez cette stratégie, les paramètres système par défaut seront utilisés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Par défaut** : aucun site  

- **Prise en charge du chiffrement Internet Explorer**  
  Ce paramètre de stratégie vous permet de désactiver la prise en charge de TLS (Transport Layer Security) 1,0, TLS 1,1, TLS 1,2, protocole SSL (SSL) 2,0 ou SSL 3,0 dans le navigateur. Les protocoles TLS et SSL permettent de protéger la communication entre le navigateur et le serveur cible. Lorsque le navigateur tente de configurer une communication protégée avec le serveur cible, le navigateur et le serveur négocient le protocole et la version à utiliser. Le navigateur et le serveur tentent de faire correspondre la liste des protocoles et versions pris en charge par l’autre, et ils sélectionnent la correspondance la plus préférée. Si vous activez ce paramètre de stratégie, le navigateur négocie ou ne négocie pas un tunnel de chiffrement à l’aide des méthodes de chiffrement que vous sélectionnez dans la liste déroulante. Si vous désactivez ou ne configurez pas ce paramètre de stratégie, l’utilisateur peut sélectionner la méthode de chiffrement prise en charge par le navigateur.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Valeur par défaut**: 2 éléments: TLS v 1.1 et TLS v 1.2  
  *Sélectionnez la flèche vers le bas pour afficher les options que vous pouvez sélectionner pour ce paramètre.*
  
- **Internet Explorer > Zone Internet verrouillée : SmartScreen**  
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone restreinte : Lancer les applications et les fichiers dans un iFrame**  
  Ce paramètre de stratégie permet d’indiquer si les applications peuvent s’exécuter et les fichiers être téléchargés depuis une référence IFRAME dans le code source HTML des pages de cette zone. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les applications et télécharger des fichiers depuis des IFRAME sans entrer de confirmation. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent exécuter des applications et télécharger des fichiers depuis des IFRAME des pages de cette zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter d’applications, ni télécharger des fichiers depuis les IFRAME des pages de cette zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter d’applications ni télécharger des fichiers depuis les IFRAME des pages de cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Par défaut**: désactiver 
  
- **Internet Explorer : ignorer les avertissements SmartScreen relatifs aux fichiers rares**  
  Ce paramètre de stratégie détermine si l’utilisateur peut ignorer les avertissements du filtre SmartScreen. Le filtre SmartScreen avertit l’utilisateur au sujet des fichiers exécutables que les utilisateurs d’Internet Explorer ne téléchargent généralement pas à partir d’Internet. Si vous activez ce paramètre de stratégie, les avertissements du filtre SmartScreen bloquent l’utilisateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut ignorer les avertissements du filtre SmartScreen.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : Bloqueur de fenêtres publicitaires**  
  Ce paramètre de stratégie permet d’indiquer si les fenêtres publicitaires s’affichent. Les fenêtres indépendantes qui sont ouvertes lorsque l’utilisateur final clique sur un lien ne sont pas bloquées. Si vous activez ce paramètre de stratégie, la plupart des fenêtres publicitaires sont bloquées. Si vous désactivez ce paramètre de stratégie, les fenêtres indépendantes ne sont pas bloquées. Si vous ne configurez pas ce paramètre de stratégie, la plupart des fenêtres indépendantes non désirées ne s’afficheront pas.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Par défaut** : activer  
  
- **Processus Internet Explorer > Gestion MIME cohérente**  
  Internet Explorer contient des comportements binaires dynamiques : les composants qui intègrent une fonctionnalité spécifique pour les éléments HTML auxquels ils sont attachés. Ce paramètre de stratégie indique si le paramètre Restriction de sécurité de comportement binaire est bloqué ou autorisé. Ce paramètre de stratégie permet aux administrateurs d’indiquer les applications pour lesquelles ils souhaitent bloquer ou activer cette fonctionnalité de sécurité. Si vous désactivez ce paramètre de stratégie, les comportements binaires sont autorisés dans les processus de l’Explorateur de fichiers et d’Internet Explorer. Si vous ne configurez pas ce paramètre de stratégie, les comportements binaires sont bloqués dans les processus de l’Explorateur de fichiers et d’Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer : autorisations Java des zones restreintes**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Par défaut**: désactiver Java  
    
  
- **Internet Explorer > Contrôles ActiveX en mode protégé**  
  Ce paramètre de stratégie empêche l’exécution des contrôles ActiveX en mode protégé lorsque le mode protégé amélioré est activé. Lorsqu’un utilisateur a un contrôle ActiveX installé qui n’est pas compatible avec le mode protégé amélioré et qu’un site web tente de charger le contrôle, Internet Explorer avertit l’utilisateur et lui donne la possibilité d’exécuter le site web en mode protégé normal. Ce paramètre de stratégie désactive cette notification et force l’exécution de tous les sites Web en mode protégé amélioré. Le mode protégé amélioré renforce la protection contre les sites Web malveillants en utilisant des processus 64 bits sur des versions 64 bits de Windows. Pour les ordinateurs qui exécutent Windows 8 ou version ultérieure, le mode protégé amélioré limite également les emplacements à partir desquels Internet Explorer peut lire dans le Registre et le système de fichiers. Lorsque le mode protégé amélioré est activé et qu’un utilisateur rencontre un site web qui tente de charger un contrôle ActiveX qui n’est pas compatible avec le mode protégé amélioré, Internet Explorer avertit l’utilisateur et lui donne la possibilité de désactiver le mode protégé amélioré pour ce site web spécifique. Si vous activez ce paramètre de stratégie, Internet Explorer ne donne pas à l’utilisateur la possibilité de désactiver le mode protégé amélioré. Tous les sites Web en mode protégé sont exécutés en mode protégé amélioré. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, Internet Explorer avertit les utilisateurs et offre la possibilité d’exécuter des sites web avec des contrôles ActiveX incompatibles en mode protégé normal.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Chargement des fichiers XAML**  
  Ce paramètre de stratégie vous permet de gérer le chargement des fichiers XAML (Extensible Application Markup Language). Le langage XAML est un langage de balisage déclaratif basé sur le langage XML et couramment utilisé pour la création d’interfaces utilisateur et de graphismes avancés qui tirent parti de Windows Presentation Foundation. Si vous activez ce paramètre de stratégie et si vous affectez la valeur Activer à la zone de liste déroulante, les fichiers XAML sont automatiquement chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous affectez la valeur Demander à la zone de liste déroulante, l’utilisateur est invité à confirmer le chargement des fichiers XAML. Si vous désactivez ce paramètre de stratégie, les fichiers XAML ne sont pas chargés dans Internet Explorer. L’utilisateur ne peut pas modifier ce comportement. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur est libre de charger ou non les fichiers XAML dans Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Par défaut**: désactiver  
  
- **Processus Internet Explorer : Restrictions de sécurité de scripts de fenêtres**  
  Internet Explorer permet aux scripts d’ouvrir, de redimensionner et de déplacer des fenêtres de divers types. La fonctionnalité de sécurité de Restrictions des fenêtres limite les fenêtres indépendantes et empêche les scripts d’ouvrir des fenêtres dont les barres de titre et d’état sont invisibles pour l’utilisateur ou cachent d’autres barres de titre et d’état Windows. Si vous activez ce paramètre de stratégie, les fenêtres avec scripts sont restreintes pour tous les processus. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les fenêtres scriptées ne sont pas restreintes.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Par défaut** : Activé   
  
- **Internet Explorer > Zone restreinte : Exécuter les contrôles ActiveX et les plug-ins**  
  Ce paramètre de stratégie permet d’indiquer si les contrôles ActiveX et les plug-ins peuvent s’exécuter dans les pages d’une zone spécifiée. Si vous activez ce paramètre de stratégie, les contrôles et les plug-ins peuvent s’exécuter de façon automatique. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution des contrôles ou des plug-ins. Si vous désactivez ce paramètre de stratégie, l’exécution des contrôles et des plug-ins est bloquée. Si vous ne configurez pas ce paramètre de stratégie, l’exécution des contrôles et des plug-ins est bloquée.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Contrôles ActiveX reconnus comme étant sécurisés pour les scripts**  
  Ce paramètre de stratégie permet d’indiquer si un contrôle ActiveX marqué comme sûr pour les scripts peut interagir avec un script. Si vous activez ce paramètre de stratégie, l’interaction avec les scripts peut se produire automatiquement, sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser les interactions avec les scripts. Si vous désactivez ce paramètre de stratégie, l’interaction avec les scripts est interdite. Si vous ne configurez pas ce paramètre de stratégie, l’interaction avec les scripts ne se produit pas.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Options d’ouverture de session**  
  Ce paramètre de stratégie permet de gérer les paramètres des options de connexion. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options de connexion suivantes. 
  - *Anonyme* : utilisez la connexion anonyme pour désactiver l’authentification HTTP et n’utilisez le compte invité que pour le protocole CIFS (Common Internet File System). 
  - *Invite* : utilisez l’invite pour interroger les utilisateurs sur leurs identifiants utilisateur et leurs mots de passe. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées de manière silencieuse pour le reste de la session. 
  - *Connexion automatique uniquement dans la zone Intranet* : utilisez cette option pour demander aux utilisateurs leur identifiant utilisateur et leur mot de passe pour accéder à d’autres zones. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées de manière silencieuse pour le reste de la session. 
  - *Connexion automatique avec le nom d’utilisateur et le mot de passe actuels*  : utilisez cette option pour tenter une connexion à l’aide de l’authentification Stimulation/réponse de Windows NT (également connue sous le nom Authentification NTLM). Si le protocole Stimulation/réponse de Windows NT est pris en charge par le serveur, la connexion utilise le nom d’utilisateur réseau de l’utilisateur et son mot de passe pour l’ouverture de session. Si le protocole Stimulation/réponse de Windows NT n’est pas pris en charge par le serveur, l’utilisateur doit entrer son nom et son mot de passe. 

  Si vous désactivez ce paramètre de stratégie, la connexion est définie comme *Automatique uniquement dans la zone intranet*. Si vous ne configurez pas ce paramètre de stratégie, la connexion est définie sur *Invite* pour le nom d’utilisateur et le mot de passe.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Par défaut** : anonyme  
  
- **Internet Explorer > Zone de confiance : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Vérifier la révocation du certificat serveur**  
  Ce paramètre de stratégie permet d’administrer la vérification par Internet Explorer de l’état de révocation des certificats de serveur. Les certificats sont révoqués lorsqu’ils sont compromis ou qu’ils ne sont plus valides. Cette option protège les utilisateurs de l’envoi de données confidentielles vers un site qui pourrait être frauduleux ou non sécurisé. Si vous activez ce paramètre de stratégie, Internet Explorer vérifie si les certificats de serveur ont été révoqués. Si vous désactivez ce paramètre de stratégie, Internet Explorer ne vérifie pas si les certificats de serveur ont été révoqués. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer ne vérifie pas si les certificats de serveur ont été révoqués.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone Internet : Sites de moindre privilège**  
  Ce paramètre de stratégie permet de spécifier si les sites web des zones moins privilégiées, tels que les sites sensibles, peuvent naviguer dans cette zone. Si vous activez ce paramètre de stratégie, les sites web des zones de moindre privilège peuvent ouvrir de nouvelles fenêtres dans cette zone ou y accéder. La zone de sécurité fonctionne sans la couche de sécurité supplémentaire qui est fournie par la fonctionnalité Protection contre l’élévation de zone. Si vous sélectionnez Demander dans la zone de liste déroulante, l’utilisateur est averti qu’un accès potentiellement risqué est sur le point de se produire. Si vous désactivez ce paramètre de stratégie, les accès potentiellement dangereux sont empêchés. La fonctionnalité de sécurité d’Internet Explorer est activée sur cette zone comme défini par le contrôle de la fonctionnalité Protection contre l’élévation de zone. Si vous ne configurez pas ce paramètre de stratégie, les sites web des zones moins privilégiées peuvent ouvrir de nouvelles fenêtres ou naviguer dans cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Téléchargements de fichiers**  
  Ce paramètre de stratégie permet d’indiquer si les téléchargements de fichiers sont autorisés depuis la zone. Cette option est définie par la zone de la page contenant le lien qui lance le téléchargement, et non pas la zone depuis laquelle le fichier est envoyé. Si vous activez ce paramètre de stratégie, les fichiers peuvent être téléchargés depuis la zone. Si vous désactivez ce paramètre de stratégie, les fichiers ne peuvent pas être téléchargés depuis la zone. Si vous ne configurez pas ce paramètre de stratégie, les fichiers ne peuvent pas être téléchargés depuis la zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Exécuter les composants dépendant du .NET Framework signés avec Authenticode**  
  Ce paramètre de stratégie vous permet d’indiquer si les composants .NET Framework qui sont signés avec Authenticode peuvent s’exécuter dans Internet Explorer. Ces composants incluent les contrôles managés référencés par une balise objet et les exécutables managés référencés à partir d’un lien. Si vous activez ce paramètre de stratégie, Internet Explorer exécute les composants managés signés. Si vous sélectionnez Demander dans la liste déroulante, Internet Explorer demande aux utilisateurs s’ils souhaitent exécuter les composants managés signés. Si vous désactivez ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Empêcher l’installation par utilisateur des contrôles ActiveX**  
  Ce paramètre de stratégie vous permet d’empêcher l’installation de contrôles ActiveX en fonction de chaque utilisateur. Si vous activez ce paramètre de stratégie, les contrôles ActiveX ne peuvent pas être installés pour chaque utilisateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les contrôles ActiveX peuvent être installés pour chaque utilisateur.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Empêcher la gestion du filtre SmartScreen**  
  Ce paramètre de stratégie empêche l’utilisateur de gérer le filtre SmartScreen, qui avertit l’utilisateur lorsque le site web visité est connu pour des tentatives frauduleuses de collecte d’informations personnelles par « hameçonnage », ou qu’il est connu pour héberger des programmes malveillants. Si vous activez ce paramètre de stratégie, l’utilisateur n’est pas invité à activer le filtre SmartScreen. Toutes les URL qui ne figurent pas dans la liste des URL autorisées par les filtres sont automatiquement envoyées à Microsoft, sans que l’utilisateur en soit informé. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur est invité à choisir s’il veut activer le filtre SmartScreen lors de l’expérience de première exécution.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Par défaut** : activer  
  
- **Processus Internet Explorer > Fonctionnalité de sécurité de détection MIME**  
  Ce paramètre de stratégie indique si la détection MIME dans Internet Explorer doit empêcher la promotion d’un fichier ou d’un type de fichier vers un type plus dangereux. Si vous activez ce paramètre de stratégie, la fonctionnalité de sécurité de détection MIME n’autorisera jamais la promotion d’un fichier vers un type de fichier plus dangereux. Si vous désactivez ce paramètre de stratégie, les processus Internet Explorer autoriseront la détection MIME à promouvoir un fichier vers un type de fichier plus dangereux. Si vous ne configurez pas ce paramètre de stratégie, la détection MIME n’autorise jamais la promotion d’un type de fichier vers un type de fichier plus dangereux.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Télécharger les contrôles ActiveX signés**  
  Ce paramètre de stratégie vous permet d’indiquer si les utilisateurs peuvent télécharger les contrôles ActiveX signés depuis une page de la zone. Si vous activez cette stratégie, les utilisateurs peuvent télécharger les contrôles signés de façon automatique. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation. Si vous désactivez ce paramètre de stratégie, les contrôles signés ne peuvent pas être téléchargés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Saisie semi-automatique**  
  Cette fonctionnalité de saisie semi-automatique peut se souvenir des noms d’utilisateurs et des mots de passe entrés dans des formulaires et les suggérer. Si vous activez ce paramètre, l’utilisateur ne peut pas modifier les options « Noms d’utilisateur et mots de passe sur les formulaires » ou « Demander l’enregistrement des mots de passe ». La fonctionnalité de saisie semi-automatique est activée pour l’option « Noms d’utilisateur et mots de passe sur les formulaires ». Vous devez décider de sélectionner ou non l’option « Demander l’enregistrement des mots de passe ». Si vous désactivez ce paramètre, l’utilisateur ne peut pas modifier les options « Noms d’utilisateur et mots de passe sur les formulaires » ou « Demander l’enregistrement des mots de passe ». La fonctionnalité de saisie semi-automatique est désactivée pour « Noms d’utilisateur et mots de passe sur les formulaires ». En outre, l’utilisateur ne peut pas choisir de demander l’enregistrement des mots de passe. Si vous ne configurez pas ce paramètre, l’utilisateur est libre d’activer la saisie semi-automatique pour l’option « Noms d’utilisateur et mots de passe sur les formulaires» et de choisir de demander l’enregistrement des mots de passe. Pour afficher cette option, les utilisateurs ouvrent la boîte de dialogue Options Internet, cliquent sur l’onglet Contenu, puis sur le bouton Paramètres.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : Autoriser l’exécution de VBscript**  
  Ce paramètre de stratégie vous permet de décider si VBScript peut être exécuté sur les pages de certaines zones Internet Explorer. Les options sont les suivantes : 
  - *Activé* : VBScript s’exécute sur les pages de certaines zones, sans intervention de l’utilisateur. 
  - *Invite* : les employés sont invités à choisir s’il faut autoriser l’exécution de VBScript dans la zone. 
  - *Désactivé* : l’exécution de VBScript est empêchée dans la zone. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, VBScript s’exécute dans la zone spécifiée, sans que l’utilisateur n’ait à intervenir.    

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Autoriser uniquement les domaines approuvés à utiliser le contrôle Active X TDC**  
  Ce paramètre de stratégie contrôle si l’utilisateur est ou non autorisé à exécuter le contrôle ActiveX TDC sur des sites web. Si vous activez ce paramètre de stratégie, le contrôle ActiveX TDC n’est pas exécuté sur les sites web de cette zone. Si vous désactivez ce paramètre de stratégie, le contrôle ActiveX TDC s’exécute sur tous les sites de cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Par défaut** : Activé  
  
- **La zone de confiance Internet Explorer n’exécute pas de logiciels anti-programme malveillant sur les contrôles ActiveX**  
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer utilise toujours votre logiciel anti-programme malveillant pour vérifier si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Ordinateur local : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Sécurité moyenne ».  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Par défaut**: désactiver Java 
  
- **Internet Explorer > Zone Intranet : Ne pas exécuter de logiciels anti-programme malveillant sur les contrôles ActiveX**  
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Par défaut** : Désactivé  

- **Internet Explorer > Zone restreinte : Scriptlets**  
  Ce paramètre de stratégie vous permet de déterminer si l’utilisateur peut exécuter des scriptlets. Si vous activez ce paramètre de stratégie, l’utilisateur peut exécuter des scriptlets. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne peut pas exécuter de scriptlets. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver les scriptlets.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Par défaut** : Désactivé  
  
- **Processus Internet Explorer > Barre de notification**  
  Ce paramètre de stratégie vous permet d’indiquer si la Barre de notification est affichée pour les processus Internet Explorer lorsque des installations de fichiers ou de code sont restreintes. Par défaut, la Barre de notification est affichée pour les processus Internet Explorer. Si vous activez ce paramètre de stratégie, la barre de notification s’affiche pour les processus Internet Explorer. Si vous désactivez ce paramètre de stratégie, la barre de notification ne s’affiche pas pour les processus Internet Explorer. Si vous ne configurez pas ce paramètre de stratégie, la barre de notification ne s’affiche pas pour les processus Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone Internet : Télécharger les contrôles ActiveX signés**  
  Ce paramètre de stratégie vous permet d’indiquer si les utilisateurs peuvent télécharger les contrôles ActiveX signés depuis une page de la zone. Si vous activez cette stratégie, les utilisateurs peuvent télécharger les contrôles signés de façon automatique. Si vous sélectionnez Demander dans la liste déroulante, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation. Si vous désactivez ce paramètre de stratégie, les contrôles signés ne peuvent pas être téléchargés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent confirmer qu’ils souhaitent télécharger les contrôles signés par des éditeurs autres que des éditeurs de confiance. Le code signé par des éditeurs de confiance est téléchargé sans confirmation.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : SmartScreen**  
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Supprimer le bouton Exécuter une fois pour les contrôles ActiveX obsolètes**  
  Ce paramètre de stratégie vous permet d’empêcher les utilisateurs de voir le bouton « Exécuter une fois » et d’exécuter des contrôles ActiveX obsolètes spécifiques dans Internet Explorer. Si vous activez ce paramètre de stratégie, les utilisateurs ne voient pas le bouton « Exécuter une fois » sur le message d’avertissement qui s’affiche quand Internet Explorer bloque un contrôle ActiveX obsolète. Si vous désactivez ou ne configurez pas ce paramètre de stratégie, les utilisateurs voient le bouton « Exécuter une fois » sur le message d’avertissement qui s’affiche quand Internet Explorer bloque un contrôle ActiveX obsolète. Si l’utilisateur clique sur ce bouton, le contrôle ActiveX obsolète est exécuté une seule fois. Pour plus d’informations, consultez « Contrôles ActiveX obsolètes » dans la bibliothèque TechNet Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Par défaut** : Activé 
  
- **Internet Explorer > Zone Internet : Lancer les applications et les fichiers dans un iframe**  
  Ce paramètre de stratégie permet d’indiquer si les applications peuvent s’exécuter et les fichiers être téléchargés depuis une référence IFRAME dans le code source HTML des pages de cette zone. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les applications et télécharger des fichiers depuis des IFRAME sans entrer de confirmation. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent exécuter des applications et télécharger des fichiers depuis des IFRAME des pages de cette zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter d’applications, ni télécharger des fichiers depuis les IFRAME des pages de cette zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent indiquer s’ils souhaitent exécuter des applications et télécharger des fichiers depuis des IFRAME sur les pages de cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Zone restreinte : Naviguer dans des fenêtres et des cadres sur différents domaines**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : SmartScreen**  
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone de confiance verrouillée : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Par défaut**: désactiver Java 
  
- **Internet Explorer > Vérifier les signatures des programmes téléchargés**  
  Ce paramètre de stratégie vous permet de décider si Internet Explorer recherche des signatures numériques (pour identifier l’éditeur du logiciel signé et vérifier qu’il n’a pas été modifié ni falsifié) sur les ordinateurs des utilisateurs avant de télécharger des programmes exécutables. Si vous activez ce paramètre de stratégie, Internet Explorer vérifie les signatures numériques des programmes exécutables et affiche leur identité avant de les télécharger sur les ordinateurs des utilisateurs. Si vous désactivez ce paramètre de stratégie, Internet Explorer ne vérifie pas les signatures numériques des programmes exécutables ou n’affiche pas leurs identités avant de les télécharger sur les ordinateurs des utilisateurs. Si vous ne configurez pas cette stratégie, Internet Explorer ne vérifie pas les signatures numériques des programmes exécutables ou n’affiche pas leurs identités avant de les télécharger sur les ordinateurs des utilisateurs.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Écriture de scripts pour les contrôles de navigateur web**  
  Ce paramètre de stratégie détermine si une page peut gérer les contrôles incorporés WebBrowser par script. Si vous activez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser est autorisé. Si vous désactivez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser n’est pas autorisé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver l’accès du script au contrôle WebBrowser. Par défaut, l’accès du script au contrôle WebBrowser est autorisé uniquement dans les zones Ordinateur local et Intranet.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Filtre anti-script de site à site**  
  Cette stratégie détermine si le filtre anti-script de site à site (XSS) détecte et évite les injections de script de site à site dans les sites web de cette zone. Si vous activez ce paramètre de stratégie, le filtre XSS est activé pour les sites de cette zone et tente de bloquer les injections de script de site à site. Si vous désactivez ce paramètre de stratégie, le filtre XSS est désactivé pour les sites de cette zone et Internet Explorer autorise les injections de script de site à site.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Comportements binaires et des scripts**  
  Ce paramètre de stratégie vous permet de gérer les comportements binaires et des scripts dynamiques : des composants qui encapsulent des fonctionnalités spécifiques pour les éléments HTML auxquels ils sont attachés. Si vous activez ce paramètre de stratégie, les comportements binaires et des scripts sont disponibles. Si vous sélectionnez Approuvé par l’administrateur dans la zone de liste déroulante, seuls les comportements listés dans les comportements approuvés par l’administrateur sous la stratégie Restriction de sécurité des comportements binaires sont disponibles. Si vous désactivez ce paramètre de stratégie, les comportements binaires et des scripts ne sont pas disponibles, sauf si les applications ont implémenté un gestionnaire de sécurité personnalisé. Si vous ne configurez pas ce paramètre de stratégie, les comportements binaires et des scripts ne sont pas disponibles, sauf si les applications ont implémenté un gestionnaire de sécurité personnalisé.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Vérification des paramètres de sécurité**  
  Ce paramètre de stratégie désactive la fonction de vérification des paramètres de sécurité, qui vérifie les paramètres de sécurité Internet Explorer pour déterminer quand les paramètres exposent Internet Explorer à des risques. Si vous activez ce paramètre de stratégie, la fonction est désactivée. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la fonctionnalité est activée.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone Internet : Avertissement de sécurité pour les fichiers potentiellement dangereux**  
  Ce paramètre de stratégie détermine si le message « Fichier ouvert : Avertissement de sécurité » s’affiche lorsque l’utilisateur essaie d’ouvrir des fichiers exécutables ou d’autres fichiers potentiellement non sécurisés (à partir d’un partage de fichiers intranet via l’Explorateur de fichiers, par exemple). Si vous activez ce paramètre de stratégie et affectez la valeur Activer à la zone de liste déroulante, les fichiers concernés s’ouvrent sans avertissement de sécurité préalable. Si vous affectez la valeur Demander à la zone de liste déroulante, un avertissement de sécurité s’affiche avant l’ouverture des fichiers. Si vous désactivez ce paramètre de stratégie, les fichiers concernés ne s’ouvrent pas. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut configurer la façon dont l’ordinateur gère ces fichiers. Par défaut, ces fichiers sont bloqués dans la zone restreinte, activés dans les zones Intranet et Ordinateur local, et définis sur Demander dans les zones Internet et de confiance.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Par défaut** : invite  
  
- **Internet Explorer > Zone Intranet : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Sécurité moyenne ».  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Par défaut** : haute sécurité 
  
- **Internet Explorer bloque les contrôles ActiveX obsolètes**   
  Ce paramètre de stratégie détermine si Internet Explorer bloque des contrôles ActiveX obsolètes spécifiques. Les contrôles ActiveX obsolètes ne sont jamais bloqués dans la zone Intranet. Si vous activez ce paramètre de stratégie, Internet Explorer cesse de bloquer les contrôles ActiveX obsolètes. Si vous désactivez ou ne configurez pas ce paramètre de stratégie, Internet Explorer continue de bloquer des contrôles ActiveX obsolètes spécifiques. Pour plus d’informations, consultez « Contrôles ActiveX obsolètes » dans la bibliothèque TechNet Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Bloqueur de fenêtres publicitaires**  
  Ce paramètre de stratégie permet d’indiquer si les fenêtres publicitaires s’affichent. Les fenêtres indépendantes qui sont ouvertes lorsque l’utilisateur final clique sur un lien ne sont pas bloquées. Si vous activez ce paramètre de stratégie, la plupart des fenêtres publicitaires sont bloquées. Si vous désactivez ce paramètre de stratégie, les fenêtres indépendantes ne sont pas bloquées. Si vous ne configurez pas ce paramètre de stratégie, la plupart des fenêtres indépendantes non désirées ne s’afficheront pas.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Par défaut** : activer  
  
- **Processus Internet Explorer > Restriction de sécurité du protocole MK**  
  Le paramètre de stratégie Restriction de sécurité du protocole MK réduit l’exposition aux attaques en empêchant l’utilisation du protocole MK. Cela se traduit par l’échec des ressources hébergées sur le protocole MK. Si vous activez ce paramètre de stratégie, l’utilisation du protocole MK est interdite dans l’Explorateur de fichiers et Internet Explorer, ce qui se traduit par l’échec des ressources hébergées sur le protocole MK. Si vous désactivez ce paramètre de stratégie, les applications peuvent utiliser l’API du protocole MK. Les ressources hébergées sur le protocole MK fonctionnent pour les processus de l’Explorateur de fichiers et d’Internet Explorer. Si vous ne configurez pas ce paramètre de stratégie, l’utilisation du protocole MK est interdite dans l’Explorateur de fichiers et Internet Explorer, ce qui se traduit par l’échec des ressources hébergées sur le protocole MK.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Par défaut** : Activé  
  
- **Autorisations Java de la zone approuvée Internet Explorer**   
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Basse sécurité ».  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Par défaut** : haute sécurité  
  
- **Internet Explorer > Zone restreinte : Écriture de scripts pour les applets Java**  
  Ce paramètre de stratégie vous permet de décider si les applets sont exposées aux scripts dans la zone. Si vous activez ce paramètre de stratégie, les scripts peuvent accéder aux applets automatiquement, sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser les scripts à accéder aux applets. Si vous désactivez ce paramètre de stratégie, les scripts ne peuvent pas accéder aux applets. Si vous ne configurez pas ce paramètre de stratégie, les scripts ne peuvent pas accéder aux applets.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Par défaut**: désactiver  
  
- **Autorisations Java de la zone Sites sensibles verrouillée Internet Explorer**   
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Par défaut**: désactiver Java 
  
- **La zone internet Internet Explorer autorise uniquement les domaines approuvés pour utiliser les contrôles ActiveX**   
  Ce paramètre de stratégie détermine si l’utilisateur est invité ou non à autoriser l’exécution des contrôles ActiveX sur des sites web autres que le site web qui a installé le contrôle ActiveX. Si vous activez ce paramètre de stratégie, l’utilisateur est invité à confirmer l’exécution des contrôles ActiveX à partir des sites web de cette zone. L’utilisateur peut choisir d’autoriser l’exécution du contrôle à partir du site actuel ou à partir de tous les sites. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne voit pas l’invite ActiveX propre au site, et les contrôles ActiveX peuvent s’exécuter à partir de tous les sites de cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Inclure tous les chemins réseau**  
  Internet Explorer inclure tous les chemins réseau.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Internet : Mode protégé**  
  Ce paramètre de stratégie vous permet d’activer le mode protégé. Le mode protégé favorise la protection d’Internet Explorer face à des vulnérabilités exploitées en réduisant les emplacements où Internet Explorer peut écrire dans le Registre et le système de fichiers. Si vous activez ce paramètre de stratégie, le mode protégé est activé. L’utilisateur ne peut pas désactiver le mode protégé. Si vous désactivez ce paramètre de stratégie, le mode protégé est désactivé. L’utilisateur ne peut pas activer le mode protégé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver le mode protégé.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Par défaut** : activer 
  
- **Internet Explorer > Zone Internet : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Par défaut**: désactiver 
  
- **Internet Explorer verrouille la zone restreinte verrouillée SmartScreen**   
  Ce paramètre de stratégie détermine si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous activez ce paramètre de stratégie, le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Si vous désactivez ce paramètre de stratégie, le filtre SmartScreen n’analyse pas les pages de cette zone à la recherche d’un contenu malveillant. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si le filtre SmartScreen analyse les pages de cette zone à la recherche d’un contenu malveillant. Remarque : Dans Internet Explorer 7, ce paramètre de stratégie détermine si le filtre antihameçonnage analyse les pages de cette zone à la recherche d’un contenu malveillant.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Détection des plantages**  
  Ce paramètre de stratégie vous permet de gérer la fonctionnalité de détection des plantages de la gestion des modules complémentaires. Si vous activez ce paramètre de stratégie, un plantage dans Internet Explorer aura le même comportement que pour Windows XP Professionnel Service Pack 1 et antérieur, à savoir l’affichage de la boîte de dialogue de rapport d’erreurs Windows. Tous les paramètres de stratégie du rapport d’erreurs Windows continuent à s’appliquer. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, la fonctionnalité de détection des incidents pour la gestion des modules complémentaires est fonctionnelle.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : Autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, l’autorisation est définie sur « Haute sécurité ».  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Par défaut**: désactiver Java  
  
- **Internet Explorer > Zone restreinte : Active Scripting**  
  Ce paramètre de stratégie vous permet de gérer si le code de script dans les pages de la zone est exécuté. Si vous activez ce paramètre de stratégie, le code de script dans les pages de la zone peut s’exécuter automatiquement. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du code de script dans les pages de la zone. Si vous désactivez ce paramètre de stratégie, le code de script dans les pages de la zone ne peut pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, le code de script dans les pages de la zone ne peut pas s’exécuter.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Options d’ouverture de session**  
  Ce paramètre de stratégie permet de gérer les paramètres des options de connexion. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options de connexion suivantes. Ouverture de session anonyme, pour désactiver l’authentification HTTP et n’utiliser le compte Invité que pour le protocole CIFS (Common Internet File System). Demander aux utilisateurs leur nom d’utilisateur et leur mot de passe. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées pour le reste de la session. Ouverture de session automatique uniquement dans la zone Intranet, pour demander aux utilisateurs leur nom et leur mot de passe pour accéder aux autres zones. Après qu’un utilisateur a été interrogé, ces valeurs peuvent être utilisées de manière silencieuse pour le reste de la session. Connexion automatique avec le nom d’utilisateur et le mot de passe actuels, pour tenter l’ouverture de session avec le protocole Stimulation/réponse de Windows NT (également connu sous le nom d’Authentification NTLM). Si l’authentification Stimulation/réponse de Windows NT est pris en charge par le serveur, la connexion utilise le nom d’utilisateur réseau de l’utilisateur et son mot de passe pour l’ouverture de session. Si le protocole Stimulation/réponse de Windows NT n’est pas pris en charge par le serveur, l’utilisateur doit entrer son nom et son mot de passe. Si vous désactivez ce paramètre de stratégie, l’ouverture de session est définie comme automatique uniquement dans la zone intranet. Si vous ne configurez pas ce paramètre de stratégie, la connexion est définie sur Connexion automatique uniquement dans la zone intranet.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Par défaut** : invite  
  
- **La zone restreinte Internet Explorer autorise l’exécution de vbscript**   
  Ce paramètre de stratégie permet d’indiquer si VBScript peut s’exécuter dans les pages d’une zone spécifiée dans Internet Explorer. Si vous sélectionnez Activer dans la zone de liste déroulante, VBScript peut s’exécuter sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution de VBScript. Si vous sélectionnez Désactiver dans la zone de liste déroulante, VBScript ne peut pas s’exécuter. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, VBScript ne peut pas s’exécuter.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Faire glisser du contenu provenant de domaines différents entre des fenêtres**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Par défaut** : Désactivé 
  
- **Internet Explorer > Zone Intranet : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Par défaut**: désactiver 
  
- **Internet Explorer > Télécharger des fichiers joints**  
  Ce paramètre de stratégie empêche l’utilisateur de télécharger des fichiers joints (pièces jointes) à partir d’un flux sur l’ordinateur de l’utilisateur. Si vous activez ce paramètre de stratégie, l’utilisateur ne peut pas définir le moteur de synchronisation de flux pour qu’il télécharge un fichier joint via la page des propriétés de flux. Un développeur ne peut pas modifier le paramètre de téléchargement via les interfaces de programmation d’applications de flux. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut définir le moteur de synchronisation de flux pour qu’il télécharge un fichier joint via la page des propriétés de flux. Un développeur peut modifier le paramètre de téléchargement via les API de flux.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Télécharger les contrôles ActiveX non signés**  
  Ce paramètre de stratégie permet d’indiquer si les utilisateurs peuvent télécharger des contrôles ActiveX non signés à partir de la zone. Ce code est potentiellement dangereux, surtout s’il provient d’une zone non approuvée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les contrôles non signés sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du contrôle non signé. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Faire glisser du contenu provenant de domaines différents dans les fenêtres**  
  Ce paramètre de stratégie permet d’indiquer si les utilisateurs peuvent télécharger des contrôles ActiveX non signés à partir de la zone. Ce code est potentiellement dangereux, surtout s’il provient d’une zone non approuvée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les contrôles non signés sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du contrôle non signé. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Par défaut** : Désactivé  
  
- **Processus Internet Explorer restreint l’installation ActiveX**   
  Ce paramètre de stratégie permet aux applications qui hébergent le contrôle de navigateur web de bloquer la demande automatique d’installation de contrôles ActiveX. Si vous activez ce paramètre de stratégie, le contrôle de navigateur web bloque la demande automatique d’installation de contrôles ActiveX pour tous les processus. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le contrôle de navigateur web ne bloque pas la demande automatique d’installation de contrôle ActiveX pour tous les processus.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Par défaut** : Activé  
  
- **Scriptlets de la zone Internet Internet Explorer**  
  Ce paramètre de stratégie vous permet de déterminer si l’utilisateur peut exécuter des scriptlets. Si vous activez ce paramètre de stratégie, l’utilisateur peut exécuter des scriptlets. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne peut pas exécuter de scriptlets. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver les scriptlets.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Glisser-déplacer ou copier et coller des fichiers**  
  Ce paramètre de stratégie vous permet de spécifier si les utilisateurs peuvent faire glisser ou copier et coller des fichiers à partir d’une source dans la zone. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent faire glisser ou copier et coller des fichiers à partir de cette zone automatiquement. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent faire glisser ou copier des fichiers à partir de cette zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas faire glisser ni copier et coller des fichiers à partir de cette zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs doivent indiquer s’ils souhaitent faire glisser ou copier des fichiers à partir de cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Par défaut**: désactiver  
  
- **Logiciels Internet Explorer quand la signature n’est pas valide**  
  Ce paramètre de stratégie vous permet de spécifier si des logiciels, tels que les contrôles ActiveX et les téléchargements de fichiers, peuvent être installés ou exécutés par l’utilisateur, même si la signature n’est pas valide. Une signature non valide peut indiquer que quelqu’un a falsifié le fichier. Si vous activez ce paramètre de stratégie, les utilisateurs sont invités à installer ou exécuter des fichiers avec une signature non valide. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter ou installer des fichiers avec une signature non valide. Si vous ne configurez pas cette stratégie, les utilisateurs peuvent choisir d’exécuter ou d’installer des fichiers avec une signature non valide.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Copier et coller par le biais d’un script**  
  Ce paramètre de stratégie vous permet d’indiquer si les scripts peuvent utiliser le Presse-papiers (pour couper, copier, coller, etc.) dans une région spécifiée. Si vous activez ce paramètre de stratégie, un script peut effectuer une opération sur le Presse-papiers. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent effectuer des opérations sur le Presse-papiers. Si vous désactivez ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers. Si vous ne configurez pas ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : Faire glisser du contenu provenant de domaines différents entre des fenêtres**  
  Ce paramètre de stratégie vous permet de définir des options pour faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Si vous activez ce paramètre de stratégie et cliquez sur Activer, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Si vous activez ce paramètre de stratégie et cliquez sur Désactiver, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre. Dans Internet Explorer 10, si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les utilisateurs ne peuvent pas faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs peuvent modifier ce paramètre dans la boîte de dialogue Options Internet. Dans Internet Explorer 9 et versions antérieures, si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent faire glisser un contenu d’un domaine vers un autre lorsque la source et la destination se trouvent dans des fenêtres différentes. Les utilisateurs ne peuvent pas modifier ce paramètre.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Par défaut** : Désactivé  
  
- **Internet Explorer : utilisateurs ajoutant des sites**  
  Empêche les utilisateurs d’ajouter ou de supprimer des sites dans des zones de sécurité. Une zone de sécurité est un groupe de sites web partageant le même niveau de sécurité. Si vous activez cette stratégie, les paramètres de gestion de sites pour les zones de sécurité seront désactivés. (Pour voir les paramètres de gestion de sites pour les zones de sécurité, dans la boîte de dialogue Options Internet, cliquez sur l’onglet Sécurité, puis sur le bouton Sites.) Si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent non seulement ajouter ou supprimer des sites web dans les zones de Sites de confiance et de Sites sensibles, mais aussi modifier les paramètres de la zone intranet locale. Cette stratégie empêche les utilisateurs de changer les paramètres de gestion de sites pour les zones de sécurité définies par l’administrateur. Remarque : La stratégie « Désactiver la page Sécurité » (située dans \Configuration utilisateur\Modèles d’administration\Composants Windows\Internet Explorer\Panneau de configuration Internet), qui élimine l’onglet Sécurité de l’interface, est prioritaire sur cette stratégie. Si elle est activée, cette stratégie est ignorée. Consultez également la stratégie « Zones de sécurité : utiliser uniquement des paramètres machine ».  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : fenêtres initiées par des scripts**  
  Ce paramètre de stratégie permet de gérer les restrictions sur les fenêtres indépendantes lancées par des scripts, et sur celles qui incluent les barres de titre et d’état. Si vous activez ce paramètre de stratégie, la fonctionnalité de sécurité des Restrictions des fenêtres ne s’applique pas à cette zone. La zone de sécurité s’exécute sans la couche de sécurité supplémentaire fournie par cette fonctionnalité. Si vous désactivez ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts. Si vous ne configurez pas ce paramètre de stratégie, les actions potentiellement malveillantes contenues dans les fenêtres indépendantes lancées par des scripts et dans les fenêtres qui incluent des barres de titre et d’état, ne peuvent pas s’exécuter. Cette fonctionnalité de sécurité d’Internet Explorer est activée dans cette zone, comme indiqué par le paramètre de contrôle des fonctionnalités de Restrictions de sécurité des fenêtres lancées par des scripts.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zones de sécurité : utiliser uniquement des paramètres machine**  
  Applique l’information sur les zones de sécurité à tous les utilisateurs du même ordinateur. Une zone de sécurité est un groupe de sites web partageant le même niveau de sécurité. Si vous activez ce paramètre de stratégie, les changements apportés par l’utilisateur à une zone de sécurité s’appliquent à tous les utilisateurs de cet ordinateur. Si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs du même ordinateur peuvent définir leurs propres paramètres de zone de sécurité. Utilisez cette stratégie pour garantir que les paramètres de zone de sécurité s’appliquent uniformément au même ordinateur et ne varient pas d’un utilisateur à l’autre. En outre, consultez la stratégie « Zones de sécurité : ne pas autoriser les utilisateurs à modifier les stratégies ».  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone Ordinateur local verrouillé : autorisations Java**  
  Ce paramètre de stratégie permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Par défaut**: désactiver Java 
  
- **La zone restreinte Internet Explorer n’exécute pas de logiciel anti-programme malveillant sur les contrôles ActiveX**   
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer utilise toujours votre logiciel anti-programme malveillant pour vérifier si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Exécuter les composants dépendant du .NET Framework signés avec Authenticode**  
  Ce paramètre de stratégie vous permet d’indiquer si les composants .NET Framework qui sont signés avec Authenticode peuvent s’exécuter dans Internet Explorer. Ces composants incluent les contrôles managés référencés par une balise objet et les exécutables managés référencés à partir d’un lien. Si vous activez ce paramètre de stratégie, Internet Explorer exécute les composants managés signés. Si vous sélectionnez Demander dans la liste déroulante, Internet Explorer demande aux utilisateurs s’ils souhaitent exécuter les composants managés signés. Si vous désactivez ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer n’exécute pas les composants managés signés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone restreinte : accès aux sources de données**  
  Ce paramètre de stratégie vous permet d’indiquer si Internet Explorer peut accéder aux données provenant d’une autre zone de sécurité en utilisant le moteur d’analyse XML de Microsoft (MSXML) ou les objets ADO (ActiveX Data Objects). Si vous activez ce paramètre de stratégie, les utilisateurs peuvent charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement d’une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas charger une page dans la zone qui utilise MSXML ou ADO pour accéder aux données provenant d’un autre site de la zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Par défaut**: désactiver 
  
- **La zone internet Internet Explorer n’exécute pas de logiciels anti-programme malveillant sur les contrôles ActiveX**  
  Ce paramètre de stratégie détermine si Internet Explorer exécute des logiciels anti-programme malveillant sur les contrôles ActiveX pour déterminer s’ils peuvent être chargés sur des pages de façon sécurisée. Si vous activez ce paramètre de stratégie, Internet Explorer ne consulte pas votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous désactivez ce paramètre de stratégie, Internet Explorer consulte toujours votre logiciel anti-programme malveillant pour déterminer si une instance du contrôle ActiveX peut être créée de façon sécurisée. Si vous ne configurez pas ce paramètre de stratégie, Internet Explorer utilise toujours votre logiciel anti-programme malveillant pour vérifier si une instance du contrôle ActiveX peut être créée de façon sécurisée. Les utilisateurs peuvent activer ou désactiver ce comportement au moyen des paramètres Sécurité d’Internet Explorer.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : copier et coller par le biais d’un script**  
  Ce paramètre de stratégie vous permet d’indiquer si les scripts peuvent utiliser le Presse-papiers (pour couper, copier, coller, etc.) dans une région spécifiée. Si vous activez ce paramètre de stratégie, un script peut effectuer une opération sur le Presse-papiers. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent effectuer des opérations sur le Presse-papiers. Si vous désactivez ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers. Si vous ne configurez pas ce paramètre de stratégie, un script ne peut pas effectuer d’opérations de Presse-papiers.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer : utiliser le service de d’installation ActiveX**  
  Ce paramètre de stratégie vous permet de spécifier la façon dont les contrôles ActiveX sont installés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont installés uniquement si le service de l’installateur ActiveX est présent et s’il a été configuré pour permettre l’installation de contrôles ActiveX. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les contrôles ActiveX, notamment les contrôles par utilisateur, sont installés par le biais du processus d’installation standard.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Par défaut** : Activé  
  
- **Processus Internet Explorer : protection contre l’élévation de zone**  
  Internet Explorer place des restrictions sur toutes les pages web qu’il ouvre. Les restrictions dépendent de l’emplacement de la page web (Internet, intranet, zone Ordinateur local, etc.). Par exemple, les pages web sur l’ordinateur local ont le moins de restrictions de sécurité et sont situées dans la zone Ordinateur local, faisant de cette zone une cible idéale pour les utilisateurs malveillants. Si vous activez ce paramètre de stratégie, toute zone peut être protégée contre l’élévation de zone pour tous les processus. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les processus autres qu’Internet Explorer ou ceux figurant dans la liste des processus ne reçoivent pas cette protection.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Par défaut** : Activé  
  
- **La zone internet Internet Explorer télécharge des contrôles ActiveX non signés**   
  Ce paramètre de stratégie permet d’indiquer si les utilisateurs peuvent télécharger des contrôles ActiveX non signés à partir de la zone. Ce code est potentiellement dangereux, surtout s’il provient d’une zone non approuvée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent exécuter les contrôles non signés sans intervention de l’utilisateur. Si vous sélectionnez Demander dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser l’exécution du contrôle non signé. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas exécuter de contrôles non signés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Par défaut**: désactiver  
  
- **La zone internet Internet Explorer navigue dans des fenêtres et des cadres sur différents domaines**   
  Ce paramètre de stratégie vous permet de gérer l’ouverture de fenêtres et de cadres, ainsi que l’accès des applications sur différents domaines. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent ouvrir des fenêtres et des cadres à partir d’autres domaines et accéder aux applications à partir d’autres domaines. Si vous sélectionnez Demander dans la zone de liste déroulante, il est demandé aux utilisateurs s’il faut autoriser les fenêtres et les cadres à accéder aux applications à partir d’autres domaines. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas ouvrir de fenêtres et de cadres pour accéder aux applications à partir d’autres domaines. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs peuvent ouvrir des fenêtres et des cadres à partir d’autres domaines et accéder aux applications à partir d’autres domaines.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer > Zone Internet : Mises à jour de la barre d’état via un script**  
  Ce paramètre de stratégie vous permet de spécifier si un script est autorisé à mettre à jour la barre d’état dans la zone. Si vous activez ce paramètre de stratégie, les scripts peuvent mettre à jour la barre d’état. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le script n’est pas autorisé à mettre à jour la barre d’état.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Inclure le chemin local lors du chargement des fichiers sur un serveur**  
  Ce paramètre de stratégie spécifie si les informations du chemin d’accès local sont envoyées ou non lorsque l’utilisateur charge un fichier via un formulaire HTML. Si les informations de chemin local sont envoyées, certaines informations peuvent être involontairement révélées au serveur. Par exemple, des fichiers envoyés à partir du Bureau de l’utilisateur peuvent avoir un chemin contenant le nom de l’utilisateur. Si vous activez ce paramètre de stratégie, les informations de chemin sont envoyées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous désactivez ce paramètre de stratégie, les informations de chemin sont supprimées lorsque l’utilisateur charge un fichier via un formulaire HTML. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut choisir si les informations du chemin d’accès sont envoyées lorsqu’il charge un fichier via un formulaire HTML. Par défaut, les informations de chemin sont envoyées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Par défaut** : Désactivé  
  
- **Les processus Internet Explorer restreignent le téléchargement de fichiers**   
  Ce paramètre de stratégie permet aux applications qui hébergent le contrôle de navigateur web de bloquer la demande automatique de confirmation des téléchargements de fichiers non lancés par l’utilisateur. Si vous activez ce paramètre de stratégie, le contrôle de navigateur web bloque la demande automatique de confirmation des téléchargements de fichiers non initiés par l’utilisateur pour tous les processus. Si vous désactivez ce paramètre de stratégie, le contrôle de navigateur web ne bloque pas la demande automatique de confirmation des téléchargements de fichiers non initiés par l’utilisateur pour tous les processus.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Par défaut** : Activé  
  
- **La zone restreinte Internet Explorer autorise uniquement les domaines approuvés pour utiliser les contrôles Active X**   
  Ce paramètre de stratégie détermine si l’utilisateur est invité ou non à autoriser l’exécution des contrôles ActiveX sur des sites web autres que le site web qui a installé le contrôle ActiveX. Si vous activez ce paramètre de stratégie, l’utilisateur est invité à confirmer l’exécution des contrôles ActiveX à partir des sites web de cette zone. L’utilisateur peut choisir d’autoriser l’exécution du contrôle à partir du site actuel ou à partir de tous les sites. Si vous désactivez ce paramètre de stratégie, l’utilisateur ne voit pas l’invite ActiveX propre au site, et les contrôles ActiveX peuvent s’exécuter à partir de tous les sites de cette zone.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer > Zone restreinte : Contrôles d’initialisation et de script ActiveX non marqués comme sécurisés**  
  Ce paramètre de stratégie vous permet de gérer les contrôles ActiveX non marqués comme sécurisés. Si vous activez ce paramètre de stratégie, les contrôles ActiveX sont exécutés, chargés avec des paramètres, puis scriptés sans définir la sécurité des objets pour les scripts ou les données non fiables. Ce paramètre n’est pas recommandé, sauf pour les zones sécurisées et administrées. Ce paramètre entraîne l’initialisation et l’écriture de scripts pour les contrôles sécurisés et non sécurisés, en ignorant l’option Contrôles ActiveX reconnus sûrs pour l’écriture de scripts. Si vous activez ce paramètre de stratégie et sélectionnez Invite dans la zone de liste déroulante, les utilisateurs doivent indiquer s’ils souhaitent autoriser le chargement du contrôle avec des paramètres ou scripté. Si vous désactivez ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés. Si vous ne configurez pas ce paramètre de stratégie, les contrôles ActiveX qui ne peuvent pas être sécurisés ne sont pas chargés avec des paramètres ou scriptés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Par défaut**: désactiver  
  
- **Internet Explorer : modification des stratégies par les utilisateurs**  
  Empêche les utilisateurs de modifier les paramètres des zones de sécurité. Une zone de sécurité est un groupe de sites web partageant le même niveau de sécurité. Si vous activez cette stratégie, le bouton Personnaliser le niveau et le curseur de niveau de sécurité sont désactivés sous l’onglet Sécurité de la boîte de dialogue Options Internet. Si vous désactivez cette stratégie ou ne la configurez pas, les utilisateurs peuvent changer les paramètres des zones de sécurité. Cette stratégie empêche les utilisateurs de changer les paramètres des zones de sécurité configurés par l’administrateur. Remarque : La stratégie « Désactiver la page Sécurité » (située dans \Configuration utilisateur\Modèles d’administration\Composants Windows\Internet Explorer\Panneau de configuration Internet), qui supprime l’onglet Sécurité dans le Panneau de configuration Internet Explorer, est prioritaire sur cette stratégie. Si elle est activée, cette stratégie est ignorée. Consultez également la stratégie « Zones de sécurité : utiliser uniquement des paramètres machine ».  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Mode protégé**  
  Ce paramètre de stratégie vous permet d’activer le mode protégé. Le mode protégé favorise la protection d’Internet Explorer face à des vulnérabilités exploitées en réduisant les emplacements où Internet Explorer peut écrire dans le Registre et le système de fichiers. Si vous activez ce paramètre de stratégie, le mode protégé est activé. L’utilisateur ne peut pas désactiver le mode protégé. Si vous désactivez ce paramètre de stratégie, le mode protégé est désactivé. L’utilisateur ne peut pas activer le mode protégé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver le mode protégé.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Par défaut** : activer  
  
- **Internet Explorer > Zone Internet : Persistance des données utilisateur**  
  Ce paramètre de stratégie vous permet de gérer la conservation des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Quand un utilisateur revient à une page persistante, l’état de la page peut être restauré si ce paramètre de stratégie est configuré de façon appropriée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent conserver des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas conserver d’informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs peuvent conserver des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Internet : Écriture de scripts pour les contrôles de navigateur Web**  
 
  Ce paramètre de stratégie détermine si une page peut gérer les contrôles incorporés WebBrowser par script. Si vous activez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser est autorisé. Si vous désactivez ce paramètre de stratégie, l’accès du script au contrôle WebBrowser n’est pas autorisé. Si vous ne configurez pas ce paramètre de stratégie, l’utilisateur peut activer ou désactiver l’accès du script au contrôle WebBrowser. Par défaut, l’accès du script au contrôle WebBrowser est autorisé uniquement dans les zones Ordinateur local et Intranet.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : Persistance des données utilisateur**  
  Ce paramètre de stratégie vous permet de gérer la conservation des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Quand un utilisateur revient à une page persistante, l’état de la page peut être restauré si ce paramètre de stratégie est configuré de façon appropriée. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent conserver des informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous désactivez ce paramètre de stratégie, les utilisateurs ne peuvent pas conserver d’informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque. Si vous ne configurez pas ce paramètre de stratégie, les utilisateurs ne peuvent pas conserver d’informations dans l’historique du navigateur, dans les favoris, dans un magasin XML ou directement dans une page web enregistrée sur le disque.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone Intranet verrouillée : autorisations Java**  
  Ce paramètre de stratégie vous permet de gérer les autorisations des applets Java. Si vous activez ce paramètre de stratégie, vous pouvez choisir parmi les options dans la zone de liste déroulante. « Personnalisé » permet de contrôler les paramètres d’autorisations de façon individuelle. « Basse sécurité » permet aux applets d’effectuer toutes les opérations. Sécurité moyenne permet aux applets de s’exécuter dans leur bac à sable (une zone mémoire en dehors de laquelle le programme ne peut pas effectuer d’appels), avec en plus des fonctionnalités telles que l’espace de travail (une zone de stockage sécurisée sur l’ordinateur client) et les E/S de fichiers contrôlées par l’utilisateur. « Haute sécurité » permet aux applets de s’exécuter dans leur bac à sable. « Désactiver Java » empêche l’exécution de toutes les applets. Si vous désactivez ce paramètre de stratégie, les applets Java ne peuvent pas s’exécuter. Si vous ne configurez pas ce paramètre de stratégie, les applets Java sont désactivées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Par défaut**: désactiver Java  
  
- **Internet Explorer : mode protégé amélioré**  
  Le mode protégé amélioré renforce la protection contre les sites Web malveillants en utilisant des processus 64 bits sur des versions 64 bits de Windows. Pour les ordinateurs qui exécutent Windows 8 ou version ultérieure, le mode protégé amélioré limite également les emplacements à partir desquels Internet Explorer peut lire dans le Registre et le système de fichiers. Si vous activez ce paramètre de stratégie, le mode protégé amélioré est activé. Toute zone pour laquelle le mode protégé est activé utilise le mode protégé amélioré. Les utilisateurs ne sont pas en mesure de désactiver le mode protégé amélioré. Si vous désactivez ce paramètre de stratégie, le mode protégé amélioré est activé. Toute zone pour laquelle le mode protégé est activé utilise la version du mode protégé introduite dans Internet Explorer 7 pour Windows Vista. Si vous ne configurez pas cette stratégie, les utilisateurs peuvent activer ou désactiver le mode protégé amélioré sur l’onglet Avancé de la boîte de dialogue Options Internet.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Par défaut** : Activé  
  
- **Internet Explorer : ignorer les avertissements SmartScreen**  
  Ce paramètre de stratégie détermine si l’utilisateur peut ignorer les avertissements du filtre SmartScreen. Le filtre SmartScreen avertit l’utilisateur au sujet des fichiers exécutables que les utilisateurs d’Internet Explorer ne téléchargent généralement pas à partir d’Internet. Si vous activez ce paramètre de stratégie, les avertissements du filtre SmartScreen bloquent l’utilisateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, l’utilisateur peut ignorer les avertissements du filtre SmartScreen.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Par défaut** : Désactivé  
  
- **Internet Explorer > Zone restreinte : actualisation des métafichiers**  
  Ce paramètre de stratégie vous permet de spécifier si le navigateur d’un utilisateur peut être redirigé vers une autre page web si l’auteur de la page web utilise le paramètre (la balise) Meta Refresh pour rediriger les navigateurs vers une autre page web. Si vous activez ce paramètre de stratégie, le navigateur d’un utilisateur qui charge une page contenant un paramètre Meta Refresh actif peut être redirigé vers une autre page web. Si vous désactivez ce paramètre de stratégie, le navigateur d’un utilisateur qui charge une page contenant un paramètre Meta Refresh actif ne peut pas être redirigé vers une autre page web. Si vous ne configurez pas ce paramètre de stratégie, le navigateur d’un utilisateur qui charge une page contenant un paramètre Meta Refresh actif ne peut pas être redirigé vers une autre page web.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Par défaut** : Désactivé  
  
## <a name="local-policies-security-options"></a>Options de sécurité des stratégies locales
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) dans la documentation Windows. 

- **Restreindre l’accès anonyme aux canaux nommés et aux partages**  
  Lorsque l’option est activée, ce paramètre de sécurité restreint l’accès anonyme aux partages et aux canaux pour les paramètres pour : (1) des canaux nommés qui peuvent être accessibles de manière anonyme (2) des partages qui sont accessibles de manière anonyme.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Par défaut** : oui  
  
- **Sécurité de session minimale pour les serveurs basés sur NTLM SSP**  
  Ce paramètre de sécurité permet à un serveur d’exiger la négociation d’un chiffrement de 128 bits et/ou de la sécurité de session NTLMv2. Ces valeurs dépendent de la valeur du paramètre de sécurité Niveau d’authentification LAN Manager. Les options sont : nécessite une sécurité de session NTLMv2 : la connexion échoue si l’intégrité des messages n’est pas négociée. Exiger un chiffrement 128 bits : La connexion échoue si un chiffrement fort (128 bits) n’est pas négocié.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Par défaut** : exiger NTLM V2 et un chiffrement de 128 bits  
  
- **Minutes d’inactivité de l’écran de verrouillage avant l’activation de l’économiseur d’écran**  
  Windows identifie les sessions ouvertes inactives. Si le délai d’inactivité dépasse la limite d’inactivité définie, l’écran de veille s’exécute, ce qui entraîne le verrouillage de la session.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Par défaut** : 15
  
- **Exiger du client qu’il signe toujours numériquement les communications** Ce paramètre de sécurité détermine si tout le trafic d’un canal sécurisé initié par le membre du domaine doit être signé ou chiffré. Lorsqu’un ordinateur rejoint un domaine, un compte d’ordinateur est créé. Après cela, lorsque le système démarre, il utilise le mot de passe du compte d’ordinateur pour créer un canal sécurisé avec un contrôleur de domaine pour son domaine. Ce canal sécurisé est utilisé pour effectuer des opérations telles que l’authentification directe NTLM, la recherche de nom SID de l’autorité de sécurité locale (LSA), etc. Ce paramètre détermine si tout le trafic du canal sécurisé initialisé par le membre du domaine répond ou non aux exigences de sécurité minimales. Plus précisément, il détermine si tout le trafic du canal sécurisé initialisé par le membre du domaine doit être signé ou chiffré. Si cette stratégie est activée, le canal sécurisé ne sera établi que si la signature ou le chiffrement de tout le trafic du canal sécurisé est négocié. Si cette stratégie est désactivée, le chiffrement et la signature de tout le trafic du canal sécurisé sont négociés avec le contrôleur de domaine, auquel cas le niveau de signature et de chiffrement dépend de la version du contrôleur de domaine et des paramètres des deux stratégie suivantes : membre de domaine : données de canal sécurisé par le chiffrement numérique (si possible) Membre de domaine : données de canal sécurisé par connexion numérique (si possible).  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Par défaut** : oui
  
- **Niveau d'authentification**  
  Ce paramètre de sécurité détermine le protocole d'authentification de stimulation/réponse utilisé pour les ouvertures de session réseau. Ce choix a une incidence sur le niveau du protocole d'authentification qu'utilisent les clients, le niveau de sécurité de session négocié et le niveau d'authentification qu'acceptent les serveurs, de la façon suivante :  
  - *Envoyer des réponses LM et NTLM* : les clients utilisent les authentifications LM et NTLM et n’ont jamais recours à la sécurité de session NTLMv2. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer des authentifications LM et NTLM, NTLMv2 si négociées* : les clients utilisent les authentifications LM et NTLM, ainsi que la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer une réponse NTLM uniquement* : les clients utilisent uniquement l’authentification NTLM et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer une réponse NTLMv2 uniquement* : les clients utilisent uniquement l’authentification NTLMv2 et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine acceptent les authentifications LM, NTLM et NTLMv2. 
  - *Envoyer uniquement une réponse NTLMv2. Refuser l’authentification LM* : les clients utilisent uniquement l’authentification NTLMv2 et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine refusent l’authentification LM (ils acceptent uniquement les authentifications NTLM et NTLMv2). 
  - *Envoyer uniquement une réponse NTLMv2. Refuser les authentifications LM et NTLM* : les clients utilisent uniquement l’authentification NTLMv2 et la sécurité de session NTLMv2 si le serveur la prend en charge. Les contrôleurs de domaine refusent les authentifications LM et NTLM (ils acceptent uniquement l’authentification NTLMv2).  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Par défaut** : envoyez uniquement une réponse NTLMv2. Refuser LM et NTLM
  
- **Empêcher les clients d’envoyer des mots de passe non chiffrés à des serveurs SMB tiers**  
  Si ce paramètre de sécurité est activé, le redirecteur SMB (Server Message Block) est autorisé à envoyer des mots de passe en clair à des serveurs qui ne sont pas des serveurs Microsoft SMB et qui ne prennent pas en charge le chiffrement des mots de passe lors de l’authentification. L'envoi de mots de passe non chiffrés constitue un risque pour la sécurité.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Par défaut** : oui
  
- **Exige la signature numérique systématique des communications par le serveur**  
  Ce paramètre de sécurité détermine si le client SMB tente de négocier la signature des paquets SMB. Le protocole SMB (Server Message Block) représente la base sur laquelle s'appuient le partage des fichiers et des imprimantes Microsoft ainsi que beaucoup d'autres opérations de gestion de réseau, telles que l'administration à distance de Windows. Pour empêcher des attaques de l’intercepteur, susceptibles de modifier les paquets SMB en transit, le protocole SMB prend en charge la signature numérique des paquets SMB. Ce paramètre de stratégie détermine si le composant client SMB tente de négocier la signature des paquets SMB lorsqu'il se connecte à un serveur SMB. Si ce paramètre est activé, le client réseau Microsoft demandera au serveur de signer les paquets SMB lors de la configuration de la session. Si la signature de paquet a été activée sur le serveur, la signature de paquet est négociée. Si cette stratégie est désactivée, le client SMB ne négocie jamais la signature des paquets SMB.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Par défaut** : oui
  
- **Comportement de l’invite d’élévation d’administrateur**  
  Ce paramètre de stratégie contrôle le comportement de l’invite d’élévation pour les administrateurs. Les options disponibles sont : 
  - *Élever sans invite utilisateur* : permet aux comptes privilégiés d’effectuer une opération qui nécessite une élévation sans demander de consentement ou d’informations d’identification. Remarque : Utilisez cette option uniquement dans les environnements les plus contraints. 
  - *Invite pour les informations d'identification sur le bureau sécurisé* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à entrer un nom d’utilisateur et un mot de passe privilégié. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur. 
  - *Invite pour le consentement sur le bureau sécurisé* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à sélectionner Autoriser et Refuser. Si l’utilisateur sélectionne Autoriser, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur. 
  - *Invite pour les informations d’identification* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité à entrer un nom d’utilisateur et un mot de passe administrateur. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables. 
  - *Invite pour le consentement* : lorsqu’une opération requiert une élévation de privilège, l’utilisateur est invité à choisir entre Autoriser et Refuser. Si l’utilisateur sélectionne Autoriser, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur.  
  - *Invite pour le consentement pour les binaires non Windows* : lorsqu’une opération pour une application non Microsoft nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à choisir entre Autoriser et Refuser. Si l’utilisateur sélectionne Autoriser, l’opération continue avec les privilèges les plus élevés disponibles de l’utilisateur. 
  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Par défaut** : demander le consentement sur le bureau sécurisé
  
- **Sécurité de session minimale pour les clients basés sur NTLM SSP**  
  Ce paramètre de sécurité permet à un client d’exiger la négociation d’un chiffrement de 128 bits et/ou de la sécurité de session NTLMv2. Ces valeurs dépendent de la valeur du paramètre de sécurité Niveau d’authentification LAN Manager. Les options disponibles sont :
  - *Nécessite une sécurité de session NTLMv2* : la connexion échoue si le protocole NTLMv2 n’est pas négocié. 
  - *Nécessite un chiffrement 128 bits* : la connexion échoue si un chiffrement fort (128 bits) n’est pas négocié.
  - *Exiger l’authentification NTLMv2 et un chiffrement de 128 bits*.  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Par défaut** : exiger le chiffrement 128 de l’authentification NTLM V2
  
- **Comportement lorsque la carte à puce est retirée**  
  Ce paramètre de sécurité détermine ce qui se passe quand la carte à puce d’un utilisateur connecté est retirée du lecteur de cartes à puce. Les options disponibles sont :
  - *Aucune action*. 
  - *Verrouiller la station de travail* : la station de travail est verrouillée lorsque la carte à puce est supprimée, ce qui permet aux utilisateurs de quitter la zone, prendre leur carte à puce avec eux tout en conservant une session protégée.
  - *Forcer la fermeture de session* : l’utilisateur est automatiquement déconnecté lorsque la carte à puce est retirée.
  - *Déconnecter la session de Bureau à distance* : le retrait de la carte à puce déconnecte la session sans déconnecter l’utilisateur. Ceci permet à l'utilisateur d'insérer la carte à puce et de reprendre la session ultérieurement ou sur un autre ordinateur équipé d'un lecteur de cartes à puce, sans avoir à ouvrir de nouveau une session. Si la session est locale, cette stratégie fonctionne comme l’option Verrouiller la station de travail.
  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Par défaut** : verrouiller la station de travail
  
- **Bloquer l’énumération anonyme des comptes et partages SAM**  
  Ce paramètre de sécurité détermine si l’énumération anonyme des comptes et partages de gestion des actifs logiciels est autorisée. Windows autorise les utilisateurs anonymes à effectuer certaines activités, comme l'énumération des noms des comptes de domaine et des partages réseau. Cette possibilité est pratique, par exemple lorsqu’un administrateur veut accorder aux utilisateurs l’accès dans un domaine approuvé ne conservant pas une approbation réciproque. Si vous ne voulez pas autoriser l’énumération anonyme des comptes et partages de gestion des actifs logiciels, puis configurez cette stratégie sur *Oui*.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Par défaut** : oui
  
- **Bloquer l’ouverture de session à distance avec un mot de passe vide**  
  Ce paramètre de sécurité détermine si les comptes locaux qui ne sont pas protégés par un mot de passe peuvent être utilisés pour ouvrir une session à partir d’emplacements autres que la console de l’ordinateur physique. S'il est activé, les comptes locaux qui ne sont pas protégés par mot de passe ne permettent une ouverture de session que sur le clavier de l'ordinateur. 

  *Avertissement* : les ordinateurs qui ne se trouvent pas à des emplacements physiquement sécurisés doivent toujours appliquer des stratégies de mot de passe fort pour tous les comptes d’utilisateur locaux. Dans le cas contraire, toute personne ayant un accès physique à l’ordinateur peut ouvrir une session en utilisant un compte d’utilisateur sans mot de passe. Ce paramètre est particulièrement important pour les ordinateurs portables. 

  Si vous appliquez cette stratégie de sécurité au groupe Tout le monde, personne ne peut ouvrir une session via les services Bureau à distance. Ce paramètre n’affecte pas les ouvertures de sessions qui utilisent des comptes de domaine. Les applications qui utilisent des ouvertures de session interactives à distance peuvent contourner ce paramètre.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Par défaut** : oui
  
- **Comportement de l’invite d’élévation d’utilisateur standard**  
  Ce paramètre de stratégie contrôle le comportement de l’invite d’élévation pour les utilisateurs standard. 
  - *Refuser automatiquement les requêtes d’élévation* : lorsqu’une opération nécessite une élévation de privilège, un message d’erreur d’accès configurable refusé s’affiche. Une entreprise qui utilise des ordinateurs de bureau en tant qu’utilisateur standard peut choisir ce paramètre pour réduire les appels au support technique. 
  - *Invite pour les informations d'identification sur le bureau sécurisé* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité sur le bureau sécurisé à entrer un nom d’utilisateur et un mot de passe différent. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables. 
  - *Invite pour les informations d’identification* : lorsqu’une opération nécessite une élévation de privilège, l’utilisateur est invité à entrer un nom d’utilisateur et un mot de passe administrateur. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables.  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Par défaut** : refuser automatiquement les demandes d’élévation de privilèges
  
- **Exiger le mode d’approbation Administrateur pour les administrateurs**  
  Ce paramètre de stratégie contrôle le comportement de tous les paramètres de stratégie de contrôle de compte d’utilisateur (UAC) pour l’ordinateur. Si vous modifiez ce paramètre de stratégie, vous devez redémarrer votre ordinateur. Les options disponibles sont :   
  - *Non configuré* : le mode d’approbation Administrateur et tous les paramètres de stratégie UAC associés sont désactivés. Remarque : Si ce paramètre de stratégie est désactivé, le Centre de sécurité vous avertit que la sécurité globale du système d’exploitation a été réduite. 
  - *Oui* : le mode d’approbation Administrateur est activé. Cette stratégie doit être activée et les paramètres de stratégie UAC associés doivent également être définis en conséquence pour permettre au compte Administrateur intégré et à tous les autres utilisateurs membres du groupe Administrateurs de s’exécuter en mode d’approbation Administrateur.  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Par défaut** : oui
  
- **Empêcher l’énumération anonyme des comptes SAM**  
  Ce paramètre de sécurité détermine quelles autorisations supplémentaires sont octroyées aux connexions anonymes à l’ordinateur. Windows autorise les utilisateurs anonymes à effectuer certaines activités, comme l'énumération des noms des comptes de domaine et des partages réseau. Cette possibilité est pratique, par exemple lorsqu’un administrateur veut accorder aux utilisateurs l’accès dans un domaine approuvé ne conservant pas une approbation réciproque. Cette option de sécurité permet d'imposer aux connexions anonymes les restrictions supplémentaires suivantes : 
  - *Oui* : ne pas autoriser l’énumération des comptes de gestion des actifs logiciels. Cette option remplace Tout le monde par Utilisateurs authentifiés dans les autorisations de sécurité pour les ressources.
  - *Non configuré* : aucune autre restriction. Correspond aux autorisations par défaut.  
  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Par défaut** : oui
  
- **Autoriser les appels distants au Gestionnaire des comptes de sécurité**  
  Ce paramètre de stratégie vous permet de limiter les connexions rpc à distance au gestionnaire SAM. S’il n’est pas sélectionné, le descripteur de sécurité par défaut est utilisé.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Par défaut** : *O:BAG:BAD:(A;;RC;;;BA)*

- **Utiliser le mode d’approbation Administrateur**  
  Ce paramètre de sécurité détermine le comportement du mode d’approbation Administrateur pour le compte Administrateur intégré. Les options disponibles sont : 
  - *Oui* : le compte Administrateur intégré utilise le mode d’approbation Administrateur. Par défaut, une invite d’approbation est présentée à l’utilisateur pour chaque opération nécessitant une élévation de privilège. 
  - *Non configuré* : le compte Administrateur intégré exécute toutes les applications avec des privilèges administratifs complets. 

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Par défaut** : oui
  
- **Autoriser les applications d’accès de l’interface utilisateur pour des emplacements sécurisés**  
  Ce paramètre de sécurité indique si les programmes d’accessibilité de l’interface utilisateur (UIAccess ou UIA) peuvent désactiver automatiquement le bureau sécurisé pour les invites d’élévation utilisées par un utilisateur standard. 
  - *Oui* : les programmes UIA, notamment l’Assistance à distance Windows, désactivent automatiquement le bureau sécurisé pour les invites d’élévation. Si vous ne désactivez pas le paramètre de stratégie « Contrôle de compte d’utilisateur : passer au bureau sécurisé lors d’une demande d’élévation », les invites s’affichent sur le bureau de l’utilisateur interactif et non sur le bureau sécurisé. 
  - *Non configuré* : le bureau sécurisé ne peut être désactivé que par l’utilisateur du bureau interactif ou en désactivant le paramètre de stratégie « Contrôle de compte d’utilisateur : passer au bureau sécurisé lors d’une demande d’élévation ».  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Par défaut** : oui

- **Détecter les installations d’applications et demander l’élévation**  
  Ce paramètre de stratégie contrôle le comportement de détection des installations d’applications pour l’ordinateur. Les options disponibles sont : 
  - *Activé* : lorsqu’un package d’installation d’application nécessitant une élévation de privilège est détecté, l’utilisateur est invité à entrer un nom d’utilisateur et un mot de passe administrateur. Si l’utilisateur entre des informations d’identification valides, l’opération continue avec les privilèges applicables. 
  - *Désactivé* : les packages d’installation d’application ne sont pas détectés ni invités pour une élévation. Les entreprises qui utilisent des ordinateurs de bureau pour utilisateur standard et ont recours à des technologies d’installation déléguée telles que GPSI (Group Policy Software Install) ou SMS (Systems Management Server) doivent désactiver ce paramètre de stratégie. Dans ce cas, la détection d’un programme d’installation n’est pas nécessaire.  
  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Par défaut** : oui
  
- **Empêcher le stockage d’une valeur de hachage LAN Manager lors du prochain changement de mot de passe**  
  Ce paramètre de sécurité détermine si, au prochain changement de mot de passe, la valeur de hachage LAN Manager (LM) est stockée pour le nouveau mot de passe. Le hachage LM est relativement faible et vulnérable aux attaques par rapport au hachage Windows NT, plus fort en matière de chiffrement. Étant donné que le hachage LM est stocké sur l’ordinateur local dans la base de données de sécurité, les mots de passe peuvent être compromis si la base de données de sécurité est attaquée.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Par défaut** : oui

- **Virtualiser les échecs d’écriture de fichier et de Registre dans des emplacements par utilisateur**  
  Ce paramètre de stratégie détermine si les échecs d’écriture d’application sont redirigés vers des emplacements définis du système de fichiers et du Registre. Ce paramètre de stratégie atténue les applications qui s’exécutent en tant qu’administrateur et écrivent des données d’application au moment de l’exécution dans *%ProgramFiles%* , *%Windir%* , *%Windir%\system32*, or *HKLM\Software*.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Par défaut** : oui

## <a name="ms-security-guide"></a>Guide de sécurité Microsoft  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) dans la documentation Windows.  

- **Appliquer des restrictions du contrôle de compte d’utilisateur à des comptes locaux lors de l’ouverture de session réseau**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Par défaut** : Activé
  
- **Configuration de démarrage du pilote du client SMB v1**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Par défaut** : pilote désactivé
  
- **Serveur SMB v1**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Par défaut** : Désactivé
  
- **Authentification Digest**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Par défaut** : Désactivé
  
- **Protection structurée contre le remplacement de la gestion des exceptions**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Par défaut** : Activé
  
## <a name="mss-legacy"></a>MSS hérité  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) dans la documentation Windows.  

- **Niveau de protection du routage de source IP réseau**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Par défaut** : protection la plus élevée  
  
- **Ignorer sur le réseau les demandes de libération de noms NetBIOS sauf à partir de serveurs WINS**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Par défaut** : Activé
  
- **Niveau de protection du routage de source IPv6 réseau**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Par défaut** : protection la plus élevée

- **Les redirections ICMP réseau remplacent les routes OSPF générées**  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Par défaut** : Désactivé
  
## <a name="power"></a>Puissance  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) dans la documentation Windows.  

- **Exiger un mot de passe à la sortie de veille quand l’appareil est branché**  
  Ce paramètre de stratégie spécifie si l’utilisateur doit entrer un mot de passe à la sortie du mode veille du système. Si vous activez ou ne configurez pas ce paramètre de stratégie, l’utilisateur est invité à entrer un mot de passe lorsque le système sort du mode veille. Si vous désactivez ce paramètre de stratégie, l’utilisateur n’est pas invité à entrer de mot de passe lorsque le système sort du mode veille.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Par défaut** : Activé
  
- **États de mise en attente lorsque l'appareil est en veille sur batterie**  
  Ce paramètre de stratégie indique si Windows est autorisé à utiliser les états de mise en attente lors de la mise en veille de l'ordinateur. Si vous activez ou ne configurez pas ce paramètre de stratégie, Windows utilise les états de mise en attente pour mettre l’ordinateur en veille. Si vous désactivez ce paramètre de stratégie, les états de mise en attente (S1-S3) ne sont pas autorisés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Par défaut** : Désactivé
  
- **États de mise en attente lorsque l'appareil est en veille et branché**  
  Ce paramètre de stratégie indique si Windows est autorisé à utiliser les états de mise en attente lors de la mise en veille de l'ordinateur. Si vous activez ou ne configurez pas ce paramètre de stratégie, Windows utilise les états de mise en attente pour mettre l’ordinateur en veille. Si vous désactivez ce paramètre de stratégie, les états de mise en attente (S1-S3) ne sont pas autorisés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Par défaut** : Désactivé
  
- **Exiger un mot de passe à la sortie de veille quand l’appareil est sur batterie**  
  Ce paramètre de stratégie spécifie si l’utilisateur doit entrer un mot de passe à la sortie du mode veille du système. Si vous activez ou ne configurez pas ce paramètre de stratégie, l’utilisateur est invité à entrer un mot de passe lorsque le système sort du mode veille. Si vous désactivez ce paramètre de stratégie, l’utilisateur n’est pas invité à entrer de mot de passe lorsque le système sort du mode veille.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Par défaut** : Activé

## <a name="remote-assistance"></a>Assistance à distance
- **Assistance à distance sollicitée**  
  Ce paramètre de stratégie vous permet d’activer ou de désactiver l’assistance à distance sollicitée (demander) sur cet ordinateur. 
  - *Si vous activez ce paramètre de stratégie*, les utilisateurs de cet ordinateur peuvent utiliser la messagerie ou le transfert de fichiers pour demander de l’aide à une personne. En outre, les utilisateurs peuvent utiliser des programmes de messagerie instantanée pour autoriser les connexions à cet ordinateur, et vous pouvez configurer des paramètres d’assistance à distance supplémentaires. 
  - *Si vous désactivez ce paramètre de stratégie*, les utilisateurs de cet ordinateur ne peuvent pas utiliser de courrier électronique ou de transfert de fichiers pour demander de l’aide à une personne. En outre, les utilisateurs ne peuvent pas utiliser les programmes de messagerie instantanée pour autoriser les connexions à cet ordinateur. 
  - *Si vous ne configurez pas ce paramètre de stratégie*, les utilisateurs peuvent activer ou désactiver l’assistance à distance (demandez) eux-mêmes dans les propriétés système du panneau de configuration. Les utilisateurs peuvent également configurer les paramètres d’assistance à distance. 

  Si vous activez ce paramètre de stratégie, vous disposez de deux méthodes pour permettre aux applications d’assistance de fournir une assistance à distance: «autoriser les applications d’assistance à afficher uniquement l’ordinateur» ou «autoriser le contrôle à distance de l’ordinateur par les assistances». Le paramètre de stratégie «durée maximale du ticket» définit une limite sur la durée pendant laquelle une invitation d’assistance à distance créée à l’aide de la messagerie ou du transfert de fichiers peut rester ouverte. Le paramètre «sélectionner la méthode d’envoi d’invitations par courrier électronique» spécifie la norme de messagerie à utiliser pour envoyer des invitations d’assistance à distance. En fonction de votre programme de messagerie, vous pouvez utiliser la norme mailto (le destinataire de l’invitation se connecte via une liaison Internet) ou la norme SMAPI (simple MAPI) (l’invitation est jointe à votre message électronique). Ce paramètre de stratégie n’est pas disponible dans Windows Vista, car SMAPI est la seule méthode prise en charge. Si vous activez ce paramètre de stratégie, vous devez également activer les exceptions de pare-feu appropriées pour permettre les communications d’assistance à distance.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Par défaut**: désactiver l’assistance à distance

  Quand vous définissez cette *fonctionnalité sur Activer l’assistance à distance*, configurez les paramètres supplémentaires suivants:  
  - **Autorisation sollicitée d’assistance à distance**  
    **Par défaut** : affichage  

  - **Valeur maximale de la durée du ticket**  
    **Par défaut** : *non configuré*  

  - **Période de temps maximale du ticket**  
    **Valeur par défaut**: minutes    

  - **Méthode d’invitation par courrier électronique**  
    **Valeur par défaut**: MAPI simple

  
## <a name="remote-desktop-services"></a>Services Bureau à distance  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) dans la documentation Windows.  

- **Bloquer l’enregistrement de mot de passe**  
  Indique si les mots de passe peuvent être enregistrés sur cet ordinateur à partir de la connexion Bureau à distance. Si vous activez ce paramètre, la case à cocher proposant d’enregistrer le mot de passe dans Connexion Bureau à distance est désactivée et les utilisateurs ne peuvent plus enregistrer les mots de passe. Lorsqu’un utilisateur ouvre un fichier RDP à l’aide de la Connexion Bureau à distance et enregistre ses paramètres, tout mot de passe qui existait précédemment dans le fichier RDP est supprimé. Si vous désactivez ce paramètre ou ne le configurez pas, l’utilisateur peut enregistrer les mots de passe en utilisant la Connexion Bureau à distance.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Par défaut** : Activé
  
- **Sécuriser la communication RPC**  
  Spécifie si un serveur hôte de session Bureau à distance nécessite des communications RPC sécurisées avec tous les clients ou autorise les communications non sécurisées. Vous pouvez utiliser ce paramètre pour renforcer la sécurité des communications RPC avec les clients en n'autorisant que les demandes chiffrées et authentifiées. Si vous activez ce paramètre, les Services Bureau à distance acceptent les demandes des clients RPC qui prennent en charge les demandes sécurisées et n’autorisent pas les communications non sécurisées avec des clients non approuvés. Si vous désactivez ce paramètre, les services Bureau à distance demandent toujours des mesures de sécurité pour tout le trafic RPC. Toutefois, les communications non sécurisées sont autorisées pour les clients RPC qui ne répondent pas à la demande. Si vous ne configurez pas ce paramètre, les communications non sécurisées sont autorisées. Remarque : L’interface RPC sert à administrer et configurer les Services Bureau à distance.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Par défaut** : Activé
  
- **Bloquer la redirection des lecteurs**  
  Ce paramètre de stratégie spécifie s’il faut empêcher ou non le mappage des lecteurs client dans une session des services Bureau à distance (redirection de lecteur). Par défaut, un serveur hôte de session Bureau à distance mappe automatiquement les lecteurs client à la connexion. Les lecteurs mappés apparaissent dans l'arborescence des dossiers de sessions dans l'Explorateur de fichiers ou Poste de travail sous le format *\<lettre_lecteur>* dans *\<nom_ordinateur>* . Vous pouvez utiliser ce paramètre de stratégie pour remplacer ce comportement. Si vous activez ce paramètre de stratégie, la redirection des lecteurs client n’est pas autorisée dans les sessions des Services Bureau à distance, et la redirection de copie de fichiers du Presse-papiers n’est pas autorisée sur les ordinateurs exécutant Windows Server 2003, Windows 8 et Windows XP. Si vous désactivez ce paramètre de stratégie, la redirection des lecteurs client est toujours autorisée. En outre, la redirection de copie de fichiers du Presse-papiers est toujours autorisée si la redirection du Presse-papiers est autorisée. Si vous ne configurez pas ce paramètre de stratégie, la redirection de lecteurs client et la redirection de copie de fichiers du Presse-papiers ne sont pas spécifiées au niveau de la stratégie de groupe.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Par défaut** : Activé
  
- **Demander un mot de passe lors de la connexion**  
  Ce paramètre de stratégie spécifie si les services Bureau à distance demandent toujours au client de fournir un mot de passe lors de la connexion. Vous pouvez utiliser ce paramètre pour forcer la demande de mot de passe aux utilisateurs se connectant aux services Bureau à distance, même s'ils ont déjà fourni le mot de passe dans le client de connexion au Bureau à distance. Par défaut, les services Bureau à distance autorisent les utilisateurs à se connecter automatiquement en entrant un mot de passe dans le client de connexion au Bureau à distance. Si vous activez ce paramètre de stratégie, les utilisateurs ne peuvent pas se connecter automatiquement aux Services Bureau à distance en fournissant leurs mots de passe dans le client de la Connexion Bureau à distance. Un mot de passe leur est demandé pour ouvrir une session. Si vous activez ce paramètre de stratégie, les utilisateurs peuvent toujours se connecter automatiquement aux services Bureau à distance en fournissant leurs mots de passe dans le client de connexion au Bureau à distance. Si vous ne configurez pas ce paramètre de stratégie, l’ouverture de session automatique n’est pas spécifiée au niveau de la stratégie de groupe.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Par défaut** : Activé
  
- **Niveau de chiffrement de connexion des clients aux services Bureau à distance**  
  Spécifie s’il faut exiger l’utilisation d’un niveau de chiffrement spécifique pour sécuriser les communications entre les ordinateurs clients et les serveurs hôtes de session Bureau à distance lors de connexions RDP (Remote Desktop Protocol). Cette stratégie s’applique uniquement lorsque vous utilisez le chiffrement RDP natif. Toutefois, le chiffrement RDP natif (contrairement au chiffrement SSL) n’est pas recommandé. Cette stratégie ne s’applique pas au chiffrement SSL. Si vous activez ce paramètre de stratégie, toutes les communications entre les clients et les serveurs hôtes de session Bureau à distance au cours des connexions à distance doivent utiliser la méthode de chiffrement spécifiée dans ce paramètre. Par défaut, le niveau de chiffrement est défini sur Élevé. Vous pouvez utiliser les méthodes de chiffrement suivantes :  
  - *Élevé* : le paramètre Élevé chiffre les données envoyées du client au serveur et du serveur au client à l’aide d’un chiffrement de 128 bits renforcé. Utilisez ce niveau de chiffrement dans des environnements qui contiennent uniquement des clients 128 bits (par exemple, les clients qui exécutent la connexion Bureau à distance). Les clients qui ne prennent pas en charge ce niveau de chiffrement ne peuvent pas se connecter aux serveurs Hôte de session Bureau à distance.  
  - *Compatible client* : le paramètre Compatible client chiffre les données envoyées entre le client et le serveur à la puissance de clé maximale prise en charge par le client. Utilisez ce niveau de chiffrement dans les environnements qui incluent les clients qui ne prennent pas en charge le chiffrement de 128 bits.  
  - *Faible* : le paramètre Faible chiffre uniquement les données envoyées du client au serveur à l’aide d’un chiffrement de 56 bits.  
  
  Si vous désactivez ce paramètre ou ne le configurez pas, le niveau de chiffrement à utiliser pour les connexions à distance aux serveurs Hôte de session Bureau à distance n’est pas appliqué via la stratégie de groupe. Une conformité FIPS importante peut être configurée via le chiffrement système. Utilisez des algorithmes compatibles FIPS pour les paramètres de chiffrement, de hachage et de signature dans la stratégie de groupe (sous Configuration ordinateur\Paramètres Windows\Paramètres de sécurité\Stratégies locales\Options de sécurité). Le paramètre compatible FIPS chiffre et déchiffre les données envoyées du client au serveur et du serveur au client, avec les algorithmes de chiffrement FIPS (Federal Information Processing Standard) 140, à l’aide des modules de chiffrement Microsoft. Utilisez ce niveau de chiffrement lorsque les communications entre les clients et les serveurs hôtes de session Bureau à distance nécessitent le niveau de chiffrement le plus élevé.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Par défaut** : élevé
  
## <a name="remote-management"></a>Gestion à distance  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) dans la documentation Windows.  

- **Bloquer l’exécution du stockage en tant qu’informations d’identification**  
  Authentification de base client.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Par défaut** : Activé
  
- **Authentification de base**  
  Ce paramètre de stratégie vous permet de spécifier si le service Windows Remote Management (WinRM) accepte l’authentification de base à partir d’un client distant. Si vous activez ce paramètre de stratégie, le service WinRM accepte l’authentification de base à partir d’un client distant. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le service WinRM n’accepte pas l’authentification de base à partir d’un client distant.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Par défaut** : Désactivé
  
- **Bloquer l’authentification Digest client**  
  Ce paramètre de stratégie vous permet de spécifier si le client Windows Remote Management (WinRM) utilise l’authentification Digest. Si vous activez ce paramètre de stratégie, le client WinRM n’utilise pas l’authentification Digest. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM utilise l’authentification Digest.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Par défaut** : Activé
  
- **Trafic non chiffré**  
  Ce paramètre de stratégie vous permet de spécifier si le service Windows Remote Management (WinRM) envoie et reçoit des messages non chiffrés via le réseau. Si vous activez ce paramètre de stratégie, le client WinRM envoie et reçoit des messages non chiffrés via le réseau. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM envoie ou reçoit uniquement des messages chiffrés via le réseau.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Par défaut** : Désactivé
  
- **Trafic client non chiffré**  
  Ce paramètre de stratégie vous permet de spécifier si le client Windows Remote Management (WinRM) envoie et reçoit des messages non chiffrés via le réseau. Si vous activez ce paramètre de stratégie, le client WinRM envoie et reçoit des messages non chiffrés via le réseau. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM envoie ou reçoit uniquement des messages chiffrés via le réseau.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Par défaut** : Désactivé
  
- **Authentification de base client**  
  Ce paramètre de stratégie vous permet de spécifier si le client Windows Remote Management (WinRM) utilise l’authentification de base. Si vous activez ce paramètre de stratégie, le client WinRM utilise l’authentification de base. Si WinRM est configuré pour utiliser le transport HTTP, le nom d’utilisateur et le mot de passe sont envoyés via le réseau en texte clair. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, le client WinRM utilise l’authentification de base.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Par défaut** : Désactivé
  
## <a name="remote-procedure-call"></a>Appel de procédure distante  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) dans la documentation Windows.  

- **Options du client RPC non authentifié**  
  Ce paramètre de stratégie contrôle la façon dont le runtime du serveur RPC gère les clients RPC non authentifiés se connectant aux serveurs RPC. Ce paramètre de stratégie affecte toutes les applications RPC. Dans un environnement de domaine, utilisez ce paramètre de stratégie avec précaution, car il peut avoir un impact sur un large éventail de fonctionnalités, y compris sur le traitement de la stratégie de groupe lui-même. Le rétablissement d’une modification apportée à ce paramètre de stratégie peut nécessiter une intervention manuelle sur chaque machine affectée. Ce paramètre de stratégie ne doit jamais être appliqué à un contrôleur de domaine. Si vous désactivez ce paramètre de stratégie, le runtime du serveur RPC utilise la valeur « Authentifié » sur le client Windows et la valeur « Aucun » sur les versions de Windows Server qui prennent en charge ce paramètre de stratégie. Si vous ne configurez pas ce paramètre de stratégie, il reste désactivé. Le runtime du serveur RPC se comporte comme s’il avait été activé avec la valeur « Authentifié » utilisée pour le client Windows et la valeur « Aucun » utilisée pour les références SKU Server qui prennent en charge ce paramètre de stratégie. Si vous activez ce paramètre de stratégie, il indique au runtime du serveur RPC de limiter les clients RPC non authentifiés qui se connectent aux serveurs RPC s’exécutant sur une machine. Un client est considéré comme étant authentifié s’il utilise un canal nommé pour communiquer avec le serveur ou s’il utilise la sécurité RPC. Les interfaces RPC qui ont demandé spécifiquement à être accessible par des clients non authentifiés peuvent être exemptées de cette restriction, en fonction de la valeur sélectionnée pour ce paramètre de stratégie.  
  - *Aucun* permet à tous les clients RPC de se connecter aux serveurs RPC s’exécutant sur la machine sur laquelle le paramètre de stratégie est appliqué. 
  - *Authentifié* autorise seulement les clients RPC authentifiés (selon la définition ci-dessus) à se connecter aux serveurs RPC s’exécutant sur la machine sur laquelle le paramètre de stratégie est appliqué. Des exemptions sont accordées aux interfaces qui les ont demandées. 
  - *Authentifié sans exceptions* autorise seulement les clients RPC authentifiés (selon la définition ci-dessus) à se connecter aux serveurs RPC s’exécutant sur la machine sur laquelle le paramètre de stratégie est appliqué. Aucune exception n’est autorisée. Remarque : Ce paramètre de stratégie n’est pas appliqué tant que le système n’est pas redémarré.  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Par défaut** : authentifié

## <a name="search"></a>Recherche 
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Recherche](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) dans la documentation Windows.  

- **Désactiver l’indexation des éléments chiffrés**  
  Autorise ou interdit l’indexation des éléments. Ce commutateur concerne l’indexeur Windows Search, qui contrôle s’il indexe les éléments chiffrés, comme les fichiers protégés par la Protection des informations Windows. Quand la stratégie est activée, les éléments protégés par la Protection des informations Windows sont indexés et leurs métadonnées sont stockées à un emplacement non chiffré. Les métadonnées incluent des éléments comme le chemin et la date de modification des fichiers. Lorsque la stratégie est désactivée, les éléments TEC protégés ne sont pas indexés et n’apparaissent pas dans les résultats de Cortana ou de l’Explorateur de fichiers. Il peut également y avoir un impact sur les performances pour les photos et les applications Groove si de nombreux fichiers multimédias sont protégés par la Protection des informations Windows sur l’appareil.  
  [En savoir plus]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Par défaut** : oui
  
## <a name="smart-screen"></a>SmartScreen  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) dans la documentation Windows.  

- **Bloquer l’exécution de fichiers non vérifiés**  
  Bloque l’exécution par l’utilisateur des fichiers non vérifiés. 
  - *Non configuré* : les employés peuvent ignorer les avertissements SmartScreen et exécuter des fichiers malveillants. 
  - *Oui* : les employés ne peuvent pas ignorer les avertissements SmartScreen et exécuter des fichiers malveillants.

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Par défaut** : oui

- **Exiger SmartScreen pour les applications et les fichiers**  
  Permet aux administrateurs informatiques de configurer SmartScreen pour Windows.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Par défaut** : oui
  
## <a name="system"></a>Système  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Système](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) dans la documentation Windows.  

- **Système : Initialisation des pilotes de démarrage**  
  Ce paramètre de stratégie vous permet de spécifier quels pilotes de démarrage sont initialisés selon une classification déterminée par un pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé. Le pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé peut retourner les classifications suivantes pour chaque pilote de démarrage : 
  - *Bon* : le pilote a été signé et n’a pas été falsifié.  
  - *Mauvais* : Le pilote a été identifié comme étant un programme malveillant. Il est recommandé de ne pas autoriser l’initialisation des mauvais pilotes connus. 
  - *Mauvais, mais requis lors du démarrage* : le pilote a été identifié comme étant un programme malveillant, mais l’ordinateur ne peut pas démarrer correctement sans charger ce pilote. 
  - *Inconnu* : ce pilote n’a pas été confirmé par votre application de détection des programmes malveillants et n’a pas été classé par le pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé.  

  Si vous activez ce paramètre de stratégie, vous pouvez choisir les pilotes de démarrage à initialiser lors du prochain démarrage de l’ordinateur. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas, les pilotes de démarrage déterminés comme étant « Bons », « Inconnus » ou « Mauvais, mais critique pour le démarrage » sont initialisés. L’initialisation des pilotes déterminés comme étant « Mauvais » est ignorée. Si votre application de détection des programmes malveillants n’inclut pas un pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé ou si votre pilote de démarrage du logiciel anti-programme malveillant à lancement anticipé a été désactivé, ce paramètre n’a aucun effet et tous les pilotes de démarrage sont initialisés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Par défaut** : Bon, Inconnu et Mauvais, mais critique


## <a name="wi-fi"></a>Wi-Fi  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) dans la documentation Windows.  

- **Bloquer le partage Internet**  
  Spécifie si le partage Internet est possible sur l’appareil.   
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Par défaut** : oui  

- **Bloquer la connexion automatique aux points d’accès Wi-Fi**  
  Autorise ou interdit la connexion automatique de l’appareil aux points d’accès Wi-Fi.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Par défaut** : oui  
  
## <a name="windows-connection-manager"></a>Gestionnaire de connexions Windows  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) dans la documentation Windows.  

- **Bloquer la connexion aux réseaux sans domaine**  
  Ce paramètre de stratégie empêche les ordinateurs de se connecter en même temps à un réseau avec domaine et à un réseau sans domaine. Si ce paramètre de stratégie est activé, l’ordinateur répond aux tentatives de connexion au réseau automatiques et manuelles selon les circonstances suivantes : 
  - Tentatives de connexion automatiques : quand l’ordinateur est déjà connecté à un réseau avec domaine, toutes les tentatives de connexion automatiques à des réseaux sans domaine sont bloquées. Quand l’ordinateur est déjà connecté à un réseau sans domaine, les tentatives de connexion automatiques à des réseaux avec domaine sont bloquées. 
  - Tentatives de connexion manuelles : lorsque l’ordinateur est déjà connecté à un réseau sans domaine ou à un réseau avec domaine via un média autre qu’Ethernet, et qu’un utilisateur tente de créer une connexion manuelle à un autre réseau en violation de ce paramètre de stratégie, la connexion réseau existante est déconnectée et la connexion manuelle est autorisée. Quand l’ordinateur est déjà connecté à un réseau sans domaine ou à un réseau avec domaine via Ethernet, et qu’un utilisateur tente de créer une connexion manuelle à un autre réseau en violation de ce paramètre de stratégie, la connexion Ethernet existante est maintenue et la tentative de connexion manuelle est bloquée.  

  Si ce paramètre de stratégie n’est pas configuré ou est désactivé, les ordinateurs sont autorisés à se connecter simultanément à des réseaux avec domaine et sans domaine.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Par défaut** : Activé
  
## <a name="windows-defender"></a>Windows Defender  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) dans la documentation Windows.  

- **Analyser les e-mails entrants**  
  Autorise ou interdit l’analyse des e-mails.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Par défaut** : oui  

- **Les applications Office lancent un type de processus enfant**  
  Les applications Office ne sont pas autorisées à créer des processus enfants. Elles incluent Word, Excel, PowerPoint, OneNote et Access. Il s’agit d’un comportement malveillant typique, en particulier pour les attaques basées sur des macros qui tentent d’utiliser des applications Office pour lancer ou télécharger des fichiers exécutables malveillants.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Par défaut** : bloc
  
- **Type de consentement pour l’envoi d’exemples par Defender**  
  Vérifie le niveau de consentement de l’utilisateur dans Windows Defender pour envoyer des données. Si le consentement nécessaire a déjà été accordé, Windows Defender les envoie. Si ce n’est pas le cas (et si l’utilisateur a spécifié de ne jamais lui demander), l’interface utilisateur est lancée pour demander le consentement de l’utilisateur (quand Defender/AllowCloudProtection est autorisé) avant d’envoyer des données.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Par défaut** : Envoyer automatiquement des échantillons sécurisés 
  
- **Intervalle de mise à jour des signatures (en heures)**  
  Intervalle de mise à jour des signatures de Defender en heures
  
  **Par défaut** : 4
  
- **Script : type d’exécution de charge utile téléchargée**  
  Script Defender : type d’exécution de charge utile téléchargée
  
  **Par défaut** : bloc
  
- **Empêcher le vol d’informations d’identification**  
  Windows Defender Credential Guard utilise une sécurité basée sur la virtualisation pour isoler les secrets, afin que seuls les logiciels système privilégiés puissent y accéder. L’accès non autorisé à ces informations secrètes peut entraîner des vols, par exemple de type Pass-the-Hash ou Pass-the-Ticket. Windows Defender Credential Guard empêche ces attaques en protégeant les hachages de mot de passe NTLM, les TGT (Ticket Granting Ticket) Kerberos et les informations d’identification stockées par les applications comme informations d’identification de domaine.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Par défaut** : activer

- **Type d’exécution du contenu des e-mails**  
  Cette règle bloque les types de fichiers suivants pour qu’ils ne soient pas exécuter ou lancée à partir d’un email dans Microsoft Outlook ou d’une message sur le Web (par exemple, Gmail.com ou Outlook.com) : fichiers exécutables (par exemple, .exe, .dll ou .scr) fichiers de Script (par exemple, un fichier .ps PowerShell, .vbs VisualBasic, .js ou JavaScript) fichiers d’archive de Script.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **Par défaut** : bloc

- **Lancement d’Adobe Reader dans un processus enfant**  

  **Par défaut** : activer

- **Type de protection réseau**  
  Cette stratégie vous permet d’activer la protection réseau (bloquer/auditer) ou de la désactiver dans Windows Defender Exploit Guard. La protection réseau est une fonctionnalité de Windows Defender Exploit Guard qui protège les employés utilisant une application d’accéder à des tentatives d’hameçonnage, à des sites hébergeant du code malveillant exploitant une faille de sécurité et à du contenu malveillant sur Internet. Cela inclut le fait d’empêcher des navigateurs tiers de se connecter à des sites dangereux. Le type de la valeur est un entier. Si vous activez ce paramètre, la protection réseau est activée et les employés ne peuvent pas la désactiver. Son comportement peut être contrôlé par les options suivantes : Bloquer et Auditer. Si vous activez cette stratégie avec l’option « Bloquer », la connexion des utilisateurs et des applications à des domaines dangereux est bloquée. Vous pouvez consulter cette activité dans Windows Defender Security Center. Si vous activez cette stratégie avec l’option « Auditer », la connexion des utilisateurs/applications à des domaines dangereux n’est pas bloquée. Vous pouvez néanmoins toujours voir cette activité dans le Centre de sécurité Windows Defender. Si vous désactivez cette stratégie, la connexion des utilisateurs/applications à des domaines dangereux n’est pas bloquée. Vous ne voyez pas cette activité réseau dans le Centre de sécurité Windows Defender. Si vous ne configurez pas cette stratégie, le blocage réseau est désactivé par défaut.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067102)  
  
  **Par défaut** : activer
  
- **Defender : Planifier le jour de l’analyse**  
  Jour de l’analyse planifié dans Defender.
  
  **Par défaut** : tous les jours
  
- **Protection assurée par le cloud**  
  Pour protéger au mieux votre PC, Windows Defender envoie des informations à Microsoft sur les problèmes détectés. Microsoft analyse ces informations, en apprend plus sur les problèmes qui vous affectent ainsi que d’autres clients, et offre des solutions améliorées.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Par défaut** :  oui  

- **Defender : action contre les applications potentiellement indésirables**  
  La fonctionnalité de protection contre les applications potentiellement indésirables dans l’antivirus Windows Defender peut identifier et bloquer le téléchargement et l’installation des applications potentiellement indésirables sur les points de terminaison de votre réseau. Ces applications ne sont pas considérées comme des virus, des logiciels malveillants ou d’autres types de menaces, mais elles peuvent effectuer des actions sur les points de terminaison qui dégradent leurs performances ou leur utilisation. Les applications potentiellement indésirables peuvent également faire référence à des applications considérées comme ayant une mauvaise réputation. Le comportement typique des PUA est notamment : différents types de bundle de logiciels Injection de publicité dans les navigateurs web, Optimiseurs de pilotes et du Registre qui détectent des problèmes et proposent de corriger les erreurs moyennant finance, mais restent sur le point de terminaison et n'effectuent ni changements ni optimisations (connus aussi sous le nom de programmes « antivirus non fiables »). Ces applications peuvent augmenter le risque d'infection de votre réseau par des programmes malveillants, rendent les infections de programmes malveillants difficiles à identifier et peuvent utiliser à perte les ressources informatiques pour nettoyer les applications.  
  [En savoir plus](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Par défaut** : bloc  

- **Type de code de macro obfusqué dans les scripts**  
  Les logiciels malveillants et d’autres menaces peuvent tenter d’obfusquer ou de masquer leur code malveillant dans certains fichiers de script. Cette règle empêche l’exécution des scripts qui paraissent obfusqués.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Par défaut** : bloc
  
- **Analyser les disques amovibles lors d’une analyse complète**  
  Permet à Windows Defender rechercher les logiciels malveillants et indésirables dans les lecteurs amovibles (par exemple les lecteurs flash) lors d’une analyse complète. L’antivirus Windows Defender analyse tous les fichiers sur les périphériques USB avant exécution.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Par défaut** : oui  
  
- **Analyser les fichiers d’archive**  
  Defender : Analyser les fichiers d’archive.
  
  **Par défaut** : oui
  
- **Surveillance du comportement**  
  Autorise ou interdit la fonctionnalité de surveillance du comportement de Windows Defender. Intégré dans Windows 10, ces capteurs collectent et traitent les signaux comportementaux du système d’exploitation et envoient ces données de capteur à votre instance cloud, isolée et privée de Windows Defender ATP.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Par défaut** : oui

- **Analyser les fichiers ouverts à partir de dossiers réseau**  
  Si des fichiers sont en lecture seule, l’utilisateur ne peut pas supprimer les programmes malveillants détectés.
  
  **Par défaut** : oui

- **Type de processus USB non approuvés**  
  Avec cette règle, les administrateurs peuvent empêcher l’exécution des fichiers exécutables non signés ou non fiables partir de lecteurs USB amovibles, notamment les cartes SD.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Par défaut** : bloc
  
- **Applications Office : Type d’injection dans d’autres processus**  
  Les applications Office, notamment Word, Excel, PowerPoint et OneNote, ne peuvent pas injecter du code dans d’autres processus. Ceci est généralement utilisé par des programmes malveillants pour exécuter du code malveillant de façon à masquer l’activité aux moteurs d’analyse antivirus.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Par défaut** : bloc
  
- **Code de macro Office autorisant un type d’importation Win32**  
  Les programmes malveillants peuvent utiliser du code de macro dans des fichiers Office pour importer et charger des DLL Win32, qui peuvent alors être utilisées pour effectuer des appels d’API, permettant ensuite une infection de tout le système. Cette règle tente de bloquer les fichiers Office qui contiennent du code de macro capable d’importer des DLL Win32. Ceci inclut Word, Excel, PowerPoint et OneNote.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Par défaut** : bloc  
  
- **Defender : Niveau de blocage cloud**  
  Niveau de blocage cloud de Defender.
  
  **Par défaut** : non configuré

- **Surveillance en temps réel**  
  Defender requiert une surveillance en temps réel.
  
  **Par défaut** : oui
 
- **Lancement d’applications de communication Office dans un processus enfant**  

  **Par défaut** : activer

- **Applications Office : type de création ou de lancement de contenu exécutable**  
  Cette règle cible des comportements typiques utilisés par des modules complémentaires et des scripts suspects et malveillants (extensions) qui créent ou lancent des fichiers exécutables. Il s’agit d’une technique classique des programmes malveillants. L’utilisation des extensions par les applications Office est bloquée. En général, ces extensions utilisent l’hôte de script Windows (fichiers .wsh) pour exécuter des scripts qui automatisent certaines tâches ou fournissent des fonctionnalités de modules complémentaires créés par l’utilisateur.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Par défaut** : bloc

## <a name="windows-defender-firewall"></a>Pare-feu Windows Defender  
Pour plus d’informations, consultez [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) dans la documentation des protocoles Windows.  

- **Domaine du profil de pare-feu**  
  Spécifie les profils auxquels appartient la règle : domaine, privé, public. Cette valeur représente le profil des réseaux qui sont connectés à des domaines.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Connexions entrantes bloquées**  
    **Par défaut** : oui

  - **Connexions sortantes requises**  
    **Par défaut** : oui 

  - **Notifications entrantes bloquées**  
    **Par défaut** : oui

  - **Pare-feu activé**  
    **Par défaut** : autorisé

- **Profil de pare-feu public**  
  Spécifie les profils auxquels appartient la règle : domaine, privé, public. Cette valeur représente le profil des réseaux publics. Ces réseaux sont classés publics par les administrateurs dans l’hôte du serveur. La classification se produit dès que l’hôte se connecte au réseau. Ces réseaux sont généralement dans les aéroports, cafés-restaurants et autres lieux publics, où les pairs dans le réseau ou l’administrateur réseau ne sont pas approuvés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Connexions entrantes bloquées**  
    **Par défaut** : oui

  - **Connexions sortantes requises**  
    **Par défaut** : oui 

  - **Notifications entrantes bloquées**  
    **Par défaut** : oui

  - **Pare-feu activé**  
    **Par défaut** : autorisé

  - **Non fusion des règles de sécurité de connexion à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Non fusion des règles de stratégie à partir de la stratégie de groupe**  
    **Par défaut** : oui

- **Profil de pare-feu privé**  
  Spécifie les profils auxquels appartient la règle : domaine, privé, public. Cette valeur représente le profil des réseaux privés.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **Connexions entrantes bloquées**  
    **Par défaut** : oui

  - **Connexions sortantes requises**  
    **Par défaut** : oui 

  - **Notifications entrantes bloquées**  
    **Par défaut** : oui

  - **Pare-feu activé**  
    **Par défaut** : autorisé

## <a name="windows-hello-for-business"></a>Windows Hello Entreprise  
- **Exiger la détection d’usurpation avancée, si disponible**  
  Si c’est le cas, les appareils utilisent l’anti-usurpation améliorée, le cas échéant. Si ce n’est pas le cas, l’anti-usurpation est bloquée. Non configuré honore les configurations effectuées sur le client.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Par défaut** : oui

- **Configurer Windows Hello for Business**   
    Windows Hello Entreprise est une méthode alternative de connexion à Windows en remplaçant les mots de passe, les cartes à puce et les cartes à puce virtuelles.  

  - Lorsque la valeur est *Oui*, vous activez cette stratégie et l’appareil provisionne Windows Hello entreprise.  
  - Lorsque la valeur *n’est pas configurée*, la ligne de base n’affecte pas le paramètre de stratégie de l’appareil. Cela signifie que si Windows Hello entreprise est désactivé sur un appareil, il reste désactivé. Si elle est activée, elle reste activée. 

  Vous ne pouvez pas désactiver Windows Hello entreprise par le biais de cette ligne de base. Vous pouvez désactiver Windows Hello entreprise lors de la configuration de l' [inscription Windows](windows-hello.md)ou dans le cadre d’un profil de configuration d’appareil pour la [protection d’identité](identity-protection-configure.md).  

  **Par défaut** : oui

- **Exiger des minuscules dans le code confidentiel**  
  Si nécessaire, le code PIN de l’utilisateur doit inclure au moins une lettre minuscule.

  **Par défaut** : autorisé

- **Exiger des caractères spéciaux dans le code confidentiel**  
  Si nécessaire, le code PIN de l’utilisateur doit inclure au moins un caractère spécial.

  **Par défaut** : autorisé

- **Longueur minimale du code confidentiel**  
  La longueur minimale du code confidentiel doit être comprise entre 4 et 127.

  **Par défaut** : 6

- **Exiger des majuscules dans le code confidentiel**  
  Si nécessaire, le code PIN de l’utilisateur doit inclure au moins une lettre majuscule.

  **Par défaut** : autorisé

## <a name="windows-ink-workspace"></a>Espace de travail Windows Ink  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) dans la documentation Windows.  

- **Espace de travail Ink**  
  Spécifie s’il faut autoriser l’utilisateur à accéder à l’espace de travail Ink. 
  - *Désactivé* : l’accès à l’espace de travail Ink est désactivé. La fonctionnalité est désactivée.
  - *Activé* : la fonctionnalité Espace de travail Ink est activée, mais l’utilisateur ne peut pas y accéder sur l’écran de verrouillage.
  - *Non configuré* : la fonctionnalité Espace de travail Ink est activée, mais l’utilisateur ne peut pas y accéder sur l’écran de verrouillage.  

  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Par défaut** : Activé
 
## <a name="windows-powershell"></a>Windows PowerShell  
Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) dans la documentation Windows.  

- **Journalisation de blocs de scripts PowerShell**  
  Ce paramètre de stratégie active la journalisation de toutes les entrées de script PowerShell dans le journal des événements Microsoft-Windows-PowerShell/Operational. Si vous activez ce paramètre de stratégie, Windows PowerShell journalise le traitement des commandes, les blocs de script, les fonctions et les scripts, qu’il soit appelé de façon interactive ou via l’automatisation. Si vous désactivez ce paramètre de stratégie, la journalisation des entrées de script PowerShell est désactivée. Si vous activez la journalisation des appels de bloc de script, PowerShell journalise en plus les événements lors de l’appel d’une commande, un bloc de script, d’une fonction, ou quand un script démarre ou s’arrête. L’activation de la journalisation des appels génère un grand volume de journaux des événements. Remarque : Ce paramètre de stratégie existe à la fois sous Configuration ordinateur et Configuration utilisateur dans l’Éditeur de stratégie de groupe. Le paramètre de stratégie de Configuration ordinateur est prioritaire sur le paramètre de stratégie Configuration utilisateur.  
  [En savoir plus](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Par défaut** : Activé

## <a name="whats-changed-in-the-new-template"></a>Ce qui a changé dans le nouveau modèle
La *ligne de base de sécurité MDM pour le modèle 2019 mai* présente les modifications suivantes par rapport à la version *préliminaire* du modèle.

### <a name="changes-to-the-baseline-settings"></a>Modifications apportées aux paramètres de base
Les paramètres suivants sont soit :
- *Nouveauté* de cette dernière version de la ligne de base.
- *Supprimé* de cette dernière version de référence, mais qui étaient présents dans la version précédente.
- *Modifié* de quelque manière que ce soit de la façon dont les paramètres apparaissent dans la version précédente. 

*[Nouveau]* [**Au-dessus du verrou**](#above-lock):
- **Activer les applications vocales à partir de l’écran verrouillé**    

*[Nouveau]* [**Gestion des applications**](#application-management) : 
- **Bloquer le contrôle utilisateur sur les installations**  
- **Bloquer les installations d’applications MSI avec des privilèges élevés**  

*[Supprimé]* [**BitLocker**](#bitlocker):  
- Stratégie de lecteur amovible de verrouillage de bits > **méthode** de chiffrement
- **Stratégie de lecteur fixe de verrouillage de bits** *(tous les paramètres)*
- **Stratégie de lecteur système du dispositif de verrouillage de bit** *(tous les paramètres)*

*[Nouveau]* [**Connectivité**](#connectivity) :
- **Configurer un accès sécurisé aux chemins UNC**

*[Nouveau]* [**Protection de l’appareil**](#device-guard) :
- **Sécurité basée sur la virtualisation**


*[Nouveau]* [**Protection de DMA**](#dma-guard):
- **Énumération des périphériques externes incompatibles avec la protection DMA de noyau**  

*[Nouveau]* [**Internet Explorer**](#internet-explorer) :
- **La zone Internet Explorer se met à jour sur la barre d’état via un script**
- **Fichiers glisser et déplacer ou copier et coller de la zone internet Internet Explorer**  
- **Composants dépendants du .NET Framework de la zone restreinte Internet Explorer**  
- **La zone de l’ordinateur local Internet Explorer n’exécute pas de logiciel anti-programme malveillant sur les contrôles ActiveX**
- **Prise en charge du chiffrement Internet Explorer**  

*[Révisé]* [**Internet Explorer**](#internet-explorer):
- **Invite automatique de la zone Internet Internet Explorer pour les téléchargements de fichiers** > la valeur par défaut est désormais **désactivée**. Dans Aperçu, cette option a été activée.

*[Nouveau]* [**Assistance à distance**](#remote-assistance) :  
- **Assistance à distance sollicitée** 
  - **Autorisation sollicitée d’assistance à distance**
  - **Valeur maximale de la durée du ticket**  
  - **Période de temps maximale du ticket**  
  - **Méthode d’invitation par courrier électronique**


*[Nouveau]* [**Windows Defender**](#windows-defender) :
- **Lancement d’Adobe Reader dans un processus enfant**  
- **Lancement d’applications de communication Office dans un processus enfant** 

*[Nouveau]* [**Pare-feu Windows Defender**](#windows-defender-firewall)
- **Domaine du profil de pare-feu**  
  - **Connexions entrantes bloquées**  
  - **Connexions sortantes requises**  
  - **Notifications entrantes bloquées**  
  - **Pare-feu activé**  
- **Profil de pare-feu public**  
  - **Connexions entrantes bloquées**  
  - **Connexions sortantes requises**  
  - **Notifications entrantes bloquées**  
  - **Pare-feu activé** 
  - **Non fusion des règles de sécurité de connexion à partir de la stratégie de groupe**   
  - **Non fusion des règles de stratégie à partir de la stratégie de groupe**  
- **Profil de pare-feu privé**  
  - **Connexions entrantes bloquées**  
  - **Connexions sortantes requises**  
  - **Notifications entrantes bloquées**  
  - **Pare-feu activé**  

*[Nouveau]* [**Windows Hello for Business**](#windows-hello-for-business) :  
- **Exiger la détection d’usurpation avancée, si disponible**  
- **Configurer Windows Hello for Business**  
- **Exiger des minuscules dans le code confidentiel** 
- **Exiger des caractères spéciaux dans le code confidentiel** 
- **Longueur minimale du code confidentiel**  
- **Exiger des majuscules dans le code confidentiel** 



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Windows Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Windows Defender SmartScreen. Enabling this policy turns off Windows Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Windows defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Windows Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Windows Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Windows Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Windows Defender Exploit Guard. Network protection is a feature of Windows Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Windows Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Windows Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Windows Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Windows Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Windows Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Windows Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Windows Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->
