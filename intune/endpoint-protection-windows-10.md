---
title: Ajouter Endpoint Protection sur Windows 10 dans Microsoft Intune - Azure | Microsoft Docs
description: Sur les appareils Windows 10, utilisez ou configurez les paramètres Endpoint Protection pour activer les fonctionnalités de Windows Defender, notamment Application Guard, Pare-feu, SmartScreen, le chiffrement et BitLocker, Exploit Guard, Contrôle d’application, Centre de sécurité, ainsi que la sécurité sur les appareils locaux dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a7c7ebca1c6472b58021a57b1b4a59fc42966b0
ms.sourcegitcommit: d8edd1c3d24123762dd6d14776836df4ff2a31dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51576951"
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Paramètres Endpoint Protection pour Windows 10 (et versions ultérieures) dans Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le profil Endpoint Protection vous permet de contrôler les fonctionnalités de sécurité sur les appareils Windows 10, telles que BitLocker et Windows Defender.

Utilisez les informations de cet article pour créer des profils Endpoint Protection. Pour configurer l’antivirus Windows Defender, consultez[Restrictions d’appareil Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus). 

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Pris en charge sur les éditions de Windows 10 suivantes :

- Enterprise 
- Professionnel

Lors de l’utilisation de Microsoft Edge, Windows Defender Application Guard protège votre environnement des sites qui ne sont pas approuvés par votre organisation. Quand des utilisateurs visitent des sites qui ne figurent pas dans la liste des limites de votre réseau isolé, les sites sont ouverts dans une session de navigation virtuelle Hyper-V. Les sites approuvés sont définis par une limite réseau, qui peut être configurée dans Configuration de l'appareil.

Application Guard est uniquement disponible pour les appareils Windows 10 (64 bits). L’utilisation de ce profil permet d’installer un composant Win32 pour activer Application Guard.

- **Application Guard** : **Activer** pour activer cette fonctionnalité, ce qui ouvre des sites non approuvés dans un conteneur de navigation virtualisé Hyper-V. **Non configuré** (valeur par défaut) signifie que n’importe quel site (approuvé et non approuvé) s’ouvre sur l’appareil.
- **Comportement du Presse-papiers** : choisissez les actions de copier-coller autorisées entre le PC local et le navigateur virtuel Application Guard.
- **Contenu externe sur les sites d’entreprise** : **Bloquer** le chargement du contenu des sites web non approuvés. **Non configuré** (valeur par défaut) signifie que les sites autres que les sites d’entreprise peuvent s’ouvrir sur l’appareil.
- **Imprimer à partir du navigateur virtuel** : **Autoriser** pour autoriser l’impression en PDF et en XPS, ainsi que les imprimantes locales et/ou réseau à imprimer du contenu à partir du navigateur virtuel. **Non configuré** (valeur par défaut) désactive toutes les fonctionnalités d’impression.
- **Collecter les journaux** : **Autoriser** pour collecter les journaux des événements qui se produisent dans une session de navigation Application Guard. **Non configuré** (valeur par défaut) ne collecte aucun journal dans la session de navigation.
- **Conserver les données du navigateur générées par l’utilisateur** : **Autoriser** enregistre les données utilisateur (comme les mots de passe, les favoris et les cookies) qui sont créées au cours d’une session de navigation virtuelle Application Guard. **Non configuré** (valeur par défaut) ignore les données et les fichiers téléchargés par l’utilisateur lors du redémarrage de l’appareil ou quand un utilisateur se déconnecte.
- **Accélération graphique** : **Activer** pour charger des sites web utilisant beaucoup de graphiques et aux performances vidéo plus rapides en obtenant l’accès à une unité de traitement graphique virtuelle. **Non configuré** (valeur par défaut) utilise le processeur de l’appareil pour les graphiques. Il n’utilise pas l’unité de traitement graphique virtuelle.
- **Télécharger les fichiers sur le système de fichiers hôte** : **Activer** pour que les utilisateurs téléchargent des fichiers à partir du navigateur virtualisé sur le système d’exploitation hôte. **Non configuré** (valeur par défaut) conserve les fichiers en local sur l’appareil et n’en télécharge pas sur le système de fichiers hôte.

## <a name="windows-defender-firewall"></a>Pare-feu Windows Defender

Pris en charge sur les éditions de Windows 10 suivantes :
- Accueil
- Professionnel
- Professionnel
- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

### <a name="global-settings"></a>Paramètres globaux

Ces paramètres s’appliquent à tous les types de réseaux.

- **Protocole FTP** : **Bloquer** pour désactiver le protocole FTP avec état. Quand **Non configuré** (valeur par défaut) est sélectionné, le pare-feu fait FTP avec état, le filtrage pour autoriser les connexions secondaires.
- **Durée d’inactivité des associations de sécurité avant suppression** : les associations de sécurité sont supprimées si aucun trafic réseau n’est visible pendant *n* secondes. Entrez une durée d’inactivité, en secondes.
- **Codage des clés prépartagées** : **Activer** pour utiliser le codage des clés prépartagées avec UTF-8. **Non configuré** (valeur par défaut) utilise la valeur du magasin local.
- **Exemptions IPsec** : configurez un trafic spécifique pour être exempté d’IPsec, notamment :
  - **Codes type ICMP IPv6 de découverte de voisin**
  - **ICMP**
  - **Codes type ICMP IPv6 de découverte de routeur**
  - **Trafic réseau DHCP IPv4 et IPv6**
- **Vérification de la liste de révocation de certificats** : déterminez comment la vérification de la liste de révocation de certificats est appliquée, notamment **Désactiver la vérification de la liste de révocation de certificats**, **Échec de vérification de la liste de révocation de certificats sur le certificat révoqué uniquement** et **Échec de vérification de la liste de révocation de certificats pour toute erreur rencontrée**.
- **Associer le jeu d’authentification de façon opportuniste par module de génération de clés** : **Activer** pour OBLIGER les modules de génération de clés à ignorer uniquement les suites d’authentification qu’ils ne prennent pas en charge. Quand ce paramètre a la valeur**Non configuré**, les modules de génération de clés DOIVENT ignorer la totalité du jeu d’authentification s’ils ne prennent pas en charge toutes les suites de l’authentification spécifiées dans le jeu.
- **Mise en file d’attente des paquets** : indiquez comment la mise à l’échelle des logiciels côté réception est activée pour la réception chiffrée et efface le texte pour le scénario de passerelle du tunnel IPsec. Ce paramètre garantit la préservation de l’ordre des paquets.

### <a name="network-settings"></a>Paramètres du réseau

Ces paramètres s’appliquent à des types de réseaux spécifiques, notamment **Réseau (espace de travail) avec domaine**, **Réseau privé (détectable)** et **Réseau public (non détectable)**.

#### <a name="general-settings"></a>Paramètres généraux :

- **Pare-feu Windows Defender** : **Activer** pour activer le pare-feu et les fonctions de sécurité avancées. **Non configuré** (valeur par défaut) autorise tout le trafic réseau, quels que soit les autres paramètres de stratégie.
- **Mode furtif** : **Bloquer** le fonctionnement du pare-feu en mode furtif. Le blocage du mode furtif vous permet de bloquer également **Exemption de paquets sécurisés IPsec**. **Non configuré** (valeur par défaut) fait fonctionner le pare-feu en mode furtif, ce qui permet d’empêcher les réponses aux demandes de détection.
- **Protégé** : **Bloquer** désactive cette fonctionnalité. **Non configuré** (valeur par défaut) active ce paramètre. Quand ce paramètre et le pare-feu Windows Defender sont activés, tout le trafic entrant est bloqué, quels que soit les autres paramètres de stratégie.
- **Réponses en monodiffusion au trafic en multidiffusion** : quand ce paramètre a la valeur **Bloquer**, elle désactive les réponses en monodiffusion au trafic en multidiffusion. En règle générale, vous ne souhaitez pas recevoir des réponses en monodiffusion à des messages de multidiffusion ou de diffusion. Ces réponses peuvent indiquer une attaque par déni de service ou un attaquant qui tente de sonder un ordinateur actif connu. **Non configuré** (valeur par défaut) active ce paramètre.
- **Notifications entrantes** : quand ce paramètre a la valeur **Bloquer**, il masque les notifications pour les utilisateurs lors du blocage d’une application pour écouter sur un port. **Non configuré** (valeur par défaut) active ce paramètre et peut afficher une notification aux utilisateurs lors du blocage d’une application pour écouter sur un port.
- **Action par défaut pour les connexions entrantes** : quand ce paramètre a la valeur **Bloquer**, l’action de pare-feu par défaut n’est pas exécutée sur les connexions entrantes. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), l’action de pare-feu par défaut est exécutée sur les connexions entrantes.

#### <a name="rule-merging"></a>Fusion des règles

- **Règles de pare-feu Windows Defender d’application autorisées du magasin local** : **Activer** pour appliquer des règles de pare-feu du magasin local à reconnaître et à appliquer. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les règles de pare-feu d’applications autorisées du magasin local sont ignorées et non appliquées.
- **Règles de pare-feu Windows Defender de port globales du magasin local** : **Activer** pour appliquer des règles de pare-feu de port globales du magasin local à reconnaître et à appliquer. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les règles de pare-feu de port globales du magasin local sont ignorées et non appliquées.
- **Règles de pare-feu Windows Defender du magasin local** : **Activer** pour appliquer des règles de pare-feu du magasin local à reconnaître et à appliquer. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les règles de pare-feu du magasin local sont ignorées et non appliquées.
- **Règles IPsec du magasin local** : **Activer** pour appliquer les règles de sécurité de connexion du magasin local, quelles que soient les versions des règles de sécurité de connexion ou du schéma. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les règles de sécurité de connexion du magasin local sont ignorées et ne sont pas appliquées, quelles que soient la version du schéma et la version des règles de sécurité de connexion.

## <a name="windows-defender-smartscreen-settings"></a>Paramètres Windows Defender SmartScreen

Pris en charge sur les éditions de Windows 10 sur lesquelles Microsoft Edge est installé :
- Accueil
- Professionnel
- Professionnel
- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

**Paramètres** :

- **SmartScreen pour les applications et fichiers** : **Activer** Windows SmartScreen pour l’exécution de fichiers et d’applications. SmartScreen est un composant cloud anti-hameçonnage et anti-programme malveillant. **Non configuré** (valeur par défaut) désactive SmartScreen.
- **Exécution de fichiers non vérifiés** : **Bloquer**  permet d’empêcher les utilisateurs finaux d’exécuter des fichiers qui n’ont pas été vérifiés par Windows SmartScreen. **Non configuré** (valeur par défaut) désactive cette fonctionnalité et permet aux utilisateurs finaux d’exécuter des fichiers qui n’ont pas été vérifiés.

## <a name="windows-encryption"></a>Chiffrement Windows

### <a name="windows-settings"></a>Paramètres Windows

Pris en charge sur les éditions de Windows 10 suivantes :

- Professionnel
- Professionnel
- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

**Paramètres** :

- **Chiffrer les appareils** : **Exiger** pour demander aux utilisateurs d’activer le chiffrement des appareils. En fonction de l’édition de Windows et de la configuration du système, les utilisateurs peuvent être invités à :  
  - Vérifier que le chiffrement d’un autre fournisseur n’est pas activé
  - Être amenés à désactiver le chiffrement de lecteur Bitlocker, puis à réactiver Bitlocker
    
    Si le chiffrement Windows est activé alors qu’une autre méthode de chiffrement est active, l’appareil peut devenir instable. 
- **Chiffrer la carte de stockage (mobile uniquement)** : **Exiger** le chiffrement de toutes les cartes de stockage amovibles utilisées par l’appareil. **Non configuré** (valeur par défaut) n’exige pas le chiffrement des cartes de stockage et n’invite pas l’utilisateur à l’activer. Ce paramètre s’applique uniquement aux appareils mobiles Windows 10.

### <a name="bitlocker-base-settings"></a>Paramètres de base BitLocker

Pris en charge sur les éditions de Windows 10 suivantes :

- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

Les paramètres de base correspondent aux paramètres BitLocker universels pour tous les types de lecteurs de données. Ces paramètres permettent de gérer les options de configuration ou les tâches de chiffrement de lecteur modifiables par l’utilisateur final pour tous les types de lecteurs de données.

- **Avertissement pour tout autre chiffrement de disque** : sélectionnez **Bloquer** pour désactiver l’invite d’avertissement si un autre service de chiffrement de disque se trouve sur l’appareil. **Non configuré** (valeur par défaut) permet l’affichage de l’avertissement.
- **Configurer les méthodes de chiffrement** : **Activer** ce paramètre pour configurer des algorithmes de chiffrement pour le système d’exploitation, les données et les lecteurs amovibles. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), BitLocker utilise XTS-AES 128 bits comme méthode de chiffrement par défaut, ou utilise la méthode de chiffrement spécifiée par tout script d’installation.
  - **Chiffrement pour les lecteurs du système d’exploitation** : choisissez la méthode de chiffrement pour les lecteurs de système d’exploitation. Nous vous recommandons d’utiliser l’algorithme AES-XTS.
  - **Chiffrement pour les lecteurs de données fixes** : choisissez la méthode de chiffrement pour les lecteurs de données fixes (intégrés). Nous vous recommandons d’utiliser l’algorithme AES-XTS.
  - **Chiffrement pour les lecteurs de données amovibles** : choisissez la méthode de chiffrement pour les lecteurs de données amovibles. Si le lecteur amovible est utilisé avec des appareils qui n’exécutent pas Windows 10, nous vous recommandons d’utiliser l’algorithme AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Paramètres de lecteur du système d’exploitation BitLocker
Pris en charge sur les éditions de Windows 10 suivantes :

- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

Ces paramètres s’appliquent spécifiquement aux lecteurs de données de système d’exploitation.

- **Authentification supplémentaire au démarrage** : sélectionnez **Exiger** pour configurer les conditions d’authentification pour le démarrage de l’ordinateur, notamment l’utilisation du module de plateforme sécurisée (TPM). Sélectionnez **Non configuré** (valeur par défaut) pour configurer uniquement les options de base sur les appareils dotés d’un module TPM.
  - **BitLocker avec puce TPM non compatible** : **Bloquer** (désactiver) à l’aide de BitLocker quand un appareil ne dispose pas d’une puce TPM compatible. Quand ce paramètre a la valeur **Non configuré**, les utilisateurs peuvent utiliser BitLocker sans puce TPM compatible. BitLocker peut exiger un mot de passe ou une clé de démarrage.
  - **Démarrage du module TPM compatible** : indiquez si la puce TPM est autorisée, non autorisée ou obligatoire.
  - **Code PIN de démarrage du module TPM compatible** : indiquez si l’utilisation d’un code PIN de démarrage avec la puce TPM est autorisée, non autorisée ou obligatoire. L’activation d’un code confidentiel de démarrage nécessite une intervention de l’utilisateur final. 
  - **Clé de démarrage du module TPM compatible** : indiquez si l’utilisation d’une clé de démarrage avec la puce TPM est autorisée, non autorisée ou obligatoire. L’activation d’une clé de démarrage nécessite une intervention de l’utilisateur final. 
  - **Code PIN et clé de démarrage du module TPM compatible** : indiquez si l’utilisation d’un code PIN et d’une clé de démarrage avec la puce TPM est autorisée, non autorisée ou obligatoire. L’activation d’une clé de démarrage et d’un code confidentiel de démarrage nécessite une intervention de l’utilisateur final.
- **Longueur minimale du code PIN** : **Activer** ce paramètre pour configurer une longueur minimale pour le code PIN de démarrage de TPM. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les utilisateurs peuvent configurer un code confidentiel de démarrage d’une longueur comprise entre 6 et 20 chiffres.
  - **Nombre minimal de caractères** : entrez le nombre de caractères obligatoires pour le code PIN de démarrage (**4**-**20**).
- **Récupération du lecteur du système d’exploitation** : **Activer** ce paramètre pour contrôler la façon dont les lecteurs de système d’exploitation protégés par BitLocker sont récupérés quand les informations de démarrage nécessaires ne sont pas disponibles. Quand la valeur de ce paramètre **Non configuré** (valeur par défaut), les options de récupération par défaut sont prises en charge pour la récupération BitLocker. Par défaut, un agent de récupération de données (DRA) est autorisé. Les options de récupération sont spécifiées par l’utilisateur, notamment le mot de passe de récupération et la clé de récupération, et les informations de récupération ne sont pas sauvegardées dans AD DS.
  - **Agent de récupération de données basé sur les certificats** : quand ce paramètre a la valeur **Bloquer**, vous ne pouvez pas utiliser l’agent de récupération de données avec des lecteurs de système d’exploitation protégés par BitLocker. Définissez la valeur **Non configuré** (valeur par défaut) pour activer ce paramètre, ce qui permet d’utiliser des agents de récupération de données avec les lecteurs de système d’exploitation protégés par BitLocker.
  - **Création d’un mot de passe de récupération par l’utilisateur** : indiquez si les utilisateurs sont autorisés, non autorisés ou contraints à générer un mot de passe de récupération de 48 chiffres.
  - **Création d’une clé de récupération par l’utilisateur** : indiquez si les utilisateurs sont autorisés, non autorisés ou contraints à générer une clé de récupération de 256 bits.
  - **Options de récupération dans l’Assistant Installation de BitLocker** : définissez ce paramètre sur **Bloquer** pour que les utilisateurs ne puissent pas voir ni changer les options de récupération. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les utilisateurs peuvent voir et changer les options de récupération quand ils activent BitLocker.
  - **Enregistrer les informations de récupération BitLocker dans AD DS** : **Activer** pour stocker les informations de récupération BitLocker dans Azure Active Directory (AAD). Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les informations de récupération ne sont pas stockées dans AAD.
  - **Informations de récupération BitLocker stockées dans AD DS** : configurez les parties des informations de récupération BitLocker qui sont stockées dans Azure AD. Choisissez parmi :
    - **Sauvegarder les mots de passe et les jeux de clés de récupération**
    - **Sauvegarder les mots de passe de récupération uniquement**
  - **Stocker les informations de récupération dans AD DS avant l’activation de BitLocker** : **Exiger** la définition de ce paramètre pour empêcher les utilisateurs d’activer BitLocker, sauf si les informations de récupération BitLocker sont correctement stockées dans Azure Active Directory. **Non configuré** (valeur par défaut) permet aux utilisateurs d’activer BitLocker, même si les informations de récupération ne sont pas correctement stockées dans Azure Active Directory.
- **Message et URL de récupération préalables au démarrage** : **Activer** ce paramètre pour configurer le message et l’URL qui s’affichent sur l’écran de récupération de clé préalable au démarrage. **Non configuré** (valeur par défaut) désactive cette fonctionnalité.
  - **Message de récupération préalable au démarrage** : configurez la façon dont le message de récupération préalable au démarrage est présenté aux utilisateurs. Choisissez parmi :
    - **Utiliser le message et l’URL de récupération par défaut**
    - **Utiliser un message et une URL de récupération vides**
    - **Utiliser le message de récupération personnalisé**
    - **Utiliser l’URL de récupération personnalisée**

### <a name="bitlocker-fixed-data-drive-settings"></a>Paramètres BitLocker des lecteurs de données fixes

Pris en charge sur les éditions de Windows 10 suivantes :

- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

**Paramètres** :

- **Accès en écriture à un lecteur de données fixe non protégé par BitLocker** : définissez la valeur **Bloquer** pour octroyer l’accès en lecture seule aux lecteurs de données qui ne sont protégés par BitLocker. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les lecteurs de données qui ne sont pas protégés par BitLocker bénéficient d’un accès en lecture et écriture.
- **Récupération d’un lecteur fixe** : **Activer** ce paramètre pour contrôler la façon dont les lecteurs fixes protégés par BitLocker sont récupérés quand les informations de démarrage nécessaires ne sont pas disponibles. **Non configuré** (valeur par défaut) désactive cette fonctionnalité.
  - **Agent de récupération de données** : **Bloquer** l’utilisation de l’agent de récupération de données avec l’Éditeur de stratégie des lecteurs fixes protégés par BitLocker. **Non configuré** (valeur par défaut) permet d’utiliser des agents de récupération de données avec des lecteurs fixes protégés par BitLocker.
  - **Création d’un mot de passe de récupération par l’utilisateur** : configurez si les utilisateurs sont autorisés, non autorisés ou contraints à générer un mot de passe de récupération de 48 chiffres.  
  - **Création d’une clé de récupération par l’utilisateur** : configurez si les utilisateurs sont autorisés, non autorisés ou contraints à générer une clé de récupération de 256 bits.
  - **Options de récupération dans l’Assistant Installation de BitLocker** : définissez ce paramètre sur **Bloquer** pour que les utilisateurs ne puissent pas voir ni changer les options de récupération. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les utilisateurs peuvent voir et changer les options de récupération quand ils activent BitLocker.
  - **Enregistrer les informations de récupération BitLocker dans AD DS** : **Activer** pour stocker les informations de récupération BitLocker dans Azure Active Directory (AAD). Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les informations de récupération ne sont pas stockées dans AAD.
  - **Informations de récupération BitLocker dans AD DS** : configurez les parties des informations de récupération BitLocker qui sont stockées dans Azure Active Directory. Choisissez parmi :
    - **Sauvegarder les mots de passe et les jeux de clés de récupération**
    - **Sauvegarder les mots de passe de récupération uniquement**
  - **Stocker les informations de récupération dans AD DS avant l’activation de BitLocker** : **Exiger** la définition de ce paramètre pour empêcher les utilisateurs d’activer BitLocker, sauf si les informations de récupération BitLocker sont correctement stockées dans Azure Active Directory. **Non configuré** (valeur par défaut) permet aux utilisateurs d’activer BitLocker, même si les informations de récupération ne sont pas correctement stockées dans Azure Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Paramètres BitLocker des lecteurs de données amovibles

Pris en charge sur les éditions de Windows 10 suivantes :

- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

**Paramètres** :

- **Accès en écriture à un lecteur de données amovibles non protégé par BitLocker** : définissez la valeur **Bloquer** pour octroyer l’accès en lecture seule aux lecteurs de données qui ne sont protégés par BitLocker. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les lecteurs de données qui ne sont pas protégés par BitLocker bénéficient d’un accès en lecture et écriture.
  - **Accès en écriture aux appareils configurés dans une autre organisation** : la valeur **Bloquer** autorise l’accès en écriture pour les appareils configurés dans une autre organisation. **Non configuré** (valeur par défaut) refuse l’accès en écriture.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Pris en charge sur les éditions de Windows 10 suivantes :

- Accueil
- Professionnel
- Professionnel
- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

Utilisez [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) pour gérer et réduire la surface d’attaque des applications utilisées par vos employés.

### <a name="attack-surface-reduction"></a>Règles de réduction de la surface d’attaque

- **Marquer le vol des informations d’identification du sous-système de l’autorité de sécurité locale Windows**

  Cette fonctionnalité contribue à [empêcher les actions et les applications](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) généralement utilisées par les programmes malveillants pour infecter les ordinateurs.

#### <a name="rules-to-prevent-office-macro-threats"></a>Règles pour empêcher les menaces sur les macros Office

Empêchez les applications Office d’effectuer les actions suivantes :

- **Applications Office effectuant des injections dans d’autres processus (aucune exception)**
- **Applications/macros Office créant du contenu exécutable**
- **Applications Office lançant des processus enfants**
- **Importations Win32 de code macro Office**

#### <a name="rules-to-prevent-script-threats"></a>Règles pour empêcher les menaces sur les scripts

Bloquez les éléments suivants pour empêcher les menaces sur les scripts :

- **Code js/vbs/ps/macro brouillé**
- **js/vbs, exécution de la charge utile téléchargée à partir d’Internet (aucune exception)**
- **Création de processus à partir des commandes PSExec et WMI**
- **Processus non approuvés et non signés exécutés à partir d’USB**
- **Fichiers exécutables qui ne répondent pas à des critères de prédominance, d’âge ou de liste approuvée**

#### <a name="rules-to-prevent-email-threats"></a>Règles pour empêcher les menaces sur les e-mails

Bloquez ce qui suit pour empêcher les menaces sur les e-mails :

- **Exécution du contenu exécutable (exe, dll, ps, js, vbs, etc.) supprimé de la messagerie (messagerie web/client de messagerie) (aucune exception)**

#### <a name="rules-to-protect-against-ransomware"></a>Règles de protection contre les ransomware
- **Protection avancée contre les ransomware**

> [!TIP]
> Pour plus d’informations sur ces règles, consultez [Reduce attack surfaces with Windows Defender Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) (Réduire les surfaces d’attaque avec Windows Defender Exploit Guard).

#### <a name="attack-surface-reduction-exceptions"></a>Exceptions de la réduction de surface d’attaque

- **Fichiers et dossiers à exclure des règles de réduction de la surface d’attaque** : importez/ajoutez une liste d’emplacements à exclure des règles configurées.

### <a name="controlled-folder-access"></a>Accès contrôlé aux dossiers

Protégez vos données importantes contre des applications malveillantes et des menaces, telles que les ransomware.

- **Protection des dossiers** : protégez les fichiers et dossiers contre des modifications indésirables apportées par des applications malveillantes. Vous pouvez importer une **liste des applications qui ont accès aux dossiers protégés** ou les ajouter manuellement. Vous pouvez également ajouter une **liste de dossiers supplémentaires qui doivent être protégés** par un chargement ou les ajouter manuellement.

### <a name="network-filtering"></a>Filtrage du réseau

Bloquez les connexions sortantes de toutes les applications aux adresses IP/domaines de faible réputation.

### <a name="exploit-protection"></a>Exploit Protection

Pour activer Exploit Protection, créez un fichier XML qui inclut les paramètres d’atténuation du système et des applications souhaités. Deux options sont disponibles :

 1. PowerShell : utilisez une ou plusieurs des applets de commande PowerShell (Get-ProcessMitigation, Set-ProcessMitigation et ConvertTo-ProcessMitigationPolicy). Les applets de commande permettent de configurer les paramètres d’atténuation et de les exporter sous forme d’une représentation XML.

 2. Interface utilisateur du Centre de sécurité Windows Defender : dans le Centre de sécurité Windows Defender, cliquez sur Contrôle des applications et du navigateur, puis faites défiler l’écran vers le bas jusqu’à Exploit Protection. Utilisez d’abord les onglets Paramètres système et Paramètres du programme pour configurer les paramètres d’atténuation. Recherchez ensuite le lien Exporter les paramètres en bas de l’écran pour les exporter sous forme d’une représentation XML.

Bloquez les **modifications par l’utilisateur de l’interface d’Exploit Protection** en chargeant un fichier XML qui vous permet de configurer des restrictions au niveau de la mémoire, du flux de contrôle et des stratégies. Les paramètres du fichier XML permettent de protéger une application contre les attaques. **Non configuré** (valeur par défaut) ne transmet pas une configuration personnalisée. 

## <a name="windows-defender-application-control"></a>Contrôle d’application Windows Defender

Pris en charge sur les éditions de Windows 10 suivantes :

**Gestion des appareils mobiles (MDM)** : 
- Professionnel
- Professionnel
- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

**Gestion des stratégies de groupe** : 
- Enterprise

Utilisez **Stratégies d’intégrité du code de contrôle des applications** pour choisir d’autres applications qui sont auditées ou dont l’exécution est approuvée par le contrôle d’application Windows Defender. L’exécution des composants Windows et de toutes les applications du Windows Store est automatiquement approuvée.

Les applications ne sont pas bloquées quand elles s’exécutent en mode **Auditer uniquement**. Le mode **Auditer uniquement** enregistre tous les événements dans les journaux du client local.

Une fois activé, le contrôle d’application peut être désactivé uniquement en changeant le mode **Appliquer** en **Auditer uniquement**. Quand vous changez le mode **Appliquer** en **Non configuré**, le contrôle d’application continue à s’appliquer sur les appareils attribués.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard

Pris en charge sur les éditions de Windows 10 suivantes :

- Enterprise

Windows Defender Credential Guard protège contre le vol d’informations d’identification. Il isole les clés secrètes afin que seuls les logiciels système privilégiés puissent y accéder.

Les paramètres **Credential Guard** incluent :

- **Désactiver** : désactive Credential Guard à distance s’il a été préalablement activé avec l’option **Activé sans verrouillage UEFI**.

- **Activer avec le verrouillage UEFI** : Credential Guard ne peut pas être désactivé à distance à l’aide d’une clé de Registre ou d’une stratégie de groupe.

    > [!NOTE]
    > Si vous utilisez ce paramètre et souhaitez ultérieurement désactiver Credential Guard, vous devez définir la stratégie de groupe sur **Désactivé**. Vous devez également effacer physiquement les informations de configuration UEFI sur chaque ordinateur. Tant que la configuration UEFI persiste, Credential Guard est activé.

- **Activer sans verrouillage UEFI** : permet de désactiver Credential Guard à distance à l’aide d’une stratégie de groupe. Les appareils utilisant ce paramètre doivent exécuter Windows 10 (version 1511) et versions ultérieures.

Lorsque vous activez Credential Guard, les fonctionnalités requises suivantes sont également activées :

- **Sécurité basée sur la virtualisation** (VBS) : s’active au prochain redémarrage. La sécurité basée sur la virtualisation utilise l’hyperviseur Windows pour prendre en charge les services de sécurité.
- **Démarrage sécurisé avec accès direct à la mémoire** : active VBS avec les protections Démarrage sécurisé et Accès direct à la mémoire (DMA). Les protections DMA nécessitent une prise en charge matérielle et sont uniquement activées sur des appareils configurés correctement.

## <a name="windows-defender-security-center"></a>Centre de sécurité Windows Defender

Pris en charge sur les éditions de Windows 10 suivantes :

- Accueil
- Professionnel
- Professionnel
- Enterprise
- Éducation
- Mobile
- Mobile Entreprise

Le Centre de sécurité Windows Defender fonctionne comme une application ou un processus distinct de chacune des fonctionnalités individuelles. Elle affiche des notifications dans le centre de notifications. Elle agit comme un collecteur de données ou emplacement unique pour afficher l’état et configurer chacune des fonctionnalités. Vous trouverez plus d’informations dans la documentation [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>Application Centre de sécurité Windows Defender et notifications

Empêchez l’utilisateur final d’accéder aux différentes zones de l’application Centre de sécurité Windows Defender. Le masquage d’une section bloque également les notifications associées.

- **Protection contre les virus et menaces**
- **Performances des appareils et intégrité**
- **Pare-feu et protection du réseau**
- **Contrôle des applications et du navigateur**
- **Options de contrôle parental**
- **Notifications des zones affichées de l’application** : choisissez les notifications à afficher aux utilisateurs finaux. Les notifications non critiques sont notamment les récapitulatifs d’activité de l’antivirus Windows Defender, dont les notifications indiquant qu’une analyse est terminée. Toutes les autres notifications sont considérées comme critiques.

#### <a name="it-contact-information"></a>Informations de contact du service informatique

Indiquez les informations de contact du service informatique à afficher dans l’application Centre de sécurité Windows Defender et ses notifications. Vous avez le choix entre **Afficher dans l’application et dans les notifications**, **Afficher uniquement dans l’application**, **Afficher uniquement dans les notifications** ou **Ne pas afficher**. Entrez le **nom de l’organisation du service informatique** et au moins l’une des options de contact suivantes :

- **Numéro de téléphone ou ID Skype du service informatique**
- **Adresse e-mail du service informatique**
- **URL du site web de support informatique**

## <a name="local-device-security-options"></a>Option de sécurité de l’appareil local

Pris en charge sur les éditions de Windows 10 suivantes :
 
- Accueil
- Professionnel
- Professionnel
- Enterprise
- Éducation

Utilisez ces options pour configurer les paramètres de sécurité locale sur les appareils Windows 10.

### <a name="accounts"></a>Comptes

- **Ajouter de nouveaux comptes Microsoft** : définissez la valeur **Bloquer** pour empêcher les utilisateurs d’ajouter de nouveaux comptes Microsoft sur cet appareil. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les utilisateurs peuvent utiliser des comptes Microsoft sur l’appareil.
- **Connexion à distance sans mot de passe** : **Activer** permet à des comptes locaux avec des mots de passe vides pour se connecter à l’aide du clavier de l’appareil. **Non configuré** (valeur par défaut) autorise les comptes locaux avec des mots de passe vides à se connecter à partir d’emplacements autres que l’appareil physique.

#### <a name="admin"></a>Administrateur

- **Compte Administrateur local** : définissez la valeur **Activé** pour autoriser le compte d’administrateur local. Définissez la valeur **Non configuré** (valeur par défaut) pour désactiver le compte d’administrateur local.
- **Renommer un compte Administrateur** : définit un autre nom de compte à associer à l’identificateur de sécurité (SID) pour le compte administrateur.

#### <a name="guest"></a>Invité

- **Compte invité** : définissez la valeur **Activé** pour autoriser le compte Invité local. Définissez la valeur **Non configuré** (valeur par défaut) pour désactiver le compte Invité local.
- **Renommer le compte Invité** : définit un autre nom de compte à associer à l’identificateur de sécurité (SID) pour le compte Invité.

### <a name="devices"></a>Appareils

- **Retirer l’appareil de la station d’accueil sans ouverture de session** : définissez la valeur **Bloquer** pour permettre aux utilisateurs d’appuyer sur le bouton d’éjection physique d’un appareil portable placé sur une station d’accueil afin de retirer l’appareil de manière sécurisée. **Non configuré** (valeur par défaut) oblige l’utilisateur à se connecter à l’appareil et à être autorisé à retirer l’appareil.
- **Installer des pilotes d’imprimante pour les imprimantes partagées** : quand ce paramètre a la valeur **Activé**, n’importe quel utilisateur peut installer un pilote d’imprimante lors de la connexion à une imprimante partagée. Quand **Non configuré** (valeur par défaut) est défini, seuls les administrateurs peuvent installer un pilote lors de la connexion à une imprimante partagée.
- **Autoriser l’accès au CD-ROM uniquement aux utilisateurs ayant ouvert une session localement** : quand ce paramètre a la valeur **Activé**, seul l’utilisateur connecté de manière interactive peut utiliser le CD-ROM. Si cette stratégie est activée et qu’aucun utilisateur n’est connecté de façon interactive, le CD-ROM est accessible sur le réseau. Quand la valeur définie est **Non configuré** (valeur par défaut), tout le monde a accès au CD-ROM.
- **Permettre le formatage et l’éjection des médias amovibles** : définit les personnes autorisées à formater et à éjecter un support NTFS amovible :
  - **Non configuré**
  - **Administrateurs**
  - **Administrateurs et utilisateurs avec pouvoir**
  - **Administrateurs et utilisateurs interactifs**

### <a name="interactive-logon"></a>Ouverture de session interactive

- **Minutes d’inactivité de l’écran de veille avant que l’économiseur d’écran s’active** : entrez le nombre maximal de minutes d’inactivité sur l’écran de connexion du bureau interactif avant l’apparition de l’économiseur d’écran.
- **Nécessiter CTRL+ALT+DEL pour ouvrir une session** : définissez la valeur **Activer** afin que les utilisateurs n’aient pas à appuyer sur CTRL+ALT+SUPPR pour se connecter. Définissez la valeur **Non configuré** (valeur par défaut) pour obliger les utilisateurs à appuyer sur CTRL+ALT+SUPPR avant de se connecter à Windows.
- **Comportement en cas de suppression de la carte à puce** : détermine ce qui se passe quand la carte à puce d’un utilisateur connecté est retirée du lecteur de carte à puce. Les options disponibles sont les suivantes :

  - **Verrouiller la station de travail** : la station de travail est verrouillée quand la carte à puce est retirée. Cette option permet aux utilisateurs de quitter les lieux, d’emporter leur carte à puce et de conserver une session protégée.
  - **Forcer la fermeture de session** : l’utilisateur est automatiquement déconnecté quand la carte à puce est retirée.
  - **Déconnecter en cas de session des services Bureau à distance** : le retrait de la carte à puce déconnecte la session sans déconnecter l’utilisateur. Cette option permet à l’utilisateur d’insérer la carte à puce et de reprendre la session ultérieurement, ou sur un autre ordinateur équipé d’un lecteur de carte à puce, sans avoir à se reconnecter. Si la session est locale, cette stratégie fonctionne comme l’option Verrouiller la station de travail.

    Les [options LocalPoliciesSecurity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) fournissent plus de détails.

#### <a name="display"></a>Afficher

- **Informations utilisateur sur l’écran de verrouillage** : configure les informations de l’utilisateur qui apparaissent lorsque la session est verrouillée. Si cette option n’est pas configurée, le nom d’utilisateur, le domaine et le nom d’utilisateur complet sont affichés.
  - **Non configuré**
  - **Nom d’affichage de l’utilisateur, domaine et nom d’utilisateur**
  - **Nom d'affichage de l'utilisateur uniquement**
  - **Ne pas afficher les informations utilisateur**
- **Masquer le dernier utilisateur connecté** : **Activer** masque le nom d’utilisateur. **Non configuré** (valeur par défaut) affiche le nom d’utilisateur.
- **Masquer le nom d’utilisateur lors de la connexion** : **Activer** masque le nom d’utilisateur. **Non configuré** (valeur par défaut) affiche le nom d’utilisateur.
- **Titre du message de connexion** : définissez le titre du message pour les utilisateurs se connectant.
- **Texte du message de connexion** : définissez le texte du message pour les utilisateurs se connectant.

### <a name="network-access-and-security"></a>Accès réseau et sécurité

- **Accès anonyme aux canaux nommés et aux partages** : **Non configuré** (valeur par défaut) restreint l’accès anonyme aux paramètres de partage et de canal nommé. S’applique aux paramètres accessibles de manière anonyme.
- **Énumération anonyme des comptes SAM** : **Autoriser** les utilisateurs anonymes à énumérer les comptes SAM. Windows autorise les utilisateurs anonymes à énumérer les noms des comptes de domaine et les partages réseau.
- **Énumération anonyme des comptes SAM** : **Non configuré** (valeur par défaut) signifie que des utilisateurs anonymes peuvent énumérer les noms des comptes de domaine et des partages réseau. Pour empêcher l’énumération anonyme des comptes et partages SAM, définissez cette option sur **Bloquer**.
- **Valeur de hachage LAN Manager stockée lors du changement de mot de passe** : lors du prochain changement du mot de passe, choisissez d’**Autoriser** LAN Manager (LM) à stocker la valeur de hachage du nouveau mot de passe. Quand la valeur définie est **Non configuré** (valeur par défaut), la valeur de hachage n’est pas stockée.
- **Demandes d’authentification PKU2U** : **Bloquer** les demandes d’authentification PKU2U auprès de l’appareil afin d’utiliser des identités en ligne. **Non configuré** (valeur par défaut) autorise ces demandes.
- **Restreindre les connexions RPC distantes à SAM** : **Autoriser** la chaîne SDDL (Security Descriptor Definition Language) par défaut à empêcher les utilisateurs et groupes d’effectuer des appels à distance au SAM. **Non configuré** (valeur par défaut) permet à la chaîne SDDL (Security Descriptor Definition Language) d’autoriser les utilisateurs et groupes à effectuer des appels à distance au SAM.
  - **Descripteur de sécurité**

### <a name="recovery-console-and-shutdown"></a>Console de récupération et arrêt

- **Effacer le fichier d’échange de mémoire virtuelle lors de l’arrêt** : définissez la valeur **Activer** pour effacer le fichier d’échange de mémoire virtuelle quand l’appareil est mis hors tension. La valeur **Non configuré** n’efface pas la mémoire virtuelle.
- **Arrêt sans ouverture de session** : **Bloquer** masque l’option d’arrêt sur l’écran d’ouverture de session Windows. Les utilisateurs doivent se connecter à l’appareil, puis l’arrêter. **Non configuré** (valeur par défaut) permet aux utilisateurs d’arrêter l’appareil à partir de l’écran d’ouverture de session Windows.

### <a name="user-account-control"></a>Contrôle de compte d'utilisateur

- **Intégrité UIA sans emplacement sécurisé** : quand ce paramètre est défini sur **Activer**, les applications se trouvant dans un emplacement sécurisé dans le système de fichiers s’exécutent uniquement avec l’intégrité UIAccess. **Non configuré** (valeur par défaut) permet aux applications à s’exécuter avec l’intégrité UIAccess, même si elles ne se trouvent pas dans un emplacement sécurisé dans le système de fichiers.
- **Virtualiser les échecs d’écritures de fichiers et de Registre dans des emplacements définis par utilisateur** : quand ce paramètre a la valeur **Bloquer**, les échecs d’écriture d’application sont redirigés au moment de l’exécution vers des emplacements définis pour le système de fichiers et le Registre. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), les applications qui écrivent des données dans des emplacements protégés échouent.
- **Élever uniquement les fichiers exécutables signés et validés** : définissez la valeur **Activé** pour appliquer la validation du chemin de certification PKI d’un fichier exécutable avant qu’il puisse s’exécuter. Définissez la valeur **Non configuré** (valeur par défaut) pour ne pas appliquer de validation de chemin de certificat PKI avant qu’un fichier exécutable puisse s’exécuter.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Paramètres de comportement de l’invite d’élévation UIA

- **Invite d’élévation pour les administrateurs** : définit le comportement de l’invite d’élévation pour les administrateurs en mode d’approbation Administrateur :
  - **Élever sans invite**
  - **Demande d’informations d’identification sur le bureau sécurisé**
  - **Demande de consentement sur le bureau sécurisé**
  - **Demande d’informations d’identification**
  - **Demande de consentement**
  - **Non configuré** : demande de consentement pour les binaires non Windows
- **Invite d’élévation pour les utilisateurs standard** : définit le comportement de l’invite d'élévation pour les utilisateurs standard :
  - **Refuser automatiquement les demandes d’élévation de privilèges**
  - **Demande d’informations d’identification sur le bureau sécurisé**
  - **Non configuré** : invite demandant les informations d'identification
- **Acheminer les invites d’élévation vers le bureau de l’utilisateur interactif** : **Activer** pour que toutes les demandes d’élévation passent au bureau de l’utilisateur interactif, et non pas au bureau sécurisé. Tous les paramètres de stratégie de comportement d’invite pour les administrateurs et les utilisateurs standard sont utilisés. **Non configuré** (valeur par défaut) force toutes les demandes d’élévation à passer au bureau sécurisé, quels que soient les paramètres de stratégie de comportement d’invite pour les administrateurs et les utilisateurs standard.
- **Invite avec élévation de privilèges pour les installations d’application** : quand la valeur définie est **Bloquer**, les packages d’installation d’application ne sont pas détectés ou ne font pas l’objet d’une demande d’élévation. Quand ce paramètre a la valeur **Non configuré** (valeur par défaut), l’utilisateur est invité à entrer un nom d’utilisateur et un mot de base d’administration quand un package d’installation d’application nécessite une élévation de privilège.
- **Invite d’élévation UIA sans bureau sécurisé** : **Activer** pour autoriser les applications UIAccess à demander l’élévation sans utiliser le bureau sécurisé. Quand la valeur est **Non configuré** (valeur par défaut), les invites d’élévation utilisent un bureau sécurisé.

#### <a name="admin-approval-mode-settings"></a>Paramètres du mode d’approbation Administrateur

- **Mode d’approbation Administrateur pour l’administrateur intégré** : **Activé** permet au compte Administrateur intégré d’utiliser le mode d’approbation Administrateur. Une invite d’approbation est présentée à l’utilisateur pour toute opération nécessitant une élévation de privilège. **Non configuré** (valeur par défaut) exécute toutes les applications avec des privilèges d’administrateur complets.
- **Exécuter tous les administrateurs en mode d’approbation Administrateur** : définissez la valeur **Bloquer** pour désactiver le mode d’approbation Administrateur et tous les paramètres de stratégie UAC associés. **Non configuré** (valeur par défaut) active le mode d’approbation Administrateur.

### <a name="microsoft-network-client"></a>Client réseau Microsoft

- **Signer numériquement les communications (si le serveur accepte)** : détermine si le client SMB négocie la signature de paquet SMB. Quand ce paramètre a la valeur **Non configuré** ou est activé (par défaut), le client réseau Microsoft demande au serveur d’exécuter la signature de paquet SMB lors de la configuration de la session. Si la signature de paquet est activée sur le serveur, la signature de paquet est négociée. Si la valeur définie est **Désactiver**, le client SMB ne négocie jamais la signature de paquet SMB.
- **Envoyer un mot de passe non chiffré aux serveurs SMB tiers** : quand ce paramètre a la valeur **Activer**, le redirecteur Server Message Block (SMB) peut envoyer des mots de passe en clair aux serveurs SMB non-Microsoft qui ne prennent pas en charge le chiffrement de mot de passe lors de l’authentification. Quand la valeur définie est **Non configuré** (valeur par défaut), les mots de passe sont chiffrés.

### <a name="microsoft-network-server"></a>Serveur réseau Microsoft

- **Communications signées numériquement (lorsque le client l'accepte)** : détermine si le serveur SMB négocie la signature de paquet SMB avec les clients qui en font la demande. Quand ce paramètre a la valeur **Activer**, le serveur réseau Microsoft négocie la signature de paquet SMB comme demandé par le client. Autrement dit, si la signature de paquet a été activée sur le client, la signature de paquet est négociée. Quand l’option a la valeur **Non configuré** ou est désactivée, le client SMB ne négocie jamais la signature de paquet SMB.
- **Communications signées numériquement (toujours)** : détermine si la signature de paquet est requise par le composant serveur SMB. Quand ce paramètre a la valeur **Activer**, le serveur réseau Microsoft ne communique avec un client réseau Microsoft que si ce client accepte la signature de paquet SMB. Quand ce paramètre a la valeur **Non configuré** ou est désactivé (par défaut), la signature de paquet SMB est négociée entre le client et le serveur.

## <a name="next-steps"></a>Étapes suivantes

Pour attribuer ce profil à des groupes, consultez [Guide pratique pour attribuer des profils d’appareil](device-profile-assign.md).
