---
title: Résolution des problèmes d’accès aux ressources d’entreprise | Microsoft Docs
description: Utilisez les codes d’erreur et d’état de Microsoft Intune pour résoudre les problèmes d’accès aux ressources.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 40622ced-6029-4abf-873e-b51d2b51934c
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: e600c2db57352eb2348ded9fe55295837223797b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843083"
---
# <a name="troubleshoot-company-resource-access-problems-with-microsoft-intune"></a>Résoudre les problèmes d’accès aux ressources d’entreprise avec Microsoft Intune

Utilisez les codes d’erreur et d’état de cette rubrique pour vous aider à résoudre les problèmes à l’origine des codes d’erreur retournés dans Microsoft Intune.

Si ces informations ne vous permettent pas de remédier à votre problème, consultez [Comment obtenir un support technique pour Microsoft Intune](get-support.md) pour accéder à d’autres types d’assistance.

## <a name="status-codes-for-mdm-managed-windows-devices"></a>Codes d'état des appareils Windows gérés par MDM

|Code d'état|Message d'erreur|Procédure à suivre|
|---------------|-----------------|--------------|
|10 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Installation en cours||
|20 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|En attente de contenu||
|30 (APP_CI_ENFORCEMENT_ERROR_RETRIEVING_CONTENT)|Extraction de contenu|Cause probable : L'état du travail 30 indique l'échec d'un téléchargement d'application lancé par un utilisateur.<br /><br />Les causes probables de ce problème sont les suivantes :<br /><br />La connexion Internet de l'appareil a été interrompue pendant le téléchargement.<br /><br />Le certificat émis à l'appareil au moment de l'inscription est peut-être arrivé à expiration.<br /><br />Prévention :<br /><br />Lancez l'application Applications d'entreprise à partir du Panneau de configuration de l'appareil pour vérifier que le certificat de l'appareil n'est pas arrivé à expiration ; s'il a expiré, vous devez réinscrire l'appareil.<br /><br />Vérifiez que l'appareil est connecté à Internet et réessayez de demander l'application.|
|40 (APP_CI_ENFORCEMENT_IN_PROGRESS_CONTENT_DOWNLOADED)|Téléchargement de contenu terminé||
|50 (APP_CI_ENFORCEMENT_IN_PROGRESS_INSTALLING)|Installation en cours||
|60 (APP_CI_ENFORCEMENT_ERROR_INSTALLING)|Une erreur d’installation s'est produite|Échec de l'installation de l'application après le téléchargement.<br /><br />Le certificat de signature de code avec lequel l'application a été signée n'est pas présente sur l'appareil.<br /><br />Une infrastructure dont dépend l’application n’est pas installée sur l’appareil.<br /><br />Vérifiez que le certificat de signature de code avec lequel votre application a été signée est présent sur l'appareil et confirmez avec l'administrateur que tous les appareils Windows RT inscrits dans l'entreprise ciblent ce certificat.<br /><br />Si l'échec de l'installation est dû à une dépendance d'infrastructure manquante, l'administrateur doit republier l'application en empaquetant l'infrastructure dans le package d'application.<br /><br />Le package d'application téléchargé n'est pas un package valide, a peut-être été endommagé ou peut ne pas être compatible avec la version du système d'exploitation installé sur l'appareil.|
|70 (APP_CI_ENFORCEMENT_SUCCEEDED)|Réussite de l'installation||
|80 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Désinstallation en cours||
|90 (APP_CI_ENFORCEMENT_ERROR)|Erreur de désinstallation||
|100 (APP_CI_ENFORCEMENT_SUCCEEDED)|Réussite de la désinstallation||
|110 (APP_CI_ENFORCEMENT_ERROR)|Incohérence du hachage de contenu||
|120 (APP_CI_ENFORCEMENT_ERROR)|SLK / chargement de version test non activé||
|130 (APP_CI_ENFORCEMENT_ERROR)|Échec de l'installation de la licence MSADP||
|Aucun état (APP_CI_ENFORCEMENT_UNKNOWN)|Non applicable|L'état est actuellement inconnu.|

## <a name="company-resource-access-common-errors"></a>Accès aux ressources d'entreprise (erreurs fréquentes)

|Code d'état|Code d’erreur hexadécimal|Message d'erreur|
|---------------|--------------------------|-----------------|
|-2016281101|0x87D1FDF3|Requête MDM CRP introuvable|
|-2016281102|0x87D1FDF2|URL NDES introuvable|
|-2016281103|0x87D1FDF1|Information de certificat MDM CRP introuvable|
|-2016281104|0x87D1FDF0|Information de certificat MDM CI introuvable|
|-2016281105|0x87D1FDEF|Impossible d'évaluer la règle|
|-2016281106|0x87D1FDEE|Non applicable en raison d'une résolution de conflits|
|-2016281107|0x87D1FDED|Source de découverte de paramètre non prise en charge|
|-2016281108|0x87D1FDEC|Paramètre référencé introuvable dans l'élément de configuration|
|-2016281109|0x87D1FDEB|Échec de la conversion du type de données|
|-2016281110|0x87D1FDEA|Paramètre non valide sur le paramètre CIM|
|-2016281111|0x87D1FDE9|Ne s'applique pas à cet appareil|
|-2016281112|0x87D1FDE8|Échec de la correction|
|-2016330905|0x87D13B67|L'état de l'application est inconnu|
|-2016330906|0x87D13B66|L'application est gérée, mais elle a été supprimée par l'utilisateur|
|-2016330907|0x87D13B65|L'appareil échange son code d'échange|
|-2016330908|0x87D13B64|L'installation de l'application a échoué|
|-2016330909|0x87D13B63|L'utilisateur a refusé la mise à jour de l'application|
|-2016330910|0x87D13B62|L'utilisateur a refusé l'installation de l'application|
|-2016330911|0x87D13B61|L'utilisateur a installé l'application avant que l'installation d'application gérée puisse avoir lieu|
|-2016330912|0x87D13B60|L'installation de l'application est planifiée, mais un code d'échange est requis pour terminer la transaction|
|-2016341109|0x87D1138B|L'appareil iOS a retourné une erreur|
|-2016341110|0x87D1138A|L'appareil iOS a rejeté la commande en raison d'un format incorrect|
|-2016341111|0x87D11389|L'appareil iOS a retourné un état inactif inattendu|
|-2016341112|0x87D11388|L'appareil iOS est actuellement occupé|

## <a name="errors-returned-by-ios-devices"></a>Erreurs retournées par les appareils iOS

### <a name="company-portal-errors"></a>Erreurs du portail d’entreprise

|Texte d’erreur dans le portail d’entreprise|Code d'état HTTP|Informations supplémentaires sur l’erreur|
|---|---|---|
|__Problème de serveur interne__ <br>Il semble que nous n’ayez pas pu nous joindre en raison d’une erreur interne sur notre serveur. Réessayez, puis contactez votre administrateur informatique si le problème persiste.|Erreur 500|Cette erreur est probablement due à un problème au niveau du service Intune. Le problème doit être résolu du côté du service Intune et n’est probablement pas dû à un problème du côté client.|
|__Temporairement indisponible__ <br>Il semble que nous n’ayez pas pu nous joindre car notre service est temporairement indisponible. Réessayez, puis contactez votre administrateur informatique si le problème persiste.|Erreur 503|Il s’agit probablement d’un problème temporaire au niveau du service Intune, tel qu’une maintenance en cours. Le problème doit être résolu du côté du service Intune et n’est probablement pas dû à un problème du côté client.|
|__Impossible de se connecter au serveur__ <br>Il semble que nous n’ayez pas pu nous joindre. Réessayez, puis contactez votre administrateur informatique si le problème persiste.|Non associé à un code d’état HTTP|Impossible d’établir une connexion sécurisée au serveur. Cela est probablement dû à un problème SSL avec les certificats utilisés. Ce problème peut être dû à des configurations de clients non conformes aux exigences d’Apple en matière de sécurité de transport d’application (ATS, App Transport Security).|
|__Un problème s’est produit__ <br>Impossible de charger le client du portail d’entreprise. Réessayez, puis contactez votre administrateur informatique si le problème persiste.|Erreur 400|Toute erreur ayant un code d’état HTTP dans les 400 et qui ne dispose pas d’un message d’erreur plus spécifique provoque l’affichage de ce message. Il s’agit d’une erreur côté client qui se produit dans l’application Portail d’entreprise pour iOS.|
|__Serveur inaccessible__ <br>Il semble que nous n’ayez pas pu nous joindre. Réessayez, puis contactez votre administrateur informatique si le problème persiste.|Erreur 500|Toute erreur ayant un code d’état HTTP dans les 500 et qui ne dispose pas d’un message d’erreur plus spécifique provoque l’affichage de ce message. Il s’agit d’une erreur côté service dans le service Intune.|

### <a name="service-errors"></a>Erreurs de service

|Code d'état|Code d’erreur hexadécimal|Message d'erreur|
|---------------|--------------------------|-----------------|
|-2016299111|0x87D1B799|Erreur interne|
|-2016299112|0x87D1B798|Erreur interne|
|-2016300111|0x87D1B3B1|36001 : (erreur interne)|
|-2016300112|0x87D1B3B0|36000 : appareil cellulaire déjà configuré|
|-2016301110|0x87D1AFCA|35002 : plusieurs polices dans une seule charge utile|
|-2016301111|0x87D1AFC9|35001 : échec de l'installation de la police|
|-2016301112|0x87D1AFC8|35000 : données de police non valides|
|-2016302109|0x87D1ABE3|34003 : nom de principal Kerberos non valide|
|-2016302110|0x87D1ABE2|34002 : nom de principal Kerberos manquant|
|-2016302111|0x87D1ABE1|34001 : modèle de correspondance d'URL non valide|
|-2016302112|0x87D1ABE0|34000 : modèle de correspondance d'identificateur d'application non valide|
|-2016304112|0x87D1A410|32000 : applications trop nombreuses|
|-2016305111|0x87D1A029|31001: impossible d'appliquer les paramètres|
|-2016305112|0x87D1A028|31000 : impossible d'appliquer les informations d'identification|
|-2016306111|0x87D19C41|30001: délai d'attente dépassé|
|-2016306112|0x87D19C40|30000 : échec de l'authentification|
|-2016307109|0x87D1985B|29003 : données de certificat incorrectes|
|-2016307110|0x87D1985A|29002 :|
|-2016307111|0x87D19859|29001 :|
|-2016307112|0x87D19858|29000 : appareil non supervisé|
|-2016308110|0x87D19472|28002 : impossible de définir le papier peint|
|-2016308111|0x87D19471|28001 : image de papier peint incorrecte|
|-2016308112|0x87D19470|28000 : élément inconnu|
|-2016310111|0x87D18CA1|26001 : chiffrement au niveau du fichier non pris en charge|
|-2016310112|0x87D18CA0|26000 : chiffrement au niveau du bloc non pris en charge|
|-2016311110|0x87D188BA|25002 : suppression impossible|
|-2016311111|0x87D188B9|25001 : installation impossible|
|-2016311112|0x87D188B8|25000 : profil incorrect|
|-2016312109|0x87D184D3|24003 : profil final incorrect|
|-2016312110|0x87D184D2|24002 : charge utile d'identité incorrecte|
|-2016312111|0x87D184D1|24001 : impossible de signer le dictionnaire d'attributs|
|-2016312112|0x87D184D0|24000 : impossible de créer le dictionnaire d'attributs|
|-2016313110|0x87D180EA|23002 : certificat serveur incorrect|
|-2016313111|0x87D180E9|23001 : réponse du serveur incorrecte|
|-2016313112|0x87D180E8|23000 : identité incorrecte|
|-2016314099|0x87D17D0D|22013 : réponse PKIOperation non valide|
|-2016314100|0x87D17D0C|22012 : impossible de stocker CACertificate|
|-2016314101|0x87D17D0B|22011 : impossible de générer CSR|
|-2016314102|0x87D17D0A|22010 : impossible de stocker l'identité temporaire|
|-2016314103|0x87D17D09|22009 : impossible de créer l'identité temporaire|
|-2016314104|0x87D17D08|22008 : impossible de créer l'identité|
|-2016314105|0x87D17D07|22007 : certificat signé non valide|
|-2016314106|0x87D17D06|22006 : CACaps insuffisants|
|-2016314107|0x87D17D05|22005 : erreur réseau|
|-2016314108|0x87D17D04|22004 : configuration de certificat non prise en charge|
|-2016314109|0x87D17D03|22003 : RAResponse non valide|
|-2016314110|0x87D17D02|22002 : CAResponse non valide|
|-2016314111|0x87D17D01|22001: impossible de générer la paire de clés|
|-2016314112|0x87D17D00|22000 : utilisation de la clé non valide|
|-2016315105|0x87D1791F|21007 : impossible de vérifier le compte|
|-2016315106|0x87D1791E|21006 : impossible de déchiffrer le certificat|
|-2016315107|0x87D1791D|21005 : le compte n’est pas unique (un profil de messagerie existe déjà sur l’appareil)|
|-2016315108|0x87D1791C|21004 : impossible de créer le compte|
|-2016315109|0x87D1791B|21003 : aucun nom d'hôte|
|-2016315110|0x87D1791A|21002 : impossible de se conformer à la stratégie de chiffrement du serveur|
|-2016315111|0x87D17919|21001 : impossible de se conformer à la stratégie du serveur|
|-2016315112|0x87D17918|21000 : impossible d'obtenir la stratégie du serveur|
|-2016316110|0x87D17532|20002 : le compte n'est pas unique|
|-2016316111|0x87D17531|20001 : aucun nom d'hôte|
|-2016316112|0x87D17530|20000 : impossible de créer le compte|
|-2016317110|0x87D1714A|19002 : le compte n'est pas unique|
|-2016317111|0x87D17149|19001 : aucun nom d'hôte|
|-2016317112|0x87D17148|19000 : impossible de créer le compte|
|-2016318110|0x87D16D62|18002 : informations d'identification non valides|
|-2016318111|0x87D16D61|18001 : hôte indisponible|
|-2016318112|0x87D16D60|18000 : erreur inconnue|
|-2016319110|0x87D1697A|17002 : le compte n'est pas unique|
|-2016319111|0x87D16979|17001 : aucun nom d'hôte|
|-2016319112|0x87D16978|17000 : impossible de créer le compte|
|-2016320110|0x87D16592|16002 : le compte n'est pas unique|
|-2016320111|0x87D16591|16001 : aucun nom d'hôte|
|-2016320112|0x87D16590|16000 : impossible de créer l'abonnement|
|-2016321109|0x87D161AB|15003 : certificat non valide|
|-2016321110|0x87D161AA|15002 : impossible de verrouiller la configuration du réseau|
|-2016321111|0x87D161A9|15001 : impossible de supprimer le VPN|
|-2016321112|0x87D161A8|15000 : impossible d'installer le VPN|
|-2016322110|0x87D15DC2|14002 : la configuration cloud existe déjà|
|-2016322111|0x87D15DC1|14001 : appareil verrouillé|
|-2016322112|0x87D15DC0|14000 : champ non valide|
|-2016323107|0x87D159DD|13005 : impossible de configurer le proxy|
|-2016323108|0x87D159DC|13004 : impossible de configurer EAP|
|-2016323109|0x87D159DB|13003: impossible de créer la configuration WiFi|
|-2016323110|0x87D159DA|13002 : mot de passe requis|
|-2016323111|0x87D159D9|13001 : nom d'utilisateur requis|
|-2016323112|0x87D159D8|13000 : installation impossible|
|-2016324070|0x87D1561A|12042 : code de paramètres régionaux inconnu|
|-2016324071|0x87D15619|12041 : code de langue inconnu|
|-2016324072|0x87D15618|12040 : identifiant de connexion à l'iTunes Store requis|
|-2016324073|0x87D15617|12039 : (inutilisé)|
|-2016324074|0x87D15616|12038 : application non gérée|
|-2016324075|0x87D15615|12037 : code d'échange non valide|
|-2016324076|0x87D15614|12036 : impossible de supprimer l'application à l'état actuel|
|-2016324077|0x87D15613|12035 : impossible d'acheter l'application|
|-2016324078|0x87D15612|12034 : l'URL n'est pas HTTPS|
|-2016324079|0x87D15611|12033 : manifeste non valide|
|-2016324080|0x87D15610|12032 : applications trop nombreuses dans le manifeste|
|-2016324081|0x87D1560F|12031 : installation d'application désactivée|
|-2016324082|0x87D1560E|12030 : URL non valide|
|-2016324083|0x87D1560D|12029 : application non gérée|
|-2016324084|0x87D1560C|12028 : sans attendre l'échange|
|-2016324085|0x87D1560B|12027 : ceci n'est pas une application|
|-2016324086|0x87D1560A|12026 : application déjà en file d'attente|
|-2016324087|0x87D15609|12025 : application déjà installée|
|-2016324088|0x87D15608|12024 : impossible de valider le manifeste de l'application|
|-2016324089|0x87D15607|12023 : impossible de valider l'ID de l'application|
|-2016324090|0x87D15606|12022 : rubrique non valide|
|-2016324091|0x87D15605|12021 : type de demande non valide|
|-2016324092|0x87D15604|12020 : non autorisé par le serveur|
|-2016324093|0x87D15603|12019 : impossible de copier la clé (escrow) secrète|
|-2016324094|0x87D15602|12018 : impossible de copier les données de conteneur de clés escrow|
|-2016324095|0x87D15601|12017 : impossible de créer le conteneur de clés escrow|
|-2016324096|0x87D15600|12016 : identité manquante|
|-2016324097|0x87D155FF|12015 : impossible d'émettre (push) le jeton|
|-2016324098|0x87D155FE|12014 : configuration du profil non gérée|
|-2016324099|0x87D155FD|12013 : profil non géré|
|-2016324100|0x87D155FC|12012 : incohérence de remplacement MDM|
|-2016324101|0x87D155FB|12011 : configuration MDM non valide|
|-2016324102|0x87D155FA|12010 : erreur d'incohérence interne|
|-2016324103|0x87D155F9|12009 : profil de remplacement non valide|
|-2016324104|0x87D155F8|12008 : format de demande incorrect|
|-2016324105|0x87D155F7|12007 : non autorisé|
|-2016324106|0x87D155F6|12006 : redirection refusée|
|-2016324107|0x87D155F5|12005 : certificat introuvable|
|-2016324108|0x87D155F4|12004 : certificat push non valide|
|-2016324109|0x87D155F3|12003 : réponse de test non valide|
|-2016324110|0x87D155F2|12002 : archivage impossible|
|-2016324111|0x87D155F1|12001 : plusieurs instances MDM|
|-2016324112|0x87D155F0|12000 : droits d'accès incorrects|
|-2016325111|0x87D15209|11001 : APN personnalisé déjà installé|
|-2016325112|0x87D15208|11000 : impossible d'installer l'APN|
|-2016326111|0x87D14E21|10001 : signataire incorrect|
|-2016326112|0x87D14E20|10000 : impossible d'installer les éléments par défaut|
|-2016327106|0x87D14A3E|9006 : le certificat n'est pas une identité|
|-2016327107|0x87D14A3D|9005 : format du certificat incorrect|
|-2016327108|0x87D14A3C|9004 : impossible de stocker le certificat racine|
|-2016327109|0x87D14A3B|9003 : impossible de stocker les données WAPI|
|-2016327110|0x87D14A3A|9002 : impossible de stocker le certificat|
|-2016327111|0x87D14A39|9001 : certificats trop nombreux dans une charge utile|
|-2016327112|0x87D14A38|9000 : mot de passe non valide|
|-2016328112|0x87D14650|8000 : impossible d'installer Web Clip|
|-2016329105|0x87D1426F|7007 : compte SMTP mal configuré|
|-2016329106|0x87D1426E|7006 : compte POP mal configuré|
|-2016329107|0x87D1426D|7005 : compte IMAP mal configuré|
|-2016329108|0x87D1426C|7004 : certificat SMIME incorrect|
|-2016329109|0x87D1426B|7003 : certificat SMIME introuvable|
|-2016329110|0x87D1426A|7002 : une erreur inconnue s'est produite pendant la validation|
|-2016329111|0x87D14269|7001 : informations d'identification non valides|
|-2016329112|0x87D14268|7000 : hôte indisponible|
|-2016330110|0x87D13E82|6002 : impossible de créer la requête|
|-2016330111|0x87D13E81|6001 : chaîne vide|
|-2016330112|0x87D13E80|6000 : erreur système Keychain|
|-2016331097|0x87D13AA7|5015 : impossible de définir la période de grâce|
|-2016331098|0x87D13AA6|5014 : impossible de définir le code secret|
|-2016331099|0x87D13AA5|5013 : impossible de supprimer le code secret|
|-2016331100|0x87D13AA4|5012 : (inutilisé)|
|-2016331101||5011 : code secret incorrect|
|-2016331102||5010 : appareil verrouillé|
|-2016331103|0x87D13AA4|5009 : (inutilisé)|
|-2016331104|0x87D13AA0|5008 : code secret trop récent|
|-2016331105|0x87D13A9F|5007 : code secret expiré|
|-2016331106|0x87D13AA3|5006 : le code secret requiert des caractères alpha|
|-2016331107|0x87D13A9D|5005 : le code secret requiert des chiffres|
|-2016331108|0x87D13A9C|5004 : le code secret contient des caractères croissant/décroissant|
|-2016331109|0x87D13A9B|5003 : le code secret contient des caractères qui se répètent|
|-2016331110|0x87D13A9A|5002 : trop peu de caractères complexes|
|-2016331111|0x87D13A99|5001 : trop peu de caractères uniques|
|-2016331112|0x87D13A98|5000 : code secret trop court|
|-2016332093|0x87D136C3|4019 : plusieurs charges utiles de verrouillage d'application|
|-2016332094|0x87D136C2|4018 : plusieurs APN ou charges utiles cellulaires|
|-2016332095|0x87D136C1|4017 : plusieurs charges utiles HTTPProxy globales|
|-2016332096|0x87D136C0|4016 : (erreur interne)|
|-2016332097|0x87D136BF|4015 : le profil de remplacement ne contient pas une charge utile MDM|
|-2016332098|0x87D136BE|4014 : aucune identité d'appareil disponible|
|-2016332099|0x87D136BD|4013 : échec de la mise à jour|
|-2016332100|0x87D136BC|4012 : impossible de mettre à jour le profil|
|-2016332101|0x87D136BB|4011 : le profil final n'est pas un profil de configuration|
|-2016332102|0x87D136BA|4010 : le profil mis à jour n'a pas le même identificateur|
|-2016332103|0x87D136B9|4009 : appareil verrouillé|
|-2016332104|0x87D136B8|4008 : certificats incohérents|
|-2016332105|0x87D136B7|4007 : format de fichier non reconnu|
|-2016332106|0x87D136B6|4006 : date de suppression du profil dans le passé|
|-2016332107|0x87D136B5|4005 : code secret non conforme|
|-2016332108|0x87D136B4|4004 : installation annulée par l'utilisateur|
|-2016332109|0x87D136B3|4003 : le profil pour l'installation n'est pas en file d'attente|
|-2016332110|0x87D136B2|4002 : UUID en double|
|-2016332111|0x87D136B1|4001 : échec de l'installation|
|-2016332112|0x87D136B0|4000 : impossible d'analyser le profil|
|-2016333111|0x87D132C9|3001 : comparaison de valeurs incohérentes (erreur interne)|
|-2016333112|0x87D132C8|3000 : restrictions incohérentes (erreur interne)|
|-2016334108|0x87D12EE4|2004 : valeur de champ non prise en charge|
|-2016334109|0x87D12EE3|2003 : type de données incorrect dans le champ|
|-2016334110|0x87D12EE2|2002 : champ requis manquant|
|-2016334111|0x87D12EE1|2001 : version de charge utile non prise en charge|
|-2016334112|0x87D12EE0|2000 : format de charge utile incorrect|
|-2016335102|0x87D12B02|1010 : valeur de champ non prise en charge|
|-2016335103|0x87D12B01|1009 : échec d'installation du profil|
|-2016335104|0x87D12B00|1008 : identificateurs de charge utile non uniques|
|-2016335105|0x87D12AFF|1007 : UUID non uniques|
|-2016335106|0x87D12AFE|1006 : déchiffrement impossible|
|-2016335107|0x87D12AFD|1005 : profil vide|
|-2016335108|0x87D12AFC|1004 : signature incorrecte|
|-2016335109|0x87D12AFB|1003 : type de données incorrect dans le champ|
|-2016335110|0x87D12AFA|1002 : champ requis manquant|
|-2016335111|0x87D12AF9|1001 : version de profil non prise en charge|
|-2016335112|0x87D12AF8|1000 : format de profil incorrect|

## <a name="oma-response-codes"></a>Codes de réponse OMA

|Code d'état|Code d’erreur hexadécimal|Message d'erreur|
|---------------|--------------------------|-----------------|
|-2016344008|0x87D10838|(1404) : accès au certificat refusé|
|-2016344009|0x87D10837|(1403) : certificat introuvable|
|-2016344010|0x87D10836|DCMO(1402) : échec de l'opération|
|-2016344011|0x87D10835|DCMO(1401) : l'utilisateur a choisi de ne pas accepter l'opération proposée|
|-2016344012|0x87D10834|DCMO(1400) : erreur du client|
|-2016344108|0x87D107D4|DCMO(1204) : la fonctionnalité de l'appareil est désactivée, et l'utilisateur est autorisé à la réactiver|
|-2016344109|0x87D107D3|DCMO(1203) : la fonctionnalité de l'appareil est désactivée, et l'utilisateur n'est pas autorisé à la réactiver|
|-2016344110|0x87D107D2|DCMO(1202) : l'opération d'activation est effectuée avec succès mais la fonctionnalité de l'appareil est actuellement détachée|
|-2016344111|0xF3FB4D95|DCMO(1201) : l'opération d'activation est effectuée avec succès mais la fonctionnalité de l'appareil est actuellement attachée|
|-2016344112|0x87D107D0|DCMO(1200) : l'opération est effectuée avec succès|
|-2016345595|0x87D10205|Syncml(517) : la réponse à une commande atomique était trop volumineuse pour tenir dans un seul message.|
|-2016345596|0x87D10204|SyncML(516) : une commande était dans un élément Atomic et Atomic a échoué. Cette commande n'a pas été restaurée avec succès.|
|-2016345598|0x87D10202|Syncml(514) : la commande SyncML n'a pas été exécutée correctement, car l'opération était déjà annulée avant le traitement de la commande.|
|-2016345599|0x87D10201|SyncML(513) : le destinataire ne prend pas en charge ou refuse de prendre en charge la version spécifiée du protocole de synchronisation SyncML utilisé dans le message SyncML de requête.|
|-2016345600|0x87D10200|SyncML(512) : une erreur d'application s'est produite durant la session de synchronisation|
|-2016345601|0x87D101FF|Syncml(511) : une erreur grave s'est produite sur le serveur durant le traitement de la requête.|
|-2016345602|0x87D101FE|Syncml(510) : une erreur s'est produite durant le traitement de la requête. L'erreur est liée à un échec du magasin de données du destinataire.|
|-2016345603|0x87D101FD|SyncML(509) : réservé à une utilisation future.|
|-2016345604|0x87D101FC|SyncML(508) : une erreur s'est produite et nécessite une actualisation de l'état de synchronisation actuel du client avec le serveur.|
|-2016345605|0x87D101FB|Syncml(507) : l'erreur a provoqué l'échec de toutes les commandes SyncML dans un type d'élément Atomic.|
|-2016345606|0x87D101FA|Syncml(506) : une erreur d'application s'est produite durant le traitement de la requête.|
|-2016345607|0x87D101F9|Syncml(505) : le destinataire ne prend pas en charge ou refuse de prendre en charge la version spécifiée du fichier DTD SyncML utilisé dans le message SyncML de requête.|
|-2016345608|=0x87D101F8|Syncml(504) : le destinataire, qui sert de passerelle ou de proxy, n'a pas reçu de réponse dans les temps de la part du destinataire en amont spécifié par l'URI (par ex. HTTP, FTP, LDAP) ou d'un destinataire auxiliaire (par ex. DNS) auquel il avait besoin d'accéder pour tenter d'exécuter la requête.|
|-2016345609|0x87D101F7|Syncml(503) : le destinataire est actuellement incapable de traiter la requête en raison d'une surcharge temporaire ou de la maintenance du destinataire.|
|-2016345610|0x87D101F6|Syncml(502) : le destinataire, utilisé en tant que passerelle ou proxy, a reçu une réponse non valide du destinataire en amont auquel il a accédé pour répondre à la requête.|
|-2016345611|0x87D101F5|Syncml(501) : le destinataire ne prend pas en charge la commande nécessaire pour exécuter la requête.|
|-2016345612|0x87D101F4|SyncML(500) : le destinataire a rencontré une situation inattendue qui l'a empêché de répondre à la requête|
|-2016345684|0x87D101AC|Syncml(428) : échec du déplacement|
|-2016345685|0x87D101AB|Syncml(427) : le parent ne peut pas être supprimé, car il contient des enfants.|
|-2016345686|0x87D101AA|Syncml(426) : élément partiel non accepté.|
|-2016345687|0x87D101A9|Syncml(425) : échec de la commande demandée, car l'émetteur ne dispose pas des autorisations de liste de contrôle d'accès (ACL) adéquates sur le destinataire.|
|-2016345688|0x87D101A8|Syncml(424) : l'objet mémorisé en bloc a été reçu, mais la taille de l'objet reçu ne correspond pas à la taille déclarée dans le premier bloc.|
|-2016345689|0x87D101A7|Syncml(423) : échec de la commande, car l'élément ayant fait l'objet d'une suppression réversible a fait précédemment l'objet d'une suppression définitive sur le serveur.|
|-2016345690|0x87D101A6|Syncml(422) : échec de la commande demandée sur le serveur, car le format du script CGI dans LocURI est incorrect.|
|-2016345691|0x87D101A5|SyncML(421) : échec de la commande demandée sur le serveur, car la grammaire de recherche spécifiée est inconnue.|
|-2016345692|0x87D101A4|Syncml(420) : le destinataire n'a plus d'espace de stockage pour les données de synchronisation restantes.|
|-2016345693|0x87D101A3|Syncml(419) : la requête cliente a créé un conflit qui a été résolu par la commande serveur gagnante|
|-2016345694|0x87D101A2|Syncml(418) : échec de la commande Put ou Add demandée, car la cible existe déjà.|
|-2016345695|0x87D101A1|Syncml(417) : échec de la requête pour le moment. Son auteur doit la réessayer plus tard.|
|-2016345696|0x87D101A0|Syncml(416) : échec de la requête, car la taille en octets spécifiée dans la requête est trop grande.|
|-2016345697|0x87D1019F|Syncml(415) : type ou format de média non pris en charge.|
|-2016345698|0x87D1019E|Syncml(414) : échec de la commande demandée, car l'URI cible est trop long pour ce que le destinataire peut ou veut traiter.|
|-2016345699|0x87D1019D|Syncml(413) : le destinataire refuse d'exécuter la commande demandée, car l'élément demandé est plus volumineux que ce que le destinataire peut ou veut traiter.|
|-2016345700|0x87D1019C|Syncml(412) : échec de la commande demandée sur le destinataire, car elle est incomplète ou mal formée.|
|-2016345701|0x87D1019B|Syncml(411) : la commande demandée doit être accompagnée d'informations sur la taille ou la longueur en octets dans le type d'élément Méta.|
|-2016345702|0x87D1019A|Syncml(410) : la cible demandée ne se trouve plus sur le destinataire et aucun URI de transfert n'est connu.|
|-2016345703|0x87D10199|SyncML(409) : échec de la commande demandée en raison d'un conflit de mise à jour entre les versions cliente et serveur des données.|
|-2016345704|0x87D10198|SyncML(408) : un message attendu n'a pas été reçu dans le délai imparti.|
|-2016345705|0x87D10197|SyncML(407) : échec de la commande demandée, car son auteur doit fournir une authentification correcte.|
|-2016345706|0x87D10196|SyncML(406) : échec de la commande demandée, car une fonctionnalité facultative dans la requête n'est pas prise en charge.|
|-2016345707|0x87D10195|SyncML(405) : la commande demandée n'est pas autorisée sur la cible.|
|-2016345708|0x87D10194|SyncML(404) : la cible demandée est introuvable.|
|-2016345709|0x87D10193|SyncML(403) : échec de la commande demandée, mais le destinataire l'a comprise.|
|-2016345710|0x87D10192|Syncml(402) : échec de la commande demandée, car un paiement correct est nécessaire.|
|-2016345711|0x87D10191|Syncml(401) : échec de la commande demandée, car le demandeur doit fournir une authentification correcte.|
|-2016345712|0x87D10190|Syncml(400) : la commande demandée n'a pas pu être exécutée en raison d'une syntaxe incorrecte.|
|-2016345807|0x87D10131|Syncml(305) : la cible demandée doit être accessible via l'URI de proxy spécifié.|
|-2016345808|0x87D10130|Syncml(304) : la commande SyncML demandée n'a pas été exécutée sur la cible.|
|-2016345809|0x87D1012F|Syncml(303) : la cible demandée se trouve sur un autre URI.|
|-2016345810|0x87D1012E|Syncml(302) : la cible demandée a été déplacée temporairement vers un autre URI.|
|-2016345811|0x87D1012D|Syncml(301) : la cible demandée a un nouvel URI.|
|-2016345812|0x87D1012C|Syncml(300) : la cible demandée fait partie d'un ensemble de plusieurs autres cibles demandées.|
|-2016345896|0x87D100D8|Syncml(216) : une commande était dans un élément Atomic et Atomic a échoué. Cette commande a été restaurée correctement.|
|-2016345897|0x87D100D7|Syncml(215) : une commande n'a pas été exécutée en raison d'une interaction de l'utilisateur. L'utilisateur a décidé de ne pas accepter le choix proposé.|
|-2016345898|0x87D100D6|Syncml(214) : opération annulée. La commande SyncML s'est exécutée correctement, mais aucune commande supplémentaire ne sera traitée dans la session.|
|-2016345899|0x87D100D5|SyncML(213) : l'élément mémorisé en bloc a été accepté et mis en mémoire tampon.|
|-2016345900|0x87D100D4|SyncML(212) : authentification acceptée. Aucune authentification supplémentaire n'est nécessaire pour le reste de la session de synchronisation. Ce code de réponse ne peut être utilisé qu'en réponse à une requête dans laquelle les informations d'identification ont été fournies.|
|-2016345901|0x87D100D3|SyncML(211) : élément non supprimé. L'élément demandé est introuvable. Il a peut-être été supprimé auparavant.|
|-2016345902|0x87D100D2|SyncML(210) : suppression sans archivage. La réponse indique que les données demandées ont été supprimées correctement mais qu'elles n'ont pas été archivées avant la suppression, car cette fonctionnalité optionnelle n'était pas prise en charge par l'implémentation.|
|-2016345903|0x87D100D1|Conflit résolu par duplication. La réponse indique que la requête a créé un conflit de mise à jour, lequel a été résolu par une duplication des données du client en cours de création dans la base de données du serveur. La réponse inclut à la fois l'URI cible du doublon dans l'élément de l'état. En outre, dans le cas d'une synchronisation bidirectionnelle, une commande Add est retournée avec la définition des données dupliquées.|
|-2016345904|0x87D100D0|Conflit résolu par la commande « gagnante » du client. La réponse indique l'existence d'un conflit de mise à jour, lequel a été résolu par la commande cliente gagnante.|
|-2016345905|0x87D100CF|Conflit résolu par fusion. La réponse indique que la requête a créé un conflit, lequel a été résolu par une fusion des instances cliente et serveur des données. La réponse inclut à la fois les URL cible et source dans l'élément de l'état. En outre, une commande Replace est retournée avec les données fusionnées.|
|-2016345906|0x87D100CE|La réponse indique qu'une partie de la commande seulement a été exécutée. Si le reste de la commande peut être exécuté plus tard, un autre code d'état de requête d'achèvement approprié DOIT être créé à l'issue de cette exécution.|
|-2016345907|0x87D100CD|La source DOIT mettre à jour son contenu. L'auteur de la requête DOIT synchroniser le contenu de cette dernière pour obtenir une version à jour.|
|-2016345908|0x87D100CC|La requête a été exécutée correctement, mais aucune donnée n'est retournée. Le code de réponse est également retourné en réponse à une commande Get quand la cible n'a aucun contenu.|
|-2016345909|0x87D100CB|Réponse ne faisant pas autorité. La requête obtient une réponse de la part d'une autre entité que celle ciblée. La réponse n'est retournée qu'au moment où la requête entraîne la génération d'un code de réponse 200 de la part de la cible faisant autorité.|
|-2016345910|0x87D100CA|Accepté pour traitement. La requête visant à exécuter à distance une application, ou à alerter un utilisateur ou une application a été effectuée correctement.|
|-2016345911|0x87D100C9|L'élément demandé a été ajouté.|
|-2016345912|0x87D100C8|La commande SyncML s'est exécutée correctement.|
|-2016346011|0x87D10065|La commande SyncML spécifiée est en cours d'exécution, mais n'est pas encore finie.|

### <a name="next-steps"></a>Étapes suivantes
Si ces informations de dépannage n’ont pas permis de vous aider, contactez le support Microsoft comme décrit dans [Comment obtenir un support technique pour Microsoft Intune](get-support.md).
