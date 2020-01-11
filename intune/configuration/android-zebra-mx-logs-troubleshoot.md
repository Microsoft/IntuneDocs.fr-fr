---
title: Utiliser les journaux StageNow sur les appareils Android rayures dans Microsoft Intune-Azure | Microsoft Docs
description: Consultez les problèmes courants et les solutions lors de l’utilisation de StageNow sur des appareils Android avec Microsoft Intune. Découvrez également comment obtenir des journaux et des exemples de lecture des journaux en cas de réussite ou d’erreurs.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2319fb0d1198289398912793e52482bf66d87173
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206837"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Dépannez et consultez les problèmes potentiels sur les appareils Android rayures dans Microsoft Intune



Dans Microsoft Intune, vous pouvez utiliser [rayures Mobility extensions (MX) pour gérer les appareils Android rayures](android-zebra-mx-overview.md). Lorsque vous utilisez des appareils rayures, vous créez des profils dans StageNow pour gérer les paramètres et les télécharger dans Intune. Intune utilise l’application StageNow pour appliquer les paramètres sur les appareils. L’application StageNow crée également un fichier journal détaillé sur l’appareil utilisé pour la résolution des problèmes.

Cette fonctionnalité s’applique à :

- Android

Par exemple, vous créez un profil dans StageNow pour configurer un appareil. Lorsque vous créez le profil StageNow, la dernière étape génère un fichier pour tester le profil. Vous consommez ce fichier avec l’application StageNow sur l’appareil.

Dans un autre exemple, vous créez un profil dans StageNow et le testez. Dans Intune, vous ajoutez le profil StageNow, puis vous l’affectez à vos appareils rayures. Lors de la vérification de l’état du profil affecté, le profil affiche un état de haut niveau.

Dans ces deux cas, vous pouvez obtenir plus de détails à partir du fichier journal StageNow, qui est enregistré sur l’appareil chaque fois qu’un profil StageNow s’applique.

Certains problèmes ne sont pas liés au contenu du profil StageNow et ne sont pas reflétés dans les journaux.

Cet article explique comment lire les journaux StageNow et répertorie d’autres problèmes potentiels liés aux appareils rayures qui peuvent ne pas être reflétés dans les journaux.

[Utilisez et gérez les appareils rayures avec rayures Mobility extensions](android-zebra-mx-overview.md) pour plus d’informations sur cette fonctionnalité.

## <a name="get-the-logs"></a>Récupérer les journaux

### <a name="use-the-stagenow-app-on-the-device"></a>Utiliser l’application StageNow sur l’appareil
Lorsque vous testez un profil directement à l’aide de StageNow sur votre ordinateur dans, au lieu d’utiliser [Intune pour déployer le profil](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), l’application StageNow sur l’appareil enregistre les journaux à partir du test. Pour obtenir le fichier journal, utilisez l’option **plus (...)** dans l’application StageNow sur l’appareil.

### <a name="get-logs-using-android-debug-bridge"></a>Récupération des journaux à l’aide de Android Debug Bridge
Pour obtenir des journaux une fois que le profil est déjà déployé avec Intune, connectez l’appareil à un ordinateur avec [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) (ouvre le site Web d’Android).

Sur l’appareil, les journaux sont enregistrés dans `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Récupérer les journaux à partir de la messagerie
Pour recevoir les journaux après le déploiement du profil avec Intune, les utilisateurs finaux peuvent envoyer un message électronique aux journaux à l’aide d’une application de messagerie sur l’appareil. Sur l’appareil rayures, ouvrez l’application Portail d’entreprise et [envoyez les journaux](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). L’utilisation de la fonctionnalité journaux d’envoi crée également un ID d’incident PowerLift, que vous pouvez référencer si vous contactez le support Microsoft.

## <a name="read-the-logs"></a>Lire les journaux

Lorsque vous examinez les journaux, il y a une erreur à chaque fois que vous voyez la balise `<characteristic-error>`. Les détails de l’erreur sont écrits dans la balise `<parm-error>` > propriété `desc`.

## <a name="error-types"></a>Types d'erreurs

Les appareils rayures incluent différents niveaux de signalement d’erreurs :

- Le CSP n’est pas pris en charge sur l’appareil. Par exemple, l’appareil n’est pas un appareil mobile et n’a pas de Mobile Manager.
- La version de MX ou OSX est incompatible. Chaque CSP est associé à une version. Pour obtenir une matrice de prise en charge complète, consultez la [documentation de rayures](http://techdocs.zebra.com/mx/) (pour ouvrir le site Web de rayures).
- L’appareil signale un autre problème ou une autre erreur.

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

Dans le journal, le XML est identique à l’entrée. Cette sortie de correspondance signifie que le profil a été appliqué avec succès à l’appareil sans erreur :

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

Dans un autre exemple, vous disposez de l’entrée suivante :

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

Le journal affiche une erreur, car il contient une balise `<characteristic-error>`. Dans ce scénario, le profil a essayé d’installer un package Android (APK) qui n’existe pas dans le chemin d’accès donné :

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

## <a name="other-potential-issues-with-zebra-devices"></a>Autres problèmes potentiels avec les appareils rayures

Cette section répertorie les autres problèmes que vous pouvez être amené à observer lors de l’utilisation d’appareils rayures avec l’administrateur de l’appareil. Ces problèmes ne sont pas signalés dans les journaux StageNow.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView est obsolète

Lorsque des appareils plus anciens se connectent à l’aide de l’application Portail d’entreprise, les utilisateurs peuvent voir un message indiquant que le composant de WebView du système est obsolète et qu’il a besoin d’une mise à niveau. Si l’appareil n’a Google Play installé, connectez-le à Internet et recherchez les mises à jour. Si Google Play n’est pas installé sur l’appareil, procurez-vous la version mise à jour du composant et appliquez-le aux appareils. Ou, mettez à jour vers le dernier système d’exploitation de l’appareil émis par rayures.

### <a name="management-actions-take-a-long-time"></a>Les actions de gestion prennent beaucoup de temps

Si Google Play services ne sont pas disponibles, la fin de certaines tâches peut prendre jusqu’à 8 heures. [Les limitations de portail d’entreprise Intune application pour Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (ouvre un autre site Web Microsoft) peuvent être une bonne ressource.

### <a name="device-spoofing-suspected-shows-in-intune"></a>Les « usurpations d’appareil suspectes » dans Intune

Cette erreur signifie qu’Intune soupçonne qu’un appareil Android non rayures signale son modèle et son fabricant en tant qu’appareil rayures.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>La version de Portail d’entreprise application est antérieure à la version minimale requise

Intune peut mettre à jour la version minimale requise de l’application Portail d’entreprise. Si Google Play n’est pas installé sur l’appareil, l’application Portail d’entreprise n’est pas automatiquement mise à jour. Si la version minimale requise est plus récente que la version installée, l’application Portail d’entreprise cesse de fonctionner. Mettez à jour vers la dernière application Portail d’entreprise à l’aide [de chargement sur les appareils rayures](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Étapes suivantes

[Forums de discussion rayures](https://developer.zebra.com/community/home/discussions) (ouvre le site Web de rayures)

[Utiliser et gérer des appareils Zebra avec des Extensions de mobilité Zebra dans Intune](android-zebra-mx-overview.md)
