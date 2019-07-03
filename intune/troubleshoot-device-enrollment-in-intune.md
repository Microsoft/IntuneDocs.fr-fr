---
title: Résoudre les problèmes d’inscription d’appareils
titleSuffix: Microsoft Intune
description: Suggestions pour résoudre les problèmes liés à l’inscription d’appareils dans Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/09/2018
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6982ba0e-90ff-4fc4-9594-55797e504b62
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 063a288c99f3f773b63bd6fe0040e200a754c888
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67046303"
---
# <a name="troubleshoot-device-enrollment-in-microsoft-intune"></a>Résoudre les problèmes d’inscription d’appareils dans Microsoft Intune

Cet article fournit des suggestions pour résoudre les problèmes liés à l’[inscription d’appareils](device-enrollment.md). Si ces informations ne vous permettent pas de remédier au problème, consultez [Guide pratique pour obtenir un support technique pour Microsoft Intune](get-support.md) afin d’accéder à d’autres types d’assistance.


## <a name="initial-troubleshooting-steps"></a>Étapes initiales de dépannage

Avant de commencer le dépannage, vérifiez que vous avez configuré Intune correctement pour activer l’inscription. Vous pouvez consulter ces exigences de configuration dans les rubriques suivantes :

-   [Se préparer à inscrire des appareils dans Microsoft Intune](setup-steps.md)
-   [Configurer la gestion des appareils iOS et Mac](ios-enroll.md)
-   [Configurer la gestion des appareils Windows](windows-enroll.md)
-   [Configurer la gestion des appareils Android](android-enroll.md) -aucune étape supplémentaire requise

Vous pouvez également vérifier que l’heure et la date sur l’appareil de l’utilisateur sont correctement définies :

1. Redémarrez l’appareil.
2. Vérifiez que la date et l’heure sont définies selon les normes GMT (+ ou - 12 heures) pour le fuseau horaire de l’utilisateur final.
3. Désinstallez et réinstallez le portail d’entreprise Intune (le cas échéant).

Les utilisateurs d’appareils gérés peuvent recueillir des journaux d’inscription et de diagnostic qui peuvent vous être utiles. Les instructions destinées aux utilisateurs permettant de recueillir les journaux sont fournies dans :

- [Envoyer les erreurs d’inscription Android à votre administrateur informatique](https://docs.microsoft.com/intune-user-help/send-enrollment-errors-to-your-it-admin-android)
- [Envoyer les erreurs iOS à votre administrateur informatique](https://docs.microsoft.com/intune-user-help/send-errors-to-your-it-admin-ios)


## <a name="general-enrollment-issues"></a>Problèmes généraux d’inscription
Ces problèmes peuvent se produire sur toutes les plateformes.

### <a name="device-cap-reached"></a>Plafond d’appareils atteint
**Problème :** Un utilisateur reçoit une erreur durant l’inscription (par exemple **Portail d’entreprise temporairement indisponible**), et le journal DMPdownloader.log de Configuration Manager contient l’erreur **DeviceCapReached**.

**Résolution :**

#### <a name="check-number-of-devices-enrolled-and-allowed"></a>Vérifier le nombre d’appareils inscrits et le nombre autorisé

Vérifiez si le nombre d’appareils affectés à l’utilisateur n’est pas supérieur au nombre maximal. Pour cela, effectuez les étapes suivantes :

1. Dans Intune, choisissez **Inscription de l’appareil** > **Restrictions d’inscription** > **Restrictions de limite d’appareils**. Notez la valeur dans la colonne **Limite d’appareils**.

2. Dans Intune, choisissez **Utilisateurs** > **Tous les utilisateurs** > sélectionnez l’utilisateur > **Appareils**. Notez le nombre d’appareils.

3. Si le nombre d’appareils inscrits de l’utilisateur est déjà égal à la restriction de limite d’appareils, aucun autre appareil ne peut être inscrit, sauf si :
    - [vous supprimez des appareils existants](devices-wipe.md) ;
    - vous augmentez la limite d’appareils en [modifiant la restriction de limite d’appareils](enrollment-restrictions-set.md#set-device-limit-restrictions).

Pour éviter d’atteindre le nombre maximal d’appareils, supprimez les enregistrements d’appareils obsolètes.

> [!NOTE]
> 
> Pour éviter d’atteindre le plafond d’inscription d’appareils, vous pouvez utiliser le compte de gestionnaire d’inscription d’appareil, comme décrit dans [Inscrire des appareils d’entreprise avec le gestionnaire d’inscription d’appareil dans Microsoft Intune](device-enrollment-manager-enroll.md).
> 
> Un compte d’utilisateur ajouté au compte des gestionnaires d’inscription d’appareil ne peut pas effectuer d’inscription si la stratégie d’accès conditionnel est appliquée à cette connexion d’utilisateur spécifique.

### <a name="company-portal-temporarily-unavailable"></a>Portail d’entreprise temporairement indisponible
**Problème :** Les utilisateurs reçoivent l’erreur **Portail d’entreprise temporairement indisponible** sur leur appareil.

**Résolution :**

1.  Supprimez l’application Portail d’entreprise Intune de l’appareil.

2.  Sur l’appareil, ouvrez le navigateur, accédez à [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com), puis essayez d’effectuer une connexion utilisateur.

3.  Si la connexion échoue, l’utilisateur peut essayer un autre réseau.

4.  En cas d’échec, vérifiez que les informations d’identification de l’utilisateur ont bien été synchronisées avec Azure Active Directory.

5.  Si la connexion aboutit, l’appareil iOS vous invite à installer l’application Portail d’entreprise Intune et à procéder à l’inscription. Sur un appareil Android, vous devez d’abord installer manuellement l’application Portail d’entreprise Intune avant de retenter l’inscription.

### <a name="mdm-authority-not-defined"></a>Autorité MDM non définie
**Problème :** Un utilisateur reçoit l’erreur **Autorité MDM non définie**.

**Résolution :**

1.  Vérifier que l’autorité MDM est [correctement définie](mdm-authority-set.md).
    
2.  Vérifiez que les informations d’identification de l’utilisateur ont été correctement synchronisées avec Azure Active Directory. Vous pouvez vérifier que l’UPN de l’utilisateur correspond aux informations Active Directory dans le centre d’administration Microsoft 365.
    Si l’UPN ne correspond pas aux informations Active Directory :

    1.  Désactivez DirSync sur le serveur local.

    2.  Supprimez l’utilisateur en question de la liste d’utilisateurs du **Portail de compte Intune** .

    3.  Patientez environ une heure avant que le service Azure supprime les données incorrectes.

    4.  Réactivez DirSync et vérifiez que l’utilisateur est à présent correctement synchronisé.

3.  Dans le cas où vous utilisez System Center Configuration Manager avec Intune, vérifiez que l’utilisateur dispose d’un identifiant utilisateur Cloud valide :

    1.  Ouvrez SQL Management Studio.

    2.  Connectez-vous à la base de données appropriée.

    3.  Ouvrez le dossier de bases de données, recherchez et ouvrez le dossier **CM_DBName**, DBName représentant le nom de la base de données client.

    4.  Dans la partie supérieure, choisissez **Nouvelle requête** et exécutez les requêtes suivantes :

        -   Pour afficher tous les utilisateurs : `select * from [CM_ DBName].[dbo].[User_DISC]`

        -   Pour afficher des utilisateurs spécifiques, utilisez la requête suivante, où %testuser1% est un espace réservé correspondant à username@domain.com pour l’utilisateur que vous recherchez : `select * from [CM_ DBName].[dbo].[User_DISC] where User_Principal_Name0 like '%testuser1%'`

        Après avoir écrit la requête, choisissez **!Execute**.
        Une fois que les résultats ont été retournés, recherchez l’ID d’utilisateur cloud.  Si vous n’en trouvez pas, c’est que l’utilisateur n’a pas de licence Intune.

### <a name="unable-to-create-policy-or-enroll-devices-if-the-company-name-contains-special-characters"></a>Impossible de créer une stratégie ou d’inscrire des appareils si le nom de l’entreprise contient des caractères spéciaux
**Problème :** Vous ne pouvez pas créer de stratégies, ni inscrire d’appareils.

**Résolution :** Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com/), supprimez les caractères spéciaux dans le nom de l’entreprise et enregistrez les informations de l’entreprise.

### <a name="unable-to-sign-in-or-enroll-devices-when-you-have-multiple-verified-domains"></a>Impossible de se connecter ou d’inscrire des appareils quand vous avez plusieurs domaines vérifiés
**Problème :** Ce problème peut se produire quand vous ajoutez un deuxième domaine vérifié à votre ADFS. Les utilisateurs dotés du suffixe UPN (nom d’utilisateur principal) du deuxième domaine risquent de ne pas pouvoir se connecter aux portails ou d’inscrire des appareils.


<strong>Résolution :</strong> Les clients Microsoft Office 365 doivent déployer une instance distincte du service de fédération AD FS 2.0 pour chaque suffixe :
- S’ils utilisent SSO (authentification unique) via AD FS 2.0, et
- S’ils ont plusieurs domaines de premier niveau pour les suffixes UPN des utilisateurs dans l’organisation (par exemple @contoso.com ou @fabrikam.com)


Un [correctif cumulatif pour AD FS 2.0](http://support.microsoft.com/kb/2607496) fonctionne conjointement avec le commutateur <strong>SupportMultipleDomain</strong> pour permettre au serveur AD FS de prendre en charge ce scénario sans nécessiter d’autres serveurs AD FS 2.0. Pour plus d’informations, consultez [ce blog](https://blogs.technet.microsoft.com/abizerh/2013/02/05/supportmultipledomain-switch-when-managing-sso-to-office-365/).


## <a name="android-issues"></a>Problèmes Android

### <a name="android-enrollment-errors"></a>Erreurs d’inscription Android

Le tableau suivant répertorie les erreurs auxquelles les utilisateurs finaux peuvent être confrontés durant l’inscription d’appareils Android dans Intune.

|Message d'erreur|Problème|Résolution|
|---|---|---|
|**L’administrateur informatique doit affecter une licence pour autoriser l’accès**<br>Votre administrateur informatique ne vous a pas accordé l’accès à cette application. Demandez-lui de l’aide ou réessayez plus tard.|Impossible d’inscrire l’appareil, car le compte de l’utilisateur ne dispose pas de la licence nécessaire.|Pour que les utilisateurs puissent inscrire leurs appareils, ils doivent avoir reçu la licence nécessaire. Ce message signifie qu’ils ont un type de licence incorrect pour l’autorité de gestion des appareils mobiles. Par exemple, ils voient cette erreur si les deux conditions suivantes sont remplies :<ol><li>Intune a été défini en tant qu’autorité de gestion des appareils mobiles</li><li>Ils utilisent une licence System Center 2012 R2 Configuration Manager.</li></ol>Pour plus d’informations, consultez [Attribuer des licences Intune à vos comptes d’utilisateur](/intune/licenses-assign).|
|**L’administrateur informatique doit définir une autorité MDM**<br>Apparemment, votre administrateur informatique n’a pas défini d’autorité MDM. Demandez-lui de l’aide ou réessayez plus tard.|L’autorité de gestion des appareils mobiles n’a pas été définie.|L’autorité de gestion des appareils mobiles n’a pas été définie dans Intune. Découvrez comment [définir l’autorité de gestion des appareils mobiles](/intune/mdm-authority-set).|


### <a name="devices-fail-to-check-in-with-the-intune-service-and-display-as-unhealthy-in-the-intune-admin-console"></a>Les appareils ne parviennent pas à se connecter au service Intune et affichent le message « Défectueux » dans la console d’administration Intune
**Problème :** Certains appareils Samsung exécutant des versions Android 4.4.x et 5.x peuvent interrompre la connexion au service Intune. Si les appareils ne sont pas connectés :

- Ils ne peuvent pas recevoir la stratégie, les applications et les commandes à distance du service Intune.
- Ils affichent un état de gestion **Défectueux** dans la console Administrateur.
- Les utilisateurs qui sont protégés par des stratégies d’accès conditionnel peuvent perdre l’accès aux ressources d’entreprise.

Le logiciel Samsung Smart Manager, fourni sur certains appareils Samsung, peut désactiver le Portail d’entreprise Intune et ses composants. Quand le portail d’entreprise est désactivé, il ne peut pas s’exécuter en arrière-plan, ni contacter le service Intune.

**Résolution #1 :**

Demandez à vos utilisateurs de démarrer manuellement l’application Portail d’entreprise. Une fois l’application redémarrée, l’appareil se connecte au service Intune.

> [!IMPORTANT]
> L’ouverture manuelle de l’application Portail d’entreprise est une solution temporaire, car Samsung Smart Manager peut la désactiver de nouveau.

**Résolution #2 :**

Demandez à vos utilisateurs de tenter la mise à niveau vers Android 6.0. Le problème de désactivation ne se produit pas sur les appareils Android 6.0. Pour vérifier si une mise à jour est disponible, accédez à **Paramètres** > **À propos de l’appareil** > **Télécharger manuellement des mises à jour** > suivez les instructions.

**Résolution #3 :**

Si la résolution #2 ne fonctionne pas, indiquez à vos utilisateurs de suivre ces étapes afin que Smart Manager exclue l’application Portail d’entreprise :

1. Lancez l’application Smart Manager sur l’appareil.

   ![Sélectionner l’icône Smart Manager sur l’appareil](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-icon.png)

2. Choisissez la vignette **Batterie**.

   ![Sélectionner la vignette Batterie](./media/troubleshoot-device-enrollment-in-intune/smart-manager-battery-tile.png)

3. Sous **Économie d’énergie de l’application** ou **Optimisation de l’application**, sélectionnez **Détail**.

   ![Sélectionner Détail sous Économie d’énergie de l’application ou Optimisation de l’application](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-power-saving-detail.png)

4. Choisissez **Portail d’entreprise** dans la liste des applications.

   ![Sélectionner Portail d’entreprise dans la liste des applications](./media/troubleshoot-device-enrollment-in-intune/smart-manager-company-portal.png)

5. Choisissez **Désactivé**.

   ![Sélectionner Désactivé dans la boîte de dialogue Optimisation de l’application](./media/troubleshoot-device-enrollment-in-intune/smart-manager-app-optimization-turned-off.png)

6. Sous **Économie d’énergie de l’application** ou **Optimisation de l’application**, vérifiez que le portail d’entreprise est désactivé.

   ![Vérifier que le portail d’entreprise est désactivé](./media/troubleshoot-device-enrollment-in-intune/smart-manager-verify-comp-portal-turned-off.png)


### <a name="profile-installation-failed"></a>Échec de l’installation du profil
**Problème :** Un utilisateur reçoit l’erreur **Échec de l’installation du profil** sur un appareil Android.

**Résolution :**

1.  Vérifiez que l’utilisateur a reçu une licence appropriée pour la version du service Intune que vous utilisez.

2.  Vérifiez que l’appareil n’est pas déjà inscrit auprès d’un autre fournisseur MDM.

3. Vérifiez qu’un profil de gestion n’est pas déjà installé sur l’appareil.

4.  Vérifiez que Chrome pour Android est le navigateur par défaut et que les cookies sont activés.

### <a name="android-certificate-issues"></a>Problèmes touchant les certificats Android

**Problème** : Les utilisateurs reçoivent le message suivant sur leur appareil : *Vous ne pouvez pas vous connecter, car il manque un certificat obligatoire à votre appareil.*

**Résolution 1**:

L’utilisateur peut récupérer le certificat manquant en suivant les instructions de la rubrique [Un certificat obligatoire est manquant sur votre appareil](/intune-user-help/your-device-is-missing-a-required-certificate-android). Si l’erreur persiste, essayez la résolution 2.

**Résolution 2** :

Une fois que les utilisateurs ont entré leurs informations d’identification d’entreprise, et qu’ils ont été redirigés vers une connexion fédérée, ils continuent parfois à voir l’erreur relative au certificat manquant. Dans ce cas, l’erreur peut signifier qu’il manque un certificat intermédiaire sur votre serveur AD FS (Active Directory Federation Services).

L’erreur de certificat se produit car les appareils Android nécessitent l’inclusion de certificats intermédiaires dans un message [hello de serveur SSL](https://technet.microsoft.com/library/cc783349.aspx), mais actuellement une installation de serveur AD FS ou WAP ou de serveur Proxy AD FS par défaut envoie uniquement le certificat SSL du service AD FS dans la réponse hello de serveur SSL à une demande hello de client SSL.

Pour résoudre ce problème, importez les certificats dans les certificats personnels de l’ordinateur sur les proxys ou le serveur AD FS en procédant comme suit :

1.  Sur les serveurs ADFS et proxy, cliquez avec le bouton droit sur **Démarrer** > **Exécuter** > **certlm.msc** pour lancer la console de gestion des certificats de l’ordinateur local.
2.  Développez **Personnel** et choisissez **Certificats**.
3.  Recherchez le certificat pour votre communication avec le service AD FS (un certificat signé publiquement) et double-cliquez dessus pour afficher ses propriétés.
4.  Choisissez l’onglet **Chemin d’accès de certification** pour afficher les certificats parents du certificat.
5.  Sur chaque certificat parent, choisissez **Afficher le certificat**.
6.  Choisissez **Détails** > **Copier dans un fichier**.
7.  Suivez les invites de l’Assistant pour exporter ou enregistrer la clé publique du certificat parent dans l’emplacement de fichier de votre choix.
8.  Cliquez avec le bouton droit sur **Certificats** > **Toutes les tâches** > **Importer**.
9.  Suivez les invites de l’assistant pour importer le(s) certificat(s) parent(s) dans **Local Computer\Personal\Certificates**.
10. Redémarrez les serveurs AD FS.
11. Répétez les étapes ci-dessus sur tous les serveurs proxy et AD FS.

Pour vérifier la bonne installation d’un certificat, vous pouvez utiliser l’outil de diagnostic disponible sur [https://www.digicert.com/help/](https://www.digicert.com/help/). Dans le champ **Adresse du serveur**, entrez le nom de domaine complet de votre serveur ADFS (par exemple, sts.contso.com), puis cliquez sur **Check Server**.

**Pour vérifier que le certificat a été installé correctement** :

Les étapes suivantes décrivent l’une des nombreuses méthodes et outils permettant de vérifier que le certificat a été installé correctement.

1. Accédez à l’[outil gratuit Digicert](ttps://www.digicert.com/help/).
2. Entrez le nom de domaine complet de votre serveur AD FS (par exemple, sts.contoso.com), puis sélectionnez **CHECK SERVER**.

Si le certificat de serveur est installé correctement, toutes les coches s’affichent dans les résultats. Si le problème ci-dessus se produit, un X rouge apparaît dans les sections « Certificate Name Matches » et « SSL Certificate is correctly Installed » du rapport.


## <a name="ios-issues"></a>Problèmes iOS

### <a name="ios-enrollment-errors"></a>Erreurs d'inscription iOS
Le tableau suivant répertorie les erreurs que les utilisateurs finaux peuvent rencontrer lors de l’inscription d’appareils iOS dans Intune.

|Message d'erreur|Problème|Résolution|
|-------------|-----|----------|
|NoEnrollmentPolicy|Aucune stratégie d’inscription détectée|Vérifiez que tous les prérequis de l’inscription, comme le certificat Apple Push Notification Service (APNs), ont été configurés et que l’option « iOS comme plateforme » est activée. Pour obtenir des instructions, consultez [Configurer la gestion des appareils iOS et Mac](ios-enroll.md).|
|DeviceCapReached|Vous avez trop d’appareils mobiles déjà inscrits.|L’utilisateur doit supprimer un de ses appareils mobiles actuellement inscrits du portail d’entreprise avant d’en inscrire un autre. Consultez les instructions correspondant au type d’appareil que vous utilisez : [Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android), [iOS](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-ios), [Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-windows).|
|APNSCertificateNotValid|En raison d’un problème lié au certificat, l’appareil mobile peut communiquer avec le réseau de votre entreprise.<br /><br />|Le service APNs (Apple Push Notification Service) fournit un canal permettant de contacter les appareils iOS inscrits. L’inscription n’aboutit pas, et ce message s’affiche si :<ul><li>Les étapes d’obtention d’un certificat APNs n’ont pas été effectuées, ou</li><li>Le certificat APNs est arrivé à expiration</li></ul>Passez en revue les informations sur la façon de configurer les utilisateurs dans les rubriques [Synchroniser Active Directory et ajouter des utilisateurs à Intune](users-add.md) et [Organisation des utilisateurs et des appareils](groups-add.md).|
|AccountNotOnboarded|En raison d’un problème lié au certificat, l’appareil mobile peut communiquer avec le réseau de votre entreprise.<br /><br />|Le service APNs (Apple Push Notification Service) fournit un canal permettant de contacter les appareils iOS inscrits. L’inscription n’aboutit pas, et ce message s’affiche si :<ul><li>Les étapes d’obtention d’un certificat APNs n’ont pas été effectuées, ou</li><li>Le certificat APNs est arrivé à expiration</li></ul>Pour plus d’informations, consultez [Configurer la gestion des appareils iOS et Mac avec Microsoft Intune](ios-enroll.md).|
|DeviceTypeNotSupported|L’utilisateur a peut-être tenté une inscription en utilisant un appareil non-iOS. Le type d’appareil mobile que vous essayez d’inscrire n’est pas pris en charge.<br /><br />Vérifiez que l’appareil exécute iOS version 8.0 ou ultérieure.<br /><br />|Vérifiez que l’appareil de l’utilisateur exécute iOS version 8.0 ou ultérieure.|
|UserLicenseTypeInvalid|Impossible d’inscrire l’appareil, car le compte de l’utilisateur n’est pas encore membre d’un groupe d’utilisateurs obligatoire.<br /><br />|Pour pouvoir inscrire leurs appareils, les utilisateurs doivent être membres du groupe d’utilisateurs approprié. Ce message signifie qu’ils ont un type de licence incorrect pour l’autorité de gestion des appareils mobiles. Par exemple, ils voient cette erreur si les deux conditions suivantes sont remplies :<ol><li>Intune a été défini en tant qu’autorité de gestion des appareils mobiles</li><li>Ils utilisent une licence System Center 2012 R2 Configuration Manager</li></ol>Pour plus d’informations, passez en revue les articles suivants :<br /><br />Consultez [Configurer la gestion des appareils iOS et Mac avec Microsoft Intune](ios-enroll.md) et passez en revue les informations sur la façon de configurer les utilisateurs dans [Synchroniser Active Directory et ajouter des utilisateurs à Intune](users-add.md) et [Organisation des utilisateurs et des appareils](groups-add.md).|
|MdmAuthorityNotDefined|L’autorité de gestion des appareils mobiles n’a pas été définie.<br /><br />|L’autorité de gestion des appareils mobiles n’a pas été définie dans Intune.<br /><br />Examinez l’élément 1 de la section « Étape 6 : Inscrire des appareils mobiles et installer une application » dans [Démarrage rapide : Essayer gratuitement Microsoft Intune pendant 30 jours](free-trial-sign-up.md).|

### <a name="devices-are-inactive-or-the-admin-console-cant-communicate-with-them"></a>Les appareils sont inactifs ou la console d’administration ne peut pas communiquer avec eux
**Problème :** Les appareils iOS ne sont pas enregistrés auprès du service Intune. Les appareils doivent être régulièrement enregistrés auprès du service pour conserver l’accès aux ressources d’entreprise protégées. Si les appareils ne sont pas enregistrés :

- Ils ne peuvent pas recevoir la stratégie, les applications et les commandes à distance du service Intune.
- Ils affichent un état de gestion **Défectueux** dans la console Administrateur.
- Les utilisateurs qui sont protégés par des stratégies d’accès conditionnel peuvent perdre l’accès aux ressources d’entreprise.

**Résolution :** Partagez les solutions suivantes avec les utilisateurs finaux pour les aider à récupérer l’accès aux ressources d’entreprise.

Quand les utilisateurs démarrent l’application Portail d’entreprise iOS, celle-ci peut leur indiquer si leur appareil a perdu le contact avec Intune. Si elle détecte une absence de contact, elle essaie automatiquement de se synchroniser avec Intune pour se reconnecter (les utilisateurs voient le message **Tentative de synchronisation** s’afficher).

  ![Notification Tentative de synchronisation](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_trying_to_sync_notification.png)

Si la synchronisation est réussie, la notification en ligne **Synchronisation réussie** s’affiche dans l’application Portail d’entreprise iOS, indiquant que votre appareil est dans un état d’intégrité correct.

  ![Notification Synchronisation réussie](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_sync_successful_notification.png)

Si la synchronisation échoue, la notification en ligne **Synchronisation impossible** s’affiche dans l’application Portail d’entreprise iOS.

  ![Notification Synchronisation impossible](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_unable_to_sync_notification.png)

Pour résoudre le problème, les utilisateurs doivent sélectionner le bouton **Configurer** qui apparaît à droite de la notification **Synchronisation impossible**. Le bouton Configurer dirige les utilisateurs vers l’écran de flux de configuration de l’accès à l’entreprise, où ils peuvent suivre les invites pour inscrire leur appareil.

  ![Écran de configuration de l’accès à l’entreprise](./media/troubleshoot-device-enrollment-in-intune/ios_cp_app_company_access_setup.png)

Une fois inscrits, les appareils retrouvent un état d’intégrité correct et récupèrent l’accès aux ressources d’entreprise.

### <a name="verify-ws-trust-13-is-enabled"></a>Vérifier que WS-Trust 1.3 est activé
**Problème** : les appareils iOS DEP (Programme d’inscription des appareils) d’Apple ne peuvent pas être inscrits

Dans le cas de l’inscription d’appareils DEP avec affinité utilisateur, vous devez activer un point de terminaison WS-Trust 1.3 Username/Mixed pour demander des jetons utilisateur. Active Directory active ce point de terminaison par défaut. Pour obtenir une liste de points de terminaison activés, utilisez l’applet de commande PowerShell Get-AdfsEndpoint et recherchez le point de terminaison trust/13/UsernameMixed. Par exemple :

      Get-AdfsEndpoint -AddressPath “/adfs/services/trust/13/UsernameMixed”

Pour plus d’informations, consultez la [documentation Get-AdfsEndpoint](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

Pour plus d’informations, consultez [Meilleures pratiques pour la sécurisation des services de fédération Active Directory](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/operations/best-practices-securing-ad-fs). Pour déterminer si WS-Trust 1.3 Username/Mixed est activé dans votre fournisseur de fédération des identités :
- Contactez le Support Microsoft si vous utilisez ADFS
- Contactez votre fournisseur d’identités tiers


### <a name="profile-installation-failed"></a>Échec de l’installation du profil
**Problème :** Un utilisateur reçoit l’erreur **Échec de l’installation du profil** sur un appareil iOS.

### <a name="troubleshooting-steps-for-failed-profile-installation"></a>Procédure de dépannage en cas d’échec de l’installation d’un profil

1.  Vérifiez que l’utilisateur a reçu une licence appropriée pour la version du service Intune que vous utilisez.

2.  Vérifiez que l’appareil n’est pas déjà inscrit auprès d’un autre fournisseur MDM.

3. Vérifiez qu’un profil de gestion n’est pas déjà installé sur l’appareil.

4.  Accédez à [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com), puis essayez d’installer le profil quand vous y êtes invité.

5.  Vérifiez que Safari pour iOS est le navigateur par défaut et que les cookies sont activés.

### <a name="enrolled-ios-device-doesnt-appear-in-console-when-using-system-center-configuration-manager-with-intune"></a>L’appareil iOS inscrit n’apparaît pas dans la console lors de l’utilisation de System Center Configuration Manager avec Intune
**Problème :** L’utilisateur inscrit l’appareil iOS, mais celui-ci n’apparaît pas dans la console d’administration de Configuration Manager. L’appareil n’indique pas qu’il a été inscrit. Causes possibles :

- Le connecteur Microsoft Intune sur votre site Configuration Manager ne communique pas avec le service Intune.
- Le composant Data Discovery Manager (ddm) ou le composant State Manager (statmgr) ne traite pas les messages du service Intune.
- Vous avez peut-être téléchargé le certificat de gestion des appareils mobiles à partir d’un compte et vous l’avez utilisé dans un autre compte.


**Résolution :** Passez en revue les fichiers journaux suivants pour détecter les erreurs possibles :

- dmpdownloader.log
- ddm.log
- statmgr.log

Des exemples seront bientôt ajoutés concernant les éléments à rechercher dans ces fichiers journaux.


### <a name="users-ios-device-is-stuck-on-an-enrollment-screen-for-more-than-10-minutes"></a>L’appareil iOS de l’utilisateur est bloqué sur un écran d’inscription pendant plus de 10 minutes

**Problème** : Un appareil en cours d’inscription peut rester bloqué sur l’un des deux écrans suivants :
- En attente de configuration finale de « Microsoft »
- Application d’accès guidé non disponible. Contactez l’administrateur.

Ce problème peut se produire dans les cas suivants :
- Une panne temporaire affecte les services Apple, ou
- L’inscription iOS est configurée pour utiliser les jetons VPP comme indiqué dans le tableau, mais il existe un problème relatif au jeton VPP

| Paramètres d’inscription | Valeur |
| ---- | ---- |
| Plate-forme | iOS |
| Affinité utilisateur | Inscrire avec l’affinité utilisateur |
|S’authentifier avec le Portail d’entreprise au lieu de l’Assistant Configuration Apple | Oui |
| Installer le Portail d’entreprise avec VPP | Utilisez le jeton : adresse du jeton |
| Exécuter le Portail d’entreprise en mode Application unique jusqu’à l’authentification | Oui |

**Résolution** : Pour résoudre le problème, vous devez :
1. Déterminer s’il existe un problème avec le jeton VPP et le corriger
2. Identifier les appareils bloqués
3. Réinitialiser les appareils affectés
4. Indiquer à l’utilisateur de redémarrer le processus d’inscription

#### <a name="determine-if-theres-something-wrong-with-the-vpp-token"></a>Déterminer s’il existe un problème avec le jeton VPP
1. Accédez à **Intune** > **Inscription des appareils** > **Inscription Apple** > **Jeton du programme d’inscription** > nom du jeton > **Profils** > nom du profil > **Gérer** > **Propriétés**.
2. Passez en revue les propriétés pour déterminer s’il existe des erreurs similaires à ce qui suit :
    - Ce jeton a expiré.
    - Ce jeton ne fait pas partie des licences du Portail d’entreprise.
    - Ce jeton est utilisé par un autre service.
    - Ce jeton est utilisé par un autre locataire.
    - Ce jeton a été supprimé.
3. Corrigez les problèmes liés au jeton.

#### <a name="identify-which-devices-are-blocked-by-the-vpp-token"></a>Identifier les appareils bloqués par le jeton VPP
1. Accédez à **Intune** > **Inscription des appareils** > **Inscription Apple** > **Jeton du programme d’inscription** > nom du jeton > **Appareils**.
2. Filtrez la colonne **État du profil** en fonction de la valeur **Bloqué**.
3. Notez les numéros de série de tous les appareils **bloqués**.

#### <a name="remotely-wipe-the-blocked-devices"></a>Réinitialiser à distance les appareils bloqués
Une fois que vous avez résolu les problèmes liés au jeton VPP, vous devez réinitialiser les appareils bloqués.
1. Accédez à **Intune** > **Appareils** > **Tous les appareils** > **Colonnes** > **Numéro de série** > **Appliquer**. 
2. Choisissez chaque appareil bloqué dans la liste **Tous les appareils**, puis choisissez **Réinitialiser** > **Oui**.

#### <a name="tell-the-users-to-restart-the-enrollment-process"></a>Indiquer aux utilisateurs de redémarrer le processus d’inscription
Une fois que vous avez réinitialisé les appareils bloqués, vous pouvez demander aux utilisateurs de redémarrer le processus d’inscription.

## <a name="macos-issues"></a>Problèmes liés à macOS

### <a name="macos-enrollment-errors"></a>Erreurs d’inscription macOS
**Message d’erreur 1 :** *Vous semblez utiliser une machine virtuelle. Veillez à effectuer une configuration complète de votre machine virtuelle en spécifiant notamment le numéro de série et le modèle de matériel. S’il ne s’agit pas d’une machine virtuelle, contactez le support.*  

**Message d’erreur 2 :** *Votre appareil ne peut pas être géré. Ce problème peut avoir l’une des causes suivantes : vous utilisez une machine virtuelle, votre appareil a un numéro de série restreint ou l’appareil est déjà attribué à une autre personne. Découvrez comment résoudre ces problèmes ou contactez le support de votre entreprise.*

**Problème :** Ce message peut s’afficher pour l’une des raisons suivantes :  
* Une machine virtuelle macOS n’est pas configurée correctement  
* Vous avez activé des restrictions d’appareil qui exigent que l’appareil appartienne à l’entreprise ou qu’il porte un numéro de série inscrit dans Intune  
* L’appareil a déjà été inscrit, mais il est encore attribué à un autre utilisateur dans Intune  

**Résolution :** Commencez par vérifier auprès de l’utilisateur lequel de ces problèmes concerne son appareil. Choisissez ensuite la solution la plus pertinente parmi les solutions suivantes :
* Si l’utilisateur souhaite inscrire une machine virtuelle pour des tests, assurez-vous que cette machine est entièrement configurée pour que Intune puisse reconnaître son numéro de série et le modèle de matériel. Découvrez-en davantage sur la [configuration des machines virtuelles](macos-enroll.md#enroll-virtual-macos-machines-for-testing) dans Intune.  
* Si votre organisation a activé des restrictions d’inscription qui bloquent les appareils macOS personnels, vous devez manuellement [ajouter le numéro de série de l’appareil personnel](corporate-identifiers-add.md#manually-enter-corporate-identifiers) dans Intune.  
* Si l’appareil est encore attribué à un autre utilisateur dans Intune, son propriétaire précédent n’a pas utilisé l’application Portail d’entreprise pour supprimer ou réinitialiser l’appareil. Pour supprimer l’entrée d’appareil obsolète dans Intune :  

    1. Accédez à [Intune dans le portail Azure](https://portal.manage.microsoft.com) et connectez-vous à l’aide de vos informations d’identification d’administration.
    2. Accédez à Intune > **Appareils** > **Tous les appareils**.  
    3. Recherchez l’appareil qui rencontre le problème d’inscription. Recherchez l’appareil par son nom ou son adresse MAC/HW pour limiter les résultats.
    4. Sélectionnez l’appareil > **Supprimer**. Supprimez toutes les autres entrées associées à l’appareil.  

## <a name="issues-when-using-system-center-configuration-manager-with-intune"></a>Problèmes quand vous utilisez System Center Configuration Manager avec Intune
### <a name="mobile-devices-disappear"></a>Les appareils mobiles disparaissent
**Problème :** Après avoir inscrit un appareil mobile dans Configuration Manager, cet appareil disparaît du regroupement d’appareils mobiles. Toutefois, l’appareil a toujours le profil de gestion et est listé dans la passerelle CSS.

**Résolution :** Ce problème peut se produire pour les raisons suivantes :
- Vous avez un processus personnalisé qui supprime les appareils non membres d’un domaine, ou 
- L’utilisateur a mis hors service l’appareil en le retirant de l’abonnement
Pour identifier le processus ou le compte d’utilisateur qui a supprimé l’appareil de la console Configuration Manager, procédez comme suit.

#### <a name="check-how-device-was-removed"></a>Vérifier comment l’appareil a été supprimé

1.  Dans la console d’administration Configuration Manager, sélectionnez **Analyse** &gt; **État du système** &gt; **Requêtes sur les messages d’état**.

2.  Cliquez avec le bouton droit sur **Ressources du membre pour un regroupement supprimées manuellement**, puis sélectionnez **Afficher les messages**.

3.  Choisissez une heure/date appropriée ou les 12 dernières heures.

4.  Recherchez l’appareil en question et vérifiez comment l’appareil a été supprimé. L’exemple ci-dessous indique que le compte SCCMInstall a supprimé l’appareil via une application inconnue.

    ![Capture d’écran du diagnostic de suppression d’appareil](./media/troubleshoot-device-enrollment-in-intune/CM_With_Intune_Unknown_App_Deleted_Device.jpg)

5.  Vérifiez que Configuration Manager n’a pas de tâche, de script ou tout autre processus planifié qui peut vider automatiquement les appareils mobiles hors domaine ou associés.

### <a name="other-ios-enrollment-errors"></a>Autres erreurs d’inscription iOS
La liste des erreurs d’inscription iOS est fournie dans notre documentation, dans [Résolution des problèmes d’inscription d’appareils iOS dans Microsoft Intune](https://support.microsoft.com/help/4039809/troubleshooting-ios-device-enrollment-in-intune).

## <a name="pc-issues"></a>Problèmes liés aux PC

|Message d'erreur|Problème|Résolution|
|---|---|---|
|**L’administrateur informatique doit affecter une licence pour autoriser l’accès**<br>Votre administrateur informatique ne vous a pas accordé l’accès à cette application. Demandez-lui de l’aide ou réessayez plus tard.|Impossible d’inscrire l’appareil, car le compte de l’utilisateur ne dispose pas de la licence nécessaire.|Pour que les utilisateurs puissent inscrire leurs appareils, ils doivent avoir reçu la licence nécessaire. Ce message signifie qu’ils ont un type de licence incorrect pour l’autorité de gestion des appareils mobiles. Par exemple, ils voient cette erreur si les deux conditions suivantes sont remplies : <ol><li>Intune a été défini en tant qu’autorité de gestion des appareils mobiles</li><li>Ils utilisent une licence System Center 2012 R2 Configuration Manager.</li></ol>Découvrez comment [attribuer des licences Intune à vos comptes d’utilisateur](https://docs.microsoft.com/intune/licenses-assign).|



### <a name="the-machine-is-already-enrolled---error-hr-0x8007064c"></a>L’ordinateur est déjà inscrit - Erreur hr 0x8007064c
**Problème :** L’inscription échoue avec l’erreur **L’ordinateur est déjà inscrit**. Le journal d’inscription affiche l’erreur **hr 0x8007064c**.

Cette défaillance peut se produire, car l’ordinateur :
- A été déjà inscrit, ou
- A l’image clonée d’un ordinateur déjà inscrit
Le certificat de compte du compte précédent est toujours présent sur l’ordinateur.

**Résolution :**

1. Dans le menu **Démarrer**, tapez **Exécuter** -> **MMC**.
1. Choisissez **Fichier** > **Ajouter/supprimer des composants logiciels enfichables**.
1. Double-cliquez sur **Certificats**, choisissez **Compte ordinateur** > **Suivant**, puis sélectionnez **Ordinateur local**.
1. Double-cliquez sur **Certificats (ordinateur local)** , puis choisissez **Personnel / certificats**.
1. Recherchez le certificat Intune émis par Sc_Online_Issuing et supprimez-le, le cas échéant.
1. Si la clé de Registre suivante existe, supprimez-la : **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\OnlineManagement regkey** et toutes les sous-clés.
1. Tentez la réinscription.
1. Si vous n’arrivez toujours pas à inscrire l’ordinateur, recherchez cette clé et supprimez-la, si elle existe : **KEY_CLASSES_ROOT\Installer\Products\6985F0077D3EEB44AB6849B5D7913E95**.
1. Tentez la réinscription.

    > [!IMPORTANT]
    > Cette section, méthode ou tâche contient des étapes qui vous indiquent comment modifier le registre. Toutefois, des problèmes importants peuvent survenir si vous modifiez le registre de façon incorrecte. Par conséquent, assurez-vous de suivre les étapes avec précaution. Pour plus de protection, sauvegardez le registre avant de le modifier. Vous pourrez ainsi restaurer le Registre en cas de problème.
    > Pour plus d’informations sur la procédure de sauvegarde et de restauration du registre, consultez [Procédure de sauvegarde et de restauration du registre dans Windows](https://support.microsoft.com/kb/322756)

## <a name="general-enrollment-error-codes"></a>Codes généraux des erreurs d’inscription

|Code d'erreur|Problème possible|Solution suggérée|
|--------------|--------------------|----------------------------------------|
|0x80CF0437 |L’horloge de l’ordinateur client n’est pas réglée sur la bonne heure.|Assurez-vous que l'horloge et le fuseau horaire de l'ordinateur client sont correctement réglés.|
|0x80240438, 0x80CF0438, 0x80CF402C|Connexion impossible au service Intune. Vérifiez les paramètres de proxy du client.|Vérifiez qu’Intune prend en charge la configuration du proxy sur l’ordinateur client. Vérifiez que l’ordinateur client dispose d’un accès à Internet.|
|0x80240438, 0x80CF0438|Les paramètres de proxy dans Internet Explorer et le système local ne sont pas configurés.|Connexion impossible au service Intune. Vérifiez les paramètres de proxy du client. Vérifiez qu’Intune prend en charge la configuration du proxy sur l’ordinateur client. Vérifiez que l’ordinateur client dispose d’un accès à Internet.|
|0x80043001, 0x80CF3001, 0x80043004, 0x80CF3004|Le package d'inscription n'est plus à jour.|Téléchargez et installez le package de logiciel client le plus récent à partir de l’espace de travail Administration.|
|0x80043002, 0x80CF3002|Le compte est en mode de maintenance.|Vous ne pouvez pas inscrire de nouveaux ordinateurs clients quand le compte est en mode maintenance. Pour afficher les paramètres de votre compte, connectez-vous à ce dernier.|
|0x80043003, 0x80CF3003|Le compte a été supprimé.|Vérifiez que votre compte et votre abonnement à Intune sont toujours actifs. Pour afficher les paramètres de votre compte, connectez-vous à ce dernier.|
|0x80043005, 0x80CF3005|L'ordinateur client a été mis hors service.|Patientez quelques heures, supprimez les anciennes versions du logiciel client de l'ordinateur et essayez de le réinstaller.|
|0x80043006, 0x80CF3006|Le nombre maximal de sièges autorisés pour le compte a été atteint.|Votre organisation doit acheter des sièges supplémentaires pour que vous puissiez inscrire davantage d’ordinateurs clients auprès du service.|
|0x80043007, 0x80CF3007|Le fichier de certificat est introuvable dans le dossier du programme d’installation.|Extrayez tous les fichiers avant de commencer l'installation. Ne renommez pas et ne déplacez pas les fichiers extraits : tous les fichiers doivent se trouver dans le même dossier, sinon l’installation sera un échec.|
|0x8024D015, 0x00240005, 0x80070BC2, 0x80070BC9, 0x80CFD015|Impossible d’installer le logiciel, car un redémarrage de l’ordinateur client est en attente.|Redémarrez l'ordinateur, puis réessayez d'installer le logiciel client.|
|0x80070032|Un ou plusieurs prérequis pour l’installation du logiciel client n’ont pas été détectés sur l’ordinateur client.|Assurez-vous que toutes les mises à jour nécessaires sont installées sur l'ordinateur client, puis réessayez d'installer le logiciel client.|
|0x80043008, 0x80CF3008|Échec du démarrage du service des mises à jour de gestion Microsoft Online.|Contactez le support Microsoft comme décrit dans [Comment obtenir un support technique pour Microsoft Intune](get-support.md).|
|0x80043009, 0x80CF3009|L'ordinateur client est déjà inscrit dans le service.|Vous devez mettre hors service l'ordinateur client avant de le réinscrire dans le service.|
|0x8004300B, 0x80CF300B|Impossible d’exécuter le package d’installation du logiciel client, car la version de Windows exécutée sur le client n’est pas prise en charge.|Intune ne prend pas en charge la version de Windows en cours d’exécution sur l’ordinateur client.|
|0xAB2|Windows Installer n’a pas pu accéder au runtime de VBScript pour une action personnalisée.|Cette erreur est générée par une action personnalisée basée sur des DLL (Dynamic-Link Libraries). Pour résoudre les problèmes avec la DLL, vous devrez peut-être utiliser les outils décrits dans l’article [KB198038 du support technique Microsoft : Useful Tools for Package and Deployment Issues (Outils utiles en cas de problèmes de package et de déploiement)](https://support.microsoft.com/kb/198038).|
|0x80cf0440|La connexion au point de terminaison de service s'est terminée.|Le compte d’évaluation ou payant est suspendu. Créez un nouveau compte d’évaluation ou payant et recommencez l’inscription.|




### <a name="next-steps"></a>Étapes suivantes
Si ces informations de dépannage n’ont pas permis de vous aider, contactez le support Microsoft comme décrit dans [Comment obtenir un support technique pour Microsoft Intune](get-support.md).
