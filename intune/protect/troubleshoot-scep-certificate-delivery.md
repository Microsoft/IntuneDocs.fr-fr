---
title: Résoudre les problèmes de remise de certificats aux appareils lorsque vous utilisez SCEP avec Microsoft Intune | Microsoft Docs
description: Résolvez les problèmes de remise d'un certificat à un appareil par l’autorité de certification lors de l'utilisation des profils de certificats SCEP avec Intune pour déployer des certificats.
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
ms.openlocfilehash: 77be59d126dc7e73bee468ca938938c6bb1b2e1a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915874"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Résoudre les problèmes de remise de certificats fournis par SCEP aux appareils dans Microsoft Intune

Utilisez les informations contenues dans cet article pour vous aider à examiner la remise de certificats aux appareils lorsque vous utilisez le protocole SCEP (Simple Certificate Enrollment Protocol) afin de fournir des certificats dans Intune. Lorsque le serveur Network Device Enrollment Service (NDES) reçoit le certificat demandé pour un appareil de la part de l'autorité de certification (CA), il le renvoie à l'appareil.

Cet article s'applique à l'étape 5 du [workflow de communication SCEP](troubleshoot-scep-certificate-profiles.md) ; remise du certificat à l'appareil qui a soumis la demande de certificat.

## <a name="review-the-certification-authority"></a>Examiner l'autorité de certification

Lorsque l’autorité de certification remet le certificat, vous verrez une inscription similaire à l'exemple suivant sur l’autorité de certification :

![Exemples de certificats émis](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>Examiner l’appareil

### <a name="android"></a>Android

Pour les appareils inscrits par l'administrateur des appareils, vous verrez une notification similaire à l'image suivante, vous invitant à installer le certificat :

![Notification Android](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

Pour Android Enterprise ou Samsung Knox, l'installation du certificat est automatique et silencieuse.

Pour visualiser un certificat installé sur Android, utilisez une application tierce de visualisation de certificats.

Vous pouvez également consulter le [journal OMADM des appareils](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Recherchez les entrées qui ressemblent aux suivantes, consignées lors de l'installation des certificats :

**Certificat racine** :

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**Certificat fourni via SCEP**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="ios-and-ipados"></a>iOS et iPadOS

Sur l'appareil iOS ou iPadOS, vous pouvez consulter le certificat sous le profil de gestion des appareils. Vous pouvez également explorer les détails des certificats installés.

![Certificat iOS](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

Vous trouverez aussi des entrées similaires à ce qui suit dans le [journal de débogage iOS](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices) :

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

Sur l'appareil Windows, vérifiez que le certificat a été remis :

- Exécutez **eventvwr.msc** pour ouvrir l’Observateur d’événements. Accédez à **Journaux des applications et services** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**, puis recherchez **Event 39**. Cet événement doit avoir une description générale de type : **SCEP : Certificat correctement installé.**

   ![Event 39 dans le journal des applications Windows](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

Pour visualiser le certificat sur l'appareil, lancez **certmgr.msc** pour ouvrir le composant MMC Certificats, puis vérifiez si les certificats racine et SCEP sont correctement installés sur l'appareil dans le magasin personnel :

   1. Accédez à **Certificats (ordinateur local)**  > **Autorités de certification racines de confiance** > **Certificats**, et vérifiez que le certificat racine de votre autorité de certification est présent. Les valeurs de *Issued To* (Délivré à) et *Issued By* (Délivré par) seront les mêmes.
   2. Dans le composant MMC Certificats, accédez à **Certificats - Utilisateur actuel** > **Personnel** > **Certificats**, et vérifiez que le certificat demandé est présent et que le nom de l’autorité de certification apparaît dans le champ *Issued By* (Délivré par).

## <a name="troubleshoot-failures"></a>Résoudre les défaillances

### <a name="android"></a>Android

Pour résoudre les problèmes de cette étape, examinez les erreurs consignées dans le journal OMA DM.

### <a name="ios-and-ipados"></a>iOS et iPadOS

Pour résoudre les problèmes de cette étape, examinez les erreurs consignées dans le journal de débogage des appareils.

### <a name="windows"></a>Windows

Pour résoudre les problèmes liés au fait que le certificat n'est pas installé sur l'appareil, recherchez dans le journal des événements Windows les erreurs qui indiquent des problèmes :

- Sur l’appareil, exécutez **eventvwr.msc** pour ouvrir l’Observateur d'événements, puis accédez à **Journaux des applications et services** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**.

Les erreurs de remise et d'installation du certificat sur l'appareil sont généralement liées à des opérations Windows, et non à Intune.

## <a name="next-steps"></a>Étapes suivantes

Lorsque le certificat se déploie avec succès sur l'appareil, mais qu’Intune n’indique pas que cette opération a réussi, consultez [Création de rapports NDES destinés à Intune](troubleshoot-scep-certificate-reporting.md) pour résoudre ce problème de création de rapports.
