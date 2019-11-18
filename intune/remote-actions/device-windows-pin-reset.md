---
title: Réinitialiser le code secret sur des appareils Windows avec Microsoft Intune - Azure | Microsoft Docs
description: Pour réinitialiser le code secret sur des appareils Windows, installez le service de réinitialisation du code PIN Microsoft et le client de réinitialisation du code PIN Microsoft, créez une stratégie d’appareil à l’aide de votre ID Azure Active Directory, puis réinitialisez le code secret dans le portail Azure à l’aide de Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1b2390462376c88129435de30eb98020563f3878
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713104"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>Réinitialiser le code secret sur des appareils Windows à l’aide d’Intune

Vous pouvez réinitialiser le code secret pour des appareils Windows. La fonctionnalité de réinitialisation du code secret utilise le service de réinitialisation de code PIN Microsoft pour générer un nouveau code secret pour les appareils qui exécutent Windows 10 Mobile. 

## <a name="supported-platforms"></a>Plateformes prises en charge

- Windows 10 Mobile exécutant Creators Update et les versions ultérieures (joint à Azure AD).

Les plateformes suivantes ne sont **pas** prises en charge :
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>Autoriser les services de réinitialisation du code PIN

Pour réinitialiser le code secret sur des appareils Windows, vous devez intégrer le service de réinitialisation du code PIN à votre locataire Intune.

1. Accédez à [Microsoft PIN Reset Service Production](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent) et connectez-vous à l’aide du compte d’administrateur client.
2. Cliquez sur **Accept** afin de donner votre consentement pour que le service de réinitialisation du code PIN accède à votre compte : ![Accepter la demande d’autorisation pour le serveur de réinitialisation du code PIN](./media/device-windows-pin-reset/pin-reset-service-home-screen.png)
3. Accédez à [Microsoft PIN Reset Client Production](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent) et connectez-vous à l’aide du compte d’administrateur client. Cliquez sur **Accept** afin de donner votre consentement pour que le client de réinitialisation du code PIN accède à votre compte.
4. Dans le [portail Azure](https://portal.azure.com), vérifiez que les services de réinitialisation du code PIN sont listés dans Applications d’entreprise (toutes les applications) : ![Page des autorisations du service de réinitialisation de code PIN](./media/device-windows-pin-reset/pin-reset-service-application.png)

> [!NOTE]
> Une fois que vous avez accepté les demandes de réinitialisation du code PIN, vous pouvez obtenir un message `Page not found`, ou il peut vous sembler que rien ne s’est produit. Ce comportement est normal. Vérifiez que les deux applications de réinitialisation du code PIN sont répertoriées pour votre client.

## <a name="configure-windows-devices-to-use-pin-reset"></a>Configurer les appareils Windows pour utiliser la réinitialisation de code PIN

Pour configurer la réinitialisation du code PIN sur les appareils Windows que vous gérez, utilisez une [stratégie d’appareil personnalisée Windows 10 Intune](../configuration/custom-settings-windows-10.md). Configurez la stratégie à l’aide du fournisseur de services de configuration de stratégie Windows suivant :

**Utiliser la stratégie d’appareil** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

Remplacez *ID de locataire* par l’ID de votre annuaire Azure AD, qui est répertorié dans les **Propriétés** d’Azure Active Directory dans le [portail Azure](https://portal.azure.com).

Affectez à ce fournisseur de services de configuration la valeur **True**.

> [!TIP]
> Après avoir créé la stratégie, vous l’affectez (ou la déployez) à un groupe. La stratégie peut être affectée à des groupes d’utilisateurs ou à des groupes d’appareils. Si vous l’affectez à un groupe d’utilisateurs, celui-ci peut comprendre des utilisateurs qui ont d’autres appareils, par exemple des appareils IOS. Techniquement, la stratégie ne s’applique pas, mais ces appareils sont quand même inclus dans les détails d’état.

## <a name="reset-the-passcode"></a>Réinitialiser le code secret

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). 
2. Sélectionnez **Appareils**, puis **Tous les appareils**.
3. Sélectionnez l’appareil dont vous souhaitez réinitialiser le code secret. Dans les propriétés de l’appareil, sélectionnez **Nouveau code secret**.
4. Cliquez sur **Oui** pour confirmer la suppression. Le code secret est généré et affiché dans le portail pendant les sept prochains jours.

## <a name="next-step"></a>Étape suivante

Si la réinitialisation du code secret échoue, un lien est fourni dans le portail pour obtenir plus d’informations.
