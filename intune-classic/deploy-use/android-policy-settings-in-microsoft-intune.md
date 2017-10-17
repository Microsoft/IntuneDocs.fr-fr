---
title: "Paramètres de stratégie Android et Samsung KNOX"
description: "Créez des stratégies qui contrôlent les paramètres et fonctionnalités sur les appareils Android que vous gérez avec Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 10/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 502ee0f3107d197537f7f9ab3b2888246bbca1d3
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2017
---
# <a name="android-and-samsung-knox-standard-policy-settings-in-microsoft-intune"></a>Paramètres de la stratégie de configuration Android et Samsung KNOX Standard dans Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune fournit un éventail de paramètres généraux intégrés que vous pouvez configurer sur les appareils Android. Vous pouvez aussi spécifier des valeurs OMA-URI (Open Mobile Alliance Uniform Resource Identifier) pour créer des paramètres personnalisés qui ne sont pas disponibles à partir d’Intune.

## <a name="general-configuration-policy"></a>Stratégie de configuration générale

Utilisez la **stratégie de configuration générale Android** d’Intune pour configurer les paramètres suivants :

-   **Paramètres de sécurité des appareils mobiles** - Choisissez des paramètres dans une liste de paramètres prédéfinis qui vous permettent de contrôler diverses fonctions et fonctionnalités sur l’appareil.

-   **Mode plein écran** (appareils Samsung KNOX Standard uniquement) - Verrouillez un appareil pour n’autoriser que certaines fonctionnalités. Par exemple, vous pouvez autoriser un appareil à exécuter une seule application gérée que vous spécifiez ou désactiver les boutons du volume sur un appareil. Ces paramètres peuvent être utilisés pour le modèle de démonstration d’un appareil ou pour un appareil dédié à une seule fonction, par exemple dans un point de vente.

-   **Applications conformes et non conformes** - Spécifiez une liste d’applications conformes ou non conformes dans votre entreprise. Sur les appareils Android et iOS, le **Rapport sur les applications non conformes** peut être utilisé pour comparer la conformité des applications que vous avez spécifiées dans la liste aux applications que les utilisateurs ont installées. En fait, le rapport ne peut pas bloquer l’installation de l’application.

> [!TIP]
> Vous pouvez configurer les conditions générales pour vous assurer que les utilisateurs acceptent que toutes les applications sur leurs appareils, y compris les applications personnelles, soient évaluées et que les applications non conformes soient bloquées ou signalées non conformes. Les utilisateurs doivent accepter ces conditions générales avant de pouvoir inscrire leur appareil et utiliser le portail d'entreprise pour obtenir des applications. Pour plus d’informations sur l’utilisation des conditions générales, consultez [Paramètres de la stratégie de conditions générales dans Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Si le paramètre que vous recherchez n’est pas mentionné dans cette rubrique, vous pourrez peut-être le créer à l’aide d’une stratégie personnalisée Android qui vous permet d’utiliser des paramètres OMA-URI pour contrôler l’appareil. Pour plus d’informations, accédez à la section [Paramètres de stratégie personnalisée](#custom-policy-settings) plus loin dans cette rubrique.

### <a name="password-settings"></a>Paramètres de mot de passe

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|-|----------------|----------------|
|**Exiger un mot de passe pour déverrouiller des appareils mobiles**|Spécifie si un mot de passe est exigé sur les appareils pris en charge.|Oui|Oui|
|**Longueur minimale du mot de passe**|Spécifie la longueur minimale du mot de passe.|Oui|Oui|
|**Nombre d’échecs de connexion répétée autorisé avant réinitialisation de l’appareil**|Spécifie le nombre d’échecs de connexion à autoriser avant réinitialisation de l’appareil.|Oui|Oui|
|**Minutes d’inactivité avant arrêt de l’écran**|Spécifie le nombre de minutes d’inactivité avant verrouillage automatique de l’appareil.|Oui|Oui|
|**Expiration du mot de passe (jours)**|Spécifie le nombre de jours avant qu’un mot de passe ne doive être changé.|Oui|Oui|
|**Mémoriser l’historique des mots de passe**|Spécifie le nombre de mots de passe déjà utilisés à mémoriser.|Oui|Oui|
|**Mémoriser l'historique des mots de passe** - **Empêcher la réutilisation des mots de passe précédents**|Empêche la réutilisation des mots de passe précédents.|Oui|Oui|
|**Qualité du mot de passe**|Spécifie le niveau de complexité du mot de passe exigé et si les appareils biométriques peuvent être utilisés.|Oui|Oui|
|**Autoriser le déverrouillage par empreinte digitale**|Autorise l’utilisation d’une empreinte digitale pour déverrouiller l’appareil.|Non|Oui|
|**Autoriser Smart Lock et d’autres agents de confiance**<br>(Android 5 et versions ultérieures)|Permet de contrôler la fonctionnalité Smart Lock sur les appareils Android compatibles. Cette fonctionnalité du téléphone, parfois appelée agent de confiance, vous permet de désactiver ou de contourner le mot de passe de l’écran de verrouillage de l’appareil si celui-ci se trouve dans un emplacement fiable (par exemple, quand il est connecté à un appareil Bluetooth spécifique ou qu’il se trouve à proximité d’une balise NFC). Vous pouvez utiliser ce paramètre pour empêcher les utilisateurs de configurer Smart Lock.|Oui|Non|

### <a name="encryption-settings"></a>Paramètres de chiffrement

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Exiger le chiffrement sur l'appareil mobile**|Requiert que les fichiers de l'appareil mobile soient chiffrés.|Oui|Oui|
|**Exiger le chiffrement sur les cartes de stockage**|Spécifie si la carte de stockage de l’appareil doit être chiffrée.|Non|Oui|

### <a name="system-settings"></a>Paramètres système

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Autoriser la capture d’écran**|Autorise l’utilisateur à capturer le contenu de l’écran comme image.|Non|Oui|
|**Autoriser la soumission des données de diagnostic**|Autorise l’appareil à soumettre des informations de diagnostic à Google.|Non|Oui|
|**Autoriser la réinitialisation aux paramètres d’usine**|Autorise l’utilisateur à rétablir les paramètres d’usine sur l’appareil.|Non|Oui|

### <a name="cloud-settings---documents-and-data"></a>Paramètres du cloud - documents et données

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------------------|----------------|
|**Autoriser la sauvegarde Google**|Autorise l’utilisation de la sauvegarde de Google.|Non|Oui|

### <a name="cloud-settings---accounts-and-synchronization"></a>Paramètres du cloud - comptes et synchronisation

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Autoriser la synchronisation automatique de compte Google**|Autorise la synchronisation automatique des paramètres du compte Google.|Non|Oui|

### <a name="application-settings---browser"></a>Paramètres de l'application - navigateur

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Autoriser le navigateur web**|Spécifie si le navigateur web par défaut de l’appareil peut être utilisé.|Non|Oui|
|**Autoriser le remplissage automatique**|Autorise l’utilisation de la fonction de remplissage automatique du navigateur web.|Non|Oui|
|**Autoriser le bloqueur de fenêtres publicitaires**|Autoriser l’utilisation du bloqueur de fenêtres publicitaires dans le navigateur.|Non|Oui|
|**Autoriser les cookies**|Autorise le navigateur web de l’appareil à utiliser des cookies.|Non|Oui|
|**Autoriser les scripts actifs**|Autorise le navigateur web de l’appareil à utiliser Active Scripting.|Non|Oui|

### <a name="application-settings---apps"></a>Paramètres de l'application - applications

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Autoriser la boutique Google Play**|Autorise l’utilisateur à accéder à la Boutique Google Play sur l’appareil.|Non|Oui|

### <a name="device-capabilities-settings---hardware"></a>Paramètres des fonctionnalités de l'appareil - matériel

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Autoriser l’appareil photo**|Autorise l’utilisation de l’appareil photo de l’appareil.|Oui|Oui|
|**Autoriser le stockage amovible**|Autorise l’appareil à utiliser du stockage amovible, comme une carte SD.|Non|Oui|
|**Autoriser le Wi-Fi**|Autorise l’utilisation des fonctionnalités Wi-Fi de l’appareil.|Non|Oui|
|**Autoriser la connexion Wi-Fi**|Autorise l’utilisation de la connexion Wi-Fi sur l’appareil.|Non|Oui|
|**Autoriser la géolocalisation**|Permet à l'appareil d'utiliser les informations d'emplacement.|Non|Oui|
|**Autoriser NFC**|Autorise les opérations qui utilisent la communication en champ proche si l’appareil la prend en charge.|Non|Oui|
|**Autoriser Bluetooth**|Autorise l’utilisation de la fonction Bluetooth sur l’appareil.|Non|Oui|
|**Autoriser l’extinction**|Autorise l’utilisateur à mettre l’appareil hors tension.<br /><br />Si ce paramètre est désactivé, le paramètre **Nombre d’échecs de connexion successifs autorisé avant réinitialisation de l’appareil** pour les appareils Samsung KNOX Standard ne fonctionne pas.|Non|Oui|

### <a name="device-capabilities-settings---cellular"></a>Paramètres des fonctionnalités de l'appareil - cellulaire

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Autoriser l’itinérance vocale**|Autorise l’itinérance vocale quand l’appareil se trouve sur un réseau de téléphonie mobile.|Non|Oui|
|**Autoriser l’itinérance des données**|Autorise l’itinérance des données quand l’appareil se trouve sur un réseau de téléphonie mobile.|Non|Oui|
|**Autoriser les messages SMS/MMS**|Autorise l’utilisation de la messagerie SMS et MMS sur l’appareil.|Non|Oui|

### <a name="device-capabilities-settings---features"></a>Paramètres des fonctionnalités de l'appareil - fonctionnalités

|Nom du paramètre|Détails|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Autoriser l’assistant vocal**|Autorise l’utilisation du logiciel Assistant vocal sur l’appareil.|Non|Oui|
|**Autoriser la composition vocale**|Active ou désactive la fonctionnalité de numérotation vocale sur l’appareil.|Non|Oui|
|**Autoriser la fonction copier-coller**|Autorise les fonctions Copier et Coller sur l’appareil.|Non|Oui|
|**Autoriser le partage du Presse-papiers entre applications**|Autorise l’utilisation du Presse-papiers pour copier-coller entre les applications.|Non|Oui|
|**Autoriser YouTube**|Autorise l’utilisation de YouTube sur l’appareil.|Non|Oui|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Paramètres des applications conformes et non conformes
Dans la liste **Applications conformes &amp; non conformes**, spécifiez une liste d’applications conformes ou non conformes qui utilisent les informations suivantes :

> [!NOTE]
> Une stratégie ne peut contenir qu’une liste d’applications conformes ou une liste d’applications non conformes. Vous ne pouvez pas spécifier les deux dans la même stratégie.

|Nom du paramètre|Détails|
|----------------|--------------------|
|**Signaler une non-conformité quand les utilisateurs installent les applications listées**|Répertorie les applications qui ne sont pas gérées par Intune et que les utilisateurs ne sont pas autorisés à installer et à exécuter. Si les utilisateurs installent l’une de ces applications, elle apparaîtra dans le rapport sur les applications non conformes.|
|**Ne pas signaler une non-conformité quand les utilisateurs installent les applications listées**|Répertorie les applications que vous voulez autoriser. Pour rester conformes, les utilisateurs ne doivent pas installer d’applications qui ne sont pas répertoriées. Les applications qui sont gérées par Intune sont autorisées automatiquement.|
|**Ajouter**|Ajoute une application à la liste sélectionnée. Spécifiez le nom de l’application, l’éditeur de l’application (facultatif) et l’URL de l’application dans l’App Store.<br /><br />Pour plus d’informations, consultez [Spécifier les URL vers les App Stores](#specify-urls-to-app-stores) plus loin dans cette rubrique.|
|**Importer des applications**|Importe une liste d’applications que vous avez spécifiée dans un fichier de valeurs séparées par des virgules. Utilisez le format, le nom de l’application, l’éditeur et l’URL de l’application dans le fichier.|
|**Éditer**|Vous permet de modifier le nom, l’éditeur et l’URL de l’application sélectionnée.|
|**Supprimer**|Supprime l'application sélectionnée dans la liste.|

Les stratégies contenant des paramètres d’application conformes et non conformes doivent être déployés sur des groupes d’utilisateurs.

### <a name="kiosk-mode-settings"></a>Paramètres du mode plein écran
Spécifiez les paramètres suivants pour les **appareils Samsung KNOX Standard** :

|Nom du paramètre|Détails|
|----------------|--------------------|
|**Sélectionner une application gérée qui peut s’exécuter quand l’appareil est en mode plein écran**|Sélectionnez **Parcourir** et choisissez l’application gérée qui peut s’exécuter quand l’appareil est en mode plein écran (les applications spécifiées sous la forme d’un lien vers le magasin ne sont pas prises en charge). Aucune autre application ne pourra s'exécuter sur l'appareil.|
|**Autoriser les boutons de volume**|Active ou désactive l'utilisation des boutons de volume sur l'appareil.|
|**Activer le bouton Veille/sortie de veille de l’écran**|Active ou désactive le bouton Veille/sortie de veille de l'écran sur l'appareil.|

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Informations de référence pour les applications conformes et non conformes

#### <a name="monitor-compliant-and-noncompliant-apps"></a>Contrôler les applications conformes et non conformes
Utilisez le **Rapport sur les applications non conformes** pour afficher la conformité des applications autorisées et bloquées.

###### <a name="to-run-the-noncompliant-apps-report"></a>Pour exécuter le rapport sur les applications non conformes

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), sélectionnez **Rapports** &gt; **Rapport sur les applications non conformes**.

2.  Sélectionnez les groupes d’appareils que vous souhaitez vérifier. Décidez ensuite si vous souhaitez vérifier les applications conformes, les applications non conformes ou les deux. Enfin, choisissez **Afficher le rapport**.

#### <a name="specify-urls-to-app-stores"></a>Spécifier les URL vers les App Stores
Pour spécifier une URL d’application dans la liste des applications conformes et non conformes, procédez comme suit :

Dans la [section Applications de Google Play](https://play.google.com/store/apps), recherchez l’application à utiliser.

Ouvrez la page d’installation de l’application, puis copiez l’URL dans le Presse-papiers. Vous pouvez maintenant utiliser cette URL dans la liste des applications conformes ou non conformes.

Exemple : Recherchez Microsoft Office Mobile dans Google Play. L’URL que vous utilisez est **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## <a name="custom-policy-settings"></a>Paramètres de la stratégie personnalisée
Utilisez la **stratégie de configuration personnalisée Android** de Microsoft Intune pour déployer les paramètres OMA-URI qui peuvent être utilisés pour contrôler les fonctionnalités sur les appareils Android. Il s'agit de paramètres standard qui sont utilisés par de nombreux fabricants d'appareils mobiles pour contrôler les fonctionnalités des appareils.

Cette fonctionnalité est conçue pour vous permettre de déployer les paramètres Android qui ne sont pas configurables avec des stratégies Intune.
Intune prend en charge un nombre limité de stratégies personnalisées Android à l’heure actuelle. Consultez les exemples de cette rubrique pour savoir quelles stratégies vous pouvez configurer.

### <a name="general-settings"></a>Paramètres généraux :

|Nom du paramètre|Détails|
    |----------------|--------------------|
    | **Nom** |Entrez un nom unique pour la stratégie personnalisée Android pour pouvoir l’identifier dans la console Intune.|
    | **Description** |Fournissez une description générale de la stratégie personnalisée Android et d'autres informations pertinentes pour mieux la localiser.|

### <a name="oma-uri-settings"></a>Paramètres OMA-URI

   |Nom du paramètre|Détails|
    |--------|--------------------|
    | **Nom du paramètre** |Affectez un nom unique au paramètre OMA-URI pour vous aider à l'identifier dans la liste des paramètres.|
    | **Description du paramètre** |Entrez une description générale du paramètre et d'autres informations pertinentes pour faciliter sa localisation.|
    | **Type de données** |Sélectionnez le type de données pour lequel vous allez spécifier ce paramètre OMA-URI. Choisissez **Chaîne, Chaîne (XML), Date et heure, Entier, Virgule flottante** ou **Booléen**.|
    | **OMA-URI (sensible à la casse)** |Spécifiez l'identificateur OMA-URI pour lequel vous souhaitez fournir un paramètre.|
    | **Valeur** |Spécifiez la valeur à associer à l’identificateur OMA-URI spécifié précédemment.|

### <a name="examples"></a>Exemples

- [Création d’un profil Wi-Fi avec une clé prépartagée](pre-shared-key-wi-fi-profile.md)
- [Utiliser une stratégie personnalisée pour créer un profil VPN par application pour les appareils Android](per-app-vpn-for-android-pulse-secure.md)
- [Utiliser des stratégies personnalisées pour autoriser et bloquer des applications pour les appareils Samsung KNOX](custom-policy-to-allow-and-block-samsung-knox-apps.md)

## <a name="supported-samsung-knox-standard-devices"></a>Appareils Samsung KNOX Standard pris en charge

L’application Portail d’entreprise tente l’activation de Samsung KNOX lors de l’inscription à MDM si l’appareil figure dans la [liste des appareils KNOX pris en charge](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Ceci permet d’éviter les erreurs d’activation de KNOX qui empêchent l’inscription à MDM. Les appareils qui ne prennent pas en charge l’activation de Samsung KNOX s’inscrivent en tant qu’appareils Android standard. Les appareils Samsung peuvent avoir des numéros de modèles qui prennent en charge KNOX, alors que d’autres ne le prennent pas en charge. Vérifiez la compatibilité de KNOX auprès du revendeur de votre appareil avant d’acheter et de déployer des appareils Samsung.

La liste suivante contient les modèles d’appareils Samsung qui ne prennent pas en charge KNOX et qui sont inscrits en tant qu’appareils Android natifs par l’application Portail d’entreprise pour Android :

| **Nom de l’appareil** | **Numéros de modèle de l’appareil** |
| --- | --- |
| Galaxy A3 | SM-A300G<br>SM-A310Y<br>SM-A320FL |
| Galaxy A5 | SM-A500G |
| Galaxy Alpha | SM-G850M |
| Galaxy Avant | SM-G386T |
| Galaxy C9/C9 Pro | SM-C900F |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime | SM-G530M |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M<br>SM-J320W8 |
| Galaxy J5 | SM-J500G |
| Galaxy J7 | SM-J710F |
| Galaxy J7 Prime | SM-J727T1 |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 5 | SM-N920G<br>SM-N920I<br>SM-N920W8 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy NotePRO 12.2&quot; | SM-P902 |
| Galaxy On5 | SM-G570MSM-G570Y |
| Galaxy On7 | SM-G600FY<br>SM-G610M<br>SM-G610Y |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Active | GT-I9295 |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W<br>SM-G900M |
| Galaxy S5 Neo | SM-G903M |
| Galaxy S6 Edge | 404SCSM-G925I<br>SM-G928G |
| Galaxy Tab A 7.0&quot; | SM-T280SM-T285 |
| Galaxy Tab A 9.7&quot; | SM-P555M |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116SM-T210SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |



### <a name="see-also"></a>Voir aussi
[Gérer des paramètres et des fonctionnalités sur vos appareils avec des stratégies Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
