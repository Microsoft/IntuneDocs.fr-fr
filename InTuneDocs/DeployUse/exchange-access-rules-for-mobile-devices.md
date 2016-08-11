---
title: "Règles d’accès Exchange pour les appareils mobiles | Microsoft Intune"
description: "Règles d’accès Exchange ActiveSync permettant d’autoriser ou de bloquer les connexions d’appareils avec EAS"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c49e19e8c478af252d7b59c380d5500a57b71db5
ms.openlocfilehash: 7714a338d02afedde2ac090964e4d18d4410a80e


---

# Règles d’accès Exchange pour les appareils mobiles
Les règles d’accès Exchange pour les appareils mobiles déterminent le niveau d’accès à Exchange ActiveSync accordé à ces appareils. Ces paramètres affectent tous les appareils mobiles, y compris ceux qui ne sont pas inscrits dans Microsoft Intune. Vous pouvez commencer par définir une **Règle par défaut** qui s'appliquera à tout appareil mobile auquel aucune règle personnalisée n'est appliquée. Le tableau suivant contient les niveaux d'accès gérés par Exchange ActiveSync :

|Niveaux d'accès|Description|
|----------------|---------------|
|**Autoriser les appareils à accéder à Exchange**|À l’état *Autoriser l’accès*, un appareil mobile peut se synchroniser par le biais d’ActiveSync Exchange et se connecter au serveur Exchange pour récupérer le courrier électronique et gérer les informations relatives le Calendrier, les Contacts, les Tâches et les Notes. Il en est ainsi tant que l’appareil est conforme à la stratégie de boîte aux lettres Exchange ActiveSync que vous avez configurée dans Exchange, sauf si l’utilisateur ou l’appareil mobile spécifique a été bloqué par l’administrateur Exchange.|
|**Bloquer l’accès à Exchange pour les appareils**|À l’état *Bloquer l’accès*, les appareils mobiles sont bloqués et ne sont pas autorisés à se connecter au serveur Exchange. Les appareils reçoivent une erreur HTTP 403 Interdit. L'utilisateur recevra un message électronique envoyé par le serveur Exchange pour l'avertir que l'appareil mobile a été bloqué et qu'il ne peut pas accéder à sa boîte aux lettres. Ce message ne peut pas apparaître sur l’appareil mobile bloqué. Vous pouvez ajouter du texte personnalisé à ce message pour fournir des instructions aux utilisateurs dont les appareils sont bloqués avec la tâche **Définir la notification utilisateur**.|
|**Placer les appareils mobiles en quarantaine afin de pouvoir les autoriser ou les bloquer ultérieurement**|Lorsqu'un appareil mobile est mis en quarantaine, il est autorisé à se connecter au serveur Exchange. Toutefois, il bénéficie uniquement d'un accès limité aux données. L'utilisateur peut ajouter du contenu à ses propres dossiers Calendrier, Contacts, Tâches et Notes, mais le serveur n'autorisera pas l'appareil à récupérer le contenu de la boîte aux lettres de l'utilisateur. L’utilisateur recevra un seul message électronique indiquant que l’appareil mobile est mis en quarantaine. Ce message est reçu sur l’appareil et dans la boîte aux lettres de l’utilisateur. Vous pouvez ajouter du texte personnalisé à ce message pour fournir des instructions aux utilisateurs dont les appareils sont mis en quarantaine par le biais de la tâche **Définir la notification utilisateur**.|

Une stratégie d’accès associe une **Règle par défaut** et des **Exceptions de plateforme** applicables à tous les appareils mobiles connectés à Exchange. Le tableau ci-dessous répertorie certains exemples de stratégies d'accès.

|Stratégie d’accès|Description|
|-------------------|---------------|
|Liste verte|Vous pouvez utiliser une *liste verte* pour accorder l’accès à une liste d’appareils connus et restreindre l’accès pour tout le reste. Pour ce faire, vous devez créer des règles personnalisées pour les plateformes d’appareil autorisées à accéder aux boîtes aux lettres des utilisateurs. Dès que vous créez une telle règle, vous devez définir la règle d'accès par défaut sur le blocage ou la mise en quarantaine de tous les autres appareils. Pour ajouter un nouvel appareil à la liste verte, créez une nouvelle règle personnalisée.|
|Liste rouge|Vous pouvez utiliser une *liste rouge* pour accorder un accès à tous les appareils par défaut, mais pour bloquer l’accès d’un ensemble d’appareils qui ne doivent pas accéder à votre organisation. Créez une liste rouge en créant des règles personnalisées pour bloquer les plateformes d’appareil qui ne doivent pas se synchroniser avec les boîtes aux lettres de l’organisation. La règle par défaut doit être définie sur l'autorisation d'accès de tous les appareils qui ne sont pas explicitement bloqués par les règles existantes. Pour ajouter un nouvel appareil ou un ensemble d'appareils à la liste rouge, créez une nouvelle règle personnalisée.|
|Liste mixte|Outre la création de listes rouges et vertes, vous pouvez mettre en quarantaine des nouveaux appareils mobiles devant être utilisés par l'organisation afin de les évaluer. Par exemple, si vous avez créé une liste rouge pour les appareils mobiles non autorisés au sein de votre organisation, et une liste verte pour les appareils mobiles autorisés au sein de celle-ci, vous pouvez définir la règle par défaut sur la mise en quarantaine. Tous les autres appareils seront automatiquement mis en quarantaine. Cela vous permet de détecter les nouveaux appareils devant être utilisés dans l’organisation et de décider de leur ajout à la liste rouge ou la liste verte.|
La procédure suivante décrit comment créer une règle personnalisée.

## Créer une règle d’accès par défaut

1.  Sélectionnez [Console d’administration Microsoft Intune](http://manage.microsoft.com) &gt; **Stratégie** &gt; **Exchange ActiveSync**.

2.  Dans la liste **Règle par défaut**, sélectionnez la règle d'accès à appliquer à tous les appareils mobiles non couverts par une règle ou une exemption personnelle. Choisissez **Enregistrer**.

La procédure suivante décrit comment créer une règle personnalisée.

## Créer une règle d’accès personnalisée

1. Sélectionnez [Console d’administration Microsoft Intune](http://manage.microsoft.com) &gt; **Stratégie** &gt; **Exchange ActiveSync**.

2.  Dans la liste **Exceptions de plateforme**, choisissez **Ajouter une règle** et créez une règle personnalisée. Choisissez **Enregistrer**.



<!--HONumber=Aug16_HO1-->


