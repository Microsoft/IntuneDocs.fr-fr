---
title: fichier descriptif
description: inclure fichier
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 373aeea9ab4fcbd075ac2ab18f205f3ddd191a39
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609270"
---
Ces remarques fournissent des informations importantes qui peuvent vous aider à préparer de futures modifications et fonctionnalités Intune.

### <a name="microsoft-intune-support-for-windows-10-mobile-ending--3544938--"></a>Fin de la prise en charge de Microsoft Intune pour Windows 10 Mobile<!--3544938-->
La prise en charge standard Microsoft pour Windows 10 Mobile s’est terminée en décembre 2019. Comme indiqué dans cette déclaration de prise en charge, les utilisateurs de Windows 10 Mobile ne pourront plus recevoir de nouvelles mises à jour de sécurité, de correctifs non liés à la sécurité, d’options de support assisté gratuites ou de mises à jour de contenu technique en ligne de Microsoft. Conformément à la prise en charge du système d’exploitation complet Mobile, Microsoft Intune mettra fin à la prise en charge du Portail d’entreprise pour l’application Windows 10 Mobile et du système d’exploitation Windows 10 Mobile le 11 mai 2020.

#### <a name="how-does-this-affect-me"></a>Dans quelle mesure suis-je affecté ?
Si vous avez déployé des appareils Windows 10 Mobile dans votre organisation, entre aujourd’hui et le 11 mai 2020, vous pouvez inscrire de nouveaux appareils, ajouter ou supprimer des stratégies et des applications, ou mettre à jour les paramètres de gestion. Après le 11 mai, nous mettrons fin aux nouvelles inscriptions et supprimerons à terme la gestion de Windows 10 Mobile de l’interface utilisateur Intune. Les appareils ne seront plus enregistrés dans le service Intune et nous supprimerons les données d’appareil et de stratégie.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que faire pour se préparer à ce changement ?
Vous pouvez vérifier vos rapports Intune pour voir quels appareils ou utilisateurs sont concernés. Accédez à **Appareils** > **Tous les appareils**, puis filtrez par Système d’exploitation. Vous pouvez ajouter des colonnes supplémentaires pour aider à identifier les membres de votre organisation disposant d’appareils exécutant Windows 10 Mobile. Demandez à vos utilisateurs finaux de mettre à niveau leurs appareils ou de cesser d’utiliser les appareils pour un accès professionnel.



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

### <a name="decreasing-support-for-android-device-administrator--5857738--"></a>Diminution du support pour l’administrateur d’appareil Android<!--5857738-->
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



