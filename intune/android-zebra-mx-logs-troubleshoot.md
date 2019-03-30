---
title: Utilisez StageNow ouvre une session sur les appareils Android Zebra dans Microsoft Intune - Azure | Microsoft Docs
description: Consultez les problèmes et résolutions courants lors de l’utilisation de StageNow sur les appareils Android avec Microsoft Intune. Apprenez également à obtenir des journaux et voir des exemples montrant comment lire les journaux pour la réussite ou d’erreurs.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490539"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Résoudre les problèmes et de voir les problèmes potentiels sur les appareils Android Zebra dans Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Dans Microsoft Intune, vous pouvez utiliser [Zebra mobilité Extensions (MX) pour gérer les appareils Android Zebra](android-zebra-mx-overview.md). Lorsque vous utilisez des appareils Zebra, vous créez des profils dans StageNow pour gérer les paramètres et les téléchargez dans Intune. Intune utilise l’application StageNow pour appliquer les paramètres sur les appareils. L’application StageNow crée également un fichier journal détaillé sur l’appareil qui est utilisé pour résoudre les problèmes.

Cette fonctionnalité s’applique à :

- Android

Par exemple, vous créez un profil dans StageNow pour configurer un appareil. Lorsque vous créez le profil StageNow, la dernière étape génère un fichier pour vous testez le profil. Vous consommez ce fichier avec l’application StageNow sur l’appareil.

Dans un autre exemple, vous créez un profil dans StageNow et testez. Dans Intune, vous ajoutez le profil StageNow et attribuez-les à vos appareils Zebra. Lors de la vérification de l’état du profil affecté, le profil affiche un état de haut niveau.

Dans ces deux cas, vous pouvez obtenir plus d’informations à partir du fichier journal StageNow, qui est enregistré sur l’appareil chaque fois qu’un profil StageNow s’applique.

Certains problèmes ne sont pas liées au contenu du profil StageNow et ne sont pas répercutées dans les journaux.

Cet article vous montre comment lire les journaux StageNow et répertorie d’autres problèmes potentiels avec les appareils Zebra qui risquent de ne pas être reflétées dans les journaux.

[Utiliser et gérer des appareils avec des Extensions de mobilité Zebra Zebra](android-zebra-mx-overview.md) a plus d’informations sur cette fonctionnalité.

## <a name="get-the-logs"></a>Obtenir les journaux

### <a name="use-the-stagenow-app-on-the-device"></a>Utilisez l’application de StageNow sur l’appareil
Lorsque vous testez un profil directement à l’aide de StageNow sur votre ordinateur, au lieu d’utiliser [Intune pour déployer le profil](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), l’application StageNow sur l’appareil enregistre les journaux à partir du test. Pour obtenir le fichier journal, utilisez le **plus (...)**  option dans l’application StageNow sur l’appareil.

### <a name="get-logs-using-android-debug-bridge"></a>Obtenir les journaux à l’aide de Android Debug Bridge
Pour obtenir les journaux une fois que le profil est déjà déployé avec Intune, connectez l’appareil à un ordinateur avec [Android Debug Bridge (adb)](https://developer.android.com/studio/command-line/adb) (ouvre le site web de d’Android).

Sur l’appareil, les journaux sont enregistrés dans `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Obtenir les journaux d’e-mail
Pour obtenir les journaux une fois que le profil est déjà déployé avec Intune, les utilisateurs finaux pouvez envoyer les journaux à l’aide d’une application de messagerie sur l’appareil. Sur l’appareil Zebra, ouvrez l’application portail d’entreprise, et [envoyer les journaux](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). À l’aide de la fonctionnalité de journaux d’envoi crée également un PowerLift incident ID, que vous pouvez référencer si contacter le support Microsoft.

## <a name="read-the-logs"></a>Lire les journaux

Lorsque vous examinez les journaux, il existe une erreur chaque fois que vous voyez le `<characteristic-error>` balise. Détails de l’erreur sont écrits dans le `<parm-error>` balise > `desc` propriété.

## <a name="error-types"></a>Types d’erreurs

Les appareils Zebra incluent erreur différents niveaux de création de rapports :

- Le CSP n’est pas pris en charge sur l’appareil. Par exemple, l’appareil n’est pas un appareil cellulaire et n’a pas un gestionnaire de téléphonie mobile.
- La version MX ou OSX est incompatible. Chaque fournisseur de services cryptographiques est créée. Pour une matrice de prise en charge complète, consultez [documentation de Zebra](http://techdocs.zebra.com/mx/) (ouvre le site web de Zebra).
- L’appareil signale un autre problème ou erreur.

## <a name="examples"></a>Exemples

Par exemple, vous avez le profil d’entrée suivant :

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

Dans le journal, le code XML est identique à l’entrée. Cette sortie correspondante indique que le profil a été appliqué à l’appareil sans erreurs :

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

Dans un autre exemple, vous avez l’entrée suivante :

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

Le journal affiche une erreur, car il contient un `<characteristic-error>` balise. Dans ce scénario, le profil essayé d’installer un package Android (APK) qui n’existe pas dans le chemin d’accès donné :

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Autres problèmes potentiels avec les appareils Zebra

Cette section répertorie les autres problèmes possibles que peut s’afficher lors de l’utilisation d’appareils de Zebra avec administrateur de l’appareil. Ces problèmes ne sont pas signalés dans les journaux StageNow.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView est obsolète

Lorsque anciens appareils se connectent à l’aide de l’application portail d’entreprise, les utilisateurs peuvent voir un message que le composant System WebView est obsolète et a besoin de mise à niveau. Si l’appareil Google Play installé, vous connecter à internet et la vérification des mises à jour. Si l’appareil n’a pas installé de Google Play, obtenir la version mise à jour du composant et s’appliquent aux appareils. Ou bien, mise à jour de l’appareil plus récente du système d’exploitation émis par Zebra.

### <a name="management-actions-take-a-long-time"></a>Actions de gestion prennent beaucoup de temps

Si Google Play services ne sont pas disponibles, certaines tâches prennent jusqu'à 8 heures. [Application de portail d’entreprise des limitations de Intune pour Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (ouvre un autre site web de Microsoft) peut être une bonne ressource.

### <a name="device-spoofing-suspected-shows-in-intune"></a>« APPAREIL l’usurpation suspectés » s’affiche dans Intune

Cette erreur signifie qu’Intune soupçonne qu'un appareil non - Zebra Android signale son modèle et le fabricant comme appareil Zebra.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Application portail d’entreprise est antérieure à la version minimale requise

Intune peut mettre à jour la version minimale requise de l’application portail d’entreprise. Si Google Play n’est pas installé sur l’appareil, l’application portail d’entreprise ne mis à jour automatiquement. Si la version minimale requise est plus récente que la version installée, l’application portail d’entreprise cesse de fonctionner. Mise à jour de la dernière application portail d’entreprise à l’aide [chargement de version test sur les appareils Zebra](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Étapes suivantes

[Forums de discussion Zebra](https://developer.zebra.com/community/home/discussions) (ouvre le site web de Zebra)

[Utiliser et gérer des appareils Zebra avec des Extensions de mobilité Zebra dans Intune](android-zebra-mx-overview.md)
