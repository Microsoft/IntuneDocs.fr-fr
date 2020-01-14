---
title: Résoudre les problèmes et passer en revue les journaux des profils d’appareil Wi-Fi dans Microsoft Intune - Azure | Microsoft Docs
description: Comprenez et dépannez les problèmes de profil de configuration d’appareil Wi-Fi sur les appareils Android, iOS et Windows dans Microsoft Intune. Examinez les journaux et découvrez les problèmes courants et solutions possibles.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 70f471e7f4db7ddce89d8956474822375c684944
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547979"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Dépannage des profils de configuration d’appareil Wi-Fi dans Microsoft Intune

Dans Intune, vous pouvez créer des profils de configuration d’appareil qui incluent des paramètres de connexion pour votre réseau Wi-Fi. Utilisez ces paramètres pour connecter des appareils Android, iOS et Windows aux utilisateurs sur le réseau de l’organisation.

Cet article montre à quoi ressemble un profil Wi-Fi lorsqu’il s’applique correctement aux appareils. Il comprend également les informations de journalisation, les problèmes courants et bien plus encore. Utilisez cet article pour vous aider à dépanner vos profils Wi-Fi.

Pour plus d’informations sur les profils Wi-Fi dans Intune, consultez [Ajouter et utiliser des paramètres Wi-Fi sur vos appareils](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Avant de commencer

Les exemples de cet article utilisent l’authentification par certificat SCEP pour les profils Intune. Il suppose également que les profils racine approuvés et SCEP fonctionnent correctement sur l’appareil.

## <a name="android"></a>Android

Dans cette section, nous parcourons l’expérience utilisateur final lors de l’installation des profils de configuration sur un appareil Android.

### <a name="end-user-experience-example"></a>Exemple d’expérience utilisateur final

Ce scénario utilise un appareil Nokia 6.1. Avant d’installer le profil Wi-Fi sur l’appareil, installez les profils racine approuvés et SCEP.

1. Les utilisateurs finaux reçoivent une notification pour installer le profil de certificat racine approuvé :

    > [!div class="mx-imgBorder"]
    > ![Exemple de notification d’application Portail d’entreprise sur Android pour installer le profil de certificat racine approuvé](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. Le message suivant vous invite à installer le profil de certificat SCEP :

    > [!div class="mx-imgBorder"]
    > ![Exemple de notification d’application Portail d’entreprise sur Android pour installer le profil de certificat SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > Lorsque vous utilisez un appareil Android géré par l’administrateur de l’appareil, plusieurs certificats peuvent être répertoriés. Lorsqu’un profil de certificat est révoqué ou supprimé, le certificat reste sur l’appareil. Dans ce scénario, sélectionnez le certificat le plus récent. Il s’agit généralement du dernier certificat figurant dans la liste.
    >
    > Cette situation ne se produit pas sur les appareils Android Enterprise et Samsung Knox. Pour plus d’informations, consultez [Gérer les appareils de profil professionnel Android](../enrollment/android-enterprise-overview.md) et [Supprimer des certificats SCEP et PKCS](../protect/remove-certificates.md#android-knox-devices).

3. Ensuite, les utilisateurs reçoivent une notification pour installer le profil Wi-Fi :

    > [!div class="mx-imgBorder"]
    > ![Exemple de notification d’application Portail d’entreprise sur Android pour installer le profil de certificat SCEP](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. Lorsque vous avez terminé, la connexion Wi-Fi est indiquée comme un réseau enregistré :

    > [!div class="mx-imgBorder"]
    > ![La connexion Wi-Fi apparaît comme un réseau enregistré](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Consulter les journaux des applications Portail d’entreprise

Sur Android, le fichier **Omadmlog.log** détaille les activités du profil Wi-Fi lorsqu’il est installé sur l’appareil. Vous pouvez avoir jusqu’à cinq fichiers journaux Omadmlog. Veillez à obtenir l’horodatage de la dernière synchronisation, car il vous aidera à trouver les entrées de journal associées.

Dans l’exemple suivant, utilisez [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) pour lire les journaux, puis recherchez « wifimgr » :

> [!div class="mx-imgBorder"]
> ![La connexion Wi-Fi apparaît comme un réseau enregistré](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

Le journal suivant affiche vos résultats de recherche et indique que le profil Wi-Fi a été appliqué avec succès :

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

Une fois le profil Wi-Fi installé sur l’appareil, il est affiché dans le **profil de gestion** :

> [!div class="mx-imgBorder"]
> ![Profil de gestion sur un appareil iOS](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![La connexion Wi-Fi apparaît comme un réseau Wi-Fi sur un appareil iOS](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>Examiner la console iOS et les journaux des appareils

Sur les appareils iOS, le journal des applications Portail d’entreprise n’inclut pas d’informations sur les profils Wi-Fi. Pour afficher les détails de l’installation de vos profils Wi-Fi, utilisez la console/les journaux de l’appareil :

1. Connectez l’appareil iOS à Mac. Accédez à **Applications** > **Utilitaires** et ouvrez l’application Console.
2. Sous **Action**, sélectionnez **Inclure les messages d’information** et **Inclure les messages de débogage** :

    > [!div class="mx-imgBorder"]
    > ![Inclure les messages d’information et Inclure les messages de débogage dans l’application Console d’iOS](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Reproduisez le scénario et enregistrez les journaux dans un fichier texte :

    1. Sélectionnez tous les messages sur l’écran actuel : **Modifier** > **Sélectionner tout**.
    2. Copiez les messages : **Modifier** > **Copier**.
    3. Collez les données du journal dans un éditeur de texte, puis enregistrez le fichier.

4. Recherchez le fichier journal enregistré pour afficher les informations détaillées. Une fois le profil correctement installé, votre sortie ressemble au journal suivant :

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

Une fois le profil Wi-Fi installé sur l’appareil, accédez à **Paramètres** > **Comptes** > **Accès Professionnel ou Scolaire**. Sélectionnez votre compte > **Informations** :

> [!div class="mx-imgBorder"]
> ![Accédez au compte d’entreprise ou scolaire et sélectionnez Informations sur l’appareil Windows](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

Dans **Zones gérées par Microsoft**, **Wi-Fi** s’affiche :

> [!div class="mx-imgBorder"]
> ![Dans les domaines gérés par Microsoft, vérifiez que le Wi-Fi est répertorié sur Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Pour afficher la connexion Wi-Fi, accédez à **Paramètres** > **Réseau & Internet**  > **Wi-Fi** :

> [!div class="mx-imgBorder"]
> ![Sur Windows, trouvez la connexion Wi-Fi en tant que réseau connu dans Paramètres](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Consulter les journaux de l’observateur d’événements

Sur les appareils Windows, les détails relatifs aux profils Wi-Fi sont consignés dans l’observateur d’événements :

1. Ouvrez l’application **Observateur d’événements**.
2. Dans le menu **Affichage**, sélectionnez **Afficher les journaux d'analyse et de débogage**.
3. Développez **Journaux des applications et services** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**

Vous générez ainsi des informations qui ressemblent aux journaux suivants :

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>Problèmes courants

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>Problème 1 : Le profil Wi-Fi n’est pas déployé sur l’appareil

- Confirmez que le profil Wi-Fi est affecté au groupe approprié :

    1. Dans le [Centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Appareils** > **Profils de configuration**.
    2. Sélectionnez votre profil > **Attributions**. Vérifiez que les groupes sélectionnés sont corrects.
    3. Dans Endpoint Manager, sélectionnez **Dépannage + support**. Passez en revue les informations sur les **Affectations**.

- Dans Endpoint Manager, sélectionnez **Dépannage + support**. Confirmez que l’appareil peut se synchroniser avec Intune en vérifiant l’heure de **Dernière vérification**.

- Si le profil Wi-Fi est lié aux profils racine approuvés et SCEP, vérifiez que les deux profils sont déployés sur l’appareil. Le profil Wi-Fi dépend de ces profils.

- Sur les appareils Windows 10 et versions ultérieures, consultez le journal des informations de diagnostic de la gestion des appareils mobiles :

  1. Accédez à **Paramètres** > **Comptes** > **Accès scolaire ou professionnel**.
  2. Sélectionnez votre compte professionnel ou scolaire > **Informations**.
  3. En bas de la page **Paramètres**, sélectionnez **Créer un rapport**.
  4. Une fenêtre s’ouvre et affiche le chemin d’accès aux fichiers journaux. Sélectionnez **Exporter**.
  5. Accédez au chemin d’accès `\Users\Public\Documents\MDMDiagnostics` et affichez le rapport :

      > [!div class="mx-imgBorder"]
      > ![Exemples d’informations de diagnostic de la gestion des appareils mobiles montrant la configuration du profil Wi-Fi sur les appareils Windows 10](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > Pour plus d’informations, consultez [Diagnostiquer les échecs de gestion des appareils mobiles dans Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).

- Sur les appareils Android, si les profils racine approuvés et SCEP ne sont pas installés sur l’appareil, l’entrée suivante s’affiche dans le fichier Omadmlog de l’application Portail d’entreprise :

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - Lorsque les profils racine approuvés et SCEP se trouvent sur l’appareil Android et sont conformes, le profil Wi-Fi peut ne pas se trouver sur l’appareil. Ce problème se produit lorsque le fournisseur **CertificateSelector** de l’application Portail d’entreprise ne trouve pas de certificat qui correspond aux critères spécifiés. Les critères spécifiques peuvent figurer dans le modèle de certificat ou dans le profil SCEP.

    Si le certificat correspondant est introuvable, les certificats sur l’appareil ne sont pas installés. Le profil Wi-Fi n’est pas appliqué, car il ne dispose pas du certificat approprié. Dans ce scénario, vous voyez l’entrée suivante dans le fichier Omadmlog de l’application Portail d’entreprise :

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    L’exemple de journal suivant indique que les certificats sont exclus, car le critère d’utilisation améliorée de la clé (EKU) **N’importe quel motif** a été spécifié. Toutefois, les certificats attribués à l’appareil n’ont pas cette utilisation améliorée de la clé :

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    L’exemple suivant montre le profil SCEP entré dans l'utilisation améliorée de la clé **N’importe quel motif**. Toutefois, il n’est pas entré dans le modèle de certificat de l’autorité de certification. Pour résoudre ce problème, ajoutez l’option **N’importe quel motif** au modèle de certificat. Vous pouvez également supprimer l’option **N’importe quel motif** à partir du profil SCEP.

    > [!div class="mx-imgBorder"]
    > ![Sur Android, ajoutez N’importe quel motif au modèle de certificat sur l’autorité de certification](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![Sur Android, ajoutez N’importe quel motif au profil de configuration de certificat SCEP dans Intune](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Vérifiez que tous les certificats requis dans la chaîne de certificats complète se trouvent sur l’appareil Android. Dans le cas contraire, le profil Wi-Fi ne peut pas être installé sur l’appareil. Pour plus d’informations, consultez [Autorité de certification intermédiaire manquante](https://developer.android.com/training/articles/security-ssl#MissingCa) (ouvre le site web d’Android).
  - Filtrez Omadmlog avec des mots-clés pour rechercher des informations, comme le certificat utilisé dans le profil Wi-Fi, et si le profil a été appliqué avec succès.

    Par exemple, utilisez [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) pour lire les journaux. Utilisez la chaîne de recherche pour filtrer « wifimgr » :

    > [!div class="mx-imgBorder"]
    > ![Filtrer CMTrace pour rechercher les profils de configuration WiFiMgr sur les appareils Android](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    La sortie doit ressembler au journal suivant :

    > [!div class="mx-imgBorder"]
    > ![Exemple de sortie de journal CMTrace qui indique que le profil de configuration Wi-Fi est correctement appliqué sur les appareils](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Si vous voyez une erreur dans le journal, copiez l’horodatage de l’erreur et annulez le filtre du journal. Ensuite, utilisez l’option « Rechercher » avec l’horodatage pour voir ce qui s’est produit juste avant l’erreur.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>Problème 2 : Le profil Wi-Fi est déployé sur l’appareil, mais l’appareil ne peut pas se connecter au réseau

En général, ce problème est causé par un problème en dehors d’Intune. Les tâches suivantes peuvent vous aider à comprendre et résoudre les problèmes de connectivité :

- Connectez-vous manuellement au réseau à l’aide d’un certificat ayant les mêmes critères que ceux du profil Wi-Fi.

  Si vous pouvez vous connecter, examinez les propriétés du certificat dans la connexion manuelle. Ensuite, mettez à jour le profil Wi-Fi Intune avec les mêmes propriétés de certificat.
- Les erreurs de connectivité sont généralement enregistrées dans le journal du serveur Radius. Par exemple, il doit indiquer si l’appareil a tenté de se connecter avec le profil Wi-Fi.

## <a name="need-more-help"></a>Besoin d'aide

- Utilisez les [forums des utilisateurs d’Intune](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) ou [accédez au support technique de Microsoft](../fundamentals/get-support.md).

- Pour plus d’informations sur les profils Wi-Fi dans Microsoft Intune, consultez les articles suivants :

  - Ajouter des paramètres Wi-Fi pour les appareils exécutant [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md) et [Windows 10 et versions ultérieures](wi-fi-settings-windows.md).
  - [Astuce de support : comment configurer NDES pour les déploiements de certificats SCEP dans Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Résolvez les problèmes liés au [déploiement de profils de certificat SCEP](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) et à la [configuration de NDES](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune).

- Pour obtenir les dernières actualités, des informations et des conseils techniques, consultez les blogs officiels :
  - [Blog de l’équipe de support Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Blog Microsoft Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>Étapes suivantes

[Analysez vos profils](device-profile-monitor.md).
