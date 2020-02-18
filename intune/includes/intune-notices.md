---
title: fichier descriptif
description: inclure fichier
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 4e93cb7f2d503704251b16d1af03924358020d4e
ms.sourcegitcommit: 1aaff35fddb3d06458d739968d28971fed0bb2ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2020
ms.locfileid: "77156122"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune.

### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>Modification planifiée : Évolution de l’expérience d’inscription des appareils Android Enterprise dédiés dans Intune<!--6114580-->
Nous avons annoncé, à la sortie de la version de novembre, que nous ajoutions la prise en charge du déploiement de certificat SCEP aux appareils Android Enterprise dédiés pour permettre l’accès par certificat aux profils Wi-Fi. Cette modification impliquait quelques modifications mineures du déroulement de l’inscription des appareils Android Enterprise dédiés. À l’approche de la mise à jour du service de mars (2003), nous aimerions vous faire part d’autres modifications.

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
Si vous gérez des appareils Android Enterprise dédiés dans votre environnement, vous commencerez à voir les modifications apportées en mars.
- Pour les appareils Android dédiés inscrits avant le 22 novembre 2019 ou la mise à jour du service 1911 : l’application Microsoft Intune est installée sur ces appareils. Une fois les modifications du backend déployées dans le service Intune en mars, les certificats SCEP déployés sur les appareils et associés à des profils Wi-Fi commenceront à s’appliquer.
- Pour les appareils inscrits après le 22 novembre 2019 et avant le déploiement de cette modification en mars : l’application Microsoft Intune est installée sur ces appareils. Les certificats SCEP déployés sur les appareils et associés à des profils Wi-Fi continuent à s’appliquer.
- Pour les nouvelles inscriptions d’appareils dédiés Android Enterprise après le déploiement de cette modification en mars : les utilisateurs finaux voient un autre ensemble d’étapes sur les appareils lors de l’inscription. L’inscription commencera comme aujourd’hui (code QR, NFC, Zero Touch ou identificateur d’appareil), mais il n’y aura pas d’étape obligatoire d’installation de l’application. L’application Microsoft Intune s’installera automatiquement sur les appareils. Par ailleurs, les utilisateurs finaux n’auront pas besoin d’appuyer sur « Activer l’agent Intune » au cours du processus. Les certificats SCEP associés à des profils Wi-Fi pourront être déployés sur ces appareils.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que faire pour me préparer à ce changement ?
Vous pouvez mettre à jour l’aide destinée à l’utilisateur final et informer votre support technique de cette modification. Nous allons mettre à jour notre page Nouveautés. Nous vous avertirons par le biais du Centre de messages du début du déploiement de cette modification.

#### <a name="additional-information"></a>Informations supplémentaires
[Prise en charge des certificats SCEP dans les appareils Android Enterprise dédiés](https://aka.ms/Dedicated_devices_enrollment)

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>Déclaration de prise en charge mise à jour pour l’application mobile « Adobe Acrobat Reader pour Intune »<!--5746776-->
Nous avons partagé dans notre MC188653 à la fin du mois d’août que l’application mobile Adobe Acrobat Reader pour Intune arriverait en fin de vie le 1er décembre 2019, et qu’Adobe planifiait la prise en charge des stratégies de protection des applications Intune au sein de son application Acrobat Reader principale. Depuis, nous avons reçu des commentaires de clients indiquant que nous avions besoin de temps pour continuer de permettre aux administrateurs informatiques de cibler, et aux utilisateurs finaux d’utiliser Adobe Acrobat Reader pour Intune. Compte tenu de l’utilisation intensive d’Adobe Acrobat Reader pour Intune sur les appareils des utilisateurs finaux et de son importance dans les scénarios d’entreprise, nous voulons nous assurer que toute expérience répond aux besoins de votre organisation en matière de protection des applications. 

Bien que nous recommandions toujours de cibler l’application mobile Acrobat Reader générale dans vos stratégies, puisque l’application mobile Acrobat Reader prend en charge les stratégies de protection des applications et a intégré le SDK Intune, l’application Adobe Acrobat Reader pour Intune continuera à être prise en charge jusqu’au 31 mars 2020. 

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
Vous recevez ce message, car nos rapports indiquent qu’une ou plusieurs stratégies de votre organisation ciblent l’application Adobe Acrobat Reader pour Intune et/ou que vous avez pu recevoir nos dernières communications relatives à sa fin de vie. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ?
Informez vos utilisateurs finaux et votre support technique de ce changement. Vous pouvez utiliser la [fonctionnalité d’informations de support du Portail d’entreprise](../apps/company-portal-app.md#support-information) pour établir un canal pour les questions liées à Intune.

#### <a name="additional-information"></a>Informations supplémentaires
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Fin de support pour Windows Phone 8.1<!--3544909-->
Le support standard de Microsoft pour Windows Phone 8.1 s’est terminé en juillet 2017, et le support étendu s’est terminé en juin 2019. L’application Portail d’entreprise pour Windows Phone 8.1 est en mode soutenu depuis octobre 2017. La prise en charge de Microsoft Intune se terminera le 20 février 2020 pour Windows Phone 8.1.

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
Après le 20 février 2020, ces appareils ne recevront aucune mise à jour de sécurité et vous ne pourrez pas inscrire de nouveaux appareils. Les appareils Windows Phone 8.1 existants resteront inscrits (stratégie, applications, rapports), mais notez que le dépannage d’une inscription existante ne sera plus pris en charge après cette date, car de nombreux composants, tels que les certificats tiers, n’ont déjà plus de support pour la plateforme. Intune arrêtera les tests de compatibilité avec Intune et Windows Phone 8.1.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ?
Vous pouvez vérifier vos rapports Intune pour voir quels appareils ou utilisateurs sont concernés. Accédez à Appareils > Tous les appareils, puis filtrez par système d’exploitation. Vous pouvez ajouter des colonnes supplémentaires pour aider à identifier les membres de votre organisation disposant d’appareils exécutant Windows Phone 8.1. Demandez aux utilisateurs finaux de mettre à niveau leurs appareils avec une version de système d’exploitation prise en charge.


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Action nécessaire : Utilisez Microsoft Edge pour votre expérience Protected Intune Browser<!--5728447-->
Comme annoncé au cours de l’année dernière, Microsoft Edge mobile prend en charge le même ensemble de fonctions de gestion que Managed Browser, tout en offrant une expérience de l’utilisateur final nettement améliorée. Pour faire place aux expériences robustes offertes par Microsoft Edge, nous allons retirer Intune Managed Browser. À partir du 27 janvier 2020, Intune ne prendra plus en charge Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ? 
À partir du 1er février 2020, Intune Managed Browser ne sera plus disponible dans le Google Play Store ni dans l’iOS App Store. À ce stade, vous pourrez toujours cibler les nouvelles stratégies de protection des applications sur Intune Managed Browser, mais les nouveaux utilisateurs ne pourront pas télécharger l’application Intune Managed Browser. De plus, sous iOS, les nouveaux clips web envoyés vers un appareil inscrit via MDM s'ouvriront dans Microsoft Edge au lieu d’Intune Managed Browser.  

Le 31 mars 2020, Intune Managed Browser sera retiré de la console Azure. Cela signifie que vous ne pourrez plus créer de nouvelles stratégies pour Intune Managed Browser. Si vous avez déjà mis en place des stratégies Intune Managed Browser, elles ne seront pas affectées. Intune Managed Browser s’affichera dans la console en tant qu’application métier sans icône, et les stratégies existantes s’afficheront toujours comment étant ciblées à l’application. À ce stade, nous supprimerons également l’option permettant de rediriger le contenu web vers Intune Managed Browser dans la section Protection des données des stratégies de protection des applications.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ? 
Pour assurer une transition en douceur entre Intune Managed Browser et Microsoft Edge, nous vous recommandons de prendre les mesures suivantes de manière proactive : 

1. Ciblez Microsoft Edge pour iOS et Android avec la stratégie de protection des applications (également appelée MAM) et les paramètres de configuration des applications. Vous pouvez réutiliser vos stratégies Intune Managed Browser pour Microsoft Edge en ciblant ces stratégies existantes également sur Microsoft Edge.  
2. Assurez-vous que le paramètre de stratégie de protection des applications « Restreindre le transfert de contenu web à d'autres applications » est défini sur « Navigateurs gérés par stratégie » pour toutes les applications protégées par MAM dans votre environnement. 
3. Ciblez tous les applications protégées par MAM en définissant le paramètre de configuration des applications gérées « com.microsoft.intune.useEdge » sur true. Dès le mois prochain avec la sortie de la version 1911, vous pourrez effectuer les étapes 2 et 3 simplement en définissant le paramètre « Restreindre le transfert de contenu web à d’autres applications » sur « Microsoft Edge » dans la section Protection des données de vos stratégies de protection des applications. 

La prise en charge des clips web sur iOS et Android sera bientôt disponible. Une cette prise en charge disponible, vous devrez recibler les clips web préexistants pour vous assurer qu’ils s’ouvrent dans Microsoft Edge au lieu de Managed Browser. 

#### <a name="additional-information"></a>Informations supplémentaires
Pour plus d’informations, consultez notre documentation sur [l’utilisation de Microsoft Edge avec les stratégies de protection des applications](../apps/manage-microsoft-edge.md), ou notre [billet de blog de support](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="end-of-support-for-legacy-pc-management"></a>Fin du support pour la gestion des PC hérités

La gestion des PC hérités ne sera plus prise en charge à partir du 15 octobre 2020. Mettez à niveau les appareils vers Windows 10 et réinscrivez-les en tant qu’appareils de gestion des appareils mobiles (MDM) pour qu’ils continuent d’être gérés par Intune.

[En savoir plus](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Diminution du support pour l’administrateur d’appareil Android 
L’administrateur d’appareil Android (parfois appelé gestion Android « héritée » et publiée avec Android 2.2) est un moyen de gérer les appareils Android. Toutefois, des fonctionnalités de gestion améliorées sont désormais disponibles avec [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (fournie avec Android 5.0). Dans le but de passer à une gestion des périphériques modernes, plus riche et plus sécurisée, Google diminue le support des administrateurs d’appareil dans les nouvelles versions Android.

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
En raison de ces modifications apportées par Google, les utilisateurs Intune seront affectés des manières suivantes :  
- Intune pourra uniquement assurer le support complet des appareils Android gérés par l’administrateur d’appareil exécutant Android 10 ou version ultérieure jusqu’au 2e trimestre 2020. Les appareils gérés par l’administrateur d’appareil qui exécutent Android 10 ou une version ultérieure après cette échéance ne pourront plus être entièrement gérés. En particulier, les appareils impactés ne recevront pas de nouvelles exigences en matière de mot de passe.
    - Les appareils Samsung Knox ne seront pas affectés dans ce laps de temps, car le support étendu est assuré via l’intégration d’Intune avec la plateforme Knox. Vous avez ainsi plus de temps pour planifier la transition de la gestion de l’administration des appareils.    
- Les appareils Android gérés par l’administrateur d’appareil qui restent sur les versions Android inférieures à Android 10 ne sont pas affectés et peuvent continuer à être entièrement gérés avec l’administrateur d’appareil.    
- Pour tous les appareils exécutant Android 10 et versions ultérieures, Google a limité la possibilité pour les agents de gestion des administrateurs d’appareil, notamment le Portail d’entreprise, d’accéder aux informations d’identification de l’appareil. Cette restriction a un impact sur les fonctionnalités Intune suivantes après la mise à jour d’un appareil vers Android 10 ou ultérieur :  
    - Le contrôle d’accès réseau pour VPN ne fonctionnera plus.   
    - L’identification des appareils comme appartenant à l’entreprise avec le numéro IMEI ou le numéro de série ne marque pas automatiquement les appareils comme appartenant à l’entreprise.  
    - Le numéro IMEI et le numéro de série ne seront plus visibles pour les administrateurs informatiques dans Intune. 
        > [!NOTE]
        > Cela affecte uniquement les appareils gérés par l’administrateur d’appareil sur Android 10 et versions ultérieures et n’affecte pas les appareils gérés comme Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ?
Pour éviter la réduction des fonctionnalités prévues pour le 3e trimestre 2020, nous vous recommandons les points suivants :
- N’intégrez pas de nouveaux appareils dans la gestion des administrateurs d’appareil.
- Si un appareil est censé recevoir une mise à jour d’Android 10, migrez-le de la gestion de l’administrateur d’appareil vers la gestion Android Enterprise et/ou des stratégies de protection d’application.

#### <a name="additional-information"></a>Informations supplémentaires
- [Aide de Google pour la migration de l’administrateur d’appareil vers Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentation Google sur le plan de dépréciation de l’API de l’administrateur d’appareil](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Modification planifiée : Les stratégies de protection des applications et du Kit de développement logiciel (SDK) des applications Intune pour Android évoluent vers le support d’Android 5.0 et versions ultérieures dans une version à venir <!--4911065 -->
Intune passera au support d’Android 5.x (lollipop) et versions ultérieures dans une version à venir. Mettez à jour les applications inclues dans un wrapper avec le dernier Kit de développement logiciel (SDK) des applications Intune et mettez à jour vos appareils.

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
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

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ?
Incluez dans un wrapper vos applications avec le dernier Kit de développement logiciel (SDK) d’application Intune. Vous pouvez également définir le paramètre de lancement conditionnel « Exiger une version minimale du système d’exploitation (avertissement uniquement) » pour informer les utilisateurs finaux des appareils personnels à mettre à niveau.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Modification planifiée d’Intune : Fin de la prise en charge de Windows 7<!-- 3042987 -->
Comme nous l'avons annoncé dans le message MC148476 publié en septembre 2018, et de nouveau dans le message MC176794 de mars 2019, la prise en charge étendue de Windows 7 cessera le 14 janvier 2020. À cette date, Intune arrêtera la prise en charge des appareils fonctionnant sous Windows 7 pour se concentrer sur ses investissements dans la prise en charge de nouvelles technologies et offrir une nouvelle expérience de qualité à ses utilisateurs finaux. Après cette date, l'assistance technique et les mises à jour automatiques qui aident à protéger votre PC Windows 7 ne seront plus disponibles via Intune. Microsoft vous recommande fortement de passer à Windows 10 avant janvier 2020 afin d'éviter un scénario où vous avez besoin d'un service ou d'une assistance qui n'est plus disponible. Cliquez [ici](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) pour en savoir plus sur le cycle de vie du support Windows.

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
Vous recevez ce message car vous gérez actuellement des PC Windows 7 à l'aide de l'ancien agent logiciel pour PC Intune. À moins d'un an de la fin de la prise en charge étendue de Windows 7, nous encourageons vivement votre entreprise à commencer dès que possible la mise à niveau vers Windows 10.  

Les capacités de gestion pour PC sont directement intégrées au système d'exploitation Windows 10 et vous n'avez plus besoin d'installer un agent client tel que le client logiciel Intune pour Windows 7. À partir de Windows 8.1, Microsoft utilise l'architecture MDM (Mobile Device Management) pour approvisionner, configurer, mettre à jour et gérer les PC Windows. Une fois que vous avez configuré Intune, vous pouvez simplifier l'inscription à Windows en [inscrivant les PC Windows 10 dans Intune](..\windows-enroll.md) via le canal MDM. Nous vous recommandons d'utiliser cette solution de gestion MDM « sans agent » pour gérer vos PC Windows 10.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ?
Nous encourageons votre entreprise à mettre en œuvre immédiatement ce plan d'action :

- Planifiez et mettez à niveau le parc de PC Windows 7 vers Windows 10 avant le 14 janvier 2020.
- Explorez la [prise en charge du déploiement Windows 10](https://docs.microsoft.com/windows/deployment/) pour en savoir plus sur la façon de mettre à niveau votre parc existant de PC Windows 7 vers Windows 10.
- Examinez l'offre [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) proposée par le biais de Fast Track, qui vous aidera à garantir la compatibilité des applications Microsoft.
- Faites évoluer vos actuels appareils gérés par le client logiciel Intune vers la solution recommandée par Microsoft pour gérer Windows 10 avec la gestion MDM. Inscrivez tous les nouveaux PC Windows 10 en utilisant la gestion MDM pour Intune dans le portail Azure.

Pour plus d’informations, consultez le [billet de blog ici](https://aka.ms/Windows7_Intune).


