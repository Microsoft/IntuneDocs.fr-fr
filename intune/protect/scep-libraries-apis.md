---
title: API d’intégration d’autorités de certification tierces
titleSuffix: Microsoft Intune
description: Ajoutez ou intégrez la solution SCEP GitHub afin de permettre à des autorités de certification tierces de délivrer des certificats SCEP à des appareils dans Microsoft Intune. Cette solution inclut des API Java et C# qui valident, envoient des notifications de réussite et d’échec à Intune, et utilisent une fabrique de socket SSL lors de la communication avec Intune. Découvrez également une vue d’ensemble des étapes nécessaires pour tester votre configuration d’autorité de certification SCEP.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a91f4ac69c010400478de5df9838ea1f6d2429ac
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735985"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>Utiliser des API pour ajouter des autorités de certification tierces pour SCEP à Intune

Dans Microsoft Intune, vous pouvez ajouter des autorités de certification tierces et faire en sorte qu’elles émettent et valident des certificats à l’aide du protocole SCEP (Simple Certificate Enrollment Protocol). [Ajouter une autorité de certification tierce](certificate-authority-add-scep-overview.md) fournit une vue d’ensemble de cette fonctionnalité et décrit les tâches d’administration dans Intune.

Certaines tâches de développement utilisent également une bibliothèque open source publiée par Microsoft sur GitHub.com. La bibliothèque inclut une API qui :

- Valide le mot de passe SCEP généré de manière dynamique par Intune.
- Informe Intune des certificats créés sur les appareils soumettant des requêtes SCEP.

À l’aide de cette API, votre serveur SCEP tiers s’intègre avec la solution de gestion SCEP Intune pour les appareils MDM. La bibliothèque offre une abstraction d’aspects tels que l’authentification, l’emplacement du service et l’API de service ODATA Intune par rapport à ses utilisateurs.

## <a name="scep-management-solution"></a>Solution de gestion SCEP

![Intégration d’une autorité de certification tierce SCEP avec Microsoft Intune](./media/scep-libraries-apis/scep-certificate-vendor-integration.png)

À l’aide d’Intune, les administrateurs créent des profils SCEP, puis affectent ces profils à des appareils MDM. Les profils SCEP incluent des paramètres tels que :

- L’URL du serveur SCEP
- Le certificat racine approuvé de l’autorité de certification
- Les attributs de certificats, et bien plus encore

Le profil SCEP est affecté aux appareils inscrits auprès d’Intune, et ceux-ci sont configurés avec ces paramètres. Un mot de passe de stimulation SCEP généré de manière dynamique est créé par Intune, puis affecté à l’appareil.

Cette stimulation contient :

- le mot de passe de stimulation généré de manière dynamique ;
- les détails sur les paramètres attendus dans la demande de signature de certificat envoyée par l’appareil au serveur SCEP ;
- l’heure d’expiration de la stimulation.

Intune chiffre ces informations, signe l’objet blob chiffré, puis empaquète ces détails dans le mot de passe de stimulation SCEP.

Les appareils contactant le serveur SCEP pour demander un certificat donnent ensuite ce mot de passe de stimulation SCEP. Le serveur SCEP envoie la demande de signature de certificat et le mot de passe de stimulation SCEP chiffré à Intune pour validation.  Ce mot de passe de stimulation et la demande de signature de certificat doivent réussir la phase de validation afin que le serveur SCEP émette un certificat pour l’appareil. Quand une stimulation SCEP est validée, les vérifications suivantes se produisent :


- Validation de la signature de l’objet blob chiffré
- Validation du fait que la demande n’a pas expiré
- Validation du fait que le profil cible toujours l’appareil
- Validation du fait que les propriétés de certificat demandées par l’appareil dans la demande de signature de certificat correspondent aux valeurs attendues

La solution de gestion SCEP comprend également des rapports. Un administrateur peut obtenir des informations sur l’état du déploiement du profil SCEP, ainsi que sur les certificats délivrés aux appareils.

## <a name="integrate-with-intune"></a>Intégrer à Intune

Le code d’intégration de la bibliothèque avec le protocole SCEP Intune peut être téléchargé à partir du [dépôt GitHub Microsoft/Intune-Resource-Access](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).

L’intégration de la bibliothèque dans vos produits nécessite les étapes suivantes. Pour effectuer ces étapes, vous devez savoir comment utiliser des dépôts GitHub et comment créer des solutions et des projets dans Visual Studio.

1. Inscrivez-vous pour recevoir des notifications du dépôt.
2. Clonez ou téléchargez le dépôt.
3. Accédez à l’implémentation de la bibliothèque dont vous avez besoin sous le dossier `\src\CsrValidation` (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).
4. Générez la bibliothèque en suivant les instructions fournies dans le fichier Lisez-moi.
5. Incluez la bibliothèque dans le projet qui génère votre serveur SCEP.
6. Effectuez les tâches suivantes sur le serveur SCEP :

    - Autorisez l’administrateur à configurer l’[identificateur d’application Azure, la clé d’application Azure et l’ID de locataire](#onboard-scep-server-in-azure) (dans cet article) utilisés par la bibliothèque pour l’authentification. Les administrateurs doivent être autorisés à mettre à jour la clé d’application Azure.
    - Identifiez les requêtes SCEP qui comprennent un mot de passe SCEP généré par Intune.
    - Utilisez la bibliothèque d’**API Valider la requête** pour valider les mots de passe SCEP générés par Intune.
    - Utilisez les API de notification de la bibliothèque afin d’informer Intune des certificats émis pour les requêtes SCEP qui contiennent des mots de passe SCEP générés par Intune. Informez également Intune des erreurs qui peuvent se produire lors du traitement de ces requêtes SCEP.
    - Vérifiez que le serveur enregistre suffisamment d’informations dans le journal pour aider les administrateurs à résoudre les problèmes.

7. Effectuez les [tests d’intégration](#integration-testing) (dans cet article) et résolvez les éventuels problèmes.
8. Donnez des instructions écrites au client qui expliquent :

    - Comment le serveur SCEP doit être intégré dans le portail Azure.
    - Comment obtenir l’identificateur d’application Azure et la clé d’application Azure nécessaires pour configurer la bibliothèque.

### <a name="onboard-scep-server-in-azure"></a>Intégrer le serveur SCEP dans Azure

Pour s’authentifier auprès d’Intune, le serveur SCEP a besoin d’un ID d’application Azure, d’une clé d’application Azure et d’un ID de locataire. Il doit également être autorisé à accéder à l’API Intune.

Pour obtenir ces données, l’administrateur de serveur SCEP se connecte au portail Azure, inscrit l’application, lui donne l’autorisation **API Microsoft Intune\Validation de test SCEP**, crée une clé pour l’application, puis télécharge l’ID d’application, sa clé et l’ID de locataire.

Pour obtenir des instructions sur l’inscription d’une application et l’obtention d’ID et de clés, consultez [Utiliser le portail pour créer une application et un principal du service Azure Active Directory pouvant accéder aux ressources](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

### <a name="java-library-api"></a>API de bibliothèque Java

La bibliothèque Java est implémentée en tant que projet Maven qui extrait ses dépendances quand il est généré. L’API est implémentée sous l’espace de noms `com.microsoft.intune.scepvalidation` par la classe `IntuneScepServiceClient`.

#### <a name="intunescepserviceclient-class"></a>Classe IntuneScepServiceClient

La classe `IntuneScepServiceClient` contient les méthodes utilisées par le service SCEP pour valider les mots de passe SCEP, pour informer Intune des certificats qui sont créés, et pour répertorier les erreurs éventuelles.

##### <a name="intunescepserviceclient-constructor"></a>Constructeur IntuneScepServiceClient

Signature :

```java
IntuneScepServiceClient(
    Properties configProperties)
```

Description :

Instancie et configure un objet `IntuneScepServiceClient`.

Paramètres :

    - configProperties    Objet de propriétés contenant des informations sur la configuration du client

La configuration doit inclure les propriétés suivantes :

    - AAD_APP_ID="ID d’application Azure obtenu pendant le processus d’intégration"
    - AAD_APP_KEY="Clé d’application Azure obtenue pendant le processus d’intégration"
    - TENANT="ID de locataire obtenu pendant le processus d’intégration"
    - PROVIDER_NAME_AND_VERSION="Informations permettant d’identifier votre produit et sa version"
    
Si votre solution nécessite un proxy avec ou sans authentification, vous pouvez ajouter les propriétés suivantes :

    - PROXY_HOST="Hôte d’hébergement du proxy."
    - PROXY_PORT="Port d’écoute du proxy."
    - PROXY_USER="Nom d’utilisateur à employer si le proxy utilise l’authentification de base."
    - PROXY_PASS="Mot de passe à employer si le proxy utilise l’authentification de base."

Lève :

    - IllegalArgumentException    Levée si le constructeur est exécuté sans objet de propriété approprié.

> [!IMPORTANT]
> Il est préférable d’instancier une instance de cette classe et de l’utiliser pour traiter plusieurs requêtes SCEP. Cela réduit la charge, grâce à la mise en cache des jetons d’authentification et des informations d’emplacement du service.

**Notes de sécurité**  
L’implémenteur du serveur SCEP doit protéger contre la falsification et la divulgation les données entrées dans les propriétés de configuration rendues persistantes dans le stockage. Nous vous recommandons d’utiliser les ACL et le chiffrement appropriés pour sécuriser les informations.

##### <a name="validaterequest-method"></a>Méthode ValidateRequest

Signature :

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

Description :

Valide une demande de certificat SCEP.

Paramètres :

    - transactionId         ID de transaction SCEP
    - certificateRequest    Demande de certificat PKCS #10 encodée DER, codée en Base64 sous forme de chaîne

Lève :

    - IllegalArgumentException      Levée en cas d’appel avec un paramètre qui n’est pas valide
    - IntuneScepServiceException      Levée s’il est constaté que la demande de certificat n’est pas valide
    - Exception                     Levée si une erreur non attendue se produit

> [!IMPORTANT]
> Les exceptions levées par cette méthode doivent être consignées par le serveur. Notez que les propriétés `IntuneScepServiceException` ont des informations détaillées sur la cause de l’échec de la validation de demande de certificat.

**Notes de sécurité**  

- Si cette méthode lève une exception, le serveur SCEP **ne doit pas** délivrer de certificat au client.
- Les échecs de validation de demande de certificat SCEP peuvent indiquer un problème dans l’infrastructure Intune. Ils peuvent également signifier qu’une personne malveillante essaie d’obtenir un certificat.

##### <a name="sendsuccessnotification-method"></a>Méthode SendSuccessNotification

Signature :

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

Description :

Signale à Intune qu’un certificat est créé dans le cadre du traitement d’une requête SCEP.

Paramètres :

    - transactionId           ID de transaction SCEP
    - certificateRequest      Demande de certificat PKCS #10 encodée DER, codée en Base64 sous forme de chaîne
    - certThumprint           Empreinte numérique du certificat provisionné
    - certSerialNumber        Numéro de série du certificat provisionné
    - certExpirationDate      Date d’expiration du certificat provisionné. La chaîne de date et heure doit être mise en forme en tant qu’heure UTC web (AAAA-MM-JJThh:mm:ss.sssTZD) ISO 8601.
    - certIssuingAuthority    Nom de l’autorité qui a émis le certificat

Lève :

    - IllegalArgumentException      Levée en cas d’appel avec un paramètre qui n’est pas valide
    - IntuneScepServiceException      Levée s’il est constaté que la demande de certificat n’est pas valide
    - Exception                     Levée si une erreur non attendue se produit

> [!IMPORTANT]
> Les exceptions levées par cette méthode doivent être consignées par le serveur. Notez que les propriétés `IntuneScepServiceException` ont des informations détaillées sur la cause de l’échec de la validation de demande de certificat.

**Notes de sécurité**

- Si cette méthode lève une exception, le serveur SCEP **ne doit pas** délivrer de certificat au client.
- Les échecs de validation de demande de certificat SCEP peuvent indiquer un problème dans l’infrastructure Intune. Ils peuvent également signifier qu’une personne malveillante essaie d’obtenir un certificat.

##### <a name="sendfailurenotification-method"></a>Méthode SendFailureNotification

Signature :

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

Description :

Signale à Intune qu’une erreur s’est produite lors du traitement d’une requête SCEP. Cette méthode ne doit pas être appelée pour les exceptions levées par les méthodes de cette classe.

Paramètres :

    - transactionId         ID de transaction SCEP
    - certificateRequest    Demande de certificat PKCS #10 encodée DER, codée en Base64 sous forme de chaîne
    - hResult               Code d’erreur Win32 décrivant le mieux l’erreur qui s’est produite. Voir [Codes d’erreur Win32](https://msdn.microsoft.com/library/cc231199.aspx)
    - errorDescription      Description de l’erreur qui s’est produite

Lève :

    - IllegalArgumentException      Levée en cas d’appel avec un paramètre qui n’est pas valide
    - IntuneScepServiceException      Levée s’il est constaté que la demande de certificat n’est pas valide
    - Exception                     Levée si une erreur non attendue se produit

> [!IMPORTANT]
> Les exceptions levées par cette méthode doivent être consignées par le serveur. Notez que les propriétés `IntuneScepServiceException` ont des informations détaillées sur la cause de l’échec de la validation de demande de certificat.

**Notes de sécurité**

- Si cette méthode lève une exception, le serveur SCEP **ne doit pas** délivrer de certificat au client.
- Les échecs de validation de demande de certificat SCEP peuvent indiquer un problème dans l’infrastructure Intune. Ils peuvent également signifier qu’une personne malveillante essaie d’obtenir un certificat.

##### <a name="setsslsocketfactory-method"></a>Méthode SetSslSocketFactory

Signature :

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

Description :

Utilisez cette méthode pour signaler au client qu’il doit utiliser la fabrique de socket SSL spécifiée (au lieu de la fabrique par défaut) lors des communications avec Intune.

Paramètres :

    - factory    Fabrique de socket SSL que le client doit utiliser pour les requêtes HTTPS

Lève :

    - IllegalArgumentException    Levée en cas d’appel avec un paramètre qui n’est pas valide

> [!NOTE]
> La fabrique de socket de SSL doit être définie si nécessaire avant d’exécuter les autres méthodes de cette classe.

## <a name="integration-testing"></a>Tests d’intégration

Il est indispensable de tester et de valider l’intégration correcte de votre solution à Intune. Vous trouverez ci-dessous une vue d’ensemble des étapes :

1. Configurer un [compte d’évaluation Intune](../fundamentals/account-sign-up.md).
2. Intégrer le [serveur SCEP dans le portail Azure](#onboard-scep-server-in-azure) (dans cet article).
3. [Configurer le serveur SCEP](certificates-scep-configure.md) avec les ID et la clé créés lors de l’intégration de votre serveur SCEP.
4. [Inscrire des appareils](../enrollment/device-enrollment.md) pour tester les scénarios dans la [matrice de test de scénario](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
5. [Créer un profil de certificat racine approuvé](certificates-scep-configure.md) pour votre autorité de certification de test.
6. Créer des profils SCEP pour tester les scénarios répertoriés dans la [matrice de test de scénario](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
7. [Attribuer les profils](../configuration/device-profile-assign.md) aux utilisateurs ayant inscrit leurs appareils.
8. Attendre que les appareils se synchronisent avec Intune. Ou [synchroniser manuellement les appareils](../remote-actions/device-sync.md).
9. Confirmer que le certificat racine approuvé et les [profils SCEP sont déployés sur les appareils](../configuration/device-profile-monitor.md).
10. Confirmer que le certificat racine approuvé est installé sur tous les appareils.
11. Confirmer que les certificats SCEP pour les profils affectés sont installés sur tous les appareils.
12. Confirmer que les propriétés des certificats installés correspondent aux propriétés définies dans le profil SCEP.
13. Confirmer que les certificats émis sont correctement répertoriés dans la console Intune

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’ajout d’une autorité de certification tierce](certificate-authority-add-scep-overview.md)
- [Configurer Intune](../fundamentals/setup-steps.md)
- [Inscription des appareils](../enrollment/device-enrollment.md)
- [Configurer des profils de certificat SCEP](certificates-profile-scep.md) (la configuration Connecteur/Serveur NDES Microsoft n’est pas utilisée pour ce scénario)
