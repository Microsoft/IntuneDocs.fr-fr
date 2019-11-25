---
title: fichier descriptif
description: fichier descriptif
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: b59419be9f381a1c646a7778b73ed172526f6ef6
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188429"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune.

### <a name="update-your-intune-outlook-app-protection-policies-app--2576686--"></a>Mettre à jour vos stratégies de protection des applications Outlook Intune (APP)<!--2576686-->
Vous devrez peut-être agir si vous avez reçu MC195618 dans votre centre de messages. Comme partagé dans les ID de fonctionnalité de feuille de route Microsoft 365 : 56325 et 56326, Intune et Outlook pour iOS et Android déploient une prise en charge pour limiter les données sensibles dans les notifications de messagerie et les rappels de calendrier. Suite à ces améliorations, Outlook pour iOS et Android vont supprimer la prise en charge de plusieurs clés de configuration d’applications de protection des données que vous utilisez actuellement pour gérer les notifications.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Les nouvelles fonctionnalités ne sont pas livrées, mais lorsqu’elles le seront, les clés de configuration d’applications suivantes ne fonctionneront plus dans Outlook pour iOS et Android :
- com.microsoft.outlook.Mail.NotificationsEnabled
- com.microsoft.outlook.Mail.NotificationsEnabled.UserChangeAllowed
- com.microsoft.outlook.Calendar.NotificationsEnabled
- com.microsoft.outlook.Calendar.NotificationsEnabled.UserChangeAllowed

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Nous vous recommandons de configurer le paramètre de protection des données « Notifications de données de l’organisation » de la stratégie Intune App Protection avec une valeur « Bloquer les données d’organisation » pour préparer cette nouvelle fonctionnalité. À partir du 16 décembre 2019, Outlook pour iOS et Android tiendra compte du paramètre de protection des données « Notifications de données de l’organisation » et ne prendra plus en charge les clés susmentionnées. Si vous configurez ce nouveau paramètre, les données sensibles ne seront pas divulguées lorsque les clés de configuration ci-dessus ne seront plus prises en charge. En outre, Outlook offre une granularité supplémentaire lorsque le paramètre de protection des données « Notifications de données de l’organisation » est défini sur « Bloquer les données de l’organisation » avec un paramètre de configuration d’application supplémentaire, « Notifications de calendrier ». La combinaison du paramètre de stratégie de protection des applications et de ce paramètre de configuration d’application limite les informations sensibles dans les notifications par courrier électronique, tout en exposant les informations sensibles dans les notifications de calendrier, afin que les utilisateurs puissent accéder à leurs réunions en parcourant rapidement la notification ou le centre de notifications.

#### <a name="additional-information"></a>Informations supplémentaires
Pour plus d’informations sur les paramètres d’application et les paramètres d’Outlook, consultez :
- [Paramètres de stratégie de protection d’application Android](../apps/app-protection-policy-settings-android.md)
- [Paramètres de stratégie de protection des applications iOS](../apps/app-protection-policy-settings-ios.md)
- [Déploiement des paramètres de configuration de l’application Outlook pour iOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)


### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Modification planifiée d’Intune : Fin de la prise en charge de Portail d'entreprise sur Windows 10, version 1703<!--5026679-->
Windows 10, version 1703 (aussi connu sous le nom de Windows 10, RS2) a été mis hors service le 8 octobre 2019 pour les éditions Entreprise et Éducation. Intune cessera la prise en charge de l'application Portail d'entreprise correspondante pour RS2/RS1 à partir du 26 décembre 2019.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
À l’avenir, vous ne verrez pas de nouvelles fonctionnalités dans la version spécifique de l’application Portail d'entreprise, bien que nous continuerons à prendre en charge cette version jusqu’au 26 décembre 2019, y compris en fournissant les mises à jour de sécurité de l'application Portail d'entreprise si nécessaire. Cependant, étant donné que Windows 10, version 1703 ne recevra aucune mise à jour de sécurité après sa mise hors service, nous vous recommandons fortement de mettre à jour vos appareils Windows avec une version Windows plus récente et de vous assurer que vous utilisez la dernière version de l’application Portail d'entreprise afin de continuer à bénéficier des nouvelles fonctionnalités supplémentaires.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Les étapes à suivre dépendent de la configuration de votre environnement. En général, vous devrez identifier puis mettre à jour les appareils dotés de l’ancienne version de l’OS et/ou de l’application Portail d'entreprise. Pour définir les anneaux de mise à jour de Windows 10, connectez-vous à Intune -> Mises à jour logicielles - Anneaux de mise à jour Windows 10. La dernière version de l’application Portail d’entreprise est la version 10.3.5601.0. Invitez vos utilisateurs à obtenir cette version sur le Microsoft Store afin de recevoir les prochaines versions. Vous pouvez également configurer Intune pour installer les dernières versions sur vos appareils Windows via le [Microsoft Store pour Entreprises](https://docs.microsoft.com/intune/windows-store-for-business).

#### <a name="additional-information"></a>Informations supplémentaires
[Ajouter manuellement l’application Portail d’entreprise Windows 10 à l’aide de Microsoft Intune](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Action nécessaire : Utilisez Microsoft Edge pour votre expérience Protected Intune Browser<!--5728447-->
Comme annoncé au cours de l’année dernière, Microsoft Edge mobile prend en charge le même ensemble de fonctions de gestion que Managed Browser, tout en offrant une expérience de l’utilisateur final nettement améliorée. Pour faire place aux expériences robustes offertes par Microsoft Edge, nous allons retirer Intune Managed Browser. À partir du 27 janvier 2020, Intune ne prendra plus en charge Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ? 
À partir du 1er février 2020, Intune Managed Browser ne sera plus disponible dans le Google Play Store ni dans l’iOS App Store. À ce stade, vous pourrez toujours cibler les nouvelles stratégies de protection des applications sur Intune Managed Browser, mais les nouveaux utilisateurs ne pourront pas télécharger l’application Intune Managed Browser. De plus, sous iOS, les nouveaux clips web envoyés vers un appareil inscrit via MDM s'ouvriront dans Microsoft Edge au lieu d’Intune Managed Browser.  

Le 31 mars 2020, Intune Managed Browser sera retiré de la console Azure. Cela signifie que vous ne pourrez plus créer de nouvelles stratégies pour Intune Managed Browser. Si vous avez déjà mis en place des stratégies Intune Managed Browser, elles ne seront pas affectées. Intune Managed Browser s’affichera dans la console en tant qu’application métier sans icône, et les stratégies existantes s’afficheront toujours comment étant ciblées à l’application. À ce stade, nous supprimerons également l’option permettant de rediriger le contenu web vers Intune Managed Browser dans la section Protection des données des stratégies de protection des applications.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ? 
Pour assurer une transition en douceur entre Intune Managed Browser et Microsoft Edge, nous vous recommandons de prendre les mesures suivantes de manière proactive : 

1. Ciblez Microsoft Edge pour iOS et Android avec la stratégie de protection des applications (également appelée MAM) et les paramètres de configuration des applications. Vous pouvez réutiliser vos stratégies Intune Managed Browser pour Microsoft Edge en ciblant ces stratégies existantes également sur Microsoft Edge.  
2. Assurez-vous que le paramètre de stratégie de protection des applications « Restreindre le transfert de contenu web à d'autres applications » est défini sur « Navigateurs gérés par stratégie » pour toutes les applications protégées par MAM dans votre environnement. 
3. Ciblez tous les applications protégées par MAM en définissant le paramètre de configuration des applications gérées « com.microsoft.intune.useEdge » sur true. Dès le mois prochain avec la sortie de la version 1911, vous pourrez effectuer les étapes 2 et 3 simplement en définissant le paramètre « Restreindre le transfert de contenu web à d’autres applications » sur « Microsoft Edge » dans la section Protection des données de vos stratégies de protection des applications. 

La prise en charge des clips web sur iOS et Android sera bientôt disponible. Une cette prise en charge disponible, vous devrez recibler les clips web préexistants pour vous assurer qu’ils s’ouvrent dans Microsoft Edge au lieu de Managed Browser. 

#### <a name="additional-information"></a>Informations supplémentaires
Pour plus d’informations, consultez notre documentation sur [l’utilisation de Microsoft Edge avec les stratégies de protection des applications](../apps/manage-microsoft-edge.md), ou notre [billet de blog de support](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).

### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Modification planifiée : Expérience mise à jour pour l’inscription des appareils Android Entreprise dédiés dans Intune<!--5198878-->
Avec la version de novembre ou 1911 de Intune, nous ajoutons la prise en charge du déploiement de certificat d’appareil SCEP aux appareils Android Enterprise dédiés pour activer l’accès par certificat aux profils Wi-Fi. Cette modification implique également des modifications mineures du workflow lors de l’inscription des appareils Android Enterprise dédiés.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Si vous gérez des appareils Android Enterprise dédiés dans votre environnement, vous commencerez à voir les modifications apportées en novembre.

- Pour les nouvelles inscriptions d’appareil dédié Android Entreprise : les utilisateurs finaux voient un autre ensemble d’étapes sur les appareils lors de l’inscription. L’inscription continuera de démarrer comme elle le fait aujourd’hui (avec QR, NFC, Zero Touch ou l’identificateur de périphérique), mais après la publication de service de novembre, une étape d’installation d’application obligatoire s’affichera.
- Pour les appareils Android existants inscrits en tant qu’appareils dédiés : Intune commencera à installer automatiquement l’application Microsoft Intune sur les appareils à partir du début du mois de novembre. Aucune action de votre part n’est nécessaire. L’application est téléchargée et installée automatiquement sur les appareils. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Vous devez envisager de mettre à jour les conseils à l’utilisateur final et d’informer votre support technique de cette modification. Pour plus d’informations et de captures d’écran, cliquez sur Informations supplémentaires. Nous mettrons à jour la page de nouveautés une fois ce changement déployé.

#### <a name="additional-information"></a>Informations supplémentaires
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="end-of-support-for-legacy-pc-management"></a>Fin du support pour la gestion des PC hérités

La gestion des PC hérités ne sera plus prise en charge à partir du 15 octobre 2020. Mettez à niveau les appareils vers Windows 10 et réinscrivez-les en tant qu’appareils de gestion des appareils mobiles (MDM) pour qu’ils continuent d’être gérés par Intune.

[En savoir plus](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Diminution du support pour l’administrateur d’appareil Android 
L’administrateur d’appareil Android (parfois appelé gestion Android « héritée » et publiée avec Android 2.2) est un moyen de gérer les appareils Android. Toutefois, des fonctionnalités de gestion améliorées sont désormais disponibles avec [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (fournie avec Android 5.0). Dans le but de passer à une gestion des périphériques modernes, plus riche et plus sécurisée, Google diminue le support des administrateurs d’appareil dans les nouvelles versions Android.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
En raison de ces modifications apportées par Google, les utilisateurs Intune seront affectés des manières suivantes :  
- Intune pourra uniquement assurer le support des appareils Android gérés par l’administrateur d’appareil exécutant Android 10 et versions ultérieures (également appelé Android Q) jusqu’à l’été 2020. Il s’agit de la date à laquelle la prochaine version principale d’Android est censée être publiée.   
- Les appareils gérés par l’administrateur d’appareil qui exécutent Android 10 ou une version ultérieure après l’été 2020 ne peuvent plus être entièrement gérés.       
- Les appareils Android gérés par l’administrateur d’appareil qui restent sur les versions Android inférieures à Android 10 ne sont pas affectés et peuvent continuer à être entièrement gérés avec l’administrateur d’appareil.    
- Pour tous les appareils exécutant Android 10 et versions ultérieures, Google a limité la possibilité pour les agents de gestion des administrateurs d’appareil, notamment le Portail d’entreprise, d’accéder aux informations d’identification de l’appareil. Cette restriction a un impact sur les fonctionnalités Intune suivantes après la mise à jour d’un appareil vers Android 10 ou version ultérieure :  
    - Le contrôle d’accès réseau pour VPN ne fonctionnera plus.   
    - L’identification des appareils comme appartenant à l’entreprise avec le numéro IMEI ou le numéro de série ne marque pas automatiquement les appareils comme appartenant à l’entreprise.  
    - Le numéro IMEI et le numéro de série ne seront plus visibles pour les administrateurs informatiques dans Intune. 
        > [!NOTE]
        > Cela affecte uniquement les appareils gérés par l’administrateur d’appareil sur Android 10 et versions ultérieures et n’affecte pas les appareils gérés comme Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Pour éviter la réduction des fonctionnalités de l’été 2020, nous vous recommandons d’effectuer les opérations suivantes :
- N’intégrez pas de nouveaux appareils dans la gestion des administrateurs d’appareil.
- Si un appareil est censé recevoir une mise à jour d’Android 10, migrez-le de la gestion de l’administrateur d’appareil vers la gestion Android Enterprise et/ou des stratégies de protection d’application.

#### <a name="additional-information"></a>Informations supplémentaires
- [Aide de Google pour la migration de l’administrateur d’appareil vers Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentation Google sur le plan de dépréciation de l’API de l’administrateur d’appareil](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Modification planifiée : Les stratégies de protection des applications et du Kit de développement logiciel (SDK) des applications Intune pour Android évoluent vers le support d’Android 5.0 et versions ultérieures dans une version à venir <!--4911065 -->
Intune passera au support d’Android 5.x (lollipop) et versions ultérieures dans une version à venir. Mettez à jour les applications inclues dans un wrapper avec le dernier Kit de développement logiciel (SDK) des applications Intune et mettez à jour vos appareils.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Si vous n’utilisez pas ou si vous envisagez d’utiliser le Kit de développement logiciel (SDK) ou l’APP pour Android, cette modification n’aura aucun effet. Si vous utilisez le Kit de développement logiciel (SDK) d’applications Intune, veillez à mettre à jour vers la dernière version et à mettre à jour vos appareils vers Android 5.x et versions ultérieures. Si vous ne mettez pas à jour, les applications ne recevront aucune mise à jour et perdront en qualité au fil du temps.

Vous trouverez ci-dessous une liste des appareils courants inscrits dans Intune qui exécutent Android version 4.x. Si vous avez l’un de ces appareils, prenez les mesures appropriées pour vous assurer que cet appareil prendra en charge Android version 5.0 ou ultérieure ou qu’il sera remplacé par un appareil qui prend en charge Android version 5.0 ou ultérieure. Cette liste n’est pas exhaustive de tous les appareils qui peuvent avoir besoin d’être évalués :

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Incluez dans un wrapper vos applications avec le dernier Kit de développement logiciel (SDK) d’application Intune. Vous pouvez également définir le paramètre de lancement conditionnel « Exiger une version minimale du système d’exploitation (avertissement uniquement) » pour informer les utilisateurs finaux des appareils personnels à mettre à niveau.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Modification planifiée d’Intune : Fin de la prise en charge de Windows 7<!-- 3042987 -->
Comme nous l'avons annoncé dans le message MC148476 publié en septembre 2018, et de nouveau dans le message MC176794 de mars 2019, la prise en charge étendue de Windows 7 cessera le 14 janvier 2020. À cette date, Intune arrêtera la prise en charge des appareils fonctionnant sous Windows 7 pour se concentrer sur ses investissements dans la prise en charge de nouvelles technologies et offrir une nouvelle expérience de qualité à ses utilisateurs finaux. Après cette date, l'assistance technique et les mises à jour automatiques qui aident à protéger votre PC Windows 7 ne seront plus disponibles via Intune. Microsoft vous recommande fortement de passer à Windows 10 avant janvier 2020 afin d'éviter un scénario où vous avez besoin d'un service ou d'une assistance qui n'est plus disponible. Cliquez [ici](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) pour en savoir plus sur le cycle de vie du support Windows.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Vous recevez ce message car vous gérez actuellement des PC Windows 7 à l'aide de l'ancien agent logiciel pour PC Intune. À moins d'un an de la fin de la prise en charge étendue de Windows 7, nous encourageons vivement votre entreprise à commencer dès que possible la mise à niveau vers Windows 10.  

Les capacités de gestion pour PC sont directement intégrées au système d'exploitation Windows 10 et vous n'avez plus besoin d'installer un agent client tel que le client logiciel Intune pour Windows 7. À partir de Windows 8.1, Microsoft utilise l'architecture MDM (Mobile Device Management) pour approvisionner, configurer, mettre à jour et gérer les PC Windows. Une fois que vous avez configuré Intune, vous pouvez simplifier l'inscription à Windows en [inscrivant les PC Windows 10 dans Intune](..\windows-enroll.md) via le canal MDM. Nous vous recommandons d'utiliser cette solution de gestion MDM « sans agent » pour gérer vos PC Windows 10.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Nous encourageons votre entreprise à mettre en œuvre immédiatement ce plan d'action :

- Planifiez et mettez à niveau le parc de PC Windows 7 vers Windows 10 avant le 14 janvier 2020.
- Explorez la [prise en charge du déploiement Windows 10](https://docs.microsoft.com/windows/deployment/) pour en savoir plus sur la façon de mettre à niveau votre parc existant de PC Windows 7 vers Windows 10.
- Examinez l'offre [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) proposée par le biais de Fast Track, qui vous aidera à garantir la compatibilité des applications Microsoft.
- Faites évoluer vos anciens appareils gérés par le client logiciel Intune vers la solution recommandée par Microsoft pour gérer Windows 10 à l'aide de MDM. Inscrivez tous les nouveaux PC Windows 10 en utilisant la gestion MDM pour Intune dans le portail Azure.

Pour plus d’informations, consultez le [billet de blog ici](https://aka.ms/Windows7_Intune).


