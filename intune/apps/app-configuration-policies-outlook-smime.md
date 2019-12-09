---
title: Configurer S/MIME avec Outlook pour iOS dans Microsoft Intune
description: Comprenez le fonctionnement de S/MIME avec Outlook pour iOS dans Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 348d1fe2fd236a2af11f7e58dc11530a5ce397bc
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564201"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Configurer S/MIME avec Outlook pour iOS

S/MIME (Secure/Multipurpose Internet Mail Extensions) fournit une couche de sécurité supplémentaire pour les e-mails envoyés vers et à partir d’un compte Exchange ActiveSync (EAS). [Microsoft Outlook](https://aka.ms/omsmime) peut utiliser S/MIME pour permettre aux utilisateurs de chiffrer les messages et pièces jointes sortants, ce qui garantit que seul le destinataire prévu peut lire et accéder au contenu des messages lors de l’utilisation de comptes Office 365. Les utilisateurs peuvent également signer numériquement un message, ce qui permet aux destinataires de vérifier l’identité de l’expéditeur et de confirmer que le message n’a pas été falsifié. Cette fonctionnalité est rendue possible par les certificats. Pour plus d'informations, consultez [Présentation de S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> Cette rubrique explique comment déployer des certificats racine approuvés par le biais de [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Microsoft Endpoint Manager est une plateforme de gestion de points de terminaison intégrée unique pour la gestion de tous vos points de terminaison. Ce Centre d’administration de Microsoft Endpoint Manager intègre ConfigMgr et Microsoft Intune.

## <a name="about-message-encryption"></a>À propos du chiffrement des messages
Les utilisateurs peuvent envoyer des messages chiffrés à des personnes de leur organisation et à des personnes extérieures à leur organisation s’ils disposent de la partie publique des certificats de chiffrement. Les clés privées associées aux certificats de chiffrement doivent toujours être protégées et sécurisées par le destinataire du message chiffré. La clé privée du certificat de chiffrement est utilisée pour déchiffrer le message par le destinataire.

Les messages chiffrés ne peuvent être lus que par les destinataires qui ont le certificat correspondant à celui qui a chiffré le message. Si vous essayez d’envoyer un message chiffré à des destinataires dont le certificat de chiffrement n’est pas disponible, l’application vous invite à supprimer ces destinataires avant d’envoyer l’e-mail.

## <a name="about-digital-signatures"></a>À propos des signatures numériques
Un message signé numériquement garantit au destinataire que le message n’a pas été falsifié et que l’identité de l’expéditeur est authentique. Les destinataires peuvent uniquement vérifier la signature numérique s’ils utilisent un client de messagerie qui prend en charge S/MIME.

## <a name="prerequisites"></a>Prérequis
- Outlook pour iOS prend uniquement en charge S/MIME sur les comptes Office 365.
- S/MIME doit être configuré pour Office 365. Pour plus d'informations, consultez [Guide pratique pour configurer S/MIME dans Office 365](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516).
- Vous devez disposer d’une autorité de certification qui peut émettre des certificats qui peuvent être utilisés pour la signature et le chiffrement.
- Déployez des certificats racines approuvés par le biais d’Endpoint Manager. Pour plus d’informations, consultez [Créer des profils de certificat approuvés](~/protect/certificates-configure.md#create-trusted-certificate-profiles).
- Les certificats de chiffrement doivent être importés dans Endpoint Manager. Pour plus d’informations, consultez [Configurer et utiliser des certificats PKCS importés avec Intune](~/protect/certificates-imported-pfx-configure.md).
- Installez et configurez le connecteur PFX pour Microsoft Intune. Pour plus d’informations, consultez [Télécharger, installer et configurer PFX Certificate Connector pour Microsoft Intune](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- Les appareils doivent être inscrits dans la gestion des appareils mobiles pour recevoir automatiquement les certificats racine et S/MIME approuvés à partir d’Endpoint Manager.

> [!IMPORTANT]
> Vous devez télécharger et installer le connecteur PFX mis à jour (version 6.1911.11.0 ou ultérieure) pour Microsoft Intune pour utiliser des certificats de chiffrement S/MIME avec Outlook pour iOS.

## <a name="smime-support-in-outlook-for-ios"></a>Prise en charge de S/MIME dans Outlook pour iOS
Outlook pour iOS prend en charge la signature S/MIME et le chiffrement des messages à l’aide de certificats. De nombreux clients possèdent des certificats de signature et de chiffrement distincts, par opposition à un seul certificat prenant en charge la signature et le chiffrement. Les certificats de signature sont généralement uniques sur les appareils inscrits d’un utilisateur individuel, tandis que les certificats de chiffrement sont partagés entre les appareils inscrits d’un utilisateur individuel. Souvent, les utilisateurs auront utilisé S/MIME pendant des années et auront utilisé des certificats de chiffrement différents au fil du temps, à mesure que les certificats sont renouvelés. Les historiques de certificats de chiffrement, y compris leurs clés privées, doivent être présents sur l’appareil de l’utilisateur afin que les e-mails qui ont pu être chiffrés avec un de ces certificats par le passé puissent être lus. Il est également possible d’avoir un seul certificat prenant en charge la signature et le chiffrement.

Outlook pour iOS prend en charge deux méthodes pour remettre des certificats aux appareils afin qu’ils puissent être utilisés pour S/MIME :

- **Les utilisateurs** peuvent s’envoyer des certificats S/MIME à eux-mêmes et les installer à partir de pièces jointes dans Outlook pour iOS sur leurs appareils mobiles.
- **Les administrateurs** peuvent importer des historiques de certificats de chiffrement à partir d’une autorité de certification dans Endpoint Manager. Endpoint Manager remet automatiquement ces certificats à tous les appareils inscrits par l’utilisateur. En général, le protocole d’inscription de certificats simple (SCEP) est utilisé pour la signature des certificats. Avec SCEP, la clé privée est générée et stockée sur l’appareil inscrit et un certificat unique est remis à chaque appareil inscrit par un utilisateur, et peut être utilisé pour la non-répudiation. Les administrateurs importent des historiques de certificats de chiffrement pour leurs utilisateurs sur Endpoint Manager, qui remet ensuite tous les certificats de chiffrement de l’utilisateur à n’importe quel appareil qu’ils inscrivent. Enfin, Endpoint Manager prend en charge les informations d’identification dérivées pour les clients qui ont besoin de la prise en charge de la norme NIST 800-157. Sur iOS, le Portail d’entreprise est utilisé pour récupérer des certificats de signature et de chiffrement à partir d’Intune.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Configuration d’Outlook pour S/MIME iOS dans Endpoint Manager
Pour configurer Outlook pour S/MIME iOS dans Endpoint Manager, y compris pour la diffusion automatique de certificats S/MIME qu’Outlook pour iOS peut utiliser, procédez comme suit :

### <a name="add-the-microsoft-outlook-app"></a>Ajouter l’application Microsoft Outlook
1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Ajoutez l’application Microsoft Outlook pour iOS de l’App Store à Endpoint Manager ou synchronisez Outlook pour iOS à partir du Programme d’achat en volume (VPP) Apple. Pour plus d’informations, consultez [Ajouter des applications de l’App Store iOS dans Microsoft Intune](~/apps/store-apps-ios.md) ou [Guide pratique pour gérer les applications iOS et macOS achetées par le biais d’un programme d’achat en volume Apple avec Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Créer la stratégie de configuration Outlook pour S/MIME iOS

Les étapes suivantes vous permettent de créer et de configurer la stratégie S/MIME d’Outlook pour iOS dans Endpoint Manager. Ces paramètres fournissent la remise automatisée des certificats de signature et de chiffrement.

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) et sélectionnez **Applications** > **Stratégies de configuration des applications** > **Ajouter**.<br>
Le volet **Ajouter une stratégie de configuration** s’affiche.
2. Entrez le **nom** et la **description** de la stratégie de configuration.
3. Sélectionnez **Appareils gérés** comme **Type d’inscription de l’appareil**.
4. Sélectionnez **iOS/iPadOS** comme **Plateforme**.
5. Cliquez sur **Sélectionner l’application requise** pour rechercher et associer l’application Microsoft Outlook pour iOS que vous avez ajoutée précédemment. 
6. Cliquez sur **Paramètres de configuration** pour ajouter des paramètres de configuration. 
    - Sélectionnez **Utiliser le concepteur de configuration** en regard de **Format des paramètres de configuration** et acceptez les paramètres par défaut. Pour plus d’informations, consultez [Paramètres de configuration Microsoft Outlook](~/apps/app-configuration-policies-outlook.md).
7. Cliquez sur **S/MIME** pour afficher les **Paramètres S/MIME d’Outlook**.

    ![Capture d’écran des paramètres S/MIME d’Outlook pour iOS](./media/app-configuration-policies-outlook-smime/app-configuration-policies-outlook-smime-01.png)

8. Définissez **Activer S/MIME** sur **Oui**.
9. Définissez **Déployer les certificats S/MIME à partir d’Intune** sur **Oui**.
10. Sous **Certificats de signature** en regard de **Type de profil de certificat**, choisissez une des options suivantes :
    - **SCEP** : crée un certificat unique pour l’appareil et l’utilisateur qui peut être utilisé par Microsoft Outlook pour la signature. Pour obtenir des informations connexes, consultez [Configurer l’infrastructure pour prendre en charge SCEP avec Intune](~/protect/certificates-scep-configure.md) et [Créer un profil de certificat SCEP](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **Certificats importés par PKCS** : utilise un certificat unique pour l’utilisateur, mais peut être partagé entre plusieurs appareils et a été importé dans Endpoint Manager par l’administrateur au nom de l’utilisateur. Le certificat est remis à tous les appareils inscrits par un utilisateur. Endpoint Manager terminaison sélectionne automatiquement le certificat importé qui prend en charge la signature à remettre à l’appareil qui correspond à l’utilisateur inscrit.
    - **Informations d’identification dérivées** : utilise un certificat qui se trouve déjà sur l’appareil et qui peut être utilisé pour la signature. Le certificat doit être récupéré sur l’appareil à l’aide des flux d’informations d’identification dérivés dans Intune.
11. Sous **Certificats de chiffrement** en regard de **Type de profil de certificat**, choisissez une des options suivantes :
    - **Certificats importés par PKCS** : remet tous les certificats de chiffrement qui ont été importés dans Endpoint Manager par l’administrateur sur tous les appareils qu’un utilisateur inscrit dans Endpoint Manager, et sélectionne automatiquement les certificats importés prenant en charge le chiffrement à remettre à l’appareil qui correspond à l’utilisateur inscrit.
    - **Informations d’identification dérivées** : utilise un certificat qui se trouve déjà sur l’appareil et qui peut être utilisé pour la signature. Le certificat doit être récupéré sur l’appareil à l’aide des flux d’informations d’identification dérivés dans Intune.
12. En regard de **Notifications de l’utilisateur final**, choisissez de notifier les utilisateurs finaux en sélectionnant **Portail d’entreprise** ou **E-mail** pour récupérer les certificats S/MIME pour Outlook pour iOS.

    Sur iOS, les utilisateurs doivent utiliser l’application Portail d’entreprise pour récupérer leurs certificats S/MIME. Endpoint Manager informe l’utilisateur qu’il doit lancer le Portail d’entreprise pour récupérer ses certificats S/MIME via la section Notifications du Portail d’entreprise, une notification push et/ou un e-mail. Si vous cliquez sur une des notifications, l’utilisateur arrive sur une page d’accueil qui l’informe de la progression de la récupération des certificats. Une fois les certificats récupérés, l’utilisateur peut utiliser S/MIME à partir de Microsoft Outlook pour iOS pour signer et chiffrer des e-mails.
    
    Les notifications de l’utilisateur final incluent les options suivantes :
       - **Portail d’entreprise** : si cette option est sélectionnée, les utilisateurs recevront une notification push sur leur appareil, ce qui les conduira à la page d’accueil du Portail d’entreprise où les certificats S/MIME seront récupérés.
        - **E-mail** : envoie un e-mail à l’utilisateur final en l’informant qu’il doit lancer le Portail d’entreprise pour récupérer ses certificats S/MIME. Si l’utilisateur se trouve sur son appareil iOS inscrit lorsqu’il clique sur le lien dans l’e-mail, il est redirigé vers le Portail d’entreprise pour récupérer ses certificats.
    
13. Sélectionnez **Affectations** pour affecter la stratégie de configuration des applications aux groupes Azure AD. Pour plus d’informations, consultez [Affecter des applications à des groupes avec Microsoft Intune](~/apps/apps-deploy.md).

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations, consultez [Stratégies de configuration des applications pour Microsoft Intune](app-configuration-policies-overview.md).
