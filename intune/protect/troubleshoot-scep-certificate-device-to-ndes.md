---
title: Résoudre les problèmes de communication entre un appareil géré et NDES dans Microsoft Intune | Microsoft Docs
description: Résolvez les problèmes de communication entre un appareil géré et le serveur NDES lors de l'utilisation des profils de certificat SCEP pour déployer des certificats avec Intune.
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
ms.openlocfilehash: 8c81fa9b521b0d950fb69c29f7625981e709863d
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916108"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Résoudre les problèmes de communication entre un appareil et le serveur NDES pour les profils de certificats SCEP dans Microsoft Intune

Utilisez les informations suivantes pour déterminer si un appareil qui a reçu et traité un profil de certificat Intune Simple Certificate Enrollment Protocol (SCEP) peut contacter avec succès Network Device Enrollment Service (NDES) pour présenter une demande d’accès. Sur l'appareil, une clé privée est générée et la demande de signature de certificat (CSR) et la demande d’accès sont transmises de l'appareil au serveur NDES. Pour contacter le serveur NDES, l'appareil utilise l'URI du profil de certificat SCEP.

Cet article fait référence à l'étape 2 de la [vue d’ensemble du flux de communication SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>Examiner les journaux IIS pour une connexion à partir de l'appareil

Les journaux IIS incluent le même type d'entrées pour toutes les plateformes.


1. Sur le serveur NDES, ouvrez le fichier journal IIS le plus récent présent dans le dossier suivant :   *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. Recherchez dans le journal des entrées similaires aux exemples suivants. Les deux exemples contiennent un état **200**, qui apparaît en fin de fichier :

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   And

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. Lorsque l'appareil contacte IIS, une requête HTTP GET pour mscep.dll est consignée.

   Examinez le code d’état vers la fin de cette requête :
   - **Code d’état 200** : Cet état indique que la connexion avec le serveur NDES a réussi.
   - **Code d’état 500** : Le groupe IIS_IURS n’a peut-être pas les autorisations adéquates. Voir [Code d’état 500](#status-code-500) plus loin dans cet article.
   - Si le code d’état n’est pas 200 ou 500 :

     - Voir [Tester l'URL du serveur SCEP](#test-the-scep-server-url) plus loin dans cet article pour faciliter la validation de la configuration.

     - Voir [Le code d’état HTTP dans IIS 7 et versions ultérieures](https://support.microsoft.com/help/943891) pour des informations sur les codes d'erreur moins courants.

   Si la demande de connexion n'est pas consignée du tout, le contact de l'appareil peut être bloqué sur le réseau entre l'appareil et le serveur NDES.

## <a name="review-device-logs-for-connections-to-ndes"></a>Consulter les journaux des appareils pour les connexions à NDES

### <a name="android-devices"></a>Appareils Android

Consultez le [journal OMADM des appareils](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Recherchez les entrées qui ressemblent aux suivantes, consignées lorsque l’appareil se connecte à NDES :

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

Les entrées de clés incluent les exemples de chaînes de texte suivants :

- There are 1 requests
- Received '200 OK' when sending GetCACaps(ca) to https://\<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
- Signing pkiMessage using key belonging to [dn=CN=\<username>; serial=1]


The connection is also logged by IIS in the %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ folder of the NDES server. Voici un exemple :

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="ios-and-ipados-devices"></a>Appareils iOS et iPadOS

Consultez le [journal de débogage des appareils](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Recherchez les entrées qui ressemblent aux suivantes, consignées lorsque l’appareil se connecte à NDES :

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

Les entrées de clés incluent les exemples de chaînes de texte suivants :

- operation=GetCACert
- Tentative de récupération du certificat émis
- Envoi de CSR via GET
- operation=PKIOperation

### <a name="windows-devices"></a>Appareils Windows

Sur un appareil Windows qui établit une connexion à NDES, vous pouvez afficher l'Observateur d'événements Windows des appareils et rechercher des indications d'une connexion réussie. Les connexions sont consignées sous la forme d'un identifiant d'événement **36** dans le journal *DeviceManagement-Enterprise-Diagnostics-Provide* > **Admin** des appareils.

Pour ouvrir le journal :

1. Sur l'appareil, exécutez **eventvwr.msc** pour ouvrir l'Observateur d'événements Windows.

2. Développez **Journaux des applications et services** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**.

3. Cherchez Event **36**, qui ressemble à l'exemple suivant, avec la ligne clé **SCEP : Certificate request generated successfully**: (Demande de certificat générée avec succès)

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>Résoudre les erreurs courantes

Les sections suivantes peuvent vous aider à résoudre les problèmes de connexion communs à toutes les plateformes d’appareils à NDES.

### <a name="status-code-500"></a>Code d'état 500

Les connexions qui ressemblent à l'exemple suivant, avec un code d’état 500, indiquent que le droit d'utilisateur *Emprunter l’identité d’un client après l’authentification* n'est pas attribué au groupe IIS_IURS sur le serveur NDES. La valeur d’état **500** apparaît à la fin :

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**Pour résoudre ce problème** :

1. Sur le serveur NDES, exécutez **secpol.msc** pour ouvrir la stratégie de sécurité locale.

2. Développez **Stratégies locales**, puis cliquez sur **Attribution des droits utilisateur**.

3. Double-cliquez sur **Emprunter l'identité d'un client après authentification** dans le volet de droite.

4. Cliquez sur **Ajouter un utilisateur ou un groupe...** , entrez **IIS_IURS** dans le champ **Entrez les noms d’objets à sélectionner**, puis cliquez sur **OK**.

5. Cliquez sur **OK**.

6. Redémarrez l'ordinateur, puis retestez la connexion à partir de l'appareil.

### <a name="test-the-scep-server-url"></a>Tester l'URL du serveur SCEP

Utilisez les étapes suivantes pour tester l'URL spécifiée dans le profil du certificat SCEP.

1. Dans Intune, modifiez votre profil de certificat SCEP et copiez l'URL du serveur. L’URL devrait ressembler à *https://contoso.com/certsrv/mscep/msecp.dll* .

2. Ouvrez un navigateur web, puis naviguez jusqu'à l'URL de ce serveur SCEP. Le résultat devrait être : **HTTP Error 403.0 – Forbidden**. Ce résultat indique que l'URL fonctionne correctement.

   Si vous ne recevez pas cette erreur, sélectionnez le lien qui ressemble à l'erreur que vous voyez afin d’afficher des conseils spécifiques au problème :
   - [Je reçois un message Network Device Enrollment Service général](#general-ndes-message)
   - [Je reçois un message « HTTP Error 503. The service is unavailable »](#http-error-503)
   - [Je reçois l’erreur « GatewayTimeout »](#gatewaytimeout)
   - [Je reçois le message « HTTP 414 Request-URI Too Long »](#http-414-request-uri-too-long)
   - [Je reçois le message « This page can't be displayed »](#this-page-cant-be-displayed)
   - [Je reçois le message « 500 - Internal server error »](#internal-server-error)

#### <a name="general-ndes-message"></a>Message NDES général

Lorsque vous accédez à l'URL du serveur SCEP, vous recevez le message Network Device Enrollment Service suivant :

![URL du serveur SCEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **Cause** : Ce problème est généralement lié à l'installation de Microsoft Intune Connector.

  Mscep.dll est une extension ISAPI qui intercepte les requêtes entrantes et affiche l'erreur HTTP 403 si elle est installée correctement.
  
  **Résolution** : Consultez le fichier *SetupMsi.log* pour déterminer si Microsoft Intune Connector est installé correctement. Dans l'exemple suivant, *Installation effectuée avec succès* et *Réussite de l'installation ou état d'erreur : 0* indiquent une installation réussie :

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  Si l'installation échoue, supprimez Microsoft Intune Connector puis réinstallez-le.

#### <a name="http-error-503"></a>Erreur HTTP 503

Lorsque vous accédez à l’URL du serveur SCEP, vous recevez l’erreur suivante :

![Erreur HTTP 503. Service non disponible](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

Ce problème est généralement dû au fait que le pool d'applications **SCEP** dans IIS n'est pas lancé. Sur le serveur NDES, ouvrez le **Gestionnaire des services Internet** et accédez à **Pools d'applications**. Localisez le pool d’applications **SCEP** et confirmez qu'il est lancé.

Si le pool d'applications SCEP n'est pas lancé, vérifiez le journal des événements de l'application sur le serveur :

1. Sur l'appareil, exécutez **eventvwr.msc** pour ouvrir l’**Observateur d'événements**, puis accédez à **Journaux Windows** > **Application**.

2. Recherchez un événement similaire à l'exemple suivant, indiquant que le pool d’applications se bloque à la réception d’une requête :

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**Causes courantes d'un crash de pool d'applications** :

- **Cause 1** : Il existe des certificats CA intermédiaires (non autosignés) dans le magasin de certificats des autorités de certification racine de confiance du serveur NDES.

  **Résolution** : Supprimez les certificats intermédiaires du magasin de certificats Autorités de certification racines de confiance, puis redémarrez le serveur NDES.
  
  Pour identifier tous les certificats intermédiaires du magasin de certificats des autorités de certification racines de confiance, exécutez l’applet de commande PowerShell suivante : `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  Un certificat qui affiche les mêmes valeurs **Issued to** (Émis à) et **Issued by** (Émis par) est un certificat racine. Sinon, il s'agit d'un certificat intermédiaire.

  Après avoir supprimé les certificats et redémarré le serveur, exécutez à nouveau l’applet de commande PowerShell pour confirmer qu'il n'y a pas de certificats intermédiaires. S'il y en a, vérifiez si une stratégie de groupe envoie (push) les certificats intermédiaires au serveur NDES. Dans ce cas, excluez le serveur NDES de la stratégie de groupe puis supprimez à nouveau les certificats intermédiaires.

- **Cause 2** : Les URL de la liste de révocation des certificats (CRL) sont bloquées ou inaccessibles pour les certificats utilisés par Intune Certificate Connector.

  **Résolution** : Activez la journalisation supplémentaire afin de recueillir plus d'informations :
  1. Ouvrez l’Observateur d'événements, cliquez sur **Afficher**, puis vérifiez que l'option **Afficher les journaux d'analyse et de débogage** est cochée.
  2. Accédez à **Journaux des applications et des services** > **Microsoft** > **Windows** > **CAPI2** > **Opérationnel**, cliquez avec le bouton droit sur **Opérationnel**, puis sélectionnez **Activer le journal**.
  3. Après avoir activé la journalisation CAPI2, reproduisez le problème, puis consultez le journal des événements pour résoudre le problème.

- **Cause 3** : **Authentification Windows** est activée pour l’autorisation IIS **CertificateRegistrationSvc**.

  **Résolution** : Activez **Authentification anonyme**, désactivez **Authentification Windows**, puis redémarrez le serveur NDES.

  ![Autorisation IIS](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

Lorsque vous accédez à l’URL du serveur SCEP, vous recevez l’erreur suivante :

![Erreur Gatewaytimeout](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **Cause** : Le service **Connecteur proxy d'application Microsoft AAD** n’est pas démarré.

  **Résolution** :  Exécutez **services.msc**, puis vérifiez que le service **Connecteur proxy d'application Microsoft AAD** est en cours d’exécution et que l’option **Type de démarrage** est définie sur **Automatique**.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 Request-URI Too Long

Lorsque vous accédez à l’URL du serveur SCEP, vous recevez l’erreur suivante : `HTTP 414 Request-URI Too Long`

- **Cause** : Le filtrage des demandes IIS n’est pas configuré pour prendre en charge les URL longues (requêtes) que le service NDES reçoit. Cette prise en charge est configurée lorsque vous [configurez le service NDES](certificates-scep-configure.md#configure-the-ndes-service) afin de l'utiliser avec votre infrastructure pour SCEP.

- **Résolution** : Configurez la prise en charge pour les URL longues.

  1. Sur le serveur NDES, ouvrez le Gestionnaire IIS, sélectionnez **Site web par défaut** > **Filtrage des demandes** > **Modifier les paramètres de la fonctionnalité** pour ouvrir la page **Modifier les paramètres de filtrage des demandes**.

  2. Configurez les paramètres suivants :
     - **Longueur maximale des URL (octets)** = 65534
     - **Longueur maximale des chaînes de requête (octets)** = 65534

  3. Sélectionnez **OK** pour enregistrer cette configuration et fermer le Gestionnaire IIS.

  4. Validez cette configuration en localisant la clé de Registre suivante pour confirmer qu’elle a les valeurs indiquées :

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     Les valeurs suivantes sont définies comme des entrées DWORD :
     - Nom : **MaxFieldLength**, avec une valeur décimale de **65534**
     - Nom : **MaxRequestBytes**, avec une valeur décimale de **65534**

  5. Redémarrez le serveur NDES.

#### <a name="this-page-cant-be-displayed"></a>This page can't be displayed

Vous avez configuré le proxy d'application Azure AD. Lorsque vous accédez à l’URL du serveur SCEP, vous recevez l’erreur suivante :

`This page can't be displayed`

- **Cause** : Ce problème survient lorsque l'URL externe SCEP est incorrecte dans la configuration du proxy d'application. https://contoso.com/certsrv/mscep/mscep.dll est un exemple d’URL.

  **Résolution** : Utilisez le domaine par défaut *yourtenant.msappproxy.net* pour l'URL externe SCEP dans la configuration du proxy d'application.

#### <a name="internal-server-error"></a>500 - Internal server error

Lorsque vous accédez à l’URL du serveur SCEP, vous recevez l’erreur suivante :

![500 - Internal server error](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **Cause 1** : Le compte du service NDES est verrouillé ou son mot de passe a expiré.

  **Résolution** : Déverrouillez le compte ou réinitialisez le mot de passe.

- **Cause 2** : Les certificats MSCEP-RA ont expiré.

  **Résolution** : Si les certificats MSCEP-RA ont expiré, réinstallez le rôle NDES ou demandez de nouveaux certificats Chiffrement CEP et Agent d’inscription Exchange (demande hors connexion).

  Pour demander de nouveaux certificats, procédez comme suit :

  1. Sur l'autorité de certification (CA) ou l’autorité de certification émettrice, ouvrez le MMC Modèles de certificats. Assurez-vous que l'utilisateur connecté et le serveur NDES disposent des autorisations **Lecture** et **Inscription** pour les modèles de certificats Chiffrement CEP et Agent d’inscription Exchange (demande hors connexion).

  2. Vérifiez les certificats expirés sur le serveur NDES, puis copiez les informations **Objet** du certificat.

  3. Ouvrez le MMC des certificats pour **Compte d'ordinateur**.

  4. Développez **Personnel**, cliquez avec le bouton droit sur **Certificats**, puis sélectionnez **Toutes les tâches** > **Demander un nouveau certificat**.

  5. Dans la page **Demander un certificat**, sélectionnez **Chiffrement CEP**, puis cliquez sur **L'inscription pour obtenir ce certificat nécessite des informations supplémentaires. Cliquez ici pour configurer les paramètres**.

     ![Sélectionner Chiffrement CEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. Dans **Propriétés du certificat**, cliquez sur l'onglet **Objet**, entrez dans le champ **Nom de l’objet** les informations que vous avez recueillies à l'étape 2, cliquez sur **Ajouter**, puis sur **OK**.

  7. Complétez l'inscription de certificats.

  8. Ouvrez le MMC des certificats pour **Mon compte d’utilisateur**.

     Lorsque vous vous inscrivez pour obtenir le certificat Agent d’inscription Exchange (demande hors connexion), vous devez le faire dans le contexte de l'utilisateur. Car l’option **Type d’objet** de ce modèle de certificat est définie sur **Utilisateur**.

  9. Développez **Personnel**, cliquez avec le bouton droit sur **Certificats**, puis sélectionnez **Toutes les tâches** > **Demander un nouveau certificat**.

  10. Dans la page **Demander un certificat**, sélectionnez **Agent d’inscription Exchange (demande hors connexion)** , puis cliquez sur **L'inscription pour obtenir ce certificat nécessite des informations supplémentaires. Cliquez ici pour configurer les paramètres**.

      ![Sélectionner Agent d’inscription Exchange](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. Dans **Propriétés du certificat**, cliquez sur l'onglet **Objet**, entrez dans le champ **Nom de l’objet** les informations que vous avez recueillies à l'étape 2, cliquez sur **Ajouter**.

      ![Propriétés du certificat](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      Sélectionnez l'onglet **Clé privée**, **Permettre l’exportation de la clé privée**, puis cliquez sur **OK**.

      ![Clé privée](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. Complétez l'inscription de certificats.

  13. Exportez le certificat Agent d’inscription Exchange (demande hors connexion) du magasin de certificats de l'utilisateur actuel. Dans l'Assistant Exportation de certificat, sélectionnez **Oui, exportez la clé privée**.

  14. Importez le certificat dans le magasin de certificats de l'ordinateur local.

  15. Dans le MMC des certificats, effectuez l'action suivante pour chacun des nouveaux certificats :

      Cliquez avec le bouton droit sur le certificat, cliquez sur **Toutes les tâches** > **Gérer les clés privées**, ajoutez l’autorisation **Lire** au compte de service NDES.

  16. Exécutez la commande **iisreset** pour redémarrer IIS.

## <a name="next-steps"></a>Étapes suivantes

Si l’appareil atteint avec succès le serveur NDES pour présenter la demande de certificat, l'étape suivante consiste à examiner le [module de stratégie des connecteurs de certificats Intune](troubleshoot-scep-certificate-ndes-policy-module.md).
