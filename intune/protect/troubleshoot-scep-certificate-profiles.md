---
title: Résoudre les problèmes d’utilisation des profils de certificats SCEP pour provisionner des certificats avec Microsoft Intune | Microsoft Docs
description: Résolvez les problèmes d'utilisation de SCEP par les appareils pour demander des certificats à utiliser avec Intune, y compris la communication des appareils vers NDES, de NDES vers les autorités de certification, et d’Intune Certificate Connector vers le service Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae7ffe5a8c20aa7edd67853ff86ef9e28cf2d175
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915822"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>Vue d’ensemble de la résolution des problèmes liés aux profils de certificat SCEP avec Microsoft Intune

Les problèmes d’utilisation des profils de certificat Simple Certificate Enrollment Protocol (SCEP) peuvent être difficiles à résoudre dans Intune. Cet article fournit une vue d'ensemble qui peut vous aider à résoudre ces problèmes en :

- Expliquant l'architecture et le flux de communication du processus SCEP
- Vous aidant à réduire le nombre de cas où un problème survient dans ce flux de communication
- Identifiant les fichiers journaux clés référencés dans les articles suivants pour le dépannage des profils de certificats

Les informations contenues dans ce document et dans les articles connexes de dépannage des certificats SCEP s'appliquent à l'utilisation des profils de certificats SCEP avec les appareils Android, iOS/iPad et Windows. Les informations similaires pour macOS ne sont actuellement pas disponibles.

Pour résoudre les problèmes liés à Network Device Enrollment Service (NDES), consultez les articles suivants sur le site support.microsoft.com :

- [Vérifier la configuration NDES locale pour les certificats SCEP dans Intune](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune)
- [Résolution des problèmes de configuration NDES pour une utilisation avec des profils de certificat Microsoft Intune]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune)

Avant de poursuivre, assurez-vous de remplir les [conditions préalables à l'utilisation des profils de certificat SCEP](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates), notamment pour le déploiement d'un certificat racine via un profil de certificat approuvé.

## <a name="scep-communication-flow-overview"></a>Vue d’ensemble du flux de communication SCEP

Le graphique suivant montre une vue d’ensemble de base du flux de communication SCEP dans Intune.

![Flux du profil de certificat SCEP](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [Déployez un profil de certificat SCEP](troubleshoot-scep-certificate-profile-deployment.md). Intune génère une chaîne de demande d’accès, qui nécessite un utilisateur, un objectif de certificat et un type de certificat spécifiques.

2. [Communication de l’appareil au serveur NDES](troubleshoot-scep-certificate-device-to-ndes.md). L'appareil utilise l'URI de NDES à partir du profil pour contacter le serveur NDES et lui présenter une demande d’accès.

3. [Communication de NDES au module de stratégie](troubleshoot-scep-certificate-ndes-policy-module.md). NDES transmet la demande d’accès au module de stratégie Intune Certificate Connector sur le serveur, qui valide cette demande.

4. [NDES à l’autorité de certification](troubleshoot-scep-certificate-ndes-policy-module.md). NDES transmet les demandes valides d’émission d’un certificat à l'autorité de certification (CA).

5. [Remise du certificat à l’appareil](troubleshoot-scep-certificate-delivery.md). Le certificat est remis à l'appareil.

6. [Création de rapports de déploiement sur Intune](troubleshoot-scep-certificate-reporting.md). Intune Certificate Connector crée des rapports sur l'événement d'émission du certificat et les transmet à Intune.

## <a name="log-files"></a>Fichiers journaux

Pour identifier les problèmes au niveau du flux communication et de provisionnement des certificats, consultez les fichiers journaux de l'infrastructure serveur et des appareils. Les sections ultérieures sur la résolution des problèmes affectant les profils de certificats SCEP se réfèrent aux fichiers journaux référencés dans cette section.

- [Journaux de l’infrastructure et du serveur](#logs-for-on-premises-infrastructure)

Les journaux des appareils dépendent de la plate-forme de l'appareil :  

- [iOS et iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>Journaux pour l’infrastructure locale
  
L'infrastructure locale qui prend en charge l'utilisation des profils de certificats SCEP pour les déploiements de certificats inclut Microsoft Intune Certificate Connector, NDES exécuté sur un serveur Windows, et l'autorité de certification.

Les fichiers journaux pour ces rôles incluent l’Observateur d'événements visualiseur, les consoles de certificats et divers fichiers journaux spécifiques à Intune Certificate Connector, à NDES ou à d'autres rôles et opérations qui font partie de l'infrastructure locale.

La liste suivante comprend les journaux ou consoles référencés dans les prochains articles de résolution des problèmes SCEP. 

- **NDESConnector_date_time.svclog** :

  Ce journal montre la communication entre Microsoft Intune Certificate Connector et le service cloud Intune. Vous pouvez utiliser l'[outil Service Trace Viewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) pour afficher ce fichier journal.

  Clé de Registre associée : *HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  Emplacement : Sur le serveur qui héberge NDES : *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **CertificateRegistrationPoint_date_time.svclog** :

  Ce journal indique que le module de stratégie SNED reçoit et vérifie les demandes de certificat. Vous pouvez utiliser l'[outil Service Trace Viewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) pour afficher ce fichier journal.

  Emplacement : Sur le serveur qui héberge NDES : *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **NDESPlugin.log** :

  Ce journal montre l’envoi des demandes de certificat au point d'enregistrement de certificat, et la vérification qui résulte de ces demandes.

  Emplacement : Sur le serveur qui héberge NDES : *%program_files%\Microsoft Intune\NDESPolicyModule\logs*

- **Journaux IIS** :

  Les journaux IIS montrent les demandes de certificats des appareils mobiles entrant dans NDES.

  Emplacement : Sur le serveur qui héberge NDES : *c:\inetpub\logs\LogFiles\W3SVC1*

- **Journal des applications Windows** :

  Ce journal est utile pour examiner les problèmes relatifs à IIS, notamment le pool d'applications SCEP.

  Emplacement : Sur le serveur qui héberge NDES : Exécuter **eventvwr.msc** pour ouvrir l’Observateur d'événements Windows




### <a name="logs-for-android-devices"></a>Journaux pour appareils Android

Pour les appareils qui exécutent Android, utilisez le fichier journal de l'application **Android Company Portal**, **OMADM.log**. Avant de collecter et de consulter les journaux, assurez-vous que l'option [Journalisation détaillée](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android.md) est activée, puis reproduisez le problème.

Pour collecter les fichiers OMADM.logs à partir d'un appareil, voir [Upload and email logs using a USB cable](/intune-user-help/send-logs-to-your-it-admin-using-cable-android.md) (Charger et envoyer par e-mail des journaux à l'aide d'un câble USB).

Vous pouvez également [Charger et envoyer par e-mail des journaux](/intune-user-help/send-logs-to-your-it-admin-by-email-android.md#upload-and-email-logs-from-microsoft-intune-app) au support.

### <a name="logs-for-ios-and-ipados-devices"></a>Journaux pour appareils iOS et iPadOS

Pour les appareils qui exécutent iOS ou iPadOS, vous utilisez les journaux de débogage et **Xcode** sur un ordinateur Mac :

1. Connectez l’appareil iOS au Mac, puis accédez à **Applications** > **Utilitaires** pour ouvrir l'application Console. 

2. Sous **Action**, sélectionnez **Inclure les messages d’information** et **Inclure les messages de débogage**.

   ![Sélectionner les options du journal](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. Reproduisez le problème et enregistrez les journaux dans un fichier texte :
   1. Sélectionnez **Modifier** > **Sélectionner tout** pour sélectionner tous les messages sur l'écran actuel, puis choisissez **Modifier** > **Copier** pour copier les messages dans le presse-papiers. 
   2. Ouvrez l'application TextEdit, collez les journaux copiés dans un nouveau fichier texte, puis enregistrez le fichier.


Le journal Portail d'entreprise pour les appareils iOS et iPadOS ne contient pas d'informations sur les profils de certificats SCEP.

### <a name="logs-for-windows-devices"></a>Journaux pour appareils Windows

Pour les appareils qui exécutent Windows, utilisez les journaux d’événements Windows pour diagnostiquer les problèmes d'inscription ou de gestion des appareils que vous gérez avec Intune.

Sur l’appareil, ouvrez l’**Observateur d’événements** > **Journaux des applications et des services** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostics-Provider**

![Journaux d’événements Windows](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>Étapes suivantes

Consultez la section sur la [déploiement des profils de certificats SCEP](troubleshoot-scep-certificate-profile-deployment.md) 
