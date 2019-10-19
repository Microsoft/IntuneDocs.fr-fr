---
title: Inclure des applications iOS dans un wrapper avec l’outil de création de package de restrictions d’application Intune
description: Découvrez comment inclure vos applications iOS dans un wrapper sans changer leur code. Préparez les applications afin d’appliquer des stratégies de gestion des applications mobiles.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b42642ec593112b0b247cd85b9230f68d6a803b8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490977"
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Préparer des applications iOS pour les stratégies de protection des applications avec l’outil de création de package de restrictions d’application Intune

[!INCLUDE [both-portals](../../intune-classic/includes/note-for-both-portals.md)]

Utilisez l’outil de création de package de restrictions d’application Microsoft Intune pour iOS pour activer les stratégies de protection des applications Intune sans modifier le code de l’application proprement dit.

L’outil est une application en ligne de commande macOS qui crée un wrapper autour d’une application. Lorsqu'une application est traitée, vous pouvez modifier la fonctionnalité de cette application en y déployant [des stratégies de protection des applications](../apps/app-protection-policies.md).

Pour télécharger l’outil, consultez la section [Outil de création de package de restrictions d’application Microsoft Intune pour iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) sur GitHub.



## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>Conditions préalables générales pour l’outil de création de package de restrictions d’application

Avant d’exécuter l’outil de création de package de restrictions d’application, vous devez remplir certaines conditions préalables générales :

* Téléchargez l’outil [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) (Outil de création de package de restrictions d’application Microsoft Intune pour iOS) à partir de GitHub.

* Un ordinateur macOS qui exécute OS X 10.8.5 ou ultérieur et sur lequel est installé l’ensemble d’outils Xcode version 9 ou ultérieure.

* L'application iOS d'entrée doit être développée et signée par votre entreprise ou par un éditeur de logiciels indépendant (ISV).

  * Le fichier de l'application d’entrée doit avoir l’extension **.ipa** ou **.app**.

  * L’application d’entrée doit être compilée pour iOS 10 ou version ultérieure.

  * L’application d’entrée ne peut pas être chiffrée.

  * L’application d’entrée ne peut pas contenir des attributs de fichiers étendus.

  * L’application d’entrée doit disposer de droits définis avant d’être traitée par l’outil de création de package de restrictions d’application Intune. Ces [droits](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html) confèrent à l’application des autorisations et des fonctionnalités supplémentaires qui vont au-delà de celles qui sont généralement accordées. Consultez [Définition des droits de l’application](#setting-app-entitlements) pour obtenir des instructions.

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>Conditions préalables pour développeur Apple pour l’outil de création de package de restrictions d’application

Pour distribuer des applications encapsulées exclusivement aux utilisateurs de votre organisation, vous avez besoin d’un compte de type [Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/) et de plusieurs entités pour la signature des applications liées à votre compte de développeur Apple.

Pour en savoir plus sur la distribution d'applications iOS en interne pour les utilisateurs de votre organisation, lisez le guide officiel [Distributing Apple Developer Enterprise Program Apps](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1).

Vous aurez besoin des éléments suivants pour distribuer des applications encapsulées par Intune :

* Un compte de développeur de type Apple Developer Enterprise Program.

* Un certificat de signature de distribution en interne et ad-hoc avec identificateur d’équipe valide.

  * Vous aurez besoin du hachage SHA1 du certificat de signature comme paramètre pour l’outil de création de package de restrictions d’application Intune.


* Profil de configuration de distribution interne.

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Étapes de création d’un compte Apple Developer Enterprise
1. Accédez au [site Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/).

2. Dans le coin supérieur droit de la page, cliquez sur **Enroll** (Inscription).

3. Lisez la checklist des éléments requis pour l'inscription. Cliquez sur **Start Your Enrollment** (Démarrer votre inscription) en bas de la page.

4. **Connectez-vous** avec l’ID Apple de votre organisation. Si vous n’en avez pas, cliquez sur **Create Apple ID** (Créer un identifiant Apple).

5. Sélectionnez votre **type d’entité** puis cliquez sur **Continue** (Continuer).

6. Remplissez le formulaire avec les informations de votre organisation. Cliquez sur **Continue**(Continuer). À ce stade, Apple vous contacte pour vérifier que vous êtes autorisé à inscrire votre organisation.

8. Après vérification, cliquez sur **Agree to License** (Accepter la licence).

9. Après avoir accepté la licence, terminez en **achetant et en activant le programme**.

10. Si vous êtes l’agent de l’équipe (la personne qui rejoint le programme Apple Developer Enterprise Program au nom de votre organisation), constituez d’abord votre équipe en invitant les membres de l’équipe et en leur attribuant des rôles. Pour savoir comment gérer votre équipe, lisez la documentation d’Apple sur [la gestion de votre équipe de compte développeur](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1).

### <a name="steps-to-create-an-apple-signing-certificate"></a>Étapes de création d'un certificat de signature Apple

1. Accédez au [portail des développeurs Apple](https://developer.apple.com/).

2. Dans le coin supérieur droit de la page, cliquez sur **Account** (Compte).

3. **Connectez-vous** à l'aide de l'identifiant Apple de votre entreprise.

4. Cliquez sur **Certificates, IDs & Profiles** (Certificats, identifiants et profils).

   ![Portail des développeurs Apple - Certificats, ID et profils](./media/app-wrapper-prepare-ios/iOS-signing-cert-1.png)

5. Cliquez sur le bouton ![signe plus du portail des développeurs Apple](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) dans le coin supérieur droit pour ajouter un certificat iOS.

6. Choisissez de créer un certificat **In-House and Ad Hoc** (interne et ad-hoc) sous **Production**.

   ![Sélectionnez le certificat interne et ad-hoc](./media/app-wrapper-prepare-ios/iOS-signing-cert-3.png)

   >[!NOTE]
   >Si vous n’envisagez pas de distribuer l’application et souhaitez uniquement la tester en interne, vous pouvez utiliser un certificat de développement d’applications iOS au lieu d’un certificat pour la production. Si vous utilisez un certificat de développement, vérifiez que le profil de configuration mobile fait référence aux appareils sur lesquels l’application doit être installée.

7. Cliquez sur **Next** (Suivant) en bas de la page.

8. Lisez les instructions sur la création d’une **demande de signature de certificat (CSR)** à l’aide de l’application Trousseau d’accès sur votre ordinateur macOS.

   ![Lisez les instructions pour créer une demande de signature de certificat](./media/app-wrapper-prepare-ios/iOS-signing-cert-4.png)

9. Suivez les instructions ci-dessus pour créer une demande de signature de certificat. Sur votre ordinateur macOS, lancez l'application **Trousseau d’accès**.

10. Dans le menu macOS en haut de l’écran, accédez à **Trousseau d’accès > Assistant de certification > Demander un certificat à une autorité de certificat**.  

    ![Pour demander un certificat à une autorité de certificat dans Trousseau d'accès](./media/app-wrapper-prepare-ios/iOS-signing-cert-5.png)

11. Suivez les instructions du site des développeur Apple ci-dessus pour créer un fichier CSR. Enregistrez le fichier CSR sur votre ordinateur macOS.

    ![Entrez les informations pour le certificat que vous demandez](./media/app-wrapper-prepare-ios/iOS-signing-cert-6.png)

12. Retourner sur le site des développeurs Apple. Cliquez sur **Continue** (Continuer). Puis téléchargez le fichier CSR.

13. Apple génère votre certificat de signature. Téléchargez et enregistrez-le sur un emplacement facile à mémoriser sur votre ordinateur macOS.

    ![Télécharger votre certificat de signature](./media/app-wrapper-prepare-ios/iOS-signing-cert-7.png)

14. Double-cliquez sur le fichier de certificat que vous venez de télécharger afin d'ajouter le certificat à un trousseau d’accès.

15. Ouvrez à nouveau **Trousseau d’accès**. Localisez votre certificat en recherchant son nom dans la barre de recherche en haut à droite. Cliquez avec le bouton droit sur l’élément pour afficher le menu, puis cliquez sur **Lire les informations**. Dans les exemples d’écrans, nous utilisons un certificat de développement au lieu d’un certificat de production.

    ![Ajouter votre certificat à un trousseau d’accès](./media/app-wrapper-prepare-ios/iOS-signing-cert-8.png)

16. Une fenêtre d’information s’affiche. Faites défiler vers le bas et regardez sous l'étiquette **Empreintes**. Copiez la chaîne **SHA1** (floue) à utiliser comme paramètre pour « -c » pour l’outil de création de package de restrictions d’application.

    ![Informations iPhone - chaîne d’empreintes digitales SHA1](./media/app-wrapper-prepare-ios/iOS-signing-cert-9.png)



### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>Étapes de création d’un profil de configuration de distribution interne

1. Revenez au [portail du compte des développeurs Apple](https://developer.apple.com/account/) et **connectez-vous** avec l'identifiant Apple de votre organisation.

2. Cliquez sur **Certificates, IDs & Profiles** (Certificats, identifiants et profils).

3. Cliquez sur le bouton ![signe plus du portail des développeurs Apple](./media/app-wrapper-prepare-ios/iOS-signing-cert-2.png) dans le coin supérieur droit pour ajouter un profil de configuration iOS.

4. Choisissez de créer un profil de configuration **In House** (interne) sous **Distribution**.

   ![Sélectionner un profil d’approvisionnement interne](./media/app-wrapper-prepare-ios/iOS-provisioning-profile-1.png)

5. Cliquez sur **Continue** (Continuer). Veillez à lier le certificat de signature généré précédemment au profil de configuration.

6. Suivez les étapes pour télécharger votre profil (avec l’extension .mobileprovision) sur votre ordinateur macOS.

7. Enregistrez le fichier dans un emplacement facile à mémoriser. Ce fichier servira pour le paramètre -p lors de l’utilisation de l'outil de création de package de restrictions d'application.



## <a name="download-the-app-wrapping-tool"></a>Télécharger l'outil de création de package de restrictions d'application

1. Téléchargez les fichiers de l’outil de création de package de restrictions d’application depuis [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) vers un ordinateur macOS.

2. Double-cliquez sur **Microsoft Intune App Wrapping Tool for iOS.dmg**. Une fenêtre présentant le Contrat de licence utilisateur final (CLUF) s’affiche. Lisez attentivement le document.

3. Choisissez **J’accepte** pour accepter le CLUF, qui monte le package sur votre ordinateur.

## <a name="run-the-app-wrapping-tool"></a>exécuter l'outil de création de package de restrictions d'application

### <a name="use-terminal"></a>Utiliser un terminal

Ouvrez le terminal macOS et exécutez la commande suivante :

```bash
/Volumes/IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Certains paramètres sont facultatifs, comme indiqué dans le tableau suivant.

**Exemple :** l’exemple de commande suivant exécute l’outil de création de package de restrictions d’application sur une application nommée MyApp.ipa. Un profil de configuration et le hachage SHA-1 du certificat de signature sont spécifiés et utilisés pour signer l’application encapsulée. L’application de sortie (MyApp_Wrapped.ipa) est créée et stockée dans votre dossier Bureau.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>Paramètres de ligne de commande
Vous pouvez utiliser les paramètres de ligne de commande suivants avec l’outil de création de package de restrictions d’application :

|Propriété|Comment l’utiliser|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. Le nom de fichier doit se terminer par .app ou .ipa. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**| Affiche des informations détaillées sur l’utilisation des propriétés de ligne de commande disponibles pour l’outil de création de package de restrictions d’application. |
|**-aa**|(Facultatif) `<Authority URI of the input app if the app uses the Azure Active Directory Authentication Library>` c.-à-d. `login.windows.net/common` |
|**-ac**|(Facultatif) `<Client ID of the input app if the app uses the Azure Active Directory Authentication Library>` il s’agit du GUID dans le champ ID client est issu de la liste de votre application dans le panneau inscription de l’application. |
|**-ar**|(Facultatif) `<Redirect/Reply URI of the input app if the app uses the Azure Active Directory Authentication Library>` il s’agit de l’URI de redirection configuré dans l’inscription de votre application. En général, il s’agit du protocole d’URL de l’application que l’application Microsoft Authenticator retourne à après l’authentification répartie. |
|**-v**| (Facultatif) Affiche les messages détaillés sur la console. Il est recommandé d’utiliser cet indicateur pour déboguer les éventuelles erreurs. |
|**-e**| (Facultatif) Utilisez cet indicateur pour que l’outil de création de package de restrictions d’application supprime les droits manquants pendant le traitement de l’application. Pour plus d’informations, consultez [Définition des droits de l’application](#setting-app-entitlements).|
|**-xe**| (Facultatif) Imprime des informations sur les extensions iOS dans l’application et les droits qui sont nécessaires pour les utiliser. Pour plus d’informations, consultez [Définition des droits de l’application](#setting-app-entitlements). |
|**-x**| (Facultatif) `<An array of paths to extension provisioning profiles>`. À utiliser si votre application a besoin d’extension des profils d’approvisionnement d’extension.|
|**-b**|(Facultatif) Utilisez -b sans argument si vous voulez que l’application de sortie encapsulée ait la même version d’ensemble (bundle) que l’application d’entrée (non recommandé). <br/><br/> Utilisez `-b <custom bundle version>` si vous voulez que l’application encapsulée ait une valeur CFBundleVersion personnalisée. Si vous choisissez de spécifier une valeur CFBundleVersion personnalisée, pensez à incrémenter la valeur CFBundleVersion de l’application native sur le composant le moins significatif, par exemple, 1.0.0 -> 1.0.1. |
|**-citrix**|Facultatif Incluez le kit de développement logiciel (SDK) d’application Citrix XenMobile (variante en réseau uniquement). Pour utiliser cette option, vous devez avoir installé la [boîte à outils Citrix MDX](https://docs.citrix.com/en-us/mdx-toolkit/about-mdx-toolkit.html) . |
|**-f**|(Facultatif) `<Path to a plist file specifying arguments.>` Utilisez cet indicateur devant le fichier [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) si vous choisissez d’utiliser le modèle plist pour spécifier le reste des propriétés IntuneMAMPackager telles que -i, -o et -p. Consultez Utiliser un fichier plist pour les arguments d’entrée. |

### <a name="use-a-plist-to-input-arguments"></a>Utiliser un fichier plist pour les arguments d’entrée
Placer tous les arguments de commande dans un fichier [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) constitue un moyen simple d’exécuter l’outil de création de package de restrictions d’application. Plist est un format de fichier similaire à XML que vous pouvez utiliser pour vos arguments de ligne de commande à l’aide d’une interface de formulaire.

Dans le dossier IntuneMAMPackager/contenu/MacOS, ouvrez `Parameters.plist` (un modèle plist vide) à l’aide d’un éditeur de texte ou Xcode. Entrez vos arguments pour les clés suivantes :

| Clé plist | Type |  Valeur par défaut | Remarques |
|------------------|-----|--------------|-----|
| Chemin du package d’application d’entrée |Chaîne|empty| Identique à -i|
| Chemin du package d’application de sortie |Chaîne|empty| Identique à -o|
| Chemin du profil d’approvisionnement |Chaîne|empty| Identique à -p|
| Hachage du certificat SHA-1 |Chaîne|empty| Identique à -c|
| Autorité ADAL |Chaîne|empty| Identique à -aa|
| ID client ADAL |Chaîne|empty| Identique à -ac|
| URI de réponse ADAL |Chaîne|empty| Identique à -ar|
| Mode détaillé activé |Booléen|false| Identique à -v|
| Supprimer les droits manquants |Booléen|false| Identique à -c|
| Empêcher la mise à jour de la build par défaut |Boolen|false| Équivaut à utiliser -b sans arguments|
| Générer le remplacement de chaîne |Chaîne|empty| Valeur CFBundleVersion personnalisée de l’application de sortie encapsulée|
| Inclure le kit de développement logiciel (SDK) d’application Citrix XenMobile (variante en réseau uniquement)|Booléen|false| Identique à-Citrix|
| Chemins des profils d’approvisionnement d’extension |Tableau de chaînes|empty| Tableau de profils d’approvisionnement d’extension pour l’application.


Exécutez la commande IntuneMAMPackager avec le fichier plist comme unique argument :

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>Après l’habillage

Une fois le processus d’habillage terminé, le message « L’application a été encapsulée correctement » s’affiche. Si une erreur se produit, consultez [Messages d'erreur](#error-messages-and-log-files) pour obtenir de l'aide.

L'application encapsulée est enregistrée dans le dossier de sortie spécifié précédemment. Vous pouvez maintenant charger l’application sur la console d’administration Intune et l’associer à une stratégie de gestion des applications mobiles.

> [!IMPORTANT]
> Lors du chargement d’une application encapsulée, vous pouvez tenter de mettre à jour une version antérieure de l’application si telle version (encapsulée ou native) a déjà été déployée pour Intune. Si vous rencontrez une erreur, chargez l’application comme nouvelle application et supprimez l’ancienne version.

Vous pouvez désormais déployer l’application vers vos groupes d’utilisateurs et cibler les stratégies de protection de l’application sur celle-ci. L’application s’exécutera sur l’appareil utilisant les stratégies de protection que vous spécifiez.

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>À quelle fréquence dois-je réempaqueter mon application iOS avec l’outil de création de package de restrictions d’application Intune ?
Les principaux scénarios dans lesquels vous devez réencapsuler vos applications sont les suivants :
* L’application elle-même a publié une nouvelle version. La version précédente de l’application a été empaquetée et chargée sur la console Intune.
* L’outil de création de package de restrictions d’application Intune pour iOS a publié une nouvelle version qui intègre la correction de bogues importants ou des fonctionnalités des stratégies de protection d’application Intune nouvelles et spécifiques. Elle arrive après 6 à 8 semaines via un dépôt GitHub pour [l’outil de création de package de restrictions d’application Microsoft Intune pour iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

Pour iOS, alors qu’il est possible d’empaqueter avec un profil de provisionnement/certificat différent de celui d’origine utilisé pour signer l’application, si les droits spécifiés dans l’application ne sont pas dans le nouveau profil de provisionnement, la création de package de restrictions échoue. L’utilisation de l’option de ligne de commande « -e », qui supprime les droits manquants de l’application pour obliger la création de package de restrictions à ne pas échouer dans ce scénario, peut rompre les fonctionnalités dans l’application.

Voici quelques bonnes pratiques de réencapsulation :
* Vérification qu’un autre profil de provisionnement a tous les droits requis comme tous les profils de provisionnement précédents. 

## <a name="error-messages-and-log-files"></a>Messages d’erreur et fichiers journaux
Aidez-vous des informations suivantes pour résoudre les problèmes que vous rencontrez avec l’outil de création de package de restrictions d’application.

### <a name="error-messages"></a>Messages d'erreur
Si l’outil de création de package de restrictions d’application échoue, l’un des messages d’erreur suivants s’affiche dans la console :

|Message d'erreur|Plus d’informations|
|-----------------|--------------------|
|Vous devez spécifier un profil de configuration iOS valide.|Votre profil de configuration n'est peut-être pas valide. Vérifiez que vous avez les autorisations appropriées pour les appareils et que votre profil cible correctement le développement ou la distribution. Votre profil de configuration a peut être aussi expiré.|
|Spécifiez un nom d'application d'entrée valide.|Assurez-vous que le nom de l'application d'entrée spécifié est correct.|
|Spécifiez un chemin d'accès valide vers l'application de sortie.|Assurez-vous que le chemin d'accès à l'application de sortie que vous avez spécifié existe et est correct.|
|Spécifiez un profil de configuration d'entrée valide.|Vérifiez que vous avez fourni un nom et une extension de profil de configuration valides. Votre profil de configuration n’a peut-être pas les droits nécessaires, ou vous n’avez peut-être pas inclus l’option de ligne de commande –p.|
|L'application d'entrée spécifiée est introuvable. Spécifiez un nom et un chemin d'accès d'application d'entrée valides.|Assurez-vous que le chemin d'accès à l'application d'entrée est valide et qu'il existe. Assurez-vous que l'application d'entrée existe à cet emplacement.|
|Le fichier de profil de configuration d'entrée spécifié est introuvable. Spécifiez un fichier de profil de configuration d'entrée valide.|Assurez-vous que le chemin d'accès au fichier de configuration d'entrée est valide et que le fichier spécifié existe.|
|Le dossier d'application de sortie spécifié est introuvable. Spécifiez un chemin d'accès valide vers l'application de sortie.|Assurez-vous que le chemin de sortie spécifié est valide et qu'il existe.|
|L’application de sortie n’a pas une extension **.ipa**.|Seules les applications avec les extensions **.app** et **.ipa** sont acceptées par l’outil de création de package de restrictions d’application. Assurez-vous que votre fichier de sortie a une extension valide.|
|Un certificat de signature non valide a été spécifié. Spécifiez un certificat de signature Apple valide.|Assurez-vous d'avoir téléchargé le certificat de signature correct à partir du portail de développement Apple. Votre certificat a peut-être expiré, ou une clé publique ou privée est peut-être manquante. Si votre profil de configuration et votre certificat Apple peuvent être utilisés pour signer correctement une application dans Xcode, cela signifie qu’ils sont valides pour l’outil de création de package de restrictions d’application.|
|L'application d'entrée spécifiée n'est pas valide. Spécifiez une application valide.|Assurez-vous que votre application iOS est valide et qu'elle a été compilée sous forme de fichier .app ou .ipa.|
|L'application d'entrée spécifiée est chiffrée. Spécifiez une application non chiffrée valide.|L’outil de création de package de restrictions d’application ne gère pas les applications chiffrées. Fournissez une application non chiffrée.|
|L'application d'entrée spécifiée n'est pas au format PIE (Position Independent Executable). Spécifiez une application valide au format PIE.|Vous pouvez charger les applications PIE (Position Independent Executable) à une adresse mémoire aléatoire au moment de l’exécution. Cela peut offrir certains avantages en termes de sécurité. Pour plus d’informations sur les avantages en termes de sécurité, consultez votre documentation pour développeurs Apple.|
|L'application d'entrée spécifiée a déjà été encapsulée. Spécifiez une application non encapsulée valide.|Vous ne pouvez pas traiter une application qui a déjà été traitée par l'outil. Si vous souhaitez retraiter une application, exécutez l'outil à l'aide de la version d'origine de l'application.|
|L'application d'entrée spécifiée n'est pas signée. Spécifiez une application signée valide.|L'outil de création de package de restrictions d'application nécessite que les applications soient signées. Consultez votre documentation pour développeurs pour savoir comment signer une application encapsulée.|
|L'application d'entrée spécifiée doit être au format .ipa ou .app.|Seules les extensions .app et .ipa sont acceptées par l'outil de création de package de restrictions d'application. Assurez-vous que votre fichier d'entrée a une extension valide et qu'il a été compilé sous forme de fichier .app ou .ipa.|
|L'application d'entrée spécifiée a déjà été encapsulée et est à la dernière version de modèle de stratégie.|L’outil de création de package de restrictions d’application ne peut pas ré-encapsuler une application encapsulée existante avec la dernière version du modèle de stratégie.|
|AVERTISSEMENT : vous n’avez pas spécifié de hachage de certificat SHA1. Assurez-vous que votre application encapsulée est signée avant le déploiement.|Veillez à spécifier un hachage SHA1 valide à la suite de l’indicateur de ligne de commande –c. |

### <a name="log-files-for-the-app-wrapping-tool"></a>Fichiers journaux de l’outil de création de package de restrictions d’application
Les applications qui ont été encapsulées à l’aide de l’outil de création de package de restrictions d’application génèrent des journaux qui sont écrits dans la console de l’appareil iOS client. Ces informations sont utiles quand vous rencontrez des problèmes avec l’application et que vous devez déterminer si le problème est lié à l’outil de création de package de restrictions d’application. Pour récupérer ces informations, procédez comme suit :

1. Reproduisez le problème en exécutant l'application.

2. Recueillez la sortie de console en suivant les instructions d'Apple pour le [débogage des applications iOS déployées](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3. Filtrez les journaux enregistrés pour la sortie de Restrictions d'application en entrant le script suivant dans la console :

    ```bash
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```

    Vous pouvez envoyer les journaux filtrés à Microsoft.

    > [!NOTE]
    > Dans le fichier journal, l'élément « build version » représente le numéro de build de Xcode.

    Les applications encapsulées offrent également aux utilisateurs la possibilité d'envoyer les journaux directement à partir de l'appareil par courrier électronique, après un blocage de l'application. Les utilisateurs peuvent vous envoyer les journaux pour que vous les examiniez et le transmettiez à Microsoft si nécessaire.


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>Exigences concernant le certificat, le profil de configuration et l’authentification

L’outil de création de package de restrictions d’application pour iOS présente des conditions qui doivent être remplies pour pouvoir bénéficier de toutes les fonctionnalités.

|Condition requise|Détails|
|---------------|-----------|
|Profil de configuration iOS|Vérifiez que le profil d’approvisionnement est valide avant de l’inclure. L’outil de création de package de restrictions d’application ne vérifie pas si le profil d’approvisionnement a expiré pendant le traitement d’une application iOS. Si vous spécifiez un profil de configuration ayant expiré, l’outil de création de package de restrictions d’application inclut le profil de configuration ayant expiré, et vous ne découvrez le problème qu’une fois que l’installation de l’application a échoué sur un appareil iOS.|
|Certificat de signature iOS|Vérifiez que le certificat de signature est valide avant de le spécifier. L’outil ne vérifie pas si un certificat a expiré lors du traitement des applications iOS. Si vous fournissez le hachage d'un certificat ayant expiré, l'outil traitera et signera l'application, mais l'installation sur les appareils échouera.<br /><br />Vérifiez que le certificat fourni pour signer l’application encapsulée a une correspondance dans le profil d’approvisionnement. L’outil ne vérifie pas si le profil d’approvisionnement a une correspondance avec le certificat fourni pour signer l’application encapsulée.|
|Authentification|Pour que le chiffrement fonctionne, un code confidentiel doit être défini pour l’appareil. Sur les appareils sur lesquels vous avez déployé une application encapsulée, une pression sur la barre d’état sur l’appareil nécessite que l’utilisateur se reconnecte avec un compte professionnel ou scolaire. La stratégie par défaut dans une application encapsulée est l’*authentification lors du redémarrage*. iOS gère toutes les notifications externes (telles qu’un appel téléphonique) en quittant l’application, puis en la redémarrant.


## <a name="setting-app-entitlements"></a>Définition des droits de l’application
Avant d’encapsuler votre application, vous pouvez lui accorder des *droits* dans le but de lui octroyer des autorisations et des fonctionnalités supplémentaires qui vont au-delà de ce qu’une application peut généralement faire. Un *fichier de droits* est utilisé pendant la signature du code pour spécifier des autorisations spéciales dans votre application (par exemple, l’accès à un trousseau partagé). Des services d’application spécifiques appelés *capabilities* (fonctionnalités) sont activés dans Xcode pendant le développement de l’application. Une fois activées, les fonctionnalités apparaissent dans votre fichier de droits. Pour plus d’informations sur les droits et les fonctionnalités, consultez [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) (Ajout de fonctionnalités) dans la bibliothèque du développeur iOS. Pour obtenir la liste complète des fonctionnalités prises en charge, consultez [Supported capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html) (Fonctionnalités prises en charge).

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>Fonctionnalités prises en charge pour App Wrapping Tool for iOS

|Fonctionnalité|Description|Recommandation|
|--------------|---------------|------------------------|
|Groupes d’applications|Utilisez des groupes d’applications pour autoriser plusieurs applications à accéder à des conteneurs partagés et autoriser une communication interprocessus supplémentaire entre les applications.<br /><br />Pour activer les groupes d’applications, ouvrez le volet **Capabilities** (Fonctionnalités), puis cliquez sur **ON** (Activer) dans **App Groups** (Groupes d’applications). Vous pouvez ajouter des groupes d’applications en ou sélectionner des existants.|Quand vous utilisez App Groups, utilisez la notation DNS inverse :<br /><br />*group.com.companyName.AppGroup*|
|Modes d’arrière-plan|L’activation des modes d’arrière-plan permet à votre application iOS de continuer à s’exécuter en arrière-plan.||
|Protection des données|Data Protection (protection des données) ajoute un niveau de sécurité aux fichiers stockés sur le disque par votre application iOS. Data Protection utilise le matériel de chiffrement intégré présent sur certains appareils pour stocker les fichiers dans un format chiffré sur disque. Votre application doit être configurée pour utiliser Data Protection.||
|Achat dans l’application|L’achat dans l’application incorpore un store directement dans votre application. Vous pouvez vous y connecter et traiter les paiements de l’utilisateur en toute sécurité. Vous pouvez utiliser l’achat dans l’application pour récupérer les paiements en contrepartie de fonctionnalités améliorées ou de contenu supplémentaire que votre application peut exploiter.||
|Partage de trousseau|Le partage de trousseau permet à votre application de partager des mots de passe dans le trousseau avec les autres applications développées par votre équipe.|Quand vous utilisez le partage de trousseau, utilisez la notation DNS inverse :<br /><br />*com.companyName.KeychainGroup*|
|Personal VPN|Activez Personal VPN (VPN personnel) pour permettre à votre application de créer et contrôler une configuration VPN système personnalisée à l’aide de l’infrastructure Network Extension.||
|Notifications push|Le service de notification Push Apple (APN) permet à une application qui ne s’exécute pas au premier plan de notifier l’utilisateur que des informations sont à sa disposition.|Pour que les notifications Push fonctionnent, vous devez utiliser un profil de configuration spécifique à l’application.<br /><br />Suivez la procédure décrite dans la [documentation pour développeurs Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Configuration d’accessoire sans fil|L’activation de la configuration d’accessoire sans fil a pour effet d’ajouter le framework External Accessory à votre projet et permet à votre application de configurer les accessoires Wi-Fi MFi.||

### <a name="steps-to-enable-entitlements"></a>Étapes d’activation des droits

1. Activez les fonctionnalités dans votre application :

    a.  Dans Xcode, accédez à la cible de votre application, puis cliquez sur **Capabilities** (Fonctionnalités).

    b.  Activez les fonctionnalités appropriées. Pour obtenir des informations détaillées sur chaque fonctionnalité et pour savoir comment déterminer les valeurs correctes, consultez [Adding Capabilities](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) dans la bibliothèque du développeur iOS.

    c.  Notez les ID que vous avez créés pendant le processus. Il peuvent également être appelés valeurs `AppIdentifierPrefix`.

    d.  Générer et signez votre application à encapsuler.

2. Activez les droits dans votre profil de configuration :

    a.  Connectez-vous à l’Apple Developer Member Center.

    b.  Créez un profil de configuration pour votre application. Pour obtenir des instructions, consultez la page [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/) (Comment obtenir la configuration requise pour Intune App Wrapping Tool for iOS).

    c.  Dans votre profil de configuration, activez les mêmes droits que ceux que vous avez dans votre application. Vous devez fournir les mêmes ID (valeurs `AppIdentifierPrefix`) que ceux que vous avez spécifiés pendant le développement de votre application. 

    d.  Terminez l’Assistant de configuration de profil, puis téléchargez votre fichier.

3. Assurez-vous que vous avez rempli toutes les conditions préalables, puis encapsulez l’application.

### <a name="troubleshoot-common-errors-with-entitlements"></a>Résoudre les erreurs courantes liées aux droits
Si App Wrapping Tool for iOS affiche une erreur de droit, essayez d’exécuter les étapes de dépannage suivantes.

|Problème|Cause|Résolution|
|---------|---------|--------------|
|Impossible d’analyser les droits générés à partir de l’application d’entrée.|L’outil de création de package de restrictions d’application ne peut pas lire le fichier de droits qui a été extrait de l’application. Le fichier de droits est peut être incorrect.|Examinez le fichier de droits de votre application. Les instructions suivantes expliquent comment effectuer cette opération. Au moment d’inspecter le fichier de droits, assurez-vous que la syntaxe est correcte. Le fichier doit être au format XML.|
|Il manque des droits dans le profil de configuration (les droits manquants sont répertoriés). Recréez le package de l’application avec un profil de configuration qui contienne ces droits.|Il y a une incohérence entre les droits activés dans le profil de configuration et les fonctionnalités activées dans l’application. Cette incohérence vaut aussi pour les ID associés à des fonctionnalités particulières (telles que les groupes d’applications et l’accès à un trousseau).|En règle générale, vous pouvez créer un nouveau profil de configuration qui active les mêmes fonctionnalités que l’application. Quand les ID du profil et de l’application ne correspondent pas, l’outil de création de package de restrictions d’application remplace les ID, dans la mesure du possible. Si vous obtenez encore cette erreur après avoir créé un profil de configuration, vous pouvez essayer de supprimer les droits de l’application à l’aide du paramètre –e (voir la section Utilisation du paramètre –e pour supprimer les droits d’accès).|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Rechercher les droits existants d’une application signée
Pour examiner les droits existants d’une application signée et le profil de configuration :

1. Recherchez le fichier .ipa et remplacez son extension par .zip.

2. Développez le fichier .zip. Un dossier Payload contenant votre ensemble .app est alors généré.

3. Utilisez l’outil codesign pour vérifier les droits de l’ensemble .app, où `YourApp.app` correspond au nom réel de votre ensemble .app :

    ```bash
    codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4. Utilisez l’outil de sécurité pour vérifier les droits du profil de configuration incorporé de l’application, où `YourApp.app` correspond au nom réel de votre ensemble .app.

    ```bash
    security cms -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Supprimer les droits d’accès d’une application à l’aide du paramètre –e
Cette commande supprime toutes les fonctionnalités activées dans l’application qui ne figurent pas dans le fichier de droits. Si vous supprimez des fonctionnalités qui sont utilisées par l’application, elle risque de se bloquer. Vous pourriez par exemple supprimer des fonctionnalités manquantes dans une application générée par un fournisseur qui dispose de toutes les fonctionnalités par défaut.

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Sécurité et confidentialité pour l’outil de création de package de restrictions d’application
Respectez les bonnes pratiques de sécurité et de confidentialité suivantes quand vous utilisez l’outil de création de package de restrictions d’application.

- Le certificat de signature, le profil d’approvisionnement et l’application métier que vous spécifiez doivent se trouver sur le même ordinateur macOS que celui que vous utilisez pour exécuter l’outil de création de package de restrictions d’application. Si les fichiers se trouvent sur un chemin UNC, vérifiez qu’ils sont accessibles à partir de l’ordinateur macOS. Le chemin d'accès doit être sécurisé via la signature SMB ou la sécurité IPsec.

    L’application encapsulée importée dans la console d’administration doit se trouver sur le même ordinateur que celui sur lequel vous exécutez l’outil. Si le fichier se trouve dans un chemin UNC, assurez-vous qu’il est accessible sur l’ordinateur qui exécute la console d’administration. Le chemin d'accès doit être sécurisé via la signature SMB ou la sécurité IPsec.

- L’environnement où l’outil de création de package de restrictions d’application est téléchargé à partir du site du dépôt GitHub doit être sécurisé par le biais de la signature SMB ou la sécurité IPsec.

- L’application que vous traitez doit provenir d’une source digne de confiance pour garantir la protection contre les attaques.

- Vérifiez que le dossier de sortie que vous spécifiez dans l’outil de création de package de restrictions d’application est sécurisé, en particulier s’il s’agit d’un dossier distant.

- Les applications iOS qui incluent une boîte de dialogue de chargement de fichier peuvent permettre aux utilisateurs de contourner les restrictions relatives aux opérations couper, copier et coller appliquées à l’application. Par exemple, un utilisateur peut utiliser la boîte de dialogue de téléchargement de fichier pour télécharger une capture d'écran des données de l'application.

- Quand vous analysez le dossier de documents sur votre appareil depuis une application encapsulée, vous risquez de voir un dossier nommé .msftintuneapplauncher. Si vous modifiez ou supprimez ce fichier, cela peut affecter le bon fonctionnement des applications restreintes.

## <a name="intune-app-wrapping-tool-for-ios-with-citrix-mdx-mvpn"></a>Intune App Wrapping Tool pour iOS avec mVPN Citrix MDX
Cette fonctionnalité est une intégration avec le wrapper d’applications Citrix MDX pour iOS. Cette intégration consiste simplement en un indicateur de ligne de commande supplémentaire et facultatif, `-citrix`, ajouté à la version générale d’Intune App Wrapping Tools.

### <a name="requirements"></a>Configuration requise

Pour pouvoir utiliser l’indicateur `-citrix`, il est nécessaire d’installer également le [wrapper d’applications Citrix MDX pour iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) sur le même ordinateur macOS. Les téléchargements se trouvent sur [Téléchargements Citrix XenMobile](https://www.citrix.com/downloads/xenmobile/) et sont réservés aux clients de Citrix une fois connectés. Vérifiez que l’installation s’effectue dans l’emplacement par défaut : `/Applications/Citrix/MDXToolkit`. 

> [!NOTE] 
> La prise en charge de l’intégration entre Intune et Citrix est limitée aux appareils iOS 10 (ou version ultérieure).

### <a name="use-the--citrix-flag"></a>Utiliser l’indicateur `-citrix`
Exécutez simplement votre commande générale d’inclusion d’applications dans un wrapper en ajoutant l’indicateur `-citrix`. L’indicateur `-citrix` ne prend à l’heure actuelle pas d’arguments.

**Format d’utilisation** :

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioing profile paths>] [-citrix]
```

**Exemple de commande** :

```bash
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true -citrix
```

## <a name="getting-logs-for-your-wrapped-applications"></a>Obtention des journaux pour vos applications encapsulées
Procédez comme suit pour obtenir des journaux pour vos applications encapsulées pendant le dépannage.

1. Accédez à l’app Réglages iOS sur votre appareil et sélectionnez votre application métier.
2. Basculez la **console Diagnostics** sur **On**.
3. Lancez votre application métier.
4. Cliquez sur le lien « Get Started » (Démarrer).
5. Vous pouvez maintenant partager des journaux par e-mail ou en les copiant dans un emplacement OneDrive.

> [!NOTE]
> La fonctionnalité de journalisation est activée pour les applications qui ont été encapsulées avec Intune App Wrapping Tool version 7.1.13 ou ultérieure.

## <a name="see-also"></a>Voir aussi

- [Décider comment préparer les applications pour la gestion des applications mobiles avec Microsoft Intune](apps-prepare-mobile-application-management.md)
- [Questions, problèmes et solutions concernant les stratégies et les profils d’appareil](../configuration/device-profile-troubleshoot.md)
- [Utiliser le SDK pour activer des applications pour la gestion des applications mobiles](app-sdk.md)
