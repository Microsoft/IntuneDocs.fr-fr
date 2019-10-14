---
title: Paramètres de protection pour appareils Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Sur les appareils Windows 10, utilisez ou configurez les paramètres Endpoint Protection pour activer les fonctionnalités de Windows Defender, notamment Application Guard, Pare-feu, SmartScreen, le chiffrement et BitLocker, Exploit Guard, Contrôle d’application, Centre de sécurité, ainsi que la sécurité sur les appareils locaux dans Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/08/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: karthig
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22e3779cd0772753ccd8843cd1f1ff38617298d6
ms.sourcegitcommit: 884654da8e72a63bfaea6b5def6c7891b065f251
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163578"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Paramètres Windows 10 (et versions ultérieures) pour protéger les appareils à l’aide d’Intune  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]  

Microsoft Intune comprend de nombreux paramètres permettant de protéger vos appareils. Cet article décrit tous les paramètres que vous pouvez activer et configurer dans les appareils Windows 10 et ultérieurs. Ces paramètres sont créés dans un profil de configuration de protection des points de terminaison dans Intune pour contrôler la sécurité, notamment BitLocker et Windows Defender.  

Pour configurer l’antivirus Windows Defender, consultez [Restrictions relatives aux appareils Windows 10](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).  

## <a name="before-you-begin"></a>Avant de commencer  

[Créez un profil de configuration de protection des points de terminaison](endpoint-protection-configure.md).  

Pour plus d’informations sur les fournisseurs de services de configuration (CSP), consultez [Référence du fournisseur de services de configuration](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).  

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard  

Lors de l’utilisation de Microsoft Edge, Windows Defender Application Guard protège votre environnement des sites qui ne sont pas approuvés par votre organisation. Quand des utilisateurs visitent des sites qui ne figurent pas dans la liste des limites de votre réseau isolé, les sites s’ouvrent dans une session de navigation virtuelle Hyper-V. Les sites approuvés, qui sont configurés dans Configuration de l’appareil, sont définis par une limite réseau.  

Application Guard est uniquement disponible pour les appareils Windows 10 (64 bits). L’utilisation de ce profil permet d’installer un composant Win32 pour activer Application Guard.  

- **Application Guard**  
  **Par défaut** : Non configuré  
   CSP application Guard : [paramètres/AllowWindowsDefenderApplicationGuard](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#allowwindowsdefenderapplicationguard)  

  - **Activer pour Edge** : active cette fonctionnalité pour ouvrir des sites non approuvés dans un conteneur de navigation virtualisé Hyper-V.  
  - **Non configuré** : tout site (approuvé et non approuvé) peut être ouvert sur l’appareil.  

- **Comportement du Presse-papiers**  
  **Par défaut** : Non configuré  
   CSP application Guard : [paramètres/ClipboardSettings](https://go.microsoft.com/fwlink/?linkid=872351)  

  Choisissez les actions de copier-coller autorisées entre le PC local et le navigateur virtuel Application Guard.  
  - **Non configuré**  
  - **Autoriser le copier-coller du PC vers le navigateur uniquement**  
  - **Autoriser le copier-coller à partir du navigateur sur le PC uniquement**  
  - **Autoriser le copier-coller entre le PC et le navigateur**  
  - **Bloquer le copier-coller entre le PC et le navigateur**  

- **Contenu du presse-papiers**  
  Ce paramètre est disponible uniquement lorsque le *comportement du presse-papiers* est défini sur l’un des paramètres d' *autorisation* .  
  **Par défaut** : Non configuré  
  CSP application Guard : [paramètres/ClipboardFileType](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp#clipboardfiletype)  

  Sélectionnez le contenu autorisé du presse-papiers.  
  - **Non configuré**  
  - **Text**  
  - **Images**  
  - **Texte et images**  

- **Contenu externe sur les sites de l’entreprise**  
  **Par défaut** : Non configuré  
  CSP application Guard : [paramètres/BlockNonEnterpriseContent](https://go.microsoft.com/fwlink/?linkid=872352)  

  - **Bloquer** : bloquer le chargement du contenu des sites web non approuvés.  
  - **Non configuré** : les sites autres que les sites d’entreprise peuvent s’ouvrir sur l’appareil.  
 
- **Imprimer à partir du navigateur virtuel**  
  **Par défaut** : Non configuré  
  CSP application Guard : [paramètres/PrintingSettings](https://go.microsoft.com/fwlink/?linkid=872354)  

  - **Autoriser** : autorise l’impression du contenu sélectionné à partir du navigateur virtuel.  
  - **Non configuré** Désactivez toutes les fonctionnalités d’impression.  

  Lorsque vous *autorisez* l’impression, vous pouvez configurer le paramètre suivant :
  - **Type (s) d’impression** Sélectionnez une ou plusieurs des options suivantes :  
    - PDF  
    - XPS  
    - Imprimantes locales
    - Imprimantes réseau  

- **Collecter les journaux**  
  **Par défaut** : Non configuré  
  CSP application Guard : [audit/AuditApplicationGuard](https://go.microsoft.com/fwlink/?linkid=872418)  

  - **Autoriser** : collecter les journaux des événements qui se produisent dans une session de navigation Application Guard.  
  - **Non configuré** : ne collecter aucun journal dans la session de navigation.  

- **Conserver les données du navigateur générées par l’utilisateur**  
  **Par défaut** : Non configuré  
  CSP application Guard : [paramètres/AllowPersistence](https://go.microsoft.com/fwlink/?linkid=872419)  

  - **Autoriser** : enregistrer les données utilisateur (comme les mots de passe, les favoris et les cookies) qui sont créées au cours d’une session de navigation virtuelle Application Guard.  
  - **Non configuré** : ignorer les données et les fichiers téléchargés par l’utilisateur lors du redémarrage de l’appareil ou quand un utilisateur se déconnecte.  

- **Accélération graphique**  
 **Par défaut** : Non configuré  
  CSP application Guard : [paramètres/AllowVirtualGPU](https://go.microsoft.com/fwlink/?linkid=872420)  
      
  - **Activer** : charger des sites web utilisant beaucoup de graphiques et aux performances vidéo plus rapides en obtenant l’accès à une unité de traitement graphique virtuelle.  
  - **Non configuré** Utilisez l’UC de l’appareil pour les graphiques ; N’utilisez pas l’unité de traitement graphique virtuelle.  

- **Télécharger des fichiers sur le système de fichiers hôte**  
  **Par défaut** : Non configuré  
  CSP application Guard : [paramètres/SaveFilesToHost](https://go.microsoft.com/fwlink/?linkid=872421)  

  - **Activer** : les utilisateurs peuvent télécharger des fichiers à partir du navigateur virtualisé sur le système d’exploitation hôte.  
  - **Non configuré** : conserve les fichiers en local sur l’appareil et n’en télécharge pas sur le système de fichiers hôte.  

## <a name="windows-defender-firewall"></a>Pare-feu Windows Defender  
 
### <a name="global-settings"></a>Paramètres globaux  

Ces paramètres s’appliquent à tous les types de réseaux.  

- **Protocole FTP**  
  **Par défaut** : Non configuré  
   Fournisseur CSP de pare-feu : [MdmStore/global/DisableStatefulFtp](https://go.microsoft.com/fwlink/?linkid=872536)  

  - **Bloquer** : désactiver le protocole FTP avec état.  
  - **Non configuré** : le pare-feu effectue un filtrage FTP avec état pour autoriser les connexions secondaires.  

- **Durée d’inactivité des associations de sécurité avant suppression**  
  **Par défaut** : *non configuré*  
   Fournisseur CSP de pare-feu : [MdmStore/global/SaIdleTime](https://go.microsoft.com/fwlink/?linkid=872539)  

   Spécifiez une durée d’inactivité en secondes, après laquelle les associations de sécurité sont supprimées.   

- **Codage des clés prépartagées**  
  **Par défaut** : Non configuré  
   Fournisseur CSP de pare-feu : [MdmStore/global/PresharedKeyEncoding](https://go.microsoft.com/fwlink/?linkid=872541)  

   - **Activer** -encoder les clés prédéfinies en UTF-8.  
   - **Non configuré** : encodez les clés prédéfinies à l’aide de la valeur du magasin local.  

- **Exemptions IPsec**  
  **Valeur par défaut**: *0 sélectionné*  
   Fournisseur CSP de pare-feu : [MdmStore/global/IPsecExempt](https://go.microsoft.com/fwlink/?linkid=872547)

   Sélectionnez un ou plusieurs des types de trafic suivants à exempter d’IPsec :  
   - **Codes type ICMP IPv6 de découverte de voisin**  
   - **ICMP**  
   - **Codes type ICMP IPv6 de découverte de routeur**  
   - **Trafic réseau DHCP IPv4 et IPv6**  

- **Vérification de la liste de révocation de certificats**  
  **Par défaut** : Non configuré  
  Fournisseur CSP de pare-feu : [MdmStore/global/CRLcheck](https://go.microsoft.com/fwlink/?linkid=872548)  

  choisissez la façon dont l’appareil vérifie la liste de révocation de certificats. Les options disponibles sont les suivantes :  
  - **Désactiver la vérification de la liste de révocation**  
  - **Échec de la vérification de la liste de révocation de certificats sur le certificat révoqué uniquement**  
  - **Échec de la vérification de la liste de révocation de certificats en cas d’erreur**.  
 

- **Associer le jeu d’authentification de façon opportuniste par module de génération de clés**  
  **Par défaut** : Non configuré  
  Fournisseur CSP de pare-feu : [MdmStore/global/OpportunisticallyMatchAuthSetPerKM](https://go.microsoft.com/fwlink/?linkid=872550)  
  
  - **Activer** : les modules de génération de clés doivent ignorer uniquement les suites d’authentification qu’ils ne prennent pas en charge.  
  - **Non configuré** : les modules de génération de clés doivent ignorer la totalité du jeu d’authentification s’ils ne prennent pas en charge toutes les suites de l’authentification spécifiées dans le jeu.  


- **Mise en file d’attente des paquets**  
  **Par défaut** : Non configuré  
  Fournisseur CSP de pare-feu : [MdmStore/global/EnablePacketQueue](https://go.microsoft.com/fwlink/?linkid=872551)  

  Spécifiez comment la mise à l’échelle des logiciels côté réception est activée pour la réception chiffrée et efface le texte pour le scénario de passerelle du tunnel IPsec. Ce paramètre confirme la préservation de l’ordre des paquets. Les options disponibles sont les suivantes :  
  - **Non configuré**  
  - **Désactiver tous les paquets de mise en file d’attente**  
  - **Mise en file d’attente des paquets chiffrés entrants uniquement**  
  - **Les paquets de file d’attente après le déchiffrement sont exécutés pour le transfert uniquement**  
  - **Configurer les paquets entrants et sortants**  

### <a name="network-settings"></a>Paramètres du réseau  

Les paramètres suivants sont répertoriés dans cet article une seule fois, mais tous s’appliquent aux trois types de réseau spécifiques :  
- **Réseau de domaine (espace de travail)**  
- **Réseau privé (détectable)**  
- **Réseau public (non détectable)**  

#### <a name="general-settings"></a>Paramètres généraux :  

- **Pare-feu Windows Defender**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [EnableFirewall](https://go.microsoft.com/fwlink/?linkid=872558)  
  
  - **Activer** : activer le pare-feu et les fonctions de sécurité avancées. 
  - **Non configuré** : autorise tout le trafic réseau, quels que soient les autres paramètres de stratégie.  

- **Mode furtif**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [DisableStealthMode](https://go.microsoft.com/fwlink/?linkid=872559)  
  - **Non configuré**  
  - **Bloc** : le pare-feu est bloqué de fonctionner en mode furtif. Le blocage du mode furtif vous permet de bloquer également **Exemption de paquets sécurisés IPsec**.  
  - **Autoriser** : le pare-feu fonctionne en mode furtif, ce qui permet d’empêcher les réponses à la détection des requêtes.  

- **Exemption de paquets sécurisés IPsec avec le mode furtif**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [DisableStealthModeIpsecSecuredPacketExemption](https://go.microsoft.com/fwlink/?linkid=872560)  

  Cette option est ignorée si le *mode furtif* est défini sur *bloquer*.  

  - **Non configuré**  
  - **Bloquer** : les paquets sécurisés IPSec ne reçoivent pas d’exemptions.  
  - **Autoriser : autorise** les exemptions. Le mode furtif du pare-feu ne doit pas empêcher l’ordinateur hôte de répondre au trafic réseau non sollicité qui est sécurisé par IPsec.  

- **Protégé**  
  **Par défaut** : Non configuré  
  CSP pare-feu : [protégé](https://go.microsoft.com/fwlink/?linkid=872561)  
    - **Non configuré**  
    - **Bloquer** : lorsque le pare-feu Windows Defender est activé et que ce paramètre est défini sur *bloquer*, tout le trafic entrant est bloqué, quels que soient les autres paramètres de stratégie. 
    - **Allow** -lorsque la valeur est *allow*, ce paramètre est désactivé et le trafic entrant est autorisé en fonction d’autres paramètres de stratégie.

- **Réponses en monodiffusion au trafic en multidiffusion**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [DisableUnicastResponsesToMulticastBroadcast](https://go.microsoft.com/fwlink/?linkid=872562)  
  
  En règle générale, vous ne souhaitez pas recevoir des réponses en monodiffusion à des messages de multidiffusion ou de diffusion. Ces réponses peuvent indiquer une attaque par déni de service ou un attaquant qui tente de sonder un ordinateur actif connu.  
  - **Non configuré**  
  - **Bloquer** : désactive les réponses en monodiffusion au trafic en multidiffusion.  
  - **Autoriser** : autoriser les réponses en monodiffusion au trafic en multidiffusion.  

- **Notifications entrantes**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [DisableInboundNotifications](https://go.microsoft.com/fwlink/?linkid=8725630)  

  - **Non configuré**  
  - **Bloquer** -masquer les notifications à utiliser lorsqu’une application est bloquée de l’écoute sur un port.  
  - **Autoriser**  : active ce paramètre et peut afficher une notification aux utilisateurs lors du blocage d’une application pour écouter sur un port.  

- **Action par défaut pour les connexions sortantes**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [DefaultOutboundAction](https://aka.ms/intune-firewall-outboundaction)  
  
  Configurez le pare-feu des actions par défaut sur les connexions sortantes. Ce paramètre sera appliqué à Windows version 1809 et versions ultérieures.  

  - **Non configuré**  
  - **Bloquer** : l’action de pare-feu par défaut n’est pas exécutée sur le trafic sortant, sauf si elle est explicitement spécifiée pour ne pas bloquer.  
  - **Autoriser** : les actions de pare-feu par défaut s’exécutent sur les connexions sortantes.  

- **Action par défaut pour les connexions entrantes**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [DefaultInboundAction](https://go.microsoft.com/fwlink/?linkid=872564)  
 
  - **Non configuré**  
  - **Bloquer** : l’action de pare-feu par défaut n’est pas exécutée sur les connexions entrantes.  
  - **Autoriser** : les actions de pare-feu par défaut s’exécutent sur les connexions entrantes.  

#### <a name="rule-merging"></a>Fusion des règles  

- **Règles de pare-feu Windows Defender d’application autorisées du magasin local**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [AuthAppsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872565)  

  - **Non configuré**  
  - **Bloquer** : les règles de pare-feu d’applications autorisées du magasin local sont ignorées et non appliquées.  
  - **Autoriser** : -
   choisissez **Activer** pour appliquer des règles de pare-feu du magasin local afin qu’elles soient reconnues et appliquées.  

- **Règles de pare-feu Windows Defender de port globales du magasin local**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [GlobalPortsAllowUserPrefMerge](https://go.microsoft.com/fwlink/?linkid=872566)  

  - **Non configuré**  
  - **Bloquer** : les règles de pare-feu de port globales dans le magasin local sont ignorées et ne sont pas appliquées.  
  - **Autoriser** : appliquer des règles de pare-feu de port globales du magasin local à reconnaître et à appliquer.  

- **Règles du pare-feu Windows Defender du magasin local**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [AllowLocalPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872567)  

  - **Non configuré**  
  - **Bloquer** : les règles de pare-feu du magasin local sont ignorées et ne sont pas appliquées.
  - **Autoriser** : appliquer les règles de pare-feu du magasin local à reconnaître et à appliquer.  

- **Règles IPsec du magasin local**  
  **Par défaut** : Non configuré  
  CSP du pare-feu : [AllowLocalIpsecPolicyMerge](https://go.microsoft.com/fwlink/?linkid=872568)  

  - **Non configuré**  
  - **Bloquer**  : les règles de sécurité de connexion du magasin local sont ignorées et ne sont pas appliquées, quelles que soient la version du schéma et la version des règles de sécurité de connexion.  
  - **Autoriser** : appliquer les règles de sécurité de connexion du magasin local, quelles que soient les versions des règles de sécurité de connexion ou du schéma.  

### <a name="firewall-rules"></a>Règles de pare-feu  

Vous pouvez **Ajouter** une ou plusieurs règles de pare-feu personnalisées. Pour plus d’informations, consultez [Ajouter des règles de pare-feu personnalisées pour les appareils Windows 10](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices).  

Les règles de pare-feu personnalisées prennent en charge les options suivantes :  

#### <a name="general-settings"></a>Paramètres généraux :  

- **Nom**  
  **Valeur par défaut**: *aucun nom*  

  Spécifiez un nom convivial pour votre règle. Ce nom apparaîtra dans la liste des règles pour vous aider à l’identifier.  

- **Description**  
  **Valeur par défaut**: *aucune description*  

  Fournissez une description de la règle.  

- **Sens**   
  **Par défaut** : Non configuré  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/direction](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#direction)  
  
  Spécifie si cette règle s' **applique au trafic entrant ou** **sortant** . Si la valeur **n’est pas configurée**, la règle s’applique automatiquement au trafic sortant.  

- **Action**  
  **Par défaut** : Non configuré  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/action](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#action)et [firewallrules/*FirewallRuleName*/action/type](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#type)  

  Sélectionnez dans **autoriser** ou **bloquer**. Quand la valeur est définie sur **non configuré**, la règle autorise par défaut le trafic.  

- **Type de réseau**  
  **Valeur par défaut**: 0 sélectionné  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/Profiles](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#profiles)  

  Sélectionnez jusqu’à trois types de réseau auxquels cette règle appartient. Les options incluent **domaine**, **privé**et **public**.  Si aucun type de réseau n’est sélectionné, la règle s’applique aux trois types de réseau.  

#### <a name="application-settings"></a>Paramètres d'application  

- **Application (s)**  
  **Valeur par défaut**: tous  

  Contrôler les connexions pour une application ou un programme. Sélectionnez l’une des options suivantes, puis terminez la configuration supplémentaire :  
  - **Nom** de la famille de packages : spécifiez un nom de famille de packages. Pour rechercher le nom de la famille de packages, utilisez la commande PowerShell **AppxPackage**.   
    Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/App/PackageFamilyName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#packagefamilyname)  
 
  - **Chemin de fichier** : vous devez spécifier un chemin d’accès de fichier à une application sur l’appareil client, qui peut être un chemin d’accès absolu ou un chemin d’accès relatif. Par exemple : C:\Windows\System\Notepad.exe ou%WINDIR%\Notepad.exe.  
    Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/App/FilePath](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#filepath)  

  - **Service Windows** : spécifiez le nom abrégé du service Windows s’il s’agit d’un service et non d’une application qui envoie ou reçoit le trafic. Pour rechercher le nom abrégé du service, utilisez la commande PowerShell **obtenir-service**.  
    Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/App/ServiceName](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#servicename)  

  - **Tout**: *aucune configuration supplémentaire n’est disponible*.  

#### <a name="ip-address-settings"></a>Paramètres d’adresse IP  

Spécifiez les adresses locales et distantes auxquelles cette règle s’applique.  

- **Adresses locales**    
  **Valeur par défaut**: toute adresse  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  

  Sélectionnez **n’importe quelle adresse** ou **adresse spécifiée**.  

  Lorsque vous utilisez l' *adresse spécifiée*, vous ajoutez une ou plusieurs adresses sous la forme d’une liste séparée par des virgules d’adresses locales qui sont couvertes par la règle. Les jetons valides sont les suivants :  
  - Utilisez un astérisque « * » pour *toute* adresse locale. Si vous utilisez un astérisque, il doit s’agir du seul jeton que vous utilisez.  
  - Pour spécifier un sous-réseau, utilisez le masque de sous-réseau ou la notation de préfixe réseau. Si ni un masque de sous-réseau ni un préfixe réseau ne sont spécifiés, le masque de sous-réseau est par défaut 255.255.255.255.  
  - Une adresse IPv6 valide.  
  - Une plage d’adresses IPv4 au format « Start Address-end Address » sans espaces inclus.  
  - Une plage d’adresses IPv6 au format « Start Address-end Address » sans espaces inclus.  

- **Adresses distantes**  
  **Valeur par défaut**: toute adresse  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/RemoteAddressRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteaddressranges)  
 
  Sélectionnez **n’importe quelle adresse** ou **adresse spécifiée**.  

  Lorsque vous utilisez l' *adresse spécifiée*, vous ajoutez une ou plusieurs adresses sous la forme d’une liste séparée par des virgules d’adresses distantes couvertes par la règle. Les jetons ne respectent pas la casse. Les jetons valides sont les suivants :  
  - Utilisez un astérisque « * » pour *toute* adresse distante. Si vous utilisez un astérisque, il doit s’agir du seul jeton que vous utilisez.  
  - "Defaultgateway"  
  - « DHCP »  
  - « DNS »  
  - « WINS »  
  - « Intranet » (pris en charge sur les versions Windows 1809 et ultérieures)  
  - « RmtIntranet » (pris en charge sur les versions Windows 1809 et ultérieures)  
  - « Internet » (pris en charge sur les versions Windows 1809 et ultérieures)  
  - « Ply2Renders » (pris en charge sur les versions Windows 1809 et ultérieures)  
  - « LocalSubnet » indique toute adresse locale sur le sous-réseau local.  
  - Pour spécifier un sous-réseau, utilisez le masque de sous-réseau ou la notation de préfixe réseau. Si ni un masque de sous-réseau ni un préfixe réseau ne sont spécifiés, le masque de sous-réseau est par défaut 255.255.255.255.  
  - Une adresse IPv6 valide.  
  - Une plage d’adresses IPv4 au format « Start Address-end Address » sans espaces inclus.  
  - Une plage d’adresses IPv6 au format « Start Address-end Address » sans espaces inclus.  

#### <a name="port-and-protocol-settings"></a>Paramètres de port et de protocole  
Spécifiez les ports locaux et distants auxquels cette règle s’applique.  

- **Protocole**  
  **Valeur par défaut**: any  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/Protocol](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#protocol)  
  Sélectionnez l’une des options suivantes et effectuez toutes les configurations requises :  
  - **Tout** : aucune configuration supplémentaire n’est disponible.  
  - **TCP** : configurez les ports locaux et distants. Les deux options prennent en charge tous les ports ou les ports spécifiés. Entrez les ports spécifiés à l’aide d’une liste séparée par des virgules.  
    - **Ports locaux** -CSP pare-feu : [firewallrules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Ports distants** -fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **UDP** : configurez les ports locaux et distants. Les deux options prennent en charge tous les ports ou les ports spécifiés. Entrez les ports spécifiés à l’aide d’une liste séparée par des virgules.  
    - **Ports locaux** -CSP pare-feu : [firewallrules/*FirewallRuleName*/LocalPortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#localportranges)  
    - **Ports distants** -fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/RemotePortRanges](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#remoteportranges)  
  - **Personnalisé** : spécifiez un numéro de **protocole** personnalisé compris entre 0 et 255.  

#### <a name="advanced-configuration"></a>Configuration avancée  
- **Types d'interface**  
  **Valeur par défaut**: 0 sélectionné  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/InterfaceTypes](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp#interfacetypes)  

  Sélectionnez l'une des options suivantes :  
  - **Accès à distance**  
  - **Sans fil**  
  - **Réseau local**  

- **Autoriser uniquement les connexions à partir de ces utilisateurs**  
  **Valeur par défaut**: tous les utilisateurs *(toutes les valeurs par défaut sont utilisées quand aucune liste n’est spécifiée)*  
  Fournisseur CSP de pare-feu : [firewallrules/*FirewallRuleName*/LocalUserAuthorizationList](https://aka.ms/intunefirewallauthorizedusers)  

  Spécifiez une liste d’utilisateurs locaux autorisés pour cette règle. Une liste d’utilisateurs autorisés ne peut pas être spécifiée si cette règle s’applique à un service Windows.  


## <a name="windows-defender-smartscreen-settings"></a>Paramètres Windows Defender SmartScreen  
 
Microsoft Edge doit être installé sur l’appareil.  

- **SmartScreen pour les applications et les fichiers**  
  **Par défaut** : Non configuré  
   CSP SmartScreen : [SmartScreen/EnableSmartScreenInShell](https://go.microsoft.com/fwlink/?linkid=872784)  

  - **Non configuré** : désactive l’utilisation de SmartScreen.  
  - **Activer** : activer Windows SmartScreen pour l’exécution de fichiers et d’applications. SmartScreen est un composant cloud anti-hameçonnage et anti-programme malveillant.  

- **Exécution de fichiers non vérifiés**  
  **Par défaut** : Non configuré  
   CSP SmartScreen : [SmartScreen/PreventOverrideForFilesInShell](https://go.microsoft.com/fwlink/?linkid=872783)

  - **Non configuré** : désactive cette fonctionnalité et permet aux utilisateurs finaux d’exécuter des fichiers qui n’ont pas été vérifiés.  
  - **Bloquer** : empêcher les utilisateurs finaux d’exécuter des fichiers qui n’ont pas été vérifiés par Windows SmartScreen.  

## <a name="windows-encryption"></a>Chiffrement Windows  
 
### <a name="windows-settings"></a>Paramètres Windows  

Ces paramètres de chiffrement s’appliquent à toutes les versions de Windows 10.  

- **Chiffrer les appareils**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [RequireDeviceEncryption](https://go.microsoft.com/fwlink/?linkid=872523)  

  - **Exiger** : demander aux utilisateurs d’activer le chiffrement des appareils. En fonction de l’édition de Windows et de la configuration du système, les utilisateurs peuvent être invités à :  
    - Vérifier que le chiffrement d’un autre fournisseur n’est pas activé.  
    - Être amenés à désactiver le chiffrement de lecteur BitLocker, puis à réactiver BitLocker.  
  - **Non configuré**  
  
  Si le chiffrement Windows est activé alors qu’une autre méthode de chiffrement est active, l’appareil peut devenir instable.  

- **Chiffrer la carte de stockage (mobile uniquement)**  
  *Ce paramètre s’applique uniquement à Windows 10.*  
  **Par défaut** : Non configuré  
  CSP BitLocker : [RequireStorageCardEncryption](https://go.microsoft.com/fwlink/?linkid=872524)  

  - **Exiger** pour chiffrer toutes les cartes de stockage amovibles utilisées par l’appareil.  
  - **Non configuré** : n’exige pas le chiffrement des cartes de stockage et n’invite pas l’utilisateur à l’activer.  

### <a name="bitlocker-base-settings"></a>Paramètres de base BitLocker  

Les paramètres de base correspondent aux paramètres BitLocker universels pour tous les types de lecteurs de données. Ces paramètres permettent de gérer les options de configuration ou les tâches de chiffrement de lecteur modifiables par l’utilisateur final pour tous les types de lecteurs de données.  

- **Avertissement pour tout autre chiffrement de disque**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [AllowWarningForOtherDiskEncryption](https://go.microsoft.com/fwlink/?linkid=872525)  

  - **Bloquer** : désactiver l’invite d’avertissement si un autre service de chiffrement de disque se trouve sur l’appareil.  
  - **Non configuré** : autorisez l’affichage de l’avertissement pour le chiffrement d’un autre disque.  

  Quand vous définissez cette option sur *bloquer*, vous pouvez configurer le paramètre suivant :  

  - **Autoriser les utilisateurs standard à activer le chiffrement pendant une jonction Azure AD**  
    *Ce paramètre s’applique uniquement aux appareils Azure Active Directory joints (Azure ADJ), et dépend du paramètre précédent, `Warning for other disk encryption`.*  
    **Par défaut** : Non configuré  
    CSP BitLocker : [AllowStandardUserEncryption](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowstandarduserencryption)

     - **Autoriser** : les utilisateurs standard (non-administrateurs) peuvent activer le chiffrement BitLocker lorsqu’ils sont connectés.  
     - **Non configuré** : seuls les administrateurs peuvent activer le chiffrement BitLocker sur l’appareil.  

- **Configurer les méthodes de chiffrement**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [EncryptionMethodByDriveType](https://go.microsoft.com/fwlink/?linkid=872526)  

  - **Activer** : configurer des algorithmes de chiffrement pour le système d’exploitation, les données et les lecteurs amovibles.  
  - **Non configuré** : BitLocker utilise XTS-AES 128 bits comme méthode de chiffrement par défaut, ou utilise la méthode de chiffrement spécifiée par tout script d’installation.  

  Lorsque cette option est définie sur *Activer*, vous pouvez configurer les paramètres suivants :  

  - **Chiffrement pour les lecteurs du système d’exploitation**  
    **Par défaut**: XTS-AES 128 bits  
   
    choisissez la méthode de chiffrement pour les lecteurs de système d’exploitation. Nous vous recommandons d’utiliser l’algorithme AES-XTS.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128 bits**  
    - **XTS-AES 256 bits**  

  - **Chiffrement pour les lecteurs de données fixes**  
    **Valeur par défaut**: AES-CBC 128-bit  
   
    choisissez la méthode de chiffrement pour les lecteurs de données fixes (intégrés). Nous vous recommandons d’utiliser l’algorithme AES-XTS.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128 bits**  
    - **XTS-AES 256 bits**  

  - **Chiffrement pour les lecteurs de données amovibles**  
    **Valeur par défaut**: AES-CBC 128-bit  

    choisissez la méthode de chiffrement pour les lecteurs de données amovibles. Si le lecteur amovible est utilisé avec des appareils qui n’exécutent pas Windows 10, nous vous recommandons d’utiliser l’algorithme AES-CBC.  
    - **AES-CBC 128-bit**  
    - **AES-CBC 256-bit**  
    - **XTS-AES 128 bits**  
    - **XTS-AES 256 bits**  

### <a name="bitlocker-os-drive-settings"></a>Paramètres de lecteur du système d’exploitation BitLocker  

Ces paramètres s’appliquent spécifiquement aux lecteurs de données de système d’exploitation.  

- **Authentification supplémentaire au démarrage**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [SystemDrivesRequireStartupAuthentication](https://go.microsoft.com/fwlink/?linkid=872527)  

  - **Exiger** : configurer les conditions d’authentification pour le démarrage de l’ordinateur, notamment l’utilisation du module de plateforme sécurisée (TPM).  
  - **Non configuré** : configurez uniquement les options de base sur les appareils avec un module de plateforme sécurisée.  

  Lorsque cette option est définie sur *Exiger*, vous pouvez configurer les paramètres suivants :  

  - **BitLocker avec puce TPM non compatible**  
    **Par défaut** : Non configuré  

    - **Bloquer** : désactiver l’utilisation de BitLocker quand un appareil ne dispose pas d’une puce TPM compatible.  
    - **Non configuré** : les utilisateurs peuvent utiliser BitLocker sans puce TPM compatible. BitLocker peut exiger un mot de passe ou une clé de démarrage.  

  - **Démarrage du module TPM compatible**  
    **Valeur par défaut** : autoriser TPM  

    Configurer si le module de plateforme sécurisée est autorisé, obligatoire ou non autorisé.  

    - **Autoriser le module de plateforme sécurisée**  
    - **Ne pas autoriser TPM**  
    - **Exiger TPM**  

  - **Code PIN de démarrage du module TPM compatible**  
    **Valeur par défaut**: autoriser le code PIN de démarrage avec TPM  

    indiquez si l’utilisation d’un code PIN de démarrage avec la puce TPM est autorisée, non autorisée ou obligatoire. L’activation d’un code confidentiel de démarrage nécessite une intervention de l’utilisateur final.  

    - **Autoriser le code PIN de démarrage avec TPM**  
    - **Ne pas autoriser le code PIN de démarrage avec TPM**  
    - **Exiger un code PIN de démarrage avec TPM**

  - **Clé de démarrage du module TPM compatible**  
    **Valeur par défaut**: autoriser la clé de démarrage avec TPM  

    indiquez si l’utilisation d’une clé de démarrage avec la puce TPM est autorisée, non autorisée ou obligatoire. L’activation d’une clé de démarrage nécessite une intervention de l’utilisateur final.  

    - **Autoriser une clé de démarrage avec TPM**  
    - **Ne pas autoriser la clé de démarrage avec TPM**  
    - **Exiger une clé de démarrage avec TPM**  

  - **Code PIN et clé et de démarrage du module TPM compatible**  
    **Valeur par défaut**: autoriser la clé de démarrage et le code confidentiel avec TPM  

    indiquez si l’utilisation d’un code PIN et d’une clé de démarrage avec la puce TPM est autorisée, non autorisée ou obligatoire. L’activation d’une clé de démarrage et d’un code confidentiel de démarrage nécessite une intervention de l’utilisateur final.  
    - **Autoriser la clé de démarrage et le code confidentiel avec TPM**  
    - **Ne pas autoriser la clé de démarrage et le code confidentiel avec TPM**  
    - **Exiger une clé et un code PIN de démarrage avec TPM**   

- **Longueur minimale du code confidentiel**  
    **Par défaut** : Non configuré  
    CSP BitLocker : [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)   

    - **Activer** Configurez une longueur minimale pour le code PIN de démarrage du module de plateforme sécurisée.  
    - **Non configuré** : les utilisateurs peuvent configurer un code confidentiel de démarrage d’une longueur comprise entre 6 et 20 chiffres.  

  Lorsque cette option est définie sur *Activer*, vous pouvez configurer le paramètre suivant :  

  - **Nombre minimal de caractères**  
    **Valeur par défaut**: *non configuré* CSP BitLocker : [SystemDrivesMinimumPINLength](https://go.microsoft.com/fwlink/?linkid=872528)  

    entrez le nombre de caractères obligatoires pour le code PIN de démarrage (**4**-**20**).  

- **Récupération du lecteur du système d’exploitation**  
  **Par défaut** : Non configuré   
  CSP BitLocker : [SystemDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872529)  

  - **Activer** : contrôler la façon dont les lecteurs de système d’exploitation protégés par BitLocker récupèrent quand les informations de démarrage nécessaires ne sont pas disponibles.  
  - **Non configuré** : les options de récupération par défaut sont prises en charge pour la récupération BitLocker. Par défaut, un agent de récupération de données (DRA) est autorisé. Les options de récupération sont choisies par l’utilisateur, notamment le mot de passe de récupération et la clé de récupération. De plus, les informations de récupération ne sont pas sauvegardées dans AD DS.  

  Lorsque cette option est définie sur *Activer*, vous pouvez configurer les paramètres suivants :  

  - **Agent de récupération de données basé sur les certificats**  
    **Par défaut** : Non configuré  
     
    - **Bloquer** : empêche l’utilisation de l’agent de récupération de données avec les lecteurs de système d’exploitation protégés par BitLocker.  
    - **Non configuré** : autorisez l’utilisation des agents de récupération de données avec les lecteurs du système d’exploitation protégés par BitLocker.  

  - **Création d’un mot de passe de récupération par l’utilisateur**  
    **Valeur par défaut**: autoriser le mot de passe de récupération à 48 chiffres  

    indiquez si les utilisateurs sont autorisés, non autorisés ou contraints à générer un mot de passe de récupération de 48 chiffres.  
    - **Autoriser le mot de passe de récupération à 48 chiffres**  
    - **Ne pas autoriser le mot de passe de récupération à 48 chiffres**  
    - **Exiger un mot de passe de récupération à 48 chiffres**  

  - **Création d’une clé de récupération par l’utilisateur**  
    **Valeur par défaut**: autoriser la clé de récupération 256 bits  

    indiquez si les utilisateurs sont autorisés, non autorisés ou contraints à générer une clé de récupération de 256 bits.  
    - **Autoriser une clé de récupération de 256 bits**  
    - **N’autorisez pas la clé de récupération 256 bits**  
    - **Exiger une clé de récupération de 256 bits**  

  - **Options de récupération dans l’Assistant Installation de BitLocker**  
    **Par défaut** : Non configuré  

    - **Bloquer** : les utilisateurs ne peuvent pas voir ni changer les options de récupération. Quand la valeur est 
    - **Non configuré** : les utilisateurs peuvent voir et changer les options de récupération quand ils activent BitLocker. 
 
  - **Enregistrer les informations de récupération BitLocker dans Azure Active Directory**  
    **Par défaut** : Non configuré  

    - **Activer** : stocker les informations de récupération BitLocker dans Azure Active Directory (Azure AD).  
    - **Non configuré** : les informations de récupération BitLocker ne sont pas stockées dans AAD.  

  - **Informations de récupération BitLocker stockées dans Azure Active Directory**  
    **Par défaut**: sauvegarder les mots de passe et les jeux de clés de récupération  

    configurez les parties des informations de récupération BitLocker qui sont stockées dans Azure AD. Choisissez parmi :  
    - **Sauvegarder les mots de passe et les jeux de clés de récupération**  
    - **Sauvegarder les mots de passe de récupération uniquement**  

  - **Rotation du mot de passe de récupération pilotée par le client**  
    **Valeur par défaut**: la rotation des clés est activée pour les appareils joints à Azure ad  
    CSP BitLocker : [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Ce paramètre déclenche une rotation de mot de passe de récupération pilotée par le client après la récupération d’un lecteur de système d’exploitation (à l’aide de bootmgr ou WinRE).  

    - Non configuré  
    - Rotation de clé désactivée  
    - Rotation de clé activée pour le déciem joint Azure AD  
    - Rotation des clés activée pour les Azure AD et les appareils joints hybrides  

  - **Stocker les informations de récupération dans Azure Active Directory avant d’activer BitLocker**  
    **Par défaut** : Non configuré  
 
     Empêchez les utilisateurs d’activer BitLocker, sauf si l’ordinateur sauvegarde correctement les informations de récupération BitLocker dans Azure Active Directory.  

    - **Exiger** : empêcher les utilisateurs d’activer BitLocker, sauf si les informations de récupération BitLocker sont correctement stockées dans Azure AD.  
    - **Non configuré** : les utilisateurs peuvent activer BitLocker, même si les informations de récupération ne sont pas correctement stockées dans Azure AD.  

- **Message et URL de récupération préalables au démarrage**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [SystemDrivesRecoveryMessage](https://go.microsoft.com/fwlink/?linkid=872530)  

  - **Activer** -configurer le message et l’URL qui s’affichent sur l’écran de récupération de clé préalable au démarrage.  
  - **Non configuré** : désactiver cette fonctionnalité.  
  
  Lorsque cette option est définie sur *Activer*, vous pouvez configurer le paramètre suivant :  
  - **Message de récupération préalable au démarrage**  
    **Par défaut** : utiliser le message et l’URL de récupération par défaut   
 
    configurez la façon dont le message de récupération préalable au démarrage est présenté aux utilisateurs. Choisissez parmi :  
    - **Utiliser le message et l’URL de récupération par défaut**  
    - **Utiliser un message et une URL de récupération vides**  
    - **Utiliser le message de récupération personnalisé**  
    - **Utiliser l’URL de récupération personnalisée**  

### <a name="bitlocker-fixed-data-drive-settings"></a>Paramètres BitLocker des lecteurs de données fixes  

Ces paramètres s’appliquent spécifiquement aux lecteurs de données fixes.  

- **Accès en écriture à un lecteur de données fixe non protégé par BitLocker**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [FixedDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872534)  

  - **Bloquer** : octroyer l’accès en lecture seule aux lecteurs de données qui ne sont protégés par BitLocker.  
  - **Non configuré** : par défaut, accès en lecture et en écriture aux lecteurs de données qui ne sont pas chiffrés.  

- **Récupération d’un lecteur fixe**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [FixedDrivesRecoveryOptions](https://go.microsoft.com/fwlink/?linkid=872538)  

  - **Activer** : contrôler la façon dont les lecteurs fixes protégés par BitLocker récupèrent quand les informations de démarrage nécessaires ne sont pas disponibles.  
  - **Non configuré** : désactiver cette fonctionnalité.  

  Lorsque cette option est définie sur *Activer*, vous pouvez configurer les paramètres suivants :  

  - **Agent de récupération de données**  
    **Par défaut** : Non configuré  
 
    - **Bloquer** : empêcher l’utilisation de l’agent de récupération de données avec l’Éditeur de stratégie des lecteurs fixes protégés par BitLocker. 
    - **Non configuré** : permet d’utiliser des agents de récupération de données avec des lecteurs fixes protégés par BitLocker.  

  - **Création d’un mot de passe de récupération par l’utilisateur**  
    **Valeur par défaut**: autoriser le mot de passe de récupération à 48 chiffres  

    indiquez si les utilisateurs sont autorisés, non autorisés ou contraints à générer un mot de passe de récupération de 48 chiffres.  
    - **Autoriser le mot de passe de récupération à 48 chiffres**  
    - **Ne pas autoriser le mot de passe de récupération à 48 chiffres**  
    - **Exiger un mot de passe de récupération à 48 chiffres**  

  - **Création d’une clé de récupération par l’utilisateur**  
    **Valeur par défaut**: autoriser la clé de récupération 256 bits

    indiquez si les utilisateurs sont autorisés, non autorisés ou contraints à générer une clé de récupération de 256 bits.
    - **Autoriser une clé de récupération de 256 bits**  
    - **N’autorisez pas la clé de récupération 256 bits**  
    - **Exiger une clé de récupération de 256 bits**  

  - **Options de récupération dans l’Assistant Installation de BitLocker**  
    **Par défaut** : Non configuré  

    - **Bloquer** : les utilisateurs ne peuvent pas voir ni changer les options de récupération. Quand la valeur est 
    - **Non configuré** : les utilisateurs peuvent voir et changer les options de récupération quand ils activent BitLocker.
 
  - **Enregistrer les informations de récupération BitLocker dans Azure Active Directory**  
    **Par défaut** : Non configuré  

    - **Activer** : stocker les informations de récupération BitLocker dans Azure Active Directory (Azure AD).  
    - **Non configuré** : les informations de récupération BitLocker ne sont pas stockées dans AAD.

  - **Informations de récupération BitLocker stockées dans Azure Active Directory**  
    **Par défaut**: sauvegarder les mots de passe et les jeux de clés de récupération  

    configurez les parties des informations de récupération BitLocker qui sont stockées dans Azure AD. Choisissez parmi :  
    - **Sauvegarder les mots de passe et les jeux de clés de récupération**  
    - **Sauvegarder les mots de passe de récupération uniquement**  

  - **Rotation du mot de passe de récupération pilotée par le client**  
    **Valeur par défaut**: la rotation des clés est activée pour les appareils joints à Azure ad  
    CSP BitLocker : [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)  
    
    Ce paramètre déclenche une rotation de mot de passe de récupération pilotée par le client après la récupération d’un lecteur de système d’exploitation (à l’aide de bootmgr ou WinRE).  

    - Non configuré  
    - Rotation de clé désactivée  
    - Rotation de clé activée pour le déciem joint Azure AD  
    - Rotation des clés activée pour les Azure AD et les appareils joints hybrides  

  - **Stocker les informations de récupération dans Azure Active Directory avant d’activer BitLocker**  
    **Par défaut** : Non configuré  
 
    Empêchez les utilisateurs d’activer BitLocker, sauf si l’ordinateur sauvegarde correctement les informations de récupération BitLocker dans Azure Active Directory.  

    - **Exiger** : empêcher les utilisateurs d’activer BitLocker, sauf si les informations de récupération BitLocker sont correctement stockées dans Azure AD.  
    - **Non configuré** : les utilisateurs peuvent activer BitLocker, même si les informations de récupération ne sont pas correctement stockées dans Azure AD.  

### <a name="bitlocker-removable-data-drive-settings"></a>Paramètres BitLocker des lecteurs de données amovibles  

Ces paramètres s’appliquent spécifiquement aux lecteurs de données amovibles.  

- **Accès en écriture à un lecteur de données amovible non protégé par BitLocker**  
  **Par défaut** : Non configuré  
  CSP BitLocker : [RemovableDrivesRequireEncryption](https://go.microsoft.com/fwlink/?linkid=872540)  

  - **Bloquer** : octroyer l’accès en lecture seule aux lecteurs de données qui ne sont protégés par BitLocker.  
  - **Non configuré** : par défaut, accès en lecture et en écriture aux lecteurs de données qui ne sont pas chiffrés.  

  Lorsque cette option est définie sur *Activer*, vous pouvez configurer le paramètre suivant :  

  - **Accès en écriture aux appareils configurés dans une autre organisation**  
    **Par défaut** : Non configuré  

    - **Bloquer** : autoriser l’accès en écriture pour les appareils configurés dans une autre organisation.  
    - **Non configuré** -refuser l’accès en écriture.  
 
## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard  

Utilisez la [protection contre](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/exploit-protection) les attaques pour gérer et réduire la surface d’attaque des applications utilisées par vos employés.  

### <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque  

Les règles de réduction de la surface d’attaque aident à empêcher les comportements que les logiciels malveillants utilisent souvent pour infecter des ordinateurs avec du code malveillant.  

#### <a name="attack-surface-reduction-rules"></a>Règles de réduction de la surface d'attaque  

- **Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows**  
  **Par défaut** : Non configuré  
  Règle : [bloquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows (lsass.exe)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-credential-stealing-from-the-windows-local-security-authority-subsystem-lsassexe)

  Cette fonctionnalité contribue à empêcher les actions et les applications généralement utilisées par les programmes malveillants pour infecter les ordinateurs.  

  - **Non configuré**  
  - **Activer** : marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows (lsass.exe).  
  - **Auditer uniquement**  

- **Création de processus à partir d’Adobe Reader (bêta)**  
  **Par défaut** : Non configuré  
  Règle : [empêcher Adobe Reader de créer des processus enfants](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-adobe-reader-from-creating-child-processes)  

  - **Non configuré**  
  - **Activer** -bloquer les processus enfants qui sont créés à partir d’Adobe Reader.  
  - **Auditer uniquement**  

#### <a name="rules-to-prevent-office-macro-threats"></a>Règles pour empêcher les menaces sur les macros Office  

Empêchez les applications Office d’effectuer les actions suivantes :  

- **Applications Office effectuant des injections dans d’autres processus (aucune exception)**  
  **Par défaut** : Non configuré  
  Règle : [empêcher les applications Office d’injecter du code dans d’autres processus](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-injecting-code-into-other-processes)  

  - **Non configuré**  
  - **Bloquer** : empêchez les applications Office d’injecter dans d’autres processus.  
  - **Auditer uniquement**  

- **Applications/macros Office créant du contenu exécutable**  
  **Par défaut** : Non configuré  
  Règle : [empêcher les applications Office de créer du contenu exécutable](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-applications-from-creating-executable-content)  

  - **Non configuré**  
  - **Bloquer** : empêchez les applications et les macros Office de créer du contenu exécutable.  
  - **Auditer uniquement**  

- **Applications Office lançant des processus enfants**  
  **Par défaut** : Non configuré  
  Règle : [bloquer toutes les applications Office de la création de processus enfants](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-all-office-applications-from-creating-child-processes)  

  - **Non configuré**  
  - **Bloquer** : empêchez les applications Office de lancer des processus enfants.  
  - **Auditer uniquement**  
  
- **Importations Win32 de code macro Office**  
  **Par défaut** : Non configuré  
  Règle : [bloquer les appels d'API Win32 à partir des macros Office](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-win32-api-calls-from-office-macros)  

  - **Non configuré**  
  - **Bloc-bloquer** les importations Win32 à partir du code macro dans Office.  
  - **Auditer uniquement**  
  
- **Création de processus à partir de produits de communication Office**  
  **Par défaut** : Non configuré  
  Règle : [empêcher l’application de communication Office de créer des processus enfants](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-office-communication-application-from-creating-child-processes)  

  - **Non configuré**  
  - **Activer** -bloquer la création de processus enfants à partir d’applications Office Communications.  
  - **Auditer uniquement**  

#### <a name="rules-to-prevent-script-threats"></a>Règles pour empêcher les menaces sur les scripts  

Bloquez les éléments suivants pour empêcher les menaces sur les scripts :  

- **Code js/vbs/ps/macro brouillé**  
  **Par défaut** : Non configuré  
  Règle : [bloquer l’exécution de scripts potentiellement obfusqués](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-execution-of-potentially-obfuscated-scripts)    

  - **Non configuré**  
  - **Bloquer : bloquer** tout code js/vbs/PS/macro masqué.  
  - **Auditer uniquement**  

- **js/vbs, exécution de la charge utile téléchargée à partir d’Internet (aucune exception)**  
  **Par défaut** : Non configuré  
  Règle : [empêcher JavaScript ou VBScript de lancer du contenu exécutable téléchargé](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-javascript-or-vbscript-from-launching-downloaded-executable-content)  

  - **Non configuré**  
  - **Bloc-bloc** js/vbs à partir de l’exécution de la charge utile téléchargée à partir d’Internet.  
  - **Auditer uniquement**  

- **Création de processus à partir des commandes PSExec et WMI**  
  **Par défaut** : Non configuré  
  Règle : [bloquer les créations de processus issues des commandes PSExec et WMI](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-process-creations-originating-from-psexec-and-wmi-commands)  

  - **Non configuré**  
  - **Bloquer** : bloquer les créations de processus issues des commandes PSExec et WMI.  
  
  - **Auditer uniquement**  

- **Processus non approuvés et non signés exécutés à partir d’USB**  
  **Par défaut** : Non configuré  
  Règle : [bloquer les processus non approuvés et non signés exécutés à partir d’un lecteur USB](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-untrusted-and-unsigned-processes-that-run-from-usb)    

  - **Non configuré**  
  - **Bloquer** : bloquer les processus non approuvés et non signés exécutés à partir d’USB.  
  - **Auditer uniquement**  
  
- **Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée**  
  **Par défaut** : Non configuré  
  Règle : [bloquer l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prédominance, d’âge ou de liste approuvée](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion)    

  - **Non configuré**  
  - **Bloquer** : bloquer l’exécution des fichiers exécutables sauf s’ils répondent à des critères de prédominance, d’âge ou de liste approuvée.  
  - **Auditer uniquement**  

#### <a name="rules-to-prevent-email-threats"></a>Règles pour empêcher les menaces sur les e-mails  

Bloquez ce qui suit pour empêcher les menaces sur les e-mails :  

- **Exécution du contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de la messagerie (messagerie web/client de messagerie) (aucune exception)**  
  **Par défaut** : Non configuré  
  Règle : [bloquer le contenu exécutable du client de messagerie et de la messagerie web](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail)  

  - **Non configuré**  
  - **Bloquer** : bloquer l’exécution du contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de la messagerie (messagerie web/client de messagerie).  
  - **Auditer uniquement**  

#### <a name="rules-to-protect-against-ransomware"></a>Règles de protection contre les ransomware  

- **Protection avancée contre les ransomware**  
  Par défaut : non configuré  
  Règle : [utiliser une protection avancée contre les rançongiciels](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#use-advanced-protection-against-ransomware)  

  - **Non configuré**  
  - **Activer** : utiliser une protection agressive contre les ransomware.  
  - **Auditer uniquement**  

#### <a name="attack-surface-reduction-exceptions"></a>Exceptions de la réduction de surface d’attaque

- **Fichiers et dossiers à exclure des règles de réduction de la surface d’attaque**  
  Fournisseur CSP Defender : [AttackSurfaceReductionOnlyExclusions](https://go.microsoft.com/fwlink/?linkid=872981)  

  - **Importez** un fichier. csv qui contient des fichiers et des dossiers à exclure des règles de réduction de la surface d’attaque.  
  - **Ajoutez** manuellement des fichiers ou dossiers locaux.  

> [!IMPORTANT]  
> Pour permettre une installation et une exécution correctes des applications Win32 métier, les paramètres de logiciel anti-programme malveillant doivent exclure les répertoires suivants de l’analyse :  
> **Sur des ordinateurs clients X64** :  
> *C:\Program Files (x86)\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  
>  
> **Sur des ordinateurs clients X86** :  
> *C:\Program Files\Microsoft Intune Management Extension\Content*  
> *C:\windows\IMECache*  

### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers  

[Protégez vos données importantes](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) contre des applications malveillantes et des menaces, telles que les ransomware.  

- **Protection des dossiers**  
  **Par défaut** : Non configuré  
  Fournisseur CSP Defender : [EnableControlledFolderAccess](https://go.microsoft.com/fwlink/?linkid=872614)  

  Protéger les fichiers et les dossiers contre les modifications non autorisées par des applications hostiles.  

  - **Non configuré**  
  - **Activer**  
  - **Auditer uniquement**  
  - **Bloquer la modification du disque**  
  - **Auditer la modification du disque**  

  Lorsque vous sélectionnez une configuration autre que *non configurée*, vous pouvez configurer les éléments suivants :  
  - **Liste des applications qui ont accès aux dossiers protégés**  
    Fournisseur CSP Defender : [ControlledFolderAccessAllowedApplications](https://go.microsoft.com/fwlink/?linkid=872616)  

    - **Importez** un fichier. csv qui contient une liste d’applications.  
    - **Ajoutez** manuellement des applications à cette liste.  

  - **Liste des dossiers supplémentaires qui doivent être protégés**  
    Fournisseur CSP Defender : [ControlledFolderAccessProtectedFolders](https://go.microsoft.com/fwlink/?linkid=872617)  

    - **Importez** un fichier. csv qui contient une liste de dossiers.  
    - **Ajoutez** manuellement des dossiers à cette liste.  

### <a name="network-filtering"></a>Filtrage du réseau  

Bloquez les connexions sortantes à partir de n’importe quelle application vers des adresses IP ou des domaines avec des réputations faibles. Le filtrage réseau est pris en charge en mode d’audit et de blocage.  

- **Protection du réseau**  
  **Par défaut** : Non configuré  
  Fournisseur CSP Defender : [EnableNetworkProtection](https://go.microsoft.com/fwlink/?linkid=872618)  

  L’objectif de ce paramètre est de protéger les utilisateurs finaux des applications ayant accès à des arnaques de hameçonnage, à des sites d’hébergement d’exploitation et à du contenu malveillant sur Internet. Il empêche également des navigateurs tiers de se connecter à des sites dangereux.  

  - **Non configuré** : désactiver cette fonctionnalité. Les utilisateurs et les applications ne sont pas bloqués pour se connecter aux domaines dangereux. Les administrateurs ne peuvent pas voir cette activité dans Windows Defender Security Center.  
  - **Activer** : activer la protection du réseau et empêcher les utilisateurs et les applications de se connecter à des domaines dangereux. Les administrateurs peuvent consulter cette activité dans Windows Defender Security Center.  
  - **Audit uniquement**:-les utilisateurs et les applications ne sont pas bloqués lors de la connexion à des domaines dangereux. Les administrateurs peuvent consulter cette activité dans Windows Defender Security Center.  

### <a name="exploit-protection"></a>Exploit Protection  
 

- **Télécharger XML**  
  **Par défaut** : *non configuré*  

  Pour utiliser exploit protection afin de [protéger les appareils contre les attaques](https://docs.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), créez un fichier XML qui comprend les paramètres d’atténuation du système et des applications de votre choix. Il existe deux méthodes pour créer le fichier XML :  

  - *PowerShell* : utilisez une ou plusieurs des applets de commande PowerShell *Get-ProcessMitigation*, *Set-ProcessMitigation* et *ConvertTo-ProcessMitigationPolicy*. Les applets de commande permettent de configurer les paramètres d’atténuation et de les exporter sous forme d’une représentation XML.  

  - *Interface utilisateur du Centre de sécurité Windows Defender* : dans le Centre de sécurité Windows Defender, cliquez sur Contrôle des applications et du navigateur, puis faites défiler l’écran vers le bas jusqu’à Exploit Protection. Utilisez d’abord les onglets Paramètres système et Paramètres du programme pour configurer les paramètres d’atténuation. Recherchez ensuite le lien Exporter les paramètres en bas de l’écran pour les exporter sous forme d’une représentation XML.  

- **Modification par l’utilisateur de l’interface de protection contre les attaques**  
  **Par défaut** : Non configuré  
  CSP ExploitGuard : [ExploitProtectionSettings](https://go.microsoft.com/fwlink/?linkid=872887)  


  - **Bloquer** : téléchargez un fichier XML qui vous permet de configurer la mémoire, le processus de contrôle et les restrictions de stratégie. Les paramètres du fichier XML permettent de protéger une application contre les attaques.  
  - **Non configuré** : aucune configuration personnalisée n’est utilisée.  

## <a name="windows-defender-application-control"></a>Contrôle d’application Windows Defender  

Choisissez des applications supplémentaires qui doivent être auditées par ou qui peuvent être approuvées pour être exécutées par Windows Defender application Control. L’exécution des composants Windows et de toutes les applications du Windows Store est automatiquement approuvée.  


- **Stratégies d’intégrité du code de contrôle des applications**  
  **Par défaut** : Non configuré  
   CSP : [CSP AppLocker](https://go.microsoft.com/fwlink/?linkid=874543)  

  - **Appliquer** : choisissez les stratégies d’intégrité du code de contrôle des applications pour les appareils de vos utilisateurs.  
  
    Une fois activé sur un appareil, le contrôle d’application peut être désactivé uniquement en changeant le mode *Appliquer* en *Auditer uniquement*. Quand vous changez le mode *Appliquer* en *Non configuré*, le contrôle d’application continue à s’appliquer sur les appareils attribués.  

  - **Non configuré** : le contrôle d’application n’est pas ajouté aux appareils. Toutefois, les paramètres qui ont été précédemment ajoutés continuent à être appliqués sur les appareils affectés. 
 
  - **Auditer uniquement** -les applications ne sont pas bloquées. Tous les événements sont consignés dans les journaux du client local.  

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard  

Windows Defender Credential Guard protège contre le vol d’informations d’identification. Il isole les clés secrètes afin que seuls les logiciels système privilégiés puissent y accéder.  

- **Credential Guard**  
  **Par défaut**: désactiver  
  [CSP DeviceGuard](https://go.microsoft.com/fwlink/?linkid=872424)  

  - **Désactiver** : désactiver Credential Guard à distance s’il a été préalablement activé avec l’option **Activé sans verrouillage UEFI**.  

  - **Activer avec le verrouillage UEFI** : Credential Guard ne peut pas être désactivé à distance à l’aide d’une clé de Registre ou d’une stratégie de groupe.  

    > [!NOTE]
    > Si vous utilisez ce paramètre et souhaitez ultérieurement désactiver Credential Guard, vous devez définir la stratégie de groupe sur **Désactivé**. Vous devez également effacer physiquement les informations de configuration UEFI sur chaque ordinateur. Tant que la configuration UEFI persiste, Credential Guard est activé.  

  - **Activer sans verrouillage UEFI** : permet de désactiver Credential Guard à distance à l’aide d’une stratégie de groupe. Les appareils utilisant ce paramètre doivent exécuter Windows 10 (version 1511) et versions ultérieures.  

  Lorsque vous *activez* Credential Guard, les fonctionnalités requises suivantes sont également activées :  
  
  - **Sécurité basée sur la virtualisation (VBS)**  
    s’active au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité.  
  - **Démarrage sécurisé avec accès direct à la mémoire**  
    active VBS avec les protections Démarrage sécurisé et Accès direct à la mémoire (DMA). Les protections DMA nécessitent une prise en charge matérielle et sont uniquement activées sur des appareils configurés correctement.  

## <a name="windows-defender-security-center"></a>Centre de sécurité Windows Defender  

Le Centre de sécurité Windows Defender fonctionne comme une application ou un processus distinct de chacune des fonctionnalités individuelles. Elle affiche des notifications dans le centre de notifications. Elle agit comme un collecteur de données ou emplacement unique pour afficher l’état et exécuter la configuration de chacune des fonctionnalités. Vous trouverez plus d’informations dans la documentation [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).  

### <a name="windows-defender-security-center-app-and-notifications"></a>Application Centre de sécurité Windows Defender et notifications  

Empêchez l’utilisateur final d’accéder aux différentes zones de l’application Centre de sécurité Windows Defender. Le masquage d’une section bloque également les notifications associées.  

- **Protection contre les virus et menaces**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableVirusUI](https://go.microsoft.com/fwlink/?linkid=873662)  

  Configurez si les utilisateurs finaux peuvent afficher la zone de protection contre les virus et les menaces dans le Security Center Windows Defender. Le masquage de cette section bloquera également toutes les notifications liées à la protection contre les virus et les menaces.  

  - **Non configuré**  
  - **Masquer**  

- **Protection contre les ransomware**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [HideRansomwareDataRecovery](https://go.microsoft.com/fwlink/?linkid=873664)  

  Configurez si les utilisateurs finaux peuvent afficher la zone de protection de ransomware dans le Security Center Windows Defender. Le masquage de cette section bloquera également toutes les notifications liées à la protection contre les ransomware.  

  - **Non configuré**  
  - **Masquer**  

- **Protection des comptes**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableAccountProtectionUI](https://go.microsoft.com/fwlink/?linkid=873666)  

  Configurez si les utilisateurs finaux peuvent afficher la zone de protection des comptes dans le Security Center Windows Defender. Le masquage de cette section bloquera également toutes les notifications liées à la protection des comptes.  

  - **Non configuré**  
  - **Masquer**  

- **Pare-feu et protection du réseau**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableNetworkUI](https://go.microsoft.com/fwlink/?linkid=873668)  

  Configurez si les utilisateurs finaux peuvent afficher la zone de protection du pare-feu et du réseau dans le centre de sécurité Windows Defender. Si vous masquez cette section, toutes les notifications relatives à la protection du pare-feu et du réseau seront également bloquées.  

  - **Non configuré**  
  - **Masquer**  

- **Contrôle des applications et du navigateur**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableAppBrowserUI](https://go.microsoft.com/fwlink/?linkid=873669)  

  Configurez si les utilisateurs finaux peuvent afficher la zone de contrôle de l’application et du navigateur dans le centre de sécurité Windows Defender. Si vous masquez cette section, toutes les notifications relatives au contrôle de l’application et du navigateur seront également bloquées.  

  - **Non configuré**  
  - **Masquer**  

- **Protection matérielle**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableDeviceSecurityUI](https://go.microsoft.com/fwlink/?linkid=873670)  

  Configurez si les utilisateurs finaux peuvent afficher la zone de protection matérielle dans le Security Center Windows Defender. Le masquage de cette section entraînera également la blocage de toutes les notifications liées à la protection matérielle.  

  - **Non configuré**  
  - **Masquer**  

- **Performances des appareils et intégrité**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableHealthUI](https://go.microsoft.com/fwlink/?linkid=873671)  

  Configurer si les utilisateurs finaux peuvent afficher la zone performances et intégrité des appareils dans le centre de sécurité Windows Defender. Si vous masquez cette section, toutes les notifications relatives aux performances et à l’intégrité de l’appareil seront également bloquées.  
  
  - **Non configuré**  
  - **Masquer**  

- **Options de contrôle parental**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableFamilyUI](https://go.microsoft.com/fwlink/?linkid=873673)  

  Configurez si les utilisateurs finaux peuvent afficher la zone Options de famille dans le centre de sécurité Windows Defender. Le masquage de cette section entraîne également le blocage de toutes les notifications liées aux options de la famille.  
  
  - **Non configuré**  
  - **Masquer**  

- **Notifications des zones affichées de l’application**  
  **Par défaut** : Non configuré  
  CSP WindowsDefenderSecurityCenter : [DisableNotifications](https://go.microsoft.com/fwlink/?linkid=873675)  

  choisissez les notifications à afficher aux utilisateurs finaux. Les notifications non critiques sont notamment les récapitulatifs d’activité de l’antivirus Windows Defender, dont les notifications indiquant qu’une analyse est terminée. Toutes les autres notifications sont considérées comme critiques.  

  - **Non configuré**  
  - **Bloquer les notifications non critiques**  
  - **Bloquer toutes les notifications**  

- **Icône Windows Security Center dans la barre d’état système**  
  **Par défaut** : Non configuré  

  Configurez l’affichage du contrôle de zone de notification. L’utilisateur doit se déconnecter et se connecter ou redémarrer l’ordinateur pour que ce paramètre prenne effet.  
  
  - **Non configuré**  
  - **Masquer**  

- **Bouton Effacer le module de plateforme sécurisée**  
  **Par défaut** : Non configuré  

  Configurez l’affichage du bouton Effacer le module de plateforme sécurisée.  
  
  - **Non configuré**  
  - **Désactiver**  

- **Avertissement de mise à jour du microprogramme TPM**  
  **Par défaut** : Non configuré  
  
  Configurez l’affichage du microprogramme de mise à jour du module de plateforme sécurisée lorsqu’un microprogramme vulnérable est détecté.  

  - **Non configuré**  
  - **Masquer**  

- **Protection contre les falsifications**  
  **Par défaut** : Non configuré

  Activez ou désactivez la protection contre les falsifications sur les appareils. Pour utiliser la protection contre les falsifications, vous devez [intégrer Microsoft Defender-protection avancée contre les menaces avec Intune](advanced-threat-protection.md)et disposer de [Enterprise Mobility + Security E5 licences](../fundamentals/licenses.md).  
  - **Non configuré** -aucune modification n’est apportée aux paramètres de l’appareil.
  - **Activé** : la protection contre les falsifications est activée et les restrictions sont appliquées sur les appareils.
  - **Désactivé** : la protection contre les falsifications est désactivée et les restrictions ne sont pas appliquées.

### <a name="it-contact-information"></a>Informations de contact du service informatique  

Indiquez les informations de contact du service informatique à afficher dans l’application Centre de sécurité Windows Defender et ses notifications.  

Vous avez le choix entre **Afficher dans l’application et dans les notifications**, **Afficher uniquement dans l’application**, **Afficher uniquement dans les notifications** ou **Ne pas afficher**. Entrez le **nom de l’organisation du service informatique** et au moins l’une des options de contact suivantes :  


- **Informations de contact du service informatique**  
  **Valeur par défaut**: ne pas afficher  
  CSP WindowsDefenderSecurityCenter : [EnableCustomizedToasts](https://go.microsoft.com/fwlink/?linkid=873676)  
  
  Configurez l’emplacement d’affichage des informations de contact pour les utilisateurs finaux.  
  
  - **Afficher dans l’application et dans les notifications**  
  - **Afficher uniquement dans l’application**  
  - **Afficher uniquement dans les notifications**  
  - **Ne pas afficher**  

  Lorsqu’il est configuré pour afficher, vous pouvez configurer les paramètres suivants :  

  - **Nom du département informatique**  
    **Par défaut** : *non configuré*  
    CSP WindowsDefenderSecurityCenter : [CompanyName](https://go.microsoft.com/fwlink/?linkid=873677)  

  - **Numéro de téléphone ou ID Skype du service informatique**  
    **Par défaut** : *non configuré*  
    CSP WindowsDefenderSecurityCenter : [téléphone](https://go.microsoft.com/fwlink/?linkid=873678) 

  - **Adresse e-mail du service informatique**  
    **Par défaut** : *non configuré*  
    CSP WindowsDefenderSecurityCenter : [e-mail](https://go.microsoft.com/fwlink/?linkid=873679)  

  - **URL du site web de support informatique**  
    **Par défaut** : *non configuré*  
    CSP WindowsDefenderSecurityCenter : [URL](https://go.microsoft.com/fwlink/?linkid=873680)  
 
## <a name="local-device-security-options"></a>Option de sécurité de l’appareil local  

Utilisez ces options pour configurer les paramètres de sécurité locale sur les appareils Windows 10.  

### <a name="accounts"></a>Comptes  

- **Ajouter de nouveaux comptes Microsoft**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [Accounts_BlockMicrosoftAccounts](https://go.microsoft.com/fwlink/?linkid=867916)  


  - **Bloquer** : empêcher les utilisateurs d’ajouter de nouveaux comptes Microsoft sur l’appareil.  
  - **Non configuré** : les utilisateurs peuvent utiliser des comptes Microsoft sur l’appareil.  

- **Ouverture de session à distance sans mot de passe**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867890)  


   - **Bloquer** : autoriser uniquement les comptes locaux avec des mots de passe vides à se connecter à l’aide du clavier de l’appareil.  
   - **Non configuré** : autoriser les comptes locaux avec des mots de passe vides à se connecter à partir d’emplacements autres que l’appareil physique.  

#### <a name="admin"></a>Administrateur  

- **Compte Administrateur local**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [Accounts_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly](https://go.microsoft.com/fwlink/?linkid=867850)  


  - **Bloc** Empêcher l’utilisation d’un compte d’administrateur local.  
  - **Non configuré**  

- **Renommer le compte Administrateur**  
  **Par défaut** : *non configuré*  
  CSP LocalPoliciesSecurityOptions : [Accounts_RenameAdministratorAccount](https://go.microsoft.com/fwlink/?linkid=867917)  
 

  Définir un autre nom de compte à associer à l’identificateur de sécurité (SID) pour le compte « Administrateur ».  

 #### <a name="guest"></a>Invité  

- **Compte Invité**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [LocalPoliciesSecurityOptions](https://go.microsoft.com/fwlink/?linkid=867853)  

  - **Bloquer** : empêche l’utilisation d’un compte invité.  
  - **Non configuré**  

- **Renommer le compte invité**  
  **Par défaut** : *non configuré*  
  CSP LocalPoliciesSecurityOptions : [Accounts_RenameGuestAccount](https://go.microsoft.com/fwlink/?linkid=867918)  
  
  Définir un autre nom de compte à associer à l’identificateur de sécurité (SID) pour le compte « Invité ».  

### <a name="devices"></a>Périphériques  

- **Retirer l’appareil de la station d’accueil sans ouverture de session**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [Devices_AllowUndockWithoutHavingToLogon](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-devices-allowundockwithouthavingtologon)  

  
  - **Bloquer** : les utilisateurs peuvent appuyer sur le bouton d’éjection physique d’un appareil portable placé sur une station d’accueil afin de retirer l’appareil de manière sécurisée.  
  - **Non configuré** : un utilisateur doit se connecter à l’appareil et recevoir l’autorisation de détacher l’appareil.  

- **Installer des pilotes d’imprimante pour les imprimantes partagées**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [Devices_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters](https://go.microsoft.com/fwlink/?linkid=867921)  


  - **Activé** : n’importe quel utilisateur peut installer un pilote d’imprimante lors de la connexion à une imprimante partagée.  
  - **Non configuré** : seuls les administrateurs peuvent installer un pilote lors de la connexion à une imprimante partagée.  

- **Limiter l’accès au CD-ROM à l’utilisateur actif local**  
  **Par défaut** : non configuré  
  CSP : [Devices_RestrictCDROMAccessToLocallyLoggedOnUserOnly](https://go.microsoft.com/fwlink/?linkid=867922)  


  - **Activé** : seul l’utilisateur connecté de manière interactive peut utiliser le CD-ROM. Si cette stratégie est activée et qu’aucun utilisateur n’est connecté de façon interactive, le CD-ROM est accessible sur le réseau.  
  - **Non configuré** : tout le monde a accès au CD-ROM.  

- **Formater et éjecter les supports amovibles**  
  **Valeur par défaut**: administrateurs  
  CSP : [Devices_AllowedToFormatAndEjectRemovableMedia](https://go.microsoft.com/fwlink/?linkid=867920)  
 

  définit les personnes autorisées à formater et à éjecter un support NTFS amovible :  
  - **Non configuré**  
  - **Administrateurs**  
  - **Administrateurs et utilisateurs avec pouvoir**  
  - **Administrateurs et utilisateurs interactifs**  

### <a name="interactive-logon"></a>Ouverture de session interactive  

- **Minutes d’inactivité de l’écran de verrouillage avant l’activation de l’économiseur d’écran**  
  **Par défaut** : *non configuré*  
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_MachineInactivityLimit](https://go.microsoft.com/fwlink/?linkid=867891)  


  entrez le nombre maximal de minutes d’inactivité sur l’écran de connexion du bureau interactif avant le démarrage de l’économiseur d’écran. (**0** - **99999**)  

- **Exiger CTRL+ALT+SUPPR pour ouvrir une session**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_DoNotRequireCTRLALTDEL](https://go.microsoft.com/fwlink/?linkid=867951)  


  - **Activer** : les utilisateurs n’ont pas à appuyer sur CTRL+ALT+SUPPR pour se connecter.  
  - **Non configuré** : obliger les utilisateurs à appuyer sur CTRL+ALT+SUPPR avant de se connecter à Windows.  

- **Comportement lorsque la carte à puce est retirée**  
  **Par défaut** : verrouiller la station de travail   
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_SmartCardRemovalBehavior](https://go.microsoft.com/fwlink/?linkid=868437)  
    
  détermine ce qui se passe quand la carte à puce d’un utilisateur connecté est retirée du lecteur de carte à puce. Les options disponibles sont les suivantes :  

  - **Verrouiller la station de travail** : la station de travail est verrouillée quand la carte à puce est retirée. Cette option permet aux utilisateurs de quitter les lieux, d’emporter leur carte à puce et de conserver une session protégée.  
  - **Aucune action**  
  - **Forcer la fermeture de session** : l’utilisateur est automatiquement déconnecté lorsque la carte à puce est retirée.  
  - **Déconnecter en cas de session des services Bureau à distance** : le retrait de la carte à puce déconnecte la session sans déconnecter l’utilisateur. Cette option permet à l’utilisateur d’insérer la carte à puce et de reprendre la session ultérieurement, ou sur un autre ordinateur équipé d’un lecteur de carte à puce, sans avoir à se reconnecter. Si la session est locale, cette stratégie fonctionne comme l’option Verrouiller la station de travail.  

#### <a name="display"></a>Écran  

- **Informations utilisateur sur l’écran de verrouillage**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_DisplayUserInformationWhenTheSessionIsLocked](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-displayuserinformationwhenthesessionislocked)  

  configurez les informations de l’utilisateur qui s’affichent quand la session est verrouillée. Si cette option n’est pas configurée, le nom d’utilisateur, le domaine et le nom d’utilisateur complet sont affichés.  

  - **Non configuré**  
  - **Nom d’affichage de l’utilisateur, domaine et nom d’utilisateur**  
  - **Nom d'affichage de l'utilisateur uniquement**  
  - **Ne pas afficher les informations utilisateur**  

- **Masquer le dernier utilisateur connecté**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_DoNotDisplayLastSignedIn](https://go.microsoft.com/fwlink/?linkid=868437)  
  
  
  - **Enable** -masquer le nom d’utilisateur.  
  - **Non configuré** : afficher le dernier nom d’utilisateur.  

- **Masquer le nom d’utilisateur lors**de la connexion 
  **par défaut**: non configuré  
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_DoNotDisplayUsernameAtSignIn](https://go.microsoft.com/fwlink/?linkid=867959)  

  
  - **Enable** -masquer le nom d’utilisateur.  
  - **Non configuré** : afficher le dernier nom d’utilisateur.  

- **Titre du message de connexion**  
  **Par défaut** : *non configuré*  
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_MessageTitleForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867964)  

  définissez le titre du message pour les utilisateurs se connectant.  

- **Texte du message de connexion**  
  **Par défaut** : *non configuré*  
  CSP LocalPoliciesSecurityOptions : [InteractiveLogon_MessageTextForUsersAttemptingToLogOn](https://go.microsoft.com/fwlink/?linkid=867962)  

  définissez le texte du message pour les utilisateurs se connectant.  
  
### <a name="network-access-and-security"></a>Accès réseau et sécurité

- **Accès anonyme aux canaux nommés et aux partages**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [NetworkAccess_RestrictAnonymousAccessToNamedPipesAndShares](https://go.microsoft.com/fwlink/?linkid=868432)  

  - **Non configuré** : restreindre l’accès anonyme aux paramètres de partage et de canal nommé. S’applique aux paramètres accessibles de manière anonyme.  
  - **Bloquer** : désactivez cette stratégie, en rendant les accès anonymes disponibles.  

- **Énumération anonyme des comptes SAM**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [NetworkAccess_DoNotAllowAnonymousEnumerationOfSAMAccounts](https://go.microsoft.com/fwlink/?linkid=868434)  
  
  - **Non configuré** : les utilisateurs anonymes peuvent énumérer les comptes Sam.  
  - **Bloquer** : empêcher l’énumération anonyme des comptes SAM.  

- **Énumération anonyme des comptes et partages SAM**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [NetworkAccess_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares](https://go.microsoft.com/fwlink/?linkid=868435)  

  - **Non configuré** : des utilisateurs anonymes peuvent énumérer les noms des comptes de domaine et des partages réseau.  
  - **Bloquer** : empêcher l’énumération anonyme des comptes et des partages SAM. 

- **Valeur de hachage LAN Manager stockée au changement de mot de passe**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [NetworkSecurity_DoNotStoreLANManagerHashValueOnNextPasswordChange](https://go.microsoft.com/fwlink/?linkid=868431)  
   
  Détermine si la valeur de hachage pour les mots de passe est stockée la prochaine fois que le mot de passe est modifié. 
  - **Non configuré** : la valeur de hachage n’est pas stockée  
  - **Bloquer** : LAN Manager (LM) stocke la valeur de hachage pour le nouveau mot de passe.  

- **Demandes d’authentification PKU2U**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [NetworkSecurity_AllowPKU2UAuthenticationRequests](https://go.microsoft.com/fwlink/?linkid=867892)  

  - **Non configuré**-autoriser les requêtes PU2U.  
  - **Bloquer : bloquer** les demandes d’authentification PKU2U sur l’appareil.  

- **Limiter les connexions RPC à distance au SAM**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [NetworkAccess_RestrictClientsAllowedToMakeRemoteCallsToSAM](https://go.microsoft.com/fwlink/?linkid=867893)  
  
  - **Non configuré** : utilisez le descripteur de sécurité par défaut, qui peut permettre aux utilisateurs et aux groupes d’effectuer des appels RPC distants vers le Sam.
  - **Autoriser** : interdire aux utilisateurs et aux groupes d’effectuer des appels RPC distants vers le gestionnaire de comptes de sécurité (Sam), qui stocke les comptes d’utilisateur et les mots de passe. L’option **autoriser** vous permet également de modifier la chaîne SDDL (Security Descriptor Definition Language) par défaut afin d’autoriser ou de refuser explicitement les utilisateurs et les groupes à effectuer ces appels distants.  

    - **Descripteur de sécurité**  
      **Par défaut** : *non configuré*  
    
- **Sécurité de session minimale pour les clients basés sur NTLM SSP**  
  **Valeur par défaut**: aucune  
  CSP LocalPoliciesSecurityOptions : [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedClients](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedclients)  
  
  Ce paramètre de sécurité permet à un serveur d’exiger la négociation d’un chiffrement de 128 bits et/ou de la sécurité de session NTLMv2.  

  - **Aucune.**  
  - **Exiger la sécurité de session NTLMv2**  
  - **Exiger un chiffrement 128 bits**  
  - **Authentification NTLMv2 et chiffrement de 128 bits**  
 
- **Sécurité de session minimale pour serveur basé sur NTLM SSP**  
  **Valeur par défaut**: aucune  
  CSP LocalPoliciesSecurityOptions : [NetworkSecurity_MinimumSessionSecurityForNTLMSSPBasedServers](https://aka.ms/policy-csp-localpoliciessecurityoptions-networksecurity-minimumsessionsecurityforntlmsspbasedservers)  

  Ce paramètre de sécurité détermine le protocole d'authentification de stimulation/réponse utilisé pour les ouvertures de session réseau.  

  - **Aucune.**  
  - **Exiger la sécurité de session NTLMv2**  
  - **Exiger un chiffrement 128 bits**  
  - **Authentification NTLMv2 et chiffrement de 128 bits**  

- **Niveau d’authentification LAN Manager**  
  **Valeur par défaut**: LM et NTLM  
  CSP LocalPoliciesSecurityOptions : [NetworkSecurity_LANManagerAuthenticationLevel](https://aka.ms/policy-csp-localpoliciessecurityoptions-lanmanagerauthenticationlevel)  


  - **LM et NTLM**  
  - **LM, NTLM et NTLMv2**  
  - **NTLM**  
  - **Authentification**  
  - **NTLMv2 et non LM**  
  - **NTLMv2 et non LM ou NTLM**  
  
- **Connexions invitées non sécurisées**  
  **Par défaut** : Non configuré  
  Fournisseur de services de chiffrement LanmanWorkstation : [LanmanWorkstation](https://aka.ms/policy-csp-lanmanworkstation-enableinsecureguestlogons)  

  Si vous activez ce paramètre, le client SMB rejette les ouvertures de session invité non sécurisées.  

  - **Non configuré**  
  - **Bloquer** : le client SMB rejette les ouvertures de session invitées non sécurisées.  

### <a name="recovery-console-and-shutdown"></a>Console de récupération et arrêt  

- **Effacer le fichier d’échange de mémoire virtuelle pendant l’arrêt**  
  **Par défaut** : Non configuré  
   CSP LocalPoliciesSecurityOptions : [Shutdown_ClearVirtualMemoryPageFile](https://go.microsoft.com/fwlink/?linkid=867914)  


  - **Activer** : effacer le fichier d’échange de mémoire virtuelle quand l’appareil est mis hors tension.  
  - **Non configuré** : n’efface pas la mémoire virtuelle.  

- **Arrêt sans ouverture de session**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [Shutdown_AllowSystemToBeShutDownWithoutHavingToLogOn](https://go.microsoft.com/fwlink/?linkid=867912)  

  
  - **Bloquer** : masquer l’option d’arrêt sur l’écran d’ouverture de session Windows. Les utilisateurs doivent se connecter à l’appareil, puis l’arrêter.  
  - **Non configuré** : autoriser les utilisateurs à arrêter l’appareil à partir de l’écran d’ouverture de session Windows.  

### <a name="user-account-control"></a>Contrôle de compte d'utilisateur  

- **Intégrité UIA sans emplacement sécurisé**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867897)  
  
  - **Bloc** : les applications qui se trouvent dans un emplacement sécurisé dans le système de fichiers s’exécutent uniquement avec l’intégrité UIAccess.  
  - **Non configuré** : autorise les applications à s’exécuter avec l’intégrité UIAccess, même si elles ne se trouvent pas dans un emplacement sécurisé dans le système de fichiers.  

- **Virtualiser les échecs d’écriture de fichier et de Registre dans des emplacements par utilisateur**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations](https://go.microsoft.com/fwlink/?linkid=867900)  

  - **Désactivé** : les applications qui écrivent des données dans des emplacements protégés échouent.  
  - **Non configuré** : les échecs d’écriture d’application sont redirigés au moment de l’exécution vers des emplacements définis par l’utilisateur pour le système de fichiers et le registre.  

- **Élever uniquement les fichiers exécutables signés et validés**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations](https://go.microsoft.com/fwlink/?linkid=867965)  

  - **Activé** : appliquer la validation du chemin de certification PKI d’un fichier exécutable avant qu’il puisse s’exécuter.  
  - **Non configuré** : ne pas appliquer de validation de chemin de certificat PKI avant qu’un fichier exécutable puisse s’exécuter.  

#### <a name="uia-elevation-prompt-behavior"></a>Comportement de l’invite d’élévation UIA  

- **Invite d’élévation pour les administrateurs**  
  **Par défaut** : demande de consentement pour les binaires non Windows  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_BehaviorOfTheElevationPromptForAdministrators](https://go.microsoft.com/fwlink/?linkid=867895)  

  Définir le comportement de l’invite d’élévation pour les administrateurs en mode d’approbation Administrateur.  

  - **Non configuré**  
  - **Élever sans invite**  
  - **Demande d’informations d’identification sur le bureau sécurisé**  
  - **Demande d’informations d’identification**  
  - **Demande de consentement**  
  - **Demande de consentement pour les binaires non-Windows**  


- **Invite d’élévation pour les utilisateurs standard**  
  **Par défaut** : demande des informations d'identification  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_BehaviorOfTheElevationPromptForStandardUsers](https://go.microsoft.com/fwlink/?linkid=867896)  

  Définir le comportement de l’invite d’élévation pour les utilisateurs standard.  

  - **Non configuré**  
  - **Refuser automatiquement les demandes d’élévation de privilèges**  
  - **Demande d’informations d’identification sur le bureau sécurisé**  
  - **Demande d’informations d’identification**  

- **Router les invites d’élévation vers le Bureau interactif de l’utilisateur**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_SwitchToTheSecureDesktopWhenPromptingForElevation](https://go.microsoft.com/fwlink/?linkid=867899)  


  - **Activé** : toutes les demandes d’élévation pour aller sur le Bureau de l’utilisateur interactif plutôt que sur le Bureau sécurisé. Tous les paramètres de stratégie de comportement d’invite pour les administrateurs et les utilisateurs standard sont utilisés.  
  - **Non configuré** : forcer toutes les demandes d’élévation à passer au bureau sécurisé, quels que soient les paramètres de stratégie de comportement d’invite pour les administrateurs et les utilisateurs standard.

- **Invite avec élévation de privilèges pour les installations d’application**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_DetectApplicationInstallationsAndPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867901)  

   - **Désactivé** : les packages d’installation d’application ne sont pas détectés ni invités pour une élévation.
   - **Non configuré** : les utilisateurs sont invités à entrer un nom d’utilisateur et un mot de base d’administration quand un package d’installation d’application nécessite une élévation de privilège.

- **Invite d’élévation UIA sans Bureau sécurisé**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_AllowUIAccessApplicationsToPromptForElevation](https://go.microsoft.com/fwlink/?linkid=867894)  

- **Activer** : autoriser les applications UIAccess à demander l’élévation sans utiliser le bureau sécurisé.  
- **Non configuré** : les invites d’élévation utilisent un Bureau sécurisé.  

#### <a name="admin-approval-mode"></a>Mode d’approbation Administrateur  

- **Mode d’approbation Administrateur pour l’administrateur intégré**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_UseAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867902)  

  - **Activé** : autoriser le compte Administrateur intégré à utiliser le mode d’approbation Administrateur. Une invite d’approbation est présentée à l’utilisateur pour toute opération nécessitant une élévation de privilège.  
  - **Non configuré** : exécute toutes les applications avec des privilèges d’administrateur complets.  

- **Exécuter tous les administrateurs en mode d’approbation Administrateur**  
  **Par défaut** : non configuré  
  CSP LocalPoliciesSecurityOptions : [UserAccountControl_RunAllAdministratorsInAdminApprovalMode](https://go.microsoft.com/fwlink/?linkid=867898)  


  - **Activé**: activez le mode d’approbation administrateur.  
  - **Non configuré** : désactiver le mode d’approbation Administrateur et tous les paramètres de stratégie UAC associés.  

### <a name="microsoft-network-client"></a>Client réseau Microsoft  

- **Signer numériquement les communications (si le serveur accepte)**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [MicrosoftNetworkClient_DigitallySignCommunicationsIfServerAgrees](https://go.microsoft.com/fwlink/?linkid=868423)  

  détermine si le client SMB négocie la signature de paquet SMB.  
  - **Bloquer** : le client SMB ne négocie jamais la signature des paquets SMB.
  - **Non configuré** : le client réseau Microsoft demande au serveur d’effectuer la signature de paquet SMB lors de la configuration de la session. Si la signature de paquet est activée sur le serveur, la signature de paquet est négociée.  

- **Envoyer un mot de passe non chiffré aux serveurs SMB tiers**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [MicrosoftNetworkClient_SendUnencryptedPasswordToThirdPartySMBServers](https://go.microsoft.com/fwlink/?linkid=868426)  


  - **Bloquer** : le redirecteur Server Message Block (SMB) peut envoyer des mots de passe en clair aux serveurs SMB non-Microsoft qui ne prennent pas en charge le chiffrement de mot de passe lors de l’authentification.  
  - **Non configuré** -bloquer l’envoi de mots de passe en texte clair. Les mots de passe sont chiffrés.  

- **Signer numériquement les communications (toujours)**  
  **Par défaut** : Non configuré  
  CSP LocalPoliciesSecurityOptions : [MicrosoftNetworkClient_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868425)  


  - **Activer** : le client réseau Microsoft ne communique avec un serveur réseau Microsoft que si ce serveur accepte la signature de paquet SMB.  
  - **Non configuré** : la signature des paquets SMB est négociée entre le client et le serveur.  

### <a name="microsoft-network-server"></a>Serveur réseau Microsoft  
  
- **Signer numériquement les communications (si le client accepte)**  
  **Par défaut** : Non configuré  
  CSP : [MicrosoftNetworkServer_DigitallySignCommunicationsIfClientAgrees](https://go.microsoft.com/fwlink/?linkid=868429)  

  - **Activer** : le serveur réseau Microsoft négocie la signature de paquet SMB comme demandé par le client. Autrement dit, si la signature de paquet a été activée sur le client, la signature de paquet est négociée.  
  - **Non configuré** : le client SMB ne négocie jamais la signature des paquets SMB.  

- **Signer numériquement les communications (toujours)**  
  **Par défaut** : Non configuré  
  CSP : [MicrosoftNetworkServer_DigitallySignCommunicationsAlways](https://go.microsoft.com/fwlink/?linkid=868428)  

  - **Activer** : le serveur réseau Microsoft ne communique avec un client réseau Microsoft que si ce client accepte la signature de paquet SMB.  
  - **Non configuré** : la signature des paquets SMB est négociée entre le client et le serveur.  

## <a name="xbox-services"></a>Services Xbox

- **Tâche d’enregistrement du jeu Xbox**  
  **Par défaut** : Non configuré  
  CSP : [TaskScheduler/EnableXboxGameSaveTask](https://go.microsoft.com/fwlink/?linkid=875480)  
   
  Ce paramètre détermine si la tâche d’enregistrement du jeu Xbox est activée ou désactivée.  
  - **Enabled**
  - **Non configuré**

- **Service de gestion des accessoires Xbox**  
  **Par défaut**: Manuel  
  CSP : [SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875481)  

  Ce paramètre détermine le type de démarrage du service de gestion des accessoires.  
  - **Manuel**
  - **Automatique**
  - **Désactivé**

- **Service Xbox Live auth Manager**  
  **Par défaut**: Manuel  
  CSP : [SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875482)  
 
  Ce paramètre détermine le type de démarrage du service Live auth Manager.  
  - **Manuel**
  - **Automatique**
  - **Désactivé**
 
- **Service de sauvegarde de jeux Xbox Live**  
  **Par défaut**: Manuel  
  CSP : [SystemServices/ConfigureXboxLiveGameSaveServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875483)  

  Ce paramètre détermine le type de démarrage du service d’enregistrement de jeux en direct.  
  - **Manuel**
  - **Automatique**
  - **Désactivé**

- **Service de mise en réseau Xbox Live**  
  **Par défaut**: Manuel  
  CSP : [SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode](https://go.microsoft.com/fwlink/?linkid=875484)  

  Ce paramètre détermine le type de démarrage du service de mise en réseau.  
  - **Manuel**
  - **Automatique**
  - **Désactivé**

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. À présent, [affectez le profil](../configuration/device-profile-assign.md), puis [supervisez son état](../configuration/device-profile-monitor.md).  

Configurez les paramètres de protection des points de terminaison sur les appareils [macOS](endpoint-protection-macos.md).  
