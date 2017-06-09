---
title: "Résolution des problèmes de profils d’appareil dans Microsoft Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Version préliminaire d&quot;Intune Azure : si vous ne savez pas comment vous y prendre, utilisez cette rubrique pour vous aider à résoudre les problèmes de profils d’appareil Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2f3586c4cbe37c44cc289ba3ea47bf127c150d35
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---

# <a name="troubleshooting-device-profiles-in-microsoft-intune"></a>Résoudre les problèmes de profil d’appareil dans Microsoft Intune


[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Les informations contenues dans cette rubrique peuvent être utilisées pour vous aider à résoudre les problèmes courants avec les profils d’appareil Intune.

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Combien de temps faut-il pour que les appareils mobiles obtiennent une stratégie ou les applications une fois que celles-ci ont été affectées ?
Quand une stratégie ou une application est affectée, Intune essaie d’envoyer immédiatement une notification à l’appareil pour qu’il s’enregistre auprès du service Intune. Cette opération prend généralement moins de 5 minutes.

Si un appareil ne se manifeste pas pour obtenir la stratégie après l’envoi de la première notification, Intune effectue trois autres tentatives.  Si l’appareil est hors connexion (par exemple, s’il est éteint ou n’est pas connecté à un réseau), il ne peut pas recevoir de notifications. Dans ce cas, l’appareil obtiendra la stratégie lors de son prochain enregistrement planifié auprès du service Intune, de la manière suivante :

- iOS et macOS : toutes les 6 heures.
- Android  : toutes les 8 heures.
- Windows Phone : toutes les 8 heures.
- PC Windows 8.1 et Windows 10 inscrits en tant qu’appareils : toutes les 8 heures.

Si l’appareil vient d’être inscrit, la fréquence d’enregistrement est plus fréquente :

- iOS et macOS : toutes les 15 minutes pendant 6 heures, puis toutes les 6 heures.
- Android : toutes les 3 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis toutes les 8 heures.
- Windows Phone : toutes les 5 minutes pendant 15 minutes, puis toutes les 15 minutes pendant 2 heures, puis toutes les 8 heures.
- PC Windows inscrits en tant qu’appareils : toutes les 3 minutes pendant 30 minutes, puis toutes les 8 heures.

Les utilisateurs peuvent également ouvrir l’application Portail d’entreprise et synchroniser l’appareil pour qu’il recherche immédiatement les stratégies à tout moment.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quelles sont les actions qui déclenchent l’envoi immédiat d’une notification par Intune ?
Les appareils s’enregistrent auprès d’Intune quand ils reçoivent une notification leur demandant de s’enregistrer ou lors de leur enregistrement régulièrement planifié.  Quand vous ciblez un appareil ou un utilisateur spécifiquement avec une action de type réinitialisation, verrouillage, réinitialisation de code secret, attribution d’application, attribution de profil (Wi-Fi, VPN, messagerie, etc.) ou attribution de stratégie, Intune essaie immédiatement d’indiquer à l’appareil qu’il doit s’enregistrer auprès du service Intune pour recevoir ces mises à jour.

D’autres modifications, comme la modification des coordonnées dans le portail d’entreprise, ne déclenchent pas l’envoi immédiat d’une notification aux appareils.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>Si plusieurs stratégies sont affectées au même utilisateur ou appareil, quels sont les paramètres appliqués ?
Quand plusieurs stratégies sont affectées au même utilisateur ou appareil, l’évaluation du paramètre à appliquer est effectuée au niveau de chaque paramètre :

-   Les paramètres de stratégie de conformité ont toujours la priorité sur les paramètres de stratégie de configuration.

-   En présence de deux stratégies de conformité, c’est le paramètre de la stratégie de conformité la plus restrictive qui est appliqué.

-   Si un paramètre de stratégie de configuration entre en conflit avec un paramètre dans une autre stratégie de configuration, ce conflit apparaît dans la console Intune. Vous devez corriger ces conflits manuellement.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>Que se passe-t-il quand des stratégies de protection d’application entrent en conflit ? Laquelle est appliquée à l’application ?
Les valeurs en conflit sont les paramètres les plus restrictifs disponibles dans une stratégie de protection d’application, à l’exception des champs d’entrée numérique (comme le nombre de tentatives autorisées avant la réinitialisation du code PIN).  Les champs d’entrée numérique sont définis sur les mêmes valeurs que quand vous créez une stratégie de gestion des applications mobiles dans la console en choisissant les paramètres recommandés.

Des conflits se produisent quand deux paramètres de profil sont identiques.  Par exemple, vous avez configuré deux stratégies MAM identiques, à l’exception du paramètre de copier/coller.  Dans ce scénario, le paramètre de copier/coller est défini sur la valeur la plus restrictive, mais le reste des paramètres est appliqué selon leur configuration.

Si un profil est affecté à l’application et entre en vigueur, puis qu’un deuxième profil est affecté, le premier est prioritaire et reste appliqué, tandis que le deuxième s’affiche comme étant en conflit. S’ils sont appliqués en même temps, ce qui signifie qu’il n’existe aucun profil précédent, ils sont alors tous deux en conflit. Tous les paramètres en conflit sont définis sur les valeurs les plus limitées.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Que se passe-t-il quand les stratégies personnalisées iOS entrent en conflit ?
Intune n’évalue pas la charge utile des fichiers de configuration Apple ni le profil OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personnalisé. Son rôle se limite simplement au mécanisme de livraison.

Quand vous affectez un profil personnalisé, vérifiez que les paramètres configurés ne sont pas en conflit avec les stratégies de conformité, de configuration, ou d’autres stratégies personnalisées. Dans le cas d’un profil personnalisé avec des paramètres en conflit, l’ordre dans lequel les paramètres sont appliqués est aléatoire.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Que se passe-t-il quand un profil est supprimé ou n’est plus applicable ?
Quand vous supprimez un profil ou retirez un appareil d’un groupe auquel un profil a été affecté, le profil et les paramètres sont supprimés de cet appareil conformément aux listes suivantes.

### <a name="enrolled-devices"></a>Appareils inscrits

- Profils Wi-Fi, VPN, de certificat et de messagerie : ces profils sont supprimés de tous les appareils inscrits et pris en charge.
- Tous les autres types de profils :
    - **Appareils Windows et Android** : les paramètres ne sont pas supprimés de l’appareil.
    - **Appareils Windows Phone 8.1** : les paramètres suivants sont supprimés :
        - Exiger un mot de passe pour déverrouiller des appareils mobiles
        - Autoriser les mots de passe simples
        - Longueur minimale du mot de passe
        - Type de mot de passe requis
        - Expiration du mot de passe (jours)
        - Mémoriser l'historique des mots de passe
        - Nombre d'échecs de connexion répétée autorisé avant réinitialisation de l'appareil
        - Minutes d'inactivité avant demande du mot de passe
        - Type de mot de passe requis - Nombre minimum de jeux de caractères
        - Autoriser l'appareil photo
        - Exiger le chiffrement sur l'appareil mobile
        - Autoriser le stockage amovible
        - Autoriser le navigateur web
        - Autoriser la boutique d'applications
        - Autoriser la capture d'écran
        - Autoriser la géolocalisation
        - Autoriser le compte Microsoft
        - Autoriser la fonction copier-coller
        - Autoriser la connexion Wi-Fi
        - Autoriser la connexion automatique aux points d'accès Wi-Fi gratuits
        - Autoriser l'indication des points d'accès Wi-Fi
        - Autoriser la réinitialisation aux paramètres d'usine
        - Autoriser Bluetooth
        - Autoriser NFC
        - Autoriser le Wi-Fi

    - **iOS** : tous les paramètres sont supprimés, sauf :
        - Autoriser l'itinérance vocale
        - Autoriser l'itinérance des données
        - Autoriser la synchronisation automatique lors de l'itinérance

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>J’ai modifié un profil de restriction d’appareil, mais les modifications n’ont pas pris effet
Les appareils Windows Phone n’autorisent pas d’assouplir les stratégies de sécurité définies via GPM ou EAS a posteriori. Tel est le cas, par exemple, si vous fixez le **nombre minimal de caractères des mots de passe** à 8, puis que vous essayez de le réduire à 4. Le profil le plus restrictif a déjà été appliqué à l’appareil.

Selon la plateforme d’appareil, si vous voulez attribuer au profil une valeur moins sûre, vous devrez peut-être réinitialiser les stratégies de sécurité.
Par exemple, dans Windows, sur le Bureau, balayez à partir de la droite pour ouvrir la barre **Icônes**, puis choisissez **Paramètres** &gt; **Panneau de configuration**.  Sélectionnez l’applet **Comptes d’utilisateurs**.
Au bas du menu de navigation gauche figure le lien **Réinitialiser les stratégies de sécurité**. Choisissez-le, puis choisissez le bouton **Réinitialiser les stratégies**.
Pour pouvoir appliquer un profil moins restrictif, vous devrez peut-être retirer les autres appareils de gestion des appareils mobiles (par exemple Android, Windows Phone 8.1 et versions ultérieures, et iOS), puis les réinscrire dans le service.

<!--- ## Status codes for MDM managed Windows devices

|Status code|Error message|What to do|
|---------------|-----------------|--------------|
|10 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Installation in progress||
|20 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|Waiting for content||
|30 (APP_CI_ENFORCEMENT_ERROR_RETRIEVING_CONTENT)|Retrieving content|Probable Cause: Job status 30 indicates that a user download of an app failed.<br /><br />Likely causes for this may be:<br /><br />The device lost Internet connectivity while the download was in progress.<br /><br />The certificate issued to the device at the time of enrollment may have expired.<br /><br />Mitigation:<br /><br />Launch the Company Apps app from Control Panel on the device to confirm that the device certificate hasn’t expired; if it has then you will need to re-enroll the device.<br /><br />Confirm that the device is connected to the Internet and try to request the app again.|
|40 (APP_CI_ENFORCEMENT_IN_PROGRESS_CONTENT_DOWNLOADED)|Content download complete||
|50 (APP_CI_ENFORCEMENT_IN_PROGRESS_INSTALLING)|Installation in progress||
|60 (APP_CI_ENFORCEMENT_ERROR_INSTALLING)|Installation Error occurred|The app installation failed after download.<br /><br />The code signing certificate with which app was signed is not present on the device.<br /><br />A framework dependency on which the application depends is not found installed on the device.<br /><br />Ensure that the code signing certificate with which your app was signed is present on the device and confirm with the admin that such a certificate was targeted for all enterprise enrolled Windows RT devices.<br /><br />In case the installation failure is due to a missing framework dependency, the admin will have to re-publish the application again packaging the framework along with the application package.<br /><br />The application package downloaded isn’t a valid package, may have been corrupted, or may not be compatible with the OS version on the device.|
|70 (APP_CI_ENFORCEMENT_SUCCEEDED)|Installation Success||
|80 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Uninstall in progress||
|90 (APP_CI_ENFORCEMENT_ERROR)|Uninstall Error occurred||
|100 (APP_CI_ENFORCEMENT_SUCCEEDED)|Uninstall Success||
|110 (APP_CI_ENFORCEMENT_ERROR)|Content hash mismatch||
|120 (APP_CI_ENFORCEMENT_ERROR)|SLK / side loading not enabled||
|130 (APP_CI_ENFORCEMENT_ERROR)|MSADP license install failed||
|No status (APP_CI_ENFORCEMENT_UNKNOWN)|n/a|The status is currently unknown.|

## Company resource access (common errors)

|Status code|Hexadecimal error code|Error message|
|---------------|--------------------------|-----------------|
|-2016281101|0x87D1FDF3|MDM CRP request not found|
|-2016281102|0x87D1FDF2|NDES URL not found|
|-2016281103|0x87D1FDF1|MDM CRP certificate info not found|
|-2016281104|0x87D1FDF0|MDM CI certificate info not found|
|-2016281105|0x87D1FDEF|Failed to evaluate the Rule|
|-2016281106|0x87D1FDEE|Not applicable because it lost in conflict resolution|
|-2016281107|0x87D1FDED|Unsupported setting discovery source|
|-2016281108|0x87D1FDEC|Referenced setting not found in CI|
|-2016281109|0x87D1FDEB|Data type conversion failed|
|-2016281110|0x87D1FDEA|Invalid parameter to CIM setting|
|-2016281111|0x87D1FDE9|Not applicable for this device|
|-2016281112|0x87D1FDE8|Remediation failed|
|-2016330905|0x87D13B67|The app state is unknown|
|-2016330906|0x87D13B66|The app is managed, but has been removed by the user|
|-2016330907|0x87D13B65|The device is redeeming the redemption code|
|-2016330908|0x87D13B64|The app install has failed|
|-2016330909|0x87D13B63|The user rejected the offer to update the app|
|-2016330910|0x87D13B62|The user rejected the offer to install the app|
|-2016330911|0x87D13B61|The user has installed the app before managed app installation could take place|
|-2016330912|0x87D13B60|The app is scheduled for installation, but needs a redemption code to complete the transaction|
|-2016341109|0x87D1138B|iOS device has returned an error|
|-2016341110|0x87D1138A|iOS device has rejected the command due to incorrect format|
|-2016341111|0x87D11389|iOS device has returned an unexpected Idle status|
|-2016341112|0x87D11388|iOS device is currently busy|

## Errors returned by iOS devices

|Status code|Hexadecimal error code|Error message|
|---------------|--------------------------|-----------------|
|-2016299111|0x87D1B799|Internal error|
|-2016299112|0x87D1B798|Internal error|
|-2016300111|0x87D1B3B1|36001:(internal error)|
|-2016300112|0x87D1B3B0|36000:Cellular already configured|
|-2016301110|0x87D1AFCA|35002:Multiple fonts in a single payload|
|-2016301111|0x87D1AFC9|35001:Failed font installation|
|-2016301112|0x87D1AFC8|35000:Invalid font data|
|-2016302109|0x87D1ABE3|34003:Kerberos principal name invalid|
|-2016302110|0x87D1ABE2|34002:Kerberos principal name missing|
|-2016302111|0x87D1ABE1|34001:Invalid URL match pattern|
|-2016302112|0x87D1ABE0|34000:Invalid app identifier match pattern|
|-2016304112|0x87D1A410|32000:Too many apps|
|-2016305111|0x87D1A029|31001:Cannot apply settings|
|-2016305112|0x87D1A028|31000:Cannot apply credential|
|-2016306111|0x87D19C41|30001:Timed out|
|-2016306112|0x87D19C40|30000:Authentication failed|
|-2016307109|0x87D1985B|29003:Bad certificate data|
|-2016307110|0x87D1985A|29002:|
|-2016307111|0x87D19859|29001:|
|-2016307112|0x87D19858|29000:Device not supervised|
|-2016308110|0x87D19472|28002:Cannot set wallpaper|
|-2016308111|0x87D19471|28001:Bad wallpaper image|
|-2016308112|0x87D19470|28000:Unknown item|
|-2016310111|0x87D18CA1|26001:File level encryption unsupported|
|-2016310112|0x87D18CA0|26000:Block level encryption unsupported|
|-2016311110|0x87D188BA|25002:Cannot remove|
|-2016311111|0x87D188B9|25001:Cannot install|
|-2016311112|0x87D188B8|25000:Bad profile|
|-2016312109|0x87D184D3|24003:Bad final profile|
|-2016312110|0x87D184D2|24002:Bad identity payload|
|-2016312111|0x87D184D1|24001:Cannot sign attribute dictionary|
|-2016312112|0x87D184D0|24000:Cannot create attribute dictionary|
|-2016313110|0x87D180EA|23002:Invalid server certificate|
|-2016313111|0x87D180E9|23001:Bad server response|
|-2016313112|0x87D180E8|23000:Bad identity|
|-2016314099|0x87D17D0D|22013:Invalid PKIOperation response|
|-2016314100|0x87D17D0C|22012:Cannot store CACertificate|
|-2016314101|0x87D17D0B|22011:Cannot generate CSR|
|-2016314102|0x87D17D0A|22010:Cannot store temporary identity|
|-2016314103|0x87D17D09|22009:Cannot create temporary identity|
|-2016314104|0x87D17D08|22008:Cannot create identity|
|-2016314105|0x87D17D07|22007:Invalid signed certificate|
|-2016314106|0x87D17D06|22006:Insufficient CACaps|
|-2016314107|0x87D17D05|22005:Network error|
|-2016314108|0x87D17D04|22004:Unsupported certificate configuration|
|-2016314109|0x87D17D03|22003:Invalid RAResponse|
|-2016314110|0x87D17D02|22002:Invalid CAResponse|
|-2016314111|0x87D17D01|22001:Cannot generate key pair|
|-2016314112|0x87D17D00|22000:Invalid key usage|
|-2016315105|0x87D1791F|21007:Cannot verify account|
|-2016315106|0x87D1791E|21006:Cannot decrypt certificate|
|-2016315107|0x87D1791D|21005:Account not unique (Email Profile already exists on device)|
|-2016315108|0x87D1791C|21004:Cannot create account|
|-2016315109|0x87D1791B|21003:No host name|
|-2016315110|0x87D1791A|21002:Cannot comply with encryption policy from server|
|-2016315111|0x87D17919|21001:Cannot comply with policy from server|
|-2016315112|0x87D17918|21000:Cannot get policy from server|
|-2016316110|0x87D17532|20002:Account not unique|
|-2016316111|0x87D17531|20001:No host name|
|-2016316112|0x87D17530|20000:Cannot create account|
|-2016317110|0x87D1714A|19002:Account not unique|
|-2016317111|0x87D17149|19001:No host name|
|-2016317112|0x87D17148|19000:Cannot create account|
|-2016318110|0x87D16D62|18002:Invalid credentials|
|-2016318111|0x87D16D61|18001:Host unreachable|
|-2016318112|0x87D16D60|18000:Unknown error|
|-2016319110|0x87D1697A|17002:Account not unique|
|-2016319111|0x87D16979|17001:No host name|
|-2016319112|0x87D16978|17000:Cannot create account|
|-2016320110|0x87D16592|16002:Account not unique|
|-2016320111|0x87D16591|16001:No host name|
|-2016320112|0x87D16590|16000:Cannot create subscription|
|-2016321109|0x87D161AB|15003:Invalid certificate|
|-2016321110|0x87D161AA|15002:Cannot lock network configuration|
|-2016321111|0x87D161A9|15001:Cannot remove VPN|
|-2016321112|0x87D161A8|15000:Cannot install VPN|
|-2016322110|0x87D15DC2|14002:Cloud configuration already exists|
|-2016322111|0x87D15DC1|14001:Device locked|
|-2016322112|0x87D15DC0|14000:Invalid field|
|-2016323107|0x87D159DD|13005:Cannot set up proxy|
|-2016323108|0x87D159DC|13004:Cannot set up EAP|
|-2016323109|0x87D159DB|13003:Cannot create WiFi configuration|
|-2016323110|0x87D159DA|13002:Password required|
|-2016323111|0x87D159D9|13001:Username required|
|-2016323112|0x87D159D8|13000:Cannot install|
|-2016324070|0x87D1561A|12042:Unknown locale code|
|-2016324071|0x87D15619|12041:Unknown language code|
|-2016324072|0x87D15618|12040:iTunes store login required|
|-2016324073|0x87D15617|12039:(unused)|
|-2016324074|0x87D15616|12038:App not managed|
|-2016324075|0x87D15615|12037:Invalid redemption code|
|-2016324076|0x87D15614|12036:Cannot remove app in current state|
|-2016324077|0x87D15613|12035:App cannot be purchased|
|-2016324078|0x87D15612|12034:URL is not HTTPS|
|-2016324079|0x87D15611|12033:Invalid manifest|
|-2016324080|0x87D15610|12032:Too many apps in manifest|
|-2016324081|0x87D1560F|12031:App installation disabled|
|-2016324082|0x87D1560E|12030:Invalid URL|
|-2016324083|0x87D1560D|12029:App not managed|
|-2016324084|0x87D1560C|12028:Not waiting for redemption|
|-2016324085|0x87D1560B|12027:Not an app|
|-2016324086|0x87D1560A|12026:App already queued|
|-2016324087|0x87D15609|12025:App already installed|
|-2016324088|0x87D15608|12024:Could not validate app manifest|
|-2016324089|0x87D15607|12023:Could not validate app iD|
|-2016324090|0x87D15606|12022:Invalid topic|
|-2016324091|0x87D15605|12021:Invalid request type|
|-2016324092|0x87D15604|12020:Unauthorized by server|
|-2016324093|0x87D15603|12019:Cannot copy escrow secret|
|-2016324094|0x87D15602|12018:Cannot copy escrow keybag data|
|-2016324095|0x87D15601|12017:Cannot create escrow keybag|
|-2016324096|0x87D15600|12016:Missing identity|
|-2016324097|0x87D155FF|12015:Cannot get push token|
|-2016324098|0x87D155FE|12014:Provisioning profile not managed|
|-2016324099|0x87D155FD|12013:Profile not managed|
|-2016324100|0x87D155FC|12012:MDM replacement mismatch|
|-2016324101|0x87D155FB|12011:Invalid MDM configuration|
|-2016324102|0x87D155FA|12010:Internal inconsistency error|
|-2016324103|0x87D155F9|12009:Invalid replacement profile|
|-2016324104|0x87D155F8|12008:Malformed request|
|-2016324105|0x87D155F7|12007:Not authorized|
|-2016324106|0x87D155F6|12006:Redirect refused|
|-2016324107|0x87D155F5|12005:Cannot find certificate|
|-2016324108|0x87D155F4|12004:Invalid push certificate|
|-2016324109|0x87D155F3|12003:Invalid challenge response|
|-2016324110|0x87D155F2|12002:Cannot check in|
|-2016324111|0x87D155F1|12001:Multiple MDM instances|
|-2016324112|0x87D155F0|12000:Invalid access rights|
|-2016325111|0x87D15209|11001:Custom APN already installed|
|-2016325112|0x87D15208|11000:Cannot install APN|
|-2016326111|0x87D14E21|10001:Invalid signer|
|-2016326112|0x87D14E20|10000:Cannot install defaults|
|-2016327106|0x87D14A3E|9006:Certificate is not an identity|
|-2016327107|0x87D14A3D|9005:Certificate is malformed|
|-2016327108|0x87D14A3C|9004:Cannot store root certificate|
|-2016327109|0x87D14A3B|9003:Cannot store WAPI data|
|-2016327110|0x87D14A3A|9002:Cannot store certificate|
|-2016327111|0x87D14A39|9001:Too many certificates in a payload|
|-2016327112|0x87D14A38|9000:Invalid password|
|-2016328112|0x87D14650|8000:Cannot install Web Clip|
|-2016329105|0x87D1426F|7007:SMTP account is misconfigured|
|-2016329106|0x87D1426E|7006:POP account is misconfigured|
|-2016329107|0x87D1426D|7005:IMAP account is misconfigured|
|-2016329108|0x87D1426C|7004:SMIME certificate is bad|
|-2016329109|0x87D1426B|7003:SMIME certificate not found|
|-2016329110|0x87D1426A|7002:Unknown error occurred during validation|
|-2016329111|0x87D14269|7001:Invalid credentials|
|-2016329112|0x87D14268|7000:Host unreachable|
|-2016330110|0x87D13E82|6002:Cannot create query|
|-2016330111|0x87D13E81|6001:Empty string|
|-2016330112|0x87D13E80|6000:Keychain system error|
|-2016331097|0x87D13AA7|5015:Cannot set grace period|
|-2016331098|0x87D13AA6|5014:Cannot set passcode|
|-2016331099|0x87D13AA5|5013:Cannot clear passcode|
|-2016331100|0x87D13AA4|5012:(unused)|
|-2016331101||5011:Wrong passcode|
|-2016331102||5010:Device locked|
|-2016331103|0x87D13AA4|5009:(unused)|
|-2016331104|0x87D13AA0|5008:Passcode too recent|
|-2016331105|0x87D13A9F|5007:Passcode expired|
|-2016331106|0x87D13AA3|5006:Passcode requires alpha characters|
|-2016331107|0x87D13A9D|5005:Passcode requires number|
|-2016331108|0x87D13A9C|5004:Passcode has ascending descending characters|
|2016331109|0x87D13A9B|5003:Passcode has repeating characters|
|-2016331110|0x87D13A9A|5002:Too few complex characters|
|-2016331111|0x87D13A99|5001:Too few unique characters|
|-2016331112|0x87D13A98|5000:Passcode too short|
|-2016332093|0x87D136C3|4019:Multiple App Lock payloads|
|-2016332094|0x87D136C2|4018:Multiple APN or Cellular payloads|
|-2016332095|0x87D136C1|4017:Multiple global HTTPProxy payloads|
|-2016332096|0x87D136C0|4016:(Internal error)|
|-2016332097|0x87D136BF|4015:Replacement profile does not contain an MDM payload|
|-2016332098|0x87D136BE|4014:No device identity available|
|-2016332099|0x87D136BD|4013:Update failed|
|-2016332100|0x87D136BC|4012:Profile is not updatable|
|-2016332101|0x87D136BB|4011:Final profile is not a configuration profile|
|-2016332102|0x87D136BA|4010:Updated profile does not have the same identifier|
|-2016332103|0x87D136B9|4009:Device locked|
|-2016332104|0x87D136B8|4008:Mismatched certificates|
|-2016332105|0x87D136B7|4007:Unrecognized file format|
|-2016332106|0x87D136B6|4006:Profile removal date is in the past|
|-2016332107|0x87D136B5|4005:Passcode does not comply|
|-2016332108|0x87D136B4|4004:User cancelled installation|
|-2016332109|0x87D136B3|4003:Profile not queued for installation|
|-2016332110|0x87D136B2|4002:Duplicate UUID|
|-2016332111|0x87D136B1|4001:Installation failure|
|-2016332112|0x87D136B0|4000:Cannot parse profile|
|2016333111|0x87D132C9|3001:Inconsistent value comparison sense (internal error)|
|-2016333112|0x87D132C8|3000:Inconsistent restriction sense (internal error)|
|-2016334108|0x87D12EE4|2004:Unsupported field value|
|-2016334109|0x87D12EE3|2003:Bad data type in field|
|-2016334110|0x87D12EE2|2002:Missing required field|
|-2016334111|0x87D12EE1|2001:Unsupported payload version|
|-2016334112|0x87D12EE0|2000:Malformed Payload|
|-2016335102|0x87D12B02|1010:Unsupported field value|
|-2016335103|0x87D12B01|1009:Profile installation failure|
|-2016335104|0x87D12B00|1008:Non-unique payload identifiers|
|-2016335105|0x87D12AFF|1007:Non-unique UUIDs|
|-2016335106|0x87D12AFE|1006:Cannot decrypt|
|-2016335107|0x87D12AFD|1005:Empty profile|
|-2016335108|0x87D12AFC|1004:Bad signature|
|-2016335109|0x87D12AFB|1003:Bad data type in field|
|-2016335110|0x87D12AFA|1002:Missing required field|
|-2016335111|0x87D12AF9|1001:Unsupported profile version|
|-2016335112|0x87D12AF8|1000:Malformed profile|

## OMA response codes

|Status code|Hexadecimal error code|Error message|
|---------------|--------------------------|-----------------|
|-2016344008|0x87D10838|(1404): Certificate access denied|
|2016344009|0x87D10837|(1403): Certificate not found|
|-2016344010|0x87D10836|DCMO(1402): The Operation failed|
|-2016344011|0x87D10835|DCMO(1401): User chose not to accept the operation when prompted|
|-2016344012|0x87D10834|DCMO(1400): Client error|
|-2016344108|0x87D107D4|DCMO(1204): Device Capability is disabled and User is allowed to re-enable it|
|-2016344109|0x87D107D3|DCMO(1203): Device Capability is disabled and User is not allowed to re-enable it|
|-2016344110|0x87D107D2|DCMO(1202): Enable operation is performed successfully but the Device Capability is currently detached|
|-2016344111|0xF3FB4D95|DCMO(1201): Enable operation is performed successfully and the Device Capability is currently attached|
|-2016344112|0x87D107D0|DCMO(1200): Operation is performed successfully|
|2016345595|0x87D10205|Syncml(517): The response to an atomic command was too large to fit in a single message.|
|-2016345596|0x87D10204|Syncml(516): Command was inside Atomic element and Atomic failed. This command was not rolled back successfully.|
|-2016345598|0x87D10202|Syncml(514): The SyncML command was not completed successfully, since the operation was already cancelled before processing the command.|
|-2016345599|0x87D10201|Syncml(513): The recipient does not support or refuses to support the specified version of the SyncML Synchronization Protocol used in the request SyncML Message.|
|-2016345600|0x87D10200|Syncml(512): An application error occurred during the synchronization session.|
|-2016345601|0x87D101FF|Syncml(511): A severe error occurred in the server while processing the request.|
|-2016345602|0x87D101FE|Syncml(510): An error occurred while processing the request. The error is related to a failure in the recipient data store.|
|-2016345603|0x87D101FD|Syncml(509): Reserved for future use.|
|2016345604|0x87D101FC|Syncml(508): An error occurred that necessitates a refresh of the current synchronization state of the client with the server.|
|-2016345605|0x87D101FB|Syncml(507): The error caused all SyncML commands within an Atomic element type to fail.|
|-2016345606|0x87D101FA|Syncml(506): An application error occurred while processing the request.|
|-2016345607|0x87D101F9|Syncml(505): The recipient does not support or refuses to support the specified version of SyncML DTD used in the request SyncML Message.|
|-2016345608|=0x87D101F8|Syncml(504): The recipient, while acting as a gateway or proxy, did not receive a timely response from the upstream recipient specified by the URI (e.g. HTTP, FTP, LDAP) or some other auxiliary recipient (e.g. DNS) it needed to access in attempting to complete the request.|
|-2016345609|0x87D101F7|Syncml(503): The recipient is currently unable to handle the request due to a temporary overloading or maintenance of the recipient.|
|-2016345610|0x87D101F6|Syncml(502): The recipient, while acting as a gateway or proxy, received an invalid response from the upstream recipient it accessed in attempting to fulfill the request.|
|-2016345611|0x87D101F5|Syncml(501): The recipient does not support the command required to fulfill the request.|
|-2016345612|0x87D101F4|Syncml(500): The recipient encountered an unexpected condition which prevented it from fulfilling the request|
|2016345684|0x87D101AC|Syncml(428): Move failed|
|-2016345685|0x87D101AB|Syncml(427): Parent cannot be deleted since it contains children.|
|-2016345686|0x87D101AA|Syncml(426): Partial item not accepted.|
|-2016345687|0x87D101A9|Syncml(425): The requested command failed because the sender does not have adequate access control permissions (ACL) on the recipient.|
|-2016345688|0x87D101A8|Syncml(424): The chunked object was received, but the size of the received object did not match the size declared within the first chunk.|
|-2016345689|0x87D101A7|Syncml(423): The requested command failed because the "Soft Deleted" item was previously "Hard Deleted" on the server.|
|-2016345690|0x87D101A6|Syncml(422): The requested command failed on the server because the CGI scripting in the LocURI was incorrectly formed.|
|-2016345691|0x87D101A5|Syncml(421): The requested command failed on the server because the specified search grammar was not known.|
|-2016345692|0x87D101A4|Syncml(420): The recipient has no more storage space for the remaining synchronization data.|
|-2016345693|0x87D101A3|Syncml(419): The client request created a conflict which was resolved by the server command winning.|
|-2016345694|0x87D101A2|Syncml(418): The requested Put or Add command failed because the target already exists.|
|2016345695|0x87D101A1|Syncml(417): The request failed at this time and the originator should retry the request later.|
|-2016345696|0x87D101A0|Syncml(416): The request failed because the specified byte size in the request was too big.|
|-2016345697|0x87D1019F|Syncml(415): Unsupported media type or format.|
|-2016345698|0x87D1019E|Syncml(414): The requested command failed because the target URI is too long for what the recipient is able or willing to process.|
|-2016345699|0x87D1019D|Syncml(413): The recipient is refusing to perform the requested command because the requested item is larger than the recipient is able or willing to process.|
|-2016345700|0x87D1019C|Syncml(412): The requested command failed on the recipient because it was incomplete or incorrectly formed.|
|-2016345701|0x87D1019B|Syncml(411): The requested command must be accompanied by byte size or length information in the Meta element type.|
|-2016345702|0x87D1019A|Syncml(410): The requested target is no longer on the recipient and no forwarding URI is known.|
|-2016345703|0x87D10199|Syncml(409): The requested failed because of an update conflict between the client and server versions of the data.|
|-2016345704|0x87D10198|Syncml(408): An expected message was not received within the required period of time.|
|-2016345705|0x87D10197|Syncml(407): The requested command failed because the originator must provide proper authentication.|
|-2016345706|0x87D10196|Syncml(406): The requested command failed because an optional feature in the request was not supported.|
|-2016345707|0x87D10195|Syncml(405): The requested command is not allowed on the target.|
|-2016345708|0x87D10194|Syncml(404): The requested target was not found.|
|-2016345709|0x87D10193|Syncml(403): The requested command failed, but the recipient understood the requested command.|
|-2016345710|0x87D10192|Syncml(402): The requested command failed because proper payment is needed.|
|-2016345711|0x87D10191|Syncml(401): The requested command failed because the requestor must provide proper authentication.|
|-2016345712|0x87D10190|Syncml(400): The requested command could not be performed because of malformed syntax in the command.|
|-2016345807|0x87D10131|Syncml(305): The requested target must be accessed through the specified proxy URI.|
|-2016345808|0x87D10130|Syncml(304):The requested SyncML command was not executed on the target.|
|-2016345809|0x87D1012F|Syncml(303): The requested target can be found at another URI.|
|-2016345810|0x87D1012E|Syncml(302): The requested target has temporarily moved to a different URI.|
|-2016345811|0x87D1012D|Syncml(301): The requested target has a new URI.|
|-2016345812|0x87D1012C|Syncml(300): The requested target is one of a number of multiple alternatives requested target.|
|-2016345896|0x87D100D8|Syncml(216): A command was inside Atomic element and Atomic failed. This command was rolled back successfully.|
|-2016345897|0x87D100D7|Syncml(215): A command was not executed, as a result of user interaction and user chose not to accept the choice.|
|-2016345898|0x87D100D6|Syncml(214): Operation cancelled. The SyncML command completed successfully, but no more commands will be processed within the session.|
|-2016345899|0x87D100D5|Syncml(213): Chunked item accepted and buffered|
|-2016345900|0x87D100D4|Syncml(212): Authentication accepted. No further authentication is needed for the remainder of the synchronization session. This response code can only be used in response to a request in which the credentials were provided.|
|-2016345901|0x87D100D3|Syncml(211): Item not deleted. The requested item was not found. It could have been previously deleted.|
|-2016345902|0x87D100D2|Syncml(210): Delete without archive. The response indicates that the requested data was successfully deleted, but that it was not archived prior to deletion because this OPTIONAL feature was not supported by the implementation.|
|-2016345903|0x87D100D1|Conflict resolved with duplicate. The response indicates that the request created an update conflict; which was resolved with a duplication of the client's data being created in the server database. The response includes both the target URI of the duplicate in the Item of the Status. In addition, in the case of a two-way synchronization, an Add command is returned with the duplicate data definition.|
|-2016345904|0x87D100D0|Conflict resolved with client's command "winning". The response indicates that there was an update conflict; which was resolved by the client command winning.|
|-2016345905|0x87D100CF|Conflict resolved with merge. The response indicates that the request created a conflict; which was resolved with a merge of the client and server instances of the data. The response includes both the Target and Source URLs in the Item of the Status. In addition, a Replace command is returned with the merged data.|
|-2016345906|0x87D100CE|The response indicates that only part of the command was completed. If the remainder of the command can be completed later, then when completed another appropriate completion request status code SHOULD be created.|
|-2016345907|0x87D100CD|The source SHOULD update their content. The originator of the request is being told that their content SHOULD be synchronized to get an up to date version.|
|-2016345908|0x87D100CC|The request was successfully completed but no data is being returned. The response code is also returned in response to a Get when the target has no content.|
|-2016345909|0x87D100CB|Non-authoritative response. The request is being responded to by an entity other than the one targeted. The response is only to be returned when the request would have been resulted in a 200 response code from the authoritative target.|
|-2016345910|0x87D100CA|Accepted for processing. The request to either run a remote execution of an application or to alert a user or application was successfully performed.|
|-2016345911|0x87D100C9|The requested item was added.|
|-2016345912|0x87D100C8|The SyncML command completed successfully.|
|-2016346011|0x87D10065|The specified SyncML command is being carried out, but has not yet completed.| 
--->

### <a name="next-steps"></a>Étapes suivantes
Si ces informations de dépannage n’ont pas permis de vous aider, contactez le support Microsoft comme décrit dans [Comment obtenir un support technique pour Microsoft Intune](get-support.md).