---
title: Résolution des problèmes d’intégration de JAMF Pro à Microsoft Intune
titleSuffix: Microsoft Intune
description: Des suggestions pour la résolution des problèmes les plus courants lors de l’intégration des appareils JAMF Pro pour Mac, avec Microsoft Intune.
keywords: ''
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
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e92e3442e1347cb1a2cd1c737078912b74f075c9
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817636"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Résoudre les problèmes d’intégration de JAMF Pro avec Microsoft Intune

Cet article aide les administrateurs Intune à comprendre et à résoudre les problèmes liés à l’intégration de JAMF Pro pour macOS avec Intune.

> [!TIP]  
> La plupart des informations contenues dans cet article sont initialement apparues dans [résoudre les problèmes lorsque vous intégrez JAMF à Microsoft Intune](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune) sur support.Microsoft.com.

## <a name="prerequisites"></a>Prérequis

Avant de commencer le dépannage, recueillez des informations de base pour clarifier le problème et réduire le temps nécessaire pour trouver une solution. Par exemple, lorsque vous rencontrez un problème lié à l’intégration de JAMF-Intune, vérifiez toujours que les conditions préalables sont remplies. Avant de commencer le dépannage, prenez connaissance des éléments suivants :

- Passez en revue les conditions préalables de l' [intégration de JAMF Pro à Intune](conditional-access-integrate-jamf.md#prerequisites).
- Tous les utilisateurs doivent avoir des licences Microsoft Intune et Microsoft AAD Premium P1 
- Vous devez disposer d’un compte d’utilisateur disposant d’autorisations d’intégration Microsoft Intune dans la console JAMF Pro.
- Vous devez disposer d’un compte d’utilisateur disposant d’autorisations d’administrateur général dans Azure.


Tenez compte des informations suivantes lors de l’examen de l’intégration de JAMF Pro à Intune : 
- Quel est le message d’erreur exact ?
- Où se trouve le message d’erreur ?
- Quand le problème a-t-il commencé ?  L’intégration de JAMF Pro avec Intune a-t-elle déjà fonctionné ?
- Combien d’utilisateurs sont affectés ? Tous les utilisateurs sont-ils affectés ou juste quelques-uns ?
- Combien d’appareils sont affectés ? Tous les appareils sont-ils affectés ou simplement certains ?
 

## <a name="common-problems"></a>Problèmes courants 

Les informations suivantes peuvent vous aider à identifier et à résoudre les problèmes courants des appareils après avoir configuré Intune et l’intégration de JAMF Pro.  

| Problème   | Plus d’informations                  |
|-----------------|--------------------------|
| **Les appareils sont marqués comme ne répondant pas dans JAMF Pro**  | [Les appareils ne parviennent pas à s’archiver avec JAMF Pro ou avec Azure AD](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **Les appareils Mac demandent la connexion au trousseau lorsque vous ouvrez une application échec de l’inscription des appareils**  | [Les utilisateurs sont invités à entrer leur mot de passe pour permettre aux applications de s’inscrire auprès de Azure ad](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **Échec de l’inscription des appareils**  | Les causes possibles sont les suivantes : <br> **-** [ ***cause 1*** -l’application JAMF Pro dans Azure possède des autorisations incorrectes](#cause-1) <br> **-** [ ***cause 2*** : il y a un problème pour *le connecteur JAMF Native MacOS* dans Azure ad](#cause-2) <br> **-** [ ***cause 3*** : l’utilisateur n’a pas de licence Intune ou JAMF valide](#cause-3) <br> **-** [ ***cause 4*** : l’utilisateur n’a pas utilisé le libre-service JAMF pour démarrer l’application portail d’entreprise](#cause-4) <br> **-** [ ***cause 5*** -l’intégration d’Intune est désactivée](#cause-5) <br> **-** [ ***cause 6*** -l’appareil a déjà été inscrit dans Intune ou l’utilisateur a tenté d’inscrire l’appareil plusieurs fois](#cause-6) <br> **-** [ ***cause 7*** -JamfAAD demande l’accès à une « clé de Workplace join Microsoft » à partir du trousseau d’utilisateurs](#cause-7) |
|  **L’appareil Mac affiche la conformité dans Intune, mais non conforme dans Azure** | [Problèmes d’inscription de l’appareil](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Les entrées en double s’affichent dans la console Intune pour les appareils Mac inscrits à l’aide de JAMF** | [Inscriptions multiples sur le même appareil](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **La stratégie de conformité ne parvient pas à évaluer l’appareil** | [La stratégie cible les groupes d’appareils](#compliance-policy-fails-to-evaluate-the-device) |
| **Impossible de récupérer le jeton d’accès pour l’API Microsoft Graph** | Les causes possibles sont les suivantes : <br> Autorisations -[pour l’application JAMF Pro dans Azure](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> licence - [expirée pour JAMF ou Intune](#a-license-required-for-jamf-intune-integration-has-expired) <br> les ports **-** ne [sont pas ouverts](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Les appareils sont marqués comme ne répondant pas dans JAMF Pro  

**Cause**: les causes courantes des périphériques marqués comme ne *répondant* pas par JAMF Pro sont les suivantes :

- L’appareil ne parvient pas à s’archiver avec JAMF Pro.  
  JAMF Pro s’attend à ce que les appareils soient vérifiés toutes les 15 minutes. Les appareils sont marqués comme ne répondant pas par JAMF lorsqu’ils ne parviennent pas à effectuer un archivage sur une période de 24 heures.  

- L’appareil ne parvient pas à s’archiver avec Azure AD.  
  Une fois l’inscription à Azure AD réussie, les appareils macOS reçoivent un jeton Azure :
  - Ce jeton est actualisé toutes les 12 heures.   
  - Lorsque l’actualisation du jeton échoue pendant 24 heures ou plus, JAMF Pro marque l’appareil comme ne répondant pas.  
  - Si le jeton Azure expire, les utilisateurs sont invités à se connecter à Azure pour obtenir un nouveau jeton. Un jeton d’actualisation pour l’accès Azure est généré tous les sept jours.

**Résolution**  
Une fois qu’un appareil est marqué comme ne *répondant* pas par JAMF Pro, l’utilisateur inscrit de l’appareil doit se connecter pour corriger l’état de non-réponse. Il doit s’agir de l’utilisateur qui a rejoint le compte, car il a l’identité d’Intune dans son trousseau de connexion.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>Les appareils Mac demandent la connexion au trousseau lorsque vous ouvrez une application  

Une fois que vous avez configuré Intune et JAMF Pro Integration et déployé des stratégies d’accès conditionnel, les utilisateurs d’appareils gérés avec JAMF Pro reçoivent des invites de mot de passe lors de l’ouverture de Microsoft Office applications 365, telles que des équipes, Outlook et d’autres applications nécessitant Azure Authentification Active Directory. 

Par exemple, une invite contenant du texte semblable à l’exemple suivant s’affiche lors de l’ouverture de Microsoft teams :

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**Cause**: ces invites sont générées par JAMF Pro pour chaque application applicable qui requiert l’inscription de Azure ad. 

**Résolution**   
À l’invite, l’utilisateur doit fournir le mot de passe de son appareil pour se connecter à Azure AD. Les options sont les suivantes :
- **Refuser** -ne pas se connecter et ne pas utiliser l’application.
- Connexion **à un** moment donné. La prochaine fois que l’application s’ouvre, elle vous demande de vous connecter à nouveau.
- **Toujours autoriser** : les informations d’identification de connexion sont mises en cache pour l’application. La prochaine fois que l’application s’ouvre, elle ne demande pas de connexion.  

Sélectionner *toujours autoriser* pour une application n’approuve cette application que pour la prochaine connexion. Les applications supplémentaires demandent l’authentification jusqu’à ce qu’elles soient également définies sur *toujours autoriser*. Les informations d’identification mises en cache pour une application ne peuvent pas être utilisées par une autre application.  

### <a name="devices-fail-to-register"></a>Échec de l’inscription des appareils  

Il existe plusieurs causes courantes pour les appareils Mac qui ne parviennent pas à s’inscrire.  

#### <a name="cause-1"></a>Cause 1  

**L’application JAMF Pro Enterprise dans Azure a une autorisation incorrecte ou a plus d’une autorisation**  

  Lorsque vous créez l’application dans Azure, vous devez supprimer toutes les autorisations d’API par défaut, puis attribuer à Intune une seule autorisation *update_device_attributes*. 

  **Résolution**  
  Passez en revue et, si nécessaire, corrigez les autorisations pour l’application JAMF que vous avez créée dans Azure AD. Consultez la procédure de [création d’une application pour JAMF dans Azure ad](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory). 

#### <a name="cause-2"></a>Cause 2  

**L’application **JAMF Native MacOS Connector** n’a pas été créée dans votre Azure ad locataire ou le consentement pour le connecteur a été signé par un compte qui ne dispose pas de droits d’administrateur général**  

  **Résolution**  
  Consultez la section Configuration de l' *intégration de MacOS Intune* dans [intégration de à Microsoft Intune](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html) sur docs.JAMF.com. 

#### <a name="cause-3"></a>Cause 3

**L’utilisateur ne dispose pas d’une licence Intune ou JAMF valide**  

  L’absence d’une licence valide peut entraîner l’erreur suivante, qui indique que la licence JAMF a expiré :  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **Résolution**
  - Licence JAMF : contactez JAMF pour obtenir de l’aide afin d’obtenir une nouvelle licence pour JAMF.  
  - Licence Intune : attribuez à l’utilisateur une licence valide ou contactez Microsoft ou votre partenaire pour obtenir des informations sur l’obtention d’une licence actuelle.

#### <a name="cause-4"></a>Cause 4  

**L’utilisateur n’a pas utilisé le *libre-service JAMF* pour démarrer l’application portail d’entreprise**

Pour qu’un appareil s’inscrive et s’inscrive auprès d’Intune par le biais de JAMF, l’utilisateur doit utiliser le libre-service JAMF pour ouvrir l’Portail d’entreprise Intune. Si l’utilisateur ouvre le portail d’entreprise manuellement, l’appareil s’inscrit et s’inscrit sans sa connexion à JAMF.  

Pour déterminer le service que l’appareil a utilisé pour l’inscription et l’inscription, recherchez dans l’application Portail d’entreprise sur l’appareil. Quand vous êtes inscrit via JAMF, vous devez recevoir une notification pour ouvrir l’application libre-service et y apporter des modifications.

Dans l’application Portail d’entreprise, l’utilisateur peut voir **`Not registered`** , et une entrée semblable à l’exemple suivant peut apparaître dans les journaux portail d’entreprise :  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**Résolution**  
Pour modifier la source d’inscription d’Intune en JAMF :
1. [Désinscrivez l’appareil macOS d’Intune](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos). Pour éviter d’autres complications pour les appareils qui ne sont pas entièrement supprimés d’Intune, consultez la [*cause 6*](#cause-6) dans cette liste de causes.  

2. Sur l’appareil, utilisez JAMF self service pour ouvrir l’application Portail d’entreprise, puis inscrivez l’appareil auprès d’Intune. Cette tâche nécessite que vous ayez [utilisé JAMF pour déployer l’application portail d’entreprise pour MacOS](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)et que vous ayez [créé une stratégie dans JAMF Pro qui inscrit l’appareil des utilisateurs auprès de Azure ad](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory).  

3. Lorsque le portail s’ouvre, le premier écran que vous voyez vous invite à vous connecter. Utiliser votre compte professionnel ou scolaire  

4. Le Portail d’entreprise vérifie les informations de votre compte, puis affiche les états Inscription de l’appareil et Conformité de l’appareil. Des triangles jaunes signalent les actions que vous devez effectuer pour sécuriser votre appareil macOS professionnel ou scolaire. Cliquez sur Commencer pour démarrer l’inscription.  

5. Si vous y êtes invité, tapez les informations de connexion de votre ordinateur.  
     
L’inscription de votre appareil pour la gestion peut prendre plusieurs minutes. Pendant ce temps, vous pouvez effectuer d’autres tâches sur votre appareil. Un message s’affiche une fois la configuration de l’application Portail d’entreprise terminée pour vous informer que vous avez fini.

#### <a name="cause-5"></a>Cause 5  

**L’intégration d’Intune est désactivée**

Si l’intégration d’Intune est désactivée, les utilisateurs reçoivent une fenêtre contextuelle dans le Portail d’entreprise avec le message suivant lorsqu’ils essaient d’inscrire un appareil :  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

Le serveur JAMF Pro envoie une impulsion aux serveurs Intune lorsque l’intégration est désactivée, ce qui indique à Intune que l’intégration est désactivée. 

**Résolution**  
Réactivez l’intégration d’Intune dans JAMF Pro. Consultez [Configurer l’intégration de Microsoft Intune dans Jamf Pro](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro).


#### <a name="cause-6"></a>Cause 6  

**L’appareil a déjà été inscrit dans Intune ou l’utilisateur a tenté d’inscrire l’appareil plusieurs fois**

Si un appareil est désinscrit de JAMF mais qu’il n’a pas été correctement supprimé d’Intune, ou si plusieurs tentatives d’inscription sont effectuées, vous pouvez voir plusieurs instances du même appareil dans le portail. Cela provoque l’échec de l’inscription de JAMF.

**Résolution**  
1. Sur le Mac, démarrez **Terminal**.
2. Exécutez **sudo JAMF removemdmprofile**.
3. Exécutez **sudo JAMF removeFramework**.
4. Sur le serveur JAMF Pro, supprimez l’enregistrement d’inventaire de l’ordinateur.
5. Supprimez l’appareil de AzureAD.
6. Supprimez les fichiers suivants sur le périphérique s’ils existent :
   - Prise en charge/Library/Application Support/com. Microsoft. CompanyPortal. UserContext. info
   - Prise en charge/Library/Application Support/com. Microsoft. CompanyPortal
   - Prise en charge/Library/Application Support/com. jamfsoftware. selfservice. Mac
   - Application/Library/Saved
   - State/com. jamfsoftware. selfservice. Mac. savedState
   - État de l’application/Library/Saved/com. Microsoft. CompanyPortal. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/Library/cookies/com. Microsoft. CompanyPortal. binarycookies
   - /Users/<username>/Library/cookies/com. JAMF. Management. jamfAAD. binarycookies
   - com. Microsoft. CompanyPortal
   - com. Microsoft. CompanyPortal. HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Clé de transport de session Microsoft (clés publiques et privées)
   - Clé de Workplace Join Microsoft (clés publiques et privées)
7. Supprimez tout ce qui se trouve dans le trousseau du périphérique qui fait référence à *Microsoft*, *Intune*ou *portail d’entreprise*, y compris les certificats DeviceLogin.Microsoft.com. Supprimez les références *JAMF* à l’exception de la clé publique et privée JAMF. 
   > [!IMPORTANT]  
   > La suppression de la clé publique et privée interrompt l’inscription de l’appareil.

8. Supprimez les entrées suivantes que vous trouvez :  
   - Genre : mot de passe d’application ; Compte : com. Microsoft. workplacejoin. empreinte numérique
   - Genre : mot de passe d’application ; Compte : com. Microsoft. workplacejoin. registeredUserPrincipalName
   - Genre : certificat ; Délivré par : MS-Organization-Access
   - Genre : préférence d’identité ; Nom (URL STS AD FS, le cas échéant) : https://adfs\<DNSName>.com/adfs/ls
   - Genre : préférence d’identité ; Nom : https://enterpriseregistration.windows.net
   - Genre : préférence d’identité ; Nom : https://enterpriseregistration.windows.net/  
9. Redémarrez l’appareil Mac.
10. Désinstallez Portail d’entreprise de l’appareil.
11. Accédez à portal.manage.microsoft.com et supprimez toutes les instances du périphérique Mac. Attendez au moins 30 minutes avant de passer à l’étape suivante.
12. Réinscrivez l’appareil dans JAMF Pro.
13. Rouvrez le libre-service et démarrez la stratégie d’inscription.


#### <a name="cause-7"></a>Cause 7  

**JamfAAD demande l’accès à une « clé de Workplace Join Microsoft » à partir du trousseau d’utilisateurs**

Lors de l’inscription, l’utilisateur d’un appareil macOS reçoit l’invite suivante pour autoriser JamfAAD à accéder à une clé à partir de son trousseau : 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**Résolution**  
Pour inscrire correctement l’appareil auprès de Azure AD, JAMF exige que l’utilisateur fournisse son mot de passe de compte, puis sélectionnez **autoriser**.

Cette requête est similaire à la demande d' [appareils Mac invite à entrer la connexion au trousseau lorsque vous ouvrez une application](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app), plus haut dans cet article.  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>L’appareil Mac affiche la conformité dans Intune, mais non conforme dans Azure  

**Cause**: les conditions suivantes peuvent entraîner l’affichage d’un appareil comme conforme dans Intune, mais pas comme conforme dans Azure :  
- L’appareil n’est pas inscrit correctement.  
- L’appareil a été inscrit plusieurs fois sans le nettoyage nécessaire.

**Résolution**  
Pour résoudre ce problème, suivez la résolution de la [*cause 6*](#cause-6) pour l’échec de l' *inscription des appareils*, plus haut dans cet article. 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Les entrées en double s’affichent dans la console Intune pour les appareils Mac inscrits à l’aide de JAMF  
 
**Cause**: un appareil est inscrit plusieurs fois auprès d’Intune, qui est généralement réinscrit après avoir été supprimé d’Intune.  

Lorsqu’un appareil est supprimé d’Intune et de l’intégration de JAMF Pro, certaines données peuvent être conservées, ce qui peut entraîner des inscriptions successives pour créer des entrées en double.  

**Résolution**  
Pour résoudre ce problème, suivez la résolution de la [*cause 6*](#cause-6) pour l’échec de l' *inscription des appareils*, plus haut dans cet article. 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>La stratégie de conformité ne parvient pas à évaluer l’appareil  

**Cause**: l’intégration de JAMF à Intune ne prend pas en charge la stratégie de conformité qui cible les groupes d’appareils. 

**Résolution**  
Modifiez la stratégie de conformité pour les appareils macOS à affecter aux groupes d’utilisateurs. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Impossible de récupérer le jeton d’accès pour l’API Microsoft Graph

Vous recevez l’erreur suivante :

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

La source de cette erreur peut être l’une des causes suivantes : 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Il y a un problème d’autorisation avec l’application JAMF Pro dans Azure

Lors de l’inscription de l’application JAMF Pro dans Azure, l’une des conditions suivantes s’est produite :  
- L’application a reçu plus d’une autorisation.
- L’option **accorder le consentement de l’administrateur pour l’option de *> de \<your***  n’a pas été sélectionnée.  

**Résolution**  
Consultez la résolution de la cause 1 de l’échec de l' [inscription des appareils](#devices-fail-to-register), plus haut dans cet article.

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>Une licence requise pour l’intégration de JAMF-Intune a expiré

**Résolution**: consultez la résolution de la cause 3 de l’échec de l' [inscription des appareils](#devices-fail-to-register). 

#### <a name="the-required-ports-arent-open-on-your-network"></a>Les ports requis ne sont pas ouverts sur votre réseau

**Résolution**: passez en revue les informations relatives aux ports réseau dans la section [conditions préalables](conditional-access-integrate-jamf.md#prerequisites) à l’intégration de JAMF Pro avec Intune.


## <a name="next-steps"></a>Étapes suivantes
En savoir plus sur l' [intégration de JAMF Pro avec Intune](conditional-access-integrate-jamf.md)