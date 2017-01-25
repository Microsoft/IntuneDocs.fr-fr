---
title: Configuration requise | Microsoft Docs
description: "Liens menant vers les prérequis et les conditions requises pour utiliser Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/10/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a567d55141c4510a5c81861df1522f118104de61
ms.openlocfilehash: 900b3a9bcc9ce58cd165b14592c850b50739a33a


---

# <a name="prerequisites-to-getting-started-with-intune"></a>Conditions préalables à la prise en main de Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Avant de commencer la configuration de Microsoft Intune, passez en revue les conditions suivantes :

- [Appareils et ordinateurs pris en charge](#intune-supported-devices)
- [Liste des navigateurs web pris en charge pour l’utilisation d’Intune](#intune-supported-web-browsers)

Vous devez également vous familiariser avec l'[utilisation de la bande passante réseau Intune](network-bandwidth-use.md).

## <a name="intune-supported-devices"></a>Appareils pris en charge par Intune

Vous pouvez gérer les appareils suivants avec la gestion des appareils mobiles Intune :

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Vous ne pouvez pas utiliser Intune pour gérer les systèmes d’exploitation Windows Server.

La gestion des appareils Intune fournit [ces fonctionnalités](mobile-device-management-capabilities-in-microsoft-intune.md).

### <a name="windows-pc-software-client"></a>Logiciel client pour PC Windows

Vous pouvez déployer et installer un [logiciel client Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune) sur les PC Windows en guise d’alternative à l’inscription. Vous pouvez utiliser le client logiciel Intune pour gérer des PC Windows 7 et versions ultérieures. La gestion des PC avec le logiciel client fournit [ces fonctionnalités](windows-pc-management-capabilities-in-microsoft-intune.md).

### <a name="exchange-activesync-management"></a>Gestion d’Exchange ActiveSync

Vous pouvez gérer des [appareils Exchange ActiveSync](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune) à partir de la console Intune. Cette option fournit un ensemble limité de fonctionnalités de gestion par rapport aux autres méthodes. Pour obtenir une liste des appareils pris en charge, consultez [Fonctionnalités de gestion des appareils mobiles intégrées à Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0).

## <a name="intune-supported-web-browsers"></a>Navigateurs web pris en charge par Intune

Différentes tâches administratives vous obligent à utiliser l’un des sites web d’administration suivants.

- [Portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Console d'administration Microsoft Intune](https://admin.manage.microsoft.com/)

|Fonctionnalité Intune |Navigateurs pris en charge|
|---------|---------|
|**Console d’administration Intune**     |  Internet Explorer 10 ou version ultérieure<br /><br />Google Chrome (versions antérieures à la version 42)<br /><br />Mozilla Firefox avec Silverlight activé<br />**Remarque :** Mozilla supprimera la prise en charge de Silverlight dès mars 2017. [En savoir plus](https://go.microsoft.com/fwlink/?linkid=836872). |
|**Portail d’administration Office 365**     |Tous les navigateurs, y compris les navigateurs mobiles et gérés  |
|**Site web Portail d’entreprise**     |**Sur les appareils mobiles :** Utiliser le navigateur web par défaut pour chaque plateforme prise en charge   <br /><br />**Sur les PC Windows :** Internet Explorer 10 ou version ultérieure, ou Microsoft Edge<br /><br />**Sur Mac OS X 10.9 ou version ultérieure :** Apple Safari    |

> [!Note]
> Microsoft Edge et les navigateurs mobiles ne sont pas pris en charge pour la console d’administration, car ils ne prennent pas en charge [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx). La console Intune quitte progressivement Silverlight ; à terme, toutes les fonctionnalités de gestion d’applications et d’appareils mobiles d’Intune seront [disponibles dans le nouveau portail Microsoft Azure](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/).


Seuls les utilisateurs disposant d’autorisations d’administrateur de service ou les administrateurs clients ayant le rôle Administrateur général peuvent se connecter à ce portail. Pour accéder à la console d’administration, votre compte doit posséder une licence d’utilisation de Microsoft Intune et son état de connexion doit être **Autorisé**.

>[!div class="step-by-step"]

>[**Mise en réseau**&rarr;](network-bandwidth-use.md)  



<!--HONumber=Jan17_HO2-->


