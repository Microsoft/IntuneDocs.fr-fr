---
title: Résoudre les problèmes de mise à jour logicielle dans Microsoft Intune - Azure | Microsoft Docs
description: Résoudre les problèmes de mise à jour logicielle dans Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 1354c789a6756a6ddf2d9c5d6400ece91c80d57c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188620"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Résoudre les problèmes de mise à jour logicielle dans Microsoft Intune

Aidez à résoudre les problèmes de mise à jour logicielle dans Microsoft Intune.

Si ces informations ne vous aident pas, vous pouvez également [bénéficier d’un support technique pour Microsoft Intune](get-support.md).

## <a name="update-agent-error-codes"></a>Mettre à jour les codes d’erreur de l’agent

Le tableau suivant répertorie les codes d’erreur de l’**agent de mise à jour** d’Intune. Si vous ne trouvez pas un code d'erreur spécifique dans ce tableau, consultez la [liste des codes d’erreur Windows Update](https://support.microsoft.com/help/938205/windows-update-error-code-list).

|Code d'erreur|Nom symbolique|Plus d’informations|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|L'agent a été arrêté.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|L'opération a réussi, mais des erreurs se sont produites lors de l'application des mises à jour.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|Un rappel a été marqué pour être déconnecté ultérieurement car la demande de déconnexion de l'opération s'est produite pendant l'exécution d'un rappel.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|Le système doit être redémarré pour terminer l'installation de la mise à jour.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|La mise à jour à installer est déjà installée sur le système.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|La mise à jour à supprimer n'est pas installée sur le système.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|L'installation de la mise à jour est en cours.|
|**0x80cf0001**|OM_E_NO_SERVICE|L'agent n'a pas pu fournir le service.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|La capacité maximale du service a été dépassée.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|ID introuvable.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|L'objet n'a pas pu être initialisé.|
|**0x80cf0007**|OM_E_INVALIDINDEX|L'index d'une collecte n'est pas valide.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|Clé pour l'élément demandé introuvable.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|Une opération en conflit était en cours. Certaines opérations, telles que les installations multiples, ne peuvent pas être effectuées simultanément.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|L'opération a été annulée.|
|**0x80cf000C**|OM_E_NOOP|Aucune opération n'était requise.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|L'agent n'a pas pu trouver les informations requises dans les données XML de la mise à jour.|
|**0x80cf000E**|OM_E_XML_INVALID|L'agent a trouvé des informations dans les données XML de la mise à jour qui ne sont pas valides.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|Des relations de mise à jour circulaire ont été détectées dans les métadonnées.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|Les relations de mise à jour étaient trop profondément imbriquées pour être évaluées.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|Une relation de mise à jour a été trouvée qui n'est pas valide.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|Une valeur de Registre a été lue qui n'est pas valide.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|L'opération a tenté d'ajouter un élément en double à une liste.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|L'appelant ne peut pas installer les mises à jour qui ont été demandées pour l'installation.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|L'opération a tenté d'installer alors qu'une autre installation était en cours, ou le système était en attente d'un redémarrage obligatoire.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|L'opération n'a pas été effectuée car il n'y a aucune mise à jour applicable.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|L'opération a échoué car un jeton d'utilisateur requis est manquant.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|Une mise à jour exclusive ne peut pas être installée simultanément avec les autres mises à jour.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|Une valeur de stratégie n'a pas été définie.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|Une mise à jour contient des métadonnées qui ne sont pas valides.|
|**0x80cf001E**|OM_E_SERVICE_STOP|L'opération n'a pas pu aboutir car le service ou le système a été arrêté.|
|**0x80cf001F**|OM_E_NO_CONNECTION|L'opération n'a pas pu aboutir car la connexion réseau n'était pas disponible.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|L'opération n'a pas pu aboutir car il n'y a aucun utilisateur interactif connecté.|
|**0x80cf0021**|OM_E_TIME_OUT|L'opération n'a pas pu aboutir car elle a expiré.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|L'opération a échoué pour toutes les mises à jour.|
|**0x80cf0024**|OM_E_NO_UPDATE|Il n'y a aucune mise à jour.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|Les paramètres de stratégie de groupe ont empêché l'accès à Windows Update.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|Le type de mise à jour n'est pas valide.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|La mise à jour n'a pas pu être désinstallée car la demande ne provenait pas d'un serveur WSUS.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|La recherche peut avoir manqué certaines mises à jour, ou il peut y avoir une application sans licence sur le système.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|Une mise à jour compressée par delta n'a pas pu être installée car elle nécessitait la source.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|Une mise à jour de fichier complet n'a pas pu être installée car elle nécessitait la source.|
|**0x80cf002E**|OM_E_WU_DISABLED|L'accès à un serveur non géré n'est pas autorisé.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|L’opération n’a pas abouti car la stratégie **DisableWindowsUpdateAccess** a été définie.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|Le format de liste de proxy n'est pas valide.|
|**0x80cf0031**|OM_E_INVALID_FILE|Le fichier est dans un format incorrect.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|La chaîne de critères de recherche n'est pas valide.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|Impossible de télécharger la mise à jour.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|La mise à jour n'a pas été traitée.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|L'état actuel de l'objet ne permettait pas l'opération.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|L'opération n'est pas prise en charge.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|Le fichier téléchargé possède un type de contenu inattendu.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|Le serveur a demandé à l'agent de se resynchroniser trop souvent.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|Il n'existe aucune prise en charge pour l'IU de WUA.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|Seuls les administrateurs peuvent effectuer cette opération sur les mises à jour par ordinateur.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|Une recherche a été tentée avec une étendue non prise en charge.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|L'URL n'indique pas de fichier.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|L'opération demandée n'est pas prise en charge.|
|**0x80cf0049**|OM_E_OUTOFRANGE|Les données sont hors limites.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|Les données contiennent une version qui n'est pas valide.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|L'appel de recherche a été effectué, mais n'a pas pu détecter certaines des mises à jour.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|L'appel de téléchargement a été effectué, mais n'a pas pu télécharger certaines des mises à jour.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|L'appel d'installation a été effectué, mais n'a pas pu installer certaines des mises à jour.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|Le cache de Windows Update est vide car il n'a pas été initialisé.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|Le serveur ne prend pas en charge les recherches spécifiques à une catégorie. La recherche dans le catalogue complet doit être émise à la place.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|Un problème d'autorisation avec le service s'est produit.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|Il n'existe aucune connectivité réseau ou d'itinéraire pour le point de terminaison.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|Les données reçues ne respectent pas les attentes en matière de contrat de données.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|L'URL n'est pas valide.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|Impossible de charger l'exécution NWS.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|Le schéma d'authentification de proxy n'est pas pris en charge.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|La propriété de service demandée n'est pas disponible.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|Le plug-in du fournisseur de point de terminaison requiert une actualisation en ligne.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|Une URL pour le point de terminaison de service demandé n'est pas disponible.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|La connexion au point de terminaison de service s'est terminée.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|L'opération n'est pas valide car l'émetteur de protocole se trouve dans un état inapproprié.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|Une opération a échoué à cause de raisons qui ne sont pas expliquées par un autre code d'erreur.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|La recherche peut avoir manqué certaines mises à jour car Windows Installer est une version antérieure à la version 3.1.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|La recherche peut avoir manqué certaines mises à jour car Windows Installer n'est pas configuré.|
|**0x80cf1003**|OM_E_MSP_DISABLED|La recherche peut avoir manqué certaines mises à jour car la stratégie a désactivé l'application de correctifs de Windows Installer.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|Une mise à jour n'a pas pu être appliquée car l'application est installée par utilisateur.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|Une demande d'un gestionnaire de mise à jour à distance n'a pas pu aboutir car aucun processus distant n'est disponible.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|Une demande d'un gestionnaire de mise à jour à distance a échoué car le gestionnaire est uniquement local.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|Un gestionnaire de mise à jour à distance n'a pas pu être créé car il en existe déjà un.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|Une demande du gestionnaire pour installer (désinstaller) une mise à jour n'a pas pu être terminée car la mise à jour ne prend pas en charge l'installation (désinstallation).|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|Une opération n'a pas pu aboutir car le gestionnaire incorrect a été spécifié.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|Une opération de gestionnaire n'a pas pu aboutir car la mise à jour contient des métadonnées qui ne sont pas valides.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|Une opération n'a pas pu aboutir car le programme d'installation a dépassé la limite de temps. Vérifiez si une mise à jour nécessitant une interaction utilisateur a été approuvée pour le déploiement. Dans ce cas, vous devez modifier les paramètres d'installation de mise à jour pour qu'elle puisse s'installer en silence.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|Une opération qui a été effectuée par le gestionnaire de mise à jour a été annulée.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|Une opération n'a pas pu aboutir car les métadonnées spécifiques au gestionnaire ne sont pas valides.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|Le programme d'installation n'a pas pu installer (désinstaller) une ou plusieurs mises à jour.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|Le gestionnaire de mise à jour n'a pas installé la mise à jour car elle doit être téléchargée de nouveau.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|Le gestionnaire de mise à jour n'a pas pu envoyer une notification de l'état de l'opération d'installation (désinstallation).|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|L'opération de post-redémarrage pour la mise à jour est toujours en cours.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|Le résultat de l'opération de post-redémarrage pour la mise à jour n'a pas pu être déterminé.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|L'état de la mise à jour après l'exécution de son opération de post-redémarrage est inattendu.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|La pile de traitements du système d'exploitation doit être mise à jour avant que cette mise à jour soit téléchargée ou installée.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|Un programme d'installation de rappel a rappelé avec une erreur.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|La signature du programme d'installation personnalisé ne correspondait pas à la signature requise par la mise à jour.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|Le programme d'installation ne prend pas en charge la configuration d'installation.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|La session ciblée pour l'installation n'est pas valide.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|Une erreur du gestionnaire de mise à jour n’est pas couverte par un autre code OM_E_UH_&#42;.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|Impossible d'afficher l'IU en mode non IU. Les modules de l'IU cliente Windows Update ne peuvent pas être installés.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|Cette version des fonctions exportées de l'IU cliente de WU n'est pas prise en charge.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|Une erreur d’interface utilisateur qui n’est pas couverte par un autre code d’erreur OM_E_AUCLIENT_&#42; s’est produite.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|Identique à **SOAPCLIENT_SOAPFAULT**. Le client SOAP a échoué car une erreur SOAP de type de code d’erreur **OM_E_PT_SOAP_&#42;** s’est produite.|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|Identique à **SOAPCLIENT_PARSEFAULT_ERROR**.  Le client SOAP n'a pas pu analyser une erreur de défaillance SOAP.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|Identique à **SOAPCLIENT_PARSE_ERROR**.  Le client SOAP n'a pas pu analyser la réponse du serveur.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|Identique à **SOAP_E_VERSION_MISMATCH**. Le client SOAP a trouvé un espace de noms non reconnaissable pour l'enveloppe SOAP.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|Identique à **SOAP_E_MUST_UNDERSTAND**. Le client SOAP n'a pas pu interpréter un en-tête.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|Identique à **SOAP_E_CLIENT**. Le client SOAP a déterminé que le message était incorrect. Corrigez avant de le renvoyer.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|Identique à **SOAP_E_SERVER**. Le message SOAP n'a pas pu être traité en raison d'une erreur de serveur. Renvoyez ultérieurement.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|Le nombre d'allers-retours au serveur a dépassé la limite maximale.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|L'initialisation a échoué car l'objet était déjà initialisé.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|Le nom d'ordinateur n'a pas pu être déterminé.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|La réponse du serveur indique que le serveur a été modifié ou que le cookie n'était pas valide. Actualisez le cache interne et réessayez.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|Identique à **État HTTP 400**. Le serveur n'a pas pu traiter la demande car la syntaxe n'est pas valide.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|Identique à **État HTTP 401**. La ressource demandée nécessite l'authentification des utilisateurs.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|Identique à **État HTTP 403**. Le serveur a compris la demande, mais a refusé de la réaliser.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|Identique à **État HTTP 404**. Le serveur ne peut pas trouver l'URI (Uniform Resource Identifier) demandé.|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|Identique à **État HTTP 405**. La méthode HTTP n'est pas autorisée.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|Identique à **État HTTP 407**. L'authentification proxy est requise.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|Identique à **État HTTP 408**. Le serveur a expiré lorsqu'il attendait la demande.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|Identique à **État HTTP 409**. La demande a échoué en raison d'un conflit avec l'état actuel de la ressource.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|Identique à **État HTTP 410**. La ressource demandée n'est plus disponible sur le serveur.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|Identique à **État HTTP 500**. Une erreur interne au serveur a empêché la réalisation de la demande.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|Identique à **État HTTP 500**. Le serveur ne prend pas en charge la fonctionnalité requise pour répondre à la demande.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|Identique à **État HTTP 502**. Le serveur, en tant que passerelle ou proxy, a reçu une réponse non valide du serveur en amont auquel il a accédé lorsqu'il a tenté de répondre à la demande.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|Identique à **État HTTP 503**. Le service est temporairement surchargé.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|Identique à **État HTTP 503**. La demande a expiré lorsqu'elle attendait une passerelle.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|Identique à **État HTTP 505**. Le serveur ne prend pas en charge la version du protocole HTTP utilisée pour la demande.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|L'opération a échoué en raison d'un emplacement de fichier modifié. Actualisez l'état interne et renvoyez.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|Le serveur a renvoyé une liste d'informations d'authentification vide.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|L'agent n'a pas pu créer tous les cookies d'authentification valides.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|Une valeur de propriété de configuration était erronée.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|Une valeur de propriété de configuration était manquante.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|La demande HTTP n’a pas pu être effectuée et la raison ne correspondait à aucun des codes d’erreur **OM_E_PT_HTTP_&#42;**.|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|Identique à **ERROR_WINHTTP_NAME_NOT_RESOLVED**. Le nom du serveur proxy ou du serveur de destination ne peut pas être résolu.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|Le traitement des fichiers .cab externes s'est terminé avec des erreurs.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|L'initialisation du processeur .cab externe ne s'est pas terminée.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|Le format d'un fichier de métadonnées n'est pas valide.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|Le processeur cab externe a trouvé des métadonnées qui ne sont pas valides.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|Le fichier condensé n'a pas pu être extrait à partir d'un fichier .cab externe.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|Impossible de décompresser un fichier .cab externe.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|Le processeur cab externe n'a pas pu obtenir les emplacements de fichiers.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|Une erreur de communication s’est produite et n’est pas couverte par un autre code d’erreur **OM_E_PT_&#42;**.|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|Une opération du gestionnaire de téléchargement n'a pas pu aboutir car le fichier demandé n'a pas d'URL.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|Une opération du gestionnaire de téléchargement n'a pas pu aboutir car le fichier condensé n'était pas reconnu.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|Une opération du gestionnaire de téléchargement n'a pas pu aboutir car les métadonnées du fichier demandaient un algorithme de hachage non reconnu.|
|**0x80cf6005**|OM_E_DM_NONETWORK|Une opération du gestionnaire de téléchargement n'a pas pu aboutir car la connexion réseau n'était pas disponible.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|La mise à jour n'a pas été téléchargée.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|Une opération du gestionnaire de téléchargement a échoué car le gestionnaire de téléchargement n'a pas pu se connecter au Service de transfert intelligent en arrière-plan (BITS).|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|Une opération du gestionnaire de téléchargement a échoué car une erreur de transfert du Service de transfert intelligent en arrière-plan (BITS) non spécifiée s'est produite.|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|Un téléchargement doit être redémarré car l'emplacement source de téléchargement a été modifié.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|Un téléchargement doit être redémarré car le contenu de la mise à jour a changé dans une nouvelle révision.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|Une erreur du gestionnaire de téléchargement s’est produite et n’est pas couverte par un autre code d’erreur **OM_E_DM_&#42;**.|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|Une charge utile de l'événement a été spécifiée et n'est pas valide.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|La taille de la charge utile de l'événement soumise n'est pas valide.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|Le service n'est pas enregistré.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|Une opération a échoué car l'agent s'arrête.|
|**0x80cf8001**|OM_E_DS_INUSE|Une opération a échoué car le magasin de données était en cours d'utilisation.|
|**0x80cf8002**|OM_E_DS_INVALID|Les états actuels et prévus du magasin de données ne correspondent pas.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|Il manque un tableau dans le magasin de données.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|Le magasin de données contient un tableau qui comporte des colonnes inattendues.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|Un tableau n'a pas pu être ouvert car il ne se trouve pas dans le magasin de données.|
|**0x80cf8006**|OM_E_DS_BADVERSION|Les versions actuelles et prévues du magasin de données ne correspondent pas.|
|**0x80cf8007**|OM_E_DS_NODATA|Les informations demandées ne se trouvent pas dans le magasin de données.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|Il manque des informations requises dans le magasin de données ou le magasin de données a une valeur null dans une colonne de tableau qui requiert une valeur non null.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|Il manque des informations requises dans le magasin de données ou le magasin de données possède une référence à des conditions de contrat de licence, un fichier, une propriété localisée ou une ligne liée manquants.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|La mise à jour n'a pas été traitée car son gestionnaire de mise à jour n'a pas été reconnu.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|La mise à jour n'a pas été supprimée car elle est toujours référencée par un ou plusieurs services.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|La section du magasin de données n'a pas pu être verrouillée dans le temps imparti.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|La ligne n'a pas été ajoutée car une ligne existante a la même clé primaire.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|Le magasin de données n'a pas pu être initialisé car il a été verrouillé par un autre processus.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|Le magasin de données n'est pas autorisé à être enregistré avec COM dans le processus en cours.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|Une opération n'a pas pu créer un objet de magasin de données dans un autre processus.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|Le serveur a envoyé la même mise à jour au client avec deux ID de révision différents.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|Une opération n'a pas pu aboutir car le service n'est pas dans le magasin de données.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|Une opération n'a pas pu aboutir car l'inscription du service a expiré.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|Une demande pour masquer une mise à jour a été refusée car il s'agit d'une mise à jour obligatoire ou car elle a été déployée avec une échéance.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|Un tableau n'a pas été fermé car il n'est pas associé à la session.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|Un tableau n'a pas été fermé car il n'est pas associé à la session.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|La demande pour supprimer le service ou annuler son inscription a été refusée car il s'agit d'un service intégré ou car le service Mises à jour automatiques ne peut pas revenir à un autre service.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|La demande a été refusée car l'opération n'est pas autorisée.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|Le schéma du magasin de données actuel et le schéma d'un tableau dans un document XML de sauvegarde ne correspondent pas.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|Le magasin de données requiert une réinitialisation de session. Libérez la session et réessayez avec une nouvelle session.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|Une opération du magasin de données n'a pas pu aboutir car elle a été demandée avec une identité usurpée.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|Une erreur du magasin de données s’est produite et n’est pas couverte par un autre code **OM_E_DS_&#42;**.|
|**0x80cfA000**|OM_E_AU_NOSERVICE|Le service Mises à jour automatiques n'a pas pu entretenir les demandes entrantes.|
|**0x80cfA004**|OM_E_AU_PAUSED|Le service Mises à jour automatiques n'a pas pu traiter les demandes entrantes car il était suspendu.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|Aucun service non géré n'est inscrit avec le service Mises à jour automatiques.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|Le service par défaut enregistré avec le service Mises à jour automatiques a été modifié lors de la recherche.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|Le service Mises à jour automatiques invite déjà l'utilisateur à un redémarrage.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|Une erreur du service Mises à jour automatiques s’est produite et n’est pas couverte par un autre code **OM_E_AU &#42;**.|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|Une opération de l'évaluateur d'expression n'a pas pu aboutir car une expression n'a pas été reconnue.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|Une opération de l'évaluateur d'expression n'a pas pu aboutir car une expression n'était pas valide.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|Une opération de l'évaluateur d'expression n'a pas pu aboutir car une expression contient un nombre incorrect de nœuds de métadonnées.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|Une opération de l'évaluateur d'expression n'a pas pu aboutir car la version des données d'expression sérialisées n'est pas valide.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|L'évaluateur d'expression n'a pas pu être initialisé.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|Une opération de l'évaluateur d'expression n'a pas pu aboutir car un attribut n'est pas valide.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|Une opération de l'évaluateur d'expression n'a pas pu aboutir car l'état de cluster de l'ordinateur n'a pas pu être déterminé.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|Une erreur de l’évaluateur d’expression s’est produite et n’est pas couverte par un autre code d’erreur **OM_E_EE_&#42;**.|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|Le fichier de cache des événements était défectueux.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|Le XML dans le descripteur d'espace de noms d'événement n'a pas pu être analysé.|
|**0x80cfF003**|OM_E_INVALID_EVENT|Le XML dans le descripteur d'espace de noms d'événement n'est pas valide.|
|**0x80cfF004**|OM_E_SERVER_BUSY|Le serveur a rejeté un événement car le serveur était trop occupé.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|Une erreur d'informateur non couverte par un autre code d'erreur s'est produite.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|L'installation a échoué car un redémarrage obligatoire est en attente.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|Le téléchargement a été annulé.|

## <a name="windows-7-based-computers-with-lots-of-superseded-updates-stop-reporting-to-the-microsoft-intune-console"></a>Les ordinateurs Windows 7 avec un grand nombre de mises à jour remplacées cessent de communiquer avec la console Microsoft Intune
**Problème** : vous pouvez être confronté à la situation où les clients Microsoft Intune rencontrent un ou plusieurs des problèmes suivants :
- Ils cessent soudain de créer des rapports auprès de la console d’administration Microsoft.  
- Ils subissent une utilisation élevée du processeur.
- L’installation des applications via le portail Intune est lente.
- Microsoft Intune Center déclenche l’erreur suivante : *Une erreur s’est produite lors de la mise à jour de votre ordinateur. Erreur détectée : Code 0x800705b4*.
- Le champ d’état dans la Console d’administration Intune > Groupes > Tous les appareils affiche ceci : *Un ou plusieurs agents installés sur cet ordinateur signalent des erreurs. Les informations de cet ordinateur sont peut-être incorrectes ou obsolètes*.

Ce problème peut se produire si des mises à jour remplacées (des mises à jour qui ont été remplacées par une autre mise à jour) n’ont pas été suspendues pendant une période prolongée. Au cours de certains processus, tels que l’installation d’une application, Windows vérifie toutes les mises à jour remplacées dans l’ordre afin que les mises à jour et celles qui leur succèdent puissent être correctement mappées. Si la liste des mises à jour remplacées devient trop importante, cette tâche de vérification peut entraîner une utilisation élevée du processeur en raison de la charge de traitement et du temps requis. Ce problème affecte principalement les clients qui exécutent Windows 7 en raison du grand nombre de mises à jour remplacées qui sont disponibles pour Windows 7. Windows 8 et les systèmes d’exploitation ultérieurs n’ont pas autant de mises à jour remplacées et par conséquent, ne sont pas vulnérables à ce problème.

**Résolution** :  
1. Connectez-vous au [portail Azure](https://portal.azure.com) et ouvrez **Microsoft Intune**. 
2. Sélectionnez **Mises à jour logicielles**.
3. Refusez toutes les mises à jour remplacées qui peuvent s’appliquer à Windows 7 ou aux applications (par exemple, Microsoft Office) qui ont été installées sur les clients concernés.
4. Redémarrez les clients concernés.

En outre, si vous utilisez Windows 7, vérifiez que vous disposez de la mise à jour suivante installée :[3050265 Client de mise à jour Windows pour Windows 7 : juin 2015](https://support.microsoft.com/kb/3050265).

### <a name="next-steps"></a>Étapes suivantes
Si ces informations ne vous aident pas, vous pouvez également [bénéficier d’un support technique pour Microsoft Intune](get-support.md).