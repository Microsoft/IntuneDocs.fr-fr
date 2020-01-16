---
title: Chiffrer un appareil Android pour Intune | Microsoft Docs
description: Étapes à suivre pour activer le chiffrement d’appareil Android lorsqu’il est requis par Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: d4430e92-04cc-48e9-a77a-81b95a90b6b3
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 2774a4f4c571b8a965c9ec47376a671df2dbf006
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856680"
---
# <a name="encrypting-your-android-device"></a>Chiffrement de votre appareil Android

Le chiffrement de l’appareil protège vos fichiers et dossiers contre tout accès non autorisé si votre appareil est perdu ou volé. Une fois que vous avez activé le chiffrement de l’appareil, seules les personnes avec le mot de passe ou le code confidentiel corrects pourront se connecter à votre appareil. 

Avant de pouvoir accéder aux ressources scolaires ou professionnelles, votre organisation peut vous demander de chiffrer votre appareil Android. Certains appareils Android plus récents sont chiffrés par défaut, prêts à l’emploi.  

## <a name="turn-on-encryption"></a>Activer le chiffrement

Si Portail d’entreprise ou l’application Microsoft Intune vous invite à chiffrer votre appareil, procédez comme suit. 

> [!Note]
> Certains appareils Android de Huawei, vivo et OPPO ne peuvent pas être chiffrés. Découvrez-en plus [ici](your-device-appears-encrypted-but-cp-says-otherwise-android.md).  

1. Définissez un verrouillage de l’écran de l’appareil.  
    a. Accédez à **Paramètres** > **Écran de verrouillage et sécurité** > **Type d’écran de verrouillage**.  
    b. Sélectionnez **pin**, **mot de passe**ou **modèle**.  
    c. Suivez les instructions à l’écran pour configurer votre verrouillage d’écran.  

2. Revenez à l' **écran de verrouillage et à sécurité** , puis sélectionnez **Démarrage sécurisé**.
3. Choisissez **exiger un code PIN quand l’appareil s’allume** > **OK**.
4. Entrez votre code PIN pour confirmer et chiffrer votre appareil.
5. Ouvrez l’application Portail d’entreprise ou Microsoft Intune.
    * Utilisateurs Portail d’entreprise : sélectionnez votre appareil, puis appuyez sur **Vérifier les paramètres de l’appareil**. 
    * Microsoft Intune utilisateurs : vous devez attendre la mise à jour de la page, mais dans ce cas, votre état de chiffrement doit passer à conforme.  

Les appareils exécutant Android 4,4 et versions antérieures peuvent ne pas disposer de l’option de **Démarrage sécurisé** . Dans ce cas, procédez comme suit pour chiffrer votre appareil.

1. Accédez à **paramètres** > **sécurité** > **chiffrer l’appareil**. Les étiquettes à l’écran varient d’un appareil Android à l’autre. Si vous ne voyez pas l’option **chiffrer l’appareil** , cochez la case suivante :
    * **Stockage** > le **chiffrement du stockage**
    * **Écran de verrouillage du** > **de stockage et sécurité** > **autres paramètres de sécurité** 

2. Suivez les instructions à l'écran. Au cours du chiffrement, votre appareil peut redémarrer plusieurs fois.
3. Ouvrez l’application Portail d’entreprise ou Microsoft Intune.
    * Utilisateurs Portail d’entreprise : sélectionnez votre appareil, puis appuyez sur **Vérifier les paramètres de l’appareil**.  
    * Microsoft Intune utilisateurs : vous devez attendre la mise à jour de la page, mais dans ce cas, votre état de chiffrement doit passer à conforme.

## <a name="troubleshoot"></a>Dépannage  
**Problème**: vous avez déjà chiffré votre appareil et

- Le bouton de chiffrement est désactivé.
- Un message vous informe que vous devez chiffrer votre appareil.
- Vous recevez des erreurs lors de la tentative d’utilisation de l’application Portail d’entreprise ou Microsoft Intune.

**Solutions possibles**

- Vérifiez que votre appareil dispose de suffisamment de batterie ou qu’il est branché sur secteur.  
- Vérifiez que vous avez configuré un code confidentiel ou un mot de passe sur votre appareil.  

Encore besoin d’aide ? Contactez le support technique de votre entreprise (consultez le [site web du portail d’entreprise](https://go.microsoft.com/fwlink/?linkid=2010980) pour les informations de contact) ou écrivez à <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with encryption on my Android device&body=Describe the issue you're experiencing here.">l’équipe Microsoft Android</a>.  
