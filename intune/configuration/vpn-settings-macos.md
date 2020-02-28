---
title: Configurer les paramètres VPN des appareils macOS dans Microsoft Intune - Azure | Microsoft Docs
description: Ajoutez ou créez un profil de configuration VPN (réseau privé virtuel), notamment les détails de la connexion, le tunneling fractionné, les paramètres VPN personnalisés avec l’identificateur, les paires clé/valeur, les paramètres de proxy pour inclure un script de configuration, une adresse IP ou FQDN (nom de domaine complet) et le port TCP dans Microsoft Intune sur les appareils exécutant macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b20a7eca6f71d46380f9fcdb1674226cc54a104f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510777"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>Ajouter des paramètres VPN sur les appareils macOS dans Microsoft Intune



Cet article présente les paramètres Intune permettant de configurer des connexions VPN sur les appareils exécutant macOS.

Selon les paramètres que vous choisissez, toutes les valeurs de la liste suivante ne sont pas nécessairement configurables.

## <a name="before-you-begin"></a>Avant de commencer

[Créez un profil de configuration d’appareil](vpn-settings-configure.md).

> [!NOTE]
> Ces paramètres sont disponibles pour tous les types d’inscription. Pour plus d’informations sur les types d’inscriptions, consultez [Inscription macOS](../enrollment/macos-enroll.md).

## <a name="base-vpn-settings"></a>Paramètres VPN de base

**Nom de connexion** : entrez un nom pour cette connexion. Les utilisateurs finaux voient ce nom quand ils recherchent dans leur appareil la liste des connexions VPN disponibles.
- **Adresse IP ou nom de domaine complet** : Fournissez l’adresse IP ou le nom de domaine complet du serveur VPN auquel les appareils se connectent. Exemples : **192.168.1.1**, **vpn.contoso.com**.
- **Méthode d’authentification** : choisissez la manière dont les appareils s’authentifient auprès du serveur VPN :
  - **Certificats** : sous **Certificat d’authentification**, choisissez le profil de certificat SCEP ou PKCS que vous avez créé précédemment pour authentifier la connexion. Pour plus d’informations sur les profils de certificat, consultez [Guide pratique pour configurer des certificats](../protect/certificates-configure.md).
  - **Nom d’utilisateur et mot de passe** : les utilisateurs finaux doivent fournir un nom d’utilisateur et un mot de passe pour se connecter au serveur VPN.
- **Type de connexion** : Sélectionnez le type de connexion VPN dans la liste de fournisseurs suivante :
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **Client F5 Edge**
  - **Pulse Secure**
  - **VPN personnalisé**
- **Fractionner le tunneling** : **activez** ou **désactivez** cette option qui permet aux appareils de choisir la connexion à utiliser en fonction du trafic. Par exemple, un utilisateur dans un hôtel utilise la connexion VPN pour accéder aux fichiers de travail, mais utilise le réseau standard de l’hôtel pour la navigation web ordinaire.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS/iPadOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Paramètres VPN personnalisés

Si vous avez sélectionné **VPN personnalisé**, configurez ces paramètres supplémentaires :

- **Identificateur VPN** : entrez un identificateur pour l’application VPN que vous utilisez. Cet identificateur est fourni par votre fournisseur VPN.
- **Entrez les paires clé-valeur pour les attributs du VPN personnalisé** : ajoutez ou importez des **Clés** et **Valeurs** pour personnaliser votre connexion VPN. Ces valeurs sont généralement fournies par votre fournisseur de VPN.

## <a name="proxy-settings"></a>Paramètres du proxy

- **Script de configuration automatique** : utilisez un fichier pour configurer le serveur proxy. Entrez l’**URL du serveur Proxy** qui contient le fichier de configuration. Par exemple, entrez `http://proxy.contoso.com`.
- **Adresse** : entrez l’adresse du serveur proxy (comme une adresse IP).
- **Numéro de port** : entrez le numéro de port associé au serveur proxy.

## <a name="next-steps"></a>Étapes suivantes

Le profil est créé, mais il ne fait rien pour le moment. Vous devez à présent [affecter le profil](device-profile-assign.md) et [superviser son état](device-profile-monitor.md).

Configurez les paramètres VPN sur les appareils [Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [iOS/iPadOS](vpn-settings-ios.md) et [Windows 10](vpn-settings-windows-10.md).
