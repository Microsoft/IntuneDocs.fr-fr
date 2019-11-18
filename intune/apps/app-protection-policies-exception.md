---
title: Exceptions de la stratégie de transfert de données pour les applications
titleSuffix: Microsoft Intune
description: Créez des exceptions à la stratégie de transfert de données Intune App Protection (APP).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f9015e3a-c22c-42eb-90e6-ba48dee3a41d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18b1b8feda00f5c669b39bc365c637dcd3968078
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984067"
---
# <a name="how-to-create-exceptions-to-the-intune-app-protection-policy-app-data-transfer-policy"></a>Guide pratique pour créer des exceptions à la stratégie de transfert de données Intune App Protection (APP)

En tant qu’administrateur, vous pouvez créer des exceptions à la stratégie de transfert de données Intune App Protection (APP). Une exception vous permet de choisir spécifiquement quelles applications non gérées peuvent transférer des données vers et depuis des applications gérées. Votre service informatique doit approuver les applications non gérées que vous incluez dans la liste des exceptions. 

>[!WARNING] 
> Vous êtes responsable des modifications apportées à la stratégie des exceptions de transfert de données. Les ajouts à cette stratégie autorisent les applications non gérées (les applications qui ne sont pas gérées par Intune) à accéder aux données protégées par les applications gérées. Cet accès à des données protégées peut entraîner des fuites de sécurité des données. Ajoutez seulement des exceptions de transfert de données pour les applications que votre organisation doit utiliser, mais qui ne prennent pas en charge les stratégies de protection d’application Intune. Ajoutez des exceptions seulement pour les applications dont vous ne considérez pas qu’elles représentent des risques de fuite de données.

Dans une stratégie de protection d’application Intune, si vous affectez la valeur **Applications gérées par la stratégie** à **Autoriser l’application à transférer des données vers d’autres applications**, cela signifie que l’application peut transférer des données uniquement aux applications gérées par Intune. Si vous avez besoin d’autoriser le transfert de données vers des applications spécifiques qui ne prennent pas en charge les stratégies de protection d’application Intune, vous pouvez créer des exceptions à cette stratégie à l’aide de l’option **Sélectionner des applications à exclure**. Les exemptions permettent aux applications gérées par Intune d’appeler des applications non gérées en fonction du protocole d’URL (iOS) ou du nom du package (Android). Par défaut, Intune ajoute des applications natives essentielles à cette liste d’exceptions. 

> [!NOTE]
> La modification ou l’ajout d’exceptions à la stratégie de transfert de données n’impacte pas les autres stratégies de protection d’application, comme des restrictions sur les opérations de couper, de copier et de coller. 

## <a name="ios-data-transfer-exceptions"></a>Exceptions du transfert des données iOS
Pour une stratégie ciblant iOS, vous pouvez configurer des exceptions de transfert de données par protocole d’URL. Pour ajouter une exception, consultez la documentation fournie par le développeur de l’application pour rechercher des informations sur les protocoles d’URL pris en charge. Pour plus d’informations sur les exceptions de transfert de données iOS, consultez [Paramètres de stratégie de protection d’application iOS - Exemptions du transfert de données](app-protection-policy-settings-ios.md#data-transfer-exemptions).

> [!NOTE]
> Microsoft ne propose pas de méthode permettant de rechercher manuellement le protocole URL dans le but de créer des exceptions pour des applications tierces. 

## <a name="android-data-transfer-exceptions"></a>Exceptions du transfert de données Android
Pour une stratégie ciblant Android, vous pouvez configurer des exceptions de transfert de données par nom de package d’application. Vous pouvez consulter la page de **Google Play Store** pour trouver le nom de package de l’application pour laquelle vous voulez ajouter une exception. Pour plus d’informations sur les exceptions de transfert de données Android, consultez [Paramètres de stratégie de protection d’application Android - Exemptions du transfert de données](app-protection-policy-settings-android.md#data-transfer-exemptions).


>[!TIP]
> Vous pouvez connaître l’ID de package d’une application en accédant à l’application dans le Google Play Store. L’ID de package est contenu dans l’URL de la page d’application. Par exemple, l’ID de package de l’application Microsoft Word est **com.microsoft.office.word**.

### <a name="example"></a>Exemple
Si vous ajoutez le package **Webex** comme exception à la stratégie de transfert des données de la Gestion des applications mobiles, les liens Webex qui se trouvent dans un e-mail d’une application Outlook gérée sont autorisés à s’ouvrir directement dans l’application Webex. Le transfert de données reste toujours limité dans les autres applications non gérées.

- Exemple **Webex** iOS :   pour exempter l’application **Webex** et l’autoriser à être appelée par des applications gérées par Intune, vous devez ajouter une exception de transfert de données pour la chaîne suivante : <code>wbx</code>
    
- Exemple **Plans** iOS :   pour exempter l’application native **Plans** et l’autoriser à être appelée par des applications gérées par Intune, vous devez ajouter une exception de transfert de données pour la chaîne suivante : <code>maps</code>

- Exemple **Webex** Android :   pour exempter l’application **Webex** et l’autoriser à être appelée par des applications gérées par Intune, vous devez ajouter une exception de transfert de données pour la chaîne suivante : <code>com.cisco.webex.meetings</code>
    
- Exemple **SMS** Android :   pour exempter l’application native **SMS** et l’autoriser à être appelée par des applications gérées par Intune parmi diverses applications de messagerie et divers appareils Android, vous devez ajouter des exceptions de transfert de données pour les chaînes suivantes : 
    <code>com.google.android.apps.messaging</code>
    
    <code>com.android.mms</code>
    
    <code>com.samsung.android.messaging</code>

- Exemple du **programme d’installation de certificats** Android : Pour exempter l’application native du **programme d’installation du certificat** afin qu’Outlook pour Android puisse installer un certificat S/MIME (remis sous forme d’une pièce jointe à un e-mail) dans le magasin de clés Android, vous devez ajouter l’exception de transfert de données pour la chaîne suivante : <code>com.android.certinstaller</code>. Pour plus d’informations, voir [Étiquetage et protection de la confidentialité dans Outlook pour iOS et Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/sensitive-labeling-and-protection-outlook-for-ios-android).

## <a name="next-steps"></a>Étapes suivantes

- [Créer et déployer des stratégies de protection d’applications](app-protection-policies.md)
- [Paramètres de stratégie de protection d’application iOS - Exemptions du transfert de données](app-protection-policy-settings-ios.md#data-transfer-exemptions)
- [Paramètres de stratégie de protection d’application Android - Exemptions du transfert de données](app-protection-policy-settings-android.md#data-transfer-exemptions)
