---
title: Paramètres de lignes de base de sécurité Intune pour Microsoft Edge
titleSuffix: Microsoft Intune
description: Paramètres de ligne de base de sécurité pris en charge par Intune pour gérer le navigateur Microsoft Edge
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
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
ms.openlocfilehash: 8f4e56340d871ea5e0bcec7e541a418c32d021d0
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415644"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Paramètres de ligne de base Microsoft Edge pour Intune

Affichez les paramètres de ligne de base du navigateur Web Microsoft Edge pris en charge par Microsoft Intune. Les valeurs par défaut de la ligne de base Microsoft Edge représentent la configuration recommandée pour les navigateurs Microsoft Edge et peuvent ne pas correspondre aux valeurs par défaut de référence pour d’autres lignes de base de sécurité.

> [!NOTE]
> La ligne de base Microsoft Edge est en version préliminaire publique. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **Empêcher le contournement des invites Microsoft Defender SmartScreen pour les sites**  
  **Par défaut** : Activé  
  CSP Microsoft Edge : [navigateur/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  Ce paramètre de stratégie vous permet de décider si les utilisateurs peuvent ignorer les avertissements Microsoft Defender SmartScreen concernant les sites Web potentiellement malveillants. 
  - Si vous activez ce paramètre, les utilisateurs ne peuvent pas ignorer les avertissements Microsoft Defender SmartScreen et ils ne peuvent pas continuer à accéder au site. 
  - Si vous désactivez ou ne configurez pas ce paramètre, les utilisateurs peuvent ignorer les avertissements Microsoft Defender SmartScreen et accéder au site.

- **Version SSL minimale activée**  
  **Par défaut** : Activé  

  Définissez une version minimale prise en charge de SSL. Si vous définissez cette stratégie sur *non configuré*, Microsoft Edge utilise une version minimale par défaut de *TLS 1,0*. Lorsque cette option est *activée*, vous pouvez sélectionner une version minimale parmi les valeurs suivantes :

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **Version SSL minimale activée**  
    **Valeur par défaut**: TLS 1,2

- **Empêcher le contournement des avertissements Microsoft Defender SmartScreen concernant les téléchargements**  
  **Par défaut** : Activé  
  CSP Microsoft Edge : [navigateur/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  Cette stratégie vous permet de déterminer si les utilisateurs peuvent ignorer les avertissements Microsoft Defender SmartScreen concernant les téléchargements non vérifiés.
  - Si vous activez cette stratégie, les utilisateurs de votre organisation ne peuvent pas ignorer les avertissements Microsoft Defender SmartScreen et ne peuvent pas effectuer les téléchargements non vérifiés.
  - Si vous désactivez ou ne configurez pas cette stratégie, les utilisateurs peuvent ignorer les avertissements Microsoft Defender SmartScreen et effectuer des téléchargements non vérifiés.

- **Autoriser les utilisateurs à continuer à partir de la page d’avertissement SSL**  
  **Par défaut** : Désactivé  
  CSP Microsoft Edge : [navigateur/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  Microsoft Edge affiche une page d’avertissement lorsque les utilisateurs consultent des sites qui contiennent des erreurs SSL. Si vous définissez cette stratégie sur *activé* ou *non configuré*, les utilisateurs peuvent cliquer sur ces pages d’avertissement. Lorsque cette stratégie est *désactivée*, les utilisateurs ne peuvent pas cliquer sur une page d’avertissement. 

- **Paramètre Adobe Flash par défaut**  
  **Par défaut** : Activé  
  CSP Microsoft Edge : [navigateur/AllowFlash](https://docs.microsoft.coms/windows/client-management/mdm/policy-csp-browser#browser-allowflash)et [Browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  Détermine si les sites Web qui ne sont pas couverts par « PluginsAllowedForUrls » ou « PluginsBlockedForUrls » peuvent exécuter automatiquement le plug-in Adobe Flash. 

  - Sélectionnez « BlockPlugins » pour bloquer Adobe Flash sur tous les sites
  - Sélectionnez « ClickToPlay » pour laisser Adobe Flash s’exécuter mais demander à l’utilisateur de cliquer sur l’espace réservé pour le démarrer.
  
   Dans tous les cas, les stratégies « PluginsAllowedForUrls » et « PluginsBlockedForUrls » ont priorité sur « DefaultPluginsSetting ». La lecture automatique est autorisée uniquement pour les domaines explicitement listés dans la stratégie « PluginsAllowedForUrls ». 
   Si vous souhaitez activer la lecture automatique pour tous les sites, envisagez d’ajouter http://* et https://* à cette liste. 
   
   - Si vous affectez à cette stratégie la valeur *non configuré*, l’utilisateur peut modifier ce paramètre manuellement. * 2 = bloquer le plug-in Adobe Flash * 3 = Cliquez pour lire le premier ensemble d’options' 1 'Allow-All, mais cette fonctionnalité est désormais gérée uniquement par la stratégie’PluginsAllowedForUrls'. Les stratégies existantes utilisant « 1 » fonctionneront en mode « en lecture seule ».  
 
  - **Paramètre Adobe Flash par défaut**  
    **Par défaut**: bloquer le plug-in Adobe Flash

- **Activer l’isolation de site pour chaque site**  
  **Par défaut** : Activé  

  La stratégie « SitePerProcess » peut être utilisée pour empêcher les utilisateurs de refuser le comportement par défaut de l’isolation de tous les sites. Vous pouvez également utiliser la stratégie IsolateOrigins pour isoler des origines supplémentaires et plus précises.

  - Lorsque cette stratégie est définie sur *activé*, les utilisateurs ne peuvent pas refuser le comportement par défaut où chaque site s’exécute dans son propre processus. 
  - Si vous utilisez l’option *désactivé* ou *non configuré*, un utilisateur peut refuser l’isolation du site. (Par exemple, à l’aide de l’entrée « désactiver l’isolation de site » dans edge://flags.) La désactivation de la stratégie ou la non-configuration de la stratégie ne désactive pas l’isolation de site.

- **Schémas d’authentification pris en charge**  
  **Par défaut** : Activé  

  Spécifie les schémas d’authentification HTTP pris en charge. Vous pouvez configurer la stratégie à l’aide des valeurs suivantes : « Basic », « Digest », « NTLM » et « Negotiate ». Séparez les valeurs par des virgules. Si vous ne configurez pas cette stratégie, les quatre schémas sont utilisés.
 
  - **Schémas d’authentification pris en charge**  
    Sélectionnez l'une des options suivantes : 
    - de base
    - Digest
    - NTLM *(sélectionné par défaut)*
    - Négocier *(sélectionnée par défaut)*

- **Activer l’enregistrement des mots de passe dans le gestionnaire de mots de passe**  
  **Par défaut** : Désactivé  
  CSP Microsoft Edge : [navigateur/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Activez Microsoft Edge pour enregistrer les mots de passe utilisateur. 
  - Si vous activez cette stratégie, les utilisateurs peuvent enregistrer leurs mots de passe dans Microsoft Edge. La prochaine fois qu’ils visitent le site, Microsoft Edge entrera automatiquement le mot de passe. 
  - Si vous désactivez cette stratégie, les utilisateurs ne peuvent pas enregistrer de nouveaux mots de passe, mais ils peuvent toujours utiliser des mots de passe précédemment enregistrés. 
  
  Lorsque vous affectez la valeur *activé* ou *désactivé*à cette stratégie, les utilisateurs ne peuvent pas modifier ou remplacer cette stratégie dans Microsoft Edge. 
  
  Si vous définissez cette option sur *non configuré*, les utilisateurs peuvent enregistrer les mots de passe et désactiver cette fonctionnalité.

- **Contrôler les extensions qui ne peuvent pas être installées**  
  **Par défaut** : Activé  

  Répertoriez les extensions spécifiques que les utilisateurs ne peuvent pas installer dans Microsoft Edge. Lorsque vous déployez cette stratégie, toutes les extensions qui étaient précédemment installées sur cette liste sont désactivées et l’utilisateur ne peut pas les activer. Si vous supprimez un élément de la liste des extensions bloquées, cette extension est automatiquement réactivée partout où elle a été installée précédemment.
  
  Utilisez **\*** pour bloquer toutes les extensions qui ne sont pas explicitement répertoriées dans la liste verte. Si cette stratégie est définie sur *non configuré*, les utilisateurs peuvent installer n’importe quelle extension dans Microsoft Edge. 
  
  Exemple de valeur : extension_id1 extension_id2.  
  <br>
  - **ID d’extension l’utilisateur ne doit pas installer (ou * pour tout)**  
    Sélectionnez **Ajouter** et spécifiez des extensions supplémentaires. **\*** est sélectionné par défaut.

- **Configurer Microsoft Defender SmartScreen**  
  **Par défaut** : Activé  
  CSP Microsoft Edge : [navigateur/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  Ce paramètre de stratégie vous permet de configurer l’activation ou non de Microsoft Defender SmartScreen. Microsoft Defender SmartScreen fournit des messages d’avertissement pour vous aider à protéger vos utilisateurs contre les escroqueries de type hameçonnage et les logiciels malveillants potentiels. 
  
  - Par défaut, Microsoft Defender SmartScreen est activé. Si vous activez ce paramètre, Microsoft Defender SmartScreen est activé et les utilisateurs ne peuvent pas le désactiver.
  - Si vous désactivez ce paramètre, Microsoft Defender SmartScreen est désactivé et les utilisateurs ne peuvent pas l’activer. 
  - Lorsque la valeur *n’est pas configurée*, les utilisateurs peuvent choisir d’utiliser ou non Microsoft Defender SmartScreen. 
  
  Cette stratégie est disponible uniquement sur les instances Windows qui sont jointes à un domaine Microsoft Active Director, ou sur les instances Windows 10 professionnel ou Enterprise qui sont inscrites pour la gestion des appareils.

- **Autoriser les hôtes de messagerie natifs au niveau de l’utilisateur (installés sans autorisations d’administrateur)**  
  **Par défaut** : Désactivé  

  Active l’installation au niveau utilisateur des hôtes de messagerie natifs. 
  - Si vous désactivez cette stratégie, Microsoft Edge utilise uniquement des hôtes de messagerie natifs installés au niveau du système. Par défaut, si vous ne configurez pas cette stratégie, Microsoft Edge autorisera l’utilisation des hôtes de messagerie natif au niveau de l’utilisateur.

## <a name="next-steps"></a>Étapes suivantes

[Utiliser des lignes de base de sécurité dans Intune](security-baselines.md)
