---
title: "Verrouillage à distance et réinitialisation du code d’accès | Microsoft Intune"
description: "Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code secret."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
translationtype: Human Translation
ms.sourcegitcommit: b76e9e16ef1fa6870783326630ae74d07ae59cbb
ms.openlocfilehash: f69855f27ddc8ab6903c317383ef715f98590caf

---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>Protéger vos appareils à l’aide du verrouillage à distance et de la réinitialisation du code d’accès
Microsoft Intune fournit des fonctionnalités de verrouillage à distance et de réinitialisation du code d’accès.

## <a name="lock-a-device-remotely"></a>Verrouiller un appareil à distance
Si un utilisateur perd un appareil, vous pouvez verrouiller celui-ci à distance. Le tableau ci-dessous illustre le fonctionnement du verrouillage à distance sur différentes plateformes mobiles.

|Plateforme|Verrouillage à distance|
|------------|---------------|
|iOS|Pris en charge|
|Android|Pris en charge|
|Windows 10 et Windows 10 Mobile|Pris en charge|
|Windows Phone 8 et Windows Phone 8.1|Pris en charge|
|Windows RT 8.1 et Windows RT|Prise en charge si l'utilisateur actuel de l'appareil est le même utilisateur qui a inscrit l'appareil.|
|Windows 8.1|Prise en charge si l'utilisateur actuel de l'appareil est le même utilisateur qui a inscrit l'appareil.|

Le verrouillage à distance n’est pas pris en charge pour les PC Windows inscrits auprès du client logiciel Intune.

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>Verrouiller un appareil mobile à distance par le biais de la console Intune

1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **Groupes** &gt; **Tous les appareils** &gt; **Tous les appareils mobiles**.

2.  Choisissez **Tous les appareils gérés par gestion directe** pour les appareils inscrits dans Intune ou **Tous les appareils gérés par Exchange ActiveSync**.

    > [!TIP]
    > Vous pouvez également accéder à un appareil par l'utilisateur. Sélectionnez **Tous les utilisateurs**. Dans la page des propriétés de l’utilisateur, sélectionnez **Appareils**, puis le nom de l’appareil mobile à verrouiller.

3.  Dans la liste, cliquez sur le ou les appareils à verrouiller. Dans la barre des tâches, choisissez **Tâches à distance**, puis sélectionnez **Verrouillage à distance**.

## <a name="reset-the-passcode-on-a-device"></a>Réinitialiser le code d’accès d’un appareil
Si un utilisateur oublie un code d’accès, vous pouvez l’aider à résoudre ce problème en supprimant le code d’accès d’un appareil ou en forçant l’application d’un nouveau code accès temporaire sur un appareil. Le tableau suivant indique la méthode de réinitialisation du code d’accès sur différentes plateformes mobiles.

|Plateforme|Réinitialiser le code secret|
|------------|------------------|
|iOS|Prise en charge de l'effacement du code d'accès d'un appareil. Ne crée pas un nouveau code d'accès temporaire.|
|Android|Prise en charge sur les versions antérieures à Android 7.0. Crée un code d’accès temporaire.|
|Windows 10 Mobile|Pris en charge|
|Windows Phone 8 et Windows Phone 8.1|Pris en charge|
|Windows RT 8.1 et Windows RT|Non pris en charge|
|Windows 8.1|Non pris en charge|

La réinitialisation du code d’accès n’est pas prise en charge pour les PC Windows inscrits auprès du client logiciel Intune.

### <a name="reset-a-passcode"></a>Réinitialiser un code secret

1.  Dans la [console d’administration Intune](https://manage.microsoft.com/), choisissez **Groupes** &gt; **Tous les appareils** &gt; **Tous les appareils mobiles**.

2.  Choisissez **Tous les appareils gérés par gestion directe** pour les appareils inscrits dans Intune ou **Tous les appareils gérés par Exchange ActiveSync**.

    > [!TIP]
    > Vous pouvez également accéder à un appareil par l'utilisateur. Cliquez sur **Tous les utilisateurs**. Dans la page Propriétés de l’utilisateur, cliquez sur **Appareils**, puis sur le nom de l’appareil mobile à réinitialiser.

3.  Dans la liste, cliquez sur le ou les appareils à verrouiller. Dans la barre des tâches, choisissez **Tâches à distance**, puis sélectionnez **Réinitialisation du code d’accès**.


### <a name="see-also"></a>Voir aussi
[Mettre des appareils hors service](retire-devices-from-microsoft-intune-management.md) et [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx) (Réinitialisation sélective de Windows pour la gestion des données d’appareils)



<!--HONumber=Nov16_HO2-->


