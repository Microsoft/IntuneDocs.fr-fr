---
title: Résoudre les problèmes courants liés à Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Dépannez et résolvez les problèmes courants liés au connecteur Microsoft Intune Exchange local.
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
ms.openlocfilehash: 14da6274546cbd4c1867975c08c60ece313714b1
ms.sourcegitcommit: 78f9750712c254d8b123ef15b74f30ca999aa128
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71917984"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Résoudre les problèmes courants liés à Intune Exchange Connector
 
Cet article peut aider l’administrateur Intune à résoudre les problèmes courants liés au fonctionnement d’Intune Exchange Connector.  

Avant de commencer le dépannage, consultez [résoudre les problèmes liés au connecteur Exchange local Intune](troubleshoot-exchange-connector.md) pour obtenir des informations de base sur le connecteur. Passez également en revue les problèmes courants liés à la configuration du connecteur. 

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Un appareil Exchange ActiveSync n’est pas découvert à partir d’Exchange

Lorsqu’un appareil Exchange ActiveSync n’est pas découvert à partir d’Exchange, [Surveillez l’activité du connecteur Exchange](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) pour déterminer si le connecteur Exchange est en synchronisation avec le serveur Exchange. Si aucune synchronisation ne s’est produite depuis la jonction de l’appareil, collectez les journaux de synchronisation et joignez-les à une demande de support. Si une synchronisation complète ou une synchronisation rapide s’est terminée correctement depuis la jonction de l’appareil, recherchez les problèmes suivants : 

- Assurez-vous que les utilisateurs disposent d’une licence Intune. Si ce n’est pas le cas, le connecteur Exchange ne découvre pas ses appareils.  

- Si l’adresse SMTP principale de l’utilisateur est différente de son nom d’utilisateur principal (UPN) dans Azure Active Directory (Azure AD), le connecteur Exchange ne découvre aucun appareil pour cet utilisateur. Corrigez l’adresse SMTP principale pour résoudre le problème.  

- Si vous avez des serveurs de boîtes aux lettres Exchange 2010 et Exchange 2013 dans votre environnement, nous vous recommandons de faire pointer le connecteur Exchange vers un serveur d’accès au client (CAS) Exchange 2013. Si le connecteur Exchange est configuré pour communiquer avec un CAS Exchange 2010, le connecteur Exchange ne découvre aucun appareil d’utilisateur sur Exchange 2013.  

- Pour les environnements Exchange Online Dedicated, vous devez faire pointer le connecteur Exchange vers une autorité de certification Exchange 2013 (et non une autorité de certification Exchange 2010) dans l’environnement dédié lors de la configuration initiale. Le connecteur communique uniquement avec une autorité de certification Exchange 2013 lorsqu’il exécute des applets de commande PowerShell.  


## <a name="problems-with-the-notification-email-message"></a>Problèmes avec le message électronique de notification  

Pour prendre en charge l’accès conditionnel pour les boîtes aux lettres locales sur des appareils qui n’exécutent pas Android Knox, assurez-vous que l’inscription Intune démarre à partir du message électronique « bien démarrer maintenant » que le connecteur Exchange Intune envoie. Le démarrage de l’inscription à partir du message garantit que l’appareil reçoit un ActiveSyncID unique sur toutes les plateformes (Exchange, Azure AD, Intune).  

Un utilisateur peut ne pas recevoir le message électronique de notification car :  

- Le compte de notification n’a pas été configuré correctement.
- Échec de la découverte automatique pour le compte de notification.
- La demande d’envoi du message électronique par Exchange Web Services (EWS) a échoué.

Consultez les sections suivantes pour résoudre les problèmes de notification par courrier électronique.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>Vérifier le compte de notification qui récupère les paramètres de découverte automatique
1. Assurez-vous que le service de découverte automatique et EWS sont configurés sur les services d’accès au client Exchange. Pour plus d’informations, consultez [services d’accès au client](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) et [service de découverte automatique dans Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).


2. Vérifiez que votre compte de notification remplit les conditions suivantes :

   - Le compte dispose d’une boîte aux lettres active qui est hébergée par votre serveur Exchange sur site.  

   - L’UPN du compte correspond à l’adresse SMTP.

3. La découverte automatique requiert un serveur DNS qui possède un enregistrement DNS pour **autodiscover.SMTPdomain.com** (par exemple autodiscover.contoso.com) qui pointe vers votre serveur d’accès au client Exchange. Pour vérifier l’enregistrement, spécifiez votre nom de domaine complet à la place de *autodiscover.SMTPdomain.com* et procédez comme suit :

   1. À l’invite de commandes, entrez *nslookup*.  

   2. Entrez *autodiscover.SMTPdomain.com*. La sortie doit ressembler à l’image suivante :  
      résultats de la ![Nslookup](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
)

   Vous pouvez également tester le service de découverte automatique à partir d’Internet à https://testconnectivity.microsoft.com. Ou testez-le à partir d’un domaine local à l’aide de l’outil Microsoft Connectivity Analyzer. Pour plus d’informations, consultez [outil Microsoft Connectivity Analyzer](https://docs.microsoft.com/en-us/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)). Si nécessaire, [Téléchargez l’outil Microsoft Connectivity Analyzer](http://go.microsoft.com/fwlink/?LinkID=313782).


### <a name="check-autodiscovery"></a>Vérifier la détection automatique  

Si la découverte automatique échoue, procédez comme suit :
1. [Configurez un enregistrement DNS de découverte automatique valide](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)). 

2. Coder en dur l’URL EWS dans le fichier de configuration du connecteur Intune Exchange :

   1. Déterminez l’URL EWS. L’URL EWS par défaut pour Exchange est `https://<mailServerFQDN>/ews/exchange.asmx`, mais votre URL peut être différente. Contactez l’administrateur Exchange pour vérifier l’URL correcte de votre environnement.

   2. Modifiez le fichier *OnPremisesExchangeConnectorServiceConfiguration.xml*. Par défaut, le fichier se trouve dans *%ProgramData%\Microsoft\Windows Intune Exchange Connector* sur l’ordinateur qui exécute le connecteur Exchange. Ouvrez le fichier dans un éditeur de texte, puis modifiez la ligne suivante pour qu’elle reflète l’URL EWS pour votre environnement : `<ExchangeWebServiceURL>https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`
    

3. Enregistrez le fichier, puis redémarrez l’ordinateur ou le service Connecteur Microsoft Intune Exchange.

>[!NOTE]
> Dans cette configuration, Intune Exchange Connector cesse d’utiliser la découverte automatique et se connecte au lieu de cela directement à l’URL EWS.

## <a name="next-steps"></a>Étapes suivantes  

Pour obtenir de l’aide sur des erreurs spécifiques, essayez de [résoudre les erreurs courantes pour Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Pour obtenir de l’aide ou pour obtenir de l’aide auprès de la communauté Intune :
- Consultez [obtenir](../fundamentals/get-support.md) de l’aide pour utiliser la console Intune pour résoudre le problème ou pour ouvrir un dossier de support avec Microsoft. 
- Publiez votre problème dans les [forums Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
