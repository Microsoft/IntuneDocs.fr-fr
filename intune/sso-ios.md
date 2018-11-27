---
title: Ajouter l’authentification unique pour les appareils iOS dans Microsoft Intune - Azure | Microsoft Docs
description: Dans Microsoft Intune, créez, configurez, autorisez ou activez les appareils iOS de manière à ce qu’ils utilisent l’authentification unique (SSO) au lieu d’un mot de passe pour s’authentifier auprès des ressources et des données de votre organisation. Pour utiliser l’authentification unique, créez un profil de configuration d’appareil, puis entrez l’UPN, l’ID de l’appareil, vos applications et un certificat pour authentifier l’utilisateur et l’appareil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c4d19807ecfcc33b957d5f6582f095427dbf978e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190198"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>Utiliser un appareil iOS avec authentification unique dans Microsoft Intune

La plupart des applications métier nécessitent un certain niveau d’authentification utilisateur pour prendre en charge la sécurité. Dans de nombreux cas, cette authentification oblige l’utilisateur à entrer les informations d’identification plusieurs fois, ce qui est frustrant. Pour améliorer l’expérience utilisateur, les développeurs peuvent créer des applications qui utilisent l’authentification unique (SSO), réduisant ainsi le nombre de fois où un utilisateur doit entrer des informations d’identification.

Cet article vous montre comment activer l’authentification unique pour les appareils iOS à l’aide d’un profil de configuration d’appareil dans Microsoft Intune.

## <a name="before-you-begin"></a>Avant de commencer

Veillez à disposer d’une application codée pour rechercher le magasin d’informations d’identification utilisateur dans la charge utile d’authentification unique sur l’appareil iOS.

## <a name="create-the-sso-profile"></a>Créer le profil d’authentification unique

1. Dans le [Portail Azure](https://portal.azure.com), sélectionnez **Tous les services**, filtrez sur **Intune**, puis sélectionnez **Microsoft Intune**.
2. Choisissez **Configuration de l’appareil** > **Profils** > **Créer un profil**.
3. Entrez les paramètres suivants :

    - **Nom** : entrez un nom pour le profil, par exemple `ios sso profile`.
    - **Description** : entrez une description avec des termes clés pour faciliter la recherche du profil dans la liste.
    - **Plateforme** : choisissez **iOS**.
    - **Type de profil** : choisissez **Fonctionnalités de l’appareil**.

4. Choisissez **authentification unique**.

    ![Volet Authentification unique](./media/sso-blade.png)

5. entrez les paramètres suivants : 

    - **Attribut de nom d’utilisateur d’AAD** : Intune recherche cet attribut pour chaque utilisateur dans Azure AD. Ensuite, Intune renseigne le champ correspondant (par exemple, UPN) avant de générer la charge utile XML installée sur l’appareil. Les options disponibles sont les suivantes :
    
        - **Nom d’utilisateur principal** : l’UPN est analysé de la façon suivante :

            ![Attribut de nom d’utilisateur](media/User-name-attribute.png)

            Vous pouvez également remplacer le domaine par le texte que vous entrez dans la zone de texte **Domaine**.

            Par exemple, la société Contoso peut avoir plusieurs sous-régions telles qu’Amérique du Nord, Europe et Asie. Elle peut souhaiter que les utilisateurs en Asie utilisent la charge utile d’authentification unique et que l’application exige le nom d’utilisateur principal au format `username@asia.contoso.com`. Dans ce cas, si vous sélectionnez **Nom d’utilisateur principal**, par défaut, le domaine pour chaque utilisateur est extrait d’Azure AD et peut être *contoso.com*. Si vous le souhaitez, vous pouvez créer spécialement cette charge utile pour les utilisateurs en Asie, et remplacer le domaine par la valeur *asia.contoso.com*. Maintenant, le nom UPN de l’utilisateur final devient username@asia.contoso.com au lieu de username@contoso.com.

        - **ID d’appareil Intune** : Intune sélectionne automatiquement l’ID d’appareil Intune. 

            Par défaut, les applications ont besoin d’utiliser uniquement l’ID d’appareil. Mais si votre application utilise le domaine *et* l’ID d’appareil, vous pouvez taper le domaine dans la zone de texte **Domaine**.

            > [!NOTE]
            > Par défaut, vous devez laisser le champ de domaine vide si vous utilisez l’ID d’appareil.

    - **Domaine** : partie domaine de l’URL.
    
    - **Préfixes d’URL qui utiliseront l’authentification unique** : **ajoutez** toutes les URL de votre organisation qui nécessitent une authentification unique de l’utilisateur. 

        Par exemple, quand un utilisateur se connecte à l’un de ces sites, l’appareil iOS utilise les informations d’identification d’authentification unique. L’utilisateur n’a pas besoin d’entrer d’informations d’identification supplémentaires. Toutefois, si vous avez activé l’authentification multifacteur, les utilisateurs doivent entrer la deuxième authentification.

        > [!NOTE]
        > Ces URL doivent être spécifiées sous la forme de noms de domaine complets correctement mis en forme. Apple exige que les URL soient spécifiées au format `http://<yourURL.domain>`.

        Les modèles de correspondance d’URL doivent commencer par `http://` ou `https://`. Une correspondance de chaîne simple est effectuée. Ainsi, le préfixe d’URL `http://www.contoso.com/` ne correspond pas à `http://www.contoso.com:80/`. Toutefois, avec iOS 10.0 ou ultérieur, vous pouvez utiliser un seul caractère générique (\*) pour entrer toutes les valeurs correspondantes. Par exemple, `http://*.contoso.com/` correspond à la fois à `http://store.contoso.com/` et à `http://www.contoso.com`.

        Les modèles `http://.com` et `https://.com` correspondent respectivement à toutes les URL HTTP et HTTPS.
    
    - **Applications qui utiliseront l’authentification unique** : **ajoutez** les applications sur les appareils de l’utilisateur final qui peuvent utiliser l’authentification unique. 

        Le tableau `AppIdentifierMatches` doit contenir des chaînes qui correspondent aux ID de bundles d’applications. Ces chaînes peuvent être des correspondances exactes (telles que `com.contoso.myapp`) ou entrez une correspondance de préfixe sur l’ID de bundle à l’aide du caractère générique \*. Le caractère générique doit apparaître après un point (.), et ne peut apparaître qu’une seule fois, à la fin de la chaîne (par exemple `com.contoso.*`). Quand un caractère générique est inclus, toute application dont l’ID de bundle commence par le préfixe bénéficie de l’accès au compte.

        Utilisez **Nom de l’application** pour entrer un nom convivial afin de faciliter l’identification de l’ID de bundle.
    
    - **Certificat de renouvellement des informations d’identification** : si vous utilisez des certificats pour l’authentification (pas des mots de passe), sélectionnez le certificat SCEP ou PFX déployé pour l’utilisateur en tant que certificat d’authentification. En général, il s’agit du même certificat que celui déployé pour l’utilisateur pour d’autres profils, tels que VPN, Wi-Fi ou e-mail.

6. Sélectionnez **OK** > **OK** > **Créer** pour enregistrer vos changements et créer le profil. Une fois créé, il apparaît dans la liste **Configuration de l’appareil - Profils**. 

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir des informations supplémentaires sur la configuration des fonctionnalités des appareils, consultez [Guide pratique pour configurer les paramètres de fonctionnalités d’appareil dans Microsoft Intune](device-features-configure.md).

[Attribuez ce profil](device-profile-assign.md) à vos appareils iOS.
