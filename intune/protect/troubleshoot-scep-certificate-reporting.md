---
title: Résoudre les problèmes de création de rapports sur le déploiement réussi du certificat aux appareils lorsque vous utilisez SCEP avec Microsoft Intune | Microsoft Docs
description: Résoudre les problèmes de création de rapports par NDES et le connecteur signalent à Intune sur le déploiement réussi des certificats qui ont été fournis avec les profils de certificat SCEP.
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916017"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Résoudre les problèmes de création de rapports par NDES sur les déploiements de certificats dans Microsoft Intune

Utilisez les informations suivantes pour confirmer que NDES et Microsoft Intune Certificate Connector envoient avec succès des rapports à Intune confirmant que le certificat a été remis à un appareil. La création de rapports destinés à Intune est la dernière phase de l'utilisation des profils de certificat SCEP pour fournir un certificat aux appareils Windows.

Cet article s'applique à l'étape 6 du [workflow de communication SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="review-for-signs-of-successful-reporting"></a>Identifiant des signes confirmant la création de rapports

Si la création de rapports a réussi, vous trouverez des entrées qui ressemblent aux exemples suivants sur le serveur NDES :

- **Journal IIS** :

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log** :

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog** :

  ![Journal du connecteur de certificat Intune](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog** :

  ![Journal du connecteur de certificat Intune](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus** :

  Accédez au dossier *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus* où figurent les sous-dossiers **Failed** (Échec), **Processing** (Traitement en cours) et **Succeed** (Réussite) contenant des fichiers d’état de demande de certificat.

  Si la demande de certificat a été traitée avec succès, de nouveaux fichiers apparaissent dans le dossier **Succeed** (Réussite). Vous pouvez utiliser *Notepad.exe* pour ouvrir les fichiers et visualiser les données chargées vers le service Intune par le connecteur de certificat Intune. Les données chargées incluent des détails comme **CertificateSerialNumber**, **UserID**, **DeviceID** et **Thumbprint**.

### <a name="troubleshoot-stuck-files"></a>Dépanner les fichiers bloqués

Si vous ne voyez aucun nouveau fichier créé dans le dossier *Succeed* (Réussite), vérifiez la présence de fichiers bloqués dans le dossier *Processing* (Traitement en cours).

Vérifiez que le service Intune Connector est lancé sur le serveur NDES, et qu'il n'y a pas d'erreurs dans le fichier Ndesconnector.svclog.

## <a name="next-steps"></a>Étapes suivantes

[Comment obtenir un support technique pour Microsoft Intune](../fundamentals/get-support.md)
