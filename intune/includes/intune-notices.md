---
title: fichier descriptif
description: fichier descriptif
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 5ebab881a524bc361e271856b6762776974cea20
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601532"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune.

### <a name="end-of-support-for-legacy-pc-management"></a>Fin du support pour la gestion des PC hérités

La gestion des PC hérités ne sera plus prise en charge à partir du 15 octobre 2020. Mettez à niveau les appareils vers Windows 10 et réinscrivez-les en tant qu’appareils MDM pour qu’ils continuent d’être gérés par Intune.

[En savoir plus](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Diminution du support pour l’administrateur d’appareil Android 
L’administrateur d’appareil Android (parfois appelé gestion Android « héritée » et publiée avec Android 2.2) est un moyen de gérer les appareils Android. Toutefois, des fonctionnalités de gestion améliorées sont désormais disponibles avec [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (fournie avec Android 5.0). Dans le but de passer à une gestion des périphériques modernes, plus riche et plus sécurisée, Google diminue le support des administrateurs d’appareil dans les nouvelles versions Android.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
En raison de ces modifications apportées par Google, les utilisateurs Intune seront affectés des manières suivantes :  
- Intune pourra uniquement assurer le support des appareils Android gérés par l’administrateur d’appareil exécutant Android 10 et versions ultérieures (également appelé Android Q) jusqu’à l’été 2020. Il s’agit de la date à laquelle la prochaine version principale d’Android est censée être publiée.   
- Les appareils gérés par l’administrateur d’appareil qui exécutent Android 10 ou une version ultérieure après l’été 2020 ne peuvent plus être entièrement gérés.       
- Les appareils Android gérés par l’administrateur d’appareil qui restent sur les versions Android inférieures à Android 10 ne sont pas affectés et peuvent continuer à être entièrement gérés avec l’administrateur d’appareil.    
- Pour tous les appareils exécutant Android 10 et versions ultérieures, Google a limité la possibilité pour les agents de gestion des administrateurs d’appareil, notamment le Portail d’entreprise, d’accéder aux informations d’identification de l’appareil. Cela a un impact sur les fonctionnalités Intune suivantes après la mise à jour d’un appareil vers Android 10 ou version ultérieure :  
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

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Mettre à jour votre application de Portail d’entreprise Android vers la dernière version <!--4536963-->
Intune publie régulièrement des mises à jour vers l’application Portail d’entreprise Android. En novembre 2018, nous avons publié une mise à jour du portail d’entreprise, incluant un commutateur principal pour vous préparer à la modification de Google à partir de leur plateforme de notification existante vers Firebase Cloud Messaging (FCM) de Google. Une fois que Google a retiré sa plateforme de notification et s’est déplacé vers FCM, les utilisateurs finaux doivent avoir mis à jour leur application Portail d’entreprise au moins vers la version de novembre 2018 pour continuer à communiquer avec Google Play Store.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Notre télémétrie indique que vous avez des appareils avec une version du Portail d’entreprise antérieure à 5.0.4269.0. Si cette version ou une version ultérieure de l’application Portail d’entreprise n’est pas installée, les professionnels de l’informatique lancent des actions telles que la réinitialisation de tout l’appareil, la réinitialisation du mot de passe, l’installation des applications disponibles et requises et l’inscription des certificats peut ne pas fonctionner comme prévu. Si vos appareils sont inscrits à la Gestion des données de référence dans Intune, vous pouvez voir les versions du portail d’entreprise et les utilisateurs en accédant à des applications clientes – applications découvertes. En sélectionnant les versions antérieures de l’application Portail d’entreprise, vous pourrez voir ce quels utilisateurs finaux disposent des appareils qui n’ont pas de mises à jour de l’application Portail d’entreprise.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Demandez aux utilisateurs finaux d’appareils Android qui n’ont pas été mis à jour de mettre à jour l’application Portail d’entreprise via Google Play. Informez le support technique au cas où un utilisateur n’a pas conservé la mise à jour automatique de l’application Portail d’entreprise. Consultez le lien *Informations supplémentaires* pour en savoir plus sur la plateforme FCM et les modifications apportées par Google.

#### <a name="additional-information"></a>Informations supplémentaires
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Nouvelle expérience plein écran prochainement disponible sur Intune <!--4593669-->
Nous déployons actuellement une mise à jour des options de création et d’édition dans l’interface utilisateur Intune sur le portail Azure. Cette nouvelle expérience simplifiera les flux de travail existants grâce à un format de style assistant condensé au sein d’un seul panneau. Cette mise à jour fera disparaître la « prolifération de panneaux » ainsi que tous les flux de création et d’édition qui vous obligent à parcourir de façon approfondie une multitude de panneaux. Les flux de travail de création seront également à jour pour inclure des affectations (à l’exception de l’affectation d’applications).

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
L’expérience plein écran sera déployée sur Intune à la fois sur portal.azure.com et sur devicemanagement.microsoft.com dans les prochains mois. Cette mise à jour de l’interface utilisateur n’aura aucune incidence sur la fonctionnalité de vos stratégies et profils existants : vous bénéficierez simplement d’un flux de travail légèrement modifié. Lorsque vous créez des stratégies, par exemple, vous pourrez définir certaines attributions dans le cadre de ce flux au lieu d’effectuer cette opération après la création de la stratégie. Consultez le billet de blog de la section *Informations supplémentaires* pour obtenir des captures d’écran présentant la nouvelle expérience dans la console.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Vous n’avez rien à faire, mais nous vous recommandons de mettre à jour vos ressources informatiques professionnelles. Nous mettrons à jour notre documentation à mesure que cette expérience est déployée sur les différents panneaux Intune dans le portail Azure.

#### <a name="additional-information"></a>Informations supplémentaires 
https://aka.ms/intune_fullscreen


### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-october---4911065---"></a>Modification planifiée : Les stratégies de protection des applications et du Kit de développement logiciel (SDK) des applications Intune pour Android évoluent vers le support d’Android 5.0 et versions ultérieures en octobre <!--4911065 -->
Intune passera au support d’Android 5.x (lollipop) et versions ultérieures en octobre. Mettez à jour les applications inclues dans un wrapper avec le dernier Kit de développement logiciel (SDK) des applications Intune et mettez à jour vos appareils.

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

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7----3042987---"></a>Modification planifiée d’Intune : Fin de la prise en charge de Windows 7 <!-- 3042987 -->
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
