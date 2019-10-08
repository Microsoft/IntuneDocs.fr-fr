---
title: Résoudre les erreurs courantes pour Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Dépanner et résoudre les erreurs courantes pour le Connecteur Microsoft Intune Exchange local
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa4dbfb7c13d767df41655b391767fc7aa13d914
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817584"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Résoudre les erreurs courantes pour Intune Exchange Connector

Cet article peut aider l’administrateur Intune à résoudre des erreurs et des messages spécifiques sur le fonctionnement du connecteur Intune Exchange.  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>La configuration a échoué et a retourné le code d’erreur 0x0000001

**Problème** :  
Lorsque vous essayez de configurer la Connecteur Microsoft Intune Exchange, vous recevez le message d’erreur suivant :

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

Ce problème peut se produire si les paramètres du proxy Internet sont mal configurés.

**Résolution** :  
Configurez les paramètres du proxy :
1. Contactez l’administrateur du réseau local pour vous assurer que les paramètres de proxy sont correctement configurés. 
2. Utilisez la commande **netsh WinHTTP** pour configurer le serveur proxy et ajouter la liste d’exclusions requise. Par exemple :  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>La configuration a échoué et a retourné le code d’erreur 0x000000b   

**Problème** :  
Lorsque vous essayez de configurer la Connecteur Microsoft Intune Exchange, vous recevez le message d’erreur suivant :  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Ce problème peut se produire si le compte que vous avez utilisé pour vous connecter à Intune n’est pas un compte d’administrateur général Intune.

**Résolution** :  
Connectez-vous à Intune avec un compte d’administrateur général ou ajoutez votre compte au groupe d’administration globale. Pour plus d’informations, consultez [Contrôle d’accès en fonction du rôle (RBAC) avec Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>La configuration a échoué et a retourné le code d’erreur 0x0000006

**Problème** :  
Lorsque vous essayez de configurer la Connecteur Microsoft Intune Exchange, vous recevez le message d’erreur suivant :  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
Cette erreur peut se produire si un serveur proxy est utilisé pour se connecter à Internet et bloque le trafic vers le service Intune. Pour déterminer si un proxy est en cours d’utilisation, accédez à **panneau de configuration** > **Options Internet**, sélectionnez l’onglet **connexion** , puis cliquez sur **paramètres réseau**.

**Résolution** :  

- **Option 1** : supprimez les paramètres de proxy pour permettre à l’ordinateur de se connecter à Internet sans passer par le proxy.  

- **Option 2** : configurez votre serveur proxy pour permettre la communication avec le service Intune, comme indiqué dans [Intune Exchange Connector Requirements](exchange-connector-install.md#intune-exchange-connector-requirements).



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>Événement 7000 ou 7041 : le service Connecteur Microsoft Intune Exchange ne démarre pas

**Problème** :  
Un appareil iOS ne parvient pas à s’inscrire dans Intune et génère l’un des messages d’erreur suivants :  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
Ce problème peut se produire si le compte **WIEC_User** ne dispose pas du droit d’utilisateur **ouvrir une session en tant que service** dans la stratégie locale.

**Résolution** :  
Sur l’ordinateur qui exécute Intune Exchange Connector, attribuez le droit d’utilisateur **ouvrir une session en tant que service** au compte de service **WIEC_User** . Si l’ordinateur est un nœud dans un cluster, veillez à attribuer le droit d’utilisateur *ouvrir une session en tant que service* au compte de service de cluster sur tous les nœuds du cluster.  

Pour affecter le droit d’utilisateur **ouvrir une session en tant que service** au compte de service **WIEC_User** sur l’ordinateur, procédez comme suit :

1. Connectez-vous à l’ordinateur en tant qu’administrateur ou membre du groupe administrateurs.
2. Exécutez **secpol. msc** pour ouvrir la stratégie de sécurité locale.
3. Accédez à **paramètres de sécurité** > **stratégies locales**, puis sélectionnez **attribution des droits utilisateur**.
4. Dans le volet droit, double-cliquez sur **Ouvrir une session en tant que service**.
5. Sélectionnez **Ajouter un utilisateur ou un groupe**, ajoutez **WIEC_USER** à la stratégie, puis sélectionnez **OK** deux fois.

Si le droit d’utilisateur **ouvrir une session en tant que service** a été affecté à **WIEC_User** mais a été supprimé ultérieurement, contactez l’administrateur du domaine pour déterminer si un paramètre de stratégie de groupe est écrasé.  

## <a name="next-steps"></a>Étapes suivantes  

L’article suivant peut aider à résoudre des erreurs spécifiques :
- [Résoudre les problèmes courants liés à Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md). git 

Demandez de l’aide au support technique ou à la communauté Intune.
- Consultez [obtenir](../fundamentals/get-support.md) de l’aide pour utiliser la console Intune pour résoudre le problème ou pour ouvrir un dossier de support auprès de Microsoft. 
- Publiez votre problème dans les [forums Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
