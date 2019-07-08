---
title: Chiffrer un appareil Android pour Intune | Microsoft Docs
description: Étapes pour activer le chiffrement d’appareil Android lorsque requis par Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfc17c60412a1cfe90693216caa69ada3d2d2c9a
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67545260"
---
# <a name="encrypting-your-android-device"></a>Chiffrement de votre appareil Android

Chiffrement de l’appareil protège vos fichiers et dossiers contre tout accès non autorisé si votre appareil est perdu ou volé. Une fois que vous activez le chiffrement de l’appareil, seules les personnes qui le mot de passe correct ou un code pin sera en mesure de se connecter à votre appareil. 

Avant de pouvoir accéder à des ressources scolaires ou professionnels, votre organisation peut vous obliger à chiffrer votre appareil Android. Certains appareils Android plus récents sont chiffrées par défaut, out-of-the-box.  

## <a name="turn-on-encryption"></a>Activer le chiffrement

Si le portail d’entreprise ou de l’application Microsoft Intune vous invite à chiffrer votre appareil, procédez comme suit. 

> [!Note]
> Certains appareils Android à partir de Huawei Vivo et OPPO ne peut pas être chiffrées. Découvrez-en plus [ici](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Définissez un verrouillage d’écran de périphérique.  
    a. Accédez à **Paramètres** > **Écran de verrouillage et sécurité** > **Type d’écran de verrouillage**.  
    b. Sélectionnez **PIN**, **mot de passe**, ou **modèle**.  
    c. Suivez les instructions à l’écran pour configurer votre écran de verrouillage.  

2. Revenez à **écran de verrouillage et sécurité** et sélectionnez **le démarrage sécurisé**.
3. Choisissez **exiger le code PIN lors de l’appareil s’allume** > **OK**.
4. Entrez votre PIN pour confirmer et chiffrer votre appareil.
5. Ouvrez l’application portail d’entreprise ou Microsoft Intune.
    * Utilisateurs Portail d’entreprise : sélectionnez votre appareil, puis appuyez sur **Vérifier les paramètres de l’appareil**. 
    * Les utilisateurs de Microsoft Intune : vous devez attendre jusqu'à ce que les mises à jour de la page, mais lorsque cela arrive, votre état de chiffrement doit passer à conforme.  

Appareils exécutant Android 4.4 et versions antérieures ne peuvent pas avoir le **démarrage sécurisé** option. Dans ce cas, effectuez les étapes suivantes pour chiffrer votre appareil.

1. Accédez à **paramètres** > **sécurité** > **chiffrer appareil**. Les étiquettes à l’écran varient entre les appareils Android. Si vous ne voyez pas le **chiffrer l’appareil** option, l’archivage :
    * **Stockage** > **chiffrement du stockage**
    * **Stockage** > **écran de verrouillage et sécurité** > **autres paramètres de sécurité** 

2. Suivez les instructions à l'écran. Au cours du chiffrement, votre appareil peut redémarrer plusieurs fois.
3. Ouvrez l’application portail d’entreprise ou Microsoft Intune.
    * Utilisateurs Portail d’entreprise : sélectionnez votre appareil, puis appuyez sur **Vérifier les paramètres de l’appareil**.  
    * Les utilisateurs de Microsoft Intune : vous devez attendre jusqu'à ce que les mises à jour de la page, mais lorsque cela arrive, votre état de chiffrement doit passer à conforme.

## <a name="troubleshoot"></a>Dépannage  
**Problème**: vous avez déjà chiffré votre appareil et

- Le bouton de chiffrement est désactivé.
- Un message vous informe que vous devez chiffrer votre appareil.
- Vous obtenez des erreurs lorsque vous tentez d’utiliser l’application portail d’entreprise ou Microsoft Intune.

**Solutions possibles**

- Vérifiez que votre appareil dispose de suffisamment de batterie ou qu’il est branché sur secteur.  
- Vérifiez que vous avez configuré un code confidentiel ou un mot de passe sur votre appareil.  

Encore besoin d’aide ? Contactez le support technique de votre entreprise (consultez le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour les informations de contact) ou écrivez à <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">l’équipe Microsoft Android</a>.  
