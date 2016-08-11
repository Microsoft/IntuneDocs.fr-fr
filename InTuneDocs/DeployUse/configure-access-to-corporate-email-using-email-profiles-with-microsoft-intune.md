---
title: "Accéder à la messagerie d’entreprise en utilisant des profils de messagerie | Microsoft Intune"
description: "Vous pouvez utiliser des paramètres de profil de messagerie pour configurer les paramètres d’accès à la messagerie électronique pour des clients de messagerie spécifiques sur les appareils mobiles."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/021/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 10f0cd61-e514-4e44-b13e-aeb85a8e53ae
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: cddc1a68b14520774555416dcd496a06a0f89385


---

# Configurer l’accès à la messagerie d’entreprise à l’aide de profils de messagerie avec Microsoft Intune
De nombreuses plateformes mobiles incluent un client de messagerie *natif* fourni avec le système d’exploitation.  Certains de ces clients peuvent être configurables à l’aide de profils de messagerie, décrits dans cette rubrique.

Si vous avez besoin d’une protection supplémentaire contre la perte de données, choisissez l’[accès conditionnel](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) qui contrôle l’accès à la boîte aux lettres de l’utilisateur pour n’importe quel client de messagerie, notamment les clients de messagerie natifs.

Vous pouvez utiliser des paramètres de profil de messagerie pour configurer les paramètres d’accès à la messagerie électronique pour des clients de messagerie spécifiques sur les appareils mobiles. La plupart des plateformes mobiles incluent un client de messagerie *natif* fourni avec le système d’exploitation.  Sur les plateformes prises en charge, les clients de messagerie natifs peuvent être configurés par Microsoft Intune pour permettre aux utilisateurs d’accéder à leur messagerie d’entreprise sur les appareils personnels sans aucune configuration supplémentaire.  

Les administrateurs informatiques ou les utilisateurs peuvent choisir d’installer d’autres clients de messagerie, par exemple Microsoft Outlook pour Android ou iOS.  Ces clients de messagerie peuvent ne pas prendre en charge les profils de messagerie et ne sont pas configurables à l’aide des profils de messagerie Microsoft Intune.  

Vous pouvez utiliser des profils de messagerie pour configurer le client de messagerie natif sur les types d’appareils suivants :
-   Windows Phone 8 et versions ultérieures
-   Windows 10 Desktop, Windows 10 Mobile et versions ultérieures
-   iOS 7.1 et versions ultérieures
-   Samsung KNOX Standard (4.0 et versions ultérieures)


Outre la configuration d’un compte de messagerie sur l’appareil, vous pouvez configurer des paramètres de synchronisation tels que le volume de courrier électronique à synchroniser et, en fonction du type d’appareil, les types de contenu à synchroniser.
>[!NOTE]
>
>Si l’utilisateur a installé un profil de messagerie avant de configurer un profil via Intune, le résultat du déploiement du profil de messagerie Intune dépend de la plate-forme d’appareil :

>-**iOS**: Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Le profil de messagerie en double que l’utilisateur a créé bloque le déploiement d’un profil créé par un administrateur Intune. Il s’agit d’un problème courant parce que les utilisateurs iOS créent généralement un profil de messagerie, puis s’inscrivent. Le portail d’entreprise informe les utilisateurs qu’ils ne sont pas conformes en raison de leur profil de messagerie configuré manuellement et les invite à supprimer ce profil. Les utilisateurs doivent supprimer leur profil de messagerie pour que le profil Intune puisse être déployé. Pour éviter ce problème, demandez à vos utilisateurs de s’inscrire avant d’installer le profil de messagerie et d’autoriser Intune à déployer le profil.

>-**Windows** : Intune détecte un profil de messagerie existant en double, en fonction de l’adresse e-mail et du nom d’hôte. Intune remplace le profil de messagerie existant que l’utilisateur a créé.

>-**Samsung KNOX** : Intune identifie un compte de messagerie en double en fonction de l’adresse e-mail et le remplace par le profil Intune. Si l’utilisateur configure ce compte, il est remplacé à nouveau par le profil Intune. Remarque : cela peut entraîner une certaine confusion pour l’utilisateur dont la configuration de compte est remplacée.

>Étant donné que Samsung KNOX n’utilise pas le nom d’hôte pour identifier le profil, nous vous recommandons de ne pas créer plusieurs profils de messagerie à déployer à la même adresse e-mail sur des hôtes différents, car ils se remplaceront l’un l’autre.
    

## Profils de messagerie sécurisés
Vous pouvez sécuriser les profils de messagerie à l’aide de l’une des deux méthodes suivantes :

### Certificats
Quand vous créez le profil de messagerie, vous choisissez un profil de certificat que vous avez créé précédemment dans Intune. Il s’agit du certificat d’identité, qui est utilisé pour l’authentification par rapport à un profil de certificat approuvé (ou un certificat racine) pour établir le fait que l’utilisateur est autorisé à se connecter. Le certificat approuvé est déployé sur l’ordinateur qui authentifie la connexion de messagerie, en général le serveur de messagerie natif.

Pour plus d’informations sur la création et l’utilisation des profils de certificat dans Intune, consultez [Secure resource access with certificate profiles](secure-resource-access-with-certificate-profiles.md) (Sécuriser l’accès aux ressources avec des profils de certificat).

### Nom d'utilisateur et mot de passe
L’utilisateur s’authentifie auprès du serveur de messagerie natif en fournissant son nom d’utilisateur et son mot de passe.

Comme le mot de passe n'est pas contenu dans le profil de messagerie, l'utilisateur doit le fournir quand il se connecte à sa messagerie électronique.

### Créer un profil de messagerie

1.  Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), cliquez sur **Stratégie** &gt; **Ajouter une stratégie**.

2.  Configurez l'un des types de stratégies suivants :

    -   **Profil de messagerie pour Samsung KNOX Standard (4.0 et versions ultérieures)**

    -   **Profil de messagerie (iOS 7.1 et versions ultérieures)**

    -   **Profil de messagerie (Windows Phone 8 et versions ultérieures)**

    -   **Profil de messagerie (Windows 10 Desktop et Mobile, et versions ultérieures)**

    Vous pouvez uniquement créer et déployer une stratégie de profil de messagerie personnalisée. Les paramètres recommandés ne sont pas disponibles.

3.  Utilisez le tableau suivant pour vous aider à configurer les paramètres de profil de messagerie :
    |Nom du paramètre|Plus d'informations|
    |----------------|-----------------------------------------------------------------------------|
    |**Nom**|Nom unique du profil de messagerie.|
    |**Description**|Description qui vous aide à identifier ce profil.|
    |**Hôte**|Nom d’hôte du serveur de votre société qui héberge votre service de messagerie natif.|
    |**Nom du compte**|Nom complet du compte de messagerie, tel qu’il apparaîtra aux utilisateurs sur leurs appareils.|
    |**Nom d'utilisateur**|Façon dont le nom d’utilisateur du compte de messagerie est obtenu. Sélectionnez **Nom d’utilisateur** pour un serveur Exchange local ou **Nom principal de l’utilisateur** pour Office 365.|
    |**Adresse de messagerie**|Façon dont l’adresse de messagerie de l’utilisateur est générée sur chaque appareil. Sélectionnez **Adresse SMTP principale** pour utiliser l’adresse SMTP principale pour vous connecter à Exchange ou **Nom principal de l’utilisateur** pour utiliser le nom principal complet comme adresse de messagerie.|
    |**Méthode d’authentification** (Samsung KNOX et iOS)|Sélectionnez **Nom d’utilisateur et mot de passe** ou **Certificats** comme méthode d’authentification utilisée par le profil de messagerie.|
    |**Sélectionner un certificat client pour l’authentification client (certificat d’identité)** (Samsung KNOX et iOS)|Sélectionnez le certificat SCEP client que vous avez créé précédemment qui servira à authentifier la connexion Exchange. Pour plus d’informations sur la façon de créer des profils de certificat dans Intune, consultez [Sécuriser l’accès aux ressources avec des profils de certificat](secure-resource-access-with-certificate-profiles.md).<br /><br />Cette option est visible uniquement quand la méthode d'authentification est **Certificats**.|
    |**Utiliser S/MIME** (Samsung KNOX et iOS)|Envoyez des messages électroniques en utilisant le chiffrement S/MIME.|
    |**Certificat de signature** (Samsung KNOX et iOS)|Sélectionnez le certificat de signature qui sera utilisé pour signer le courrier électronique sortant.<br /><br />Cette option est visible uniquement quand vous sélectionnez **Utiliser S/MIME**.|
    |**Nombre de jours de courrier électronique à synchroniser**|Nombre de jours de courrier électronique à synchroniser, ou sélectionnez **Illimité** pour synchroniser tous les messages disponibles.|
    |**Planification de la synchronisation** (Samsung KNOX, Windows Phone 8 et versions ultérieures, Windows 10)|Sélectionnez la planification selon laquelle les appareils vont synchroniser les données d'Exchange Server. Vous pouvez également sélectionner **À mesure que les messages arrivent** pour synchroniser les données dès qu’elles arrivent ou **Manuel** pour que ce soit l’utilisateur de l’appareil qui lance la synchronisation.|
    |**Utiliser SSL**|Utilisez la communication SSL (Secure Sockets Layer) pour envoyer des messages électroniques, en recevoir et communiquer avec Exchange Server.<br /><br />Pour les appareils qui exécutent Samsung KNOX 4.0 ou vers ultérieure, vous devez exporter le certificat SSL de votre serveur Exchange et le déployer comme profil de certificat approuvé par Android dans Intune. Intune ne prend pas en charge l’accès à ce certificat s’il est installé sur le serveur Exchange par d’autres moyens.|
    |**Type de contenu à synchroniser**|Sélectionnez les types de contenu à synchroniser avec des appareils.|
    |**Autoriser l’envoi de courrier électronique à partir d’applications tierces** (iOS uniquement)|Autoriser l’utilisateur à sélectionner ce profil en tant que compte par défaut pour l’envoi d’e-mails et autoriser les applications tierces à ouvrir les e-mails dans l’application de messagerie native, par exemple pour y joindre des fichiers.|

    > [!IMPORTANT]
    > Si vous avez déployé un profil de messagerie et que vous souhaitez ensuite modifier les valeurs **Hôte** ou **Adresse de messagerie**, vous devez supprimer le profil de messagerie existant et en créer un avec les valeurs requises.

4.  Quand vous avez terminé, cliquez sur **Enregistrer la stratégie**.

La nouvelle stratégie s'affiche sous le nœud **Stratégies de configuration** de l'espace de travail **Stratégie** .

## Déploiement de la stratégie

1.  Dans l’espace de travail **Stratégie** , sélectionnez la stratégie à déployer, puis cliquez sur **Gérer le déploiement**.

2.  Dans la boîte de dialogue **Gérer le déploiement** :

    -   **Pour déployer la stratégie** : sélectionnez un ou plusieurs groupes sur lesquels déployer la stratégie, puis cliquez sur **Ajouter** &gt; **OK**.

    -   **Pour fermer la boîte de dialogue sans la déployer**, cliquez sur **Annuler**.

Un récapitulatif de l'état et des alertes identifient, dans la page **Vue d'ensemble** de l'espace de travail **Stratégie** , les problèmes liés à la stratégie qui nécessitent votre attention. En outre, le Tableau de bord contient un récapitulatif de l'état.

> [!NOTE]
> Si vous souhaitez supprimer un profil de messagerie d'un appareil, modifiez le déploiement et supprimez les groupes dont l'appareil est membre.



<!--HONumber=Aug16_HO1-->


