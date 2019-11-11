---
title: Résolution des problèmes d’inscription d’appareils Windows dans Microsoft Intune
titleSuffix: Microsoft Intune
description: Suggestions pour la résolution des problèmes les plus courants lors de l’inscription d’appareils Windows dans Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 348768be4a42667f579df0ccb500434425258db0
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712860"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Résolution des problèmes d’inscription d’appareils Windows dans Microsoft Intune

Cet article aide les administrateurs Intune à comprendre et à résoudre les problèmes liés à l’inscription d’appareils Windows dans Intune.

## <a name="prerequisites"></a>Prérequis
Avant de commencer le dépannage, il est important de recueillir des informations de base. Ces informations peuvent vous aider à mieux comprendre le problème et à réduire le temps nécessaire pour trouver une solution.

Collectez les informations suivantes sur le problème :
- Une licence Intune valide est-elle attribuée à l’utilisateur ? Avant que les utilisateurs puissent inscrire leurs appareils, ils doivent disposer de la licence nécessaire.
- La dernière mise à jour est-elle installée sur l’appareil Windows ? Certaines fonctionnalités d’Intune fonctionnent uniquement avec la dernière version de Windows. De nombreux correctifs pour les problèmes connus sont disponibles par le biais de Windows Update. L’application de toutes les mises à jour les plus récentes résout souvent un problème d’inscription d’appareils Windows. 
- Quel est le message d’erreur exact ?
- Où s’affiche le message d’erreur ?
- Quand le problème a-t-il commencé ? L’inscription a-t-elle déjà fonctionné ? 
- Quelle plateforme (Android, iOS, Windows) rencontre le problème ?
- Combien d’utilisateurs sont affectés ? Tous les utilisateurs sont-ils affectés ou juste quelques-uns ?
- Combien d’appareils sont affectés ? Tous les appareils sont-ils affectés ou simplement certains ?
- Qu’est-ce que l’autorité MDM ? Si c’est System Center Configuration Manager, quelle version de Configuration Manager utilisez-vous ?
- Comment l’inscription est-elle effectuée ? S’agit-il d’un BYOD (Bring Your Own Device) ou d’Apple Programme d’inscription des appareils (DEP) avec des profils d’inscription ?

## <a name="error-messages"></a>Messages d'erreur

### <a name="this-user-is-not-authorized-to-enroll"></a>L’inscription de cet utilisateur n’est pas autorisée.

Erreur 0x801c003 : «cet utilisateur n’est pas autorisé à s’inscrire. Vous pouvez réessayer de le faire ou contactez votre administrateur système avec le code d’erreur (0x801c0003).
Erreur 80180003 : « Un problème s’est produit. L’inscription de cet utilisateur n’est pas autorisée. Vous pouvez réessayer de le faire ou contactez votre administrateur système avec le code d’erreur 80180003.»

**Cause :** L’une des conditions suivantes : 

- L’utilisateur a déjà inscrit le nombre maximal d’appareils autorisés dans Intune.    
- L’appareil est bloqué par les restrictions de type d’appareil.    
- L’ordinateur exécute Windows 10 famille. Toutefois, l’inscription dans Intune ou la jonction de Azure AD est prise en charge uniquement sur Windows 10 professionnel et versions ultérieures.

#### <a name="resolution"></a>Résolution
Il existe plusieurs solutions possibles à ce problème :

##### <a name="remove-devices-that-were-enrolled"></a>Supprimer les appareils qui ont été inscrits
1. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).    
2. Accédez à **utilisateurs**  > **tous les utilisateurs**.    
3. Sélectionnez le compte d’utilisateur affecté, puis cliquez sur **périphériques**.    
4. Sélectionnez les appareils inutilisés ou indésirables, puis cliquez sur **supprimer**. 

##### <a name="increase-the-device-enrollment-limit"></a>Augmenter la limite d’inscriptions d’appareils

> [!NOTE]
> Cette méthode augmente la limite d’inscription d’appareils pour tous les utilisateurs, pas seulement pour l’utilisateur affecté.

1. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Accédez à **inscription d’appareil**  > **restrictions d’inscription**, puis sélectionnez restrictions de **limite d’appareils**.    
3. Augmentez la valeur de la limite de l' **appareil**. 

##### <a name="check-device-type-restrictions"></a>Vérifier les restrictions de type d’appareil
1. Connectez-vous au [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) à l’aide d’un compte d’administrateur général.
2. Accédez à **inscription d’appareil**  > **restrictions d’inscription**, puis sélectionnez la restriction **par défaut** sous restrictions de **type d’appareil**.    
3. Sélectionnez **plateformes**, puis sélectionnez **autoriser** pour **Windows (MDM)** .

    > [!IMPORTANT]
    > Si le paramètre actuel est déjà **autorisé**, remplacez-le par **bloquer**, enregistrez le paramètre, puis réaffectez-le à la valeur **autoriser** et réenregistrez le paramètre. Cela réinitialise le paramètre d’inscription.

4. Attendez environ 15 minutes, puis réinscrivez l’appareil affecté.    

##### <a name="upgrade-windows-10-home"></a>Mettre à niveau Windows 10 Famille
[Mettez à niveau Windows 10 famille vers Windows 10 professionnel](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) ou une édition supérieure. 



### <a name="this-user-is-not-allowed-to-enroll"></a>L’inscription de cet utilisateur n’est pas autorisée.

Erreur 0x801c0003 : «cet utilisateur n’est pas autorisé à s’inscrire. Vous pouvez réessayer ou contacter votre administrateur système avec le code d’erreur 801c0003.

**Cause :** Les **utilisateurs peuvent joindre des appareils à Azure ad** paramètre est défini sur **aucun**. Cela empêche les nouveaux utilisateurs de joindre leurs appareils à Azure AD. Par conséquent, l’inscription Intune échoue.

#### <a name="resolution"></a>Résolution
1. Connectez-vous au [portail Azure](https://portal.azure.com/) en tant qu’administrateur.    
2. Accédez à **Azure Active Directory**  > **appareils**  > **paramètres**de l’appareil.    
3. Définissez **Les utilisateurs peuvent joindre des appareils à Azure AD** sur **Tous**.    
4. Réinscrivez l’appareil.   

### <a name="the-device-is-already-enrolled"></a>L’appareil est déjà inscrit.

Erreur 8018000a : «un problème est survenu. L’appareil est déjà inscrit.  Vous pouvez contacter votre administrateur système avec le code d’erreur 8018000a.

**Cause :** si une des conditions suivantes est vraie :
- Un autre utilisateur a déjà inscrit l’appareil dans Intune ou a rejoint l’appareil pour Azure AD. Pour déterminer si c’est le cas, accédez à **paramètres**  > **comptes**  > **accès professionnel**. Recherchez un message semblable à ce qui suit : «un autre utilisateur sur le système est déjà connecté à une entreprise ou un établissement scolaire. Veuillez supprimer cette connexion professionnelle ou scolaire, puis réessayez.»    
- L’agent du client Configuration Manager est installé sur l’ordinateur.    

#### <a name="resolution"></a>Résolution

Recourez à l'une des méthodes suivantes pour résoudre cette erreur :

##### <a name="remove-the-other-work-or-school-account"></a>Supprimer l’autre compte professionnel ou scolaire
1. Déconnectez-vous de Windows, puis connectez-vous à l’aide de l’autre compte ayant inscrit ou joint l’appareil.    
2. Accédez à **paramètres**  > **comptes**  > **accès professionnel**, puis supprimez le compte professionnel ou scolaire.
3. Déconnectez-vous de Windows, puis connectez-vous à l’aide de votre compte.    
4. Inscrivez l’appareil dans Intune ou joignez l’appareil à Azure AD. 

##### <a name="remove-the-configuration-manager-client"></a>Supprimer le client Configuration Manager
Supprimez le client Configuration Manager, puis réinscrivez le périphérique.



### <a name="this-account-is-not-allowed-on-this-phone"></a>Ce compte n’est pas autorisé sur ce téléphone.

Erreur : «ce compte n’est pas autorisé sur ce téléphone. Assurez-vous que les informations que vous avez fournies sont correctes, puis réessayez ou demandez un support à votre entreprise.»

**Cause :** L’utilisateur qui a essayé d’inscrire l’appareil ne dispose pas d’une licence Intune valide.

#### <a name="resolution"></a>Résolution
Attribuez une licence Intune valide à l’utilisateur, puis inscrivez l’appareil.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Il semble que le point de terminaison des conditions d’utilisation MDM n’est pas correctement configuré.

**Cause :** si une des conditions suivantes est vraie : 
 - Vous utilisez la gestion des appareils mobiles (MDM) pour Office 365 et Intune sur le locataire, et l’utilisateur qui tente d’inscrire l’appareil ne dispose pas d’une licence Intune valide ou d’une licence Office 365.     
- Les termes et conditions MDM de Azure AD sont vides ou ne contiennent pas l’URL correcte.    

#### <a name="resolution"></a>Résolution

Pour résoudre ce problème, utilisez l’une des méthodes suivantes : 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Attribuer une licence valide à l’utilisateur
Accédez au [Centre d’administration Microsoft 365](https://portal.office.com/adminportal/home), puis attribuez une licence Intune ou Office 365 à l’utilisateur.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Corriger l’URL des conditions d’utilisation de MDM
  1. Connectez-vous au [Portail Azure](https://portal.azure.com/), puis sélectionnez **Azure Active Directory**.    
  2. Sélectionnez **mobilité (MDM et GAM)** , puis cliquez sur **Microsoft Intune**.    
  3. Sélectionnez **restaurer les URL MDM par défaut**, vérifiez que l' **URL des conditions d’utilisation MDM** est définie sur **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Choisissez **Enregistrer**.    


### <a name="something-went-wrong"></a>Un problème s’est produit.

Erreur 80180026 : « Un problème s’est produit. Vérifiez que vous utilisez les informations de connexion correctes et que votre organisation utilise cette fonctionnalité. Vous pouvez réessayer de le faire ou contactez votre administrateur système avec le code d’erreur 80180026.»

**Cause :** Cette erreur peut se produire lorsque vous essayez de joindre un ordinateur Windows 10 à Azure AD et que les deux conditions suivantes sont remplies : 
- L’inscription automatique MDM est activée dans Azure.    
- Le client Intune PC (agent du PC Intune) ou l’agent du client Configuration Manager est installé sur l’ordinateur Windows 10.

#### <a name="resolution"></a>Résolution
Recourez à l'une des méthodes suivantes pour résoudre cette erreur :

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Désactivez l’inscription automatique MDM dans Azure.
1. Connectez-vous au [portail Azure](https://portal.azure.com/).    
2. Accédez à **Azure Active Directory**  > **Mobility (MDM et gam)**  > **Microsoft Intune**.    
3. Définissez **étendue de l’utilisateur MDM** sur **aucun**, puis cliquez sur **Enregistrer**.    
     
##### <a name="uninstall"></a>Désinstaller
Désinstallez le client du PC Intune ou l’agent du client de Configuration Manager de l’ordinateur.    

### <a name="the-software-cannot-be-installed"></a>Le logiciel ne peut pas être installé.

Erreur : « le logiciel ne peut pas être installé, 0x80cf4017. »

**Cause :** Le logiciel client est obsolète.

#### <a name="resolution"></a>Résolution
1. Connectez-vous à [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Accédez à **Admin**  > **Téléchargement du logiciel client**, puis cliquez sur **Télécharger le logiciel client**.    
3. Enregistrez le package d’installation, puis installez le logiciel client. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>Le certificat du compte n’est pas valide et peut avoir expiré.

Erreur : « Le certificat du compte n’est pas valide et peut avoir expiré, 0x80cf4017. »

**Cause :** Le logiciel client est obsolète.

#### <a name="resolution"></a>Résolution
1. Connectez-vous à [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Accédez à **Admin**  > **Téléchargement du logiciel client**, puis cliquez sur **Télécharger le logiciel client**.    
3. Enregistrez le package d’installation, puis installez le logiciel client.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Votre organisation ne prend pas en charge cette version de Windows. 

Erreur : «un problème est survenu. Votre organisation ne prend pas en charge cette version de Windows.  (0x80180014) "

**Cause :** L’inscription Windows MDM est désactivée dans votre locataire Intune.

#### <a name="resolution"></a>Résolution
Pour résoudre ce problème dans un environnement Intune autonome, procédez comme suit : 
 
1. Connectez-vous au [portail Azure](https://portal.azure.com/) en tant qu’administrateur.    
2. Sélectionnez **Intune** sur la gauche, puis accédez à **inscription d’appareil**  >  restrictions d'**inscription**.    
3. Dans **restrictions de type d’appareil**, cliquez sur **plateformes**, puis sélectionnez **autoriser** pour **Windows (MDM)** .    
4. Cliquez sur **Save**.    
 
Pour résoudre ce problème dans le MDM hybride avec Intune et Configuration Manager, procédez comme suit : 
1. Ouvrez la console Configuration Manager.    
2. Sélectionnez **administration**, puis **services Cloud**.    
3. Cliquez avec le bouton droit sur **Microsoft Intune abonnement**, puis sélectionnez **configurer des plateformes > Windows**.    
4. Cochez la case **activer l’inscription Windows**  > **appliquer**  > **OK**.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Une erreur d’installation s’est produite lors de l’inscription en bloc.

**Cause :** Les comptes d’utilisateur Azure AD dans le package de comptes (Package_GUID) pour le package d’approvisionnement correspondant ne sont pas autorisés à joindre des appareils à Azure AD. Ces comptes de Azure AD sont créés automatiquement lorsque vous configurez un package d’approvisionnement à l’aide du concepteur de configuration Windows (WCD) ou de l’application configurer les PC scolaires, et ces comptes sont ensuite utilisés pour joindre les appareils à Azure AD.

#### <a name="resolution"></a>Résolution
1. Connectez-vous au [portail Azure](https://portal.azure.com/) en tant qu’administrateur.    
2. Accédez à **Azure Active Directory > appareils > paramètres**de l’appareil.    
3. Définissez **Les utilisateurs peuvent joindre des appareils à Azure AD** sur **Tous** ou **Sélectionné**.

   Si vous choisissez **sélectionné**, cliquez sur **sélectionné**, puis cliquez sur **Ajouter des membres** pour ajouter tous les utilisateurs qui peuvent joindre leurs appareils à Azure ad. Assurez-vous que tous les comptes de Azure AD pour le package de configuration sont ajoutés.
 
Pour plus d’informations sur la création d’un package d’approvisionnement pour le concepteur de configuration Windows, consultez [créer un package d’approvisionnement pour Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Pour plus d’informations sur l’application configurer les PC scolaires, consultez [utiliser l’application configurer des PC scolaires](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Inscription MDM automatique : échec 

Lorsque vous essayez d’inscrire un appareil Windows 10 automatiquement à l’aide de stratégie de groupe, vous rencontrez les problèmes suivants : 
- Dans Planificateur de tâches, sous **Microsoft**  > **Windows**  > **EnterpriseMgmt**, le résultat de la dernière exécution de la **planification créée par le client d’inscription pour s’inscrire automatiquement dans MDM à partir de** la tâche AAD est le suivant : **événement 76 Inscription MDM automatique : échec (code d’erreur Win32 inconnu : 0x8018002b)**       
- Dans observateur d’événements, l’événement suivant est enregistré sous **journaux des applications et des services/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Cause :** si une des conditions suivantes est vraie : 
- L’UPN contient un domaine non vérifié ou non routable, tel que. local (par exemple, joe@contoso.local).    
- L’étendue de l' **utilisateur MDM** est définie sur **aucune**. 

#### <a name="resolution"></a>Résolution
Si le nom d’utilisateur principal contient un domaine non vérifié ou non routable, procédez comme suit : 

1. Sur le serveur sur lequel Active Directory Domain Services (AD DS) s’exécute, ouvrez **Active Directory utilisateurs et ordinateurs** en tapant **DSA. msc** dans la boîte de dialogue **exécuter** , puis cliquez sur **OK**.    
2. Cliquez sur **utilisateurs** sous votre domaine, puis procédez comme suit :  
    - S’il n’y a qu’un seul utilisateur affecté, cliquez avec le bouton droit sur l’utilisateur, puis cliquez sur **Propriétés**. Sous l’onglet **compte** , dans la liste déroulante suffixe UPN sous **nom d’ouverture de session**de l’utilisateur, sélectionnez un suffixe UPN valide, tel que contoso.com, puis cliquez sur **OK**.    
    - S’il y a plusieurs utilisateurs affectés, sélectionnez les utilisateurs, dans le menu **action** , cliquez sur **Propriétés**. Sous l’onglet **compte** , activez la case à cocher **suffixe UPN** , sélectionnez un suffixe UPN valide, par exemple Contoso.com dans la liste déroulante, puis cliquez sur **OK**.
3. Attendez la prochaine synchronisation, ou forcez une synchronisation Delta à partir du serveur de synchronisation en exécutant les commandes suivantes dans une invite PowerShell avec élévation de privilèges :
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Si l’étendue de l' **utilisateur MDM** est définie sur **aucun**, procédez comme suit : 
 
1. Connectez-vous au [Portail Azure](https://portal.azure.com/), puis sélectionnez **Azure Active Directory**.
2. Sélectionnez **mobilité (MDM et GAM)** , puis sélectionnez **Microsoft Intune**.    
3. Définissez **étendue de l’utilisateur MDM** sur **tout**. Vous pouvez définir l’étendue de l' **utilisateur MDM** sur **some**et sélectionner les groupes qui peuvent inscrire automatiquement leurs appareils Windows 10.    
4. Affectez la valeur **aucun**à l’étendue de l' **utilisateur GAM** .


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Une erreur s’est produite lors de la création du profil AutoPilot.

**Cause :** Le format d’appellation spécifié du modèle de nom de périphérique ne répond pas aux exigences. Par exemple, vous utilisez des minuscules pour la macro série, par exemple% Serial% au lieu de% SERIAL%.

#### <a name="resolution"></a>Résolution

Assurez-vous que le format d’affectation de noms répond aux spécifications suivantes :

- Créez un nom unique pour vos appareils. Les noms doivent comporter au plus 15 caractères, et ils peuvent contenir des lettres (a-z, A-Z), des chiffres (0-9) et des traits d’union (‐).
- Les noms ne peuvent pas être constitués uniquement de chiffres.
- Les noms ne peuvent pas contenir d’espace.
- Utilisez la macro %SERIAL% pour ajouter un numéro de série spécifique du matériel. Ou bien, utilisez la valeur% RAND : < # de chiffres > la macro% pour ajouter une chaîne aléatoire de nombres, la chaîne contient < nombre de chiffres > chiffres. Par exemple, MYPC-% RAND : 6% génère un nom tel que MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Un problème s’est produit. OOBEIDPS.

**Cause :** Ce problème se produit s’il existe un proxy, un pare-feu ou un autre périphérique réseau qui bloque l’accès au fournisseur d’identité (IdP).

#### <a name="resolution"></a>Résolution
Assurez-vous que l’accès requis aux services Internet pour AutoPilot n’est pas bloqué. Pour plus d’informations, consultez [Configuration réseau requise pour Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Inscription de votre appareil pour la gestion des appareils mobiles (échec : 3, 0x801C03EA).

**Cause :** L’appareil dispose d’une puce TPM qui prend en charge la version 2,0, mais qui n’a pas encore été mise à niveau vers la version 2,0.

#### <a name="resolution"></a>Résolution
Mettez à niveau la puce TPM vers la version 2,0.

Si le problème persiste, vérifiez si le même appareil se trouve dans deux groupes attribués, chaque groupe étant affecté à un autre profil AutoPilot. S’il se trouve dans deux groupes, déterminez le profil AutoPilot qui doit être appliqué à l’appareil, puis supprimez l’attribution de l’autre profil.

Pour plus d’informations sur le déploiement d’un appareil Windows en mode plein écran avec AutoPilot, consultez [déploiement d’une borne à l’aide de Windows AutoPilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Sécurisation de votre matériel (échec : 0x800705B4).

Erreur 800705b4 : 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Cause :** L’appareil Windows ciblé ne remplit pas l’une des conditions suivantes :

- L’appareil doit disposer d’une puce TPM 2,0 physique. Les appareils avec plateforme sécurisée virtuels (par exemple, les machines virtuelles Hyper-V) ou les puces TPM 1,2 ne fonctionnent pas avec le mode de déploiement automatique.
- L’appareil doit exécuter l’une des versions suivantes de Windows :
    - Windows 10 Build 1703 ou version ultérieure.
    - Si jonction Azure AD Hybride est utilisé, Windows 10 Build 1809 ou une version ultérieure.


#### <a name="resolution"></a>Résolution
Assurez-vous que l’appareil ciblé répond à la configuration requise décrite dans la section **cause** .

Pour plus d’informations sur le déploiement d’un appareil Windows en mode plein écran avec AutoPilot, consultez [déploiement d’une borne à l’aide de Windows AutoPilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Un problème s’est produit. Code d’erreur 80070774.

Erreur 0x80070774 : un problème s’est produit. Vérifiez que vous utilisez les informations de connexion correctes et que votre organisation utilise cette fonctionnalité. Vous pouvez réessayer de le faire ou contactez votre administrateur système avec le code d’erreur 80070774.

Ce problème se produit généralement avant le redémarrage de l’appareil dans un scénario de Azure AD Hybride AutoPilot, lorsque l’appareil expire pendant l’écran de connexion initial. Cela signifie que le contrôleur de domaine est introuvable ou a été correctement atteint en raison de problèmes de connectivité. Ou que l’appareil est entré dans un État qui ne peut pas rejoindre le domaine.

**Cause :** La cause la plus courante est que jonction Azure AD Hybride est utilisé et que la fonctionnalité attribuer un utilisateur est configurée dans le profil AutoPilot. L’utilisation de la fonctionnalité attribuer un utilisateur permet d’effectuer une jonction de Azure AD sur l’appareil au cours de l’écran de connexion initial, qui place l’appareil dans un État où il ne peut pas joindre votre domaine local. Par conséquent, la fonctionnalité attribuer un utilisateur doit être utilisée uniquement dans les scénarios de connexion Azure AD standard.  La fonctionnalité ne doit pas être utilisée dans les scénarios de jonction Azure AD Hybride.

#### <a name="resolution"></a>Résolution

1. Accédez à **Intune**  >  **inscription d’appareils**  > **inscription Windows**  > **appareils**.
2. Sélectionnez l’appareil qui rencontre le problème > cliquez sur les points de suspension (...) du côté le plus à droite.
3. Sélectionnez **Annuler l’affectation** de l’utilisateur et attendez la fin du processus.
4. Vérifiez que le profil AutoPilot Azure AD Hybride est affecté avant de retenter l’installation de OOBE.

#### <a name="second-resolution"></a>Deuxième résolution
Si le problème persiste, sur le serveur qui héberge le connecteur Intune de jonction de domaine hors connexion, vérifiez si l’événement ID 30312 est consigné dans le journal du service du connecteur ODJ. L’événement 30312 ressemble à ce qui suit :

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

Ce problème est généralement lié à la délégation incorrecte des autorisations à l’unité d’organisation dans laquelle les appareils Windows AutoPilot sont créés. Pour plus d’informations, consultez [augmenter la limite du compte d’ordinateur dans l’unité d’organisation](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Ouvrez **Utilisateurs et ordinateurs Active Directory (DSA.msc)** .
2. Cliquez avec le bouton droit sur l’unité d’organisation à utiliser pour créer des ordinateurs joints à un domaine Azure AD hybride > **Déléguer le contrôle**.
3. Dans l’Assistant **Délégation de contrôle**, sélectionnez **Suivant** > **Ajouter** > **Types d’objets**.
4. Dans le volet **Types d’objets**, cochez la case **Ordinateurs**, puis sélectionnez **OK**.
5. Dans le volet **Sélectionner des utilisateurs**, des **ordinateurs** ou des **groupes**, dans la zone **Entrez les noms des objets à sélectionner**, entrez le nom de l’ordinateur où le connecteur est installé.
6. Sélectionnez **vérifier les noms** pour valider votre entrée > **OK**  > **suivant**.
7. Sélectionnez **Créer une tâche personnalisée à déléguer** > **Suivant**.
8. Cochez la case **Seulement des objets suivants dans le dossier**, puis cochez les cases **Objets ordinateur**, **Créer les objets sélectionnés dans ce dossier** et **Supprimer les objets sélectionnés dans ce dossier**.
9. Sélectionnez **Suivant**.
10. Sous **Autorisations**, cochez la case **Contrôle total**. Cette action sélectionne toutes les autres options.
11. Sélectionnez **suivant**  > **Terminer**.

## <a name="next-steps"></a>Étapes suivantes

- [Résoudre les problèmes d’inscription d’appareils dans Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Posez une question sur le forum Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consultez le blog de l’équipe de support Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Consultez le blog Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Obtenir un support pour Microsoft Intune](../fundamentals/get-support.md)
- [Rechercher les erreurs d’inscription à la cogestion](https://docs.microsoft.com/sccm/comanage/how-to-monitor#enrollment-errors)