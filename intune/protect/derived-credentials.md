---
title: Utiliser des informations d’identification dérivées pour les appareils mobiles dans Microsoft Intune - Azure | Microsoft Docs
description: Utilisez des informations d’identification dérivées sur les appareils mobiles en tant que méthode d’authentification pour les réseaux VPN Intune, la messagerie, les profils Wi-Fi, les applications, S/MIME et le chiffrement. Les informations d’identification dérivées sont une implémentation des recommandations de la publication spéciale 800-157 du NIST.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1716da820fd0d9a4b6d1bbc5024440cfb141c5a1
ms.sourcegitcommit: 0d6f323152ec62f7d383891cce12ea0a4289cd8f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889547"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Utiliser des informations d’identification dérivées dans Microsoft Intune

*Cet article s’applique aux appareils qui exécutent iOS*

Dans un environnement où des cartes à puce sont requises pour l’authentification, le chiffrement et la signature, vous pouvez désormais utiliser Intune pour provisionner des appareils mobiles avec un certificat dérivé de la carte à puce d’un utilisateur. Ce certificat est appelé *informations d’identification dérivées*. Intune [prend en charge plusieurs émetteurs d’informations d’identification dérivées](#supported-issuers), même si vous ne pouvez utiliser qu’un seul émetteur par locataire à la fois. 

Les informations d’identification dérivées sont une implémentation des recommandations du NIST (National Institute of Standards and Technology) en matière d’informations d’identification de vérification de l’identité personnelle (PIV) dérivées, fournies dans la publication spéciale (SP) 800-157.  

**Avec l’implémentation d’Intune** :  

- L’administrateur Intune configure le locataire pour qu’il fonctionne avec un émetteur d’informations d’identification dérivées pris en charge. Vous n’avez pas besoin de configurer de paramètres Intune spécifiques dans le système de l’émetteur d’informations d’identification dérivées.

- L’administrateur Intune spécifie **Informations d’identification dérivées** en tant que *méthode d’authentification* pour les objets suivants :  

  - Types de profils courants, comme pour le Wi-Fi, les réseaux VPN et la messagerie, qui incluent l’application de messagerie native iOS 

  - Authentification des applications

  - Signature et chiffrement S/MIME 

- Les utilisateurs obtiennent des informations d’identification dérivées à l’aide de leur carte à puce sur un ordinateur pour s’authentifier auprès de l’émetteur d’informations d’identification dérivées. L’émetteur émet ensuite pour l’appareil mobile un certificat dérivé de sa carte à puce. 

- Une fois que l’appareil a reçu les informations d’identification dérivées, il les utilise pour s’authentifier et pour la signature et le chiffrement S/MIME lorsque des applications ou des profils d’accès aux ressources nécessitent les informations d’identification dérivées. 

## <a name="prerequisites"></a>Prérequis

Passez en revue les informations suivantes avant de configurer votre locataire de manière à utiliser des informations d’identification dérivées.

### <a name="supported-platforms"></a>Plateformes prises en charge

Intune prend en charge les informations d’identification dérivées sur les plateformes de système d’exploitation suivantes :
- iOS/iPadOS
 
### <a name="supported-issuers"></a>Émetteurs pris en charge

Intune prend en charge un seul émetteur d’informations d’identification dérivées par locataire. Vous pouvez configurer Intune pour qu’il fonctionne avec les émetteurs suivants :  

- **DISA Purebred** : https://cyber.mil/pki-pke/purebred/ 
- **Entrust Datacard** : https://www.entrustdatacard.com/
- **Intercede** : https://www.intercede.com/

Pour connaître les informations importantes à savoir sur les différents émetteurs, consultez l’aide correspondante<!-- , including the issuers end-user workflow-->. Pour plus d’informations, consultez [Planifier l’obtention d’informations d’identification dérivées](#plan-for-derived-credentials) dans cet article.

> [!IMPORTANT]  
> Si vous supprimez un émetteur d’informations d’identification dérivées de votre locataire, les informations d’identification dérivées qui ont été configurées par le biais de cet émetteur ne fonctionneront plus.  
> 
> Consultez [Changer d’émetteur d’informations d’identification dérivées](#change-the-derived-credential-issuer) plus loin dans cet article.   

### <a name="company-portal-app"></a>Application Portail d’entreprise

Planifiez le déploiement de l’application Portail d’entreprise Intune sur les appareils qui s’inscriront pour obtenir des informations d’identification dérivées. Les utilisateurs d’appareils utilisent l’application Portail d’entreprise pour démarrer le processus d’inscription pour obtenir des informations d’identification. 

Pour les appareils iOS, consultez [Ajouter des applications de l’App Store iOS dans Microsoft Intune](../apps/store-apps-ios.md).

## <a name="plan-for-derived-credentials"></a>Planifier l’obtention d’informations d’identification dérivées

Tenez compte des points suivants avant de configurer un émetteur d’informations d’identification dérivées.  

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) Passer en revue la documentation relative à l’émetteur d’informations d’identification dérivées que vous choisissez  

Avant de configurer un émetteur, passez en revue la documentation de cet émetteur pour comprendre comment son système fournit des informations d’identification dérivées aux appareils.  

Selon l’émetteur que vous choisissez, vous devrez peut-être disposer d’un personnel disponible au moment de l’inscription pour aider les utilisateurs à exécuter le processus. Vous devez également passer en revue vos configurations Intune actuelles pour vous assurer qu’elles ne bloquent pas l’accès requis aux appareils et utilisateurs pour effectuer la demande d’informations d’identification. 

Par exemple, vous pouvez utiliser un accès conditionnel pour bloquer l’accès des appareils non conformes à la messagerie. Si vous vous fiez aux notifications par e-mail pour informer les utilisateurs qu’ils doivent démarrer le processus d’inscription pour obtenir des informations d’identification dérivées, il se peut que vos utilisateurs ne recevront ces instructions qu’une fois qu’ils seront conformes à la stratégie.  

De même, certains flux de travail de demande d’informations d’identification dérivées requièrent l’utilisation de la caméra de l’appareil pour scanner un code QR à l’écran. Ce code lie cet appareil à la demande d’authentification reçue par l’émetteur d’informations d’identification dérivées avec les informations d’identification de la carte à puce de l’utilisateur. Si les stratégies de configuration d’appareil bloquent l’utilisation de l’appareil photo, l’utilisateur ne peut pas terminer la demande d’obtention d’informations d’identification dérivées.  

Informations générales :  

- Vous ne pouvez configurer qu’un seul émetteur par locataire à la fois et cet émetteur est disponible pour tous les utilisateurs et appareils pris en charge dans votre locataire.

- Les utilisateurs ne recevront une notification leur indiquant qu’ils doivent s’inscrire pour obtenir des informations d’identification dérivées que lorsque vous les ciblerez avec une stratégie nécessitant des informations d’identification dérivées.

- La notification peut être envoyée via une notification d’application pour le Portail d’entreprise, via e-mail, ou les deux. Si vous choisissez d’utiliser les notifications par e-mail et que vous utilisez un accès conditionnel, les utilisateurs peuvent ne pas recevoir la notification par e-mail si leur appareil n’est pas conforme.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) Examiner le flux de travail de l’utilisateur final pour l’émetteur que vous avez choisi

Voici les principales considérations à prendre en compte pour chacun des partenaires pris en charge<!--  , and links to that issuers end-user workflow -->.  Familiarisez-vous avec ces informations afin de vous assurer que vos stratégies et configurations Intune n’empêchent pas les utilisateurs et les appareils d’effectuer correctement leur inscription pour obtenir des informations d’identification dérivées de cet émetteur.

#### <a name="disa-purebred"></a>DISA Purebred

Familiarisez-vous avec le workflow des utilisateurs finaux et les principales conditions requises :  
<!-- TEMP EDIT - preceeding line to be replaced with the following once user content is ready. 
Review the [user workflow for DISA Purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). Key requirements for this workflow include:  
-->

- Les utilisateurs doivent avoir accès à un ordinateur ou à une borne où ils peuvent utiliser leur carte à puce pour s’authentifier auprès de l’émetteur. 

- Les appareils qui s’inscriront pour obtenir des informations d’identification dérivées doivent installer l’application Portail d’entreprise Intune.

- Utilisez Intune pour [déployer l’application DISA Purebred](#deploy-the-disa-purebred-app) sur les appareils qui s’inscriront pour obtenir des informations d’identification dérivées. Cette application doit être déployée via Intune afin d’être gérée et peut ensuite fonctionner avec l’application Portail d’entreprise Intune. Cette application est utilisée par les utilisateurs d’appareils pour effectuer la demande d’informations d’identification dérivées. 

- L’application DISA Purebred requiert un [VPN par application](../configuration/vpn-settings-configure.md) pour s’assurer que l’application peut accéder à DISA Purebred lors de l’inscription afin d’obtenir des informations d’identification dérivées. 

- Les utilisateurs d’appareils doivent travailler avec un agent en ligne au cours du processus d’inscription. Au cours de l’inscription, des codes secrets à usage unique et à durée limitée sont fournis à l’utilisateur au fur et à mesure du processus d’inscription.   

Pour obtenir des informations sur l’obtention et la configuration de l’application DISA Purebred, consultez [Déployer l’application DISA Purebred](#deploy-the-disa-purebred-app) plus loin dans cet article.  

#### <a name="entrust-datacard"></a>Entrust Datacard  

Familiarisez-vous avec le workflow des utilisateurs finaux et les principales conditions requises :  
<!-- TEMP EDIT - preceeding line to be replaced with the following once user content is ready. 
Review the [user workflow for Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust). Key requirements for this workflow include: 
--> 
- Les utilisateurs doivent avoir accès à un ordinateur ou à une borne où ils peuvent utiliser leur carte à puce pour s’authentifier auprès de l’émetteur. 

- Les appareils qui s’inscriront pour obtenir des informations d’identification dérivées doivent installer l’application Portail d’entreprise Intune.

- L’appareil photo de l’appareil doit être utilisé pour scanner un code QR qui lie la demande d’authentification à la demande d’informations d’identification dérivées de l’appareil mobile.

#### <a name="intercede"></a>Intercede

Familiarisez-vous avec le workflow des utilisateurs finaux et les principales conditions requises :  
<!-- TEMP EDIT - preceeding line to be replaced with the following once user content is ready. 
Review the [user workflow for Intercede](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). Key requirements for this workflow include: 
-->
- Les utilisateurs doivent avoir accès à un ordinateur ou à une borne où ils peuvent utiliser leur carte à puce pour s’authentifier auprès de l’émetteur. 

- Les appareils qui s’inscriront pour obtenir des informations d’identification dérivées doivent installer l’application Portail d’entreprise Intune.

- L’appareil photo de l’appareil doit être utilisé pour scanner un code QR qui lie la demande d’authentification à la demande d’informations d’identification dérivées de l’appareil mobile.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) Déployer un certificat racine approuvé sur les appareils 

Un certificat racine approuvé est utilisé avec les informations d’identification dérivées pour vérifier que la chaîne de certificat d’informations d’identification dérivées est valide et approuvée. Même s’il n’est pas directement référencé par la stratégie, un certificat racine approuvé est requis. Consultez [Configurer un profil de certificat pour vos appareils dans Microsoft Intune](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) Fournir à l’utilisateur final des instructions pour qu’il obtienne des informations d’identification dérivées 

Créez et fournissez à vos utilisateurs des conseils sur la façon de démarrer le processus d’inscription pour obtenir des informations d’identification dérivées, et de parcourir le flux de travail d’inscription pour l’émetteur que vous avez choisi. 

Nous vous recommandons de fournir une URL qui hébergera vos conseils. Vous spécifiez cette URL lorsque vous configurez l’émetteur d’informations d’identification dérivées pour votre locataire et que cette URL est disponible dans l’application Portail d’entreprise. Si vous ne spécifiez pas votre propre URL, Intune fournit un lien vers des détails génériques. Ces détails ne peuvent pas couvrir tous les scénarios et peuvent ne pas être corrects pour votre environnement. 

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) Déployer des stratégies Intune qui requièrent des informations d’identification dérivées 

Créez de nouvelles stratégies ou modifiez des stratégies existantes pour utiliser les informations d’identification dérivées. Les informations d’identification dérivées remplacent d’autres méthodes d’authentification pour l’authentification auprès des applications, du Wi-Fi, des réseaux VPN et de la messagerie, ainsi que pour la signature et le chiffrement S/MIME. 

Évitez d’exiger l’utilisation d’informations d’identification dérivées pour accéder à un processus que vous utiliserez dans le cadre du processus d’obtention d’informations d’identification dérivées, car cela peut empêcher les utilisateurs d’effectuer la demande. 

## <a name="set-up-a-derived-credential-issuer"></a>Configurer un émetteur d’informations d’identification dérivées

Avant de créer des stratégies qui nécessitent l’utilisation d’informations d’identification dérivées, configurez un émetteur d’informations d’identification dans la console Intune. Un émetteur d’informations d’identification dérivées est un paramètre à l’échelle du locataire. Les locataires prennent en charge un seul émetteur à la fois. 

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et accédez à **Configuration de l’appareil** > **Informations d’identification dérivées**.  

   ![Configurer les informations d’identification dérivées dans la console](./media/derived-credentials/configure-provider.png)   

2. Spécifiez un **nom complet** convivial pour la stratégie d’émetteur d’informations d’identification dérivées.  Ce nom n’est pas indiqué à vos utilisateurs d’appareils.

3. Pour **Émetteur des informations d’identification dérivées**, sélectionnez l’émetteur d’informations d’identification dérivées que vous avez choisi pour votre locataire :
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

4. Spécifiez une **URL d’aide sur les informations d’identification dérivées** pour fournir un lien vers un emplacement contenant des instructions personnalisées qui aideront les utilisateurs à obtenir des informations d’identification dérivées pour votre organisation. Ces instructions doivent être spécifiques à votre organisation et au workflow nécessaire pour obtenir des informations d’identification auprès de l’émetteur que vous avez choisi. Le lien est fourni dans l’application Portail d’entreprise et doit être accessible depuis l’appareil. 

   Si vous ne spécifiez pas votre propre URL, Intune fournit un lien vers des détails génériques qui ne peuvent pas couvrir tous les scénarios. Ces instructions générales risquent de ne pas être exactes pour votre environnement.

5. Sélectionnez une ou plusieurs options pour **Type de notification**. Les types de notification sont les méthodes que vous utilisez pour informer les utilisateurs au sujet des scénarios suivants :

   - Inscrire un appareil auprès d’un émetteur pour obtenir de nouvelles informations d’identification dérivées. 
   - Obtenir de nouvelles informations d’identification dérivées lorsque les informations d’identification actuelles sont sur le point d’expirer. 
   - Utiliser des informations d’identification dérivées avec une stratégie pour l’authentification auprès des applications, du Wi-Fi, des réseaux VPN et de la messagerie, ainsi que pour la signature et le chiffrement S/MIME. 

6. Quand vous êtes prêt, sélectionnez **Enregistrer** pour terminer la configuration de l’émetteur d’informations d’identification dérivées. 

Une fois la configuration enregistrée, vous pouvez apporter des modifications dans tous les champs, à l’exception de *Émetteur des informations d’identification dérivées*.  Pour changer d’émetteur, consultez [Changer d’émetteur d’informations d’identification dérivées](#change-the-derived-credential-issuer). 

## <a name="deploy-the-disa-purebred-app"></a>Déployer l’application DISA Purebred

*Cette section s’applique uniquement lorsque vous utilisez DISA Purebred*.

Pour utiliser **DISA Purebred** en tant qu’émetteur d’informations d’identification dérivées pour Intune, vous devez obtenir l’application DISA Purebred, puis utiliser Intune pour la déployer sur les appareils. Les utilisateurs d’appareils utilisent cette application sur leur appareil pour demander les informations d’identification dérivées auprès de DISA Purebred. 

Outre le déploiement de l’application avec Intune, configurez un VPN par application Intune pour l’application DISA Purebred. 

**Réalisez les tâches suivantes** : 
  
1. Téléchargez l’[application DISA Purebred](https://cyber.mil/pki-pke/purebred/).
2. Déployez l’application DISA Purebred dans Intune.  Consultez [Ajouter une application métier iOS à Microsoft Intune](../apps/lob-apps-ios.md).
3. [Créez un VPN par application](../configuration/vpn-settings-configure.md) pour l’application DISA Purebred.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Utiliser des informations d’identification dérivées pour l’authentification, ainsi que pour le chiffrement et la signature S/MIME

Vous pouvez spécifier des **informations d’identification dérivées** pour les types de profils et les objectifs suivants :  
- [Applications](#use-derived-credentials-for-app-authentication)
- [Courrier électronique](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [Chiffrement et signature S/MIME](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  Pour les profils Wi-Fi, la *méthode d’authentification* est disponible uniquement lorsque le **type EAP** est défini sur l’une des valeurs suivantes : 
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Utiliser des informations d’identification dérivées pour l’authentification auprès des applications

Utilisez des informations d’identification dérivées pour bénéficier d’une authentification basée sur un certificat auprès des applications et des sites web. Pour fournir des informations d’identification dérivées pour une authentification auprès des applications, procédez comme suit dans la console Intune :  

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), accédez à **Configuration de l’appareil** > **Profils**et sélectionnez **Créer un profil**.

2. Entrez un nom convivial pour le profil, sous **Nom**.

3. Pour l’option **Plateforme**, sélectionnez **iOS**.

4. Pour **Type de profil**, sélectionnez **Informations d’identification dérivées**.

5. Sélectionnez **OK**, puis cliquez sur **Créer**.

6. Sélectionnez **Affectations** pour choisir les groupes qui doivent recevoir la stratégie.
 
Les utilisateurs reçoivent l’application ou une notification par e-mail selon les paramètres que vous avez spécifiés quand vous avez configuré l’émetteur d’informations d’identification dérivées. La notification informe l’utilisateur qu’il doit lancer l’application Portail d’entreprise pour que les stratégies d’informations d’identification dérivées puissent être traitées.

## <a name="renew-a-derived-credential"></a>Renouveler des informations d’identification dérivées

Les informations d’identification dérivées ne peuvent pas être étendues ni renouvelées. Au lieu de cela, les utilisateurs doivent utiliser le flux de travail de demande d’informations d’identification pour demander de nouvelles informations d’identification dérivées pour leur appareil.

Si vous configurez une ou plusieurs méthodes pour **Type de notification**, Intune avertit automatiquement les utilisateurs lorsque les informations d’identification dérivées actuelles atteignent 80 % de leur durée de vie. La notification indique aux utilisateurs de suivre le processus de demande d’informations d’identification pour obtenir de nouvelles informations d’identification dérivées. 

Une fois qu’un appareil a reçu de nouvelles informations d’identification dérivées, les stratégies qui utilisent des informations d’identification dérivées sont redéployées sur cet appareil. 


## <a name="change-the-derived-credential-issuer"></a>Changer d’émetteur d’informations d’identification dérivées

Au niveau du locataire, vous pouvez changer d’émetteur d’informations d’identification, même si un seul émetteur est pris en charge pour un locataire à la fois. 

Après avoir changé d’émetteur, les utilisateurs sont invités à obtenir de nouvelles informations d’identification dérivées auprès du nouvel émetteur. Ils doivent le faire avant de pouvoir utiliser des informations d’identification dérivées pour l’authentification.

### <a name="change-the-issuer-for-your-tenant"></a>Changer d’émetteur pour votre locataire

> [!IMPORTANT]  
> Si vous supprimez un émetteur et reconfigurez immédiatement le même émetteur, vous devez encore mettre à jour les profils et les appareils pour utiliser les informations d’identification dérivées de cet émetteur. Les informations d’identification dérivées obtenues avant la suppression de l’émetteur ne sont plus valides. 

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et accédez à **Configuration de l’appareil** > **Informations d’identification dérivées**.

2. Sélectionnez **Supprimer** pour supprimer l’émetteur d’informations d’identification dérivées actuel.

3. Configurez un nouvel émetteur. 


### <a name="update-profiles-that-use-derived-credentials"></a>Mettre à jour les profils qui utilisent des informations d’identification dérivées

Après avoir supprimé un émetteur, puis en avoir ajouté un nouveau, modifiez chaque profil qui utilise des informations d’identification dérivées. Cette règle s’applique même si vous restaurez l’émetteur précédent. Toute modification du profil déclenche une mise à jour, y compris une simple modification de la *description* du profil.

### <a name="update-derived-credentials-on-devices"></a>Mettre à jour les informations d’identification dérivées sur les appareils

Après avoir supprimé un émetteur, puis en avoir ajouté un nouveau, les utilisateurs d’appareils doivent demander de nouvelles informations d’identification dérivées. Cette règle s’applique même lorsque vous ajoutez l’émetteur que vous avez supprimé. Le processus de demande de nouvelles informations d’identification dérivées est le même que celui utilisé pour l’inscription d’un nouvel appareil ou le renouvellement d’informations d’identification existantes. 

## <a name="next-steps"></a>Étapes suivantes

[Créer des profils de configuration d’appareil](../configuration/device-profile-create.md)


 