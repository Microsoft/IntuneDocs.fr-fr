---
title: Paramètres de bases de référence de la sécurité Intune pour Microsoft Defender Advanced Threat Protection
titleSuffix: Microsoft Intune
description: Paramètres de bases de référence de la sécurité pris en charge par Intune pour la gestion de Microsoft Defender Advanced Threat Protection
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: eee3d4187dd513cd3945e86aff478fe96b341660
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71732956"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Paramètres de bases de référence de Windows Defender Advanced Threat Protection pour Intune

Afficher les paramètres de bases de référence de Microsoft Defender Advanced Threat Protection (anciennement Windows Defender Advanced Threat Protection) qui sont pris en charge par Microsoft Intune. Les valeurs par défaut de la base de référence Advanced Threat Protection (ATP) représentent la configuration recommandée pour ATP. Elles peuvent ne pas correspondent aux valeurs par défaut pour d’autres bases de référence de sécurité.  

Ligne de base Microsoft Defender Advanced Threat Protection est disponible lorsque votre environnement répond à la configuration requise pour l’utilisation de [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites). 

Cette ligne de base est optimisée pour les appareils physiques et n’est actuellement pas recommandée pour une utilisation sur des machines virtuelles ou des points de terminaison VDI. Certains paramètres de la base de référence peuvent impacter les sessions interactives à distance sur les environnements virtualisés. Pour plus d’informations, consultez [Améliorer la conformité à la base de référence de la sécurité de Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) dans la documentation Windows.


> [!NOTE]  
> Les paramètres de base de référence ATP sont en **préversion**. En préversion, la liste des paramètres disponibles et l’ordre dans lequel ce contenu les présente varient en fonction de ce qui est disponible dans le portail.  
>
> Lorsque les paramètres de base de référence sont hors Préversion, ce contenu est mis à jour pour correspondre à une liste actuelle des paramètres de base de référence de la sécurité pris en charge par Intune.

## <a name="application-guard"></a>Application Guard  
Pour plus d’informations, consultez [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp) dans la documentation Windows.  

Lors de l’utilisation de Microsoft Edge, Windows Defender Application Guard protège votre environnement des sites qui ne sont pas approuvés par votre organisation. Quand des utilisateurs visitent des sites qui ne figurent pas dans la liste des limites de votre réseau isolé, les sites s’ouvrent dans une session de navigation virtuelle Hyper-V. Les sites de confiance sont définis par une limite réseau.  

- **Application Guard** - *Paramètres/AllowWindowsDefenderApplicationGuard*  
  Sélectionnez *Oui* pour activer cette fonctionnalité, ce qui ouvre des sites non approuvés dans un conteneur de navigation virtualisé Hyper-V. Lorsque défini sur *Non configuré*, n’importe quel site (approuvé et non approuvé) s’ouvre sur l’appareil et pas dans un conteneur virtualisé.  

  **Par défaut** : oui
 
  - **Contenu externe sur les sites d’entreprise** - *Paramètres/BlockNonEnterpriseContent*  
    Sélectionnez *Oui* pour bloquer le chargement du contenu des sites web non approuvés. Lorsque défini sur *Non configuré* les sites autres que les sites d’entreprise peuvent s’ouvrir sur l’appareil. 
 
    **Par défaut** : oui

  - **Comportement du Presse-papiers** - *Paramètres/ClipboardSettings*  
    Choisissez les actions de copier-coller autorisées entre le PC local et le navigateur virtuel Application Guard.  Les options sont les suivantes :
    - *Non configuré*  
    - *Bloquer les deux* : impossible de transférer les données entre l’ordinateur et le navigateur virtuel.  
    - *Bloquer l’hôte vers le conteneur* : impossible de transférer les données à partir de l’ordinateur dans le navigateur virtuel.
    - *Bloquer le conteneur vers l’hôte* : impossible de transférer les données à partir du navigateur virtuel vers l’ordinateur hôte.
    - *Aucun bloc* : aucun bloc de contenu existe.  

    **Par défaut** : bloquer les deux  

- **Stratégie d’isolation de réseau Windows – noms de domaine réseau d’entreprise**  
  Pour plus d’informations, consultez [Stratégie CSP - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation) dans la documentation Windows.
  
  Spécifiez une liste de ressources d’entreprise en tant que domaines, plages d’adresses IP et limites réseau hébergés dans le cloud que l’Application Guard traite comme des sites d’entreprise.  

  **Par défaut** : securitycenter.windows.com

## <a name="application-reputation"></a>Réputation de l’application  

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) dans la documentation Windows.

- **Bloquer l’exécution de fichiers non vérifiés**  
    Bloque l’exécution par l’utilisateur des fichiers non vérifiés. Lorsque défini sur *Non configuré*, les employés peuvent ignorer les avertissements SmartScreen et exécuter des fichiers malveillants. Définissez-le sur *Oui* pour que les employés ne puissent pas ignorer les avertissements SmartScreen et exécuter des fichiers malveillants.  
  
    **Par défaut** : oui

- **Exiger SmartScreen pour les applications et les fichiers**  
  Définissez-le sur *Oui* pour activer SmartScreen pour Windows.  

  **Par défaut** : oui

## <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque  

- **Les applications Office lancent un type de processus enfant**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : lorsque définie sur*Bloc*, les applications Office ne seront pas autorisées à créer des processus enfants. Les applications Office incluent Word, Excel, PowerPoint, OneNote et Access. La création d’un processus enfant est un comportement malveillant standard, en particulier pour les attaques basées sur des macros qui tentent d’utiliser des applications Office pour lancer ou télécharger des fichiers exécutables malveillants.  

  **Par défaut** : bloc

- **Script : type d’exécution de charge utile téléchargée**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) : spécifiez un niveau de détection pour les applications potentiellement indésirables que vous téléchargez ou tentez d’installer.  

  **Par défaut** : bloc 

- **Empêcher le vol d’informations d’identification**  
  Définissez sur *Activer* pour [Protéger les informations d’identification de domaine dérivées avec Credential Guard](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard). Windows Defender Credential Guard utilise une sécurité basée sur la virtualisation pour isoler les secrets, afin que seuls les logiciels système privilégiés puissent y accéder. L’accès non autorisé à ces informations secrètes peut entraîner des vols, par exemple de type Pass-the-Hash ou Pass-the-Ticket. Windows Defender Credential Guard empêche ces attaques en protégeant les hachages de mot de passe NTLM, les TGT (Ticket Granting Ticket) Kerberos et les informations d’identification stockées par les applications comme informations d’identification de domaine.  

  **Par défaut** : activer

- **Type d’exécution du contenu des e-mails**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : lorsque définie sur *Bloc*, cette règle empêche l’exécution ou le lancement des types de fichiers suivants à partir d’un email affiché dans Microsoft Outlook ou dans une messagerie Web (par exemple Gmail.com ou Outlook.com) :  

  - Fichiers exécutables (par exemple, .exe, .dll ou .scr)  
  - Fichiers de script (par exemple, un fichier .ps PowerShell, .vbs VisualBasic ou .js JavaScript)  
  - Fichiers d’archive de script  

  **Par défaut** : bloc

- **Lancement d’Adobe Reader dans un processus enfant**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : *activez* cette règle pour bloquer Adobe Reader à partir de la création d’un processus enfant. Via le piratage psychologique ou des attaques, les programmes malveillants peuvent télécharger et lancer des charges utiles supplémentaires et rompre Adobe Reader.  

  **Par défaut** : activer

- **Type de code de macro obfusqué dans les scripts**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : les programme malveillants et d’autres menaces peuvent tenter d’obfusquer ou de masquer leur code malveillant dans certains fichiers de script. Cette règle empêche l’exécution des scripts qui paraissent obfusqués.  
    
  **Par défaut** : bloc

- **Type de processus USB non approuvés**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : lorsque définie sur *Bloc*, les fichiers exécutables, non signés ou non approuvés à partir de lecteurs USB amovibles et de cartes SD ne peuvent pas s’exécuter.

  Les fichiers exécutables incluent :
  - Fichiers exécutables (par exemple, .exe, .dll ou .scr)
  - Fichiers de script (par exemple, un fichier .ps PowerShell, .vbs VisualBasic ou .js JavaScript)  

  **Par défaut** : bloc

- **Applications Office : Type d’injection dans d’autres processus**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : lorsque définie sur *Bloc*, les applications Office, notamment Word, Excel, PowerPoint et OneNote, ne peuvent pas injecter du code dans d’autres processus. L’injection de code est généralement utilisé par des programmes malveillants pour exécuter du code malveillant de façon à tenter de masquer l’activité depuis des moteurs d’analyse antivirus.  

  **Par défaut** : bloc

- **Code de macro Office autorisant un type d’importation Win32**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : lorsque définie sur *Bloc*, cette règle tente de bloquer des fichiers Office qui contiennent du code de macro que vous pouvez importer les DLL Win32. Les fichiers Office incluent Word, Excel, PowerPoint et OneNote. Les programmes malveillants peuvent utiliser du code de macro dans des fichiers Office pour importer et charger des DLL Win32, qui peuvent alors être utilisées pour effectuer des appels d’API, permettant ensuite une infection de tout le système.  

  **Par défaut** : bloc

- **Lancement d’applications de communication Office dans un processus enfant**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : lorsque la valeur est définie sur *Activer*, cette règle empêche Outlook de créer des processus enfants. En bloquant la création d’un processus enfant, cette règle protège contre les attaques de piratage psychologique et empêche le code d’exploitation à partir de l’utilisation abusive d’une vulnérabilité dans Outlook.  

  **Par défaut** : activer

- **Applications Office : type de création ou de lancement de contenu exécutable**  
  [Règle de réduction de la surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard#attack-surface-reduction-rules) : lorsque la valeur est définie sur *Bloc*, les applications Office ne peuvent pas créer du contenu exécutable. Les applications Office incluent Word, Excel, PowerPoint, OneNote et Access.  

  Cette règle cible des comportements typiques utilisés par des modules complémentaires et des scripts suspects et malveillants (extensions) qui créent ou lancent des fichiers exécutables. Il s’agit d’une technique classique des programmes malveillants. L’utilisation des extensions par les applications Office est bloquée. En général, ces extensions utilisent l’hôte de script Windows (fichiers .wsh) pour exécuter des scripts qui automatisent certaines tâches ou fournissent des fonctionnalités de modules complémentaires créés par l’utilisateur.

  **Par défaut** : bloc

## <a name="bitlocker"></a>BitLocker  

Pour plus d’informations, consultez [Paramètres de stratégie de groupe Bitlocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings) dans la documentation Windows.  

- **Chiffrer les appareils**  
  Sélectionnez *Oui* pour activer le chiffrement BitLocker de l’appareil. Selon le matériel de l’appareil et la version de Windows, les utilisateurs d’appareils peuvent être invités à confirmer qu’il n’existe aucun chiffrement tiers sur l’appareil. L’activation du chiffrement de Windows lorsque le chiffrement de tiers est actif affichera l’appareil comme instable.  

   **Par défaut** : oui

- **Stratégie de lecteur amovible BitLocker**  
  Les valeurs de cette stratégie déterminent la force du chiffrement utilisé par BitLocker pour le chiffrement des lecteurs amovibles. Les entreprises contrôlent le niveau de chiffrement pour renforcer la sécurité (AES-256 est plus puissant que AES-128). Si vous sélectionnez *Oui* pour activer ce paramètre, vous pouvez configurer un algorithme de chiffrement et la puissance de chiffrement clé pour les lecteurs de données fixes, les lecteurs de système d’exploitation et les lecteurs de données amovibles individuellement. Pour les lecteurs du système fixe et de fonctionnement, nous vous recommandons d’utiliser l’algorithme AES-XTS. Pour les lecteurs amovibles, vous devez utiliser AES-CBC 128 bits ou AES-CBC 256 bits si le lecteur est utilisé sur d’autres appareils qui n’exécutent pas la version 1511 de Windows 10 ou une version ultérieure. Le changement de la méthode de chiffrement est sans effet si le disque est déjà chiffré ou si le chiffrement est en cours. Dans ces cas, ce paramètre de stratégie est ignoré. 

  Pour la stratégie de lecteur amovible BitLocker, configurez les paramètres suivants :

  - **Exiger le chiffrement pour l’accès en écriture**  
    **Par défaut** : oui

  - **Méthode de chiffrement**  
    **Par défaut** : AES-CBC 128 bits

- **Stratégie de lecteur fixe BitLocker**  
  Les valeurs de cette stratégie déterminent la force du chiffrement utilisé par BitLocker pour le chiffrement des lecteurs amovibles. Les entreprises contrôlent le niveau de chiffrement pour renforcer la sécurité (AES-256 est plus puissant que AES-128). Si vous activez ce paramètre, vous pouvez configurer un algorithme de chiffrement et la puissance de chiffrement clé pour les lecteurs de données fixes, les lecteurs de système d’exploitation et les lecteurs de données amovibles individuellement. Pour les lecteurs du système fixe et de fonctionnement, nous vous recommandons d’utiliser l’algorithme AES-XTS. Pour les lecteurs amovibles, vous devez utiliser AES-CBC 128 bits ou AES-CBC 256 bits si le lecteur est utilisé sur d’autres appareils qui n’exécutent pas la version 1511 de Windows 10 ou une version ultérieure. Le changement de la méthode de chiffrement est sans effet si le disque est déjà chiffré ou si le chiffrement est en cours. Dans ces cas, ce paramètre de stratégie est ignoré.

  Pour la stratégie de lecteur fixe BitLocker, configurez les paramètres suivants :

  - **Exiger le chiffrement pour l’accès en écriture**  
    **Par défaut** : oui

  - **Méthode de chiffrement**  
    **Par défaut** : AES-XTS 128 bits

- **Stratégie de lecteur système BitLocker**  
  Les valeurs de cette stratégie déterminent la force du chiffrement utilisé par BitLocker pour le chiffrement du lecteur système. Les entreprises peuvent contrôler le niveau de chiffrement pour renforcer la sécurité (AES-256 est plus puissant que AES-128). Si vous activez ce paramètre, vous pouvez configurer un algorithme de chiffrement et la puissance de chiffrement clé pour les lecteurs de données fixes, les lecteurs de système d’exploitation et les lecteurs de données amovibles individuellement. Pour les lecteurs du système fixe et de fonctionnement, nous vous recommandons d’utiliser l’algorithme AES-XTS. Pour les lecteurs amovibles, vous devez utiliser AES-CBC 128 bits ou AES-CBC 256 bits si le lecteur est utilisé sur d’autres appareils qui n’exécutent pas la version 1511 de Windows 10 ou une version ultérieure. Le changement de la méthode de chiffrement est sans effet si le disque est déjà chiffré ou si le chiffrement est en cours. Dans ces cas, ce paramètre de stratégie est ignoré.  

  Pour la stratégie de lecteur système BitLocker, configurez les paramètres suivants :  

  - **Méthode de chiffrement**  
    **Par défaut** : AES-XTS 128 bits

## <a name="device-control"></a>Contrôle de l’appareil  

- **Analyser les disques amovibles lors d’une analyse complète**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) : lorsque la valeur est définie sur*Oui*, Defender recherchera les logiciels malveillants et indésirables dans les lecteurs amovibles, tels que les lecteurs flash, lors d’une analyse complète. L’antivirus Windows Defender analyse tous les fichiers sur les périphériques USB avant exécution des fichiers sur l’appareil USB.

  Paramètre connexe dans cette liste : *Defender/AllowFullScanOnMappedNetworkDrives*  

  **Par défaut** : oui

- **Énumération des périphériques externes incompatibles avec la protection DMA de noyau**  
   Consultez *DmaGuard/DeviceEnumerationPolicy* dans [stratégie CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  Cette stratégie offre une sécurité supplémentaire par rapport à des appareils compatibles DMA externes. Elle permet de mieux contrôler l’énumération des appareils compatibles DMA externes qui sont incompatibles avec le sandboxing et l’isolation de la mémoire de l’appareil DMA.

  Cette stratégie n’entre en vigueur que lorsque la protection DMA de noyau est prise en charge et activée par le microprogramme système. La protection DMA de noyau est une fonctionnalité de plateforme qui ne peut pas être contrôlée par la stratégie ou par l’utilisateur d’un appareil. Il doit être pris en charge par le système au moment de la fabrication. 

  Pour vérifier si le système prend en charge la protection DMA de noyau, exécutez MSINFO32.exe sur le système et révisez le champ *Protection DMA de noyau* sur la page Résumé.  

  Les options sont les suivantes : 
  - *Valeur par défaut de l’appareil* : après la connexion ou le déverrouillage de l’écran, des appareils avec pilotes compatibles au remappage DMA peuvent être énumérés à tout moment. Les appareils avec pilotes compatibles au remappage DMA seront énumérés uniquement une fois que l’utilisateur déverrouille l’écran
  - *Autoriser tout* : tous les appareils PCIe compatibles DMA externes seront énumérés à tout moment
  - *Bloquer tout* : les appareils avec pilotes compatibles au remappage DMA peuvent être énumérés à tout moment. Les appareils avec pilotes compatibles au remappage DMA ne seront jamais autorisés pour démarrer et effectuer le DMA à tout moment.

  **Par défaut** : valeurs par défaut de l’appareil

- **Installation de périphériques matériels par identificateurs d’appareil**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) : cette stratégie vous permet de spécifier une liste d’ID de matériel Plug-and-Play et d’ID compatibles de périphériques que Windows ne peut pas installer. Ce paramètre de stratégie prévaut sur tout autre paramètre de stratégie autorisant l’installation de périphériques par Windows. Si vous activez ce paramètre de stratégie, (défini sur *Bloquer l’installation du périphérique matériel*), Windows n’est pas autorisé à installer un périphérique dont l’ID de matériel ou l’ID compatible figure dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur Bureau à distance, la stratégie a une incidence sur la redirection des périphériques spécifiés à partir d’un client Bureau à distance vers le serveur Bureau à distance. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas (défini sur *Autoriser l’installation du périphérique matériel*), des périphériques peuvent être installés et mis à jour conformément aux autorisations ou interdictions prévues par d’autres paramètres de stratégie.  

  **Par défaut** : Bloquer l’installation de périphériques matériels  

  Lorsque la case *Bloquer l’installation de périphériques matériels* est sélectionnée, les paramètres suivants sont disponibles.
  - **Supprimer les périphériques matériels correspondants**  
    Ce paramètre est disponible uniquement quand *Installation de périphériques matériels par identificateurs d’appareil* a la valeur *Bloquer l’installation de périphériques matériels*.  

    **Par défaut** : *Aucune configuration par défaut*

  - **Identificateurs de périphériques matériels bloqués**  
    Ce paramètre est disponible uniquement quand *Installation de périphériques matériels par identificateurs d’appareil* a la valeur *Bloquer l’installation de périphériques matériels*. Pour configurer ce paramètre, développez l’option, sélectionnez **+ Ajouter**, puis spécifiez l’identificateur de périphérique matériel que vous souhaitez bloquer.  

    **Par défaut** : *aucun appareil bloqué*  

- **Bloquer l’accès direct à la mémoire**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) : utilisez ce paramètre de stratégie pour bloquer l’accès direct à la mémoire (DMA) pour tous les ports en aval PCI enfichables à chaud sur un appareil, jusqu’à ce qu’un utilisateur se connecte sur Windows. Une fois l’utilisateur connecté, Windows énumère les périphériques PCI connectés aux ports PCI enfichables à chaud. À chaque verrouillage de l’ordinateur par l’utilisateur, l’Assistant Migration de données Microsoft est bloqué sur les ports PCI enfichables à chaud sans périphériques enfants, tant que l’utilisateur ne se reconnecte pas. Les périphériques déjà énumérés quand l’ordinateur a été déverrouillé continuent de fonctionner tant qu’ils sont branchés. 

  Ce paramètre de stratégie est appliqué uniquement quand BitLocker ou le chiffrement de l’appareil est activé.  

  **Par défaut** : oui


- **Installation de périphériques matériels par classes d’installation**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) : cette stratégie permet de spécifier une liste d’identificateur global unique de classe d’installation de périphériques (GUID) décrivant les pilotes de périphériques que Windows ne peut pas installer. Ce paramètre de stratégie prévaut sur tout autre paramètre de stratégie autorisant l’installation de périphériques par Windows. Si vous activez ce paramètre de stratégie (défini sur *Bloquer l’installation de périphérique matériel*), Windows ne peut pas installer ou mettre à jour les pilotes de périphériques dont les GUID de classe d’installation de périphériques figurent dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur Bureau à distance, il a une incidence sur la redirection des périphériques spécifiés à partir d’un client Bureau à distance vers le serveur Bureau à distance. Si vous désactivez ce paramètre de stratégie ou ne le configurez pas (défini sur *Autoriser l’installation du périphérique matériel*), Windows peut installer et mettre à jour des périphériques conformément aux autorisations ou interdictions prévues par d’autres paramètres de stratégie.  

  **Par défaut** : Bloquer l’installation de périphériques matériels

  Lorsque la case *Bloquer l’installation de périphériques matériels* est sélectionnée, les paramètres suivants sont disponibles.  

  - **Supprimer les périphériques matériels correspondants**  
    Ce paramètre est disponible seulement quand *Installation de périphériques matériels par classes d’installation* est défini sur *Bloquer l’installation de périphériques matériels*.  
 
    **Par défaut** : *Aucune configuration par défaut*  

  - **Identificateurs de périphériques matériels bloqués**  
    Ce paramètre est disponible seulement quand l’installation de périphériques matériels par classes d’installation est défini sur Bloquer l’installation de périphériques matériels. Pour configurer ce paramètre, développez l’option, sélectionnez **+ Ajouter**, puis spécifiez l’identificateur de périphérique matériel que vous souhaitez bloquer.  
 
    **Par défaut** : *aucun appareil bloqué*

## <a name="endpoint-detection-and-response"></a>Détection de point de terminaison et réponse  
Pour plus d’informations, consultez [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp) dans la documentation Windows.  

- **Augmenter la fréquence des rapports de télémétrie** - *Configuration/TelemetryReportingFrequency*  

  Augmente la fréquence des rapports de télémétrie de Microsoft Defender Advanced Threat Protection.  

  **Par défaut** : oui

- **Partage d’exemples pour tous les fichiers** - *Configuration/SampleSharing*  

  Retourne ou définit le paramètre de configuration du partage d'exemples de Microsoft Defender Advanced Threat Protection.  

  **Par défaut** : oui

## <a name="exploit-protection"></a>Exploit Protection  

- **Protection contre le code malveillant XML**  
  Pour plus d’informations, consultez [Importer, exporter et déployer des configurations de protection contre le code malveillant](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/import-export-exploit-protection-emet-xml) dans la documentation de Windows.  

  Permet à l’administrateur informatique de diffuser une configuration qui représente les options souhaitées d’atténuation des risques pour le système et les applications auprès de tous les appareils de l’organisation. La configuration est représentée par du code XML. 

  Exploit Protection aide à protéger les appareils contre les programmes malveillants qui utilisent du code malveillant exploitant une faille de sécurité pour se propager et les infecter. Utilisez l’application Sécurité Windows ou PowerShell pour créer un ensemble d’atténuations des risques (qui est appelé « configuration »). Vous pouvez ensuite exporter cette configuration dans un fichier XML et le partager sur plusieurs machines de votre réseau pour donner à toutes le même ensemble de paramètres d’atténuation des risques.
 
  Vous pouvez aussi convertir et importer un fichier XML de configuration EMET existant en un fichier XML de configuration de protection contre le code malveillant.

- **Bloquer le remplacement de la protection contre le code malveillant**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) : définissez la valeur sur *Oui* pour empêcher les utilisateurs d’apporter des modifications à la zone de paramètres de protection contre le code malveillant dans le centre de sécurité Windows Defender. Si vous désactivez ou ne configurez pas ce paramètre, les utilisateurs locaux peuvent apporter des modifications dans la zone de paramètres de protection contre le code malveillant.  
  **Par défaut** : oui  

- **Accès contrôlé aux dossiers**  
  Consultez [Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications) et [Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders) 
  
   Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.

  **Par défaut** : mode audit

## <a name="web--network-protection"></a>Protection réseau et Web  

- **Type de protection réseau**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) : cette stratégie vous permet d’activer la protection réseau (bloquer/auditer) ou de la désactiver dans Windows Defender Exploit Guard.This policy allows you to turn network protection on or off in Windows Defender Exploit Guard. La protection réseau est une fonctionnalité de Windows Defender Exploit Guard qui protège les employés utilisant une application d’accéder à des tentatives d’hameçonnage, à des sites hébergeant du code malveillant exploitant une faille de sécurité et à du contenu malveillant sur Internet. Cela inclut le fait d’empêcher des navigateurs tiers de se connecter à des sites dangereux.  

  Lorsque la valeur *Activer* ou *Mode audit* est définie, les utilisateurs ne peuvent pas désactiver la protection du réseau et vous pouvez utiliser le centre de sécurité Windows Defender pour afficher des informations sur les tentatives de connexion.  
 
  - *Activer* empêchera les utilisateurs et applications de se connecter à des domaines dangereux.  
  - *Mode audit* n’empêche pas les utilisateurs et applications de se connecter à des domaines dangereux.  

  Lorsque la valeur *Défini par l’utilisateur* est activée, les utilisateurs et les applications peuvent se connecter à des domaines dangereux et informations sur les connexions n’est pas disponibles dans le centre de la sécurité Windows Defender.  

  **Par défaut** : mode audit

- **Exiger SmartScreen pour Microsoft Edge**  
  [Navigateur/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) : Microsoft Edge utilise Windows Defender SmartScreen (activé) pour protéger les utilisateurs contre d’éventuels courriers indésirables d’hameçonnage et logiciels malveillants par défaut. Par défaut, cette stratégie est activée (valeur définie sur *Oui*) et empêche les utilisateurs de désactiver Windows Defender SmartScreen.  Lorsque la stratégie effective pour un appareil est égale à Non configuré, les utilisateurs peuvent désactiver Windows Defender SmartScreen, ce qui laisse l’appareil non protégé.  

  **Par défaut** : oui
  
- **Bloquer l’accès aux sites malveillants**  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) : Par défaut, Microsoft Edge permet aux utilisateurs de contourner (ignorer) les avertissements de Windows Defender SmartScreen relatifs aux sites potentiellement malveillants, leur permettant ainsi d’accéder au site. Avec cette stratégie activée (définie sur *Oui*), Microsoft Edge empêche les utilisateurs de contourner les avertissements, les empêchant ainsi d’accéder au site.  

  **Par défaut** : oui

- **Bloquer le téléchargement des fichiers non vérifiés**  
  [Navigateur/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) : par défaut, Microsoft Edge permet aux utilisateurs de contourner (ignorer) les avertissements de Windows Defender SmartScreen relatifs aux fichiers potentiellement malveillants, leur permettant ainsi de continuer à télécharger les fichiers non vérifiés. Avec cette stratégie est activée (définie sur *Oui*), les utilisateurs ne peuvent pas contourner les avertissements et ne peut pas télécharger des fichiers non vérifiés.  

  **Par défaut** : oui

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>Antivirus Windows Defender [vérifier les paramètres en attente pour cette section]

Pour plus d’informations, consultez [Fournisseur de services de configuration de stratégie - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) dans la documentation Windows.

- **Analyser les scripts chargés dans les navigateurs web Microsoft**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) : définissez la valeur sur *Oui* pour autoriser les fonctionnalités d’analyse de scripts de Windows Defender.  

  **Par défaut** : oui

- **Analyser les e-mails entrants**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) : la valeur définie sur *Oui* pour autoriser Windows Defender à analyser les emails.  

  **Par défaut** : oui

- **Type de consentement pour l’envoi d’exemples par Defender**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) : Vérifie le niveau de consentement de l’utilisateur dans Windows Defender pour envoyer des données. Si le consentement nécessaire a déjà été accordé, Windows Defender les envoie. Si ce n’est pas le cas (et si l’utilisateur a spécifié de ne jamais lui demander), l’interface utilisateur est lancée pour demander le consentement de l’utilisateur (quand *Protection assurée par la cloud* est définie sur *Oui*) avant l’envoi des données.  

  **Par défaut** : Envoyer automatiquement des échantillons sécurisés

- **Système NIS (Network Inspection System)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) : bloquez tout trafic malveillant détecté par des signatures dans le système NIS (Network Inspection System).  
 
  **Par défaut** : oui

- **Intervalle de mise à jour des signatures (en heures)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) : indiquez en heures, la fréquence à laquelle l’appareil recherche de nouvelles mises à jour de signature Defender.  
 
  **Par défaut** : 4

- **Configurer une faible priorité de l’UC pour des analyses planifiées**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) : lorsque la valeur est définie sur *Oui*, la priorité d’analyse de l’UC est définie sur faible. Lorsque *Non configuré* est activé, aucune modification n’est apportée à la priorité de l’UC pour les analyses planifiées.  

    **Par défaut** : oui

- **Bloc Defender sur la protection d’accès**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) : lorsque la valeur est définie sur *Oui*, Windows Defender - Protection de l'accès est activé.  

  **Par défaut** : oui

- **Type d’analyse système à effectuer**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) : type d’analyse Defender.  

  **Par défaut** : analyse rapide

- **Analyser tous les téléchargements**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) : lorsque la valeur est définie sur *Oui*, Defender analyse tous les fichiers téléchargés et les pièces jointes.  

  **Par défaut** : oui

- **Nombre de jours avant la suppression des programmes malveillants en quarantaine**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) : spécifiez le nombre de jours pour conserver les éléments en quarantaine sur le système avant qu’ils ne soient automatiquement supprimés. Lorsque cette valeur est définie sur zéro, les éléments en quarantaine ne sont jamais supprimés automatiquement.  

  **Par défaut** : 0

- **Heure de début d’analyse planifiée**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) : programmez une heure dans la journée pour l’analyse des périphériques par Defender. 
  
  Option connexe dans la liste : *Defender/ScheduleScanDay*   

  **Par défaut** : 2h00

- **Protection assurée par le cloud**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) : lorsque la valeur est définie sur *Oui*, Windows Defender envoie des informations à Microsoft sur les problèmes détectés. Microsoft analyse ces informations, en apprend plus sur les problèmes qui vous affectent ainsi que d’autres clients, et offre des solutions améliorées.

  Quand cette stratégie est définie sur *Oui*, vous pouvez utiliser *Exemple de type de consentement de soumission Defender* pour permettre aux utilisateurs de contrôler l’envoi d’informations à partir de leur appareil.  

  **Par défaut** : oui

- **Defender : action contre les applications potentiellement indésirables**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) : l’antivirus Windows Defender peut identifier et bloquer le téléchargement et l’installation des *applications potentiellement indésirables* (PUA) sur les points de terminaison de votre réseau. 
 
  - Lorsque la valeur est définie sur *Bloc*, Windows Defender bloque les PUA et les répertorie dans l’historique, ainsi que d’autres menaces.
  - Lorsque la valeur est définie sur *Audit*, Windows Defender détecte les PUA, mais ne les bloque pas. Vous trouverez des informations sur les applications sur lesquelles Windows Defender aurait dû agir en recherchant des événements qui ont été créés par Windows Defender dans l’observateur d'événements.  
  - Lorsque la valeur est définie sur *Valeurs par défaut du périphérique*, la protection contre les PUA est désactivée.  
 
  **Par défaut** : bloc

- **Délai d'expiration étendu de Cloud Defender**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) : spécifiez la durée maximale avant que Antivirus Windows Defender ne bloque un fichier lors de l’attente d’un résultat venu du cloud. Le temps d’attente de base de Windows Defender est de 10 secondes. Tout temps supplémentaire que vous spécifiez ici (jusqu'à 50 secondes) est ajouté à ces 10 secondes. Dans la plupart des cas, l’analyse prend beaucoup moins de temps que la valeur maximale. Prolonger la durée permet au cloud de rechercher des fichiers suspects de manière plus approfondie.  

  Par défaut la valeur de temps développée est 0 (désactivé). Intune recommande d’activer ce paramètre et de spécifier au moins 20 secondes supplémentaires.  
 
  **Par défaut** : 0

- **Analyser les fichiers d’archive**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) : définissez la valeur sur *Oui*  pour que Windows Defender analyse les fichiers d’archive.  

  **Par défaut** : oui

- **Planification d’analyse système de Defender**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) : planifiez quel jour Defender analyse les appareils. 
 
  Options connexes dans la liste : *Defender/ScheduleScanTime*

  **Par défaut** : défini par l’utilisateur

- **Surveillance du comportement**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) : définissez la valeur sur *Oui* pour activer la fonctionnalité analyse du comportement de Windows Defender. Intégré dans Windows 10, les capteurs d’analyse du comportement de Windows Defender collectent et traitent les signaux comportementaux du système d’exploitation et envoient ces données de capteur à votre instance cloud, isolée et privée de Windows Defender ATP.  

  **Par défaut** : oui

- **Analyser les fichiers ouverts à partir de dossiers réseau**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) : définissez la valeur sur *Oui* pour que Windows Defender analyse les fichiers sur le réseau. L’utilisateur ne peut pas supprimer les programmes malveillants détectés à partir des fichiers en lecture seule.  

  **Par défaut** : oui

- **Defender : Niveau de blocage cloud**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) : utilisez cette stratégie pour déterminer le degré d’agressivité de l’Antivirus Windows Defender dans le blocage et l’analyse des fichiers suspects. Les options sont les suivantes :

  - Élevé : bloque de façon agressive les fichiers inconnus tout en optimisant les performances du client (probabilité plus grande de faux positifs)
  - Plus élevé : bloque de façon agressive les fichiers inconnus et applique des mesures de protection supplémentaires (peut affecter les performances du client)
  - Tolérance zéro - bloque tous les exécutables inconnus

  **Par défaut** : non configuré

- **Surveillance en temps réel**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)  définissez la valeur sur *Oui* pour permettre l’analyse de Windows Defender en temps réel.  

  **Par défaut** : oui

- **Limite de l’utilisation de l’UC pendant une analyse**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) : spécifiez le pourcentage moyen maximum de l’UC que Windows Defender peut utiliser lors d’une analyse.  

  **Par défaut** : 50

- **Analyser les lecteurs réseau mappés lors d’une analyse complète**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) : définissez la valeur sur *Oui* pour que Windows Defender analyse les fichiers sur le réseau. L’utilisateur ne peut pas supprimer les programmes malveillants détectés à partir des fichiers en lecture seule,

  Paramètre connexe dans cette liste : *Defender/AllowScanningNetworkFiles*

  **Par défaut** : oui

- **Bloquer l’accès de l’utilisateur final à Defender**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) : définissez la valeur sur *Oui* pour bloquer l’accès des utilisateurs finaux à l’interface utilisateur de Windows Defender sur leur appareil.  

  **Par défaut** : oui

- **Heure de début de l’analyse rapide**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) : planifiez une heure pour l’exécution d’une analyse rapide par Defender.  

  **Par défaut** : 2h00

## <a name="windows-defender-firewall"></a>Pare-feu Windows Defender
Pour plus d’informations, consultez [Pare-feu CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) dans la documentation de Windows.

- **Durée d’inactivité des associations de sécurité avant suppression** - *MdmStore/Global/SaIdleTime*   
  Les associations de sécurité sont supprimées si aucun trafic réseau n’est détecté pendant ce nombre de secondes.  
  **Par défaut** : 300

- **Protocole de transfert de fichiers** - *MdmStore/Global/DisableStatefulFtp*   
  Bloque le protocole FTP avec état.  
  **Par défaut** : oui

- **Mise en file d’attente de paquets** - *MdmStore/Global/EnablePacketQueue*    
  Spécifiez comment la mise à l’échelle des logiciels côté réception est activée pour la réception chiffrée et efface le texte pour le scénario de passerelle du tunnel IPsec. Cela garantit la préservation de l’ordre des paquets.  
  **Par défaut** : valeurs par défaut de l’appareil

- **Domaine de profil de pare-feu** - *FirewallRules/FirewallRuleName/profils*  
  Spécifie les profils auxquels appartient la règle : domaine, privé, public. Cette valeur représente le profil des réseaux qui sont connectés à des domaines.  

  Paramètres disponibles :  
  - **Réponses en monodiffusion au trafic en multidiffusion requis**  
    **Par défaut** : oui

  - **Fusion des règles d’application autorisée à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Notifications entrantes bloquées**  
    **Par défaut** : oui

  - **Fusion des règles de port global à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Mode furtif bloqué**  
    **Par défaut** : oui

  - **Pare-feu activé**  
    **Par défaut** : autorisé

  - **Non fusion des règles de sécurité de connexion à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Non fusion des règles de stratégie à partir de la stratégie de groupe**  
    **Par défaut** : oui

- **Profil de pare-feu public** - *FirewallRules/FirewallRuleName/Profiles*  
  Spécifie les profils auxquels appartient la règle : domaine, privé, public. Cette valeur représente le profil des réseaux publics. Ces réseaux sont classés publics par les administrateurs dans l’hôte du serveur. La classification se produit dès que l’hôte se connecte au réseau. Ces réseaux est généralement dans les aéroports, cafés-restaurants et autres lieux publics, où les pairs dans le réseau ou l’administrateur réseau ne sont pas approuvés.  

  Paramètres disponibles :

  - **Connexions entrantes bloquées**  
    **Par défaut** : oui 

  - **Réponses en monodiffusion au trafic en multidiffusion requis**  
    **Par défaut** : oui  

  - **Mode furtif requis**  
    **Par défaut** : oui 
 
  - **Connexions sortantes requises**  
    **Par défaut** : oui  

  - **Fusion des règles d’application autorisée à partir de la stratégie de groupe**  
    **Par défaut** : oui  

  - **Notifications entrantes bloquées**  
    **Par défaut** : oui  

  - **Fusion des règles de port global à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Mode furtif bloqué**  
    **Par défaut** : oui

  - **Pare-feu activé**  
    **Par défaut** : autorisé  

  - **Non fusion des règles de sécurité de connexion à partir de la stratégie de groupe**  
    **Par défaut** : oui  

  - **Trafic entrant requis**  
    **Par défaut** : oui

  - **Non fusion des règles de stratégie à partir de la stratégie de groupe**  
    **Par défaut** : oui  

- **Profil de pare-feu privé** - *FirewallRules/FirewallRuleName/Profiles*  
  Spécifie les profils auxquels appartient la règle : domaine, privé, public. Cette valeur représente le profil des réseaux privés.  

  Paramètres disponibles : 

  - **Connexions entrantes bloquées**  
    **Par défaut** : oui

  - **Réponses en monodiffusion au trafic en multidiffusion requis**  
    **Par défaut** : oui

  - **Mode furtif requis**  
    **Par défaut** : oui

  - **Connexions sortantes requises**  
    **Par défaut** : oui

  - **Notifications entrantes bloquées**  
    **Par défaut** : oui

  - **Fusion des règles de port global à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Mode furtif bloqué**  
    **Par défaut** : oui  

  - **Pare-feu activé**  
    **Par défaut** : autorisé

  - **Non fusion des règles d’application autorisée à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Non fusion des règles de sécurité de connexion à partir de la stratégie de groupe**  
    **Par défaut** : oui

  - **Trafic entrant requis**  
    **Par défaut** : oui

  - **Non fusion des règles de stratégie à partir de la stratégie de groupe**  
    **Par défaut** : oui  

- **Méthode de codage de clés pré-partagées du pare-feu**  
  **Par défaut** : UTF-8

- **Vérification de la liste de révocation de certificats**  
  **Par défaut** : valeurs par défaut de l’appareil

## <a name="windows-hello-for-business"></a>Windows Hello Entreprise  

Pour plus d’informations, consultez [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp) dans la documentation de Windows.

- **Configurer Windows Hello Entreprise** - *TenantId/stratégies/UsePassportForWork*    
  Windows Hello Entreprise est une méthode alternative de connexion à Windows en remplaçant les mots de passe, les cartes à puce et les cartes à puce virtuelles.  

  - Lorsque la valeur est *Oui*, vous activez cette stratégie et l’appareil provisionne Windows Hello entreprise.  
  - Lorsque la valeur *n’est pas configurée*, la ligne de base n’affecte pas le paramètre de stratégie de l’appareil. Cela signifie que si Windows Hello entreprise est désactivé sur un appareil, il reste désactivé. Si elle est activée, elle reste activée. 

  Vous ne pouvez pas désactiver Windows Hello entreprise par le biais de cette ligne de base. Vous pouvez désactiver Windows Hello entreprise lors de la configuration de l' [inscription Windows](windows-hello.md)ou dans le cadre d’un profil de configuration d’appareil pour la [protection d’identité](identity-protection-configure.md).  

Windows Hello Entreprise est une méthode alternative de connexion à Windows en remplaçant les mots de passe, les cartes à puce et les cartes à puce virtuelles.  

  Si vous activez ou ne configurez pas ce paramètre de stratégie, l’appareil configure Windows Hello Entreprise. Si vous désactivez ce paramètre de stratégie, l’appareil ne configure pas Windows Hello Entreprise pour tous les utilisateurs.

  Intune ne prend pas en charge la désactivation de Windows Hello. Au lieu de cela, vous pouvez configurer la stratégie pour activer Windows Hello Entreprise (Oui) ou ne pas configurer Windows Hello directement (non configuré). Lorsqu’il n’est pas configuré, un appareil peut recevoir la configuration via une autre stratégie, ce qui peut activer ou désactiver cette fonctionnalité.  

  **Par défaut** : oui  

- **Exiger des lettres en minuscules dans le code PIN** - *TenantId/stratégies/PINComplexity/LowercaseLetters*  
  **Par défaut** : autorisé  

- **Exiger des caractères spéciaux dans le code PIN** - *TenantId/Policies/PINComplexity/SpecialCharacters*  
  **Par défaut** : autorisé  

- **Exiger des lettres en majuscules dans le code PIN** - *TenantId/Policies/PINComplexity/UppercaseLetters*   
  **Par défaut** : autorisé  

