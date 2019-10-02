---
title: Résoudre les problèmes de Microsoft Intune Certificate Connector et des ID d’événement | Microsoft Docs
description: Corrigez les problèmes de Microsoft Intune Certificate Connector en examinant les ID et les descriptions d’événement, et passez en revue les codes de diagnostic du service de connecteur Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 682d51269798dff181a3bd8384268da862118a70
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721758"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Événements et codes de diagnostic d’Intune Certificate Connector

À compter de la version 6.1806.x.x, le service du connecteur Intune journalise les événements dans **l’observateur d’événements**  (**Journaux des applications et des services** > **Connecteur Microsoft Intune**). Utilisez ces événements pour résoudre les problèmes potentiels dans la configuration du connecteur Intune. Ces événements journalisent les réussites et les échecs d’une opération. Ils contiennent également des codes de diagnostic avec des messages pour aider l’administrateur informatique à résoudre le problème.

> [!TIP]  
> Pour résoudre les problèmes et vérifier la configuration du connecteur Intune, consultez [Exemples de scripts d’autorité de certification](https://aka.ms/intuneconnectorverificationscript).

## <a name="event-ids-and-descriptions"></a>ID d’événement et descriptions

| ID de l'événement      | Nom de l’événement    | Description de l’événement | Codes de diagnostic associés |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Service du connecteur démarré | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Service du connecteur arrêté | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Certificat d’inscription du connecteur correctement renouvelé | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Échec du renouvellement du certificat d’inscription du connecteur. Réinstallez le connecteur. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Impossible de récupérer le certificat d’inscription du connecteur à partir du Registre. Consultez les détails de l’événement pour connaître l’empreinte numérique de certificat liée à cet événement. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Vérifiez les informations de diagnostic dans les détails de l’événement. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | Certificat PKCS correctement émis. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification, le nom du modèle de certificat et l’empreinte numérique de certificat associés à cet événement. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Échec de l’émission d’un certificat PKCS. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification, le nom du modèle de certificat et l’empreinte numérique de certificat associés à cet événement. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Certificat correctement révoqué. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification et le numéro de série du certificat associés à cet événement. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Échec de la révocation du certificat. Consultez les détails de l’événement pour connaître l’ID d’appareil, l’ID d’utilisateur, le nom de l’autorité de certification et le numéro de série du certificat associés à cet événement. Pour plus d’informations, consultez les journaux SVC NDES.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Données de demande ou de révocation du certificat correctement chargées. Consultez les détails de l’événement pour connaître les informations relatives au chargement. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Échec du chargement des données de demande ou de révocation du certificat. Consultez les détails de l’événement > État de chargement pour déterminer le point de défaillance.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Demande de signature d’un certificat, de téléchargement d’un certificat client ou de révocation d’un certificat correctement téléchargée. Consultez les détails de l’événement pour connaître les informations relatives au téléchargement.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Échec du téléchargement de la demande de signature d’un certificat, de téléchargement d’un certificat client ou de révocation d’un certificat. Consultez les détails de l’événement pour connaître les informations relatives au téléchargement. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Demande d’accès client correctement vérifiée par le point d’enregistrement de certificat | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Demande exécutée mais rejetée par le point d’enregistrement de certificat. Pour plus d’informations, consultez le code de diagnostic et le message. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Échec de la vérification d’une demande d’accès client par le point d’enregistrement de certificat. Pour plus d’informations, consultez le code de diagnostic et le message. Consultez les détails du message d’événement pour connaître l’ID d’appareil correspondant à la demande. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | Le point d’enregistrement de certificat a correctement terminé le processus de notification et a envoyé le certificat à l’appareil client. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | Le point d’enregistrement de certificat n’a pas pu terminer le processus de notification. Consultez les détails du message d’événement pour obtenir des informations sur la demande. Vérifiez la connexion entre le serveur NDES et l’autorité de certification. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Codes de diagnostic

| Code de diagnostic | Nom du diagnostic | Message de diagnostic |
| -------------   | -------------   | -------------      |
| 0x00000000 | Opération réussie  | Opération réussie |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | L’autorité de certification n’est pas valide ou est inaccessible. Vérifiez que l’autorité de certification est disponible et que votre serveur peut communiquer avec elle. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Le certificat d’authentification client Symantec est introuvable dans le magasin de certificats local. Pour plus d’informations, consultez [Installer le certificat d’autorisation d’inscription Symantec](certificates-digicert-configure.md#install-the-digicert-ra-certificate).  |
| 0x00000402 | RevokeCert_AccessDenied  | Le compte spécifié ne dispose pas d’autorisations pour révoquer un certificat d’une autorité de certification. Pour déterminer l’autorité de certification émettrice, consultez le champ Nom de l’autorité de certification dans les détails du message d’événement.  |
| 0x00000403 | CertThumbprint_NotFound  | Impossible de trouver un certificat correspondant à votre entrée. Inscrivez le connecteur de certificat, puis réessayez. |
| 0x00000404 | Certificate_NotFound  | Impossible de trouver un certificat correspondant à l’entrée fournie. Réinscrivez le connecteur de certificat, puis réessayez. |
| 0x00000405 | Certificate_Expired  | Un certificat a expiré. Réinscrivez le connecteur de certificat pour renouveler le certificat, puis réessayez. |
| 0x00000408 | CRPSCEPCert_NotFound  | Certificat de chiffrement NDES introuvable. Vérifiez que le connecteur NDES et Intune sont configurés correctement. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Impossible de récupérer le certificat de signature. Vérifiez que le service du connecteur Intune est configuré correctement et qu’il est en cours d’exécution. Vérifiez également que les événements de téléchargement de certificat ont réussi. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Échec de la désérialisation de la demande de challenge SCEP. Vérifiez que le connecteur NDES et Intune sont configurés correctement. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Demande refusée en raison de l’expiration de la demande d’accès au certificat. L’appareil client peut réessayer après avoir obtenu une nouvelle demande d’accès à partir du serveur d’administration. |
| 0x0FFFFFFFF | Unknown_Error  | Nous ne pouvons pas traiter votre demande, car une erreur côté serveur s’est produite. Recommencez. |


## <a name="next-steps"></a>Étapes suivantes
Pour obtenir une aide supplémentaire, utilisez le guide [Dépannage du déploiement de profil de certificat SCEP dans Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune).
