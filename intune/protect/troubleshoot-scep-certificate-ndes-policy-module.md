---
title: Résoudre les problèmes du module de stratégie Microsoft Intune Certificate Connector | Microsoft Docs
description: Résoudre les problèmes de fonctionnement du module de stratégie NDES lorsque le module traite une demande de certificat et que vous utilisez des profils de certificat SCEP pour déployer des certificats avec Intune.
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915835"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Résoudre les problèmes du module de stratégie NDES dans Microsoft Intune

Les informations contenues dans cet article peuvent vous aider à valider le fonctionnement du module de stratégie Network Device Enrollment Service (NDES) installé avec Microsoft Intune Certificate Connector. Lorsque NDES reçoit une demande de certificat, il la transmet au module de stratégie, qui valide cette demande pour l'appareil. Après la validation, NDES contacte l'autorité de certification (CA) pour demander le certificat au nom de l'appareil.

Cet article s'applique à la fois à l'étape 3 et à l’étape 4 du [workflow de communication SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="ndes-communication-to-the-policy-module"></a>Communication entre NDES et le module de stratégie

Après avoir reçu la demande de certificat d'un appareil, NDES valide cette demande auprès d’Intune via le module de stratégie installé avec Microsoft Intune Certificate Connector. Ces entrées se réfèrent au *point d'enregistrement de certificat*.

**Entrées du journal indiquant une réussite** :

Pour confirmer l’envoi de la demande de validation au module, recherchez une entrée qui ressemble aux exemples suivants dans les journaux du serveur NDES :

- **Journaux IIS** :

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **Journal NDESPlugin** :

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  L'exemple suivant indique que la demande d’accès des appareils a été validée et que NDES peut désormais contacter l’autorité de certification :

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog** :

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**Lorsque les indicateurs de réussite ne sont pas présents** :

Si vous ne trouvez pas ces entrées, commencez par consulter le guide de dépannage sur la [communication entre l’appareil et le serveur NDES](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors).

Si les informations contenues dans cet article ne vous permettent pas de résoudre le problème, voici des entrées supplémentaires qui peuvent indiquer des problèmes.

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log contient une erreur 12175

Lorsque le journal contient une erreur 12175 similaire à la suivante, le problème peut venir du certificat SSL :

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

Les navigateurs modernes et ceux installés sur des appareils mobiles ignorent le *nom commun* d'un certificat SSL en présence d’*autres noms d’objets*.

**Résolution** :  Délivrer le certificat SSL du serveur web avec les attributs suivants pour *Common Name* (Nom commun) et *Subject Alternative Name* (Autre nom d’objet), puis le lier au port 443 dans IIS :

  - **Nom de l’objet**  
    CN = nom du serveur externe
  - **Autre nom de l’objet**  
     Nom = nom du serveur externe  
     Nom DNS = nom du serveur interne

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log contient une erreur 403 – Interdit : Accès refusé »

Lorsque les journaux suivants contiennent une erreur 403 semblable à celle-ci, le certificat du client n’est peut-être pas approuvé ni valide :

**NDESPlugin.log** :

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**Journal IIS** :

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

Ce problème se produit s'il existe des certificats CA intermédiaires dans le magasin de certificats des autorités de certification racine de confiance du serveur NDES.

Si un certificat affiche les mêmes valeurs *Issued to* (Émis à) et *Issued by* (Émis par), il s'agit d'un certificat racine. Sinon, il s'agit d'un certificat intermédiaire.

**Résolution** : Pour résoudre le problème, identifiez et supprimez les certificats intermédiaires de l'autorité de certification du magasin de certificats Autorités de certification racines de confiance.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log indique que la demande d’accès renvoie une valeur false

Lorsque le résultat de la demande d’accès renvoie une valeur **false**, vérifiez que le fichier *CertificateRegistrationPoint.svclog* ne contient pas d'erreurs. Par exemple, il peut contenir une erreur « Impossible de récupérer le certificat de signature » semblable à l'entrée suivante :

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**Résolution** : Sur le serveur où le connecteur est installé, ouvrez l'Éditeur du Registre, localisez la clé de registre `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector`, puis vérifiez si la valeur SigningCertificate existe.

Si cette valeur n'existe pas, redémarrez le service Intune Connector dans services.msc, puis vérifiez si la valeur apparaît dans le registre. Si la valeur est toujours manquante, il s’agit souvent de problèmes de connectivité réseau entre le serveur qui exécute NDES et le service Intune.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES transmet la demande d’émission du certificat

Après une validation réussie par le point d'enregistrement de certificat (module de stratégie), NDES transmet la demande de certificat à l’autorité de certification au nom de l'appareil.

**Entrées du journal indiquant une réussite** :

- **Journal NDESPlugin** :

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **Journaux IIS** :

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog** :

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**Lorsque les indicateurs de réussite ne sont pas présents** :

Si vous ne voyez pas les entrées indiquant la réussite, procédez comme suit :

1. Recherchez les problèmes consignés dans le fichier *CertificateRegistrationPoint.svclog* lorsque le point d'enregistrement de certificat vérifie la demande d’accès. Recherchez les entrées entre les lignes suivantes :

   - VerifyRequest Started.
   - VerifyRequest Finished with status False

2. Ouvrez le MMC Autorité de certification sur l’autorité de certification, et sélectionnez les **demandes ayant échoué** pour rechercher les erreurs facilitant l’identification d’un problème. L’image suivante est un exemple :

   ![Exemple de requête ayant échoué](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. Vérifiez que le journal des événements de l'application sur l’autorité de certification ne contient pas d'erreurs. En général, vous pouvez afficher les erreurs qui correspondent à ce que vous voyez dans les **demandes ayant échoué** de l'étape précédente. L’image suivante est un exemple :

   ![Passer en revue le journal des applications](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>Étapes suivantes

Si le module de stratégie NDES valide la demande et que celle-ci est transmise à l'autorité de certification, l'étape suivante consiste à examiner la [remise du certificat à l'appareil](troubleshoot-scep-certificate-delivery.md).
